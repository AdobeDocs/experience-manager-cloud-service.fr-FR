---
title: Configuration de ressources Cloud via Cloud Manager
description: Consultez cette page pour savoir comment configurer des ressources Cloud via Cloud Manager
hide: true
hidefromtoc: true
index: false
source-git-commit: 9caf3447fedf13fa81bb616cc54b7cb6a08ff159
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 1%

---

# Configuration de ressources Cloud via Cloud Manager {#setup-cloud-resources}

L’administrateur système affecté au rôle *Propriétaire de l’entreprise* doit accéder à Cloud Manager et se connecter. Ensuite, un membre de l’équipe affecté au profil de produit *Propriétaire de l’entreprise* doit se connecter à Cloud Manager et créer votre programme et vos environnements cloud afin que votre équipe d’experts puisse commencer.

## Objectif {#objective}

Ce document vous aide à comprendre comment vos ressources cloud sont créées et qui peut les réaliser.

Après avoir lu cette section, vous devez comprendre :

* Un administrateur système affecté au rôle *Propriétaire de l’entreprise* doit être le premier à accéder à Cloud Manager et à se connecter.
* Comment votre programme et vos environnements cloud sont créés.

## Présentation {#introduction}

L’ajout de vos ressources cloud est effectué via Cloud Manager par un membre de votre équipe affecté au profil de produit du propriétaire d’entreprise de Cloud Manager. Cette personne est généralement celle qui comprend les besoins de l’entreprise et qui effectue la configuration initiale de Cloud Manager.

Consultez les sections ci-dessous pour savoir comment créer vos [programmes de service cloud](#create-cloud-service-program) et [environnements](#create-cloud-environments).

### Prérequis {#prerequisites}

* L’administrateur système affecté au rôle *Propriétaire de l’entreprise* doit accéder à Cloud Manager et se connecter.

* Découvrez comment [accéder à Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/what-is-required/navigate-to-cloud-manager.html?lang=en) et vous connecter.

* Familiarisez-vous avec les [profils de produits Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles).

* Découvrez les points à prendre en compte pour créer votre programme. Regardez cette vidéo pour en savoir plus.

* Comprendre les concepts des [programmes](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/understand-program-types.html?lang=en) et [environnements](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=en) de Cloud Manager

## Accéder à Cloud Manager {#navigate-cloud-manager}

1. L’utilisateur *Propriétaire de l’entreprise* recevra un e-mail de bienvenue à partir duquel il pourra commencer ou, s’il ne parvient pas à le trouver, accédez directement à [Adobe Experience Cloud](https://experience.adobe.com/#/@ccs/home) et connectez-vous à l’aide de votre Adobe ID.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources1.png)

1. Sur la page d’accueil de Adobe Experience Cloud, sélectionnez **Experience Manager**.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources2.png)

1. Vous accédez alors à la page d’accueil AEM. À partir de là, lancez **Cloud Manager** .

   ![](/help/onboarding/onboarding-journey/assets/setup-resources3.png)

1. La page d’entrée de Cloud Manager s’affiche, comme illustré dans la figure ci-dessous.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources4.png)

1. Vérifiez que le profil de produit Propriétaire de l’entreprise vous a été attribué. Pour ce faire, sélectionnez votre profil en haut à droite, comme illustré ci-dessous.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources5.png)

1. Sélectionnez **Rôles utilisateur** et assurez-vous que vous êtes affecté au propriétaire de l’entreprise.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources6.png)

1. Ceci confirme votre rôle d’utilisateur en tant que propriétaire d’entreprise.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources7.png)

   Super boulot ! Vous vous êtes connecté à Cloud Manager en tant que propriétaire d’entreprise.

## Créer un programme Cloud Service {#create-cloud-service-program}

Pour créer votre programme de service cloud à partir de Cloud Manager, procédez comme suit :

1. Accédez à la page d’entrée de Cloud Manager comme illustré ci-dessous.

   >[!NOTE]
   >Pour réussir cette étape, vous devez être un membre de l’équipe affecté au profil de produit Propriétaire d’entreprise de Cloud Manager .

1. À partir de là, sélectionnez Ajouter un programme pour lancer l’assistant Ajouter un programme . Regardez la vidéo pour découvrir comment créer votre programme AEMaaCS et les points importants à prendre en compte avant de créer votre programme.

1. Pour obtenir des instructions étape par étape sur l’utilisation de l’assistant Ajouter un programme, cliquez ici.

   >[!CAUTION]
   >N’oubliez pas que le nom du programme ne peut pas être modifié après sa création. Nous vous recommandons d’être certain du nom que vous souhaitez donner à votre programme.

   Si vous devez modifier le nom de votre programme, vous devrez ouvrir un dossier auprès de l’assistance Adobe ou contacter votre représentant Adobe. Ils aideront à supprimer efficacement le programme. Vous devrez recommencer avec la perte potentielle de travail que votre équipe a faite.

1. Une fois la création de votre programme cloud terminée, vous pouvez accéder à votre programme pour afficher la page d’aperçu de votre programme, comme illustré ci-dessous :

1. Si vous ne l’avez pas déjà fait, c’est le moment d’ajouter les membres de votre équipe de développement à votre équipe Cloud Manager, d’accéder au profil de produit Ajout d’utilisateurs au développeur et de suivre les étapes décrites.

1. Les membres affectés au profil de produit Développeur peuvent se connecter à Cloud Manager et à Gérer Cloud Manager Git.


   Super travail ! Maintenant que votre programme a été créé, votre Git Cloud Manager est accessible à vos développeurs.


## Création d’environnements cloud {#create-cloud-environments}

Pour créer vos environnements cloud à partir de Cloud Manager, procédez comme suit :

1. Une fois que vous avez créé votre programme cloud, créez vos environnements cloud en accédant à la page d’aperçu de Cloud Manager et en sélectionnant Ajouter dans la carte d’environnement.

   >[!IMPORTANT]
   >Un utilisateur de Cloud Manager possédant le rôle Propriétaire de l’entreprise ou Responsable de déploiement doit être connecté pour réussir cette étape.

   En outre, regardez le tutoriel vidéo rapide pour en savoir plus sur les environnements Cloud Manager et sur la manière dont vous pouvez les ajouter à votre programme.

1. Cela lancera l’assistant d’ajout d’environnement qui vous guidera dans l’ajout de votre environnement. Ajoutez d’abord votre environnement de développement pour vous familiariser.

1. Si vous ne l’avez pas déjà fait, vous pouvez ajouter les membres de votre équipe de développement à votre équipe Cloud Manager maintenant, accéder au profil de produit Ajout d’utilisateurs au développeur et suivre les étapes décrites. Ainsi, vos développeurs peuvent commencer à accéder à Cloud Manager et à gérer Cloud Manager Git.


   Félicitations ! Maintenant, vos environnements de programme cloud ont été créés et vos développeurs ont été ajoutés à l’équipe !

## Eléments suivants {#whats-next}

Les membres de votre équipe doivent recevoir des autorisations pour l’instance, car les autorisations d’administration de Cloud Manager ne seront pas suffisantes. Maintenant que vos ressources cloud ont été créées et que votre équipe est prête à y accéder, l’administrateur système doit affecter les membres de votre équipe à AEM en tant que profils de produit Cloud Service depuis Admin Console.

Continuez votre parcours d’intégration en consultant le document Attribution de membres de l’équipe à AEM en tant que profils de produit Cloud Service .

>[!NOTE]
>Pour pouvoir accéder à AEM en tant qu’utilisateurs Cloud Service, les utilisateurs doivent appartenir à l’un des deux profils de produit &quot;AEM utilisateurs&quot; ou &quot;administrateurs d’AEM&quot;. En savoir plus.

## Ressources supplémentaires {#additional-resources}

Suivez les autres ressources pour en savoir plus sur :

* [Types de programme et ajout d’un programme](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=en)
* [Types d’environnement et ajout d’un environnement](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=en)
* [Gestion de Cloud Manager Git](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/managing-code/accessing-git.html?lang=en)
* [Configuration de l’accès à AEM en tant que Cloud Service à partir de Admin Console](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/overview.html?lang=en#adobe-ims-users)
