---
title: Formats de fichiers pris en charge
description: Formats de fichiers pris en charge pour les différents cas d’utilisation d’ [!DNL Assets view]
role: User, Leader, Admin, Developer
contentOwner: AG
exl-id: 5936ace2-318e-4888-9ad4-23e6f6bfb857
feature: Asset Management, Publishing, Collaboration, Asset Processing
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 100%

---

# Prise en charge des formats de fichiers dans [!DNL Assets view] {#file-format-support}

[!DNL Assets view] prend en charge un large éventail de formats de fichier. Chaque fonctionnalité prend en charge différents types de fichiers.

* ![icône de type de fichier image](assets/image-icon.svg) Images : JPG, PNG, GIF, TIFF et autres.
* ![Icône creative cloudtype](assets/creative-cloud-files.svg) Fichiers de Creative Cloud : PSD, PSB, AI et INDD.
* ![icône de type appareil photo](assets/camera-icon.svg) Fichiers RAW de caméras : CR2/CR3, NEF, SRW/SRF et autres.
* ![Icône de type de fichier document](assets/document-icon.svg) Documents : DOCX, PDF, PPTX et XLSX
* ![Icône de type de fichier vidéo](assets/video-icon.svg) Vidéos : MP4

[!DNL Assets view] prend en charge tout format de fichier binaire avec les services de base, tels que le stockage, le chargement, la copie, le déplacement, la suppression et l’ajout de métadonnées.

[!DNL Assets view] prend également en charge les fichiers RAW de caméras provenant de nombreux fabricants de premier plan, dont Canon (CR2/CR3), Nikon (NEF), Sony (SRW/SRF), Fujifilm (RAF), Olympus (ORF), etc., optimisés par Adobe Camera Raw.

Les différents types de fichiers ont différents degrés de prise en charge pour les cas d’utilisation et les fonctionnalités comme décrit ci-dessous. Reportez-vous à la légende pour comprendre le niveau de prise en charge.

| Niveau de prise en charge | Description |
|-------------------|-------------------------|
| ✓ | Pris en charge |
| ✓ ‡ | Pris en charge dans certaines conditions |
| − | Non applicable |

## Ajout, chargement et affichage de ressources {#support-to-upload-view}

<!-- TBD: For AEM, AI files require the PDF option to be selected when saving the AI file.
-->

| Type de ressource | [Parcourir](/help/assets/navigate-assets-view.md) | Copier | [Chargement](/help/assets/add-delete-assets-view.md) | Créer | [Supprimer](/help/assets/add-delete-assets-view.md#delete-assets) | Détails | Zoom sur l’image | [Récemment consultés](/help/assets/navigate-assets-view.md) |
|-------------------|----------|----------|----------|----------|----------|-------------------|------------|-----------------|
| Images pixellisées | ✓ | ✓ | ✓ | − | ✓ | ✓ | ✓ | ✓ |
| Fichiers RAW | ✓ | ✓ | ✓ | − | ✓ | ✓ | ✓ | ✓ |
| Dossiers | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | − | − |
| Vidéos MP4 | ✓ | ✓ | ✓ | − | ✓ | ✓ ‡ | − | ✓ |
| PDF | ✓ | ✓ | ✓ | − | ✓ | ✓ | − | ✓ |
| PSD, PSB, AI et INDD | ✓ | ✓ | ✓ | − | ✓ | ✓ ‡ | − | ✓ |
| Autres fichiers binaires. | ✓ | ✓ | ✓ | − | ✓ | ✓ | − | ✓ |

<!-- Hiding CC Libraries (considered beta) as per PM feedback.
| CC Libraries  | &#10003; | &minus;  | &#10003; | &#10003; | &#10003; | &#10003; | &minus;    | &minus;         |
-->

## Recherche, utilisation et modification de ressources {#support-to-search-use-edit}

| Type de ressource | [Télécharger](/help/assets/manage-organize-assets-view.md#download) | Glisser-déplacer | [Éditeur d’image](/help/assets/edit-images-assets-view.md) | [Rechercher](/help/assets/search-assets-view.md) | [Balises intelligentes](/help/assets/metadata-assets-view.md#tags) | [Renommer](/help/assets/manage-organize-assets-view.md) | [Versions](/help/assets/manage-organize-assets-view.md#versions-of-assets) |
|---------------|----------|---------------|--------------|----------|------------|----------|----------|
| Images pixellisées | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Fichiers RAW | ✓ | ✓ | − | ✓ | ✓ | ✓ | ✓ | ✓ |
| Dossiers | ✓ | ✓ | − | ✓ | − | ✓ | ✓ |
| Vidéos | ✓ | ✓ | − | ✓ | ✓ | ✓ | ✓ |
| Bibliothèques CC | − | − | − | − | − | ✓ | ✓ |
| PDF | ✓ | ✓ | − | ✓ | ✓ | ✓ | ✓ |
| PSD et PSB | ✓ | ✓ | − | ✓ | ✓ | ✓ | ✓ |
| AI et INDD | ✓ | ✓ | − | ✓ | − | ✓ | ✓ |
| Autres fichiers binaires. | ✓ | ✓ | − | ✓ | − | ✓ | ✓ |


## Révision de ressources et collaboration {#support-to-review-collaborate}

| Type de ressource | Annoter | Commentaire | Création de tâches et révision |
|---------------|----------|----------|-------------------------|
| Images pixellisées | ✓ | ✓ | ✓ |
| Fichiers RAW | ✓ | ✓ | ✓ |
| Dossiers | − | − | − |
| Vidéos | − | ✓ | ✓ |
| Bibliothèques CC | − | − | − |
| PDF | − | ✓ | ✓ |
| PSD, PSB, AI et INDD | − | ✓ | ✓ |
| Autres fichiers binaires. | − | ✓ | ✓ |
| DOC | − | ✓ | ✓ |
| DOCX | − | ✓ | ✓ |
| PPT | − | ✓ | ✓ |
| PPTX | − | ✓ | ✓ |
| XLS | − | ✓ | ✓ |
| XLSX | − | ✓ | ✓ |
| TXT | − | ✓ | ✓ |
| RTF | − | ✓ | ✓ |

## Autres tâches de gestion des ressources {#support-to-manage-assets}

| Type de ressource | [Métadonnées](/help/assets/metadata-assets-view.md) | [Rendus](/help/assets/add-delete-assets-view.md#renditions) | [Corbeille](/help/assets/add-delete-assets-view.md#delete-assets) | Copier | Déplacer |
|---------------|-------------------|------------|----------|----------|----------|
| Images pixellisées | ✓ | ✓ | ✓ | ✓ | ✓ |
| Fichiers RAW | ✓ | ✓ | ✓ | ✓ | ✓ |
| Dossiers | ✓ | − | ✓ | ✓ | ✓ |
| Vidéos | ✓ | − | ✓ | ✓ | ✓ |
| Bibliothèques CC | ✓ | − | − | − | − |
| PDF | ✓ | − | ✓ | ✓ | ✓ |
| AI et INDD | ✓ | − | ✓ | ✓ | ✓ |
| PSD et PSB | ✓ | ✓ | ✓ | ✓ | ✓ |
| Autres fichiers binaires. | ✓ | − | ✓ | ✓ | ✓ |

Les utilisateurs de [!DNL Adobe Asset Link] peuvent charger et enregistrer (charger une nouvelle version) des fichiers dans le référentiel [!DNL Assets view] des applications de bureau [!DNL Adobe Creative Cloud] prises en charge.

<!-- TBD: Saving the template table separately for later use.
| Asset type    | Features |
|---------------|----------|
| Raster images |          |
| Folders       |          |
| Videos        |          |
| CC Libraries  |          |
| PDF files     |          |
| PSD, PSB           |          |
| AI            |          |
| INDD          |          |

>[!MORELIKETHIS]
>
>* []()
-->

## Étapes suivantes {#next-steps}

* Faites des commentaires sur le produit en utilisant l’option [!UICONTROL Commentaires] disponible dans l’interface utilisateur de la vue Assets

* Faites des commentaires sur la documentation en utilisant l’option [!UICONTROL Modifier cette page] ![modifier la page](assets/do-not-localize/edit-page.png) ou [!UICONTROL Enregistrer un problème] ![créer un problème GitHub](assets/do-not-localize/github-issue.png) disponible dans la barre latérale droite.

* Contactez l’[assistance clientèle](https://experienceleague.adobe.com/fr?support-solution=General#support).
