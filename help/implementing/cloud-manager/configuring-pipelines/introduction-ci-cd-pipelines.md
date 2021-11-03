---
title: Pipelines CI-CD
description: Consultez cette page pour en savoir plus sur les pipelines CI-CD de Cloud Manager
index: false
source-git-commit: b6749b149e2166a6f2881817368e418d8b2adb00
workflow-type: tm+mt
source-wordcount: '826'
ht-degree: 3%

---


# Pipelines CI-CD de Cloud Manager {#intro-cicd}

## Présentation {#introduction}

Un pipeline CI/CD dans Cloud Manager peut être déclenché par un type d’événement, tel qu’une demande d’extraction provenant d’un référentiel de code source, c’est-à-dire un changement de code, ou une planification standard pour correspondre à une cadence de publication.

>[!NOTE]
>Pour configurer votre pipeline, vous devez :
>* définir le déclencheur qui démarrera le pipeline ;
>* définir les paramètres contrôlant le déploiement en production ;
>* configurer les paramètres de test de performance


Dans Cloud Manager, il existe deux types de pipelines :

* [Pipeline de production](#prod-pipeline)
* [Pipeline hors production](#non-prod-pipeline)

## Pipeline de production {#prod-pipeline}

Un pipeline de production est un pipeline créé à des fins spécifiques qui comprend une série d’étapes orchestrées permettant d’intégrer le code source jusqu’à la production. Les étapes incluent d’abord la création, le conditionnement, le test, la validation et le déploiement dans tous les environnements intermédiaires. Il va sans dire qu’un pipeline de production ne peut être ajouté qu’une fois qu’un ensemble d’environnements de production et d’évaluation est créé.

Voir [Configuration d’un pipeline de production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) pour plus d’informations.


## Pipeline hors production {#non-prod-pipeline}

Un pipeline hors production vise à exécuter des analyses de qualité du code ou à déployer le code source dans un environnement de développement.

Voir [Configuration d’un pipeline hors production](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) pour plus d’informations.

## Présentation des pipelines CI-CD dans Cloud Manager {#understand-pipelines}

Le tableau suivant récapitule tous les pipelines dans Cloud Manager, ainsi que leur utilisation.

| Type de pipeline | Déploiement ou qualité du code | Code source | Quand utiliser | Quand ou pourquoi dois-je utiliser ? |
|--- |--- |--- |---|---|---|
| Production ou hors production | Déploiement | Front end | Pour déployer le code frontal. Le code frontal est tout code qui est servi en tant que fichier statique. Il est distinct du code de l’interface utilisateur fourni par AEM. Il comprend les thèmes Sites, SPA définis par le client, Firefly SPA et toute autre solution. Doit se trouver sur AEM version. | Temps de déploiement rapide<br> Plusieurs pipelines front-end peuvent être configurés et exécutés simultanément par environnement. |
|  | Déploiement | Pile complète | Pour déployer la configuration du serveur principal, front-end et HTTPD/dispatcher en même temps. Certaines restrictions s’appliquent. | Lorsque les pipelines front-end n’ont pas encore été adoptés. |
| Hors production | Qualité du code | Front end | Exécution des analyses de qualité du code sur le code frontal | Temps de déploiement rapide<br> Plusieurs pipelines peuvent être configurés et exécutés. |
|  | Qualité du code | Pile complète | Exécution d’une analyse de la qualité du code sur le code de pile complet | Temps de déploiement rapide<br> Plusieurs pipelines peuvent être configurés et exécutés. |

Le diagramme suivant illustre les configurations de pipeline Cloud Manager avec un référentiel front-end unique traditionnel ou une configuration de référentiel front-end indépendant :

![](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-configurations.png)

## Pipelines front-end de Cloud Manager {#front-end}

Les pipelines front-end aident vos équipes à rationaliser votre processus de conception et de développement, en activant des pipelines front-end accélérés pour déployer le code front-end. Ce pipeline différencié déploie JavaScript et CSS sur la couche de distribution AEM en tant que thème, ce qui entraîne une nouvelle version de thème qui peut être référencée à partir des pages diffusées à partir du runtime AEM. Le code frontal est tout code qui est servi en tant que fichier statique. Il est distinct du code de l’interface utilisateur fourni par AEM. Il comprend les thèmes Sites, SPA définis par le client, Firefly SPA et toute autre solution.

>[!NOTE]
>Un utilisateur connecté en tant que rôle Deployment Manager peut créer et exécuter plusieurs pipelines front-end simultanément. Cependant, il existe une limite maximale de 300 pipelines par programme (pour tous les types de pipelines).

Il peut s’agir de pipelines de qualité du code frontal ou de déploiement front-end.

### Avant de configurer les pipelines front-end {#before-start}

Avant de commencer à configurer les pipelines front-end, reportez-vous à la section Parcours de création de site rapide pour un workflow de bout en bout grâce à l’outil de création de site rapide AEM convivial. Ce site de documentation vous aidera à rationaliser le développement frontal de votre site AEM et à personnaliser rapidement votre site sans aucune connaissance AEM du serveur principal.

### Configuration de votre pipeline front-end {#configure-front-end}

Pour savoir comment configurer le pipeline front-end, reportez-vous à :

* Ajout d’un pipeline de production
* Ajout d’un pipeline hors production

## Pipelines complets empilés {#full-stack-pipeline}

Le pipeline de pile complète permet à l’utilisateur de déployer simultanément la configuration back-end, front-end et HTTPD/dispatcher.  Il déploie le code et le contenu sur le runtime AEM, y compris le code frontal (JavaScript/CSS) conditionné en tant que bibliothèques clientes AEM. Il peut déployer la configuration de niveau web si un pipeline de niveau web n’est pas configuré. Il s’agit du pipeline &quot;uber&quot;, tout en permettant aux utilisateurs de déployer exclusivement leur code frontal ou leur configuration de dispatcher via le pipeline front-end et le pipeline de configuration de niveau web, respectivement.

Les restrictions suivantes s’appliquent :

1. Un utilisateur doit être connecté en tant que Deployment Manager pour configurer ou exécuter des pipelines.

1. À tout moment, il ne peut y avoir qu’un seul pipeline de pile complète par environnement.

1. L’utilisateur peut configurer le pipeline de pile complète pour qu’un environnement ignore ou ne pas ignorer la configuration du Dispatcher. Si le pipeline de configuration de niveau Web correspondant à l’environnement n’existe pas.

1. Le pipeline de pile complète pour un environnement ignore la configuration du Dispatcher si le pipeline de configuration de niveau web correspondant à l’environnement existe.

Il peut s’agir d’un pipeline de type Pile complète - Qualité du code ou Pile complète - Déploiement .

### Configuration de votre pipeline de pile {#configure-full-stack}

Pour savoir comment configurer un pipeline de pile complète, reportez-vous à :

* Ajout d’un pipeline de production
* Ajout d’un pipeline hors production