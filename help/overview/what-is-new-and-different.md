---
title: Ce qui est différent et ce qui est nouveau - Adobe Experience Manager en tant que Cloud Service
description: 'Différent et Nouveautés - Adobe Experience Manager (AEM) en tant que Cloud Service. '
translation-type: tm+mt
source-git-commit: e381807d7c199113689304e9481dfe2022ee5f93
workflow-type: tm+mt
source-wordcount: '1809'
ht-degree: 10%

---


# Nouveautés et différences {#what-is-new-and-what-is-different}

Depuis de nombreuses années, AEM est disponible dans les deux cas :

* Local

* en tant que service géré

Il existe des différences intrinsèques entre ces approches précédentes et AEM en tant que Cloud Service :

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
>Ces aperçus ne sont pas exhaustifs, mais visent à fournir une introduction.

>[!NOTE]
>
>Pour plus d’informations sur les versions sur site et de service géré, voir la documentation définie pour [AEM 6.5](https://helpx.adobe.com/fr/support/experience-manager/6-5.html).

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


## Mises à niveau {#upgrades}

>[!NOTE]
>
>Pour plus d’informations, voir l’introduction [](/help/implementing/deploying/overview.md)du déploiement.

En tant que Cloud Service, AEM utilise désormais l’intégration continue et la Diffusion continue (CI/CD) pour s’assurer que vos projets sont entièrement à jour. Cela signifie que toutes les opérations de mise à niveau sont entièrement automatisées. Par conséquent, il n’est pas nécessaire d’interrompre le service pour les utilisateurs.

Adobe prend en charge de manière proactive la mise à jour de toutes les instances opérationnelles du service vers la dernière version de la base de code AEM :

* Correctifs :

   * Peut être publié quotidiennement.

   * Les instances sont fréquemment mises à jour avec les derniers correctifs de bogues. Les modifications étant appliquées régulièrement, l’impact est incrémentiel, ce qui réduit l’impact sur votre service.

   * La plupart des mises à jour sont effectuées pour des raisons de maintenance et de sécurité.

* Nouvelles fonctionnalités:

   * Sera publié selon un calendrier mensuel prévisible.

>[!NOTE]
>
>Pour plus d’informations, voir Architecture [de](/help/core-concepts/architecture.md#deployment-architecture)déploiement.

## Cloud Manager {#cloud-manager}

Adobe Cloud Manager fait partie intégrante de l’approche de mise à niveau continue d’AEM en tant que Cloud Service, dans la mesure où il contrôle toutes les mises à jour apportées à vos instances - ceci est obligatoire.

Les mises à jour peuvent être déclenchées par Adobe lorsqu’une nouvelle version du service cloud est disponible. Vous pouvez également déclencher les mises à jour de votre application à l’aide des pipelines fournis par Cloud Manager.

Cloud Manager est :

* utilisé pour gérer les programmes et environnements AEM,

* un composant essentiel d’AEM en tant que Cloud Service ; chaque nouveau client est d’abord configuré pour l’accès à Cloud Manager,

* point d’entrée unique pour votre personnel d’exploitation et de développement.

Plus précisément, le nombre et le type de programmes AEM pouvant être créés à partir de Cloud Manager sont dérivés de :

* du contrat de licence client,

* provenant d’acteurs internes lorsque AEM en tant que Cloud Service est utilisé pour l’activation ou la formation,

* provenant de processus externes tels que les essais ont commencé à partir de Adobe.com.

Cloud Manager a évolué en tant que portail en libre-service où les principaux composants d’AEM en tant que Cloud Service peuvent être créés et configurés :

* Création et gestion de nouveaux programmes.

* Création et gestion des environnements AEM dans ces programmes.

* Création et gestion des pipelines pour le déploiement du code client et de la configuration associée sur un environnement spécifique.

* Être informé des événements de cycle de vie importants de ces composants (par exemple, les mises à jour de produits).

Actuellement, Cloud Manager est en mesure de créer des environnements dans 3 régions géographiques (avec plus de régions suivantes) :

* États-Unis (Est)

* EMEA (Pays-Bas)

* APAC (Australie)

## Intégration {#onboarding}

>[!NOTE]
>
>Pour plus d’informations, voir [Intégration](/help/onboarding/home.md).

Le démarrage et la gestion d’un projet AEM sont simples lorsque vous utilisez AEM en tant que service Cloud car Adobe est responsable de nombreux aspects :

* Les images AEM de base sont optimisées pour des cas d’utilisation spécifiques.

* La plupart des tâches de configuration manuelle ont été rendues redondantes.

Elle est également très différente de celle qui existe actuellement :

* une phase d&#39;évaluation pour s&#39;assurer que toutes les conditions préalables ont été remplies ; par exemple :

   * Exigences juridiques

   * Accords contractuels

   * Exigences techniques pour tout contenu et/ou code existant personnalisé par le client

* Conditions requises pour le déploiement :

   * Mises à jour du code ; toutes les applications client développées pour une version précédente d’AEM devront être revues et éventuellement mises à jour.

   * Migration du contenu

## Développement {#developing}

>[!NOTE]
>
>Pour plus de détails, vous pouvez début avec les lignes directrices [](/help/implementing/developing/introduction/development-guidelines.md) de développement et [Développement - le tutoriel](/help/implementing/developing/introduction/develop-wknd-tutorial.md)WKND.

La nouvelle architecture prenant en charge AEM en tant que Cloud Service implique quelques modifications clés de l’expérience globale du développeur. L’un des principaux objectifs d’AEM en tant que Cloud Service est de permettre aux clients expérimentés (ayant utilisé AEM sur site ou dans le contexte des Adobes Managed Services) de migrer vers AEM en tant que Cloud Service le plus rapidement possible, sans avoir à réécrire la majeure partie de leur code personnalisé. Toutefois, certains ajustements pourraient encore être nécessaires.

### Développement du cloud {#aem-as-a-cloud-service-developing-cloud-development}

Pour que les applications AEM existantes s’exécutent sur AEM en tant que Cloud Service, les étapes suivantes sont attendues :

* Le code et la configuration de l’application doivent être stockés dans le référentiel de code Git du programme Cloud Manager associé.
* Le code et la configuration de l’application doivent être compatibles avec la dernière version de l’image AEM de base (qui peut changer quotidiennement).
   * L’application cliente doit être créée et déployée à l’aide du pipeline Cloud Manager associé à l’environnement Cloud Manager.
* L&#39;application cliente doit transmettre toutes les barrières de qualité, de sécurité et de performances du code appliquées dans le pipeline.
* Les images créées pour l’application cliente doivent être déployées par le pipeline Cloud Manager.

Ce processus est généralement appelé développement Cloud initial. Comme la durée de bout en bout doit prendre des minutes (de 20 à 50 selon la complexité de l&#39;application), il est nécessaire d&#39;adopter des méthodologies de développement rapide avant que le code en attente et les modifications de configuration ne soient tentées dans le cloud.

La console Web, dans laquelle les lots OSGI et leur configuration associée sont gérés, et qui faisait auparavant partie d’AEM Quickstart, n’est plus directement accessible aux utilisateurs d’AEM en tant qu’environnement Cloud Service. Cette interface est toujours accessible en mode lecture seule à l’aide d’une nouvelle console de développement. Avec cette console, les développeurs peuvent sélectionner et se connecter directement à n’importe quel noeud particulier d’un service d’auteur ou de publication, puis accéder aux zones bloquées par défaut.

>[!NOTE]
>
>Voir aussi Configuration [OSGi](/help/implementing/deploying/overview.md#osgi-configuration)

Une autre exigence courante pour les développeurs est l&#39;accès rapide aux fichiers journaux des différents environnements. Avec AEM en tant que Cloud Service, les fichiers journaux des différents noeuds des noeuds d’auteur et de publication sont disponibles via Cloud Manager, sous la forme de fichiers pouvant être téléchargés ou via des API.

En raison de la séparation claire du code et du contenu, les développeurs peuvent utiliser un processus particulier de mise à jour du contenu dans le cadre d’un déploiement. Les cas d’utilisation types pour le contenu mutable sont les suivants :

* Contenu *par défaut* standard faisant partie du projet client (dossiers, modèles, workflows, etc.)

* Rechercher les définitions d&#39;index

* Listes ACL et autorisations

* Utilisateurs du service et groupes d’utilisateurs

### Développement local {#aem-as-a-cloud-service-developing-local-development}

Afin de prendre en charge les itérations et le développement rapides, il est également possible de développer des applications AEM en dehors d’AEM en tant que contexte Cloud Service. À cette fin, les artefacts suivants sont mis à la disposition des développeurs :

* AEM en tant que Cloud Service QuickStart : un programme d’installation autonome `.jar` basé sur la dernière base de code AEM, avec la même surface fonctionnelle et d’API.

* AEM en tant que SDK de Dispatcher Cloud Service : un processus basé sur les images pour tester et valider localement les configurations de Dispatcher

>[!NOTE]
>
>Notez que Cloud QuickStart ne prend pas en charge toutes les fonctionnalités AEM Sites et AEM Assets. Il s&#39;agit d&#39;un simple environnement d&#39;auteur où la majorité des extensions peuvent être développées et testées.

## Opérations et performances {#operations-and-performance}

>[!NOTE]
>
>Pour plus d’informations, commencez par [Sauvegarde](/help/operations/backup.md), [Indexation](/help/operations/indexing.md) et [autres tâches de maintenance](/help/operations/maintenance.md).

Avec AEM en tant que Cloud Service, ces opérations sont automatisées de sorte que toute interruption de service n’est plus nécessaire.

Dans ces domaines :

* De nombreuses tâches ont été automatisées.

* Les topologies sont optimisées pour une résilience et une efficacité optimales ; par exemple, la réplication binaire est la réplication par défaut.

* Les tâches à charge importante, telles que les files d’attente, les tâches et les tâches de traitement en masse, ont été déplacées hors de l’instance AEM principale pour être gérées par des micro-services partagés et dédiés.

Les opérations pour AEM en tant que Cloud Service sont également prises en charge par une nouvelle infrastructure de surveillance, de rapports et d’alerte. Cela permet aux ingénieurs Adobe SRE (Site Reliability Engineers) de maintenir le service en bonne santé de manière proactive. Les différents éléments de l&#39;architecture sont équipés d&#39;une variété de contrôles de santé. Si, pour une raison quelconque, un noeud particulier de l&#39;architecture est jugé malsain, il est retiré du service et remplacé en silence par un nouveau noeud sain.

## Gestion d’identité {#identity-management}

>[!NOTE]
>
>Pour plus de détails, voir [Sécurité - Soutien](/help/security/ims-support.md)IMS.

Un changement majeur apporté à AEM en tant que Cloud Service est l’utilisation entièrement intégrée des ID Adobe pour l’accès au niveau auteur.

Pour ce faire, vous devez utiliser la console [d’administration](https://helpx.adobe.com/fr/enterprise/using/admin-console.html) Adobe pour gérer les utilisateurs et les groupes d’utilisateurs. Les comptes d’utilisateurs permettent à vos utilisateurs d’accéder aux produits et services Adobe, dans la mesure où les informations sur les profils d’utilisateurs sont centralisées dans le système Adobe Identity Management (IMS) afin d’être partagées sur tous les services Cloud. Une fois que l’accès à AEM est attribué, les comptes d’utilisateurs peuvent être référencés dans AEM en tant que Cloud Service (comme auparavant) ; par exemple, pour la définition de rôles et d’autorisations à partir des interfaces utilisateur d’AEM Security.

Cela permet de combiner les avantages suivants :

* Utilisation du système Adobe Identity Management System (IMS) pour fournir une authentification unique sur toutes les applications Adobe cloud.

* Préférences utilisateur restantes locales pour chaque instance particulière d’AEM en tant que Cloud Service.

## Interface utilisateur de création {#authoring-user-interface}

>[!NOTE]
>
>Pour plus de détails, la gestion [](/help/sites-cloud/authoring/getting-started/basic-handling.md) de base est un bon point de départ.

Les principes de base de l’interface utilisateur de création, tant pour les sites que pour les ressources, seront très familiers avec quiconque a utilisé AEM dans le passé.

La principale différence réside dans le fait que l’interface utilisateur est uniquement tactile ; l’interface utilisateur classique n’est plus disponible. Sinon, les bases restent inchangées, avec seulement de petits changements apparents.

## AEM Sites {#aem-sites}

Adobe Experience Manager Sites en tant que Cloud Service vous permet de fournir à vos clients des expériences personnalisées basées sur le contenu, en combinant la puissance d’AEM Gestion de contenu System avec AEM Digital Asset Management.

Pour plus d&#39;informations, reportez-vous à l&#39;aperçu des [modifications apportées aux sites](/help/sites-cloud/sites-cloud-changes.md).

## AEM Assets {#aem-assets}

Adobe Experience Manager Assets en tant qu&#39;offres Cloud Service est une solution SaaS native de cloud pour que les entreprises puissent non seulement effectuer leurs opérations Digital Asset Management et Dynamic Media avec rapidité et impact, mais aussi utiliser des fonctionnalités intelligentes de prochaine génération, telles que l&#39;IA/ML, à partir d&#39;un système toujours à jour, toujours disponible et toujours en cours d&#39;apprentissage.

L’offre de ressources inclut le traitement des ressources de nouvelle génération dans le cloud et la recherche et l’assimilation des ressources hautes performances.

Pour plus d’informations, voir [Présentation et présentation des ressources en tant que Cloud Service](/help/assets/overview.md).

## Premiers pas avec Adobe Experience Manager as a Cloud Service {#getting-to-know-aem-as-cloud-service}

Pour plus d’informations, voir :

* [Présentation d’Adobe Experience Manager as a Cloud Service](/help/overview/introduction.md)
* [Architecture](/help/core-concepts/architecture.md) d’Adobe Experience Manager as a Cloud Service
* [Modifications notables apportées à AEM en tant que Cloud Service (notes de mise à jour)](/help/release-notes/aem-cloud-changes.md)
* [Modifications notables d’AEM Sites en tant que as a Cloud Service](/help/sites-cloud/sites-cloud-changes.md)
* [Modifications notables apportées à AEM Assets as a Cloud Service](/help/assets/assets-cloud-changes.md)
* [Présentation du AEM Assets en tant que Cloud Service](/help/assets/overview.md)
* [Tutoriels sur Adobe Experience Manager as a Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/overview.html)
