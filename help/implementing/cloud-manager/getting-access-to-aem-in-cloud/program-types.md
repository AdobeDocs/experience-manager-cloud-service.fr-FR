---
title: Programmes et types de programmes
description: Découvrez la hiérarchie de Cloud Manager et comment les différents types de programmes s’intègrent dans sa structure et en quoi ils diffèrent.
exl-id: 507df619-a5b5-419a-9e38-db77541425a2
source-git-commit: 74e17ccb93c97dd6881c9b63d9a2d784d3add430
workflow-type: ht
source-wordcount: '533'
ht-degree: 100%

---


# Programmes et types de programmes {#understanding-programs}

Cloud Manager repose sur une hiérarchie d’entités. Les détails ne sont pas essentiels à votre travail au quotidien dans Cloud Manager, mais un aperçu vous aidera à comprendre les programmes et à configurer vos propres programmes.

![Hiérarchie de Cloud Manager](assets/program-types1.png)

* **CLIENT** - Il s’agit du haut de la hiérarchie. Chaque client est configuré avec un identifiant client.
* **PROGRAMMES** - Chaque client possède un ou plusieurs programmes, [qui reflètent souvent les solutions sous licence du client.](introduction-production-programs.md)
* **ENVIRONNEMENTS** - Chaque programme comporte plusieurs environnements, tels que la production pour le contenu en direct, un pour l’évaluation et un à des fins de développement.
   * Chaque programme ne peut avoir qu’un seul environnement de production, mais plusieurs environnements hors production.
* **RÉFÉRENTIEL** - Les programmes disposent de référentiels Git dans lesquels l’application et le code front-end sont conservés pour les environnements.
* **OUTILS ET WORKFLOWS** - Les pipelines gèrent le déploiement du code des référentiels vers les environnements, tandis que d’autres outils permettent d’accéder aux journaux, à la surveillance et à la gestion de l’environnement.

Un exemple est souvent utile pour contextualiser cette hiérarchie.

* Les entreprises de voyage et d’aventure WKND peuvent être un **client** qui se concentre sur les médias liés aux voyages.
* Le client Entreprises de voyage et d’aventure WKND peut avoir deux **programmes** : un programme Sites pour le magazine WKND et un programme Assets pour les médias WKND.
* Les programmes pour le magazine WKND et les médias WKND auraient tous les deux des **environnements** de développement, d’évaluation et de production.

## Référentiel de code source {#source-code-repository}

Un programme Cloud Manager est fourni avec son propre référentiel Git.

Pour accéder au référentiel Git de Cloud Manager, les utilisateurs doivent utiliser un client Git avec un outil de ligne de commande, un client Git visuel autonome ou l’IDE choisi par l’utilisateur tel qu’Eclipse, IntelliJ ou NetBeans.

Une fois le client Git configuré, vous pouvez gérer votre référentiel Git à partir de l’interface utilisateur de Cloud Manager. Pour en savoir plus sur la gestion de Git à l’aide de l’interface utilisateur de Cloud Manager, consultez le document [Accès à Git.](/help/implementing/cloud-manager/managing-code/accessing-repos.md)

Pour commencer à développer l’application AEM Cloud, une copie locale du code de l’application doit être effectuée en l’extrayant du référentiel Cloud Manager vers un emplacement de votre ordinateur local.

```java
$ git clone {URL}
```

Le workflow est donc un workflow Git standard.

1. Un utilisateur clone une copie locale du référentiel Git.
1. L’utilisateur apporte des modifications au référentiel de code local.
1. Une fois prêt, l’utilisateur valide les modifications dans le référentiel Git distant.

La seule différence réside dans le fait que le référentiel Git distant fait partie de Cloud Manager, qui est transparent pour le développeur.

## Types de programme {#program-types}

Un utilisateur peut créer un programme de **production** ou un programme **Sandbox**.

* Un **programme de production** est créé pour activer le trafic en direct pour votre site.
   * Veuillez consulter le document [Présentation des programmes de production](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md) pour plus d’informations.
* Un **programme Sandbox** est généralement créé pour les besoins de formation, à des fins de démonstration, d’activation, de preuve de concept ou de documentation.
   * Un environnement Sandbox n’est pas destiné à gérer un trafic en direct et comportera des restrictions absentes d’un programme de production.
   * Ils incluront Sites et Assets et seront pourvus automatiquement d’une branche Git comprenant un exemple de code, un environnement de développement et un pipeline hors production.
   * Veuillez consulter le document [Présentation des programmes Sandbox](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md) pour plus d’informations.
