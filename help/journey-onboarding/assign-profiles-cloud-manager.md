---
title: Affectation de membres de l’équipe à des profils de produit Cloud Manager
description: Consultez cette page pour savoir comment affecter des membres de l’équipe à des profils de produits Cloud Manager.
feature: Onboarding
role: Admin, User, Developer
exl-id: 555688e5-f937-462c-9fcc-b90685f1882b
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '1520'
ht-degree: 94%

---


# Affecter des membres de l’équipe à des profils de produits Cloud Manager {#assign-team-members}

Dans cette partie du [parcours d’intégration](overview.md), découvrez comment affecter des membres de l’équipe aux profils de produits Cloud Manager.

## Objectif {#objective}

À l’étape précédente dans ce parcours, [Accès à l’Admin Console ](admin-console.md), vous avez appris à vous connecter à l’Admin Console et à vérifier vos privilèges en tant qu’administrateur système. Vous êtes maintenant prêt à autoriser les membres de votre équipe à accéder à Cloud Manager. Pour ce faire, attribuez des profils de produits.

Lorsque vous accordez à un utilisateur l’accès à une solution Adobe, vous n’avez pas nécessairement besoin de lui accorder un accès complet. Les profils de produit permettent à chaque solution d’avoir son propre jeu d’autorisations utilisateur. Vous utilisez Admin Console pour affecter des profils de produits.

La première étape consiste à accorder aux utilisateurs l’accès à Cloud Manager. Cloud Manager vous aide à mettre en place des configurations de développement d’entreprise et leurs pipelines CI/CD conçus spécifiquement, qui sont équipés pour garantir des tests approfondis et une qualité de code optimale pour offrir des expériences exceptionnelles.

Après avoir lu ce document, vous devriez :

* Comprendre ce que sont les profils de produits.
* Savoir en quoi consiste Cloud Manager.
* Comprendre les trois principaux profils de produits de Cloud Manager : **Propriétaire de l’entreprise**, **Responsable de déploiement** et **Développeur**.
* Être capable d’affecter des membres de l’équipe aux profils de produits Cloud Manager.

## Conditions préalables {#prerequisites}

Pour affecter des membres de l’équipe à des profils de produits, vous devez disposer d’informations sur les membres de l’équipe qui devront accéder à AEM as a Cloud Service, notamment :

* leur nom ;
* leur adresse e-mail ;
* leurs rôles et responsabilités.

>[!TIP]
>
>Dans le cadre de l’intégration, Adobe vous recommande d’ajouter initialement des utilisateurs qui participeront aux tâches immédiates, tels que les administrateurs, les développeurs et les auteurs de contenu.
>
>Vous pouvez poursuivre le processus d’intégration sans avoir besoin d’ajouter tous les utilisateurs. Une fois l’intégration terminée, vous pouvez ajouter d’autres utilisateurs.

## Profils de produits {#product-profiles}

Lorsque vous accordez à un utilisateur l’accès à une solution Adobe, vous n’avez pas nécessairement besoin de lui accorder un accès complet. Les profils de produits permettent à chaque solution d’avoir son propre ensemble d’autorisations utilisateur définies à l’aide d’Admin Console.

Par exemple, plus tard dans ce parcours, vous utiliserez Admin Console pour accorder aux utilisateurs l’accès à la solution AEM en affectant des profils de produits aux administrateurs AEM et aux auteurs d’AEM.

Toutefois, l’étape suivante consiste à accorder des profils de produits pour que les membres de votre équipe aient d’abord accès à Cloud Manager.

## Cloud Manager {#cloud-manager}

En tant qu’administrateur système, vous savez qu’un projet AEM as a Cloud Service réussi dépend non seulement de la création de contenu étonnant à l’aide d’AEM, mais aussi du développement et du déploiement de votre propre code personnalisé et de vos applications pour diffuser votre contenu AEM.

Cloud Manager fait partie intégrante d’AEM as a Cloud Service. Il permet de gérer vos pipelines CI/CD pour le déploiement du code, de gérer vos référentiels de code et de gérer vos environnements.

Avant que votre équipe puisse faire quoi que ce soit d’autre, elle doit être intégrée à Cloud Manager. Cela s’effectue à travers l’octroi des profils de produits nécessaires. Les étapes suivantes vous indiquent où trouver les profils de produits Cloud Manager à l’aide d’Admin Console et comment les affecter aux membres de votre équipe.

## Consulter les profils de produits Cloud Manager {#review-product-profiles}

Admin Console vous permet de voir la liste des profils Cloud Manager.

1. Connectez-vous à Adobe Admin Console à l’adresse [adminconsole.adobe.com](https://adminconsole.adobe.com/) et depuis la page **Aperçu**, sélectionnez **Adobe Experience Manager as a Cloud Service** dans la carte **Produits et services**.

   ![AEM en tant que produit](/help/journey-onboarding/assets/assign-team1.png)

1. Accédez à l’instance **Cloud Manager** à partir de la liste de toutes les instances.

   ![Cloud Manager](/help/journey-onboarding/assets/assign-team2.png)

1. La liste des profils de produits Cloud Manager préconfigurés s’affiche.

   ![Profils de produits.](/help/journey-onboarding/assets/assign-team3.png)

Les profils les plus importants à affecter dans le cadre du processus d’intégration initial sont les suivants :

* **Propriétaire de l’entreprise** : ces utilisateurs gèrent différents programmes.
* **Responsable de déploiement** : ces utilisateurs déploient le code de vos référentiels vers des environnements AEM en cours d’exécution.
* **Développeur** : ces utilisateurs développent vos applications AEM personnalisées et valident le code dans vos référentiels.

Connaissant ces rôles et ce qu’ils font, consultez votre liste de membres de l’équipe pour déterminer qui a besoin de quel profil. Gardez à l’esprit que des utilisateurs peuvent avoir et ont souvent plusieurs rôles dans une équipe et ont donc également besoin de plusieurs profils.

## Attribuer le profil de produit Propriétaire de l’entreprise {#assign-business-owner}

Vous êtes maintenant prêt à ajouter des utilisateurs et à les affecter au profil de produit **Propriétaire de l’entreprise**.

1. Identifiez les utilisateurs et utilisatrices qui géreront les programmes Cloud Manager. Il s’agit des **Propriétaires de l’entreprise**.

1. Connectez-vous à l’Admin Console à l’adresse `[adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview)` et, dans la page **Vue d’ensemble**, sélectionnez le produit **Adobe Experience Manager as a Cloud Service** à partir de la vignette **Produits et services**.

   ![Produits et services](/help/journey-onboarding/assets/assign-team1.png)

1. Sélectionnez l’onglet **Utilisateurs** dans la barre de navigation supérieure, puis sélectionnez **Ajouter un utilisateur**.

   ![Ajouter un utilisateur](/help/journey-onboarding/assets/assign-team4.png)

1. Dans la boîte de dialogue **Ajouter des utilisateurs à votre équipe**, entrez l’adresse e-mail de l’utilisateur que vous souhaitez ajouter.

   * Si l’identifiant fédéré des membres de votre équipe n’a pas encore été configuré, sélectionnez **Adobe ID** pour le **Type d’ID**.

   ![Ajout des détails utilisateur](/help/journey-onboarding/assets/assign-team5.png)

1. Cliquez sur le bouton Plus sous l’en-tête **Sélection de produits ou de groupes d’utilisateurs** pour commencer la sélection de produits, sélectionnez **Adobe Experience Manager as a Cloud Service** et affectez le profil de produit **Propriétaire de l’entreprise** à l’utilisateur.

   * Affectez chaque utilisateur à au moins un profil de produit afin qu’il puisse accéder à Cloud Manager.
   * N’oubliez pas de vous affecter en tant qu’administrateur système au rôle **Propriétaire de l’entreprise**.

   ![Assignation des utilisateurs](/help/journey-onboarding/assets/assign-team6.png)

1. Cliquez sur **Enregistrer** et un e-mail de bienvenue est envoyé à l’utilisateur que vous avez ajouté. L’utilisateur invité peut accéder à Cloud Manager en cliquant sur le lien contenu dans l’e-mail de bienvenue et en se connectant à l’aide d’un Adobe ID.

1. Répétez ces étapes pour les utilisateurs de votre équipe.

Vos **Propriétaires d’entreprise** ont été affectés et peuvent désormais accéder à Cloud Manager. N’oubliez pas également de vous affecter en tant qu’administrateur système au profil de **Propriétaire de l’entreprise**.

## Attribuer le profil de produit Responsable de déploiement {#assign-deployment-manager}

1. Identifiez le ou les utilisateurs qui doivent déployer du code.

1. Connectez-vous à Admin Console à l’adresse `[adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview)` et, dans la page **Aperçu**, sélectionnez le produit **Adobe Experience Manager as a Cloud Service** dans la vignette **Produits et services**.

   ![Produits et services](/help/journey-onboarding/assets/assign-team1.png)

1. Sélectionnez l’onglet **Utilisateurs** dans la barre de navigation supérieure, puis sélectionnez **Ajouter un utilisateur**.

   ![Ajouter un utilisateur](/help/journey-onboarding/assets/assign-team4.png)

1. Dans la boîte de dialogue **Ajouter des utilisateurs à votre équipe**, entrez l’adresse e-mail de l’utilisateur que vous souhaitez ajouter.

   * Si l’identifiant fédéré des membres de votre équipe n’a pas encore été configuré, sélectionnez **Adobe ID** pour le **Type d’ID**.

   ![Saisie de l’ID](/help/journey-onboarding/assets/assign-team5.png)

1. Cliquez sur le bouton Plus sous l’en-tête **Sélection de produits ou de groupes d’utilisateurs** pour commencer la sélection de produit et sélectionnez **Adobe Experience Manager as a Cloud Service** et affecter le profil de produit **Gestionnaire de déploiement** à l’utilisateur.

   ![Attribuer un profil](/help/journey-onboarding/assets/assign-team6.png)

Vos **Responsables de déploiement** ont été affectés et peuvent désormais accéder à Cloud Manager. Selon vos responsabilités futures, vous devrez peut-être également vous affecter en tant qu’administrateur système au profil de **Responsable de déploiement**.

## Attribuer le profil de produit Développeur {#assign-developer}

1. Identifiez le ou les utilisateurs qui doivent développer des applications AEM et gérer le code.

1. Connectez-vous à Admin Console à l’adresse `[adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview)` et, sur la page **Aperçu**, sélectionnez le produit **Adobe Experience Manager as a Cloud Service** dans la vignette **Produits et services**.

   ![Produits et services](/help/journey-onboarding/assets/assign-team1.png)

1. Sélectionnez l’onglet **Utilisateurs** dans la barre de navigation supérieure, puis sélectionnez **Ajouter un utilisateur**.

   ![Ajouter un utilisateur](/help/journey-onboarding/assets/assign-team4.png)

1. Dans la boîte de dialogue **Ajouter des utilisateurs à votre équipe**, saisissez l’adresse e-mail de l’utilisateur que vous souhaitez ajouter.

   * Si l’identifiant fédéré des membres de votre équipe n’a pas encore été configuré, sélectionnez **Adobe ID** pour le **Type d’ID**.

   ![Ajout d’un ID d’utilisateur](/help/journey-onboarding/assets/assign-team5.png)

1. Cliquez sur le bouton Plus sous l’en-tête **Sélection de produits ou de groupes d’utilisateurs** pour commencer la sélection de produit et sélectionnez **Adobe Experience Manager as a Cloud Service** et affecter le profil de produit **Développeur** à l’utilisateur.

   ![Attribution d’un profil](/help/journey-onboarding/assets/assign-team6.png).

Vos **développeurs** ont été affectés et peuvent désormais accéder à Cloud Manager. Selon vos responsabilités futures, vous devrez peut-être également vous affecter en tant qu’administrateur système au profil de **Développeur**.

## Prochaines étapes {#whats-next}

Félicitations ! Votre équipe Cloud Manager fraîchement formée (y compris vous-même, affecté au profil de **Propriétaire de l’entreprise**) a été configurée. Étant doté du rôle **Propriétaire de l’entreprise**, vous n’êtes qu’à une étape de la connexion à Cloud Manager et de l’activation de la création de vos ressources cloud.

Cette partie du parcours d’intégration vous a permis d’en savoir plus sur l’affectation de membres de votre équipe à des profils dans Admin Console. Vous devriez maintenant :

* Comprendre ce que sont les profils de produits.
* Savoir en quoi consiste Cloud Manager.
* Comprendre les trois principaux profils de produits de Cloud Manager : **Propriétaire de l’entreprise**, **Responsable de déploiement** et **Développeur**.
* Être capable d’affecter des membres de l’équipe aux profils de produits Cloud Manager.

Vous êtes maintenant prêt à poursuivre votre parcours d’intégration en consultant le document [Accès à Cloud Manager](cloud-manager.md), dans lequel vous apprendrez à accéder à Cloud Manager et à créer vos ressources de projet.

## Ressources supplémentaires {#additional-resources}

Il est recommandé de poursuivre le parcours d’intégration comme décrit précédemment. Voici quelques ressources supplémentaires si vous souhaitez approfondir un sujet particulier de ce parcours.

* [Présentation de Cloud Manager](/help/onboarding/cloud-manager-introduction.md) : découvrez Cloud Manager, les programmes et les environnements.
* [Profils de produits Cloud Manager](/help/onboarding/aem-cs-team-product-profiles.md) : découvrez l’équipe et les profils de produits AEM as a Cloud Service.
* [Types d’identité dans Adobe Admin Console](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/identity.ug.html) : le système Identity Management d’Adobe permet aux administrateurs et administratrices de créer et de gérer l’accès des utilisateurs et utilisatrices aux applications et services. Adobe propose ces types d’identités ou comptes pour authentifier et autoriser les utilisateurs et utilisatrices.

