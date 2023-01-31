---
title: Intégration de la visionneuse de vidéos ou d’images Dynamic Media dans une page web
description: Découvrez comment intégrer des ressources d’images ou des vidéos Dynamic Media dans une page web.
contentOwner: Rick Brough
feature: Asset Management
role: User
exl-id: 76335781-e39f-4aae-967f-5af8634d8f61
source-git-commit: 35caac30887f17077d82f3370f1948e33d7f1530
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 100%

---

# Intégration de la visionneuse de vidéos ou d’images Dynamic Media, ou de la visionneuse dimensionnelle dans une page web {#embedding-the-video-or-image-viewer-on-a-web-page}

Utilisez la fonction **[!UICONTROL Code incorporé]** lorsque vous souhaitez lire une vidéo ou afficher une ressource incorporée dans une page web. Vous copiez le code incorporé dans le Presse-papiers afin de le coller dans vos pages web. Vous ne pouvez pas modifier le code dans la boîte de dialogue **[!UICONTROL Code incorporé]**.

Vous devez incorporer les URL uniquement si vous _n’utilisez pas_ Adobe Experience Manager comme outil de gestion de contenu web. Dans le cas contraire, [vous pouvez ajouter les ressources directement à votre page](adding-dynamic-media-assets-to-pages.md).

Voir [Liaison d’URL à une application web](linking-urls-to-yourwebapplication.md).

Voir [Diffusion d’images optimisées pour un site réactif](responsive-site.md).

>[!NOTE]
>
>Le code incorporé n’est pas disponible pour la copie tant que vous n’avez pas publié la ressource sélectionnée. En outre, vous devez également publier le paramètre de visionneuse prédéfini ou le paramètre d’image prédéfini.
>
>Voir [Publication de ressources](publishing-dynamicmedia-assets.md).
>
>Voir [Publication de paramètres de visionneuse prédéfinis](managing-viewer-presets.md#publishing-viewer-presets).
>
>Voir [Publication de paramètres d’image prédéfinis](managing-image-presets.md#publishing-image-presets).

**Intégration de la visionneuse de vidéos ou d’images Dynamic Media dans une page web:**

1. Accédez à la ressource vidéo ou d’image *publiée* dont vous souhaitez copier le code incorporé.

   N’oubliez pas que le code incorporé n’est disponible à la copie *qu’après* la première *publication* des ressources. En outre, le paramètre de visionneuse prédéfini ou le paramètre d’image prédéfini doit également être publié.

   Voir [Publication de ressources](publishing-dynamicmedia-assets.md).

   Voir [Publication de paramètres de visionneuse prédéfinis](managing-viewer-presets.md#publishing-viewer-presets).

   Voir [Publication de paramètres d’image prédéfinis](managing-image-presets.md#publishing-image-presets).

1. Dans le rail de gauche, sélectionnez la liste déroulante et sélectionnez ensuite **[!UICONTROL Visionneuses]**.
1. Dans le rail de gauche, sélectionnez un nom de paramètre prédéfini de la visionneuse. Le paramètre de visionneuse prédéfini est appliqué à la ressource.
1. Sélectionnez **[!UICONTROL Intégrer]**.
1. Dans la boîte de dialogue **[!UICONTROL Code intégré]**, copiez l’ensemble du code dans le Presse-papiers, puis sélectionnez **[!UICONTROL Fermer]**.
1. Collez le code intégré dans vos pages web.

## Utilisation de HTTP/2 pour diffuser vos ressources Dynamic Media {#using-http-to-deliver-your-dynamic-media-assets}

HTTP/2 est le nouveau protocole web qui améliore la manière dont les serveurs et les navigateurs communiquent. Il permet un transfert rapide d’informations et réduit la puissance de traitement nécessaire. Les ressources Dynamic Media peuvent désormais être diffusées sur HTTP/2, un protocole qui garantit de meilleurs temps de réponse et de chargement.

Voir [Diffusion du contenu sur HTTP2](http2faq.md) pour tout savoir sur l’utilisation du protocole HTTP/2 avec votre compte Dynamic Media.
