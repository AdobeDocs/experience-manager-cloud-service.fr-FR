---
title: Recherche et indexation de contenu
description: Découvrez la recherche et l’indexation de contenu dans AEM as a Cloud Service.
exl-id: 4fe5375c-1c84-44e7-9f78-1ac18fc6ea6b
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: tm+mt
source-wordcount: '2324'
ht-degree: 39%

---

# Recherche et indexation de contenu {#indexing}

## Changements dans AEM as a Cloud Service {#changes-in-aem-as-a-cloud-service}

Avec AEM as a Cloud Service, Adobe s’éloigne d’un modèle centré sur les instances AEM pour passer à une vue basée sur les services avec des conteneurs n-x pilotés par des pipelines CI/CD dans Cloud Manager. Au lieu de configurer et de gérer les index sur des instances AEM uniques, la configuration d’index doit être spécifiée avant un déploiement. Les changements de configuration dans la production enfreignent clairement les politiques CI/CD. Il en va de même pour les changements d’index, car ceux-ci peuvent avoir un impact sur la stabilité et les performances du système s’ils ne sont pas testés et réindexés avant leur mise en production.

Voici la liste des principaux changements par rapport à AEM version 6.5 et antérieure :

1. Les utilisateurs n’ont plus accès au gestionnaire d’index d’une seule instance AEM pour déboguer, configurer ou gérer l’indexation. Le gestionnaire d’index n’est utilisé que pour le développement local et les déploiements sur site.
1. Les utilisateurs ne modifient plus les index sur une seule instance AEM et n’ont plus à se soucier des contrôles de cohérence ou de la réindexation.
1. En règle générale, les modifications d’index sont initiées avant de passer en production afin de ne pas contourner les passerelles de qualité dans les pipelines CI/CD de Cloud Manager et de ne pas affecter les indicateurs de performance clés métier en production.
1. Toutes les mesures associées, y compris les performances de recherche en production, sont disponibles pour les clients au moment de l’exécution afin de fournir une vue d’ensemble des sujets de recherche et d’indexation.
1. Les clients peuvent configurer des alertes selon leurs besoins.
1. Les SRE surveillent l’intégrité du système 24/7 et prennent des mesures dès que possible.
1. La configuration de l’index est modifiée par le biais de déploiements. Les modifications apportées à la définition de l’index sont configurées comme les autres modifications apportées au contenu.
1. À un niveau élevé sur AEM as a Cloud Service, avec l’introduction de la [modèle de déploiement en continu](#index-management-using-rolling-deployments), il existe deux ensembles d’index : un pour l’ancienne version et un autre pour la nouvelle version.
1. Les clients peuvent déterminer si la tâche d’indexation est terminée sur la page de génération de Cloud Manager et reçoivent une notification lorsque la nouvelle version est prête à recevoir le trafic.

Restrictions :

* Actuellement, la gestion des index dans AEM as a Cloud Service n’est prise en charge que pour les index de type `lucene`.
* Seuls les analyseurs standard sont pris en charge (c’est-à-dire ceux fournis avec le produit). Les analyseurs personnalisés ne sont pas pris en charge.
* En interne, d’autres index peuvent être configurés et utilisés pour les requêtes. Par exemple, les requêtes écrites selon l’index `damAssetLucene` peuvent, sur Skyline, être exécutées par rapport à une version Elasticsearch de cet index. Cette différence n’est généralement pas visible par l’application et l’utilisateur. Cependant, certains outils tels que la fonction `explain` rapport d’un index différent. Pour connaître les différences entre les index Lucene et les index Elastic, consultez [la documentation Elastic dans Apache Jackrabbit Oak](https://jackrabbit.apache.org/oak/docs/query/elastic.html). Les clients n’ont pas besoin ni ne peuvent configurer directement les index Elasticsearch.
* Recherche de vecteurs de fonctionnalités similaires (`useInSimilarity = true`) n’est pas pris en charge.

## Utilisation {#how-to-use}

Les définitions d’index peuvent être classées en trois principaux cas d’utilisation, comme suit :

1. **Ajouter** une nouvelle définition d’index personnalisée.
2. **Mettre à jour** une définition d’index existante en ajoutant une nouvelle version.
3. **Supprimer** une définition d’index qui n’est plus nécessaire.

Pour les points 1 et 2 ci-dessus, vous devez créer une définition d’index dans le cadre de votre base de code personnalisé dans le calendrier de publication Cloud Manager correspondant. Pour plus d’informations, voir [Déploiement sur AEM as a Cloud Service](/help/implementing/deploying/overview.md) la documentation.

## Noms d’index {#index-names}

Une définition d’index peut appartenir à l’une des catégories suivantes :

1. Index prêt à l’emploi. Par exemple : `/oak:index/cqPageLucene-2` ou `/oak:index/damAssetLucene-8`.

2. Personnalisation d’un index prêt à l’emploi. Elles sont indiquées par un ajout `-custom-` suivi d’un identifiant numérique au nom de l’index d’origine. Par exemple : `/oak:index/damAssetLucene-8-custom-1`.

3. Index entièrement personnalisé : il est possible de créer un index entièrement nouveau à partir de zéro. Leur nom doit comporter un préfixe pour éviter les conflits de noms. Par exemple : `/oak:index/acme.product-1-custom-2`, où le préfixe est `acme.`

## Préparation de la nouvelle définition d’index {#preparing-the-new-index-definition}

>[!NOTE]
>
>Si vous personnalisez un index prêt à l’emploi, par exemple `damAssetLucene-8`, copiez la dernière définition d’index d’usine à partir d’un *Environnement Cloud Service* à l’aide du gestionnaire de packages CRX DE (`/crx/packmgr/`). Renommez-le en `damAssetLucene-8-custom-1` (ou version ultérieure) et ajoutez vos personnalisations dans le fichier XML. Ainsi, les configurations requises ne sont pas supprimées par inadvertance. Par exemple, le nœud `tika` sous `/oak:index/damAssetLucene-8/tika` est requis dans l’index personnalisé du service cloud. Il n’existe pas dans le SDK *Cloud.

Pour les personnalisations d’un index prêt à l’emploi, préparez un nouveau package contenant la définition d’index actuelle qui suit ce modèle de dénomination :

`<indexName>-<productVersion>-custom-<customVersion>`

Pour un index entièrement personnalisé, préparez un nouveau package de définition d’index qui contient la définition d’index qui suit ce modèle de dénomination :

`<prefix>.<indexName>-<productVersion>-custom-<customVersion>`

<!-- Alexandru: temporarily drafting this statement due to CQDOC-17701

The package from the above sample is built as `com.adobe.granite:new-index-content:zip:1.0.0-SNAPSHOT`. -->

>[!NOTE]
>
>Tout module de contenu contenant des définitions d’index doit avoir les propriétés suivantes définies dans le fichier de propriétés du module de contenu, situé dans `<package_name>/META-INF/vault/properties.xml`:
>
> * `noIntermediateSaves=true`
>
> * `allowIndexDefinitions=true`

## Déploiement de définitions d’index personnalisées {#deploying-custom-index-definitions}

Pour illustrer le déploiement d’une version personnalisée de l’index prêt à l’emploi `damAssetLucene-8`, nous vous fournirons un guide détaillé. Dans cet exemple, nous allons le renommer en `damAssetLucene-8-custom-1`. Puis le processus est le suivant :

1. Créez un dossier avec le nom d’index mis à jour dans la `ui.apps` directory:
   * Exemple : `ui.apps/src/main/content/jcr_root/_oak_index/damAssetLucene-8-custom-1/`

2. Ajout d’un fichier de configuration `.content.xml` avec les configurations personnalisées dans le dossier nouvellement créé. Voici un exemple de personnalisation : Nom de fichier : `ui.apps/src/main/content/jcr_root/_oak_index/damAssetLucene-8-custom-1/.content.xml`

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

3. Ajoutez une entrée au filtre FileVault dans `ui.apps/src/main/content/META-INF/vault/filter.xml`:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <workspaceFilter version="1.0">
       ...
       <filter root="/oak:index/damAssetLucene-8-custom-1"/> 
   </workspaceFilter>
   ```

4. Ajoutez un fichier de configuration pour Apache Tika dans : `ui.apps/src/main/content/jcr_root/_oak_index/damAssetLucene-8-custom-1/tika/config.xml`:

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

Il est vivement recommandé d’utiliser version >= `1.3.2` du Jackrabbit `filevault-package-maven-plugin`. Les étapes pour l’intégrer à votre projet sont les suivantes :

1. Mettre à jour la version au niveau supérieur `pom.xml`:

   ```xml
   <plugin>
       <groupId>org.apache.jackrabbit</groupId>
           <artifactId>filevault-package-maven-plugin</artifactId>
           ...
           <version>1.3.2</version>
       ...
   </plugin>
   ```

2. Ajoutez ce qui suit au niveau supérieur. `pom.xml`:

   ```xml
   <jackrabbit-packagetype>
       <options>   
           <immutableRootNodeNames>apps,libs,oak:index</immutableRootNodeNames>
       </options>
   </jackrabbit-packagetype>
   ```

   Voici un exemple des principaux niveaux du projet : `pom.xml` avec les configurations mentionnées ci-dessus :

   Nom de fichier: `pom.xml`

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

3. Dans `ui.apps/pom.xml` et `ui.apps.structure/pom.xml` il est nécessaire d’activer la fonction `allowIndexDefinitions` et `noIntermediateSaves` dans le `filevault-package-maven-plugin`. Activation `allowIndexDefinitions` autorise les définitions d’index personnalisées, tandis que `noIntermediateSaves` s’assure que les configurations sont ajoutées de manière atomique.

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

4. Ajouter un filtre pour `/oak:index` in `ui.apps.structure/pom.xml`:

   ```xml
   <filters>
       ...
       <filter><root>/oak:index</root></filter>
   </filters>
   ```

Après avoir ajouté la nouvelle définition d’index, déployez la nouvelle application à l’aide de Cloud Manager. Ce déploiement lance deux tâches, chargées respectivement d’ajouter (et de fusionner si nécessaire) les définitions d’index à MongoDB et Azure Segment Store pour création et publication. Avant le commutateur, les référentiels sous-jacents font l’objet d’une réindexation avec les définitions d’index mises à jour.

>[!TIP]
>
>Pour plus de détails sur la structure de package requise pour AEM as a Cloud Service, reportez-vous au document [Structure de projets AEM](/help/implementing/developing/introduction/aem-project-content-package-structure.md).

## Gestion des index à l’aide de déploiements en continu {#index-management-using-rolling-deployments}

### Qu’est-ce que la gestion des index ? {#what-is-index-management}

La gestion des index consiste à ajouter, supprimer et modifier des index. Changer la *définition* d’un index est rapide, mais appliquer le changement (opération souvent appelée « création d’un index » ou, pour les index existants, « réindexation ») nécessite du temps. Elle n’est pas instantanée : le référentiel doit être analysé pour que les données soient indexées.

### Que sont les déploiements en continu ? {#what-are-rolling-deployments}

Un déploiement en continu peut réduire les temps d’arrêt. Il autorise également des mises à niveau sans interruption de service et des restaurations rapides. L’ancienne version de l’application s’exécute en même temps que la nouvelle version de l’application.

### Zones en lecture seule et en lecture-écriture {#read-only-and-read-write-areas}

Certaines zones du référentiel (parties en lecture seule du référentiel) peuvent être différentes dans l’ancienne et dans la nouvelle version de l’application. Les zones en lecture seule du référentiel sont généralement `/app` et `/libs`. Dans l’exemple suivant, des italiques sont utilisés pour marquer les zones en lecture seule, tandis que du gras est utilisé pour les zones en lecture-écriture.

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

### Gestion des index sans déploiement en continu {#index-management-without-rolling-deployments}

Lors du développement ou de l’utilisation d’installations on-premise, les index peuvent être ajoutés, supprimés ou modifiés au moment de l’exécution. Les index sont utilisés lorsqu’ils sont disponibles. Si un index n’est pas encore utilisé dans l’ancienne version de l’application, il est généralement créé lors d’une interruption planifiée. Il en va de même lors de la suppression d’un index ou de la modification d’un index existant. Lors de la suppression d’un index, celui-ci devient indisponible lorsqu’il est supprimé.

### Gestion des index avec déploiements en continu {#index-management-with-rolling-deployments}

Avec les déploiements continus, il n’y a pas de temps d’arrêt. Pendant un certain temps lors d’une mise à jour, l’ancienne version (par exemple, la version 1) de l’application et la nouvelle version (la version 2) s’exécutent simultanément sur le même référentiel. Si la version 1 nécessite qu’un certain index soit disponible, cet index ne doit pas être supprimé dans la version 2. L’index doit être supprimé ultérieurement, par exemple dans la version 3, auquel cas il est garanti que la version 1 de l’application ne s’exécute plus. En outre, les applications doivent être écrites de manière à ce que la version 1 fonctionne correctement, même si la version 2 est en cours d’exécution et si des index de la version 2 sont disponibles.

Une fois la mise à niveau vers la nouvelle version terminée, les anciens index peuvent être récupérés par le système. Les anciens index peuvent rester un certain temps afin d’accélérer les restaurations (si une restauration doit être nécessaire).

Le tableau suivant présente cinq définitions d’index : l’index `cqPageLucene` est utilisé dans les deux versions tandis que index `damAssetLucene-custom-1` l’est uniquement dans la version 2.

>[!NOTE]
>
>La variable `<indexName>-custom-<customerVersionNumber>` est nécessaire pour qu’AEM as a Cloud Service puisse le marquer comme un remplacement d’un index existant.

| Index | Index prêt à l’emploi | Utilisation dans la version 1 | Utilisation dans la version 2 |
|---|---|---|---|
| /oak:index/damAssetLucene | Oui | Oui | Non |
| /oak:index/damAssetLucene-custom-1 | Oui (personnalisé) | Non | Oui |
| /oak:index/acme.product-custom-1 | Non | Oui | Non |
| /oak:index/acme.product-custom-2 | Non | Non | Oui |
| /oak:index/cqPageLucene | Oui | Oui | Oui |

Le numéro de version est incrémenté chaque fois que l’index est modifié. Pour éviter que des noms d’index personnalisés n’entrent en conflit avec des noms d’index du produit lui-même, les index personnalisés et les modifications apportées aux index prêts à l’emploi doivent se terminer par `-custom-<number>`.

### Modifications apportées aux index prêts à l’emploi {#changes-to-out-of-the-box-indexes}

Après que Adobe a modifié un index prêt à l’emploi tel que &quot;damAssetLucene&quot; ou &quot;cqPageLucene&quot;, un nouvel index nommé `damAssetLucene-2` ou `cqPageLucene-2` est créée. Ou, si l’index a déjà été personnalisé, la définition d’index personnalisé est fusionnée avec les modifications de l’index prêt à l’emploi, comme illustré ci-dessous. La fusion des modifications se produit automatiquement. Cela signifie que vous n’avez rien à faire si un index prêt à l’emploi change. Cependant, il est possible de personnaliser à nouveau l’index ultérieurement.

| Index | Index prêt à l’emploi | Utilisation dans la version 2 | Utilisation dans la version 3 |
|---|---|---|---|
| /oak:index/damAssetLucene-custom-1 | Oui (personnalisé) | Oui | Non |
| /oak:index/damAssetLucene-2-custom-1 | Oui (automatiquement fusionné à partir de damAssetLucene-custom-1 et damAssetLucene-2) | Non | Oui |
| /oak:index/cqPageLucene | Oui | Oui | Non |
| /oak:index/cqPageLucene-2 | Oui | Non | Oui |

### Limites actuelles {#current-limitations}

La gestion des index est uniquement prise en charge pour les index de type `lucene`, avec `compatVersion` défini sur `2`. En interne, d’autres index peuvent être configurés et utilisés pour les requêtes, par exemple les index Elasticsearch. Les requêtes écrites sur l’index `damAssetLucene` peuvent être exécutées sur une version Elasticsearch de cet index dans AEM as a Cloud Service. Cette différence est invisible pour l’utilisateur final de l’application, mais certains outils tels que le `explain` La fonction signale un index différent. Pour connaître les différences entre les index Lucene et Elasticsearch, consultez [la documentation d’Elasticsearch dans Apache Jackrabbit Oak](https://jackrabbit.apache.org/oak/docs/query/elastic.html). Les index Elasticsearch ne peuvent pas et n’ont pas besoin d’être configurés directement par les client(e)s.

Seuls les analyseurs intégrés sont pris en charge (c’est-à-dire ceux fournis avec le produit). Les analyseurs personnalisés ne sont pas pris en charge.

Pour de meilleures performances opérationnelles, les index ne doivent pas être trop volumineux. La taille totale de tous les index peut servir de guide. Si cette taille augmente de plus de 100 % après l’ajout d’index personnalisés et si les index standard ont été ajustés sur un environnement de développement, les définitions d’index personnalisés doivent être ajustées. AEM as a Cloud Service peut empêcher le déploiement d’index qui auraient un impact négatif sur la stabilité et les performances du système.

### Ajout d’un index {#adding-an-index}

Pour ajouter un index entièrement personnalisé nommé `/oak:index/acme.product-custom-1`, à utiliser dans une nouvelle version de l’application et ultérieurement, l’index doit être configuré comme suit :

`acme.product-1-custom-1`

Cette configuration fonctionne en ajoutant un identifiant personnalisé au nom de l’index, suivi d’un point (**`.`**). L’identifiant doit comporter de 2 à 5 caractères.

Comme ci-dessus, cette configuration garantit que l’index n’est utilisé que par la nouvelle version de l’application.

### Modification d’un index {#changing-an-index}

Lorsqu’un index existant est modifié, un nouvel index doit être ajouté avec la définition d’index modifiée. Par exemple, imaginons que l’index existant « `/oak:index/acme.product-custom-1` » a été modifié. L’ancien index est stocké sous `/oak:index/acme.product-custom-1` et le nouvel index sous `/oak:index/acme.product-custom-2`.

L’ancienne version de l’application utilise la configuration suivante :

`/oak:index/acme.product-custom-1`

La nouvelle version de l’application utilise la configuration suivante (modifiée) :

`/oak:index/acme.product-custom-2`

>[!NOTE]
>
>Les définitions d’index dans AEM as a Cloud Service peuvent ne pas correspondre entièrement aux définitions d’index sur une instance de développement locale. L’instance de développement ne dispose pas d’une configuration Tika, alors que les instances d’AEM as a Cloud Service en ont une. Si vous personnalisez un index avec une configuration Tika, conservez la configuration Tika.

### Annulation d’une modification {#undoing-a-change}

Parfois, il devient nécessaire d’annuler une modification dans une définition d’index. Cela peut se produire en raison d’une erreur involontaire ou parce que la modification n’est plus requise. Prenez, par exemple, la définition d’index. `damAssetLucene-8-custom-3,` qui a été créé par erreur et a déjà été déployé. Par conséquent, vous souhaitez revenir à la définition d’index précédente, `damAssetLucene-8-custom-2.` Pour ce faire, vous devez introduire un nouvel index nommé `damAssetLucene-8-custom-4` qui intègre la définition de l&#39;index précédent, `damAssetLucene-8-custom-2.`

### Suppression d’un index {#removing-an-index}

Les éléments suivants s’appliquent uniquement aux index personnalisés. Les index de produit ne peuvent pas être supprimés car ils sont utilisés par AEM.

Si un index est supprimé dans une version ultérieure de l’application, vous pouvez définir un index vide (un index vide qui n’est jamais utilisé et ne contient aucune donnée), avec un nouveau nom. Pour cet exemple, vous pouvez le nommer `/oak:index/acme.product-custom-3`. Ce nom remplace l’index `/oak:index/acme.product-custom-2`. Après `/oak:index/acme.product-custom-2` est supprimé par le système, l’index vide. `/oak:index/acme.product-custom-3` peut ensuite être supprimé. Voici un exemple d’index vide de ce type :

```xml
<acme.product-custom-3
        jcr:primaryType="oak:QueryIndexDefinition"
        async="async"
        compatVersion="2"
        includedPaths="/dummy"
        queryPaths="/dummy"
        type="lucene">
        <indexRules jcr:primaryType="nt:unstructured">
            <rep:root jcr:primaryType="nt:unstructured">
                <properties jcr:primaryType="nt:unstructured">
                    <dummy
                        jcr:primaryType="nt:unstructured"
                        name="dummy"
                        propertyIndex="{Boolean}true"/>
                </properties>
            </rep:root>
        </indexRules>
</acme.product-custom-3>
```

S’il n’est plus nécessaire de personnaliser un index prêt à l’emploi, vous devez copier la définition d’index prête à l’emploi. Par exemple, si vous avez déjà déployé `damAssetLucene-8-custom-3`, mais que vous n’avez plus besoin des personnalisations et que vous souhaitez revenir à l’index `damAssetLucene-8` par défaut, vous devez ajouter un index `damAssetLucene-8-custom-4` contenant la définition d’index de `damAssetLucene-8`.

## Optimisations des index et des requêtes {#index-query-optimizations}

Apache Jackrabbit Oak offre des configurations d’index flexibles pour gérer efficacement les requêtes de recherche. Les index sont particulièrement importants pour les référentiels les plus volumineux. Assurez-vous que toutes les requêtes sont sauvegardées par un index approprié. Les requêtes sans index approprié peuvent lire des milliers de noeuds, qui sont ensuite consignés comme avertissement.

Voir [ce document](query-and-indexing-best-practices.md) pour plus d’informations sur la manière dont les requêtes et les index peuvent être optimisés.
