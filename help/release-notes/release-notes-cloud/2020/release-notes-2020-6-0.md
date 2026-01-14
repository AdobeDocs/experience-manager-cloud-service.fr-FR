---
title: Notes de mise à jour d’Adobe Experience Manager as a Cloud Service version 2020.6.0
description: '[!DNL Adobe Experience Manager] les notes de mise à jour de la version 2020.6.0 d’as a Cloud Service.'
exl-id: fd6ebe2b-6d98-498c-a45d-b9a9c34e6be7
feature: Release Information
role: Admin
source-git-commit: 281a8efcd18920dd926d92db9c757c0513d599fd
workflow-type: tm+mt
source-wordcount: '1938'
ht-degree: 94%

---

# Notes de mise à jour d’AEM as a Cloud Service 2020.6.0 {#release-notes}

Cette page décrit les notes de mise à jour générales d’Experience Manager as a Cloud Service 2020.6.0.

## Date de publication {#release-date}

La date de publication d’[!DNL Experience Manager] as a Cloud Service version 2020.6.0 est le 4 juin 2020.

## Nouveautés d’AEM Sites {#aem-sites}

Consultez cette section pour en savoir plus sur les nouveautés et les mises à jour d’AEM Sites dans AEM as a Cloud Service 2020.6.0.

### Nouveautés {#whats-new-2020.6.0}

La version 2.9.0 des [composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr) est maintenant disponible dans AEM Sites, notamment :

* Intégration entre la [couche de données du client Adobe](https://github.com/adobe/adobe-client-data-layer) et les composants principaux
* Attributs d’ID HTML configurables pour tous les composants
* Un nouveau composant de barre de progression
* De nombreux correctifs

### Correctifs {#sites-bug-fixes}

* Les composants du conteneur de mise en page ne sont pas visibles lorsqu’il est copié et collé de nouveau sur une page.

* Correction d’un problème lié au redimensionnement du composant de mise en page.

* Ajout de la possibilité de gérer le routage de pages exclusivement Angular et de pages AEM/Angular.

### Accessibilité {#accessibility}

* Les commentaires de rôle et d’état sont désormais possibles pour les éléments Masonry dans la boîte de dialogue **Créer une page** en naviguant à l’aide de la flèche vers le bas.

* Ajout d’un lien dans la navigation pour permettre aux utilisateurs d’accéder directement au contenu principal.

* Améliorations du lecteur d’écran.

## Nouveautés de Foundations dans AEM as a Cloud Service {#foundations}

les délais de création des projets AEM s’améliorent en supprimant toutes les références dans le fichier pom.xml du projet AEM vers le référentiel distant `https://downloads.experiencecloud.adobe.com/content/maven/public`.

Le fichier Jar de l’API SDK d’AEM as a Cloud Service, qui était auparavant hébergé à cet emplacement, se trouve désormais dans Maven Central, qui est le référentiel d’artefacts par défaut de Maven.

## Nouveautés de Cloud Manager {#cloud-manager}

Consultez cette section pour en savoir plus sur les nouveautés et les mises à jour de Cloud Manager dans AEM as a Cloud Service 2020.6.0.

### Nouveautés {#what-is-new-cloud-manager}

* Un utilisateur ou une utilisatrice possédant le rôle *Propriétaire de l’entreprise* dans Cloud Manager peut désormais supprimer un programme Sandbox depuis la page de destination (par le biais d’un bouton d’action rapide sur la carte Programme) ou depuis le programme.

  Pour plus d’informations, voir [Suppression d’un programme de sandbox](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html?lang=fr).

* Un utilisateur ou une utilisatrice du programme Sandbox possédant le rôle *Propriétaire d’entreprise* ou *Responsable de déploiement* dans Cloud Manager peut désormais supprimer ses jeux d’environnements de production et d’évaluation via l’interface utilisateur de Cloud Manager. L’option de suppression est désormais disponible à partir de la vignette Environnement dans la page **Vue d’ensemble du programme** et dans la page **Environnements**. La sélection de l’option de suppression dans l’environnement de production ou d’évaluation supprime également l’autre dans le jeu d’environnements.

  Pour plus d’informations, voir [Suppression d’un programme de sandbox](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html?lang=fr).

* Repères sur la page de destination pour informer l’utilisateur sur la navigation de base.

* Assistants graphiques sur la page **Aperçu du programme** afin d’informer l’utilisateur sur la navigation de base dans Cloud Manager pour la prise en main.

* Une page **APPRENDRE** est désormais disponible dans Cloud Manager, accessible par le biais de la navigation supérieure. Cette page comprend des ressources destinées à aider les utilisateurs à en savoir plus sur les workflows les plus fréquemment utilisés en fonction du rôle qui leur est attribué dans Cloud Manager.

* Les programmes de sandbox sont maintenant identifiés au moyen d’un badge **Sandbox**, affiché dans la vignette du programme sur la page de destination, en regard du nom du programme sur la page **Vue d’ensemble du programme**.

* Un utilisateur possédant le rôle SysAdmin dispose désormais d’un accès d’un simple clic à l’emplacement d’Admin Console d’où peuvent être gérés les rôles des utilisateurs ou les autorisations d’accès à Cloud Manager. Un bouton **Gérer l’accès** est désormais disponible dans la page de destination en regard du bouton **Ajouter le programme**.

  Consultez [Tâches SysAdmin](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/navigation.html?lang=fr#sysadmin-tasks) pour plus d’informations.

* Un utilisateur ou une utilisatrice possédant le rôle SysAdmin dispose désormais d’un accès en un clic à l’instance de création directement à partir de Cloud Manager.

  Pour plus d’informations, voir [Gestion de l’accès à l’instance de création](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/navigation.html?lang=fr#manage-access-aem).

* Le journal de génération inclut désormais la liste des artefacts détectés, y compris les modules de contenu ignorés.

* L’étape de création confirme désormais que tous les packages de contenu générés incluent toutes les propriétés obligatoires - nom, groupe et version.

* L’étape de génération confirme désormais qu’elle a produit au moins un module de contenu.

### Correctifs {#bug-fixes-cm}

* Dans certains cas, les icônes de la boîte de dialogue **Créer un Programme** n’étaient pas alignées.

* L’identifiant de version d’AEM n’était pas affiché de manière cohérente sur la page **Aperçu du programme**.

* Lors de la configuration du pipeline de production, l’option **Déploiement planifié** n’était pas visible pour certains clients.

### Problèmes connus {#known-issues-cm}

* Les environnements d’un programme de sandbox sont mis en veille lorsqu’aucune activité n’est détectée pendant une certaine durée. Cet état ne sera pas appliqué dans Cloud Manager. Il peut toutefois être appliqué par le biais de Developer Console. Ce problème sera traité dans une prochaine version.

* Le lien vers Developer Console directement à partir de Cloud Manager n’affiche pas l’option permettant de mettre en veille/réactiver un environnement de programme Sandbox. Pour résoudre ce problème, une fois dans Developer Console, ajoutez le motif `#release-cm-p1234-e5678` à la fin de l’URL, où *1234* correspond à l’identifiant de programme et *5678* à l’identifiant d’environnement. Ce problème sera traité dans une prochaine version.

## Nouveautés de la version [!DNL Adobe Experience Manager Assets] {#aem-assets}

**Expérience utilisateur guidée pour les balises intelligentes améliorées, optimisée par l’IA dédiée à Adobe**

Les balises intelligentes améliorées permettent aux entreprises d’entraîner des modèles de balisage intelligent pour reconnaître les images en fonction de balises commerciales spécifiques à la clientèle, en plus des balises intelligentes génériques.

Cette version apporte une nouvelle expérience client assistée qui permet de configurer l’entraînement des balises intelligentes pour des ensembles de balises spécifiques à la clientèle, mais aussi de les entraîner sur des ressources qui devront être reconnues et balisées plus tard. L’expérience est désormais plus intuitive.
Entraînez des balises intelligentes améliorées pour un entraînement plus intuitif. Voir la section [Comment ajouter des balises intelligentes aux ressources](/help/assets/smart-tags.md).

**Prise en charge de l’ingestion, de la prévisualisation et de la diffusion des contenus 3D**

Les entreprises peuvent désormais stocker et utiliser des fichiers 3D dans AEM Assets. L’utilisateur peut charger, prévisualiser et utiliser différents fichiers 3D de base, notamment des fichiers OBJ, STL, GLTF et GLB. Avec l’ajout de [!DNL Dynamic Media], vous pouvez configurer et diffuser des expériences 3D à l’aide d’URL ou de visionneuses agnostiques. Il s’agit notamment de la visionneuse [!DNL Dynamic Media] 3D Experience, du composant Sites 3D Viewer et de la possibilité de diffuser des fichiers 3D à l’aide de [!DNL Dynamic Media] (réalité augmentée/réalité virtuelle). Voir [Utilisation de ressources 3D dans Dynamic Media](/help/assets/dynamic-media/assets-3d.md).

**Prise en charge d’Adobe Asset Link pour Adobe XD**

Avec la dernière version, [!DNL Experience Manager Assets] prend en charge un nouveau plug-in [!DNL Adobe Asset Link] publié avec [!DNL Adobe XD] v29.3. L’intégration permet aux concepteurs d’accéder aux ressources d’[!DNL Experience Manager] et de les utiliser dans leurs projets, sans avoir à quitter l’application [!DNL Adobe XD]. Voir [Adobe Asset Link pour Adobe XD](https://helpx.adobe.com/fr/enterprise/using/adobe-asset-link-for-xd.html).

Grâce à cette version, les utilisateurs créatifs et les concepteurs peuvent désormais utiliser des ressources gérées dans [!DNL AEM Assets] en utilisant [!DNL Adobe Asset Link] avec toute une gamme d’applications de bureau Creative Cloud, notamment [!DNL Adobe XD], [!DNL Photoshop], [!DNL Illustrator] et [!DNL InDesign].

**Amélioration de l’accessibilité**

[!DNL Adobe Experience Manager Assets] est désormais plus accessible, conformément aux directives WCAG (Web Content Accessibility Guidelines) v2.1. L’accessibilité a été améliorée pour les cas d’utilisation ou les interfaces suivants :

Les éléments de l’interface utilisateur sont compatibles avec les lecteurs d’écran, sont accessibles à l’aide d’un clavier et offrent un meilleur contraste. Voici une liste détaillée des améliorations :

* Les barres de progression [!UICONTROL Options], [!UICONTROL Portée] et [!UICONTROL Workflows] de la page [!UICONTROL Gérer la publication] ne sont pas lues par le lecteur d’écran comme des barres de progression. Les utilisateurs de lecteurs d’écran perçoivent plutôt ces indicateurs d’état comme une liste d’onglets. (CQ-4273015)

* Lors de l’ajout de balises sur la page [!UICONTROL Propriétés] d’une ressource, les utilisateurs naviguent dans une arborescence de balises. La structure de l’arborescence n’est pas accessible, car les utilisateurs de lecteurs d’écran n’entendent rien lorsqu’ils la parcourent. (CQ-4272964)

* Dans la boîte de dialogue de partage de liens, lorsque vous naviguez en mode de navigation, le lecteur d’écran :

   * Lit les informations du tableau immédiatement au chargement de la boîte de dialogue.
   * Ne peut pas accéder à toutes les suggestions automatiques répertoriées.
   * Ne décrit pas les suggestions automatiques affichées pour la zone combinée [!UICONTROL Rechercher/ajouter l’adresse électronique]. (CQ-4294232)

* La page [!UICONTROL Éditeur de schéma de métadonnées] et ses éléments sont désormais accessibles via un clavier et sont compatibles avec les lecteurs d’écran. (CQ-4272953) Les utilisateurs peuvent faire glisser les composants à l’aide du clavier dans le mode de navigation NVDA. (CQ-4296326)

* Dans l’interface utilisateur Assets, les paramètres d’affichage ne sont pas accessibles au clavier. (CQ-4289038)

* Le rapport de luminosité est inférieur à 3 :1 pour les icônes d’évaluation de couleur jaune. La fonction n’est pas utile pour les utilisateurs dont la vision est limitée ou ne percevant pas les couleurs. Les étoiles d’évaluation s’affichent dans l’onglet en mode Carte ou Ressource.

* La couleur et le contraste de certains éléments de l’interface utilisateur ont été mis à jour afin que les utilisateurs disposant d’une vision limitée ou qui ne perçoivent pas les couleurs puissent distinguer ces éléments de l’interface utilisateur. Par exemple, la couleur des icônes d’évaluation par étoiles dans la section [!UICONTROL Notation] de l’onglet [!UICONTROL Avancé] des [!UICONTROL Propriétés] dans les modes Ressource et Carte a été redéfinie sur un contraste approprié. (CQ-4295106)

* Les lecteurs d’écran peuvent désormais lire les entrées du menu pop-up de zone de liste de la zone combinée (dans divers champs de différentes pages) en tant que liste d’options. (CQ-4294017)

* Pour appliquer un workflow à une ressource, vous pouvez accéder à la flèche chevron de la [!UICONTROL chronologie] via le clavier. (CQ-4289268)

* Les utilisateurs peuvent supprimer les balises sélectionnées dans le champ [!UICONTROL Balises] de l’onglet [!UICONTROL De base] de la page [!UICONTROL Propriétés] d’une ressource à l’aide du symbole `x`. Les lecteurs d’écran annoncent maintenant l’objectif des balises sélectionnées et leur nombre (CQ-4273033).

* Les champs de formulaire en lecture seule peuvent être affichés avec le clavier. Par exemple, les champs désactivés de l’onglet [!UICONTROL De base] de la page [!UICONTROL Propriétés] d’une ressource. (CQ-4273031)

* Accédez maintenant aux options de filtrage des ressources dans la barre latérale gauche à l’aide du clavier. (CQ-4273018)

* Le lecteur d’écran annonce l’objectif de divers éléments de zone combinée, tels que le champ Chemin et l’option d’ouverture de la boîte de dialogue Sélection dans l’onglet [!UICONTROL De base] de la page [!UICONTROL Propriétés] d’une ressource. (CQ-4273016)

* Les contrôles de volume des vidéos sont accessibles via le clavier. (CQ-4272696)

* De nombreuses options exploitables dans l’interface utilisateur Assets n’indiquent pas le focus en cas d’utilisation du clavier. (CQ-4272694)

* Les utilisateurs de lecteurs d’écran peuvent désormais savoir quand les lignes dans la vue Liste peuvent être sélectionnées à l’aide du clavier. Les informations sont annoncées lorsque la souris survole les lignes. (CQ-4271824)

* Certains champs de formulaires, tels que les champs Nom d’utilisateur et Mot de passe de la page de connexion, reposent uniquement sur des valeurs d’espace réservé pour donner un libellé accessible. (CQ-4271716)

* Les éléments interactifs de l’interface utilisateur, tels que les liens et les options (par exemple, dans les options d’en-tête et de zoom de la page de ressources, navigation dans les dossiers), sont désormais accessibles à l’aide du clavier. (CQ-4271412)

* Les titres de toutes les pages consultées dans [!DNL Adobe Experience Manager] Assets sont désormais uniques. (CQ-4271409)

**Autres améliorations**

Cette version comprend les autres améliorations suivantes :

* Possibilité de retraiter des ressources avec des profils de traitement des ressources. Les utilisateurs peuvent ainsi contrôler entièrement le processus (effectuer le traitement complet des ressources, appliquer simplement un profil de traitement spécifique et décider si le workflow de post-traitement doit être exécuté).
* Les requêtes de recherche renvoient maintenant les résultats plus rapidement, car l’instance de grappe associée a été redémarrée en arrière-plan (auparavant, l’exécution de la recherche initiale pouvait durer plus longtemps).
* Tri par nom lorsque vous affichez des ressources dans la vue Liste de l’interface Assets et dans les résultats de recherche. Voir [Rechercher des ressources](/help/assets/search-assets.md#sort).
* Effectuez un tri sur « Créé » (date) lors de l’affichage de ressources dans la vue Liste de l’interface d’Assets et dans les résultats de recherche. Voir [Rechercher des ressources](/help/assets/search-assets.md#sort).
* Prise en charge de la conversion de fichiers EPS en images à l’aide des microservices de ressources.

### Correctifs {#assets-bug-fixes}

En plus des nouvelles fonctionnalités ci-dessus, la version actuelle apporte les correctifs suivants suite aux commentaires des clients sur [!DNL Assets].

* Pour les fichiers de musique MP3, le bouton de lecture affiché sur la miniature dans l’aperçu DAM ne fonctionne pas. (CQ-4294731)
* Le passage du pointeur en mode Carte permet de faire défiler l’écran suite à l’activation du focus (automatique) sur les actions rapides disponibles dans la carte. (GRANITE-26895)
* L’affichage d’un trop grand nombre d’images après le défilement d’un nombre important de résultats de recherche provoque un blocage du navigateur. (GRANITE-26432)
* Lors du téléchargement d’une ressource, si l’option de courrier électronique est sélectionnée et même si une adresse électronique valide est fournie, l’option de téléchargement n’est pas disponible. (CQ-4296535)
* Les filtres personnalisés enregistrés à titre de collections dynamiques ne sont pas correctement appliqués aux ressources. (CQ-4294942)
* Différentes améliorations concernant la recherche et l’indexation, et des corrections de bogues, ont été réalisées pour obtenir des gains de performances. (CQ-4286373)
* L’onglet des propriétés de dossier est inaccessible dans Assets et renvoie une erreur 500. (CQ-4295701)
