---
title: Génération de Jetons d'accès pour les API côté serveur
description: Découvrez comment faciliter la communication entre un serveur tiers et AEM en tant que Cloud Service en générant un jeton JWT sécurisé
translation-type: tm+mt
source-git-commit: 251f5de85d63f6afd730fc450fe2b5a06bc90c38
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 0%

---


# Présentation {#introduction}

>[!IMPORTANT]
>
>Cette fonction n’est pas encore disponible. Consultez les [Notes de mise à jour](/help/release-notes/release-notes-cloud/release-notes-current.md) pour connaître la liste à jour des fonctionnalités.

Certaines architectures reposent sur des appels à AEM en tant que Cloud Service à partir d&#39;une application hébergée sur un serveur en dehors de l&#39;infrastructure AEM. Par exemple, une application mobile qui appelle un serveur, qui effectue ensuite des demandes d’API à AEM en tant que Cloud Service.

Le flux serveur à serveur est décrit ci-dessous, ainsi qu’un flux simplifié de développement. L&#39;AEM en tant que Cloud Service [Console développeur](development-guidelines.md#crxde-lite-and-developer-console) est utilisé pour générer les jetons nécessaires au processus d&#39;authentification.

## Flux serveur à serveur {#the-server-to-server-flow}

Un utilisateur doté du rôle d’administrateur peut générer un jeton porteur JWT, qui doit être installé sur le serveur et doit être traité avec soin comme une clé secrète. Le jeton porteur JWT doit être échangé avec IMS pour un jeton d&#39;accès, qui doit être inclus dans la demande d&#39;AEM en tant que Cloud Service.

Le flux serveur à serveur implique les étapes suivantes :

* Générer le jeton porteur JWT à partir de la console de développement
* Installez le jeton sur un serveur non AEM qui appelle AEM
* Échange du jeton porteur JWT pour un jeton d&#39;accès à l’aide des API IMS de Adobe
* Appel de l’API AEM

### Génération du jeton de garde JWT {#generating-the-jwt-bearer-token}

Les utilisateurs qui ont le rôle d’administrateur pour une organisation voient l’onglet intégrations dans la console de développement pour un environnement donné, ainsi que deux boutons. Cliquez sur le bouton **Obtenir les informations d’identification du service** pour générer la clé privée, le certificat et la configuration pour les niveaux d’auteur et de publication de l’environnement, quelle que soit la sélection de la capsule.

![Génération JWT](assets/JWTtoken3.png)

La sortie sera similaire à la suivante :

```
{
  "ok": true,
  "integration": {
    "imsEndpoint": "ims-na1.adobelogin.com",
    "metascopes": "ent_aem_cloud_sdk,ent_cloudmgr_sdk",
    "technicalAccount": {
      "clientId": "cm-p123-e1234",
      "clientSecret": "4AREDACTED17"
    },
    "email": "abcd@techacct.adobe.com",
    "id": "ABCDAE10A495E8C@techacct.adobe.com",
    "org": "1234@AdobeOrg",
    "privateKey": "-----BEGIN RSA PRIVATE KEY-----\r\REDACTED\r\n==\r\n-----END RSA PRIVATE KEY-----\r\n",
    "publicKey": "-----BEGIN CERTIFICATE-----\r\nREDACTED\r\n-----END CERTIFICATE-----\r\n"
  },
  "statusCode": 200
}
```

### Installer le jeton sur un serveur non AEM {#install-the-token-on-a-non-aem-server}

L’application non-AEM qui appelle AEM doit installer le jeton porteur JWT, en le traitant comme un secret.

### Échanger le jeton JWT pour un Jeton d&#39;accès {#exchange-the-jwt-token-for-an-access-token}

Incluez le jeton JWT dans un appel au service IMS de l’Adobe afin de récupérer un jeton d&#39;accès valide pendant 24 heures.

### Appel de l’API AEM {#calling-the-aem-api}

Effectuez les appels d’API serveur à serveur appropriés à un AEM en tant qu’environnement Cloud Service, y compris le jeton d&#39;accès dans l’en-tête. Pour l’en-tête &quot;Autorisation&quot;, utilisez la valeur `"Bearer <access_token>"`.

<!-- ### Code Samples {#code-samples}

https://git.corp.adobe.com/boston/skyline-api-client-lib (internal note: URL will change to public git repo before we publish) contains client libraries written in node.js that will exchange the JSON outputted by the developer console for an access token. -->

## Flux de développement {#developer-flow}

Les développeurs voudront probablement tester en utilisant une instance de développement de leur application non-AEM (exécutée sur leur ordinateur portable ou hébergée) qui envoie des requêtes à un AEM de développement en tant qu’environnement de développement Cloud Service. Cependant, comme les développeurs n’ont pas nécessairement accès au rôle d’administrateur à l’AEM en tant qu’environnement de développement Cloud Service, nous ne pouvons pas supposer qu’ils peuvent générer le porteur JWT décrit dans le flux serveur à serveur régulier. Ainsi, nous fournissons un mécanisme permettant à un développeur de générer directement un jeton d&#39;accès qui peut être utilisé dans les demandes à AEM en tant qu&#39;environnements Cloud Service auxquels ils ont accès. Pour plus d&#39;informations sur les autorisations requises pour utiliser l&#39;AEM en tant que console de développement Cloud Service, consultez la [documentation destinée aux développeurs](/help/implementing/developing/introduction/development-guidelines.md).

>[!NOTE]
>
>Le jeton est valide pendant 24 heures après quoi il doit être régénéré selon la même méthode.

Les développeurs peuvent utiliser ce jeton pour passer des appels de leur application de test non-AEM à un AEM en tant qu’environnement Cloud Service. En règle générale, le développeur utilise ce jeton avec l’application non-AEM sur son propre ordinateur portable. En outre, l’AEM en tant que Cloud est généralement un environnement hors production.

Le flux de développement comprend les étapes suivantes :

* Générer un jeton d&#39;accès à partir de la Console développeur
* Appelez l&#39;application AEM avec le jeton d&#39;accès.

Les développeurs peuvent également invoquer l’API pour un projet AEM exécuté sur leur ordinateur local, auquel cas un jeton d&#39;accès n’est pas nécessaire.

### Génération du Jeton d&#39;accès {#generating-the-access-token}

Cliquez sur le bouton **Obtenir le jeton de développement local** de la Console développeur pour générer un jeton d&#39;accès.

### Appelez ensuite l&#39;application AEM avec un Jeton d&#39;accès {#call-the-aem-application-with-an-access-token}

Effectuez les appels d’API serveur à serveur appropriés de l’application non-AEM à un AEM en tant qu’environnement Cloud Service, y compris le jeton d&#39;accès dans l’en-tête. Pour l’en-tête &quot;Autorisation&quot;, utilisez la valeur `"Bearer <access_token>"`.

## Révocation du jeton JWT Bearer {#jwt-bearer-token-revocation}

Veuillez envoyer une demande au service clientèle si le jeton porteur JWT doit être révoqué.