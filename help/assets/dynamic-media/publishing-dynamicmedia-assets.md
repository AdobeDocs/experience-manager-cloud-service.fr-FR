---
title: Publication de ressources Dynamic Media
description: Découvrez comment publier des ressources d’images et des vidéos Dynamic Media afin de les inclure dans une page web au moyen d’une URL ou d’une incorporation de code sur une page web.
contentOwner: Rick Brough
feature: Asset Management
role: User
exl-id: 8ee759dc-cb8f-4e80-8175-2c3ba06da862
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 93%

---

# Publication de ressources Dynamic Media {#publishing-dynamic-media-assets}

Vous publiez vos ressources Dynamic Media en sélectionnant celles que vous avez déjà chargées et en sélectionnant **[!UICONTROL Publier]** ou **[!UICONTROL Publication rapide]**. Une fois vos ressources Dynamic Media publiées, vous pouvez les inclure dans une page web au moyen d’une URL ou d’une incorporation de code sur la page.

Vous pouvez également publier immédiatement les ressources que vous chargez, sans intervention de l’utilisateur. Vous pouvez également publier ces ressources de manière sélective. Voir [Configuration de Dynamic Media](config-dm.md). Vous pouvez également publier des ressources de manière sélective sur Dynamic Media exclusivement ou dans Adobe Experience Manager exclusivement, à l’aide d’une **[!UICONTROL Publication sélective]** au niveau des dossiers. Voir [Utilisation de la publication sélective dans Dynamic Media](/help/assets/dynamic-media/selective-publishing.md).

En **[!UICONTROL mode Carte]**, une petite icône en forme de globe apparaît directement sous le nom d’une ressource et à gauche de la date et de l’heure pour indiquer qu’elle est publiée. Dans la vue **[!UICONTROL Liste]**, une colonne **[!UICONTROL Publié]** indique les ressources qui sont publiées et celles qui ne le sont pas.

>[!NOTE]
>
>Si une ressource est déjà publiée, vous devez utiliser AEM pour la déplacer vers un autre dossier et la republier à partir du nouvel emplacement. L’emplacement de la ressource publiée d’origine est toujours disponible avec la ressource republiée. Toutefois, la ressource publiée d’origine est « perdue » pour Experience Manager et elle ne peut pas être dépubliée. Il est donc recommandé de dépublier les ressources avant de les déplacer vers un autre dossier.

Si vous envisagez de publier des ressources vidéo immédiatement après les avoir codées, vérifiez que l’encodage est terminé. Lorsque les vidéos sont en cours d’encodage, le système vous informe qu’un processus de traitement vidéo est en cours. Lorsque l’encodage vidéo est terminé, vous pouvez prévisualiser les rendus vidéo. À ce stade, vous pouvez publier en toute sécurité les vidéos, sans entraîner aucune erreur de publication.

Voir aussi [Liaison d’URL à une application web](linking-urls-to-yourwebapplication.md).

Voir aussi [Intégration de la visionneuse de vidéos ou d’images Dynamic Media dans une page web](embed-code.md).

>[!NOTE]
>
>* Pour utiliser l’URL, les ressources doivent être publiées. Si les ressources ne sont pas publiées, la copie et le collage de l’URL ne fonctionnent pas dans un navigateur web.
>* Les paramètres d’image prédéfinis et les paramètres de visionneuse prédéfinis doivent être activés et publiés pour une diffusion en direct.
>

Pour plus d’informations sur la publication d’une visionneuse ou d’une ressource, reportez-vous à la section [Publication de ressources](/help/assets/manage-digital-assets.md).

## Diffusion de ressources Dynamic Media via HTTP/2 {#http-delivery-of-dynamic-media-assets}

Experience Manager prend à présent en charge la diffusion de tout le contenu Dynamic Media (images et vidéo) sur HTTP/2. En d’autres termes, une URL publiée ou un code incorporé pour l’image ou la vidéo peut être intégré à toute application qui accepte une ressource hébergée. Cette ressource publiée est ensuite diffusée au moyen du protocole HTTP/2. Cette méthode de distribution améliore la communication entre les navigateurs et les serveurs, ce qui permet d’améliorer les temps de réponse et de chargement de toutes vos ressources Dynamic Media.

Consultez [Questions les plus fréquentes sur la diffusion en HTTP/2 des contenus](/help/assets/dynamic-media/http2faq.md).

<!--this md file used to reside under sites-administering-->
