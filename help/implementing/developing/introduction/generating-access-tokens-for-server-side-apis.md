---
title: Génération de jetons d’accès pour les API côté serveur
description: Découvrez comment faciliter la communication entre un serveur tiers et AEM as a Cloud Service en générant un jeton JWT sécurisé
exl-id: 20deaf8f-328e-4cbf-ac68-0a6dd4ebf0c9
source-git-commit: d361ddc9a50a543cd1d5f260c09920c5a9d6d675
workflow-type: tm+mt
source-wordcount: '2090'
ht-degree: 40%

---

# Génération de jetons d’accès pour les API côté serveur {#generating-access-tokens-for-server-side-apis}

Certaines architectures reposent sur des appels à AEM as a Cloud Service à l’aide d’une application hébergée sur un serveur en dehors de l’infrastructure AEM. Il peut s’agir, par exemple, d’une application mobile qui appelle un serveur, puis effectue des requêtes d’API auprès d’AEM as a Cloud Service.

Le flux de serveur à serveur est décrit ci-dessous, ainsi qu’un flux simplifié de développement. La [Developer Console](development-guidelines.md#crxde-lite-and-developer-console) d’AEM as a Cloud Service sert à générer les jetons nécessaires au processus d’authentification.

<!-- Alexandru: hiding this until the tutorials reflect the new UI

>[!NOTE]
>
>In addition to this documentation, you can also consult the tutorials on [Token-based authentication for AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=en#authentication) and [Getting a Login Token for Integrations](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-getting-login-token-integrations.html). -->

## Flux de serveur à serveur {#the-server-to-server-flow}

Les utilisateurs disposant d’un rôle d’administrateur d’organisation IMS et qui sont membres du profil produit Utilisateurs AEM ou Administrateurs AEM sur l’auteur AEM peuvent générer un ensemble d’informations d’identification provenant d’un groupe d’utilisateurs as a Cloud Service. Chaque information d’identification est une charge utile JSON qui comprend un certificat (la clé publique), une clé privée et un compte technique constitué d’un `clientId` et `clientSecret`. Ces informations d’identification peuvent ensuite être récupérées par un utilisateur disposant du rôle d’administrateur d’environnement as a Cloud Service AEM et doivent être installées sur un serveur non AEM et traitées avec précaution comme une clé secrète. Ce fichier de format JSON contient toutes les données requises pour l’intégration à une API AEM as a Cloud Service. Les données sont utilisées pour créer un jeton JWT signé, qui est échangé avec les services Identity Management (IMS) d’Adobe contre un jeton d’accès IMS. Ce jeton d’accès peut ensuite être utilisé comme jeton d’authentification du porteur pour adresser des requêtes à AEM as a Cloud Service. Le certificat figurant dans les informations d’identification expire par défaut après un an, mais il peut être actualisé si nécessaire, comme décrit [here](#refresh-credentials).

Le flux de serveur à serveur comprend les étapes suivantes :

* Récupérer les informations d’identification sur AEM as a Cloud Service à partir de Developer Console
* Installez les informations d’identification d’AEM as a Cloud Service sur un serveur non AEM qui effectue des appels à l’AEM
* Générer un jeton JWT et l’échanger contre un jeton d’accès à l’aide des API IMS d’Adobe
* Appeler l’API AEM avec le jeton d’accès servant de jeton d’authentification du porteur
* Définir les autorisations appropriées pour l’utilisateur du compte technique dans l’environnement AEM

### Extraction des informations d’identification AEM as a Cloud Service {#fetch-the-aem-as-a-cloud-service-credentials}

Les utilisateurs ayant accès à AEM console de développement as a Cloud Service voient l’onglet Intégrations dans Developer Console pour un environnement donné. Un utilisateur disposant du rôle d’administrateur d’environnement as a Cloud Service AEM peut créer, afficher ou gérer des informations d’identification.

Cliquer **Créer un compte technique**, un ensemble d’informations d’identification est créé. Il comprend l’identifiant client, le secret client, la clé privée, le certificat et la configuration pour les niveaux de création et de publication de l’environnement, quelle que soit la sélection de capsule.

![Créer un nouveau compte technique](/help/implementing/developing/introduction/assets/s2s-createtechaccount.png)

Un nouvel onglet du navigateur s’ouvre, affichant les informations d’identification. Vous pouvez utiliser cette vue pour télécharger les informations d’identification en appuyant sur l’icône de téléchargement située à côté du titre du statut :

![Télécharger des informations d’identification](/help/implementing/developing/introduction/assets/s2s-credentialdownload.png)

Une fois les informations d’identification créées, elles s’affichent sous l’onglet **Comptes techniques** dans la section **Intégrations** :

![Afficher les informations d’identification](/help/implementing/developing/introduction/assets/s2s-viewcredentials.png)

Les utilisateurs ou utilisatrices peuvent ensuite afficher les informations d’identification à l’aide de l’action Afficher. En outre, comme décrit plus loin dans l’article, les utilisateurs peuvent modifier les informations d’identification du même compte technique. Pour ce faire, ils créent une clé privée ou un certificat, dans les cas où le certificat doit être renouvelé ou révoqué.

Les utilisateurs disposant du rôle d’administrateur d’environnement as a Cloud Service AEM peuvent ultérieurement créer des informations d’identification pour des comptes techniques supplémentaires. Cette fonctionnalité est utile lorsque différentes API ont des exigences d’accès différentes. Par exemple, lecture et lecture-écriture.

>[!NOTE]
>
>Les clients peuvent créer jusqu’à dix comptes techniques, y compris ceux qui ont déjà été supprimés.

>[!IMPORTANT]
>
>Un administrateur de l’organisation IMS (généralement le même utilisateur qui a configuré l’environnement au moyen de Cloud Manager), qui est également membre du profil produit Utilisateurs AEM ou Administrateurs AEM sur l’auteur AEM, doit d’abord accéder à Developer Console. Cliquez ensuite sur **Créer un compte technique** pour que les informations d’identification soient générées et récupérées ultérieurement par un utilisateur disposant d’autorisations d’administrateur pour l’environnement as a Cloud Service AEM. Si l’administrateur de l’organisation IMS n’a pas encore créé le compte technique, un message l’informe qu’il a besoin du rôle Administrateur de l’organisation IMS.

### Installation des informations d’identification du service AEM sur un serveur non AEM {#install-the-aem-service-credentials-on-a-non-aem-server}

L’application qui appelle AEM doit pouvoir accéder aux informations d’identification d’AEM as a Cloud Service, les considérant comme un secret.

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

>[!NOTE]
>S’il existe plusieurs informations d’identification, veillez à référencer le fichier json approprié pour l’appel API à AEM qui sera appelé ultérieurement.

### Appel de l’API AEM {#calling-the-aem-api}

Effectuez les appels d’API appropriés de serveur à serveur auprès d’AEM as a Cloud Service, y compris le jeton d’accès dans l’en-tête. Pour l’en-tête « Authorization », utilisez la valeur `"Bearer <access_token>"`. Par exemple, en utilisant `curl` :

```curlc
curl -H "Authorization: Bearer <your_ims_access_token>" https://author-p123123-e23423423.adobeaemcloud.com/content/dam.json
```

### Définissez les autorisations appropriées pour l’utilisateur du compte technique dans AEM {#set-the-appropriate-permissions-for-the-technical-account-user-in-aem}

Tout d’abord, un nouveau profil de produit doit être créé dans Adobe Admin Console.

1. Accédez à Adobe Admin Console depuis la page [https://adminconsole.adobe.com/](https://adminconsole.adobe.com/).
1. Cliquez sur le lien **Gérer** sous la colonne **Produits et services** sur la gauche.
1. Sélectionnez **AEM as a Cloud Service**.
1. Appuyez sur le bouton **Nouveau profil.**

   ![Nouveau profil](/help/implementing/developing/introduction/assets/s2s-newproductprofile.png)

1. Donnez un nom au profil et appuyez sur **Enregistrer**.

   ![Enregistrer le profil](/help/implementing/developing/introduction/assets/s2s-saveprofile.png)

1. Sélectionnez le profil que vous avez créé dans la liste des profils.
1. Sélectionner **Ajouter un utilisateur**.

   ![Ajouter un utilisateur](/help/implementing/developing/introduction/assets/s2s-addusers.png)

1. Ajoutez le compte technique que vous avez créé (dans ce cas `84b2c3a2-d60a-40dc-84cb-e16b786c1673@techacct.adobe.com`), puis cliquez sur **Enregistrer**.

   ![Ajouter un compte technique](/help/implementing/developing/introduction/assets/s2s-addtechaccount.png)

1. Patientez 10 minutes pour que les modifications prennent effet et effectuez un appel API vers AEM avec un jeton d’accès généré à partir des nouvelles informations d’identification. En tant que commande cURL, il serait représenté comme suit :

   `curl -H "Authorization: Bearer <access_token>" https://author-pXXXXX-eXXXXX.adobeaemcloud.net/content/dam.json `


Après avoir effectué l’appel API, le profil de produit s’affiche en tant que groupe d’utilisateurs dans l’instance d’auteur as a Cloud Service AEM, avec le compte technique approprié en tant que membre de ce groupe.

Pour vérifier ces informations, procédez comme suit :

1. Connectez-vous à l’instance d’auteur.
1. Accédez à **Outils** > **Sécurité**, puis cliquez sur le bouton **Groupes** carte.
1. Localisez le nom du profil que vous avez créé dans la liste des groupes et cliquez dessus :

   ![Profil de groupe](/help/implementing/developing/introduction/assets/s2s-groupprofile.png)

1. Dans la fenêtre suivante, aller dans l’onglet **Membres** et vérifier si le compte technique y est correctement répertorié :

   ![Onglet Membres](/help/implementing/developing/introduction/assets/s2s-techaccountmembers.png)


Vous pouvez également vérifier que le compte technique apparaît dans la liste de l’utilisateur en procédant comme suit sur l’instance de création :

1. Accédez à **Outils** > **Sécurité** > **Utilisateurs**.
1. Vérifiez que votre compte technique est la liste des utilisateurs et sélectionnez-la.
1. Cliquez sur le bouton **Groupes** afin que vous puissiez vérifier que l’utilisateur fait partie du groupe correspondant à votre profil de produit. Cet utilisateur est également membre d’une poignée d’autres groupes, y compris Contributeurs :

   ![Appartenance à un groupe](/help/implementing/developing/introduction/assets/s2s-groupmembership.png)

>[!NOTE]
>
>Avant la mi-2023, avant qu’il ne soit possible de créer plusieurs informations d’identification, les clients n’étaient pas invités à créer un profil de produit dans Adobe Admin Console. Ainsi, le compte technique n’était pas associé à un groupe autre que &quot;Contributeurs&quot; dans l’instance as a Cloud Service AEM. Par souci de cohérence, il est recommandé, pour ce compte technique, de créer un profil de produit dans Adobe Admin Console comme décrit ci-dessus, puis d’ajouter le compte technique existant à ce groupe.

<u>**Définir les autorisations de groupe appropriées**</u>

Enfin, configurez le groupe avec les autorisations nécessaires pour pouvoir appeler ou verrouiller vos API de manière appropriée.

1. Connectez-vous à l’instance d’auteur appropriée et accédez à **Paramètres** > **Sécurité** > **Autorisations**
1. Recherchez le nom du groupe correspondant au profil de produit dans le volet de gauche (dans ce cas, les API en lecture seule) et sélectionnez-le :

   ![Rechercher un groupe](/help/implementing/developing/introduction/assets/s2s-searchforgroup.png)

1. Cliquez sur le bouton Modifier dans la fenêtre suivante :

   ![Modifier les autorisations](/help/implementing/developing/introduction/assets/s2s-editpermissions.png) 

1. Modifiez les autorisations de manière appropriée, puis cliquez sur **Enregistrer**

   ![Confirmer la modification des autorisations](/help/implementing/developing/introduction/assets/s2s-confirmeditpermissions.png)

>[!INFO]
>
>En savoir plus sur Adobe Identity Management System (IMS) et les utilisateurs et groupes d’AEM. Voir [documentation](/help/security/ims-support.md).

## Flux de développement {#developer-flow}

Les développeurs souhaitent probablement réaliser des tests à l’aide d’une instance de développement de leur application non AEM (s’exécutant sur leur ordinateur portable ou hébergée) qui émet des requêtes vers un environnement de développement AEM as a Cloud Service. Cependant, comme les développeurs ne disposent pas nécessairement d’autorisations de rôle d’administrateur IMS, Adobe ne peut pas présumer qu’ils peuvent générer le porteur JWT décrit dans le flux serveur à serveur standard. Par conséquent, Adobe fournit un mécanisme permettant à un développeur de générer directement un jeton d’accès qui peut être utilisé dans les demandes aux environnements sur AEM auxquels il a accès.

Pour plus d’informations sur les autorisations requises pour utiliser la Developer Console dans AEM as a Cloud Service, consultez la [documentation destinée aux développeurs](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console).

>[!NOTE]
>
>Le jeton d’accès de développement local est valide pendant 24 heures au maximum, après quoi il doit être régénéré selon la même méthode.

Les développeurs peuvent utiliser ce jeton pour émettre des appels depuis leur application de test non AEM vers l’environnement AEM as a Cloud Service. En règle générale, le développeur utilise ce jeton avec l’application non AEM sur son propre ordinateur portable. En outre, AEM as a Cloud Service est généralement un environnement distinct de la production.

Le flux de développement comprend les étapes suivantes :

* Générer un jeton d’accès à partir de la Developer Console
* Appeler l’application AEM à l’aide du jeton d’accès

Les développeurs peuvent également effectuer des appels d’API vers un projet AEM exécuté sur leur ordinateur local, auquel cas un jeton d’accès n’est pas nécessaire.

### Génération du jeton d’accès {#generating-the-access-token}

1. Accédez au **Jeton local** sous **Intégrations**.
1. Cliquez sur **Obtention du jeton de développement local** dans Developer Console afin de générer un jeton d’accès.

### Appelez ensuite l’application AEM à l’aide du jeton d’accès. {#call-the-aem-application-with-an-access-token}

Effectuez les appels d’API de serveur à serveur appropriés auprès de l’application non AEM vers un environnement AEM as a Cloud Service, y compris le jeton d’accès dans l’en-tête. Pour l’en-tête « Authorization », utilisez la valeur `"Bearer <access_token>"`.

## Actualisation des informations d’identification {#refresh-credentials}

Par défaut, les informations d’identification sur AEM as a Cloud Service expirent au bout d’un an. Pour assurer la continuité du service, les développeurs ont la possibilité d’actualiser les informations d’identification, en prolongeant leur disponibilité pendant un an supplémentaire.

Pour obtenir cette extension d’actualisation, procédez comme suit :

* Utiliser le bouton **Ajouter un certificat** sous **Intégrations** - **Comptes techniques** dans la Developer Console, tel qu’indiqué ci-dessous.

  ![Actualisation des informations d’identification](/help/implementing/developing/introduction/assets/s2s-credentialrefresh.png)

* Après avoir appuyé sur le bouton, un ensemble d’informations d’identification contenant un nouveau certificat est généré. Installez les nouvelles informations d’identification sur votre serveur hors AEM et assurez-vous que la connectivité est correcte, sans supprimer les anciennes informations d’identification.
* Assurez-vous que les nouvelles informations d’identification sont utilisées à la place des anciennes lors de la génération du jeton d’accès.
* Vous pouvez éventuellement révoquer (puis supprimer) le certificat précédent afin qu’il ne puisse plus être utilisé pour s’authentifier avec AEM as a Cloud Service.

## Révocation des informations d’identification {#credentials-revocation}

Si la clé privée est compromise, vous devez créer des informations d’identification avec un nouveau certificat et une nouvelle clé privée. Une fois que votre application a utilisé les nouvelles informations d’identification pour générer des jetons d’accès, vous pouvez révoquer et supprimer les anciens certificats en procédant comme suit :

1. Tout d’abord, ajoutez la nouvelle clé. Cette clé génère des informations d’identification avec une nouvelle clé privée et un nouveau certificat. La nouvelle clé privée est marquée dans l’interface utilisateur comme **current** et est donc utilisé pour toutes les nouvelles informations d’identification de ce compte technique. Les informations d’identification associées aux anciennes clés privées restent valides jusqu’à leur révocation. Pour obtenir cette révocation, sélectionnez les trois points (**...**) sous votre compte technique actuel, puis sélectionnez **Ajout d’une clé privée**:

   ![Ajouter une clé privée](/help/implementing/developing/introduction/assets/s2s-addnewprivatekey.png)

1. Sélectionner **Ajouter** à l’invite suivante :

   ![Confirmer l’ajout d’une nouvelle clé privée](/help/implementing/developing/introduction/assets/s2s-addprivatekeyconfirm.png)

   Un nouvel onglet de navigation avec les nouvelles informations d’identification s’ouvre et l’interface utilisateur est mise à jour afin d’afficher à la fois les clés privées avec le nouveau marqué comme **current**:

   ![Clés privées dans l’interface utilisateur](/help/implementing/developing/introduction/assets/s2s-twokeys.png)

1. Installez les nouvelles informations d’identification sur le serveur non AEM et assurez-vous que la connectivité fonctionne comme prévu. Voir [Section Flux serveur à serveur](#the-server-to-server-flow) pour plus d’informations.
1. Révoquez l’ancien certificat en sélectionnant les trois points (**...**) à droite du certificat, et en sélectionnant **Révoquer**:

   ![Révoquer le certificat](/help/implementing/developing/introduction/assets/s2s-revokecert.png)

   Ensuite, confirmez la révocation dans l’invite suivante en appuyant sur le bouton **Révoquer** :

   ![Confirmation de révocation du certificat](/help/implementing/developing/introduction/assets/s2s-revokecertificateconfirmation.png)

1. Pour finir, supprimez le certificat compromis.
