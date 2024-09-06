---
title: Annotations de la vérification GitHub
description: Découvrez comment les vérifications GitHub annotent les requêtes d’extraction de vos référentiels privés afin de vous fournir des commentaires utiles.
exl-id: 15178de8-8a8a-4300-8510-88875ad0fc8c
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5d6d3374f2dd95728b2d3ed0cf6fab4092f73568
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 100%

---


# Annotations de la vérification GitHub {#github-annotations}

Découvrez comment les vérifications GitHub annotent les requêtes d’extraction de vos référentiels privés afin de vous fournir des commentaires utiles.

## Vue d’ensemble {#overview}

Si vous utilisez des [référentiels privés](private-repositories.md) pour votre programme Cloud Manager, les vérifications dans GitHub sont automatiquement exécutées pour chaque requête d’extraction. Elles sont annotées avec des informations utiles pour vous aider à comprendre les problèmes liés à votre code aussi rapidement que possible.

![Exemple d’annotations de vérification GitHub](assets/github-check-annotations.png)

Des problèmes de [qualité du code](/help/implementing/cloud-manager/code-quality-testing.md) détectés par [SonarQube](/help/implementing/cloud-manager/custom-code-quality-rules.md) sont clairement répertoriés.

![Exemple d’annotation de problème de code](assets/github-check-annotations-example.png)

La ligne de code exacte avec le problème est fournie et vous pouvez cliquer dessus pour afficher le code concerné. Ces annotations sont fournies pour tous les problèmes de code, pas seulement ceux qui ont été modifiés dans la requête d’extraction.

![Exemple d’annotation de problème de code](assets/github-check-annotations-example-code.png)

Toutes les lignes annotées sont regroupées dans l’onglet **Fichiers modifiés** de la requête d’extraction GitHub. Les annotations des fichiers qui n’ont pas été modifiés dans la requête d’extraction apparaissent dans leur propre section.

![Exemple d’annotations dans l’onglet Fichiers modifiés](assets/github-check-annotations-files-changed.png)

## Pipelines de qualité du code {#code-quality-pipelines}

Les résultats concernant la [qualité du code](/help/implementing/cloud-manager/code-quality-testing.md) sont également visibles dans le pipeline qui est automatiquement déclenché par Cloud Manager au bas de l’onglet **Vérifications**. Ils sont également accessibles dans les **Détails** de la vérification de la requête d’extraction.

![Exemple d’annotations](assets/github-check-annotations-code-quality.png)

![Exemple d’annotations](assets/github-check-annotations-code-quality-2.png)

Vous pouvez également visualiser les problèmes sous la forme d’un fichier CSV. Celui-ci peut être récupéré en [affichant les détails de l’exécution du pipeline dans Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#view-details).
