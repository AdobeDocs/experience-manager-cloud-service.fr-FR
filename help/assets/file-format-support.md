---
title: Formats de fichiers et types MIME pris en charge par Experience Manager Assets as a Cloud Service
description: Formats de fichier et types MIME pris en charge par Experience Manager Assets as a Cloud Service.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 9a7d2cff969a7920eb4fa3597846c11aa16392d9

---


# Formats de fichiers pris en charge par Assets {#supported-file-formats}

Adobe Experience Manager en tant que service Cloud prend en charge les fonctionnalités de base des  de base —  , gestion des métadonnées en ligne, gestion des versions, téléchargement et téléchargement, etc. — pour tout fichier binaire, quel que soit son format. Adobe Experience Manager Assets prend en charge un large éventail de formats de fichier et chaque fonctionnalité de produit prend en charge différents formats.

En outre, Experience Manager Assets offre une prise en charge étendue pour générer des  et des rendus et pour extraire des métadonnées et du texte pour l’indexation en texte intégral. Cette prise en charge étendue est assurée à l’aide de [microservices de ressources](asset-microservices-configure-and-use.md).

La légende suivante décrit le niveau de prise en charge.

| Niveau de prise en charge | Description |
| ------------------------------------------------------------ | --------------------------- |
| ✓ | Pris en charge |
| * | Référez-vous aux remarques ci-dessous. |
| - | Non applicable |

## Asset conversion using asset microservices {#asset-microservices-supported-formats}

En voici un aperçu :

* [Formats de fichiers Adobe](#adobe-formats) clés générés par les applications et services Adobe, notamment Adobe Photoshop, InDesign, Illustrator, XD, Dimension et Acrobat / PDF.
* [Formats de fichier d’imagerie](#image-formats) clés.
* [Formats de fichiers Camera Raw](#camera-raw-formats) pour un large éventail d’appareils photo, dont Canon, Nikon, Fujifilm, Olympus et d’autres fabricants (optimisés par Adobe Camera Raw).
* [Formats de document](#document-formats) courants, y compris les formats [Microsoft Office](#microsoft-office-formats) (Word, Excel, PowerPoint) et [Open Document.](#opendocument-formats)
* Large éventail de formats [vidéo](#video-formats) et [audio.](#audio-formats)

Les colonnes des tableaux suivants fournissent les informations suivantes :

| Colonne | Description |
| ------------ | --------------------------------------------------------------- |
| Format | Format de fichier (extension de fichier) du fichier binaire d’origine |
| GIF | Format GIF pour la génération de rendu |
| JPEG | Format JPEG pour la génération de rendu |
| PNG | Format PNG pour la génération de rendu |
| XMP | Extraction des métadonnées du fichier binaire d’origine |
| TXT | Extraction de texte du document pour indexation |
| Largeur/Hauteur | Prise en charge de la définition de la largeur et de la hauteur d’un rendu (pixels) |

### Formats Adobe {#adobe-formats}

| Format de fichier | GIF | JPEG | PNG | TXT | XMP | Largeur/Hauteur |
| ----------- | --- | ---- | --- | --- | --- | ------------ |
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

| Format de fichier | GIF | JPEG | PNG | XMP | Largeur/Hauteur |
| ----------- | --- | ---- | --- | --- | ------------ |
| BMP | ✓ | ✓ | ✓ | - | ✓ |
| EPS | - | - | - | ✓ | - |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ |
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ |
| SVG | - | - | - | ✓ | - |
| TIFF | ✓ | ✓ | ✓ | ✓ | ✓ |

### Formats Camera RAW {#camera-raw-formats}

| Format de fichier | GIF | JPEG | PNG | XMP | Largeur/Hauteur |
| ----------- | --- | ---- | --- | --- | ------------ |
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

| Format de fichier | TXT | XMP |
| ----------- | --- | --- |
| EPUB | ✓ | - |
| HTML | ✓ | - |
| PS | - | ✓ |
| RTF | ✓ | - |
| TEXTE | ✓ | - |
| XML | ✓ | - |

### Formats Microsoft Office {#microsoft-office-formats}

| Format de fichier | GIF | JPEG | PNG | TEXTE | Largeur/Hauteur |
| ----------- | --- | ---- | --- | ---- | ------------ |
| DOCX | ✓ | ✓ | ✓ | ✓ | ✓ |
| PPTX | ✓ | ✓ | ✓ | ✓ | ✓ |
| XLSX | ✓ | ✓ | ✓ | ✓ | ✓ |

### Formats OpenDocument {#opendocument-formats}

| Format de fichier | GIF | JPEG | PNG | TEXTE | Hauteur |
| ----------- | --- | ---- | --- | ---- | ------ |
| ODF | ✓ | ✓ | ✓ | ✓ | ✓ |
| OFG | ✓ | ✓ | ✓ | ✓ | ✓ |
| ODM | ✓ | ✓ | ✓ | ✓ | ✓ |
| ODP | ✓ | ✓ | ✓ | ✓ | ✓ |
| ODS | ✓ | ✓ | ✓ | ✓ | ✓ |
| ODT | ✓ | ✓ | ✓ | ✓ | ✓ |

### Formats vidéo {#video-formats}

| Format de fichier | GIF | JPEG | PNG | XMP | Largeur/Hauteur |
| ----------- | --- | ---- | --- | --- | ------------ |
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

Assets as a Cloud Service assure la prise en charge XMP des formats audio suivants : AIF, ASF, M4A, MP3, WAV et WMA.

## Formats de document pris en charge {#doc-formats}

Les formats de  pris en charge pour les fonctionnalités de gestion des ressources sont les suivants.

| Format de fichier | Stockage | Gestion des métadonnées | [Ressources connectées](use-assets-across-connected-assets-instances.md) |
|---|---|---|---|
| DOC | ✓ | ✓ | ✓ |
| DOCX | ✓ | ✓ | ✓ |
| ODT | ✓ | ✓ | ✓ |
| PDF | ✓ | ✓ | ✓ |
| HTML | ✓ | ✓ | ✓ |
| RTF | ✓ | ✓ | ✓ |
| TXT | ✓ | ✓ | ✓ |
| XLS | ✓ | ✓ | ✓ |
| XLSX | ✓ | ✓ | ✓ |
| PPT | ✓ | ✓ | ✓ |
| PPTX | ✓ | ✓ | ✓ |

>[!MORELIKETHIS]
>
>* [Traitement des ressources à l’aide des microservices de ressources](asset-microservices-overview.md)

