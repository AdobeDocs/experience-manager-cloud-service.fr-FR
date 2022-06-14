---
title: Configuration de ressources cloud via Cloud Manager
description: Découvrez comment utiliser Cloud Manager pour configurer et gérer vos propres ressources cloud.
role: Admin, User, Developer
exl-id: de3a33b7-b459-4e47-b232-a0f88e2ce22e
source-git-commit: 0db24518610fccf0d2ea5e0620a0c6a5f8009ea8
workflow-type: tm+mt
source-wordcount: '1369'
ht-degree: 100%

---

# Configuration de ressources cloud via Cloud Manager {#setup-cloud-resources}

Découvrez comment utiliser Cloud Manager pour configurer et gérer vos propres ressources cloud.

## Objectif {#objective}

Ce document vous aide à comprendre comment vos ressources cloud sont créées et qui peut les créer. Après avoir lu cette section, vous devez comprendre :

* Un administrateur système affecté au rôle **Propriétaire de l’entreprise** doit être le premier dans votre organisation à se connecter et à accéder à Cloud Manager.
* comment votre programme et vos environnements cloud sont créés.

## Présentation {#introduction}

L’ajout de vos ressources cloud est effectué via Cloud Manager par un membre de votre équipe affecté au profil de produit **Propriétaire d’entreprise**. Cette personne est généralement celle qui comprend les besoins de l’entreprise et qui effectue la configuration initiale de Cloud Manager.

Consultez les sections ci-dessous pour savoir comment créer vos [environnements](#create-cloud-environments) et [programmes de services cloud](#create-cloud-service-program).

### Conditions préalables {#prerequisites}

* L’administrateur système affecté au rôle **Propriétaire de l’entreprise** doit se connecter à Cloud Manager avant toute tentative d’un autre utilisateur disposant du rôle de **Propriétaire de l’entreprise** d’accéder à Cloud Manager pour effectuer les étapes décrites dans ce document.

   * Revenez au document [Affectation de membres d’équipe à des profils de produit Cloud Manager](/help/journey-onboarding/sysadmin/assign-team-members-cloud-manager.md) de ce parcours pour plus d’informations.

* Vous devez comprendre comment [accéder à Cloud Manager et vous connecter.](/help/onboarding/learn-concepts/cloud-manager-introduction.md)

* Vous devriez vous familiariser avec les [profils de produits Cloud Manager.](/help/onboarding/learn-concepts/aem-cs-team-product-profiles.md#cloud-manager-product-profiles)

* Vous devriez comprendre les concepts des [programmes](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) et [environnements](/help/implementing/cloud-manager/manage-environments.md) Cloud Manager.

## Accédez à Cloud Manager en tant qu’administrateur système et propriétaire de l’entreprise {#access-sysadmin-bo}

Avant que les membres de l’équipe que vous avez affectés au rôle de **Propriétaire de l’entreprise** puissent accéder à cloud manager et commencer à créer des ressources cloud, l’administrateur système doit se voir affecter le rôle de **Propriétaire de l’entreprise** et se connecter à Cloud Manager.

1. Assurez-vous que, en tant qu’administrateur système, le rôle de **Propriétaire de l’entreprise** vous est affecté.

   * Revenez à l’étape précédente dans ce parcours, [Affectation des membres d’équipe à des profils de produit Cloud Manager,](/help/journey-onboarding/sysadmin/assign-team-members-cloud-manager.md) pour plus d’informations sur l’attribution du rôle de **Propriétaire de l’entreprise** à l’administrateur système si vous ne l’avez pas déjà fait.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et familiarisez-vous avec la page d’entrée normale.

En vous connectant correctement en tant qu’administrateur système avec le rôle de **Propriétaire de l’entreprise**, vous initialisez Cloud Manager pour une utilisation par les autres utilisateurs qui disposent du rôle de **Propriétaire de l’entreprise**. Vous ne recevrez aucune confirmation ou message. Il vous suffit de vous connecter.

Jusqu’à ce que vous vous connectiez à Cloud Manager en tant qu’administrateur système avec le rôle de **Propriétaire de l’entreprise**, les autres utilisateurs qui disposent du rôle de **Propriétaire de l’entreprise** ne seront pas en mesure de créer des programmes dans Cloud Manager même s’ils disposent des rôles appropriés.

## Accéder à Cloud Manager {#navigate-cloud-manager}

L’utilisateur avec le rôle de **Propriétaire de l’entreprise** recevra un e-mail de bienvenue avec un lien pour commencer. Suivez les étapes ci-dessous pour accéder à Cloud Manager à l’aide de cet e-mail de bienvenue.

1. Dans l’e-mail de bienvenue, cliquez sur **Commencer**, comme illustré dans l’illustration ci-dessous.
   ![Exemple d’e-mail](/help/journey-onboarding/assets/get-started-email.png)

1. Vous accédez à la page **Programmes et produits** de Cloud Manager.

   >[!TIP]
   >
   >Vous pouvez également accéder directement à la page de connexion de Cloud Manager à partir de [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/). Veuillez mettre un signet sur cette page pour vous en servir ultérieurement.

1. Vous serez redirigé vers la page d’entrée de Cloud Manager. Voir [Affichage des programmes de Cloud Manager](#viewing-programs) pour plus d’informations.

Vous pouvez également accéder à la page **Programmes et produits** de Cloud Manager à partir de la page d’accueil d’Adobe Experience Cloud

1. Accédez directement à [Adobe Experience Cloud](https://experience.adobe.com) et connectez-vous à l’aide de votre Adobe ID.

1. Sur la page d’accueil d’Adobe Experience Cloud, sélectionnez **Experience Manager**.

   ![Page d’accueil Experience Cloud](/help/journey-onboarding/assets/setup-resources2.png)

1. Vous accédez alors à la page d’accueil AEM. À partir de là, cliquez sur **Ouvrir** sur la mosaïque **Cloud Manager**.

   ![Page d’accueil AEM](/help/journey-onboarding/assets/setup-resources3.png)

1. Une fois votre connexion établie, vous êtes dirigé vers la page d’entrée de Cloud Manager, comme indiqué ci-dessous. Voir [Affichage des programmes de Cloud Manager](#viewing-programs) pour plus d’informations.

C’est à vous de décider comment accéder à vos programmes et produits via Cloud Manager et cela n’a aucun effet sur la manière dont vous utilisez Cloud Manager ou dont vous gérez vos programmes.

>[!NOTE]
>
>Selon les rôles affectés dans [!UICONTROL Cloud Manager] et l’état de l’application, vous verrez plusieurs écrans lors de l’utilisation de l’interface utilisateur de [!UICONTROL Cloud Manager].

### Affichage des programmes {#viewing-programs}

Une fois que vous avez accédé à Cloud Manager, ce que vous voyez dépend de l’état de vos programmes, comme indiqué dans les sections suivantes.

#### Lorsqu’il n’existe aucun programme {#no-programs}

S’il n’existe aucun programme dans votre organisation, votre page d’entrée vous invite à créer votre premier programme.

![Aucun programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin0.png)

#### Quand les programmes existent déjà {#programs-exist}

Si des programmes existent déjà dans votre organisation, votre page d’entrée affiche vos programmes existants et propose également un bouton pour ajouter des programmes supplémentaires.

![Il existe des programmes](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin1.png)

#### Lorsqu’un programme existe et que vous êtes administrateur système {#programs-exist-sysadmin}

Si des programmes existent déjà dans votre organisation et que vous êtes administrateur système, votre page d’entrée affiche le bouton **Gérer l’accès** avec l’option **Ajouter un programme**.

![Vue de l’administrateur système](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/admin-console-4.png)


## Vérification des rôles utilisateur {#verify-user-roles}

Une fois que vous êtes connecté à Cloud Manager, vous pouvez vérifier que le profil de produit **Propriétaire de l’entreprise** vous a été attribué.

1. Sélectionnez votre profil en haut à droite de la fenêtre.

   ![Profil utilisateur](/help/journey-onboarding/assets/setup-resources5.png)

1. Sélectionnez **Rôles utilisateur** pour afficher les rôles affectés à votre utilisateur.

   ![Rôles utilisateur](/help/journey-onboarding/assets/setup-resources6.png)

1. Confirme que l’utilisateur dispose du rôle de **Propriétaire de l’entreprise**.

   ![Liste des rôles utilisateur](/help/journey-onboarding/assets/setup-resources7.png)

Vous vous êtes connecté à Cloud Manager en tant que propriétaire d’entreprise. Si le rôle de **Propriétaire de l’entreprise** ne vous est pas affecté, contactez votre administrateur système.

## Création d’un programme de Cloud Service {#create-cloud-service-program}

Maintenant que vous avez un accès approprié, vous pouvez créer votre premier programme.

1. Accédez à la page d’entrée de Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et connectez-vous.

1. Sur la page d’entrée de Cloud Manager, cliquez sur **Ajouter un programme** pour lancer l’assistant Ajouter un programme.

   ![Page d’entrée](/help/journey-onboarding/assets/setup-resources4.png)

   >[!TIP]
   >
   >Pour obtenir des instructions étape par étape sur l’utilisation de l’assistant Ajouter un programme, reportez-vous au document [Création de programmes de production](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) ou regardez cette [vidéo](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=fr) pour savoir comment créer votre programme AEM as a Cloud et connaître les points importants à prendre en compte avant de créer votre programme.


1. Une fois la création de votre programme cloud terminée, vous pouvez accéder à votre programme à partir de la page d’entrée de Cloud Manager pour afficher la page de **Présentation** de votre programme.

   ![Aperçu du programme](/help/journey-onboarding/assets/setup-resources8.png)

1. Les membres affectés au profil de produit Développeur peuvent se connecter à Cloud Manager et gérer le référentiel Git de Cloud Manager.

   * Si vous ne l’avez pas déjà fait, le moment est venu d’affecter des membres au rôle de **Développeur** dans votre équipe Cloud Manager. Revenez au document [Affectation de membres d’équipe à des profils de produit Cloud Manager](/help/journey-onboarding/sysadmin/assign-team-members-cloud-manager.md) de ce parcours pour plus d’informations.

Votre programme est maintenant créé et votre référentiel Git de Cloud Manager est accessible pour vos développeurs.

## Création d’environnements cloud {#create-cloud-environments}

Une fois que vous avez créé votre programme cloud, créez vos environnements cloud.

1. Accédez à la page d’entrée de Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez **Ajouter** depuis la carte environnement.

   ![Bouton Ajouter un environnement](/help/journey-onboarding/assets/setup-resources9.png)

1. L’assistant Ajouter un environnement se lance et vous guide tout au long de l’ajout de votre environnement. Ajoutez d’abord votre environnement de développement pour vous familiariser avec l’assistant.

   >[!TIP]
   >
   >Reportez-vous au document [Ajout d’un environnement](/help/implementing/cloud-manager/manage-environments.md#adding-environments) pour en savoir plus ou regarder [ce court tutoriel vidéo](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=fr) pour en savoir plus sur les environnements Cloud Manager et sur la manière dont vous pouvez les ajouter à votre programme.

1. Les membres affectés au profil de produit **Développeur** peuvent se connecter à Cloud Manager et gérer le référentiel Git de Cloud Manager.

Votre programme est maintenant créé et votre Git Cloud Manager est accessible à vos développeurs.

## Prochaines étapes {#whats-next}

Maintenant que vos ressources cloud ont été créées et sont prêtes à être consultées par votre équipe, l’administrateur système doit affecter les membres de votre équipe à AEM en tant que profils de produit Cloud Service à partir d’Adobe Admin Console afin d’accéder à ces ressources.

Vous devriez continuer votre parcours d’intégration en consultant le document [Affectation de membres de l’équipe à des profils de produit AEM as a Cloud Service](/help/journey-onboarding/sysadmin/assign-team-members-aem-cloud-service.md) où vous apprendrez à accorder aux membres de votre équipe les droits dont ils ont besoin pour accéder à vos nouveaux environnements.

## Ressources supplémentaires {#additional-resources}

Suivez les autres ressources pour en savoir plus sur les aspects suivants :

* [Types de programme et ajout d’un programme](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html)
* [Types d’environnement et ajout d’un environnement](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html)
* [Gérer le référentiel Git de Cloud Manager](/help/implementing/cloud-manager/managing-code/accessing-repos.md)
* [Configurer l’accès à AEM as a Cloud Service à partir de l’Admin Console](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/overview.html?lang=fr#adobe-ims-users)
