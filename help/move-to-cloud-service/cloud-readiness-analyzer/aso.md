---
title: Présentation du système AEM
description: Présentation du système AEM
translation-type: tm+mt
source-git-commit: 3478827949356c4a4f5133b54c6cf809f416efef
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 3%

---


# Présentation du système AEM {#aem-system}

Cette page décrit la présentation du système Adobe Experience Manager (AEM).

## Arrière-plan {#background}

Ce modèle permet d’identifier des informations générales qui fournissent un aperçu du système AEM. Les informations peuvent inclure des éléments tels que :

Version d’AEM Produits AEM utilisés (Sites, Ressources, Formulaires, etc.) Nombre de noeuds (pages, ressources, etc.)

## Données du modèle {#pattern-data}

Les objets suivants sont inclus dans la représentation JSON du modèle :

* **item.message**: fait référence au message du modèle.
* **item.context**: renvoie à des informations supplémentaires sur les informations d’aperçu :
   * *type*: Type de données contextuelles, &quot;aem.version&quot;, &quot;aem.product&quot; ou &quot;node.count&quot;.
   * *data*: Un objet JSON contenant les données correspondant au type : &quot;version&quot; (chaîne), &quot;product&quot; (chaîne) ou &quot;count&quot; (entier).

### Incidences possibles et risques {#possible-implications}

Non applicable.

### Solutions possibles  {#possible-solutions}

Non applicable.
