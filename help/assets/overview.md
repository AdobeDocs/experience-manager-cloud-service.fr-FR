---
title: Présentation d’Assets as a Cloud Service
description: Nouveautés d’Assets as a Cloud Service.
contentOwner: AG
translation-type: ht
source-git-commit: 26833f59f21efa4de33969b7ae2e782fe5db8a14

---


# Présentation d’Assets as a Cloud Service {#assets-cloud-service-introduction}

<!-- Need review information from gklebus -->

Adobe Experience Manager Assets as a Cloud Service offre aux entreprises une solution PaaS cloud native pour qu’elles puissent non seulement exécuter rapidement et efficacement leurs opérations de gestion des ressources numériques et Dynamic Media, mais aussi utiliser des fonctionnalités intelligentes de nouvelle génération, telles que l’intelligence artificielle ou l’apprentissage automatique, à partir d’un système toujours à jour, toujours disponible et toujours à l’écoute.

L’ingestion simultanée d’un grand nombre de ressources ou de ressources complexes est une tâche gourmande en ressources pour une instance d’auteur AEM. L’instance principale consomme beaucoup de ressources processeur, mémoire et E/S lorsque des ressources sont ajoutées, traitées ou migrées. Ces problèmes de performances ont un impact sur l’expérience de création et la navigation des utilisateurs finaux.

Les entreprises ont besoin de la prise en charge d’un large éventail de formats de fichier et de résolutions de contenu pour les cas d’utilisation sur plusieurs appareils, dans plusieurs zones géographiques et plusieurs langues. Les besoins en matière de traitement et de stockage des ressources exigent des ressources et des capacités qui peuvent surcharger une solution traditionnelle. Parfois, les limites techniques du traitement des ressources ne produisent pas les résultats escomptés et, à d’autres moments, le coût du stockage constitue un obstacle aux marges bénéficiaires.

Pour commencer, il faut comprendre les [avantages de l’offre cloud native](#solution-benefits). Découvrez les [modifications notables apportées à AEM as a Cloud Service](/help/release-notes/aem-cloud-changes.md) qui ont également eu un impact sur Experience Manager Assets, suivies des [modifications notables apportées à Assets](/help/assets/assets-cloud-changes.md).

Lisez la suite pour connaître les [détails sur les nouvelles fonctionnalités Assets](#whats-new-assets) et les [problèmes connus](/help/release-notes/known-issues.md). Consultez la liste des [fonctionnalités obsolètes ou supprimées](/help/release-notes/deprecated-removed-features.md) pour savoir ce qui a été supprimé dans cette version et consultez cette [liste des fonctionnalités à venir](/help/release-notes/known-issues.md#upcoming-assets-capabilities) pour savoir ce qui est à venir. Enfin, utilisez ce [glossaire](/help/overview/terminology.md) pour mieux comprendre les termes AEM.

## Avantages de la solution {#solution-benefits}

Voici les principaux avantages d’Assets as a Cloud Service. Pour en savoir plus, reportez-vous à la [présentation d’Experience Manager as a Cloud Service](/help/overview/introduction.md).

* **Cloud Service moderne pour le traitement des ressources** : les nouveaux microservices de ressources sont un service de traitement des ressources basé sur le cloud, évolutif, fiable et sans tracas.
* **Très évolutif** : évolutivité adaptable à tous les types de déploiement. Ressources pratiquement illimitées, disponibles à la demande et au besoin. Réduit les coûts de surconception par rapport à un système traditionnel.
* **Logiciel le plus récent** : toujours actualisé et toujours à jour. Tous les utilisateurs ne disposent que des derniers logiciels avec tous les correctifs, fonctionnalités, sécurité et correctifs disponibles. Les développeurs et les intégrateurs utilisent les derniers jeux d’API sans problèmes de prise en charge de plusieurs versions.
* **Toujours en ligne** : « zéro temps mort » grâce à l’instance déployée dans une grappe avec des sauvegardes et une redondance. Les mises à niveau sont également conformes à l’objectif de zéro temps mort.
* **Surveillance constante** : la surveillance du système est automatisée et les contrôles et déclencheurs intégrés permettent de maintenir les performances, la disponibilité et la robustesse globales.
* **Déploiements sans tracas** : les opérations AEM en mode cloud sont entièrement automatisées et ne nécessitent aucune intervention manuelle. Pour les déploiements automatisés, le composant Cloud Manager (CM) automatise la création d’images Docker déployables contenant votre code personnalisé.

## Nouvelles fonctionnalités d’Assets {#whats-new-assets}

Les nouvelles fonctionnalités importantes sont les suivantes :

* [Microservices de ressources](/help/assets/asset-microservices-overview.md)
* [Méthodes de transfert de ressources](/help/assets/add-assets.md)
