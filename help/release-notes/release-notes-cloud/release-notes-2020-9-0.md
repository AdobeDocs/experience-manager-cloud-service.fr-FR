---
title: Notes de mise à jour de la version 2020.9.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour d’[!DNL Adobe Experience Manager] as a Cloud Service pour la version 2020.9.0.
translation-type: tm+mt
source-git-commit: 701d9ff3c9553c28bce0ef417487facedb22373f
workflow-type: tm+mt
source-wordcount: '726'
ht-degree: 25%

---


# Notes de mise à jour d’[!DNL Adobe Experience Manager] as a Cloud Service 2020.9.0 {#release-notes}

La section suivante décrit les Notes de mise à jour générales de [!DNL Experience Manager] en tant que Cloud Service 2020.9.0.

## Date de publication {#release-date}

La date de publication de [!DNL Adobe Experience Manager] en tant que Cloud Service 2020.9.0 est le 24 septembre 2020.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service{#sites}

### Nouveautés d’[!DNL Sites] {#what-is-new-sites}

* Le SDK JavaScript de l’éditeur d’applications d’une seule page [est désormais open source.](/help/implementing/developing/hybrid/reference-materials.md)

## [!DNL Adobe Experience Manager Assets] as a Cloud Service{#assets}

### Nouveautés d’[!DNL Assets] {#what-is-new-assets}

* Les fichiers image de filigrane sont pris en charge pour les rendus générés avec les microservices de ressources. Il peut être configuré en tant que Profil de traitement et utilise un fichier PNG en tant que filigrane. Voir [filigrane de vos ressources](/help/assets/watermark-assets.md).

* Améliorations apportées à [!DNL Dynamic Media]

   * Publication sélective : il est désormais possible pour une équipe marketing d’accéder à [!DNL Dynamic Media] des images de recadrage intelligent et des rendus dynamiques synchronisés avec [!DNL Dynamic Media] afin de pouvoir créer des supports promotionnels, sans avoir à publier ces ressources dans [!DNL Dynamic Media] pour une diffusion globale. [!DNL Experience Manager] et  [!DNL Dynamic Media] la publication est découplée et peut se produire séparément pour y parvenir. Voir [publication sélective](/help/assets/dynamic-media/selective-publishing.md).
   * Les administrateurs peuvent désormais réinitialiser le [!DNL Dynamic Media] mot de passe du Cloud Service reçu lors de la mise en service. La réinitialisation peut être effectuée dans l&#39;[!DNL Experience Manager] interface utilisateur, sans qu&#39;il soit nécessaire d&#39;utiliser l&#39;application de bureau [!DNL Dynamic Media Classic].

* Pour en savoir plus sur les améliorations suivantes, voir [les nouveautés de Brand Portal](https://docs.adobe.com/content/help/fr-FR/experience-manager-brand-portal/using/introduction/whats-new.html).

   * Prévisualisation PDF améliorée avec l’intégration du SDK de Vue Adobe Document Cloud.
   * Fonction de téléchargement en un clic.
   * Nouvelles configurations d’administration pour l’expérience de téléchargement.

<!--
### Bugs Fixed {#bugs-fixed-assets}

TBD: list of Assets aaCS bugs that are fixed.
-->

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nouveautés {#what-is-new-commerce}

* Composants principaux CIF version 1.3.0. Pour plus d&#39;informations, consultez [Composants principaux CIF](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.3.0).

* La fonctionnalité de prévisualisation avec produit/catégorie pour les modèles de produit et de catégorie est désormais disponible. Cela permet aux utilisateurs/marketeurs d’entreprise en AEM de vue des modèles de produit/catégorie avec des données réelles.

* Page de propriétés ajoutée aux produits et catégories pour permettre aux utilisateurs professionnels d’accéder aux détails de vue associés au SKU/ID de catégorie du produit.

* Fonction de tri ajoutée à la console de produits pour permettre le tri des produits/catégories par nom ou par attribut de prix.

* La fonctionnalité de recherche de produits a été ajoutée à la console de produits.

### Correctifs {#bug-fixes-commerce}

* Les configurations de Commerce Cloud ne respectaient pas l&#39;héritage. Ce problème a été corrigé afin de garantir que la configuration hérite des valeurs.

## Cloud Manager {#cloud-manager}

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

* L&#39;analyseur de l&#39;état de préparation du cloud (CRA) dispose d&#39;une console d&#39;état de début qui affiche un bouton **Générer un rapport** explicite sur lequel l&#39;utilisateur doit cliquer pour exécuter l&#39;ARC.

* L&#39;interface utilisateur de l&#39;ARC affiche la progression pendant son exécution. Il affiche les éléments analysés et les résultats trouvés pendant l&#39;exécution.

* Le rapport de l&#39;ARC présente un résumé et le nombre de constatations sous forme de tableau, selon le type de conclusions et le niveau d&#39;importance. En cliquant sur le numéro de cette recherche, vous accédez automatiquement à l&#39;emplacement de cette recherche dans le rapport.

### Correctifs {#cra-bug-fixes}

* Dans certains cas, le rapport de l&#39;ARC n&#39;était pas mis à jour après avoir forcé une actualisation. Ce problème a été corrigé dans cette version.

## Outil de transfert de contenu {#content-transfer-tool}

Suivez cette section pour en savoir plus sur les nouveautés et les mises à jour de la version 1.1.10 de l’outil de transfert de contenu.

### Nouveautés {#what-is-new-ctt}

* L&#39;outil de transfert de contenu (CTT) prend en charge le magasin de données Azure Blob Store.

* L’interface utilisateur du CTT dispose d’une fonction de rechargement automatique qui recharge la page d’aperçu toutes les 30 secondes.

* Bouton ajouté à l’interface utilisateur CTT pour récupérer *Jeton d&#39;accès* facilement.

* Ajout d’un message de validation descriptif pour *URL* et *Nom du jeu de migration*.

## Outils de refactorisation du code {#code-refactoring}

Consultez cette section pour en savoir plus sur les nouveautés et les mises à jour des outils de refactorisation du code.

### Nouveautés {#what-is-new-refactoring}

* Le module externe AIO-CLI prend en charge Repository Modernizer et permet aux utilisateurs d’exécuter l’outil à l’aide du module externe.

   Pour plus d’informations, voir [Ressource Git : aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration).

* L&#39;utilitaire Repository Modernizer peut être utilisé pour restructurer des packages de projet existants en packages compatibles avec la structure de projet définie pour AEM en tant que Cloud Service.

   Reportez-vous à [Ressource Git : Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) pour plus de détails.

