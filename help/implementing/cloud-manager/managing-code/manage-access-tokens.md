---
title: Gestion des jetons d’accès des référentiels externes dans Cloud Manager
description: Découvrez comment afficher, modifier et supprimer les jetons d’accès utilisés pour apporter votre propre Git dans AEM Cloud Manager.
feature: Cloud Manager, Developing
role: Admin, Developer
exl-id: bc9f392c-61f5-4d39-972b-4c6c8f9bab4a
source-git-commit: 2ea076c42a6406548bf48cd246227fc8ddb3a080
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 3%

---

# Gestion des jetons d’accès pour les référentiels externes {#manage-access-tokens}

<!-- badge: label="Private beta" type="Positive" url="/help/implementing/cloud-manager/release-notes/current.md#manage-access-tokens" -->

Cloud Manager utilise des jetons d’accès pour gérer les référentiels hébergés sur des plateformes Git externes. Auparavant, si un jeton expirait, le référentiel associé devait être réintégré pour rester opérationnel.

Désormais, la fonctionnalité **`Manage Access Tokens`** vous permet de gérer les jetons plus efficacement. Vous pouvez afficher, renommer ou supprimer des jetons connectés aux fournisseurs Git externes pris en charge, notamment GitHub Enterprise, GitLab, Bitbucket et Azure DevOps.

Voir aussi [Ajouter des référentiels externes dans Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md).

## Afficher les jetons d’accès {#view-access-tokens}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.
1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme dont vous souhaitez gérer le jeton d’accès Git Apporter votre propre jeton Git.
1. Dans le menu latéral, sous **Programme**, cliquez sur ![Icône Composition du dossier](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderOutline_18_N.svg) **Référentiels**.
1. Dans le coin supérieur droit de la page, cliquez sur **Gérer les jetons d’accès**.

   Le bouton **Gérer les jetons d’accès** n’est visible que si votre programme utilise la fonctionnalité Apporter votre propre Git.

   ![Boîte de dialogue Gérer les jetons d’accès répertoriant un jeton actif et un jeton inactif](/help/implementing/cloud-manager/managing-code/assets/access-tokens-manage.png)

1. Dans la boîte de dialogue **Gérer les jetons d’accès** :
   * Tous les jetons d’accès sont répertoriés.
   * Vous pouvez **modifier** n’importe quel jeton d’accès.
   * Vous ne pouvez **supprimer** que les jetons d’accès qui ne sont *pas en cours d’utilisation*. Si un jeton est en cours d’utilisation, le bouton ![Supprimer l’icône de plan](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DeleteOutline_18_N.svg) est désactivé.

## Modification d’un jeton d’accès {#edit-access-tokens}

1. Dans la boîte de dialogue **Gérer les jetons d’accès**, à droite d’un nom de jeton, cliquez sur ![Modifier l’icône](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg).
1. Dans la boîte de dialogue **Modifier le jeton d’accès**, mettez à jour la valeur **Nom du jeton** ou **Jeton d’accès**, ou les deux.

   ![Boîte de dialogue Modifier le jeton d’accès](/help/implementing/cloud-manager/managing-code/assets/access-tokens-edit.png)

1. Si le **jeton d’accès** est en cours d’utilisation, une notification s’affiche pour vous avertir que tous les référentiels associés sont automatiquement revalidés après la mise à jour.

1. Cliquez sur **Mettre à jour** pour enregistrer les modifications.

## Suppression d’un jeton d’accès {#delete-access-token}

1. Dans la boîte de dialogue **Gérer les jetons d’accès**, à droite d’un nom de jeton, cliquez sur ![Icône Supprimer](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg)

   L’icône est désactivée (![icône Supprimer la composition](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DeleteOutline_18_N.svg)) pour les jetons en cours d’utilisation.

1. Dans la boîte de dialogue **`Delete Access Token`**, cliquez sur **Supprimer** pour supprimer définitivement le jeton.
