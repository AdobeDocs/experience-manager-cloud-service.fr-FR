---
title: Événements de l’éditeur universel
description: Découvrez les différents événements envoyés par l’éditeur universel que vous pouvez utiliser pour réagir aux modifications de contenu ou d’interface utilisateur dans votre application distante.
exl-id: c9f7c284-f378-4725-a4e6-e4799f0f8175
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 2%

---

# Événements de l’éditeur universel {#events}

Découvrez les différents événements envoyés par l’éditeur universel que vous pouvez utiliser pour réagir aux modifications de contenu ou d’interface utilisateur dans votre application distante.

## Présentation {#introduction}

Les applications peuvent avoir des exigences différentes pour les mises à jour de page ou de composant. Par conséquent, l’éditeur universel envoie les événements définis aux applications distantes. Si l’application distante ne dispose pas d’écouteur d’événement personnalisé pour l’événement envoyé, un [ écouteur d’événement de secours ](#fallback-listeners) fourni par le package `universal-editor-cors` est exécuté.

Tous les événements sont appelés sur l’élément DOM concerné de la page distante. Les événements se propagent jusqu’à l’élément `BODY` où l’écouteur d’événement par défaut fourni par le package `universal-editor-cors` est enregistré. Il existe des événements pour le contenu et des événements pour l’interface utilisateur.

Tous les événements suivent une convention de nommage.

* `aue:<content-or-ui>-<event-name>`

Par exemple, `aue:content-update` et `aue:ui-select`

Les événements incluent la payload de la requête et de la réponse et sont déclenchés une fois l’appel correspondant réussi. Pour plus d’informations sur les appels et des exemples de payloads, consultez le document [Appels de l’éditeur universel](/help/implementing/universal-editor/calls.md).

## Événements de mise à jour du contenu {#content-events}

### aue:content-add {#content-add}

L’événement `aue:content-add` est déclenché lorsqu’un nouveau composant est ajouté à un conteneur.

La payload correspond au contenu du service d’éditeur universel, avec le contenu de secours de la définition du composant.

```json
{
    details: {
        request: request payload;   // what is sent to the service
        response: {                 // what is returned by the service
            resource: string;       // newly created content resource
            updates: [{
                resource: string;   // resource to update
                type: string;       // type of instrumentation
                content?: string;   // content to replace
            }]
        }
    }
}
```

### aue:content-details {#content-details}

L’événement `aue:content-details` est déclenché lorsqu’un composant est chargé dans le panneau des propriétés.

La payload correspond au contenu du composant et, éventuellement, à son schéma.

```json
{
    details: {
        content: object             // content object
        model: [object]             // model object
        request: request payload;   // what is sent to the service
        response: response payload; // what is returned by the service
    }
}
```

### aue:content-move {#content-move}

L’événement `aue:content-move` est déclenché lorsqu’un composant est déplacé.

La payload est le composant , le conteneur source et le conteneur cible.

```json
{
    details: {
        from: string;                   // container we move the component from
        component: string;              // component we move
        to: string;                     // container we move the component to
        before: string;                    // before which component shall we place the component
        request: request payload;       // what is sent to the service
        response: response payload;     // what is returned by the service
    }
}
```

### aue:content-patch {#content-patch}

L’événement `aue:content-patch` est déclenché lorsque les données d’un composant sont mises à jour dans le panneau des propriétés.

La payload est un correctif JSON des propriétés mises à jour.

```json
{
    details: {
        patch: {
            name: string;               // attribute which is updated
            value: string;              // new value which is stored to the attribute
        },
        request: request payload;       // what is sent to the service
        response: response payload;     // what is returned by the service
    }
}
```

### aue:content-remove {#content-remove}

L’événement `aue:content-remove` est déclenché lorsqu’un composant est supprimé d’un conteneur.

La payload est l’identifiant d’élément du composant supprimé.

```json
{
    details: {
        resource: string;               // the resource which got removed
        request: request payload;       // what is sent to the service
        response: response payload;     // what is returned by the service
    }
}
```

### aue:content-update {#content-update}

L’événement `aue:content-update` est déclenché lorsque les propriétés d’un composant sont mises à jour en contexte.

La payload est la valeur mise à jour.

```json
{
    details: {
        value: string;                  // updated value
        request: request payload;       // what is sent to the service
        response: response payload;     // what is returned by the service 
    }
}
```

### Transmission des payloads {#passing-payloads}

Pour tous les événements de mise à jour de contenu, la payload demandée ainsi que la payload de réponse sont transmises à l’événement. Par exemple, pour un appel de mise à jour :

Payload de requête :

```json
{
  "connections": [
    {
      "name": "aemconnection",
      "protocol": "aem",
      "uri": "https://author-p7452-e12433.adobeaemcloud.com"
    }
  ],
  "target": {
    "resource": "urn:aemconnection:/content/dam/wknd-shared/en/magazine/arctic-surfing/aloha-spirits-in-northern-norway/jcr:content/data/master",
    "type": "text",
    "prop": "title"
  },
  "value": "Alhoa Spirit Northern Norway!"
}
```

Payload de réponse

```json
{
    "updates": [
        {
            "resource": "urn:aemconnection:/content/dam/wknd-shared/en/magazine/arctic-surfing/aloha-spirits-in-northern-norway/jcr:content/data/master",
            "prop": "title",
            "type": "text"
        }
    ]
}
```

## Événements d’interface utilisateur {#ui-events}

### aue:ui-publish {#ui-publish}

L’événement `aue:ui-publish` est déclenché lors de la publication du contenu (avec des appels au niveau du `BODY`).

La payload consiste en une liste d’ID d’élément et de leur statut de publication.

### aue:ui-select {#ui-select}

L’événement `aue:ui-select` est déclenché lorsqu’un composant est sélectionné.

La payload correspond à l’ID d’élément, aux propriétés de l’élément et au type d’élément du composant sélectionné.

```json
{
    details: {
        resource: string;       // resource of the selected
        prop: string;           // prop of the selected
        type: string;           // type of the selected
        selected: boolean;      // was selected or unselected
    }
}
```

### aue:ui-preview {#ui-preview}

L’événement `aue:ui-preview` est déclenché lorsque le mode de modification de la page devient **Aperçu**.

La payload est vide pour cet événement.

```json
{
    details: {}
}
```

### aue:ui-edit {#ui-edit}

L’événement `aue:ui-edit` est déclenché lorsque le mode de modification de la page est remplacé par **Modifier**.

La payload est vide pour cet événement.

```json
{
    details: {}
}
```

### aue:ui-viewport-change {#ui-viewport-change}

L’événement `aue:ui-viewport-change` est déclenché lorsque la taille de la fenêtre d’affichage est modifiée.

La payload correspond aux dimensions de la fenêtre d’affichage.

```json
{
    details: {
        height: number?;        // height of the viewport. Undefined when fullscreen
        width: number?;         // width of the viewport. Undefined when fullscreen
    }
}
```

### aue:initialized {#initialized}

L’événement `aue:initialized` est déclenché pour informer la page distante qu’elle a bien été chargée dans l’éditeur universel.

La payload est vide pour cet événement.

```json
{
    details: {}
}
```

## Écouteurs d’événements de secours {#fallback-listeners}

### Mises à jour du contenu {#content-update-fallbacks}

| Événement | Comportement |
|---|---|
| `aue:content-add` | Rechargement de page |
| `aue:content-details` | Ne rien faire |
| `aue:content-move` | Déplacez le contenu/la structure du composant vers la zone cible |
| `aue:content-patch` | Rechargement de page |
| `aue:content-remove` | Supprimer l’élément DOM |
| `aue:content-update` | Mise à jour de la `innerHTML` avec la payload |

### Événements d’interface utilisateur {#ui-event-fallbacks}

| Événement | Comportement |
|---|---|
| `aue:ui-publish` | Ne rien faire |
| `aue:ui-select` | Faire défiler jusqu’à l’élément sélectionné |
| `aue:ui-preview` | Ajouter un `class="adobe-ue-preview"` à la balise d’HTML |
| `aue:ui-edit` | Ajouter un `class=adobe-ue-edit"` à la balise d’HTML |
| `aue:ui-viewport-change` | Ne rien faire |
| `aue:initialized` | Ne rien faire |

## Ressources supplémentaires {#additional-resources}

* [Appels de l’éditeur universel](/help/implementing/universal-editor/calls.md)

