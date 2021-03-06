---
title: Modification de programmes
description: Découvrez comment modifier vos programmes de production et Sandbox pour ajuster leurs options après les avoir créés.
exl-id: 819e4a6e-f77a-4594-a402-a300dcbdf510
source-git-commit: d805ed744af0e5c95863a1c67439b384cc5d11b2
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 74%

---

# Modification de programmes {#editing-programs}

Les utilisateurs disposant des autorisations requises peuvent modifier les [programmes de production créés dans votre organisation](creating-production-programs.md) ainsi que les [programmes Sandbox créés dans votre organisation.](creating-sandbox-programs.md) En modifiant un programme, vous pouvez :

* Ajouter la solution Sites à un programme existant avec Assets et inversement.
* Supprimer Sites ou Assets d’un programme existant contenant à la fois Sites et Assets.
* Ajouter un deuxième droit non utilisé sur une solution à un programme existant ou à titre de nouveau programme.
* Supprimer les programmes Sandbox.

>[!NOTE]
>
>Vous devez être membre du rôle **Propriétaire de l’entreprise** pour modifier des programmes ou supprimer des programmes Sandbox.

Pour modifier un programme, procédez comme suit.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Cliquez sur le programme que vous souhaitez modifier pour en afficher les détails.

1. Cliquez sur le nom de votre programme dans le coin supérieur gauche de la page, puis sélectionnez **Modifier le programme**.

   ![Option Modifier le programme](assets/edit-program-overview.png)

1. Le **Modifier le programme** s’ouvre. Sur le **Général** modifiez le nom et la description du programme.

   * Au moins une solution doit être sélectionnée pour un programme.

   ![Onglet Général](assets/edit-program-prod1.png)

1. Sur le **Solutions et modules complémentaires** , modifiez les solutions du programme.

   ![Solutions sélectionnées](assets/edit-prg.png)

1. Cliquez sur le chevron situé avant les noms des solutions pour afficher les modules complémentaires facultatifs, tels que la sélection de l’option de module complémentaire **Commerce** sous **Sites**.

   ![Modifier les modules complémentaires](assets/edit-program-add-on.png)

1. Sur le **Paramètres d’activation** modifiez la date d’activation prévue du programme.

   ![Modification des paramètres d’activation](assets/edit-program-go-live.png)

   * Cette date est destinée à un usage informatif uniquement et déclenche le widget GoLive sur la page d’aperçu du programme afin de fournir des liens internes au produit vers AEM documentation des bonnes pratiques as a Cloud Service en temps opportun, afin de vous aligner sur votre parcours et d’offrir ainsi une expérience GoLive réussie et fluide.

1. Cliquez sur **Mettre à jour** pour enregistrer vos modifications dans le programme.

Chaque fois qu’un programme est modifié, y compris l’ajout ou la suppression d’une solution ou d’un module complémentaire, ces modifications prennent effet après le prochain déploiement.

## Suppression de programmes Sandbox {#delete-sandbox-program}

La suppression d’un programme Sandbox supprimera tous les environnements et les pipelines qui y sont associés.

>[!TIP]
>
>Les utilisateurs avec des rôles de **Propriétaire de l’entreprise** ou **Responsable du déploiement** peuvent également supprimer leurs environnements de production et d’évaluation plutôt que l’ensemble du programme Sandbox.

Pour supprimer un programme Sandbox, procédez comme suit.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Cliquez sur le programme que vous souhaitez modifier pour en afficher les détails.

1. Cliquez sur le nom de votre programme dans le coin supérieur gauche de la page et sélectionnez **Supprimer le programme**.

   ![Option Supprimer le programme](assets/delete-sandbox1.png)

Vous pouvez également cliquer sur le bouton représentant des points de suspension sur la vignette de votre programme dans la page de présentation de Cloud Manager et sélectionner **Supprimer le programme**.

![Supprimer Sandbox d’une vignette de programme](assets/delete-sandbox2.png)

>[!NOTE]
>
>Seuls les programmes Sandbox peuvent être supprimés. Les programmes de production ne peuvent pas être supprimés.
