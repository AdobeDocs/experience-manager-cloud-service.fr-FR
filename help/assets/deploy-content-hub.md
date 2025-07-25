---
title: Déployer [!DNL Content Hub]
description: Découvrez comment déployer et activer Content Hub et accorder l’accès à des personnes disposant de différents types de privilèges (chargement de ressources, utilisateurs et utilisatrices d’Adobe Express) et comment accorder des privilèges d’administration aux utilisateurs et utilisatrices.
role: Admin
exl-id: 58194858-6e1c-460b-bab3-3496176b2851
source-git-commit: 367406ff325eb71a4c75018c4440eae6535f20dc
workflow-type: tm+mt
source-wordcount: '1586'
ht-degree: 8%

---

# Déployer Content Hub {#deploy-content-hub}

Content Hub est disponible dans le cadre de Experience Manager Assets as a Cloud Service pour démocratiser l’accès au contenu de marque pour les organisations et leurs partenaires commerciaux.

Les ressources marquées comme Approuvées sur Experience Manager Assets as a Cloud Service sont disponibles pour la distribution de ressources sur Content Hub.

Cet article fournit un workflow de bout en bout pour fournir aux utilisateurs un accès à Content Hub, y compris les variations de privilèges en fonction de leurs besoins.

Regardez cette vidéo pour savoir comment activer Content Hub pour Experience Manager Assets :

>[!VIDEO](https://video.tv.adobe.com/v/3469851)

Les variantes des privilèges sur Content Hub incluent :

* [Utilisateurs de Content Hub ](#onboard-content-hub-users) : accédez aux ressources approuvées par la marque sur le portail Content Hub.

* [Administrateurs Content Hub ](#onboard-content-hub-administrator) : accès à l’[interface utilisateur de configuration](/help/assets/configure-content-hub-ui-options.md) sur Content Hub, en plus d’accéder aux ressources approuvées par la marque, de charger des ressources vers Content Hub et d’intégrer Adobe Express pour modifier les images (si vous disposez de droits Adobe Express).

* [Utilisateurs de Content Hub avec des droits d’ajout de ressources ](#onboard-content-hub-users-add-assets) : possibilité de [charger des ressources vers Content Hub](/help/assets/upload-brand-approved-assets.md) en plus d’accéder aux ressources approuvées par la marque sur le portail Content Hub.

* [Les utilisateurs de Content Hub disposant de droits pour remixer les ressources dans de nouvelles variantes ](#onboard-content-hub-users-remix-assets) : [Intégration d’Adobe Express](/help/assets/edit-images-content-hub.md) (si vous disposez de droits Adobe Express) en plus d’accéder aux ressources approuvées par la marque sur le portail Content Hub.

* [Utilisateurs Experience Manager Assets ](#experience-manager-assets-users) : possibilité d’approuver des ressources sur Experience Manager Assets as a Cloud Service pour les rendre disponibles sur Content Hub.

Le tableau suivant résume les types d’utilisateurs Content Hub disponibles, les privilèges dont ils disposent et les profils de produit requis pour obtenir ces privilèges :

| Rôle utilisateur | Utilisateurs de Content Hub | Utilisateurs de Content Hub autorisés à ajouter des ressources | Utilisateurs de Content Hub autorisés à remixer des ressources | Administrateurs Content Hub |
|---------------|----------|----------|-------------------------|---|
| **Fonctionnalités** |
| Accéder aux ressources approuvées par la marque sur le portail Content Hub | ✓ | ✓ | ✓ | ✓ |
| Chargement de ressources à partir du portail Content Hub | − | ✓ | ✓ | ✓ |
| Utilisation de l’intégration Adobe Express pour modifier les images | − | − | ✓ | − |
| Accès à l’interface utilisateur de configuration de Content Hub | − | − | − | ✓ |
| **L’utilisateur ou l’utilisatrice doit se trouver dans ces profils de produit (Admin Console)** |
| AEM > Instance de diffusion > Utilisateurs et utilisatrices limités dans AEM Assets | ✓ | ✓ | ✓ | ✓ |
| AEM > Instance de création de production > Utilisateurs AEM | − | ✓ | ✓ | − |
| AEM > Instance de création de production > Administration AEM | − | − | − | ✓ |
| Adobe Express | − | − | ✓ | − |
| **Informations supplémentaires** | Voir [Utilisateurs de Content Hub](#onboard-content-hub-users) | Voir [Utilisateurs de Content Hub avec des droits d’ajout de ressources](#onboard-content-hub-users-add-assets) | Voir [Utilisateurs de Content Hub avec des droits pour remixer les ressources vers de nouvelles variations](#onboard-content-hub-users-remix-assets) | Voir [Administrateurs Content Hub](#onboard-content-hub-administrator) |

>[!NOTE]
>
>Les utilisateurs de [Experience Manager Assets](#experience-manager-assets-users) peuvent approuver des ressources dans un environnement Experience Manager Assets as a Cloud Service afin de les rendre disponibles sur Content Hub. Ces utilisateurs doivent être ajoutés au profil de produit AEM > Instance de création de production > Utilisateurs AEM à l’aide d’Admin Console.

## Étape 1 : activer Content Hub pour Experience Manager Assets à l’aide de Cloud Manager {#enable-content-hub}


Pour accéder au portail Content Hub, les administrateurs doivent d’abord activer Content Hub pour Experience Manager Assets as a Cloud Service à l’aide de Cloud Manager.

### Autorisations {#permissions-edit-program}

Vous devez disposer du rôle Propriétaire de l’entreprise pour modifier les programmes dans Cloud Manager. Pour plus d’informations, voir [Modifier des programmes](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md).

Pour activer Content Hub pour Experience Manager Assets :

1. Connectez-vous à Cloud Manager. Veillez à sélectionner la bonne organisation lors de la connexion. Le Cloud Manager répertorie tous vos programmes.

1. Accédez au programme Experience Manager Assets as a Cloud Service, cliquez sur l’icône Plus d’options (...) et sélectionnez **[!UICONTROL Modifier le programme]**.

   ![Modifier le programme dans Cloud Manager](assets/edit-program-cloud-manager.png)

1. Dans la boîte de dialogue [!UICONTROL Modifier le programme], sélectionnez l’onglet **[!UICONTROL Solutions et modules complémentaires]**.

1. Développez **[!UICONTROL Assets]** puis sélectionnez **[!UICONTROL Content Hub]**.
   ![Sélectionnez Content Hub dans Cloud Manager](assets/edit-program-cloud-manager-content-hub.png)

   >[!NOTE]
   >
   >Si l’option **[!UICONTROL Mettre à jour]** n’est pas activée après avoir sélectionné Content Hub, vérifiez que vous avez spécifié les paramètres d’activation du programme.

1. Cliquez sur **[!UICONTROL Mettre à jour]**.

Content Hub est désormais activé pour Experience Manager Assets as a Cloud Service. Après l’activation de Content Hub dans un environnement de production, vous ne pouvez pas le désactiver en libre-service.

>[!NOTE]
>
>Vous pouvez accéder à Content Hub et l’utiliser avec jusqu’à 250 utilisateurs Content Hub. Pour toute question supplémentaire, contactez votre représentant ou représentante Adobe.


Si vous découvrez Experience Manager Assets, cliquez sur **[!UICONTROL Ajouter un programme]** puis fournissez les détails du programme (Nom du programme, Configuration pour la production) et cliquez sur **[!UICONTROL Continuer]**. Vous pouvez ensuite sélectionner **[!UICONTROL Assets]** et **[!UICONTROL Content Hub]** dans l’onglet **[!UICONTROL Solutions et modules complémentaires]**.

### Instance de Content Hub et profil de produit sur Admin Console{#content-hub-instance-product-profile}

Après [activation de Content Hub pour Assets as a Cloud Service à l’aide de Cloud Manager](#enable-content-hub), une nouvelle instance est créée dans AEM Assets as a Cloud Service sur Admin Console avec `delivery` comme suffixe :

![Nouvelle instance pour Content Hub ](assets/new-instance-content-hub.png)

>[!NOTE]
>
>Si vous avez configuré Content Hub avant le 14 août 2024, la nouvelle instance est créée avec `contenthub` comme suffixe.

Notez qu’il n’y a aucun `author` ni `publish` dans le nom de l’instance pour Content Hub.

Cliquez sur le nom de l’instance pour afficher le profil de produit Content Hub.

![Profil de produit Content Hub](assets/content-hub-product-profile.png)

>[!NOTE]
>
>Si vous avez configuré Content Hub avant le 14 août 2024, le profil de produit Content Hub a `contenthub` mentionné après `Limited Users` au lieu de `delivery`.

## Étape 2 : intégration d’un administrateur Content Hub {#onboard-content-hub-administrator}

Les administrateurs et administratrices de Content Hub peuvent accéder à l’[interface utilisateur de configuration](/help/assets/configure-content-hub-ui-options.md) sur Content Hub, en plus d’accéder aux ressources approuvées par la marque, de charger des ressources vers Content Hub et d’intégrer Adobe Express pour modifier les images (si vous disposez de droits Adobe Express).

Pour intégrer l’administrateur Content Hub :

1. [Accédez au profil de produit utilisateur Content Hub et cliquez dessus](#content-hub-instance-product-profile).

1. Cliquez sur **[!UICONTROL Ajouter des utilisateurs]** pour ajouter des utilisateurs ou des groupes d’utilisateurs au profil de produit.

1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les modifications.

1. Après avoir ajouté l’utilisateur au profil de produit Content Hub, accédez aux profils de produit Experience Manager Assets en cliquant sur le nom du produit AEM as a Cloud Service dans la liste des produits sur Admin Console.

1. Cliquez sur l’instance d’auteur d’exploitation pour AEM as a Cloud Service :
   ![Profils de produit pour AEM as a Cloud Service](assets/aem-cloud-service-instances.png)

   Admin Console affiche deux profils de produit pour AEM as a Cloud Service : Administrateurs et Utilisateurs.
1. Cliquez sur le profil de produit Administrateurs et cliquez sur **[!UICONTROL Ajouter des utilisateurs]** pour ajouter l’utilisateur au profil de produit.
   ![Profil de produit administrateur](assets/aem-cs-admin-product-profile.png)

1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les modifications.

## Étape 3 : intégration des utilisateurs Content Hub {#onboard-content-hub-users}

Les utilisateurs de Content Hub peuvent accéder aux ressources disponibles sur le portail, mais ne peuvent pas ajouter de nouvelles ressources ni modifier des ressources existantes.

Pour intégrer des utilisateurs Content Hub :

1. [Accédez au profil de produit utilisateur Content Hub et cliquez dessus](#content-hub-instance-product-profile).

1. Cliquez sur **[!UICONTROL Ajouter des utilisateurs]** pour ajouter des utilisateurs ou des groupes d’utilisateurs au profil de produit.

1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les modifications.

Ces utilisateurs peuvent désormais accéder aux ressources disponibles sur le portail Content Hub.

>[!NOTE]
>
>Vous pouvez utiliser toutes les fonctionnalités d’entreprise avancées, telles que la synchronisation avec des fournisseurs d’identité externes.

### Comment accéder à Content Hub ? {#access-content-hub}

Pour accéder à Content Hub, procédez comme suit :

* Accédez à Content Hub à l’aide du lien suivant :

  `https://experience.adobe.com/#/assets/contenthub`

* Connectez-vous à `experience.adobe com` et cliquez sur **[!UICONTROL Experience Manager Assets Content Hub]** disponible dans la section **[!UICONTROL Accès rapide]** :
  ![Accès au hub de contenus](assets/access-content-hub.png)

* Connectez-vous à `experience.adobe com` et cliquez sur **[!UICONTROL Experience Manager Assets Content Hub]** disponible dans le sélecteur de produits :
  ![Méthode 3 d’accès à Content Hub](assets/access-content-hub-alternate.png)

### Désactiver les notifications par e-mail aux utilisateurs {#disable-email-notifications}

Si les administrateurs doivent désactiver les notifications par e-mail envoyées aux utilisateurs lorsqu’ils sont ajoutés au profil de produit Content Hub :

Cliquez sur l’icône de recherche adjacente au nom du profil de produit et désactivez le bouton (bascule) **[!UICONTROL Notifier les utilisateurs par e-mail]**.

![Désactiver les notifications par e-mail](assets/disable-email-notifications.png)


## Étape 4 : intégration des utilisateurs Content Hub avec des droits d’ajout de ressources (facultatif) {#onboard-content-hub-users-add-assets}

Les utilisateurs de Content Hub autorisés à ajouter des ressources peuvent [charger de nouvelles ressources approuvées par la marque dans Content Hub](/help/assets/upload-brand-approved-assets.md).

Pour intégrer des utilisateurs Content Hub avec des droits d’ajout d’utilisateurs :

1. [Après avoir ajouté l’utilisateur au profil de produit Content Hub](#onboard-content-hub-users) accédez aux profils de produit Experience Manager Assets en cliquant sur le nom du produit AEM as a Cloud Service dans la liste des produits sur Admin Console.

1. Cliquez sur l’instance d’auteur d’exploitation pour AEM as a Cloud Service :
   ![Profils de produit pour AEM as a Cloud Service](assets/aem-cloud-service-instances.png)

   Admin Console affiche deux profils de produit pour AEM as a Cloud Service : Administrateurs et Utilisateurs.
1. Cliquez sur le profil de produit Utilisateurs et cliquez sur **[!UICONTROL Ajouter des utilisateurs]** pour ajouter l’utilisateur au profil de produit.
   ![Profil de produit utilisateur](assets/aem-cs-user-product-profile.png)

1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les modifications.

## Étape 4 : intégration des utilisateurs de Content Hub avec des droits pour remixer les ressources vers de nouvelles variations (facultatif) {#onboard-content-hub-users-remix-assets}

Les utilisateurs de Content Hub autorisés à remixer des ressources dans de nouvelles variantes peuvent [modifier des ressources existantes à l’aide d’Adobe Express et enregistrer la ressource dans le référentiel](/help/assets/edit-images-content-hub.md). La modification de ressources à l’aide d’Adobe Express n’est disponible que si l’utilisateur dispose de droits Adobe Express.

Pour intégrer des utilisateurs Content Hub avec les droits nécessaires pour remixer les ressources à de nouvelles variations :

1. [Après avoir ajouté l’utilisateur au profil de produit Content Hub](#onboard-content-hub-users) accédez aux profils de produit Experience Manager Assets en cliquant sur le nom du produit AEM as a Cloud Service dans la liste des produits sur Admin Console.

1. Cliquez sur l’instance d’auteur d’exploitation pour AEM as a Cloud Service :
   ![Profils de produit pour AEM as a Cloud Service](assets/aem-cloud-service-instances.png)

   Admin Console affiche deux profils de produit pour AEM as a Cloud Service : Administrateurs et Utilisateurs.
1. Cliquez sur le profil de produit Utilisateurs et cliquez sur **[!UICONTROL Ajouter des utilisateurs]** pour ajouter l’utilisateur au profil de produit.
   ![Profil de produit utilisateur](assets/aem-cs-user-product-profile.png)

1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les modifications.

## Utilisateurs de Experience Manager Assets {#experience-manager-assets-users}

Les utilisateurs de Experience Manager Assets peuvent approuver des ressources sur AEM as a Cloud Service afin qu’elles soient disponibles sur Content Hub.

Pour configurer les utilisateurs de Experience Manager Assets :

1. Accédez aux profils de produit Experience Manager Assets en cliquant sur le nom du produit AEM as a Cloud Service dans la liste des produits sur Admin Console.

1. Cliquez sur l’instance d’auteur d’exploitation pour AEM as a Cloud Service :
   ![Profils de produit pour AEM as a Cloud Service](assets/aem-cloud-service-instances.png)

   Admin Console affiche deux profils de produit pour AEM as a Cloud Service : Administrateurs et Utilisateurs.
1. Cliquez sur le profil de produit Utilisateurs et cliquez sur **[!UICONTROL Ajouter des utilisateurs]** pour ajouter l’utilisateur au profil de produit.
   ![Profil de produit utilisateur](assets/aem-cs-user-product-profile.png)

1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les modifications.

   >[!NOTE]
   >
   > Vous n&#39;avez pas besoin d&#39;être ajouté au profil de produit [Content Hub](#onboard-content-hub-users) pour les utilisateurs de Experience Manager Assets.
