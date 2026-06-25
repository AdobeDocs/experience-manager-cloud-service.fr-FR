---
title: Gestion des versions du projet Maven
description: Pour les déploiements d’évaluation et de production d’AEM as a Cloud Service, Cloud Manager génère une version incrémentée unique
exl-id: 658bcbed-0733-45da-a3e3-9a5f817099c5
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: 6f5eadfcf66d6726bd279347eeed22938d3f271d
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 82%

---


# Gestion des versions de projet par Maven {#maven-project-version-handling}

Pour les déploiements d’évaluation et de production d’AEM as a Cloud Service, Cloud Manager génère une version incrémentée unique.

Cette version est affichée sur la [page des détails d’exécution du pipeline](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#view-details), ainsi que sur la page des activités. Lorsqu’une génération est exécutée, le projet Maven est mis à jour pour utiliser cette version et une balise est créée dans le référentiel Git avec cette version comme nom.

Si la version d’origine du projet répond à certains critères, la version mise à jour du projet Maven fusionne la version originale du projet et la version générée par Cloud Manager. Toutefois, la balise utilise toujours la version générée. Pour que cette fusion s’effectue, la version initiale du projet doit être formée avec exactement trois segments de version, comme `1.0.0` ou `1.2.3`, mais pas `1.0` ou `1`. Par ailleurs, la version initiale ne doit pas se terminer par `-SNAPSHOT`.

>[!IMPORTANT]
>
>Cette valeur de version de projet d’origine doit être définie de manière statique dans l’élément `<version>` du fichier `pom.xml` de niveau supérieur dans la branche du référentiel Git.

Si la version d’origine ne répond pas à ces critères, la version générée est ajoutée à la version d’origine en tant que segment de nouvelle version. La version générée est également ajustée pour prendre en charge un tri et une gestion des versions précis. Par exemple, en supposant qu’une version générée de `2019.926.121356.0000020490` produise les résultats suivants.

| Version | Version dans `pom.xml` | Commentaire |
| --- |--- | --- |
| `1.0.0` | `1.0.0.2019_0926_121356_0000020490` | Version originale correctement formée |
| `1.0.0-SNAPSHOT` | `2019.926.121356.0000020490` | Version Snapshot, écrasée |
| `1` | `2019.926.121356.0000020490` | Version incomplète, écrasée |

>[!NOTE]
>
>Que la version d’origine ait été incorporée ou non dans la version initialisée de Cloud Manager, la version d’origine est disponible sous la forme d’une propriété Maven nommée `cloudManagerOriginalVersion`.
