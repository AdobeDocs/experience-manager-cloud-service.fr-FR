---
title: Appels de l’éditeur universel
description: Découvrez les différents types d’appels effectués sur votre application par l’éditeur universel pour vous aider lors du débogage.
exl-id: 00d66e59-e445-4b5c-a5b1-c0a9f032ebd9
source-git-commit: 11a244b7dd4810fbfec92b3effc362102e7322dc
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 2%

---


# Appels de l’éditeur universel {#calls}

Découvrez les différents types d’appels effectués sur votre application par l’éditeur universel pour vous aider lors du débogage.

## Vue d’ensemble {#overview}

L’éditeur universel communique avec votre application instrumentée par le biais d’une série d’appels définis. Cela est transparent pour et n’a aucun effet sur l’expérience utilisateur finale.

Toutefois, pour le développeur, la compréhension de ces appels et de ce qu’ils font peut s’avérer utile lors du débogage de votre application lors de l’utilisation d’Universal Editor. Si vous avez instrumenté votre application et qu’elle ne se comporte pas comme prévu, il peut s’avérer utile d’ouvrir la **Réseau** des outils de développement de votre navigateur et examinez les appels lorsque vous modifiez du contenu dans votre application.

![Exemple d’appel de détails sur l’onglet Réseau des outils de développement du navigateur](assets/calls-network-tab.png)

* La variable **Payload** de l’appel contient des détails sur les éléments mis à jour par l’éditeur, y compris l’identification des éléments à mettre à jour et la manière de les mettre à jour.
* La variable **Réponse** inclut des détails sur ce qui a été mis à jour exactement par le service d’éditeur. Cela facilite l’actualisation du contenu dans l’éditeur. Dans certains cas, comme une `move` , la page entière doit être actualisée.

Une fois qu’un appel est terminé avec succès, les événements sont déclenchés et incluent la charge utile de la requête et de la réponse, qui peut être personnalisée pour votre propre application. Consultez le document [Événements d’éditeur universels](/help/implementing/universal-editor/events.md) pour plus d’informations.

Vous trouverez ci-dessous une liste des types d’appels effectués par l’éditeur universel vers votre application, ainsi que des exemples de payloads et de réponses.

## Mettre à jour {#update}

Un `update` Cet appel se produit lorsque vous modifiez du contenu dans votre application à l’aide d’Universal Editor. La variable `update` conserve les modifications.

Sa charge utile inclut des détails sur les éléments à écrire dans le JCR.

* `resource`: chemin JCR à mettre à jour
* `prop`: propriété JCR mise à jour
* `type`: type de valeur JCR de la propriété mise à jour.
* `value`: données mises à jour

>[!BEGINTABS]

>[!TAB Exemple de charge utile]

```json
{
  "connections": [
    {
      "name": "aem",
      "protocol": "aem",
      "uri": "https://localhost:8443"
    }
  ],
  "target": {
    "resource": "urn:aem:/content/wknd/language-masters/en/jcr:content/root/container/carousel/item_1571954853062",
    "type": "text",
    "prop": "jcr:title"
  },
  "value": "Tiny Toon Adventures"
}
```

>[!TAB Exemple de réponse]

```json
{
  "updates": [
    {
      "resource": "urn:aem:/content/wknd/language-masters/en/jcr:content/root/container/carousel/item_1571954853062",
      "prop": "jcr:title",
      "type": "text"
    }
  ]
}
```

>[!ENDTABS]

## Détails {#details}

A `details` survient lors du chargement de votre application dans l’éditeur universel pour récupérer le contenu de l’application.

Sa charge utile inclut les données à générer ainsi que des détails sur ce que représentent les données (le schéma) afin qu’elles puissent être rendues dans l’éditeur universel.

* Pour un composant, l’éditeur universel récupère uniquement une `data` , puisque le schéma des données est défini dans l’application.
* Pour les fragments de contenu, l’éditeur universel récupère également une `schema` car le modèle de fragment de contenu est défini dans le JCR.

>[!BEGINTABS]

>[!TAB Exemple de charge utile]

```json
{
  "connections": [
    {
      "name": "aem",
      "protocol": "aem",
      "uri": "https://localhost:8443"
    }
  ],
  "target": {
    "resource": "urn:aem:/content/wknd/language-masters/en/jcr:content/root/container/carousel/item_1571954853062",
    "type": "component",
    "prop": ""
  }
}
```

>[!TAB Exemple de réponse]

```json
{
  "data": {
    "jcr:primaryType": "nt:unstructured",
    "jcr:title": "Tiny Toon Adventures",
    "fileReference": "/content/dam/wknd-shared/en/adventures/riverside-camping-australia/adobestock-216674449.jpeg",
    "cq:panelTitle": "WKND Adventures",
    "actionsEnabled": "true",
    "jcr:lastModifiedBy": "admin",
    "titleFromPage": "false",
    "jcr:description": "<p>With WKND Adventures, you don't just see the world you experinece it.</p>\r\n",
    "jcr:lastModified": "Fri Jan 19 2024 11:05:59 GMT+0100",
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

>[!ENDTABS]

## Ajouter {#add}

Un `add` Cet appel se produit lorsque vous placez un nouveau composant dans votre application à l’aide d’Universal Editor.

Sa payload comprend une `path` contenant l’emplacement d’ajout du contenu.

Elle comprend également une `content` avec des objets supplémentaires pour les détails spécifiques au point de fin du contenu à stocker. [pour chaque module externe.](/help/implementing/universal-editor/architecture.md) Par exemple, si votre application est basée sur le contenu d’AEM et de Magento, la payload contiendra un objet de données pour chaque système.

>[!BEGINTABS]

>[!TAB Exemple de charge utile]

```json
{
  "connections": [
    {
      "name": "aemconnection",
      "protocol": "aem",
      "uri": "https://author-pXXXX-eYYYYY.adobeaemcloud.com"
    }
  ],
  "target": {
    "container": {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "type": "container",
      "prop": ""
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

>[!TAB Exemple de réponse]

```json
{
  "updates": [
    {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "type": "container"
    }
  ],
  "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_1138559521"
}
```

>[!ENDTABS]

## Déplacer {#move}

A `move` Cet appel se produit lorsque vous déplacez un composant dans votre application à l’aide d’Universal Editor.

Sa payload comprend une `from` définissant l’emplacement du composant et un `to` définissant l’emplacement de déplacement.

>[!BEGINTABS]

>[!TAB Exemple de charge utile]

```json
{
  "connections": [
    {
      "name": "aemconnection",
      "protocol": "aem",
      "uri": "https://author-pXXXX-eYYYYY.adobeaemcloud.com"
    }
  ],
  "from": {
    "container": {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "type": "container",
      "prop": ""
    },
    "component": {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/image_275525847",
      "type": "media",
      "prop": "fileReference"
    }
  },
  "to": {
    "container": {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "type": "container",
      "prop": ""
    }
  }
}
```

>[!TAB Exemple de réponse]

```json
{
  "updates": [
    {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "type": "container"
    }
  ]
}
```

>[!ENDTABS]

## Supprimez {#remove}

A `remove` Cet appel se produit lorsque vous supprimez un composant dans votre application à l’aide d’Universal Editor.

Sa charge utile inclut le chemin d’accès de l’objet qui est supprimé.

>[!BEGINTABS]

>[!TAB Exemple de charge utile]

```json
{
  "connections": [
    {
      "name": "aemconnection",
      "protocol": "aem",
      "uri": "https://author-pXXXX-eYYYYY.adobeaemcloud.com"
    }
  ],
  "target": {
    "component": {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_593170193",
      "type": "text",
      "prop": "text"
    },
    "container": {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "type": "container",
      "prop": ""
    }
  }
}
```

>[!TAB Exemple de réponse]

```json
{
  "updates": [
    {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "prop": "",
      "type": "container"
    }
  ]
}
```

>[!ENDTABS]

## Publier {#publish}

A `publish` survient lorsque vous cliquez sur le bouton **Publier** dans l’éditeur universel pour publier le contenu que vous avez modifié.

L’éditeur universel effectue une itération sur le contenu et génère une liste de références qui doit également être publiée.

>[!BEGINTABS]

>[!TAB Exemple de charge utile]

```json
{
  "connections": [
    {
      "name": "aemconnection",
      "protocol": "aem",
      "uri": "https://author-pXXXX-eYYYYY.adobeaemcloud.com"
    }
  ],
  "references": [
    "urn:aemconnection:/content/dam/wknd-shared/en/magazine/arctic-surfing/aloha-spirits-in-northern-norway/jcr:content/data/master",
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
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/image",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/image_229050934",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/image_2123678383",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_1668104604",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_1138559521",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/image_275525847"
  ]
}
```

>[!TAB Exemple de réponse]

```json
{
  "publishes": [
    "/content/dam/wknd-shared/en/magazine/arctic-surfing/aloha-spirits-in-northern-norway",
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

>[!ENDTABS]

## Ressources supplémentaires {#additional-resources}

* [Événements d’éditeur universels](/help/implementing/universal-editor/events.md)

