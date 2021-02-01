---
title: Notes de mise à jour actuelles de  [!DNL Adobe Experience Manager] en tant que Cloud Service.
description: Notes de mise à jour actuelles de  [!DNL Adobe Experience Manager] en tant que Cloud Service.
translation-type: tm+mt
source-git-commit: 1ac061dfc9773a1de0b1d5f8c427f8d770ca73fa
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 15%

---


# Notes de mise à jour pour [!DNL Adobe Experience Manager] as a Cloud Service  {#release-notes}

La section suivante décrit les Notes de mise à jour générales de [!DNL Experience Manager] en tant que Cloud Service.

## Date de publication {#release-date}

La date de publication de [!DNL Adobe Experience Manager] en tant que Cloud Service 2020.12.0 est le 17 décembre 2020.
La version suivante (2021.1.0) sera publiée le 28 janvier 2021.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service{#sites}

* **[API](/help/assets/content-fragments/assets-api-content-fragments.md)** HTTP de fragment de contenu : Ajoutez la possibilité d’ajouter/de mettre à jour et de supprimer des variations de fragments de contenu à l’aide de l’API HTTP.

## [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

* L&#39;intégration à [!DNL Adobe InDesign Server] est désormais disponible pour [!DNL Experience Manager] en tant que [!DNL Cloud Service]. Il permet l’automatisation du traitement des fichiers [!DNL Adobe InDesign] à l’aide de scripts [!DNL Adobe InDesign Server] et aux utilisateurs d’utiliser l’interface utilisateur des modèles [!DNL Assets] pour créer des brochures ou des publicités. Seul [!DNL InDesign Server] hébergé par [!DNL Adobe Managed Services] est pris en charge pour [!DNL Experience Manager as a Cloud Service]. <!-- TBD: Add link to article. -->

* [!DNL Experience Manager] est amélioré pour suivre et afficher les références de ressources lorsqu’une ressource est utilisée dans un  [!DNL Experience Manager Sites] déploiement distant à l’aide de la fonctionnalité Ressources connectées. Un nouvel onglet [!UICONTROL Références] de la page [!UICONTROL Propriétés] de la ressource liste désormais les références locales et distantes de la ressource. Les références permettent aux utilisateurs DAM de suivre l&#39;utilisation des ressources dans les pages [!DNL Sites] et dans les ressources composées dans [!DNL Assets]. Voir [configuration et utilisation des ressources connectées](/help/assets/use-assets-across-connected-assets-instances.md).

* [!DNL Dynamic Media] les fonctionnalités sont désormais accessibles via les composants principaux basés sur les  [!DNL Sites] images. Les auteurs peuvent configurer rapidement les composants pour qu’ils utilisent les paramètres d’image prédéfinis, les options de recadrage dynamique et les modificateurs d’image lors de la création de pages Web. Voir [Core Components 2.13.0 release](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.13.0).

* [!DNL Experience Manager] application de bureau permet aux utilisateurs de télécharger des fichiers et des dossiers en faisant glisser les fichiers depuis l’Explorateur Windows ou l’Outil de recherche Mac sur l’interface de l’application de bureau. Voir [ajout de ressources à l’aide de l’application de bureau](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#upload-and-add-new-assets-to-aem).

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nouveautés {#what-is-new-commerce}

* Site de référence de CIF Venia - 2020.12.01 qui comprend la dernière version des composants principaux de CIF version 1.6.0. Pour plus d&#39;informations, consultez [Site de référence de CIF Venia](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.12.01).

* Publication des composants principaux CIF version 1.6.0. Reportez-vous à [Composants principaux CIF](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.6.0) pour plus de détails.

## Cloud Manager {#cloud-manager}

### Date de publication {#release-date-cm}

La date de publication de Cloud Manager en tant que Cloud Service 2021.1.0 est le 14 janvier 2021.

### Correctifs {#bug-fixes-cloud-manager}

* L’instance de production de ressources peut, à l’occasion, afficher l’état du portail de la marque sur la page de détails **Environnements** sous la forme *En attente* sans permettre à l’utilisateur d’effectuer une action.

* Lors du déclenchement d’une désactivation de l’hibernation à partir de Cloud Manager, un message d’échec s’affichait parfois, même lorsque la désactivation de l’hibernation était correctement lancée.

* Les rares cas d&#39;échec rencontrés lors de la création ou de la suppression d&#39;environnements ont été résolus.

## Outils de refactorisation du code {#code-refactoring-tools}

### Nouveautés de [!DNL Code Refactoring Tools] {#what-is-new-crt}

* Nouvelle version du module externe AIO-CLI publiée. La dernière version de ce module comprend des correctifs pour AEM Dispatcher Converter et Repository Modernizer et prend également en charge un nouvel utilitaire - Index Converter. Consultez [Expérience unifiée](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html?lang=en#benefits) pour en savoir plus sur ce module externe.

* Index Converter est un utilitaire qui permet de transformer les définitions d&#39;index OAK personnalisées d&#39;un client en AEM en définitions d&#39;index OAK compatibles avec les Cloud Service. Pour plus d&#39;informations, consultez [Index Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter).

* Nouvelle fonctionnalité ajoutée à [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) qui crée un package distinct `ui.config` qui contient toutes les configurations OSGi.

### Correctifs {#crt-bug-fixes}

* Plusieurs correctifs de bogues ont été apportés aux outils  Dispatcher Converter et Repository Modernizer. Veuillez vous reporter à [AEM Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter) et [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer).

## Outils de transition vers le cloud {#code-transition-tools}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu v1.2.20 est le 01 février 2021.

### Nouveautés de [!DNL Content Transfer Tool] {#what-is-new-ctt}

* Nouvelle fonctionnalité et interface utilisateur ajoutées à l’outil de transfert de contenu - Outil de mappage des utilisateurs. Cette fonctionnalité mappe automatiquement les utilisateurs et les groupes existants à leurs identifiants système Identity Management Adobe dans le cadre de l’activité de migration de contenu. Pour plus d&#39;informations, consultez [Utilisation de l&#39;outil de mappage utilisateur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html).
* L’outil de transfert de contenu migre désormais tous les groupes et utilisateurs référencés dans le jeu de migration, y compris les enfants.
* Les utilisateurs sont autorisés à sélectionner certains chemins sous `/etc` lors de la création de jeux de migration.
