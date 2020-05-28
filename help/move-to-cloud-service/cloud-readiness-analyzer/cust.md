---
title: Personnalisation détectée
description: Personnalisation détectée
translation-type: tm+mt
source-git-commit: 3478827949356c4a4f5133b54c6cf809f416efef
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 3%

---


# Personnalisation détectée {#cust-pattern}

Cette page décrit le code de modèle Personnalisation détectée.

## Arrière-plan {#background}

Ce code de modèle est utilisé pour identifier les personnalisations apportées à l’instance AEM. La personnalisation d’AEM étant courante, ce modèle n’indique pas nécessairement qu’il existe un problème. Il identifie un enregistrement des personnalisations afin qu’elles puissent être évaluées en fonction de leur impact sur les plans de mise à niveau.

Les personnalisations détectées sont les suivantes :

* Code client (packages) et configurations
* Packages tiers
* Intégrations à des services tiers
* Index de chêne non standard

## Données du modèle {#pattern-data}

Les objets suivants sont inclus dans la représentation JSON du modèle :

* **item.message**: fait référence au message du modèle.
* **item.context**: renvoie à des informations supplémentaires sur les informations d’aperçu :
   * *type*: customization.detect.
   * *data*: Un objet JSON contenant les données décrivant la personnalisation

### Incidences possibles et risques {#possible-implications}

Non applicable.

### Solutions possibles  {#possible-solutions}

Non applicable.
