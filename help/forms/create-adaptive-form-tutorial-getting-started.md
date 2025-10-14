---
title: Prise en main d’Adaptive Forms.
description: Découvrez comment créer une Forms adaptative adaptée aux périphériques mobiles avec notre tutoriel détaillé. Ces formulaires s’adaptent de manière transparente sur tous les périphériques, assurant ainsi une expérience fluide.
keywords: Forms adaptatif, Forms réactif, HTML5 Forms
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner
hide: true
hidefromtoc: true
exl-id: b59cb56c-9629-48e4-b5c9-a861013a1360
source-git-commit: af58a784f24f212962ad73f11015fb788493d8b5
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 3%

---

# Créer un formulaire adaptatif (composants principaux) - Tutoriel

De nos jours, les utilisateurs attendent une expérience conviviale pour les mobiles dans toutes leurs interactions et les formulaires ne font pas exception. Les formulaires adaptatifs peuvent vous aider à créer des formulaires non seulement compatibles avec les appareils mobiles, mais aussi à améliorer l’engagement des utilisateurs et à réduire le temps nécessaire pour les remplir.

Ce tutoriel fournit un guide détaillé sur la création d’un formulaire adaptatif. Il est ventilé en un cas d’utilisation et plusieurs guides, dont chacun vous apprendra à ajouter une nouvelle fonctionnalité à votre formulaire adaptatif.

À la fin du tutoriel, vous serez en mesure de :

* Créer un formulaire adaptatif et son modèle de données
* Application d’un style à votre formulaire adaptatif
* Création de règles de fonctionnement à l’aide de l’éditeur de règles de formulaire adaptatif
* Préremplir les champs de formulaire adaptatif
* Ajout de signatures électroniques à votre formulaire
* Protect de votre formulaire à partir de robots à l’aide de Google reCAPTCHA
* Localisation de votre formulaire adaptatif pour différentes langues
* Configuration de votre formulaire pour produire des données structurées
* Configuration de votre formulaire pour envoyer des données à un point de terminaison REST
* Publish de votre formulaire adaptatif


## Pourquoi créer des formulaires basés sur des composants principaux ?

AEM Forms fournit des composants de base et des composants principaux pour créer des expériences de formulaires. Les composants principaux sont l’approche moderne et recommandée pour créer de nouvelles expériences de formulaires. Pourquoi utiliser les composants principaux ? Ces composants sont légers, Open Source (disponibles sur github), offrent un excellent score Google Lighthouse et des vitaux web, sont compatibles avec l’accessibilité et apportent toutes les fonctionnalités courantes d’AEM Sites (telles que le contrôle de version et la localisation). En outre, ces composants sont plus faciles à mettre en forme. Vous pouvez facilement personnaliser leur aspect selon les directives de valorisation de marque de votre entreprise. Ils n’ont aucune dépendance tierce, tout développeur maîtrisant JavaScript et CSS peut facilement personnaliser ces composants.

![&#x200B; Pourquoi créer un Forms adaptatif basé sur les composants principaux ? Ces composants sont légers, plus faciles à mettre en forme, offrent un score de phare élevé, prennent en charge les normes d’accessibilité, facilement personnalisables et open source, disponibles sur github, sans dépendance à l’égard des bibliothèques tierces et n’ont pratiquement pas de courbe d’apprentissage pour les développeurs AEM et les auteurs AEM En plus, les composants principaux AEM Forms disposent de toutes les fonctionnalités des composants principaux de la gestion de contenu web d’.](/help/forms/assets/cc-core-components-benefits.png){width="50%"}

## Cas d’utilisation : pré-qualification simplifiée du prêt immobilier avec Forms adaptatif

Dans ce tutoriel, vous créez un formulaire adaptatif pour une grande banque. Le cas d’utilisation est le suivant :

Les acheteurs potentiels de maisons visitent le site web ou la succursale de la banque pour explorer les options de prêt immobilier. Le processus d’application traditionnel est long et fastidieux et nécessite souvent une documentation à l’avance. Cela dissuade certains acheteurs de lancer le processus, ce qui entrave à la fois la génération de dirigeants de la banque et la capacité de l&#39;acheteur à rechercher en toute confiance la maison de leurs rêves.

Vous êtes chargé de développer un formulaire interactif de pré-qualification des prêts immobiliers. Ce formulaire rassemblerait des informations de base, préqualifierait l’emprunteur en fonction de ses données, offrirait des montants estimés de prêt, des besoins de mise en service potentiels et des taux d’intérêt en fonction de différents types de prêts. Les utilisateurs préqualifiés pourront lancer une demande de prêt complète directement à partir du formulaire de pré-qualification.

Le formulaire serait créé à l’aide de formulaires adaptatifs. Cela permet une expérience personnalisée tout en collectant les données financières nécessaires pour une pré-qualification précise du prêt immobilier.

Une fois le tutoriel terminé, votre formulaire ressemblerait au formulaire suivant :

![Ajouter un formulaire de travail ici](/help/forms/assets/cc-tutorial-final-form.png)

## Configurer l’environnement de développement

Vous pouvez créer et tester le formulaire adaptatif directement sur votre ordinateur local, avant de le déployer dans un environnement de Cloud Service. Adobe fournit un SDK AEM à pour le développement local qui vous permet de

* Créez, personnalisez et testez localement des formulaires.
* Concevez des thèmes de formulaires et créez des configurations localement,
* Déployez facilement vos ressources terminées dans le cloud.

Le développement local avec AEM SDK vous permet de gagner du temps et de simplifier le processus de développement.


**Prêt à commencer ?**

1. [Configuration des outils de développement pour AEM Projects](/help/forms/setup-local-development-environment.md#set-up-development-tools-for-aem-projects) : téléchargez et installez la dernière version de [Java 11™](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=fr#local-development-environment-set-up), [Git](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=fr#install-git), [Node.js (npm)](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=fr#node-js) et [Maven](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=fr#install-maven). Installez également un éditeur de texte brut. Les exemples de ce tutoriel sont basés sur Visual Studio Code.

1. [Installation du SDK AEM](/help/forms/setup-local-development-environment.md#set-up-local-experience-manager-environment-for-development) : téléchargez et installez la dernière version du SDK AEM. Cela fournit les outils essentiels au développement AEM. Notez la version du SDK AEM.

   ![&#x200B; Distribution-Logiciels](/help/forms/assets/software-distribution.png)

   ![installer AEM SDK](/help/forms/assets/start-aem-sdk.png)

1. [Ajoutez le module complémentaire AEM Forms](/help/forms/setup-local-development-environment.md#add-forms-archive-to-local-author-and-publish-instances-and-configure-forms-specific-users) : téléchargez et installez le module complémentaire AEM Forms correspondant à la version de votre SDK à partir du portail [Distribution logicielle](https://experience.adobe.com/#/downloads).
   ![install-aem-forms-add-on](/help/forms/assets/install-aem-forms-add-on.png)

   +++Installer le module complémentaire AEM Forms :

   Pour installer le module complémentaire AEM Forms :

   1. Arrêtez AEM SDK.
   1. Ajoutez le fichier de module complémentaire AEM Forms (.far) au dossier `AEM SDK/crx-quickstart/install`,
   1. Redémarrez AEM SDK.

   +++

1. [Configurer les autorisations d’utilisateur](/help/forms/setup-local-development-environment.md#configure-users-and-permissions) : créez des utilisateurs disposant d’autorisations de développement, de création et autres et ajoutez ces utilisateurs à des groupes de formulaires prédéfinis.


1. [Ajouter des modèles Forms adaptatifs](/help/forms/setup-local-development-environment.md#set-up-a-development-project-for-forms-based-on-experience-manager-archetype) : utilisez AEM archetypes 48 ou version ultérieure pour créer un projet AEM et le déployer sur votre SDK. Le projet ajoute des modèles Forms adaptatifs à votre SDK AEM.

   ![Modèles de formulaire adaptatif](/help/forms/assets/adaptive-forms-templates.png)

   +++Ajoutez des modèles Forms adaptatifs à votre SDK AEM :

   1. Exécutez la commande ci-dessous pour créer un projet AEM.

      ```
      mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate -D archetypeGroupId=com.adobe.aem -D archetypeArtifactId=aem-project-archetype -D archetypeVersion="48" -D appTitle=securbank -D appId=securbank -D groupId=com.securbank -D includeFormsenrollment="y" -D aemVersion="cloud"
      ```

      ![AEM-Archetyoe-Project](/help/forms/assets/aem-archetype-project.png)

   1. Déployez le projet sur votre environnement de développement local. Vous pouvez utiliser la commande suivante pour effectuer un déploiement sur votre environnement de développement local :

      ```
      cd securbank
      
      mvn -PautoInstallPackage clean install
      ```

   Une fois le projet AEM déployé, vous pouvez voir les modèles Forms adaptatifs dans votre environnement.

   +++


Pour obtenir des instructions détaillées et un guide détaillé sur la configuration de votre environnement de développement AEM Forms local, reportez-vous à l’article [Configuration de l’environnement de développement local pour AEM Forms](/help/forms/setup-local-development-environment.md) .



## Étape suivante

Après avoir configuré l’environnement de développement, vous êtes prêt à créer un formulaire adaptatif. Dans l’article suivant, vous apprendrez à

* Création d’un formulaire adaptatif à partir du modèle vide
* Champs de mise en page à afficher et à accepter facilement les informations.
* Aperçu du formulaire.

<!-- 

### Step 2: Create Form Data Model

A form data model lets you connect an adaptive form to disparate data sources. For example, AEM user profile, RESTful web services, SOAP-based web services, OData services, and relational databases. You can use the form data model with an adaptive form to retrieve, update, delete, and add data to connected data sources.

Goals of article:

* Create the form data model using Rest endpoint.
* Add data model objects so you can form the data model.
* Configure read and write services for the form data model.
* Test form data model and configured services with test data.

### Step 4: Apply rules to adaptive form fields

AEM Forms provide an editor to write rules on adaptive form objects. These rules define actions to trigger on form objects based on preset conditions, user inputs, and user actions on the form. It helps ensure accuracy and speeds up the form-filling experience.

Goals:

* Create and apply rules to adaptive form fields.
* Use rules to trigger form data model services to update the data to database.

### Step 5: Style your adaptive form

Adaptive forms provide OOTB themes and allows you to customize an existing theme to make a brand specific theme. 


A theme contains styling details for components and panels, and you can reuse a theme in different forms. Styles include properties such as background colors, state colors, transparency, alignment, and size. When you apply the theme to your form, the specified style reflects on corresponding components of your form.

Goals:

* Apply an out of the box theme to an adaptive form.
* Create your brand specific theme.


### Step 6: Publish your adaptive form

You can publish adaptive forms as a stand-alone form (single page application), include in AEM Sites page, or include in a non-AEM Sites page.

Goals:

* Publish the adaptive form as an AEM Page.
* Embed the adaptive form in an AEM Sites Page.
* Embed the adaptive form in an external webpage (a non-AEM webpage hosted outside AEM).

-->
