---
title: Activer Assets Ultimate
description: Découvrez comment activer Assets Ultimate pour les nouveaux clients et les clients existants.
feature: Asset Management
role: User, Admin
exl-id: 45cd8ccd-e5cf-42cd-aa7f-4ae59d0587f7
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '1402'
ht-degree: 3%

---

# Activer [!DNL Assets] as a Cloud Service Ultimate {#enable-assets-cloud-service-ultimate}

![Mettre à niveau vers Asset Cloud Service Ultimate](/help/assets/assets/upgrade-assets-cs-ultimate-package-banner.png)

Assets as a Cloud Service Ultimate vous permet d’exécuter diverses fonctionnalités essentielles de gestion des ressources numériques, telles que la gestion des ressources et des services de bibliothèque, la sécurité et la gestion des droits, les connexions Creative et Experience Cloud, l’extensibilité de l’interface utilisateur, l’automatisation pilotée par les API, les intégrations avec des applications Adobe et non Adobe, le déploiement de code personnalisé, etc. Consultez [Présentation d’Assets as a Cloud Service Ultimate](/help/assets/assets-ultimate-overview.md) pour obtenir la liste complète.

## Activer Assets Ultimate {#enable-assets-ultimate}

Les nouveaux clients Assets as a Cloud Service doivent d’abord activer Assets Ultimate en créant un nouveau programme à l’aide de Cloud Manager.

Procédez comme suit :

1. Connectez-vous à Cloud Manager en tant qu’administrateur système. Veillez à sélectionner la bonne organisation lors de la connexion.

   >[!NOTE]
   >
   >Assurez-vous d’être ajouté au profil de produit Cloud Manager approprié pour ajouter un nouveau programme. Pour plus d’informations, voir [Autorisations basées sur les rôles dans Cloud Manager](/help/onboarding/cloud-manager-introduction.md#role-based-permissions).

1. [Créez un nouveau programme](/help/journey-onboarding/create-program.md) et [ajoutez-y des environnements](/help/journey-onboarding//create-environments.md).

   Lors de la création du programme, dans l’onglet **[!UICONTROL Solutions et modules complémentaires]**, sélectionnez **[!UICONTROL Assets Ultimate]**. Vous pouvez également développer **[!UICONTROL Assets Ultimate]** et sélectionner **[!UICONTROL Content Hub]** pour activer [Content Hub](/help/assets/product-overview.md) pour la distribution de ressources.

   ![AEM Assets Ultimate](assets/aem-assets-ultimate-solutions.png)

1. Cliquez sur **[!UICONTROL Créer]** pour créer le programme. Assets Ultimate est désormais activé pour Experience Manager Assets as a Cloud Service.

L’administrateur système est automatiquement autorisé en tant qu’administrateur AEM sur Assets Ultimate et reçoit un courrier électronique lui permettant d’accéder à Admin Console pour gérer les profils de produit disponibles.

Votre instance AEM as a Cloud Service sur Admin Console comprend les profils de produit suivants :

* Administrateurs et administratrices AEM

* Utilisateurs et utilisatrices AEM

* [Utilisateurs collaborateurs et utilisatrices collaboratrices AEM Assets](#onboard-collaborator-users)

* [Utilisateurs et utilisatrices experts AEM Assets](#onboard-power-users)

  ![Profils de produit AEM Assets](assets/aem-assets-product-profiles.png)

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

## Activer Assets Ultimate pour les clients existants {#enable-assets-ultimate-existing-customers}

Les clients Assets as a Cloud Service existants peuvent effectuer la mise à niveau vers Assets Ultimate en suivant deux étapes simples. Vous pouvez accéder au programme Assets as a Cloud Service dans Cloud Manager et voir le statut de mise à niveau sur la carte Programme en fonction de la disponibilité des crédits Assets Ultimate. S’il y a suffisamment de crédits disponibles pour la mise à niveau vers Assets Ultimate, vous pouvez voir le statut comme `Assets license upgrade required`, comme illustré dans l’image suivante :

![Mise à niveau d’AEM Assets vers Assets Ultimate](assets/aem-assets-upgrade-status-ultimate.png)

Si un client existant achète une nouvelle licence pour Assets Ultimate, le statut de mise à niveau s’affiche comme `Assets license upgrade available`.

### Conditions préalables à la mise à niveau {#prerequisites-assets-upgrade}

Tous les environnements doivent être mis à niveau vers la dernière version d’AEM as a Cloud Service ou au moins vers la version `2024.10.18175`. Si vous ne répondez pas à la configuration minimale requise, contactez votre représentant Adobe pour passer à la version d’AEM requise.

### Mettre à niveau vers Assets Ultimate {#upgrade-assets-ultimate}

Procédez comme suit :

1. Après avoir basculé vers la configuration minimale requise pour la version AEM, cliquez sur le nom du programme. Une carte Mise à niveau s’affiche juste au-dessus de la section **[!UICONTROL Environnements]**, comme illustré dans l’image suivante :

   ![Mise à niveau d’AEM Assets vers Assets Ultimate](assets/aem-assets-upgrade-card.png)

1. Cliquez sur **[!UICONTROL Ajouter des profils de produit]**. Cloud Manager affiche des options permettant d’ajouter de nouveaux profils de produit à tous les environnements disponibles dans le programme ou dans des environnements individuels.

   ![options de mise à niveau d’AEM Assets](assets/aem-assets-upgrade-options.png)

1. Cliquez sur **[!UICONTROL Tous les environnements]** pour ajouter les nouveaux profils de produit à tous les environnements du programme ou **[!UICONTROL Environnements individuels]** pour ajouter les nouveaux profils de produit à des environnements sélectionnés.

   Cliquez sur **[!UICONTROL Environnements individuels]** pour afficher la liste de tous les environnements disponibles dans le programme.

1. Cliquez sur l’icône Plus d’options correspondant à un environnement et sélectionnez **[!UICONTROL Ajouter des profils de produit]** pour ajouter les nouveaux profils de produit à l’environnement sélectionné.

   ![AEM Assets sélectionnez des environnements individuels](assets/aem-assets-individual-environments.png)

   Vous pouvez également ajouter des profils de produit à des environnements sélectionnés en accédant à la section **[!UICONTROL Environnements]**, en cliquant sur l’icône Plus d’options correspondant à un environnement et en sélectionnant **[!UICONTROL Ajouter des profils de produit]**.

   Le statut de l’environnement s’affiche `Adding Product Profiles` pendant l’ajout des nouveaux profils de produit, puis s’affiche `Running` lorsque le processus est terminé.

   Vous devez ajouter des profils de produit à tous les environnements disponibles dans le programme, individuellement ou à tous les environnements ensemble, avant d’exécuter l’étape suivante.

1. Cliquez sur **[!UICONTROL Mettre à niveau]**. L’option **[!UICONTROL Mettre à niveau]** s’affiche uniquement lorsque vous ajoutez des profils de produit à tous les environnements disponibles.

   ![Dernière étape du processus de mise à niveau](assets/aem-assets-upgrade-button.png)

   Le processus de mise à niveau est terminé et vous avez correctement mis à niveau votre as a Cloud Service Assets vers Assets Ultimate. Le statut du programme affiche `Assets Ultimate`.

   ![Statut du programme après la mise à niveau](assets/program-status-post-upgrade.png)

Votre instance AEM as a Cloud Service sur Admin Console comprend maintenant les profils de produit suivants :

* Administrateurs et administratrices AEM

* Utilisateurs et utilisatrices AEM

* [Utilisateurs collaborateurs et utilisatrices collaboratrices AEM Assets](#onboard-collaborator-users)

* [Utilisateurs et utilisatrices experts AEM Assets](#onboard-power-users)

![Profils de produit AEM Assets](assets/aem-assets-product-profiles.png)

Si Content Hub doit être activé, cliquez sur l’icône Autres options (...) sur le nom du programme dans Cloud Manager et sélectionnez **[!UICONTROL Modifier le programme]**. Développez **[!UICONTROL Assets Ultimate]** puis cliquez sur **[!UICONTROL Content Hub]**. Cette étape active Content Hub pour Assets Ultimate. Une nouvelle instance a été créée dans AEM Assets as a Cloud Service sur Admin Console avec `delivery` comme suffixe :

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

1. Cliquez sur le profil de produit Utilisateurs Collaborateurs et cliquez sur **[!UICONTROL Ajouter des utilisateurs]** pour ajouter des utilisateurs ou des groupes d’utilisateurs au profil de produit.
   ![Profil de produit utilisateur](assets/aem-assets-collaborator-user-permissions.png)

1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les modifications.

Vous pouvez également accéder aux services affectés aux utilisateurs de l&#39;espace de collaboration et les afficher, comme illustré dans l&#39;image suivante :

![Services pour les utilisateurs collaborateurs](assets/aem-assets-collaborator-users.png)

Les services `Adobe Express` et `AEM Assets Collaborator Users` sont activés par défaut.

>[!NOTE]
>
>Vous pouvez activer et désactiver le bouton (bascule) pour activer ou désactiver les services disponibles, en fonction de vos besoins, mais Adobe recommande d’utiliser les services par défaut activés pour les profils de produit.


## Intégration d’AEM Assets Power users {#onboard-power-users}

Les utilisateurs expérimentés d’AEM Assets peuvent accéder à toutes les fonctionnalités d’AEM Assets, notamment la gestion des ressources, les autorisations, les métadonnées, la gouvernance globale et l’automatisation autour des ressources numériques, travailler avec des ressources d’Experience Manager par le biais d’intégrations d’Assets disponibles pour votre entreprise dans d’autres applications Adobe et non Adobe, créer et modifier des ressources à l’aide d’Adobe Express et de Firefly intégrés à l’aide de modèles conçus par des professionnels, de kits de marque, de ressources Adobe Stock, etc., et accéder aux ressources approuvées de votre entreprise et les exploiter à l’aide du portail AEM Assets Content Hub.

Pour intégrer des utilisateurs expérimentés :

1. Accédez aux profils de produit Experience Manager Assets en cliquant sur le nom du produit AEM as a Cloud Service dans la liste des produits sur Admin Console.

1. Cliquez sur l’instance d’auteur d’exploitation pour AEM as a Cloud Service :
   ![Profils de produit pour AEM as a Cloud Service](assets/aem-cloud-service-instances.png)

1. Cliquez sur le profil de produit Utilisateurs avec pouvoir et cliquez sur **[!UICONTROL Ajouter des utilisateurs]** pour ajouter des utilisateurs ou des groupes d’utilisateurs au profil de produit.
   ![Profil de produit utilisateur](assets/aem-assets-power-user-permissions.png)

1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les modifications.

Vous pouvez également accéder aux services affectés aux utilisateurs expérimentés et les afficher, comme illustré dans l’image suivante :

![Services pour les utilisateurs expérimentés](assets/aem-assets-power-users.png)

Les services `Adobe Express` et `AEM Assets Power Users` sont activés par défaut.

>[!NOTE]
>
>Vous pouvez activer et désactiver le bouton (bascule) pour activer ou désactiver les services disponibles, en fonction de vos besoins, mais Adobe recommande d’utiliser les services par défaut activés pour les profils de produit.
