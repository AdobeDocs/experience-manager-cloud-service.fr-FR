---
title: Publication de ressources Dynamic Media
description: Découvrez comment publier des ressources Dynamic Media.
contentOwner: Rick Brough
translation-type: tm+mt
source-git-commit: d84a6692f2d0aae496bd2bd98ac99c2663f3fe52
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 77%

---


# Publication de ressources Dynamic Media  {#publishing-dynamic-media-assets}

Pour publier vos fichiers Contenu multimédia dynamique, sélectionnez les fichiers que vous avez déjà téléchargés et appuyez sur **[!UICONTROL Publier]** ou Publication **** rapide. Une fois vos fichiers Contenu multimédia dynamique publiés, vous pouvez les inclure dans une page Web au moyen d’une URL ou en incorporant du code sur la page.

Vous pouvez également publier immédiatement les ressources que vous téléchargez, sans intervention de l’utilisateur. Vous pouvez également publier ces ressources de manière sélective. Voir [Configuration de Dynamic Media](config-dm.md).

Dans la Vue **** Carte, une petite icône en forme de globe apparaît directement sous le nom d’un fichier et à gauche de la date et de l’heure pour indiquer qu’il est publié. En mode **[!UICONTROL Liste]**, une colonne **[!UICONTROL Publié]** indique les ressources qui sont publiées et celles qui ne le sont pas.

>[!NOTE]
>
>Si une ressource est déjà publiée et que vous utilisez AEM pour la déplacer vers un autre dossier et la republier à partir du nouvel emplacement, l’emplacement d’origine de la ressource publiée est toujours disponible, avec la ressource republiée. La ressource d’origine publiée est toutefois « perdue » pour AEM et sa publication ne peut pas être annulée. Il est par conséquent recommandé d’annuler la publication des ressources avant de les déplacer vers un autre dossier.

Si vous envisagez de publier des ressources vidéo immédiatement après les avoir codées, vérifiez que le codage est entièrement terminé. Lorsque des vidéos sont en cours de codage, le système vous informe qu’un workflow de traitement vidéo est en cours. Lorsque le codage vidéo est terminé, vous êtes en mesure de prévisualiser les rendus vidéo. À ce stade, vous pouvez publier les vidéos sans rencontrer d’erreurs de publication.

Voir aussi [Liaison d’URL à une application web](linking-urls-to-yourwebapplication.md).

See also [Embedding the Dynamic Media Video viewer or Image viewer on a web page.](embed-code.md)

>[!NOTE]
>
>* Pour utiliser l’URL, les ressources doivent être publiées. Si les ressources ne sont pas publiées, la copie et le collage de l’URL ne fonctionnent pas dans un navigateur web.
>* Les paramètres d’image prédéfinis et les paramètres de visionneuse prédéfinis doivent être activés et publiés pour une diffusion en direct.
>



Pour plus d’informations sur la publication d’une visionneuse ou d’une ressource, reportez-vous à la section [Publication de ressources.](/help/assets/manage-digital-assets.md)

## Diffusion de ressources Dynamic Media via HTTP/2  {#http-delivery-of-dynamic-media-assets}

AEM prend à présent en charge la diffusion de tout le contenu Dynamic Media (images et vidéo) sur HTTP/2. En d’autres termes, une URL publiée ou un code intégré pour l’image ou la vidéo peut être intégré dans toute application acceptant une ressource hébergée. Cette ressource publiée est alors distribuée par le biais du protocole HTTP/2. Cette méthode de distribution améliore la communication entre les navigateurs et les serveurs, ce qui permet d’améliorer les temps de réponse et de chargement de toutes vos ressources Dynamic Media.

Pour en savoir plus, reportez-vous aux [Questions fréquentes sur la diffusion de contenu HTTP/2](/help/assets/dynamic-media/http2faq.md).
<!--this md file used to reside under sites-administering-->
