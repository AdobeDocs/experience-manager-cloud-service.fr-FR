---
title: Présentation du service de diffusion Edge AEM Forms
description: Le service de diffusion Edge d’AEM Forms, conçu pour offrir des performances optimales, vous permet d’envisager l’avenir d’une collecte de données rationalisée et de l’engagement des utilisateurs.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 6fbeb94d3547d50e93ab80aee5d6458e51edb1da
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 1%

---


# Service de diffusion Edge AEM Forms

AEM Forms Edge Delivery Service est un service composable proposé par Adobe qui vous permet de créer et de diffuser des formulaires web à fort impact et performants.

![Fonctionnalités clés d’EDS Forms](/help/edge/assets/eds-forms-key-features.png)

Vous pouvez utiliser le service pour effectuer les opérations suivantes :

* **Utilisateurs Captivate avec des formulaires époustouflants**: créez facilement des formulaires complexes et attrayants à l’aide d’une bibliothèque de composants prédéfinis. Intégrez facilement reCAPTCHA, envoyez des formulaires directement par e-mail et autorisez des téléchargements de fichiers transparents pour des solutions de stockage sécurisées telles que Sharepoint, Azure Storage et Amazon S3. Créez même vos propres composants de formulaires personnalisés pour donner vie à votre vision unique.

* **Créer des expériences d’inscription numérique avec les outils de votre choix**: augmentez l’efficacité de la création en découplant les sources de contenu. Vous pouvez utiliser la création basée sur des documents (Microsoft 365 et Google Workspace) et AEM la création (AEM Editors). Ainsi, vous pouvez utiliser plusieurs sources de contenu sur le même site web et utiliser vos outils de création préférés, tels que Microsoft Excel, Google Sheets ou Adaptive Forms Editor.

* **Créer des formulaires avec un score Lighthouse parfait**: créez des formulaires qui se chargent et s’affichent rapidement, même avec des connexions Internet lentes. Des temps de chargement plus rapides et une expérience utilisateur optimisée contribuent à des taux d’achèvement de formulaire plus élevés et à de meilleurs taux de conversion.


<!-- >
* **Captivate users with stunning forms**: 
Build complex and engaging forms with ease using a library of pre-built components. Easily integrate reCAPTCHA, submit forms directly to email, and allow seamless file uploads to secure storage solutions like Sharepoint, Azure Storage, and Amazon S3. Even create your own custom forms components to bring your unique vision to life. 

    ![Enrollment forms](/help/edge/assets/enrollment-form.png)

* **Build forms with perfect lighthouse score**: Build forms that load and render quickly, even on slow internet connections. Faster loading times and optimized user experience contribute to higher form completion rates and improved conversion rates.

    ![perfect lighthouse score for your forms](/help/edge/assets/lighthouse-forms.png)

* **Create digital enrollment experiences with tools of your choice**: Increase authoring efficiency by decoupling content sources. Out of the box you can use both AEM authoring and document-based authoring. As such, you can work with multiple content sources on the same website and use your preferred authoring tools, such as Microsoft Excel, Google Sheets, or AEM Editors.

    ![Edge Delivery forms authoring tools](/help/edge/assets/edge-delivery-forms-authoring-tools.png)
    
<!--
* **Measure customer impact and deliver effective forms**: Use our RUM dashboards to visualize form performance and identify areas for improvement. Experiment with different versions and continuously optimize your forms for maximum effectiveness, ensuring you capture the data you need and drive better business outcomes.

* **Use Integrated services:** Use integrated services to streamline and empowers your users with a one-stop shop for managing their digital enrollment journeys. Use e-signatures, automated workflows, document of record (DoR), and seamless data integration, simplify the entire digital enrollment process, accelerate approvals, and optimizes your business workflows. 

    
>[!NOTE]
    >
    >
    > WYSIWYG authoring capability, integrated services, and customer impact measuring features are available under early adopter program. You can write to aem-forms-early-adopter-program@adobe.com from your official email id to join the early adopter program and request access to the capability.

    -->

## Commencer à créer des formulaires

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
            <img src="/help/edge/assets/smock_devices_18_n.svg" alt="Création d’un formulaire à l’aide de formulaires AEM" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Création d’un formulaire à l’aide de feuilles de calcul Google ou de Microsoft Excel</b>
        </a>
        <p>Créez des formulaires qui se chargent et s’affichent rapidement et automatiquement sur les périphériques mobiles.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/create-forms.md#manually-configure-a-spreadsheet-to-accept-data">   
            <img src="/help/edge/assets/smock_platformdatamapping_18_n.svg" alt="Envoyer le formulaire" alt="Utilisation de fragments de formulaire dans un formulaire EDS" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Envoyer le formulaire à la feuille de calcul</b>
        </a>
        <p>Envoyez des formulaires directement à vos feuilles Microsoft Excel ou Google.</p>
    </div>
     <div class="card-container">
        <a href="/help/edge/docs/forms/style-theme-forms.md">
            <img src="/help/edge/assets/smock_imageautomode_18_N.svg" alt="Application de styles ou de thèmes à un formulaire de texte" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Personnalisation d’un thème</b>
        </a>
        <p>Créez une image de marque cohérente en appliquant le même thème à tous les formulaires.</p>
    </div>
      <div class="card-container">
        <a href="/help/edge/docs/forms/validate-forms.md">
            <img src="/help/edge/assets/smock_condition_18_n.svg" alt="Ajouter des validations à des champs de formulaire" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Appliquer les validations de champ</b>
        </a>
        <p>Réduisez les erreurs et les frustrations en vérifiant les entrées du formulaire pour une mise en forme correcte.</p>
    </div> 
            <div class="card-container">
        <a href="/help/edge/docs/forms/rules-forms.md">
            <img src="/help/edge/assets/smock_documentfragment_18_n.svg" alt="Utilisation de règles pour ajouter un comportement dynamique à un formulaire" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Utilisation de règles pour ajouter un comportement dynamique à un formulaire</b>
        </a>
        <p>Réutilisation de fragments préconfigurés dans plusieurs formulaires.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/translate-forms.md">  
            <img src="/help/edge/assets/smock_abc_18_n.svg" alt="Traduire un formulaire EDS" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Traduire un formulaire</b>
        </a>
        <p>Étendez la portée de vos formulaires tout en surveillant les coûts.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/repeatable-forms.md">  
            <img src="/help/edge/assets/smock_addto_18_n.svg" alt="Ajout de sections répétables à un formulaire EDS" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Ajout de sections répétables</b>
        </a>
        <p>Créez et ajoutez facilement des sections répétables à un formulaire.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/custom-components-forms.md"> 
            <img src="/help/edge/assets/smock_userdeveloper_18_n.svg" alt="Création de composants de formulaires personnalisés à l’aide du code JavaScript et CSS standard"  style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Création de composants personnalisés</b>
        </a>
        <p>Utilisez JavaScript et CSS standard pour créer des composants et des thèmes.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/recaptacha-forms.md">  
            <img src="/help//edge/assets/smock_keyclock_18_n.svg" alt="Utiliser reCAPTCHA dans un formulaire EDS" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Utiliser reCAPTCHA</b>
        </a>
        <p>Utilisez l’intégration reCAPTCHA prête à l’emploi pour une protection robuste contre les spams et les robots.</p>
    </div>


</div>


</br>









