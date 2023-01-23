---
title: Génération de jetons d’accès pour les API côté serveur
description: Découvrez comment faciliter la communication entre un serveur tiers et AEM as a Cloud Service en générant un jeton JWT sécurisé
exl-id: 20deaf8f-328e-4cbf-ac68-0a6dd4ebf0c9
source-git-commit: 41458eb1fba12e8ef45a32d3bb6fc5dd732f78ec
workflow-type: tm+mt
source-wordcount: '2199'
ht-degree: 36%

---

# Génération de jetons d’accès pour les API côté serveur {#generating-access-tokens-for-server-side-apis}

>[!AVAILABILITY]
>
>Adobe est en train de déployer progressivement les nouvelles fonctionnalités de révocation d’informations d’identification et d’informations d’identification multiples décrites dans cet article. Si, en vérifiant l’onglet Intégrations de la console de développement d’AEM de votre entreprise, vous constatez que l’écran est différent des captures d’écran ci-dessous, cela signifie que les nouvelles modifications n’ont pas encore été déployées dans votre entreprise. Dans ce cas, reportez-vous à la section [documentation héritée](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis-legacy.md).

Certaines architectures reposent sur des appels à AEM as a Cloud Service à l’aide d’une application hébergée sur un serveur en dehors de l’infrastructure AEM. Il peut s’agir, par exemple, d’une application mobile qui appelle un serveur, puis effectue des requêtes d’API auprès d’AEM as a Cloud Service.

Le flux de serveur à serveur est décrit ci-dessous, ainsi qu’un flux simplifié de développement. La [Developer Console](development-guidelines.md#crxde-lite-and-developer-console) d’AEM as a Cloud Service sert à générer les jetons nécessaires au processus d’authentification.

<!-- Alexandru: hiding this until the tutorials reflect the new UI

>[!NOTE]
>
>In addition to this documentation, you can also consult the tutorials on [Token-based authentication for AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=en#authentication) and [Getting a Login Token for Integrations](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-getting-login-token-integrations.html). -->

## Flux de serveur à serveur {#the-server-to-server-flow}

Un utilisateur disposant d’un rôle d’administrateur d’organisation IMS et qui est également membre du profil produit Utilisateurs AEM ou Administrateurs AEM sur l’auteur AEM, peut générer un ensemble d’informations d’identification as a Cloud Service, chacune étant une charge utile JSON qui inclut un certificat (la clé publique), une clé privée et un compte technique constitué d’un `clientId` et `clientSecret`. Ces informations d’identification peuvent ensuite être récupérées par un utilisateur disposant du rôle d’administrateur d’environnement as a Cloud Service AEM et doivent être installées sur un serveur non AEM et traitées avec précaution comme une clé secrète. Ce fichier de format JSON contient toutes les données requises pour l’intégration avec une API AEM as a Cloud Service. Les données sont utilisées pour créer un jeton JWT signé, qui est échangé avec Adobe Identity Management Services (IMS) pour un jeton d’accès IMS. Ce jeton d’accès peut ensuite être utilisé comme jeton d’authentification du porteur pour adresser des requêtes à AEM as a Cloud Service. Le certificat des informations d’identification expire par défaut après un an, mais il peut être actualisé si nécessaire, comme décrit [here](#refresh-credentials).

Le flux de serveur à serveur comprend les étapes suivantes :

* Récupérer les informations d’identification AEM as a Cloud Service dans la Developer Console
* Installer les informations d’identifications AEM as a Cloud Service sur un serveur non AEM qui effectue des appels à AEM
* Générer un jeton JWT et l’échanger contre un jeton d’accès à l’aide des API IMS d’Adobe
* Appeler l’API AEM avec le jeton d’accès servant de jeton d’authentification du porteur
* Définir les autorisations appropriées pour l’utilisateur du compte technique dans l’environnement AEM

### Extraction des informations d’identification AEM as a Cloud Service {#fetch-the-aem-as-a-cloud-service-credentials}

Les utilisateurs ayant accès à AEM console de développement as a Cloud Service verront apparaître l’onglet Intégrations dans Developer Console pour un environnement donné. Un utilisateur disposant du rôle d’administrateur d’environnement as a Cloud Service AEM peut créer, afficher ou gérer des informations d’identification.

Cliquez sur le bouton **Créer un compte technique** , un nouvel ensemble d’informations d’identification sera créé, qui comprend l’identifiant client, le secret client, la clé privée, le certificat et la configuration pour les niveaux de création et de publication de l’environnement, quelle que soit la sélection de la capsule.

![Créer un nouveau compte technique](/help/implementing/developing/introduction/assets/s2s-createtechaccount.png)

Un nouvel onglet du navigateur s’ouvre et affiche les informations d’identification. Vous pouvez utiliser cette vue pour télécharger les informations d’identification en appuyant sur l’icône de téléchargement située en regard du titre de l’état :

![Téléchargement des informations d’identification](/help/implementing/developing/introduction/assets/s2s-credentialdownload.png)

Une fois les informations d’identification créées, elles s’affichent sous le **Comptes techniques** dans le **Intégrations** section :

![Afficher les informations d’identification](/help/implementing/developing/introduction/assets/s2s-viewcredentials.png)

Les utilisateurs peuvent ensuite afficher les informations d’identification à l’aide de l’action Afficher . En outre, comme décrit plus loin dans l’article, les utilisateurs peuvent modifier les informations d’identification du même compte technique en créant une clé privée ou un nouveau certificat, dans les cas où le certificat doit être renouvelé ou révoqué.

Les utilisateurs disposant du rôle d’administrateur d’environnement as a Cloud Service AEM peuvent ultérieurement créer de nouvelles informations d’identification pour des comptes techniques supplémentaires. Cela s’avère utile lorsque différentes API ont des exigences d’accès différentes. Par exemple, lecture ou lecture-écriture.

>[!NOTE]
>
>Les clients peuvent créer jusqu’à 10 comptes techniques, y compris ceux qui ont déjà été supprimés.

>[!IMPORTANT]
>
>Un administrateur d’organisation IMS (généralement le même utilisateur qui a configuré l’environnement via Cloud Manager), qui doit également être membre du profil produit Utilisateurs AEM ou Administrateurs AEM sur l’auteur AEM, doit d’abord accéder à Developer Console et cliquer sur le bouton **Créer un compte technique** pour que les informations d’identification soient générées et récupérées ultérieurement par un utilisateur disposant des droits d’administrateur sur l’environnement as a Cloud Service AEM. Si l’administrateur de l’organisation IMS ne l’a pas fait, un message l’informera que le rôle d’administrateur de l’organisation IMS doit lui être attribué.

### Installation des informations d’identification de service AEM sur un serveur non AEM {#install-the-aem-service-credentials-on-a-non-aem-server}

L’application qui appelle AEM doit pouvoir accéder aux identifiants as a Cloud Service AEM, les traiter comme un secret.

### Génération d’un jeton JWT et échange contre un jeton d’accès  {#generate-a-jwt-token-and-exchange-it-for-an-access-token}

Utilisez les informations d’identification pour créer un jeton JWT lors d’un appel au service IMS d’Adobe afin de récupérer un jeton d’accès valide pendant 24 heures.

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

Le jeton d’accès définit le moment de son expiration, généralement au bout de 24 heures. Le référentiel git contient un exemple de code pour gérer un jeton d’accès et l’actualiser avant son expiration.

>[!NOTE]
>S’il existe plusieurs informations d’identification, veillez à référencer le fichier json approprié pour l’appel API à AEM qui sera appelé ultérieurement.

### Appel de l’API AEM {#calling-the-aem-api}

Effectuez les appels d’API appropriés de serveur à serveur auprès d’AEM as a Cloud Service, y compris le jeton d’accès dans l’en-tête. Pour l’en-tête « Authorization », utilisez la valeur `"Bearer <access_token>"`. Par exemple, en utilisant `curl` :

```curlc
curl -H "Authorization: Bearer <your_ims_access_token>" https://author-p123123-e23423423.adobeaemcloud.com/content/dam.json
```

### Définissez les autorisations appropriées pour l’utilisateur du compte technique dans AEM {#set-the-appropriate-permissions-for-the-technical-account-user-in-aem}

Tout d’abord, un nouveau profil de produit doit être créé dans Adobe Admin Console. Pour ce faire, procédez comme suit :

1. Accédez à Adobe Admin Console à l’adresse [https://adminconsole.adobe.com/](https://adminconsole.adobe.com/)
1. Appuyez sur la touche **Gérer** sous le lien **Produits et services** sur la gauche.
1. Sélectionner **AEM as a Cloud Service**
1. Appuyez sur la touche **Nouveau profil** button

   ![Nouveau profil](/help/implementing/developing/introduction/assets/s2s-newproductprofile.png)

1. Nommez le profil et appuyez sur **Enregistrer**

   ![Enregistrer le profil](/help/implementing/developing/introduction/assets/s2s-saveprofile.png)

1. Sélectionnez le profil que vous venez de créer dans la liste des profils.
1. Appuyez sur la touche **Ajouter un utilisateur** button

   ![Ajouter un utilisateur](/help/implementing/developing/introduction/assets/s2s-addusers.png)

1. Ajoutez le compte technique que vous venez de créer (dans ce cas `84b2c3a2-d60a-40dc-84cb-e16b786c1673@techacct.adobe.com`) et appuyez sur **Enregistrer**

   ![Ajout d’un compte technique](/help/implementing/developing/introduction/assets/s2s-addtechaccount.png)

1. Patientez 10 minutes pour que les modifications prennent effet et effectuez un appel API vers AEM avec un jeton d’accès généré à partir des nouvelles informations d’identification. En tant que commande cURL, elle serait représentée comme suit :

   `curl -H "Authorization: Bearer <access_token>" https://author-pXXXXX-eXXXXX.adobeaemcloud.net/content/dam.json `


Une fois l’appel API effectué, le profil de produit s’affiche en tant que groupe d’utilisateurs dans l’instance d’auteur as a Cloud Service AEM, avec le compte technique approprié en tant que membre de ce groupe.

Pour vérifier cela, vous devez :

1. Connexion à l’instance d’auteur
1. Accédez à **Outils** - **Sécurité** et cliquez sur le bouton **Groupes** carte
1. Localisez le nom du profil que vous avez créé dans la liste des groupes et cliquez dessus :

   ![Profil du groupe](/help/implementing/developing/introduction/assets/s2s-groupprofile.png)

1. Dans la fenêtre suivante, passez à la **Membres** et vérifiez si le compte technique y est correctement répertorié :

   ![Onglet Membres](/help/implementing/developing/introduction/assets/s2s-techaccountmembers.png)


Vous pouvez également vérifier que le compte technique apparaît dans la liste des utilisateurs en procédant comme suit sur l’instance de création :

1. Accédez à **Outils** - **Sécurité** - **Utilisateurs**
1. Vérifiez que votre compte technique est la liste des utilisateurs et cliquez dessus.
1. Cliquez sur le bouton **Groupes** pour vérifier que l’utilisateur fait partie du groupe correspondant à votre profil de produit. Cet utilisateur est également membre d’une poignée d’autres groupes, y compris Contributeurs :

   ![Appartenance à un groupe](/help/implementing/developing/introduction/assets/s2s-groupmembership.png)

>[!NOTE]
>
>Avant la mi-2023, avant qu’il ne soit possible de créer plusieurs informations d’identification, les clients n’étaient pas invités à créer un profil de produit dans la console d’administration des Adobes et le compte technique n’était donc pas associé à un groupe autre que &quot;Contributeurs&quot; dans l’instance as a Cloud Service AEM. Par souci de cohérence, il est recommandé, pour ce compte technique, de créer un profil de produit dans Adobe Admin Console comme décrit ci-dessus, puis d’ajouter le compte technique existant à ce groupe.

<u>**Définition des autorisations de groupe d’approbation**</u>

Enfin, configurez le groupe avec les autorisations appropriées nécessaires pour appeler ou verrouiller correctement vos API. Pour ce faire, procédez comme suit :

1. Connectez-vous à l’instance d’auteur appropriée et accédez à **Paramètres** - **Sécurité** - **Autorisations**
1. Recherchez le nom du groupe correspondant au profil de produit dans le volet de gauche (dans ce cas, les API en lecture seule) et cliquez dessus :

   ![Rechercher un groupe](/help/implementing/developing/introduction/assets/s2s-searchforgroup.png)

1. Cliquez sur le bouton Editer dans la fenêtre suivante :

   ![Modifier les autorisations](/help/implementing/developing/introduction/assets/s2s-editpermissions.png) 

1. Modifiez les autorisations de manière appropriée, puis cliquez sur **Enregistrer**

   ![Confirmer la modification des autorisations](/help/implementing/developing/introduction/assets/s2s-confirmeditpermissions.png)

>[!INFO]
>
>Pour en savoir plus sur Adobe Identity Management System (IMS) et les utilisateurs et groupes d’AEM, consultez la section [documentation](/help/security/ims-support.md).

## Flux de développement {#developer-flow}

Les développeurs voudront probablement effectuer des tests en utilisant une instance de développement de leur application non AEM (exécutée sur leur ordinateur portable ou hébergée). Cette application adresse des requêtes à un environnement de développement AEM as a Cloud Service. Cependant, comme les développeurs ne disposent pas nécessairement d’autorisations d’administrateur IMS, nous ne pouvons pas supposer qu’ils peuvent effectuer une génération du porteur JWT décrite pour le flux régulier de serveur à serveur. Nous fournissons donc un mécanisme permettant à un développeur de générer directement un jeton d’accès utilisable dans les requêtes adressées à AEM as a Cloud Service auxquels ils ont accès.

Pour plus d’informations sur les autorisations requises pour utiliser la Developer Console dans AEM as a Cloud Service, consultez la [documentation destinée aux développeurs](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console).

>[!NOTE]
>
>Le jeton d’accès de développement local est valide pendant 24 heures au maximum, après quoi il doit être régénéré selon la même méthode.

Les développeurs peuvent utiliser ce jeton pour émettre des appels depuis leur application de test non AEM vers l’environnement AEM as a Cloud Service. En règle générale, un développeur utilise ce jeton avec l’application non AEM sur son propre ordinateur portable. En outre, AEM as a Cloud Service est généralement un environnement distinct de la production.

Le flux de développement comprend les étapes suivantes :

* Générer un jeton d’accès à partir de la Developer Console
* Appeler l’application AEM à l’aide du jeton d’accès

Les développeurs peuvent également effectuer des appels d’API vers un projet AEM exécuté sur leur ordinateur local, auquel cas un jeton d’accès n’est pas nécessaire.

### Génération du jeton d’accès {#generating-the-access-token}

1. Accédez au **Jeton local** under **Intégrations**
1. Cliquez sur le bouton **Get Local Development Token** (Obtenir le jeton de développement local) de la Developer Console pour générer un jeton d’accès.

### Appel de l’application AEM avec un jeton d’accès {#call-the-aem-application-with-an-access-token}

Effectuez les appels d’API de serveur à serveur appropriés auprès de l’application non AEM vers un environnement AEM as a Cloud Service, y compris le jeton d’accès dans l’en-tête. Pour l’en-tête « Authorization », utilisez la valeur `"Bearer <access_token>"`.

## Actualisation des informations d’identification {#refresh-credentials}

Par défaut, les informations d’identification AEM as a Cloud Service expirent au bout d’un an. Pour assurer la continuité du service, les développeurs ont la possibilité d’actualiser les informations d’identification, en prolongeant leur disponibilité pendant un an supplémentaire.

Pour ce faire, vous pouvez :

* Utilisez la variable **Ajout d’un certificat** sous **Intégrations** - **Comptes techniques** dans Developer Console, comme illustré ci-dessous

   ![Actualisation des informations d’identification](/help/implementing/developing/introduction/assets/s2s-credentialrefresh.png)

* Après avoir appuyé sur le bouton, un ensemble d’informations d’identification contenant un nouveau certificat est généré. Installez les nouvelles informations d’identification sur votre serveur hors AEM et assurez-vous que la connectivité est correcte, sans supprimer les anciennes informations d’identification. 
* Assurez-vous que les nouvelles informations d’identification sont utilisées à la place des anciennes lors de la génération du jeton d’accès.
* Vous pouvez éventuellement révoquer (puis supprimer) le certificat précédent afin qu’il ne puisse plus être utilisé pour s’authentifier avec AEM as a Cloud Service.

## Révocation des informations d’identification {#credentials-revocation}

Si la clé privée est compromise, vous devez créer des informations d’identification avec un nouveau certificat et une nouvelle clé privée. Une fois que votre application a utilisé les nouvelles informations d’identification pour générer des jetons d’accès, vous pouvez révoquer et supprimer les anciens certificats.

Pour ce faire, procédez comme suit :

1. Tout d’abord, ajoutez la nouvelle clé. Cela génère des informations d’identification avec une nouvelle clé privée et un nouveau certificat. La nouvelle clé privée sera marquée comme **current** et sera donc utilisé pour toutes les nouvelles informations d’identification de ce compte technique à venir. Notez que les informations d’identification associées aux anciennes clés privées restent valides jusqu’à la révocation. Pour ce faire, appuyez sur les trois points (**...**) sous votre compte technique actuel et appuyez sur **Ajout d’une clé privée**:

   ![Ajout d’une clé privée](/help/implementing/developing/introduction/assets/s2s-addnewprivatekey.png)

1. Press **Ajouter** à l’invite suivante :

   ![Confirmer l’ajout d’une nouvelle clé privée](/help/implementing/developing/introduction/assets/s2s-addprivatekeyconfirm.png)

   Un nouvel onglet de navigation avec les nouveaux détails s’ouvre et l’interface utilisateur est mise à jour afin d’afficher les deux clés privées, la nouvelle clé étant marquée comme **current**:

   ![Clés privées dans l’interface utilisateur](/help/implementing/developing/introduction/assets/s2s-twokeys.png)

1. Installez les nouvelles informations d’identification sur le serveur non AEM et assurez-vous que la connectivité fonctionne comme prévu. Voir [Section Flux serveur à serveur](#the-server-to-server-flow) pour plus d’informations sur la procédure à suivre
1. Révoquez l’ancien certificat. Pour ce faire, sélectionnez les trois points (**...**) à droite du certificat et en appuyant sur **Révoquer**:

   ![Révoquer le certificat](/help/implementing/developing/introduction/assets/s2s-revokecert.png)

   Ensuite, confirmez la révocation dans l’invite suivante en appuyant sur la touche **Révoquer** button :

   ![Révoquer la confirmation du certificat](/help/implementing/developing/introduction/assets/s2s-revokecertificateconfirmation.png)

1. Enfin, supprimez le certificat compromis.
