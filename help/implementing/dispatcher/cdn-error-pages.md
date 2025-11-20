---
title: Configuration des pages d’erreur du réseau CDN
description: Découvrez comment remplacer la page d’erreur par défaut en hébergeant des fichiers statiques dans un stockage auto-hébergé tel qu’Amazon S3 ou Azure Blob Storage, et en les référençant dans un fichier de configuration déployé à l’aide du pipeline de configuration Cloud Manager.
feature: Dispatcher
exl-id: 1ecc374c-b8ee-41f5-a565-5b36445d3c7c
role: Admin
source-git-commit: 3a46db9c98fe634bf2d4cffd74b54771de748515
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 4%

---


# Configuration des pages d’erreur du réseau CDN {#cdn-error-pages}

Dans le cas peu probable où le réseau CDN géré par Adobe [&#128279;](/help/implementing/dispatcher/cdn.md#aem-managed-cdn) ne pourrait pas atteindre l’origine AEM, le réseau CDN diffuse par défaut une page d’erreur générique sans marque qui indique que le serveur ne peut pas être atteint. Vous pouvez remplacer la page d’erreur par défaut en hébergeant des fichiers statiques dans un stockage auto-hébergé tel qu’Amazon S3 ou Azure Blob Storage, et en les référençant dans un fichier de configuration déployé à l’aide du pipeline Cloud Manager [config](/help/operations/config-pipeline.md#managing-in-cloud-manager).

## Configuration {#setup}

Avant de pouvoir remplacer la page d’erreur par défaut, procédez comme suit :

1. Créez un fichier nommé `cdn.yaml` ou similaire, en vous référant à la section de syntaxe ci-dessous.

1. Placez le fichier quelque part sous un dossier de niveau supérieur nommé *config* ou similaire, comme décrit dans la section [&#x200B; Utilisation des pipelines de configuration](/help/operations/config-pipeline.md#folder-structure).

1. Créez un pipeline de configuration dans Cloud Manager, comme décrit dans la section [&#x200B; Utilisation de pipelines de configuration &#x200B;](/help/operations/config-pipeline.md#managing-in-cloud-manager).

1. Déployez la configuration.

### Syntaxe {#syntax}

La page d’erreur est implémentée en tant qu’application monopage (SPA) et référence une poignée de propriétés, comme illustré dans l’exemple ci-dessous.  Les fichiers statiques référencés par les URL doivent être hébergés par vous sur un service accessible par Internet, tel qu’Amazon S3 ou Azure Blob Storage.

Exemple de configuration :

```
kind: "CDN"
version: "1"
data:
  errorPages:
    spa:
      title: the error page
      icoUrl: https://www.example.com/error.ico
      cssUrl: https://www.example.com/error.css
      jsUrl: https://www.example.com/error.js
```

Voir [Utilisation des pipelines de configuration](/help/operations/config-pipeline.md#common-syntax) pour une description des propriétés au-dessus du nœud de données. La valeur de la propriété kind doit être *CDN* et la propriété `version` doit être définie sur *1*.


| Nom | Propriétés autorisées | Signification |
|-----------|--------------------------|-------------|
| **spa** | title | Titre de la page d’erreur. |
|     | icoUrl | URL vers un fichier icône. |
|     | cssUrl | URL vers un fichier CSS. |
|     | jsUrl | URL vers un fichier JavaScript. |

### Exemple d’HTML générée {#sample-generated-html}

Le code HTML généré par le réseau CDN et diffusé au client, tel qu’un navigateur, ressemblera (sans être identique) au fragment de code suivant :

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

À des fins de test, appelez le point d’entrée dédié avec le code d’erreur pris en charge, par exemple :

```
curl "https://publish-pXXXXX-eXXXXXX.adobeaemcloud.com/cdnstatus?code=403"
```

Les codes pris en charge sont : 403, 404, 406, 500 et 503.

Ainsi, vous déclenchez directement le gestionnaire d’erreurs du réseau CDN afin de tester la réponse synthétique pour un code d’erreur donné.

### Tutoriel

Reportez-vous au tutoriel [Pages d’erreur du réseau CDN](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/content-delivery/custom-error-pages#cdn-error-pages) pour obtenir des instructions détaillées sur la création, le déploiement et le test des pages d’erreur du réseau CDN.


