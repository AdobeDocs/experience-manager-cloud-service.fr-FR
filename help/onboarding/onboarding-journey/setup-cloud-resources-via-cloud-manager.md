---
title: Configuration de ressources Cloud via Cloud Manager
description: Consultez cette page pour savoir comment configurer des ressources Cloud via Cloud Manager
hide: true
hidefromtoc: true
index: false
source-git-commit: 021146e4e1d65c7fe81ed3dba70b32daf34b9704
workflow-type: tm+mt
source-wordcount: '891'
ht-degree: 1%

---

# Configuration de ressources Cloud via Cloud Manager {#setup-cloud-resources}

L’administrateur système affecté au rôle &quot;Propriétaire de l’entreprise&quot; doit accéder à Cloud Manager et se connecter à celui-ci. Ensuite, un membre de l’équipe affecté au profil de produit &quot;Propriétaire de l’entreprise&quot; doit se connecter à Cloud Manager et créer votre programme et vos environnements cloud afin que votre équipe d’experts puisse commencer.

## Objectif {#objective}

Ce document vous aide à comprendre comment vos ressources cloud sont créées et qui peut les réaliser.

Après avoir lu cette section, vous devez :

* Comprenez qu’un administrateur système affecté au rôle &quot;Propriétaire de l’entreprise&quot; doit être le premier à accéder à Cloud Manager et à se connecter à ce dernier.
* Découvrez comment votre programme cloud et vos environnements sont créés.

## Présentation {#introduction}

L’ajout de vos ressources cloud est effectué via Cloud Manager par un membre de votre équipe affecté au profil de produit du propriétaire d’entreprise de Cloud Manager. Cette personne est généralement celle qui comprend les besoins de l’entreprise et qui effectue la configuration initiale de Cloud Manager.

Consultez les sections ci-dessous pour savoir comment créer vos [programmes de service cloud](#create-cloud-service-program) et [environnements](#create-cloud-environments).

### Prérequis {#prerequisites}

* L’administrateur système affecté au rôle &quot;Propriétaire de l’entreprise&quot; doit accéder à Cloud Manager et se connecter à ce dernier.

* Découvrez comment naviguer dans Cloud Manager et vous connecter.

* Familiarisez-vous avec les profils de produit Cloud Manager

* Découvrez les points à prendre en compte pour créer votre programme. Regardez cette vidéo pour en savoir plus.

* Présentation des concepts des programmes et environnements Cloud Manager

## Accès à Cloud Manager {#navigate-cloud-manager}

1. L’utilisateur &quot;Propriétaire de l’entreprise&quot; recevra un e-mail de bienvenue lui indiquant où il pourra commencer ou, s’il ne parvient pas à le trouver, accédez directement à experience.adobe.com et connectez-vous à l’aide de votre Adobe ID.

1. Sur la page d’accueil de l’Experience Cloud, sélectionnez Experience Manager :


1. Vous accédez alors à la page d’accueil AEM. À partir de là, sélectionnez Cloud Manager :


1. Vous accédez alors à la page d’entrée de Cloud Manager comme illustré ci-dessous :


1. Vérifiez maintenant que le profil de produit du propriétaire de l’entreprise vous a été attribué. Pour ce faire, sélectionnez votre profil en haut à droite, comme illustré ci-dessous :


1. Sélectionnez maintenant Rôles utilisateur et assurez-vous que vous êtes affecté au propriétaire de l’entreprise.


   Super boulot ! Vous vous êtes connecté à Cloud Manager en tant que propriétaire de l’entreprise.

## Création d’un programme Cloud Service {#create-cloud-service-program}


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


## Création de vos environnements cloud {#create-cloud-environments}

1. Une fois que vous avez créé votre programme cloud, créez vos environnements cloud en accédant à la page d’aperçu de Cloud Manager et en sélectionnant Ajouter dans la carte d’environnement.

   >[!NOTE]
   >Un utilisateur de Cloud Manager possédant le rôle Propriétaire de l’entreprise ou Responsable de déploiement doit être connecté pour réussir cette étape.

   En outre, regardez le tutoriel vidéo rapide pour en savoir plus sur les environnements Cloud Manager et sur la manière dont vous pouvez les ajouter à votre programme.

1. Cela lancera l’assistant d’ajout d’environnement qui vous guidera dans l’ajout de votre environnement. Ajoutez d’abord votre environnement de développement pour vous familiariser.

1. Si vous ne l’avez pas déjà fait, vous pouvez ajouter les membres de votre équipe de développement à votre équipe Cloud Manager maintenant, accéder au profil de produit Ajout d’utilisateurs au développeur et suivre les étapes décrites. Ainsi, vos développeurs peuvent commencer à accéder à Cloud Manager et à gérer Cloud Manager Git.


   Félicitations ! Maintenant, vos environnements de programme cloud ont été créés et vos développeurs ont été ajoutés à l’équipe !

## Eléments suivants {#whats-next}

Désormais, les membres de votre équipe doivent recevoir des autorisations pour l’instance, car les autorisations pour administrer Cloud Manager ne seront pas suffisantes. Maintenant que vos ressources cloud ont été créées et que votre équipe est prête à y accéder, l’administrateur système doit affecter les membres de votre équipe à AEM en tant que profils de produit Cloud Service depuis Admin Console.

>[!NOTE]
>Pour pouvoir accéder à AEM en tant qu’utilisateurs Cloud Service, les utilisateurs doivent appartenir à l’un des deux profils de produit &quot;AEM utilisateurs&quot; ou &quot;administrateurs d’AEM&quot;. En savoir plus.

## Ressources supplémentaires {#additional-resources}

Suivez les autres ressources pour en savoir plus sur :

* Types de programme et ajout d’un programme
* Types d’environnement et ajout d’un environnement
* Gestion de Cloud Manager Git
* Configuration de l’accès à AEM en tant que Cloud Service à partir de Admin Console
