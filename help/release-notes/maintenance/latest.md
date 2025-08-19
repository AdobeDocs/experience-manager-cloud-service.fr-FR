---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 90e92cfb15a6dfe5a8a474996f52c8a0c689f5e6
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 37%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 21994 {#21994}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 21994, publiée le mercredi 19 août 2025. La version de maintenance précédente était la version 21772.

L’activation des fonctionnalités de la version 2025.8.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Nouvelles fonctionnalités  {#new-features-21994}

Aucun.

### Améliorations {#enhancements-21994}

* GRANITE-53488 : amélioration de la gestion des erreurs du point d’entrée deleteconf.json.
* GRANITE-59968 : permet de configurer REPLICATION_FORCE_READY_MILLIES.
* GRANITE-60183 : Apache commons-fileupload 1.6.0.
* GRANITE-60306 : Apache commons-lang vers 3.18.0.
* GRANITE-60637 : codec Apache commons vers la version 1.19.0.
* GRANITE-60645 : Apache commons-ui 2.20.0.
* GRANITE-60663 : Apache commons-text 1.14.0.
* GRANITE-60714 : pilote Java Mongo 5.2.
* GRANITE-60778 : Filevault 4.0.0.
* GRANITE-60823 : Jackrabbit 2.22.2.
* GRANITE-60967 : création de mesures pour le suivi du temps de compilation de la bibliothèque cliente.
* SKYOPS-105469 : ajout de la prise en charge d’acsredirectMgr dans l’api de correctif automatique.
* SKYOPS-113929 : ajout de mesures pour la vérification de la réplication prête.
* SKYOPS-84821 : moteur Sling 2.16.6.
* SKYOPS-114322 : augmenter le langage du compilateur de fermeture au niveau de la `ECMASCRIPT_2018`.

### Problèmes résolus {#fixed-issues-21994}

* GRANITE-60167 : la mise à jour de l’index asynchrone dans Skyline ne prend pas en charge les données CSV.
* GRANITE-60532 : la modification des bascules de valeur n’est pas sélectionnée.
* SITES-34277 : correction d’une erreur de blocage dans les workflows de traduction de pages.
* SKYOPS-105471 : Prise en charge du correctif dambaseredirect pour le correctif automatique aso.
* SKYOPS-109532 : ajout d’un lien de suppression de fonctionnalité en tant que commentaire derrière le bouton bascule.

#### AEM Guides {#guides-21994}

* GUIDES-26688 : les fichiers de mise en page et CSS dans les modèles PDF natifs présentent un comportement de verrouillage de fichier incohérent, ce qui permet d’apporter des modifications même lorsque les fichiers sont verrouillés.
* GUIDES-30900 : la copie d’un dossier contenant un grand nombre de ressources à partir de l’interface utilisateur d’Assets entraîne un délai d’expiration de l’API. L’opération continue de s’exécuter sur le serveur principal et se termine au bout d’un certain temps, mais aucun message de réussite ou d’échec, ou de notification n’est affiché dans l’interface utilisateur.
* GUIDES-29090 : dans la sortie Native PDF, la liste des index (LOI) s’affiche dans un ordre non alphabétique et les termes d’index imbriqués ne sont pas correctement regroupés, ce qui rend l’index difficile à parcourir.
* GUIDES-11227 : la copie d&#39;un plan DITA à partir de l&#39;interface utilisateur d&#39;Assets copie également sa ligne de base associée dans le nouveau plan.
* GUIDES-31506 : la page d’accueil devient vide lorsque l’un des fichiers répertoriés dans le widget Fichiers récents est basé sur un modèle dont le modèle source n’inclut pas de miniature.

Pour plus d’informations sur les fonctionnalités nouvelles et améliorées, ainsi que sur les problèmes résolus dans la version, consultez la [Feuille de route de publication d’Experience Manager Guides](https://experienceleague.adobe.com/fr/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Problèmes connus {#known-issues-21994}

* La version 2.4.65 d’Apache HTTPD introduit des modifications qui peuvent affecter certaines configurations en raison de nouvelles restrictions implémentées dans le cadre de correctifs de sécurité. Ces correctifs corrigent les vulnérabilités en s’assurant que les directives telles que `RequestHeader set`, `edit` et `edit_r` utilisées pour modifier l’en-tête Type de contenu sont désormais correctement limitées aux en-têtes de requête. Cette modification empêche toute modification involontaire des en-têtes de réponse, en particulier pour le contenu statique.

### Fonctionnalités et API obsolètes {#deprecated-21994}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-21994}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 2 vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-21994}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1,84,0 | [API Oak 1.84.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.84/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Serveur HTTP Apache | 2,4,65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| Composants principaux d’AEM | 2.29.0 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (par défaut) | [Versions de Node.js prises en charge](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
