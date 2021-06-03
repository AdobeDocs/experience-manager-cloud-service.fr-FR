---
title: AEM en tant qu’équipe de Cloud Service et profils de produit
description: Consultez cette page pour en savoir plus sur AEM en tant qu’équipe de Cloud Service et les profils de produit.
source-git-commit: 02e954d294100a17fff327742fa442fc4759860c
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 1%

---


# AEM en tant qu’équipe de Cloud Service et profils de produit {#product-profiles}

## Profils de produit {#profiles}

Lorsque vous accordez à un utilisateur l’accès à une solution d’Adobe spécifique, vous ne souhaitez pas nécessairement lui accorder un accès complet. Les profils de produit permettent à chaque solution d’avoir son propre jeu d’autorisations utilisateur. Elles sont disponibles et accessibles à partir de [Adobe Admin Console](/help/onboarding/learn-concepts/admin-console.md).

Pour en savoir plus sur les [profils de produit AEM en tant que Cloud Service](#aem-product-profiles) et [profils de produit Cloud Manager](#cloud-manager-product-profiles), consultez comment ces profils fonctionnent de concert pendant la configuration de votre équipe.

## Profils de produit AEM en tant que Cloud Service {#aem-product-profiles}

AEM en tant que Cloud Service est l’offre entièrement native du cloud qui fournit AEM en tant que service. Elle fournit l’AEM de manière native au cloud, avec de nouveaux attributs comme toujours activé, toujours à jour, toujours sécurisé et toujours à grande échelle. En même temps, elle conserve la proposition de valeur principale que AEM fournit en tant que plateforme personnalisable aux clients et permet aux équipes de niveau entreprise d’intégrer dans leur procédure de développement et de diffusion. Pour en savoir plus sur AEM en tant que Cloud Service, voir [Présentation d’Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/introduction.html?lang=fr) .

Votre AEM en tant que membre de l’équipe de Cloud Service sera ajoutée et affectée à un ou plusieurs des profils de produit suivants via Admin Console lors de l’intégration.

* **AEM Administrateurs** : Un administrateur AEM est généralement affecté aux développeurs, en particulier les développeurs qui devront avoir accès aux environnements de développement, par exemple. Le profil de produit Administrateurs AEM sera utilisé pour accorder des privilèges d’administrateur à l’instance AEM associée.

* **AEM utilisateurs** : AEM utilisateurs sont les utilisateurs de votre entreprise qui utilisent AEM comme Cloud Service dans le cadre du contrat avec l’Adobe. Ces membres devront accéder à AEM pour effectuer leurs tâches. Le profil de produit Utilisateurs AEM est généralement attribué à un auteur de contenu AEM qui crée et révise le contenu (il peut s’agir de plusieurs types). par exemple, les pages, les ressources, les publications, etc.) avant qu’elles ne soient publiées sur votre site web. Le profil de produit Utilisateurs AEM présenté ci-dessous est attribué à ces membres.

   ![](/help/onboarding/learn-concepts/assets/admin-console-profiles.png)

   >[!NOTE]
   >Chaque utilisateur affecté à un AEM en tant que profil de produit de Cloud Service a (lecture seule) accès à Cloud Manager.

## Profils de produit Cloud Manager {#cloud-manager-product-profiles}

Cloud Manager dispose de profils de produit préconfigurés ou, plus simplement, d’autorisations basées sur les rôles. L’administrateur système est chargé de configurer votre équipe Cloud Manager en attribuant le à ces profils de produit. Il doit se familiariser avec ces profils de produit et avec les membres de l’équipe à qui les affecter.
>[!NOTE]
>Pour plus d’informations, voir [Autorisations basées sur les rôles dans Cloud Manager](/help/onboarding/what-is-required/user-roles-permissions.md).

Chacun des profils de produit est associé à des autorisations spécifiques. Par exemple, si vous êtes dans le rôle d’un :

* **Propriétaire de l’entreprise**, vous avez l’autorisation d’ajouter un nouveau programme ou de modifier un programme, d’ajouter ou de mettre à jour un environnement, d’ajouter/modifier/supprimer le pipeline et d’exécuter n’importe quel pipeline, ainsi que de déployer du code pour AEM la qualité de l’environnement ou du code.

* **Deployment Manager** vous permet d’ajouter ou de mettre à jour un environnement, d’exécuter n’importe quel pipeline et de déployer du code dans AEM environnement ou qualité du code.

* **Développeur**, vous êtes autorisé à générer un jeton d’accès personnel pour accéder à Git.

* **Gestionnaire de programmes**, vous avez l’autorisation de planifier des pipelines, de remplacer les points de contrôle qualité à 3 niveaux et de fournir l’approbation de production.

Un utilisateur peut être affecté à plusieurs profils de produit. Par exemple, l’attribution des rôles Propriétaire de l’entreprise et Responsable de déploiement à un utilisateur leur donne la combinaison ou la somme de ces autorisations.

Votre équipe Cloud Manager comprend au moins :

* Propriétaire de l’entreprise, qui est généralement également administrateur système et qui doit être la première personne à se connecter et accéder à Cloud Manager
* Un responsable de déploiement
* Un développeur

   >[!NOTE]
   >Pour pouvoir accéder à AEM en tant que Cloud Service, les utilisateurs doivent appartenir à l’un des deux profils de produit tels que `AEM Users` ou `AEM Administrators`. Vous devez disposer d’autorisations sur l’instance, mais les autorisations pour administrer Cloud Manager associé ne seront pas suffisantes.