---
title: Utilisation du panneau Site pour gérer le thème de votre site
description: Découvrez les puissantes fonctionnalités du panneau Site pour vous aider à personnaliser et gérer facilement le thème de votre site pour les projets de création AEM traditionnels avec une diffusion de publication.
feature: Administering
role: Admin
exl-id: 45785e5a-4fa2-4cf2-a300-f1865f6f5807
solution: Experience Manager Sites
recommendations: noDisplay, noCatalog
source-git-commit: 8c4b34a77ef85869048fae254728c58cf0d99b66
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 36%

---


# Utilisation du panneau Site pour gérer le thème de votre site {#site-panel}

{{traditional-aem}}

Découvrez les puissantes fonctionnalités du panneau Site pour vous aider à personnaliser et gérer facilement le thème de votre site pour les projets de création AEM traditionnels avec une diffusion de publication.

## Vue d’ensemble {#overview}

Le panneau Site vous permet de gérer le thème et les ressources de modèle de votre site pour les projets de création AEM traditionnels avec diffusion [publication).](/help/sites-cloud/authoring/author-publish.md) [Comme les autres panneaux](/help/sites-cloud/authoring/sites-console/console-side-panel.md) tels que les panneaux Arborescence de contenu, Références ou Chronologie, le panneau Site s’affiche en tant que panneau le plus à gauche de la console Sites et affiche des informations sur l’élément sélectionné. Contrairement aux autres panneaux, le panneau Site s’applique uniquement aux racines du site.

Le panneau Site permet de gérer les informations relatives au thème et au modèle pour votre site, notamment :

* [Le téléchargement des sources de thème](#downloading-theme-sources)
* [Le téléchargement de ressources de modèle telles que des structures filaires](#downloading-template-resources)
* [L’affichage et la modification des versions de thème](#theme-vrsions)
* [L’activation du pipeline front-end](#enabling-the-front-end-pipeline)

>[!TIP]
>
>Consultez la section [Parcours de création de site rapide](/help/journey-sites/quick-site/overview.md) pour vous familiariser avec l’outil de création rapide de site et le pipeline front-end afin de personnaliser facilement le thème de votre site.

## Télécharger les sources de thème {#downloading-theme-sources}

Lorsque vous créez un site dans AEM à partir d’un modèle de site [site](site-templates.md) vous pouvez télécharger votre [thème du site](site-themes.md) à l’aide du panneau Site.

Avec le panneau Site affiché dans la console Sites, sélectionnez la racine de votre site pour afficher les informations sur le thème du site.

![Téléchargement de sources de thème](/help/sites-cloud/administering/assets/download-theme-wireframe.png)

Sélectionnez **Télécharger des sources de thème** pour télécharger une copie locale du thème du site sous forme de fichier `.zip` à des fins de personnalisation.

## Télécharger les ressources de modèle {#downloading-template-resources}

Les [modèles de site](site-templates.md) peuvent contenir des informations en plus de la structure de contenu de votre site et du [thème du site.](site-themes.md) Les modèles de site peuvent contenir des designs de structure filaire ou d’autres fichiers liés au site, par exemple.

Si votre site est basé sur un modèle de site, avec le panneau Site affiché dans la console Sites, sélectionnez la racine de votre site pour afficher les informations sur le thème du site, y compris des ressources supplémentaires.

![Téléchargement de sources de thème](/help/sites-cloud/administering/assets/download-theme-wireframe.png)

Sélectionnez le ou les boutons situés sous l’en-tête **Télécharger des ressources de modèle supplémentaires** pour télécharger une copie locale des fichiers disponibles.

## Affichage et modification des versions d’un thème {#them-versions}

Si votre site est basé sur un modèle de site, il est possible que son thème ait déjà été personnalisé par votre développeur front-end. À l’aide du panneau Site, vous pouvez afficher la version du thème du site actuellement déployé et passer aux versions précédentes.

Avec le panneau Site affiché dans la console Sites, sélectionnez la racine de votre site pour afficher les informations sur le thème du site.

![Versions du site dans le panneau](/help/sites-cloud/administering/assets/theme-versions.png)

La version actuelle du thème s’affiche avec son hachage de validation et l’horodatage de sa dernière mise à jour.

Sélectionnez **Sélectionner la version** pour afficher les versions précédentes du thème.

![Sélection de la version du thème](/help/sites-cloud/administering/assets/select-theme-versions.png)

Sélectionnez la version à modifier, puis sélectionnez **Appliquer** pour effectuer la modification.

Si AEM détecte qu’une version plus récente du thème a été déployée via le pipeline front-end, mais n’est pas appliquée à votre site, une icône de notification s’affiche.

![Nouvelle version de l’indicateur de thème](/help/sites-cloud/administering/assets/new-theme-version.png)

Vous pouvez utiliser le bouton **Sélectionner la version** pour mettre à jour vers la nouvelle version du thème.

## Activation du pipeline front-end {#enabling-front-end-pipeline}

Si votre site n’a pas été créé à l’aide d’un modèle de site, il n’est pas possible d’utiliser le pipeline front-end pour personnaliser et déployer son thème.

Vous pouvez toutefois activer le pipeline front-end pour votre site à l’aide du panneau Site.

Avec le panneau Site affiché dans la console Sites, sélectionnez la racine de votre site pour afficher les informations sur le thème du site, puis sélectionnez **Activer le pipeline front-end**.

![Activation du pipeline front-end](/help/sites-cloud/administering/assets/enable-fep.png)

Pour plus d’informations, consultez le document [Activation du pipeline front-end.](enable-front-end-pipeline.md)
