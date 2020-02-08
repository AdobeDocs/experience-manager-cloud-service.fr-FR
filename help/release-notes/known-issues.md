---
title: Problèmes connus
description: Notes de mise à jour spécifiques aux problèmes connus avec Adobe Experience Manager en tant que service Cloud
translation-type: tm+mt
source-git-commit: 82dd9bd69fe994f74c7be8a571e386f0e902f6a1

---


# Problèmes connus {#known-issues}

Cet article répertorie les problèmes connus d’Adobe Experience Manager en tant qu’offre de service Cloud. La liste est révisée et mise à jour à chaque version continue d’Experience Manager.

[Contactez l’assistance](https://helpx.adobe.com/support/experience-manager.html) pour plus d’informations sur les problèmes connus.

<!-- 
## Platform {#platform}

## Sites {#sites}
-->

## Assets {#assets}

<!-- Jira label: assets-cloud-known-issues -->

Voici quelques problèmes connus :

* **Schéma** de métadonnées : Le widget d’évaluation des ressources peut entraîner une erreur de compilation JSP. Une solution consiste à supprimer le composant d’évaluation des ressources du schéma de métadonnées. <!-- CQ-4282865 -->

Certaines limitations de la fonctionnalité Ressources sont les suivantes :

* Avec AEM Assets en tant que service Cloud, la fonctionnalité Ressources connectées fonctionne lorsque les sites AEM 6.5 sont déployés sur AMS.

### Fonctionnalités des ressources à venir {#upcoming-assets-capabilities}

Quelques fonctionnalités des ressources Adobe Experience Manager qui dépendent des fonctionnalités de base, qui ne sont pas encore disponibles dans Experience Manager en tant qu’architecture de déploiement de services Cloud, devraient être activées ultérieurement :

* La publication sur le portail de marque n’est pas activée à ce stade. Vous pouvez étendre et déployer l’implémentation [d’Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/) pour les cas d’utilisation de la distribution d’actifs.
* La fonctionnalité de balisage intelligent améliorée qui utilise les services d’IA des E/S Adobe n’est pas disponible pour l’instant.
* Fonctionnalités non activées à ce stade en raison d’une dépendance aux API de Commerce Integration Framework :
   * Modèles de flux de production Photoshop.
   * L’onglet d’informations sur les produits de l’interface utilisateur des propriétés des ressources n’est pas renseigné.
* Fonctionnalités non activées à ce stade en raison d’une dépendance vis-à-vis de l’intégration d’InDesign Server :
   * Modèles de ressources et catalogues de ressources.
   * Aperçu de plusieurs pages de fichiers InDesign.

>[!MORELIKETHIS]
>
>* [Changements majeurs dans AEM](aem-cloud-changes.md)
>* [Fonctions obsolètes et supprimées](deprecated-removed-features.md)
>* [les notes de mise à jour.](home.md)

