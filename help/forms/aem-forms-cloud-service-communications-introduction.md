---
title: Présentation de la fonctionnalité Communications de Forms as a Cloud Service
description: Fusionner automatiquement les données avec des modèles XDP et PDF ou générer une sortie aux formats PCL, ZPL et PostScript
exl-id: b6f05b2f-5665-4992-8689-d566351d54f1
source-git-commit: 22018450f6d4383f3df6a9f5382a0ad6b4058480
workflow-type: tm+mt
source-wordcount: '1137'
ht-degree: 91%

---

# Utilisation d’AEM Forms as a Cloud Service Communications {#frequently-asked-questions}

La fonctionnalité Communications vous permet de créer des documents personnalisés, normalisés et approuvés par la marque, tels que des correspondances commerciales, des récapitulatifs, des lettres de traitement des demandes, des avis de prestations, des factures mensuelles ou des kits de bienvenue.

Cette fonctionnalité fournit des API pour générer et manipuler les documents. Vous pouvez générer ou manipuler un document à la demande ou créer une tâche par lots pour générer plusieurs documents à des intervalles définis. Les API Communications fournissent les éléments suivants :

* Des fonctionnalités simplifiées de génération de documentation par lots et à la demande

* La possibilité de combiner, réorganiser et valider des documents PDF à la demande

* Des API HTTP pour une intégration plus facile aux systèmes existants Des API distinctes pour les opérations à la demande (faible latence) et par lots (opérations à débit élevé) sont incluses.

* un accès sécurisé aux données. Les API Communications se connectent aux données et n’y accèdent que depuis des référentiels de données désignés par les clients, ce qui sécurisent les communications de façon très fiable.

![Exemple de relevé de carte de crédit](assets/statement.png)
Un relevé de carte de crédit peut être créé à l’aide des API Communications. Cet exemple de relevé utilise le même modèle, mais des données distinctes pour chaque client selon son utilisation de la carte de crédit.

## Génération de documents

Les API de génération de documents de communication permettent de combiner un modèle (XFA ou PDF) avec des données client (XML) afin de générer des documents dans des formats PDF et d’impression tels que PS, PCL, DPL, IPL et ZPL. Ces API utilisent des modèles PDF et XFA avec des [données XML](communications-known-issues-limitations.md#form-data) pour générer un seul document à la demande ou plusieurs documents à l’aide d’une tâche par lots.

En règle générale, vous créez un modèle à l’aide de [Designer](use-forms-designer.md) et utilisez les API Communications pour fusionner les données avec le modèle. Votre application peut envoyer le document de sortie à une imprimante réseau, à une imprimante locale ou à un système de stockage pour archivage. Les workflows standard et personnalisés se présentent comme suit :

![Workflow de génération de documents Communications](assets/communicaions-workflow.png)

En fonction du cas d’utilisation, vous pouvez également rendre ces documents disponibles au téléchargement via votre site Web ou un serveur de stockage.

Voici quelques exemples d’API de génération de documents :

### Création de documents PDF {#create-pdf-documents}

Vous pouvez utiliser les API de génération de documents pour créer un document PDF basé sur un design de formulaire et des données de formulaire XML. La sortie est un document PDF non interactif. En d’autres termes, les utilisateurs ne peuvent pas saisir ni modifier les données de formulaire. Un processus de base consiste à fusionner les données de formulaire XML avec un design de formulaire pour créer un document PDF. L’illustration suivante présente la fusion d’un design de formulaire et de données de formulaire XML pour produire un document PDF.

![Création de documents PDF](assets/outPutPDF_popup.png)
Schéma : workflow standard de création d’un document PDF

### Créer un document PostScript (PS), Printer Command Language (PCL), Zebra Printing Language (ZPL) {#create-PS-PCL-ZPL-documents}

Vous pouvez utiliser des API de génération de documents pour créer des documents PostScript (PS), PCL (Printer Command Language) et Zebra Printing Language (ZPL) basés sur un design de formulaire XDP ou sur un document PDF. Ces API permettent de fusionner un design de formulaire avec des données de formulaire pour générer un document. Vous pouvez enregistrer le document dans un fichier et développer un processus personnalisé pour l’envoyer à une imprimante.

<!-- ### Processing batch data to create multiple documents

Communications APIs can create separate documents for each record within an XML batch data source. The APIs can also create a single document that contains all records (this functionality is the default). Assume that an XML data source contains ten records and you instruct the APIs to create a separate document for each record (for example, PDF documents). As a result, the APIs generate ten PDF documents.

The following illustration also shows Communications APIs processing an XML data file that contains multiple records. However, assume that you instruct the APIs to create a single PDF document that contains all data records. In this situation, the APIs generate one document that contains all of the records.

The following illustration shows Communications APIs processing an XML data file that con tains multiple records. Assume that you instruct the Communications APIs to create a separate PDF document for each data record. In this situation, the APIs generates a separate PDF document for each data record.

 -->

### Traitement des données par lots pour créer plusieurs documents {#processing-batch-data-to-create-multiple-documents}

Vous pouvez utiliser des API de génération de documents pour créer des documents distincts pour chaque enregistrement au sein d’une source de données par lots XML. Vous pouvez générer des documents en mode massif et asynchrone. Vous pouvez configurer différents paramètres pour la conversion, puis lancer le traitement par lots.

![Création de documents PDF](assets/ou_OutputBatchMany_popup.png)

<!-- You can can also create a single document that contains all records (this functionality is the default).  Assume that an XML data source contains ten records and you have a requirement to create a separate document for each record (for example, PDF documents). You can use the Communication APIs to generate ten PDF documents. -->

<!-- The following illustration shows the Communication APIs processing an XML data file that contains multiple records. However, assume that you instruct the Communication APIs to create a single PDF document that contains all data records. In this situation, the Communication APIs generate one document that contains all of the records.

![Create PDF Documents](assets/ou_OutputBatchSingle_popup.png)

The following illustration shows the Communication APIs processing an XML data file that contains multiple records. Assume that you instruct the Communication APIs to create a separate PDF document for each data record. In this situation, the Communication APIs generates a separate PDF document for each data record.

![Create PDF Documents](assets/ou_OutputBatchMany_popup.png)

For detailed information on using Batch APIs, see Communication APIs: Processing batch data to create multiple documents. 

### Flatten interactive PDF documents {#flatten-interactive-pdf-documents}

You can use document generation APIs to transform an interactive PDF document (for example, a form) to a non-interactive PDF document. An interactive PDF document lets users enter or modify data located in the PDF document fields. The process of transforming an interactive PDF document to a non-interactive PDF document is called flattening. When a PDF document is flattened, a user cannot modify the data located in the document’s fields. One reason to flatten a PDF document is to ensure that data cannot be modified.

You can flatten the following types of PDF documents:

* Interactive PDF documents created in Designer (that contain XFA streams).

* Acrobat PDF forms

If you attempt to flatten a non-interactive PDF document, an exception occurs.

### Retain Form State {#retain-form-state}

An interactive PDF document contains various elements that constitute a form. These elements may include fields (to accept or display data), buttons (to trigger events), and scripts (commands to perform a specific action). Clicking a button may trigger an event that changes the state of a field. For example, choosing a gender option may change the color of a field or the appearance of the form. This is an example of a manual event causing the form state to change.

When such an interactive PDF document is flattened using the Communications APIs, the state of the form is not retained. To ensure that the state of the form is retained even after the form is flattened, set the Boolean value _retainFormState_ to True to save and retain the state of the form. -->

## Manipulation de documents

Les API de manipulation de documents Communications permettent de combiner, de réorganiser et de valider des documents PDF. En règle générale, vous créez un DDX et l’envoyez aux API de manipulation de document pour assembler ou réorganiser un document. Le [document DDX](https://helpx.adobe.com/content/dam/help/en/experience-manager/forms-cloud-service/ddxRef.pdf) décrit comment utiliser les documents source pour générer un ensemble de documents désirés. La documentation de référence DDX fournit des informations détaillées sur toutes les opérations prises en charge. Voici quelques exemples de manipulation de documents :

### Assemblage de documents PDF

Vous pouvez utiliser les API de manipulation de documents pour assembler deux ou plusieurs documents PDF ou XDP en un seul document ou Portfolio de PDF. Vous pouvez assembler des documents PDF de différentes manières, dont voici quelques exemples :

* Assemblage dans un document PDF unique
* Création d’un portfolio PDF
* Assemblage de documents chiffrés
* Assemblage de documents à l’aide de la numérotation Bates
* Aplatissement et assemblage de documents

![Assemblage d’un document PDF unique à partir de plusieurs documents PDF](assets/as_document_assembly.png)
Schéma : assemblage d’un document PDF unique à partir de plusieurs documents PDF

### Désassemblage de documents PDF

Vous pouvez utiliser les API de manipulation de documents pour désassembler un document de PDF. Ces API peuvent extraire des pages du document source ou diviser un document source en fonction de signets. Cette tâche est particulièrement utile lorsque le document PDF d’origine a été créé à partir de plusieurs documents séparés, par exemple un ensemble d’articles.

* Extraction de pages d’un document source
* Division d’un document source en fonction de signets

![Division d’un document source en plusieurs documents en fonction de signets](assets/as_intro_pdfsfrombookmarks.png)
Schéma : division d’un document source en plusieurs documents en fonction de signets

### Conversion et validation de documents conformes à la norme PDF/A

Vous pouvez utiliser les API de manipulation de documents pour convertir un document de PDF en document conforme au PDF/A et déterminer si un document de PDF est compatible avec le PDF/A. PDF / A est un format d’archivage, prévu pour la conservation sur le long terme du contenu d’un document. Les polices sont incorporées dans le document et le fichier est décompressé. Par conséquent, un document PDF/A est généralement plus volumineux qu’un document PDF standard. De plus, un document PDF/A ne contient aucune donnée audio et vidéo.

## Types d’API de communication

Communications fournit des API HTTP pour la génération de documents à la demande et par lots :

* Les **[API synchrones](https://www.adobe.io/experience-manager-forms-cloud-service-developer-reference/)** sont adaptées aux scénarios de génération de documents à la demande, à faible latence et à enregistrement unique. Ces API sont plus adaptées aux cas d’utilisation basés sur une action de l’utilisateur. Par exemple, la génération d’un document une fois qu’un utilisateur a rempli un formulaire.

* Les **[API par lot (API asynchrones)](https://www.adobe.io/experience-manager-forms-cloud-service-developer-reference/)** sont adaptées aux scénarios de génération de documents multiples, à débit élevé et planifiés. Ces API génèrent des documents par lots. Il peut s’agir, par exemple, de factures de téléphone, de relevés de carte de crédit et de relevés de prestations générés tous les mois.

## Intégration 

La fonctionnalité Communications est disponible sous la forme d’un module autonome et d’un module complémentaire pour les utilisateurs de Forms as a Cloud Service. Vous pouvez contacter l’équipe des ventes d’Adobe ou votre représentant Adobe pour demander l’accès. Adobe autorise l’accès de votre entreprise et fournit les privilèges requis à la personne désignée comme administrateur au sein de votre entreprise. L’administrateur peut accorder l’accès aux développeurs (utilisateurs) de Forms as a Cloud Service dans votre entreprise pour utiliser les API.

Une fois l’intégration terminée, suivez les étapes suivantes pour activer la fonctionnalité Communications pour votre environnement Forms as a Cloud Service :

1. Connectez-vous à Cloud Manager et ouvrez votre instance AEM Forms as a Cloud Service.

1. Ouvrez l’option Modifier le programme, accédez à l’onglet Solutions et modules complémentaires, puis sélectionnez l’option **[!UICONTROL Formulaires - Communications]**.

   ![Communications](assets/communications.png)

   Si vous avez déjà activé l’option **[!UICONTROL Forms - Inscription numérique]**, sélectionnez l’option **[!UICONTROL Forms - Module complémentaire Communications]**.

   ![Module complémentaire](assets/add-on.png)

1. Cliquez sur **[!UICONTROL Mettre à jour]**.

1. Exécutez le pipeline de build. Une fois que le pipeline de build a réussi, les API Communications sont activées pour votre environnement.

>[!NOTE]
>
> Pour activer et configurer les API de manipulation de documents, ajoutez la règle suivante à la [Configuration du Dispatcher](setup-local-development-environment.md#forms-specific-rules-to-dispatcher) :
>
> `# Allow Forms Doc Generation requests`
> `/0062 { /type "allow" /method "POST" /url "/adobe/forms/assembler/*" }`

<!--

Communication help you combine a template and XML data to generate print documents in various formats. The service allows you to generate documents in synchronous and batch modes. The APIs enables you to create applications that let you:

  * Generate documents by populating template files (PDF and XDP) with XML data.
  * Generate output forms in various formats, including non-interactive PDF print streams.

Consider a scenario where you have one or more templates and multiple records of XML data for each template. You can use Communications APIs to generate a print document for each record.  You can also combine the records into a single document.  The result is a non-interactive PDF document. A non-interactive PDF document does not let users enter data into its fields.

 There are two main Communications APIs. The _generatePDFOutput_ generates PDFs, while the _generatePrintedOutput_ generates PostScript, ZPL, and PCL formats. These APIs are available as REST endpoints on your environment, both on author and publish instances. Since the publish instances are configured to scale faster than the author instances, it is recommended use these APIs via publish instances.

The first parameter of both the operations accept the path and name of the template file (for example ExpenseClaim.xdp). You can specify a fully qualified path, reference path of your AEM Repository, or path of a binary file. The second parameter accepts an XML document that is merged with the template while generating the output document.  

The [API reference documentation](https://documentcloud.adobe.com/link/track?uri=urn:aaid:scds:US:b1223732-ae0f-4921-bdc0-c31e48b56044) provides detailed information about all the parameters, authentication methods, and various services provided by APIs. The API reference documentation is also available in the .yaml format. You can download the .yaml for [Batch APIs](assets/batch-api.yaml) or [non-Batch API.yaml](assets/non-batch-api.yaml) file and upload it to postman to check functionality of APIs.

>[!VIDEO](https://video.tv.adobe.com/v/335771)

Uploading Communication APIs .yaml file to postman to check functionality of APIs.

## Using the Communications APIs {#workflows}

Typically, you create a template using [Designer](use-forms-designer.md) and use communications APIs ( generatePDFOutput and generatePrintedOutput) to:

* Convert these templates to various formats, including PDF, PostScript, ZPL, and PCL.
* Merge XML form data with a form design to generate a document.
* Generate a document without merging XML form data into the document. However, the primary workflow is merging data into the document.

Then, the output document is stored to a file. You can design custom workflows to send the file to a network printer, a local printer, or to a storage system for archival. A typical out of the box and custom workflows look like the following:

![Communications Workflow](assets/communicaions-workflow.png)

### Create PDF documents {#create-pdf-documents}

You can use the _generatePDFOutput_ API to create PDF document that is based on a form design and XML form data. The output is a non-interactive PDF document. That is, users cannot enter or modify form data. A basic workflow is to merge XML form data with a form design to create a PDF document. The following illustration shows the merging of a form design and XML form data to produce a PDF document.

![Create PDF Documents](assets/outPutPDF_popup.png)

### Create PostScript (PS), Printer Command Language (PCL), Zebra Printing Language (ZPL) document {#create-PS-PCL-ZPL-documents}

You can use Communications APIs to create PostScript (PS), Printer Command Language (PCL), and Zebra Printing Language (ZPL) document that are based on a XDP form design or PDF document. The _generatePrintedOutput_ API merges a form design with form data to generate a document. You can save the document to a file and develop a custom process to send it to a printer.

 ### Processing batch data to create multiple documents

Communications APIs can create separate documents for each record within an XML batch data source. The APIs can also create a single document that contains all records (this functionality is the default). Assume that an XML data source contains ten records and you instruct the APIs to create a separate document for each record (for example, PDF documents). As a result, the APIs generate ten PDF documents.

The following illustration also shows Communications APIs processing an XML data file that contains multiple records. However, assume that you instruct the APIs to create a single PDF document that contains all data records. In this situation, the APIs generate one document that contains all of the records.

The following illustration shows Communications APIs processing an XML data file that contains multiple records. Assume that you instruct the Communications APIs to create a separate PDF document for each data record. In this situation, the APIs generates a separate PDF document for each data record.

### Processing batch data to create multiple documents {#processing-batch-data-to-create-multiple-documents}

You create separate documents for each record within an XML batch data source. You can can also create a single document that contains all records (this functionality is the default). Assume that an XML data source contains ten records and you have a requirement to create a separate document for each record (for example, PDF documents). You can use the Communication APIs to generate ten PDF documents.

The following illustration shows the Communication APIs processing an XML data file that contains multiple records. However, assume that you instruct the Communication APIs to create a single PDF document that contains all data records. In this situation, the Communication APIs generate one document that contains all of the records.

![Create PDF Documents](assets/ou_OutputBatchSingle_popup.png)

The following illustration shows the Communication APIs processing an XML data file that contains multiple records. Assume that you instruct the Communication APIs to create a separate PDF document for each data record. In this situation, the Communication APIs generates a separate PDF document for each data record.

![Create PDF Documents](assets/ou_OutputBatchMany_popup.png)

For detailed information on using Batch APIs, see Communication APIs: Processing batch data to create multiple documents.

### Flatten interactive PDF documents {#flatten-interactive-pdf-documents}

You can use the Communications APIs to transform an interactive PDF document (for example, a form) to a non-interactive PDF document. An interactive PDF document lets users enter or modify data located in the PDF document fields. The process of transforming an interactive PDF document to a non-interactive PDF document is called flattening. When a PDF document is flattened, a user cannot modify the data located in the document’s fields. One reason to flatten a PDF document is to ensure that data cannot be modified.

You can flatten the following types of PDF documents:

* Interactive PDF documents created in Designer (that contain XFA streams).

* Acrobat PDF forms

If you attempt to flatten a non-interactive PDF document, an exception occurs.

### Retain Form State {#retain-form-state}

An interactive PDF document contains various elements that constitute a form. These elements may include fields (to accept or display data), buttons (to trigger events), and scripts (commands to perform a specific action). Clicking a button may trigger an event that changes the state of a field. For example, choosing a gender option may change the color of a field or the appearance of the form. This is an example of a manual event causing the form state to change.

When such an interactive PDF document is flattened using the Communications APIs, the state of the form is not retained. To ensure that the state of the form is retained even after the form is flattened, set the Boolean value _retainFormState_ to True to save and retain the state of the form.  -->
