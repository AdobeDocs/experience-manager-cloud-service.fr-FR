---
title: Présentation de Cloud Readiness Analyzer
description: Présentation de Cloud Readiness Analyzer
translation-type: tm+mt
source-git-commit: 47773a56f8bb24342281068a8c4d03d6edfb9277
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# Présentation {#overview-cloud-readiness-analyzer}

L’analyseur de l’état de préparation de Cloud aide à évaluer la préparation au déplacement d’une instance AEM existante vers AEM en tant que service Cloud.

Cet outil détermine les zones qui nécessitent une refactorisation, qui constitue la première étape du parcours de transition vers AEM en tant que service Cloud.

L&#39;ARC détecte et signale les modèles qui :

* Utiliser une fonctionnalité AEM 6.x qui n’est actuellement pas prise en charge sur AEM en tant que service Cloud

* Violer certaines règles, configurations ou utilisations qui seront affectées par le déplacement vers AEM en tant que service Cloud

## Rapport de synthèse dans Cloud Readiness Analyzer {#summary-report}

Cloud Readiness Analyzer génère un rapport de synthèse qui peut être utilisé pour mieux comprendre l’état de préparation à la mise à niveau générale.

Le rapport organise les conclusions par catégories et sous-types dans ces catégories. Des informations complémentaires sur les catégories, les implications possibles et les solutions associées à ces catégories sont fournies par le biais de liens figurant dans le rapport de synthèse.

>[!NOTE]
>La sortie de Cloud Readiness Analyzer permet d’accélérer le processus d’estimation du temps et du coût requis pour passer à AEM en tant que service Cloud.