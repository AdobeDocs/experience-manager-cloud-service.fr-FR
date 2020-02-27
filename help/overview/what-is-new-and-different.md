---
title: Nouveautés et différences - Adobe Experience Manager en tant que service Cloud
description: 'Nouveautés et différences - Adobe Experience Manager (AEM) en tant que service Cloud. '
translation-type: tm+mt
source-git-commit: 160db0dabc99eccdef5bd579f8ccc26a861b1380

---


# Nouveautés et différences {#what-is-new-and-what-is-different}

Depuis de nombreuses années, AEM est disponible dans les deux cas :

* Local

* en tant que service géré

Il existe des différences intrinsèques entre ces approches précédentes et AEM en tant que service Cloud :

* [Architecture](#architecture)
* [Mises à niveau](#upgrades)
* [Cloud Manager](#cloud-manager)
* [Intégration](#onboarding)
* [Développement](#developing)
* [Opérations et performances](#operations-and-performance)
* [Gestion d’identité](#identity-management)
* [Interface utilisateur de création](#authoring-user-interface)
* [AEM Sites](#aem-sites)
* [AEM Assets](#aem-assets)

>[!NOTE]
>
>Ces aperçus ne sont pas exhaustifs, mais ils ont pour but de fournir une introduction.

>[!NOTE]
>
>Pour plus d’informations sur les versions sur site et de service géré, reportez-vous à la documentation définie pour [AEM 6.5](https://helpx.adobe.com/support/experience-manager/6-5.html).

## Architecture {#architecture}

>[!NOTE]
>
>Pour plus de détails, voir [Architecture](/help/core-concepts/architecture.md).

Le service AEM en tant que service cloud dispose désormais des fonctionnalités suivantes :

* Architecture dynamique avec un nombre variable d’images AEM.

![Architecture](assets/introduction-03.png "dynamiqueArchitecture dynamique")

Cette architecture :

* Est mis à l’échelle en fonction du trafic *réel* et de l’activité *réelle* .

* Comporte des instances individuelles qui ne s’exécutent que lorsque cela est nécessaire.

* Utilise des applications modulaires.

* Comporte une grappe d’auteurs par défaut ; cela évite les temps d’arrêt pour les tâches de maintenance.

Cela permet la mise à l’échelle automatique pour divers modèles d’utilisation :

![Mise à l’échelle automatique pour divers](assets/introduction-04.png "modèles d’utilisationMise à l’échelle automatique pour divers modèles d’utilisation")


## Mises à niveau {#upgrades}

>[!NOTE]
>
>Pour plus d’informations, reportez-vous à la section Présentation du [déploiement](/help/implementing/deploying/overview.md).

AEM en tant que service Cloud utilise désormais l’intégration continue et la diffusion continue (CI/CD) pour vous assurer que vos projets sont entièrement à jour. Cela signifie que toutes les opérations de mise à niveau sont entièrement automatisées. Par conséquent, ne nécessitent aucune interruption de service pour les utilisateurs.

Adobe prend en charge de manière proactive la mise à jour de toutes les instances opérationnelles du service vers la dernière version de la base de code AEM :

* Correctifs :

   * Peut être publié quotidiennement.

   * Les instances sont fréquemment mises à jour avec les derniers correctifs. Lorsque des modifications sont appliquées régulièrement, l’impact est incrémentiel, réduisant ainsi l’impact sur votre service.

   * La plupart des mises à jour sont effectuées pour des raisons de maintenance et de sécurité.

* Nouvelles fonctionnalités:

   * Sera publié selon un calendrier mensuel prévisible.

>[!NOTE]
>
>Pour plus d’informations, voir Architecture [de](/help/core-concepts/architecture.md#deployment-architecture)déploiement.

## Cloud Manager {#cloud-manager}

Adobe Cloud Manager fait partie intégrante de l’approche de mise à niveau continue d’AEM en tant que service Cloud, dans la mesure où il contrôle toutes les mises à jour apportées à vos instances - ceci est obligatoire.

Les mises à jour peuvent être déclenchées par Adobe lorsqu’une nouvelle version du service cloud est disponible. Vous pouvez également déclencher les mises à jour de votre application à l’aide des pipelines fournis par Cloud Manager.

Cloud Manager est :

* utilisé pour gérer les programmes et environnements AEM,

* un composant essentiel d’AEM en tant que service Cloud ; chaque nouveau client est d’abord mis en service pour l’accès à Cloud Manager,

* point d’entrée unique pour votre personnel d’exploitation et de développement.

Plus précisément, le nombre et le type de programmes AEM pouvant être créés à partir de Cloud Manager sont dérivés de :

* du contrat de licence client,

* provenant d’acteurs internes lorsque AEM en tant que service Cloud est utilisé pour l’activation ou la formation,

* issus de processus externes, tels que des tests, lancés à partir d’Adobe.com.

Cloud Manager a évolué en tant que portail en libre-service où les principaux composants d’AEM en tant que service Cloud peuvent être créés et configurés :

* Création et gestion de nouveaux programmes.

* Création et gestion des environnements AEM au sein de ces programmes.

* Création et gestion des pipelines pour le déploiement du code client et de la configuration associée dans un environnement spécifique.

* Être informé des événements de cycle de vie importants pour ces composants (par exemple, les mises à jour de produits).

Actuellement, Cloud Manager est en mesure de créer des environnements dans 3 régions géographiques (avec plus de régions suivantes) :

* US (Est)

* EMEA (Pays-Bas)

* APAC (Australie)

## Intégration {#onboarding}

>[!NOTE]
>
>Pour plus d&#39;informations, reportez-vous à la page [Intégration](/help/onboarding/home.md).

Le démarrage et la gestion d’un projet AEM sont simples lorsque vous utilisez AEM en tant que service Cloud en tant qu’Adobe responsable de nombreux aspects :

* Les images AEM de base sont optimisées pour des cas d’utilisation spécifiques.

* La plupart des tâches de configuration manuelle ont été rendues redondantes.

Elle est également très différente de ce qu&#39;elle est aujourd&#39;hui :

* une phase d&#39;évaluation pour s&#39;assurer que toutes les conditions préalables ont été remplies; par exemple :

   * Conditions légales

   * Accords contractuels

   * Conditions techniques requises pour tout contenu et/ou code existants personnalisés par le client

* Conditions requises pour le déploiement :

   * Mises à jour du code ; toutes les applications client développées pour une version précédente d’AEM devront être examinées et éventuellement mises à jour.

   * Migration de contenu

## Développement {#developing}

>[!NOTE]
>
>Pour plus de détails, vous pouvez commencer avec [les lignes directrices](/help/implementing/developing/introduction/development-guidelines.md) et le [développement - le didacticiel](/help/implementing/developing/introduction/develop-wknd-tutorial.md)WKND.

La nouvelle architecture prenant en charge AEM en tant que service Cloud implique quelques modifications clés de l’expérience globale du développeur. L’un des principaux objectifs d’AEM en tant que service Cloud consiste à permettre aux clients expérimentés (ayant utilisé AEM sur site ou dans le contexte des services gérés Adobe) de migrer vers AEM en tant que service Cloud le plus rapidement possible, sans avoir à réécrire le gros de leur code personnalisé. Toutefois, certains ajustements pourraient encore être nécessaires.

### Développement du cloud {#aem-as-a-cloud-service-developing-cloud-development}

Pour que les applications AEM existantes s’exécutent sur AEM en tant que service Cloud, les étapes suivantes sont attendues :

* Le code et la configuration de l’application doivent être stockés dans le référentiel de code Git du programme Cloud Manager associé.
* Le code et la configuration de l’application doivent être compatibles avec la dernière version de l’image AEM de base (qui peut changer quotidiennement).
   * L’application cliente doit être créée et déployée à l’aide du pipeline Cloud Manager associé à l’environnement Cloud Manager.
* L’application cliente doit transmettre toutes les portes de qualité du code, de sécurité et de performances appliquées dans le pipeline.
* Les images créées pour l’application cliente doivent être déployées par le pipeline Cloud Manager.

Ce processus est communément appelé développement Cloud-premier. Puisque la durée de bout en bout doit durer des minutes (de 20 à 50 selon la complexité de l’application), il est nécessaire d’adopter des méthodologies de développement rapide avant que les modifications en attente du code et de la configuration ne soient tentées dans le cloud.

La console Web, où sont gérés les lots OSGI et leur configuration associée, et qui faisait auparavant partie d’AEM Quickstart, n’est plus directement accessible aux utilisateurs d’un environnement de service cloud AEM. Cette interface est toujours accessible en lecture seule à l’aide d’une nouvelle console de développement. Avec cette console, les développeurs peuvent sélectionner et se connecter directement à n’importe quel noeud particulier d’un service d’auteur ou de publication, puis accéder aux zones bloquées par défaut.

>[!NOTE]
>
>Voir aussi Configuration [OSGi](/help/implementing/deploying/overview.md#osgi-configuration)

Les développeurs ont également besoin d’accéder rapidement aux fichiers journaux des différents environnements. Avec AEM en tant que service Cloud, les fichiers journaux des différents noeuds des noeuds d’auteur et de publication sont rendus disponibles via Cloud Manager, sous la forme de fichiers pouvant être téléchargés ou via des API.

En raison de la séparation claire du code et du contenu, les développeurs peuvent utiliser un processus particulier pour mettre à jour le contenu dans le cadre d’un déploiement. Les cas d’utilisation courants du contenu modifiable sont les suivants :

* Contenu *par défaut* standard faisant partie du projet client (dossiers, modèles, processus, etc.)

* Rechercher des définitions d’index

* ACL et autorisations

* Utilisateurs du service et groupes d’utilisateurs

### Développement local {#aem-as-a-cloud-service-developing-local-development}

Afin de prendre en charge les itérations et le développement rapides, il est également possible de développer des applications AEM en dehors d’AEM en tant que contexte de service Cloud. A cette fin, les artefacts suivants sont mis à la disposition des développeurs :

* AEM as a Cloud Service QuickStart : un programme d’installation autonome `.jar` basé sur la dernière base de code AEM, avec la même surface fonctionnelle et API.

* Le SDK AEM as a Cloud Service Dispatcher : un processus basé sur les images pour tester et valider localement les configurations du répartiteur

>[!NOTE]
>
>Notez que Cloud QuickStart n’autorise pas toutes les fonctionnalités des sites AEM et des ressources AEM. Il s&#39;agit d&#39;un environnement d&#39;auteur simple où la majorité des extensions peuvent être développées et testées.

## Opérations et performances {#operations-and-performance}

>[!NOTE]
>
>Pour plus d’informations, commencez par [Sauvegarde](/help/operations/backup.md), [Indexation](/help/operations/indexing.md) et [autres tâches de maintenance](/help/operations/maintenance.md).

Avec AEM en tant que service Cloud, ces opérations sont automatisées de sorte que toute interruption de service n’est plus nécessaire.

Dans ces domaines :

* De nombreuses tâches ont été automatisées.

* Les topologies sont optimisées pour une résilience et une efficacité optimales; par exemple, la réplication binaire est la réplication par défaut.

* Les tâches à chargement lourd, telles que les files d’attente, les tâches et les tâches de traitement en masse ont été déplacées hors de l’instance principale d’AEM pour être gérées par des micro-services partagés et dédiés.

Les opérations pour AEM en tant que service Cloud sont également prises en charge par une nouvelle infrastructure de surveillance, de création de rapports et d’alertes. Cela permet aux SRE d’Adobe (Ingénieurs de fiabilité du site) de maintenir le service en bonne santé de manière proactive. Les différents éléments de l&#39;architecture sont équipés d&#39;une variété de contrôles de santé. Si, pour une raison quelconque, un noeud particulier de l&#39;architecture est jugé malsain, il est retiré du service et remplacé silencieusement par un nouveau noeud sain.

## Gestion d’identité {#identity-management}

>[!NOTE]
>
>Pour plus d&#39;informations, voir [Sécurité - Support](/help/security/ims-support.md)IMS.

Une modification majeure apportée à AEM en tant que service Cloud est l’utilisation entièrement intégrée des ID Adobe pour accéder au niveau Auteur.

Pour ce faire, vous devez utiliser la console [d’administration](https://helpx.adobe.com/enterprise/using/admin-console.html) Adobe pour gérer les utilisateurs et les groupes d’utilisateurs. Les comptes utilisateur permettent à vos utilisateurs d’accéder aux produits et services Adobe, dans la mesure où les informations de profil utilisateur sont centralisées dans le système de gestion des identités Adobe (IMS) pour être partagées entre tous les services cloud. Une fois l’accès attribué à AEM, les comptes d’utilisateurs peuvent être référencés dans AEM en tant que service Cloud (comme auparavant) ; par exemple, pour définir des rôles et des autorisations à partir des interfaces utilisateur d’AEM Security.

Cela combine les avantages suivants :

* Utilisation d’Adobe Identity Management System (IMS) pour permettre l’authentification unique dans toutes les applications Adobe Cloud.

* Préférences utilisateur restantes locales pour chaque instance particulière d’AEM en tant que service Cloud.

## Interface utilisateur de création {#authoring-user-interface}

>[!NOTE]
>
>Pour plus de détails, la gestion [de base](/help/sites-cloud/authoring/getting-started/basic-handling.md) est un bon point de départ.

Les principes de base de l’interface utilisateur de création, tant pour les sites que pour les ressources, seront très familiers avec quiconque a utilisé AEM dans le passé.

La principale différence réside dans le fait que l’interface utilisateur est uniquement tactile ; l’interface utilisateur classique n’est plus disponible. Dans le cas contraire, les principes de base restent inchangés, avec de petits changements apparents.

## AEM Sites {#aem-sites}

Adobe Experience Manager Sites as a Cloud Service vous permet de fournir à vos clients des expériences personnalisées basées sur le contenu, en combinant la puissance du système de gestion de contenu AEM à la gestion des ressources numériques AEM.

Pour plus d&#39;informations, consultez la présentation des [modifications apportées aux sites](/help/sites-cloud/sites-cloud-changes.md).

## AEM Assets {#aem-assets}

Adobe Experience Manager Assets as a Cloud Service offre une solution SaaS native du cloud pour que les entreprises puissent non seulement exécuter rapidement et efficacement leurs opérations de gestion des ressources numériques et de médias dynamiques, mais aussi utiliser des fonctionnalités intelligentes de nouvelle génération, telles que l’IA/ML, à partir d’un système toujours à jour, toujours disponible et toujours en cours d’apprentissage.

L’offre de ressources inclut le traitement des ressources de nouvelle génération dans le cloud, ainsi que l’assimilation et la recherche de ressources hautes performances.

Pour plus d’informations, reportez-vous à la section [Présentation et présentation des ressources en tant que service](/help/assets/overview.md)Cloud.
