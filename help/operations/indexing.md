---
title: Recherche et indexation de contenu
description: Recherche et indexation de contenu
exl-id: 4fe5375c-1c84-44e7-9f78-1ac18fc6ea6b
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '2481'
ht-degree: 82%

---

# Recherche et indexation de contenu {#indexing}

## Changements dans AEM as a Cloud Service {#changes-in-aem-as-a-cloud-service}

Avec AEM as a Cloud Service, Adobe s’éloigne d’un modèle centré sur les instances AEM pour passer à une vue basée sur les services avec des conteneurs n-x pilotés par des pipelines CI/CD dans Cloud Manager. Au lieu de configurer et de gérer les index sur des instances AEM uniques, la configuration d’index doit être spécifiée avant un déploiement. Les changements de configuration dans la production enfreignent clairement les politiques CI/CD. Il en va de même pour les changements d’index, car ceux-ci peuvent avoir un impact sur la stabilité et les performances du système s’ils ne sont pas testés et réindexés avant leur mise en production.

Voici la liste des principaux changements par rapport à AEM version 6.5 et antérieure :

1. Les utilisateurs n’ont plus accès au gestionnaire d’index d’une seule instance AEM pour déboguer, configurer ou gérer l’indexation. Le gestionnaire d’index n’est utilisé que pour le développement local et les déploiements sur site.
1. Les utilisateurs ne changent pas d’index sur une seule instance AEM et n’ont plus à s’inquiéter des vérifications de cohérence ni de la réindexation.
1. En règle générale, les modifications d’index sont initiées avant de passer en production afin de ne pas contourner les passerelles de qualité dans les pipelines CI/CD de Cloud Manager et de ne pas affecter les indicateurs de performance clés métier en production.
1. Toutes les mesures associées, y compris les performances de recherche en production, sont disponibles pour les clients au moment de l’exécution afin de fournir une vue d’ensemble des sujets de recherche et d’indexation.
1. Les clients peuvent configurer des alertes en fonction de leurs besoins.
1. Les SRE surveillent l’intégrité du système 24 heures sur 24, 7 jours sur 7 et prendront les mesures nécessaires le plus tôt possible.
1. La configuration de l’index est modifiée par le biais de déploiements. Les modifications apportées à la définition de l’index sont configurées comme les autres modifications apportées au contenu.
1. À un niveau élevé sur AEM as a Cloud Service, avec l’introduction de la [modèle de déploiement en continu](#index-management-using-rolling-deployments) deux ensembles d’index existent : un jeu pour l’ancienne version et un autre pour la nouvelle version.
1. Les clients peuvent voir si la tâche d’indexation est terminée sur la page de version Cloud Manager et recevront une notification lorsque la nouvelle version sera prête à recevoir le trafic.

Restrictions :

* Actuellement, la gestion des index dans AEM as a Cloud Service n’est prise en charge que pour les index de type `lucene`.
* Seuls les analyseurs standard sont pris en charge (c’est-à-dire ceux fournis avec le produit). Les analyseurs personnalisés ne sont pas pris en charge.
* En interne, d’autres index peuvent être configurés et utilisés pour les requêtes. Par exemple, les requêtes écrites selon l’index `damAssetLucene` peuvent, sur Skyline, être exécutées par rapport à une version Elasticsearch de cet index. Cette différence n’est généralement pas visible par l’application et par l’utilisateur, mais certains outils tels que la fonctionnalité `explain` signalent un index différent. Pour connaître les différences entre les index Lucene et les index Elastic, consultez [la documentation Elastic dans Apache Jackrabbit Oak](https://jackrabbit.apache.org/oak/docs/query/elastic.html). Les clients n’ont pas besoin de configurer directement les index Elasticsearch et ne peuvent pas le faire.

## Utilisation {#how-to-use}

La définition des index peut comprendre les trois cas d’utilisation suivants :

1. Ajouter une nouvelle définition d’index client.
1. Mettre à jour une définition d’index existante. Cela signifie ajouter une nouvelle version d’une définition d’index existante..
1. Supprimer un index existant redondant ou obsolète.

Pour les points 1 et 2 ci-dessus, vous devez créer une définition d’index dans le cadre de votre base de code personnalisé dans le calendrier de publication Cloud Manager correspondant. Pour plus d’informations, reportez-vous à [Déploiement vers AEM as a Cloud Service](/help/implementing/deploying/overview.md).

## Noms d’index {#index-names}

Une définition d’index peut être :

1. Index prêt à l’emploi. Exemple : `/oak:index/cqPageLucene-2`.
1. Personnalisation d’un index prêt à l’emploi. Ces personnalisations sont définies par le client. Exemple : `/oak:index/cqPageLucene-2-custom-1`.
1. Index entièrement personnalisé. Exemple : `/oak:index/acme.product-1-custom-2`. Pour éviter les collisions de noms, il est nécessaire que les index entièrement personnalisés comportent un préfixe, par exemple, `acme.`.

Notez que la personnalisation d’un index prêt à l’emploi, ainsi que les index entièrement personnalisés, doivent contenir `-custom-`. Seuls les index entièrement personnalisés doivent commencer par un préfixe.

## Préparation de la nouvelle définition d’index {#preparing-the-new-index-definition}

>[!NOTE]
>
>Si vous personnalisez un index prêt à l’emploi, par exemple `damAssetLucene-6`, copiez la dernière définition d’index d’usine à partir d’un *Environnement Cloud Service* à l’aide du gestionnaire de packages CRX DE (`/crx/packmgr/`). Renommez ensuite la configuration, par exemple en `damAssetLucene-6-custom-1`, puis ajoutez ensuite vos personnalisations. Vous vous assurez ainsi que les configurations requises ne sont pas supprimées par inadvertance. Par exemple, le nœud `tika` sous `/oak:index/damAssetLucene-6/tika` est requis dans l’index personnalisé du service cloud. Il n’existe pas dans le SDK *Cloud.

Vous devez préparer un nouveau package de définition d’index qui contient la définition d’index réelle, en suivant ce modèle de dénomination :

`<indexName>[-<productVersion>]-custom-<customVersion>`

qui doit ensuite être placé dans `ui.apps/src/main/content/jcr_root`. Toutes les définitions d’index personnalisées doivent être stockées sous `/oak:index`.

Le filtre du package doit être défini de sorte que les index existants (index prêts à l’emploi) soient conservés. Dans le fichier `ui.apps/src/main/content/META-INF/vault/filter.xml`, chaque index personnalisé doit être répertorié, par exemple sous le nom de `<filter root="/oak:index/damAssetLucene-6-custom-1"/>`. Si la version de l’index est modifiée ultérieurement, le filtre doit être ajusté.

<!-- Alexandru: temporarily drafting this statement due to CQDOC-17701

The package from the above sample is built as `com.adobe.granite:new-index-content:zip:1.0.0-SNAPSHOT`. -->

>[!NOTE]
>
>La propriété suivante doit être définie pour tout module de contenu contenant des définitions d’index dans le fichier de propriétés du package de contenu, situé à l’emplacement `/META-INF/vault/properties.xml` :
>
>`noIntermediateSaves=true`

## Déploiement de définitions d’index {#deploying-index-definitions}

Les définitions d’index sont désormais marquées comme étant personnalisées et versionnées :

* La définition d’index elle-même (par exemple, `/oak:index/ntBaseLucene-custom-1`)

Pour déployer un index personnalisé, la définition d’index (`/oak:index/definitionname`) doit être diffusée via `ui.apps`, à l’aide du processus de déploiement de Cloud Manager et via Git. Dans le filtre FileVault, par exemple, `ui.apps/src/main/content/META-INF/vault/filter.xml`, répertoriez individuellement chaque index personnalisé, par exemple, `<filter root="/oak:index/damAssetLucene-7-custom-1"/>`. La définition d’index personnalisée elle-même sera alors stockée dans le fichier `ui.apps/src/main/content/jcr_root/_oak_index/damAssetLucene-7-custom-1/.content.xml`, comme suit :

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:oak="https://jackrabbit.apache.org/oak/ns/1.0" xmlns:dam="http://www.day.com/dam/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:nt="http://www.jcp.org/jcr/nt/1.0" xmlns:rep="internal"
        jcr:primaryType="oak:QueryIndexDefinition"
        async="[async,nrt]"
        compatVersion="{Long}2"
        ...
        </indexRules>
        <tika jcr:primaryType="nt:unstructured">
            <config.xml jcr:primaryType="nt:file"/>
        </tika>
</jcr:root>
```

L’exemple ci-dessus contient une configuration pour Apache Tika. Le fichier de configuration Tika serait stocké sous `ui.apps/src/main/content/jcr_root/_oak_index/damAssetLucene-7-custom-1/tika/config.xml`.

### Configuration du projet

Selon la version du plug-in Jackrabbit Filevault Maven Package utilisée, une configuration supplémentaire est requise dans le projet. Lors de l’utilisation du plug-in de package Jackrabbit Filevault Maven version **1.1.6** ou plus récente, le fichier `pom.xml` doit contenir la section suivante dans la configuration du plug-in pour le `filevault-package-maven-plugin`, dans `configuration/validatorsSettings` (juste avant `jackrabbit-nodetypes`) :

```xml
<jackrabbit-packagetype>
    <options>
        <immutableRootNodeNames>apps,libs,oak:index</immutableRootNodeNames>
    </options>
</jackrabbit-packagetype>
```

En outre, dans ce cas, la version `vault-validation` doit être mise à niveau vers une version plus récente :

```xml
<dependency>
    <groupId>org.apache.jackrabbit.vault</groupId>
    <artifactId>vault-validation</artifactId>
    <version>3.5.6</version>
</dependency>
```

Ensuite, dans `ui.apps.structure/pom.xml` et `ui.apps/pom.xml`, la configuration du `filevault-package-maven-plugin` doit avoir les options `allowIndexDefinitions` et `noIntermediateSaves` activées. L’option `noIntermediateSaves` garantit que les configurations d’index sont ajoutées de manière atomique.

```xml
<groupId>org.apache.jackrabbit</groupId>
    <artifactId>filevault-package-maven-plugin</artifactId>
    <configuration>
        <allowIndexDefinitions>true</allowIndexDefinitions>
        <properties>
            <cloudManagerTarget>none</cloudManagerTarget>
            <noIntermediateSaves>true</noIntermediateSaves>
        </properties>
    ...
```

Dans `ui.apps.structure/pom.xml`, la section `filters` pour ce plug-in, doit contenir une racine de filtre comme suit :

```xml
<filter><root>/oak:index</root></filter>
```

Une fois la nouvelle définition d’index ajoutée, la nouvelle application doit être déployée via Cloud Manager. Lors du déploiement, deux tâches sont démarrées et sont chargées d’ajouter (et de fusionner si nécessaire) les définitions d’index à MongoDB et Azure Segment Store pour l’auteur et la publication, respectivement. Les référentiels sous-jacents sont réindexés avec les nouvelles définitions d’index, avant que la reprise du commutateur ne soit effectuée.

### REMARQUE

Si vous constatez l’erreur suivante dans la validation filevault <br>
`[ERROR] ValidationViolation: "jackrabbit-nodetypes: Mandatory child node missing: jcr:content [nt:base] inside node with types [nt:file]"` <br>
Vous pouvez ensuite suivre l’une des étapes suivantes pour résoudre le problème : <br>
1. Développez filevault vers la version 1.0.4 et ajoutez les éléments suivants au modèle pom de niveau supérieur :

```xml
<allowIndexDefinitions>true</allowIndexDefinitions>
```

Vous trouverez ci-dessous un exemple de l’emplacement de la configuration ci-dessus dans le modèle pom.

```xml
<plugin>
    <groupId>org.apache.jackrabbit</groupId>
    <artifactId>filevault-package-maven-plugin</artifactId>
    <configuration>
        <properties>
        ...
        </properties>
        ...
        <allowIndexDefinitions>true</allowIndexDefinitions>
        <repositoryStructurePackages>
        ...
        </repositoryStructurePackages>
        <dependencies>
        ...
        </dependencies>
    </configuration>
</plugin>
```

1. Désactivez la validation du type de noeud. Définissez la propriété suivante dans la section jackrabbit-nodetypes de la configuration du module externe filevault :

```xml
<isDisabled>true</isDisabled>
```

Vous trouverez ci-dessous un exemple de l’emplacement de la configuration ci-dessus dans le modèle pom.

```xml
<plugin>
    <groupId>org.apache.jackrabbit</groupId>
    <artifactId>filevault-package-maven-plugin</artifactId>
    ...
    <configuration>
    ...
        <validatorsSettings>
        ...
            <jackrabbit-nodetypes>
                <isDisabled>true</isDisabled>
            </jackrabbit-nodetypes>
        </validatorsSettings>
    </configuration>
</plugin>
```

>[!TIP]
>
>Pour plus de détails sur la structure de package requise pour AEM as a Cloud Service, reportez-vous au document [Structure de projets AEM](/help/implementing/developing/introduction/aem-project-content-package-structure.md).

## Gestion des index à l’aide de déploiements en continu {#index-management-using-rolling-deployments}

### Qu’est-ce que la gestion des index ? {#what-is-index-management}

La gestion des index consiste à ajouter, supprimer et modifier des index. Changer la *définition* d’un index est rapide, mais appliquer le changement (opération souvent appelée « création d’un index » ou, pour les index existants, « réindexation ») nécessite du temps. Cette opération n’est pas instantanée : le référentiel doit être analysé pour que les données soient indexées.

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

### Gestion des index sans déploiements en continu {#index-management-without-rolling-deployments}

Lors du développement ou de l’utilisation d’installations sur site, les index peuvent être ajoutés, supprimés ou modifiés au moment de l’exécution. Les index sont utilisés dès qu’ils sont disponibles. Si un index n’est pas encore censé être utilisé dans l’ancienne version de l’application, il est généralement créé lors d’un temps d’arrêt planifié. Il en va de même lors de la suppression d’un index ou de la modification d’un index existant. Lors de la suppression d’un index, celui-ci cesse d’être disponible dès sa suppression.

### Gestion des index avec déploiements en continu {#index-management-with-rolling-deployments}

Avec les déploiements continus, il n’y a pas de temps d’arrêt. Pendant un certain temps lors d’une mise à jour, l’ancienne version (par exemple, version 1) de l’application, ainsi que la nouvelle version (version 2), s’exécutent simultanément sur le même référentiel. Si la version 1 nécessite la disponibilité d&#39;un certain index, celui-ci ne doit pas être supprimé dans la version 2. L&#39;index doit être supprimé ultérieurement, par exemple dans la version 3. À ce stade, il est garanti que la version 1 de l&#39;application n&#39;est plus en cours d&#39;exécution. En outre, les applications doivent être écrites de manière à ce que la version 1 fonctionne correctement, même si la version 2 est en cours d’exécution et si des index de la version 2 sont disponibles.

Une fois la mise à niveau vers la nouvelle version terminée, les anciens index peuvent être récupérés par le système. Les anciens index peuvent rester un certain temps afin d’accélérer les restaurations (si une restauration doit être nécessaire).

Le tableau suivant présente cinq définitions d’index : l’index `cqPageLucene` est utilisé dans les deux versions tandis que index `damAssetLucene-custom-1` l’est uniquement dans la version 2.

>[!NOTE]
>
>`<indexName>-custom-<customerVersionNumber>` est nécessaire pour qu’AEM as a Cloud Service puisse marquer cela comme un remplacement d’un index existant.

| Index | Index prêt à l’emploi | Utilisation dans la version 1 | Utilisation dans la version 2 |
|---|---|---|---|
| /oak:index/damAssetLucene | Oui | Oui | Non |
| /oak:index/damAssetLucene-custom-1 | Oui (personnalisé) | Non | Oui |
| /oak:index/acme.product-custom-1 | Non | Oui | Non |
| /oak:index/acme.product-custom-2 | Non | Non | Oui |
| /oak:index/cqPageLucene | Oui | Oui | Oui |

Le numéro de version est incrémenté chaque fois que l’index est modifié. Pour éviter que des noms d’index personnalisés n’entrent en conflit avec des noms d’index du produit lui-même, les index personnalisés, ainsi que les modifications apportées aux index prêts à l’emploi, doivent se terminer par . `-custom-<number>`.

### Modifications apportées aux index prêts à l’emploi {#changes-to-out-of-the-box-indexes}

Une fois qu’Adobe a modifié un index prêt à l’emploi tel que « damAssetLucene » ou « cqPageLucene », un nouvel index nommé `damAssetLucene-2` ou `cqPageLucene-2` est créé ou, si l’index a déjà été personnalisé, la définition d’index personnalisé est fusionnée avec les modifications de l’index prêt à l’emploi, comme illustré ci-dessous. La fusion des modifications se produit automatiquement. Cela signifie que vous n’avez rien à faire si un index prêt à l’emploi change. Cependant, il est possible de personnaliser à nouveau l’index ultérieurement.

| Index | Index prêt à l’emploi | Utilisation dans la version 2 | Utilisation dans la version 3 |
|---|---|---|---|
| /oak:index/damAssetLucene-custom-1 | Oui (personnalisé) | Oui | Non |
| /oak:index/damAssetLucene-2-custom-1 | Oui (automatiquement fusionné à partir de damAssetLucene-custom-1 et damAssetLucene-2) | Non | Oui |
| /oak:index/cqPageLucene | Oui | Oui | Non |
| /oak:index/cqPageLucene-2 | Oui | Non | Oui |

### Limites actuelles {#current-limitations}

Actuellement, la gestion des index n’est prise en charge que pour les index de type `lucene`, avec la `compatVersion` définie sur `2`. En interne, d’autres index peuvent être configurés et utilisés pour les requêtes, par exemple les index Elasticsearch. Les requêtes écrites sur l’index `damAssetLucene` peuvent être exécutées sur une version Elasticsearch de cet index dans AEM as a Cloud Service. Cette différence n’est pas visible par l’utilisateur ou l’utilisatrice final(e) de l’application, mais certains outils tels que la fonctionnalité `explain` signalent un index différent. Pour connaître les différences entre les index Lucene et Elasticsearch, consultez [la documentation d’Elasticsearch dans Apache Jackrabbit Oak](https://jackrabbit.apache.org/oak/docs/query/elastic.html). Les index Elasticsearch ne peuvent pas et n’ont pas besoin d’être configurés directement par les client(e)s.

Seuls les analyseurs intégrés sont pris en charge (c’est-à-dire ceux fournis avec le produit). Les analyseurs personnalisés ne sont pas pris en charge.

Pour de meilleures performances opérationnelles, les index ne doivent pas être trop volumineux. La taille totale de tous les index peut être utilisée comme indice : si elle augmente de plus de 100 % après l’ajout d’index personnalisés et l’ajustement des index standards sur un environnement de développement, les définitions des index personnalisés doivent être ajustées. AEM as a Cloud Service peut empêcher le déploiement d’index qui auraient un impact négatif sur la stabilité et les performances du système.

### Ajout d’un index {#adding-an-index}

Pour ajouter un index entièrement personnalisé nommé « `/oak:index/acme.product-custom-1` » à utiliser dans une nouvelle version de l’application et ultérieurement, l’index doit être configuré comme suit :

`acme.product-1-custom-1`

Cette opération consiste à ajouter un identifiant personnalisé au nom de l’index, suivi d’un point (**`.`**). L’identifiant doit comporter entre 2 et 5 caractères.

Comme ci-dessus, cette règle garantit que l’index n’est utilisé que par la nouvelle version de l’application.

### Modification d’un index {#changing-an-index}

Lorsqu’un index existant est modifié, un nouvel index doit être ajouté avec la définition d’index modifiée. Par exemple, imaginons que l’index existant « `/oak:index/acme.product-custom-1` » a été modifié. L’ancien index est stocké sous `/oak:index/acme.product-custom-1` et le nouvel index sous `/oak:index/acme.product-custom-2`.

L’ancienne version de l’application utilise la configuration suivante :

`/oak:index/acme.product-custom-1`

La nouvelle version de l’application utilise la configuration suivante (modifiée) :

`/oak:index/acme.product-custom-2`

>[!NOTE]
>
>Les définitions d’index dans AEM as a Cloud Service peuvent ne pas correspondre entièrement aux définitions d’index sur une instance de développement locale. L’instance de développement ne dispose pas d’une configuration Tika, alors que les instances AEM as a Cloud Service en ont une. Si vous personnalisez un index avec une configuration Tika, conservez la configuration Tika.

### Annulation d’une modification {#undoing-a-change}

Parfois, une modification de la définition d’index doit être annulée. Les raisons peuvent être qu’un changement a été fait par erreur ou qu’un changement n’est plus nécessaire. Par exemple, la définition d’index `damAssetLucene-8-custom-3` a été créée par erreur et est déjà déployée. Pour cette raison, vous souhaiterez peut-être revenir à la définition d’index précédente `damAssetLucene-8-custom-2`. Pour ce faire, vous devez ajouter un nouvel index appelé `damAssetLucene-8-custom-4` contenant la définition de l’index précédent, `damAssetLucene-8-custom-2`.

### Suppression d’un index {#removing-an-index}

Les éléments suivants s’appliquent uniquement aux index personnalisés. Les index de produit ne peuvent pas être supprimés car ils sont utilisés par AEM.

Si un index doit être supprimé dans une version ultérieure de l’application, vous pouvez définir un index vide (un index vide qui n’est jamais utilisé et ne contient aucune donnée), avec un nouveau nom. Pour les besoins de cet exemple, vous pouvez le nommer `/oak:index/acme.product-custom-3`. Cette opération remplace l’index `/oak:index/acme.product-custom-2`. Une fois `/oak:index/acme.product-custom-2` supprimé par le système, l’index vide `/oak:index/acme.product-custom-3` peut également être supprimé. Voici un exemple d’index vide de ce type :

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

Apache Jackrabbit Oak offre des configurations d’index flexibles pour gérer efficacement les requêtes de recherche. Les index sont particulièrement importants pour les référentiels les plus volumineux. Assurez-vous que toutes les requêtes sont soutenues par un index approprié. Les requêtes sans index approprié peuvent lire des milliers de nœuds qui sont ensuite consignés en tant qu’avertissements.

Veuillez consulter [ce document](query-and-indexing-best-practices.md) pour en savoir plus sur la manière dont les requêtes et les index peuvent être optimisés.
