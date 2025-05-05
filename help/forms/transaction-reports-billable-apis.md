---
title: API de rapports de transactions facturables
description: Liste de toutes les API comptabilisées comme des transactions
feature: Adaptive Forms, Foundation Components
exl-id: 6dfcac3e-5654-4b4f-9134-0cd8be24332e
role: Admin, Developer, User
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '1438'
ht-degree: 86%

---


# API de rapports de transactions facturables {#transaction-reports-billable-apis}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/forms/transaction-reports/transaction-reports-billable-apis) |
| AEM as a Cloud Service | Cet article |


AEM Forms fournit plusieurs API permettant d’envoyer des formulaires, de traiter et de générer des documents. Certaines API sont comptabilisées comme des transactions et d’autres sont gratuites. Ce document fournit une liste de toutes les API comptabilisées comme des transactions dans un rapport de transaction. Voici quelques scénarios courants dans lesquels une API facturable est utilisée :

* Envoi d’un formulaire adaptatif
* Conversion d’un document d’un format à un autre
* Aplatissement d’un document PDF dynamique
* Génération d’un document d’enregistrement (à l’aide du service Forms ou du service Output)
* Fusion d’un document PDF interactif avec un autre document PDF
* Utilisation de l’étape Affecter une tâche et des étapes de l’API de communication des processus AEM

Les API de facturation ne prennent pas en compte le nombre de pages, la taille d’un document ou d’un formulaire, ni le format final du document rendu. Un rapport de transaction divise les transactions en deux catégories : Forms Envoyé et Documents Rendu.

* **Formulaires envoyés :** les données envoyées à partir de n’importe quel type de formulaire créé avec AEM Forms et les données envoyées à nʼimporte quel référentiel de stockage de données ou base de données sont considérées comme un envoi de formulaire. Par exemple, l’envoi d’un formulaire adaptatif ou d’un jeu de formulaires est considéré comme un envoi de formulaires. Si un jeu de formulaires comporte 5 formulaires et que le jeu de formulaires est envoyé, le service de reporting sur les transactions le comptabilise comme 5 envois.

* **Documents rendus :** la génération d’un document en combinant un modèle et des données, la signature ou la certification numérique d’un document, l’utilisation dʼune API Document Services facturable pour les services de documents ou la conversion d’un document d’un format à un autre sont comptabilisés comme des documents rendus.

>[!CONTEXTUALHELP]
>id="aemforms_cs_transaction_reporting_submission_graph_en"
>title="Outil de suivi des soumissions de formulaires"
>abstract="Ce graphe représente le nombre d’envois de formulaires adaptatifs pendant des périodes spécifiques. L’augmentation des envois peut indiquer que le formulaire est de plus en plus populaire ou qu’il est nécessaire de collecter plus de données auprès des utilisateurs et utilisatrices. **Note :** le graphe fournit des données spécifiques à l’instance actuelle, ce qui vous permet d’analyser rapidement les tendances et de prendre des décisions éclairées. Pour les données d’envoi d’autres instances, accédez simplement au tableau de bord de l’instance correspondante."

>[!CONTEXTUALHELP]
>id="aemforms_cs_transaction_reporting_conversions_graph_en"
>title="Outil de suivi du rendu du document"
>abstract="Ce graphe représente le nombre de rendus de document pendant des périodes spécifiques. **Note :** le graphe fournit des données spécifiques à l’instance actuelle, ce qui vous permet d’analyser rapidement les tendances et de prendre des décisions éclairées. Pour les données d’envoi d’autres instances, accédez simplement au tableau de bord de l’instance correspondante."

>[!CONTEXTUALHELP]
>id="aemforms_cs_transaction_reporting_newForms_graph_en"
>title="Outil de suivi des nouveaux formulaires"
>abstract="Le graphe fournit des informations sur le nombre des formulaires nouvellement créés au cours de périodes spécifiques. **Note :** le graphe fournit des données spécifiques à l’instance de création AEM Forms actuelle. Pour afficher les données d’autres instances, accédez au tableau de bord de chacune d’elles."

>[!CONTEXTUALHELP]
>id="aemforms_cs_transaction_reporting_publishedForms_graph_en"
>title="Outil de suivi des formulaires publiés"
>abstract="Le graphe fournit des informations sur le nombre de formulaires publiés avec succès au cours de périodes spécifiques. **Note :** le graphe fournit des données spécifiques à l’instance de publication AEM Forms actuelle. Pour afficher les données de conversion d’autres instances, accédez au tableau de bord de chaque instance."

>[!CONTEXTUALHELP]
>id="aemforms_cs_transaction_reporting_formCreationAvgDuration_graph_en"
>title="Durée moyenne de la génération d’un formulaire"
>abstract="Le graphique illustre la durée moyenne nécessaire à la création d’un formulaire. Chaque barre du graphe représente un formulaire spécifique. La hauteur de la barre indique la durée moyenne de création d’un formulaire au cours de cette période."

>[!CONTEXTUALHELP]
>id="aemforms_cs_transaction_reporting_formPublishAvgDuration_en"
>title="Durée moyenne de création de formulaire"
>abstract="Le graphique affiche la durée moyenne nécessaire à la création et à la publication d’un formulaire, mesurée à partir du premier jour où le formulaire a été ouvert pour édition. **Note :** le graphe fournit des données spécifiques à l’instance de création AEM Forms actuelle. Pour afficher les données d’autres instances, accédez au tableau de bord de chacune d’elles."


>[!CONTEXTUALHELP]
>id="aemforms_cs_transaction_reporting_formFragments_graph_en"
>title="Outil de suivi des fragments de formulaires"
>abstract="Ce graphe vous permet de voir combien de fragments de formulaire vous utilisez dans vos formulaires. **Note :** le graphe fournit des données spécifiques à l’instance de publication AEM Forms actuelle. Pour afficher les données de conversion d’autres instances, accédez au tableau de bord de chaque instance."

>[!CONTEXTUALHELP]
>id="aemforms_cs_transaction_reporting_avgFormPerFragments_graph_en"
>title="Outil de suivi du temps moyen des fragments de formulaires"
>abstract="Le graphe affiche la durée moyenne nécessaire à la création d’un fragment de formulaire, mesurée à partir du premier jour où le fragment de formulaire a été ouvert pour modification. **Note :** le graphe fournit des données spécifiques à l’instance de publication AEM Forms actuelle. Pour afficher les données de conversion d’autres instances, accédez au tableau de bord de chaque instance."


<!-- 

>[!NOTE]
>
>Transaction Reports UI displays three categories: Forms Submitted, Documents Rendered, and Documents Processed. Both Documents Rendered and Documents Processed are accounted as Documents Rendered.
-->


<!--

## Billable Document Services APIs {#billable-document-services-apis}

### Generate PDF Service {#generate-pdf-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#createPDF-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF</a></td>
   <td>Creates Adobe PDF from supported file types.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#createPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF2</a></td>
   <td>Creates Adobe PDF from supported file types.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF</a></td>
   <td>Converts Adobe PDF to supported file types. </td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF2</a></td>
   <td>Converts Adobe PDF to supported file types. </td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF3</a></td>
   <td>Converts Adobe PDF to supported file types. </td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-3/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlFileToPdf-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-">htmlFileToPdf</a></td>
   <td><p>Creates PDF from HTML pages.</p> </td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlToPdf-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">htmlToPdf</a></td>
   <td>Creates PDF from URLs pointing to an HTML page.</td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlToPdf2-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">htmlToPdf2</a></td>
   <td>Creates PDF from URLs pointing to an HTML page.</td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#optimizePDF-com.adobe.aemfd.docmanager.Document-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">optimizePDF</a></td>
   <td>Optimizes PDF to reduce file size by stripping unnecessary metadata without affecting the quality.</td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
 </tbody>
</table>

-->


<!--
### Distiller Service {#distiller-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/DistillerService.html#createPDF-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF</a><br /> </td>
   <td>Creates Adobe PDF from supported file types.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/DistillerService.html#createPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF2</a></td>
   <td>Creates Adobe PDF from supported file types.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
 </tbody>
</table>
-->

## API de Document Services facturables {#billable-document-services-apis}

### Service Generate PDF {#generate-pdf-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Catégorie de rapport de transaction</td>
   <td>Informations supplémentaires</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/output-sync/#section/Before-you-start" target="_blank">createPDF</a></td>
   <td>Générer un document PDF à partir d’un modèle et fusionner les données dans ce document.</td>
   <td>Documents traités</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/output-sync/#tag/Communications-Services/paths/~1adobe~1forms~1doc~1v1~1generatePrintedOutput/post" target="_blank">exportPDF</a></td>
   <td>Convertit un fichier XDP ou un document de PDF en types de fichiers pris en charge.</td>
   <td>Documents traités</td>
   <td> </td>
  </tr>
  <!--<tr>
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF</a></td>
   <td>Converts Adobe PDF to supported file types. </td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF2</a></td>
   <td>Converts Adobe PDF to supported file types. </td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF3</a></td>
   <td>Converts Adobe PDF to supported file types. </td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-3/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlFileToPdf-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-">htmlFileToPdf</a></td>
   <td><p>Creates PDF from HTML pages.</p> </td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlToPdf-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">htmlToPdf</a></td>
   <td>Creates PDF from URLs pointing to an HTML page.</td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlToPdf2-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">htmlToPdf2</a></td>
   <td>Creates PDF from URLs pointing to an HTML page.</td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#optimizePDF-com.adobe.aemfd.docmanager.Document-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">optimizePDF</a></td>
   <td>Optimizes PDF to reduce file size by stripping unnecessary metadata without affecting the quality.</td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>-->
 </tbody>
</table>

### Service Output {#output-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Catégorie de rapport de transaction</td>
   <td>Informations supplémentaires</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/output-sync/#tag/PDFOutput" target="_blank">generatePDFOutput</a></td>
   <td>Fusionne des données et des modèles pour créer un document PDF.</td>
   <td>Documents traités</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/output-sync/#tag/PDFOutputOptions" target="_blank">generatePDFOutput (PDFOutputOptions)</a></td>
   <td>Fusionne des données et des modèles pour créer un document PDF.</td>
   <td>Documents traités</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/output-batch/#tag/Batch-Configuration/operation/CreateBatchConfig" target="_blank">generatePDFOutputBatch</a></td>
   <td>Fusionne des données et des modèles pour créer un ensemble de documents PDF.</td>
   <td>Documents traités</td>
   <td> <!-- The generatePDFOutputBatch API combines a form template with a record and generates a PDF. When you process a batch of records, the transaction reporting service counts each record as a separate PDF rendition. <br> You can use the <a href="https://helpx.adobe.com/fr/experience-manager/6-5/forms/javadocs/com/adobe/fd/output/api/BatchOptions.html#getGenerateManyFiles--">getGenerateManyFiles</a> flag to combine multiple renditions to single PDF file. Irrespective of the status of flag, the service counts each record as a separate PDF rendition. --> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/output-sync/#tag/PrintedOutput" target="_blank">generatePrintedOutput</a></td>
   <td>Convertit les documents XDP et PDF aux formats PostScript (PS), PCL (Printer Command Language) et ZPL. </td>
   <td>Documents traités</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/output-sync/#tag/PrintedOutputOptions" target="_blank">generatePrintedOutput (PrintedOutputOptions)</a></td>
   <td>Convertit les documents XDP et PDF aux formats PostScript (PS), PCL (Printer Command Language) et ZPL. </td>
   <td>Documents traités</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/output-batch/#tag/Batch-Configuration/operation/CreateBatchConfig" target="_blank">generatePrintedOutputBatch</a></td>
   <td>Convertit un ensemble de documents XDP et PDF en un ensemble de formats de fichiers PostScript (PS), PCL (Printer Command Language) et ZPL. </td>
   <td>Documents traités</td>
   <td> <!-- The generatePDFOutputBatch API combines a form template with a record and generates a PDF. When you process a batch of records, the transaction reporting service counts each record as a separate PDF rendition. <br> You can use the <a href="https://developer.adobe.com/experience-manager/reference-materials/6-5/forms/javadocs/com/adobe/fd/output/api/BatchOptions.html#getGenerateManyFiles--">getGenerateManyFiles</a> flag to combine multiple renditions to single PDF file. Irrespective of the status of flag, the service counts each record as a separate PDF rendition. --> </td>
  </tr>
 </tbody>
</table>

### Service DocAssurance {#DocAssurance-Service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Catégorie de rapport de transaction</td>
   <td>Informations supplémentaires</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/docassurance/#tag/DocAssurance" target="_blank">secureDocument</a><br /> </td>
   <td>Cette API vous permet de protéger votre document. Vous pouvez utiliser l’API pour signer, certifier, étendre Reader ou chiffrer un document PDF.</td>
   <td>Documents traités</td>
   <td>Seule l’opération de signature et de certification du secureDocument est facturée.</td>
  </tr>
 </tbody>
</table>

### Service de document d’enregistrement (DOR) {#document-of-record-dor-forms-service-and-output-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Catégorie de rapport de transaction</td>
   <td>Informations supplémentaires</td>
  </tr>
  <tr>
   <td><a href="https://opensource.adobe.com/aem-forms-af-runtime/api/#tag/Generate-DoR/operation/generateDoR" target="_blank">render</a></td>
   <td>Appelle la méthode de rendu spécifiée pour générer un document d’enregistrement à l’aide des paramètres fournis.</td>
   <td>Documents traités à l’aide du service Forms</td>
   <td> </td>
  </tr>
  <!--<tr>
   <td><a href="" target="_blank">render</a></td>
   <td>Invokes the specified render method to generate a document of record using provided parameters.</td>
   <td>Documents Processed using Output Service</td>
   <td> </td>
  </tr>-->
 </tbody>
</table>

<!--

### Forms Service {#forms-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-5/forms/javadocs/com/adobe/fd/forms/api/FormsService.html#renderPDFForm-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.fd.forms.api.PDFFormRenderOptions-" target="_blank">renderPDFForm</a></td>
   <td>Renders PDF Form from XDP templates. The XP templates are created in Forms Designer.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-5/forms/javadocs/com/adobe/fd/forms/api/FormsService.html#exportData-com.adobe.aemfd.docmanager.Document-com.adobe.fd.forms.api.DataFormat-" target="_blank">exportData</a></td>
   <td>Extracts data from a PDF Form or XDP templates</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
 </tbody>
</table>
-->

<!--
### Convert PDF Service {#convert-pdf-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-5/forms/javadocs/com/adobe/fd/cpdf/api/ConvertPdfService.html#toImage-com.adobe.aemfd.docmanager.Document-com.adobe.fd.cpdf.api.ToImageOptionsSpec-" target="_blank">toImage</a></td>
   <td>Converts a PDF document to a list of image documents. Supported image formats are JPEG, JPEG2K, PNG, and TIFF.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-5/forms/javadocs/com/adobe/fd/cpdf/api/ConvertPdfService.html#toImage-com.adobe.aemfd.docmanager.Document-com.adobe.fd.cpdf.api.ToImageOptionsSpec-" target="_blank">toPS</a></td>
   <td>Converts a Flat PDF file to PostScript format using the options specified in the option spec.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
 </tbody>
</table>
-->

<!--
### Barcoded Forms Service {#barcoded-forms-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-5/forms/javadocs/com/adobe/fd/bcf/api/BarcodedFormsService.html#decode-com.adobe.aemfd.docmanager.Document-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-com.adobe.fd.bcf.api.CharSet-" target="_blank">decode</a></td>
   <td>Decodes all the barcodes in a Document object and returns an org.w3c.dom.Document object that contains data that was retrieved from the barcode.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
 </tbody>
</table>
-->

### Incohérence affectant le service assembleur {#assembler-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Catégorie de rapport de transaction</td>
   <td>Informations supplémentaires</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/assembler-sync/#tag/DDX-execution/operation/InvokeDDX">invoke</a></td>
   <td>Exécute le DDX sur les documents d’entrée donnés et renvoie un objet contenant les documents de résultat.</td>
   <td>Documents traités</td>
   <td>Les opérations suivantes ne sont pas comptabilisées comme des transactions :
    <ul>
     <li>Créer des packages ou des portfolios</li>
     <li>Assembler plusieurs fichiers XDP </li>
    </ul> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/assembler-sync/#tag/DDX-execution/operation/InvokeDDX" target="_blank">invoke</a></td>
   <td>Exécute le DDX sur les documents d’entrée donnés et renvoie un objet contenant les documents de résultat.</td>
   <td>Documents traités</td>
   <td>Tous les formats de fichiers d’entrée pris en charge par PDF Generator, Forms et Output, le service Assembler prend en charge tous ces formats en tant que formats de fichiers de sortie. </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/assembler-sync/#tag/Document-conversion/operation/ConvertToPDFA">toPDFA</a></td>
   <td>Convertissez un document spécifié en format PDF/A à l’aide d’options indiquées.</td>
   <td>Documents traités</td>
   <td> </td>
  </tr>
 </tbody>
</table>

L’utilisation de l’API d’appel est comptabilisée comme une transaction lorsque vous effectuez une ou plusieurs des opérations suivantes :

1. Conversion de formats non PDF en formats PDF. <!--For instance, the conversion from XDP format to PDF format, catering to both interactive and non-interactive forms of communication, and the conversion from Word to PDF.-->
1. Conversion du format PDF au format PDF/A.
1. Conversion du format PDF aux formats non PDF. Les exemples incluent la transformation du format PDF au format Image ou la conversion du format PDF au format Texte.


>[!NOTE]
>
>* L’API Invoke du service Assembler peut appeler en interne une API facturable d’un autre service selon l’entrée. Ainsi, l’API Invoke peut être comptabilisée comme aucune, une ou plusieurs transactions. Le nombre de transactions comptabilisées dépend de l’entrée et des API internes appelées.
>* Un seul document PDF produit à l’aide du service Assembler peut être comptabilisé comme aucune, une ou plusieurs transactions. Le nombre de transactions comptabilisées dépend du code fourni.
>

<!--
### PDF Utility Service  {#pdf-utility-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-5/forms/javadocs/com/adobe/fd/pdfutility/services/PDFUtilityService.html#convertPDFtoXDP-com.adobe.aemfd.docmanager.Document-" target="_blank">convertPDFtoXDP</a></td>
   <td>Converts a PDF document into an XDP file. In order for a PDF document to be successfully converted to an XDP file, the PDF document must contain an XFA stream in the AcroForm dictionary.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
 </tbody>
</table>
-->

## API de capture de données facturables {#billable-data-capture-apis}

Tous les événements d’envoi des formulaires adaptatifs sont comptabilisés comme des transactions. Par défaut, l’envoi d’un formulaire PDF n’est pas comptabilisé comme une transaction. Utilisez les [API d’enregistrement de transaction](record-transaction-custom-implementation.md) pour enregistrer un envoi de formulaires PDF en tant que transaction.

### Formulaires adaptatifs {#adaptive-forms}

<table>
 <tbody>
  <tr>
   <td><p>Cas d’utilisation</p> </td>
   <td>Description</td>
   <td>Catégorie de rapport de transaction</td>
   <td>Informations supplémentaires</td>
  </tr>
  <tr>
   <td>Envoi d’un formulaire adaptatif</td>
   <td>Envoie un formulaire adaptatif à une action d’envoi configurée. </td>
   <td>Formulaires envoyés</td>
   <td>
    <ul>
     <li>Les envois réussis comptabilisent une ou deux transactions. Le nombre de transactions comptabilisées dépend du type d’action d’envoi utilisée pour l’envoi. Par exemple, l’envoi d’un PDF par le biais d’une action d’envoi par e-mail comptabilise deux transactions. Une transaction pour l’envoi de formulaire et une autre pour le PDF généré à l’aide du service Document of Record (DOR). </li>
     <li>L’utilisation du formulaire adaptatif dans un formulaire adaptatif (jeu de formulaires adaptatifs) comptabilise une seule transaction. Vous pouvez avoir un nombre illimité de formulaires adaptatifs dans un formulaire adaptatif.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

<!--

### HTML5 Forms {#html-forms}

<table>
 <tbody>
  <tr>
   <td><p>Use Case</p> </td>
   <td>Description </td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td>Submitting an HTML5 Form</td>
   <td>Submits an HTML5 Form to submit URL configured in the form.</td>
   <td>Forms Submitted</td>
   <td> </td>
  </tr>
 </tbody>
</table>

### Form set {#form-set}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td>Submitting a form set</td>
   <td>Submits form set to the submit URL configured in the form set.</td>
   <td>Forms Submitted</td>
   <td>
    <ul>
     <li>Using the adaptive form within an adaptive form (Adaptive form formset) accounts only single transaction. You can have any number of adaptive forms within an adaptive form.</li>
     <li>Every form in an HTML5 Forms form set accounts as a separate transaction. </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

-->

## Processus d’AEM facturation {#billable--form-centric-aem-workflows}

Les étapes Affecter des tâches et des services de document des processus d’AEM basés sur l’utilisation de Forms sont comptabilisées comme des transactions. Si une étape de workflow comptabilise une transaction et que le workflow ne se termine pas, le nombre de transactions n’est pas inversé.

<!--
Assign task and document services steps of Form-centric AEM Workflows on OSGi and all the renditions of interactive communication and are accounted as transactions. Previewing an interactive communication on the author instance and previewing on the publish instance using Agent UI are not accounted as transactions. If a workflow step accounts a transaction and the workflow fails to complete, the transaction count is not reversed.
-->


<!--

### Interactive Communication - Web Channel {#interactive-communication-web-channel}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td>Rendering a web channel</td>
   <td>Opens the web version of an interactive communication.</td>
   <td>Documents Rendered</td>
   <td>
    <div>
    </div> </td>
  </tr>
 </tbody>
</table>

### Interactive Communication - Print Channel {#interactive-communication-print-channel}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/fr/experience-manager/6-5/forms/javadocs/com/adobe/fd/ccm/channels/print/api/model/PrintChannel.html" target="_blank">render</a> (convert to PDF)</td>
   <td>Generates the PDF version of an interactive communication.</td>
   <td>Documents Rendered</td>
   <td>
    <div>
    </div> </td>
  </tr>
 </tbody>
</table>

-->

### Processus d’AEM centrés sur les formulaires {#form-centric-aem-workflows}

<table>
 <tbody>
  <tr>
   <td><p>Cas d’utilisation</p> </td>
   <td>Catégorie de rapport de transaction</td>
   <td>Informations supplémentaires</td>
  </tr>
  <tr>
   <td>Envoyer une opération Affecter une tâche</td>
   <td>Formulaires envoyés</td>
   <td>
    <div>
    </div> </td>
  </tr>
  <tr>
   <td>Envoyer un point de départ d’application de workflow </td>
   <td>Formulaires envoyés</td>
   <td> </td>
  </tr>
 </tbody>
</table>

## Enregistrer les API de facturation en tant que transactions pour le code personnalisé {#recording-billable-apis-as-transactions-for-custom-code}

Les actions telles que l’envoi d’un formulaire PDF, l’utilisation de l’interface utilisateur de l’agent pour prévisualiser une communication interactive, l’utilisation d’un formulaire non standard et les implémentations personnalisées ne sont pas comptabilisées comme des transactions. AEM Forms fournit une API pour enregistrer ces actions en tant que transactions. Vous pouvez appeler l’API à partir de vos implémentations personnalisées pour [enregistrer une transaction](/help/forms/record-transaction-custom-implementation.md).

## Articles connexes {#related-articles}

* [Enregistrer une transaction pour les implémentations personnalisées](/help/forms/record-transaction-custom-implementation.md)
