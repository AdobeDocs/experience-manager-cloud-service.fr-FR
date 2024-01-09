---
title: Personnalisation de l’interface utilisateur
description: Découvrez les différents points d’extension qui vous permettent de personnaliser l’interface utilisateur d’Universal Editor afin de prendre en charge les besoins de vos auteurs de contenu.
source-git-commit: 65893c0c0dee37bed8ecfbb06a12e7c093c4397c
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%

---


# Personnalisation de l’interface utilisateur {#customizing-ui}

Découvrez les différents points d’extension qui vous permettent de personnaliser l’interface utilisateur d’Universal Editor afin de prendre en charge les besoins de vos auteurs de contenu.

## Désactivation de la publication {#disable-publish}

Certains workflows de création nécessitent que le contenu soit examiné avant d’être publié. Dans ce cas, l’option de publication ne doit être disponible pour aucun auteur.

La variable **Publier** peut donc être entièrement supprimé dans une application en ajoutant les métadonnées suivantes.

```html
<meta name="urn:adobe:aue:config:disable" content="publish"/>
```
