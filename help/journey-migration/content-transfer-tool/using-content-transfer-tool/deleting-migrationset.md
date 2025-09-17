---
title: Suppression d’un ensemble de migration dans l’outil de transfert de contenu
description: Découvrez comment supprimer un jeu de migration dans l’outil de transfert de contenu.
exl-id: 7ec1c5ca-bac7-4617-8068-78569d7cb503
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 68%

---

# Suppression d’un ensemble de migration {#delete-migration-set}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_delete_migrationset"
>title="Suppression d’un ensemble de migration"
>abstract="Découvrez la suppression d’un ensemble de migration."

Les ensembles de migration peuvent être supprimés de Cloud Acceleration Manager.

## Procédure de suppression d’un ensemble de migration {#deleting-migration-set}

Pour supprimer un ensemble de migration, procédez comme suit :

1. Accédez à la vue Liste des jeux de migration dans Cloud Acceleration Manager et cliquez sur les trois points (**...**) en regard du jeu de migration à supprimer. L’action **Supprimer** doit être visible, comme illustré ci-dessous.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/migration-delete1.png)

1. Lorsque vous cliquez sur **Supprimer** une boîte de dialogue s’affiche pour confirmer la suppression.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/migration-delete2.png)

>[!NOTE]
>
>La suppression d’un ensemble de migration à partir de Cloud Acceleration Manager (CAM) ne le supprime pas de l’outil de transfert de contenu. Une fois qu’un ensemble de migration est supprimé de CAM, vous ne pourrez pas exécuter d’extractions sur cet ensemble à partir de l’assistant de transfert de contenu. Cependant, si l’ensemble de migration a été supprimé de l’assistant de transfert de contenu, il peut être récréé tant que l’ensemble de migration est disponible dans Cloud Acceleration Manager.
>
>Pour que l’outil de transfert de contenu reste synchronisé avec Cloud Acceleration Manager, vous pouvez également supprimer l’ensemble de migration de l’outil de transfert de contenu.

Pour supprimer le jeu de migration de l’assistant de transfert de contenu, sélectionnez le jeu de migration et cliquez sur **Supprimer** dans la barre d’actions.

![Image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam27.png)
