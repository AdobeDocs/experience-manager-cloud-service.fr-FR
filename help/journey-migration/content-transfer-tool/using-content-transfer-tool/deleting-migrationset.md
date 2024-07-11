---
title: Suppression d’un jeu de migration dans l’outil de transfert de contenu
description: Découvrez comment supprimer un jeu de migration dans l’outil de transfert de contenu.
exl-id: 7ec1c5ca-bac7-4617-8068-78569d7cb503
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 68%

---

# Suppression d’un jeu de migration {#delete-migration-set}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_delete_migrationset"
>title="Suppression d’un jeu de migration"
>abstract="Découvrez la suppression d’un jeu de migration."

Les jeux de migration peuvent être supprimés de Cloud Acceleration Manager.

## Procédure de suppression d’un jeu de migration {#deleting-migration-set}

Pour supprimer un jeu de migration, procédez comme suit :

1. Accédez à la vue Liste du jeu de migration dans Cloud Acceleration Manager et cliquez sur les trois points (**..**) en regard du jeu de migration que vous souhaitez supprimer. L’action **Supprimer** doit être visible, comme illustré ci-dessous.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/migration-delete1.png)

1. Lorsque vous cliquez **Supprimer** une boîte de dialogue s’affiche pour confirmer la suppression.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/migration-delete2.png)

>[!NOTE]
>
>La suppression d’un jeu de migration à partir de Cloud Acceleration Manager (CAM) ne le supprime pas de l’outil de transfert de contenu. Une fois qu’un jeu de migration est supprimé de CAM, l’utilisateur ne pourra pas exécuter d’extractions sur ce jeu de migration à partir de l’assistant de transfert de contenu. Cependant, si le jeu de migration a été supprimé de l’assistant de transfert de contenu, l’utilisateur peut le recréer tant que le jeu de migration est toujours disponible dans Cloud Acceleration Manager.
>
>Pour que l’outil de transfert de contenu reste synchronisé avec Cloud Acceleration Manager, l’utilisateur peut également supprimer le jeu de migration de l’outil de transfert de contenu.

Pour supprimer le jeu de migration de l’assistant de transfert de contenu, sélectionnez-le et cliquez sur **Supprimer** dans la barre d’actions.

![Image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam27.png)
