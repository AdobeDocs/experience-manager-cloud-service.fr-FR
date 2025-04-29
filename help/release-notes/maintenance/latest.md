---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 437125b6819edf70539ebacb4a8beddb755fcb7a
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 39%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 20626 {#20626}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 20626, rendue publique le mercredi 29 avril 2025. La version de maintenance précédente était la version 20476.

L’activation des fonctionnalités de la version 2025.5.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-20626}

* ASSETS-46413, ASSETS-46580 : ajout d’un nouveau statut de révision, « Aperçu ».
* ASSETS-49542 : développement des langues prises en charge pour la transcription et la traduction vidéo et audio.
* ASSETS-48264 : extension de la prise en charge de la qualité PNG des rendus.

### Problèmes résolus {#fixed-issues-20626}

* ASSETS-50387 : correction de la miniature par défaut du fragment de contenu à utiliser dans GenStudio.
* ASSETS-49006 : affichage des propriétés vidéo lorsque l’utilisateur ne dispose pas des autorisations d’écriture.
* ASSETS-46757, ASSETS-46997 : amélioration de l’accessibilité dans l’éditeur de recadrage intelligent.
* ASSETS-48018 : amélioration du suivi des références de ressources dans le rapport de publication Assets.
* ASSETS-35846 : améliorer la cohérence de l’accès entre le niveau de création et celui de diffusion.
* ASSETS-48171 : amélioration de la cohérence du modèle Dynamic Media avec la zone de travail.
* ASSETS-49813 : Améliorez Les Notifications D’Expiration.
* ASSETS-47768, ASSETS-49825, ASSETS-49008, ASSETS-48287 : améliorez la gestion et la visibilité des opérations en bloc.
* ASSETS-50003, ASSETS-50004 : améliorez l’attribution de noms et le contrôle des rendus inclus dans un téléchargement de ressource.
* ASSETS-47939 : amélioration de l’organisation des réponses pour Content Hub.
* ASSETS-46738 : améliore les performances des très grandes collections.
* ASSETS-50121 : amélioration de la fiabilité des événements publiés sur les ressources.
* ASSETS-48490 : amélioration de la résilience du traitement automatisé lors de l’ingestion d’images.
* ASSETS-28106, ASSETS-49404 : amélioration de la robustesse de la recherche de texte intégral.
* ASSETS-50006, ASSETS-50423 : améliorez les performances de recherche et de traversée dans un dossier volumineux.
* ASSETS-46021 : amélioration de l’affichage vidéo pour les navigateurs Safari et mobiles.
* ASSETS-49002 : amélioration de la gestion de la modification des modèles Dynamic Media.
* ASSETS-48376 : diverses améliorations de l’interface utilisateur de Content Hub.
* ASSETS-48504, ASSETS-49378 : diverses améliorations du comportement de l’interface utilisateur.
* ASSETS-49540 : sortie de la phase expérimentale de l’OpenAPI Asset Relations.
* ASSETS-40284 : mise à jour de la documentation sur l’intégration d’Adobe Stock.
* ASSETS-49739 : travail d’intégration de Figma à partir du sélecteur de ressources.

#### Guides AEM {#guides}

* GUIDES-21734 : la génération de nouveaux identifiants pour les éléments échoue lorsque ces éléments sont ajoutés via des fragments de code ou créés via des modèles, même si l’option de génération automatique d’identifiants est activée dans XMLEditorConfig.
* GUIDES-25969 : si l&#39;attribut `scope=external` est absent des liens externes dans une rubrique DITA, la publication HTML5 échoue sans indiquer les fichiers dans lesquels cet attribut est absent des journaux d&#39;erreurs, en particulier lorsque le microservice est activé.
* GUIDES-27288 : impossible de transmettre les propriétés de métadonnées pour mapper les pages de destination générées à l’aide d’une nouvelle publication AEM Sites.

Pour plus d’informations sur les fonctionnalités nouvelles et améliorées, ainsi que sur les problèmes résolus dans la version, consultez la [Feuille de route de publication d’Experience Manager Guides](https://experienceleague.adobe.com/fr/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Problèmes connus {#known-issues-20626}

Aucun.

### Fonctionnalités et API obsolètes {#deprecated-20626}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-20626}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 11 vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-20626}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.78.0 | [API Oak 1.78.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.78.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.26-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | 2.29.0 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
