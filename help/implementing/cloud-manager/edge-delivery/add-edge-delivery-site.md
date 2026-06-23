---
title: Ajouter un site Edge Delivery à Cloud Manager
description: Découvrez comment ajouter un site Edge Delivery à votre programme de production ou à votre programme sandbox.
feature: Cloud Manager, Developing
role: Admin, Developer
exl-id: 17e842c9-599a-4877-9834-1e7220f508a8
source-git-commit: 069e94e230b856fba15c3f465c966a5bf6b0ac46
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 58%

---

# Ajouter un site Edge Delivery à Cloud Manager {#adding}

>[!IMPORTANT]
>
>Comprenez pourquoi vous devez ajouter votre site Edge Delivery Services à Cloud Manager.
>Voir [Avantages de l’utilisation du chemin d’accès recommandé d’Adobe pour Edge Delivery Services](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md#recommended-path-eds).

**Pour ajouter un site Edge Delivery à Cloud Manager, procédez comme suit :**

1. Assurez-vous d’avoir créé votre programme avec une licence Edge Delivery Services avant d’intégrer un site Edge Delivery dans Cloud Manager.
Voir [ Création d’un programme de production ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md).

   >[!TIP]
   >
   >Si vous souhaitez créer un site Edge Delivery qui utilise la création AEM avec l’éditeur universel, plutôt que d’enregistrer un site existant, reportez-vous à la section [Création de votre premier site Edge Delivery en un seul clic](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md). Pour les programmes qui utilisent Edge Delivery pour la diffusion, un niveau de publication peut ne pas être requis. Voir [Niveau de publication flexible (Beta)](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#flexible-publish-tier).

{{sign-in-to-cloud-manager}}

1. Sur la console **Mes programmes**, cliquez sur un programme.
1. Utilisez l’une des méthodes suivantes :

   * Sur la page **Vue d’ensemble du programme**, cliquez sur l’onglet **Edge Delivery**. Ensuite, près du coin inférieur droit de la page, cliquez sur **Ajouter un site Edge Delivery**.

     ![Ajouter un site Edge Delivery à partir de l’onglet Edge Delivery](/help/implementing/cloud-manager/assets/cm-eds-add1.png)

   * Dans le coin supérieur gauche de la page, cliquez sur ![Afficher l’icône de menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour ouvrir le menu latéral gauche.
Sous l’en-tête **Services**, cliquez sur ![Icône de page web](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Edge Delivery Sites**.
Dans le coin supérieur droit de la page, cliquez sur ![Icône Lien ou Ajouter](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Link_18_N.svg) **Ajouter un site Edge Delivery**.

     ![Ajouter un site Edge Delivery à partir du bouton Sites Edge Delivery](/help/implementing/cloud-manager/assets/cm-eds-add2.png)

1. Dans la boîte de dialogue **Ajouter un site Edge Delivery**, fournissez les informations suivantes dans les champs requis :

   | Champ de texte | Description |
   | - | --- |
   | Nom du site | Saisissez le nom du site Edge Delivery que vous ajoutez.<br>Le nom sert d’identifiant unique au site dans Cloud Manager. |
   | Origine Edge Delivery | Cette valeur spécifie le chemin d’URL vers la source de contenu de votre site dans Edge Delivery Services. Cloud Manager est également lié à votre site en ligne.<br>L’URL inclut généralement la *branche*, le *projet* et le *client*, comme dans l’exemple suivant (à des fins d’illustration uniquement) :<br>`https://main--{site}--{org}.aem.live` |
   | Description du site (facultative) | Saisissez une brève description du site Edge Delivery que vous ajoutez.<br>Une description permet d’identifier et de différencier le site, ce qui facilite sa gestion et sa reconnaissance parmi les autres sites que vous avez ajoutés. |

1. Dans l’angle inférieur droit de la boîte de dialogue, cliquez sur **Ajouter**.

1. Dans la boîte de dialogue **Vérifier la propriété du référentiel**, vérifiez la propriété de votre référentiel en procédant comme suit :

   | Numéro de l’étape | Description |
   | - | - |
   | **1** | Ajoutez un fichier avec le chemin d’accès et le nom `well-known/adobe/cloudmanager-challenge.txt` à la branche `main` du référentiel Git répertorié dans le champ **URL des référentiels**. N’ajoutez *pas* de point au début du chemin d’accès à l’emplacement.<br>Si nécessaire, cliquez sur ![icône Copier](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) pour copier le chemin vers le presse-papiers. |
   | **2** | Ajoutez le code affiché dans le champ de texte de l’étape 2 au fichier que vous venez de créer à l’étape 1.<br>Si nécessaire, cliquez sur ![Icône Copier](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) pour copier le code dans le presse-papiers. |
   | **3** | Créez une demande d’extraction dans le référentiel Git pour les modifications que vous venez de créer, puis fusionnez-la en `main` pour valider le code. |

1. Cliquez sur **Vérifier**.

   >[!NOTE]
   >
   >Si votre site Edge Delivery Services utilise l’authentification Helix, le défi de vérification n’est pas accessible. Désactivez temporairement l’authentification, effectuez la vérification du site, puis réactivez l’authentification.



Lorsque le référentiel est vérifié, son statut dans la table des sites Edge Delivery est mis à jour. Un cercle vert avec une coche blanche à l’intérieur indique le statut.

Dans le même tableau, cliquez sur l’![icône Informations sur le site Edge Delivery](https://spectrum.adobe.com/static/icons/workflow_18/Smock_InfoOutline_18_N.svg) pour afficher les détails du site. Ces informations comprennent l’URL du référentiel vérifiée, ainsi que les URL du site web de prévisualisation et de production.
