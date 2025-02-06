---
title: Blocs pour la création WYSIWYG et la création basée sur les documents
description: Découvrez comment créer des blocs utilisables à la fois pour la création WYSIWYG et pour la création basée sur des documents.
feature: Edge Delivery Services
role: User
exl-id: f039c70a-e1a0-4fcc-8f42-dfa0f8bb3764
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 82%

---

# Blocs pour la création WYSIWYG et la création basée sur les documents {#wysiwyg-and-doc-blocks}

Découvrez comment créer des blocs utilisables à la fois pour la création WYSIWYG et pour la création basée sur des documents.

## Vue d’ensemble {#overview}

Sur certains projets, vous pouvez prendre en charge la création de [WYSIWYG à l’aide de l’éditeur universel](/help/edge/wysiwyg-authoring/authoring.md) ainsi que la création [basée sur des documents](/help/edge/docs/authoring.md). Pour réduire le temps de développement et garantir la même expérience sur le site, vous pouvez créer un ensemble de blocs pour prendre en charge les deux cas d’utilisation.

Pour ce faire, vous devez utiliser la même approche de modélisation de contenu pour votre configuration de création WYSIWYG, ainsi que pour votre configuration de création basée sur des documents.

## Approche {#approach}

Dans la création WYSIWYG dans AEM, vous [déclarez un modèle](/help/edge/wysiwyg-authoring/content-modeling.md) et fournissez des conventions de nommage. Les données sont ensuite rendues dans des structures de blocs de type tableau à l’aide d’Edge Delivery de la même manière que si le tableau avait été créé manuellement à l’aide de la création basée sur les documents.

Pour ce faire, certaines hypothèses sont faites, par exemple pour un bloc simple comme un teaser, selon lequel toutes les propriétés et tous les groupes de propriétés sont rendus dans 1..n lignes comportant chacune une seule colonne. Pour les blocs comportant 1..n éléments (carousel et cartes, par exemple), les éléments sont ajoutés après ces lignes avec une ligne chacune et une colonne pour chaque propriété/groupe de propriétés.

Si vous appliquez la même approche pour la création basée sur des documents, vous pouvez réutiliser vos blocs WYSIWYG.
