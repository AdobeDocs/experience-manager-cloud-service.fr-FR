---
title: Présentation du service de diffusion Edge AEM Forms
description: Le service de diffusion Edge d’AEM Forms, conçu pour offrir des performances optimales, vous permet d’envisager l’avenir d’une collecte de données rationalisée et de l’engagement des utilisateurs.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: b94bd6cd70af541444fda1d03f502b4588fd879b
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---


# Service de diffusion Edge AEM Forms {#aem-forms-edge-delivery-service-overview}

AEM Forms Edge Delivery Service est un service composable proposé par Adobe qui vous permet de créer et de diffuser des formulaires web à fort impact et performants. Ce service composable s’intègre parfaitement à Adobe Experience Manager (AEM) pour vous permettre de concevoir, de créer et de déployer des formulaires web à fort impact et à la vitesse d’éclair avec un workflow intuitif et efficace.

AEM Forms Edge Delivery Service vous aide à :

* **Concevoir des formulaires étonnants**: décompressez les conceptions fades et découpeuses de cookies et séduisez les utilisateurs avec des formulaires dynamiques et modernes qui reflètent l’identité de votre marque. Tirez parti des composants prédéfinis ou créez vos propres composants personnalisés pour donner vie rapidement et facilement à votre vision.

* **Créer des formulaires avec un score parfait pour Lightouse**: créez des formulaires qui se chargent et s’affichent rapidement, même avec des connexions Internet lentes. Des temps de chargement plus rapides et une expérience utilisateur optimisée contribuent à des taux d’achèvement de formulaire plus élevés et à de meilleurs taux de conversion.

* **Simplification de la création et des envois**: créez des formulaires à l’aide d’outils familiers tels que Microsoft Excel ou Google Sheets au lieu des environnements de création traditionnels. Envoyez des formulaires directement à vos feuilles Microsoft Excel ou Google et utilisez leur écosystème pour traiter facilement les données envoyées.

## Prise en main du service de diffusion Edge d’AEM Forms

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
            <br><b style="margin-top: 5px;">Création d’un formulaire</b>
        </a>
        <p>Créez des formulaires qui se chargent et s’affichent rapidement et automatiquement sur les périphériques mobiles.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/validate-forms.md">
            <img src="/help/edge/assets/smock_condition_18_n.svg" alt="Ajouter des validations à des champs de formulaire" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Appliquer les validations de champ</b>
        </a>
        <p>Réduisez les erreurs et les frustrations en vérifiant les entrées du formulaire pour une mise en forme correcte.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/form-fragments.md">
            <img src="/help/edge/assets/smock_documentfragment_18_n.svg" alt="Utilisation de fragments de formulaire dans un formulaire EDS" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Créer des fragments de formulaire</b>
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
        <a href="/help/edge/docs/forms/style-theme-forms.md">
            <img src="/help/edge/assets/smock_imageautomode_18_N.svg" alt="Application de styles ou de thèmes à un formulaire de texte" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Personnalisation d’un thème</b>
        </a>
        <p>Créez une image de marque cohérente en appliquant le même thème à tous les formulaires.</p>
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
    <div class="card-container">
        <a href="/help/edge/docs/forms/create-forms.md#manually-configure-a-spreadsheet-to-accept-data">   
            <img src="/help/edge/assets/smock_platformdatamapping_18_n.svg" alt="Envoyer le formulaire" alt="Utilisation de fragments de formulaire dans un formulaire EDS" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Envoyer le formulaire à la feuille de calcul</b>
        </a>
        <p>Envoyez des formulaires directement à vos feuilles Microsoft Excel ou Google.</p>
    </div>
</div>


</br>









