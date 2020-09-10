---
title: ContextHub
description: ContextHub est un framework qui permet de stocker, de manipuler et de présenter des données de contexte
translation-type: tm+mt
source-git-commit: 75d6b51c0148a21ca401d98a5eaf644fc6b0e8cc
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 65%

---


# ContextHub {#contexthub}

ContextHub est une structure pour stocker, manipuler et présenter des données contextuelles. Il est Principal de proposer la possibilité de [vue des données contextuelles tout en simulant et en changeant de personne.](/help/sites-cloud/authoring/personalization/contexthub.md)

ContextHub vous permet d’effectuer les opérations suivantes :

* [Présenter, vue, changer de personne et simuler l’expérience](#presentation) de l’utilisateur lors de la création de pages à l’aide de données contextuelles.
* [Persister les données](#persistence) contextuelles sur votre site Web en tant que représentation de couche de données.
* [Gérez les segments](#segmentation) pour le contexte sélectionné.

L’API Javascript côté client vous permet d’accéder aux données pour personnaliser le contenu.

## Présentation {#presentation}

La barre d’outils [ContextHub](/help/sites-cloud/authoring/personalization/contexthub.md) permet aux spécialistes du marketing et aux auteurs de voir et de manipuler les données du magasin afin de simuler l’expérience utilisateur lors de la création de pages. La barre d’outils est constituée de groupes de modules d’interface qui permettent d’accéder aux magasins [ContextHub,](#persistence) qui conservent les données ContextHub sur le client.

Chaque module d’IU ContextHub est une instance d’un type de module prédéfini :

* ContextHub fournit plusieurs [exemples de types de module](sample-modules.md).
* Utilisez les consoles AEM pour [ajouter des modules d’IU](configuring-contexthub.md#adding-a-ui-module) et [pour les regrouper en modes IU](configuring-contexthub.md#adding-a-ui-mode).
* Les développeurs peuvent [créer des types de module personnalisés](extending-contexthub.md#creating-contexthub-ui-module-types).

Les développeurs doivent [ajouter le composant ContextHub à la page](configuring-contexthub.md).

## Persistance {#persistence}

ContextHub stocke les données de contexte de persistance sur le client. L’API Javascript ContextHub vous permet d’accéder aux magasins pour créer, mettre à jour et supprimer des données si nécessaire. En tant que tel, ContextHub représente une couche de données sur vos pages.

Chaque magasin ContextHub est une instance d’un type de magasin prédéfini :

* ContextHub fournit plusieurs [exemples de types de magasin](sample-stores.md).
* Utilisez les consoles AEM pour [créer des magasins](configuring-contexthub.md#creating-a-contexthub-store).
* Developers can [create custom store types](extending-contexthub.md#creating-custom-store-candidates).
* Les développeurs peuvent [accéder aux données du magasin](configuring-contexthub.md#interacting-with-contexthub-stores) via Javascript.

## Segmentation {#segmentation}

ContextHub propose un moteur de segmentation qui gère les segments et détermine les segments qui sont résolus pour le contexte actuel. Plusieurs segments sont définis. Vous pouvez utiliser l’API Javascript pour [déterminer les segments résolus](configuring-contexthub.md#determining-resolved-contexthub-segments).
