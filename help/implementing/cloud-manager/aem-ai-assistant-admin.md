---
title: Configuration de l’assistant d’IA dans Adobe Experience Manager
description: Découvrez comment installer et configurer l’assistant AI à l’aide d’Admin Console dans Adobe Experience Manager.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
source-git-commit: ab8fefe18e43c1fe937d0d16df65b6137fc8a292
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 4%

---

# Configuration de l’assistant AEM AI - Configuration de l’administration {#aem-ai-asst-admin-setup}

Un administrateur doit configurer l’accès, les autorisations et les paramètres pour que les utilisateurs de son entreprise puissent utiliser les fonctionnalités de l’assistant AEM AI. Cet article décrit comment activer l’assistant AI pour votre organisation, configurer les informations d’identification requises et enregistrer les modifications apportées à la configuration.

**Présentation du processus de configuration de l’assistant AEM AI**

Le processus de configuration comprend les étapes suivantes :

1. Créez un profil de produit dans Adobe Admin Console.
1. Activez l’autorisation « Connaissance des produits de l’assistant AI ».
1. Créez ou utilisez un groupe d’utilisateurs existant.
1. Ajoutez des utilisateurs au groupe d’utilisateurs .
1. Attribuez le profil de produit au groupe d’utilisateurs.

**Conditions préalables**

Avant de commencer, assurez-vous d’avoir satisfait aux conditions préalables suivantes :

* Vous devez disposer au minimum des droits d’administrateur de produit dans Adobe Admin Console.
* Vous avez une compréhension de la structure de gestion des utilisateurs de votre entreprise.

## 1 - Création d’un profil de produit dans Adobe Admin Console{#create-profile}

1. Suivez les instructions détaillées dans [Création d’un profil de produit dans Adobe Admin Console](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/ui/create-profile) consultez la documentation d’Experience Platform.

1. Lors de la création du profil de produit, utilisez les exemples suivants des valeurs que vous pouvez utiliser pour l’assistant AI.

   | Champ de texte | Valeur suggérée |
   | --- | --- |
   | Nom du profil de produit | `AEM AI Assistant` (ou votre nom descriptif préféré) |
   | Nom d’affichage (facultatif) | `AI Assistant` |
   | Description (facultative) | `Product profile for managing AEM AI Assistant access` |
   | Notification | Configuration d’en fonction des préférences de votre organisation |




## 2 - Activer l’autorisation « Connaissance des produits de l’assistant IA »{#enable-permission}

Le processus d’attribution d’autorisations personnalisées aux profils de produit suit le processus standard des autorisations personnalisées d’Adobe Cloud Manager .

Article de référence : [Attribuer des autorisations personnalisées au nouveau profil de produit](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/requirements/custom-permissions#assign-permissions)

1. Dans Admin Console, cliquez sur le nom de votre profil de produit nouvellement créé (`AEM AI Assistant`)

   ![Capture d’écran](/help/implementing/cloud-manager/assets/ai-assistant-console.png)

1. Pour afficher la liste des autorisations modifiables, cliquez sur l’onglet **Autorisations**.

1. Dans la liste des tableaux, recherchez l’autorisation `AI Assistant Product Knowledge`.

   ![Onglet Autorisations de l’assistant AI dans Admin Console](/help/implementing/cloud-manager/assets/ai-assistant-permission.png)

1. À droite du nom de l’autorisation, cliquez sur ![icône Crayon ou icône Modifier](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg).

1. Sur la page **Modifier les autorisations pour l’assistant AI**, activez le bouton (bascule) **Connaissances du produit de l’assistant AI**.

   ![Page Modifier les autorisations pour l’option de basculement Connaissance du produit de l’assistant IA ](/help/implementing/cloud-manager/assets/ai-assistant-prod-knowledge.png)

1. Dans le coin inférieur droit de la page, cliquez sur **Enregistrer**.

   L’autorisation Connaissance des produits de l’assistant AI est désormais activée pour votre profil de produit.


## 3 - Créer un groupe d’utilisateurs (ou utiliser un groupe d’utilisateurs existant){#create-user-group}

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

1. Sur la page **Ajouter des utilisateurs à ce groupe d’utilisateurs**, recherchez et sélectionnez les utilisateurs qui doivent accéder à l’assistant AEM AI.

   ![Ajouter des utilisateurs à cette page de groupe d’utilisateurs](/help/implementing/cloud-manager/assets/ai-assistant-add-users-to-this-group.png)

1. Dans le coin inférieur droit de la page, cliquez sur **Enregistrer**.

>[!TAB Ajout d’utilisateurs en bloc]

Vous pouvez utiliser la fonction de chargement en bloc dans Admin Console.

1. Préparez un fichier CSV contenant des informations sur l’utilisateur.

1. Utilisez l’option **Ajouter des utilisateurs par fichier CSV** pour un ajout en bloc efficace.

>[!ENDTABS]




## 5 - Attribuer le profil de produit au groupe d’utilisateurs{#assign-product-profile}




