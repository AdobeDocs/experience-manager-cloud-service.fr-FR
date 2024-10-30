---
title: Enable Assets Ultimate
description: Learn how to enable Assets Ultimate for new and existing customers.
feature: Asset Management
role: User, Admin
source-git-commit: 16ce83409044ad54140754112eb4d35b97883b44
workflow-type: tm+mt
source-wordcount: '1420'
ht-degree: 3%

---

# [!DNL Assets] {#enable-assets-cloud-service-ultimate}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [Bonnes pratiques relatives aux métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Fonctionnalités Dynamic Media avec OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation de développement pour AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

![](/help/assets/assets/upgrade-assets-cs-ultimate-package-banner.png)

Assets as a Cloud Service Ultimate vous permet d’exécuter diverses fonctionnalités clés de gestion des actifs numériques, telles que la gestion des ressources et les services de bibliothèque, la gestion de la sécurité et des droits, les connexions Creative et Experience Cloud, l’extensibilité de l’interface utilisateur, l’automatisation pilotée par les API, les intégrations avec les applications d’Adobe et non-Adobe, le déploiement de code personnalisé, etc. Voir [Assets as a Cloud Service Ultimate Overview](/help/assets/assets-ultimate-overview.md) pour obtenir la liste complète.

## Activation d’Assets Ultimate {#enable-assets-ultimate}

Les nouveaux clients as a Cloud Service d’Assets doivent d’abord activer Assets Ultimate en créant un nouveau programme à l’aide de Cloud Manager.

Procédez comme suit :

1. En tant qu’administrateur système, connectez-vous à Cloud Manager. Assurez-vous de sélectionner la bonne organisation lors de la connexion.

   >[!NOTE]
   >
   >Assurez-vous d’être ajouté au profil de produit Cloud Manager approprié pour ajouter un nouveau programme. Pour plus d’informations, voir [Autorisations basées sur les rôles dans Cloud Manager](/help/onboarding/cloud-manager-introduction.md#role-based-permissions).

1. [Créez un nouveau programme](/help/journey-onboarding/create-program.md) et [ajoutez des environnements](/help/journey-onboarding//create-environments.md) à celui-ci.

   Lors de la création du nouveau programme, dans l’onglet **[!UICONTROL Solutions &amp; Add-ons]**, sélectionnez **[!UICONTROL Assets Ultimate]**. Vous pouvez également développer **[!UICONTROL Assets Ultimate]** et sélectionner **[!UICONTROL Content Hub]** pour activer [Content Hub](/help/assets/product-overview.md) pour la distribution de ressources.

   ![AEM Assets Ultimate](assets/aem-assets-ultimate-solutions.png)

1. Cliquez sur **[!UICONTROL Créer]** pour créer le programme. Assets Ultimate est désormais activée pour Experience Manager Assets as a Cloud Service.

L’administrateur système est automatiquement autorisé en tant qu’administrateur AEM sur Assets Ultimate et reçoit un courrier électronique pour accéder à l’Admin Console afin de gérer les profils de produit disponibles.

Votre instance AEM as a Cloud Service sur Admin Console comprend les profils de produit suivants :

* Administrateurs AEM

* Utilisateurs et utilisatrices AEM

* [Utilisateurs collaborateurs d’AEM Assets](#onboard-collaborator-users)

* [Utilisateurs AEM Assets Power](#onboard-power-users)

  ![Profils de produit AEM Assets](assets/aem-assets-product-profiles.png)

Si vous avez activé Content Hub pour Assets as a Cloud Service, une nouvelle instance est créée dans AEM Assets as a Cloud Service on Admin Console avec `delivery` comme suffixe :

![Nouvelle instance pour Content Hub](assets/new-instance-content-hub.png)

>[!NOTE]
>
>Si vous avez configuré Content Hub avant le 14 août 2024, la nouvelle instance est créée avec `contenthub` comme suffixe.

Notez qu’il n’y a pas `author` ou `publish` dans le nom d’instance pour Content Hub.

Cliquez sur le nom de l’instance pour afficher le profil de produit `AEM Assets Limited Users` Content Hub.

![](assets/content-hub-product-profile.png)

You can start adding users or user groups to this product profile to provide them access to Content Hub.

>[!NOTE]
>
>`contenthub``Limited Users``delivery`

## Activation d’Assets Ultimate pour les clients existants {#enable-assets-ultimate-existing-customers}

Les clients Assets as a Cloud Service existants peuvent effectuer une mise à niveau vers Assets Ultimate en exécutant deux étapes simples. Vous pouvez accéder au programme Assets as a Cloud Service dans Cloud Manager et afficher l’état de la mise à niveau sur la carte Programme en fonction de la disponibilité des crédits Assets Ultimate. Si suffisamment de crédits sont disponibles pour la mise à niveau vers Assets Ultimate, vous pouvez voir le statut `Assets license upgrade required`, comme illustré sur l’image suivante :

![Mise à niveau d’AEM Assets vers Assets Ultimate](assets/aem-assets-upgrade-status-ultimate.png)

Si un client existant achète une nouvelle licence pour Assets Ultimate, l’état de mise à niveau s’affiche comme `Assets license upgrade available`.

### Conditions préalables à la mise à niveau {#prerequisites-assets-upgrade}

`2024.10.18175` If you do not meet the minimum requirements, contact your Adobe representative to switch to the required AEM release version.

### Mettre à niveau vers Assets Ultimate {#upgrade-assets-ultimate}

Procédez comme suit :

1. After switching to the minimum requirements for the AEM release version, click the program name. ****

   ![](assets/aem-assets-upgrade-card.png)

1. Cliquez sur **[!UICONTROL Ajouter des profils de produit]**. Cloud Manager affiche des options pour ajouter de nouveaux profils de produit à tous les environnements disponibles dans le programme ou les environnements individuels.

   ![Options de mise à niveau AEM Assets](assets/aem-assets-upgrade-options.png)

1. Cliquez sur **[!UICONTROL Tous les environnements]** pour ajouter les nouveaux profils de produit à tous les environnements du programme ou sur **[!UICONTROL Environnements individuels]** pour ajouter les nouveaux profils de produit aux environnements sélectionnés.

   Cliquez sur **[!UICONTROL Individual Environments]** pour afficher la liste de tous les environnements disponibles dans le programme.

1. Cliquez sur l’icône Plus d’options correspondant à un environnement et sélectionnez **[!UICONTROL Ajouter des profils de produit]** pour ajouter les nouveaux profils de produit à l’environnement sélectionné.

   ![AEM Assets sélectionnez des environnements individuels](assets/aem-assets-individual-environments.png)

   Vous pouvez également ajouter des profils de produit aux environnements sélectionnés en accédant à la section **[!UICONTROL Environnements]**, en cliquant sur l’icône Plus d’options correspondant à un environnement, puis en sélectionnant **[!UICONTROL Ajouter des profils de produit]**.

   L’état de l’environnement s’affiche `Adding Product Profiles` pendant que les nouveaux profils de produit sont ajoutés et affiche par la suite `Running` une fois le processus terminé.

   Vous devez ajouter des profils de produit à tous les environnements disponibles dans le programme, individuellement ou tous ensemble, avant d’exécuter l’étape suivante.

1. Cliquez sur **[!UICONTROL Upgrade]**. ****

   ![](assets/aem-assets-upgrade-button.png)

   The upgrade process is complete and you have successfully upgraded your Assets as a Cloud Service to Assets Ultimate. `Assets Ultimate`

   ![](assets/program-status-post-upgrade.png)

Votre instance AEM as a Cloud Service sur Admin Console comprend désormais les profils de produit suivants :

* AEM Administrators

* Utilisateurs et utilisatrices AEM

* [AEM Assets Collaborator Users](#onboard-collaborator-users)

* [AEM Assets Power Users](#onboard-power-users)

![](assets/aem-assets-product-profiles.png)

**** Développez **[!UICONTROL Assets Ultimate]** et cliquez sur **[!UICONTROL Content Hub]**. Cette étape active Content Hub pour Assets Ultimate. Une nouvelle instance est créée dans AEM Assets as a Cloud Service Admin Console avec `delivery` comme suffixe :

![Nouvelle instance pour Content Hub](assets/new-instance-content-hub.png)

>[!NOTE]
>
>Si vous avez configuré Content Hub avant le 14 août 2024, la nouvelle instance est créée avec `contenthub` comme suffixe.

Notez qu’il n’y a pas `author` ou `publish` dans le nom d’instance pour Content Hub.

Cliquez sur le nom de l’instance pour afficher le profil de produit `AEM Assets Limited Users` Content Hub.

![Profil de produit Content Hub](assets/content-hub-product-profile.png)

Vous pouvez commencer à ajouter des utilisateurs ou des groupes d’utilisateurs à ce profil de produit pour leur permettre d’accéder à Content Hub.

>[!NOTE]
>
>Si vous avez configuré Content Hub avant le 14 août 2024, le profil de produit Content Hub a `contenthub` mentionné après `Limited Users` au lieu de `delivery`.

## Utilisateurs de collaborateur AEM Assets intégrés {#onboard-collaborator-users}

Les utilisateurs collaborateurs d’AEM Assets peuvent travailler avec des ressources d’Experience Manager via des intégrations d’Assets disponibles pour votre entreprise dans d’autres produits d’Adobe et applications non Adobes, créer et modifier des ressources à l’aide d’un Adobe Express intégré et d’un Firefly exploitant des modèles conçus de manière professionnelle, des kits de marque, des ressources Adobe Stock, etc., ainsi qu’accéder et exploiter des ressources approuvées de votre entreprise à l’aide du portail AEM Assets Content Hub.

Pour les utilisateurs de collaborateur intégrés :

1. Accédez aux profils de produit Experience Manager Assets en cliquant sur le nom du produit AEM as a Cloud Service dans la liste des produits sur Admin Console.

1. Cliquez sur l’instance d’auteur de production pour AEM as a Cloud Service :
   ![Profils de produit pour AEM as a Cloud Service](assets/aem-cloud-service-instances.png)

1. Cliquez sur le profil de produit Utilisateurs collaborateurs et cliquez sur **[!UICONTROL Ajouter des utilisateurs]** pour ajouter des utilisateurs ou des groupes d’utilisateurs au profil de produit.
   ![Profil de produit utilisateur](assets/aem-assets-collaborator-user-permissions.png)

1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les modifications.

Vous pouvez également accéder aux services affectés aux utilisateurs Collaborateurs et les afficher, comme illustré dans l’image suivante :

![ Services pour les utilisateurs collaborateurs](assets/aem-assets-collaborator-users.png)

Les services `Adobe Express` et `AEM Assets Collaborator Users` sont activés par défaut.

>[!NOTE]
>
>Vous pouvez activer ou désactiver les services disponibles, en fonction de vos besoins. Toutefois, Adobe recommande d’utiliser les services par défaut activés pour les profils de produit.


## Utilisateurs AEM Assets Power intégrés {#onboard-power-users}

Les utilisateurs AEM Assets Power peuvent accéder à toutes les fonctionnalités d’AEM Assets, notamment la gestion des ressources, les autorisations, les métadonnées et la gouvernance et l’automatisation globales des ressources numériques, travailler avec des ressources d’Experience Manager via des intégrations d’Assets disponibles pour votre entreprise dans d’autres applications d’Adobe et non-Adobe, créer et modifier des ressources à l’aide d’un Adobe Express intégré et d’un Firefly en utilisant des modèles conçus de manière professionnelle, des kits de marque, des ressources d’Adobe Stock, des ressources d’, des ressources d’et des ressources d’AEM Assets portail Content Hub.

Pour embarquer des utilisateurs Power :

1. Access Experience Manager Assets product profiles by clicking the AEM as a Cloud Service product name in the list of products on Admin Console.

1. Click the production author instance for AEM as a Cloud Service:
   ![](assets/aem-cloud-service-instances.png)

1. Cliquez sur le profil de produit Power users et cliquez sur **[!UICONTROL Ajouter des utilisateurs]** pour ajouter des utilisateurs ou des groupes d’utilisateurs au profil de produit.
   ![Profil de produit utilisateur](assets/aem-assets-power-user-permissions.png)

1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les modifications.

Vous pouvez également accéder aux services affectés aux utilisateurs Power et les afficher, comme illustré dans l’image suivante :

![Services pour les utilisateurs d’Power](assets/aem-assets-power-users.png)

Les services `Adobe Express` et `AEM Assets Power Users` sont activés par défaut.

>[!NOTE]
>
>Vous pouvez activer ou désactiver les services disponibles, en fonction de vos besoins. Toutefois, Adobe recommande d’utiliser les services par défaut activés pour les profils de produit.
