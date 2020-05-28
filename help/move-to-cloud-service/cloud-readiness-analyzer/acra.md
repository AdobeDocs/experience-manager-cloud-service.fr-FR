---
title: Présentation du système AEM
description: Présentation du système AEM
translation-type: tm+mt
source-git-commit: 3478827949356c4a4f5133b54c6cf809f416efef
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 1%

---


# Présentation du système AEM {#aem-system}

Cette page décrit AEM comme un service Cloud qui fournit de nouvelles fonctionnalités avec une architecture qui représente une amélioration significative par rapport aux versions antérieures d’AEM. La mise à niveau vers cette nouvelle architecture nécessite un effort considérable.

## Description {#background}

Le méta-modèle ACRA est utilisé pour identifier plusieurs problèmes liés aux mises à niveau vers AEM en tant que service Cloud. Il prend en charge plusieurs types d’informations d’alerte par le biais d’une combinaison des valeurs de *référence* du modèle et des valeurs &quot;referméePar&quot; et de son objet *contextuel* . La valeur de *type* de l’objet *context* détermine le problème spécifique qui a été détecté.

On s&#39;attend à ce que les questions de préparation incluses dans le modèle ACRA aient relativement peu de cas à l&#39;origine de l&#39;avis. Il existe d’autres problèmes de préparation liés à AEM en tant que service Cloud qui peuvent présenter de nombreuses instances nécessitant une attention particulière et qui reçoivent leur propre code de modèle. (voir UUI et URS).

## Données du modèle {#pattern-data}

Les objets suivants sont inclus dans la représentation JSON du modèle :

* **item.message**: Type de problème de préparation. (Voir ci-dessous.)
* **data**: Objet JSON contenant les données correspondant au type.

### Incidences possibles et risques {#possible-implications}

à déterminer

### Solutions possibles  {#possible-solutions}

à déterminer
