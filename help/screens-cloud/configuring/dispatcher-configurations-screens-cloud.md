---
title: Configurations de Dispatcher dans Screens en tant que Cloud Service
description: Cette page décrit les configurations du Dispatcher dans Screens en tant que Cloud Service.
source-git-commit: b00856e1be8842c4e9fa6ed4ada9129926c73ef5
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 5%

---


# Configurations de Dispatcher dans Screens en tant que Cloud Service{#dispatcher-configurations-screens-cloud}

Cette section décrit les configurations du Dispatcher pour Screens en tant que Cloud Service.

## Configurations de Dispatcher pour le déploiement Screens en tant que Cloud Service {#deployment}

Autorisez les filtres et règles de mise en cache suivants dans les Dispatchers pour les instances de publication dans Screens en tant que Cloud Service.

### Filtres {#filters}

## Filtres AEM Screens

```
## # Content Configurations
/0200 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*" }
#/0201 { /type "allow" /method '(GET|HEAD)' /url "/content/experience-fragments/*" } ## uncomment this, if you're using experience-fragments
## add any other formats required for your project here
/0202 { /type "allow" /extension '(css|eot|gif|ico|jpeg|jpg|js|gif|pdf|png|svg|swf|ttf|woff|woff2|html|mp4|mov|m4v)' /path "/content/dam/*" }
/0203 { /type "allow" /method 'GET' /url "/screens/channels.json" }
## # Enable clientlibs proxy servlet
/0210 { /type "allow" /method "GET" /url "/etc.clientlibs/*" }
```

## Règles de cache {#cache-rules}

* Ajoutez `/statfileslevel "10"` à la section `/cache` dans `publish_farm.any`/.

   >[!NOTE]
   >Cela prend en charge la mise en cache jusqu’à 10 niveaux à partir du docroot du cache et invalide lorsque le contenu est publié plutôt que d’invalider tout. Vous pouvez modifier ce niveau en fonction de la profondeur de la structure de contenu.

* Ajoutez ce qui suit à la section `/invalidate` dans `publish_farm.any`.

   ```
   /0003 {
       /glob "*.json"
       /type "allow"
   }
   ```

* Ajoutez les règles suivantes à la section `/rules` dans `/cache` dans publish_farm.any ou dans un fichier inclus à partir de `publish_farm.any`.

   ```
   ## Allow Dispatcher Cache for Screens channels
    /0002
        {
        /glob "/content/screens/*.html"
        /type "allow"
            }
   
   ## Allow Dispatcher Cache for Screens offline manifests
   
   /0003
       {
       /glob "/content/screens/*.manifest.json"
       /type "allow"
       }
   
   ## Allow Dispatcher Cache for Assets
   /0004
       {
       /glob "/content/dam/*"
       /type "allow"
       }
   
   ## Deny Screens Channels json
   /0005
       {
       /glob "/screens/channels.json"
       /type "deny"
       }
   ```
