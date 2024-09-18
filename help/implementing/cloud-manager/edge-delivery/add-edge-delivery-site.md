---
title: Ajout d’un site Edge Delivery à Cloud Manager
description: Découvrez comment ajouter un site Edge Delivery à votre programme de production ou à votre programme sandbox.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: ad6a0e13f27839b9900e440d60948158ddf75d99
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 3%

---


# Ajout d’un site Edge Delivery à Cloud Manager {#adding}

Une fois que vous avez ajouté un site Edge Delivery à votre programme de production, votre licence Edge Delivery Services lui est appliquée.

L&#39;ajout d&#39;un site Edge Delivery à Cloud Manager est nécessaire pour [enregistrer un ticket d&#39;assistance pour votre projet Edge Delivery](/help/edge/overview.md##support-ticket).

Voir aussi [Présentation des Edge Delivery Services dans Cloud Manager](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md).

**Pour ajouter un site Edge Delivery à Cloud Manager :**

1. Connectez-vous à Cloud Manager à l’adresse [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com/) et sélectionnez le programme approprié.
1. Utilisez l’une des méthodes suivantes :

   * Sur la page **Aperçu du programme**, cliquez sur l’onglet **Edge Delivery**. Ensuite, près du coin inférieur droit de la page, cliquez sur **Ajouter un site Edge Delivery**.

     ![Ajouter un site Edge Delivery à partir de l’onglet Edge Delivery](/help/implementing/cloud-manager/assets/cm-eds-add1.png)

   * Dans le coin supérieur gauche de la page, cliquez sur l’icône représentant un hamburger pour afficher le menu de navigation de gauche. Sous l’en-tête **Services**, cliquez sur **Edge Delivery Sites**. Dans le coin supérieur droit de la page, cliquez sur **Ajouter un site**.

     ![Ajouter un site Edge Delivery à partir du bouton Edge Delivery Sites](/help/implementing/cloud-manager/assets/cm-eds-add2.png)

1. Dans la boîte de dialogue **Ajouter un site Edge Delivery** , fournissez les informations suivantes dans les champs requis :

   | Champ de texte | Description |
   | - | --- |
   | Nom du site | Saisissez le nom du site Edge Delivery que vous ajoutez.<br>Le nom sert d’identifiant unique au site dans Cloud Manager. |
   | URL du référentiel | Saisissez le référentiel Git dans lequel le code de votre site web est stocké.<br>Ce champ permet à Cloud Manager d’extraire le code de ce référentiel pendant le processus de déploiement. |
   | Description du site (facultative) | Entrez une brève description du site Edge Delivery que vous ajoutez.<br>Une description permet d’identifier et de différencier le site, ce qui facilite la gestion et la reconnaissance des autres sites que vous avez ajoutés. |

1. Dans le coin inférieur droit de la boîte de dialogue, cliquez sur **Ajouter**.

1. Dans la boîte de dialogue **Vérifier la propriété du référentiel**, vérifiez la propriété de votre référentiel en procédant comme suit :

   | Numéro de l’étape | Description |
   | - | - |
   | **1** | Ajoutez un fichier avec le chemin d’accès et le nom `well-known/adobe/cloudmanager-challenge.txt` à la branche `main` du référentiel Git répertoriée dans le champ **Repository URL** . N’ajoutez *pas* de point au début du chemin d’accès à l’emplacement.<br>Si nécessaire, cliquez sur l’icône **Copier** pour copier le chemin d’accès au Presse-papiers. |
   | **2** | Ajoutez le code affiché dans le champ de texte de l’étape 2 au fichier que vous venez de créer à l’étape 1.<br>Si nécessaire, cliquez sur l’icône **Copier** pour copier le code dans le Presse-papiers. |
   | **3** | Créez une requête de tirage dans le référentiel Git pour les modifications que vous venez de créer, puis fusionnez-la en `main` pour valider le code. |

1. Cliquez sur **Vérifier**.

Une fois le référentiel vérifié, son état dans le tableau Edge Deliver Sites passe à un cercle vert avec une coche blanche à l’intérieur.
