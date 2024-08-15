---
title: Interdire la sérialisation des ResourceResolvers via l’exporteur de modèle Sling
description: Interdire la sérialisation des ResourceResolvers via l’exporteur de modèle Sling
exl-id: 63972c1e-04bd-4eae-bb65-73361b676687
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 85cef99dc7a8d762d12fd6e1c9bc2aeb3f8c1312
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 5%

---

# Interdire la sérialisation des ResourceResolvers via l’exporteur de modèle Sling {#disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter}

La fonction d’exportateur de modèle Sling permet de sérialiser des objets de modèles Sling au format JSON. Cette fonctionnalité est largement utilisée car elle permet à SPA (applications d’une seule page) d’accéder facilement aux données d’AEM. Du côté de l’implémentation, la bibliothèque Jacson Databind est utilisée pour sérialiser ces objets.

La sérialisation est une opération récursive. À partir d’un &quot;objet racine&quot;, il effectue une itération récursive à travers tous les objets éligibles et les sérialise ainsi que leurs enfants. Vous trouverez une description des champs qui sont sérialisés dans l’article [Jackson - Decide What Fields Get Serialized/Deserialized](https://www.baeldung.com/jackson-field-serializable-deserializable-or-not).

Cette approche sérialise tous les types d’objets dans JSON et peut naturellement également sérialiser un objet Sling `ResourceResolver` s’il est couvert par les règles de sérialisation. Ceci est problématique, car le service `ResourceResolver` (et donc également l’objet de service qui le représente) contient des informations potentiellement sensibles, qui ne doivent pas être divulguées. Par exemple :

* ID utilisateur
* Chemins de recherche pour résoudre les chemins relatifs
* Le `propertyMap`.

`propertyMap` est particulièrement sensible (voir la documentation de l’API de [`getPropertyMap`](https://sling.apache.org/apidocs/sling12/org/apache/sling/api/resource/ResourceResolver.html#getPropertyMap--)), car il s’agit d’une structure de données interne, qui peut être utilisée à de nombreuses fins, par exemple pour mettre en cache des objets qui partagent le même cycle de vie que `ResourceResolver`. La sérialisation de ces données peut entraîner une fuite des détails de mise en oeuvre et avoir un impact sur la sécurité, car les données sont exposées et ne doivent pas être lisibles et accessibles à un utilisateur final. Pour cette raison, `ResourceResolvers` ne doit pas être sérialisé dans JSON.

Adobe prévoit de désactiver la sérialisation de `ResourceResolvers` selon une approche en 2 étapes :

1. À compter de la version 14697 d’AEM as a Cloud Service, chaque fois qu’une AEM `ResourceResolver` est sérialisée, un message d’avertissement s’affiche. Tous les clients sont invités à consulter leurs journaux d’application pour connaître ces instructions de journal et à adapter leur code en conséquence.
1. À un stade ultérieur, l’Adobe désactivera la sérialisation de ResourceResolvers au format JSON.

## Implémentation {#implementation}

Le message WARN est consigné à la fois dans les instances de SDK AEM as a Cloud Service et d’AEM local, et il ressemble à ceci :

```
[127.0.0.1 [1705061734620] GET /content/../page.model.json HTTP/1.1] org.apache.sling.models.jacksonexporter.impl.JacksonExporter A ResourceResolver is serialized with all its private fields containing implementation details you should not disclose. Please review your Sling Model implementation(s) and remove all public accessors to a ResourceResolver.
```

Ce message de journal signifie que pendant le processus de sérialisation de `/content/…/page` dans JSON, un `ResourceResolver` est déjà sérialisé. En demandant `/content/../page.model.json`, vous pouvez vérifier où se trouvent exactement les champs de `ResourceResolver` et les utiliser pour identifier la classe de modèle Sling qui déclenche réellement ce comportement.


>[!NOTE]
>
>AEM composants principaux ont été validés pour ne pas être affectés par ce problème.

## Action requise {#requested-action}

Adobe demande à tous ses clients de vérifier leurs journaux d’application et leurs bases de code pour voir s’ils sont affectés par ce problème, et de modifier l’application personnalisée si nécessaire, afin que ce message d’avertissement ne s’affiche plus.

Dans la plupart des cas, on suppose que ces modifications requises sont directement avancées, car les objets `ResourceResolver` ne sont pas du tout requis dans la sortie JSON, car les informations qu’ils contiennent ne sont normalement pas requises par les applications frontales. Cela signifie que, dans la plupart des cas, il doit suffire d’exclure l’objet `ResourceResolver` de la prise en compte par Jackson (voir les [règles](https://www.baeldung.com/jackson-field-serializable-deserializable-or-not)).

Si un modèle Sling est affecté par ce problème, mais qu’il n’est pas modifié, la désactivation explicite de la sérialisation de l’objet `ResourceResolver` (tel qu’il est exécuté par Adobe comme deuxième étape) applique une modification dans la sortie JSON.
