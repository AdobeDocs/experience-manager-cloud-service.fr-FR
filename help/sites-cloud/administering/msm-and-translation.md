---
title: Gestionnaire et traduction multisite
description: Découvrez comment réutiliser votre contenu dans votre projet et gérer des sites Web multilingues dans AEM.
feature: Administration
role: Administrator
translation-type: tm+mt
source-git-commit: 0f2b7176b44bb79bdcd1cecf6debf05bd652a1a1
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 36%

---


# Gestionnaire de sites multiples et traduction {#msm-and-translation}

La mise en place d’un gestionnaire multisite intégré et d’outils de traduction simplifie la localisation de votre contenu.

* Le gestionnaire multisite (MSM) et ses fonctionnalités Live Copy vous permettent d’utiliser le même contenu de site en plusieurs emplacements, tout en permettant des variations :
   * [Réutilisation de contenu : Multi Site Manager et Live Copy](msm/overview.md)
* La traduction vous permet d’automatiser la traduction du contenu des pages afin de créer et de gérer des sites Web multilingues :
   * [Traduction de contenu pour les sites multilingues](translation/overview.md)

Ces deux fonctionnalités peuvent être combinées pour répondre aux sites Web [multinationaux et multilingues](#multinational-and-multilingual-sites).

## Sites internationaux et multilingues {#multinational-and-multilingual-sites}

Vous pouvez créer efficacement du contenu pour les sites internationaux et multilingues par l’utilisation conjointe de Multi Site Manager et du workflow de traduction.

En règle générale, vous créez un site maître dans une langue et pour un pays spécifique, puis vous utilisez ce contenu comme base pour les autres sites, en utilisant la traduction si nécessaire.

1. [Traduisez](translation/overview.md) le site de gabarit dans différentes langues.
1. Utilisez [Multi Site Manager](msm/overview.md) pour effectuer les tâches suivantes :
   1. Réutilisez le contenu du site maître et ses traductions pour créer des sites pour d&#39;autres pays et cultures.
   1. Si nécessaire, détachez des éléments des Live Copies pour ajouter des détails de localisation.

>[!TIP]
>
>Limitez l’utilisation de Multi Site Manager au contenu d’une langue.
>
>Par exemple, utilisez le gabarit anglais pour créer la version anglaise des pages pour les États-Unis, le Canada, le Royaume-Uni, etc. et utiliser le gabarit français pour créer la version française des pages pour la France, la Suisse, le Canada, etc.

Le diagramme suivant illustre la manière dont les principaux concepts sont en corrélation (mais n’affiche pas tous les niveaux/éléments impliqués) :

![Présentation de la localisation](assets/localization-overview.png)

Dans ces scénarios et dans d’autres scénarios comparables, MSM ne gère pas les différentes versions de langues en tant que telles.

* [](msm/overview.md) MSMgère le déploiement du contenu traduit d&#39;un plan directeur (c&#39;est-à-dire un gabarit global) vers les Live Copies (c&#39;est-à-dire les sites locaux), dans les limites d&#39;une langue.
* Les fonctionnalités d’intégration de [traduction](translation/overview.md) d’AEM, combinées aux services de gestion de traduction tiers, gèrent les langues et le contenu de traduction dans ces différentes langues.

Pour les cas d’utilisation plus avancés, MSM peut également être utilisé dans les gabarits de langue.

>[!TIP]
>
>Dans tous les cas, il est recommandé de lire les meilleures pratiques suivantes :
>
>* [Bonnes pratiques relatives aux médias multimédias](msm/best-practices.md)
>* [Meilleures pratiques de traduction](translation/best-practices.md)

