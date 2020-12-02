---
title: Développer le commerce AEM pour l'AEM en tant que Cloud Service
description: Découvrez comment générer un projet AEM compatible avec le commerce à l'aide de l'archétype de projet AEM. Découvrez comment créer et déployer le projet sur un environnement de développement local à l’aide de l’AEM en tant que SDK Cloud Service.
topics: Commerce, Development
feature: Commerce Integration Framework
version: cloud-service
doc-type: tutorial
kt: 5826
thumbnail: 39476.jpg
translation-type: tm+mt
source-git-commit: 72d98c21a3c02b98bd2474843b36f499e8d75a03
workflow-type: tm+mt
source-wordcount: '987'
ht-degree: 12%

---


# Développer le commerce AEM pour l&#39;AEM en tant que Cloud Service {#develop}

Le développement de projets de commerce AEM basés sur le cadre d&#39;intégration commerciale (CIF) pour l&#39;AEM en tant que Cloud Service suit les mêmes règles et bonnes pratiques que d&#39;autres projets d&#39;AEM sur l&#39; en tant que Cloud Service. Veuillez d&#39;abord les lire :

- [Structure de projet AEM](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html)
- [SDK AEM as a Cloud Service](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html)
- [Conseils de développement pour AEM as a Cloud Service](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/developing/development-guidelines.html)

## Développement local avec AEM comme SDK Cloud Service {#local}

>[!VIDEO](https://video.tv.adobe.com/v/39476/?quality=12&learn=on)

Un environnement de développement local est recommandé pour travailler avec les projets du FCI. L&#39;Ajoute du FCI, qui permet l&#39;AEM en tant qu&#39;environnement Cloud Service, est également disponible pour le développement local. Il peut être téléchargé à partir du [portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/fr-FR/aemcloud.html).

L’Ajoute CIF est fournie sous la forme d’une archive de fonctionnalité Sling. Le fichier zip disponible sur le portail de distribution de logiciels comprend deux fichiers d’archives de fonctionnalités Sling, l’un pour l’auteur AEM et l’autre pour les instances de publication AEM.

**Vous êtes nouveau à AEM en tant que Cloud Service ?** Consultez  [un guide plus détaillé pour configurer un environnement de développement local à l’aide de l’AEM en tant que SDK](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html) Cloud Service.

### Logiciels requis

Les éléments suivants doivent être installés localement :

- [SDK AEM as a Cloud Service](https://docs.adobe.com/content/help/en/*experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime.html#download-the-aem-as-a-cloud-service-sdk)
- [Java 11](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/general.html)
- [Apache Maven](https://maven.apache.org/)  (3.3.9 ou version ultérieure)
- [Node.js v10+](https://nodejs.org/fr/)
- [npm 6+](https://www.npmjs.com/)
- [Git](https://git-scm.com/)

### Accès au module complémentaire CIF

Le module complémentaire CIF peut être téléchargé sous forme de fichier zip à partir du [portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html). Le fichier zip contient le module complémentaire CIF en tant qu&#39;**archive de la fonctionnalité Sling**, il ne s&#39;agit pas d&#39;un package AEM. Notez que l’accès aux listes de SDK est limité à celles avec AEM en tant que licence Cloud Service.

>[!TIP]
>
>Veillez à toujours utiliser la dernière version d’Ajoute CIF.

### Configuration locale

Pour le développement d’Ajoutes CIF locales à l’aide de l’AEM en tant que SDK Cloud Service, procédez comme suit :

1. Nouveautés AEM en tant que SDK Cloud Service
2. Décompressez le fichier AEM .jar pour créer le dossier `crx-quickstart`, exécutez :

   ```bash
   java -jar <jar name> -unpack
   ```

3. Créer un dossier `crx-quickstart/install`
4. Copiez le fichier d’archive Sling Feature correct du module complémentaire CIF dans le dossier `crx-quickstart/install`.

   Le fichier zip du module complémentaire CIF contient deux fichiers d’archive de fonctionnalités Sling `.far`. Assurez-vous d’utiliser l’AEM appropriée pour AEM Author ou AEM Publish, selon la manière dont vous envisagez d’exécuter l’locale en tant que SDK Cloud Service.

5. Créez une variable d&#39;environnement système d&#39;exploitation locale `COMMERCE_ENDPOINT` contenant le point de terminaison GraphQL Magento.

   Exemple Mac OSX :

   ```bash
   export COMMERCE_ENDPOINT=https://demo.magentosite.cloud/graphql
   ```

   Exemple de fenêtres :

   ```bash
   set COMMERCE_ENDPOINT=https://demo.magentosite.cloud/graphql
   ```

   Cette variable doit également être configurée pour l’AEM en tant qu’environnement Cloud Service.

6. Début de l’AEM en tant que SDK Cloud Service

7. Début du serveur proxy GraphQL local

   Pour rendre le point de terminaison GraphQL Magento disponible localement pour le module complémentaire CIF et les composants CIF, utilisez la commande suivante. Le point de terminaison GraphQL sera alors disponible à `http://localhost:3002/graphql`.
Exemple Mac OSX :

   ```bash
   npx local-cors-proxy --proxyUrl https://demo.magentosite.cloud --port 3002 --proxyPartial ''
   ```

   Exemple de fenêtres :

   ```bash
   npx local-cors-proxy --proxyUrl https://demo.magentosite.cloud --port 3002 --proxyPartial '""'
   ```
   L&#39;argument `--proxyPartial` doit recevoir une chaîne vide.

   Vous pouvez tester le proxy GraphQL local en pointant un outil de requête GraphQL sur `http://localhost:3002/graphql` et en testant quelques requêtes.

8. Connectez-vous à AEM SDK et configurez CIF pour utiliser le serveur proxy GraphQL local.

   Accédez à la configuration du Cloud Service CIF (Outils > Cloud Services > Configuration CIF). Ouvrez la vue de propriétés de la configuration utilisée par votre projet.

   Pour la propriété `GraphQL Proxy Path`, utilisez le point de terminaison du serveur proxy local `http://localhost:3002/graphql`. Enregistrez la configuration.

>[!NOTE]
>
>N’insérez pas la configuration de l’étape 8 dans le référentiel du projet. Cette configuration n&#39;est requise que pour une configuration de développement local. aem en tant qu&#39;environnements Cloud Service sont déjà configurés avec le proxy GraphQL lors de l&#39;intégration.

Vérifiez la configuration via la console OSGI : `http://localhost:4502/system/console/osgi-installer`. La liste doit inclure les lots de module complémentaire CIF, les configurations content-package et OSGI associés, comme défini dans le fichier de modèle de fonctionnalité.

## Configuration du projet {#project}

Il existe deux façons d&#39;amorcer votre projet CIF pour AEM en tant que Cloud Service.

### Utiliser l&#39;archétype de projet AEM

L&#39;[AEM Archétype de projet](https://github.com/adobe/aem-project-archetype) est le principal outil pour amorcer un projet préconfiguré pour démarrer avec le FIC. Les composants de base CIF et toutes les configurations requises peuvent être inclus dans un projet généré avec une option supplémentaire.

>[!TIP]
>
>Utilisez [AEM Project Archetype 24 ou version ultérieure](https://github.com/adobe/aem-project-archetype/releases) pour générer le projet.

Voir les [instructions d&#39;utilisation de l&#39;archétype de projet AEM](https://github.com/adobe/aem-project-archetype#usage) sur la façon de générer un projet AEM. Pour inclure CIF dans le projet, utilisez l&#39;option `includeCommerce`.

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

Les composants de base CIF peuvent être utilisés dans n&#39;importe quel projet en incluant le package `all` fourni ou individuellement en utilisant le package de contenu CIF et les lots OSGI connexes. Pour ajouter manuellement des composants principaux CIF à un projet, utilisez les dépendances suivantes :

```java
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>core-cif-components-apps</artifactId>
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

### Utiliser AEM Venia Reference Store

Une deuxième option pour début d&#39;un projet CIF consiste à cloner et à utiliser le [magasin de référence Venia ](https://github.com/adobe/aem-cif-guides-venia) de l&#39;AEM. Le magasin de référence d&#39;AEM Venia est un exemple d&#39;application de vitrine de référence qui montre l&#39;utilisation des composants principaux de CIF pour l&#39;AEM. Il s’agit d’un ensemble d’exemples de bonnes pratiques ainsi que d’un point de départ potentiel pour développer votre propre fonctionnalité.

Pour commencer avec le Venia Reference Store, il vous suffit de cloner le référentiel Git et de personnaliser le projet en fonction de vos besoins.

>[!NOTE]
>
>Le projet Venia Reference Store contient deux profils de génération pour AEM en tant que Cloud Service et AEM 6.5. Consultez le [projet readme.md](https://github.com/adobe/aem-cif-guides-venia/blob/main/README.md) pour savoir comment ils sont utilisés.

## Ressources supplémentaires

- [Archétype de projet AEM](https://github.com/adobe/aem-project-archetype)
- [aem Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
- [Portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)
