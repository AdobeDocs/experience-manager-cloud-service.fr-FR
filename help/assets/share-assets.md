---
title: Partage de ressources, de dossiers et de collections sous forme de lien
description: Cet article décrit le partage de ressources, de dossiers et de collections dans les ressources d’Experience Manager sous forme de lien hypertexte.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 82dd9bd69fe994f74c7be8a571e386f0e902f6a1

---


# Partage et distribution de ressources gérées dans Experience Manager {#share-assets-from-aem}

Adobe Experience Manager (AEM) Assets vous permet de partager des ressources, des dossiers et des collections avec des membres de votre entreprise et des tiers, notamment des partenaires et des fournisseurs. Vous pouvez procéder comme suit pour partager des ressources à partir d’Experience Manager Assets as a Cloud Service :

* Partager des ressources sous la forme d’un lien
* Télécharger des ressources
* Partager via l’application de bureau AEM
* Partager via Adobe Asset Link
* (Fonctionnalité à venir) Partager à l’aide de Brand Portal

## Partage de ressources en tant que lien {#sharelink}

Pour générer une URL pour les ressources que vous souhaitez partager avec des utilisateurs, utilisez la boîte de dialogue Partage de lien. Les utilisateurs disposant de privilèges d’administrateur ou avec des autorisations de lecture à l’emplacement `/var/dam/share` peuvent afficher les liens partagés avec eux. Le partage de ressources au moyen d’un lien est très pratique dans la mesure où il permet à des tiers d’y accéder sans avoir besoin de se connecter au préalable à AEM Assets.

>[!NOTE]
>
>* Vous devez disposer de l’autorisation Modifier l’ACL pour le dossier ou la ressource que vous souhaitez partager sous forme d’un lien.
>* Avant de partager un lien avec des utilisateurs, assurez-vous que le service de messagerie Day CQ est bien configuré. Dans le cas contraire, une erreur se produira.


1. Dans l’interface utilisateur Assets, sélectionnez la ressource à partager sous forme de lien.
1. Dans la barre d’outils, cliquez/appuyez sur **[!UICONTROL Partager le lien]**.

   Le lien de la ressource est créé automatiquement dans le champ **[!UICONTROL Partager le lien]**. Copiez ce lien et partagez-le avec les utilisateurs. Le délai d’expiration par défaut du lien est de 1 jour.

   Vous pouvez également effectuer les étapes 3 à 7 de cette procédure pour ajouter des destinataires de courrier électronique, configurer le délai d’expiration du lien et l’envoyer à partir de la boîte de dialogue.

   >[!NOTE]
   >
   >Si une ressource partagée est déplacée vers un autre emplacement, son lien cesse de fonctionner. Recréez ce lien et partagez-le de nouveau avec les utilisateurs.

1. Dans la console web, ouvrez la configuration de **[!UICONTROL l’externaliseur de liens Day CQ]** et modifiez les propriétés suivantes dans le champ **[!UICONTROL Domaines]** avec les valeurs correspondantes pour :

   * local
   * author
   * publish
   Pour les propriétés local et author, saisissez respectivement l’URL du site local et l’URL de l’instance d’auteur. Les propriétés local et author ont la même valeur si vous exécutez une instance d’auteur AEM unique. Pour la propriété publish, indiquez l’URL de l’instance de publication.

1. Dans la zone Adresse électronique de la boîte de dialogue **[!UICONTROL Partage de liens]**, saisissez l’ID de courrier électronique de l’utilisateur avec lequel vous souhaitez partager le lien. Vous pouvez également partager le lien avec plusieurs utilisateurs.

   Si l’utilisateur fait partie de votre entreprise, sélectionnez son ID de message électronique dans la liste des ID de message électronique suggérés, affichée sous la zone de saisie. Dans le cas d’un utilisateur externe, saisissez l’ID de message électronique complet puis sélectionnez-le dans la liste.

   Pour que les courriers électroniques soient envoyés aux utilisateurs, configurez les détails de serveur SMTP dans le [service de messagerie Day CQ](/help/assets/configure-asset-sharing.md#configmailservice).

   >[!NOTE]
   >
   >Si vous saisissez l’ID de message électronique d’un utilisateur qui ne fait pas partie de votre entreprise, les mots « Utilisateur externe » sont ajoutés à son ID de message électronique.

1. Dans le champ **[!UICONTROL Objet]**, indiquez l’objet de la ressource que vous souhaitez partager.
1. Dans le champ **[!UICONTROL Message]**, vous pouvez saisir un message si vous le souhaitez.
1. Dans le champ **[!UICONTROL Expiration]**, spécifiez la date et l’heure d’expiration du lien à l’aide du sélecteur de date. Par défaut, la date d’expiration est définie sur une semaine à compter de la date à laquelle vous partagez le lien.
1. Pour autoriser les utilisateurs à télécharger l’image originale avec les rendus, sélectionnez **[!UICONTROL Autoriser le téléchargement du fichier d’origine]**.

   >[!NOTE]
   >
   >Par défaut, les utilisateurs peuvent uniquement télécharger les rendus de la ressource que vous partagez sous forme de lien.

1. Cliquez sur **[!UICONTROL Partager]**. Un message confirme le partage du lien avec le ou les utilisateurs par e-mail.
1. Pour afficher la ressource partagée, cliquez/appuyez sur le lien dans le courrier électronique envoyé à l’utilisateur. La ressource partagée s’affiche sur la page **[!UICONTROL Adobe Marketing Cloud]**.

   Pour basculer en mode d’affichage Liste, cliquez/appuyez sur l’icône de mise en page dans la barre d’outils.

1. Pour générer un aperçu de la ressource, cliquez/appuyez sur la ressource partagée. Pour fermer l’aperçu et revenir à la page **[!UICONTROL Marketing Cloud]**, cliquez/appuyez sur **[!UICONTROL Précédent]** dans la barre d’outils. Si vous avez partagé un dossier, cliquez/appuyez sur **[!UICONTROL Dossier parent]** pour revenir au dossier parent.

   >[!NOTE]
   >
   >AEM prend en charge la génération de l’aperçu des ressources des types MIME suivants : JPG, PNG, GIF, BMP, INDD, PDF et PPT. Vous pouvez uniquement télécharger les ressources des autres types MIME.

1. Pour télécharger la ressource partagée, cliquez/appuyez sur **[!UICONTROL Sélectionner]** dans la barre d’outils, cliquez/appuyez sur la ressource, puis sur **[!UICONTROL Télécharger]** dans la barre d’outils.
1. Pour afficher les ressources que vous avez partagées en tant que liens, accédez à l’interface utilisateur d’Assets, puis cliquez/appuyez sur l’icône de navigation globale. Sélectionnez **[!UICONTROL Navigation]** dans la liste pour afficher le panneau Navigation.
1. Dans le panneau Navigation, sélectionnez **[!UICONTROL Liens partagés]** pour afficher la liste des ressources partagées.
1. Pour annuler le partage d’une ressource, sélectionnez-la et appuyez/cliquez sur **[!UICONTROL Annuler le partage]** dans la barre d’outils.

Un message confirmera l’annulation du partage de la ressource. En outre, l’entrée correspondante sera supprimée de la liste.

## Téléchargement et partage de ressources {#download-and-share-assets}

Les utilisateurs peuvent télécharger certaines ressources et les partager en dehors d’Experience Manager. Pour plus d’informations, consultez les pages suivantes (en anglais) [Recherche de ressources](/help/assets/search-assets.md), [Téléchargement de ressources](/help/assets/download-assets-from-aem.md) et [Téléchargement de collections](manage-collections.md#download-a-collection)

## Partage de ressources avec des professionnels de la création {#share-with-creatives}

Les spécialistes marketing et les utilisateurs de services dédiés peuvent facilement partager des ressources approuvées avec des professionnels de la création à l’aide des solutions suivantes :

* **Application de bureau AEM** : cette application fonctionne sous Windows et Mac. Voir [Vue d’ensemble de l’appli de bureau AEM](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/introduction.html). Pour savoir comment un utilisateur autorisé peut facilement accéder aux ressources partagées, voir [Parcourir, rechercher et prévisualiser des ressources](https://docs.adobe.com/content/help/fr-FR/experience-manager-desktop-app/using/using.html#browse-search-preview-assets). Les utilisateurs peuvent créer des ressources et les repartager avec leurs collaborateurs qui sont des utilisateurs d’AEM ; en chargeant de nouvelles images, par exemple. Voir [Chargement de ressources à l’aide de l’application de bureau](https://docs.adobe.com/content/help/fr-FR/experience-manager-desktop-app/using/using.html).

* **Adobe Asset Link** : les professionnels de la création peuvent rechercher et utiliser des ressources directement dans Adobe InDesign, Adobe Illustrator et Adobe Photoshop.

### Bonnes pratiques et résolution des problèmes {#bestpractices}

* Les collections ou les dossiers de ressources dont le nom contient un espace blanc risquent de ne pas être partagés.
* Si les utilisateurs ne peuvent pas télécharger les ressources partagées, contactez votre administrateur AEM pour connaître les [limites de téléchargement](/help/assets/configure-asset-sharing.md#maxdatasize).
* Si vous ne pouvez pas envoyer de courrier électronique avec des liens vers des ressources partagées ou si les autres utilisateurs ne peuvent pas recevoir votre courrier électronique, contactez votre administrateur AEM pour savoir si le [service de messagerie](/help/assets/configure-asset-sharing.md#configmailservice) est configuré ou non.
* Si vous ne pouvez pas partager des fichiers à l’aide de la fonctionnalité de partage de liens, assurez-vous que vous disposez des autorisations appropriées. Voir [Partager des fichiers](#sharelink).

<!--
Add content or link about how to share using BP, DA, AAL, etc.
-->
