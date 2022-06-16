---
title: Tests de contrôle de l’expérience
description: Découvrez comment le contrôle de l’expérience valide votre processus de déploiement et vous aide à vous assurer que les modifications déployées répondent aux normes de base en matière de performances, d’accessibilité, de bonnes pratiques et d’optimisation pour les moteurs de recherche.
exl-id: 8d31bc9c-d38d-4d5b-b2ae-b758e02b7073
source-git-commit: 1a7a9ee78d09a9360922a63dfa315ef9d106209e
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 26%

---


# Tests de contrôle de l’expérience {#experience-audit-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_expaudittesting"
>title="Tests de contrôle de l’expérience"
>abstract="Découvrez comment le contrôle de l’expérience valide votre processus de déploiement et vous aide à vous assurer que les modifications déployées répondent aux normes de base en matière de performances, d’accessibilité, de bonnes pratiques et d’optimisation pour les moteurs de recherche."

Découvrez comment le contrôle de l’expérience valide votre processus de déploiement et vous aide à vous assurer que les modifications déployées répondent aux normes de base en matière de performances, d’accessibilité, de bonnes pratiques et d’optimisation pour les moteurs de recherche.

## Présentation {#overview}

Le contrôle de l’expérience est une fonctionnalité disponible dans les pipelines de production de Cloud Manager Sites qui valide le processus de déploiement et permet de s’assurer que les modifications sont déployées :

1. Respectez les normes de base en matière de performances, d’accessibilité, de bonnes pratiques, d’optimisation du moteur de recherche (SEO) et d’application web progressive (PWA).

1. N’introduisez pas de régressions.

Le contrôle de l’expérience dans Cloud Manager garantit que l’expérience de l’utilisateur final sur le site est de la plus haute qualité.

Les résultats de l’audit sont informatifs et permettent au responsable de déploiement d’afficher les scores et le changement entre les scores actuels et précédents. Ces informations sont utiles pour déterminer si une régression sera introduite avec le déploiement actuel.

Le contrôle de l’expérience est optimisé par Google Lighthouse, un outil open source de Google qui est activé dans tous les pipelines de production de Cloud Manager.

## Compréhension des résultats du contrôle de l’expérience {#understanding-experience-audit-results}

Le contrôle de l’expérience fournit des résultats de test au niveau de la page agrégés et détaillés via le [page d’exécution du pipeline de production.](/help/implementing/cloud-manager/deploy-code.md)

* Les mesures agrégées mesurent les scores moyens sur les pages qui ont fait l’objet d’un audit en termes de performances, d’accessibilité, de bonnes pratiques, d’optimisation du moteur de recherche (SEO).
* Des scores individuels au niveau de la page sont également disponibles via une analyse en profondeur.
* Des détails sur les scores sont disponibles pour afficher les résultats des tests individuels, ainsi que des conseils sur la façon de résoudre les problèmes identifiés.
* Un historique des résultats de test est conservé dans Cloud Manager afin de déterminer si les modifications introduites dans le pipeline incluent des régressions par rapport à l’exécution précédente.

### Scores agrégés {#aggregate-scores}

Le score au niveau agrégé extrait le score moyen des pages incluses dans l’exécution. Le changement au niveau agrégé représente le score moyen des pages de l’exécution actuelle par rapport à la moyenne des scores de l’exécution précédente, même si la collection de pages configurées pour être incluses a été modifiée entre les exécutions.

Il existe pour chaque type de test un score au niveau agrégé, tel que les performances, l’accessibilité, le SEO et les bonnes pratiques.

La mesure de modification peut avoir l’une des valeurs suivantes.

* **Valeur positive** - La ou les pages ont été améliorées sur le test sélectionné depuis la dernière exécution du pipeline de production.

* **Valeur négative** - la ou les pages ont régressé sur le test sélectionné depuis la dernière exécution du pipeline de production.

* **Aucune modification** - La ou les pages ont obtenu le même score depuis la dernière exécution du pipeline de production.

* **N/A** - Aucun score précédent n’était disponible pour la comparaison.

![Résultats du contrôle de l’expérience](/help/implementing/cloud-manager/assets/exp-audit-1.png)


### Scores au niveau de la page {#page-level-scores}

En analysant les tests dans n’importe lequel, des scores de niveau page plus détaillés sont disponibles. Vous pouvez voir le score des pages individuelles pour le test spécifique, ainsi que la modification par rapport à l’exécution de test précédente.

Cliquer sur les détails d’une page spécifique fournit des informations sur les éléments de la page qui ont été évalués, ainsi que des conseils pour résoudre les problèmes si des opportunités d’amélioration sont détectées.

![Scores au niveau de la page](/help/implementing/cloud-manager/assets/exp-audit-2.png)
