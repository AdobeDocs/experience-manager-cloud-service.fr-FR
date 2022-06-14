---
title: Notes de mise à jour de la version 2021.8.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour de la version 2021.8.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 8b041934-1c4a-4670-9b03-d38f683b99e5
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '1032'
ht-degree: 100%

---

# Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour générales de la version actuelle (la plus récente) d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes ; par exemple, celles de 2020, 2021 et ainsi de suite.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de la version actuelle de [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2021.8.0) est le 26 août 2021.
La version suivante (2021.9.0) date du 6 octobre 2021.

## Vidéo de publication {#release-video}

Regardez la vidéo [Aperçu de la version d’août 2021](https://video.tv.adobe.com/v/336277) pour un résumé des fonctionnalités ajoutées.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de [!DNL Assets] {#assets-features}

* Lors du partage de ressources numériques dans un lien, les utilisateurs peuvent copier immédiatement l’URL dans le presse-papiers. Cette amélioration vous permet de partager des ressources plus rapidement et plus facilement. Cette fonctionnalité permet un partage de ressources plus rapide et pratique.

   ![Option Copier l’URL lors du partage d’une ressource dans un lien](/help/assets/assets/link-share-copy-URL-option.png)
   *Image : lors du partage d’une ressource dans un lien, vous pouvez désormais copier l’URL pour la partager séparément.*

* Lorsque vous chargez des fichiers TXT, les microservices de ressources génèrent automatiquement une miniature. La miniature PNG est un rendu de fichier TXT qui aide les utilisateurs à identifier le contenu ou les fichiers dans une certaine mesure, sans ouvrir les fichiers. Cette fonctionnalité ne nécessite aucune configuration et fonctionne par défaut.

   ![Un rendu d’un fichier TXT est automatiquement généré par [!DNL Assets] au format PNG](/help/assets/assets/thumbnail-rendition-txt-file.png)
   *Image : un rendu d’un fichier TXT est automatiquement généré pour vous aider à identifier le fichier sans l’ouvrir.*

### Nouvelle fonctionnalité dans le canal de version préliminaire [!DNL Assets] {#assets-prerelease-features}

* Les utilisateurs peuvent désormais trier en vue Colonne et Carte les ressources affichées dans les résultats de recherche. Le tri fonctionne sur les colonnes Nom, Créé, Modifié et Aucune.

   ![Trier les résultats de recherche dans [!DNL Assets] dans les vues Colonne et Carte](/help/assets/assets/sort-searched-assets.png)
   *Image : trier les résultats de recherche dans [!DNL Assets] dans les vues Colonne et Carte.*

### Correctifs d’[!DNL Assets] {#assets-bugs-fixed}

* Lorsqu’un membre du groupe de contributeurs accède à la console [!DNL Assets], un code `POST` supplémentaire est généré pour tenter de créer une collection. Cette requête n’est pas obligatoire, elle échoue en raison de problèmes d’autorisation et crée de nombreuses erreurs dans les journaux. (CQ-4328856)
* Lorsque les utilisateurs affichent une ressource et sélectionnent la [!UICONTROL Chronologie] dans le menu contextuel du panneau de gauche, une erreur s’affiche. Dans les journaux, de nombreux avertissements sont consignés en raison d’une requête erronée. (CQ-4328919)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouveautés de [!DNL Forms] {#what-is-new-forms}

* Le service de conversion automatique des formulaires peut [convertir des formulaires PDF en italien et en portugais](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=fr#language-specific-meta-model) dans les formulaires adaptatifs.

* **Document d’enregistrement basé sur Acrobat** : AEM Forms as a Cloud Service prend en charge l’utilisation d’[Adobe Acrobat Form PDF (Acrobat PDF)](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/generate-document-of-record-for-non-xfa-based-adaptive-forms.html?lang=fr) comme modèle de document d’enregistrement en plus des modèles de formulaire basés sur XFA.

* **Connecteur de magasin de données Microsoft Azure** : vous pouvez désormais [connecter le modèle de données de formulaire au stockage Microsoft Azure](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/use-form-data-model/configure-azure-storage.html?lang=fr). Ceci vous permet de récupérer et de stocker des données de formulaire adaptatif dans le stockage Microsoft Azure en tant que BLOB.

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Forms] {#prerelease-features-forms}

* **Utilisation des rôles Adobe Sign dans un formulaire adaptatif** : les niveaux de service professionnel et entreprise d’Adobe Sign offrent la possibilité d’étendre les rôles des destinataires du contrat au-delà du simple signataire, afin de mieux répondre aux exigences de leur workflow. Vous pouvez désormais permettre à chaque destinataire de contrat de configurer son rôle dans un formulaire adaptatif, avec le rôle Signer par défaut.

* **Analytics pour les formulaires adaptatifs** : vous pouvez désormais capturer et suivre le comportement de l’utilisateur final via Adobe Analytics pour les formulaires adaptatifs afin de rassembler les informations sur l’utilisateur final. Il permet de prendre des décisions éclairées basées sur les données afin d’améliorer l’expérience de l’utilisateur final.

* **Connectez facilement AEM Forms à Microsoft Dynamics et à Salesforce.com** : le service fournit des modèles de données et de configuration de source de données prêts à l’emploi pour Microsoft Dynamics et Salesforce.com, ce qui permet aux développeurs de configurer plus rapidement et plus facilement Microsoft Dynamics et Salesforce.com en tant que sources de données pour un formulaire adaptatif.

## Module complémentaire CIF {#cloud-services-cif}

### Nouveautés {#what-is-new-cif}

* Nouvelle interface utilisateur du sélecteur de catégorie pour une meilleure expérience utilisateur, efficacité améliorée et meilleure prise en charge pour les catalogues complexes de produits

   ![Nouveau sélecteur de catégorie](/help/assets/CIF/category-picker.png)

* Meilleure prise en charge d’A11Y pour les composants principaux CIF

## Cloud Manager {#cloud-manager}

Cette section présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.8.0 et 2021.7.0.

## Date de publication {#release-date-cm-aug}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.8.0 est le 12 août 2021.
La prochaine version est prévue pour le 9 septembre 2021.

### Nouveautés {#what-is-new-aug}

* Les clients Cloud Service peuvent désormais afficher les rapports de Contrat de niveau de service (SLA) dans Cloud Manager. Cette fonctionnalité sera disponible progressivement au cours des prochains mois.
Consultez [Rapport de SLA](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/sla-reporting.html?lang=fr) pour en savoir plus.

* Le type et la gravité de l’IndexType et des règles de qualité de `IndexDamAssetLucene` ont été modifiés. Ils sont maintenant tous deux répertoriés en tant que niveau de *sévérité* « bogues de blocage ».

* De nouvelles règles de qualité d’index Oak ont été introduites pour couvrir les configurations asynchrones et tika.

* Augmentez le nombre maximal de certificats SSL par programme à 50.

* Fonctionnalité de libre-service pour permettre aux utilisateurs de créer et de gérer plusieurs référentiels via l’interface utilisateur de Cloud Manager.

* SonarQube lisait inutilement les données de l’historique Git. Avec les bases de code volumineuses, cela pouvait entraîner une pénalité de performance de build inutile.

* Une API est désormais disponible pour invalider le cache de dépendance Maven par pipeline.

* L’archétype de projet AEM utilisé par Cloud Manager a été mis à jour à la version 29.

### Correctifs {#bug-fixes-aug}

* Le statut Mise à jour disponible ne doit pas s’afficher lorsque la dernière version est inférieure à la version présente.

* L’intégration initiale échouait pour les nouvelles organisations dont les noms étaient très longs.

* Parfois, lorsqu’un pipeline est déclenché deux fois pour une raison quelconque, l’une ou l’autre des exécutions échoue avec l’erreur *Impossible de mettre à jour l’état d’exécution du pipeline*.

## Outil de transfert de contenu {#content-transfer-tool}

### Date de publication {#release-date-ctt-latest}

La date de publication de l’outil de transfert de contenu version v1.5.6 est le 11 août 2021.

### Correctifs {#bug-fixes-ctt}

* Dans certains cas, certains utilisateurs n’ont pas été migrés vers l’instance cible. Pour obtenir ce correctif, la version v1.5.6 de CTT est requise avec aem-ethos-tools version 1.2.354 ou une version ultérieure dans l’instance cible d’AEM as a Cloud Service.

* Le bouton **Arrêter l’ingestion** était désactivé lors de l’ingestion vers l’instance de publication. Cela n’est pas nécessaire, car il n’existe aucune étape de restauration de mongo pendant l’ingestion de publication.

* CTT ne nettoyait pas le répertoire `/tmp` après une extraction réussie. Cette erreur entraînait parfois des problèmes d’espace disque.
