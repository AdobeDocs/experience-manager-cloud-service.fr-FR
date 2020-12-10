---
title: Exportateur JSON pour Content Services
description: AEM Content Services est conçu pour généraliser la description et la diffusion de contenu dans/à partir d’AEM à des canaux autres que des pages web. Il assure la diffusion du contenu aux canaux autres que les pages web AEM classiques, à l’aide de méthodes normalisées qui peuvent être utilisées par tous les clients.
translation-type: tm+mt
source-git-commit: 0799a817095558edd49b53ddc915c9474181fef7
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 100%

---


# Exportateur JSON pour Content Services  {#json-exporter-for-content-services}

AEM Content Services est conçu pour généraliser la description et la diffusion du contenu dans/depuis AEM, au-delà des pages web.

Il assure la diffusion du contenu aux canaux autres que les pages web AEM classiques, à l’aide de méthodes normalisées qui peuvent être utilisées par tous les clients. Ces canaux peuvent inclure :

* des applications sur une seule page ;
* des applications mobiles natives ;
* D’autres canaux et points de contact externes à AEM.

Comme les fragments de contenu utilisent du contenu structuré, vous pouvez fournir des services de contenu à l’aide de l’exportateur JSON pour diffuser le contenu de toute page AEM au format du modèle de données JSON. Ce contenu peut ensuite être utilisé dans vos propres applications.

## Exportateur JSON avec les composants principaux des fragments de contenu  {#json-exporter-with-content-fragment-core-components}

Grâce à l’exportateur JSON AEM, vous pouvez diffuser le contenu des pages AEM au format du modèle de données JSON. Ce contenu peut ensuite être utilisé dans vos propres applications.

Avec AEM, la diffusion s’effectue à l’aide du sélecteur `model` et de l’extension `.json`.

`.model.json`

1. Par exemple, une adresse URL comme :

   ```shell
   http://localhost:4502/content/wknd/language-masters/en/magazine/guide-la-skateparks.model.json
   ```

1. diffusera du contenu comme :

   ![Modèle JSON du contenu WKND](assets/json-model-wknd.png)

Vous pouvez également diffuser le contenu d’un fragment de contenus structuré en le ciblant spécifiquement.

Pour ce faire, utilisez le chemin du fragment dans son intégralité (via `jcr:content`), par exemple avec un suffixe comme :

`.../jcr:content/root/container/container/contentfragment.model.json`

Votre page peut contenir un fragment de contenu unique ou plusieurs composants de différents types. Vous pouvez également utiliser des mécanismes tels que des composants de liste pour rechercher automatiquement du contenu pertinent.

* Par exemple, une adresse URL comme :

   ```shell
   http://localhost:4502/content/wknd/language-masters/en/magazine/guide-la-skateparks/jcr:content/root/container/container/contentfragment.model.json
   ```

* diffusera du contenu comme :

   ![Modèle JSON du fragment de contenu WKND](assets/json-model-wknd-content-fragment.png)

   >[!NOTE]
   >
   >Vous pouvez [adapter vos propres composants](enabling-json-exporter.md) pour accéder à ces données et les utiliser.

   >[!NOTE]
   >
   >Bien qu’il ne s’agisse pas d’une implémentation standard, [plusieurs sélecteurs sont pris en charge,](enabling-json-exporter.md#multiple-selectors) mais `model` doit être le premier.

### Informations supplémentaires {#further-information}

Voir également :

* API HTTP Assets
   * [API HTTP Assets](/help/assets/developer-reference-material-apis.md)
* Modèles Sling :
   * [Modèles Sling - Association d’une classe de modèles à un type de ressource depuis la version 1.3.0](https://sling.apache.org/documentation/bundles/models.html#associating-a-model-class-with-a-resource-type-since-130)
* AEM avec JSON :
   * [Activation de l’exportateur JSON pour un composant](enabling-json-exporter.md)

## Documentation connexe {#related-documentation}

Pour plus d’informations, voir :

* [Fragments de contenu dans le guide de l’utilisateur d’Assets](/help/assets/content-fragments/content-fragments.md)
* [Modèles de fragment de contenu](/help/assets/content-fragments/content-fragments-models.md)
* [Création à l’aide de fragments de contenu](/help/sites-cloud/authoring/fundamentals/content-fragments.md)
* [Composants principaux](https://docs.adobe.com/content/help/fr-FR/experience-manager-core-components/using/introduction.html) et [composant Fragment de contenu](https://docs.adobe.com/content/help/fr-FR/experience-manager-core-components/using/components/content-fragment-component.html)
