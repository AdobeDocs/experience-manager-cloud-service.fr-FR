---
title: Notes de mise à jour de la version 2020.11.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour d’[!DNL Adobe Experience Manager] as a Cloud Service version 2020.11.0.
exl-id: 8066c0fb-c2f5-4625-9448-b0c74ff4e192
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1223'
ht-degree: 91%

---

# Notes de mise à jour pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante présente les notes de mise à jour générales d’[!DNL Experience Manager] as a Cloud Service.

## Date de publication {#release-date}

La date de publication d’[!DNL Adobe Experience Manager] as a Cloud Service version 2020.11.0 est le 2 décembre 2020.
La version suivante (2020.12.0) sera publiée le 17 décembre 2020.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### Nouveautés d’[!DNL Sites]  {#what-is-new-sites}

* **[Lancement de la gestion de hiérarchie](/help/sites-cloud/authoring/launches/managing-pages.md) et de la fonction [Future Timewarp](/help/sites-cloud/authoring/launches/preview.md)** : nouvelle interface utilisateur pour ajouter ou supprimer des pages lors d’un lancement. De plus, le site de navigation affiche l’état futur des lancements grâce à Timewarp.

* **[Modèles et éditeur étendus de fragments de contenu](/help/assets/content-fragments/content-fragments-models.md)** : affichage de nouvelles options de validation des entrées sur différents types de données, type de données d’énumération amélioré avec de nouvelles visualisations de formulaires et le nom du modèle de fragment de contenu. Ces éléments peuvent faire l’objet de recherches dans l’interface utilisateur d’Assets.

* **Tri des pages de la Live Copy disponibles pour déploiement** : nouvelle option pour trier les pages de la Live Copy disponibles pour déploiement à l’aide des propriétés [!UICONTROL Nom], [!UICONTROL Date de dernière modification] et [!UICONTROL Date du dernier déploiement]. La [!UICONTROL Date du dernier déploiement] pour une page est une nouvelle propriété introduite.

## [!DNL Adobe Experience Manager Assets] as a Cloud Service {#assets}

### Nouveautés d’[!DNL Assets] et [!DNL Dynamic Media] {#what-is-new-assets}

* **Ingestion de ressources en bloc** : proposez aux clients un service d’ingestion évolutif et natif dans le cloud qui utilise [!DNL Experience Manager] une architecture as a Cloud Service, y compris des microservices de ressources. Les cas d’utilisation essentiels incluent l’ingestion à l’échelle voulue avec la surveillance, les rapports et la planification, tout en permettant le transfert initial des ressources vers les entrepôts de données dans le cloud à l’aide d’outils de téléchargement courants. Voir [Outil d’ingestion de ressources en masse](/help/assets/add-assets.md#asset-bulk-ingestor).

  Cet outil est destiné aux administrateurs système, consultants ou partenaires concernés par l’implémentation. Cette fonction permet l’ingestion à grande échelle et est idéalement adaptée pour une ingestion initiale ou occasionnellement volumineuse. Pour les tâches d’ingestion de volume plus modeste, utilisez l’[[!DNL Experience Manager] application de bureau](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html?lang=fr) ou [effectuez un chargement à l’aide de l’interface utilisateur d’Assets](/help/assets/add-assets.md#upload-assets).

  ![Configuration de l’importateur en masse](/help/assets/assets/bulk-import-config-low-res.png)

* Les utilisateurs peuvent désormais trier les ressources numériques à l’aide des vues Carte et Colonne.

  ![tri des ressources](/help/assets/assets/asset-sort-options.png)

* Les améliorations suivantes ont été apportées à l’accessibilité d’[!DNL Experience Manager Assets] grâce à cette version. Pour plus d’informations, voir [Fonctionnalités d’accessibilité d’ [!DNL Assets]](/help/assets/accessibility.md).

   * Lorsque vous naviguez dans la chronologie à l’aide du clavier, la touche Échap permet de réduire l’option Tout afficher sans perdre la sélection.
   * Lorsque vous naviguez à l’aide de la touche de tabulation du clavier, après avoir supprimé la dernière des balises ajoutées, le champ de balise conserve la sélection.
   * Les composants d’[!DNL Experience Manager] contiennent désormais les informations appropriées concernant le nom, le rôle et la valeur à utiliser par les lecteurs d’écran.
   * Après suppression des zones de liste déroulante Type/Taille, Lien et Langue, ou de la zone d’édition Texte, la sélection du clavier revient aux éléments suivants ou précédents de l’interface utilisateur ou à un élément plus pertinent de l’interface utilisateur.
   * Lorsque vous placez le pointeur de la souris sur des options, des conseils concernant par exemple les fonctions Sélectionner et Télécharger s’affichent. Il est possible que les utilisateurs de la loupe ne voient pas les miniatures des fichiers en raison de ces conseils. Il est désormais possible de conserver la sélection après avoir supprimé l’option à l’aide de la touche `Escape`.
   * Lors du choix d’une cellule dans la grille de la page, la sélection se déplace vers la barre d’action affichée à l’écran.
   * Les utilisateurs peuvent faire la différence entre un texte normal et un lien, car des indices visuels (soulignement et icône en forme de chevron) sont affichés pour les liens vers les solutions de la page d’accueil d’[!DNL Experience Manager].

* **Paramètres prédéfinis de lot dans Dynamic Media** : vous pouvez désormais automatiser la création et l’organisation de différentes ressources dans une visionneuse d’images ou une visionneuse à 360° lorsque vous chargez des fichiers de ressources dans un dossier, individuellement ou par une ingestion en masse.

  Voir [À propos des paramètres prédéfinis de lot](/help/assets/dynamic-media/batch-set-presets-dm.md).

* Les améliorations d’accessibilité suivantes sont désormais disponibles dans [!DNL Dynamic Media] :

   * Les lecteurs d’écran (JAWS, Narrateur) indiquent le nom, le rôle et le statut des éléments de menu dans l’option de menu Taille intégrée.
   * Il est possible pour les utilisateurs d’accéder à la boîte de dialogue Envoi d’un lien par courrier électronique à l’aide de la touche `Tab`.
   * Le workflow permettant de créer des profils de codage vidéo est plus convivial grâce à l’amélioration du lecteur d’écran.
   * Lorsque vous naviguez à l’aide de la touche `Tab`, la sélection se déplace vers les éléments d’interface utilisateur appropriés dans le workflow pour créer une vidéo interactive.
   * Les pages Publier, Modifier ressource, Modifier les recadrages intelligents et Éditeur de visionneuse d’images ont été améliorées pour répondre aux références standard du web. Les utilisateurs de la technologie d’assistance (AT) peuvent désormais naviguer facilement sur ces pages et agir sur celles-ci, comme recadrer des images.
   * Les lecteurs sont améliorés pour permettre aux utilisateurs de naviguer à l’aide du clavier.
   * Les utilisateurs du clavier et du lecteur d’écran peuvent employer la fonctionnalité de recadrage.
   * Les utilisateurs du clavier peuvent mieux gérer les zones réactives.

  Voir [Accessibilité dans [!DNL Dynamic Media]](/help/assets/dynamic-media/accessibility-dm.md).

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nouveautés {#what-is-new-commerce}

* Publication CIF site de référence Venia - 2020.11.05 incluant la dernière version des CIF composants principaux v1.5.0. Pour plus d’informations, voir [CIF site de référence Venia](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.10.27) .

* Publication CIF composants principaux v1.5.0. Pour plus d’informations, voir [CIF Core Components](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.5.0) .

### Correctifs {#bug-fixes-commerce}

* La configuration du client GraphQL n’était pas lue correctement lorsque la configuration n’était pas spécifiée directement dans la configuration de l’autorité de certification Sling, mais dans l’une des configurations parentes. Ce problème a été résolu.

## Cloud Manager {#cloud-manager}

### Date de publication {#release-date-cm}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2020.11.0 est le 12 novembre 2020.

### Nouveautés d’[!DNL Cloud Manager]  {#what-is-new-cm}

* Une nouvelle option de menu **Connexion locale** est désormais disponible pour les utilisateurs à partir des options du menu Environnement dans la carte **Environnements** et les pages de résumé des **environnements**.
Pour plus d’informations, consultez [Gestion des environnements](/help/implementing/cloud-manager/manage-environments.md#login-locally).

* L’onglet **Apprendre** de Cloud Manager est actualisé avec de nouvelles images dans l’interface utilisateur.

### Correctifs {#bug-fixes-cloud-manager}

* Le chargement des dépendances effectué avant l’exécution du build nécessitait le téléchargement d’un module externe Maven.
* Le lien du pied de page de Cloud Manager destiné à sélectionner une langue dirige désormais vers l’emplacement approprié.
* Parfois, pendant la numérisation du code, le processus SonarQube ne démarrait pas. Désormais, il sera automatiquement détecté et un redémarrage sera tenté.
* Tous les pipelines de production existants sont automatiquement activés avec l’étape d’audit de l’expérience.

## Adobe Experience Manager as a Cloud Service Foundation {#cloud-service-foundation}

### Workflows {#workflows}

* La prise en charge de la recherche des instances de workflow a été ajoutée en fonction du titre du workflow, du modèle de workflow, du statut, de l’initiateur, du chemin d’accès à la charge utile et de la date de début. Voir [Instances des workflows de recherche](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/workflows-administering.html?lang=fr).

### Synchronisation des données utilisateur du niveau Publication {#user-sync}

* Les données de l’utilisateur, y compris les attributs de profil et les adhésions aux groupes, peuvent être conservées dans la couche de publication. Pour en savoir plus sur cette fonctionnalité, consultez la [documentation relative à l’abonnement, à la connexion et au profil d’utilisateur](/help/sites-cloud/authoring/personalization/user-and-group-sync-for-publish-tier.md).

### Analyseurs de build de SDK {#analyzers}

Le plug-in Build Analyzer Maven du SDK AEM as a Cloud Service détecte des problèmes dans un projet Maven, y compris les dépendances manquantes. Il permet aux développeurs d’identifier des problèmes au cours du développement local, bien avant leur déploiement dans les environnements Cloud avec Cloud Manager. Pour plus d’informations, voir la documentation [ici](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=fr#developing) et [ici](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=fr#building-for-the-sdk).

### Autres {#others-foundation}

Nouvelle vérification [&quot;httpd -t&quot; de la syntaxe ](/help/implementing/dispatcher/disp-overview.md#local-validation) pour la configuration Apache et Dispatcher exécutée pendant la génération Cloud Manager, qui peut également être exécutée à l’aide des outils Dispatcher du SDK AEM as a Cloud Service.

## Outil de transfert de contenu {#content-transfer-tool}

Consultez cette section pour découvrir les nouveautés et les mises à jour de l’[outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=fr) version 1.1.12.

### Nouveautés {#what-is-new-ctt}

* Amélioration de l’expérience utilisateur des journaux. Horodatages ajoutés aux journaux d’extraction et d’importation. Message ajouté pour indiquer si les journaux sont vides.

### Correctifs {#ctt-bug-fixes}

* L’outil de transfert de contenu ignorait les fichiers de contenu si le jeu de migration contenait des chemins dont les noms de fichiers étaient partiellement similaires. Ce problème a été résolu.

## Analyseur des bonnes pratiques {#best-practices-analyzer}

### Date de publication {#release-date-bpa}

La date de publication de l’analyseur de bonnes pratiques est le 13 novembre 2020.

### Nouveautés d’[!DNL Best Practices Analyzer]  {#what-is-new-bpa}

* Cloud Readiness Analyzer est désormais appelé Analyseur de bonnes pratiques (Best Practices Analyzer, BPA). L’analyseur de bonnes pratiques réalise une évaluation des bonnes pratiques de votre mise en œuvre d’AEM en cours et permet d’évaluer plus efficacement la capacité de passer d’une instance AEM existante à AEM as a Cloud Service.

* Un nouveau détecteur a été ajouté pour repérer l’utilisation de `java.io.InputStream`, ce qui peut provoquer des problèmes s’il est utilisé dans AEM as a Cloud Service.

### Correctifs {#bpa-bug-fixes}

* Le bogue qui provoquait des positifs liés au composant *textfield foundation* a été résolu.
