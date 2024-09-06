---
title: Sélecteur de ressources pour [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]
description: Intégrez le sélecteur de ressources à diverses applications Adobe, non Adobe et tierces.
role: Admin, User
source-git-commit: fb1350c91468f9c448e34b66dc938fa3b5a3e9a9
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 47%

---


# Intégration du sélecteur de ressources à l’aide de Vanilla JS {#integration-using-vanilla-js}

Vous pouvez intégrer n&#39;importe quelle application [!DNL Adobe] ou non Adobe au référentiel [!DNL Experience Manager Assets] et sélectionner des ressources dans l&#39;application. Voir [Intégration de sélecteur de ressources avec diverses applications](#integrate-asset-selector.md).

L’intégration est effectuée en important le package Sélecteur de ressources et en se connectant à Assets as a Cloud Service à l’aide de la bibliothèque JavaScript Vanilla. Modifiez un `index.html` ou tout fichier approprié dans votre application pour :

* Définition des détails d’authentification
* Accès au référentiel Assets as a Cloud Service
* Configuration des propriétés d’affichage du sélecteur de ressources

Vous pouvez effectuer une authentification sans définir certaines des propriétés IMS, si :

* Vous intégrez une application [!DNL Adobe] sur [Unified Shell](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/aem-cloud-service-on-unified-shell.html?lang=fr).
* Un jeton IMS est déjà généré pour l’authentification.

## Intégration du sélecteur de ressources à différentes applications {#asset-selector-integration-with-apps}

Vous pouvez intégrer le sélecteur de ressources à diverses applications, telles que :

* [Intégrer le sélecteur de ressources à une application  [!DNL Adobe] ](#integrate-asset-selector.md)
* [Intégration du sélecteur de ressources à une application non Adobe](#integrate-asset-selector-non-adobe.md)
* [Intégration pour Dynamic Media avec les fonctionnalités OpenAPI](#integrate-asset-selector-dynamic-media-open-api.md)


>[!MORELIKETHIS]
>
>* [Personnalisation du sélecteur de ressources](/help/assets/asset-selector-customization.md)
>* [Propriétés du sélecteur de ressources](/help/assets/asset-selector-properties.md)
>* [ API d’ouverture de média dynamique du sélecteur de ressources ](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)

