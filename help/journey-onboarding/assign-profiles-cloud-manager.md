---
title: Affectation de membres de l’équipe à des profils de produit Cloud Manager
description: Consultez cette page pour savoir comment affecter des membres de l’équipe à des profils de produit Cloud Manager
feature: Onboarding
role: Admin, User, Developer
exl-id: 555688e5-f937-462c-9fcc-b90685f1882b
source-git-commit: 709a80683357b0d56280ff14aa5f4ba6bf2c6b23
workflow-type: tm+mt
source-wordcount: '1534'
ht-degree: 42%

---


# Affectation de membres de l’équipe à des profils de produit Cloud Manager {#assign-team-members}

Dans cette partie du [parcours d&#39;intégration,](overview.md) vous apprendrez comment affecter des membres de l’équipe à des profils de produit Cloud Manager.

## Objectif {#objective}

Dans l&#39;étape précédente de ce parcours, [Accéder au Admin Console,](admin-console.md) vous avez appris à vous connecter au Admin Console et à vérifier vos privilèges en tant qu’administrateur système. Vous êtes maintenant prêt à autoriser les membres de votre équipe à accéder à Cloud Manager. Pour ce faire, attribuez des profils de produit.

Lorsque vous accordez aux utilisateurs l’accès à une solution d’Adobe, vous ne souhaitez pas nécessairement leur accorder un accès complet. Les profils de produit permettent à chaque solution d’avoir son propre jeu d’autorisations utilisateur. Vous utilisez le Admin Console pour affecter des profils de produit.

La première étape consiste à accorder aux utilisateurs l’accès à Cloud Manager. Cloud Manager vous prend en charge avec les configurations de développement d’entreprise et ses pipelines CI/CD conçus spécifiquement, qui sont équipés pour garantir des tests approfondis et une qualité de code optimale pour offrir des expériences exceptionnelles.

Après avoir lu ce document, vous devriez :

* Comprendre les profils de produits.
* Découvrez Cloud Manager.
* Connaissez les trois profils de produits Cloud Manager importants : **Propriétaire de l’entreprise**, **Responsable de déploiement**, et **Développeur**.
* pouvoir affecter des membres de l’équipe aux profils de produits Cloud Manager.

## Prérequis {#prerequisites}

Pour affecter des membres de l’équipe à des profils de produit, vous devez disposer d’informations sur les membres de l’équipe, qui devront accéder à AEM as a Cloud Service, notamment :

* leur nom ;
* leur adresse e-mail ;
* leurs rôles et responsabilités.

>[!TIP]
>
>Dans le cadre de l’intégration, Adobe vous recommande d’ajouter initialement des utilisateurs qui participeront aux tâches immédiates, tels que les administrateurs, les développeurs et les auteurs de contenu.
>
>Vous pouvez poursuivre le processus d’intégration sans avoir besoin d’ajouter tous les utilisateurs. Une fois l’intégration terminée, vous pouvez ajouter d’autres utilisateurs.

## Profils de produit {#product-profiles}

Lorsque vous accordez aux utilisateurs l’accès à une solution d’Adobe, vous ne souhaitez pas nécessairement leur accorder un accès complet. Les profils de produit permettent à chaque solution d’avoir son propre jeu d’autorisations utilisateur définies à l’aide du Admin Console.

Par exemple, plus tard dans ce parcours, vous utiliserez le Admin Console pour accorder aux utilisateurs l’accès à la solution AEM en affectant des profils de produit aux administrateurs AEM et aux auteurs d’AEM.

Toutefois, l’étape suivante consiste à accorder des profils de produit pour que les membres de votre équipe aient d’abord accès à Cloud Manager.

## Cloud Manager {#cloud-manager}

En tant qu’administrateur système, vous savez qu’un projet as a Cloud Service réussi AEM dépend non seulement de la création de contenu étonnant à l’aide d’AEM, mais aussi du développement et du déploiement de votre propre code personnalisé et de vos applications pour diffuser votre contenu .

Cloud Manager fait partie intégrante d’AEM as a Cloud Service. Il permet de gérer vos pipelines CI/CD pour le déploiement du code, de gérer vos référentiels de code et de gérer vos environnements.

Avant que votre équipe ne puisse rien faire d’autre, ils doivent être intégrés à Cloud Manager en leur accordant les profils de produit nécessaires. Les étapes suivantes vous indiquent où trouver le profil de produit Cloud Manager à l’aide du Admin Console et comment les affecter aux membres de votre équipe.

## Vérification des profils de produit Cloud Manager {#review-product-profiles}

Le Admin Console vous permet d’afficher la liste des profils Cloud Manager.

1. Connectez-vous à Adobe Admin Console à l’adresse [adminconsole.adobe.com](https://adminconsole.adobe.com/) et depuis la page **Aperçu**, sélectionnez **Adobe Experience Manager as a Cloud Service** dans la carte **Produits et services**.

   ![AEM en tant que produit](/help/journey-onboarding/assets/assign-team1.png)

1. Accédez à l’instance **Cloud Manager** à partir de la liste de toutes les instances.

   ![Cloud Manager](/help/journey-onboarding/assets/assign-team2.png)

1. La liste des profils de produits Cloud Manager préconfigurés s’affiche.

   ![Profils de produits](/help/journey-onboarding/assets/assign-team3.png)

Les profils les plus importants à affecter dans le cadre du processus d’intégration initial sont les suivants :

* **Propriétaire de l’entreprise** - Ces utilisateurs gèrent différents programmes.
* **Responsable de déploiement** - Ces utilisateurs déploient le code de vos référentiels vers des environnements AEM en cours d’exécution.
* **Développeur** - Ces utilisateurs développent vos applications AEM personnalisées et valident le code dans vos référentiels.

Connaissant ces rôles et ce qu’ils font, consultez votre liste de membres de l’équipe pour déterminer qui a besoin de quel profil. Gardez à l’esprit que les utilisateurs peuvent avoir et ont souvent plusieurs rôles dans votre équipe et ont donc également besoin de plusieurs profils.

## Attribution du profil de produit du propriétaire de l’entreprise {#assign-business-owner}

Vous êtes maintenant prêt à ajouter des utilisateurs et à les affecter au profil de produit **Propriétaire d’entreprise**.

1. Identifiez le ou les utilisateurs qui doivent gérer les programmes Cloud Manager. Ce sera votre **Propriétaires d’entreprise**.

1. Connectez-vous à Admin Console à l’adresse `[adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview)` et dans la page **Aperçu**, sélectionnez le produit **Adobe Experience Manager as a Cloud Service** à partir de la carte **Produits et services**.

   ![Produits et services](/help/journey-onboarding/assets/assign-team1.png)

1. Sélectionnez l’onglet **Utilisateurs** dans la barre de navigation supérieure, puis sélectionnez **Ajouter un utilisateur**.

   ![Ajouter un utilisateur](/help/journey-onboarding/assets/assign-team4.png)

1. Dans la boîte de dialogue **Ajouter des utilisateurs à votre équipe**, entrez l’adresse e-mail de l’utilisateur que vous souhaitez ajouter.

   * Si l’identifiant fédéré des membres de votre équipe n’a pas encore été configuré, sélectionnez **Adobe ID** pour le **Type d’ID**.

   ![Ajout des détails utilisateur](/help/journey-onboarding/assets/assign-team5.png)

1. Cliquez sur le bouton Plus sous l’en-tête **Sélection de produits ou de groupes d’utilisateurs** pour commencer la sélection de produits, sélectionnez **Adobe Experience Manager as a Cloud Service** et affectez le profil de produit **Propriétaire de l’entreprise** à l’utilisateur.

   * Affectez chaque utilisateur à au moins un profil de produit afin qu’il puisse accéder à Cloud Manager.
   * N’oubliez pas de vous affecter en tant qu’administrateur système au **Propriétaire de l’entreprise** rôle.

   ![Assignation des utilisateurs](/help/journey-onboarding/assets/assign-team6.png)

1. Cliquez sur **Enregistrer** et un e-mail de bienvenue est envoyé à l’utilisateur que vous avez ajouté. L’utilisateur invité peut accéder à Cloud Manager en cliquant sur le lien contenu dans l’e-mail de bienvenue et en se connectant à l’aide d’un Adobe ID.

1. Répétez ces étapes pour les utilisateurs de votre équipe.

Votre **Propriétaire de l’entreprise** ont été attribués et peuvent désormais accéder à Cloud Manager. N’oubliez pas de vous affecter en tant qu’administrateur système au **Propriétaire de l’entreprise** profile.

## Affectation du profil de produit Deployment Manager {#assign-deployment-manager}

1. Identifiez le ou les utilisateurs qui doivent déployer du code.

1. Connectez-vous à Admin Console à l’adresse `[adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview)` et dans la page **Aperçu** et sélectionnez le produit **Adobe Experience Manager as a Cloud Service** dans la carte **Produits et services**.

   ![Produits et services](/help/journey-onboarding/assets/assign-team1.png)

1. Sélectionnez l’onglet **Utilisateurs** dans la barre de navigation supérieure, puis sélectionnez **Ajouter un utilisateur**.

   ![Ajouter un utilisateur](/help/journey-onboarding/assets/assign-team4.png)

1. Dans la boîte de dialogue **Ajouter des utilisateurs à votre équipe**, entrez l’adresse e-mail de l’utilisateur que vous souhaitez ajouter.

   * Si l’identifiant fédéré des membres de votre équipe n’a pas encore été configuré, sélectionnez **Adobe ID** pour le **Type d’ID**.

   ![Saisie de l’ID](/help/journey-onboarding/assets/assign-team5.png)

1. Cliquez sur le bouton Plus sous l’en-tête **Sélection de produits ou de groupes d’utilisateurs** pour commencer la sélection de produit et sélectionnez **Adobe Experience Manager as a Cloud Service** et affecter le profil de produit **Gestionnaire de déploiement** à l’utilisateur.

   ![Attribution d’un profil](/help/journey-onboarding/assets/assign-team6.png)

Votre **Responsable de déploiement** ont été attribués et peuvent désormais accéder à Cloud Manager. Selon vos responsabilités futures, vous devrez peut-être également vous affecter en tant qu’administrateur système au **Responsable de déploiement** profile.

## Attribution du profil du produit développeur {#assign-developer}

1. Identifiez le ou les utilisateurs qui doivent développer des applications AEM et gérer le code.

1. Connectez-vous à Admin Console à l’adresse `[adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview)` et dans la page **Aperçu** et sélectionnez le produit **Adobe Experience Manager as a Cloud Service** dans la carte **Produits et services**.

   ![Produits et services](/help/journey-onboarding/assets/assign-team1.png)

1. Sélectionnez l’onglet **Utilisateurs** dans la barre de navigation supérieure, puis sélectionnez **Ajouter un utilisateur**.

   ![Ajouter un utilisateur](/help/journey-onboarding/assets/assign-team4.png)

1. Dans la boîte de dialogue **Ajouter des utilisateurs à votre équipe**, saisissez l’adresse e-mail de l’utilisateur que vous souhaitez ajouter.

   * Si l’identifiant fédéré des membres de votre équipe n’a pas encore été configuré, sélectionnez **Adobe ID** pour le **Type d’ID**.

   ![Ajout d’un ID d’utilisateur](/help/journey-onboarding/assets/assign-team5.png)

1. Cliquez sur le bouton Plus sous l’en-tête **Sélection de produits ou de groupes d’utilisateurs** pour commencer la sélection de produit et sélectionnez **Adobe Experience Manager as a Cloud Service** et affecter le profil de produit **Développeur** à l’utilisateur.

   ![Attribution d’un profil](/help/journey-onboarding/assets/assign-team6.png).

Votre **Développeur** ont été attribués et peuvent désormais accéder à Cloud Manager. Selon vos responsabilités futures, vous devrez peut-être également vous affecter en tant qu’administrateur système au **Développeur** profile.

## Prochaines étapes {#whats-next}

Félicitations ! Votre nouvelle équipe Cloud Manager (y compris vous-même affecté à la **Propriétaire de l’entreprise** profile) a été configuré. En tant que **Propriétaire d’entreprise** vous n’êtes qu’à une étape de la connexion à Cloud Manager et de l’activation de la création de vos ressources cloud.

Dans cette partie du parcours d’intégration, vous avez appris à affecter des membres de votre équipe à des profils dans le Admin Console. Vous devez maintenant :

* Comprendre les profils de produits.
* Découvrez Cloud Manager.
* Connaissez les trois profils de produits Cloud Manager importants : **Propriétaire de l’entreprise**, **Responsable de déploiement**, et **Développeur**.
* pouvoir affecter des membres de l’équipe aux profils de produits Cloud Manager.

Vous êtes maintenant prêt à poursuivre votre parcours d’intégration en consultant le document. [Accès à Cloud Manager,](cloud-manager.md) où vous apprendrez à accéder à Cloud Manager et à créer vos ressources de projet.

## Ressources supplémentaires {#additional-resources}

Il est recommandé de continuer votre parcours d’intégration comme décrit précédemment. Voici quelques ressources supplémentaires si vous souhaitez approfondir un sujet particulier de ce parcours.

* [Présentation de Cloud Manager](/help/onboarding/cloud-manager-introduction.md) - En savoir plus sur Cloud Manager, les programmes Cloud Manager et les environnements.
* [Profils de produit Cloud Manager](/help/onboarding/aem-cs-team-product-profiles.md) - Découvrez AEM l’équipe as a Cloud Service et les profils de produits.
* [Types d’identité dans Adobe Admin Console](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/identity.ug.html) - Le système de gestion des identités d’Adobe permet aux administrateurs de créer et de gérer l’accès des utilisateurs aux applications et services. Adobe propose ces types d’identités ou comptes pour authentifier et autoriser les utilisateurs.

