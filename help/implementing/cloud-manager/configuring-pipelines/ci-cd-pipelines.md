---
title: Pipelines CI-CD
description: Pipelines CI-CD
index: false
source-git-commit: e51b995aebb053f38cb99879be70e23447f543c0
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 16%

---


# Pipelines CI-CD de Cloud Manager {#intro-cicd}

Dans Cloud Manager, il existe deux types de pipeline :

* **Pipeline de production**
* **Pipeline hors production**

## Pipeline de production {#prod-pipeline}

Un pipeline de production est un pipeline créé à des fins spécifiques qui comprend une série d’étapes orchestrées permettant d’intégrer le code source jusqu’à la production. Les étapes incluent d’abord la création, le conditionnement, le test, la validation et le déploiement dans tous les environnements intermédiaires. Il va sans dire qu’un pipeline de production ne peut être ajouté qu’une fois qu’un ensemble d’environnements de production et d’évaluation est créé.

>[!NOTE]
>Pour plus d’informations, voir Configuration du pipeline de production .


## Pipeline hors production {#non-prod-pipeline}

Un pipeline hors production vise à exécuter des analyses de qualité du code ou à déployer le code source dans un environnement de développement.

>[!NOTE]
>Pour plus d’informations, consultez Pipelines hors production et dédiés à la qualité du code.

Le déploiement et la qualité du code pris en charge dans les pipelines de production et hors production de Cloud Manager sont classés en deux types différents :

* Front end
* Pile complète

Le tableau suivant résume les pipelines :


>[!NOTE]
>Un pipeline CI/CD dans Cloud Manager est déclenché par un événement, tel qu’une demande d’extraction provenant d’un référentiel de code source, c’est-à-dire un changement de code ou une planification régulière pour correspondre à une cadence de publication.
>
>Pour configurer votre pipeline, vous devez :
>* définir le déclencheur qui démarrera le pipeline ;
>* définir les paramètres contrôlant le déploiement en production ;
>* configurer les paramètres de test de performance