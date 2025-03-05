---
title: Activation de l’exportateur JSON pour un composant
description: Les composants peuvent être adaptés pour générer l’exportation JSON de leur contenu en fonction d’un framework de modeleur.
exl-id: e9be5c0c-618e-4b56-a365-fcdd185ae808
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 07327f80b23e1e6fdbb3fb49d861221877724d39
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 100%

---

# Activation de l’exportateur JSON pour un composant {#enabling-json-export-for-a-component}

Les composants peuvent être adaptés pour générer l’exportation JSON de leur contenu en fonction d’un framework de modeleur.

## Vue d’ensemble {#overview}

L’exportation JSON est basée sur des [modèles Sling](https://sling.apache.org/documentation/bundles/models.html) et sur le framework d’[exportation des modèles Sling](https://sling.apache.org/documentation/bundles/models.html#exporter-framework-since-130) (lequel s’appuie lui-même sur des [annotations Jackson](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations)).

Cela signifie que le composant doit disposer d’un modèle Sling s’il doit exporter du code JSON. Par conséquent, vous devrez suivre ces deux étapes pour activer l’exportation du code JSON sur n’importe quel composant.

* [Définition d’un modèle Sling pour le composant](#define-a-sling-model-for-the-component)
* [Annotation de l’interface du modèle Sling](#annotate-the-sling-model-interface)

## Définition d’un modèle Sling pour le composant {#define-a-sling-model-for-the-component}

Il faut d’abord définir un modèle Sling pour le composant.

>[!NOTE]
>
>Pour obtenir un exemple d’utilisation des modèles Sling, consultez l’article sur le [développement d’exportateurs de modèles Sling dans AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/develop-sling-model-exporter.html?lang=fr).

La classe de mise en œuvre des modèles Sling doit être annotée comme suit :

```java
@Model(... adapters = {..., ComponentExporter.class})
@Exporter(name = ExporterConstants.SLING_MODEL_EXPORTER_NAME, extensions = ExporterConstants.SLING_MODEL_EXTENSION)
@JsonSerialize(as = MyComponent.class)
```

Cela garantit que votre composant peut être exporté seul, à l’aide du sélecteur `.model` de l’extension `.json`.

En outre, cela indique que la classe de modèles Sling peut être adaptée dans l’interface `ComponentExporter`.

>[!NOTE]
>
>Les annotations Jackson ne sont généralement pas spécifiées au niveau de la classe de modèles Sling, mais plutôt au niveau de l’interface de modèle. Cela permet de s’assurer que l’exportation du code JSON est considéré comme faisant partie de l’API du composant.

>[!NOTE]
>
>Les classes `ExporterConstants` et `ComponentExporter` proviennent du lot `com.adobe.cq.export.json`.

### Utilisation de plusieurs sélecteurs {#multiple-selectors}

Bien qu’il ne s’agisse pas d’un cas d’utilisation standard, il est possible de configurer plusieurs sélecteurs en plus du sélecteur `model`.

```
https://<server>:<port>/content/page.model.selector1.selector2.json
```

Toutefois, dans ce cas, le sélecteur `model` doit être le premier et l’extension doit être `.json`.

## Annotation de l’interface du modèle Sling {#annotate-the-sling-model-interface}

Pour être prise en compte par le framework de l’exportateur JSON, l’interface Modèle doit mettre en œuvre l’interface `ComponentExporter` (ou `ContainerExporter` dans le cas d’un composant de conteneur).

L’interface de modèle Sling correspondante (`MyComponent`) est alors marquée avec les [annotations Jackson](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations) pour définir la manière dont les méthodes doivent être exportées (sérialisées).

L’interface de modèle doit être correctement annotée pour définir les méthodes à sérialiser. Par défaut, toutes les méthodes qui respectent la convention de nommage habituelle pour les méthodes getter sont sérialisées. En outre, leurs noms de propriétés JSON sont naturellement dérivés des noms des méthodes getter. Cela peut être évité en utilisant `@JsonIgnore` ou `@JsonProperty` pour renommer la propriété JSON.

## Exemple {#example}

[Les composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr) prennent en charge l’exportation JSON et peuvent être utilisés comme référence.

Pour obtenir un exemple, consultez la mise en œuvre du modèle Sling sur le composant principal de l’image et son interface annotée.

## Documentation connexe {#related-documentation}

* [Fragments de contenu](/help/sites-cloud/administering/content-fragments/overview.md)
* [Modèles de fragment de contenu](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md)
* [Création à l’aide de fragments de contenu](/help/sites-cloud/authoring/fragments/content-fragments.md)
* [Composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr) et [composant Fragment de contenu](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html?lang=fr)
