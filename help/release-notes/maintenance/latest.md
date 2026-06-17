---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 8e557ae876a591b03294ecf938f1017eee34dd5e
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 41%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## 26635 de publication {#release-26635}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 26635, rendue publique le 17 juin 2026. La version de maintenance précédente était la version 26353.

L’activation de la fonctionnalité 2026.6.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-26635}

* GRANITE-67251 : présentation de `cqSiteSearch`, un nouvel index prêt à l’emploi défini sur le type de mixin `cq:Searchable`. Cela permet un contrôle précis du contenu qui entre dans l’index du site et fournit une recherche de site complète pour les sites web AEM, y compris une recherche sémantique.
* GRANITE-68099 : mise à jour d’Apache Jackrabbit Oak incorporé vers la dernière version publique (2.2.0).
* SKYOPS-135241 : introduisez un préfixe aem pour les filtres de batterie non modifiables afin d’éviter les conflits de noms avec les configurations définies par le client ou la cliente.

### Problèmes résolus {#fixed-issues-26635}

Aucun.

#### AEM Guides {#guides-26635}

* GUIDES-46275 : les dimensions d’image spécifiées avec des unités telles que `mm` ne sont pas rendues correctement, ce qui entraîne l’affichage des images à leur taille d’origine au lieu des dimensions spécifiées.
* GUIDES-45800 : si vous copiez et collez des `<keywords>` à l’intérieur de `<topicmeta>` dans un `<keydef>` ou un `<topicref>`, les mots-clés sont insérés dans des balises étrangères indésirables.
* GUIDES-45409 : lorsqu&#39;un mappage contient un `topicref` externe pointant vers une ressource non-DITA (telle que `.html`), son aperçu ne s&#39;affiche pas dans l&#39;interface utilisateur d&#39;Assets.
* GUIDES-45254 : lorsque vous utilisez des fichiers `.plt` et `.css` dans des modèles PDF, l’option **Générer des identifiants** est disponible dans le menu contextuel accessible par un clic droit, bien qu’elle ne s’applique pas à ces types de fichiers.
* GUIDES-45508 : l’application d’une ligne de base à une carte avec de nombreuses ressources retarde le chargement du rapport de traduction pour la langue sélectionnée, ce qui entraîne parfois un délai d’expiration de la demande avant le rendu du rapport.
* GUIDES-45511 : l’info-bulle de l’icône **Historique des versions** est manquante dans le panneau de gauche de l’interface utilisateur de révision à côté du nom de la rubrique.
* GUIDES-44942 : Lors de l&#39;ajout de questions à un quiz à l&#39;aide de l&#39;option Insérer à partir de la banque de questions, les questions à réponse courte ne sont pas répertoriées malgré un ID de question valide.

Pour plus d’informations sur les fonctionnalités nouvelles et améliorées, ainsi que sur les problèmes résolus dans la version, consultez la [Feuille de route de publication d’Experience Manager Guides](https://experienceleague.adobe.com/fr/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Problèmes connus {#known-issues-26635}

Aucun.

### Fonctionnalités et API obsolètes {#deprecated-26635}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-26635}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 10 vulnérabilités identifiées, renforçant ainsi notre engagement en faveur d’une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-26635}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 2.2.0 | [API Oak 2.2.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/2.2.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Serveur HTTP Apache | 2.4.67 | [Apache Httpd 2.4.67](https://apache.googlesource.com/httpd/+/refs/tags/2.4.67/CHANGES) |
| Dispatcher | 2.0.274 |  |
| Composants principaux AEM | 2.31.0 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (par défaut) | [Versions de Node.js prises en charge](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |

