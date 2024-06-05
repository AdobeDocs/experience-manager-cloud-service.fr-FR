---
title: Notes de mise à jour de la version 2020.12.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour de la version 2020.12.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 16875180-1f23-477d-9d4d-e220998c4983
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '652'
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

* [!DNL Experience Manager] a été amélioré pour suivre et afficher les références de ressources lorsqu’une ressource est utilisée dans un déploiement [!DNL Experience Manager Sites] distant à l’aide de la fonctionnalité Ressources connectées. Une nouvelle [!UICONTROL Références] dans le [!UICONTROL Propriétés] répertorie désormais les références locales et distantes de la ressource. Les références permettent aux utilisateurs DAM de suivre l’utilisation des ressources dans les pages [!DNL Sites] et dans les ressources composées dans [!DNL Assets]. Voir [Configuration et utilisation des ressources connectées](/help/assets/use-assets-across-connected-assets-instances.md).

* [!DNL Dynamic Media] Les fonctionnalités sont désormais accessibles par AEM [!DNL Sites] composants principaux basés sur des images. Les auteurs peuvent configurer rapidement les composants pour qu’ils utilisent les paramètres d’image prédéfinis, les options de recadrage dynamique et les modificateurs d’image lors de la création de pages web. Voir [Version 2.13.0 des composants de base](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.13.0).

* La variable [!DNL Experience Manager] L’appli de bureau permet aux utilisateurs de charger des fichiers et des dossiers en les faisant glisser depuis l’Explorateur Windows ou le Finder Mac sur l’interface de l’appli de bureau. Voir [ajout de ressources à l’aide de l’appli de bureau](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=fr#upload-and-add-new-assets-to-aem).

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nouveautés {#what-is-new-commerce}

* Publication CIF site de référence Venia - 2020.12.01 qui comprend la dernière version de CIF Core Components v1.6.0. Voir [Site de référence Venia CIF](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.12.01) pour plus d’informations.

* Publication CIF composants principaux v1.6.0. Voir [CIF composants principaux](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.6.0) pour plus d’informations.

## Cloud Manager {#cloud-manager}

### Date de publication {#release-date-cm}

La date de publication de Cloud Manager dans Adobe Experience Manager (AEM) as a Cloud Service 2020.12.0 est le 10 décembre 2020.

### Nouveautés de [!DNL Cloud Manager]  {#what-is-new-cm}

* Gestion en libre-service des [certificats SSL](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md) et des [noms de domaine personnalisés](/help/implementing/cloud-manager/custom-domain-names/introduction.md).

* Gestion en libre-service des [listes autorisées d’adresses IP](/help/implementing/cloud-manager/ip-allow-lists/introduction.md).

* La mise à jour **Environnement** La page détails permet désormais aux utilisateurs de gérer les noms de domaine personnalisés et les Listes autorisées IP dans leurs environnements.

### Correctifs {#bug-fixes-cloud-manager}

* Certaines occurrences d’échecs au stade de l’analyse du code sans fournir de résultats sont corrigées.

* La carte Environnement n’affichait pas de manière cohérente la variable **Ajouter** bouton .

## Outils de refactorisation du code {#code-refactoring-tools}

### Nouveautés d’[!DNL Code Refactoring Tools]  {#what-is-new-crt}

* Publication de la nouvelle version du plug-in AIO-CLI. La dernière version de ce plug-in inclut des correctifs pour le convertisseur du Dispatcher AEM et Repository Modernizer et prend également en charge un nouvel utilitaire : le convertisseur d’index. Voir [Expérience unifiée](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/refactoring-tools/unified-experience.html#benefits) où vous pouvez en savoir plus sur ce module externe.

* Le convertisseur d’index est un utilitaire qui permet de transformer les définitions d’index Oak personnalisées d’un client en définitions d’index Oak compatibles as a Cloud Service AEM. Voir [Convertisseur d’index](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter) pour plus d’informations.

* Nouvelle fonctionnalité ajoutée à [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) qui crée un package distinct `ui.config` contenant toutes les configurations OSGi.

### Correctifs {#crt-bug-fixes}

* Plusieurs correctifs ont été apportés aux outils Dispatcher Converter et Repository Modernizer d’AEM. Voir [Convertisseur du Dispatcher AEM](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter) et [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer).

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu version v1.1.20 est le 8 janvier 2021.

### Nouveautés d’[!DNL Content Transfer Tool]  {#what-is-new-ctt}

* Les utilisateurs peuvent désormais savoir si leur jeton d’accès a expiré en pointant vers l’icône de statut de l’interface utilisateur de l’outil de transfert de contenu (CTT). Ils sont également informés dans l’interface utilisateur des détails du jeu de migration qu’ils ne peuvent pas se connecter à leur instance de Cloud Service.

### Correctifs {#ctt-bug-fixes}

* Le statut de l’interface utilisateur de l’outil de transfert de contenu (CTT) pour un jeu de migration n’était pas conservé et modifié après une période d’inactivité. Ce problème a été résolu.
* L’option d’affichage des journaux était désactivée si les journaux n’étaient pas disponibles. Ce problème a été corrigé et des messages ont été ajoutés pour informer les utilisateurs de l’absence de logs.
* L’état de l’interface utilisateur de l’outil de transfert de contenu *ÉCHEC* lorsque l’utilisateur a arrêté une ingestion. Ce problème a été corrigé pour afficher à la place *STOPPED*.
