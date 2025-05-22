---
title: Configuration de votre Source de contenu
description: Découvrez comment configurer la source de contenu de votre site Edge Delivery. Utilisez « fstab.yaml » avec l’architecture Helix 4 ou utilisez l’assistant guidé dans Cloud Manager (ou l’API du service de configuration) avec l’architecture Helix 5.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: f82eafc0-03d0-4c69-9b28-e769a012531b
source-git-commit: 71618a5603328990603db2ee7554048c9020a883
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 40%

---

# Configurer votre source de contenu en un clic pour Edge Delivery Services {#config-content-source}

>[!IMPORTANT]
>
>*Helix* est le nom interne de l’architecture sous-jacente qui alimente AEM Sites avec la création basée sur des documents. Il ne s’agit pas d’un nom de fonctionnalité ou de produit. Dans cet article, *Helix* fait référence à la version de l’architecture utilisée par vos sites Edge Delivery. Helix 5 est la version actuelle de l’architecture sous-jacente ; Helix 4 est la version précédente.

Adobe Experience Manager (AEM) Edge Delivery Services permet la diffusion de contenu à partir de plusieurs sources telles que Google Drive, SharePoint ou AEM lui-même, à l’aide d’un réseau Edge Network rapide distribué dans le monde entier.

La configuration de la source de contenu diffère entre les deux versions d’architecture de la manière suivante :

| Version | Méthode de configuration de la source de contenu |
| --- | --- |
| Helix 4 | Fichier YAML (`fstab.yaml`) |
| Helix 5 | API Configuration Service (*sans`fstab.yaml`*) |

Cet article fournit des étapes de configuration complètes, des exemples et des instructions de validation pour les deux versions.

**Avant de commencer**

Si vous utilisez [Edge Delivery en un clic dans Cloud Manager](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md##one-click-edge-delivery-site), votre site utilise Helix 5 avec un seul référentiel. [Suivez les instructions de Helix 5](#config-helix5) et utilisez la version Helix 4 YAML fournie des instructions comme solution de secours.

**Déterminer votre version Helix**

* Helix 4 : votre projet comprend un fichier `fstab.yaml`.
* Helix 5 - Votre projet *n’utilise pas* utilise `fstab.yaml` et a été configuré via [Cloud Manager à l’aide de l’assistant guidé](/help/implementing/cloud-manager/edge-delivery/add-edge-delivery-site.md) ou de l’API.

Confirmez via les métadonnées du référentiel ou consultez votre administrateur ou administratrice si vous n’avez toujours pas de certitude.

## Configuration de la source de contenu pour Helix 4

Dans Helix 4, le fichier `fstab.yaml` définit la source de contenu de votre site. Situé à la racine de votre référentiel GitHub, ce fichier mappe les préfixes de chemin d’URL (appelés points de montage) à des sources de contenu externes. Voici un exemple type :

```yaml
mountpoints:
  /: https://drive.google.com/drive/folders/your-folder-id
```

L’exemple ci-dessus est fourni uniquement à titre d’illustration. L’URL réelle doit pointer vers votre source de contenu, telle qu’un dossier de lecteur Google, un répertoire SharePoint ou un chemin d’accès AEM.

**Pour configurer la source de contenu pour Helix 4:**

Les étapes varient en fonction du système source que vous utilisez.

* **Google Drive**

   1. Créez un dossier Google Drive.
   1. Partagez le dossier avec `helix@adobe.com`.
   1. Obtenez le lien du dossier partageable.
   1. Mettez à jour votre `fstab.yaml` comme illustré ci-dessous :

      ```yaml
      mountpoints: 
          /: https://drive.google.com/drive/folders/<folder-id>
      ```

   1. Validez et envoyez les modifications à GitHub.

* **SharePoint**

   1. Créez un dossier ou une bibliothèque de documents SharePoint.
   1. Partagez l’accès avec `helix@adobe.com`.
   1. Obtenez l’URL du dossier.
   1. Mettez à jour votre `fstab.yaml` comme illustré ci-dessous :

      ```yaml
      mountpoints:
        /: https://<tenant>.sharepoint.com/sites/<site>/Shared%20Documents/<folder>
      ```

   1. Validez et envoyez les modifications à GitHub.

* **AEM**

   1. Identifiez le chemin d’accès au contenu AEM.
   1. Utilisez l’URL d’export de contenu AEM comme illustré ci-dessous :

      ```yaml
      mountpoints:
        /: https://author.<your-aem-instance>.com/bin/franklin.delivery/<org>/<repo>/main
      ```

   1. Validez et envoyez les modifications à GitHub.

### Validation

* À l’aide de l’extension Chrome AEM Sidekick, cliquez sur **Prévisualisation** > **Publier** > **Tester le site actif**.
* Valider l’URL : `https://main--<repo>--<org>.hlx.page/`

## Configuration de la source de contenu pour Helix 5 {#config-helix5}

Helix 5 est repoless, n&#39;utilise pas `fstab.yaml` et prend en charge plusieurs sites partageant le même répertoire. La configuration est gérée via l’API Configuration Service ou l’interface utilisateur d’Edge Delivery Sites. La configuration s’effectue au niveau du site (et non du référentiel).

Les différences conceptuelles sont les suivantes :

| Aspect | Helix 4 | Helix 5 |
| --- | --- | --- |
| Configuration | Effectué via `fstab.yaml` | Effectué via l’API ou l’interface utilisateur au lieu de YAML. |
| Points de montage | Défini en `fstab.yaml`. | Non requis. La racine est implicitement comprise. |

**Pour configurer la source de contenu pour Helix 5:**

1. À l’aide de l’API Configuration Service, authentifiez par le biais d’une clé API ou d’un jeton d’accès.
1. Effectuez l’appel API `PUT` suivant :

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

1. Validez la réponse (attendue : HTTP 200 OK).

### Validation

* À l’aide de l’extension Chrome AEM Sidekick, cliquez sur **Prévisualisation** > **Publier** > **Tester le site actif**.
* Valider l’URL : `https://main--<repo>--<org>.aem.page/`
* (Facultatif) Inspectez la configuration actuelle par le biais de l’appel API `GET` suivant :

  ```bash
  GET /api/{program}/{programId}/site/{siteId}
  ```
