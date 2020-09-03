---
title: Notes de mise à jour de la version 2020.8.0 [!DNL Adobe Experience Manager] de Cloud Service.
description: '[ !DNL Adobe Experience Manager] en tant que notes de mise à jour Cloud Service pour la version 2020.8.0.'
translation-type: tm+mt
source-git-commit: 87d41dc311e96c41be230046f511d2c3301d48f1
workflow-type: tm+mt
source-wordcount: '1057'
ht-degree: 12%

---


# Release Notes for [!DNL Adobe Experience Manager] as a Cloud Service 2020.8.0 {#release-notes}

La section suivante décrit les notes de mise à jour générales d’Experience Manager as a Cloud Service 2020.8.0.

## Date de publication {#release-date}

The release date for [!DNL Experience Manager] as a Cloud Service 2020.8.0 is August 27, 2020.

## [!DNL Adobe Experience Manager Sites]as a Cloud Service{#sites}

### What is new in [!DNL Sites] {#what-is-new-sites}

* Possibilité de [restaurer les pages et les sous-pages (arbres de page) dans une version](/help/sites-cloud/authoring/features/page-versions.md#reinstating-versions)antérieure.

* Possibilité de créer des lancements dans AEM éditeur d’applications monopages.

## [!DNL Adobe Experience Manager Assets]as a Cloud Service{#assets}

### What is new in [!DNL Assets] {#what-is-new-assets}

* Le transcodage vidéo est désormais pris en charge avec les microservices de ressources, avec une nouvelle section Vidéo dans l’écran Profils [!UICONTROL de] traitement prenant en charge la configuration du débit vidéo et des dimensions (le format de sortie est MP4 avec le codec H.264). For details, see [manage video assets](/help/assets/manage-video-assets.md#transcode-video). Pour d’autres options de transcodage et un module complémentaire de diffusion vidéo [!DNL Dynamic Media] peuvent être utilisés.

* Lors des nouveaux [!DNL Experience Manager Assets] déploiements, la fonctionnalité de balisage intelligent est désormais configurée par défaut. Il n’est pas nécessaire d’intégrer manuellement [!DNL Adobe Developer Console]. Sur les déploiements existants, les administrateurs [configurent l’intégration](/help/assets/smart-tags-configuration.md#aio-integration) des balises actives comme auparavant.

* Une nouvelle expérience [de téléchargement de](/help/assets/download-assets-from-aem.md) ressources permet,

   * Téléchargement asynchrone pour les téléchargements volumineux afin que les utilisateurs n’aient pas à attendre.

   * Une nouvelle API modulaire pour l&#39;extensibilité des développeurs.

* [!DNL Experience Manager] a amélioré les performances de l’extraction des métadonnées pour les microservices de ressources. Cela augmente le débit global d&#39;assimilation des actifs.

* Utilisez le profil de traitement pour générer des métadonnées personnalisées à l’aide de Compute Service. Voir Métadonnées [personnalisées à l’aide du profil de traitement](/help/assets/manage-metadata.md#metadata-compute-service)

* Une expérience de téléchargement plus simple pour les utilisateurs du portail de marque que les administrateurs peuvent configurer. Voir Présentation [de l’expérience](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/introduction/whats-new.html#download-configurations)de téléchargement.

* Les prévisualisations de document PDF natives et de haute fidélité sont désormais disponibles dans le portail des marques. Voir Présentation [du lecteur de](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/introduction/whats-new.html#doc-viewer)documents.

* Vous pouvez désormais invalider le cache CDN (Content Diffusion Network) directement depuis [!DNL Dynamic Media] AEM en tant que Cloud Service (au lieu d’utiliser [!DNL Dynamic Media Classic]) pour vous assurer que les derniers actifs sont diffusés en quelques minutes au lieu de quelques heures. Voir [Invalidation du cache CDN à l’aide de Contenu multimédia dynamique.](/help/assets/dynamic-media/invalidate-cdn-cache-dynamic-media.md)

* La prise en charge de l’accessibilité est ajoutée aux commandes d’interface utilisateur, à la navigation, à la navigation et à la recherche dans [!DNL Assets].

   * Si vous appuyez sur la touche Echap après avoir sélectionné l’option [!UICONTROL Ajouter le rendu] , la sélection revient à la barre d’outils. <!-- via CQ-4293594-->
   * La mise au point du clavier fonctionne comme prévu lors de l’utilisation de la zone de liste déroulante Courriel. <!-- via CQ-4286215 -->
   * Les éléments en accordéon de la section filtres de recherche sont interprétés comme des accordéons extensibles standard. <!-- via CQ-4273103 -->
   * Lors de l’application d’une balise à une ressource, la boîte de dialogue affiche les balises sous forme d’éléments d’arborescence. Les attributs ARIA sont correctement appliqués aux éléments de l&#39;arborescence pour les rendre accessibles dès maintenant. <!-- via CQ-4272964 -->

* [!DNL AEM Desktop app] La version 2.0.3 est désormais disponible, ce qui améliore la compatibilité avec la version [!DNL AEM] 6.5.5 [!DNL Service Pack] et met à jour la liste de compatibilité du système d’exploitation client (suppression [!DNL Windows] 7 et [!DNL MacOS] versions antérieures à la version 10.14).

### Bugs résolus dans [!DNL Assets] {#bugs-fixed}

* L’option Créer une relation et Annuler la relation ne répond pas lorsque l’utilisateur clique pour la première fois. (CQ-4299022)
* Lors du téléchargement d’un fichier, si vous sélectionnez l’option permettant de le recevoir par courrier électronique, le courrier électronique n’est pas envoyé. (CQ-4299146)

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nouveautés {#what-is-new-commerce}

* La fonction Console produit est désormais disponible. Cela permet aux spécialistes du marketing/auteurs d’AEM de vue et de parcourir les catégories et les produits stockés dans l’arrière-plan du commerce. La prise en charge des propriétés des catégories et des produits dans la Console produit est également fournie.

* Les sélecteur de produits et de Catégories ont été améliorés pour permettre aux spécialistes du marketing de sélectionner un produit via le SKU ou de sélectionner une catégorie via l’ID de catégorie.

## Cloud Manager {#cloud-manager}

### Date de publication {#release-date-cm}

La date de publication de la mise à jour 2020.8.0 de [!UICONTROL Cloud Manager] est le 06 août 2020.

### Nouveautés {#what-is-new-cloud-manager}

* L’audit de contenu est une fonctionnalité activée sur les pipelines de production de sites Cloud Manager. La configuration du pipeline de production pour les programmes avec sites comprend désormais un troisième onglet nommé Audit **du** contenu. Chaque fois qu&#39;un pipeline de production est exécuté, une nouvelle étape de contrôle du contenu est incluse dans le pipeline après des tests fonctionnels personnalisés qui évaluent le site par rapport à un certain nombre de dimensions, y compris les performances, l&#39;optimisation du référencement (optimisation pour les moteurs de recherche), l&#39;accessibilité, les meilleures pratiques et le PWA (application Web progressive).

   >[!NOTE]
   >L’audit de contenu est désormais renommé Audit d’expérience.

   Refer to [Experience Audit Testing](/help/implementing/cloud-manager/experience-audit-testing.md) for more details.

* Les nouveaux environnements créés dans les programmes Ressources seront désormais automatiquement configurés avec Smart Content Services.

* Les environnements en veille prolongée peuvent être désactivés à partir de la page **Présentation** de Cloud Manager.

* Possibilité d’effectuer des vérifications d’expérience sur les pages, optimisées par Google Lighthouse. Dans le cadre du pipeline de Cloud Manager, jusqu’à 25 pages peuvent être vérifiées et validées par rapport aux IPC d’expérience et les scores s’affichent dans l’interface utilisateur de Cloud Manager.

### Correctifs {#bug-fixes-cm}

* Certains plug-ins SonarQube inutiles et indésirables étaient exécutés dans le cadre de l’analyse de la qualité du code.

* Sur la page d’exécution du pipeline, le nom de la branche n’était pas correctement formaté.

* Dans certains cas, les exécutions de pipeline achevées n’étaient pas été enregistrées comme ayant été achevées, ce qui empêchait de nouvelles exécutions de pipeline.

* Les exécutions de pipelines étaient parfois *bloquées* en raison de problèmes de communication interne.

* Lors de la mise en service d’une nouvelle organisation, certains utilisateurs ayant des rôles d’administration autres que les administrateurs système ont reçu par erreur l’accès à Cloud Manager.

* Dans certaines conditions, la tâche de mise à jour des index a été lancée plusieurs fois en parallèle, ce qui a entraîné un échec du déploiement.

* Les info-bulles des cartes de programme n’étaient pas toujours correctes.

* L’interface utilisateur permettait par erreur de tenter une opération sur un environnement alors qu’elle était en cours de suppression.

* There was a color mismatch on the Cloud Manager&#39;s **Overview** page.

### Problèmes connus {#known-issues-cm}

* Les pages non valides sont incluses en plaçant la note moyenne d’audit du contenu en dessous de ce qu’elle devrait être.

* L’onglet Audit de contenu affiche incorrectement l’URL de base à l’aide du domaine d’auteur et non du domaine de publication.

* Pour activer l’étape de contrôle du contenu, les utilisateurs doivent modifier le pipeline et, éventuellement, ajouter des pages. Si aucune page n&#39;est ajoutée, la page d&#39;accueil fera l&#39;objet d&#39;un audit.

## Outil de transfert de contenu {#content-transfer-tool}

Suivez cette section pour en savoir plus sur les nouveautés et les mises à jour de la version 1.0.4 de l’outil de transfert de contenu.

### Nouveautés {#what-is-new-ctt}

* L’outil de transfert de contenu prend désormais en charge le magasin de données partagé S3.

### Correctifs {#ctt-bug-fixes}

* Ajout de délais d’attente supplémentaires pour que l’outil exécute les actions.

* L’interface utilisateur des versions antérieures présentait parfois une extraction réussie, même si le journal présentait des erreurs.

## Outils de refactorisation du code {#code-refactoring-tools}

Suivez cette section pour en savoir plus sur les nouveautés et les mises à jour des outils de refactorisation du code.

### Nouveautés {#what-is-new-refactoring}

* Module externe AIO-CLI sorti pour unifier les outils de refactorisation du code pour permettre aux développeurs d’appeler et d’exécuter des outils de refactorisation du code à partir d’un seul endroit. Refer to [Git Resource: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) for more details.

* aem Dispatcher Converter a été étendu pour prendre en charge les conversions des configurations On-premise et Adobe Managed Services Dispatcher en AEM en tant que configurations de Répartiteur compatibles avec les Cloud Service. Reportez-vous à la ressource [Git : aem Cloud Service Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter) pour plus d&#39;informations.

* aem Réécriture du convertisseur de répartiteur dans ` node.js ` et intégration avec le module externe AIO-CLI.
