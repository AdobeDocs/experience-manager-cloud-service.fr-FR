---
title: Portail d’approvisionnement des ressources pour AEM Assets
description: Découvrez comment créer un portail d’approvisionnement Assets qui offre une expérience sécurisée en libre-service pour la collecte de ressources auprès de contributeurs externes sans leur accorder l’accès à Adobe Experience Manager Assets.
role: Admin
hide: true
badgeSaas: label="AEM Assets" type="Positive" tooltip="S’applique à AEM Assets)."
source-git-commit: c2a7e7ab0b3c8c336343036af105a827cd77f3c2
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 4%

---


# Portail d’approvisionnement des ressources pour AEM Assets {#asset-sourcing-portal-aem-assets}

Les entreprises s’appuient souvent sur des photographes, des agences de création et d’autres contributeurs externes pour fournir des ressources numériques. La collecte de ces ressources par e-mail, lecteurs partagés ou services de partage de fichiers peut entraîner des incohérences au niveau des métadonnées, du traitement manuel et des tâches administratives supplémentaires. Fournir aux contributeurs externes un accès direct à un système de gestion des ressources numériques (DAM) peut également nécessiter des licences supplémentaires et exposer le contenu interne.

Le portail d’approvisionnement Assets offre une expérience sécurisée en libre-service pour la collecte de ressources auprès de contributeurs externes sans leur accorder l’accès à Adobe Experience Manager Assets. Les contributeurs peuvent charger des ressources, fournir les métadonnées requises et envoyer directement du contenu à un emplacement d’entrée désigné, tandis que les administrateurs conservent le contrôle sur l’organisation et la gouvernance des ressources.

>[!IMPORTANT]
>
>Cette fonctionnalité est disponible en tant que fonctionnalité à disponibilité limitée. Vous pouvez [créer et envoyer un dossier d’assistance client Adobe](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html) pour l’activer pour votre déploiement.

## Avantages {#benefits-asset-sourcing-aem-assets}

L’utilisation du portail d’approvisionnement Assets offre les avantages suivants :

- Permet aux contributeurs externes de charger des ressources sans avoir besoin d’une licence AEM Assets.
- Simplifiez la prise de ressources grâce à une expérience de chargement dédiée.
- Réduisez le traitement manuel en appliquant automatiquement des politiques d’ingestion et de métadonnées.
- Améliorez la gouvernance en contrôlant l’emplacement de stockage des ressources chargées et les métadonnées fournies par les contributeurs.
- Faites évoluer l’intégration pour plusieurs contributeurs ou contributrices sans créer de solutions de chargement personnalisées.

## Comment fonctionne l’approvisionnement des ressources ? {#how-asset-sourcing-works-in-aem-assets}

Un administrateur configure un portail de source pour un contributeur externe en définissant les éléments suivants :

- Emplacement d’entrée de destination des ressources chargées.
- Les contributeurs et contributrices de champs de métadonnées doivent remplir.
- Politiques d’ingestion facultatives, telles que les conventions de nommage et les notifications.

Les contributeurs bénéficient d’une expérience de chargement dédiée où ils peuvent :

- Chargez une ou plusieurs ressources.
- Renseignez les champs de métadonnées requis.
- Envoi de ressources pour ingestion dans Adobe Experience Manager Assets.

Lors de l’ingestion, les ressources chargées sont traitées conformément aux politiques configurées avant d’être stockées à l’emplacement d’entrée désigné.

## Méthodes de chargement {#upload-methods-asset-sourcing-aem-assets}

Le portail Assets Sourcing prend en charge plusieurs méthodes de chargement afin que les contributeurs puissent travailler dans leurs workflows préférés.

- **Portail de navigateur :** fournit une expérience de chargement web dans laquelle les contributeurs et contributrices peuvent glisser-déposer des fichiers et remplir les métadonnées requises avant d’envoyer des ressources.

- **API REST :** permet aux entreprises d’intégrer des chargements de ressources dans des systèmes de production existants ou des workflows automatisés.

- **Fournisseur MCP :** permet aux contributeurs travaillant dans des environnements assistés par l’IA de charger des ressources par le biais de workflows de conversation pris en charge.

Toutes les méthodes de chargement fournissent les mêmes fonctionnalités principales d’ingestion de ressources.

## Fonctionnalités essentielles {#key-capabilities-asset-sourcing-aem-assets}

- **Accès sécurisé des contributeurs et contributrices** les contributeurs et contributrices externes peuvent charger des ressources sans accéder à la gestion des ressources numériques (DAM), parcourir les référentiels ou afficher d’autres ressources.

- **Collecte de métadonnées configurable :** les administrateurs sélectionnent les champs de métadonnées dans le schéma de métadonnées AEM Assets. Le portail génère automatiquement le formulaire d’envoi du contributeur en fonction des champs sélectionnés.

- **Ingestion automatisée des ressources :** les ressources chargées sont acheminées vers un emplacement d’entrée désigné, les métadonnées configurées étant appliquées lors de l’ingestion.

- **Politiques d’ingestion configurables :** les administrateurs peuvent définir des règles d’ingestion pour chaque contributeur, y compris les champs de métadonnées obligatoires et facultatifs, les valeurs préremplies, les identifiants de lot, les conventions de nommage des ressources, les chemins de destination, les dimensions minimales des ressources et les notifications des administrateurs.

- **Intégration évolutive des contributeurs :** configurez plusieurs contributeurs avec différentes destinations de chargement, exigences en matière de métadonnées et politiques d’ingestion sans développer d’applications de chargement personnalisées.

## Exemples de cas d’utilisation {#example-use-cases-asset-sourcing}

- **Collecter des ressources auprès des agences de création :** permet aux agences d’envoyer des ressources de campagne par le biais d’un portail de chargement dédié sans accorder l’accès à la gestion des ressources numériques (DAM) de l’organisation.

- **Recevoir les photographies envoyées :** proposer aux photographes une expérience de chargement simple qui capture automatiquement les métadonnées requises et stocke les ressources à l’emplacement d’entrée approprié.

- **Intégrer des systèmes de production externes :** utilisez l’API REST pour envoyer automatiquement des ressources à partir de systèmes de production ou de création de contenu tiers.

## Quand utiliser cette fonctionnalité ? {#when-to-use-this-capability}

Utilisez le Portail d’approvisionnement d’Assets lorsque vous devez :

- Collectez des ressources auprès de photographes, d’agences et de fournisseurs externes.
- Normaliser la collecte de métadonnées lors de la réception des ressources.
- Sécurisation des envois de ressources sans accès à la gestion des ressources numériques (DAM).
- Automatisez l’ingestion des ressources dans les emplacements d’entrée désignés.
- Soutenir un grand nombre de contributeurs externes.

## Quand ne pas utiliser cette fonctionnalité {#when-not-to-use-this-capability}

Le portail d’approvisionnement Assets n’est pas destiné aux :

- Gestion des ressources dans la gestion des ressources numériques après l’ingestion
- Permet aux contributeurs d’accéder à la navigation, à la recherche ou au téléchargement des ressources de gestion des ressources numériques.
- Workflows de collaboration internes qui nécessitent des fonctionnalités complètes de gestion des ressources numériques.