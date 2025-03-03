---
title: Gestion de sites Edge Delivery dans Cloud Manager
description: Découvrez comment ajouter une configuration de réseau CDN à un site Edge Delivery ou supprimer un site Edge Delivery.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 960aa3c6-27b9-44b1-81ea-ad8c5bbc99a5
source-git-commit: a078d45f81fc7081012ebf24fa8f46dc1a218cd7
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 100%

---

# Gestion d’un site Edge Delivery dans Cloud Manager {#manage-edge-delivery-sites}

Découvrez comment gérer des sites Edge Delivery dans Cloud Manager en ajoutant une configuration de réseau CDN à un site existant. Vous pouvez également supprimer un site Edge Delivery.

## Ajout d’une configuration de réseau CDN à un site Edge Delivery existant {#add-cdn-to-edge-delivery-site}

Voir [Ajout d’une configuration de réseau CDN](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md).

## Attribution d’un nouveau nom à un site Edge Delivery (#rename-edge-delivery-site)

Dans Adobe Cloud Manager, vous pouvez renommer un site Edge Delivery pour plusieurs raisons :

* **Clarté et organisation** : pour mieux décrire l’objectif du site ou son environnement associé (par exemple, production, évaluation).
* **Éviter toute confusion** : si plusieurs sites sont utilisés, le fait de les renommer permet de les différencier facilement, ce qui réduit le risque d’appliquer des configurations ou des mises à jour au mauvais site.
* **Normalisation** : pour respecter une convention de nommage cohérente qui s’aligne sur les directives de votre entreprise pour une gestion et un audit plus simples.

**Pour renommer un site Edge Delivery, procédez comme suit :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez le programme approprié.
1. Dans la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme avec Edge Delivery Services configuré, là où vous souhaitez ajouter un site Edge Delivery.
1. Effectuez l’une des opérations suivantes :

   * Dans la page **Vue d’ensemble du programme**, cliquez sur l’onglet **Edge Delivery**. Dans le tableau du site Edge Delivery, cliquez sur les points de suspension en fin de ligne du site que vous souhaitez renommer.
Cliquez sur **Renommer**.
   * Dans le coin supérieur gauche de la page, cliquez sur ![Icône Afficher le menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour afficher le menu de gauche. Sous l’en-tête **Services**, cliquez sur ![Icône Pages web](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Sites Edge Delivery**.
Dans le tableau du site Edge Delivery, cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) à la fin d’une ligne dont vous souhaitez renommer le site. Cliquez sur **Renommer**.

1. Dans la boîte de dialogue **Modifier le site Edge Delivery**, dans le champ de texte **Nom du site**, saisissez le nouveau nom du site.

1. Cliquez sur **Modifier**.

## Suppression d’un site Edge Delivery {#delete-edge-delivery-site}

Si vous supprimez un site Edge Delivery Services, toutes les configurations de réseau CDN associées sont également supprimées. Cette action rompt la connexion entre les domaines personnalisés et le site. Pour plus d’informations, voir Configurations du réseau CDN. <!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2024.9.0+Release -->

**Pour supprimer un site Edge Delivery, procédez comme suit :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez le programme approprié.
1. Dans la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme avec Edge Delivery Services configuré, là où vous souhaitez ajouter un site Edge Delivery.
1. Effectuez l’une des opérations suivantes :

   * Sur la page **Vue d’ensemble du programme**, cliquez sur l’onglet **Edge Delivery**. Dans le tableau du site Edge Delivery, cliquez sur ![Icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) à la fin d’une ligne dont vous souhaitez supprimer le site.
Cliquez sur ![Icône Supprimer le site Edge Delivery](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg) **Supprimer**, puis cliquez de nouveau sur **Supprimer** pour confirmer la suppression du site.

     ![Ajout d’un site Edge Delivery depuis l’onglet Edge Delivery](/help/implementing/cloud-manager/assets/cm-eds-delete1.png)

   * Dans le coin supérieur gauche de la page, cliquez sur l’![icône Afficher le menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour afficher le menu de gauche. Sous l’en-tête **Services**, cliquez sur ![Icône Page web pour les sites Edge Delivery](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Sites Edge Delivery**.
Dans le tableau du site Edge Delivery, cliquez sur ![Icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) à la fin d’une ligne dont vous souhaitez supprimer le site. Cliquez sur ![Icône Supprimer le site Edge Delivery](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg) **Supprimer**, puis cliquez de nouveau sur **Supprimer** pour confirmer la suppression du site.

     ![Ajout d’un site Edge Delivery à partir du bouton Sites Edge Delivery](/help/implementing/cloud-manager/assets/cm-eds-delete2.png)

## Soumettre un ticket d’assistance {#eds-support-ticket}

{{support-ticket}}
