---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 1d6a54f87d55179c11c7ccc7766eeeb475674f05
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 49%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 19567 {#19567}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 19567, rendue publique le mercredi 18 février 2025. La version de maintenance précédente était la version 19352.

L’activation des fonctionnalités de la version 2025.2.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-19567}

* GRANITE-56650 : la distribution de contenu ne doit signaler que la file d’attente bloquée après quelques reprises
* SKYOPS-89616 : permet de créer jusqu’à 40 comptes techniques dans Adobe Developer Console.

### Problèmes résolus {#fixed-issues-19567}

* CNTBF-232 : nœuds nt:file profonds de package pour inclure l’enfant jcr:content obligatoire
* CQ-4358930 : Problème de performance lors du chargement des propriétés de page avec de nombreux champs multiples
* GRANITE-55960 : problème de performances du champ Coral Select sur AEM as a Cloud Service
* GRANITE-56197 : la nouvelle étape du workflow TreeActivation ne traite pas par lots les ressources dans une grande structure de dossiers plats

#### Guides AEM {#guides}

* GUIDES-23526 : lors de la mise à jour de conditions à partir du profil de dossier, tous les groupes de conditions sont perdus et les conditions sont aplaties.
* GUIDES-22574 : si un lien externe contient un UUID, il passe en post-traitement et convertit le lien externe en lien UUID, rompant ainsi le lien dans l&#39;éditeur ainsi que sur les sites de publication.
* GUIDES-24983 : lors de la copie d’une image à partir d’un produit externe (par exemple, MS PowerPoint) et de son collage dans Guides, la fonctionnalité de chargement à la volée de la ressource en vue de son utilisation dans les fichiers est interrompue.
* GUIDES-21772 : la génération native de PDF échoue pour le contenu avec l’attribut **chunk** défini sur **à contenu**.
* GUIDES-23964 : lorsque vous choisissez **Modifier les propriétés**, la boîte de dialogue de ligne de base n&#39;affiche pas les critères précédemment enregistrés pour la ligne de base dynamique.
* GUIDES-19067 : Lors de la duplication d’un profil de dossier, sa liste d’utilisateurs administrateurs est également copiée à partir du profil de dossier d’origine

Pour plus d’informations sur les fonctionnalités nouvelles et améliorées, ainsi que sur les problèmes résolus dans la version, consultez la [Feuille de route de publication d’Experience Manager Guides](https://experienceleague.adobe.com/fr/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Problèmes connus {#known-issues-19567}

Aucun.

### Fonctionnalités et API obsolètes {#deprecated-19567}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-19567}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 21 vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-19567}

| Technologie | Version | Lien |
|---|--------------|-------------------------------------------------------------------------------------------------------------------|
| AEM Oak | 1.76.0 | [API Oak 1.76.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.76.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.26-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | 2.27.0 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
