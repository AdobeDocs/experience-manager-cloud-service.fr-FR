---
title: Configuration des pages d’erreur CDN
description: Découvrez comment remplacer la page d’erreur par défaut en hébergeant des fichiers statiques dans un stockage auto-hébergé tel qu’Amazon S3 ou Azure Blob Storage, et en les référençant dans un fichier de configuration déployé à l’aide du pipeline de configuration de Cloud Manager.
feature: Dispatcher
source-git-commit: 11036c3e95f0444fc5d865232a7dccab5b7f26ae
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 1%

---


# Configuration des pages d’erreur CDN {#cdn-error-pages}

>[!NOTE]
>Cette fonctionnalité n’est pas encore disponible pour l’ensemble de la population. Pour rejoindre le programme d’adoption précoce, envoyez un email à `aemcs-cdn-config-adopter@adobe.com` et décrivez votre cas d’utilisation.

Dans le cas improbable où la variable [Réseau de diffusion de contenu géré par Adobe](/help/implementing/dispatcher/cdn.md#aem-managed-cdn) ne peut pas atteindre l’origine de l’AEM, le réseau de diffusion de contenu diffuse par défaut une page d’erreur générique sans marque qui indique que le serveur ne peut pas être atteint. Vous pouvez remplacer la page d’erreur par défaut en hébergeant des fichiers statiques dans un stockage auto-hébergé tel qu’Amazon S3 ou Azure Blob Storage, et en les référençant dans un fichier de configuration déployé à l’aide de la variable [Pipeline de configuration de Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#config-deployment-pipeline).

## Configuration {#setup}

Avant de pouvoir remplacer la page d’erreur par défaut, vous devez effectuer les opérations suivantes :

* Créez tout d’abord cette structure de dossiers et de fichiers dans le dossier de niveau supérieur de votre projet Git :

```
config/
     cdn.yaml
```

* Deuxièmement, le `cdn.yaml` Le fichier de configuration doit contenir des métadonnées et les références de page d’erreur, comme décrit ci-dessous.

### Configuration {#configuration}

La page d’erreur est implémentée sous la forme d’une application d’une seule page (SPA) et référence quelques propriétés, comme illustré dans l’exemple ci-dessous.  Les fichiers statiques référencés par les URL doivent être hébergés par vous sur un service accessible sur Internet tel qu’Amazon S3 ou Azure Blob Storage.

Exemple de configuration :

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  experimental_errorPages:
    spa:
      title: the error page
      icoUrl: https://www.example.com/error.ico
      cssUrl: https://www.example.com/error.css
      jsUrl: https://www.example.com/error.js
```

| Nom | Propriétés autorisées | Signification |
|-----------|--------------------------|-------------|
| **spa** | title | Titre de la page d’erreur. |
|     | icoUrl | URL d’un fichier d’icône. |
|     | cssUrl | URL vers un fichier CSS. |
|     | jsUrl | URL d’un fichier JavaScript. |

### Exemple de HTML généré {#sample-generated-html}

Le code de HTML généré par le réseau de diffusion de contenu et diffusé au client, tel qu’un navigateur, ressemblera (mais ne sera pas identique) au fragment de code suivant :

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
