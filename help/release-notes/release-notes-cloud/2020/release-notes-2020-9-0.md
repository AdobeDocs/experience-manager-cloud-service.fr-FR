---
title: Notes de mise à jour de la version 2020.9.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour d’[!DNL Adobe Experience Manager] as a Cloud Service version 2020.9.0.
exl-id: 2332512f-8c52-4569-a006-faa36a7670a1
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 94%

---

# Notes de mise à jour pour [!DNL Adobe Experience Manager] as a Cloud Service 2020.9.0 {#release-notes}

La section suivante présente les notes de mise à jour générales d’[!DNL Experience Manager] as a Cloud Service version 2020.9.0.

## Date de publication {#release-date}

La date de publication d’[!DNL Adobe Experience Manager] as a Cloud Service version 2020.9.0 est le 24 septembre 2020.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### Nouveautés de [!DNL Sites]  {#what-is-new-sites}

* Le SDK JavaScript de l’éditeur d’application sur une seule page [&#x200B; est désormais Open Source &#x200B;](/help/implementing/developing/hybrid/reference-materials.md).

## [!DNL Adobe Experience Manager Assets] as a Cloud Service {#assets}

### Nouveautés d’[!DNL Assets]  {#what-is-new-assets}

* L’application de filigrane aux fichiers d’images est prise en charge pour les rendus générés avec les microservices de ressources. Elle peut être configurée en tant que profil de traitement et utilise un fichier PNG en tant que filigrane. Voir [Application d’un filigrane à vos ressources](/help/assets/watermark-assets.md).

* Améliorations dans [!DNL Dynamic Media]

   * Publication sélective : il est désormais possible pour une équipe marketing d’accéder à des images de recadrage intelligent [!DNL Dynamic Media] et à des rendus dynamiques synchronisés avec [!DNL Dynamic Media] afin de pouvoir créer des supports promotionnels, le tout sans avoir à publier ces ressources sur [!DNL Dynamic Media] pour une diffusion globale. La publication [!DNL Experience Manager] et [!DNL Dynamic Media] est découplée et peut se produire séparément à cette fin. Voir [Publication sélective](/help/assets/dynamic-media/selective-publishing.md).
   * Les administrateurs peuvent désormais réinitialiser le mot de passe de [!DNL Dynamic Media] Cloud Service reçu lors de l’approvisionnement. La réinitialisation peut être effectuée dans l’interface utilisateur de [!DNL Experience Manager], sans qu’il soit nécessaire d’utiliser l’application de bureau [!DNL Dynamic Media Classic].

* Pour en savoir plus sur les améliorations suivantes, voir [Nouveautés de Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/whats-new.html?lang=fr).

   * Aperçu PDF amélioré avec l’intégration du SDK Adobe Document Cloud View.
   * Fonction de téléchargement en un clic.
   * Nouvelles configurations d’administration pour l’expérience de téléchargement.

<!--
### Bugs Fixed {#bugs-fixed-assets}

TBD: list of Assets aaCS bugs that are fixed.
-->

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nouveautés {#what-is-new-commerce}

* Publication CIF composants principaux v1.3.0. Pour plus d’informations, voir [CIF Core Components](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.3.0) .

* La fonctionnalité d’aperçu avec produit/catégorie pour les modèles de produit et de catégorie est désormais disponible. Elle permet aux utilisateurs métier/spécialistes du marketing dans AEM d’afficher les modèles de produit/catégorie avec des données réelles.

* Page de propriétés ajoutée aux produits et aux catégories pour permettre aux utilisateurs métier d’afficher les détails associés au SKU/à l’ID de catégorie de produit.

* Fonction de tri ajoutée à la console de produit pour permettre le tri des produits/catégories par nom ou par attribut de prix.

* Fonctionnalité de recherche de produit ajoutée à la console de produit.

### Correctifs {#bug-fixes-commerce}

* Les configurations de Commerce Cloud ne respectaient pas l’héritage. Ce problème a été corrigé afin de garantir que la configuration hérite des valeurs.

## Cloud Manager {#cloud-manager}

### Date de publication {#release-date-cm}

La date de publication de [!UICONTROL Cloud Manager] version 2020.9.0 est le 3 septembre 2020.

### Nouveautés {#what-is-new-cloud-manager}

* La fonction Audit de contenu se nomme désormais Contrôle de l’expérience.
* Le processus de création a été divisé en trois commandes Maven distinctes.
* Si le clonage du référentiel Git échoue, il est tenté à nouveau jusqu’à trois fois.

### Correctifs {#bug-fixes-cm}

* L’onglet Audit de contenu affichait incorrectement l’URL de base à l’aide du domaine de création et non du domaine de publication.

## Cloud Readiness Analyzer {#cloud-readiness-analyzer}

Consultez cette section pour en savoir plus sur les nouveautés et les mises à jour de la version 1.1.0 de Cloud Readiness Analyzer.

### Nouveautés {#what-is-new-cra}

* Cloud Readiness Analyzer (CRA) dispose d’une console d’état de début qui affiche un bouton **Générer un rapport** explicite sur lequel l’utilisateur peut cliquer pour exécuter CRA.

* L’interface utilisateur de CRA affiche la progression pendant son exécution. Elle affiche les éléments en cours d’analyse et les résultats trouvés pendant l’exécution.

* Le rapport de CRA présente un résumé et le nombre de résultats dans un format tabulaire organisé selon le type de résultat et le niveau d’importance. En cliquant sur le numéro de ce résultat, vous accédez automatiquement à l’emplacement de ce résultat dans le rapport.

### Correctifs {#cra-bug-fixes}

* Dans certains cas, le rapport de CRA n’était pas mis à jour après l’exécution forcée d’une actualisation. Ce problème a été corrigé dans cette version.

## Outil de transfert de contenu {#content-transfer-tool}

Consultez cette section pour découvrir les nouveautés et les mises à jour de l’outil de transfert de contenu version 1.1.10.

### Nouveautés {#what-is-new-ctt}

* L’outil de transfert de contenu (CTT) prend en charge le magasin de données Azure Blob Store.

* L’interface utilisateur de CTT dispose d’une fonction de rechargement automatique qui recharge la page d’aperçu toutes les 30 secondes.

* Bouton ajouté à l’interface utilisateur de CTT pour récupérer facilement le *jeton d’accès*.

* Ajout d’un message de validation descriptif pour l’*URL* et le *nom du jeu de migration*.

## Outils de refactorisation du code {#code-refactoring}

Consultez cette section pour découvrir les nouveautés et les mises à jour des outils de refactorisation du code.

### Nouveautés {#what-is-new-refactoring}

* Le plug-in AIO-CLI prend en charge Repository Modernizer et permet aux utilisateurs d’exécuter l’outil.

  Voir [Ressource Git : aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) pour plus d’informations.

* L’utilitaire Repository Modernizer peut être utilisé pour restructurer des packages de projets existants en packages compatibles avec la structure de projet définie pour AEM as a Cloud Service.

  Voir [Ressource Git : Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) pour plus d’informations.
