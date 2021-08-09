---
title: Recherche et indexation de contenu
description: Recherche et indexation de contenu
exl-id: 4fe5375c-1c84-44e7-9f78-1ac18fc6ea6b
source-git-commit: eae25dc48a7cd5d257e23b515f497588a13917ea
workflow-type: tm+mt
source-wordcount: '1780'
ht-degree: 100%

---

# Recherche et indexation de contenu {#indexing}

## Changements dans AEM as a Cloud Service {#changes-in-aem-as-a-cloud-service}

Avec AEM as a Cloud Service, Adobe s’éloigne d’un modèle centré sur les instances AEM pour passer à une vue basée sur les services avec des conteneurs n-x pilotés par des pipelines CI/CD dans Cloud Manager. Au lieu de configurer et de gérer les index sur des instances AEM uniques, la configuration d’index doit être spécifiée avant un déploiement. Les changements de configuration dans la production enfreignent clairement les politiques CI/CD. Il en va de même pour les changements d’index, car ceux-ci peuvent avoir un impact sur la stabilité et les performances du système s’ils ne sont pas testés et réindexés avant leur mise en production.

Voici la liste des principaux changements par rapport à AEM version 6.5 et antérieure :

1. Les utilisateurs n’ont plus accès au gestionnaire d’index d’une seule instance AEM pour déboguer, configurer ou gérer l’indexation. Le gestionnaire d’index n’est utilisé que pour le développement local et les déploiements sur site.

1. Les utilisateurs ne changent pas d’index sur une seule instance AEM et n’ont plus à s’inquiéter des vérifications de cohérence ni de la réindexation.

1. En général, les changements d’index sont amorcés avant le passage à la production afin de ne pas contourner les passerelles de qualité dans les pipelines CI/CD de Cloud Manager et de ne pas affecter les indicateurs de performance clés métier en production.

1. Toutes les mesures associées, y compris les performances de recherche en production, sont à la disposition des clients au moment de l’exécution afin de fournir une vue holistique sur les sujets de recherche et d’indexation.

1. Les clients pourront configurer des alertes en fonction de leurs besoins.

1. Les SRE surveillent l’intégrité du système 24 heures sur 24, 7 jours sur 7 et prendront les mesures nécessaires le plus tôt possible.

1. La configuration de l’index est modifiée par le biais de déploiements. Les modifications apportées à la définition de l’index sont configurées comme les autres modifications apportées au contenu.

1. À un niveau élevé dans AEM as a Cloud Service, avec l’introduction du [modèle de déploiement bleu/vert](#index-management-using-blue-green-deployments), deux ensembles d’index coexisteront : l’un pour l’ancienne version (bleu), et l’autre pour la nouvelle version (vert).

1. Les clients peuvent voir si la tâche d’indexation est terminée sur la page de version Cloud Manager et recevront une notification lorsque la nouvelle version sera prête à recevoir le trafic.

1. Limites : actuellement, la gestion des index dans AEM as a Cloud Service n’est prise en charge que pour les index de type lucene.

## Utilisation {#how-to-use}

La définition d’index peut comprendre les trois cas d’utilisation suivants :

1. Ajouter une nouvelle définition d’index client.
1. Mettre à jour une définition d’index existante. Cela signifie ajouter une nouvelle version d’une définition d’index existante.
1. Supprimer un index existant redondant ou obsolète.

Pour les points 1 et 2 ci-dessus, vous devez créer une définition d’index dans le cadre de votre base de code personnalisé dans le calendrier de publication Cloud Manager correspondant. Pour plus d’informations, reportez-vous à [Déploiement vers AEM as a Cloud Service](/help/implementing/deploying/overview.md).

### Préparation de la nouvelle définition d’index {#preparing-the-new-index-definition}

>[!NOTE]
>
>Si vous personnalisez un index prêt à l’emploi, par exemple `damAssetLucene-6`, copiez la dernière définition d’index prêt à l’emploi à partir d’un *environnement de Cloud Service* et ajoutez vos personnalisations pour garantir que les configurations requises ne sont pas supprimées par inadvertance. Par exemple, le nœud `tika` sous `/oak:index/damAssetLucene-6/tika` est un nœud obligatoire et doit également faire partie de votre index personnalisé ; il n’existe pas dans le SDK Cloud.

Vous devez préparer un nouveau package de définition d’index qui contient la définition d’index réelle, en suivant ce modèle de dénomination :

`<indexName>[-<productVersion>]-custom-<customVersion>`

qui doit ensuite être placé dans `ui.apps/src/main/content/jcr_root`. Les dossiers de sous-racine ne sont pas pris en charge pour l’instant.

Le package de l’exemple ci-dessus est nommé `com.adobe.granite:new-index-content:zip:1.0.0-SNAPSHOT`.

>[!NOTE]
>
>La propriété suivante doit être définie pour tout module de contenu contenant des définitions d’index dans le fichier de propriétés du module de contenu, situé à l’emplacement `/META-INF/vault/properties.xml` :
>
>`noIntermediateSaves=true`

### Déploiement de définitions d’index {#deploying-index-definitions}

>[!NOTE]
>
>Le plug-in Jackrabbit Filevault Maven Package version **1.1.0** présente un problème connu qui empêche d’ajouter `oak:index` aux modules `<packageType>application</packageType>`. Pour contourner ce problème, utilisez la version **1.0.4**.

Les définitions d’index sont désormais marquées comme personnalisées et versionnées :

* La définition d’index elle-même (par exemple, `/oak:index/ntBaseLucene-custom-1`)

Par conséquent, pour déployer un index, la définition d’index (`/oak:index/definitionname`) doit être fournie via `ui.apps` via Git et le processus de déploiement de Cloud Manager.

Une fois la nouvelle définition d’index ajoutée, la nouvelle application doit être déployée via Cloud Manager. Au moment du déploiement, deux tâches sont démarrées, chargées d’ajouter (et de fusionner si nécessaire) les définitions d’index à MongoDB et Azure Segment Store pour la création et la publication, respectivement. Les référentiels sous-jacents sont réindexés avec les nouvelles définitions d’index, avant que la commutation bleu/vert n’ait lieu.

>[!TIP]
>
>Pour plus de détails sur la structure de package requise pour AEM as a Cloud Service, reportez-vous au document [Structure de projets AEM](/help/implementing/developing/introduction/aem-project-content-package-structure.md).

## Gestion des index à l’aide de déploiements bleu/vert {#index-management-using-blue-green-deployments}

### Qu’est-ce que la gestion des index ?  {#what-is-index-management}

La gestion des index consiste à ajouter, supprimer et modifier des index. Changer la *définition* d’un index est rapide, mais appliquer le changement (opération souvent appelée « création d’un index » ou, pour les index existants, « réindexation ») nécessite du temps. Cette opération n’est pas instantanée : le référentiel doit être analysé pour que les données soient indexées.

### Qu’est-ce que le déploiement bleu/vert ?  {#what-is-blue-green-deployment}

Le déploiement bleu/vert peut réduire les temps d’inactivité. Il autorise également des mises à niveau sans interruption de service et des restaurations rapides. L’ancienne version de l’application (bleue) s’exécute en même temps que la nouvelle version (verte).

### Zones en lecture seule et en lecture-écriture {#read-only-and-read-write-areas}

Certaines zones du référentiel (parties en lecture seule) peuvent être différentes dans l’ancienne version (bleue) et dans la nouvelle version (verte) de l’application. Les zones en lecture seule du référentiel sont généralement « `/app` » et « `/libs` ». Dans l’exemple suivant, des italiques sont utilisés pour marquer les zones en lecture seule, tandis que du gras est utilisé pour les zones en lecture-écriture.

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

### Gestion des index sans déploiement bleu/vert {#index-management-without-blue-green-deployment}

Lors du développement ou de l’utilisation d’installations sur site, les index peuvent être ajoutés, supprimés ou modifiés au moment de l’exécution. Les index sont utilisés dès qu’ils sont disponibles. Si un index n’est pas encore censé être utilisé dans l’ancienne version de l’application, il est généralement créé lors d’un temps d’arrêt planifié. Il en va de même lors de la suppression d’un index ou de la modification d’un index existant. Lors de la suppression d’un index, celui-ci cesse d’être disponible dès sa suppression.

### Gestion des index avec déploiement bleu/vert {#index-management-with-blue-green-deployment}

Avec des déploiements bleu/vert, il n’existe pas de temps d’arrêt. Toutefois, pour la gestion des index, cela nécessite que les index ne soient utilisés que par certaines versions de l’application. Par exemple, lorsque vous ajoutez un index dans la version 2 de l’application, vous ne souhaitez pas que cet index soit déjà utilisé par la version 1 de l’application. L’inverse vaut également lorsqu’un index est supprimé : un index supprimé dans la version 2 est toujours nécessaire dans la version 1. Lors de la modification d’une définition d’index, nous voulons que l’ancienne version de l’index soit utilisée uniquement pour la version 1 et la nouvelle version de l’index uniquement pour la version 2.

Le tableau suivant présente cinq définitions d’index : l’index `cqPageLucene` est utilisé dans les deux versions tandis que index `damAssetLucene-custom-1` l’est uniquement dans la version 2.

>[!NOTE]
>
>`<indexName>-custom-<customerVersionNumber>` est nécessaire pour qu’AEM as a Cloud Service puisse marquer cela comme un remplacement d’un index existant.

| Index | Index prêt à l’emploi | Utilisation dans la version 1 | Utilisation dans la version 2 |
|---|---|---|---|
| /oak:index/damAssetLucene | Oui | Oui | Non |
| /oak:index/damAssetLucene-custom-1 | Oui (personnalisé) | Non | Oui |
| /oak:index/acme.product-custom-1 | Non | Oui | Non |
| /oak:index/acme.product-custom-2 | Non | Non | Oui |
| /oak:index/cqPageLucene | Oui | Oui | Oui |

Le numéro de version est incrémenté chaque fois que l’index est modifié. Pour éviter que des noms d’index personnalisés n’entrent en conflit avec des noms d’index du produit lui-même, les index personnalisés, ainsi que les modifications apportées aux index prêts à l’emploi, doivent se terminer par `-custom-<number>`.

### Modifications apportées aux index prêts à l’emploi {#changes-to-out-of-the-box-indexes}

Une fois qu’Adobe a modifié un index prêt à l’emploi tel que « damAssetLucene » ou « cqPageLucene », un nouvel index nommé `damAssetLucene-2` ou `cqPageLucene-2` est créé ou, si l’index a déjà été personnalisé, la définition d’index personnalisé est fusionnée avec les modifications de l’index prêt à l’emploi, comme illustré ci-dessous. La fusion des modifications se produit automatiquement. Cela signifie que vous n’avez rien à faire si un index prêt à l’emploi change. Cependant, il est possible de personnaliser à nouveau l’index ultérieurement.

| Index | Index prêt à l’emploi | Utilisation dans la version 2 | Utilisation dans la version 3 |
|---|---|---|---|
| /oak:index/damAssetLucene-custom-1 | Oui (personnalisé) | Oui | Non |
| /oak:index/damAssetLucene-2-custom-1 | Oui (automatiquement fusionné à partir de damAssetLucene-custom-1 et damAssetLucene-2) | Non | Oui |
| /oak:index/cqPageLucene | Oui | Oui | Non |
| /oak:index/cqPageLucene-2 | Oui | Non | Oui |

### Limites actuelles {#current-limitations}

Actuellement, la gestion des index n’est prise en charge que pour les index de type `lucene`.

### Ajout d’un index {#adding-an-index}

Pour ajouter un index nommé « `/oak:index/acme.product-custom-1` » à utiliser dans une nouvelle version de l’application et ultérieurement, l’index doit être configuré comme suit :

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
>Les définitions d’index dans AEM as a Cloud Service peuvent ne pas correspondre entièrement aux définitions d’index sur une instance de développement locale. L’instance de développement ne dispose pas d’une configuration Tika, alors que les instances AEM as a Cloud Service en ont une. Si vous personnalisez un index avec une configuration Tika, conservez la configuration Tika.

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
