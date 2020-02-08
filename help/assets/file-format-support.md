---
title: Formats de fichiers et types MIME pris en charge par Experience Manager Assets en tant que service Cloud
description: Formats de fichier et types MIME pris en charge par Experience Manager Assets en tant que service Cloud.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 776b089a322cc4f86fdcb9ddf1c3cc207fc85d39

---


# Assets supported file formats {#supported-file-formats}

Adobe Experience Manager as a Cloud Service prend en charge les fonctionnalités de base de gestion de contenu (stockage, gestion des métadonnées en ligne, gestion des versions, téléchargement et téléchargement, etc.) pour tout fichier binaire, quel que soit son format. En outre, pour les formats de fichier courants, tels que image, propriétaire Adobe, document et vidéo, il offre une prise en charge étendue pour générer des aperçus et des rendus et extraire des métadonnées et du texte pour l’indexation en texte intégral. Cette prise en charge étendue est assurée à l’aide de microservices [de](asset-microservices-configure-and-use.md)ressources.

Voici quelques points saillants des formats de fichier avec prise en charge étendue :

* Formats [de fichiers](#adobe-formats) Adobe clés générés par les applications et services Adobe, notamment Adobe Photoshop, InDesign, Illustrator, XD, Dimension et Acrobat / PDF.
* Formats de fichier [d’imagerie clés](#image-formats)
* [Formats](#camera-raw-formats) de fichiers Camera Raw pour un large éventail d’appareils photo, dont Canon, Nikon, Fujifilm, Olympus et d’autres fabricants (optimisés par Adobe Camera Raw)
* Formats [de](#document-formats)document courants, y compris les formats [Microsoft Office](#microsoft-office-formats) (Word, Excel, PowerPoint) et [Open Document](#opendocument-formats)
* Large éventail de formats [vidéo](#video-formats) et [audio](#audio-formats)

## Légende pour des informations d&#39;assistance détaillées {#legend-for-detailed-support-information}

La légende suivante décrit le niveau de prise en charge d’une fonction :

| Niveau de prise en charge | Description |
| ------------------------------------------------------------ | --------------------------- |
| ✓ | Pris en charge |
| * | Voir les remarques ci-dessous. |
| - | Non applicable |

Les colonnes des tableaux de prise en charge fournissent les informations suivantes :

| Colonne | Description |
| ------------ | --------------------------------------------------------------- |
| Format | Format de fichier (extension de fichier) du fichier binaire d’origine |
| GIF | Format GIF pour la génération de rendu |
| JPEG | Format JPEG pour la génération de rendu |
| PNG | Format PNG pour la génération de rendu |
| XMP | Extraction des métadonnées du fichier binaire d’origine |
| TXT | Extraction de texte du document pour indexation |
| Largeur/Hauteur | Prise en charge de la définition de la largeur et de la hauteur d’un rendu (pixels) |

<!-- Adding this checkmark icon ✓ does not look good in table. The icon's shade and size has to be toned down for good readability and less clutter.
@gklebus: I suggest using a checkmark character, either U+2713 ✓ CHECK MARK or U+2714 ✔ HEAVY CHECK MARK
-->

## Formats Adobe {#adobe-formats}

| Format de fichier | GIF | JPEG | PNG | TXT | XMP | Largeur/Hauteur |
| ----------- | --- | ---- | --- | --- | --- | ------------ |
| AI | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| COLLAGE | - | - | - | - | ✓ | - |
| DN | ✓ | ✓ | ✓ |  | ✓ | ✓ |
| IDÉES | - | - | - | - | ✓ | - |
| INDD | ✓ | ✓ | ✓ | - | ✓ | ✓* |
| INDT | - | - | - | - | ✓ | - |
| PDF | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| PROTO | - | - | - | - | ✓ | - |
| PSB | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| PSD | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| XD | ✓ | ✓ | ✓ | - | ✓ | ✓ |

\* Pour les fichiers INDD (InDesign), la taille du rendu est déterminée par l’aperçu incorporé dans le fichier INDD. Configurez les préférences dans InDesign (**[!UICONTROL Préférences > Gestion des fichiers > Toujours enregistrer les images d’aperçu avec les documents, Taille]** d’aperçu) pour incorporer un rendu plus grand.

## Formats d’image {#image-formats}

| Format de fichier | GIF | JPEG | PNG | XMP | Largeur/Hauteur |
| ----------- | --- | ---- | --- | --- | ------------ |
| BMP | ✓ | ✓ | ✓ | - | ✓ |
| EPS | - | - | - | ✓ | - |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ |
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ |
| SVG | - | - | - | ✓ | - |
| TIFF | ✓ | ✓ | ✓ | ✓ | ✓ |


## Format Camera RAW {#camera-raw-formats}

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

## Formats de document {#document-formats}

| Format de fichier | TXT | XMP |
| ----------- | --- | --- |
| EPUB | ✓ | - |
| HTML | ✓ | - |
| PS | - | ✓ |
| RTF | ✓ | - |
| TEXTE | ✓ | - |
| XML | ✓ | - |

## Formats Microsoft Office {#microsoft-office-formats}

| Format de fichier | GIF | JPEG | PNG | TEXTE | Largeur/Hauteur |
| ----------- | --- | ---- | --- | ---- | ------------ |
| DOCX | ✓ | ✓ | ✓ | ✓ | ✓ |
| PPTX | ✓ | ✓ | ✓ | ✓ | ✓ |
| XLSX | ✓ | ✓ | ✓ | ✓ | ✓ |

## Formats OpenDocument {#opendocument-formats}

| Format de fichier | GIF | JPEG | PNG | TEXTE | Hauteur |
| ----------- | --- | ---- | --- | ---- | ------ |
| ODF | ✓ | ✓ | ✓ | ✓ | ✓ |
| OFG | ✓ | ✓ | ✓ | ✓ | ✓ |
| ODM | ✓ | ✓ | ✓ | ✓ | ✓ |
| ODP | ✓ | ✓ | ✓ | ✓ | ✓ |
| ODS | ✓ | ✓ | ✓ | ✓ | ✓ |
| ODT | ✓ | ✓ | ✓ | ✓ | ✓ |

## Formats vidéo {#video-formats}

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

## Formats audio {#audio-formats}

Assets as a Cloud Service fournit une prise en charge XMP des formats audio suivants : AIF, ASF, M4A, MP3, WAV et WMA.

<!-- TBD: Some items from https://helpx.adobe.com/experience-manager/6-5/assets/using/assets-formats.html#SupportedinputvideoformatsforDynamicMediatranscoding may be applicable.

Bring more parity with https://helpx.adobe.com/experience-manager/6-5/assets/using/assets-formats.html#SupportedMIMEtypes.
https://helpx.adobe.com/experience-manager/6-5/assets/using/assets-formats.html#Supportedmultimediaformats
-->

>[!MORELIKETHIS]
>
>* [Traitement des ressources à l’aide des microservices de ressources](asset-microservices-overview.md)

