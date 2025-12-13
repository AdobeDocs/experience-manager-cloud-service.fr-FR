---
title: Architecture d’AEM Forms as a Cloud Service pour les API de Forms et de communication adaptatifs
description: Découvrez l’architecture d’ [!DNL AEM Forms] as a Cloud Service pour en savoir plus sur l’évolutivité, la résilience et les performances de la plateforme.
role: Admin, Developer, User
feature: Adaptive Forms
exl-id: 9d677bee-50ca-460e-b503-6b7799900735
source-git-commit: 8f39bffd07e3b4e88bfa200fec51572e952ac837
workflow-type: tm+mt
source-wordcount: '1097'
ht-degree: 88%

---

# Architecture [!DNL AEM] Forms as a Cloud Service {#architecture}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/install-aem-forms/aem-forms-architecture-deployment.html?lang=fr) |
| AEM as a Cloud Service | Cet article |

[!DNL Adobe Experience Manager Forms] as a Cloud Service est une solution native cloud permettant aux entreprises de créer, de gérer, de publier et de mettre à jour des formulaires numériques et des communications complexes, tout en intégrant des données envoyées à des processus d’arrière-plan et des règles métier, et en enregistrant des données dans un magasin de données externe. Elle étend les possibilités d’[!DNL Adobe Experience Manager as a Cloud Service]. Pour en savoir plus sur la mise à l’échelle, le déploiement, les environnements et les autres infrastructures, consultez [Présentation de l’architecture d’ [!DNL Adobe Experience Manager as a Cloud Service]](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/core-concepts/architecture.html?lang=fr).

AEM Forms as a Cloud Service prend en charge deux cas d’utilisation principaux : l’inscription numérique et les communications client. Les illustrations suivantes illustrent l’architecture pour les deux cas d’utilisation.

## Inscription numérique à Forms

![Inscription numérique à Forms](assets/forms-cloud-service-architecture-forms-digital-enrollment.svg)

## Communications Forms

![Communication Forms](assets/forms-cloud-service-architecture-forms-communications.svg)

## Applicabilité et cas d’utilisation

### Assurance

## AEM Forms peut-il gérer les opérations d’assurance à grande échelle ?

Oui. Lorsqu’il est déployé à l’aide d’architectures recommandées sur Adobe Managed Services ou un cloud privé, AEM Forms prend en charge les envois de formulaires volumineux et les charges de travail à l’échelle de l’entreprise.

## AEM Forms est-il sécurisé pour les données d’assurance ?

Oui. AEM Forms prend en charge la transmission sécurisée des données, l’accès contrôlé et les mécanismes d’authentification des entreprises, ce qui le rend adapté à la gestion des données d’assurance sensibles.

## Composants

Forms as a Cloud Service comprend plusieurs composants :

### CDN (réseau de diffusion de contenu)

Chaque programme AEM Forms as a Cloud Service a accès au [service CDN intégré](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn.html?lang=fr). Il est inclus dans la licence de Forms en tant que Cloud Services.

### Création

Un auteur est une instance AEM Forms as a Cloud Service s’exécutant en mode d’exécution Auteur standard. Il est destiné aux utilisateurs internes, aux concepteurs de formulaires et aux développeurs. Un environnement d’auteur permet les fonctionnalités suivantes :

* La création et la gestion de formulaires
* La connexion au service de conversion automatisée de formulaires pour convertir des formulaires PDF ou XDP en formulaires adaptatifs
* La création et l’exécution de workflows centrés sur Forms
* La gestion des ressources de formulaires adaptatifs
* La gestion des ressources Communications
* Des API RESTful synchrones (API en temps réel) et les API par lots pour créer, assembler et diffuser des communications orientées sur la marque et personnalisées
* Des API synchrones pour combiner, réorganiser et valider des documents PDF

### Publication

Une instance de publication est une instance AEM Forms as a Cloud Service s’exécutant en mode d’exécution Publication standard. Les instances de publication sont destinées aux utilisateurs finaux des applications de formulaires (par exemple, les utilisateurs accédant à un site Web public et envoyant des formulaires). L’élément Publier active les fonctionnalités suivantes :

* Le rendu et l’envoi de formulaires pour les utilisateurs finaux
* Le transport de données de formulaire brutes envoyées pour être ultérieurement traitées et stockées dans le système d’enregistrement final
* La connexion à un stockage géré par le client pour stocker des données
* La connexion à Adobe Sign pour la signature électronique d’un document d’enregistrement d’envoi de formulaire adaptatif
* Des API synchrones pour créer, assembler et diffuser des communications personnalisées et orientées sur la marque
* Des API synchrones pour combiner, réorganiser et valider des documents PDF

La réplication inverse n’est pas disponible dans AEM as a Cloud Service pour envoyer du contenu et des données du service de publication vers le service de création. Cependant, vous pouvez configurer des formulaires adaptatifs s’exécutant en Publication pour envoyer des données à un workflow sur une instance Auteur (les workflows ne peuvent être exécutés que sur l’Auteur). Cette procédure s’avère utile dans les cas d’utilisation d’approbation.

#### Dispatcher

Le [Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/disp-overview.html?lang=fr) est l’outil de mise en cache et d’équilibrage de charge d’Adobe Experience Manager, qui peut être utilisé conjointement avec un serveur web de niveau élevé.

### Adobe Services

**Service de conversion automatisée de formulaires**

Le [Service de conversion automatisée de formulaires](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/introduction.html?lang=fr) convertit automatiquement vos formulaires PDF et XFA en formulaires adaptatifs réactifs, compatibles avec les différents appareils et basés sur le HTML5.

**Adobe Sign**

Adobe Sign est un service de signature électronique basé sur le cloud qui permet à l’utilisateur d’envoyer, de signer, de suivre et de gérer les processus de signature à l’aide d’un navigateur ou d’un appareil mobile. Vous pouvez intégrer Adobe Sign à un formulaire adaptatif pour automatiser les processus de signature, simplifier les processus à signature unique et multiple, et signer électroniquement des formulaires adaptatifs.

<!-- **PDF Service API**
Adobe’s PDF Services API lets create, combine, export, and extract data from PDFs through powerful and flexible cloud-based APIs. -->

### Stockage géré par le client

Forms as a Cloud Service propose des options pour stocker du contenu dans un système de stockage externe tel que Blob Store, Database ou un service de stockage. Vous pouvez également stocker des données de processus en cours (données variables de workflow AEM) qui contiennent des éléments de données personnelles sensibles (SPD) dans un référentiel géré par le client pour un traitement sécurisé. Adobe recommande de stocker uniquement les données sensibles sur les stockages gérés par le client.

Vous pouvez utiliser le **Connecteur de stockage unifié** pour vous connecter à Blob Storage et le **Modèle de données de formulaire (FDM)** pour vous connecter à des bases de données ou à des services principaux (RESTful, SOAP, Azure Blob Storage, etc.).

### Services de document

Les services de document sont les suivants :

* **Le service de sortie (Communications - API de génération de documents)** vous permet de créer des documents personnalisés, normalisés et approuvés par la marque, tels que des correspondances commerciales, des récapitulatifs, des lettres de traitement des demandes, des avis de prestations, des factures mensuelles ou des kits de bienvenue.

* **Le service Assembler (Communications - API de manipulation de documents)** permet de combiner, de réorganiser et de valider des documents PDF.

* **Le service de document d’enregistrement (DoR)** aide à générer un document d’enregistrement (DoR). Le service s’exécute dans ses propres capsules différentes instances de création et de publication de Forms as a Cloud Service. Il permet d’offrir de meilleures performances et d’adapter chacune des capsules en fonction de la charge.

### Cloud Manager 

Cloud Manager est un composant essentiel pour [AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/introduction.html?lang=fr). Cloud Manager est le point d’entrée unique pour les rôles de responsable des opérations et de développeurs de nos clients. Il s’agit de l’endroit à partir duquel les programmes et environnements AEM peuvent être gérés. Cloud Manager a évolué sous la forme d’un portail en libre-service où les principaux composants d’AEM as a Cloud Service peuvent être créés et configurés :

* Création et gestion des programmes
* Création et gestion des environnements AEM dans ces programmes
* Création et gestion des pipelines pour le déploiement du code client et de la configuration associée dans un environnement spécifique
* Obtention de notifications sur des événements de cycle de vie importants pour ces composants (par exemple, les mises à jour de produits)
Pour plus d’informations sur Cloud Manager, consultez [Comprendre Adobe Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/cloud-manager/understand-cloud-manager-for-aem.html?lang=fr) et [Présentation de Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html?lang=fr).

### Developer Console

Une Developer Console fournit divers détails sur chaque environnement Forms as a Cloud Service en cours d’exécution. Ces informations sont utiles pour déboguer l’environnement. Pour plus d’informations, consultez [Débogage AEM as a Cloud Service avec la Developer Console](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html?lang=fr).

<!--

+++CDN (Content Delivery Network):

Every AEM Forms as a Cloud Service program has access to Fastly CDN service. It is included in the licence of Forms as a Cloud Services.

+++

+++Adaptive Forms
Adaptive Forms enable customers to author web-friendly reflowable web forms and fragments that are used by the customers for their data capture needs. This feature enables customers to manage their complex data capture needs easily, by using multiple integrations with Adobe Sign, Document Services, Form Data Model (FDM), Automated Forms Conversion service, and more.

+++

+++Automated Forms Conversion Service (AFCS)
Automated Forms Conversion service helps accelerate digitization and modernization of data capture experience through automated conversion of PDF forms to adaptive forms. The service, powered by Adobe Sensei, automatically converts your PDF forms to device-friendly, responsive, and HTML5-based adaptive forms. While using the existing investments in PDF Forms and XFA, the service also applies appropriate validations, styling, and layout to adaptive form fields during conversion.

+++

+++Form Data Model (FDM)
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

Cloud Manager is an essential component to [AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/introduction.html?lang=fr). Each new tenant of the [!DNL AEM Forms] as a Cloud Service is first provisioned for Cloud Manager access. Cloud Manager is the single-entry point for the operations and developer persona of our customers. It is the place from where the AEM programs and environments can be managed. Cloud Manager has evolved as a self-service portal where the main components of the AEM as a Cloud Service can be created and configured:

* Creating and managing programs
* Creating and managing the AEM environments within the programs
* Creating and managing the pipelines for deploying the customer code and configuration to a particular environment
* Getting notified of important lifecycle events for these components (for example, product updates)
For more information about Cloud Manager, see [Understand Adobe Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/cloud-manager/understand-cloud-manager-for-aem.html?lang=fr) and [Introduction to Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html?lang=fr).

## Users and Authentication {#users-and-authentication}

AEM as a Cloud Service includes Admin Console support for AEM instances and Adobe Identity Management System (IMS) based authentication. The Admin Console allows administrators to centrally manage all Experience Cloud users. Users and Groups can be assigned to product profiles associated with AEM as a Cloud Service instances, allowing them to log in to that instance. For more information about users, authentication, and, and accessing an instance of AEM as a Cloud Service, see [IMS Support for [!DNL Adobe Experience Manager] as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=fr#introduction).

Various personas are involved in a typical [!DNL AEM Forms] project. After you log in to your [!DNL AEM Forms] as a Cloud Service instance, you can [add users in admin console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=fr) for personas applicable to your organization or project and [assign users to built-in groups](forms-groups-privileges-tasks.md) to provide them required privileges.

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
Also, one of the most common requirements for developers is quick access to the log files of the various environments. With [!DNL AEM Cloud Service], the log files of the different nodes in the Author, Publish are made available via the Cloud Manager, either in the form of files that can be downloaded or via APIs for tailing the logs. Due to the clear separation of code and content, developers can use a particular process for updating content as part of a deployment. The typical use cases for mutable content are:
* Standard “default” content that is part of the customer project (for example, folders, templates, workflows...)
* Search index definitions
* ACLs and permissions
* Service users and user groups
Set up your development environment, [Configure your CI/CD Pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=fr), and learn to [deploy your code](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html?lang=fr) on the environment. -->

### Création de formulaires adaptatifs {#local-development}

Lorsque vous configurez un environnement [!DNL AEM Forms] as a Cloud Service, vous configurez des environnements de développement, d’évaluation et de production. En outre, définissez et configurez un environnement de développement local pour des itérations et un développement rapides. Vous pouvez télécharger et paramétrer le SDK AEM et l’archive des fonctionnalités de module complémentaire d’[!DNL AEM Forms] pour configurer un environnement de développement [!DNL Forms] as a Cloud Service local.  Pour obtenir des instructions détaillées, voir [Configuration d’un environnement de développement local](setup-local-development-environment.md).

## Débogage {#debugging}

AEM as a Cloud Service s’exécute sur une infrastructure cloud en libre-service et évolutive. Les développeurs AEM doivent donc comprendre et déboguer les différents aspects d’AEM as a Cloud Service, de la génération et du déploiement à l’obtention des informations sur l’exécution des applications AEM. Pour plus d’informations, consultez [Débogage d’AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/overview.html?lang=fr).


>[!MORELIKETHIS]
>
>* [Présentation des communications AEM Forms as a Cloud Service](/help/forms/aem-forms-cloud-service-communications-introduction.md)
>* [Traitement Par Lots Des Communications AEM Forms as a Cloud Service](/help/forms/aem-forms-cloud-service-communications-batch-processing.md)
>* [Traitement des communications - API synchrones](/help/forms/aem-forms-cloud-service-communications.md)
