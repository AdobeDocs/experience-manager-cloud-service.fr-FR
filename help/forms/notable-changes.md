---
title: Quelles sont les différences entre AEM 6.5 Forms et les Cloud Service AEM ?
description: Comparez AEM Forms 6.5 et AEM Cloud Services et découvrez les modifications les plus importantes avant de procéder à la mise à niveau ou à la migration vers Cloud Service.
exl-id: 46fcc1b4-8fd5-40e1-b0fc-d2bc9df3802e
role: Admin, Developer, User
feature: Adaptive Forms
contentOwner: khsingh
source-git-commit: a5179851af8ec88e23d79a74265b10cbce2d50f1
workflow-type: tm+mt
source-wordcount: '1325'
ht-degree: 63%

---

# Différence entre AEM 6.5 Forms (AMS et on-Prem) et AEM Forms as a Cloud Service (AEM CS Forms) {#notable-changes-for-existing-AEM-Forms-users}

Adobe Experience Manager Forms as a Cloud Service apporte des modifications notables aux fonctionnalités existantes par rapport aux environnements Adobe Experience Manager Forms On-Premise et [!DNL Adobe-Managed Service]. Les principales différences sont énumérées ci-dessous :

## Fonctionnalités natives du cloud

* Le service dispose d’une architecture native au cloud qui permet la mise à l’échelle automatique en fonction de la charge, de n’avoir aucun temps d’arrêt pour les mises à niveau, le déploiement fréquent et ultérieur de nouvelles fonctionnalités et mises à jour, ainsi que des topologies optimisées pour une résilience et une efficacité optimales.

* Le service n’inclut aucune action d’envoi qui stocke les données dans les instances de Cloud Service Adobe Experience Manager, ce qui le rend super sécurisé. Les données capturées par le biais de formulaires sont directement envoyées aux magasins de données configurés.

* Un réseau de diffusion de contenu (CDN) gratuit est également inclus pour vous aider à diffuser et rendre les formulaires plus rapidement.


## Mises à jour du flux de développement

* Le service fournit un SDK pour développer et tester du code personnalisé dans un environnement local (ordinateur local) avant de déployer le code sur un Cloud Service. Les développeurs et développeuses développent et testent des composants personnalisés, des thèmes, des applications de workflows, des configurations, des modèles, etc. à l’aide du SDK sur leurs ordinateurs locaux. Après avoir testé le code personnalisé dans leur environnement de développement local, ils et elles déploient le code personnalisé dans un [environnement CS de formulaires ou un environnement d’évaluation](/help/implementing/cloud-manager/deploy-code.md) pour effectuer d’autres tests avant de le promouvoir dans un environnement de production.

* Les développeurs et développeuses gèrent du code pour l’environnement de développement local et Cloud Service dans un [référentiel git](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/cloud-manager-repositories.html?lang=fr) commun. Un référentiel git, basé sur l’archétype AEM, est créé automatiquement lors de la création d’un programme AEM as a Cloud Service.

  ![création automatique du référentiel git sur AEM as a cloud service program](/help/forms/assets/git-repo-local-and-forms-cs.png)

* Le flux de développement pour Forms as a Cloud Service s’aligne sur l’archétype AEM pour AEM Cloud Service. Toutefois, certains changements sont nécessaires pour que les projets Adobe Experience Manager Maven soient compatibles avec AEM Cloud Service. À un niveau élevé, AEM exige une séparation du contenu et du code en sous-packages discrets pour respecter la division entre le contenu mutable et le contenu non mutable. Utilisez l’[outil Repository Modernizer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/repo-modernizer.html?lang=fr) pour restructurer les packages de projets existants en séparant le contenu et le code en packages distincts compatibles avec la structure de projet définie par Adobe Experience Manager as a Cloud Service.

* Avant d’utiliser les bundles de vos clients ou de vos clientes avec Forms as a Cloud Service, recompilez votre code personnalisé avec la dernière version d’adobe-aemfd-docmanager.

* Utilisez l’[utilitaire de migration d’AEM Forms as a Cloud Service](/help/forms/migrate-to-forms-as-a-cloud-service.md) pour préparer et migrer vos formulaires adaptatifs, thèmes, modèles et configurations cloud depuis <!-- AEM 6.3 Forms--> AEM 6.4 Forms sur OSGi et AEM 6.5 Forms sur OSGi vers [!DNL AEM] as a Cloud Service. Utilisez le [référentiel Git de votre programme](/help/implementing/cloud-manager/managing-code/managing-repositories.md) pour importer des modèles de formulaires adaptatifs existants.

* Par défaut, l’e-mail ne prend en charge que les protocoles HTTP et HTTPS. [Contactez l’équipe d’assistance](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=fr#sending-email) pour activer les ports d’envoi des emails et activer le protocole SMTP pour votre environnement.

## Localisation

* La convention d’URL de la Forms adaptative localisée prend désormais en charge la spécification d’un paramètre régional dans l’URL. La nouvelle convention d’URL permet la mise en cache de formulaires localisés sur Dispatcher ou CDN. Sur un environnement Cloud Service, utilisez le format d’URL `http://host:port/content/forms/af/<afName>.<locale>.html` pour demander une version localisée d’un formulaire adaptatif au lieu de `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>`.

* Adobe recommande d’utiliser la mise en cache du Dispatcher ou du CDN. Cela permet d’améliorer la vitesse de rendu des formulaires préremplis.


## Formulaires adaptatifs

* **Éditeur de règles :** AEM Forms as a Cloud Service fournit un [Éditeur de règles](rule-editor.md#visual-rule-editor) renforcé. L’éditeur de code n’est pas disponible sur Forms as a Cloud Service.

  L’ [utilitaire de migration](/help/forms/migrate-to-forms-as-a-cloud-service.md) vous aide à migrer les formulaires qui comportent des règles personnalisées (créées dans l’éditeur de code). L’utilitaire convertit ces règles en fonctions personnalisées prises en charge sur Forms as a Cloud Service. Vous pouvez utiliser les fonctions réutilisables avec l’éditeur de règles pour continuer à accéder aux résultats obtenus avec les scripts de règles. Les fonctions `onSubmitError` ou `onSubmitSuccess` sont désormais disponibles en tant qu’actions dans l’éditeur de règles.

<!--* **Prefill Service:** By default, the prefill service merges data with an Adaptive Form at client as opposed to merging data on Server in AEM 6.5 Forms. The feature helps improve the time required to prefill an Adaptive Form. You can always configure to run the merge action on the Adobe Experience Manager Forms Server.-->

* **Service de préremplissage :** le service de préremplissage récupère les données du serveur et les fusionne pour préremplir votre Forms adaptatif côté client. Cette fonctionnalité permet d’améliorer le temps nécessaire au remplissage d’un formulaire adaptatif. Vous pouvez toujours configurer le [service de préremplissage](https://experienceleague.adobe.com/docs/experience-manager-learn/forms/adaptive-forms/prefill-service-adaptive-forms-article-use.html?lang=fr) pour exécuter l’action de fusion sur le serveur Adobe Experience Manager Forms.

* **Actions d’envoi :** l’action d’envoi **Envoyer par e-mail** fournit des options pour envoyer des pièces jointes et joindre un document d’enregistrement (DE) par e-mail. Vous pouvez l’utiliser à la place de l’action **Email as PDF** disponible dans AEM Forms 6.5.

* **Service Automated forms conversion** : le service ne fournit pas de métamodèle pour le service Automated forms conversion. Vous pouvez [le télécharger à partir de la documentation Automated forms conversion Service](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=fr#default-meta-model).

* **Formulaires adaptatifs basés XSD :** vous pouvez utiliser un modèle XDP pour concevoir un modèle de document à enregistrer. Le service ne prend pas en charge le Forms adaptatif basé sur XFA.

* **Composants** : le service ne prend pas en charge l’expérience de signature dans le formulaire et n’inclut pas les composants Résumé et vérification pour le formulaire adaptatif.

* **Interface de l’assistant :** Vous pouvez utiliser l’ [interface de l’assistant](/help/forms/creating-adaptive-form-core-components.md) pour configurer rapidement les options communes et créer facilement un formulaire adaptatif.

## Portail Formulaires

* Le service ne conserve pas les métadonnées des brouillons et des formulaires adaptatifs envoyés.

## Document Services :

Forms as a Cloud Service fournit des API RESTful de génération de documents et de manipulation de documents. Vous pouvez utiliser ces API pour générer ou manipuler des documents à la demande ou par lots selon les besoins :

* **Services de document : API de génération de document (service de sortie)** : dans un seul appel d’API ou lot, vous ne pouvez utiliser qu’un seul modèle avec plusieurs fichiers XML de données. L’utilisation de plusieurs modèles avec plusieurs fichiers de données dans un seul appel API n’est pas prise en charge.

* **API de manipulation de documents (service Assembler)** :

   * Les opérations qui dépendent de services ou d’applications de documents ne sont pas disponibles. Par exemple, Microsoft® Word vers PDF, Microsoft® Excel vers PDF et l’HTML vers PDF, PostScript (PS) vers PDF, XDP vers PDF forms ne sont pas pris en charge. Ces opérations dépendent respectivement de Microsoft® Office, Adobe Acrobat, Adobe Distiller et Forms Document Service.

   * Convertissez les documents qui ne sont pas au format PDF en format PDF avant de les utiliser avec les API de manipulation de documents de communication. Par exemple, si vos documents sont au format Microsoft® Office, HTML, PostScript (PS) ou XDP, convertissez-les au format PDF avant de les utiliser avec des documents PDF. Vous pouvez utiliser le service [ConvertPDF](https://experienceleague.adobe.com/docs/experience-manager-65/forms/use-document-services/using-convertpdf-service.html?lang=fr) pour ce type de conversions.

   * Vous pouvez utiliser un environnement AEM 6.5 Forms pour les services Digital Signature, Encryption, Reader Extensions, Send to printer, Convert PDF et Barcoded Forms.


## Intégration de données (modèle de données de formulaire)

* Le service fournit également la prise en charge du connecteur JDBC, de Microsoft® Dynamics, de SalesForce, de services web basés sur SOAP et des services qui prennent en charge OData.

* Vous pouvez également connecter le profil utilisateur AEM pour récupérer et mettre à jour les informations utilisateur.

* Le modèle de données de formulaire ne prend en charge que les points d’entrée HTTP et HTTPS pour l’envoi de données. Le service ne prend pas en charge le protocole d’authentification SSL mutuelle pour le connecteur REST ni l’authentification par certificat x509 pour les sources de données SOAP.

* Forms as a Cloud Service permet d’utiliser Microsoft® Azure Blob, Microsoft® SharePoint, Microsoft® OneDrive et les services prenant en charge les opérations CRUD générales (création, lecture, mise à jour et suppression) en tant que entrepôts de données. Les spécifications Open API 2.0 et Open API 3.0 sont prises en charge.


## E-Sign

* Le service fournit une intégration prête à l’emploi à Adobe Sign et prend en charge DocuSign pour les signatures électroniques.

* Le service prend également en charge les rôles Adobe Sign. Vous pouvez configurer les rôles dans l’éditeur de Forms adaptatif pour que les utilisateurs professionnels configurent facilement les processus de signature.


## Formulaires HTML5

* Vous pouvez utiliser un environnement AEM 6.5 Forms pour :

   * effectuer le rendu de vos formulaires basés sur XDP en tant que formulaires HTML5. Le service ne prend pas en charge HTML5 Forms.

   * capturer des données hors ligne et les synchroniser la prochaine fois que vous revenez en ligne avec l’application [AEM Forms Workspace](https://experienceleague.adobe.com/docs/experience-manager-65/forms/use-aem-forms-workspace/introduction-html-workspace.html?lang=fr).

## Communications interactives

* Vous pouvez utiliser des API de communication pour créer des documents personnalisés à la demande ou par lots sur Forms as a Cloud Service. Vous pouvez utiliser un environnement AEM 6.5 Forms pour les communications interactives et l’interface utilisateur de l’agent.

## Voir également

* [Migration d’un AEM Forms (environnements On-Premise et AMS) vers AEM Forms as a Cloud Service](/help/forms/migrate-to-forms-as-a-cloud-service.md)
* [Ajout ou création d’une Forms adaptative à une page AEM Sites](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)
* [Créer un formulaire adaptatif (composants principaux)](/help/forms/creating-adaptive-form-core-components.md)
* [Présentation d’AEM Forms as a Cloud Service](/help/forms/home.md)
* [Configuration d’un environnement de développement local et d’un projet de développement initial](/help/forms/setup-local-development-environment.md)


<!--

## Additional Information

* [Introduction to AEM Forms as a Cloud Service](/help/forms/home.md)
* [Set up a local development environment and initial development project](/help/forms/setup-local-development-environment.md)

-->
