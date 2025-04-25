---
title: Notes de mise à jour de la version 2025.3.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la version 2025.3.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
feature: Release Information
role: Admin
source-git-commit: b1a551aeebd0b3c5cf8111bf30341bd4ac41536f
workflow-type: tm+mt
source-wordcount: '1099'
ht-degree: 100%

---

# Notes de mise à jour de la version 2025.3.0 d’[!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour de la version 2025.3.0 d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes, telles que 2023 ou 2024.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Pour recevoir chaque mois une notification par e-mail concernant des informations sur les notes de mise à jour d’Experience Cloud, abonnez-vous aux [Mises à jour de produits prioritaires d’Adobe](https://www.adobe.com/subscription/priority-product-update.html).

## Date de publication {#release-date}

La date de publication de la version actuelle d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2025.3.0) est le 27 mars 2025. La prochaine disponibilité des fonctionnalités (2025.4.0) est prévue pour le 24 avril 2025.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

<!-- 

## Release Video {#release-video}

Have a look at the February 2025 Release Overview video for a summary of the features added in the 2025.2.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440920?quality=12)

-->

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de Dynamic Media {#new-features-dynamic-media}

**Prise en charge des formes longues pour les vidéos diffusées à l’aide de Dynamic Media avec OpenAPI**

Dynamic Media avec OpenAPI prend désormais en charge les vidéos de forme longue. Les vidéos de forme longue peuvent prendre en charge jusqu’à 50 Go et 2 heures.

### Dynamic Media Classic {#dmc}

<!-- CARRY OVER TO APRIL 2025 RELEASE NOTES -->

L’onglet Bande passante du tableau de bord de création de rapports Dynamic Media Classic n’est plus pris en charge depuis avril 2025.

Consultez [Bande passante et stockage, types de rapports](https://experienceleague.adobe.com/fr/docs/dynamic-media-classic/using/setup/administration-setup#types-of-reports).


## Nouvelles fonctionnalités de la vue Assets {#new-features-assets-view}


**Prise en charge des balises racines**

AEM Assets prend désormais en charge le mappage d’une propriété de balise dans un formulaire de métadonnées vers des métadonnées personnalisées. En outre, l’équipe d’administration peut limiter la disponibilité des balises pour les personnes en limitant l’accès à une balise racine spécifique et aux balises qui existent sous la balise racine.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Fonctionnalités d’accès anticipé dans AEM Forms {#forms-new-early-access-features}

Le programme d’accès anticipé d’AEM Forms vous offre une opportunité unique d’accéder de manière exclusive à des innovations de pointe et de contribuer à façonner leur développement.

Les notes de mise à jour répertorient les innovations apportées à la version actuelle. Pour obtenir la liste complète des innovations disponibles dans le cadre du programme d’accès anticipé, voir [Documentation du programme d’accès anticipé d’AEM Forms](/help/forms/early-access-ea-features.md).

#### Modèles d’e-mail HTML dans les formulaires adaptatifs

Les formulaires adaptatifs vous permettent d’utiliser des [modèles d’e-mail HTML](/help/forms/html-email-templates-in-adaptive-forms.md). Les modèles d’e-mail HTML vous permettent d’envoyer des e-mails enrichis, personnalisés et visuellement attrayants lorsqu’un formulaire est envoyé. Ces e-mails peuvent être personnalisés avec des données de formulaire et améliorés à l’aide de différentes balises d’e-mail, telles que des images et des liens. Avec les formulaires adaptatifs, vous pouvez charger un fichier contenant un modèle HTML ou utiliser un éditeur de texte brut pour créer ces modèles.

![Modèle d’e-mail HTML](/help/forms/assets/html-email.png)

#### Amélioration de la prise en charge de l’espace de stockage dans le cloud : chargement direct de PDF vers le stockage Blob Azure

Les API de génération de documents AEM Forms permettent désormais de [charger directement les documents PDF générés](/help/forms/early-access-ea-features.md#doc-generation-api) vers le stockage Azure Blob. Cette amélioration simplifie le stockage et la récupération, améliorant l’efficacité et l’intégration aux workflows cloud.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Prise en charge de Java 21 {#java21}

Depuis la version de janvier, vous pouvez créer du code avec Java 21 et Java 17. Vous avez accès à de nouvelles fonctionnalités telles que la correspondance de motifs, les classes scellées et diverses améliorations des performances. Pour connaître les étapes de configuration, notamment la mise à jour des versions de votre projet Maven et de votre bibliothèque, consultez l’article [Environnement de création](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#using-java-support).

L’**exécution** de Java 21 la plus performante est automatiquement déployée lorsqu’une version Java 17 ou 21 est détectée. Cependant, Adobe recommande également d’opter pour l’exécution de Java 21 pour les environnements créés avec Java 11, en envoyant un e-mail à [aemcs-java-adopter@adobe.com](mailto:aemcs-java-adopter@adobe.com). Découvrez les [exigences d’exécution de Java 21](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements).

>[!IMPORTANT]
>
> L’**exécution** Java 21 a été déployée dans vos environnements de développement/RDE en février. Elle sera appliquée à vos environnements d’évaluation/de production les **28 et 29 avril**. Notez que la **création de code** avec Java 21 (ou Java 17) est indépendante de l’exécution Java 21. Vous devez engager des mesures explicites pour créer du code avec Java 21 (ou Java 17).

### Transfert de journal AEM vers d’autres destinations - Programme bêta {#log-forwarding-earlyadopter}

Avec la version bêta, vous pouvez désormais transférer les journaux AEM vers New Relic (à l’aide de HTTPS), Amazon S3 et Sumo Logic. Notez que les journaux AEM (y compris Apache/Dispatcher) sont pris en charge, contrairement aux journaux de réseau CDN. Envoyer un e-mail à l’adresse [aemcs-logforwarding-beta@adobe.com](mailto:aemcs-logforwarding-beta@adobe.com) pour obtenir l’accès.

Bien que les journaux puissent être téléchargés depuis Cloud Manager, de nombreuses organisations préfèrent diffuser ces journaux vers une destination de journalisation spécifique. AEM prend déjà en charge le transfert de journaux AEM (disponibilité générale) et de réseau CDN vers Azure Blob Storage, Datadog, HTTPS, Elasticsearch (et OpenSearch) et Splunk. Cette fonctionnalité est configurée en libre-service et déployée à l’aide du pipeline de configuration.

Pour en savoir plus, consultez la [documentation sur le transfert de journaux](/help/implementing/developing/introduction/log-forwarding.md).

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

Découvrez les [API OpenAPI AEM](/help/implementing/developing/open-api-based-apis.md) et suivez un [tutoriel de bout en bout](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/aem-apis/openapis/invoke-api-using-oauth-s2s) illustrant la configuration et l’utilisation.

Concrètement, les points d’entrée d’API répertoriés ci-dessous sont disponibles dans le cadre d’un programme d’adoption précoce. Si cela vous intéresse, envoyez un e-mail à l’adresse [aem-apis@adobe.com](mailto:aem-apis@adobe.com) décrivant comment vous prévoyez de les utiliser.

* [API Sites Content Fragments](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/)
* [API Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/assets/author/)
* [API Sites and Assets Folders](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/folders/)
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
