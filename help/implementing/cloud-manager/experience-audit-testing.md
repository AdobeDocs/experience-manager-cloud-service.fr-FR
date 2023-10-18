---
title: Tests d’audit de l’expérience
description: Découvrez comment l’audit de l’expérience valide votre processus de déploiement et vous aide à vous assurer que les modifications déployées répondent aux normes de base en matière de performances, d’accessibilité, de bonnes pratiques et d’optimisation des moteurs de recherche.
exl-id: 8d31bc9c-d38d-4d5b-b2ae-b758e02b7073
source-git-commit: 9f305e1127957fdba6dae978da4ac5fce4d3a776
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 93%

---


# Tests d’audit de l’expérience {#experience-audit-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_expaudittesting"
>title="Tests d’audit de l’expérience"
>abstract="Découvrez comment l’audit de l’expérience valide votre processus de déploiement et vous aide à vous assurer que les modifications déployées répondent aux normes de base en matière de performances, d’accessibilité, de bonnes pratiques et d’optimisation des moteurs de recherche."

Découvrez comment l’audit de l’expérience valide votre processus de déploiement et vous aide à vous assurer que les modifications déployées répondent aux normes de base en matière de performances, d’accessibilité, de bonnes pratiques et d’optimisation des moteurs de recherche.

## Vue d’ensemble {#overview}

L’audit de l’expérience est une fonctionnalité disponible dans les pipelines de production de Cloud Manager Sites qui valide le processus de déploiement et permet de s’assurer que les modifications déployées :

1. Respectent les normes de base en matière de performances, d’accessibilité, de bonnes pratiques, d’optimisation du moteur de recherche (SEO) et d’application web progressive (PWA).

1. N’introduisent pas de régressions.

L’audit de l’expérience dans Cloud Manager garantit que l’expérience de l’utilisateur final sur le site est de la plus haute qualité.

Les résultats sont informatifs et permettent au responsable de déploiement de voir les scores et les différences existant entre les scores précédents et actuels. Ces informations sont utiles pour déterminer si une régression a été introduite avec le déploiement actuel.

L’audit de l’expérience est optimisé par Google Lighthouse, un outil open source de Google qui est activé dans tous les pipelines de production de Cloud Manager.

>[!INFO]
>
>À compter du 31 août 2023, le contrôle de l’expérience effectuera la transition vers la présentation des résultats spécifiques à la plateforme mobile. Notez que les mesures de performances mobiles s’inscrivent généralement en dessous de celles des ordinateurs de bureau. Par conséquent, veuillez anticiper un changement des performances signalées suite à ce changement.

>[!TIP]
>
>Vous configurez les pages incluses dans l’audit de l’expérience lorsque vous [configurez votre pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#full-stack-code).

## Comprendre les résultats de l’audit de l’expérience {#understanding-experience-audit-results}

L’audit de l’expérience fournit des résultats de test au niveau de la page agrégés et détaillés via la [page d’exécution du pipeline de production](/help/implementing/cloud-manager/deploy-code.md).

* Les mesures agrégées déterminent le score moyen sur les pages ayant fait l’objet d’un audit en termes de performances, d’accessibilité, de bonnes pratiques et d’optimisation du moteur de recherche (SEO).
* Des scores individuels au niveau de la page sont également disponibles via une analyse en profondeur.
* Des détails sur les scores sont disponibles et indiquent les résultats des tests individuels, tout en fournissant des conseils sur la façon de résoudre les problèmes identifiés.
* Un historique des résultats de test est conservé dans Cloud Manager afin de pouvoir voir si les modifications introduites dans le pipeline incluent des régressions par rapport à l’exécution précédente.

### Scores agrégés {#aggregate-scores}

Le score au niveau agrégé extrait le score moyen des pages incluses dans l’exécution. Le changement au niveau agrégé représente le score moyen des pages de l’exécution actuelle par rapport à la moyenne des scores de l’exécution précédente, même si la collection de pages configurées pour être incluses a été modifiée entre les exécutions.

Il existe pour chaque type de test un score au niveau agrégé, tel que les performances, l’accessibilité, l’optimisation du moteur de recherche et les bonnes pratiques.

La mesure de modification peut avoir l’une des valeurs suivantes.

* **Valeur positive** : la ou les pages ont été améliorées sur le test sélectionné depuis la dernière exécution du pipeline de production.

* **Valeur négative** : la ou les pages ont régressé sur le test sélectionné depuis la dernière exécution du pipeline de production.

* **Aucune modification** : la ou les pages ont obtenu le même score depuis la dernière exécution du pipeline de production.

* **N/A** : il n’y a pas de score précédent avec lequel effectuer la comparaison.

![Résultats de l’audit de l’expérience](/help/implementing/cloud-manager/assets/exp-audit-1.png)

### Scores au niveau de la page {#page-level-scores}

En analysant en profondeur n’importe lequel des tests, vous obtiendrez des scores au niveau de la page plus détaillés. Vous pouvez voir le score des pages individuelles pour le test spécifique, ainsi que la modification par rapport à l’exécution de test précédente.

Cliquer sur les détails d’une page donnée fournit des informations sur les éléments de la page qui ont été évalués, et des conseils pour résoudre les problèmes si des possibilités d’amélioration sont détectées.

![Scores au niveau de la page](/help/implementing/cloud-manager/assets/exp-audit-2.png)
