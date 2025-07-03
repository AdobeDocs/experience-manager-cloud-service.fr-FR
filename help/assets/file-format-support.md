---
title: Formats de fichiers et types MIME pris en charge
description: Formats de fichier et types MIME pris en charge par [!DNL Experience Manager Assets] as a [!DNL Cloud Service].
contentOwner: AG
feature: Asset Management, Renditions
role: User, Admin
exl-id: e848aa77-7829-4adc-8b88-0279791a4525
source-git-commit: 0129bf13301a208b777b61f65623222cdf2b4b18
workflow-type: tm+mt
source-wordcount: '1082'
ht-degree: 94%

---

# Formats de fichiers pris en charge [!DNL Assets]  {#supported-file-formats}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] prend en charge les fonctionnalités de base de gestion de contenu (stockage, gestion des métadonnées en ligne, contrôle de version, chargement et téléchargement, etc.) pour tout fichier binaire, quel que soit son format. [!DNL Adobe Experience Manager Assets] prend en charge un large éventail de formats de fichiers et chaque fonctionnalité de produit prend en charge différents formats.

En outre, [!DNL Experience Manager Assets] offre une prise en charge étendue pour générer des aperçus et des rendus et extraire des métadonnées et du texte en vue de l’indexation en texte intégral. Cette prise en charge étendue est assurée à l’aide de [microservices de ressources](asset-microservices-configure-and-use.md).

Les éléments essentiels concernant la conversion des ressources à l’aide des microservices de ressources sont les suivants :

* [Formats de fichiers Adobe](#adobe-formats) clés générés par les applications et services Adobe, notamment [!DNL Adobe Photoshop], [!DNL Adobe InDesign], [!DNL Adobe Illustrator], [!DNL Adobe XD], [!DNL Adobe Dimension] et [!DNL Adobe Acrobat] ou PDF.
* [Formats de fichiers d’imagerie](#image-formats) clés.
* [Formats de fichiers Camera Raw](#camera-raw-formats) pour un large éventail d’appareils photo, dont Canon, Nikon, Fujifilm, Olympus et d’autres fabricants (optimisés par Adobe Camera Raw).
* [Formats de documents](#document-formats) courants, y compris les formats Microsoft® Office et Open Document.
* Large éventail de formats [vidéo](#video-formats) et [audio](#audio-formats).

Le tableau suivant décrit le niveau de prise en charge pour chaque format.

| Niveau de prise en charge | Description |
| ------------- | --------------------------- |
| ✓ | Pris en charge |
| * | Référez-vous aux remarques ci-dessous. |
| - | Non applicable |

>[!IMPORTANT]
>
>[!DNL Adobe Experience Manager Assets] ne prend en charge que les formats de fichiers répertoriés dans cet article.
>>Certaines fonctionnalités peuvent sembler fonctionner avec d’autres formats, mais ces derniers ne sont pas officiellement pris en charge. Les résultats peuvent être incohérents et les fonctionnalités peuvent ne pas fonctionner comme prévu.
>>Pour garantir des résultats cohérents et fiables, utilisez uniquement les formats pris en charge.

## Formats Adobe {#adobe-formats}

| Format de fichier | Génération de miniatures | Extraction de texte intégral | Extraction de métadonnées | Largeur/Hauteur |
| ----------- | -------------------- | ------------------- | ------------------- | ------------ |
| AI | ✓ | - | ✓ | ✓ |
| COLLAGE | - | - | ✓ | - |
| DN | ✓ | - | ✓ | ✓ |
| SBSAR | ✓ | - | ✓ | ✓ |
| IDEAS | - | - | ✓ | - |
| INDD | ✓ | - | ✓ | ✓ * |
| INDT | - | - | ✓ | - |
| PDF | ✓ | ✓ | ✓ | ✓ |
| PROTO | - | - | ✓ | - |
| PSB | ✓ | - | ✓ | ✓ |
| PSD | ✓ | - | ✓ | ✓ |
| XD | ✓ | - | ✓ | ✓ |

\* Pour les fichiers [!DNL Adobe InDesign] (INDD), la taille des rendus est déterminée par l’aperçu incorporé dans le fichier INDD. Configurez les préférences dans [!DNL InDesign] (**[!UICONTROL Préférences > Gestion des fichiers > Toujours enregistrer les images d’aperçu avec les documents, Taille d’aperçu]**) pour incorporer des rendus plus grands.

## Formats d’image {#image-formats}

| Format de fichier | Génération de miniatures | Extraction de métadonnées | Largeur/Hauteur | Recadrer |
| ----------- | -------------------- | ------------------- | ------------ | -------- |
| BMP | ✓ | - | ✓ | ✓ |
| EPS | ✓ | ✓ | - | - |
| GIF | ✓ | ✓ | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ |
| PNG | ✓ | ✓ | ✓ | ✓ |
| RVB | ✓ | ✓ | ✓ | ✓ |
| RGBA | ✓ | ✓ | ✓ | ✓ |
| SGI™ | ✓ | ✓ | ✓ | ✓ |
| SVG | ✓ | - | ✓ | ✓ |
| TIFF | ✓ | ✓ | ✓ | - |
| WebP | ✓ | ✓ | ✓ | ✓ |

## Formats 3D {#support-3d-formats}

Les formats 3D suivants sont pris en charge.

Cnsultez également la section [Utilisation de ressources 3D dans Dynamic Media](/help/assets/dynamic-media/assets-3d.md).

| Format | Stockage | Contrôle de version | Workflow | Publication | Contrôle d’accès | Aperçu de miniature | Aperçu 3D | Diffusion Dynamic Media |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| DN | ✓ | ✓ | ✓ | - | ✓ | ✓ | - | - |
| gLB | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| gLTF | ✓ | ✓ | ✓ | - | ✓ | - | ✓ | - |
| OBJ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| STL | ✓ | ✓ | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| FBX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | - | - |
| 3DS | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | - | - |
| USDz | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | - | ✓ |
| SBSAR | ✓ | ✓ | ✓ | - | ✓ | ✓ | - | - |

## Formats [!DNL Camera Raw]  {#camera-raw-formats}

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

| Format de fichier | Génération de miniatures | Extraction de texte intégral | Largeur/Hauteur | Gestion des métadonnées | [Ressources connectées](use-assets-across-connected-assets-instances.md) | Aperçu complet du document |
| ----------- | -------------------- | ------------------- | ------------ | ------------------- | ---------------- |--------|
| DOC | - | - | - | ✓ | ✓ | ✓ |
| DOCX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| EPUB | - | ✓ | - | - | - | - |
| HTML | - | ✓ | - | ✓ | ✓ | - |
| ODF | ✓ | ✓ | ✓ | - | - | - |
| ODM | ✓ | ✓ | ✓ | - | - | - |
| ODP | ✓ | ✓ | ✓ | - | - | - |
| ODS | ✓ | ✓ | ✓ | - | - | - |
| ODT | ✓ | ✓ | ✓ | ✓ | ✓ | - |
| OFG | ✓ | ✓ | ✓ | - | - | - |
| PDF | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| PPT | - | - | - | ✓ | ✓ | ✓ |
| PPTX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| PS | - | - | ✓ | - | - | - |
| RTF | - | ✓ | - | ✓ | ✓ | ✓ |
| TXT | ✓ | ✓ | - | ✓ | ✓ | ✓ |
| XLS | - | - | - | ✓ | ✓ | ✓ |
| XLSX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| XML | - | ✓ | - | - | - | - |

## Formats vidéo {#video-formats}

| Format de fichier | Génération de miniatures | Extraction de métadonnées | Largeur/Hauteur | Prévisualisation | Sortie |
| ----------- | -------------------- | ------------------- | ------------ | ------- | ------- |
| 3G2 | - | ✓ | - | - | - |
| 3GP | - | ✓ | - | - | - |
| AVI | ✓ | ✓ | ✓ | ✓ | - |
| DIVX | ✓ | - | ✓ | ✓ | - |
| F4V | ✓ | ✓ | ✓ | ✓ | - |
| FLV | ✓ | ✓ | ✓ | ✓ | - |
| M2T | ✓ | - | ✓ | ✓ | - |
| M2TS | ✓ | - | ✓ | ✓ | - |
| M2V | ✓ | - | ✓ | ✓ | - |
| M4V | ✓ | ✓ | ✓ | ✓ | - |
| MKV | ✓ | - | ✓ | ✓ | - |
| MOV | ✓ | ✓ | ✓ | ✓ | - |
| MP4 | ✓ | ✓ | ✓ | ✓ | ✓ |
| MPEG | ✓ | ✓ | ✓ | ✓ | - |
| MPG | ✓ | ✓ | ✓ | ✓ | - |
| MTS | ✓ | - | ✓ | ✓ | - |
| MXF | ✓ | - | ✓ | ✓ | - |
| OGV | ✓ | - | ✓ | ✓ | - |
| QT | ✓ | - | ✓ | ✓ | - |
| R3D | - | ✓ | ✓ | ✓ | - |
| SWF | ✓ | - | ✓ | ✓ | - |
| WebM | ✓ | - | ✓ | ✓ | ✓ |
| WMV | ✓ | ✓ | ✓ | ✓ | - |

## Formats audio {#audio-formats}

[!DNL Assets] as a [!DNL Cloud Service] offre une prise en charge de l’extraction de métadonnées XMP pour les formats audio AIF, ASF, M4A, MP3, WAV et WMA.

## Formats d’entrée pris en charge pour la transcription audio et vidéo {#audio-video-transcription-formats}

* FLV (avec les codecs H.264 et AAC) (.flv)
* MXF (.mxf)
* MPEG2-PS, MPEG2-TS, 3GP (.ts, .ps, .3gp, .3gpp, .mpg)
* Windows Media Video (WMV) / ASF (.wmv, .asf)
* AVI (8 bits/10 bits non compressés) (.avi)
* MP4 (.mp4, .m4a, .m4v)
* Microsoft® Digital Video Recording (DVR-MS) (.dvr-ms)
* Matroska/WebM (.mkv)
* WAVE/WAV (.wav)
* QuickTime (.mov)

## Conseils et restrictions {#limitations-and-tips}

* Actuellement, la taille de fichier maximale pour l’extraction des métadonnées est d’environ 15 Go. Lors du chargement de ressources volumineuses, l’opération d’extraction des métadonnées peut parfois échouer.

## Dynamic Media : formats vidéo d’entrée pris en charge pour le transcodage {#video-dynamic-media-transcoding}

| Extension de fichier vidéo | Conteneur | Codecs vidéo recommandés | Codecs vidéo non pris en charge |
| --- | --- | --- | --- |
| AVI | A/V Interleave | XVID, DIVX, HDV, MiniDV (DV25), Techsmith Camtasia, Huffyuv, Fraps, Panasonic DVCPro | Indeo3 (IV30), MJPEG, Microsoft® Video 1 (MS-CRAM) |
| FLV, F4V | Adobe Flash | H264/AVC, Flix VP6, H263, Sorenson | SWF (fichiers d’animation vectorielle) |
| M4V | Apple iTunes | H264/AVC | − |
| MKV | Matroska | H264/AVC | − |
| MOV, QT | Apple QuickTime | H264/AVC, Apple ProRes422 et HQ, Sony XDCAM, Sony DVCAM, HDV, Panasonic DVCPro, Apple DV (DV25), Apple PhotoJPEG, Sorenson, Avid DNxHD, Avid AVR | Apple Intermediate, Apple Animation |
| MP4 | MPEG-4 | H264/AVC (tous les profils) | − |
| MPG, VOB, M2V, MP2 | MPEG-2 | MPEG-2 | − |
| MXF ‡ | MXF | Sony XDCAM, MPEG-2, MPEG-4, Panasonic DVCPro | − |
| OGV, OGG | OGG | Theora, VP3, Dirac | − |
| WebM | WebM | Google VP8 | − |
| WMV | Windows Media 9 | WMV3 (v9), WMV2 (v8), WMV1 (v7), GoToMeeting (G2M2, G2M3, G2M4) | Microsoft® Screen (MSS2), Microsoft® Photo Story (WVP2) |

‡ Ce format vidéo n’est pas encore pris en charge pour une utilisation avec les vidéos interactives dans Dynamic Media ou avec lʼannotation dans Experience Manager Assets.

## Dynamic Media - Formats de document pris en charge {#document-support-dynamic-media}

| Format | Charger (format d’entrée) | Créer un paramètre prédéfini d’image (format de sortie) | Prévisualiser un rendu dynamique | Diffuser un rendu dynamique | Télécharger un rendu dynamique |
| ------ | --------------------- | ----------------------------------- | ------------------------- | ------------------------- | -------------------------- |
| AI | ✓ | - | - | - | - |
| INDD | ✓ | - | - | - | - |
| PDF (voir la remarque ci-dessous) | ✓ | ✓ | ✓ | ✓ | ✓ |

>[!NOTE]
>
>Pour les PDF sécurisés, seul le chargement est pris en charge.

## Dynamic Media - Formats d’images pixellisées prises en charge {#image-support-dynamic-media}

| Format | Charger (format d’entrée) | Créer un paramètre prédéfini d’image (format de sortie) | Prévisualiser un rendu dynamique | Diffuser un rendu dynamique | Télécharger un rendu dynamique | Types de visionneuses qui prennent en charge ce format |
|---|:---:|:---:|:---:|:---:|:---:| --- |
| AVIF | − | − | − | ✓ | − | − |
| BMP | ✓ | − | − | − | − | [Image](/help/assets/dynamic-media/image-sets.md), [Supports variés](/help/assets/dynamic-media/mixed-media-sets.md) et [360°](/help/assets/dynamic-media/spin-sets.md) |
| [EPS](/help/assets/dynamic-media/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ | ✓ | − |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ | − |
| HEIC | − | − | − | ✓ | − | − |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ | [Image](/help/assets/dynamic-media/image-sets.md), [Supports variés](/help/assets/dynamic-media/mixed-media-sets.md) et [360°](/help/assets/dynamic-media/spin-sets.md) |
| PICT | ✓ | − | − | − | − | − |
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ | [Image](/help/assets/dynamic-media/image-sets.md), [Supports variés](/help/assets/dynamic-media/mixed-media-sets.md) et [360°](/help/assets/dynamic-media/spin-sets.md) |
| PSD ‡ | ✓ | − | − | − | − | − |
| TIFF | ✓ | ✓ | ✓ | ✓ | ✓ | [Image](/help/assets/dynamic-media/image-sets.md), [Supports variés](/help/assets/dynamic-media/mixed-media-sets.md) et [Rotation](/help/assets/dynamic-media/spin-sets.md) |
| WEBP | − | − | − | ✓ | − | − |

<!-- AVIF, HEIC, and WebP added to table above on March 4, 2024 based on CQDOC-21294 -->

‡ L’image fusionnée est extraite du fichier PSD. Il s’agit d’une image générée par [!DNL Adobe Photoshop] et incluse dans le fichier PSD. Selon les paramètres, l’image fusionnée peut constituer ou non l’image réelle.

## Dynamic Media - Formats d’images pixellisées non prises en charge {#unsupported-raster-image-formats-dm}

Les sous-types suivants de formats de fichiers d’image matricielle *ne sont pas* pris en charge dans [!DNL Dynamic Media] :

* Fichiers PNG dont la taille de bloc IDAT est supérieure à 100 Mo.
* Fichiers PSB.
* Les fichiers PSD avec un espace colorimétrique autre que CMJN, RVB, niveaux de gris ou bitmap ne sont pas pris en charge. Les espaces colorimétriques DuoTone, Lab et indexé ne sont pas pris en charge.
* Fichiers PSD ayant une résolution binaire supérieure à 16.
* Fichiers TIFF contenant des données à virgule flottante.
* Fichiers TIFF dotés d’un espace colorimétrique Lab.

## Dynamic Media - Formats de fichiers 3D pris en charge {#support-3d-formats-dynamic-media}

Voir aussi [Formats 3D pris en charge](/help/assets/file-format-support.md#support-3d-formats)

| Extension de fichier 3D | Format de fichier | Type MIME | Remarques |
|---|---|---|---|
| GLB | Transmission GL binaire | model/gltf-binary | Inclut les matières et les textures dans une seule ressource. |
| OBJ | Fichier d’objet 3D WaveFront | application/x-tgif | |
| STL | Stéréolithographie | application/vnd.ms-pki.stl | |
| USDZ | Fichier zip de description de scène universelle | model/vnd.usdz+zip | *Prise en charge de l’ingestion et de la génération de miniatures, les aperçus 3D ne pas encore pris en charge.* USDZ est un format 3D qui peut être visualisé en mode natif à l’aide de Safari ou iOS. |

**Voir également**

* [Traduire les ressources](translate-assets.md)
* [API HTTP Assets](mac-api-assets.md)
* [Rechercher des ressources](search-assets.md)
* [Ressources connectées](use-assets-across-connected-assets-instances.md)
* [Rapports de ressources](asset-reports.md)
* [Schémas de métadonnées](metadata-schemas.md)
* [Télécharger des ressources](download-assets-from-aem.md)
* [Gestion des métadonnées](manage-metadata.md)
* [Facettes de recherche](search-facets.md)
* [Gérer les collections](manage-collections.md)
* [Import des métadonnées en bloc](metadata-import-export.md)
* [Publier des ressources sur AEM et Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [Traitement des ressources à l’aide des microservices de ressources](asset-microservices-overview.md).
>* [Formats de fichiers pris en charge pour le balisage intelligent des ressources textuelles](/help/assets/smart-tags.md#smart-tags-supported-file-formats)
