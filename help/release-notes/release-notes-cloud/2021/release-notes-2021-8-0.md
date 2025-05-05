---
title: Notes de mise à jour de la version 2021.8.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour de la version 2021.8.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 8b041934-1c4a-4670-9b03-d38f683b99e5
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1011'
ht-degree: 58%

---

# Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour générales de la version actuelle (la plus récente) d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes. Par exemple, pour les années 2020 et 2021.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de la version actuelle de [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2021.8.0) est le 26 août 2021.
La version suivante (2021.9.0) date du 6 octobre 2021.

## Vidéo de publication {#release-video}

Regardez la vidéo [Aperçu de la version d’août 2021](https://video.tv.adobe.com/v/336277) pour un résumé des fonctionnalités ajoutées.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de [!DNL Assets] {#assets-features}

* Lors du partage de ressources numériques sous la forme d’un lien, l’utilisateur peut copier immédiatement l’URL dans le Presse-papiers. Cette amélioration vous permet de partager des ressources plus rapidement et plus facilement. Cette fonctionnalité permet un partage de ressources plus rapide et pratique.

  ![Option Copier l’URL lors du partage d’une ressource dans un lien](/help/assets/assets/link-share-copy-URL-option.png)
  *Image : lors du partage d’une ressource dans un lien, vous pouvez désormais copier l’URL pour la partager séparément.*

* Lorsque vous chargez des fichiers TXT, les microservices de ressources génèrent automatiquement une miniature. La miniature PNG est un rendu d’un fichier TXT qui permet aux utilisateurs d’identifier le contenu ou les fichiers dans une certaine mesure, sans ouvrir les fichiers. Cette fonctionnalité ne nécessite aucune configuration et fonctionne par défaut.

  ![Un rendu d’un fichier TXT est automatiquement généré par [!DNL Assets] au format PNG](/help/assets/assets/thumbnail-rendition-txt-file.png)
  *Image : un rendu d’un fichier TXT est automatiquement généré pour vous aider à identifier le fichier sans l’ouvrir.*

### Nouvelle fonctionnalité dans le canal de version préliminaire [!DNL Assets] {#assets-prerelease-features}

* Les utilisateurs peuvent désormais trier en vue Colonne et Carte les ressources affichées dans les résultats de recherche. Le tri fonctionne sur les colonnes Nom, Créé, Modifié et Aucune.

  ![Trier les résultats de recherche dans [!DNL Assets] dans les vues Colonne et Carte](/help/assets/assets/sort-searched-assets.png)
  *Image : trier les résultats de recherche dans [!DNL Assets] dans les vues Colonne et Carte.*

### Correctifs d’[!DNL Assets] {#assets-bugs-fixed}

* Lorsqu’un membre du groupe de contributeurs accède à la console [!DNL Assets], une requête `POST` supplémentaire est générée pour créer une collection. Cette requête n’est pas obligatoire ; elle échoue en raison de problèmes d’autorisation et crée de nombreuses erreurs dans les journaux. (CQ-4328856)
* Lorsque les utilisateurs affichent une ressource et sélectionnent la [!UICONTROL Chronologie] dans le menu contextuel du panneau de gauche, une erreur s’affiche. Dans les journaux, de nombreux avertissements sont consignés en raison d’une requête erronée. (CQ-4328919)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouveautés de [!DNL Forms] {#what-is-new-forms}

* Le service de conversion automatique des formulaires peut [convertir des formulaires PDF en italien et en portugais](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=fr#language-specific-meta-model) dans les formulaires adaptatifs.

* **Document d’enregistrement basé sur Acrobat** : AEM Forms as a Cloud Service prend en charge l’utilisation d’[Adobe Acrobat Form PDF (Acrobat PDF)](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/generate-document-of-record-for-non-xfa-based-adaptive-forms) comme modèle de document d’enregistrement en plus des modèles de formulaire basés sur XFA.

* **Connecteur Microsoft® Azure Data Store** : vous pouvez désormais [connecter le modèle de données de formulaire à Microsoft® Azure Storage](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-azure-storage.html?lang=fr). Il vous permet de récupérer et de stocker des données de formulaire adaptatif dans Microsoft® Azure Storage as a BLOB.

### Nouvelles fonctionnalités disponibles dans le canal de préversion [!DNL Forms] {#prerelease-features-forms}

* **Utilisation des rôles Adobe Sign dans un formulaire adaptatif** - Adobe Sign pour les niveaux de service d’entreprise et d’entreprise peut éventuellement étendre les rôles des destinataires du contrat, au-delà du simple signataire, afin de mieux répondre aux exigences de leur workflow. Vous pouvez désormais permettre à chaque destinataire de l’accord de configurer son rôle dans un formulaire adaptatif, avec le signataire comme rôle par défaut.

* **Analytics for Adaptive Forms** - Vous pouvez désormais capturer et suivre le comportement de l’utilisateur final par le biais d’Adobe Analytics pour Adaptive Forms afin de rassembler les informations sur l’utilisateur final. Il permet de prendre des décisions éclairées basées sur les données afin d’améliorer l’expérience de l’utilisateur final.

* **Connectez facilement AEM Forms à Microsoft® Dynamics et Salesforce.com** - Le service fournit la configuration de source de données et les modèles de données prêts à l’emploi pour Microsoft® Dynamics et Salesforce.com. Cela permet aux développeurs de configurer plus rapidement et plus facilement Microsoft® Dynamics et Salesforce.com comme sources de données pour un formulaire adaptatif.

## Module complémentaire CIF {#cloud-services-cif}

### Nouveautés {#what-is-new-cif}

* Nouvelle interface utilisateur du sélecteur de catégorie pour une meilleure expérience client, une efficacité améliorée et une meilleure prise en charge du catalogue de produits complexe

  ![Nouveau sélecteur de catégorie](/help/assets/CIF/category-picker.png)

* Meilleure prise en charge d’A11Y pour les composants principaux CIF

## Cloud Manager {#cloud-manager}

Cette section présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.8.0 et 2021.7.0.

## Date de publication {#release-date-cm-aug}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.8.0 est le 12 août 2021.
La prochaine version est prévue pour le 9 septembre 2021.

### Nouveautés {#what-is-new-aug}

* Les clients Cloud Service peuvent désormais afficher les rapports de Contrat de niveau de service (SLA) dans Cloud Manager. Elle sera disponible progressivement au cours des prochains mois.
Consultez [Rapport SLA](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/sla-reporting.html?lang=fr).

* Le type et la gravité d’IndexType et des règles de qualité de `IndexDamAssetLucene` ont été modifiés. Il s’agit désormais des deux bogues de Blocker *gravité*.

* De nouvelles règles de qualité d’index Oak ont été introduites pour couvrir les configurations asynchrones et Tika.

* Augmentez le nombre maximal de certificats SSL par programme à 50.

* Fonctionnalité de libre-service permettant aux utilisateurs de créer et gérer plusieurs référentiels au moyen de l’interface utilisateur de Cloud Manager.

* SonarQube lisait inutilement les données de l’historique Git. Avec les bases de code volumineuses, cela pouvait entraîner une pénalité de performance de build inutile.

* Une API est désormais disponible pour invalider le cache de dépendance Maven par pipeline.

* L’archétype de projet AEM utilisé par Cloud Manager a été mis à jour à la version 29.

### Correctifs {#bug-fixes-aug}

* Mise à jour L’état Disponible ne doit pas s’afficher lorsque la dernière version est inférieure à la version actuelle.

* L’intégration initiale échouait pour les nouvelles organisations dont les noms étaient longs.

* Parfois, lorsqu’un pipeline est déclenché deux fois pour une raison quelconque, l’une des exécutions échoue avec une erreur *`cannot update pipeline execution status`*.

## Outil de transfert de contenu {#content-transfer-tool}

### Date de publication {#release-date-ctt-latest}

La date de publication de l’outil de transfert de contenu version v1.5.6 est le 11 août 2021.

### Correctifs {#bug-fixes-ctt}

* Parfois, tous les utilisateurs n’étaient pas migrés vers l’instance cible. Pour obtenir ce correctif, CTT v1.5.6 est requis avec aem-ethos-tools 1.2.354 ou version ultérieure sur l’instance AEM as a Cloud Service cible.

* Le bouton **Arrêter l’ingestion** était désactivé lors de l’ingestion vers l’instance de publication. Cela n’est pas nécessaire, car il n’existe aucune étape de restauration de mongo pendant l’ingestion de publication.

* CTT ne nettoyait pas le répertoire `/tmp` après une extraction réussie. Cette erreur entraînait parfois des problèmes d’espace disque.
