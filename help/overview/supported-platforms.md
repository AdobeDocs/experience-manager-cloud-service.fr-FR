---
title: Plateformes clientes prises en charge
description: Découvrez les navigateurs pris en charge pour la création de contenu avec Adobe Experience Manager as a Cloud Service et l’accès aux sites publiés avec AEM.
topic-tags: platform
solution: Experience Manager, Experience Manager Sites
feature: Deploying
role: Admin
exl-id: 7ddd0a75-621a-4499-91d1-7b3408a68269
source-git-commit: bb149cd43158bfd1ceb43b04cc536c8c8291f968
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 99%

---

# Plateformes clientes prises en charge {#supported-platforms}

Découvrez les navigateurs pris en charge pour la création de contenu avec Adobe Experience Manager as a Cloud Service et l’accès aux sites publiés avec AEM.

>[!TIP]
>
>Ce document couvre les plateformes clientes prises en charge par AEM as a Cloud Service. Pour plus d’informations sur l’environnement de génération pour le développement de votre projet AEM, consultez le document [Environnement de création.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md)

## Niveaux de prise en charge {#support-levels}

Adobe définit les niveaux de prise en charge suivants pour les plateformes clientes AEM.

| Niveau de prise en charge | Description |
|---|---|
| A : pris en charge | Adobe fournit une prise en charge et une maintenance complètes de cette configuration. Cette configuration est couverte par le processus d’assurance qualité d’Adobe. |
| R : Prise en charge limitée  | Pour utiliser la configuration dans un projet, une demande officielle doit être adressée à Adobe. Une fois la confirmation d’Adobe obtenue, Adobe fournit une prise en charge complète dans les limites du programme d’assistance restreint. Pour plus d’informations, contactez l’assistance clientèle d’Adobe. |
| Z : non pris en charge | La configuration n’est pas prise en charge. Adobe ne fait aucune déclaration indiquant si la configuration fonctionne et ne la prend pas en charge. |

## Navigateurs pris en charge pour la création de contenu {#authoring}

L’interface d’utilisation d’AEM est optimisée pour les grands écrans, généralement les notebooks, les ordinateurs de bureau et les tablettes (Apple iPad ou Microsoft Surface, par exemple). Le format de téléphone n’est pris en charge dans aucun cas d’utilisation de création.

L’interface d’utilisation d’Adobe Experience Manager fonctionne avec les plateformes clientes suivantes en fonction de la [méthode de création.](/help/edge/overview.md#authoring-method)

* [Éditeur universel](/help/sites-cloud/authoring/universal-editor/authoring.md)
* [Éditeur de page](/help/sites-cloud/authoring/page-editor/introduction.md)
* [Création basée sur des documents](https://www.aem.live/docs/aem-authoring) à l’aide de [Sidekick](https://www.aem.live/docs/sidekick)

Tous les navigateurs sont testés avec l’ensemble par défaut de plug-ins et de modules complémentaires.

| Navigateur | Niveau de prise en charge de l’éditeur universel | Niveau de prise en charge de l’éditeur de page | Niveau de prise en charge de Sidekick |
|---|---|---|---|
| Google Chrome (Evergreen) | A : pris en charge | A : pris en charge | A : pris en charge |
| Microsoft Edge (Evergreen) | A : pris en charge | A : pris en charge | Z : non pris en charge |
| Mozilla Firefox (Evergreen) | A : pris en charge | A : pris en charge | Z : non pris en charge |
| Mozilla Firefox, dernier ESR [1] | A : pris en charge | A : pris en charge | Z : non pris en charge |
| Safari sous macOS (Evergreen) | A : pris en charge | A : pris en charge | Z : non pris en charge |
| Safari sous iPadOS (Evergreen) | Z : non pris en charge | A : pris en charge | Z : non pris en charge |

1. Version de prise en charge étendue de Firefox ([en savoir plus sur mozilla.org](https://www.mozilla.org/fr/firefox/enterprise/))

>[!NOTE]
>
>**Prise en charge des navigateurs avec des cycles de version rapides :**
>
>Firefox, Chrome et Edge publient régulièrement des mises à jour. Adobe s’engage à maintenir le niveau de prise en charge comme indiqué ci-dessus pour les versions ultérieures de ces navigateurs.

## Navigateurs pris en charge pour les sites web {#websites}

La prise en charge des navigateurs pour les sites web rendus par AEM dépend de l’implémentation des modèles de page, des blocs, de la conception et de la sortie des composants d’AEM. Par conséquent, l’équipe de développement qui met en œuvre votre projet est également responsable du niveau de compatibilité de votre site.

Les [modèles de projet standard](https://www.aem.live/developer/ue-tutorial#create-github-project), les [composants principaux](/help/implementing/developing/components/overview.md#aem-core-components) et l’[exemple de site WKND](/help/implementing/developing/introduction/develop-wknd-tutorial.md) d’AEM sont compatibles avec tous les navigateurs modernes.
