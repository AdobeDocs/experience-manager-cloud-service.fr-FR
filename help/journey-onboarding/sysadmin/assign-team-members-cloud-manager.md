---
title: Affectation de membres de l’équipe à des profils de produit Cloud Manager
description: Consultez cette page pour savoir comment affecter des membres de l’équipe à des profils de produit Cloud Manager
feature: Onboarding
role: Admin, User, Developer
exl-id: 555688e5-f937-462c-9fcc-b90685f1882b
source-git-commit: 22a08a0cb80052485309ce3d33537e9fe303c6f5
workflow-type: ht
source-wordcount: '1154'
ht-degree: 100%

---

# Affectation de membres de l’équipe à des profils de produit Cloud Manager {#assign-team-members}

Dans l’étape précédente de ce parcours, [Prise en main du processus d’intégration](/help/journey-onboarding/sysadmin/get-started-onboarding-journey.md), vous avez maintenant appris à vous connecter à l’Admin Console et à afficher vos privilèges en tant qu’administrateur système. Vous êtes maintenant prêt à affecter des membres de l’équipe aux profils de produit Cloud Manager.

## Objectif {#objective}

Ce document résume la manière d’affecter des membres de l’équipe à des profils de produit Cloud Manager à partir d’Adobe Admin Console. Une fois affectés, ces membres peuvent alors créer des ressources d’accès cloud comme décrit dans l’étape suivante de ce parcours.

Après avoir lu cette section, vous devriez être en mesure de :

* Comprenez pourquoi et comment ajouter des membres de l’équipe.
* Découvrez trois profils majeurs de produit Cloud Manager : **Propriétaire d’entreprise**, **Responsable de déploiement** et **Développeur**.
* Affectez des membres d’équipe à des profils de produit Cloud Manager.

>[!TIP]
>
>Dans le cadre de l’intégration, Adobe vous recommande d’ajouter initialement des utilisateurs qui participeront aux tâches immédiates, tels que les administrateurs, les développeurs et les auteurs de contenu. Vous pouvez poursuivre le processus d’intégration sans avoir besoin d’ajouter tous les utilisateurs. Une fois l’intégration terminée, vous pouvez ajouter d’autres utilisateurs.

## Conditions préalables {#prerequisites}

Les prérequis suivants doivent être satisfaits avant de commencer cette section. Vous devez :

* être administrateur système et comprendre les profils de produit Cloud Manager ;
   * Revenez à l’[Aperçu du parcours d’intégration](onboarding-journey-overview.md) si vous ne connaissez pas ces concepts.
* comprendre les bases d’Adobe Admin Console ;
   * Revenez à l’[Aperçu du parcours d’intégration](onboarding-journey-overview.md) si vous ne connaissez pas ces concepts.
* disposer des informations sur les membres de votre équipe qui devront accéder à AEM as a Cloud Service, parmi lesquels
   * leur nom ;
   * leur adresse e-mail ;
   * leurs rôles et responsabilités.

## Vérification des profils de produit Cloud Manager {#review-product-profiles}

Dans Adobe Admin Console, vous pouvez voir la liste des profils Cloud Manager.

1. Connectez-vous à Adobe Admin Console à l’adresse [adminconsole.adobe.com](https://adminconsole.adobe.com/) et depuis la page **Aperçu**, sélectionnez **Adobe Experience Manager as a Cloud Service** dans la carte **Produits et services**.

   ![AEM en tant que produit](/help/journey-onboarding/assets/assign-team1.png)

1. Accédez à l’instance **Cloud Manager** à partir de la liste de toutes les instances.

   ![Cloud Manager](/help/journey-onboarding/assets/assign-team2.png)

1. La liste des profils de produits Cloud Manager préconfigurés s’affiche.

   ![Profils de produits](/help/journey-onboarding/assets/assign-team3.png)

## Affectation d’utilisateurs au profil de produit Propriétaire de l’entreprise {#assign-users-business-owner}

Vous êtes maintenant prêt à ajouter des utilisateurs et à les affecter au profil de produit **Propriétaire d’entreprise**.

1. Identifiez le ou les utilisateurs qui géreront les programmes Cloud Manager et ajoutez-les au profil de produit Propriétaire de l’entreprise.

1. Connectez-vous à Admin Console à l’adresse [adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview) et dans la page **Aperçu**, sélectionnez le produit **Adobe Experience Manager as a Cloud Service** à partir de la carte **Produits et services**.

   ![Produits et services](/help/journey-onboarding/assets/assign-team1.png)

1. Sélectionnez l’onglet **Utilisateurs** dans la barre de navigation supérieure, puis sélectionnez **Ajouter un utilisateur**.

   ![Ajouter un utilisateur](/help/journey-onboarding/assets/assign-team4.png)

1. Dans la boîte de dialogue **Ajouter des utilisateurs à votre équipe**, entrez l’adresse e-mail de l’utilisateur que vous souhaitez ajouter.

   * Si l’identifiant fédéré des membres de votre équipe n’a pas encore été configuré, sélectionnez **Adobe ID** pour le **Type d’ID**.

   ![Ajout des détails utilisateur](/help/journey-onboarding/assets/assign-team5.png)

1. Cliquez sur le bouton Plus sous l’en-tête **Sélection de produits ou de groupes d’utilisateurs** pour commencer la sélection de produits, sélectionnez **Adobe Experience Manager as a Cloud Service** et affectez le profil de produit **Propriétaire de l’entreprise** à l’utilisateur.

   * Affectez chaque utilisateur à au moins un profil de produit afin qu’il puisse accéder à Cloud Manager.
   * N’oubliez pas de vous affecter en tant qu’administrateur système au rôle **Propriétaire d’entreprise**.

   ![Assignation des utilisateurs](/help/journey-onboarding/assets/assign-team6.png)

1. Cliquez sur **Enregistrer** et un e-mail de bienvenue est envoyé à l’utilisateur que vous avez ajouté. L’utilisateur invité peut accéder à Cloud Manager en cliquant sur le lien contenu dans l’e-mail de bienvenue et en se connectant à l’aide d’un Adobe ID.

1. Répétez ces étapes pour les utilisateurs de votre équipe.

Votre équipe Cloud Manager fraîchement formée (y compris vous en tant que **Propriétaire d’entreprise**) a été configurée. En tant que **Propriétaire d’entreprise** vous n’êtes qu’à une étape de la connexion à Cloud Manager et de l’activation de la création de vos ressources cloud.

## Affectation d’utilisateurs au profil de produit Gestionnaire de déploiement {#assign-users-deployment-manager}

1. Identifiez le ou les utilisateurs qui géreront les programmes Cloud Manager et ajoutez-les au profil de produit Gestionnaire de déploiement.

1. Connectez-vous à Admin Console à l’adresse [adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview) et dans la page **Aperçu** et sélectionnez le produit **Adobe Experience Manager as a Cloud Service** dans la carte **Produits et services**.

   ![Produits et services](/help/journey-onboarding/assets/assign-team1.png)

1. Sélectionnez l’onglet **Utilisateurs** dans la barre de navigation supérieure, puis sélectionnez **Ajouter un utilisateur**.

   ![Ajouter un utilisateur](/help/journey-onboarding/assets/assign-team4.png)

1. Dans la boîte de dialogue **Ajouter des utilisateurs à votre équipe**, entrez l’adresse e-mail de l’utilisateur que vous souhaitez ajouter.

   * Si l’identifiant fédéré des membres de votre équipe n’a pas encore été configuré, sélectionnez **Adobe ID** pour le **Type d’ID**.

   ![Saisie de l’ID](/help/journey-onboarding/assets/assign-team5.png)

1. Cliquez sur le bouton Plus sous l’en-tête **Sélection de produits ou de groupes d’utilisateurs** pour commencer la sélection de produit et sélectionnez **Adobe Experience Manager as a Cloud Service** et affecter le profil de produit **Gestionnaire de déploiement** à l’utilisateur.

   ![Attribution d’un profil](/help/journey-onboarding/assets/assign-team6.png).

## Affectation d’utilisateurs au profil de produit Développeur {#assign-users-developer}

1. Identifiez le ou les utilisateurs qui géreront les programmes Cloud Manager.

1. Connectez-vous à Admin Console à l’adresse [adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview) et dans la page **Aperçu** et sélectionnez le produit **Adobe Experience Manager as a Cloud Service** dans la carte **Produits et services**.

   ![Produits et services](/help/journey-onboarding/assets/assign-team1.png)

1. Sélectionnez l’onglet **Utilisateurs** dans la barre de navigation supérieure, puis sélectionnez **Ajouter un utilisateur**.

   ![Ajouter un utilisateur](/help/journey-onboarding/assets/assign-team4.png)

1. Dans la boîte de dialogue **Ajouter des utilisateurs à votre équipe**, saisissez l’adresse e-mail de l’utilisateur que vous souhaitez ajouter.

   * Si l’identifiant fédéré des membres de votre équipe n’a pas encore été configuré, sélectionnez **Adobe ID** pour le **Type d’ID**.

   ![Ajout d’un ID d’utilisateur](/help/journey-onboarding/assets/assign-team5.png)

1. Cliquez sur le bouton Plus sous l’en-tête **Sélection de produits ou de groupes d’utilisateurs** pour commencer la sélection de produit et sélectionnez **Adobe Experience Manager as a Cloud Service** et affecter le profil de produit **Développeur** à l’utilisateur.

   ![Attribution d’un profil](/help/journey-onboarding/assets/assign-team6.png).

## Prochaines étapes {#whats-next}

Cette partie du parcours d’intégration vous a permis d’en savoir plus sur l’affectation de membres de votre équipe à des rôles dans l’Admin Console. Vous devez maintenant :

* savoir pourquoi et comment ajouter des membres de l’équipe ;
* comprendre les trois principaux profils de produit Cloud Manager : **Propriétaire d’entreprise**, **Responsable de déploiement** et **Développeur**.
* pouvoir affecter des membres de l’équipe aux profils de produits Cloud Manager.

Vous êtes maintenant prêt à poursuivre votre parcours d’intégration en consultant le document [Configuration de ressources Cloud via Cloud Manager](/help/journey-onboarding/sysadmin/setup-cloud-resources-via-cloud-manager.md), où vous apprendrez :

1. Pour que d’autres propriétaires d’entreprise puissent créer des programmes, vous, en tant qu’administrateur système disposant du rôle **Propriétaire d’entreprise**, devez d’abord accéder à Cloud Manager et vous connecter.
1. Comment un utilisateur disposant du rôle **Propriétaire d’entreprise** peut se connecter et configurer vos ressources cloud, y compris votre programme cloud et vos environnements.
1. Comment les utilisateurs dotés des rôles **Développeur** et **Responsable de déploiement** peuvent accéder à Cloud Manager.

## Ressources supplémentaires {#additional-resources}

Il est recommandé de continuer votre parcours d’intégration comme décrit précédemment. Voici quelques ressources supplémentaires si vous souhaitez approfondir un sujet particulier de ce parcours.

* [Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html?lang=fr)
* [Profils de produit Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=fr#cloud-manager-product-profiles)
* [Aperçu de l’identité Admin Console](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/identity.ug.html)
