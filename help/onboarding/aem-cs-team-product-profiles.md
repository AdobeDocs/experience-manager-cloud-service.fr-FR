---
title: Équipe et profils de produits AEM as a Cloud Service
description: Découvrez comment l’équipe et les profils de produits AEM as a Cloud Service accordent et limitent l’accès à vos solutions Adobe sous licence.
exl-id: 7b1474c9-aca0-4354-8798-1abdcda2f6dd
source-git-commit: a3e79441d46fa961fcd05ea54e84957754890d69
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 85%

---


# Équipe et profils de produits AEM as a Cloud Service {#product-profiles}

Découvrez comment l’équipe et les profils de produits AEM as a Cloud Service accordent et limitent l’accès à vos solutions Adobe sous licence.

## Profils de produit {#profiles}

Lorsque vous accordez à un utilisateur l’accès à une solution Adobe spécifique, vous ne souhaitez pas nécessairement lui accorder un accès complet. Les profils de produit permettent à chaque solution d’avoir son propre jeu d’autorisations utilisateur. Ils sont disponibles et accessibles à partir de l’[Admin Console](/help/journey-onboarding/admin-console.md).

## Profils de produit AEM as a Cloud Service {#aem-product-profiles}

AEM as a Cloud Service est une offre entièrement native cloud qui fournit AEM as a service. Elle fournit AEM de manière native au cloud, avec de nouveaux attributs comme toujours activé, toujours à jour, toujours sécurisé et toujours à grande échelle. Dans le même temps, elle conserve la proposition de valeur principale qu’AEM fournit en tant que plateforme personnalisable aux clients et permet aux équipes de niveau entreprise d’intégrer dans leur procédure de développement et de diffusion. Pour en savoir plus sur AEM as a Cloud Service, voir [Présentation d’Adobe Experience Manager as a Cloud Service](/help/overview/introduction.md).

Vos personnes membres de l’équipe d’AEM as a Cloud Service sont ajoutées et affectées à un ou plusieurs des profils de produit suivants via l’Admin Console lors de l’intégration.

* **Administrateurs AEM**: un administrateur d’AEM est généralement affecté aux développeurs, en particulier les développeurs qui ont besoin d’accéder, par exemple, aux environnements de développement. Le profil de produit d’administration d’AEM est utilisé pour accorder des privilèges d’administration dans l’instance AEM associée.

* **Utilisateurs AEM** : les utilisateurs AEM sont les utilisateurs de votre organisation qui utilisent AEM as a Cloud Service généralement pour créer du contenu. Ces utilisateurs doivent accéder à AEM pour effectuer leurs tâches. Le profil de produit des utilisateurs AEM est généralement attribué à un créateur de contenu AEM qui crée et révise le contenu. Ce contenu peut être de nombreux types, tels que des pages, des ressources, des publications, etc. Le profil de produit Utilisateurs AEM présenté ci-dessous est attribué à ces membres.

![Profils de produits](/help/onboarding/assets/admin-console-profiles.png)

>[!NOTE]
>
>Chaque utilisateur/utilisatrice affecté(e) à un profil de produit AEM as a Cloud Service dispose d’un accès en lecture seule à Cloud Manager via le rôle **Utilisateur de Cloud Manager**.
>
>Les utilisateurs disposant uniquement du rôle **Utilisateur de Cloud Manager** peuvent se connecter à Cloud Manager et accéder aux environnements de création AEM (s’ils existent) à l’aide des options de menu **Programmes**. Le rôle **Utilisateur de Cloud Manager** n’est pas suffisant pour accéder aux détails du programme. Si cet accès est nécessaire, les utilisateurs doivent faire appel à leur administrateur/administratrice système pour recevoir des rôles supplémentaires.

>[!WARNING]
>
>Le nom du profil de produit **Administrateurs et administratrices AEM** ne doit pas être modifié. La modification du nom du profil de produit **Administrateurs et administratrices AEM** supprime les droits d’administration de toutes les personnes affectées à ce profil.

>[!TIP]
>
>* Pour en savoir plus sur les profils de produits d’AEM, consultez [Attribuer des profils de produit d’AEM](/help/journey-onboarding/assign-profiles-aem.md).
>* Pour plus d’informations sur le processus d’intégration, voir [parcours d’intégration](/help/journey-onboarding/overview.md).

## Profils de produit Cloud Manager {#cloud-manager-product-profiles}

Cloud Manager dispose de profils de produit préconfigurés qui peuvent être considérés comme des autorisations basées sur les rôles. L’administrateur système est chargé de configurer votre équipe Cloud Manager en affectant ses membres à ces profils de produit.

>[!TIP]
>
>Pour plus d’informations, voir [Autorisations basées sur les rôles dans Cloud Manager](/help/onboarding/cloud-manager-introduction.md#role-based-permissions).

Chacun des profils de produit est associé à des autorisations spécifiques.

* **Propriétaire de l’entreprise**
   * Dans ce rôle, vous avez l’autorisation d’ajouter un nouveau programme ou de modifier un programme, d’ajouter ou de mettre à jour un environnement, de déployer du code dans AEM environnement ou d’exécuter des contrôles qualité du code.
   * Cet utilisateur est chargé de définir les indicateurs de performance clés, d’approuver les déploiements en production et de remplacer les échecs importants à 3 niveaux si nécessaire.
* **Responsable de déploiement**
   * Dans ce rôle, vous avez l’autorisation d’ajouter ou de mettre à jour un environnement, d’exécuter n’importe quel pipeline, de déployer le code dans AEM environnement ou d’exécuter des contrôles qualité du code.
   * Cet utilisateur gère les opérations de déploiement et utilise Cloud Manager pour exécuter des déploiements d’évaluation/de production, modifier les pipelines CI/CD ou approuver des échecs importants à 3 niveaux si nécessaire. Il peut également accéder au référentiel Git.
* **Développeur**
   * Dans ce rôle, vous avez la permission de générer des jetons d’accès personnels pour accéder à git.
   * Cet utilisateur développe et teste des codes d’application personnalisés et utilise principalement Cloud Manager pour afficher l’état du déploiement. Il peut accéder au référentiel Git pour les validations de code.
* **Responsable de programme**
   * Dans ce rôle, vous avez l’autorisation de planifier des pipelines, de remplacer les points de contrôle qualité à trois niveaux et de fournir une approbation de production.
   * Cet utilisateur utilise Cloud Manager pour effectuer la configuration de l’équipe, réviser l’état, afficher les ICP et approuver les échecs importants à 3 niveaux si nécessaire.

Un utilisateur peut être affecté à plusieurs profils de produit. Par exemple, l’attribution des rôles **Propriétaire de l’entreprise** et **Responsable de déploiement** à un utilisateur leur donne la somme de ces autorisations.

Votre équipe Cloud Manager comprend au moins :

* Un **propriétaire d’entreprise**, qui est généralement aussi l’administrateur système et doit être la première personne à se connecter et accéder à Cloud Manager.
* Un **responsable de déploiement**
* Un **développeur**

>[!NOTE]
>
>Pour pouvoir accéder à AEM as a Cloud Service, les utilisateurs doivent appartenir à l’un des deux profils de produit suivants : `AEM Users` ou `AEM Administrators`. Les autorisations d’administration de Cloud Manager ne suffiront pas.

>[!TIP]
>
>* Pour en savoir plus sur les profils de produits Cloud Manager, consultez [Attribuer des membres d’équipe à des profils de produit Cloud Manager](/help/journey-onboarding/assign-profiles-cloud-manager.md).
>* Pour plus d’informations sur le processus d’intégration, voir [parcours d’intégration](/help/journey-onboarding/overview.md).
