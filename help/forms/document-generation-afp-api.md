---
title: Comment utiliser l’API de synchronisation de sortie AFP ?
description: Découvrez comment utiliser l’API de synchronisation de sortie AFP pour récupérer et synchroniser les rendus de sortie.
feature: Adaptive Forms, APIs & Integrations, Document Services
role: Admin, User
exl-id: 5602fc63-ef74-44eb-b3be-61b8f8a2795a
source-git-commit: b6316401bea7d6593d89d15e70c50536df5f116c
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 11%

---

# Générer une sortie AFP à l’aide de l’API AEM Forms

<span class="preview">Il s’agit d’une fonctionnalité de version préliminaire accessible par le biais de notre [canal de version préliminaire](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=fr#new-features). </span>

La présentation de fonctions avancées (AFP) est un format de document haute performance conçu principalement à des fins d&#39;impression.\
Ce guide décrit toutes les étapes et configurations nécessaires pour générer une sortie AFP à l’aide d’AEM Forms.

<!--
## Prerequisites

To support AFP output generation, the following OSGi bundles must be present and in an **active** state:

* **AFP Core Bundle** – Available in the AFP repository
* **Forms Output Core** – Found in the Forms Output comments package
* **Bedrock Connector** – Provided by the Forms Output API
* **Cloud Ready Implementation** – Available through the Forms installer

>[!NOTE]
>
> * If any bundle is inactive, resolve dependency issues or reinstall manually.
> * To enable AFP generation, the `FT_FORMS-17887` toggle configurations must be set in AEM configuration manager.-->

## API de génération AFP

Génère un fichier AFP (Advanced Function Presentation) à l&#39;aide d&#39;un modèle XDP et de données d&#39;entrée.

### L’autorisation

Vous pouvez utiliser l’autorisation **BasicAuth** (informations d’identification d’administrateur) pour les environnements locaux ou **BearerAuth** pour les instances AEM Cloud.

### Requête

**Point d’entrée:**
`POST http://<server>:<port>/adobe/forms/document/generate/afp`

### En-têtes

| Clé | Valeur |
| --------------- | ------------------------------------------------------ |
| `Content-Type` | `application/pdf` |
| `Authorization` | `(Bearer Access token)` |

### Corps de la requête

**Content-Type : multipart/form-data**

| Clé | Type | Requis | Description |
| ---------- | ---- | -------- | ------------------------------------------------------------------------- |
| `template` | Fichier/Texte | Oui | Fichier XDP utilisé comme modèle pour la génération AFP (par exemple, `demo.xdp`) |
| `data` | Fichier/Texte | Non | Fichier de données (XML ou JSON) à fusionner avec le modèle (`data.xml`, par exemple) |
| `options` | Texte | Non | Chaîne JSON avec des options pour contrôler la sortie AFP (par exemple, résolution, paramètres régionaux) |

**Exemple `options` JSON (champ de texte) :**

```json
{
  "pdfVersion": "1.7",
  "resolution": 300,
  "locale": "en-US",
  "embedFonts": true,
  "contentRoot": "/usr/tmp"
}
```

### Réponses

| Code | Description |
| ----- | ------------------------------------------------------------------------- |
| `200` | Opération réussie. Renvoie le flux du document AFP. |
| `400` | Requête incorrecte. La payload de la requête comporte des champs obligatoires incorrects ou manquants. |
| `500` | Erreur de serveur interne. Réessayez après un certain temps. |

### Commande Curl

```
curl --location 'http://<server>:<port>/adobe/forms/document/generate/afp' \
--header 'Authorization: Bearertoken <base64-encoded-credentials>' \
--form 'template=@"<path-to-template>.xdp"' \
--form 'data=@"<path-to-data-file>.xml"' \
--form 'options=<JSON-options-string>'
```

### Test de l’API

Vous pouvez télécharger le fichier .yaml et le charger dans Postman pour vérifier les fonctionnalités des API.

![image Postman AFP](/help/forms/assets/afp-postman.png)

Vous pouvez enregistrer la réponse et ouvrir le fichier enregistré dans le lecteur AFP pour l’afficher.

<!-- ![PDF reader](/help/forms/assets/afp-pdf.png) -->
