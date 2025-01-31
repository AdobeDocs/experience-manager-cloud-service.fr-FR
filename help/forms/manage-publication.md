---
title: Comment publier ou dépublier des formulaires sur des instances d’aperçu ou de publication ?
description: Découvrez comment publier ou dépublier des formulaires dans l’environnement de création AEM pour prévisualiser ou publier des instances. Que vous testiez vos formulaires dans un environnement d’évaluation ou que vous les déployiez en direct pour les utilisateurs finaux, AEM fournit des outils rationalisés pour gérer ce processus efficacement.
Keywords: Manage publication, Forms Manage publication, AF Manage publication, Adaptive Forms Manage publication, Cloud Manage publication
feature: Adaptive Forms
feature-set: Experience Manager Assets,Experience Manager Sites,Experience Manager, Experience Manager Forms, Experience Manager Cloud Manager
role: User, Developer
level: Intermediate
source-git-commit: d3c089dcca80255f53c0888d46ee1b4b6246741e
workflow-type: tm+mt
source-wordcount: '970'
ht-degree: 2%

---


# &#x200B;Gérer la publication dans Experience Manager Forms

En tant qu’administrateur Adobe Experience Manager Forms, vous pouvez publier des formulaires de votre instance de création dans Experience Manager Forms. Vous pouvez planifier la publication d’un formulaire ou d’un dossier à une date ou une heure ultérieure. Une fois la publication effectuée, les utilisateurs peuvent accéder aux formulaires et les remplir.

Dans l’interface de Experience Manager Forms, vous pouvez publier un formulaire à l’aide de l’action :
* [Option Publish](#publish-forms-using-the-publish-option)
* [Option Gérer la publication](#publish-forms-using-the-manage-publication-option)

Si vous apportez des modifications ultérieures aux formulaires ou dossiers d’origine dans Experience Manager Forms, les modifications ne sont pas répercutées dans l’instance **Publish** tant que vous n’avez pas republié à partir de Experience Manager Forms. Cela garantit que les modifications en cours ne sont pas disponibles dans l’instance **Publish**. Seules les modifications publiées par un administrateur sont disponibles dans l’instance **Publish**.

## Publish forms avec l’option Publish

L&#39;option **Publish** permet de publier immédiatement un formulaire. Pour publier un formulaire Experience Manager à l’aide du bouton **Publish** de la barre d’outils. Pour publier des formulaires à l’aide de l’option Publish, procédez comme suit :

1. Dans la console Experience Manager Forms, accédez au dossier parent et sélectionnez un formulaire que vous souhaitez publier.
1. Cliquez sur l’option **Publish** dans la barre d’outils, consultez toutes les ressources de référence qui seraient publiées avec le formulaire.
1. Cliquez sur **[!UICONTROL Publier]**.

   ![Publish et dépublier le formulaire](/help/edge/docs/forms/assets/publish-form-option.png)

   Une fois le formulaire et ses ressources associées publiés, une boîte de dialogue **Succès** s’affiche. Cliquez sur **Fermer** pour fermer la boîte de dialogue.

   ![Boîte de dialogue Succès](/help/forms/assets/publish-success.png)

### Dépublication du formulaire

Une fois le formulaire publié à l’aide de l’option **Publish** et des ressources associées, vous pouvez même le dépublier à l’aide du bouton **[!UICONTROL Dépublier]** de la barre d’outils. Pour dépublier le formulaire :

1. Pour dépublier le formulaire et les ressources associées, sélectionnez le formulaire et cliquez sur **[!UICONTROL Dépublier]** dans la barre d’outils

   Lorsque vous cliquez sur le bouton **[!UICONTROL Dépublier]**, la boîte de dialogue **Dépublier l’élément** s’affiche.
1. Cliquez sur **[!UICONTROL Dépublier]** pour lancer le processus de dépublication

   ![Boîte de dialogue Dépublier](/help/forms/assets/unpublish-asset.png)

   Une fois la dépublication du formulaire et des ressources associées effectuée, une boîte de dialogue **Succès** s’affiche. Cliquez sur **Fermer** pour fermer la boîte de dialogue.

   ![dépublication réussie](/help/forms/assets/unpublishing-start.png)

## Publish forms à l’aide de l’option Gérer la publication

L’option Gérer la publication permet de publier ou de dépublier du contenu vers et depuis la destination sélectionnée, d’ajouter du contenu à la liste de publication à partir du dossier Formulaires et documents, de sélectionner les références à publier et de planifier une publication à une date ou une heure ultérieure.  Pour publier des formulaires à l’aide de l’option Gérer la publication , procédez comme suit :

1. Dans la console Experience Manager Forms, accédez au dossier parent et sélectionnez un formulaire que vous souhaitez publier.
1. Cliquez sur l’option **[!UICONTROL Gérer la publication]** dans la barre d’outils.

   ![Option Gérer la publication](/help/forms/assets/manage-publication-option.png)

   L’interface **Gérer la publication** s’affiche :

   ![Gérer la publication.](/help/forms/assets/manage-publication.png)

   Les options suivantes sont disponibles dans l’interface **Gérer la publication** :

   * **Actions**

      * **Publish** : Publish forms vers la destination sélectionnée
      * **Dépublier** : dépublication de formulaires de la destination

   * **Destination**

      * **Publish** : instance Publish forms vers Experience Manager Forms (AEM) Publish.
      * **Aperçu** : instance d’aperçu de Publish forms vers Experience Manager Forms (AEM).

   * **Planification**

      * **Maintenant** : Publish forms immédiatement
      * **Ultérieurement** : formulaires Publish basés sur la **Date d’activation** ou l’heure

1. Cliquez sur **Suivant** pour continuer.
1. Dans l’onglet **Portée**, utilisez l’option [Ajouter du contenu](#add-content) pour ajouter plus de contenu à publier. Par exemple, vous pouvez ajouter d’autres fichiers Forms ou Document d’enregistrement.
   ![onglet portée](/help/forms/assets/scope-tab.png)
1. Cliquez sur **[!UICONTROL Publish]** pour publier les formulaires et les ressources associées et un message de réussite s’affiche.
   ![publication du message réussie](/help/forms/assets/publish-successful.png)

### Ajouter du contenu

La publication vers Experience Manager Forms vous permet d’ajouter davantage de contenu (formulaires et dossiers) à la liste de publication. Vous pouvez ajouter d’autres formulaires ou dossiers à la liste à partir du dossier `formsanddocuments` . Cependant, vous ne pouvez pas ajouter de formulaires provenant de plusieurs dossiers à la fois. Pour ajouter d’autres formulaires à publier :

1. Cliquez sur le bouton **Ajouter du contenu** pour ajouter plus de contenu.

   ![ Ajouter du contenu ](/help/forms/assets/add-content.png)

1. Sélectionnez le formulaire dans l’écran **Sélectionner le chemin d’accès**. Vous pouvez ajouter plusieurs formulaires à partir d’un dossier ou ajouter plusieurs dossiers à la fois. Cependant, vous ne pouvez pas ajouter de formulaires provenant de plusieurs dossiers à la fois.

   ![ Ajouter du contenu ](/help/forms/assets/add-assets.png)

1. Pour configurer les références afin de publier ou non pour un formulaire, sélectionnez le formulaire et cliquez sur **[!UICONTROL Références publiées]**.

   ![références publiées](/help/forms/assets/published-references.png)

1. Dans la boîte de dialogue **Références publiées**, désélectionnez les ressources que vous prévoyez de ne pas publier et cliquez sur **[!UICONTROL Terminé]**.
   ![ boîte de dialogue références publiées ](/help/forms/assets/published-references-dialog.png)

<!--
### Include Folder Settings
By default, publishing a folder to Experience Manager Forms publishes all the assets, subfolders, and their references. To filter the folder for publishing:

1. Click **[Include Folder Settings]** to filter the folder.

    ![Include folder](/help/forms/assets/include-folder.png)

    The **[UICONTROL Include Folder Settings]** dialog appears. 
    
    ![Include folder dialog](/help/forms/assets/include-folder-dialog.png)
    
    The **[UICONTROL Include Folder Settings]** includes following options:

    * **[!UICONTROL Include folder contents]** checkbox. 
        * If selected, all forms and assets in the chosen folder, its subfolders (including all forms and assets within them), and references are published.
        * If not selected, only the forms and assets in the selected folder are published, while subfolder forms and assets are not.

    * **[!UICONTROL Include only immediate folder contents]** checkbox
        Selecting the **[!UICONTROL Include folder contents]** checkbox enables the **[!UICONTROL Include only immediate folder contents]** checkbox for selection.

        * If you select both options, all the forms and assets of the selected folder, subfolders (empty), and references are published. The forms and assets of the subfolders are not published.
        * -->


### Publish ou dépublication ultérieure d’un formulaire

En plus de vous permettre de publier ou de dépublier des formulaires à une date et une heure ultérieures, l’option publier ou dépublier ultérieurement permet également de configurer un workflow. Les formulaires sont publiés ou dépubliés une fois le workflow terminé. Pour planifier la publication ou la dépublication d’un formulaire :

1. Dans la console Experience Manager Forms, accédez au dossier parent et sélectionnez le formulaire dont vous souhaitez planifier la publication.
1. Cliquez sur l’option **[!UICONTROL Gérer la publication]** dans la barre d’outils.

   ![Gérer la publication.](/help/forms/assets/manage-publication.png)

1. Cliquez sur **Publish** ou **Dépublier** dans **[!UICONTROL Action]**, puis sélectionnez la **[!UICONTROL Destination]** dans laquelle vous souhaitez publier ou dépublier le contenu.
   * **Prévisualisation** : utilisez l’option **Prévisualisation** pour publier ou dépublier dans un environnement de prévisualisation Experience Manager Forms. Les environnements de prévisualisation Experience Manager Forms sont utilisés pour tester les formulaires en cours de développement.
   * **Publish** : utilisez l’option Experience Manager Forms Publish pour envoyer le formulaire à l’environnement de publication Experience Manager Forms une fois que le formulaire est prêt à être utilisé dans un environnement de production.

1. Sélectionnez **[!UICONTROL Plus tard]** dans Planification.

   ![Gérer la publication ultérieurement](/help/forms/assets/manage-publication-later.png)

1. Sélectionnez une **[!UICONTROL Date d’activation]** et spécifiez la date et l’heure.
1. Cliquez sur **[!UICONTROL Suivant]**.
1. Dans l’onglet **Portée**, **[!UICONTROL Ajouter du contenu]** (si nécessaire).
   ![Gérer la publication ajouter du contenu ultérieurement](/help/forms/assets/publish-later-add-content.png)
1. Cliquez sur **[!UICONTROL Suivant]**.
1. (Facultatif) Dans l’onglet **Workflows**, spécifiez un **[!UICONTROL titre du workflow]**.
1. Cliquez sur **[!UICONTROL Publish ultérieurement]**.

   ![Gestion du processus de publication](/help/forms/assets/manage-publication-workflows.png)

## Définition du statut de publication

Il existe plusieurs façons de déterminer le statut de publication :

* Connectez-vous à l’instance de destination pour vérifier les formulaires publiés et d’autres ressources (selon la date ou l’heure planifiée).

* Utilisez la vue chronologique pour déterminer le statut de la publication.

* Utilisez le menu d’informations sur la page dans l’éditeur de Forms adaptatif.
