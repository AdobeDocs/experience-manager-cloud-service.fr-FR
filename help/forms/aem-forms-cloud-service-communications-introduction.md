---
title: Présentation de la fonctionnalité Communications de Forms as a Cloud Service
description: Fusionner automatiquement les données avec des modèles XDP et PDF ou générer une sortie aux formats PCL, ZPL et PostScript
exl-id: b6f05b2f-5665-4992-8689-d566351d54f1
source-git-commit: 8e20383a03f157f01da66bab930a3eccf674dde7
workflow-type: tm+mt
source-wordcount: '1840'
ht-degree: 93%

---

# Utilisation des communications as a Cloud Service AEM Forms {#frequently-asked-questions}

**La fonctionnalité de communications as a Cloud Service d’AEM Forms est en version bêta.**

La fonctionnalité de communication vous permet de créer des documents personnalisés, normalisés et axés sur la marque, tels que des correspondances commerciales, des récapitulatifs, des lettres de traitement des demandes, des avis de prestations, des factures mensuelles ou des kits de bienvenue.


Vous pouvez générer un document à la demande ou créer une tâche par lots pour générer plusieurs documents à des intervalles définis. Les API de communication fournissent les éléments suivants :

* fonctionnalités de génération de documentation par lots et à la demande simplifiées ;

* fournir des API HTTP pour une intégration plus facile aux systèmes existants ;

* un accès sécurisé aux données. Les API de communication se connectent aux données et y accèdent uniquement à partir de référentiels de données désignés par les clients, ne créent aucune copie locale de données, ce qui rend les communications hautement sécurisées ;

* des API distinctes pour les opérations de faible latence et de débit élevé, ce qui fait de la génération de documents une tâche efficace.

![Exemple de relevé de carte de crédit](assets/statement.png)

## Fonctionnement ?

Communications utilise des [modèles PDF et XFA](#supported-document-types) avec des [données XML](#form-data) pour générer un seul document à la demande ou plusieurs documents à l’aide d’une tâche par lots à intervalle défini.

Une API de communication permet de combiner un modèle (XFA ou PDF) avec des données client ([Données XML](#form-data)) pour générer des documents aux formats PDF et d’impression tels que PS, PCL, DPL, IPL et ZPL.

En règle générale, vous créez un modèle à l’aide de [Designer](use-forms-designer.md) et utiliser les API de communication pour fusionner les données avec le modèle. Votre application peut envoyer le document de sortie à une imprimante réseau, à une imprimante locale ou à un système de stockage pour archivage. Les workflows standard et personnalisés se présentent comme suit :

![Workflow Communications](assets/communicaions-workflow.png)

En fonction du cas d’utilisation, vous pouvez également rendre ces documents disponibles au téléchargement via votre site Web ou un serveur de stockage.

## API de communication

Les communications fournissent des API HTTP pour la génération de documents à la demande et par lots :

* Les **[API synchrones](https://adobedocs.github.io/experience-manager-forms-cloud-service-developer-reference/api/sync/)** sont adaptées aux scénarios de génération de documents à la demande, à faible latence et à enregistrement unique. Ces API sont plus adaptées aux cas d’utilisation basés sur une action de l’utilisateur. Par exemple, la génération d’un document une fois qu’un utilisateur a rempli un formulaire.

* Les **[API par lot (API asynchrones)](https://adobedocs.github.io/experience-manager-forms-cloud-service-developer-reference/api/batch/)** sont adaptées aux scénarios de génération de documents multiples, à débit élevé et planifiés. Ces API génèrent des documents par lots. Il peut s’agir, par exemple, de factures de téléphone, de relevés de carte de crédit et de relevés de prestations générés tous les mois.

## Intégration 

Les communications sont disponibles sous la forme d’un module autonome et complémentaire pour les utilisateurs de Forms as a Cloud Service. Vous pouvez contacter l’équipe commerciale d’Adobe ou votre représentant Adobe pour demander l’accès.

Adobe autorise l’accès de votre entreprise et fournit les privilèges requis à la personne désignée comme administrateur au sein de votre entreprise. L’administrateur peut accorder l’accès aux développeurs (utilisateurs) AEM Forms de votre entreprise pour utiliser les API.

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

## Considérations {#considerations-for-communications-apis}

Avant de commencer à générer des documents à l’aide des API de communication, tenez compte des points suivants :

### Données de formulaire {#form-data}

Les API de communication acceptent une conception de formulaire généralement créée dans [Designer](use-forms-designer.md) et les données de formulaire XML en tant qu’entrée. Pour remplir un document avec des données, un élément XML doit exister dans les données de formulaire XML pour chaque champ de formulaire à remplir. Le nom de l’élément XML doit correspondre au nom du champ. Un élément XML est ignoré s’il ne correspond pas à un champ de formulaire ou si le nom de l’élément XML ne correspond pas au nom du champ. Il n’est pas nécessaire de correspondre à l’ordre dans lequel les éléments XML sont affichés. Le facteur important est que les éléments XML sont spécifiés avec les valeurs correspondantes.

Examinez l’exemple de formulaire de demande de prêt suivant :

![Formulaire de demande de prêt](assets/loanFormData.png)

Pour fusionner les données dans ce design de formulaire, créez une source de données XML correspondant au formulaire. Le code XML suivant représente une source de données XML correspondant à l’exemple de formulaire de demande de prêt immobilier.

```XML
<?xml version="1.0" encoding="UTF-8" ?>
* <xfa:datasets xmlns:xfa="http://www.xfa.org/schema/xfa-data/1.0/">
* <xfa:data>
* <data>
    * <Layer>
        <closeDate>1/26/2007</closeDate>
        <lastName>Johnson</lastName>
        <firstName>Jerry</firstName>
        <mailingAddress>JJohnson@NoMailServer.com</mailingAddress>
        <city>New York</city>
        <zipCode>00501</zipCode>
        <state>NY</state>
        <dateBirth>26/08/1973</dateBirth>
        <middleInitials>D</middleInitials>
        <socialSecurityNumber>(555) 555-5555</socialSecurityNumber>
        <phoneNumber>5555550000</phoneNumber>
    </Layer>
    * <Mortgage>
        <mortgageAmount>295000.00</mortgageAmount>
        <monthlyMortgagePayment>1724.54</monthlyMortgagePayment>
        <purchasePrice>300000</purchasePrice>
        <downPayment>5000</downPayment>
        <term>25</term>
        <interestRate>5.00</interestRate>
    </Mortgage>
</data>
</xfa:data>
</xfa:datasets>
```

### Types de documents pris en charge {#supported-document-types}

Pour un accès complet aux fonctionnalités de rendu des API Communications, il est recommandé d’utiliser un fichier XDP comme entrée. Il est parfois possible d’utiliser un seul fichier PDF. Toutefois, l’utilisation d’un fichier PDF en entrée présente les restrictions suivantes :

Un document PDF qui ne contient pas de flux XFA ne peut pas être rendu au format PostScript, PCL ou ZPL. Les API de communication peuvent générer des documents de PDF avec des flux XFA (c’est-à-dire des formulaires créés dans [Designer](use-forms-designer.md)) en formats laser et d’étiquette. Si le document PDF est signé, certifié ou contient des droits d’utilisation (appliqués à l’aide du service AEM Forms Reader Extensions), il ne peut pas être rendu dans ces formats d’impression.

<!-- Run-time options such as PDF version and tagged PDF are not supported for Acrobat forms. They are valid for PDF forms that contain XFA streams; however, these forms cannot be signed or certified. 

### Email support {#email-support}

For email functionality, you can create a process in Experience Manager Workflows that uses the Email Step. A workflow represents a business process that you are automating. -->

### Zones imprimables {#printable-areas}

La marge non imprimable de 0,25 pouce par défaut n’est pas exacte pour les imprimantes d’étiquettes et varie d’une imprimante à l’autre et de la taille de l’étiquette à la taille de l’étiquette. Il est recommandé de conserver la marge de 0,25 pouce ou de la réduire. Il est toutefois recommandé de ne pas augmenter la marge non imprimable. Dans le cas contraire, les informations de la zone imprimable ne s’impriment pas correctement.

Assurez-vous toujours d’utiliser le fichier XDC approprié pour l’imprimante. Par exemple, évitez de choisir un fichier XDC pour une imprimante 300 dpi et d’envoyer le document vers une imprimante 200 dpi.

### Scripts {#scripts}

Un design de formulaire utilisé avec les API Communications peut contenir des scripts qui s’exécutent sur le serveur. Assurez-vous qu’un design de formulaire ne contient pas de scripts exécutés sur le client. Pour plus d’informations sur la création de scripts de conception de formulaire, voir [Aide de Designer](use-forms-designer.md).

<!-- #### Working with Fonts
 Document Considerations for Working with Fonts>> -->

### Mappage de polices {#font-mapping}

Pour concevoir un formulaire qui utilise des polices installées sur l’imprimante, choisissez dans Designer un nom de police correspondant aux polices disponibles sur l’imprimante. La liste des polices prises en charge pour PCL ou PostScript se trouve dans les profils d’appareils correspondants (fichiers XDC). Vous pouvez également créer un mappage des polices pour mapper les polices non installées sur l’imprimante aux polices installées sur l’imprimante d’un autre nom de police. Par exemple, dans un scénario PostScript, les références à la police Arial® peuvent être mappées à la police Helvetica® installée sur l’imprimante.

Si une police est installée sur un ordinateur client, elle est disponible dans la liste déroulante de Designer. Si la police n’est pas installée, il est nécessaire de la spécifier manuellement. L’option « Remplacer définitivement les polices non disponibles » dans Designer peut être désactivée. Dans le cas contraire, lorsque le fichier XDP est enregistré dans Designer, le nom de la police de substitution est écrit dans le fichier XDP. Cela signifie que la police installée sur l’imprimante n’est pas utilisée.

Il existe deux types de polices OpenType®. Un type est une police OpenType® TrueType prise en charge par PCL. L’autre est l’OpenType CFF®. Les sorties PDF et PostScript prennent en charge les polices Type-1, TrueType et OpenType® incorporées. La sortie PCL prend en charge les polices TrueType incorporées.

Les polices Type-1 et OpenType® ne sont pas incorporées dans la sortie PCL. Le contenu formaté avec les polices Type-1 et OpenType® est pixellisé et généré sous la forme d’une image bitmap pouvant être grande et plus lente à générer.

Les polices téléchargées ou incorporées sont automatiquement remplacées lors de la génération d’une sortie PostScript, PCL ou PDF. Cela signifie que seul le sous-ensemble des glyphes de police requis pour effectuer correctement le rendu du document généré est inclus dans la sortie générée.

### Utilisation des fichiers de profil de l’appareil (fichier XDC) {#working-with-xdc-files}

Un profil de périphérique (fichier XDC) est un fichier de description d’imprimante au format XML. Ce fichier permet aux API Communications de produire des documents sous la forme de formats d’imprimantes laser ou d’imprimantes d’étiquettes. Les API de communication utilisent les fichiers XDC, notamment les suivants :

* hppcl5c.xdc

* hppcl5e.xdc

* ps_plain_level3.xdc

* ps_plain.xdc

* zpl300.xdc

* zpl600.xdc

* zpl300.xdc

* ipl300.xdc

* ipl400.xdc

* tpcl600.xdc

* dpl300.xdc

* dpl406.xdc

* dpl600.xdc

Vous pouvez utiliser les fichiers XDC fournis pour générer des documents d’impression ou les modifier en fonction de vos besoins.
&lt;!-* Il n’est pas nécessaire de modifier ces fichiers pour créer des documents. Vous pouvez toutefois les modifier pour répondre aux besoins de votre entreprise. -->

Ces fichiers sont des fichiers XDC de référence qui prennent en charge les fonctionnalités d’imprimantes spécifiques, telles que les polices propres à l’imprimante, les bacs d’alimentation papier et les agrafeuses. L’objectif de cette référence est de vous aider à comprendre comment configurer vos propres imprimantes à l’aide de profils d’appareil. Les références sont également un point de départ pour des imprimantes similaires dans la même gamme de produits.

### Utilisation du fichier de configuration XCI {#working-with-xci-files}

Les API Communications utilisent un fichier de configuration XCI pour effectuer des tâches, comme contrôler si la sortie est un panneau unique ou si elle est paginée. Bien que ce fichier contienne des paramètres qui peuvent être définis, il n’est pas courant de modifier cette valeur. <!-- The default.xci file is located in the svcdata\XMLFormService folder. -->

Vous pouvez transmettre un fichier XCI modifié en utilisant une API Communications. Pour ce faire, créez une copie du fichier par défaut, modifiez uniquement les valeurs qui doivent être modifiées pour répondre aux besoins de votre entreprise et utilisez le fichier XCI modifié.

Les API Communications commencent par le fichier XCI par défaut (ou le fichier modifié). Ensuite, elles appliquent les valeurs spécifiées à l’aide des API Communications. Ces valeurs remplacent les paramètres XCI.

Le tableau suivant indique les options XCI.

| Option XCI | Description |
| ------------------------------------| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| config/present/pdf/creator | Identifie le créateur du document à l’aide de l’entrée Créateur du dictionnaire d’informations sur le document. Pour plus d’informations sur ce dictionnaire, consultez le guide de référence PDF. |
| config/present/pdf/producer | Identifie le producteur du document à l’aide de l’entrée Producteur du dictionnaire d’informations sur le document. Pour plus d’informations sur ce dictionnaire, consultez le guide de référence PDF. |
| config/present/layout | Contrôle si la sortie est un panneau unique ou si elle est paginée. |
| config/present/pdf/compression/level | Indique le degré de compression à utiliser lors de la génération d’un document PDF. |
| config/present/pdf/scriptModel | Contrôle si des informations spécifiques à XFA sont incluses dans le document PDF de sortie. |
| config/present/common/data/adjustData | Contrôle si l’application XFA ajuste les données après la fusion. |
| config/present/pdf/renderPolicy | Contrôle si la génération du contenu de la page est effectuée sur le serveur ou différée au client. |
| config/present/common/locale | Spécifie le paramètre régional par défaut utilisé dans le document de sortie. |
| config/present/destination | Lorsque contenu par un élément présent, indique le format de sortie. Lorsqu’il est contenu par un élément openAction, spécifie l’action à effectuer lors de l’ouverture du document dans un client interactif. |
| config/present/output/type | Spécifie le type de compression à appliquer à un fichier ou le type de sortie à produire. |
| config/present/common/temp/uri | Spécifie l’URI du formulaire. |
| config/present/common/template/base | Fournit un emplacement de base pour les URI dans le design de formulaire. Lorsque cet élément est absent ou vide, l’emplacement du design de formulaire est utilisé comme base. |
| config/present/common/log/to | Contrôle l’emplacement dans lequel les données du journal ou les données de sortie sont écrites. |
| config/present/output/to | Contrôle l’emplacement dans lequel les données du journal ou les données de sortie sont écrites. |
| config/present/script/currentPage | Indique la page initiale à l’ouverture du document. |
| config/present/script/exclude | Informe le serveur AEM Forms et les API Communications des événements à ignorer. |
| config/present/pdf/linearized | Contrôle si le document PDF de sortie est linéarisé. |
| config/present/script/runScripts | Contrôle l’ensemble de scripts qu’AEM Forms exécute. |
| config/present/pdf/tagged | Contrôle l’inclusion de balises dans le document PDF de sortie. Les balises, dans le contexte d’un PDF, sont des informations supplémentaires incluses dans un document afin d’exposer la structure logique du document. Les balises aident à l’accessibilité et au reformatage. Par exemple, un numéro de page peut être balisé en tant qu’artefact afin qu’un lecteur d’écran ne l’indique pas au milieu du texte. Bien que les balises rendent un document plus utile, elles augmentent également sa taille et le temps de traitement pour le créer. |
| config/present/pdf/version | Spécifie la version du document PDF à générer. |
