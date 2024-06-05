---
title: Multi Site Manager et traduction
description: Découvrez comment réutiliser votre contenu dans tout votre projet et comment gérer des sites web multilingues dans AEM.
feature: Administering
role: Admin
exl-id: a3d48884-081e-44f8-8055-ee3657757bfd
solution: Experience Manager Sites
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 96%

---

# Multi Site Manager et traduction {#msm-and-translation}

L’intégration de Multi Site Manager et d’outils de traduction à Adobe Experience Manager simplifie la localisation de votre contenu.

* Multi Site Manager (MSM) et ses fonctionnalités Live Copy vous permettent d’utiliser le même contenu de site à plusieurs emplacements, tout en permettant des variations :
   * [Réutilisation de contenu : Multi Site Manager et Live Copy](msm/overview.md)
* La traduction permet d&#39;automatiser la traduction du contenu des pages afin de créer et gérer des sites web multilingues :
   * [Traduction de contenu pour les sites multilingues](translation/overview.md)

Ces deux fonctions peuvent être combinées pour gérer les sites web qui sont à la fois [internationaux et multilingues](#multinational-and-multilingual-sites).

>[!TIP]
>
>Si vous débutez dans la traduction de contenu, référez-vous à notre [Parcours de traduction Sites](/help/journey-sites/translation/overview.md). Cette page vous guide sur le chemin de la traduction de votre contenu AEM Sites à l’aide des puissants outils de traduction d’AEM, idéaux pour celles et ceux qui ne disposent pas d’une expérience concernant AEM ou la traduction.

## Sites internationaux et multilingues {#multinational-and-multilingual-sites}

Vous pouvez créer efficacement du contenu pour les sites internationaux et multilingues par l’utilisation conjointe de Multi Site Manager et du workflow de traduction.

Vous pouvez généralement créer un site principal dans une langue, pour un pays spécifique, puis utiliser ce contenu comme base des autres sites, à l’aide de la traduction si nécessaire.

1. [Traduisez](translation/overview.md) le site principal dans différentes langues.
1. Utilisez [Multi Site Manager](msm/overview.md) pour effectuer les tâches suivantes :
   1. Réutilisez le contenu du site principal et ses traductions afin de créer des sites pour d’autres pays et cultures.
   1. Si nécessaire, désolidarisez les éléments des Live Copies pour ajouter les détails de localisation.

>[!TIP]
>
>Limitez l’utilisation de Multi Site Manager au contenu d’une seule langue.
>
>Par exemple, utilisez le gabarit anglais pour créer la version anglaise des pages pour les États-Unis, le Canada et le Royaume-Uni. Ensuite, utilisez le gabarit français pour créer la version française des pages pour la France, la Suisse, le Canada, etc.

Le diagramme suivant illustre la manière dont les principaux concepts sont en corrélation (mais n’affiche pas tous les niveaux/éléments impliqués) :

![Présentation de la localisation](assets/localization-overview.png)

Dans ces scénarios et dans d’autres scénarios comparables, MSM ne gère pas les différentes versions de langues en tant que telles.

* [MSM](msm/overview.md) gère le déploiement du contenu traduit d’un plan directeur (par exemple, un gabarit mondial) vers des Live Copies (par exemple, les sites locaux), dans les limites d’une langue.
* Les fonctionnalités d’intégration de la [traduction](translation/overview.md) d’AEM, avec des services de gestion de traduction tiers, gèrent les langues et traduisent le contenu dans ces différentes langues.

Pour les cas d’utilisation plus avancés, MSM peut également être utilisé dans des langues principales.

>[!TIP]
>
>Dans tous les cas, il est recommandé de lire les bonnes pratiques suivantes :
>
>* [Bonnes pratiques liées à MSM](msm/best-practices.md)
>* [Bonnes pratiques de traduction](translation/best-practices.md)
