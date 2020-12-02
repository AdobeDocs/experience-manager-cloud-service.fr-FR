---
title: Aperçu des composants
description: Les composants sont des unités modulaires qui exécutent des fonctionnalités spécifiques pour présenter du contenu sur votre site web.
translation-type: tm+mt
source-git-commit: 83c27daae4e8ae2ae6a8f115c9da9527971c6ecb
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 49%

---


# Aperçu des composants {#components-overview}

Cette page donne un aperçu des composants AEM (Adobe Experience Manager), tels que ceux [utilisés pour la création de pages](/help/sites-cloud/authoring/fundamentals/components.md).

## Que sont les composants ? {#what-are-components}

Les composants de AEM sont les suivants :

* Unités modulaires qui réalisent des fonctionnalités spécifiques pour présenter votre contenu sur votre site Web.
* Réutilisable.
* Développé en tant qu&#39;unités autonomes dans un dossier du référentiel.
* Ils ne comportent aucun fichier de configuration masqué.
* Ils peuvent contenir d’autres composants.
* Peut s’exécuter n’importe où dans n’importe quel système AEM et peut également être limité à s’exécuter sous des composants spécifiques.
* Ils possèdent une interface utilisateur standardisée.
* Comportement de modification pouvant être configuré.
* Utilisez les boîtes de dialogue créées à l’aide de sous-éléments basés sur les composants de l’interface utilisateur Granite.
* Sont développés à l&#39;aide de [HTL](https://docs.adobe.com/content/help/en/experience-manager-htl/using/overview.html).
* Ils peuvent être développés pour créer des composants personnalisés qui étendent les fonctionnalités par défaut.

Compte tenu de la nature modulaire des composants, vous pouvez effectuer les opérations suivantes :

* Développer un nouveau composant sur votre instance locale.
* Déployez-le sur votre environnement de test.
* Déployer le composant sur votre environnement de création actif et permettre ainsi aux auteurs et/ou développeurs d’ajouter et de configurer du contenu.
* Déployez-le sur vos environnements de publication en direct, où il est utilisé pour générer du contenu pour des visiteurs sur votre site Web.

Chaque composant AEM :

* Est un type de ressource.
* Collection de scripts qui réalisent complètement une fonction spécifique.
* Peut fonctionner isolément, c&#39;est-à-dire dans AEM ou sur un portail.

## AEM Core Components {#aem-core-components}

[Les ](https://docs.adobe.com/content/help/fr-FR/experience-manager-core-components/using/introduction.html) composants de base AEM sont un ensemble de composants de Gestion de contenu Web normalisés (WCM) pour AEM accélérer le temps de développement et réduire les coûts de maintenance de vos sites Web.

Les composants principaux sont fournis avec AEM en tant que Cloud Service et le [tutoriel WKND](/help/implementing/developing/introduction/develop-wknd-tutorial.md) illustre comment implémenter et utiliser les composants. Les composants sont fournis avec l’intégralité du code source et peuvent être utilisés tels quels ou comme points de départ pour des composants modifiés ou étendus.

### Affichage des composants disponibles {#viewing-available-components}

Pour avoir un aperçu de tous les composants disponibles dans votre instance AEM, utilisez la [console Composants](/help/sites-cloud/authoring/features/components-console.md).

Une autre méthode consiste à utiliser CRXDE Lite pour obtenir la liste de tous les composants disponibles dans le référentiel.

1. Dans **[!UICONTROL CRXDE Lite]**, sélectionnez **[!UICONTROL Outils]** dans la barre d&#39;outils, puis **[!UICONTROL Requête]**, qui ouvre l&#39;onglet **[!UICONTROL Requête]**.

1. Dans l’onglet **[!UICONTROL Requête]**, sélectionnez `XPath` comme **[!UICONTROL Type]**.

1. Dans la zone de saisie **[!UICONTROL Requête]**, entrez la chaîne suivante :

   `//element(*, cq:Component)`

1. Cliquez sur **[!UICONTROL Exécuter]** et les composants sont répertoriés.

