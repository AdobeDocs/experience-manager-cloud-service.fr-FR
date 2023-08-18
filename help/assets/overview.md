---
title: Présentation d’Assets as a [!DNL Cloud Service]
description: Découvrez les nouveautés et les avantages de Experience Manager Assets as a [!DNL Cloud Service]. Solution PaaS cloud native pour les entreprises.
contentOwner: AK
feature: Asset Management
role: User,Leader,Architect
exl-id: 4437f214-d058-4975-8b8f-869a12c8103b
source-git-commit: d663c258a83473ec8d3c68bc5683955003d889c7
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 66%

---

# Présentation d’Assets as a [!DNL Cloud Service] {#assets-cloud-service-introduction}

<!-- Need review information from gklebus -->

Adobe Experience Manager Assets as a [!DNL Cloud Service] offre aux entreprises une solution PaaS cloud native pour qu’elles puissent non seulement exécuter rapidement et efficacement leurs opérations de gestion des ressources numériques et Dynamic Media, mais aussi utiliser des fonctionnalités intelligentes de nouvelle génération, telles que l’intelligence artificielle ou l’apprentissage automatique, à partir d’un système toujours à jour, toujours disponible et qui apprend en permanence.

L’ingestion simultanée d’un grand nombre de ressources ou de ressources complexes est une tâche gourmande en ressources pour une instance d’auteur Experience Manager. L’instance principale consomme beaucoup de ressources processeur, mémoire et E/S lorsque des ressources sont ajoutées, traitées ou migrées. Ces problèmes de performances ont un impact sur l’expérience de création et la navigation des utilisateurs finaux.

Les entreprises ont besoin de la prise en charge d’un large éventail de formats de fichier et de résolutions de contenu pour les cas d’utilisation sur plusieurs appareils, dans plusieurs zones géographiques et plusieurs langues. Les besoins en matière de traitement et de stockage des ressources exigent des ressources et des capacités qui peuvent surcharger une solution traditionnelle. Parfois, les limites techniques du traitement des ressources ne produisent pas les résultats escomptés et, à d’autres moments, le coût du stockage constitue un obstacle aux marges bénéficiaires.

Pour commencer, il faut comprendre les [avantages de l’offre cloud native](#solution-benefits). Découvrez les [modifications notables apportées à Experience Manager as a [!DNL Cloud Service]](/help/release-notes/aem-cloud-changes.md) qui ont également eu un impact sur Experience Manager Assets, suivies des [modifications notables apportées à Assets](/help/assets/assets-cloud-changes.md).

Lisez la suite pour connaître les [détails sur les nouvelles fonctionnalités Assets](#whats-new-assets) et les [problèmes connus](/help/release-notes/maintenance/latest.md). Consultez la liste des [fonctionnalités obsolètes ou supprimées](/help/release-notes/deprecated-removed-features.md) pour savoir ce qui a été supprimé dans cette version. Enfin, utilisez ce [glossaire](/help/overview/terminology.md) pour mieux comprendre les termes Experience Manager.

## Avantages de la solution {#solution-benefits}

Voici les principaux avantages d’Assets as a [!DNL Cloud Service]. Pour en savoir plus, reportez-vous à la [présentation d’Experience Manager as a [!DNL Cloud Service]](/help/overview/introduction.md).

* **Services cloud modernes pour le traitement des ressources** : les nouveaux microservices de ressources sont un service de traitement des ressources basé sur le cloud, évolutif, fiable et sans tracas.
* **Très évolutif** : évolutivité adaptable à tous les types de déploiement. Ressources pratiquement illimitées, disponibles à la demande et au besoin. Réduit les coûts de surconception par rapport à un système traditionnel.
* **Logiciel le plus récent** : toujours actualisé et toujours à jour. Tous les utilisateurs ne disposent que des derniers logiciels avec tous les correctifs, fonctionnalités, sécurité et correctifs disponibles. Les développeurs et les intégrateurs utilisent les derniers jeux d’API sans problèmes de prise en charge de plusieurs versions.
* **Toujours en ligne** : « zéro temps mort » grâce à l’instance déployée dans une grappe avec des sauvegardes et une redondance. Les mises à niveau sont également conformes à l’objectif de zéro temps mort.
* **Surveillance constante** : la surveillance du système est automatisée et les contrôles et déclencheurs intégrés permettent de maintenir les performances, la disponibilité et la robustesse globales.
* **Déploiements sans tracas** : les opérations d’Experience Manager en mode cloud sont entièrement automatisées et ne nécessitent aucune intervention manuelle. Pour les déploiements automatisés, le composant Cloud Manager (CM) automatise la création d’images Docker déployables contenant votre code personnalisé.

## Expériences personnalisées disponibles {#persona-based-experiences}

Adobe propose une solution de Gestion des actifs numériques (DAM) robuste qui vous permet de tirer le meilleur parti de vos ressources numériques. Adobe Experience Manager Assets comporte deux expériences distinctes qui utilisent le même référentiel de Cloud Service :

* **Vue d’administration**: interface utilisateur as a Cloud Service d’Assets existante. Utilisez la vue d’administration pour toutes les fonctionnalités avancées de gestion des ressources, notamment les intégrations, les workflows, l’automatisation du contenu, la publication, etc.

* **Affichage des ressources**: expérience légère de gestion des ressources d’Adobe pour stocker, gérer, découvrir et utiliser des ressources numériques. Interface utilisateur rationalisée contenant les fonctionnalités essentielles de gestion des ressources. Conçu pour les utilisateurs de la gestion des ressources numériques légère qui se concentrent sur le chargement, la gestion des métadonnées, la recherche, le téléchargement et le partage.

Les utilisateurs ayant accès à la vue Admin peuvent également accéder à la vue Ressources. La vue Assets offre une interface utilisateur simplifiée qui facilite la gestion, la découverte et la distribution de vos ressources numériques. Un large ensemble d’utilisateurs provenant de différentes fonctions, y compris des créatifs, des équipes marketing et commerciales, peuvent collaborer sur les ressources et accéder aux ressources approuvées appropriées lorsqu’elles en ont besoin. De nombreux utilisateurs de la gestion des actifs numériques préfèrent la vue Ressources, car elle ne contient qu’un sous-ensemble de fonctionnalités. L’expérience est destinée aux créatifs, aux consommateurs de ressources en lecture seule et aux utilisateurs DAM plus légers.

Les bibliothécaires de la gestion des actifs numériques, les développeurs et les super-utilisateurs peuvent continuer à utiliser la vue Admin ou basculer entre les interfaces utilisateur, si nécessaire. Vous pouvez sélectionner l’expérience qui fonctionne le mieux pour votre rôle.

![add-tags](assets/newui-overview.svg)

Pour plus d’informations sur l’accès à la vue Assets et sur certaines des simplifications qu’elle offre par rapport à la vue Admin, voir [Présentation de la vue Assets](/help/assets/assets-view-introduction.md).

## Nouvelles fonctionnalités d’Assets {#whats-new-assets}

Les nouvelles fonctionnalités importantes sont les suivantes :

* [Microservices de ressources](/help/assets/asset-microservices-overview.md)
* [Méthodes de chargement de ressources](/help/assets/add-assets.md)

**Voir également**

* [Traduire les ressources](translate-assets.md)
* [API HTTP Assets](mac-api-assets.md)
* [Formats de fichiers pris en charge par Assets](file-format-support.md)
* [Rechercher des ressources](search-assets.md)
* [Ressources connectées](use-assets-across-connected-assets-instances.md)
* [Rapports de ressources](asset-reports.md)
* [Schémas de métadonnées](metadata-schemas.md)
* [Télécharger des ressources](download-assets-from-aem.md)
* [Gestion des métadonnées](manage-metadata.md)
* [Facettes de recherche](search-facets.md)
* [Gérer les collections](manage-collections.md)
* [Import des métadonnées en bloc](metadata-import-export.md)
