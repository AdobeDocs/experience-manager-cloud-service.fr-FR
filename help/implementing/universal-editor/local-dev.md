---
title: Développement d’AEM locales avec l’éditeur universel
description: Découvrez comment Universal Editor prend en charge la modification sur les instances d’AEM locales à des fins de développement.
exl-id: ba1bf015-7768-4129-8372-adfb86e5a120
source-git-commit: 16f2922a3745f9eb72f7070c30134e5149eb78ce
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 0%

---


# Développement d’AEM locales avec l’éditeur universel {#local-dev-ue}

Découvrez comment Universal Editor prend en charge la modification sur les instances d’AEM locales à des fins de développement.

{{universal-editor-status}}

## Vue d’ensemble {#overview}

Ce document explique comment exécuter AEM en HTTPS avec une copie locale du service Universal Editor afin que vous puissiez développer localement sur AEM à l’aide de l’éditeur universel.

## Configuration d’AEM à exécuter sur HTTPS {#aem-https}

Dans un cadre externe sécurisé avec HTTPS, un cadre HTTP non sécurisé ne peut pas être chargé. Le service Universal Editor s’exécute sur HTTPS. Par conséquent, AEM ou toute autre page distante doit s’exécuter également sur HTTPS.

Pour ce faire, vous devez configurer AEM pour qu’il s’exécute sur HTTPS. À des fins de développement, vous pouvez utiliser un certificat auto-signé.

Consultez ce document sur la configuration d’AEM s’exécutant sur HTTPS, y compris un certificat auto-signé que vous pouvez utiliser.

## Installation du service Universal Editor {#install-ue-service}

Le service d’éditeur universel est ce qui lie l’éditeur universel et le système principal. Comme le service Universal Editor officiel est hébergé globalement, votre instance AEM locale doit être exposée à Internet. Pour éviter cela, vous pouvez exécuter une copie locale du service Universal Editor.

[NodeJS version 16](https://nodejs.org/en/download/releases) est nécessaire pour exécuter une copie locale du service Universal Editor

Le service d’éditeur universel est distribué directement par AEM Engineering. Contactez votre ingénieur dans le programme VIP pour obtenir une copie locale.

L’ingénieur vous fournira un `universal-editor-service.cjs` fichier . Enregistrez-le dans votre environnement de développement local.

## Création d’un certificat pour exécuter le service Universal Editor avec HTTPS {#ue-https}

Le service d’éditeur universel requiert également un certificat à exécuter sur HTTPS dans votre environnement de développement.

Exécutez la commande suivante.

```text
$ openssl req -newkey rsa:2048 -nodes -keyout key.pem -x509 -days 365 -out certificate.pem
```

La commande génère un `key.pem` et un `certificate.pem` fichier . Enregistrez ces fichiers au même chemin que votre `universal-editor-service.cjs` fichier .

## Configuration de la configuration du service d’éditeur universel {#setting-up-service}

Un certain nombre de variables d’environnement doivent être définies dans NodeJS pour exécuter localement le service d’éditeur universel.

Sur le même chemin que votre `universal-editor-service.cjs`, `key.pem` et `certificate.pem` fichiers, créez une `.env` avec le contenu suivant.

```text
EXPRESS_PORT=8000
EXPRESS_PRIVATE_KEY=./key.pem
EXPRESS_CERT=./certificate.pem
NODE_TLS_REJECT_UNAUTHORIZED=0
```

La variable a les significations suivantes :

* `EXPRESS_PORT`: définit le port sur lequel écoute le service Universal Editor.
* `EXPRESS_PRIVATE`: pointe vers votre [clé privée créée précédemment,](#ue-https) `key.pem`
* `EXPRESS_CERT`: pointe vers votre [certificat créé précédemment,](#ue-https) `certificate.pem`
* `NODE_TLS_REJECT_UNAUTHORIZED=0`: accepte les certificats auto-signés

## Exécution du service Universal Editor {#running-ue}

Pour démarrer le service Universal Editor, exécutez la commande suivante :

```text
$ node ./universal-editor-service.cjs
```

Il doit générer les résultats suivants sur votre terminal :

```text
Universal Editor Service listening on port 8000 as HTTPS Server
```

Assurez-vous que le service démarre le serveur HTTPS et non le serveur HTTP.

## Utilisation du service d’éditeur universel local au lieu du service global {#using-local-ue}

Universal Editor sait quel service d’éditeur universel utiliser pour modifier une page en fonction de la manière dont la page est instrumentée. Cette opération s’effectue par le biais de balises META dans la page chargée dans Universal Editor.

Pour qu’une page soit modifiée à l’aide de votre service Universal Editor local, la balise meta suivante doit être définie :

```html
<meta name="urn:adobe:aue:config:service" content="https://localhost:8000">
```

Une fois défini, vous devriez voir chaque appel de mise à jour de contenu envoyé à `https://localhost:8000` au lieu du service Universal Editor par défaut.

>[!TIP]
>
>Pour plus d’informations sur la manière dont les pages sont instrumentées pour utiliser le service Global Universal Editor, consultez le document . [Prise en main d’Universal Editor dans AEM](/help/implementing/universal-editor/getting-started.md#instrument-page)

## Modification d’une page avec le service d’éditeur universel local {#editing}

Avec la variable [Service d’éditeur universel s’exécutant localement](#running-ue) et votre [page de contenu instrumentée pour utiliser le service local,](#using-loca-ue) vous pouvez maintenant lancer l’éditeur.

1. Ouvrez votre navigateur pour `https://localhost:8000/`.
1. Dirigez votre navigateur pour accepter [votre certificat auto-signé.](#ue-https)
1. Une fois le certificat autosigné approuvé, vous pouvez modifier la page à l’aide de votre service d’éditeur universel local.
