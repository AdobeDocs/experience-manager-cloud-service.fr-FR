---
title: Publication de ressources Dynamic Media
description: Découvrez comment publier des ressources Dynamic Media.
contentOwner: Rick Brough
translation-type: tm+mt
source-git-commit: fd75af0bf0c16e20c3b98703af14f329ea6c6371
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 98%

---


# Publication de ressources Dynamic Media  {#publishing-dynamic-media-assets}

Vous publiez vos ressources Dynamic Media en sélectionnant celles que vous avez déjà chargées et en appuyant sur **[!UICONTROL Publier]** ou **[!UICONTROL Publication rapide]**. Une fois vos ressources Dynamic Media publiées, vous pouvez les inclure dans une page web au moyen d’une URL ou d’une incorporation de code sur la page.

Vous pouvez également publier immédiatement les ressources que vous chargez, sans intervention de l’utilisateur. Vous pouvez également publier ces ressources de manière sélective. Voir [Configuration de Dynamic Media.](config-dm.md) Vous pouvez également publier des ressources de manière sélective sur Dynamic Media exclusivement ou sur AEM exclusivement, à l’aide d’une **[!UICONTROL Publication sélective]** au niveau des dossiers. Voir [Utilisation de la publication sélective dans Dynamic Media.](/help/assets/dynamic-media/selective-publishing.md)

En **[!UICONTROL mode Carte]**, une petite icône en forme de globe apparaît directement sous le nom d’une ressource et à gauche de la date et de l’heure pour indiquer qu’elle est publiée. En **[!UICONTROL mode Liste]**, une colonne **[!UICONTROL Publié]** indique les ressources qui sont publiées et celles qui ne le sont pas.

>[!NOTE]
>
>Si une ressource est déjà publiée et que vous utilisez AEM pour la déplacer vers un autre dossier et la republier à partir du nouvel emplacement, l’emplacement d’origine de la ressource publiée est toujours disponible, avec la ressource republiée. La ressource d’origine publiée est toutefois « perdue » pour AEM et sa publication ne peut pas être annulée. Il est par conséquent recommandé d’annuler la publication des ressources avant de les déplacer vers un autre dossier.

Si vous envisagez de publier des ressources vidéo immédiatement après les avoir codées, vérifiez que le codage est entièrement terminé. Lorsque des vidéos sont en cours de codage, le système vous informe qu’un workflow de traitement vidéo est en cours. Lorsque le codage vidéo est terminé, vous êtes en mesure de prévisualiser les rendus vidéo. À ce stade, vous pouvez publier les vidéos sans rencontrer d’erreurs de publication.

Voir aussi [Liaison d’URL à une application web.](linking-urls-to-yourwebapplication.md)

Voir aussi [Intégration de la visionneuse de vidéos ou d’images Dynamic Media dans une page web.](embed-code.md)

>[!NOTE]
>
>* Pour utiliser l’URL, les ressources doivent être publiées. Si les ressources ne sont pas publiées, la copie et le collage de l’URL ne fonctionnent pas dans un navigateur web.
>* Les paramètres d’image prédéfinis et les paramètres de visionneuse prédéfinis doivent être activés et publiés pour une diffusion en direct.

>



Pour plus d’informations sur la publication d’une visionneuse ou d’une ressource, reportez-vous à la section [Publication de ressources.](/help/assets/manage-digital-assets.md)

## Diffusion de ressources Dynamic Media via HTTP/2   {#http-delivery-of-dynamic-media-assets}

AEM prend à présent en charge la diffusion de tout le contenu Dynamic Media (images et vidéo) sur HTTP/2. En d’autres termes, une URL publiée ou un code intégré pour l’image ou la vidéo peut être intégré dans toute application acceptant une ressource hébergée. Cette ressource publiée est alors distribuée par le biais du protocole HTTP/2. Cette méthode de distribution améliore la communication entre les navigateurs et les serveurs, ce qui permet d’améliorer les temps de réponse et de chargement de toutes vos ressources Dynamic Media.

Pour en savoir plus, reportez-vous aux [Questions fréquentes sur la diffusion de contenu HTTP/2](/help/assets/dynamic-media/http2faq.md).
<!--this md file used to reside under sites-administering-->
