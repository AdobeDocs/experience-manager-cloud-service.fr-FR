---
title: Plateformes clientes prises en charge
description: Découvrez les navigateurs pris en charge pour la création de contenu avec Adobe Experience Manager as a Cloud Service et l’accès aux sites publiés avec AEM.
topic-tags: platform
solution: Experience Manager, Experience Manager Sites
feature: Deploying
role: Admin
source-git-commit: 22d4e6b5f87221b2739cf1dd9d59b4652a014316
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 26%

---


# Plateformes clientes prises en charge {#supported-platforms}

Découvrez les navigateurs pris en charge pour la création de contenu avec Adobe Experience Manager as a Cloud Service et l’accès aux sites publiés avec AEM.

>[!TIP]
>
>Ce document couvre les plateformes clientes prises en charge par AEM as a Cloud Service. Pour plus d’informations sur l’environnement de génération pour le développement de votre projet AEM, consultez le document [Environnement de génération.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md)

## Niveaux de prise en charge {#support-levels}

Adobe définit les niveaux de prise en charge suivants pour les plateformes clientes AEM.

| Niveau de prise en charge | Description |
|---|---|
| A : pris en charge | Adobe fournit une prise en charge et une maintenance complètes de cette configuration. Cette configuration est couverte par le processus d’assurance qualité d’Adobe. |
| R : Prise en charge limitée  | La prise en charge nécessite une demande officielle à Adobe pour utiliser la configuration dans un projet. Une fois confirmé par Adobe, Adobe fournit une prise en charge complète dans le cadre du programme d’assistance restreint. Pour plus d’informations, contactez l’assistance clientèle d’Adobe. |
| Z : non pris en charge | La configuration n’est pas prise en charge. Adobe ne fait aucune déclaration indiquant si la configuration fonctionne et ne la prend pas en charge. |

## Navigateurs pris en charge pour la création de contenu {#authoring}

L’interface utilisateur d’AEM est optimisée pour les grands écrans des notebooks, des ordinateurs de bureau et des tablettes (comme Apple iPad ou Microsoft Surface). Le format de téléphone n’est pris en charge dans aucun cas d’utilisation de création.

L’interface utilisateur de Adobe Experience Manager fonctionne avec les plateformes clientes suivantes en fonction de [ méthode de création ](/help/edge/authoring-methods.md).

* [Éditeur universel](/help/sites-cloud/authoring/universal-editor/authoring.md)
* [Éditeur de page](/help/sites-cloud/authoring/page-editor/introduction.md)
* [Création basée sur des documents](/help/edge/docs/authoring.md) à l’aide de [Sidekick](/help/edge/docs/sidekick.md)

Tous les navigateurs sont testés avec l’ensemble par défaut de plug-ins et de modules complémentaires.

| Navigateur | Niveau de prise en charge de l’éditeur universel | Niveau de prise en charge de l’éditeur de page | Niveau de prise en charge de Sidekick |
|---|---|---|---|
| Google Chrome (reconduction tacite) | A : pris en charge | A : pris en charge | A : pris en charge |
| Microsoft Edge (evergreen) | A : pris en charge | A : pris en charge | Z : non pris en charge |
| Mozilla Firefox (vert persistant) | A : pris en charge | A : pris en charge | Z : non pris en charge |
| Mozilla Firefox le plus récent ESR [1] | A : pris en charge | A : pris en charge | Z : non pris en charge |
| Safari sur macOS (evergreen) | A : pris en charge | A : pris en charge | Z : non pris en charge |
| Safari sur iOS (evergreen) [2] | Z : non pris en charge | A : pris en charge | Z : non pris en charge |

1. Version de prise en charge étendue de Firefox ([en savoir plus sur mozilla.org](https://www.mozilla.org/fr/firefox/enterprise/))
1. Prise en charge d’Apple iPad uniquement

>[!NOTE]
>
>**Prise en charge des navigateurs avec des cycles de version rapides :**
>
>Firefox, Chrome et Edge publient régulièrement des mises à jour. Adobe s’engage à maintenir le niveau de prise en charge comme indiqué ci-dessus pour les versions à venir de ces navigateurs.

## Navigateurs pris en charge pour les sites web {#websites}

La prise en charge des navigateurs pour les sites web rendus par AEM dépend de l’implémentation des modèles de page, des blocs, de la conception et de la sortie des composants d’AEM. Par conséquent, les développeurs qui mettent en œuvre votre projet contrôlent en fin de compte la compatibilité de votre site.

Les modèles de projet AEM [standard](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md#create-github-project) [composants principaux](/help/implementing/developing/components/overview.md#aem-core-components) et [exemple de site WKND](/help/implementing/developing/introduction/develop-wknd-tutorial.md) sont tous compatibles avec tous les navigateurs modernes.
