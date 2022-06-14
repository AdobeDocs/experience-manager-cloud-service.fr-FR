---
title: Activation du pipeline front-end
description: Découvrez comment activer le pipeline front-end pour les sites existants afin d’utiliser les thèmes du site pour personnaliser plus rapidement votre site.
feature: Administering
role: Admin
exl-id: 55d54d72-f87b-47c9-955f-67ec5244dd6e
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 100%

---

# Activation du pipeline front-end {#enable-front-end-pipeline}

Découvrez comment activer le pipeline front-end pour les sites existants afin d’utiliser les thèmes du site pour personnaliser plus rapidement votre site.

## Présentation {#overview}

Le pipeline front-end est un mécanisme qui peut rapidement déployer uniquement le code front-end de vos sites web en fonction des [thèmes du site](site-themes.md) et des [modèles de site.](site-templates.md)

Au lieu d’un déploiement full stack, seul le code front-end est géré par ce pipeline, ce qui accélère le processus et permet également aux développeurs front-end de personnaliser facilement et rapidement votre site sans connaissances d’AEM.

Les sites basés sur des modèles de site peuvent utiliser le pipeline front-end par défaut. Ce document décrit la façon dont vous pouvez adapter vos sites existants pour tirer parti du pipeline front-end.

>[!TIP]
>
>Si vous ne connaissez pas le pipeline front-end et que vous ne savez pas comment l’utiliser pour déployer rapidement des sites et des modèles de site, consultez la section [Parcours de création rapide de site](/help/journey-sites/quick-site/overview.md) en guise d’introduction.

Si vous n’avez pas créé votre site existant en fonction de modèles et de thèmes, AEM peut configurer votre site pour charger les thèmes déployés avec le pipeline front-end sur les bibliothèques clientes existantes.

## Détails techniques {#technical-details}

Lorsque vous activez le pipeline front-end d’un site, AEM apporte les modifications suivantes à la structure de votre site.

* Toutes les pages du site comprennent un fichier CSS et JS supplémentaire, qui peut être modifié en déployant des mises à jour via un pipeline front-end Cloud Manager dédié.
* Les fichiers CSS et JS ajoutés seront initialement vides, mais un dossier « sources de thème » peut être téléchargé pour amorcer la structure du dossier qui permet de déployer les mises à jour de code CSS et JS via ce pipeline.
* Cette modification ne peut être annulée que par un développeur, en supprimant les nœuds `SiteConfig` et `HtmlPageItemsConfig` créés sous cette opération `/conf/<site-name>/sling:configs`.

>[!NOTE]
>
>Cette action ne convertit pas automatiquement les bibliothèques clientes existantes du site pour utiliser le pipeline front-end. Le déplacement de ces sources du dossier de bibliothèque cliente vers le dossier de pipeline front-end est une tâche qui nécessite un travail manuel par un développeur front-end.

## Conditions requises {#requirements}

AEM peut adapter automatiquement votre site existant pour utiliser le pipeline front-end. Pour ce faire, votre site doit utiliser [v2 ou une version ultérieure du composant Page des composants principaux.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/page.html?lang=fr)

## Activation du pipeline front-end {#enabling}

L’activation de votre site s’effectue à partir de la console Sites à l’aide de la fonction [rail Site.](site-rail.md)

1. Connectez-vous à AEM et naviguez sur votre site via **Navigation globale** > **Sites**.
1. Sélectionnez votre site dans la console. Vous devez sélectionner la racine du site et pas les pages enfants.
1. Une fois votre site sélectionné, ouvrez le [sélecteur de rail](/help/sites-cloud/authoring/getting-started/basic-handling.md#rail-selector) à gauche et choisissez **Site**.
1. Dans le rail **Site** cliquez sur le bouton **Activer le pipeline front-end**.

   ![Activation du pipeline front-end](/help/sites-cloud/administering/assets/enable-front-end-pipeline.png)

1. AEM vous invite à confirmer avec un aperçu les modifications qui seront apportées. Confirmez et votre site est adapté.

Votre site est maintenant prêt à utiliser le pipeline front-end. Pour en savoir plus sur le pipeline front-end et la gestion du thème de votre site, consultez :

* [Utilisation du rail Site pour gérer le thème de votre site](site-rail.md)
* [Parcours de création rapide de site](/help/journey-sites/quick-site/overview.md) - Ce parcours de documentation vous donne, du début à la fin, une vue d’ensemble du processus de déploiement rapide d’un site à l’aide du pipeline front-end et de l’outil de création rapide de site.
* [Pipelines CI/CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) - Ce document décrit le pipeline front-end dans le contexte des pipelines de la couche web et full-stack.
