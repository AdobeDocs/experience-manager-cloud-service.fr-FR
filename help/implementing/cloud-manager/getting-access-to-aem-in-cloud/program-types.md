---
title: Programmes et types de programmes
description: Découvrez la hiérarchie de Cloud Manager et comment les différents types de programmes s’intègrent dans sa structure et en quoi ils diffèrent.
exl-id: 507df619-a5b5-419a-9e38-db77541425a2
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: dc4008a33f6a786884a9aad30096ff4f0561346c
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 42%

---


# Programmes et types de programmes {#understanding-programs}

Cloud Manager repose sur une hiérarchie d’entités. Les détails ne sont pas essentiels à votre travail quotidien dans Cloud Manager, mais un aperçu de ce dernier peut vous aider à comprendre les programmes et à configurer les vôtres.

![Hiérarchie de Cloud Manager](assets/program-types1.png)

* **TENANT** - Haut de la hiérarchie. Chaque client est configuré avec un identifiant client.
* **PROGRAMS** - Chaque client possède un ou plusieurs programmes, [qui reflètent souvent les solutions sous licence du client](introduction-production-programs.md).
* **ENVIRONNEMENTS** - Chaque programme comporte plusieurs environnements, tels que la production pour le contenu en direct, un pour l’évaluation et un à des fins de développement.
   * Chaque programme ne peut avoir qu’un seul environnement de production, mais plusieurs environnements hors production.
* **REPOSITORY** - Les programmes disposent de référentiels Git où le code d’application et le code frontal sont conservés pour les environnements.
* **OUTILS ET WORKFLOWS** - Les pipelines gèrent le déploiement du code des référentiels vers les environnements, tandis que d’autres outils permettent d’accéder aux journaux, à la surveillance et à la gestion de l’environnement.

Un exemple est souvent utile pour contextualiser cette hiérarchie.

* Disons que WKND Travel and Adventure Enterprises est un **client** qui se concentre sur les médias liés aux voyages.
* Disons que le client WKND Travel and Adventure Enterprises peut avoir deux **programmes** : un programme Sites pour WKND Magazine et un programme Assets pour WKND Media.
* Les programmes de WKND Magazine et de WKND Media auraient chacun des **environnements** de développement, d’évaluation et de production.

## Référentiel de code source {#source-code-repository}

Un programme Cloud Manager est fourni automatiquement avec son propre référentiel Git.

Les utilisateurs peuvent accéder au référentiel Git Cloud Manager à l’aide d’un client Git avec un outil de ligne de commande ou un client Git visuel autonome. Ils peuvent également utiliser leur environnement de développement intégré (IDE) préféré, comme Eclipse, IntelliJ ou NetBeans.

Une fois un client Git configuré, vous pouvez gérer votre référentiel Git à partir de l’interface utilisateur de Cloud Manager. Pour en savoir plus sur la gestion de Git à l’aide de l’interface utilisateur de Cloud Manager, voir [Accès à Git](/help/implementing/cloud-manager/managing-code/accessing-repos.md).

Pour commencer à développer l’application AEM Cloud, extrayez le code de l’application du référentiel Cloud Manager sur votre ordinateur local.

```java
$ git clone {URL}
```

Le workflow suit un processus Git standard :

1. Un utilisateur clone localement le référentiel Git distant.
1. L’utilisateur apporte des modifications dans son référentiel local.
1. Une fois prêt, l’utilisateur révalide les modifications dans le référentiel Git distant.

La seule différence est que le référentiel Git distant fait partie de Cloud Manager, qui est transparent pour le développeur.

## Types de programmes {#program-types}

Un utilisateur peut créer un programme **production** ou un programme **sandbox**.

* Un **programme de production** est créé pour activer le trafic en direct pour votre site.
   * Consultez [Présentation des programmes de production](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md) pour plus d’informations.
* Un **programme sandbox** est généralement créé pour les besoins de formation, à des fins de démonstration, d’activation, de preuve de concept ou de documentation.
   * Un environnement de test n’est pas destiné à transporter du trafic en direct et comporte des restrictions qu’un programme de production ne prévoit pas.
   * Elle comprend des sites, Assets et des Edge Delivery Services. Elle est préremplie avec une branche Git contenant un exemple de code, un environnement de développement et un pipeline hors production.
   * Consultez [Présentation des programmes de sandbox](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md) pour plus d’informations.
