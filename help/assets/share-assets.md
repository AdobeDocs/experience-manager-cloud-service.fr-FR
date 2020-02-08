---
title: Partage de fichiers, de dossiers et de collections sous forme de lien
description: Cet article décrit le partage de fichiers, de dossiers et de collections dans les ressources d’Experience Manager sous forme d’hyperlien.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 82dd9bd69fe994f74c7be8a571e386f0e902f6a1

---


# Partage et distribution de fichiers gérés dans Experience Manager {#share-assets-from-aem}

Les ressources d’Adobe Experience Manager (AEM) vous permettent de partager des ressources, des dossiers et des collections avec des membres de votre organisation et des entités externes, notamment des partenaires et des fournisseurs. Vous pouvez utiliser les méthodes suivantes pour partager des ressources à partir des ressources Experience Manager en tant que service Cloud :

* Partager en tant que lien
* Téléchargement de ressources
* Partager via l’application de bureau AEM
* Partager via Adobe Asset Link
* (Fonctionnalité à venir) Partage à l’aide de Brand Portal

## Partage de ressources en tant que lien {#sharelink}

Pour générer une URL pour les ressources que vous souhaitez partager avec des utilisateurs, utilisez la boîte de dialogue Partage de lien. Users with administrator privileges or with read permissions at `/var/dam/share` location are able to view the links shared with them. Le partage de ressources au moyen d’un lien est très pratique dans la mesure où il permet à des tiers d’y accéder sans avoir besoin de se connecter au préalable à AEM Assets.

>[!NOTE]
>
>* Vous devez disposer de l’autorisation Modifier la liste de contrôle d’accès sur le dossier ou la ressource que vous souhaitez partager en tant que lien.
>* Avant de partager un lien avec des utilisateurs, assurez-vous que le service de messagerie Day CQ est bien configuré. Sinon, une erreur se produit.


1. Dans l’interface utilisateur Assets, sélectionnez la ressource à partager sous la forme de lien.
1. Dans la barre d’outils, cliquez/appuyez sur **[!UICONTROL Partager le lien]**.

   An asset link is auto-created in the **[!UICONTROL Share Link]** field. Copiez ce lien et partagez-le avec des utilisateurs. Le délai d’expiration par défaut du lien est de 1 jour.

   Vous pouvez également effectuer les étapes 3 à 7 de cette procédure pour ajouter des destinataires de courrier électronique, configurer le délai d’expiration du lien et l’envoyer à partir de la boîte de dialogue.

   >[!NOTE]
   >
   >Si une ressource partagée est déplacée vers un autre emplacement, son lien cesse de fonctionner. Recréez le lien et partagez-le de nouveau avec les utilisateurs.

1. From the web console, open the **[!UICONTROL Day CQ Link Externalizer]** configuration and modify the following properties in the **[!UICONTROL Domains]** field with the values mentioned against each:

   * local
   * author
   * serveur 
   Pour les propriétés local et author, saisissez respectivement l’URL du site local et l’URL de l’instance d’auteur. Les propriétés local et author ont la même valeur si vous exécutez une instance d’auteur AEM unique. Pour la propriété publish, indiquez l’URL de l’instance de publication.

1. Dans la boîte de dialogue de l’adresse électronique du **[!UICONTROL Partage de lien]**, saisissez l’ID de message électronique de l’utilisateur avec lequel vous souhaitez partager le lien. Vous pouvez également partager le lien avec plusieurs utilisateurs.

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

1. Pour générer un aperçu de la ressource, cliquez/appuyez sur la ressource partagée. To close the preview and return to the **[!UICONTROL Marketing Cloud]** page, click/tap **[!UICONTROL Back]** in the toolbar. Si vous avez partagé un dossier, cliquez/appuyez sur **[!UICONTROL Dossier parent]** pour revenir au dossier parent.

   >[!NOTE]
   >
   >AEM prend en charge la génération de l’aperçu des ressources des types MIME suivants : JPG, PNG, GIF, BMP, INDD, PDF et PPT. Vous pouvez uniquement télécharger les ressources des autres types MIME.

1. To download the shared asset, click/tap **[!UICONTROL Select]** from the toolbar, click/tap the asset, and then click/tap **[!UICONTROL Download]** from the toolbar.
1. Pour afficher les ressources que vous avez partagées en tant que liens, accédez à l’interface utilisateur Assets, puis cliquez/appuyez sur l’icône de navigation globale. Choose **[!UICONTROL Navigation]** from the list to display the Navigation pane.
1. Dans le panneau Navigation, sélectionnez **[!UICONTROL Liens partagés]** pour afficher la liste des ressources partagées.
1. To un-share an asset, select it and tap/click **[!UICONTROL Unshare]** from the toolbar.

Un message confirmera l’annulation du partage de la ressource. En outre, l’entrée correspondante sera supprimée de la liste.

## Téléchargement et partage de fichiers {#download-and-share-assets}

Les utilisateurs peuvent télécharger certains fichiers et les partager en dehors d’Experience Manager. Pour plus d’informations, voir [comment rechercher des ressources](/help/assets/search-assets.md), [comment télécharger des ressources](/help/assets/download-assets-from-aem.md)et [comment télécharger des collections](manage-collections.md#download-a-collection)

## Partage de fichiers avec des professionnels de la création {#share-with-creatives}

Les spécialistes du marketing et les utilisateurs de la ligne d’entreprise peuvent facilement partager des ressources approuvées avec leurs créatifs à l’aide de la fonction

* **Application** de bureau AEM : L’application fonctionne sous Windows et Mac. Reportez-vous à la page Présentation [des applications de](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/introduction.html)bureau. Pour savoir comment un utilisateur de bureau autorisé peut facilement accéder aux ressources partagées, voir [Parcourir, rechercher et prévisualiser les ressources](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html#browse-search-preview-assets). Les utilisateurs de bureau peuvent créer de nouveaux fichiers et les partager avec leurs homologues qui sont des utilisateurs d’AEM, par exemple en téléchargeant de nouvelles images. Voir [Téléchargement de fichiers à l’aide d’une application](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html#upload-and-add-new-assets-to-aem)de bureau.

* **Lien vers** Adobe Asset : Les professionnels de la création peuvent rechercher et utiliser des fichiers directement depuis Adobe InDesign, Adobe Illustrator et Adobe Photoshop.

### Bonnes pratiques et résolution des problèmes {#bestpractices}

* Les dossiers de fichiers ou les collections qui contiennent un espace blanc dans leur nom peuvent ne pas être partagés.
* Si les utilisateurs ne peuvent pas télécharger les ressources partagées, contactez votre administrateur AEM pour connaître les [limites de téléchargement](/help/assets/configure-asset-sharing.md#maxdatasize).
* Si vous ne pouvez pas envoyer de courrier électronique avec des liens vers des ressources partagées ou si les autres utilisateurs ne peuvent pas recevoir votre courrier électronique, contactez votre administrateur AEM pour savoir si le [service de messagerie](/help/assets/configure-asset-sharing.md#configmailservice) est configuré ou non.
* Si vous ne pouvez pas partager des fichiers à l’aide de la fonctionnalité de partage de liens, assurez-vous que vous disposez des autorisations appropriées. Reportez-vous à [Partager des fichiers](#sharelink).

<!--
Add content or link about how to share using BP, DA, AAL, etc.
-->
