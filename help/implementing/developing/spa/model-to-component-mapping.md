---
title: Mappage Modèle dynamique/Composant pour les applications monopages
description: Cet article décrit comment le mappage modèle dynamique/composant se produit dans le SDK SPA JavaScript pour AEM.
translation-type: tm+mt
source-git-commit: c075bcc415b68ba0deaeca61d6d179bd7263ca5f
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---


# Mappage Modèle dynamique/Composant pour les applications monopages {#dynamic-model-to-component-mapping-for-spas}

Ce document décrit comment le mappage modèle dynamique avec composant se produit dans le SDK SPA JavaScript pour AEM.

## Module ComponentMapping {#componentmapping-module}

The `ComponentMapping` module is provided as an NPM package to the front-end project. Il stocke les composants frontaux et permet à l’application d’une seule page de mapper les composants frontaux aux types de ressources AEM. Ceci active une résolution dynamique des composants lors de l’analyse du modèle JSON de l’application.

Chaque élément présent dans le modèle contient un `:type` champ qui expose un type de ressource AEM. Une fois monté, le composant frontal peut être rendu à l’aide du fragment de modèle reçu des bibliothèques sous-jacentes.

Pour plus d&#39;informations sur l&#39;analyse des modèles et sur l&#39;accès des composants frontaux au modèle, consultez le document [SPA Blueprint](blueprint.md) .

Voir aussi le package npm : [@adobe/aem-spa-component-mapping](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)

## Application d&#39;une seule page pilotée par un modèle {#model-driven-single-page-application}

Les applications d’une seule page qui utilisent le SDK SPA Javascript pour AEM sont pilotées par des modèles :

1. Les composants frontaux s&#39;enregistrent dans le magasin [de mappage des](#componentmapping-module)composants.
1. Ensuite, le [Conteneur](blueprint.md#container), une fois fourni avec un modèle par le fournisseur [de](blueprint.md#the-model-provider)modèles, effectue une itération sur son contenu de modèle (`:items`).

1. Dans le cas d’une page, ses enfants (`:children`) obtiennent d’abord une classe de composants à partir du mappage [des](blueprint.md#componentmapping) composants, puis l’instancient.

## Initialisation de l’application {#app-initialization}

Chaque composant est étendu avec les capacités de la [`ModelProvider`](blueprint.md#the-model-provider)fonction. L&#39;initialisation se présente donc sous la forme générale suivante :

1. Chaque fournisseur de modèles s’initialise et écoute les modifications apportées à la pièce de modèle qui correspond à son composant interne.
1. Le [`PageModelManager`](blueprint.md#pagemodelmanager) fichier doit être initialisé tel qu’il est représenté par le flux [d’](blueprint.md)initialisation.

1. Une fois stocké, le gestionnaire de modèles de page renvoie le modèle complet de l’application.
1. Ce modèle est ensuite transmis au composant [Conteneur](blueprint.md#container) racine principal de l’application.
1. Les fragments du modèle sont finalement propagés à chaque composant enfant individuel.

![Initialisation du modèle d’application](assets/app-model-initialization.png)
