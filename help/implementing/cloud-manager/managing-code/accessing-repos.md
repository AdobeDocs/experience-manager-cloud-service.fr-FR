---
title: Accéder aux référentiels
description: Découvrez comment accéder à votre référentiel Git et comment le gérer à l’aide de la gestion de compte Git en libre-service à partir de Cloud Manager.
exl-id: 0c0671a3-e400-46f3-ad86-166a6cfdd44b
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 85%

---


# Accéder aux référentiels {#accessing-repos}

Découvrez comment accéder à votre référentiel Git et comment le gérer à l’aide de la gestion de compte Git en libre-service à partir de Cloud Manager.

## Utiliser la gestion de compte Git en libre-service {#self-service-repos}

Cloud Manager facilite la récupération des informations de votre référentiel à l’aide du bouton **Accéder aux informations sur le référentiel** mis en évidence sur la vignette Pipeline.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la vignette **Pipelines** à partir de votre page **Aperçu du programme** et recherchez le bouton **Accéder aux informations sur le référentiel** pour accéder à votre référentiel Git et le gérer.

   ![Bouton Accéder aux informations sur le référentiel de la vignette d’environnements](/help/implementing/cloud-manager/assets/repos/access-repo1.png)

1. Cliquez sur le bouton **Afficher les informations sur le référentiel** pour ouvrir une boîte de dialogue affichant les éléments suivants :

   * L’URL vers le référentiel Git de Cloud Manager.
   * Le nom d’utilisateur Git.
   * Le mot de passe Git, dont la valeur s’affiche lorsqu’on clique sur le bouton **Générer un mot de passe**.

   ![Affichage des informations sur le référentiel](/help/implementing/cloud-manager/assets/repos/access-repo-create.png)

À l’aide de ces informations d’identification, l’utilisateur ou l’utilisatrice peut cloner une copie locale du référentiel et apporter des modifications à ce référentiel local. Une fois prêt, il peut valider toutes les modifications de code vers le référentiel de code distant de Cloud Manager.

L’option **Accéder aux informations sur le référentiel** est également disponible sur l’onglet du pipeline **Hors production** de la vignette **Pipelines**.

![Bouton Accéder aux informations sur le référentiel dans l’onglet hors production](/help/implementing/cloud-manager/assets/repos/access-repo-nonprod.png)

>[!NOTE]
>
>L’option **Accéder aux informations sur le référentiel** est visible par les utilisateurs et utilisatrices possédant les rôles **Développeur** ou **Responsable de déploiement**.

## Révocation d’un mot de passe d’accès {#revoke-password}

Vous pouvez révoquer un mot de passe d’accès à tout moment. Pour ce faire, veuillez [créez un ticket d’assistance pour cette requête.](https://experienceleague.adobe.com/?support-solution=Experience+Manager&amp;support-tab=home#support)

Le ticket sera traité en priorité et doit être révoqué dans la journée.
