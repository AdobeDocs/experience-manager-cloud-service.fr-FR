---
title: Configuration de ressources Cloud via Cloud Manager
description: Consultez cette page pour savoir comment configurer des ressources Cloud via Cloud Manager
hide: true
hidefromtoc: true
index: false
source-git-commit: 5f599eb877565c65aad3d54af411bd8d40f4580d
workflow-type: tm+mt
source-wordcount: '1429'
ht-degree: 15%

---

# Configuration de ressources Cloud via Cloud Manager {#setup-cloud-resources}

L’administrateur système affecté au rôle Propriétaire de l’entreprise doit accéder à Cloud Manager et se connecter à celui-ci. Ensuite, un membre de l’équipe affecté au profil de produit Propriétaire de l’entreprise doit se connecter à Cloud Manager et créer votre programme et vos environnements cloud afin que votre équipe d’experts puisse commencer.

## Objectif {#objective}

Ce document vous aide à comprendre comment vos ressources cloud sont créées et qui peut les réaliser.

Après avoir lu cette section, vous devez comprendre :

* Un administrateur système affecté au rôle Propriétaire de l’entreprise doit être le premier à accéder à Cloud Manager et à se connecter.
* Comment votre programme et vos environnements cloud sont créés.

## Présentation {#introduction}

L’ajout de vos ressources cloud est effectué via Cloud Manager par un membre de votre équipe affecté au profil de produit du propriétaire d’entreprise de Cloud Manager. Cette personne est généralement celle qui comprend les besoins de l’entreprise et qui effectue la configuration initiale de Cloud Manager.

Consultez les sections ci-dessous pour savoir comment créer vos [programmes de service cloud](#create-cloud-service-program) et [environnements](#create-cloud-environments).

### Prérequis {#prerequisites}

* L’administrateur système affecté au rôle Propriétaire de l’entreprise doit accéder à Cloud Manager et se connecter à celui-ci.

* Découvrez comment [accéder à Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/what-is-required/navigate-to-cloud-manager.html?lang=en) et vous connecter.

* Familiarisez-vous avec les [profils de produits Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles).

* Comprendre les concepts des [programmes](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/understand-program-types.html?lang=en) et [environnements](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=fr) de Cloud Manager

## Accéder à Cloud Manager {#navigate-cloud-manager}

L’utilisateur Propriétaire de l’entreprise recevra un e-mail de bienvenue contenant un lien pour commencer ou, s’il ne parvient pas à le trouver, accédez directement à [Adobe Experience Cloud](https://experience.adobe.com) et connectez-vous à l’aide de votre Adobe ID.

Pour accéder à Cloud Manager, procédez comme suit :

1. Dans l’e-mail de bienvenue, cliquez sur **Commencer**, comme illustré dans l’illustration ci-dessous.
   ![](/help/onboarding/onboarding-journey/assets/get-started-email.png)

1. Vous accédez à la page **Programmes et produits** de Cloud Manager.

   >[!IMPORTANT]
   >Vous pouvez également accéder directement à la page de connexion de Cloud Manager à partir de [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/). Mettez cette page en signet à des fins de référence ultérieure et pour accéder directement à la page d’entrée de Cloud Manager.

1. Vous serez redirigé vers la page d’entrée de Cloud Manager. Voir [Affichage des programmes de Cloud Manager](#viewing-programs) pour plus d’informations.

De plus, vous pouvez accéder à la page **Programmes et produits** de Cloud Manager à partir de la page d’accueil de Adobe Experience Cloud. Suivez les étapes ci-dessous :

1. Accédez directement à [Adobe Experience Cloud](https://experience.adobe.com) et connectez-vous à l’aide de votre Adobe ID.

1. Sur la page d’accueil de Adobe Experience Cloud, sélectionnez **Experience Manager**.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources2.png)

1. Vous accédez alors à la page d’accueil AEM. À partir de là, lancez **Cloud Manager** .

   ![](/help/onboarding/onboarding-journey/assets/setup-resources3.png)

1. Une fois votre connexion établie, vous êtes dirigé vers la page d’entrée de Cloud Manager, comme indiqué ci-dessous. Voir [Affichage des programmes de Cloud Manager](#viewing-programs) pour plus d’informations.

   >[!NOTE]
   >Selon les rôles affectés dans [!UICONTROL Cloud Manager] et l’état de l’application, vous verrez plusieurs écrans lors de l’utilisation de l’interface utilisateur de [!UICONTROL Cloud Manager].

### Affichage des programmes sur la page d’entrée de Cloud Manager {#viewing-programs}

Une fois votre connexion établie, vous êtes dirigé vers la page d’entrée de Cloud Manager, comme indiqué ci-dessous. L’une des trois options suivantes s’affiche :

#### Lorsqu’aucun programme n’existe dans Cloud Manager {#no-programs}

S’il n’existe aucun programme dans votre organisation, votre page d’entrée vous demande de créer votre premier programme, comme le montre la figure ci-dessous.

![](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin0.png)

#### Lorsque des programmes existent déjà dans Cloud Manager {#programs-exist}

Si des programmes existent déjà dans votre organisation, votre page d’entrée vous demande d’ajouter un autre programme et d’afficher tous vos programmes existants, comme le montre la figure ci-dessous.

![](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin1.png)

#### Lorsqu’un programme existe et qu’un utilisateur est administrateur système {#programs-exist-sysadmin}

Si des programmes existent déjà dans votre organisation et que vous êtes administrateur système, votre page d’entrée affiche le bouton **Gérer l’accès** avec l’option **Ajouter un programme**, comme dans l’illustration ci-dessous.

![](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/admin-console-4.png)


## Vérification des rôles utilisateur {#verify-user-roles}

Une fois que vous êtes connecté à Cloud Manager, procédez comme suit pour vérifier que le profil du produit Propriétaire de l’entreprise vous a été attribué :

1. Sélectionnez votre profil en haut à droite, comme illustré ci-dessous.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources5.png)

1. Sélectionnez **Rôles utilisateur** et assurez-vous que vous êtes affecté au propriétaire de l’entreprise.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources6.png)

1. Ceci confirme votre rôle d’utilisateur en tant que propriétaire d’entreprise.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources7.png)

   Super boulot ! Vous vous êtes connecté à Cloud Manager en tant que propriétaire d’entreprise.

## Créer un programme Cloud Service {#create-cloud-service-program}

Pour créer votre programme de service cloud à partir de Cloud Manager, procédez comme suit :

1. Accédez à la page d’entrée de Cloud Manager, comme illustré ci-dessous.

   >[!NOTE]
   >Pour réussir cette étape, vous devez être un membre de l’équipe affecté au profil de produit Propriétaire d’entreprise de Cloud Manager .

   À partir de là, cliquez sur **Ajouter un programme** pour lancer l’assistant Ajouter un programme .

   ![](/help/onboarding/onboarding-journey/assets/setup-resources4.png)

   >[!NOTE]
   >Regardez la [vidéo](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=en) pour savoir comment créer votre AEM en tant que programme cloud et pour en savoir plus sur les points importants à prendre en compte avant de créer votre programme.

   >[!IMPORTANT]
   >Pour obtenir des instructions étape par étape sur l’utilisation de l’assistant Ajouter un programme, accédez à [ici](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/production-programs/creating-production-program.html?lang=en).
   >
   >* N’oubliez pas que le nom du programme ne peut pas être modifié après sa création. Nous vous recommandons d’être certain du nom que vous souhaitez donner à votre programme.
   >* Si vous devez modifier le nom de votre programme, vous devrez ouvrir un dossier auprès de l’assistance Adobe ou contacter votre représentant Adobe. Ils aideront à supprimer efficacement le programme. Vous devrez recommencer avec la perte potentielle de travail que votre équipe a faite.


1. Une fois la création de votre programme cloud terminée, vous pouvez accéder à votre programme pour afficher la page **Aperçu** de votre programme, comme illustré ci-dessous.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources8.png)

   >[!NOTE]
   >Si vous ne l’avez pas déjà fait, c’est le moment d’ajouter les membres de votre développeur à votre équipe Cloud Manager. Reportez-vous à Ajout d’utilisateurs au profil de produit Développeur et suivez les étapes décrites.

1. Les membres affectés au profil de produit Développeur peuvent se connecter à Cloud Manager et à [Git de Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/managing-code/accessing-git.html?lang=en).

   Super travail ! Maintenant que votre programme a été créé, votre Git Cloud Manager est accessible à vos développeurs.


## Création d’environnements cloud {#create-cloud-environments}

Une fois que vous avez créé votre programme cloud, créez vos environnements cloud.

Pour créer vos environnements cloud à partir de Cloud Manager, procédez comme suit :

1. Accédez à la page **Aperçu** de Cloud Manager et sélectionnez **Ajouter** dans la carte d’environnement.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources9.png)

   >[!IMPORTANT]
   >Un utilisateur de Cloud Manager possédant le rôle Propriétaire de l’entreprise ou Responsable de déploiement doit être connecté pour réussir cette étape.

   En outre, regardez le tutoriel rapide [vidéo](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=en) pour en savoir plus sur les environnements Cloud Manager et sur la manière dont vous pouvez les ajouter à votre programme.

1. Cela lancera l’assistant d’ajout d’environnement qui vous guidera tout au long de l’ajout de votre environnement. Ajoutez d’abord votre environnement de développement pour vous familiariser avec l’assistant. Voir [Ajout d’un environnement](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=fr#adding-environments) pour en savoir plus.

   >[!NOTE]
   >Si vous ne l’avez pas déjà fait, c’est le moment d’ajouter les membres de votre développeur à votre équipe Cloud Manager. Reportez-vous à Ajout d’utilisateurs au profil de produit Développeur et suivez les étapes décrites.

1. Les membres affectés au profil de produit Développeur peuvent se connecter à Cloud Manager et à [Git de Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/managing-code/accessing-git.html?lang=en).

   Super travail ! Votre programme a été créé avec succès et votre Git Cloud Manager est accessible à vos développeurs.

   Félicitations ! Maintenant, vos environnements de programme cloud ont été créés et vos développeurs ont été ajoutés à l’équipe !

## Eléments suivants {#whats-next}

Les membres de votre équipe doivent recevoir des autorisations pour l’instance, car les autorisations d’administration de Cloud Manager ne seront pas suffisantes. Maintenant que vos ressources cloud ont été créées et sont prêtes à être consultées par votre équipe, l’administrateur système doit affecter les membres de votre équipe à AEM en tant que profils de produit Cloud Service à partir de Adobe Admin Console.

>[!NOTE]
>Pour que l’accès à AEM en tant qu’utilisateurs Cloud Service soit accordé, les utilisateurs doivent appartenir à l’un des deux profils de produit `AEM Users` ou `AEM Administrators`. Voir [Gestion des produits et accès utilisateur en Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=en#managing-products-and-user-access-in-admin-console) pour en savoir plus.

Continuez votre parcours d’intégration en consultant le document Attribution de membres de l’équipe à AEM en tant que profils de produit Cloud Service .


## Ressources supplémentaires {#additional-resources}

Suivez les autres ressources pour en savoir plus sur :

* [Types de programme et ajout d’un programme](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=en)
* [Types d’environnement et ajout d’un environnement](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=en)
* [Gestion de Cloud Manager Git](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/managing-code/accessing-git.html?lang=en)
* [Configuration de l’accès à AEM en tant que Cloud Service à partir de Admin Console](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/overview.html?lang=en#adobe-ims-users)
