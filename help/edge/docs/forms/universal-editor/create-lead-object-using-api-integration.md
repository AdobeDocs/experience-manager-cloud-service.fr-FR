---
title: Créer un objet de lead Salesforce à l’aide de l’intégration d’API
description: Découvrez comment créer un objet de lead Salesforce à l’aide de l’intégration d’API.
feature: Adaptive Forms, Core Components, Edge Delivery Services
role: User, Developer
level: Beginner, Intermediate
keywords: intégration d’API dans l’éditeur de règles, améliorations du service d’appel
exl-id: 55835ffe-1b77-449b-b76d-16c0a343cf5c
hide: true
hidefromtoc: true
index: false
source-git-commit: 3a09a3fa9b8fb3dacef4c900979c4cc256551941
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 100%

---

# Créer un objet de lead Salesforce à l’aide de l’intégration d’API

Ce cas d’utilisation explique comment créer un lead dans Salesforce à l’aide de l’intégration d’API. À la fin de ce processus, vous serez en mesure d’effectuer les opérations suivantes :

Configurer une [application connectée dans Salesforce](https://help.salesforce.com/s/articleView?id=platform.ev_relay_create_connected_app.htm&type=5) pour activer l’accès sécurisé à l’API.

Configurer CORS (partage de ressources entre origines multiples) pour permettre au code (tel que JavaScript) s’exécutant dans un navigateur web de communiquer avec Salesforce à partir d’une origine spécifique, ajouter l’origine à la liste autorisée comme illustré ci-dessous

![cors](assets/salesforce-cors.png)

## Paramètres de l’application connectée

Les paramètres suivants sont utilisés dans l’application connectée. Vous pouvez attribuer les portées OAuth en fonction de vos besoins.
![connections-app-settings](assets/salesforce-connected-app-settings.png)

## Créer une intégration d’API

| Nom | Valeur |
|--------------------------------|------------------|
| URL de l’API | https://`<your-domain>`d.my.salesforce.com/services/data/v32.0/sobjects/Lead |
| ID client | Spécifique à votre application connectée |
| Secret client | Spécifique à votre application connectée |
| URL OAuth | https://login.salesforce.com/services/oauth2/authorize |
| URL du jeton d’accès | https://`<your-domain>`/services/oauth2/token |
| URL du jeton d’actualisation | https://`<your-domain>`/services/oauth2/token |
| Champ d’application de l’autorisation | api chatter_api full id openid refresh_token visualforce web |
| En-tête d’autorisation | Support d’autorisation |

![api-integration](assets/salesforce-api-integration-create-lead.png)

## Paramètres d’entrée et de sortie

Définissez les paramètres d’entrée de l’appel API et mappez les paramètres de sortie à l’aide du code JSON suivant.

```json
{
    "id": "00QKY000001LyJR2A0",
    "success": true
}
```

![input-output](assets/create-lead-api-integration-input-output.png)

## Créer un formulaire

Créez un formulaire adaptatif simple à l’aide de l’éditeur universel pour capturer les détails de l’objet Lead comme illustré ci-dessous.
![lead-object-form](assets/create-lead.png)

Gérez l’événement de clic sur la case à cocher Créer un lead à l’aide de l’éditeur de règles. Mappez les paramètres d’entrée aux valeurs des objets de formulaire appropriés, comme illustré ci-dessous. Affichez l’identifiant de l’objet Lead nouvellement créé dans l’objet TextField `leadid`.
![rule-editor](assets/create-leade-rule-editor.png)

## Tester l’intégration

- Prévisualisez le formulaire.
- Saisissez des valeurs significatives.
- Cochez la case `Create Lead` pour déclencher l’appel API.
- L’ID de lead de l’objet Lead nouvellement créé s’affiche dans le champ de texte `Lead ID`.
