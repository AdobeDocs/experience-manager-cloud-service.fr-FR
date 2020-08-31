---
title: Activation de l’exportation JSON pour un composant
description: Les composants peuvent être adaptés pour générer l’exportation JSON de leur contenu en fonction d’une structure de application d’une seule pageeur.
translation-type: tm+mt
source-git-commit: 83c27daae4e8ae2ae6a8f115c9da9527971c6ecb
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 65%

---


# Activation de l’exportateur JSON pour un composant{#enabling-json-export-for-a-component} 

Les composants peuvent être adaptés pour générer l’exportation JSON de leur contenu en fonction d’une structure de application d’une seule pageeur.

## Présentation {#overview}

The JSON Export is based on [Sling Models](https://sling.apache.org/documentation/bundles/models.html), and on the [Sling Model Exporter](https://sling.apache.org/documentation/bundles/models.html#exporter-framework-since-130) framework (which itself relies on [Jackson annotations](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations)).

Cela signifie que le composant doit avoir un modèle Sling pour effectuer une exportation JSON. Par conséquent, vous devez suivre ces deux étapes pour activer l’exportation JSON des composants.

* [Définition d’un modèle Sling pour le composant](#define-a-sling-model-for-the-component)
* [Annotation de l’interface du modèle Sling](#annotate-the-sling-model-interface)

## Définition d’un modèle Sling pour le composant {#define-a-sling-model-for-the-component}

Il faut d’abord définir un modèle Sling pour le composant.

>[!NOTE]
>
>For an example of using Sling Models see the article [Developing Sling Model Exporters in AEM](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/develop-sling-model-exporter.html).

La classe de mise en œuvre des modèles Sling doit être annotée comme suit :

```java
@Model(... adapters = {..., ComponentExporter.class})
@Exporter(name = ExporterConstants.SLING_MODEL_EXPORTER_NAME, extensions = ExporterConstants.SLING_MODEL_EXTENSION)
@JsonSerialize(as = MyComponent.class)
```

This ensures that your component could be exported on its own, using the `.model` selector and the `.json` extension.

In addition, this specifies that the Sling Model class can be adapted into the `ComponentExporter` interface.

>[!NOTE]
>
>Les annotations Jackson ne sont généralement pas spécifiées au niveau de la classe de modèles Sling, mais plutôt au niveau de l’interface de modèle. Cela permet de vérifier que l’exportation JSON est considérée comme faisant partie de l’API du composant.

>[!NOTE]
>
>The `ExporterConstants` and `ComponentExporter` classes come from the `com.adobe.cq.export.json` bundle.

### Utilisation de plusieurs sélecteurs {#multiple-selectors}

Bien qu’il ne s’agisse pas d’un cas d’utilisation standard, il est possible de configurer plusieurs sélecteurs en plus du `model` sélecteur.

```
https://<server>:<port>/content/page.model.selector1.selector2.json
```

Toutefois, dans ce cas, le `model` sélecteur doit être le premier sélecteur et l’extension doit être `.json`indiquée.

## Annotation de l’interface du modèle Sling {#annotate-the-sling-model-interface}

Pour être prise en compte par la structure de l’exportateur JSON, l’interface Modèle doit mettre en œuvre l’interface `ComponentExporter` (ou `ContainerExporter`   dans le cas d’un composant de conteneur).

The corresponding Sling Model interface (`MyComponent`) would be then annotated using [Jackson annotations](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations) to define how it should be exported (serialized).

L’interface de modèle doit être correctement annotée afin de définir les méthodes qui doivent être sérialisées. Par défaut, on attribue un numéro de série à toutes les méthodes qui respectent la convention de dénomination habituelle pour des getters. En outre, leurs noms de propriétés JSON sont naturellement dérivés des noms des getters. This can be prevented or overridden using `@JsonIgnore` or `@JsonProperty` to rename the JSON property.

## Exemple {#example}

[Les composants](https://docs.adobe.com/content/help/fr-FR/experience-manager-core-components/using/introduction.html) principaux prennent en charge l’exportation JSON et peuvent être utilisés comme référence.

Pour obtenir un exemple, consultez la mise en œuvre du modèle Sling sur le composant principal de l’image et son interface annotée.

## Documentation connexe {#related-documentation}

Pour plus d’informations, voir :

* [Fragments de contenu dans le guide de l’utilisateur Ressources](/help/assets/content-fragments/content-fragments.md)
* [Modèles de fragment de contenu](/help/assets/content-fragments/content-fragments-models.md)
* [Création à l’aide de fragments de contenu](/help/sites-cloud/authoring/fundamentals/content-fragments.md)
* [Composants principaux](https://docs.adobe.com/content/help/fr-FR/experience-manager-core-components/using/introduction.html) et [composant Fragment de contenu](https://docs.adobe.com/content/help/fr-FR/experience-manager-core-components/using/components/content-fragment-component.html)
