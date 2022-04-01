---
title: AEM Forms as a Cloud Service - Communications
description: Fusionner automatiquement les données avec des modèles XDP et PDF ou générer une sortie aux formats PCL, ZPL et PostScript
exl-id: 9fa9959e-b4f2-43ac-9015-07f57485699f
source-git-commit: fdbb927dbd7f6d640100d444431f931d95414ebc
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 39%

---


# Utilisation du traitement synchrone {#sync-processing-introduction}

La fonctionnalité de communication vous permet de créer des documents approuvés, personnalisés et normalisés par la marque, tels que des correspondances commerciales, des récapitulatifs, des lettres de traitement des demandes, des avis de prestations, des factures mensuelles ou des kits de bienvenue.

Cette fonctionnalité fournit des API pour générer et manipuler les documents. Vous pouvez générer ou manipuler un document à la demande ou créer une tâche par lots pour générer plusieurs documents à des intervalles définis.

La fonctionnalité Communications fournit des API pour la génération de documents planifiés et à la demande. Vous pouvez utiliser des API synchrones pour les API à la demande et Batch (API asynchrones) concernant la génération de documents planifiés :

* Les API synchrones sont adaptées aux cas d’utilisation de génération de documents à la demande, à faible latence et pour un enregistrement unique. Ces API sont plus adaptées aux cas d’utilisation basés sur une action de l’utilisateur. Il peut s’agir, par exemple, de la génération d’un document après qu’un utilisateur a rempli un formulaire.

* Les API Batch (API asynchrones) conviennent pour la génération planifiée à débit élevé de documents multiples. Ces API génèrent des documents par lots. Il peut s’agir, par exemple, de factures de téléphone, de relevés de carte de crédit et de relevés de prestations générés tous les mois.

## Utilisation des opérations synchrones {#batch-operations}

Une opération synchrone est un processus de génération ou de manipulation de documents de manière linéaire. Il prend en charge deux types d’authentification :

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

### (API de génération de documents uniquement) Conditions préalables {#pre-requisites}

Pour utiliser des API synchrones pour la génération de document, les conditions suivantes sont requises :

* Modèles PDF ou XDP
* [Données à fusionner avec des modèles](#form-data)
* Utilisateurs disposant des privilèges d’administrateur Experience Manager
* Chargez les modèles et d’autres ressources vers votre instance Experience Manager Forms Cloud Service.

#### Chargement de modèles et d’autres ressources vers votre instance Experience Manager

Une entreprise possède généralement différents modèles. Par exemple, un modèle pour les relevés de carte de crédit, les relevés de prestations et les réclamations. Chargez tous ces modèles XDP et PDF vers votre instance Experience Manager. Pour charger un modèle :

1. Ouvrez votre instance Experience Manager.
1. Accédez à Formulaires > Formulaires et documents
1. Cliquez sur Créer > Dossier et créez un dossier. Ouvrez le dossier.
1. Cliquez sur Créer > Téléchargement de fichier et chargez les modèles.

### Utilisation de l’API synchrone pour générer des documents

Des API distinctes sont disponibles pour :

* Génère un document PDF à partir d’un modèle et y fusionne les données.
* Générez un document PostScript (PS), PCL (Printer Command Language), Zebra Printing Language) à partir d’un fichier XDP ou d’un document de PDF.

La [documentation de référence sur les API](https://www.adobe.io/experience-manager-forms-cloud-service-developer-reference/api/sync/#tag/Communications-Services) fournit des informations détaillées sur tous les paramètres, les méthodes d’authentification et les différents services fournis par les API. La documentation de référence de l’API est également disponible au format .yaml. Vous pouvez télécharger le fichier .yaml pour [API synchrones](assets/sync.yaml) et chargez-le sur postman pour vérifier la fonctionnalité des API.

>[!VIDEO](https://video.tv.adobe.com/v/335771)

>[!NOTE]
>
>Seuls les membres du groupe des utilisateurs de formulaires peuvent accéder aux API Communications.
