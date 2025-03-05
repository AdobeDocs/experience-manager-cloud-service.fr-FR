---
title: Interprétation des informations d’utilisation des formulaires à l’aide du tableau de bord de réalisation des valeurs
description: Découvrez comment utiliser le tableau de bord des informations d’utilisation de Forms pour surveiller et comprendre les performances de vos formulaires et de vos fragments de formulaire.
role: User, Developer
level: Intermediate
feature: Adaptive Forms, Foundation Components, Core Components
hide: true
hidefromtoc: true
source-git-commit: 85d788eeb5017b99ea4962105b63b20c487f363f
workflow-type: tm+mt
source-wordcount: '869'
ht-degree: 1%

---


# Interprétation des informations d’utilisation de Forms à l’aide du tableau de bord de réalisation des valeurs

<span class="preview"> Cette fonctionnalité est disponible via le programme d’accès anticipé. Pour demander l’accès, envoyez un e-mail à l’adresse aem-forms-ea@adobe.com. <span>

![Tableau de bord de réalisation des valeurs](/help/edge/docs/forms/universal-editor/assets/forms-insights-banner.svg)


En surveillant régulièrement les mesures présentées dans le tableau de bord « Informations sur l’utilisation de Forms », vous pouvez obtenir des informations précieuses sur les performances de vos formulaires, documents et fragments de formulaire. Utilisez ces données pour prendre des décisions éclairées sur la conception de formulaire, la gestion des fragments et la stratégie de formulaire globale.

Cet article fournit des instructions d’utilisation détaillées et l’interprétation des mesures pour le tableau de bord de réalisation des valeurs. Pour une présentation conceptuelle et les avantages du tableau de bord, voir [Présentation du tableau de bord de réalisation de la valeur](/help/forms/aem-forms-value-realization-dashboard.md).


## Accès au tableau de bord des informations d’utilisation

Pour accéder au tableau de bord des informations d’utilisation de Forms :

1. Accédez à **Forms** > **Forms et documents**
1. Cliquez sur **Tableau de bord des informations**. Le tableau de bord s’ouvre dans une nouvelle fenêtre.

![Tableau de bord de réalisation des valeurs](/help/forms/assets/forms-usage-insights.png)

## Vue d’ensemble

Le tableau de bord se compose de deux sections principales :

- **Activité Formulaires et documents au fil du temps :** cette section fournit des informations sur l’utilisation et l’évolution de vos formulaires au cours d’une période sélectionnée.
- **Utilisation des fragments :** cette section vous permet de surveiller l’adoption et la réutilisation des fragments de formulaire.

## Activité Formulaires et documents dans le temps

Cette section contient quatre graphiques, chacun effectuant le suivi d’un aspect différent de l’activité de formulaire. Tous les graphiques partagent la même structure :

- **Type de graphique :** Graphique en courbes et Graphique à barres
- **Axe X:** Date (indiquant l’activité quotidienne)
- **Axe Y:** Nombre (représentant le nombre d’occurrences de l’activité suivie)
- **Période :** réglable via un menu déroulant (options : « 30 derniers jours », « 12 derniers mois »)




### Envois de formulaire

- **Objectif :** ce graphique affiche le nombre de fois où les formulaires ont été envoyés avec succès au cours de la période sélectionnée.

  ![Graphique des envois Forms](/help/forms/assets/forms-submissions-vr-dashboard-form-insights.png)
- **Informations à extraire :**
   - **Analyse des tendances :** observez la tendance globale des envois de formulaires. Le nombre augmente-t-il, diminue-t-il ou reste-t-il relativement constant ?
   - **Périodes de pointe :** identifier les jours ou les périodes présentant des taux d’envoi anormalement élevés. Examinez les raisons possibles de ces pics (par exemple, campagnes marketing, événements spécifiques).
   - **Périodes de faible activité :** identifier les périodes où le taux d’envoi est faible et étudier les causes potentielles (par exemple, temps d’arrêt des formulaires, problèmes d’utilisation).
   - **Analyse comparative :** comparez les taux de soumission sur différentes périodes (p. ex., les 30 derniers jours par rapport aux 30 jours précédents) pour évaluer les changements de rendement.

### Rendus de document

- **Objectif :** ce graphique permet de suivre le nombre de documents générés suite aux envois de formulaires. Cela est pertinent si vos formulaires déclenchent la création de documents (par exemple, des contrats, des rapports).

  ![Graphique Rendus de document](/help/forms/assets/document-rendetions-vr-dashboard-form-insights.png)


- **Informations à extraire :**
   - **Corrélation avec les envois de formulaire :** comparer la tendance des rendus de document à la tendance des envois de formulaire. Idéalement, ces paramètres doivent être étroitement corrélés. Des incohérences peuvent indiquer des problèmes liés au processus de génération de documents.
   - **Volume de génération de documents :** évaluez le volume global de documents générés pour comprendre la charge de travail sur votre système de génération de documents.

### Formulaires créés


- **Objectif :** ce graphique affiche le nombre de nouveaux formulaires créés au cours de la période sélectionnée.

  ![Graphique Forms Créé](/help/forms/assets/forms-created-vr-dashboard-form-insights.png)

- **Informations à extraire :**
   - **Taux de création de formulaire :** suivez le taux de création de formulaires. Cela permet de mieux comprendre la demande de nouveaux formulaires au sein de l’organisation.
   - **Pics de création :** identifier les périodes présentant une activité de création de formulaire inhabituellement élevée. Cela peut indiquer des projets ou des initiatives spécifiques qui nécessitent de nouveaux formulaires.

### Forms Published

- **Objectif :** ce graphique permet de suivre le nombre de formulaires qui ont été publiés (mis à disposition pour utilisation) au cours de la période sélectionnée.

  ![Graphique Publié Forms](/help/forms/assets/forms-publish-vr-dashboard-form-insights.png)


- **Informations à extraire :**
   - **Taux de déploiement des formulaires :** surveiller le taux de déploiement de nouveaux formulaires pour les utilisateurs.
   - **Décalage entre la création et la publication :** analysez le décalage horaire entre le graphique « Forms Created » et le graphique « Forms Published ». Un retard significatif peut indiquer des goulots d’étranglement dans le processus d’approbation ou de déploiement du formulaire.

## Utilisation du fragment

Cette section fournit des informations sur l’utilisation des fragments de formulaire, qui sont des composants réutilisables pouvant être incorporés dans plusieurs formulaires.

![Graphique Publié Forms](/help/forms/assets/fragment-usage-vr-dashboard-form-insights.png)

### Nombre de fragments de formulaire actuellement utilisés

- **Type de graphique :** Affichage numérique (présentant une seule valeur)
- **Objectif :** affiche le nombre total de fragments de formulaire uniques actuellement utilisés dans les formulaires actifs.
- **Informations à extraire :**
   - **Adoption des fragments :** évaluez l’adoption globale des fragments de formulaire au sein de l’organisation. Un nombre plus élevé indique une utilisation plus importante des composants réutilisables.

### Réutilisation du fragment de formulaire

- **Type de graphique :** Affichage numérique (présentant une seule valeur)
- **Objectif :** affiche le nombre total de fois où les fragments de formulaire ont été réutilisés dans différents formulaires. Cette mesure indique l’efficacité de l’utilisation des fragments pour éviter la duplication et maintenir la cohérence.
- **Informations à extraire :**
   - **Taux de réutilisation des fragments :** permet de surveiller le taux de réutilisation des fragments existants dans de nouveaux formulaires. Un nombre plus élevé indique une meilleure utilisation des composants réutilisables et une efficacité améliorée.

## Exemples de scénarios

- **Scénario :** vous constatez une baisse soudaine des « envois de formulaire ».
   - **Action :** étudier les causes potentielles telles que le temps d’arrêt du formulaire, des problèmes de convivialité ou une baisse du trafic sur la page de destination du formulaire.
- **Scénario :** la valeur « Réutilisation du fragment de formulaire » est faible.
   - **Action :** faites valoir les avantages de l’utilisation des fragments de formulaire auprès de votre équipe, assurez-vous que les fragments sont bien organisés et faciles à trouver, et fournissez une formation sur la création et la réutilisation efficaces des fragments.
- **Scénario :** il y a un décalage important entre « Forms Created » et « Forms Published ».
   - **Action :** passez en revue votre processus d’approbation et de déploiement de formulaire pour identifier et éliminer les goulots d’étranglement.



## Voir également

- [Présentation de votre tableau de bord de réalisation des valeurs](/help/forms/aem-forms-value-realization-dashboard.md)