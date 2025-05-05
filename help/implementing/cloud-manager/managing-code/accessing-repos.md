---
title: Informations d’accès au référentiel
description: Découvrez comment accéder à votre référentiel Git géré par Adobe et comment le gérer à l’aide de la gestion de compte Git en libre-service, à partir de Cloud Manager.
exl-id: 0c0671a3-e400-46f3-ad86-166a6cfdd44b
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f2364de6237ca9f0285815b581bcf3881488188d
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 44%

---


# Informations d’accès au référentiel {#accessing-repos}

Découvrez comment accéder à votre référentiel Git géré par Adobe et comment le gérer à l’aide de la gestion de compte Git en libre-service, à partir de Cloud Manager.

## Accès aux informations du référentiel à partir de la page Aperçu {#overview-page}

Cloud Manager facilite la récupération des informations d’accès au référentiel pour les référentiels gérés par l’Adobe à l’aide de l’option **Accéder à Repo Info** à partir de la carte **Pipelines**.

La boîte de dialogue **Repository Info** vous permet d’afficher les informations d’accès suivantes pour les référentiels gérés par Adobe :

* Le nom d’utilisateur ou d’utilisatrice Git.
* Le mot de passe Git.
* L’URL vers le référentiel Git de Cloud Manager.
* Des commandes Git préconfigurées pour ajouter rapidement un référentiel distant à votre référentiel Git et pour transférer du code.

![Fenêtre Informations sur le référentiel](assets/repository-info.png)

Les informations d’accès relatives aux [référentiels privés](private-repositories.md) ne sont pas disponibles dans Cloud Manager.

La fonction **Accéder aux informations sur le référentiel** est visible pour les utilisateurs disposant de rôles **Développeur** ou **Responsable de déploiement**.

**Pour accéder aux informations du référentiel à partir de la page Aperçu :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Sur la page **Aperçu du programme**, sous la carte **Pipelines**, cliquez sur **Accéder aux informations sur les référents**.

   ![Accéder à Repo Info sur la carte Pipeline](assets/pipelines-card.png)

1. Pour accéder au mot de passe, un nouveau mot de passe doit être généré. Dans la boîte de dialogue **Repository Info**, sélectionnez **Generate password**.

1. Dans la boîte de dialogue de confirmation, sélectionnez **Générer le mot de passe**.

   ![Confirmation de la génération du mot de passe](assets/confirm-generated-password.png)

1. À droite du champ **Mot de passe**, cliquez sur ![Icône Copier](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) pour copier le mot de passe dans le Presse-papiers.

   * La génération d’un mot de passe invalide le mot de passe précédent.
   * Cloud Manager n’enregistre pas le mot de passe. Il vous appartient d’enregistrer le mot de passe en toute sécurité.
   * Comme Cloud Manager n’enregistre pas le mot de passe, si vous le perdez, vous devez en régénérer un nouveau.

   ![Copier le mot de passe dans la boîte de dialogue Repository Info](/help/implementing/cloud-manager/managing-code/assets/repository-copy-password.png)

À l’aide de ces informations d’identification, vous pouvez cloner une copie locale du référentiel et apporter des modifications à ce référentiel local. Lorsque vous avez terminé, vous pouvez ensuite valider toutes les modifications du code vers le référentiel de code distant dans Cloud Manager.

## Accès aux informations du référentiel à partir de la page Référentiels {#repositories-window}

La fonction **Accéder à Repo Info** est également disponible sur la page [**Référentiels**](managing-repositories.md). Il affiche les mêmes informations sur l’accès aux référentiels gérés par Adobe.

## Révoquer un mot de passe d’accès {#revoke-password}

Vous pouvez révoquer un mot de passe d’accès à tout moment.

Pour ce faire, [créez un ticket d’assistance pour cette requête](https://experienceleague.adobe.com/fr?support-solution=Experience+Manager&amp;support-tab=home#support). Le ticket est traité avec une priorité élevée et est généralement révoqué dans la journée.
