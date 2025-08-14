---
title: Notes de mise à jour de la version 2025.1.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la version 2025.1.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 085629bf-fb24-4511-af6c-bbbeedcb6b98
source-git-commit: bb149cd43158bfd1ceb43b04cc536c8c8291f968
workflow-type: tm+mt
source-wordcount: '1703'
ht-degree: 92%

---

# Notes de mise à jour de la version 2025.1.0 d’[!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour de la version 2025.1.0 d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes, telles que 2023 ou 2024.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Pour recevoir chaque mois une notification par e-mail concernant des informations sur les notes de mise à jour d’Experience Cloud, abonnez-vous aux [Mises à jour de produits prioritaires d’Adobe](https://www.adobe.com/subscription/priority-product-update.html).

## Date de publication {#release-date}

La date de publication de la version actuelle de [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2025.1.0) est le 30 janvier 2025. La prochaine disponibilité des fonctionnalités (2025.2.0) est prévue pour le 4 mars 2025.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

## Vidéo de mise à jour {#release-video}

Consultez la vidéo Vue d’ensemble de la version de janvier 2025 pour un résumé des fonctionnalités ajoutées dans la version 2025.1.0 :

>[!VIDEO](https://video.tv.adobe.com/v/3456072?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

**Commentaires disponibles dans l’éditeur de fragment de contenu**

Collaborez facilement avec vos collègues lors de la création de fragments de contenu AEM en utilisant le nouveau service de commentaires modernisé de l’éditeur de fragments de contenu AEM.
[En savoir plus](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/sites/administering/content-fragments/authoring?#commenting-on-your-fragment).

**Interfaces utilisateur de l’édition et de l’administration des fragment de contenu, prise en charge des versions mises à jour d’AEM as a Cloud Service**

La version AEM as a Cloud Service minimale prise en charge pour les nouvelles interfaces utilisateur d’administration et de l’éditions des fragments de contenu est désormais 2023.8.13099. Les versions antérieures à la version de disponibilité générale des nouvelles interfaces d’utilisation ne sont plus prises en charge.

### Programme d’adoption précoce {#sites-early-adopter}

**Amélioration des fragments de contenu**

Amélioration du [référencement de fragments de contenu avec des références basées sur des ID uniques](/help/headless/graphql-api/uuid-reference-upgrade.md), afin que les requêtes GraphQL pour les fragments de contenu individuels puissent rester stables même si le fragment a été déplacé vers un autre emplacement. Cela est désormais possible avec les requêtes « ByID ». Bien que les chemins puissent changer, rompant potentiellement les requêtes « ByPath », les UUID sont stables. Les nouveaux ID peuvent également être renvoyés en tant que propriétés dans toute requête ou autre requête d’API applicable. Limites actuelles (2025.1) : les références de page ne sont pas encore prises en charge avec les identifiants uniques. Si des pages sont référencées dans des fragments de contenu, cette fonctionnalité ne doit pas être utilisée. Il est prévu de supprimer cette limitation dans la prochaine version d’AEM as a Cloud Service.

**AEM REST OpenAPI pour la diffusion de fragments de contenu**

L’API [AEM REST OpenAPI pour la diffusion de fragments de contenu](/help/headless/aem-content-fragment-delivery-with-openapi.md) est désormais disponible pour AEM as a Cloud Service.

### Fonctionnalités obsolètes {#sites-deprecated}

#### Éditeur de SPA {#spa-editor}

[L’éditeur de SPA](/help/implementing/developing/hybrid/introduction.md) a été abandonné pour les nouveaux projets à partir de la version 2025.1.0. L’éditeur de SPA reste pris en charge pour les projets existants, mais ne doit pas être utilisé pour de nouveaux projets.

Les éditeurs privilégiés pour la gestion du contenu découplé dans AEM sont désormais les suivants :

* [Éditeur universel](https://www.aem.live/docs/aem-authoring) pour la modification visuelle.
* [Éditeur de fragments de contenu](/help/assets/content-fragments/content-fragments-managing.md) pour la modification basée sur les formulaires.

#### Fonctionnalités PWA {#pwa-features}

[Les fonctionnalités de l’application web progressive (PWA)](/help/sites-cloud/authoring/sites-console/enable-pwa.md) pour AEM Sites sont désormais obsolètes pour les nouveaux projets commençant par la version 2025.1.0. Cette fonctionnalité reste prise en charge pour les projets existants, mais ne doit pas être utilisée pour les nouveaux projets

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités d’AEM Assets {#new-features-assets}

**Rapports de diffusion Dynamic Media**

Obtenez des informations de diffusion pour les ressources diffusées avec Dynamic Media, y compris le nombre de diffusions au niveau des ressources, les détails sur les référents, les chemins d’accès aux ressources dans AEM Assets et des identifiants de ressource uniques. Générez des rapports pour toutes les ressources du référentiel AEM Assets ou pour des hiérarchies de dossiers spécifiques. Ces informations vous permettent de mesurer le retour sur investissement des ressources diffusées, d’évaluer les performances des canaux et de prendre des décisions éclairées en matière de gestion des ressources.

![Rendus dynamiques](/help/assets/assets/referrer.png)

**Plusieurs sous-titres et pistes audio Dynamic Media**

[Prise en charge de plusieurs sous-titres et pistes audio pour les vidéos dans Dynamic Media](/help/assets/dynamic-media/video.md#about-msma). Vous pouvez désormais facilement ajouter plusieurs sous-titres et plusieurs pistes audio à une vidéo principale. Cette fonctionnalité signifie que vos vidéos sont accessibles à une audience mondiale. Vous pouvez personnaliser une seule vidéo principale publiée pour une audience mondiale dans plusieurs langues et respecter les directives d’accessibilité pour différentes régions géographiques. Les auteurs et autrices peuvent également gérer les sous-titres et les pistes audio à partir d’un seul onglet de l’interface d’utilisation.

**Prise en charge du streaming adaptatif dynamique via HTTP**

Prise en charge du nouveau protocole (DASH, Dynamic Adaptive Streaming over HTTP) pour le streaming adaptatif dans les diffusions vidéo Dynamic Media (avec CMAF activé) :

* Le streaming adaptatif (DASH/HLS) garantit une meilleure expérience de visionnage des vidéos aux utilisateurs et utilisatrices.

* Largement adopté dans le secteur, DASH est le protocole standard international pour le streaming à débit adaptatif de vidéos.


**Retraiter les ressources**

La vue Assets prend désormais en charge le retraitement des ressources disponibles dans un dossier. Vous pouvez choisir d’utiliser l’option **Processus complet** ou d’utiliser des options avancées, telles que les rendus d’aperçu par défaut, les métadonnées, le workflow de post-traitement et le profil de traitement.

### Fonctionnalités d’accès anticipé dans AEM Assets {#early-access-features-assets}

**Sous-titres vidéo générés par l’IA**

Adobe Dynamic Media utilise l’intelligence artificielle pour générer automatiquement des sous-titres pour le contenu vidéo. Cette fonctionnalité est conçue pour améliorer l’accessibilité et l’expérience d’utilisation en fournissant des sous-titres précis en temps réel. Les sous-titres sont générés à partir de l’audio original, de pistes audio supplémentaires ou de sous-titres supplémentaires fournis dans l’onglet « Sous-titres et audio » de la page des propriétés vidéo. Avec une prise en charge de plus de 60 langues, les sous-titres peuvent être examinés et prévisualisés avant de publier la vidéo.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités d’AEM Forms {#forms-new-features}

* **Gérer la publication** : vous pouvez utiliser le workflow [Gérer la publication](/help/forms/manage-publication.md#publish-forms-using-the-manage-publication-option)) pour publier ou dépublier des formulaires dans les environnements, généralement de l’instance d’auteur aux instances de publication et de prévisualisation. Cela permet aux utilisateurs et utilisatrices de publier, d’annuler la publication ou de planifier la publication du contenu de manière rationnalisée.

* **[Enregistrement automatique d’un brouillon pour les formulaires adaptatifs basés sur les composants principaux](/help/forms/save-core-component-based-form-as-draft.md)** : les utilisateurs et les utilisatrices peuvent désormais bénéficier d’une fonction d’enregistrement automatique, qui sauvegarde automatiquement un formulaire partiellement complété en tant que brouillon. Ces personnes peuvent revenir ultérieurement pour finir de le remplir sur le même appareil ou sur un autre. Cette fonctionnalité améliore les taux de conversion pour les organisations en réduisant l’abandon de formulaire, car les utilisateurs et utilisatrices n’ont pas besoin de recommencer à remplir le formulaire depuis le début.

* **[Améliorations de l’éditeur de règles](/help/forms/invoke-service-enhancements-rule-editor.md)** : pour le Forms adaptatif basé sur les composants principaux, vous pouvez utiliser la sortie d’Invoke Service pour renseigner les options de liste déroulante et définir des panneaux répétables ou individuels. De plus, cette sortie peut être utilisée pour valider d’autres champs.

* **[Amélioration de l’interface d’utilisation grâce aux boutons de navigation dans les mises en page de panneau](/help/forms/rule-editor-core-components-usecases.md#navigating-among-panels-using-button)** : vous pouvez désormais ajouter des boutons de navigation à vos mises en page de panneau, par exemple Onglets horizontaux, Onglets verticaux, Accordéons ou Assistant. Ces boutons optimisent la navigation en simplifiant les transitions entre les panneaux et en mettant l’accent sur le panneau sélectionné.


### Fonctionnalités d’accès anticipé dans AEM Forms {#forms-new-early-access-features}

Le programme d’accès anticipé d’AEM Forms vous offre une opportunité unique d’accéder de manière exclusive à des innovations de pointe et de contribuer à façonner leur développement.

Les notes de mise à jour répertorient les innovations apportées à la version actuelle. Pour obtenir la liste complète des innovations disponibles dans le cadre du programme d’accès anticipé, voir [Documentation du programme d’accès anticipé d’AEM Forms](/help/forms/early-access-ea-features.md).

#### [Modèles d’e-mail HTML dans Adaptive Forms](/help/forms/html-email-templates-in-adaptive-forms.md)

Le Forms adaptatif permet d’utiliser des modèles d’e-mail HTML. Les modèles d’e-mail HTML vous permettent d’envoyer des e-mails enrichis, personnalisés et visuellement attrayants lorsqu’un formulaire est envoyé. Ces e-mails peuvent être personnalisés avec des données de formulaire et améliorés à l’aide de différentes balises d’e-mail, telles que des images et des liens. Avec les formulaires adaptatifs, vous pouvez charger un fichier contenant un modèle HTML ou utiliser un éditeur de texte brut pour créer ces modèles.

![Modèle d’e-mail HTML](/help/forms/assets/html-email.png)

#### Amélioration de la prise en charge de l’espace de stockage dans le cloud : chargement direct de PDF vers le stockage Blob Azure

Les API de génération de documents d’AEM Forms prennent désormais en charge le chargement direct des documents de PDF générés vers Azure Blob Storage. Cette amélioration simplifie le stockage et la récupération, améliorant l’efficacité et l’intégration aux workflows cloud.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Prise en charge de Java 21 {#java21}

Vous pouvez désormais créer du code avec Java 21, ce qui inclut de nouvelles fonctionnalités (par exemple, la correspondance de modèles pour les instructions switch, les classes scellées) et des améliorations de performances. Les versions Java 17 sont également prises en charge. Pour connaître les étapes de configuration, notamment la mise à jour des versions de votre projet Maven et de votre bibliothèque, voir l’article [Environnement de création](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#using-java-support).

L’**exécution** de Java 21 la plus performante sera automatiquement déployée lorsqu’une version Java 17 ou 21 est détectée. Cependant, nous vous recommandons également d’opter pour l’exécution de Java 21 pour les environnements créés avec Java 11, en envoyant un e-mail à [aemcs-java-adopter@adobe.com](mailto:aemcs-java-adopter@adobe.com). Découvrez les [exigences d’exécution de Java 21](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements).

>[!IMPORTANT]
>
> L’**exécution** de Java 21 sera progressivement déployée dans **tous** les environnements (à l’exception de ceux déjà créés avec Java 17 ou 21, qui disposent déjà d’une exécution Java 21), en commençant par les sandbox et le développement/RDE en février, puis l’évaluation/l’exploitation en avril.

### Les programmes de sandbox prennent en charge les pipelines de configuration. {#sandbox-config-pipelines}

Les programmes de sandbox prennent désormais en charge les pipelines de configuration, qui peuvent être configurés dans Cloud Manager pour déployer des fichiers yaml conservés dans Git.

[Découvrez](/help/operations/config-pipeline.md) les pipelines de configuration, qui permettent la configuration du réseau CDN, le transfert de journaux et les tâches de maintenance de purge de version ou de journal d’audit.

### API OpenAPI - Programme d’adoption anticipée {#open-apis-earlyadopter}

Les développeurs et développeuses peuvent intégrer des fonctionnalités AEM as a Cloud Service en profondeur dans leurs propres applications et outils. Les nouvelles API AEM as a Cloud Service suivent la spécification OpenAPI dans le but d’être cohérentes, bien documentées et conviviales. Les informations d’identification des points d’entrée nécessitant une authentification sont générées lors de la création de projets Adobe Developer Console.

Découvrez les [API OpenAPI AEM](/help/implementing/developing/open-api-based-apis.md) et suivez un [tutoriel de bout en bout](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis) illustrant la configuration et l’utilisation.

Concrètement, les points d’entrée d’API répertoriés ci-dessous sont disponibles dans le cadre d’un programme d’adoption précoce. Si cela vous intéresse, envoyez un e-mail à l’adresse [aem-apis@adobe.com](mailto:aem-apis@adobe.com) décrivant comment vous prévoyez de les utiliser.

* [API Sites Content Fragments](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/)
* [API Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/assets/author/)
* API de dossiers Sites et Assets
* [API Forms Communications](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/)

### Edge Computing - Demande de commentaires {#edge-computing-feedback}

L’Edge Computing rapproche le traitement des données du navigateur, ce qui présente des avantages, notamment une latence réduite. Adobe aimerait savoir si cette technologie est utile pour la diffusion de publications AEM et les projets Edge Delivery Services. De plus, faites-nous part de l’utilisation que vous envisagez d’en faire afin de contribuer à la feuille de route du produit. Envoyez un e-mail à [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) contenant des questions et des commentaires.

### Nouvelle AEM Developer Console (version bêta publique) {#aem-developer-console-beta}

Testez une [AEM Developer Console](/help/implementing/developing/introduction/aem-developer-console.md) repensée qui offre une expérience plus interactive pour le débogage du code dans les environnements cloud.

Tout le monde peut accéder à la version Beta publique en cliquant sur le bouton *Nouvelle console disponible* dans la console AEM Developer Console actuelle. Adobe souhaite connaître votre avis. Vous pouvez envoyer vos commentaires par e-mail à [aemcs-new-devconsole-ui-beta@adobe.com](mailto:aemcs-new-devconsole-ui-beta@adobe.com).

## [!DNL Experience Manager] Guides {#guides}

Vous trouverez une liste complète des nouvelles fonctionnalités améliorées de la dernière version d’Adobe Experience Manager Guides [ici](https://experienceleague.adobe.com/fr/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2412-release/fixed-issues-2024-12-0).

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
