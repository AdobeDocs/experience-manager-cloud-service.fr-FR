---
title: Notes de mise à jour actuelles de  [!DNL Adobe Experience Manager] en tant que Cloud Service.
description: Notes de mise à jour actuelles de  [!DNL Adobe Experience Manager] en tant que Cloud Service.
translation-type: tm+mt
source-git-commit: 89f7e60205efc275bbeb97246ccc3add28810cfa
workflow-type: tm+mt
source-wordcount: '1329'
ht-degree: 10%

---


# Notes de mise à jour d’[!DNL Adobe Experience Manager] as a Cloud Service  {#release-notes}

La section suivante décrit les Notes de mise à jour générales de [!DNL Experience Manager] en tant que Cloud Service.

## Date de publication {#release-date}

La date de publication de [!DNL Adobe Experience Manager] en tant que Cloud Service 2020.11.0 est le 1er décembre 2020.
La version suivante (2020.12.0) sera publiée le 17 décembre 2020.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service{#sites}

### Nouveautés d’[!DNL Sites] {#what-is-new-sites}

* **[Lance la gestion](/help/sites-cloud/authoring/launches/managing-pages.md)  hiérarchique et le  [futur calendrier](/help/sites-cloud/authoring/launches/preview.md)** : Nouvelle interface utilisateur permettant d’ajouter ou de supprimer des pages au cours d’un lancement, et le site de navigation avec Timewarp affiche l’état futur des lancements.

* **[Modèles et éditeur](/help/assets/content-fragments/content-fragments-models.md)** de fragments de contenu étendu : De nouvelles options pour la validation des entrées sur divers types de données, un type de données de Énumération amélioré avec de nouvelles visualisations de formulaire et le nom du modèle Fragment de contenu s’affichent et peuvent faire l’objet de recherches dans l’interface utilisateur Ressources.

* **Rendre un site installable** : Nouvelles propriétés du site pour configurer les fonctionnalités du Progressive Web Application (PWA), qui rendront un site installable et disponible hors ligne en option. Les fonctionnalités nécessitent des composants principaux.

* **[Composants principaux 2.12.0](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)** : aem en tant que Cloud Service bénéficie des mises à jour automatiques de la dernière version des composants principaux. La version 2.12.0 comprend les dernières améliorations apportées par la communauté, telles que [un nouveau gestionnaire de formulaires POST ;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/forms/form-container.html#post-data) la possibilité d’inclure des balises CSS, JavaScript et [de métadonnées personnalisées par le biais d’une configuration contextuelle ;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/including-clientlibs.html#context-aware-loading) et un utilitaire [`DataLayerBuilder`](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/integrations.html#enabling-custom-components) pour simplifier l’intégration de la couche de données Adobe dans les composants personnalisés. Voir la [liste des modifications](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.12.0) dans la version 2.12.0.

## [!DNL Adobe Experience Manager Assets] as a Cloud Service{#assets}

### Nouveautés de [!DNL Assets] et [!DNL Dynamic Media] {#what-is-new-assets}

* **Importation** de ressources en vrac : Offrez aux clients un service d’assimilation évolutif et natif au cloud qui tire parti  [!DNL Experience Manager] en tant qu’architecture Cloud Service, y compris les microservices de ressources. Les cas d’utilisation clés incluent l’assimilation à l’échelle avec la surveillance, le rapports et la planification, tout en permettant le transfert initial des ressources vers les entrepôts de données en nuage à l’aide d’outils de téléchargement de cloud courants. Voir [outil d&#39;importation en vrac](/help/assets/add-assets.md#bulk-ingestion-tool).
Cet outil est destiné aux administrateurs système, aux consultants ou aux partenaires d’implémentation. Cette fonction permet l&#39;ingestion à grande échelle et est idéalement utilisée lors de l&#39;ingestion initiale ou parfois d&#39;une ingestion importante. Pour les tâches d’assimilation plus petites, utilisez l’[[!DNL Experience Manager] application de bureau](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html?lang=fr) ou [téléchargez à l’aide de l’interface utilisateur Ressources](/help/assets/add-assets.md#upload-assets).

   ![Configuration de l&#39;importateur en vrac](/help/assets/assets/bulk-import-config-low-res.png)

* Les utilisateurs peuvent trier les ressources numériques dans les vues Carte et Colonne.

   ![trier les fichiers](/help/assets/assets/asset-sort-options.png)

* Les améliorations suivantes ont été apportées à l’accessibilité dans [Experience Manager Assets] de cette version. Pour plus d&#39;informations, voir [fonctionnalités d&#39;accessibilité dans [!DNL Assets]](/help/assets/accessibility.md).

   * Lorsque vous naviguez dans le plan de montage chronologique à l’aide du clavier, la touche Echap peut réduire l’option Afficher tout sans perdre la cible d’action.
   * Lors de la navigation à l’aide de la touche de tabulation du clavier, après avoir supprimé la dernière balise des balises ajoutées, le champ de balise conserve la cible d’action.
   * [!DNL Experience Manager] les composants contiennent désormais les informations appropriées concernant le nom, le rôle et la valeur à utiliser par les lecteurs d’écran.
   * Après avoir supprimé la zone de liste déroulante Type/Taille, la zone de liste déroulante Lien, la zone de liste déroulante Langue ou la zone d’édition Texte, la sélection du clavier revient aux éléments suivants ou précédents de l’interface utilisateur ou à un élément d’interface utilisateur plus pertinent.
   * Lorsque vous placez le pointeur de la souris sur des options, des conseils tels que Sélectionner et Télécharger s’affichent. Les utilisateurs qui utilisent une loupe d’écran peuvent ne pas voir les miniatures de fichier en raison de ces conseils. Désormais, il est possible de conserver la cible d’action, après avoir supprimé l’option à l’aide de la touche `Escape`.
   * Lors de la sélection d’une cellule de grille dans la grille présente dans la page, la sélection se déplace vers la barre d’actions qui s’affiche à l’écran.
   * Les utilisateurs visuels peuvent faire la différence entre un texte normal et un lien, car des indices visuels (soulignement et icône en chevron) sont affichés pour les liens vers toutes les solutions dans la page d&#39;accueil [!DNL Experience Manager].

* **Paramètres prédéfinis d’ensemble par lot dans le contenu multimédia** dynamique : Vous pouvez désormais automatiser la création et l’organisation de plusieurs fichiers dans une visionneuse d’images ou une visionneuse à 360° au moment où vous téléchargez des fichiers de fichiers dans un dossier, soit individuellement, soit par assimilation en masse.

   Voir [A propos des paramètres prédéfinis d’ensemble par lot](/help/assets/dynamic-media/batch-set-presets-dm.md).

* Les améliorations d’accessibilité suivantes sont désormais disponibles dans [!DNL Dynamic Media] :

   * Les lecteurs d’écran (JAWS, Narrateur) indiquent le nom, le rôle et l’état des éléments de menu dans l’option de menu Taille d’incorporation.
   * Les utilisateurs peuvent naviguer dans la boîte de dialogue de lien Courrier électronique à l’aide de la clé `Tab`.
   * Le flux de travail permettant de créer des profils de codage vidéo est plus convivial, étant donné l’amélioration du lecteur d’écran.
   * Lorsque vous naviguez à l’aide de la touche `Tab`, la cible d’action se déplace vers les éléments d’interface utilisateur appropriés dans le processus pour créer une vidéo interactive.
   * La page Publier, la page Modifier un fichier, la page Modifier les cultures dynamiques et la page Editeur de visionneuse d’images sont améliorées pour répondre aux normes Web. Les utilisateurs de la technologie d’assistance (AT) peuvent désormais naviguer facilement sur ces pages et prendre des mesures telles que le recadrage d’images.
   * Les lecteurs sont améliorés pour permettre aux utilisateurs de naviguer à l’aide du clavier.
   * Les utilisateurs du clavier et du lecteur d’écran peuvent utiliser la fonctionnalité de recadrage.
   * Les utilisateurs du clavier peuvent mieux gérer les zones réactives.

   Voir [Accessibilité dans  [!DNL Dynamic Media]](/help/assets/dynamic-media/accessibility-dm.md).

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nouveautés {#what-is-new-commerce}

* Site de référence de CIF Venia - 2020.11.05 qui comprend les derniers composants principaux de CIF version 1.5.0. Pour plus d&#39;informations, consultez [Site de référence de CIF Venia](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.10.27).

* Composants principaux CIF version 1.5.0. Pour plus d&#39;informations, consultez [Composants principaux CIF](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.5.0).

### Correctifs {#bug-fixes-commerce}

* La configuration du client GraphQL n&#39;était pas lue correctement lorsque la configuration n&#39;était pas spécifiée directement dans la configuration de l&#39;autorité de certification Sling, mais dans l&#39;une des configurations parentes. Ce problème a été résolu.



## Cloud Manager {#cloud-manager}

### Date de publication {#release-date-cm}

La date de publication de Cloud Manager en tant que Cloud Service 2020.11.0 est le 12 novembre 2020.

### Nouveautés d’[!DNL Cloud Manager] {#what-is-new-cm}

* Une nouvelle option de menu **Connexion locale** est désormais disponible pour les utilisateurs à partir des options du menu environnement sur les pages de résumé **Environnements** et **Environnements**.
Pour plus d’informations, consultez [Gestion des environnements](/help/implementing/cloud-manager/manage-environments.md##login-locally).

* L’onglet **Apprendre** de Cloud Manager a été actualisé avec de nouvelles images dans l’interface utilisateur.

### Correctifs {#bug-fixes-cloud-manager}

* Le chargement des dépendances effectué avant l’exécution du build nécessitait le téléchargement d’un module externe Maven.
* Le lien du pied de page de Cloud Manager destiné à sélectionner une langue dirige désormais vers l’emplacement approprié.
* Parfois, pendant la numérisation du code, le processus SonarQube ne démarrait pas. Désormais, il sera automatiquement détecté et un redémarrage sera tenté.
* Tous les pipelines de production existants seront automatiquement activés avec l’étape Audit d’expérience.

## Adobe Experience Manager as a Cloud Service Foundation {#cloud-service-foundation}

### Workflows {#workflows}

* La prise en charge de la recherche des instances de flux de travail a été ajoutée en fonction du titre du flux de travail, du modèle de flux de travail, de l’état, de l’initiateur, du chemin d’accès à la charge et de la date de Début. Voir [Instances de flux de travaux de recherche](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/sites/administering/workflows-administering.html).

### Synchronisation utilisateur {#user-sync}

* Les données utilisateur, y compris les attributs de profil et les adhésions au groupe, peuvent être conservées sur la couche de publication. Pour en savoir plus sur cette fonctionnalité, consultez la [documentation sur l&#39;abonnement, la connexion et le Profil d&#39;utilisateur](/help/sites-cloud/authoring/personalization/user-and-group-sync-for-publish-tier.md).

### Analyseurs {#analyzers}

L’AEM en tant que module externe expert de création de SDK Cloud Service détecte des problèmes dans un projet expert, y compris les dépendances manquantes. Il permet aux développeurs de découvrir des problèmes au cours du développement local, bien avant leur déploiement dans les environnements Cloud avec Cloud Manager. Pour plus d’informations, voir la documentation [ici](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=en#developing) et [ici](https://experienceleague.corp.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en#building-for-the-sdk).

## Outil de transfert de contenu {#content-transfer-tool}

Suivez cette section pour en savoir plus sur les nouveautés et les mises à jour de [Outil de transfert de contenu](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html) Version v1.1.12.

### Nouveautés {#what-is-new-ctt}

* Amélioration de l’expérience utilisateur des journaux. Horodatages ajoutés aux journaux d&#39;Extraction et d&#39;importation. Message ajouté pour indiquer si les journaux sont vides.

### Correctifs {#ctt-bug-fixes}

* L’outil de transfert de contenu ignorait les fichiers de contenu si le jeu de migration contenait des chemins dont les noms de fichier étaient partiellement similaires. Ce problème a été résolu.

## Analyseur des meilleures pratiques {#best-practices-analyzer}

### Date de publication {#release-date-bpa}

La date de publication de l’analyseur des meilleures pratiques est le 13 novembre 2020.

### Nouveautés d’[!DNL Best Practices Analyzer] {#what-is-new-bpa}

* Cloud Readiness Analyzer est désormais Best Practices Analyzer (BPA). BPA fournit une évaluation des meilleures pratiques de votre mise en oeuvre AEM en cours et aide à évaluer la capacité de passer d’une instance AEM existante à l’AEM en tant que Cloud Service.

* Un nouveau détecteur a été ajouté pour détecter l&#39;utilisation de `java.io.InputStream`, ce qui peut causer des problèmes s&#39;il est utilisé en AEM comme Cloud Service.

### Correctifs {#bpa-bug-fixes}

* Nous avons corrigé un bogue qui provoquait les éléments positifs liés au composant *textfield foundation*.
