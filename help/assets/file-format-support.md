---
title: Formats de fichiers et types MIME pris en charge
description: Formats de fichier et types MIME pris en charge par  [!DNL Experience Manager Assets] as a [!DNL Cloud Service].
contentOwner: AG
translation-type: tm+mt
source-git-commit: ceaa9546be160e01b124154cc827e6b967388476
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 93%

---


# Formats de fichiers pris en charge [!DNL Assets] {#supported-file-formats}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] prend en charge les fonctionnalités de base de gestion de contenu (stockage, gestion des métadonnées en ligne, contrôle de version, chargement et téléchargement, etc.) pour tout fichier binaire, quel que soit son format. [!DNL Adobe Experience Manager Assets] prend en charge un large éventail de formats de fichiers et chaque fonctionnalité de produit prend en charge différents formats.

En outre, [!DNL Experience Manager Assets] offre une prise en charge étendue pour générer des aperçus et des rendus et extraire des métadonnées et du texte en vue de l’indexation en texte intégral. Cette prise en charge étendue est assurée à l’aide de [microservices de ressources](asset-microservices-configure-and-use.md).

Voici les points saillants de la conversion d’actifs à l’aide des microservices d’actifs :

* [Formats de fichiers Adobe](#adobe-formats) clés générés par les applications et services Adobe, notamment [!DNL Adobe Photoshop], [!DNL Adobe InDesign], [!DNL Adobe Illustrator], [!DNL Adobe XD], [!DNL Adobe Dimension] et [!DNL Adobe Acrobat] ou PDF.
* [Formats de fichiers d’imagerie](#image-formats) clés.
* [Formats de fichiers Camera Raw](#camera-raw-formats) pour un large éventail d’appareils photo, dont Canon, Nikon, Fujifilm, Olympus et d’autres fabricants (optimisés par Adobe Camera Raw).
* [Formats de documents](#document-formats) courants, y compris les formats Microsoft Office et Open Document.
* Large éventail de formats [vidéo](#video-formats) et [audio](#audio-formats).

La légende suivante décrit le niveau de prise en charge de chaque format.

| Niveau de prise en charge | Description |
| ------------- | --------------------------- |
| ✓ | Pris en charge |
| * | Référez-vous aux remarques ci-dessous. |
| - | Non applicable |

## Formats Adobe {#adobe-formats}

| Format de fichier | Génération de miniatures | Extraction de texte intégral | Extraction de métadonnées | Largeur/Hauteur |
| ----------- | -------------------- | ------------------- | ------------------- | ------------ |
| AI | obj | - | obj | obj |
| COLLAGE | - | - | obj | - |
| DN | obj | - | obj | obj |
| IDEAS | - | - | obj | - |
| INDD | obj | - | obj | ✓ * |
| INDT | - | - | obj | - |
| PDF | obj | obj | obj | obj |
| PROTO | - | - | obj | - |
| PSB | obj | - | obj | obj |
| PSD | obj | - | obj | obj |
| XD | obj | - | obj | obj |

\* Pour les fichiers [!DNL Adobe InDesign] (INDD), la taille du rendu est déterminée par l’aperçu incorporé dans le fichier. Configurez les préférences dans [!DNL InDesign] (**[!UICONTROL Préférences > Gestion des fichiers > Toujours enregistrer les images d’aperçu avec les documents, Taille d’aperçu]**) pour incorporer un rendu plus grand.

## Formats d’image {#image-formats}

| Format de fichier | Génération de miniatures | Extraction de métadonnées | Largeur/Hauteur | Recadrer |
| ----------- | -------------------- | ------------------- | ------------ | -------- |
| BMP | obj | - | obj | obj |
| EPS | - | obj | - | - |
| GIF | obj | obj | obj | obj |
| JPEG | obj | obj | obj | obj |
| PNG | obj | obj | obj | obj |
| RVB | obj | obj | obj | obj |
| RGBA | obj | obj | obj | obj |
| SGI | obj | obj | obj | obj |
| SVG | obj | - | obj | obj |
| TIFF | obj | obj | obj | - |

## Formats des images dans [!DNL Dynamic Media] {#image-support-dynamic-media}

| Format | Transférer (format d’entrée) | Créer un paramètre d’image prédéfini (format de sortie) | Prévisualiser un rendu dynamique | Diffuser un rendu dynamique | Télécharger un rendu dynamique |
| ------- | --------------------- | ----------------------------------- | ------------------------- | ------------------------- | -------------------------- |
| BMP | obj | - | - | - | - |
| EPS | obj | obj | obj | obj | obj |
| GIF | obj | obj | obj | obj | obj |
| JPEG | obj | obj | obj | obj | obj |
| PICT | obj | - | - | - | - |
| PNG | obj | obj | obj | obj | obj |
| PSD   ‡ | obj | - | - | - | - |
| TIFF | obj | obj | obj | obj | obj |

‡ L’image fusionnée est extraite du fichier PSD. Il s’agit d’une image générée par [!DNL Adobe Photoshop] et incluse dans le fichier PSD. Selon les paramètres, l’image fusionnée peut constituer ou non l’image réelle.

Les sous-types suivants de formats de fichiers d’images pixellisées ne sont pas pris en charge dans [!DNL Dynamic Media] :

* Fichiers PNG dont la taille de bloc IDAT est supérieure à 100 Mo.
* Fichiers PSB.
* Les fichiers PSD avec un espace colorimétrique autre que CMJN, RVB, niveaux de gris ou bitmap ne sont pas pris en charge. Les espaces colorimétriques DuoTone, Lab et indexé ne sont pas pris en charge.
* Fichiers PSD ayant une résolution binaire supérieure à 16.
* Fichiers TIFF contenant des données à virgule flottante.
* Fichiers TIFF dotés d’un espace colorimétrique Lab.

## Formats 3D {#support-3d-formats}

Les formats 3D suivants sont pris en charge.

Voir [Utilisation de ressources 3D dans Dynamic Media.](/help/assets/dynamic-media/assets-3d.md)

| Format | Stockage | Contrôle de version | Workflow | Publication | Contrôle d’accès | Aperçu de miniature | Aperçu 3D | Diffusion Dynamic Media |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| DN | obj | obj | obj | - | obj | obj | - | - |
| gLB | obj | obj | obj | obj | obj | - | obj | obj |
| gLTF | obj | obj | obj | - | obj | - | obj | - |
| OBJ | obj | obj | obj | obj | obj | - | obj | obj |
| STL | obj | obj | obj | obj | obj | - | obj | obj |
| USDz | obj | obj | obj | obj | obj | - | - | obj |

## Formats [!DNL Camera RAW] {#camera-raw-formats}

| Format de fichier | Génération de miniatures | Extraction de métadonnées | Largeur/Hauteur |
| ----------- | -------------------- | ------------------- | ------------ |
| 3FR | obj | obj | obj |
| ARW | obj | obj | obj |
| CR2 | obj | obj | obj |
| CR3 | obj | obj | obj |
| CRW | obj | obj | obj |
| DCR | obj | obj | obj |
| DNG | obj | obj | obj |
| ERF | obj | obj | obj |
| FFF | obj | obj | obj |
| GPR | obj | obj | obj |
| IIQ | obj | obj | obj |
| KDC | obj | obj | obj |
| MEF | obj | obj | obj |
| MFW | obj | obj | obj |
| MOS | obj | obj | obj |
| MRW | obj | obj | obj |
| NEF | obj | obj | obj |
| NRW | obj | obj | obj |
| ORF | obj | obj | obj |
| PEF | obj | obj | obj |
| RAF | obj | obj | obj |
| RAW | obj | obj | obj |
| RW2 | obj | obj | obj |
| RWL | obj | obj | obj |
| SRF | obj | obj | obj |
| SRW | obj | obj | obj |
| X3F | obj | obj | obj |

## Formats de document {#document-formats}

Les formats de documents pris en charge pour les fonctionnalités de gestion des ressources sont les suivants.

| Format de fichier | Génération de miniatures | Extraction de texte intégral | Largeur/Hauteur | Gestion des métadonnées | [Ressources connectées](use-assets-across-connected-assets-instances.md) |
| ----------- | -------------------- | ------------------- | ------------ | ------------------- | ---------------- |
| DOC | - | - | - | obj | obj |
| DOCX | obj | obj | obj | obj | obj |
| EPUB | - | obj | - | - | - |
| HTML | - | obj | - | obj | obj |
| ODF | obj | obj | obj | - | - |
| ODM | obj | obj | obj | - | - |
| ODP | obj | obj | obj | - | - |
| ODS | obj | obj | obj | - | - |
| ODT | obj | obj | obj | obj | obj |
| OFG | obj | obj | obj | - | - |
| PDF | obj | obj | obj | obj | obj |
| PPT | - | - | - | obj | obj |
| PPTX | obj | obj | obj | obj | obj |
| PS | - | - | obj | - | - |
| RTF | - | obj | - | obj | obj |
| TXT | - | obj | - | obj | obj |
| XLS | - | - | - | obj | obj |
| XLSX | obj | obj | obj | obj | obj |
| XML | - | obj | - | - | - |

## Formats de document dans [!DNL Dynamic Media] {#document-support-dynamic-media}

| Format | Transférer (format d’entrée) | Créer un paramètre d’image prédéfini (format de sortie) | Prévisualiser un rendu dynamique | Diffuser un rendu dynamique | Télécharger un rendu dynamique |
| ------ | --------------------- | ----------------------------------- | ------------------------- | ------------------------- | -------------------------- |
| AI | obj | - | - | - | - |
| INDD | obj | - | - | - | - |
| PDF | obj | obj | obj | obj | obj |

## Formats vidéo {#video-formats}

| Format de fichier | Génération de miniatures | Extraction de métadonnées | Largeur/Hauteur |
| ----------- | -------------------- | ------------------- | ------------ |
| 3G2 | - | obj | - |
| 3GP | - | obj | - |
| AVI | obj | obj | obj |
| DIVX | obj | - | obj |
| F4V | obj | obj | obj |
| FLV | obj | obj | obj |
| M2T | obj | - | obj |
| M2TS | obj | - | obj |
| M2V | obj | - | obj |
| M4V | obj | obj | obj |
| MKV | obj | - | obj |
| MOV | obj | obj | obj |
| MP4 | obj | obj | obj |
| MPEG | obj | obj | obj |
| MPG | obj | obj | obj |
| MTS | obj | - | obj |
| MXF | obj | - | obj |
| OGV | obj | - | obj |
| QT | obj | - | obj |
| R3D | - | obj | obj |
| SWF | obj | - | obj |
| WebM | obj | - | obj |
| WMV | obj | obj | obj |

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

[!DNL Assets] as a offre une prise en charge de l’extraction de métadonnées XMP pour les formats audio AIF, ASF, M4A, MP3, WAV et WMA.[!DNL Cloud Service]

## Conseils et restrictions {#limitations-and-tips}

* Actuellement, la taille de fichier maximale pour l’extraction des métadonnées est d’environ 10 Go. Lors du téléchargement de fichiers très volumineux, l’opération d’extraction des métadonnées échoue parfois.

>[!MORELIKETHIS]
>
>* [Traitement des ressources à l’aide des microservices de ressources](asset-microservices-overview.md)
>* [Formats de fichiers pris en charge pour le balisage intelligent des fichiers texte](/help/assets/smart-tags.md#smart-tags-supported-file-formats)

