---
title: Modification d’un pipeline de production
description: Modification d’un pipeline de production
index: true
source-git-commit: d090329c46155d77a7b132583c777c09555a03c9
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Modification d’un pipeline de production {#edit-prod-pipeline}

Vous pouvez modifier les configurations de pipeline à partir de la page **Aperçu du programme**.

>[!IMPORTANT]
>Vous ne pouvez pas modifier un pipeline en cours d’exécution.

Pour modifier la configuration du pipeline, procédez comme suit :

1. Accédez à la carte **Pipelines** à partir de votre page **Aperçu du programme**.

1. Cliquez sur **...** dans la carte **Pipelines** et cliquez sur **Modifier**, comme illustré dans l’image ci-dessous.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-edit1.png)

1. La boîte de dialogue **Modifier le pipeline de production** s’affiche.

   1. L’onglet **Configuration** vous permet de mettre à jour le **nom du pipeline**, le **déclencheur de déploiement** et le **comportement en cas d’échec de mesure grave**.

      >[!NOTE]
      >Consultez [Ajout et gestion de référentiels](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) pour découvrir comment ajouter et gérer des référentiels dans Cloud Manager.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-edit2.png)


   1. L’onglet **Source** vous offre la possibilité de cocher ou de désélectionner les options **Mettre en pause avant le déploiement en production** et **Planifié** dans les **Options de déploiement en production**.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-editnotier.png)

   1. L’option **Contrôle de l’expérience** vous permet de mettre à jour ou d’ajouter de nouvelles pages.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-edit4.png)

1. Cliquez sur **Mettre à jour** une fois que vous avez terminé de modifier le pipeline.

## Autres actions de pipeline de production {#additional-prod-actions}

### Exécution d’un pipeline de production {#run-prod}

Vous pouvez exécuter le pipeline de production à partir de la carte Pipelines :

1. Accédez à la carte **Pipelines** à partir de votre page **Aperçu du programme**.

1. Cliquez sur **...** dans la carte **Pipelines** et cliquez sur **Exécuter**, comme illustré dans l’image ci-dessous.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-run.png)

### Suppression d’un pipeline de production {#delete-prod}

Vous pouvez supprimer le pipeline de production de la carte Pipelines :

1. Accédez à la carte **Pipelines** à partir de votre page **Aperçu du programme**.

1. Cliquez sur **...** dans la carte **Pipelines** et cliquez sur **Supprimer**, comme illustré dans l’image ci-dessous.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-delete.png)

   >[!NOTE]
   >Un utilisateur disposant du rôle Gestionnaire de déploiement peut désormais supprimer le pipeline de production en libre-service grâce à l’option **Supprimer** de la carte Pipeline.