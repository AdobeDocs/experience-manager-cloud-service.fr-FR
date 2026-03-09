---
title: Intégration du sélecteur de ressources à l’aide de Vanilla JS
description: Intégrer le sélecteur de ressources à diverses applications Adobe, non Adobe et tierces.
role: Admin, User
badgeSaas: label="AEM Assets" type="Positive" tooltip="S’applique à AEM Assets)."
exl-id: 1c0051a3-549c-4783-9fc1-594f424a70c3
source-git-commit: a641933d1049cd07ee8935672c8ef357a5bbf18c
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 58%

---

# Intégration du sélecteur de ressources à l’aide de Vanilla JS {#integration-using-vanilla-js}

Vous pouvez intégrer n’importe quelle application [!DNL Adobe] ou non Adobe à [!DNL Experience Manager Assets] référentiel et sélectionner des ressources dans l’application. Voir [ Intégration du sélecteur de ressources à diverses applications ](#asset-selector-integration-with-apps).

L’intégration est effectuée en important le package Sélecteur de ressources et en se connectant à Assets as a Cloud Service à l’aide de la bibliothèque JavaScript Vanilla. Modifiez un `index.html` ou tout fichier approprié dans votre application pour :

* Définition des détails d’authentification
* Accès au référentiel Assets as a Cloud Service
* Configuration des propriétés d’affichage du sélecteur de ressources

Vous pouvez effectuer une authentification sans définir certaines des propriétés IMS, si :

* Vous intégrez une application [!DNL Adobe] sur [Unified Shell](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/aem-cloud-service-on-unified-shell.html?lang=fr).
* Un jeton IMS est déjà généré pour l’authentification.

## Intégration du sélecteur de ressources à diverses applications {#asset-selector-integration-with-apps}

Vous pouvez intégrer le sélecteur de ressources à diverses applications, telles que :

* [Intégration du sélecteur de ressources à une application  [!DNL Adobe] ](/help/assets/integrate-asset-selector-adobe-app.md)
* [Intégrer le sélecteur de ressources à une application non Adobe](/help/assets/integrate-asset-selector-non-adobe-app.md)
* [Intégration de Dynamic Media aux fonctionnalités OpenAPI](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)


>[!MORELIKETHIS]
>
>* [Personnalisation du sélecteur de ressources](/help/assets/asset-selector-customization.md)
>* [Propriétés du sélecteur de ressources](/help/assets/asset-selector-properties.md)
>* [Intégration du sélecteur de ressources à Dynamic Media avec fonctionnalités OpenAPI](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)
