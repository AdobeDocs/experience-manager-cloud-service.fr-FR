---
title: Prise en main du Forms adaptatif.
description: Découvrez comment créer des Forms adaptatifs réactifs sur les appareils mobiles à l’aide de notre tutoriel détaillé. Ces formulaires s’adaptent de manière transparente sur tous les appareils, assurant ainsi une expérience fluide.
keywords: Forms adaptatif, Responsive Forms, HTML5 Forms
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner
hide: true
hidefromtoc: true
badgeSaas: label="AEM Forms" type="Positive" tooltip="S’applique à AEM Forms)."
exl-id: b59cb56c-9629-48e4-b5c9-a861013a1360
source-git-commit: 89b0f2a8ca9d2f60365a5c3962b0b4e826f79b3e
workflow-type: tm+mt
source-wordcount: '924'
ht-degree: 4%

---

# Création d’un formulaire adaptatif (composants principaux) - Tutoriel

De nos jours, les utilisateurs et utilisatrices s’attendent à une expérience conviviale sur mobile dans toutes leurs interactions, et les formulaires ne font pas exception. Les formulaires adaptatifs peuvent vous aider à créer des formulaires compatibles avec les appareils mobiles, mais aussi à améliorer l’interaction client et à réduire le temps nécessaire pour les remplir.

Ce tutoriel fournit un guide détaillé sur la création d’un formulaire adaptatif. Il est divisé en un cas d’utilisation et plusieurs guides, chacun d’eux vous apprenant à ajouter une nouvelle fonctionnalité à votre formulaire adaptatif.

À la fin du tutoriel, vous serez en mesure de :

* Créer un formulaire adaptatif et son modèle de données
* Application d’un style à votre formulaire adaptatif
* Créer des règles métier à l’aide de l’éditeur de règles de formulaire adaptatif
* Préremplir les champs de formulaires adaptatifs
* Ajouter des signatures électroniques à votre formulaire
* Protégez votre formulaire des robots à l’aide de Google reCAPTCHA
* Localisez votre formulaire adaptatif pour différentes langues
* Configurer votre formulaire pour produire des données structurées
* Configurer votre formulaire pour envoyer des données à un point d’entrée REST
* Publication de votre formulaire adaptatif


## Pourquoi créer des formulaires basés sur les composants principaux ?

AEM Forms fournit des composants de base et des composants principaux pour créer des expériences de formulaires. Les composants principaux constituent l’approche moderne et recommandée pour créer n’importe quelle nouvelle expérience de formulaires. Pourquoi utiliser les composants principaux ? Ces composants sont légers, open source (disponibles sur github), offrent un excellent score pour Google Lighthouse et les web vitals, sont conformes à l’accessibilité, et apportent toutes les fonctionnalités familières d’AEM Sites (telles que le contrôle de version et la localisation). En outre, ces composants sont plus faciles à mettre en forme. Vous pouvez facilement personnaliser leur apparence en fonction des directives de marque de votre entreprise. Ils n’ont aucune dépendance tierce. Tout développeur connaissant JavaScript et CSS peut facilement personnaliser ces composants.

![Pourquoi créer un Forms adaptatif basé sur les composants principaux ? Ces composants sont légers, plus faciles à mettre en forme, offrent un score lighthouse élevé, prennent en charge les normes d’accessibilité, sont facilement personnalisables, open-source, disponibles sur github, ne dépendent pas de bibliothèques tierces et n’ont presque pas de courbe d’apprentissage pour les développeurs AEM et les auteurs AEM. En plus, les composants principaux AEM Forms ont toutes les fonctionnalités des composants principaux AEM WCM.](/help/forms/assets/cc-core-components-benefits.png){width="50%"}

## Cas pratique : pré-qualification rationalisée des prêts immobiliers avec le Forms adaptatif

Dans ce tutoriel, vous allez créer un formulaire adaptatif pour une grande banque. Le cas d’utilisation est le suivant :

Les acheteurs potentiels visitent le site Web ou la succursale de la banque pour explorer les options de prêt immobilier. Le processus de demande traditionnel est long et accablant et nécessite souvent de la documentation préalable. Cela dissuade certains acheteurs de commencer le processus, ce qui entrave à la fois la génération de leads de la banque et la capacité de l&#39;acheteur à rechercher en toute confiance la maison de ses rêves.

Vous êtes chargé d&#39;élaborer un formulaire interactif de préqualification de prêt immobilier. Ce formulaire recueillerait des renseignements de base, préqualifierait l&#39;emprunteur en fonction de ses données, offrirait des montants estimatifs de prêt, des besoins potentiels de mise de fonds et des taux d&#39;intérêt en fonction de différents types de prêt. Les utilisateurs présélectionnés pourraient présenter une demande de prêt complète directement à partir du formulaire de présélection.

Le formulaire est créé à l’aide de formulaires adaptatifs. Cela permet une expérience personnalisée tout en collectant les données financières nécessaires pour une pré-qualification précise du prêt immobilier.

Une fois le tutoriel terminé, votre formulaire se présente et fonctionne comme suit :

![Ajoutez un formulaire de travail ici](/help/forms/assets/cc-tutorial-final-form.png)

## Configurer l’environnement de développement

Vous pouvez créer et tester le formulaire adaptatif directement sur votre ordinateur local, avant de le déployer dans un environnement Cloud Service. Adobe fournit un SDK AEM à pour le développement local qui vous permet de :

* Créez, personnalisez et testez des formulaires localement.
* Conception de thèmes de formulaires et création de configurations localement
* Déployez facilement vos ressources terminées dans le cloud.

Le développement local avec AEM SDK vous fait gagner du temps et simplifie le processus de développement


**Prêt à commencer ?**

1. [Configuration des outils de développement pour les projets AEM](/help/forms/setup-local-development-environment.md#set-up-development-tools-for-aem-projects) : téléchargez et installez la dernière version de [Java 11™](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=fr#local-development-environment-set-up), [Git](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=fr#install-git), [Node.js (npm)](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=fr#node-js) et [Maven](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=fr#install-maven). Installez également un éditeur de texte brut. Les exemples de ce tutoriel sont basés sur Visual Studio Code.

1. [Installer le SDK AEM](/help/forms/setup-local-development-environment.md#set-up-local-experience-manager-environment-for-development) : téléchargez et installez la dernière version d’AEM SDK. Vous disposez ainsi des outils indispensables au développement d’AEM. Notez la version d’AEM SDK.

   ![Distribution-Logicielle](/help/forms/assets/software-distribution.png)

   ![installer AEM SDK](/help/forms/assets/start-aem-sdk.png)

1. [Ajouter le module complémentaire AEM Forms](/help/forms/setup-local-development-environment.md#add-forms-archive-to-local-author-and-publish-instances-and-configure-forms-specific-users) : téléchargez et installez le module complémentaire AEM Forms correspondant à la version de votre SDK AEM à partir du portail [Distribution logicielle](https://experience.adobe.com/#/downloads).
   ![install-aem-forms-add-on](/help/forms/assets/install-aem-forms-add-on.png)

   +++Installez le module complémentaire AEM Forms :

   Pour installer le module complémentaire AEM Forms :

   1. Arrêtez AEM SDK.
   1. Ajoutez le fichier de module complémentaire AEM Forms (.far) au dossier `AEM SDK/crx-quickstart/install`,
   1. Redémarrez AEM SDK.

   +++

1. [Configurer les autorisations d’utilisateur](/help/forms/setup-local-development-environment.md#configure-users-and-permissions) : créez des utilisateurs et utilisatrices disposant d’autorisations de développement, de création et autres et ajoutez-les à des groupes de formulaires prédéfinis.


1. [Ajout de modèles de Forms adaptatifs](/help/forms/setup-local-development-environment.md#set-up-a-development-project-for-forms-based-on-experience-manager-archetype) : utilisez AEM Archetypes 48 ou une version ultérieure pour créer un projet AEM et le déployer sur votre SDK AEM. Le projet ajoute des modèles Forms adaptatifs à votre SDK AEM.

   ![ Modèles de formulaire adaptatif ](/help/forms/assets/adaptive-forms-templates.png)

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

   Après le déploiement du projet AEM, vous pouvez voir les modèles de Forms adaptatifs dans votre environnement.

   +++


Pour obtenir des instructions détaillées et un guide détaillé sur la configuration de votre environnement de développement AEM Forms local, reportez-vous à l’article [Configuration de l’environnement de développement local pour AEM Forms](/help/forms/setup-local-development-environment.md).



## Étape suivante

Après avoir configuré l’environnement de développement, vous êtes prêt à créer un formulaire adaptatif. Dans l’article suivant, vous apprendrez à :

* Créer un formulaire adaptatif à partir du modèle vierge
* Mettre en forme des champs pour afficher et accepter facilement des informations
* Prévisualisez le formulaire.

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
