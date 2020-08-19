---
title: Test d'audit de contenu - Cloud Services
description: Test d'audit de contenu - Cloud Services
translation-type: tm+mt
source-git-commit: ce25ec1472dc349937fdbd5f7265d4295fe111e8
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---


# Test de l’audit du contenu {#content-audit-testing}

L’audit de contenu est une fonctionnalité disponible dans les oléoducs de production de sites Cloud Manager optimisés par Lighthouse, un outil open source de Google. Cette fonctionnalité est activée dans tous les pipelines de production de Cloud Manager.

Il valide le processus de déploiement et permet de s’assurer que les modifications sont déployées :

1. Respectez les normes de base en matière de performances, d&#39;accessibilité, de bonnes pratiques, d&#39;optimisation du référencement (optimisation pour les moteurs de recherche) et de PWA (application Web progressive).

1. N’incluez pas de régressions dans ces dimensions.

L’audit de contenu dans Cloud Manager garantit que l’expérience numérique des utilisateurs finaux sur le site peut être maintenue aux normes les plus élevées. Les résultats sont informatifs et permettent à l’utilisateur de voir les scores et le changement entre les scores actuel et précédent. Cette connaissance est utile pour déterminer si une régression est introduite avec le déploiement actuel.

## Présentation des résultats de l&#39;audit du contenu {#understanding-content-audit-results}

L’audit de contenu fournit des résultats de test détaillés et agrégats au niveau de la page via la page d’exécution du pipeline de production.

* Les mesures au niveau de l’Agrégat mesurent le score moyen sur les pages qui ont été vérifiées.
* Des scores individuels au niveau de la page sont également disponibles par le biais d’une analyse approfondie.
* Des détails sur les notes sont disponibles pour voir quels sont les résultats des tests individuels, ainsi que des conseils sur la façon de résoudre les problèmes qui ont été identifiés lors de la vérification du contenu.
* Un historique des résultats du test est conservé dans Cloud Manager afin que les clients puissent voir si les modifications introduites dans l’exécution du pipeline incluent des régressions par rapport à l’exécution précédente.

### Scores d’Agrégat {#aggregate-scores}

Il existe un score de niveau agrégat pour chaque type de test (performances, accessibilité, optimisation du référencement, bonnes pratiques et PWA).

Le score de niveau agrégat correspond au score moyen des pages incluses dans l’exécution. Le changement au niveau de l’agrégat représente le score moyen des pages de l’exécution en cours par rapport à la moyenne des scores de l’exécution précédente, même si la collection de pages configurées pour être incluses a été modifiée entre les exécutions.

La mesure Valeur de changement peut être l’une des mesures suivantes :

* **Valeur** positive : les pages ont été améliorées sur le test sélectionné depuis la dernière exécution du pipeline de production.

* **Valeur** négative : les pages ont régressé sur le test sélectionné depuis la dernière exécution du pipeline de production.

* **Aucune modification** : les pages ont obtenu le même score depuis la dernière exécution du pipeline de production.

* **S/O** - aucun score précédent n’était disponible pour la comparaison

   ![](/help/implementing/developing/introduction/assets/content-audit-test1.png)

### Scores au niveau de la page {#page-level-scores}

En analysant n’importe lequel des tests, vous obtenez des scores de niveau de page plus détaillés. L’utilisateur pourra voir comment les pages individuelles ont obtenu un score pour le test spécifique, ainsi que la variation par rapport à la précédente exécution du test.

Un clic sur les détails d&#39;une page donnée fournit des informations sur les éléments de la page qui ont été évalués et des conseils pour résoudre les problèmes si des opportunités d&#39;amélioration sont détectées. Les détails des tests et les conseils associés sont fournis par Google Lighthouse.

![](/help/implementing/developing/introduction/assets/page-level-scores.png)

