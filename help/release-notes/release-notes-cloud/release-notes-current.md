---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: a3e884347e87358d7e0ab8d0fe9d416f15b184ab
workflow-type: tm+mt
source-wordcount: '1030'
ht-degree: 27%

---


# Notes de mise à jour actuelles pour[!DNL Adobe Experience Manager]as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour générales de la version actuelle (la plus récente) d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes. par exemple, pour ceux de 2020, 2021, etc.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de la version actuelle de [!DNL Adobe Experience Manager] en tant que [!DNL Cloud Service] (2021.8.0) est le 26 août 2021.
La version suivante (2021.9.0) date du 30 septembre 2021.

## Vidéo de publication {#release-video}

Regardez la vidéo [Aperçu de la version d’août 2021](https://video.tv.adobe.com/v/336277) pour un résumé des fonctionnalités ajoutées.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de [!DNL Assets] {#assets-features}

* Lors du partage de ressources numériques sous la forme d’un lien, les utilisateurs peuvent copier immédiatement l’URL dans le Presse-papiers. Cette amélioration vous permet de partager vos ressources plus rapidement et plus facilement. Cette fonctionnalité permet un partage de ressources plus rapide et pratique.

   ![Option Copier l’URL lors du partage d’une ressource en tant que lien](/help/assets/assets/link-share-copy-URL-option.png)
   *Figure : Lors du partage d’une ressource en tant que lien, vous pouvez désormais copier l’URL pour la partager séparément.*

* Lorsque vous chargez des fichiers TXT, les microservices de ressources génèrent automatiquement une miniature. La miniature PNG est un rendu de fichier TXT qui aide les utilisateurs à identifier le contenu ou les fichiers dans une certaine mesure, sans ouvrir les fichiers. Cette fonctionnalité ne nécessite aucune configuration et fonctionne par défaut.

   ![Un rendu d’un fichier TXT est automatiquement généré par  [!DNL Assets] au format PNG.](/help/assets/assets/thumbnail-rendition-txt-file.png)
   *Figure : Un rendu d’un fichier TXT est automatiquement généré pour vous aider à identifier le fichier sans l’ouvrir.*

### Nouvelle fonctionnalité du canal de version préliminaire [!DNL Assets] {#assets-prerelease-features}

* Les utilisateurs peuvent désormais trier les ressources affichées dans les résultats de recherche en mode Colonnes et Carte. Le tri fonctionne sur les colonnes Nom, Créé, Modifié ou Aucun.

   ![Trier les résultats de la recherche  [!DNL Assets] en mode Colonnes et Carte](/help/assets/assets/sort-searched-assets.png)
   *Figure : Triez les résultats de la recherche  [!DNL Assets] en mode Colonnes et Carte.*

### Correctifs de [!DNL Assets] {#assets-bugs-fixed}

* Lorsqu’un membre du groupe de contributeurs accède à la console [!DNL Assets] , une requête `POST` supplémentaire est générée pour tenter de créer une collection. Cette requête n’est pas obligatoire, elle échoue en raison de problèmes d’autorisation et crée de nombreuses erreurs dans les journaux. (CQ-4328856)
* Lorsque les utilisateurs affichent une ressource et sélectionnent la [!UICONTROL Chronologie] dans le menu contextuel du panneau de gauche, une erreur s’affiche. Dans les journaux, de nombreux avertissements sont consignés en raison d’une mauvaise requête. (CQ-4328919)

## [!DNL Experience Manager Forms] as a  [!DNL Cloud Service] {#forms}

### Nouveautés de [!DNL Forms] {#what-is-new-forms}

* Le service Automated forms conversion peut [convertir les PDF forms en italien et portugais](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=fr#language-specific-meta-model) en Forms adaptatif.

* **Document d’enregistrement** basé sur Acrobat : AEM Forms as a Cloud Service prend en charge l’utilisation d’ [Adobe Acrobat Form PDF (Acrobat PDF)](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/generate-document-of-record-for-non-xfa-based-adaptive-forms.html?lang=fr)  comme modèle de document d’enregistrement en plus des modèles de formulaire basés sur XFA.

* **Connecteur de magasin de données Microsoft Azure** : vous pouvez désormais [connecter le modèle de données de formulaire au stockage Microsoft Azure](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/use-form-data-model/configure-azure-storage.html?lang=fr). Il vous permet de récupérer et de stocker des données de formulaire adaptatif dans le stockage Microsoft Azure en tant qu’objet BLOB.

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Forms] {#prerelease-features-forms}

* **Utilisation des rôles Adobe Sign dans un formulaire** adaptatif : Les niveaux de service d’entreprise et d’entreprise d’Adobe Sign ont la possibilité d’étendre les rôles des destinataires du contrat, au-delà du simple signataire, afin de mieux répondre aux exigences de leur workflow. Vous pouvez maintenant permettre à chaque destinataire d’accord de configurer son rôle dans un formulaire adaptatif, avec le signataire comme rôle par défaut.

* **Analytics pour le Forms** adaptatif : Vous pouvez désormais capturer et suivre le comportement de l’utilisateur final via Adobe Analytics pour Forms adaptatif afin de rassembler les informations sur l’utilisateur final. Il permet de prendre des décisions éclairées basées sur les données afin d’améliorer l’expérience de l’utilisateur final.

* **Connectez facilement AEM Forms à Microsoft Dynamics et Salesforce.com** : Le service fournit des modèles de données et de configuration de source de données prêts à l’emploi pour Microsoft Dynamics et Salesforce.com, ce qui permet aux développeurs de configurer plus rapidement et plus facilement Microsoft Dynamics et Salesforce.com comme sources de données pour un formulaire adaptatif.

## Module complémentaire CIF {#cloud-services-cif}

### Nouveautés {#what-is-new-cif}

* Nouvelle interface utilisateur du sélecteur de catégorie pour une meilleure expérience utilisateur, une efficacité accrue et une meilleure prise en charge d’un catalogue de produits complexe

   ![Nouveau sélecteur de catégorie](/help/assets/CIF/category-picker.png)

* Meilleure prise en charge d’A11Y pour les composants principaux CIF

## Cloud Manager  {#cloud-manager}

Cette section présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.8.0 et 2021.7.0.

## Date de publication {#release-date-cm-aug}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.8.0 est le 12 août 2021.
La prochaine version est prévue pour le 9 septembre 2021.

### Nouveautés {#what-is-new-aug}

* Les clients Cloud Service peuvent désormais afficher les rapports Contrat de niveau de service (SLA) dans Cloud Manager. Elle sera disponible progressivement au cours des prochains mois.
Voir [Rapports SLA](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/sla-reporting.html) pour en savoir plus.

* Le type et la gravité des règles de qualité IndexType et `IndexDamAssetLucene` ont été modifiés. Il s’agit désormais des deux bogues du bloqueur *serverity*.

* De nouvelles règles de qualité d’index Oak ont été introduites pour couvrir les configurations asynchrones et tika.

* Augmentez le nombre maximal de certificats SSL par programme à 50.

* Fonctionnalité de libre-service pour permettre aux utilisateurs de créer et de gérer plusieurs référentiels via l’interface utilisateur de Cloud Manager.

* SonarQube lisait inutilement les données de l’historique Git. Avec les bases de code volumineuses, cela pouvait entraîner une pénalité de performance de build inutile.

* Une API est désormais disponible pour invalider le cache de dépendance Maven par pipeline.

* L’archétype de projet AEM utilisé par Cloud Manager a été mis à jour à la version 29.

### Correctifs {#bug-fixes-aug}

* Le statut Mise à jour disponible ne doit pas s’afficher lorsque la dernière version est inférieure à la version présente.

* L’intégration initiale échouait pour les nouvelles organisations dont les noms étaient très longs.

* Parfois, lorsqu’un pipeline est déclenché deux fois pour une raison quelconque, l’une ou l’autre des occurrences échoue avec l’erreur *impossible de mettre à jour l’état d’exécution du pipeline*.

## Outil de transfert de contenu {#content-transfer-tool}

### Date de publication {#release-date-ctt-latest}

La date de publication de l’outil de transfert de contenu v1.5.6 est le 11 août 2021.

### Correctifs {#bug-fixes-ctt}

* Dans certains cas, tous les utilisateurs n’ont pas été migrés vers l’instance cible. Pour obtenir ce correctif, CTT v1.5.6 est requis avec aem-ethos-tools 1.2.354 ou version ultérieure sur l’AEM cible en tant qu’instance de Cloud Service.

* Le bouton **Arrêter l’ingestion** était désactivé lors de l’ingestion vers l’instance de publication. Cela n’est pas nécessaire, car il n’existe aucune étape de restauration de mongo pendant l’ingestion de publication.

* CTT n’a pas nettoyé le répertoire `/tmp` après une extraction réussie. Cela entraînait parfois des problèmes d’espace disque.

