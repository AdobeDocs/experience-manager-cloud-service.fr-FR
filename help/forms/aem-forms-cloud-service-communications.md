---
title: AEM Forms as a Cloud Service - Communications
description: Fusionner automatiquement les données avec des modèles XDP et PDF ou générer une sortie aux formats PCL, ZPL et PostScript
exl-id: 9fa9959e-b4f2-43ac-9015-07f57485699f
source-git-commit: 20e54ff697c0dc7ab9faa504d9f9e0e6ee585464
workflow-type: tm+mt
source-wordcount: '1203'
ht-degree: 50%

---


# Utilisation du traitement synchrone {#sync-processing-introduction}

Forms as a Cloud Service : les API de communications vous permettent de créer, d’assembler et de diffuser des communications personnalisées et orientées sur la marque, telles que des correspondances commerciales, des documents, des récapitulatifs, des lettres de traitement des demandes, des avis de prestations, des lettres de traitement des demandes, des factures mensuelles et des kits de bienvenue. Vous pouvez utiliser les API Communications pour combiner un modèle (XFA ou PDF) avec des données client afin de générer des documents aux formats PDF, PS, PCL, DPL, IPL et ZPL.

Supposons que vous ayez un ou plusieurs modèles et plusieurs enregistrements de données XML pour chaque modèle. Vous pouvez utiliser les API Communications pour générer un document d’impression pour chaque enregistrement. <!-- You can also combine the records into a single document. --> Le résultat est un document PDF non interactif. Dans ce type de document, les utilisateurs n’ont pas la possibilité de saisir des données dans les champs.

Forms as a Cloud Service : les communications fournissent des API à la demande et par lots (API asynchrones) pour la génération de documents planifiés :

* Les API synchrones sont adaptées aux cas d’utilisation de génération de documents à la demande, à faible latence et pour un enregistrement unique. Ces API sont plus adaptées aux cas d’utilisation basés sur une action de l’utilisateur. Il peut s’agir, par exemple, de la génération d’un document après qu’un utilisateur a rempli un formulaire.

* Les API Batch (API asynchrones) conviennent pour la génération planifiée à débit élevé de documents multiples. Ces API génèrent des documents par lots. Il peut s’agir, par exemple, de factures de téléphone, de relevés de carte de crédit et de relevés de prestations générés tous les mois.

## Utilisation des opérations synchrones {#batch-operations}

Une opération synchrone est un processus de génération de documents de manière linéaire. Ces API sont classées comme API à un seul client et API à plusieurs clients :

### API de client unique

* API de génération de document
* API de manipulation de documents

### API multi-client

* API de l’utilitaire de document

### Authentification d’une API à client unique

Les opérations d’API à client unique prennent en charge deux types d’authentification :

* **Authentification de base** : l’authentification de base est un schéma d’authentification simple intégré au protocole HTTP. Le client envoie des requêtes HTTP avec l’en-tête Autorisation qui contient le mot Base suivi d’un espace et d’une chaîne codée en base64 - nom d’utilisateur : mot de passe. Par exemple, pour autoriser en tant qu’administrateur / admin, le client envoie Base [chaîne codée en base64 - nom d’utilisateur] : [chaîne codée en base64 - mot de passe].

* **Authentification basée sur les jetons :** l’authentification basée sur les jetons utilise un jeton d’accès (jeton d’authentification du porteur) pour envoyer des requêtes à Experience Manager as a Cloud Service. AEM Forms as a Cloud Service fournit des API pour récupérer en toute sécurité le jeton d’accès. Pour récupérer et utiliser le jeton afin d’authentifier une requête :

   1. [Récupération des informations d’identification as a Cloud Service Experience Manager à partir de Developer Console](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=fr).
   1. [Installation d’informations d’identification as a Cloud Service Experience Manager dans votre environnement](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=fr). (Serveur d’applications, serveur web ou autres serveurs non AEM) configurés pour envoyer des requêtes au service cloud (passer des appels).
   1. [Générez un jeton JWT et échangez-le avec les API Adobe IMS pour un jeton d’accès](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=fr).
   1. Exécutez l’API Experience Manager avec le jeton d’accès servant de jeton d’authentification du porteur.
   1. [Définissez les autorisations appropriées pour l’utilisateur du compte technique dans l’environnement Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=fr#configurer-l’accès-dans-aem).

   >[!NOTE]
   >
   >Adobe recommande d’utiliser l’authentification basée sur les jetons sur un environnement de production.

### Authentification d’une API à plusieurs clients

#### En-têtes d’authentification

Chaque appel d’API HTTP entrant à l’API Cloud Manager doit contenir les trois en-têtes suivants :

* `x-api-key`
* `x-gw-ims-org-id`
* `Authorization`

Les valeurs qui doivent être envoyées dans la variable `x-api-key` et `x-gw-ims-org-id` Les en-têtes sont fournis dans l’écran Détails des informations d’identification de la section [Console Adobe Developer](https://developer.adobe.com/console). La valeur de la variable `x-api-key` L’en-tête est l’identifiant du client et la valeur de la variable `x-gw-ims-org-id` header est l’ID d’organisation.

#### Configuration de la console Adobe Developer pour générer un jeton d’accès

Pour configurer les API d’authentification, créez un projet dans la console Adobe Developer et ajoutez des API de communication au projet dans la console Adobe Developer. L’intégration génère la clé API, le secret client, la charge utile (JWT):

1. Contactez votre administrateur de la console Adobe Developer. Demandez à l’administrateur de l’ajouter en tant que développeur.
1. Connectez-vous à `https://developer.adobe.com/console/`. Utilisez le compte de développeur que votre administrateur a mis à votre disposition pour vous connecter à la console Adobe Developer.
1. Sélectionnez votre entreprise dans le coin supérieur droit. Si vous ne connaissez pas le nom de votre entreprise, contactez votre administrateur.
1. Appuyez sur **[!UICONTROL Create new project]** (Créer un projet). Un écran pour démarrer votre nouveau projet apparaît. Appuyez sur **[!UICONTROL Add API]** (Ajouter une API). Un écran avec la liste de toutes les API activées pour votre compte apparaît.
1. Sélectionner **[!UICONTROL AEM Forms - Communications]** et appuyez sur **[!UICONTROL Suivant]**. Un écran de configuration de l’API apparaît.
1. Sélectionner **[!UICONTROL OPTION 1 Générer une paire de clés]** et appuyez sur **[!UICONTROL Générer une paire de clés]**. Il crée et télécharge le fichier de configuration. Le fichier de configuration téléchargé contient tous les paramètres de votre application, ainsi que la seule copie de votre clé privée. Adobe n’enregistre pas votre clé privée. Veillez à stocker le fichier téléchargé en toute sécurité. Appuyez sur **[!UICONTROL Suivant]**.
1. Sélectionner **[!UICONTROL Intégrations - Cloud Service]** et appuyez sur **[!UICONTROL Enregistrer l’API configurée]**. Appuyer **[!UICONTROL Compte de service (JWT)]** pour afficher la clé API, le secret client et d’autres informations nécessaires pour accéder aux API. Vous configurez l’utilisation du jeton pour accéder aux API.

#### Générer et utiliser un jeton d’accès par programmation

Pour générer un jeton d’accès par programmation, générez un jeton Web JSON (JWT) et échangez-le avec Adobe Identity Management Service (IMS) pour un jeton d’accès.

Utilisez les clés suivantes, appelées revendications, pour construire l’objet JSON JWT :

* `exp`- l’expiration demandée du jeton d’accès, exprimée en nombre de secondes depuis le 1er janvier 1970 GMT. Pour la plupart des cas d’utilisation, il s’agit d’une valeur relativement faible. Par exemple, dans 5 minutes, dans cinq minutes, cette valeur doit être 1670923791.
* `iss` : ID d’organisation du projet de console Adobe Developer, au format org_ident@AdobeOrg.
* `sub` - l’identifiant de compte technique de l’intégration de la console Adobe Developer, au format suivant : id@techacct.adobe.com.
* `aud` : identifiant client de l’intégration de la console Adobe Developer en préfixe avec `https://ims-na1.adobelogin.com/c/`.
* `https://ims-na1-stg1.adobelogin.com/s/ent_aemforms_docprocessing` - défini sur la valeur littérale `true`

Cet objet JSON doit ensuite être codé en base64 et signé à l’aide de la clé privée du projet. Enfin, la valeur codée est envoyée dans le corps d’une requête de POST à `https://ims-na1.adobelogin.com/ims/exchange/jwt` ainsi que l’identifiant du client et le secret du client pour le projet.

##### Exemple

```JSON
    ========================= REQUEST ==========================
    POST https://ims-na1.adobelogin.com/ims/exchange/jwt
    -------------------------- body ----------------------------
    client_id={myClientId}&client_secret={myClientSecret}&jwt_token={myJSONWebToken}
    ------------------------- headers --------------------------
    Content-Type: application/x-www-form-urlencoded
    Cache-Control: no-cache
```

#### Prise en charge linguistique de JWT

Bien qu’il soit possible d’effectuer l’ensemble du processus de génération et d’échange JWT dans du code personnalisé, il est plus courant d’utiliser une bibliothèque de niveau supérieur pour ce faire. Un certain nombre de ces bibliothèques sont répertoriées dans la [Documentation JWT sur Adobe I/O](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/).

### (Uniquement pour les API de génération de documents) Configuration des ressources et des autorisations

Pour utiliser les API synchrones, les éléments suivants sont requis :

* Utilisateurs disposant des privilèges d’administrateur Experience Manager
* Chargez les modèles et d’autres ressources vers votre instance Experience Manager Forms Cloud Service.

### (Uniquement pour les API de génération de documents) Chargez des modèles et d’autres ressources vers votre instance Experience Manager.

Une entreprise possède généralement différents modèles. Par exemple, un modèle pour les relevés de carte de crédit, les relevés de prestations et les réclamations. Chargez tous ces modèles XDP et PDF vers votre instance Experience Manager. Pour charger un modèle :

1. Ouvrez votre instance Experience Manager.
1. Accédez à Formulaires > Formulaires et documents
1. Cliquez sur Créer > Dossier et créez un dossier. Ouvrez le dossier.
1. Cliquez sur Créer > Téléchargement de fichier et chargez les modèles.

### Appel d’une API

La [documentation de référence sur les API](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/) fournit des informations détaillées sur tous les paramètres, les méthodes d’authentification et les différents services fournis par les API. La documentation de référence de l’API fournit également le fichier de définition de l’API au format .yaml . Vous pouvez télécharger le fichier .yaml et le télécharger vers [Postman](https://www.postman.com/) pour vérifier les fonctionnalités des API.

>[!VIDEO](https://video.tv.adobe.com/v/335771)

>[!NOTE]
>
>Seuls les membres du groupe des utilisateurs de formulaires peuvent accéder aux API Communications.
