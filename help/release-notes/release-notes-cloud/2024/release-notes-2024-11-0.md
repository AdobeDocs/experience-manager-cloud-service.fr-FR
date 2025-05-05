---
title: Notes de mise à jour de la version 2024.11.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la version 2024.11.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 3fd6482e-66f0-48ee-983c-4cb6b7742dcd
source-git-commit: d9db32110e1e0aaa5bdc20bd6b4bff6da6a3a3a3
workflow-type: tm+mt
source-wordcount: '1809'
ht-degree: 100%

---

# Notes de mise à jour de la version 2024.11.0 d’[!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour de la version 2024.11.0 d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes, telles que 2022 ou 2023.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Pour recevoir chaque mois une notification par e-mail concernant des informations sur les notes de mise à jour d’Experience Cloud, abonnez-vous aux [Mises à jour de produits prioritaires d’Adobe](https://www.adobe.com/subscription/priority-product-update.html).

## Date de publication {#release-date}

La date de publication de la version actuelle d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2024.11.0) est le 21 novembre 2024. La prochaine version des fonctionnalités (2025.1.0) est prévue pour le vendredi 30 janvier 2025.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

## Vidéo de mise à jour {#release-video}

Consultez la vidéo Vue d’ensemble de la version de novembre 2024 pour obtenir un résumé des fonctionnalités ajoutées dans la version 2024.11.0 :

>[!VIDEO](https://video.tv.adobe.com/v/3440922?quality=12&captions=fre_fr)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

Modèles de page **[!DNL Edge Delivery Services]avec création par l’éditeur universel**

Tansformez rapidement une page Edge Delivery en modèle de page. Vous pouvez ainsi commencer une nouvelle page avec une structure et un contenu prédéfinis au lieu d’une page vierge. [En savoir plus](/help/sites-cloud/authoring/universal-editor/templates.md).

Importateur CSV **[!DNL Edge Delivery Services]pour la publication via une instance AEM**

Gérez efficacement vos données de feuille de calcul Edge Delivery (par exemple, les redirections) dans votre outil de feuille de calcul préféré et chargez-les dans AEM via le nouvel importateur CSV. [En savoir plus](/help/edge/wysiwyg-authoring/tabular-data.md#importing).

### Fonctionnalités de version préliminaire dans AEM Sites

Amélioration du [référencement de fragment de contenu avec des références basées sur des ID uniques](/help/headless/graphql-api/uuid-reference-upgrade.md), ce qui garantit des liens stables qui restent valides même lorsque des ressources ou des fragments sont déplacés, éliminant ainsi la nécessité de mises à jour ou de republication. Limites actuelles : les références de page ne sont pas encore prises en charge avec les identifiants uniques. Si des pages sont référencées dans des fragments de contenu, cette fonctionnalité ne doit pas être utilisée.

### Programme d’adoption précoce {#sites-early-adopter}

**API AEM REST OpenAPI pour la diffusion de fragments de contenu**

L’[API AEM REST OpenAPI pour la diffusion de fragments de contenu ](/help/headless/aem-content-fragment-delivery-with-openapi.md) est désormais disponible pour AEM as a Cloud Service.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Fonctionnalités d’accès anticipé dans Dynamic Media {#dm-early-access}

**Sous-titres vidéo générés par l’IA**

Adobe Dynamic Media utilise l’intelligence artificielle pour générer automatiquement des sous-titres pour le contenu vidéo. Cette fonctionnalité est conçue pour améliorer l’accessibilité et l’expérience d’utilisation en fournissant des sous-titres précis en temps réel. L’IA analyse la piste audio de la vidéo pour transcrire la parole et créer des sous-titres, qui peuvent être modifiés pour plus de précision ou de personnalisation. Ces sous-titres permettent de répondre aux exigences d’accessibilité et d’améliorer l’engagement vidéo pour les audiences qui dépendent d’une prise en charge vidéo basée sur le texte ou qui préfèrent ce système.

Pour bénéficier d’un accès anticipé à la prise en charge des sous-titres générés par l’IA sur votre compte Dynamic Media, vous devez [créer et envoyer un cas d’assistance clientèle Adobe ](/help/assets/dynamic-media/video.md##enable-dash).

**Rapport de diffusion Dynamic Media**

Obtenez des informations de diffusion pour les ressources diffusées avec Dynamic Media, avec le nombre de diffusions au niveau des ressources, les informations sur les référents, le chemin d’accès aux ressources dans AEM Assets et un identifiant de ressource unique. Les rapports peuvent être générés pour toutes les ressources diffusées via Dynamic Media pour le référentiel AEM Assets ou pour une hiérarchie de dossiers spécifique dans AEM Assets. Les informations permettent de mesurer le retour sur investissement des ressources diffusées, de mesurer les performances des canaux et de prendre des décisions éclairées en matière de gestion des ressources.

Pour bénéficier d’un accès anticipé au rapport de diffusion Dynamic Media sur votre compte Dynamic Media, vous devez [créer et envoyer une demande d’assistance clientèle Adobe](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html).

### Nouvelles fonctionnalités de la vue Assets {#assets-view-new-features}

**Panneau Dynamic Media**

La vue Assets vous permet désormais d’accéder à Dynamic Media et à des rendus OpenAPI Dynamic Media à partir d’un panneau distinct mis à votre disposition. Vous pouvez choisir de copier l’URL de diffusion ou de télécharger les rendus en fonction de la ressource et du type de rendu. Pour plus d’informations, voir [Rendus Dynamic Media](/help/assets/renditions.md#dynamic-media-renditions) et [rendus avec fonctionnalités OpenAPI Dynamic Media](/help/assets/renditions.md#dm-with-openapi-renditions).

![Rendus dynamiques](/help/assets/assets/dm-scene7-renditions.png)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités d’AEM Forms {#forms-new-features}

* **[Mise à jour simplifiée des portées d’Adobe Sign](/help/forms/adobe-sign-integration-adaptive-forms.md)** : vous pouvez modifier les portées d’une configuration Adobe Sign directement depuis la page Configurations d’AEM Cloud, simplifiant et accélérant ainsi la mise à jour des configurations existantes.

* **[Prise en charge des fonctions asynchrones pour les formulaires adaptatifs](/help/forms/using-async-funct-in-rule-editor.md)** : lorsque votre formulaire adaptatif nécessite des opérations asynchrones, comme l’attente de processus externes ou la récupération de données, vous pouvez implémenter ces opérations avec des fonctions personnalisées et les configurer dans l’éditeur de règles.

### Fonctionnalités de version préliminaire dans AEM Forms {#forms-new-prerelease-features}

* **Gérer la publication** : vous pouvez utiliser le workflow Gérer la publication pour publier ou annuler la publication de formulaires dans tous les environnements, généralement de l’instance de création aux instances de publication et de prévisualisation. Cela permet aux utilisateurs et utilisatrices de publier, d’annuler la publication ou de planifier la publication du contenu de manière rationnalisée.

* **[Enregistrement automatique d’un brouillon pour les formulaires adaptatifs basés sur les composants principaux](/help/forms/save-core-component-based-form-as-draft.md)** : les utilisateurs et les utilisatrices peuvent désormais bénéficier d’une fonction d’enregistrement automatique, qui sauvegarde automatiquement un formulaire partiellement complété en tant que brouillon. Ces personnes peuvent revenir ultérieurement pour finir de le remplir sur le même appareil ou sur un autre. Cette fonctionnalité améliore les taux de conversion pour les organisations en réduisant l’abandon de formulaire, car les utilisateurs et utilisatrices n’ont pas besoin de recommencer à remplir le formulaire depuis le début.

* **[Améliorations apportées à l’éditeur de règles](/help/forms/invoke-service-enhancements-rule-editor.md)** : pour les formulaires adaptatifs basés sur les composants principaux, vous pouvez désormais renseigner les options de liste déroulante à l’aide de la sortie du service Invoke, définir des panneaux répétables à l’aide de la sortie du service Invoke, définir des panneaux individuels à l’aide de la sortie du service Invoke et utiliser le paramètre de sortie du service Invoke pour valider d’autres champs.

* **[Amélioration de l’interface d’utilisation grâce aux boutons de navigation dans les mises en page de panneau](/help/forms/rule-editor-core-components-usecases.md#navigating-among-panels-using-button)** : vous pouvez désormais ajouter des boutons de navigation à vos mises en page de panneau, par exemple Onglets horizontaux, Onglets verticaux, Accordéons ou Assistant. Ces boutons optimisent la navigation en simplifiant les transitions entre les panneaux et en mettant l’accent sur le panneau sélectionné.


### Fonctionnalités d’accès anticipé dans AEM Forms {#forms-new-early-access-features}

Le programme d’accès anticipé d’AEM Forms vous offre une opportunité unique d’accéder de manière exclusive à des innovations de pointe et de contribuer à façonner leur développement.

Les notes de mise à jour répertorient les innovations apportées à la version actuelle. Pour obtenir la liste complète des innovations disponibles dans le cadre du programme d’accès anticipé, voir [Documentation du programme d’accès anticipé d’AEM Forms](/help/forms/early-access-ea-features.md).

#### Intégrations

* **[Intégrer les formulaires adaptatifs à Adobe Marketo Engage](/help/forms/integrate-form-to-marketo-engage.md)** : AEM Forms as a Cloud Service comprend désormais une option conviviale pour connecter les formulaires adaptatifs à Adobe Marketo Engage. Cette intégration vous permet de créer des formulaires adaptatifs directement avec la capture de prospect de Marketo Engage et les objets personnalisés associés. Vous pouvez désormais préremplir des champs de formulaire avec des données provenant de Marketo Engage et renvoyer les données pour automatiser les workflows tels que les campagnes intelligentes et l’automatisation des e-mails. Vous pouvez également connecter un formulaire adaptatif à la bibliothèque Munchkin pour effectuer le suivi du nombre de visites, de clics et d’envois de formulaire.

#### Formulaires adaptatifs et formulaires HTML5

* **[Créer des formulaires adaptatifs basés sur un modèle XFA existant](/help/forms/create-adaptive-form-using-xfa-templates.md)** : vous pouvez désormais créer des formulaires adaptatifs basés sur des composants principaux à l’aide de modèles de formulaire XFA (*.fichiers XDP). Cette fonctionnalité permet aux clientes et clients On-Premise d’AEM Forms de bénéficier d’investissements existants dans la technologie XFA pour adopter AEM Forms as a Cloud Service.

* **Formulaires HTML5 (formulaires web XFA)** : les clientes et clients AEM Forms On-Premise qui utilisent la technologie XFA peuvent désormais passer facilement à AEM Forms as a Cloud Service tout en préservant leur expérience d’utilisation existante avec les formulaires HTML5 (formulaires web XFA). Cette fonctionnalité permet le rendu des modèles de formulaire XFA au format HTML5, rendant les formulaires accessibles sur les appareils qui ne prennent pas en charge les formulaires PDF XFA.

  ![Formulaires HTML (formulaires web XFA)](/help/forms/assets/html-forms-xfa-based-web-forms.png)


* **[Prise en charge des chaînes codées en base64 pour les pièces jointes](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/file-attachment#basic-tab)** : le composant Pièce jointe dans les formulaires adaptatifs basés sur les composants principaux inclut désormais une option pour envoyer les fichiers joints en tant que chaînes codées en base64.

#### API Interactive Communications and Communication

* **Éditeur de communication interactive** : l’éditeur de communication interactive est un outil de conception de communication graphique convivial qui simplifie la création de correspondances personnalisées et pilotées par les données et s’exécute dans n’importe quel navigateur moderne. Il prend en charge l’intégration transparente des données, une définition logique complexe et une intégration des médias riches, assurant la collecte de documents professionnels et conformes, de communications et de modèles pour divers besoins professionnels.

  ![Éditeur de communication interactive](/help/forms/assets/ic-editor.png)


* **[Améliorations de la conformité PDF/A](/help/forms/aem-forms-cloud-service-communications-introduction.md#convert-to-and-validate-pdfa-compliant-documents)** : vous pouvez désormais utiliser les API Communication pour convertir des documents PDF au format PDF/A (1a, 2a, 3a) à des fins d’archivage tout en assurant l’accessibilité et en vérifiant la conformité avec ces normes.


* **[API Signature (Document Assurance)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance)** : une nouvelle API RESTful dans les API de communication permet une gestion facile des signatures de PDF. Elle prend en charge des opérations suivantes :
   * Effacer la signature : supprime une signature d’un champ spécifié.
   * Supprimer le champ de signature : supprime un champ de signature spécifié.

<!-- 
* **Hamburger Menu Layout in Adaptive Forms**: Adaptive Forms now offers a responsive hamburger menu layout for mobile devices. This collapsible menu organizes form sections, making navigation more 
intuitive and improving the mobile form-filling experience.

* **Masked Field with Eye Icon (Password Box Component)**: The Password Box is a text input field that masks the characters typed into it by displaying placeholder symbols. It allows users to securely input sensitive information, such as passwords and enables them to toggle visibility on demand using the eye icon.

-->

## Service de conversion automatisée de formulaires

* **[Convertir des formulaires PDF en composants principaux basés sur des formulaires adaptatifs](https://experienceleague.adobe.com/fr/docs/aem-forms-automated-conversion-service/using/convert-existing-forms-to-adaptive-forms)** : vous pouvez désormais utiliser le service de conversion automatisée de formulaires pour transformer des formulaires PDF, AcroForms ou des formulaires XFA en formulaires adaptatifs basés sur des composants principaux.

>[!IMPORTANT]
>
> Vous souhaitez adhérer au Programme d’accès anticipé pour des formulaires innovants ? Envoyez un e-mail depuis votre adresse officielle à [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) avec la liste des fonctionnalités qui vous intéressent.## Module complémentaire CIF {#cloud-services-cif}

## Module complémentaire CIF {#cif}

### Correctifs {#bug-fixes-cif}

* Correction des tests de l’interface d’utilisation pour qu’ils fonctionnent correctement avec les composants principaux CIF.
* Correction d’un problème en raison duquel le format des URL de catégorie ne fonctionnait pas comme prévu dans l’instance cloud.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Amélioration des performances de réplication d’arborescence (et obsolescence du workflow de publication d’arborescence de contenu) {#tree-replication-performance}

L’[étape de workflow d’activation de l’arborescence](/help/operations/replication.md#tree-activation) est une nouvelle étape de modèle de workflow recommandée pour répliquer des hiérarchies de contenu profondes. Elle permet aux réplications indépendantes (par exemple, par le biais d’une publication rapide ou d’une gestion de la publication) de se poursuivre en parallèle du workflow de réplication de l’arborescence en cours. Cela s’avère particulièrement utile si vous devez publier du contenu urgent alors qu’une réplication en masse est toujours en cours. L’étape de réplication de l’arborescence remplace le workflow de publication de l’arborescence de contenu et son étape de workflow associée, qui sont désormais obsolètes.

### API OpenAPI - Programme d’adoption anticipée {#open-apis-earlyadopter}

Les développeurs et développeuses peuvent intégrer des fonctionnalités AEM as a Cloud Service en profondeur dans leurs propres applications et outils. Les nouvelles API AEM as a Cloud Service suivront la spécification OpenAPI dans le but d’être cohérentes, bien documentées et conviviales. Les informations d’identification des points d’entrée nécessitant une authentification seront générées lors de la création de projets Adobe Developer Console.

Découvrez les [API OpenAPI AEM](/help/implementing/developing/open-api-based-apis.md) et suivez un [tutoriel de bout en bout](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis) illustrant la configuration et l’utilisation.

Concrètement, les points d’entrée d’API répertoriés ci-dessous sont disponibles dans le cadre d’un programme d’adoption précoce. Si cela vous intéresse, envoyez un e-mail à l’adresse [aem-apis@adobe.com](mailto:aem-apis@adobe.com) décrivant comment vous prévoyez de les utiliser.
* [API Sites Content Fragments](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/)
* [API Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/assets/author/)
* [API Sites and Assets Folders](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/folders/)
* [API Forms Communications](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/)

### Edge Computing - Demande de commentaires {#edge-computing-feedback}

L’Edge Computing rapproche le traitement des données du navigateur, ce qui présente des avantages, notamment une latence réduite. En tant que contribution à la feuille de route, nous aimerions savoir si cette technologie est utile pour la diffusion de publication AEM et les projets Edge Delivery Services et ce pour quoi vous envisagez de l’utiliser. Envoyez un e-mail à [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) contenant des questions et des commentaires.

### Nouvelle AEM Developer Console (version bêta publique) {#aem-developer-console-beta}

Testez une [AEM Developer Console](/help/implementing/developing/introduction/aem-developer-console.md) repensée qui offre une expérience plus interactive pour le débogage du code dans les environnements cloud.

Tout le monde peut accéder à la version Beta publique en cliquant sur le bouton *Nouvelle console disponible* dans la console AEM Developer Console actuelle. Adobe souhaite connaître votre avis. Vous pouvez envoyer vos commentaires par e-mail à [aemcs-new-devconsole-ui-beta@adobe.com](mailto:aemcs-new-devconsole-ui-beta@adobe.com).

## [!DNL Experience Manager] Guides {#guides}

Vous trouverez une liste complète des nouvelles fonctionnalités améliorées de la dernière version d’Adobe Experience Manager Guides [ici](https://experienceleague.adobe.com/fr/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici](/help/implementing/cloud-manager/release-notes/current.md).

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [ici](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).

## Éditeur universel {#universal-editor}

Vous trouverez une liste complète des versions de l’éditeur universel [ici](/help/release-notes/universal-editor/current.md).

## Générer des variations {#generate-variations}

Vous trouverez une liste complète des versions de la génération de variations [ici](/help/generative-ai/release-notes-generate-variations.md).

## Notes de mise à jour dʼExperience Cloud {#experience-cloud}

Vous trouverez des informations sur les versions d’autres applications Experience Cloud [ici](https://experienceleague.adobe.com/fr/docs/release-notes/experience-cloud/current).
