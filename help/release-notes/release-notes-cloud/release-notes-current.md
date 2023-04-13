---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
source-git-commit: 085ce15ebe4d48d32a437f13e728f60cfc57d0fa
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 33%

---


# Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour techniques de la version actuelle (la plus récente) d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes ; par exemple, celles de 2021, 2022 et ainsi de suite.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] la version actuelle des fonctionnalités (2023.2.0) est le 12 avril 2023. La prochaine version de la fonctionnalité (2023.4.0) est prévue pour le 27 avril 2023.

## Vidéo de mise à jour {#release-video}

Regardez la vidéo Aperçu de la version de février 2023 pour un résumé des fonctionnalités ajoutées dans la version 2023.2.0 :

>[!VIDEO](https://video.tv.adobe.com/v/3416885/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités de [!DNL Experience Manager Sites] premise {#prerelease-sites}

* Exportez des fragments de contenu d’AEM en tant que service cloud pour Adobe de la cible en tant qu’offres JSON.
* La prise en charge de la pagination et du tri GraphQL, ainsi que des améliorations de la mise en cache interne, permettent désormais d’améliorer les performances des applications clientes découplées lors de la récupération de jeux de contenu volumineux d’AEM à l’aide de requêtes et de filtres GraphQL complexes.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de [!DNL Assets] {#assets-features}

* Nouvelle prise en charge du protocole (DASH - Dynamic Adaptive Streaming over HTTP) pour la diffusion en continu adaptative dans les diffusions vidéo Dynamic Media (avec CMAF activé) :
   * La diffusion en continu adaptative (DASH/HLS) garantit une meilleure expérience de visionnage des vidéos par l’utilisateur final.
   * DASH est le protocole standard international pour la diffusion de vidéo adaptative en continu et est largement adopté dans le secteur.
   * Disponible dans NA, pour activation via un ticket d’assistance, bientôt disponible dans APAC, EMEA

* Ajout de la prise en charge des images WebP pour extraire automatiquement les métadonnées, générer des miniatures et des rendus personnalisés. Les fonctionnalités Balisage intelligent et Recadrage intelligent sont désormais également prises en charge pour ces fichiers.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités disponibles dans [!DNL Forms] {#new-features-available-in-channel}

* **[Utiliser des composants principaux de capture de données pour créer des formulaires adaptatifs](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=fr)** : [utilisez l’éditeur de formulaires adaptatifs](/help/forms/creating-adaptive-form-core-components.md) pour créer des formulaires basés sur des composants de capture de données normalisés (composants principaux). Ces composants offrent des fonctionnalités de personnalisation, un délai de développement réduit et de plus bas coûts de maintenance pour vos expériences d’inscription numérique.

* **[Prise en charge du pipeline Frontend pour le style d’un Forms adaptatif basé sur des composants principaux](/help/forms/using-themes-in-core-components.md)**: Utilisez des thèmes normalisés basés sur BEM pour les Forms adaptatives basées sur les composants principaux en les déployant avec le pipeline de déploiement Frontend afin d’améliorer l’aspect des formulaires et de vous aligner sur les directives de conception approuvées par votre entreprise.

* **[Générer un document d’enregistrement pour le Forms adaptatif basé sur les composants principaux](/help/forms/generate-document-of-record-core-components.md)**: Créez un document d’enregistrement contenant les données envoyées pour le Forms adaptatif créé à l’aide des composants principaux pour l’archivage ou la référence aux utilisateurs finaux, sur papier ou au format de document.

![https://www.aemcomponents.dev/](/help/forms/assets/sample-core-components-based-adaptive-form.png)

* **[Création de formulaires efficace à l’aide de la fonction Enregistrer un formulaire adaptatif en tant que modèle](/help/forms/template-editor.md#save-an-adaptive-form-as-template-saving-adaptive-form-as-template)**: Accélérez et normalisez le développement de formulaires en enregistrant les formulaires existants approuvés par la marque en tant que modèles de formulaire pour une réutilisation rapide.

* **[Connexion d’AEM Forms à des bases de données prises en charge par JDBC](/help/forms/configure-data-sources.md#configure-relational-database-configure-relational-database)**: Connectez-vous à des bases de données d’entreprise directement à partir d’AEM Cloud Service à l’aide du protocole JDBC, sans avoir à les exposer via l’API REST.

* **[Intégration aux points de fin REST à l’aide de l’API Open 3.0](/help/forms/configure-data-sources.md#configure-restful-services-open-api-specification-version-20-configure-restful-services-swagger-version30)**: Intégrez en toute transparence dans les systèmes d’enregistrement qui prennent en charge l’API Open 3.0 pour stocker et récupérer des données à l’aide de modèles de données de formulaire.

* **[Partager un formulaire adaptatif pour révision](/help/forms/create-reviews-forms.md)** : utilisez le mécanisme de révision des formulaires adaptatifs pour permettre à une ou plusieurs personnes de réviser le formulaire.


### Fonctionnalités d’ [!DNL Forms] préliminaires {#prerelease-features-forms}

* **[Envoyer le Forms adaptatif à Microsoft SharePoint et Microsoft OneDrive](/help/forms/configuring-submit-actions.md)**: Améliorez l’agilité des utilisateurs professionnels afin de lancer rapidement de nouveaux formulaires et de stocker les données envoyées dans les outils quotidiens qu’ils utilisent comme le site Microsoft SharePoint ou le dossier OneDrive.

![Envoyer le Forms adaptatif à Microsoft SharePoint et Microsoft OneDrive](/help/forms/assets/onedrive-and-sharepoint.jpg)


## Programme d’adoption précoce de Forms adaptatif sans tête {#forms-early-adopter}

Utilisez Headless Adaptive Forms pour permettre aux développeurs de créer, publier et gérer des formulaires interactifs accessibles et interactifs via les API, plutôt que par le biais d’une interface utilisateur graphique classique. Les formulaires adaptatifs sans affichage vous aident à :

* créer des formulaires multicanaux de haute qualité dans le langage de programmation de votre choix ;
* Intégration native de formulaires à vos applications de bureau et mobiles, à vos sites web et à vos applications de conversation
* réutilisation de vos composants d’IU propriétaires avec des applications de formulaires
* tirer parti de la puissance d’Adobe Experience Manager Forms

Vous pouvez envoyer un courrier électronique à aem-forms-headless@adobe.com à partir de votre ID de courrier électronique officiel pour rejoindre le programme des premiers adopteurs.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici.](/help/implementing/cloud-manager/release-notes/current.md)

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [ici](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
