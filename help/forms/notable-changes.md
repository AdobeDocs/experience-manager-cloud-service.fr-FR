---
title: Différences entre AEM 6.5 Forms et AEM Cloud Services
description: Êtes-vous un utilisateur Experience Manager Forms qui souhaitez effectuer une mise à niveau vers Adobe Experience Manager Forms as a Cloud Service ? Comparez AEM Forms 6.5 et les services cloud AEM et découvrez les modifications les plus importantes avant de procéder à la mise à niveau ou à la migration vers Cloud Service.
exl-id: 46fcc1b4-8fd5-40e1-b0fc-d2bc9df3802e
contentOwner: khsingh
source-git-commit: 54a1ae1cc030030e44612b502b70c9b567144538
workflow-type: tm+mt
source-wordcount: '1352'
ht-degree: 14%

---

# Modifications notables apportées aux utilisateurs d’Adobe Experience Manager 6.5 Forms existants  {#notable-changes-for-existing-AEM-Forms-users}

Adobe Experience Manager Forms as a Cloud Service apporte quelques modifications notables aux fonctionnalités existantes par rapport à Adobe Experience Manager Forms On-Premise et [!DNL Adobe-Managed Service] des environnements. Les principales différences sont énumérées ci-dessous :

## Fonctionnalités natives du cloud

* Le service dispose d’une architecture native au cloud qui permet la mise à l’échelle automatique en fonction de la charge, du temps d’arrêt zéro pour les mises à niveau, du déploiement fréquent et ultérieur de nouvelles fonctionnalités et mises à jour, ainsi que des topologies optimisées pour une résilience et une efficacité optimales.

* Le service n’inclut aucune action d’envoi qui stocke les données dans les instances de Cloud Service Adobe Experience Manager, ce qui le rend super sécurisé. Les données capturées par le biais de formulaires sont directement envoyées aux entrepôts de données configurés.

* Un réseau de diffusion de contenu (CDN) gratuit est également inclus pour vous aider à diffuser et rendre les formulaires plus rapidement.


## Mises à jour du flux de développement

* Le service fournit un SDK pour développer et tester du code personnalisé dans un environnement local (ordinateur local) avant de déployer le code sur un Cloud Service. Les développeurs développent et testent des composants personnalisés, des thèmes, des applications de processus, des configurations, des modèles, etc. à l’aide du SDK sur leurs ordinateurs locaux. Après avoir testé le code personnalisé dans leur environnement de développement local, ils déploient le code personnalisé dans une [Développement de l’environnement Forms CS ou environnement intermédiaire](/help/implementing/cloud-manager/deploy-code.md) pour effectuer d’autres tests avant de le promouvoir dans un environnement de production.

* Les développeurs gèrent du code pour l’environnement de développement local et Cloud Service dans un environnement commun. [référentiel git](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/cloud-manager-repositories.html). Un référentiel git, basé sur AEM Archetype, est automatiquement créé lors de la création d’un programme as a Cloud Service AEM.

   ![](/help/forms/assets/git-repo-local-and-forms-cs.png)

* Le flux de développement pour Forms as a Cloud Service s’aligne sur AEM Archetype pour AEM Cloud Service. Toutefois, certains changements sont nécessaires pour que les projets Adobe Experience Manager Maven soient compatibles avec AEM Cloud Service. À un niveau élevé, AEM exige une séparation du contenu et du code en sous-packages discrets pour respecter la division entre le contenu mutable et le contenu non mutable. Utilisez l’outil [](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/repo-modernizer.html?lang=fr)Repository Modernizer pour restructurer les packages de projets existants en séparant le contenu et le code en packages distincts compatibles avec la structure de projet définie par Adobe Experience Manager as a Cloud Service.

* Avant d’utiliser les lots de vos clients avec Forms as a Cloud Service, recompilez votre code personnalisé avec la dernière version d’adobe-aemfd-docmanager.

* Utilisation [Utilitaire de migration as a Cloud Service AEM Forms](/help/forms/migrate-to-forms-as-a-cloud-service.md) pour préparer et migrer votre Forms adaptatif, vos thèmes, modèles et configurations cloud depuis <!-- AEM 6.3 Forms--> AEM 6.4 Forms sur OSGi et AEM 6.5 Forms sur OSGi à [!DNL AEM] as a Cloud Service. Utilisation [Référentiel Git de votre programme](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) pour importer des modèles de formulaires adaptatifs existants.

* Par défaut, les courriers électroniques ne prennent en charge que les protocoles HTTP et HTTP. [Contactez l’équipe d’assistance](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=fr#sending-email) pour activer les ports pour l’envoi d’e-mails et pour activer le protocole SMTP pour votre environnement.

## Localisation

* La convention d’URL des formulaires adaptatifs localisés prend désormais en charge la spécification d’un paramètre régional dans l’URL. La nouvelle convention d’URL permet de mettre en cache les formulaires localisés sur un Dispatcher ou un CDN. Dans un environnement de Cloud Service, utilisez le format d’URL. `http://host:port/content/forms/af/<afName>.<locale>.html` pour demander une version localisée d’un formulaire adaptatif au lieu de `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>`.

* Adobe recommande d’utiliser la mise en cache du Dispatcher ou du CDN. Cela permet d’améliorer la vitesse de rendu des formulaires préremplis.


## Formulaires adaptatifs

* **Éditeur de règles :** AEM Forms as a Cloud Service offre une fonction renforcée [Éditeur de règles](rule-editor.md#visual-rule-editor). L’éditeur de code n’est pas disponible sur Forms as a Cloud Service.

   Le [utilitaire de migration](/help/forms/migrate-to-forms-as-a-cloud-service.md) vous aide à migrer vos formulaires contenant des règles personnalisées (créées dans l’éditeur de code). L’utilitaire convertit ces règles en fonctions personnalisées prises en charge sur Forms as a Cloud Service. Vous pouvez utiliser les fonctions réutilisables avec l’éditeur de règles pour continuer à obtenir les résultats obtenus avec les scripts de règle. Le `onSubmitError` ou `onSubmitSuccess` Les fonctions sont désormais disponibles en tant qu’actions dans l’éditeur de règles.

* **Service de préremplissage :** Par défaut, le service de préremplissage fusionne les données avec un formulaire adaptatif au niveau du client plutôt que de fusionner les données sur le serveur dans AEM Forms 6.5. Cette fonctionnalité permet d’améliorer le temps nécessaire au préremplissage d’un formulaire adaptatif. Vous pouvez toujours configurer pour exécuter l’action de fusion sur le serveur Adobe Experience Manager Forms.

* **Actions Envoyer :** Le **Email** L’action d’envoi fournit des options pour envoyer des pièces jointes et joindre un document d’enregistrement à un courrier électronique. Vous pouvez l’utiliser à la place de la fonction **Email en tant que PDF** action disponible dans AEM 6.5 Forms.

* **automated forms conversion Service**: Le service ne fournit pas de métamodèle pour Automated forms conversion Service. Vous pouvez [téléchargez-le à partir de la documentation d’Automated forms conversion Service](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=en#default-meta-model).

* **Forms adaptatif basé sur XSD :** Vous pouvez utiliser XDP-template pour concevoir un modèle de document à enregistrer. Le service ne prend pas en charge le Forms adaptatif basé sur XFA

* **Composants**: Vous pouvez utiliser [Composants principaux de Forms adaptatif](/help/forms/creating-adaptive-form-core-components.md) pour concevoir vos formulaires. Ces composants sont basés sur les composants principaux de la gestion de contenu web, suivent les normes BEM et peuvent être facilement personnalisés. Le service ne prend pas en charge l’expérience de signature dans le formulaire et n’inclut pas les composants Résumé et vérification pour le formulaire adaptatif.

## Portail Formulaires

* Vous pouvez utiliser les composants Search &amp; Lister, Drafts and Submission et Link de Forms Portal pour répertorier les formulaires pour les utilisateurs connectés. La prise en charge de l’utilisation anonyme du portail Forms n’est pas disponible en standard (prête à l’emploi). Vous pouvez personnaliser Forms Portal pour activer l’affichage de formulaires pour les utilisateurs non connectés.

* Le service ne conserve pas les métadonnées des brouillons et des Forms adaptatives envoyées.

## Document Services:

Forms as a Cloud Service fournit des API RESTful de génération de documents et de manipulation de documents. Vous pouvez utiliser ces API pour générer ou manipuler des documents à la demande ou par lots, selon les besoins :

* **Document Services : API Document Generation (Output Service)**: Dans un seul appel API ou lot, vous ne pouvez utiliser qu’un seul modèle avec plusieurs fichiers XML de DONNÉES. L’utilisation de plusieurs modèles avec plusieurs fichiers de données dans un seul appel API n’est pas prise en charge.

* **API de manipulation de documents (service Assembler)**:

   * Les opérations qui reposent sur des services de document ou des applications ne sont pas disponibles. Par exemple, Microsoft Word vers PDF, Microsoft Excel vers PDF et HTML vers PDF, PostScript vers PDF, XDP vers PDF forms ne sont pas pris en charge. Ces opérations dépendent respectivement de Microsoft Office, Adobe Acrobat, Adobe Distiller et Forms Document Service.

   * Convertissez les documents qui ne sont pas au format PDF en format PDF avant de les utiliser avec les API de manipulation de documents de communication. Par exemple, si vos documents sont au format Microsoft Office, HTML, PostScript (PS) ou XDP, convertissez-les au format PDF avant de les utiliser avec des documents PDF. Vous pouvez utiliser la variable [ConvertPDF](https://experienceleague.adobe.com/docs/experience-manager-65/forms/use-document-services/using-convertpdf-service.html) pour de telles conversions.

* Vous pouvez utiliser un environnement Forms AEM 6.5 pour les services Digital Signature, Encryption, Reader Extension, Send to printer, Convert PDF et Barcoded Forms.


## Intégration de données (modèle de données de formulaire)

* Le service fournit également la prise en charge du connecteur JDBC, de Microsoft Dynamics, de SalesForce, des services Web basés sur SOAP et des services qui prennent en charge OData.

* Vous pouvez également connecter AEM profil utilisateur pour récupérer et mettre à jour les informations utilisateur.

* Le modèle de données Forms ne prend en charge que les points d’entrée HTTP et HTTPS pour envoyer des données. Le service ne prend pas en charge le protocole SSL mutuel pour le connecteur REST et l’authentification par certificat x509 pour les sources de données SOAP.

* Forms as a Cloud Service permet d’utiliser Microsoft Azure Blob, Microsoft SharePoint, Microsoft OneDrive et les services prenant en charge les opérations CRUD (Create, Read, Update et Delete) générales en tant que entrepôts de données. Les spécifications Open API 2.0 et Open API 3.0 sont prises en charge.


## E-Sign

* Le service fournit une intégration prête à l’emploi avec Adobe Sign et prend en charge DocuSign pour les signatures électroniques.

* Le service prend également en charge les rôles Adobe Sign. Vous pouvez configurer les rôles dans l’éditeur de Forms adaptatif pour que les utilisateurs professionnels configurent facilement les processus de signature.


## Formulaires HTML5

* Vous pouvez utiliser un environnement Forms AEM 6.5 pour :

   * Effectuez le rendu de vos formulaires basés sur XDP en tant que Forms HTML5. Le service ne prend pas en charge HTML5 Forms (Mobile Forms).

   * capturer des données hors ligne et les synchroniser la prochaine fois que vous serez en ligne avec [Espace de travail AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-65/forms/use-aem-forms-workspace/introduction-html-workspace.html) application.

## Communications interactives

* Vous pouvez utiliser des API de communication pour produire des documents personnalisés à la demande ou par lots sur Forms as a Cloud Service. Vous pouvez utiliser un environnement Forms AEM 6.5 pour les communications interactives et les cas d’utilisation de l’interface utilisateur de l’agent.


