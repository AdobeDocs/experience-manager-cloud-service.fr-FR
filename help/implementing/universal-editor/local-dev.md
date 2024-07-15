---
title: Développement d’AEM locales avec l’éditeur universel
description: Découvrez comment Universal Editor prend en charge la modification sur les instances d’AEM locales à des fins de développement.
exl-id: ba1bf015-7768-4129-8372-adfb86e5a120
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 2%

---


# Développement d’AEM locales avec l’éditeur universel {#local-dev-ue}

Découvrez comment Universal Editor prend en charge la modification sur les instances d’AEM locales à des fins de développement.

## Vue d’ensemble {#overview}

Le service d’éditeur universel est ce qui lie l’éditeur universel et le système principal. Pour pouvoir développer localement pour Universal Editor, vous devez exécuter une copie locale du service Universal Editor. En effet :

* Le service d’éditeur universel officiel d’Adobe est hébergé globalement, et votre instance AEM locale doit être exposée à Internet.
* Lors du développement avec un SDK d’AEM local, le service d’éditeur universel d’Adobe n’est pas accessible sur Internet.
* Si votre instance d’AEM comporte des restrictions d’adresse IP et que le service d’éditeur universel d’Adobe ne se trouve pas dans une plage d’adresses IP définie, vous pouvez l’héberger vous-même.

Ce document explique comment exécuter AEM en HTTPS avec une copie locale du service d’éditeur universel afin que vous puissiez développer localement sur AEM pour une utilisation avec l’éditeur universel.

## Configuration d’AEM à exécuter sur HTTPS {#aem-https}

Dans un cadre externe sécurisé avec HTTPS, un cadre HTTP non sécurisé ne peut pas être chargé. Le service Universal Editor s’exécute sur HTTPS. Par conséquent, AEM ou toute autre page distante doit s’exécuter également sur HTTPS.

Pour ce faire, vous devez configurer AEM pour qu’il s’exécute sur HTTPS. À des fins de développement, vous pouvez utiliser un certificat auto-signé.

[Consultez ce document](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/use-the-ssl-wizard.html?lang=fr) sur la configuration de l’AEM s’exécutant sur HTTPS, y compris un certificat auto-signé que vous pouvez utiliser.

## Installation du service Universal Editor {#install-ue-service}

Le service d’éditeur universel n’est pas une copie complète de l’éditeur universel, mais seulement un sous-ensemble de ses fonctionnalités pour s’assurer que les appels provenant de votre environnement d’AEM local ne sont pas acheminés sur Internet, mais à partir d’un point de terminaison défini que vous contrôlez.

[NodeJS version 16](https://nodejs.org/en/download/releases) est nécessaire pour exécuter une copie locale du service Universal Editor.

Le service d’éditeur universel est disponible via Distribution logicielle. Pour plus d’informations sur la façon d’y accéder, consultez la [documentation sur la distribution de logiciels](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=fr).

Enregistrez le fichier `universal-editor-service.cjs` de Distribution logicielle dans votre environnement de développement local.

## Création d’un certificat pour exécuter le service Universal Editor avec HTTPS {#ue-https}

Le service d’éditeur universel requiert également un certificat à exécuter sur HTTPS dans votre environnement de développement.

Exécutez la commande suivante.

```text
$ openssl req -newkey rsa:2048 -nodes -keyout key.pem -x509 -days 365 -out certificate.pem
```

La commande génère un fichier `key.pem` et un fichier `certificate.pem`. Enregistrez ces fichiers dans le même chemin que votre fichier `universal-editor-service.cjs`.

## Configuration de la configuration du service d’éditeur universel {#setting-up-service}

Un certain nombre de variables d’environnement doivent être définies dans NodeJS pour exécuter localement le service d’éditeur universel.

Sur le même chemin que vos fichiers `universal-editor-service.cjs`, `key.pem` et `certificate.pem`, créez un fichier `.env` avec le contenu suivant.

```text
EXPRESS_PORT=8000
EXPRESS_PRIVATE_KEY=./key.pem
EXPRESS_CERT=./certificate.pem
NODE_TLS_REJECT_UNAUTHORIZED=0
```

La variable a les significations suivantes :

* `EXPRESS_PORT` : définit le port sur lequel écoute le service Universal Editor
* `EXPRESS_PRIVATE` : pointe vers votre [clé privée créée précédemment,](#ue-https) `key.pem`
* `EXPRESS_CERT` : pointe vers votre [ certificat créé précédemment,](#ue-https) `certificate.pem`
* `NODE_TLS_REJECT_UNAUTHORIZED=0` : accepte les certificats auto-signés

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

Une fois défini, vous devriez voir chaque appel de mise à jour de contenu aller à `https://localhost:8000` au lieu du service d’éditeur universel par défaut.

>[!NOTE]
>
>Toute tentative d&#39;accès direct à `https://localhost:8000` entraîne une erreur `404`. Ce comportement est attendu.
>
>Pour tester l’accès à votre service Universal Editor local, utilisez `https://localhost:8000/corslib/LATEST`. Pour plus d’informations, reportez-vous à la [section suivante](#editing) .

>[!TIP]
>
>Pour plus d’informations sur la manière dont les pages sont instrumentées pour utiliser le service Global Universal Editor, consultez le document [Prise en main d’Universal Editor dans AEM](/help/implementing/universal-editor/getting-started.md#instrument-page)

## Modification d’une page avec le service d’éditeur universel local {#editing}

Avec le [service d&#39;éditeur universel s&#39;exécutant localement](#running-ue) et votre [ page de contenu instrumentée pour utiliser le service local, ](#using-loca-ue) vous pouvez maintenant démarrer l&#39;éditeur.

1. Ouvrez votre navigateur sur `https://localhost:8000/corslib/LATEST`.
1. Dirigez votre navigateur pour accepter [votre certificat auto-signé.](#ue-https)
1. Une fois le certificat autosigné approuvé, vous pouvez modifier la page à l’aide de votre service d’éditeur universel local.

