---
title: Développement d’AEM Commerce pour AEM as a Cloud Service
description: Découvrir comment générer un projet AEM compatible avec le commerce à l’aide de l’archétype de projet AEM. Découvrir comment créer et déployer le projet sur un environnement de développement local à l’aide du SDK AEM as a Cloud Service.
topics: Commerce, Development
feature: Commerce Integration Framework
version: Experience Manager as a Cloud Service
doc-type: tutorial
kt: 5826
thumbnail: 39476.jpg
exl-id: 6f28a52b-52f8-4b30-95cd-0f9cb521de62
role: Admin
index: false
source-git-commit: 856442039fcd25ec675a6258d182f7a35f590c3c
workflow-type: tm+mt
source-wordcount: '904'
ht-degree: 74%

---


# Développement d’AEM Commerce pour AEM as a Cloud Service {#develop}

Le développement de projets AEM Commerce basés sur Commerce Integration Framework (CIF) pour AEM as a Cloud Service suit les mêmes règles et bonnes pratiques que les autres projets AEM dans AEM as a Cloud Service. Passez en revue les éléments suivants :

* [Structure de projet AEM](/help/implementing/developing/introduction/aem-project-content-package-structure.md)
* [SDK AEM as a Cloud Service](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)
* [Conseils de développement pour AEM as a Cloud Service](/help/implementing/developing/introduction/development-guidelines.md)

## Développement local avec le SDK AEM as a Cloud Service {#local}

>[!VIDEO](https://video.tv.adobe.com/v/347036/?quality=12&learn=on&captions=fre_fr)

Un environnement de développement local est recommandé pour travailler avec des projets CIF. Le module complémentaire CIF fourni pour AEM as a Cloud Service est également disponible pour le développement local. Il peut être téléchargé à partir du [portail de distribution de logiciels](/help/implementing/developing/tools/package-manager.md#software-distribution).

Le module complémentaire est fourni sous la forme d’une archive de fonctionnalités Sling. Le fichier zip disponible sur le portail de distribution de logiciels comprend deux fichiers archivés de fonctionnalités Sling, l’un pour l’auteur AEM et l’autre pour les instances de publication AEM.

>[!TIP]
>
>**Vous découvrez AEM as a Cloud Service ?**
>&#x200B;>Consultez [un guide plus détaillé de configuration d’environnement de développement local à l’aide d’AEM as a Cloud Service SDK.](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=fr)

### Logiciels requis {#required-software}

Les logiciels suivants doivent être installés localement :

* [SDK AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime.html?lang=fr#download-the-aem-as-a-cloud-service-sdk)
* [Java™ 11](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/general.html)
* [Apache Maven](https://maven.apache.org/) (3.3.9 ou version ultérieure)
* [Node.js v10+](https://nodejs.org/fr)
* [npm 6+](https://www.npmjs.com/)
* [Git](https://git-scm.com/)

### Accès au module complémentaire CIF {#accessing-add-on}

Le module complémentaire CIF peut être téléchargé sous la forme d’un fichier zip à partir du portail [&#x200B; Distribution de logiciels .](/help/implementing/developing/tools/package-manager.md) Le fichier zip contient le module complémentaire CIF en tant qu’**archive des fonctionnalités Sling**, il ne s’agit pas d’un package AEM. Les listes de SDK sont accessibles avec une licence AEM as a Cloud Service.

>[!TIP]
>
>Veillez à toujours utiliser la dernière version du module complémentaire CIF.

### Configuration locale {#local-setup}

Pour le développement local du module complémentaire CIF à l’aide d’AEM as a Cloud Service SDK, procédez comme suit :

1. Obtenez la dernière version d’AEM as a Cloud Service SDK.
1. Décompressez le fichier AEM .jar afin de pouvoir créer le dossier `crx-quickstart`. Exécutez la commande suivante :

   ```bash
   java -jar <jar name> -unpack
   ```

1. Créez un dossier `crx-quickstart/install`.
1. Copiez le fichier archivé de fonctionnalités Sling correct du module complémentaire CIF dans le dossier `crx-quickstart/install`.

   * Le fichier zip du module complémentaire CIF contient deux fichiers `.far` d’archive de fonctionnalités Sling.
   * Assurez-vous d’utiliser le fichier correspondant à AEM Author ou à AEM Publish, selon la manière dont vous envisagez d’exécuter le SDK AEM as a Cloud Service local.

1. Créez une variable d’environnement de système d’exploitation locale nommée `COMMERCE_ENDPOINT` et contenant le point d’entrée GraphQL d’Adobe Commerce.

   * Cette variable est utilisée par AEM pour se connecter à votre système commercial. Le module complémentaire CIF comprend un proxy inverse local pour rendre le point d’entrée Commerce GraphQL disponible localement. Ce proxy est utilisé par les outils de création CIF (console de produit et sélecteurs) et pour les composants CIF côté client effectuant des appels GraphQL directs.

   * Cette variable doit également être configurée pour l’environnement AEM as a Cloud Service. Pour plus d’informations sur les variables, voir [Configuration d’OSGi pour AEM as a Cloud Service.](/help/implementing/deploying/configuring-osgi.md#local-development)

   * Exemple sous macOS :

     ```bash
     export COMMERCE_ENDPOINT=https://<yourcommercesystem>/graphql
     ```

   * Exemple sous Windows :

     ```bash
     set COMMERCE_ENDPOINT=https://<yourcommercesystem>/graphql
     ```

1. (Facultatif) Pour activer les fonctionnalités de catalogue par étapes, vous devez créer un jeton d’intégration pour votre instance d’Adobe Commerce. Suivez les étapes décrites à la section [Prise en main](/help/commerce-cloud/cif-storefront/getting-started.md#staging) pour créer le jeton.

   * Définissez un secret OSGi portant le nom `COMMERCE_AUTH_HEADER` sur la valeur suivante :

     ```xml
     Authorization: Bearer <Access Token>
     ```

   * Pour plus d’informations sur les secrets, voir [Configuration d’OSGi pour AEM as a Cloud Service.](/help/implementing/deploying/configuring-osgi.md#local-development)

1. Démarrez AEM as a Cloud Service SDK.

>[!NOTE]
>
>Veillez à démarrer le SDK AEM as a Cloud Service dans la même fenêtre de terminal selon la variable d’environnement définie à l’étape 5. Si vous le lancez dans une fenêtre de terminal distincte ou que vous double-cliquez sur le fichier .jar, assurez-vous que la variable d’environnement est visible.

Vérifiez la configuration via la console OSGi : `http://localhost:4502/system/console/osgi-installer`. La liste doit inclure les lots liés au module complémentaire CIF, le package de contenu et les configurations OSGi tels que définis dans le fichier de modèle de fonctionnalité.

## Configuration du projet {#project}

Il existe deux manières de démarrer votre projet CIF pour AEM as a Cloud Service.

### Utilisation de l’archétype de projet AEM {#project-archetype}

L’[archétype de projet AEM](https://github.com/adobe/aem-project-archetype) est le principal outil utilisé pour démarrer un projet préconfiguré afin de démarrer avec CIF. Les composants principaux CIF et toutes les configurations requises peuvent être inclus dans un projet généré avec une option supplémentaire.

>[!TIP]
>
>Utilisez toujours la dernière version de lʼ[archétype de projet AEM](https://github.com/adobe/aem-project-archetype/releases) pour générer le projet.

Reportez-vous aux [instructions d’utilisation](https://github.com/adobe/aem-project-archetype#usage) de l’archétype de projet AEM pour savoir comment générer un projet AEM. Pour inclure CIF dans le projet, utilisez l’option `includeCommerce`.

Par exemple :

```bash
mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate \
 -D archetypeGroupId=com.adobe.aem \
 -D archetypeArtifactId=aem-project-archetype \
 -D archetypeVersion=35 \
 -D appTitle="My Site" \
 -D appId="mysite" \
 -D groupId="com.mysite" \
 -D includeCommerce=y
```

Les composants principaux CIF peuvent être utilisés dans n’importe quel projet en incluant le package `all` fourni ou individuellement en utilisant le package de contenu CIF et les bundles OSGi associés. Pour ajouter manuellement des composants principaux CIF à un projet, utilisez les dépendances suivantes :

```java
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>core-cif-components-apps</artifactId>
    <type>zip</type>
    <version>x.y.z</version>
</dependency>
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>core-cif-components-config</artifactId>
    <type>zip</type>
    <version>x.y.z</version>
</dependency>
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>core-cif-components-core</artifactId>
    <version>x.y.z</version>
</dependency>
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>graphql-client</artifactId>
    <version>x.y.z</version>
</dependency>
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>magento-graphql</artifactId>
    <version>x.y.z</version>
</dependency>
```

### Utilisation du magasin de référence Venia AEM {#venia-reference}

Une deuxième manière de démarrer un projet CIF consiste à cloner et à utiliser le [magasin de référence Venia AEM](https://github.com/adobe/aem-cif-guides-venia). Le magasin de référence Venia AEM est un exemple d’application storefront de référence qui illustre l’utilisation des composants principaux CIF pour AEM. Cette application offre des exemples de bonnes pratiques, ainsi qu’un point de départ potentiel pour développer vos propres fonctionnalités.

Pour commencer à utiliser le magasin de référence Venia, il vous suffit de cloner le référentiel Git et de personnaliser le projet en fonction de vos besoins.

>[!NOTE]
>
>Le projet de magasin de référence Venia contient deux profils de version pour AEM as a Cloud Service et AEM 6.5. Reportez-vous au [fichier readme.md du projet](https://github.com/adobe/aem-cif-guides-venia/blob/main/README.md) pour savoir comment ces profils sont utilisés.

## Ressources supplémentaires {#additional-resources}

* [Archétype de projet AEM](https://github.com/adobe/aem-project-archetype)
* [Magasin de référence Venia AEM](https://github.com/adobe/aem-cif-guides-venia)
* [Portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)
