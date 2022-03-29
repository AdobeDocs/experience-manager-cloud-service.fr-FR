---
title: Thèmes de site
description: Découvrez comment les thèmes de site AEM peuvent être utilisés pour personnaliser le style et la conception de votre site.
feature: Administering
role: Admin
exl-id: 53d4afb3-d091-47a1-ba12-5bcec99f46b9
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 100%

---

# Thèmes de site {#site-themes}

Découvrez comment les thèmes de site AEM peuvent être utilisés pour personnaliser le style et la conception de votre site.

## Présentation {#overview}

Un thème de site AEM est un package contenant les ressources statiques, CSS et JavaScript qui définissent la mise en forme de votre site AEM et se conforme à la structure d’un thème de site AEM.

Les sites créés avec des modèles de site AEM permettent de télécharger, de personnaliser et de redéployer facilement les thèmes.

>[!NOTE]
>
>Les thèmes de site AEM ne doivent pas être confondus avec les modèles de site [AEM.](site-templates.md) Les thèmes de site AEM contiennent uniquement les informations de style d’un site AEM. Les modèles de site AEM définissent la structure du site et le contenu initial et contiennent un thème de site AEM afin de permettre une [création rapide de site.](create-site.md)

## Utilisation des thèmes de site {#using-themes}

Les thèmes de site sont utilisés de deux manières différentes :

* Ils sont utilisés dans le cadre d’un modèle de site pour définir la mise en forme lors de la [création d’un site.](create-site.md)
* Ils sont téléchargés après la création d’un site basé sur un modèle de site afin qu’un développeur front-end puisse personnaliser davantage la mise en forme.

>[!TIP]
>
>Vous trouverez une description de bout en bout du processus de création d’un site à partir d’un modèle et de personnalisation de son thème dans le [Parcours de création rapide de site.](/help/journey-sites/quick-site/overview.md)

## Structure des thèmes de site {#structure}

Les thèmes du site sont simplement des packages avec une structure logique qui reflète clairement l’objectif du contenu du package. Un thème de site présente la structure suivante typique d’un projet front-end.

* `src/main.ts` : point d’entrée principal de votre thème JS et CSS.
* `src/site` : fichiers JS et CSS qui s’appliquent à l’ensemble du site.
* `src/components` : fichiers JS et CSS spécifiques aux composants AEM.
* `src/resources` : fichiers statiques (icônes, logos et polices).

## Thème de site standard {#standard-site-theme}

Adobe fournit un thème de référence des bonnes pratiques que vous pouvez utiliser comme base pour créer votre propre thème. [Le thème de site standard est disponible sur GitHub.](https://github.com/adobe/aem-site-template-standard-theme-e2e)

## Développement de thèmes de site {#developing-themes}

Adobe fournit un Créateur de thèmes de site AEM sous la forme d’un ensemble de scripts permettant de créer des thèmes de site.

[Le Créateur de thèmes de site AEM est disponible avec la documentation d’utilisation sur GitHub.](https://github.com/adobe/aem-site-theme-builder) Une expérience de développement front-end est requise pour personnaliser le thème.
