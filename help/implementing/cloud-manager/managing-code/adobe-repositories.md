---
title: Ajout d’un référentiel d’Adobe dans Cloud Manager
description: Découvrez comment ajouter un référentiel géré par Adobe dans Cloud Manager.
exl-id: 6c32c4ae-f48d-4440-bfc2-cdc1a3d59599
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 533fa72b7610f671a24461073112b7fb798ce166
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 8%

---

# Ajout d’un référentiel d’Adobe dans Cloud Manager {#adobe-repositories}

Découvrez comment ajouter un référentiel géré par Adobe dans Cloud Manager.

La page **Référentiels** permet d’ajouter facilement des référentiels gérés par Adobe à un programme sélectionné.

**Pour ajouter un référentiel d’Adobe dans Cloud Manager :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée et le programme auquel vous souhaitez ajouter un référentiel géré par Adobe.

1. Sur la page **Aperçu du programme**, dans le menu latéral, cliquez sur l’onglet ![Icône Dossier](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **Référentiels** . pour passer à la page **Référentiels**.

1. Sur la page **Référentiels**, près du coin supérieur droit, cliquez sur **Ajouter un référentiel**.

   ![Bouton Ajouter un référentiel](assets/add-repository.png)

1. Dans la boîte de dialogue **Ajouter un référentiel**, assurez-vous que **Adobe Repository** est sélectionné comme type de référentiel.

1. Dans les champs de texte respectifs, saisissez ce qui suit :

   * **Nom du référentiel** : nom expressif de votre nouveau référentiel.
   * **Aperçu de l’URL du référentiel** - Vous n’avez pas besoin de saisir un chemin d’URL ni de modifier le chemin existant, car l’infrastructure est déjà en place et entièrement intégrée et gérée par Adobe.
   * **Description (facultatif)** - Description détaillée du référentiel.

   ![Boîte de dialogue Ajouter un référentiel](assets/add-adobe-repository.png)

1. Cliquez sur **Enregistrer**.
Votre nouveau référentiel est affiché dans le tableau de la page **Référentiels**.

Vous pouvez désormais associer un [pipeline CI/CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) ou le gérer dans la page [**Référentiels**](managing-repositories.md).

>[!TIP]
>
>Vous pouvez également ajouter des référentiels GitHub que vous gérez vous-même, en tant que [référentiels privés](private-repositories.md).
