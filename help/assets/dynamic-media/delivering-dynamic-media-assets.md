---
title: Diffusion de ressources Dynamic Media
description: Découvrez comment diffuser des ressources Dynamic Media vers vos pages web par le biais de vidéos et d’images incorporées ou en liant des URL à votre application web.
contentOwner: Rick Brough
feature: Asset Management
role: User
exl-id: 4557b561-b3c4-4d6f-8044-2069bda41613
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 93%

---

# Diffusion de ressources Dynamic Media{#delivering-dynamic-media-assets}

La diffusion des ressources Dynamic Media (vidéos et images) dépend de la mise en œuvre de votre site web.

Avec Dynamic Media, vous disposez de plusieurs options :

* Si votre site web est hébergé sur Adobe Experience Manager, vous souhaiterez ajouter les ressources Dynamic Media directement à votre page.
* Si votre site web n’est pas hébergé par Experience Manager, les possibilités suivantes s’offrent à vous :

   * Incorporation de votre vidéo ou image sur votre site Web.
   * Liez des URL à votre application web. Utilisez la liaison lorsque vous souhaitez présenter un lecteur vidéo dans une fenêtre pop-up ou modale.
   * Si votre site est réactif, vous pouvez [diffuser des images optimisées](/help/assets/dynamic-media/responsive-site.md).

>[!NOTE]
>
>L’imagerie dynamique fonctionne avec vos paramètres d’image prédéfinis existants. Elle utilise les informations disponibles à la dernière milliseconde avant la diffusion pour réduire encore la taille du fichier image en fonction de la vitesse de connexion du navigateur ou du réseau. Voir [Imagerie numérique](/help/assets/dynamic-media/imaging-faq.md) pour plus d’informations.

Pour plus d’informations, reportez-vous aux rubriques suivantes :

* [Ajout de ressources Dynamic Media aux pages web](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md)
* [Intégration de la visionneuse de vidéos ou d’images à une page web](/help/assets/dynamic-media/embed-code.md)
* [Activation de la protection de lien dynamique dans Dynamic Media](/help/assets/dynamic-media/hotlink-protection.md)
* [Liaison d’URL à votre application web](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md)
* [Diffusion d’images optimisées pour un site réactif](/help/assets/dynamic-media/responsive-site.md)
* [Diffusion de contenu HTTP/2](/help/assets/dynamic-media/http2faq.md)
* [Invalidation du cache de réseau CDN par le biais de Dynamic Media](/help/assets/dynamic-media/invalidate-cdn-cache-dynamic-media.md)
* [Invalidation du cache de réseau CDN par le biais de Dynamic Media Classic](/help/assets/dynamic-media/invalidate-cdn-cache-dm-classic.md)
* [Utilisation de jeux de règles de transformation d’URL](/help/assets/dynamic-media/using-rulesets-to-transform-urls.md)

## Diffusion de ressources Dynamic Media via HTTP/2 {#http-delivery-of-dynamic-media-assets}

Experience Manager prend à présent en charge la diffusion de tout le contenu Dynamic Media (images et vidéo) sur HTTP/2. En d’autres termes, une URL publiée ou un code incorporé pour l’image ou la vidéo peut être intégré à toute application qui accepte une ressource hébergée. Cette ressource publiée est ensuite diffusée au moyen du protocole HTTP/2. Cette méthode de distribution améliore la communication entre les navigateurs et les serveurs, ce qui permet d’améliorer les temps de réponse et de chargement de toutes vos ressources Dynamic Media.

Pour en savoir plus, consultez [Foire aux questions sur la diffusion HTTP/2 du contenu](/help/assets/dynamic-media/http2faq.md).
