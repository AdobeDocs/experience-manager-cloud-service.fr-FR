---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 5d00bed4008c70e81f3a70d219ddc411ec8bdc59
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 94%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 21484 {#21484}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 21484, publiée le vendredi 10 juillet 2025. La version de maintenance précédente était la version 21331.

L’activation des fonctionnalités de la version 2025.7.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-21484}

Aucun.

### Problèmes résolus {#fixed-issues-21484}

Aucun.

#### AEM Guides {#guides-21484}

* GUIDES-29781 : lorsqu’un commentaire XML est ajouté dans un élément de la vue Source, les espaces de début et de fin autour du commentaire sont perdues lors du changement de vue.
* GUIDES-29078 : lors de l’ouverture d’une rubrique en mode Création après l’actualisation du navigateur, les balises précédemment appliquées dans le panneau Propriétés du fichier ne sont pas conservées et l’ajout de nouvelles balises remplace les balises existantes, en particulier lorsqu’un grand nombre de balises sont disponibles à la sélection.
* GUIDES-28214 : les tentatives de création de tâches de révision par le biais du workflow AEM échouent systématiquement, car le nœud de révision n’est pas créé.
* GUIDES-28104 : la publication d’un plan DITA avec un attribut `chunk=to-content` crée des nœuds JCR en double dans la nouvelle sortie AEM Sites, ce qui entraîne une structure de contenu redondante dans AEM Sites.
* GUIDES-29065, GUIDES-28793 : des problèmes de performances tels que des temps de chargement plus longs et des délais d’expiration intermittents sont observés lors de l’utilisation de collections volumineuses.

Pour plus d’informations sur les fonctionnalités nouvelles et améliorées, ainsi que sur les problèmes résolus dans la version, consultez la [Feuille de route de publication d’Experience Manager Guides](https://experienceleague.adobe.com/fr/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Problèmes connus {#known-issues-21484}

* Le SDK rendu disponible dans le portail de distribution de logiciels présente des problèmes d’exécution locale. Veuillez continuer à utiliser le SDK précédent pour les tests locaux.

### Fonctionnalités et API obsolètes {#deprecated-21484}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-21484}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 5 vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-21484}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.80.0 | [API Oak 1.80.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.80.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | 2.29.0 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
