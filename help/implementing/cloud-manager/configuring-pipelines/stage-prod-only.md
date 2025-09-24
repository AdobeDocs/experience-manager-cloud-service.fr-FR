---
title: Partager des pipelines d’évaluation uniquement et de production uniquement
description: Découvrez comment séparer les déploiements d’évaluation et de production à l’aide de pipelines dédiés.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
badge: label="Beta" type="Positive" url="/help/implementing/cloud-manager/release-notes/current.md#staging-production-only-pipelines"
hide: true
hidefromtoc: true
index: false
exl-id: 7d76a87c-122c-4c4d-8071-957bef4c9cf1
source-git-commit: 51318172b826eb81dff86b3e8dfb6f2ded648c4c
workflow-type: tm+mt
source-wordcount: '1052'
ht-degree: 48%

---

# Fractionner les pipelines d’évaluation uniquement et de production uniquement {#stage-prod-only}

Vous pouvez diviser les déploiements d’évaluation et de production à l’aide de pipelines dédiés.

## Vue d’ensemble {#overview}

Les environnements d’évaluation et de production sont étroitement liés. Par défaut, les déploiements qui leur sont associés sont liés à un pipeline unique. Il s’agit d’un pipeline de déploiement qui effectue le déploiement pour les environnements d’évaluation et de production de ce programme. Bien que cette liaison soit habituellement adaptée, certains cas d’utilisation présentent des inconvénients :

* Si vous souhaitez effectuer un déploiement vers l’environnement d’évaluation uniquement, vous rejetez l’étape **Promouvoir en production** dans le pipeline. Cependant, l’exécution est marquée comme annulée.
* Si vous souhaitez déployer le code le plus récent d’un environnement d’évaluation vers la production, vous devez redéployer l’ensemble du pipeline, y compris le déploiement de l’évaluation, même s’il n’y a eu aucune modification du code dans ce dernier.
* Les environnements ne peuvent pas être mis à jour pendant les déploiements. Si vous souhaitez mettre en pause pour effectuer des tests sur plusieurs jours dans l’environnement d’évaluation avant de procéder à la promotion en production, l’environnement de production reste bloqué et ne peut pas être mis à jour. Ce scénario rend les tâches non dépendantes, telles que la mise à jour des [variables d’environnement](/help/implementing/cloud-manager/environment-variables.md), impossibles à effectuer.

Les pipelines dédiés à l’évaluation uniquement et à la production uniquement offrent des solutions à ces cas d’utilisation en fournissant des options de déploiement dédiées.

* Les **pipelines de déploiement en environnement d’évaluation uniquement** déploient uniquement vers un environnement d’évaluation, l’exécution se terminant une fois le déploiement et les tests terminés. Un pipeline dédié à l’évaluation uniquement se comporte de la même manière que le pipeline de pile pleine de production couplé standard, mais sans les étapes de déploiement de production (approbation, planification, déploiement).
* **Pipelines de déploiement en production uniquement :** se déploie uniquement en production en sélectionnant la dernière exécution d’étape réussie. Ils déploient ensuite ses artefacts en production. Les pipelines dédiés à la production uniquement réutilisent les artefacts de déploiement en évaluation, en contournant la phase de création.

Les pipelines dédiés uniquement à l’évaluation et à la production ne sont pas exécutés lorsqu’un pipeline de production de pile pleine est en cours, et vice versa. Si le pipeline dédié uniquement à l’évaluation et à la production de pile complète dispose du déclencheur **Lors des modifications Git** configuré et pointent vers la même branche et le même référentiel, seul le pipeline dédié uniquement à l’évaluation est lancé automatiquement. Les pipelines dédiés à la production uniquement ne démarrent pas **`On Git Changes`**, car ils ne sont pas directement liés à un référentiel.

Les pipelines dédiés à la production uniquement sont déclenchés manuellement, car ils ne sont pas directement liés à un référentiel pour **Lors des modifications Git**.

Ces pipelines dédiés offrent plus de flexibilité, mais tenez compte des informations ci-après concernant leur fonctionnement et les recommandations associées.

>[!NOTE]
>
>Les pipelines dédiés à la production uniquement utilisent toujours des artefacts du pipeline d’évaluation uniquement. Ce processus reste vrai même si le pipeline dédié à la production couplé standard a déployé quelque chose d’autre sur l’environnement d’évaluation entre-temps.
>
>* Un tel scénario peut entraîner des restaurations de code indésirables.
>* Adobe vous recommande d’arrêter d’utiliser le pipeline de production couplé standard une fois que vous commencez à utiliser les pipelines dédiés à la production uniquement et à l’évaluation uniquement.
>* Si vous décidez malgré tout d’exécuter les pipelines couplés standard et les pipelines dédiés à l’évaluation/la production uniquement, tenez compte de la réutilisation des artefacts pour éviter les restaurations de code.

## Création de pipeline {#pipeline-creation}

Les pipelines dédiés à la production uniquement et à l’évaluation uniquement sont créés de la même manière que les [pipelines de production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) et les [pipelines hors production](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) couplés standard. Consultez ces documents pour plus de détails.

1. Dans la fenêtre **Pipelines**, cliquez sur **Ajouter un pipeline**.

   * Sélectionnez **Ajouter un pipeline hors production** pour [créer un pipeline d’évaluation seule](#stage-only).
   * Sélectionnez **Ajouter un pipeline de production uniquement** pour [créer un pipeline de production uniquement](#prod-only).

![Création d’un pipeline dédié à la production/l’évaluation uniquement](/help/implementing/cloud-manager/configuring-pipelines/assets/prod-stage-pipeline.png)

>[!NOTE]
>
>Certaines options peuvent être grisées si les pipelines correspondants existent déjà.
>
>* L’option **Ajouter un pipeline de production uniquement** n’est pas disponible si le pipeline dédié uniquement à l’évaluation n’existe pas encore.
>* L’option **Ajouter un pipeline de production** n’est pas disponible s’il n’existe pas encore de pipeline couplé standard.
>* Un seul pipeline dédié uniquement à la production et un seul pipeline dédié uniquement à l’évaluation sont autorisés par programme.

### Création d’un pipeline d’étape seule {#stage-only}

1. Dans la boîte de dialogue **Ajouter un pipeline hors production**, dans l’onglet **Configuration**, sélectionnez le champ **Pipeline de déploiement** pour votre pipeline.
1. Dans le champ Nom du pipeline hors production , saisissez un nom en texte libre.
1. Sélectionnez les options de déploiement souhaitées, puis cliquez sur **Continuer**.

   ![Onglet Configuration de la boîte de dialogue Ajouter un pipeline hors production ](/help/implementing/cloud-manager/configuring-pipelines/assets/add-non-prod-pipeline-1.png)

1. Dans l’onglet **Code Source**, sélectionnez **Code de pile complète**. Cette option crée et déploie l’ensemble de l’application AEM (back-end, configuration de niveau web Dispatcher et tout module front-end du référentiel).

1. Dans la liste déroulante **Environnements de déploiement éligibles**, sélectionnez l’environnement **d’évaluation** comme environnement de déploiement pour votre pipeline. La sélection de l’étape crée un pipeline dédié à l’environnement intermédiaire (la promotion de la production se fait par le biais d’un pipeline distinct).

1. Sélectionnez vos **Référentiel** et **Branche Git** dans les listes déroulantes respectives, puis cliquez sur **Continuer**.

   ![Onglet Code Source dans la boîte de dialogue Ajouter un pipeline hors production](/help/implementing/cloud-manager/configuring-pipelines/assets/add-non-prod-pipeline-2.png)

1. Dans l’onglet **Contrôle de l’expérience**, l’URL du site spécifiée est l’URL publiée que Cloud Manager vérifie pour la qualité de la page.

1. Dans le champ **Chemin d’accès à la page**, spécifiez les pages à auditer, puis cliquez sur **![Ajouter une icône](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg) Ajouter une page**.

   Le contrôle de l’expérience analyse chaque chemin que vous ajoutez en termes de performances, d’accessibilité, d’applications web progressives, de bonnes pratiques, d’optimisation pour les moteurs de recherche et d’autres contrôles qualité. Vous pouvez ajouter plusieurs chemins d’accès et en supprimer en cliquant sur ![icône taille croisée 400](https://spectrum.adobe.com/static/icons/ui_18/CrossSize400.svg).

   ![Onglet Contrôle de l’expérience dans la boîte de dialogue Ajouter un pipeline hors production ](/help/implementing/cloud-manager/configuring-pipelines/assets/add-non-prod-pipeline-3.png)

1. Cliquez sur **Enregistrer**.


### Création d’un pipeline en production seule {#prod-only}

1. Dans la boîte de dialogue **Ajouter un pipeline de production uniquement**, dans le champ de texte **Nom du pipeline**, saisissez le nom en texte libre du pipeline.
1. Dans le champ **Nom du pipeline**, saisissez le nom de votre choix.
1. Sous **Options de déploiement en production**, sélectionnez **Mettre en pause avant le déploiement en production**.

   Cette option insère un point de contrôle d’approbation manuel juste avant l’étape de production. Le pipeline s’arrête et attend qu’un approbateur (un responsable de déploiement ou un propriétaire d’entreprise, par exemple) approuve ou annule le déploiement en production.

   Utilisez pour le contrôle des modifications ou les vérifications de dernière minute.

1. Cliquez sur **Enregistrer** pour créer le pipeline de production uniquement avec ces options.

   ![Création d’un pipeline dédié uniquement à la production](/help/implementing/cloud-manager/configuring-pipelines/assets/add-production-only-pipeline.png)

## Exécuter des pipelines d’évaluation uniquement et de production uniquement {#running}

Vous pouvez démarrer les nouveaux pipelines [comme tout autre pipeline](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#running-pipelines). Vous pouvez également déclencher un pipeline de production uniquement directement à partir des détails d’exécution d’un pipeline d’évaluation uniquement.

<!-- * Stage-only and prod-only pipelines offer a new [emergency mode](#emergency-mode) to skip testing.
Prod-only pipeline run can be triggered directly from the execution details of a [stage-only pipeline](#stage-only-run).


### Emergency Mode {#emergency-mode}

When starting production-only and staging-online pipelines, you are prompted to confirm the start and how it starts.

* **Normal Mode** is a standard run and includes stage testing steps.
* **Emergency Mode** skips stage testing steps.

![Emergency Mode](/help/assets/configure-pipelines/emergency-mode.png) -->

### Exécuter des pipelines d’évaluation uniquement {#stage-only-run}

Dans les détails d’exécution, un bouton **Promouvoir la version** s’affiche après les étapes de test. Cliquez dessus pour déclencher un pipeline de production uniquement qui déploie les artefacts d’étape de cette exécution en production. Le bouton s’affiche uniquement lors de la dernière exécution d’évaluation réussie.

![Exécution d’un pipeline dédié uniquement à l’évaluation](/help/implementing/cloud-manager/configuring-pipelines/assets/stage-only-pipelines-run.png)

Lorsque vous cliquez sur **Promouvoir la création**, une boîte de dialogue s’ouvre pour vous permettre de confirmer l’exécution du pipeline de production associé. Cliquez sur **Exécuter** pour le démarrer.

![Convertir la version - Exécuter le pipeline, boîte de dialogue](/help/implementing/cloud-manager/configuring-pipelines/assets/promote-build-run.png)

S’il n’en existe pas, une boîte de dialogue de configuration vous invite à en créer une.

![Convertir la version - Aucune boîte de dialogue de pipeline valide](/help/implementing/cloud-manager/configuring-pipelines/assets/promote-build-no-valid-pipeline.png)


### Exécuter les pipelines de production uniquement {#prod-only-run}

Pour un pipeline **de production uniquement**, Cloud Manager affiche les artefacts source déployés en production. Vérifiez l’étape **Préparation de l’artefact** pour l’exécution de la source, puis ouvrez-la pour afficher les détails et les journaux.


![Détails d’un artefact](/help/implementing/cloud-manager/configuring-pipelines/assets/prod-only-pipelines-run.png)
