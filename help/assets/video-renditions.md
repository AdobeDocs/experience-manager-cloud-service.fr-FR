---
title: Rendus vidéo
description: Rendus vidéo
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Rendus vidéo {#video-renditions}

Le composant Adobe Experience Manager (AEM) Assets génère des rendus vidéo pour les ressources vidéo de différents formats dont OGG, FLV, etc.

Le composant AEM Assets prend en charge les rendus statiques et dynamiques (rendus avec codage DM) pour les ressources multimédias.

Les rendus statiques sont générés en mode natif à l’aide de FFMPEG (installé et disponible sur le chemin système) et stockés dans le référentiel de contenu.

Les rendus codés DM sont stockés dans le serveur proxy et diffusés au moment de l’exécution.

Les ressources AEM fournissent une prise en charge de lecture pour ces rendus du côté client.

Pour afficher les rendus d’une ressource vidéo particulière, ouvrez sa page de ressources, puis appuyez sur l’icône Navigation globale. Then, choose **[!UICONTROL Renditions]** from the list.

La liste des rendus vidéo s’affiche dans le panneau **[!UICONTROL Rendus.]**

Pour configurer le serveur proxy des rendus codés en MD, configurez les services cloud Dynamic Media.

<!-- To generate video renditions with desired parameters, [create a corresponding video profile](video-profiles.md). -->

Une fois que vous avez configuré le serveur proxy et créé les profils vidéo, vous pouvez inclure ce paramètre vidéo prédéfini dans un profil de traitement et appliquer le profil de traitement à un dossier.

>[!NOTE]
>
>La lecture audio ne fonctionne pas pour les fichiers OGG et WAV sur Internet Explorer 11. Une erreur « Source non valide » apparaît sur la page des détails des ressources présentant l’extension OGG ou WAV. Sous MS Edge et iPad, les fichiers OGG ne s’exécutent pas et génèrent une erreur de format non pris en charge.