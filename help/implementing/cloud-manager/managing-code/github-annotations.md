---
title: Annotations de la vérification GitHub
description: Découvrez comment les vérifications GitHub annotent les requêtes d’extraction de vos référentiels privés afin de vous fournir des commentaires utiles.
exl-id: 15178de8-8a8a-4300-8510-88875ad0fc8c
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: 'null'
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 52%

---


# Annotations de la vérification GitHub {#github-annotations}

Découvrez comment les vérifications GitHub annotent les requêtes d’extraction de vos référentiels privés afin de vous fournir des commentaires utiles.

## Vue d’ensemble {#overview}

Si vous utilisez des [référentiels privés](private-repositories.md) pour votre programme Cloud Manager, les vérifications dans GitHub sont automatiquement exécutées pour chaque requête d’extraction. Ces PR sont annotées avec des informations utiles pour vous aider à comprendre dès que possible tout problème lié à votre code.

![Exemple d’annotations de vérification GitHub](assets/github-check-annotations.png)

Des problèmes de [qualité du code](/help/implementing/cloud-manager/code-quality-testing.md) détectés par [SonarQube](/help/implementing/cloud-manager/custom-code-quality-rules.md) sont clairement répertoriés.

![Exemple d’annotation de problème de code](assets/github-check-annotations-example.png)

La ligne exacte de code avec le problème est fournie et vous pouvez la sélectionner pour afficher le code approprié. Ces annotations couvrent les problèmes de code, et pas seulement ceux de la demande d’extraction.

![Exemple d’annotation de problème de code](assets/github-check-annotations-example-code.png)

Toutes les lignes annotées sont regroupées dans l’onglet **Fichiers modifiés** de la requête d’extraction GitHub. Les annotations des fichiers de requête de tirage inchangés apparaissent dans leur propre section.

![Exemple d’annotations dans l’onglet Fichiers modifiés](assets/github-check-annotations-files-changed.png)

## Pipelines de qualité du code {#code-quality-pipelines}

Les résultats [qualité du code](/help/implementing/cloud-manager/code-quality-testing.md) sont également visibles dans le pipeline que Cloud Manager déclenche automatiquement au bas de l’onglet **Contrôles**. Elle est également accessible à partir de la **Détails** de la vérification de la requête de tirage.

![Exemple d’annotations](assets/github-check-annotations-code-quality.png)

![Exemple d’annotations](assets/github-check-annotations-code-quality-2.png)

Vous pouvez également visualiser les problèmes sous la forme d’un fichier CSV. Vous pouvez récupérer ce fichier CSV en [affichant les détails de l’exécution du pipeline dans Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#view-details).
