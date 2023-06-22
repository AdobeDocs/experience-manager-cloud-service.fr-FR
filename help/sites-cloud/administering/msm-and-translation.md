---
title: Multi Site Manager et traduction
description: Découvrez comment réutiliser votre contenu dans tout votre projet et comment gérer des sites web multilingues dans AEM.
feature: Administering
role: Admin
exl-id: a3d48884-081e-44f8-8055-ee3657757bfd
source-git-commit: 1fc57dacbf811070664d5f5aaa591dd705516fa8
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 49%

---

# Multi Site Manager et traduction {#msm-and-translation}

L’intégration de Multi Site Manager et d’outils de traduction à Adobe Experience Manager simplifie la localisation de votre contenu.

* Multi Site Manager (MSM) et ses fonctionnalités Live Copy vous permettent d’utiliser le même contenu de site à plusieurs emplacements, tout en permettant des variations :
   * [Réutilisation de contenu : Multi Site Manager et Live Copy](msm/overview.md)
* La traduction vous permet d’automatiser la traduction du contenu des pages pour créer et tenir à jour des sites web multilingues :
   * [Traduction de contenu pour les sites multilingues](translation/overview.md)

Ces deux fonctions peuvent être combinées pour gérer les sites web qui sont à la fois [internationaux et multilingues](#multinational-and-multilingual-sites).

>[!TIP]
>
>Si vous commencez à traduire du contenu, reportez-vous à la section [Parcours de traduction de sites](/help/journey-sites/translation/overview.md). Il s’agit d’un chemin guidé permettant de traduire votre contenu AEM Sites à l’aide AEM puissants outils de traduction. idéal si vous n’avez pas d’AEM ou d’expérience de traduction.

## Sites internationaux et multilingues {#multinational-and-multilingual-sites}

Vous pouvez créer efficacement du contenu pour les sites internationaux et multilingues par l’utilisation conjointe de Multi Site Manager et du workflow de traduction.

En règle générale, vous créez un site Principal dans une langue et pour un pays spécifique, puis vous utilisez ce contenu comme base pour les autres sites, en utilisant la traduction si nécessaire.

1. [Traduire](translation/overview.md) le Principal site dans différentes langues.
1. Utilisez [Multi Site Manager](msm/overview.md) pour effectuer les tâches suivantes :
   1. Réutiliser le contenu du Principal site et ses traductions pour créer des sites pour d&#39;autres pays et cultures.
   1. Si nécessaire, désolidarisez les éléments des Live Copies pour ajouter les détails de localisation.

>[!TIP]
>
>Limitez l’utilisation de Multi Site Manager au contenu d’une seule langue.
>
>Par exemple, utilisez le Principal anglais pour créer la version anglaise des pages pour les pages États-Unis, Canada et Royaume-Uni. Ensuite, utilisez le Principal français pour créer la version française des pages pour la France, la Suisse, le Canada, etc.

Le diagramme suivant illustre la manière dont les principaux concepts sont en corrélation (mais n’affiche pas tous les niveaux/éléments impliqués) :

![Présentation de la localisation](assets/localization-overview.png)

Dans ce scénario, et dans les versions comparables, MSM ne gère pas les différentes versions linguistiques en tant que telles.

* [MSM](msm/overview.md) gère le déploiement du contenu traduit d’un plan directeur (c’est-à-dire d’un Principal global) vers les Live Copies (c’est-à-dire les sites locaux), dans les limites d’une langue.
* Le [translation](translation/overview.md) les fonctionnalités d’intégration d’AEM, avec des services de gestion de traduction tiers, gèrent les langues et traduisent le contenu dans ces différentes langues.

Pour les cas d’utilisation plus avancés, MSM peut également être utilisé dans de Principales langues.

>[!TIP]
>
>Dans tous les cas, il est recommandé de lire les bonnes pratiques suivantes :
>
>* [Bonnes pratiques liées à MSM](msm/best-practices.md)
>* [Bonnes pratiques de traduction](translation/best-practices.md)
