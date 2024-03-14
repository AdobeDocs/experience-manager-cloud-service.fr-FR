---
title: Tableau de bord d’audit de l’expérience
description: Découvrez comment le contrôle de l’expérience valide votre processus de déploiement et vous aide à vous assurer que les modifications déployées répondent aux normes de base en termes de performances, d’accessibilité, de bonnes pratiques et d’optimisation pour les moteurs de recherche par le biais d’une interface de tableau de bord claire et informative.
exl-id: 6d33c3c5-258c-4c9c-90c2-d566eaeb14c0
source-git-commit: 390faed91889e16d06c5024eaf1b4b1ad1427444
workflow-type: tm+mt
source-wordcount: '1957'
ht-degree: 7%

---


# Tableau de bord d’audit de l’expérience {#experience-audit-dashboard}

Découvrez comment le contrôle de l’expérience valide votre processus de déploiement et vous aide à vous assurer que les modifications déployées répondent aux normes de base en termes de performances, d’accessibilité, de bonnes pratiques et d’optimisation pour les moteurs de recherche par le biais d’une interface de tableau de bord claire et informative.

>[!NOTE]
>
>Cette fonctionnalité n’est disponible que pour le [programme d’adoption précoce.](/help/implementing/cloud-manager/release-notes/current.md#early-adoption)
>
>Pour plus d’informations sur la fonction d’audit d’expérience existante pour AEM as a Cloud Service, consultez le document . [Tests de contrôle de l’expérience](/help/implementing/cloud-manager/experience-audit-testing.md)

## Vue d’ensemble {#overview}

Le contrôle de l’expérience valide le processus de déploiement et permet de s’assurer que les modifications sont déployées :

1. Respectent les normes de base en matière de performances, d’accessibilité, de bonnes pratiques, d’optimisation du moteur de recherche (SEO) et d’application web progressive (PWA).

1. N’introduisent pas de régressions.

Le contrôle de l’expérience dans Cloud Manager garantit que l’expérience de l’utilisateur sur le site est de la plus haute qualité.

Les résultats sont informatifs et permettent au responsable de déploiement de voir les scores et les différences existant entre les scores précédents et actuels. Ces informations sont utiles pour déterminer si une régression a été introduite avec le déploiement actuel.

Le contrôle de l’expérience est optimisé par [Google Lighthouse](https://developer.chrome.com/docs/lighthouse/overview/), un outil Open Source de Google, qui est activé dans tous les pipelines de production de Cloud Manager.

## Disponibilité {#availability}

Le contrôle de l’expérience est disponible pour Cloud Manager :

* Pipelines de production Sites par défaut
* Développement de pipelines entièrement empilés, éventuellement
* Pipelines front-end, éventuellement

Voir [Section de configuration](#configuration) pour plus d’informations sur la configuration de l’audit pour les environnements facultatifs.

Les audits sont exécutés dans le cadre du pipeline. Les audits peuvent également être [exécuter à la demande](#on-demand) en dehors des pipelines.

## Configuration {#configuration}

Le contrôle de l’expérience est disponible par défaut pour les pipelines de production. Il peut être éventuellement activé pour le développement de pipelines front-end et plein-pile. Dans tous les cas, vous devez définir les chemins de contenu évalués lors de l’exécution du pipeline.

1. Selon le type de pipeline que vous souhaitez configurer, suivez les instructions pour :

   * Ajouter un nouveau [pipeline de production,](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) si vous souhaitez définir les chemins à évaluer par l’audit.
   * Ajouter un nouveau [pipeline hors production,](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) si vous souhaitez activer l’audit sur un pipeline front-end ou de développement full-stack.
   * Ou vous pouvez [modifier un pipeline existant,](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) et mettre à jour les options existantes.

1. Si vous ajoutez ou modifiez un pipeline hors production pour lequel vous souhaitez utiliser le contrôle de l’expérience, vous devez sélectionner la variable **Audit de l’expérience** de la **Code source** .

   ![Activation du contrôle de l’expérience](assets/experience-audit-enable.jpg)

   * Cela n’est nécessaire que pour les pipelines hors production.
   * La variable **Audit de l’expérience** s’affiche lorsque la case est cochée.

1. Pour les pipelines de production et hors production, vous définissez les chemins qui doivent être inclus dans le contrôle de l’expérience sur le **Audit de l’expérience** .

   * Les chemins de page doivent commencer par `/` et sont relatifs à votre site.
   * Par exemple, si votre site est `wknd.site` et souhaite inclure `https://wknd.site/us/en/about-us.html` dans le contrôle de l’expérience, saisissez le chemin d’accès. `/us/en/about-us.html`.

   ![Définition d’un chemin pour le contrôle de l’expérience](assets/experience-audit-add-page.png)

1. Appuyez ou cliquez sur **Ajouter une page** et le chemin est renseigné automatiquement avec l’adresse de votre environnement et ajouté au tableau des chemins.

   ![Enregistrement du chemin d’accès dans la table](assets/experience-audit-page-added.png)

1. Continuez à ajouter des chemins selon vos besoins en répétant les deux étapes précédentes.

   * Vous pouvez ajouter 25 chemins au maximum.
   * Si vous ne définissez aucun chemin, la page d’accueil du site sera incluse par défaut dans l’audit de l’expérience.

1. Cliquez sur **Enregistrer** pour enregistrer votre pipeline.

## Résultats du contrôle de l’expérience {#results}

Les résultats du contrôle de l’expérience sont présentés dans la section **Test d’évaluation** phase du pipeline de production via la [page d’exécution du pipeline de production.](/help/implementing/cloud-manager/deploy-code.md)

![Tableau de bord dans le pipeline](assets/experience-audit-dashboard.jpg)

Le contrôle de l’expérience fournit les scores Google Lighthouse médians pour [pages configurées](#configuration) et la différence de score par rapport à l’analyse précédente.

Dans cette vue récapitulative, dans la fonction **Test d’évaluation** vous disposez de deux options :

* **[Affichage des pages les plus lentes](#view-slowest-pages)**
* **[Afficher le rapport complet](#view-full-report)**

Outre le résumé présenté dans les détails d’une exécution de pipeline, vous pouvez accéder directement aux résultats complets de l’audit en utilisant la variable **Rapports** onglet du tableau de bord Cloud Manager pour accéder à [rapport complet](#view-full-report) directement.

>[!TIP]
>
>Les sections suivantes décrivent comment afficher les résultats du contrôle de l’expérience.
>
>* Si vous souhaitez obtenir des informations sur le fonctionnement de l’audit, reportez-vous à la section . [Détails de l’évaluation du contrôle de l’expérience.](#details)
>* Si vous souhaitez savoir comment exécuter un audit d’expérience à la demande, consultez la section [Rapports d’audit On-Demand.](#on-demand)
>* Si vous rencontrez des problèmes avec l’audit, reportez-vous à la section [Le Contrôle De L’Expérience Rencontre Des Problèmes.](#issues)
>* Pour obtenir des conseils généraux sur les performances, consultez la section [Conseils généraux sur les performances.](#performance-tips)

### Afficher les pages les plus lentes {#view-slowest-pages}

Appuyez ou cliquez sur **Affichage des pages les plus lentes** ouvre la fonction **5 pages au plus lent** , affichant les cinq pages les moins performantes que vous [configuré pour l’audit.](#configuration)

![Cinq plus lent](assets/experience-audit-slowest-five.jpg)

Les scores sont ventilés par **Performances**, **Accessibilité**, **Bonnes pratiques**, et **SEO** ainsi que l’écart entre chaque mesure et le dernier audit.

Par défaut, la boîte de dialogue s’ouvre avec les scores des appareils mobiles. Vous pouvez le modifier en scores de bureau à l’aide de la fonction **Périphériques** bascule dans la partie supérieure de la boîte de dialogue.

La boîte de dialogue est destinée à un aperçu rapide. Pour obtenir des détails complets, appuyez ou cliquez sur **Afficher le rapport complet**.

### Afficher le rapport complet {#view-full-report}

Vous pouvez afficher le rapport Audit de l’expérience complet en procédant comme suit :

* Appuyez ou cliquez sur **Afficher le rapport complet** dans le **[5 pages au plus lent](#view-slowest-pages)** boîte de dialogue.
* Appuyez ou cliquez sur **Afficher le rapport complet** lors de l’affichage de la variable [exécution d’un pipeline.](#results)
* Appuyez ou cliquez sur le bouton **Rapports** dans Cloud Manager.

La variable **Rapports** de Cloud Manager s’ouvre, affichant le **Suivi d’expérience**.

![Rapports d’audit d’expérience](assets/experience-audit-reports.png)

Le rapport est divisé en deux zones :

* **[Scores de page - Tendance](#trend)**
* **[Résultats de l’analyse de l’expérience](#results)**

#### Scores de page - tendance {#trend}

Par défaut, la vue sélectionnée pour **Scores de page - Tendance** is **scores médians** pour le **6 derniers mois**.

Utilisez la variable **Sélectionner** et **Affichage** des listes déroulantes en haut et en bas du bouton du graphique pour sélectionner respectivement les détails spécifiques à la page et les différentes périodes. Appuyez ou cliquez sur l’icône et le **tendance de mise à jour** en haut du graphique pour appliquer les sélections et actualiser le graphique.

Lorsque vous placez le pointeur de la souris sur le graphique, une info-bulle affiche les valeurs des catégories Google Lighthouse à des moments spécifiques.

![Détails des tendances](assets/experience-audit-trend-details.png)

Si vous appuyez ou cliquez sur le graphique à un moment donné, une fenêtre contextuelle s’ouvre avec le détail de cette analyse. Appuyez ou cliquez sur le bouton **analyse d’audit d’expérience ouverte** pour charger ces résultats d’analyse dans la variable **[Résultats de l’analyse de l’expérience](#scan-results)** .

![Sélectionner une autre analyse](assets/experience-audit-open-scan.png)

#### Résultats de l’analyse de l’audit de l’expérience {#scan-results}

La variable **Résultats de l’analyse de l’expérience** donne des recommandations sur la façon d’améliorer votre score et les détails de toutes les pages analysées. Il est divisé en deux sections :

* **[Recommandations](#recommendations)**
* **[Pages analysées](#scanned-pages)**

##### Recommandations {#recommendations}

La variable **Recommendations** affiche un ensemble agrégé d’informations. Par défaut, les recommandations pour **performance** s’affichent. Utilisez le menu déroulant en regard de la variable **Recommendations** pour passer à une autre catégorie.

![Recommandations](assets/experience-audit-recommendations.png)

Appuyez ou cliquez sur le chevron d’une recommandation pour en afficher les détails.

![Détails de la recommandation](assets/experience-audit-recommendation-details.png)

Lorsqu’elles sont disponibles, les détails de la recommandation étendue contiennent également le pourcentage de l’impact des recommandations, afin de vous aider à vous concentrer sur les modifications ayant le plus d’impact.

Appuyez ou cliquez sur le bouton **afficher les pages ;** dans la vue détails pour afficher les pages auxquelles s’applique la recommandation.

![Pages des détails de la recommandation](assets/experience-audit-details-pages.png)

##### Pages analysées {#scanned-pages}

La variable **Pages analysées** donne des scores de détails sur toutes les pages analysées. Vous pouvez utiliser la variable **Prev** et **Suivant** pour parcourir les résultats et choisir le nombre de pagination de l’affichage.

![Pages analysées](assets/experience-audit-scanned-pages.png)

Si vous appuyez ou cliquez sur le lien d’une page spécifique, la fonction **Sélectionner** du filtre [**Scores de page - Tendance** section](#trend) et affiche la variable **Scores et recommandations** de la page sélectionnée.

![Résultats de la page](assets/experience-audit-page-results.png)

La variable **Rapports bruts** vous donne des scores pour chaque audit de la page. Appuyez ou cliquez sur le bouton **Télécharger** pour récupérer un fichier JSON des données brutes.

![Rapport brut](assets/experience-audit-raw-reports.png)

Un nouvel onglet s’ouvre alors dans votre navigateur, en pointant vers `https://googlechrome.github.io/lighthouse/viewer/` avec une URL signée du rapport Notation d’objet JavaScript brut (JSON) de Lighthouse pour la page sélectionnée, qui s’ouvre automatiquement pour votre inspection détaillée.

![Affichage d’un rapport brut](assets/experience-audit-view-raw-report.png)

## Rapports d’audit On-Demand {#on-demand}

En plus d’être exécutés pendant l’exécution du pipeline, les rapports d’audit d’expérience peuvent également être générés à la demande. Il s’agit d’une bonne solution pour analyser rapidement vos pages sans avoir à exécuter un pipeline.

Pour exécuter une analyse à la demande, accédez au  **Rapports** pour afficher le rapport d’audit complet, puis appuyez ou cliquez sur l’onglet **Exécution de l’analyse** bouton .

![Analyse à la demande](assets/experience-audit-on-demand.png)

Les analyses à la demande déclenchent un audit de l’expérience pour les 25 dernières versions [pages configurées](#configuration) et généralement se terminent en quelques minutes.

Une fois l’analyse terminée, le graphique des scores sera automatiquement mis à jour. Vous pouvez consulter les résultats exactement comme pour une analyse d’exécution de pipeline.

Vous pouvez filtrer le graphique des scores en fonction du type de déclencheur à l’aide de la variable **Déclencheur** sélecteur.

![Filtre Déclencheur](assets/experience-audit-on-demand-trigger.png)

>[!NOTE]
>
>Une analyse à la demande ne peut être lancée que si l’environnement n’est pas supprimé et qu’il n’y a pas d’autres analyses en attente sur le même environnement.

## Problèmes rencontrés dans le contrôle de l’expérience {#issues}

If [pages que vous avez configurées](#configuration) pour que l’audit ne soit pas disponible, le contrôle de l’expérience le reflète.

Le pipeline affiche une section d’erreur extensible pour afficher les chemins d’URL relatifs auxquels il n’a pas pu accéder.

![Problèmes rencontrés par le contrôle de l’expérience](assets/experience-audit-issues.jpg)

Si vous affichez l’intégralité du rapport, les détails sont affichés dans le **[Résultats de l’analyse de l’expérience](#results)** .

![Problèmes de rapport complets](assets/experience-audit-issues-reports.jpeg)

Voici quelques raisons pour lesquelles les pages peuvent ne pas être disponibles :

* La configuration bloque l’accès.
* La page n’existe pas.
* La page redirige qui nécessite une authentification autre que de base.
* Un problème interne s’est produit.
* Etc.

>[!TIP]
>
>[Accès aux rapports bruts](#scanned-pages) pour une page peut fournir des détails sur les raisons pour lesquelles la page n’a pas pu être contrôlée.

## Conseils généraux sur les performances {#performance-tips}

Deux des problèmes d’impact les plus courants qui sont faciles à résoudre concernent les changements de mise en page cumulés (CLS) et la plus grande peinture de contenu (LCP).

Ils peuvent être améliorés en procédant comme suit :

* Ne pas ralentir le chargement des images au-dessus du pli (contenu visible dans le navigateur sans avoir à faire défiler vers le bas).
* Définir correctement la priorité du chargement des ressources (par exemple en chargeant de manière asynchrone les images sous le pli une fois le document chargé).
* Prérécupération des fichiers JavaScript et CSS utilisés pour effectuer le rendu du contenu au-dessus du pli (le cas échéant).
* Réservez l’espace vertical en attribuant un format aux conteneurs qui se chargent lentement ou dont le rendu est effectué ultérieurement.
* Conversion des images au format WebP pour réduire leur taille.
* Utilisation `<picture>` et image `srcset` avec des tailles d’image variables pour différentes tailles de fenêtre d’affichage (et en s’assurant que le redimensionnement fonctionne).

## Détails de l’évaluation du contrôle de l’expérience {#details}

Les détails suivants fournissent des informations supplémentaires sur la manière dont le contrôle de l’expérience évalue votre site. Elles ne sont pas nécessaires à l’utilisation générale de la fonctionnalité et sont fournies ici pour être complètes.

* Bien que la variable [chemins de page d’audit d’expérience configurés](#configuration) afficher la variable `.com` domaine de l’éditeur, l’audit analyse l’origine (`.net`), afin de garantir que les problèmes introduits lors du développement sont détectés.
   * La variable `.com` Le domaine utilise un CDN et peut générer de meilleurs scores ou contenir des résultats mis en cache.
* Dans les pipelines de production à pile complète, l’environnement d’évaluation est analysé.
   * Pour que l’audit fournisse des détails pertinents lors du contrôle, le contenu de l’environnement d’évaluation doit être aussi proche que possible de l’environnement de production.
* Les pages affichées dans la **Sélectionner** dans la liste déroulante [**Scores de page - Tendance** section](#trend) sont toutes des pages connues qui ont été analysées par le passé par le contrôle de l’expérience.
* [Une recommandation](#recommendations) peut présenter un gain potentiel et une différence par rapport à l’analyse précédente.
   * Le contrôle de l’expérience estime le gain potentiel en traitant le rapport brut pour chaque page et en corrélant les octets perdus ou les millisecondes avec un insight qui a un impact pondéré sur le score de performances.
   * L’audit fournit ces informations (ainsi que les pages concernées) pour vous aider à décider quelle recommandation poursuivre.
   * Pour plus d’informations, voir [Section Conseils généraux sur les performances](#performance-tips)
* Étant donné qu’un pipeline front-end peut être déployé dans un environnement existant (ou qu’il peut y avoir plusieurs pipelines front-end ciblant le même environnement) et que les résultats de l’analyse sont agrégés au niveau de l’environnement, les scores, tendances et recommandations s’affichent dans le même environnement sélectionné, quelle que soit l’exécution du pipeline qui a déclenché l’analyse.
