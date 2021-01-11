---
title: Notes de mise à jour actuelles de  [!DNL Adobe Experience Manager] en tant que Cloud Service.
description: Notes de mise à jour actuelles de  [!DNL Adobe Experience Manager] en tant que Cloud Service.
translation-type: tm+mt
source-git-commit: cfe49fe414f387c660259de540af0cc26ef3951f
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 17%

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

La date de publication de Cloud Manager en tant que Cloud Service 2020.12.0 est le 10 décembre 2020.

### Nouveautés de [!DNL Cloud Manager] {#what-is-new-cm}

* Gestion en libre-service des [certificats SSL](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md) et [noms de domaine personnalisés](/help/implementing/cloud-manager/custom-domain-names/introduction.md).

* Gestion en libre-service des [Listes autorisées IP](/help/implementing/cloud-manager/ip-allow-lists/introduction.md).

* La page de détails **Environnement** mise à jour permet désormais aux utilisateurs de gérer les noms de domaine personnalisés et les Listes autorisées IP sur leurs environnements.

### Correctifs {#bug-fixes-cloud-manager}

* Certaines occurrences d’échecs au stade de l’analyse du code sans fournir de résultats ont été corrigées.

* La carte d&#39;Environnement n&#39;affichait pas systématiquement le bouton **Ajouter**.

## Outils de refactorisation du code {#code-refactoring-tools}

### Nouveautés de [!DNL Code Refactoring Tools] {#what-is-new-crt}

* Nouvelle version du module externe AIO-CLI publiée. La dernière version de ce module comprend des correctifs pour AEM Dispatcher Converter et Repository Modernizer et prend également en charge un nouvel utilitaire - Index Converter. Consultez [Expérience unifiée](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html?lang=en#benefits) pour en savoir plus sur ce module externe.

* Index Converter est un utilitaire qui permet de transformer les définitions d&#39;index OAK personnalisées d&#39;un client en AEM en définitions d&#39;index OAK compatibles avec les Cloud Service. Pour plus d&#39;informations, consultez [Index Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter).

* Nouvelle fonctionnalité ajoutée à [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) qui crée un package distinct `ui.config` qui contient toutes les configurations OSGi.

### Correctifs {#crt-bug-fixes}

* Plusieurs correctifs de bogues ont été apportés aux outils  Dispatcher Converter et Repository Modernizer. Veuillez vous reporter à [AEM Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter) et [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer).

## Outils de transition vers le cloud {#code-transition-tools}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu v1.1.20 est le 8 janvier 2021.

### Nouveautés de [!DNL Content Transfer Tool] {#what-is-new-ctt}

* Les utilisateurs peuvent désormais savoir si leur Jeton d&#39;accès a expiré en pointant vers l’icône d’état de l’interface utilisateur de l’outil de transfert de contenu (CTT). Ils seront également avertis dans l’interface utilisateur Détails du jeu de migration qu’ils ne peuvent pas se connecter à leur instance de Cloud Service.

### Correctifs {#ctt-bug-fixes}

* L’état de l’interface utilisateur de l’outil de transfert de contenu (CTT) pour un jeu de migration n’était pas conservé et modifié après une période d’inactivité. Ce problème a été résolu.
* L&#39;option permettant d&#39;accéder aux journaux de vue était désactivée si les journaux n&#39;étaient pas disponibles. Ce problème a été corrigé et un message a été ajouté pour informer l’utilisateur de l’absence de journaux.
* L’état de l’interface utilisateur de l’outil de transfert de contenu affichait ÉCHOUÉ lorsque l’utilisateur arrêtait une assimilation. Ce problème a été corrigé pour afficher à la place *STOPPED*.

