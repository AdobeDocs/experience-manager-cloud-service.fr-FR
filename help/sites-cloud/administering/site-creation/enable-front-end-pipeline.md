---
title: Activer le pipeline front-end
description: Découvrez comment activer le pipeline front-end pour les sites de création AEM traditionnels existants avec diffusion de publication afin d’utiliser les thèmes du site pour personnaliser votre site plus rapidement.
feature: Administering
role: Admin
exl-id: 55d54d72-f87b-47c9-955f-67ec5244dd6e
solution: Experience Manager Sites
recommendations: noDisplay, noCatalog
source-git-commit: 8c4b34a77ef85869048fae254728c58cf0d99b66
workflow-type: tm+mt
source-wordcount: '930'
ht-degree: 24%

---


# Activer le pipeline front-end {#enable-front-end-pipeline}

{{traditional-aem}}

Découvrez comment activer le pipeline front-end pour les sites de création AEM traditionnels existants avec diffusion de publication afin d’utiliser les thèmes du site pour personnaliser votre site plus rapidement.

## Vue d’ensemble {#overview}

Le pipeline front-end est un mécanisme pour les projets de création AEM traditionnels avec [diffusion de publication](/help/sites-cloud/authoring/author-publish.md) qui peut rapidement déployer uniquement le code front-end de vos sites web en fonction de [thèmes du site](site-themes.md) et [modèles de site.](site-templates.md)

Ce pipeline ne gère que le code front-end, ce qui rend le processus de déploiement plus rapide que les déploiements full-stack. Il permet aux développeurs front-end de personnaliser facilement votre site sans avoir besoin de connaître AEM.

Les sites basés sur des modèles de site peuvent utiliser le pipeline front-end par défaut. Ce document décrit la façon dont vous pouvez adapter vos sites existants pour tirer parti du pipeline front-end.

>[!TIP]
>
>Si vous ne connaissez pas le pipeline front-end et que vous ne savez pas comment l’utiliser pour déployer rapidement des sites et des modèles de site, consultez [Parcours de création rapide de site](/help/journey-sites/quick-site/overview.md) en guise d’introduction.

AEM peut configurer votre site pour charger les thèmes déployés avec le pipeline front-end, même si votre site n’a pas été créé à l’aide de modèles et de thèmes de site, en les superposant à des bibliothèques clientes existantes.

## Détails techniques {#technical-details}

Lorsque vous activez le pipeline front-end d’un site, AEM apporte les modifications suivantes à la structure de votre site.

* Toutes les pages du site comprennent un fichier CSS et JS supplémentaire, qui peut être modifié en déployant des mises à jour via un pipeline front-end Cloud Manager dédié.
* Les fichiers CSS et JS ajoutés sont initialement vides. Cependant, vous pouvez télécharger un dossier « sources de thème » pour configurer la structure de dossiers nécessaire au déploiement des mises à jour de code CSS et JS via le pipeline.
* Seul un développeur peut annuler la modification, en supprimant les nœuds `SiteConfig` et `HtmlPageItemsConfig` créés sous `/conf/<site-name>/sling:configs` par cette opération.

>[!NOTE]
>
>Cette action ne convertit pas automatiquement les bibliothèques clientes existantes du site pour utiliser le pipeline front-end. Le déplacement de ces sources du dossier de bibliothèque cliente vers le dossier de pipeline front-end est une tâche qui nécessite un travail manuel par un développeur front-end.

## Conditions requises {#requirements}

AEM peut adapter automatiquement votre site existant pour utiliser le pipeline front-end. Pour pouvoir effectuer ce workflow, votre site doit utiliser [v2 ou une version ultérieure du composant Page des composants principaux](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/wcm-components/page).

## Activation du pipeline front-end {#enabling}

{{add-cm-allowlist-frontend-pipeline}}

L’activation de votre site s’effectue à partir de la console Sites à l’aide du [rail Site](site-rail.md).

1. Connectez-vous à AEM et naviguez sur votre site via **Navigation globale** > **Sites**.
1. Sélectionnez votre site dans la console. Sélectionnez la racine du site et pas les pages enfants.
1. Une fois votre site sélectionné, ouvrez le [sélecteur de rail](/help/sites-cloud/authoring/basic-handling.md#rail-selector) à gauche et choisissez **Site**.
1. Dans le rail **Site** cliquez sur le bouton **Activer le pipeline front-end**.

   ![Activation du pipeline front-end](/help/sites-cloud/administering/assets/enable-front-end-pipeline.png)

1. AEM vous invite à confirmer avec un aperçu des modifications apportées. Confirmez et votre site est adapté.

Désormais, votre site est prêt à utiliser le pipeline front-end. Pour en savoir plus sur le pipeline front-end et la gestion du thème de votre site, consultez :

* [Utilisation du rail Site pour gérer le thème de votre site](site-rail.md)
* [Parcours de création rapide de site](/help/journey-sites/quick-site/overview.md) - Ce parcours de documentation vous donne, du début à la fin, une vue d’ensemble du processus de déploiement rapide d’un site à l’aide du pipeline front-end et de l’outil de création rapide de site.
* [Pipelines CI/CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) - Ce document décrit le pipeline front-end dans le contexte des pipelines de la couche web et full-stack.

## Pipeline front-end et domaines personnalisés {#custom-domains}

Le pipeline front-end peut être utilisé avec la fonctionnalité de domaines personnalisés [Cloud Manager](/help/implementing/cloud-manager/custom-domain-names/introduction.md) mais tenez compte des exigences suivantes lorsque vous utilisez les deux fonctionnalités ensemble.

### Fichiers front-end statiques {#static-files}

Les ressources front-end statiques déployées via le pipeline front-end seront, par défaut, diffusées à partir du domaine statique prédéfini d’Adobe.

Si vous avez besoin d’un domaine personnalisé pour les ressources front-end, vous pouvez installer un domaine personnalisé au niveau de publication et configurer le Dispatcher pour acheminer des chemins spécifiques (tels que `/static/`) vers l’emplacement d’hébergement statique d’Adobe. Cette méthode nécessite la mise à jour de vos [règles Dispatcher](https://experienceleague.adobe.com/fr/docs/experience-manager-dispatcher/using/dispatcher) pour transférer et mettre en cache correctement les requêtes pour les ressources statiques.

Une fois que vous avez configuré votre domaine personnalisé et votre Dispatcher, vous pouvez configurer AEM pour diffuser vos ressources front-end à partir du domaine statique.

### Configuration {#configuration}

Comme décrit dans la section [Détails techniques](#technical-details), l’activation de la fonctionnalité de pipeline front-end pour un site crée un `SiteConfig` et des nœuds `HtmlPageItemsConfig` sous `/conf/<site-name>/sling:configs`.

Si vous souhaitez utiliser la fonctionnalité de domaines personnalisés Cloud Manager pour votre site avec le pipeline front-end pour les ressources d’état, des propriétés supplémentaires doivent être ajoutées à ces nœuds.

1. Définissez la propriété `customFrontendPrefix` dans `SiteConfig` pour le site.
   1. Accédez à `/conf/<site-name>/sling:configs/com.adobe.aem.wcm.site.manager.config.SiteConfig`.
   1. Ajoutez ou mettez à jour le `customFrontendPrefix = "https://your-custom-domain.com/static/"` de propriété.
1. Cette opération met à jour la valeur `prefixPath` du `HtmlPageItemsConfig` avec le domaine personnalisé.
   1. Accédez à `/conf/<site-name>/sling:configs/com.adobe.cq.wcm.core.components.config.HtmlPageItemsConfig`.
   1. Vérifiez que le `prefixPath` reflète votre domaine personnalisé, par exemple `prefixPath = "https://your-custom-domain.com/static/<hash>/..."`.
   * Cette valeur peut également être remplacée manuellement selon les besoins.
1. Vérifiez votre configuration.
   1. Après le déploiement, vérifiez que les pages référencent correctement les artefacts de thème du domaine personnalisé.
   1. Ouvrez les outils de développement de votre navigateur et examinez les chemins d’accès aux fichiers `theme.css` et `theme.js` pour vérifier qu’ils sont chargés à partir du domaine approprié.

Les pages du site font ensuite référence aux artefacts de thème de cette URL mise à jour. Le Dispatcher achemine ensuite les requêtes pour ces ressources vers le domaine statique.

## Bonnes pratiques pour les développeurs front-end {#best-practices}

Si vous devez développer et tester les ressources front-end localement avant de les déployer via le pipeline front-end, envisagez les approches suivantes :

* Utilisez le [mode proxy du créateur de thèmes de site](https://github.com/adobe/aem-site-theme-builder?tab=readme-ov-file#proxy) pour remplacer les artefacts de thème localement à des fins de test.
* Servez manuellement vos fichiers de thème à partir d’un serveur de développement local et mettez à jour le `prefixPath` en `HtmlPageItemsConfig` de correspondre à l’adresse du serveur local.
* Assurez-vous que la mise en cache du navigateur est désactivée pendant le test pour afficher les mises à jour en direct.

Pour plus d’informations sur le développement front-end local, consultez la documentation du [&#x200B; Créateur de thèmes de site &#x200B;](https://github.com/adobe/aem-site-theme-builder).
