---
title: Notes de mise à jour de la version 2020.12.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour de la version 2020.12.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 16875180-1f23-477d-9d4d-e220998c4983
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 89%

---

# Notes de mise à jour pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante présente les notes de mise à jour générales d’[!DNL Experience Manager] as a Cloud Service.

## Date de publication {#release-date}

La date de publication d’[!DNL Adobe Experience Manager] as a Cloud Service version 2020.12.0 est le 17 décembre 2020.
La version suivante (2021.1.0) sera publiée le 28 janvier 2021.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

* **[API HTTP de fragment de contenu](/help/assets/content-fragments/assets-api-content-fragments.md)** : ajoutez la possibilité d’ajouter ou de mettre à jour et de supprimer des variations de fragments de contenu à l’aide de l’API HTTP.

## [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

* L’intégration à [!DNL Adobe InDesign Server] est désormais disponible pour [!DNL Experience Manager] as a [!DNL Cloud Service]. Il permet l’automatisation du traitement des fichiers [!DNL Adobe InDesign] à l’aide de scripts [!DNL Adobe InDesign Server] et aux utilisateurs d’utiliser l’interface utilisateur des modèles [!DNL Assets] pour créer des brochures ou des publicités. Seul [!DNL InDesign Server] hébergé par [!DNL Adobe Managed Services] est pris en charge pour [!DNL Experience Manager as a Cloud Service]. <!-- TBD: Add link to article. -->

* [!DNL Experience Manager] a été amélioré pour suivre et afficher les références de ressources lorsqu’une ressource est utilisée dans un déploiement [!DNL Experience Manager Sites] distant à l’aide de la fonctionnalité Ressources connectées. Un nouvel onglet [!UICONTROL Références] dans la page [!UICONTROL Propriétés] de la ressource répertorie désormais les références locales et distantes de la ressource. Les références permettent aux utilisateurs DAM de suivre l’utilisation des ressources dans les pages [!DNL Sites] et dans les ressources composées dans [!DNL Assets]. Voir [Configuration et utilisation des ressources connectées](/help/assets/use-assets-across-connected-assets-instances.md).

* Les fonctionnalités [!DNL Dynamic Media] sont désormais accessibles via les composants principaux basés sur les images [!DNL Sites]. Les auteurs peuvent configurer rapidement les composants pour qu’ils utilisent les paramètres d’image prédéfinis, les options de recadrage dynamique et les modificateurs d’image lors de la création de pages web. Voir [Version 2.13.0 des composants de base](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.13.0).

* L’application de bureau [!DNL Experience Manager] permet aux utilisateurs de charger des fichiers et des dossiers en faisant glisser les fichiers depuis l’Explorateur Windows ou l’Outil de recherche Mac vers l’interface de l’application de bureau. Voir [Ajout de ressources à l’aide de l’application de bureau](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=fr#upload-and-add-new-assets-to-aem).

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nouveautés {#what-is-new-commerce}

* Site de référence CIF Venia - 2020.12.01 qui comprend la dernière version des composants principaux CIF v1.6.0. Voir [Site de référence CIF Venia](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.12.01) pour plus d’informations.

* Composants principaux CIF version 1.6.0. Voir [Composants principaux CIF](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.6.0) pour plus d’informations.

## Cloud Manager {#cloud-manager}

### Date de publication {#release-date-cm}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2020.12.0 est le 10 décembre 2020.

### Nouveautés d’[!DNL Cloud Manager]  {#what-is-new-cm}

* Gestion en libre-service de [Certificats SSL](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md) et [Noms de domaine personnalisés](/help/implementing/cloud-manager/custom-domain-names/introduction.md).

* Gestion en libre-service de [LISTES AUTORISÉES IP](/help/implementing/cloud-manager/ip-allow-lists/introduction.md).

* La page des détails de l’**environnement** mise à jour permet désormais aux utilisateurs de gérer les noms de domaine personnalisés et les listes autorisées IP sur leurs environnements.

### Correctifs {#bug-fixes-cloud-manager}

* Certaines occurrences d’échecs à l’étape d’analyse du code sans fournir de résultats ont été corrigées.

* La carte d’environnement n’affichait pas systématiquement le bouton **Ajouter**.

## Outils de refactorisation du code {#code-refactoring-tools}

### Nouveautés d’[!DNL Code Refactoring Tools]  {#what-is-new-crt}

* Publication de la nouvelle version du plug-in AIO-CLI. La dernière version de ce plug-in comprend des correctifs pour le Dispatcher Converter et le Repository Modernizer AEM et prend également en charge un nouvel utilitaire : Index Converter. Voir [Expérience unifiée](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html?lang=fr#benefits) pour en savoir plus sur ce module externe.

* Index Converter est un utilitaire qui permet de transformer les définitions d’index OAK personnalisées d’un client en définitions d’index OAK compatibles avec AEM as a Cloud Service. Voir [Convertisseur d’index](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter) pour plus d’informations.

* Nouvelle fonctionnalité ajoutée à [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) qui crée un package distinct `ui.config` contenant toutes les configurations OSGi.

### Correctifs {#crt-bug-fixes}

* Plusieurs correctifs de bogues ont été apportés aux outils Dispatcher Converter et Repository Modernizer d’AEM. Voir [Convertisseur du Dispatcher AEM](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter) et [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer).

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu version v1.1.20 est le 8 janvier 2021.

### Nouveautés d’[!DNL Content Transfer Tool]  {#what-is-new-ctt}

* Les utilisateurs peuvent désormais savoir si leur jeton d’accès a expiré en pointant vers l’icône de statut de l’interface utilisateur de l’outil de transfert de contenu (CTT). Ils seront également avertis dans l’interface utilisateur des détails du jeu de migration qu’ils ne peuvent pas se connecter à leur instance de Cloud Service.

### Correctifs {#ctt-bug-fixes}

* Le statut de l’interface utilisateur de l’outil de transfert de contenu (CTT) pour un jeu de migration n’était pas conservé et modifié après une période d’inactivité. Ce problème a été résolu.
* L’option permettant d’accéder aux journaux de vue était désactivée si les journaux n’étaient pas disponibles. Ce problème a été corrigé et un message a été ajouté pour informer l’utilisateur de la raison de l’absence des journaux.
* Le statut de l’interface utilisateur de l’outil de transfert de contenu affichait *FAILED* lorsque l’utilisateur stoppait une ingestion. Ce problème a été corrigé pour afficher à la place *STOPPED*.
