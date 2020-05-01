---
title: Formats de fichiers et types MIME pris en charge par Experience Manager Assets as a Cloud Service
description: Formats de fichier et types MIME pris en charge par Experience Manager Assets as a Cloud Service.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0686acbc61b3902c6c926eaa6424828db0a6421a

---


# Formats de fichiers pris en charge par Assets {#supported-file-formats}

Adobe Experience Manager as a Cloud Service prend en charge les fonctionnalités de gestion de contenu de base (enregistrement, gestion des métadonnées en ligne, contrôle de version, téléchargement et téléchargement, etc.) pour tout fichier binaire, quel que soit son format. Adobe Experience Manager Assets prend en charge un large éventail de formats de fichier et chaque fonction de produit prend en charge différents formats.

En outre, Experience Manager Assets offre une prise en charge étendue pour générer des prévisualisations et des rendus et pour extraire des métadonnées et du texte en vue de l’indexation en texte intégral. Cette prise en charge étendue est assurée à l’aide de [microservices de ressources](asset-microservices-configure-and-use.md).

La légende suivante décrit le niveau de prise en charge.

| Niveau de prise en charge | Description |
| ------------- | --------------------------- |
| ✓ | Pris en charge |
| * | Référez-vous aux remarques ci-dessous. |
| - | Non applicable |

## Asset conversion using asset microservices {#asset-microservices-supported-formats}

En voici un aperçu :

* Key [Adobe file formats](#adobe-formats) produced by Adobe applications and services, including Adobe Photoshop, Adobe InDesign, Adobe Illustrator, Adobe XD, Adobe Dimension, and Adobe Acrobat or PDF.
* Key [imaging file formats](#image-formats).
* [Formats de fichiers Camera Raw](#camera-raw-formats) pour un large éventail d’appareils photo, dont Canon, Nikon, Fujifilm, Olympus et d’autres fabricants (optimisés par Adobe Camera Raw).
* Common [document formats](#document-formats), including Microsoft Office and Open Document formats.
* Large éventail de formats [vidéo](#video-formats) et [audio.](#audio-formats)

Les colonnes des tableaux suivants fournissent les informations suivantes :

| Colonne | Description |
| ------------ | --------------------------------------------------------------- |
| Format | Format de fichier (extension de fichier) du fichier binaire d’origine. |
| GIF | Format GIF pour la génération de rendu. |
| JPEG | Format JPEG pour la génération de rendu. |
| PNG | Format PNG pour la génération de rendu. |
| Largeur/Hauteur | Prise en charge de la définition de la largeur et de la hauteur d’un rendu en pixels. |

### Formats Adobe {#adobe-formats}

| Format de fichier | GIF | JPEG | PNG | Extraction de texte intégral | Extraction de métadonnées | Largeur/Hauteur |
| ----------- | -------- | -------- | -------- | ------------------- | ------------------- | ------------ |
| AI | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| COLLAGE | - | - | - | - | ✓ | - |
| DN | ✓ | ✓ | ✓ |  | ✓ | ✓ |
| IDEAS | - | - | - | - | ✓ | - |
| INDD | ✓ | ✓ | ✓ | - | ✓ | ✓* |
| INDT | - | - | - | - | ✓ | - |
| PDF | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| PROTO | - | - | - | - | ✓ | - |
| PSB | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| PSD | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| XD | ✓ | ✓ | ✓ | - | ✓ | ✓ |

\* Pour les fichiers INDD (InDesign), la taille du rendu est déterminée par l’aperçu incorporé dans le fichier INDD. Configurez les préférences dans InDesign (**[!UICONTROL Préférences > Gestion des fichiers > Toujours enregistrer les images d’aperçu avec les documents, Taille d’aperçu]**) pour incorporer un rendu plus grand.

### Formats d’image {#image-formats}

| Format de fichier | GIF | JPEG | PNG | Extraction de métadonnées | Largeur/Hauteur |
| ----------- | -------- | -------- | -------- | ------------------- | ------------ |
| BMP | ✓ | ✓ | ✓ | - | ✓ |
| EPS | - | - | - | ✓ | - |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ |
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ |
| SVG | - | - | - | ✓ | - |
| TIFF | ✓ | ✓ | ✓ | ✓ | ✓ |

### Formats Camera RAW {#camera-raw-formats}

| Format de fichier | GIF | JPEG | PNG | Extraction de métadonnées | Largeur/Hauteur |
| ----------- | -------- | -------- | -------- | ------------------- | ------------ |
| 3FR | ✓ | ✓ | ✓ | ✓ | ✓ |
| ARW | ✓ | ✓ | ✓ | ✓ | ✓ |
| CR2 | ✓ | ✓ | ✓ | ✓ | ✓ |
| CR3 | ✓ | ✓ | ✓ | ✓ | ✓ |
| CRW | ✓ | ✓ | ✓ | ✓ | ✓ |
| DCR | ✓ | ✓ | ✓ | ✓ | ✓ |
| DNG | ✓ | ✓ | ✓ | ✓ | ✓ |
| ERF | ✓ | ✓ | ✓ | ✓ | ✓ |
| FFF | ✓ | ✓ | ✓ | ✓ | ✓ |
| GPR | ✓ | ✓ | ✓ | ✓ | ✓ |
| IIQ | ✓ | ✓ | ✓ | ✓ | ✓ |
| KDC | ✓ | ✓ | ✓ | ✓ | ✓ |
| MEF | ✓ | ✓ | ✓ | ✓ | ✓ |
| MFW | ✓ | ✓ | ✓ | ✓ | ✓ |
| MOS | ✓ | ✓ | ✓ | ✓ | ✓ |
| MRW | ✓ | ✓ | ✓ | ✓ | ✓ |
| NEF | ✓ | ✓ | ✓ | ✓ | ✓ |
| NRW | ✓ | ✓ | ✓ | ✓ | ✓ |
| ORF | ✓ | ✓ | ✓ | ✓ | ✓ |
| PEF | ✓ | ✓ | ✓ | ✓ | ✓ |
| RAF | ✓ | ✓ | ✓ | ✓ | ✓ |
| RAW | ✓ | ✓ | ✓ | ✓ | ✓ |
| RW2 | ✓ | ✓ | ✓ | ✓ | ✓ |
| RWL | ✓ | ✓ | ✓ | ✓ | ✓ |
| SRF | ✓ | ✓ | ✓ | ✓ | ✓ |
| SRW | ✓ | ✓ | ✓ | ✓ | ✓ |
| X3F | ✓ | ✓ | ✓ | ✓ | ✓ |

### Formats de document {#document-formats}

Les formats de document pris en charge pour les fonctionnalités de gestion des ressources sont les suivants.

|  | GIF | JPEG | PNG | Extraction de texte intégral | Largeur/Hauteur | Gestion des métadonnées | [Ressources connectées](use-assets-across-connected-assets-instances.md) |
| ---- | -------- | -------- | -------- | ------------------- | ------------ | ------------------- | ---------------- |
| PDF | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| DOCX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| DOC | - | - | - | - | - | ✓ | ✓ |
| PPTX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| PPT | - | - | - | - | - | ✓ | ✓ |
| XLSX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| XLS | - | - | - | - | - | ✓ | ✓ |
| ODF | ✓ | ✓ | ✓ | ✓ | ✓ | - | - |
| OFG | ✓ | ✓ | ✓ | ✓ | ✓ | - | - |
| ODM | ✓ | ✓ | ✓ | ✓ | ✓ | - | - |
| ODP | ✓ | ✓ | ✓ | ✓ | ✓ | - | - |
| ODS | ✓ | ✓ | ✓ | ✓ | ✓ | - | - |
| ODT | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| EPUB | - | - | - | ✓ | - | - | - |
| HTML | - | - | - | ✓ | - | ✓ | ✓ |
| PS | - | - | - | - | ✓ | - | - |
| RTF | - | - | - | ✓ | - | ✓ | ✓ |
| TXT | - | - | - | ✓ | - | ✓ | ✓ |
| XML | - | - | - | ✓ | - | - | - |

### Formats vidéo {#video-formats}

| Format de fichier | GIF | JPEG | PNG | Extraction de métadonnées | Largeur/Hauteur |
| ----------- | -------- | -------- | -------- | ------------------- | ------------ |
| 3G2 | - | - | - | ✓ | - |
| 3GP | - | - | - | ✓ | - |
| AVI | ✓ | ✓ | ✓ | ✓ | ✓ |
| DIVX | ✓ | ✓ | ✓ |  | ✓ |
| F4V | ✓ | ✓ | ✓ | ✓ | ✓ |
| FLV | ✓ | ✓ | ✓ | ✓ | ✓ |
| M2T | ✓ | ✓ | ✓ | - | ✓ |
| M2TS | ✓ | ✓ | ✓ | - | ✓ |
| M2V | ✓ | ✓ | ✓ | - | ✓ |
| M4V | ✓ | ✓ | ✓ | ✓ | ✓ |
| MKV | ✓ | ✓ | ✓ | - | ✓ |
| MOV | ✓ | ✓ | ✓ | ✓ | ✓ |
| MP4 | ✓ | ✓ | ✓ | ✓ | ✓ |
| MPEG | ✓ | ✓ | ✓ | ✓ | ✓ |
| MPG | ✓ | ✓ | ✓ | ✓ | ✓ |
| MTS | ✓ | ✓ | ✓ | - | ✓ |
| OGV | ✓ | ✓ | ✓ | - | ✓ |
| QT | ✓ | ✓ | ✓ | - | ✓ |
| R3D | ✓ | ✓ | ✓ | - | ✓ |
| SWF | ✓ | ✓ | ✓ | - | ✓ |
| WEBM | ✓ | ✓ | ✓ | - | ✓ |
| WMV | ✓ | ✓ | ✓ | ✓ | ✓ |

### Formats audio {#audio-formats}

Assets as a Cloud Service offre une prise en charge de l’extraction de métadonnées XMP pour les formats audio AIF, ASF, M4A, MP3, WAV et WMA.

>[!MORELIKETHIS]
>
>* [Traitement des ressources à l’aide des microservices de ressources](asset-microservices-overview.md)

