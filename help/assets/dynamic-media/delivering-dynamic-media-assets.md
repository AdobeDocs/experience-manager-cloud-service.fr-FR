---
title: Diffusion de ressources Dynamic Media
description: Découvrez comment diffuser des ressources Dynamic Media.
feature: Gestion des ressources
role: Business Practitioner
exl-id: 4557b561-b3c4-4d6f-8044-2069bda41613
translation-type: tm+mt
source-git-commit: e94289bccc09ceed89a2f8b926817507eaa19968
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 77%

---

# Diffusion de ressources Dynamic Media{#delivering-dynamic-media-assets}

La diffusion des ressources Dynamic Media (vidéos et images) dépend de la mise en œuvre de votre site web.

Avec Dynamic Media, vous disposez de plusieurs options :

* Si votre site Web est hébergé sur AEM, vous souhaitez ajouter les ressources Dynamic Media directement à votre page.
* Si votre site web n’est pas hébergé par AEM, les possibilités suivantes s’offrent à vous :

   * Intégration de votre vidéo ou image à votre site web.
   * Liez des URL à votre application web. Utilisez la liaison lorsque vous souhaitez présenter un lecteur vidéo dans une fenêtre contextuelle ou modale.
   * Si votre site est réactif, vous pouvez [diffuser des images optimisées](/help/assets/dynamic-media/responsive-site.md).

>[!NOTE]
>
>L’imagerie intelligente fonctionne avec vos paramètres d’image prédéfinis existants. Il utilise les informations à la dernière milliseconde de diffusion pour réduire davantage la taille du fichier image en fonction de la vitesse de connexion du navigateur ou du réseau. Voir [Imagerie numérique](/help/assets/dynamic-media/imaging-faq.md) pour plus d’informations.

Pour plus d’informations, reportez-vous aux rubriques suivantes :

* [Ajout de ressources Dynamic Media aux pages web](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md)
* [Incorporation de la visionneuse de vidéos ou d’images dans une page web](/help/assets/dynamic-media/embed-code.md)
* [Activation de la protection de lien dynamique dans Dynamic Media](/help/assets/dynamic-media/hotlink-protection.md)
* [Liaison d’URL à une application web](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md)
* [Diffusion d’images optimisées pour un site réactif](/help/assets/dynamic-media/responsive-site.md)
* [Diffusion de contenu HTTP/2](/help/assets/dynamic-media/http2faq.md)
* [Invalidation du cache du réseau CDN par le biais de Dynamic Media](/help/assets/dynamic-media/invalidate-cdn-cache-dynamic-media.md)
* [Invalidation du cache du réseau CDN par le biais de Dynamic Media Classic](/help/assets/dynamic-media/invalidate-cdn-cache-dm-classic.md)
* [Utilisation de jeux de règles de transformation d’URL](/help/assets/dynamic-media/using-rulesets-to-transform-urls.md)

## Diffusion de ressources Dynamic Media via HTTP/2 {#http-delivery-of-dynamic-media-assets}

AEM prend à présent en charge la diffusion de tout le contenu Dynamic Media (images et vidéo) sur HTTP/2. En d’autres termes, une URL publiée ou un code intégré pour l’image ou la vidéo peut être intégré dans toute application acceptant une ressource hébergée. Cette ressource publiée est alors distribuée par le biais du protocole HTTP/2. Cette méthode de distribution améliore la communication entre les navigateurs et les serveurs, ce qui permet d’améliorer les temps de réponse et de chargement de toutes vos ressources Dynamic Media.

Pour en savoir plus, voir [HTTP/2 Diffusion du contenu Foire aux questions](/help/assets/dynamic-media/http2faq.md).
