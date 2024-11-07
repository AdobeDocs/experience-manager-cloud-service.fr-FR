---
title: Événements d’éditeur universels
description: Découvrez les différents événements que l’éditeur universel envoie et que vous pouvez utiliser pour réagir aux changements de contenu ou d’interface utilisateur dans votre application distante.
exl-id: c9f7c284-f378-4725-a4e6-e4799f0f8175
feature: Developing
role: Admin, Architect, Developer
source-git-commit: a7b48559e5bf60c86fecd73a8bcef6c9aaa03b80
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 2%

---

# Événements d’éditeur universels {#events}

Découvrez les différents événements que l’éditeur universel envoie et que vous pouvez utiliser pour réagir aux changements de contenu ou d’interface utilisateur dans votre application distante.

## Présentation {#introduction}

Les applications peuvent avoir des exigences différentes pour les mises à jour de page ou de composant. Par conséquent, l’éditeur universel envoie des événements définis aux applications distantes. Si l’application distante n’a pas d’écouteur d’événement personnalisé pour l’événement envoyé, un [écouteur d’événement de secours](#fallback-listeners) fourni par le package `universal-editor-cors` est exécuté.

Tous les événements sont appelés sur l’élément DOM affecté de la page distante. Les événements se propagent jusqu’à l’élément `BODY` où l’écouteur d’événement par défaut fourni par le package `universal-editor-cors` est enregistré. Il existe des événements pour le contenu et des événements pour l’interface utilisateur.

Tous les événements suivent une convention d’affectation des noms.

* `aue:<content-or-ui>-<event-name>`

Par exemple, `aue:content-update` et `aue:ui-select`

Les événements incluent la charge utile de la requête et de la réponse et sont déclenchés une fois que l’appel correspondant a réussi. Pour plus d’informations sur les appels et des exemples de leurs payloads, consultez le document [Appels Universal Editor.](/help/implementing/universal-editor/calls.md)

## Événements de mise à jour de contenu {#content-events}

### aue:content-add {#content-add}

L’événement `aue:content-add` est déclenché lorsqu’un nouveau composant est ajouté à un conteneur.

La payload est le contenu du service Universal Editor, avec le contenu de secours de la définition du composant.

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

La payload est le contenu du composant et éventuellement son schéma.

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

La charge utile est le composant, le conteneur source et le conteneur cible.

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

La payload est l’identifiant de l’élément du composant supprimé.

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

### Transmission de payloads {#passing-payloads}

Pour tous les événements de mise à jour du contenu, la charge utile demandée ainsi que la charge de réponse sont transmises à l’événement. Par exemple, pour un appel de mise à jour :

Charge utile de requête :

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

## Événements de l’interface utilisateur {#ui-events}

### aue:ui-publish {#ui-publish}

L’événement `aue:ui-publish` est déclenché lorsque le contenu est publié (avec appel au niveau `BODY`).

La payload est une liste d’identifiants d’élément et de leur état de publication.

### aue:ui-select {#ui-select}

L’événement `aue:ui-select` est déclenché lorsqu’un composant est sélectionné.

La charge utile correspond à l’identifiant de l’élément, aux propriétés de l’élément et au type d’élément du composant sélectionné.

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

L’événement `aue:ui-preview` est déclenché lorsque le mode de modification de la page est remplacé par **Preview**.

La payload est vide pour cet événement.

```json
{
    details: {}
}
```

### aue:ui-edit {#ui-edit}

L’événement `aue:ui-edit` est déclenché lorsque le mode de modification de la page est remplacé par **Edit**.

La payload est vide pour cet événement.

```json
{
    details: {}
}
```

### aue:ui-viewport-change {#ui-viewport-change}

L’événement `aue:ui-viewport-change` est déclenché lorsque la taille de la fenêtre d’affichage est modifiée.

La payload est les dimensions de la fenêtre d’affichage.

```json
{
    details: {
        height: number?;        // height of the viewport. Undefined when fullscreen
        width: number?;         // width of the viewport. Undefined when fullscreen
    }
}
```

### aue:initialized {#initialized}

L’événement `aue:initialized` est déclenché pour informer la page distante qu’elle est correctement chargée dans l’éditeur universel.

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
| `aue:content-move` | Déplacer le contenu/la structure du composant vers la zone cible |
| `aue:content-patch` | Rechargement de page |
| `aue:content-remove` | Suppression de l’élément DOM |
| `aue:content-update` | Mettre à jour `innerHTML` avec la payload |

### Événements de l’interface utilisateur {#ui-event-fallbacks}

| Événement | Comportement |
|---|---|
| `aue:ui-publish` | Ne rien faire |
| `aue:ui-select` | Accédez à l’élément sélectionné |
| `aue:ui-preview` | Ajouter `class="adobe-ue-preview"` à la balise d’HTML |
| `aue:ui-edit` | Ajouter `class=adobe-ue-edit"` à la balise d’HTML |
| `aue:ui-viewport-change` | Ne rien faire |
| `aue:initialized` | Ne rien faire |

## Ressources supplémentaires {#additional-resources}

* [Appels de l’éditeur universel](/help/implementing/universal-editor/calls.md)

