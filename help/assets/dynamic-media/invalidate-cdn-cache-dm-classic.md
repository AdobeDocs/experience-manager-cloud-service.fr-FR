---
title: Invalidation du cache de réseau CDN par le biais de Dynamic Media Classic
description: '"Découvrez comment invalider votre contenu mis en cache CDN (Content Diffusion Network) afin de vous permettre de mettre rapidement à jour les ressources fournies par Dynamic Media, au lieu d’attendre l’expiration du cache."'
feature: Gestion des ressources,Dynamic Media Classic
topic: Professionnel
translation-type: tm+mt
source-git-commit: 80a59a02067d478713aa7dcdb436ad1345d89c1a
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 46%

---


# Invalidation du cache de réseau CDN par le biais de Dynamic Media Classic {#invalidating-your-cdn-cached-content}

Les ressources Dynamic Media sont mises en cache par le réseau CDN (Content Diffusion Network) pour une diffusion rapide. Cependant, lorsque vous apportez des mises à jour à une ressource, vous souhaitez que ces modifications prennent effet immédiatement. L’invalidation du contenu mis en cache sur le réseau de diffusion de contenu vous permet de mettre rapidement à jour les ressources fournies par Dynamic Media, plutôt que d’attendre l’expiration du cache.

>[!NOTE]
>
>Cette fonctionnalité nécessite l’utilisation du CDN prêt à l’emploi fourni avec Adobe Experience Manager Dynamic Media. Aucun autre CDN personnalisé n’est pris en charge avec cette fonctionnalité.

>[!IMPORTANT]
>
>Ces étapes s’appliquent uniquement à Dynamic Media dans AEM 6.5, Service Pack 5 ou version antérieure. <!-- If you are using Dynamic Media in AEM as a Cloud Service, [use the new steps found here](/help/assets/invalidate-cdn-cache-dynamic-media.md). -->

Voir aussi [Présentation du cache dans Dynamic Media Classic](https://helpx.adobe.com/fr/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html).

**Pour invalider votre cache de réseau CDN au moyen de Dynamic Media Classic :**

1. Ouvrez [l’application de bureau Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html?lang=fr#getting-started) puis connectez-vous à votre compte.

   Vos informations d’identification et de connexion ont été fournies par l’Adobe au moment de l’attribution des privilèges d’accès. Si vous ne disposez pas de ces informations, contactez l’assistance technique.

1. Cliquez sur **[!UICONTROL Configuration > Configuration de l’application > Paramètres généraux]**.
1. Recherchez la zone de texte **[!UICONTROL Modèle d’invalidation sur le réseau de diffusion de contenu]** dans la section Serveurs de la page Paramètres généraux de l’application.

1. Précisez le modèle utilisé pour invalider le cache du réseau de diffusion de contenu (CDN).

   Supposons, par exemple, que vous saisissiez une URL d’image (comprenant des paramètres d’image prédéfinis et des modificateurs) faisant référence à `<ID>`, au lieu d’un ID d’image spécifique, comme dans l’exemple suivant :

   `https://server.com/is/image/Company/<ID>?$product$`

   Si le modèle contient uniquement `<ID>`, Dynamic Media remplit `https://<server>/is/image` où `<server>` correspond au nom du serveur de publication défini dans Paramètres généraux et &lt;ID> aux actifs sélectionnés pour invalidation.

1. Dans le coin inférieur droit de la page, appuyez sur **[!UICONTROL Fermer]**.
1. Dans l’interface utilisateur Dynamic Media Classic (Scene7), sélectionnez un ou plusieurs fichiers, puis appuyez sur **[!UICONTROL Fichier > Invalider CDN]**. Une liste d’une ou de plusieurs URL générées à partir du modèle que vous avez créé et des ressources que vous avez sélectionnées s’affiche. Elle utilise l’URL du serveur répertoriée sous « Nom du serveur de publication » dans les paramètres généraux de l’application.

   Par exemple, avec le modèle d’invalidation défini à l’étape précédente, supposons que vous sélectionniez une seule image de ressource nommée `Backpack_B`. Lorsque vous appuyez sur **[!UICONTROL Fichier > Invalider le CDN]**, l’URL suivante est générée dans l’interface utilisateur de l’invalidation du CDN :

   `https://server.com/is/image/Company/Backpack_B?$product$`

1. Dans la zone liste de l’URL, appuyez sur **[!UICONTROL Continuer]** pour effacer le cache de chaque URL spécifique. Vous pouvez modifier une URL ou ajouter une URL en la saisissant ou en la collant dans la zone liste d’URL ; vous n’avez pas besoin de définir le modèle CDN Invalidate au préalable.

   Après avoir appuyé sur **[!UICONTROL Continuer]**, un indicateur s’affiche qui vous donne une estimation du temps nécessaire pour vider le cache.

   Si vous avez sélectionné plusieurs fichiers, puis appuyé sur **[!UICONTROL Fichier > Invalider CDN]**, chaque fichier est référencé dans l’URL **[!UICONTROL modèle]** enregistrée. Par conséquent, vous pouvez définir un **[!UICONTROL modèle d’invalidation CDN]** référençant chaque paramètre d’image prédéfini d’URL référencé sur votre site Web, tel que les détails du produit et les résultats de la recherche. Par la suite, lorsque vous sélectionnerez une ou plusieurs images à invalider dans le cache, les URL seront automatiquement renseignées dans l’interface.

   >[!NOTE]
   >
   >Lorsque vous sélectionnez des fichiers, puis appuyez sur **[!UICONTROL Fichier > Invalider CDN]**, Dynamic Media utilise un modèle CDN invalide pour créer automatiquement des URL à invalider à partir du CDN. Si rien n’est renseigné dans la zone de texte **[!UICONTROL Modèle d’invalidation sur le réseau de diffusion de contenu]**, la liste d’URL renvoyée est vide. La mise en cache sur le réseau de diffusion de contenu n’est pas basée sur les ressources ; elle est basée sur des URL. Il est donc nécessaire de connaître les URL complètes qui se trouvent sur votre site web. Dès que vous avez déterminé ces URL, vous pouvez les ajouter dans la zone de texte **[!UICONTROL Modèle d’invalidation sur le réseau de diffusion de contenu]** (voir les étapes précédentes). Vous pouvez ensuite sélectionner ces ressources et invalider les URL en une seule étape.
   >
   >Une autre option consiste à ajouter des URL complètes dans la liste **[!UICONTROL Invalider sur le réseau de diffusion de contenu]**. Si vous optez pour cette méthode, il n’est pas nécessaire de sélectionner des ressources dans Dynamic Media Classic avant d’accéder à l’option **[!UICONTROL Fichier > Invalider sur le réseau de diffusion de contenu]**.

