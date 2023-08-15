---
title: Utilisation du rail Site pour gérer le thème de votre site
description: Découvrez les puissantes fonctionnalités du rail Site qui vous aidera à personnaliser et gérer facilement le thème de votre site.
feature: Administering
role: Admin
exl-id: 45785e5a-4fa2-4cf2-a300-f1865f6f5807
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 97%

---

# Utilisation du rail Site pour gérer le thème de votre site {#site-rail}

Découvrez les puissantes fonctionnalités du rail Site qui vous aidera à personnaliser et gérer facilement le thème de votre site.

## Présentation {#overview}

Le rail Site vous permet de gérer le thème et les ressources de modèle de votre site. [Comme les autres rails](/help/sites-cloud/authoring/getting-started/basic-handling.md#rail-selector) tels que les rails Arborescence de contenu, Références ou Chronologie, le rail Site s’affiche dans le panneau le plus à gauche de la console Sites et affiche des informations sur l’élément sélectionné. Contrairement aux autres rails, le rail Site s’applique uniquement aux racines du site.

Le rail Site permet de gérer les informations relatives aux thèmes et aux modèles pour votre site, notamment les éléments suivants :

* [Le téléchargement des sources de thème](#downloading-theme-sources)
* [Le téléchargement de ressources de modèle telles que des structures filaires](#downloading-template-resources)
* [L’affichage et la modification des versions de thème](#theme-vrsions)
* [L’activation du pipeline front-end](#enabling-the-front-end-pipeline)

>[!TIP]
>
>Consultez la section [Parcours de création de site rapide](/help/journey-sites/quick-site/overview.md) pour vous familiariser avec l’outil de création rapide de site et le pipeline frontal afin de personnaliser facilement le thème de votre site.

## Télécharger les sources de thème {#downloading-theme-sources}

Lorsque vous créez un site dans AEM d’après un [modèle de site,](site-templates.md) vous pouvez télécharger votre [thème du site](site-themes.md) à l’aide du rail Site.

Avec le rail Site affiché dans la console Sites, sélectionnez la racine de votre site pour afficher les informations sur le thème du site.

![Téléchargement de sources de thème](/help/sites-cloud/administering/assets/download-theme-wireframe.png)

Appuyez ou cliquez sur **Télécharger des sources de thème** pour télécharger une copie locale du thème du site sous forme de fichier `.zip` à des fins de personnalisation.

## Télécharger les ressources de modèle {#downloading-template-resources}

Les [modèles de site](site-templates.md) peuvent contenir des informations en plus de la structure de contenu de votre site et du [thème du site.](site-themes.md) Les modèles de site peuvent contenir des designs de structure filaire ou d’autres fichiers liés au site, par exemple.

Si votre site est basé sur un modèle de site, avec le rail Site affiché dans la console Sites, sélectionnez la racine de votre site pour afficher les informations de thème sur le site, y compris des ressources supplémentaires.

![Téléchargement de sources de thème](/help/sites-cloud/administering/assets/download-theme-wireframe.png)

Appuyez ou cliquez sur le ou les boutons situés sous l’en-tête **Télécharger des ressources de modèle supplémentaires** pour télécharger une copie locale des fichiers disponibles.

## Affichage et modification des versions d’un thème {#them-versions}

Si votre site est basé sur un modèle de site, il est possible que son thème ait déjà été personnalisé par votre développeur front-end. À l’aide du rail Site, vous pouvez afficher la version du thème du site actuellement déployé et passer aux versions précédentes.

Avec le rail Site affiché dans la console Sites, sélectionnez la racine de votre site pour afficher les informations sur le thème du site.

![Versions du site dans le rail](/help/sites-cloud/administering/assets/theme-versions.png)

La version actuelle du thème s’affiche avec son hachage de validation et l’horodatage de sa dernière mise à jour.

Appuyez ou cliquez sur **Sélectionner la version** pour afficher les versions précédentes du thème.

![Sélection de la version du thème](/help/sites-cloud/administering/assets/select-theme-versions.png)

Appuyez ou cliquez sur la version à modifier, puis appuyez ou cliquez sur **Appliquer** pour effectuer la modification.

Si AEM détecte qu’une version plus récente du thème a été déployée via le pipeline front-end, mais n’est pas appliquée à votre site, une icône de notification s’affiche.

![Nouvelle version de l’indicateur de thème](/help/sites-cloud/administering/assets/new-theme-version.png)

Vous pouvez utiliser le bouton **Sélectionner la version** pour mettre à jour vers la nouvelle version du thème.

## Activation du pipeline front-end {#enabling-front-end-pipeline}

Si votre site n’a pas été créé à l’aide d’un modèle de site, il n’est pas possible d’utiliser le pipeline front-end pour personnaliser et déployer son thème.

Vous pouvez toutefois activer le pipeline front-end pour votre site à l’aide du rail Site.

Avec le rail Site affiché dans la console Sites, sélectionnez la racine de votre site pour afficher les informations sur le thème du site, puis appuyez ou cliquez sur **Activation du pipeline front-end**.

![Activation du pipeline front-end](/help/sites-cloud/administering/assets/enable-fep.png)

Pour plus d’informations, consultez le document [Activation du pipeline front-end.](enable-front-end-pipeline.md)
