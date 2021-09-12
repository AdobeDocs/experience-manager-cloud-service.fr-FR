---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: 534fd193181fe22392fb598625d3a018a4a09e69
workflow-type: tm+mt
source-wordcount: '1628'
ht-degree: 24%

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

<!-- * Automated Forms Conversion service can [convert PDF Forms in Italian and Portuguese language](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?#language-specific-meta-model) to Adaptive Forms. -->

* AEM projet Archetype pour Forms as a Cloud Service comprend désormais [des modèles de données de formulaire pour Microsoft Dynamics et Salesforce.com](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/setup-environment/setup-local-development-environment.html?#forms-cloud-service-local-development-environment).

* **Document d’enregistrement** basé sur Acrobat : AEM Forms as a Cloud Service prend en charge l’utilisation d’ [Adobe Acrobat Form PDF (Acrobat PDF)](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/generate-document-of-record-for-non-xfa-based-adaptive-forms.html?lang=fr)  comme modèle de document d’enregistrement en plus des modèles de formulaire basés sur XFA.

* **Connecteur de magasin de données Microsoft Azure** : vous pouvez désormais [connecter le modèle de données de formulaire au stockage Microsoft Azure](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/use-form-data-model/configure-azure-storage.html?lang=fr). Il vous permet de récupérer et de stocker des données de formulaire adaptatif dans le stockage Microsoft Azure en tant qu’objet BLOB.

### Fonction bêta de [!DNL Forms] {#aug-what-is-new-forms-prerelease}

* **Unified Storage Connector :** utilisez Unified Storage Connector pour externaliser les données en cours de traitement dans les référentiels gérés par le client. Par exemple, vous pouvez
   * Activez la fonctionnalité d’enregistrement et de reprise de Forms Portal et stockez les brouillons de formulaires adaptatifs dans un référentiel de données géré par le client.
   * Stocker les données AEM processus en cours (AEM données des variables de processus) qui contiennent des données personnelles sensibles (SPD) dans un référentiel géré par le client.

* **[!DNL AEM Forms as a Cloud Service - Communications]** : les [API Communications](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/aem-forms-cloud-service-communications.html?lang=fr) vous permet de combiner des modèles XDP et des données XML pour générer des documents d’impression dans différents formats. Le service vous permet de générer des documents en mode synchrone. Les API permettent de créer des applications grâce auxquelles vous pouvez accomplir les actions suivantes :
   * Générer des documents en complétant des fichiers de modèle avec des données XML.
   * Générer des formulaires dans divers formats, y compris les flux d’impression PDF non interactifs.
   * Générer des fichiers PDF d’impression à partir d’un formulaire XFA au format PDF et d’un formulaire Adobe Acrobat.

Vous pouvez écrire à [!DNL formscsbeta@adobe.com] pour vous inscrire au programme bêta.

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Forms] {#prerelease-features-forms}

* **Utilisation des rôles Adobe Sign dans un formulaire** adaptatif : Les niveaux de service d’entreprise et d’entreprise d’Adobe Sign ont la possibilité d’étendre les rôles des destinataires du contrat, au-delà du simple signataire, afin de mieux répondre aux exigences de leur workflow. Vous pouvez désormais [permettre à chaque destinataire d’accord de configurer son rôle dans un formulaire adaptatif](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/use-adobe-sign/working-with-adobe-sign.html?#addsignerstoanadaptiveform), avec le rôle par défaut Signer.

* **Analytics pour le Forms** adaptatif : Vous pouvez désormais capturer et suivre le comportement de l’utilisateur final via Adobe Analytics pour Forms adaptatif afin de rassembler les informations sur l’utilisateur final. Il permet de prendre des décisions éclairées basées sur les données afin d’améliorer l’expérience de l’utilisateur final.

* **Connectez facilement AEM Forms à Microsoft Dynamics et Salesforce.com** : Le service fournit des modèles de données et de configuration de source de données prêts à l’emploi pour Microsoft Dynamics et Salesforce.com, ce qui rend  [plus rapide et plus facile pour les développeurs de configurer Microsoft Dynamics et Salesforce.com comme sources de données pour un formulaire](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/use-form-data-model/configure-msdynamics-salesforce.html) adaptatif.

## [!DNL Experience Manager Screens] as a  [!DNL Cloud Service] {#screens}

### Nouveautés {#what-is-new-screens}

* Screens en tant que Cloud Service prend désormais en charge la surveillance de lecture de base. Le lecteur signale désormais diverses mesures de lecture pour chaque ping (30 secondes par défaut). En fonction des mesures, il permet de détecter différents cas de périphérie (expérience bloquée, écran vide, problème de planification, etc.). Cette fonctionnalité permet à l’équipe de surveiller à distance si un lecteur lit correctement du contenu, améliore la réactivité aux écrans vierges ou aux expériences rompues sur le champ et réduit le risque d’afficher une expérience rompue à l’utilisateur final.
Voir [Surveillance de lecture de base](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/manage-player-registration/installing-screens-cloud-player.html?lang=en#playback-monitoring) pour plus d’informations.

* Prise en charge des miniatures pour les vidéos dans Screens en tant que Cloud Service. Un auteur de contenu peut définir une miniature pour les vidéos afin que l’image puisse être utilisée comme espace réservé et tester correctement la lecture et le ciblage du contenu, pendant que la vidéo réelle est en cours de finalisation par l’équipe appropriée. L’image peut également être utilisée, au cas où la lecture de la vidéo échouerait.
Pour plus d’informations, voir [Prise en charge des miniatures pour les vidéos](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/core-product-features/thumbnail-support-videos.html) .

### Correctifs {#bug-fixes-screens}

* Le lecteur n’a pas pu afficher le contenu de la page incorporée et ce problème a été corrigé.

* Une fois la connexion établie, la navigation vers la page par défaut (canaux) a abouti à une page d’erreur interne du serveur.

* Les entrées de balise associées n’ont pas été supprimées lors de la suppression des listes de lecture.


## Module complémentaire CIF {#cloud-services-cif}

### Nouveautés {#what-is-new-cif}

* Nouvelle interface utilisateur du sélecteur de catégorie pour une meilleure expérience utilisateur, une efficacité accrue et une meilleure prise en charge d’un catalogue de produits complexe

   ![Nouveau sélecteur de catégorie](/help/assets/CIF/category-picker.png)

* Meilleure prise en charge d’A11Y pour les composants principaux CIF

## Cloud Manager  {#cloud-manager}

Cette section présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.9.0 et 2021.8.0.

## Date de publication {#release-date-cm-sept}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.9.0 est le 9 septembre 2021.
La prochaine version est prévue pour le 7 octobre 2021.

### Nouveautés {#what-is-new-cm-sept}

* L’archétype de projet AEM utilisé par Cloud Manager a été mis à jour à la version 30.

* Les cartes de programme sur la page d’entrée de Cloud Manager et l’expérience associée ont été actualisées.

* Le journal des étapes de qualité du code comprend désormais des informations de journalisation en mode verbeux sur le processus d’analyse OakPal.

* Les options de menu de la page Activité comprennent désormais une option **Télécharger le journal** pour les exécutions du Générateur de code terminées. Si vous sélectionnez cette option, le journal de l’étape de création sera téléchargé.

* Cliquez directement sur la carte Programme pour accéder à la page Aperçu de Cloud Manager .


### Correctifs {#bug-fixes-sept}

* L’utilisateur voit désormais un message plus compréhensible lorsqu’il tente d’ajouter une nouvelle Liste autorisée IP dans un programme qui a atteint le nombre maximal autorisé de Listes autorisées IP configurables.

* Une URL incorrecte a été copiée lors de la sélection de l’option de menu Copier l’URL dans l’écran Référentiels .

## Date de publication {#release-date-cm-aug}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.8.0 est le 12 août 2021.

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

* Parfois, lorsqu’un pipeline est déclenché deux fois pour une raison quelconque, l’une ou l’autre des exécutions échoue avec l’erreur *Impossible de mettre à jour l’état d’exécution du pipeline*.

## Outil de transfert de contenu {#content-transfer-tool}

### Date de publication {#release-date-ctt-latest}

La date de publication de l’outil de transfert de contenu v1.5.6 est le 11 août 2021.

### Correctifs {#bug-fixes-ctt}

* Dans certains cas, tous les utilisateurs n’ont pas été migrés vers l’instance cible. Pour obtenir ce correctif, CTT v1.5.6 est requis avec aem-ethos-tools 1.2.354 ou version ultérieure sur l’AEM cible en tant qu’instance de Cloud Service.

* Le bouton **Arrêter l’ingestion** était désactivé lors de l’ingestion vers l’instance de publication. Cela n’est pas nécessaire, car il n’existe aucune étape de restauration de mongo pendant l’ingestion de publication.

* CTT n’a pas nettoyé le répertoire `/tmp` après une extraction réussie. Cela entraînait parfois des problèmes d’espace disque.

## Analyseur des bonnes pratiques {#best-practices-analyzer}

### Date de publication {#release-date-bpa-latest}

La date de publication de la version 2.1.18 de l’analyseur des bonnes pratiques est le 2 septembre 2021.

### Nouveautés {#what-is-new}

* Possibilité de détecter et de générer des rapports sur le nombre total de noeuds.

* Possibilité de détecter et de générer des rapports sur le type et la taille du magasin de noeuds.

### Correctifs {#bug-fixes-bpa}

* BPA détectait faussement la présence de Commerce Integration Framework.

