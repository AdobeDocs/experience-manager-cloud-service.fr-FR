---
title: Modification d’un pipeline hors production
description: Modification d’un pipeline hors production
index: true
source-git-commit: 7dc9f9a189927f3522445fac36a1606521f410b2
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---


# Modification d’un pipeline hors production {#edit-non-prod-pipeline}

Vous pouvez modifier les configurations de pipeline à partir du **Carte Pipelines** de **Aperçu du programme** page.

>[!IMPORTANT]
>Vous ne pouvez pas modifier un pipeline en cours d’exécution.

Suivez les étapes ci-dessous pour modifier le pipeline hors production configuré :

1. Accédez à **Pipelines** de la carte **Aperçu du programme** page.

1. Sélectionnez le pipeline hors production et cliquez sur **...**. Cliquez sur **Modifier**, comme illustré dans la figure ci-dessous.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-edit1.png)

1. Le **Modifier le pipeline de production** s’affiche.

   1. Le **Configuration** vous permet de mettre à jour la variable **Nom du pipeline**, **Déclencheur de déploiement**, et **Comportement des échecs de mesure importants**.

      >[!NOTE]
      >Voir [Ajout et gestion des référentiels](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) pour savoir comment ajouter et gérer des référentiels dans Cloud Manager.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-edit2.png)


   1. Le **Code source** vous permet de mettre à jour la variable **Référentiel** et le **Branche Git**.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-edit3.png)

1. Cliquez sur **Mettre à jour** une fois la modification du pipeline hors production terminée.

## Autres actions de pipeline hors production {#additional-nonprod-actions}

### Exécution d’un pipeline hors production {#run-nonprod}

Vous pouvez exécuter le pipeline de production à partir de la carte Pipelines :

1. Accédez à **Pipelines** de la carte **Aperçu du programme** page.

1. Cliquez sur **...** de la **Pipelines** et cliquez sur **Exécuter**, comme illustré dans la figure ci-dessous.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-run1.png)

### Suppression d’un pipeline hors production {#delete-nonprod}

Vous pouvez supprimer le pipeline de production de la carte Pipelines :

1. Accédez à **Pipelines** de la carte **Aperçu du programme** page.

1. Cliquez sur **...** de la **Pipelines** et cliquez sur **Supprimer**, comme illustré dans la figure ci-dessous.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-delete.png)
