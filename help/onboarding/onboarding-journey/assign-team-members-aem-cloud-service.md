---
title: 'Affecter des membres de l’équipe à AEM en tant que profils de produit Cloud Service '
description: Consultez cette page pour savoir comment affecter des membres de l’équipe à AEM en tant que profils de produit Cloud Service
hide: true
hidefromtoc: true
index: false
source-git-commit: f0d7886c0bf88fe42d05a1cdd6eb03b07b165c52
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 2%

---


# Affecter des membres de l’équipe à AEM en tant que profils de produit Cloud Service {#assign-team-members-cloud-service}

## Objectif {#objective}

Ce document vous aide à comprendre les étapes que votre administrateur système doit suivre pour affecter les membres de votre équipe à AEM en tant que profils de produit Cloud Service et pourquoi il est essentiel de permettre à vos auteurs AEM de se lancer dans leur parcours avec AEM.

Après avoir lu cette section, vous devez comprendre :

* Pourquoi et comment les membres de votre équipe sont affectés à AEM en tant que profils de produit de Cloud Service.
* Comment ajouter des membres de l’équipe à AEM profil de produit utilisateur.
* Comment ajouter des membres de l’équipe au profil de produit des administrateurs d’AEM.


## Présentation {#introduction}

Pour que l’accès à AEM en tant qu’utilisateurs Cloud Service soit accordé, il faut qu’il s’agisse de l’un des deux profils de produit suivants :  `AEM Users` ou `AEM Administrators`. Les membres de votre équipe doivent recevoir des autorisations sur l’instance AEM, car les autorisations d’administration de Cloud Manager ne seront pas suffisantes. En savoir plus.

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


   >[!IMPORTANT]
   >Avant de commencer à passer en revue les étapes d’attribution des membres de l’équipe à AEM en tant que profils de produit Cloud Service, veillez à suivre les deux étapes suivantes :
   >
   >1. Connectez-vous à [Adobe Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/admin-console.html?lang=en). Pour plus d’informations, voir Connexion à Admin Console .
      >
      >
   1. Examinez [AEM en tant que profils de produit Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#aem-product-profiles).


Pour afficher la liste des profils Cloud Manager à partir de Adobe Admin Console, procédez comme suit :

1. Connectez-vous à [Adobe Admin Console](https://adminconsole.adobe.com/). Sur la page **Aperçu**, sélectionnez **Adobe Experience Manager as a Cloud Service** dans la carte **Produits et services**.

   ![](/help/onboarding/onboarding-journey/assets/assign-team1.png)

1. Accédez à l’instance (instance Auteur de l’environnement de développement) et sélectionnez-la, comme illustré dans l’illustration ci-dessous.

   ![](/help/onboarding/onboarding-journey/assets/cloud-profiles-1.png)


1. La liste des AEM en tant que profils de produit de Cloud Service qui devront être attribués à un utilisateur en fonction de son rôle s’affiche.

   >[!NOTE]
   >Pour en savoir plus à ce sujet, voir [AEM en tant que profils de produit Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#aem-product-profiles).

   ![](/help/onboarding/onboarding-journey/assets/cloud-profiles-2.png)


## Ajout de membres d’équipe à AEM profil de produit utilisateur ou AEM administrateur {#add-team-members}

Pour pouvoir accéder à AEM en tant qu’instance de Cloud Service, les utilisateurs doivent appartenir à l’un des deux profils de produit `AEM Users` ou `AEM Administrators`.

>[!NOTE]
>Vous devez disposer d’autorisations sur l’instance, mais les autorisations pour administrer Cloud Manager ne seront pas suffisantes. En savoir plus.

Les étapes ci-dessous doivent être suivies par un administrateur système qui joue également le rôle Propriétaire de l’entreprise.

1. Accédez à votre programme à partir de Cloud Manager et sélectionnez le bouton **Gérer l’accès** dans le contexte de l’environnement ciblé, comme illustré ci-dessous.

   ![](/help/onboarding/onboarding-journey/assets/add-team1.png)

1. Un nouvel onglet vous permet d’accéder à Adobe Admin Console à partir duquel vous avez accès à l’instance de création de l’environnement. Sélectionnez *AEM Administrateurs* ou *AEM Utilisateurs* en fonction des autorisations que cette personne doit accorder. En savoir plus sur [AEM en tant que profils de produit Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#aem-product-profiles).

   ![](/help/onboarding/onboarding-journey/assets/add-team2.png)

1. Sélectionnez `AEM Administrator` ou `AEM User` et cliquez sur **Ajouter un utilisateur** comme illustré ci-dessous et envoyez les détails nécessaires pour terminer l’ajout du membre de l’équipe.

   ![](/help/onboarding/onboarding-journey/assets/add-team3.png)

   L’utilisateur que vous avez ajouté aura désormais accès à l’AEM en tant que service d’auteur de Cloud Service !

   >[!NOTE]
   >Vous souhaiterez répéter ces étapes pour tous les environnements, y compris le développement, l’évaluation et la production, si vous disposez des informations des membres de l’équipe qui ont besoin d’un accès disponible.


## Eléments suivants {#whats-next}

Les utilisateurs que vous avez affectés à AEM en tant que profils de produit Cloud Service sont maintenant prêts à apprendre à accéder à l’instance de création et à vous familiariser avec la création de pages dans AEM en tant que Cloud Service. Vous devez suivre le chemin, en consultant ensuite le document Chemin d’apprentissage pour les utilisateurs AEM ou Chemin d’apprentissage pour les développeurs et les responsables de déploiement.

## Ressources supplémentaires {#additional-resources}

* [Configuration de l’accès à AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/walk-through.html?lang=en)
* [Guide rapide pour la création de pages](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/getting-started/quick-start.html?lang=en)
