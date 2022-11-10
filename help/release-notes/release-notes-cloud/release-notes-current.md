---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: b1715c819a6d049c88de8f0bc7061951bbcd5248
workflow-type: tm+mt
source-wordcount: '914'
ht-degree: 15%

---


# Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour générales de la version actuelle (la plus récente) d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>La disponibilité du SDK as a Cloud Service correspondant AEM est retardée, avec une cible du 11 novembre.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes ; par exemple, celles de 2020, 2021 et ainsi de suite.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

>[!CAUTION]
>
>**Période d’exclusion de la maintenance du vendredi et de Noël noir**
>
> Aucune maintenance automatique d’AEMaaCS ne sera exécutée pendant les périodes suivantes, commençant et se terminant à minuit (00:00) CET :
>
>* Lundi 21 novembre au lundi 5 décembre
>* Lundi 19 décembre au mardi 3 janvier
>
> Ces périodes couvrent le Noël, le Lundi cybernétique, Noël et le Nouvel An.

## Date de publication {#release-date}

La date de publication de [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] la version mensuelle actuelle (2022.10.0) date du 10 novembre 2022. La prochaine version mensuelle (2023.1.0) est prévue pour le 26 janvier 2022.

## Vidéo de mise à jour {#release-video}

Regardez la vidéo Présentation de la version d’octobre 2022 pour un résumé des fonctionnalités ajoutées à la version 2022.10.0 :

>[!VIDEO](https://video.tv.adobe.com/v/3409801/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}


### Nouvelles fonctionnalités de [!DNL Sites] {#sites-features}

* Le [Onglet Personnalisation pour les fragments d’expérience](/help/sites-cloud/authoring/fundamentals/experience-fragments.md#personalization-experience-fragment) permet des fonctionnalités de spécification de segmentation à l’éditeur de fragments d’expérience, ainsi que la possibilité de créer des fragments d’expérience imbriqués dans lesquels des variations d’en-têtes et de pieds de page peuvent être créées pour plusieurs segments. Avant le lancement de cette fonctionnalité, la personnalisation proposée par AEM n’est disponible que pour les pages du site, mais pas pour les fragments d’expérience.

* Le [Console de fragments de contenu](/help/sites-cloud/administering/content-fragments/content-fragments-console.md) permet désormais aux utilisateurs de gérer efficacement les fragments de contenu traduits. Un accès en 1 clic a été fourni pour afficher toutes les copies de langue. Les utilisateurs peuvent également filtrer l’affichage du tableau en fonction des paramètres régionaux qui les intéressent.

![Langues de fragments de contenu](/help/release-notes/assets/cfconsole-languages.png)

* Réduisez davantage le temps de chargement des pages pour les visiteurs en optimisant les paramètres de tailles d’image dans les modèles. Pour plus d’informations sur le composant d’image, voir [Composant WCM principal](https://github.com/adobe/aem-core-wcm-components)

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de [!DNL Assets] {#assets-features}

* Experience Manager Assets vous permet désormais de charger des documents dans d’autres types de format pris en charge et[ prévisualisez-les à l’aide de la visionneuse de Documents Cloud incluse.](/help/assets/manage-pdf-documents.md). Les types de format pris en charge sont TXT, RTF, DOC, DOCX, PPT, PPTX, XLS et XLSX.

   ![Rendu PDF pour d’autres formats](/help/release-notes/assets/multi-page-other-formats.png)


### Nouvelles fonctionnalités d’ [!DNL Assets] préliminaires {#prerelease-features-assets}

* Experience Manager Assets utilise désormais un framework d’intelligence artificielle amélioré pour les balises intelligentes d’image. Cette intelligence de contenu améliore la pertinence et la précision des balises intelligentes disponibles pour toutes les ressources d’image lors de l’ingestion. En outre, les informations d’orientation sont renseignées dans `cq:tags`, qui active de meilleurs résultats de recherche à l’aide du filtre d’orientation.

   Si vous souhaitez participer à la version bêta, [remplir ce formulaire](https://forms.office.com/pages/responsepage.aspx?id=Wht7-jR7h0OUrtLBeN7O4epXZrTVKKdJkUiHeolccf9UNEwyNEpHVEFaODdBNFZQSlFDREZQOVRRTy4u) le 14 novembre.

* Experience Manager Assets maintenant [prend en charge le jeton SAS](/help/assets/add-assets.md#asset-bulk-ingestor) en plus de la clé d’accès pour l’authentification lors de la connexion à la source de données Azure Blob Storage pour l’ingestion de ressources à l’aide de l’outil d’importation en bloc.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Forms] {#prerelease-features-forms}

* **Éditeur de modèle de Forms adaptatif**: L’éditeur de modèles vous permet de prédéfinir la structure de base et l’aspect de Forms adaptatif d’une organisation. Cette version apporte les améliorations suivantes à l’éditeur de modèles :
   * **[Modèle de données de formulaire dans l’éditeur de modèles](/help/forms/creating-adaptive-form.md#edit-form-model-properties-of-an-adaptive-form-edit-form-model)**: Vous pouvez associer un schéma de modèle de données de formulaire à un modèle de formulaire adaptatif dans l’éditeur de modèles. Cela permet de réduire le temps nécessaire à la création d’un formulaire adaptatif. L’option est également ajoutée à l’éditeur de Forms adaptatif pour permettre aux utilisateurs de sélectionner ou de modifier le modèle de données de formulaire pour les formulaires existants.
   * **[Document d’enregistrement dans l’éditeur de modèles](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#document-of-record-support-in-adaptive-form-editor-dor-support-in-adaptiveform)**: Vous pouvez désormais normaliser la génération du document d’enregistrement pour tous les formulaires créés à l’aide d’un modèle. Cela permet d’améliorer la conformité et la normalisation des exigences de l’organisation.

* **[Lancement de l’assistant de formulaire adaptatif à partir d’une page AEM Sites](/help/forms/embed-adaptive-form-aem-sites.md)**: La page AEM Sites a étendu la prise en charge d’Adaptive Forms. Vous pouvez désormais créer un formulaire adaptatif ou incorporer un formulaire adaptatif existant tout en restant sur la page AEM Sites.
* **[Modifier l’alignement de l’affichage des cases à cocher et du bouton radio dans le DE](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#customize-the-branding-information-in-document-of-record-customize-the-branding-information-in-document-of-record)**: Vous pouvez maintenant définir l’alignement souhaité (horizontal, vertical, identique à Forms adaptatif) pour la case à cocher et le bouton radio du document d’enregistrement. Cette option détermine le positionnement des options de case à cocher et de bouton radio dans le document d’enregistrement.

## Module complémentaire CIF {#cloud-services-cif}

### Nouveautés {#what-is-new-cif}

* Les auteurs peuvent enrichir dynamiquement des listes de produits avec des fragments d’expérience (par exemple : placer une bannière entre les listes de produits).
* Le composant Liste prend désormais en charge les pages de produits/catégories associées afin d’afficher dynamiquement les pages associées.
* La prise en charge des composants Peregrine 12.5 a été ajoutée.
* La prise en charge du chargement des prix côté client dans le teaser de produit et le carrousel a été ajoutée.

## [!DNL Experience Manager as a Cloud Service] Foundation {#foundation}

### Nouveautés {#what-is-new-foundation}

* AEM as a Cloud Service (Author Service) est désormais intégré à l’environnement de travail unifié afin d’améliorer l’expérience utilisateur et de l’unifier avec toutes les autres applications Experience Cloud. Reportez-vous à AEM en tant que [Cloud Service sur Shell unifié](/help/overview/aem-cloud-service-on-unified-shell.md) pour plus d’informations.

* Comme mentionné précédemment dans les notes de mise à jour, l’utilisation de l’écran d’administration de l’agent de réplication ou de l’API de réplication pour distribuer des modules de contenu de plus de 10 Mo (noeuds avec des propriétés, sans inclure les fichiers binaires) est obsolète et sera appliquée dans les prochains jours. Reportez-vous à la section [Gérer la publication](/help/operations/replication.md#manage-publication) ou le [Processus de publication de l’arborescence de contenu](/help/operations/replication.md#publish-content-tree-workflow) pour connaître les approches suggérées pour répliquer ces modules de contenu volumineux.

* La configuration de Dispatcher référence désormais un fichier qui répertorie les paramètres de requête de campagne marketing courants. Les clients peuvent choisir de supprimer les commentaires des paramètres qui les concernent, ce qui se traduit par une meilleure mise en cache. Voir [Paramètres de campagne marketing](/help/implementing/dispatcher/caching.md#marketing-parameters) pour plus d’informations.

## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici](/help/implementing/cloud-manager/release-notes-cloud-manager/release-notes-cm-current.md).

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [ici](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
