---
title: Ajouter un site Edge Delivery à Cloud Manager
description: Découvrez comment ajouter un site Edge Delivery à votre programme de production ou à votre programme sandbox.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 17e842c9-599a-4877-9834-1e7220f508a8
source-git-commit: e99bec4515c79e181ce38b94b1ea327fd99d2695
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 83%

---

# Ajouter un site Edge Delivery à Cloud Manager {#adding}

>[!IMPORTANT]
>
>Découvrez pourquoi intégrer votre site Edge Delivery Services à Cloud Manager.
>>Consultez les [Avantages de l’utilisation du chemin recommandé par Adobe pour Edge Delivery Services](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md#recommended-path-eds).

**Pour ajouter un site Edge Delivery à Cloud Manager, procédez comme suit :**

1. Assurez-vous d’avoir d’abord créé votre programme avec une licence Edge Delivery Services avant d’intégrer un site Edge Delivery dans Cloud Manager.
Voir [ Création d’un programme de production ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md).
1. Connectez-vous à Cloud Manager à l’adresse [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com/) et sélectionnez le programme approprié.
1. Utilisez l’une des méthodes suivantes :

   * Sur la page **Vue d’ensemble du programme**, cliquez sur l’onglet **Edge Delivery**. Ensuite, près du coin inférieur droit de la page, cliquez sur **Ajouter un site Edge Delivery**.

     ![Ajouter un site Edge Delivery à partir de l’onglet Edge Delivery](/help/implementing/cloud-manager/assets/cm-eds-add1.png)

   * Dans le coin supérieur gauche de la page, cliquez sur ![Icône Afficher le menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour afficher le menu de gauche.
Sous l’en-tête **Services**, cliquez sur ![Icône Page web](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Sites Edge Delivery**.
Près du coin supérieur droit de la page, cliquez sur **Ajouter un site**.

     ![Ajouter un site Edge Delivery à partir du bouton Sites Edge Delivery](/help/implementing/cloud-manager/assets/cm-eds-add2.png)

1. Dans la boîte de dialogue **Ajouter un site Edge Delivery**, fournissez les informations suivantes dans les champs requis :

   | Champ de texte | Description |
   | - | --- |
   | Nom du site | Saisissez le nom du site Edge Delivery que vous ajoutez.<br>Le nom sert d’identifiant unique au site dans Cloud Manager. |
   | Origine Edge Delivery | Cette valeur spécifie le chemin d’URL vers la source de contenu de votre site dans Edge Delivery Services. Cloud Manager est également lié à votre site en ligne.<br>L’URL inclut généralement les *branche*, *projet* et *client*, comme dans l’exemple suivant (à des fins d’illustration uniquement) :<br>`https://main--{site}--{org}.aem.live` |
   | Description du site (facultative) | Saisissez une brève description du site Edge Delivery que vous ajoutez.<br>Une description permet d’identifier et de différencier le site, ce qui facilite la gestion et la reconnaissance des autres sites que vous avez ajoutés. |

1. Dans l’angle inférieur droit de la boîte de dialogue, cliquez sur **Ajouter**.

1. Dans la boîte de dialogue **Vérifier la propriété du référentiel**, vérifiez la propriété de votre référentiel en procédant comme suit :

   | Numéro de l’étape | Description |
   | - | - |
   | **1** | Ajoutez un fichier avec le chemin d’accès et le nom `well-known/adobe/cloudmanager-challenge.txt` à la branche `main` du référentiel Git répertorié dans le champ **URL des référentiels**. N’ajoutez *pas* de point au début du chemin d’accès à l’emplacement.<br>Si nécessaire, cliquez sur ![icône Copier](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) pour copier le chemin vers le presse-papiers. |
   | **2** | Ajoutez le code affiché dans le champ de texte de l’étape 2 au fichier que vous venez de créer à l’étape 1.<br>Si nécessaire, cliquez sur ![icône Copier](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) pour copier le code dans le presse-papiers. |
   | **3** | Créez une demande d’extraction dans le référentiel Git pour les modifications que vous venez de créer, puis fusionnez-la en `main` pour valider le code. |

1. Cliquez sur **Vérifier**.

Une fois le référentiel vérifié, son statut dans le tableau des sites Edge Delivery est mis à jour. Un cercle vert avec une coche blanche à l’intérieur indique le statut.

Dans le même tableau, cliquez sur l’![icône Informations sur le site Edge Delivery](https://spectrum.adobe.com/static/icons/workflow_18/Smock_InfoOutline_18_N.svg) pour afficher les détails du site. Ces informations comprennent l’URL du référentiel vérifiée, ainsi que les URL du site web de prévisualisation et de production.
