---
title: Ce qui a changé entre AEM 6.5 Forms et AEM Cloud Services
description: Êtes-vous un utilisateur Experience Manager Forms qui souhaitez effectuer une mise à niveau vers Adobe Experience Manager Forms as a Cloud Service ? Découvrez les modifications les plus importantes avant de mettre à niveau ou de migrer vers Cloud Service.
contentOwner: khsingh
exl-id: 46fcc1b4-8fd5-40e1-b0fc-d2bc9df3802e
source-git-commit: d77b8d389be4b5c0ffa262ad6f1ff8b4d899e82b
workflow-type: tm+mt
source-wordcount: '1178'
ht-degree: 27%

---

# Modifications notables apportées aux utilisateurs d’Adobe Experience Manager 6.5 Forms existants  {#notable-changes-for-existing-AEM-Forms-users}

Adobe Experience Manager Forms as a Cloud Service apporte quelques modifications notables aux fonctionnalités existantes par rapport à Adobe Experience Manager Forms On-Premise et [!DNL Adobe-Managed Service] des environnements. Les principales différences sont énumérées ci-dessous :

| Fonctionnalité/fonctionnalité | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms |
|---|---|---|
| Architecture native au cloud | ☑ | ☒ |
| Mise à l’échelle automatique en fonction de la charge | ☑ | ☒ |
| Pas de temps d’arrêt pour les mises à niveau | ☑ | ☒ |
| Fréquence de déploiement des fonctionnalités | Agile* | Trimestrielle |
| Réseau de diffusion de contenu (CDN) inclus | ☑ | ☒ |
| Topologies optimisées pour une résilience et une efficacité optimales | ☑ | ☒ |
| Environnement de développement natif dans le cloud | ☑ | ☒ |
| Libre-service via Cloud Manager | ☑ | ☒ |
| Mises à niveau automatisées avec intégration continue et diffusion continue (CI/CD) | ☑ | ☒ |
| Intégration à [!DNL Micosoft Power Automate] | ☑ | ☒ |
| Intégration à [!DNL DocuSign] | ☑ | ☒ |
| Connectivité facile avec Microsoft Dynamics et Salesforce | ☑ | ☒ |
| Connexion aisée avec le magasin de données Microsoft Azure | ☑ | ☒ |
| Éditeur de règles accentué | ☑ | ☒ |
| Assistant de création de formulaires | ☑ | ☒ |
| Prise en charge XCI personnalisée d’un document d’enregistrement | ☑ | ☒ |
| Forms adaptatif <sup>1</sup> | ☑ | ☑ |
| Intégration de données à plusieurs sources de données | ☑ | ☑ |
| API de communications (Document Services) <sup>2,3</sup> | ☑ | ☑ |
| automated forms conversion Service <sup>4</sup> | ☑ | ☑ |
| Intégration à [!DNL Adobe Sign] | ☑ | ☑ |
| Intégration à [!DNL AEM Sites] | ☑ | ☑ |
| Intégration à [!DNL Adobe Launch] | ☑ | ☑ |
| Intégration à [!DNL Adobe Analytics] | ☑ | ☑ |
| Portail Forms <sup>5</sup> | ☑ | ☑ |
| Workflows AEM | ☑ | ☑ |
| Document d’enregistrement | ☑ | ☑ |
| Captcha invisible | ☑ | ☑ |
| Configurations de modèles de données de formulaire réutilisables | ☑ | ☑ |
| Document d’enregistrement basé sur Acrobat | ☑ | ☑ |
| Authentification d’identité basée sur les identifiants de gouvernement pour Forms adaptatif activé par Adobe Sign | ☑ | ☑ |
| HTML5 <sup>6</sup> | ☒ | ☑ |
| Document Security | ☒ | ☑ |

Avant de poursuivre le service, veuillez tenir compte des cas exceptionnels suivants :

+++ 1. Forms adaptatif

* **Forms adaptatif basé sur XSD :** Le service ne prend pas en charge HTML5 Forms (Mobile Forms). Si vous effectuez le rendu de vos formulaires basés sur XDP sous HTML5 Forms, vous pouvez continuer à utiliser la fonctionnalité sur AEM 6.5 Forms. Vous pouvez utiliser XDP-template pour concevoir un modèle de document à enregistrer. Le service ne prend pas en charge le Forms adaptatif basé sur XFA
* **Importation de modèles de formulaires adaptatifs :** Utilisez le pipeline de génération et le référentiel Git correspondant de votre programme pour importer les modèles de formulaire adaptatif existants.
* **Éditeur de règles :** AEM Forms as a Cloud Service offre une fonction renforcée [Éditeur de règles](rule-editor.md#visual-rule-editor). L’éditeur de code n’est pas disponible sur Forms as a Cloud Service. L’utilitaire de migration vous permet de migrer les formulaires dotés de règles personnalisées (créées dans l’éditeur de code). L’utilitaire convertit ces règles en fonctions personnalisées prises en charge sur Forms as a Cloud Service. Vous pouvez utiliser les fonctions réutilisables avec l’éditeur de règles pour continuer à obtenir les résultats obtenus avec les scripts de règle. `onSubmitError` ou `onSubmitSuccess` Les fonctions sont désormais disponibles en tant qu’actions dans l’éditeur de règles.
* **Brouillons et envois :** Le service ne conserve pas les métadonnées des brouillons et des Forms adaptatives envoyées.
* **Service de préremplissage :** Par défaut, le service de préremplissage fusionne les données avec un formulaire adaptatif au niveau du client plutôt que de fusionner les données sur le serveur dans AEM Forms 6.5. Cette fonctionnalité permet d’améliorer le temps nécessaire au préremplissage d’un formulaire adaptatif. Vous pouvez toujours configurer pour exécuter l’action de fusion sur le serveur Adobe Experience Manager Forms.
* **Actions Envoyer :** Le **Email en tant que PDF** n’est pas disponible. L’action d’envoi **Email** fournit des options pour envoyer des pièces jointes et joindre un document d’enregistrement (DE) par email.
* **Composants**: Le service ne prend pas en charge l’expérience de signature dans le formulaire et n’inclut pas les composants Résumé et vérification pour Forms adaptatif.



+++


+++ 2. Services de document : API de manipulation de documents (service Assembler)


Le service ne prend pas en charge les opérations qui dépendent d’autres services ou applications :

* La conversion de documents dans un format autre qu’un PDF au format PDF n’est pas prise en charge. Par exemple, Microsoft Word vers PDF, Microsoft Excel vers PDF et HTML vers PDF ne sont pas pris en charge. Si vos documents sont au format non PDF. Convertissez ces documents au format PDF avant de les utiliser avec les API de manipulation de documents de communication. Par exemple, si vos documents sont au format Microsoft Office, HTML, PostScript (PS) ou XDP, convertissez-les au format PDF avant de les utiliser avec des documents PDF.
* Les conversions basées sur Distiller Adobe ne sont pas prises en charge. Par exemple, PostScript(PS) vers PDF
* Les conversions basées sur le service Forms ne sont pas prises en charge. Par exemple, XDP aux PDF forms.
* Le service ne prend pas en charge la conversion d’un PDF signé ou d’un PDF transparent dans un autre format de PDF.
* L’application de droits d’utilisation à l’aide du service Reader Extensions n’est pas disponible.
* Le service ne permet pas de convertir des documents de PDF signés ou transparents au format PDF/A.

+++


+++ 3. Services de document : API Document Generation (Output Service)

Dans un seul appel API ou lot, vous ne pouvez utiliser qu’un seul modèle avec plusieurs fichiers XML de DONNÉES. L’utilisation de plusieurs modèles avec plusieurs fichiers de données dans un seul appel API n’est pas prise en charge.

+++

+++ 4. Service Automated forms conversion

Le service ne fournit pas de métamodèle pour Automated forms conversion Service. Vous pouvez [téléchargez-le à partir de la documentation d’Automated forms conversion Service](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=en#default-meta-model).

+++

+++ 5. Portail Forms

La prise en charge de l’utilisation anonyme du portail Forms n’est pas prête à l’emploi. Vous pouvez personnaliser le portail de formulaires pour activer l’affichage de formulaires pour les utilisateurs non connectés.

+++


+++ 6. HTML5 Forms (Forms mobile)

Le service ne prend pas en charge HTML5 Forms (Mobile Forms). Si vous effectuez le rendu de vos formulaires basés sur XDP sous HTML5 Forms, vous pouvez continuer à utiliser la fonctionnalité sur AEM 6.5 Forms.

+++


+++ 7. Modèle de données de formulaire

Le modèle de données Forms ne prend en charge que les points de terminaison HTTP et HTTP pour envoyer des données. Le service ne prend pas en charge le protocole SSL mutuel pour le connecteur REST et l’authentification par certificat x509 pour les sources de données SOAP. * Forms as a Cloud Service permet d’utiliser Microsoft Azure Blob, Microsoft SharePoint, Microsoft OneDrive et les services prenant en charge les opérations CRUD générales (créer, lire, mettre à jour et supprimer) en tant que entrepôts de données. Les spécifications Open API 2.0 et Open API sont prises en charge. Le service fournit également la prise en charge du connecteur JDBC.

+++


+++ 8. Environnement du développeur

* Un environnement conçu pour le cloud ne dispose pas de console web (gestionnaire de configuration). Vous pouvez utiliser le SDK [[!DNL AEM Forms] as a Cloud Service pour générer des configurations](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=fr#generating-osgi-configurations-using-the-aem-sdk-quickstart) et un pipeline CI/CD pour [déployer la configuration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=fr#deployment-process) sur votre instance de Cloud Service.
* Par défaut, seuls les protocoles HTTP et HTTPs sont pris en charge. [Contactez l’équipe d’assistance](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=fr#sending-email) pour activer les ports pour l’envoi d’e-mails et pour activer le protocole SMTP pour votre environnement.
* Le service ne prend pas en charge la conversion d’un PDF signé ou d’un PDF transparent dans un autre format de PDF. Avant d’utiliser les lots de vos clients avec Forms as a Cloud Service, recompilez votre code personnalisé avec la dernière version de la convention d’URL adobe-aemfd-docmanager* de l’Forms adaptatif localisé prend désormais en charge la spécification d’un paramètre régional dans l’URL. La nouvelle convention d’URL permet de mettre en cache les formulaires localisés sur un Dispatcher ou un CDN. Sur l’environnement Cloud Service, utilisez le format d’URL `http://host:port/content/forms/af/<afName>.<locale>.html` pour demander une version localisée d’un formulaire adaptatif au lieu de `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>`. Adobe recommande d’utiliser la mise en cache du Dispatcher ou du CDN. Cela permet d’améliorer la vitesse de rendu des formulaires préremplis
* Adobe Experience Manager Forms as a Cloud Service offre de nombreuses nouvelles fonctionnalités et possibilités de gestion pour vos projets AEM. Toutefois, certains changements sont nécessaires pour que les projets Adobe Experience Manager Maven soient compatibles avec AEM Cloud Service. À un niveau élevé, AEM exige une séparation du contenu et du code en sous-packages discrets pour respecter la division entre le contenu mutable et le contenu non mutable. Utilisez l’outil [Repository Modernizer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/repo-modernizer.html?lang=fr) pour restructurer les packages de projets existants en séparant le contenu et le code en packages distincts compatibles avec la structure de projet définie par Adobe Experience Manager as a Cloud Service.


+++

<!-- 

### HTML5 Forms (Mobile Forms)

The service does not support HTML5 Forms (Mobile Forms). If you render your XDP-based forms as HTML5 Forms, you can continue using the feature on AEM 6.5 Forms.

### Adaptive Forms 

* **XSD-Based Adaptive Forms:** The service does not support HTML5 Forms (Mobile Forms). If you render your XDP-based forms as HTML5 Forms, you can continue using the feature on AEM 6.5 Forms. You can use XDP-template to design a template for Document for Record. The service does not support XFA based Adaptive Forms  
* **Importing Adaptive Form templates:** Use build pipeline and corresponding Git repository of your program to import existing Adaptive Form templates. 
*  **Rule editor:** AEM Forms as a Cloud Service provides a hardened [Rule editor](rule-editor.md#visual-rule-editor). The code editor is not available on Forms as a Cloud Service. The migration utility helps you migrate your forms that have custom rules (created in code editor). The utility converts such rules into custom functions supported on Forms as a Cloud Service. You can use the reusable functions with Rule editor to continue obtaining results obtained with rule scripts  The `onSubmitError` or `onSubmitSuccess` functions are now available as actions the Rule Editor.  
* **Drafts and submissions:** The service does not retain metadata for drafts and submitted Adaptive Forms.  
* **Prefill Service:** By default, the prefill service merges data with an Adaptive Form at client as opposed to merging data on Server in AEM 6.5 Forms. The feature helps improve the time required to prefill an Adaptive Form. You can always configure to run the merge action on the Adobe Experience Manager Forms Server. 
* **Submit actions:** The **Email as PDF** action is not available. The **Email** submit action provide options to send attachments and attach Document of Record (DoR) with email. 
* **Components**:  The service does not support in-form signing experience and does not include the Summary and Verify components for Adaptive Forms.  
* **Forms portal**: Support for anonymous use of Forms portal is not available out of the box (OOTB). You can customize the forms portal to enable displaying forms for non-logged in users.

### Form Data Model

* Forms data model supports only HTTP and HTTPs endpoints to submit data. The service does not support Mutual SSL for REST connector and x509 certificate-based authentication for SOAP data sources. * Forms as a Cloud Service allows to use Microsoft Azure Blob, Microsoft Sharepoint, Microsoft OneDrive, and services supporting general CRUD (Create, Read, Update, and Delete) operations as data stores, both Open API specification 2.0 and Open API specification are supported. The service also provides support for JDBC connector.


### Automated Forms Conversion Service     

The service does not provide meta-model for Automated Forms Conversion Service. You can [download it from Automated Forms Conversion Service documentation](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=en#default-meta-model).


### Configurations

* Email support only HTTP and HTTPs protocols, by default. [Contact the support team](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html#sending-email) to enable ports for sending emails and to enable SMTP protocol for your environment.  
* If you use custom bundles, recompile your code with latest version of adobe-aemfd-docmanager before using these bundles with Forms as a Cloud Service. 


### Document Services: Document Manipulation APIs (Assembler Service)

The service does not support operations dependent on other services or applications:  

* Conversion of documents in a non-PDF format to a PDF format is not supported. For example, Microsoft Word to PDF, Microsoft Excel to PDF, and HTML to PDF are not supported. If your documents are in a non-PDF format. Convert such documents to PDF format before using those with Communications Document Manipulation APIs. For example, if your documents are in Microsoft Office, HTML, PostScript (PS), XDP format, convert these documents to PDF format before using those with PDF documents. 
* Adobe Distiller-based conversions are not supported. For example, PostScript(PS) to PDF
* Forms Service-based conversions are not supported. For example, XDP to PDF Forms.
* The service does not support converting a Signed PDF or Transparent PDF to another PDF format.
* Applying usage rights using Reader Extensions Service is not available. 
* The service does not provide the ability to convert signed or transparent PDF Documents to PDF/A format. 

### Document Services: Document Generation APIs (Output Service)

* In a single API call or batch, you can use one template with multiple DATA XML files. Using mutiple templates with multiple data files in a single API call is not supported. 

### Other differences

* A cloud-native environment does not have web console (configuration manager). You can use [[!DNL AEM Forms] as a Cloud Service SDK to generate configurations](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#generating-osgi-configurations-using-the-aem-sdk-quickstart) and CI/CD pipeline to [deploy the configuration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#deployment-process) to your Cloud Service instance.
* Email support only HTTP and HTTPs protocols, by default. [Contact the support team](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html#sending-email) to enable ports for sending emails and to enable SMTP protocol for your environment.
* The service does not support converting a Signed PDF or Transparent PDF to another PDF format.* Before using your customer bundles with Forms as a Cloud Service, recompile your custom code with the latest version of adobe-aemfd-docmanager* URL convention of localized Adaptive Forms now supports specifying a locale in the URL. New URL convention enables caching localized forms on a Dispatcher or CDN. On Cloud Service environment, use the URL format `http://host:port/content/forms/af/<afName>.<locale>.html` to request a localized version of an Adaptive Form instead of `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>`. Adobe recommends using Dispatcher or CDN caching. It helps improve rendering speed of prefilled forms 
* Adobe Experience Manager Forms as a Cloud Service brings many new features and possibilities into your AEM Projects. However, there are some changes required to Adobe Experience Manager Maven projects to be compatible with AEM Cloud Service. At a high-level, AEM requires a separation of content and code into discrete subpackages to respect the split between mutable and immutable content. Use the [Repository Modernizer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/repo-modernizer.html) tool to restructure existing project packages by separating content and code into discrete packages to be compatible with the project structure defined for Adobe Experience Manager as a Cloud Service.
-->




