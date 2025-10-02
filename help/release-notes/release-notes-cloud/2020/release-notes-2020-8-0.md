---
title: Notes de mise à jour de la version 2020.8.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour d’[!DNL Adobe Experience Manager] as a Cloud Service pour la version 2020.8.0.
exl-id: 83413130-ae90-4419-bcf7-42fdc740452b
feature: Release Information
role: Admin
source-git-commit: 2aea79d42ef9627a8fc758077a7ee012592888d7
workflow-type: tm+mt
source-wordcount: '1031'
ht-degree: 90%

---

# Notes de mise à jour pour [!DNL Adobe Experience Manager] as a Cloud Service 2020.8.0 {#release-notes}

La section suivante décrit les notes de mise à jour générales d’Experience Manager as a Cloud Service 2020.8.0.


## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### Nouveautés d’[!DNL Sites]  {#what-is-new-sites}

* Possibilité de [restaurer les pages et les sous-pages (arborescences de page) dans une version antérieure](/help/sites-cloud/authoring/sites-console/page-versions.md#reinstating-versions).

* Possibilité de [créer des lancements](/help/sites-cloud/authoring/launches/overview.md) dans AEM [Éditeur SPA](/help/implementing/developing/hybrid/introduction.md).


## [!DNL Adobe Experience Manager Assets] as a Cloud Service {#assets}

### Nouveautés d’[!DNL Assets]  {#what-is-new-assets}

* Le transcodage vidéo est désormais pris en charge avec les microservices de ressources. Une nouvelle section de la configuration des [!UICONTROL Profils de traitement] permet de définir le débit et les dimensions d’une vidéo. Le format de sortie est MP4 avec le codec H.264. Pour plus d’informations, voir [Gestion des ressources vidéo](/help/assets/manage-video-assets.md#transcode-video). Pour accéder à d’autres options de transcodage et à la diffusion vidéo, utilisez le module complémentaire [!DNL Dynamic Media].

* Pour les nouveaux déploiements d’[!DNL Experience Manager Assets], la fonctionnalité de balisage intelligent est désormais configurée par défaut. Il n’est pas nécessaire d’intégrer manuellement [!DNL Adobe Developer Console]. Sur les déploiements existants, les administrateurs et administratrices configurent l’intégration des balises intelligentes comme auparavant.

* Une nouvelle [expérience de téléchargement de ressources](/help/assets/download-assets-from-aem.md) offre les avantages suivants :

   * Téléchargement asynchrone pour les téléchargements volumineux afin que les utilisateurs n’aient pas à attendre.
   * Une nouvelle API modulaire pour l’extensibilité destinée aux développeurs.

* Les performances d’extraction des métadonnées des microservices de ressources ont été améliorées. Le débit global d’ingestion des ressources a ainsi été augmenté.

* Utilisez un profil de traitement pour générer des métadonnées personnalisées à l’aide de Compute Service. Voir [Métadonnées personnalisées à l’aide de profils de traitement](/help/assets/manage-metadata.md#metadata-compute-service).

* Une expérience de téléchargement plus simple pour les utilisateurs de Brand Portal, configurable par les administrateurs. Voir [Aperçu de l’expérience de téléchargement](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/whats-new.html?lang=fr#download-configurations).

* Les aperçus de documents PDF natifs et haute fidélité sont désormais disponibles dans Brand Portal. Voir [Aperçu du logiciel de visualisation de documents](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/whats-new.html?lang=fr#doc-viewer).

* Vous pouvez désormais invalider le cache CDN (réseau de diffusion de contenu) directement depuis [!DNL Dynamic Media]AEM as a Cloud Service (plutôt qu’avec [!DNL Dynamic Media Classic]). Cette opération garantit que les dernières ressources sont diffusées en quelques minutes au lieu de quelques heures auparavant. Voir [Invalidation du cache CDN à l’aide de Dynamic Media](/help/assets/dynamic-media/invalidate-cdn-cache-dynamic-media.md).

* Une prise en charge améliorée de l’accessibilité a été ajoutée aux commandes de l’interface utilisateur, à la navigation et à la recherche dans [!DNL Assets].

   * Si vous appuyez sur la touche Échap après avoir sélectionné l’option [!UICONTROL Ajouter le rendu], la sélection revient sur la barre d’outils. <!-- via CQ-4293594-->
   * La sélection du clavier fonctionne comme prévu lors de l’utilisation de la zone de liste modifiable E-mail. <!-- via CQ-4286215 -->
   * Les éléments en accordéon de la section des filtres de recherche sont interprétés comme des accordéons extensibles standard. <!-- via CQ-4273103 -->
   * Lors de l’application d’une balise à une ressource, la boîte de dialogue affiche les balises sous forme d’éléments d’arborescence. Les attributs ARIA sont correctement appliqués aux éléments de l’arborescence pour les rendre immédiatement accessibles. <!-- via CQ-4272964 -->

* La version 2.0.3 d’[!DNL AEM Desktop app] est désormais disponible. Elle améliore la compatibilité avec le Service Pack [!DNL Experience Manager] 6.5.5 et comporte une liste de compatibilité du système d’exploitation client mise à jour. Les versions de [!DNL Windows] 7 et [!DNL macOS] antérieures à la version 10.14 ne sont pas prises en charge.

### Correctifs d’[!DNL Assets]  {#bugs-fixed}

* Les options Mettre en relation et Ne plus mettre en relation ne répondent pas lorsque l’utilisateur clique pour la première fois. (CQ-4299022)
* Lors du téléchargement d’une ressource, si vous sélectionnez l’option permettant de le recevoir par e-mail, l’e-mail n’est pas envoyé. (CQ-4299146)

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nouveautés {#what-is-new-commerce}

* La fonction Console produit est désormais disponible. Elle permet aux spécialistes du marketing/auteurs d’AEM d’afficher et parcourir les catégories et les produits stockés en arrière-plan des activités de commerce. La prise en charge des propriétés des catégories et des produits est également assurée dans la Console produit.

* Les sélecteurs de produits et de catégories ont été améliorés pour permettre aux spécialistes du marketing de sélectionner un produit par le biais de l’unité de gestion de stock (SKU) ou une catégorie à l’aide de l’identifiant de catégorie.

## Cloud Manager {#cloud-manager}

### Date de publication {#release-date-cm}

La date de publication de la mise à jour 2020.8.0 de [!UICONTROL Cloud Manager] est le 06 août 2020.

### Nouveautés {#what-is-new-cloud-manager}

* L’audit de contenu est une fonctionnalité activée sur les pipelines de production de sites Cloud Manager. La configuration du pipeline de production pour les programmes utilisant Sites comprend désormais un troisième onglet nommé **Audit de contenu**. Chaque fois qu’un pipeline de production est exécuté, une nouvelle étape d’audit du contenu est incluse dans le pipeline après des tests fonctionnels personnalisés qui évaluent le site par rapport à plusieurs dimensions, y compris les performances, l’optimisation du moteur de recherche (SEO), l’accessibilité, les bonnes pratiques et le PWA (application web progressive).


  >[!NOTE]
  >L’audit de contenu a depuis été renommé Audit d’expérience.

  Pour plus d’informations, voir [Tests d’audit d’expérience](/help/implementing/cloud-manager/reports/report-experience-audit.md).

* Les environnements nouvellement créés dans les programmes Assets seront désormais automatiquement configurés avec les services de contenu dynamique.

* Il est possible de désactiver les environnements placés en veille prolongée à l’aide de la page **Aperçu** de Cloud Manager.

* Possibilité d’effectuer des vérifications d’expérience sur les pages, optimisées par Google Lighthouse. Dans le cadre du pipeline de Cloud Manager, il est possible de vérifier et valider jusqu’à 25 pages concernant les indicateurs de performances clés d’expérience et les scores s’affichent dans l’interface utilisateur de Cloud Manager.

### Correctifs {#bug-fixes-cm}

* Certains plug-ins SonarQube inutiles et indésirables étaient exécutés dans le cadre de l’analyse de la qualité du code.

* Sur la page d’exécution du pipeline, le nom de la branche n’était pas correctement formaté.

* Dans certains cas, les exécutions de pipeline achevées n’étaient pas été enregistrées comme ayant été achevées, ce qui empêchait de nouvelles exécutions de pipeline.

* Les exécutions de pipelines étaient parfois *bloquées* en raison de problèmes de communication interne.

* Lors de la mise en service d’une nouvelle organisation, certains utilisateurs exerçant des rôles d’administration autres que ceux des administrateurs système recevaient par erreur l’accès à Cloud Manager.

* Dans certaines conditions, le traitement de mise à jour des index était lancé plusieurs fois en parallèle, ce qui entraînait l’échec du déploiement.

* Les info-bulles des cartes de programme n’étaient pas toujours correctes.

* L’interface utilisateur permettait par erreur de tenter une opération sur un environnement alors qu’elle était en cours de suppression.

* Les couleurs n’étaient pas cohérentes sur la page **Aperçu** de Cloud Manager.

### Problèmes connus {#known-issues-cm}

* Les pages non valides sont incluses, ce qui amène la note moyenne d’audit de contenu au-dessous de ce qu’elle devrait être.

* L’onglet Audit du contenu affiche incorrectement l’URL de base en utilisant le domaine d’auteur au lieu du domaine de publication.

* Pour activer l’étape d’audit du contenu, les personnes utilisatrices doivent modifier le pipeline et éventuellement ajouter des pages. Si aucune page n’est ajoutée, la page d’accueil fait l’objet d’un audit.

## Outil de transfert de contenu {#content-transfer-tool}

Consultez cette section pour en savoir plus sur les nouveautés et les mises à jour de la version 1.0.4 de l’outil de transfert de contenu.

### Nouveautés {#what-is-new-ctt}

* L’outil de transfert de contenu prend désormais en charge le magasin de données partagé S3.

### Correctifs {#ctt-bug-fixes}

* Ajout de délais d’attente supplémentaires pour que l’outil mette en œuvre les actions.

* L’interface utilisateur des versions antérieures indiquait parfois la réussite d’une extraction, même si le journal contenait des erreurs.

## Outils de refactorisation du code {#code-refactoring-tools}

Consultez cette section pour découvrir les nouveautés et les mises à jour des outils de refactorisation du code.

### Nouveautés {#what-is-new-refactoring}

* Publication du module AIO-CLI afin d’unifier les outils de refactorisation du code pour permettre aux développeurs d’appeler et d’exécuter ces outils à partir d’un seul emplacement. Voir [Ressource Git : aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) pour plus d’informations.

* Le convertisseur du Dispatcher AEM a été étendu pour prendre en charge les conversions des configurations On-Premise et Adobe Managed Services du Dispatcher dans celles compatibles avec AEM as a Cloud Service. Consultez [Ressource Git : AEM Cloud Service Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter) pour plus d’informations.

* Réécriture du convertisseur du Dispatcher dans ` node.js ` et intégration avec le module AIO-CLI.
