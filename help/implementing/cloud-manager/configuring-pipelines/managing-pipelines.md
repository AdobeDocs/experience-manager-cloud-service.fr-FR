---
title: Gérer les pipelines
description: Découvrez comment gérer vos pipelines existants, notamment en les modifiant, en les exécutant et en les supprimant.
index: true
exl-id: 4aff5a84-134a-43fa-8de8-8d564f4edd16
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f7a8e823f058115f11241f0864517432a7dea5ab
workflow-type: tm+mt
source-wordcount: '1164'
ht-degree: 32%

---


# Gérer les pipelines {#managing-pipelines}

Découvrez comment gérer vos pipelines existants, notamment en les modifiant, en les exécutant et en les supprimant.

## Carte de pipeline {#pipeline-card}

La vignette **Pipelines** de la page **Aperçu du programme** dans Cloud Manager vous donne un aperçu de tous vos pipelines et de leur statut actuel.

![Vignette de pipelines dans Cloud Manager](/help/implementing/cloud-manager/assets/configure-pipeline/pipelines-card.png)

En cliquant sur ![Ellipsis - Icône More](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) en regard de chaque pipeline, vous pouvez effectuer les actions suivantes :

* [Exécution d’un pipeline](#running-pipelines)
* [Annulation d’un pipeline](#cancel)
* [Modification d’un pipeline](#editing-pipelines)
* [Suppression d’un pipeline](#deleting-pipelines)
* [Affichage des détails de la dernière exécution d’un pipeline](#view-details)

Au bas de la liste des pipelines, vous disposez des options générales suivantes :

* **Ajouter** - Pour [ajouter un nouveau pipeline de production](configuring-production-pipelines.md) ou [ajouter un nouveau pipeline hors production](configuring-non-production-pipelines.md)
* **Tout afficher** : dirige l’utilisateur vers l’écran Pipelines pour afficher tous les pipelines dans un tableau plus détaillé.
* **Accéder aux informations sur le référentiel** : affiche les informations nécessaires pour accéder au référentiel Git de Cloud Manager.
* **En savoir plus** : permet d’accéder aux ressources de documentation du pipeline CI/CD.

## Page Pipelines {#pipelines}

La page **Pipelines** affiche la liste complète de tous les pipelines pour le programme sélectionné. Ces informations sont utiles car elles présentent des informations plus complètes que celles disponibles dans la [carte de pipeline](#pipeline-card).

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.

1. Sur la page **Aperçu du programme**, cliquez sur l’onglet ![Pipeline tab - Icône Workflow](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) **Pipelines** .

1. Sur la page **Pipelines**, vous pouvez voir une liste de tous les pipelines pour le programme et lancer et arrêter l’exécution du pipeline comme vous le feriez dans la **carte Pipelines**.

Si un pipeline est en cours d’exécution, cliquez sur ![Info - icône moyenne](https://spectrum.adobe.com/static/icons/ui_18/InfoMedium.svg) dans la colonne **État** pour afficher une fenêtre contextuelle contenant des détails sur l’exécution. Dans la fenêtre contextuelle, cliquez sur **Afficher les détails** pour afficher les [détails de l’exécution du pipeline](#view-details).

![Détails de l’exécution du pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-status.png)


Vous pouvez également cliquer sur ![Ellipsis - Icône More](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) en regard du pipeline pour prendre des actions supplémentaires appropriées à l’état du pipeline, telles que [le modifier](#editing-pipelines) ou [annuler l’exécution](#cancel).

![Actions de pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-actions.png)

## Page d’activité {#activity}

La page **Activité** affiche une liste complète de toutes les exécutions de pipelines pour le programme sélectionné ainsi que d’autres événements de programme importants.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Sur la page **Aperçu du programme**, dans le menu latéral, cliquez sur ![Icône Bell](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Bell_18_N.svg) **Activité**.

1. Sur la page **Activité** , vous pouvez voir une liste de toutes les exécutions de pipeline pour le programme, y compris les exécutions actuelles et historiques.

Si un pipeline est en cours d’exécution, vous pouvez cliquer sur ![Info - icône moyenne](https://spectrum.adobe.com/static/icons/ui_18/InfoMedium.svg) dans la colonne **État** pour afficher une fenêtre contextuelle contenant des informations sur l’exécution.

![Détails de l’exécution du pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-activity.png)

Cliquez sur la ligne représentant l’exécution du pipeline pour afficher les [détails de l’exécution du pipeline](#view-details).

Vous pouvez également cliquer sur ![Ellipsis - Icône More](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) pour effectuer des actions supplémentaires sur l’exécution du pipeline, comme afficher ses détails ou télécharger le journal, ce qui vous permet d’accéder à la [ page des détails du pipeline](#view-details).

![Actions d’exécution de pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-execution-actions.png)

## Exécution d’un pipeline {#running-pipelines}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la carte **Pipelines** à partir de la page **Vue d’ensemble du programme**.

1. Cliquez sur ![Ellipsis - Icône More](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) en regard du pipeline que vous exécutez.

1. Dans le menu déroulant, cliquez sur ![Icône Exécuter - Lecture](https://spectrum.adobe.com/static/icons/workflow_18/Smock_PlayCircle_18_N.svg) **Exécuter**.

   L’exécution du pipeline démarre et la colonne **Status** affiche sa progression.

Pour afficher les détails de l’exécution, cliquez de nouveau sur ![Ellipse - Icône More](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) et cliquez sur **[Afficher les détails](#view-details)**.

Selon le type de pipeline, vous pouvez annuler l’exécution en cliquant de nouveau sur ![Ellipsis - Icône More](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) et en cliquant sur **Annuler**.

## Modification d’un pipeline {#editing-pipelines}

Vous pouvez modifier un pipeline s’il n’est pas en cours d’exécution.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la carte **Pipelines** à partir de la page **Vue d’ensemble du programme**.

1. Cliquez sur ![Ellipsis - Icône More](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) en regard du pipeline que vous souhaitez modifier.

1. Dans le menu déroulant, cliquez sur **Modifier**.

1. Dans la boîte de dialogue **Modifier le pipeline de production** ou **Modifier le pipeline hors production**, modifiez les mêmes informations que celles que vous avez saisies lors de la création du pipeline.

   Consultez les pages suivantes pour plus d’informations sur les champs et les options de configuration disponibles pour les pipelines.
   * [Configurer un pipeline de production](configuring-production-pipelines.md)
   * [Configurer un pipeline hors production](configuring-non-production-pipelines.md)

1. Une fois que vous avez terminé, cliquez sur **Mettre à jour**.

>[!NOTE]
>
>Les pipelines de niveau web et de configuration ne sont pas pris en charge pour les référentiels privés. Voir [Ajout d’un référentiel GitHub privé dans Cloud Manager](/help/implementing/cloud-manager/managing-code/private-repositories.md) pour plus d’informations et la liste complète des limites.

## Suppression d’un pipeline {#deleting-pipelines}

Vous pouvez supprimer un pipeline s’il n’est pas en cours d’exécution.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la carte **Pipelines** à partir de la page **Vue d’ensemble du programme**.

1. Cliquez sur ![Ellipsis - Icône More](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) en regard du pipeline que vous exécutez.

1. Dans le menu déroulant, cliquez sur **Supprimer**.


## Affichage des détails de la dernière exécution d’un pipeline {#view-details}

Vous pouvez vérifier les détails d’un pipeline pour afficher l’état et les journaux de son exécution la plus récente. Cependant, vous ne pouvez accéder aux détails que si le pipeline est en cours d’exécution ou a été exécuté au moins une fois.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la carte **Pipelines** à partir de la page **Vue d’ensemble du programme**.

1. Dans le menu déroulant, cliquez sur ![Ellipsis - Icône More](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) en regard du pipeline que vous exécutez.

1. Dans le menu déroulant, cliquez sur **Afficher la dernière exécution**.

   Vous accédez à la page des détails du pipeline en cours d’exécution.

   ![Détails du pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-running-details.png)

   Vous pouvez y voir le statut des différentes étapes du pipeline et récupérer les journaux de génération à des fins de diagnostic. Voir [Déploiement de votre code](/help/implementing/cloud-manager/deploy-code.md) pour plus d’informations sur le déploiement du code et l’exécution des tests.

   Toutes les étapes d’exécution d’un pipeline s’affichent, celles n’ayant pas encore commencé étant grisées. Les étapes terminées affichent leur durée.

   Une fois l’étape de pipeline terminée, un résumé est présenté.

   ![Résumé d’étape](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-step.png)

1. Cliquez sur **Afficher les détails** pour développer la section **Durée**, dans laquelle vous pouvez afficher la durée moyenne du pipeline en fonction des tendances historiques du programme.

   ![Durée](/help/implementing/cloud-manager/assets/configure-pipeline/duration.png)

1. Si votre pipeline incluait une étape **Analyse du code** qui signalait des problèmes, cliquez sur **Télécharger les détails** pour accéder à une liste de [tests de qualité du code](/help/implementing/cloud-manager/code-quality-testing.md) qui n’ont pas réussi.

   ![Problèmes de qualité du code](assets/managing-pipelines-code-quality-issues.png)

   Le fichier CSV comprend une colonne **Emplacement du fichier du projet**, indiquant le chemin d’accès au code problématique par rapport au projet. En revanche, la colonne **Emplacement du fichier** reflète le chemin généré par Maven.

   ![Détails des problèmes de l’analyse du code du projet](assets/managing-pipelines-code-quality-details.png)

## Annulation d’un pipeline {#cancel}

Vous pouvez annuler l’exécution du pipeline en toute sécurité si elle est dans la phase de validation ou de création d’image.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Sur la page de présentation du programme, cliquez sur ![Ellipsis - Icône More](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) du pipeline que vous souhaitez annuler sur la carte **Pipelines** .

   ![Annulation d’un pipeline](/help/implementing/cloud-manager/assets/cancel-pipeline.png)

1. Cliquez sur **Annuler**.

Vous pouvez également annuler un pipeline à partir de la page des détails du pipeline.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à l’onglet ![Pipelines - Icône de workflow](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) **Pipelines** de la page **Aperçu du programme** et sélectionnez le pipeline que vous souhaitez annuler.

   Vous accédez à la page des détails du pipeline en cours d’exécution.

   ![Annuler les détails du pipeline](/help/implementing/cloud-manager/assets/cancel-pipeline-details.png)

1. Cliquez sur **Annuler**.
