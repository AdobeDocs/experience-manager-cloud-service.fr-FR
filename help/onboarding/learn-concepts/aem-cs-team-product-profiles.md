---
title: Équipe et profils de produit AEM as a Cloud Service
description: Consultez cette page pour en savoir plus sur l’équipe les profils de produit AEM as a Cloud Service.
exl-id: 7b1474c9-aca0-4354-8798-1abdcda2f6dd
source-git-commit: fd23701414a2ae4142ea2a11cef92bc0cb202421
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 94%

---

# Équipe et profils de produit AEM as a Cloud Service {#product-profiles}

## Profils de produit {#profiles}

Lorsque vous accordez à un utilisateur l’accès à une solution Adobe spécifique, vous ne souhaitez pas nécessairement lui accorder un accès complet. Les profils de produit permettent à chaque solution d’avoir son propre jeu d’autorisations utilisateur. Ils sont disponibles et accessibles à partir d’[Adobe Admin Console](/help/onboarding/learn-concepts/admin-console.md).

Lisez davantage sur les [profils de produit AEM as a Cloud Service](#aem-product-profiles) et les [profils de produit Cloud Manager](#cloud-manager-product-profiles) pour comprendre comment ces profils fonctionnent de concert pendant la configuration de votre équipe.

## Profils de produit AEM as a Cloud Service {#aem-product-profiles}

AEM as a Cloud Service est l’offre entièrement native du cloud qui fournit AEM en tant que service. Elle fournit AEM de manière native au cloud, avec de nouveaux attributs comme toujours activé, toujours à jour, toujours sécurisé et toujours à grande échelle. Dans le même temps, elle conserve la proposition de valeur principale qu’AEM fournit en tant que plateforme personnalisable aux clients et permet aux équipes de niveau entreprise d’intégrer dans leur procédure de développement et de diffusion. Pour en savoir plus sur AEM as a Cloud Service, voir [Présentation d’Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/introduction.html?lang=fr).

Vos membres d’équipe AEM as a Cloud Service seront ajoutés et affectés à un ou plusieurs des profils de produit suivants via Admin Console lors de l’intégration.

* **Administrateurs AEM** : un administrateur AEM est généralement affecté aux développeurs, en particulier les développeurs qui devront avoir accès aux environnements de développement, par exemple. Le profil de produit Administrateurs AEM sera utilisé pour accorder des privilèges d’administrateur dans l’instance AEM associée.

* **Utilisateurs AEM** : les utilisateurs AEM sont les utilisateurs de votre entreprise qui utilisent AEM as a Cloud Service dans le cadre du contrat avec Adobe. Ces membres devront accéder à AEM pour effectuer leurs tâches. Le profil de produit Utilisateurs AEM est généralement attribué à un auteur de contenu AEM qui crée et révise le contenu (il peut s’agir de plusieurs types, par exemple, les pages, les ressources, les publications, etc.) avant qu’elles ne soient publiées sur votre site web. Le profil de produit Utilisateurs AEM présenté ci-dessous est attribué à ces membres.

   ![](/help/onboarding/learn-concepts/assets/admin-console-profiles.png)

   >[!NOTE]
   >Chaque utilisateur affecté à un profil de produit AEM as a Cloud Service a un accès (lecture seule) à Cloud Manager.

## Profils de produit Cloud Manager {#cloud-manager-product-profiles}

Cloud Manager dispose de profils de produit préconfigurés ou, plus simplement, d’autorisations basées sur les rôles. L’administrateur système est chargé de configurer votre équipe Cloud Manager en les affectant à ces profils de produit. Il doit se familiariser avec ces profils de produit et avec les membres de l’équipe à qui les affecter.
>[!NOTE]
>Pour plus d’informations, voir [Autorisations basées sur les rôles dans Cloud Manager](/help/onboarding/learn-concepts/cloud-manager-introduction.md##role-based-permissions).

Chacun des profils de produit est associé à des autorisations spécifiques. Par exemple, si vous êtes dans le rôle d’un :

* **Propriétaire dl’entreprise**, vous êtes autorisé à ajouter ou modifier un programme, à ajouter ou mettre à jour un environnement, à ajouter/modifier/supprimer le pipeline et à exécuter n’importe quel pipeline, ainsi qu’à déployer le code dans l’environnement AEM ou gérer la qualité du code.

* **Responsable de déploiement** vous permet d’ajouter ou de mettre à jour un environnement, d’exécuter n’importe quel pipeline et de déployer du code dans AEM environnement ou gérer la qualité du code.

* **Développeur**, vous êtes autorisé à générer un jeton d’accès personnel pour accéder à Git.

* **Gestionnaire de programmes**, vous avez l’autorisation de planifier des pipelines, de remplacer les points de contrôle qualité à 3 niveaux et de fournir l’approbation de production.

Un utilisateur peut être affecté à plusieurs profils de produit. Par exemple, l’attribution des rôles Propriétaire de l’entreprise et Responsable de déploiement à un utilisateur leur donne la combinaison ou la somme de ces autorisations.

Votre équipe Cloud Manager comprend au moins :

* Un propriétaire d’entreprise, qui est généralement également administrateur système et qui doit être la première personne à se connecter et accéder à Cloud Manager
* Un responsable de déploiement
* Un développeur

   >[!NOTE]
   >Pour pouvoir accéder à AEM as a Cloud Service, les utilisateurs doivent appartenir à l’un des deux profils de produit suivants : `AEM Users` ou `AEM Administrators`. Vous devez disposer d’autorisations sur l’instance, mais les autorisations pour administrer le Cloud Manager associé ne seront pas suffisantes.
