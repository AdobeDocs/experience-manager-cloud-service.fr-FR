---
title: Exécuter votre propre service d’éditeur universel
description: Découvrez comment exécuter votre propre service d’éditeur universel pour le développement local ou dans le cadre de votre propre infrastructure.
exl-id: ba1bf015-7768-4129-8372-adfb86e5a120
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '950'
ht-degree: 100%

---


# Exécuter votre propre service d’éditeur universel {#local-ue-service}

Découvrez comment exécuter votre propre service d’éditeur universel pour le développement local ou dans le cadre de votre propre infrastructure.

>[!NOTE]
>
>Les services de l’éditeur universel local ne sont pas requis ou pris en charge pour les projets utilisant la création AEM avec Edge Delivery Services.

## Vue d’ensemble {#overview}

Le service d’éditeur universel lie l’éditeur universel et le système principal. Pour développer localement avec l’éditeur universel, exécutez une copie locale du service d’éditeur universel. En effet :

* Le service d’éditeur universel officiel d’Adobe est hébergé globalement, et votre instance AEM locale doit être exposée à Internet.
* Lors du développement avec un SDK AEM local, le service d’éditeur universel d’Adobe n’est pas accessible depuis Internet.
* Si votre instance AEM comporte des restrictions IP et que le service d’éditeur universel d’Adobe ne figure pas dans une plage IP définie, vous pouvez l’héberger vous-même.

## Cas d’utilisation {#use-cases}

Votre propre copie du service d’éditeur universel est utile si vous souhaitez :

* Développer localement sur AEM pour une utilisation avec l’éditeur universel.
* Exécuter votre propre service d’éditeur universel dans le cadre de votre infrastructure, indépendamment du service Éditeur universel d’Adobe.

Les deux cas d’utilisation sont pris en charge. Ce document explique comment exécuter AEM en HTTPS avec une copie locale du service d’éditeur universel.

Si vous souhaitez exécuter votre propre service d’éditeur universel dans le cadre de votre infrastructure, suivez les mêmes étapes que dans l’exemple de développement local.

## Configuration d’AEM pour une exécution sur HTTPS {#aem-https}

Dans une trame externe sécurisée par HTTPS, une trame HTTP non sécurisée ne peut pas être chargée. Le service d’éditeur universel s’exécute en HTTPS et, par conséquent, AEM ou toute autre page distante doit également s’exécuter en HTTPS.

Pour ce faire, configurez AEM pour qu’il s’exécute en HTTPS. À des fins de développement, vous pouvez utiliser un certificat auto-signé.

[Consultez ce document](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/use-the-ssl-wizard.html?lang=fr) expliquant comment configurer AEM pour qu’il s’exécute en HTTPS, y compris avec un certificat auto-signé que vous pouvez utiliser.

## Installation du service d’éditeur universel {#install-ue-service}

Le service d’éditeur universel n’est pas une copie complète de l’éditeur universel, mais seulement un sous-ensemble de ses fonctionnalités afin de garantir que les appels provenant de votre environnement AEM local ne transitent pas par Internet, mais par un point de terminaison défini que vous contrôlez.

[NodeJS version 20](https://nodejs.org/en/download/releases) est nécessaire pour exécuter une copie locale du service d’éditeur universel.

Le service d’éditeur universel est disponible via la plateforme Software Distribution (Distribution de logiciels). Veuillez consulter la documentation [Software Distribution](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=fr) pour obtenir des détails sur la manière d’y accéder.

Enregistrez le fichier `universal-editor-service.cjs` depuis Software Distribution dans votre environnement de développement local.

## Créez un certificat pour exécuter le service d’éditeur universel avec HTTPS. {#ue-https}

Le service d’éditeur universel nécessite également un certificat pour s’exécuter en HTTPS dans votre environnement de développement.

Exécutez la commande suivante.

```text
$ openssl req -newkey rsa:2048 -nodes -keyout key.pem -x509 -days 365 -out certificate.pem
```

La commande génère un fichier `key.pem` et un fichier `certificate.pem`. Enregistrez ces fichiers dans le même chemin d’accès que votre fichier `universal-editor-service.cjs`.

## Configuration du service d’éditeur universel {#setting-up-service}

Un certain nombre de variables d’environnement doivent être définies dans NodeJS pour exécuter le service d’éditeur universel localement.

Sur le même chemin d’accès que vos fichiers `universal-editor-service.cjs`, `key.pem` et `certificate.pem`, créez un fichier `.env` avec le contenu suivant.

```text
UES_PORT=8000
UES_PRIVATE_KEY=./key.pem
UES_CERT=./certificate.pem
UES_TLS_REJECT_UNAUTHORIZED=false
UES_CORS_PRIVATE_NETWORK=true
```

Ce sont les valeurs minimales requises pour le développement local dans notre exemple.

>[!NOTE]
>
>Si vous exécutez Chrome version 130 ou ultérieure, vous devez activer l’envoi d’en-têtes CORS pour [accès au réseau privé](https://wicg.github.io/private-network-access/#private-network-request) à l’aide de l’option `UES_CORS_PRIVATE_NETWORK`.


Le tableau suivant détaille ces valeurs et les valeurs supplémentaires disponibles.

| Valeur | Facultatif | Valeur par défaut | Description |
|---|---|---|---|
| `UES_PORT` | Oui | `8080` | Port sur lequel le serveur s’exécute |
| `UES_PRIVATE_KEY` | Oui | Aucune | Chemin d’accès à la clé privée du serveur HTTPS |
| `UES_CERT` | Oui | Aucune | Chemin d’accès au fichier de certification pour le serveur HTTPS |
| `UES_TLS_REJECT_UNAUTHORIZED` | Oui | `true` | Rejeter les connexions TLS non autorisées |
| `UES_DISABLE_IMS_VALIDATION` | Oui | `false` | Désactiver la validation IMS |
| `UES_ENDPOINT_MAPPING` | Oui | Vide | Mappage des points d’entrée pour les réécritures internes<br>Exemple : `UES_ENDPOINT_MAPPING='[{"https://your-public-facing-author-domain.net": "http://10.0.0.1:4502"}]'`<br>résultat : le service d’éditeur universel se connectera à `http://10.0.0.1:4502` au lieu de la connexion fournie `https://your-public-facing-author-domain.net`. |
| `UES_LOG_LEVEL` | Oui | `info` | Niveau de journalisation pour le serveur, valeurs possibles : `silly`, `trace`, `debug`, `verbose`, `info`, `log`, `warn`, `error` et `fatal` |
| `UES_SPLUNK_HEC_URL` | Oui | Aucune | URL HEC vers le point d’entrée Splunk |
| `UES_SPLUNK_TOKEN` | Oui | Aucune | Jeton Splunk |
| `UES_SPLUNK_INDEX` | Oui | Aucune | Index vers lequel écrire les journaux |
| `UES_SPLUNK_SOURCE` | Oui | `universal-editor-service` | Nom de la source dans les journaux Splunk |
| `UES_CORS_PRIVATE_NETWORK` | Oui | `false` | Activer l’envoi des en-têtes CORS pour autoriser [ le réseau privé](https://wicg.github.io/private-network-access/#private-network-request). Requis pour les utilisateurs ou utilisatrices de Chrome version 130+ |

>[!NOTE]
>
>Avant la version [ du 13 août 2024](/help/release-notes/universal-editor/current.md) de l’éditeur universel, les variables suivantes étaient requises dans le fichier `.env`. Ces valeurs seront prises en charge jusqu’au 1er octobre 2024 pour assurer la rétrocompatibilité.
>
>`EXPRESS_PORT=8000`
>`EXPRESS_PRIVATE_KEY=./key.pem`
>`EXPRESS_CERT=./certificate.pem`
>`NODE_TLS_REJECT_UNAUTHORIZED=0`

## Exécution du service d’éditeur universel {#running-ue}

Pour démarrer le service d’éditeur universel, exécutez la commande suivante :

```text
$ node ./universal-editor-service.cjs
```

Le terminal doit afficher le résultat suivant :

```text
Universal Editor Service listening on port 8000 as HTTPS Server
```

Assurez-vous que le service démarre en HTTPS Server et non en HTTP Server.

## Utilisation du service d’éditeur universel local au lieu du service global {#using-local-ue}

L’éditeur universel sait quel service d’éditeur universel utiliser pour modifier une page, en fonction de la manière dont la page est instrumentée. Cette opération s’effectue à l’aide de balises méta dans la page chargée dans l’éditeur universel.

Pour qu’une page soit modifiée à l’aide de votre service d’éditeur universel local, la balise méta suivante doit être définie :

```html
<meta name="urn:adobe:aue:config:service" content="https://localhost:8000">
```

Une fois définie, chaque appel de mise à jour de contenu doit être dirigé vers `https://localhost:8000` au lieu du service d’éditeur universel par défaut.

>[!NOTE]
>
>Toute tentative d’accès direct à `https://localhost:8000` entraîne une erreur `404`. Il s’agit d’un comportement attendu.
>
>Pour tester l’accès à votre service d’éditeur universel local, utilisez `https://localhost:8000/corslib/LATEST`. Voir la [section suivante](#editing) pour plus d’informations.

>[!TIP]
>
>Pour plus d’informations sur la manière dont les pages sont instrumentées pour utiliser le service d’éditeur universel global, consultez le document [Prise en main de l’éditeur universel dans AEM](/help/implementing/universal-editor/getting-started.md#instrument-page).

## Modification d’une page avec le service d’éditeur universel local {#editing}

Avec le service d’éditeur universel [ exécuté localement](#running-ue) et votre page de contenu [ instrumentée pour utiliser le service local](/help/implementing/universal-editor/getting-started.md), vous pouvez maintenant démarrer l’éditeur.

1. Ouvrez votre navigateur sur `https://localhost:8000/ping`.
1. Demandez à votre navigateur d’accepter [votre certificat auto-signé](#ue-https).
1. Une fois le certificat auto-signé approuvé, vous pouvez modifier la page à l’aide de votre service d’éditeur universel local.

