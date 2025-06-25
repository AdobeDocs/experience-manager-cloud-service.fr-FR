---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: d3cdc3d69c0002c5b124150050f905123457331c
workflow-type: ht
source-wordcount: '380'
ht-degree: 100%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 21193 {#21193}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 21193, publiée le 10 juin 2025. La version de maintenance précédente était la version 21005.

L’activation des fonctionnalités de la version 2025.6.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-21193}

* ASSETS-51245 : amélioration des performances pour les listes de dossiers volumineuses dans l’interface d’utilisation tactile.
* ASSETS-51686 : améliorations apportées aux traitements d’opérations en masse, notamment une annulation de traitement plus facile, une journalisation améliorée et des téléchargements d’audit pour des résultats volumineux.
* CQ-4360131 : amélioration de la réponse d’erreur pour les points d’entrée OpenAPI, ce qui permet aux clients API de recevoir des informations d’erreur structurées correctes.

### Problèmes résolus {#fixed-issues-21193}

* ASSETS-41007 : les ressources supprimées peuvent rester visibles dans Content Hub.
* ASSETS-50994 : AemRequestEventFilter entraînant un conflit de threads Jetty excessif.
* ASSETS-50155 : déclenchement d’événements de modification de métadonnées en double.
* ASSETS-50716 : le tri par titre dans la vue Liste Assets ne fonctionne pas comme prévu.
* ASSETS-50820 : assurez-vous que les requêtes non valides envoyées à l’API des relations des ressources sont correctement rejetées avec une erreur 400.
* ASSETS-50562 : l’API de chargement de ressources doit créer une version par défaut en cas de conflit de noms.
* ASSETS-50992 : le point d’entrée initioUpload.json de l’API Assets doit renvoyer le type de contenu « application/json ».
* ASSETS-51322 : suppression et expiration automatiques des barricades asynchrones qui persistent indéfiniment après l’échec d’un traitement.
* ASSETS-51809 : l’éditeur CSV n’a pas affiché les modifications récemment enregistrées en raison de la mise en cache du navigateur.
* SITES-31678 : les fragments d’expérience avec des références contextuelles n’ont pas résolu la racine de langue correcte dans l’API de publication des fragments d’expérience.


### Problèmes connus {#known-issues-21193}

Aucun.

### Fonctionnalités et API obsolètes {#deprecated-21193}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-21193}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 2 vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-21193}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.80.0 | [API Oak 1.80.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.80.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | 2.29.0 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
