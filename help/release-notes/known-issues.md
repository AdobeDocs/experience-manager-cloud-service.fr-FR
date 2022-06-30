---
title: Problèmes connus
description: Problèmes connus liés à Adobe Experience Manager as a Cloud Service
exl-id: 897b944a-d320-4d21-91f4-2cd3da6179b1
source-git-commit: 755c0072148ad73486df2ccfed69248b9d73ec2a
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 66%

---

# Problèmes connus {#known-issues}

Cet article répertorie les problèmes connus de l’offre [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]. La liste est révisée et mise à jour à chaque version d’[!DNL Experience Manager].

Pour en savoir plus sur les problèmes connus ci-dessous, [contactez l’assistance](https://experienceleague.adobe.com/?lang=fr&amp;support-solution=Experience+Manager#support).

<!-- 
## Platform {#platform}
-->

## Sites {#sites}

Certains problèmes connus dans [!DNL Sites] sont :

* Dans l’IDE GraphQL, vous pouvez [gérer le cache de vos requêtes persistantes ;](/help/headless/graphql-api/graphiql-ide.md##managing-cache).
   * Lors du premier enregistrement, les valeurs enregistrées pour les en-têtes sont définies sur `0` (au lieu des valeurs par défaut) : si l’utilisateur n’a pas modifié ces valeurs dans la boîte de dialogue.
   * Lors des enregistrements suivants, les valeurs sont correctement enregistrées.
   * Par conséquent, l’utilisateur doit enregistrer les en-têtes deux fois.

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

