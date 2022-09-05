---
title: AEM Forms as a Cloud Service - Communications
description: Fusionner automatiquement les données avec des modèles XDP et PDF ou générer une sortie aux formats PCL, ZPL et PostScript
exl-id: 9fa9959e-b4f2-43ac-9015-07f57485699f
source-git-commit: 07b9118b8cfc27bc9e2bfa134fbb57c7ae2728ad
workflow-type: tm+mt
source-wordcount: '731'
ht-degree: 99%

---


# Utilisation du traitement synchrone {#sync-processing-introduction}

La fonctionnalité Communications vous permet de créer, d’assembler et de diffuser des communications personnalisées et axées sur la marque. Il peut notamment s’agir de correspondances d’entreprise, de documents, de relevés, de courriers de traitement des réclamations, d’avis de prestations, de factures mensuelles et de kits de bienvenue. Vous pouvez utiliser les API Communications pour combiner un modèle (XFA ou PDF) avec des données client afin de générer des documents aux formats PDF, PS, PCL, DPL, IPL et ZPL.

Supposons que vous ayez un ou plusieurs modèles et plusieurs enregistrements de données XML pour chaque modèle. Vous pouvez utiliser les API Communications pour générer un document d’impression pour chaque enregistrement. <!-- You can also combine the records into a single document. --> Le résultat est un document PDF non interactif. Dans ce type de document, les utilisateurs n’ont pas la possibilité de saisir des données dans les champs.


La fonctionnalité Communications fournit des API pour la génération de documents planifiés et à la demande. Vous pouvez utiliser des API synchrones pour les API à la demande et Batch (API asynchrones) concernant la génération de documents planifiés :

* Les API synchrones sont adaptées aux cas d’utilisation de génération de documents à la demande, à faible latence et pour un enregistrement unique. Ces API sont plus adaptées aux cas d’utilisation basés sur une action de l’utilisateur. Il peut s’agir, par exemple, de la génération d’un document après qu’un utilisateur a rempli un formulaire.

* Les API Batch (API asynchrones) conviennent pour la génération planifiée à débit élevé de documents multiples. Ces API génèrent des documents par lots. Il peut s’agir, par exemple, de factures de téléphone, de relevés de carte de crédit et de relevés de prestations générés tous les mois.

## Utilisation des opérations synchrones {#batch-operations}

Une opération synchrone est un processus de génération de documents de manière linéaire. Des API distinctes sont disponibles pour :

* Générer un document PDF à partir d’un modèle et fusionner les données dans ce document.
* Générer un document PostScript (PS), PCL (Printer Command Language), ZPL (Zebra Printing Language) à partir d’un fichier XDP ou d’un document PDF.
* Assemblage de documents PDF
* Désassemblage de documents PDF
* Conversion d’un document en document conforme au PDF/A
* Validation d’un document conforme au PDF/A


### Authentification d’un appel API

Les opérations synchrones prennent en charge deux types d’authentification :

* **Authentification de base** : l’authentification de base est un schéma d’authentification simple intégré au protocole HTTP. Le client envoie des requêtes HTTP avec l’en-tête Autorisation qui contient le mot Base suivi d’un espace et d’une chaîne codée en base64 - nom d’utilisateur : mot de passe. Par exemple, pour autoriser en tant qu’administrateur / admin, le client envoie Base [chaîne codée en base64 - nom d’utilisateur] : [chaîne codée en base64 - mot de passe].

* **Authentification basée sur les jetons :** l’authentification basée sur les jetons utilise un jeton d’accès (jeton d’authentification du porteur) pour envoyer des requêtes à Experience Manager as a Cloud Service. AEM Forms as a Cloud Service fournit des API pour récupérer en toute sécurité le jeton d’accès. Pour récupérer et utiliser le jeton afin d’authentifier une requête :

   1. [Récupérez les informations d’identification Experience Manager as a Cloud Service à partir de la console de développement](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=fr).
   1. [Installez les informations d’identification Experience Manager as a Cloud Service sur votre environnement](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html). (Serveur d’applications, serveur web ou autres serveurs non AEM) configurés pour envoyer des requêtes au service cloud (passer des appels).
   1. [Générez un jeton JWT et échangez-le avec les API Adobe IMS pour un jeton d’accès](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html).
   1. Exécutez l’API Experience Manager avec le jeton d’accès servant de jeton d’authentification du porteur.
   1. [Définissez les autorisations appropriées pour l’utilisateur du compte technique dans l’environnement Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=fr#configurer-l’accès-dans-aem).

   >[!NOTE]
   >
   >Adobe recommande d’utiliser l’authentification basée sur les jetons sur un environnement de production.


### (Uniquement pour les API de génération de documents) Configuration des ressources et des autorisations

Pour utiliser les API synchrones, les éléments suivants sont requis :

* Modèles PDF ou XDP
* [Données à fusionner avec des modèles](#form-data)
* Utilisateurs disposant des privilèges d’administrateur Experience Manager
* Chargez les modèles et d’autres ressources vers votre instance Experience Manager Forms Cloud Service.

### (Uniquement pour les API de génération de documents) Chargez des modèles et d’autres ressources vers votre instance Experience Manager.

Une entreprise possède généralement différents modèles. Par exemple, un modèle pour les relevés de carte de crédit, les relevés de prestations et les réclamations. Chargez tous ces modèles XDP et PDF vers votre instance Experience Manager. Pour charger un modèle :

1. Ouvrez votre instance Experience Manager.
1. Accédez à Formulaires > Formulaires et documents
1. Cliquez sur Créer > Dossier et créez un dossier. Ouvrez le dossier.
1. Cliquez sur Créer > Téléchargement de fichier et chargez les modèles.


### Appel d’une API

La [documentation de référence sur les API](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/) fournit des informations détaillées sur tous les paramètres, les méthodes d’authentification et les différents services fournis par les API. La documentation de référence sur les API fournit également un fichier de définition de l’API au format .yaml. Vous pouvez télécharger le fichier .yaml et le charger dans Postman pour vérifier les fonctionnalités des API.

>[!VIDEO](https://video.tv.adobe.com/v/335771)

>[!NOTE]
>
>Seuls les membres du groupe des utilisateurs de formulaires peuvent accéder aux API Communications.
