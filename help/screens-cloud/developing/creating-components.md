---
title: Création de composants
description: Les composants AEM servent à stocker, mettre en forme et générer le rendu du contenu diffusé dans vos pages web. Consultez cette page pour en savoir plus sur la création de canaux et le rendu de composants.
exl-id: a81e812e-29ed-45de-b2d0-1fb0a8c5ce1a
feature: Developing Screens
role: Admin, Developer
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 90%

---

# Création de composants {#creating-components}

Les composants AEM servent à stocker, mettre en forme et générer le rendu du contenu diffusé dans vos pages web.

## Création de canaux {#authoring-channels}

Le canal est l’objet central du contenu diffusé à un ensemble d’affichages. Par conséquent, un auteur ou une autrice de contenu ouvre généralement un canal dans l’éditeur pour ajouter ou modifier du contenu. Étant donné que le canal est un nœud ***cq:Page***, il applique le même schéma UX traditionnel pour ajouter et modifier des composants dans le canal.

Cependant, dans la mesure où les composants d’un canal sont généralement rendus en mode Plein écran, l’expérience de création est dégradée lorsque vous essayez de modifier des composants uniques ou de composer de nouvelles séquences. Par conséquent, le canal dépend des sélecteurs pour effectuer le rendu des différentes vues des composants. L’environnement de création utilise le sélecteur de modification pour activer le rendu de canal personnalisé.

Par exemple, `http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html`

L’utilisateur ne doit pas se charger de l’ajout du sélecteur à l’URL au cours de l’édition. Une logique côté client écoute l’événement de changement de calque et ajoute le sélecteur si le canal possède le type de ressource dédié *screens/core/components/channel.*

## Rendu des composants {#rendering-components}

Pour garantir une création correcte, les composants doivent fournir les deux rendus suivants :

| **Component** | **Rendus** |
|---|---|
| *my-component/my-component.html* | rendu de production |
| *my-component/edit.html* | modification du rendu dans une vue plus petite |

Les composants intégrés utilisent les catégories de bibliothèques clientes suivantes :

| **Component** | **Bibliothèque cliente** |
|---|---|
| *cq.screens.components.edit* | CSS et JS devant être chargés lors de la création |
| *cq.screens.components.production* | CSS et JS devant être chargés lorsque le canal est en cours d’exécution |
| *cq.screens.components* | CSS et JS partagés |

>[!NOTE]
>
>Pour développer des composants personnalisés, utilisez le ***[modèle d’exemple de composant AEM Screens](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)***.
