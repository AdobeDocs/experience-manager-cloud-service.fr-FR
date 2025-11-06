---
title: Programmes et types de programmes
description: Découvrez la hiérarchie de Cloud Manager et comment les différents types de programmes s’intègrent dans sa structure et en quoi ils diffèrent.
exl-id: 507df619-a5b5-419a-9e38-db77541425a2
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 42%

---


# Programmes et types de programmes {#understanding-programs}

Cloud Manager repose sur une hiérarchie d’entités. Les détails ne sont pas essentiels à votre travail au quotidien dans Cloud Manager, mais un aperçu peut vous aider à comprendre les programmes et à configurer les vôtres.

![Hiérarchie de Cloud Manager](assets/program-types1.png)

* **CLIENT** - Haut de la hiérarchie. Chaque client est configuré avec un identifiant client.
* **PROGRAMMES** - Chaque client possède un ou plusieurs programmes, [qui reflètent souvent les solutions sous licence du client](introduction-production-programs.md).
* **ENVIRONNEMENTS** - Chaque programme comporte plusieurs environnements, tels que la production pour le contenu en direct, un pour l’évaluation et un à des fins de développement.
   * Chaque programme ne peut avoir qu’un seul environnement de production, mais plusieurs environnements hors production.
* **RÉFÉRENTIEL** - Les programmes disposent de référentiels Git dans lesquels l’application et le code front-end sont conservés pour les environnements.
* **OUTILS ET WORKFLOWS** - Les pipelines gèrent le déploiement du code des référentiels vers les environnements, tandis que d’autres outils permettent d’accéder aux journaux, à la surveillance et à la gestion de l’environnement.

Un exemple est souvent utile pour contextualiser cette hiérarchie.

* Disons que WKND Travel and Adventure Enterprises est un **client** qui se concentre sur les médias liés aux voyages.
* Disons que le client WKND Travel and Adventure Enterprises peut avoir deux **programmes** : un programme Sites pour WKND Magazine et un programme Assets pour WKND Media.
* Les programmes de WKND Magazine et de WKND Media auraient chacun des **environnements** de développement, d’évaluation et de production.

## Référentiel de code source {#source-code-repository}

Un programme Cloud Manager est automatiquement configuré avec son propre référentiel Git.

Les utilisateurs peuvent accéder au référentiel Git de Cloud Manager à l’aide d’un client Git avec un outil de ligne de commande ou un client Git visuel autonome. Ils peuvent également utiliser leur environnement de développement intégré (IDE) préféré, tel qu’Eclipse, IntelliJ ou NetBeans.

Une fois le client Git configuré, vous pouvez gérer votre référentiel Git à partir de l’interface utilisateur de Cloud Manager. Pour en savoir plus sur la gestion de Git à l’aide de l’interface utilisateur de Cloud Manager, voir [Accès à Git](/help/implementing/cloud-manager/managing-code/accessing-repos.md).

Pour commencer à développer l’application AEM Cloud, extrayez le code de l’application du référentiel Cloud Manager sur votre ordinateur local.

```java
$ git clone {URL}
```

Le workflow suit un processus Git standard :

1. Un utilisateur clone localement le référentiel Git distant.
1. L’utilisateur apporte des modifications à son référentiel local.
1. Une fois prêt, l’utilisateur valide les modifications dans le référentiel Git distant.

La seule différence est que le référentiel Git distant fait partie de Cloud Manager, qui est transparent pour le développeur.

## Types de programme {#program-types}

Un utilisateur peut créer un programme **de production** ou un programme **sandbox**.

* Un **programme de production** est créé pour activer le trafic en direct pour votre site.
   * Consultez [Présentation des programmes de production](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md) pour plus d’informations.
* Un **programme sandbox** est généralement créé pour les besoins de formation, à des fins de démonstration, d’activation, de preuve de concept ou de documentation.
   * Un environnement sandbox n’est pas destiné à transporter du trafic en direct et comporte des restrictions absentes d’un programme de production.
   * Il comprend Sites, Assets et Edge Delivery Services et est prérempli avec une branche Git contenant un exemple de code, un environnement de développement et un pipeline hors production.
   * Consultez [Présentation des programmes de sandbox](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md) pour plus d’informations.
