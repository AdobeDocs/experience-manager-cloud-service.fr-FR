---
title: Notes de mise à jour de la version 2023.2.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la version 2023.2.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 671056e6-84cc-4c2c-bca3-fde68d5cc835
feature: Release Information
role: Admin
source-git-commit: b4ffcddddfcd990c359380071f19b5442dee9eb2
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 100%

---

# Notes de mise à jour de la version 2023.2.0 d’[!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour techniques de la version 2023.2.0 d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes ; par exemple, celles de 2021, 2022 et ainsi de suite.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de la version actuelle (2023.2.0) d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le 12 avril 2023. La prochaine mise à jour des fonctionnalités (2023.4.0) est prévue pour le 7 juin 2023.

## Vidéo de mise à jour {#release-video}

Consultez la vidéo Aperçu de la mise à jour de février 2023 pour un résumé des fonctionnalités ajoutées dans la version 2023.2.0 :

>[!VIDEO](https://video.tv.adobe.com/v/3416885/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités de la version préliminaire d’[!DNL Experience Manager Sites] {#prerelease-sites}

* Exportez des fragments de contenu d’AEM as a Cloud Service vers Adobe Target en tant qu’offres JSON.
* La prise en charge de la pagination et du tri GraphQL, ainsi que des améliorations de la mise en cache interne, permettent désormais d’accroître les performances des applications clientes découplées lors de la récupération de jeux de contenu volumineux d’AEM à l’aide de requêtes et de filtres GraphQL complexes.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de [!DNL Assets] {#assets-features}

* Prise en charge du nouveau protocole (DASH, Dynamic Adaptive Streaming over HTTP) pour le streaming adaptatif dans les diffusions vidéo Dynamic Media (avec CMAF activé) :
   * La diffusion en continu à débit adaptatif (DASH/HLS) garantit une meilleure expérience de visionnage des vidéos aux utilisateurs et utilisatrices finaux
   * Largement adopté dans le secteur, DASH est le protocole standard international pour le streaming à débit adaptatif de vidéos.

* Ajout de la prise en charge des images WebP pour extraire automatiquement les métadonnées, générer des miniatures et des rendus personnalisés. Les fonctionnalités de balisage et de recadrage intelligents sont désormais également prises en charge pour ces fichiers.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités disponibles dans [!DNL Forms] {#new-features-available-in-channel}

* **[Utiliser des composants principaux de capture de données pour créer des formulaires adaptatifs](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=fr)** : [utilisez l’éditeur de formulaires adaptatifs](/help/forms/creating-adaptive-form-core-components.md) pour créer des formulaires basés sur des composants de capture de données normalisés (composants principaux). Ces composants offrent des fonctionnalités de personnalisation, un délai de développement réduit et de plus bas coûts de maintenance pour vos expériences d’inscription numérique.

* **[Prise en charge du pipeline front-end pour la mise en forme des formulaires adaptatifs basés sur des composants principaux](/help/forms/using-themes-in-core-components.md)** : utilisez des thèmes basés sur la méthodologie AEM pour les formulaires adaptatifs basés sur les composants principaux en les déployant avec le pipeline de déploiement front-end afin d’améliorer l’aspect de vos formulaires et de respecter les directives de conception approuvées de votre organisation.

* **[Génération d’un document d’enregistrement pour les formulaires adaptatifs basés sur les composants principaux](/help/forms/generate-document-of-record-core-components.md)**: créez un document d’enregistrement contenant les données envoyées pour les formulaires adaptatifs créés à l’aide des composants principaux pour l’archivage ou la référence aux utilisateurs et utilisatrices finaux, sur papier ou au format document.

![https://www.aemcomponents.dev/](/help/forms/assets/sample-core-components-based-adaptive-form.png)

* **[Création de formulaires efficace à l’aide de la fonction Enregistrer un formulaire adaptatif en tant que modèle](/help/forms/template-editor.md#save-an-adaptive-form-as-template-saving-adaptive-form-as-template)** : accélérez et normalisez la création de formulaires en enregistrant les formulaires existants approuvés par la marque en tant que modèles de formulaire pour une réutilisation rapide.

* **[Connexion d’AEM Forms à des bases de données prises en charge par JDBC](/help/forms/configure-data-sources.md#configure-relational-database-configure-relational-database)** : connectez-vous à des bases de données d’entreprise directement à partir d’AEM Cloud Service à l’aide du protocole JDBC, sans avoir à les exposer via l’API REST.

* **[Intégration aux points d’entrée REST à l’aide de l’API Open 3.0](/help/forms/configure-data-sources.md#configure-restful-services-open-api-specification-version-20-configure-restful-services-swagger-version30)** : réalisez aisément des intégrations à des systèmes d’enregistrement qui prennent en charge l’API Open 3.0 pour stocker et récupérer des données à l’aide de modèles de données de formulaire.

* **[Partager un formulaire adaptatif pour révision](/help/forms/create-reviews-forms.md)** : utilisez le mécanisme de révision des formulaires adaptatifs pour permettre à une ou plusieurs personnes de réviser le formulaire.


### Fonctionnalités de la version préliminaire de [!DNL Forms] {#prerelease-features-forms}

* **[Envois de formulaires adaptatifs à Microsoft SharePoint et Microsoft OneDrive](/help/forms/configuring-submit-actions.md)** : améliorez l’agilité des utilisateurs et utilisatrices professionnels pour ouvrir rapidement de nouveaux formulaires et stockez les données envoyées dans les outils quotidiens qu’ils et elles utilisent comme les sites Microsoft SharePoint ou les dossiers OneDrive.

![Envoi de formulaires adaptatifs à Microsoft SharePoint et Microsoft OneDrive](/help/forms/assets/onedrive-and-sharepoint.jpg)


## Programme des formulaires adaptatifs découplés destiné aux utilisateurs et utilisatrices précoces {#forms-early-adopter}

Utilisez les formulaires adaptatifs découplés pour permettre à vos développeurs et développeuses de créer, publier et gérer des formulaires interactifs accessibles via des API, plutôt que par le biais d’une interface utilisateur graphique classique. Les formulaires adaptatifs découplés vous aident à :

* créer des formulaires multicanaux de haute qualité dans le langage de programmation de votre choix ;
* intégrer nativement les formulaires à vos applications de bureau et mobiles, à vos sites web et à vos applications de chat ;
* réutiliser vos composants d’IU propriétaires avec des applications de formulaires ;
* tirer profit de la puissance d’Adobe Experience Manager Forms

Vous pouvez envoyer un e-mail à aem-forms-headless@adobe.com à partir de votre ID d’e-mail officiel pour rejoindre le programme d’utilisateurs et utilisatrices précoces.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici](/help/implementing/cloud-manager/release-notes/current.md).

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [ici](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
