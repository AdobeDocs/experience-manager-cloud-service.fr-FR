---
title: Modification d’un pipeline de production
description: Modification d’un pipeline de production
index: true
source-git-commit: d090329c46155d77a7b132583c777c09555a03c9
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---


# Modification d’un pipeline de production {#edit-prod-pipeline}

Vous pouvez modifier les configurations de pipeline à partir du **Aperçu du programme** page.

>[!IMPORTANT]
>Vous ne pouvez pas modifier un pipeline en cours d’exécution.

Pour modifier le pipeline configuré, procédez comme suit :

1. Accédez à **Pipelines** de la carte **Aperçu du programme** page.

1. Cliquez sur **...** de la **Pipelines** et cliquez sur **Modifier**, comme illustré dans la figure ci-dessous.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-edit1.png)

1. Le **Modifier le pipeline de production** s’affiche.

   1. Le **Configuration** vous permet de mettre à jour la variable **Nom du pipeline**, **Déclencheur de déploiement**, et **Comportement d’échec des mesures importantes**.

      >[!NOTE]
      >Voir [Ajout et gestion des référentiels](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) pour savoir comment ajouter et gérer des référentiels dans Cloud Manager.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-edit2.png)


   1. Le **Source** vous offre la possibilité de vérifier ou de décocher des **Mettre en pause avant le déploiement en production** et **Planifié** options de **Options de déploiement en production**.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-editnotier.png)

   1. Le **Audit de l’expérience** vous permet de mettre à jour ou d’ajouter de nouvelles pages.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-edit4.png)

1. Cliquez sur **Mettre à jour** une fois que vous avez terminé de modifier le pipeline.

## Autres actions de pipeline de production {#additional-prod-actions}

### Exécution d’un pipeline de production {#run-prod}

Vous pouvez exécuter le pipeline de production à partir de la carte Pipelines :

1. Accédez à **Pipelines** de la carte **Aperçu du programme** page.

1. Cliquez sur **...** de la **Pipelines** et cliquez sur **Exécuter**, comme illustré dans la figure ci-dessous.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-run.png)

### Suppression d’un pipeline de production {#delete-prod}

Vous pouvez supprimer le pipeline de production de la carte Pipelines :

1. Accédez à **Pipelines** de la carte **Aperçu du programme** page.

1. Cliquez sur **...** de la **Pipelines** et cliquez sur **Supprimer**, comme illustré dans la figure ci-dessous.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-delete.png)

   >[!NOTE]
   >Un utilisateur disposant du rôle Gestionnaire de déploiement peut désormais supprimer le pipeline de production en libre-service via le **Supprimer** de la carte Pipeline.