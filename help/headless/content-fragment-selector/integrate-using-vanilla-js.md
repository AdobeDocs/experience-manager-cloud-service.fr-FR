---
title: Intégrer le sélecteur de fragment de contenu à l’aide de Vanilla JS
description: Intégrez le sélecteur de fragment de contenu à diverses applications Adobe, non Adobe et tierces.
role: Admin, User, Developer
source-git-commit: 592e443928f2c9c18ac281027026132b1c877ce3
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 2%

---

# Intégrer le sélecteur de fragment de contenu à l’aide de Vanilla JS {#integrate-content-fragment-selector-using-vanilla-js}

Vous pouvez intégrer n’importe quelle application Adobe ou autre qu’Adobe à Adobe Experience Manager (AEM) as a Cloud Repository et sélectionner des fragments de contenu depuis cette application.

L’intégration est effectuée en important le package Sélecteur de fragment de contenu et en se connectant à AEM as a Cloud Service à l’aide de la bibliothèque JavaScript Vanilla. Modifiez un `index.html` ou tout fichier approprié dans votre application pour :

* Définition des détails d’authentification
* Accès au référentiel AEM as a Cloud Service
* Configurer les propriétés d’affichage du sélecteur de fragments de contenu

Vous pouvez effectuer une authentification sans définir certaines des propriétés IMS, si vous :

* intègrent une application Adobe sur [ Unified Shell ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/overview/aem-cloud-service-on-unified-shell)
* un jeton IMS est déjà généré pour l’authentification
