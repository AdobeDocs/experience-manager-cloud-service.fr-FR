---
title: Affectation de membres de l’équipe à des profils de produit AEM as a Cloud Service
description: Consultez cette page pour savoir comment affecter des membres de l’équipe à des profils de produit AEM as a Cloud Service
feature: Onboarding
role: Admin, User, Developer
exl-id: c00f5d28-85af-4bd3-a50c-913d1342241c
source-git-commit: 96a0dacf69f6f9c5744f224d1a48b2afa11fb09e
workflow-type: ht
source-wordcount: '833'
ht-degree: 100%

---

# Affectation de membres de l’équipe à des profils de produit AEM as a Cloud Service {#assign-team-members-cloud-service}

## Objectif {#objective}

Ce document vous aide à comprendre les étapes que votre administrateur système doit suivre pour affecter les membres de votre équipe à des profils de produit AEM as a Cloud Service et pourquoi il est essentiel de permettre à vos auteurs AEM de se lancer dans leur parcours avec AEM.

Après avoir lu cette section, vous devez comprendre :

* Pourquoi et comment les membres de votre équipe sont affectés à des profils de produit AEM as a Cloud Service.
* Comment ajouter des membres de l’équipe à un profil de produit utilisateur AEM.
* Comment ajouter des membres de l’équipe au profil de produit des administrateurs AEM.


## Présentation {#introduction}

Pour pouvoir accéder à AEM as a Cloud Service les utilisateurs doivent appartenir à l’un des deux profils de produit suivants : `AEM Users` ou `AEM Administrators`. Les membres de votre équipe doivent recevoir des autorisations sur l’instance AEM, car les autorisations d’administration de Cloud Manager ne seront pas suffisantes.

>[!NOTE]
>Chaque utilisateur affecté à un profil de produit utilisateur AEM par l’administrateur système disposera d’un accès (lecture seule) à Cloud Manager.

## Prérequis {#prerequisites}

Avant de commencer à lire cette section, vous devez tenir compte des conditions préalables suivantes :

* Comprendre [les profils de produit AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=fr#aem-product-profiles)
* Connaître [Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/admin-console.html?lang=fr)
* Les profils de produit Cloud Manager ont été attribués aux membres de votre équipe selon le cas, et les ressources cloud ont été configurées.
* Informations détaillées sur le membre de l’équipe : l’administrateur système doit disposer des noms et adresses électroniques ainsi que des rôles et responsabilités des membres de l’équipe qui devront accéder à AEM as a Cloud Service.

   >[!NOTE]
   >Dans le cadre de l’intégration, nous vous recommandons d’ajouter initialement des utilisateurs qui participeront aux tâches immédiates, tels que les administrateurs, les développeurs et les auteurs de contenu. Vous pouvez continuer l’intégration sans ajouter tous les utilisateurs. Une fois l’intégration terminée, vous pouvez mettre à l’échelle un plus grand nombre d’utilisateurs ultérieurement.


   >[!IMPORTANT]
   >Avant de commencer à passer en revue les étapes d’affectation de membres de l’équipe à des profils de produit AEM as a Cloud Service, veillez à suivre les deux étapes suivantes :
   >
   >1. Connectez-vous à [Adobe Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/admin-console.html?lang=fr). Pour plus d’informations, voir Connexion à Admin Console.
   >
   >1. Examinez [Profils de produit AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=fr#aem-product-profiles).


Pour afficher la liste des profils Cloud Manager à partir d’Adobe Admin Console, procédez comme suit :

1. Connectez-vous à [Adobe Admin Console](https://adminconsole.adobe.com/). Sur la page **Aperçu**, sélectionnez **Adobe Experience Manager as a Cloud Service** dans la carte **Produits et services**.

   ![](/help/journey-onboarding/assets/assign-team1.png)

1. Accédez à l’instance (instance Auteur de l’environnement de développement) et sélectionnez-la, comme illustré dans l’illustration ci-dessous.

   ![](/help/journey-onboarding/assets/cloud-profiles-1.png)


1. La liste des profils de produit AEM as a Cloud Service qui devront être attribués à un utilisateur en fonction de son rôle s’affiche.

   >[!NOTE]
   >Pour en savoir plus à ce sujet, voir [Profils de produit AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=fr#aem-product-profiles).

   ![](/help/journey-onboarding/assets/cloud-profiles-2.png)


## Ajout de membres d’équipe au profil de produit Administrateur AEM ou Utilisateur AEM {#add-team-members}

Pour pouvoir accéder à l’instance AEM as a Cloud Service, les utilisateurs doivent appartenir à l’un des deux profils de produit `AEM Users` ou `AEM Administrators`.

>[!NOTE]
>Vous devez disposer d’autorisations sur l’instance, mais les autorisations pour administrer Cloud Manager ne seront pas suffisantes. En savoir plus.

Les étapes ci-dessous doivent être suivies par un administrateur système qui joue également le rôle Propriétaire de l’entreprise.

1. Accédez à votre programme à partir de Cloud Manager et sélectionnez le bouton **Gérer l’accès** dans le contexte de l’environnement ciblé, comme illustré ci-dessous.

   ![](/help/journey-onboarding/assets/add-team1.png)

1. Un nouvel onglet vous permet d’accéder à Adobe Admin Console, à partir duquel vous avez accès à l’instance de création de l’environnement. Sélectionnez **Administrateurs AEM** ou **Utilisateurs AEM** en fonction des autorisations que cette personne doit se voir attribuer. En savoir plus sur les [profils de produit AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=fr#aem-product-profiles).

   ![](/help/journey-onboarding/assets/add-team2.png)

1. Sélectionnez `AEM Administrator` ou `AEM User` et cliquez sur **Ajouter un utilisateur** comme illustré ci-dessous et envoyez les détails nécessaires pour terminer l’ajout du membre de l’équipe.

   ![](/help/journey-onboarding/assets/add-team3.png)

   L’utilisateur que vous avez ajouté aura désormais accès aux services AEM d’auteur AEM as a Cloud Service.

   >[!NOTE]
   >Il vous faudra répéter ces étapes pour tous les environnements, y compris le développement, l’évaluation et la production, si vous disposez des informations des membres de l’équipe qui ont besoin d’un accès disponible.


## Et après ? {#whats-next}

Les utilisateurs que vous avez affectés aux profils de produit AEM as a Cloud Service sont maintenant prêts à apprendre à accéder à l’instance de création et à se familiariser avec la création de pages dans AEM as a Cloud Service. Vous devez suivre le chemin, en consultant ensuite le document Chemin d’apprentissage pour les [utilisateurs AEM](/help/journey-onboarding/sysadmin/learning-path-aem-users.md) ou le cursus de formation pour les [développeurs et les responsables de déploiement](/help/journey-onboarding/sysadmin/learning-path-developers-deploymentmanagers.md).

## Ressources supplémentaires {#additional-resources}

* [Gestion des produits et accès utilisateur dans Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=fr#managing-products-and-user-access-in-admin-console)
* [Configuration de l’accès à AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/walk-through.html?lang=fr)
* [Guide rapide pour la création de pages](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/getting-started/quick-start.html?lang=fr)
