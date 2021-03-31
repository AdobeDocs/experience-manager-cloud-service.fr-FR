---
title: 'Tâches de l''administrateur système '
description: Suivez cette page pour savoir comment ajouter des utilisateurs et les affecter à des rôles Cloud Manager en tant qu’administrateur système
translation-type: tm+mt
source-git-commit: f1f5766a41763634e0aaba44e55471ac2ea5dc8f
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---


# Tâches de l&#39;administrateur système {#add-users-assign}

Les administrateurs système gèrent tous les aspects de leurs utilisateurs, de l’accès aux autorisations. Cet utilisateur est la première personne à avoir accès à des tâches d’exécution de début dans Admin Console et Cloud Manager.
Un administrateur système effectue les tâches d&#39;organisation suivantes :

* Ajouter des utilisateurs
* Affectation d’utilisateurs aux rôles et autorisations de Cloud Manager

## Ajouter des utilisateurs {#add-users}

>[!NOTE]
>Pour ajouter un utilisateur, vous devez être administrateur système.

1. Si vous êtes administrateur système, accédez au [Admin Console](https://adminconsole.adobe.com). Vous pouvez également accéder à Cloud Manager où vous verrez le bouton **Gérer l’accès**, comme décrit ci-dessous.

1. Cliquez sur le bouton **Gérer l’accès**, situé en haut à droite du landing page Cloud Manager, pour ouvrir le Admin Console dans un nouvel onglet.

   ![](/help/onboarding/getting-access-to-aem-in-cloud/assets/sys-admin5.png)

   À partir du **Admin Console**, vous pouvez ajouter des utilisateurs à Cloud Manager et les affecter à des rôles, appelés Profils de produits dans le Admin Console.

1. Sélectionnez **Adobe Experience Manager en tant que Cloud Service** dans la carte **Produits et services**, comme indiqué ci-dessous.

   ![](/help/onboarding/what-is-required/assets/admin-console-1.png)

1. Sélectionnez l&#39;onglet **Utilisateurs** dans la barre d&#39;actions, puis sélectionnez **Ajouter l&#39;utilisateur**.

   ![](/help/onboarding/what-is-required/assets/admin-console-2.png)

1. Sélectionnez l’utilisateur et affectez à l’utilisateur les rôles ou Profils de produits Cloud Manager appropriés, comme indiqué ci-dessous.

   ![](/help/onboarding/what-is-required/assets/admin-console-3.png)

   >[!NOTE]
   >Reportez-vous aux sections précédentes, [Rôles utilisateur et autorisations](#user-roles) et [Permissions associées aux définitions de rôles](#permissions) pour vous assurer que les bons utilisateurs se voient attribuer le ou les rôles appropriés dans le **Admin Console**.

   Vous avez maintenant ajouté des utilisateurs à Adobe Experience Manager en tant que contexte de produit Cloud Service et vous avez configuré les rôles ou Profils de produits appropriés.

   Par exemple, si vous êtes dans le rôle d’un :

   * ***Propriétaire*** d&#39;entreprise, vous avez l&#39;autorisation d&#39;Ajouter un nouveau programme ou de modifier un programme, d&#39;ajouter ou de mettre à jour un environnement, d&#39;ajouter/modifier/supprimer le pipeline et d&#39;exécuter un pipeline, et de déployer le code pour AEM qualité d&#39;environnement ou de code.

   * ***Deployment Manager*** vous permet d’ajouter ou de mettre à jour un environnement, d’exécuter tout pipeline et de déployer le code dans AEM environnement ou qualité du code.

   * ***Développeur***, vous avez l&#39;autorisation de générer un Jeton d&#39;accès personnel pour accéder à Git.

      >[!NOTE]
      > Un utilisateur peut être affecté à plusieurs rôles. Par exemple, l’attribution des rôles Business Owner et Deployment Manager à un utilisateur leur donne la combinaison ou la somme de ces autorisations.
