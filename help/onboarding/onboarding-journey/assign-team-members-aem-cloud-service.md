---
title: 'Affectation de membres d’équipe à AEM en tant que profils de produit Cloud Service '
description: Consultez cette page pour savoir comment affecter des membres de l’équipe à AEM en tant que profils de produit Cloud Service
hide: true
hidefromtoc: true
index: false
source-git-commit: c2301227eb65bedb77acd9754e2bc4b62527863d
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 1%

---


# Affectation de membres d’équipe à AEM en tant que profils de produit Cloud Service {#assign-team-members-cloud-service}

## Objectif {#objective}

Ce document vous aide à comprendre les étapes que votre administrateur système doit suivre pour affecter les membres de votre équipe à AEM en tant que profils de produit Cloud Service et pourquoi il est essentiel de permettre à vos auteurs AEM de se lancer dans leur parcours avec AEM.

Après avoir lu cette section, vous devez comprendre :

* Pourquoi et comment les membres de votre équipe sont affectés à AEM en tant que profils de produit de Cloud Service.
* Comment ajouter des membres de l’équipe à AEM profil de produit utilisateur.
* Comment ajouter des membres de l’équipe au profil de produit des administrateurs d’AEM.


## Présentation {#introduction}

Pour que l’accès à AEM en tant qu’utilisateurs Cloud Service soit accordé, il faut appartenir à l’un des deux profils de produit, tels que `AEM Users` ou `AEM Administrators`. Les membres de votre équipe doivent recevoir des autorisations sur l’instance AEM, car les autorisations d’administration de Cloud Manager ne seront pas suffisantes. En savoir plus.

>[!NOTE]
>Chaque utilisateur affecté à AEM profil de produit User par l’administrateur système disposera d’un accès (lecture seule) à Cloud Manager.

## Prérequis {#prerequisites}

Avant de commencer à lire cette section, vous devez tenir compte des conditions préalables suivantes :

* Comprendre [AEM en tant que profils de produits Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#aem-product-profiles)
* Familiarisez-vous avec [Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/admin-console.html?lang=en)
* Les profils de produit Cloud Manager ont été attribués aux membres de votre équipe selon le cas, et les ressources cloud ont été configurées.
* Informations détaillées sur le membre de l’équipe : L’administrateur système doit disposer des noms et adresses électroniques ainsi que des rôles et responsabilités des membres de l’équipe qui devront accéder à AEM en tant que Cloud Service.

   >[!NOTE]
   >Dans le cadre de l’intégration, nous vous recommandons d’ajouter initialement des utilisateurs qui participeront aux tâches immédiates, tels que les administrateurs, les développeurs et les auteurs de contenu. Vous pouvez continuer l’intégration sans ajouter tous les utilisateurs. Une fois l’intégration terminée, vous pouvez mettre à l’échelle un plus grand nombre d’utilisateurs ultérieurement.


1. Connectez-vous à [Adobe Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/admin-console.html?lang=en). Pour plus d’informations, voir Connexion à Admin Console .

1. Examinez [AEM en tant que profils de produit Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#aem-product-profiles).

Pour afficher la liste des profils Cloud Manager à partir de Adobe Admin Console, procédez comme suit :

1. Une fois connecté à Adobe Admin Console, sélectionnez Adobe Experience Manager as a Cloud service dans la carte Produits et services :

1. Accédez à l’instance (instance Auteur de l’environnement de développement) et sélectionnez-la, comme illustré dans l’illustration ci-dessous.

   Vous pouvez désormais voir la liste des profils de produit d’AEM en tant que Cloud Service qui devront être attribués à un utilisateur en fonction de son rôle. Pour en savoir plus à ce sujet, accédez à AEM as a Cloud Service Product Profiles.


## Ajout de membres de l’équipe à AEM profil de produit utilisateur ou AEM administrateur {#add-team-members}

Pour pouvoir accéder à AEM en tant qu’instance de Cloud Service, les utilisateurs doivent appartenir à l’un des deux profils de produit `AEM Users` ou `AEM Administrators`.

>[!NOTE]
>Vous devez disposer d’autorisations sur l’instance, mais les autorisations pour administrer Cloud Manager ne seront pas suffisantes. En savoir plus.

Les étapes ci-dessous doivent être suivies par l’administrateur système qui joue également le rôle Propriétaire de l’entreprise.

1. Dans Cloud Manager, accédez à Cloud Manager et sélectionnez le bouton Gérer l’accès dans le contexte de l’environnement ciblé, comme illustré ci-dessous :

1. Une fois que vous avez cliqué sur Gérer l’accès, un nouvel onglet vous permet d’accéder au Admin Console à partir duquel vous avez accès à l’instance de création de l’environnement. Sélectionnez *AEM Administrateurs* ou *AEM Utilisateurs* en fonction des autorisations que cette personne doit accorder. En savoir plus sur [AEM en tant que profils de produit Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#aem-product-profiles).

1. Sélectionnez Ajouter un utilisateur comme illustré ci-dessous et envoyez les détails nécessaires pour terminer l’ajout du membre de l’équipe :


1. Vous souhaiterez répéter ces étapes pour tous les environnements, y compris le développement, l’évaluation et la production, si vous disposez des informations des membres de l’équipe qui ont besoin d’un accès disponible.

   L’utilisateur que vous avez ajouté aura désormais accès à l’AEM en tant que service d’auteur de Cloud Service !


## Eléments suivants {#whats-next}

Les utilisateurs que vous avez affectés à AEM en tant que profils de produit Cloud Service sont maintenant prêts à apprendre à accéder à l’instance de création et à vous familiariser avec la création de pages dans AEM en tant que Cloud Service. Vous devez suivre le chemin, en consultant ensuite le document Chemin d’apprentissage pour les utilisateurs AEM.

## Ressources supplémentaires {#additional-resources}

* [Configuration de l’accès à AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/walk-through.html?lang=en)
* [Guide rapide pour la création de pages](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/getting-started/quick-start.html?lang=en)
