---
title: Modification de programmes
description: Découvrez comment modifier vos programmes de production et Sandbox pour ajuster leurs options après les avoir créés.
exl-id: 819e4a6e-f77a-4594-a402-a300dcbdf510
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 30%

---


# Modification de programmes {#editing-programs}

Pour gérer et modifier des programmes, commencez à l’adresse [**Mes programmes** console.](/help/implementing/cloud-manager/navigation.md) La variable **Mes programmes** fournit un aperçu de tous les programmes auxquels vous avez accès. Lors de la sélection d’un programme individuel, la variable **Aperçu du programme** fournit des détails sur le programme en un coup d’oeil.

Dans la **Aperçu du programme**, les utilisateurs disposant des autorisations requises peuvent modifier [programmes de production créés dans votre organisation](creating-production-programs.md) et [programmes sandbox créés dans votre entreprise.](creating-sandbox-programs.md) En éditant un programme, vous pouvez :

* Ajoutez la solution Sites à un programme existant avec Assets et inversement.
* Supprimer Sites ou Assets d’un programme existant contenant à la fois Sites et Assets.
* Ajoutez un second droit de solution inutilisé à un programme existant ou en tant que nouveau programme.
* Supprimer les programmes Sandbox.

## Autorisations {#permissions}

Vous devez être membre de la fonction **Propriétaire de l’entreprise** rôle permettant de modifier des programmes ou de supprimer des programmes Sandbox, ainsi que d’accéder au tableau de bord de licence.

## Modifier un programme {#editing}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur le **[Mes programmes](#my-programs)** , cliquez sur le programme à modifier pour en afficher les détails.

1. Cliquez sur le nom de votre programme dans le coin supérieur gauche de la page, puis sélectionnez **Modifier le programme**.

   ![Option Modifier le programme](assets/edit-program-overview.png)

1. La variable **Modifier le programme** s’ouvre sur la page **Général** .

   ![Onglet Général](assets/edit-program-prod1.png)

1. Les options disponibles pour la modification du programme sont les mêmes que lors de la création du programme.
   * Veuillez consulter les documents [Création de programmes de production](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) et [Création de programmes Sandbox](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) pour plus d’informations sur les différentes options.
   * [Options supplémentaires](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#options) peut être disponible pour votre programme de production en fonction des droits de votre organisation.

1. Cliquez sur **Mettre à jour** pour enregistrer vos modifications dans le programme.

Les modifications apportées au programme sont enregistrées.

>[!NOTE]
>
>Chaque fois qu’un programme est modifié, y compris l’ajout ou la suppression d’une solution ou d’un module complémentaire, ces modifications prennent effet après le prochain déploiement.

## Suppression de programmes Sandbox {#delete-sandbox-program}

La suppression d’un programme d’environnement de test supprime tous les environnements et pipelines qui y sont associés.

>[!TIP]
>
>Les utilisateurs avec des rôles de **Propriétaire de l’entreprise** ou **Responsable du déploiement** peuvent également supprimer leurs environnements de production et d’évaluation plutôt que l’ensemble du programme Sandbox.

Pour supprimer un programme sandbox, procédez comme suit.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur le **[Mes programmes](#my-programs)** , cliquez sur le programme à modifier pour en afficher les détails.

1. Cliquez sur le nom de votre programme dans le coin supérieur gauche de la page, puis sélectionnez **Supprimer le programme**.

   ![Option Supprimer le programme](assets/delete-sandbox1.png)

Vous pouvez également cliquer sur le bouton représentant des points de suspension sur la vignette de votre programme dans la page de présentation de Cloud Manager et sélectionner **Supprimer le programme**.

![Supprimer Sandbox d’une vignette de programme](assets/delete-sandbox2.png)

>[!NOTE]
>
>Seuls les programmes Sandbox peuvent être supprimés. Les programmes de production ne peuvent pas être supprimés.
