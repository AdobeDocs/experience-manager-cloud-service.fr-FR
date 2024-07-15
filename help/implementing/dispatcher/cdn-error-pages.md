---
title: Configuration des pages d’erreur CDN
description: Découvrez comment remplacer la page d’erreur par défaut en hébergeant des fichiers statiques dans un stockage auto-hébergé tel qu’Amazon S3 ou Azure Blob Storage, et en les référençant dans un fichier de configuration déployé à l’aide du pipeline de configuration Cloud Manager.
feature: Dispatcher
exl-id: 1ecc374c-b8ee-41f5-a565-5b36445d3c7c
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 5%

---

# Configuration des pages d’erreur CDN {#cdn-error-pages}

Dans le cas improbable où le [CDN géré par l&#39;Adobe](/help/implementing/dispatcher/cdn.md#aem-managed-cdn) ne peut pas atteindre l&#39;origine de l&#39;AEM, le CDN diffuse par défaut une page d&#39;erreur générique sans marque qui indique que le serveur ne peut pas être atteint. Vous pouvez remplacer la page d’erreur par défaut en hébergeant des fichiers statiques dans un stockage auto-hébergé tel qu’Amazon S3 ou Azure Blob Storage, et en les référençant dans un fichier de configuration déployé à l’aide du [pipeline de configuration Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#config-deployment-pipeline).

## Configuration {#setup}

Avant de pouvoir remplacer la page d’erreur par défaut, vous devez effectuer les opérations suivantes :

* Créez ce dossier et cette structure de fichiers dans le dossier de niveau supérieur de votre projet Git :

```
config/
     cdn.yaml
```

* Le fichier de configuration `cdn.yaml` doit contenir à la fois des métadonnées et les règles décrites dans les exemples ci-dessous. Le paramètre `kind` doit être défini sur `CDN` et la version doit être définie sur la version du schéma, qui est actuellement `1`.

* Créez un pipeline de configuration de déploiement ciblé dans Cloud Manager. Voir [configuration des pipelines de production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) et [configuration des pipelines hors production](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md).

**Remarques**

* Les RDE ne prennent actuellement pas en charge le pipeline de configuration.
* Vous pouvez utiliser `yq` pour valider localement le format YAML de votre fichier de configuration (par exemple, `yq cdn.yaml`).

### Configuration {#configuration}

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
