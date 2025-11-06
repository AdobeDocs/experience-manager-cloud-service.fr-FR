---
title: Interdire la sérialisation des ResourceResolvers via l’exporteur de modèle Sling
description: Interdire la sérialisation des ResourceResolvers via l’exporteur de modèle Sling
exl-id: 63972c1e-04bd-4eae-bb65-73361b676687
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 6%

---

# Interdire la sérialisation des ResourceResolvers via l’exporteur de modèle Sling {#disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter}

La fonctionnalité d’exporteur de modèle Sling permet de sérialiser les objets de modèle Sling au format JSON. Cette fonctionnalité est largement utilisée, car elle permet aux SPA (applications d’une seule page) d’accéder facilement aux données d’AEM. Du côté de l’implémentation, la bibliothèque Jackson Databind est utilisée pour sérialiser ces objets.

La sérialisation est une opération récursive. À partir d’un « objet racine », il effectue une itération récursive sur tous les objets éligibles et les sérialise ainsi que leurs enfants. Vous trouverez une description des champs sérialisés dans l’article [Jackson - Choix des champs sérialisés/désérialisés](https://www.baeldung.com/jackson-field-serializable-deserializable-or-not).

Cette approche sérialise tous les types d’objets dans JSON. Naturellement, il peut également sérialiser un objet `ResourceResolver` Sling, s’il est couvert par les règles de sérialisation. Cela pose problème, car le service `ResourceResolver` (et donc également l’objet de service qui le représente) contient des informations potentiellement sensibles qui ne doivent pas être divulguées. Par exemple :

* L’identifiant utilisateur
* Les chemins de recherche pour résoudre les chemins relatifs
* La `propertyMap`

La `propertyMap` est particulièrement sensible (voir la documentation de l’API de [`getPropertyMap`](https://sling.apache.org/apidocs/sling12/org/apache/sling/api/resource/ResourceResolver.html#getPropertyMap--)), car il s’agit d’une structure de données interne, qui peut être utilisée à de nombreuses fins, par exemple pour mettre en cache des objets qui partagent le même cycle de vie que la `ResourceResolver`. La sérialisation de ces éléments peut faire fuiter les détails d’implémentation et avoir un impact potentiel sur la sécurité, car les données exposées ne doivent pas être lisibles et accessibles à un utilisateur final. Pour cette raison, `ResourceResolvers` ne doit pas être sérialisé en JSON.

Adobe prévoit de désactiver la sérialisation des `ResourceResolvers` selon une approche en deux étapes :

1. À partir des 14697 de mise à jour d’AEM as a Cloud Service, chaque fois qu’un `ResourceResolver` est sérialisé, AEM consigne un message d’avertissement. Nous recommandons à tous les clients de vérifier leurs journaux d’application pour trouver ces instructions de journal et d’adapter leur base de code en conséquence.
1. Ultérieurement, Adobe désactivera la sérialisation de `ResourceResolver` en tant que JSON.

## Implémentation {#implementation}

Le message AVERTISSEMENT est consigné à la fois dans les instances AEM as a Cloud Service et AEM SDK locales et ressemble à ceci :

```text
[127.0.0.1 [1705061734620] GET /content/../page.model.json HTTP/1.1] org.apache.sling.models.jacksonexporter.impl.JacksonExporter A ResourceResolver is serialized with all its private fields containing implementation details you should not disclose. Please review your Sling Model implementation(s) and remove all public accessors to a ResourceResolver.
```

Ce message du journal signifie que pendant le processus de sérialisation du `/content/…/page` dans JSON, un `ResourceResolver` est déjà sérialisé. En demandant des `/content/../page.model.json`, vous pouvez vérifier où exactement les champs du `ResourceResolver` s’affichent et les utiliser pour identifier la classe de modèle Sling qui déclenche réellement ce comportement.


>[!NOTE]
>
>Il a été validé que les [composants principaux d’AEM](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/introduction) ne sont pas affectés par ce problème.

## Action demandée {#requested-action}

Adobe demande à tous les clients de vérifier leurs journaux d’application et leurs bases de code pour voir s’ils sont affectés par ce problème, et de modifier l’application personnalisée si nécessaire, de sorte que ce message d’avertissement ne s’affiche plus dans les journaux.

On suppose que, dans la plupart des cas, ces changements nécessaires sont simples. Les objets `ResourceResolver` ne sont pas du tout requis dans la sortie JSON, puisque les informations qu’ils contiennent ne sont normalement pas requises par les applications frontales, ce qui signifie que dans la plupart des cas, il devrait suffire d’exclure l’objet `ResourceResolver` de sa prise en compte par Jackson (consultez les [règles](https://www.baeldung.com/jackson-field-serializable-deserializable-or-not)).

Si un modèle Sling est affecté par ce problème, mais n’est pas modifié, la désactivation explicite de la sérialisation de l’objet `ResourceResolver` (telle qu’exécutée par Adobe lors de la deuxième étape) impose une modification de la sortie JSON.
