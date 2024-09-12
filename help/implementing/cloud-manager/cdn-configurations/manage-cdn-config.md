---
title: Gestion des configurations CDN
description: Découvrez comment utiliser Cloud Manager pour modifier, mettre à jour ou supprimer des configurations CDN pour un site Edge Delivery ou un environnement Cloud Manager.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 70f99cfb2cd00278d9ebbb7972ef455af7a87a1b
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 8%

---


# Gestion des configurations CDN {#manage-cdn-configurations}

Découvrez comment utiliser Cloud Manager pour modifier, mettre à jour ou supprimer des configurations CDN pour un site Edge Delivery ou un environnement Cloud Manager.

## Modification d’une configuration CDN {#edit-cdn}

Lors de la modification d’une configuration CDN, vous pouvez ajuster des paramètres tels que le niveau de l’environnement (Publish ou Aperçu) ou les certificats SSL, sans supprimer entièrement la configuration existante. Les modifications s’appliquent à l’environnement sélectionné (par exemple, l’évaluation ou la production) et peuvent affecter la manière dont le contenu est diffusé et sécurisé.

Un utilisateur doit être membre du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** pour terminer cette tâche.

**Pour modifier une configuration CDN :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Dans le panneau de navigation de gauche, sous **Services**, cliquez sur **Configurations CDN**.

1. Dans la table **Configurations du réseau de diffusion de contenu**, cliquez sur les points de suspension en fin de ligne dont vous souhaitez mettre à jour le réseau de diffusion de contenu.

   ![Modification d’une configuration CDN](/help/implementing/cloud-manager/assets/cdn-config-edit.png)

1. Cliquez sur **Modifier**.

1. Dans la boîte de dialogue **Modifier le CDN**, définissez une ou plusieurs des options de la liste déroulante correspondante.

   Les options affichées dans la boîte de dialogue peuvent varier selon que vous utilisez un réseau de diffusion de contenu géré par l’Adobe ou un réseau de diffusion de contenu géré par le client.

1. Cliquez sur **Mettre à jour**.

   L’état du réseau de diffusion de contenu modifié est mis à jour dans la table **Configurations du réseau de diffusion de contenu** pour prendre en compte les modifications que vous avez apportées.


## Suppression d’une configuration CDN {#delete-cdn}

Lorsque vous supprimez une configuration de réseau de diffusion de contenu géré par l’Adobe ou par le client dans Adobe Cloud Manager, les paramètres de routage et de certificat SSL du domaine associé sont supprimés. Le domaine n’utilise plus le réseau de diffusion de trafic et toute amélioration de la sécurité ou des performances fournie par le réseau de diffusion de contenu est perdue. Vous pouvez subir des perturbations du service jusqu’à la configuration d’une nouvelle configuration, que ce soit la réajout du réseau de diffusion de contenu supprimé ou l’ajout d’une nouvelle configuration.

Un utilisateur doit être membre du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** pour terminer cette tâche.

**Pour supprimer une configuration CDN :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Dans le panneau de navigation de gauche, sous **Services**, cliquez sur **Configurations CDN**.

1. Dans le tableau Configurations du réseau de diffusion de contenu, cliquez sur les points de suspension en fin de ligne dont vous souhaitez supprimer le réseau de diffusion de contenu.

   ![Suppression d’une configuration CDN](/help/implementing/cloud-manager/assets/cdn-config-delete.png)

1. Cliquez sur **Supprimer**.
1. Cliquez de nouveau sur **Supprimer** pour confirmer la suppression du réseau de diffusion de contenu du site.


