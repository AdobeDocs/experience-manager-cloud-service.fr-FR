---
title: Configuration de la vérification GitHub pour les référentiels privés
description: Découvrez comment contrôler les pipelines créés automatiquement afin de valider chaque requête d’extraction dans un référentiel privé.
exl-id: 3ae3c19e-2621-4073-ae17-32663ccf9e7b
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 0a08d5fc033f4f4f57b824492766e5b42a801b6e
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 33%

---

# Configuration de la vérification GitHub pour les référentiels privés {#github-check-config}

Découvrez comment contrôler les pipelines créés automatiquement afin de valider chaque requête d’extraction dans un référentiel privé.

## Configuration des vérifications GitHub {#configuration}

Lors de l’utilisation de [référentiels privés](private-repositories.md#using), un [pipeline de qualité de code de pile pleine](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) est créé automatiquement. Ce pipeline démarre à chaque mise à jour de demande d’extraction.

Vous pouvez contrôler ces contrôles en créant un fichier de configuration `.cloudmanager/pr_pipelines.yml` dans la branche par défaut du référentiel privé.

```yaml
github:
  shouldDeletePreviousComment: false
  shouldSkipCheckAnnotations: false
pipelines:
  - type: CI_CD
    template:
      programId: 1234
      pipelineId: 456
    namePrefix: Full Stack Code Quality Pipeline for PR
    importantMetricsFailureBehavior: CONTINUE
```

| Paramètre | Valeurs possibles | Valeur par défaut | Description |
| --- | --- | --- | --- |
| `shouldDeletePreviousComment` | `true` ou `false` | `false` | Si vous souhaitez conserver uniquement le dernier commentaire avec les résultats de l’analyse du code sur cette demande d’extraction GitHub ou conserver tout. La définition de cette valeur sur `false` (valeur par défaut) signifie que les commentaires précédents ne sont pas supprimés. |
| `shouldSkipCheckAnnotations` | `true` ou `false` | `false` | Indique si des annotations supplémentaires doivent être présentes dans la vérification de la requête d’extraction GitHub. La définition de cette valeur sur `false` (par défaut) signifie que les annotations de vérification ne sont pas ignorées et sont incluses dans les commentaires. |
| `type` | `CI_CD` | n/a | Définit le comportement des configurations de pipeline CI/CD (intégration continue/déploiement continu). |
| `template.programId` | Entier | Aucune variable de pipeline n’est réutilisée. | Vous pouvez l’utiliser pour réutiliser les [variables de pipeline](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md) définies sur un pipeline existant automatiquement créé par chaque requête de tirage. |
| `template.pipelineId` | Entier | Aucune variable de pipeline n’est réutilisée. | Vous pouvez l’utiliser pour réutiliser les [variables de pipeline](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md) définies sur un pipeline existant automatiquement créé par chaque requête de tirage. |
| `namePrefix` | Chaîne | `Full Stack Code Quality Pipeline for PR` | Utilisé pour définir le préfixe du nom du pipeline créé automatiquement. |
| `importantMetricsFailureBehavior` | `CONTINUE` ou `FAIL` ou `PAUSE` | `CONTINUE` | Définit le comportement de mesure important du pipeline<br>`CONTINUE` = Si une mesure importante échoue, le pipeline se déplace automatiquement<br>`FAIL` = Le pipeline se termine avec un état ÉCHEC si une mesure importante échoue<br>`PAUSE` = L’étape d’analyse du code reçoit un état ATTENDU lorsqu’une mesure importante échoue et doit être reprise manuellement |




