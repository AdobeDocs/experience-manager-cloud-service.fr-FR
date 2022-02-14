---
title: Activation du pipeline front-end
description: Découvrez comment activer le pipeline frontal pour les sites existants afin d’exploiter les thèmes du site pour personnaliser plus rapidement votre site.
feature: Administering
role: Admin
source-git-commit: dc7e89c601bb02c78f65ca58eff34c15092b5561
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---


# Activation du pipeline front-end {#enable-front-end-pipeline}

Découvrez comment activer le pipeline frontal pour les sites existants afin d’exploiter les thèmes du site pour personnaliser plus rapidement votre site.

## Présentation {#overview}

Le pipeline frontal est un mécanisme qui peut rapidement déployer uniquement le code frontal de vos sites web en fonction des [thèmes du site](site-themes.md) et [modèles de site.](site-templates.md)

Au lieu de déployer la pile complète, seul le code frontal est géré par ce pipeline, ce qui accélère le processus et permet également aux développeurs front-end de personnaliser facilement et rapidement votre site sans en avoir connaissance AEM.

Les sites basés sur des modèles de site peuvent utiliser le pipeline frontal par défaut. Ce document décrit comment adapter vos sites existants pour tirer parti du pipeline frontal.

>[!TIP]
>
>Si vous ne connaissez pas le pipeline frontal et que vous ne savez pas comment déployer rapidement des sites à l’aide de celui-ci et des modèles de site, consultez la section [Parcours de création de site rapide](/help/journey-sites/quick-site/overview.md) pour une introduction.

Si vous n’avez pas créé votre site existant en fonction de modèles et de thèmes, AEM peut configurer votre site pour charger les thèmes déployés avec le pipeline front-end au-dessus des bibliothèques clientes existantes.

## Conditions requises {#requirements}

AEM peut adapter automatiquement votre site existant pour utiliser le pipeline frontal. Pour ce faire, votre site doit utiliser [v2 ou version ultérieure du composant Page des composants principaux.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/page.html)

## Activation du pipeline front-end {#enabling}

L’activation de votre site est effectuée à partir de la console Sites.

1. Connectez-vous à AEM et accédez à votre site via **Navigation globale** > **Sites**.
1. Sélectionnez votre site dans la console. Vous devez sélectionner la racine du site et non les pages enfants.
1. Une fois votre site sélectionné, ouvrez la [sélecteur de rail](/help/sites-cloud/authoring/getting-started/basic-handling.md#rail-selector) à gauche et choisissez **Site**.
1. Dans le **Site** rail, cliquez sur le bouton **Activation du pipeline front-end**.

   ![Activation du pipeline front-end](/help/sites-cloud/administering/assets/enable-front-end-pipeline.png)

1. AEM vous invite à confirmer avec un aperçu les modifications qui seront apportées. Confirmez et votre site est adapté.

Votre site est maintenant prêt à utiliser le pipeline frontal. Pour en savoir plus sur le pipeline front-end, voir :

* [Parcours de création de site rapide](/help/journey-sites/quick-site/overview.md) - Ce parcours de documentation vous donne, de début à fin, une vue d’ensemble du processus de déploiement rapide d’un site à l’aide du pipeline frontal et de l’outil de création rapide de site.
* [Pipelines CI/CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) - Ce document décrit le pipeline front-end dans le contexte des pipelines de niveau web et de pile complète.
