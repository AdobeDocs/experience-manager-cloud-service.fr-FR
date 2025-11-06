---
title: Tableau de bord d’audit d’expérience
description: Découvrez comment le contrôle de l’expérience valide votre processus de déploiement, en vous assurant que les modifications respectent les normes de base en matière de performances, d’accessibilité, de bonnes pratiques et d’optimisation du moteur de recherche. Il fournit une interface de tableau de bord claire et informative pour effectuer le suivi de ces mesures.
exl-id: 6d33c3c5-258c-4c9c-90c2-d566eaeb14c0
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1534'
ht-degree: 8%

---


# Tableau de bord du contrôle de l’expérience {#experience-audit-dashboard}

<!-- Engineer architect over this feature was Bogdan Anton; scrum master Alexandru Nica -->

Découvrez comment le contrôle de l’expérience valide votre processus de déploiement, en vous assurant que les modifications respectent les normes de base en matière de performances, d’accessibilité, de bonnes pratiques et d’optimisation du moteur de recherche (SEO). Il fournit une interface de tableau de bord claire et informative pour effectuer le suivi de ces mesures.

## Vue d’ensemble {#overview}

Le contrôle de l’expérience valide le processus de déploiement et permet de s’assurer que les modifications sont déployées :

1. Respectez les normes de base en matière de performances, d’accessibilité, de bonnes pratiques et d’optimisation du moteur de recherche.
1. N’introduisent pas de régressions.

Le contrôle de l’expérience dans Cloud Manager garantit que l’expérience de l’utilisateur sur le site est de la plus haute qualité.

Les résultats sont informatifs et permettent au responsable de déploiement de voir les scores et les différences existant entre les scores précédents et actuels. Ces informations sont utiles pour déterminer si une régression a été introduite avec le déploiement actuel.

Le contrôle de l’expérience est optimisé par [Google Lighthouse](https://developer.chrome.com/docs/lighthouse/overview/), un outil open source de Google, et est activé dans tous les pipelines de production de Cloud Manager.

## Disponibilité {#availability}

Le contrôle de l’expérience est disponible pour Cloud Manager :

* (Par défaut) Pipelines de production de Sites.
* (Facultatif) Développement de pipelines full stack.
* (Facultatif) Développement de pipelines front-end.

Consultez la [section Configuration](#configuration) pour plus d’informations sur la configuration de l’audit pour les environnements facultatifs.

Les audits sont exécutés dans le cadre du pipeline. Les audits peuvent également être [exécutés à la demande](#on-demand) en dehors des pipelines.

## Configuration {#configuration}

Le contrôle de l’expérience est disponible par défaut pour les pipelines de production. Il peut être activé de manière facultative pour le développement de pipelines full-stack et front-end. Dans tous les cas, vous devez définir les chemins de contenu à évaluer lors de l’exécution du pipeline.

1. Selon le type de pipeline que vous souhaitez configurer, effectuez l’une des opérations suivantes :

   * [Ajoutez un pipeline de production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) pour définir les chemins que l’audit doit évaluer.
   * [Ajoutez un pipeline hors production](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md), si vous souhaitez activer l’audit sur un pipeline front-end ou de développement full-stack.
   * [Modifiez un pipeline existant](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) puis mettez à jour les options existantes.

1. Pour utiliser le contrôle de l’expérience lors de l’ajout ou de la modification d’un pipeline hors production, cochez la case **Contrôle de l’expérience**. Cette option est disponible dans l&#39;onglet **Code Source**.

   ![Activation du contrôle de l’expérience](/help/implementing/cloud-manager/reports/assets/experience-audit-enable.jpg)

   * Nécessaire uniquement pour les pipelines hors production.
   * L’onglet **Contrôle de l’expérience** s’affiche lorsque la case est cochée.

1. Pour les pipelines de production et hors production, vous définissez les chemins d’accès à inclure dans le contrôle de l’expérience dans l’onglet **Contrôle de l’expérience**.

   * Les chemins d’accès doivent commencer par `/` et sont relatifs à votre site.
   * Par exemple, si votre site est `wknd.site` et souhaite inclure des `https://wknd.site/us/en/about-us.html` dans le contrôle de l’expérience, saisissez le chemin d’accès `/us/en/about-us.html`.

   ![Définition d’un chemin pour l’audit d’expérience](/help/implementing/cloud-manager/reports/assets/experience-audit-add-page.png)

1. Cliquez sur **Ajouter une page** et le chemin est renseigné automatiquement avec l’adresse de votre environnement, puis ajouté à la table des chemins.

   ![Enregistrement du chemin d’accès dans la table](/help/implementing/cloud-manager/reports/assets/experience-audit-page-added.png)

1. Continuez à ajouter des chemins selon vos besoins en répétant les deux étapes précédentes.

   * Vous pouvez ajouter 25 chemins au maximum.
   * Si vous ne définissez aucun chemin, la page d’accueil du site sera incluse par défaut dans l’audit d’expérience.

1. Cliquez sur **Enregistrer**.

## Résultats du contrôle de l’expérience {#results}

Les résultats du contrôle de l’expérience sont présentés dans la phase **test d’évaluation** du pipeline de production via la page [exécution du pipeline de production](/help/implementing/cloud-manager/deploy-code.md).

![ Tableau de bord dans le pipeline ](/help/implementing/cloud-manager/reports/assets/experience-audit-dashboard.png)

Le contrôle de l’expérience fournit les scores Google Lighthouse médians pour les [pages configurées](#configuration) et la différence de score par rapport à l’analyse précédente.

Dans cette vue récapitulative de la phase **Test d’évaluation** du pipeline, vous disposez de deux options :

* **[Afficher les pages les plus lentes](#view-slowest-pages)**
* **[Afficher le rapport complet](#view-full-report)**

Vous pouvez accéder aux résultats complets de l’audit en cliquant sur l’onglet **Rapports** dans le tableau de bord Cloud Manager. Outre le résumé affiché dans les détails d’exécution du pipeline, vous pouvez directement afficher [le rapport complet](#view-full-report).

>[!TIP]
>
>Les sections suivantes décrivent comment afficher les résultats du contrôle de l’expérience.
>
>* Pour en savoir plus sur le fonctionnement de l’audit, voir [ Détails de l’évaluation du contrôle de l’expérience ](#details).
>* Pour savoir comment exécuter un contrôle de l’expérience à la demande, voir [Rapports d’audit à la demande](#on-demand).
>* Si vous rencontrez des problèmes lors de l’audit, voir [Le contrôle de l’expérience rencontre des problèmes](#issues).

### Affichage des pages les plus lentes {#view-slowest-pages}

Cliquez sur **Afficher les pages les plus lentes** pour ouvrir la boîte de dialogue **5 pages les plus lentes**. Les cinq pages les moins performantes que vous [avez configurées pour l’audit](#configuration) s’affichent.

![Cinq plus lents](/help/implementing/cloud-manager/reports/assets/experience-audit-slowest-five.png)

Cloud Manager ventile les scores par **Performances**, **Accessibilité**, **Bonnes pratiques** et **SEO**, montrant l’écart de chaque mesure par rapport à l’audit précédent.

Par défaut, la boîte de dialogue s’ouvre avec les scores pour les appareils mobiles. Vous pouvez afficher les scores du bureau à l’aide du bouton (bascule) **Appareils** situé en haut de la boîte de dialogue.

La boîte de dialogue a pour but de vous donner un aperçu rapide. Pour plus d’informations, cliquez sur **Afficher le rapport complet**.

### Afficher le rapport complet {#view-full-report}

Vous pouvez afficher l’intégralité du rapport de contrôle de l’expérience en procédant comme suit :

* Cliquez sur **`View full report`** dans la boîte de dialogue **[5 pages les plus lentes](#view-slowest-pages)**.
* Cliquez sur **`View full report`** lors de l’affichage de l’[exécution d’un pipeline](#results).
* Cliquez sur l’onglet **Rapports** dans Cloud Manager.

L’onglet **Rapports** de Cloud Manager s’ouvre et affiche le **contrôle de l’expérience**.

![Rapports de contrôle de l’expérience](/help/implementing/cloud-manager/reports/assets/experience-audit-reports.png)

Le rapport est divisé en deux parties :

* **[Scores de page — tendance](#trend)**
* **[Résultats de l’analyse du contrôle de l’expérience](#results)**

#### Scores de page — Tendance {#trend}

Par défaut, la vue sélectionnée pour **Scores de page — tendance** est **scores médians** pour l’**Année dernière**.

Vous pouvez choisir d’afficher les tendances pour des catégories Lighthouse spécifiques en cliquant sur le nom de la catégorie dans la légende.

![Tendance sélectionnable](/help/implementing/cloud-manager/reports/assets/experience-audit-trend-selectable.png)

Utilisez la liste déroulante **Sélectionner** en haut du graphique pour sélectionner les détails spécifiques à la page, et les listes déroulantes **Affichage** et **Déclencheur** en bas pour sélectionner différents délais et le type de déclencheur, respectivement.

La liste déroulante **Affichage** offre la possibilité de sélectionner une période prédéfinie ou un intervalle personnalisé pour une vue plus spécifique.

![Vue Tendance](/help/implementing/cloud-manager/reports/assets/experience-audit-trend-view.png)

Lorsque vous déplacez le pointeur de la souris sur le graphique, une info-bulle affiche les valeurs des catégories Google Lighthouse à des moments spécifiques.

![Détails de la tendance](/help/implementing/cloud-manager/reports/assets/experience-audit-trend-details.png)

Si vous cliquez sur le graphique à un moment donné, un pop-up s’ouvre avec les détails de cette analyse. Cliquez sur le **ouvrir l’analyse de contrôle de l’expérience** pour charger les résultats de cette analyse dans la section **[Résultats de l’analyse du contrôle de l’expérience](#scan-results)**.

![Sélectionner une analyse différente](/help/implementing/cloud-manager/reports/assets/experience-audit-open-scan.png)

#### Résultats de l’analyse de l’audit d’expérience {#scan-results}

La section **Résultats de l’analyse du contrôle de l’expérience** donne des détails sur les scores de toutes les pages numérisées. Utilisez les boutons **Précédent** et **Suivant** pour parcourir les résultats et choisir le nombre d’affichages à paginer.

![Pages numérisées](/help/implementing/cloud-manager/reports/assets/experience-audit-scanned-pages.png)

Cliquez sur le lien d’une page particulière pour mettre à jour le filtre **Sélectionner** de la section [**Scores de la page — Tendance** ](#trend) et afficher l’onglet **Rapports bruts** qui vous donne les scores de chaque audit de la page. Cliquez sur la date du rapport dans la colonne **Rapport Lighthouse** pour récupérer un fichier JSON des données brutes.

![Rapport brut](/help/implementing/cloud-manager/reports/assets/experience-audit-raw-reports.png)

Un nouvel onglet qui s’ouvre dans votre navigateur vous dirige vers `https://googlechrome.github.io/lighthouse/viewer/`. Il charge automatiquement une URL signée contenant le rapport JSON brut Lighthouse pour la page sélectionnée, ce qui permet une inspection détaillée.

![Affichage du rapport brut](/help/implementing/cloud-manager/reports/assets/experience-audit-view-raw-report.png)

## Rapports d&#39;audit d&#39;analyse à la demande {#on-demand}

En plus d’être exécutés pendant l’exécution du pipeline, les rapports de contrôle de l’expérience peuvent également être générés à la demande. Cette option est une bonne solution pour analyser rapidement vos pages, sans avoir à exécuter un pipeline.

Pour exécuter une analyse à la demande, accédez à l’onglet **Rapports** afin de voir le rapport d’audit complet, puis cliquez sur le bouton **Exécuter l’analyse**.

![ Analyse à la demande ](/help/implementing/cloud-manager/reports/assets/experience-audit-on-demand.png)

Le bouton **Exécuter l’analyse** devient indisponible et est marqué d’une icône d’horloge lorsqu’une analyse à la demande est déjà en cours d’exécution.

![Analyse à la demande en cours](/help/implementing/cloud-manager/reports/assets/experience-audit-on-demand-running.png)

Les analyses à la demande déclenchent un contrôle de l’expérience pour les 25 dernières [pages configurées](#configuration) et se terminent généralement en quelques minutes.

Une fois l’opération terminée, le graphique des scores est automatiquement mis à jour et vous pouvez examiner les résultats exactement comme pour une analyse d’exécution de pipeline.

Vous pouvez filtrer le graphique de scores en fonction du type de déclencheur à l’aide du sélecteur **Déclencheur**.

![Filtre Trigger](/help/implementing/cloud-manager/reports/assets/experience-audit-on-demand-trigger.png)

>[!NOTE]
>
>Une analyse à la demande ne peut être lancée que si l’environnement n’est pas supprimé et qu’il n’y a pas d’autres analyses en attente sur le même environnement.

## Le contrôle de l’expérience rencontre des problèmes {#issues}

Si les [pages que vous avez configurées](#configuration) à auditer n’étaient pas disponibles ou si l’audit comportait d’autres erreurs, l’audit de l’expérience reflète ce fait.

Le pipeline affiche une section d’erreur extensible pour afficher les chemins d’URL relatifs auxquels il n’a pas pu accéder.

![Problèmes rencontrés par le contrôle de l’expérience](/help/implementing/cloud-manager/reports/assets/experience-audit-issues.png)

Si vous consultez le rapport complet, les détails sont affichés dans la section **[Résultats de l’analyse du contrôle de l’expérience](#results)**, qui peut également être développée.

![Problèmes de rapport complet](/help/implementing/cloud-manager/reports/assets/experience-audit-issues-report.png)

Voici quelques raisons pour lesquelles les pages peuvent ne pas être disponibles :

* La configuration bloque l’accès.
* La page n’existe pas.
* Les redirections de page nécessitant une authentification autre que de base.
* Un problème interne s’est produit.

>[!TIP]
>
>L’[accès aux rapports bruts](#scan-results) d’une page peut fournir des détails sur les raisons pour lesquelles la page n’a pas pu être contrôlée.

## Détails de l’évaluation du contrôle de l’expérience {#details}

Les détails suivants apportent des informations supplémentaires sur la manière dont le contrôle de l’expérience évalue votre site. Ils ne sont pas nécessaires à l’utilisation générale de la fonctionnalité et sont fournis ici pour plus d’exhaustivité.

* L’audit analyse le domaine d’origine (`.com`) à partir des chemins de page du contrôle de l’expérience [ configurés](#configuration) de l’éditeur afin de simuler de vraies expériences utilisateur, ce qui vous aide à prendre de meilleures décisions concernant la gestion et l’optimisation de vos sites web.
* Dans les pipelines de production full stack, l’environnement d’évaluation est analysé. Pour que l’audit fournisse des détails pertinents lors de l’audit, le contenu de l’environnement d’évaluation doit être aussi proche que possible de l’environnement de production.
* Les pages affichées dans la liste déroulante **Sélectionner** dans la section [**Scores de page — tendance** ](#trend) sont toutes des pages connues que le contrôle de l’expérience a parcourues par le passé.
