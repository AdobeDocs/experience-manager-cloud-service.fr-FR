---
title: Équipe et profils de produit AEM as a Cloud Service
description: Découvrez comment AEM l’équipe as a Cloud Service et les profils de produits et accordez et limitez l’accès à vos solutions d’Adobe sous licence.
exl-id: 7b1474c9-aca0-4354-8798-1abdcda2f6dd
source-git-commit: d54c25791cbb06232ff6e24bb7b8005b366a2144
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 30%

---

# Équipe et profils de produit AEM as a Cloud Service {#product-profiles}

Découvrez comment AEM l’équipe as a Cloud Service et les profils de produits et accordez et limitez l’accès à vos solutions d’Adobe sous licence.

## Profils de produit {#profiles}

Lorsque vous accordez à un utilisateur l’accès à une solution Adobe spécifique, vous ne souhaitez pas nécessairement lui accorder un accès complet. Les profils de produit permettent à chaque solution d’avoir son propre jeu d’autorisations utilisateur. Ils sont disponibles et accessibles à partir d’[ Admin Console.](/help/journey-onboarding/admin-console.md)

## Profils de produit AEM as a Cloud Service {#aem-product-profiles}

AEM as a Cloud Service est une offre entièrement native du cloud qui fournit AEM en tant que service. Elle fournit AEM de manière native au cloud, avec de nouveaux attributs comme toujours activé, toujours à jour, toujours sécurisé et toujours à grande échelle. Dans le même temps, elle conserve la proposition de valeur principale qu’AEM fournit en tant que plateforme personnalisable aux clients et permet aux équipes de niveau entreprise d’intégrer dans leur procédure de développement et de diffusion. Pour en savoir plus sur AEM as a Cloud Service, voir [Présentation d’Adobe Experience Manager as a Cloud Service](/help/overview/introduction.md).

Les membres de votre équipe as a Cloud Service AEM seront ajoutés et affectés à un ou plusieurs des profils de produits suivants via le Admin Console lors de l’intégration.

* **Administrateurs AEM**: Un administrateur d’AEM est généralement affecté aux développeurs, en particulier les développeurs qui doivent avoir accès aux environnements de développement, par exemple. Le profil de produit de l’administrateur AEM sera utilisé pour accorder des privilèges d’administrateur à l’instance AEM associée.

* **Utilisateurs AEM**: Les utilisateurs AEM sont les utilisateurs de votre entreprise qui utilisent AEM as a Cloud Service généralement pour créer du contenu. Ces utilisateurs devront accéder à AEM pour effectuer leurs tâches. Le profil de produit des utilisateurs AEM est généralement attribué à un auteur de contenu AEM qui crée et révise le contenu. Ce contenu peut être de nombreux types tels que des pages, des ressources, des publications, etc. Le profil de produit AEM utilisateurs illustré ci-dessous est attribué à ces membres.

![Profils de produits](/help/onboarding/assets/admin-console-profiles.png)

>[!NOTE]
>
>Chaque utilisateur affecté à un profil de produit AEM as a Cloud Service a un accès (lecture seule) à Cloud Manager.

>[!TIP]
>
>Pour plus d’informations sur le processus d’intégration, reportez-vous à la section [parcours d’intégration.](/help/journey-onboarding/overview.md)

## Profils de produit Cloud Manager {#cloud-manager-product-profiles}

Cloud Manager dispose de profils de produit préconfigurés qui peuvent être considérés comme des autorisations basées sur les rôles. L’administrateur système est chargé de configurer votre équipe Cloud Manager en les affectant à ces profils de produit.

>[!TIP]
>
>Reportez-vous au document [Autorisations basées sur les rôles dans Cloud Manager](/help/onboarding/cloud-manager-introduction.md#role-based-permissions) pour plus d’informations.

Chacun des profils de produit est associé à des autorisations spécifiques.

* **Propriétaire de l’entreprise** - Dans ce rôle, vous avez l’autorisation d’ajouter un nouveau programme ou de modifier un programme, d’ajouter ou de mettre à jour un environnement, de déployer du code dans AEM environnement ou d’exécuter des contrôles qualité du code.
* **Responsable de déploiement** - Dans ce rôle, vous avez l’autorisation d’ajouter ou de mettre à jour un environnement, d’exécuter n’importe quel pipeline, de déployer du code dans AEM environnement ou d’exécuter des contrôles qualité du code.
* **Développeur** - Dans ce rôle, vous avez la permission de générer des jetons d’accès personnels pour accéder à git.
* **Responsable de programme** - Dans ce rôle, vous avez l’autorisation de planifier des pipelines, de remplacer les points de contrôle qualité à 3 niveaux et de fournir une approbation de production.

Un utilisateur peut être affecté à plusieurs profils de produit. Par exemple, si vous attribuez les deux **Propriétaire de l’entreprise** et **Gérer le déploiement** Les rôles d’un utilisateur leur donnent la somme de ces autorisations.

Votre équipe Cloud Manager comprend au moins :

* One **Propriétaire de l’entreprise**, qui est généralement également administrateur système et qui doit être la première personne à se connecter et à accéder à Cloud Manager
* One **Responsable de déploiement**
* One **Développeur**

>[!NOTE]
>
>Pour pouvoir accéder à AEM as a Cloud Service, les utilisateurs doivent appartenir à l’un des deux profils de produit suivants : `AEM Users` ou `AEM Administrators`. Les autorisations d’administration de Cloud Manager ne suffiront pas.
