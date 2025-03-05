---
title: Exportateur JSON pour Content Services
description: AEM Content Services est conçu pour généraliser la description et la diffusion de contenu dans/à partir d’AEM à des canaux autres que des pages web. Il assure la diffusion du contenu aux canaux autres que les pages web AEM classiques, à l’aide de méthodes normalisées qui peuvent être utilisées par tous les clients.
exl-id: d3ddffb7-cef9-4c86-aa31-175f13f9b4a5
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 46b0af152d5f297419e7d1fa372975aded803bc7
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 88%

---

# Exportateur JSON pour Content Services {#json-exporter-for-content-services}

AEM Content Services est conçu pour généraliser la description et la diffusion du contenu dans/depuis AEM, au-delà des pages web.

Il assure la diffusion du contenu aux canaux autres que les pages web AEM classiques, à l’aide de méthodes normalisées qui peuvent être utilisées par tous les clients. Ces canaux peuvent inclure :

* des applications sur une seule page ;
* des applications mobiles natives ;
* D’autres canaux et points de contact externes à AEM.

Comme les fragments de contenu utilisent du contenu structuré, vous pouvez fournir des services de contenu à l’aide de l’exportateur JSON pour diffuser le contenu de toute page AEM au format du modèle de données JSON. Ce contenu peut ensuite être utilisé dans vos propres applications.

## Exportateur JSON avec les composants principaux des fragments de contenu {#json-exporter-with-content-fragment-core-components}

Grâce à l’exportateur JSON AEM, vous pouvez diffuser le contenu des pages AEM au format du modèle de données JSON. Ce contenu peut ensuite être utilisé dans vos propres applications.

Avec AEM, la diffusion s’effectue à l’aide du sélecteur `model` et de l’extension `.json`.

`.model.json`

1. Par exemple, une URL telle que :

   ```shell
   http://localhost:4502/content/wknd/language-masters/en/magazine/guide-la-skateparks.model.json
   ```

1. Diffusera du contenu tel que :

   ![Modèle JSON du contenu WKND](assets/json-model-wknd.png)

Vous pouvez également diffuser le contenu d’un fragment de contenus structuré en le ciblant spécifiquement.

Cette opération s’effectue à l’aide du chemin d’accès complet au fragment (via l’`jcr:content` ) ; par exemple, avec un suffixe tel que :

`.../jcr:content/root/container/container/contentfragment.model.json`

Votre page peut contenir un fragment de contenu unique ou plusieurs composants de différents types. Vous pouvez également utiliser des mécanismes tels que des composants de liste pour rechercher automatiquement du contenu pertinent.

* Par exemple, une URL telle que :

  ```shell
  http://localhost:4502/content/wknd/language-masters/en/magazine/guide-la-skateparks/jcr:content/root/container/container/contentfragment.model.json
  ```

* Diffusera du contenu tel que :

  ![Modèle JSON du fragment de contenu WKND](assets/json-model-wknd-content-fragment.png)

  >[!NOTE]
  >
  >Vous pouvez [adapter vos propres composants](enabling-json-exporter.md) pour accéder à ces données et les utiliser.

  >[!NOTE]
  >
  >Bien qu’il ne s’agisse pas d’une implémentation standard, [plusieurs sélecteurs sont pris en charge](enabling-json-exporter.md#multiple-selectors), mais `model` doivent être les premiers.

### Informations supplémentaires {#further-information}

* API HTTP Assets
   * [API HTTP Assets](/help/assets/developer-reference-material-apis.md)
* Modèles Sling :
   * [Modèles Sling – Association d’une classe de modèles à un type de ressource depuis la version 1.3.0](https://sling.apache.org/documentation/bundles/models.html#associating-a-model-class-with-a-resource-type-since-130)
* AEM avec JSON :
   * [Activation de l’exportateur JSON pour un composant](enabling-json-exporter.md)

## Documentation connexe {#related-documentation}

* [Fragments de contenu](/help/sites-cloud/administering/content-fragments/overview.md)
* [Modèles de fragment de contenu](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md)
* [Création à l’aide de fragments de contenu](/help/sites-cloud/authoring/fragments/content-fragments.md)
* [Composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr) et [composant Fragment de contenu](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html?lang=fr)
