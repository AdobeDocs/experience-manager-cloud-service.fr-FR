---
title: ContextHub
description: ContextHub est une structure pour stocker, manipuler et présenter des données contextuelles
exl-id: 604477c6-d96a-441f-b5fc-5def93832478
feature: Developing, Personalization
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 86%

---

# ContextHub {#contexthub}

ContextHub est une structure pour stocker, manipuler et présenter des données contextuelles. Sa principale fonctionnalité permet d’[afficher des données contextuelles tout en simulant et en basculant entre différentes personnages](/help/sites-cloud/authoring/personalization/contexthub.md).

ContextHub vous permet d’effectuer les opérations suivantes :

* [Présenter, afficher, changer de personnages et simuler l’expérience utilisateur](#presentation) tout en créant des pages à l’aide de données contextuelles.
* [Conserver les données contextuelles](#persistence) sur votre site web en tant que représentation de couche de données.
* [Gérer les segments](#segmentation) pour le contexte sélectionné.

L’API Javascript côté client vous permet d’accéder aux données pour personnaliser le contenu.

## Présentation {#presentation}

La barre d’outils [ContextHub](/help/sites-cloud/authoring/personalization/contexthub.md) permet aux spécialistes du marketing et aux auteurs de voir et de manipuler les données du magasin afin de simuler l’expérience utilisateur lors de la création de pages. La barre d’outils se compose de groupes de modules d’interface utilisateur qui permettent d’accéder aux [magasins ContextHub](#persistence), qui conservent les données ContextHub sur le client.

Chaque module d’IU ContextHub est une instance d’un type de module prédéfini :

* ContextHub fournit plusieurs [exemples de types de module](sample-modules.md).
* Utilisez les consoles AEM pour [ajouter des modules d’IU](configuring-contexthub.md#adding-a-ui-module) et [les regrouper en modes d’IU](configuring-contexthub.md#adding-a-ui-mode).
* Les développeurs et développeuses peuvent [créer des types de module personnalisés](extending-contexthub.md#creating-contexthub-ui-module-types).

Les développeurs et développeuses doivent [ajouter le composant ContextHub à la page](configuring-contexthub.md).

## Persistance {#persistence}

ContextHub stocke les données de contexte de persistance sur le client. L’API JavaScript ContextHub vous permet d’accéder aux magasins pour créer, mettre à jour et supprimer des données si nécessaire. En tant que tel, ContextHub représente une couche de données sur vos pages.

Chaque magasin ContextHub est une instance d’un type de magasin prédéfini :

* ContextHub fournit plusieurs [exemples de types de magasin](sample-stores.md).
* Utilisez les consoles AEM pour [créer des magasins](configuring-contexthub.md#creating-a-contexthub-store).
* Les développeurs peuvent [créer des types de magasin personnalisés](extending-contexthub.md#creating-custom-store-candidates).
* Les développeurs et développeuses peuvent [accéder aux données du magasin](adding-contexthub.md#interacting-with-contexthub-stores) par le biais de JavaScript.

## Segmentation {#segmentation}

ContextHub propose un moteur de segmentation qui gère les segments et détermine les segments qui sont résolus pour le contexte actuel. Plusieurs segments sont définis. Vous pouvez utiliser l’API JavaScript pour [déterminer les segments résolus](adding-contexthub.md#determining-resolved-contexthub-segments).
