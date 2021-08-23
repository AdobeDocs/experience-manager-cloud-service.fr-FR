---
title: 'Affectation de membres d’équipe à des profils de produit Cloud Manager '
description: Consultez cette page pour savoir comment affecter des membres de l’équipe à des profils de produit Cloud Manager
hide: true
index: false
source-git-commit: 4ef8c167e24a18af578d58c21fd1079a080f71d1
workflow-type: tm+mt
source-wordcount: '1440'
ht-degree: 3%

---


# Affectation de membres d’équipe à des profils de produit Cloud Manager {#assign-team-members}

Une fois que vous avez appris à vous connecter à [Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/admin-console.html?lang=en) et que vous avez consulté vos privilèges en tant qu’[administrateur système](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/system-administrator.html?lang=en), vous êtes prêt à affecter des membres de l’équipe aux profils de produit Cloud Manager.

## Objectif {#objective}

Ce document résume la manière d’affecter des membres de l’équipe à des profils de produit Cloud Manager à partir de Adobe Admin Console.

Après avoir lu cette section, vous devriez être en mesure de :

* Comprenez pourquoi et comment ajouter des membres de l’équipe.
* Découvrez trois profils de produit Cloud Manager différents, tels que Propriétaire d’entreprise, Responsable de déploiement et Développeur.
* Affectez des membres de l’équipe à des profils de produit Cloud Manager tels que Propriétaire de l’entreprise, Responsable de déploiement et Développeur.

## Prérequis {#prerequisites}

Les conditions préalables suivantes doivent être prises en compte avant de commencer cette section. Vous devez :

* Soyez administrateur système et comprenez [Profils produit Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles).
* Comprendre les [bases de Adobe Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/admin-console.html?lang=en).
* Consultez les détails sur les membres de votre équipe. Un administrateur système doit avoir les noms, les adresses électroniques et les rôles et responsabilités des membres de l’équipe qui devront accéder à AEM en tant que Cloud Service.

   >[!NOTE]
   >Dans le cadre de l’intégration, nous vous recommandons d’ajouter initialement des utilisateurs qui participeront aux tâches immédiates, tels que les administrateurs, les développeurs et les auteurs de contenu. Vous pouvez continuer l’intégration sans ajouter tous les utilisateurs. Une fois l’intégration terminée, vous pouvez mettre à l’échelle un plus grand nombre d’utilisateurs ultérieurement.

## Vérification des profils de produit Cloud Manager {#review-product-profiles}

Dans Adobe Admin Console, vous pouvez voir la liste des profils Cloud Manager.

>[!NOTE]
>Avant de passer en revue les profils de produit Cloud Manager à partir de Admin Console, il est recommandé de consulter les [Profils de produit Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles) disponibles.

Suivez les étapes ci-dessous pour afficher la liste des profils Cloud Manager :

1. Connectez-vous à [Adobe Admin Console](https://adminconsole.adobe.com/). Sur la page **Aperçu**, sélectionnez **Adobe Experience Manager as a Cloud Service** dans la carte **Produits et services**.

   ![](/help/onboarding/onboarding-journey/assets/assign-team1.png)

   >[!NOTE]
   >Pour savoir comment utiliser Admin Console, voir Connexion à Admin Console .


1. Accédez à l’instance **Cloud Manager** dans la liste de toutes les instances.

   ![](/help/onboarding/onboarding-journey/assets/assign-team2.png)

1. La liste des [profils de produits Cloud Manager préconfigurés s’affiche ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles).

   ![](/help/onboarding/onboarding-journey/assets/assign-team3.png)


## Affectation d’utilisateurs au profil de produit du propriétaire de l’entreprise {#assign-users-business-owner}

Vous êtes maintenant prêt à ajouter des utilisateurs et à les affecter au profil de produit Propriétaire de l’entreprise de Cloud Manager.

>[!NOTE]
>Pour ce faire, à partir d’Adobe Admin Console, vous devez ajouter un utilisateur au produit (AEM en tant que Cloud Service dans ce cas) et au [profil de produit Propriétaire de l’entreprise Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles).

Les étapes suivantes vous guideront :

1. Identifiez le ou les utilisateurs qui géreront les programmes Cloud Manager et ajoutez-les au profil de produit Propriétaire de l’entreprise . L’administrateur système doit être la première personne à accéder à Cloud Manager et à s’y connecter. Vous devez d’abord vous ajouter (administrateur système) au profil de produit Propriétaire de l’entreprise .

1. Dans la page [Admin Console](https://adminconsole.adobe.com/enterprise/overview) **Aperçu**, sélectionnez **Adobe Experience Manager en tant que Cloud Service** à partir de la carte **Produits et services** comme illustré ci-dessous.

   ![](/help/onboarding/onboarding-journey/assets/assign-team1.png)

1. Sélectionnez l’onglet **Utilisateurs** dans le volet de navigation supérieur, puis sélectionnez **Ajouter un utilisateur**.

   ![](/help/onboarding/onboarding-journey/assets/assign-team4.png)

1. Dans la boîte de dialogue **Ajouter des utilisateurs à votre équipe**, saisissez l’e-mail de l’utilisateur que vous souhaitez ajouter. Pour le type d’identifiant, sélectionnez Adobe ID si le Federated ID des membres de votre équipe n’a pas encore été configuré.

   ![](/help/onboarding/onboarding-journey/assets/assign-team5.png)

1. Dans la sélection de produit, sélectionnez **Adobe Experience Manager as a Cloud Service** et affectez le **Propriétaire de l’entreprise** profil de produit à l’utilisateur comme illustré ci-dessous.

   >[!NOTE]
   >Reportez-vous à [Profils de produit Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles) pour vous assurer que les utilisateurs appropriés se voient attribuer le ou les rôles appropriés en Admin Console, comme illustré ci-dessous.

   ![](/help/onboarding/onboarding-journey/assets/assign-team6.png)

   >[!NOTE]
   >Affectez l’utilisateur à au moins un profil de produit afin qu’il puisse accéder à Cloud Manager. N’oubliez pas de vous affecter (administrateur système) au propriétaire de l’entreprise.

1. Cliquez sur **Enregistrer**. Un e-mail de bienvenue est envoyé à l’utilisateur que vous avez ajouté. L’utilisateur invité peut accéder à Cloud Manager en cliquant sur le lien contenu dans l’e-mail de bienvenue et en se connectant à l’aide de son Adobe ID.

   Félicitations ! Votre nouvelle équipe Cloud Manager (y compris vous-même affecté au rôle &quot;Propriétaire de l’entreprise&quot;) a été configurée. Les membres recevront un e-mail de bienvenue les invitant à se connecter et à accéder à Cloud Manager. En tant que propriétaire d’entreprise, vous n’êtes qu’à une étape de la connexion à Cloud Manager et de l’activation de la création de vos ressources cloud.

## Affectation d’utilisateurs au profil de produit Deployment Manager {#assign-users-deployment-manager}

1. Identifiez le ou les utilisateurs qui géreront les programmes Cloud Manager et ajoutez-les au profil de produit Deployment Manager. L’administrateur système doit être la première personne à accéder à Cloud Manager et à s’y connecter. Vous devez d’abord vous ajouter (administrateur système) au profil de produit Propriétaire de l’entreprise (comme décrit dans la section précédente).

1. Dans la page [Admin Console](https://adminconsole.adobe.com/enterprise/overview) **Aperçu**, sélectionnez **Adobe Experience Manager en tant que Cloud Service** à partir de la carte **Produits et services** comme illustré ci-dessous.

   ![](/help/onboarding/onboarding-journey/assets/assign-team1.png)

1. Sélectionnez l’onglet **Utilisateurs** dans le volet de navigation supérieur, puis sélectionnez **Ajouter un utilisateur**.

   ![](/help/onboarding/onboarding-journey/assets/assign-team4.png)

1. Dans la boîte de dialogue **Ajouter des utilisateurs à votre équipe**, saisissez l’e-mail de l’utilisateur que vous souhaitez ajouter. Pour le type d’identifiant, sélectionnez Adobe ID si le Federated ID des membres de votre équipe n’a pas encore été configuré.

   ![](/help/onboarding/onboarding-journey/assets/assign-team5.png)

1. Dans la sélection de produit, sélectionnez **Adobe Experience Manager as a Cloud Service** et affectez **Deployment Manager** profil de produit à l’utilisateur, comme illustré ci-dessous.

   >[!NOTE]
   >Reportez-vous à [Profils de produit Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles) pour vous assurer que les utilisateurs appropriés se voient attribuer le ou les rôles appropriés en Admin Console, comme illustré ci-dessous.

   ![](/help/onboarding/onboarding-journey/assets/assign-team6.png).

   >[!IMPORTANT]
   >Un utilisateur peut être ajouté au profil de produit Deployment Manager après la création de ressources Cloud Manager.

## Affecter des utilisateurs au profil de produit du développeur {#assign-users-developer}

1. Identifiez le ou les utilisateurs qui géreront les programmes Cloud Manager et ajoutez-les au profil de produit Développeur. L’administrateur système doit être la première personne à accéder à Cloud Manager et à s’y connecter. Vous devez d’abord vous ajouter (administrateur système) au profil de produit Propriétaire de l’entreprise .

1. Dans la page [Admin Console](https://adminconsole.adobe.com/enterprise/overview) **Aperçu**, sélectionnez **Adobe Experience Manager en tant que Cloud Service** à partir de la carte **Produits et services** comme illustré ci-dessous.

   ![](/help/onboarding/onboarding-journey/assets/assign-team1.png)

1. Sélectionnez l’onglet **Utilisateurs** dans le volet de navigation supérieur, puis sélectionnez **Ajouter un utilisateur**.

   ![](/help/onboarding/onboarding-journey/assets/assign-team4.png)

1. Dans la boîte de dialogue **Ajouter des utilisateurs à votre équipe**, saisissez l’e-mail de l’utilisateur que vous souhaitez ajouter. Pour le type d’identifiant, sélectionnez Adobe ID si le Federated ID des membres de votre équipe n’a pas encore été configuré.

   >[!NOTE]
   >Pour en savoir plus sur les types d’identité sur Adobe Admin Console, consultez [Présentation des identités](https://helpx.adobe.com/fr/enterprise/using/identity.html).

   ![](/help/onboarding/onboarding-journey/assets/assign-team5.png)

1. Dans la sélection de produit, sélectionnez **Adobe Experience Manager as a Cloud Service** et affectez le **développeur** profil de produit à l’utilisateur, comme illustré ci-dessous.

   >[!NOTE]
   >Reportez-vous à [Profils de produit Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles) pour vous assurer que les utilisateurs appropriés se voient attribuer le ou les rôles appropriés en Admin Console, comme illustré ci-dessous.

   ![](/help/onboarding/onboarding-journey/assets/assign-team6.png).


   >[!IMPORTANT]
   >Un utilisateur peut être ajouté au profil de produit Développeur après la création de ressources Cloud Manager.

## Eléments suivants {#whats-next}

Vous avez découvert trois profils de produit Cloud Manager différents, tels que Propriétaire de l’entreprise, Responsable de déploiement et Développeur. Ensuite, vous avez affecté des membres de l’équipe à des profils de produit Cloud Manager tels que Propriétaire de l’entreprise, Responsable de déploiement et Développeur. Vous êtes maintenant prêt à poursuivre votre parcours d’intégration en consultant ensuite le document Configuration de ressources Cloud via Cloud Manager, dans lequel vous apprendrez :

1. En tant qu’administrateur système affecté au rôle *Propriétaire de l’entreprise*, vous devez accéder à Cloud Manager et vous connecter à celui-ci.

1. Ensuite, un utilisateur de Cloud Manager possédant le rôle *Propriétaire de l’entreprise* peut se connecter et configurer vos ressources cloud, y compris votre programme cloud et vos environnements. Votre équipe d’experts pourra ainsi commencer à accéder à AEM en tant que Cloud Service dès que possible.

1. Une fois que le *propriétaire d’entreprise* a configuré vos ressources cloud, les *développeurs* et *responsables de déploiement* qui ont été ajoutés avec succès aux profils de produit Cloud Manager peuvent accéder à Cloud Manager et se familiariser avec la manière dont ils peuvent continuer leur parcours d’apprentissage.

## Ressources supplémentaires {#additional-resources}

Suivez les autres ressources pour en savoir plus sur :

* [Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html?lang=en)
* [Profils de produit Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles)
* [Présentation de l’identité du Admin Console](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/identity.ug.html)
