---
title: Appels universels de l’éditeur
description: Découvrez les différents types d’appels effectués sur votre application par l’éditeur universel pour vous aider lors du débogage.
source-git-commit: 16f2922a3745f9eb72f7070c30134e5149eb78ce
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 1%

---


# Appels universels de l’éditeur {#calls}

Découvrez les différents types d’appels effectués sur votre application par l’éditeur universel pour vous aider lors du débogage.

{{universal-editor-status}}

## Vue d’ensemble {#overview}

L’éditeur universel communique avec votre application instrumentée par le biais d’une série d’appels définis. Cela est transparent pour et n’a aucun effet sur l’expérience utilisateur finale.

Toutefois, pour le développeur, la compréhension de ces appels et de ce qu’ils font peut s’avérer utile lors du débogage de votre application lors de l’utilisation d’Universal Editor. Si vous avez instrumenté votre application et qu’elle ne se comporte pas comme prévu, il peut s’avérer utile d’ouvrir la **Réseau** des outils de développement de votre navigateur et examinez les appels lorsque vous modifiez du contenu dans votre application.

![Exemple d’appel de détails sur l’onglet Réseau des outils de développement du navigateur](assets/calls-network-tab.png)

* La variable **Payload** de l’appel contient des détails sur les éléments mis à jour par l’éditeur, y compris l’identification des éléments à mettre à jour et la manière de les mettre à jour.
* La variable **Réponse** inclut des détails sur ce qui a été mis à jour exactement par le service d’éditeur. Cela facilite l’actualisation du contenu dans l’éditeur. Dans certains cas, comme une `move` , la page entière doit être actualisée.

Vous trouverez ci-dessous une liste des types d’appels effectués par l’éditeur universel vers votre application, ainsi que des exemples de payloads et de réponses.

## Mettre à jour {#update}

Un `update` Cet appel se produit lorsque vous modifiez du contenu dans votre application à l’aide d’Universal Editor. La variable `update` conserve les modifications.

Sa charge utile inclut des détails sur les éléments à écrire dans le JCR.

* `itemid`: chemin JCR à mettre à jour
* `itemprop`: propriété JCR mise à jour
* `itemtype`: type de valeur JCR de la propriété mise à jour.
* `value`: données mises à jour

### Exemple de charge utile {#update-payload}

```json
{
  "op": "patch",
  "connections": {
    "aem": "aem:https://author-pXXXX-eYYYYY.adobeaemcloud.com"
  },
  "path": {
    "itemid": "urn:aem:/content/wknd/language-masters/en/jcr:content/root/container/carousel/item_1571954853062",
    "itemtype": "text",
    "itemprop": "jcr:title"
  },
  "value": "Tiny Toon Adventures"
}
```

### Exemple de réponse {#update-response}

```json
{
  "updates": [
    {
      "itemid": "urn:aem:/content/wknd/language-masters/en/jcr:content/root/container/carousel/item_1571954853062",
      "itemprop": "jcr:title",
      "itemtype": "text"
    }
  ]
}
```

## Détails {#details}

A `details` survient lors du chargement de votre application dans l’éditeur universel pour récupérer le contenu de l’application.

Sa charge utile inclut les données à générer ainsi que des détails sur ce que représentent les données (le schéma) afin qu’elles puissent être rendues dans l’éditeur universel.

* Pour un composant, l’éditeur universel récupère uniquement une `data` , puisque le schéma des données est défini dans l’application.
* Pour les fragments de contenu, l’éditeur universel récupère également une `schema` car le modèle de fragment de contenu est défini dans le JCR.

### Exemple de charge utile {#details-payload}

```json
{
  "op": "patch",
  "connections": {
    "aem": "aem:https://author-pXXXX-eYYYYY.adobeaemcloud.com"
  },
  "path": {
    "itemid": "urn:aem:/content/wknd/language-masters/en/jcr:content/root/container/carousel/item_1571954853062",
    "itemtype": "component",
    "itemprop": ""
  }
}
```

### Exemple de réponse {#details-response}

```json
{
  "data": {
    "jcr:primaryType": "nt:unstructured",
    "jcr:title": "Tiny Toon Adventures!",
    "fileReference": "/content/dam/wknd-shared/en/adventures/riverside-camping-australia/adobestock-216674449.jpeg",
    "cq:panelTitle": "WKND Adventures",
    "actionsEnabled": "true",
    "jcr:lastModifiedBy": "admin",
    "titleFromPage": "false",
    "jcr:description": "<p>With WKND Adventures, you don't just see the world you experinece it.</p>",
    "jcr:lastModified": "Wed Jan 03 2024 09:06:05 GMT+0100",
    "descriptionFromPage": "true",
    "sling:resourceType": "wknd/components/teaser",
    "textIsRich": "true",
    "cq:styleIds": [
      "1555543212672"
    ],
    "actions": {
      "jcr:primaryType": "nt:unstructured",
      "item0": {
        "jcr:primaryType": "nt:unstructured",
        "link": "/content/wknd/language-masters/en/adventures",
        "text": "View Trips"
      }
    }
  }
}
```

## Ajouter {#add}

Un `add` Cet appel se produit lorsque vous placez un nouveau composant dans votre application à l’aide d’Universal Editor.

Sa payload comprend une `path` contenant l’emplacement d’ajout du contenu.

Elle comprend également une `content` avec des objets supplémentaires pour les détails spécifiques au point de fin du contenu à stocker. [pour chaque module externe.](/help/implementing/universal-editor/architecture.md) Par exemple, si votre application est basée sur le contenu d’AEM et de Magento, la payload contiendra un objet de données pour chaque système.

### Exemple de charge utile {#add-payload}

```json
{
  "op": "patch",
  "connections": {
    "aemconnection": "aem:https://author-pXXXX-eYYYYY.adobeaemcloud.com"
  },
  "path": {
    "container": {
      "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "itemtype": "container",
      "itemprop": ""
    }
  },
  "content": {
    "name": "text",
    "aem": {
      "page": {
        "resourceType": "wknd/components/text",
        "template": {
          "text": "Default Text"
        }
      }
    }
  }
}
```

### Exemple de réponse {#add-response}

```json
{
  "updates": [
    {
      "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "itemtype": "container"
    }
  ]
}
```

## Déplacer {#move}

A `move` Cet appel se produit lorsque vous déplacez un composant dans votre application à l’aide d’Universal Editor.

Sa payload comprend une `from` définissant l’emplacement du composant et un `to` définissant l’emplacement de déplacement.

### Exemple de charge utile {#move-payload}

```json
{
  "op": "patch",
  "connections": {
    "aemconnection": "aem:https://author-pXXXX-eYYYYY.adobeaemcloud.com"
  },
  "from": {
    "container": {
      "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "itemtype": "container",
      "itemprop": ""
    },
    "component": {
      "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_1068508321",
      "itemtype": "text",
      "itemprop": "text"
    }
  },
  "to": {
    "container": {
      "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "itemtype": "container",
      "itemprop": ""
    },
    "before": {
      "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_2063168902",
      "itemtype": "text",
      "itemprop": "text"
    }
  }
}
```

### Exemple de réponse {#move-response}

```json
{
  "updates": [
    {
      "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "itemtype": "container"
    }
  ]
}
```

## Supprimez {#remove}

A `remove` Cet appel se produit lorsque vous supprimez un composant dans votre application à l’aide d’Universal Editor.

Sa charge utile inclut le chemin d’accès de l’objet qui est supprimé.

### Exemple de charge utile {#remove-payload}

```json
{
  "op": "patch",
  "connections": {
    "aemconnection": "aem:https://author-pXXXX-eYYYYY.adobeaemcloud.com"
  },
  "path": {
    "component": {
      "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_1068508321",
      "itemtype": "text",
      "itemprop": "text"
    },
    "container": {
      "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "itemtype": "container",
      "itemprop": ""
    }
  }
}
```

### Exemple de réponse {#remove-response}

```json
{
  "updates": [
    {
      "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "itemprop": "",
      "itemtype": "container"
    }
  ]
}
```

## Correctif {#patch}

A `patch` Cet appel se produit lorsque vous mettez à jour le contenu dans une boîte de dialogue de votre application. Cela met à jour le contenu de la page de l’application sous forme de correctif JSON vers le contenu existant.

Sa charge utile inclut le chemin d’accès au contenu sur la page ainsi que le correctif JSON de la modification à effectuer.

### Exemple de charge utile {#patch-payload}

```json
{
  "op": "patch",
  "connections": {
    "aemconnection": "aem:https://author-pXXXX-eYYYYY.adobeaemcloud.com"
  },
  "path": {
    "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_1540979193",
    "itemtype": "text",
    "itemprop": "text"
  },
  "patch": [
    {
      "op": "replace",
      "path": "/text",
      "value": "Still More WKND Adventures"
    }
  ]
}
```

### Exemple de réponse {#patch-response}

```json
{
  "updates": [
    {
      "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_1540979193"
    }
  ]
}
```

## Publier {#publish}

A `publish` survient lorsque vous cliquez sur le bouton **Publier** dans l’éditeur universel pour publier le contenu que vous avez modifié.

L’éditeur universel effectue une itération sur le contenu et génère une liste de références qui doit également être publiée.

### Exemple de charge utile {#publish-payload}

```json
{
  "op": "patch",
  "connections": {
    "aemconnection": "aem:https://author-pXXXX-eYYYYY.adobeaemcloud.com"
  },
  "references": [
    "urn:aemconnection:/content/dam/wknd-shared/en/magazine/arctic-surfing/aloha-spirits-in-northern-norway/jcr:content/data/master",
    "urn:aemconnection:/content/wknd/us/en/adventures/jcr:content/root/container/container/title",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/bali-surf-camp/bali-surf-camp/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/climbing-new-zealand/climbing-new-zealand/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/cycling-southern-utah/cycling-southern-utah/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/cycling-tuscany/cycling-tuscany/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/downhill-skiing-wyoming/downhill-skiing-wyoming/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/napa-wine-tasting/napa-wine-tasting/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/riverside-camping-australia/riverside-camping-australia/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/ski-touring-mont-blanc/ski-touring-mont-blanc/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/surf-camp-in-costa-rica/surf-camp-costa-rica/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/tahoe-skiing/tahoe-skiing/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/west-coast-cycling/west-coast-cycling/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/yosemite-backpacking/yosemite-backpacking/jcr:content/data/master",
    "urn:aemconnection:/content/wknd/us/en/newsletter/jcr:content/root/container/title",
    "urn:aemconnection:/content/wknd/us/en/newsletter/jcr:content/root/container/text",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/title",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/image",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/image_2123678383",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_1668104604",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/image_229050934",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/image_275525847",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_358189229",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_2063168902",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_1540979193"
  ]
}
```

### Exemple de réponse {#publish-response}

```json
{
  "publishes": [
    "/content/dam/wknd-shared/en/magazine/arctic-surfing/aloha-spirits-in-northern-norway",
    "/content/wknd/us/en/adventures",
    "/content/dam/wknd-shared/en/adventures/bali-surf-camp/bali-surf-camp",
    "/content/dam/wknd-shared/en/adventures/climbing-new-zealand/climbing-new-zealand",
    "/content/dam/wknd-shared/en/adventures/cycling-southern-utah/cycling-southern-utah",
    "/content/dam/wknd-shared/en/adventures/cycling-tuscany/cycling-tuscany",
    "/content/dam/wknd-shared/en/adventures/downhill-skiing-wyoming/downhill-skiing-wyoming",
    "/content/dam/wknd-shared/en/adventures/napa-wine-tasting/napa-wine-tasting",
    "/content/dam/wknd-shared/en/adventures/riverside-camping-australia/riverside-camping-australia",
    "/content/dam/wknd-shared/en/adventures/ski-touring-mont-blanc/ski-touring-mont-blanc",
    "/content/dam/wknd-shared/en/adventures/surf-camp-in-costa-rica/surf-camp-costa-rica",
    "/content/dam/wknd-shared/en/adventures/tahoe-skiing/tahoe-skiing",
    "/content/dam/wknd-shared/en/adventures/west-coast-cycling/west-coast-cycling",
    "/content/dam/wknd-shared/en/adventures/yosemite-backpacking/yosemite-backpacking",
    "/content/wknd/us/en/newsletter",
    "/content/wknd/language-masters/en/universal-editor-container"
  ]
}
```
