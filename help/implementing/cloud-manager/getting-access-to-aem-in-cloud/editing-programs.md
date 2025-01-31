---
title: Modifier des programmes
description: Découvrez comment modifier vos programmes de production et Sandbox pour ajuster leurs options après les avoir créés.
exl-id: 819e4a6e-f77a-4594-a402-a300dcbdf510
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f0cf9fa7da7e89d42ab90dee0e8400b26f004574
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 25%

---


# Modifier des programmes {#editing-programs}

Pour gérer et modifier des programmes, commencez par la console [**Mes programmes**](/help/implementing/cloud-manager/navigation.md). La page **Mes programmes** donne un aperçu de tous les programmes auxquels vous avez accès. Lors de la sélection d’un programme individuel, la page **Aperçu du programme** fournit en un coup d’œil des détails sur le programme.

Dans l’**Aperçu du programme**, les utilisateurs disposant des autorisations requises peuvent modifier les [programmes de production créés dans votre organisation](creating-production-programs.md) et les [programmes Sandbox créés dans votre organisation](creating-sandbox-programs.md). En modifiant un programme, vous pouvez :

* Ajoutez la solution Sites à un programme existant avec Assets et inversement.
* Supprimer Sites ou Assets d’un programme existant contenant à la fois Sites et Assets.
* Ajoutez un droit de solution inutilisé à un programme existant ou créez un programme.
* Supprimer les programmes Sandbox.

## Autorisations {#permissions}

Vous devez disposer du rôle **Propriétaire de l’entreprise** pour modifier des programmes, supprimer des programmes Sandbox et accéder au tableau de bord des licences.

## Modifier un programme {#editing}

Chaque fois qu’un programme est modifié, y compris par l’ajout ou la suppression d’une solution ou d’un module complémentaire, ces modifications prennent effet après le prochain déploiement.

**Pour modifier un programme, procédez comme suit**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur la page **[Mes programmes](#my-programs)**, cliquez sur le programme que vous souhaitez modifier pour en afficher les détails.

1. Cliquez sur le nom de votre programme dans le coin supérieur gauche de la page, puis sélectionnez **Modifier le programme**.

   ![Option Modifier le programme](assets/edit-program-overview.png)

1. La page **Modifier le programme** s’ouvre sur l’onglet **Général**.

   ![Onglet Général](assets/edit-program-prod1.png)

1. Les options disponibles pour la modification du programme sont les mêmes que pour la création du programme.
   * Voir [Créer des programmes de production](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) et [Créer des programmes Sandbox](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) pour plus d’informations sur les différentes options.
   * [D’autres options](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#options) peuvent être disponibles pour votre programme de production en fonction des droits de votre entreprise.

1. Cliquez sur **Mettre à jour** pour enregistrer vos modifications dans le programme.

## Suppression d’un programme Sandbox {#delete-sandbox-program}

La suppression d’un programme Sandbox supprime tous les environnements et les pipelines qui y sont associés.

>[!TIP]
>
>Les utilisateurs avec des rôles de **Propriétaire de l’entreprise** ou **Responsable du déploiement** peuvent également supprimer leurs environnements de production et d’évaluation plutôt que l’ensemble du programme Sandbox.

**Pour supprimer un programme Sandbox, procédez comme suit**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur la page **[Mes programmes](#my-programs)**, cliquez sur le programme que vous souhaitez modifier pour en afficher les détails.

1. Cliquez sur le nom de votre programme dans le coin supérieur gauche de la page, puis sélectionnez **Supprimer le programme**.

   ![Option Supprimer le programme](assets/delete-sandbox1.png)

Vous pouvez également cliquer sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) sur la vignette de votre programme dans la page d’aperçu de Cloud Manager et sélectionner **Supprimer le programme**.

![Supprimer Sandbox d’une vignette de programme](assets/delete-sandbox2.png)

>[!NOTE]
>
>Seuls les programmes Sandbox peuvent être supprimés. Les programmes de production ne peuvent pas être supprimés.
