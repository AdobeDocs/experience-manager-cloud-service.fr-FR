---
title: Publication de ressources Dynamic Media
description: Découvrez comment publier des ressources Dynamic Media.
translation-type: tm+mt
source-git-commit: c8f8598e3e476af529a87b056e66ddb619a2da0a

---


# Publication de ressources Dynamic Media {#publishing-dynamic-media-assets}

You publish your Dynamic Media assets by selecting the assets and tapping **[!UICONTROL Publish]**. Une fois vos fichiers de médias dynamiques publiés, vous pouvez les inclure dans une page Web par URL ou par incorporation.

Vous pouvez également publier instantanément des fichiers que vous téléchargez, sans intervention de l’utilisateur. Vous pouvez également publier ces fichiers de manière sélective. Voir [Configuration de Dynamic Media](config-dm.md).

Dans le **[!UICONTROL mode Carte]**, une petite icône en forme de globe apparaît directement sous le nom d’un fichier pour indiquer qu’il est publié. En **[!UICONTROL mode Liste]**, une colonne **[!UICONTROL Publié]** indique les fichiers publiés ou non.

>[!NOTE]
>
>Si un fichier est déjà publié, vous utilisez AEM pour déplacer le fichier vers un autre dossier et le republier depuis son nouvel emplacement, l’emplacement du fichier publié d’origine est toujours disponible, ainsi que le fichier récemment republié. La ressource publiée d’origine est toutefois &quot;perdue&quot; pour AEM et ne peut pas être annulée. Par conséquent, il est recommandé d’annuler la publication des fichiers avant de les déplacer vers un autre dossier.

Si vous prévoyez de publier des fichiers vidéo immédiatement après leur codage, assurez-vous que le codage est terminé. Lorsque les vidéos sont toujours codées, le système vous informe qu’un processus de traitement vidéo est en cours. Une fois le codage vidéo effectué, vous devez être en mesure de  les rendus vidéo. A ce stade, vous pouvez publier les vidéos en toute sécurité sans générer d’erreurs de publication.

Reportez-vous également à la section [Liaison d’URL à une application web](linking-urls-to-yourwebapplication.md).

Voir aussi [Incorporation de la visionneuse de vidéos dans une page web.](embed-code.md)

>[!NOTE]
>
>* Pour utiliser l’URL, les ressources doivent être publiées. Si les ressources ne sont pas publiées, la copie et le collage de l’URL ne fonctionnent pas dans un navigateur web.
>* Les paramètres d’image prédéfinis et les paramètres de visionneuse prédéfinis doivent être activés et publiés pour une diffusion en direct.
>



Pour plus d’informations sur la publication d’une visionneuse ou d’une ressource, reportez-vous à la section [Publication de ressources.](/help/assets/manage-digital-assets.md)

## Diffusion de ressources Dynamic Media via HTTP/2 {#http-delivery-of-dynamic-media-assets}

AEM prend à présent en charge la diffusion de tout le contenu Dynamic Media (images et vidéo) sur HTTP/2. En d’autres termes, une URL publiée ou un code intégré pour l’image ou la vidéo peut être intégré dans toute application acceptant une ressource hébergée. Cette ressource publiée est alors distribuée par le biais du protocole HTTP/2. Cette méthode de distribution améliore la communication entre les navigateurs et les serveurs, ce qui permet d’améliorer les temps de réponse et de chargement de toutes vos ressources Dynamic Media.

See [HTTP/2 delivery of content frequently asked questions](/help/assets/dynamic-media/http2faq.md) to learn more.
<!--this md file used to reside under sites-administering-->
