---
title: Gestion des ressources sous licence sur Content Hub
description: Découvrez comment ajouter un champ de licence au formulaire de métadonnées de ressource, appliquer la propriété de métadonnées Licence aux dossiers de ressources et approuver les ressources avec des licences pour les utiliser.
exl-id: ac3aad9f-c7b3-47a7-9314-a2f8277f0d3e
source-git-commit: bfa7ceeb839574ff1b80ffc25b6519a629247385
workflow-type: tm+mt
source-wordcount: '610'
ht-degree: 3%

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

## Questions fréquemment posées {#faqs-manage-licensed-assets-content-hub}

### Quel est l’objectif de la gestion des ressources sous licence sur AEM Assets Content Hub ?

La gestion des ressources sous licence sur Content Hub permet aux administrateurs de s’assurer que seules les ressources approuvées avec des licences valides sont disponibles, tout en maintenant la conformité et le suivi approprié des métadonnées dans l’environnement de création AEM.

### Comment ajouter un champ de licence aux propriétés d’une ressource dans Experience Manager as a Cloud Service ?

Vous pouvez ajouter un champ de licence aux propriétés de la ressource en modifiant le formulaire de métadonnées afin d’inclure un nouveau champ de texte mappé à la propriété `dc:license`. Ce champ apparaît ensuite dans les propriétés de la ressource de l’environnement de création AEM Assets.

### Comment appliquer un formulaire de métadonnées à un dossier de ressources pour inclure le champ de licence dans les propriétés des ressources ?

Modifiez le formulaire de métadonnées pour inclure le champ de licence. Appliquez ce formulaire de métadonnées au dossier de ressources de votre choix afin de vous assurer que les nouveaux paramètres sont intégrés pour toutes les ressources de ce dossier.

### Comment spécifier les détails de licence d’une ressource ?

Pour spécifier les détails de licence, sélectionnez la ressource, cliquez sur **Détails** pour afficher ses propriétés, puis saisissez le chemin d’accès absolu à la licence de ressource approuvée dans le champ licence ajouté au formulaire de métadonnées.

### Quel est le format requis pour le chemin d’accès absolu Content Hub d’une licence de ressource ?

Le chemin d’accès absolu au Content Hub doit suivre le modèle suivant : /content/dam/(La hiérarchie de dossiers de la ressource dans le référentiel DAM)/(asset_name).(extension_fichier). Par exemple, `/content/dam/teamA/projects/documents/file1.pdf`.

### Pourquoi est-il important d’approuver la ressource et sa licence pour les rendre disponibles sur AEM Assets Content Hub ?

L’approbation de la ressource et de sa licence garantit que seules les ressources correctement sous licence et autorisées sont disponibles sur AEM Assets Content Hub, ce qui contribue au maintien de la conformité et des droits d’utilisation appropriés.

### Comment rendre une ressource disponible dans AEM Assets Content Hub après approbation de sa licence ?

Après avoir défini le chemin d’accès de licence dans les propriétés de la ressource, approuvez la ressource et cliquez sur Enregistrer. Cette action rend la ressource sous licence disponible dans AEM Assets Content Hub.

### Qui est responsable de la gestion des ressources sous licence dans Content Hub ?

Les administrateurs sont chargés de modifier les formulaires de métadonnées, de les affecter à des dossiers de ressources et d’approuver les ressources et leurs licences dans Content Hub.
