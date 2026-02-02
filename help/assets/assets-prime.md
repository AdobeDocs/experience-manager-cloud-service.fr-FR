---
title: Assets Prime
description: Découvrez les principaux aspects d’Assets Prime, tels que les principaux avantages, les types d’utilisateurs et leurs privilèges.
feature: Asset Management
role: User, Admin
exl-id: 012f94c5-b1c3-4799-8eaf-af68d06c036f
source-git-commit: 504464ed1277c1d9629ae1f96892ebaa5ef701c8
workflow-type: tm+mt
source-wordcount: '1100'
ht-degree: 15%

---

# [!DNL Assets] as a Cloud Service Prime  {#assets-prime}

![image de bannière AEM Assets Prime](/help/assets/assets/aem-assets-prime-package-banner.png)

Assets as a Cloud Service Prime comprend une gestion des ressources numériques allégée qui vous permet d’exécuter diverses fonctionnalités essentielles, telles que :

* **Gestion des ressources et services de bibliothèque** : outils qui permettent aux utilisateurs et utilisatrices d’ingérer, de stocker, de cataloguer, de contrôler, de gérer et de gouverner les ressources numériques d’une marque dans un référentiel centralisé.

* **Recherche, découverte et collaboration** : outils qui permettent aux utilisateurs et utilisatrices de parcourir, de découvrir, de partager et de collaborer sur les ressources dont ils ont besoin pour créer des expériences client riches.

* **Sécurité et Rights Management** : outils de gestion de l’accès, des autorisations, des droits et de la sécurité pour garantir la conformité, la cohérence et l’intégrité de la marque.

* **Connexions Creative Cloud** : outils qui permettent aux équipes marketing et créatives de collaborer avec un accès, des commentaires, des révisions et des annotations simplifiés pour mettre à jour ou finaliser des ressources numériques.

* **Connexions Experience Cloud** : outils permettant de prendre en charge l’accès natif aux ressources numériques à partir d’autres applications et services Experience Cloud.

* **Expérience de portail de distribution sans options d’extensibilité (Content Hub)** : outils permettant d’étendre l’accès aux ressources numériques approuvées d’une marque à des parties prenantes étendues afin d’assurer l’utilisation et la cohérence de la marque.

* **Intégrations** : intégrations à d’autres applications Adobe et autres qu’Adobe.

* **Dynamic Media (module complémentaire)** : outils permettant de transformer et de diffuser des images, des vidéos et d’autres contenus émergents pour des expériences multimédias riches, interactives et à grande échelle sur n’importe quel appareil.

  >[!NOTE]
  >
  >Dynamic Media avec des fonctionnalités OpenAPI, qui permet d’accéder aux modificateurs d’image de base tels que rotation, recadrage (manuel uniquement, pas de recadrage intelligent), retournement, hauteur, largeur, qualité, format et diffusion en continu de vidéo adaptative, est également disponible avec Assets Prime. Contactez l’équipe du compte Adobe pour en savoir plus.

Cependant, à mesure que vos besoins en gestion des ressources numériques augmentent et que vous avez besoin de davantage de fonctionnalités, telles que l’extensibilité de l’interface utilisateur, l’automatisation pilotée par les API et le déploiement de code personnalisé, vous devez envisager une mise à niveau vers [Assets Ultimate](/help/assets/assets-ultimate-overview.md).

Cet article fournit un workflow de bout en bout pour activer Assets as a Cloud Service Prime.

## Activer Assets as a Cloud Service Prime{#enable-assets-prime}

Activez Assets Prime lors de la création d’un programme à l’aide de Cloud Manager. Procédez comme suit :

1. Connectez-vous à Cloud Manager en tant qu’administrateur système. Veillez à sélectionner la bonne organisation lors de la connexion.

   >[!NOTE]
   >
   >Assurez-vous d’être ajouté au profil de produit Cloud Manager approprié pour ajouter un nouveau programme. Pour plus d’informations, voir [Autorisations basées sur les rôles dans Cloud Manager](/help/onboarding/cloud-manager-introduction.md#role-based-permissions).

1. [Créer un nouveau programme](/help/journey-onboarding/create-program.md).

   Lors de la création du programme, dans l’onglet **[!UICONTROL Solutions et modules complémentaires]**, sélectionnez **[!UICONTROL Assets Prime]**. Vous pouvez également développer **[!UICONTROL Assets Prime]** et sélectionner **[!UICONTROL Content Hub]** pour activer [Content Hub](/help/assets/product-overview.md) pour la distribution de ressources.

   ![AEM Assets Ultimate](assets/aem-assets-prime.png)


1. Cliquez sur **[!UICONTROL Créer]** pour créer le programme.

1. Cliquez sur la carte du programme, puis sur **[!UICONTROL Ajouter un environnement]**.

1. Indiquez le nom de l’environnement, définissez une région et cliquez sur **[!UICONTROL Enregistrer]** pour créer l’environnement.

   ![Ajouter un environnement à Assets Prime](assets/aem-assets-prime-add-environment.png)

>[!NOTE]
>
>Assets Prime vous permet uniquement de créer un environnement de production. L’option Ajouter un environnement n’est plus disponible une fois l’environnement de production créé.

Assets Prime est désormais activé pour Experience Manager Assets as a Cloud Service.

![AEM Assets Prime est disponible](assets/aem-assets-prime-setup-complete.png)

L’administrateur système est automatiquement désigné comme administrateur AEM et reçoit un courrier électronique lui permettant d’accéder à Admin Console pour gérer les profils de produit.


Votre instance AEM as a Cloud Service sur Admin Console comprend les profils de produit suivants :

* Administrateurs et administratrices AEM

* Utilisateurs et utilisatrices AEM

* [Utilisateurs collaborateurs et utilisatrices collaboratrices AEM Assets](#onboard-collaborator-users)

* [Utilisateurs et utilisatrices experts AEM Assets](#onboard-power-users)


![Profils de produit AEM Assets](assets/aem-assets-product-profiles.png)

Vous pouvez commencer à ajouter des utilisateurs ou des groupes d’utilisateurs aux profils de produits AEM Assets Collaborator Users et AEM Assets Power Users. Pour plus d’informations, consultez [Intégration d’utilisateurs AEM Assets Collaborator](#onboard-collaborator-users) et [Intégration d’utilisateurs avancés d’AEM Assets](#onboard-power-users).

Si vous avez activé Content Hub pour Assets as a Cloud Service, une nouvelle instance est créée dans AEM Assets as a Cloud Service sur Admin Console avec `delivery` comme suffixe :

![Nouvelle instance pour Content Hub &#x200B;](assets/new-instance-content-hub.png)

>[!NOTE]
>
>Si vous avez configuré Content Hub avant le 14 août 2024, la nouvelle instance est créée avec `contenthub` comme suffixe.

Notez qu’il n’y a aucun `author` ni `publish` dans le nom de l’instance pour Content Hub.

Cliquez sur le nom de l’instance pour afficher le profil de produit Content Hub `AEM Assets Limited Users`.

![Profil de produit Content Hub](assets/content-hub-product-profile.png)

Vous pouvez commencer à ajouter des utilisateurs ou des groupes d’utilisateurs à ce profil de produit pour leur fournir l’accès à Content Hub.

>[!NOTE]
>
>Si vous avez configuré Content Hub avant le 14 août 2024, le profil de produit Content Hub a `contenthub` mentionné après `Limited Users` au lieu de `delivery`.

## Intégration d’utilisateurs AEM Assets Collaborator {#onboard-collaborator-users}

Les utilisateurs d’AEM Assets Collaborator peuvent travailler avec des ressources d’Experience Manager par le biais d’intégrations d’Assets disponibles pour votre organisation dans d’autres produits Adobe et applications non Adobe, créer et modifier des ressources à l’aide d’Adobe Express et de Firefly intégrés, en utilisant des modèles conçus par des professionnels, des kits de marque, des ressources Adobe Stock, etc., et accéder aux ressources approuvées de votre organisation et les exploiter à l’aide du portail AEM Assets Content Hub.

Pour intégrer des utilisateurs collaborateurs :

1. Accédez aux profils de produit Experience Manager Assets en cliquant sur le nom du produit AEM as a Cloud Service dans la liste des produits sur Admin Console.

1. Cliquez sur l’instance d’auteur d’exploitation pour AEM as a Cloud Service :
   ![Profils de produit pour AEM as a Cloud Service](assets/aem-cloud-service-instances.png)

1. Cliquez sur le profil de produit Utilisateurs collaborateurs et cliquez sur **[!UICONTROL Ajouter des utilisateurs]** pour ajouter l’utilisateur au profil de produit.
   ![Profil de produit utilisateur](assets/aem-assets-collaborator-user-permissions.png)

1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les modifications.

Vous pouvez également accéder aux services affectés aux utilisateurs de l&#39;espace de collaboration et les afficher, comme illustré dans l&#39;image suivante :

![Services pour les utilisateurs collaborateurs](assets/aem-assets-collaborator-users.png)

Les services `Adobe Express` et `AEM Assets Collaborator Users` sont activés par défaut. Vous pouvez activer et désactiver le bouton (bascule) selon vos besoins. Toutefois, Adobe recommande d’utiliser les services par défaut activés pour les profils de produit.

## Intégration d’AEM Assets Power users {#onboard-power-users}

Les utilisateurs expérimentés d’AEM Assets peuvent accéder à toutes les fonctionnalités d’AEM Assets, notamment la gestion des ressources, les autorisations, les métadonnées, la gouvernance globale et l’automatisation autour des ressources numériques, travailler avec des ressources d’Experience Manager par le biais d’intégrations d’Assets disponibles pour votre entreprise dans d’autres applications Adobe et non Adobe, créer et modifier des ressources à l’aide d’Adobe Express et de Firefly intégrés à l’aide de modèles conçus par des professionnels, de kits de marque, de ressources Adobe Stock, etc., et accéder aux ressources approuvées de votre entreprise et les exploiter à l’aide du portail AEM Assets Content Hub.

Pour intégrer des utilisateurs expérimentés :

1. Accédez aux profils de produit Experience Manager Assets en cliquant sur le nom du produit AEM as a Cloud Service dans la liste des produits sur Admin Console.

1. Cliquez sur l’instance d’auteur d’exploitation pour AEM as a Cloud Service :
   ![Profils de produit pour AEM as a Cloud Service](assets/aem-cloud-service-instances.png)

1. Cliquez sur le profil de produit Utilisateurs avec pouvoir et cliquez sur **[!UICONTROL Ajouter des utilisateurs]** pour ajouter l’utilisateur au profil de produit.
   ![Profil de produit utilisateur](assets/aem-assets-power-user-permissions.png)

1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les modifications.

Vous pouvez également accéder aux services affectés aux utilisateurs expérimentés et les afficher, comme illustré dans l’image suivante :

![Services pour les utilisateurs expérimentés](assets/aem-assets-power-users.png)

Les services `Adobe Express` et `AEM Assets Power Users` sont activés par défaut. Vous pouvez activer et désactiver le bouton (bascule) selon vos besoins. Toutefois, Adobe recommande d’utiliser les services par défaut activés pour les profils de produit.
