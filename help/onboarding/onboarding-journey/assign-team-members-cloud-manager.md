---
title: 'Affectation de membres d’équipe à des profils de produit Cloud Manager '
description: Consultez cette page pour savoir comment affecter des membres de l’équipe à des profils de produit Cloud Manager
hide: true
hidefromtoc: true
index: false
source-git-commit: 8b30fc9494e152aa742cf17c02f982f5c9479473
workflow-type: tm+mt
source-wordcount: '1110'
ht-degree: 1%

---


# Affectation de membres d’équipe à des profils de produit Cloud Manager {#assign-team-members}

Une fois que vous avez appris à vous connecter à Admin Console et que vous avez consulté vos privilèges en tant qu’administrateur système, vous êtes prêt à affecter des membres de l’équipe aux profils de produit Cloud Manager.

## Objectif {#objective}

Ce document résume la manière d’affecter des membres de l’équipe à des profils de produit Cloud Manager à partir du Admin Console.

Après avoir lu cette section, vous devriez être en mesure de :

* Comprenez pourquoi et comment ajouter des membres de l’équipe.
* Découvrez trois profils de produit Cloud Manager différents, tels que Propriétaire d’entreprise, Responsable de déploiement et Développeur.
* Affectez des membres de l’équipe à des profils de produit Cloud Manager (Propriétaire de l’entreprise, Responsable de déploiement et Développeur).

## Vérification des profils de produit Cloud Manager {#review-product-profiles}

Dans Admin Console, vous pouvez voir la liste des profils Cloud Manager.

>[!NOTE]
>Avant de passer en revue les profils de produit Cloud Manager à partir d’Admin Console, il est recommandé de consulter les profils de produit Cloud Manager disponibles.

Suivez les étapes ci-dessous pour afficher la liste des profils Cloud Manager :

1. Connectez-vous à Adobe Admin Console. Sur la page **Aperçu**, sélectionnez Adobe Experience Manager as a Cloud service dans la carte Produits et services .

   >[!NOTE]
   >Pour savoir comment utiliser Admin Console, voir Connexion à Admin Console .


1. Accédez à l’instance de gestion du cloud à partir du tableau avec la liste de toutes les instances. La liste des profils de produits Cloud Manager préconfigurés s’affiche.


## Affectation d’utilisateurs au profil de produit du propriétaire de l’entreprise {#assign-users-business-owner}

Vous êtes maintenant prêt à ajouter des utilisateurs et à les affecter au profil de produit Propriétaire de l’entreprise de Cloud Manager.

Pour ce faire, à partir d’Admin Console d’Adobe, vous devez ajouter un utilisateur au produit (AEM en tant que Cloud Service dans ce cas) et au profil de produit Propriétaire de l’entreprise de Cloud Manager.

Les étapes suivantes vous guideront :

1. Identifiez le ou les utilisateurs qui géreront les programmes Cloud Manager et ajoutez-les au profil de produit Propriétaire de l’entreprise . L’administrateur système doit être la première personne à accéder à Cloud Manager et à se connecter à ce dernier. Vous devez d’abord vous ajouter (administrateur système) au profil de produit Propriétaire de l’entreprise .

1. Sur la page Aperçu du Admin Console , sélectionnez Adobe Experience Manager comme produit Cloud Service dans la carte produits et services , comme illustré ci-dessous :

1. Sélectionnez l’onglet Utilisateurs dans le volet de navigation supérieur, puis sélectionnez Ajouter un utilisateur.

1. Dans la boîte de dialogue Ajouter un utilisateur, saisissez l’e-mail de l’utilisateur que vous souhaitez ajouter. Pour le type d’identifiant, sélectionnez Adobe ID si le Federated ID des membres de votre équipe n’a pas encore été configuré.

1. Dans la sélection de produit, sélectionnez &quot;Adobe Experience Manager as a Cloud Service&quot; et affectez le profil de produit &quot;Propriétaire de l’entreprise&quot; à l’utilisateur, comme illustré ci-dessous. Reportez-vous aux profils de produit Cloud Manager pour vous assurer que les bons utilisateurs se voient attribuer le ou les rôles appropriés dans Admin Console, comme illustré ci-dessous.

1. Affectez l’utilisateur à au moins un profil de produit afin qu’il puisse accéder à Cloud Manager. N’oubliez pas de vous affecter (administrateur système) à &quot;Propriétaire de l’entreprise&quot;.

1. Cliquez sur Enregistrer. Un e-mail de bienvenue est envoyé à l’utilisateur que vous avez ajouté. L’utilisateur invité peut accéder à Cloud Manager en cliquant sur le lien contenu dans l’e-mail de bienvenue et en se connectant à l’aide de son Adobe ID.

Félicitations ! Désormais, votre nouvelle équipe Cloud Manager, y compris le rôle &quot;Propriétaire de l’entreprise&quot; qui vous a été attribué, a été configurée. Les membres recevront un e-mail de bienvenue les invitant à se connecter et à accéder à Cloud Manager. En tant que propriétaire d’entreprise, vous n’êtes qu’à une étape de la connexion à Cloud Manager et de l’activation de la création de vos ressources cloud.

## Affectation d’utilisateurs au profil de produit Deployment Manager {#assign-users-deployment-manager}

1. Identifiez le ou les utilisateurs qui géreront les programmes Cloud Manager et ajoutez-les au profil de produit Propriétaire de l’entreprise . L’administrateur système doit être la première personne à accéder à Cloud Manager et à se connecter à ce dernier. Vous devez d’abord vous ajouter (administrateur système) au profil de produit Propriétaire de l’entreprise .

1. Sur la page Aperçu du Admin Console , sélectionnez Adobe Experience Manager comme produit Cloud Service dans la carte produits et services , comme illustré ci-dessous :

1. Sélectionnez l’onglet Utilisateurs dans le volet de navigation supérieur, puis sélectionnez Ajouter un utilisateur.

1. Dans la boîte de dialogue Ajouter un utilisateur, saisissez l’e-mail de l’utilisateur que vous souhaitez ajouter. Pour le type d’identifiant, sélectionnez Adobe ID si le Federated ID des membres de votre équipe n’a pas encore été configuré.

1. Dans la sélection de produit, sélectionnez &quot;Adobe Experience Manager as a Cloud Service&quot; et affectez un profil de produit &quot;Deployment Manager&quot; à l’utilisateur, comme illustré ci-dessous. Reportez-vous aux profils de produit Cloud Manager pour vous assurer que les bons utilisateurs se voient attribuer le ou les rôles appropriés dans Admin Console, comme illustré ci-dessous.

   >[!NOTE]
   >Un utilisateur peut être ajouté au profil de produit Deployment Manager après la création de ressources Cloud Manager.

## Affecter des utilisateurs au profil de produit du développeur {#assign-users-developer}

1. Identifiez le ou les utilisateurs qui géreront les programmes Cloud Manager et ajoutez-les au profil de produit Propriétaire de l’entreprise . L’administrateur système doit être la première personne à accéder à Cloud Manager et à se connecter à ce dernier. Vous devez d’abord vous ajouter (administrateur système) au profil de produit Propriétaire de l’entreprise .

1. Sur la page Aperçu du Admin Console , sélectionnez Adobe Experience Manager comme produit Cloud Service dans la carte produits et services , comme illustré ci-dessous :

1. Sélectionnez l’onglet Utilisateurs dans le volet de navigation supérieur, puis sélectionnez Ajouter un utilisateur.

1. Dans la boîte de dialogue Ajouter un utilisateur, saisissez l’e-mail de l’utilisateur que vous souhaitez ajouter. Pour le type d’identifiant, sélectionnez Adobe ID si le Federated ID des membres de votre équipe n’a pas encore été configuré.

1. Dans la sélection de produit, sélectionnez &quot;Adobe Experience Manager as a Cloud Service&quot; et affectez un profil de produit &quot;Développeur&quot; à l’utilisateur, comme illustré ci-dessous. Reportez-vous aux profils de produit Cloud Manager pour vous assurer que les bons utilisateurs se voient attribuer le ou les rôles appropriés dans Admin Console, comme illustré ci-dessous.

   >[!NOTE]
   >Un utilisateur peut être ajouté au profil de produit Développeur après la création de ressources Cloud Manager.

## Eléments suivants {#whats-next}

En tant qu’administrateur système affecté au rôle *Propriétaire de l’entreprise*, vous devez accéder à Cloud Manager et vous connecter à celui-ci.
>[!NOTE]
>Reportez-vous à la section Accès à Cloud Manager pour savoir comment vous connecter et accéder à Cloud Manager.

Un utilisateur de Cloud Manager possédant le rôle Propriétaire de l’entreprise peut se connecter et configurer vos ressources cloud, y compris vos programmes et environnements. Votre équipe d’experts pourra ainsi commencer à accéder à AEM en tant que Cloud Service dès que possible.
Une fois que votre propriétaire d’entreprise a configuré vos ressources cloud, les développeurs et les responsables de déploiement qui ont été ajoutés avec succès aux profils de produit Cloud Manager peuvent accéder à Cloud Manager et se familiariser avec la manière dont ils peuvent continuer leur parcours d’apprentissage.

## Ressources supplémentaires {#additional-resources}

Suivez les autres ressources pour en savoir plus sur :

* Cloud Manager
* Profils de produit Cloud Manager
* Présentation de l’identité du Admin Console
