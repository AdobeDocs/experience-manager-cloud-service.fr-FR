---
title: Générer des jetons d’accès pour les API côté serveur
description: Découvrez comment faciliter la communication entre un serveur tiers et AEM as a Cloud Service en générant un jeton JWT sécurisé
exl-id: 20deaf8f-328e-4cbf-ac68-0a6dd4ebf0c9
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 22216d2c045b79b7da13f09ecbe1d56a91f604df
workflow-type: tm+mt
source-wordcount: '2112'
ht-degree: 94%

---

# Générer des jetons d’accès pour les API côté serveur {#generating-access-tokens-for-server-side-apis}

Certaines architectures reposent sur des appels à AEM as a Cloud Service à l’aide d’une application hébergée sur un serveur en dehors de l’infrastructure AEM. Il peut s’agir, par exemple, d’une application mobile qui appelle un serveur, puis effectue des requêtes d’API auprès d’AEM as a Cloud Service.

Le flux de serveur à serveur est décrit ci-dessous, ainsi qu’un flux simplifié de développement. La [Developer Console](development-guidelines.md#crxde-lite-and-developer-console) d’AEM as a Cloud Service sert à générer les jetons nécessaires au processus d’authentification.

<!-- Alexandru: hiding this until the tutorials reflect the new UI

>[!NOTE]
>
>In addition to this documentation, you can also consult the tutorials on [Token-based authentication for AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html#authentication) and [Getting a Login Token for Integrations](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-getting-login-token-integrations.html). -->

## Flux de serveur à serveur {#the-server-to-server-flow}

Les personnes utilisatrices disposant d’un rôle d’administration d’organisation IMS et qui sont membres du profil produit d’utilisation ou d’administration AEM sur l’instance de création AEM peuvent générer un ensemble d’informations d’identification provenant d’AEM as a Cloud Service. Chaque information d’identification est une payload JSON qui comprend un certificat (la clé publique), une clé privée et un compte technique constitué d’un `clientId` et d’un `clientSecret`. Ces informations d’identification peuvent ensuite être récupérées par une personne utilisatrice disposant du rôle d’administration d’AEM as a Cloud Service. Elles doivent être installées sur un serveur non AEM et traitées avec précaution comme une clé secrète. Ce fichier de format JSON contient toutes les données requises pour l’intégration à une API AEM as a Cloud Service. Les données sont utilisées pour créer un jeton JWT signé, qui est échangé avec les services Identity Management (IMS) d’Adobe contre un jeton d’accès IMS. Ce jeton d’accès peut ensuite être utilisé comme jeton d’authentification du porteur pour adresser des requêtes à AEM as a Cloud Service. Par défaut, le certificat des informations d’identification expire après un an, mais celles-ci peuvent être actualisées si nécessaire. Voir [ Actualiser les informations d’identification ](#refresh-credentials).

Le flux de serveur à serveur comprend les étapes suivantes :

* Récupérer les informations d’identification AEM as a Cloud Service dans la Developer Console
* Installer les informations d’identification AEM as a Cloud Service sur un serveur non AEM qui effectue des appels à AEM
* Générer un jeton JWT et l’échanger contre un jeton d’accès à l’aide des API IMS d’Adobe
* Appeler l’API AEM avec le jeton d’accès servant de jeton d’authentification du porteur
* Définir les autorisations appropriées pour l’utilisateur du compte technique dans l’environnement AEM

### Extraction des informations d’identification AEM as a Cloud Service {#fetch-the-aem-as-a-cloud-service-credentials}

Les personnes utilisatrices ayant accès à la Developer Console dans AEM as a Cloud Service y voient l’onglet Intégrations correspondant à un environnement donné. Toute personne utilisatrice disposant du rôle d’administration d’environnement d’AEM as a Cloud Service peut créer, afficher ou gérer des informations d’identification.

Cliquez sur le bouton **Créer un compte technique** pour créer un ensemble d’informations d’identification, qui comprend l’ID client, le secret client, la clé privée, le certificat et la configuration pour les niveaux de création et de publication de l’environnement, quelle que soit la capsule choisie.

![Création d’un nouveau compte technique](/help/implementing/developing/introduction/assets/s2s-createtechaccount.png)

Un nouvel onglet du navigateur s’ouvre et affiche les informations d’identification. Vous pouvez utiliser cette vue pour télécharger les informations d’identification en appuyant sur l’icône de téléchargement située à côté du titre du statut :

![Télécharger des informations d’identification](/help/implementing/developing/introduction/assets/s2s-credentialdownload.png)

Une fois les informations d’identification créées, elles s’affichent sous l’onglet **Comptes techniques** dans la section **Intégrations** :

![Afficher les informations d’identification](/help/implementing/developing/introduction/assets/s2s-viewcredentials.png)

Les utilisateurs ou utilisatrices peuvent ensuite afficher les informations d’identification à l’aide de l’action Afficher. En outre, comme décrit plus loin dans l’article, les personnes utilisatrices peuvent modifier les informations d’identification du même compte technique. Pour ce faire, ils créent une clé privée ou un certificat dans les cas où le certificat doit être renouvelé ou révoqué.

Les personnes utilisatrices disposant du rôle d’administration d’environnement d’AEM as a Cloud Service peuvent ensuite créer des informations d’identification pour des comptes techniques supplémentaires. Cette fonctionnalité est utile lorsque plusieurs API ont des exigences d’accès différentes. Par exemple, lecture et lecture-écriture.

>[!NOTE]
>
>Les clientes et clients peuvent créer jusqu’à 10 comptes techniques, y compris ceux qui ont déjà été supprimés.

>[!IMPORTANT]
>
>Une personne administratrice de l’organisation IMS (généralement la même personne qui a configuré l’environnement au moyen de Cloud Manager), qui est également membre du profil produit d’utilisation ou d’administration AEM sur l’instance de création AEM, doit d’abord accéder à la Developer Console. Cliquez ensuite sur **Créer un compte technique** pour que les informations d’identification soient générées et récupérées ultérieurement par une personne utilisatrice disposant d’autorisations d’administration pour l’environnement AEM as a Cloud Service. Si la personne administratrice de l’organisation IMS n’a pas encore créé le compte technique, un message l’informe qu’elle a besoin du rôle d’administration de l’organisation IMS.

### Installer les informations d’identification du service AEM sur un serveur non AEM {#install-the-aem-service-credentials-on-a-non-aem-server}

L’application qui appelle AEM doit pouvoir accéder aux informations d’identification d’AEM as a Cloud Service en les traitant comme un secret.

### Générer un jeton JWT et l’échanger contre un jeton d’accès {#generate-a-jwt-token-and-exchange-it-for-an-access-token}

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

>[!NOTE]
>S’il existe plusieurs informations d’identification, veillez à indiquer le fichier json approprié pour l’appel API à AEM qui sera appelé ultérieurement.

### Appel de l’API AEM {#calling-the-aem-api}

Effectuez les appels d’API appropriés de serveur à serveur auprès d’AEM as a Cloud Service, y compris le jeton d’accès dans l’en-tête. Pour l’en-tête « Authorization », utilisez la valeur `"Bearer <access_token>"`. Par exemple, en utilisant `curl` :

```curlc
curl -H "Authorization: Bearer <your_ims_access_token>" https://author-p123123-e23423423.adobeaemcloud.com/content/dam.json
```

### Définissez les autorisations appropriées pour l’utilisateur du compte technique dans AEM {#set-the-appropriate-permissions-for-the-technical-account-user-in-aem}

Tout d’abord, un nouveau profil de produit doit être créé dans l’Adobe Admin Console.

1. Accédez à l’Adobe Admin Console depuis la page [https://adminconsole.adobe.com/](https://adminconsole.adobe.com/).
1. Cliquez sur le lien **Gérer** sous la colonne **Produits et services** sur la gauche.
1. Sélectionnez **AEM as a Cloud Service**.
1. Appuyez sur le bouton **Nouveau profil**.

   ![Nouveau profil](/help/implementing/developing/introduction/assets/s2s-newproductprofile.png)

1. Nommez le profil et appuyez sur **Enregistrer**.

   ![Enregistrement du profil](/help/implementing/developing/introduction/assets/s2s-saveprofile.png)

1. Sélectionnez le profil que vous venez de créer dans la liste des profils.
1. Sélectionnez **Ajouter un utilisateur**.

   ![Ajout d’un utilisateur ou d’une utilisatrice](/help/implementing/developing/introduction/assets/s2s-addusers.png)

1. Ajoutez le compte technique que vous venez de créer (dans ce cas `84b2c3a2-d60a-40dc-84cb-e16b786c1673@techacct.adobe.com`) et cliquez sur **Enregistrer**.

   ![Ajouter un compte technique](/help/implementing/developing/introduction/assets/s2s-addtechaccount.png)

1. Patientez 10 minutes pour que les modifications prennent effet et effectuez un appel API vers AEM avec un jeton d’accès généré à partir des nouvelles informations d’identification. En tant que commande cURL, il serait représenté comme suit :

   `curl -H "Authorization: Bearer <access_token>" https://author-pXXXXX-eXXXXX.adobeaemcloud.net/content/dam.json `


Une fois l’appel API effectué, le profil de produit s’affiche en tant que groupe d’utilisateurs et d’utilisatrices dans l’instance de création AEM as a Cloud Service, avec le compte technique approprié en tant que membre de ce groupe.

Pour vérifier ces informations, procédez comme suit :

1. Connectez-vous à l’instance de création.
1. Accédez à **Outils** > **Sécurité** et cliquez sur la vignette **Groupes**.
1. Localisez le nom du profil que vous avez créé dans la liste des groupes et cliquez dessus :

   ![Profil de groupe](/help/implementing/developing/introduction/assets/s2s-groupprofile.png)

1. Dans la fenêtre suivante, aller dans l’onglet **Membres** et vérifier si le compte technique y est correctement répertorié :

   ![Onglet Membres](/help/implementing/developing/introduction/assets/s2s-techaccountmembers.png)


Vous pouvez également vérifier que le compte technique apparaît dans la liste des utilisateurs et utilisatrices en procédant comme suit dans l’instance de création :

1. Accédez à **Outils** > **Sécurité** > **Utilisateurs**.
1. Vérifiez que votre compte technique est dans la liste des utilisateurs et utilisatrices, puis sélectionnez-le.
1. Cliquez sur l’onglet **Groupes** pour vérifier que l’utilisateur ou l’utilisatrice fait partie du groupe correspondant à votre profil de produit. Cet utilisateur ou cette utilisatrice est également membre d’autres groupes, y compris le groupe Contributeurs :

   ![Appartenance à un groupe](/help/implementing/developing/introduction/assets/s2s-groupmembership.png)

>[!NOTE]
>
>Avant la mi-2023, alors qu’il n’était pas possible de créer plusieurs informations d’identification, les clientes et les clients n’étaient pas invités à créer un profil de produit dans l’Adobe Admin Console. Ainsi, le compte technique n’était pas associé à un groupe autre que le groupe « Contributeurs » dans l’instance d’AEM as a Cloud Service. Par souci de cohérence, il est recommandé, pour ce compte technique, de créer un profil de produit dans l’Adobe Admin Console comme décrit ci-dessus, puis d’ajouter le compte technique existant à ce groupe.

<u>**Définir les autorisations de groupe appropriées**</u>

Configurez pour finir le groupe avec les autorisations appropriées nécessaires pour appeler ou verrouiller correctement vos API.

1. Connectez-vous à l’instance de création appropriée et accédez à **Paramètres** > **Sécurité** > **Autorisations**
1. Recherchez le nom du groupe correspondant au profil de produit dans le volet de gauche (dans ce cas, API en lecture seule) et sélectionnez-le :

   ![Rechercher un groupe](/help/implementing/developing/introduction/assets/s2s-searchforgroup.png)

1. Cliquez sur le bouton Modifier dans la fenêtre suivante :

   ![Modifier les autorisations](/help/implementing/developing/introduction/assets/s2s-editpermissions.png) 

1. Modifiez les autorisations de manière appropriée, puis cliquez sur **Enregistrer**

   ![Confirmer la modification des autorisations](/help/implementing/developing/introduction/assets/s2s-confirmeditpermissions.png)

>[!INFO]
>
>En savoir plus sur le système Adobe Identity Management (IMS) et les utilisateurs, utilisatrices et groupes d’AEM. Voir la [documentation](/help/security/ims-support.md).

## Flux de développement {#developer-flow}

Les personnes chargées du développement voudront probablement effectuer des tests en utilisant une instance de développement de leur application non AEM (exécutée sur leur ordinateur portable ou hébergée). Cette application adresse des requêtes à un environnement de développement AEM as a Cloud Service. Cependant, comme les personnes chargées du développement ne disposent pas nécessairement d’autorisations d’administration IMS, Adobe ne peut pas supposer qu’elles peuvent effectuer une génération du jeton porteur JWT décrite pour le flux régulier de serveur à serveur. Aussi, Adobe fournit un mécanisme permettant à une personne chargée du développement de générer directement un jeton d’accès utilisable dans les requêtes adressées aux environnements AEM as a Cloud Service auxquels ils ont accès.

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

1. Accédez au **Jeton local** sous **Intégrations**.
1. Cliquez sur **Obtenir le jeton de développement local** dans la Developer Console afin de générer un jeton d’accès.

### Appelez ensuite l’application AEM à l’aide du jeton d’accès. {#call-the-aem-application-with-an-access-token}

Effectuez les appels d’API de serveur à serveur appropriés auprès de l’application non AEM vers un environnement AEM as a Cloud Service, y compris le jeton d’accès dans l’en-tête. Pour l’en-tête « Authorization », utilisez la valeur `"Bearer <access_token>"`.

## Actualisation des informations d’identification {#refresh-credentials}

Par défaut, les informations d’identification sur AEM as a Cloud Service expirent au bout d’un an. Pour assurer la continuité du service, les personnes chargées du développement ont la possibilité d’actualiser les informations d’identification, ce qui prolonge leur disponibilité d’une année supplémentaire.

Pour obtenir cette extension d’actualisation, procédez comme suit :

* Utiliser le bouton **Ajouter un certificat** sous **Intégrations** - **Comptes techniques** dans la Developer Console, tel qu’indiqué ci-dessous.

  ![Actualisation des informations d’identification](/help/implementing/developing/introduction/assets/s2s-credentialrefresh.png)

* Une fois que vous avez appuyé sur le bouton, un ensemble d’informations d’identification avec un nouveau certificat est généré. Installez les nouvelles informations d’identification sur votre serveur hors AEM et assurez-vous que la connectivité est correcte, sans supprimer les anciennes informations d’identification.
* Assurez-vous que les nouvelles informations d’identification sont utilisées à la place des anciennes lors de la génération du jeton d’accès.
* Vous pouvez éventuellement révoquer (puis supprimer) le certificat précédent afin qu’il ne puisse plus être utilisé pour s’authentifier avec AEM as a Cloud Service.

## Révocation des informations d’identification {#credentials-revocation}

Si la clé privée est compromise, vous devez créer des informations d’identification avec un nouveau certificat et une nouvelle clé privée. Une fois que votre application a utilisé les nouvelles informations d’identification pour générer des jetons d’accès, vous pouvez révoquer et supprimer les anciens certificats en procédant comme suit :

1. Tout d’abord, ajoutez la nouvelle clé. Cela génère des informations d’identification avec une nouvelle clé privée et un nouveau certificat. La nouvelle clé privée est marquée dans l’interface utilisateur comme **actuelle** et sera dorénavant utilisée pour toutes les nouvelles informations d’identification de ce compte technique. Les informations d’identification associées aux anciennes clés privées restent valides jusqu’à leur révocation. Pour ce faire, sélectionnez les points de suspension (**...**) sous votre compte technique actuel et sélectionnez **Ajouter une clé privée** :

   ![Ajout d’une clé privée](/help/implementing/developing/introduction/assets/s2s-addnewprivatekey.png)

1. Sélectionnez **Ajouter** au prompt suivant :

   ![Confirmation de l’ajout d’une nouvelle clé privée](/help/implementing/developing/introduction/assets/s2s-addprivatekeyconfirm.png)

   Un nouvel onglet de navigation avec les nouvelles informations d’identification s’ouvre et l’interface utilisateur est mise à jour afin d’afficher les deux clés privées, la nouvelle clé étant marquée comme **actuelle** :

   ![Clés privées dans l’interface utilisateur](/help/implementing/developing/introduction/assets/s2s-twokeys.png)

1. Installez les nouvelles informations d’identification sur le serveur non AEM et assurez-vous que la connectivité fonctionne comme prévu. Consultez la [section Flux serveur à serveur](#the-server-to-server-flow) pour plus d’informations.
1. Révoquez l’ancien certificat en sélectionnant les points de suspension (**...**) à droite du certificat, et en sélectionnant **Révoquer** :

   ![Révoquer le certificat](/help/implementing/developing/introduction/assets/s2s-revokecert.png)

   Ensuite, confirmez la révocation dans le prompt en appuyant sur le bouton **Révoquer** :

   ![Confirmation de révocation du certificat](/help/implementing/developing/introduction/assets/s2s-revokecertificateconfirmation.png)

1. Pour finir, supprimez le certificat compromis.
