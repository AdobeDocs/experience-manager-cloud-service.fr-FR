---
title: Ajout d’une configuration CDN
description: Découvrez comment ajouter une configuration CDN pour un site Edge Delivery ou un environnement Cloud Manager.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: e57a6ceb2482e61acabe928da0f539d26989985c
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 8%

---


# Ajout d’une configuration CDN {#add-cdn}

L’ajout d’une configuration CDN doit être renseigné pour configurer un domaine avec un protocole SSL.

>
>
>Pour les réseaux de diffusion de contenu gérés par l’Adobe, lors de l’utilisation de certificats DV, seuls les sites avec validation ACME sont autorisés.

**Pour ajouter une configuration CDN :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Cliquez sur **Configurations CDN**.

1. Dans le coin supérieur droit de la page Configurations du réseau de diffusion de contenu, cliquez sur **Ajouter**.

   ![Boîte de dialogue Configurer le réseau de diffusion de contenu](/help/implementing/cloud-manager/assets/configure-cdn-dialog.png)

1. Dans la boîte de dialogue **Configurer CDN** , fournissez les informations nécessaires.

   * Dans la liste déroulante **Origin** , effectuez l’une des opérations suivantes :
      * **Sites :** Sélectionnez un site Edge Delivery Services.
      * **Environnements :** Sélectionnez un environnement de Cloud Service.
         * **Niveau :** Sélectionnez un niveau Web **Publish** ou **Aperçu** pour l’environnement sélectionné.
   * Sélectionnez votre type CDN : **Adobe géré CDN** ou **Autre fournisseur CDN**.
   * Sélectionnez le domaine.
   * Sélectionnez le certificat SSL. Uniquement requis si vous avez sélectionné **Adobe géré CDN** comme type CDN.

1. Cliquez sur **Enregistrer**.




