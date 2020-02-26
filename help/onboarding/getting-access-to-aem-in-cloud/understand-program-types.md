---
title: Présentation des types de programmes et de programmes
description: Présentation des types de programmes et de programmes - Services Cloud
translation-type: tm+mt
source-git-commit: 14da491cf09ed46ea425a8d65670d8b851aef388

---


# Présentation des programmes et des types de programmes {#understanding-programs}

Dans Cloud Manager, vous avez l’entité Tenant tout en haut qui peut comporter plusieurs programmes.  Chaque programme ne peut pas contenir plus d’un environnement de production et plusieurs environnements de non production.

Le diagramme suivant montre la hiérarchie des entités dans Cloud Manager.

![image](assets/program-types1.png)

## Types de programmes {#program-types}

Un utilisateur peut créer un **Sandbox** ou un programme **régulier** .

Une *sandbox* est généralement créée pour répondre aux besoins de la formation, de l’exécution des démos, de l’activation, des points de vue ou de la documentation. Il n&#39;est pas destiné à transporter du trafic en direct et il y aura des restrictions qu&#39;un programme régulier ne fera pas. Elle inclura des sites et des ressources et sera générée automatiquement avec une branche Git qui inclut un exemple de code, un environnement Dev et un pipeline de non-production.

Un programme ** régulier est créé pour activer le trafic en direct au moment approprié dans le futur.