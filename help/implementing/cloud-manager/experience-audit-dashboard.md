---
title: Tableau de bord du contrôle de l’expérience
description: Découvrez comment le contrôle de l’expérience valide votre processus de déploiement et vous aide à vous assurer que les modifications déployées répondent aux normes de base en termes de performances, d’accessibilité, de bonnes pratiques et d’optimisation pour les moteurs de recherche par le biais d’une interface de tableau de bord claire et informative.
exl-id: 6d33c3c5-258c-4c9c-90c2-d566eaeb14c0
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '831'
ht-degree: 23%

---

# Tableau de bord du contrôle de l’expérience {#experience-audit-dashboard}


Découvrez comment le contrôle de l’expérience valide votre processus de déploiement et vous aide à vous assurer que les modifications déployées répondent aux normes de base en termes de performances, d’accessibilité, de bonnes pratiques et d’optimisation pour les moteurs de recherche par le biais d’une interface de tableau de bord claire et informative.

>[!NOTE]
>
>Cette fonctionnalité n’est disponible que pour [le programme d&#39;adoption précoce.](/help/implementing/cloud-manager/release-notes/current.md#early-adoption)
>
>Pour plus d’informations sur la fonction d’audit d’expérience existante pour AEM as a Cloud Service, voir [Tests de contrôle de l’expérience](/help/implementing/cloud-manager/experience-audit-testing.md).

## Vue d’ensemble {#overview}

L’audit de l’expérience est une fonctionnalité disponible dans les pipelines de production de Cloud Manager Sites qui valide le processus de déploiement et permet de s’assurer que les modifications déployées :

1. Respectent les normes de base en matière de performances, d’accessibilité, de bonnes pratiques, d’optimisation du moteur de recherche (SEO) et d’application web progressive (PWA).

1. N’introduisent pas de régressions.

L’audit de l’expérience dans Cloud Manager garantit que l’expérience de l’utilisateur final sur le site est de la plus haute qualité.

Les résultats sont informatifs et permettent au responsable de déploiement de voir les scores et les différences existant entre les scores précédents et actuels. Ces informations sont utiles pour déterminer si une régression a été introduite avec le déploiement actuel.

Le contrôle de l’expérience est optimisé par [Google Lighthouse](https://developer.chrome.com/docs/lighthouse/overview/), un outil Open Source de Google qui est activé dans tous les pipelines de production de Cloud Manager.

>[!TIP]
>
>Vous configurez les pages incluses dans l’audit de l’expérience lorsque vous [configurez votre pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#full-stack-code).

## Tableau de bord du contrôle de l’expérience {#dashboard}

Les résultats du contrôle de l’expérience sont présentés dans la section **Test d’évaluation** phase du pipeline de production via la [page d’exécution du pipeline de production](/help/implementing/cloud-manager/deploy-code.md).

![Tableau de bord dans le pipeline](assets/dashboard.png)

Le contrôle de l’expérience fournit des résultats de test au niveau de la page agrégés et détaillés, résumés sur quatre onglets :

* **[Informations](#insights)** fournissez une brève description des recommandations pratiques pour améliorer les performances de votre site.
* **[Scores de Lighthouse](#lighthouse)** sont un résumé des scores Lighthouse pour le code déployé dans cette exécution de pipeline.
* **[Pages](#pages)** est un résumé des performances des pages configurées spécifiquement pour être analysées.
* **[Problèmes](#issues)** résume les problèmes de performances détectés dans le code de cette exécution de pipeline.

### Insights {#insights}

La variable **Informations** fournit une brève description des recommandations pratiques pour améliorer les performances de votre site.

![Insights](assets/insights.png)

Sélectionnez la variable **Afficher plus** pour ouvrir le tableau de bord complet.

Dans le **Statistiques et recommandations** , vous trouverez une liste détaillée des recommandations pratiques avec un indicateur de valeur clair lié aux gains de performances attendus, ainsi que le pourcentage impacté des pages. Cela vous permet de hiérarchiser facilement ces recommandations pour vos équipes.

![Statistiques et recommandations](assets/insights-recommendations.png)

Pour revenir à la page d’exécution du pipeline de production, sélectionnez simplement la flèche Précédent sur votre navigateur.

### Scores Lighthouse {#lighthouse}

La variable **Scores de Lighthouse** Cet onglet est un résumé des scores Lighthouse pour le code déployé dans l’exécution de ce pipeline.

![Scores de Lighthouse](assets/lighthouse.png)

Sélectionnez la variable **Afficher plus** pour ouvrir le tableau de bord complet.

Dans le **Scores de Lighthouse** , vous trouverez une vue de tendance des différents scores. Sélectionner **Performances**, **Accessibilité**, **PWA**, ou **SEO** pour afficher la vue de tendance mensuelle de ces valeurs.

![Graphique de scores de Lighthouse](assets/lighthouse-scores.png)

Notez que chaque point du graphique est la moyenne de tous les déploiements pendant le mois d’intérêt.

Pour revenir à la page d’exécution du pipeline de production, sélectionnez simplement la flèche Précédent sur votre navigateur.

### Pages {#pages}

La variable **Pages** est un résumé des performances des pages spécifiquement configurées pour être analysées.

![Onglet Pages](assets/pages.png)

Sélectionnez la variable **Afficher plus** pour ouvrir le tableau de bord complet.

La variable **Pages** Cette section répertorie les pages qui ont été testées, leurs scores de performances et la ventilation les plus récents de Lighthouse.

![Vue Pages](assets/pages-view.png)

Vous configurez les pages incluses dans l’audit de l’expérience lorsque vous [configurez votre pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#full-stack-code).

Pour revenir à la page d’exécution du pipeline de production, sélectionnez simplement la flèche Précédent sur votre navigateur.

### Numéros {#issues}

La variable **Problèmes** répertorie tous les problèmes de performances détectés dans le code de cette exécution de pipeline.

![Onglet Problèmes](assets/issues.png)

Sélectionnez la variable **Afficher plus** pour ouvrir le tableau de bord complet.

Dans le **Statistiques et recommandations** , vous trouverez une liste plus détaillée des recommandations exploitables avec un indicateur de valeur clair lié aux gains de performances prévisibles, ainsi qu’au pourcentage de pages concerné. Cela vous permet de hiérarchiser facilement ces recommandations pour vos équipes.

![Statistiques et recommandations](assets/insights-recommendations.png)

Pour revenir à la page d’exécution du pipeline de production, sélectionnez simplement la flèche Précédent sur votre navigateur.

### Détails de la page {#page-detail}

Si vous sélectionnez le lien d’une page dans l’un des onglets de la **Audit de l’expérience** de l’onglet page d’exécution du pipeline ou dans la section **Pages** du tableau de bord Audit de l’expérience complet, vous pouvez afficher le détail d’une page spécifique.

![Données de page](assets/page-data.png)

Vous pouvez voir le score des pages individuelles pour le test spécifique, ainsi que la modification par rapport à l’exécution de test précédente.

Cliquer sur les détails d’une page donnée fournit des informations sur les éléments de la page qui ont été évalués, et des conseils pour résoudre les problèmes si des possibilités d’amélioration sont détectées.

Pour revenir à la page d’exécution du pipeline de production, sélectionnez simplement la flèche Précédent sur votre navigateur.
