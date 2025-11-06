---
title: Comment publier ou dépublier des formulaires sur des instances d’aperçu ou de publication ?
description: Découvrez comment publier ou dépublier des formulaires dans l’environnement de création d’AEM pour prévisualiser ou publier des instances. Que vous testiez vos formulaires dans un environnement d’évaluation ou que vous les déployiez en direct pour les utilisateurs finaux, AEM fournit des outils rationalisés pour gérer ce processus efficacement.
Keywords: Manage publication, Forms Manage publication, AF Manage publication, Adaptive Forms Manage publication, Cloud Manage publication
feature: Adaptive Forms
feature-set: Experience Manager Assets,Experience Manager Sites,Experience Manager, Experience Manager Forms, Experience Manager Cloud Manager
role: User, Developer
level: Intermediate
exl-id: 6ade40f1-bad5-4f5e-aa0e-84b7c6a82e02
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '945'
ht-degree: 7%

---


# Gestion de la publication dans Experience Manager Forms

En tant qu’administrateur ou administratrice Adobe Experience Manager (AEM) Forms, vous pouvez publier des formulaires de votre instance d’auteur sur Experience Manager Forms. Vous avez également la possibilité de planifier la publication d’un formulaire ou d’un dossier à une date ou une heure ultérieure. Une fois la publication effectuée, les utilisateurs et utilisatrices peuvent accéder aux formulaires et les remplir.

Dans Experience Manager Forms, vous pouvez publier un formulaire à l’aide de l’une des méthodes suivantes :

* [Option de publication](#publish-forms-using-the-publish-option)
* [Option Gérer la publication](#publish-forms-using-the-manage-publication-option)

## Éléments à garder à l’esprit

* Seuls les membres du groupe de `forms-users` peuvent utiliser l’option **Gérer la publication** pour publier les formulaires.
* Les modifications apportées aux formulaires ou aux dossiers dans Experience Manager Forms n’apparaissent pas dans l’instance de **Publication** tant qu’elles n’ont pas été republiées. Cela garantit que les mises à jour de travail en cours restent indisponibles dans l’instance de **publication**. Seules les modifications explicitement publiées par un administrateur sont répercutées dans l’instance de **publication**.

## Publication de formulaires à l’aide de l’option Publication

L&#39;option **Publier** permet de publier immédiatement un formulaire. Pour publier un formulaire Experience Manager à l’aide du bouton **Publier** de la barre d’outils. Pour publier des formulaires à l’aide de l’option Publier , procédez comme suit :

1. Dans la console Experience Manager Forms, accédez au dossier parent et sélectionnez un formulaire que vous souhaitez publier.
1. Cliquez sur l’option **Publier** dans la barre d’outils, consultez toutes les ressources de référence qui seraient publiées avec le formulaire.
1. Cliquez sur **[!UICONTROL Publier]**.

   ![Publier et dépublier le formulaire](/help/edge/docs/forms/assets/publish-form-option.png)

   Une fois le formulaire et ses ressources associées publiés, une boîte de dialogue **Succès** s’affiche.
1. Cliquez sur **Fermer**.

   ![Boîte de dialogue Succès](/help/forms/assets/publish-success1.png)

### Dépublication du formulaire

Une fois le formulaire publié à l’aide de l’option **Publier** et des ressources associées, vous pouvez même le dépublier à l’aide du bouton **[!UICONTROL Dépublier]** disponible dans la barre d’outils. Pour dépublier le formulaire :

1. Pour dépublier le formulaire et les ressources associées, sélectionnez le formulaire et cliquez sur **[!UICONTROL Dépublier]** dans la barre d’outils

   Lorsque vous cliquez sur le bouton **[!UICONTROL Dépublier]**, la boîte de dialogue **Dépublier l’élément** s’affiche.
1. Cliquez sur **[!UICONTROL Dépublier]** pour lancer le processus de dépublication

   ![Boîte de dialogue Dépublier](/help/forms/assets/unpublish-asset.png)

   Une fois la dépublication du formulaire et des ressources associées effectuée, une boîte de dialogue **Succès** s’affiche.
1. Cliquez sur **Fermer**.

   ![dépublication réussie](/help/forms/assets/unpublishing-start.png)

## Publier des formulaires à l’aide de l’option Gérer la publication

L’option Gérer la publication permet de publier ou de dépublier du contenu vers et depuis la destination sélectionnée, d’ajouter du contenu à la liste de publication à partir du dossier `forms&documents`, de sélectionner les références à publier et de planifier une publication à une date ou une heure ultérieure.  Pour publier des formulaires à l’aide de l’option **Gérer la publication**, procédez comme suit :

1. Dans la console Experience Manager Forms, accédez au dossier parent et sélectionnez un formulaire que vous souhaitez publier.
1. Cliquez sur l’option **[!UICONTROL Gérer la publication]** dans la barre d’outils.

   ![Option Gérer la publication](/help/forms/assets/manage-publication-option.png)

   L’interface utilisateur **Gérer la publication** s’affiche :

   ![Gérer la publication.](/help/forms/assets/manage-publication.png)

   Les options suivantes sont disponibles dans l’interface utilisateur **Gérer la publication** :

   * **Actions**

      * **Publier** : permet de publier des formulaires vers la destination sélectionnée
      * **Dépublier** : dépublication de formulaires de la destination

   * **Destination**

      * **Publication** : publication de formulaires sur l’instance de publication Experience Manager Forms (AEM).
      * **Aperçu** : publication de formulaires sur l’instance d’aperçu de Experience Manager Forms (AEM).

   * **Planification**

      * **Maintenant** : publiez immédiatement les formulaires
      * **Ultérieurement** : publiez les formulaires en fonction de l’**Date ou heure d’activation**

1. Cliquez sur **Suivant** pour continuer.
1. (Facultatif) Dans l’onglet **Portée**, utilisez l’option [Ajouter du contenu](#add-content) pour ajouter plus de contenu à publier. Par exemple, vous pouvez ajouter d’autres fichiers Forms ou Document d’enregistrement.
   ![onglet portée](/help/forms/assets/scope-tab.png)
1. Cliquez sur **[!UICONTROL Publier]** pour publier les formulaires et les ressources associées et un message de réussite s’affiche.
   ![publication du message réussie](/help/forms/assets/publish-successful.png)

### Ajouter du contenu

La publication sur Experience Manager Forms vous permet d’ajouter davantage de contenu (formulaires) à la liste de publication.
Pour ajouter d’autres formulaires à publier :

1. Cliquez sur le bouton **Ajouter du contenu** pour ajouter plus de contenu.

   ![ Ajouter du contenu ](/help/forms/assets/add-content.png)

2. Sélectionnez le formulaire dans l’écran **Sélectionner le chemin d’accès**.

   ![ Ajouter du contenu ](/help/forms/assets/add-assets.png)

   >[!NOTE]
   >
   > Vous pouvez ajouter d’autres formulaires ou dossiers à la liste à partir du dossier `formsanddocuments` . Cependant, vous ne pouvez pas ajouter de formulaires provenant de plusieurs dossiers à la fois.

3. Pour configurer les références afin de publier ou non pour un formulaire, sélectionnez le formulaire et cliquez sur **[!UICONTROL Références publiées]**.

   ![références publiées](/help/forms/assets/published-references.png)

4. Dans la boîte de dialogue **Références publiées**, désélectionnez les ressources que vous prévoyez de ne pas publier et cliquez sur **[!UICONTROL Terminé]**.
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


### Publication ou dépublication ultérieure d’un formulaire

En plus de vous permettre de publier ou de dépublier des formulaires à une date et une heure ultérieures, l’option publier ou dépublier ultérieurement permet également de configurer un workflow. Les formulaires sont publiés ou dépubliés une fois le workflow terminé.

Pour planifier la publication ou la dépublication d’un formulaire :

1. Dans la console Experience Manager Forms, accédez au dossier parent et sélectionnez le formulaire dont vous souhaitez planifier la publication.
1. Cliquez sur l’option **[!UICONTROL Gérer la publication]** dans la barre d’outils.

   ![Gérer la publication.](/help/forms/assets/manage-publication.png)

1. Cliquez sur **Publier** ou **Dépublier** dans **[!UICONTROL Action]**.
1. Sélectionnez la **[!UICONTROL Destination]** où vous souhaitez publier ou dépublier le contenu.
   * **Prévisualisation** : utilisez l’option **Prévisualisation** pour publier ou dépublier dans un environnement de prévisualisation Experience Manager Forms. Les environnements de prévisualisation Experience Manager Forms sont utilisés pour tester les formulaires en cours de développement.
   * **Publication** : utilisez l’option Experience Manager Forms **Publication** pour envoyer le formulaire à l’environnement de publication Experience Manager Forms une fois que le formulaire est prêt à être utilisé dans un environnement de production.

1. Sélectionnez **[!UICONTROL Plus tard]** dans **Planification**.

   ![Gérer la publication ultérieurement](/help/forms/assets/manage-publication-later.png)

1. Sélectionnez une **[!UICONTROL Date d’activation]** et spécifiez la date et l’heure.
1. Cliquez sur **[!UICONTROL Suivant]**.
1. (Facultatif) Dans l’onglet **Portée**, ajoutez du contenu à l’aide de **[!UICONTROL Ajouter du contenu]** .
   ![Gérer la publication ajouter du contenu ultérieurement](/help/forms/assets/publish-later-add-content.png)
1. Cliquez sur **[!UICONTROL Suivant]**.
1. Dans l’onglet **Workflows**, spécifiez un **[!UICONTROL Titre du workflow]**.
1. Cliquez sur **[!UICONTROL Publier ultérieurement]**.

   ![Gestion du processus de publication](/help/forms/assets/manage-publication-workflows.png)

## Définition du statut de publication

Il existe plusieurs façons de déterminer le statut de publication :

* Connectez-vous à l’instance de destination pour vérifier les formulaires publiés et d’autres ressources (selon la date ou l’heure planifiée).

* Utilisez la vue chronologique pour déterminer le statut de la publication.

* Utilisez le menu d’informations sur la page dans l’éditeur de Forms adaptatif.
