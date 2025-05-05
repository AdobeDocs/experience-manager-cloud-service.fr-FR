---
title: Phase dʼimplémentation
description: Assurez-vous que votre code et contenu sont prêts pour la migration vers le cloud
exl-id: d124f9a5-a754-4ed0-a839-f2968c7c8faa
feature: Migration
role: Admin
source-git-commit: 913b1beceb974243f0aa7486ddd195998d5e9439
workflow-type: tm+mt
source-wordcount: '2288'
ht-degree: 96%

---

# Phase dʼimplémentation {#implementation-phase}

Dans la phase dʼimplémentation du parcours, vous découvrirez les outils à votre disposition pour préparer votre code et votre contenu pour la migration vers AEM as a Cloud Service.

## Un peu d’histoire… {#story-so-far}

Dans les parties précédentes du parcours, vous avez appris les [tenants et aboutissants de la migration vers AEM as a Cloud Service](/help/journey-migration/getting-started.md), ainsi quʼà déterminer si votre déploiement est prêt à être migré vers le cloud, dans la [phase de préparation](/help/journey-migration/readiness.md).

Votre parcours de migration continue dans cet article, qui propose des conseils sur la façon dʼutiliser les outils fournis par Adobe pour sʼassurer que votre code et contenu sont prêts à être migrés vers le cloud.

## Objectif {#objective}

Ce document vise à vous fournir les éléments suivants :

* Présentation de Cloud Manager, le framework dʼintégration et de livraison continues dʼAEM, utilisé pour déployer du code vers AEM as a Cloud Service.
* Familiarisation avec lʼoutil de transfert de contenu.
* Description des outils de refactorisation de code à utiliser afin de pouvoir moderniser votre code pour AEM as a Cloud Service

## Utilisation de Cloud Manager {#using-cloud-manager}

Avant de commencer, vous devez vous familiariser avec Cloud Manager, car il s’agit du seul mécanisme de déploiement du code vers AEM as a Cloud Service.

Cloud Manager permet aux entreprises de gérer elles-mêmes AEM dans le cloud. Il comprend une structure d’intégration et de diffusion continues (CI/CD) qui permet aux équipes informatiques et aux partenaires d’implémentation d’accélérer la diffusion des personnalisations ou des mises à jour sans compromettre les performances ou la sécurité.

Pour vous familiariser avec l’utilisation de Cloud Manager, consultez les ressources suivantes :

* [Parcours d’intégration](/help/journey-onboarding/overview.md) pour comprendre les ressources d’aide autonome sur l’intégration à Experience Manager as a Cloud Service.

* [Intégration de Git à Adobe Cloud Manager](/help/implementing/cloud-manager/managing-code/integrating-with-git.md) pour en savoir plus sur l’utilisation d’un référentiel Git unique pour déployer du code.

* [Configuration d’Adobe Experience as a Cloud Service](/help/security/ims-support.md#aem-configuration) pour en savoir plus sur la gestion des produits et de l’accès utilisateur dans Admin Console.

## Utilisation des outils fournis par Adobe pour préparer votre contenu et votre code pour le cloud {#use-tools-to-make-code-and-content-cloud-ready}

Les étapes exactes de votre transition vers Cloud Service dépendent des systèmes achetés et de vos pratiques de cycle de vie du développement logiciel.

La figure suivante montre les principales étapes de la phase de conversion de votre code et de votre contenu en vue de leur utilisation avec AEM as a Cloud Service :

![Étapes de conversion](/help/journey-migration/assets/exec-image1.png)

Nous commencerons par détailler les outils à utiliser afin que vous puissiez y parvenir dans les chapitres ci-dessous.

## Migration du contenu {#content-migration}

Pour migrer le contenu de votre instance AEM actuelle vers l’instance Cloud Service, vous pouvez utiliser l’outil de transfert de contenu d’Adobe.

Il permet de spécifier le sous-ensemble de contenu que vous souhaitez transférer entre votre instance AEM source et l’instance AEM Cloud Service.

Le processus de migration de contenu consiste en plusieurs étapes, qui demandent une planification, un suivi et une collaboration entre les différentes équipes.

Pour plus d’informations sur le fonctionnement de l’outil et sur la façon dont Adobe vous recommande de l’utiliser, consultez la [documentation de l’outil de transfert de contenu](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md).

## Refactorisation du code {#code-refactor}

### Configuration pour le développement {#set-up-for-development}

À présent, il est temps de commencer à refactoriser les fonctionnalités existantes pour les rendre compatibles avec Cloud Service.

Tout d’abord, consultez la documentation détaillant les outils de base et commencez à refactoriser votre code :


* Lors de la planification, il est utile de disposer dʼune liste des éléments qui doivent être refactorisés afin d’être compatibles avec AEM as a Cloud Service. Vous pouvez consulter les [Conseils de développement](/help/implementing/developing/introduction/development-guidelines.md) pour en savoir plus sur la refactorisation et l’optimisation du code pour Cloud Service.
* Découvrez comment effectuer la [Gestion des configurations](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/configurations.html?lang=fr#what-is-a-configuration) dans AEM as a Cloud Service.
* Découvrez comment configurer un environnement de développement local en téléchargeant le [SDK AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=fr).
* Pour terminer, familiarisez-vous avec lʼ[API Java AEM as a Cloud Service](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html).

Vous pouvez également :

* Regardez cette vidéo pour comprendre comment installer le SDK Dispatcher localement :

  >[!VIDEO](https://video.tv.adobe.com/v/30601)

* Regardez cette vidéo pour comprendre comment configurer le SDK Dispatcher :

  >[!VIDEO](https://video.tv.adobe.com/v/30602)

### Un changement d’état d’esprit {#a-change-in-mindset}

Développer et exécuter du code dans AEM as a Cloud Service nécessite un changement d’état d’esprit. Le code doit être résilient, d’autant plus qu’une instance peut être arrêtée à tout moment. Le code s’exécutant dans Cloud Service doit savoir qu’il s’exécute toujours dans une grappe. Cela signifie qu’il y a toujours plusieurs instances en cours d’exécution.

Certaines modifications sont nécessaires pour que les projets Maven d’AEM soient compatibles avec le cloud. AEM as a Cloud Service exige une séparation du *contenu* et du *code* dans des packages distincts pour le déploiement dans AEM :

* `/apps` et `/libs` sont considérées comme des zones immuables d’AEM, car ils ne peuvent pas être modifiés après le démarrage d’AEM (c’est-à-dire au moment de l’exécution). Cela inclut les opérations de création, de mise à jour ou de suppression. Toute tentative de modification d’une zone immuable au moment de l’exécution échouera.

* Toutes les autres zones du référentiel (par exemple, `/content` , `/conf` , `/var` , `/home` , `/etc` , `/oak:index` , `/system` , `/tmp`) sont toutes des zones modifiables, ce qui signifie qu’elles peuvent être modifiées au moment de l’exécution.

Pour en savoir plus, consultez la documentation sur la [structure de package recommandée](/help/implementing/developing/introduction/aem-project-content-package-structure.md#recommended-package-structure).


### Outils de migration vers le cloud {#cloud-migration-tools}

Adobe propose plusieurs outils pour accélérer certaines de vos tâches de refonte du code. La maîtrise de ces outils et des problèmes qu’ils résolvent, permet de réduire la complexité et la durée de la migration.

* [Migration des processus de ressources](/help/journey-migration/moving-to-aem-assets/asset-workflow-migration-tool.md), un outil qui permet de migrer automatiquement les processus de traitement des ressources
* [Convertisseur du Dispatcher](/help/journey-migration/refactoring-tools/dispatcher-transformation-utility-tools.md), un outil qui convertit vos configurations de Dispatcher existantes dans un format prêt pour AEM as a Cloud Service.
* [Référentiel Modernizer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/moving/refactoring-tools/repo-modernizer.html?lang=fr), un outil qui prend un projet AEM Multimode en entrée et le convertit en un projet AEM as a Cloud Service.
* [Convertisseur d’index](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/moving/refactoring-tools/index-converter.html?lang=fr), un outil qui convertit les index en une forme compatible avec AEM as a Cloud Service
* Les [outils de modernisation](/help/journey-migration/refactoring-tools/aem-modernization-tools.md) une suite d’utilitaires qui peuvent être utilisés pour convertir les anciennes fonctionnalités d’AEM en fonctionnalités modernes et prises en charge par AEM as a Cloud Service.

Une fois que vous avez configuré l’environnement de développement local, familiarisez-vous avec le SDK AEM as a Cloud Service en consultant la [documentation](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md).

### Planifier un gel de code {#schedule-a-code-freeze}

Pour gérer le développement continu de votre code sur votre AEM active, ainsi que les tâches de refactorisation du code dans le cadre de votre parcours de transition, Adobe vous recommande de planifier une période de gel du code jusqu’à ce que vous ayez terminé la restructuration de votre projet Maven afin qu’il soit compatible avec AEM as a Cloud Service.

Une fois la restructuration du projet terminée, vous pouvez reprendre le développement de nouveau code à l’aide de cette nouvelle structure. Les défaillances du pipeline de Cloud Manager seront ainsi réduites au cours du déploiement et du test du code.

>[!NOTE]
>Les tâches de transfert de contenu et de refonte du code n’ont pas à être effectuées séquentiellement. et peuvent être réalisées indépendamment les unes des autres. Toutefois, une structure de projet appropriée est requise pour que le contenu soit correctement rendu dans votre environnement Cloud Service.

## Bonnes pratiques de déploiement et de test du code {#best-practices}

Le pipeline Cloud Manager prend en charge l’exécution de tests par rapport à l’environnement d’évaluation.

Suivez les bonnes pratiques des documents ci-dessous concernant les tests de qualité du code :

* [Test de qualité du code](/help/implementing/cloud-manager/code-quality-testing.md), un document qui décrit le processus d’écriture de scripts de test et explique le concept de couverture recommandée d’au moins 50 %.
* [Présentation des règles de qualité de code personnalisées](/help/implementing/cloud-manager/custom-code-quality-rules.md) qui vise à décrire les règles de qualité de code personnalisées exécutées par Cloud Manager, créées en fonction des bonnes pratiques en matière d’ingénierie AEM.

## Préparation à l’activation {#preparing-for-go-live}

La préparation du système source pour la migration implique des tâches au niveau du système et de l’administrateur AEM. Vous pouvez commencer par vérifier que le référentiel de contenu est bien entretenu en contrôlant le [nettoyage des révisions](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/revision-cleanup.html?lang=fr) et l’état de la tâche de [nettoyage de la mémoire d’entrepôt de données](https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/data-store-garbage-collection.html?lang=fr). Si vous exécutez la version 6.3 d’AEM (car l’outil de transfert de contenu est compatible à partir de la version 6.3), il est recommandé d’effectuer un compactage hors ligne, suivi du nettoyage de la mémoire d’entrepôt de données.

La [vérification de la cohérence des données](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/consistency-check.html?lang=fr) est recommandée pour toutes les versions d’AEM afin de s’assurer que le référentiel de contenu est en bon état pour lancer des activités de migration.

Un accès de niveau administrateur système est requis pour installer et configurer [AZCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md).

Il est également recommandé de consulter toutes les ressources, pages, projets AEM, utilisateurs et groupes inutilisés afin de gagner du temps lors de la migration. Voir la section [Santé du référentiel de contenu](#repository-health).

### Santé du référentiel de contenu {#repository-health}

Une fois que l’accès à un [clone de production](#proof-of-migration) est établi, il faut vérifier la santé du référentiel. Comme mentionné dans la section précédente, l’objectif est de nettoyer et de compacter le référentiel sur la source avant de démarrer la migration. Cette étape peut permettre de gagner beaucoup de temps autrement consacré à la résolution des problèmes une fois la migration commencée.

| Action | Points clés |
|---------|----------|
| Utilisateurs, groupes et autorisations | Vous devez comprendre le volume d’utilisateurs, de groupes et la complexité autour des adhésions. Recherchez les occasions de nettoyer les utilisateurs et les groupes inutilisés dans la source avant la migration. |
| Traitement des ressources incomplet | Essayez de terminer le traitement des ressources dans le système source avant de démarrer la migration afin d’éviter tout problème potentiel dans AEM as a Cloud Service après la migration. |
| État du contenu | Il est recommandé de rechercher du contenu incorrect et de le purger avant de démarrer la migration. Par exemple, recherchez les ressources ou les pages qui n’ont pas de rendu original ou qui sont bloquées dans le traitement du processus. Voir aussi [État de la ressource](#asset-health). |

## Collecte de données {#gathering-data}

>[!NOTE]
> La section [Stratégie et chronologie de migration du contenu](#content-strategy-and-timeline) explique en détail comment extrapoler les données collectées et créer un plan de migration.

La collecte de données peut vous aider à planifier les activités de migration et les tâches associées. Les temps d’extraction et d’ingestion sont particulièrement utiles car les points de données peuvent être associés à une taille spécifique du jeu de migration. Par conséquent, ces points de données peuvent être extrapolés pour établir une formule :

* Durée totale de l’[extraction](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md)
* Durée totale de l’[ingestion](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md)
* Durée totale de l’[extraction](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process) du complément
* Durée totale de l’[ingestion](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process) du complément


<!-- Alexandru: hiding this for now

One more important datapoint is the amount of time it takes to complete the [user mapping](/help/journey-migration/content-transfer-tool/user-mapping-tool/overview-user-mapping-tool.md), if this is coupled with the content migration. You can take this data point into consideration for more realistic estimates, because it is added to the overall extraction timeline and it may not be required to run it during top-ups.

-->

Ces points de données peuvent également vous aider à [établir des indicateurs clés de performance](/help/journey-migration/readiness.md#establish-kpis) et autres tâches liées à la migration.

### Plan de migration {#migration-plan}

En fonction des points de données que vous avez collectés (voir ci-dessus), vous pouvez créer un plan de migration qui peut être intégré dans un plan de macro-projet. Cette étape permet à tous les principaux intervenants de visualiser et de planifier les activités de migration.

Le tableau suivant illustre un plan de migration type :

| Itération de la migration | Date de début | Date de fin estimée | Dépendances | Durée estimée (en jours) | Détails supplémentaires / Actions |
|---|---|---|---|---|---|
| PRDCLONE-AUTEUR-INITIAL-USRMAP-CSSTAGE-AUTEUR |   |   |   |   |   |
| PRDCLONE-PUBLICATION-COMPLEMENT-CSSTAGE-AUTEUR |   |   |   |   |   |

Comme vous pouvez le voir dans le tableau ci-dessus, il est utile de suivre un format de dénomination spécifique pour identifier les itérations de migration, par exemple : **PRDCLONE** pour l’environnement AEM source, **AUTEUR/PUBLICATION** pour l’environnement AEM as a Cloud Service, **CSSTAGE-AUTEUR** pour l’instance AEM as a Cloud Service, etc.

Voici quelques détails importants qui influencent votre plan de migration :

**Le nombre total d’extractions nécessaires**

* Les extractions Auteur et Publication dans des environnements spécifiques sont considérées comme deux extractions parallèles, car elles sont indépendantes l’une de l’autre.
* Le nombre d’extractions de complément basé sur la croissance du référentiel dans des périodes de temps spécifiques.

**Nombre total des ingestions requises**

* Il est important de saisir cet élément dans le plan, car un ensemble extrait peut être ingéré dans plusieurs environnements de Cloud Service.
* Nombre d’ingestions de complément.
* La migration du contenu de l’auteur source vers l’instance de l’auteur du service cloud et de la publication source vers la publication Cloud Service est la bonne pratique pour éviter d’ingérer tout le contenu de l’auteur dans la publication Cloud Service.

### Suivi de la migration {#migration-tracker}

Vous pouvez utiliser le suivi de la migration pour noter les durées de l’exécution initiale et de complément. Ces points de données vous aideront à formuler des exigences réalistes en matière de gel du contenu avant le complément final.

L’outil de suivi vous aidera également à :

* Identifier tout écart par rapport au planificateur qui nécessite des ajustements du plan ou des délais d’activation
* Fournir un statut réaliste qui peut être utilisé dans toutes les communications nécessaires
* Planifier les migrations initiales ou futures de complément

Le tableau suivant illustre un suivi de migration fonctionnel :

| Source (Environnement / Instance / URL) | Destination (Environnement / Instance / URL) | Nom du jeu de migration, type (initial ou complément) | Taille du jeu de migration (Mo) | Mappage utilisateur (Oui/Non) | Durée de l’extraction (Début, Fin, Temps pris) | Durée d’ingestion (Début, Fin, Temps pris) | Problèmes / Résolutions / Détails |
|---|---|---|---|---|---|---|---|
|   |   |   |   |   |   |   |   |

## Stratégie et calendrier de migration de contenu {#content-strategyand-timeline}

La section suivante présente les étapes importantes et les tâches associées qui peuvent être utilisées pour formuler une stratégie et un calendrier de migration de contenu.

![Étapes pour formuler une stratégie de migration](/help/journey-migration/assets/content-migration2.png)

### Adaptation {#fitment}

* Effectuez le nettoyage des révisions, la récupération de l’espace mémoire de stockage des données et des contrôles de cohérence des données. Consultez aussi la section [Préparer la mise en production](#preparing-for-go-live).
* [Collectez des statistiques](#gathering-data) à propos du référentiel source d’AEM :
   * Taille de la banque de segments
   * Taille de la banque d’index
   * Nombre de pages
   * Nombre de ressources
   * Nombre d’utilisateurs et de groupes
* Vérifiez si les fonctionnalités suivantes sont activées sur la source AEM (également requis dans AEM as a Cloud Service) :
   * Balisage intelligent
   * Recherche par analogie
   * Recherche de documents Word ou PDF contenant du texte
* Collectez le [rapport](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md) de l’analyseur de bonnes pratiques.
* Effectuez une importation dans [Cloud Acceleration Manager](/help/journey-migration/cloud-acceleration-manager/introduction/overview-cam.md).
   * Consultez la recommandation d’auto-analyse pour vous assurer qu’AEM as a Cloud Service peut gérer les besoins en matière de stockage.
* Créez un ticket de support Adobe pour toute clarification avant de poursuivre le plan de migration.

### Preuve de la migration {#proof-of-migration}

* Demandez un clone de production qui :
   * Se trouve dans la même zone réseau.
   * Fournit du contenu de production tel que des utilisateurs et des groupes.
   * Clone l’auteur et la publication : un nœud chacun dans le cas d’un cluster ou d’une batterie de publication.
* Sélectionnez un sous-ensemble du contenu qui est migré en tenant compte des éléments suivants :
   * Il s’agit d’un mélange de tous les types de contenu disponibles
   * Contient tous les utilisateurs, utilisatrices et groupes
* Inclut 25 % du contenu ou jusqu’à 1 To de contenu, selon ce qui est moins élevé.
* Exécutez au moins une opération de migration intégrale et [complémentaire](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process), depuis le clone de production vers l’environnement hors production d’AEM as a Cloud Service.
* Résolvez tous les problèmes potentiels tels que :
   * Espace disque sur la source AEM.
   * Connectivité entre la source AEM et AEM as a Cloud Service.
   * Toute [limite liée à l’ingestion](go-live.md#known-limitations).
* Enregistrez le temps pris pour l’[extraction et l’ingestion](#gathering-data) :
   * Déterminez la quantité de contenu ajoutée chaque semaine.
   * Extrapolez les temps mesurés à partir de la preuve de migration pour créer un [plan de migration](#migration-plan).

## Prochaines étapes {#what-is-next}

Une fois que vous avez entièrement compris comment évaluer si votre installation AEM est prête à être déplacée vers le cloud, alors que nous apprenons à utiliser les outils nécessaires pour la préparer, il est temps de passer à la [phase de mise en production](/help/journey-migration/go-live.md).
