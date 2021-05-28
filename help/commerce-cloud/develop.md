---
title: Développement d’AEM Commerce pour AEM as a Cloud Service
description: Découvrir comment générer un projet AEM compatible avec le commerce à l’aide de l’archétype de projet AEM. Découvrir comment créer et déployer le projet sur un environnement de développement local à l’aide du SDK AEM as a Cloud Service.
topics: Commerce, Development
feature: Commerce Integration Framework
version: cloud-service
doc-type: tutorial
kt: 5826
thumbnail: 39476.jpg
exl-id: 6f28a52b-52f8-4b30-95cd-0f9cb521de62
source-git-commit: 856266faf4cb99056b1763383d611e9b2c3c13ea
workflow-type: tm+mt
source-wordcount: '1001'
ht-degree: 85%

---

# Développement d’AEM Commerce pour AEM as a Cloud Service {#develop}

Le développement de projets AEM Commerce basés sur Commerce Integration Framework (CIF) pour AEM as a Cloud Service suit les mêmes règles et bonnes pratiques que les autres projets AEM dans AEM as a Cloud Service. Veuillez d’abord examiner les éléments suivants :

- [Structure de projet AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html?lang=fr)
- [SDK AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html)
- [Conseils de développement pour AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html)

## Développement local avec le SDK AEM as a Cloud Service {#local}

>[!VIDEO](https://video.tv.adobe.com/v/39476/?quality=12&learn=on)

Un environnement de développement local est recommandé pour travailler avec des projets CIF. Le module complémentaire CIF fourni pour AEM as a Cloud Service est également disponible pour le développement local. Il peut être téléchargé à partir du [portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html).

Le module complémentaire est fourni sous la forme d’une archive de fonctionnalités Sling. Le fichier zip disponible sur le portail de distribution de logiciels comprend deux fichiers archivés de fonctionnalités Sling, l’un pour l’auteur AEM et l’autre pour les instances de publication AEM.

**Vous découvrez AEM as a Cloud Service ?** Consultez un [guide plus détaillé de configuration d’environnement de développement local à l’aide du SDK AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html).

### Logiciels requis

Les logiciels suivants doivent être installés localement :

- [SDK AEM as a Cloud Service](https://experienceleague.adobe.com/docs/*experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime.html#download-the-aem-as-a-cloud-service-sdk)
- [Java 11](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/general.html)
- [Apache Maven](https://maven.apache.org/) (3.3.9 ou version ultérieure)
- [Node.js v10+](https://nodejs.org/en/)
- [npm 6+](https://www.npmjs.com/)
- [Git](https://git-scm.com/)

### Accès au module complémentaire CIF

Il est possible de télécharger le module complémentaire CIF en tant que fichier zip à partir du [portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html). Le fichier zip contient le module complémentaire CIF sous la forme d’une **archive de fonctionnalités Sling** ; il ne s’agit pas d’un module AEM. Notez que l’accès aux listes de SDK est limité aux environnements disposant d’une licence AEM as a Cloud Service.

>[!TIP]
>
>Veillez à toujours utiliser la dernière version du module complémentaire CIF.

### Configuration locale

Pour le développement local du module complémentaire CIF avec le SDK AEM as a Cloud Service, procédez comme suit :

1. Procurez-vous le dernier SDK AEM as a Cloud Service.
1. Décompressez le fichier AEM .jar pour créer le dossier `crx-quickstart` et exécutez :

   ```bash
   java -jar <jar name> -unpack
   ```

1. Créez un dossier `crx-quickstart/install`.
1. Copiez le fichier archivé de fonctionnalités Sling correct du module complémentaire CIF dans le dossier `crx-quickstart/install`.

   Le fichier zip du module complémentaire CIF contient deux fichiers `.far` archivés de fonctionnalités Sling. Assurez-vous d’utiliser le fichier correspondant à AEM Author ou à AEM Publish, selon la manière dont vous envisagez d’exécuter le SDK AEM as a Cloud Service local.

1. Créez une variable d’environnement de système d’exploitation locale nommée `COMMERCE_ENDPOINT` et contenant le point d’entrée Magento GraphQL.

   Exemple pour Mac OSX :

   ```bash
   export COMMERCE_ENDPOINT=https://demo.magentosite.cloud/graphql
   ```

   Exemple pour Windows :

   ```bash
   set COMMERCE_ENDPOINT=https://demo.magentosite.cloud/graphql
   ```

   Cette variable est utilisée par AEM pour se connecter à votre système commercial. En outre, le module complémentaire CIF inclut un proxy inverse local pour rendre le point d’entrée GraphQL de Commerce disponible localement. Il est utilisé par les outils de création CIF (console de produit et sélecteurs) et pour les composants CIF côté client effectuant des appels GraphQL directs.

   Cette variable doit également être configurée pour l’environnement AEM as a Cloud Service. Pour plus d’informations sur les variables, voir [Configuration d’OSGi pour AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=fr#local-development).

1. (Facultatif) Pour activer les fonctionnalités de catalogue intermédiaire, vous devez créer un jeton d’intégration pour votre instance de Magento. Suivez les étapes décrites dans [Prise en main](./getting-started.md#staging) pour créer le jeton.

   Définissez un secret OSGi portant le nom `COMMERCE_AUTH_HEADER` sur la valeur suivante :

   ```xml
   Authorization: Bearer <Access Token>
   ```

   Pour plus d’informations sur les secrets, voir [Configuration d’OSGi pour AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html#local-development).

1. Démarrez le SDK AEM as a Cloud Service.

>[!NOTE]
>
>Assurez-vous de commencer AEM en tant que SDK Cloud Service dans la même fenêtre de terminal que la variable d’environnement a été définie à l’étape 5. Si vous le lancez dans une fenêtre de terminal distincte ou que vous double-cliquez sur le fichier .jar, assurez-vous que la variable d’environnement est visible.

Vérifiez la configuration via la console OSGI : `http://localhost:4502/system/console/osgi-installer`. La liste doit inclure les bundles liés au module complémentaire CIF, le module de contenu et les configurations OSGI, comme défini dans le fichier de modèle de fonctionnalité.

## Configuration du projet {#project}

Il existe deux manières de démarrer votre projet CIF pour AEM as a Cloud Service.

### Utilisation de l’archétype de projet AEM

L’[archétype de projet AEM](https://github.com/adobe/aem-project-archetype) est le principal outil utilisé pour démarrer un projet préconfiguré afin de démarrer avec CIF. Les composants principaux CIF et toutes les configurations requises peuvent être inclus dans un projet généré avec une option supplémentaire.

>[!TIP]
>
>Utilisez la [version 24 ou ultérieure de l’archétype de projet AEM](https://github.com/adobe/aem-project-archetype/releases) pour générer le projet.

Reportez-vous aux [instructions d’utilisation](https://github.com/adobe/aem-project-archetype#usage) de l’archétype de projet AEM pour savoir comment générer un projet AEM. Pour inclure CIF dans le projet, utilisez l’option `includeCommerce`.

Par exemple :

```bash
mvn -B archetype:generate \
 -D archetypeGroupId=com.adobe.granite.archetypes \
 -D archetypeArtifactId=aem-project-archetype \
 -D archetypeVersion=24 \
 -D aemVersion=cloud \
 -D appTitle="My Site" \
 -D appId="mysite" \
 -D groupId="com.mysite" \
 -D frontendModule=general \
 -D includeExamples=n \
 -D includeCommerce=y
```

Les composants principaux CIF peuvent être utilisés dans n’importe quel projet en incluant le module `all` fourni ou individuellement en utilisant le module de contenu CIF et les lots OSGI associés. Pour ajouter manuellement des composants principaux CIF à un projet, utilisez les dépendances suivantes :

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

### Utilisation du magasin de référence Venia AEM

Une deuxième manière de démarrer un projet CIF consiste à cloner et à utiliser le [magasin de référence Venia AEM](https://github.com/adobe/aem-cif-guides-venia). Le magasin de référence Venia AEM est un exemple d’application storefront de référence qui illustre l’utilisation des composants principaux CIF pour AEM. Il s’agit d’un ensemble de bonnes pratiques et d’un point de départ potentiel pour développer vos propres fonctionnalités.

Pour commencer à utiliser le magasin de référence Venia AEM, il vous suffit de cloner le référentiel Git et de personnaliser le projet en fonction de vos besoins.

>[!NOTE]
>
>Le projet de magasin de référence Venia contient deux profils de version pour AEM as a Cloud Service et AEM 6.5. Reportez-vous au [fichier readme.md du projet](https://github.com/adobe/aem-cif-guides-venia/blob/main/README.md) pour savoir comment ces profils sont utilisés.

## Ressources supplémentaires

- [Archétype de projet AEM](https://github.com/adobe/aem-project-archetype)
- [Magasin de référence Venia AEM](https://github.com/adobe/aem-cif-guides-venia)
- [Portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)
