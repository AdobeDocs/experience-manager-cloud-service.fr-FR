---
title: Extensibilité de l’interface utilisateur de la vue AEM Assets
description: Découvrez la fonctionnalité d’extensibilité de l’interface utilisateur de la vue AEM Assets. L’interface utilisateur de la vue AEM Assets permet d’ajouter des composants d’interface utilisateur personnalisés pour répondre à des besoins spécifiques.
feature: App Builder
role: User, Developer
exl-id: a11f7043-17cf-4331-b76c-d3db099c2411
source-git-commit: af7e6ab40212dfa3d91cda80a76b1b6b01dd65a3
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 3%

---

# Extensibilité de l’interface utilisateur de la vue AEM Assets{#AEM-Assets-View-UI-Extensibility}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [Bonnes pratiques relatives aux métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Fonctionnalités Dynamic Media avec OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation de développement pour AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

La vue AEM Assets dispose d’une fonctionnalité d’extensibilité de l’interface utilisateur. Cette fonctionnalité permet aux utilisateurs d’ajouter des composants d’interface utilisateur personnalisés à l’interface utilisateur d’Assets View afin de répondre aux besoins spécifiques que les fonctionnalités prêtes à l’emploi d’AEM Assets View ne répondent pas. Cette fonctionnalité d’extensibilité optimise la flexibilité de la vue AEM Assets qui permet aux entreprises d’adapter l’interface aux workflows et aux exigences spécifiques.
Vous pouvez ajouter vos extensions aux niveaux Ressource, Dossier et Collection. L’extension ajoutée s’affiche dans un panneau dédié sur la page Détails de la ressource, de la collection ou du dossier.

>[!IMPORTANT]
>
> * L’extensibilité de l’interface utilisateur de la vue AEM Assets est disponible avec [Assets Ultimate](/help/assets/assets-ultimate-overview.md).
> * L’extensibilité de l’interface utilisateur d’Assets View est disponible dans une version de Beta. Pour obtenir un accès anticipé à l’extensibilité de l’interface utilisateur de la vue Assets, [créez et envoyez un cas de service clientèle Adobe](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html).
> * Vous pouvez fournir des commentaires sur la documentation en développant les options de commentaires détaillés et en cliquant sur Signaler un problème.

## <a id="1"></a> Accès à la vue Assets

Accédez à la vue Assets comme suit :
![access-assets-view-ui](/help/assets/assets/access-assets-view.jpg)

## Où les extensions de l’interface utilisateur s’affichent-elles dans l’interface utilisateur de la vue Assets ? {#ui-extensibility-panel-assets-view}

Dans la vue Assets, accédez à la page Détails d’une ressource, d’un dossier ou d’une collection. Cette page Détails comporte un panneau dédié qui affiche l’extension d’IU ajoutée.
![mon espace de travail](/help/assets/assets/my-workspace-assets-view3.png)


## Conditions préalables pour l’ajout du composant Extensibilité

* [Accès à la vue Assets](#1).
* Accès au [créateur d’applications Adobe](https://developer.adobe.com/app-builder/docs/overview/), qui est inclus par défaut dans l’ [Assets Ultimate](/help/assets/assets-ultimate-overview.md).
* Autorisé à être développeur du rôle Administrateur système au sein de l’organisation. Voir [this](https://developer.adobe.com/uix/docs/guides/get-access/) pour plus d’informations.
* L’outil de ligne de commande Adobe IO (AIO CLI) doit être installé sur vos ordinateurs locaux. Cet outil est essentiel pour la création et le déploiement de projets d’extension. Voir [this](https://developer.adobe.com/app-builder/docs/getting_started/#local-environment-set-up) pour plus d’informations.
* Bonne compréhension des technologies JavaScript, Node.js et React.

## Ajout du composant d’extensibilité de l’interface utilisateur sur l’interface utilisateur de la vue Assets{#Adding-UI-Extensibility-Component-on-Assets-View}

1. Voir [Prise en main](https://developer.adobe.com/uix/docs/getting-started/) pour obtenir des informations essentielles sur les extensions de l’interface utilisateur et la structure Adobe App Builder. Découvrez comment l’extensibilité de l’interface utilisateur permet l’intégration d’une logique et d’une interface utilisateur personnalisées dans les services Adobe Experience Cloud et comprenez l’architecture et le processus d’implémentation des extensions de l’interface utilisateur.
1. Voir [Guides](https://developer.adobe.com/uix/docs/guides/) pour obtenir des informations générales sur l’extensibilité de l’interface utilisateur, notamment la configuration de l’environnement local, l’aperçu local, la publication et la gestion.
1. Reportez-vous à la section [Concepts communs de la création d’extensions](https://developer.adobe.com/uix/docs/services/aem-assets-view/api/commons/) pour comprendre les principes de base nécessaires au développement d’une extension d’interface utilisateur pour la vue AEM Assets.
1. Ajoutez des panneaux latéraux personnalisés à l’interface de la vue Assets. L’application hôte (vue Assets) gère ces panneaux pour gérer les interactions de l’interface utilisateur, telles que le basculement et la création de liens profonds. Les extensions utilisent le point d’extension `aem/assets/details/1` pour intégrer des panneaux personnalisés qui spécifient des propriétés, telles que l’identifiant du panneau, le titre et l’URL du contenu. Les développeurs enregistrent des panneaux personnalisés avec la méthode `getPanels()` et créent des itinéraires pour afficher du contenu personnalisé. Pour une mise en oeuvre détaillée, y compris des références d’API et des exemples de code, voir [Affichage des détails](https://developer.adobe.com/uix/docs/services/aem-assets-view/api/details-view/).
1. Configurez directement votre environnement local et Experience le processus de développement d’extensions d’interface utilisateur dans la vue Assets en créant votre première extension d’interface utilisateur. Pour plus d’informations, voir [Développement de l’extension de la vue AEM Assets étape par étape](https://developer.adobe.com/uix/docs/services/aem-assets-view/extension-development/) .
1. Configurez votre application à l’aide de l’interface de ligne de commande AIO pour générer la structure d’extension de base et le code requis. Pour plus d’informations, voir [Génération de code pour la vue AEM Assets](https://developer.adobe.com/uix/docs/services/aem-assets-view/code-generation/) .
1. Testez vos extensions localement pour vous assurer qu’elles fonctionnent comme prévu avant le déploiement. Exécutez votre extension dans un environnement complètement isolé ou avec une isolation partielle et connectez votre extension à la vue AEM Assets de production pour le test. Pour plus d’informations, voir [Dépannage - Extensibilité de la vue AEM Assets](https://developer.adobe.com/uix/docs/services/aem-assets-view/debug/) .
