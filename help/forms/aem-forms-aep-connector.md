---
title: Connexion d’AEM Forms à Adobe Experience Platform (AEP) | Guide d’intégration des données
description: Découvrez comment intégrer AEM Forms à Adobe Experience Platform pour exploiter les profils client, envoyer des données de formulaire et créer des expériences personnalisées. Guide détaillé.
contentOwner: Khushwant Singh
docset: CloudService
role: Admin, Developer, User
feature: Adaptive Forms, Core Components
exl-id: b0eb19d3-0297-4583-8471-edbb7257ded4
source-git-commit: dabf8029577c5fb6bb5eebdbf10d77f3d4d95a5d
workflow-type: tm+mt
source-wordcount: '2047'
ht-degree: 2%

---

# Intégration d’AEM Forms à Adobe Experience Platform (AEP) {#aem-forms-aep-integration}

<span class="preview"> La possibilité de connecter Adaptive Forms (AEM Forms) à Adobe Experience Platform (AEP) s’inscrit dans le cadre du programme d’accès anticipé. Pour demander l’accès à la fonctionnalité, envoyez simplement un e-mail à partir de votre adresse officielle à [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com?subject=Request%20for%20Early%20Access%20to%20AEP%20Connector%20\(AEM%20Forms%20Integration%20with%20Adobe%20Experience%20Platform\)&body=Dear%20AEM%20Forms%20Team%2C%0D%0A%0D%0AI%20hope%20this%20message%20finds%20you%20well.%0D%0A%0D%0AI%20am%20writing%20to%20request%20access%20to%20the%20Early%20Access%20Program%20for%20the%20AEP%20Connector%2C%20which%20enables%20integration%20between%20AEM%20Forms%20and%20Adobe%20Experience%20Platform.%0D%0A%0D%0AOrganization%20Name%3A%20%5BYour%20organization%20name%5D%0D%0AOrganization%20ID%3A%20%5BYour%20organization%20ID%2C%20if%20available%5D%0D%0AUse%20Case%3A%20%5BBriefly%20describe%20your%20intended%20use%20case%2C%20including%20goals%20or%20benefits%20you%20aim%20to%20achieve%20with%20the%20integration%5D%0D%0A%0D%0AThank%20you%20for%20your%20time%20and%20consideration.%0D%0A%0D%0ABest%20regards%2C%0D%0A%5BYour%20Full%20Name%5D%0D%0A%5BYour%20Job%20Title%2C%20if%20applicable%5D%0D%0A%5BYour%20Contact%20Information%2C%20if%20appropriate%5D). Vous pouvez également consulter la page <a href="/help/forms/early-access-ea-features.md">Programme d’accès anticipé</a> pour découvrir toutes les innovations et fonctionnalités disponibles. . </span>

## Vue d’ensemble {#overview}

Vous pouvez connecter AEM Forms à Adobe Experience Platform afin de transformer vos expériences de formulaires. Cette puissante intégration permet aux entreprises d’exploiter les profils clients en temps réel pour offrir des expériences de formulaire personnalisées, de rationaliser l’envoi de données **AEM Forms vers Experience Platform** et de créer des enregistrements de clients unifiés dans l’écosystème Adobe. En connectant vos formulaires adaptatifs aux puissantes fonctionnalités de gestion des données d’Experience Platform, vous pouvez créer des expériences plus pertinentes et améliorer les taux de conversion, tout en conservant une source unique de vérité pour les données client.

### Qu’est-ce qu’AEM Forms Connector for Adobe Experience Platform (AEP) ? {#what-is-connector}

Le connecteur AEM Forms pour Adobe Experience Platform (AEP) est un connecteur prêt à l’emploi fourni par AEM Forms qui permet une intégration transparente entre AEM Forms et Adobe Experience Platform (AEP). Cette intégration vous permet de créer des formulaires à l’aide des schémas XDM disponibles dans AEP et de renvoyer des données à AEP à des fins de personnalisation et d’hydratation de profil.

## Pourquoi connecter AEM Forms à Adobe Experience Platform (AEP) ? {#benefits}

La connexion de votre Forms adaptative à Adobe Experience Platform présente des avantages significatifs pour votre entreprise et vos clients :

* **Profils client unifiés** - Enrichissez les profils client avec des données d’envoi de formulaire, pour créer une vue complète des interactions et des préférences des clients
* **Expériences de formulaire personnalisées** - Tirez parti des données de profil existantes pour préremplir les champs et personnaliser les formulaires en fonction des informations connues du client
* **Collecte de données rationalisée** - Capturez les données de formulaire directement dans les jeux de données AEP sans créer de connecteurs personnalisés ou de code d’intégration
* **Activation des données en temps réel** - Envoyez les données d’envoi de formulaire à d’autres applications Adobe via Real-Time CDP pour une activation immédiate
* **Gestion simplifiée de la conformité** - Gérez de manière centralisée les politiques de consentement et de gouvernance des données via AEP
* **Temps de développement réduit** - Éliminez le travail d’intégration personnalisé avec un connecteur préconfiguré qui suit les bonnes pratiques
* **Enrichissement du profil client avec des données de formulaire** - Mettez automatiquement à jour et améliorez les profils client à chaque envoi de formulaire, ce qui crée des informations client plus riches

## Fonctions clés {#key-features}

* Création de formulaires à l’aide de schémas XDM d’AEP
* Envoi de données de formulaire à AEP pour personnalisation
* Prise en charge de l’ingestion de données en flux continu
* Activer l’hydratation des profils pour améliorer les expériences utilisateur
* Intégration au système de profils d’AEP
* Intégration du schéma XDM aux formulaires adaptatifs pour une collecte de données normalisée
* Connexion en continu AEP pour formulaires permettant le traitement des données en temps réel

La vidéo ci-dessous présente un guide détaillé sur les conditions préalables (telles que la création d’un schéma, la configuration des données et l’authentification) et montre comment créer et connecter le Forms adaptatif à Adobe Experience Platform (AEP)

>[!VIDEO](https://video.tv.adobe.com/v/3457850/)

<span> Cette vidéo s’applique uniquement aux composants principaux. Pour les composants UE/Foundation, reportez-vous à l’article </span>.

## Prérequis {#prerequisites}

Avant de configurer le connecteur AEP dans AEM Forms, vérifiez que vous avez effectué les opérations suivantes dans Adobe Experience Platform :

1. Configuration du schéma
   * [Créer un schéma XDM](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/create-schema-ui)
   * [Activer le schéma pour le profilage](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/create-schema-ui#profile)
   * [Définir un champ d’identité](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/create-schema-ui#profile)

2. Configuration des données
   * [Créer un jeu de données](https://experienceleague.adobe.com/en/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/create-datasets)
   * [Configurer une connexion en continu](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/tutorials/create-streaming-connection) (vous aurez besoin de l’URL du point d’entrée en continu ultérieurement, alors prenez-en note maintenant.)

3. Authentification
   * [Générer des informations d’identification d’API](https://experienceleague.adobe.com/en/docs/experience-platform/landing/platform-apis/api-authentication#generate-credentials) (identifiant client et secret client) à partir de Adobe Developer Console


## Étapes de mise en œuvre

### &#x200B;1. Création d’une configuration cloud AEP

1. Accédez à votre **instance Adobe Experience Manager** > **Outils** > **Services cloud** > **Adobe Experience Platform**.
1. Sélectionnez un **Conteneur de configurations** pour stocker la configuration.
1. Cliquez sur **Créer** pour lancer l’assistant de configuration AEP
1. Saisissez les informations suivantes :
   * Titre
   * Identifiant client (obtenu à partir de la Developer Console)
   * Secret client (obtenu à partir de la console de développement)
   * URL OAuth (il existe une URL par défaut, mais elle peut également être obtenue à partir de la Developer Console).

   ![Configuration d’AEP Cloud](/help/forms/assets/aep-cloud-configuration.png)

1. Cliquez sur **Connexion** pour établir la connexion. Après avoir établi la connexion, configurez les paramètres supplémentaires suivants :
   * URL de base : platform.adobe.io (il s’agit d’une URL par défaut qui peut être obtenue à partir de Developer Console. En outre, les URL oauth et platform sont définies par défaut sur les URL de production. Si nécessaire, vous devez vous connecter à l’environnement d’évaluation. Les URL d’évaluation doivent être utilisées.)
   * ID d’organisation (obtenu à partir de la Developer Console avec l’ID client/secret)
   * Nom du sandbox (requis pour les environnements de développement et de production)

### &#x200B;2. Création de formulaire avec intégration de schéma XDM {#form-creation}

>[!BEGINTABS]

>[!TAB Composant de base]

Pour créer un formulaire adaptatif basé sur des composants de base avec une intégration de schéma, procédez comme suit :

1. Accédez à l’assistant de création de formulaire :
   * Accédez à votre **instance Adobe Experience Manager** > **Forms** > **Forms et documents**.
   * Cliquez sur **Créer** > **Formulaire adaptatif**.
1. Dans l’onglet **source**, sélectionnez un modèle de base.
1. Dans l’onglet **Données**, sélectionnez l’option **Adobe Experience Platform**.
1. Dans le volet des propriétés, sélectionnez votre configuration cloud.

   ![](/help/forms/assets/xdm-schema-integration.png)

   Le système charge tous les schémas disponibles à partir de Adobe Experience Platform

   >[!NOTE]
   >
   >
   > * Seuls les schémas activés et non générés par le système sont récupérés.
   > * Le chargement initial du schéma peut prendre un certain temps lors de la première configuration.

1. Sélectionnez les champs appropriés/obligatoires du schéma. (Voir la vidéo pour obtenir des instructions détaillées)
1. Dans l’onglet Envoi :
   * Sélectionnez l’action d’envoi **Envoyer à Adobe Experience Platform**
   * Configurez les paramètres d’envoi du formulaire pour l’envoi de données **AEM Forms vers Experience Platform**
1. Dans le volet des propriétés :
   * Ajoutez l’URL de streaming (obtenue à partir de Sources AEP > Connexion de streaming)
   * Ajoutez l’identifiant du flux de données (accessible dans Sources AEP > Flux > Informations d’utilisation de l’API)
1. Cliquez sur **Enregistrer**. Fournissez les détails du formulaire :
   * Titre
   * Nom
   * Chemin de stockage
1. Ajoutez le bouton d’envoi au formulaire. Votre formulaire est prêt à envoyer des données à AEP.

>[!TAB Composant principal]

Pour créer un formulaire adaptatif basé sur les composants principaux avec intégration de schéma, procédez comme suit :

1. Accédez à l’assistant de création de formulaire :
   * Accédez à votre **instance Adobe Experience Manager** > **Forms** > **Forms et documents**.
   * Cliquez sur **Créer** > **Formulaire adaptatif**.
1. Dans l’onglet **source**, sélectionnez un modèle basé sur les composants principaux.
1. Dans l’onglet **Données**, sélectionnez l’option **Adobe Experience Platform**.
1. Dans le volet des propriétés, sélectionnez votre configuration cloud.

   ![](/help/forms/assets/xdm-schema-integration.png)

   Le système charge tous les schémas disponibles à partir de Adobe Experience Platform

   >[!NOTE]
   >
   >
   > * Seuls les schémas activés et non générés par le système sont récupérés.
   > * Le chargement initial du schéma peut prendre un certain temps lors de la première configuration.

1. Sélectionnez les champs appropriés/obligatoires du schéma. (Voir la vidéo pour obtenir des instructions détaillées)
1. Dans l’onglet Envoi :
   * Sélectionnez l’action d’envoi **Envoyer à Adobe Experience Platform**
   * Configurez les paramètres d’envoi du formulaire pour l’envoi de données **AEM Forms vers Experience Platform**
1. Dans le volet des propriétés :
   * Ajoutez l’URL de streaming (obtenue à partir de Sources AEP > Connexion de streaming)
   * Ajoutez l’identifiant du flux de données (accessible dans Sources AEP > Flux > Informations d’utilisation de l’API)
1. Cliquez sur **Enregistrer**. Fournissez les détails du formulaire :
   * Titre
   * Nom
   * Chemin de stockage
1. Ajoutez le bouton d’envoi au formulaire. Votre formulaire est prêt à envoyer des données à AEP.

>[!TAB Éditeur universel]

Pour créer un formulaire adaptatif à l’aide de l’éditeur universel avec l’intégration de schémas, procédez comme suit :

1. Accédez à l’assistant de création de formulaire :
   * Accédez à votre **instance Adobe Experience Manager** > **Forms** > **Forms et documents**.
   * Cliquez sur **Créer** > **Formulaire adaptatif**.
1. Dans l’onglet **source**, sélectionnez le modèle basé sur Edge Delivery.
1. Dans l’onglet **Données**, sélectionnez l’option **Adobe Experience Platform**.
1. Dans le volet des propriétés, sélectionnez votre configuration cloud.

   ![intégration de schéma](/help/forms/assets/xdm-schema-integration.png)

   Le système charge tous les schémas disponibles à partir de Adobe Experience Platform

   >[!NOTE]
   >
   >
   > * Seuls les schémas activés et non générés par le système sont récupérés.
   > * Le chargement initial du schéma peut prendre un certain temps lors de la première configuration.

1. Sélectionnez les champs appropriés/obligatoires du schéma. (Voir la vidéo pour obtenir des instructions détaillées)
1. Dans l’onglet Envoi :
   * Sélectionnez l’action d’envoi **Envoyer à Adobe Experience Platform**
   * Configurez les paramètres d’envoi du formulaire pour l’envoi de données **AEM Forms vers Experience Platform**

     >[!NOTE]
     >
     >* Si l’icône Sources de données ne s’affiche pas dans l’interface de l’éditeur universel ou si la propriété Référence de liaison s’affiche dans le panneau de propriété de droite, activez l’extension **Source de données** dans Extension Manager.
     >* Si l’icône **Modifier les propriétés de formulaire** ne s’affiche pas dans l’interface de l’éditeur universel, activez l’extension **Modifier les propriétés de formulaire** dans Extension Manager.
     > 
     > * Consultez l’article [Caractéristiques des fonctionnalités d’Extension Manager](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions) pour savoir comment activer ou désactiver les extensions dans l’éditeur universel.

   Le service de préremplissage des formulaires dans l’éditeur universel n’est actuellement pas pris en charge.

1. Dans le volet des propriétés :
   * Ajoutez l’URL de streaming (obtenue à partir de Sources AEP > Connexion de streaming)
   * Ajoutez l’identifiant du flux de données (accessible dans Sources AEP > Flux > Informations d’utilisation de l’API)
1. Cliquez sur **Enregistrer**. Fournissez les détails du formulaire :
   * Titre
   * Nom
   * Chemin de stockage
1. Ajoutez le bouton d’envoi au formulaire. Votre formulaire est prêt à envoyer des données à AEP.

>[!ENDTABS]

## Remarques importantes {#important-notes}

* Les données envoyées par le biais de formulaires deviennent visibles dans AEP après environ 10 à 15 minutes
* Par défaut, seuls les schémas activés pour le profil sont répertoriés
* Bien que l’envoi de données fonctionne pour tous les schémas, la fonctionnalité de préremplissage est limitée aux schémas activés pour les profils
* Les données contenues dans des schémas non activés pour les profils ne seront pas utilisées pour la création de profils, même si le schéma est activé ultérieurement pour le profilage
* **L’enrichissement du profil client avec des données de formulaire** nécessite une configuration de champ d’identité appropriée dans votre schéma XDM
* **L’envoi de données AEM Forms à Experience Platform** utilise la connexion en continu **AEP pour les formulaires** afin d’assurer le flux de données en temps réel

## Bonnes pratiques {#best-practices}

1. Planifiez soigneusement la structure de votre schéma avant d’activer le profilage
1. Tenez compte des exigences de volume de données et de mise à l’échelle du système lors de la configuration de la connexion en continu **AEP pour les formulaires**
1. Testez minutieusement l’intégration avant le déploiement en production
1. Surveiller les processus d’ingestion de données et de création de profils
1. Concevez votre **intégration de schéma XDM avec des formulaires adaptatifs** pour collecter uniquement les données nécessaires
1. Utilisez l’**enrichissement du profil client avec des données de formulaire** de manière stratégique pour améliorer la personnalisation

## Considérations techniques {#technical-considerations}

* Le connecteur utilise des API de streaming publiques pour l’envoi de données
* La création du profil est basée sur le champ d’identité
* L’unification des données se produit automatiquement dans AEP
* L’intégration prend en charge la création de formulaires et la modification de formulaires existants
* L’intégration du schéma XDM aux formulaires adaptatifs normalise la structure des données entre différents points de contact
* La connexion en continu AEP pour forms fournit des fonctionnalités d’ingestion de données en temps réel

## Questions fréquentes {#faq}

### Questions générales {#general-questions}

**Q : « Ce connecteur est-il disponible avec plusieurs offres d’AEM Forms ?**
R : Non, cette intégration n’est disponible que pour AEM Forms as a Cloud Service et est comprise dans le programme d’accès anticipé.

**Q : Ce connecteur fonctionne-t-il avec les composants principaux de Forms adaptatif et les composants de base ?**
R : Ce connecteur fonctionne avec les composants principaux de Forms adaptatif et les composants de base de Forms adaptatif.

**Q : Puis-je envoyer des données à plusieurs jeux de données AEP à partir d’un seul formulaire ?**
R : Actuellement, chaque formulaire ne peut envoyer qu’à un seul jeu de données.

**Q : Existe-t-il une limite au nombre d’envois de formulaire pouvant être traités ?**
R : Les envois de formulaires sont soumis à l’ingestion par flux d’AEP [quotas et limites de débit](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/api/quota).

<!-- >
**Q: Can form attachments be sent to AEP?**
A: No, form attachments cannot be directly sent to AEP. You would need to store attachments separately and only send metadata to AEP. -->

### Questions relatives à la mise en œuvre {#implementation-questions}

**Q : Comment résoudre les problèmes de connexion entre AEM Forms et AEP ?**
R : Vérifiez les paramètres de configuration de votre cloud, assurez-vous que les informations d’identification de l’API sont correctes et que l’URL du point d’entrée de streaming est correctement configurée.

**Q : Puis-je utiliser des schémas XDM personnalisés avec cette intégration ?**
R : Oui, vous pouvez utiliser n’importe quel schéma XDM personnalisé tant qu’il est correctement configuré dans AEP et, pour la fonctionnalité de préremplissage, activé pour les profils.

**Q : Comment activer le préremplissage de formulaire avec les données de profil AEP ?**
R : Assurez-vous que votre schéma est activé pour le profil et que votre formulaire est configuré pour utiliser le même champ d’identité que celui défini dans votre schéma.

**Q : Que se passe-t-il si je dois transformer des données avant de les envoyer à AEP ?**
R : Vous pouvez utiliser des règles de formulaire ou des fonctions personnalisées pour transformer les données avant envoi. Pour les transformations complexes, pensez à utiliser une action d’envoi personnalisée.

**Q : Puis-je utiliser cette intégration dans un modèle de déploiement hybride ?**
R : Non, cette intégration est spécifique à AEM Forms as a Cloud Service.

## Résumé et étapes suivantes {#summary-next-steps}

L’intégration d’AEM Forms à Adobe Experience Platform permet aux entreprises de créer un flux de données transparent entre les formulaires et l’écosystème Experience Platform au sens large. Cette intégration vous permet de créer des expériences de formulaire plus personnalisées, de rationaliser la collecte de données et d’améliorer les profils client avec des données d’envoi de formulaire précieuses.

Pour commencer à utiliser cette intégration :

1. **Demander l&#39;accès** - Si vous ne l&#39;avez pas déjà fait, rejoignez le programme d&#39;accès anticipé en contactant [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com?subject=Request%20for%20Early%20Access%20to%20AEP%20Connector%20\(AEM%20Forms%20Integration%20with%20Adobe%20Experience%20Platform\)&body=Dear%20AEM%20Forms%20Team%2C%0D%0A%0D%0AI%20hope%20this%20message%20finds%20you%20well.%0D%0A%0D%0AI%20am%20writing%20to%20request%20access%20to%20the%20Early%20Access%20Program%20for%20the%20AEP%20Connector%2C%20which%20enables%20integration%20between%20AEM%20Forms%20and%20Adobe%20Experience%20Platform.%0D%0A%0D%0AOrganization%20Name%3A%20%5BYour%20organization%20name%5D%0D%0AOrganization%20ID%3A%20%5BYour%20organization%20ID%2C%20if%20available%5D%0D%0AUse%20Case%3A%20%5BBriefly%20describe%20your%20intended%20use%20case%2C%20including%20goals%20or%20benefits%20you%20aim%20to%20achieve%20with%20the%20integration%5D%0D%0A%0D%0AThank%20you%20for%20your%20time%20and%20consideration.%0D%0A%0D%0ABest%20regards%2C%0D%0A%5BYour%20Full%20Name%5D%0D%0A%5BYour%20Job%20Title%2C%20if%20applicable%5D%0D%0A%5BYour%20Contact%20Information%2C%20if%20appropriate%5D)
2. **Préparation de votre environnement** - Assurez-vous de disposer des autorisations et des configurations nécessaires dans AEM Forms et Adobe Experience Platform
3. **Suivez les étapes d’implémentation** - Utilisez le guide ci-dessus pour configurer votre cloud et créer votre premier formulaire connecté à AEP avec l’intégration de schéma XDM
4. **Test approfondi** - Validez les fonctionnalités d’envoi et de préremplissage des données dans un environnement de développement
5. **Planifier la production** - Collaborez avec votre équipe d’implémentation pour planifier le déploiement en production de l’envoi de données d’AEM Forms à Experience Platform

## Ressources connexes {#related-resources}

* [Documentation AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/home.html?lang=fr)
* [Documentation Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/landing/home.html?lang=fr)
* [ Présentation du système XDM ](https://experienceleague.adobe.com/docs/experience-platform/xdm/home.html?lang=fr)
* [Ingestion par flux dans Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/ingestion/streaming/overview.html)
* [Présentation du profil client en temps réel](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html)
* [Fonctionnalités d’accès anticipé AEM Forms](/help/forms/early-access-ea-features.md)
* [Création d’un Forms adaptatif avec des composants principaux](/help/forms/creating-adaptive-form-core-components.md)
* [Utilisation de modèles de données de formulaire dans AEM Forms](/help/forms/using-form-data-model.md)

<!--
Schema markup for technical documentation
{
  "@context": "https://schema.org",
  "@type": "TechArticle",
  "headline": "Connect AEM Forms with Adobe Experience Platform (AEP) | Data Integration Guide",
  "description": "Learn how to integrate AEM Forms with Adobe Experience Platform to leverage customer profiles, submit form data, and create personalized experiences.",
  "datePublished": "2025-05-28",
  "author": {
    "@type": "Corporation",
    "name": "Adobe"
  },
  "publisher": {
    "@type": "Organization",
    "name": "Adobe Experience League",
    "logo": {
      "@type": "ImageObject",
      "url": "https://experienceleague.adobe.com/assets/img/favicons/apple-touch-icon.png"
    }
  },
  "mainEntityOfPage": {
    "@type": "WebPage",
    "@id": "https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/aem-forms-aep-connector.html"
  },
  "articleSection": "AEM Forms",
  "keywords": "AEM Forms, Adobe Experience Platform, XDM schema, data integration, form submission, customer profiles, personalization"
}
-->
