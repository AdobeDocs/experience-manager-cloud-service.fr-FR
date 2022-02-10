---
title: Affectation de membres de l’équipe à des profils de produit Cloud Manager
description: Consultez cette page pour savoir comment affecter des membres de l’équipe à des profils de produit Cloud Manager
feature: Onboarding
role: Admin, User, Developer
exl-id: 555688e5-f937-462c-9fcc-b90685f1882b
source-git-commit: 22a08a0cb80052485309ce3d33537e9fe303c6f5
workflow-type: tm+mt
source-wordcount: '1154'
ht-degree: 25%

---

# Affectation de membres de l’équipe à des profils de produit Cloud Manager {#assign-team-members}

Dans l&#39;étape précédente de ce parcours, [Prise en main du processus d’intégration](/help/journey-onboarding/sysadmin/get-started-onboarding-journey.md), vous avez maintenant appris à vous connecter au Admin Console et à afficher vos privilèges en tant qu’administrateur système. Vous êtes maintenant prêt à affecter des membres de l’équipe aux profils de produit Cloud Manager.

## Objectif {#objective}

Ce document résume la manière d’affecter des membres de l’équipe à des profils de produit Cloud Manager à partir d’Adobe Admin Console. Une fois affectés, ces membres peuvent alors créer des ressources cloud d’accès comme décrit à l’étape suivante de ce parcours.

Après avoir lu cette section, vous devriez être en mesure de :

* Comprenez pourquoi et comment ajouter des membres de l’équipe.
* Découvrez les trois profils de produit Cloud Manager importants : **Propriétaire de l’entreprise**, **Responsable de déploiement**, et **Développeur**.
* Affectez des membres de l’équipe à des profils de produit Cloud Manager.

>[!TIP]
>
>Dans le cadre de l’intégration, Adobe vous recommande d’ajouter initialement des utilisateurs qui participeront aux tâches immédiates, tels que les administrateurs, les développeurs et les auteurs de contenu. Vous pouvez poursuivre le processus d’intégration sans ajouter tous les utilisateurs. Une fois l’intégration terminée, vous pouvez ajouter d’autres utilisateurs.

## Prérequis {#prerequisites}

Les conditions préalables suivantes doivent être remplies avant de commencer cette section. Vous devez :

* Être administrateur système et comprendre les profils de produits Cloud Manager.
   * Revenez au [Présentation du Parcours d’intégration](onboarding-journey-overview.md) si vous ne connaissez pas ces concepts.
* comprendre les bases d’Adobe Admin Console ;
   * Revenez au [Présentation du Parcours d’intégration](onboarding-journey-overview.md) si vous ne connaissez pas ces concepts.
* Posséder des informations sur les membres de votre équipe, qui devront accéder à AEM as a Cloud Service, y compris
   * Noms
   * Adresses email
   * Rôles et responsabilités

## Vérification des profils de produit Cloud Manager {#review-product-profiles}

Dans Adobe Admin Console, vous pouvez voir la liste des profils Cloud Manager.

1. Connectez-vous à Adobe Admin Console à l’adresse [adminconsole.adobe.com](https://adminconsole.adobe.com/) et depuis le **Présentation** page, sélectionnez **Adobe Experience Manager as a Cloud Service** de la **Produits et services** carte.

   ![AEM en tant que produit](/help/journey-onboarding/assets/assign-team1.png)

1. Accédez à l’instance **Cloud Manager** à partir de la liste de toutes les instances.

   ![Cloud Manager](/help/journey-onboarding/assets/assign-team2.png)

1. La liste des profils de produits Cloud Manager préconfigurés s’affiche.

   ![Profils de produit](/help/journey-onboarding/assets/assign-team3.png)

## Affectation d’utilisateurs au profil de produit Propriétaire de l’entreprise {#assign-users-business-owner}

Vous êtes maintenant prêt à ajouter des utilisateurs et à les affecter à la variable **Propriétaire de l’entreprise** profil de produit.

1. Identifiez le ou les utilisateurs qui géreront les programmes Cloud Manager et ajoutez-les au profil de produit Propriétaire de l’entreprise.

1. Connectez-vous au Admin Console à l’adresse [adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview) et sur le **Présentation** page, sélectionnez **Adobe Experience Manager as a Cloud Service** produit à partir de **Produits et services** carte.

   ![Produits et services](/help/journey-onboarding/assets/assign-team1.png)

1. Sélectionnez l’onglet **Utilisateurs** dans la barre de navigation supérieure, puis sélectionnez **Ajouter un utilisateur**.

   ![Ajouter un utilisateur](/help/journey-onboarding/assets/assign-team4.png)

1. Dans le **Ajout d’utilisateurs à votre équipe** , saisissez l’e-mail de l’utilisateur que vous souhaitez ajouter.

   * Si l’identifiant fédéré des membres de votre équipe n’a pas encore été configuré, sélectionnez **Adobe ID** pour le **Type d’ID**.

   ![Ajout des détails utilisateur](/help/journey-onboarding/assets/assign-team5.png)

1. Cliquez sur le bouton Plus sous la **Sélection de produits ou de groupes d’utilisateurs** en-tête pour commencer la sélection de produit et sélectionnez **Adobe Experience Manager as a Cloud Service** et affecter **Propriétaire de l’entreprise** profil de produit à l’utilisateur.

   * Affectez chaque utilisateur à au moins un profil de produit afin qu’il puisse accéder à Cloud Manager.
   * N’oubliez pas de vous affecter en tant qu’administrateur système au **Propriétaire de l’entreprise** rôle.

   ![Attribution d’utilisateurs](/help/journey-onboarding/assets/assign-team6.png)

1. Cliquez sur **Enregistrer** et un e-mail de bienvenue est envoyé à l’utilisateur que vous avez ajouté. L’utilisateur invité peut accéder à Cloud Manager en cliquant sur le lien contenu dans l’e-mail de bienvenue et en se connectant à l’aide d’un Adobe ID.

1. Répétez ces étapes pour les utilisateurs de votre équipe.

Votre nouvelle équipe Cloud Manager (y compris vous-même affecté à la **Propriétaire de l’entreprise** ) a été configuré. Dans le rôle de **Propriétaire de l’entreprise**, vous n’êtes qu’à une étape de la connexion à Cloud Manager et de l’activation de la création de vos ressources cloud.

## Affectation d’utilisateurs au profil de produit Gestionnaire de déploiement {#assign-users-deployment-manager}

1. Identifiez le ou les utilisateurs qui géreront les programmes Cloud Manager et ajoutez-les au profil de produit Gestionnaire de déploiement.

1. Connectez-vous au Admin Console à l’adresse [adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview) et sur le **Présentation** page select **Adobe Experience Manager as a Cloud Service** du produit **Produits et services** carte.

   ![Produits et services](/help/journey-onboarding/assets/assign-team1.png)

1. Sélectionnez la **Utilisateurs** dans le volet de navigation supérieur, puis sélectionnez **Ajouter un utilisateur**.

   ![Ajouter un utilisateur](/help/journey-onboarding/assets/assign-team4.png)

1. Dans le **Ajout d’utilisateurs à votre équipe** , saisissez l’e-mail de l’utilisateur que vous souhaitez ajouter.

   * Si l’identifiant fédéré des membres de votre équipe n’a pas encore été configuré, sélectionnez **Adobe ID** pour le **Type d’ID**.

   ![Saisir l’ID](/help/journey-onboarding/assets/assign-team5.png)

1. Cliquez sur le bouton Plus sous la **Sélection de produits ou de groupes d’utilisateurs** en-tête pour commencer la sélection de produit et sélectionnez **Adobe Experience Manager as a Cloud Service** et affecter **Responsable de déploiement** profil de produit à l’utilisateur.

   ![Attribution d’un profil](/help/journey-onboarding/assets/assign-team6.png).

## Affectation d’utilisateurs au profil de produit Développeur {#assign-users-developer}

1. Identifiez le ou les utilisateurs qui géreront les programmes Cloud Manager.

1. Connectez-vous au Admin Console à l’adresse [adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview) et sur le **Présentation** page select **Adobe Experience Manager as a Cloud Service** du produit **Produits et services** carte.

   ![Produits et services](/help/journey-onboarding/assets/assign-team1.png)

1. Sélectionnez la **Utilisateurs** dans le volet de navigation supérieur, puis sélectionnez **Ajouter un utilisateur**.

   ![Ajouter un utilisateur](/help/journey-onboarding/assets/assign-team4.png)

1. Dans **Ajout d’utilisateurs à votre équipe** , saisissez l’e-mail de l’utilisateur que vous souhaitez ajouter.

   * Si l’identifiant fédéré des membres de votre équipe n’a pas encore été configuré, sélectionnez **Adobe ID** pour le **Type d’ID**.

   ![Ajout d’un ID d’utilisateur](/help/journey-onboarding/assets/assign-team5.png)

1. Cliquez sur le bouton Plus sous la **Sélection de produits ou de groupes d’utilisateurs** en-tête pour commencer la sélection de produit et sélectionnez **Adobe Experience Manager as a Cloud Service** et affecter **Développeur** profil de produit à l’utilisateur.

   ![Attribution d’un profil](/help/journey-onboarding/assets/assign-team6.png).

## Et après ? {#whats-next}

Dans cette partie du parcours d’intégration, vous en savez plus sur l’affectation de membres de votre équipe à des rôles dans le Admin Console. Vous devez maintenant :

* Comprenez pourquoi et comment ajouter des membres de l’équipe.
* Comprendre trois profils de produit Cloud Manager importants : **Propriétaire de l’entreprise**, **Responsable de déploiement**, et **Développeur**.
* Vous pouvez affecter des membres de l’équipe aux profils de produits Cloud Manager.

Vous êtes maintenant prêt à poursuivre votre parcours d’intégration en consultant le document [Configuration de ressources Cloud via Cloud Manager](/help/journey-onboarding/sysadmin/setup-cloud-resources-via-cloud-manager.md), où vous apprendrez :

1. Pour que d’autres propriétaires d’entreprise créent des programmes, vous, en tant qu’administrateur système affecté au **Propriétaire de l’entreprise** , vous devez d’abord accéder à Cloud Manager et vous connecter.
1. Comment un utilisateur utilise la variable **Propriétaire de l’entreprise** Le rôle peut se connecter et configurer vos ressources cloud, y compris votre programme cloud et vos environnements.
1. Comment les utilisateurs de la variable **Développeur** et **Responsable de déploiement** peuvent accéder à Cloud Manager.

## Ressources supplémentaires {#additional-resources}

Il est recommandé de continuer sur le parcours d’intégration comme décrit précédemment. Voici quelques ressources supplémentaires si vous souhaitez approfondir un sujet particulier de ce parcours.

* [Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html?lang=fr)
* [Profils de produit Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=fr#cloud-manager-product-profiles)
* [Présentation de l’identité Admin Console](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/identity.ug.html)
