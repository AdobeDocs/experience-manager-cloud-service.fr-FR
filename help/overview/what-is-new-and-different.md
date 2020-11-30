---
title: Nouveautés et différences – Adobe Experience Manager as a Cloud Service
description: 'Nouveautés et différences – Adobe Experience Manager (AEM) as a Cloud Service. '
translation-type: tm+mt
source-git-commit: 52e8cf1e3fb503c1d222a9543cfc1ddfe87132b6
workflow-type: tm+mt
source-wordcount: '1876'
ht-degree: 100%

---


# Nouveautés et différences {#what-is-new-and-what-is-different}

Depuis de nombreuses années, AEM est disponible sous deux formes :

* On-Premise

* As a Managed Service

Il existe des différences intrinsèques entre ces approches antérieures et AEM as a Cloud Service :

* [Architecture](#architecture)
* [Mises à niveau](#upgrades)
* [Cloud Manager](#cloud-manager)
* [Intégration](#onboarding)
* [Développement](#developing)
* [Opérations et performances](#operations-and-performance)
* [Identity Management](#identity-management)
* [Interface utilisateur de création](#authoring-user-interface)
* [AEM Sites](#aem-sites)
* [AEM Assets](#aem-assets)

>[!NOTE]
>
>Ces présentations non exhaustives constituent une simple introduction.

>[!NOTE]
>
>Pour plus d’informations sur les versions On-Premise et Managed Service, consultez la documentation relative à [AEM 6.5](https://helpx.adobe.com/fr/support/experience-manager/6-5.html).

## Architecture {#architecture}

>[!NOTE]
>
>Pour plus de détails, voir [Architecture](/help/core-concepts/architecture.md).

AEM as a Cloud Service présente désormais les caractéristiques suivantes :

* Une architecture dynamique avec un nombre variable d’images AEM.

![Architecture dynamique](assets/introduction-03.png "Architecture dynamique")

Cette architecture :

* est mise à l’échelle en fonction du trafic *réel* et de l’activité *réelle* ;

* comporte des instances individuelles qui ne s’exécutent que lorsque cela s’avère nécessaire ;

* utilise des applications modulaires ;

* comprend un cluster d’auteur par défaut, ce qui permet d’éviter les temps d’arrêt pour les tâches de maintenance.

Cela permet une mise à l’échelle automatique pour divers schémas d’utilisation :

![Mise à l’échelle automatique pour divers schémas d’utilisation](assets/introduction-04.png "Mise à l’échelle automatique pour divers schémas d’utilisation")


## Mises à jour d’AEM {#aem-updates}

>[!NOTE]
>Pour plus d’informations, voir [Mises à jour de la version d’AEM](/help/implementing/deploying/aem-version-updates.md).

AEM as a Cloud Service utilise maintenant l’intégration et la distribution continues (CI/CD) pour s’assurer que vos projets bénéficient de la version d’AEM la plus récente. Les instances de production et d’évaluation sont donc mises à jour à la dernière version d’AEM sans interruption de service pour les utilisateurs.

>[!NOTE]
> Si la mise à jour de l’environnement de production échoue, Cloud Manager restaure automatiquement l’environnement d’évaluation. Cette opération est effectuée automatiquement pour s’assurer qu’une fois la mise à jour terminée, les environnements d’évaluation et de production se trouvent sur la même version d’AEM.

Les mises à jour de la version d’AEM sont de deux types :

* **Mises à jour Push d’AEM**

   * Elles peuvent être publiées quotidiennement.
   * Il s’agit principalement de maintenance, notamment les derniers correctifs de bogues et les mises à jour de sécurité.

      Les modifications étant appliquées régulièrement, l’impact est incrémentiel, ce qui réduit l’incidence sur votre service.

* **Nouvelles mises à jour de fonctionnalités**

   * Elles sont publiées selon un calendrier mensuel prévisible.

## Cloud Manager {#cloud-manager}

Adobe Cloud Manager fait partie intégrante de l’approche de mise à niveau continue d’AEM as a Cloud Service, car il contrôle toutes les mises à jour appliquées à vos instances, ce qui est obligatoire.

Les mises à jour peuvent être déclenchées par Adobe lorsqu’une nouvelle version du service cloud est disponible. Vous pouvez également déclencher les mises à jour de votre application à l’aide des pipelines fournis par Cloud Manager.

Cloud Manager est :

* utilisé pour gérer les programmes et environnements AEM ;

* une composante essentielle d’AEM as a Cloud Service ; chaque nouveau client est d’abord configuré pour accéder à Cloud Manager ;

* le point d’entrée unique pour votre personnel d’exploitation et de développement.

Plus précisément, le nombre et le type des programmes AEM pouvant être créés à partir de Cloud Manager résultent, au choix :

* du contrat de licence client ;

* d’acteurs internes lorsqu’AEM as a Cloud Service est utilisé pour l’habilitation ou la formation,

* de processus externes, notamment d’essais lancés à partir d’Adobe.com.

Cloud Manager a évolué sous la forme d’un portail en libre-service où les principaux composants d’AEM as a Cloud Service peuvent être créés et configurés :

* Création et gestion de nouveaux programmes. Pour plus d’informations, consultez [Présentation des programmes et des types de programmes](/help/onboarding/getting-access-to-aem-in-cloud/understand-program-types.md).

* Création et gestion des environnements AEM dans ces programmes. Pour plus d’informations, consultez [Gestion des environnements](/help/implementing/cloud-manager/manage-environments.md).

* Création et gestion des pipelines pour le déploiement du code client et de la configuration associée dans un environnement spécifique. Pour plus d’informations, consultez [Configuration de votre pipeline CI-CD](/help/implementing/cloud-manager/configure-pipeline.md).

* Réception de notifications relatives à des événements de cycle de vie importants pour ces composants (par exemple, mises à jour de produits).

Actuellement, Cloud Manager est en mesure de créer des environnements dans 3 zones géographiques (avec d’autres régions dans le futur) :

* États-Unis (Est)

* EMEA (Pays-Bas)

* APAC (Australie)

>[!NOTE]
>Reportez-vous à [Accès à Experience Manager as a Cloud Service](/help/onboarding/getting-access-to-aem-in-cloud/navigation.md) pour prendre en main Cloud Manager dans AEM as a Cloud Service.

## Intégration {#onboarding}

>[!NOTE]
>
>Pour plus de détails, voir [Intégration](/help/onboarding/home.md).

Le démarrage et la gestion d’un projet AEM sont simples avec AEM as a Cloud service, car Adobe est responsable de nombreux aspects :

* Les images de référence d’AEM sont optimisées pour des cas d’utilisation spécifiques.

* La plupart des tâches de configuration manuelles ont été rendues redondantes.

Les opérations sont également très différentes du fait des éléments suivants :

* Une phase d’évaluation pour s’assurer que toutes les conditions préalables ont été remplies ; par exemple :

   * Exigences juridiques.

   * Accords contractuels.

   * Exigences techniques pour tout contenu et/ou code existant personnalisé par le client.

* Conditions requises pour le déploiement :

   * Mises à jour du code ; toutes les applications client développées pour une version précédente d’AEM devront être examinées et éventuellement mises à jour.

   * Migration du contenu

## Développement {#developing}

>[!NOTE]
>
>Pour plus de détails, vous pouvez consulter [Conseils de développement](/help/implementing/developing/introduction/development-guidelines.md) et [Développement – Tutoriel WKND](/help/implementing/developing/introduction/develop-wknd-tutorial.md).

La nouvelle architecture qui prend en charge AEM as a Cloud Service implique un certain nombre de changements clés dans l’expérience globale des développeurs. L’un des principaux objectifs d’AEM as a Cloud Service est de permettre aux clients expérimentés (qui ont utilisé AEM On-Premise ou dans le contexte des Adobe Managed Services) de migrer vers AEM as a Cloud Service le plus rapidement possible sans avoir à réécrire la majeure partie de leur code personnalisé. Toutefois, certains ajustements peuvent encore être nécessaires.

### Développement dans le cloud {#aem-as-a-cloud-service-developing-cloud-development}

Pour que les applications AEM existantes s’exécutent sur AEM as a Cloud Service, les étapes suivantes sont nécessaires :

* Le code et la configuration de l’application doivent être stockés dans le référentiel de code Git du programme Cloud Manager associé.
* Le code et la configuration de l’application doivent être compatibles avec la dernière version de l’image de référence d’AEM (qui peut changer quotidiennement).
   * L’application cliente doit être créée et déployée à l’aide du pipeline Cloud Manager associé à l’environnement Cloud Manager.
* L’application cliente doit satisfaire tous les points de contrôle de qualité, de sécurité et de performance du code appliqués dans le pipeline.
* Les images créées pour l’application cliente doivent être déployées par le pipeline Cloud Manager.

Ce processus est généralement appelé développement « Cloud-first », donnant la priorité au cloud sur tout autre environnement. Comme la durée de bout en bout peut se compter en minutes (de 20 à 50 selon la complexité de l’application), il est nécessaire d’adopter des méthodologies de développement rapide avant que les changements de code et de configuration en attente ne soient testés dans le cloud.

La console web, dans laquelle les lots OSGi et leur configuration associée sont gérés, précédemment intégrée au QuickStart AEM, n’est plus directement accessible pour les utilisateurs d’un environnement AEM as a Cloud Service. Cette interface reste accessible en mode lecture seule à l’aide d’une nouvelle console de développement. Avec cette console, les développeurs peuvent sélectionner un nœud particulier d’un service de création ou de publication, s’y connecter directement, puis accéder aux zones bloquées par défaut.

>[!NOTE]
>
>Voir également [Configuration OSGi](/help/implementing/deploying/overview.md#osgi-configuration)

L’accès rapide aux fichiers journaux des différents environnements est une autre exigence courante pour les développeurs. Avec AEM as a Cloud Service, les fichiers journaux des différents nœuds de création et de publication sont disponibles par le biais de Cloud Manager, sous la forme de fichiers pouvant être téléchargés ou à l’aide d’API.

En raison de la séparation stricte du code et du contenu, les développeurs peuvent utiliser un processus particulier de mise à jour du contenu dans le cadre d’un déploiement. Les cas d’utilisation standard des contenus modifiables sont les suivants :

* Contenu *par défaut* standard faisant partie du projet client (dossiers, modèles, workflows, etc.)

* Rechercher les définitions d’index

* Listes ACL et autorisations

* Utilisateurs du service et groupes d’utilisateurs

### Développement local {#aem-as-a-cloud-service-developing-local-development}

Pour assurer la rapidité des itérations et du développement, il est également possible de développer des applications AEM en dehors du contexte AEM as a Cloud Service. À cette fin, les artefacts suivants sont mis à la disposition des développeurs :

* QuickStart AEM as a Cloud Service : programme d’installation autonome basé sur `.jar`, correspondant à la base de code la plus récente d’AEM, avec les mêmes capacités fonctionnelles et API.

* SDK Dispatcher AEM as a Cloud Service : processus à base d’images servant à tester et valider localement les configurations du Dispatcher.

>[!NOTE]
>
>À noter que le QuickStart Cloud ne prend pas en charge toutes les fonctionnalités d’AEM Sites et AEM Assets. Il s’agit d’un simple environnement de création permettant de développer et créer la majorité des extensions.

## Opérations et performances {#operations-and-performance}

>[!NOTE]
>
>Pour plus d’informations, commencez par les sections [Sauvegarde](/help/operations/backup.md), [Indexation](/help/operations/indexing.md) et [Autres tâches de maintenance](/help/operations/maintenance.md).

Avec AEM as a Cloud Service, ces opérations sont automatisées pour éviter toute interruption de service.

Dans ces domaines :

* De nombreuses tâches ont été automatisées.

* Les topologies sont optimisées pour une résilience et une efficacité maximales ; par exemple, la réplication binaire est configurée par défaut.

* Les tâches traitant des charges importantes, comme les files d’attente, les traitements et les tâches de traitement massif, ont été déplacées hors de l’instance AEM principale pour être gérées par des micro-services partagés et dédiés.

Les opérations d’AEM as a Cloud Service sont également assurées par une nouvelle infrastructure de surveillance, de rapports et d’alerte. Ainsi, les ingénieurs de fiabilité du site (SRE) d’Adobe peuvent maintenir le service en bon état de fonctionnement de manière proactive. Les différents éléments de l’architecture sont dotés de différents contrôles de l’intégrité. Si, pour une raison quelconque, un nœud particulier de l’architecture est considéré comme dysfonctionnel, il est retiré du service et remplacé de manière transparente par un nouveau nœud en bon état de fonctionnement.

## Identity Management {#identity-management}

>[!NOTE]
>
>Pour plus de détails, voir [Sécurité – Prise en charge d’IMS](/help/security/ims-support.md).

L’un des changements majeurs apportés à AEM as a Cloud Service est l’utilisation entièrement intégrée des Adobe ID pour l’accès au niveau création.

Pour ce faire, vous devez utiliser [Adobe Admin Console](https://helpx.adobe.com/fr/enterprise/using/admin-console.html) afin de gérer les utilisateurs et les groupes d’utilisateurs. Les comptes d’utilisateurs permettent à vos utilisateurs d’accéder aux produits et services d’Adobe, dans la mesure où les informations de profil utilisateur sont centralisées dans Adobe IMS (Identity Management System) pour les partager avec tous les services cloud. Une fois l’accès à AEM accordé, les comptes d’utilisateurs peuvent être référencés dans AEM as a Cloud Service (comme auparavant) ; par exemple, pour définir des rôles et des autorisations à partir des interfaces utilisateur de sécurité d’AEM.

Cela a pour effet de combiner les avantages suivants :

* Utilisation d’Adobe Identity Management System (IMS) pour fournir une authentification unique à toutes les applications cloud d’Adobe.

* Préférences utilisateur restant locales pour chaque instance particulière d’AEM as a Cloud Service.

## Interface utilisateur de création {#authoring-user-interface}

>[!NOTE]
>
>Pour plus de détails, la section [Manipulation de base](/help/sites-cloud/authoring/getting-started/basic-handling.md) est un bon point de départ.

Les principes de base de l’interface utilisateur de création, tant pour Sites que pour Assets, seront très familiers pour toute personne ayant utilisé AEM dans le passé.

La principale différence réside dans le fait que l’interface utilisateur est exclusivement tactile ; la version classique n’est plus disponible. Les fondamentaux restent par ailleurs inchangés, avec seulement quelques changements mineurs visibles.

## AEM Sites {#aem-sites}

Adobe Experience Manager Sites as a Cloud Service vous permet de fournir à vos clients des expériences personnalisées basées sur le contenu, en combinant la puissance du système de gestion de contenu AEM à la gestion des ressources numériques AEM.

Pour plus d’informations, reportez-vous à l’aperçu proposé dans [Modifications apportées à Sites](/help/sites-cloud/sites-cloud-changes.md).

## AEM Assets {#aem-assets}

Adobe Experience Manager Assets as a Cloud Service offre aux entreprises une solution SaaS cloud native pour qu’elles puissent non seulement exécuter rapidement et efficacement leurs opérations de gestion des ressources numériques et Dynamic Media, mais aussi utiliser des fonctionnalités intelligentes de nouvelle génération, telles que l’intelligence artificielle ou l’apprentissage automatique, à partir d’un système toujours à jour, toujours disponible et qui apprend en permanence.

L’offre d’Assets comprend un traitement des ressources de nouvelle génération dans le cloud et des processus hautement performants de recherche et d’ingestion de ressources.

Pour plus d’informations, voir [Présentation et introduction d’Assets as a Cloud Service](/help/assets/overview.md).

## Premiers pas avec Adobe Experience Manager as a Cloud Service {#getting-to-know-aem-as-cloud-service}

Pour plus d’informations, voir :

* [Introduction à Adobe Experience Manager as a Cloud Service](/help/overview/introduction.md)
* [Architecture](/help/core-concepts/architecture.md) d’Adobe Experience Manager as a Cloud Service
* [Modifications notables apportées à AEM as a Cloud Service (notes de mise à jour)](/help/release-notes/aem-cloud-changes.md)
* [Modifications notables apportées à AEM Sites as a Cloud Service](/help/sites-cloud/sites-cloud-changes.md)
* [Modifications notables apportées à AEM Assets as a Cloud Service](/help/assets/assets-cloud-changes.md)
* [Introduction à AEM Assets as a Cloud Service](/help/assets/overview.md)
* [Tutoriels sur Adobe Experience Manager as a Cloud Service](https://docs.adobe.com/content/help/fr/experience-manager-learn/cloud-service/overview.html)
