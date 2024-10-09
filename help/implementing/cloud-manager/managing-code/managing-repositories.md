---
title: Gérer les référentiels dans Cloud Manager
description: Découvrez comment ajouter, afficher et supprimer vos référentiels Git dans Cloud Manager.
exl-id: 6e1cf636-78f5-4270-9a21-38b4d5e5a0b0
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 9cde6e63ec452161dbeb1e1bfb10c75f89e2692c
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 86%

---


# Gérer les référentiels dans Cloud Manager {#managing-repos}

Découvrez comment afficher, ajouter et supprimer vos référentiels Git dans Cloud Manager.

## À propos des référentiels dans Cloud Manager {#overview}

Les référentiels de Cloud Manager servent à stocker et gérer le code de votre projet à l’aide de Git. Pour chaque *programme* que vous ajoutez, un référentiel géré par Adobe est automatiquement créé.

En outre, vous avez la possibilité de créer d’autres référentiels gérés par Adobe ou d’ajouter vos propres référentiels privés. Tous les référentiels associés à votre programme peuvent être consultés sur la page **Référentiels**.

Les référentiels créés dans Cloud Manager peuvent également être sélectionnés lors de l’ajout ou de la modification de pipelines. Pour plus d’informations sur la configuration des pipelines, voir [Pipelines CI-CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md).

Chaque pipeline est lié à un référentiel ou à une branche principale. Toutefois, grâce à la [prise en charge des sous-modules Git](git-submodules.md), de nombreuses branches secondaires peuvent être incluses au moment de la création.

## Afficher la page Référentiels {#repositories-window}

Dans la page **Référentiels**, vous pouvez afficher des détails sur le référentiel sélectionné. Ces informations incluent le type de référentiel en cours d’utilisation. Si le référentiel est marqué comme **Adobe**, il s’agit d’un référentiel géré par Adobe. S’il est étiqueté **GitHub**, il s’agit d’un référentiel GitHub privé que vous gérez. En outre, la page fournit des détails tels que le moment où le référentiel a été créé et les pipelines qui lui sont associés.

Pour agir sur un référentiel sélectionné, vous pouvez cliquer sur le référentiel et utiliser l’![Icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) pour ouvrir un menu déroulant. Pour les référentiels gérés par Adobe, vous pouvez **[Vérifier les branches / Créer un projet](#check-branches)**.

![Actions du référentiel](assets/repository-actions.png)
*Menu déroulant sur la page Référentiels.*

Parmi les autres actions disponibles dans le menu déroulant, citons notamment **[Copier l’URL du référentiel](#copy-url)**, **[Afficher et mettre à jour](#view-update)** et **[Supprimer](#delete)** le référentiel.

**Pour afficher la page Référentiels :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Sur la page **Aperçu du programme**, dans le menu latéral, cliquez sur l’![Icône Dossier](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg), **Référentiels**.

1. La page **Référentiels** affiche tous les référentiels associés à votre programme sélectionné.

   ![Page Référentiels](assets/repositories.png)
   *Page Référentiels dans Cloud Manager.*

## Ajouter un référentiel {#adding-repositories}

Un utilisateur ou une utilisatrice doit disposer du rôle **Responsable de déploiement** ou **Propriétaire de l’entreprise** pour ajouter un référentiel.

Sur la page **Référentiels**, près du coin supérieur droit, cliquez sur **Ajouter un référentiel**.

![Boîte de dialogue Ajouter un référentiel](assets/repository-add.png)
*Boîte de dialogue Ajouter un référentiel.*

Cloud Manager prend en charge deux types de référentiels : les référentiels gérés par Adobe (**Référentiel Adobe**) et les référentiels auto-gérés (**Référentiel privé**). Les champs requis pour le paramétrage varient en fonction du type de référentiel que vous choisissez d’ajouter. Pour plus d’informations, consultez les sections suivantes :

* [Ajouter des référentiels Adobe dans Cloud Manager](adobe-repositories.md)
* [Ajouter des référentiels privés dans Cloud Manager](private-repositories.md)

Les référentiels sont limités à 300 pour tous les programmes d’une société ou d’une organisation IMS donnée.

## Accéder aux informations du référentiel {#repo-info}

Lorsque vous consultez vos référentiels dans la fenêtre **Référentiels**, vous pouvez consulter des informations sur la façon d’accéder aux référentiels gérés par Adobe par programmation, en cliquant sur le bouton **Accéder aux informations sur le référentiel** dans la barre d’outils.

![Informations sur le référentiel](assets/repository-access-repo-info2.png)

La fenêtre **Informations sur le référentiel** s’ouvre et affiche les détails. Pour plus d’informations sur l’accès aux informations du référentiel, voir la section [Accéder aux informations du référentiel](/help/implementing/cloud-manager/managing-code/accessing-repos.md).

## Vérifier les branches / Créer un projet {#check-branches}

Dans **AEM Cloud Manager**, l’action **Vérifier les branches / Créer un projet** a deux objectifs, selon l’état actuel du référentiel.

* Si le référentiel est nouvellement créé, l’action génère un exemple de projet basé sur l’[archétype de projet AEM](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/developing/archetype/overview).
* Si l’exemple de projet est déjà créé dans le référentiel, l’action vérifie le statut du référentiel et de ses branches, en indiquant si l’exemple de projet existe déjà.

  ![Action Vérifier les branches](assets/check-branches.png)

## Copier l’URL du référentiel {#copy-url}

L’action **Copier l’URL du référentiel** copie l’URL du référentiel sélectionné à la page **Référentiels** vers le Presse-papiers afin d’utiliser cette URL ailleurs.

## Afficher et mettre à jour un référentiel {#view-update}

L’action **Afficher et mettre à jour** ouvre la boîte de dialogue **Mettre à jour le référentiel**, dans laquelle vous pouvez afficher le **Nom** et l’**aperçu de l’URL du référentiel**. En outre, elle permet de mettre à jour la **description** du référentiel.

![Afficher et mettre à jour les informations du référentiel](assets/repository-view-update.png)

## Supprimer un référentiel {#delete}

L’action **Supprimer** supprime le référentiel de votre projet. Un référentiel ne peut pas être supprimé s’il est associé à un pipeline.

![Supprimer](assets/repository-delete.png)

La suppression d’un référentiel rend son nom inutilisable pour tout nouveau référentiel créé ultérieurement. Si vous tentez d’ajouter un référentiel portant le même nom qu’un référentiel supprimé, le message d’erreur suivant s’affiche :

`Repository name should be unique within organization.`

En outre, le référentiel supprimé n’est plus disponible dans Cloud Manager et ne peut être lié à aucun pipeline.

