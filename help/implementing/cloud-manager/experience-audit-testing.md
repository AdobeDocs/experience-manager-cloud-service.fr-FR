---
title: Tests de contrôle de l’expérience – Cloud Services
description: Tests de contrôle de l’expérience – Cloud Services
translation-type: tm+mt
source-git-commit: c1ce44fb8a7b12818b58ff5ef661b9b447b9cd5c
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 100%

---


# Tests de contrôle de l’expérience {#experience-audit-testing}

Le contrôle de l’experience est une fonctionnalité disponible dans les pipelines de production de Cloud Manager Sites, reposant sur Google Lighthouse, un outil open source de Google. Cette fonctionnalité est activée dans tous les pipelines de production de Cloud Manager.

Elle valide le processus de déploiement et permet de s’assurer que les modifications sont déployées :

1. Respectez les normes de base en matière de performances, d’accessibilité, de bonnes pratiques, d’optimisation du moteur de recherche (SEO) et d’application web progressive (PWA).

1. N’incluez pas de régressions dans ces dimensions.

Le contrôle de l’expérience dans Cloud Manager garantit que l’expérience numérique des utilisateurs finaux sur le site peut être maintenue aux normes les plus élevées. Les résultats sont informatifs et permettent à l’utilisateur de voir les scores et le changement entre les scores actuels et précédents. Ces informations sont utiles pour déterminer si une régression sera introduite avec le déploiement actuel.

## Compréhension des résultats du contrôle de l’expérience {#understanding-experience-audit-results}

Le contrôle de l’expérience fournit des résultats de test au niveau de la page agrégés et détaillés via la page d’exécution du pipeline de production.

* Les mesures au niveau agrégé déterminent le score moyen sur les pages ayant fait l’objet d’un audit en termes de performances, d’accessibilité, de bonnes pratiques et d’optimisation du moteur de recherche (SEO).
   >[!NOTE]
   >Le score d’application web progressive (PWA) n’est pas inclus dans le score récapitulatif et ne sera affiché que sur l’écran des détails de rapport au niveau de la page.
* Des scores individuels au niveau de la page sont également disponibles via une analyse en profondeur.
* Des détails sur les scores sont disponibles et indiquent les résultats des tests individuels, tout en fournissant des conseils sur la façon de résoudre les problèmes identifiés dans le cadre du contrôle de l’expérience.
* Un historique des résultats de test est conservé dans Cloud Manager afin que les clients puissent voir si les modifications introduites dans l’exécution du pipeline incluent des régressions par rapport à l’exécution précédente.

### Scores agrégés {#aggregate-scores}

Il existe pour chaque type de test un score au niveau agrégé, tel que les performances, l’accessibilité, le SEO et les bonnes pratiques.
>[!NOTE]
>Le score d’application web progressive (PWA) n’est pas inclus dans le score récapitulatif et ne sera affiché que sur l’écran des détails de rapport au niveau de la page.

Le score au niveau agrégé extrait le score moyen des pages incluses dans l’exécution. Le changement au niveau agrégé représente le score moyen des pages de l’exécution actuelle par rapport à la moyenne des scores de l’exécution précédente, même si la collection de pages configurées pour être incluses a été modifiée entre les exécutions.

La valeur de la mesure Change (Modification) peut être l’une des suivantes :

* **Valeur positive** : la ou les pages ont été améliorées sur le test sélectionné depuis la dernière exécution du pipeline de production.

* **Valeur négative** : la ou les pages ont régressé sur le test sélectionné depuis la dernière exécution du pipeline de production.

* **Aucune modification** : la ou les pages ont obtenu le même score depuis la dernière exécution du pipeline de production.

* **N/A** : il n’y a pas de score précédent avec lequel effectuer la comparaison.

   ![](/help/implementing/cloud-manager/assets/exp-audit-1.png)


### Scores au niveau de la page {#page-level-scores}

En analysant en profondeur n’importe lequel des tests, vous obtiendrez des scores de niveau page plus détaillés. L’utilisateur pourra voir le score des pages individuelles pour le test spécifique, ainsi que la modification par rapport à la précédente exécution du test.

Cliquer sur les détails d’une page donnée fournit des informations sur les éléments de la page qui ont été évalués, ainsi que des conseils pour résoudre les problèmes si des opportunités d’amélioration sont détectées. Les détails des tests et les conseils associés sont fournis par Google Lighthouse.

![](/help/implementing/cloud-manager/assets/exp-audit-2.png)

