---
title: Sélecteur de ressources pour [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]
description: Intégrez le sélecteur de ressources à diverses applications Adobe, non Adobe et tierces.
role: Admin, User
exl-id: 1c0051a3-549c-4783-9fc1-594f424a70c3
source-git-commit: 575980320c1dbd32f799bf9c2fddf3d6773c838a
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 46%

---

# Intégration du sélecteur de ressources à l’aide de Vanilla JS {#integration-using-vanilla-js}

Vous pouvez intégrer n&#39;importe quelle application [!DNL Adobe] ou non Adobe au référentiel [!DNL Experience Manager Assets] et sélectionner des ressources dans l&#39;application. Voir [Intégration de sélecteur de ressources avec diverses applications](#asset-selector-integration-with-apps).

L’intégration est effectuée en important le package Sélecteur de ressources et en se connectant à Assets as a Cloud Service à l’aide de la bibliothèque JavaScript Vanilla. Modifiez un `index.html` ou tout fichier approprié dans votre application pour :

* Définition des détails d’authentification
* Accès au référentiel Assets as a Cloud Service
* Configuration des propriétés d’affichage du sélecteur de ressources

Vous pouvez effectuer une authentification sans définir certaines des propriétés IMS, si :

* Vous intégrez une application [!DNL Adobe] sur [Unified Shell](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/aem-cloud-service-on-unified-shell.html?lang=fr).
* Un jeton IMS est déjà généré pour l’authentification.

## Intégration du sélecteur de ressources à différentes applications {#asset-selector-integration-with-apps}

Vous pouvez intégrer le sélecteur de ressources à diverses applications, telles que :

* [Intégrer le sélecteur de ressources à une application  [!DNL Adobe] ](/help/assets/integrate-asset-selector-adobe-app.md)
* [Intégration du sélecteur de ressources à une application non Adobe](/help/assets/integrate-asset-selector-non-adobe-app.md)
* [Intégration pour Dynamic Media avec les fonctionnalités OpenAPI](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)


>[!MORELIKETHIS]
>
>* [Personnalisations du sélecteur de ressources](/help/assets/asset-selector-customization.md)
>* [Propriétés du sélecteur de ressources](/help/assets/asset-selector-properties.md)
>* [Intégrer le sélecteur de ressources à Dynamic Media avec les fonctionnalités OpenAPI](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)