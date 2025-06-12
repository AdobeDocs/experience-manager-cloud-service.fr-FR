---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: 75816f35a8bca8356e17b13341c2ddbd850f8eff
workflow-type: tm+mt
source-wordcount: '2077'
ht-degree: 31%

---

# Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour techniques de la version actuelle (la plus récente) d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes, telles que 2023 ou 2024.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Pour recevoir chaque mois une notification par e-mail concernant des informations sur les notes de mise à jour d’Experience Cloud, abonnez-vous aux [Mises à jour de produits prioritaires d’Adobe](https://www.adobe.com/subscription/priority-product-update.html).

## Date de publication {#release-date}


La date de publication de la version actuelle (2025.5.0) d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le vendredi 5 juin 2025. La prochaine mise à jour des fonctionnalités (2025.6.0) est prévue pour le vendredi 26 juin 2025.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

<!-- 

## Release Video {#release-video}

Have a look at the February 2025 Release Overview video for a summary of the features added in the 2025.2.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440920?quality=12)

-->

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

**Métadonnées générées par l’IA**

AEM Assets utilise désormais [AI pour générer automatiquement des métadonnées, y compris le titre, la description et les mots-clés](/help/assets/metadata-assets-view.md#ai-smart-tags). Ces champs générés par l’IA améliorent la précision des métadonnées, ce qui facilite la recherche, la classification et la recommandation des ressources. Cette approche améliore non seulement l’efficacité en éliminant le balisage manuel, mais garantit également la cohérence et l’évolutivité sur de grands volumes de contenu numérique.

![Métadonnées générées par l’IA](/help/assets/assets/enhanced-smart-tags.png)

**Intégration avec Figma**

AEM Assets s’intègre de manière native à Figma, ce qui permet aux concepteurs d’accéder directement aux ressources stockées dans AEM Assets à partir de l’interface utilisateur de Figma. Vous pouvez placer le contenu géré dans AEM Assets dans la zone de travail Figma, puis enregistrer le contenu nouveau ou modifié dans le référentiel AEM Assets. Pour accéder au connecteur AEM Assets disponible sur la page Communauté Figma, cliquez [ici](https://www.figma.com/community/plugin/1512561378275712210/adobe-experience-manager-aem-assets-connector).

>[!VIDEO](https://video.tv.adobe.com/v/3463828)


### Nouvelles fonctionnalités de Content Hub {#new-features-content-hub}

**Contrôle d’accès basé sur les attributs (ABAC)**

[Content Hub vous permet désormais d’appliquer des restrictions basées sur des règles pour accéder aux ressources](/help/assets/attribute-based-access-control.md). Les autorisations des ressources assurent la gouvernance et s’assurent également que seules les ressources appropriées sont accessibles aux utilisateurs.

Les règles de restriction de ressources sont basées sur des métadonnées et si les conditions définies dans la règle correspondent aux métadonnées de la ressource, la ressource est affichée pour les groupes d’utilisateurs.

Voici quelques-uns des principaux avantages du contrôle d’accès basé sur les attributs :

* Élimine la dépendance à la structure de dossiers pour les autorisations

* Permet aux administrateurs de charger des ressources et de déterminer rétroactivement des structures d’autorisation

* Réduit le nombre de doublons - améliore l’intégrité des ressources. Des doublons sont nécessaires dans les autorisations basées sur des dossiers lorsque les mêmes ressources sont partagées avec différents groupes.

**Image de marque de l’interface utilisateur**

Content Hub permet désormais aux administrateurs de [personnaliser l’interface utilisateur avec des éléments spécifiques à la marque](/help/assets/configure-content-hub-ui-options.md##configure-branding-content-hub) tels que des images de bannière, des titres de bannière et du corps de texte, ainsi que des couleurs primaires et secondaires. Ces améliorations permettent d’assurer la cohérence de la marque, de simplifier l’intégration des utilisateurs et d’établir la confiance.

![Image de marque de l’interface utilisateur](/help/assets/assets/content-hub-ui-branding.png)

**Partage de liens public**

Content Hub prend désormais en charge la [génération de liens partageables pour permettre aux utilisateurs externes](/help/assets/share-assets-content-hub.md##share-assets) sans accès aux applications, d’afficher les métadonnées des ressources ou de télécharger des ressources.

![Image de marque de l’interface utilisateur](/help/assets/assets/public-and-private-link.png)

**Gouvernance des collections**

Content Hub vous permet désormais de [contrôler l’accès aux collections lors de leur création, en veillant à ce que seuls les utilisateurs autorisés puissent afficher ou gérer les ressources regroupées](/help/assets/collections-content-hub.md##create-collections). Il garantit une sécurité améliorée, une meilleure collaboration, une gestion des ressources organisée et une gouvernance simplifiée.

>[!VIDEO](https://video.tv.adobe.com/v/3463336)

>[!NOTE]
>
>La gouvernance des collections est une fonctionnalité à disponibilité limitée. Vous pouvez l’activer en créant un ticket d’assistance.

**Télécharger plusieurs ressources au format ZIP**

Content Hub vous permet désormais de [télécharger les ressources sélectionnées et leurs rendus dans un fichier ZIP](/help/assets/download-assets-content-hub.md#download-asset-renditions) et non plus dans des fichiers séparés, ce qui simplifie la gestion des fichiers.

**Rendus Dynamic Media dans Content Hub**

Accédez à tous vos [rendus de paramètres prédéfinis Dynamic Media et recadrages intelligents pour téléchargement, directement depuis l’interface utilisateur de Content Hub](/help/assets/download-assets-content-hub.md#download-asset-renditions).

&#x200B;![Rendus Dynamic Media](/help/assets/assets/dm-renditions-content-hub.png)

### Nouvelles fonctionnalités de Dynamic Media {#new-features-dynamic-media}

**Intégration native de Dynamic Media à AJO B2C&#x200B;**

[Intégration native d’Experience Manager (AEM) Dynamic Media à Journey Optimizer (AJO) B2C](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/content-management/combine/aem-dynamic), ce qui permet aux spécialistes marketing d’incorporer facilement des ressources Dynamic Media AEM (rendu et modèle de gestion de contenu) dans le contenu AJO et de fournir des mises à jour en temps réel et des expériences hyper-personnalisées sur plusieurs canaux.

>[!VIDEO](https://video.tv.adobe.com/v/3457695/?learn=on&enablevpops=&autoplay=true)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Fonctionnalités de version préliminaire

* [Éditeur universel - Fragments de formulaire](/help/edge/docs/forms/universal-editor/creating-form-fragments.md) : l’éditeur universel vous permet désormais de créer et de réutiliser des fragments de formulaire pour le formulaire adaptatif. Ces fragments sont des sections de formulaire réutilisables (par exemple, coordonnées, champs de consentement) qui peuvent être créées une seule fois et appliquées à plusieurs formulaires. Cette fonctionnalité simplifie la création de formulaires, assure la cohérence et améliore l’efficacité de création.

* [Bibliothèque de documents SharePoint - Enregistrer les pièces jointes avec les noms de fichier d’origine](/help/forms/connect-forms-to-sharepoint-document-library.md#connect-an-adaptive-form-to-microsoft-sharepoint-document-library) : vous avez désormais la possibilité d’enregistrer les pièces jointes de formulaire en utilisant leurs noms de fichier d’origine lors de leur stockage dans une bibliothèque de documents SharePoint. Cette amélioration simplifie l’identification et la gestion des fichiers chargés.

* **Éditeur de règles** :
   * [Condition binaire avec événement de clic dans la clause « When »](/help/forms/rule-editor-core-components-events-operators.md#available-operator-types-and-events-in-rule-editor) : l’éditeur de règles permet désormais de combiner un événement de clic de bouton (_Est cliqué_) avec d’autres conditions dans la clause « When ». Cela permet un contrôle plus précis de l’exécution des règles en fonction de l’interaction utilisateur et d’autres facteurs. Remarque : lorsque vous utilisez plusieurs conditions, l’événement de clic doit être la première condition répertoriée.
   * [Conditions de validation des champs et des panneaux](/help/forms/rule-editor-core-components-usecases.md) : l’éditeur de règles inclut désormais les conditions _IsValid_ et _IsNotValid_. Ils vous permettent de vérifier l’état de validation de champs spécifiques ou de panneaux entiers (y compris des dispositions telles que les onglets horizontaux, verticaux, accordéons et assistants), ce qui améliore la navigation dans les formulaires et l’expérience client en fonction des résultats de validation.
* [Amélioration de la gestion de l’étendue pour les listes SharePoint](/help/forms/connect-forms-to-sharepoint-list.md) : les sites SharePoint prennent désormais en charge tous les chemins gérés, par exemple /sites et /team. Cette amélioration permet une intégration plus large entre différentes structures de site SharePoint, offrant ainsi une plus grande flexibilité pour se connecter au contenu organisationnel.
* [Prise en charge de l’enregistrement du document d’enregistrement dans la liste SharePoint](/help/forms/generate-document-of-record-core-components.md#bind-adaptive-form-components-with-template-fields) : les formulaires créés à l’aide d’un modèle de données de formulaire (FDM) basé sur une liste SharePoint peuvent désormais enregistrer le document d’enregistrement (DoR) dans les listes SharePoint en configurant la propriété de champ Référence de liaison de document d’enregistrement. Cette amélioration permet une intégration transparente des données de formulaire et des documents pris en charge avec le stockage SharePoint.

### Fonctionnalités d’accès anticipé d’AEM Forms {#forms-new-early-access-features}

Le programme d’accès anticipé d’AEM Forms vous offre une opportunité unique d’accéder de manière exclusive à des innovations de pointe et de contribuer à façonner leur développement.

Les notes de mise à jour répertorient les innovations apportées à la version actuelle. Pour obtenir la liste complète des innovations disponibles dans le cadre du programme d’accès anticipé, voir [Documentation du programme d’accès anticipé d’AEM Forms](/help/forms/early-access-ea-features.md).

#### Intégration d’Adobe Experience Platform (AEP) à Forms

Les fonctionnalités d’intégration entre Forms et AEP sont désormais disponibles pour les utilisateurs et utilisatrices précoces.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Processus d’obsolescence mis à jour {#updated-deprecation-process}

Adobe examine régulièrement les fonctionnalités, les bibliothèques, les API et les configurations afin de s’assurer qu’elles répondent aux normes de performance, de sécurité et de valeur ajoutée. Lorsque les fonctionnalités ne répondent plus à ces normes, elles sont marquées pour obsolescence et leur utilisation doit s’arrêter à une date de suppression spécifiée. D’ici là, Adobe rappellera aux clients et clientes, par le biais de notifications par e-mail, les actions à entreprendre dans Cloud Manager avant de poursuivre ou de déployer de nouvelles versions. Si vous ne prenez pas les mesures nécessaires, il se peut que vous ne puissiez pas effectuer la mise à niveau vers de nouvelles versions d’AEM, ce qui peut avoir des répercussions sur la sécurité, les performances, la fiabilité et la disponibilité.

Voir l’article [obsolescence](/help/release-notes/deprecated-removed-features.md) pour plus d’informations.

#### API Java obsolètes et configuration OSGi proche des dates de suppression {#deprecated-near-removals}

Développez la liste ci-dessous pour afficher les API et les configurations OSGi obsolètes qui ne doivent plus être utilisées. Pour plus d’informations, y compris sur les délais de suppression, reportez-vous à l’article sur l’obsolescence .

<details>
  <summary>Développez pour afficher les éléments obsolètes.</summary>

API Java :
* `org.apache.sling.commons.auth`
* `org.apache.felix.webconsole`
* `org.eclipse.jetty`
* `com.mongodb`
* `org.apache.abdera`
* `org.apache.felix.http.whiteboard`
* `org.apache.cocoon.xml`
* `ch.qos.logback`
* `org.slf4j.spi`
* `org.slf4j.event`
* `org.apache.log4j`
* `com.google.common`
* `com.drew`
* `org.bson`
* `org.apache.jackrabbit.oak.plugins.blob`
* `org.apache.jackrabbit.oak.plugins.memory`

Propriétés OSGi :

* `org.apache.sling.commons.log.LogManager` (toutes les propriétés)
* `org.apache.sling.commons.log.LogManager.factory.config` (`org.apache.sling.commons.log.file`, `org.apache.sling.commons.log.pattern`)

</details>

### Obsolescence d’exécution Java 11 {#java11-runtime-deprecation}

Le **runtime Java 11** est désormais obsolète et la plupart des environnements ont déjà été mis à niveau vers le **runtime Java 21** plus performant.

Si votre environnement n’a pas pu être mis à niveau en raison de dépendances non prises en charge (voir [Exigences d’exécution Java 21](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements)), vous avez dû recevoir un e-mail d’Adobe contenant les étapes suivantes spécifiques. Veillez à ce que toutes les mises à jour requises soient terminées d’ici le **28 août 2025**, afin que votre environnement puisse être mis à niveau sans interruption.

Remarque : la version d’exécution est distincte de la version de build de votre code. Bien que nous recommandions la création de builds avec Java 21, les builds Java 11 sont toujours pris en charge pour l’instant. Un avis d’obsolescence distinct pour les versions Java 11 sera partagé ultérieurement.

### Application de la politique de configuration des journaux Java AEM {#logconfig-policy}

Comme indiqué dans les notes de mise à jour d’avril, les journaux Java d’AEM doivent suivre un format standard pour assurer une surveillance fiable dans tous les environnements client. Les configurations de journal personnalisées, telles que les modifications apportées au formatage du journal, aux fichiers de sortie ou aux niveaux de journal par défaut, ne sont plus prises en charge. Les journaux doivent rester redirigés vers les fichiers par défaut et les niveaux de journal par défaut du code de produit AEM doivent être conservés. Consultez toutes les informations dans l’article [ Journalisation ](/help/implementing/developing/introduction/logging.md#configuration-loggers).

À compter de **fin août**, tous les remplacements de journalisation personnalisée non pris en charge seront ignorés. D’après notre analyse, la plupart des clients ne seront pas affectés et Adobe contactera directement tous les clients dont la configuration actuelle peut être affectée.

Passez en revue et mettez à jour tous les processus en aval qui reposent sur un comportement de journalisation personnalisé. Par exemple :

* Si votre système de transfert de journal attend un format de journal personnalisé, vous devrez peut-être ajuster vos règles d’ingestion.
* Si vous avez précédemment réduit le niveau de détail du journal en modifiant les niveaux de journal, notez que le retour aux niveaux par défaut peut augmenter le volume du journal.

### Purge par défaut des anciennes versions et des journaux d’audit {#mt-defaults}

Actuellement, les versions de contenu et les journaux d’audit ont leurs *tâches de maintenance de purge* associées désactivées par défaut. Aucune donnée n’est donc supprimée, sauf configuration explicite.

Toutefois, pour optimiser les performances du référentiel, à partir de **fin juin 2025**, la purge sera activée par défaut, en suivant ces instructions :

#### Versions du contenu {#mt-content}

* **Nouveaux environnements** (créés après une date à venir (à communiquer ultérieurement).
   * Les versions de plus de **30 jours** seront régulièrement supprimées.
   * Les cinq versions les plus récentes au cours des 30 derniers jours sont conservées, ainsi que la version la plus récente et la version actuelle, quel que soit leur âge.

* **Environnements existants** (créés avant cette date à venir) :
   * Les versions antérieures à **7 ans** seront régulièrement supprimées.
   * Toutes les versions des 7 dernières années sont conservées.
   * Ce seuil par défaut élevé empêche la suppression involontaire des données récentes. Cependant, il est recommandé de configurer des valeurs plus faibles pour optimiser les performances du référentiel.

* Vous pouvez modifier ces valeurs par défaut via la configuration YAML, déployée à l’aide du pipeline de configuration.

#### Journal d’audit {#mt-auditlogs}

* **Nouveaux environnements** (créés après une date à venir, qui sera communiquée séparément) :
   * Les journaux d’audit de réplication, de gestion des ressources numériques et de page datant de plus de 7 **jours** seront régulièrement supprimés.
   * Tous les événements sont consignés par défaut.

* **Environnements existants** (créés avant cette date à venir) :
   * **Les journaux d’audit de réplication, de gestion des ressources numériques et de pages de plus de 7 ans** seront régulièrement supprimés.
   * Tous les événements sont consignés par défaut.
   * Ce seuil par défaut élevé empêche la suppression involontaire des données récentes. Cependant, il est recommandé de configurer des valeurs plus faibles pour optimiser les performances du référentiel.

* Vous pouvez modifier ces valeurs par défaut via la configuration YAML, déployée à l’aide du pipeline de configuration.

Pour plus d’informations, consultez l’article [ Tâches de maintenance ](/help/operations/maintenance.md#defaults).

### Edge Computing (Programme Alpha) {#edge-computing}

L’informatique Edge vous permet d’exécuter JavaScript sur la couche CDN, ce qui rapproche le traitement des données de l’utilisateur final. Cela réduit la latence et permet d’obtenir des expériences réactives et dynamiques en périphérie.

Cas d’utilisation courants :

* Authentifier les utilisateurs auprès d’un fournisseur d’identité avant d’accorder l’accès au contenu
* Personnalisation du contenu en fonction de la géolocalisation, du type d’appareil ou des attributs utilisateur
* Agir comme middleware entre le réseau CDN et votre origine
* Reformatage des réponses d’API tierces (et éventuellement agrégation de plusieurs réponses d’API) avant de les diffuser au navigateur
* Composer et diffuser des HTML générées par serveur en périphérie à l’aide de contenu assemblé à partir de divers serveurs principaux

Nous disposons d’un nombre limité d’opportunités pour la diffusion de l’instance de publication AEM ou les projets Edge Delivery Services pour les sites de production en direct. Si vous souhaitez participer ou en savoir plus, veuillez envoyer un e-mail à [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) avec une brève description de votre cas d’utilisation.

### Configuration du réseau CDN pour Edge Delivery Services (programme Beta) {#cdn-eds-beta}

Le réseau CDN géré par Adobe offre des options de configuration flexibles, comme décrit dans l’article [Configurer le pipeline](/help/operations/config-pipeline.md#configurations).

Désormais en version bêta, déployez un pipeline de configuration pour des fonctionnalités telles que les sélecteurs d’origine du réseau CDN, les transformations de réponse et de requête, etc. Veuillez contacter [aemcs-cdn-config-adopter@adobe.com](mailto:aemcs-cdn-config-adopter@adobe.com) avec les détails de votre cas d&#39;utilisation.

### Transfert du journal AEM vers d’autres destinations (programme Beta) {#log-forwarding-beta}

Bien que les journaux puissent être téléchargés depuis Cloud Manager, de nombreuses organisations préfèrent diffuser ces journaux vers une destination de journalisation spécifique. AEM prend déjà en charge le transfert des journaux AEM et CDN vers Azure Blob Storage, Datadog, HTTPS, Elasticsearch (et OpenSearch) et Splunk. Cette fonctionnalité est configurée en libre-service et déployée à l’aide du pipeline de configuration.

Désormais, en version bêta, vous pouvez transférer les journaux AEM vers Amazon S3, Sumo Logic et votre propre compte New Relic (et non le compte fourni par Adobe). Notez que les journaux AEM (y compris Apache/Dispatcher) sont pris en charge pour ces destinations de journalisation, mais pas les journaux CDN. Envoyer un e-mail à l’adresse [aemcs-logforwarding-beta@adobe.com](mailto:aemcs-logforwarding-beta@adobe.com) pour obtenir l’accès.

Pour en savoir plus, consultez la [documentation sur le transfert de journaux](/help/implementing/developing/introduction/log-forwarding.md).

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
