---
title: Gestion des pipelines
description: Découvrez comment gérer vos pipelines existants, notamment en les modifiant, en les exécutant et en les supprimant.
index: true
exl-id: 4aff5a84-134a-43fa-8de8-8d564f4edd16
source-git-commit: a3e79441d46fa961fcd05ea54e84957754890d69
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 46%

---


# Gestion des pipelines {#managing-pipelines}

Découvrez comment gérer vos pipelines existants, notamment en les modifiant, en les exécutant et en les supprimant.

## Vignette de pipeline {#pipeline-card}

La vignette **Pipelines** de la page **Aperçu du programme** dans Cloud Manager vous donne un aperçu de tous vos pipelines et de leur statut actuel.

![Vignette de pipelines dans Cloud Manager](/help/implementing/cloud-manager/assets/configure-pipeline/pipelines-card.png)

En cliquant sur le bouton représentant des points de suspension à côté de chaque pipeline, vous pouvez effectuer les actions suivantes.

* [Exécuter le pipeline](#running-pipelines)
* [Modifier le pipeline](#editing-pipelines)
* [Supprimer le pipeline](#deleting-pipelines)
* [Afficher les détails](#view-details)

Au bas de la liste des pipelines, vous disposez d’options générales.

* **Ajouter** : permet d’[ajouter un nouveau pipeline de production](configuring-production-pipelines.md) ou d’[ajouter un nouveau pipeline hors production](configuring-non-production-pipelines.md).
* **Tout afficher** : dirige l’utilisateur vers l’écran Pipelines pour afficher tous les pipelines dans un tableau plus détaillé.
* **Accéder aux informations sur le référentiel** : affiche les informations nécessaires pour accéder au référentiel Git de Cloud Manager.
* **En savoir plus** : permet d’accéder aux ressources de documentation du pipeline CI/CD.

## Fenêtre Pipelines {#pipelines}

La variable **Pipelines** affiche une liste complète de tous les pipelines pour le programme sélectionné. Cela s’avère utile, car il présente des informations plus complètes que celles disponibles dans la variable [Pipeline Card.](#pipeline-card)

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Dans la **Aperçu du programme** , appuyez ou cliquez sur l’icône **Pipelines** pour basculer vers l’onglet **Pipelines** fenêtre.

1. Vous y trouverez une liste de tous les pipelines pour le programme ainsi que le démarrage et l’arrêt de l’exécution du pipeline, comme vous le feriez dans la section **Pipelines Card**.

Si un pipeline est en cours d’exécution, survolez son **État** affiche des détails sur l’exécution.

![Détails de l’exécution du pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-status.png)

Appuyez ou cliquez sur **Afficher les détails** vous emmènera au [détails de l’exécution du pipeline.](#view-details)

## Fenêtre d’activité {#activity}

La variable **Activités** affiche une liste complète de toutes les exécutions de pipelines pour le programme sélectionné.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Dans la **Aperçu du programme** , appuyez ou cliquez sur l’icône **Activité** pour basculer vers l’onglet **Activité** fenêtre.

1. Vous y trouverez une liste de toutes les exécutions de pipeline pour le programme, y compris les exécutions actuelles et historiques.

Si un pipeline est en cours d’exécution, survolez son **État** affiche des détails sur l’exécution.

![Détails de l’exécution du pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-activity.png)

Appuyez ou cliquez sur **Afficher les détails** vous emmènera au [détails de l’exécution du pipeline.](#view-details)

## Exécution des pipelines {#running-pipelines}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez au **Pipelines** de la carte **Aperçu du programme** et cliquez sur le bouton représentant des points de suspension en regard du pipeline que vous exécutez sélectionnez **Exécuter** dans le menu.

1. L’exécution du pipeline démarre et est indiquée par la colonne **Statut**.

Pour afficher les détails de l’exécution, cliquez de nouveau sur le bouton représentant des points de suspension et sélectionnez **[Afficher les détails](#view-details)**.

Selon le type de pipeline, vous pouvez être en mesure d’annuler l’exécution en cliquant de nouveau sur le bouton représentant des points de suspension et en sélectionnant **Annuler**.

## Modification de pipelines {#editing-pipelines}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez au **Pipelines** de la carte **Aperçu du programme** et cliquez sur le bouton représentant des points de suspension en regard du pipeline que vous souhaitez modifier, puis sélectionnez **Modifier** dans le menu.

1. La boîte de dialogue **Modifier le pipeline de production** ou **Modifier le pipeline hors production** s’affiche, ce qui vous permet de modifier les mêmes détails que ceux saisis lors de la création du pipeline.

   * Consultez les pages suivantes pour plus d’informations sur tous les champs et options de configuration disponibles pour les pipelines.
      * [Configuration des pipelines de production](configuring-production-pipelines.md)
      * [Configurer des pipelines hors production](configuring-non-production-pipelines.md)

1. Cliquez sur **Mettre à jour** une fois que vous avez terminé de modifier le pipeline.

>[!NOTE]
>
>Vous ne pouvez pas modifier un pipeline en cours d’exécution.

## Suppression de pipelines {#deleting-pipelines}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez au **Pipelines** de la carte **Aperçu du programme** et cliquez sur le bouton représentant des points de suspension en regard du pipeline que vous exécutez sélectionnez **Supprimer** dans le menu.

>[!NOTE]
>
>Vous ne pouvez pas supprimer un pipeline en cours d’exécution.

## Afficher les détails du pipeline {#view-details}

Vous pouvez afficher les détails d’un pipeline pour afficher l’état et les journaux de sa dernière exécution.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez au **Pipelines** de la carte **Aperçu du programme** et cliquez sur le bouton représentant des points de suspension en regard du pipeline que vous exécutez sélectionnez **Afficher les détails** dans le menu.

1. Vous accédez à la page des détails du pipeline en cours d’exécution.

![Détails du pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-running-details.png)

Vous pouvez y voir le statut des différentes étapes du pipeline et récupérer les journaux de génération à des fins de diagnostic. Voir le document [Déploiement de votre code](/help/implementing/cloud-manager/deploy-code.md) pour plus d’informations sur le déploiement du code et l’exécution des tests.

Toutes les étapes d’exécution d’un pipeline s’affichent avec celles qui n’ont pas encore commencé en grisé. Les étapes terminées affichent leur durée.

Une fois une étape de pipeline terminée, un résumé est présenté.

![Synthèse des étapes](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-step.png)

Appuyez ou cliquez sur le bouton **Afficher les détails** pour afficher le lien **Durée** . Cela inclut la durée moyenne du pipeline en fonction de la tendance historique de ce programme.

![Durée](/help/implementing/cloud-manager/assets/configure-pipeline/duration.png)

>[!NOTE]
>
>Vous pouvez uniquement afficher les détails d’un pipeline en cours d’exécution ou qui a été exécuté au moins une fois.

## Annuler les pipelines {#cancel}

Si un pipeline se trouve dans la phase de validation ou d’image de version, vous pouvez annuler l’exécution du pipeline en toute sécurité.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Dans la page de présentation du programme, cliquez sur le bouton représentant des points de suspension du pipeline que vous souhaitez annuler sur la page **Pipelines** carte.

   ![Annulation d’un pipeline](/help/implementing/cloud-manager/assets/cancel-pipeline.png)

1. Appuyez ou cliquez sur **Annuler**.

Vous pouvez également annuler un pipeline à partir de la page des détails du pipeline.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez au **Pipelines** à partir de la **Aperçu du programme** et appuyez ou cliquez sur le pipeline que vous souhaitez annuler.

1. Vous accédez à la page des détails du pipeline en cours d’exécution.

   ![Annuler les détails du pipeline](/help/implementing/cloud-manager/assets/cancel-pipeline-details.png)

1. Appuyez ou cliquez sur **Annuler**.
