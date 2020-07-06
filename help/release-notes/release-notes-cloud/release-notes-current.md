---
title: Notes de mise à jour d’Adobe Experience Manager as a Cloud Service version 2020.6.0
description: Notes de mise à jour d’Experience Manager version 2020.6.0
translation-type: tm+mt
source-git-commit: fcae90c8e24dbd2994e8700daf22f5dff039b299
workflow-type: tm+mt
source-wordcount: '1942'
ht-degree: 70%

---


# Notes de mise à jour d’AEM as a Cloud Service 2020.6.0 {#release-notes}

La section suivante décrit les notes de mise à jour générales d’Experience Manager as a Cloud Service 2020.6.0.

## Date de publication {#release-date}

La date de publication d’[!DNL Experience Manager] as a Cloud Service version 2020.6.0 est le 4 juin 2020.

## Nouveautés d’AEM Sites {#aem-sites}

Consultez cette section pour en savoir plus sur les nouveautés et les mises à jour d’AEM Sites dans AEM as a Cloud Service 2020.6.0.

### Nouveautés {#whats-new-2020.6.0}

La version 2.9.0 des [composants principaux](https://docs.adobe.com/content/help/fr-FR/experience-manager-core-components/using/introduction.html) est maintenant disponible dans AEM Sites, notamment :

* Intégration entre la [couche de données du client Adobe](https://github.com/adobe/adobe-client-data-layer) et les composants principaux
* Attributs d’ID HTML configurables pour tous les composants
* Un nouveau composant de barre de progression
* De nombreux correctifs

### Correctifs {#sites-bug-fixes}

* Les composants du conteneur de mises en page ne sont pas visibles lorsqu’il est copié et collé de nouveau sur une page.

* Correction d’un problème lié au redimensionnement du composant de mise en page.

* Ajout de la possibilité de gérer le routage de pages exclusivement Angular et de pages AEM/Angular.

### Accessibilité {#accessibility}

* Les commentaires de rôle et d’état sont désormais possibles pour les éléments Masonry dans la boîte de dialogue **Créer une page** en naviguant à l’aide de la flèche vers le bas.

* Ajout d’un lien dans la navigation pour permettre aux utilisateurs d’accéder directement au contenu principal.

* Améliorations du lecteur d’écran.

## Nouveautés de Foundations dans AEM as a Cloud Service {#foundations}

Amélioration des délais d’élaboration d’un projet AEM en supprimant toutes les références au fichier pom.xml du projet AEM dans le référentiel distant `https://downloads.experiencecloud.adobe.com/content/maven/public`.

Le fichier Jar d’API du SDK AEM as a Cloud Service, qui était auparavant hébergé à cet emplacement, se trouve désormais dans Maven Central, qui est le référentiel d’artefacts par défaut de Maven.

## Nouveautés de Cloud Manager {#cloud-manager}

Consultez cette section pour en savoir plus sur les nouveautés et les mises à jour de Cloud Manager dans AEM as a Cloud Service 2020.6.0.

### Nouveautés {#what-is-new-cloud-manager}

* Un utilisateur possédant le rôle *Propriétaire de l’entreprise* dans Cloud Manager peut désormais supprimer un programme Sandbox depuis la landing page (par le biais d’un bouton d’action rapide sur la carte Programme) ou depuis le programme.

   Pour plus d’informations, voir [Suppression d’un programme Sandbox](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html).

* Un utilisateur du programme Sandbox possédant le rôle *Propriétaire d’entreprise* ou *Responsable de déploiement* dans Cloud Manager peut désormais supprimer ses jeux d’environnements de production et d’évaluation via l’interface utilisateur de Cloud Manager. L’option de suppression est désormais disponible à partir de la carte Environnement dans la page **Aperçu du programme**, mais aussi dans la page **Environnements**. La sélection de l’option de suppression dans l’environnement de production ou d’évaluation supprime également l’autre dans le jeu d’environnements.

   Pour plus d’informations, voir [Suppression d’un programme Sandbox](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html).

* Repères sur la landing page pour informer l’utilisateur sur la navigation de base.

* Assistants graphiques sur la page **Aperçu du programme** afin d’informer l’utilisateur sur la navigation de base dans Cloud Manager pour la prise en main.

* Une page **APPRENDRE** est désormais disponible dans Cloud Manager, accessible par le biais de la navigation supérieure. Cette page comprend des ressources destinées à aider les utilisateurs à en savoir plus sur les workflows les plus fréquemment utilisés en fonction du rôle qui leur est attribué dans Cloud Manager.

* Les programmes Sandbox sont maintenant identifiés au moyen d’un badge **Sandbox**, affiché dans la carte du programme sur la landing page, ainsi qu’en regard du nom du programme sur la page **Aperçu du Programme**.

* Un utilisateur possédant le rôle SysAdmin dispose désormais d’un accès d’un simple clic à l’emplacement d’Admin Console d’où peuvent être gérés les rôles des utilisateurs ou les autorisations d’accès à Cloud Manager. Un bouton **Gérer l’accès** est désormais disponible dans la landing page en regard du bouton **Ajouter le programme**.

   Pour plus d’informations, voir [Tâches SysAdmin](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/onboarding/getting-access/navigation.html#sysadmin-tasks).

* Un utilisateur possédant le rôle SysAdmin dispose désormais d’un accès en un clic à l’instance d’auteur directement à partir de Cloud Manager.

   Pour plus d’informations, voir [Gestion de l’accès à l’instance d’auteur](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/onboarding/getting-access/navigation.html#manage-access-aem).

* Le journal de génération inclut désormais la liste des artefacts détectés, y compris les packages de contenu ignorés.

* L’étape de création valide désormais que tous les packages de contenu générés comprennent toutes les propriétés obligatoires : nom, groupe et version.

* L’étape de génération confirme désormais qu’elle a produit au moins un module de contenu.

### Correctifs {#bug-fixes-cm}

* Dans certains cas, les icônes de la boîte de dialogue **Créer un Programme** n’étaient pas alignées.

* L’identifiant de version d’AEM n’était pas affiché de manière cohérente sur la page **Aperçu du programme**.

* Lors de la configuration du pipeline de production, l’option **Déploiement planifié** n’était pas visible pour certains clients.

### Problèmes connus {#known-issues-cm}

* Les environnements d’un programme Sandbox sont mis en veille prolongée lorsqu’aucune activité n’est détectée pendant une certaine durée. Cet état ne sera pas appliqué dans Cloud Manager. Il peut toutefois être appliqué par le biais de Developer Console. Ce problème sera traité dans une prochaine version.

* Le lien vers Developer Console directement à partir de Cloud Manager n’affiche pas l’option permettant de mettre en veille/réactiver un environnement de programme Sandbox. Pour résoudre ce problème, une fois dans Developer Console, ajoutez le motif `#release-cm-p1234-e5678` à la fin de l’URL, où *1234* correspond à l’identifiant de programme et *5678* à l’identifiant d’environnement. Ce problème sera traité dans une prochaine version.

## Nouveautés de [!DNL Adobe Experience Manager Assets] {#aem-assets}

**Expérience utilisateur assistée pour les balises intelligentes améliorées, optimisée par Adobe Sensei**

Les balises intelligentes améliorées permettent aux entreprises d’entraîner des modèles de balisage intelligent pour reconnaître les images en fonction de balises commerciales spécifiques aux clients, en plus des balises intelligentes génériques.

Cette version apporte une nouvelle expérience utilisateur assistée qui permet de configurer l’entraînement des balises intelligentes pour des ensembles de balises spécifiques au client, mais aussi de les entraîner sur des ressources qui devront être reconnues et balisées plus tard. L&#39;expérience est désormais plus intuitive.
Former des balises intelligentes améliorées pour une formation plus intuitive aux balises intelligentes. Voir [comment ajouter des balises actives aux ressources](/help/assets/smart-tags.md) et [configurer le balisage](/help/assets/smart-tags-configuration.md)intelligent.

**Prise en charge de l&#39;assimilation, de la prévisualisation et de la diffusion du contenu 3D**

Les entreprises peuvent désormais stocker et utiliser des fichiers 3D dans AEM Assets. L’utilisateur peut télécharger, prévisualisation et utiliser divers fichiers 3D de base, notamment des fichiers OBJ, STL, GLTF et GLB. Avec l’ajout de [!DNL Dynamic Media], vous pouvez configurer et diffuser des expériences 3D à l’aide d’URL ou de visionneuses agnostiques. Il s’agit notamment de la visionneuse [!DNL Dynamic Media] 3D Experience, du composant Sites 3D Viewer et de la possibilité de diffuser des fichiers 3D à l’aide de [!DNL Dynamic Media] (réalité augmentée/réalité virtuelle). Voir [Utilisation de ressources 3D dans Dynamic Media](/help/assets/dynamic-media/assets-3d.md).

**Prise en charge d’Adobe Asset Link pour Adobe XD**

With the latest release, [!DNL Experience Manager Assets] supports a new [!DNL Adobe Asset Link] plug-in that is released with [!DNL Adobe XD] v29.3. The integration allows designers to access and use assets from [!DNL Experience Manager] in their designs, without the need to leave [!DNL Adobe XD] application. Voir [Adobe Asset Link pour Adobe XD](https://helpx.adobe.com/fr/enterprise/using/adobe-asset-link-for-xd.html).

Grâce à cette version, les utilisateurs créatifs et les concepteurs peuvent désormais utiliser des ressources gérées dans [!DNL AEM Assets] en utilisant [!DNL Adobe Asset Link] avec toute une gamme d’applications de bureau Creative Cloud, notamment [!DNL Adobe XD], [!DNL Photoshop], [!DNL Illustrator] et [!DNL InDesign].

**Amélioration de l’accessibilité**

[!DNL Adobe Experience Manager Assets] est désormais plus accessible, conformément aux directives WCAG (Web Content Accessibility Guidelines) v2.1. L’accessibilité a été améliorée pour les cas d’utilisation ou les interfaces suivants :

Les éléments de l’interface utilisateur sont compatibles avec les lecteurs d’écran, sont accessibles à l’aide du clavier et présentent un meilleur contraste. Voici une liste détaillée des améliorations :

* The [!UICONTROL Options], [!UICONTROL Scope], and [!UICONTROL Workflows] progress bars on [!UICONTROL Manage Publication] page are not read out by the screen-reader as progress bar. Les utilisateurs de lecteurs d’écran perçoivent plutôt ces indicateurs d’état comme une liste d’onglets. (CQ-4273015)

* Lors de l’ajout de balises sur la page [!UICONTROL Propriétés] d’une ressource, les utilisateurs naviguent dans une arborescence de balises. La structure de l’arborescence n’est pas accessible, car les utilisateurs de lecteurs d’écran n’entendent rien lorsqu’ils la parcourent. (CQ-4272964)

* Dans la boîte de dialogue de partage de liens, lorsque vous naviguez en mode de navigation, le lecteur d’écran :

   * Extrait les informations du tableau immédiatement au chargement de la boîte de dialogue.
   * Ne peut pas accéder à toutes les suggestions automatiques répertoriées.
   * Does not narrate the displayed auto-suggestions for the [!UICONTROL Add Email Address/Search] combo box. (CQ-4294232)

* The [!UICONTROL Metadata Schema Editor] page and its elements are now accessible using a keyboard and are screen reader friendly. (CQ-4272953) Les utilisateurs peuvent faire glisser les composants à l’aide du clavier en mode de navigation NVDA. (CQ-4296326)

* Dans l’interface utilisateur Assets, les paramètres d’affichage ne sont pas accessibles au clavier. (CQ-4289038)

* Le rapport de luminosité est inférieur à 3:1 pour les icônes de classement de couleur jaune. La fonction n’est pas utile pour les utilisateurs dont la vision est limitée ou ne percevant pas les couleurs. Les étoiles d’évaluation s’affichent dans l’onglet de la ressource ou dans la vue de carte.

* La couleur et le contraste de certains éléments de l’interface utilisateur sont mis à jour afin que les utilisateurs ayant une vision limitée ou les utilisateurs sans perception de la couleur puissent distinguer ces éléments de l’interface utilisateur. Par exemple, la couleur des icônes d’évaluation des étoiles dans la section [!UICONTROL Notation] de l’onglet [!UICONTROL Avancé] dans les [!UICONTROL propriétés] d’un fichier et dans la vue de carte est modifiée pour un contraste approprié. (CQ-4295106)

* Les lecteurs d’écran peuvent désormais lire les entrées du menu contextuel de la zone de liste de la zone de liste modifiable (dans divers champs sur différentes pages) en tant que liste d’options. (CQ-4294017)

* Pour appliquer un flux de travail à une ressource, vous pouvez accéder à la flèche chevron du [!UICONTROL journal] à l’aide du clavier. (CQ-4289268)

* Les utilisateurs peuvent supprimer les balises sélectionnées dans le champ [!UICONTROL Balises] de l’onglet [!UICONTROL Simple] de la page [!UICONTROL Propriétés] d’une ressource à l’aide d’un `x` symbole. Les lecteurs d’écran annoncent maintenant l’objectif et le nombre de balises sélectionnées (CQ-4273033).

* Les champs de formulaire en lecture seule peuvent être utilisés avec le clavier. Par exemple, les champs désactivés dans l’onglet [!UICONTROL Réglages de base] de la page [!UICONTROL Propriétés] d’une ressource. (CQ-4273031)

* Accédez maintenant aux options de filtrage des fichiers dans la barre latérale gauche à l’aide du clavier. (CQ-4273018)

* Le lecteur d’écran annonce l’objectif de divers éléments de zone de liste modifiable, tels que le champ Chemin et l’option d’ouverture de la boîte de dialogue Sélection dans l’onglet [!UICONTROL Réglages de base] de la page [!UICONTROL Propriétés] d’un fichier. (CQ-4273016)

* Les commandes de volume des vidéos sont accessibles à l’aide du clavier. (CQ-4272696)

* De nombreuses options exploitables dans l’interface utilisateur Assets n’indiquent pas le focus en cas d’utilisation du clavier. (CQ-4272694)

* Les utilisateurs de lecteurs d’écran peuvent désormais savoir quand les lignes de la vue de liste peuvent être sélectionnées à l’aide du clavier. Les informations sont annoncées lorsque le pointeur est placé sur les lignes. (CQ-4271824)

* Certains champs de formulaire, tels que les champs de nom d’utilisateur et de mot de passe sur la page de connexion, reposent sur des valeurs d’espace réservé pour donner une étiquette accessible. (CQ-4271716)

* Les éléments interactifs de l’interface utilisateur, tels que les liens et les options telles que les options d’en-tête et de zoom des ressources, la page ou le dossier de navigation, sont désormais accessibles à l’aide du clavier. (CQ-4271412)

* Les titres de toutes les pages consultées dans [!DNL Adobe Experience Manager] Assets sont désormais uniques. (CQ-4271409)

**Autres améliorations**

Cette version comprend les autres améliorations suivantes :

* Possibilité de retraiter des ressources avec des profils de traitement des ressources. Les utilisateurs peuvent ainsi contrôler entièrement le processus (effectuer le traitement complet des ressources, appliquer simplement un profil de traitement spécifique et décider si le workflow de post-traitement doit être exécuté).
* Les requêtes de recherche renvoient maintenant les résultats plus rapidement, car l’instance de grappe associée a été redémarrée en arrière-plan (auparavant, l’exécution de la recherche initiale pouvait durer plus longtemps).
* Tri par nom lorsque vous affichez des ressources en mode Liste de l’interface Assets et dans les résultats de recherche. Voir [Rechercher des ressources](/help/assets/search-assets.md#sort).
* Tri sur le critère Créé (Date) lorsque vous affichez des ressources en mode Liste de l’interface Assets et dans les résultats de recherche. Voir [Rechercher des ressources](/help/assets/search-assets.md#sort).
* Prise en charge de la conversion de fichiers EPS en images à l’aide des microservices de ressources.

### Correctifs {#assets-bug-fixes}

<!-- TBD: Add enhancements above and bug fixes below.
Seek DM bug fixes if any.
Add Nui update as shared on Slack: https://git.corp.adobe.com/nui/app/releases/tag/22
-->

In addition to the above new features, the current release provides the following bug fixes based on customer feedback for [!DNL Assets].

* Pour les fichiers de musique MP3, le bouton de lecture affiché sur la miniature dans l’aperçu DAM ne fonctionne pas. (CQ-4294731)
* Le passage du pointeur en mode Carte permet de faire défiler l’écran suite à l’activation du focus (automatique) sur les actions rapides disponibles dans la carte. (GRANITE-26895)
* L’affichage d’un trop grand nombre d’images après le défilement de nombreux résultats de recherche provoque un blocage du navigateur. (GRANITE-26432)
* Lors du téléchargement d’une ressource, si l’option de courrier électronique est sélectionnée et même si une adresse électronique valide est fournie, l’option de téléchargement n’est pas disponible. (CQ-4296535)
* Les filtres personnalisés enregistrés à titre de collections dynamiques ne sont pas correctement appliqués aux ressources. (CQ-4294942)
* Différentes améliorations concernant la recherche et l’indexation, et des corrections de bogues, ont été réalisées pour obtenir des gains de performances. (CQ-4286373)
