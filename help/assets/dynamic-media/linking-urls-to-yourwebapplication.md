---
title: Liaison d’URL à une application web
description: Découvrez comment lier des URL à votre application web dans Dynamic Media.
role: Business Practitioner
exl-id: 3cd3f4d5-ebf0-4318-9a0d-1ea69453d57b
source-git-commit: d3ee23917eba4a2e4ae1f2bd44f5476d2ff7dce1
workflow-type: tm+mt
source-wordcount: '1275'
ht-degree: 69%

---

# Liaison d’URL à une application web {#linking-urls-to-your-web-application}

Vos applications et sites web accèdent aux services Dynamic Media par l’intermédiaire d’appels d’URL. Une fois que vous avez publié une ressource, Dynamic Media active une chaîne d’URL qui fait référence à la ressource. Vous pouvez coller ces URL dans un navigateur web à des fins de test.

Vous ne créez un lien vers les URL que si vous *et non* utilisez Adobe Experience Manager comme système de gestion de contenu web. La liaison (plutôt que l’incorporation) est utilisée lorsque vous souhaitez diffuser un lecteur vidéo sous la forme d’une fenêtre contextuelle ou modale. Si vous utilisez Experience Manager comme gestion de contenu web, [vous ajoutez les ressources directement sur votre page.](adding-dynamic-media-assets-to-pages.md)

Pour placer ces chaînes URL dans vos pages et applications web, copiez-les depuis Dynamic Media.

>[!NOTE]
>
>Les chaînes URL ne sont disponibles que pour les rendus dynamiques de ressources. Ils ne sont actuellement pas disponibles pour les ressources statiques qui résident dans la gestion des ressources numériques et non dans le serveur Dynamic Media. Le bouton URL n’apparaît pas pour les rendus statiques.

Voir aussi [Incorporation de la visionneuse de vidéos ou d’images dans une page web](embed-code.md).

Voir aussi [Liaison d’URL YouTube à une application web](video.md).

Voir aussi [Diffusion d’images optimisées pour un site réactif](responsive-site.md).

Voir aussi [Chargement de ressources](/help/assets/manage-digital-assets.md#uploading-assets).

## Obtention d’une URL pour une ressource {#obtaining-a-url-for-an-asset}

Vous pouvez obtenir une chaîne URL qui est générée par un paramètre d’image prédéfini ou un paramètre prédéfini de la visionneuse. Une fois que vous avez copié l’URL, elle se trouve dans le presse-papiers ce qui vous permet de la coller dans les pages de votre site web ou de votre application.

>[!NOTE]
>
>Vous ne pouvez pas copier l’URL tant que la ressource sélectionnée n’a pas été publiée. En outre, vous devez également publier le paramètre de visionneuse prédéfini ou le paramètre d’image prédéfini.
>
>Voir [Publication de ressources](publishing-dynamicmedia-assets.md).
>
>Voir [Publication de paramètres de visionneuse prédéfinis](managing-viewer-presets.md#publishing-viewer-presets).
>
>Voir [Publication de paramètres d’image prédéfinis](managing-image-presets.md#publishing-image-presets).

Il existe différents moyens d’obtenir une chaîne URL. Néanmoins, les étapes ci-dessous ne vous présentent qu’une seule méthode.

**Obtention de l’URL d’une ressource:**

1. Accédez à la ressource *publiée* dont vous souhaitez copier l’URL du paramètre d’image ou de visionneuse prédéfini, puis appuyez sur la ressource pour l’ouvrir.

   N’oubliez pas que les URL ne peuvent être copiées qu’*après* la *publication* des ressources. En outre, le paramètre de visionneuse prédéfini ou le paramètre d’image prédéfini doit également être publié.

   Voir [Publication de ressources](publishing-dynamicmedia-assets.md).

   Voir [Publication de paramètres de visionneuse prédéfinis](managing-viewer-presets.md#publishing-viewer-presets).

   Voir [Publication de paramètres d’image prédéfinis](managing-image-presets.md#publishing-image-presets).

1. Selon la ressource sélectionnée, procédez comme suit :

   * Si vous avez sélectionné une image, dans le menu déroulant, appuyez sur **[!UICONTROL Rendus]**.

      Sous l’en-tête **[!UICONTROL Dynamique]**, appuyez sur un nom de paramètre prédéfini afin d’afficher son rendu dans le cadre de droite. Si nécessaire, faites défiler la liste Rendus pour afficher l’en-tête Dynamique .

      Dans la partie inférieure du rail gauche, appuyez sur **[!UICONTROL URL]**.

      ![chlimage_1-270](assets/chlimage_1-270.png)

   * Si vous avez sélectionné une visionneuse à 360°, une visionneuse d’images, un ensemble de carrousel ou une vidéo, dans le menu déroulant, appuyez sur **[!UICONTROL Visionneuses]**.

      Dans le rail de gauche, appuyez sur un nom de paramètre prédéfini de la visionneuse. Un aperçu de la visionneuse ou de la vidéo s’ouvre dans une page distincte.

      Dans le rail de gauche, dans la partie inférieure, appuyez sur **[!UICONTROL URL]**.

      ![chlimage_1-271](assets/chlimage_1-271.png)

1. Pour prévisualiser la ressource ou l’ajouter à votre page de contenu web, sélectionnez le texte et copiez-le dans votre navigateur web.

   Pour fermer la fenêtre d’URL, appuyez sur **[!UICONTROL X]** ou sur **[!UICONTROL Fermer]**.

## Obtention d’une URL pour une ressource statique {#obtaining-a-url-for-a-static-asset}

Dynamic Media prend en charge la diffusion de ressources statiques, qui sont d’autres ressources que des images et des vidéos. Les formats de ressources statiques pris en charge pour la diffusion comprennent les formats suivants :

* Fichiers 3D
* GIF animé
* Fichiers audio
* CSS
* JavaScript™ (lorsque votre entreprise est configurée avec son propre domaine)
* PDF
* SVG
* XML
* ZIP

**Obtention de l’URL d’une ressource statique:**

1. Accédez à la ressource statique *publiée* dont vous souhaitez copier l’URL et appuyez dessus pour l’ouvrir.

   N’oubliez pas que les URL ne peuvent être copiées qu’*après* la *publication* de la ressource statique.

   Voir [Publication de ressources](publishing-dynamicmedia-assets.md).

1. Utilisez l’une des méthodes suivantes pour obtenir l’URL de la ressource statique publiée :

   * `The URL of the published static is the following:`

      * `https://*<server_name>*/is/content/*<company_name>*/*<static_asset_filename>*.*<extension>*`

         Par exemple, `https://aem.com/is/content/adobe/image.gif`.
   * Appuyez sur **[!UICONTROL Ressource > Rendu(s) dynamique(s)]**, puis sur le rendu dynamique de la ressource statique et copiez l’URL.

      Modifiez l’URL copiée afin d’utiliser `is/content` au lieu de `is/image/` dans le chemin d’accès.


## Obtention d’une URL de vidéo pour un rendu vidéo publié {#obtaining-a-video-url-for-a-published-video-rendition}

1. Dans Experience Manager, accédez à **[!UICONTROL Outils]** > **[!UICONTROL Déploiement]** > **[!UICONTROL Cloud]** > **[!UICONTROL Cloud Services]**.
1. Sur la page **[!UICONTROL Cloud Services]**, faites défiler l’écran jusqu’au titre **[!UICONTROL Dynamic Media Cloud Services]**, puis cliquez sur **[!UICONTROL Afficher les configurations]**.
1. Sous **[!UICONTROL Configurations disponibles]**, appuyez sur le nom de la configuration qui vous intéresse.

1. Sur la page **[!UICONTROL Paramètres de cloud Dynamic Media]**, sous **[!UICONTROL URL du service vidéo]**, copiez le chemin URL complet. Vous aurez besoin du chemin d’URL copié plus loin dans les étapes.

   Par exemple, le chemin de l’URL peut ressembler à ce qui suit :

   `https://s7athens.macromedia.com:9090/DMGateway/`

   (Le chemin ci-dessus est fourni à titre d’explication uniquement ; il ne s’agit pas du chemin d’accès réel que vous copiez.)

1. Sous **[!UICONTROL ID d’enregistrement]**, copiez le nom du client dans la dernière partie de l’ID.

   Par exemple, si l’ID d’enregistrement est `87654321|MyCompany`, le nom du client est `MyCompany`.

1. Dans le coin supérieur gauche de la page, appuyez sur **[!UICONTROL Cloud Services]**, puis appuyez sur l’icône du Experience Manager et accédez à **[!UICONTROL Général]** > **[!UICONTROL CRXDE Lite]**.
1. Copiez le chemin d’accès complet au rendu vidéo depuis le JCR (référentiel de contenu Java™).

   Par exemple, le chemin du rendu de la vidéo peut ressembler à ce qui suit :

   `/_renditions_/0bd/0bd28743-a616-4fe6-92aa-6eae7c2112f/avs/Momentum_1080-0x720-2600k.mp4`

   (Le chemin ci-dessus est fourni à titre d’explication uniquement ; il ne s’agit pas du chemin d’accès réel que vous copiez.)

1. Pour former un chemin URL complet, organisez les informations copiées dans l’ordre suivant :

   `<Video_Service_URL>/public/<Customer_name_from_Registration_ID>/<Video_rendition_path>`

   Si l’on reprend les exemples de chemin et de nom de client ci-dessus, le chemin d’accès complet est le suivant :

   `https://s7athens.macromedia.com:9090/DMGateway/public/MyCompany/_renditions_/0bd/0bd28743-a616-4fe6-92aa-6eae7c2112ff/avs/Momentum_1080-0x720-2600k.mp4`

   Ce chemin d’accès est l’URL complète d’un rendu vidéo publié.

## Obtention d’une URL de vidéo pour la diffusion adaptative (HLS)  {#obtaining-a-video-url-for-adaptive-streaming-hls}

1. Dans Experience Manager, accédez à **[!UICONTROL Outils]** > **[!UICONTROL Déploiement]** > **[!UICONTROL Cloud]** > **[!UICONTROL Cloud Services]**.
1. Sur la page **[!UICONTROL Cloud Services]**, faites défiler l’écran jusqu’au titre **[!UICONTROL Dynamic Media Cloud Services]**, puis cliquez sur **[!UICONTROL Afficher les configurations]**.
1. Sous **[!UICONTROL Configurations disponibles]**, appuyez sur le nom de la configuration qui vous intéresse.
1. Sur la page **[!UICONTROL Paramètres Dynamic Media Cloud Services]**, procédez comme suit :

   * Sous **[!UICONTROL URL du service vidéo]**, copiez le chemin d’URL entier. Vous aurez besoin du chemin d’URL copié plus loin dans ces étapes. Par exemple, le chemin de l’URL peut ressembler à ce qui suit :

   `https://gateway-na.assetsadobe.com/DMGateway/`

   (Le chemin ci-dessus est fourni à titre d’explication uniquement ; il ne s’agit pas du chemin d’accès réel que vous copiez.)

   * Sous **[!UICONTROL ID d’enregistrement]**, copiez le nom du client dans la dernière partie de l’ID. Vous aurez besoin du nom du client copié plus loin dans ces étapes.

      Par exemple, si l’ID d’enregistrement est `87654321|demoCo`, le nom du client est `demoCo`.


1. En fonction du protocole de diffusion vidéo que vous utilisez, copiez le sélecteur de protocole correspondant. Vous aurez besoin du sélecteur de protocole copié plus loin dans ces étapes.

   <table>
    <tbody>
      <tr>
      <td><strong>Protocole de diffusion vidéo que vous utilisez</strong></td>
      <td><strong>Sélecteur de protocole à utiliser</strong></td>
      </tr>
      <tr>
      <td><p>HTTP</p> <p>Si vous utilisez HTTP (diffusion vidéo non sécurisée), assurez-vous de remplacer <code>https</code> par <code>http</code> dans la valeur URL du service vidéo que vous avez copiée précédemment.</p> </td>
      <td><code>public/</code></td>
      </tr>
      <tr>
      <td>HTTPS</td>
      <td><code>public-ssl/</code></td>
      </tr>
    </tbody>
   </table>

1. Copiez le chemin complet de la ressource vidéo en Experience Manager, tel qu’il est traité par Dynamic Media. Vous aurez besoin de ce chemin d’accès à la ressource vidéo copié plus loin dans ces étapes.

   Par exemple :

   `/content/dam/marketing/MyVideo.mp4`

1. Combinez tous les éléments copiés précédemment pour créer une chaîne dans l’ordre suivant :

   &lt; `video service URL`>&lt; `protocol selector`>&lt; `customer name`>&lt; `video asset path`>

   Par exemple, en utilisant les informations copiées à partir des exemples de ces étapes, la chaîne apparaît comme suit :

   `https://gateway-na.assetsadobe.com/DMGateway/public-ssl/demoCo/content/dam/marketing/MyVideo.mp4`

1. Complétez l’URL en ajoutant `.m3u8` à la fin de la chaîne. Par exemple, en ajoutant `.m3u8` à la chaîne de l’étape précédente, le chemin d’accès complet de l’URL se présenterait comme suit :

   `https://gateway-na.assetsadobe.com/DMGateway/public-ssl/demoCo/content/dam/marketing/MyVideo.mp4.m3u8`

## Utilisation de HTTP/2 pour diffuser vos ressources Dynamic Media {#using-http-to-deliver-your-dynamic-media-assets}

HTTP/2 est le nouveau protocole web qui améliore la manière dont les serveurs et les navigateurs communiquent. Il permet un transfert rapide d’informations et réduit la puissance de traitement nécessaire. Les ressources Dynamic Media peuvent désormais être diffusées sur HTTP/2, un protocole qui garantit de meilleurs temps de réponse et de chargement.

Voir [Diffusion du contenu sur HTTP2](http2faq.md) pour tout savoir sur l’utilisation du protocole HTTP/2 avec votre compte Dynamic Media.
