---
title: Développement et outil de comparaison des pages
description: Comprendre le fonctionnement de la fonction Diff de page et son impact sur un développeur
translation-type: tm+mt
source-git-commit: fee73b5f5ba69422494efe554ac5aa62c046ad86
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 52%

---


# Développement et outil de comparaison des pages {#developing-and-page-diff}

## Présentation des fonctionnalités {#feature-overview}

La création de contenu est un processus itératif. Pour être efficace lorsque vous créez du contenu, vous devez pouvoir voir ce qui a changé d’une version à l’autre. Afficher les versions en alternance est une méthode inefficace avec un fort risque d’erreur. Un auteur souhaite afficher, côte à côte, deux versions d’une page afin de les comparer en mettant les différences en évidence.

L’outil de comparaison des pages permet à un utilisateur de comparer la page active aux lancements, aux versions précédentes, etc. Pour plus d’informations sur cette fonctionnalité utilisateur, voir [Outil de comparaison des pages](/help/sites-cloud/authoring/features/page-diff.md).

## Détails de l&#39;opération {#operation-details}

Lors de la comparaison de versions d’une page, la version précédente que l’utilisateur souhaite comparer est recréée par AEM en arrière-plan afin de faciliter la comparaison. Ceci est nécessaire pour pouvoir générer le contenu [pour une comparaison](/help/sites-cloud/authoring/features/page-diff.md)côte à côte.

Cette opération de loisirs est réalisée par AEM en interne et est transparente pour l&#39;utilisateur et ne nécessite aucune intervention. Cependant, un administrateur qui consulte le référentiel par exemple dans CRX DE Lite voit ces versions recréées dans la structure de contenu.

Lors de la comparaison du contenu, l’arborescence entière jusqu’à la page à comparer est recréée à l’emplacement suivant :

`/tmp/versionhistory/`

Une tâche de nettoyage s’exécute automatiquement pour nettoyer ce contenu temporaire.

## Autorisations {#permissions}

La différence se produit côté client par le biais de la comparaison DOM, ce qui rend le processus de différenciation simple. Cependant, il existe un certain nombre de limitations qui doivent être prises en compte par le développeur.

* Cette fonctionnalité utilise des classes CSS qui ne sont pas placées dans un espace de noms sur le produit AEM. Si d’autres classes CSS personnalisées ou des classes CSS tierces portant le même nom sont incluses sur la page, l’affichage de la comparaison peut s’en trouver affectée.

   * `html-added`
   * `html-removed`
   * `cq-component-added`
   * `cq-component-removed`
   * `cq-component-moved`
   * `cq-component-changed`

* Étant donné que la comparaison s’effectue du côté client et s’exécute au chargement de la page, les réglages apportés au DOM après l’exécution de ce service de comparaison ne sont pas pris en compte. Cela peut avoir une incidence sur éléments suivants :

   * Composants qui utilisent AJAX pour inclure du contenu
   * des applications sur une seule page ;
   * Composants basés sur JavaScript qui manipulent le DOM lors d’une interaction de l’utilisateur
