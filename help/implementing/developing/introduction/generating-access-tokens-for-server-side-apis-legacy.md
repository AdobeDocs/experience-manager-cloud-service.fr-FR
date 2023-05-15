---
title: Génération de jetons d’accès pour les API côté serveur (héritées)
description: Découvrez comment faciliter la communication entre un serveur tiers et AEM as a Cloud Service en générant un jeton JWT sécurisé
hidefromtoc: true
exl-id: 6561870c-cbfe-40ef-9efc-ea75c88c4ed7
source-git-commit: 98eff568686c72c626d2bf77d82e8c3f224eda42
workflow-type: tm+mt
source-wordcount: '1360'
ht-degree: 55%

---

# Génération de jetons d’accès pour les API côté serveur (héritées) {#generating-access-tokens-for-server-side-apis-legacy}

Certaines architectures reposent sur des appels à AEM as a Cloud Service à l’aide d’une application hébergée sur un serveur en dehors de l’infrastructure AEM. Il peut s’agir, par exemple, d’une application mobile qui appelle un serveur, puis effectue des requêtes d’API auprès d’AEM as a Cloud Service.

Le flux de serveur à serveur est décrit ci-dessous, ainsi qu’un flux simplifié de développement. La [Developer Console](development-guidelines.md#crxde-lite-and-developer-console) d’AEM as a Cloud Service sert à générer les jetons nécessaires au processus d’authentification.

<!-- ERROR: Not Found (HTTP error 404)
>[!NOTE]
>
>In addition to this documentation, you can also consult the tutorials on [Token-based authentication for AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=en#authentication) and [Getting a Login Token for Integrations](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-getting-login-token-integrations.html). -->

## Flux de serveur à serveur {#the-server-to-server-flow}

Un utilisateur disposant d’un rôle d’administrateur d’organisation IMS et qui est également membre du profil produit Utilisateurs AEM ou Administrateurs AEM sur le service de création AEM, peut générer des informations d’identification d’AEM as a Cloud Service. Ces informations d’identification peuvent ensuite être récupérées par un utilisateur disposant du rôle d’administrateur d’environnement as a Cloud Service AEM. Elles doivent être installées sur le serveur et doivent être traitées avec précaution comme une clé secrète. Ce fichier de format JSON contient toutes les données requises pour l’intégration avec une API AEM as a Cloud Service. Les données sont utilisées pour créer un jeton JWT signé, qui est échangé auprès d’IMS contre un jeton d’accès IMS. Ce jeton d’accès peut ensuite être utilisé comme jeton d’authentification du porteur pour adresser des requêtes à AEM as a Cloud Service. Par défaut, les informations d’identification expirent après un an, mais elles peuvent être actualisées si nécessaire, comme décrit [ici](#refresh-credentials).

Le flux de serveur à serveur comprend les étapes suivantes :

* Récupérer les informations d’identification pour AEM as a Cloud Service à partir de Developer Console
* Installez les informations d’identification d’AEM as a Cloud Service sur un serveur non AEM qui effectue des appels à l’AEM
* Générer un jeton JWT et l’échanger contre un jeton d’accès à l’aide des API IMS d’Adobe
* Appeler l’API AEM avec le jeton d’accès servant de jeton d’authentification du porteur
* Définir les autorisations appropriées pour l’utilisateur du compte technique dans l’environnement AEM

### Extraction des informations d’identification AEM as a Cloud Service {#fetch-the-aem-as-a-cloud-service-credentials}

Les utilisateurs ayant accès à AEM console de développement as a Cloud Service voient l’onglet Intégrations dans Developer Console pour un environnement donné et deux boutons. Un utilisateur disposant du rôle d’administrateur d’environnement as a Cloud Service AEM peut cliquer sur le bouton **Générer les informations d’identification du service** pour générer et afficher le fichier json des informations d’identification du service. Le fichier json contient toutes les informations requises pour le serveur non AEM, y compris l’ID client, le secret client, la clé privée, le certificat et la configuration pour les niveaux de création et de publication de l’environnement, quelle que soit la sélection de la capsule.

![Génération JWT](assets/JWTtoken3.png)

La sortie est similaire à ce qui suit :

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

Une fois générées, les informations d’identification peuvent être récupérées ultérieurement en appuyant sur la touche **Obtention des informations d’identification du service** au même emplacement.

>[!IMPORTANT]
>
>Un administrateur de l’organisation IMS, généralement l’utilisateur qui a configuré l’environnement au moyen de Cloud Manager, qui doit également être membre du profil produit Utilisateurs AEM ou Administrateurs sur l’auteur AEM, accède à Developer Console. Ils doivent alors cliquer sur le bouton **Générer les informations d’identification du service** afin que les informations d’identification soient générées et récupérées ultérieurement par un utilisateur disposant d’autorisations d’administrateur pour l’environnement as a Cloud Service AEM. Si l’administrateur de l’organisation IMS n’a pas effectué cette tâche, un message l’informe qu’il a besoin du rôle Administrateur de l’organisation IMS.

### Installation des informations d’identification du service AEM sur un serveur non AEM {#install-the-aem-service-credentials-on-a-non-aem-server}

L’application non-AEM qui appelle AEM doit pouvoir accéder aux informations d’identification de l’as a Cloud Service, les considérant comme un secret.

### Génération d’un jeton JWT et échange contre un jeton d’accès  {#generate-a-jwt-token-and-exchange-it-for-an-access-token}

Utilisez les informations d’identification pour créer un jeton JWT dans un appel au service IMS d’Adobe afin de récupérer un jeton d’accès, qui est valide pendant 24 heures.

Il est possible d’échanger les informations d’identification d’AEM CS Service contre un jeton d’accès à l’aide de bibliothèques clientes conçues à cet effet. Ces bibliothèques clientes sont disponibles dans le [référentiel public GitHub d’Adobe](https://github.com/adobe/aemcs-api-client-lib). Il contient des instructions plus détaillées et les informations les plus récentes.

```
/*jshint node:true */
"use strict";

const fs = require('fs');
const exchange = require("@adobe/aemcs-api-client-lib");

const jsonfile = "aemcs-service-credentials.json";

var config = JSON.parse(fs.readFileSync(jsonfile, 'utf8'));
exchange(config).then(accessToken => {
    // output the access token in json form including when it will expire.
    console.log(JSON.stringify(accessToken,null,2));
}).catch(e => {
    console.log("Failed to exchange for access token ",e);
});
```

Il est possible de procéder au même échange dans n’importe quel langage capable de générer un jeton JWT signé, dans un format correct, et d’appeler les API IMS Token Exchange.

Le jeton d’accès définit le moment où il expire, généralement 24 heures. Le référentiel git contient un exemple de code pour gérer un jeton d’accès et l’actualiser avant son expiration.

### Appel de l’API AEM {#calling-the-aem-api}

Effectuez les appels d’API appropriés de serveur à serveur auprès d’AEM as a Cloud Service, y compris le jeton d’accès dans l’en-tête. Pour l’en-tête « Authorization », utilisez la valeur `"Bearer <access_token>"`. Par exemple, en utilisant `curl` :

```curlc
curl -H "Authorization: Bearer <your_ims_access_token>" https://author-p123123-e23423423.adobeaemcloud.com/content/dam.json
```

### Définissez les autorisations appropriées pour l’utilisateur du compte technique dans AEM {#set-the-appropriate-permissions-for-the-technical-account-user-in-aem}

Une fois l’utilisateur du compte technique créé dans AEM (survient après la première demande avec le jeton d’accès correspondant), l’utilisateur du compte technique doit disposer des autorisations appropriées. **in** AEM.

Par défaut, sur le service AEM Author, l’utilisateur de compte technique est ajouté au groupe d’utilisateurs Contributeurs qui fournit des AEM d’accès en lecture.

Il est possible de configurer de manière plus détaillée les autorisations de cet utilisateur de compte technique AEM à l’aide des méthodes habituelles.

## Flux de développement {#developer-flow}

Les développeurs doivent tester à l’aide d’une instance de développement de leur application non AEM (s’exécutant sur leur ordinateur portable ou hébergée) qui effectue des requêtes vers un environnement de développement AEM as a Cloud Service. Cependant, comme les développeurs ne disposent pas nécessairement d’autorisations de rôle d’administrateur IMS, Adobe ne peut pas présumer qu’ils peuvent générer le porteur JWT décrit dans le flux serveur à serveur standard. Par conséquent, Adobe fournit un mécanisme permettant à un développeur de générer directement un jeton d’accès qui peut être utilisé dans les demandes à un environnement as a Cloud Service auquel il a accès.

Pour plus d’informations sur les autorisations requises pour utiliser la Developer Console dans AEM as a Cloud Service, consultez la [documentation destinée aux développeurs](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console).

>[!NOTE]
Le jeton d’accès de développement local est valide pendant 24 heures au maximum, après quoi il doit être régénéré selon la même méthode.

Les développeurs peuvent utiliser ce jeton pour émettre des appels depuis leur application de test non AEM vers l’environnement AEM as a Cloud Service. En règle générale, le développeur utilise ce jeton avec l’application non AEM sur son propre ordinateur portable. En outre, AEM as a Cloud Service est généralement un environnement distinct de la production.

Le flux de développement comprend les étapes suivantes :

* Générer un jeton d’accès à partir de la Developer Console
* Appeler l’application AEM à l’aide du jeton d’accès

Les développeurs peuvent également effectuer des appels d’API vers un projet AEM exécuté sur leur ordinateur local, auquel cas un jeton d’accès n’est pas nécessaire.

### Génération du jeton d’accès {#generating-the-access-token}

Pour générer un jeton d’accès, dans Developer Console, cliquez sur **Obtention du jeton de développement local**.

### Appelez ensuite l’application AEM à l’aide du jeton d’accès {#call-the-aem-application-with-an-access-token}

Effectuez les appels d’API de serveur à serveur appropriés auprès de l’application non AEM vers un environnement AEM as a Cloud Service, y compris le jeton d’accès dans l’en-tête. Pour l’en-tête « Authorization », utilisez la valeur `"Bearer <access_token>"`.

## Actualisation des informations d’identification {#refresh-credentials}

Par défaut, les informations d’identification sur AEM as a Cloud Service expirent au bout d’un an. Pour assurer la continuité du service, les développeurs ont la possibilité d’actualiser les informations d’identification, en prolongeant leur disponibilité pendant un an supplémentaire. Utilisation **Actualiser les informations d’identification du service** de la **Intégrations** dans Developer Console, comme illustré ci-dessous.

![Actualisation des informations d’identification](assets/credential-refresh.png)

En appuyant sur ce bouton, vous générez un ensemble d’informations d’identification. Vous pouvez mettre à jour votre stockage secret avec les nouvelles informations d’identification et vérifier qu’elles fonctionnent normalement.

>[!NOTE]
Après avoir cliqué sur le bouton **Refresh Service Credentials** (Actualiser les informations d’identification du service), les anciennes informations d’identification restent enregistrées jusqu’à leur expiration, mais seul le jeu le plus récent est visible à tout moment à partir de la Developer Console.

## Révocation des informations d’identification du service {#service-credentials-revocation}

Si les informations d’identification doivent être révoquées, vous devez envoyer une demande au service clientèle en procédant comme suit :

1. Désactivez l’utilisateur du compte technique pour Adobe Admin Console dans l’interface utilisateur :
   * Dans Cloud Manager, appuyez sur le bouton **...** en regard de votre environnement. Cette action ouvre la page des profils de produit
   * Cliquez maintenant sur le **Utilisateurs AEM** profile, pour afficher la liste des utilisateurs
   * Cliquez sur l’onglet **Informations d’identification d’API**, puis recherchez l’utilisateur de compte technique approprié et supprimez-le.
2. Contactez l’assistance clientèle et demandez que les informations d’identification du service pour cet environnement spécifique soient supprimées.
3. Enfin, vous pouvez générer à nouveau les informations d’identification, comme décrit dans cette documentation. Assurez-vous également que le nouvel utilisateur de compte technique créé dispose des autorisations appropriées.
