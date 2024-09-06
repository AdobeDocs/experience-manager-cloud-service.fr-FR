---
title: Gestion des référentiels dans Cloud Manager
description: Découvrez comment créer, afficher et supprimer vos référentiels Git dans Cloud Manager.
exl-id: 6e1cf636-78f5-4270-9a21-38b4d5e5a0b0
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5d6d3374f2dd95728b2d3ed0cf6fab4092f73568
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 92%

---


# Gestion des référentiels dans Cloud Manager {#managing-repos}

Découvrez comment créer, afficher et supprimer vos référentiels Git dans Cloud Manager.

## Vue d’ensemble {#overview}

Les référentiels servent à stocker et gérer le code de votre projet à l’aide de Git. Chaque programme que vous créez dans Cloud Manager dispose d’un référentiel géré par Adobe créé pour lui.

Vous pouvez choisir de créer d’autres référentiels gérés par Adobe ainsi que d’ajouter vos propres référentiels privés. Tous les référentiels associés à votre programme peuvent être consultés dans la fenêtre **Référentiels**.

Vous pouvez également sélectionner les référentiels créés dans Cloud Manager lors de l’ajout ou de la modification de pipelines. Consultez [Pipelines CI-CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) pour en savoir plus.

Il existe un référentiel principal unique ou une branche pour chaque pipeline donné. Grâce à la [prise en charge des sous-modules Git](git-submodules.md), de nombreuses branches secondaires peuvent être incluses lors de la création.

## Fenêtre Référentiels {#repositories-window}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Sur la page **Vue d’ensemble du programme**, cliquez sur l’onglet **Référentiels** pour accéder à la page **Référentiels**.

1. La fenêtre **Référentiels** affiche tous les référentiels associés à votre programme.

   ![Fenêtre Référentiels](assets/repositories.png)

La fenêtre **Référentiels** fournit des détails sur les référentiels :

* Le type de référentiel
   * **Adobe** indique les référentiels gérés par Adobe.
   * **GitHub** indique les référentiels GitHub privés que vous gérez.
* La date de création
* Les pipelines associés au référentiel

Vous pouvez sélectionner le référentiel dans la fenêtre et cliquer sur le bouton représentant des points de suspension pour agir sur le référentiel sélectionné.

* **[Vérifier les branches/Créer un projet](#check-branches)** (disponible uniquement pour les référentiels Adobe)
* **[Copier l’URL du référentiel](#copy-url)**
* **[Afficher et mettre à jour](#view-update)**
* **[Supprimer](#delete)**

![Actions du référentiel](assets/repository-actions.png)

## Ajouter des référentiels {#adding-repositories}

Appuyez ou cliquez sur le bouton **Ajouter un référentiel** dans la fenêtre **Référentiels** pour lancer l’assistant **Ajouter un référentiel**.

![Assistant Ajouter un référentiel](assets/add-repository-wizard.png)

Cloud Manager prend en charge les référentiels gérés par Adobe (**Référentiel Adobe**) ainsi que vos propres référentiels auto-gérés (**Référentiel privé**). Les champs requis varient en fonction du type de référentiel que vous choisissez d’ajouter. Pour plus d’informations, consultez les documents suivants.

* [Ajout de référentiels Adobe dans Cloud Manager](adobe-repositories.md)
* [Ajout de référentiels privés dans Cloud Manager](private-repositories.md)

>[!NOTE]
>
>* Un utilisateur ou une utilisatrice doit disposer du rôle **Responsable de déploiement** ou **Propriétaire de l’entreprise** pour pouvoir ajouter un référentiel.
>* Les référentiels sont limités à 300 pour tous les programmes d’une société ou d’une organisation IMS donnée.

## Accéder aux informations sur le référentiel {#repo-info}

Lors de l’affichage de vos référentiels dans la fenêtre **Référentiels**, vous pouvez afficher les détails sur la manière d’accéder par programmation aux référentiels gérés par Adobe en cliquant sur le bouton **Accéder aux informations sur les référents** dans la barre d’outils.

![Informations sur le référentiel](assets/repo-info.png)

La fenêtre **Informations sur le référentiel** s’ouvre et affiche les détails. Pour plus d’informations sur l’accès aux informations du référentiel, consultez le document [Accès aux informations du référentiel](accessing-repos.md).

## Vérifier les branches / Créer un projet {#check-branches}

L’action **Vérifier les branches / Créer un projet** exécute deux fonctions selon l’état du référentiel.

* Si le référentiel est nouvellement créé, l’action crée un exemple de projet basé sur [l’archétype de projet AEM](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/developing/archetype/overview).
* Si le référentiel a déjà créé l’exemple de projet, il vérifie l’état du référentiel et de ses branches et signale si l’exemple de projet existe déjà.

![Action Vérifier les branches](assets/check-branches.png)

## Copier l’URL du référentiel {#copy-url}

L’action **Copier l’URL du référentiel** copie l’URL du référentiel sélectionné dans la fenêtre **Référentiels** vers le Presse-papiers afin d’utiliser cette URL ailleurs.

## Afficher et mettre à jour {#view-update}

L’action **Afficher et mettre à jour** ouvre la boîte de dialogue **Mettre à jour le référentiel**. À l’aide de celle-ci, vous pouvez afficher le **Nom** et la **Prévisualisation de l’URL du référentiel** et mettre à jour la **Description** du référentiel.

![Afficher et mettre à jour les informations du référentiel](assets/view-update.png)

## Supprimer {#delete}

L’action **Supprimer** supprime le référentiel de votre projet. Un référentiel ne peut pas être supprimé s’il est associé à un pipeline.

![Supprimer](assets/delete.png)

La suppression d’un référentiel entraînera les éléments suivants :

* Le nom du référentiel supprimé sera inutilisable pour de nouveaux référentiels qui pourraient être créés ultérieurement.
   * Le message d’erreur `Repository name should be unique within organization.` s’affiche dans de tels cas.
* Le référentiel supprimé sera indisponible dans Cloud Manager et ne pourra donc pas être lié à un pipeline.
