---
title: Phase de préparation
description: Découvrez les étapes à suivre pour vous assurer que votre installation AEM est prête à être déplacée vers le cloud.
exl-id: 3bc8c037-d82a-4455-bce6-3c80c359a4ae
feature: Migration
role: Admin
source-git-commit: 1683d53491e06ebe2dfcc96184ce251539ecf732
workflow-type: tm+mt
source-wordcount: '1915'
ht-degree: 93%

---

# Phase de préparation {#readiness-phase}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_planning"
>title="Planifier votre transition"
>abstract="Avant de commencer votre parcours de transition vers Cloud Service, familiarisez-vous avec AEM as a Cloud Service. Passez en revue les modifications notables qui y ont été apportées et les fonctionnalités qui ont été remplacées ou rendues obsolètes."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=fr" text="Analyseur des bonnes pratiques"

Dans cette phase du parcours de migration AEM as a Cloud Service, vous vous familiarisez avec AEM as a Cloud Service. Vous pouvez passer en revue les modifications notables introduites et découvrir les actions à entreprendre pour planifier une migration réussie vers le cloud.

## Un peu d’histoire… {#story-so-far}

Le document précédent, [Prise en main de la transition vers AEM as a Cloud Service](/help/journey-migration/getting-started.md), présente une liste des étapes à suivre pour pouvoir migrer vers AEM as a Cloud Service. Il présente également les avantages de la migration.

## Objectif {#objective}

Ce document vous aide à comprendre les facteurs à prendre en compte pour vous assurer que votre installation AEM est prête à être déplacée vers le cloud :

* En savoir plus sur les modifications notables et les fonctionnalités obsolètes.
* Comprendre comment planifier la migration vers AEM as a Cloud Service.

## Examinez les modifications notables apportées à l’architecture AEM as a Cloud Service {#notable-changes-in-aem-cloud-service-architecture}

AEM as a Cloud Service offre de très nombreuses fonctionnalités et possibilités nouvelles pour gérer vos projets AEM.

Outre ces améliorations, plusieurs différences ont été introduites entre les installations on-premise d’AEM et d’Adobe Managed Services, par rapport à AEM as a Cloud Service.

La liste des éléments du tableau ci-dessous est le sous-ensemble des modifications les plus pertinentes pour une migration vers AEM as a Cloud Service. Vous pouvez consulter la liste complète des [modifications notables apportées à Adobe Experience Manager as a Cloud Service](/help/release-notes/aem-cloud-changes.md).

<table>
<thead>
  <tr>
    <th>Qu’est-ce qui a changé ?</th>
    <th>Référence</th>
    <th>Points clés</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Séparation des filtres modifiables et non modifiables en packages correspondants</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/aem-cloud-changes.html?lang=fr">Modifications notables d’AEM as a Cloud Service</a><br><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html?lang=fr#mutable-vs-immutable">Structure de projet AEM pour AEM as a Cloud Service</a></td>
    <td>Un package unique pouvant être déployé dans AEM as a Cloud Service peut comporter des sous-packages, principalement pour contenir du contenu modifiable et non modifiable séparé dans leurs propres packages.</td>
  </tr>
  <tr>
    <td>Repo Init</td>
    <td><a href="https://sling.apache.org/documentation/bundles/repository-initialization.html#the-repoinit-repository-initialization-language">Documentation d’Apache Sling RepoInit</a></td>
    <td>Les scripts Repoinit sont recommandés pour créer les structures de nœud, les personnes utilisatrices, les groupes ou les personnes utilisatrices de service initiaux. Comme ces scripts peuvent être ciblés par le mode d’exécution et gérables via le déploiement du package de code, ils offrent une grande flexibilité pour réaliser les tâches d’initialisation du référentiel.</td>
  </tr>
  <tr>
    <td>Les modes d’exécution personnalisés ne sont pas autorisés.</td>
    <td></td>
    <td>Seuls les modes d’exécution prêts à l’emploi avec AEM as a Cloud Service sont pris en charge.<br>Lorsque d’autres environnements de développement sont ajoutés, ils sont tous liés au mode d’exécution « dev ».</td>
  </tr>
  <tr>
    <td>L’exécution du pipeline de Cloud Manager est la seule méthode de déploiement.</td>
    <td></td>
    <td>Dans AEM as a Cloud Service, l’accès à /system/console n’est pas autorisé. Par conséquent, toutes les configurations OSGi doivent faire partie du code et doivent être déployées en tant que code.<br>Les configurations OSGi sont disponibles en mode lecture seule pour un affichage via Developer Console via Cloud Manager.</td>
  </tr>
  <tr>
    <td>Les agents de réplication sont remplacés par la distribution de contenu Sling.</td>
    <td></td>
    <td>Le concept de l’agent de réplication est remplacé par la distribution de contenu Sling. Si des personnalisations utilisent des agents de réplication, elles doivent être repensées.<br>La réplication inverse n’est pas prise en charge.</td>
  </tr>
  <tr>
    <td>CRX/DE et le Gestionnaire de package</td>
    <td></td>
    <td>CRX/DE n’est autorisé que dans l’environnement de développement.<br>Le Gestionnaire de package est accessible sur toutes les instances de création, mais les packages qui vont être déployés ne doivent contenir que du contenu modifiable (par exemple : /content ou /conf).</td>
  </tr>
  <tr>
    <td>Réseau de diffusion de contenu intégré et Obtention de votre propre réseau de diffusion de contenu</td>
    <td></td>
    <td>AEM as a Cloud Service inclut le réseau de diffusion de contenu pour tous les environnements, optimisé pour la plupart des cas d’utilisation.<br>Si vous souhaitez configurer votre propre réseau CDN, vous devez soumettre une demande au support technique d’Adobe pour qu’il soit approuvé.<br>Si votre demande est approuvée, le réseau CDN pointe vers Fastly et non vers les instances AEM, quel que soit lʼenvironnement.</td>
  </tr>
  <tr>
    <td>Tâches de longue durée</td>
    <td></td>
    <td>Évitez les tâches de longue durée telles que des planifications Sling ou des tâches Cron, car les instances AEM exécutées dans les conteneurs peuvent apparaître et disparaître à tout moment.<br>Repensez ces fonctionnalités afin de pouvoir les décharger vers Adobe Developer.</td>
  </tr>
  <tr>
    <td>Passer aux opérations asynchrones</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/asynchronous-jobs.html?lang=fr#configuring-asynchronous-msm-operations">Configurer des opérations asynchrones</a></td>
    <td>Dans le but dʼaméliorer les performances globales de vos environnements, certaines opérations sont exécutées en mode asynchrone. Les tâches asynchrones seront mises en file d’attente et exécutées lorsque les ressources système seront disponibles.</td>
  </tr>
  <tr>
    <td>Stratégies d’authentification et d’intégration basées sur des jetons</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=fr#the-server-to-server-flow">Génération de jetons d’accès pour les API côté serveur</a><br><a href="https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=fr#authentication">Tutoriel sur l’authentification par jeton</a></td>
    <td>Il est fréquent que des systèmes externes à AEM tentent d’effectuer des opérations HTTP dans AEM.<br>L’approche recommandée consiste à implémenter les stratégies décrites ici, plutôt que de sʼappuyer sur la création de noms dʼutilisateurs locaux avec des mots de passe dans AEM.</td>
  </tr>
  <tr>
    <td>Fichier E/S / Espace disque</td>
    <td></td>
    <td>Il n’y a aucune garantie quant à la quantité d’espace disque allouée. Les instances dans les conteneurs apparaissent et disparaissent. Par conséquent, il n’est pas recommandé d’utiliser les opérations d’E/S de fichier pour écrire ou lire à partir du disque attaché à l’instance AEM.</td>
  </tr>
  <tr>
    <td>Workflow Ressource de mise à jour de la gestion des ressources numériques (DAM)</td>
    <td><a href="https://experienceleague.adobe.com/docs/asset-compute/using/introduction.html?lang=fr">Asset Compute Service</a></td>
    <td>Les étapes de traitement des médias qui font partie du workflow Ressource de mise à jour de la gestion des ressources numériques (DAM) sont désormais remplacées par Asset Compute Service.</td>
  </tr>
  <tr>
    <td>Méthodes de téléchargement des ressources et étapes du processus de workflow prises en charge dans AEM as a Cloud Service</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/developer-reference-material-apis.html?lang=fr#post-processing-workflows-steps">Comparaisons des API de téléchargement et étapes du processus de workflow prises en charge</a></td>
    <td>Dans AEM as a Cloud Service, lors du chargement ou téléchargement d’une ressource, celle-ci entre ou sort directement du stockage binaire. <br>Toutes les étapes de processus de workflow ne sont pas prises en charge dans AEMaaCS.</td>
  </tr>
  <tr>
    <td>Lanceurs de workflow</td>
    <td></td>
    <td>Supprimez de votre code tous les lanceurs de workflow qui déclenchent un workflow Ressource de mise à jour de la gestion des ressources numériques prêt à lʼemploi ou personnalisé. <br>Toutes les ressources téléchargées vers AEM as a Cloud Service seront traitées par le service de traitement des ressources. Pour les étapes personnalisées, reportez-vous à la section <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/asset-microservices-configure-and-use.html?lang=fr#post-processing-workflows">Workflows de post-traitement</a> sur la configuration des workflows de post-traitement.</td>
  </tr>
  <tr>
    <td>Étapes de rendu personnalisé</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/asset-microservices-configure-and-use.html?lang=fr">Profils de traitement</a></td>
    <td>Toute opération de génération de rendus personnalisés, de conversion dʼimages ou dʼencodage vidéo doit être confiée au service de traitement des ressources en créant les profils de traitement correspondants.</td>
  </tr>
  <tr>
    <td>Recherche et indexation de contenu</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html?lang=fr">Modifications apportées à la recherche et lʼindexation de contenu</a></td>
    <td>Le traitement sous-jacent des index et le moment dʼentrée en action ont subi des modifications importantes.<br>Assurez-vous de comprendre pleinement et de refactoriser les index Oak avant de les gérer dans le code que vous déployez.</td>
  </tr>
  <tr>
    <td>Certaines tâches de maintenance ne sont pas configurables</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/maintenance.html?lang=fr">Tâches de maintenance AEM as a Cloud Service</a></td>
    <td>Vous ne pouvez configurer que certaines tâches de maintenance avec AEM as a Cloud Service.</td>
  </tr>
  <tr>
    <td>Modifications apportées au référentiel de publication</td>
    <td></td>
    <td>Les modifications directes du référentiel de publication ne sont pas autorisées, sauf celles effectuées sous /home. Il est toujours recommandé de distribuer les modifications apportées à l’instance de création. Toutes les modifications de code et de configuration doivent être déployées via le pipeline correspondant de Cloud Manager.</td>
  </tr>
  <tr>
    <td>Configurations et mise en cache du Dispatcher</td>
    <td>Gestion du cache du <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/disp-overview.html?lang=fr">Dispatcher en mode cloud</a><br><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/caching.html?lang=fr#other-content"><br></td>
    <td>Les configurations du Dispatcher doivent suivre une structure spécifique.<br>Les configurations doivent être gérées dans le cadre du code et déployées via le pipeline Cloud Manager.</td>
  </tr>
  <tr>
    <td>Sauvegarder et restaurer</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/backup.html?lang=fr">Sauvegarde et restauration d’AEM as a Cloud Service</a></td>
    <td></td>
  </tr>
  <tr>
    <td>Modifications de l’authentification</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/ims-support.html?lang=fr">Prise en charge IMS d’AEM as a Cloud Service</td>
    <td>Si vous utilisiez précédemment l’intégration SAML 2.0 sur les instances de création et de publication avant de passer à Cloud Service, notez que le principal changement est que l’instance de création d’AEM as a Cloud Service s’intègre uniquement à Adobe IMS. Cependant, l’instance de publication d’AEM as a Cloud Service peut toujours utiliser SAML ou d’autres intégrations d’authentification. AEM as a Cloud Service ne prend en charge l’authentification IMS que pour les utilisateurs et utilisatrices ayant les droits de création, d’administration et de développement. L’authentification IMS n’offre pas de prise en charge pour les utilisateurs finaux externes de sites clients tels que les visiteurs de site.</td>
  </tr>
</tbody>
</table>

## Fonctionnalités obsolètes {#deprecated-features}

Adobe étudie constamment les fonctionnalités du produit de façon à les réinventer au fil du temps ou à remplacer les fonctions plus anciennes par des variantes plus modernes, pour améliorer la valeur client globale, le tout en faisant toujours attention à la compatibilité ascendante.

Adobe vous recommande de consulter les [Fonctionnalités obsolètes](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/deprecated-removed-features.html?lang=fr#deprecated-features) pour vous familiariser avec les fonctionnalités signalées comme étant obsolètes dans Experience Manager as a Cloud Service. Découvrez l’impact sur votre déploiement AEM.

## Planifier la révision de votre installation AEM {#review-planning}

Après avoir pris connaissance des modifications apportées à AEM as a Cloud Service, il est temps de commencer à planifier un examen de votre installation existante. Vous pourrez ainsi évaluer le niveau de modifications requis pour le déplacement vers le cloud.

La figure suivante présente les principales étapes impliquées lors de la phase de révision :

![Étapes clés de la phase de révision](/help/journey-migration/assets/planning-phaseimg1.png)

Ensuite, vous allez explorer en détail la signification de chacune de ces étapes.

### Évaluer le niveau de préparation pour la transition vers Cloud Service {#assess-cloud-readiness}

La première étape consiste à évaluer votre préparation pour passer de votre version d’AEM existante à Cloud Service et à déterminer les domaines qui nécessitent une refactorisation afin d’être compatibles avec AEM as a Cloud Service.

Effectuez une évaluation complète de votre code source AEM actuel par rapport aux modifications notables et aux fonctionnalités obsolètes afin de déterminer le niveau d’effort attendu dans le parcours de transition.

La quantité de connaissances influence directement les chronologies et la réussite globale du projet. Par conséquent, Adobe vous recommande d’en obtenir le plus possible afin de pouvoir planifier la diffusion. Vous pouvez également lancer des discussions afin de reconcevoir les personnalisations qui doivent être conformes aux bonnes pratiques d’AEM as a Cloud Service.

**Analyseur des bonnes pratiques**

Vous pouvez accélérer l’évaluation en exécutant l’analyseur des bonnes pratiques par rapport à votre version d’AEM actuelle. Une bonne compréhension de son fonctionnement est essentielle pour accélérer la planification de votre évaluation.

Vous pouvez en savoir plus sur son fonctionnement en consultant la documentation [Analyseur des bonnes pratiques](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md).

**Création d’un rapport d’évaluation du niveau de préparation pour la transition vers Cloud**

L’étape suivante consiste à créer un rapport basé sur toutes les connaissances acquises jusqu’à présent. Vous créez des rapports Best Practices Analyzer à partir des instances d’évaluation et de production, [puis les chargez dans Cloud Acceleration Manager](/help/journey-migration/cloud-acceleration-manager/using-cam/cam-readiness-phase.md#readiness-phase-cam) pour obtenir un rapport digestible d’éléments exploitables.

Un rapport type doit contenir les entrées suivantes :

* Documentation détaillant l’ensemble des fonctionnalités de votre installation AEM particulière.
* Détails sur vos configurations et code personnalisés AEM.
* Configurations du Dispatcher de production.
* Mappages de domaines (configurations de réseau CDN) (le cas échéant)

**Socialisation du rapport**

Une fois les rapports Best Practices Analyzer terminés, partagez-les avec les équipes appropriées afin de confirmer vos résultats et de planifier vos prochaines étapes. En fonction des préférences, vous pouvez également distribuer une version imprimée du rapport à l’aide de l’option [Aperçu avant impression](/help/journey-migration/cloud-acceleration-manager/using-cam/cam-readiness-phase.md#print-preview-cam).

### Examen de la planification des ressources {#review-resource-planning}

Une fois que vous avez estimé le niveau d’effort requis pour passer à Cloud Service, vous devez identifier les ressources, créer une équipe et définir les rôles et les responsabilités pour le processus de transition.

### Définition des indicateurs de performance clés (IPC) {#establish-kpis}

Si vous n’avez pas encore défini d’indicateurs de performance clés (IPC), il est recommandé d’établir des indicateurs de performance clés pour votre implémentation AEM afin d’aider votre équipe à se concentrer sur ce qui importe le plus.

Voir [Développement des KPI](https://experienceleague.adobe.com/welcome/aem/part6.html?lang=fr) pour savoir comment choisir les KPI appropriés à vos objectifs métier.

## Prochaines étapes {#what-is-next}

Une fois que vous avez compris la portée des modifications requises pour passer à AEM as a Cloud Service, il est temps de [Rendre votre code et votre contenu prêts pour le cloud](/help/journey-migration/implementation.md) avant d’effectuer la migration.

## Ressources supplémentaires {#additional-resources}

* [Prise en main de Cloud Acceleration Manager](/help/journey-migration/cloud-acceleration-manager/using-cam/getting-started-cam.md) - Un guide complet sur l’utilisation de Cloud Acceleration Manager pour accélérer votre déplacement vers le cloud.
* [AEM as a Cloud Service : introduction, architecture et pensée différente](https://experienceleague.adobe.com/fr?launch=ExperienceManager-D-1-2021.1.migration&recommended=ExperienceManager-D-1-2021.1.migration&lang=fr#dashboard/learning)
* [Accueil d’AEM a Cloud Service](/help/overview/introduction.md) - Pour une présentation de la documentation d’Experience Manager as a Cloud Service, commencez ici.
* [Présentation d’AEM as a Cloud Service](/help/overview/introduction.md) - Ce guide présente Experience Manager as a Cloud Service, y compris une introduction, la terminologie et l’architecture.
* [Parcours d’intégration](/help/journey-onboarding/overview.md)- Ce guide résume la prise en main d’Experience Manager as a Cloud Service, y compris la manière d’y accéder et de configurer votre équipe.
