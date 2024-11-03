---
title: Gestion d’Assets sous licence sur Content Hub
description: Découvrez comment ajouter un champ de licence au formulaire de métadonnées de ressource, appliquer la propriété de métadonnées de licence aux dossiers de ressources et approuver les ressources avec des licences d’utilisation.
source-git-commit: 9324faf8c93620f5fccb1476eb124f5e640f193e
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 1%

---


# Gestion d’Assets sous licence sur Content Hub {#manage-licensed-assets-on-content-hub}

En tant qu’administrateur, modifiez le formulaire de métadonnées pour inclure le champ de licence de ressource afin qu’il s’affiche dans les propriétés Asset dans l’environnement de création AEM. Vous pouvez ensuite approuver la ressource ainsi que sa licence pour la rendre disponible et sous licence sur Content Hub.

Procédez comme suit :

1. Modifiez le formulaire de métadonnées afin d’inclure un nouveau champ de texte contenant les détails de la licence. Faites correspondre le champ de texte à la propriété `dc:license`. Pour plus d’informations sur l’ajout de champs à un formulaire de métadonnées et la définition de propriétés, voir [Configuration de la Forms de métadonnées](/help/assets/metadata-assets-view.md#metadata-forms).
   ![Extraction zip](/help/assets/assets/metadata-form-edit.png)
1. Appliquez le formulaire de métadonnées au dossier de ressources pour appliquer les paramètres intégrés à l’étape 1. Pour plus d’informations sur l’affectation d’un formulaire de métadonnées au dossier de ressources, voir [Affectation d’un formulaire de métadonnées à un dossier](/help/assets/metadata-assets-view.md#metadata-forms).
1. [Approuver le PDF sous licence](/help/assets/manage-organize-assets-view.md#set-asset-status)
1. Sélectionnez la ressource et cliquez sur **Details** pour afficher ses propriétés. Dans le champ de licence ajouté à l’étape 1, définissez le chemin absolu de la licence de ressource qui a été approuvée à l’étape 3 ou déjà approuvée précédemment. Le chemin d’accès absolu de Content Hub suit ce modèle standard : `/content/dam/(The asset's folder hierarchy within the DAM repository)/(asset_name).(file_extension)`. Par exemple, /content/dam/teamA/projects/documents/file1.pdf
   ![Chemin absolu](/help/assets/assets/absolute-path.png)
1. Approuvez la ressource pour la rendre disponible dans Content Hub et cliquez sur **Enregistrer**. Pour plus d’informations sur l’approbation d’une ressource, voir [Définition de l’état de la ressource](/help/assets/manage-organize-assets-view.md#set-asset-status).



