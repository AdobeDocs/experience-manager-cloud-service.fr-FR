---
title: Problèmes connus
description: Problèmes connus liés à Adobe Experience Manager as a Cloud Service
exl-id: 897b944a-d320-4d21-91f4-2cd3da6179b1
source-git-commit: 8ec0ce3425e7cade0a6774a4452d4f47ab971375
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 100%

---

# Problèmes connus {#known-issues}

Cet article répertorie les problèmes connus de l’offre [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]. La liste est révisée et mise à jour à chaque version d’[!DNL Experience Manager].

Pour en savoir plus sur les problèmes connus ci-dessous, [contactez l’assistance](https://experienceleague.adobe.com/?lang=fr&amp;support-solution=Experience+Manager#support).

<!-- 
## Platform {#platform}

## Sites {#sites}
-->

## [!DNL Assets] {#assets}

<!-- Jira label: assets-cloud-known-issues -->

Certains problèmes connus dans [!DNL Assets] sont :

* **Télécharger** : si vous téléchargez un dossier vide, [!DNL Experience Manager] transmet un message de réussite concernant la création d’une archive ZIP, mais l’archive n’est pas créée.

* **Schéma de métadonnées** : le widget d’évaluation des ressources entraînait une erreur de compilation JSP. Il a été supprimé du schéma de métadonnées. <!-- CQ-4282865, CQ-4284633 -->

Voir aussi [modifications notables apportées à [!DNL Experience Manager Assets]](/help/assets/assets-cloud-changes.md).

<!-- This content was added at GA. Not sure if we should continue to have this commitment about upcoming features/enh. in the docs. Commenting it for now.

### Upcoming Assets capabilities {#upcoming-assets-capabilities}

A few capabilities of Adobe Experience Manager Assets that depend on foundation capabilities, which are not yet available in the Experience Manager as a Cloud Service deployment architecture, are expected to be enabled at a later stage:

* Capabilities not enabled at this stage due to dependency on Commerce Integration Framework APIs:
  * Photoshoot workflow models.
  * Product information tab in the asset properties user interface is not populated.

* Capabilities not enabled at this stage due to dependency on InDesign Server integration:
  * Asset Templates and Asset Catalogs.
  * Multi-page preview of Adobe InDesign files.
-->

>[!MORELIKETHIS]
>
>* [Modifications majeures dans [!DNL Experience Manager]](aem-cloud-changes.md)
>* [Fonctionnalités obsolètes et supprimées](deprecated-removed-features.md)
>* [Notes de mise à jour](home.md)

