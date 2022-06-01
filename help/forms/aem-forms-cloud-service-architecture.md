---
title: Architecture d’Experience Manager [!DNL AEM Forms] as a Cloud Service
description: Découvrez l’architecture d’ [!DNL AEM Forms] as a Cloud Service pour en savoir plus sur l’évolutivité, la résilience et les performances de la plateforme.
source-git-commit: 494e37b24ab1c8432613d6a62a4c3a1d48d216ee
workflow-type: tm+mt
source-wordcount: '1049'
ht-degree: 25%

---


# [!DNL AEM] Architecture as a Cloud Service de Forms {#architecture}

[!DNL Adobe Experience Manager Forms] as a Cloud Service est une solution native au cloud qui permet aux entreprises de créer, gérer, publier et mettre à jour des formulaires et communications numériques complexes tout en intégrant les données envoyées aux processus principaux, aux règles métier et en enregistrant des données dans un entrepôt de données externe. Elle étend [!DNL Adobe Experience Manager as a Cloud Service]. Pour en savoir plus sur la mise à l’échelle, le déploiement, les environnements et d’autres infrastructures, voir [Présentation de l’architecture de [!DNL Adobe Experience Manager as a Cloud Service]](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/core-concepts/architecture.html?lang=fr).

AEM Forms as a Cloud Service prend en charge deux cas d’utilisation principaux : Inscription numérique et communications client. Les illustrations suivantes illustrent l’architecture pour les deux cas d’utilisation.

## Diagrammes d’architecture et de flux

|  |  |
|---|---|
| **Inscription numérique Forms** | ![Inscription numérique Forms](assets/forms-cloud-service-architecture-forms-digital-enrollment.svg) |
| **Forms Communications** | ![Forms-Communication](assets/forms-cloud-service-architecture-forms-communications.svg) |

## Composants

Forms as a Cloud Service comprend plusieurs composants :

### CDN (réseau de diffusion de contenu)

Chaque programme as a Cloud Service AEM Forms a accès à [service CDN intégré](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn.html). Il est inclus dans la licence de Forms en tant que Cloud Services.

### Création

Un auteur est une instance AEM Forms as a Cloud Service s’exécutant en mode d’exécution Auteur standard. Il est destiné aux utilisateurs internes, aux concepteurs de formulaires et aux développeurs. Un environnement de création permet les fonctionnalités suivantes :

* Création et gestion de formulaires.
* Connexion au service Automated forms conversion pour convertir un PDF ou un formulaire XDP en formulaire adaptatif.
* Création et exécution de workflows centrés sur Forms.
* Gestion des actifs de formulaires adaptatifs.
* Gestion des ressources de communication.
* API RESTful synchrones (API en temps réel) et API par lots pour créer, assembler et diffuser des communications orientées sur la marque et personnalisées.
* API synchrones pour combiner, réorganiser et valider des documents de PDF.

### Publication

Une instance de publication est une instance AEM Forms as a Cloud Service s’exécutant en mode d’exécution Publier standard. Les instances de publication sont destinées aux utilisateurs finaux des applications de formulaires (par exemple, les utilisateurs accédant à un site Web public et envoyant des formulaires). L’élément Publier active les fonctionnalités suivantes :

* Rendu et envoi de formulaires pour les utilisateurs finaux
* Transportation des données de formulaire brutes envoyées pour un traitement et un stockage ultérieurs dans le système d’enregistrement final.
* Connexion à un stockage géré par le client pour stocker des données.
* Connexion à Adobe Sign pour la signature électronique d’un enregistrement d’envoi de formulaire adaptatif.
* API de synchronisation pour créer, assembler et diffuser des communications personnalisées et orientées sur la marque.
* API de synchronisation pour combiner, réorganiser et valider des documents de PDF.

La réplication inverse n’est pas disponible sur AEM as a Cloud Service pour envoyer du contenu/des données du service de publication vers le service de création. Cependant, vous pouvez configurer une Forms adaptative s’exécutant sur Publier pour envoyer des données à un workflow sur un auteur (les workflows ne peuvent être exécutés que sur l’auteur). Ceci s’avère utile dans les cas d’utilisation d’approbation.

#### Dispatcher

[Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/disp-overview.html) est l’outil de mise en cache et/ou d’équilibrage de charge d’Adobe Experience Manager qui peut être utilisé avec un serveur web de niveau élevé.

### Services Adobe

**automated forms conversion Service**

[Service Automated forms conversion](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/introduction.html?lang=fr) convertit automatiquement vos formulaires PDF et XFA en formulaires adaptatifs compatibles avec les périphériques, réactifs et basés sur HTML5.

**Adobe Sign**

Adobe Sign est un service de signature électronique basé sur le cloud qui permet à l’utilisateur d’envoyer, de signer, de suivre et de gérer les processus de signature à l’aide d’un navigateur ou d’un appareil mobile. Vous pouvez intégrer Adobe Sign à un formulaire adaptatif pour automatiser les processus de signature, simplifier les processus à signature unique et multiple et signer électroniquement des formulaires adaptatifs.

<!-- **PDF Service API**
Adobe’s PDF Services API lets create, combine, export, and extract data from PDFs through powerful and flexible cloud-based APIs. -->

### Stockage géré par le client

Forms as a Cloud Service propose des options pour stocker du contenu dans un système de stockage externe tel que Blob Store, Database ou un service de stockage. Vous pouvez également stocker des données de processus en cours (données AEM variables de processus) qui contiennent des éléments de données personnelles sensibles (SPD) dans un référentiel géré par le client pour un traitement sécurisé. Adobe recommande de stocker uniquement les données sensibles sur les stockages gérés par le client.

Vous pouvez utiliser la variable **Connecteur de stockage unifié** pour vous connecter à Blob Storage et **Modèle de données de formulaire** pour vous connecter à des bases de données ou à des services principaux (RESTful, SOAP, Azure Blob Storage, etc.).

### Services de document

Les services de document sont les suivants :

* **Output Service (communications - API de génération de documents)** permet de créer des documents approuvés, personnalisés et normalisés par la marque, tels que des correspondances commerciales, des récapitulatifs, des lettres de traitement des demandes, des avis de prestations, des factures mensuelles ou des kits de bienvenue.

* **Assembler Service (Communications - API de manipulation de documents)** permet de combiner, de réorganiser et de valider des documents de PDF.

* **Service de document d’enregistrement (DoR)** aide à générer un document d’enregistrement (DE). Le service s’exécute dans ses propres capsules différentes instances de création et de publication de Forms as a Cloud Service. Cela permet d’offrir de meilleures performances et d’adapter les capsules indépendamment en fonction de la charge.

### Cloud Manager 

Cloud Manager est un composant essentiel pour [AEM en tant que Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/introduction.html). Il s’agit du point d’entrée unique pour les opérations et le personnage développeur de nos clients. Il s’agit de l’endroit à partir duquel les programmes et environnements AEM peuvent être gérés. Cloud Manager a évolué sous la forme d’un portail en libre-service où les principaux composants d’AEM as a Cloud Service peuvent être créés et configurés :

* Création et gestion des programmes
* Création et gestion des environnements AEM dans ces programmes
* Création et gestion des pipelines pour le déploiement du code client et de la configuration associée dans un environnement spécifique
* Recevoir des notifications sur les événements de cycle de vie importants pour ces composants (par exemple, les mises à jour des produits) Pour plus d’informations sur Cloud Manager, voir [Présentation d’Adobe Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/cloud-manager/understand-cloud-manager-for-aem.html?lang=fr) et [Présentation de Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html?lang=fr).

### Developer Console

Une console de développement fournit divers détails sur chaque environnement de service Forms as a Cloud en cours d’exécution. Ces détails sont utiles pour déboguer l’environnement. Pour plus d’informations, voir [Débogage AEM as a Cloud Service avec Developer Console](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html?lang=fr).

<!--

+++CDN (Content Delivery Network):

Every AEM Forms as a Cloud Service program has access to Fastly CDN service. It is included in the licence of Forms as a Cloud Services.

+++

+++Adaptive Forms
Adaptive Forms enable customers to author web-friendly reflowable web forms and fragments that are used by the customers for their data capture needs. This feature enables customers to manage their complex data capture needs easily, by leveraging multiple integrations with Adobe Sign, Document Services, Form Data Model, Automated Forms Conversion service, and more.

+++

+++Automated Forms Conversion Service (AFCS)
Automated Forms Conversion service helps accelerate digitization and modernization of data capture experience through automated conversion of PDF forms to adaptive forms. The service, powered by Adobe Sensei, automatically converts your PDF forms to device-friendly, responsive, and HTML5-based adaptive forms. While leveraging the existing investments in PDF Forms and XFA, the service also applies appropriate validations, styling, and layout to adaptive form fields during conversion.

+++

+++Form Data Model
The Form Data Model (FDM) feature is the standard way of creating data integrations with external/internal data sources and using them across the different Forms as a Cloud Service features. FDM provides a rich editor for customers to integrate, define, and manage relationships between the different entities and data sources and perform operations on them. Form data is stored in a data store hosted on the customer premises. Organizations can also use blob store hosted by the cloud provider and Adobe Experince Platform to store data.

+++

+++Forms Workflows
Forms-centric workflows is an extension to the default AEM Workflow and provides our customers with additional workflow capabilities like Form Data review, task assignment, and document services invocation.

+++

+++Communications
Forms as a Cloud Service offering consists of multiple services tailored specifically for document processing.

+++

+++Document of Record
A Document of Record is a PDF version of a form. It provides an ability to keep a record of the information  that you provide and submit in an Adaptive Form in PDF fromat. The service provides a default DoR template and tools to develop a custom template.

+++

## Terminologies

<!-- ## Cloud Manager{#cloud-manager}

Cloud Manager is an essential component to [AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/introduction.html?lang=en). Each new tenant of the [!DNL AEM Forms] as a Cloud Service is first provisioned for Cloud Manager access. Cloud Manager is the single-entry point for the operations and developer persona of our customers. It is the place from where the AEM programs and environments can be managed. Cloud Manager has evolved as a self-service portal where the main components of the AEM as a Cloud Service can be created and configured:

* Creating and managing programs
* Creating and managing the AEM environments within the programs
* Creating and managing the pipelines for deploying the customer code and configuration to a particular environment
* Getting notified of important lifecycle events for these components (e.g. product updates)
For more information about Cloud Manager, see [Understand Adobe Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/cloud-manager/understand-cloud-manager-for-aem.html) and [Introduction to Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html).

## Users and Authentication {#users-and-authentication}

AEM as a Cloud Service includes Admin Console support for AEM instances and Adobe Identity Management System (IMS) based authentication. The Admin Console allows administrators to centrally manage all Experience Cloud users. Users and Groups can be assigned to product profiles associated with AEM as a Cloud Service instances, allowing them to log in to that instance. For more information about users, authentication, and, and accessing an instance of AEM as a Cloud Service, see [IMS Support for [!DNL Adobe Experience Manager] as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=en#introduction).

Various personas are involved in a typical [!DNL AEM Forms] project. After you log in to your [!DNL AEM Forms] as a Cloud Service instance, you can [add users in admin console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html) for personas applicable to your organization or project and [assign users to built-in groups](forms-groups-privileges-tasks.md) to provide them required privileges.

To learn various in-built [!DNL AEM Forms] specific user groups and privileges available on [!DNL AEM Forms] as a Cloud Services instance, see [Configure, user, roles and groups](forms-groups-privileges-tasks.md). 

## Developer Experience {#developer-experience}

The new architecture supporting AEM as a Cloud Service brings some key changes to the overall developer experience. One of the major goals for the changes to developer experience is to allow migration to AEM as a Cloud Service as quickly as possible, with little modifications to existing custom code.

## Cloud development {#cloud-development}

Here are the guidelines to run your existing code smoothly on AEM as a Cloud Service environment:

* Store your code and configurations to the Git repository of the associated Cloud Manager program. It makes managing and integrating code with CI/CD a breeze.  
* Make application code and configuration compatible with the baseline [!DNL AEM Forms] images. Using the latest APIs helps to build faster and secure applications.
* Use the Cloud Manager pipeline associated with the Cloud Manager environment to build and deploy applications. It helps you bring the latest features and bug fixed for [!DNL AEM Forms] as a Cloud Service to your environment.
* Try that your custom applications pass all the code quality, security, and performance gates enforced in the pipeline. It helps build secure and better performing applications which leads to better customer experience. You can always use Cloud Manager UI to skip some checks.
This process is commonly referred to as cloud-first development. [!DNL AEM Forms] as a Cloud Service also provides an SDK to support rapid development before the pending code and configuration changes are attempted in the cloud.
Some interfaces that were previously part of the AEM QuickStart are no longer available to the users of the AEM as a Cloud Service environment. For instance, the Web Console where OSGI bundles and their associated configuration are managed. The CRXDE Lite content repository browser becomes only accessible on non-production environment types. A subset of the Web Console functionalities that developers require, especially when it comes to diagnostics and status purposes, is made available via a new developer console.
Also, one of the most common requirements for developers is quick access to the log files of the various environments. With [!DNL AEM Cloud Service], the log files of the different nodes in the Author, Publish are made available via the Cloud Manager, either in the form of files that can be downloaded or via APIs for tailing the logs. Due to the clear separation of code and content, developers can leverage a particular process for updating content as part of a deployment. The typical use cases for mutable content are:
* Standard “default” content that is part of the customer project (e.g. folders, templates, workflows...)
* Search index definitions
* ACLs and permissions
* Service users and user groups
Set up your development environment, [Configure your CI/CD Pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html), and learn to [deploy your code](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html) on the environment. -->

### Création de formulaires adaptatifs {#local-development}

Lorsque vous configurez un environnement [!DNL AEM Forms] as a Cloud Service, vous configurez des environnements de développement, d’évaluation et de production. En outre, définissez et configurez un environnement de développement local pour des itérations et un développement rapides. Vous pouvez télécharger et paramétrer le SDK AEM et l’archive des fonctionnalités de module complémentaire d’[!DNL AEM Forms] pour configurer un environnement de développement [!DNL Forms] as a Cloud Service local.  Pour obtenir des instructions détaillées, voir [Configuration d’un environnement de développement local](setup-local-development-environment.md).

## Débogage {#debugging}

AEM as a Cloud Service s’exécute sur une infrastructure cloud en libre-service et évolutive. Pour cela, les développeurs AEM doivent comprendre et déboguer différentes facettes d’AEM as a Cloud Service, depuis la création et le déploiement jusqu’à l’obtention des détails sur l’exécution des applications d’AEM. Pour plus d’informations, voir [Débogage d’AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/overview.html).
