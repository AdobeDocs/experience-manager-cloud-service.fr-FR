---
title: Générer des jetons d’accès pour les API côté serveur (hérité)
description: Découvrez comment faciliter la communication entre un serveur tiers et AEM as a Cloud Service en générant un jeton JWT sécurisé
hidefromtoc: true
exl-id: 6561870c-cbfe-40ef-9efc-ea75c88c4ed7
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 22216d2c045b79b7da13f09ecbe1d56a91f604df
workflow-type: tm+mt
source-wordcount: '1382'
ht-degree: 94%

---

# Générer des jetons d’accès pour les API côté serveur (hérité) {#generating-access-tokens-for-server-side-apis-legacy}

Certaines architectures reposent sur des appels à AEM as a Cloud Service à l’aide d’une application hébergée sur un serveur en dehors de l’infrastructure AEM. Il peut s’agir, par exemple, d’une application mobile qui appelle un serveur, puis effectue des requêtes d’API auprès d’AEM as a Cloud Service.

Le flux de serveur à serveur est décrit ci-dessous, ainsi qu’un flux simplifié de développement. La [Developer Console](development-guidelines.md#crxde-lite-and-developer-console) d’AEM as a Cloud Service sert à générer les jetons nécessaires au processus d’authentification.

<!-- ERROR: Not Found (HTTP error 404)
>[!NOTE]
>
>In addition to this documentation, you can also consult the tutorials on [Token-based authentication for AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=fr#authentication) and [Getting a Login Token for Integrations](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-getting-login-token-integrations.html). -->

## Flux de serveur à serveur {#the-server-to-server-flow}

Un utilisateur disposant d’un rôle d’administrateur d’organisation IMS et qui est également membre du profil produit Utilisateurs AEM ou Administrateurs AEM sur le service de création AEM, peut générer des informations d’identification d’AEM as a Cloud Service. Ces informations d’identification peuvent ensuite être récupérées par une personne utilisatrice disposant du rôle d’administration AEM as a Cloud Service. Elles doivent être installées sur le serveur et doivent être traitées avec précaution comme une clé secrète. Ce fichier de format JSON contient toutes les données requises pour l’intégration avec une API AEM as a Cloud Service. Les données sont utilisées pour créer un jeton JWT signé, qui est échangé auprès d’IMS contre un jeton d’accès IMS. Ce jeton d’accès peut ensuite être utilisé comme jeton d’authentification du porteur pour adresser des requêtes à AEM as a Cloud Service. Par défaut, les informations d’identification expirent après un an, mais elles peuvent être actualisées si nécessaire. Voir [Actualiser les informations d’identification](#refresh-credentials).

Le flux de serveur à serveur comprend les étapes suivantes :

* Récupérer les informations d’identification AEM as a Cloud Service dans la Developer Console
* Installer les informations d’identification AEM as a Cloud Service sur un serveur non AEM qui effectue des appels à AEM
* Générer un jeton JWT et l’échanger contre un jeton d’accès à l’aide des API IMS d’Adobe
* Appeler l’API AEM avec le jeton d’accès servant de jeton d’authentification du porteur
* Définir les autorisations appropriées pour l’utilisateur du compte technique dans l’environnement AEM

### Extraction des informations d’identification AEM as a Cloud Service {#fetch-the-aem-as-a-cloud-service-credentials}

Les personnes utilisatrices ayant accès à la Developer Console d’AEM as a Cloud Service y voient l’onglet Intégrations correspondant à un environnement donné, et deux boutons. Une personne utilisatrice disposant du rôle d’administration d’environnement AEM as a Cloud Service peut cliquer sur le bouton **Générer les informations d’identification du service** pour générer et afficher le fichier JSON des informations d’identification du service. Le fichier JSON contient toutes les informations requises pour le serveur non AEM, y compris l’ID client, le secret client, la clé privée, le certificat et la configuration pour les niveaux de création et de publication de l’environnement, quel que soit le pod choisi.

![Génération JWT](assets/JWTtoken3.png)

Le résultat ressemble à ce qui suit :

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

Une fois générées, les informations d’identification peuvent être récupérées ultérieurement en appuyant sur le bouton **Obtenir les informations d’identification du service** au même emplacement.

>[!IMPORTANT]
>
>Une personne administratrice de l’organisation IMS (généralement la même personne qui a configuré l’environnement au moyen de Cloud Manager), qui est également membre du profil produit d’utilisation ou d’administration AEM sur l’instance de création AEM, accède à la Developer Console. Elle doit alors cliquer sur le bouton **Générer les informations d’identification du service** afin que les informations d’identification soient générées et récupérées ultérieurement par une personne utilisatrice disposant d’autorisations d’administration pour l’environnement AEM as a Cloud Service. Si la personne administratrice de l’organisation IMS n’a pas effectué cette tâche, un message l’informera que le rôle d’administration de l’organisation IMS doit lui être attribué.

### Installer les informations d’identification du service AEM sur un serveur non AEM {#install-the-aem-service-credentials-on-a-non-aem-server}

L’application non AEM qui appelle AEM doit pouvoir accéder aux informations d’identification d’AEM as a Cloud Service en les traitant comme un secret.

### Génération d’un jeton JWT et échange contre un jeton d’accès  {#generate-a-jwt-token-and-exchange-it-for-an-access-token}

Utilisez les informations d’identification pour créer un jeton JWT lors d’un appel au service IMS d’Adobe afin de récupérer un jeton d’accès valide pendant 24 heures.

Les informations d’identification de service AEM CS peuvent être échangées contre un jeton d’accès à l’aide d’exemples de code conçus à cet effet. L’exemple de code est disponible à partir du référentiel GitHub public d’Adobe [&#128279;](https://github.com/adobe/aemcs-api-client-lib), qui contient des exemples de code que vous pouvez copier et adapter à vos propres projets. Notez que ce référentiel contient un exemple de code à titre de référence et n’est pas conservé en tant que dépendance de bibliothèque prête pour la production.

```
/*jshint node:true */
"use strict";

const fs = require('fs');
// Sample code adapted from Adobe's GitHub repository
const exchange = require("./your-local-aemcs-client"); // Copy and adapt the code from the GitHub repository

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

Le jeton d’accès définit le moment de son expiration, généralement au bout de 24 heures. Le référentiel git contient un exemple de code pour gérer un jeton d’accès et l’actualiser avant son expiration.

### Appel de l’API AEM {#calling-the-aem-api}

Effectuez les appels d’API appropriés de serveur à serveur auprès d’AEM as a Cloud Service, y compris le jeton d’accès dans l’en-tête. Pour l’en-tête « Authorization », utilisez la valeur `"Bearer <access_token>"`. Par exemple, en utilisant `curl` :

```curlc
curl -H "Authorization: Bearer <your_ims_access_token>" https://author-p123123-e23423423.adobeaemcloud.com/content/dam.json
```

### Définissez les autorisations appropriées pour l’utilisateur du compte technique dans AEM {#set-the-appropriate-permissions-for-the-technical-account-user-in-aem}

Une fois que la personne utilisatrice du compte technique est créée dans AEM (après la première demande avec le jeton d’accès correspondant), elle doit bénéficier d’autorisations correctes **dans** AEM.

Par défaut, pour le service de création AEM, la personne utilisatrice du compte technique est ajoutée au groupe d’utilisateurs Contributeurs qui fournit un accès en lecture à AEM.

Il est possible de configurer de manière plus détaillée les autorisations de cet utilisateur de compte technique AEM à l’aide des méthodes habituelles.

## Flux de développement {#developer-flow}

Les personnes chargées du développement doivent effectuer des tests en utilisant une instance de développement de leur application non AEM (exécutée sur leur ordinateur portable ou hébergée). Cette application adresse des requêtes à un environnement de développement AEM as a Cloud Service. Cependant, comme les personnes chargées du développement ne disposent pas nécessairement d’autorisations d’administration IMS, Adobe ne peut pas supposer qu’elles peuvent effectuer une génération du jeton porteur JWT décrite pour le flux régulier de serveur à serveur. Adobe fournit donc un mécanisme permettant à une personne chargée du développement de générer directement un jeton d’accès utilisable dans les requêtes adressées à un environnement AEM as a Cloud Service auquel elle a accès.

Pour plus d’informations sur les autorisations requises pour utiliser la Developer Console dans AEM as a Cloud Service, consultez la [documentation destinée aux développeurs](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console).

>[!NOTE]
>
>Le jeton d’accès de développement local est valide pendant 24 heures au maximum, après quoi il doit être régénéré selon la même méthode.

Les développeurs peuvent utiliser ce jeton pour émettre des appels depuis leur application de test non AEM vers l’environnement AEM as a Cloud Service. En règle générale, une personne chargée du développement utilise ce jeton avec l’application non AEM sur son propre ordinateur portable. En outre, AEM as a Cloud Service est généralement un environnement distinct de la production.

Le flux de développement comprend les étapes suivantes :

* Générer un jeton d’accès à partir de la Developer Console
* Appeler l’application AEM à l’aide du jeton d’accès

Les développeurs peuvent également effectuer des appels d’API vers un projet AEM exécuté sur leur ordinateur local, auquel cas un jeton d’accès n’est pas nécessaire.

### Génération du jeton d’accès {#generating-the-access-token}

Pour générer un jeton d’accès, cliquez sur **Obtenir le jeton de développement local** dans la Developer Console.

### Appelez ensuite l’application AEM à l’aide du jeton d’accès {#call-the-aem-application-with-an-access-token}

Effectuez les appels d’API de serveur à serveur appropriés auprès de l’application non AEM vers un environnement AEM as a Cloud Service, y compris le jeton d’accès dans l’en-tête. Pour l’en-tête « Authorization », utilisez la valeur `"Bearer <access_token>"`.

## Actualisation des informations d’identification {#refresh-credentials}

Par défaut, les informations d’identification AEM as a Cloud Service expirent au bout d’un an. Pour assurer la continuité du service, les développeurs et les développeuses ont la possibilité d’actualiser les informations d’identification, en prolongeant leur disponibilité pendant un an supplémentaire. Utilisez **Actualiser les informations d’identification du service** dans l’onglet **Intégrations** de la Developer Console, comme illustré ci-dessous.

![Actualisation des informations d’identification](assets/credential-refresh.png)

En appuyant sur ce bouton, vous générez un ensemble d’informations d’identification. Vous pouvez mettre à jour votre stockage secret avec les nouvelles informations d’identification et vérifier qu’elles fonctionnent normalement.

>[!NOTE]
>
> Après avoir cliqué sur le bouton **Refresh Service Credentials** (Actualiser les informations d’identification du service), les anciennes informations d’identification restent enregistrées jusqu’à leur expiration, mais seul le jeu le plus récent est visible à tout moment à partir de la Developer Console.

## Révocation des informations d’identification du service {#service-credentials-revocation}

Si les informations d’identification doivent être révoquées, vous devez soumettre une demande au service clientèle en procédant comme suit :

1. Désactivez l’utilisateur du compte technique pour Adobe Admin Console dans l’interface utilisateur :
   * Dans Cloud Manager, appuyez sur le bouton **...** en regard de votre environnement. Cette action ouvre la page des profils de produit
   * Cliquez maintenant sur le profil **Utilisateurs AEM** pour afficher une liste des utilisateurs et utilisatrices
   * Cliquez sur l’onglet **Informations d’identification d’API**, puis recherchez l’utilisateur de compte technique approprié et supprimez-le.
2. Contactez l’assistance clientèle et demandez que les informations d’identification du service pour cet environnement spécifique soient supprimées.
3. Enfin, vous pouvez générer à nouveau les informations d’identification, comme décrit dans cette documentation. Assurez-vous également que le nouvel utilisateur de compte technique créé dispose des autorisations appropriées.
