---
title: Utilisation des compétences de migration vers le cloud AEM
description: Référence pour chaque modèle de migration pris en charge par les compétences de migration vers le cloud AEM, y compris la conversion de configuration OSGi, les options de source BPA et les conseils de gestion de session.
feature: Migration
role: Developer
source-git-commit: 7ea634871fc1655e5f0ec5b3fb88edbb0f317249
workflow-type: tm+mt
source-wordcount: '890'
ht-degree: 0%

---


# Utilisation des compétences de migration vers le cloud AEM {#using-cloud-migration-skill}

Cette référence couvre chaque modèle de migration pris en charge, la manière de fournir des résultats BPA et de gérer les sessions dans un projet volumineux. Pour obtenir une introduction et des instructions de configuration, consultez la [présentation](/help/journey-migration/cloud-migration-skill/overview-cloud-migration-skill.md).

## Fonctionnement d’une session {#workflow-overview}

Chaque session de migration suit cette séquence :

1. **Nommez le modèle** : spécifiez un modèle (par exemple, `scheduler`)
2. **Fournir des résultats** : à partir d’un fichier CSV BPA, CAM via MCP ou de chemins d’accès à des fichiers spécifiques
3. **L’agent lit les règles de transformation** : la compétence lit les règles de transformation appropriées de la compétence `code-assessment` compagnon avant d’apporter des modifications au code
4. **Premier lot de cinq** : l’agent transforme jusqu’à cinq résultats et signale ce qu’il a modifié
5. **Vous vérifiez et continuez** : après avoir vérifié chaque lot, répondez `continue` pour passer au suivant

L’agent traite un modèle et un lot à la fois. Il ne se poursuit pas automatiquement ; chaque lot nécessite votre confirmation.

## Modèles de migration {#patterns}

### Planificateur {#scheduler}

Cible les classes Java à l’aide de l’injection `sling.commons.scheduler` ou `Scheduler` qui sont incompatibles avec l’exécution en conteneur sans état d’AEMaaCS.

**Identifiant de modèle BPA :** `scheduler`

L’agent convertit les tâches injectées par `Scheduler` en implémentations `@Component` de `Runnable` à l’aide de `@Designate`, en remplaçant l’enregistrement du planificateur basé sur le constructeur par des méthodes de cycle de vie `@Activate`/`@Deactivate`.

### ResourceChangeListener {#resource-change-listener}

Cible les implémentations de listener `ResourceChangeListener` ou `ResourceChange` qui nécessitent des mises à jour pour AEMaaCS.

**Identifiant de modèle BPA :** `resourceChangeListener`

### Réplication {#replication}

Classes cibles important des API de réplication `com.day.cq.replication.Replicator` ou associées, qui ne sont pas prises en charge dans AEMaaCS. L’agent les remplace par des équivalents basés sur `ContentDistribution` et met à jour les références de service OSGi correspondantes.

**Identifiant de modèle BPA :** `replication`

### Écouteur d’événement {#event-listener}

Cible les implémentations OSGi `EventListener` ou `EventHandler` qui doivent être mises à jour pour la sémantique de traitement des événements AEMaaCS.

**Identifiant de modèle BPA :** `eventListener`

### Gestionnaire d&#39;événements {#event-handler}

Cible les services `EventHandler` OSGi synchrones qui doivent être adaptés à AEMaaCS.

**Identifiant de modèle BPA :** `eventHandler`

### API de ressources {#asset-api}

Cible les classes à l’aide d’API `AssetManager`, `DAMEvent` ou DAM non prises en charge obsolètes. L’agent les remplace par les équivalents API AEM Assets pris en charge.

**Identifiant de modèle BPA :** `assetApi`

### HTL Lint (data-sly-test) {#htl-lint}

Cible les modèles HTL sous `ui.apps` qui génèrent des avertissements `data-sly-test: redundant constant value comparison`. L’agent détecte les modèles affectés en analysant directement le package de contenu ; ce modèle ne nécessite pas de connexion CSV ou CAM BPA.

**Identifiant de modèle BPA :** `htlLint`

>[!NOTE]
>`htlLint` résultats n’apparaissent pas dans les exportations CSV BPA. L’agent les découvre par analyse directe des fichiers lorsque vous démarrez une session pour ce modèle.

### Configurations OSGi pour Cloud Manager {#osgi-cloud-manager}

Convertit les configurations OSGi en `ui.config` au format `.cfg.json` compatible avec Cloud Manager avec une gestion complète spécifique à l’environnement. Cela couvre deux tâches associées :

**Conversion du format de configuration**

AEMaaCS nécessite que les configurations OSGi soient stockées sous la forme de fichiers `.cfg.json`, avec des configurations spécifiques à l’environnement dans les dossiers dont le mode d’exécution a la portée (`config.author/`, `config.publish/`, `config.dev/`, etc.). L’agent :

* Convertit les configurations OSGi `.config`, `.cfg` et au format XML existantes en `.cfg.json`
* Divise les configurations contenant à la fois des valeurs spécifiques à l’auteur et à la publication en fichiers distincts de l’étendue du mode d’exécution
* Valide les types de propriété par rapport à la spécification du métatype OSGi (chaînes, entiers, booléens, tableaux).
* Indique les PID appartenant à Adobe pour une révision manuelle plutôt que pour une conversion automatique

**Secrets et variables d’environnement**

Déplace les secrets en texte brut et les valeurs spécifiques à l’environnement des fichiers de configuration validés et les remplace par des espaces réservés Cloud Manager :

* `$[secret:NAME]` : pour les mots de passe, jetons et autres valeurs sensibles
* `$[env:NAME]` : pour les valeurs non sensibles qui diffèrent par environnement (par exemple, les URL de service)

Les variables et secrets correspondants sont appliqués dans Cloud Manager et injectés au moment de l’exécution ; aucune valeur n’est stockée dans le contrôle de code source.

>[!IMPORTANT]
>L’agent ne génère jamais de valeurs secrètes dans la conversation. Toutes les données sensibles sont écrites dans un fichier de remise ignoré pour que vous puissiez les appliquer via l’API ou l’interface utilisateur de Cloud Manager.

**Ce modèle n’utilise pas BPA CSV ni CAM.** Démarrer une session avec :

```
Scan my config files and create Cloud Manager environment secrets or variables.
```

## Options Source BPA {#bpa-source}

| Source | Quand l’utiliser |
|--------|------------|
| **Fichier CSV BPA** | Vous avez exporté un fichier CSV à partir de votre instance AEM ou Cloud Acceleration Manager. Indiquez le chemin d’accès au fichier lors du démarrage de la session. |
| **CAM via MCP** | Le MCP Migration vers le cloud AEM est configuré. L’agent répertorie vos projets CAM, vous confirmez lequel utiliser et les résultats sont directement récupérés. Voir [Utilisation du MCP de migration vers le cloud](/help/journey-migration/cloud-migration-skill/using-cloud-migration-mcp.md). |
| **Chemins d’accès manuels aux fichiers** | Vous souhaitez migrer des fichiers spécifiques sans rapport BPA. Indiquez les chemins directement dans votre invite. |

### Gestion des erreurs MCP {#mcp-errors}

Si la connexion MCP renvoie une erreur (notamment un projet introuvable ou des échecs d’authentification), l’agent s’arrête et vous indique l’erreur. Il ne bascule pas automatiquement vers une autre source. À partir de l’état arrêté , vous pouvez :

* Confirmez le projet correct à partir de la liste de l’agent affichée
* Fournir un chemin d’accès CSV BPA en alternative
* Fournir des chemins d’accès aux fichiers Java spécifiques pour une migration manuelle

## Gestion des sessions dans les rapports volumineux {#large-reports}

Pour les rapports BPA comportant de nombreux résultats, l’approche lot par lot vous permet de valider de manière incrémentielle :

1. Vérifier la différence pour chaque lot
2. Validez le lot avec un message de validation dont la portée est définie sur un modèle
3. Répondre `continue` pour démarrer le lot suivant
4. Répétez l&#39;opération jusqu&#39;à ce que l&#39;agent signale que tous les résultats du modèle ont été obtenus

**Un modèle par validation** rend votre historique Git lisible et permet d’annuler facilement les transformations individuelles des modèles, si nécessaire.

>[!NOTE]
>Si vous mettez fin à une session avant que tous les résultats ne soient traités, redémarrez avec le même modèle et la même source BPA dans une nouvelle session. L’agent reprend là où il s’est arrêté.

## Workspace Scope {#workspace-scope}

L’agent recherche et modifie uniquement les fichiers dans les dossiers de l’espace de travail IDE ouverts. Il n’analyse pas les répertoires parents, les dossiers frères ni d’autres emplacements sur le disque.

Si un résultat de recherche BPA fait référence à un chemin d’accès au fichier qui n’existe pas dans l’espace de travail, l’agent s’arrête et vous indique quels chemins d’accès sont manquants. Ouvrez le dossier de projet approprié ou indiquez explicitement les chemins d’accès pour continuer.

