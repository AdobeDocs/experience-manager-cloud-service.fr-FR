---
title: Configuration de l’invalidation push pour un site Edge Delivery
description: Découvrez comment configurer l’invalidation push pour un site Edge Delivery afin d’assurer des mises à jour de contenu efficaces et un contrôle de la mise en cache.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
exl-id: 7cded93c-325c-4a4b-8644-e6a2379d5179
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 100%

---

# Configuration de l’invalidation push

L’invalidation push garantit que les mises à jour de contenu effectuées par les personnes chargées de la création sont automatiquement supprimées du réseau de diffusion de contenu (CDN) géré lors de la publication. Cela garantit que seul le contenu le plus récent est diffusé.

Le système efface le contenu en fonction d’URL spécifiques et de balises ou clés de cache, ce qui garantit que les versions obsolètes sont purgées.

Pour activer l’invalidation push, des propriétés spécifiques doivent être ajoutées au fichier de configuration du projet. Par exemple, un classeur Microsoft Excel nommé `.helix/config.xlsx` dans SharePoint ou une feuille Google Sheet nommée `.helix/config` dans Google Drive.

Les propriétés de configuration suivantes définissent le nom de l’hôte de production et le type de gestion du réseau CDN :

| key | value | comment |
| --- | --- | --- |
| `cdn.prod.host` | `<Production Host>` | Nom d’hôte du site de production. Par exemple, `www.example.com`. |
| `cdn.prod.type` | managed |   |

Une fois les modifications apportées à la feuille de configuration, les utilisateurs et utilisatrices doivent les prévisualiser et les activer à l’aide de l’[outil Sidekick](https://www.aem.live/docs/sidekick) pour appliquer les mises à jour.

Voir aussi [À propos de la liste de tâches Edge Delivery dans Cloud Manager](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md#ed-todo-list).
