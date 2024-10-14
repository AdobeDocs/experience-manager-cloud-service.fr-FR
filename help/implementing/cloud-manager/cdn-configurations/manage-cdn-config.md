---
title: Gérer les configurations CDN
description: Découvrez comment utiliser Cloud Manager pour modifier, mettre à jour ou supprimer des configurations CDN pour un site Edge Delivery ou un environnement Cloud Manager.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 02f9b035320bb4b6219d5ed4273554259fc09e59
workflow-type: tm+mt
source-wordcount: '802'
ht-degree: 9%

---


# Gestion des configurations CDN {#manage-cdn-configurations}

Découvrez comment utiliser Cloud Manager pour modifier ou supprimer des configurations CDN pour un site Edge Delivery ou un environnement Cloud Manager.

## Modification d’une configuration CDN à partir de la page Configurations CDN {#edit-cdn}

Dans Adobe Cloud Manager, vous pouvez modifier une configuration CDN (réseau de diffusion de contenu), y compris le niveau d’environnement (Publish ou Preview) et le certificat SSL, pour plusieurs raisons.

* **Modifications de l’environnement** : le réglage du niveau permet de faire correspondre les paramètres du réseau de diffusion de contenu avec l’environnement approprié, que ce soit pour la production en direct (Publish) ou le test (Aperçu).
* **Améliorations de la sécurité** : la sélection d’un autre certificat SSL peut être nécessaire lors de la mise à jour des certificats ou pour répondre aux besoins de conformité et de sécurité.
* **Optimisation des performances** : la modification de la configuration garantit les paramètres CDN corrects pour la diffusion de contenu en fonction des besoins opérationnels changeants.

Vous pouvez modifier une configuration sans supprimer complètement la configuration existante. Les modifications s’appliquent à l’environnement sélectionné (par exemple, l’évaluation ou la production) et peuvent affecter la manière dont le contenu est diffusé et sécurisé.

Un utilisateur doit être membre du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** pour terminer cette tâche.

**Pour modifier une configuration CDN à partir de la page Configurations CDN :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.
1. Dans le panneau latéral, sous **Services**, cliquez sur l’icône ![ ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) **Configurations CDN**.
1. Dans la table **Configurations du réseau de diffusion de contenu**, cliquez sur ![Icône More](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) à la fin d’une ligne dont vous souhaitez mettre à jour la configuration du réseau de diffusion de contenu.

   ![Modification d’une configuration CDN](/help/implementing/cloud-manager/assets/cdn-config-edit.png)

1. Dans le menu déroulant, cliquez sur **Modifier**.

1. Dans la boîte de dialogue **Modifier la configuration du réseau de diffusion de contenu**, définissez une ou plusieurs des options de la liste déroulante correspondante.

   Les options affichées dans la boîte de dialogue varient selon que vous utilisez un **réseau de diffusion de contenu géré par Adobe** ou un **autre fournisseur de réseau de diffusion de contenu** (réseau de diffusion de contenu géré par le client).

1. Cliquez sur **Mettre à jour**.

   L’état du réseau de diffusion de contenu modifié est mis à jour dans la table **Configurations du réseau de diffusion de contenu** pour prendre en compte les modifications que vous avez apportées.


## Modification d’une configuration CDN à partir de la page Environnements

Les étapes de modification d’une configuration CDN à partir de la page **Environments** sont presque les mêmes que lors de la [modification d’une configuration CDN à partir de la page Configurations CDN](#edit-cdn), mais le point d’entrée diffère.

**Pour modifier une configuration CDN à partir de la page Environnements :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Dans le menu de gauche, cliquez sur **Environnements**.

1. Sur la page **Environments** , sélectionnez un environnement intéressant.

1. Sur la page des détails de l’environnement, dans le groupe Configurations du réseau de diffusion de contenu , cliquez sur ![Icône More](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) correspondant à la configuration du réseau de diffusion de contenu que vous souhaitez modifier.

   ![Saisie d’un nom de domaine sur la page Détails de l’environnement](/help/implementing/cloud-manager/assets/cdn/environments-cdn-config.png)

1. Dans le menu contextuel, cliquez sur **Modifier**.

1. Dans la boîte de dialogue **Modifier la configuration du réseau de diffusion de contenu**, définissez une ou plusieurs des options de la liste déroulante correspondante.

Les options affichées dans la boîte de dialogue varient selon que vous utilisez un **réseau de diffusion de contenu géré par Adobe** ou un **autre fournisseur de réseau de diffusion de contenu** (réseau de diffusion de contenu géré par le client).

1. Cliquez sur **Mettre à jour**.


<!-- ## Go live readiness {#go-live-readiness} 

1. ADD STEPS -->


## Suppression d’une configuration CDN {#delete-cdn}

Lorsque vous supprimez une configuration CDN gérée par un Adobe ou par le client dans Cloud Manager, les paramètres de routage et de certificat SSL du domaine associé sont supprimés. Le domaine n’utilise plus le réseau de diffusion de trafic et toute amélioration de la sécurité ou des performances fournie par le réseau de diffusion de contenu est perdue. Vous pouvez subir des perturbations du service jusqu’à la configuration d’une nouvelle configuration, que ce soit la réajout du réseau de diffusion de contenu supprimé ou l’ajout d’une nouvelle configuration.

Un utilisateur doit être membre du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** pour terminer cette tâche.

**Pour supprimer une configuration CDN :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Dans le panneau de gauche, sous **Services**, cliquez sur **Configurations CDN**.

1. Dans la table Configurations du réseau de diffusion de contenu, cliquez sur ![Icône More](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) à la fin d’une ligne correspondant à un réseau de diffusion de contenu que vous souhaitez supprimer.

   ![Suppression d’une configuration CDN](/help/implementing/cloud-manager/assets/cdn-config-delete.png)

1. Dans le menu déroulant, cliquez sur **Supprimer**.

1. Dans la boîte de dialogue **Supprimer la configuration CDN**, cliquez sur **Supprimer**.

1. Cliquez de nouveau sur **Supprimer** pour confirmer la suppression du réseau de diffusion de contenu du site.


## Suppression d’une configuration CDN de la page Environnements

Les étapes de suppression d’une configuration CDN de la page **Environnements** sont presque identiques à celles de la [suppression d’une configuration CDN de la page Configurations CDN](#edit-cdn), mais le point d’entrée diffère.

**Pour supprimer une configuration CDN de la page Environnements :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Dans le menu de gauche, cliquez sur **Environnements**.

1. Sur la page **Environments** , sélectionnez un environnement intéressant.

1. Sur la page des détails de l’environnement, dans le regroupement **Configurations du réseau de diffusion de contenu**, cliquez sur ![Icône More](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) correspondant à la configuration du réseau de diffusion de contenu que vous souhaitez supprimer.

   ![Groupe de configuration CDN sur une page des détails de l’environnement](/help/implementing/cloud-manager/assets/cdn/environments-cdn-config.png)

1. Dans le menu déroulant, cliquez sur **Supprimer**.

1. Dans la boîte de dialogue **Supprimer la configuration CDN**, cliquez sur **Supprimer**.

1. Cliquez de nouveau sur **Supprimer** pour confirmer la suppression du réseau de diffusion de contenu du site.


