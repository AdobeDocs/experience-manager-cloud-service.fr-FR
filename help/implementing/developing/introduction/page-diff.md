---
title: Développement et outil de comparaison des pages
description: Découvrez le fonctionnement de l’outil de comparaison des pages et son impact sur un développeur
exl-id: 03c08616-2203-4b90-bed6-4836266e2507
source-git-commit: 7260649eaab303ba5bab55ccbe02395dc8159949
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 30%

---

# Développement et outil de comparaison des pages {#developing-and-page-diff}

## Présentation des fonctionnalités {#feature-overview}

La création de contenu est un processus itératif. Pour être efficace lorsque vous créez du contenu, vous devez pouvoir voir ce qui a changé d’une version à l’autre. L’affichage d’une version de page, puis de l’autre, est inefficace et susceptible d’erreur. Un auteur souhaite pouvoir comparer la page active à une version précédente en même temps que les différences mises en évidence.

L’outil de comparaison des pages permet à l’utilisateur de comparer la page active aux lancements, aux versions précédentes, etc. Pour plus d’informations sur cette fonction utilisateur, voir [Outil de comparaison des pages](/help/sites-cloud/authoring/features/page-diff.md).

## Détails de l’opération {#operation-details}

Lors de la comparaison des versions d’une page, la version précédente que l’utilisateur souhaite comparer est recréée par AEM en arrière-plan afin de faciliter la comparaison. Cette version précédente est nécessaire pour effectuer le rendu du contenu. [pour la comparaison côte à côte](/help/sites-cloud/authoring/features/page-diff.md).

Cette opération de recréation, réalisée par AEM en interne, est transparente pour l’utilisateur et ne nécessite aucune intervention. Cependant, un administrateur qui consulte le référentiel, par exemple en CRXDE Lite, voit ces versions recréées dans la structure de contenu.

Lorsque le contenu est comparé, l’ensemble de l’arborescence jusqu’à la page à comparer est recréé à l’emplacement suivant :

`/tmp/versionhistory/`

Une tâche de nettoyage s’exécute automatiquement pour nettoyer ce contenu temporaire.

## Restrictions {#limitations}

La comparaison côté client se fait par comparaison DOM, ce qui simplifie le processus de comparaison. Cependant, plusieurs limitations doivent être prises en compte par le développeur.

* Cette fonctionnalité utilise des classes CSS qui ne sont pas des espaces de noms du produit AEM. Si d’autres classes CSS personnalisées ou des classes CSS tierces portant le même nom sont incluses sur la page, l’affichage de la comparaison peut être affecté.

   * `html-added`
   * `html-removed`
   * `cq-component-added`
   * `cq-component-removed`
   * `cq-component-moved`
   * `cq-component-changed`

* Étant donné que la comparaison est côté client et s’exécute au chargement de la page, les ajustements apportés au DOM après l’exécution du service de comparaison côté client ne sont pas pris en compte. Ce processus peut affecter les éléments suivants :

   * Composants qui utilisent AJAX pour intégrer du contenu
   * Applications sur une seule page
   * Composants JavaScript qui manipulent le DOM lors de l’interaction de l’utilisateur.
