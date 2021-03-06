---
title: Configuration du service de transcription
seo-title: Configure transcription service
description: Adobe Experience Manager Assets est configuré avec [!DNL Azure Media Services] qui génère automatiquement une transcription textuelle de la langue parlée dans un fichier audio ou vidéo pris en charge au format WebVTT (Vtt) .
seo-description: When an audio or video asset is processed in Experience Manager Assets, the AI-based transcription service automatically generates the text transcript rendition of the audio or video asset and stores it at the same location within your Assets repository where the original asset resides. The Experience Manager Assets transcription service allows marketers to effectively manage their audio and video content with added discoverability of the text content as well as increase the ROI of these assets by supporting accessibility and localization.
products: SG_EXPERIENCEMANAGER/ASSETS and Experience Manager as a Cloud Service
sub-product: assets
content-type: reference
contentOwner: Vishabh Gupta
topic-tags: Configuration
feature: Asset Management, Configuration
role: Admin
exl-id: e96c8d68-74a6-4d61-82dc-20e619338d4b
source-git-commit: 4edf66127696ce91466811e2ffdcfbbd73f7cc2c
workflow-type: tm+mt
source-wordcount: '1666'
ht-degree: 3%

---

# Configuration de la transcription dans [!DNL Experience Manager Assets] {#configure-transcription-service}

La transcription est le processus de traduction de l’audio d’un fichier audio ou vidéo en texte (voix contre texte) à l’aide de la technologie de reconnaissance vocale.
[!DNL Adobe Experience Manager Assets] est configuré avec [!DNL Azure Media Services] qui génère automatiquement une transcription textuelle de la langue parlée dans un fichier audio ou vidéo pris en charge au format WebVTT (.vtt) . Lorsqu’une ressource audio ou vidéo est traitée dans [!DNL Experience Manager Assets], le service de transcription génère automatiquement le rendu de transcription texte de la ressource audio ou vidéo et la stocke au même emplacement dans votre référentiel Assets où se trouve la ressource d’origine. Le [!DNL Experience Manager Assets] Le service de transcription permet aux marketeurs de gérer efficacement leur contenu audio et vidéo en ajoutant la possibilité de découvrir le contenu texte et en augmentant le retour sur investissement de ces ressources en prenant en charge l’accessibilité et la localisation.

Les transcriptions sont des versions textuelles de contenu parlé ; un exemple est un film que vous visionnez sur n’importe quelle plateforme OTT et qui comprend souvent des sous-titres pour faciliter l’accessibilité ou utiliser le contenu dans d’autres langues. Ou tout fichier audio ou vidéo utilisé à des fins de marketing, d’apprentissage ou de divertissement. Ces expériences commencent par une transcription qui est ensuite formatée ou traduite selon les besoins. La transcription audio ou vidéo est un processus long et sujet aux erreurs lorsqu’il est exécuté manuellement. Il est également difficile d&#39;adapter le processus manuel, compte tenu du besoin croissant de contenu audio-vidéo. [!DNL Experience Manager Assets] utilise la transcription basée sur l’IA d’Azure qui permet un traitement à grande échelle des ressources audio et vidéo et génère les transcriptions textuelles (fichiers .vtt) avec les détails de l’horodatage. Avec Assets, la fonctionnalité de transcription est également prise en charge avec Dynamic Media.

La fonction de transcription est disponible sans frais dans [!DNL Experience Manager Assets]. Toutefois, les administrateurs ont besoin des informations d’identification Azure de l’utilisateur pour configurer le service de transcription dans [!DNL Experience Manager Assets]. Vous pouvez également [obtenir les informations d’identification d’évaluation](https://azure.microsoft.com/en-us/pricing/details/media-services/) directement depuis Microsoft® pour découvrir la fonctionnalité de transcription audio ou vidéo dans Assets.

## Conditions préalables à la transcription {#prerequisites}

1. Une [!DNL Experience Manager Assets as a Cloud Service] instance.
1. Les informations d’identification Azure suivantes sont requises pour la configuration dans [!DNL Experience Manager Assets]:

   * ID client (clé API)
   * Clé secrète client
   * Point de terminaison du client (domaine)
   * Compte multimédia
   * Groupe de ressources
   * ID d’abonnement

   Voir [Documentation Azure](https://docs.microsoft.com/en-us/azure/media-services/latest/access-api-howto?tabs=portal) pour obtenir des informations d’identification pour accéder à l’API Azure Media Services.

1. Assurez-vous que le compte Azure dispose d’un crédit suffisant pour traiter les nouvelles demandes.

## Configuration de la transcription dans [!DNL Experience Manager Assets] {#configure-transcription}

Voici les configurations requises pour activer la fonction de transcription dans [!DNL Experience Manager Assets]:

1. [Configuration d’Azure Media Services](#configure-azure-media-service)
1. [Configuration du profil de traitement pour la transcription audio/vidéo](#configure-processing-profile-for-transcription)


### Configuration d’Azure Media Services {#configure-azure-media-services}

[!DNL Experience Manager Assets] utilise la variable [!DNL Azure Media Services] qui génère automatiquement des transcriptions textuelles de la langue parlée dans une [fichier audio ou vidéo pris en charge](#supported-file-formats-for-transcription) au format WebVTT (.vtt) . Les administrateurs peuvent configurer [!DNL Azure Media Services] in [!DNL Experience Manager Assets] à l’aide des informations d’identification Azure. Le [conditions préalables à la transcription](#transcription-prerequisites) répertorie la variable [!DNL Azure] informations d’identification requises pour la configuration. Si vous n’avez pas [!DNL Azure] compte et informations d’identification, voir [Documentation d’Azure Media Services](https://azure.microsoft.com/en-us/pricing/details/media-services/) pour obtenir des informations d’identification d’évaluation.

![configure-transcription-service](assets/configure-transcription-service.png)

Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Configuration d’Azure Media Services]**. Sélectionnez un dossier (emplacement) dans le rail de gauche, puis cliquez sur le [!UICONTROL Créer] pour configurer la connexion à votre [!DNL Azure] compte . Ce dossier correspond à l’emplacement où votre [!DNL Azure] la configuration du cloud est stockée dans Experience Manager Assets. Saisissez le [!DNL Azure] informations d’identification et cliquez sur **[!UICONTROL Enregistrer et fermer]**.

### Configuration du profil de traitement pour la transcription {#configure-processing-profile}

Une fois que la variable [!DNL Azure Media Services] est configuré dans Experience Manager Assets, l’étape suivante consiste à créer un profil de traitement des ressources pour générer une transcription basée sur l’IA des ressources audio et vidéo. Le profil de traitement basé sur l’IA génère des transcriptions de la variable [ressource audio ou vidéo prise en charge](#supported-file-formats-for-transcription) comme rendu dans Experience Manager Assets et stocke la transcription (fichier .vtt) dans le même dossier que celui où réside la ressource d’origine. Il est donc plus facile pour les utilisateurs de rechercher et de localiser la ressource et son rendu de transcription.

Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Profils de traitement]** et cliquez sur le bouton **[!UICONTROL Créer]** pour créer un profil de traitement basé sur l’IA afin de générer la transcription de vos fichiers audio et vidéo. Par défaut, la page du profil de traitement ne reflète que trois onglets (Image, Vidéo et Personnalisé). Cependant, une **[!UICONTROL IA dédiée au contenu]** est visible si vous avez configuré [!DNL Azure Media Services] dans votre [!DNL Experience Manager Assets] instance. Vérifiez vos [!DNL Azure] informations d’identification si vous ne voyez pas la variable **[!UICONTROL IA dédiée au contenu]** lors de la création d’un profil de traitement.

Dans le **[!UICONTROL IA dédiée au contenu]** , cliquez sur l’onglet **[!UICONTROL Ajouter]** pour configurer la transcription. Ici, vous pouvez inclure et exclure les formats de fichiers (types MIME) pour générer les transcriptions en sélectionnant les types de fichiers dans la liste déroulante. Dans l’illustration suivante, tous les fichiers audio et vidéo pris en charge sont inclus et les fichiers texte sont exclus.

Activez la variable **[!UICONTROL Créer une transcription VTT dans le même répertoire]** pour créer et stocker le rendu de transcription (fichier .vtt) dans le même dossier que celui où réside la ressource d’origine. Les autres rendus sont également générés par le workflow de traitement des ressources de la gestion des actifs numériques par défaut, quel que soit ce paramètre.

![configure-transcription-service](assets/configure-transcription-profile.png)

L’illustration suivante présente un profil vidéo personnalisé créé dans Experience Manager Assets.

![configure-transcription-service](assets/video-processing-profile.png)

Le profil vidéo contient également les configurations personnalisées suivantes. Voir [documentation du profil de traitement](/help/assets/asset-microservices-configure-and-use.md) pour plus d’informations sur la création d’un profil de traitement personnalisé.

![configure-transcription-service](assets/video-processing-profile2.png)

Nous allons maintenant configurer la transcription dans ce profil vidéo. Accédez au **[!UICONTROL IA dédiée au contenu]** et cliquez sur l’onglet **[!UICONTROL Ajouter]** bouton . Incluez tous les fichiers audio et vidéo et excluez les fichiers image et application. Activez la variable **[!UICONTROL Créer une transcription VTT dans le même répertoire]** basculez et enregistrez la configuration.

![configure-transcription-service](assets/video-processing-profile1.png)

Une fois le profil de traitement configuré pour la transcription des fichiers audio et vidéo, vous pouvez appliquer ce profil de traitement aux dossiers à l’aide de l’une des méthodes suivantes :

* Sélection d’une définition de profil de traitement dans **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Profils de traitement]** et utilisez **[!UICONTROL Appliquer le profil au(x) dossier(s)]** action. L’explorateur de contenu vous permet d’accéder à un dossier spécifique, de sélectionner un dossier et de confirmer l’application du profil.
* Sélectionnez un dossier dans l’interface utilisateur d’Assets, puis cliquez sur **[!UICONTROL Propriétés]** pour ouvrir les propriétés du dossier. Cliquez sur le bouton **[!UICONTROL Traitement des ressources]** et sélectionnez le profil de traitement approprié pour le dossier dans l’onglet **[!UICONTROL Profil de traitement]** liste. Pour enregistrer les modifications, cliquez sur **[!UICONTROL Enregistrer et fermer]**.

   ![configure-transcription-service](assets/video-processing-profile3.png)

* Les utilisateurs peuvent sélectionner des dossiers ou des ressources spécifiques dans l’interface utilisateur d’Assets pour appliquer un profil de traitement, puis sélectionner **[!UICONTROL Retraiter les ressources]** des options disponibles dans la partie supérieure.

>[!TIP]
>Un seul profil de traitement peut être appliqué à un dossier.
>
>Une fois qu’un profil de traitement est appliqué à un dossier, toutes les nouvelles ressources chargées (ou mises à jour) dans ce dossier ou dans l’un de ses sous-dossiers sont traitées à l’aide du profil de traitement supplémentaire configuré. Ce dernier s’ajoute au profil par défaut standard.

>[!NOTE]
>
>Un profil de traitement appliqué à un dossier fonctionne pour l’ensemble de l’arborescence. Cependant, il est possible de le remplacer par un autre profil appliqué à un sous-dossier.
>
>Lorsque des ressources sont chargées dans un dossier, Experience Manager communique avec les propriétés du dossier conteneur pour identifier le profil de traitement. Si aucun dossier parent n’est appliqué, un dossier parent dans la hiérarchie est vérifié pour appliquer un profil de traitement.


## Générer la transcription de vos ressources audio ou vidéo {#generate-transcription}

Lors du traitement d’une ressource vidéo, la variable [Profil de traitement basé sur l’IA](#configure-processing-profile-for-transcription) génère automatiquement la transcription (fichier .vtt) en tant que rendu avec la ressource d’origine dans le même dossier.

![configure-transcription-service](assets/transcript1.png)

Vous pouvez également afficher le rendu de transcription en accédant aux Rendus de la ressource vidéo d’origine. Pour accéder au **[!UICONTROL Rendus]** sélectionnez la ressource vidéo d’origine, puis ouvrez le rail de gauche. Vous pouvez constater que le rendu de transcription (fichier .vtt) est visible sous la variable **[!UICONTROL TRANSCRIPTVTT]** head.

![configure-transcription-service](assets/transcript.png)

Vous pouvez télécharger la transcription (fichier texte .vtt) directement à partir du dossier sous la forme d’un rendu de ressource distinct ou à partir de l’ **[!UICONTROL Rendus]** de la ressource d’origine en téléchargeant tous les rendus de la ressource.

Actuellement, Experience Manager ne prend pas en charge l’aperçu de texte intégral ou la modification native des fichiers VTT. Vous pouvez toutefois télécharger le rendu de transcription et utiliser n’importe quel éditeur de texte pour modifier ou vérifier la transcription. La transcription reflète la langue parlée sous forme de texte à l’horodatage donné dans la vidéo avec le degré de confiance (précision) de la transcription.

![configure-transcription-service](assets/transcript-text.png)

## Utilisation de la transcription dans Dynamic Media {#using-transcription-in-dynamic-media}

Si vous avez [Dynamic Media configuré](/help/assets/dynamic-media/config-dm.md) dans votre instance Experience Manager Assets, vous pouvez publier la ressource (fichier audio ou vidéo) et sa transcription (fichier .vtt) dans Dynamic Media. Ce faisant, la ressource d’origine (fichier audio ou vidéo) et son rendu transcrit (fichier .vtt) sont publiés sur Dynamic Media dans le même dossier. L’administrateur Dynamic Media peut [Activation de l’expérience sous-titrage codé CC](/help/assets/dynamic-media/video.md#adding-captions-to-video) pour le fichier audio ou vidéo utilisant le rendu de transcription (fichier .vtt).

Voir également :

* [Tutoriel vidéo sur l’ajout d’un sous-titrage codé CC à Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-overview-feature-video-use.html#add-cc-closed-captioning-to-dynamic-media-video)
* [Publication de vidéos Dynamic Media sur YouTube](/help/assets/dynamic-media/video.md#publishing-videos-to-youtube)

Dans l’illustration suivante, l’URL reflète la partie légende qui fait référence à la transcription (fichier .vtt). La vidéo reflète la langue parlée (texte transcrit) en tant que **[!UICONTROL Sous-titrage codé]** à l’horodatage donné dans la vidéo. L’utilisateur peut activer ou désactiver la légende à l’aide de la fonction **[!UICONTROL CC]** bouton .

![configure-transcription-service](assets/transcript-example.png)

## Formats de fichiers pris en charge pour la transcription {#supported-file-format}

Les formats de fichiers audio et vidéo suivants sont pris en charge pour la transcription :

| Formats audio/vidéo pris en charge | Extensions |
|----|----|
| FLV (avec les codecs H.264 et AAC) | (.flv) |
| MXF | (.mxf) |
| MPEG2-PS, MPEG2-TS, 3GP | (.ts, .ps, .3gp, .3gpp, .mpg) |
| Vidéo Windows Media (WMV)/ASF | (.wmv, .asf) |
| AVI (Décompressé 8 bits/10 bits) | (.avi) |
| MP4 |  (.mp4, .m4a, .m4v) |
| Enregistrement vidéo numérique Microsoft® (DVR-MS) | (.dvr-ms) |
| Matroska/WebM | (.mkv) |
| VAGUE/WAV | (.wav) |
| QuickTime  | (.mov) |


>[!NOTE]
>
>Les ressources (fichiers audio ou vidéo) de type application ne sont pas prises en charge pour la transcription.

## Limites connues {#known-limitations}

* La fonction de transcription est prise en charge pour les vidéos d’une durée maximale de 10 minutes.
* Le titre de la vidéo doit comporter moins de 80 caractères.
* La taille de fichier prise en charge peut aller jusqu’à 15 Go.
* La durée de traitement maximale prise en charge est de 60 minutes.
* Dans un payement [!DNL Azure] vous pouvez télécharger jusqu’à 50 films par minute. Cependant, dans un compte d’évaluation, vous pouvez télécharger jusqu’à cinq films par minute.

## Conseils de dépannage {#troubleshooting}

Connectez-vous à [!DNL Azure Media Services] compte avec les mêmes informations d’identification (que vous avez utilisées pour la configuration) pour vérifier l’état de la requête. Contact [!DNL Azure] prise en charge si votre demande n’est pas traitée correctement.
