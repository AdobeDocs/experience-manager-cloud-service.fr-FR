---
title: Présentation d’ [!DNL AEM Forms]  as a Cloud Service
description: Découvrez AEM Forms et apprenez à créer des documents et du contenu de formulaire pour les entreprises. Découvrez Platform-as-a-Service (PaaS) et apprenez à gérer des formulaires numériques et des processus d’entreprise à l’échelle de l’organisation, ainsi qu’à connecter Forms aux sources de données actives.
landing-page-description: Découvrez comment utiliser les formulaires dans AEM as a Cloud Service.
exl-id: aa5ef10c-ba78-4a9d-8b2b-a72a7a306888
source-git-commit: 95e1981faf9532aa56cc8a2e18166d08f35ecf29
workflow-type: tm+mt
source-wordcount: '1251'
ht-degree: 23%

---

# Présentation {#introduction}

Adobe [!DNL Experience Manager Forms as a Cloud Service] propose aux entreprises une solution PaaS native cloud permettant de créer, de gérer, de publier et de mettre à jour des formulaires numériques complexes, tout en intégrant des données envoyées à des processus d’arrière-plan et des règles métier, et en enregistrant des données dans un magasin de données externe. Le service est toujours à jour, toujours disponible et évolue sans cesse.

Vous pouvez utiliser ce service pour créer et déployer des formulaires numériques interactifs et attrayants. Par exemple, prenez une organisation qui cherche à numériser son parcours d’inscription des clients. Elle dispose de plusieurs sources de données avec des données client existantes. Elle cherche à préremplir les formulaires, à ajouter des signatures électroniques à ses formulaires et à archiver les formulaires remplis en tant que fichiers PDF. En outre, l’entreprise dispose de plusieurs formulaires imprimés (formulaires PDF), et elle cherche également à convertir tous ses formulaires imprimés en formulaires numériques.

L’entreprise peut utiliser [!DNL AEM Forms] as a Cloud Service pour créer des formulaires numériques, connecter des formulaires à des sources de données existantes, intégrer des formulaires avec [!DNL Adobe Sign] pour ajouter des signatures électroniques aux formulaires et générer un document d’enregistrement pour archiver les formulaires envoyés en tant que fichiers PDF. L’entreprise peut également utiliser le service pour convertir ses formulaires PDF existants en formulaires numériques.

Elle peut utiliser [!DNL AEM Forms] as a Cloud Service et obtenir toutes ces fonctionnalités dans le cloud sans avoir besoin d’infrastructure locale. Ce service libère également les entreprises de cycles de mise à niveau complexes, car il est toujours à jour avec les dernières fonctionnalités.

## Fonctions clés {#key-features}

<!-- 
>[!BEGINTABS]

>[!TAB Adaptive Forms]

Adaptive Forms allows businesses to create and manage interactive, data-driven forms for their websites and other digital channels responsive, mobile-friendly forms without. </br> </br> Adaptive Forms in AEM also include a drag-and-drop form builder, which enables non-technical users to easily create and customize forms using pre-built form components such as text boxes, dropdown menus, and date pickers. This enables faster form creation and eliminates the need for extensive coding and development. </br> </br> In addition, AEM Adaptive Forms offer several other features, including: <ul><li>Advanced workflows for routing, approval, and submission of form data Real-time validation and error checking to ensure data accuracy </li><li>Integration with third-party data sources and APIs for pre-filling form fields or validating data </li><li>Advanced analytics and reporting capabilities to track form usage, conversion rates, and other key metrics </li><li>Integration with Adobe Sign and DocuSign for e-signatures </li>

>[!TAB Automated Forms Conversion Service]

Automated Forms Conversion Service allows businesses to convert legacy PDF-based forms into interactive, digital forms that can be easily managed and distributed online. The service helps: <ul><li>Save manual effort required to convert print forms to adaptive forms.</li><li>Applies patterns and appropriate validations during conversion</li><li>Generate Document of Record during conversion </li><li>Group commonly occurring fields into reusable form fragments </li> <li>Enables Adobe Analytics during conversion</li>

>[!TAB Communications API (Document Services)]

Communications APIs are a set of RESTful APIs (Application Programming Interfaces) that enable businesses to automate the creation, management, and delivery of personalized, data-driven communications. </br> </br> These APIs also enable businesses to integrate their communications workflows with third-party systems and data sources, allowing them to create highly targeted and personalized messages that are triggered by specific events or user behaviors. Some key features of AEM Forms Communications APIs include:<ul><li> Dynamic content delivery: The APIs allow businesses to create and deliver dynamic content that is tailored to individual users based on their preferences, behaviors, and past interactions with the business.</li> <li>Personalized messaging: The APIs enable businesses to personalize their communications by including user-specific data such as names, addresses, and purchase history.</li><li>Integration with back-end systems: The APIs can be integrated with a wide range of back-end systems, including CRMs, databases, and marketing automation platforms.</li><li> Generate Pixel Perfect PDF documents: The APIs generate pixel-perfect PDF documents that are customized with user-specific data and content. This feature enables businesses to create highly professional and polished documents, such as invoices, contracts, and statements, that are delivered to users in PDF format.

>[!TAB Advanced Analytics]

The service provides OOTB support to connect with Adobe Analytics. Connecting forms with Adobe Analytics provides several benefits for businesses, including: <ul><li> Improved understanding of user behavior: By connecting forms with Adobe Analytics, businesses can gain a deeper understanding of how users are interacting with their forms. This includes insights into user engagement, conversion rates, drop-off points, and other key metrics that can help businesses identify areas for improvement and optimize their forms for better user experiences. </li><li>Better targeting of marketing efforts: By analyzing user behavior on forms, businesses can gain valuable insights into user preferences and interests. This information can be used to better target marketing efforts and create more effective campaigns that drive engagement and conversions. </li><li> Reduced error rate: By integrating forms with Adobe Analytics, you can find insights about field with most errors and improve data quality, leading to better decision-making and more accurate insights. </li><li> Improved ROI: By optimizing forms based on insights gained from Adobe Analytics, businesses can improve conversion rates and drive more revenue from their digital channels. This can lead to a higher return on investment (ROI) for marketing and digital initiatives, helping businesses to achieve their goals and drive growth.</li>


>[!ENDTABS] -->


| Formulaires adaptatifs | Service de conversion automatisée de formulaires | API Communications | Intégrations | Forms Workflow |
|---|---|---|---|---|
| Adaptive Forms permet aux entreprises de créer et de gérer des formulaires interactifs pilotés par les données pour leurs sites web et d’autres canaux numériques réactifs et compatibles avec les appareils mobiles. | automated forms conversion Service permet aux entreprises de convertir des formulaires basés sur des PDF hérités en formulaires numériques interactifs qui peuvent être facilement gérés et distribués en ligne. | Les API de communications sont un ensemble d’API RESTful (interfaces de programmation d’applications) qui permettent aux entreprises d’automatiser la création, la gestion et la diffusion de communications personnalisées basées sur les données. | La plateforme peut s’intégrer à Adobe Sign et à DocuSign, ce qui facilite l’envoi et le suivi des demandes de signature numérique directement à partir de leurs formulaires adaptatifs pour les utilisateurs. </br></br>En outre, la plateforme peut s’intégrer à Adobe Analytics, ce qui permet aux entreprises d’obtenir des informations précieuses sur le comportement et les préférences des utilisateurs. </br></br> Enfin, AEM Forms Cloud Service permet aux utilisateurs d’incorporer directement des formulaires adaptatifs dans des pages AEM Sites, ce qui crée une expérience utilisateur transparente. | Les processus Forms dans Adobe Experience Manager (AEM) Forms sont conçus pour automatiser les processus d’entreprise impliquant des formulaires. Ces workflows automatisent le routage, la révision et l’approbation des formulaires lorsqu’ils passent par différentes étapes d’un processus d’entreprise. Les processus basés sur l’utilisation de Forms peuvent être créés visuellement à l’aide d’AEM Forms Workflow Designer et peuvent être intégrés à AEM Forms pour déclencher des processus lorsqu’un formulaire est envoyé. Les workflows peuvent être configurés pour acheminer les formulaires vers différents utilisateurs ou groupes en fonction de critères spécifiques et peuvent inclure des notifications et des rappels automatiques pour s’assurer que les formulaires sont traités en temps voulu. Dans l’ensemble, les processus basés sur l’utilisation de formulaires dans AEM Forms aident les entreprises à rationaliser leurs processus d’entreprise, à améliorer l’efficacité et à réduire les erreurs. |


<!--
| | |
|---|---|
| Adaptive Forms | Adaptive Forms allows businesses to create and manage interactive, data-driven forms for their websites and other digital channels responsive, mobile-friendly forms without. </br> </br> Adaptive Forms in AEM also include a drag-and-drop form builder, which enables non-technical users to easily create and customize forms using pre-built form components such as text boxes, dropdown menus, and date pickers. This enables faster form creation and eliminates the need for extensive coding and development. </br> </br> In addition, AEM Adaptive Forms offer several other features, including: <ul><li>Advanced workflows for routing, approval, and submission of form data Real-time validation and error checking to ensure data accuracy </li><li>Integration with third-party data sources and APIs for pre-filling form fields or validating data </li><li>Advanced analytics and reporting capabilities to track form usage, conversion rates, and other key metrics </li><li>Integration with Adobe Sign and DocuSign for e-signatures </li>|
| Automated Forms Conversion Service | Automated Forms Conversion Service allows businesses to convert legacy PDF-based forms into interactive, digital forms that can be easily managed and distributed online. The service helps: <ul><li>Save manual effort required to convert print forms to adaptive forms.</li><li>Applies patterns and appropriate validations during conversion</li><li>Generate Document of Record during conversion </li><li>Group commonly occurring fields into reusable form fragments </li> <li>Enables Adobe Analytics during conversion</li>|
| Communications API (Document Services) | Communications APIs are a set of RESTful APIs (Application Programming Interfaces) that enable businesses to automate the creation, management, and delivery of personalized, data-driven communications. </br> </br> These APIs also enable businesses to integrate their communications workflows with third-party systems and data sources, allowing them to create highly targeted and personalized messages that are triggered by specific events or user behaviors. Some key features of AEM Forms Communications APIs include:<ul><li> Dynamic content delivery: The APIs allow businesses to create and deliver dynamic content that is tailored to individual users based on their preferences, behaviors, and past interactions with the business.</li> <li>Personalized messaging: The APIs enable businesses to personalize their communications by including user-specific data such as names, addresses, and purchase history.</li><li>Integration with back-end systems: The APIs can be integrated with a wide range of back-end systems, including CRMs, databases, and marketing automation platforms.</li><li> Generate Pixel Perfect PDF documents: The APIs generate pixel-perfect PDF documents that are customized with user-specific data and content. This feature enables businesses to create highly professional and polished documents, such as invoices, contracts, and statements, that are delivered to users in PDF format.|
|Advanced Analytics| The service provides OOTB support to connect with Adobe Analytics. Connecting forms with Adobe Analytics provides several benefits for businesses, including: <ul><li> Improved understanding of user behavior: By connecting forms with Adobe Analytics, businesses can gain a deeper understanding of how users are interacting with their forms. This includes insights into user engagement, conversion rates, drop-off points, and other key metrics that can help businesses identify areas for improvement and optimize their forms for better user experiences. </li><li>Better targeting of marketing efforts: By analyzing user behavior on forms, businesses can gain valuable insights into user preferences and interests. This information can be used to better target marketing efforts and create more effective campaigns that drive engagement and conversions. </li><li> Reduced error rate: By integrating forms with Adobe Analytics, you can find insights about field with most errors and improve data quality, leading to better decision-making and more accurate insights. </li><li> Improved ROI: By optimizing forms based on insights gained from Adobe Analytics, businesses can improve conversion rates and drive more revenue from their digital channels. This can lead to a higher return on investment (ROI) for marketing and digital initiatives, helping businesses to achieve their goals and drive growth.</li>|

-->

## Dernières innovations {#latest-innovations}

>[!BEGINTABS]

>[!TAB &#x200B; Forms adaptatif sans affichage]

[Forms adaptatif sans affichage](https://experienceleague.corp.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html) est une solution pour créer et gérer des formulaires web sans interface utilisateur graphique dans la plateforme Adobe Experience Manager. Cette fonctionnalité permet aux entreprises de créer, publier et gérer des formulaires interactifs accessibles et interactifs via des API, plutôt que par le biais d’une interface utilisateur graphique classique. AEM Forms adaptatif sans affichage permet une plus grande flexibilité et évolutivité dans le développement et le déploiement de formulaires, ainsi qu’une meilleure expérience utilisateur grâce à la possibilité d’adapter la conception et les fonctionnalités de formulaire à des besoins spécifiques. En utilisant les fonctionnalités de la technologie AEM et sans interface utilisateur, cette solution offre une plate-forme robuste pour la création, la gestion et le déploiement de formulaires web pour divers cas d’utilisation et applications.


>[!TAB Composants principaux]

Le [Composants principaux de Forms adaptatif](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html#features) sont un ensemble de 24 composants Open Source compatibles avec BEM qui sont construits sur la base des composants principaux de la gestion de contenu web Adobe Experience Manager. Elles sont spécialement conçues pour être utilisées pour créer des Forms adaptatives, qui sont des formulaires qui s’adaptent au périphérique, au navigateur et à la taille d’écran de l’utilisateur.

Ces composants peuvent être utilisés pour créer des expériences de capture et d’inscription de données exceptionnelles en proposant un large éventail d’options de champ de formulaire, notamment des champs de texte, des cases à cocher, des menus déroulants, etc. Ils comprennent également des fonctionnalités telles que la validation, la logique conditionnelle et la conception réactive, qui peuvent être utilisées pour créer des formulaires conviviaux et faciles à utiliser.

En outre, comme ces composants sont Open Source, les développeurs peuvent facilement personnaliser et étendre les composants pour répondre aux besoins spécifiques de leur entreprise. Et ces composants sont construits sur une méthodologie BEM qui garantit qu&#39;ils sont extensibles et maintenables.


>[!TAB Microsoft PowerAutomate Connector &#x200B;]

Microsoft Power Automate Connector for AEM Forms est un connecteur qui vous permet d’intégrer Adobe Experience Manager (AEM) Forms à Microsoft Power Automate (précédemment appelé flux Microsoft). Power Automate est un service basé sur le cloud qui vous permet de créer des processus automatisés entre différentes applications et services.

Avec Power Automate Connector for AEM Form, vous pouvez créer des processus qui se déclenchent automatiquement en fonction de l’envoi d’un formulaire adaptatif. Par exemple, vous pouvez créer un workflow qui envoie automatiquement une notification électronique à une personne spécifique lorsqu’un utilisateur envoie un formulaire ou crée une tâche dans le planificateur Microsoft lorsqu’un utilisateur remplit un formulaire.

L’utilisation de Power Automate Connector for AEM Forms présente de nombreux avantages, notamment :

* **Automatisation**: Vous pouvez automatiser les tâches de routine et rationaliser les processus, ce qui vous permet de gagner du temps et de réduire les erreurs.

* **Intégration**: Le connecteur vous permet d’intégrer Adobe Experience Manager Forms à d’autres applications et services, ce qui vous permet de travailler avec un large éventail d’outils.

* **Personnalisation**: Vous pouvez créer des workflows adaptés à vos besoins spécifiques, avec la possibilité d’ajouter des actions, des conditions et des déclencheurs personnalisés.

* **Analytics**: Power Automate fournit des analyses et des rapports détaillés, ce qui vous permet de surveiller et d’optimiser vos workflows au fil du temps.

Dans l’ensemble, Power Automate Connector for AEM Forms est un puissant outil qui vous permet d’automatiser et d’intégrer votre AEM Forms à d’autres applications et services, ce qui améliore l’efficacité et la productivité.

>[!TAB Connecteurs de stockage Microsoft : OneDrive et SharePoint]

Les connecteurs de stockage Microsoft AEM Forms pour OneDrive et SharePoint sont des connecteurs qui vous permettent d’intégrer Adobe Experience Manager (AEM) Forms à Microsoft OneDrive et SharePoint. Ces connecteurs vous permettent de stocker et de gérer des données et des documents AEM Forms dans les solutions de stockage dans le cloud Microsoft.

Ces connecteurs vous permettent de stocker et de gérer des données et des documents AEM Forms dans Microsoft OneDrive. Avec ce connecteur, vous pouvez charger des fichiers de données et des pièces jointes vers OneDrive et SharePoint directement depuis AEM Forms.

L’utilisation des connecteurs de stockage AEM Forms Microsoft pour OneDrive et SharePoint présente plusieurs avantages :

* **Intégration**: Ces connecteurs vous permettent d’intégrer AEM Forms à des solutions de stockage dans le cloud Microsoft, ce qui vous permet d’exploiter la puissance de ces plateformes.

* **Collaboration**: OneDrive et SharePoint sont des plateformes de collaboration qui permettent aux membres de l’équipe de travailler ensemble sur des fichiers et des documents. En intégrant AEM Forms à ces plateformes, vous pouvez améliorer la collaboration et le travail d’équipe.

* **Sécurité**: OneDrive et SharePoint offrent des fonctionnalités de sécurité fiables, ce qui garantit que vos données et documents sont stockés et accessibles en toute sécurité.

Dans l’ensemble, les connecteurs de stockage AEM Forms Microsoft pour OneDrive et SharePoint sont de puissants outils qui vous permettent de stocker et de gérer des données et des documents AEM Forms dans les solutions de stockage dans le cloud Microsoft, ce qui améliore la collaboration et la sécurité.

>[!ENDTABS]

<!--

| | |
|---|---|
| Adaptive Forms | Adaptive Forms allows businesses to create and manage interactive, data-driven forms for their websites and other digital channels responsive, mobile-friendly forms without. </br> </br> Adaptive Forms in AEM also include a drag-and-drop form builder, which enables non-technical users to easily create and customize forms using pre-built form components such as text boxes, dropdown menus, and date pickers. This enables faster form creation and eliminates the need for extensive coding and development. </br> </br> In addition, AEM Adaptive Forms offer several other features, including: <ul><li>Advanced workflows for routing, approval, and submission of form data Real-time validation and error checking to ensure data accuracy </li><li>Integration with third-party data sources and APIs for pre-filling form fields or validating data </li><li>Advanced analytics and reporting capabilities to track form usage, conversion rates, and other key metrics </li><li>Integration with Adobe Sign and DocuSign for e-signatures </li>|
| Automated Forms Conversion Service | Automated Forms Conversion Service allows businesses to convert legacy PDF-based forms into interactive, digital forms that can be easily managed and distributed online. The service helps: <ul><li>Save manual effort required to convert print forms to adaptive forms.</li><li>Applies patterns and appropriate validations during conversion</li><li>Generate Document of Record during conversion </li><li>Group commonly occurring fields into reusable form fragments </li> <li>Enables Adobe Analytics during conversion</li>|
| Communications API (Document Services) | Communications APIs are a set of RESTful APIs (Application Programming Interfaces) that enable businesses to automate the creation, management, and delivery of personalized, data-driven communications. </br> </br> These APIs also enable businesses to integrate their communications workflows with third-party systems and data sources, allowing them to create highly targeted and personalized messages that are triggered by specific events or user behaviors. Some key features of AEM Forms Communications APIs include:<ul><li> Dynamic content delivery: The APIs allow businesses to create and deliver dynamic content that is tailored to individual users based on their preferences, behaviors, and past interactions with the business.</li> <li>Personalized messaging: The APIs enable businesses to personalize their communications by including user-specific data such as names, addresses, and purchase history.</li><li>Integration with back-end systems: The APIs can be integrated with a wide range of back-end systems, including CRMs, databases, and marketing automation platforms.</li><li> Generate Pixel Perfect PDF documents: The APIs generate pixel-perfect PDF documents that are customized with user-specific data and content. This feature enables businesses to create highly professional and polished documents, such as invoices, contracts, and statements, that are delivered to users in PDF format.|
|Advanced Analytics| The service provides OOTB support to connect with Adobe Analytics. Connecting forms with Adobe Analytics provides several benefits for businesses, including: <ul><li> Improved understanding of user behavior: By connecting forms with Adobe Analytics, businesses can gain a deeper understanding of how users are interacting with their forms. This includes insights into user engagement, conversion rates, drop-off points, and other key metrics that can help businesses identify areas for improvement and optimize their forms for better user experiences. </li><li>Better targeting of marketing efforts: By analyzing user behavior on forms, businesses can gain valuable insights into user preferences and interests. This information can be used to better target marketing efforts and create more effective campaigns that drive engagement and conversions. </li><li> Reduced error rate: By integrating forms with Adobe Analytics, you can find insights about field with most errors and improve data quality, leading to better decision-making and more accurate insights. </li><li> Improved ROI: By optimizing forms based on insights gained from Adobe Analytics, businesses can improve conversion rates and drive more revenue from their digital channels. This can lead to a higher return on investment (ROI) for marketing and digital initiatives, helping businesses to achieve their goals and drive growth.</li>|

Adaptive Forms enable organizations to quickly design and deploy responsive, mobile-friendly forms without the need for extensive coding or development. With Adaptive Forms, businesses can create complex, multi-step forms with conditional logic, validations, and integrations with back-end systems such as CRMs and databases.

Adaptive Forms in AEM also include a drag-and-drop form builder, which enables non-technical users to easily create and customize forms using pre-built form components such as text boxes, dropdown menus, and date pickers. This enables faster form creation and eliminates the need for extensive coding and development.

In addition, AEM Adaptive Forms offer several other features, including:

Advanced workflows for routing, approval, and submission of form data
Real-time validation and error checking to ensure data accuracy
Integration with third-party data sources and APIs for pre-filling form fields or validating data
Advanced analytics and reporting capabilities to track form usage, conversion rates, and other key metrics
Overall, AEM Adaptive Forms provide businesses with a powerful tool for creating and managing complex, interactive forms that can be easily integrated into their digital experiences. |




| Feature/Capability | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
| Cloud-native architecture | &#x2611;  | &#x2612; |
| Auto-scaling based on load | &#x2611;  | &#x2612; |
| Zero downtime for upgrades | &#x2611;  | &#x2612; |
| Feature roll-out frequency | Agile*  | Quarterly |
| CDN (content delivery network) included | &#x2611;  | &#x2612; | 
| Topologies optimized for maximum resilience and efficiency| &#x2611;  | &#x2612; | 
| Cloud-native development environment | &#x2611;  | &#x2612; | 
| Self-Service via Cloud Manager | &#x2611;  | &#x2612; | 
| Automated upgrades with Continuous Integration and Continuous Delivery (CI/CD) | &#x2611;  | &#x2612; | 
| Adaptive Forms | &#x2611; | &#x2611; | 
| Data Integration with multiple data sources| &#x2611; | &#x2611; | 
| Communications APIs (Document Services) | &#x2611;* | &#x2611; | 
| Automated Forms Conversion Service | &#x2611; | &#x2611; | 
| Integration with [!DNL Micosoft Power Automate] | &#x2611; | &#x2612; | 
| Integration with [!DNL Adobe Sign] | &#x2611; | &#x2611; | 
| Integration with [!DNL AEM Sites] | &#x2611; | &#x2611; | 
| Integration with [!DNL Adobe Launch] | &#x2611; | &#x2611; | 
| Integration with [!DNL Adobe Analytics] | &#x2611; | &#x2611; | 
| Easy connectivity with Microsoft Dynamics and Salesforce | &#x2611; | &#x2612; |
| Custom submit action for with [!DNL DocuSign] | &#x2611; | &#x2612; | 
| Microsoft Azure data store connector | &#x2611; | &#x2612; |
| Hardened Rule editor | &#x2611; | &#x2612; | 
| Forms Portal | &#x2611; | &#x2611; | 
| AEM Workflows | &#x2611; | &#x2611; | 
| Document of Record | &#x2611; | &#x2611; | 
| Adaptive Forms Wizard | &#x2611; | &#x2612; | 
| Custom XCI for Document of Record| &#x2611; | &#x2612; |
| Invisible Captcha | &#x2611; | &#x2611; |
| Reusable Form Data Model configurations | &#x2611; | &#x2611; |
| Acroform-based Document of Record | &#x2611; | &#x2611; | 
| Government ID based identity authentication for Adobe Sign enabled Adaptive Forms | &#x2611; | &#x2611; | 
| Document Security | &#x2612; | &#x2611; |


* [Notable changes in comparison to AEM 6.5 Forms](notable-changes.md)
* [Frequently asked questions](faq.md)

-->