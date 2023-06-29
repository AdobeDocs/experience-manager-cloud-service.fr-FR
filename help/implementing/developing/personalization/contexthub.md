---
title: ContextHub
description: ContextHub est une structure pour stocker, manipuler et présenter des données contextuelles
exl-id: 604477c6-d96a-441f-b5fc-5def93832478
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 58%

---

# ContextHub {#contexthub}

ContextHub est une structure pour stocker, manipuler et présenter des données contextuelles. Il vise principalement à offrir la possibilité d’[afficher des données contextuelles tout en simulant divers personnages et en passant de l’une à l’autre](/help/sites-cloud/authoring/personalization/contexthub.md).

ContextHub vous permet d’effectuer les opérations suivantes :

* [Présenter, afficher, changer de personnages et simuler l’expérience utilisateur](#presentation) tout en créant des pages à l’aide de données contextuelles.
* [Conserver les données contextuelles](#persistence) sur votre site web en tant que représentation de couche de données.
* [Gérer les segments](#segmentation) pour le contexte sélectionné.

L&#39;API JavaScript côté client permet d&#39;accéder aux données pour personnaliser le contenu.

## Présentation {#presentation}

La barre d’outils [ContextHub](/help/sites-cloud/authoring/personalization/contexthub.md) permet aux spécialistes du marketing et aux auteurs de voir et de manipuler les données du magasin afin de simuler l’expérience utilisateur lors de la création de pages. La barre d’outils est constituée de groupes de modules d’interface utilisateur qui permettent d’accéder aux [magasins ContextHub,](#persistence) lesquels conservent les données ContextHub sur le client.

Chaque module d’IU ContextHub est une instance d’un type de module prédéfini :

* ContextHub fournit plusieurs [exemples de types de module](sample-modules.md).
* Utilisez AEM consoles pour [ajout de modules d’IU](configuring-contexthub.md#adding-a-ui-module)et à [les regrouper en modes d’interface utilisateur](configuring-contexthub.md#adding-a-ui-mode).
* Les développeurs peuvent [créer des types de module personnalisés ;](extending-contexthub.md#creating-contexthub-ui-module-types).

Les développeurs doivent [ajouter le composant ContextHub à la page ;](configuring-contexthub.md).

## Persistance {#persistence}

ContextHub stocke les données de contexte de persistance sur le client. L’API JavaScript ContextHub vous permet d’accéder aux magasins pour créer, mettre à jour et supprimer des données si nécessaire. En tant que tel, ContextHub représente une couche de données sur vos pages.

Chaque magasin ContextHub est une instance d’un type de magasin prédéfini :

* ContextHub fournit plusieurs [exemples de types de magasin](sample-stores.md).
* Utilisez AEM consoles pour [créer des magasins](configuring-contexthub.md#creating-a-contexthub-store).
* Les développeurs peuvent [créer des types de magasin personnalisés](extending-contexthub.md#creating-custom-store-candidates).
* Les développeurs peuvent [accès aux données du magasin](adding-contexthub.md#interacting-with-contexthub-stores) par le biais de JavaScript.

## Segmentation {#segmentation}

ContextHub propose un moteur de segmentation qui gère les segments et détermine les segments qui sont résolus pour le contexte actuel. Plusieurs segments sont définis. Vous pouvez utiliser l’API JavaScript pour [déterminer les segments résolus ;](adding-contexthub.md#determining-resolved-contexthub-segments).
