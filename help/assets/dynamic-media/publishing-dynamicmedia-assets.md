---
title: Publication de ressources Dynamic Media
description: Découvrez comment publier des ressources Dynamic Media.
contentOwner: Rick Brough
feature: Gestion des ressources
role: Business Practitioner
exl-id: 8ee759dc-cb8f-4e80-8175-2c3ba06da862
source-git-commit: d3ee23917eba4a2e4ae1f2bd44f5476d2ff7dce1
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 56%

---

# Publication de ressources Dynamic Media {#publishing-dynamic-media-assets}

Vous publiez vos ressources Dynamic Media en sélectionnant celles que vous avez déjà chargées et en appuyant sur **[!UICONTROL Publier]** ou **[!UICONTROL Publication rapide]**. Une fois vos ressources Dynamic Media publiées, vous pouvez les inclure dans une page web au moyen d’une URL ou d’une incorporation de code sur la page.

Vous pouvez également publier instantanément les ressources que vous chargez, sans intervention de l’utilisateur. Vous pouvez également publier ces ressources de manière sélective. Voir [Configuration de Dynamic Media](config-dm.md). Vous pouvez également publier sélectivement des ressources dans Dynamic Media ou Adobe Experience Manager, mutuellement exclusives les unes des autres, à l’aide de la fonction **[!UICONTROL Publication sélective]** au niveau du dossier. Voir [Utilisation de la publication sélective dans Dynamic Media](/help/assets/dynamic-media/selective-publishing.md).

En **[!UICONTROL mode Carte]**, une petite icône en forme de globe apparaît directement sous le nom d’une ressource et à gauche de la date et de l’heure pour indiquer qu’elle est publiée. En **[!UICONTROL mode Liste]**, une colonne **[!UICONTROL Publié]** indique les ressources qui sont publiées et celles qui ne le sont pas.

>[!NOTE]
>
>Si une ressource est déjà publiée, puis que vous la déplacez vers un autre dossier et que vous la republiez à partir de son nouvel emplacement, l’emplacement de la ressource publiée d’origine est toujours disponible, ainsi que la ressource qui vient d’être republiée. Toutefois, la ressource publiée d’origine est &quot;perdue&quot; pour le Experience Manager et ne peut pas être annulée. Par conséquent, il est recommandé d’annuler la publication des ressources avant de les déplacer vers un autre dossier.

Si vous avez l’intention de publier des ressources vidéo immédiatement après les avoir codées, assurez-vous que le codage est terminé. Lorsque des vidéos sont en cours de codage, le système vous informe qu’un workflow de traitement vidéo est en cours. Lorsque le codage vidéo est terminé, vous pouvez prévisualiser les rendus vidéo. À ce stade, vous pouvez publier en toute sécurité les vidéos, sans entraîner aucune erreur de publication.

Voir aussi [Liaison d’URL à une application web](linking-urls-to-yourwebapplication.md).

Voir aussi [Intégration de la visionneuse de vidéos ou d’images Dynamic Media dans une page web](embed-code.md).

>[!NOTE]
>
>* Les ressources doivent être publiées pour utiliser l’URL. Si les ressources ne sont pas publiées, la copie et le collage de l’URL dans un navigateur web ne fonctionnent pas.
>* Les paramètres d’image prédéfinis et les paramètres de visionneuse prédéfinis doivent être activés et publiés pour une diffusion en direct.

>



Pour plus d’informations sur la publication d’une visionneuse ou d’une ressource, reportez-vous à la section [Publication de ressources](/help/assets/manage-digital-assets.md).

## Diffusion de ressources Dynamic Media via HTTP/2  {#http-delivery-of-dynamic-media-assets}

Experience Manager prend désormais en charge la diffusion de tout le contenu Dynamic Media (images et vidéo) sur HTTP/2. En d’autres termes, une URL publiée ou un code intégré pour l’image ou la vidéo peut être intégré dans toute application acceptant une ressource hébergée. Cette ressource publiée est alors distribuée par le biais du protocole HTTP/2. Cette méthode de distribution améliore la communication entre les navigateurs et les serveurs, ce qui permet d’améliorer les temps de réponse et de chargement de toutes vos ressources Dynamic Media.

Voir [Diffusion HTTP/2 des questions fréquentes sur le contenu](/help/assets/dynamic-media/http2faq.md).

<!--this md file used to reside under sites-administering-->
