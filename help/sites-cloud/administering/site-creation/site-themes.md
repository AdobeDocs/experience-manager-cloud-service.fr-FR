---
title: Thèmes de site
description: Découvrez comment AEM thèmes de site peuvent être utilisés pour personnaliser le style et la conception de votre site.
feature: Administering
role: Admin
exl-id: 53d4afb3-d091-47a1-ba12-5bcec99f46b9
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 1%

---

# Thèmes de site {#site-themes}

Découvrez comment AEM thèmes de site peuvent être utilisés pour personnaliser le style et la conception de votre site.

## Présentation {#overview}

Un thème de site AEM est un module contenant les ressources statiques, CSS et JavaScript qui définissent le style de votre site AEM et se conforme à la structure d’un thème de site AEM.

Les sites créés avec des modèles de site AEM permettent de télécharger, de personnaliser et de redéployer facilement les thèmes.

>[!NOTE]
>
>AEM thèmes de site ne doivent pas être confondus avec [ des modèles de site.](site-templates.md) Les thèmes AEM site contiennent uniquement les informations de style d’un site AEM. AEM modèles de site définissent la structure du site et le contenu initial, ainsi qu’un thème de site AEM afin de permettre [création rapide de site.](create-site.md)

## Utilisation des thèmes du site {#using-themes}

Les thèmes du site sont utilisés de deux manières différentes :

* Ils sont utilisés dans le cadre d’un modèle de site pour définir le style lors de la [création d’un site.](create-site.md)
* Ils sont téléchargés après la création d’un site basé sur un modèle de site afin qu’un développeur front-end puisse personnaliser davantage le style.

>[!TIP]
>
>Vous trouverez une description de bout en bout du processus de création d’un site à partir d’un modèle et de personnalisation de son thème dans la section [Parcours de création rapide de site.](/help/journey-sites/quick-site/overview.md)

## Structure du thème du site {#structure}

Les thèmes du site sont simplement des modules avec une structure logique qui reflète clairement l’objectif du contenu du module. Un thème de site présente la structure suivante typique d’un projet front-end.

* `src/main.ts`: Point d’entrée principal de votre thème JS et CSS
* `src/site`: Fichiers JS et CSS qui s’appliquent à l’ensemble du site
* `src/components`: Fichiers JS et CSS spécifiques aux composants AEM
* `src/resources`: Fichiers statiques (icônes, logos et polices)

## Thème de site standard {#standard-site-theme}

Adobe fournit un thème de référence des bonnes pratiques que vous pouvez utiliser comme base pour créer votre propre thème. [Le thème de site standard est disponible sur GitHub.](https://github.com/adobe/aem-site-template-standard-theme-e2e)

## Développement de thèmes de site {#developing-themes}

Adobe fournit un Créateur de thèmes de site AEM sous la forme d’un ensemble de scripts permettant de créer des thèmes de site.

[AEM Créateur de thèmes de site est disponible avec la documentation d’utilisation sur GitHub.](https://github.com/adobe/aem-site-theme-builder) Une expérience de développement front-end est requise pour personnaliser le thème.
