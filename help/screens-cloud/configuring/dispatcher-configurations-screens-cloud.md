---
title: Configurations du Dispatcher dans Screens as a Cloud Service
description: Cette page décrit les configurations du Dispatcher dans Screens as a Cloud Service.
exl-id: cc04b480-9310-4975-a7c2-20682c567fa4
source-git-commit: f0e9fe0bdf35cc001860974be1fa2a7d90f7a3a9
workflow-type: ht
source-wordcount: '140'
ht-degree: 100%

---

# Configurations du Dispatcher dans Screens as a Cloud Service {#dispatcher-configurations-screens-cloud}

Cette section décrit les configurations du Dispatcher pour Screens as a Cloud Service.

## Ajout de filtres et de règles de cache dans Dispatcher pour le déploiement de Screens as a Cloud Service {#deployment}

Autorisez les filtres et les règles de mise en cache suivants dans les Dispatchers pour les instances de publication dans Screens as a Cloud Service.

### Filtres AEM Screens {#filters}

```
## # Content Configurations
/0200 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*" }
#/0201 { /type "allow" /method '(GET|HEAD)' /url "/content/experience-fragments/*" } ## uncomment this, if you are using experience-fragments
## add any other formats required for your project here
/0202 { /type "allow" /extension '(css|eot|gif|ico|jpeg|jpg|js|gif|pdf|png|svg|swf|ttf|woff|woff2|html|mp4|mov|m4v)' /path "/content/dam/*" }
/0203 { /type "allow" /method 'GET' /url "/screens/channels.json" }
## # Enable clientlibs proxy servlet
/0210 { /type "allow" /method "GET" /url "/etc.clientlibs/*" }
```

### Règles de cache {#cache-rules}

* Ajoutez `/statfileslevel "10"` à la section `/cache` dans `publish_farm.any`/.

  >[!NOTE]
  >Cette règle de cache prend en charge la mise en cache jusqu’à 10 niveaux à partir du docroot du cache et s’invalide lorsque le contenu est publié plutôt que d’invalider l’ensemble. Vous pouvez modifier ce niveau en fonction de la profondeur de configuration de votre structure de contenu.

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
