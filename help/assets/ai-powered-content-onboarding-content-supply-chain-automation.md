---
title: Intégration de contenu optimisé par l’IA et automatisation de Content supply chain
description: Découvrez comment automatiser les migrations de contenu ponctuelles et l’automatisation de la supply chain de contenu entre Adobe et les référentiels tiers pris en charge.
role: Admin
hide: true
badgeSaas: label="AEM Assets" type="Positive" tooltip="S’applique à AEM Assets)."
source-git-commit: c2a7e7ab0b3c8c336343036af105a827cd77f3c2
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 5%

---


# Intégration de contenu optimisé par l’IA et automatisation de Content supply chain {#ai-powered-content-onboarding-content-supply-chain-automation}

Les entreprises stockent souvent des ressources numériques et des métadonnées dans plusieurs référentiels, tels que des systèmes de gestion des ressources numériques (DAM), des services de stockage dans le cloud et des plateformes de contenu. La migration de contenu vers un nouveau système ou la synchronisation de plusieurs référentiels nécessite généralement un effort manuel ou des intégrations personnalisées qui peuvent être difficiles à créer et à gérer.

Cette fonctionnalité vous permet d’automatiser les migrations de contenu uniques et la synchronisation récurrente entre les référentiels pris en charge. Un agent optimisé par l’IA vous guide tout au long de la configuration des transferts de contenu en vous proposant des connexions de référentiel, des mappages de métadonnées et des paramètres de transfert, ce qui réduit l’effort requis pour déplacer et synchroniser le contenu entre les systèmes.

>[!IMPORTANT]
>
>Cette fonctionnalité est disponible en tant que fonctionnalité à disponibilité limitée. Vous pouvez [créer et envoyer un dossier d’assistance client Adobe](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html) pour l’activer pour votre déploiement.

## Avantages {#benefits-ai-powered-content-onboarding-content-supply-chain-automation}

L’automatisation de l’intégration et de la synchronisation du contenu offre les avantages suivants :

- Accélérez l’intégration en réduisant le temps nécessaire à la migration des ressources et métadonnées existantes vers un nouveau référentiel.
- Simplifiez la synchronisation récurrente en automatisant les transferts de contenu planifiés entre les systèmes d’enregistrement.
- Réduisez les frais de maintenance en remplaçant les intégrations personnalisées par des connexions configurables.
- Prise en charge des transferts de contenu entre Adobe et des référentiels tiers.
- Validez les paramètres de transfert avant de déplacer le contenu à l’aide d’exécutions à sec.

## Comment fonctionnent les transferts de contenu ? {#how-content-transfer-work}

L’agent optimisé par l’IA permet de configurer un transfert de contenu entre un référentiel source et un référentiel de destination.

Pendant la configuration, l’agent :

- Collecte les informations requises pour se connecter à chaque référentiel.
- Propose des mappages entre les champs de métadonnées et les taxonomies.
- Permet de passer en revue et de valider les mappages proposés avant de transférer du contenu.
- Prend en charge les exécutions à sec afin que vous puissiez vérifier la configuration avant de déplacer le contenu de production.
- Configure des plannings de transfert ponctuels ou récurrents.

Chaque transfert configuré est appelé une **connexion**. Une connexion utilise des **passerelles** pour communiquer avec les référentiels source et de destination. Chaque exécution d’une connexion est appelée une **exécution**.

Les exécutions sont avec état. Ils effectuent le suivi des ressources et des métadonnées transférées précédemment afin que les exécutions suivantes ne transfèrent que le contenu nouveau ou modifié au lieu de traiter à nouveau l’intégralité du référentiel.

## Fonctionnalités essentielles {#key-capabilities-ai-powered-content-onboarding-content-supply-chain-automation}

- **Mappage d’identité** : maintient la relation entre les ressources des référentiels source et de destination sur plusieurs exécutions.

- **Détection des modifications** : transfère uniquement les ressources et métadonnées qui ont été modifiées depuis l’exécution précédente, ce qui réduit les traitements inutiles et améliore l’efficacité.

- **Mappage des métadonnées** : mappe les champs de métadonnées et les taxonomies entre les référentiels dans le cadre du processus de transfert de contenu.

- **Exécutions à sec** : valide les mappages et les paramètres de transfert avant de déplacer le contenu dans le référentiel de destination.

- **Synchronisation planifiée** : exécute les transferts selon une planification récurrente, par exemple toutes les heures, tous les jours ou toutes les semaines.

- **Transformations personnalisées** : prend en charge une logique de transformation supplémentaire, le cas échéant, y compris JavaScript, les expressions régulières, les webhooks et le hachage de contenu.

## Référentiels pris en charge {#supported-repositories}

Le contenu peut être transféré entre Adobe et des référentiels tiers par le biais de passerelles source et de destination prises en charge.

Voici quelques exemples de référentiels pris en charge :

- Adobe Experience Manager Assets
- Adobe Content Platform
- Adobe Commerce
- Amazon S3
- Stockage d’objets blob Azure
- Box
- Dropbox
- Google Drive
- OneDrive
- WordPress
- Workfront
- Serveurs FTP et SFTP
- Partages de fichiers SMB

D’autres référentiels sont prévus pour les prochaines versions.

## Exemples de cas d’utilisation {#example-use-cases}

### Migrer le contenu dans un nouveau référentiel

Configurez une migration unique vers un nouveau système d’enregistrement à partir d’un ancien référentiel de gestion des ressources numériques ou de stockage dans le cloud. Examinez les mappages de métadonnées avec une exécution d’essai avant de transférer le contenu de production.

### Synchronisation des référentiels

Conservez la synchronisation du contenu entre l’espace de stockage cloud et la gestion des ressources numériques en configurant un transfert récurrent qui traite uniquement les ressources nouvellement ajoutées ou modifiées.

### Rationaliser votre supply chain de contenu

Réduisez les déplacements manuels de contenu en automatisant les transferts entre les référentiels utilisés tout au long du cycle de vie du contenu de votre entreprise.

## Quand utiliser cette fonctionnalité ? {#when-to-use-ai-powered-content-onboarding-content-supply-chain-automation}

Cette fonctionnalité est adaptée aux éléments suivants :

- Migrations de contenu ponctuelles.
- Intégration de nouveaux systèmes d’enregistrement.
- Synchronisation récurrente entre les référentiels.
- Mappage des métadonnées et de la taxonomie lors des transferts de contenu.
- Automatisation du déplacement du contenu entre plusieurs référentiels.

## Quand ne pas utiliser cette fonctionnalité {#when-not-to-use-ai-powered-content-onboarding-content-supply-chain-automation}

Cette fonctionnalité n’est pas destinée à :

- Automatisation générale des workflows ou des processus métier.
- Pipelines ETL de données client ou Analytics.
- Propagation en temps réel pilotée par les événements.
- Diffusion continue d’octets entre les référentiels.




