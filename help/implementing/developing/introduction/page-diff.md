---
title: Développement et outil de comparaison des pages
description: Découvrez le fonctionnement de l’outil de comparaison des pages et son impact sur un développeur
exl-id: 03c08616-2203-4b90-bed6-4836266e2507
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 93%

---

# Développement et outil de comparaison des pages {#developing-and-page-diff}

## Présentation des fonctionnalités {#feature-overview}

La création de contenu est un processus itératif. Pour être efficace lorsque vous créez du contenu, vous devez pouvoir voir ce qui a changé d’une version à l’autre. L’affichage d’une version de page, puis de l’autre, est inefficace et source d’erreurs. Les personnes qui créent du contenu doivent pouvoir comparer la page active à une version précédente en même temps que les différences mises en évidence.

L’outil de comparaison des pages permet de comparer la page active aux lancements, versions précédentes, etc. Pour plus d’informations sur cette fonctionnalité utilisateur, voir [Outil de comparaison des pages](/help/sites-cloud/authoring/sites-console/page-diff.md).

## Détails de l’opération {#operation-details}

Lors de la comparaison des versions d’une page, la version précédente à comparer est recréée en arrière-plan par AEM pour faciliter la comparaison. Cette version précédente est nécessaire pour rendre le contenu [pour la comparaison côte à côte](/help/sites-cloud/authoring/sites-console/page-diff.md).

Cette opération de recréation, réalisée par AEM en interne, est transparente pour l’utilisateur ou l’utilisatrice et ne nécessite aucune intervention. Cependant, un administrateur qui consulte le référentiel, par exemple dans CRXDE Lite, verra ces versions recréées dans la structure de contenu.

Lorsque le contenu est comparé, l’ensemble de l’arborescence jusqu’à la page à comparer est recréé à l’emplacement suivant :

`/tmp/versionhistory/`

Une tâche de nettoyage s’exécute automatiquement pour nettoyer ce contenu temporaire.

## Restrictions {#limitations}

La comparaison côté client se fait par comparaison DOM, ce qui simplifie le processus de comparaison. Cependant, plusieurs limites doivent être prises en compte par le développeur ou la développeuse.

* Cette fonctionnalité utilise des classes CSS qui ne sont pas placées dans un espace de noms sur le produit AEM. Si d’autres classes CSS personnalisées ou des classes CSS tierces portant le même nom sont incluses sur la page, l’affichage de la comparaison peut s’en trouver affecté.

   * `html-added`
   * `html-removed`
   * `cq-component-added`
   * `cq-component-removed`
   * `cq-component-moved`
   * `cq-component-changed`

* Étant donné que la comparaison se trouve côté client et s’exécute au chargement de la page, les ajustements apportés au DOM après l’exécution du service de comparaison côté client ne sont pas pris en compte. Ce processus peut avoir une incidence sur les éléments suivants :

   * Composants qui utilisent AJAX pour intégrer du contenu
   * Applications sur une seule page
   * Composants JavaScript qui manipulent le DOM lors de l’interaction de l’utilisateur ou l’utilisatrice.
