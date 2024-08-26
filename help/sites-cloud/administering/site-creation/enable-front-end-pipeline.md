---
title: Activer le pipeline front-end
description: Découvrez comment vous pouvez activer le pipeline frontal pour que les sites existants utilisent des thèmes de site pour personnaliser plus rapidement votre site.
feature: Administering
role: Admin
exl-id: 55d54d72-f87b-47c9-955f-67ec5244dd6e
solution: Experience Manager Sites
source-git-commit: 1415d07235641262814e81362c806572bcf582ba
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 47%

---

# Activer le pipeline front-end {#enable-front-end-pipeline}

Découvrez comment vous pouvez activer le pipeline frontal pour que les sites existants utilisent des thèmes de site pour personnaliser plus rapidement votre site.

## Vue d’ensemble {#overview}

Le pipeline front-end est un mécanisme qui peut rapidement déployer uniquement le code front-end de vos sites web en fonction des [thèmes du site](site-themes.md) et des [modèles de site.](site-templates.md)

Ce pipeline gère uniquement le code frontal, ce qui rend le processus de déploiement plus rapide que les déploiements en pile complète. Il permet aux développeurs front-end de personnaliser facilement votre site sans avoir besoin de connaissances en AEM.

Les sites basés sur des modèles de site peuvent utiliser le pipeline front-end par défaut. Ce document décrit la façon dont vous pouvez adapter vos sites existants pour tirer parti du pipeline front-end.

>[!TIP]
>
>Si vous ne connaissez pas le pipeline frontal et si vous ne savez pas comment déployer rapidement des sites à l’aide de celui-ci et des modèles de site, reportez-vous à la section [Parcours de création rapide de site](/help/journey-sites/quick-site/overview.md) pour une introduction.

AEM peut configurer votre site pour charger des thèmes déployés avec le pipeline front-end, même si votre site n’a pas été créé à l’aide de modèles et de thèmes de site, en les superposant aux bibliothèques clientes existantes.

## Détails techniques {#technical-details}

Lorsque vous activez le pipeline front-end d’un site, AEM apporte les modifications suivantes à la structure de votre site.

* Toutes les pages du site incluent un fichier CSS et JS supplémentaire, qui peut être modifié en déployant des mises à jour via un pipeline frontal Cloud Manager dédié.
* Les fichiers CSS et JS ajoutés sont initialement vides. Vous pouvez toutefois télécharger un dossier &quot;sources de thème&quot; pour configurer la structure de dossiers nécessaire au déploiement des mises à jour de code CSS et JS via le pipeline.
* Seul un développeur peut annuler la modification, en supprimant les noeuds `SiteConfig` et `HtmlPageItemsConfig` que cette opération crée sous `/conf/<site-name>/sling:configs`.

>[!NOTE]
>
>Cette action ne convertit pas automatiquement les bibliothèques clientes existantes du site pour utiliser le pipeline de polices-end. Le déplacement de ces sources du dossier de bibliothèque cliente vers le dossier de pipeline front-end est une tâche qui nécessite un travail manuel par un développeur front-end.

## Conditions requises {#requirements}

AEM peut adapter automatiquement votre site existant pour utiliser le pipeline front-end. Pour pouvoir exécuter ce processus, votre site doit utiliser la version [v2 ou ultérieure du composant Page des composants principaux.](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/wcm-components/page)

## Activation du pipeline front-end {#enabling}

{{add-cm-allowlist-frontend-pipeline}}

L’activation de votre site s’effectue à partir de la console Sites à l’aide de la fonction [rail Site.](site-rail.md)

1. Connectez-vous à AEM et naviguez sur votre site via **Navigation globale** > **Sites**.
1. Sélectionnez votre site dans la console. Sélectionnez la racine du site et non les pages enfants.
1. Une fois votre site sélectionné, ouvrez le [sélecteur de rail](/help/sites-cloud/authoring/basic-handling.md#rail-selector) à gauche et choisissez **Site**.
1. Dans le rail **Site** cliquez sur le bouton **Activer le pipeline front-end**.

   ![Activation du pipeline front-end](/help/sites-cloud/administering/assets/enable-front-end-pipeline.png)

1. AEM vous invite à confirmer avec un aperçu les modifications apportées. Confirmez et votre site est adapté.

Votre site est maintenant prêt à utiliser le pipeline frontal. Pour en savoir plus sur le pipeline front-end et la gestion du thème de votre site, consultez :

* [Utilisation du rail Site pour gérer le thème de votre site](site-rail.md)
* [Parcours de création rapide de site](/help/journey-sites/quick-site/overview.md) - Ce parcours de documentation vous donne, du début à la fin, une vue d’ensemble du processus de déploiement rapide d’un site à l’aide du pipeline front-end et de l’outil de création rapide de site.
* [Pipelines CI/CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) - Ce document décrit le pipeline front-end dans le contexte des pipelines de la couche web et full-stack.
