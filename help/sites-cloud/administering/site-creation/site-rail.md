---
title: Utilisation du rail de site pour gérer le thème de votre site
description: Découvrez les puissantes fonctionnalités du rail du site pour vous aider à personnaliser et gérer facilement le thème de votre site.
feature: Administering
role: Admin
source-git-commit: 002b95212d682c41a601a483df9b4365a553b669
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---


# Utilisation du rail de site pour gérer le thème de votre site {#site-rail}

Découvrez les puissantes fonctionnalités du rail du site pour vous aider à personnaliser et gérer facilement le thème de votre site.

## Présentation {#overview}

Le rail Site vous permet de gérer le thème et les ressources de modèle de votre site. [Comme les autres rails](/help/sites-cloud/authoring/getting-started/basic-handling.md#rail-selector) comme les rails Arborescence de contenu, Références ou Chronologie, le rail Site s’affiche en tant que panneau le plus à gauche de la console Sites, affichant des informations sur l’élément sélectionné. Contrairement aux autres rails, le rail Site s’applique uniquement aux racines du site.

Le rail Site permet de gérer les informations relatives aux thèmes et aux modèles pour votre site, notamment :

* [Téléchargement des sources de thème](#downloading-theme-sources)
* [Téléchargement de ressources de modèle telles que des maquettes](#downloading-template-resources)
* [Affichage et modification des versions de thème](#theme-vrsions)
* [Activation du pipeline front-end](#enabling-the-front-end-pipeline)

>[!TIP]
>
>Consultez la section [Parcours de création de site rapide](/help/journey-sites/quick-site/overview.md) pour vous familiariser avec l’outil de création rapide de site et le pipeline frontal afin de personnaliser facilement le thème de votre site.

##  Téléchargement des sources de thème {#downloading-theme-sources}

Lorsque vous créez un site dans AEM en fonction d’une [modèle de site,](site-templates.md) vous pouvez télécharger votre [thème du site](site-themes.md) à l’aide du rail Site.

Le rail Site s’affichant dans la console Sites, sélectionnez la racine de votre site pour afficher les informations sur le thème du site.

![Téléchargement de sources de thème](/help/sites-cloud/administering/assets/download-theme-wireframe.png)

Appuyez ou cliquez sur **Télécharger des sources de thème** pour télécharger une copie locale du thème du site en tant que `.zip` à des fins de personnalisation.

##  Téléchargement des ressources de modèle {#downloading-template-resources}

[Modèles de site](site-templates.md) peut contenir des informations en plus de la structure de contenu de votre site et [thème du site.](site-themes.md) Les modèles de site peuvent contenir des conceptions de cadre filaire ou d’autres fichiers liés au site, par exemple.

Si votre site est basé sur un modèle de site, avec le rail Site affiché dans la console Sites, sélectionnez la racine de votre site pour afficher les informations de thème sur le site, y compris des ressources supplémentaires.

![Téléchargement de sources de thème](/help/sites-cloud/administering/assets/download-theme-wireframe.png)

Appuyez ou cliquez sur le ou les boutons situés sous l’en-tête **Télécharger des ressources de modèle supplémentaires** pour télécharger une copie locale des fichiers disponibles.

## Affichage et modification des versions d’un thème {#them-versions}

Si votre site est basé sur un modèle de site, il est possible que son thème ait déjà été personnalisé par votre développeur front-end. À l’aide du rail Site, vous pouvez afficher la version du thème du site actuellement déployé et passer aux versions précédentes.

Le rail Site s’affichant dans la console Sites, sélectionnez la racine de votre site pour afficher les informations sur le thème du site.

![Versions du site dans le rail](/help/sites-cloud/administering/assets/theme-versions.png)

La version actuelle du thème s’affiche avec son hachage de validation et l’horodatage de sa dernière mise à jour.

Appuyez ou cliquez sur **Sélectionner la version** pour afficher les versions précédentes du thème.

![Sélectionner la version du thème](/help/sites-cloud/administering/assets/select-theme-versions.png)

Appuyez ou cliquez sur la version à modifier, puis appuyez ou cliquez sur **Appliquer** pour effectuer la modification.

Si AEM détecte qu’une version plus récente du thème a été déployée via le pipeline frontal, mais n’est pas appliquée à votre site, une icône de notification s’affiche.

![Nouvelle version de l’indicateur de thème](/help/sites-cloud/administering/assets/new-theme-version.png)

Vous pouvez utiliser la variable **Sélectionner la version** pour mettre à jour vers la nouvelle version du thème.

## Activation du pipeline front-end {#enabling-front-end-pipeline}

Si votre site n’a pas été créé à l’aide d’un modèle de site, il n’est pas possible d’utiliser le pipeline frontal pour personnaliser et déployer son thème.

Vous pouvez toutefois activer le pipeline frontal pour votre site à l’aide du rail Site.

Le rail de site s’affichant dans la console Sites, sélectionnez la racine de votre site pour afficher les informations sur le thème du site, puis appuyez ou cliquez dessus. **Activation du pipeline front-end**.

![Activation du pipeline front-end](/help/sites-cloud/administering/assets/enable-fep.png)

Pour plus d’informations, voir le document [Activation du pipeline front-end.](enable-front-end-pipeline.md)