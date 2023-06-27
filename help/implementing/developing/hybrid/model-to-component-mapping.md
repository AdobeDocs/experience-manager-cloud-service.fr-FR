---
title: Mappage du modèle dynamique avec les composants pour les SPA
description: Cet article décrit comment le mappage du modèle dynamique avec les composants se produit dans le SDK SPA JavaScript pour AEM.
exl-id: 3a7b3f26-4a09-40c1-af03-bb8408a68e57
source-git-commit: d361ddc9a50a543cd1d5f260c09920c5a9d6d675
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 61%

---

# Mappage du modèle dynamique avec les composants pour les SPA {#dynamic-model-to-component-mapping-for-spas}

Ce document décrit comment le mappage du modèle dynamique avec les composants se produit dans le SDK SPA JavaScript pour AEM.

## Module ComponentMapping {#componentmapping-module}

Le module `ComponentMapping` est fourni au projet front-end sous la forme d’un package NPM. Il contient les composants front-end et permet à l’application sur une seule page (SPA) de mapper les composants front-end avec les types de ressources AEM. Le module active une résolution dynamique des composants lors de l’analyse du modèle JSON de l’application.

Chaque élément présent dans le modèle contient une `:type` qui expose un type de ressource AEM. Une fois monté, le composant front-end peut être rendu à l’aide du fragment de modèle reçu des bibliothèques associées.

Voir [Blueprint SPA](blueprint.md) pour plus d’informations sur l’analyse des modèles et l’accès des composants front-end au modèle.

Voir aussi le package npm : [@adobe/aem-spa-component-mapping](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)

## SPA pilotée par un modèle {#model-driven-single-page-application}

Les applications d’une seule page utilisant le SDK JavaScript SPA pour AEM sont pilotées par les modèles :

1. Les composants front-end s’enregistrent eux-mêmes dans le [magasin de mappage de composants](#componentmapping-module).
1. Ensuite, le [conteneur](blueprint.md#container), qui a reçu un modèle du [fournisseur de modèles](blueprint.md#the-model-provider), effectue une itération sur son contenu de modèle (`:items`).

1. S’il existe une page, ses enfants (`:children`) Commencez par obtenir une classe de composant à partir de la propriété [Mappage des composants](blueprint.md#componentmapping) puis instanciez-le.

## Initialisation de l’application {#app-initialization}

Chaque composant est étendu grâce aux capacités de la fonction [`ModelProvider`](blueprint.md#the-model-provider). L’initialisation se présente donc sous la forme générale suivante :

1. Chaque fournisseur de modèles s’initialise et écoute les modifications apportées au fragment de modèle qui correspond à son composant interne.
1. Le gestionnaire [`PageModelManager`](blueprint.md#pagemodelmanager) doit être initialisé tel qu’il est représenté par le [flux d’initialisation](blueprint.md).

1. Une fois stocké, le gestionnaire de modèles de page renvoie le modèle complet de l’application.
1. Ce modèle est ensuite transmis au composant racine front-end [Conteneur](blueprint.md#container) de l’application.
1. Les fragments du modèle sont finalement propagés à chaque composant enfant.

![Initialisation du modèle d’application](assets/app-model-initialization.png)
