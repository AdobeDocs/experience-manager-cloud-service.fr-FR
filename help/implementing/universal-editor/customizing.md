---
title: Personnalisation de l’interface utilisateur
description: Découvrez les différents points d’extension qui vous permettent de personnaliser l’interface utilisateur d’Universal Editor afin de prendre en charge les besoins de vos auteurs de contenu.
exl-id: 8d6523c8-b266-4341-b301-316d5ec224d7
source-git-commit: 7ef3efa6e074778b7b3e3a8159056200b2663b30
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
