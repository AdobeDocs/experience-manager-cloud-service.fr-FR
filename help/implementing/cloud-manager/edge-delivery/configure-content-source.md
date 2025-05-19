---
title: Configuration de votre Source de contenu
description: Découvrez comment configurer la source de contenu de votre site Edge Delivery à l’aide de fstab.yaml dans Helix 4 ou de l’interface utilisateur de Edge Delivery Services (ou de l’API Configuration Service) dans Helix 5.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 8696cf8a7e7cfc439450b34fa6fda10b38cd415e
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 2%

---

# Configurer votre source de contenu en un clic pour Edge Delivery Services {#config-content-source}

Adobe Experience Manager (AEM) Edge Delivery Services permet la diffusion de contenu à partir de plusieurs sources telles que Google Drive, SharePoint ou AEM lui-même, à l’aide d’un réseau Edge rapidement distribué dans le monde entier.

La configuration de la source de contenu diffère entre Helix 4 et Helix 5 de la manière suivante :

| Version | Méthode de configuration de la source de contenu |
| --- | --- |
| Hélice 4 | Fichier YAML (`fstab.yaml`) |
| Hélice 5 | API Configuration Service (*pas de`fstab.yaml`*) |

Cet article fournit des étapes de configuration complètes, des exemples et des instructions de validation pour les deux versions.

**Avant de commencer**

Si vous utilisez [Edge Delivery en un clic dans Cloud Manager](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md##one-click-edge-delivery-site), votre site s’appelle Helix 5 avec un seul référentiel. [Suivez les instructions de Helix 5](#config-helix5) et utilisez la version Helix 4 YAML fournie des instructions comme solution de secours.

**Déterminer votre version Helix**

* Helix 4 - Votre projet comprend un fichier `fstab.yaml`.
* Helix 5 - Votre projet *n’utilise pas* utilise `fstab.yaml` et a été configuré via l’interface utilisateur ou l’API [Edge Delivery Services](#config-helix5).

Confirmez via les métadonnées du référentiel ou consultez votre administrateur si vous n’êtes toujours pas sûr.

## Configuration de la source de contenu pour Helix 4

Dans Helix 4, le fichier fstab.yaml définit la source de contenu de votre site. Situé à la racine de votre référentiel GitHub, ce fichier mappe les préfixes de chemin d’URL (appelés points de montage) à des sources de contenu externes. Voici un exemple type :

```yaml
mountpoints:
  /: https://drive.google.com/drive/folders/your-folder-id
```

Cet exemple est fourni uniquement à titre d’illustration. L’URL réelle doit pointer vers votre source de contenu, telle qu’un dossier de lecteur Google, un répertoire SharePoint ou un chemin d’accès AEM.

**Pour configurer la source de contenu pour Helix 4:**

Les étapes varient en fonction du système source que vous utilisez.

* **Google Drive**

   1. Créez un dossier Google Drive.
   1. Partagez le dossier avec `helix@adobe.com`.
   1. Obtenez le lien du dossier partageable.
   1. Mettez à jour votre `fstab.yaml` comme illustré ci-dessous :

      ```yaml
      mountpoints: 
          /: https://drive.google.com/drive/folders/<folder-id>
      ```

   1. Validez et envoyez les modifications à GitHub.

* **SharePoint**

   1. Créez un dossier ou une bibliothèque de documents SharePoint.
   1. Partagez l’accès avec `helix@adobe.com`.
   1. Obtenez l’URL du dossier.
   1. Mettez à jour votre `fstab.yaml` comme illustré ci-dessous :

      ```yaml
      mountpoints:
        /: https://<tenant>.sharepoint.com/sites/<site>/Shared%20Documents/<folder>
      ```

   1. Validez et envoyez les modifications à GitHub.

* **AEM**

   1. Identifiez le chemin d’accès au contenu AEM.
   1. Utilisez l&#39;URL d&#39;export de contenu AEM comme illustré ci-dessous :

      ```yaml
      mountpoints:
        /: https://author.<your-aem-instance>.com/bin/franklin.delivery/<org>/<repo>/main
      ```

   1. Validez et envoyez les modifications à GitHub.

### Validation

* À l’aide de l’extension AEM Sidekick Chrome, cliquez sur **Aperçu** > **Publier** > **Tester le site actif**.
* URL de validation : `https://main--<repo>--<org>.hlx.page/`

## Configuration de la source de contenu pour Helix 5 {#config-helix5}

Helix 5 est repoless, n&#39;utilise pas `fstab.yaml` et prend en charge plusieurs sites partageant le même répertoire. La configuration est gérée via l’API du service de configuration ou l’interface utilisateur de Edge Delivery Services. La configuration s’effectue au niveau du site (et non du référentiel).

Les différences conceptuelles sont les suivantes :

| Aspect | Hélice 4 | Hélice 5 |
| --- | --- | --- |
| Configuration | Effectué via `fstab.yaml` | Effectué via l’API ou l’interface utilisateur au lieu de YAML. |
| Points de montage | Défini en `fstab.yaml`. | Non requis. La racine est implicitement comprise. |

**Pour configurer la source de contenu pour Helix 5:**

1. À l’aide de l’API Configuration Service, authentifiez par le biais d’une clé API ou d’un jeton d’accès.
1. Effectuez l’appel API `PUT` suivant :

   ```bash {.line-numbering}
   PUT /api/{program}/{programId}/site/{siteId}
   Content-Type: application/json
   
   {
     "sitename": "my-site",
     "branchName": "main",
     "version": "v5",
     "repo": "my-content-repo-link"
   }
   ```

1. Validez la réponse (attendue : HTTP 200 OK).

### Validation

* À l’aide de l’extension AEM Sidekick Chrome, cliquez sur **Aperçu** > **Publier** > **Tester le site actif**.
* URL de validation : `https://main--<repo>--<org>.aem.page/`
* (Facultatif) Inspectez la configuration actuelle par le biais de l’appel API `GET` suivant :

  ```bash
  GET /api/{program}/{programId}/site/{siteId}
  ```
