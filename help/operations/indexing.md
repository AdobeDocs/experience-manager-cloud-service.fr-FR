---
title: Recherche et indexation de contenu
description: Découvrez la recherche et l’indexation de contenu dans AEM as a Cloud Service.
exl-id: 4fe5375c-1c84-44e7-9f78-1ac18fc6ea6b
feature: Operations
role: Admin
source-git-commit: 4de04b0a2c74406544757f9a92c061abfde5b615
workflow-type: tm+mt
source-wordcount: '2531'
ht-degree: 56%

---

# Recherche et indexation de contenu {#indexing}

## Changements dans AEM as a Cloud Service {#changes-in-aem-as-a-cloud-service}

Avec AEM as a Cloud Service, Adobe s’éloigne d’un modèle centré sur les instances AEM pour passer à une vue basée sur les services avec des conteneurs n-x pilotés par des pipelines CI/CD dans Cloud Manager. Au lieu de configurer et de gérer les index sur des instances AEM uniques, la configuration d’index doit être spécifiée avant un déploiement. Les changements de configuration dans la production enfreignent clairement les politiques CI/CD. Il en va de même pour les modifications d’index, car elles peuvent avoir un impact sur la stabilité et les performances du système si elles ne sont pas spécifiées, testées et réindexées avant de les mettre en production.

Voici la liste des principaux changements par rapport à AEM 6.5 et les versions antérieures :

1. Les utilisateurs et utilisatrices n’ont plus accès au gestionnaire d’index d’une seule instance AEM pour déboguer, configurer ou gérer l’indexation. Le gestionnaire d’index n’est utilisé que pour le développement local et les déploiements On-Prem.
1. Les utilisateurs ou utilisatrices ne changent pas d’index sur une seule instance AEM et n’ont plus à s’inquiéter des vérifications de cohérence ni de la réindexation.
1. En général, les changements d’index sont amorcés avant le passage à la production afin de ne pas contourner les passerelles de qualité dans les pipelines CI/CD de Cloud Manager et de ne pas affecter les indicateurs de performance clés métier en production.
1. Toutes les mesures associées, y compris les performances de recherche en production, sont disponibles pour les clients au moment de l’exécution afin de fournir une vue d’ensemble des sujets de recherche et d’indexation.
1. Les clients et les clientes peuvent configurer des alertes en fonction de leurs besoins.
1. Les SRE surveillent l’intégrité du système 24 h sur 24, 7 jours sur 7 et prennent des mesures dès que possible.
1. La configuration de l’index est modifiée par le biais de déploiements. Les modifications apportées à la définition de l’index sont configurées comme les autres modifications apportées au contenu.
1. À un niveau élevé dans AEM as a Cloud Service, avec l’introduction du [modèle de déploiement en continu](#index-management-using-rolling-deployments), deux ensembles d’index coexistent : un ensemble pour l’ancienne version, et un autre ensemble pour la nouvelle version.
1. Les clients et les clientes peuvent voir si la tâche d’indexation est terminée sur la page de version Cloud Manager et recevront une notification lorsque la nouvelle version sera prête à recevoir le trafic.

Restrictions :

* Actuellement, la gestion des index dans AEM as a Cloud Service n’est prise en charge que pour les index de type `lucene`.
* Seuls les analyseurs standard sont pris en charge (c’est-à-dire les analyseurs fournis avec le produit). Les analyseurs personnalisés ne sont pas pris en charge.
* En interne, d’autres index peuvent être configurés et utilisés pour les requêtes. Par exemple, les requêtes écrites selon l’index `damAssetLucene` peuvent, sur Skyline, être exécutées par rapport à une version Elasticsearch de cet index. Cette différence n’est généralement pas visible par l’application et par l’utilisateur ou l’utilisatrice, mais certains outils tels que la fonctionnalité `explain` signalent un index différent. Pour connaître les différences entre les index Lucene et les index Elastic, consultez [la documentation Elastic dans Apache Jackrabbit Oak](https://jackrabbit.apache.org/oak/docs/query/elastic.html). Les clients et les clientes n’ont pas besoin de configurer directement les index Elasticsearch et ne peuvent pas le faire.
* La recherche par des vecteurs de fonctionnalités similaires (`useInSimilarity = true`) n’est pas prise en charge.

>[!TIP]
>
>Pour plus d’informations sur l’indexation et les requêtes Oak, y compris une description détaillée des fonctionnalités de recherche et d’indexation avancées, consultez la [documentation d’Apache Oak](https://jackrabbit.apache.org/oak/docs/query/query.html).


## Utilisation {#how-to-use}

Les définitions d’index peuvent être classées en trois principaux cas d’utilisation, comme suit :

1. **Ajoutez** une nouvelle définition d’index personnalisée.
2. **Mettre à jour** une définition d’index existante en ajoutant une nouvelle version.
3. **Supprimez** une définition d’index qui n’est plus nécessaire.

Pour les points 1 et 2 ci-dessus, vous devez créer une définition d’index dans le cadre de votre base de code personnalisé dans le calendrier de publication Cloud Manager correspondant. Pour plus d’informations, consultez la documentation [Déploiement sur AEM as a Cloud Service](/help/implementing/deploying/overview.md) .

## Noms d’index {#index-names}

Une définition d’index peut appartenir à l’une des catégories suivantes :

1. Index prêt à l’emploi. Par exemple : `/oak:index/cqPageLucene-2` ou `/oak:index/damAssetLucene-8`.

2. Personnalisation d’un index prêt à l’emploi. Elles sont indiquées en ajoutant `-custom-` suivi d’un identifiant numérique au nom de l’index d’origine. Par exemple : `/oak:index/damAssetLucene-8-custom-1`.

3. Index entièrement personnalisé : il est possible de créer un index entièrement nouveau à partir de zéro. Leur nom doit comporter un préfixe pour éviter les conflits de noms. Par exemple : `/oak:index/acme.product-1-custom-2`, où le préfixe est `acme.`

>[!NOTE]
>
>L’introduction de nouveaux index sur le type de noeud `dam:Asset` (en particulier les index en texte intégral) est fortement déconseillée, car ils peuvent entrer en conflit avec les fonctionnalités de produit prêtes à l’emploi, ce qui entraîne des problèmes fonctionnels et de performances. En règle générale, l’ajout de propriétés supplémentaires à la version actuelle de l’index `damAssetLucene-*` est la manière la plus appropriée d’indexer les requêtes sur le type de noeud `dam:Asset` (ces modifications seront automatiquement fusionnées dans une nouvelle version de produit de l’index s’il est publié par la suite). En cas de doute, contactez le support Adobe pour obtenir des conseils.

## Préparation de la nouvelle définition d’index {#preparing-the-new-index-definition}

>[!NOTE]
>
>Si vous personnalisez un index prêt à l’emploi, par exemple `damAssetLucene-8`, copiez la dernière définition d’index prêt à l’emploi à partir d’un *environnement de Cloud Service* à l’aide du gestionnaire de modules CRX DE (`/crx/packmgr/`) . Renommez-le `damAssetLucene-8-custom-1` (ou supérieur) et ajoutez vos personnalisations dans le fichier XML. Ainsi, les configurations requises ne sont pas supprimées par inadvertance. Par exemple, le noeud `tika` situé sous `/oak:index/damAssetLucene-8/tika` est requis dans l’index personnalisé déployé dans un environnement AEM Cloud Service, mais n’existe pas dans le SDK d’AEM local.

Pour les personnalisations d’un index prêt à l’emploi, préparez un nouveau package contenant la définition d’index actuelle qui suit ce modèle de dénomination :

`<indexName>-<productVersion>-custom-<customVersion>`

Pour un index entièrement personnalisé, préparez un nouveau package de définition d’index qui contient la définition d’index qui suit ce modèle de dénomination :

`<prefix>.<indexName>-<productVersion>-custom-<customVersion>`

<!-- Alexandru: temporarily drafting this statement due to CQDOC-17701

The package from the above sample is built as `com.adobe.granite:new-index-content:zip:1.0.0-SNAPSHOT`. -->

>[!NOTE]
>
>Tout module de contenu contenant des définitions d’index doit avoir les propriétés suivantes définies dans le fichier `properties.xml` du module de contenu. `properties.xml` est créé par défaut dans un nouveau package, situé à l’emplacement `<package_name>/META-INF/vault/properties.xml` :
>
> * `noIntermediateSaves=true`
>
> * `allowIndexDefinitions=true`

## Déploiement de définitions d’index personnalisées {#deploying-custom-index-definitions}

Pour illustrer le déploiement d’une version personnalisée de l’index prêt à l’emploi `damAssetLucene-8`, nous allons fournir un guide détaillé. Dans cet exemple, nous allons le renommer `damAssetLucene-8-custom-1`. Puis le processus est le suivant :

1. Créez un dossier avec le nom d’index mis à jour dans le répertoire `ui.apps` :
   * Exemple : `ui.apps/src/main/content/jcr_root/_oak_index/damAssetLucene-8-custom-1/`

2. Ajoutez un fichier de configuration `.content.xml` avec les configurations personnalisées dans le dossier créé. Voici un exemple de personnalisation :
Nom de fichier : `ui.apps/src/main/content/jcr_root/_oak_index/damAssetLucene-8-custom-1/.content.xml`

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:dam="http://www.day.com/dam/1.0" xmlns:nt="http://www.jcp.org/jcr/nt/1.0" xmlns:oak="http://jackrabbit.apache.org/oak/ns/1.0" xmlns:rep="internal"
       jcr:mixinTypes="[rep:AccessControllable]"
       jcr:primaryType="oak:QueryIndexDefinition"
       async="[async,nrt]"
       compatVersion="{Long}2"
       evaluatePathRestrictions="{Boolean}true"
       includedPaths="[/content/dam]"
       maxFieldLength="{Long}100000"
       type="lucene">
       <facets
           jcr:primaryType="nt:unstructured"
           secure="statistical"
           topChildren="100"/>
       <indexRules jcr:primaryType="nt:unstructured">
           <dam:Asset jcr:primaryType="nt:unstructured">
               <properties jcr:primaryType="nt:unstructured">
                   <cqTags
                       jcr:primaryType="nt:unstructured"
                       name="jcr:content/metadata/cq:tags"
                       nodeScopeIndex="{Boolean}true"
                       propertyIndex="{Boolean}true"
                       useInSpellcheck="{Boolean}true"
                       useInSuggest="{Boolean}true"/>
               </properties>
           </dam:Asset>
       </indexRules>
       <tika jcr:primaryType="nt:folder">
           <config.xml jcr:primaryType="nt:file"/>
       </tika>
   </jcr:root>
   ```

3. Ajoutez une entrée au filtre FileVault dans `ui.apps/src/main/content/META-INF/vault/filter.xml` :

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <workspaceFilter version="1.0">
       ...
       <filter root="/oak:index/damAssetLucene-8-custom-1"/> 
   </workspaceFilter>
   ```

4. Ajoutez un fichier de configuration pour Apache Tika dans : `ui.apps/src/main/content/jcr_root/_oak_index/damAssetLucene-8-custom-1/tika/config.xml` :

   ```xml
   <properties>
       <detectors>
           <detector class="org.apache.tika.detect.TypeDetector"/>
       </detectors>
       <parsers>
           <parser class="org.apache.tika.parser.DefaultParser">
           <mime>text/plain</mime>
           </parser>
       </parsers>
       <service-loader initializableProblemHandler="ignore" dynamic="true"/>
   </properties>
   ```

5. Assurez-vous que votre configuration est conforme aux directives fournies dans la section [Configuration du projet](#project-configuration) . Effectuez les adaptations nécessaires en conséquence.

## Configuration du projet

Nous vous recommandons vivement d’utiliser version >= `1.3.2` du Jackrabbit `filevault-package-maven-plugin`. Les étapes pour l’intégrer à votre projet sont les suivantes :

1. Mettez à jour la version de niveau supérieur `pom.xml` :

   ```xml
   <plugin>
       <groupId>org.apache.jackrabbit</groupId>
           <artifactId>filevault-package-maven-plugin</artifactId>
           ...
           <version>1.3.2</version>
       ...
   </plugin>
   ```

2. Ajoutez le code suivant au niveau supérieur `pom.xml` :

   ```xml
   <jackrabbit-packagetype>
       <options>   
           <immutableRootNodeNames>apps,libs,oak:index</immutableRootNodeNames>
       </options>
   </jackrabbit-packagetype>
   ```

   Voici un exemple du fichier de niveau supérieur du projet `pom.xml` avec les configurations mentionnées ci-dessus incluses :

   Nom de fichier : `pom.xml`

   ```xml
   <plugin>
       <groupId>org.apache.jackrabbit</groupId>
           <artifactId>filevault-package-maven-plugin</artifactId>
           ...
           <version>1.3.2</version>
           <configuration>
               ...
               <validatorsSettings>
                   <jackrabbit-packagetype>
                       <options>
                           <immutableRootNodeNames>apps,libs,oak:index</immutableRootNodeNames>
                       </options>
                   </jackrabbit-packagetype>
                   ...
               ...
   </plugin>
   ```

3. Dans `ui.apps/pom.xml` et `ui.apps.structure/pom.xml`, il est nécessaire d&#39;activer les options `allowIndexDefinitions` et `noIntermediateSaves` dans le `filevault-package-maven-plugin`. L’activation de `allowIndexDefinitions` permet des définitions d’index personnalisées, tandis que `noIntermediateSaves` garantit que les configurations sont ajoutées de manière atomique.

   Noms de fichiers : `ui.apps/pom.xml` et `ui.apps.structure/pom.xml`

   ```xml
   <plugin>
       <groupId>org.apache.jackrabbit</groupId>
           <artifactId>filevault-package-maven-plugin</artifactId>
           <configuration>
               <allowIndexDefinitions>true</allowIndexDefinitions>
               <properties>
                   <cloudManagerTarget>none</cloudManagerTarget>
                   <noIntermediateSaves>true</noIntermediateSaves>
               </properties>
       ...
   </plugin>
   ```

4. Ajoutez un filtre pour `/oak:index` dans `ui.apps.structure/pom.xml` :

   ```xml
   <filters>
       ...
       <filter><root>/oak:index</root></filter>
   </filters>
   ```

Après avoir ajouté la nouvelle définition d’index, déployez la nouvelle application à l’aide de Cloud Manager. Ce déploiement lance deux tâches, chargées respectivement d’ajouter (et de fusionner si nécessaire) les définitions d’index à MongoDB et Azure Segment Store pour création et publication. Avant le commutateur, les référentiels sous-jacents font l’objet d’une réindexation avec les définitions d’index mises à jour.

>[!TIP]
>
>Pour plus d’informations sur la structure de package requise pour AEM as a Cloud Service, voir [AEM Structure de projet](/help/implementing/developing/introduction/aem-project-content-package-structure.md).

## Gestion des index à l’aide de déploiements en continu {#index-management-using-rolling-deployments}

### Qu’est-ce que la gestion des index ? {#what-is-index-management}

La gestion des index consiste à ajouter, supprimer et modifier des index. Changer la *définition* d’un index est rapide, mais appliquer le changement (opération souvent appelée « création d’un index » ou, pour les index existants, « réindexation ») nécessite du temps. Cette opération n’est pas instantanée : le référentiel doit être analysé pour que les données soient indexées.

### Que sont les déploiements en continu ? {#what-are-rolling-deployments}

Un déploiement en continu peut réduire les temps d’arrêt. Il permet également des mises à niveau sans interruption de service et des restaurations rapides. L’ancienne version de l’application s’exécute en même temps que la nouvelle version.

### Zones en lecture seule et en lecture-écriture {#read-only-and-read-write-areas}

Certaines zones du référentiel (parties en lecture seule) peuvent être différentes dans l’ancienne version et dans la nouvelle version de l’application. Les zones en lecture seule du référentiel sont généralement `/app` et `/libs`. Dans l’exemple suivant, des italiques sont utilisés pour marquer les zones en lecture seule, tandis que du gras est utilisé pour les zones en lecture-écriture.

* **/**
* */apps (lecture seule)*
* **/content**
* */libs (lecture seule)*
* **/oak:index**
* **/oak:index/acme.**
* **/jcr:system**
* **/system**
* **/var**

Les zones de lecture-écriture du référentiel sont partagées entre toutes les versions de l’application, tandis que pour chaque version de l’application, il existe un ensemble spécifique de `/apps` et `/libs`.

### Gestion des index sans déploiements en continu {#index-management-without-rolling-deployments}

Lors du développement ou de l’utilisation d’installations on-premise, les index peuvent être ajoutés, supprimés ou modifiés au moment de l’exécution. Les index sont utilisés lorsqu’ils sont disponibles. Si un index n’est pas encore utilisé dans l’ancienne version de l’application, il est généralement créé lors d’un temps d’arrêt planifié. Il en va de même lors de la suppression d’un index ou de la modification d’un index existant. Lors de la suppression d’un index, il cesse d’être disponible dès sa suppression.

### Gestion des index avec déploiements en continu {#index-management-with-rolling-deployments}

Avec des déploiements en continu, il n’existe pas de temps d’arrêt. Pendant un certain temps lors d’une mise à jour, l’ancienne version (par exemple, la version 1) de l’application et la nouvelle version (la version 2) s’exécutent simultanément sur le même référentiel. Si la version 1 nécessite qu’un certain index soit disponible, cet index ne doit pas être supprimé dans la version 2. L’index doit être supprimé ultérieurement, par exemple, dans la version 3. À ce stade, il est garanti que la version 1 de l’application n’est plus en cours d’exécution. En outre, les applications doivent être écrites de manière à ce que la version 1 fonctionne correctement, même si la version 2 est en cours d’exécution et si des index de la version 2 sont disponibles.

Une fois la mise à niveau vers la nouvelle version terminée, les anciens index peuvent être récupérés par le système. Les anciens index peuvent rester disponibles un certain temps afin d’accélérer les restaurations, le cas échéant.

Le tableau suivant présente cinq définitions d’index : l’index `cqPageLucene` est utilisé dans les deux versions tandis que index `damAssetLucene-custom-1` l’est uniquement dans la version 2.

>[!NOTE]
>
>L’index `<indexName>-custom-<customerVersionNumber>` est nécessaire pour qu’AEM as a Cloud Service puisse marquer cela comme un remplacement d’un index existant.

| Index | Index prêt à l’emploi | Utilisation dans la version 1 | Utilisation dans la version 2 |
|---|---|---|---|
| /oak:index/damAssetLucene | Oui | Oui | Non |
| /oak:index/damAssetLucene-custom-1 | Oui (personnalisé) | Non | Oui |
| /oak:index/acme.product-custom-1 | Non | Oui | Non |
| /oak:index/acme.product-custom-2 | Non | Non | Oui |
| /oak:index/cqPageLucene | Oui | Oui | Oui |

Le numéro de version est incrémenté chaque fois que l’index est modifié. Pour éviter que des noms d’index personnalisés n’entrent en conflit avec des noms d’index du produit lui-même, les index personnalisés et les modifications apportées aux index prêts à l’emploi doivent se terminer par `-custom-<number>`.

### Modifications apportées aux index prêts à l’emploi {#changes-to-out-of-the-box-indexes}

Lorsqu’Adobe modifie un index prêt à l’emploi tel que &quot;damAssetLucene&quot; ou &quot;cqPageLucene&quot;, un nouvel index nommé `damAssetLucene-2` ou `cqPageLucene-2` est créé. Ou, si l’index a déjà été personnalisé, la définition d’index personnalisé est fusionnée avec les modifications de l’index prêt à l’emploi, comme illustré ci-dessous. La fusion des modifications se produit automatiquement. Cela signifie que vous n’avez rien à faire si un index prêt à l’emploi change. Cependant, il est possible de personnaliser à nouveau l’index ultérieurement.

| Index | Index prêt à l’emploi | Utilisation dans la version 2 | Utilisation dans la version 3 |
|---|---|---|---|
| /oak:index/damAssetLucene-custom-1 | Oui (personnalisé) | Oui | Non |
| /oak:index/damAssetLucene-2-custom-1 | Oui (automatiquement fusionné à partir de damAssetLucene-custom-1 et damAssetLucene-2) | Non | Oui |
| /oak:index/cqPageLucene | Oui | Oui | Non |
| /oak:index/cqPageLucene-2 | Oui | Non | Oui |

Il est important de noter que les environnements peuvent se trouver dans différentes versions AEM. Par exemple : `dev` l&#39;environnement est sur la version `X+1` alors que l&#39;évaluation et la production sont toujours sur la version `X` et attendent d&#39;être mises à niveau vers la version `X+1` après que les tests requis sur `dev` ont été effectués. Si la version `X+1` est fournie avec une version plus récente d’un index de produit qui a été personnalisé et qu’une nouvelle personnalisation de cet index est requise, le tableau suivant explique les versions à définir sur les environnements en fonction de la version AEM :

| Environnement (AEM version de publication) | Version de l’index de produit | Version d’index personnalisé existante | Nouvelle version d’index personnalisée |
|-----------------------------------|-----------------------|-------------------------------|----------------------------|
| Dev (X+1) | damAssetLucene-11 | damAssetLucene-11-custom-1 | damAssetLucene-11-custom-2 |
| Stage (X) | damAssetLucene-10 | damAssetLucene-10-custom-1 | damAssetLucene-10-custom-2 |
| Prod (X) | damAssetLucene-10 | damAssetLucene-10-custom-1 | damAssetLucene-10-custom-2 |


### Limites actuelles {#current-limitations}

La gestion des index n’est prise en charge que pour les index de type `lucene`, avec la `compatVersion` définie sur `2`. En interne, d’autres index peuvent être configurés et utilisés pour les requêtes, par exemple les index Elasticsearch. Les requêtes écrites sur l’index `damAssetLucene` peuvent, sur AEM as a Cloud Service, être exécutées sur une version Elasticsearch de cet index. Cette différence est invisible pour l’utilisateur de l’application, mais certains outils tels que la fonction `explain` signalent un index différent. Pour connaître les différences entre les index Lucene et Elasticsearch, consultez [la documentation d’Elasticsearch dans Apache Jackrabbit Oak](https://jackrabbit.apache.org/oak/docs/query/elastic.html). Les index Elasticsearch ne peuvent pas et n’ont pas besoin d’être configurés directement par les client(e)s.

Seuls les analyseurs intégrés sont pris en charge (c’est-à-dire les analyseurs fournis avec le produit). Les analyseurs personnalisés ne sont pas pris en charge.

Actuellement, l’indexation du contenu de `/oak:index` n’est pas prise en charge.

Pour de meilleures performances opérationnelles, les index ne doivent pas être trop volumineux. La taille totale de tous les index peut servir de guide. Si cette taille augmente de plus de 100 % après l’ajout d’index personnalisés et si les index standard ont été ajustés sur un environnement de développement, les définitions d’index personnalisées doivent être ajustées. AEM as a Cloud Service peut empêcher le déploiement d’index qui auraient un impact négatif sur la stabilité et les performances du système.

### Ajouter un index {#adding-an-index}

Pour ajouter un index entièrement personnalisé nommé « `/oak:index/acme.product-custom-1` » à utiliser dans une nouvelle version de l’application et ultérieurement, l’index doit être configuré comme suit :

`acme.product-1-custom-1`

Cette opération consiste à ajouter un identifiant personnalisé au nom de l’index, suivi d’un point (**`.`**). L’identifiant doit comporter de 2 à 5 caractères.

Comme ci-dessus, cette configuration garantit que l’index n’est utilisé que par la nouvelle version de l’application.

### Modifier un index {#changing-an-index}

Lorsqu’un index existant est modifié, un nouvel index doit être ajouté avec la définition d’index modifiée. Par exemple, imaginons que l’index existant « `/oak:index/acme.product-custom-1` » a été modifié. L’ancien index est stocké sous `/oak:index/acme.product-custom-1` et le nouvel index sous `/oak:index/acme.product-custom-2`.

L’ancienne version de l’application utilise la configuration suivante :

`/oak:index/acme.product-custom-1`

La nouvelle version de l’application utilise la configuration suivante (modifiée) :

`/oak:index/acme.product-custom-2`

>[!NOTE]
>
>Les définitions d’index dans AEM as a Cloud Service peuvent ne pas correspondre entièrement aux définitions d’index sur une instance de développement locale. L’instance de développement ne dispose pas d’une configuration Tika, alors que les instances AEM as a Cloud Service en ont une. Si vous personnalisez un index avec une configuration Tika, conservez cette dernière.

### Annuler une modification {#undoing-a-change}

Parfois, il devient nécessaire d’annuler une modification dans une définition d’index. Cela peut se produire en raison d’une erreur involontaire ou parce que la modification n’est plus requise. Prenez par exemple la définition d’index `damAssetLucene-8-custom-3,` qui a été créée par erreur et qui a déjà été déployée. Par conséquent, vous souhaitez revenir à la définition d’index précédente, `damAssetLucene-8-custom-2.` Pour ce faire, vous devez introduire un nouvel index nommé `damAssetLucene-8-custom-4` qui incorpore la définition de l’index précédent, `damAssetLucene-8-custom-2.`

### Suppression d’un index {#removing-an-index}

Les éléments suivants s’appliquent uniquement aux index personnalisés. Les index de produit ne peuvent pas être supprimés car ils sont utilisés par AEM.

Un index personnalisé peut être supprimé dans une version ultérieure de l’application client, en le supprimant du référentiel client. Un index qui est supprimé du référentiel n’est pas utilisé pour les requêtes dans AEM, bien qu’il puisse encore être présent dans les instances pendant un certain temps. Il existe un mécanisme de nettoyage qui s’exécute régulièrement pour nettoyer les anciennes versions des index des instances.

## Optimisations des index et des requêtes {#index-query-optimizations}

Apache Jackrabbit Oak offre des configurations d’index flexibles pour gérer efficacement les requêtes de recherche. Les index sont particulièrement importants pour les référentiels les plus volumineux. Assurez-vous que toutes les requêtes sont soutenues par un index approprié. Les requêtes sans index approprié peuvent lire des milliers de nœuds qui sont ensuite consignés en tant qu’avertissements.

Veuillez consulter [ce document](query-and-indexing-best-practices.md) pour en savoir plus sur la manière dont les requêtes et les index peuvent être optimisés.
