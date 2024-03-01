---
title: Présentation du service de diffusion AEM Forms Edge
description: AEM Forms service de livraison Edge conçu pour des performances optimales, vous permettant d’envisager l’avenir de la collecte de données rationalisée et de l’engagement des utilisateurs.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 1c6e44fd6652d93ba73bc2eb3604cd08eae7a33c
workflow-type: tm+mt
source-wordcount: '610'
ht-degree: 3%

---


# Service de remise AEM Forms Edge

Rationalisez la création de formulaires et augmentez les taux d’exécution grâce au service de livraison AEM Forms Edge d’Adobe. Ce service puissant et composable vous permet de créer des formulaires de niveau entreprise avec des performances et un attrait visuel exceptionnels. AEM donne la priorité à la fois à l’expérience utilisateur et à vos objectifs commerciaux, garantissant des temps de chargement ultra-rapides et une augmentation du nombre de formulaires complétés.

Vous pouvez utiliser le service pour effectuer les opérations suivantes :

* **Captivez les utilisateurs avec des formulaires époustouflants : Créez facilement des formulaires** complexes et attrayants à l’aide d’une bibliothèque de composants prédéfinis. Intégrez facilement reCAPTCHA, soumettez des formulaires directement par e-mail et autorisez des téléchargements de fichiers transparents vers des solutions de stockage sécurisées telles que Sharepoint, Azure Storage et Amazon S3. Créez même vos propres composants de formulaire personnalisés pour donner vie à votre vision unique.

* **Créez des expériences d’inscription numérique avec les outils de votre choix** : Augmentez l’efficacité de la création en découplant les sources de contenu. Prêt à l’emploi, vous pouvez utiliser à la fois la création basée sur des documents (Microsoft 365 et Google Workspace) et la création AEM (éditeurs AEM). En tant que tel, vous pouvez travailler avec plusieurs sources de contenu sur le même site Web et utiliser vos outils de création préférés, tels que Microsoft Excel, Google Sheets ou Adaptive Forms Editor.

* **Créez des formulaires avec un score** Lighthouse parfait : créez des formulaires qui se chargent et s’affichent rapidement, même sur des connexions Internet lentes. Des temps de chargement plus rapides et une expérience utilisateur optimisée contribuent à des taux de remplissage des formulaires plus élevés et à de meilleurs taux de conversion.

  <div>
    <style>
    .image-container {
    width: 80%;
    text-align: center; 
    }
    .image-container img {
        width: 70%; /* Set image width to 70% of the container */
        border: .5px solid; /* Maintain the border style */
        padding: 15px; /* Maintain the padding */
    }
</style>
    <div class="image-container">
    <img src="/help/edge/assets/eds-forms-key-features.png" alt="EDS Forms Principales fonctionnalités">
    </div>


</div>
&lt;!-- &gt;
* **Captivez les utilisateurs avec des formulaires époustouflants** : 
Créez facilement des formulaires complexes et attrayants à l’aide d’une bibliothèque de composants prédéfinis. Intégrez facilement reCAPTCHA, soumettez des formulaires directement par e-mail et autorisez des téléchargements de fichiers transparents vers des solutions de stockage sécurisées telles que Sharepoint, Azure Storage et Amazon S3. Créez même vos propres composants de formulaire personnalisés pour donner vie à votre vision unique.

    .[Formulaires d’inscription] (/help/edge/assets/enrollment-form.png)

* **Créez des formulaires avec un score** phare parfait : créez des formulaires qui se chargent et s’affichent rapidement, même sur des connexions Internet lentes. Des temps de chargement plus rapides et une expérience utilisateur optimisée contribuent à des taux de remplissage des formulaires plus élevés et à de meilleurs taux de conversion.

  ![Note Lighthouse parfaite pour vos formulaires](/help/edge/assets/lighthouse-forms.png)

* **Créez des expériences d’inscription numérique avec les outils de votre choix** : Augmentez l’efficacité de la création en découplant les sources de contenu. Vous pouvez utiliser nativement les instances de création AEM et la création basée sur des documents. En tant que tel, vous pouvez travailler avec plusieurs sources de contenu sur le même site Web et utiliser vos outils de création préférés, tels que Microsoft Excel, Google Sheets ou AEM Editors.

  ![Outils de création de formulaires de remise Edge](/help/edge/assets/edge-delivery-forms-authoring-tools.png)

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
            <img src="/help/edge/assets/smock_devices_18_n.svg" alt="Création d’un formulaire à l’aide de formulaires eds" style="border-radius: 5px;"></b><br><b style="margin-top: 5px;">Créer un formulaire à l’aide de Google Sheets ou de Microsoft Excel
            </b>
        </a>
        <p>Créez des formulaires qui se chargent et restituent rapidement et redistribue automatiquement sur les appareils mobiles.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/create-forms.md#manually-configure-a-spreadsheet-to-accept-data">   
            <img src="/help/edge/assets/smock_platformdatamapping_18_n.svg" alt="Envoyer le formulaire" alt="Utilisation des fragments de formulaires dans un formulaire EDS" style="border-radius: 5px;"></b><br><b style="margin-top: 5px;">Envoyer le formulaire dans la feuille de calcul
            </b>
        </a>
        <p>Envoyez des formulaires directement à Microsoft Excel ou Google Sheets.</p>
    </div>
     <div class="card-container">
        <a href="/help/edge/docs/forms/style-theme-forms.md">
            <img src="/help/edge/assets/smock_imageautomode_18_N.svg" alt="Application de styles ou de thèmes à un formulaire eds" style="border-radius: 5px;"></b><br><b style="margin-top: 5px;">Personnalisation d’un thème
            </b>
        </a>
        <p>Créez une image de marque cohérente en appliquant le même thème à tous les formulaires.</p>
    </div>
      <div class="card-container">
        <a href="/help/edge/docs/forms/validate-forms.md">
            <img src="/help/edge/assets/smock_condition_18_n.svg" alt="Ajouter des validations aux champs de formulaire" style="border-radius: 5px;"></b><br><b style="margin-top: 5px;">Appliquer des validations de champ
            </b>
        </a>
        <p>Réduisez les erreurs et la frustration en vérifiant la mise en forme correcte des entrées de formulaire.</p>
    </div> 
            <div class="card-container">
        <a href="/help/edge/docs/forms/rules-forms.md">
            <img src="/help/edge/assets/smock_documentfragment_18_n.svg" alt="Utilisez des règles pour ajouter un comportement dynamique à un formulaire" style="border-radius: 5px;"></b><br><b style="margin-top: 5px;">Utilisez des règles pour ajouter un comportement dynamique à un formulaire
            </b>
        </a>
        <p>Réutilisez des fragments préconfigurés dans plusieurs formulaires.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/translate-forms.md">  
            <img src="/help/edge/assets/smock_abc_18_n.svg" alt="Traduire un formulaire EDS" style="border-radius: 5px;"></b><br><b style="margin-top: 5px;">Traduire un formulaire
            </b>
        </a>
        <p>Étendez la portée de vos formulaires tout en maîtrisant les coûts.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/repeatable-forms.md">  
            <img src="/help/edge/assets/smock_addto_18_n.svg" alt="Ajouter des sections répétables à un formulaire EDS" style="border-radius: 5px;"></b><br><b style="margin-top: 5px;">Ajouter des sections répétables
            </b>
        </a>
        <p>Créer et ajouter facilement des sections répétables à un formulaire.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/custom-components-forms.md"> 
            <img src="/help/edge/assets/smock_userdeveloper_18_n.svg" alt="Créez des composants de formulaire personnalisés à l’aide des JavaScript et des feuilles de style CSS standard"  style="border-radius: 5px;"></b><br><b style="margin-top: 5px;">Création de composants personnalisés
            </b>
        </a>
        <p>Utilisez des JavaScript et des feuilles de style CSS standard pour créer des composants et des thèmes.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/recaptacha-forms.md">  
            <img src="/help//edge/assets/smock_keyclock_18_n.svg" alt="Utiliser reCAPTCHA dans un formulaire EDS" style="border-radius: 5px;"></b><br><b style="margin-top: 5px;">Utiliser reCAPTCHA
            </b>
        </a>
        <p>Utilisez l’intégration reCAPTCHA prête à l’emploi pour une protection robuste contre le spam et les bots.</p>
    </div>


</div>


</br>









