---
title: Autorisations personnalisées
description: Découvrez comment utiliser des autorisations personnalisées pour créer des profils d’autorisation personnalisés avec des autorisations configurables afin de restreindre l’accès aux programmes, aux pipelines et aux environnements pour les utilisateurs responsables de cloud.
exl-id: 167da985-7f19-45b3-90a3-884817907da2
solution: Experience Manager
feature: Security, Developing
role: Admin, Architect, Developer
source-git-commit: 5d6d3374f2dd95728b2d3ed0cf6fab4092f73568
workflow-type: tm+mt
source-wordcount: '1515'
ht-degree: 46%

---


# Autorisations personnalisées {#custom-permissions}

Découvrez comment utiliser des autorisations personnalisées pour créer des profils d’autorisation personnalisés avec des autorisations configurables afin de restreindre l’accès aux programmes, aux pipelines et aux environnements pour les utilisateurs responsables de cloud.

## Présentation {#introduction}

Cloud Manager dispose d’un ensemble de rôles prédéfinis qui régissent l’accès aux différentes fonctionnalités de Cloud Manager :

* Propriétaire de l’entreprise
* Responsable de programme
* Responsable de déploiement
* Développeur

Les autorisations personnalisées permettent aux utilisateurs de créer des profils d’autorisation personnalisés avec des autorisations configurables afin de restreindre l’accès des utilisateurs responsables du cloud aux programmes, aux pipelines et aux environnements.

>[!TIP]
>
>Pour plus d’informations sur les rôles prédéfinis, voir [Équipe AEM as a Cloud Service et Profils de produit](/help/onboarding/aem-cs-team-product-profiles.md).

## Utiliser les autorisations personnalisées {#using}

Pour créer et utiliser vos propres autorisations personnalisées, trois étapes sont nécessaires :

1. [Créez un profil de produit](#create).
1. [Attribuez des autorisations personnalisées au profil de produit](#assign-permissions).
1. [ Affectez des utilisateurs au profil de produit ](#assign-users).

Cette section décrit ces étapes en détails. Il peut s’avérer utile d’afficher les sections [Termes](#terms) et [Autorisations configurables](#configurable-permissions) lorsque vous créez vos propres autorisations personnalisées.

>[!NOTE]
>
>Pour qu’Adobe Experience Manager as a Cloud Service puisse créer des profils et gérer des autorisations pour Cloud Manager, vous devez disposer de droits d’administrateur de produit dans Admin Console.

### Créer un profil de produit {#create}

Commencez par créer un profil de produit auquel vous pourrez attribuer des autorisations personnalisées.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/).

1. Sur la page d’entrée Cloud Manager, cliquez sur le bouton **Gérer l’accès** .

![Bouton Gérer l’accès](assets/manage-access.png)

1. Une redirection vers l’onglet **Produits** de l’Admin Console se produit, dans lequel vous pouvez gérer les utilisateurs et utilisatrices et les autorisations de Cloud Manager. Dans l’Admin Console, cliquez sur le bouton **Nouveau profil** .

![Bouton Nouveau profil.](assets/admin-console-new-profile.png)

1. Fournissez les détails généraux du profil.

   * **Nom du profil de produit** : un nom descriptif du profil.
   * **Nom d’affichage** : nom abrégé affiché dans l’interface utilisateur (options)
   * **Description** : une description informative du profil expliquant son objectif (facultatif).
   * **Avertir les utilisateurs par e-mail** - Lorsqu’ils sont sélectionnés, les utilisateurs sont avertis par e-mail lorsqu’ils sont ajoutés ou supprimés de ce profil.

1. Sélectionnez **Enregistrer** une fois l’opération terminée.

Le nouveau profil de produit est enregistré et visible dans la liste des profils de produits dans l’Admin Console.

### Attribuer des autorisations personnalisées au profil {#assign-permissions}

Maintenant que vous disposez d’un nouveau profil de produit, vous pouvez lui attribuer des autorisations personnalisées.

1. Dans l’Admin Console, sélectionnez le nom du [nouveau profil de produit que vous avez créé](#create).

1. Dans la fenêtre qui s’ouvre, sélectionnez l’onglet **Autorisations** pour afficher la liste des autorisations modifiables.

   ![Autorisations modifiables.](assets/permissions-tab.png)

1. Sélectionnez le lien **Modifier** d&#39;une autorisation afin que vous puissiez la modifier.

1. La fenêtre **Modifier l’autorisation** s’ouvre.
   * L’autorisation que vous avez sélectionnée à l’étape précédente est sélectionnée dans la colonne de gauche.
   * Les éléments d’autorisation disponibles pour l’affectation de l’autorisation se trouvent dans la colonne du milieu intitulée **Autorisations disponibles**.
   * Les éléments d’autorisation attribués se trouvent dans la colonne de droite intitulée **Éléments d’autorisation inclus**.

   ![Modification des éléments d’autorisation](assets/edit-permission-items.png)

1. Sélectionnez l’icône plus (`+`) en regard de l’élément d’autorisation afin que vous puissiez l’ajouter à la colonne **Éléments d’autorisation inclus**.

   * Sélectionnez l’icône `i` en regard d’un élément d’autorisation si vous souhaitez en savoir plus à ce sujet.

1. Sélectionnez le bouton **Ajouter tout** en haut de la colonne **Autorisations disponibles** afin de pouvoir ajouter toutes les autorisations.

1. Sélectionnez **Enregistrer** lorsque vous avez terminé de définir les éléments d’autorisation de votre nouveau profil de produit.

Votre nouveau profil de produit est maintenant enregistré avec ses autorisations personnalisées.

### Affecter des personnes aux autorisations personnalisées {#assign-users}

Vous pouvez désormais affecter des personnes au nouveau profil de produit que vous avez créé avec des autorisations personnalisées.

1. Dans l’Admin Console, sélectionnez le nom du [nouveau profil de produit auquel vous avez attribué des autorisations personnalisées](#assign-permissions).

1. Dans la fenêtre qui s’ouvre, sélectionnez l’onglet **Utilisateurs et utilisatrices**.

1. Sélectionnez le bouton **Ajouter des utilisateurs** et affectez des utilisateurs à votre nouveau profil de produit avec des autorisations personnalisées.

Pour plus d’informations sur l’utilisation de l’Admin Console, reportez-vous à la section **Ajout d’utilisateurs et de groupes d’utilisateurs à un profil de produit** du document [Gestion des profils de produit pour les utilisateurs d’entreprise](https://helpx.adobe.com/fr/enterprise/using/manage-product-profiles.html).

## Autorisations configurables {#configurable-permissions}

Les autorisations suivantes sont disponibles pour créer des profils personnalisés.

| Autorisation | Description |
|---|---|
| Création de programme | Autoriser les utilisateurs à créer un programme |
| Accès au programme | Autoriser des personnes à accéder aux programmes |
| Modification du programme | Autoriser les personnes à modifier des programmes |
| Création d’environnement | Autoriser les utilisateurs à créer un environnement |
| Modification de l’environnement | Autoriser les utilisateurs à mettre à jour et à modifier des environnements |
| Journaux d’environnement lus | Autoriser les utilisateurs à lire les journaux d’environnement |
| Gestion des variables d’environnement | Autoriser les utilisateurs à créer/modifier/supprimer des configurations d’environnement |
| Création d’une restauration d’environnement | Autoriser les utilisateurs à créer une restauration de l’environnement |
| Réinitialisation de l’environnement de développement rapide | Autoriser les utilisateurs à réinitialiser l’environnement de développement rapide |
| Gestion de la copie de contenu | Autoriser les personnes à gérer les opérations de copie de contenu |
| Création d’un pipeline | Autorisation des utilisateurs à créer des pipelines |
| Suppression de pipeline | Autoriser les personnes à supprimer des pipelines |
| Modification du pipeline | Autoriser les personnes à modifier les pipelines |
| Approbation et rejet des déploiements de production | Autoriser les personnes à approuver ou rejeter une étape de déploiement en production |
| Annulation des exécutions de pipeline | Autoriser les personnes à annuler les exécutions de pipeline |
| Démarrage des exécutions de pipeline | Autoriser les utilisateurs à démarrer une nouvelle exécution de pipeline |
| Remplacement et rejet d’échecs de mesures importantes | Autoriser les personnes à remplacer et à rejeter les échecs de mesures importantes |
| Planification des déploiements en production | Autoriser des personnes à planifier une étape de déploiement en production |
| Accès aux informations sur le référentiel | Autoriser les personnes à accéder aux informations du référentiel et à générer un mot de passe d’accès |
| Création de référentiel | Autoriser les utilisateurs à créer des référentiels Git |
| Suppression de référentiel | Autoriser les personnes à supprimer des référentiels Git |
| Modification de référentiel | Autoriser les personnes à modifier les référentiels Git |
| Génération de code de référentiel | Autoriser les personnes à générer des projets à partir de l’archétype |
| Gestion des noms de domaine | Autoriser les utilisateurs à créer/modifier/supprimer des noms de domaine |
| Gestion des Listes autorisées IP | Autoriser les utilisateurs à créer/modifier/supprimer des liaisons de liste autorisée IP et de liste autorisée IP |
| Gestion de l’infrastructure réseau | Autoriser les utilisateurs à créer/modifier/supprimer une infrastructure réseau |
| Gestion des certificats SSL | Autoriser les utilisateurs à créer/modifier/supprimer un certificat SSL |
| Gestion des utilisateurs du sous-compte New Relic | Autoriser les utilisateurs à lire/modifier les utilisateurs de sous-comptes New Relic |

### Autorisations au niveau de l’organisation {#organization-level}

Les autorisations au niveau de l’organisation se rapportent aux autorisations qui sont toujours accordées à tous les programmes d’une organisation.

Les autorisations suivantes sont des autorisations au niveau de l’organisation :

* **Création de programme** - Cette autorisation permet aux utilisateurs de créer un programme dans l’organisation.
* **Accès aux informations du référentiel** Cette autorisation au niveau du client/de l’organisation permet aux utilisateurs de générer le nom d’utilisateur, le mot de passe et l’URL du référentiel pour accéder au projet client et contribuer à ce dernier.
   * Le nom d’utilisateur et le mot de passe pour l’accès au référentiel sont communs à tous les référentiels dans l’organisation, mais l’URL du référentiel est unique à chaque programme.
   * Pour plus d’informations, voir [Accès aux référentiels](/help/implementing/cloud-manager/managing-code/accessing-repos.md) .

## Termes {#terms}

Les termes suivants sont utilisés pour créer et gérer des autorisations personnalisées et des rôles prédéfinis.

| Terme | Description |
|---|---|
| Autorisations prédéfinies | Rôles prédéfinis tels que **Propriétaire de l’entreprise** et **Responsable de déploiement** pour régir différentes fonctionnalités de Cloud Manager. Pour plus d’informations sur les rôles prédéfinis, voir [Équipe AEM as a Cloud Service et Profils de produit](/help/onboarding/aem-cs-team-product-profiles.md). |
| Autorisations personnalisées | Les fonctionnalités de Cloud Manager permettent aux utilisateurs de créer des profils d’autorisation pour définir des rôles pour régir les fonctionnalités prises en charge par Cloud Manager. |
| Profil de produits | Créé dans Admin Console pour gérer les autorisations configurables qui s’appliqueront aux utilisateurs et utilisatrices faisant partie du profil d’autorisation. |
| Autorisation configurable | Autorisations de Cloud Manager qui peuvent être configurées dans le profil d’autorisation. |
| Élément d’autorisation | Un programme, un environnement ou une ressource de pipeline sur lequel une autorisation peut être appliquée |

Les éléments d’autorisation se rapportent à la portée dans laquelle l’autorisation est appliquée. En règle générale, il s’agit de l’un des éléments suivants.

| Type d’élément d’autorisation | Exemple | Description |
|---|---|---|
| Organisation | Organisation:entrepriseA | Toutes les ressources applicables d’une organisation. Une ressource peut être un programme, un environnement ou un pipeline. Si l’utilisateur ou l’utilisatrice ajoute une organisation pour n’importe quelle autorisation, toutes les nouvelles ressources de cette organisation auront également cette autorisation. |
| Programme | Programme A | Toutes les ressources applicables d’un programme |
| Environnement | Programme A : environnement | Applicable dans un environnement spécifique |
| Pipeline | Programme A : pipeline | Applicable sur un pipeline spécifique |

## Limites {#limitations}

Gardez à l’esprit les restrictions suivantes lors de l’utilisation d’autorisations personnalisées.

* Le profil d’autorisations personnalisées répertorie également les programmes, les environnements et les pipelines AMS lors de la configuration des autorisations.
* Les ressources telles que le programme, l’environnement et le pipeline créés dans Cloud Manager peuvent prendre deux minutes pour s’afficher dans Admin Console pour la configuration des autorisations.
* Dans de rares cas où le service d’autorisations personnalisées ne répond pas, les profils prédéfinis sont toujours disponibles et les utilisateurs et utilisatrices des profils prédéfinis disposent toujours d’un accès approprié.

## Questions fréquentes {#faq}

### Quels profils d’autorisation sont des profils d’autorisation prédéfinis ?

* Propriétaire de l’entreprise
* Responsable de programme
* Responsable de déploiement
* Développeur

Pour plus d’informations sur les rôles prédéfinis, voir [Équipe AEM as a Cloud Service et Profils de produit](/help/onboarding/aem-cs-team-product-profiles.md).

### Qu’advient-il des profils d’autorisation prédéfinis lors de l’introduction de profils personnalisés ?

Les profils de produits et les rôles de Cloud Manager par défaut continuent de fonctionner comme auparavant.

### Puis-je modifier des profils d’autorisation prédéfinis ?

Non, les profils par défaut ne sont pas modifiables. Vous ne pouvez pas ajouter d’autorisations au profil d’autorisation par défaut, ni les supprimer de celui-ci. Vous pouvez uniquement ajouter ou supprimer des utilisateurs et utilisatrices aux/des profils prédéfinis.

### Dois-je supprimer les profils d’autorisation prédéfinis puisque les profils personnalisés sont désormais disponibles ?

Ne supprimez pas les profils d’autorisation prédéfinis de l’Admin Console.

### Puis-je ajouter des utilisateurs et utilisatrices à plusieurs profils d’autorisation ?

Oui, un utilisateur ou une utilisatrice peut faire partie de plusieurs profils, y compris des profils d’autorisation prédéfinis et personnalisés. Lorsqu’une personne est affectée à plusieurs profils, les autorisations combinées de tous les profils d’autorisation affectés lui seront disponibles.

### Que se passe-t-il si une personne est autorisée à modifier un environnement/pipeline mais n’a pas accès à un programme contenant l’environnement/le pipeline ?

Dans ce cas, l’utilisateur ne peut pas accéder à l’environnement ou au pipeline s’il ne dispose pas des autorisations **Accès au programme** contenant l’environnement ou le pipeline.
