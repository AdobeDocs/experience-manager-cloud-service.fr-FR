---
title: AEM Forms as a Cloud Service - Communications
description: Fusionner automatiquement les données avec des modèles XDP et PDF ou générer une sortie aux formats PCL, ZPL et PostScript
exl-id: 9fa9959e-b4f2-43ac-9015-07f57485699f
source-git-commit: a3c817dedbf20b21e609ad0e5bfd0d3c4fa9a431
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 48%

---


# Utilisation du traitement synchrone {#sync-processing-introduction}

La fonctionnalité Communications vous permet de créer, d’assembler et de diffuser des communications personnalisées et axées sur la marque. Il peut notamment s’agir de correspondances d’entreprise, de documents, de relevés, de courriers de traitement des réclamations, d’avis de prestations, de factures mensuelles et de kits de bienvenue. Vous pouvez utiliser les API Communications pour combiner un modèle (XFA ou PDF) avec des données client afin de générer des documents aux formats PDF, PS, PCL, DPL, IPL et ZPL.

Supposons que vous ayez un ou plusieurs modèles et plusieurs enregistrements de données XML pour chaque modèle. Vous pouvez utiliser les API Communications pour générer un document d’impression pour chaque enregistrement. <!-- You can also combine the records into a single document. --> Le résultat est un document PDF non interactif. Dans ce type de document, les utilisateurs n’ont pas la possibilité de saisir des données dans les champs.


La fonctionnalité Communications fournit des API pour la génération de documents planifiés et à la demande. Vous pouvez utiliser des API synchrones pour les API à la demande et Batch (API asynchrones) concernant la génération de documents planifiés :

* Les API synchrones sont adaptées aux cas d’utilisation de génération de documents à la demande, à faible latence et pour un enregistrement unique. Ces API sont plus adaptées aux cas d’utilisation basés sur une action de l’utilisateur. Il peut s’agir, par exemple, de la génération d’un document après qu’un utilisateur a rempli un formulaire.

* Les API Batch (API asynchrones) conviennent pour la génération planifiée à débit élevé de documents multiples. Ces API génèrent des documents par lots. Il peut s’agir, par exemple, de factures de téléphone, de relevés de carte de crédit et de relevés de prestations générés tous les mois.

## Utilisation des opérations synchrones {#batch-operations}

Une opération synchrone est un processus de génération de documents de manière linéaire. Des API distinctes sont disponibles pour :

* Génère un document PDF à partir d’un modèle et y fusionne les données.
* Générez un document PostScript (PS), PCL (Printer Command Language), Zebra Printing Language) à partir d’un fichier XDP ou d’un document de PDF.
* Assemblage de documents PDF
* Désassemblage de documents PDF
* Convertir un document en document compatible avec le PDF/A
* Validation d’un document conforme au PDF/A


### Authentification d’un appel API

Les opérations synchrones prennent en charge deux types d’authentification :

* **Authentification de base**: L’authentification de base est un schéma d’authentification simple intégré au protocole HTTP. Le client envoie des requêtes HTTP avec l’en-tête Authorization qui contient le mot Basic suivi d’un espace et d’une chaîne codée en base64 username:password. Par exemple, pour autoriser en tant qu’administrateur/administrateur le client envoie Basic [nom d’utilisateur de chaîne codée en base64]: [mot de passe de chaîne codé en base64].

* **Authentification basée sur les jetons :** L’authentification basée sur les jetons utilise un jeton d’accès (jeton d’authentification du porteur) pour envoyer des requêtes à Experience Manager as a Cloud Service. AEM Forms as a Cloud Service fournit des API pour récupérer en toute sécurité le jeton d’accès. Pour récupérer et utiliser le jeton afin d’authentifier une requête :

   1. [Récupération des informations d’identification as a Cloud Service du Experience Manager à partir de Developer Console](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html).
   1. [Installation des informations d’identification as a Cloud Service Experience Manager sur votre environnement](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html). (Serveur d’applications, serveur web ou autres serveurs non AEM) configurés pour envoyer des requêtes au service cloud (effectuer des appels).
   1. [Générer un jeton JWT et l’échanger avec les API Adobe IMS pour un jeton d’accès](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html).
   1. Exécutez l’API du Experience Manager avec le jeton d’accès comme jeton d’authentification du porteur.
   1. [Définissez les autorisations appropriées pour l’utilisateur du compte technique dans l’environnement du Experience Manager.](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=en#configure-access-in-aem).

   >[!NOTE]
   >
   >Adobe recommande d’utiliser l’authentification par jeton sur un environnement de production.


### (Uniquement pour les API Document Generation) Configuration des ressources et des autorisations

Pour utiliser des API synchrones, les conditions suivantes sont requises :

* Modèles PDF ou XDP
* [Données à fusionner avec des modèles](#form-data)
* Utilisateurs disposant des privilèges d’administrateur Experience Manager
* Chargez les modèles et d’autres ressources vers votre instance Experience Manager Forms Cloud Service.

### (Uniquement pour les API Document Generation) Téléchargez des modèles et d’autres ressources vers votre instance de Experience Manager.

Une entreprise possède généralement différents modèles. Par exemple, un modèle pour les relevés de carte de crédit, les relevés de prestations et les réclamations. Chargez tous ces modèles XDP et PDF vers votre instance Experience Manager. Pour charger un modèle :

1. Ouvrez votre instance Experience Manager.
1. Accédez à Formulaires > Formulaires et documents
1. Cliquez sur Créer > Dossier et créez un dossier. Ouvrez le dossier.
1. Cliquez sur Créer > Téléchargement de fichier et chargez les modèles.


### Appel d’une API

La [documentation de référence sur les API](https://www.adobe.io/experience-manager-forms-cloud-service-developer-reference/api/sync/#tag/Communications-Services) fournit des informations détaillées sur tous les paramètres, les méthodes d’authentification et les différents services fournis par les API. La documentation de référence de l’API fournit également un fichier de définition de l’API au format .yaml . Vous pouvez télécharger le fichier .yaml et le charger dans Postman pour vérifier les fonctionnalités des API.

>[!VIDEO](https://video.tv.adobe.com/v/335771)

>[!NOTE]
>
>Seuls les membres du groupe des utilisateurs de formulaires peuvent accéder aux API Communications.
