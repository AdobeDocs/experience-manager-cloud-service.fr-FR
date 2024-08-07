---
title: Pipelines CI/CD
description: Découvrez les pipelines CI/CD de Cloud Manager et comment les utiliser pour déployer votre code efficacement.
index: true
exl-id: 40d6778f-65e0-4612-bbe3-ece02905709b
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 585c934465215c48b9441a95c03e4c116859103e
workflow-type: tm+mt
source-wordcount: '1500'
ht-degree: 84%

---


# Pipeline CI/CD Cloud Manager {#intro-cicd}

Découvrez les pipelines CI/CD de Cloud Manager et comment les utiliser pour déployer votre code efficacement.

## Présentation {#introduction}

Un pipeline CI/CD dans Cloud Manager est un mécanisme permettant de créer du code à partir d’un référentiel source et de le déployer dans un environnement. Un pipeline peut-être déclenché par un événement, tel qu’une demande d’extraction provenant d’un référentiel de code source (c’est-à-dire un changement de code), ou selon une planification régulière pour correspondre à une cadence de publication.

Pour configurer un pipeline, vous devez :

* définir le déclencheur qui démarrera le pipeline ;
* définir les paramètres qui contrôlent le déploiement en production ;
* configurer les paramètres de test de performance.

Cloud Manager propose deux types de pipelines :

* [Pipelines de production](#prod-pipeline)
* [Pipelines hors production](#non-prod-pipeline)

![Types de pipelines](/help/implementing/cloud-manager/assets/configure-pipeline/ci-cd-config1.png)

## Pipelines de production {#prod-pipeline}

Un pipeline de production est un pipeline personnalisé qui comprend une série d’étapes orchestrées pour déployer le code source en vue d’une utilisation en production. Les étapes incluent d’abord la création, le conditionnement, le test, la validation et le déploiement dans tous les environnements d’évaluation. Par conséquent, un pipeline de production ne peut être ajouté qu’une fois qu’un ensemble d’environnements de production et d’évaluation est créé.

>[!TIP]
>
>Pour plus d’informations, consultez la section [Configuration d’un pipeline de production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md).

## Pipeline hors production {#non-prod-pipeline}

Un pipeline hors production sert principalement à exécuter des analyses de qualité du code ou à déployer le code source vers un environnement de développement.

>[!TIP]
>
>Pour plus d’informations, consultez la section [Configuration d’un pipeline hors production](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md).

## Sources de code {#code-sources}

Outre la dichotomie production et hors production, les pipelines peuvent être différenciés par le type de code qu’ils déploient.

* **[Pipelines full stack](#full-stack-pipeline)** - Déploient simultanément des versions de code front-end et back-end contenant une ou plusieurs applications de serveur AEM avec des configurations HTTPD/Dispatcher.
* **[Config Pipelines](#config-deployment-pipeline)** - Déployez rapidement les configurations pour des fonctionnalités telles que le transfert de journaux, les tâches de maintenance liées à la purge et diverses configurations de réseau de diffusion de contenu telles que les règles de filtrage du trafic (y compris les règles WAF), les transformations de requêtes et de réponses, les sélecteurs d’origine, les redirections côté client, les pages d’erreur, les clés de réseau de diffusion de contenu gérées par le client, les clés de purge et l’API de base.
   * Pour plus d’informations, consultez le document [Utilisation des pipelines de configuration](/help/operations/config-pipeline.md) .
* **[Pipelines front-end](#front-end)** - Déploient les versions de code front-end contenant une ou plusieurs applications d’interface utilisateur côté client.
* **[Pipelines de configuration de niveau web](#web-tier-config-pipelines)** - Déploient les configurations HTTPD/Dispatcher.

Ceux-ci sont décrits en détail plus loin dans ce document.

### Présentation des pipelines CI-CD dans Cloud Manager {#understand-pipelines}

Le tableau suivant résume les pipelines disponibles dans Cloud Manager et leur utilisation.

| Type de pipeline | Déploiement ou qualité du code | Code source | Objectif | Remarques |
|--- |--- |--- |---|---|
| Production ou hors production | Déploiement | Full stack | Déploie simultanément des versions de code front-end et back-end avec des configurations HTTPD/Dispatcher. | Lorsque le code front-end doit être déployé simultanément avec le code de serveur AEM.<br>Lorsque les pipelines front-end ou les pipelines de configuration de niveau web n’ont pas encore été adoptés. |
| Production ou hors production | Déploiement | Front-end | Déploie une version de code front-end contenant une ou plusieurs applications d’interface utilisateur côté client. | Prise en charge de plusieurs pipelines front-end simultanés<br>Beaucoup plus rapide que les déploiements full stack |
| Production ou hors production | Déploiement | Configuration de la couche web | Déploie des configurations HTTPD/Dispatcher | Déploiement en quelques minutes |
| Production ou hors production | Déploiement | Config | Déploie la [configuration pour un certain nombre de fonctionnalités](/help/operations/config-pipeline.md) liées au réseau de diffusion de contenu, au transfert de journal et aux tâches de maintenance de purge | Déploiement en quelques minutes |
| Hors production | Qualité du code | Full stack | Exécute des analyses de qualité du code sur le code full stack sans déploiement. | Prise en charge de plusieurs pipelines |
| Hors production | Qualité du code | Front-end | Exécute des analyses de qualité du code sur le code front-end sans déploiement. | Prise en charge de plusieurs pipelines |
| Hors production | Qualité du code | Configuration de la couche web | Exécute des analyses de qualité du code sur les configurations du Dispatcher sans déploiement. | Prise en charge de plusieurs pipelines |

Le diagramme suivant illustre les configurations de pipelines Cloud Manager avec une configuration traditionnelle, un référentiel front-end unique ou un référentiel front-end indépendant.

![Configurations de pipeline Cloud Manager](/help/implementing/cloud-manager/assets/configure-pipeline/cm-setup.png)

## Pipelines full stack {#full-stack-pipeline}

Les pipelines full stack déploient simultanément le code principal, le code front-end et les configurations de niveau web pour l’exécution d’AEM.

* Code back-end : contenu non modifiable tel que du code Java, des configurations OSGi, repoinit et du contenu modifiable
* Code front-end : ressources de l’interface utilisateur de l’application telles que JavaScript, le CSS, les polices.
* Configuration de niveau web : configurations HTTPD/Dispatcher.

Le pipeline full stack représente un « super-pipeline » qui fait tout en même temps, tout en donnant aux utilisateurs les options de déployer exclusivement leur code front-end ou leurs configurations Dispatcher respectivement via le pipeline front-end et les pipelines de configuration de niveau web.

Les pipelines full stack empaquettent le code front-end (JavaScript/CSS) sous la forme de [bibliothèques clientes AEM](/help/implementing/developing/introduction/clientlibs.md).

Les pipelines full stack peuvent déployer des configurations de niveau web si un [pipeline de configuration de niveau web](#web-tier-config-pipelines) n’est pas configuré.

Les restrictions suivantes s’appliquent.

* La personne utilisatrice doit être connectée en tant que **Gestionnaire de déploiement** pour configurer ou exécuter des pipelines.
* À tout moment, il ne peut y avoir qu’un seul pipeline full stack par environnement.

En outre, assurez-vous de savoir comment se comporte le pipeline full stack si vous choisissez d’introduire un [pipeline de configuration de niveau web.](#web-tier-config-pipelines)

* Le pipeline full stack pour un environnement ignore la configuration du Dispatcher si le pipeline de configuration de niveau web correspondant existe.
* Si le pipeline de configuration de niveau web correspondant à l’environnement n’existe pas, l’utilisateur peut configurer le pipeline full stack pour inclure ou ignorer la configuration de Dispatcher.

Les pipelines full stack peuvent être des pipelines de type qualité de code ou déploiement.

### Configuration de pipelines full stack {#configure-full-stack}

Pour savoir comment configurer des pipelines full stack, reportez-vous aux documents suivants :

* [Ajout d’un pipeline de production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#full-stack-code)
* [Ajout d’un pipeline hors production](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#full-stack-code)

## Configuration des pipelines {#config-deployment-pipeline}

Avec un pipeline de configuration, vous pouvez déployer rapidement des configurations pour le transfert de journaux, les tâches de maintenance liées à la purge et diverses configurations du réseau de diffusion de contenu, telles que les règles de filtrage du trafic (y compris les règles WAF), les transformations de requête et de réponse, les sélecteurs d’origine, les redirections côté client, les pages d’erreur, les clés de réseau de diffusion de contenu gérées par le client, les clés d’API de purge et l’authentification de base.

Consultez le document [Utilisation des pipelines de configuration](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) pour obtenir une liste complète des fonctionnalités prises en charge et pour savoir comment gérer les configurations de votre référentiel afin qu’elles soient déployées correctement.

### Configuration des pipelines de configuration {#configure-config-deployment}

Pour savoir comment configurer les pipelines de configuration, consultez les documents suivants :

* [Ajout d’un pipeline de production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#targeted-deployment)
* [Ajout d’un pipeline hors production](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#targeted-deployment)

## Pipelines front-end {#front-end}

Un code front-end correspond à tout code qui est servi en tant que fichier statique. Il est distinct du code de l’interface utilisateur fourni par AEM et peut inclure des thèmes de site, des SPA définis par le client ou la clente, des SPA ainsi que d’autres solutions.

Les pipelines front-end aident vos équipes à rationaliser votre processus de conception et de développement en activant le déploiement accéléré de code front-end asynchrone du développement principal. Ce pipeline dédié déploie le JavaScript et le CSS vers le calque de distribution AEM en tant que thème, ce qui entraîne une nouvelle version du thème qui peut être référencée à partir des pages fournies par AEM.

>[!NOTE]
>
>Un utilisateur disposant du rôle **Responsable de déploiement** peut créer et exécuter plusieurs pipelines front-end simultanément.
>
>Toutefois, il existe une limite maximale de 300 pipelines par programme (pour tous les types de pipelines).

Les pipelines front-end peuvent être des pipelines de qualité de code ou de déploiement.

### Avant de configurer des pipelines front-end {#before-start}

Avant de configurer des pipelines front-end, consultez le [Parcours de création rapide d’un site](/help/journey-sites/quick-site/overview.md) pour une présentation complète de son exécution grâce à l’outil de création rapide de site d’AEM, particulièrement simple d’utilisation. Ce parcours vous aidera à rationaliser votre développement front-end et à personnaliser rapidement votre site sans aucune connaissance back-end d’AEM.

### Configuration d’un pipeline front-end {#configure-front-end}

Pour savoir comment configurer les pipelines front-end, voir :

* [Ajout d’un pipeline de production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#adding-production-pipeline)
* [Ajout d’un pipeline hors production](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#adding-non-production-pipeline)

### Développer des sites avec le pipeline front-end {#developing-with-front-end-pipeline}

Avec les pipelines front-end, les développeurs front-end bénéficient d’une plus grande indépendance et le processus de développement peut être accéléré.

Consultez le document [Développement de sites avec le pipeline front-end](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md) pour connaître le fonctionnement de ce processus ainsi que certaines considérations à prendre en compte pour en tirer le meilleur parti.

## Pipelines de configuration de niveau web {#web-tier-config-pipelines}

Les pipelines de configuration de niveau web permettent le déploiement exclusif de la configuration HTTPD/Dispatcher pour l’exécution d’AEM en le découplant des autres modifications de code. Il s’agit d’un pipeline rationalisé qui fournit aux utilisateurs qui souhaitent déployer uniquement les modifications de configuration du Dispatcher, une méthode accélérée pour le faire en quelques minutes seulement.

>[!TIP]
>
>Avec les pipelines de configuration de niveau web, vous pouvez choisir entre stocker votre configuration web au même emplacement source que le pipeline full stack ou à un autre emplacement, selon la structure qui convient le mieux à votre projet.

Les restrictions suivantes s’appliquent.

* Vous devez être sur une version `2021.12.6151.20211217T120950Z` ou plus récente d’AEM pour utiliser les pipelines de configuration de niveau web.
* Vous devez [vous inscrire au mode flexible des outils du Dispatcher](/help/implementing/dispatcher/disp-overview.md#validation-debug) pour utiliser les pipelines de configuration de niveau web.
* La personne utilisatrice doit être connectée en tant que **Gestionnaire de déploiement** pour configurer ou exécuter des pipelines.
* À tout moment, il ne peut y avoir qu’un seul pipeline de configuration de niveau web par environnement.
* L’utilisateur ne peut pas configurer de pipeline de configuration de niveau web lorsque le pipeline de pile complète correspondant est en cours d’exécution.
* La structure de niveau web doit se conformer à la structure de mode flexible, telle que définie dans le document [Dispatcher en mode cloud](/help/implementing/dispatcher/disp-overview.md#validation-debug).

En outre, assurez-vous de savoir comment se comporte le [pipeline full stack](#full-stack-pipeline) lorsque vous introduisez un pipeline de configuration de niveau web.

* Si un pipeline de configuration de niveau web n’a pas été configuré pour un environnement, l’utilisateur peut effectuer une sélection lors de la configuration de son pipeline full stack correspondant afin d’inclure ou d’ignorer la configuration de Dispatcher pendant l’exécution et le déploiement.
* Une fois qu’un pipeline de configuration de niveau web a été configuré pour un environnement, son pipeline full stack correspondant (s’il en existe un) ignorera la configuration du Dispatcher lors de l’exécution et du déploiement.
* Une fois qu’un pipeline de configuration de niveau web est supprimé, son pipeline full stack correspondant est réinitialisé pour déployer les configurations du Dispatcher pendant son exécution.

Les pipelines de configuration de niveau web peuvent être de type qualité de code ou déploiement.

### Configuration des pipelines de niveau web {#configure-web-tier}

Pour savoir comment configurer des pipelines de niveau web, consultez les documents suivants :

* [Ajout d’un pipeline de production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#targeted-deployment)
* [Ajout d’un pipeline hors production](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#targeted-deployment)

## Présentation vidéo des types de pipeline {#video}

Pour obtenir un aperçu rapide des types de pipeline, regardez cette courte vidéo.

>[!VIDEO](https://video.tv.adobe.com/v/342363)
