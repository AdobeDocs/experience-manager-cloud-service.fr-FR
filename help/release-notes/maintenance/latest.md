---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 6087c41fda8f00d3606059484b0452ef5187f6ef
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 30%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## 26309 de publication {#release-26309}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 26309, rendue publique le 26 mai 2026. La version de maintenance précédente était la version 25892.

L’activation de la fonctionnalité 2026.5.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

>[!NOTE]
>
>La version 26125 a été rendue privée.

### Améliorations {#enhancements-26309}

* ASSETS-56957 : ajout de la prise en charge du chargement multipiste audio et multilégende pour les vidéos dans Dynamic Media avec OpenAPI.
* ASSETS-58563 : ajout de l’intégration d’Adobe Commerce à AEM Assets.
* ASSETS-65603 : amélioration des performances de la liste des dossiers dans l’interface utilisateur tactile en permettant la configuration d’un nombre de ressources réduit.
* ASSETS-66032 : ajout de la prise en charge avancée du proxy de réseau à l’importation en bloc Assets pour les environnements disposant d’un stockage dans le cloud limité par adresse IP.
* CQ-4363346 : amélioration de l’interface utilisateur des directives de traduction avec la prise en charge du téléchargement d’exemples de directives, du chargement de fichiers de directives aux formats JSON, PDF et DOCX et de la suppression de directives existantes.
* GRANITE-67514 : isolation d’un lot de bibliothèque de mise en cache interne pour empêcher les échecs des tâches de transformation et les conflits avec les lots déployés par le client.
* SITES-42076 : expérimental : ajout d’opérations de recherche et de remplacement en masse pour les pages en tant que primitives MCP dans l’API de contenu.
* SITES-42835 : expérimental : les pages AEM Forms créées en dehors de l’API de contenu sont désormais accessibles via l’API de contenu d’AEM Sites sans nécessiter de migration ou de modifications de schéma.
* SITES-44265 : ajout d’un identifiant de page répliqué stable à l’API de contenu qui reste valide après les déplacements de page, ce qui empêche les erreurs 404 de référence obsolète.

### Problèmes résolus {#fixed-issues-26309}

* ASSETS-36208 : correction des profils d’image qui n’apparaissaient pas dans les propriétés de dossier lorsque Dynamic Media était désactivé.
* ASSETS-63240 : correction des opérations Relier à sélection multiple en bloc en mode d’ajout, qui laissaient les utilisateurs sur une page vierge au lieu de revenir à la console Assets.
* ASSETS-65076 : correction d’une valeur de protocole incorrecte transmise à l’API Externalizer, qui provoquait des échecs lors de l’utilisation des créateurs de requêtes Sling.
* ASSETS-66102 : correction des événements de publication de ressources Adobe I/O Runtime signalant une valeur de `repo:version` incorrecte, ce qui provoquait des échecs dans les intégrations en aval.
* ASSETS-66226 : les ressources fixes ne sont pas supprimées du niveau de diffusion lors de la suppression lorsque leur statut d’approbation est stocké avec des valeurs à casse mixte.
* ASSETS-66669 : correction du bouton Accueil de la page Résultats de la recherche qui ne naviguait pas vers l’écran de démarrage de l’interface utilisateur tactile lorsque Unified Shell était activé.
* ASSETS-66683 : correction d’une boucle d’approbation dans Dynamic Media avec OpenAPI déclenchée par des échecs de chargement, qui entraînait des retards et des perturbations des workflows d’approbation des ressources.
* ASSETS-67113 : correction de l’importation en bloc en ignorant les ressources SVG lors du filtrage par `image/svg+xml` de type MIME.
* CQ-4363466 : correction d’échecs de résolution de chemin de configuration du cloud affectant les connecteurs de traduction tiers qui utilisent la résolution de configuration personnalisée.
* CQ-4363355 : correction des demandes de traduction dans le connecteur de traduction GenAI en cours d’acheminement vers un point d’entrée régional incorrect en raison d’une URL statique codée en dur.
* SITES-44186 : correction d’une injection de balise meta sur l’auteur, interrompant la gestion des événements de l’éditeur de page pour certains clients.

### Problèmes connus {#known-issues-26309}

Aucun.

### Fonctionnalités et API obsolètes {#deprecated-26309}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-26309}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 19 vulnérabilités, renforçant ainsi notre engagement en faveur d’une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-26125}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 2.0.0 | [API Oak 2.0.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/2.0.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Serveur HTTP Apache | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| Composants principaux d’AEM | 2.30.4 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (par défaut) | [Versions de Node.js prises en charge](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
