---
title: Informations d’accès au référentiel
description: Découvrez comment accéder à vos référentiels Git gérés par l’Adobe et les gérer à l’aide de la gestion de compte Git en libre-service à partir de Cloud Manager.
exl-id: 0c0671a3-e400-46f3-ad86-166a6cfdd44b
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 0b39fc4dcaf86d436547d3941b1f12bca8c5bc9b
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 14%

---


# Informations d’accès au référentiel {#accessing-repos}

Découvrez comment accéder à vos référentiels Git gérés par l’Adobe et les gérer à l’aide de la gestion de compte Git en libre-service à partir de Cloud Manager.

## Accès aux informations du référentiel à partir de la page Aperçu {#overview-page}

Cloud Manager facilite la récupération des informations d’accès au référentiel pour les référentiels gérés par Adobe à l’aide de la fonction **Accès aux informations sur le référentiel** est disponible en bonne place sur la carte de pipeline.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la carte **Pipelines** à partir de votre page **Aperçu du programme**.

   ![Bouton Accéder aux informations sur le référentiel de la vignette d’environnements](assets/pipelines-card.png)

1. Appuyez ou cliquez sur le bouton **Accès aux informations sur le référentiel** pour ouvrir le bouton **Informations sur le référentiel** dialog et view :

   * Le nom d’utilisateur Git.
   * Mot de passe Git.
   * L’URL vers le référentiel Git de Cloud Manager.
   * Commandes git préconfigurées pour ajouter rapidement une commande distante à votre code git repo et push.

   ![Fenêtre Informations sur le référentiel](assets/repository-info.png)

1. Pour accéder au mot de passe, un nouveau mot de passe doit être généré. Pour ce faire, appuyez ou cliquez sur l’icône **Générer un mot de passe** bouton .

1. Confirmez la génération du mot de passe dans le **Êtes-vous sûr...** en appuyant ou en cliquant sur **Générer un mot de passe**.

   ![Confirmer la génération du mot de passe](assets/confirm-password-generation.png)

1. Le mot de passe est généré et visible pour la copie dans la variable **Password** champ .

   * La génération d’un mot de passe invalide le mot de passe précédent.
   * Cloud Manager n’enregistre pas le mot de passe. Il vous appartient d’enregistrer ce mot de passe en toute sécurité.
   * Comme Cloud Manager n’enregistre pas le mot de passe, si vous le perdez, vous devez en régénérer un nouveau.

   ![Exemple de mot de passe généré](assets/generated-password.png)

À l’aide de ces informations d’identification, vous pouvez cloner une copie locale du référentiel, apporter des modifications à ce référentiel local et, une fois prêt, valider toute modification de code dans le référentiel de code distant dans Cloud Manager.

>[!NOTE]
>
>* L’option **Accéder aux informations sur le référentiel** est visible par les utilisateurs et utilisatrices possédant les rôles **Développeur** ou **Responsable de déploiement**.
>* La variable **Accès aux informations sur le référentiel** n’affiche que les informations d’accès au référentiel pour les référentiels gérés par Adobe. Accès aux informations relatives à [référentiels privés](private-repositories.md) n’est pas disponible dans Cloud Manager.

## Accès aux informations du référentiel à partir de la fenêtre Référentiels {#repositories-window}

Un **Accès aux informations sur le référentiel** est également disponible dans la barre d’outils de la fonction [**Référentiels** fenêtre.](managing-repositories.md) il affiche les mêmes informations sur l’accès aux référentiels gérés par Adobe.

## Révocation d’un mot de passe d’accès {#revoke-password}

Vous pouvez révoquer un mot de passe d’accès à tout moment. Pour ce faire, veuillez [créez un ticket d’assistance pour cette requête.](https://experienceleague.adobe.com/?support-solution=Experience+Manager&amp;support-tab=home#support)

Le ticket sera traité en priorité et doit être révoqué dans la journée.
