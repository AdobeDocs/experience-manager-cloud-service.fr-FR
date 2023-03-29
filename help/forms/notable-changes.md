---
title: Différences entre AEM 6.5 Forms et AEM Cloud Services
description: Êtes-vous un utilisateur Experience Manager Forms qui souhaitez effectuer une mise à niveau vers Adobe Experience Manager Forms as a Cloud Service ? Comparez AEM Forms 6.5 et les services cloud AEM et découvrez les modifications les plus importantes avant de procéder à la mise à niveau ou à la migration vers Cloud Service.
exl-id: 46fcc1b4-8fd5-40e1-b0fc-d2bc9df3802e
contentOwner: khsingh
source-git-commit: dea6c266e5c10135a320f923dc77d0fd2050988e
workflow-type: tm+mt
source-wordcount: '1395'
ht-degree: 18%

---

# Modifications notables apportées aux utilisateurs d’Adobe Experience Manager 6.5 Forms existants  {#notable-changes-for-existing-AEM-Forms-users}

Adobe Experience Manager Forms as a Cloud Service apporte quelques modifications notables aux fonctionnalités existantes par rapport à Adobe Experience Manager Forms On-Premise et [!DNL Adobe-Managed Service] des environnements. Les principales différences sont énumérées ci-dessous :

<!-- 
<table>
    <thead>
        <tr>
            <th>AEM Forms Components</th>
            <th>Feature/Capability</th>
            <th>[!DNL AEM Forms] as a Cloud Service</th>
            <th>AEM 6.5 Forms on-premise </th>
            <th>AEM 6.5 Forms Adobe Managed Services </th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan="6">Cloud native features</td>
            <td>Cloud-native architecture</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Auto-scaling based on load</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Zero downtime for upgrades</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Feature roll-out frequency</td>
            <td>Monthly</td>
            <td>Quarterly</td>
            <td>Quarterly</td>
        </tr>
        <tr>
            <td>CDN (content delivery network) included</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Topologies optimized for maximum resilience and efficiency</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td rowspan="3">Developer environment <sup>6</sup></td>
            <td>Self-Service via Cloud Manager</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Cloud-native development environment</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        <tr>
            <td>Automated upgrades with Continuous Integration and Continuous Delivery (CI/CD)</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td rowspan="8">Third-party and Adobe integrations</td>
            <td>[!DNL Micosoft Power Automate] for business process automation</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>[!DNL Microsoft Dynamics] and [!DNL Salesforce] for Customer Relationship Management (CRM)</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Integration with [!DNL Microsoft Azure] for data storage</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>[!DNL DocuSign] for e-signatures</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>[!DNL Adobe Sign] for e-signatures</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>[Adobe Launch] to track usage and performance</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>[!DNL Adobe Analytics] to track usage and performance</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Google reCaptcha for adaptive challenges</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td rowspan="11">Adaptive Forms</td>
            <td>Automated Forms Conversion Service<sup>1</sup></td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Core Components</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Foundation Components</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Form creation wizard</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Rule Editor<sup>1</sup></td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Prefill Service <sup>1</sup></td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Auto-save an adaptive form</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>XSD-Based adaptive forms <sup>1</sup></td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>In-form signing experience for adaptive forms</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Submit an adaptive form to AEM Forms on JEE Workflows (Process Management)</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Summary, Verify, and Scribble Signature components for adaptive forms</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td rowspan="4">Forms Portal</td>
            <td>Drafts and Submission component <sup>2<sup></td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Search & Lister component</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Link component</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>List forms for non-logged in users <sup>2</sup></td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td rowspan="13">Data integration (Form Data Model) </td>
            <td>OData services</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Microsoft Dynamics</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>SalesForce</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Microsoft Azure Blob Storage</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>RESTful web services - Open API version 3.0 <sup>4</sup></td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>RESTful web services - Open API version 2.0 <sup>4</sup></td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>SOAP-based web services <sup>4</sup></td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Microsoft SQL Server</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>MySQL</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>IBM DB2</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
                <tr>
            <td>Oracle RDBMS</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>AEM user profile</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Sybase</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td rowspan="8">Communication APIs (Document Services)</td>
            <td>Document Generation (Output Service) <sup>3</sup></td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Document Manipulation (Assembler Service) <sup>3</sup></td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Signature Service</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Encryption service</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Reader Extension service</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Send to printer service</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Convert PDF service</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Barcoded Forms service </td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Document Security</td>
            <td>Document Security Extension for Microsoft Office (Digital Rights Management)</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td rowspan="2">HTML5 Forms <sup>5</sup></td>
            <td>HTML5 Forms</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Forms Workspace</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Interactive Communications</td>
            <td>Interactive Communications</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
    </tbody>
</table>


<!-- 

## Cloud native features 

| Feature/Capability | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
| Cloud-native architecture | &#x2705;  | --- |
| Auto-scaling based on load | &#x2705;  | --- |
| Zero downtime for upgrades | &#x2705;  | --- |
| Feature roll-out frequency | Agile*  | Quarterly |
| CDN (content delivery network) included | &#x2705;  | --- | 
| Topologies optimized for maximum resilience and efficiency| &#x2705;  | --- | 

## Integrations 

| Feature/Capability | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
| Integration with [!DNL Micosoft Power Automate] | &#x2705; | --- | 
| Integration with [!DNL DocuSign] | &#x2705; | --- | 
| Integration with [!DNL Microsoft Dynamics] and [!DNL Salesforce] | &#x2705; | --- |  
| Integration with Microsoft Azure data stores | &#x2705; | --- | 
| Integration with [!DNL Adobe Sign] | &#x2705; | &#x2705; | 
| Integration with [!DNL AEM Sites] | &#x2705;| &#x2705; | 
| Integration with [!DNL Adobe Launch] | &#x2705; | &#x2705; | 
| Integration with [!DNL Adobe Analytics] | &#x2705; | &#x2705; |
| Data integration (Form Data Model) | &#x2705; | &#x2705; |
 
## Adaptive forms <sup> 1 </sup>

| Feature/Capability | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
| Automated Forms Conversion Service  | &#x2705; | &#x2705; |
| Forms Portal Submissions | &#x2705; | &#x2705; | 
| Google Captcha integrations | &#x2705; | &#x2705; |
| Repeatable sections in an adaptive form | &#x2705;| &#x2705; |
| Form fragments | &#x2705; | --- |
| Hardened rule editor | &#x2705; | --- | 
| Form creation wizard | &#x2705; | --- |
| Auto-save an adaptive form | --- | &#x2705; |
| Scribble Signatures | --- | &#x2705; |
| XSD-Based adaptive forms | --- | &#x2705; |
| Using Adobe Sign to add signatures within an Adaptive Form | --- | &#x2705; |
|Submit to AEM Forms on JEE Workflows (Process Management)| --- | &#x2705; | 

## Communication APIs (Document Services <sup> 2 </sup>) and Document Security 

| Feature/Capability | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
| Document Generation (Output Service)| &#x2705; | &#x2705; |
| Document Manipulation (Assembler Service) | &#x2705; | &#x2705; |
| Signature service | --- | &#x2705; |
| Encryption service | --- | &#x2705; |
| Reader Extension service | --- | &#x2705; |
| Send to printer service | --- | &#x2705; |
| Convert PDF service | --- | &#x2705; |
| Barcoded Forms service | --- | &#x2705; |
| Document Security Extension for Microsoft Office (Digital Rights Management) | --- | &#x2705; | 

## Data integration (Form Data Model) <sup> 3 </sup>

| Data Sources | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
| OData services | &#x2705; (Version 4.0)|  --- | 
| Microsoft Dynamics| &#x2705;  | --- | 
| SalesForce|  &#x2705; | ---| 
| Microsoft Azure Blob Storage| &#x2705;  | --- | 
| RESTful web services Open API version 3.0| &#x2705; | --- |
| RESTful web services Open API version 2.0| &#x2705; | &#x2705; |
| SOAP-based web services| &#x2705;| &#x2705; |   
| MySQL| &#x2705; | &#x2705; | 
| Microsoft SQL Server| &#x2705; | &#x2705; | 
| IBM DB2| &#x2705; | &#x2705; | 
| Oracle RDBMS| &#x2705; | &#x2705; | 
| Sybase|  ---  | &#x2705; | 
| AEM user profile| --- | &#x2705; | 

## Form-centric workflows

| Feature/Capability | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
|Submit to AEM Forms on JEE Workflows (Process Management)| --- | &#x2705; | 

## HTML5 Forms<sup> 4 </sup> and Interactive Communications 

| Feature/Capability | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
| HTML5 Forms | --- | &#x2705; | 
| HTML5 Workspace| --- | &#x2705; | 
| Interactive Communications | --- | &#x2705; | 

## Developer environment <sup> 5 </sup>

| Feature/Capability | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
| Cloud-native development environment | &#x2705;  | --- | 
| Self-Service via Cloud Manager | &#x2705;  | --- | 
| Automated upgrades with Continuous Integration and Continuous Delivery (CI/CD) | &#x2705;  | --- | 


-->

## Fonctionnalités natives du cloud

* Le service dispose d’une architecture native au cloud qui permet la mise à l’échelle automatique en fonction de la charge, du temps d’arrêt zéro pour les mises à niveau, du déploiement fréquent et ultérieur de nouvelles fonctionnalités et mises à jour, ainsi que des topologies optimisées pour une résilience et une efficacité optimales.

* Le service fournit des fonctionnalités d’externalisation de données (aucune donnée n’est conservée sur le serveur pour tout type de traitement) et n’inclut aucune action d’envoi qui stocke les données dans des instances de Cloud Service Adobe Experience Manager, ce qui le rend super sécurisé. Les données capturées par le biais de formulaires sont directement envoyées aux entrepôts de données configurés.

* Un réseau de diffusion de contenu (CDN) gratuit est également inclus pour vous aider à diffuser et rendre les formulaires plus rapidement.


## Mises à jour du flux de développement

* Le service fournit un SDK pour développer et tester du code personnalisé dans un environnement local (ordinateur local) avant de déployer le code sur un Cloud Service. Les développeurs développent et testent des composants personnalisés, des thèmes, des applications de processus, des configurations, des modèles, etc. à l’aide du SDK sur leurs ordinateurs locaux. Après avoir testé le code personnalisé dans leur environnement de développement local, ils déploient le code personnalisé dans une [Développement de l’environnement Forms CS ou environnement intermédiaire](/help/implementing/cloud-manager/deploy-code.md) pour effectuer d’autres tests avant de le promouvoir dans un environnement de production.

* Les développeurs gèrent du code pour l’environnement de développement local et Cloud Service dans un environnement commun. [référentiel git](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/cloud-manager-repositories.html). Un référentiel git, basé sur AEM Archetype, est automatiquement créé lors de la création d’un programme as a Cloud Service AEM.

   ![](/help/forms/assets/git-repo-local-and-forms-cs.png)


* Un environnement conçu pour le cloud ne dispose pas de console web (gestionnaire de configuration). Vous pouvez utiliser le SDK [[!DNL AEM Forms] as a Cloud Service pour générer des configurations](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=fr#generating-osgi-configurations-using-the-aem-sdk-quickstart) et un pipeline CI/CD pour [déployer la configuration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=fr#deployment-process) sur votre instance de Cloud Service.

* Adobe Experience Manager Forms as a Cloud Service offre de nombreuses nouvelles fonctionnalités et possibilités de gestion pour vos projets AEM. Toutefois, certains changements sont nécessaires pour que les projets Adobe Experience Manager Maven soient compatibles avec AEM Cloud Service. À un niveau élevé, AEM exige une séparation du contenu et du code en sous-packages discrets pour respecter la division entre le contenu mutable et le contenu non mutable. Utilisez l’outil [Repository Modernizer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/repo-modernizer.html?lang=fr) pour restructurer les packages de projets existants en séparant le contenu et le code en packages distincts compatibles avec la structure de projet définie par Adobe Experience Manager as a Cloud Service.

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

* **Composants**: Le service ne prend pas en charge l’expérience de signature dans le formulaire et n’inclut pas les composants Résumé et vérification pour Forms adaptatif.

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

* Forms as a Cloud Service permet d’utiliser Microsoft Azure Blob, Microsoft SharePoint, Microsoft OneDrive et les services prenant en charge les opérations CRUD (Create, Read, Update et Delete) générales en tant que entrepôts de données. Les spécifications Open API 2.0 et Open API 3.0 sont prises en charge.

* Le service fournit également la prise en charge du connecteur JDBC, de Microsoft Dynamics, de SalesForce, des services Web basés sur SOAP et des services qui prennent en charge OData.

* Vous pouvez également connecter AEM profil utilisateur pour récupérer et mettre à jour les informations utilisateur.

* Le modèle de données Forms ne prend en charge que les points d’entrée HTTP et HTTPS pour envoyer des données. Le service ne prend pas en charge le protocole SSL mutuel pour le connecteur REST et l’authentification par certificat x509 pour les sources de données SOAP.


## E-Sign

* Le service fournit une intégration prête à l’emploi avec Adobe Sign et prend en charge DocuSign pour les signatures électroniques.


## Formulaires HTML5

* Vous pouvez utiliser un environnement Forms AEM 6.5 pour :

   * Effectuez le rendu de vos formulaires basés sur XDP en tant que Forms HTML5. Le service ne prend pas en charge HTML5 Forms (Mobile Forms).

   * capturer des données hors ligne et les synchroniser la prochaine fois que vous serez en ligne avec [Espace de travail AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-65/forms/use-aem-forms-workspace/introduction-html-workspace.html) application.

## Communications interactives

* Vous pouvez utiliser des API de communication pour produire des documents personnalisés à la demande ou par lots. Vous pouvez utiliser un environnement Forms AEM 6.5 pour les canaux web et l’interface utilisateur de l’agent.

## Extension Document Security pour Microsoft Office

* Document Security Extension for Microsoft Office (Digital Rights Management) prend en charge AEM 6.5 Forms. L’extension n’est pas disponible pour Forms as a Cloud Service.








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




