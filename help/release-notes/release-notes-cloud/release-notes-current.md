---
title: Notes de mise à jour d’Adobe Experience Manager as a Cloud Service version 2020.6.0
description: Notes de mise à jour d’Experience Manager version 2020.6.0
translation-type: tm+mt
source-git-commit: 41684858f1fe516046b9601c1d869fff180320e0
workflow-type: tm+mt
source-wordcount: '1843'
ht-degree: 11%

---


# Notes de mise à jour d’AEM as a Cloud Service 2020.6.0 {#release-notes}

La section suivante décrit les notes de mise à jour générales d’Experience Manager Sites as a Cloud Service 2020.6.0.

## Date de publication {#release-date}

The release date for [!DNL Experience Manager] as a Cloud Service 2020.6.0 is June 04, 2020.

## What&#39;s New in AEM Sites {#aem-sites}

Suivez cette section pour en savoir plus sur les nouveautés et les mises à jour des sites AEM dans AEM as a Cloud Service Release 2020.6.0.

### Nouveautés {#whats-new-2020.6.0}

La version 2.9.0 des composants [](https://docs.adobe.com/content/help/fr-FR/experience-manager-core-components/using/introduction.html) principaux est désormais disponible dans le cadre des sites AEM, notamment :

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


## Nouveautés des fondations dans AEM en tant que service Cloud {#foundations}

Les délais de création du projet AEM s’améliorent en supprimant toutes les références du fichier pom.xml du projet AEM dans le référentiel distant `https://downloads.experiencecloud.adobe.com/content/maven/public`.

Le Jar API AEM as a Cloud Service SDK, qui était auparavant hébergé à cet emplacement, se trouve désormais dans Maven Central, qui est le référentiel d’artefacts par défaut de Maven.

## Nouveautés de Cloud Manager {#cloud-manager}

Suivez cette section pour en savoir plus sur les nouveautés et les mises à jour de Cloud Manager dans AEM as a Cloud Service 2020.6.0.

### Nouveautés {#what-is-new-cloud-manager}

* Un utilisateur du rôle Propriétaire ** d’entreprise dans Cloud Manager peut désormais supprimer un Programme Sandbox du landing page (par le biais d’un bouton d’action rapide sur la carte de Programme) ou du programme.

   Pour plus d&#39;informations, reportez-vous à la section [Suppression d&#39;un Programme](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html) Sandbox.

* Un utilisateur de Programme Sandbox dans le rôle Propriétaire ** d’entreprise ou *Deployment Manager* dans Cloud Manager peut désormais supprimer son jeu d’environnements de production et d’étape via l’interface utilisateur de Cloud Manager. L’option de suppression est désormais disponible à partir de la carte d’Environnement sur la page Aperçu **des** Programmes ainsi que sur la page **Environnements** . La sélection de l’option de suppression sur Production ou Stage supprime également l’autre dans l’ensemble.

   Pour plus d&#39;informations, reportez-vous à la section [Suppression d&#39;un Programme](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html) Sandbox.

* Repères sur la page d’entrée pour informer l’utilisateur sur la navigation de base.

* Coach marks sur la page Aperçu **du** Programme pour informer et informer l’utilisateur sur la navigation de base dans Cloud Manager afin de le faire démarrer.

* Une page **APPRENDRE** est désormais disponible dans Cloud Manager, accessible par le biais de la navigation supérieure. Cette page comprend des ressources destinées à aider les utilisateurs à en savoir plus sur les workflows les plus fréquemment utilisés en fonction du rôle qui leur est attribué dans Cloud Manager.

* Les Programmes Sandbox sont maintenant identifiés au moyen d’un badge **Sandbox** qui s’affichera sur la carte de programme sur le landing page, ainsi qu’en regard du nom du programme dans la page Aperçu **du** Programme.

* Un utilisateur du rôle Administrateur système dispose désormais d’un accès en un clic à l’emplacement dans la console d’administration à partir duquel les rôles utilisateur ou les autorisations de Cloud Manager peuvent être gérés. Un bouton **Gérer l’accès** est désormais disponible sur le landing page en regard du bouton **Ajouter le Programme** .

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

<!-- 
Assets RNs are being authored and are a work in progress.
PM/EM review required before publishing.
-->

**Expérience utilisateur guidée pour les balises actives optimisées, optimisée par Adobe Sensei**

Les balises actives améliorées permettent aux entreprises de former des modèles de balisage intelligent pour reconnaître les images basées sur des balises commerciales spécifiques aux clients, en plus des balises actives génériques.

Avec cette version, il existe une nouvelle expérience utilisateur guidée qui permet de configurer une formation sur les balises actives pour des ensembles de balises spécifiques au client et de les former à l’utilisation de ressources qui devront être reconnues et balisées avec elles à l’avenir. C&#39;est une expérience plus intuitive.
Former des balises intelligentes améliorées pour une formation plus intuitive aux balises intelligentes. Voir [comment utiliser les balises](/help/assets/smart-tags.md) actives et [configurer le balisage](/help/assets/smart-tags-configuration.md)intelligent.

**Prise en charge de l&#39;assimilation, de la prévisualisation et de la diffusion du contenu 3D**

Les entreprises peuvent désormais stocker et utiliser des fichiers 3D dans AEM Assets. L’utilisateur peut télécharger, prévisualisation et exploiter divers fichiers 3D de base, notamment des fichiers .obj, .stl, .gltf et .glb. Avec l’ajout d’ [!DNL Dynamic Media]expériences 3D, les expériences 3D peuvent être configurées et livrées par le biais d’URL ou de visionneuses agnostiques. Cela inclut une visionneuse d’expérience [!DNL Dynamic Media] 3D, un composant Visionneuse 3D Sites et la possibilité de diffuser des fichiers 3D via [!DNL Dynamic Media] (AR/VR). Voir [Utilisation de fichiers 3D dans Contenu multimédia](/help/assets/dynamic-media/assets-3d.md)dynamique.

<!-- Hiding this as the GA is at a later date. 
**Adobe Asset Link support for Adobe XD**

With the latest release, [!DNL Experience Manager Assets] provides support for a new [!DNL Adobe Asset Link] plug-in that is released with [!DNL Adobe XD] v29. The integration allows designers to access and use assets from [!DNL Experience Manager] in their designs, without the need to leave [!DNL Adobe XD] application. See [Adobe Asset Link documentation](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html).
-->

**Améliorations de l’accessibilité**

[!DNL Adobe Experience Manager Assets] est désormais plus accessible, conformément aux directives WCAG (Web Content Accessibility Guidelines) v2.1. L’accessibilité a été améliorée pour les cas d’utilisation ou les interfaces suivants :

* Les éléments, commandes, pages et boîtes de dialogue de l’interface utilisateur sont faciles à lire.
* Les éléments, les contrôles et les champs de formulaire d’entrée de l’interface utilisateur sont accessibles à l’aide du clavier.
* Changement de couleur ou de contraste de certains éléments d&#39;interface pour les rendre plus reconnaissables par les utilisateurs avec une vision limitée et sans perception de la couleur. Par exemple, les ressources présentent désormais un contraste approprié dans les icônes d’évaluation des étoiles de la page [!UICONTROL Propriétés] et de la vue des cartes.

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

Outre les nouvelles fonctionnalités ci-dessus, la version actuelle fournit les améliorations et correctifs suivants en fonction des commentaires des clients sur [!DNL Assets]la page.

* Pour les fichiers de musique MP3, le bouton de lecture affiché sur la miniature dans la prévisualisation DAM ne fonctionne pas. (CQ-4294731)
* Placer le pointeur sur la vue de la carte permet de faire défiler l’écran lorsque l’utilisateur se concentre (automatiquement) sur les actions rapides disponibles dans la carte. (GRANITE-26895)
* L’affichage d’un trop grand nombre d’images après le défilement d’un grand nombre de résultats de recherche provoque un blocage du navigateur. (GRANITE-26432)
* Les indicateurs de progression des [!UICONTROL options], de la [!UICONTROL portée]et des [!UICONTROL Workflows] de la page [!UICONTROL Gérer la publication ne sont pas lus par le lecteur d’écran comme des indicateurs de progression. ] Les utilisateurs de lecteurs d’écran perçoivent ces indicateurs d’état comme une liste d’onglets. (CQ-4273015)
* Lors du téléchargement d’un fichier, si l’option de messagerie est sélectionnée et même si un ID de messagerie valide est fourni, l’option de téléchargement n’est pas disponible. (CQ-4296535)

* Lors de l’ajout de balises dans la page [!UICONTROL Propriétés] d’une ressource, les utilisateurs naviguent dans une arborescence de balises. La structure de l’arborescence n’est pas accessible, car les utilisateurs de lecteurs d’écran n’entendent rien lors de leur navigation. (CQ-4272964)
* Dans la boîte de dialogue de partage de liens, lorsque vous naviguez en mode de navigation, le lecteur d’écran,

   * Indique les informations du tableau dès que la boîte de dialogue est chargée.
   * ne peut pas accéder à toutes les suggestions automatiques répertoriées.
   * ne décrit pas les suggestions automatiques affichées pour la zone combinée [!UICONTROL Ajouter l’adresse électronique/Rechercher] . (CQ-4294232)

* Les options de glissement ne fonctionnent pas avec le clavier en mode de navigation NVDA dans l’éditeur de schémas de métadonnées. (CQ-4296326)
* Dans l’interface utilisateur Ressources, les paramètres de vue ne sont pas accessibles par le clavier. (CQ-4289038)
* Les filtres personnalisés enregistrés en tant que collections dynamiques ne sont pas correctement appliqués aux ressources. (CQ-4294942)
* Plusieurs améliorations de la recherche et de l’indexation et corrections de bogues ont été apportées pour améliorer les performances. (CQ-4286373)
* Le rapport de luminosité est inférieur à 3:1 pour les icônes de classement de couleur jaune. Elle n’est pas utile aux utilisateurs ayant une vision limitée et sans perception de la couleur. Les étoiles d’évaluation s’affichent dans la section [!UICONTROL Évaluation] de l’onglet [!UICONTROL Avancé] dans [!UICONTROL Propriétés] de la ressource ou dans la vue de carte (CQ-4295106).
* La liste déroulante de la zone de liste de la zone combinée (dans divers champs sur différentes pages) affiche désormais les entrées en tant que liste d’options qui peuvent être annoncées par les lecteurs d’écran. (CQ-4294017)
* Impossible d&#39;accéder à la flèche du chevron vers le haut dans le [!UICONTROL journal] à l&#39;aide du clavier pour appliquer un flux de travail à une ressource. (CQ-4289268)
* Les options (comportant [!UICONTROL x]) permettant de supprimer chacune des balises sélectionnées sous le champ [!UICONTROL Balises] de l’onglet [!UICONTROL Réglages de base] de [!UICONTROL Propriétés sont désormais accessibles aux lecteurs d’écran. ] (CQ-4273033)
* Les champs de formulaire en lecture seule (par exemple, les champs désactivés dans l’onglet  Simple de [!UICONTROL Propriétés]de fichier) sont désormais activables à l’aide du clavier. (CQ-4273031)
* L’option permettant d’ouvrir la barre latérale du filtre est désormais accessible à l’aide du clavier. (CQ-4273018)
* L’objectif de divers éléments de la zone de liste modifiable (tels que le champ Chemin et l’option permettant d’ouvrir la boîte de dialogue Sélection dans l’onglet Elémentaire Propriétés du fichier) est maintenant correctement annoncé par les lecteurs d’écran. (CQ-4273016)
* [!UICONTROL La page Editeur] de Schéma de métadonnées et ses éléments ne sont pas accessibles à l’aide du clavier et ne sont pas compatibles avec les lecteurs d’écran. (CQ-4272953)
* Les commandes de volume de vidéo ne sont pas accessibles à l’aide du clavier. (CQ-4272696)
* De nombreuses options exploitables dans l’interface utilisateur Ressources n’indiquent pas la cible d’action lors de l’utilisation du clavier. (CQ-4272694)
* Les utilisateurs de lecteurs d’écran ne savent pas que les lignes de la vue de liste peuvent être sélectionnées lors de l’utilisation du clavier. Les informations ne sont annoncées que lorsque la souris survole les lignes. (CQ-4271824)
* Certains champs de formulaire, tels que les champs de nom d’utilisateur et de mot de passe sur la page de connexion, reposent uniquement sur des valeurs d’espace réservé pour donner une étiquette accessible. (CQ-4271716)
* Les éléments interactifs de l’interface utilisateur, tels que les liens et les options (sur les options d’en-tête et de zoom de la page de ressources, la navigation dans les dossiers), sont désormais accessibles à l’aide du clavier. (CQ-4271412)
* Les titres de toutes les pages consultées sur [!DNL Adobe Experience Manager] les ressources sont désormais uniques. (CQ-4271409)
