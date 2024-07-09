---
title: Déployer [!DNL Content Hub]
description: Découvrez comment déployer et activer Content Hub et accorder l’accès à des utilisateurs disposant de différents types de privilèges (chargement de ressources, utilisateurs d’Adobe Express) et comment accorder des privilèges d’administrateur aux utilisateurs.
role: Admin
source-git-commit: 7224cca950e61bea298f246245bdb221fd8fa22e
workflow-type: tm+mt
source-wordcount: '1316'
ht-degree: 3%

---


# Déployer le hub de contenus {#deploy-content-hub}

![Déploiement de Content Hub](assets/deploy-content-hub.png)

Content Hub est disponible dans le cadre de Experience Manager Assets as a Cloud Service pour démocratiser l’accès au contenu de marque pour les organisations et leurs partenaires commerciaux.

Les ressources marquées comme approuvées as a Cloud Service Experience Manager Assets sont disponibles pour la distribution des ressources sur Content Hub.

Cet article fournit un processus de bout en bout pour fournir aux utilisateurs un accès Content Hub, y compris les variantes d’autorisations en fonction de leurs besoins.

Les variations de privilèges sur Content Hub incluent :

* [Utilisateurs de Content Hub](#onboard-content-hub-users): accédez aux ressources approuvées par la marque sur le portail Content Hub.

* [Administrateurs de Content Hub](#onboard-content-hub-administrator): accès au [Interface utilisateur de configuration](/help/assets/configure-content-hub-ui-options.md) sur Content Hub, en plus d’accéder aux ressources approuvées par la marque, téléchargez des ressources vers Content Hub, l’intégration Adobe Express pour modifier les images (si vous disposez des droits d’Adobe Express).

* [Utilisateurs de Content Hub disposant des droits d’ajout de ressources](#onboard-content-hub-users-add-assets): capacité à [chargement de ressources vers Content Hub](/help/assets/upload-brand-approved-assets.md) en plus d’accéder aux ressources approuvées par la marque sur le portail Content Hub.

* [Utilisateurs de Content Hub disposant des droits de remix de ressources vers de nouvelles variations](#onboard-content-hub-users-remix-assets): [Intégration d’Adobe Express](/help/assets/edit-images-content-hub.md) (si vous disposez des droits d’Adobe Express) en plus d’accéder aux ressources approuvées par la marque sur le portail Content Hub.

* [Utilisateurs de Experience Manager Assets](#experience-manager-assets-users): possibilité d’approuver les ressources as a Cloud Service Experience Manager Assets pour les rendre disponibles sur Content Hub.

## Étape 1 : Activation de Content Hub pour Experience Manager Assets à l’aide de Cloud Manager {#enable-content-hub}

Pour accéder au portail Content Hub, les administrateurs doivent d’abord activer Content Hub pour Experience Manager Assets as a Cloud Service à l’aide de Cloud Manager. Procédez comme suit :

1. Connectez-vous à Cloud Manager. Assurez-vous de sélectionner la bonne organisation lors de la connexion. Le Cloud Manager répertorie tous vos programmes.

1. Accédez au programme Experience Manager Assets as a Cloud Service, cliquez sur l’icône Autres options (...) et sélectionnez **[!UICONTROL Modifier le programme]**.

   ![Modifier le programme dans Cloud Manager](assets/edit-program-cloud-manager.png)

1. Sur le [!UICONTROL Modifier le programme] , sélectionnez **[!UICONTROL Solutions et modules complémentaires]** .

1. Développer **[!UICONTROL Assets]** et sélectionnez **[!UICONTROL Content Hub]**.
   ![Sélection de Content Hub dans Cloud Manager](assets/edit-program-cloud-manager-content-hub.png)

   >[!NOTE]
   >
   >If **[!UICONTROL Mettre à jour]** n’est pas activé pour vous après avoir sélectionné Content Hub, assurez-vous que vous avez spécifié les paramètres d’activation pour le programme.

1. Cliquez sur **[!UICONTROL Mettre à jour]**.

Content Hub est désormais activé pour Experience Manager Assets as a Cloud Service.

>[!NOTE]
>
>Vous pouvez accéder à Content Hub et l’utiliser avec jusqu’à 250 utilisateurs de Content Hub. Contactez votre représentant Adobe si vous avez d’autres questions.


Si vous découvrez Experience Manager Assets, cliquez sur **[!UICONTROL Ajout d’un programme]** puis fournissez les détails du programme (nom du programme, configurer pour la production) et cliquez sur **[!UICONTROL Continuer]**. Vous pouvez ensuite sélectionner **[!UICONTROL Assets]** et **[!UICONTROL Content Hub]** dans le **[!UICONTROL Solutions et modules complémentaires]** .

### Instance Content Hub et profil de produit sur Admin Console{#content-hub-instance-product-profile}

Après [Activation de Content Hub pour Assets as a Cloud Service à l’aide de Cloud Manager](#enable-content-hub), une nouvelle instance est créée dans AEM Assets as a Cloud Service Admin Console avec `contenthub` comme suffixe :

![Nouvelle instance pour Content Hub](assets/new-instance-content-hub.png)

Notez qu’il n’existe pas de `author` ou `publish` dans le nom de l’instance pour Content Hub.

Cliquez sur le nom de l’instance pour afficher le profil de produit Content Hub.

![Profil de produits Content Hub](assets/content-hub-product-profile.png)

## Étape 2 : administrateur Content Hub intégré {#onboard-content-hub-administrator}

Les administrateurs Content Hub peuvent accéder aux [Interface utilisateur de configuration](/help/assets/configure-content-hub-ui-options.md) sur Content Hub, en plus d’accéder aux ressources approuvées par la marque, téléchargez des ressources vers Content Hub, l’intégration Adobe Express pour modifier les images (si vous disposez des droits d’Adobe Express).

Pour intégrer l’administrateur Content Hub :

1. [Accédez au profil de produit utilisateur Content Hub et cliquez dessus.](#content-hub-instance-product-profile).

1. Cliquez sur **[!UICONTROL Ajout d’utilisateurs]** pour ajouter des utilisateurs ou des groupes d’utilisateurs au profil de produit.

1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les modifications.

1. Après avoir ajouté l’utilisateur au profil de produit Content Hub, accédez aux profils de produit Experience Manager Assets en cliquant sur le nom du produit AEM as a Cloud Service dans la liste des produits sur Admin Console.

1. Cliquez sur l’instance d’auteur de production pour AEM as a Cloud Service :
   ![Profils de produit pour AEM as a Cloud Service](assets/aem-cloud-service-instances.png)

   Admin Console affiche deux profils de produit pour AEM as a Cloud Service : Administrateurs et Utilisateurs.
1. Cliquez sur le profil de produit Administrateurs , puis sur **[!UICONTROL Ajout d’utilisateurs]** pour ajouter l’utilisateur au profil de produit.
   ![Profil produit administrateur](assets/aem-cs-admin-product-profile.png)

1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les modifications.

## Étape 3 : utilisateurs Content Hub intégrés {#onboard-content-hub-users}

Les utilisateurs de Content Hub peuvent accéder aux ressources disponibles sur le portail, mais ne peuvent pas ajouter de nouvelles ressources ni modifier des ressources existantes.

Pour intégrer des utilisateurs Content Hub :

1. [Accédez au profil de produit utilisateur Content Hub et cliquez dessus.](#content-hub-instance-product-profile).

1. Cliquez sur **[!UICONTROL Ajout d’utilisateurs]** pour ajouter des utilisateurs ou des groupes d’utilisateurs au profil de produit.

1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les modifications.

Ces utilisateurs peuvent désormais accéder aux ressources disponibles sur le portail Content Hub.

>[!NOTE]
>
>Vous pouvez utiliser toutes les fonctionnalités avancées de l’entreprise, telles que la synchronisation avec des fournisseurs d’identité externes.

### Comment accéder à Content Hub ? {#access-content-hub}

Content Hub est accessible de différentes manières :

* Accédez à Content Hub à l’aide du lien suivant :

  `https://experience.adobe.com/#/assets/contenthub`

* Connectez-vous à `experience.adobe com` et cliquez sur **[!UICONTROL Experience Manager Assets Content Hub]** disponible dans le **[!UICONTROL Accès rapide]** section :
  ![Accès Content Hub](assets/access-content-hub.png)

* Connectez-vous à `experience.adobe com` et cliquez sur **[!UICONTROL Experience Manager Assets Content Hub]** disponible dans le sélecteur de produits :
  ![Méthode d’accès Content Hub 3](assets/access-content-hub-alternate.png)

### Désactivation des notifications par e-mail aux utilisateurs {#disable-email-notifications}

Si les administrateurs doivent désactiver les notifications électroniques envoyées aux utilisateurs lorsqu’ils sont ajoutés au profil de produit Content Hub :

Cliquez sur l’icône de recherche en regard du nom du profil de produit et désactivez la variable **[!UICONTROL Notifier les utilisateurs par courrier électronique]** bascule.

![Désactivation des notifications par e-mail](assets/disable-email-notifications.png)


## Étape 4 : Intégration des utilisateurs de Content Hub avec les droits d’ajout de ressources (facultatif) {#onboard-content-hub-users-add-assets}

Les utilisateurs Content Hub disposant de droits pour ajouter des ressources peuvent [charger de nouvelles ressources approuvées par la marque dans Content Hub](/help/assets/upload-brand-approved-assets.md).

Pour intégrer des utilisateurs Content Hub disposant de droits d’ajout d’utilisateurs :

1. [Après l’ajout de l’utilisateur au profil de produit Content Hub](#onboard-content-hub-users), accédez aux profils de produit Experience Manager Assets en cliquant sur le nom du produit AEM as a Cloud Service dans la liste des produits sur Admin Console.

1. Cliquez sur l’instance d’auteur de production pour AEM as a Cloud Service :
   ![Profils de produit pour AEM as a Cloud Service](assets/aem-cloud-service-instances.png)

   Admin Console affiche deux profils de produit pour AEM as a Cloud Service : Administrateurs et Utilisateurs.
1. Cliquez sur le profil de produit Utilisateurs , puis sur **[!UICONTROL Ajout d’utilisateurs]** pour ajouter l’utilisateur au profil de produit.
   ![Profil de produit utilisateur](assets/aem-cs-user-product-profile.png)

1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les modifications.

## Étape 4 : Intégration des utilisateurs de Content Hub avec les droits de remix de ressources vers de nouvelles variations (facultatif) {#onboard-content-hub-users-remix-assets}

Les utilisateurs de Content Hub disposant des droits de remix de ressources vers de nouvelles variations peuvent [modifier des ressources existantes à l’aide d’Adobe Express et enregistrer la ressource dans le référentiel ;](/help/assets/edit-images-content-hub.md). La modification de ressources à l’aide d’Adobe Express n’est disponible que si l’utilisateur dispose de droits d’Adobe Express.

Pour intégrer des utilisateurs Content Hub autorisés à remixer des ressources vers de nouvelles variations :

1. [Après l’ajout de l’utilisateur au profil de produit Content Hub](#onboard-content-hub-users), accédez aux profils de produit Experience Manager Assets en cliquant sur le nom du produit AEM as a Cloud Service dans la liste des produits sur Admin Console.

1. Cliquez sur l’instance d’auteur de production pour AEM as a Cloud Service :
   ![Profils de produit pour AEM as a Cloud Service](assets/aem-cloud-service-instances.png)

   Admin Console affiche deux profils de produit pour AEM as a Cloud Service : Administrateurs et Utilisateurs.
1. Cliquez sur le profil de produit Utilisateurs , puis sur **[!UICONTROL Ajout d’utilisateurs]** pour ajouter l’utilisateur au profil de produit.
   ![Profil de produit utilisateur](assets/aem-cs-user-product-profile.png)

1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les modifications.

## Utilisateurs de Experience Manager Assets {#experience-manager-assets-users}

Les utilisateurs de Experience Manager Assets peuvent approuver les ressources dans AEM as a Cloud Service afin qu’elles soient disponibles dans Content Hub.

Pour configurer les utilisateurs de Experience Manager Assets :

1. Accédez aux profils de produit Experience Manager Assets en cliquant sur le nom du produit AEM as a Cloud Service dans la liste des produits sur Admin Console.

1. Cliquez sur l’instance d’auteur de production pour AEM as a Cloud Service :
   ![Profils de produit pour AEM as a Cloud Service](assets/aem-cloud-service-instances.png)

   Admin Console affiche deux profils de produit pour AEM as a Cloud Service : Administrateurs et Utilisateurs.
1. Cliquez sur le profil de produit Utilisateurs , puis sur **[!UICONTROL Ajout d’utilisateurs]** pour ajouter l’utilisateur au profil de produit.
   ![Profil de produit utilisateur](assets/aem-cs-user-product-profile.png)

1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les modifications.

   >[!NOTE]
   >
   > Vous n’avez pas besoin d’être ajouté à la variable [Profil de produits Content Hub](#onboard-content-hub-users) pour les utilisateurs de Experience Manager Assets.



