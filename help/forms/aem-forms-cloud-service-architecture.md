---
title: Architecture d’Experience Manager [!DNL AEM Forms] as a Cloud Service
description: Découvrez l’architecture d’ [!DNL AEM Forms] as a Cloud Service pour en savoir plus sur l’évolutivité, la résilience et les performances de la plateforme.
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '1091'
ht-degree: 100%

---


# Architecture d’[!DNL AEM] as a Cloud {#architecture}

[!DNL AEM Forms] as a Cloud Service normalise l’architecture de déploiement pour tous les clients, dans le but de les libérer complètement des considérations d’architecture. Par exemple, alors que la nouvelle architecture d’AEM as a Cloud Service repose toujours sur le concept de micro-noyaux pour la persistance, les clients n’ont pas à s’inquiéter de savoir quel micro-noyau choisir. Les micro-noyaux utilisés du côté auteur et du côté publication sont propres à [!DNL AEM Cloud Service] et ne sont pas disponibles pour les clients avec des installations On-Premise.

AEM en tant que Cloud Service possède une architecture dynamique avec un nombre variable d’instances AEM. Il fournit des environnements de développement, d’évaluation, de production et de démonstration. Il propose des outils permettant d’administrer les instances AEM (Cloud Manager), de gérer les utilisateurs et les authentifications (Admin Console et système IMS), de configurer la mise en cache (Fast CDN) et l’environnement de développement natif au cloud. Pour plus d’informations sur l’architecture, voir [Une introduction à l’architecture de [!DNL Adobe Experience Manager as a Cloud Service]](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/core-concepts/architecture.html?lang=fr).

## Cloud Manager {#cloud-manager}

Cloud Manager est un composant essentiel pour [AEM en tant que Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/introduction.html?lang=fr). Chaque nouveau client d’[!DNL AEM Forms] as a Cloud Service est d’abord configuré pour l’accès à Cloud Manager. Cloud Manager est le point d’entrée unique pour les rôles de responsable des opérations et de développeurs de nos clients. Il s’agit de l’endroit à partir duquel les programmes et environnements AEM peuvent être gérés. Cloud Manager a évolué sous la forme d’un portail en libre-service où les principaux composants d’AEM as a Cloud Service peuvent être créés et configurés :

* Création et gestion des programmes
* Création et gestion des environnements AEM dans ces programmes
* Création et gestion des pipelines pour le déploiement du code client et de la configuration associée dans un environnement spécifique
* Obtention de notifications sur des événements de cycle de vie importants pour ces composants (par exemple, les mises à jour de produits)
Pour plus d’informations sur Cloud Manager, voir [Comprendre Adobe Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/cloud-manager/understand-cloud-manager-for-aem.html?lang=fr) et [Présentation de Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html?lang=fr).

## Utilisateurs et authentification {#users-and-authentication}

AEM as a Cloud Service inclut la prise en charge des instances AEM et de l’authentification basée sur Adobe IMS (Identity Management System) par Admin Console. Admin Console permet aux administrateurs de gérer de manière centralisée tous les utilisateurs d’Experience Cloud. Les utilisateurs et les groupes peuvent être affectés aux profils de produit associés à une instance AEM as a Cloud Service, ce qui leur permet de se connecter à cette instance. Pour plus d’informations sur les utilisateurs, l’authentification et l’accès à une instance d’AEM as a Cloud Service, voir [Prise en charge d’IMS pour [!DNL Adobe Experience Manager] as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=fr#introduction).

Divers rôles participent à un projet [!DNL AEM Forms] classique. Après vous être connecté à votre instance [!DNL AEM Forms] as a Cloud Service, vous pouvez [ajouter des utilisateurs dans la console d’administration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=fr) pour les rôles applicables à votre organisation ou projet et [affecter des utilisateurs à des groupes intégrés](forms-groups-privileges-tasks.md) afin de leur fournir les privilèges requis.

Pour connaître les différents groupes d’utilisateurs et les privilèges spécifiques à [!DNL AEM Forms] intégrés disponibles sur une instance [!DNL AEM Forms] as a Cloud Services, voir [Configuration, utilisateur, rôles et groupes](forms-groups-privileges-tasks.md).

## Expérience des développeurs {#developer-experience}

La nouvelle architecture qui prend en charge AEM as a Cloud Service apporte un certain nombre de changements clés dans l’expérience globale des développeurs. L’un des principaux objectifs des changements apportés à l’expérience des développeurs est d’autoriser la migration vers AEM as a Cloud Service le plus rapidement possible, avec peu de modifications du code personnalisé existant.

## Développement dans le cloud {#cloud-development}

Voici les instructions pour exécuter sans difficulté votre code existant dans l’environnement AEM as a Cloud Service :

* Stockez votre code et vos configurations dans le référentiel Git du programme Cloud Manager associé. La gestion et l’intégration du code avec CI/CD devient ainsi un jeu d’enfant.
* Rendez le code et la configuration de l’application compatibles avec les images [!DNL AEM Forms] de base. L’utilisation des dernières API permet de créer des applications plus rapides et sécurisées.
* Utilisez le pipeline Cloud Manager associé à l’environnement Cloud Manager pour créer et déployer des applications. Les dernières fonctionnalités et la correction de bogues pour [!DNL AEM Forms] as a Cloud Service sont ainsi intégrées à votre environnement.
* Vérifiez que vos applications personnalisées respectent toutes les exigences de qualité de code, de sécurité et de performances appliquées dans le pipeline. Cela permet de créer des applications sécurisées et plus performantes, ce qui améliore la satisfaction des clients. Vous pouvez toujours utiliser l’interface utilisateur de Cloud Manager pour ignorer certaines vérifications.
Ce processus est généralement appelé développement « Cloud-first », donnant la priorité au cloud sur tout autre environnement. [!DNL AEM Forms] as a Cloud Service fournit également un SDK pour prendre en charge le développement rapide avant que le code en attente et les modifications de configuration ne soient implémentés dans le cloud.
Certaines interfaces qui faisaient auparavant partie du QuickStart AEM ne sont plus disponibles pour les utilisateurs de l’environnement AEM as a Cloud Service. Par exemple, la console web dans laquelle les lots OSGI et leur configuration associée sont gérés. Le navigateur du référentiel de contenu de CRXDE Lite devient accessible uniquement sur les environnements hors production. Un sous-ensemble des fonctionnalités de la console web dont les développeurs ont besoin, notamment en termes de diagnostics et d’état, est disponible via une nouvelle console de développement.
En outre, l’un des besoins les plus courants des développeurs est l’accès rapide aux fichiers journaux des différents environnements. Avec [!DNL AEM Cloud Service], les fichiers journaux des différents nœuds des instances d’auteur et de publication sont disponibles par le biais de Cloud Manager, sous la forme de fichiers pouvant être téléchargés ou à l’aide d’API. En raison de la séparation stricte du code et du contenu, les développeurs peuvent utiliser un processus particulier de mise à jour du contenu dans le cadre d’un déploiement. Les cas d’utilisation standard des contenus modifiables sont les suivants :
* Contenu par défaut standard faisant partie du projet client (dossiers, modèles, processus, etc.)
* Rechercher les définitions d’index
* Listes ACL et autorisations
* Utilisateurs et groupes d’utilisateurs du service
Configurez votre environnement de développement, [configurez votre pipeline CI/CD](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=fr) et apprenez à [déployer votre code](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html?lang=fr) sur l’environnement.

## Développement local {#local-development}

Lorsque vous configurez un environnement [!DNL AEM Forms] as a Cloud Service, vous configurez des environnements de développement, d’évaluation et de production. En outre, définissez et configurez un environnement de développement local pour des itérations et un développement rapides. Vous pouvez télécharger et paramétrer le SDK AEM et l’archive des fonctionnalités de module complémentaire d’[!DNL AEM Forms] pour configurer un environnement de développement [!DNL Forms] as a Cloud Service local.  Pour obtenir des instructions détaillées, voir [Configuration d’un environnement de développement local](setup-local-development-environment.md).

## Débogage {#debugging}

AEM as a Cloud Service s’exécute sur une infrastructure cloud en libre-service et évolutive. Les développeurs AEM doivent donc comprendre et déboguer les différentes aspects d’AEM as a Cloud Service, depuis la génération et le déploiement jusqu’à l’obtention des détails sur l’exécution des applications AEM. Pour plus d’informations, voir [Débogage d’AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/overview.html?lang=fr).
