---
title: Invalidation du cache CDN (réseau de diffusion de contenu) par le biais de Dynamic Media Classic
description: « Apprenez comment l’invalidation du contenu de réseau de diffusion de continu (CDN) en cache vous permet de mettre à jour rapidement les ressources diffusées par Dynamic Media, au lieu d’attendre l’expiration du cache. »
feature: Gestion des ressources,Dynamic Media Classic
role: Admin,User
exl-id: 7e488699-5633-437f-9e2e-58c98aa13145
source-git-commit: 24a4a43cef9a579f9f2992a41c582f4a6c775bf3
workflow-type: tm+mt
source-wordcount: '693'
ht-degree: 100%

---

# Invalidation du cache de réseau CDN par le biais de Dynamic Media Classic {#invalidating-your-cdn-cached-content}

Les ressources Dynamic Media sont mises en cache par le réseau de diffusion de contenu (CDN) pour une diffusion rapide. Cependant, lorsque vous appliquez des mises à jour à une ressource, vous pouvez faire en sorte qu’elles soient prises immédiatement en compte. L’invalidation du CDN en cache vous permet de mettre à jour rapidement les ressources diffusées par Dynamic Media, au lieu d’attendre l’expiration du cache.

>[!NOTE]
>
>Cette fonctionnalité nécessite l’utilisation du réseau CDN prêt à l’emploi fourni avec Adobe Experience Manager Dynamic Media. Aucun autre réseau CDN personnalisé n’est pris en charge avec cette fonctionnalité.

>[!IMPORTANT]
>
>Ces étapes s’appliquent uniquement à Dynamic Media dans Experience Manager 6.5, Service Pack 5 ou version antérieure. <!-- If you are using Dynamic Media in AEM as a Cloud Service, [use the new steps found here](/help/assets/invalidate-cdn-cache-dynamic-media.md). -->

Voir aussi [Présentation du cache dans Dynamic Media Classic](https://helpx.adobe.com/fr/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html).

**Pour invalider votre cache de réseau CDN au moyen de Dynamic Media Classic :**

1. Ouvrez [l’application de bureau Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html?lang=fr#getting-started) puis connectez-vous à votre compte.

   Vos informations d’identification et de connexion vous ont été communiquées par Adobe au moment de la configuration. Si vous ne disposez pas de ces informations, contactez l’assistance technique.

1. Cliquez sur **[!UICONTROL Configuration]** > **[!UICONTROL Configuration de l’application]** > **[!UICONTROL Paramètres généraux]**.
1. Recherchez la zone de texte **[!UICONTROL Modèle d’invalidation sur le réseau de diffusion de contenu]** dans la section Serveurs de la page Paramètres généraux de l’application.

1. Précisez le modèle utilisé pour invalider le cache du réseau de diffusion de contenu (CDN).

   Supposons, par exemple, que vous saisissiez une URL d’image (comprenant des paramètres d’image prédéfinis et des modificateurs) faisant référence à `<ID>`, au lieu d’un ID d’image spécifique, comme dans l’exemple suivant :

   `https://server.com/is/image/Company/<ID>?$product$`

   Si le modèle contient uniquement `<ID>`, Dynamic Media renseigne `https://<server>/is/image`, où `<server>` désigne le nom du serveur de publication défini dans les paramètres généraux et où &lt;ID> correspond aux ressources dont la validité doit être annulée.

1. Dans le coin inférieur droit de la page, appuyez sur **[!UICONTROL Fermer]**.
1. Dans l’interface utilisateur de Dynamic Media Classic (Scene7), sélectionnez une ou plusieurs ressources, puis appuyez sur **[!UICONTROL ****Fichier > Invalider sur le réseau de diffusion de contenu]**. La liste qui s’affiche alors se compose d’une ou de plusieurs URL générées à partir du modèle que vous avez créé et des ressources que vous avez sélectionnées. Elle utilise l’URL du serveur répertoriée sous « Nom du serveur de publication » dans les paramètres généraux de l’application.

   Par exemple, avec le modèle d’invalidation défini à l’étape précédente, supposons que vous sélectionniez une seule image de ressource nommée `Backpack_B`. Lorsque vous appuyez sur **[!UICONTROL Fichier]** > **[!UICONTROL Invalider sur le réseau de diffusion de contenu]**, l’URL suivante est générée dans l’interface utilisateur d’invalidation sur le réseau de diffusion de contenu :

   `https://server.com/is/image/Company/Backpack_B?$product$`

1. Dans la zone Liste d’URL, appuyez sur **[!UICONTROL Continuer]** pour effacer le cache de chaque URL spécifique. Vous pouvez modifier une URL ou en ajouter une en la saisissant ou en la copiant dans la zone Liste d’URL ; il n’est pas nécessaire de définir le modèle d’invalidation sur le réseau de diffusion de contenu au préalable.

   Après avoir appuyé sur **[!UICONTROL Continuer]**, un indicateur s’affiche pour vous donner une estimation de la durée nécessaire pour effacer le cache.

   Si vous avez sélectionné plusieurs ressources, puis appuyé sur **[!UICONTROL Fichier]** > **[!UICONTROL Invalider sur le réseau de diffusion de contenu]**, chaque ressource est référencée dans l’**[!UICONTROL URL du modèle]** enregistrée. Par conséquent, vous pouvez définir un **[!UICONTROL modèle d’invalidation sur le réseau de diffusion de contenu]** faisant référence à chaque URL de paramètre d’image prédéfini qui figure sur votre site web comme les détails d’un produit et les résultats de recherche. Par la suite, lorsque vous sélectionnerez une ou plusieurs images à invalider dans le cache, les URL seront automatiquement renseignées dans l’interface.

   >[!NOTE]
   >
   >Lorsque vous sélectionnez des ressources, puis appuyez sur **[!UICONTROL Fichier]** > **[!UICONTROL Invalider sur le réseau de diffusion de contenu]**, Dynamic Media utilise un modèle d’invalidation pour créer automatiquement des URL à invalider dans le CDN. Si rien n’est renseigné dans la zone de texte **[!UICONTROL Modèle d’invalidation sur le réseau de diffusion de contenu]**, la liste d’URL renvoyée est vide. La mise en cache sur le réseau de diffusion de contenu n’est pas basée sur les ressources ; elle est basée sur des URL. Il est donc nécessaire de connaître les URL complètes qui se trouvent sur votre site web. Dès que vous avez déterminé ces URL, vous pouvez les ajouter dans la zone de texte **[!UICONTROL Modèle d’invalidation sur le réseau de diffusion de contenu]** (voir les étapes précédentes). Vous pouvez ensuite sélectionner ces ressources et invalider les URL en une seule étape.
   >
   >Une autre option consiste à ajouter des URL complètes dans la liste **[!UICONTROL Invalider sur le réseau de diffusion de contenu]**. Si vous optez pour cette méthode, il n’est pas nécessaire de sélectionner des ressources dans Dynamic Media Classic avant d’accéder à l’option **[!UICONTROL Fichier]** > **[!UICONTROL Invalider sur le réseau de diffusion de contenu]**.
