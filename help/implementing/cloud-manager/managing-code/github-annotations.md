---
title: Annotations de vérification GitHub
description: Découvrez comment GitHub vérifie l’annotation des relations publiques pour vos référentiels privés afin de vous fournir des commentaires utiles.
exl-id: 15178de8-8a8a-4300-8510-88875ad0fc8c
source-git-commit: f7348d388918a31d255babcfb64b3dc547153d62
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---


# Annotations de vérification GitHub {#github-annotations}

Découvrez comment GitHub vérifie l’annotation des relations publiques pour vos référentiels privés afin de vous fournir des commentaires utiles.

## Vue d’ensemble {#overview}

Si vous utilisez [référentiels privés](private-repositories.md) pour votre programme Cloud Manager, les contrôles dans GitHub sont automatiquement exécutés pour chaque demande d’extraction. Elles sont annotées avec des informations utiles pour vous aider à comprendre dès que possible les problèmes liés à votre code.

![Exemple d’annotations de vérification GitHub](assets/github-check-annotations.png)

[Qualité du code](/help/implementing/cloud-manager/code-quality-testing.md) problèmes détectés par [SonarQube](/help/implementing/cloud-manager/custom-code-quality-rules.md) sont clairement répertoriées.

![Exemple d’annotation de problème de code](assets/github-check-annotations-example.png)

La ligne de code exacte avec le problème est fournie et vous pouvez cliquer dessus pour afficher le code approprié. Ces annotations sont fournies pour tous les problèmes de code, et pas seulement ceux qui ont été modifiés dans la requête de tirage.

![Exemple d’annotation de problème de code](assets/github-check-annotations-example-code.png)

Toutes les lignes annotées sont agrégées sur le **Fichiers modifiés** sur la requête de tirage GitHub. Les annotations des fichiers qui n’ont pas été modifiés dans la requête de tirage apparaissent dans leur propre section.

![Exemple d’annotations sur l’onglet des fichiers modifiés](assets/github-check-annotations-files-changed.png)

## Pipelines de qualité du code {#code-quality-pipelines}

La variable [qualité du code](/help/implementing/cloud-manager/code-quality-testing.md) les résultats sont également visibles dans le pipeline qui est automatiquement déclenché par Cloud Manager au bas de la **Vérifications** . Il est également accessible à partir de la **Détails** de la vérification de la requête de tirage.

![Exemple d’annotations](assets/github-check-annotations-code-quality.png)

![Exemple d’annotations](assets/github-check-annotations-code-quality-2.png)

Vous pouvez également visualiser les problèmes sous la forme d’un fichier CSV. Elle peut être récupérée par [affichage des détails de l’exécution du pipeline dans Cloud Manager.](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#view-details)
