---
title: Publication de ressources Dynamic Media
description: Découvrez comment publier des ressources Dynamic Media.
contentOwner: Rick Brough
feature: Gestion des ressources
topic: Professionnel
role: Business Practitioner
exl-id: 8ee759dc-cb8f-4e80-8175-2c3ba06da862
translation-type: tm+mt
source-git-commit: 6b232ab512a6faaf075faa55c238dfb10c00b100
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 59%

---

# Publication de ressources Dynamic Media {#publishing-dynamic-media-assets}

Vous publiez vos ressources Dynamic Media en sélectionnant celles que vous avez déjà chargées et en appuyant sur **[!UICONTROL Publier]** ou **[!UICONTROL Publication rapide]**. Une fois vos ressources Dynamic Media publiées, vous pouvez les inclure dans une page web au moyen d’une URL ou d’une incorporation de code sur la page.

Vous pouvez également publier immédiatement les ressources que vous chargez, sans intervention de l’utilisateur. Vous pouvez également publier ces ressources de manière sélective. Voir [Configuration de Dynamic Media](config-dm.md). Vous pouvez également publier des fichiers de manière sélective sur Dynamic Media ou Adobe Experience Manager, mutuellement exclusifs les uns des autres, en utilisant **[!UICONTROL Publication sélective]** au niveau du dossier. Voir [Utilisation de la publication sélective dans Dynamic Media](/help/assets/dynamic-media/selective-publishing.md).

En **[!UICONTROL mode Carte]**, une petite icône en forme de globe apparaît directement sous le nom d’une ressource et à gauche de la date et de l’heure pour indiquer qu’elle est publiée. En **[!UICONTROL mode Liste]**, une colonne **[!UICONTROL Publié]** indique les ressources qui sont publiées et celles qui ne le sont pas.

>[!NOTE]
>
>Si un fichier est déjà publié, vous déplacez le fichier dans un autre dossier, puis vous republiez le fichier à partir de son nouvel emplacement, l’emplacement du fichier publié d’origine est toujours disponible, ainsi que l’élément récemment republié. Toutefois, l’actif publié d’origine est &quot;perdu&quot; pour le Experience Manager et ne peut pas être annulé. Par conséquent, il est recommandé d’annuler la publication des fichiers avant de les déplacer vers un autre dossier.

Si vous avez l’intention de publier des fichiers vidéo immédiatement après leur codage, assurez-vous que le codage est terminé. Lorsque des vidéos sont codées, le système vous informe qu’un processus de traitement vidéo est en cours. Lorsque le codage vidéo est terminé, vous pouvez prévisualisation les rendus vidéo. À ce stade, vous pouvez publier en toute sécurité les vidéos, sans entraîner aucune erreur de publication.

Voir aussi [Liaison d’URL à une application web](linking-urls-to-yourwebapplication.md).

Voir aussi [Intégration de la visionneuse de vidéos ou d’images Dynamic Media dans une page web](embed-code.md).

>[!NOTE]
>
>* Les ressources doivent être publiées pour utiliser l’URL. Si les ressources ne sont pas publiées, la copie et le collage de l’URL dans un navigateur Web ne fonctionnent pas.
>* Les paramètres d’image prédéfinis et les paramètres de visionneuse prédéfinis doivent être activés et publiés pour une diffusion en direct.

>



Pour plus d’informations sur la publication d’une visionneuse ou d’une ressource, reportez-vous à la section [Publication de ressources](/help/assets/manage-digital-assets.md).

## Diffusion de ressources Dynamic Media via HTTP/2  {#http-delivery-of-dynamic-media-assets}

Experience Manager prend désormais en charge la diffusion de tous les contenus Dynamic Media (images et vidéo) sur HTTP/2. En d’autres termes, une URL publiée ou un code intégré pour l’image ou la vidéo peut être intégré dans toute application acceptant une ressource hébergée. Cette ressource publiée est alors distribuée par le biais du protocole HTTP/2. Cette méthode de distribution améliore la communication entre les navigateurs et les serveurs, ce qui permet d’améliorer les temps de réponse et de chargement de toutes vos ressources Dynamic Media.

Voir [HTTP/2 diffusion du contenu aux questions fréquentes](/help/assets/dynamic-media/http2faq.md).

<!--this md file used to reside under sites-administering-->
