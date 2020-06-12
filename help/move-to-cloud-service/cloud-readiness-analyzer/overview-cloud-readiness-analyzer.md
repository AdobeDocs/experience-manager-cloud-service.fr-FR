---
title: Présentation de Cloud Readiness Analyzer
description: Présentation de Cloud Readiness Analyzer
translation-type: tm+mt
source-git-commit: f0e69dba5d670d141c82e762069f4831c2527dbe
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---


# Présentation {#overview-cloud-readiness-analyzer}

Cloud Readiness Analyzer permet d’accélérer les processus d’évaluation de la préparation au passage d’un déploiement existant d’Adobe Experience Manager (AEM) à AEM en tant que service Cloud.

Cet outil génère un rapport qui identifie les zones de refactorisation potentielle, qui constitue la première étape du parcours de transition vers AEM en tant que service Cloud.

## Rapport de synthèse dans Cloud Readiness Analyzer {#summary-report}

Le rapport de synthèse de Cloud Readiness Analyzer permet de mieux comprendre la préparation générale à la mise à niveau. Le rapport comprend les conclusions, dans les catégories, des problèmes qui doivent être résolus avant un déploiement réussi vers AEM en tant que service Cloud.

Le rapport de synthèse comprend les catégories suivantes :

* Fonctionnalités de l’application qui doivent être reconfigurées
* Éléments du référentiel qui doivent être déplacés vers un emplacement pris en charge
* Boîtes de dialogue et composants d’interface utilisateur hérités qui doivent être modernisés
* Problèmes de déploiement et de configuration
* Fonctionnalités d’AEM 6.x qui ont été remplacées par de nouvelles fonctionnalités ou qui ne sont actuellement pas prises en charge sur AEM en tant que service Cloud

Des informations complémentaires sur les catégories, les implications possibles et les solutions associées à ces catégories sont fournies par le biais de liens figurant dans le rapport de synthèse.

>[!NOTE]
>Le rapport Cloud Readiness Analyzer accélère le processus d’estimation du temps et du coût requis pour la transition d’AEM en tant que service Cloud en fournissant des informations qui autrement auraient dû être collectées et évaluées manuellement.

Vous pouvez également télécharger le rapport de synthèse à partir de l’interface utilisateur d’AEM. Consultez **Affichage des résultats au format** CSV pour plus de détails en attente.