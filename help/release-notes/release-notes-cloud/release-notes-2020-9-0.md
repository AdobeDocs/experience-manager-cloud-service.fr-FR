---
title: Notes de mise à jour de la version 2020.9.0 [!DNL Adobe Experience Manager] de Cloud Service.
description: '[!DNL Adobe Experience Manager] comme notes de mise à jour Cloud Service pour la version 2020.9.0.'
translation-type: tm+mt
source-git-commit: db5ca67c583166f4ecb09884a064dfc1378f436e
workflow-type: tm+mt
source-wordcount: '726'
ht-degree: 12%

---


# Release Notes for [!DNL Adobe Experience Manager] as a Cloud Service 2020.9.0 {#release-notes}

The following section outlines the general Release Notes for [!DNL Experience Manager] as a Cloud Service 2020.9.0.

## Date de publication {#release-date}

The Release Date for [!DNL Adobe Experience Manager] as a Cloud Service 2020.9.0 is September 24, 2020.

## [!DNL Adobe Experience Manager Sites]as a Cloud Service{#sites}

### What is new in [!DNL Sites] {#what-is-new-sites}

* Le SDK JavaScript de l’éditeur d’application à page unique (SPA) [est désormais open source.](/help/implementing/developing/spa/reference-materials.md)

## [!DNL Adobe Experience Manager Assets]as a Cloud Service{#assets}

### What is new in [!DNL Assets] {#what-is-new-assets}

* Les fichiers image de filigrane sont pris en charge pour les rendus générés avec les microservices de ressources. Il peut être configuré en tant que Profil de traitement et utilise un fichier PNG en tant que filigrane. Voir [filigrane de vos fichiers](/help/assets/watermark-assets.md).

* Améliorations des [!DNL Dynamic Media]

   * Publication sélective : il est désormais possible pour une équipe marketing d’accéder à des images de recadrage [!DNL Dynamic Media] intelligentes et à des rendus dynamiques synchronisés avec [!DNL Dynamic Media] afin de pouvoir créer des supports promotionnels, le tout sans avoir à publier ces ressources [!DNL Dynamic Media] pour une diffusion globale. [!DNL Experience Manager] et [!DNL Dynamic Media] la publication est découplée et peut se produire séparément pour y parvenir. Voir Publication [](/help/assets/dynamic-media/selective-publishing.md)sélective.
   * Les administrateurs peuvent désormais réinitialiser le mot de passe [!DNL Dynamic Media] du Cloud Service reçu lors de la mise en service. La réinitialisation peut être effectuée dans [!DNL Experience Manager] l’interface utilisateur, sans qu’il soit nécessaire d’utiliser l’application de [!DNL Dynamic Media Classic] bureau.

* Pour en savoir plus sur les améliorations suivantes, voir [les nouveautés de Brand Portal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/introduction/whats-new.html).

   * Prévisualisation PDF améliorée avec l’intégration du SDK de Vue Adobe Document Cloud.
   * Fonction de téléchargement en un clic.
   * Nouvelles configurations d’administration pour l’expérience de téléchargement.

<!--
### Bugs Fixed {#bugs-fixed-assets}

TBD: list of Assets aaCS bugs that are fixed.
-->

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nouveautés {#what-is-new-commerce}

* Composants principaux CIF version 1.3.0. Pour plus d&#39;informations, reportez-vous à la section Composants [principaux](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.3.0) CIF.

* La fonctionnalité de prévisualisation avec produit/catégorie pour les modèles de produit et de catégorie est désormais disponible. Cela permet aux utilisateurs/marketeurs d’entreprise en AEM de vue des modèles de produit/catégorie avec des données réelles.

* Page de propriétés ajoutée aux produits et catégories pour permettre aux utilisateurs professionnels d’accéder aux détails de vue associés au SKU/ID de catégorie du produit.

* Fonction de tri ajoutée à la console de produits pour permettre le tri des produits/catégories par nom ou par attribut de prix.

* La fonctionnalité de recherche de produits a été ajoutée à la console de produits.

### Correctifs {#bug-fixes-commerce}

* Les configurations de Commerce Cloud ne respectaient pas l&#39;héritage. Ce problème a été corrigé afin de garantir que la configuration hérite des valeurs.

## Cloud Manager {#cloud-manager}

### Date de publication {#release-date-cm}

La date de publication de [!UICONTROL Cloud Manager] version 2020.9.0 est le 3 septembre 2020.

### Nouveautés {#what-is-new-cloud-manager}

* L’audit de contenu a été renommé Audit d’expérience.
* Le processus de création a été divisé en trois commandes Maven distinctes.
* Si le référentiel Git n’est pas cloné, il sera multiplié par trois.

### Correctifs {#bug-fixes-cm}

* L’onglet Audit de contenu affichait incorrectement l’URL de base à l’aide du domaine d’auteur et non du domaine de publication.

## Cloud Readiness Analyzer {#cloud-readiness-analyzer}

Suivez cette section pour en savoir plus sur les nouveautés et les mises à jour de la version 1.1.0 de Cloud Readiness Analyzer.

### Nouveautés {#what-is-new-cra}

* L&#39;Analyseur de préparation du cloud (CRA) dispose d&#39;une console d&#39;état de début qui affiche un bouton **Générer un rapport** explicite sur lequel l&#39;utilisateur peut cliquer pour exécuter l&#39;ARC.

* L&#39;interface utilisateur de l&#39;ARC affiche la progression pendant son exécution. Il affiche les éléments analysés et les résultats trouvés pendant l&#39;exécution.

* Le rapport de l&#39;ARC présente un résumé et le nombre de constatations sous forme de tableau, selon le type de conclusions et le niveau d&#39;importance. En cliquant sur le numéro de cette recherche, vous accédez automatiquement à l&#39;emplacement de cette recherche dans le rapport.

### Correctifs {#cra-bug-fixes}

* Dans certains cas, le rapport de l&#39;ARC n&#39;était pas mis à jour après avoir forcé une actualisation. Ce problème a été corrigé dans cette version.

## Outil de transfert de contenu {#content-transfer-tool}

Suivez cette section pour en savoir plus sur les nouveautés et les mises à jour de la version 1.1.10 de l’outil de transfert de contenu.

### Nouveautés {#what-is-new-ctt}

* L&#39;outil de transfert de contenu (CTT) prend en charge le magasin de données Azure Blob Store.

* L’interface utilisateur du CTT dispose d’une fonction de rechargement automatique qui recharge la page d’aperçu toutes les 30 secondes.

* Bouton ajouté à l’interface utilisateur de CTT pour récupérer facilement le *Jeton d&#39;accès* .

* Ajout d’un message de validation descriptif pour l’ *URL* et le nom *du jeu de* migration.

## Outils de refactorisation du code {#code-refactoring}

Suivez cette section pour en savoir plus sur les nouveautés et les mises à jour des outils de refactorisation du code.

### Nouveautés {#what-is-new-refactoring}

* Le module externe AIO-CLI prend en charge Repository Modernizer et permet aux utilisateurs d’exécuter l’outil à l’aide du module externe.

   Refer to [Git Resource: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) for more details.

* L&#39;utilitaire Repository Modernizer peut être utilisé pour restructurer des packages de projet existants en packages compatibles avec la structure de projet définie pour AEM en tant que Cloud Service.

   Reportez-vous à la ressource [Git : Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) pour plus d’informations.

