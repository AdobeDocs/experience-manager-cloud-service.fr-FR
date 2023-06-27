---
title: Phase de préparation
description: Découvrez les étapes à suivre pour vous assurer que votre installation AEM est prête à être déplacée vers le cloud.
exl-id: 3bc8c037-d82a-4455-bce6-3c80c359a4ae
source-git-commit: a9aa82c8258e6a5f43680069c65518093c0baf8d
workflow-type: tm+mt
source-wordcount: '2066'
ht-degree: 56%

---

# Phase de préparation {#readiness-phase}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_planning"
>title="Planification de votre Transition"
>abstract="Avant de commencer votre parcours de transition vers le Cloud Service, familiarisez-vous avec AEM as a Cloud Service. Passez en revue les modifications notables qui y ont été apportées et les fonctionnalités qui ont été remplacées ou obsolètes."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html" text="Analyseur des bonnes pratiques"

Dans cette phase du Parcours de migration as a Cloud Service, vous vous familiarisez avec AEM as a Cloud Service. Vous pouvez passer en revue les modifications notables introduites et comprendre ce qu’il faut pour planifier une migration réussie vers le cloud.

## Un peu d’histoire… {#story-so-far}

le document précédent, [Prise en main de la transition vers AEM as a Cloud Service](/help/journey-migration/getting-started.md), présente une liste des phases que vous devez subir afin de pouvoir migrer vers AEM as a Cloud Service. Il présente également les avantages de la migration.

## Objectif {#objective}

Ce document vous aide à comprendre les facteurs à prendre en compte pour vous assurer que votre installation AEM est prête à être déplacée vers le cloud :

* En savoir plus sur les modifications notables et les fonctionnalités obsolètes.
* Comprendre comment planifier la migration vers AEM as a Cloud Service.

## Examinez les modifications notables apportées à l’architecture AEM as a Cloud Service {#notable-changes-in-aem-cloud-service-architecture}

AEM as a Cloud Service offre de nombreuses nouvelles fonctionnalités et possibilités de gestion de vos projets AEM.

Outre ces améliorations, plusieurs différences ont été introduites entre les installations on-premise d’AEM et d’Adobe Managed Services, par rapport à AEM as a Cloud Service.

La liste des éléments du tableau ci-dessous est le sous-ensemble des modifications les plus pertinentes pour une migration vers AEM as a Cloud Service. Vous pouvez consulter la liste complète des modifications notables [ici](/help/release-notes/aem-cloud-changes.md).

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
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/aem-cloud-changes.html?lang=fr">Modifications notables d’AEM as a Cloud Service</a><br><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html#mutable-vs-immutable">Structure de projet AEM pour AEM as a Cloud Service</a></td>
    <td>Un package unique pouvant être déployé dans AEM as a Cloud Service peut comporter des sous-packages, principalement pour contenir du contenu modifiable et non modifiable séparé dans leurs propres packages.</td>
  </tr>
  <tr>
    <td>Repo Init</td>
    <td><a href="https://sling.apache.org/documentation/bundles/repository-initialization.html#the-repoinit-repository-initialization-language">Documentation d’Apache Sling RepoInit</a></td>
    <td>Les scripts repoinit sont la bonne pratique pour créer des structures de noeud, des utilisateurs, des groupes ou des utilisateurs de service initiaux. Comme ces scripts peuvent être ciblés par le mode d’exécution et gérables via le déploiement du package de code, ils offrent une grande flexibilité pour réaliser les tâches d’initialisation du référentiel.</td>
  </tr>
  <tr>
    <td>Les modes d’exécution personnalisés ne sont pas autorisés.</td>
    <td></td>
    <td>Seuls les modes d’exécution prêts à l’emploi avec AEM as a Cloud Service sont pris en charge.<br>Lorsque d’autres environnements de développement sont ajoutés, ils sont tous liés au mode d’exécution "dev".</td>
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
    <td>AEM as a Cloud Service inclut le réseau de diffusion de contenu pour tous les environnements, optimisé pour la plupart des cas d’utilisation.<br>Si vous souhaitez configurer votre propre réseau CDN, vous devez soumettre une demande à l’assistance Adobe pour qu’il soit approuvé.<br>S’il est approuvé, le réseau de diffusion de contenu pointe vers Fastly et non vers AEM des instances dans aucun environnement.</td>
  </tr>
  <tr>
    <td>Tâches de longue durée</td>
    <td></td>
    <td>Évitez les tâches longues telles que les planificateurs Sling ou les tâches Cron, car les instances AEM s’exécutant dans les conteneurs peuvent aller et venir à tout moment.<br>Repensez ces fonctionnalités afin de pouvoir les décharger vers Adobe Developer.</td>
  </tr>
  <tr>
    <td>Passage aux opérations asynchrones</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/asynchronous-jobs.html?lang=en#configuring-asynchronous-msm-operations">Configuration des opérations asynchrones</a></td>
    <td>Pour améliorer les performances globales de vos environnements, certaines opérations sont exécutées en mode asynchrone. Les tâches asynchrones sont mises en file d’attente et exécutées lorsque des ressources système sont disponibles.</td>
  </tr>
  <tr>
    <td>Stratégies d’authentification et d’intégration basées sur des jetons</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#the-server-to-server-flow">Génération de jetons d’accès pour les API côté serveur</a><br><a href="https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=fr#authentication">Tutoriel sur l’authentification par jeton</a></td>
    <td>Il est fréquent que des systèmes externes à AEM tentent d’effectuer des opérations HTTP dans AEM.<br>L’approche recommandée consiste à implémenter les stratégies décrites ici, plutôt que de sʼappuyer sur la création de noms dʼutilisateurs locaux avec des mots de passe dans AEM.</td>
  </tr>
  <tr>
    <td>Fichier E/S / Espace disque</td>
    <td></td>
    <td>Il n’y a aucune garantie quant à la quantité d’espace disque allouée et les instances dans les conteneurs vont et viennent. Par conséquent, il n’est pas recommandé d’utiliser les opérations d’E/S de fichier pour écrire ou lire à partir du disque joint à l’instance AEM.</td>
  </tr>
  <tr>
    <td>Workflow Ressource de mise à jour de la gestion des ressources numériques (DAM)</td>
    <td><a href="https://experienceleague.adobe.com/docs/asset-compute/using/introduction.html?lang=fr">Asset Compute Service</a></td>
    <td>Les étapes de traitement des médias qui font partie du workflow Ressource de mise à jour de la gestion des ressources numériques (DAM) sont désormais remplacées par Asset Compute Service.</td>
  </tr>
  <tr>
    <td>Méthodes de téléchargement des ressources et étapes du processus de workflow prises en charge dans AEM as a Cloud Service</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/developer-reference-material-apis.html?lang=en#post-processing-workflows-steps">Comparaisons des API de téléchargement et étapes du processus de workflow prises en charge</a></td>
    <td>Dans AEM as a Cloud Service, lors du chargement ou téléchargement d’une ressource, celle-ci entre ou sort directement du stockage binaire. <br>Toutes les étapes de processus de workflow ne sont pas prises en charge dans AEMaaCS.</td>
  </tr>
  <tr>
    <td>Lanceurs de workflow</td>
    <td></td>
    <td>Supprimez de votre code tous les lanceurs de workflow qui déclenchent un workflow de ressource de mise à jour de gestion des actifs numériques personnalisé ou prêt à l’emploi. <br>Toutes les ressources téléchargées vers AEM as a Cloud Service seront traitées par le service de traitement des ressources. Pour les étapes personnalisées, voir <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/asset-microservices-configure-and-use.html?lang=fr#post-processing-workflows"> Processus de post-traitement</a> sur la configuration et la configuration des workflows de post-traitement.</td>
  </tr>
  <tr>
    <td>Étapes de rendu personnalisé</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/asset-microservices-configure-and-use.html?lang=fr">Profils de traitement</a></td>
    <td>Toute génération de rendu personnalisé, conversion d’image ou codage vidéo doit être déchargée vers le service de traitement des ressources en créant les profils de traitement correspondants.</td>
  </tr>
  <tr>
    <td>Recherche et indexation de contenu</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html?lang=fr">Modifications apportées à la recherche et lʼindexation de contenu</a></td>
    <td>Le traitement sous-jacent des index et le moment dʼentrée en action ont subi des modifications importantes.<br>Comprendre et refactoriser complètement les index Oak avant de les gérer dans le code que vous déployez.</td>
  </tr>
  <tr>
    <td>Certaines tâches de maintenance ne sont pas configurables</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/maintenance.html?lang=en">Tâches de maintenance AEM as a Cloud Service</a></td>
    <td>Vous ne pouvez configurer que certaines tâches de maintenance avec AEM as a Cloud Service.</td>
  </tr>
  <tr>
    <td>Modifications apportées au référentiel de publication</td>
    <td></td>
    <td>Les modifications directes apportées au référentiel de publication ne sont pas autorisées, à l’exception de celles apportées sous /home. Il est toujours recommandé que toutes les modifications apportées à l’auteur soient distribuées. Toutes les modifications de code et de configuration doivent être déployées via le pipeline correspondant de Cloud Manager.</td>
  </tr>
  <tr>
    <td>Configurations et mise en cache du Dispatcher</td>
    <td>Gestion du cache du <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/disp-overview.html?lang=fr">Dispatcher en mode cloud</a><br><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/caching.html?lang=en#other-content"><br></td>
    <td>Les configurations du Dispatcher doivent suivre une structure spécifique.<br>Les configurations doivent être gérées dans le cadre du code et déployées via le pipeline Cloud Manager.</td>
  </tr>
  <tr>
    <td>Sauvegarde et restauration</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/backup.html?lang=fr">Sauvegarde et restauration d’AEM as a Cloud Service</a></td>
    <td></td>
  </tr>
  <tr>
    <td>Modifications de l’authentification</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/ims-support.html?lang=fr">Prise en charge IMS d’AEM as a Cloud Service</td>
    <td>Si vous utilisiez auparavant l’intégration SAML 2.0 sur les instances de création et de publication avant de passer à Cloud Service, le principal changement est que AEM’auteur as a Cloud Service s’intègre uniquement à Adobe IMS. Toutefois, AEM niveau Publication as a Cloud Service peut toujours utiliser SAML ou d’autres intégrations d’authentification. AEM as a Cloud Service offre une prise en charge de l’authentification IMS uniquement pour les utilisateurs Auteur, Admin et Dev. L’authentification IMS n’offre pas de prise en charge pour les utilisateurs finaux externes de sites clients tels que les visiteurs de site.</td>
  </tr>
</tbody>
</table>

## Fonctionnalités obsolètes {#deprecated-features}

Adobe étudie constamment les fonctionnalités du produit de façon à les réinventer au fil du temps ou à remplacer les fonctions plus anciennes par des variantes plus modernes, pour améliorer la valeur client globale, le tout en faisant toujours attention à la compatibilité ascendante.

Adobe recommande de consulter [Fonctionnalités obsolètes](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/deprecated-removed-features.html#deprecated-features) pour vous familiariser avec les fonctionnalités signalées comme étant obsolètes dans Experience Manager as a Cloud Service. Découvrez l’impact sur votre déploiement AEM.

## Planification de la révision de votre installation AEM {#review-planning}

Après vous être familiarisé avec les modifications apportées à AEM as a Cloud Service, il est temps de commencer à planifier une révision de votre installation existante. Cela vous permet d’évaluer le niveau de modifications requis pour le déplacer vers le cloud.

La figure suivante présente les principales étapes impliquées lors de la phase de révision :

![image](/help/journey-migration/assets/planning-phaseimg1.png)

Ensuite, vous explorez en détail ce que chacune de ces étapes signifie.

### Évaluation du niveau de préparation pour la transition vers Cloud Service {#assess-cloud-readiness}

La première étape consiste à évaluer votre volonté de passer de votre version d’AEM existante à Cloud Service et à déterminer les domaines qui nécessitent une refactorisation pour être compatibles avec AEM as a Cloud Service.

Effectuez une évaluation complète de votre code source AEM actuel par rapport aux modifications notables et aux fonctionnalités obsolètes afin de déterminer le niveau d’effort attendu dans le parcours de transition.

Le nombre de résultats peut influencer directement les calendriers et la réussite globale du projet. Par conséquent, Adobe vous recommande de découvrir autant que possible afin de pouvoir planifier la diffusion. Vous pouvez également lancer les conversations afin de reconcevoir les personnalisations qui doivent être conformes aux AEM bonnes pratiques as a Cloud Service.

**Analyseur des bonnes pratiques**

Vous pouvez accélérer l’évaluation en exécutant l’analyseur des bonnes pratiques par rapport à votre version d’AEM actuelle. Une bonne compréhension de son fonctionnement est essentielle pour accélérer la planification de votre évaluation.

Vous pouvez en savoir plus sur son fonctionnement en consultant la documentation [Analyseur des bonnes pratiques](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md).

**Création d’un rapport d’évaluation du niveau de préparation pour la transition vers Cloud**

L&#39;étape suivante consiste à créer un rapport basé sur toutes les connaissances acquises jusqu&#39;à présent. Vous créez le rapport en générant des rapports Analyseur des bonnes pratiques à partir des instances d’évaluation et de production, [puis chargez-les dans Cloud Acceleration Manager](/help/journey-migration/cloud-acceleration-manager/using-cam/cam-readiness-phase.md#readiness-phase-cam) pour un rapport digestible d’éléments exploitables.

Un rapport type doit contenir les entrées suivantes :

* Documentation détaillant l’ensemble des fonctionnalités de votre installation AEM particulière.
* Détails sur vos configurations et code personnalisés AEM.
* Configurations du Dispatcher de production.
* Configurations du réseau de diffusion de contenu (le cas échéant).

**Socialisation du rapport**

Une fois les rapports Analyseur des bonnes pratiques terminés, partagez-les avec les équipes appropriées afin que vous puissiez confirmer vos résultats et planifier vos prochaines étapes. En fonction des préférences, vous pouvez également distribuer une version imprimée du rapport à l’aide de l’option [Aperçu avant impression](/help/journey-migration/cloud-acceleration-manager/using-cam/cam-readiness-phase.md#print-preview-cam).

### Examen de la planification des ressources {#review-resource-planning}

Une fois que vous avez estimé le niveau d’effort requis pour passer à Cloud Service, vous devez identifier les ressources, créer une équipe et définir les rôles et les responsabilités pour le processus de transition.

### Définition des indicateurs de performance clés (IPC) {#establish-kpis}

Si vous n’avez pas encore défini d’indicateurs de performance clés (IPC), il est recommandé d’établir des indicateurs de performance clés pour votre implémentation AEM afin d’aider votre équipe à se concentrer sur ce qui importe le plus.

Voir [Développement d’indicateurs clés de performance](https://experienceleague.adobe.com/welcome/aem/part6.html?lang=fr) vous pouvez ainsi apprendre à choisir les IPC appropriés pour vos objectifs métier.

## Prochaines étapes {#what-is-next}

Une fois que vous avez compris la portée des modifications requises pour passer à AEM as a Cloud Service, il est temps de [Rendre votre code et votre contenu prêts pour le cloud](/help/journey-migration/implementation.md) avant d’effectuer la migration.

## Ressources supplémentaires {#additional-resources}

* [Prise en main de Cloud Acceleration Manager](/help/journey-migration/cloud-acceleration-manager/using-cam/getting-started-cam.md) - Un guide complet sur l’utilisation de Cloud Acceleration Manager pour accélérer votre déplacement vers le cloud..
* [AEM as a Cloud Service : Introduction, architecture et pensée différente](https://experienceleague.adobe.com/?launch=ExperienceManager-D-1-2021.1.migration&amp;recommended=ExperienceManager-D-1-2021.1.migration&amp;lang=fr#dashboard/learning)
* [Accueil d’AEM a Cloud Service](/help/overview/home.md) - Pour une présentation de la documentation d’Experience Manager as a Cloud Service, commencez ici.
* [Présentation d’AEM as a Cloud Service](/help/overview/home.md) - Ce guide présente Experience Manager as a Cloud Service, y compris une introduction, la terminologie et l’architecture.
* [Parcours d’intégration](/help/journey-onboarding/overview.md) : ce guide présente les différentes étapes de la prise en main d’Experience Manager as a Cloud Service, y compris la manière d’y accéder et de configurer votre équipe..
