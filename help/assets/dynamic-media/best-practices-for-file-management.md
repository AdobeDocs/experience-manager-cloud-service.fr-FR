---
title: Meilleures pratiques d’organisation des ressources numériques pour l’utilisation de profils
description: Conseils et meilleures pratiques pour nommer, organiser et gérer les métadonnées des fichiers de ressources numériques.
translation-type: tm+mt
source-git-commit: 6224d193adfb87bd9b080f48937e0af1f03386d6

---


# Meilleures pratiques pour organiser les ressources numériques afin d’utiliser les profils {#best-practices-for-organizing-your-digital-assets-for-using-profiles}

Un élément à connaître lorsque l’on utilise les profils dans AEM est qu’ils sont attribués aux dossiers. Un profil contient des paramètres sous la forme de profils de métadonnées, avec des profils vidéo ou des profils d’image. Ces paramètres traitent le contenu d’un dossier et de tous ses sous-dossiers. Aussi, la façon dont vous nommez les fichiers ou les dossiers, organisez les sous-dossiers ou gérez les fichiers au sein des dossiers a un impact significatif sur le traitement des ressources par les profils.

Grâce à des stratégies d’attribution de nom aux fichiers et dossiers cohérentes et adéquates et à une bonne pratique en matière de métadonnées, vous pouvez tirer pleinement parti de votre collection de ressources numériques et vous assurer que les bons fichiers sont traités par le profil adéquat.

Reportez-vous à la section [Profils pour le traitement des vidéos, des métadonnées et des images](processing-profiles.md).

Vous trouverez ci-dessous des conseils sur les meilleures pratiques pour organiser vos fichiers de ressources numériques.

* Organisez vos fichiers en fonction des métadonnées que vous leur ajoutez et non en fonction des dossiers où ils sont placés. Vous pouvez le faire en ajoutant des profils de métadonnées.

   * Reportez-vous à la section [Profils de métadonnées.](/help/assets/metadata-profiles.md)
   * Reportez-vous à la section [Métadonnées pour la gestion des ressources numériques](/help/assets/manage-metadata.md).

* Généralement, une collection de ressources numériques augmente et c’est probablement ce qui se produira aussi pour vous. Il est donc important, plus tôt, de formaliser l’utilisation des métadonnées, la structure des dossiers et le nommage des fichiers parmi tous les fichiers téléchargés. Grâce à cette normalisation, vous aurez l’assurance, au fur et à mesure que le nombre de vos ressources augmente, de pouvoir appliquer des profils de traitement aux dossiers avec une précision et une cohérence toujours plus grandes.
* Utilisez les dossiers uniquement pour imposer une structure de stockage cohérente pour vos ressources numériques. Par exemple, les structures de dossiers qui peuvent vous aider à affiner les profils à affecter peuvent inclure les éléments suivants :

   * **Dossiers** de développement : contient les ressources numériques sur lesquelles vous travaillez actuellement.
   * **Dossiers** clients : contient des ressources numériques basées sur les clients ou les noms de projet.
   * **Dossiers** principaux : contient les fichiers numériques source d’origine.
   * **Dossiers** de rendus : contient les rendus et les copies des fichiers numériques source d’origine.
   * **Dossiers** Taille de fichier : contient des fichiers numériques en fonction de la taille de fichier (petite, moyenne ou grande).
   * **Dossiers** d’évaluation : contient des ressources numériques prêtes à être publiées en direct sur votre site Web.
   * **Dossiers** de type MIME : contient des ressources numériques spécifiques aux types MIME tels que les images, les documents et les fichiers multimédia.
   * **Dossiers** d’archives : contient des ressources numériques à la retraite.
   * **Dossiers** basés sur des dates : contient des ressources numériques basées sur une date de création ou une date de dernière modification.

* Créez un répertoire de dossiers qui n’est pas susceptible de changer afin que les profils attribués restent fonctionnels.
* Si un fichier est déjà publié, vous utilisez AEM pour déplacer le fichier vers un autre dossier et le republier depuis son nouvel emplacement, l’emplacement du fichier publié d’origine est toujours disponible, ainsi que le fichier récemment republié. La ressource publiée d’origine est toutefois &quot;perdue&quot; pour AEM et ne peut pas être annulée. Par conséquent, il est recommandé d’annuler la publication des fichiers avant de les déplacer vers un autre dossier.

