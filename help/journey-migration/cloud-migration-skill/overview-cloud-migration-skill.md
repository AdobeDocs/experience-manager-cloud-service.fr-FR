---
title: Migration de code assisté par l’IA vers AEM as a Cloud Service
description: Présentation de la compétence de migration vers le cloud AEM et de MCP, une solution d’agent d’IA qui lit les résultats BPA et migre le code AEM 6.x vers AEM as a Cloud Service, motif par motif.
feature: Migration
role: Developer
source-git-commit: 5cda629090d9a9d020deca5192b8a89659ec4749
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 1%

---


# Migration de code assisté par l’IA vers AEM as a Cloud Service {#cloud-migration-skill-overview}

La solution **Migration du cloud** est un ensemble d’outils basé sur des agents qui guide les développeurs tout au long de la migration du code Java AEM 6.x, AMS ou On-Premise et des configurations OSGi vers **AEM as a Cloud Service (AEMaaCS)**. Il fonctionne dans tout IDE compatible avec l’IA qui prend en charge les compétences des agents et le protocole MCP (Model Context Protocol).

La vidéo de démonstration suivante fournit une présentation rapide de bout en bout de la solution de migration vers le cloud AEM et est incluse à titre de référence.

>[!VIDEO](https://publish.tv.adobe.com/bucket/7642/category/12553/video/3491438/)

La solution se compose de deux composants :

| Composant | Rôle |
|-----------|------|
| **Compétences en migration** | Orchestre le workflow de migration, il identifie les résultats de l’analyseur de bonnes pratiques (BPA), identifie les fichiers affectés dans votre projet et applique les transformations de code motif par motif. Fonctionne avec une exportation CSV BPA locale ou avec le MCP Migration vers le cloud (recommandé). |
| **MCP de migration vers le cloud** | Connecte votre agent IDE à Cloud Acceleration Manager (CAM), ce qui lui permet de récupérer directement les résultats BPA sans exportation CSV. Recommandé sur un fichier CSV local pour les résultats les plus récents. |

## Conditions préalables {#prerequisites}

- Un projet AEM (Maven ou Gradle) s’ouvre dans votre IDE
- L’une des sources de recherche BPA suivantes (fortement recommandée, non requise pour les flux manuels) :
   - Une **exportation CSV BPA** à partir de votre instance AEM
   - Un projet **** avec un rapport BPA chargé et le MCP de migration vers le cloud configuré

## La Compétence De Migration {#migration-skill}

La compétence de migration est une compétence d’agent pour les IDE compatibles avec l’IA. Il orchestre un workflow **un modèle par session** : vous nommez le modèle à corriger, pointez l’agent vers vos résultats BPA, et l’agent lit les règles de transformation appropriées, localise les fichiers affectés dans votre projet et applique les modifications par lots de cinq, en pause de votre révision après chaque lot.

### Modèles pris en charge {#supported-patterns}

| Modèle | Ce qu’il corrige |
|---------|--------------|
| `scheduler` | `sling.commons.scheduler` incompatibles avec l’exécution sans état d’AEMaaCS |
| `resourceChangeListener` | Implémentations `ResourceChangeListener` nécessitant des mises à jour de Cloud Service |
| `replication` | Appels d’API `Replicator` hérités remplacés par des équivalents `ContentDistribution` |
| `eventListener` | Implémentations `EventListener` OSGi mises à jour pour la sémantique d’événement AEMaaCS |
| `eventHandler` | Services de `EventHandler` OSGi synchrones adaptés à Cloud Service |
| `assetApi` | Appels d’API `AssetManager` et DAM obsolètes remplacés par des équivalents pris en charge |
| `htlLint` | `data-sly-test` des avertissements de comparaison constante redondants dans les modèles HTL |
| Configurations OSGi | conversion `.cfg.json`, définition de la portée du mode d’exécution et extraction des secrets Cloud Manager/env-var |

La compétence délègue toutes les étapes de transformation du code à la compétence `best-practices` associée. Les deux sont distribués ensemble sous la forme du package de compétences `aem-cloud-service` ; installez le package une fois pour obtenir les deux.

### Prise en main {#getting-started-skill}

1. Installez le package de compétences `aem-cloud-service` à partir du référentiel de compétences [Adobe](https://github.com/adobe/skills).
2. Ouvrez votre projet AEM en tant que racine de l’espace de travail dans votre IDE.
3. Obtenir des résultats BPA : exportez un fichier CSV à partir de BPA ou configurez le MCP de migration vers le cloud (voir ci-dessous).
4. Démarrez une session avec votre agent à l’aide de l’une des invites suivantes :

   **BPA CSV:**

   ```
   Use the migration skill: scheduler only, BPA CSV at ./reports/bpa.csv
   ```

   **CAM via MCP:**

   ```
   Fix replictaion findings from project <projectname>/<projectId>.
   ```

   **Manuel (pas de BPA) :**

   ```
   Migrate event listener in core/src/main/java/com/example/Listener.java
   ```

   **Configurations OSGi :**

   ```
   Scan my config files and create Cloud Manager environment secrets or variables.
   ```

   **HTL lint:**

   ```
   Fix htlLint in ui.apps - scan for data-sly-test redundant constant warnings.
   ```

>[!NOTE]
>La compétence traite un modèle par session. Si votre rapport BPA contient plusieurs modèles, l’agent vous demande d’en choisir un avant de commencer.

Pour obtenir une référence complète aux modèles et des conseils sur la gestion des sessions, voir [ Utilisation des compétences de migration vers le cloud ](/help/journey-migration/cloud-migration-skill/using-cloud-migration-skill.md).

## MCP de migration vers le cloud {#cloud-migration-mcp}

Le MCP **AEM Cloud Migration** est un serveur [Model Context Protocol](https://modelcontextprotocol.io) qui connecte votre agent IDE à Cloud Acceleration Manager. Une fois configurée, la compétence de migration peut récupérer les résultats BPA directement à partir de votre projet CAM sans nécessiter de téléchargement de CSV.

### Avantages du MCP {#mcp-tools}

| Outil | Description |
|------|-------------|
| `fetch-cam-bpa-findings-by-pattern` | Renvoie les résultats BPA pour un modèle de migration de code spécifique à partir du dernier rapport BPA dans un projet CAM. |
| `fetch-cam-bpa-findings-by-importance` | Renvoie tous les résultats de l’analyseur de bonnes pratiques à une gravité donnée (`CRITICAL`, `MAJOR`, `ADVISORY`, `INFO`), triés par nombre. Utile pour établir la priorité des modèles à utiliser en premier. |

Ces outils sont appelés automatiquement par la compétence de migration ; vous ne les appelez pas directement.

### Prise en main {#getting-started-mcp}

1. Dans la configuration MCP de votre IDE, ajoutez l’URL du serveur MCP de migration vers le cloud : `https://mcp.adobeaemcloud.com/adobe/mcp/cloud-migration`
2. Lorsque vous y êtes invité, connectez-vous avec votre Adobe ID pour vous authentifier auprès de Cloud Acceleration Manager.
3. Les compétences de migration peuvent désormais récupérer les résultats BPA directement à partir de vos projets CAM.

Pour obtenir une configuration et un dépannage détaillés, voir [Utilisation du MCP de migration vers le cloud](/help/journey-migration/cloud-migration-skill/using-cloud-migration-mcp.md).

## Comment ils s’intègrent dans le Parcours de la migration {#migration-journey}

Les compétences et le MCP complètent les autres outils de la **phase de mise en œuvre** :

- **Best Practices Analyzer** : produit les résultats qui pilotent la compétence. Voir [ Utilisation de l’analyseur des bonnes pratiques ](/help/journey-migration/best-practices-analyzer/using-best-practices-analyzer.md).
- **** : héberge les rapports BPA et suit la progression globale de la migration. Voir [Prise en main de CAM](/help/journey-migration/cloud-acceleration-manager/using-cam/getting-started-cam.md).
- **Outils de refactorisation** : gère la structure du référentiel et la modernisation de la configuration du Dispatcher. Voir [Présentation des outils de refactorisation](/help/journey-migration/refactoring-tools/overview-refactoring-tools.md).
- **Outil de transfert de contenu** : migre le contenu du référentiel d’AEM 6.x vers AEMaaCS.

Pour une vue d’ensemble, consultez la [ Présentation de la phase d’implémentation ](/help/journey-migration/implementation.md).

