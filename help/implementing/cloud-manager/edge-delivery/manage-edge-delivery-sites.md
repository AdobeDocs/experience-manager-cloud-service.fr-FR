---
title: Gestion des sites Edge Delivery dans Cloud Manager
description: Découvrez comment ajouter une configuration CDN à un site Edge Delivery ou supprimer un site Edge Delivery.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: b222b4384b1c2a21ecbb244d149ce7e51cc7990f
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 2%

---

# Gestion du site Edge Delivery dans Cloud Manager {#manage-edge-delivery-sites}

Découvrez comment gérer des sites Edge Delivery dans Cloud Manager en ajoutant une configuration CDN à un site existant. Vous pouvez également supprimer un site Edge Delivery.

## Ajout d’une configuration CDN à un site Edge Delivery existant {#add-cdn-to-edge-delivery-site}

Voir [Ajout d’une configuration CDN](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md).

## Suppression d’un site Edge Delivery {#delete-edge-delivery-site}

Si vous supprimez un site Edge Delivery Services, toutes les configurations de réseau de diffusion de contenu associées sont également supprimées. Cette action rompt la connexion entre les domaines personnalisés et le site. Pour plus d’informations, voir Configurations du réseau de diffusion de contenu. <!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2024.9.0+Release -->

**Pour supprimer un site Edge Delivery :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez le programme approprié.
1. Dans la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme avec les Edge Delivery Services configurés, où vous souhaitez ajouter un site Edge Delivery.
1. Effectuez l’une des opérations suivantes :
   * Sur la page **Aperçu du programme**, cliquez sur l’onglet **Edge Delivery**. Dans le tableau du site Edge Delivery, cliquez sur les points de suspension situés à la fin d’une ligne dont vous souhaitez supprimer le site.
Cliquez sur **Supprimer**, puis de nouveau sur **Supprimer** pour confirmer la suppression du site.

     ![Ajouter un site Edge Delivery depuis l’onglet Edge Delivery](/help/implementing/cloud-manager/assets/cm-eds-delete1.png)

   * Dans le coin supérieur gauche de la page, cliquez sur l’icône représentant un hamburger pour afficher le menu de navigation de gauche. Sous l’en-tête **Services**, cliquez sur **Edge Delivery Sites**.
Dans le tableau du site Edge Delivery, cliquez sur les points de suspension situés à la fin d’une ligne dont vous souhaitez supprimer le site. Cliquez sur **Supprimer**, puis de nouveau sur **Supprimer** pour confirmer la suppression du site.


     ![Ajouter un site Edge Delivery à partir du bouton Edge Delivery Sites](/help/implementing/cloud-manager/assets/cm-eds-delete2.png)