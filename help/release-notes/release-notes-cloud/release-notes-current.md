---
title: Notes de mise à jour d’Adobe Experience Manager as a Cloud Service version 2020.6.0
description: Notes de mise à jour d’Experience Manager version 2020.6.0
translation-type: tm+mt
source-git-commit: b0436c74389ad0b3892d1258d993c00aa470c3ab
workflow-type: tm+mt
source-wordcount: '1958'
ht-degree: 11%

---


# Notes de mise à jour d’AEM as a Cloud Service 2020.6.0 {#release-notes}

La section suivante décrit les notes de mise à jour générales d’Experience Manager Sites as a Cloud Service 2020.6.0.

## Date de publication {#release-date}

The release date for [!DNL Experience Manager] as a Cloud Service 2020.6.0 is June 04, 2020.

## Nouveautés d’AEM Sites {#aem-sites}

Consultez cette section pour en savoir plus sur les nouveautés et les mises à jour d’AEM Sites dans AEM as a Cloud Service 2020.6.0.

### Nouveautés {#whats-new-2020.6.0}

La version 2.9.0 des composants [](https://docs.adobe.com/content/help/fr-FR/experience-manager-core-components/using/introduction.html) principaux est maintenant disponible en AEM Sites, notamment :

* Intégration entre la couche [de données du client](https://github.com/adobe/adobe-client-data-layer) Adobe et les composants principaux
* Attributs d’ID HTML configurables pour tous les composants
* Un nouveau composant de barre de progression
* Plusieurs correctifs

### Correctifs {#sites-bug-fixes}

* Les composants du conteneur de mise en page ne sont pas visibles lorsque le conteneur de mise en page est copié et collé de nouveau sur une page.

* Correction d’un problème lié au redimensionnement du composant de mise en page.

* Possibilité Ajoutée de gérer les pages Angular du routage uniquement et les pages AEM/Angular.

### Accessibilité {#accessibility}

* Il est désormais possible de créer des rapports entre le rôle et l’état des masques dans la boîte de dialogue **Créer une page** lors de la navigation en mode de navigation à l’aide de la flèche vers le bas.

* Ajouté un lien dans la navigation pour permettre aux utilisateurs d’accéder au contenu principal.

* Améliorations du lecteur d’écran.

## Nouveautés des fondations dans AEM en tant que Cloud Service {#foundations}

Les délais de création du projet AEM s’améliorent en supprimant toutes les références du fichier pom.xml du projet AEM dans le référentiel distant `https://downloads.experiencecloud.adobe.com/content/maven/public`.

AEM en tant que Jar API SDK Cloud Service, qui était auparavant hébergé à cet emplacement, se trouve désormais dans Maven Central, qui est le référentiel d’artefacts par défaut de Maven.

## Nouveautés de Cloud Manager {#cloud-manager}

Consultez cette section pour en savoir plus sur les nouveautés et les mises à jour de Cloud Manager dans AEM as a Cloud Service 2020.6.0.

### Nouveautés {#what-is-new-cloud-manager}

* Un utilisateur du rôle Propriétaire ** d’entreprise dans Cloud Manager peut désormais supprimer un Programme Sandbox du landing page (par le biais d’un bouton d’action rapide sur la carte de Programme) ou du programme.

   Pour plus d&#39;informations, reportez-vous à la section [Suppression d&#39;un Programme](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html) Sandbox.

* Un utilisateur de Programme Sandbox dans le rôle Propriétaire ** d’entreprise ou *Deployment Manager* dans Cloud Manager peut désormais supprimer son jeu d’environnements de production et d’étape via l’interface utilisateur de Cloud Manager. L’option de suppression est désormais disponible à partir de la carte d’Environnement sur la page Aperçu **des** Programmes ainsi que sur la page **Environnements** . La sélection de l’option de suppression sur Production ou Stage supprime également l’autre dans l’ensemble.

   Pour plus d&#39;informations, reportez-vous à la section [Suppression d&#39;un Programme](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html) Sandbox.

* Repères sur la page d’entrée pour informer l’utilisateur sur la navigation de base.

* Coach marks sur la page Aperçu **du** Programme pour informer et informer l’utilisateur sur la navigation de base dans Cloud Manager afin de le faire démarrer.

* Une page **APPRENDRE** est désormais disponible dans Cloud Manager, accessible par le biais de la navigation supérieure. Cette page comprend des ressources destinées à aider les utilisateurs à en savoir plus sur les workflows les plus fréquemment utilisés en fonction du rôle qui leur est attribué dans Cloud Manager.

* Les Programmes Sandbox sont maintenant identifiés au moyen d’un badge **Sandbox** qui s’affichera sur la carte de programme sur le landing page, ainsi qu’en regard du nom du programme dans la page Aperçu **du** Programme.

* Un utilisateur du rôle Administrateur système dispose désormais d’un accès d’un simple clic à l’emplacement dans Admin Console d’où peuvent être gérés les rôles utilisateur ou les autorisations d’accès à Cloud Manager. Un bouton **Gérer l’accès** est désormais disponible sur le landing page en regard du bouton **Ajouter le Programme** .

   Pour plus d&#39;informations, reportez-vous aux Tâches [](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/navigation.html#sysadmin-tasks) SysAdmin.

* Un utilisateur du rôle SysAdmin dispose désormais d’un accès en un clic à l’instance d’auteur directement à partir de Cloud Manager.

   Pour plus d’informations, voir [Gestion de l’accès à l’instance](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/navigation.html#manage-access-aem) d’auteur.

* Le journal de génération inclut désormais la liste des artefacts détectés, y compris les packages de contenu ignorés.

* L’étape de création valide désormais que tous les packages de contenu générés comprennent toutes les propriétés obligatoires : nom, groupe et version.

* L’étape de création valide désormais que la génération a produit au moins un package de contenu.

### Correctifs {#bug-fixes-cm}

* Dans certains cas, les icônes de la boîte de dialogue **Créer un Programme** n’étaient pas alignées.

* L’identifiant de publication AEM n’était pas affiché de manière cohérente sur la page Aperçu **des** Programmes.

* When configuring the production pipeline, the **Scheduled Deployment** option was not visible for some customers.

### Problèmes connus {#known-issues-cm}

* Les Environnements d’un programme Sandbox sont mis en veille prolongée lorsqu’aucune activité n’est détectée pendant une certaine durée. Cet état ne sera pas observé dans Cloud Manager. L’état peut toutefois être observé via la Console développeur. Cette question sera traitée dans une prochaine version.

* Le lien vers la Console développeur directement à partir de Cloud Manager n’affiche pas l’option permettant de dé-hiberner/hiberner un environnement de Programme Sandbox. Pour résoudre ce problème, une fois dans la Console développeur, ajoutez le modèle `#release-cm-p1234-e5678` à la fin de l’URL, où *1234* correspond à l’identifiant de Programme et *5678* à l’identifiant d’Environnement. Cette question sera traitée dans une prochaine version.

## Nouveautés de la version  [!DNL Adobe Experience Manager Assets]{#aem-assets}

**Expérience utilisateur guidée pour les balises actives optimisées, optimisée par Adobe Sensei**

Les balises actives améliorées permettent aux entreprises de former des modèles de balisage intelligent pour reconnaître les images basées sur des balises commerciales spécifiques aux clients, en plus des balises actives génériques.

Avec cette version, il existe une nouvelle expérience utilisateur guidée qui permet de configurer une formation sur les balises actives pour des ensembles de balises spécifiques au client et de les former à l’utilisation de ressources qui devront être reconnues et balisées avec elles à l’avenir. C&#39;est une expérience plus intuitive.
Former des balises intelligentes améliorées pour une formation plus intuitive aux balises intelligentes. Voir [comment ajouter des balises actives aux ressources](/help/assets/smart-tags.md) et [configurer le balisage](/help/assets/smart-tags-configuration.md)intelligent.

**Prise en charge de l&#39;assimilation, de la prévisualisation et de la diffusion du contenu 3D**

Les entreprises peuvent désormais stocker et utiliser des fichiers 3D en AEM Assets. L’utilisateur peut télécharger, prévisualisation et exploiter divers fichiers 3D de base, notamment des fichiers .obj, .stl, .gltf et .glb. Avec l’ajout d’ [!DNL Dynamic Media]expériences 3D, les expériences 3D peuvent être configurées et livrées par le biais d’URL ou de visionneuses agnostiques. Cela inclut une visionneuse d’expérience [!DNL Dynamic Media] 3D, un composant Visionneuse 3D Sites et la possibilité de diffuser des fichiers 3D via [!DNL Dynamic Media] (AR/VR). Voir [Utilisation de ressources 3D dans Dynamic Media](/help/assets/dynamic-media/assets-3d.md).

**Prise en charge de Adobe Asset Link pour Adobe XD**

Avec la dernière version, [!DNL Experience Manager Assets] fournit la prise en charge d’un nouveau [!DNL Adobe Asset Link] module externe publié avec [!DNL Adobe XD] la version v29.3. L’intégration permet aux concepteurs d’accéder aux ressources et de les utiliser à partir de [!DNL Experience Manager] leurs conceptions, sans avoir à quitter [!DNL Adobe XD] l’application. Voir [Adobe Asset Link pour consulter la documentation](https://helpx.adobe.com/enterprise/using/adobe-asset-link-for-xd.html)Adobe XD.

Grâce à cette version, les utilisateurs et les concepteurs de la création peuvent désormais utiliser des ressources gérées à l’ [!DNL AEM Assets] aide [!DNL Adobe Asset Link] d’applications de bureau Creative Cloud, notamment [!DNL Adobe XD], [!DNL Photoshop][!DNL Illustrator], et [!DNL InDesign]diverses applications de bureau.

**Améliorations de l’accessibilité**

[!DNL Adobe Experience Manager Assets] est désormais plus accessible, conformément aux directives WCAG (Web Content Accessibility Guidelines) v2.1. L’accessibilité a été améliorée pour les cas d’utilisation ou les interfaces suivants :

Les éléments de l’interface utilisateur sont compatibles avec les lecteurs d’écran, sont accessibles à l’aide du clavier et présentent un meilleur contraste. Voici une liste détaillée des améliorations :

* Les indicateurs de progression des [!UICONTROL options], de la [!UICONTROL portée]et des [!UICONTROL Workflows] de la page [!UICONTROL Gérer la publication ne sont pas lus par le lecteur d’écran comme des indicateurs de progression. ] Les utilisateurs de lecteurs d’écran perçoivent ces indicateurs d’état comme une liste d’onglets. (CQ-4273015)

* Lors de l’ajout de balises dans la page [!UICONTROL Propriétés] d’une ressource, les utilisateurs naviguent dans une arborescence de balises. La structure de l’arborescence n’est pas accessible, car les utilisateurs de lecteurs d’écran n’entendent rien lors de leur navigation. (CQ-4272964)

* Dans la boîte de dialogue de partage de liens, lorsque vous naviguez en mode de navigation, le lecteur d’écran,

   * Indique les informations du tableau dès que la boîte de dialogue est chargée.
   * ne peut pas accéder à toutes les suggestions automatiques répertoriées.
   * ne décrit pas les suggestions automatiques affichées pour la zone combinée [!UICONTROL Ajouter l’adresse électronique/Rechercher] . (CQ-4294232)

* La page Editeur [!UICONTROL de Schéma de] métadonnées et ses éléments sont désormais accessibles et faciles à lire. Les options peuvent être utilisées à l’aide du clavier. (CQ-4272953) Les utilisateurs peuvent faire glisser les composants à l’aide du clavier en mode de navigation NVDA. (CQ-4296326)

* Dans l’interface utilisateur Ressources, les paramètres de vue ne sont pas accessibles par le clavier. (CQ-4289038)

* Le rapport de luminosité est inférieur à 3:1 pour les icônes de classement de couleur jaune. Elle n’est pas utile aux utilisateurs ayant une vision limitée et sans perception de la couleur. Les étoiles d’évaluation s’affichent dans l’onglet de la ressource ou dans la vue de carte.

* La couleur et le contraste de certains éléments de l’interface utilisateur sont mis à jour afin que les utilisateurs ayant une vision limitée ou les utilisateurs sans perception de la couleur puissent distinguer ces éléments de l’interface utilisateur. Par exemple, la couleur des icônes d’évaluation des étoiles dans la section [!UICONTROL Notation] de l’onglet [!UICONTROL Avancé] dans les [!UICONTROL propriétés] d’un fichier et dans la vue de carte est modifiée pour un contraste approprié. (CQ-4295106)

* Le menu contextuel de la zone de liste de la zone combinée (dans divers champs sur différentes pages) affiche désormais les entrées en tant que liste d’options qui peuvent être annoncées par les lecteurs d’écran. (CQ-4294017)

* Pour appliquer un flux de travail à une ressource, vous pouvez accéder à la flèche chevron du [!UICONTROL journal] à l’aide du clavier. (CQ-4289268)

* Les utilisateurs peuvent supprimer les balises sélectionnées dans le champ [!UICONTROL Balises] de l’onglet [!UICONTROL Simple] de la page [!UICONTROL Propriétés] d’une ressource à l’aide d’un `x` symbole. Son objectif est maintenant annoncé par les lecteurs d’écran, ainsi que le nombre de balises sélectionnées (CQ-4273033).

* Les champs de formulaire en lecture seule peuvent être utilisés avec le clavier. Par exemple, les champs désactivés dans l’onglet [!UICONTROL Réglages de base] de la page [!UICONTROL Propriétés] d’une ressource. (CQ-4273031)

* Accédez maintenant aux options de filtrage des fichiers dans la barre latérale gauche à l’aide du clavier. (CQ-4273018)

* Les lecteurs d’écran annoncent désormais correctement l’objectif de divers éléments de la zone de liste modifiable, tels que le champ Chemin et l’option d’ouverture de la boîte de dialogue Sélection dans l’onglet [!UICONTROL Réglages de base] de la page [!UICONTROL Propriétés] d’un fichier. (CQ-4273016)

* Les commandes de volume des vidéos sont accessibles à l’aide du clavier. (CQ-4272696)

* De nombreuses options exploitables dans l’interface utilisateur Ressources n’indiquent pas la cible d’action lors de l’utilisation du clavier. (CQ-4272694)

* Les utilisateurs de lecteurs d’écran peuvent désormais savoir quand les lignes de la vue de liste peuvent être sélectionnées à l’aide du clavier. Les informations sont annoncées lorsque le pointeur est placé sur les lignes. (CQ-4271824)

* Certains champs de formulaire, tels que les champs de nom d’utilisateur et de mot de passe sur la page de connexion, reposent sur des valeurs d’espace réservé pour donner une étiquette accessible. (CQ-4271716)

* Les éléments interactifs de l’interface utilisateur, tels que les liens et les options telles que les options d’en-tête et de zoom des ressources, la page ou le dossier de navigation, sont désormais accessibles à l’aide du clavier. (CQ-4271412)

* Les titres de toutes les pages consultées sur [!DNL Adobe Experience Manager] les ressources sont désormais uniques. (CQ-4271409)

**Autres améliorations**

Cette version comprend les améliorations supplémentaires suivantes :

* Possibilité de retraiter des ressources avec des profils de traitement des ressources, ce qui permet aux utilisateurs de contrôler entièrement le processus (exécuter le traitement complet des ressources, appliquer un profil de traitement spécifique et décider si le processus de post-traitement doit être exécuté).
* Les requêtes de recherche renvoient les résultats plus rapidement maintenant que l’instance de grappe sous-jacente a été redémarrée en arrière-plan (l’exécution de recherche initiale pourrait durer plus longtemps dans ce cas auparavant).
* Trier par &quot;Nom&quot; lorsque vous affichez des ressources dans la vue de listes dans l’interface Ressources et dans les résultats de la recherche. Voir Fichiers [](/help/assets/search-assets.md#sort)de recherche.
* Trier sur &quot;Créé&quot; (Date) lors de l’affichage des ressources dans la vue de liste dans l’interface Ressources et dans les résultats de la recherche. Voir Fichiers [](/help/assets/search-assets.md#sort)de recherche.
* Prise en charge de la conversion de fichiers EPS en images à l’aide de microservices de ressources.

### Correctifs {#assets-bug-fixes}

<!-- TBD: Add enhancements above and bug fixes below.
Seek DM bug fixes if any.
Add Nui update as shared on Slack: https://git.corp.adobe.com/nui/app/releases/tag/22
-->

En plus des nouvelles fonctionnalités ci-dessus, la version actuelle fournit les correctifs de bogues suivants en fonction des commentaires des clients pour [!DNL Assets].

* Pour les fichiers de musique MP3, le bouton de lecture affiché sur la miniature dans la prévisualisation DAM ne fonctionne pas. (CQ-4294731)
* Placer le pointeur sur la vue de la carte permet de faire défiler l’écran lorsque l’utilisateur se concentre (automatiquement) sur les actions rapides disponibles dans la carte. (GRANITE-26895)
* L’affichage d’un trop grand nombre d’images après le défilement d’un grand nombre de résultats de recherche provoque un blocage du navigateur. (GRANITE-26432)
* Lors du téléchargement d’un fichier, si l’option de messagerie est sélectionnée et même si un ID de messagerie valide est fourni, l’option de téléchargement n’est pas disponible. (CQ-4296535)
* Les filtres personnalisés enregistrés en tant que collections dynamiques ne sont pas correctement appliqués aux ressources. (CQ-4294942)
* Plusieurs améliorations de la recherche et de l’indexation et corrections de bogues ont été apportées pour améliorer les performances. (CQ-4286373)
