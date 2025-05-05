---
title: Notes de mise à jour de la version 2022.10.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la version 2022.10.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 8fce7c50-f322-4bcf-bd76-390faedfd5b7
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '833'
ht-degree: 78%

---

# Notes de mise à jour de la version 2022.10.0 d’[!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante décrit les notes de mise à jour des fonctionnalités de la version 2022.10.0 de l’as a Cloud Service [!DNL Experience Manager].

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes ; par exemple, celles de 2020, 2021 et ainsi de suite.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication mensuelle de la version actuelle (2022.10.0) d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le 10 novembre 2022. La prochaine version mensuelle (2023.1.0) est prévue pour le vendredi 9 février 2023.

## Vidéo de mise à jour {#release-video}

Regardez la vidéo de présentation de la version d’octobre 2022 pour un résumé des fonctionnalités ajoutées dans la version 2022.10.0 :

>[!VIDEO](https://video.tv.adobe.com/v/3409801/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}


### Nouvelles fonctionnalités de [!DNL Sites] {#sites-features}

* L’onglet [ Personalization pour les fragments d’expérience](/help/sites-cloud/authoring/fragments/content-fragments.md#personalization-experience-fragment) permet de définir des fonctionnalités pour l’éditeur de fragments d’expérience et de créer des fragments d’expérience imbriqués dans lesquels des variations d’en-tête et de pied de page peuvent être créées pour plusieurs segments. Avant le lancement de cette fonctionnalité, la personnalisation proposée par AEM n’était disponible que pour les pages du site et non pour les fragments d’expérience

* La [Console Fragments de contenu](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console) permet désormais aux utilisateurs et utilisatrices de gérer efficacement les fragments de contenu traduits. En un seul clic, vous pouvez désormais afficher toutes les copies de langue. Les utilisateurs et utilisatrices peuvent également filtrer la vue du tableau en fonction de la langue de leur choix.

![Langues de fragments de contenu](/help/release-notes/assets/cfconsole-languages.png)

* Réduisez davantage le temps de chargement des pages pour les visiteurs et visiteuses en optimisant les paramètres de tailles d’images dans les modèles. Pour plus d’informations sur le composant d’image, consultez la page [Composant WCM principal](https://github.com/adobe/aem-core-wcm-components)

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de [!DNL Assets] {#assets-features}

* Experience Manager Assets vous permet désormais de charger des documents dans d’autres types de format pris en charge et de les prévisualiser à l’aide de la visionneuse de Documents Cloud incluse [&#128279;](/help/assets/manage-pdf-documents.md).  Les types de format pris en charge sont les suivants : TXT, RTF, DOC, DOCX, PPT, PPTX, XLS et XLSX.

  ![Rendu PDF pour d’autres formats](/help/release-notes/assets/multi-page-other-formats.png)


### Nouvelles fonctionnalités de la préversion d’[!DNL Assets] {#prerelease-features-assets}

* Experience Manager Assets utilise désormais un framework d’intelligence artificielle amélioré pour les balises intelligentes d’image. Celui-ci améliore la pertinence et la précision des balises intelligentes disponibles pour toutes les ressources d’image lors de l’ingestion. En outre, les informations d’orientation sont renseignées dans `cq:tags`, ce qui permet d’obtenir de meilleurs résultats de recherche à l’aide du filtre d’orientation.

  Si vous souhaitez participer à la version Bêta, [remplissez ce formulaire](https://forms.office.com/pages/responsepage.aspx?id=Wht7-jR7h0OUrtLBeN7O4epXZrTVKKdJkUiHeolccf9UNEwyNEpHVEFaODdBNFZQSlFDREZQOVRRTy4u) avant le 14 novembre.

* Experience Manager Assets [prend désormais en charge le jeton SAS](/help/assets/add-assets.md#asset-bulk-ingestor), en plus de la clé d’accès, pour l’authentification lors de la connexion à la source de données Azure Blob Storage, à des fins d’ingestion de ressources à l’aide de l’outil d’importation en bloc.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Forms] {#prerelease-features-forms}

* **Éditeur de modèles de Forms adaptatif** : l’éditeur de modèles vous permet de prédéfinir la structure de base et l’aspect de Forms adaptatif d’une organisation. Dans cette nouvelle version, l’éditeur de modèles bénéficie des améliorations suivantes :
   * **[Modèle de données de formulaire dans l’éditeur de modèles](/help/forms/creating-adaptive-form.md#edit-form-model-properties-of-an-adaptive-form-edit-form-model)** : vous pouvez associer un schéma de modèle de données de formulaire à un modèle de formulaire adaptatif dans l’éditeur de modèles. Le temps nécessaire à la création d’un formulaire adaptatif est ainsi réduit. Cette option est également ajoutée à l’éditeur de formulaires adaptatifs pour permettre aux utilisateurs et utilisatrices de sélectionner ou de modifier le modèle de données de formulaire pour les formulaires existants.
   * **[Document d’enregistrement dans l’éditeur de modèles](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#document-of-record-support-in-adaptive-form-editor-dor-support-in-adaptiveform)** : vous pouvez désormais standardiser la génération d’un document d’enregistrement pour tous les formulaires créés à l’aide d’un modèle. Cela permet de renforcer la standardisation et la conformité aux exigences de l’organisation.

* **[Lancement de l’assistant de formulaires adaptatifs à partir d’une page AEM Sites](/help/forms/embed-adaptive-form-aem-sites.md)** : la page AEM Sites offre une prise en charge étendue des formulaires adaptatifs. Vous pouvez désormais créer un formulaire adaptatif ou incorporer un formulaire adaptatif existant tout en restant sur la page AEM Sites.
* **[Modification de l’alignement de l’affichage des cases à cocher et du bouton radio dans le document d’enregistrement](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#customize-the-branding-information-in-document-of-record-customize-the-branding-information-in-document-of-record)** : vous pouvez désormais définir l’alignement souhaité (horizontal, vertical, identique aux formulaires adaptatifs) pour la case à cocher et le bouton radio du document d’enregistrement. Cette option permet de déterminer le positionnement des cases à cocher et du bouton radio dans le document d’enregistrement.

## Module complémentaire CIF {#cloud-services-cif}

### Nouveautés {#what-is-new-cif}

* Les auteurs peuvent enrichir dynamiquement des listes de produits avec des fragments d’expérience (par exemple : placement d’une bannière entre des listes de produits).
* Le composant Liste prend désormais en charge les pages de produits/catégories associées afin de les afficher de manière dynamique.
* Ajout de la prise en charge des composants Peregrine 12.5.
* Ajout de la prise en charge du chargement des prix côté client dans le teaser du produit et le carrousel.

## [!DNL Experience Manager as a Cloud Service] Foundation {#foundation}

### Nouveautés {#what-is-new-foundation}

* AEM as a Cloud Service (service de création) est désormais intégré à Unified Shell pour améliorer l’expérience utilisateur et l’unifier avec toutes les autres applications Experience Cloud. Pour plus d’informations, voir AEM en tant que [Cloud Service sur Shell unifié](/help/overview/aem-cloud-service-on-unified-shell.md) .

* Comme mentionné précédemment dans les notes de mise à jour, l’utilisation de l’écran d’administration de l’agent de réplication ou de l’API de réplication pour distribuer des modules de contenu de plus de 10 Mo (noeuds avec des propriétés, sans inclure les fichiers binaires) est désormais obsolète et appliquée. Voir [Gérer la publication](/help/operations/replication.md#manage-publication) ou le [workflow Arborescence de contenu Publish](/help/operations/replication.md#publish-content-tree-workflow) pour connaître les approches suggérées pour répliquer ces modules de contenu volumineux.

* La configuration de Dispatcher référence désormais un fichier qui répertorie les paramètres de requête de campagne marketing courants. Les clients peuvent choisir de supprimer les commentaires des paramètres souhaités afin d’améliorer la mise en cache. Pour plus d’informations, voir [Paramètres de campagne marketing](/help/implementing/dispatcher/caching.md#marketing-parameters) .

## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici](/help/implementing/cloud-manager/release-notes/current.md).

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [ici](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
