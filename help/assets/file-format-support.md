---
title: Formats de fichiers et types MIME pris en charge
description: File formats and MIME types supported by [!DNL Experience Manager Assets] as a Cloud Service.
contentOwner: AG
translation-type: tm+mt
source-git-commit: bafcf005a2264b96caa3d59c478aa57fb38b2a4c
workflow-type: tm+mt
source-wordcount: '785'
ht-degree: 93%

---


# [!DNL Assets] formats de fichier pris en charge {#supported-file-formats}

[!DNL Adobe Experience Manager] as a Cloud Service prend en charge les fonctionnalités de base de gestion de contenu (stockage, gestion des métadonnées en ligne, contrôle de version, chargement et téléchargement, etc.) pour tout fichier binaire, quel que soit son format. [!DNL Adobe Experience Manager Assets] prend en charge un large éventail de formats de fichiers et chaque fonctionnalité de produit prend en charge différents formats.

In addition, [!DNL Experience Manager Assets] provides extended support to generate previews and renditions and to extract metadata and text for full-text indexing. Cette prise en charge étendue est assurée à l’aide de [microservices de ressources](asset-microservices-configure-and-use.md).

Les éléments essentiels concernant la conversion des ressources à l’aide des microservices de ressources sont les suivants :

* Key [Adobe file formats](#adobe-formats) produced by Adobe applications and services, including [!DNL Adobe Photoshop], [!DNL Adobe InDesign], [!DNL Adobe Illustrator], [!DNL Adobe XD], [!DNL Adobe Dimension], and [!DNL Adobe Acrobat] or PDF.
* [Formats de fichiers d’imagerie](#image-formats) clés.
* [Formats de fichiers Camera Raw](#camera-raw-formats) pour un large éventail d’appareils photo, dont Canon, Nikon, Fujifilm, Olympus et d’autres fabricants (optimisés par Adobe Camera Raw).
* [Formats de documents](#document-formats) courants, y compris les formats Microsoft Office et Open Document.
* Large éventail de formats [vidéo](#video-formats) et [audio](#audio-formats).

La légende suivante décrit le niveau de prise en charge.

| Niveau de prise en charge | Description |
| ------------- | --------------------------- |
| ✓ | Pris en charge |
| * | Référez-vous aux remarques ci-dessous. |
| - | Non applicable |

## Formats Adobe {#adobe-formats}

| Format de fichier | Génération de miniatures | Extraction de texte intégral | Extraction de métadonnées | Largeur/Hauteur |
| ----------- | -------------------- | ------------------- | ------------------- | ------------ |
| AI | ✓ | - | ✓ | ✓ |
| COLLAGE | - | - | ✓ | - |
| DN | ✓ | - | ✓ | ✓ |
| IDEAS | - | - | ✓ | - |
| INDD | ✓ | - | ✓ | ✓ * |
| INDT | - | - | ✓ | - |
| PDF | ✓ | ✓ | ✓ | ✓ |
| PROTO | - | - | ✓ | - |
| PSB | ✓ | - | ✓ | ✓ |
| PSD | ✓ | - | ✓ | ✓ |
| XD | ✓ | - | ✓ | ✓ |

\* Pour les fichiers [!DNL Adobe InDesign] (INDD), la taille du rendu est déterminée par l’aperçu incorporé dans le fichier. Configurez les préférences dans [!DNL InDesign] (**[!UICONTROL Préférences > Gestion des fichiers > Toujours enregistrer les images d’aperçu avec les documents, Taille d’aperçu]**) pour incorporer un rendu plus grand.

## Formats d’image {#image-formats}

| Format de fichier | Génération de miniatures | Extraction de métadonnées | Largeur/Hauteur | Recadrer |
| ----------- | -------------------- | ------------------- | ------------ | -------- |
| BMP | ✓ | - | ✓ | ✓ |
| EPS | - | ✓ | - | - |
| GIF | ✓ | ✓ | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ |
| PNG | ✓ | ✓ | ✓ | ✓ |
| TIFF | ✓ | ✓ | ✓ | - |

## Formats des images dans [!DNL Dynamic Media] {#image-support-dynamic-media}

| Format | Transférer (format d’entrée) | Créer un paramètre d’image prédéfini (format de sortie) | Prévisualiser un rendu dynamique | Diffuser un rendu dynamique | Télécharger un rendu dynamique |
| ------- | --------------------- | ----------------------------------- | ------------------------- | ------------------------- | -------------------------- |
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ |
| TIFF | ✓ | ✓ | ✓ | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ |
| BMP | ✓ | - | - | - | - |
| PSD   ‡ | ✓ | - | - | - | - |
| EPS | ✓ | ✓ | ✓ | ✓ | ✓ |
| PICT | ✓ | - | - | - | - |

‡ L’image fusionnée est extraite du fichier PSD. Il s’agit d’une image générée par [!DNL Adobe Photoshop] et incluse dans le fichier PSD. Selon les paramètres, l’image fusionnée peut constituer ou non l’image réelle.

Les sous-types suivants de formats de fichiers d’images pixellisées ne sont pas pris en charge dans [!DNL Dynamic Media] :

* Fichiers PNG dont la taille de bloc IDAT est supérieure à 100 Mo.
* Fichiers PSB.
* Les fichiers PSD avec un espace colorimétrique autre que CMJN, RVB, niveaux de gris ou bitmap ne sont pas pris en charge. Les espaces colorimétriques DuoTone, Lab et indexé ne sont pas pris en charge.
* Fichiers PSD ayant une résolution binaire supérieure à 16.
* Fichiers TIFF contenant des données à virgule flottante.
* Fichiers TIFF dotés d’un espace colorimétrique Lab.

## Formats 3D {#support-3d-formats}

Les formats 3D de la liste suivante sont pris en charge.

Voir [Utilisation de ressources 3D dans Dynamic Media.](/help/assets/dynamic-media/assets-3d.md)

| Format | Stockage | Contrôle de version | Workflow | Publication | Contrôle d’accès | Aperçu de miniature | Aperçu 3D | Diffusion Dynamic Media |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| DN | ✓ | ✓ | ✓ | - | ✓ | ✓ | - | - |
| gLB | ✓ | ✓ | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| gLTF | ✓ | ✓ | ✓ | - | ✓ | - | ✓ | - |
| OBJ | ✓ | ✓ | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| STL | ✓ | ✓ | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| USDz | ✓ | ✓ | ✓ | ✓ | ✓ | - | - | ✓ |

## Formats [!DNL Camera RAW] {#camera-raw-formats}

| Format de fichier | Génération de miniatures | Extraction de métadonnées | Largeur/Hauteur |
| ----------- | -------------------- | ------------------- | ------------ |
| 3FR | ✓ | ✓ | ✓ |
| ARW | ✓ | ✓ | ✓ |
| CR2 | ✓ | ✓ | ✓ |
| CR3 | ✓ | ✓ | ✓ |
| CRW | ✓ | ✓ | ✓ |
| DCR | ✓ | ✓ | ✓ |
| DNG | ✓ | ✓ | ✓ |
| ERF | ✓ | ✓ | ✓ |
| FFF | ✓ | ✓ | ✓ |
| GPR | ✓ | ✓ | ✓ |
| IIQ | ✓ | ✓ | ✓ |
| KDC | ✓ | ✓ | ✓ |
| MEF | ✓ | ✓ | ✓ |
| MFW | ✓ | ✓ | ✓ |
| MOS | ✓ | ✓ | ✓ |
| MRW | ✓ | ✓ | ✓ |
| NEF | ✓ | ✓ | ✓ |
| NRW | ✓ | ✓ | ✓ |
| ORF | ✓ | ✓ | ✓ |
| PEF | ✓ | ✓ | ✓ |
| RAF | ✓ | ✓ | ✓ |
| RAW | ✓ | ✓ | ✓ |
| RW2 | ✓ | ✓ | ✓ |
| RWL | ✓ | ✓ | ✓ |
| SRF | ✓ | ✓ | ✓ |
| SRW | ✓ | ✓ | ✓ |
| X3F | ✓ | ✓ | ✓ |

## Formats de document {#document-formats}

Les formats de documents pris en charge pour les fonctionnalités de gestion des ressources sont les suivants.

| Format de fichier | Génération de miniatures | Extraction de texte intégral | Largeur/Hauteur | Gestion des métadonnées | [Ressources connectées](use-assets-across-connected-assets-instances.md) |
| ----------- | -------------------- | ------------------- | ------------ | ------------------- | ---------------- |
| PDF | ✓ | ✓ | ✓ | ✓ | ✓ |
| DOCX | ✓ | ✓ | ✓ | ✓ | ✓ |
| DOC | - | - | - | ✓ | ✓ |
| PPTX | ✓ | ✓ | ✓ | ✓ | ✓ |
| PPT | - | - | - | ✓ | ✓ |
| XLSX | ✓ | ✓ | ✓ | ✓ | ✓ |
| XLS | - | - | - | ✓ | ✓ |
| ODF | ✓ | ✓ | ✓ | - | - |
| OFG | ✓ | ✓ | ✓ | - | - |
| ODM | ✓ | ✓ | ✓ | - | - |
| ODP | ✓ | ✓ | ✓ | - | - |
| ODS | ✓ | ✓ | ✓ | - | - |
| ODT | ✓ | ✓ | ✓ | ✓ | ✓ |
| EPUB | - | ✓ | - | - | - |
| HTML | - | ✓ | - | ✓ | ✓ |
| PS | - | - | ✓ | - | - |
| RTF | - | ✓ | - | ✓ | ✓ |
| TXT | - | ✓ | - | ✓ | ✓ |
| XML | - | ✓ | - | - | - |

## Formats de document dans [!DNL Dynamic Media] {#document-support-dynamic-media}

| Format | Transférer (format d’entrée) | Créer un paramètre d’image prédéfini (format de sortie) | Prévisualiser un rendu dynamique | Diffuser un rendu dynamique | Télécharger un rendu dynamique |
| ------ | --------------------- | ----------------------------------- | ------------------------- | ------------------------- | -------------------------- |
| AI | ✓ | - | - | - | - |
| PDF | ✓ | ✓ | ✓ | ✓ | ✓ |
| INDD | ✓ | - | - | - | - |

## Formats vidéo {#video-formats}

| Format de fichier | Génération de miniatures | Extraction de métadonnées | Largeur/Hauteur |
| ----------- | -------------------- | ------------------- | ------------ |
| 3G2 | - | ✓ | - |
| 3GP | - | ✓ | - |
| AVI | ✓ | ✓ | ✓ |
| DIVX | ✓ | - | ✓ |
| F4V | ✓ | ✓ | ✓ |
| FLV | ✓ | ✓ | ✓ |
| M2T | ✓ | - | ✓ |
| M2TS | ✓ | - | ✓ |
| M2V | ✓ | - | ✓ |
| M4V | ✓ | ✓ | ✓ |
| MKV | ✓ | - | ✓ |
| MOV | ✓ | ✓ | ✓ |
| MP4 | ✓ | ✓ | ✓ |
| MPEG | ✓ | ✓ | ✓ |
| MPG | ✓ | ✓ | ✓ |
| MTS | ✓ | - | ✓ |
| OGV | ✓ | - | ✓ |
| QT | ✓ | - | ✓ |
| R3D | ✓ | - | ✓ |
| SWF | ✓ | - | ✓ |
| WEBM | ✓ | - | ✓ |
| WMV | ✓ | ✓ | ✓ |

## Formats vidéo dans [!DNL Dynamic Media] pour le transcodage {#video-dynamic-media-transcoding}

| Extension de fichier vidéo | Conteneur | Codecs vidéo recommandés | Codecs vidéo non pris en charge |
|------------------------|--------------------|--------|-------|
| MP4 | MPEG-4 | H264/AVC (tous les profils) | - |
| MOV, QT | Apple QuickTime | H264/AVC, Apple ProRes422 et HQ, Sony XDCAM, Sony DVCAM, HDV, Panasonic DVCPro, Apple DV (DV25), Apple PhotoJPEG, Sorenson, Avid DNxHD, Avid AVR | Apple Intermediate, Apple Animation |
| FLV, F4V | Adobe Flash | H264/AVC, Flix VP6, H263, Sorenson | SWF (fichiers d’animation vectorielle) |
| WMV | Windows Media 9 | WMV3 (v9), WMV2 (v8), WMV1 (v7), GoToMeeting (G2M2, G2M3, G2M4) | Microsoft Screen (MSS2), Microsoft Photo Story (WVP2) |
| MPG, VOB, M2V, MP2 | MPEG-2 | MPEG-2 | - |
| M4V | Apple iTunes | H264/AVC | - |
| AVI | A/V Interleave | XVID, DIVX, HDV, MiniDV (DV25), Techsmith Camtasia, Huffyuv, Fraps, Panasonic DVCPro | Indeo3 (IV30), MJPEG, Microsoft Video 1 (MS-CRAM) |
| WebM | WebM | Google VP8 | - |
| OGV, OGG | Ogg | Theora, VP3, Dirac | - |
| MXF | MXF | Sony XDCAM, MPEG-2, MPEG-4, Panasonic DVCPro | - |
| MTS | AVCHD | H264/AVC | - |
| MKV | Matroska | H264/AVC | - |
| R3D, RM | Red Raw Video | MJPEG 2000 | - |
| RAM, RM | RealVideo | Non pris en charge | Real G2 (RV20), Real 8 (RV30), Real 10 (RV40) |
| FLAC | Native Flac | FLAC (Free Lossless Audio Codec) | - |
| MJ2 | Motion JPEG 2000 | Codec Motion JPEG 2000 | - |

## Formats audio {#audio-formats}

[!DNL Assets] as a Cloud Service offre une prise en charge de l’extraction de métadonnées XMP pour les formats audio AIF, ASF, M4A, MP3, WAV et WMA.

>[!MORELIKETHIS]
>
>* [Traitement des ressources à l’aide des microservices de ressources](asset-microservices-overview.md)

