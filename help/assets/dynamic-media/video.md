---
title: Vidéo
description: Découvrez comment utiliser la vidéo dans Dynamic Media.
feature: Profils vidéo
topic: Professionnel
translation-type: tm+mt
source-git-commit: bd7734c0f132b660c15a7eba0a6f92042e377a63
workflow-type: tm+mt
source-wordcount: '9512'
ht-degree: 71%

---


# Vidéo {#video}

Cette section décrit l’utilisation de vidéos dans Dynamic Media.

## Démarrage rapide : vidéos {#quick-start-videos}

Le processus détaillé décrit ci-après vise à vous aider à maîtriser rapidement les opérations liées aux visionneuses de vidéos adaptatives dans Dynamic Media. Après chaque étape, vous trouverez des références croisées vers les en-têtes de rubrique où vous trouverez plus d’informations.

>[!NOTE]
>
>Avant de travailler sur la vidéo dans Dynamic Media, assurez-vous que votre administrateur Adobe Experience Manager a déjà activé et configuré les Cloud Services Dynamic Media.
>
>* Voir [Configuration des Cloud Services Dynamic Media](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services) dans Configuration de Dynamic Media et [Dépannage de Dynamic Media](/help/assets/dynamic-media/troubleshoot-dm.md).

>



1. **Chargez les vidéos Dynamic Media** en procédant comme suit :

   * Créez votre propre profil de codage vidéo. Vous pouvez également utiliser le profil _Codage vidéo adaptatif_ prédéfini fourni avec Dynamic Media.

      * [Création d’un profil de codage vidéo](/help/assets/dynamic-media/video-profiles.md#creating-a-video-encoding-profile-for-adaptive-streaming).
      * En savoir plus sur les [bonnes pratiques relatives au codage vidéo](#best-practices-for-encoding-videos).
   * Associez le profil de traitement vidéo à un ou plusieurs dossiers dans lequel vous allez charger les vidéos issues de sources originales.

      * [Application d’un profil vidéo à des dossiers](/help/assets/dynamic-media/video-profiles.md#applying-a-video-profile-to-folders).
      * En savoir plus sur les [bonnes pratiques relatives à l’organisation des ressources numériques en vue de l’utilisation de profils de traitement](/help/assets/dynamic-media/best-practices-for-file-management.md).
      * En savoir plus sur l’[organisation des ressources numériques](/help/assets/organize-assets.md).
   * Chargez les vidéos issues de sources originales dans les dossiers. Vous pouvez charger des fichiers vidéo d’une taille de 15 Go chacun au maximum. Lorsque vous ajoutez des vidéos au dossier, elles sont codées selon le profil de traitement vidéo affecté au dossier.

      * [Chargement des vidéos](/help/assets/manage-video-assets.md#upload-and-preview-video-assets).
      * En savoir plus sur les [formats de fichiers d’entrée pris en charge](/help/assets/file-format-support.md).
   * Contrôle la façon dont l’[encodage vidéo progresse](#monitoring-video-encoding-and-youtube-publishing-progress) du point de vue de la ressource ou du processus.




1. **Gérez les vidéos Dynamic Media** en effectuant les opérations suivantes :

   * Organisez, parcourez et recherchez des ressources vidéo

      * [Organisation des ressources numériques](/help/assets/organize-assets.md)
En savoir plus sur les [bonnes pratiques relatives à l’organisation des ressources numériques en vue de l’utilisation de profils de traitement](/help/assets/dynamic-media/best-practices-for-file-management.md)

      * [Recherche de ressources vidéo](/help/assets/search-assets.md#custompredicates) ou [Recherche de ressources](/help/assets/manage-digital-assets.md#search-assets)
   * Prévisualisez et publiez des ressources vidéo

      * Affichez la vidéo source et les rendus codés de la vidéo avec les miniatures associées :
         [Prévisualisation de vidéos](/help/assets/manage-video-assets.md#upload-and-preview-video-assets) ou [Prévisualisation de ressources](/help/assets/dynamic-media/previewing-assets.md)
         [Gestion des rendus vidéo](/help/assets/manage-digital-assets.md#managing-renditions)


<!-- Commented video-renditions.md as the file is not published yet and will lead to broken link.
        * View the source video and encoded renditions of the video along with its associated thumbnails:
          [Previewing videos](/help/assets/manage-video-assets.md#upload-and-preview-video-assets) or [Previewing assets](/help/assets/dynamic-media/previewing-assets.md)
          [Viewing video renditions](/help/assets/video-renditions.md)
          [Managing video renditions](/help/assets/manage-digital-assets.md#managing-renditions) -->

    * [Gestion des paramètres prédéfinis de la visionneuse](/help/assets/dynamic-media/managing-viewer-presets.md)
    * [Publication des ressources](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md)
    
    * Utilisation des métadonnées vidéo

<!--      * View the properties of an encoded video rendition such as frame rate, audio and video bitrate, and codec:
          [Viewing video rendition properties](/help/assets/video-renditions.md) -->

    * Modifier les propriétés d’une vidéo, telles que le titre, la description, les balises et les champs de métadonnées personnalisés :
    [Modification des propriétés vidéo](/help/assets/manage-digital-assets.md#edit-properties)
    
    * [Gestion des métadonnées pour les ressources numériques](/help/assets/manage-metadata.md)
    * [Schémas de métadonnées](/help/assets/metadata-schemas.md)
    
    * Réviser, approuver et annoter les vidéos, et conserver un contrôle de version total
    
    * [Annotation des vidéos](/help/assets/manage-video-assets.md#annotate-video-video-assets) ou [Annotation des ressources](/help/assets/manage-digital-assets.md#annotating)
    
    * [Création d’une version](/help/assets/manage-digital-assets.md#asset-versioning)
    * [Démarrage d’un workflow sur une ressource](/help/assets/manage-digital-assets.md#starting-a-workflow-on-an-asset)

<!-- Removing assets-workflow.md file link as it is not applicable anymore. Workflows are replaced by processing profiles.
        * [Creating a version](/help/assets/manage-digital-assets.md#asset-versioning)
        * [Applying workflows to assets](/help/assets/assets-workflow.md) or see [Starting a workflow on an asset](/help/assets/manage-digital-assets.md#starting-a-workflow-on-an-asset)
-->

    * [Révision de ressources situées dans un dossier](/help/assets/bulk-approval.md)
    * [Projets](/help/sites-cloud/authoring/projects/overview.md)

1. Pour **publier les vidéos Dynamic Media**, effectuez l’une des opérations suivantes :

   * Si vous utilisez le Experience Manager comme système de gestion de contenu Web (Gestion de contenu Web), vous pouvez ajouter des vidéos directement à vos pages Web.

      * [Ajout de vidéos à des pages web](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).
   * Si vous utilisez un système de gestion de contenu web tiers, vous pouvez lier ou incorporer des vidéos dans vos pages web.

      * Intégrez une vidéo à l’aide d’une URL :
         [Liaison d’URL à une application web](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md).

      * Intégrez une vidéo à l’aide du code intégré dans la page web :
         [Incorporation de la visionneuse de vidéos dans une page web](/help/assets/dynamic-media/embed-code.md).
   * [Publication de vidéos sur YouTube](#publishing-videos-to-youtube).
   * [Génération de rapports vidéo](#viewing-video-reports).

   * [Ajout de sous-titres à une vidéo](#adding-captions-to-video).



## Utilisation de vidéo dans Dynamic Media  {#working-with-video-in-dynamic-media}

La vidéo à Dynamic Media est une solution de bout en bout qui facilite la publication de vidéos adaptatives de haute qualité pour la diffusion en flux continu sur plusieurs écrans, notamment sur les périphériques mobiles de bureau, iOS, Android™, BlackBerry® et Windows®. Une visionneuse de vidéos adaptative regroupe les versions d’une même vidéo codées dans des débits et des formats différents, tels que 400 kbit/s, 800 kbit/s et 1 000 kbit/s. L’ordinateur de bureau ou le périphérique mobile détecte la bande passante disponible.

Par exemple, sur un appareil mobile iOS, il détecte une bande passante telle que 3G, 4G ou une connexion Wi-Fi, puis sélectionne automatiquement la vidéo codée selon le débit correspondant parmi ceux disponibles dans la visionneuse de vidéos adaptative. La vidéo est diffusée en continu sur les postes de travail, les appareils mobiles ou les tablettes.

En outre, la qualité de la vidéo est automatiquement adaptée en temps réel selon les conditions réseau sur le poste de travail ou l’appareil mobile. En outre, si un client passe en mode plein écran sur un ordinateur de bureau, la visionneuse de vidéos adaptative répond en utilisant une meilleure résolution, améliorant ainsi l’expérience d’affichage du client. L’utilisation des visionneuses de vidéos adaptatives offre une lecture optimale aux clients qui lisent des vidéos Dynamic Media sur plusieurs écrans et appareils.

La logique appliquée par un lecteur vidéo pour déterminer quelles sont les vidéos encodées à lire ou à sélectionner au cours de la lecture repose sur l’algorithme suivant :

1. Le lecteur vidéo charge le fragment vidéo initial basé sur le débit le plus proche de la valeur définie pour le « débit initial » dans le lecteur lui-même.
1. Le lecteur vidéo est adapté en fonction des modifications de la vitesse de bande passante d’après les critères suivants :

   1. Le lecteur sélectionne le flux de bande passante le plus élevé qui est inférieur ou égal à la bande passante estimée.
   1. Le lecteur prend uniquement en compte 80 % de la bande passante disponible. Cependant, s’il change, il est préférable que ce taux soit seulement de 70 % pour éviter toute surestimation et que le lecteur ne repasse au taux précédent.

Pour obtenir des informations techniques détaillées sur l’algorithme, consultez la page [https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/httplive/LiveSession.cpp](https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/httplive/LiveSession.cpp)

Pour la gestion des visionneuses de vidéos adaptative et unique, les fonctions suivantes sont prises en charge :

* Téléchargement de vidéos en différents formats vidéo et audio pris en charge et codage vidéo au format MP4 H.264 pour la lecture sur plusieurs écrans. Vous pouvez utiliser les paramètres prédéfinis de vidéo adaptative ou de codage unique ou personnaliser le codage pour contrôler la qualité et la taille de la vidéo.

   * Lorsqu’une visionneuse de vidéos adaptative est générée, elle comprend des vidéos MP4.
   * **Remarque** : Les vidéos originales/sources ne sont pas ajoutées à la visionneuse de vidéos adaptative.

* Sous-titrage des vidéos dans toutes les visionneuses de vidéo HTML5.
* Organiser, parcourir et effectuer des recherches dans la vidéo avec une prise en charge complète des métadonnées pour une gestion efficace des ressources vidéo.
* Proposez des visionneuses de vidéos adaptatives sur le Web et les ordinateurs de bureau, ainsi que sur les périphériques mobiles, notamment l’iPhone, l’iPad, Android™, BlackBerry® et le téléphone Windows®.

La diffusion de vidéo adaptative en flux continu est prise en charge sur diverses plates-formes iOS. Voir [Guide de référence des visionneuses de médias dynamiques](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/c-html5-video-reference.html?lang=fr).

Dynamic Media prend en charge la lecture vidéo mobile pour la vidéo MP4 H.264. Vous trouverez les périphériques BlackBerry® qui prennent en charge ce format vidéo à l’adresse suivante : [Formats vidéo pris en charge sur BlackBerry®](https://support.blackberry.com/kb/articleDetail?ArticleNumber=000005482).

Vous trouverez les périphériques Windows® qui prennent en charge ce format vidéo à l’adresse suivante : [Formats vidéo pris en charge sur Windows® Phone](https://msdn.microsoft.com/library/windows/apps/ff462087%28v=vs.105%29.aspx)

* Lecture de la vidéo à l’aide des paramètres prédéfinis de la visionneuse Dynamic Media Video, tels que :

   * des visionneuses de vidéos uniques ;
   * des visionneuses de médias mixtes combinant du contenu vidéo et des images.

* Configurer des lecteurs vidéo pour répondre à vos besoins de stratégie de marque.
* Intégrer la vidéo à votre site web, site mobile ou application mobile grâce à une simple URL ou à du code intégré.

Voir l’exemple [Lecture de vidéo dynamique](https://s7d9.scene7.com/s7/uvideo.jsp?asset=GeoRetail/Mop_AVS&amp;config=GeoRetail/Universal_Video1&amp;stageSize=640,480).

Voir aussi [Visionneuses pour les ressources Experience Manager et Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/c-html5-s7-aem-asset-viewers.html?lang=fr#viewers-aem-assets-dmc) et [Visionneuses pour les ressources Experience Manager uniquement](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers.html?lang=fr#viewers-for-aem-assets-only) dans le [Guide de référence des visionneuses Dynamic Media](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/home.html?lang=fr).

## Bonne pratique : Utilisation de la visionneuse de vidéos HTML5 {#best-practice-using-the-html-video-viewer}

Les paramètres prédéfinis de la visionneuse de vidéos HTML5 Dynamic Media sont des lecteurs vidéo fiables. Vous pouvez les utiliser pour éviter de nombreux problèmes courants associés à la lecture vidéo HTML5 et aux problèmes associés aux périphériques mobiles. Par exemple, manque de diffusion de diffusion adaptative en flux continu et portée limitée du navigateur de bureau.

Du côté de la conception du lecteur, vous pouvez concevoir la fonctionnalité du lecteur vidéo à l’aide d’outils de développement Web standard. Vous pouvez, par exemple, concevoir les boutons, les commandes et les affiches personnalisées en arrière-plan au moyen du code HTML5 et CSS afin de mieux cibler les utilisateurs avec un aspect personnalisé.

En ce qui concerne la lecture, la visionneuse, détecte automatiquement les fonctionnalités vidéo du navigateur. Elle traite ensuite la vidéo en utilisant HLS (HTTP Live Streaming), également appelé diffusion en continu de vidéo adaptative. Si ces méthodes de distribution n’existent pas, la diffusion progressive HTML5 est utilisée à la place.

Vous pouvez combiner en un seul lecteur la possibilité de concevoir les composants de lecture à l’aide de code HTML5 et CSS. Il peut être doté d’une lecture intégrée et utiliser la diffusion en flux continu adaptatif et progressive en fonction des capacités du navigateur. Grâce à cette fonctionnalité, vous pouvez étendre la portée de votre contenu multimédia aux utilisateurs de bureau et mobiles et garantir une expérience vidéo rationalisée.

Voir aussi [Visionneuses pour ressources Experience Manager uniquement](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers.html#viewers-for-aem-assets-only) dans le [Guide de référence des visionneuses Dynamic Media](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/home.html).

### Lecture vidéo sur les ordinateurs de bureau et les appareils mobiles à l’aide de la visionneuse de vidéos HTML5  {#playback-of-video-on-desktop-computers-and-mobile-devices-using-the-html-video-viewer}

Pour la diffusion en flux continu de la vidéo adaptative sur un poste de travail et un appareil mobile, les vidéos utilisées pour le changement de débit reposent sur toutes les vidéos MP4 dans la visionneuse de vidéos adaptative.

La lecture vidéo se produit à l’aide d’un téléchargement vidéo HLS ou progressif. Dans les versions antérieures du Experience Manager, telles que 6.0, 6.1 et 6.2, les vidéos étaient diffusées en flux continu sur HTTP.

Cependant, dans Experience Manager 6.3 et versions ultérieures, les vidéos sont désormais diffusées en flux continu via HTTPS (c&#39;est-à-dire HLS), car l&#39;URL du service de passerelle DM utilise également le protocole HTTPS. Ce comportement par défaut n’a aucun impact sur les clients. Autrement dit, la diffusion en continu de vidéo s’effectuera tout de même via HTTPS, à moins qu’elle ne soit pas prise en charge par le navigateur (voir le tableau ci-dessous). Par conséquent,

* Si vous avez un site web HTTPS avec une diffusion vidéo en continu via HTTPS, la diffusion en continu est de qualité.
* Si vous avez un site web HTTP avec une diffusion vidéo en flux continu via HTTPS, la diffusion en continu est de qualité et il n’y a aucun problème de contenu mixte du navigateur web.

HLS est une norme d’Apple pour la diffusion de vidéo adaptative en continu qui ajuste automatiquement la lecture en fonction de la capacité de bande passante du réseau. Elle permet aussi au client de « rechercher » n’importe quel point de la vidéo sans avoir à attendre que le reste de la vidéo soit téléchargé.

La vidéo progressive est fournie grâce au téléchargement et à l’enregistrement de la vidéo en local sur le système du poste de travail ou de l’appareil mobile de l’utilisateur.

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
   <td>Internet Explorer 9 et 10</td>
   <td>Téléchargement progressif.</td>
  </tr>
  <tr>
   <td>Poste de travail</td>
   <td>Internet Explorer 11+</td>
   <td>Sous Windows® 8 et Windows® 10 - Forcer l'utilisation du protocole HTTPS chaque fois que HLS est demandé. Limite connue : HTTP sur HLS ne fonctionne pas dans cette combinaison navigateur/système d’exploitation<br /> <br /> Sous Windows® 7 - Téléchargement progressif. Utilise la logique standard pour sélectionner le protocole HTTP ou HTTPS.</td>
  </tr>
  <tr>
   <td>Poste de travail</td>
   <td>Firefox 23 à 44</td>
   <td>Téléchargement progressif.</td>
  </tr>
  <tr>
   <td>Poste de travail</td>
   <td>Firefox 45 ou version ultérieure</td>
   <td>HLS</td>
  </tr>
  <tr>
   <td>Poste de travail</td>
   <td>Chrome</td>
   <td>HLS</td>
  </tr>
  <tr>
   <td>Poste de travail</td>
   <td>Safari (Mac)</td>
   <td>HLS</td>
  </tr>
  <tr>
   <td>Mobile</td>
   <td>Chrome (Android™ 6 ou version antérieure)</td>
   <td>Téléchargement progressif.</td>
  </tr>
  <tr>
   <td>Mobile</td>
   <td>Chrome (Android™ 7 ou version ultérieure)</td>
   <td>HLS</td>
  </tr>
  <tr>
   <td>Mobile</td>
   <td>Android™ (navigateur par défaut)</td>
   <td>Téléchargement progressif.</td>
  </tr>
  <tr>
   <td>Mobile</td>
   <td>Safari (iOS)</td>
   <td>HLS</td>
  </tr>
  <tr>
   <td>Mobile</td>
   <td>Chrome (iOS)</td>
   <td>HLS</td>
  </tr>
  <tr>
   <td>Mobile</td>
   <td>BlackBerry®</td>
   <td>HLS</td>
  </tr>
 </tbody>
</table>

## Architecture de la solution vidéo Dynamic Media  {#architecture-of-dynamic-media-video-solution}

Le graphique suivant montre le workflow global de création de vidéos qui sont chargées et codées par le biais de DMGateway (dans le mode Hybride Dynamic Media) et mises à disposition pour une consommation publique.

![chlimage_1-427](assets/chlimage_1-427.png)

## Architecture de publication hybride des vidéos {#hybrid-publishing-architecture-for-videos}

![chlimage_1-428](assets/chlimage_1-428.png)

## Bonnes pratiques en matière de codage de vidéos {#best-practices-for-encoding-videos}

Le flux de travail **Dynamic Media Encode Video** code la vidéo si vous avez activé Dynamic Media et configuré des Cloud Services vidéo. Ce workflow capture l’historique de traitement des workflows et les informations d’échec. Voir [Surveillance du codage vidéo et de la progression de la publication sur YouTube](#monitoring-video-encoding-and-youtube-publishing-progress). Si vous avez activé Dynamic Media et configuré des Cloud Services vidéo, le flux de travail **[!UICONTROL Dynamic Media Encode Video]** prend automatiquement effet lorsque vous téléchargez une vidéo. (Si vous n’utilisez pas Dynamic Media, le processus **[!UICONTROL DAM Update Asset]** prend effet.)

Vous trouverez ci-dessous quelques conseils sur les bonnes pratiques de codage des fichiers source vidéo.

Pour obtenir plus de conseils sur le codage vidéo, voir :

* [Streaming 101: The Basics — Codecs, Bandwidth, Data Rate, and Resolution (« Diffusion en continu : notions fondamentales – codecs, bande passante, débit de données et résolution »)](https://www.adobe.com/go/learn_s7_streaming101_fr).
* [Video Encoding Basics](https://www.adobe.com/go/learn_s7_encoding_en).

### Fichiers vidéo source {#source-video-files}

Lorsque vous codez un fichier vidéo, utilisez un fichier vidéo source ayant la plus haute qualité possible. Évitez d’utiliser des fichiers vidéo précédemment codés, car ces fichiers sont déjà compressés, et un codage supplémentaire crée une vidéo de qualité inférieure.

Le tableau suivant décrit la taille recommandée, le format et le débit minimal requis pour vos fichiers vidéo source avant de les coder :

| Taille | Format | Débit minimal |
|--- |--- |--- |
| 1024 x 768 | 4:3 | 4 500 Kbit/s pour la plupart des vidéos. |
| 1280 x 720 | 16:9 | 3 000 à 6 000 Kbit/s, selon la quantité de mouvement dans la vidéo. |
| 1 920 x 1 080 | 16:9 | 6 000 à 8 000 kbit/s en fonction de la quantité de mouvement sur la vidéo. |

### Obtention des métadonnées d’un fichier {#obtaining-a-file-s-metadata}

Vous pouvez obtenir les métadonnées d’un fichier en les affichant à l’aide d’un outil d’édition vidéo ou d’une application d’extraction de métadonnées. Voici les instructions d’utilisation de MediaInfo, une application tierce permettant d’extraire les métadonnées d’un fichier vidéo :

1. Visitez cette page web : [https://mediainfo.sourceforge.net/en/Download](https://mediainfo.sourceforge.net/en/Download).
1. Sélectionnez et téléchargez le programme d’installation pour la version avec interface graphique utilisateur, puis suivez les instructions d’installation.
1. Après l’installation, cliquez avec le bouton droit sur le fichier vidéo (Windows® uniquement) et sélectionnez MediaInfo ou ouvrez MediaInfo et faites glisser votre fichier vidéo dans l’application. Toutes les métadonnées associées à votre fichier vidéo, y compris sa largeur, sa hauteur et ses images par seconde, s’affichent.

### Format {#aspect-ratio}

Lorsque vous choisissez ou créez un paramètre prédéfini de codage vidéo pour votre fichier vidéo issu de sources originales, assurez-vous que le paramètre prédéfini indique le même format que le fichier vidéo issu de sources originales. Le format fait référence au rapport largeur/hauteur de la vidéo.

Pour déterminer le format d’un fichier vidéo, récupérez les métadonnées de ce fichier et notez les valeurs de largeur et de hauteur (voir la section Obtention des métadonnées d’un fichier ci-dessus). Utilisez ensuite cette formule pour déterminer le format :

largeur/hauteur = format

Ce tableau décrit la façon dont les résultats de la formule se traduisent en choix de formats :

| Résultat de la formule | Format |
|--- |--- |
| 1.33 | 4:3 |
| 0,75 | 3:4 |
| 1,78 | 16:9 |
| 0.56 | 9:16 |

Par exemple, une vidéo de 1 440 largeur x 1 080 hauteur a un rapport L/H de 1 440/1 080, ou 1,33. Dans ce cas, vous choisissez un paramètre prédéfini de codage vidéo avec un rapport L/H de 4:3 pour coder le fichier vidéo.

### Débit binaire  {#bitrate}

Le débit correspond à la quantité de données encodées pour produire une seule seconde de lecture vidéo. Le débit de données est mesuré en kilobits par seconde (kbit/s).

>[!NOTE]
>
>Du fait que tous les codecs utilisent la compression avec perte, le débit de données est le facteur le plus important de la qualité vidéo. Quand vous utilisez la compression avec perte, plus vous compressez la vidéo, plus la qualité de l’image se dégrade. Toutes les autres caractéristiques étant égales (résolution, taux de rafraîchissement et codec), plus le débit de données est faible, moins la qualité du fichier compressé est bonne.

Lorsque vous sélectionnez l’encodage du débit, vous avez le choix entre deux types :

* **[!UICONTROL Codage]**  de débit constant (CBR) : pendant le codage CBR, le débit, ou le nombre de bits par seconde, est conservé de la même manière tout au long du processus de codage. L’encodage CBR maintient le débit défini selon votre configuration sur l’intégralité de la vidéo. En outre, le codage CBR n’optimise pas la qualité des fichiers multimédias, mais économise de l’espace de stockage.
 Utilisez le codage CBR si votre vidéo présente globalement un niveau de mouvement similaire. Le codage CBR est le plus souvent utilisé pour diffuser le contenu vidéo en continu. Voir également [Utilisation de paramètres de codage vidéo personnalisés](/help/assets/dynamic-media/video-profiles.md#using-custom-added-video-encoding-parameters).

* **[!UICONTROL Codage de débit variable]** (VBR) : le codage VBR ajuste le débit en le diminuant et selon la limite supérieure que vous avez définie, en fonction des données demandées par le compresseur. Cette fonctionnalité signifie que, lors d&#39;un processus de codage VBR, le débit du fichier multimédia augmente ou diminue dynamiquement en fonction des besoins de débit des fichiers multimédias.
Le VBR prend plus de temps au codage, mais garantit de meilleurs résultats, avec une qualité de fichier multimédia supérieure. Le codage VBR est couramment utilisé pour la diffusion http progressive de contenu vidéo.

Quand utilisez-vous VBR par rapport à CRB ?
Lorsque vous sélectionnez VBR ou CBR, il est presque toujours recommandé d&#39;utiliser VBR pour vos fichiers multimédias. VBR fournit des fichiers de meilleure qualité à des débits concurrentiels. Lorsque vous utilisez le VBR, assurez-vous d’utiliser le codage à deux passages, et définissez le débit maximal afin qu’il soit 1,5 fois supérieur au débit vidéo cible.

Lorsque vous choisissez un paramètre prédéfini de codage vidéo, veillez à tenir compte de la vitesse de connexion de l’utilisateur final de la cible. Choisissez un paramètre prédéfini avec un débit de données correspondant à 80 % de cette vitesse. Par exemple, si la vitesse de connexion de l’utilisateur final est de 1 000 kbit/s, le meilleur paramètre prédéfini est celui qui comprend un débit vidéo de 800 kbit/s.

Ce tableau décrit le débit de données associé à des vitesses de connexion courantes.

| Vitesse (kbit/s) | Type de connexion |
|--- |--- |
| 256 | Connexion d’accès à distance. |
| 800 | Connexion mobile standard. Pour cette connexion, visez un débit de données de 400 à 800 kbit/s pour les expériences 3G. |
| 2000 | Connexion haut débit standard de bureau. Pour cette connexion, visez un débit de données de 800 à 2 000 kbit/s, bien qu’un débit de 1 200 à 1 500 kbit/s convienne à la plupart des cibles. |
| 5 000 | Connexion haut débit standard. Il est déconseillé de coder dans cette plage supérieure, car la diffusion de la vidéo à cette vitesse n’est pas possible pour la plupart des consommateurs. |

### Résolution {#resolution}

La **résolution** décrit la hauteur et la largeur d’un fichier vidéo, exprimée en pixels. La plupart des vidéos sources sont stockées à une résolution élevée (par exemple, 1 920 x 1 080). À des fins de diffusion en flux continu, la vidéo source est compressée à une résolution inférieure (640 x 480, voire moins).

La résolution et le débit de données sont deux facteurs étroitement liés qui déterminent la qualité de la vidéo. Pour maintenir la même qualité vidéo, plus le nombre de pixels (c’est-à-dire la résolution) est élevé dans un fichier vidéo, plus le débit de données doit l’être également. Par exemple, considérez le nombre de pixels par image dans un fichier vidéo d’une résolution de 320 x 240 pixels et dans un fichier vidéo d’une résolution de 640 x 480 pixels :

| Résolution | Pixels par image |
|--- |--- |
| 320 x 240 | 76 800 |
| 640 x 480 | 307 200 |

Le fichier de 640 x 480 possède quatre fois plus de pixels par image. Pour atteindre le même débit de données avec ces deux résolutions, vous appliquez une compression de 4 au fichier d’une résolution de 640 x 480 pixels, ce qui peut réduire la qualité de la vidéo. Par conséquent, un débit de données vidéo de 250 kbit/s produit un affichage de haute qualité à une résolution de 320 x 240 pixels, mais pas à une résolution de 640 x 480 pixels.

En règle générale, plus le débit de données est élevé, plus la vidéo est belle et plus la résolution utilisée est élevée, plus le débit de données doit rester élevé (par rapport aux résolutions inférieures).

Du fait que la résolution et le débit de données sont liés, vous avez le choix entre deux options lors du codage vidéo :

* Choisir un débit de données puis, en fonction de ce paramètre, coder à la résolution la plus haute pour obtenir une vidéo de bonne qualité.
* Choisir une résolution, puis coder au débit de données nécessaire pour que la qualité vidéo soit optimale à la résolution choisie.

Lorsque vous choisissez (ou créez) un paramètre prédéfini de codage vidéo pour votre fichier vidéo source original, utilisez ce tableau pour choisir la résolution cible appropriée :

| Résolution | Hauteur (pixels) | Taille d’écran |
|--- |--- |--- |
| 240p | 240 | Écran de très petite taille |
| 300p | 300 | Petit écran équipant généralement les appareils mobiles |
| 360p | 360 | Petit écran |
| 480p | 480 | Écran de taille moyenne |
| 720p | 720 | Grand écran |
| 1 080p | 1080 | Grand écran haute définition |

### Images par seconde {#fps-frames-per-second}

Aux États-Unis et au Japon, la plupart des vidéos sont tournées à 29,97 ips (images par seconde) ; en Europe, la plupart des vidéos le sont à 25 ips. Un film est tourné à 24 ips.

Choisissez un paramètre prédéfini de codage vidéo correspondant au nombre d’images par seconde de votre vidéo issue de sources originales. Par exemple, si le débit est de 25 ips pour la vidéo issue de sources originales, choisissez un paramètre prédéfini de 25 ips pour le codage. Par défaut, tous les codages personnalisés utilisent le nombre d’images par seconde de la vidéo issue de sources originales. C’est pourquoi il est inutile d’indiquer le nombre d’images par seconde lorsque vous créez un paramètre prédéfini de codage vidéo.

### Dimensions du codage vidéo {#video-encoding-dimensions}

Pour obtenir des résultats optimaux, sélectionnez les dimensions de codage de façon à ce que la vidéo source corresponde à un multiple entier de toutes vos vidéos codées.

Pour ce faire, il suffit de diviser la largeur de la source par la largeur codée pour obtenir le rapport de largeur, puis de diviser la hauteur de la source par la hauteur codée pour obtenir le rapport de hauteur.

Si le résultat est un nombre entier, cela signifie que la mise à l’échelle de la vidéo est parfaite. Si le résultat n’est pas un nombre entier, la qualité vidéo s’en ressentira en raison de la présence d’artefacts vidéo (pixels résiduels). Cet effet est plus visible lorsque la vidéo contient du texte.

Supposons, par exemple, que la résolution de votre vidéo source soit équivalente à 1920 x 1080 pixels. Dans le tableau ci-après, les trois vidéos codées indiquent les paramètres de codage optimaux à appliquer.

| Type de vidéo | Largeur x hauteur | Rapport de largeur | Rapport de hauteur |
|--- |--- |--- |--- |
| Source | 1 920 x 1 080 | 1 | 1 |
| Codée | 960 x 540 | 2 | 2 |
| Codée | 640 x 360 | 3 | 3 |
| Codée | 480 x 270 | 4 | 4 |

### Format de fichier vidéo codé {#encoded-video-file-format}

Dynamic Media recommande d’utiliser les paramètres prédéfinis MP4 H.264 de codage vidéo. Comme les fichiers MP4 utilisent le codec vidéo H.264, la vidéo est de haute qualité mais dans un fichier au volume compressé.

## Publication de vidéos sur YouTube  {#publishing-videos-to-youtube}

Vous pouvez publier des fichiers vidéo gérés dans les ressources du Experience Manager directement sur un canal YouTube que vous avez précédemment créé.

Pour publier des fichiers vidéo sur YouTube, vous devez baliser des fichiers vidéo dans des fichiers Experience Manager avec des balises. Vous associez ces balises à une chaîne YouTube. Si la balise d’une ressource vidéo correspond à la balise d’une chaîne YouTube, la vidéo est publiée sur YouTube. La publication sur YouTube se produit avec une publication normale de la vidéo à condition qu’une balise associée soit utilisée.

YouTube procède à son propre codage. Ainsi, le fichier vidéo d’origine téléchargé dans le Experience Manager est publié sur YouTube au lieu de tout rendu vidéo créé par le codage de Dynamic Media. Bien qu’il ne soit pas nécessaire de traiter les vidéos à l’aide de Dynamic Media, il est normal qu’elles le fassent au cas où un paramètre prédéfini de visionneuse serait nécessaire pour la lecture.

Lorsque vous ignorez le profil de traitement de la vidéo et publiez directement sur YouTube, cela signifie simplement que votre fichier vidéo dans le fichier Experience Manager n’obtient pas de miniature affichable. Cela signifie également que les vidéos qui ne sont pas codées ne fonctionnent avec aucun des types de ressources Dynamic Media.

Pour garantir une authentification serveur à serveur sécurisée avec YouTube, la publication des vidéos sur les serveurs YouTube implique les tâches suivantes :

1. [Configuration des paramètres de Google Cloud](#configuring-google-cloud-settings)
1. [Création d’une chaîne YouTube](#creating-a-youtube-channel)
1. [Ajout de balises pour la publication](#adding-tags-for-publishing)
1. [Setting up YouTube in Experience Manager](#setting-up-youtube-in-aem)
1. [(Facultatif) Automatisation de la définition des propriétés YouTube par défaut pour vos vidéos chargées](#optional-automating-the-setting-of-default-youtube-properties-for-your-uploaded-videos)
1. [Publication de vidéos sur votre chaîne YouTube](#publishing-videos-to-your-youtube-channel)
1. [(Facultatif) Vérification de la vidéo publiée sur YouTube](/help/assets/dynamic-media/video.md#optional-verifying-the-published-video-on-youtube)
1. [Liaison d’URL YouTube à une application web](#linking-youtube-urls-to-your-web-application)

Vous pouvez également [annuler la publication de vidéos pour les supprimer de YouTube](#unpublishing-videos-to-remove-them-from-youtube).

### Configuration des paramètres de Google Cloud  {#configuring-google-cloud-settings}

Pour effectuer une publication sur YouTube, vous avez besoin d’un compte Google. Si vous disposez d’un compte GMAIL, vous disposez déjà d’un compte Google ; si vous n&#39;avez pas de compte Google, vous pouvez facilement en créer un. Un compte est nécessaire, car vous avez besoin des informations d’identification pour publier des ressources vidéo sur YouTube. Si vous avez déjà créé un compte, ignorez cette tâche et passez directement à [Création d’une chaîne YouTube](#creating-a-youtube-channel).

Il n’est pas nécessaire que le compte utilisé avec Google Cloud et le compte Google utilisé pour YouTube soient les mêmes.

Google modifie régulièrement son interface utilisateur. Les étapes de publication des vidéos sur YouTube peuvent donc légèrement varier par rapport à ce qui est décrit ci-dessous. Cet avertissement s’applique également à YouTube lorsque vous tentez de vérifier si des vidéos y sont téléchargées.

>[!NOTE]
>
>Les étapes suivantes étaient exactes au moment de leur rédaction. Toutefois, Google met à jour régulièrement ses sites web sans préavis. Ces étapes peuvent donc être légèrement différentes.

Pour configurer les paramètres de Google Cloud, procédez comme suit :

1. Créez un compte Google.
   [https://accounts.google.com/SignUp?service=mail](https://accounts.google.com/SignUp?service=mail)

   Si vous disposez déjà d’un compte Google, passez à l’étape suivante.

1. Accédez à [https://cloud.google.com/](https://cloud.google.com/).
1. Dans la page Google Cloud, près du coin supérieur droit, cliquez sur **[!UICONTROL Console]**.

   Si nécessaire, **[!UICONTROL connectez-vous]** en utilisant vos informations d’identification de compte Google pour voir l’option **[!UICONTROL Console]**.

1. Sur la page Tableau de bord, à droite de **[!UICONTROL Google Cloud Platform]**, cliquez sur la liste déroulante Projet pour ouvrir la boîte de dialogue Sélectionner un projet.
1. Dans la boîte de dialogue Sélectionner un projet, appuyez sur **[!UICONTROL Nouveau projet]**.

   ![6_5_googleaccount-newproject](assets/6_5_googleaccount-newproject.png)

1. Dans la boîte de dialogue Nouveau projet, saisissez le nom de votre nouveau projet dans le champ Nom du projet.

   Votre ID de projet est basé sur le nom du projet. Par conséquent, choisissez soigneusement le nom du projet ; il ne peut pas être modifié une fois créé. En outre, vous devez saisir à nouveau le même ID de projet lorsque vous configurez YouTube en Experience Manager ultérieurement. Par conséquent, écrivez-le.

1. Cliquez sur **[!UICONTROL Créer]**.

1. Effectuez l’une des opérations suivantes :

   * Dans le tableau de bord de votre projet, dans la carte Prise en main, appuyez sur **[!UICONTROL Explorer et activer les API]**.
   * Dans le tableau de bord de votre projet, dans la carte API, appuyez sur **[!UICONTROL Accéder à l’aperçu des API]**.

   ![6_5_googleaccount-apis-enable2](assets/6_5_googleaccount-apis-enable2.png)

1. En haut de la page API &amp; services, appuyez sur **[!UICONTROL Activer les API et les services]**.
1. Sur la page Bibliothèque d’API, dans la partie gauche, sous **[!UICONTROL Catégorie]**, appuyez sur **[!UICONTROL YouTube]**. Sur le côté droit de la page, appuyez sur **[!UICONTROL YouTube Data API]**.
1. Sur la page YouTube Data API v3, appuyez sur **[!UICONTROL Activer]**.

   ![6_5_googleaccount-apis-enable3](assets/6_5_googleaccount-apis-enable3.png)

1. Pour utiliser l’API, vous devez disposer des informations d’identification. Si besoin, cliquez sur **[!UICONTROL Créer des identifiants]**.

   ![6_5_googleaccount-apis-createcredentials](assets/6_5_googleaccount-apis-createcredentials.png)

1. Sur la page **[!UICONTROL Ajouter des identifiants au projet]**, à l’étape 1, procédez comme suit :

   * Dans la liste déroulante **[!UICONTROL Quelle API utilisez-vous ?]**, sélectionnez **[!UICONTROL YouTube Data API v3]**.

   * À partir de **[!UICONTROL D&#39;où appelez-vous l&#39;API ?]** liste déroulante, sélectionnez Serveur  **[!UICONTROL Web (par exemple, node.js, Tomcat)]**.

   * À partir de **[!UICONTROL Quelles données accédez-vous ?]**, appuyez sur **[!UICONTROL Données utilisateur]**.

   ![6_5_googleaccount-apis-createcredentials2](assets/6_5_googleaccount-apis-createcredentials2.png)

1. Appuyez sur **[!UICONTROL De quels identifiants ai-je besoin ?]**
1. Sur la page **[!UICONTROL Ajouter des identifiants au projet]**, à l’étape 2, sous l’en-tête **[!UICONTROL Créer un ID client OAuth 2.0]**, dans le champ Nom, saisissez un nom unique si vous le souhaitez. Vous pouvez également utiliser le nom par défaut spécifié par Google.
1. Sous l’en-tête **[!UICONTROL origines JavaScript™ autorisées]**, dans le champ de texte, saisissez le chemin suivant, en substituant votre propre domaine et numéro de port dans le chemin, puis appuyez sur **[!UICONTROL Entrée]** pour ajouter le chemin à la liste :

   `https://<servername.domain>:<port_number>`

   Par exemple, `https://1a2b3c.mycompany.com:4321`

   **Remarque :** L’exemple du chemin ci-dessus est fourni uniquement à titre illustratif.

   ![6_5_googleaccount-apis-createcredentials-oauth](assets/6_5_googleaccount-apis-createcredentials-oauth.png)

1. Dans le champ de texte sous l’en-tête **[!UICONTROL URI de redirection autorisés]**, saisissez le chemin suivant, en substituant vos propres domaine et numéro de port dans le chemin, puis appuyez sur **[!UICONTROL Entrée]** pour ajouter le chemin à la liste :

   `https://<servername.domain>:<port_number>/etc/cloudservices/youtube.youtubecredentialcallback.json`

   Par exemple, `https://1a2b3c.mycompany.com:4321/etc/cloudservices/youtube.youtubecredentialcallback.json`

   **Remarque :** L’exemple du chemin ci-dessus est fourni uniquement à titre illustratif.

1. Cliquez sur **[!UICONTROL Créer un ID client OAuth]**.
1. Sur la page **[!UICONTROL Ajouter des identifiants au projet]**, à l’étape 3, sous l’en-tête **[!UICONTROL Configuration de l’écran d’autorisation OAuth 2.0]**, sélectionnez l’adresse e-mail Gmail que vous utilisez actuellement.

   ![6_5_googleaccount-apis-createcredentials-consentscreen](assets/6_5_googleaccount-apis-createcredentials-consentscreen.png)

1. Sous l’en-tête **[!UICONTROL Nom du produit affiché à l’intention des utilisateurs]**, dans le champ de texte, entrez ce qui doit s’afficher sur l’écran d’autorisation.

   L’écran de consentement s’affiche pour l’administrateur du Experience Manager lorsqu’il s’authentifie sur YouTube. Le Experience Manager contacte YouTube pour obtenir sa permission.

1. Cliquez sur **[!UICONTROL Continuer]**.
1. Sur la page Ajouter des identifiants au projet, à l’étape 4, sous l’en-tête **[!UICONTROL Télécharger les identifiants]**, appuyez sur **[!UICONTROL Télécharger]**.

   ![6_5_googleaccount-apis-createcredentials-downloadcredentials](assets/6_5_googleaccount-apis-createcredentials-downloadcredentials.png)

1. Enregistrez le fichier `client_id.json`.

   Vous aurez besoin de ce fichier json téléchargé lorsque vous configurerez YouTube dans Adobe Experience Manager ultérieurement.

1. Cliquez sur **[!UICONTROL Terminé]**.

   Déconnectez-vous de votre compte Google. Créez maintenant un canal YouTube.

### Création d’une chaîne YouTube {#creating-a-youtube-channel}

Pour publier des vidéos sur YouTube, vous devez disposer d’une ou de plusieurs chaînes. Si vous avez déjà créé une chaîne YouTube, vous pouvez ignorer cette étape et passer à la tâche [Ajout de balises pour la publication](/help/assets/dynamic-media/video.md#adding-tags-for-publishing).

>[!CAUTION]
>
>Assurez-vous d’avoir déjà configuré un ou plusieurs canaux dans YouTube *avant* d’ajouter des canaux sous Paramètres YouTube en Experience Manager (voir [Configuration de YouTube en Experience Manager](#setting-up-youtube-in-aem) ci-dessous). Si vous ne parvenez pas à configurer le canal, vous n&#39;êtes pas averti de l&#39;absence de canaux existants. L’authentification Google a lieu lorsque vous ajoutez une chaîne, mais il n’existe pas d’option permettant de choisir la chaîne vers laquelle la vidéo est envoyée.

Pour créer une chaîne YouTube :

1. Accédez à [https://www.youtube.com](https://www.youtube.com/), puis connectez-vous à l’aide des informations d’identification de votre compte Google.
1. Dans le coin supérieur droit de la page YouTube, cliquez sur votre image de profil (elle peut également apparaître sous la forme d’une lettre dans un cercle de couleur unie), puis cliquez sur **[!UICONTROL Paramètres YouTube]** (icône d’engrenage arrondi).
1. Sur la page Présentation, sous l’en-tête Fonctionnalités supplémentaires, cliquez sur **[!UICONTROL Voir toutes mes chaînes ou créer une nouvelle chaîne]**.
1. Depuis la page Chaînes, cliquez sur **[!UICONTROL Créer une chaîne]**.
1. Sur la page Compte de marque, dans le champ nom du compte de marque, saisissez un nom d’entité professionnelle ou tout autre nom de chaîne de votre choix sous lequel vous souhaitez publier vos ressources vidéo, puis cliquez sur **[!UICONTROL Créer]**.

   Rappelez-vous le nom que vous saisissez ici car vous devez le saisir de nouveau lorsque vous configurez YouTube en Experience Manager.

1. (Facultatif) Si nécessaire, ajoutez d’autres chaînes.

   Vous ajoutez maintenant des balises pour la publication.

### Ajout de balises pour la publication {#adding-tags-for-publishing}

Pour publier sur vos vidéos sur YouTube, le Experience Manager associe des balises à un ou plusieurs canaux YouTube. Pour ajouter des balises pour la publication, voir [Administration des balises](/help/sites-cloud/authoring/features/tags.md).

Ou, si vous avez l’intention d’utiliser les balises par défaut en Experience Manager, vous pouvez ignorer cette tâche et accéder à [Configuration de YouTube en Experience Manager](#setting-up-youtube-in-aem).

>[!NOTE]
>
>Une fois le Cloud Service configuré, aucune autre configuration n’est nécessaire pour activer l’agent de réplication de publication YouTube à ce stade. La raison en est qu&#39;il a été activé lors de l&#39;enregistrement de la configuration du Cloud Service.

<!-- ### Enabling the YouTube Publish replication agent {#enabling-the-youtube-publish-replication-agent}

After you enable the YouTube Publish replication agent, if you want to test the connection to the Google Cloud account, tap **[!UICONTROL Test Connection]**. A browser tab displays the connection results. If you have added YouTube Channels, then a listing of those is displayed as part of the test.

1. In the upper-left corner of Experience Manager, click the Experience Manager logo, then in the left rail, click **[!UICONTROL Tools]** &gt; **[!UICONTROL Deployment]** &gt; **[!UICONTROL Replication]** &gt; **[!UICONTROL Agents on Author]**.
1. On the Agents of Author page, click **[!UICONTROL YouTube Publish (youtube)]**.
1. On the toolbar, to the right of Settings, click **[!UICONTROL Edit]**.
1. Select the **[!UICONTROL Enabled]** checkbox to turn on the replication agent.
1. Click **[!UICONTROL OK]**. -->

### Setting up YouTube in Experience Manager {#setting-up-youtube-in-aem}

A compter de la version 6.4 de Experience Manager, une nouvelle méthode d’interface utilisateur tactile a été introduite pour configurer la publication YouTube en Experience Manager. Selon l’instance installée du Experience Manager que vous utilisez, effectuez l’une des opérations suivantes :

* Pour configurer YouTube en Experience Manager avant la version 6.4, voir [Configuration de YouTube en Experience Manager avant la version 6.4](/help/assets/dynamic-media/video.md#setting-up-youtube-in-aem-before).
* Pour configurer YouTube dans le Experience Manager 6.4 ou version ultérieure, voir [Configuration de YouTube dans le Experience Manager 6.4 et version ultérieure](#setting-up-youtube-in-aem-and-later).

#### Configuration de YouTube dans le Experience Manager 6.4 et versions ultérieures {#setting-up-youtube-in-aem-and-later}

1. Veillez à vous connecter à votre instance Dynamic Media en tant qu’administrateur.
1. Dans le coin supérieur gauche du Experience Manager, appuyez sur le logo du Experience Manager, puis, dans le rail de gauche, appuyez sur **[!UICONTROL Outils]**(icône en forme de marteau) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Configuration de publication YouTube]**.
1. Appuyez sur **[!UICONTROL global]** (sans sélectionner cette option).

1. Dans le coin supérieur droit de la page Global, appuyez sur **[!UICONTROL Créer]**.
1. Sur la page Créer une configuration YouTube, sous Paramètres de plateforme Google Cloud, dans le champ **[!UICONTROL Nom de l’application]**, saisissez l’ID de projet Google.

   Vous avez spécifié l’ID de projet lorsque vous avez précédemment configuré les paramètres de Google Cloud.
Laissez la page Créer une configuration YouTube ouverte ; vous y reviendrez dans un instant.

   ![6_5_youtubepublish-createyoutubeconfiguration](assets/6_5_youtubepublish-createyoutubeconfiguration.png)

1. À l’aide d’un éditeur de texte brut, ouvrez le fichier JSON que vous avez téléchargé et enregistré au cours de la tâche [Configuration des paramètres de Google Cloud](/help/assets/dynamic-media/video.md#configuring-google-cloud-settings).
1. Sélectionnez l’intégralité du texte JSON et copiez-le.
1. Revenez à la boîte de dialogue Paramètres du compte YouTube. Dans le champ **[!UICONTROL Configuration JSON]**, collez le texte JSON.
1. Dans le coin supérieur droit de la page, appuyez sur **[!UICONTROL Enregistrer]**.

   Vous allez maintenant configurer des canaux YouTube en Experience Manager.

1. Appuyez sur **[!UICONTROL Ajouter un canal]**.
1. Dans la boîte de dialogue Paramètres de chaîne, saisissez le nom de la chaîne que vous avez créée lors de la tâche **[!UICONTROL Ajout d’une ou plusieurs chaînes YouTube]** précédemment.

   Vous pouvez éventuellement ajouter une description.

1. Appuyez sur **[!UICONTROL Ajouter]**.
1. L’authentification YouTube/Google s’affiche. Si vous n’êtes pas déjà connecté à un compte Google Cloud, ignorez cette étape.

   * Saisissez le nom d’utilisateur Google et le mot de passe associés à l’ID de projet Google et au texte JSON ci-dessus.
   * Selon le nombre de chaînes associées à votre compte, deux éléments au moins sont affichés. Sélectionnez une chaîne. Ne sélectionnez pas l’adresse e-mail, car il ne s’agit pas d’une chaîne.
   * Dans la page suivante, appuyez sur **[!UICONTROL Accepter]** pour autoriser l’accès à cette chaîne.

1. Appuyez sur **[!UICONTROL Autoriser]**.

   Vous allez maintenant configurer des balises pour la publication.

1. **[!UICONTROL Configuration de balises pour la publication]** : sur la page Services cloud > YouTube, appuyez sur l’icône en forme de crayon pour modifier la liste des balises que vous souhaitez utiliser.
1. Pour afficher la liste des balises disponibles dans le Experience Manager, appuyez sur l’icône de liste déroulante (insertion dans le caret).
1. Pour les ajouter, appuyez sur une ou plusieurs balises.

   Pour supprimer une balise que vous avez ajoutée, sélectionnez-la et appuyez sur **[!UICONTROL X]**.

1. Lorsque vous avez terminé d’ajouter les balises souhaitées, appuyez sur **[!UICONTROL Enregistrer]**.

   Vous allez à présent publier des vidéos sur votre chaîne YouTube.

#### Configuration de YouTube en Experience Manager avant la version 6.4 {#setting-up-youtube-in-aem-before}

1. Veillez à vous connecter à votre instance Dynamic Media en tant qu’administrateur.

1. Dans le coin supérieur gauche du Experience Manager, appuyez sur le logo du Experience Manager, puis, dans le rail de gauche, appuyez sur **[!UICONTROL Outils]** (icône en forme de marteau) > **[!UICONTROL Déploiement]** > **[!UICONTROL Cloud Services]**.
1. Sous l’en-tête Services tiers, sous YouTube, appuyez sur **[!UICONTROL Configurer maintenant]**.
1. Dans la boîte de dialogue Créer une configuration, saisissez un titre (obligatoire) et un nom (facultatif) dans les champs correspondants.
1. Appuyez sur **[!UICONTROL Créer]**.
1. Dans la boîte de dialogue Paramètres du compte YouTube, dans le champ **[!UICONTROL Nom de l’application]**, saisissez l’ID de projet Google.

   Vous avez spécifié l’ID de projet lorsque vous avez précédemment [configuré les paramètres de Google Cloud](/help/assets/dynamic-media/video.md#configuring-google-cloud-settings).
Laissez la boîte de dialogue Paramètres du compte YouTube ouverte ; vous y reviendrez dans un instant.

1. À l’aide d’un éditeur de texte brut, ouvrez le fichier JSON que vous avez téléchargé et enregistré au cours de la tâche Configuration des paramètres de Google Cloud.
1. Sélectionnez l’intégralité du texte JSON et copiez-le.
1. Revenez à la boîte de dialogue Paramètres du compte YouTube. Dans le champ **[!UICONTROL Configuration JSON]**, collez le texte JSON.
1. Appuyez sur **[!UICONTROL OK]**.

   Vous allez maintenant configurer des canaux YouTube en Experience Manager.

1. À droite des **[!UICONTROL Canaux disponibles]**, appuyez sur **+** (icône représentant un signe plus).
1. Dans la boîte de dialogue Paramètres de chaîne YouTube, dans le champ Titre, saisissez le nom de la chaîne que vous avez créée lors de la tâche **[!UICONTROL Ajout d’une ou plusieurs chaînes YouTube]** précédemment.

   Vous pouvez éventuellement ajouter une description.

1. Appuyez sur **[!UICONTROL OK]**.
1. L’authentification YouTube/Google s’affiche. Si vous n’êtes pas déjà connecté à un compte Google Cloud, ignorez cette étape.

   * Saisissez le nom d’utilisateur Google et le mot de passe associés à l’ID de projet Google et au texte JSON ci-dessus.
   * Selon le nombre de chaînes associées à votre compte, deux éléments au moins sont affichés. Sélectionnez une chaîne. Ne sélectionnez pas l’adresse e-mail, car il ne s’agit pas d’une chaîne.
   * Dans la page suivante, appuyez sur **[!UICONTROL Accepter]** pour autoriser l’accès à cette chaîne.

1. Appuyez sur **[!UICONTROL Autoriser]**.

   Vous allez maintenant configurer des balises pour la publication.

1. **[!UICONTROL Configuration de balises pour la publication]** : sur la page Services cloud > YouTube, appuyez sur l’icône en forme de crayon pour modifier la liste des balises que vous souhaitez utiliser.
1. Pour afficher la liste des balises disponibles dans le Experience Manager, appuyez sur l’icône de liste déroulante (insertion dans le caret).
1. Pour les ajouter, appuyez sur une ou plusieurs balises.

   Pour supprimer une balise que vous avez ajoutée, sélectionnez-la et appuyez sur **X**.

1. Lorsque vous avez terminé d’ajouter les balises souhaitées, appuyez sur **[!UICONTROL OK]**.

   Vous allez à présent publier des vidéos sur votre chaîne YouTube.

### (Facultatif) Automatisation de la définition des propriétés YouTube par défaut pour vos vidéos chargées {#optional-automating-the-setting-of-default-youtube-properties-for-your-uploaded-videos}

Vous pouvez si vous le souhaitez automatiser la définition des propriétés YouTube lors du transfert de vos vidéos. Créez un profil de traitement des métadonnées dans le Experience Manager.

Pour créer le profil de traitement des métadonnées, vous allez d’abord copier les valeurs des champs **[!UICONTROL Étiquette de champ]**, **[!UICONTROL Associer à la propriété]** et **[!UICONTROL Choix]**, tous situés dans les schémas de métadonnées pour la vidéo. Ensuite, vous créez votre profil de traitement des métadonnées vidéo YouTube en y ajoutant ces valeurs.

Pour automatiser la définition des propriétés YouTube par défaut pour vos vidéos transférées :

1. Dans le coin supérieur gauche du Experience Manager, cliquez sur le logo du Experience Manager, puis dans le rail de gauche, cliquez sur **[!UICONTROL Outils]** (icône en forme de marteau) > **[!UICONTROL Ressources]** > **[!UICONTROL Schémas de métadonnées]**.
1. Cliquez sur l’option **[!UICONTROL Par défaut]**. (Ne cochez pas la case de sélection à gauche de l’option « Par défaut ».)
1. Sur la page **[!UICONTROL par défaut]**, cochez la case à gauche de **[!UICONTROL vidéo]**, puis cliquez sur **[!UICONTROL Modifier]**.
1. Sur la page Éditeur de schéma de métadonnées, cliquez sur l’onglet **[!UICONTROL Avancé]**.
1. Sous l’en-tête Publication YouTube, cliquez sur **[!UICONTROL Catégorie YouTube]**.
1. Dans la partie droite de la page, sous l’onglet **[!UICONTROL Paramètres]**, procédez comme suit :

   * Dans le champ de texte **[!UICONTROL Associer à la propriété]**, sélectionnez la valeur et copiez-la.
Collez la valeur copiée dans l’éditeur de texte ouvert. Par la suite, vous aurez besoin de cette valeur lorsque vous créez le profil de traitement des métadonnées. Laissez l’éditeur de texte ouvert.

   * Sous **[!UICONTROL Choix]**, sélectionnez la valeur par défaut à utiliser (comme « Personnes et blogs » ou « Science et technologie ») et copiez-la.
Collez la valeur copiée dans l’éditeur de texte ouvert. Par la suite, vous aurez besoin de cette valeur lorsque vous créez le profil de traitement des métadonnées. Laissez l’éditeur de texte ouvert.

1. Sous l’en-tête Publication YouTube, cliquez sur **[!UICONTROL Confidentialité YouTube]**.
1. Dans la partie droite de la page, sous l’onglet **[!UICONTROL Paramètres]**, procédez comme suit :

   * Dans le champ de texte **[!UICONTROL Associer à la propriété]**, sélectionnez la valeur et copiez-la.
Collez la valeur copiée dans l’éditeur de texte ouvert. Par la suite, vous aurez besoin de cette valeur lorsque vous créez le profil de traitement des métadonnées. Laissez l’éditeur de texte ouvert.

   * Sous **[!UICONTROL Choix]**, sélectionnez la valeur par défaut à utiliser et copiez-la. Notez que les choix sont regroupés par paires. Le champ inférieur de la paire correspond à la valeur par défaut que vous souhaitez copier, comme valeur publique, non répertoriée ou privée.
Collez la valeur copiée dans l’éditeur de texte ouvert. Par la suite, vous aurez besoin de cette valeur lorsque vous créez le profil de traitement des métadonnées. Laissez l’éditeur de texte ouvert.

1. Près du coin supérieur droit de la page Éditeur de schéma de métadonnées, cliquez sur **[!UICONTROL Annuler]**.
1. Dans le coin supérieur gauche du Experience Manager, appuyez sur le logo du Experience Manager, puis, dans le rail de gauche, cliquez sur **[!UICONTROL Outils]** (icône en forme de marteau) > **[!UICONTROL Ressources]** > **[!UICONTROL Profils de métadonnées]**.

1. Sur la page Profils de métadonnées, près du coin supérieur droit de la page, cliquez sur **[!UICONTROL Créer]**.
1. Dans la boîte de dialogue Ajouter un profil de métadonnées, dans le champ de texte **[!UICONTROL Titre du profil]**, saisissez le nom `YouTube Video`, puis cliquez sur **[!UICONTROL Créer]**.
1. Sur la page Éditeur de profil de métadonnées, cliquez sur l’onglet **[!UICONTROL Avancé]**.
1. Ajoutez les valeurs de publication YouTube copiées au profil en procédant comme suit :

   * Dans la partie droite de la page, cliquez sur l’onglet **[!UICONTROL Créer le formulaire]**.
   * (Facultatif) Faites glisser le composant appelé **[!UICONTROL En-tête de section]** vers la gauche et déposez-le dans la zone de formulaire.
   * (Facultatif) Cliquez sur **[!UICONTROL Libellé du champ]** pour sélectionner le composant.
   * (Facultatif) Dans la partie droite de la page, sous l’onglet Paramètres, dans le champ de texte Libellé du champ, saisissez `YouTube Publishing`.
   * Cliquez sur l’onglet **[!UICONTROL Créer un formulaire]**, puis faites glisser le composant intitulé **[!UICONTROL Texte à plusieurs valeurs]** et déposez-le sous l’en-tête **[!UICONTROL Publication YouTube]** que vous avez créé.

   * Pour sélectionner le composant, cliquez sur **[!UICONTROL Étiquette de champ]**.
   * Dans la partie droite de la page, sous l’onglet Paramètres, collez les valeurs de publication YouTube (valeur Libellé du champ et Associer à la propriété) copiées précédemment, dans les champs respectifs du formulaire. Collez la valeur Choix dans le champ Valeur par défaut.

1. Ajoutez les valeurs de confidentialité YouTube copiées au profil en procédant comme suit :

   * Dans la partie droite de la page, cliquez sur l’onglet **[!UICONTROL Créer le formulaire]**.
   * (Facultatif) Faites glisser le composant appelé **[!UICONTROL En-tête de section]** vers la gauche et déposez-le dans la zone de formulaire.
   * (Facultatif) Cliquez sur **[!UICONTROL Libellé du champ]** pour sélectionner le composant.
   * (Facultatif) Dans la partie droite de la page, sous l’onglet Paramètres, dans le champ de texte Libellé du champ, saisissez `YouTube Privacy`.
   * Cliquez sur l’onglet **[!UICONTROL Créer un formulaire]**, puis faites glisser le composant intitulé **[!UICONTROL Texte à plusieurs valeurs]** et déposez-le sous l’en-tête **[!UICONTROL Confidentialité YouTube]** que vous avez créé.

   * Pour sélectionner le composant, cliquez sur **[!UICONTROL Étiquette de champ]**.
   * Dans la partie droite de la page, sous l’onglet Paramètres, collez les valeurs de publication YouTube (valeur Libellé du champ et Associer à la propriété) copiées précédemment, dans les champs respectifs du formulaire. Collez la valeur Choix dans le champ Valeur par défaut.

1. Près du coin supérieur droit de la page, cliquez sur **[!UICONTROL Enregistrer]**.
1. Appliquez le profil des métadonnées de publication YouTube aux dossiers dans lesquels vous allez transférer des vidéos. Le Profil de métadonnées et le Profil vidéo doivent être définis.

   Voir [Profils de métadonnées](/help/assets/metadata-profiles.md) et [Profils vidéo](/help/assets/dynamic-media/video-profiles.md).

### Publication de vidéos sur votre chaîne YouTube  {#publishing-videos-to-your-youtube-channel}

Vous devez maintenant associer les balises que vous avez précédemment ajoutées aux ressources vidéo. Ce processus permet au Experience Manager de savoir quels fichiers publier sur votre canal YouTube.

>[!NOTE]
>
>La fonction Publier immédiatement ne publie pas automatiquement sur YouTube. Lorsque Dynamic Media est configuré, il existe deux options de publication parmi lesquelles choisir : **[!UICONTROL Immédiatement]** ou **[!UICONTROL Lors de l’activation]**.
>
>Dans le mode de publication **[!UICONTROL Immédiatement]**, la ressource chargée (une fois synchronisée avec IPS) est automatiquement publiée sur le système de diffusion. Cela vaut pour Dynamic Media, mais pas pour YouTube. Pour publier sur YouTube, vous devez le faire au moyen de l’auteur Experience Manager.

>[!NOTE]
Pour publier du contenu à partir de YouTube, le Experience Manager utilise le flux de travail **[!UICONTROL Publier sur YouTube]**, qui vous permet de surveiller la progression et de vue des informations d’échec.
Voir [Surveillance du codage vidéo et de la progression de la publication sur YouTube](#monitoring-video-encoding-and-youtube-publishing-progress).
Pour obtenir des informations de progression plus détaillées, vous pouvez surveiller le journal YouTube sous la réplication. Sachez toutefois que ce type de surveillance nécessite un accès administrateur.

**Pour publier des vidéos sur votre chaîne YouTube :**

1. En Experience Manager, accédez à un fichier vidéo que vous souhaitez publier sur votre canal YouTube.
1. Sélectionnez la ressource vidéo (visionneuse de vidéos adaptative).
1. Dans la barre d’outils, cliquez sur **[!UICONTROL Propriétés]**.
1. Dans l’onglet De base, sous l’en-tête Métadonnées, cliquez sur **[!UICONTROL Boîte de dialogue Ouvrir la sélection]** à droite du champ Balises.
1. Sur la page Sélectionner des balises, accédez aux balises que vous souhaitez utiliser, puis sélectionnez-en une ou plusieurs.

   N’oubliez pas que les balises doivent être associées à la chaîne YouTube.

1. Dans le coin supérieur droit de la page, cliquez sur **[!UICONTROL Sélectionner]**.
1. Dans le coin supérieur droit de la page des propriétés de la vidéo, cliquez sur **[!UICONTROL Enregistrer et fermer]**.
1. Dans la barre d’outils, cliquez sur **[!UICONTROL Publication rapide]**.

   Voir aussi [Utilisation de la gestion des publications avec des sites Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/page-authoring/publication-management-feature-video-use.html#page-authoring).

   Vous avez la possibilité de vérifier la vidéo publiée sur votre chaîne YouTube.

### (Facultatif) Vérification de la vidéo publiée sur YouTube {#optional-verifying-the-published-video-on-youtube}

Vous pouvez si vous le souhaitez surveiller la progression de votre publication YouTube (ou de l’annulation de celle-ci).

Voir [Surveillance du codage vidéo et de la progression de la publication sur YouTube](#monitoring-video-encoding-and-youtube-publishing-progress).

Le délai de publication peut varier considérablement en fonction de nombreux facteurs, comme le format de la vidéo source originale, la taille du fichier et le trafic de chargement. La publication peut prendre de quelques minutes à plusieurs heures. En outre, les formats à haute résolution sont rendus beaucoup plus lentement. Par exemple, 720p et 1080p nécessitent plus de temps pour apparaître que 480p.

Au bout de huit heures, si un message d’état indique toujours **[!UICONTROL Téléchargé (traitement, veuillez patienter)]**, essayez de supprimer la vidéo de votre site et de la télécharger à nouveau.

### Liaison d’URL YouTube à une application web {#linking-youtube-urls-to-your-web-application}

Une fois que vous avez publié la vidéo, une chaîne URL YouTube est générée par Dynamic Media. Lorsque vous copiez l’URL YouTube, elle est envoyée au Presse-Papiers dont vous pouvez coller le contenu, le cas échéant, sur les pages de votre site web ou de votre application.

>[!NOTE]
L’URL YouTube ne peut pas être copiée tant que vous n’avez pas publié la ressource vidéo sur YouTube.

Pour lier les URL YouTube à votre application web, procédez comme suit :

1. Accédez à la ressource vidéo *publiée sur YouTube* dont vous souhaitez copier l’URL, puis sélectionnez-la.

   N’oubliez pas que les URL YouTube peuvent être copiées uniquement *après* la *publication* des ressources vidéo sur YouTube.

1. Dans la barre d’outils, cliquez sur **[!UICONTROL Propriétés]**.
1. Cliquez sur l’onglet **[!UICONTROL Avancé]**.
1. Sous l’en-tête Publication YouTube, dans la Liste URL YouTube, sélectionnez et copiez le texte de l’URL dans votre navigateur Web pour prévisualisation du fichier ou l’ajouter à votre page de contenu Web.

### Annulation de la publication d’une vidéo pour la supprimer de YouTube  {#unpublishing-videos-to-remove-them-from-youtube}

Lorsque vous annulez la publication d&#39;une ressource vidéo dans Experience Manager, la vidéo est supprimée de YouTube.

>[!CAUTION]
Si vous supprimez directement une vidéo sur YouTube, le Experience Manager n’en est pas conscient et continue à se comporter comme si la vidéo était toujours publiée sur YouTube. Annulez toujours la publication d’un fichier vidéo sur YouTube par Experience Manager.

>[!NOTE]
Pour supprimer du contenu de YouTube, le Experience Manager utilise le flux de travail **[!UICONTROL Annuler la publication de YouTube]**, qui vous permet de surveiller la progression et de vue des informations d’échec.
Voir [Surveillance du codage vidéo et de la progression de la publication sur YouTube](#monitoring-video-encoding-and-youtube-publishing-progress).

Pour annuler la publication de vidéos afin de les supprimer de YouTube, procédez comme suit :

1. Accédez à la ressource vidéo que vous souhaitez publier sur votre chaîne YouTube.
1. Dans un mode de sélection de ressource, sélectionnez une ou plusieurs ressources vidéo publiées.
1. Dans la barre d’outils, cliquez sur **[!UICONTROL Gérer la publication]**. Si nécessaire, appuyez sur l’icône des trois points (. . .) de la barre d’outils pour afficher **[!UICONTROL Gérer la publication]**.
1. Sur la page Gérer la publication, appuyez sur **[!UICONTROL Annuler la publication]**.
1. Dans le coin supérieur droit de la page, appuyez sur **[!UICONTROL Suivant]**.
1. Dans le coin supérieur droit de la page, appuyez sur **[!UICONTROL Annuler la publication]**.

## Surveillance du codage vidéo et de la progression de la publication sur YouTube  {#monitoring-video-encoding-and-youtube-publishing-progress}

Lorsque vous téléchargez une nouvelle vidéo dans un dossier pour lequel un codage vidéo est appliqué ou que vous publiez votre vidéo sur YouTube, surveillez l’avancement (ou l’échec) de votre codage vidéo/publication YouTube. La progression réelle de la publication YouTube n’est disponible que par le biais des journaux. Mais qu&#39;elle échoue ou qu&#39;elle réussisse, elle est répertoriée d&#39;autres manières décrites dans la procédure suivante. En outre, vous recevez des notifications par courrier électronique lorsqu’un processus de publication ou de codage vidéo YouTube se termine ou est interrompu.

### Suivi de la progression {#monitoring-progress}

Pour surveiller la progression (notamment l’échec du codage ou de la publication YouTube) :

1. Consultez la progression du codage vidéo dans votre dossier de ressources :

   * En mode Carte, la progression du codage vidéo s’affiche sur la ressource en pourcentage. Si une erreur se produit, ces informations s’affichent également sur cette ressource.

   ![chlimage_1-429](assets/chlimage_1-429.png)

   * En mode Liste, la progression du codage vidéo s’affiche dans la colonne **[!UICONTROL État du traitement]**. Si une erreur se produit, le message suivant s’affiche dans la même colonne.

   ![chlimage_1-430](assets/chlimage_1-430.png)

   Cette colonne ne s’affiche pas par défaut. Pour activer la colonne, sélectionnez l’option **[!UICONTROL Paramètres d’affichage]** dans le menu contextuel des affichages et ajoutez la colonne **[!UICONTROL État du traitement]** et appuyez ou cliquez sur **[!UICONTROL Mettre à jour]**.

   ![chlimage_1-431](/help/assets/dynamic-media/assets/chlimage_1-431.png)

1. Consultez la progression dans les détails de la ressource. Lorsque vous appuyez ou cliquez sur une ressource, ouvrez le menu contextuel et sélectionnez **[!UICONTROL Chronologie]**. Pour le réduire à des activités de processus comme le codage ou la publication YouTube, sélectionnez **[!UICONTROL Processus]**.

   ![chlimage_1-432](assets/chlimage_1-432.png)

   Toutes les informations de workflow, telles que le codage, s’affichent dans la chronologie. Pour la publication YouTube, la chronologie du workflow comprend également le nom de la chaîne YouTube et l’URL de la vidéo YouTube. En outre, une fois la publication terminée, les notifications d’échec s’affichent dans la chronologie du workflow.

   >[!NOTE]
   Il peut s’écouler un certain temps avant que les messages d’échec/d’erreur ne soient finalement enregistrés en raison de plusieurs configurations de processus sur **[!UICONTROL Reprises]**, **[!UICONTROL délai de nouvelle tentative]** et **[!UICONTROL délai]** de [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr), par exemple :
   * Configuration de la file d’attente des tâches Apache Sling
   * Gestionnaire des tâches du processus externe de processus Adobe Granite
   * File d’attente des délais d’attente des processus Granite

   Dans ces configurations, vous pouvez ajuster les propriétés **[!UICONTROL Reprises]**, **[!UICONTROL délai de nouvelle tentative]** et **[!UICONTROL délai d’expiration]**.

1. Pour les workflows en cours, consultez les instances de workflow disponibles sous **[!UICONTROL Outils]** > **[!UICONTROL Processus]** > **[!UICONTROL Instances]**.

   >[!NOTE]
   Vous avez besoin de droits d&#39;administration pour accéder au menu **[!UICONTROL Outils]**.

   ![chlimage_1-433](assets/chlimage_1-433.png)

   Sélectionnez l’instance et appuyez ou cliquez sur **[!UICONTROL Ouvrir l’historique]**.

   ![chlimage_1-434](/help/assets/dynamic-media/assets/chlimage_1-434.png)

   Depuis la section instances de workflow, vous pouvez également suspendre, arrêter ou renommer les workflows. Voir [Administration des workflows](/help/sites-cloud/authoring/workflows/overview.md) pour plus d’informations.

1. Pour les tâches qui ont échoué, consultez la section Échecs des processus disponible sous **[!UICONTROL Outils]** > **[!UICONTROL Processus]** > **[!UICONTROL Échecs]**. L’**[!UICONTROL échec du processus]** répertorie toutes les activités du processus ayant échoué.

   >[!NOTE]
   Vous avez besoin de droits d&#39;administration pour accéder au menu **[!UICONTROL Outils]**.

   ![chlimage_1-435](assets/chlimage_1-435.png)

   >[!NOTE]
   Il peut s’écouler un certain temps avant que le message d’erreur ne soit finalement enregistré en raison de plusieurs configurations de processus sur **[!UICONTROL Reprises]**, **[!UICONTROL délai de nouvelle tentative]** et **[!UICONTROL délai d’expiration]** de [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr), par exemple :
   * Configuration de la file d’attente des tâches Apache Sling
   * Gestionnaire des tâches du processus externe de processus Adobe Granite
   * File d’attente des délais d’attente des processus Granite

   Dans ces configurations, vous pouvez ajuster les propriétés **[!UICONTROL Reprises]**, **[!UICONTROL délai de nouvelle tentative]** et **[!UICONTROL délai d’expiration]**.

1. Pour les workflows terminés, consultez l’archive de workflow sous **[!UICONTROL Outils]** > **[!UICONTROL Processus]** > **[!UICONTROL Archive]**. La liste **[!UICONTROL Archive de workflow]** répertorie toutes les activités de workflow qui ont réussi.

   >[!NOTE]
   Vous avez besoin de droits d&#39;administration pour accéder au menu **[!UICONTROL Outils]**.

   ![chlimage_1-436](assets/chlimage_1-436.png)

1. Vous recevez des notifications par courrier électronique sur les tâches de workflow abandonnées ou en échec. Ces notifications peuvent être configurées par un administrateur. Voir [Configuration des notifications par courrier électronique](#configuring-e-mail-notifications).

<!-- EMAIL NOT AVAILABLE IN SKYLINE

#### Configuring e-mail notifications {#configuring-e-mail-notifications}

>[!NOTE]
>
>You may need administrative rights to access the **[!UICONTROL Tools]** menu.

How you configure notification depends on whether you want notifications for YouTube publishing jobs.

* For encoding jobs, you can access the configuration page for all Experience Manager workflow email notifications at **[!UICONTROL Tools]** &gt; **[!UICONTROL Operations]** &gt; **[!UICONTROL Web Console]** and by searching for **[!UICONTROL Day CQ Workflow Email Notification Service]**. You can select or clear the check boxes for **[!UICONTROL Notify on Abort]** or **[!UICONTROL Notify on Complete]** accordingly.

For YouTube publishing jobs, do the following:

1. In Experience Manager, tap **[!UICONTROL Tools]** &gt; **[!UICONTROL Workflow]** &gt; **[!UICONTROL Models]**.
1. On the Workflow Models page, select **[!UICONTROL Publish to YouTube]**, then tap **[!UICONTROL Edit]** on the toolbar.
1. Near the upper-right corner of the Publish to YouTube workflow page, tap **[!UICONTROL Edit]**.
1. Hover the mouse pointer on the YouTube Upload component, then tap once to display the inline toolbar.

   ![6_5_publishtoyoutubeworkflow](assets/6_5_publishtoyoutubeworkflow.png)

1. On the inline toolbar, tap the Configuration icon (wrench). Click the **[!UICONTROL Arguments]** tab.

   ![6_5_publishtoyoutubeworkflow-configurationicon](assets/6_5_publishtoyoutubeworkflow-configurationicon.png)

1. In the YouTube Upload Process - Step Properties dialog box, tap the **[!UICONTROL Arguments]** tab.

   ![6_5_publishtoyoutubeworkflow-arguments-tab](assets/6_5_publishtoyoutubeworkflow-arguments-tab.png)

1. You can select or clear the following check boxes:

    * Publish Start
    * Publish Failure
    * Publish Completion - includes information on channels and URLs

   Clearing a check box means that you will not receive the specified email notification from the YouTube Publish workflow.

   >[!NOTE]
   >
   >These emails are specific to YouTube and are in addition to the generic workflow email notifications. As a result, you may receive two sets of email notification - the generic notification available in the **[!UICONTROL Day CQ Workflow Email Notification Service]** and one specific to YouTube depending on your configuration settings.

1. When you are finished, near the upper-right corner of the dialog box, tap the **[!UICONTROL Done]** icon (check mark).
1. On the Publish to YouTube workflow page, near the upper-right corner, tap **[!UICONTROL Sync]**.

-->

## Affichage de rapports vidéo {#viewing-video-reports}

>[!NOTE]
Les rapports vidéo sont disponibles uniquement lorsque vous exécutez Dynamic Media en mode Hybride.

Les rapports Vidéo présentent plusieurs mesures d’agrégat sur une période spécifiée afin de vous aider à vérifier que les *vidéos publiées* individuelles et agrégats se comportent comme prévu. Les données des mesures principales suivantes sont agrégées pour toutes les vidéos publiées sur l&#39;ensemble de votre site web :

* Lancements de vidéo
* Taux d’achèvement
* Temps moyen sur la vidéo
* Durée totale sur la vidéo
* Vidéos par visite

Un tableau de toutes les vidéos *publiées* est également fourni pour vous permettre de suivre les vidéos les plus visionnées sur votre site web en fonction du total des lancements de vidéo.

Lorsque vous appuyez sur le nom d’une vidéo dans la liste, le rapport de rétention des audiences (liste déroulante) de la vidéo s’affiche sous la forme d’un graphique en courbes. Le graphique présente le nombre de vues pour un moment donné au cours de la lecture vidéo. Lorsque vous lisez la vidéo, la barre verticale effectue un suivi en synchronisation avec l’indicateur de temps du lecteur. Les pertes de données du graphique en courbes indiquent où votre audience perd de son intérêt.

Si la vidéo a été codée en dehors d’Adobe Experience Manager Dynamic Media, le graphique sur la rétention de l’audience (taux de déperdition) et les données de pourcentage de lecture du tableau ne sont pas disponibles.

>[!NOTE]
Le suivi et les données de rapport reposent exclusivement sur l’utilisation du lecteur vidéo Dynamic Media et du paramètre de lecteur vidéo prédéfini associé. Vous ne pouvez donc pas effectuer le suivi et créer de rapports sur des vidéos qui sont lues par d’autres lecteurs vidéo.

Par défaut, la première fois que vous utilisez l’option Rapports vidéo, le rapport affiche des données vidéo du premier jour du mois en cours jusqu’à la date du mois en cours. Vous pouvez toutefois remplacer la période par défaut par la vôtre. La prochaine fois que vous utiliserez l’option Rapports vidéo, la période que vous avez spécifiée sera utilisée.

Pour que les rapports vidéo fonctionnent correctement, un identifiant de suite de rapports est automatiquement créé lors de la configuration des Cloud Services Dynamic Media. Dans le même temps, l’identifiant de suite de rapports est transmis au serveur de publication pour qu’il soit disponible pour la fonctionnalité de copie d’URL lors de la prévisualisation de ressources. Toutefois, cette fonctionnalité nécessite que le serveur de publication soit déjà configuré. Si le serveur de publication n’est pas configuré, vous pouvez toujours publier pour afficher le rapport vidéo. Cependant, vous devez revenir à la configuration de Dynamic Media Cloud et appuyer sur **[!UICONTROL OK]**.

Pour afficher un rapport vidéo, procédez comme suit :

1. Dans le coin supérieur gauche du Experience Manager, appuyez sur le logo du Experience Manager, puis, dans le rail de gauche, appuyez sur **[!UICONTROL Outils]** (icône en forme de marteau) > **[!UICONTROL Ressources]** > **[!UICONTROL Rapports vidéo]**.
1. Dans la page Rapport vidéo, effectuez l’une des opérations suivantes :

   * Dans le coin supérieur droit, appuyez sur l’icône **[!UICONTROL Actualiser le rapport vidéo]**.
Vous utilisez l’option Actualiser uniquement si la date de fin du rapport est le jour en cours. Cette fonctionnalité vous permet de voir le suivi vidéo qui s’est produit depuis la dernière exécution du rapport.

   * Dans le coin supérieur droit, appuyez sur l’icône **[!UICONTROL Sélecteur de date]**.
Indiquez la période de début et de fin pour laquelle vous souhaitez obtenir les données vidéo, puis appuyez sur **[!UICONTROL Exécuter le rapport]**.

   Le groupe Mesures principales identifie diverses mesures agrégées pour toutes les vidéos publiées sur votre site.

1. Dans le tableau qui répertorie les principales vidéos publiées, appuyez sur le nom d’une vidéo pour la lire et afficher également le rapport sur la rétention de l’audience (taux de déperdition) de celle-ci.

<!-- OBSOLETE CONTENT OBSOLETE CONTENT - SDK ONLY AVAILABLE INTERNALLY NOW 
### Viewing video reports based on a video viewer that you created using the Dynamic Media HTML5 Viewer SDK {#viewing-video-reports-based-on-a-video-viewer-that-you-created-using-the-scene-hmtl-viewer-sdk}

If you are using an out-of-box video viewer provided by Dynamic Media, or if you created a custom viewer preset based off of an out-of-box video viewer, then no additional steps are required to view video reports. However, if you have created your own video viewer based off the Dynamic Media HTML5 Viewer SDK, then use the following steps to ensure the your video viewer is sending tracking events to Dynamic Media Video Reports.

Use the Dynamic Media Viewers Reference and the Dynamic Media HTML5 Viewers SDK to create your own video viewers.

See [Dynamic Media Viewers Reference Guide](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/home.html?lang=en).

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

## Ajout de sous-titres à une vidéo {#adding-captions-to-video}

Vous pouvez étendre vos vidéos aux marchés mondiaux en ajoutant des sous-titres aux vidéos ou aux visionneuses de vidéos adaptatives. En ajoutant des sous-titres, vous évitez d’avoir à réenregistrer le son ou de recourir à des locuteurs natifs pour réenregistrer la partie audio dans les différentes langues. La vidéo est lue dans la langue dans laquelle elle a été enregistrée. Les sous-titres en langue étrangère s’affichent pour que les personnes parlant d’autres langues puissent néanmoins comprendre la partie audio.

Les sous-titres offrent également une meilleure accessibilité en utilisant des sous-titres pour les sourds ou les malentendants.

>[!NOTE]
Le lecteur vidéo utilisé doit prendre en charge l’affichage des sous-titres.

Dynamic Media peut convertir des fichiers de sous-titrage au format JSON (JavaScript™ Object Notation). Cette conversion signifie que vous pouvez intégrer le texte JSON dans une page web sous forme de transcription masquée complète de la vidéo. Les moteurs de recherche peuvent alors analyser et indexer le contenu pour rendre les vidéos plus facilement détectables et donner aux clients plus de détails sur le contenu vidéo.

Voir [Diffusion de contenu statique (sans image)](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/c-serving-static-nonimage-contents.html?lang=fr#image-serving-api) pour plus d’informations sur l’utilisation de la fonction JSON dans une URL.

**Pour ajouter des sous-titres à une vidéo :**

1. Utilisez une application tierce ou un service de création de fichiers de sous-titres de vidéo.

   Assurez-vous que le fichier que vous créez est conforme à la norme WebVTT (Web Video Text Tracks). L’extension du nom de fichier de sous-titrage est .VTT. D’autres informations sur la norme de sous-titrage WebVTT sont disponibles.

   Reportez-vous à la section [WebVTT : The web video text tracks format](https://dev.w3.org/html5/webvtt/).

   Il existe des outils et des services gratuits et payants que vous pouvez utiliser pour créer les fichiers de sous-titres en dehors de Dynamic Media. Par exemple, pour créer un fichier de sous-titres vidéo simple sans style, vous pouvez utiliser l’outil de création et de modification de sous-titres en ligne gratuit suivant :

   [WebVTT Caption Maker](https://testdrive-archive.azurewebsites.net/Graphics/CaptionMaker/Default.html)

   Pour de meilleurs résultats, utilisez cet outil dans Internet Explorer 9 ou version ultérieure, dans Google Chrome ou Safari.

   Dans l’outil, dans le champ **[!UICONTROL Saisir l’URL du fichier vidéo]**, collez l’URL copiée de votre fichier vidéo, puis cliquez sur **[!UICONTROL Charger]**. Voir [Obtention d’une URL pour une ressource](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-an-asset) pour obtenir l’URL du fichier vidéo proprement dit, que vous pouvez coller ensuite dans le champ **[!UICONTROL Saisir l’URL du fichier vidéo]**. Internet Explorer, Chrome ou Safari peuvent alors lire la vidéo en mode natif.

   À présent, suivez les instructions à l’écran du site pour créer et enregistrer votre fichier WebVTT. Lorsque vous avez terminé, copiez le contenu du fichier de sous-titrage et collez-le dans un éditeur de texte brut, puis enregistrez-le avec l’extension de nom de fichier .VTT.

   >[!NOTE]
   Pour la prise en charge globale des sous-titres vidéo en plusieurs langues, la norme WebVTT exige que vous créiez des fichiers .vtt et des appels distincts pour chaque langue à prendre en charge.

   En règle générale, vous attribuez au fichier VTT de sous-titrage le même nom que le fichier vidéo et vous lui ajoutez le paramètre régional de langue, par exemple -EN, -FR ou -DE. Ainsi, vous pouvez automatiser aisément la génération des URL de vidéo avec le système de gestion de contenu web existant.

1. En Experience Manager, téléchargez votre fichier de sous-titrage WebVTT dans DAM.
1. Accédez à la ressource vidéo *publiée* à associer au fichier de sous-titres que vous avez chargé.

   N’oubliez pas que les URL ne peuvent être copiées qu’*après* la *publication* des ressources.

   Voir [Publication de ressources](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

1. Utilisez l’une des méthodes suivantes :

   * Pour une expérience de visionneuse de vidéos pop-up, appuyez sur **[!UICONTROL URL]**. Dans la boîte de dialogue URL, sélectionnez l’URL et copiez-la dans le Presse-papiers, puis collez-la dans un éditeur de texte simple. Ajoutez l’URL copiée de la vidéo avec la syntaxe suivante :

      `&caption=<server_path>/is/content/<path_to_caption.vtt_file,1>`

      Notez le « `,1` » à la fin du chemin du fichier de sous-titres. Immédiatement après l’extension de fichier .VTT dans le chemin d’accès, vous pouvez activer (activer) ou désactiver (désactiver) le bouton de sous-titrage fermé sur la barre du lecteur vidéo en définissant `,1` ou `,0`, respectivement.

   * Pour une expérience de visionneuse de vidéos intégrée, appuyez sur **[!UICONTROL Code intégré]**. Dans la boîte de dialogue Code incorporé, sélectionnez et copiez le code incorporé dans le Presse-papiers, puis collez le code dans un éditeur de texte simple. Ajoutez le code intégré copié avec la syntaxe suivante :

      `videoViewer.setParam("caption","<path_to_caption.vtt_file,1>");`

      Notez le « `,1` » à la fin du chemin du fichier de sous-titres. Immédiatement après l’extension de fichier .VTT dans le chemin d’accès, vous pouvez activer (activer) ou désactiver (désactiver) le bouton de sous-titrage fermé sur la barre du lecteur vidéo en définissant `,1` ou `,0`, respectivement.

## Ajout de marqueurs de chapitre à la vidéo {#adding-chapter-markers-to-video}

Vous pouvez faciliter la lecture et le parcours de vos vidéos les plus longues en ajoutant des marqueurs de chapitre aux vidéos uniques ou aux visionneuses de vidéos adaptatives. Lorsqu’un utilisateur lit la vidéo, il peut cliquer sur les marques de chapitre sur le plan de montage chronologique de la vidéo (également appelé barre de défilement de la vidéo). Ils peuvent facilement accéder à leur point d’intérêt ou accéder immédiatement à un nouveau contenu, à des démonstrations et à des didacticiels.

>[!NOTE]
Le lecteur vidéo utilisé doit prendre en charge l’utilisation des marqueurs de chapitre. Les lecteurs vidéo Dynamic Media prennent en charge les marques de chapitre, mais l’utilisation de lecteurs vidéo tiers peut ne pas être possible.

<!-- OBSOLETE CONTENT OBSOLETE CONTENT If desired, you can create and brand your own custom video viewer with chapters instead of using a video viewer preset. For instructions on creating your own HTML5 viewer with chapter navigation, in the Adobe Scene7 Viewer SDK for HTML5 guide, reference the heading “Customizing Behavior Using Modifiers” under the classes `s7sdk.video.VideoPlayer` and `s7sdk.video.VideoScrubber`. The Adobe Scene7 Viewer SDK is available as a download from [Adobe Developer Connection](https://help.adobe.com/en_US/scene7/using/WSef8d5860223939e2-43dedf7012b792fc1d5-8000.html). -->

Vous créez une liste de chapitres pour votre vidéo un peu de la même façon que vous créez des sous-titres. Autrement dit, vous créez un fichier WebVTT. Notez toutefois que ce fichier doit être distinct de tout fichier de sous-titrage WebVTT. Vous ne pouvez pas combiner des légendes et des chapitres dans un seul fichier WebVTT.

Vous pouvez utiliser l’exemple suivant comme un exemple du format que vous pouvez utiliser pour créer un fichier WebVTT avec une navigation par chapitre :

### Fichier WebVTT avec navigation par chapitre vidéo {#webvtt-file-with-video-chapter-navigation}

```xml
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

Dans l’exemple ci-dessus, le `Chapter 1` est l’identifiant de repère et il est facultatif. La période de repère `00:00:000 --> 01:04:364` indique l’heure de début et l’heure de fin du chapitre au format `00:00:000`. Les trois derniers chiffres sont les millisecondes et peuvent être laissés sur `000`, selon vos préférences. Le titre du chapitre `The bicycle store behind it all` est la description réelle du contenu du chapitre. L’identifiant de l’indice, l’heure de début et le titre du chapitre apparaissent tous dans une fenêtre contextuelle du lecteur vidéo lorsqu’un utilisateur place le pointeur de la souris sur un point de repère visuel du plan de montage chronologique.

Étant donné que vous utilisez une visionneuse de vidéos HTML5, assurez-vous que le fichier de chapitres que vous créez est conforme à la norme WebVTT (Web Video Text Tracks). L’extension de nom de fichier de chapitre est .VTT. D’autres informations sur la norme de sous-titrage WebVTT sont disponibles.

Reportez-vous à la section [WebVTT : The web video text tracks format](https://dev.w3.org/html5/webvtt/)

**Pour ajouter des marqueurs de chapitre à la vidéo :**

1. Enregistrez le fichier .VTT dans l’encodage UTF8 afin d’éviter tout problème de rendu des caractères dans le texte du titre du chapitre.

   En règle générale, vous attribuez au fichier de chapitres VTT le même nom que celui du fichier vidéo et lui ajoutez le mot « chapitres ». Ainsi, vous pouvez automatiser aisément la génération des URL de vidéo avec le système de gestion de contenu web existant.
1. En Experience Manager, téléchargez votre fichier de chapitre WebVTT.

   Voir la section [Chargement des ressources](/help/assets/manage-digital-assets.md#uploading-assets).

1. Utilisez l’une des méthodes suivantes :

   <table>
     <tbody>
      <tr>
       <td>Pour une expérience de visionneuse de vidéos pop-up</td>
       <td>
       <ol>
       <li>Accédez à la ressource vidéo <i>publiée</i> à associer au fichier de chapitres que vous avez chargé. N’oubliez pas que les URL ne peuvent être copiées qu’<i>après</i> la <i>publication</i> des ressources. Voir <a href="/help/assets/dynamic-media/publishing-dynamicmedia-assets.md">Publication de ressources</a>.</li>
       <li>Dans le menu déroulant, cliquez ou appuyez ensuite sur <strong>Visionneuses</strong>.</li>
       <li>Dans le rail de gauche, appuyez ou cliquez sur le nom du paramètre prédéfini de la visionneuse de vidéos. Un aperçu de la vidéo s’ouvre dans une page distincte.</li>
       <li>Dans le rail de gauche, dans la partie inférieure, cliquez sur <strong>URL</strong>.</li>
       <li>Dans la boîte de dialogue URL, sélectionnez l’URL et copiez-la dans le Presse-papiers, puis collez-la dans un simple éditeur de texte.</li>
       <li>Ajoutez l’URL copiée de la vidéo avec la syntaxe suivante pour l’associer à l’URL copiée dans votre fichier de chapitres :<br /> <br /> <code>&navigation=<<i>full_copied_URL_path_to_chapter_file</i>.vtt></code><br /> </li>
       </ol> </td>
      </tr>
      <tr>
       <td>Pour une expérience de visionneuse de vidéos incorporée<br /> </td>
       <td>
       <ol>
       <li>Accédez à la ressource vidéo <i>publiée</i> à associer au fichier de chapitres que vous avez chargé. N’oubliez pas que les URL ne peuvent être copiées qu’<i>après</i> la <i>publication</i> des ressources. Voir <a href="/help/assets/dynamic-media/publishing-dynamicmedia-assets.md">Publication de ressources</a>.</li>
       <li>Dans le menu déroulant, cliquez ou appuyez ensuite sur <strong>Visionneuses</strong>.</li>
       <li>Dans le rail de gauche, appuyez ou cliquez sur le nom du paramètre prédéfini de la visionneuse de vidéos. Un aperçu de la vidéo s’ouvre dans une page distincte.</li>
       <li>En bas du rail gauche, cliquez sur <strong>Intégrer</strong>.</li>
       <li>Dans la boîte de dialogue Code incorporé, sélectionnez et copiez l’intégralité du code dans le Presse-papiers, puis collez-le dans un éditeur de texte simple.</li>
       <li>Ajoutez le code intégré de la vidéo avec la syntaxe suivante pour l’associer à l’URL copiée dans votre fichier de chapitres :<br /> <br /> <code>videoViewer.setParam("navigation","&lt;<i>full_copied_URL_path_to_chapter_file</i>.vtt&gt;"</code></li>
       </ol> </td>
      </tr>
     </tbody>
   </table>

<!--

## About video thumbnails {#about-video-thumbnails}

A video thumbnail is a reduced-size version of a video frame or an image asset representing the video to the customer. The thumbnail should serve to encourage a customer to click on the video.

All videos in Experience Manager must have an associated thumbnail; you cannot delete a thumbnail without replacing it. By default, when you upload a video to Experience Manager, the first frame is used as the thumbnail. However, you can customize the thumbnail for branding purposes or visual search, for example. When you customize a video thumbnail, you can either play the video and pause on the frame you want to use, or you can select an image asset that you have already uploaded and *published* in your digital asset manager.

Note that a custom video thumbnail image that you select from a video is not extracted and saved in the DAM as a separate and distinct asset. However, a custom video thumbnail that you select from an existing image asset is saved to the JCR. The path of the selected asset gets stored under the video asset's node as in the following example path:

`/content/dam/*<folder_name*>/<*video_name*>/jcr:content/manualThumbnail`

The ability to customize a video thumbnail is only available after you have applied a video profile to the folder where the video is located.

### Adding a custom video thumbnail {#adding-a-custom-video-thumbnail}

1. Be sure you have already done the following:

    * Created a folder for your video assets.
    * [Applied a video profile to the folder](/help/assets/dynamic-media/video-profiles.md#applying-a-video-profile-to-folders).

    * [Uploaded your videos to the folder](/help/assets/manage-video-assets.md#upload-and-preview-video-assets).

1. Navigate to an uploaded video asset whose thumbnail image you want to change.
1. In asset selection mode either from **[!UICONTROL List View]** or **[!UICONTROL Card View]**, tap the video asset.
1. On the toolbar, tap the **[!UICONTROL Properties** icon (a circle with an "i" in it).
1. On the video's Properties page, tap **[!UICONTROL Change Thumbnail]**.
1. On the Change Thumbnail page, do one of the following:

    * To use a frame from the video as the new thumbnail:

        * On the toolbar, tap **[!UICONTROL Select Frame from video]**.
        * Tap the Play button, then tap the Pause button on the frame you want to capture as the video's new thumbnail.

    * To use an image asset as the new thumbnail:

        * On the toolbar, tap **[!UICONTROL Select Thumbnail from Assets]**.
        * Tap **[!UICONTROL Select Thumbnail]**.
        * Navigate to a previously uploaded and published image asset you want to use. Note that the asset will automatically be resized to serve as a thumbnail image for the video.
        * Select the image asset, then tap **[!UICONTROL Select]**.

1. On the Change Thumbnail page, tap **[!UICONTROL Save Change]**.
1. On the video's Properties page, in the upper-right corner, tap **[!UICONTROL Save & Close]**.

-->

<!--

## About video thumbnails in Dynamic Media Hybrid mode{#about-video-thumbnails-in-dynamic-media-hybrid-mode}

You can choose from one of ten thumbnail images automatically generated by Dynamic Media to add to your video. The video player displays your selected thumbnail when a video asset is used with the Dynamic Media component in the authoring environment of Experience Manager Sites, Experience Manager Mobile, or Experience Manager Screens. The thumbnail serves as a static picture that best represents the contents of your entire video and further encourages users to click the Play button.

Based on the total time of the video, Dynamic Media captures ten (default) thumbnail images at 1%, 11%, 21%, 31%, 41%, 51%, 61%, 71%, 81%, and 91% into the video. The ten thumbnails persist meaning that if you decide to choose a different thumbnail later on, you do not need to regenerate the series. You preview the ten thumbnail images and then select the one you want to use with your video. If you want to change to default you can use CRXDE Lite to configure the time interval that thumbnail images are generated. For example, if you only wanted to generate a series of four evenly spaced thumbnail images from your video, you can configure the interval time at 24%, 49%, 74%, and 99%.

Ideally, you can add a video thumbnail anytime after you upload your video but before you publish the video on your website.

If you prefer, you can choose to upload a custom thumbnail to represent your video instead of using a thumbnail generated by Dynamic Media. For example, you could create a custom thumbnail image that has the title of your video, an eye-catching opening image, or a very specific image captured from your video. The custom video thumbnail image that you upload should have a maximum resolution of 1280 x 720 pixels (minimum width of 640 pixels) and be no larger than 2MB.

See also [About video thumbnails](/help/assets/dynamic-media/video.md#about-video-thumbnails-in-dynamic-media-scene-mode).

-->

<!--

### Adding a video thumbnail {#adding-a-video-thumbnail}

1. Navigate to an uploaded video asset that you want to add a video thumbnail.
1. In asset selection mode either from the List View or the Card View, tap the video asset.
1. On the toolbar, tap the **[!UICONTROL View Properties]** icon (a circle with an "i" in it).
1. On the video's Properties page, tap **[!UICONTROL Change Thumbnail]**.
1. On the Change Thumbnail page, on the toolbar, tap **[!UICONTROL Select Frame]**.

   Dynamic Media generates a series thumbnail images from your video, based on the default time interval or time interval you customized.

1. Preview the generated thumbnail images, then select the one you want to add to your video.
1. Tap **[!UICONTROL Save Change]**.

   The video's thumbnail image is updated to use the thumbnail you selected. If you later decide to change the thumbnail image, you can return to the **[!UICONTROL Change Thumbnail]** page and select a new one.

   If you configured new default time intervals, or you uploaded a new video to replace the existing video, you will need to have Dynamic Media regenerate the thumbnails.

   See [Configuring the default time interval that video thumbnails are generated](#configuring-the-default-time-interval-that-video-thumbnails-are-generated).

-->

<!--

#### Configuring the default time interval that video thumbnails are generated {#configuring-the-default-time-interval-that-video-thumbnails-are-generated}

When you configure and save the new default time interval, your change automatically applies only to videos that you upload in the future. It does not automatically apply the new default to videos that you previously uploaded. For existing videos, you must regenerate the thumbnails.

See [Adding a video thumbnail](#adding-a-video-thumbnail).

**To configure the default time interval that video thumbnails are generated,**

1. In Experience Manager, tap **[!UICONTROL Tools]** &gt; **[!UICONTROL General]** &gt; **[!UICONTROL CRXDE Lite]**.

1. In the CRXDE Lite page, in the directory panel on the left, navigate t `o etc/dam/imageserver/configuration/jcr:content/settings.`

   if the directory panel is not visible, you may need to tap the &gt;&gt; icon to the left of the Home tab.

1. On the lower-right panel, in the Properties tab, double-tap `thumbnailtime`.
1. In the Edit thumbnailtime dialog box, use the text fields to enter interval values as percentages.

    * Tap the plus sign (+) icon to add one or more interval value fields. You may need to scroll to the bottom of the dialog box to see the icon.
    * Tap the minus sign (-) icon to the right of an interval value field to delete it from the list.
    * Tap the up arrow icon and the down arrow icon to reorder the interval values.

1. Tap **[!UICONTROL OK]** to return to the Properties tab.
1. Near the upper-left corner of the CRXDE Lite page, tap **[!UICONTROL Save All]**, then tap the Back Home icon in the upper-left corner to return to Experience Manager.

   See [Adding a video thumbnail.](#adding-a-video-thumbnail)

-->

<!--

### Adding a custom video thumbnail {#adding-a-custom-video-thumbnail-1}

These steps apply only to Dynamic Media running in Hybrid mode.

T**o add a custom video thumbnail**,

1. Navigate to an uploaded video asset that you want to add a custom video thumbnail.
1. In asset selection mode either from the List View or the Card View, tap the video asset.
1. On the toolbar, tap the **[!UICONTROL View Properties]** icon (a circle with an "i" in it).
1. On the video's Properties page, tap **[!UICONTROL Change Thumbnail]**.
1. On the Change Thumbnail page, on the toolbar, tap **[!UICONTROL Upload New Thumbnail]**.
1. Navigate to a thumbnail image you want to use, select it, then tap **[!UICONTROL Open]** to begin uploading the image into Experience Manager. Following the upload, be sure you publish the image.
1. After you have successfully uploaded and published the image, in the Change Thumbnail page, tap **[!UICONTROL Save Changes]**.

   The custom thumbnail is added to your video.

-->
