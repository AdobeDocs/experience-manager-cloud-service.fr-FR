---
title: Bonnes pratiques relatives à l’organisation de vos ressources numériques pour utiliser des profils d’image ou vidéo Dynamic Media
description: '"Conseils et bonnes pratiques pour nommer, organiser et gérer les fichiers image et vidéo Dynamic Media."'
contentOwner: Rick Brough
feature: Gestion des ressources, Profils d’image, Profils vidéo
role: Administrator,Business Practitioner
exl-id: 82ab5432-088c-4442-a9db-9f4e0184febf
source-git-commit: 1fe6ce1259972c1805d934327aa2f24cdcdc0bc8
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 73%

---

# Bonnes pratiques relatives à l’organisation de vos ressources numériques pour utiliser des profils d’image ou vidéo {#best-practices-for-organizing-your-digital-assets-for-using-profiles}

Un concept important concernant l’utilisation des profils d’image ou vidéo Dynamic Media est que ces profils sont affectés à des dossiers. Un profil contient des paramètres d’une image ou d’une vidéo. Ces paramètres traitent le contenu d’un dossier et de tous ses sous-dossiers. Par conséquent, la manière dont vous nommez les fichiers et les dossiers, disposez les sous-dossiers et manipulez les fichiers dans ces dossiers a une incidence sur la façon dont ces ressources sont traitées par le profil.

En appliquant des stratégies d’attribution de noms de fichiers et de dossiers cohérentes et appropriées, ainsi que de bonnes pratiques de métadonnées, vous tirez pleinement parti de votre collecte de ressources numériques et assurez-vous que les fichiers appropriés sont traités par le profil approprié.

Voir [À propos des profils d’image et vidéo Dynamic Media](about-image-video-profiles.md).

Voici quelques conseils sur les bonnes pratiques relatives à l’organisation des fichiers de ressources numériques.

* Organisez vos fichiers en fonction des métadonnées que vous leur ajoutez et non en fonction des dossiers où ils sont placés. Vous pouvez les organiser en ajoutant des profils de métadonnées.

   * Reportez-vous à la section [Profils de métadonnées](/help/assets/metadata-profiles.md).
   * Reportez-vous à la section [Métadonnées pour la gestion des ressources numériques](/help/assets/manage-metadata.md).

* En général, votre collection de ressources numériques est en constante augmentation. Il est donc important d’avoir formalisé auparavant l’utilisation des métadonnées, la structure des dossiers et l’attribution de nom aux fichiers pour toutes vos ressources téléchargées. Grâce à cette normalisation, vous aurez l’assurance, au fur et à mesure que le nombre de vos ressources augmente, de pouvoir appliquer des profils de traitement aux dossiers avec une précision et une cohérence toujours plus grandes.
* Utilisez les dossiers uniquement pour imposer une structure de stockage cohérente pour vos ressources numériques. Par exemple, voici des exemples de structures de dossier qui peuvent vous aider à définir les profils à attribuer :

   * **Dossiers**  de développement : contiennent les ressources numériques que vous utilisez actuellement.
   * **** Dossiers de clients : contiennent des ressources numériques en fonction des clients ou des noms de projet.
   * **Dossiers**  sources Principal : contiennent les ressources numériques sources originales.
   * **** Dossiers de rendus : contiennent les rendus et les copies des ressources numériques sources originales.
   * **** Dossiers de taille de fichier : contiennent des ressources numériques en fonction des tailles de fichier petite, moyenne et volumineuse.
   * **Dossiers d’évaluation**  : contiennent les ressources numériques prêtes à être publiées sur votre site web.
   * **Dossiers de type MIME**  : contiennent des ressources numériques spécifiques à des types MIME tels que des images, des documents et des fichiers multimédia.
   * **Dossiers d’archives**  : contiennent les ressources numériques retirées.
   * **Dossiers**  basés sur la date : contiennent des ressources numériques en fonction d’une date de création ou d’une date de dernière modification.

* Créez un répertoire de dossiers qui n’est pas susceptible de changer afin que les profils attribués restent fonctionnels.
* Supposons qu’une ressource ait déjà été publiée puis vous souhaitiez utiliser Adobe Experience Manager pour déplacer cette ressource vers un autre dossier et la republier depuis son nouvel emplacement. L’emplacement d’origine de la ressource publiée est toujours disponible, ainsi que la ressource récemment republiée. Toutefois, la ressource publiée d’origine est « perdue » pour Experience Manager et sa publication ne peut pas être annulée. Il est donc recommandé d’annuler la publication des ressources avant de les déplacer vers un autre dossier.
