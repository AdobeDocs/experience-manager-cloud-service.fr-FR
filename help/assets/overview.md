---
title: Gestion des ressources numériques (DAM) d’Adobe à l’aide d’AEM
description: Découvrez comment utiliser et administrer la gestion des ressources numériques (DAM) d’Adobe à l’aide d’Experience Manager Assets as a Cloud Service.
contentOwner: AK
feature: Asset Management
role: User, Leader, Architect
exl-id: 4437f214-d058-4975-8b8f-869a12c8103b
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '973'
ht-degree: 97%

---


# Présentation d’Assets as a [!DNL Cloud Service] pour la gestion des ressources numériques dans AEM {#assets-cloud-service-introduction}

<!-- Need review information from gklebus -->

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime et Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouvelle</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>Intégration d’AEM Assets à Edge Delivery Services</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>Extensibilité de l’interface utilisateur</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Activation de Dynamic Media Prime et Ultimate</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>Bonnes pratiques de recherche</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>Bonnes pratiques relatives aux métadonnées</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Hub de contenus</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>Fonctionnalités Dynamic Media avec OpenAPI</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>Documentation de développement pour AEM Assets</b></a>
        </td>
    </tr>
</table>

Adobe Experience Manager Assets as a [!DNL Cloud Service] offre aux entreprises une solution PaaS cloud native pour qu’elles puissent non seulement exécuter rapidement et efficacement leurs opérations de gestion des ressources numériques et Dynamic Media, mais aussi utiliser des fonctionnalités intelligentes de nouvelle génération, telles que l’intelligence artificielle ou l’apprentissage automatique, à partir d’un système toujours à jour, toujours disponible et qui apprend en permanence.

L’ingestion simultanée d’un grand nombre de ressources ou de ressources complexes est une tâche gourmande en ressources pour une instance d’auteur Experience Manager. L’instance principale consomme beaucoup de ressources processeur, mémoire et E/S lorsque des ressources sont ajoutées, traitées ou migrées. Ces problèmes de performances ont un impact sur l’expérience de création et la navigation des utilisateurs finaux.

Les entreprises ont besoin de la prise en charge d’un large éventail de formats de fichier et de résolutions de contenu pour les cas d’utilisation sur plusieurs appareils, dans plusieurs zones géographiques et plusieurs langues. Les besoins en matière de traitement et de stockage des ressources exigent des ressources et des capacités qui peuvent surcharger une solution traditionnelle. Parfois, les limites techniques du traitement des ressources ne produisent pas les résultats escomptés et, à d’autres moments, le coût du stockage constitue un obstacle aux marges bénéficiaires.

Pour commencer, il est nécessaire de comprendre les [avantages de l’offre cloud native](#solution-benefits) pour la gestion des ressources numériques. Découvrez les [modifications notables apportées à Experience Manager as a [!DNL Cloud Service]](/help/release-notes/aem-cloud-changes.md) qui ont également eu un impact sur Experience Manager Assets, suivies des [modifications notables apportées à Assets](/help/assets/assets-cloud-changes.md).

Lisez la suite pour connaître les [détails sur les nouvelles fonctionnalités Assets](#whats-new-assets) et les [problèmes connus](/help/release-notes/maintenance/latest.md). Consultez la liste des [fonctionnalités obsolètes ou supprimées](/help/release-notes/deprecated-removed-features.md) pour savoir ce qui a été supprimé dans cette version. Enfin, utilisez ce [glossaire](/help/overview/terminology.md) pour mieux comprendre les termes Experience Manager.

## Avantages de la solution {#solution-benefits}

Voici les principaux avantages d’Assets as a [!DNL Cloud Service] pour la gestion des ressources numériques. Pour en savoir plus, reportez-vous à la [présentation d’Experience Manager as a [!DNL Cloud Service]](/help/overview/introduction.md).

* **Services cloud modernes pour le traitement des ressources** : les nouveaux microservices de ressources sont un service de traitement des ressources basé sur le cloud, évolutif, fiable et sans tracas.
* **Très évolutif** : évolutivité adaptable à tous les types de déploiement. Ressources pratiquement illimitées, disponibles à la demande et au besoin. Réduit les coûts de surconception par rapport à un système traditionnel.
* **Logiciel le plus récent** : toujours actualisé et toujours à jour. Tous les utilisateurs ne disposent que des derniers logiciels avec tous les correctifs, fonctionnalités, sécurité et correctifs disponibles. Les développeurs et les intégrateurs utilisent les derniers jeux d’API sans problèmes de prise en charge de plusieurs versions.
* **Toujours en ligne** : « zéro temps mort » grâce à l’instance déployée dans une grappe avec des sauvegardes et une redondance. Les mises à niveau sont également conformes à l’objectif de zéro temps mort.
* **Surveillance constante** : la surveillance du système est automatisée et les contrôles et déclencheurs intégrés permettent de maintenir les performances, la disponibilité et la robustesse globales.
* **Déploiements sans tracas** : les opérations d’Experience Manager en mode cloud sont entièrement automatisées et ne nécessitent aucune intervention manuelle. Pour les déploiements automatisés, le composant Cloud Manager (CM) automatise la création d’images Docker déployables contenant votre code personnalisé.

## Expériences personnalisées disponibles pour la gestion des ressources numériques {#persona-based-experiences}

Adobe propose une solution de Gestion des actifs numériques (DAM) robuste qui vous permet de tirer le meilleur parti de vos ressources numériques. Adobe Experience Manager Assets comporte deux expériences distinctes qui utilisent le même référentiel de Cloud Services :

* **Vue Admin** : interface utilisateur Assets as a Cloud Service existante. Utilisez la vue Admin pour toutes les fonctionnalités avancées de gestion des ressources numériques, notamment les intégrations, les workflows, l’automatisation du contenu, la publication, etc.

* **Vue Assets** : expérience allégée de gestion des ressources numériques d’Adobe permettant de stocker, gérer, découvrir et utiliser des ressources numériques. Interface d’utilisation rationalisée contenant les fonctionnalités essentielles de gestion des ressources numériques. Conçue pour les personnes utilisant de la gestion des ressources numériques allégée et qui se concentrent sur le chargement, la gestion des métadonnées, la recherche, le téléchargement et le partage.

Les personnes ayant accès à la vue Admin peuvent également accéder à la vue Assets. La vue Assets propose une interface utilisateur simplifiée, qui facilite la gestion, la découverte et la distribution des ressources numériques. Un vaste ensemble de personnes provenant de différentes fonctions, y compris les équipes créatives, marketing et métier, peuvent collaborer sur les ressources et accéder aux ressources appropriées et approuvées, n’importe où et à tout moment. De nombreuses personnes dédiées à la gestion des actifs numériques préfèrent la vue Assets, car elle ne contient qu’un sous-ensemble de fonctionnalités. L’expérience est destinée aux créateurs et créatrices, aux consommateurs et consommatrices de ressources en lecture seule et aux utilisateurs et utilisatrices de DAM plus légers.

Les personnes bibliothécaires de la gestion des ressources numériques, les développeurs et développeuses et les super-utilisateurs et super-utilisatrices peuvent continuer à utiliser la vue Admin ou basculer entre les interfaces utilisateur, le cas échéant. Vous pouvez sélectionner l’expérience qui fonctionne le mieux pour votre rôle.

![add-tags](assets/newui-overview.svg)

Pour plus d’informations sur l’accès à la vue Assets et sur certaines des simplifications qu’elle offre par rapport à la vue Admin, voir [Présentation de la vue Assets](/help/assets/assets-view-introduction.md).

## Intégration à la création basée sur des documents pour Edge Delivery Services {#integrate-doc-authoring-edge-and-assets}

Edge Delivery permet de créer rapidement des sites web dans lesquels les auteurs et autrices peuvent rapidement mettre à jour et publier du contenu, afin de lancer rapidement de nouveaux sites.

Intégrez AEM Assets à la création basée sur des documents pour Edge Delivery Services afin de permettre aux créateurs et créatrices de sites web d’utiliser les images disponibles dans les référentiels AEM Assets lors de la création de documents dans Microsoft Word ou Google Docs. Pour plus d’informations, voir [Intégration d’AEM Assets à la création basée sur des documents](/help/edge/using.md#integrate-assets-edge).

## Intégration à Adobe Journey Optimizer {#integration-with-ajo}

[Adobe Journey Optimizer](https://business.adobe.com/fr/products/journey-optimizer/adobe-journey-optimizer.html) simplifie la gestion des parcours pour que les clientes et les clients puissent fournir des campagnes omnicanal avec une prise de décision et des informations intelligentes. Lors de la conception de messages à l’aide de Journey Optimizer, vous pouvez accéder au référentiel Assets as a Cloud Service directement depuis l’interface de Journey Optimizer. Les utilisateurs et les utilisatrices accèdent aux ressources à l’aide de l’interface utilisateur intégrée d’Experience Manager Assets. Pour plus d’informations, consultez [Créer et gérer des ressources à l’aide d’Experience Manager Assets](https://experienceleague.adobe.com/docs/journey-optimizer/using/content-management/assets-images/assets.html?lang=fr).

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
* [Publier des ressources sur AEM et Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
