---
title: Attribuer des profils de produit AEM
description: Une fois que vos ressources Cloud sont configurées, vous devez accorder à votre équipe l’accès à AEM lui-même à l’aide de profils de produits AEM.
feature: Onboarding
role: Admin, User, Developer
exl-id: c00f5d28-85af-4bd3-a50c-913d1342241c
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '878'
ht-degree: 93%

---

# Attribuer des profils de produit AEM {#assign-profiles-aem}

>[!CONTEXTUALHELP]
>id="assets_user_entitlements"
>title="Attribuer les profils de produits AEM"
>abstract="Vous ne disposez pas de l’autorisation requise pour utiliser Experience Manager Assets. Contactez l’administration."

Dans cette partie du [parcours d’intégration](overview.md), découvrez comment accorder l’accès à AEM à votre équipe à l’aide de profils de produits AEM.

## Objectif {#objective}

Après avoir lu le document précédent de ce parcours d’intégration, [Créer des environnements](create-environments.md) et avoir configuré vos ressources cloud, accordez à votre équipe l’accès à AEM lui-même à l’aide des profils de produit AEM. En tant qu’administrateur ou administratrice système, vous pouvez le faire en attribuant des profils de produit AEM.

Après avoir lu ce document, vous comprendrez :

* Ce que sont les profils de produits AEM.
* Comment ajouter des membres de l’équipe à un profil de produit utilisateur AEM.
* Comment ajouter des membres de l’équipe au profil de produit des administrateurs AEM.

## Profils de produit AEM {#aem-product-profiles}

Pour utiliser AEM, les membres de votre équipe doivent être affectés à au moins un profil de produit AEM. Les autorisations d’accès à Cloud Manager ne suffiront pas. Les utilisateurs doivent appartenir à l’un des deux profils de produit suivants :

* `AEM Users` - Ce groupe comprend les utilisateurs normaux qui effectuent des tâches de création de contenu quotidiennes.
* `AEM Administrators` - Ce groupe comprend les utilisateurs responsables des fonctionnalités avancées ou d’AEM.

>[!NOTE]
>
>Chaque utilisateur/utilisatrice affecté(e) à un profil de produit AEM as a Cloud Service dispose d’un accès en lecture seule à Cloud Manager via le rôle **Utilisateur de Cloud Manager**.
>
>Les personnes disposant uniquement du rôle d’utilisation de **Cloud Manager** peuvent se connecter à Cloud Manager et accéder aux environnements de création AEM, le cas échéant, à l’aide des options de menu Programmes. Le rôle **Utilisateur de Cloud Manager** n’est pas suffisant pour accéder aux détails du programme. Si cet accès est nécessaire, les utilisateurs doivent faire appel à leur administrateur/administratrice système pour recevoir des rôles supplémentaires.
>Voir la section [Ressources supplémentaires](#additional-resources) ci-dessous pour plus d’informations sur les rôles d’utilisation de Cloud Manager.

>[!CAUTION]
>
>Ne modifiez ou ne supprimez pas les profils de produit nommés Administrateurs AEM ou Utilisateurs AEM. La modification de ces noms de profil peut rompre la connexion à l’instance cloud AEM.

## Conditions préalables {#prerequisites}

Avant de commencer à lire cette section, vous devez disposer des informations suivantes sur votre équipe qui utilisera AEM.

* leur nom ;
* leur adresse e-mail ;
* leurs rôles et responsabilités.

>[!TIP]
>
>Dans le cadre de l’intégration, Adobe vous recommande d’ajouter initialement des utilisateurs qui participeront aux tâches immédiates, tels que les administrateurs, les développeurs et les auteurs de contenu. Vous pouvez continuer l’intégration sans ajouter tous les utilisateurs. Une fois l’intégration terminée, vous pouvez mettre à l’échelle un plus grand nombre d’utilisateurs ultérieurement.

## Afficher les profils de produits AEM {#view-profiles}

Suivez ces étapes pour afficher les profils de produits AEM depuis Admin Console.

1. Connectez-vous à Admin Console à l’adresse [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com).

1. Sur la page **Aperçu**, sélectionnez **Adobe Experience Manager as a Cloud Service** dans la vignette **Produits et services**.

   ![Vignettes de produits et services](/help/journey-onboarding/assets/assign-team1.png)

1. Naviguez et sélectionnez l’instance.

   ![Sélectionner une instance](/help/journey-onboarding/assets/cloud-profiles-1.png)

1. La liste des profils de produit AEM as a Cloud Service qui devront être attribués à un utilisateur en fonction de son rôle s’affiche.

   ![Profils de produits](/help/journey-onboarding/assets/cloud-profiles-2.png)

## Ajouter des membres d’équipe aux profils de produit {#add-team-members}

Maintenant que vous connaissez les profils disponibles, vous pouvez les affecter si nécessaire aux membres de votre équipe.

Ces tâches nécessitent que vous soyez un administrateur système avec le profil de produit Cloud Manager **Propriétaire de l’entreprise**.

1. Accédez à votre programme à partir de Cloud Manager et sélectionnez le bouton **Gérer l’accès** du menu contextuel de l’environnement ciblé.

   ![Gérer l’accès](/help/journey-onboarding/assets/add-team1.png)

1. Un nouvel onglet vous permet d’accéder à Admin Console, à partir de laquelle vous avez accès à l’instance de création de l’environnement. Sélectionnez **Administrateurs AEM** ou **Utilisateurs AEM** en fonction des autorisations que l’individu concerné doit se voir attribuer.

   ![Attribution de l’accès.](/help/journey-onboarding/assets/add-team2.png)

1. Sélectionnez `AEM Administrator` ou `AEM User` et cliquez sur **Ajouter un utilisateur** comme illustré ci-dessous et envoyez les détails nécessaires pour terminer l’ajout du membre de l’équipe.

   ![Ajouter un membre de l’équipe](/help/journey-onboarding/assets/add-team3.png)

1. Veuillez répéter ces étapes pour tous les environnements, y compris le développement, l’évaluation et la production, si vous disposez d’informations venant des membres de l’équipe qui ont besoin d’un accès disponible.

L’utilisateur que vous avez ajouté aura désormais accès aux services de création AEM as a Cloud Service !

## Fin du parcours ? {#the-end}

Félicitations. Les utilisateurs que vous avez affectés aux profils de produit AEM as a Cloud Service sont maintenant prêts à accéder à l’environnement de création AEM et à commencer à créer du contenu avec AEM as a Cloud Service. De même, les développeurs peuvent désormais accéder à Cloud Manager pour utiliser Git afin de stocker le code d’application personnalisé et de le déployer. Ainsi, votre parcours d’intégration est terminé et vos utilisateurs peuvent désormais se servir d’AEMaaCS.

Cependant, si vous souhaitez mieux comprendre comment les créateurs et les développeurs utilisent le système, vous pouvez continuer avec deux parties facultatives de ce parcours d’intégration :

* [Tâches du développeur et du responsable de déploiement](developers.md) - Où vous découvrirez comment les développeurs accèdent à Git pour stocker leur code personnalisé et le déployer à l’aide des pipelines de Cloud Manager.
* [Tâches utilisateur d’AEM](aem-users.md) - Où vous apprendrez à accéder à l’environnement AEM où vous pouvez commencer à créer du contenu.

## Ressources supplémentaires {#additional-resources}

Vous trouverez ci-dessous des ressources facultatives supplémentaires si vous souhaitez aller au delà du contenu du parcours d’intégration.

* [Équipe et profils de produits AEM as a Cloud Service](/help/onboarding/aem-cs-team-product-profiles.md) - Découvrez comment l’équipe et les profils de produits AEM as a Cloud Service peuvent accorder et limiter l’accès à vos solutions Adobe sous licence.
* [Gestion des produits et accès utilisateur dans Admin Console](/help/security/ims-support.md#managing-products-and-user-access-in-admin-console) - Découvrez comment utiliser Admin Console pour gérer l’accès des utilisateurs et utilisatrices.
* [Configuration de l’accès à la présentation d’AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/walk-through.html?lang=fr) - Consultez cette présentation abrégée pour en savoir plus sur la configuration des utilisateurs et utilisatrices, groupes d’utilisateurs et d’utilisatrices et profils de produits Adobe IMS dans Admin Console.

