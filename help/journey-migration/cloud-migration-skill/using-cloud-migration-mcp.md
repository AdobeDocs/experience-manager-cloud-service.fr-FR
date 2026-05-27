---
title: Utilisation du MCP de migration vers le cloud d’AEM
description: Découvrez comment ajouter le serveur MCP de migration vers le cloud AEM à votre IDE compatible avec l’IA et l’utiliser pour récupérer les résultats de l’analyseur de bonnes pratiques à partir de Cloud Acceleration Manager au cours d’une session de migration.
feature: Migration
role: Developer
source-git-commit: 5cda629090d9a9d020deca5192b8a89659ec4749
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 1%

---


# Utilisation du MCP de migration vers le cloud d’AEM {#using-cloud-migration-mcp}

Le **MCP de migration vers le cloud** est un serveur hébergé [Model Context Protocol (MCP)](https://modelcontextprotocol.io) qui connecte votre agent IDE à **Cloud Acceleration Manager (CAM)**. Une fois configurée, la [compétence de migration vers le cloud &#x200B;](/help/journey-migration/cloud-migration-skill/overview-cloud-migration-skill.md) peut récupérer les résultats de l’analyseur des bonnes pratiques directement à partir de votre projet CAM sans nécessiter d’exportation au format CSV.

## URL du serveur MCP {#server-url}

```
https://mcp.adobeaemcloud.com/adobe/mcp/cloud-migration
```

Ajoutez cette URL à la configuration MCP de votre IDE pour vous connecter.

## Ce qu’il fournit {#what-it-provides}

Le serveur MCP expose deux outils que la compétence de migration appelle automatiquement au cours d’une session :

| Outil | Description |
|------|-------------|
| `fetch-cam-bpa-findings-by-pattern` | Renvoie les résultats BPA pour un modèle de migration spécifique (`scheduler`, `assetApi`, `eventListener`, `resourceChangeListener`, `eventHandler` ou `all`) à partir du dernier rapport BPA dans un projet CAM. |
| `fetch-cam-bpa-findings-by-importance` | Renvoie tous les résultats BPA avec une gravité donnée (`CRITICAL`, `MAJOR`, `ADVISORY`, `INFO`) à partir du dernier rapport BPA, trié par nombre décroissant. Utile pour établir la priorité des modèles à traiter en premier. |

## Conditions préalables {#prerequisites}

* Un projet **&#x200B;**&#x200B;avec un rapport BPA chargé. Voir [Phase de préparation de CAM](/help/journey-migration/cloud-acceleration-manager/using-cam/cam-readiness-phase.md).
* Un **&#x200B;**&#x200B;ayant accès à ce projet CAM.
* Un IDE compatible avec l’IA qui prend en charge les serveurs MCP distants.

## Configuration {#setup}

1. Dans la configuration MCP de votre IDE, ajoutez une nouvelle entrée de serveur MCP avec l’URL `https://mcp.adobeaemcloud.com/adobe/mcp/cloud-migration`.
2. Enregistrez ou activez la configuration afin que votre IDE se connecte au serveur.
3. Lorsque vous y êtes invité, connectez-vous avec votre **&#x200B;**&#x200B;pour terminer l’authentification.
4. Une fois authentifié, votre IDE découvre les outils de migration disponibles et les compétences de migration peuvent les utiliser dans les sessions.

Pour connaître les étapes de configuration spécifiques à IDE, reportez-vous aux guides sous [Configuration de MCP avec AEM](/help/ai-in-aem/mcp-support/using-mcp-with-aem-as-a-cloud-service.md).

>[!NOTE]
>Vous devez vous connecter avec l’Adobe ID ayant accès à vos projets CAM. Si une erreur d’autorisation s’affiche, vérifiez que votre compte dispose des autorisations appropriées dans Cloud Acceleration Manager.

## Utilisation du MCP dans une session de migration {#using-in-session}

Une fois le serveur MCP connecté, démarrez une session de migration dans votre IDE à l’aide d’une invite telle que :

```
Fetch scheduler findings for project <name>/<id>.
```

L’agent :

1. Récupère les résultats de l’analyseur des bonnes pratiques pour ce projet
2. Poursuit le workflow de migration lot par lot

>[!IMPORTANT]
>Confirmez toujours le projet à partir de la liste avant que l’agent ne continue. Les résultats ne sont récupérés que lorsque vous avez explicitement sélectionné un projet.

### Hiérarchisation par gravité {#by-severity}

Pour afficher un résumé trié par décompte des résultats de votre rapport BPA avant de commencer la migration des modèles :

```
Show me CRITICAL findings from CAM for project <name>/<id>.
```

Utilisez-la pour décider des modèles à prioriser dans vos sessions.

## Résolution des problèmes {#troubleshooting}

**IDE ne peut pas se connecter au serveur MCP**

* Vérifiez que l’URL est saisie exactement comme indiqué ci-dessus, sans barre oblique
* Redémarrez votre IDE après avoir enregistré la configuration MCP

**Échec de l’authentification**

* Vérifiez que vous vous connectez avec l’Adobe ID ayant accès à vos projets CAM

**Aucun rapport BPA trouvé**

* Vérifiez qu’un rapport BPA a été chargé dans le projet CAM sélectionné. Voir [&#x200B; Utilisation de l’analyseur des bonnes pratiques &#x200B;](/help/journey-migration/best-practices-analyzer/using-best-practices-analyzer.md).

## Prochaines étapes {#whats-next}

Une fois le MCP configuré, reportez-vous à la section [&#x200B; Utilisation des compétences de migration vers le cloud &#x200B;](/help/journey-migration/cloud-migration-skill/using-cloud-migration-skill.md) pour obtenir des informations complètes sur les modèles de migration et la gestion des sessions.

