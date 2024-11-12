---
title: Configuration de l’invalidation push
description: Découvrez comment configurer l’invalidation push pour créer votre propre réseau de diffusion de contenu de production.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: bb225fcb931c6e9014ab18e6efbb0620262bcd76
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 2%

---

# Configuration de l’invalidation push

L’invalidation push garantit que les mises à jour de contenu effectuées par les auteurs sont automatiquement supprimées du réseau de diffusion de contenu géré (CDN) lors de la publication. Cela garantit que seul le contenu le plus récent est diffusé.

Le système efface le contenu en fonction d’URL spécifiques et des balises ou clés de cache, en s’assurant que les versions obsolètes sont purgées.

Pour activer l’invalidation push, des propriétés spécifiques doivent être ajoutées au fichier de configuration du projet. Par exemple, un classeur Excel Microsoft nommé `.helix/config.xlsx` dans SharePoint ou un nom de feuille Google `.helix/config` dans Google Drive.

Les propriétés de configuration suivantes définissent le nom de l’hôte de production et le type de gestion du réseau de diffusion de contenu :

| key | value | commentaire |
| --- | --- | --- |
| `cdn.prod.host` | `<Production Host>` | Nom d’hôte du site de production. Par exemple, `www.example.com`. |
| `cdn.prod.type` | géré |   |

Une fois les modifications apportées à la feuille de configuration, les utilisateurs doivent les prévisualiser et les activer à l’aide de l’ [outil de Sidekick](/help/edge/docs/sidekick.md) pour appliquer les mises à jour.

Voir aussi [Présentation des Edge Delivery Services dans Cloud Manager](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md#ed-todo-list).
