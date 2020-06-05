---
title: Problèmes connus
description: Notes de mise à jour spécifiques aux problèmes connus avec Adobe Experience Manager as a Cloud Service
translation-type: tm+mt
source-git-commit: 165dc4af656ce1bc431d2f921775ebda4cf4de9f
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 96%

---


# Problèmes connus {#known-issues}

Cet article répertorie les problèmes connus de l’offre Adobe Experience Manager as a Cloud Service. La liste est révisée et mise à jour à chaque version d’Experience Manager.

Pour en savoir plus sur les problèmes connus ci-dessous, [contactez l’assistance](https://helpx.adobe.com/fr/support/experience-manager.html).

<!-- 
## Platform {#platform}

## Sites {#sites}
-->

## Assets {#assets}

<!-- Jira label: assets-cloud-known-issues -->

Voici quelques problèmes connus :

* **Schéma de métadonnées** : le widget d’évaluation des ressources entraînait une erreur de compilation JSP. Il a été supprimé du schéma de métadonnées. <!-- CQ-4282865, CQ-4284633 -->

### Fonctionnalités Assets à venir {#upcoming-assets-capabilities}

Quelques fonctionnalités des ressources Adobe Experience Manager qui dépendent des fonctionnalités de base, qui ne sont pas encore disponibles dans Experience Manager en tant qu’architecture de déploiement Cloud Service, devraient être activées ultérieurement :

* Ces fonctionnalités ne sont pas activées à ce stade en raison d’une dépendance aux API de framework d’intégration de commerce :
   * Modèles de workflow de séance photo.
   * Onglet d’informations sur les produits de l’interface utilisateur des propriétés des ressources non renseigné
* Ces fonctionnalités ne sont pas activées à ce stade en raison d’une dépendance vis-à-vis de l’intégration d’InDesign Server :
   * Modèles de ressources et catalogues de ressources
   * prévisualisation de plusieurs pages de fichiers Adobe InDesign.

>[!MORELIKETHIS]
>
>* [Changements majeurs dans AEM](aem-cloud-changes.md)
>* [Fonctionnalités obsolètes et supprimées](deprecated-removed-features.md)
>* [Notes de mise à jour](home.md)

