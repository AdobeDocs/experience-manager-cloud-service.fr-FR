---
title: Analyse des fragments de contenu
description: comprendre la structure de vos fragments de contenu ; Vous obtiendrez ainsi des informations pertinentes pour la diffusion découplée et la création de pages.
feature: Content Fragments
role: User, Developer
exl-id: d9268c1a-bfe6-4df7-bad9-6007dd79e0aa
solution: Experience Manager Sites
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 3%

---

# Analyse de la structure du fragment de contenu {#analyzing-content-fragments-structure}

Les fragments de contenu sont conçus pour une diffusion [découplée à l’aide de GraphQL](/help/sites-cloud/administering/content-fragments/content-delivery-with-graphql.md). Cela signifie qu’ils peuvent avoir une structure à plusieurs couches.

Experience Manager (AEM) propose plusieurs méthodes d’affichage et d’analyse de la structure de vos fragments.

## Références {#references}

La structure multicouche est créée à l’aide de références :

* [Les types de données pour les références sont définis dans le modèle de fragment de contenu](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#using-references-to-form-nested-content)
* Lors de la création, vous pouvez :
   * [Gérer ces références](/help/sites-cloud/administering/content-fragments/authoring.md##manage-references)
   * [Recherche des références parentes du fragment](/help/sites-cloud/administering/content-fragments/managing.md#parent-references-fragment)

## Arborescence de la structure {#structure-tree}

Ouvrez l’onglet **Arborescence de structure** de la barre d’outils de l’éditeur pour afficher la structure hiérarchique du fragment de contenu et ses références. Utilisez l’icône de lien pour ouvrir les références.

Par exemple :

![Éditeur de fragment de contenu - Arborescence de structure](assets/cf-authoring-structure-tree.png)
