---
title: Notes de mise à jour de la version 2020.12.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour de la version 2020.12.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 16875180-1f23-477d-9d4d-e220998c4983
feature: Release Information
role: Admin
source-git-commit: 64344b9b2cce8d7c7f05d3e5ba94049346308a9d
workflow-type: tm+mt
source-wordcount: '774'
ht-degree: 50%

---

# Notes de mise à jour pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante présente les notes de mise à jour générales d’[!DNL Experience Manager] as a Cloud Service.

## Date de publication {#release-date}

La date de publication d’[!DNL Adobe Experience Manager] as a Cloud Service version 2020.12.0 est le 17 décembre 2020.
La version suivante (2021.1.0) est le 28 janvier 2021.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

* **[API HTTP de fragment de contenu](/help/assets/content-fragments/assets-api-content-fragments.md)** : ajoutez la possibilité d’ajouter ou de mettre à jour et de supprimer des variations de fragments de contenu à l’aide de l’API HTTP.

## [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

* L’intégration à [!DNL Adobe InDesign Server] est désormais disponible pour [!DNL Experience Manager] as a [!DNL Cloud Service]. Il permet l’automatisation du traitement des fichiers [!DNL Adobe InDesign] à l’aide de scripts [!DNL Adobe InDesign Server] et aux utilisateurs d’utiliser l’interface utilisateur des modèles [!DNL Assets] pour créer des brochures ou des publicités. Seul [!DNL InDesign Server] hébergé par [!DNL Adobe Managed Services] est pris en charge pour [!DNL Experience Manager as a Cloud Service]. <!-- TBD: Add link to article. -->

* [!DNL Experience Manager] a été amélioré pour suivre et afficher les références de ressources lorsqu’une ressource est utilisée dans un déploiement [!DNL Experience Manager Sites] distant à l’aide de la fonctionnalité Ressources connectées. Un nouvel onglet [!UICONTROL Références] dans la page [!UICONTROL Propriétés] de la ressource répertorie désormais les références locales et distantes de la ressource. Les références permettent aux utilisateurs DAM de suivre l’utilisation des ressources dans les pages [!DNL Sites] et dans les ressources composées dans [!DNL Assets]. Voir [Configuration et utilisation des ressources connectées](/help/assets/use-assets-across-connected-assets-instances.md).

* [!DNL Dynamic Media] fonctionnalités sont désormais accessibles par le biais des composants principaux basés sur des images d’AEM [!DNL Sites]. Il est possible de configurer rapidement les composants de manière à utiliser les paramètres d’image prédéfinis, les options de recadrage dynamique et les modificateurs d’image lors de la création de pages web. Voir [Version 2.13.0 des composants principaux](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.13.0).

* L’application de bureau [!DNL Experience Manager] permet aux utilisateurs de télécharger des fichiers et des dossiers en faisant glisser les fichiers depuis l’Explorateur Windows ou le Finder Mac vers l’interface de l’application de bureau. Voir [ Ajout de ressources à l’aide de l’application de bureau ](https://experienceleague.adobe.com/en/docs/experience-manager-desktop-app/using/using#upload-and-add-new-assets-to-aem).

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nouveautés {#what-is-new-commerce}

* Publication du site de référence CIF Venia - 2020.12.01 qui comprend les derniers composants principaux de CIF version 1.6.0. Voir [Site de référence CIF Venia](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.12.01) pour plus d’informations.

* Publication des composants principaux de CIF version 1.6.0. Voir [Composants principaux ](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.6.0) pour plus d’informations.

## Cloud Manager {#cloud-manager}

### Date de publication {#release-date-cm}

La date de publication de Cloud Manager dans Adobe Experience Manager (AEM) as a Cloud Service 2020.12.0 est le 10 décembre 2020.

### Nouveautés de [!DNL Cloud Manager] {#what-is-new-cm}

* Gestion en libre-service des [certificats SSL](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md) et [Présentation des noms de domaine personnalisés](/help/implementing/cloud-manager/custom-domain-names/introduction.md).

* Gestion en libre-service des [listes autorisées d’adresses IP](/help/implementing/cloud-manager/ip-allow-lists/introduction.md).

* La page de détails **Environnement** mise à jour permet désormais aux utilisateurs de gérer les noms de domaine personnalisés et les Listes autorisées IP sur leurs environnements.

### Correctifs {#bug-fixes-cloud-manager}

* Certaines occurrences d’échecs à l’étape d’analyse du code sans fournir de résultats sont corrigées.

* La carte Environnement n’affichait pas systématiquement le bouton **Ajouter**.

## Outils de refactorisation du code {#code-refactoring-tools}

### Nouveautés d’[!DNL Code Refactoring Tools] {#what-is-new-crt}

* Publication de la nouvelle version du plug-in AIO-CLI. La dernière version de ce plug-in inclut des correctifs pour le convertisseur AEM Dispatcher et Repository Modernizer et prend également en charge un nouvel utilitaire : le convertisseur d’index. Voir [Expérience unifiée](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/migration-journey/refactoring-tools/unified-experience#benefits) pour en savoir plus sur ce plug-in.

* Index Converter est un utilitaire qui peut être utilisé pour transformer les définitions d’index Oak personnalisées d’un client en définitions d’index Oak compatibles avec AEM as a Cloud Service. Voir [Index Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter) pour plus d’informations.

* Nouvelle fonctionnalité ajoutée à [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) qui crée un package distinct `ui.config` contenant toutes les configurations OSGi.

### Correctifs {#crt-bug-fixes}

* Plusieurs correctifs ont été apportés aux outils AEM Dispatcher Converter et Repository Modernizer. Voir [AEM Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter) et [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer).

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu version v1.1.20 est le 8 janvier 2021.

### Nouveautés d’[!DNL Content Transfer Tool] {#what-is-new-ctt}

* Les utilisateurs peuvent désormais savoir si leur jeton d’accès a expiré en pointant vers l’icône de statut de l’interface utilisateur de l’outil de transfert de contenu (CTT). Ils sont également avertis dans l’interface utilisateur Détails du jeu de migration qu’ils ne peuvent pas se connecter à leur instance Cloud Service.

### Correctifs {#ctt-bug-fixes}

* Le statut de l’interface d’utilisation de l’outil de transfert de contenu (CTT) pour un ensemble de migration n’était pas conservé et modifié après une période d’inactivité. Ce problème est maintenant résolu.
* L’option d’affichage des journaux était désactivée si les journaux n’étaient pas disponibles. Ce problème est maintenant corrigé et un message est maintenant ajouté pour informer les utilisateurs pourquoi les journaux sont manquants.
* Le statut de l’interface utilisateur de l’outil de transfert de contenu affichait *ÉCHEC* lorsque l’utilisateur arrêtait une ingestion. Ce problème est maintenant corrigé et affiche désormais *STOPPED* à la place.
