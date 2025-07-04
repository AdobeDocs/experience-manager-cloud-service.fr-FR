---
title: Notes de mise à jour de la version 2025.2.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la version 2025.2.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
feature: Release Information
role: Admin
exl-id: b893663d-35f1-43ae-a029-4c249b117f2d
source-git-commit: 403ffbede5438131d0b0e770215b990e2d16c018
workflow-type: tm+mt
source-wordcount: '1527'
ht-degree: 96%

---

# Notes de mise à jour de la version 2025.2.0 d’[!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour de la version 2025.2.0 d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes, telles que 2023 ou 2024.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Pour recevoir chaque mois une notification par e-mail concernant des informations sur les notes de mise à jour d’Experience Cloud, abonnez-vous aux [Mises à jour de produits prioritaires d’Adobe](https://www.adobe.com/subscription/priority-product-update.html).

## Date de publication {#release-date}

La date de publication de la version actuelle d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2025.2.0) est le 4 mars 2025. La prochaine disponibilité des fonctionnalités (2025.3.0) est prévue pour le 27 mars 2025.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

## Vidéo de mise à jour {#release-video}

Consultez la vidéo Aperçu de la mise à jour de février 2025 pour un résumé des fonctionnalités ajoutées dans la version 2025.2.0 :

>[!VIDEO](https://video.tv.adobe.com/v/3458080?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités d’AEM Sites {#new-features-sites}

**Balisage automatique des fragments de contenu**

Lors de la création de fragments de contenu, il est désormais possible d’hériter automatiquement des balises affectées au modèle de contenu. Cela permet une classification automatique puissante du contenu stocké dans les fragments de contenu.

**Prise en charge de l’UUID des fragments de contenu**

La prise en charge de l’UUID des fragments de contenu est désormais généralement disponible. La nouvelle fonctionnalité ne modifie pas le comportement basé sur les chemins d’accès des opérations dans AEM, telles que le déplacement, le renommage et le déploiement, où les chemins d’accès sont automatiquement ajustés. Elle peut toutefois faciliter et stabiliser la consommation externe des fragments de contenu, en particulier lors de l’utilisation de requêtes GraphQL qui ciblent directement des fragments individuels avec des requêtes ByPath. Ces requêtes peuvent être interrompues si le chemin d’accès d’un fragment change. Lors de l’utilisation du nouveau type de requête ById, la requête reste stable, car l’UUID d’un fragment ne change pas dans les cas où les chemins d’accès sont modifiés.

**Dynamic Media avec prise en charge d’OpenAPI dans l’éditeur de fragments de contenu et GraphQL**

Les ressources stockées dans des programmes AEM as a Cloud Service différents des fragments de contenu et qui sont activées avec la nouvelle fonctionnalité Dynamic Media avec OpenAPI, peuvent désormais être utilisées dans les fragments de contenu. Le sélecteur d’images dans le nouvel éditeur de fragment de contenu permet désormais de sélectionner des référentiels « distants » en tant que source des ressources d’image à référencer dans le fragment. Lors de la diffusion de ces fragments de contenu à l’aide d’AEM GraphQL, la réponse JSON inclut désormais les propriétés requises pour les ressources distantes (assetId, repositoryId) afin que les applications clientes puissent créer des médias dynamiques respectifs avec des URL OpenAPI pour récupérer l’image.

**Déploiement de l’éditeur de fragments de contenu**

Nous continuerons à activer le nouvel [Éditeur de fragment de contenu](/help/sites-cloud/administering/content-fragments/authoring.md) dans AEM as a Cloud Service, à l’aide de [Unified Shell](/help/overview/aem-cloud-service-on-unified-shell.md) (à l’aide de l’interface utilisateur Spectrum). Après être devenu la valeur par défaut pour tous les environnements de développement Cloud Service en novembre 2024, l’éditeur sera défini par défaut pour tous les environnements d’évaluation le 1er avril 2025 et pour tous les environnements de production le 1er mai 2025. Dans tous les cas, les utilisateurs et utilisatrices auront toujours la possibilité de revenir à l’éditeur de fragments de contenu traditionnel dans l’IU tactile d’AEM.

**API Translation HTTP**

L’API REST AEM Translation HTTP, en mode d’adoption précoce depuis un certain temps, est désormais généralement disponible. La documentation se trouve [ici.](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/translation/) L’API permet d’automatiser les étapes requises dans le processus de gestion de traduction du contenu dans AEM.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités d’AEM Assets {#new-features-assets}

**Nouvelle structure de package Dynamic Media**

Une structure de package Dynamic Media actualisée est désormais disponible pour mieux s’aligner sur les attentes du marché et prendre en charge le suivi. La nouvelle structure de package comprend :

* Dynamic Media Prime, qui inclut Dynamic Media avec des API ouvertes et des vidéos pour améliorer la diffusion.

* Dynamic Media Ultimate, qui ajoute des fonctionnalités de diffusion et de transformation pour répondre aux besoins d’utilisation les plus exigeants.

Vous devez disposer d’Assets as a Cloud Service Prime ou Ultimate pour bénéficier de la nouvelle structure de package.

**Sous-titres vidéo générés par l’IA**

Adobe Dynamic Media utilise l’intelligence artificielle pour générer automatiquement des sous-titres pour le contenu vidéo. Cette fonctionnalité est conçue pour améliorer l’accessibilité et l’expérience d’utilisation en fournissant des sous-titres précis. Les sous-titres sont générés à partir de l’audio original, de pistes audio supplémentaires ou de sous-titres supplémentaires fournis dans l’onglet « Sous-titres et audio » de la page des propriétés vidéo. Avec une prise en charge de plus de 60 langues, les sous-titres peuvent être examinés et prévisualisés avant de publier la vidéo.

**Personnaliser les filtres de recherche**

Les filtres de recherche personnalisés améliorent la précision et l’efficacité de la recherche d’informations pertinentes. Ils permettent des recherches plus personnalisées, en filtrant les données en fonction d’attributs spécifiques tels que la marque, le produit, la catégorie ou d’autres identifiants clés. Cela améliore l’organisation, réduit le temps passé à analyser des résultats non pertinents et permet une prise de décision plus rapide. Ils prennent également en charge l’évolutivité, car les jeux de données volumineux deviennent plus faciles à parcourir et à analyser.

![Personnaliser les filtres de recherche](/help/assets/assets/custom-search-filters.png)

### Fonctionnalités d’accès anticipé dans le hub de contenus {#early-access-content-hub}

Le hub de contenus vous permet désormais d’afficher et de télécharger des rendus de recadrage dynamique et intelligent en plus des rendus statiques existants. En tant qu’administrateur ou administratrice du hub de contenus, vous pouvez également configurer la disponibilité de ces rendus pour les utilisateurs et utilisatrices à l’aide de l’interface d’utilisation de configuration.

![Rendus dynamiques](/help/assets/assets/download-single-asset-renditions-dynamic.png)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Fonctionnalités d’accès anticipé dans AEM Forms {#forms-new-early-access-features}

Le programme d’accès anticipé d’AEM Forms vous offre une opportunité unique d’accéder de manière exclusive à des innovations de pointe et de contribuer à façonner leur développement.

Les notes de mise à jour répertorient les innovations apportées à la version actuelle. Pour obtenir la liste complète des innovations disponibles dans le cadre du programme d’accès anticipé, voir [Documentation du programme d’accès anticipé d’AEM Forms](/help/forms/early-access-ea-features.md).

#### Modèles d’e-mail HTML dans les formulaires adaptatifs

Les formulaires adaptatifs vous permettent d’utiliser des [modèles d’e-mail HTML](/help/forms/html-email-templates-in-adaptive-forms.md). Les modèles d’e-mail HTML vous permettent d’envoyer des e-mails enrichis, personnalisés et visuellement attrayants lorsqu’un formulaire est envoyé. Ces e-mails peuvent être personnalisés avec des données de formulaire et améliorés à l’aide de différentes balises d’e-mail, telles que des images et des liens. Avec les formulaires adaptatifs, vous pouvez charger un fichier contenant un modèle HTML ou utiliser un éditeur de texte brut pour créer ces modèles.

![Modèle d’e-mail HTML](/help/forms/assets/html-email.png)

#### Amélioration de la prise en charge de l’espace de stockage dans le cloud : chargement direct de PDF vers le stockage Blob Azure

Les API de génération de documents AEM Forms vous permettent désormais de [charger directement les documents PDF générés](/help/forms/early-access-ea-features.md#doc-generation-api) vers le stockage Blob Azure. Cette amélioration simplifie le stockage et la récupération, améliorant l’efficacité et l’intégration aux workflows cloud.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Prise en charge de Java 21 {#java21}

Comme mentionné dans les notes de mise à jour de janvier, vous pouvez désormais créer du code avec Java 21, qui inclut de nouvelles fonctionnalités (par exemple, la correspondance de modèles pour les instructions switch, les classes scellées, etc.) et des améliorations de performances. Les versions Java 17 sont également prises en charge. Pour connaître les étapes de configuration, notamment la mise à jour des versions de votre projet Maven et de votre bibliothèque, voir l’article [Environnement de création](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#using-java-support).

L’**exécution** de Java 21 la plus performante sera automatiquement déployée lorsqu’une version Java 17 ou 21 est détectée. Cependant, nous vous recommandons également d’opter pour l’exécution de Java 21 pour les environnements créés avec Java 11, en envoyant un e-mail à [aemcs-java-adopter@adobe.com](mailto:aemcs-java-adopter@adobe.com). Découvrez les [exigences d’exécution de Java 21](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements).

>[!IMPORTANT]
>
> En février, l’**exécution** Java 21 a été déployée dans les environnements de développement/RDE (en dehors de ceux déjà créés avec Java 17 ou 21, qui disposent déjà d’une exécution Java 21). Java 21 sera appliqué aux environnements d’évaluation/de production en avril.

### Edge Computing - Demande de commentaires {#edge-computing-feedback}

L’Edge Computing rapproche le traitement des données du navigateur, ce qui présente des avantages, notamment une latence réduite. Adobe aimerait savoir si cette technologie est utile pour la diffusion de publications AEM et les projets Edge Delivery Services. De plus, faites-nous part de l’utilisation que vous envisagez d’en faire afin de contribuer à la feuille de route du produit.

Exemples de cas d’utilisation possibles :
* Authentification avec un IdP pour accéder au contenu
* Rendu d’un contenu dynamique (personnalisé, localisé) en fonction de la géolocalisation, du type d’appareil, des attributs de l’utilisateur ou de l’utilisatrice, etc.
* Manipulation d’image avancée
* Middleware entre le réseau CDN et une origine
* Couche entre le navigateur et une API tierce, peut-être pour reformater la réponse de l’API
* Agrégation des données provenant de plusieurs origines afin de faciliter leur rendu par le navigateur client

Envoyez un e-mail à [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) avec vos questions et commentaires.

### API OpenAPI - Programme d’adoption anticipée {#open-apis-earlyadopter}

Les développeurs et développeuses peuvent intégrer des fonctionnalités AEM as a Cloud Service en profondeur dans leurs propres applications et outils. Les nouvelles API AEM as a Cloud Service suivent la spécification OpenAPI dans le but d’être cohérentes, bien documentées et conviviales. Les informations d’identification des points d’entrée nécessitant une authentification sont générées lors de la création de projets Adobe Developer Console.

Découvrez les [API OpenAPI AEM](/help/implementing/developing/open-api-based-apis.md) et suivez un [tutoriel de bout en bout](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis) illustrant la configuration et l’utilisation.

Concrètement, les points d’entrée d’API répertoriés ci-dessous sont disponibles dans le cadre d’un programme d’adoption précoce. Si cela vous intéresse, envoyez un e-mail à l’adresse [aem-apis@adobe.com](mailto:aem-apis@adobe.com) décrivant comment vous prévoyez de les utiliser.

* [API Sites Content Fragments](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/)
* [API Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/assets/author/)
* API de dossiers Sites et Assets
* [API Forms Communications](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/)

### Nouvelle AEM Developer Console (version bêta publique) {#aem-developer-console-beta}

Testez une [AEM Developer Console](/help/implementing/developing/introduction/aem-developer-console.md) repensée qui offre une expérience plus interactive pour le débogage du code dans les environnements cloud.

Tout le monde peut accéder à la version Beta publique en cliquant sur le bouton *Nouvelle console disponible* dans la console AEM Developer Console actuelle. Adobe souhaite connaître votre avis. Vous pouvez envoyer vos commentaires par e-mail à [aemcs-new-devconsole-ui-beta@adobe.com](mailto:aemcs-new-devconsole-ui-beta@adobe.com).

## [!DNL Experience Manager] Guides {#guides}

Vous trouverez une liste complète des nouvelles fonctionnalités améliorées de la dernière version d’Adobe Experience Manager Guides [ici](https://experienceleague.adobe.com/fr/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2025-releases/2502-release/whats-new-2025-02-0).

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
