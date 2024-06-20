---
title: Ajout de référentiels Adobe dans Cloud Manager
description: Découvrez comment créer des référentiels gérés par Adobe dans Cloud Manager.
exl-id: 6c32c4ae-f48d-4440-bfc2-cdc1a3d59599
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 100%

---

# Ajout de référentiels Adobe dans Cloud Manager {#adobe-repositories}

Découvrez comment créer des référentiels gérés par Adobe dans Cloud Manager.

## Ajout d’un référentiel géré par Adobe {#add-adobe-repository}

La fenêtre **Référentiels** facilite l’ajout de référentiels gérés par Adobe supplémentaires pour votre programme.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Sur la page **Vue d’ensemble du programme**, cliquez sur l’onglet **Référentiels** pour accéder à la page **Référentiels**.

1. Cliquez sur **Ajouter un référentiel** dans la barre d’outils.

   ![Bouton Ajouter un référentiel](assets/add-repository.png)

1. Saisissez le nom et la description demandés, puis cliquez sur **Enregistrer**.

   ![Boîte de dialogue Ajouter un référentiel](assets/add-adobe-repository.png)

Lorsque l’assistant se ferme, votre nouveau référentiel s’affiche dans le tableau dans la fenêtre **Référentiels**. Vous pouvez désormais associer un [Pipeline CI/CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) à celui-ci, ou le gérer dans la fenêtre [**Référentiels**.](managing-repositories.md)

>[!TIP]
>
>Vous pouvez également ajouter des référentiels GitHub que vous gérez vous-même, en tant que [référentiels privés.](private-repositories.md)
