---
title: Formats de fichiers et types MIME pris en charge
description: Formats de fichier et types MIME pris en charge par [!DNL Experience Manager Assets] as a [!DNL Cloud Service].
contentOwner: AG
feature: Asset Management,Renditions
role: User,Admin
exl-id: e848aa77-7829-4adc-8b88-0279791a4525
source-git-commit: 6c17b048631a7f61305ec4f0a4f84c4b0577aec0
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 89%

---

# Formats de fichiers pris en charge [!DNL Assets]  {#supported-file-formats}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] prend en charge les fonctionnalités de base de gestion de contenu (stockage, gestion des métadonnées en ligne, contrôle de version, chargement et téléchargement, etc.) pour tout fichier binaire, quel que soit son format. [!DNL Adobe Experience Manager Assets] prend en charge un large éventail de formats de fichiers et chaque fonctionnalité de produit prend en charge différents formats.

En outre, [!DNL Experience Manager Assets] offre une prise en charge étendue pour générer des aperçus et des rendus et extraire des métadonnées et du texte en vue de l’indexation en texte intégral. Cette prise en charge étendue est assurée à l’aide de [microservices de ressources](asset-microservices-configure-and-use.md).

Les éléments essentiels concernant la conversion des ressources à l’aide des microservices de ressources sont les suivants :

* [Formats de fichiers Adobe](#adobe-formats) clés générés par les applications et services Adobe, notamment [!DNL Adobe Photoshop], [!DNL Adobe InDesign], [!DNL Adobe Illustrator], [!DNL Adobe XD], [!DNL Adobe Dimension] et [!DNL Adobe Acrobat] ou PDF.
* [Formats de fichiers d’imagerie](#image-formats) clés.
* [Formats de fichiers Camera Raw](#camera-raw-formats) pour un large éventail d’appareils photo, dont Canon, Nikon, Fujifilm, Olympus et d’autres fabricants (optimisés par Adobe Camera Raw).
* [Formats de documents](#document-formats) courants, y compris les formats Microsoft Office et Open Document.
* Large éventail de formats [vidéo](#video-formats) et [audio](#audio-formats).

Le tableau suivant décrit le niveau de prise en charge pour chaque format.

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
| RVB | ✓ | ✓ | ✓ | ✓ |
| RGBA | ✓ | ✓ | ✓ | ✓ |
| SGI | ✓ | ✓ | ✓ | ✓ |
| SVG | ✓ | - | ✓ | ✓ |
| TIFF | ✓ | ✓ | ✓ | - |

## Formats des images dans [!DNL Dynamic Media] {#image-support-dynamic-media}

| Format | Transférer (format d’entrée) | Créer un paramètre d’image prédéfini (format de sortie) | Prévisualiser un rendu dynamique | Diffuser un rendu dynamique | Télécharger un rendu dynamique |
| ------- | --------------------- | ----------------------------------- | ------------------------- | ------------------------- | -------------------------- |
| BMP | ✓ | - | - | - | - |
| EPS | ✓ | ✓ | ✓ | ✓ | ✓ |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ |
| PICT | ✓ | - | - | - | - |
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ |
| PSD   ‡ | ✓ | - | - | - | - |
| TIFF | ✓ | ✓ | ✓ | ✓ | ✓ |

‡ L’image fusionnée est extraite du fichier PSD. Il s’agit d’une image générée par [!DNL Adobe Photoshop] et incluse dans le fichier PSD. Selon les paramètres, l’image fusionnée peut constituer ou non l’image réelle.

Les sous-types suivants de formats de fichiers d’images pixellisées ne sont pas pris en charge dans [!DNL Dynamic Media] :

* Fichiers PNG dont la taille de bloc IDAT est supérieure à 100 Mo.
* Fichiers PSB.
* Les fichiers PSD avec un espace colorimétrique autre que CMJN, RVB, niveaux de gris ou bitmap ne sont pas pris en charge. Les espaces colorimétriques DuoTone, Lab et indexé ne sont pas pris en charge.
* Fichiers PSD ayant une résolution binaire supérieure à 16.
* Fichiers TIFF contenant des données à virgule flottante.
* Fichiers TIFF dotés d’un espace colorimétrique Lab.

## Formats 3D {#support-3d-formats}

Les formats 3D suivants sont pris en charge.

Voir [Utilisation de ressources 3D dans Dynamic Media](/help/assets/dynamic-media/assets-3d.md).

| Format | Stockage | Contrôle de version | Workflow | Publication | Contrôle d’accès | Aperçu de miniature | Aperçu 3D | Diffusion Dynamic Media |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| DN | ✓ | ✓ | ✓ | - | ✓ | ✓ | - | - |
| gLB | ✓ | ✓ | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| gLTF | ✓ | ✓ | ✓ | - | ✓ | - | ✓ | - |
| OBJ | ✓ | ✓ | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| STL | ✓ | ✓ | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| USDz | ✓ | ✓ | ✓ | ✓ | ✓ | - | - | ✓ |

## Formats [!DNL Camera RAW]  {#camera-raw-formats}

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
| DOC | - | - | - | ✓ | ✓ |
| DOCX | ✓ | ✓ | ✓ | ✓ | ✓ |
| EPUB | - | ✓ | - | - | - |
| HTML | - | ✓ | - | ✓ | ✓ |
| ODF | ✓ | ✓ | ✓ | - | - |
| ODM | ✓ | ✓ | ✓ | - | - |
| ODP | ✓ | ✓ | ✓ | - | - |
| ODS | ✓ | ✓ | ✓ | - | - |
| ODT | ✓ | ✓ | ✓ | ✓ | ✓ |
| OFG | ✓ | ✓ | ✓ | - | - |
| PDF | ✓ | ✓ | ✓ | ✓ | ✓ |
| PPT | - | - | - | ✓ | ✓ |
| PPTX | ✓ | ✓ | ✓ | ✓ | ✓ |
| PS | - | - | ✓ | - | - |
| RTF | - | ✓ | - | ✓ | ✓ |
| TXT | ✓ | ✓ | - | ✓ | ✓ |
| XLS | - | - | - | ✓ | ✓ |
| XLSX | ✓ | ✓ | ✓ | ✓ | ✓ |
| XML | - | ✓ | - | - | - |

## Formats de document dans [!DNL Dynamic Media] {#document-support-dynamic-media}

| Format | Transférer (format d’entrée) | Créer un paramètre d’image prédéfini (format de sortie) | Prévisualiser un rendu dynamique | Diffuser un rendu dynamique | Télécharger un rendu dynamique |
| ------ | --------------------- | ----------------------------------- | ------------------------- | ------------------------- | -------------------------- |
| AI | ✓ | - | - | - | - |
| INDD | ✓ | - | - | - | - |
| PDF | ✓ | ✓ | ✓ | ✓ | ✓ |

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
| MXF | ✓ | - | ✓ |
| OGV | ✓ | - | ✓ |
| QT | ✓ | - | ✓ |
| R3D | - | ✓ | ✓ |
| SWF | ✓ | - | ✓ |
| WebM | ✓ | - | ✓ |
| WMV | ✓ | ✓ | ✓ |

## Formats vidéo dans [!DNL Dynamic Media] pour le transcodage {#video-dynamic-media-transcoding}

| Extension de fichier vidéo | Conteneur | Codecs vidéo recommandés | Codecs vidéo non pris en charge |
| --- | --- | --- | --- |
| AVI | A/V Interleave | XVID, DIVX, HDV, MiniDV (DV25), Techsmith Camtasia, Huffyuv, Fraps, Panasonic DVCPro | Indeo3 (IV30), MJPEG, Microsoft Video 1 (MS-CRAM) |
| FLV, F4V | Adobe Flash | H264/AVC, Flix VP6, H263, Sorenson | SWF (fichiers d’animation vectorielle) |
| M4V | Apple iTunes | H264/AVC | - |
| MKV | Matroska | H264/AVC | - |
| MOV, QT | Apple QuickTime | H264/AVC, QG Apple ProRes422, Sony XDCAM, Sony DVCAM, HDV, Panasonic DVCPro, Apple DV (DV25), Apple PhotoJPEG, Sorenson, Avid DNxHD, Avid AVR | Apple Intermediate, Apple Animation |
| MP4 | MPEG-4 | H264/AVC (tous les profils) | - |
| MPG, VOB, M2V, MP2 | MPEG-2 | MPEG-2 | - |
| MXF |  | Media eXchange Format.<br>Apple ProRes422 | - |
| OGV, OGG | Ogg | Theora, VP3, Dirac | - |
| WebM | WebM | Google VP8 | - |
| WMV | Windows Media 9 | WMV3 (v9), WMV2 (v8), WMV1 (v7), GoToMeeting (G2M2, G2M3, G2M4) | Microsoft Screen (MSS2), Microsoft Photo Story (WVP2) |

## Formats audio {#audio-formats}

[!DNL Assets] as a [!DNL Cloud Service] offre une prise en charge de l’extraction de métadonnées XMP pour les formats audio AIF, ASF, M4A, MP3, WAV et WMA.

## Formats d’entrée pris en charge pour la transcription audio et vidéo {#audio-video-transcription-formats}

* FLV (avec les codecs H.264 et AAC) (.flv)
* MXF (.mxf)
* MPEG2-PS, MPEG2-TS, 3GP (.ts, .ps, .3gp, .3gpp, .mpg)
* Vidéo Windows Media (WMV)/ASF (.wmv, .asf)
* AVI (8 bits/10 bits décompressé) (.avi)
* MP4 (.mp4, .m4a, .m4v)
* Enregistrement vidéo numérique Microsoft (DVR-MS) (.dvr-ms)
* Matroska/WebM (.mkv)
* WAVE/WAV (.wav)
* QuickTime (.mov)

## Conseils et restrictions {#limitations-and-tips}

* Actuellement, la taille de fichier maximale pour l’extraction des métadonnées est d’environ 15 Go. Lors du chargement de fichiers très volumineux, l’opération d’extraction des métadonnées peut parfois échouer.

>[!MORELIKETHIS]
>
>* [Traitement des ressources à l’aide des microservices de ressources](asset-microservices-overview.md)
>* [Formats de fichiers pris en hcarge pour le balisage intelligent des ressources textuelles](/help/assets/smart-tags.md#smart-tags-supported-file-formats)

