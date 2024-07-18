---
title: Tableau de bord d’audit de l’expérience
description: Découvrez comment le contrôle de l’expérience valide votre processus de déploiement et vous aide à vous assurer que les modifications déployées répondent aux normes de base en termes de performances, d’accessibilité, de bonnes pratiques et d’optimisation pour les moteurs de recherche par le biais d’une interface de tableau de bord claire et informative.
exl-id: 6d33c3c5-258c-4c9c-90c2-d566eaeb14c0
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: c7362a77fd929d812db3cd40bf01763ed3bef02c
workflow-type: tm+mt
source-wordcount: '1995'
ht-degree: 7%

---


# Tableau de bord d’audit de l’expérience {#experience-audit-dashboard}

Découvrez comment le contrôle de l’expérience valide votre processus de déploiement et vous aide à vous assurer que les modifications déployées répondent aux normes de base en termes de performances, d’accessibilité, de bonnes pratiques et d’optimisation pour les moteurs de recherche par le biais d’une interface de tableau de bord claire et informative.

>[!NOTE]
>
>Cette fonctionnalité n’est disponible que pour le [programme d’adoption précoce.](/help/implementing/cloud-manager/release-notes/current.md#early-adoption)
>
>Pour plus d’informations sur la fonction d’audit d’expérience existante pour AEM as a Cloud Service, consultez le document [Test d’audit d’expérience](/help/implementing/cloud-manager/experience-audit-testing.md)

## Vue d’ensemble {#overview}

Le contrôle de l’expérience valide le processus de déploiement et permet de s’assurer que les modifications sont déployées :

1. Respectent les normes de base en matière de performances, d’accessibilité, de bonnes pratiques, d’optimisation du moteur de recherche (SEO) et d’application web progressive (PWA).

1. N’introduisent pas de régressions.

Le contrôle de l’expérience dans Cloud Manager garantit que l’expérience de l’utilisateur sur le site est de la plus haute qualité.

Les résultats sont informatifs et permettent au responsable de déploiement de voir les scores et les différences existant entre les scores précédents et actuels. Ces informations sont utiles pour déterminer si une régression a été introduite avec le déploiement actuel.

Le contrôle de l’expérience est optimisé par [Google Lighthouse](https://developer.chrome.com/docs/lighthouse/overview/), un outil open source de Google, et est activé dans tous les pipelines de production Cloud Manager.

## Disponibilité {#availability}

Le contrôle de l’expérience est disponible pour Cloud Manager :

* Pipelines de production Sites par défaut
* Développement de pipelines entièrement empilés, éventuellement
* Développement de pipelines front-end, éventuellement

Pour plus d’informations sur la configuration de l’audit pour les environnements facultatifs, reportez-vous à la [section Configuration](#configuration) .

Les audits sont exécutés dans le cadre du pipeline. Les audits peuvent également être [exécutés à la demande](#on-demand) en dehors des pipelines.

## Configuration {#configuration}

Le contrôle de l’expérience est disponible par défaut pour les pipelines de production. Il peut être éventuellement activé pour le développement de pipelines front-end et plein-pile. Dans tous les cas, vous devez définir les chemins de contenu évalués lors de l’exécution du pipeline.

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

## Résultats du contrôle de l’expérience {#results}

Les résultats du contrôle de l’expérience sont présentés dans la phase **Test d’évaluation** du pipeline de production via la [ page d’exécution du pipeline de production.](/help/implementing/cloud-manager/deploy-code.md)

![Tableau de bord dans le pipeline](assets/experience-audit-dashboard.jpg)

Le contrôle de l’expérience fournit les scores Google Lighthouse médians pour les [pages configurées](#configuration) et la différence de score par rapport à l’analyse précédente.

Dans cette vue récapitulative de la phase **Test d’évaluation** du pipeline, vous disposez de deux options :

* **[Afficher les pages les plus lentes](#view-slowest-pages)**
* **[Afficher le rapport complet](#view-full-report)**

Outre le résumé présenté dans les détails d’une exécution de pipeline, vous pouvez accéder directement aux résultats complets de l’audit en utilisant l’onglet **Rapports** du tableau de bord Cloud Manager pour accéder directement à [le rapport complet](#view-full-report).

>[!TIP]
>
>Les sections suivantes décrivent comment afficher les résultats du contrôle de l’expérience.
>
>* Si vous souhaitez obtenir des détails sur le fonctionnement de l’audit, reportez-vous à la section [Détails de l’évaluation du contrôle de l’expérience.](#details)
>* Si vous souhaitez savoir comment exécuter un audit d’expérience à la demande, consultez la section [Rapports d’audit On-Demand.](#on-demand)
>* Si vous rencontrez des problèmes avec l’audit, reportez-vous à la section [Problèmes liés à l’audit d’expérience.](#issues)
>* Pour obtenir des conseils généraux sur les performances, consultez la section [Conseils généraux sur les performances.](#performance-tips)

### Afficher les pages les plus lentes {#view-slowest-pages}

Appuyez ou cliquez sur **Afficher les pages les plus lentes** pour ouvrir la boîte de dialogue **5 pages les plus lentes**, affichant les cinq pages les moins performantes que vous [ avez ](#configuration) configurées pour effectuer un audit.

![ {5](assets/experience-audit-slowest-five.png)

Les scores sont ventilés par **Performance**, **Accessibilité**, **Bonnes pratiques** et **SEO** avec l’écart de chaque mesure par rapport au dernier audit.

Par défaut, la boîte de dialogue s’ouvre avec les scores des appareils mobiles. Vous pouvez modifier ce paramètre en scores de bureau à l’aide de la bascule **Périphériques** située en haut de la boîte de dialogue.

La boîte de dialogue est destinée à un aperçu rapide. Pour plus d’informations, appuyez ou cliquez sur **Afficher le rapport complet**.

### Afficher le rapport complet {#view-full-report}

Vous pouvez afficher le rapport Audit de l’expérience complet en procédant comme suit :

* Appuyez ou cliquez sur **Afficher le rapport complet** dans la boîte de dialogue **[5 pages les plus lentes](#view-slowest-pages)**.
* Appuyez ou cliquez sur **Afficher le rapport complet** lors de l’affichage de l’ [exécution d’un pipeline.](#results)
* Appuyez ou cliquez sur l’onglet **Rapports** dans Cloud Manager.

L’onglet **Rapports** de Cloud Manager s’ouvre, affichant le **audit de l’expérience**.

![Rapports d’audit d’expérience](assets/experience-audit-reports.png)

Le rapport est divisé en deux zones :

* **[Scores de page - tendance](#trend)**
* **[Résultats de l’analyse de l’expérience](#results)**

#### Scores de page - tendance {#trend}

Par défaut, la vue sélectionnée pour **Scores de page - tendance** est **Scores médians** pour les **6 derniers mois**.

Utilisez les menus déroulants **Sélectionner** et **Afficher** en haut et en bas du bouton du graphique pour sélectionner respectivement les détails spécifiques à la page et différentes périodes. Appuyez ou cliquez sur le bouton et **mettre à jour la tendance** en haut du graphique pour appliquer les sélections et actualiser le graphique.

Lorsque vous placez le pointeur de la souris sur le graphique, une info-bulle affiche les valeurs des catégories Google Lighthouse à des moments spécifiques.

![Détails des tendances](assets/experience-audit-trend-details.png)

Si vous appuyez ou cliquez sur le graphique à un moment donné, une fenêtre contextuelle s’ouvre avec le détail de cette analyse. Appuyez ou cliquez sur l’**analyse d’audit d’expérience ouverte** pour charger ces résultats d’analyse dans la section **[résultats d’analyse d’expérience](#scan-results)** .

![Sélectionner une autre analyse](assets/experience-audit-open-scan.png)

#### Résultats de l’analyse de l’audit de l’expérience {#scan-results}

La section **Résultats de l’analyse de l’expérience** fournit des recommandations sur la manière d’améliorer votre score et les détails de toutes les pages analysées. Il est divisé en deux sections :

* **[Recommandations](#recommendations)**
* **[Pages numérisées](#scanned-pages)**

##### Recommandations {#recommendations}

La section **Recommendations** présente un ensemble agrégé d’informations. Par défaut, les recommandations pour **performance** s’affichent. Utilisez la liste déroulante en regard de l’en-tête **Recommendations** pour passer à une autre catégorie.

![Recommandations](assets/experience-audit-recommendations.png)

Appuyez ou cliquez sur le chevron d’une recommandation pour en afficher les détails.

![Détails de la recommandation](assets/experience-audit-recommendations-details.png)

Lorsqu’elles sont disponibles, les détails de la recommandation étendue contiennent également le pourcentage de l’impact des recommandations, afin de vous aider à vous concentrer sur les modifications ayant le plus d’impact.

Appuyez ou cliquez sur le lien **Afficher les pages** dans la vue Détails pour afficher les pages auxquelles la recommandation s’applique.

![Pages pour les détails de la recommandation](assets/experience-audit-details-pages.png)

##### Pages analysées {#scanned-pages}

La section **Pages analysées** donne des scores de détails sur toutes les pages numérisées. Vous pouvez utiliser les boutons **Préc** et **Suivant** pour parcourir les résultats et choisir le nombre de pagination de l’affichage.

![Pages numérisées](assets/experience-audit-scanned-pages.png)

Appuyez ou cliquez sur le lien d’une page spécifique pour mettre à jour le filtre **Sélectionner** de la section [**Scores de page - Tendance**](#trend) et affiche l’onglet **Scores &amp; recommandations** pour la page sélectionnée.

![Résultats de page](assets/experience-audit-page-results.png)

L’onglet **Rapports bruts** donne des scores pour chaque audit de la page. Appuyez ou cliquez sur la date du rapport dans la colonne **Rapport Lighthouse** pour récupérer un fichier JSON des données brutes.

![Rapport brut](assets/experience-audit-raw-reports.png)

Un nouvel onglet s’ouvre alors dans votre navigateur, pointant vers `https://googlechrome.github.io/lighthouse/viewer/` avec une URL signée du rapport Notation d’objet JavaScript (JSON) Lighthouse brute pour la page sélectionnée, qui s’ouvre automatiquement pour votre inspection détaillée.

![Affichage du rapport brut](assets/experience-audit-view-raw-report.png)

## Rapports d’audit On-Demand {#on-demand}

En plus d’être exécutés pendant l’exécution du pipeline, les rapports d’audit d’expérience peuvent également être générés à la demande. Il s’agit d’une bonne solution pour analyser rapidement vos pages sans avoir à exécuter un pipeline.

Pour exécuter une analyse à la demande, accédez à l’onglet **Rapports** pour afficher le rapport d’audit complet, puis appuyez ou cliquez sur le bouton **Exécuter l’analyse** .

![Analyse à la demande](assets/experience-audit-on-demand.png)

Le bouton **Exécuter l’analyse** n’est plus disponible et est signalé par une icône d’horloge lorsqu’une analyse à la demande est déjà en cours d’exécution.

![Analyse à la demande en cours](assets/experience-audit-on-demand-running.png)

Les analyses à la demande déclenchent un audit de l’expérience pour les 25 [dernières pages configurées](#configuration) et se terminent généralement en quelques minutes.

Une fois l’analyse terminée, le graphique des scores sera automatiquement mis à jour. Vous pouvez consulter les résultats exactement comme pour une analyse d’exécution de pipeline.

Vous pouvez filtrer le graphique des scores en fonction du type de déclencheur à l’aide du sélecteur **Déclencheur** .

![Filtre de déclenchement](assets/experience-audit-on-demand-trigger.png)

>[!NOTE]
>
>Une analyse à la demande ne peut être lancée que si l’environnement n’est pas supprimé et qu’il n’y a pas d’autres analyses en attente sur le même environnement.

## Problèmes rencontrés dans le contrôle de l’expérience {#issues}

Si les [pages que vous avez configurées](#configuration) à contrôler n’étaient pas disponibles ou qu’il y avait d’autres erreurs dans l’audit, le contrôle de l’expérience le reflète.

Le pipeline affiche une section d’erreur extensible pour afficher les chemins d’URL relatifs auxquels il n’a pas pu accéder.

![Problèmes rencontrés par l’audit d’expérience](assets/experience-audit-issues.jpg)

Si vous affichez le rapport complet, les détails sont affichés dans la section **[Résultats de l’analyse de l’audit d’expérience](#results)**, qui peut également être développée.

![Problèmes de rapport complets](assets/experience-audit-issues-report.png)

Voici quelques raisons pour lesquelles les pages peuvent ne pas être disponibles :

* La configuration bloque l’accès.
* La page n’existe pas.
* La page redirige qui nécessite une authentification autre que de base.
* Un problème interne s’est produit.
* Etc.

>[!TIP]
>
>[L’accès aux rapports bruts](#scanned-pages) pour une page peut fournir des détails sur les raisons pour lesquelles la page n’a pas pu être contrôlée.

## Conseils généraux sur les performances {#performance-tips}

Deux des problèmes d’impact les plus courants qui sont faciles à résoudre concernent les changements de mise en page cumulés (CLS) et la plus grande peinture de contenu (LCP).

Ils peuvent être améliorés en procédant comme suit :

* Ne pas ralentir le chargement des images au-dessus du pli (contenu visible dans le navigateur sans avoir à faire défiler vers le bas).
* Définir correctement la priorité du chargement des ressources (par exemple en chargeant de manière asynchrone les images sous le pli une fois le document chargé).
* Prérécupération des fichiers JavaScript et CSS utilisés pour effectuer le rendu du contenu au-dessus du pli (si nécessaire).
* Réservez l’espace vertical en attribuant un format aux conteneurs qui se chargent lentement ou dont le rendu est effectué ultérieurement.
* Conversion des images au format WebP pour réduire leur taille.
* Utilisation de `<picture>` et d’image `srcset` avec des tailles d’image variées pour différentes tailles de fenêtre d’affichage (et pour s’assurer que le redimensionnement fonctionne).

## Détails de l’évaluation du contrôle de l’expérience {#details}

Les détails suivants fournissent des informations supplémentaires sur la manière dont le contrôle de l’expérience évalue votre site. Elles ne sont pas nécessaires à l’utilisation générale de la fonctionnalité et sont fournies ici pour être complètes.

* L’audit analyse le domaine d’origine (`.com`) tel que défini dans les [ chemins de page d’audit d’expérience configurés](#configuration) de l’éditeur afin de simuler plus précisément les expériences utilisateur réelles et de vous aider à prendre des décisions plus éclairées concernant la gestion et l’optimisation de vos sites web.
* Dans les pipelines de production à pile complète, l’environnement d’évaluation est analysé.
   * Pour que l’audit fournisse des détails pertinents lors du contrôle, le contenu de l’environnement d’évaluation doit être aussi proche que possible de l’environnement de production.
* Les pages affichées dans la liste déroulante **Sélectionner** de la section [**Scores de page - tendance**](#trend) sont toutes des pages connues qui ont été analysées par le passé par le contrôle de l’expérience.
* [Une recommandation](#recommendations) peut présenter un gain potentiel et une différence par rapport à l’analyse précédente.
   * Le contrôle de l’expérience estime le gain potentiel en traitant le rapport brut pour chaque page et en corrélant les octets perdus ou les millisecondes avec un insight qui a un impact pondéré sur le score de performances.
   * L’audit fournit ces informations (ainsi que les pages concernées) pour vous aider à décider quelle recommandation poursuivre.
   * Pour plus d’informations, reportez-vous à la [section Conseils généraux sur les performances](#performance-tips)
* Étant donné qu’un pipeline front-end peut être déployé dans un environnement existant (ou qu’il peut y avoir plusieurs pipelines front-end ciblant le même environnement) et que les résultats de l’analyse sont agrégés au niveau de l’environnement, les scores, tendances et recommandations s’affichent dans le même environnement sélectionné, quelle que soit l’exécution du pipeline qui a déclenché l’analyse.
