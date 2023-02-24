---
title: Présentation d’ [!DNL AEM Forms]  as a Cloud Service
description: Découvrez AEM Forms et apprenez à créer des documents et du contenu de formulaire pour les entreprises. Découvrez Platform-as-a-Service (PaaS) et apprenez à gérer des formulaires numériques et des processus d’entreprise à l’échelle de l’organisation, ainsi qu’à connecter Forms aux sources de données actives.
landing-page-description: Découvrez comment utiliser les formulaires dans AEM as a Cloud Service.
exl-id: aa5ef10c-ba78-4a9d-8b2b-a72a7a306888
source-git-commit: b11979acc23efe5f1af690443180a6b456d589ed
workflow-type: tm+mt
source-wordcount: '1592'
ht-degree: 20%

---

# Présentation {#introduction}

Adobe [!DNL Experience Manager Forms as a Cloud Service] propose aux entreprises une solution PaaS native cloud permettant de créer, de gérer, de publier et de mettre à jour des formulaires numériques complexes, tout en intégrant des données envoyées à des processus d’arrière-plan et des règles métier, et en enregistrant des données dans un magasin de données externe. Le service est toujours à jour, toujours disponible et évolue sans cesse.

Vous pouvez utiliser ce service pour créer et déployer des formulaires numériques interactifs et attrayants. Par exemple, prenez une organisation qui cherche à numériser son parcours d’inscription des clients. Elle dispose de plusieurs sources de données avec des données client existantes. Elle cherche à préremplir les formulaires, à ajouter des signatures électroniques à ses formulaires et à archiver les formulaires remplis en tant que fichiers PDF. En outre, l’entreprise dispose de plusieurs formulaires imprimés (formulaires PDF), et elle cherche également à convertir tous ses formulaires imprimés en formulaires numériques.

L’entreprise peut utiliser [!DNL AEM Forms] as a Cloud Service pour créer des formulaires numériques, connecter des formulaires à des sources de données existantes, intégrer des formulaires avec [!DNL Adobe Sign] pour ajouter des signatures électroniques aux formulaires et générer un document d’enregistrement pour archiver les formulaires envoyés en tant que fichiers PDF. L’entreprise peut également utiliser le service pour convertir ses formulaires PDF existants en formulaires numériques.

Elle peut utiliser [!DNL AEM Forms] as a Cloud Service et obtenir toutes ces fonctionnalités dans le cloud sans avoir besoin d’infrastructure locale. Ce service libère également les entreprises de cycles de mise à niveau complexes, car il est toujours à jour avec les dernières fonctionnalités. Pour en savoir plus sur le service, voir :

## Fonctions clés {#key-features}


>[!BEGINTABS]

>[!TAB Formulaires adaptatifs]

Adaptive Forms permet aux entreprises de créer et de gérer des formulaires interactifs pilotés par les données pour leurs sites web et d’autres canaux numériques réactifs et compatibles avec les mobiles sans avoir à les utiliser. </br> </br> Les Forms adaptatives d’AEM incluent également un générateur de formulaires par glisser-déposer, qui permet aux utilisateurs non techniques de créer et de personnaliser facilement des formulaires à l’aide de composants de formulaire prédéfinis tels que des zones de texte, des menus déroulants et des sélecteurs de dates. Cela permet une création de formulaire plus rapide et élimine la nécessité d’un codage et d’un développement complets. </br> </br> En outre, AEM Forms adaptatif offre plusieurs autres fonctionnalités, notamment : <ul><li>Processus avancés de routage, d’approbation et d’envoi des données de formulaire Validation en temps réel et vérification des erreurs pour garantir la précision des données </li><li>Intégration à des sources de données et des API tierces pour préremplir des champs de formulaire ou valider des données </li><li>Fonctionnalités avancées d’analyse et de création de rapports pour effectuer le suivi de l’utilisation des formulaires, des taux de conversion et d’autres mesures clés </li><li>Intégration à Adobe Sign et DocuSign pour les signatures électroniques </li>

>[!TAB Service de conversion automatisée de formulaires]

automated forms conversion Service permet aux entreprises de convertir des formulaires basés sur des PDF hérités en formulaires numériques interactifs qui peuvent être facilement gérés et distribués en ligne. Le service aide à : <ul><li>réduire les efforts manuels requis pour la conversion de formulaires imprimés en formulaires adaptatifs ; </li><li>appliquer des modèles et des validations adaptés lors de la conversion ;</li><li>générer un document d’enregistrement au cours de la conversion ; </li><li>regrouper les champs récurrents en fragments de formulaire réutilisables ; </li> <li>activer Adobe Analytics pendant la conversion.</li>

>[!TAB API de communications (Document Services)]

Les API de communications sont un ensemble d’API RESTful (interfaces de programmation d’applications) qui permettent aux entreprises d’automatiser la création, la gestion et la diffusion de communications personnalisées basées sur les données. </br> </br> Ces API permettent également aux entreprises d’intégrer leurs processus de communication à des systèmes et sources de données tiers, ce qui leur permet de créer des messages très ciblés et personnalisés qui sont déclenchés par des événements spécifiques ou des comportements utilisateur. Voici quelques-unes des principales fonctionnalités des API de communications AEM Forms :<ul><li> Diffusion de contenu dynamique : Les API permettent aux entreprises de créer et de diffuser du contenu dynamique adapté aux utilisateurs individuels en fonction de leurs préférences, de leurs comportements et de leurs interactions antérieures avec l’entreprise.</li> <li>Messagerie personnalisée : Les API permettent aux entreprises de personnaliser leurs communications en incluant des données spécifiques à l’utilisateur telles que les noms, adresses et l’historique des achats.</li><li>Intégration aux systèmes principaux : Les API peuvent être intégrées à un large éventail de systèmes principaux, notamment des CRM, des bases de données et des plateformes d’automatisation marketing.</li><li> Générer des documents Pixel Perfect PDF : Les API génèrent des documents de PDF parfaits en pixels qui sont personnalisés avec des données et du contenu spécifiques à l’utilisateur. Cette fonctionnalité permet aux entreprises de créer des documents très professionnels et soignés, tels que des factures, des contrats et des récapitulatifs, qui sont remis aux utilisateurs au format PDF.

>[!TAB Analyses avancées]

Le service fournit une prise en charge prête à l’emploi pour se connecter à Adobe Analytics. La connexion de formulaires à Adobe Analytics offre plusieurs avantages aux entreprises, notamment : <ul><li> Amélioration de la compréhension du comportement des utilisateurs : En connectant les formulaires à Adobe Analytics, les entreprises peuvent mieux comprendre comment les utilisateurs interagissent avec leurs formulaires. Cela inclut des informations sur l’engagement des utilisateurs, les taux de conversion, les points de non-retour et d’autres mesures clés qui peuvent aider les entreprises à identifier les domaines à améliorer et à optimiser leurs formulaires pour de meilleures expériences utilisateur. </li><li>Meilleur ciblage des efforts marketing : En analysant le comportement des utilisateurs sur les formulaires, les entreprises peuvent obtenir des informations précieuses sur les préférences et les intérêts des utilisateurs. Ces informations peuvent être utilisées pour mieux cibler les efforts marketing et créer des campagnes plus efficaces qui favorisent l’engagement et les conversions. </li><li> Taux d&#39;erreur réduit : En intégrant les formulaires à Adobe Analytics, vous pouvez obtenir des informations sur les champs présentant le plus d’erreurs et améliorer la qualité des données, ce qui améliore la prise de décision et permet d’obtenir des informations plus précises. </li><li> Amélioration du retour sur investissement : En optimisant les formulaires en fonction des informations obtenues à partir d’Adobe Analytics, les entreprises peuvent améliorer les taux de conversion et générer plus de recettes à partir de leurs canaux numériques. Cela peut conduire à un retour sur investissement plus élevé pour les initiatives marketing et numériques, ce qui aide les entreprises à atteindre leurs objectifs et à stimuler la croissance.</li>


>[!ENDTABS]


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