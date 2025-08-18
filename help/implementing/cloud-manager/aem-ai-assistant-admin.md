---
title: Configuration de l’assistant d’IA dans Adobe Experience Manager
description: Découvrez comment installer et configurer l’assistant AI à l’aide d’Admin Console dans Adobe Experience Manager.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
exl-id: a7f3dc14-29f7-473a-9870-d52393e6fa6e
source-git-commit: e853e7b46c762ab724d5eecb344897a83e4fb724
workflow-type: tm+mt
source-wordcount: '950'
ht-degree: 3%

---

# Configuration de l’assistant d’IA dans Adobe Experience Manager {#aem-ai-asst-admin-setup}

Un administrateur doit configurer l’accès, les autorisations et les paramètres pour que les utilisateurs de son entreprise puissent utiliser les fonctionnalités de l’assistant AI d’AEM (Adobe Experience Manager).

Le processus de configuration de l’assistant d’IA d’AEM comprend les étapes suivantes :

1. [Création d’un profil de produit dans le Adobe Admin Console](#create-profile).
1. [Activez l’autorisation Connaissance des produits de l’assistant AI](#enable-permission).
1. [Créez un groupe d’utilisateurs (ou utilisez un groupe d’utilisateurs existant)](#create-user-group).
1. [Ajoutez des utilisateurs au groupe d’utilisateurs](#add-users).
1. [Attribuer le profil de produit au groupe d’utilisateurs](#assign-product-profile).

**Conditions préalables**

Avant de commencer, assurez-vous d’avoir satisfait aux conditions préalables suivantes :

* Vous devez disposer au minimum des droits d’administrateur de produit dans Adobe Admin Console.
* Vous avez une compréhension de la structure de gestion des utilisateurs de votre entreprise.

**Considérations relatives à la configuration**

* Temps de traitement : l’affichage des ressources créées dans Cloud Manager peut prendre jusqu’à 2 minutes dans Admin Console pour la configuration des autorisations.
* Profils multiples : les utilisateurs peuvent faire partie de plusieurs profils et les autorisations sont combinées à partir de tous les profils attribués.
* Portée de l’organisation : certaines autorisations peuvent s’appliquer au niveau de l’organisation dans tous les programmes.
* Profils prédéfinis : ne supprimez pas les profils d’autorisation prédéfinis d’Admin Console.


## 1 - Création d’un profil de produit dans Adobe Admin Console{#create-profile}

1. Suivez les instructions détaillées de la section [Création d’un profil de produit dans Adobe Admin Console](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/ui/create-profile) disponible dans la documentation d’Experience Platform.

1. Lors de la création du profil de produit, vous pouvez utiliser les valeurs suggérées suivantes pour l’assistant AI.

   | Champ de texte | Valeur suggérée |
   | --- | --- |
   | Nom du profil de produit | `AEM AI Assistant` (ou votre nom descriptif préféré) |
   | Nom d’affichage (facultatif) | `AI Assistant` |
   | Description (facultative) | `Product profile for managing AEM AI Assistant access` |
   | Notification | Configuration d’en fonction des préférences de votre organisation |


## 2 - Activer l’autorisation Connaissance des produits de l’assistant IA{#enable-permission}

Le processus d’attribution d’autorisations personnalisées aux profils de produit suit le processus standard des autorisations personnalisées d’Adobe Cloud Manager .

Article de référence : [Attribuer des autorisations personnalisées au nouveau profil de produit](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/requirements/custom-permissions#assign-permissions)

1. Dans Admin Console, cliquez sur le nom de votre profil de produit nouvellement créé (`AEM AI Assistant`)

   ![Capture d’écran](/help/implementing/cloud-manager/assets/ai-assistant-console.png)

1. Pour afficher la liste des autorisations modifiables, cliquez sur l’onglet **Autorisations**.

1. Dans la liste des tableaux, recherchez l’autorisation `AI Assistant Product Knowledge`.

   ![Onglet Autorisations de l’assistant AI dans Admin Console](/help/implementing/cloud-manager/assets/ai-assistant-permission.png)

1. À droite du nom de l’autorisation, cliquez sur ![icône Crayon ou icône Modifier](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg).

1. Sur la page **Modifier les autorisations pour l’assistant AI**, activez le bouton (bascule) **Connaissance des produits de l’assistant AI**.

   ![Page Modifier les autorisations pour l’option de basculement Connaissance du produit de l’assistant IA ](/help/implementing/cloud-manager/assets/ai-assistant-prod-knowledge.png)

1. Dans le coin inférieur droit de la page, cliquez sur **Enregistrer**.

   L’autorisation Connaissance des produits de l’assistant AI est désormais activée pour votre profil de produit.


## 3 - Créez un groupe d’utilisateurs (ou utilisez un groupe d’utilisateurs existant){#create-user-group}

1. Utilisez l’une des méthodes suivantes :

>[!BEGINTABS]

>[!TAB Créer un groupe d’utilisateurs]

1. Dans Admin Console, cliquez sur **Utilisateurs** > **Groupes d’utilisateurs**.

   ![Groupes d’utilisateurs](/help/implementing/cloud-manager/assets/ai-assistant-user-groups.png)

1. Sur la page **Groupes d’utilisateurs**, cliquez sur **Nouveau groupe d’utilisateurs**.

   ![Bouton Nouveau groupe d’utilisateurs sur la page Groupes d’utilisateurs](/help/implementing/cloud-manager/assets/ai-assistant-new-user-group.png)

1. Sur la page **Créer un groupe d’utilisateurs** fournissez les informations suivantes :

   | Option | Valeur suggérée |
   | --- | --- |
   | Nom du groupe d’utilisateurs | `AEM AI Assistant` (ou votre nom préféré) |
   | Description (facultative) | `User group for managing AEM AI Assistant access` |

   ![Créer une page de groupe d’utilisateurs](/help/implementing/cloud-manager/assets/ai-assistant-create-new-user-group.png)

1. Dans le coin inférieur droit de la page, cliquez sur **Enregistrer**.

>[!TAB Utiliser un groupe d’utilisateurs existant]

Vous pouvez utiliser un groupe d’utilisateurs AEM existant s’il répond aux exigences d’accès des assistants AI, au lieu d’en créer un nouveau.

>[!ENDTABS]

## 4 - Ajouter des utilisateurs au groupe d’utilisateurs{#add-users}

1. Utilisez l’une des méthodes suivantes :

>[!BEGINTABS]

>[!TAB Ajouter des utilisateurs individuels]

1. Sur la page **Groupes d’utilisateurs**, dans le tableau **Nom du groupe**, cliquez sur le nom du groupe d’utilisateurs que vous venez de créer ou sur un nom de groupe d’utilisateurs existant.

   ![Page de groupes d’utilisateurs affichant le nom du groupe d’utilisateurs de l’assistant AEM AI dans le tableau](/help/implementing/cloud-manager/assets/ai-assistant-user-group-name-in-table.png)

1. Sur la page **Groupes d’utilisateurs** de l’**assistant AEM AI**, cliquez sur l’onglet **Utilisateurs**, puis sur **Ajouter des utilisateurs**.

   ![Page des groupes d’utilisateurs de l’assistant AEM AI, affichant l’onglet Utilisateurs et le bouton Ajouter des utilisateurs](/help/implementing/cloud-manager/assets/ai-assistant-add-users.png)

1. Sur la page **`Add users to this user group`**, recherchez et sélectionnez les utilisateurs qui doivent accéder à l’assistant AEM AI.

   ![Ajouter des utilisateurs à cette page de groupe d’utilisateurs](/help/implementing/cloud-manager/assets/ai-assistant-add-users-to-this-group.png)

1. Dans le coin inférieur droit de la page, cliquez sur **Enregistrer**.
1. Affectez maintenant le profil de produit au groupe d’utilisateurs](#assign-product-profile).

>[!TAB Ajout d’utilisateurs en bloc]

Vous pouvez utiliser la fonction de chargement en bloc dans Admin Console.

1. Préparez un fichier CSV contenant des informations sur l’utilisateur.
1. Utilisez l’option **`Add users by CSV`** pour un ajout en bloc efficace.
1. Affectez maintenant le profil de produit au groupe d’utilisateurs](#assign-product-profile).

>[!ENDTABS]


## 5 - Attribuer le profil de produit au groupe d’utilisateurs{#assign-product-profile}

Cette étape suit le workflow Adobe Admin Console standard d’affectation de profils de produit à des groupes d’utilisateurs.

Article de référence : [gestion des profils de produit pour les utilisateurs d’entreprise](https://helpx.adobe.com/fr/enterprise/using/manage-product-profiles.html)

1. Toujours dans votre groupe d’utilisateurs AEM AI Assistant à partir du [4 - Ajouter des utilisateurs au groupe d’utilisateurs](#add-users), cliquez sur l’onglet **Profils de produit attribués**.
1. Cliquez sur **Attribuer un profil**.

   ![Page de groupe d’utilisateurs de l’assistant AEM AI avec l’onglet Profils de produit attribués sélectionné](/help/implementing/cloud-manager/assets/ai-assistant-assign-profile.png)

1. Sur la page **Attribuer des produits et des profils**, dans la boîte de dialogue **Sélectionner des profils de produit**, recherchez et sélectionnez votre profil de produit **Assistant IA**.

   ![ La page « Attribuer des produits et des profils », affichant la boîte de dialogue « Sélectionner des profils de produit » et le profil de produit « Assistant IA » sélectionné](/help/implementing/cloud-manager/assets/ai-assistant-select-product-profile.png)

1. Dans le coin inférieur droit de la boîte de dialogue, cliquez sur **Appliquer**.
1. Dans le coin inférieur droit de la page **Attribuer des produits et des profils**, cliquez sur **Enregistrer**.

   ![Le profil de produit Assistant AI affiché est affecté au groupe d’utilisateurs Assistant AI AEM](/help/implementing/cloud-manager/assets/ai-assistant-profile-assigned-to-user-group.png)


## Vérification de la configuration

* Vérifiez que votre profil de produit affiche le nombre correct de groupes d’utilisateurs affectés.
* Vérifiez que le groupe d’utilisateurs indique le nombre correct d’utilisateurs.
* Vérifiez que l’autorisation Connaissance des produits de l’assistant AI est activée et correctement configurée.


## Tester la configuration

Demandez à un utilisateur du groupe affecté d’effectuer les opérations suivantes :

1. Connectez-vous à AEM.
2. Vérifiez que les fonctionnalités de l’assistant AI sont accessibles.
3. Testez la fonctionnalité de l’assistant d’IA pour vérifier qu’elle est correctement activée.

## Voir également

* [Contrôle d’accès Adobe Experience Platform](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/ui/overview)
* [Autorisations personnalisées de Cloud Manager](/help/implementing/cloud-manager/custom-permissions.md)


