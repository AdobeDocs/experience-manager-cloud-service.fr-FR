---
title: Aperçu des composants
description: Les composants sont des unités modulaires qui exécutent des fonctionnalités spécifiques pour présenter du contenu sur votre site web.
exl-id: 0fdc99e7-2103-448d-8217-d5d52c94acea
source-git-commit: 856266faf4cb99056b1763383d611e9b2c3c13ea
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 87%

---

# Aperçu des composants {#components-overview}

Cette page donne un aperçu des composants AEM (Adobe Experience Manager), tels que ceux [utilisés pour la création de pages](/help/sites-cloud/authoring/fundamentals/components.md).

## Que sont les composants ?  {#what-are-components}

Les composants dans AEM :

* sont des unités modulaires qui exécutent des fonctionnalités spécifiques pour présenter du contenu sur votre site web ;
* peuvent être réutilisés ;
* sont développés comme des unités autonomes dans un seul dossier du référentiel ;
* ne comportent aucun fichier de configuration masqué ;
* peuvent contenir d’autres composants ;
* peuvent s’exécuter n’importe où dans n’importe quel système AEM et peuvent également être limités à s’exécuter sur des composants spécifiques ;
* possèdent une interface utilisateur standardisée ;
* sont associés à un comportement de modification qui peut être configuré ;
* utilisent des boîtes de dialogue créées à l’aide de sous-éléments basés sur les composants de l’interface utilisateur Granite ;
* sont développés à l’aide de [HTL](https://experienceleague.adobe.com/docs/experience-manager-htl/using/overview.html?lang=fr) ;
* peuvent être développés pour créer des composants personnalisés qui étendent les fonctionnalités par défaut.

Les composants étant modulaires, vous pouvez :

* Développez un nouveau composant sur votre instance locale.
* Déployer ce composant sur votre environnement de test.
* Déployer le composant sur votre environnement de création actif et permettre ainsi aux auteurs et/ou développeurs d’ajouter et de configurer du contenu.
* Déployer le composant sur votre (vos) environnement(s) de publication actif(s), où il est utilisé pour effectuer le rendu du contenu à l’intention des visiteurs de votre site Web.

Chaque composant AEM :

* est un type de ressource ;
* est un ensemble de scripts qui exécutent complètement une fonction spécifique ;
* peut fonctionner de manière isolée, c’est-à-dire soit dans AEM, soit dans un portail.

## AEM Core Components {#aem-core-components}

[Les composants principaux AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr) sont un ensemble de composants WCM (Web Content Management, gestion de contenu web) normalisés pour AEM dont l’objectif est d’accélérer le développement et de réduire les coûts de maintenance de vos sites web.

Les composants principaux sont fournis avec AEM as a Cloud Service et le [tutoriel WKND](/help/implementing/developing/introduction/develop-wknd-tutorial.md) illustre la manière d’implémenter et d’utiliser les composants. Les composants sont fournis avec l’intégralité du code source et peuvent être utilisés tels quels ou comme points de départ pour des composants modifiés ou étendus.

### Affichage des composants disponibles {#viewing-available-components}

Pour un aperçu de tous les composants disponibles dans votre instance AEM, utilisez la méthode [Console Composants](/help/sites-cloud/authoring/features/components-console.md).

Vous pouvez également utiliser CRXDE Lite pour obtenir la liste de tous les composants disponibles dans le référentiel.

1. Dans **[!UICONTROL CRXDE Lite]**, sélectionnez **[!UICONTROL Outils]** dans la barre d’outils, puis sélectionnez **[!UICONTROL Requête]** pour ouvrir l’onglet **[!UICONTROL Requête]**.

1. Dans l’onglet **[!UICONTROL Requête]**, sélectionnez `XPath` comme **[!UICONTROL Type]**.

1. Dans la zone de saisie **[!UICONTROL Requête]**, entrez la chaîne suivante :

   `//element(*, cq:Component)`

1. Cliquez sur **[!UICONTROL Exécuter]** pour répertorier les composants.
