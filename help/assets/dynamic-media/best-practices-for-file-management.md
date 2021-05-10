---
title: Bonnes pratiques relatives à l’organisation de vos ressources numériques pour utiliser des profils d’image ou vidéo Dynamic Media
description: '"Conseils et bonnes pratiques en matière de nommage, d’organisation et de gestion des fichiers d’images et de fichiers vidéo Dynamic Media."'
contentOwner: Rick Brough
feature: Gestion des ressources,Profils d’images,Profils vidéo
role: Administrator,Business Practitioner
exl-id: 82ab5432-088c-4442-a9db-9f4e0184febf
translation-type: tm+mt
source-git-commit: 1fe6ce1259972c1805d934327aa2f24cdcdc0bc8
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 44%

---

# Bonnes pratiques relatives à l’organisation de vos ressources numériques pour utiliser des profils d’image ou vidéo{#best-practices-for-organizing-your-digital-assets-for-using-profiles}

Un concept important concernant l’utilisation des profils d’image ou vidéo Dynamic Media est que ces profils sont affectés à des dossiers. Un profil contient des paramètres d’une image ou d’une vidéo. Ces paramètres traitent le contenu d’un dossier avec l’un de ses sous-dossiers. Par conséquent, la manière dont vous nommez les fichiers et les dossiers, disposez les sous-dossiers et manipulez les fichiers dans ces dossiers a une incidence sur la façon dont ces fichiers sont traités par le profil.

En appliquant des stratégies cohérentes et appropriées de nommage de fichiers et de dossiers, ainsi que de bonnes pratiques de métadonnées, vous tirez le meilleur parti de votre collection de ressources numériques et vous assurez que les fichiers appropriés sont traités par le bon profil.

Voir [À propos des profils d’image et vidéo Dynamic Media](about-image-video-profiles.md).

Voici quelques conseils sur les bonnes pratiques relatives à l’organisation des fichiers de ressources numériques.

* Organisez vos fichiers en fonction des métadonnées que vous leur ajoutez et non en fonction des dossiers où ils sont placés. Pour ce faire, vous pouvez ajouter des profils de métadonnées.

   * Reportez-vous à la section [Profils de métadonnées](/help/assets/metadata-profiles.md).
   * Reportez-vous à la section [Métadonnées pour la gestion des ressources numériques](/help/assets/manage-metadata.md).

* En général, votre collection de ressources numériques est en constante augmentation. Il est donc important d’avoir formalisé auparavant l’utilisation des métadonnées, la structure des dossiers et l’attribution de nom aux fichiers pour toutes vos ressources téléchargées. Grâce à cette normalisation, vous aurez l’assurance, au fur et à mesure que le nombre de vos ressources augmente, de pouvoir appliquer des profils de traitement aux dossiers avec une précision et une cohérence toujours plus grandes.
* Utilisez les dossiers uniquement pour imposer une structure de stockage cohérente pour vos ressources numériques. Par exemple, les structures de dossiers qui peuvent vous aider à affiner les profils à affecter peuvent inclure les éléments suivants :

   * **Dossiers**  de développement : contient des ressources numériques sur lesquelles vous travaillez actuellement.
   * **** Dossiers de clients : contiennent des ressources numériques en fonction des clients ou des noms de projet.
   * **Dossiers**  source Principal - contient des ressources numériques source d’origine.
   * **** Dossiers de rendus : contiennent les rendus et les copies des ressources numériques sources originales.
   * **** Dossiers de taille de fichier : contiennent des ressources numériques en fonction des tailles de fichier petite, moyenne et volumineuse.
   * **Dossiers**  d’évaluation : contient des ressources numériques prêtes à être publiées en direct sur votre site Web.
   * **Dossiers**  de type Mime : contient des ressources numériques spécifiques aux types MIME tels que les images, les documents et les supports multimédia.
   * **Dossiers**  d’archives - contient des ressources numériques retirées.
   * **Dossiers**  basés sur les dates : contient des ressources numériques basées sur une date de création ou une date de dernière modification.

* Créez un répertoire de dossiers qui n’est pas susceptible de changer afin que les profils attribués restent fonctionnels.
* Supposons qu’un fichier soit déjà publié, puis vous utilisez Adobe Experience Manager pour déplacer le fichier vers un autre dossier et le republier depuis son nouvel emplacement. L’emplacement d’origine de la ressource publiée est toujours disponible, ainsi que la ressource récemment republiée. Toutefois, l’actif publié d’origine est &quot;perdu&quot; pour le Experience Manager et ne peut pas être annulé. Par conséquent, il est recommandé d’annuler la publication des fichiers avant de les déplacer vers un autre dossier.
