---
title: Activez l’extensibilité de l’interface utilisateur dans  [!DNL AEM Assets View]
description: Découvrez la fonctionnalité d’extensibilité de l’interface utilisateur d [!DNL AEM Assets View]. [!DNL AEM Assets View] UI qui permet d’ajouter des composants d’interface utilisateur personnalisés pour répondre à des besoins professionnels spécifiques.
feature: App Builder
role: User, Developer
exl-id: a11f7043-17cf-4331-b76c-d3db099c2411
source-git-commit: 9c1104f449dc2ec625926925ef8c95976f1faf3d
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 0%

---

# Activer l’extensibilité de l’interface utilisateur dans [!DNL AEM Assets View] {#AEM-Assets-View-UI-Extensibility}

[!DNL AEM Assets View] prend en charge l’extensibilité de l’interface utilisateur, ce qui vous permet d’ajouter des composants d’interface utilisateur personnalisés à votre interface utilisateur [!DNL Assets View] pour des workflows spécifiques et des besoins de l’entreprise qui ne sont pas satisfaits par les fonctionnalités prêtes à l’emploi de [!DNL AEM Assets View]. Cette fonctionnalité d’extensibilité de l’interface utilisateur d’[!DNL AEM Assets View] améliore sa flexibilité, permettant aux entreprises d’adapter l’interface à des workflows et des exigences spécifiques.\
Vous pouvez ajouter vos extensions au niveau **Ressource**, **Dossier** et **Collection**. L’extension ajoutée s’affiche dans un panneau dédié sur la page **Ressource**, **Collection** ou **Dossier** **[!UICONTROL Détails]**.

>[!IMPORTANT]
>
> * L’extensibilité de l’interface utilisateur de [!DNL AEM Assets View] est disponible avec [[!DNL Assets Ultimate]](/help/assets/assets-ultimate-overview.md).
> * Pour accéder à l’extensibilité de [!DNL Assets view]’interface utilisateur, [créez et envoyez un dossier  [!DNL Adobe]  service clientèle](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html).
> * Vous pouvez fournir des commentaires sur la documentation en développant **[!UICONTROL Options de commentaires détaillés]** et en cliquant sur **[!UICONTROL Signaler un problème]**.

## <a id="1"></a> accéder à la vue Assets{#add-UI-Extensibility-in-AEM-Assets-View}

Suivez les étapes mentionnées dans l’image ci-dessous pour accéder au [!DNL Assets View] :
![access-assets-view-ui](/help/assets/assets/access-assets-view.jpg)

## Affichage des extensions d’interface utilisateur dans [!DNL Assets View] {#ui-extensibility-panel-assets-view}

Dans [!DNL Assets View], accédez à la page **[!UICONTROL Détails]** d’une ressource, d’un dossier ou d’une collection. La page **[!UICONTROL Détails]** affiche l’extension d’interface utilisateur ajoutée dans un panneau dédié.
![mon espace de travail](/help/assets/assets/my-workspace-assets-view3.png)

## Conditions préalables à l’ajout du composant d’extensibilité{#assets-view-ui-extensibility}

Remplissez les conditions requises suivantes pour commencer à ajouter le composant d’extensibilité à votre [!DNL Assets View UI] :

* [&#x200B; Accès à  [!DNL Assets View]](#1).
* Accès à la [[!DNL Adobe app builder]](https://developer.adobe.com/app-builder/docs/overview/).
* Autorisation de développer le rôle d’administrateur système au sein de l’organisation. Voir [cette documentation](https://developer.adobe.com/uix/docs/guides/get-access/) pour plus d’informations.
* [!DNL Adobe IO command line tool (AIO CLI)] est installé sur vos ordinateurs locaux. Cet outil est essentiel pour la création et le déploiement de projets d’extension. Voir [Création de votre première application App Builder](https://developer.adobe.com/app-builder/docs/get_started/app_builder_get_started/first-app#local-environment-set-up) (nécessite une authentification pour l’accès) pour plus d’informations.
* Bonne compréhension des technologies [!DNL JavaScript], [!DNL Node.js] et [!DNL React].

## Ajouter le composant d’extensibilité de l’interface utilisateur à [!DNL Assets View] {#ui-extensibility-in-assets-view}

1. Consultez [Prise en main](https://developer.adobe.com/uix/docs/getting-started/) pour obtenir des informations essentielles sur les extensions d’interface utilisateur et le framework de [!DNL Adobe App Builder]. Découvrez comment l’extensibilité de l’interface utilisateur permet l’intégration d’une logique et d’une interface utilisateur personnalisées dans [!DNL Adobe Experience Cloud services] et comprenez l’architecture et le workflow de mise en œuvre des extensions d’interface utilisateur.
1. Consultez [Guides](https://developer.adobe.com/uix/docs/guides/) pour obtenir des informations générales sur l’extensibilité de l’interface utilisateur, notamment la configuration de l’environnement local, la prévisualisation locale, la publication et la gestion.
1. Voir [Concepts courants de la création d’extensions](https://developer.adobe.com/uix/docs/services/aem-assets-view/api/commons/) pour comprendre les principes de base requis pour développer une extension d’interface utilisateur pour le [!DNL AEM Assets View].
1. Ajoutez des panneaux latéraux personnalisés à l’interface [!DNL Assets View]. L’application hôte ([!DNL Assets View]) gère ces panneaux pour gérer les interactions de l’interface utilisateur, telles que le basculement et la liaison profonde. Les extensions utilisent le point d’extension `aem/assets/details/1` pour intégrer des panneaux personnalisés qui spécifient des propriétés, telles que l’ID du panneau, le titre et l’URL du contenu. Les développeurs enregistrent des panneaux personnalisés avec la méthode `getPanels()` et créent des itinéraires pour afficher du contenu personnalisé. Pour une implémentation détaillée, y compris les références d’API et des exemples de code, voir [Vue des détails](https://developer.adobe.com/uix/docs/services/aem-assets-view/api/details-view/).
1. Configurez votre environnement local et créez votre première extension d’interface utilisateur pour découvrir de première main le processus de développement des extensions d’interface utilisateur dans [!DNL Assets View]. Voir [Développement pas à pas de l’extension AEM Assets View](https://developer.adobe.com/uix/docs/services/aem-assets-view/extension-development/) pour plus d’informations.
1. Configurez votre application à l’aide de l’interface de ligne de commande AIO pour générer la structure d’extension de base et le code requis. Pour plus d’informations, voir [génération du code pour [!DNL AEM Assets View]](https://developer.adobe.com/uix/docs/services/aem-assets-view/code-generation/).
1. Testez vos extensions localement pour vous assurer qu’elles fonctionnent comme prévu avant le déploiement. Exécutez votre extension dans un environnement entièrement isolé ou partiellement isolé et connectez-la au [!DNL AEM Assets View] de production à des fins de test. Voir [Dépannage - [!DNL AEM Assets View] extensibilité](https://developer.adobe.com/uix/docs/services/aem-assets-view/debug/) pour plus d’informations.

## Personnalisation des actions rapides et de la barre d’actions dans la vue Assets {#customize-quick-actions-and-actions-bar}

Vous pouvez personnaliser les actions qui s’affichent lorsque vous sélectionnez une ou plusieurs ressources (barre d’actions) dans la vue Assets. La vue Assets vous permet également de personnaliser les actions qui s’affichent lorsque vous cliquez sur Plus d’options (...) dans la carte de la ressource. Pour plus d’informations, voir [Vue Parcourir](https://developer.adobe.com/uix/docs/services/aem-assets-view/api/browse-view/).

## Ouvrir les boîtes de dialogue personnalisées dans la vue Assets {#open-custom-dialogs-assets-view}

La vue Assets permet également d’ouvrir des boîtes de dialogue personnalisées avec le texte de votre choix. Vous pouvez également ajouter des liens au texte. Pour plus d’informations, voir [API modale](https://developer.adobe.com/uix/docs/services/aem-assets-view/api/commons/#modal-api).
