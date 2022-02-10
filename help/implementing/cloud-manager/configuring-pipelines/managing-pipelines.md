---
title: Gestion des pipelines
description: Découvrez comment gérer vos pipelines existants, notamment les modifier, les exécuter et les supprimer.
index: true
source-git-commit: 22a08a0cb80052485309ce3d33537e9fe303c6f5
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 4%

---


# Gestion des pipelines {#managing-pipelines}

Découvrez comment gérer vos pipelines existants, notamment les modifier, les exécuter et les supprimer.

## Pipeline Card {#pipeline-card}

Le **Pipelines** sur la carte **Aperçu du programme** dans Cloud Manager , vous donne un aperçu de tous vos pipelines et de leur état actuel.

![Carte Pipelines dans Cloud Manager](/help/implementing/cloud-manager/assets/configure-pipeline/pipelines-card.png)

En cliquant sur le bouton représentant des points de suspension en regard de chaque pipeline, vous pouvez effectuer les actions suivantes.

* [Exécution du pipeline](#running-pipelines)
* [Modification du pipeline](#editing-pipelines)
* [Suppression du pipeline](#deleting-pipelines)
* [Afficher les détails](#view-details)

Au bas de la liste des pipelines, vous disposez d’options générales.

* **Ajouter** - À [ajouter un nouveau pipeline de production](configuring-production-pipelines.md) ou [ajouter un nouveau pipeline hors production](configuring-non-production-pipelines.md)
* **Tout afficher** - Permet à l’utilisateur d’accéder à l’écran Pipelines pour afficher tous les pipelines dans un tableau plus détaillé.
* **Accès aux informations sur le référentiel** - Affiche les informations nécessaires pour accéder au référentiel Git de Cloud Manager.
* **En savoir plus** - Accède aux ressources de documentation du pipeline CI/CD.

## Exécution de pipelines {#running-pipelines}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez au **Pipelines** de la carte **Aperçu du programme** et cliquez sur le bouton représentant des points de suspension en regard du pipeline que vous exécutez sélectionnez **Exécuter** dans le menu.

1. L’exécution du pipeline démarre et est indiquée par la variable **État** colonne .

Pour afficher les détails de l’exécution, cliquez de nouveau sur le bouton représentant des points de suspension et sélectionnez **[Afficher les détails.](#view-details)**

Selon le type de pipeline, vous pouvez annuler l’exécution en cliquant de nouveau sur le bouton représentant des points de suspension et en sélectionnant **Annuler**.

## Modification de pipelines {#editing-pipelines}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez au **Pipelines** de la carte **Aperçu du programme** et cliquez sur le bouton représentant des points de suspension en regard du pipeline que vous souhaitez modifier, puis sélectionnez **Modifier** dans le menu.

1. Le **Modifier le pipeline de production** ou **Modification d’un pipeline hors production** s’affiche, ce qui vous permet de modifier les informations que vous avez saisies lors de la création du pipeline.

   * Consultez les pages suivantes pour plus d’informations sur tous les champs et les options de configuration disponibles pour les pipelines.
      * [Configuration des pipelines de production](configuring-production-pipelines.md)
      * [Configuration de pipelines hors production](configuring-non-production-pipelines.md)

1. Cliquez sur **Mettre à jour** une fois que vous avez terminé de modifier le pipeline.

>[!NOTE]
>
>Vous ne pouvez pas modifier un pipeline en cours d’exécution.

## Suppression de pipelines {#deleting-pipelines}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez au **Pipelines** de la carte **Aperçu du programme** et cliquez sur le bouton représentant des points de suspension en regard du pipeline que vous exécutez sélectionnez **Supprimer** dans le menu.

>[!NOTE]
>
>Vous ne pouvez pas supprimer un pipeline en cours d’exécution.

## Afficher les détails {#view-details}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez au **Pipelines** de la carte **Aperçu du programme** et cliquez sur le bouton représentant des points de suspension en regard du pipeline que vous exécutez sélectionnez **Afficher les détails** dans le menu.

1. Vous accédez à la page des détails du pipeline en cours d’exécution.

![Détails du pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-running-details.png)

Vous pouvez y voir l’état des différentes étapes du pipeline et récupérer les journaux de génération à des fins de diagnostic. Voir le document [Déploiement de votre code](/help/implementing/cloud-manager/deploy-code.md) pour plus d’informations.

>[!NOTE]
>
>Vous ne pouvez afficher que les détails d’un pipeline en cours d’exécution ou qui a été exécuté au moins une fois.