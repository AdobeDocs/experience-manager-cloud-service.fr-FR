---
title: Tests d’audit de l’expérience
description: Découvrez comment l’audit de l’expérience valide votre processus de déploiement et vous aide à vous assurer que les modifications déployées répondent aux normes de base en matière de performances, d’accessibilité, de bonnes pratiques et d’optimisation des moteurs de recherche.
exl-id: 8d31bc9c-d38d-4d5b-b2ae-b758e02b7073
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '890'
ht-degree: 56%

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

Le contrôle de l’expérience dans Cloud Manager garantit que l’expérience de l’utilisateur sur le site est de la plus haute qualité.

Les résultats sont informatifs et permettent au responsable de déploiement de voir les scores et les différences existant entre les scores précédents et actuels. Ces informations sont utiles pour déterminer si une régression a été introduite avec le déploiement actuel.

Le contrôle de l’expérience est optimisé par Google Lighthouse, un outil Open Source de Google.

>[!INFO]
>
>À compter du 31 août 2023, le contrôle de l’expérience effectuera la transition vers la présentation des résultats spécifiques à la plateforme mobile. Les mesures de performances mobiles s’inscrivent généralement en dessous de celles des ordinateurs de bureau. Vous devez donc anticiper un changement des performances signalées suite à ce changement.

## Disponibilité {#availability}

Le contrôle de l’expérience est disponible pour Cloud Manager :

* Pipelines de production de sites, par défaut.
* Des pipelines de développement front-end, éventuellement.

Pour plus d’informations sur la configuration de l’audit pour les environnements facultatifs, reportez-vous à la [section Configuration](#configuration) .

## Configuration {#configuration}

Le contrôle de l’expérience est disponible par défaut pour les pipelines de production. Elle peut être activée éventuellement pour les pipelines de développement front-end. Dans tous les cas, vous devez définir les chemins de contenu évalués lors de l’exécution du pipeline.

Vous configurez les pages incluses dans le contrôle de l’expérience lors de la configuration de votre pipeline.

1. Selon le type de pipeline que vous souhaitez configurer, suivez les instructions pour :

   * Ajoutez un nouveau [pipeline de production,](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) si vous souhaitez définir les chemins à évaluer par l’audit.
   * Ajoutez un nouveau [pipeline hors production,](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) si vous souhaitez activer l’audit sur un pipeline front-end ou de développement à pile complète.
   * Vous pouvez également [modifier un pipeline existant,](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) et mettre à jour les options existantes.

1. Si vous ajoutez ou modifiez un pipeline hors production pour lequel vous souhaitez utiliser le contrôle de l’expérience, vous devez cocher la case **Audit de l’expérience** sur l’onglet **Code Source** .

   ![Activation de l’audit d’expérience](assets/experience-audit-enable.jpg)

   * Cela n’est nécessaire que pour les pipelines hors production.
   * L’onglet **Audit de l’expérience** s’affiche lorsque la case est cochée.

1. Pour les pipelines de production et hors production, vous définissez les chemins qui doivent être inclus dans le contrôle de l’expérience sur l’onglet **Audit de l’expérience** .

   * Les chemins de page doivent commencer par `/` et sont relatifs à votre site.
   * Par exemple, si votre site est `wknd.site` et que vous souhaitez inclure `https://wknd.site/us/en/about-us.html` dans le contrôle de l’expérience, saisissez le chemin `/us/en/about-us.html`.

   ![Définition d’un chemin pour le contrôle de l’expérience](assets/experience-audit-add-page.png)

1. Appuyez ou cliquez sur **Ajouter une page** et le chemin d’accès est automatiquement renseigné avec l’adresse de votre environnement et ajouté à la table des chemins d’accès.

   ![Enregistrement du chemin d’accès dans la table](assets/experience-audit-page-added.png)

1. Continuez à ajouter des chemins selon vos besoins en répétant les deux étapes précédentes.

   * Vous pouvez ajouter 25 chemins au maximum.
   * Si vous ne définissez aucun chemin, la page d’accueil du site sera incluse par défaut dans l’audit de l’expérience.

1. Cliquez sur **Enregistrer** pour enregistrer votre pipeline.

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

* **Valeur positive** : les pages ont été améliorées sur le test sélectionné depuis la dernière exécution du pipeline de production.

* **Valeur négative** : les pages ont régressé sur le test sélectionné depuis la dernière exécution du pipeline de production.

* **Aucune modification** : les pages ont obtenu le même score depuis la dernière exécution du pipeline de production.

* **N/A** : il n’y a pas de score précédent avec lequel effectuer la comparaison.

![Résultats de l’audit de l’expérience](/help/implementing/cloud-manager/assets/exp-audit-1.png)

### Scores au niveau de la page {#page-level-scores}

En analysant en profondeur n’importe lequel des tests, vous obtiendrez des scores au niveau de la page plus détaillés. Vous pouvez voir le score des pages individuelles pour le test spécifique, ainsi que la modification par rapport à l’exécution de test précédente.

Cliquer sur les détails d’une page donnée fournit des informations sur les éléments de la page qui ont été évalués, et des conseils pour résoudre les problèmes si des possibilités d’amélioration sont détectées.

![Scores au niveau de la page](/help/implementing/cloud-manager/assets/exp-audit-2.png)
