---
title: Gestion des ressources sous licence sur Content Hub
description: Découvrez comment ajouter un champ de licence au formulaire de métadonnées de ressource, appliquer la propriété de métadonnées Licence aux dossiers de ressources et approuver les ressources avec des licences pour les utiliser.
exl-id: ac3aad9f-c7b3-47a7-9314-a2f8277f0d3e
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 6%

---

# Gestion des ressources sous licence sur Content Hub {#manage-licensed-assets-on-content-hub}

En tant qu’administrateur, modifiez le formulaire de métadonnées pour inclure le champ de licence de la ressource afin qu’il s’affiche dans les propriétés de la ressource de l’environnement de création AEM. Vous pouvez ensuite approuver la ressource, ainsi que sa licence, afin de la rendre sous licence et disponible sur Content Hub.

Procédez comme suit :

1. Modifiez le formulaire de métadonnées afin d’inclure un nouveau champ de texte pour inclure les détails de licence. Mappez le champ de texte à `dc:license` propriété . Pour plus d’informations sur l’ajout de champs à un formulaire de métadonnées et la définition de propriétés, consultez [Configuration du Forms de métadonnées](/help/assets/metadata-assets-view.md#metadata-forms).
   ![extraction zip](/help/assets/assets/metadata-form-edit.png)
1. Appliquez le formulaire de métadonnées au dossier de ressources pour appliquer les paramètres intégrés à l’étape 1. Pour plus d’informations sur l’attribution d’un formulaire de métadonnées au dossier de ressources, consultez [Attribuer un formulaire de métadonnées à un dossier](/help/assets/metadata-assets-view.md#metadata-forms).
1. [Approuver le PDF sous licence](/help/assets/manage-organize-assets-view.md#set-asset-status)
1. Sélectionnez la ressource et cliquez sur **Détails** pour afficher ses propriétés. Dans le champ licence ajouté à l’étape 1, définissez le chemin d’accès absolu pour la licence de ressource qui a été approuvée à l’étape 3 ou qui a déjà été approuvée précédemment. Le chemin d’accès absolu Content Hub suit le modèle standard suivant : `/content/dam/(The asset's folder hierarchy within the DAM repository)/(asset_name).(file_extension)`. Par exemple, /content/dam/teamA/projects/documents/file1.pdf
   ![chemin absolu](/help/assets/assets/absolute-path.png)
1. Approuvez la ressource pour la rendre disponible dans Content Hub et cliquez sur **Enregistrer**. Pour plus d’informations sur l’approbation d’une ressource, voir [Définition du statut de la ressource](/help/assets/manage-organize-assets-view.md#set-asset-status).
