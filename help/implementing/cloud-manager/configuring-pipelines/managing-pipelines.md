---
title: Gérer les pipelines
description: Découvrez comment gérer vos pipelines existants, notamment en les modifiant, en les exécutant et en les supprimant.
index: true
exl-id: 4aff5a84-134a-43fa-8de8-8d564f4edd16
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1493'
ht-degree: 28%

---


# Gérer les pipelines {#managing-pipelines}

Découvrez comment gérer vos pipelines existants, notamment en les modifiant, en les exécutant et en les supprimant.

## Carte de pipeline {#pipeline-card}

La vignette **Pipelines** de la page **Aperçu du programme** dans Cloud Manager vous donne un aperçu de tous vos pipelines et de leur statut actuel.

![Vignette de pipelines dans Cloud Manager](/help/implementing/cloud-manager/assets/configure-pipeline/pipelines-card.png)

En cliquant sur l’icône ![Points de suspension - Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) en regard de chaque pipeline, vous pouvez effectuer les actions suivantes :

* [Exécution d’un pipeline](#running-pipelines)
* [Annuler un pipeline](#cancel)
* [Modification d’un pipeline](#editing-pipelines)
* [Suppression d’un pipeline](#deleting-pipelines)
* [Affichage des détails de la dernière exécution d’un pipeline](#view-details)

Au bas de la liste des pipelines, vous disposez des options générales suivantes :

* **Ajouter** - Pour [ajouter un nouveau pipeline de production](configuring-production-pipelines.md) ou [ajouter un nouveau pipeline hors production](configuring-non-production-pipelines.md)
* **Tout afficher** : dirige l’utilisateur vers l’écran Pipelines pour afficher tous les pipelines dans un tableau plus détaillé.
* **Accéder aux informations sur le référentiel** : affiche les informations nécessaires pour accéder au référentiel Git de Cloud Manager.
* **En savoir plus** : permet d’accéder aux ressources de documentation du pipeline CI/CD.

## Page Pipelines {#pipelines}

La page **Pipelines** affiche la liste complète de tous les pipelines du programme sélectionné. Ces informations sont utiles car elles présentent des informations plus complètes que celles disponibles dans la [carte Pipeline](#pipeline-card).

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.

1. Sur la page **Aperçu du programme**, cliquez sur ![Onglet Pipeline - Icône de workflow](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) **Onglet Pipelines**.

1. Sur la page **Pipelines**, vous pouvez voir une liste de tous les pipelines pour le programme et démarrer et arrêter l’exécution du pipeline comme vous le feriez dans la **carte Pipelines**.

Si un pipeline est en cours d’exécution, cliquez sur ![icône Informations - moyenne](https://spectrum.adobe.com/static/icons/ui_18/InfoMedium.svg) dans la colonne **Statut** pour afficher un pop-up contenant des détails sur l’exécution. Dans le pop-up, cliquez sur **Afficher les détails** pour afficher les [détails de l’exécution du pipeline](#view-details).

![Détails de l’exécution du pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-status.png)


Vous pouvez également cliquer sur l’icône ![Points de suspension - Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) en regard du pipeline pour prendre des actions supplémentaires appropriées à l’état du pipeline, telles que [modification](#editing-pipelines) ou [annulation de l’exécution](#cancel).

![Actions de pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-actions.png)

### Marquer les favoris du pipeline{#pipeline-favorites}

Vous pouvez marquer des pipelines spécifiques comme favoris afin qu’ils apparaissent en haut de la liste sur la page **Pipelines**. Cette fonctionnalité facilite la recherche et l’exécution des pipelines fréquemment consultés.

**Pour marquer les favoris de pipeline :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.
1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.
1. Sur la page **Aperçu du programme**, cliquez sur ![Onglet Pipeline - Icône de workflow](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) **Onglet Pipelines**.
1. Sur la page Pipelines, à gauche du nom et du type d’un pipeline, cliquez sur ![icône en forme d’étoile pour le pipeline supprimé des favoris](https://spectrum.adobe.com/static/icons/workflow_18/Smock_StarOutline_18_N.svg) afin de l’ajouter à votre liste de favoris.
Vous pouvez également cliquer sur ![icône Étoile d’un pipeline favori](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Star_18_N.svg) pour supprimer le pipeline de votre liste de favoris.


## Page Activité {#activity}

La page **Activité** affiche une liste complète de toutes les exécutions de pipelines pour le programme sélectionné et d’autres événements de programme importants.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Sur la page **Aperçu du programme**, dans le menu latéral, cliquez sur ![Icône cloche](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Bell_18_N.svg) **Activité**.

1. Sur la page **Activité**, vous pouvez voir une liste de toutes les exécutions de pipeline pour le programme, y compris les exécutions actuelles et historiques.

Si un pipeline est en cours d’exécution, vous pouvez cliquer sur ![Icône Infos - Moyen](https://spectrum.adobe.com/static/icons/ui_18/InfoMedium.svg) dans la colonne **Statut** pour afficher un pop-up contenant des informations sur l’exécution.

![Détails de l’exécution du pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-activity.png)

Cliquez sur la ligne représentant l’exécution du pipeline pour afficher les [détails de l’exécution du pipeline](#view-details).

Vous pouvez également cliquer sur l’icône ![Points de suspension - Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) pour effectuer une action supplémentaire sur l’exécution du pipeline, comme afficher les détails ou télécharger le journal, ce qui vous mène à la page [Détails du pipeline](#view-details).

![Actions d’exécution du pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-execution-actions.png)

## Exécution d’un pipeline {#running-pipelines}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la carte **Pipelines** à partir de la page **Vue d’ensemble du programme**.

1. Cliquez sur ![icône représentant des points de suspension - Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) en regard du pipeline que vous exécutez.

1. Dans le menu déroulant, cliquez sur ![Exécuter - Icône Lecture](https://spectrum.adobe.com/static/icons/workflow_18/Smock_PlayCircle_18_N.svg) **Exécuter**.

   L’exécution du pipeline démarre et la colonne **Statut** affiche sa progression.

Pour afficher les détails de l’exécution, cliquez de nouveau sur ![icône représentant des points de suspension](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) puis sur **[Afficher les détails](#view-details)**.

Selon le type de pipeline, vous pouvez être en mesure d’annuler l’exécution en cliquant de nouveau sur ![icône représentant des points de suspension &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) plus puis sur **Annuler**.

## Exécution de plusieurs pipelines {#run-multiple-pipelines}

Avec Cloud Manager, vous pouvez exécuter plusieurs pipelines simultanément, ce qui améliore l’efficacité du déploiement pour les clients AEM as a Cloud Service. La fonction **Exécuter sélectionné** vous permet de sélectionner plusieurs pipelines et de les déclencher pour qu’ils s’exécutent en même temps. Cela réduit l’effort manuel d’exécution des pipelines individuellement et optimise les workflows de création et de déploiement.

**Pour exécuter plusieurs pipelines :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.
1. Dans le menu de gauche, cliquez sur ![Icône de workflow &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) **Pipelines**.
1. Dans le tableau de la page **Pipeline**, cochez les cases en regard des pipelines à exécuter.
Si nécessaire, cliquez sur ![Icône Filtrer](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Filter_18_N.svg) funnel **Filtres** pour trier les pipelines par nom ou environnement, ou type de code déployé, ou une combinaison des trois.
1. Dans le coin supérieur droit de la page, cliquez sur **Exécuter la sélection (x)**.
1. Dans la boîte de dialogue **Exécuter les pipelines sélectionnés (x)**, cliquez sur **Exécuter (x)**.

   Le bouton **Exécuter** indique le nombre de pipelines qui peuvent continuer. Par exemple, vous avez peut-être sélectionné quatre pipelines, mais un est déjà en cours d’exécution. Ou bien, un environnement lié à un pipeline sélectionné n’existe plus. Dans ce cas, le système s’ajuste en conséquence. Le bouton se met à jour sur « Exécuter (3) » pour indiquer que trois pipelines peuvent continuer.

1. Les pipelines commencent à s’exécuter et leur statut est mis à jour dans la liste **Pipelines**.

## Modification d’un pipeline {#editing-pipelines}

Vous pouvez modifier un pipeline s’il n’est pas en cours d’exécution.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la carte **Pipelines** à partir de la page **Vue d’ensemble du programme**.

1. Cliquez sur ![icône représentant des points de suspension - Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) en regard du pipeline que vous souhaitez modifier.

1. Dans le menu déroulant, cliquez sur **Modifier**.

1. Dans la boîte de dialogue **Modifier le pipeline de production** ou **Modifier le pipeline hors production**, modifiez les mêmes détails que ceux saisis lors de la création du pipeline.

   Consultez les pages suivantes pour plus d’informations sur les champs et les options de configuration disponibles pour les pipelines.
   * [Configurer un pipeline de production](configuring-production-pipelines.md)
   * [Configurer un pipeline hors production](configuring-non-production-pipelines.md)

1. Lorsque vous avez terminé, cliquez sur **Mettre à jour**.

>[!NOTE]
>
>Les pipelines de niveau web et de configuration ne sont pas pris en charge pour les référentiels privés. Voir [Ajouter un référentiel GitHub privé dans Cloud Manager](/help/implementing/cloud-manager/managing-code/private-repositories.md) pour plus d’informations et la liste complète des limitations.

## Suppression d’un pipeline {#deleting-pipelines}

Vous pouvez supprimer un pipeline s’il n’est pas en cours d’exécution.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la carte **Pipelines** à partir de la page **Vue d’ensemble du programme**.

1. Cliquez sur ![icône représentant des points de suspension - Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) en regard du pipeline que vous exécutez.

1. Dans le menu déroulant, cliquez sur **Supprimer**.


## Affichage des détails de la dernière exécution d’un pipeline {#view-details}

Vous pouvez vérifier les détails d’un pipeline pour afficher le statut et les journaux de son exécution la plus récente. Cependant, vous ne pouvez accéder aux détails que si le pipeline est en cours d’exécution ou s’il a été exécuté au moins une fois.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la carte **Pipelines** à partir de la page **Vue d’ensemble du programme**.

1. Dans le menu déroulant, cliquez sur ![icône représentant des points de suspension - Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) en regard du pipeline que vous exécutez.

1. Dans le menu déroulant, cliquez sur **Afficher la dernière exécution**.

   Vous accédez à la page des détails du pipeline en cours d’exécution.

   ![Détails du pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-running-details.png)

   Vous pouvez y voir le statut des différentes étapes du pipeline et récupérer les journaux de génération à des fins de diagnostic. Voir [Déployer votre code](/help/implementing/cloud-manager/deploy-code.md) pour plus d’informations sur le déploiement du code et l’exécution des tests.

   Toutes les étapes d’exécution d’un pipeline s’affichent, celles n’ayant pas encore commencé étant grisées. Les étapes terminées affichent leur durée.

   Une fois l’étape du pipeline terminée, un résumé est présenté.

   ![Résumé d’étape](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-step.png)

1. Cliquez sur **Afficher les détails** pour développer la section **Durée**, où vous pouvez voir la durée moyenne du pipeline en fonction des tendances historiques du programme.

   ![Durée](/help/implementing/cloud-manager/assets/configure-pipeline/duration.png)

1. Si votre pipeline incluait une étape **Analyse du code** qui a signalé des problèmes, cliquez sur **Télécharger les détails** pour accéder à une liste de [tests de qualité du code](/help/implementing/cloud-manager/code-quality-testing.md) qui ont échoué.

   ![Problèmes de qualité du code](assets/managing-pipelines-code-quality-issues.png)

   Le fichier CSV comprend une colonne **Emplacement du fichier du projet**, qui indique le chemin d’accès au code problématique relatif au projet. En revanche, la colonne **Emplacement du fichier** reflète le chemin d’accès généré par Maven.

   ![Détails des problèmes de l’analyse du code du projet](assets/managing-pipelines-code-quality-details.png)

## Annuler un pipeline {#cancel}

Vous pouvez annuler en toute sécurité l’exécution du pipeline s’il est en phase de validation ou de création d’image.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Dans la page d’aperçu du programme, cliquez sur ![icône représentant des points de suspension - Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) du pipeline que vous souhaitez annuler sur la vignette **Pipelines**.

   ![Annulation d’un pipeline &#x200B;](/help/implementing/cloud-manager/assets/cancel-pipeline.png)

1. Cliquez sur **Annuler**.

Vous pouvez également annuler un pipeline à partir de la page des détails du pipeline.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à l’onglet ![Pipelines - icône de workflow](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) **Pipelines** de la page **Aperçu du programme** et sélectionnez le pipeline que vous souhaitez annuler.

   Vous accédez à la page des détails du pipeline en cours d’exécution.

   ![Annuler les détails du pipeline](/help/implementing/cloud-manager/assets/cancel-pipeline-details.png)

1. Cliquez sur **Annuler**.

