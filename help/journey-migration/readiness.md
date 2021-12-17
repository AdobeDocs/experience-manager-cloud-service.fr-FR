---
title: Phase de préparation
description: Découvrez les étapes à suivre pour vous assurer que votre installation AEM est prête à être déplacée vers le cloud.
source-git-commit: 2b2b18993d2782f01cc9361e1d558fb0d1a8c530
workflow-type: tm+mt
source-wordcount: '1965'
ht-degree: 10%

---

# Phase de préparation {#readiness-phase}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_planning"
>title="Planification de votre Transition"
>abstract="Avant de commencer votre parcours de transition vers Cloud Service, vous devez vous familiariser avec AEM as a Cloud Service, mais aussi examiner les modifications notables qui y ont été apportées, ainsi que les fonctionnalités remplacées ou obsolètes."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=fr" text="Analyseur des bonnes pratiques"

Au cours de cette phase du Parcours de migration as a Cloud Service AEM, vous allez vous familiariser avec AEM as a Cloud Service, passer en revue les modifications notables qu’il a introduites et comprendre ce qu’il faut pour planifier une migration réussie vers le cloud.

## Un peu d’histoire...  {#story-so-far}

le document précédent, [Prise en main de la transition vers AEM as a Cloud Service](/help/journey-migration/getting-started.md), présente la liste des phases que vous devez subir pour migrer vers AEM as a Cloud Service, ainsi que les avantages de cette migration.

## Objectif {#objective}

Ce document vous aide à comprendre les facteurs à prendre en compte pour vous assurer que votre installation AEM est prête à être déplacée vers le cloud :

* En savoir plus sur les modifications notables et les fonctionnalités obsolètes
* Comprendre comment planifier la migration vers AEM as a Cloud Service

## Examinez les modifications notables apportées à l’architecture as a Cloud Service AEM {#notable-changes-in-aem-cloud-service-architecture}

AEM as a Cloud Service offre de très nombreuses fonctionnalités et possibilités nouvelles pour gérer vos projets AEM.

Outre ces améliorations, plusieurs différences ont été introduites entre les installations on-premise d’AEM et d’Adobe Managed Services, par rapport à AEM as a Cloud Service.

La liste des éléments du tableau ci-dessous est le sous-ensemble des modifications les plus pertinentes pour une migration vers AEM as a Cloud Service. Vous pouvez consulter la liste complète des modifications notables [here](/help/release-notes/aem-cloud-changes.md).

<table>
<thead>
  <tr>
    <th>Qu’est-ce qui a changé ?</th>
    <th>Référence</th>
    <th>Principales mesures à prendre</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Séparation des filtres modifiables et non modifiables en packages correspondants</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/aem-cloud-changes.html?lang=fr">AEM modifications notables as a Cloud Service</a><br><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html#mutable-vs-immutable">AEM structure de projet pour AEM as a Cloud Service</a></td>
    <td>Un package unique pouvant être déployé dans AEM as a Cloud Service peut comporter des sous-modules, principalement pour contenir du contenu modifiable et non modifiable séparé dans leurs propres modules.</td>
  </tr>
  <tr>
    <td>Repo Init </td>
    <td><a href="https://sling.apache.org/documentation/bundles/repository-initialization.html#the-repoinit-repository-initialization-language">Documentation Apache Sling RepoInit</a></td>
    <td>Les scripts repoinit sont la bonne pratique pour créer les structures de noeud, les utilisateurs, les groupes ou les utilisateurs de service initiaux. Comme ces scripts peuvent être ciblés par le mode d’exécution et gérables via le déploiement du package de code, ils offrent une grande flexibilité pour réaliser les tâches d’initialisation du référentiel.</td>
  </tr>
  <tr>
    <td>Les modes d’exécution personnalisés ne sont pas autorisés</td>
    <td></td>
    <td>Seuls les modes d’exécution prêts à l’emploi avec AEM as a Cloud Service sont pris en charge.<br>Lorsque d’autres environnements de développement sont ajoutés, ils sont tous liés au mode d’exécution "dev".</td>
  </tr>
  <tr>
    <td>L’exécution du pipeline de Cloud Manager est la seule méthode de déploiement</td>
    <td></td>
    <td>Dans AEM as a Cloud Service, l’accès à /system/console n’est pas autorisé. Par conséquent, toutes les configurations OSGi doivent faire partie du code et doivent être déployées en tant que code.<br>Les configurations OSGi sont disponibles en mode lecture seule pour un affichage via Developer Console via Cloud Manager.</td>
  </tr>
  <tr>
    <td>Les agents de réplication sont remplacés par la distribution de contenu Sling</td>
    <td></td>
    <td>Le concept de l’agent de réplication est remplacé par Sing Content Distribution. Si des personnalisations utilisent des agents de réplication, elles doivent être repensées.<br>La réplication inverse n’est pas prise en charge</td>
  </tr>
  <tr>
    <td>CRX/DE et gestionnaire de modules</td>
    <td></td>
    <td>CRX/DE n’est autorisé que dans l’environnement de développement.<br>Le gestionnaire de modules est accessible sur toutes les instances d’auteur, mais les modules qui vont être déployés ne doivent contenir que du contenu modifiable ( par exemple : /content ou /conf)</td>
  </tr>
  <tr>
    <td>Intégré au réseau de diffusion de contenu et obtenez votre propre réseau de diffusion de contenu</td>
    <td></td>
    <td>AEM as a Cloud Service inclut le réseau de diffusion de contenu pour tous les environnements, optimisé pour la plupart des cas d’utilisation.<br>Si vous souhaitez configurer votre propre réseau de diffusion de contenu, vous devez envoyer une demande à l’assistance Adobe pour qu’il soit approuvé.<br>S’il est approuvé, le réseau de diffusion de contenu pointe vers Fastly et non vers AEM des instances dans aucun environnement.</td>
  </tr>
  <tr>
    <td>Tâches à long terme</td>
    <td></td>
    <td>Évitez d’exécuter des tâches longues telles que des planificateurs Sling ou des tâches Cron, car les instances AEM qui s’exécutent dans les conteneurs peuvent venir et se rendre à tout moment.<br>Repensez ces fonctionnalités pour les décharger vers Adobe I/O.</td>
  </tr>
  <tr>
    <td>Passer aux opérations asynchrones</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/asynchronous-jobs.html?lang=en#configuring-asynchronous-msm-operations">Configuration des opérations asynchrones</a></td>
    <td>Pour améliorer les performances globales de vos environnements, certaines opérations sont exécutées en mode asynchrone. Les tâches asynchrones seront mises en file d’attente et exécutées lorsque les ressources système seront disponibles.</td>
  </tr>
  <tr>
    <td>Stratégies d’authentification et d’intégration basées sur les jetons</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#the-server-to-server-flow">Génération de jetons d’accès pour les API côté serveur</a><br><a href="https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=fr#authentication">Tutoriel sur l’authentification basée sur les jetons</a></td>
    <td>Il est courant que des systèmes externes à AEM tentent d’effectuer des opérations HTTP dans AEM.<br>L’approche recommandée consiste à mettre en oeuvre les stratégies décrites ici plutôt que de compter sur la création de noms d’utilisateur locaux avec des mots de passe dans AEM.</td>
  </tr>
  <tr>
    <td>E/S de fichier/utilisation du disque</td>
    <td></td>
    <td>Comme il n’existe aucune garantie quant à la quantité d’espace disque allouée et que les instances dans les conteneurs vont et viennent, il n’est pas recommandé d’utiliser les opérations d’E/S de fichier pour écrire ou lire à partir du disque joint à l’instance AEM.</td>
  </tr>
  <tr>
    <td>Workflow Ressource de mise à jour de gestion des actifs numériques</td>
    <td><a href="https://experienceleague.adobe.com/docs/asset-compute/using/introduction.html?lang=en">Asset Compute Service</a></td>
    <td>Les étapes de traitement des médias qui font partie du workflow Ressources de mise à jour de gestion des actifs numériques sont désormais remplacées par le service Asset compute.</td>
  </tr>
  <tr>
    <td>Méthodes de chargement de ressources et étapes de processus prises en charge dans AEM as a Cloud Service</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/developer-reference-material-apis.html?lang=en#post-processing-workflows-steps">Télécharger des comparaisons d’API et les étapes de processus WF prises en charge</a></td>
    <td>Dans AEM as a Cloud Service, pendant le chargement ou le téléchargement d’une ressource, la ressource est diffusée directement dans ou hors du stockage binaire.</br>Toutes les étapes de processus de workflow ne sont pas prises en charge dans AEMaaCS.</td>
  </tr>
  <tr>
    <td>Lanceurs de workflow</td>
    <td></td>
    <td>Supprimez de votre code tous les lanceurs de workflow qui déclenchent un workflow de ressource de mise à jour de gestion des actifs numériques personnalisé ou en standard.</br>Toutes les ressources chargées dans AEM as a Cloud Service seront traitées par le service de traitement des ressources. Il existe une configuration OSGi de post-traitement de workflow qui peut être utilisée pour déclencher des étapes de traitement personnalisées supplémentaires.</td>
  </tr>
  <tr>
    <td>Étapes de rendu personnalisées</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/asset-microservices-configure-and-use.html?lang=en#manage">Profils de traitement</a></td>
    <td>Toute génération de rendu, conversion d’image ou codage vidéo personnalisé doit être déchargée vers le service de traitement des ressources en créant les profils de traitement correspondants.</td>
  </tr>
  <tr>
    <td>Recherche et indexation de contenu</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en">Modifications de la recherche et de l’indexation de contenu</a></td>
    <td>Le traitement sous-jacent des index est considérablement modifié et le moment où il est lancé.<br>Comprendre et refactoriser complètement les index Oak avant de les gérer dans le code que vous allez déployer.</td>
  </tr>
  <tr>
    <td>Toutes les tâches de maintenance ne sont pas configurables</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/maintenance.html?lang=en">AEM tâches de maintenance as a Cloud Service</a></td>
    <td>Vous ne pouvez configurer que certaines tâches de maintenance avec AEM as a Cloud Service.</td>
  </tr>
  <tr>
    <td>Modifications apportées au référentiel de publication</td>
    <td></td>
    <td>Les modifications directes apportées au référentiel de publication ne sont pas autorisées, à l’exception de celles effectuées sous /home. Il est toujours recommandé d’apporter les modifications à l’auteur et de les distribuer. Toutes les modifications de code et de configuration doivent être déployées via le pipeline Cloud Manager correspondant.</td>
  </tr>
  <tr>
    <td>Configurations et mise en cache du Dispatcher</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html?lang=fr#content-delivery">Dispatcher en mode cloud</a><br><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/caching.html?lang=en#other-content">Gestion du cache<br></td>
    <td>Les configurations de Dispatcher doivent suivre une structure spécifique.<br>Les configurations doivent être gérées dans le cadre du code et déployées via le pipeline Cloud Manager.</td>
  </tr>
  <tr>
    <td>Sauvegarde et restauration</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/backup.html?lang=en">Sauvegarde et restauration as a Cloud Service AEM</a></td>
    <td></td>
  </tr>
</tbody>
</table>

## Fonctionnalités obsolètes {#deprecated-features}

Adobe étudie constamment les fonctionnalités du produit de façon à les réinventer au fil du temps ou à remplacer les fonctions plus anciennes par des variantes plus modernes, pour améliorer la valeur client globale, le tout en faisant toujours attention à la compatibilité ascendante.

Nous vous recommandons de consulter la [Fonctionnalités obsolètes](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/deprecated-removed-features.html?lang=fr#deprecated-features) pour vous familiariser avec les fonctionnalités signalées comme étant obsolètes dans Experience Manager as a Cloud Service et voir l’impact sur votre déploiement AEM.

## Planification de la révision de votre installation AEM {#review-planning}

Une fois que vous vous êtes habitué aux modifications introduites avec AEM as a Cloud Service, il est temps de commencer à planifier une révision de votre installation existante, afin d’évaluer le niveau de modifications requis pour la déplacer vers le cloud.

La figure suivante présente les principales étapes impliquées lors de la phase de révision :

![image](/help/journey-migration/assets/planning-phaseimg1.png)

Ensuite, nous allons explorer en détail ce que chacune de ces étapes signifie.

### Évaluation du niveau de préparation pour la transition vers Cloud Service {#assess-cloud-readiness}

La première étape consiste à évaluer votre volonté de passer de votre version d’AEM existante à Cloud Service et à déterminer les domaines qui nécessiteront une refactorisation afin d’être compatibles avec AEM as a Cloud Service.

Vous devrez effectuer une évaluation complète de votre code source AEM actuel par rapport aux modifications notables et aux fonctionnalités obsolètes afin de déterminer le niveau d’effort attendu dans le parcours de transition.

Le nombre de résultats influencera directement les calendriers et la réussite globale du projet. Par conséquent, il est recommandé de découvrir autant que possible la planification de la diffusion ou de lancer les conversations nécessaires pour reconcevoir les personnalisations requises pour être en conformité avec AEM bonne pratique as a Cloud Service.

**Analyseur des bonnes pratiques**

Vous pouvez accélérer l’évaluation en exécutant l’analyseur des bonnes pratiques par rapport à votre version d’AEM actuelle. Une bonne compréhension de son fonctionnement est essentielle pour accélérer la planification de votre évaluation.

Vous pouvez en savoir plus sur son fonctionnement en consultant la section [Analyseur des bonnes pratiques](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md) documentation.

**Création d’un rapport d’évaluation de l’état de préparation du cloud**

L&#39;étape suivante consiste à créer un rapport basé sur toutes les connaissances acquises jusqu&#39;à présent. Pour ce faire, vous pouvez générer des rapports Analyseur des bonnes pratiques à partir des instances d’évaluation et de production, [puis les charger dans Cloud Acceleration Manager](/help/journey-migration/cloud-acceleration-manager/using-cam/cam-readiness-phase.md#readiness-phase-cam) pour un rapport digestible d’éléments exploitables.

Un rapport type doit contenir ces entrées :

* Documentation détaillant l’ensemble des fonctionnalités de votre installation AEM particulière.
* Détails sur vos configurations et code personnalisés AEM
* Configurations du Dispatcher de production
* Configurations du réseau de diffusion de contenu (le cas échéant)

**Socialisation du rapport**

Une fois les rapports Analyseur des bonnes pratiques terminés, partagez-les avec les équipes appropriées afin de confirmer vos résultats et de planifier vos prochaines étapes. En fonction des préférences, vous pouvez également distribuer une version imprimée du rapport à l’aide de l’option [Aperçu de l’impression](/help/journey-migration/cloud-acceleration-manager/using-cam/cam-readiness-phase.md#print-preview-cam).

### Examen de la planification des ressources {#review-resource-planning}

Une fois que vous avez estimé le niveau d’effort requis pour passer à Cloud Service, vous devez identifier les ressources, créer une équipe et définir les rôles et les responsabilités pour le processus de transition.

### Définition des indicateurs de performance clés (IPC)  {#establish-kpis}

Si vous n’avez pas encore défini d’indicateurs de performance clés (IPC), il est recommandé d’établir des indicateurs de performance clés pour votre mise en oeuvre AEM afin d’aider votre équipe à se concentrer sur ce qui importe le plus.

Voir [Développement d’indicateurs clés de performance](https://guided.adobe.com/welcome/aem/part6.html) pour savoir comment choisir les IPC appropriés pour vos objectifs métier.

## Et après ? {#what-is-next}

Une fois que vous avez compris la portée des modifications requises pour passer à AEM as a Cloud Service, il est temps de [Préparez votre code et votre cloud de contenu](/help/journey-migration/implementation.md) avant d’effectuer la migration.

## Ressources supplémentaires {#additional-resources}

* [Prise en main de Cloud Acceleration Manager](/help/journey-migration/cloud-acceleration-manager/using-cam/getting-started-cam.md) - Un guide complet sur l’utilisation de Cloud Acceleration Manager pour accélérer votre déplacement vers le cloud
* [AEM as a Cloud Service : Introduction, architecture et pensée différente](https://experienceleague.adobe.com/?launch=ExperienceManager-D-1-2021.1.migration&amp;recommended=ExperienceManager-D-1-2021.1.migration&amp;lang=en#dashboard/learning)
* [AEM accueil d’un Cloud Service](/help/overview/home.md) - Pour une présentation de la documentation as a Cloud Service du Experience Manager, commencez ici.
* [AEM Présentation as a Cloud Service](/help/overview/home.md) - Ce guide présente Experience Manager as a Cloud Service, avec une introduction, la terminologie et l’architecture.
* [Intégration](/help/onboarding/home.md)- Ce guide résume la prise en main d’Experience Manager as a Cloud Service, y compris la manière d’y accéder et de configurer votre équipe.