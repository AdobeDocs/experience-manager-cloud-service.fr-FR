---
title: Présentation des Edge Delivery Services AEM Forms
description: Les Edge Delivery Services AEM Forms conçus pour des performances optimales vous permettent d’envisager l’avenir de la collecte de données rationalisée et de l’engagement des utilisateurs.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
source-git-commit: 2b64cc8d2afb7d6064d1f60ba023448171862236
workflow-type: tm+mt
source-wordcount: '662'
ht-degree: 17%

---

# Edge Delivery Services AEM Forms

Rationalisez la création de formulaires et augmentez les taux d’achèvement avec les Edge Delivery Services AEM Forms d’Adobe. Ce service puissant et composable vous permet de créer des formulaires d’entreprise avec des performances exceptionnelles et un attrait visuel exceptionnel. AEM donne la priorité à l’expérience utilisateur et à vos objectifs professionnels, ce qui permet d’accélérer le chargement et d’augmenter les conversions de formulaires.

Vous pouvez utiliser le service pour effectuer les opérations suivantes :

* **Créer des expériences d’inscription exceptionnelles**: créez des expériences d’inscription qui se chargent et s’affichent rapidement, même sur des connexions Internet lentes. Des temps de chargement plus rapides et une expérience utilisateur optimisée contribuent à des taux d’achèvement de formulaire plus élevés et à de meilleurs taux de conversion.

* **Créer des expériences d’inscription avec les outils de votre choix**: augmentez l’efficacité de la création en découplant les sources de contenu. Vous pouvez utiliser les deux **création basée sur des documents** (Microsoft SharePoint ou Google Drive) et **Création AEM** (Éditeur de Forms adaptatif). Ainsi, vous pouvez utiliser plusieurs sources de contenu sur le même formulaire et utiliser vos outils de création préférés, tels que Microsoft Excel, Google Sheets ou Adaptive Forms Editor.

* **Utilisez l’ensemble d’outils destiné aux développeurs :** AEM Forms utilise du HTML brut, du code CSS moderne et du code JavaScript vanille pour créer des expériences exceptionnelles sans la surcharge habituelle. Tout développeur possédant des connaissances de base en HTML, CSS et JS doit être en mesure de créer ses propres composants et n’avoir besoin d’apprendre aucune langue ou structure spécifique. Aucun pipeline ni aucune attente n’est nécessaire, archivez votre code dans Github et vos modifications sont en ligne. De plus, il n’est pas nécessaire d’avoir un pipeline ou d’attendre, d’archiver votre code dans Github et vos modifications sont en ligne.


## Présentation des Edge Delivery Services AEM Forms {#edge-overview}

Le diagramme suivant illustre comment modifier du contenu dans Microsoft Excel ou Google Sheets (modification basée sur des documents) et le publier dans des Edge Delivery Services. Il affiche également la méthode de publication AEM à l’aide de l’éditeur de Forms adaptatif.

![Architecture d’Edge Delivery.](/help/edge/assets/AEM-forms-with-EDS-publishing.png)

Edge Delivery Services est un ensemble de services composables qui offre une grande flexibilité quant à la manière dont vous créez du contenu sur votre site web. Comme mentionné précédemment, vous pouvez utiliser les deux [Gestion de contenu AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/authoring/getting-started/concepts.html?lang=fr) avec [Création AEM](/help/implementing/universal-editor/introduction.md) ainsi que [création basée sur des documents](https://www.aem.live/docs/authoring)

Par exemple, vous pouvez utiliser du contenu directement à partir de Microsoft Excel ou de feuilles de calcul Google. Cela signifie que le contenu provenant de ces sources peut devenir des formulaires sur votre site web. Le nouveau contenu est ajouté instantanément sans nouveau processus de création.

Edge Delivery Services utilise GitHub afin que les clientes et les clients puissent gérer et déployer du code directement à partir de leur référentiel GitHub. Par exemple, vous pouvez écrire des formulaires dans Google Sheets ou Microsoft Excel et les composants de vos formulaires peuvent être développés à l’aide de CSS et de JavaScript dans GitHub. Lorsque tout est prêt, vous pouvez utiliser l’extension de navigateur Sidekick pour prévisualiser et publier les mises à jour de contenu.

AEM Forms Edge Delivery Services fournit un bloc de formulaires, appelé [Bloc Forms adaptatif](/help/edge/docs/forms/create-forms.md) pour ajouter un formulaire à votre site d’Edge Delivery Services.

### Principales fonctionnalités des Edge Delivery Services AEM Forms

La création basée sur les documents d’un ensemble de fonctions de base et la création AEM déverrouillent des fonctionnalités supplémentaires au-delà de la création basée sur les documents, ce qui vous permet de créer des formulaires interactifs et plus complexes. Le tableau suivant met en évidence les principales fonctionnalités de ces deux solutions :

<!-- 

>[!BEGINTABS]

>[!TAB Document-based authoring]

Document-based authoring is a versatile option suitable for creating simple forms with essential functionalities. It allows you to integrate various input types like text fields, dropdown menus, and radio buttons, enabling you to collect user data effectively. It offers a basic version of rules to add dynamic behaviour to forms. Key features of Document-based authoring are: 

* **[HTML5-based Form Field components](/help/edge/docs/forms/form-components.md)**: AEM Forms Edge Delivery Services allow you to create user-friendly and interactive forms using form components based on HTML5 [input types](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types), <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea">textarea</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select">select</a>, and <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">fieldset</a>  elements. These components cater to different types of data collection and can be easily customized to fit your specific needs.  

* **Accessibility**: The fields in the form block are accessible. Each label is linked with its respective input element, and IDs are auto-generated for linking. Descriptions associated with fields are linked via the aria-describedby attribute. Keyboard navigation using the standard Tab/Shift + Tab keys is supported.

* **[Styling](/help/edge/docs/forms/style-theme-forms.md)**: Each form field has a fixed HTML structure that can be easily decorated using custom CSS or JavaScript files. Selectors for targeting fields in CSS and JS are provided based on type and name. You can easily create new selectors due to the standradized structure and style your form. 

* **Basic Rules**: Easily create logic that adjusts field visibility, validation, and behavior based on user input or predefined conditions. Rules offer a flexible and intuitive way to add intelligence to your forms, ensuring they adapt seamlessly based on user inputs.

* **Validations**: Before submission, the form is validated, and invalid fields are appropriately marked with error messages displayed to the user. Adaptive Forms block support all the HTML form validation, supported by modern browsers, and provide additional validation mechanism like validation script, file size, file type, overall file size, and more. 

* **File Uploads**: You can add file attachment capabilities to your forms. Whether you need to gather documents, images, or other files from your users, file upload functionality serves you effortlessly. With custom handling options available, you can tailor the file upload process to suit your specific requirements.

* **reCAPTCHA**: Benefit from seamless integration of Google reCAPTCHA into your forms with our out-of-the-box (OOTB) support. Safeguard your forms against fraudulent activities, spam, and abuse, while maintaining a smooth and uninterrupted user experience. Adaptive Forms block supports reCaptcha V3 and reCaptcha Enterprise. 

* **Send email notification on form submission**: Eliminate the hassle of manual follow-ups and ensure timely communication with our built-in email automation for form submissions. This integrated solution lets you effortlessly notify relevant parties, including sending form data, whenever someone fills out a form on your website. No need for complex configurations or additional tools – it's ready to use out of the box.

>[!TAB AEM Authoring]

AEM Authoring unlocks additional capabilities beyond the document-based authoring, empowering you to build more complex and interactive forms. In additon to the features of Document-based authoring, AEM authoring offers the following additional features:  

* Advanced Rules: Define logic-based actions within your forms. You can use rules to conditionally show or hide form sections, pre-populate fields based on user input, and perform various validations to ensure data integrity.

* Server-side extensibility: Extend the functionalities of your forms by integrating them with server-side logic. This allows you to perform complex calculations, interact with external systems, and automate specific tasks based on user actions within the form.
* Streamline workflows and data management: Leverage the power of AEM to:
    * Design user-friendly forms using AEM editors.
    * Generate a "Document of Record" for secure and tamper-proof archiving of submitted data.
    * Facilitate e-signing with Adobe Sign for a smooth and secure signing experience.
    * Automate business processes through AEM workflows, triggering actions based on form submissions.
    * Effortlessly integrate with various data sources, enabling seamless data flow and exchange.

>[!ENDTABS]



## Start creating forms

-->

|                                           | Création basée sur des documents | Création d’AEM (éditeur de Forms adaptatif) |
| ----------------------------------------- | ------------------------ | ------------------------------------ |
| **Fonctionnalité de formulaire** |                          |                                      |
| Composants accessibles | ✓ | ✓ |
| Structure de HTML normalisée | ✓ | ✓ |
| Règles et validations | ✓ | ✓ |
| Pièces jointes (téléchargement de fichier) | ✓ | ✓ |
| reCAPTCHA de Google | ✓ | ✓ |
| Composants personnalisés | ✓ | ✓ |
| Envoyer par courrier électronique | ✓ | ✓ |
| **Fonctionnalités avancées** |                          |                                      |
| Règles avancées avec éditeur de règles visuel |                          | ✓ |
| Extensibilité côté serveur |                          | ✓ |
| Actions d’envoi multiples |                          | ✓ |
| **Conception et gestion de formulaires** |                          |                                      |
| Éditeur Forms adaptatif pour la modification WYSIWYG |                          | ✓ |
| **Intégrations** |                          |                                      |
| Document d’enregistrement |                          | ✓ |
| Intégration à Adobe Sign |                          | ✓ |
| Intégration avec Adobe Analytics |                          | ✓ |
| Intégration à Marketo |                          | ✓ |
| Intégration à plusieurs sources de données |                          | ✓ |
| Actions d’envoi multiples |                          | ✓ |


## Commencer à créer des formulaires

* [Prise en main - tutoriel pour les développeurs](/help/edge/docs/forms/tutorial.md)
* [Création d’un formulaire à l’aide de feuilles de calcul Google ou de Microsoft Excel](/help/edge/docs/forms/create-forms.md)
* [Envoyer des formulaires directement à vos feuilles Microsoft Excel ou Google](/help/edge/docs/forms/submit-forms.md)
* [Amélioration de l’aspect de vos formulaires : guide de mise en forme](/help/edge/docs/forms/style-theme-forms.md)


<!-- 

## Start creating forms

<div>

  <style>
    .card-container {
        width: calc(33.33% - 10px);;
        margin: 5px;
        border: 1px solid #ccc;
        border-radius: 5px;
        padding: 5px;
        box-sizing: border-box;
        transition: background-color 0.3s ease; /* Adding transition effect */
    }
    .card-container:hover {
        background-color: #f0f0f0; /* Changing background color on hover */
    }
</style>

<div style="display: flex; flex-wrap: wrap; justify-content: space-between; margin: -5px;">
    <div class="card-container">
        <a href="/help/edge/docs/forms/create-forms.md">
            <img src="/help/edge/assets/smock_devices_18_n.svg" alt="Create a form using eds forms" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Create a form using Google Sheets or Microsoft Excel</b>
        </a>
        <p>Create forms that load and render quickly and automatically reflows on mobile devices.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/create-forms.md#manually-configure-a-spreadsheet-to-accept-data">   
            <img src="/help/edge/assets/smock_platformdatamapping_18_n.svg" alt="Submit form" alt="Use Form Fragments in an EDS Form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Submit form to spreadsheet</b>
        </a>
        <p>Submit forms directly to your Microsoft Excel or Google Sheets.</p>
    </div>
     <div class="card-container">
        <a href="/help/edge/docs/forms/style-theme-forms.md">
            <img src="/help/edge/assets/smock_imageautomode_18_N.svg" alt="Apply styles or themes to an eds form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Customize a theme</b>
        </a>
        <p>Create a consistent brand image by applying the same theme across forms.</p>
    </div>
      <div class="card-container">
        <a href="/help/edge/docs/forms/validate-forms.md">
            <img src="/help/edge/assets/smock_condition_18_n.svg" alt="Add validations to form fields" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Apply field validations</b>
        </a>
        <p>Reduce errors and frustration by checking form inputs for proper formatting.</p>
    </div> 
            <div class="card-container">
        <a href="/help/edge/docs/forms/rules-forms.md">
            <img src="/help/edge/assets/smock_documentfragment_18_n.svg" alt="Use rules to add dynamic behaviour to a form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Use rules to add dynamic behaviour to a form</b>
        </a>
        <p>Reuse preconfigured fragments across multiple forms.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/translate-forms.md">  
            <img src="/help/edge/assets/smock_abc_18_n.svg" alt="Translate an EDS Form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Translate a form</b>
        </a>
        <p>Extend the reach of your forms while keeping costs in check.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/repeatable-forms.md">  
            <img src="/help/edge/assets/smock_addto_18_n.svg" alt="Add repeatable sections to an EDS Form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Add repeatable sections</b>
        </a>
        <p>Effortlessly create and add repeatable sections to a form.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/custom-components-forms.md"> 
            <img src="/help/edge/assets/smock_userdeveloper_18_n.svg" alt="Create custom forms components using standard JavaScript and CSS"  style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Create custom components</b>
        </a>
        <p>Use standard JavaScript and CSS to create components and themes.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/recaptacha-forms.md">  
            <img src="/help//edge/assets/smock_keyclock_18_n.svg" alt="Use reCAPTCHA in an EDS Form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Use reCAPTCHA</b>
        </a>
        <p>Use OOTB reCAPTCHA integration for robust spam and bot protection.</p>
    </div>


</div>


</br>


-->