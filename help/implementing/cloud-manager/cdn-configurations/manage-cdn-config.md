---
title: Gestion des mappages de domaine
description: Découvrez comment utiliser Cloud Manager pour modifier, mettre à jour ou supprimer des configurations de réseau CDN pour un site Edge Delivery ou un environnement Cloud Manager.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 2ec16c91-0195-4732-a26d-ac223e10afb9
source-git-commit: 1683d53491e06ebe2dfcc96184ce251539ecf732
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 8%

---

# Gestion des mappages de domaine {#manage-cdn-configurations}

Découvrez comment utiliser Cloud Manager pour modifier ou supprimer des configurations de réseau CDN pour un site Edge Delivery ou un environnement Cloud Manager.

## Modifier une configuration de réseau CDN à partir de la page Mappages de domaine {#edit-cdn}

Dans Adobe Cloud Manager, vous pouvez modifier une configuration de réseau de diffusion de contenu (CDN), y compris le niveau d’environnement (Publish ou Aperçu) et le certificat SSL, pour plusieurs raisons.

* **Modifications de l’environnement** : l’ajustement du niveau permet de faire correspondre les paramètres du réseau CDN à l’environnement approprié, que ce soit pour la production en direct (Publish) ou les tests (Aperçu).
* **Améliorations de la sécurité** : la sélection d’un autre certificat SSL peut être nécessaire lors de la mise à jour des certificats ou pour répondre aux besoins de conformité et de sécurité.
* **Optimisation des performances** : la modification de la configuration garantit que les paramètres de réseau CDN corrects pour diffuser du contenu en fonction des besoins opérationnels changeants.

Vous pouvez modifier une configuration sans supprimer complètement la configuration existante. Les modifications s’appliquent à l’environnement sélectionné, par exemple l’environnement d’évaluation ou de production, et peuvent affecter la manière dont le contenu est diffusé et sécurisé.

Un utilisateur doit disposer du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** pour terminer cette tâche.

**Pour modifier une configuration de réseau CDN à partir de la page Mappages de domaine :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.
1. Dans le menu de gauche, sous **Services**, cliquez sur ![Icône de réseau social](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) **Mappages de domaine**.
1. Dans le tableau **Mappages de domaine**, cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) à la fin d’une ligne dont vous souhaitez mettre à jour la configuration de réseau CDN.

1. Dans le menu déroulant, cliquez sur **Modifier**.

1. Dans la boîte de dialogue **Modifier la configuration du réseau de diffusion de contenu**, définissez une ou plusieurs des options dans la liste déroulante correspondante.

   Les options affichées dans la boîte de dialogue varient selon que vous utilisez un réseau CDN géré par l’Adobe **** ou un **autre fournisseur de réseau CDN** (réseau CDN géré par le client).

1. Cliquez sur **Mettre à jour**.

   Le statut du réseau CDN modifié est mis à jour dans le tableau **Mappages de domaine** pour refléter les modifications que vous avez apportées.


## Modifier une configuration de réseau CDN à partir de la page Environnements

Les étapes de modification d’une configuration de réseau CDN à partir de la page **Environnements** sont presque identiques à celles de la [modification d’une configuration de réseau CDN à partir de la page Mappages de domaine](#edit-cdn), mais le point d’entrée diffère.

**Pour modifier une configuration de réseau CDN à partir de la page Environnements :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Dans le menu de gauche, cliquez sur ![Icône de données](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) **Environnements**.

1. Sur la page **Environnements**, sélectionnez un environnement qui vous intéresse.

1. Sur la page des détails de l’environnement, dans le groupe Mappages de domaine, cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) qui correspond à la configuration de réseau CDN que vous souhaitez modifier.

1. Dans le menu pop-up, cliquez sur **Modifier**.

1. Dans la boîte de dialogue **Modifier la configuration du réseau de diffusion de contenu**, définissez une ou plusieurs des options dans la liste déroulante correspondante.

   Les options affichées dans la boîte de dialogue varient selon que vous utilisez un réseau CDN géré par l’Adobe **** ou un **autre fournisseur de réseau CDN** (réseau CDN géré par le client).

1. Cliquez sur **Mettre à jour**.


<!-- ## Go live readiness {#go-live-readiness} 

1. ADD STEPS -->


## Suppression d’une configuration de réseau CDN {#delete-cdn}

Lorsque vous supprimez une configuration de réseau CDN géré par l’Adobe ou géré par le client dans Cloud Manager, les paramètres de routage et de certificat SSL du domaine associé sont supprimés. Le domaine n’utilise plus le réseau CDN pour la diffusion du trafic et toute amélioration de la sécurité ou des performances fournie par le réseau CDN est perdue. Le service peut être interrompu jusqu’à ce qu’une nouvelle configuration soit configurée, que ce soit pour rajouter le réseau CDN supprimé ou en ajouter un nouveau.

Un utilisateur doit disposer du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** pour terminer cette tâche.

**Pour supprimer une configuration de réseau CDN, procédez comme suit**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Dans le menu de gauche, sous **Services**, cliquez sur ![Icône de réseau social](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) **Mappages de domaine**.

1. Dans le tableau Mappages de domaine, cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) à la fin d’une ligne correspondant au réseau CDN à supprimer, puis cliquez sur **Supprimer**.

1. Dans la boîte de dialogue **Supprimer la configuration du réseau CDN**, cliquez sur **Supprimer**.

1. Cliquez de nouveau sur **Supprimer** pour confirmer la suppression du réseau CDN du site.


## Supprimer une configuration de réseau CDN de la page Environnements

Les étapes de suppression d’une configuration de réseau CDN de la page **Environnements** sont presque identiques à celles de la [suppression d’une configuration de réseau CDN de la page Mappages de domaine](#edit-cdn), mais le point d’entrée diffère.

**Pour supprimer une configuration de réseau CDN de la page Environnements :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Dans le menu de gauche, cliquez sur ![Icône de données](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) **Environnements**.

1. Sur la page **Environnements**, sélectionnez un environnement qui vous intéresse.

1. Sur la page des détails de l’environnement, dans le regroupement **Mappages de domaine**, cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) correspondant à la configuration de réseau CDN à supprimer, puis cliquez sur **Supprimer**.

1. Dans la boîte de dialogue **Supprimer la configuration du réseau CDN**, cliquez sur **Supprimer**.

1. Cliquez de nouveau sur **Supprimer** pour confirmer la suppression du réseau CDN du site.
