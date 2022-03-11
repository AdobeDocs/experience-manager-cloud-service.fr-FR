---
title: Phase de mise en œuvre
description: Assurez-vous que votre code et votre contenu sont prêts pour la migration vers le cloud
exl-id: d124f9a5-a754-4ed0-a839-f2968c7c8faa
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '2422'
ht-degree: 10%

---

# Phase de mise en œuvre {#implementation-phase}

Au cours de la phase de mise en oeuvre du parcours, vous allez explorer les outils par lesquels vous pouvez rendre votre code et votre contenu prêts à être déplacés vers AEM as a Cloud Service.

## Un peu d’histoire...  {#story-so-far}

Dans les parties précédentes du parcours, vous avez parcouru [vous familiariser avec les modifications apportées à AEM as a Cloud Service](/help/journey-migration/getting-started.md), ainsi que de déterminer si votre déploiement est prêt à être déplacé dans le cloud avec la variable [phase de préparation](/help/journey-migration/readiness.md).

Cet article poursuit en fournissant des conseils sur l’utilisation des outils fournis par Adobe pour vous assurer que votre code et votre contenu sont prêts à être déplacés dans le cloud.

## Objectif {#objective}

Ce document vise à :

* Découvrez Cloud Manager, AEM structure d’intégration et de diffusion continues utilisée pour déployer le code vers AEM as a Cloud Service
* Mise à niveau de l’outil de transfert de contenu
* Décrivez les outils de refactorisation du code que vous devez utiliser afin de moderniser votre code pour AEM as a Cloud Service

## Utilisation de Cloud Manager {#using-cloud-manager}

Avant de commencer, vous devez vous familiariser avec Cloud Manager, car il s’agit du seul mécanisme de déploiement du code pour AEM as a Cloud Service.

Cloud Manager permet aux entreprises de gérer elles-mêmes AEM dans le cloud. Il comprend une structure d’intégration et de diffusion continues (CI/CD) qui permet aux équipes informatiques et aux partenaires d’implémentation d’accélérer la diffusion des personnalisations ou des mises à jour sans compromettre les performances ou la sécurité.

Pour vous familiariser avec l’utilisation de Cloud Manager, consultez les ressources ci-dessous :

* [Intégration à Experience Manager as a Cloud Service](/help/onboarding/home.md) pour comprendre les ressources d’aide autonome relatives à l’intégration à Experience Manager as a Cloud Service.

* [Intégration de Git à Adobe Cloud Manager](/help/implementing/cloud-manager/managing-code/integrating-with-git.md) pour en savoir plus sur l’utilisation d’un référentiel Git unique pour déployer du code.

* [Configuration d’Adobe Experience as a Cloud Service](/help/security/ims-support.md#aem-configuration) pour en savoir plus sur la gestion des produits et de l’accès utilisateur dans Admin Console.

## Utilisation des outils fournis par l’Adobe pour rendre votre contenu et votre cloud de code prêts {#use-tools-to-make-code-and-content-cloud-ready}

Les étapes exactes de votre transition vers Cloud Service dépendent des systèmes achetés et des pratiques de cycle de vie du développement logiciel que vous suivez.

La figure suivante montre les principales étapes impliquées dans la phase qui implique la conversion de votre code et de votre contenu en vue d’une utilisation avec AEM as a Cloud Service :

![image](/help/journey-migration/assets/exec-image1.png)

Nous allons commencer par détailler les outils dont vous avez besoin pour y parvenir dans les chapitres ci-dessous.

## Migration du contenu {#content-migration}

Pour migrer le contenu de votre instance d’AEM actuelle vers votre instance de Cloud Service, vous pouvez utiliser l’outil de transfert de contenu d’Adobe.

Il permet de spécifier le sous-ensemble de contenu que vous souhaitez transférer entre votre instance AEM source et l’instance AEM Cloud Service.

La migration de contenu est un processus en plusieurs étapes qui nécessite une planification, un suivi et une collaboration entre différentes équipes.

Pour plus d’informations sur le fonctionnement de l’outil et sur la manière dont nous vous recommandons de l’utiliser, voir la section [Documentation de l’outil de transfert de contenu](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md).

## Refactorisation du code {#code-refactor}

### Configuration pour le développement {#set-up-for-development}

Il est temps de commencer à refactoriser les fonctionnalités existantes pour les rendre compatibles avec les Cloud Services.

Pour ce faire, vous devez consulter la documentation détaillant les outils de base dont vous aurez besoin pour commencer à restructurer votre code :


* Lors de la planification, il est préférable d&#39;avoir une liste des zones qui doivent être restructurées afin d&#39;être compatibles avec AEM as a Cloud Service. Vous pouvez consulter [Conseils de développement](/help/implementing/developing/introduction/development-guidelines.md) pour plus d’informations sur la refactorisation et l’optimisation du code pour Cloud Service.
* Découvrez comment [Gestion des configurations](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/configurations.html?lang=en#what-is-a-configuration) dans AEM as a Cloud Service.
* Découvrez comment configurer un environnement de développement local en téléchargeant le [AEM SDK as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en)
* Enfin, familiarisez-vous avec les [AEM API Java as a Cloud Service](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html).

En outre, vous pouvez également :

* Regardez cette vidéo pour comprendre comment installer localement le SDK de Dispatcher :

   >[!VIDEO](https://video.tv.adobe.com/v/30601)

* Regardez cette vidéo pour comprendre comment configurer le SDK de Dispatcher :

   >[!VIDEO](https://video.tv.adobe.com/v/30602)

### Un changement d&#39;état d&#39;esprit {#a-change-in-mindset}

Le développement et l’exécution du code dans AEM as a Cloud Service nécessitent un changement d’état d’esprit. Le code doit être résilient, d’autant plus qu’une instance peut être arrêtée à tout moment. Le code s’exécutant dans Cloud Service doit savoir qu’il s’exécute toujours dans une grappe. Cela signifie qu’il y a toujours plusieurs instances en cours d’exécution.

Certaines modifications sont nécessaires pour que les projets Maven AEM soient compatibles avec le cloud. AEM as a Cloud Service nécessite une séparation de *content* et *code* en packages distincts pour le déploiement dans AEM :

* `/apps` et `/libs` sont considérées comme des zones immuables de l’AEM, car elles ne peuvent pas être modifiées après le démarrage d’AEM (c’est-à-dire au moment de l’exécution). Cela inclut les opérations de création, de mise à jour ou de suppression. Toute tentative de modification d’une zone de ce type au moment de l’exécution sera vouée à l’échec.

* Tous les autres éléments du référentiel (par exemple, `/content` , `/conf` , `/var` , `/home` , `/etc` , `/oak:index` , `/system` , `/tmp`) sont toutes des zones modifiables, ce qui signifie qu’elles peuvent être modifiées au moment de l’exécution.

Pour en savoir plus, consultez la section [Structure de module recommandée](/help/implementing/developing/introduction/aem-project-content-package-structure.md#recommended-package-structure) documentation.


### Outils de migration vers le cloud {#cloud-migration-tools}

Adobe fournit plusieurs outils pour accélérer certaines de vos tâches de refactorisation du code. La compréhension de ces outils et des problèmes qu’ils résolvent réduira la complexité et le temps de migration.

* [Migration des workflows de ressources](/help/journey-migration/moving-to-aem-assets/asset-workflow-migration-tool.md), outil utilisé pour migrer automatiquement les workflows de traitement des ressources
* [Convertisseur du Dispatcher](/help/journey-migration/refactoring-tools/dispatcher-transformation-utility-tools.md), un outil qui convertit vos configurations Dispatcher existantes dans un format prêt à AEM as a Cloud Service.
* [Repository Modernizer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/moving/refactoring-tools/repo-modernizer.html?lang=en), un outil qui prend un projet AEM Multimode en tant qu’entrée et le convertit en un projet AEM as a Cloud Service.
* [Convertisseur d’index](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/moving/refactoring-tools/index-converter.html?lang=en), un outil qui convertit les index en un formulaire compatible avec AEM as a Cloud Service
* [Outils de modernisation](/help/journey-migration/refactoring-tools/aem-modernization-tools.md), une suite d’utilitaires qui peut être utilisée pour convertir les fonctionnalités d’AEM héritées en fonctionnalités modernes et prises en charge par AEM as a Cloud Service.

Une fois que vous avez configuré l’environnement de développement local, familiarisez-vous avec le SDK as a Cloud Service AEM en consultant le [documentation](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md).

### Planification d’un blocage du code {#schedule-a-code-freeze}

Pour gérer le développement continu de votre code sur votre principale AEM ainsi que les tâches de refactorisation du code dans le cadre de votre parcours de transition, nous vous recommandons de planifier une période de gel du code jusqu’à ce que vous ayez terminé la restructuration de votre projet Maven afin qu’il soit compatible avec AEM as a Cloud Service.

Une fois la restructuration du projet terminée, vous pouvez reprendre le développement du code en fonction de cette nouvelle structure. Cela réduit les échecs de pipeline de Cloud Manager pendant le déploiement et le test du code.

>[!NOTE]
>Les tâches de transfert de contenu et de refactorisation du code n’ont pas à être effectuées de manière séquentielle. et peuvent être réalisées indépendamment les unes des autres. Toutefois, une structure de projet appropriée est requise pour que le contenu soit correctement rendu dans votre environnement Cloud Service.

## Bonnes pratiques de déploiement et de test du code {#best-practices}

Le pipeline Cloud Manager prend en charge l’exécution de tests par rapport à l’environnement intermédiaire.

Suivez les bonnes pratiques des documents ci-dessous concernant les tests de qualité du code :

* [Test de qualité du code](/help/implementing/cloud-manager/code-quality-testing.md), un document qui décrit le processus d’écriture de scripts de test et explique le concept de couverture recommandée d’au moins 50 %.
* [Présentation des règles de qualité du code personnalisé](/help/implementing/cloud-manager/custom-code-quality-rules.md) qui vise à décrire les règles de qualité du code personnalisé exécutées par Cloud Manager créées en fonction des bonnes pratiques en matière d’ingénierie AEM.

## Préparation à l’activation {#preparing-for-go-live}

La préparation du système source pour la migration implique des tâches de niveau système et AEM administrateur. Vous pouvez commencer en vérifiant que le référentiel de contenu est dans un état bien géré en vérifiant la variable [nettoyage des révisions](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/revision-cleanup.html?lang=fr) et le [nettoyage de la mémoire d’entrepôt de données](https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/data-store-garbage-collection.html) état de la tâche. Si vous exécutez AEM version 6.3 (car l’outil de transfert de contenu est compatible à partir de la version 6.3), il est recommandé d’effectuer un compactage hors ligne, suivi du nettoyage de la mémoire d’entrepôt de données.

[Vérification de la cohérence des données](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/consistency-check.html) est recommandé dans toutes les versions d’AEM afin de s’assurer que le référentiel de contenu est en bon état pour lancer des activités de migration.

Un accès de niveau administrateur système est requis pour l’installation et la configuration [AZCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md)

Il est également recommandé de consulter les ressources, pages, projets AEM, utilisateurs et groupes inutilisés afin de gagner du temps lors de la migration. Voir [Content Repository Health](#repository-health) .

### Content Repository Health {#repository-health}

Une fois que vous avez accès à un [clone de production](#proof-of-migration) est établi, procédez pour vérifier l’intégrité du référentiel. Comme mentionné dans la section précédente, l’objectif est de nettoyer et de compliquer le référentiel sur la source avant de démarrer la migration. Cette étape peut permettre de gagner beaucoup de temps lors de la résolution des problèmes une fois la migration commencée.

| Action | Principales mesures à prendre |
|---------|----------|
| Utilisateurs, groupes et autorisations | Vous devez comprendre le volume d’utilisateurs, de groupes et la complexité des adhésions. Recherchez des opportunités de nettoyage des utilisateurs inutilisés, des groupes dans la source avant la migration. |
| Traitement des ressources incomplètes | Essayez de terminer le traitement des ressources dans le système source avant de démarrer la migration afin d’éviter toute préoccupation potentielle lors AEM migration as a Cloud Service. |
| État du contenu | Il est recommandé de rechercher du contenu incorrect et de le purger avant de démarrer la migration. Par exemple, recherchez des ressources ou des pages qui n’ont pas de rendus originaux ou qui sont bloquées dans le traitement du workflow. Voir aussi [Asset Health](#asset-health). |

## Collecte de données {#gathering-data}

>[!NOTE]
> Le [Stratégie de migration de contenu et chronologie](#content-strategy-and-timeline) pour plus d’informations sur la manière d’extrapoler les données collectées et de créer un plan de migration.

La collecte de données peut vous aider à planifier les activités de migration et les tâches associées. Les temps d’extraction et d’ingestion sont particulièrement utiles, car les points de données peuvent être associés à une taille spécifique du jeu de migration. Par conséquent, ces données peuvent être extrapolées pour obtenir un plan :

* Durée totale de traitement [extraction](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md)
* Durée totale de traitement [ingestion](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md)
* Durée totale nécessaire au complément [extraction](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process)
* Durée totale nécessaire au complément [ingestion](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process)

Un point de données plus important est le temps nécessaire pour terminer la variable [mapping utilisateur](/help/journey-migration/content-transfer-tool/user-mapping-tool/overview-user-mapping-tool.md), si cela est couplé à la migration du contenu. Vous pouvez prendre ce point de données en considération pour des estimations plus réalistes, puisqu’il sera ajouté à la chronologie d’extraction globale et qu’il peut ne pas être nécessaire de l’exécuter lors des cumuls.

Ces points de données peuvent également vous aider à [Définition des IPC](/help/journey-migration/readiness.md#establish-kpis) et autres tâches liées à la migration.

### Plan de migration {#migration-plan}

En fonction des points de données que vous avez collectés (voir ci-dessus), vous pouvez créer un plan de migration qui peut être intégré à un plan de projet macro. Cette étape permet à tous les principaux intervenants de visualiser et de planifier les activités de migration.

Le tableau suivant illustre un plan de migration type :

| Itération de la migration | Date de début | Date de fin estimée | Dépendances | Durée estimée (en jours) | Détails supplémentaires/Éléments d’action |
|---|---|---|---|---|---|
| PRDCLONE-AUTHOR-INITIAL-USRMAP-CSSTAGE-AUTHOR |  |  |  |  |  |
| PRDCLONE-PUBLISH-TOPUP-CSSTAGE-AUTHOR |  |  |  |  |  |

Comme vous pouvez le voir dans le tableau ci-dessus, il est utile de suivre un format de nommage spécifique pour identifier les itérations de migration, par exemple : **PRDCLONE** pour l&#39;environnement de l&#39;AEM source , **AUTEUR/PUBLICATION** pour l&#39;environnement as a Cloud Service AEM, **CSSTAGE-AUTHOR** pour l’instance as a Cloud Service AEM, etc.

Voici quelques détails importants qui influencent votre plan de migration :

**Nombre total d&#39;extractions nécessaires**

* Les extractions Auteur et Publication dans des environnements spécifiques sont considérées comme deux extractions parallèles, car elles sont indépendantes les unes des autres.
* Nombre d’extractions de complément basées sur la croissance du référentiel au cours de périodes spécifiques.

**Nombre total d’assimilations requises**

* Il est important de capturer cet élément dans le plan, car un ensemble extrait peut être ingéré dans plusieurs environnements de Cloud Service.
* Nombre d’assimilations de complément.
* La migration de contenu de l’auteur source vers l’instance d’auteur du service cloud et de la publication source vers la publication Cloud Service est la bonne pratique pour éviter d’ingérer tout le contenu de l’auteur dans la publication Cloud Service.

### Suivi de migration {#migration-tracker}

Vous pouvez utiliser l’outil de suivi de migration pour noter les heures d’exécution initiale et de complément. Ces points de données vous aideront à formuler des exigences réalistes de gel du contenu avant le complément final.

L’outil de suivi vous aidera également à :

* Identifier les écarts par rapport au planificateur qui nécessitent des ajustements dans le plan ou les calendriers de mise en service.
* Fournir un statut réaliste qui peut être utilisé dans toutes les communications nécessaires
* Planification des migrations de complément initiales ou futures

Le tableau suivant illustre un dispositif de suivi de la migration fonctionnel :

| Source (Environnement/Instance/URL) | Destination (Environnement/Instance/URL) | Nom du jeu de migration, type (initial ou complément) | Taille du jeu de migration (Mo) | Mappage utilisateur (Oui/Non) | Durée de l’extraction (début, fin, temps pris) | Durée d’ingestion (début, fin, temps pris) | Problèmes / résolutions / détails |
|---|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  |  |

## Stratégie de migration de contenu et chronologie {#content-strategyand-timeline}

La section suivante présente les étapes importantes et les tâches associées qui peuvent être utilisées pour formuler une stratégie de migration de contenu et une chronologie.

![image](/help/journey-migration/assets/content-migration2.png)

### Fusion {#fitment}

* Effectuez le nettoyage des révisions, le nettoyage de la mémoire d’entrepôt de données et des contrôles de cohérence des données. Voir aussi [Préparation à l’activation](#preparing-for-go-live)
* [Collecte des statistiques](#gathering-data) à propos du référentiel source d’AEM :
   * Taille de la banque de segments
   * Taille de magasin d’index
   * Nombre de pages
   * Nombre de ressources
   * Nombre d’utilisateurs et de groupes
* Vérifiez si les fonctionnalités suivantes sont activées sur la source AEM (également requises dans AEM as a Cloud Service) :
   * Balisage intelligent
   * Recherche par analogie
   * Recherche de texte dans des mots et des documents pdf
* Collecte des analyses des bonnes pratiques [rapport](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md)
* Importez dans le [Cloud Accelerated Manager](/help/journey-migration/cloud-acceleration-manager/introduction/overview-cam.md)
   * Consultez la recommandation d’auto-analyse pour vous assurer qu’AEM as a Cloud Service peut gérer les besoins de stockage.
* Créez un ticket d’assistance Adobe pour toute clarification avant de poursuivre le plan de migration.

### Bon à tirer de la migration {#proof-of-migration}

* Demandez un clone de production qui :
   * Se trouve dans la même zone réseau
   * Fournit du contenu de production tel que des utilisateurs et des groupes
   * Cloner l’auteur et la publication : un noeud chacun dans le cas d’une grappe ou d’une ferme de publication.
* Sélectionnez un sous-ensemble du contenu qui sera migré afin que :
   * Il s’agit d’un mélange de tous les types de contenu disponibles.
   * Contient tous les utilisateurs et groupes, au cas où [mapping utilisateur](/help/journey-migration/content-transfer-tool/user-mapping-tool/overview-user-mapping-tool.md) est requis
* Inclut 25 % du contenu ou jusqu’à 1 To de contenu, selon ce qui est moins élevé.
* Exécutez au moins une opération complète et [complément](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process) migration, depuis le clone de production vers l&#39;environnement as a Cloud Service hors production AEM
* Résolvez tous les problèmes potentiels tels que :
   * Espace disque sur la source AEM
   * Connectivité entre la source AEM et AEM as a Cloud Service
   * Quelconque [limites liées à l’ingestion](go-live.md#known-limitations).
* Enregistrez le temps nécessaire pour [extraction et ingestion](#gathering-data):
   * Connaître le nombre de contenus ajoutés par semaine
   * Extrapoler les temps mesurés à partir du BAT de la migration pour créer un [plan de migration](#migration-plan).

## Et après ? {#what-is-next}

Une fois que vous avez entièrement compris comment évaluer si votre installation AEM est prête à être déplacée vers le cloud, alors que nous apprenons à utiliser les outils nécessaires pour la préparer, il est temps de passer au [phase de activation](/help/journey-migration/go-live.md).
