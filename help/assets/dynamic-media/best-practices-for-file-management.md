---
title: Bonnes pratiques relatives à l’organisation de vos ressources numériques pour utiliser des profils d’image ou vidéo Dynamic Media
description: Conseils et bonnes pratiques pour nommer, organiser et gérer les fichiers d’image et vidéo Dynamic Media.
translation-type: ht
source-git-commit: 68cf71054b1cd7dfb2790122ba4c29854ffdf703
workflow-type: ht
source-wordcount: '497'
ht-degree: 100%

---


# Bonnes pratiques relatives à l’organisation de vos ressources numériques pour utiliser des profils d’image ou vidéo{#best-practices-for-organizing-your-digital-assets-for-using-profiles}

Un concept important concernant l’utilisation des profils d’image ou vidéo Dynamic Media est que ces profils sont affectés à des dossiers. Un profil contient des paramètres d’une image ou d’une vidéo. Ces paramètres traitent le contenu d’un dossier et de tous ses sous-dossiers. Aussi, la façon dont vous nommez les fichiers ou les dossiers, organisez les sous-dossiers ou gérez les fichiers au sein des dossiers a un impact significatif sur le traitement des ressources par le profil.

Grâce à des stratégies d’attribution de nom aux fichiers et dossiers cohérentes et adéquates et à une bonne pratique en matière de métadonnées, vous pouvez tirer pleinement parti de votre collection de ressources numériques et vous assurer que les bons fichiers sont traités par le profil adéquat.

Voir [À propos des profils d’image et vidéo Dynamic Media](about-image-video-profiles.md).

Voici quelques conseils sur les bonnes pratiques relatives à l’organisation des fichiers de ressources numériques.

* Organisez vos fichiers en fonction des métadonnées que vous leur ajoutez et non en fonction des dossiers où ils sont placés. Vous pouvez le faire en ajoutant des profils de métadonnées.

   * Reportez-vous à la section [Profils de métadonnées.](/help/assets/metadata-profiles.md)
   * Reportez-vous à la section [Métadonnées pour la gestion des ressources numériques](/help/assets/manage-metadata.md).

* Généralement, une collection de ressources numériques augmente et c’est probablement ce qui se produira aussi pour vous. Il est donc important d’avoir formalisé auparavant l’utilisation des métadonnées, la structure des dossiers et l’attribution de nom aux fichiers pour toutes vos ressources téléchargées. Grâce à cette normalisation, vous aurez l’assurance, au fur et à mesure que le nombre de vos ressources augmente, de pouvoir appliquer des profils de traitement aux dossiers avec une précision et une cohérence toujours plus grandes.
* Utilisez les dossiers uniquement pour imposer une structure de stockage cohérente pour vos ressources numériques. Par exemple, voici des exemples de structures de dossier susceptibles de vous aider à définir les profils à attribuer :

   * **Dossiers de développement** : contiennent les ressources numériques que vous utilisez actuellement.
   * **Dossiers de clients** : contiennent des ressources numériques en fonction des clients ou des noms de projet.
   * **Dossiers des sources originales** : contiennent les ressources numériques sources originales.
   * **Dossiers de rendus** : contiennent les rendus et les copies des ressources numériques sources originales.
   * **Dossiers de taille de fichier** : contiennent des ressources numériques en fonction des tailles de fichier petite, moyenne et volumineuse.
   * **Dossiers intermédiaires** : contiennent les ressources numériques qui sont prêtes à être publiées sur votre site web.
   * **Dossiers de type MIME** : contiennent des ressources numériques qui sont spécifiques à des types MIME tels que des images, des documents et des fichiers multimédia.
   * **Dossiers d’archives** : contiennent les ressources numériques retirées.
   * **Dossiers reposant sur une date** : contiennent des ressources numériques en fonction d’une date de création ou d’une date de dernière modification.

* Créez un répertoire de dossiers qui n’est pas susceptible de changer afin que les profils attribués restent fonctionnels.
* Si une ressource est déjà publiée et que vous utilisez AEM pour la déplacer vers un autre dossier et la republier à partir du nouvel emplacement, l’emplacement d’origine de la ressource publiée est toujours disponible, avec la ressource republiée. La ressource d’origine publiée est toutefois « perdue » pour AEM et sa publication ne peut pas être annulée. Il est par conséquent recommandé d’annuler la publication des ressources avant de les déplacer vers un autre dossier. 

