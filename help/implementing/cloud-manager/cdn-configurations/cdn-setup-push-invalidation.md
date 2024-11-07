---
title: Configuration de l’invalidation push
description: Découvrez comment configurer l’invalidation push pour créer votre propre réseau de diffusion de contenu de production.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
hide: true
source-git-commit: 3941b7f97d434946a3cb796633f306b89e68c0a4
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 2%

---

# Configuration de l’invalidation push

L’invalidation push garantit que les mises à jour de contenu effectuées par les auteurs sont automatiquement supprimées du réseau de diffusion de contenu géré (CDN) une fois publiées, de sorte que seul le contenu le plus récent est diffusé.

Le système efface le contenu en fonction d’URL spécifiques et des balises ou clés de cache, en s’assurant que les versions obsolètes sont purgées.

Pour activer l’invalidation push, des propriétés spécifiques doivent être ajoutées au fichier de configuration du projet. Par exemple, un classeur Excel Microsoft nommé `.helix/config.xlsx` dans SharePoint ou un nom de feuille Google `.helix/config` dans Google Drive.

Les propriétés de configuration suivantes définissent le nom de l’hôte de production et le type de gestion du réseau de diffusion de contenu :

| key | value | commentaire |
| --- | --- | --- |
| `cdn.prod.host` | `<Production Host>` | Nom d’hôte du site de production. Par exemple, `www.example.com`. |
| `cdn.prod.type` | géré |   |

Une fois les modifications apportées à la feuille de configuration, les utilisateurs doivent les prévisualiser et les activer à l’aide de l’ [outil de Sidekick](/help/edge/docs/sidekick.md) pour appliquer les mises à jour.
