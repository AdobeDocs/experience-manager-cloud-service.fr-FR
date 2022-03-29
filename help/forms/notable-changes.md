---
title: Ce qui a changé entre AEM 6.5 Forms et AEM Cloud Services
description: 'Êtes-vous un utilisateur Experience Manager Forms qui souhaitez effectuer une mise à niveau vers Adobe Experience Manager Forms as a Cloud Service ? Découvrez les modifications les plus importantes avant de mettre à niveau ou de migrer vers Cloud Service.  '
contentOwner: khsingh
exl-id: 46fcc1b4-8fd5-40e1-b0fc-d2bc9df3802e
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '1214'
ht-degree: 100%

---

# Modifications notables pour les utilisateurs Adobe Experience Manager Forms existants  {#notable-changes-for-existing-AEM-Forms-users}

Adobe Experience Manager Forms as a Cloud Service apporte des modifications notables aux fonctionnalités existantes par rapport aux environnements Adobe Experience Manager Forms On-Premise et [!DNL Adobe-Managed Service]. Les principales différences sont énumérées ci-dessous :

* Ce service fournit un environnement de développement local et un environnement de développement conçu pour le cloud. Vous pouvez utiliser un [environnement de développement local](setup-local-development-environment.md) pour développer et tester votre code personnalisé, les composants, les modèles, les thèmes, les formulaires adaptatifs et d’autres ressources avant de déployer ces ressources sur un environnement cloud. Cela permet d’accélérer le processus de développement.
* [!DNL AEM] as a Cloud Service est fourni avec un réseau de diffusion de contenu intégré. Son principal objectif est de réduire la latence en fournissant du contenu pouvant être mis en cache à partir des nœuds CDN en périphérie, près du navigateur. Il est entièrement géré et configuré afin de permettre des performances optimales des applications AEM.
* Un environnement conçu pour le cloud ne dispose pas de console web (gestionnaire de configuration). Vous pouvez utiliser le SDK [[!DNL AEM Forms] as a Cloud Service pour générer des configurations](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=fr#generating-osgi-configurations-using-the-aem-sdk-quickstart) et un pipeline CI/CD pour [déployer la configuration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=fr#deployment-process) sur votre instance de Cloud Service.

* La convention d’URL des formulaires adaptatifs localisés prend désormais en charge la spécification d’un paramètre régional dans l’URL. La nouvelle convention d’URL permet de mettre en cache les formulaires localisés sur un Dispatcher ou un CDN. Sur l’environnement Cloud Service, utilisez le format d’URL `http://host:port/content/forms/af/<afName>.<locale>.html` pour demander une version localisée d’un formulaire adaptatif au lieu de `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>`. Adobe recommande d’utiliser la mise en cache du Dispatcher ou du CDN. Cela permet d’améliorer la vitesse de rendu des formulaires préremplis.
* Le service de préremplissage fusionne les données avec un formulaire adaptatif sur un client. Il permet d’accélérer le préremplissage d’un formulaire adaptatif. Vous pouvez toujours procéder à la configuration pour exécuter l’action de fusion sur le serveur Adobe Experience Manager Forms.
* Par défaut, seuls les protocoles HTTP et HTTPs sont pris en charge. [Contactez l’équipe d’assistance](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=fr#sending-email) pour activer les ports pour l’envoi d’e-mails et pour activer le protocole SMTP pour votre environnement.
* Adobe Experience Manager Forms as a Cloud Service offre de nombreuses nouvelles fonctionnalités et possibilités de gestion pour vos projets AEM. Toutefois, certains changements sont nécessaires pour que les projets Adobe Experience Manager Maven soient compatibles avec AEM Cloud Service. À un niveau élevé, AEM exige une séparation du contenu et du code en sous-modules discrets pour respecter la division entre le contenu mutable et le contenu non mutable. Utilisez l’outil [Repository Modernizer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/repo-modernizer.html?lang=fr) pour restructurer les modules de projets existants en séparant le contenu et le code en modules distincts compatibles avec la structure de projet définie par Adobe Experience Manager as a Cloud Service.

<!--  If your Cloud Configuration contains a secret (password), create a separate Cloud Configuration for every Author instance (Developer, Stage, and Production). If a Cloud Configuration is also required on Publish instances, publish/replicate a separate Cloud Configuration for every Publish instance (Developer, Stage, and Production). 

* When you create a Cloud Configuration that contains a secret, each Cloud Service instance (Developer, Stage, and Production) uses its own encryption key to encrypt the password before storing it. So, manually create such Cloud Configuration for every Cloud Service instance (Developer, Stage, and Production). Also, do not store secrets used in a Cloud Configuration to your Cloud Manager Git repository.

* Use [!DNL Cloud Manager] [APIs to convert and provide your passwords as secrets](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#setting-values-via-api). Do not store plain text password or secrets on your environments. -->

* Utilisez les configurations spécifiques à un environnement pour les valeurs de configuration OSGi secrètes, telles que les mots de passe, les clés d’API privées ou toute autre valeur. Elles ne peuvent pas être stockées dans Git pour des raisons de sécurité. [Utilisez des configurations secrètes spécifiques à un environnement pour stocker les valeurs secrètes de tous les environnements Adobe Experience Manager as a Cloud Service, y compris ceux d’évaluation et de production](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=fr#when-to-use-secret-environment-specific-configuration-values).

Pour obtenir la liste complète des changements dans Adobe Experience Manager as a Cloud Service, voir [Ce qui est nouveau et ce qui est différent](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/what-is-new-and-different.html?lang=fr).

<!-- ## Feature comparison {#comparison}

[!DNL AEM Forms] as a Cloud Service and Experience Manager 6.5 Forms share a common set of features: Adaptive Forms, data integration, integration with [!DNL Adobe Sign], themes, templates, and forms management interface are identical. You can easily port your existing Adaptive Forms from an Experience Manager 6.5 Forms or an earlier version to [!DNL AEM Forms] as a Cloud Service.

### Features of AEM 6.5 Forms and [!DNL AEM Forms] as a Cloud Service {#feature-comparison}

The following table lists the major features of Experience Manager 6.5 Forms and provides information about whether the feature is partially or fully supported in [!DNL AEM Forms] as a Cloud Service, with a link to more information about the feature. The table also lists extra features available in [!DNL AEM Forms] as a Cloud Service.


| Feature/Capability | AEM 6.5 Forms | [!DNL AEM Forms] as a Cloud Service |
| - | - | - |
| Adaptive Forms | &#x2611; | &#x2611; |
| Data Integration | &#x2611; | &#x2611;(With some changes) |
| Automated Forms Conversion Service | &#x2611; | &#x2611; |
| Integration with Adobe Sign | &#x2611; | &#x2611;(With some changes) |
| Themes and Templates | &#x2611; | &#x2611; ([With some changes](themes.md#difference-in-themes))|
| Rule editor | &#x2611; | &#x2611; (With some changes) |
| Forms Portal | &#x2611; | --- |
| Integration with Adobe Analytics | &#x2611; | &#x2612; |
| Document Security | &#x2611; | &#x2612; | -->

<!-- ## New features {#comparison} -->



## Améliorations clés {#whats-new}

<!-- [!DNL AEM Forms] as a Cloud Service offers benefits like auto-scaling, cost-effectiveness, zero downtime for upgrades, and cloud-native development environment and more. The list does not stop here. The following features are are start and are available only for [!DNL AEM Forms] as a Cloud Service: -->

Les fonctionnalités et améliorations suivantes ne sont disponibles que sur [!DNL AEM Forms] as a Cloud Service :

**Éditeur visuel de règles**
Ce service offre un [éditeur visuel de règles](rule-editor.md#visual-rule-editor) renforcé. Le service a ajouté les fonctionnalités suivantes à l’éditeur visuel de règles pour vous aider à créer des règles compatibles :

* [Nouveaux événements d’envoi](working-with-adobe-sign.md#available-operator-types-and-events-in-rule-editor) : `Navigation`, `Step Completion`, `Successful Submission` et `Error`

* [Nouveau type de données `scope`](rule-editor.md#custom-functions). Vous pouvez utiliser le type de données `scope` dans une fonction personnalisée pour transmettre la portée entière d’un formulaire.

* Possibilité d’utiliser [@this pour spécifier un JSDoc dans une fonction personnalisée](rule-editor.md#custom-functions). Il permet d’appeler une fonction personnalisée en utilisant @this dans un principal composant.

* Possibilité d’ajouter des conditions pour les règles basées sur des propriétés.

**Composants principaux**
Les [composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr) sont un ensemble de composants WCM (Web Content Management, gestion de contenu web) normalisés pour AEM dont l’objectif est d’accélérer le développement et de réduire les coûts de maintenance de vos sites Web. [!DNL AEM Forms] as a Cloud Service prend en charge le composant principal **[!UICONTROL Conteneur AEM Forms]**. Vous pouvez utiliser le composant pour incorporer un formulaire adaptatif à une page AEM Sites.

**AEM Archetype pour Forms as a Cloud Service**
[AEM Archetype](https://github.com/adobe/aem-project-archetype/releases/tag/aem-project-archetype-27) vous aide à commencer le développement pour [!DNL AEM Forms] as a.Cloud Service. Vous pouvez utiliser la version 27 ou une version ultérieure d’archetype pour créer un modèle de projet compatible avec l’environnement [!DNL AEM Forms] as a Cloud Service. L’archétype comprend également quelques exemples de thèmes et de modèles pour vous aider à démarrer rapidement.

**Flux d’informations sécurisé et amélioré entre Forms et Sign**
L’[intégration des formulaires adaptatifs et d’Adobe Sign](working-with-adobe-sign.md) dans Cloud Service offre la possibilité d’une soumission instantanée des données et des signatures. Elle permet d’éviter que l’envoi du formulaire ne se fasse en signant l’état, ce qui permet d’accélérer les envois. En outre, le service n’enregistre aucune donnée sur les instances de Cloud Service; ce qui rend le processus de signature super sécurisé.

**Analyseur de bonnes pratiques et outils de migration**
L’analyseur de bonnes pratiques fournit une évaluation de votre implémentation AEM actuelle. Exécutez l’outil avant de [migrer vers Forms as a Cloud Service](migrate-to-forms-as-a-cloud-service.md). Il évalue la capacité de passer d’un déploiement Adobe Experience Manager (AEM) existant à un déploiement AEM as a Cloud Service.

Le service offre également une [expérience de migration améliorée](migrate-to-forms-as-a-cloud-service.md) pour vous aider à migrer facilement de [!DNL AEM 6.4 Forms] et [!DNL AEM 6.5 Forms] vers [!DNL AEM Forms] as a Cloud Service.

**Rendus de formulaire plus rapides et validations plus rapides côté serveur**
Le service utilise la mise en cache du CDN et du Dispatcher pour fournir des rendus plus rapides et des validations côté serveur pour les formulaires adaptatifs.

**Amélioration de CAPTCHA**
Vous pouvez désormais [valider les CAPTCHA](captcha-adaptive-forms.md) soit lors de l’envoi de formulaires adaptatifs, soit selon une logique d’entreprise. Vous pouvez également ajouter des conditions pour valider des CAPTCHA sur une action d’utilisateur et afficher ou masquer le composant de CAPTCHA dans un formulaire adaptatif en fonction des règles.

Le composant de CAPTCHA offre une intégration prête à l’emploi avec le service reCAPTCHA de Google. Vous pouvez également configurer davantage de services de CAPTCHA pour le composant, si nécessaire.

**Plusieurs gabarits de page pour le document d’enregistrement**
Vous pouvez désormais utiliser un gabarit de page différent pour chaque page d’un document d’enregistrement et contrôler le placement d’un panneau Formulaire adaptatif sur un document d’enregistrement avec des options de pagination.

**Ajouter des colonnes à des tableaux sans en-têtes**
Vous pouvez ajouter et supprimer des colonnes à des tableaux sans en-têtes. Des en-têtes masqués sont ajoutés à ces tableaux pour vous aider à ajouter et supprimer des colonnes. Ces en-têtes sont visibles lors de la création, mais restent masqués dans le formulaire publié. Les tables sans en-têtes se trouvent principalement dans les formulaires adaptatifs créés à l’aide du service de conversion des formulaires automatiques.

**Amélioration des actions d’envoi**
Vous pouvez utiliser l’action d’envoi [Envoyer un e-mail](configuring-submit-actions.md#send-email#send-email) pour envoyer un PDF du document d’enregistrement (DE) en pièce jointe.

**Regrouper les e-mails pour e processus**
Vous pouvez choisir d’[envoyer des e-mails de notification](aem-forms-workflow-step-reference.md#assign-task-step) à partir de l’étape Affecter une tâche à une seule personne ou à un groupe.

**Amélioration de l’étape Appeler le modèle de données de formulaire**
Vous pouvez désormais spécifier le chemin d’accès du dossier pour l’option Relatif à la charge utile des arguments de service d’entrée dans une étape Appeler le modèle de données de formulaire. Il vous permet de mapper un fichier présent dans le dossier spécifié à l’argument de service sans spécifier le nom de fichier exact.

**Amélioration de la lisibilité des fichiers de traduction** Sur Forms as a Cloud Service, l’ordre de lecture des champs et des panneaux d’un formulaire adaptatif et des clés de message des fichiers de traduction correspondants (fichiers .XLIFF) a une structure similaire. Cela permet d’améliorer la vitesse de traduction manuelle.

<!-- ## Feature comparison {#feature-comparison}

[!DNL AEM Forms] as a Cloud Service and [!DNL AEM 6.5 Forms] share some features like Adaptive Forms, Data Integration, and Forms Portal. You can easily port your existing Adaptive Forms from an [!DNL AEM 6.5 Forms] or an earlier version to [!DNL AEM Forms] as a Cloud Service.

### Features of [!DNL AEM 6.5 Forms] and [!DNL AEM Forms] as a Cloud Service {#aem-6.5-vs-aem-forms-as-a-cloud-service}

The following table lists the major features of [!DNL AEM 6.5 Forms] and provides information about the features coming soon to [!DNL AEM Forms] as a Cloud Service:

| Feature/Capability | AEM 6.5 Forms  | [!DNL AEM Forms] as a Cloud Service |
|---|---|---|
| Cloud-native architecture | &#x2612; | &#x2611;  |
| Auto-scaling based on load | &#x2612; | &#x2611;  |
| Zero downtime for upgrades | &#x2612; | &#x2611;  |
| Feature roll-out frequency | Quarterly | Agile*  |
| CDN (content delivery network) included | &#x2612; | &#x2611;  |
| Topologies optimized for maximum resilience and efficiency | &#x2612; | &#x2611;  |
| Cloud-native development environment | &#x2612; | &#x2611;  |
| Self-Service via Cloud Manager | &#x2612; | &#x2611;  |
| Automated upgrades with Continuous Integration and Continuous Delivery (CI/CD)| &#x2611; | &#x2611;  |
| Adaptive Forms | &#x2611; | &#x2611; |
| Data Integration | &#x2611; | &#x2611; |
| Automated Forms Conversion Service | &#x2611; | &#x2611; |
| Integration with [!DNL Adobe Sign] | &#x2611; | &#x2611; |
| Integration with [!DNL AEM Sites] | &#x2611; | &#x2611; |
| Enhanced Visual Rule editor | &#x2612; | &#x2611; |
| Forms Portal | &#x2611; | Coming Soon |
| Integration with [!DNL Adobe Analytics] | &#x2611; | Coming Soon |
| Integration with [!DNL Adobe Target] | &#x2611; | Coming Soon |
| Document Security | &#x2611; | &#x2612; |

`*` New features every month and bug fix updates on daily basis.

For a comprehensive list of changes in AEM as a Cloud Service, See [What is New and What is Different](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/overview/what-is-new-and-different.html) and [Notable changes in [!DNL AEM Forms] as a Cloud Service](notable-changes.md) -->
