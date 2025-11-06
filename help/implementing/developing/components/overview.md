---
title: Aperçu des composants
description: Les composants sont des unités modulaires qui exécutent des fonctionnalités spécifiques pour présenter du contenu sur votre site web.
exl-id: 0fdc99e7-2103-448d-8217-d5d52c94acea
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 66%

---

# Aperçu des composants {#components-overview}

Cette page donne un aperçu des composants AEM (Adobe Experience Manager), tels que ceux [utilisés pour la création de pages](/help/sites-cloud/authoring/page-editor/components.md).

## Que sont les composants ?  {#what-are-components}

* sont des unités modulaires qui exécutent des fonctionnalités spécifiques pour présenter du contenu sur votre site web ;
* Réutilisable.
* sont développés comme des unités autonomes dans un seul dossier du référentiel ;
* ne comportent aucun fichier de configuration masqué ;
* Ils peuvent contenir d’autres composants.
* Ils peuvent s’exécuter n’importe où dans n’importe quel système AEM et peuvent également être limités à des composants spécifiques.
* possèdent une interface utilisateur standardisée ;
* sont associés à un comportement de modification qui peut être configuré ;
* Utilisez des boîtes de dialogue créées à l’aide de sous-éléments basés sur les composants de l’IU Granite.
* Ils sont développés à l’aide de [HTL](https://experienceleague.adobe.com/docs/experience-manager-htl/using/overview.html?lang=fr).
* Ils peuvent être développés pour créer des composants personnalisés qui étendent la fonctionnalité par défaut.

Les composants étant modulaires, vous pouvez :

* développer un nouveau composant sur votre instance locale ;
* Déployer ce composant sur votre environnement de test.
* Déployer le composant sur votre environnement de création actif et permettre ainsi aux auteurs et/ou développeurs d’ajouter et de configurer du contenu.
* Déployez-le dans vos environnements de publication actifs, où il est utilisé pour effectuer le rendu du contenu à l’intention des visiteurs et visiteuses de votre site web.

Chaque composant AEM :

* est un type de ressource ;
* est un ensemble de scripts qui exécutent complètement une fonction spécifique ;
* peut fonctionner de manière isolée, c’est-à-dire soit dans AEM, soit dans un portail.

## Composants principaux AEM {#aem-core-components}

[Les composants principaux AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr) sont un ensemble de composants de gestion de contenu web (Web Content Management, WCM) normalisés pour AEM dont l’objectif est d’accélérer le développement et de réduire les coûts de maintenance de vos sites Web.

Les composants principaux sont fournis avec AEM as a Cloud Service et le [tutoriel WKND](/help/implementing/developing/introduction/develop-wknd-tutorial.md) illustre la manière d’implémenter et d’utiliser les composants. Les composants sont fournis avec l’intégralité du code source et peuvent être utilisés tels quels ou comme points de départ pour des composants modifiés ou étendus.

### Affichage des composants disponibles {#viewing-available-components}

Pour obtenir un aperçu de tous les composants disponibles dans votre instance AEM, utilisez la [Console des composants](/help/sites-cloud/authoring/components-console.md).

Vous pouvez également utiliser CRXDE Lite pour obtenir la liste de tous les composants disponibles dans le référentiel.

1. Dans **[!UICONTROL CRXDE Lite]**, sélectionnez **[!UICONTROL Outils]** dans la barre d’outils, puis sélectionnez **[!UICONTROL Requête]** pour ouvrir l’onglet **[!UICONTROL Requête]**.

1. Dans l’onglet **[!UICONTROL Requête]**, sélectionnez `XPath` comme **[!UICONTROL Type]**.

1. Dans le champ de saisie **[!UICONTROL Requête]**, saisissez la chaîne suivante :

   `//element(*, cq:Component)`

1. Cliquez sur **[!UICONTROL Exécuter]** pour répertorier les composants.
