---
title: Configuration des pages d’erreur CDN
description: Découvrez comment remplacer la page d’erreur par défaut en hébergeant des fichiers statiques dans un stockage auto-hébergé tel qu’Amazon S3 ou Azure Blob Storage, et en les référençant dans un fichier de configuration déployé à l’aide du pipeline de configuration Cloud Manager.
feature: Dispatcher
exl-id: 1ecc374c-b8ee-41f5-a565-5b36445d3c7c
role: Admin
source-git-commit: 85cef99dc7a8d762d12fd6e1c9bc2aeb3f8c1312
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 1%

---


# Configuration des pages d’erreur CDN {#cdn-error-pages}

Dans le cas improbable où le [CDN géré par l&#39;Adobe](/help/implementing/dispatcher/cdn.md#aem-managed-cdn) ne peut pas atteindre l&#39;origine de l&#39;AEM, le CDN diffuse par défaut une page d&#39;erreur générique sans marque qui indique que le serveur ne peut pas être atteint. Vous pouvez remplacer la page d’erreur par défaut en hébergeant des fichiers statiques dans un stockage auto-hébergé tel qu’Amazon S3 ou Azure Blob Storage, et en les référençant dans un fichier de configuration déployé à l’aide du [pipeline de configuration Cloud Manager.](/help/operations/config-pipeline.md#managing-in-cloud-manager)

## Configuration {#setup}

Avant de pouvoir remplacer la page d’erreur par défaut, vous devez effectuer les opérations suivantes :

1. Créez un fichier nommé `cdn.yaml` ou similaire, en référençant la section de syntaxe ci-dessous.

1. Placez le fichier quelque part sous un dossier de niveau supérieur nommé *config* ou similaire, comme décrit dans [Utilisation des pipelines de configuration](/help/operations/config-pipeline.md#folder-structure).

1. Créez un pipeline de configuration dans Cloud Manager, comme décrit dans la section [Utilisation des pipelines de configuration](/help/operations/config-pipeline.md#managing-in-cloud-manager).

1. Déployez la configuration.

### Syntaxe {#syntax}

La page d’erreur est implémentée sous la forme d’une application d’une seule page (SPA) et référence quelques propriétés, comme illustré dans l’exemple ci-dessous.  Les fichiers statiques référencés par les URL doivent être hébergés par vous sur un service accessible sur Internet tel qu’Amazon S3 ou Azure Blob Storage.

Exemple de configuration :

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  errorPages:
    spa:
      title: the error page
      icoUrl: https://www.example.com/error.ico
      cssUrl: https://www.example.com/error.css
      jsUrl: https://www.example.com/error.js
```
Voir [Utilisation des pipelines de configuration](/help/operations/config-pipeline.md#common-syntax) pour une description des propriétés au-dessus du noeud de données. La valeur de la propriété type doit être *CDN* et la propriété `version` doit être définie sur *1*.


| Nom | Propriétés autorisées | Signification |
|-----------|--------------------------|-------------|
| **spa** | title | Titre de la page d’erreur. |
|     | icoUrl | URL d’un fichier d’icône. |
|     | cssUrl | URL vers un fichier CSS. |
|     | jsUrl | URL d’un fichier JavaScript. |

### Exemple d’HTML généré {#sample-generated-html}

Le code d’HTML généré par le réseau de diffusion de contenu et diffusé au client, tel qu’un navigateur, ressemblera (mais ne sera pas identique) au fragment de code suivant :

```
<!DOCTYPE html>
<html lang="en">
    <head>
        ...
        <title>the error page</title>
        <link rel="icon" href="https://www.example.com/error.ico">
        <link rel="stylesheet" href="https://www.example.com/error.css">
    </head>
    <body>
        ...
        <div id="root" status="403"></div>
        <script src="https://www.example.com/error.js"> </script>
    </body>
</html>
```

### Tests {#testing}

À des fins de test, appelez le point de terminaison dédié avec le code d’erreur pris en charge, par exemple :

```
curl "https://publish-pXXXXX-eXXXXXX.adobeaemcloud.com/cdnstatus?code=403"
```

Les codes pris en charge sont : 403, 404, 406, 500 et 503.

Ainsi, vous déclenchez directement le gestionnaire d’erreurs du CDN afin de tester la réponse synthétique pour un code d’erreur donné.
