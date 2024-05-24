---
title: Vidéo dans Dynamic Media
description: Découvrez comment utiliser la vidéo dans Dynamic Media. Examinez les bonnes pratiques en matière de codage de vidéos, de publication de vidéos dans YouTube, d’affichage de rapports vidéo et d’ajout de marqueurs de chapitre ou de sous-titrage aux vidéos.
contentOwner: Rick Brough
feature: Video Profiles
role: User
exl-id: 0d5fbb3e-b763-415f-8c69-ea36445f882b
source-git-commit: 7a80f68f71475b2bdb6b5559354d7248208a3819
workflow-type: tm+mt
source-wordcount: '9357'
ht-degree: 80%

---

# Vidéo {#video}

Cette section décrit l’utilisation de vidéos dans Dynamic Media.

## Démarrage rapide : vidéos {#quick-start-videos}

Le workflow décrit en détail ci-après vise à vous aider à maîtriser rapidement les opérations liées aux visionneuses de vidéos adaptatives dans Dynamic Media. Chaque étape comporte des renvois à des rubriques contenant de plus amples informations.

>[!NOTE]
>
>Avant d’utiliser des vidéos dans Dynamic Media, vérifiez que l’administrateur ou l’administratrice Adobe Experience Manager a activé et configuré les Cloud Services Dynamic Media.
>
>* Voir [Configuration des Cloud Services Dynamic Media](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services) dans Configuration de Dynamic Media et [Dépannage de Dynamic Media](/help/assets/dynamic-media/troubleshoot-dm.md).
>

1. **Chargez les vidéos Dynamic Media** en procédant comme suit :

   * Créez votre propre profil de codage vidéo. Vous pouvez également utiliser le profil _Codage vidéo adaptif_ prédéfini fourni avec Dynamic Media.

      * [Création d’un profil de codage vidéo](/help/assets/dynamic-media/video-profiles.md#creating-a-video-encoding-profile-for-adaptive-streaming).
      * En savoir plus sur les [bonnes pratiques relatives au codage vidéo](#best-practices-for-encoding-videos).

   * Associez le profil de traitement vidéo à un ou plusieurs dossiers dans lequel vous allez charger les vidéos issues de sources originales.

      * [Application d’un profil vidéo à des dossiers](/help/assets/dynamic-media/video-profiles.md#applying-a-video-profile-to-folders).
      * En savoir plus sur l’[organisation des ressources numériques](/help/assets/organize-assets.md).

   * Chargez les vidéos issues de sources originales dans les dossiers. Lorsque vous ajoutez des vidéos au dossier, elles sont codées selon le profil de traitement vidéo affecté au dossier.

      * Dynamic Media prend principalement en charge les vidéos de forme courte avec une durée maximale de 30 minutes et une résolution minimale supérieure à 25 x 25.
      * Vous pouvez charger des fichiers vidéo d’une taille de 15 Go chacun au maximum.
      * [Chargement des vidéos](/help/assets/manage-video-assets.md#upload-and-preview-video-assets).
      * En savoir plus sur les [formats de fichiers d’entrée pris en charge](/help/assets/file-format-support.md).

   * Surveillez [la progression du codage vidéo](#monitoring-video-encoding-and-youtube-publishing-progress) depuis la vue de la ressource ou du workflow.

1. Pour **gérer les vidéos Dynamic Media**, effectuez l’une des opérations suivantes :

   * Organisez, parcourez et recherchez des ressources vidéo

      * [Organisation des ressources numériques](/help/assets/organize-assets.md)
      * [Recherche de ressources vidéo](/help/assets/search-assets.md#custompredicates) ou [Recherche de ressources](/help/assets/manage-digital-assets.md#search-assets)

   * Prévisualisez et publiez des ressources vidéo

      * Affichez la vidéo source et les rendus codés de la vidéo avec les miniatures associées :
        [Prévisualisation de vidéos](/help/assets/manage-video-assets.md#upload-and-preview-video-assets) ou [Prévisualisation de ressources](/help/assets/dynamic-media/previewing-assets.md)
        [Gestion des rendus vidéo](/help/assets/manage-digital-assets.md#managing-renditions)

      * [Gestion des paramètres prédéfinis de visionneuse](/help/assets/dynamic-media/managing-viewer-presets.md)
      * [Publier les ressources](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md)

   * Utilisation des métadonnées vidéo

      * Modifiez les propriétés vidéo telles que le titre, la description, les balises et les champs de métadonnées personnalisées :
        [Modification des propriétés vidéo](/help/assets/manage-digital-assets.md#editing-properties)

      * [Gestion des métadonnées des ressources numériques](/help/assets/manage-metadata.md)
      * [Schémas de métadonnées](/help/assets/metadata-schemas.md)

   * Examen, approbation et annotation des vidéos, et conservation le contrôle total des versions

      * [Annotation de vidéos](/help/assets/manage-video-assets.md#annotate-video-assets) ou [Annotation de ressources](/help/assets/manage-digital-assets.md#annotating)

      * [Création d’une version](/help/assets/manage-digital-assets.md#asset-versioning)
      * [Démarrage d’un workflow sur une ressource](/help/assets/manage-digital-assets.md#starting-a-workflow-on-an-asset)

      * [Examen des ressources des dossiers](/help/assets/bulk-approval.md)
      * [Projets](/help/sites-cloud/authoring/projects/overview.md)

1. Pour **publier les vidéos Dynamic Media**, effectuez l’une des opérations suivantes :

   * Si vous utilisez Experience Manager en tant que système de gestion de contenu web (WCM), vous pouvez ajouter directement des vidéos à vos pages web.

      * [Ajout de vidéos à des pages web](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).

   * Si vous utilisez un système de gestion de contenu web tiers, vous pouvez lier ou incorporer des vidéos dans vos pages web.

      * Intégrez une vidéo à l’aide d’une URL :
        [Liaison d’URL à votre application web](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md).

      * Intégrez une vidéo à l’aide du code intégré dans la page web :
        [Incorporation de la visionneuse de vidéos dans une page web](/help/assets/dynamic-media/embed-code.md).

   * [Génération de rapports vidéo](#viewing-video-reports).

   * [Ajout de sous-titres à une vidéo](#adding-captions-to-video).

## Utilisation de vidéo dans Dynamic Media {#working-with-video-in-dynamic-media}

Video in Dynamic Media est une solution complète qui facilite la publication de vidéos adaptatives haute qualité pour la diffusion sur plusieurs écrans, notamment les postes de travail, les tablettes et les appareils mobiles. Une visionneuse de vidéos adaptative regroupe les versions d’une même vidéo codées dans des débits et des formats différents, par exemple 400 kbit/s, 800 kbit/s et 1 000 kbit/s. Le poste de travail ou l’appareil mobile détecte la bande passante disponible.

Par exemple, sur un appareil mobile iOS, il détecte une bande passante telle que 3G, 4G ou une connexion Wi-Fi, puis sélectionne automatiquement la vidéo codée selon le débit correspondant parmi ceux disponibles dans la visionneuse de vidéos adaptative. La vidéo est diffusée en continu sur les postes de travail, les appareils mobiles ou les tablettes.

En outre, la qualité de la vidéo s’adapte de manière automatique et dynamique aux fluctuations des conditions du réseau sur le poste de travail ou sur l’appareil mobile. De même, si un client ou une cliente passe en mode plein écran sur un bureau, la visionneuse de vidéos adaptative réagit en utilisant une meilleure résolution, améliorant ainsi l’expérience de visionnage. L’utilisation des visionneuses de vidéos adaptatives offre une lecture fluide et de qualité aux clients et clientes qui lisent des vidéos Dynamic Media sur plusieurs écrans et appareils.

La logique utilisée par un lecteur vidéo pour déterminer la vidéo codée à lire ou à sélectionner au cours de la lecture repose sur l’algorithme suivant :

1. Le lecteur vidéo charge le fragment vidéo initial en fonction du débit le plus proche de la valeur définie pour le « débit initial » dans le lecteur.
1. Le lecteur vidéo change en fonction des modifications de la vitesse de bande passante à l’aide des critères suivants :

   1. Le lecteur sélectionne la bande passante la plus élevée, inférieure ou égale à la bande passante estimée.
   1. Le lecteur prend uniquement en compte 80 % de la bande passante disponible. Cependant, s’il change, il est préférable que ce taux soit seulement de 70 % pour éviter toute surestimation et que le lecteur ne repasse au taux précédent.

Pour obtenir des informations techniques détaillées sur l’algorithme, consultez la page [https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/httplive/LiveSession.cpp](https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/httplive/LiveSession.cpp)

Pour la gestion des visionneuses de vidéos à débit adaptatif et uniques, les fonctions suivantes sont prises en charge :

* Téléchargement de vidéos en différents formats vidéo et audio pris en charge et codage vidéo au format MP4 H.264 pour la lecture sur plusieurs écrans. Vous pouvez utiliser des paramètres prédéfinis de vidéo adaptative, des paramètres prédéfinis de codage vidéo unique ou personnaliser votre propre codage pour contrôler la qualité et la taille de la vidéo.

   * Lorsqu’une visionneuse de vidéos adaptative est générée, elle comprend des vidéos MP4.
   * **Remarque** : Les vidéos originales/sources ne sont pas ajoutées à la visionneuse de vidéos adaptative.

* Sous-titrage vidéo dans toutes les visionneuses de vidéos HTML5.
* Organisez, parcourez et recherchez des vidéos avec une prise en charge complète des métadonnées pour une gestion efficace des ressources vidéo.
* Diffuser des visionneuses de vidéos adaptatives sur le web et sur les postes de travail, les tablettes et les appareils mobiles.

La diffusion de vidéo adaptative en continu est prise en charge sur différentes plateformes iOS. Voir [Guide de référence des visionneuses de médias dynamiques](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/c-html5-video-reference.html?lang=fr).

<!-- OUTDATED 2/28/22 BASED ON CQDOC-18692 Dynamic Media supports mobile video playback for MP4 H.264 video. You can find BlackBerry&reg; devices that support this video format at the following: [Supported video formats on BlackBerry&reg;](https://support.blackberry.com/kb/articleDetail?ArticleNumber=000005482).

OUTDATED 2/28/22 BASED ON CQDOC-18692 You can find Windows&reg; devices that support this video format at the following [Supported video formats on Windows&reg; Phone](https://docs.microsoft.com/en-us/windows/uwp/audio-video-camera/supported-codecs). -->

* Lecture de la vidéo à l’aide des paramètres prédéfinis de la visionneuse Dynamic Media Video, tels que :

   * Visionneuses de vidéos uniques.
   * des visionneuses de médias mixtes combinant du contenu vidéo et des images.

* Configurez les lecteurs vidéo pour répondre à vos besoins en matière de branding.
* Intégrez la vidéo à votre site Web, site mobile ou application mobile à l’aide d’une simple URL ou d’un code intégré.

Voir l’exemple [Lecture de vidéo dynamique](https://s7d9.scene7.com/s7/uvideo.jsp?asset=GeoRetail/Mop_AVS&amp;config=GeoRetail/Universal_Video1&amp;stageSize=640,480).

Voir aussi [Visionneuses pour Experience Manager Assets et Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/c-html5-s7-aem-asset-viewers.html?lang=fr#viewers-aem-assets-dmc) et [Visionneuses pour Experience Manager Assets uniquement](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers.html?lang=fr#viewers-for-aem-assets-only) dans le [Guide de référence des visionneuses de médias dynamiques](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources.html?lang=fr).

## Bonne pratique : Utilisation de la visionneuse de vidéos HTML5 {#best-practice-using-the-html-video-viewer}

Les paramètres prédéfinis de la visionneuse de vidéos HTML5 Dynamic Media sont des lecteurs vidéo fiables. Utilisez-les pour éviter la plupart des problèmes courants liés à la lecture de vidéos HTML5, ainsi que les problèmes liés aux appareils mobiles. Par exemple, une absence de diffusion en continu à débit adaptatif et une limitation de la portée du navigateur de bureau.

En ce qui concerne la conception du lecteur, vous pouvez concevoir les fonctionnalités du lecteur vidéo à l’aide d’outils de développement web standard. Par exemple, vous pouvez concevoir les boutons, les commandes et l’arrière-plan personnalisé de l’image d’affiche en utilisant HTML5 et CSS pour vous aider à atteindre vos clients et vos clientes à l’aide d’une apparence personnalisée.

En ce qui concerne la relecture, la visionneuse détecte automatiquement les fonctionnalités vidéo du navigateur. Elle traite ensuite la vidéo en utilisant HLS ou DASH, également connus sous le nom de diffusion en continu de vidéo adaptative. Si ces méthodes de distribution n’existent pas, la diffusion progressive HTML5 est utilisée à la place.

>[!NOTE]
>
>Pour utiliser DASH pour vos vidéos, il doit d’abord être activé par le support technique d’Adobe sur votre compte. Voir [Activer DASH sur votre compte](#enable-dash).

Vous pouvez combiner dans un unique lecteur la possibilité de concevoir les composants de lecture à l’aide de HTML5 et CSS. Il peut disposer de la relecture incorporée et utiliser la diffusion en continu adaptative et progressive en fonction des fonctionnalités du navigateur. Grâce à cette fonctionnalité, vous pouvez étendre la portée de votre contenu multimédia aux utilisateurs d’ordinateur et de mobile et garantir une expérience vidéo fluide.

Consultez également [Visionneuses pour Experience Manager Assets uniquement](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers.html?lang=fr#viewers-for-aem-assets-only) dans le [Guide de référence des visionneuses de médias dynamiques](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources.html?lang=fr).


### Lecture vidéo sur les ordinateurs de bureau et les appareils mobiles à l’aide de la visionneuse de vidéos HTML5 {#playback-of-video-on-desktop-computers-and-mobile-devices-using-the-html-video-viewer}

Pour la diffusion en continu de la vidéo adaptative sur un poste de travail et un appareil mobile, les vidéos utilisées pour le changement de débit reposent sur toutes les vidéos MP4 dans la visionneuse de vidéo adaptative.

La lecture vidéo se produit à l’aide d’un téléchargement vidéo HLS, DASH ou progressive. Dans les versions antérieures d’Experience Manager, telles que 6.0, 6.1 et 6.2, les vidéos étaient diffusées via HTTP.

Toutefois, dans la version 6.3 et les versions ultérieures d’Experience Manager, les vidéos sont diffusées en continu via HTTPS (c’est-à-dire, HLS ou DASH), car l’URL du service de la passerelle DM utilise toujours HTTPS également. Il n’y a aucun impact pour le client dans ce comportement par défaut. Autrement dit, la diffusion en continu de vidéo s’effectuera tout de même via HTTPS, à moins qu’elle ne soit pas prise en charge par le navigateur Consultez le tableau suivant.

Par conséquent :

* Si vous disposez d’un site Web HTTPS avec streaming vidéo HTTPS, le streaming est correct.
* Si vous disposez d’un site Web HTTP avec streaming vidéo HTTPS, le streaming est correct et il n’y a aucun problème de contenu mixte à partir du navigateur Web.

DASH est la norme internationale et HLS est une norme Apple. Les deux sont utilisés pour la diffusion en continu de vidéo adaptative. De plus, les deux technologies ajustent automatiquement la relecture en fonction de la capacité de bande passante du réseau. Elle permet aussi au client ou à la cliente de « rechercher » n’importe quel point de la vidéo sans avoir à attendre que le reste de la vidéo soit téléchargé.

La vidéo progressive est fournie grâce au téléchargement et à l’enregistrement de la vidéo en local sur le système du poste de travail ou de l’appareil mobile de l’utilisateur ou de l’utilisatrice.

Le tableau ci-dessous décrit l’appareil, le navigateur et la méthode de lecture des vidéos sur les ordinateurs de bureau et les appareils mobiles à l’aide de la [visionneuse de vidéos HTML5 Dynamic Media](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video.html?lang=fr#interactive-video).

<table>
 <tbody>
  <tr>
   <td><strong>Appareil</strong></td>
   <td><strong>Navigateur</strong></td>
   <td><strong>Mode lecture vidéo</strong></td>
  </tr>
  <tr>
   <td>Poste de travail</td>
   <td>Internet Explorer 9 et 10</td>
   <td>Téléchargement progressif.</td>
  </tr>
  <tr>
   <td>Poste de travail</td>
   <td>Internet Explorer 11+</td>
   <td>Sous Windows® 8 et Windows® 10 – Forcer l’utilisation de HTTPS chaque fois que DASH ou HLS est demandé. Limites connues : HTTP sur DASH ou HLS ne fonctionne pas avec cette combinaison de navigateur/système d’exploitation<br /> <br /> Sous Windows® 7 – Téléchargement progressif. Utilise la logique standard pour sélectionner le protocole HTTP ou HTTPS.</td>
  </tr>
  <tr>
   <td>Poste de travail</td>
   <td>Firefox 23-44</td>
   <td>Téléchargement progressif.</td>
  </tr>
  <tr>
   <td>Poste de travail</td>
   <td>Firefox 45 ou version ultérieure</td>
   <td>Diffusion en continu à débit adaptatif HLS ou DASH*</td>
  </tr>
  <tr>
   <td>Poste de travail</td>
   <td>Chrome</td>
   <td>Diffusion en continu à débit adaptatif HLS ou DASH*</td>
  </tr>
  <tr>
   <td>Poste de travail</td>
   <td>Safari (Mac)</td>
   <td>Streaming à débit adaptatif HLS</td>
  </tr>
  <tr>
   <td>Mobile</td>
   <td>Chrome (Android™ 6 ou version antérieure)</td>
   <td>Téléchargement progressif.</td>
  </tr>
  <tr>
   <td>Mobile</td>
   <td>Chrome (Android™ 7 ou version ultérieure)</td>
   <td>Diffusion en continu à débit adaptatif HLS ou DASH*/td&gt;
  </tr>
  <tr>
   <td>Mobile</td>
   <td>Android™ (navigateur par défaut)</td>
   <td>Téléchargement progressif.</td>
  </tr>
  <tr>
   <td>Mobile</td>
   <td>Safari (iOS)</td>
   <td>Streaming à débit adaptatif HLS</td>
  </tr>
  <tr>
   <td>Mobile</td>
   <td>Chrome (iOS)</td>
   <td>Streaming à débit adaptatif HLS</td>
  </tr>
 </tbody>
</table>

>[!IMPORTANT]
>
>*Pour utiliser le DASH pour vos vidéos, il doit d’abord être activé par le support technique d’Adobe sur votre compte. Voir [Activer DASH sur votre compte](#enable-dash).

<!--  THIS LINE WAS REMOVED FROM THE TABLE ABOVE ON FEB 28, 2022 BASED ON CQDOC 18692 -RSB <tr>
   <td>Mobile</td>
   <td>BlackBerry&reg;</td>
   <td>HLS or DASH</td>
  </tr>
 -->

## Architecture de la solution vidéo Dynamic Media {#architecture-of-dynamic-media-video-solution}

Le graphique suivant montre le workflow global de création de vidéos qui sont chargées et codées par le biais de DMGateway (dans le mode Hybride Dynamic Media) et mises à disposition pour une consommation publique.

![chlimage_1-427](assets/chlimage_1-427.png)

## Architecture de publication hybride des vidéos {#hybrid-publishing-architecture-for-videos}

![chlimage_1-428](assets/chlimage_1-428.png)

## Bonnes pratiques en matière de codage de vidéos {#best-practices-for-encoding-videos}

Le processus **Vidéo de codage de média dynamique** encode la vidéo si vous avez activé Dynamic Media et configuré les Cloud Services vidéo. Ce workflow capture l’historique de traitement des workflows et les informations d’échec. Si vous avez activé Dynamic Media et configuré les services cloud vidéo, le workflow **[!UICONTROL Vidéo de codage de média dynamique]** prend automatiquement effet lorsque vous chargez une vidéo. (Si vous n’utilisez pas Dynamic Media, le workflow **[!UICONTROL Ressource de mise à jour DAM]** prend effet.)

Vous trouverez ci-dessous quelques conseils sur les bonnes pratiques de codage des fichiers source vidéo.

<!-- For advice about video encoding, see the following:

* [Streaming 101: The Basics — Codecs, Bandwidth, Data Rate, and Resolution](https://www.adobe.com/go/learn_s7_streaming101_en).
* [Video Encoding Basics](https://www.adobe.com/go/learn_s7_encoding_en). -->

### Fichiers vidéo source {#source-video-files}

Lorsque vous codez un fichier vidéo, utilisez un fichier vidéo source de la plus haute qualité possible. Évitez d’utiliser des fichiers vidéo déjà codés, car ces fichiers sont déjà compressés, et un codage supplémentaire crée une vidéo de qualité inférieure.

* Dynamic Media prend principalement en charge les vidéos de forme courte avec une durée maximale de 30 minutes et une résolution minimale supérieure à 25 x 25.
* Vous pouvez charger des fichiers vidéo de source principale d’une taille de 15 Go chacun au maximum.

Le tableau ci-dessous décrit la taille recommandée, le format et le débit minimal requis pour vos fichiers vidéo sources au moment de leur codage :

| Taille | Format | Débit minimal |
|--- |--- |--- |
| 1 024 x 768 | 4:3 | 4 500 Kbit/s pour la plupart des vidéos. |
| 1 280 x 720 | 16:9 | 3 000 à 6 000 Kbit/s, selon la quantité de mouvement dans la vidéo. |
| 1 920 x 1 080 | 16:9 | 6 000 à 8 000 kbit/s, selon la quantité de mouvement dans la vidéo. |

### Obtention des métadonnées d’un fichier {#obtaining-a-file-s-metadata}

Vous pouvez obtenir les métadonnées d’un fichier en les affichant à l’aide d’un outil d’édition pour vidéos ou d’une application d’extraction de métadonnées. Vous trouverez ci-après les instructions d’utilisation de MediaInfo, une application tierce permettant d’extraire les métadonnées d’un fichier vidéo :

1. Accédez à [Téléchargement MediaInfo](https://mediaarea.net/fr/MediaInfo/Download).
1. Sélectionnez et téléchargez le programme d’installation pour la version avec l’interface graphique utilisateur, puis suivez les instructions d’installation.
1. Après l’installation, cliquez avec le bouton droit sur le fichier vidéo (Windows® uniquement) et sélectionnez MediaInfo, ou bien ouvrez MediaInfo et faites glisser votre fichier vidéo dans l’application. Toutes les métadonnées de votre fichier vidéo, telles que sa largeur, sa hauteur et le nombre d’images par seconde, sont alors visibles à l’écran.

### Format {#aspect-ratio}

Lorsque vous choisissez ou créez un paramètre prédéfini de codage vidéo pour votre fichier vidéo issu de sources originales, assurez-vous que le paramètre prédéfini indique le même format que le fichier vidéo issu de sources originales. Le format fait référence au rapport largeur/hauteur de la vidéo.

Pour déterminer le format d’un fichier vidéo, récupérez les métadonnées de ce fichier et notez les valeurs de largeur et de hauteur (voir Obtention des métadonnées d’un fichier ci-dessus). Utilisez ensuite cette formule pour déterminer le format :

largeur/hauteur = format

Le tableau suivant décrit comment les résultats de la formule se traduisent par des choix de format courants :

| Résultat de la formule | Format |
|--- |--- |
| 1,33 | 4:3 |
| 0,75 | 3:4 |
| 1,78 | 16:9 |
| 0,56 | 9:16 |

Par exemple, une vidéo qui a une largeur de 1440 pour une hauteur de 1080 a un format de 1440/1080, soit 1,33. Dans ce cas, vous choisissez un paramètre prédéfini de codage vidéo avec un format de 4:3 pour le codage du fichier vidéo.

### Débit binaire {#bitrate}

Le débit correspond à la quantité de données encodées pour produire une seule seconde de lecture vidéo. Le débit de données est mesuré en kilobits par seconde (kbit/s).

>[!NOTE]
>
>Du fait que tous les codecs utilisent la compression avec perte, le débit de données est le facteur le plus important de la qualité vidéo. Quand vous utilisez la compression avec perte, plus vous compressez la vidéo, plus la qualité de l’image se dégrade. Pour cette raison, toutes les autres caractéristiques étant égales (résolution, débit d’image et codec), plus le débit est faible, plus la qualité du fichier compressé est faible.

Lors de la sélection d’une vitesse de transmission, vous pouvez choisir deux types :

* **[!UICONTROL Encodage à débit constant]** (CBR) : pendant l’encodage CBR, le débit ou le nombre de bits par seconde est conservé pendant tout le processus d’encodage. L’encodage CBR maintient le débit défini selon votre configuration sur l’intégralité de la vidéo. En outre, le codage CBR n’optimise pas la qualité des fichiers multimédias, mais économise de l’espace de stockage.
Utilisez le codage CBR si votre vidéo présente globalement un niveau de mouvement similaire. Le codage CBR est le plus souvent utilisé pour diffuser le contenu vidéo en continu. Voir également [Utilisation de paramètres de codage vidéo personnalisés](/help/assets/dynamic-media/video-profiles.md#using-custom-added-video-encoding-parameters).

* **[!UICONTROL Codage à débit variable]** (VBR) - le codage VBR règle le débit en le diminuant et en l’augmentant selon la limite supérieure que vous avez définie, en fonction des données demandées par le compresseur. Cette fonctionnalité implique que lors d’un processus de codage VBR, le débit du fichier multimédia augmente ou diminue de manière dynamique en fonction des besoins du débit de fichiers multimédias.
Le VBR prend plus de temps au codage, mais garantit de meilleurs résultats, avec une qualité de fichier multimédia supérieure. Le codage VBR est couramment utilisé pour la diffusion http progressive de contenu vidéo.

Dans quels cas utilisez-vous le VBR ou le CBR ?
Lorsque vous devez choisir entre VBR et CBR, il est presque toujours recommandé d’utiliser le VBR pour vos fichiers multimédias. Le VBR vous garantit des fichiers de meilleure qualité à des débits compétitifs. Lorsque vous utilisez le VBR, assurez-vous d’utiliser le codage à deux passages, et définissez le débit maximal afin qu’il soit 1,5 fois supérieur au débit vidéo cible.

Lorsque vous choisissez un paramètre prédéfini de codage vidéo, veillez à tenir compte de la vitesse de connexion de l’utilisateur cible. Choisissez un paramètre prédéfini avec un débit de données correspondant à 80 % de cette vitesse. Par exemple, si la vitesse de connexion de l’utilisateur cible est de 1 000 Kbit/s, le meilleur paramètre prédéfini est celui avec un débit de données vidéo de 800 Kbit/s.

Ce tableau décrit le débit de données associé à des vitesses de connexion courantes.

| Vitesse (kbit/s) | Type de connexion |
|--- |--- |
| 256 | Connexion d’accès à distance. |
| 800 | Connexion mobile standard. Pour cette connexion, visez un débit de données de 400 à 800 kbit/s pour les expériences 3G. |
| 2000 | Connexion haut débit standard de bureau. Pour cette connexion, visez un débit de données de 800 à 2 000 kbit/s, bien qu’un débit de 1 200 à 1 500 kbit/s convienne à la plupart des cibles. |
| 5000 | Connexion haut débit standard. Il est déconseillé de coder dans la plage supérieure, car la diffusion vidéo à cette vitesse n’est pas disponible pour la plupart des consommateurs et des consommatrices. |

### Résolution {#resolution}

La **résolution** décrit la hauteur et la largeur d’un fichier vidéo, exprimée en pixels. La plupart des vidéos sources sont stockées à une résolution élevée (par exemple, 1 920 x 1 080). À des fins de diffusion en flux continu, la vidéo source est compressée à une résolution inférieure (640 x 480, voire moins).

La résolution et le débit de données sont deux facteurs étroitement liés qui déterminent la qualité de la vidéo. Pour maintenir la même qualité vidéo, plus il y a de pixels dans un fichier vidéo (plus la résolution est élevée), plus le débit de données doit être élevé. Prenons l’exemple du nombre de pixels par image dans un fichier vidéo de résolution 320 x 240 et dans un autre de résolution 640 x 480 :

| Résolution | Pixels par image |
|--- |--- |
| 320 x 240 | 76 800 |
| 640 x 480 | 307 200 |

Le fichier de résolution 640 x 480 a quatre fois plus de pixels par image. Pour obtenir le même débit de données pour ces deux exemples de résolution, vous compressez quatre fois le fichier 640 x 480, ce qui peut réduire la qualité de la vidéo. Par conséquent, un débit de données vidéo de 250 kbit/s produit un affichage de haute qualité à une résolution de 320 x 240 pixels, mais pas à une résolution de 640 x 480 pixels.

En général, plus le débit de données que vous utilisez est élevé, plus la qualité de votre vidéo est bonne, et plus vous utilisez une résolution élevée, plus de débit de données dont vous avez besoin est élevé pour conserver la qualité de visionnage (en comparaison avec des résolutions plus basses).

Du fait que la résolution et le débit de données sont liés, vous avez le choix entre deux options lors du codage vidéo :

* Choisir un débit de données puis, en fonction de ce paramètre, coder à la résolution la plus haute pour obtenir une vidéo de bonne qualité.
* Choisir une résolution, puis coder au débit de données nécessaire pour que la qualité vidéo soit optimale à la résolution choisie.

Lorsque vous choisissez (ou créez) un paramètre prédéfini de codage vidéo pour votre fichier vidéo source original, utilisez ce tableau pour choisir la résolution cible appropriée :

| Résolution | Hauteur (pixels) | Taille de l’écran |
|--- |--- |--- |
| 240p | 240 | Tout petit écran |
| 300p | 300 | Petit écran (appareils mobiles, le plus souvent) |
| 360p | 360 | Petit écran |
| 480p | 480 | Écran moyen |
| 720p | 720 | Grand écran |
| 1 080p | 1080 | Grand écran haute définition |

### Images par seconde  {#fps-frames-per-second}

Aux États-Unis et au Japon, la plupart des vidéos sont tournées à 29,97 images par seconde (ips). En revanche, en Europe, la plupart des vidéos sont tournées à 25 ips. Un film est tourné à 24 ips.

Choisissez un paramètre prédéfini de codage vidéo correspondant au nombre d’images par seconde de votre vidéo issue de sources originales. Par exemple, si le débit est de 25 ips pour la vidéo issue de sources originales, choisissez un paramètre prédéfini de 25 ips pour le codage. Par défaut, tous les codages personnalisés utilisent le nombre d’images par seconde de la vidéo issue de sources originales. C’est pourquoi il est inutile d’indiquer le nombre d’images par seconde lorsque vous créez un paramètre prédéfini de codage vidéo.

### Dimensions du codage vidéo {#video-encoding-dimensions}

Pour des résultats optimaux, sélectionnez des dimensions de codage de manière à ce que la vidéo source soit un multiple entier de toutes vos vidéos codées.

Pour ce faire, il suffit de diviser la largeur de la source par la largeur codée pour obtenir le rapport de largeur, Ensuite, vous divisez la hauteur source par la hauteur codée pour obtenir le rapport de hauteur.

Si le résultat est un nombre entier, cela signifie que la mise à l’échelle de la vidéo est optimale. Si le résultat n’est pas un nombre entier, la qualité vidéo s’en ressentira en raison de la présence d’artefacts vidéo (pixels résiduels). Cet effet est plus visible lorsque la vidéo comporte du texte.

Par exemple, supposons que la vidéo source soit en 1 920 x 1 080. Dans le tableau suivant, les trois vidéos codées fournissent les paramètres de codage optimaux à utiliser.

| Type de vidéo | Largeur x Hauteur | Rapport largeur | Rapport de hauteur |
|--- |--- |--- |--- |
| Source | 1 920 x 1 080 | 1 | 1 |
| Codé | 960 x 540 | 2 | 2 |
| Codé | 640 x 360 | 3 | 3 |
| Codé | 480 x 270 | 4 | 4 |

### Format de fichier vidéo codé {#encoded-video-file-format}

Dynamic Media recommande d’utiliser les paramètres prédéfinis MP4 H.264 de codage vidéo. Comme les fichiers MP4 utilisent le codec vidéo H.264, une vidéo de haute qualité est obtenue, mais avec une taille de fichier compressée.

## Affichage des rapports vidéo {#viewing-video-reports}

>[!NOTE]
>
>Les rapports vidéo sont disponibles uniquement lorsque vous exécutez Dynamic Media en mode Hybride.

Les rapports vidéo affichent plusieurs mesures agrégées sur une période spécifiée pour vous permettre de vérifier que les vidéos individuelles et agrégées *publiées* ont les performances attendues. Les données des mesures principales suivantes sont agrégées pour toutes les vidéos publiées sur l’ensemble de votre site web :

* Lancements de vidéo
* Taux d’achèvement
* Durée moyenne de visionnage
* Durée totale de visionnage
* Vidéos par visite

Un tableau de toutes les vidéos *publiées* est également fourni pour vous permettre de suivre les vidéos les plus visionnées sur votre site web en fonction du total des lancements de vidéo.

Lorsque vous sélectionnez le nom d’une vidéo dans la liste, le rapport sur la rétention de l’audience (taux de déperdition) de la vidéo s’affiche sous la forme d’un graphique linéaire. Le graphique présente le nombre de vues à un moment donné de la lecture vidéo. Lorsque vous lisez la vidéo, la barre verticale effectue un suivi en synchronisation avec l’indicateur temporel du lecteur. Les baisses des données du graphique linéaire indiquent le moment où votre audience perd son intérêt.

Si la vidéo a été codée en dehors d’Adobe Experience Manager Dynamic Media, le graphique sur la rétention de l’audience (taux de déperdition) et les données de pourcentage de lecture du tableau ne sont pas disponibles.

>[!NOTE]
>
>Le suivi et les données de rapport reposent exclusivement sur l’utilisation du lecteur vidéo Dynamic Media et du paramètre prédéfini du lecteur vidéo associé. Vous ne pouvez donc pas effectuer le suivi et créer de rapports sur des vidéos qui sont lues par d’autres lecteurs vidéo.

Par défaut, la première fois que vous utilisez l’option Rapports vidéo, le rapport affiche des données vidéo du premier jour du mois en cours jusqu’à la date du mois en cours. Vous pouvez toutefois remplacer la période par défaut par la vôtre. La prochaine fois que vous utiliserez l’option Rapports vidéo, la période que vous avez spécifiée sera utilisée.

Pour que les rapports vidéo fonctionnent correctement, un identifiant de suite de rapports est automatiquement créé lors de la configuration des Cloud Services Dynamic Media. Dans le même temps, l’identifiant de suite de rapports est transmis au serveur de publication pour qu’il soit disponible pour la fonctionnalité de copie d’URL lors de la prévisualisation de ressources. Cette fonctionnalité nécessite toutefois que le serveur de publication soit déjà configuré. Si le serveur de publication n’est pas configuré, vous pouvez tout de même lancer la publication pour afficher le rapport vidéo. Cependant, vous devez revenir à la configuration du cloud Dynamic Media et sélectionner **[!UICONTROL OK]**.

**Pour afficher un rapport vidéo, procédez comme suit :**

1. Dans le coin supérieur gauche d’Experience Manager, sélectionnez le logo Experience Manager, puis, dans le rail de gauche, accédez à **[!UICONTROL Outils]** (icône Marteau) > **[!UICONTROL Ressources]** > **[!UICONTROL Rapports vidéo]**.
1. Dans la page Rapport vidéo, effectuez l’une des opérations suivantes :

   * Dans le coin supérieur droit, sélectionnez l’icône **[!UICONTROL Actualiser le rapport vidéo]**.
N’utilisez la commande d’actualisation que si la date de fin du rapport correspond à la date du jour. Cette exigence vous garantit de voir le suivi vidéo qui a eu lieu depuis la dernière exécution du rapport.

   * Dans le coin supérieur droit, sélectionnez l’icône **[!UICONTROL Sélecteur de date]**.
Indiquez la période de début et de fin pour laquelle vous souhaitez obtenir les données vidéo, puis sélectionnez **[!UICONTROL Exécuter le rapport]**.

   Le groupe Mesures principales identifie diverses mesures agrégées pour toutes les vidéos *publiées* sur votre site.

1. Dans le tableau qui répertorie les principales vidéos publiées, sélectionnez le nom d’une vidéo pour la lire et afficher également le rapport sur la rétention de l’audience (taux de déperdition) de celle-ci.

<!-- OBSOLETE CONTENT OBSOLETE CONTENT - SDK ONLY AVAILABLE INTERNALLY NOW 
### Viewing video reports based on a video viewer that you created using the Dynamic Media HTML5 Viewer SDK {#viewing-video-reports-based-on-a-video-viewer-that-you-created-using-the-scene-hmtl-viewer-sdk}

If you are using an out-of-box video viewer provided by Dynamic Media, or if you created a custom viewer preset based off of an out-of-box video viewer, then no additional steps are required to view video reports. However, if you have created your own video viewer based off the Dynamic Media HTML5 Viewer SDK, then use the following steps to ensure the your video viewer is sending tracking events to Dynamic Media Video Reports.

Use the Dynamic Media Viewers Reference and the Dynamic Media HTML5 Viewers SDK to create your own video viewers.

See [Dynamic Media Viewers Reference Guide](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/home.html).

Download the Scene7 HTML Viewer SDK from Adobe Developer Connection.

See [Adobe Developer Connection](https://help.adobe.com/en_US/scene7/using/WSef8d5860223939e2-43dedf7012b792fc1d5-8000.html).

**To view Video Reports based on a video viewer that you created using the Dynamic Media HTML5 Viewer SDK:**

1. Navigate to any published video asset.
1. Near the upper-left corner of the asset's page, from the drop-down list, select **[!UICONTROL Viewers]**.
1. Select any video viewer preset and copy the embed code.
1. In the embed code, find the line with the following:

   `videoViewer.setParam("config2", "<value>");`

   The `config2` parameter enables tracking in HTML5 Viewers. It is also a company-specific preset that contains the configuration information for Video Reporting, and for customer-specific Adobe Analytics configurations.

   The correct value for the config2 parameter is found in both the **[!UICONTROL Embed Code]** and in the copy **[!UICONTROL URL]** function. In the URL from the copy **[!UICONTROL URL]** command, the parameter to look for is `&config2=<value>` . The value is almost always `companypreset`, but in some instances it can also be `companypreset-1`, `companypreset-2`, and so forth.

1. In your custom video viewer code, add AppMeasurementBridge .jsp to the viewer page by doing the following:

    * First, determine if you need the `&preset` parameter.
      If the `config2` parameter is `companypreset`, you do *not *need `&preset=parameter`.
      If `config2` is anything else, set the preset parameter the same as the `config2` parameter. For example, if `config2=companypreset-2`, add `&param2=companypreset-2` to the AppMeasurmentBridge.jsp URL.

    * Then, add the AppMeasurementBridge.jsp script:
      `<script language="javascript" type="text/javascript" src="https://s7d1.scene7.com/s7viewers/AppMeasurementBridge.jsp?company=robindallas&preset=companypreset-2"></script>`

1. Create the TrackingManager component by doing the following:

    * After calling `s7sdk.Utils.init();` create a TrackingManager instance to track events by adding the following:
      `var trackingManager = new s7sdk.TrackingManager();`

    * Connect components to TrackingManager by doing the following:
      In the `s7sdk.Event.SDK_READY` event handler, attach the component you want to track to the TrackingManager.
      For example, if the component is `videoPlayer`, add
      `trackingManager.attach(videoPlayer);`
      to attach the component to the trackingManager. To track multiple viewers on a page, use multiple tracking mangaer components.

    * Create the AppMeasurementBridge object by adding the following:

      ```
      var appMeasurementBridge = new AppMeasurementBridge(); appMeasurementBridge.setVideoPlayer(videoPlayer);
      ```

    * Add the tracking function by adding the following:

      ```
      trackingManager.setCallback(appMeasurementBridge.track,
       appMeasurementBridge);
      ```

   The appMeasurementBridge object has a built-in track function. OBSOLETE However, you can provide your own to support multiple tracking systems or other functionality.

   For more information, see *Using the TrackingManager Component* in the *Scene7 HTML5 Viewer SDK User Guide* available for download from [Adobe Developer Connection](https://help.adobe.com/en_US/scene7/using/WSef8d5860223939e2-43dedf7012b792fc1d5-8000.html).
 -->





## Activation de la prise en charge du suivi DASH, multilégendes et multiaudio sur votre compte Dynamic Media {#enable-dash}

**À propos de l’activation de la prise en charge DASH sur votre compte**
DASH (Digital Adaptive Streaming over HTTP) est la norme internationale pour la diffusion en continu de vidéos, largement adoptée par les différentes visionneuses de vidéos. Lorsque le DASH est activé sur votre compte, vous avez la possibilité de choisir entre DASH ou HLS pour la diffusion en continu de vidéo adaptative. Vous pouvez également opter pour les deux avec le changement automatique de lecteur lorsque **[!UICONTROL auto]** est sélectionné comme type de lecture dans le paramètre prédéfini de la visionneuse.

Voici quelques avantages clés de l’activation de DASH sur votre compte :

* Module vidéo de flux DASH pour la diffusion en continu à débit adaptatif. Cette méthode permet d’améliorer l’efficacité de la diffusion. Le streaming adaptatif garantit la meilleure expérience de visionnage à vos clients et à vos clientes.
* La diffusion en continu optimisée par le navigateur avec les lecteurs Dynamic Media bascule entre la diffusion en continu HLS et DASH pour garantir la meilleure qualité de service. Le lecteur vidéo passe automatiquement au HLS lorsqu’un navigateur Safari est utilisé.
* Vous pouvez configurer votre méthode de streaming préférée (HLS ou DASH) en modifiant le paramètre prédéfini de la visionneuse de vidéos.
* Le codage vidéo optimisé garantit qu’aucun stockage supplémentaire n’est utilisé lors de l’activation de la fonctionnalité DASH. Un seul ensemble de codes vidéo est créé pour HLS et DASH afin d’optimiser les coûts de stockage vidéo.
* Permet de rendre la diffusion vidéo plus accessible à vos clientes et clients.
* Vous pouvez également obtenir l’URL de streaming au moyen des API.

L’activation de la prise en charge DASH sur votre compte s’effectue au moyen d’un cas de service clientèle Adobe que vous créez et envoyez.

**À propos de l’activation de la prise en charge de plusieurs sous-titres et du suivi audio sur votre compte**

Au moment même où vous créez un cas de prise en charge des Adobes pour que le BASH soit activé sur votre compte, vous pouvez également bénéficier de l’activation automatique de plusieurs sous-titres et du suivi audio. Après l’activation, toutes les vidéos suivantes que vous chargez sont traitées avec une nouvelle architecture du serveur principal qui inclut la prise en charge de l’ajout de plusieurs sous-titres et pistes audio à vos vidéos.

>[!IMPORTANT]
>
>Toutes les vidéos que vous avez téléchargées *before* activation de la prise en charge de plusieurs sous-titres et du suivi audio sur votre compte Dynamic Media, [doit être retraité](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets). Cette étape de retraitement vidéo est nécessaire afin que plusieurs fonctionnalités de sous-titres et de suivi audio soient disponibles. Les URL de la vidéo continuent à fonctionner et à se lire normalement, après retraitement.

**Pour activer la prise en charge du suivi DASH, multilégendes et multiaudio sur votre compte Dynamic Media :**

1. [Utilisez l’Admin Console pour commencer la création d’un nouveau dossier de support.](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html).
1. Suivez les instructions pour créer un dossier de support. Vous devez fournir les informations suivantes :

   * Nom, adresse électronique et numéro de téléphone du contact principal.
   * Votre environnement de Cloud Service (ID de programme et ID d’environnement).
   * Nom de votre compte de société Dynamic Media.
   * Votre région Dynamic Media : Amérique du Nord (NA), Asie-Pacifique (APAC) ou Europe-Moyen-Orient-Asie (EMEA).
   * Indiquez que la prise en charge du suivi DASH, multi-légendes et multi-audio doit être activée sur votre compte Dynamic Media, dans Experience Manager 6.5.

1. Le service clientèle d’Adobe vous inscrira sur la liste d’attente des clientes et clients en se basant sur l’ordre dans lequel les demandes ont été envoyées.
1. Dès qu’Adobe sera prêt à traiter votre demande, le service clientèle vous contactera pour se coordonner avec vous et programmer une date cible d’activation.
1. Une fois la procédure achevée, l’équipe du service clientèle vous en informera.
1. Vous pouvez désormais effectuer l’une des opérations suivantes :

   * Créez votre [paramètre prédéfini de visionneuse vidéo](/help/assets/dynamic-media/managing-viewer-presets.md#creating-a-new-viewer-preset) comme d’habitude.
   * [Ajout de plusieurs sous-titres et pistes audio](#add-msma) à votre vidéo.


## À propos de la prise en charge de plusieurs sous-titres et du suivi audio pour les vidéos dans Dynamic Media{#about-msma}

Grâce à la fonctionnalité de suivi audio et de sous-titres multiples de Dynamic Media, vous pouvez facilement ajouter plusieurs sous-titres et pistes audio à une vidéo principale. Cette fonctionnalité signifie que vos vidéos sont accessibles à une audience mondiale. Vous pouvez personnaliser une seule vidéo principale publiée pour une audience mondiale dans plusieurs langues et respecter les directives d’accessibilité pour différentes régions géographiques. Les auteurs et autrices peuvent également gérer les sous-titres et les pistes audio à partir d’un seul onglet de l’interface d’utilisation.

![Onglet Sous-titres et pistes audio dans Dynamic Media , ainsi qu’un tableau présentant les fichiers de sous-titres .VTT chargés et les fichiers de suivi audio .MP3 chargés pour une vidéo.](/help/assets/dynamic-media/assets/msma-subtitle-audiotracks-tab.png)

Voici quelques cas d’utilisation à prendre en compte pour l’ajout de plusieurs sous-titres et pistes audio à votre vidéo principale :

| Type | Cas d’utilisation |
|--- |--- |
| **Sous-titres** | Prise en charge de plusieurs langues |
|  | Texte descriptif pour l’accessibilité |
| **Pistes audio** | Prise en charge de plusieurs langues |
|  | Pistes de commentaires |
|  | Audio descriptif |

Tous [Formats vidéo pris en charge par Dynamic Media](/help/assets/file-format-support.md) et toutes les visionneuses de vidéos Dynamic Media, à l’exception de Dynamic Media *Video_360* visionneuse : prise en charge pour une utilisation avec plusieurs sous-titres et pistes audio.

La fonctionnalité de suivi multilégende et audio est disponible pour votre compte Dynamic Media au moyen d’un bouton d’activation/désactivation de fonctionnalités qui doit être activé par le service clientèle d’Adobe.

### Ajout de plusieurs sous-titres et pistes audio à votre vidéo {#add-msma}

Avant d’ajouter plusieurs sous-titres et pistes audio à votre vidéo, assurez-vous que vous disposez déjà des éléments suivants :

* Dynamic Media est configuré dans un environnement AEM.
* Un [profil vidéo Dynamic Media est appliqué au dossier dans lequel vos vidéos sont ingérées](/help/assets/dynamic-media/video-profiles.md#applying-a-video-profile-to-folders).
* [Le suivi multilégende et multiaudio est activé sur votre compte Dynamic Media.](#enable-dash).

Les légendes et les légendes ajoutées sont prises en charge avec les formats WebVTT et Adobe VTT. Les fichiers des pistes audio ajoutés sont pris en charge au format MP3.

>[!IMPORTANT]
>
>Toutes les vidéos que vous avez téléchargées *before* activation de la prise en charge de plusieurs sous-titres et du suivi audio sur votre compte Dynamic Media, [doit être retraité](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets). Cette étape de retraitement vidéo est nécessaire afin que plusieurs fonctionnalités de sous-titres et de suivi audio soient disponibles. Les URL de la vidéo continuent à fonctionner et à se lire normalement, après retraitement.

**Pour ajouter plusieurs sous-titres et pistes audio à votre vidéo :**

1. [Chargez la vidéo principale dans un dossier](/help/assets/manage-video-assets.md#upload-and-preview-video-assets) qui comporte déjà un profil vidéo qui lui est affecté.
1. Accédez à la ressource vidéo chargée à laquelle vous souhaitez ajouter plusieurs sous-titres et pistes audio.
1. En mode de sélection des ressources, en vue Liste ou Carte, sélectionnez la ressource vidéo.
1. Dans la barre d’outils, sélectionnez l’icône Propriétés (cercle contenant un « i »).
   ![Ressource vidéo sélectionnée avec une coche sur l’image de la miniature vidéo et l’option Afficher les propriétés surlignée sur la barre d’outils.](/help/assets/dynamic-media/assets/msma-selectedasset-propertiesbutton.png)*Ressource vidéo sélectionnée en vue Vignette.*
1. Sur la page Propriétés de la vidéo, sélectionnez la variable **[!UICONTROL Sous-titres et suivi audio]** .

   >[!TIP]
   >Si vous ne voyez pas le **[!UICONTROL Sous-titres et suivi audio]** , cela signifie l’une des deux choses suivantes :
   >
   >* Aucun profil vidéo n’est affecté au dossier dans lequel se trouve la vidéo sélectionnée. Dans ce cas, voir [Application d’un profil vidéo au dossier](/help/assets/dynamic-media/video-profiles.md#applying-video-profiles-to-specific-folders)
   >* Ou, la vidéo doit être retraitée par Dynamic Media. Dans ce cas, voir [Retraiter des ressources Dynamic Media dans un dossier](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets).
   >
   >Une fois l’une des tâches ci-dessus terminée, reprenez cette procédure.

   ![Onglet Sous-titres et Suivi audio de la page Propriétés.](/help/assets/dynamic-media/assets/msma-audiotracks.png)*Onglet Sous-titres et Suivi audio de la page Propriétés de la vidéo.*

1. (Facultatif) Pour ajouter un ou plusieurs fichiers de sous-titres à une vidéo, procédez comme suit :
   * Sélectionner **[!UICONTROL Télécharger des sous-titres]**.
   * Accédez à un ou plusieurs fichiers .vtt (Video Text Tracks), sélectionnez-les, puis ouvrez-les.
   * Pour que les sous-titres soient visibles sur le lecteur multimédia, vous *must* ajouter les détails (métadonnées) requis à propos de *each* fichier de sous-titres que vous avez chargé. Sélectionnez l’icône représentant un crayon à droite du nom d’un fichier de légende. Dans le **Modifier la légende** , saisissez les détails requis suivants sur le fichier, puis sélectionnez **[!UICONTROL Enregistrer]**. Répétez cette procédure pour chaque fichier de sous-titres que vous avez téléchargé :

     | Métadonnées de légende | Description |
     |--- |--- |
     | Nom de fichier | Le nom de fichier par défaut est dérivé du nom de fichier d’origine. Le nom du fichier ne peut être modifié que lors du chargement et ne peut pas l’être plus tard. Les exigences relatives aux caractères de nom de fichier sont les mêmes que pour AEM Assets.<br>Le même nom de fichier ne peut pas être utilisé pour des fichiers de sous-titres et de suivi audio supplémentaires. |
     | Langue | Sélectionnez la langue de la légende. |
     | Type | Sélectionnez le type de légende que vous utilisez.<br>**Légende** - Texte de la légende affiché avec la vidéo qui traduit ou transcrit la boîte de dialogue.<br>**Légende** : le texte de la légende inclut également les bruits de fond, la différenciation des locuteurs et locutrices et d’autres informations pertinentes, ainsi que la traduction ou la transcription du dialogue, afin d’offrir un contenu plus accessible aux personnes sourdes ou malentendantes. |
     | Libellé | Le texte affiché pour le nom de la légende dans le champ **[!UICONTROL Sélection de l’audio ou de la légende]** liste déroulante dans le lecteur multimédia. Le libellé correspond à ce qu’un client voit et correspond à un suivi de légende ou de légende. Par exemple, `English (CC)`. |

     Si nécessaire, vous pourrez modifier les métadonnées de légende ultérieurement. Lorsque la vidéo est publiée, ces informations sont reflétées dans les URL publiques des vidéos publiées.

1. (Facultatif) Pour ajouter une ou plusieurs pistes audio à une vidéo, procédez comme suit :
   * Sélectionnez **[!UICONTROL Charger des pistes audio]**.
   * Accédez à un ou plusieurs fichiers .mp3 et sélectionnez-les, puis ouvrez-les.
   * Pour que les pistes audio soient visibles dans la liste déroulante **[!UICONTROL Sélectionner l’audio ou la légende]** sur le lecteur multimédia, vous *devez* ajouter les informations requises pour *chaque* fichier de piste audio que vous avez ajouté. Sélectionnez l’icône représentant un crayon à droite du nom d’un fichier de piste audio. Dans la boîte de dialogue **Modifier la piste audio**, saisissez les informations requises suivantes, puis sélectionnez **[!UICONTROL Enregistrer]**. Répétez cette procédure pour chaque fichier de piste audio que vous avez chargé.

     | Métadonnées de piste audio | Description |
     |--- |--- |
     | Nom de fichier | Le nom de fichier par défaut est dérivé du nom de fichier d’origine. Le nom du fichier ne peut être modifié que lors du chargement et ne peut pas l’être plus tard. Les exigences relatives aux caractères de nom de fichier sont les mêmes que pour AEM Assets.<br>Le même nom de fichier ne peut pas être utilisé pour d’autres fichiers de suivi audio ou de sous-titres. |
     | Langue | Sélectionnez la langue de la piste audio. |
     | Type | Sélectionnez le type de piste audio que vous utilisez.<br>**Original** : piste audio initialement jointe à la vidéo et représentée comme `[Original]` dans le libellé avec la langue `English` sélectionnée par défaut. Bien que **[!UICONTROL Libellé]** et **[!UICONTROL Langue]** peuvent être modifiés dans la boîte de dialogue **[!UICONTROL Modifier la piste audio]**, les valeurs d’origine sont utilisées par défaut si la vidéo principale est retraitée.<br>**Standard** : piste audio complémentaire pour une langue autre que la langue originale.<br>**Audio-description** : piste audio qui comprend également une narration descriptive des actions non verbales et des gestes dans la vidéo, rendant le contenu plus accessible pour les personnes malvoyantes. |
     | Libellé | Texte affiché comme nom de la piste audio dans la liste déroulante **[!UICONTROL Sélectionner l’audio ou la légende]** du lecteur multimédia. Le libellé correspond à ce qu’un client ou une cliente voit et à une piste audio. Par exemple, `English [Original]`. Le libellé de l’audio associé à une vidéo est défini sur `[Original]` par défaut. |

     Vous pouvez modifier ces métadonnées de piste audio ultérieurement, si nécessaire. Lorsque la vidéo est publiée, ces informations sont reflétées dans les URL publiques des vidéos publiées.

1. Dans le coin supérieur droit de la page, dans la liste déroulante **[!UICONTROL Enregistrer et fermer]**, sélectionnez **[!UICONTROL Enregistrer]**. Les fichiers sont chargés et le traitement des métadonnées commence, comme le montre la colonne **Statut** de l’interface.

   >[!NOTE]
   >
   >Selon les paramètres de mise en cache de votre instance, le traitement des métadonnées peut prendre plusieurs minutes avant qu’elles ne soient reflétées dans l’aperçu et dans les URL publiées.

1. (Facultatif) Si vous avez sélectionné **[!UICONTROL Enregistrer et fermer]** à l’étape précédente au lieu de **[!UICONTROL Enregistrer]**, vous pouvez toujours afficher le statut du traitement des fichiers chargés. Voir [Afficher l’état de cycle de vie des fichiers de sous-titres et de suivi audio chargés](#lifecycle-status-video).
1. (Facultatif) Prévisualisez la vidéo avant de la publier pour vous assurer que les sous-titres et le son fonctionnent comme prévu. Voir [Prévisualiser une vidéo comportant plusieurs sous-titres et pistes audio](#preview-video-audio-subtitle)
1. Publiez la vidéo. Consultez la section [Publication de ressources](publishing-dynamicmedia-assets.md).

#### À propos de l’ajout de fichiers de sous-titres et de suivi audio à une vidéo déjà publiée

Lorsque vous téléchargez des fichiers de sous-titres ou de suivi audio supplémentaires vers une vidéo déjà publiée, cela signifie que ces fichiers auront une `Processed` une fois qu’ils ont été préparés, à la suite du téléchargement. À ce stade, vous pouvez prévisualiser la vidéo dans Dynamic Media pour afficher ou entendre les fichiers qui viennent d’être chargés.

Toutefois, après l’aperçu, vous devez *publier* la vidéo pour la nouvelle légende ou les fichiers de suivi audio à publier également. Après la publication, les sous-titres ou le contenu audio sont disponibles avec l’URL Dynamic Media publique.

>[!NOTE]
>
>En fonction des paramètres de mise en cache de votre instance, les mises à jour de métadonnées peuvent prendre plusieurs minutes avant d’être répercutées dans l’aperçu et dans les URL publiées.

Dans le cas où vous avez configuré Dynamic Media pour une publication immédiate, le chargement de fichiers audio ou de sous-titres supplémentaires déclenche immédiatement la publication de la vidéo après le chargement de fichiers audio ou de sous-titres.

>[!CAUTION]
>
>Lorsque vous téléchargez des fichiers de sous-titres ou des fichiers audio vers une vidéo publiée ou dont la publication a été annulée, les fichiers sont supprimés si vous [*retraiter*](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets) la vidéo. Seul l’audio d’origine de la vidéo reste intact. Dans ce cas, vous devez charger à nouveau les fichiers de sous-titres et de suivi audio dans la vidéo.

#### Ajouter plusieurs sous-titres à une vidéo ayant une URL existante avec le modificateur de sous-titres

Dynamic Media prend en charge l’ajout de sous-titres uniques à une vidéo au moyen d’un modificateur d’URL. Consultez [Ajouter des légendes à une vidéo](#adding-captions-to-video).

Plusieurs modifications de légende ont la priorité sur une légende ajoutée par l’intermédiaire d’un modificateur d’URL pour les vidéos publiées.

**Pour ajouter plusieurs légendes à une vidéo ayant une URL existante avec le modificateur de légende :**

1. Chargez le fichier de légende déjà ajouté comme modificateur à la vidéo afin de pouvoir le gérer explicitement.
1. Transférez d’autres fichiers de sous-titres, le cas échéant.
1. Publiez la vidéo comme vous le faites habituellement.
L’URL existante avec le modificateur de légende peut désormais charger plusieurs légendes.

### Afficher l’état de cycle de vie des fichiers de sous-titres et de suivi audio chargés{#lifecycle-status-video}

Vous pouvez observer l’état de cycle de vie d’un fichier de sous-titres ou de suivi audio chargé dans votre vidéo principale à partir de la section **Sous-titres et suivi audio** de **Propriétés**.

**Pour afficher le statut du cycle de vie d’une vidéo :**

1. Accédez à la ressource vidéo dont vous souhaitez afficher le statut du cycle de vie.
1. En mode de sélection des ressources, en vue Liste ou Carte, sélectionnez la ressource vidéo.
1. Dans la barre d’outils, sélectionnez l’icône Propriétés (cercle contenant un « i »).
1. Sur la page Propriétés , sélectionnez la variable **[!UICONTROL Sous-titres et suivi audio]** . Dans la colonne État , notez l’état de chaque légende ou fichier audio.

| État du suivi audio ou de la légende | Description |
| --- | --- |
| Traitement | Lorsqu’un nouveau fichier de sous-titres ou de suivi audio est ajouté et enregistré, il passe à l’état &quot;Traitement&quot;. Dynamic Media traite le fichier en joignant le manifeste de streaming à la vidéo principale. |
| Traité | Une fois le traitement terminé, la légende ou le fichier de suivi audio, ou la piste audio d’origine associée à la vidéo principale, s’affiche à l’état &quot;Traités&quot;. Vous pouvez prévisualiser les fichiers de sous-titres et de suivi audio qui apparaissent comme &quot;Traités&quot;. *before* vous publiez la vidéo en direct. |
| Publié | Un état « Publié » représente un état similaire à « Publié » pour une vidéo principale. Les ressources sont publiées lorsque la vidéo principale est publiée et sont disponibles sur l’URL Dynamic Media publique. |
| Échec | Un état &quot;Failed&quot; signifie que le traitement d’un fichier de suivi audio ou de légende n’a pas été terminé. Supprimez la légende ou le fichier de suivi audio et chargez à nouveau le fichier. |
| Dépublié | Lorsqu’une vidéo principale publiée est explicitement dépubliée, tous les fichiers de sous-titres ou de suivi audio que vous avez ajoutés à la vidéo sont également dépubliés. |

![Colonne État mise en surbrillance pour les champs Sous-titres et Suivi audio .](/help/assets/dynamic-media/assets/msma-lifecycle-status.png)*État de cycle de vie de chaque fichier de suivi audio et de légende chargé.*

### Définir l’audio par défaut pour une vidéo comportant plusieurs pistes audio

Par défaut, l’audio d’origine d’une vidéo est défini comme l’audio par défaut à lire.

Cependant, tout fichier de piste audio chargé peut être défini comme l’audio par défaut à lire après le chargement d’une vidéo dans la visionneuse. Dans l’interface utilisateur des propriétés, sous **Sous-titres et suivi audio** , `Default` Le libellé est appliqué à droite du fichier de piste audio pour la lecture vidéo.

>[!NOTE]
>
>La lecture du contenu audio par défaut peut également dépendre de ce qui est défini dans les navigateurs suivants :
>
>* Chrome : le contenu audio par défaut défini dans la vidéo est lu.
>* Safari : si la langue par défaut est définie dans Safari, l’audio est lu avec la langue par défaut définie si elle est disponible avec le manifeste de la vidéo. Sinon, le contenu audio par défaut défini dans les propriétés d’une vidéo est lu.

**Pour définir l’audio par défaut d’une vidéo comportant plusieurs pistes audio :**

1. Accédez à la ressource vidéo dont vous souhaitez définir la piste audio par défaut.
1. En mode de sélection des ressources, en vue Liste ou Carte, sélectionnez la ressource vidéo.
1. Dans la barre d’outils, sélectionnez l’icône Propriétés (cercle contenant un « i »).
1. Sur la page Propriétés , sélectionnez la variable **[!UICONTROL Sous-titres et suivi audio]** .
1. Sous l’en-tête **Pistes audio**, sélectionnez le fichier de piste audio à définir comme fichier par défaut pour la vidéo.
1. Sélectionnez **[!UICONTROL Définir par défaut]**.
Dans la boîte de dialogue **Définir comme valeur par défaut**, sélectionnez **[!UICONTROL Remplacer]**.

   ![En-tête « Pistes audio » avec un nom de fichier de piste audio sélectionné et le bouton « Définir par défaut » mis en surbrillance.](/help/assets/dynamic-media/assets/msma-defaultaudiotrack.png)*Définition de la piste audio par défaut pour une vidéo.*

1. Dans le coin supérieur droit, sélectionnez **[!UICONTROL Enregistrer et fermer]**.
1. Publiez la vidéo. Consultez la section [Publication de ressources](publishing-dynamicmedia-assets.md).

### Prévisualiser une vidéo comportant plusieurs sous-titres et pistes audio{#preview-video-audio-subtitle}

Une fois les fichiers de sous-titres et de suivi audio chargés dans une vidéo et traités, vous pouvez utiliser la visionneuse vidéo Dynamic Media pour prévisualiser toutes les différentes pistes. Cela vous permet de voir à quoi ressemble votre vidéo pour les clients et de vous assurer qu’elle se comporte comme prévu.

Lorsque la vidéo vous satisfait, vous pouvez [la publier](publishing-dynamicmedia-assets.md) en utilisant l’une des méthodes suivantes.

Consultez [Incorporation de la visionneuse de vidéos ou d’images dans une page web](/help/assets/dynamic-media/embed-code.md).
Consultez [Liaison d’URL à une application web](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md). La méthode de liaison basée sur une URL n’est pas possible si votre contenu interactif contient des liens avec des URL relatives, en particulier des liens vers des pages Experience Manager Sites.
Voir [Ajout de ressources Dynamic Media aux pages](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).

>[!NOTE]
>
>L’onglet Aperçu du Experience Manager par défaut n’affiche pas plusieurs légendes et pistes audio. Cela est dû au fait que ces pistes sont associées à Dynamic Media et ne peuvent être affichées qu’à l’aide de l’aperçu de la visionneuse Dynamic Media.

**Pour prévisualiser une vidéo comportant plusieurs sous-titres et pistes audio :**

1. Dans **[!UICONTROL Ressources]**, accédez à une vidéo existante que vous avez ajoutée à plusieurs sous-titres et pistes audio.
1. Sélectionnez la ressource vidéo afin de pouvoir l’ouvrir en mode aperçu.
1. Dans la page d’aperçu, dans le coin supérieur gauche de la page, sélectionnez la liste déroulante, puis sélectionnez **[!UICONTROL Visionneuses]**.

   ![Liste déroulante présentant l’option Visionneuses.](/help/assets/dynamic-media/assets/msma-selectviewers.png)

1. Dans la liste Visionneuses, sélectionnez une visionneuse à utiliser pour l’aperçu vidéo. Par exemple, la capture d’écran suivante illustre la visionneuse **[!UICONTROL Vidéo]** sélectionnée.

   ![Sélection de la visionneuse Vidéo dans la liste déroulante Visionneuses.](/help/assets/dynamic-media/assets/msma-dmviewerselected.png)

1. Près du coin inférieur droit, à gauche de l’icône en forme de volume, sélectionnez l’icône en forme de bulle vocale, puis sélectionnez l’audio ou la légende que vous souhaitez entendre ou voir ou les deux. Si vous le souhaitez, sous Sous Sous-titres, vous pouvez sélectionner **[!UICONTROL Off]** pour ne pas afficher de sous-titres ou de sous-titres.

   ![Liste contextuelle Audio et légendes dans la visionneuse vidéo.](/help/assets/dynamic-media/assets/msma-selectaudiosubtitle.png)*Simulation d’un utilisateur sélectionnant le contenu audio et la légende pour la lecture vidéo.*

1. Pour commencer la lecture, sélectionnez le bouton **[!UICONTROL Lecture]** de la vidéo.
Remarquez les boutons **[!UICONTROL URL]** et **[!UICONTROL Incorporer]** en bas à gauche. Utilisez ces boutons pour [lier l’URL de la vidéo à votre application web](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) ou [incorporer la vidéo dans une page web](/help/assets/dynamic-media/embed-code.md), respectivement.
1. Près du coin supérieur droit de la page d’aperçu, sélectionnez **[!UICONTROL Fermer]**.

### Suppression de fichiers de sous-titres ou de suivi audio d’une vidéo

Vous pouvez supprimer des fichiers de sous-titres ou de suivi audio d’une vidéo. La suppression des fichiers de sous-titres ou de suivi audio publiés est automatiquement répercutée dans l’URL publiée de la vidéo.

La piste audio d’origine extraite d’une vidéo principale ne peut pas être supprimée.

**Pour supprimer une légende ou un fichier de suivi audio d’une vidéo :**

1. Accédez à la ressource vidéo dont vous souhaitez définir la piste audio par défaut.
1. En mode de sélection des ressources, en vue Liste ou Carte, sélectionnez la ressource vidéo.
1. Dans la barre d’outils, sélectionnez l’icône Propriétés (cercle contenant un « i »).
1. Sur la page Propriétés , sélectionnez la variable **[!UICONTROL Sous-titres et suivi audio]** .
1. Effectuez l’une des opérations suivantes :

   * Sous les sous-titres **Sous-titres** , sélectionnez un ou plusieurs fichiers de sous-titres à supprimer de la vidéo, puis sélectionnez **[!UICONTROL Supprimer]**.
   * Pistes audio : sous l’en-tête **Pistes audio**, sélectionnez un ou plusieurs fichiers de pistes audio à supprimer de la vidéo, puis sélectionnez **[!UICONTROL Supprimer]**.

1. Dans la boîte de dialogue Supprimer, sélectionnez **[!UICONTROL OK]**.
1. Publiez la vidéo.

### Télécharger des fichiers de sous-titres ou de suivi audio qui ont été chargés dans une vidéo

Vous pouvez télécharger un ou plusieurs fichiers de sous-titres ou de suivi audio que vous avez chargés pour les utiliser avec une vidéo. Vous avez la possibilité de télécharger tous les fichiers sélectionnés au format .zip ou de créer un dossier de téléchargement distinct pour chaque fichier.

La piste audio d’origine extraite d’un fichier principal ne peut pas être téléchargée.

**Pour télécharger des fichiers de sous-titres ou de suivi audio à partir d’une vidéo :**

1. Accédez à la ressource vidéo dont vous souhaitez définir la piste audio par défaut.
1. En mode de sélection des ressources, en vue Liste ou Carte, sélectionnez la ressource vidéo.
1. Dans la barre d’outils, sélectionnez l’icône Propriétés (cercle contenant un « i »).
1. Sur la page Propriétés , sélectionnez la variable **[!UICONTROL Sous-titres et suivi audio]** .
1. Effectuez l’une des opérations suivantes :

   * Sous les sous-titres **Sous-titres** , sélectionnez un ou plusieurs fichiers de sous-titres à télécharger à partir de la vidéo, puis sélectionnez **[!UICONTROL Télécharger]**.
   * Pistes audio : sous l’en-tête **Pistes audio**, sélectionnez un ou plusieurs fichiers de pistes audio à télécharger à partir de la vidéo, puis sélectionnez **[!UICONTROL Télécharger]**.

1. Dans la boîte de dialogue Télécharger, définissez les options suivantes :

   | Option | Description |
   |--- |--- |
   | Enregistrer sous | Utilisez le nom de fichier par défaut, spécifié dans le champ de texte Enregistrer sous ou indiquez votre propre nom. |
   | Créer un dossier distinct pour chaque ressource | Créez un dossier pour chaque fichier de sous-titres ou fichier de suivi audio que vous avez sélectionné pour téléchargement. |
   | E-mail | Utilisez votre programme de messagerie par défaut pour envoyer le fichier .zip à une adresse e-mail spécifique. |
   | Ressources | Indique le nombre de fichiers à télécharger et la taille totale combinée de tous les fichiers sélectionnés. La désélection de cette option ternit (désactive) le bouton **[!UICONTROL Télécharger]** et vous empêche de télécharger un fichier. |
1. Sélectionnez **[!UICONTROL Télécharger]**.
1. Publiez la vidéo. Consultez la section [Publication de ressources](publishing-dynamicmedia-assets.md).




## Ajout de sous-titres à une vidéo {#adding-captions-to-video}

>[!IMPORTANT]
>
>Adobe vous recommande de [activation de la fonctionnalité de suivi audio et de sous-titres multiples](#enable-dash) sur votre compte Dynamic Media. Cela vous permet de tirer parti de la dernière architecture du serveur principal Dynamic Media et d’un processus simplifié pour ajouter des sous-titres, des sous-titres et des pistes audio à vos vidéos.

Vous pouvez étendre la portée de vos vidéos aux marchés mondiaux en ajoutant des sous-titres aux vidéos uniques ou aux ensembles de vidéos adaptatives. En ajoutant des sous-titrages, vous évitez d’avoir à réenregistrer le son ou de recourir à des locuteurs natifs pour réenregistrer la partie audio dans les différentes langues. La lecture de la vidéo s’effectue dans la langue dans laquelle elle a été enregistrée. Les sous-titres de langues étrangères s’affichent afin que les personnes de différentes langues puissent toujours comprendre la partie audio.

Les légendes permettent également une plus grande accessibilité pour les personnes sourdes ou malentendantes.

>[!NOTE]
>
>Le lecteur vidéo utilisé doit prendre en charge l’affichage des légendes.

Voir aussi [Accessibilité dans Dynamic Media](/help/assets/dynamic-media/accessibility-dm.md).

Dynamic Media peut convertir les fichiers de légende au format JSON (JavaScript Object Notation). Cette conversion signifie que vous pouvez intégrer le texte JSON dans une page web sous forme de transcription masquée complète de la vidéo. Les moteurs de recherche peuvent ensuite analyser et indexer le contenu pour permettre de trouver plus facilement les vidéos et fournir aux utilisateurs des informations supplémentaires sur le contenu des vidéos.

Voir [Diffusion de contenu statique (sans image)](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/c-serving-static-nonimage-contents.html?lang=fr#image-serving-api) pour plus d’informations sur l’utilisation de la fonction JSON dans une URL.

**Pour ajouter des sous-titres à une vidéo :**

1. Utilisez une application ou un service tiers pour créer votre fichier de sous-titres vidéo.

   Assurez-vous que le fichier que vous créez est conforme à la norme WebVTT (Web Video Text Tracks). L’extension de nom de fichier pour les sous-titres est .VTT. D’autres informations sur la norme de sous-titrage WebVTT sont disponibles.

   Reportez-vous à la section [WebVTT : The web video text tracks format](https://w3c.github.io/webvtt/).

   De nombreux sites web offrent des outils et des services gratuits et de grande qualité que vous pouvez utiliser pour créer des fichiers de sous-titres WebVTT en dehors de Dynamic Media. <!-- THE FOLLOWING LINK IS NO LONGER LIVE. CHECKED DECEMBER 13, 2023 For example, to create a simple video caption file with no styling, you can use the following free online caption authoring and editing tool: -->

   <!-- [WebVTT Caption Maker](https://testdrive-archive.azurewebsites.net/Graphics/CaptionMaker/Default.html)

   For best results, use the tool in Internet Explorer 9 or above, Google Chrome, or Safari.

   In the tool, in the **[!UICONTROL Enter URL of video file]** field, paste the copied URL of your video file and then select **[!UICONTROL Load]**. See [Obtain a URL for an Asset](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-an-asset) to get the URL to the video file itself which you can then paste into the **[!UICONTROL Enter URL of video file field]**. Internet Explorer, Chrome, or Safari can then natively play back the video.-->

Suivez maintenant les instructions à l’écran pour créer et enregistrer votre fichier WebVTT. Lorsque vous avez terminé, copiez le contenu du fichier de sous-titres et collez-le dans un éditeur de texte brut, puis enregistrez-le avec une extension de fichier VTT.

>[!NOTE]
>
>Pour une prise en charge globale des sous-titres vidéo dans plusieurs langues, la norme WebVTT exige que vous créiez des fichiers .vtt et des appels distincts pour chaque langue que vous souhaitez prendre en charge.

En règle générale, vous devez attribuer au fichier de sous-titres VTT le même nom qu’au fichier vidéo et vous lui ajoutez l’indicateur de paramètres régionaux, comme -EN, -FR ou -DE. Ainsi, vous pouvez automatiser aisément la génération des URL de vidéo avec le système de gestion de contenu web existant.

1. Dans Experience Manager, chargez votre fichier de sous-titres WebVTT dans le DAM.
1. Accédez à la ressource vidéo *publiée* à associer au fichier de sous-titres que vous avez chargé.

   N’oubliez pas que les URL ne peuvent être copiées qu’*après* la *publication* des ressources.

   Voir [Publication de ressources](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

1. Utilisez l’une des méthodes suivantes :

   * Pour une expérience de visionneuse de vidéos pop-up, sélectionnez **[!UICONTROL URL]**. Dans la boîte de dialogue URL, sélectionnez l’URL et copiez-la dans le Presse-papiers, puis collez-la dans un éditeur de texte simple. Ajoutez l’URL copiée de la vidéo avec la syntaxe suivante :

     `&caption=<server_path>/is/content/<path_to_caption.vtt_file,1>`

     Notez le « `,1` » à la fin du chemin du fichier de sous-titres. Juste après l’extension de fichier VTT dans le chemin d’accès, vous avez la possibilité d’activer ou de désactiver le bouton de sous-titres dans la barre de lecteur vidéo en définissant la valeur respectivement sur « `,1` » ou « `,0` ».

   * Pour une expérience de visionneuse de vidéos intégrée, sélectionnez **[!UICONTROL Code intégré]**. Dans la boîte de dialogue Code intégré, sélectionnez le code intégré et copiez-le dans le Presse-papiers, puis collez-le dans un simple éditeur de texte. Ajoutez le code intégré copié avec la syntaxe suivante :

     `videoViewer.setParam("caption","<path_to_caption.vtt_file,1>");`

     Notez le « `,1` » à la fin du chemin du fichier de sous-titres. Juste après l’extension de fichier VTT dans le chemin d’accès, vous avez la possibilité d’activer ou de désactiver le bouton de sous-titres dans la barre de lecteur vidéo en définissant la valeur respectivement sur « `,1` » ou « `,0` ».

## Ajout de marques de chapitre à la vidéo {#adding-chapter-markers-to-video}

Vous pouvez faciliter la lecture et la consultation de vos vidéos les plus longues en ajoutant des marques de chapitre aux vidéos uniques ou aux ensembles de vidéos adaptatives. Lorsqu’un utilisateur lit la vidéo, il peut sélectionner les marqueurs de chapitre dans la chronologie de la vidéo (également appelée barre vidéo). Ils peuvent facilement accéder au passage qui les intéresse ou accéder immédiatement à de nouveaux contenus et de nouvelles formations et démonstrations.

>[!NOTE]
>
>Le lecteur vidéo utilisé doit prendre en charge l’utilisation des marqueurs de chapitre. Les lecteurs vidéo Dynamic Media prennent en charge les marqueurs de chapitre, mais l’utilisation de lecteurs vidéo tiers ne le permet pas.

<!-- OBSOLETE CONTENT OBSOLETE CONTENT If desired, you can create and brand your own custom video viewer with chapters instead of using a video viewer preset. For instructions on creating your own HTML5 viewer with chapter navigation, in the Adobe Scene7 Viewer SDK for HTML5 guide, reference the heading "Customizing Behavior Using Modifiers" under the classes `s7sdk.video.VideoPlayer` and `s7sdk.video.VideoScrubber`. The Adobe Scene7 Viewer SDK is available as a download from [Adobe Developer Connection](https://help.adobe.com/en_US/scene7/using/WSef8d5860223939e2-43dedf7012b792fc1d5-8000.html). -->

Vous créez une liste de chapitres pour votre vidéo un peu de la même façon que vous créez des sous-titres. Autrement dit, vous créez un fichier WebVTT. Notez toutefois que ce fichier doit être distinct de tout fichier de sous-titrage WebVTT. Vous ne pouvez pas combiner les sous-titres et les chapitres dans un fichier WebVTT.

Vous pouvez utiliser l’exemple suivant comme un exemple du format que vous pouvez utiliser pour créer un fichier WebVTT avec une navigation par chapitre :

### Fichier WebVTT avec navigation par chapitre vidéo {#webvtt-file-with-video-chapter-navigation}

```xml {.line-numbers}
WEBVTT
Chapter 1
00:00.000 --> 01:04.364
The bicycle store behind it all.
Chapter 2
01:04.364 --> 02:00.944
Creative Cloud.
Chapter 3
02:00.944 --> 03:02.937
Ease of management for a working solution.
Chapter 4
03:02.937 --> 03:35.000
Cost-efficient access to rapidly evolving technology.
```

Dans l’exemple ci-dessus, le `Chapter 1` est l’identifiant de repère et il est facultatif. La période de repère `00:00:000 --> 01:04:364` indique l’heure de début et l’heure de fin du chapitre au format `00:00:000`. Les trois derniers chiffres sont les millisecondes et peuvent être laissés sur `000`, selon vos préférences. Le titre du chapitre de `The bicycle store behind it all` est la description réelle du contenu du chapitre. L’identifiant de repère, l’heure de départ du repère, ainsi que le titre du chapitre apparaissent tous dans un pop-up du lecteur quand un utilisateur pointe la souris sur un point de repère visuel dans la chronologie.

Étant donné que vous utilisez une visionneuse de vidéos HTML5, assurez-vous que le fichier de chapitres que vous créez est conforme à la norme WebVTT (Web Video Text Tracks). L’extension de nom de fichier de chapitres est .VTT. D’autres informations sur la norme de sous-titrage WebVTT sont disponibles.

Reportez-vous à la section [WebVTT : The web video text tracks format](https://w3c.github.io/webvtt/).

**Pour ajouter des marqueurs de chapitre à la vidéo :**

1. Enregistrez le fichier VTT en codage UTF8 pour éviter tout problème de rendu des caractères dans le texte des titres de chapitres.

   En règle générale, vous attribuez au fichier de chapitres VTT le même nom que celui du fichier vidéo et lui ajoutez le mot « chapitres ». Ainsi, vous pouvez automatiser aisément la génération des URL de vidéo avec le système de gestion de contenu web existant.
1. Dans Experience Manager, chargez votre fichier de chapitres WebVTT.

   Consultez [Chargement de ressources](/help/assets/manage-digital-assets.md#uploading-assets).

1. Utilisez l’une des méthodes suivantes :

   <table>
     <tbody>
      <tr>
       <td>Pour une expérience de visionneuse de vidéos pop-up</td>
       <td>
       <ol>
       <li>Accédez à la ressource vidéo <i>publiée</i> à associer au fichier de chapitres que vous avez chargé. N’oubliez pas que les URL ne peuvent être copiées qu’<i>après</i> la <i>publication</i> des ressources. Voir <a href="/help/assets/dynamic-media/publishing-dynamicmedia-assets.md">Publication de ressources</a>.</li>
       <li>Dans le menu déroulant, sélectionnez <strong>Visionneuses</strong>.</li>
       <li>Dans le rail de gauche, sélectionnez le nom du paramètre prédéfini de la visionneuse de vidéos. Un aperçu de la vidéo s’ouvre dans une page distincte.</li>
       <li>Dans le rail de gauche, dans la partie inférieure, sélectionnez <strong>URL</strong>.</li>
       <li>Dans la boîte de dialogue URL, sélectionnez l’URL et copiez-la dans le Presse-papiers, puis collez-la dans un simple éditeur de texte.</li>
       <li>Ajoutez l’URL copiée de la vidéo avec la syntaxe suivante pour l’associer à l’URL copiée dans votre fichier de chapitres :<br /> <br /> <code>&navigation=<<i>full_copied_URL_path_to_chapter_file</i>.vtt></code><br /> </li>
       </ol> </td>
      </tr>
      <tr>
       <td>Pour une expérience de visionneuse de vidéos incorporée<br /> </td>
       <td>
       <ol>
       <li>Accédez à la ressource vidéo <i>publiée</i> à associer au fichier de chapitres que vous avez chargé. N’oubliez pas que les URL ne peuvent être copiées qu’<i>après</i> la <i>publication</i> des ressources. Voir <a href="/help/assets/dynamic-media/publishing-dynamicmedia-assets.md">Publication de ressources</a>.</li>
       <li>Dans le menu déroulant, sélectionnez <strong>Visionneuses</strong>.</li>
       <li>Dans le rail de gauche, sélectionnez le nom du paramètre prédéfini de la visionneuse de vidéos. Un aperçu de la vidéo s’ouvre dans une page distincte.</li>
       <li>Dans le rail de gauche, dans la partie inférieure, sélectionnez <strong>Intégrer</strong>.</li>
       <li>Dans la boîte de dialogue Code intégré, sélectionnez et copiez le code entier dans le Presse-papiers, puis collez-le dans un simple éditeur de texte.</li>
       <li>Ajoutez le code intégré de la vidéo avec la syntaxe suivante pour l’associer à l’URL copiée dans votre fichier de chapitres :<br /> <br /> <code>videoViewer.setParam("navigation","&lt;<i>full_copied_URL_path_to_chapter_file</i>.vtt>"</code></li>
       </ol> </td>
      </tr>
     </tbody>
   </table>



## À propos des miniatures vidéo {#about-video-thumbnails}

Une miniature vidéo est une version en taille réduite d’une image vidéo ou d’une ressource d’image présentant la vidéo au client. La miniature doit servir à encourager un client à sélectionner la vidéo.

Toutes les vidéos dans Experience Manager doivent être associées à une miniature. Vous ne pouvez pas supprimer une miniature sans la remplacer. Par défaut, lorsque vous chargez une vidéo sur Experience Manager, la première image est utilisée comme miniature. Cependant, vous pouvez personnaliser la miniature à des fins de valorisation de marque ou de recherche visuelle, par exemple. Lorsque vous personnalisez une miniature vidéo, vous pouvez lire la vidéo et la suspendre sur l’image que vous souhaitez utiliser. Vous pouvez également sélectionner une ressource d’image que vous avez déjà chargée et *publiée* dans votre gestionnaire de ressources numériques.

Lorsque la miniature est modifiée pour une vidéo, la génération de miniatures par le biais du service d’Asset compute lors du retraitement de la vidéo est ignorée.

La possibilité de personnaliser une miniature vidéo n’est disponible qu’après avoir appliqué un profil vidéo au dossier où se trouve la vidéo.

### Ajout d’une miniature vidéo personnalisée {#adding-a-custom-video-thumbnail}

1. Assurez-vous que vous avez déjà :

   * Créé un dossier pour vos ressources vidéo.
   * [Application d’un profil vidéo au dossier](/help/assets/dynamic-media/video-profiles.md#applying-a-video-profile-to-folders).

   * [Téléchargé vos vidéos dans le dossier](/help/assets/manage-video-assets.md#upload-and-preview-video-assets).

1. Accédez à une ressource vidéo chargée pour laquelle vous souhaitez modifier l’image miniature.
1. En mode de sélection de ressources, soit **[!UICONTROL Vue liste]** soit **[!UICONTROL Vue carte]**, sélectionnez la ressource vidéo.
1. Dans la barre d’outils, sélectionnez l’icône **[!UICONTROL Propriétés]** (cercle contenant un « i »).
1. Sur la page Propriétés de la vidéo, sélectionnez **[!UICONTROL Modifier la miniature]**.
1. Sur la page Modifier la miniature, effectuez l’une des opérations suivantes :

   * Pour utiliser une image de la vidéo comme nouvelle miniature :

      * Dans la barre d’outils, choisissez **[!UICONTROL Sélectionner une image dans la vidéo]**.
      * Sélectionnez le bouton Lecture, puis le bouton Pause sur l’image à capturer comme nouvelle miniature de la vidéo.

   * Pour utiliser une ressource image comme nouvelle miniature :

      * Dans la barre d’outils, choisissez **[!UICONTROL Sélectionner une miniature dans Ressources]**.
      * Choisissez **[!UICONTROL Sélectionner la miniature]**.
      * Accédez à une ressource d’image téléchargée et publiée précédemment que vous souhaitez utiliser. La ressource est automatiquement redimensionnée afin de servir d’image miniature pour la vidéo.
      * Sélectionnez la ressource image, puis choisissez **[!UICONTROL Sélectionner]**.

1. Sur la page Modifier la miniature, sélectionnez **[!UICONTROL Enregistrer la modification]**.
1. Sur la page Propriétés de la vidéo, dans le coin supérieur droit, sélectionnez **[!UICONTROL Enregistrer et fermer]**.



<!--

## About video thumbnails in Dynamic Media Hybrid mode{#about-video-thumbnails-in-dynamic-media-hybrid-mode}

You can choose from one of ten thumbnail images automatically generated by Dynamic Media to add to your video. The video player displays your selected thumbnail when a video asset is used with the Dynamic Media component in the authoring environment of Experience Manager Sites, Experience Manager Mobile, or Experience Manager Screens. The thumbnail serves as a static picture that best represents the contents of your entire video and further encourages users to select the Play button.

Based on the total time of the video, Dynamic Media captures ten (default) thumbnail images at 1%, 11%, 21%, 31%, 41%, 51%, 61%, 71%, 81%, and 91% into the video. The ten thumbnails persist meaning that if you decide to choose a different thumbnail later on, you do not need to regenerate the series. You preview the ten thumbnail images and then select the one you want to use with your video. If you want to change to default you can use CRXDE Lite to configure the time interval that thumbnail images are generated. For example, if you only wanted to generate a series of four evenly spaced thumbnail images from your video, you can configure the interval time at 24%, 49%, 74%, and 99%.

Ideally, you can add a video thumbnail anytime after you upload your video but before you publish the video on your website.

If you prefer, you can choose to upload a custom thumbnail to represent your video instead of using a thumbnail generated by Dynamic Media. For example, you could create a custom thumbnail image that has the title of your video, an eye-catching opening image, or a very specific image captured from your video. The custom video thumbnail image that you upload should have a maximum resolution of 1280 x 720 pixels (minimum width of 640 pixels) and be no larger than 2MB.

See also [About video thumbnails](/help/assets/dynamic-media/video.md#about-video-thumbnails-in-dynamic-media-scene-mode).

-->

<!--

### Adding a video thumbnail {#adding-a-video-thumbnail}

1. Navigate to an uploaded video asset that you want to add a video thumbnail.
1. In asset selection mode either from the List View or the Card View, select the video asset.
1. On the toolbar, select the **[!UICONTROL View Properties]** icon (a circle with an "i" in it).
1. On the video's Properties page, select **[!UICONTROL Change Thumbnail]**.
1. On the Change Thumbnail page, on the toolbar, select **[!UICONTROL Select Frame]**.

   Dynamic Media generates a series thumbnail images from your video, based on the default time interval or time interval you customized.

1. Preview the generated thumbnail images, then select the one you want to add to your video.
1. Select **[!UICONTROL Save Change]**.

   The video's thumbnail image is updated to use the thumbnail you selected. If you later decide to change the thumbnail image, you can return to the **[!UICONTROL Change Thumbnail]** page and select a new one.

   If you configured new default time intervals, or you uploaded a new video to replace the existing video, you need to have Dynamic Media regenerate the thumbnails.

   See [Configuring the default time interval that video thumbnails are generated](#configuring-the-default-time-interval-that-video-thumbnails-are-generated).

-->

<!--

#### Configuring the default time interval that video thumbnails are generated {#configuring-the-default-time-interval-that-video-thumbnails-are-generated}

When you configure and save the new default time interval, your change automatically applies only to videos that you upload in the future. It does not automatically apply the new default to videos that you previously uploaded. For existing videos, you must regenerate the thumbnails.

See [Adding a video thumbnail](#adding-a-video-thumbnail).

**To configure the default time interval that video thumbnails are generated,**

1. In Experience Manager, navigate to **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL CRXDE Lite]**.

1. In the CRXDE Lite page, in the directory panel on the left, navigate t `o etc/dam/imageserver/configuration/jcr:content/settings.`

   if the directory panel is not visible, you may need to select the >> icon to the left of the Home tab.

1. On the lower-right panel, in the Properties tab, double-select `thumbnailtime`.
1. In the Edit thumbnailtime dialog box, use the text fields to enter interval values as percentages.

    * Select the plus sign (+) icon to add one or more interval value fields. You may need to scroll to the bottom of the dialog box to see the icon.
    * Select the minus sign (-) icon to the right of an interval value field to delete it from the list.
    * Select the up arrow icon and the down arrow icon to reorder the interval values.

1. Select **[!UICONTROL OK]** to return to the Properties tab.
1. Near the upper-left corner of the CRXDE Lite page, select **[!UICONTROL Save All]**, then select the Back Home icon in the upper-left corner to return to Experience Manager.

   See [Adding a video thumbnail](#adding-a-video-thumbnail).

-->

<!--

### Adding a custom video thumbnail {#adding-a-custom-video-thumbnail-1}

These steps apply only to Dynamic Media running in Hybrid mode.

T**o add a custom video thumbnail**,

1. Navigate to an uploaded video asset that you want to add a custom video thumbnail.
1. In asset selection mode either from the List View or the Card View, select the video asset.
1. On the toolbar, select the **[!UICONTROL View Properties]** icon (a circle with an "i" in it).
1. On the video's Properties page, select **[!UICONTROL Change Thumbnail]**.
1. On the Change Thumbnail page, on the toolbar, select **[!UICONTROL Upload New Thumbnail]**.
1. Navigate to a thumbnail image you want to use, select it, then select **[!UICONTROL Open]** to begin uploading the image into Experience Manager. Following the upload, be sure you publish the image.
1. After you have successfully uploaded and published the image, in the Change Thumbnail page, select **[!UICONTROL Save Changes]**.

   The custom thumbnail is added to your video.

-->

## Modifier l’URL de Dynamic Media pour les ressources Dynamic Media

Les vidéos traitées dans Dynamic Media peuvent être lancées par le biais de visionneuses prêtes à l’emploi, mais aussi en accédant directement aux URL de manifeste et en les lisant via vos propres visionneuses personnalisées. Le contenu ci-dessous vous présente l’API pour récupérer les URL de manifeste d’une vidéo.

### À propos de l’API getVideoManifestURI

L’API `getVideoManifestURI` est exposée via c`q-scene7-api:com.day.cq.dam.scene7.api` et peut être utilisée pour générer les URL de manifeste suivantes :

```java
/**   
* Returns the manifest url for videos 
* @param resource video resource 
* @param manifestType type of video streaming manifest being requested 
* @param onlyIfPublished return a manifest only if the video is published 
* @return the manifest url for videos 
* 
* @throws Exception 
*/
@Nullable 
String getVideoManifestURI(Resource resource, ManifestType manifestType, boolean onlyIfPublished) throws Exception;
```

#### Paramètres de l’API getVideoManifestURI

Cette API utilise les trois paramètres suivants :

| Paramètre | Description |
| --- | --- |
| `resource` | Ressource correspondant à la vidéo ingérée par Dynamic Media. |
| `manifestType` | Peut être `ManifestType.DASH` ou `ManifestType.HLS` |
| `onlyIfPublished` | Définissez cette variable sur true au cas où l’uri de manifeste n’est générée que si elle est publiée et disponible au niveau de la diffusion. |

Pour récupérer les URL de manifeste des vidéos à l’aide de la méthode ci-dessus, ajoutez un [profil de codage vidéo](/help/assets/dynamic-media/video-profiles.md#creating-a-video-encoding-profile-for-adaptive-streaming) dans un dossier « charger des vidéos ». Dynamic Media traite ces vidéos en fonction des encodages trouvés dans le fichier de codage vidéo qui a été affecté au dossier. Vous pouvez maintenant appeler l’API ci-dessus pour récupérer les URL de manifeste pour les vidéos chargées.

### Scénarios d’erreur

L’API renvoie la valeur null en cas d’erreur. Les exceptions sont consignées dans les journaux d’erreurs d’Experience Manager. Toutes ces erreurs consignées commencent par `Could not generate Video Manifest URI`. Les scénarios suivants peuvent provoquer de telles erreurs :

* Une `IllegalArgumentException` est consignée pour l’un des éléments suivants :

   * Le paramètre `resource` transmis est une valeur null.
   * Le paramètre `resource` transmis n’est pas une vidéo.
   * Le paramètre `manifestType` transmis est une valeur null.
   * Le paramètre `onlyIfPublished` transmis est réel, mais la vidéo n’est pas publiée.
   * La vidéo n’a pas été ingérée à l’aide d’une visionneuse de vidéos à débit adaptatif provenant de Dynamic Media.

* `IOException` est consignée lorsqu’un problème de connexion à Dynamic Media se produit.
* `UnsupportedOperationException` est consignée lorsqu’un paramètre `manifestType` transmis est `ManifestType.DASH`, alors que la vidéo n’a pas été traitée au format DASH.

<!-- THE REMAINING SECTION IS FOR 6.5 ONLY 

The following is an example of the above API using servlets written in *HTTPWhiteBoard* specification. Select each tab for the code syntax.

>[!BEGINTABS]

>[!TAB Add dependency in pom.xml]

+++**Add dependency in pom.xml** 

```java
dependency> 
     <groupId>com.day.cq.dam</groupId> 
     <artifactId>cq-scene7-api</artifactId> 
     <version>5.12.64</version> 
     <scope>provided</scope> 
</dependency> 
```

+++

>[!TAB Sample servlet]

+++**Sample servlet** 

```java
@Component
        service = Servlet.class 
) 
@HttpWhiteboardServletPattern(value = ManifestServlet.SERVLET_PATTERN) 
@HttpWhiteboardContextSelect(value = Constants.SERVLET_CONTEXT_SELECTOR) 
public class ManifestServlet extends HttpServlet { 

   private static final Logger LOGGER = LoggerFactory.getLogger(ManifestServlet.class); 

   private final ObjectMapper objectMapper; 

    @Reference 
    private Scene7Service scene7Service; 

   public static final String SERVLET_PATTERN = Constants.VIDEO_API_PREFIX + "/manifestUrl"; 

   public ManifestServlet() {
         this.objectMapper = new ObjectMapper(); 
         objectMapper.setSerializationInclusion(JsonInclude.Include.NON_NULL); 
   }

   @Override 

   protected void doGet(HttpServletRequest request, HttpServletResponse response) throws IOException {
        final ResourceResolver resolver = getResourceResolver(request); 
        String assetPath = request.getParameter("assetPath"); 
        String manifest = request.getParameter("manifestType"); 
        String onlyIfPublished = request.getParameter("onlyIfPublished"); 
        Resource resource = resolver.getResource(assetPath); 
        response.setCharacterEncoding(StandardCharsets.UTF_8.toString()); 
        response.setContentType("application/json"); 
        if(resource == null) { 
            LOGGER.info("could not retrieve the resource from JCR"); 
            error("could not retrieve the resource from JCR", response); 
            return; 
        }

        String manifestUri = null; 

        try{ 
            ManifestType manifestType =  ManifestType.DASH; 
            if(manifest != null) { 
                manifestType = ManifestType.valueOf(manifest); 
            } 
            manifestUri = scene7Service.getVideoManifestURI(resource, manifestType, onlyIfPublished != null); 
            objectMapper.writeValue(response.getWriter(), new ManifestUrl(manifestUri)); 
            response.setContentType("application/json"); 
        } catch (Exception e) { 
            LOGGER.error(e.getMessage(), e); 
            error(String.format("Unable to get the manifest url for %s. %s", assetPath, e.getMessage()), response); 
        } 
    } 

    private ResourceResolver getResourceResolver(HttpServletRequest request) { 
        Object rr = request.getAttribute(AuthenticationSupport.REQUEST_ATTRIBUTE_RESOLVER); 
        if (!(rr instanceof ResourceResolver)) { 
            throw new IllegalStateException( 
                    "The request does not seem to have been created via Apache Sling's authentication mechanism."); 
        } else { 
            return (ResourceResolver) rr; 
        } 
    } 

    private void error(String errorMessage, HttpServletResponse response) throws IOException { 
        ManifestUrl errorManifest = new ManifestUrl(null); 
        errorManifest.setErrorMessage(errorMessage); 
        response.setStatus(HttpServletResponse.SC_INTERNAL_SERVER_ERROR); 
        objectMapper.writeValue(response.getWriter(), errorManifest); 
    } 
} 
```

+++

>[!TAB Response Class for servlet]

+++**Response Class for servlet** 

```java
public class ManifestUrl extends VideoResponse { 
     String manifestUrl; 
     public ManifestUrl(String manifestUrl) { 
         this.manifestUrl = manifestUrl; 
     } 
     public String getManifestUrl() { 
         return manifestUrl; 
     } 
} 

public abstract class VideoResponse { 
     String errorString; 

     public String getErrorString() { 
         return errorString; 
     } 

     public void setErrorMessage(String errorString) { 
         this.errorString = errorString; 
     } 
} 
```

+++

>[!TAB Constants file referenced in servlet]

+++**Constants file referenced in servlet** 

```java
public final class Constants { 

     private Constants() { 
     } 

     public static final String VIDEO_API_PREFIX = "/dynamicmedia/video"; 
     public static final String SERVLET_CONTEXT_SELECTOR = "(" + HttpWhiteboardConstants.HTTP_WHITEBOARD_CONTEXT_NAME + "=" + 
             DMSampleApiHttpContext.CONTEXT_NAME + ")"; 

 } 
```

+++

>[!TAB ServletContext]

+++**ServletContext** 

Mount the above servlet using a `servletContext`. The following is an example of `servletContext`. 

```java
public class DMSampleApiHttpContext extends ServletContextHelper { 

 public static final String CONTEXT_NAME = "com.adobe.dmSample"; 
 public static final String CONTEXT_PATH = "/dmSample"; 

 private final MimeTypeService mimeTypeService; 

 private final AuthenticationSupport authenticationSupport; 

 /** 
  * Constructs a new context that will use the given dependencies. 
  * 
  * @param mimeTypeService Used when providing mime type of requests. 
  * @param authenticationSupport Used to authenticate requests with sling. 
  */ 
 @Activate 
 public DMSampleApiHttpContext(@Reference final MimeTypeService mimeTypeService, 
                               @Reference final AuthenticationSupport authenticationSupport) { 
     this.mimeTypeService = mimeTypeService; 
     this.authenticationSupport = authenticationSupport; 
 } 

 // ---------- HttpContext interface ---------------------------------------- 
 /** 
  * Returns the MIME type as resolved by the <code>MimeTypeService</code> or 
  * <code>null</code> if the service is not available. 
  */ 
 @Override 
 public String getMimeType(String name) { 
     MimeTypeService mtservice = mimeTypeService; 
     if (mtservice != null) { 
         return mtservice.getMimeType(name); 
     } 
     return null; 
 } 

 /** 
  * Returns the real context path that is used to mount this context. 
  * @param req servlet request 
  * @return the context path 
  */ 
 public static String getRealContextPath(HttpServletRequest req) { 
     final String path = req.getContextPath(); 
     if (path.equals(CONTEXT_PATH)) { 
         return ""; 
     } 
     return path.substring(CONTEXT_PATH.length()); 
 } 

 /** 
  * Returns a request wrapper that transforms the context path back to the original one 
  * @param req request 
  * @return the request wrapper 
  */ 
 public static HttpServletRequest createContextPathAdapterRequest(HttpServletRequest req) { 
     return new HttpServletRequestWrapper(req) { 

         @Override 
         public String getContextPath() { 
             return getRealContextPath((HttpServletRequest) getRequest()); 
         } 

     }; 

 } 

 /** 
  * Always returns <code>null</code> because resources are all provided 
  * through individual endpoint implementations. 
  */ 
 @Override 
 public URL getResource(String name) { 
     return null; 
 } 

 /** 
  * Tries to authenticate the request using the 
  * <code>SlingAuthenticator</code>. If the authenticator or the Repository 
  * is missing this method returns <code>false</code> and sends a 503/SERVICE 
  * UNAVAILABLE status back to the client. 
  */ 
 @Override 
 public boolean handleSecurity(HttpServletRequest request, 
                               HttpServletResponse response) throws IOException { 

     final AuthenticationSupport authenticator = this.authenticationSupport; 
     if (authenticator != null) { 
         return authenticator.handleSecurity(createContextPathAdapterRequest(request), response); 
     } 

     // send 503/SERVICE UNAVAILABLE, flush to ensure delivery 
     response.sendError(HttpServletResponse.SC_SERVICE_UNAVAILABLE, 
             "AuthenticationSupport service missing. Cannot authenticate request."); 
     response.flushBuffer(); 

     // terminate this request now 
     return false; 
 } 
}
```

+++

>[!ENDTABS]



### Use the sample servlet

You invoke the servlet by performing a `GET` operation at `/dmSample/dynamicmedia/video/manifestUrl`. The following query parameters are passed: 

| Query parameter | Description |
| --- | --- |
| `assetPath` | Mandatory. The path to the video for which `manifestUrl` is generated. |
| `manifestType` | Optional. Parameter can be DASH or HLS. If it is not passed, it defaults to DASH. |
| `onlyIfPublished` | Optional. If passed, the `manifestUrl` is returned only if the video is published.  |

In this example, let us assume the following setup: 

* The company is `samplecompany`.
* The authoring instance is `http://sample-aem-author.com`.
* The folder `/content/dam/video-example` has a video encoding profile applied to it. 
* The video `scenery.mp4` is uploaded to the folder `/content/dam/video-example`.

You can invoke the servlet in following ways: 
     
| Type | Description |
| :--- | --- |
| HLS | `http://sample-aem-author.com/dmSample/dynamicmedia/video/manifestUrl?manifestType=HLS&assetPath=/content/dam/video-example/scenery.mp4`<br><br>In case DASH delivery is enabled:<br>`{"manifestUrl":"https://s7d1.scene7.com/is/content/samplecompany/scenery-AVS.m3u8?packagedStreaming=true"}`<br><br>In case DASH delivery is disabled:<br>`{"manifestUrl":"https://s7d1.scene7.com/is/content/samplecompany/scenery-AVS.m3u8"}` |
| DASH | `http://sample-aem-author.com/dmSample/dynamicmedia/video/manifestUrl?manifestType=DASH&assetPath=/content/dam/video-example/scenery.mp4`<br><br>In case DASH delivery is enabled:<br>`{"manifestUrl":"https://s7d1.scene7.com/is/content/samplecompany/scenery-AVS.mpd"}`<br><br>In case DASH delivery is disabled:<br>`{}` |
| Error: asset path is wrong | `http://sample-aem-author.com/dmSample/dynamicmedia/video/manifestUrl?manifestType=DASH&assetPath=/content/dam/video-example/scennnnnnery.mp4`<br><br>`{"errorString":"could not retrieve the resource from JCR"}` |

-->





