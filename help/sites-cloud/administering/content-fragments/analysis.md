---
title: Analyse des fragments de contenu
description: Découvrez la structure et la diffusion de contenu de vos fragments de contenu. Cela permet d’assurer la diffusion sans interface utilisateur et la création de pages.
feature: Content Fragments
role: User, Developer, Architect
source-git-commit: 3d20f4bca566edcdb5f13eab581c33b7f3cf286d
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 2%

---


# Analyse de la structure de fragments de contenu {#analyzing-content-fragments-structure}

Les fragments de contenu sont conçus pour [Diffusion sans affichage à l’aide de GraphQL](/help/sites-cloud/administering/content-fragments/content-delivery-with-graphql.md). Cela signifie qu’ils peuvent avoir une structure à plusieurs niveaux.

Experience Manager (AEM) propose plusieurs méthodes pour visualiser et analyser la structure de vos fragments.

## Références {#references}

La structure est construite à l’aide de Références :

* [Les types de données pour les références sont définis dans le modèle de fragment de contenu.](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#using-references-to-form-nested-content)
* Lors de la création, vous pouvez :
   * [Gérer ces références](/help/sites-cloud/administering/content-fragments/authoring.md##manage-references)
   * [Recherche des références parentes de votre fragment](/help/sites-cloud/administering/content-fragments/managing.md#parent-references-fragment)

## Arborescence de structure {#structure-tree}

Ouvrez le **Arborescence de structure** de la barre d’outils de l’éditeur pour afficher la structure hiérarchique du fragment de contenu et ses références. Utilisez l’icône de lien pour ouvrir les références.

Par exemple :

![Éditeur de fragment de contenu - Arborescence de structure](assets/cf-authoring-structure-tree.png)