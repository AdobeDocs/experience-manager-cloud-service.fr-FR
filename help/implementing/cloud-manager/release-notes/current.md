---
title: Notes de mise à jour de la version 2025.5.0 de Cloud Manager
description: En savoir plus sur la version 2025.5.0 de Cloud Manager dans Adobe Experience Manager as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 6b18623cc940856383009cd6b4ba011515c12ab5
workflow-type: tm+mt
source-wordcount: '780'
ht-degree: 22%

---

# Notes de mise à jour de Cloud Manager 2025.5.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.03.0+Release -->

En savoir plus sur la version 2025.5.0 de Cloud Manager dans AEM (Adobe Experience Manager) as a Cloud Service.

Consultez également les [notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Dates de publication {#release-date}

La date de publication de la version 2025.5.0 de Cloud Manager dans AEM as a Cloud Service est le vendredi 8 mai 2025.

La prochaine version est prévue le vendredi 5 juin 2025.

## Nouveautés {#what-is-new}

### Modification de la source de contenu en un clic pour Edge Delivery Services

Adobe Experience Manager (AEM) Edge Delivery Services permet la diffusion de contenu à partir de plusieurs sources telles que Google Drive, SharePoint ou AEM lui-même, à l’aide d’un réseau Edge rapidement distribué dans le monde entier.

La configuration de la source de contenu diffère entre Helix 4 et Helix 5 de la manière suivante :

| Version | Méthode de configuration |
| --- | --- |
| Hélice 4 | Fichier YAML (`fstab.yaml`) |
| Hélice 5 | API Configuration Service (*pas de`fstab.yaml`*) |

Cet article fournit des étapes de configuration complètes, des exemples et des instructions de validation pour les deux versions.

**Avant de commencer**

Si vous utilisez [Edge Delivery en un clic dans Cloud Manager](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md##one-click-edge-delivery-site), votre site s’appelle Helix 5 avec un seul référentiel. Suivez les instructions de Helix 5 et utilisez la version Helix 4 YAML fournie comme solution de secours.

**Déterminer votre version Helix**

* Helix 4 - Votre projet comprend un fichier `fstab.yaml`.
* Helix 5 - Votre projet *n’utilise pas* utilise `fstab.yaml` et a été configuré via l’interface utilisateur ou l’API Edge Delivery Services.

Confirmez via les métadonnées du référentiel ou consultez votre administrateur si vous n’êtes toujours pas sûr.

#### Configuration de la source de contenu (Helix 4)

Dans Helix 4, la source de contenu est définie dans un fichier de configuration YAML nommé `fstab.yaml` situé à la racine de votre référentiel GitHub.

##### Format de fichier YAML

Le fichier `fstab.yaml` définit des points de montage (préfixes de chemin d’URL mappés aux URL sources de contenu) comme dans l’exemple suivant (à titre d’illustration uniquement) :

```yaml
mountpoints:
  /: https://drive.google.com/drive/folders/your-folder-id
```

##### Modification de la source de contenu

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

##### Validation

* À l’aide de l’extension AEM Sidekick Chrome, cliquez sur **Aperçu** > **Publier** > **Tester le site actif**.
* URL de validation : `https://main--<repo>--<org>.hlx.page/`

#### Configurer la source de contenu (Helix 5)

Helix 5 est repoless, n&#39;utilise pas `fstab.yaml` et prend en charge plusieurs sites partageant le même répertoire. La configuration est gérée via l’API du service de configuration ou l’interface utilisateur de Edge Delivery Services. La configuration s’effectue au niveau du site (et non du référentiel).

##### Différences conceptuelles

| Aspect | Hélice 4 | Hélice 5 |
| --- | --- | --- |
| Fichier de configuration | `fstab.yaml` | Configuration de l’API ou de l’interface utilisateur |
| Points de montage | Défini par YAML | Non requis (racine implicite) |

##### Modification de la source de contenu

Utilisez l’API du service de configuration.

1. S’authentifier via une clé API ou un jeton d’accès.
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

##### Validation

* À l’aide de l’extension AEM Sidekick Chrome, cliquez sur **Aperçu** > **Publier** > **Tester le site actif**.
* URL de validation : `https://main--<repo>--<org>.aem.page/`
* (Facultatif) Inspectez la configuration actuelle par le biais de l’appel API `GET` suivant :

  ```bash
  GET /api/{program}/{programId}/site/{siteId}
  ```

<!--
* **AI-powered build summaries now available for internal use**

    Internal users can now use AI-powered build summaries to simplify build log analysis. The feature provides actionable recommendations and helps identify the root causes of build failures.

    ![Build Summary dialog box](/help/implementing/cloud-manager/release-notes/assets/build-summary.png)
-->


## Programme d’adoption précoce {#early-adoption}

Participez au programme des utilisateurs et utilisatrices précoces de Cloud Manager pour obtenir un accès exclusif aux fonctionnalités à venir avant leur publication générale.

Les opportunités d’utilisateurs et utilisatrices précoces suivantes sont actuellement disponibles :

### Ajouter un pipeline Edge Delivery {#add-eds-pipeline}

Les **pipelines** sont désormais pris en charge pour les sites créés avec Edge Delivery Services, étendant cette fonctionnalité au-delà des seuls environnements Cloud Service. Vous pouvez utiliser **Pipelines** pour gérer des paramètres tels que les règles de filtrage du trafic et les configurations du pare-feu d’application web (WAF), le cas échéant. Voir [ Configurations prises en charge ](/help/operations/config-pipeline.md#configurations).

<!-- ![Add Edge Delivery pipeline in Add Pipeline drop-down list](/help/implementing/cloud-manager/release-notes/assets/add-edge-delivery-pipeline.png) -->

Si vous souhaitez tester cette nouvelle fonctionnalité et partager vos commentaires, envoyez un e-mail à [grp-aemeds-config-pipeline-adopter@adobe.com](mailto:grp-aemeds-config-pipeline-adopter@adobe.com) à partir de l’adresse e-mail associée à votre Adobe ID.

### Apportez votre propre Git avec la prise en charge immédiate des opérations de développement Azure. {#gitlab-bitbucket-azure-vsts}

<!-- BOTH CS & AMS -->

Les clients peuvent désormais intégrer leurs référentiels Git Azure DevOps dans Cloud Manager, avec la prise en charge des référentiels Azure DevOps modernes et VSTS hérités (Visual Studio Team Services).

* Pour les utilisateurs de Edge Delivery Services, le référentiel intégré peut être utilisé pour synchroniser et déployer le code du site.
* Pour les utilisateurs d’AEM as a Cloud Service et d’Adobe Managed Services (AMS), le référentiel peut être lié aux pipelines full stack et frontend.

La prise en charge de types de pipeline supplémentaires et de la validation des demandes d’extraction par le biais de pipelines de qualité du code sera bientôt disponible.

Voir [Ajouter des référentiels externes dans Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md).

![Boîte de dialogue Ajouter un référentiel](/help/implementing/cloud-manager/release-notes/assets/azure-repo.png)

Si vous souhaitez tester cette nouvelle fonctionnalité et faire part de vos commentaires, envoyez un e-mail à [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) à partir de l’adresse e-mail associée à votre Adobe ID. Veillez à inclure la plateforme Git à utiliser et indiquez si vous utilisez une structure de référentiel privée/publique ou d’entreprise.

<!--
## Bug fixes

* Issue

* Issue

* Issue
-->

<!-- ## Known issues {#known-issues} -->

