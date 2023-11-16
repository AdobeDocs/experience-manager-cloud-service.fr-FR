---
title: Autorisations personnalisées
description: Découvrez comment utiliser des autorisations personnalisées pour créer de nouveaux profils d’autorisation personnalisés avec des autorisations configurables afin de restreindre l’accès aux programmes, aux pipelines et aux environnements pour les utilisateurs responsables de cloud.
exl-id: 167da985-7f19-45b3-90a3-884817907da2
source-git-commit: a3e79441d46fa961fcd05ea54e84957754890d69
workflow-type: tm+mt
source-wordcount: '1506'
ht-degree: 2%

---

# Autorisations personnalisées {#custom-permissions}

Découvrez comment utiliser des autorisations personnalisées pour créer de nouveaux profils d’autorisation personnalisés avec des autorisations configurables afin de restreindre l’accès aux programmes, aux pipelines et aux environnements pour les utilisateurs responsables de cloud.

>[!NOTE]
>
>Cette fonctionnalité n’est disponible que pour [le programme d&#39;adoption précoce.](/help/implementing/cloud-manager/release-notes/current.md#early-adoption)

## Présentation {#introduction}

Cloud Manager dispose d’un ensemble de rôles prédéfinis qui régissent l’accès aux différentes fonctionnalités de Cloud Manager :

* Propriétaire de l’entreprise
* Responsable de programme
* Responsable de déploiement
* Développeur

Les autorisations personnalisées permettent aux utilisateurs de créer de nouveaux profils d’autorisation personnalisés avec des autorisations configurables afin de restreindre l’accès des utilisateurs responsables du cloud aux programmes, aux pipelines et aux environnements.

>[!TIP]
>
>Pour plus d’informations sur les rôles prédéfinis, consultez le document [AEM l’équipe as a Cloud Service et les profils de produit.](/help/onboarding/aem-cs-team-product-profiles.md)

## Utilisation d’autorisations personnalisées {#using}

Pour créer et utiliser vos propres autorisations personnalisées, trois étapes sont nécessaires :

1. [Créez un profil de produit.](#create)
1. [Attribuez des autorisations personnalisées au nouveau profil de produit.](#assign-permissions)
1. [Affectez des utilisateurs au nouveau profil de produit.](#assign-users)

Cette section décrit ces étapes. Il peut s’avérer utile de consulter la section [Termes](#terms) et [Autorisations configurables](#configurable-permissions) lors de la création de vos propres autorisations personnalisées.

>[!NOTE]
>
>Pour qu’Adobe Experience Manager as a Cloud Service puisse créer de nouveaux profils et gérer les autorisations de Cloud Manager, vous devez disposer de droits d’administrateur de produit dans Admin Console.

### Création d’un profil de produit {#create}

Vous devez d’abord créer un profil de produit auquel vous pourrez attribuer des autorisations personnalisées.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)

1. Sur la page d’entrée de Cloud Manager, appuyez ou cliquez sur le bouton **Gérer l’accès** button

![Bouton Gérer l’accès](assets/manage-access.png)

1. Vous êtes redirigé vers le **Produits** de l’onglet du Admin Console, dans lequel vous pouvez gérer les utilisateurs et les autorisations de cloud manager. Dans le Admin Console, appuyez ou cliquez sur le **Nouveau profil** bouton .

![Bouton Nouveau profil](assets/admin-console-new-profile.png)

1. Fournissez les détails généraux du profil.

   * **Nom du profil de produit** : nom descriptif du profil.
   * **Nom d’affichage** : nom abrégé qui s’affichera dans l’interface utilisateur (options)
   * **Description** - Description informative du profil expliquant son objectif (facultatif)
   * **Notifier les utilisateurs par courrier électronique** - Lorsque cette option est sélectionnée, les utilisateurs sont avertis par e-mail lorsqu’ils sont ajoutés ou supprimés de ce profil.

1. Appuyez ou cliquez sur **Enregistrer** une fois terminé.

Le nouveau profil de produit est enregistré et visible dans la liste des profils de produit dans le Admin Console.

### Attribution d’autorisations personnalisées à Profile {#assign-permissions}

Maintenant que vous disposez d’un nouveau profil de produit, vous pouvez lui attribuer des autorisations personnalisées.

1. Dans le Admin Console, appuyez ou cliquez sur le nom de la variable [nouveau profil de produit que vous venez de créer.](#create)

1. Dans la fenêtre qui s’ouvre, sélectionnez l’option **Autorisations** pour afficher une liste des autorisations modifiables.

   ![Autorisations modifiables](assets/permissions-tab.png)

1. Appuyez ou cliquez sur le bouton **Modifier** lien d’une autorisation pour la modifier.

1. La variable **Modifier les autorisations** s’ouvre.
   * L’autorisation sélectionnée à l’étape précédente est sélectionnée dans la colonne de gauche.
   * Les éléments d’autorisation disponibles pour l’attribution de l’autorisation se trouvent dans la colonne centrale intitulée **Autorisation disponible** Éléments.
   * Les éléments d’autorisation affectés se trouvent dans la colonne de droite intitulée **Éléments d’autorisation inclus**.

   ![Modification des éléments d’autorisation](assets/edit-permission-items.png)

1. Appuyez ou cliquez sur le signe plus (`+`) en regard de l’élément d’autorisation pour l’ajouter à la colonne **Éléments d’autorisation inclus**.

   * Appuyez ou cliquez sur le bouton `i` en regard d’un élément d’autorisation pour en savoir plus.

1. Appuyez ou cliquez sur le bouton **Tout ajouter** en haut de la page **Autorisations disponibles** pour ajouter toutes les autorisations.

1. Si le profil doit toujours comporter tous les éléments d’autorisation, pensez à utiliser la variable **Inclure automatiquement** .

   * **Activé** - Tous les éléments d’autorisation actuels et les futurs éléments d’autorisation seront déplacés vers les éléments d’autorisation inclus et, à l’enregistrement, seront applicables en conséquence.
   * **Off** - Tous les éléments d’autorisation seront déplacés vers les éléments d’autorisation disponibles et, lors de l’enregistrement, seront applicables en conséquence.

1. Appuyez ou cliquez sur **Enregistrer** lorsque vous avez terminé de définir les éléments d’autorisation pour votre nouveau profil de produit.

Votre nouveau profil de produit est maintenant enregistré avec ses autorisations personnalisées.

### Affectation d’utilisateurs aux autorisations personnalisées {#assign-users}

Vous pouvez désormais affecter des utilisateurs au nouveau profil de produit que vous avez créé avec des autorisations personnalisées.

1. Dans le Admin Console, appuyez ou cliquez sur le nom de la variable [nouveau profil de produit auquel vous venez d’attribuer des autorisations personnalisées.](#assign-permissions)

1. Dans la fenêtre qui s’ouvre, sélectionnez l’option **Utilisateurs** .

1. Appuyez ou cliquez sur le bouton **Ajout d’utilisateurs** et affecter des utilisateurs à votre nouveau profil de produit avec des autorisations personnalisées.

Consultez la section **Ajout d’utilisateurs et de groupes d’utilisateurs à un profil de produit** du document [Gestion des profils de produit pour les utilisateurs d’entreprise](https://helpx.adobe.com/fr/enterprise/using/manage-product-profiles.html) pour plus d’informations sur l’utilisation du Admin Console.

## Autorisations configurables {#configurable-permissions}

Les autorisations suivantes sont disponibles pour créer des profils personnalisés.

| Autorisation | Description |
|---|---|
| Création de programme | Autoriser les utilisateurs à créer un programme |
| Accès au programme | Autoriser les utilisateurs à accéder aux programmes |
| Édition de programme | Autoriser les utilisateurs à modifier des programmes |
| Création d’environnement | Autoriser les utilisateurs à créer un environnement |
| Modification de l’environnement | Autoriser les utilisateurs à mettre à jour et à modifier des environnements |
| Journaux d’environnement lus | Autoriser les utilisateurs à lire les journaux d’environnement |
| Création d’un pipeline | Autoriser les utilisateurs à créer des pipelines |
| Suppression de pipeline | Autorisation de la suppression des pipelines par les utilisateurs |
| Modification du pipeline | Autoriser les utilisateurs à modifier les pipelines |
| Approuver/Rejeter les déploiements de production | Autoriser les utilisateurs à approuver ou rejeter une étape de déploiement en production |
| Annulation des exécutions de pipeline | Autoriser les utilisateurs à annuler les exécutions de pipeline |
| Démarrage des exécutions de pipeline | Autoriser les utilisateurs à démarrer une nouvelle exécution de pipeline |
| Échecs de mesures importantes de remplacement/rejet | Autoriser les utilisateurs à remplacer/rejeter les échecs de mesures importantes |
| Planification des déploiements en production | Autorisation des utilisateurs à planifier une étape de déploiement en production |
| Accès aux informations sur le référentiel | Autoriser les utilisateurs à accéder aux informations du référentiel et à générer un mot de passe d’accès |

### Autorisations au niveau de l’organisation {#organization-level}

Les autorisations au niveau de l’organisation se rapportent aux autorisations qui sont toujours accordées à tous les programmes d’une organisation.

Les autorisations suivantes sont des autorisations au niveau de l’organisation :

* **Création de programme** - Cette autorisation permet aux utilisateurs de créer un programme dans l’organisation.
* **Accès aux informations sur le référentiel** Cette autorisation au niveau du client/de l’organisation permet aux utilisateurs de générer le nom d’utilisateur, le mot de passe et l’URL du référentiel pour accéder au projet client et contribuer à ce dernier.
   * Le nom d’utilisateur et le mot de passe pour l’accès au référentiel seront communs à tous les référentiels dans l’organisation, mais l’URL du référentiel sera unique à chaque programme.
   * Consultez le document [Accès aux référentiels](/help/implementing/cloud-manager/managing-code/accessing-repos.md) pour plus d’informations.

## Termes {#terms}

Les termes suivants sont utilisés pour créer et gérer des autorisations personnalisées et des rôles prédéfinis.

| Terme | Description |
|---|---|
| Autorisations prédéfinies | Rôles prédéfinis tels que **Propriétaire de l’entreprise**, **Responsable de déploiement**, etc. pour régir différentes fonctionnalités de Cloud Manager. Pour plus d’informations sur les rôles prédéfinis, consultez le document [AEM l’équipe as a Cloud Service et les profils de produit.](/help/onboarding/aem-cs-team-product-profiles.md) |
| Autorisations personnalisées | Fonctionnalités de Cloud Manager qui permettent aux utilisateurs de créer des profils d’autorisation pour définir des rôles pour régir les fonctionnalités prises en charge de Cloud Manager |
| Profil du produit | Créé dans la console d’administration pour gérer les autorisations configurables qui s’appliqueront aux utilisateurs faisant partie du profil d’autorisation. |
| Autorisations configurables | Autorisations de Cloud Manager qui peuvent être configurées dans le profil d’autorisation |
| Élément d’autorisation | Ressource de programme, d’environnement ou de pipeline sur laquelle une autorisation peut être appliquée |

Les éléments d’autorisation se rapportent à la portée dans laquelle l’autorisation sera appliquée. En règle générale, il s’agit de l’un des suivants.

| Type d’élément d’autorisation | Exemple | Description |
|---|---|---|
| Organisation | organisation:companyA | Toutes les ressources applicables d’une organisation. Une ressource peut être un programme, un environnement ou un pipeline. Si l’utilisateur ajoute une organisation pour n’importe quelle autorisation, toutes les nouvelles ressources de cette organisation auront également cette autorisation. |
| Programme | Programme A | Toutes les ressources applicables d&#39;un programme |
| Environnement | Programme A : environnement | Applicable dans un environnement spécifique |
| Pipeline | Programme A : pipeline | Applicable sur un pipeline spécifique |

## Limites {#limitations}

Gardez à l’esprit les restrictions suivantes lors de l’utilisation d’autorisations personnalisées.

* Le profil d’autorisations personnalisées répertorie également les programmes, les environnements et les pipelines AMS lors de la configuration des autorisations.
* Ressources telles que le programme, l’environnement, le pipeline, etc. la création dans Cloud Manager peut prendre deux minutes pour s’afficher dans Admin Console pour la configuration des autorisations.
* Dans de rares cas où le service d’autorisations personnalisées ne répond pas, les profils prédéfinis sont toujours disponibles et les utilisateurs des profils prédéfinis disposent toujours d’un accès approprié.

## Questions fréquentes {#faq}

### Quels profils d’autorisation sont des profils d’autorisation prédéfinis ?

* Propriétaire de l’entreprise
* Responsable de programme
* Responsable de déploiement
* Développeur

Pour plus d’informations sur les rôles prédéfinis, consultez le document [AEM l’équipe as a Cloud Service et les profils de produit.](/help/onboarding/aem-cs-team-product-profiles.md)

### Qu’advient-il des profils d’autorisation prédéfinis avec l’introduction aux profils personnalisés ?

Les profils de produit et les rôles de responsable de cloud par défaut continuent de fonctionner de la même manière qu’auparavant.

### Puis-je modifier des profils d’autorisation prédéfinis ?

Non, les profils par défaut ne sont pas modifiables. Vous ne pouvez pas ajouter ni supprimer d’autorisations au profil d’autorisation par défaut. Vous pouvez uniquement ajouter ou supprimer des utilisateurs de profils prédéfinis.

### Dois-je supprimer les profils d’autorisation prédéfinis puisque les profils personnalisés sont désormais disponibles ?

Les profils d’autorisation prédéfinis ne doivent pas être supprimés du Admin Console.

### Puis-je ajouter des utilisateurs à plusieurs profils d’autorisation ?

Oui, un utilisateur peut faire partie de plusieurs profils, y compris des profils d’autorisation prédéfinis et personnalisés. Lorsqu’un utilisateur est affecté à plusieurs profils, les autorisations combinées de tous les profils d’autorisation attribués lui seront disponibles.

### Que se passe-t-il si un utilisateur est autorisé à modifier un environnement/pipeline mais n’a pas accès à un programme contenant l’environnement/le pipeline ?

Dans ce cas, l’utilisateur ne pourra pas accéder à l’environnement ou au pipeline s’il ne dispose pas de la variable **Accès au programme** autorisations contenant l’environnement ou le pipeline.
