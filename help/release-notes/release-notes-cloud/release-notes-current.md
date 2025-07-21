---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: 83aceb71ead66763b94ec523c9d9c76c4286c762
workflow-type: tm+mt
source-wordcount: '1810'
ht-degree: 100%

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

La date de publication de la version actuelle (2025.6.0) d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le 26 juin 2025. La prochaine disponibilité des fonctionnalités (2025.7.0) est prévue pour le vendredi 7 août 2025.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

<!-- 

## Release Video {#release-video}

Have a look at the February 2025 Release Overview video for a summary of the features added in the 2025.2.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440920?quality=12)

-->

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

**Gestion améliorée des formulaires de métadonnées dans la vue Assets**

Vous pouvez désormais importer des formulaires de métadonnées de la vue Administration directement dans la vue Assets. Toutes les mises à jour apportées à ces formulaires dans la vue Assets sont automatiquement répercutées dans la vue Administration, ce qui garantit la cohérence entre les deux expériences. Cette fonctionnalité permet une transition transparente vers la nouvelle vue Assets, tout en maintenant la continuité avec vos configurations de métadonnées existantes.

![Métadonnées générées par l’IA](/help/assets/assets/import-metadata-forms-page.png)

### Nouvelles fonctionnalités dans Content Hub {#new-features-content-hub}

**Gouvernance des collections**

Le hub de contenus permet désormais de [contrôler l’accès aux collections lors de leur création, en veillant à ce que seuls les utilisateurs et utilisatrices autorisés puissent afficher ou gérer les ressources regroupées](/help/assets/collections-content-hub.md##create-collections). Il garantit l’amélioration de la sécurité et de la collaboration, une gestion des ressources organisée et une gouvernance simplifiée.

>[!VIDEO](https://video.tv.adobe.com/v/3463336)


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

* [Éditeur universel pour les formulaires adaptatifs et les fragments de formulaire](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) : l’éditeur universel prend désormais en charge la création de formulaires adaptatifs et de fragments de formulaire réutilisables. Les auteurs et autrices peuvent créer des formulaires visuellement, configurer des actions d’envoi et ajouter une validation reCAPTCHA, le tout dans un environnement de création WYSIWYG simplifié. Cette fonctionnalité accélère la création de formulaires, améliore la cohérence et accroît la protection contre le spam et les abus automatisés.

### Fonctionnalités de version préliminaire

* [Générer et synchroniser les rendus AFP à partir de formulaires adaptatifs](/help/forms/document-generation-afp-api.md) : l’API de synchronisation de sortie AFP permet aux administrateurs, aux administratrices, aux utilisateurs et aux utilisatrices de générer une sortie AFP (présentation de fonction avancée) à partir de formulaires adaptatifs et de synchroniser la sortie avec des systèmes ou des emplacements de stockage externes. AFP est un format de document haute performance optimisé pour l’impression, souvent utilisé dans les environnements d’entreprise à grande échelle.

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

* [Intégration d’AEM Forms à Adobe Experience Platform](/help/forms/aem-forms-aep-connector.md) : le connecteur AEM Forms vers Adobe Experience Platform permet une intégration transparente entre les formulaires adaptatifs et Adobe Experience Platform. Cette fonctionnalité permet de mapper les données de formulaire aux schémas XDM et de les envoyer directement à AEP en temps réel. Il rationalise la capture de données pour les cas d’utilisation de personnalisation et d’activation dans les solutions Adobe Experience Cloud.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Processus d’obsolescence mis à jour {#updated-deprecation-process}

Adobe passe régulièrement en revue les fonctionnalités, les bibliothèques, les API et les configurations afin de s’assurer qu’elles répondent aux normes de performances, de sécurité et de valeur. Lorsque les fonctionnalités ne répondent plus à ces normes, elles sont marquées pour obsolescence et vous devez cesser de les utiliser à la date de suppression spécifiée. D’ici là, Adobe rappellera aux clientes et clients, par le biais de notifications par e-mail, les actions à entreprendre dans Cloud Manager avant de poursuivre ou de déployer de nouvelles versions. Si vous ne prenez pas les mesures nécessaires, il se peut que vous ne puissiez pas effectuer la mise à niveau vers de nouvelles versions d’AEM, ce qui peut avoir des répercussions sur la sécurité, les performances, la fiabilité et la disponibilité.

Pour plus d’informations, consultez l’[article sur l’obsolescence](/help/release-notes/deprecated-removed-features.md).

#### API Java obsolètes et configuration OSGi proche des dates de suppression {#deprecated-near-removals}

Développez la liste ci-dessous pour afficher les API et les configurations OSGi obsolètes qui ne doivent plus être utilisées. Pour plus d’informations, y compris concernant les délais de suppression, reportez-vous à l’article sur l’obsolescence.

<details>
  <summary>Développer pour afficher les éléments obsolètes</summary>

API Java :
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

Propriétés OSGi :

* `org.apache.sling.commons.log.LogManager` (toutes les propriétés)
* `org.apache.sling.commons.log.LogManager.factory.config` (`org.apache.sling.commons.log.file`, `org.apache.sling.commons.log.pattern`)

</details>

### Obsolescence de l’exécution Java 11 {#java11-runtime-deprecation}

L’**exécution Java 11** est désormais obsolète et la plupart des environnements ont déjà été mis à niveau vers l’**exécution Java 21** plus performante.

Si votre environnement n’a pas pu être mis à niveau en raison de dépendances non prises en charge (voir les [Exigences d’exécution Java 21](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements)), vous avez dû recevoir un e-mail d’Adobe contenant les étapes spécifiques à réaliser. Veillez à ce que toutes les mises à jour requises soient terminées d’ici le **28 août 2025**, afin que votre environnement puisse être mis à niveau sans interruption.

Remarque : la version de l’exécution est distincte de la version de build de votre code. Bien que nous recommandions la création de versions avec Java 21, les versions Java 11 sont toujours prises en charge pour l’instant. Un avis d’obsolescence distinct pour les versions Java 11 sera partagé ultérieurement.

### Application de la politique de configuration des journaux AEM Java {#logconfig-policy}

Comme indiqué dans les notes de mise à jour d’avril, les journaux Java d’AEM doivent respecter un format standard pour assurer une surveillance fiable dans tous les environnements de la clientèle. Les configurations de journal personnalisées, telles que les modifications apportées à la mise en forme du journal, aux fichiers de sortie ou aux niveaux de journal par défaut, ne sont plus prises en charge. Les journaux doivent rester dirigés vers les fichiers par défaut et les niveaux de journal par défaut du code de produit AEM doivent être conservés. Consultez toutes les informations dans [l’article Journalisation](/help/implementing/developing/introduction/logging.md#configuration-loggers).

À compter de **fin août**, tous les remplacements de journalisation personnalisée non pris en charge seront ignorés. D’après notre analyse, la plupart des clientes et clients ne seront pas affectés et Adobe a contacté ceux dont la configuration actuelle peut être affectée.

Passez en revue et mettez à jour tous les processus en aval qui reposent sur un comportement de journalisation personnalisé. Par exemple :

* Si votre système de transfert de journal attend un format de journal personnalisé, vous devrez peut-être adapter vos règles d’ingestion.
* Si vous avez précédemment réduit le niveau de détail du journal en modifiant les niveaux de journal, sachez que le retour aux niveaux par défaut peut augmenter le volume du journal.

### Purge par défaut des anciennes versions et des journaux d’audit {#mt-defaults}

Actuellement, les *tâches de maintenance de purge* des versions de contenu et des journaux d’audit sont désactivées par défaut. Par conséquent, les données ne sont supprimées, sauf si elles sont configurées explicitement..

Toutefois, pour optimiser les performances du référentiel, à compter de **début juillet 2025**, la purge sera activée par défaut, en suivant ces directives :

#### Versions du contenu {#mt-content}

* **Nouveaux environnements** (créés après une date à venir, qui sera communiquée ultérieurement)
   * Les versions de plus de **30 jours** seront régulièrement supprimées.
   * Les cinq versions les plus récentes des 30 derniers jours sont conservées, tout comme la version la plus récente et la version actuelle, quel que soit leur ancienneté.

* **Environnements existants** (créés avant cette date à venir) :
   * Les versions antérieures à **7 ans** seront régulièrement supprimées.
   * Toutes les versions des 7 dernières années sont conservées.
   * Ce seuil élevé par défaut empêche la suppression involontaire de données récentes. Cependant, il est recommandé de configurer des valeurs plus faibles pour optimiser les performances du référentiel.

* Vous pouvez modifier ces valeurs par défaut via la configuration YAML, déployée à l’aide du pipeline de configuration.

#### Journal d’audit {#mt-auditlogs}

* **Nouveaux environnements** (créés après une date à venir, qui sera communiquée séparément) :
   * Les journaux d’audit de réplication, de gestion des ressources numériques et de page datant de plus de **7 jours** seront régulièrement supprimés.
   * Tous les événements sont consignés par défaut.

* **Environnements existants** (créés avant cette date à venir) :
   * Les journaux d’audit de réplication, de gestion des ressources numériques et de page datant de plus de **7 ans** seront régulièrement supprimés.
   * Tous les événements sont consignés par défaut.
   * Ce seuil élevé par défaut empêche la suppression involontaire de données récentes. Cependant, il est recommandé de configurer des valeurs plus faibles pour optimiser les performances du référentiel.

* Vous pouvez modifier ces valeurs par défaut via la configuration YAML, déployée à l’aide du pipeline de configuration.

Pour plus d’informations, voir l’[article Tâches de maintenance](/help/operations/maintenance.md#defaults).

### Informatique de périphérie (programme Alpha) {#edge-computing}

L’informatique de périphérie permet d’exécuter JavaScript sur la couche de réseau CDN, ce qui rapproche le traitement des données de l’utilisateur final ou l’utilisatrice finale. Cela réduit la latence et permet d’obtenir des expériences réactives et dynamiques en périphérie.

Cas d’utilisation courants :

* Authentification des utilisateurs et utilisatrices auprès d’un fournisseur d’identités avant d’accorder l’accès au contenu
* Personnalisation du contenu en fonction de la géolocalisation, du type d’appareil ou des attributs d’utilisateur ou d’utilisatrice
* Fonctionnement en tant que middleware entre le réseau CDN et votre origine
* Remise en forme des réponses d’API tierces (et éventuellement agrégation de plusieurs réponses d’API) avant de les diffuser au navigateur
* Composition et diffusion de HTML rendu sur le serveur en périphérie à l’aide de contenu assemblé à partir de divers serveurs principaux

Nous disposons d’un nombre limité d’opportunités pour la diffusion de l’instance de publication AEM ou les projets Edge Delivery Services pour les sites de production en direct. Si vous souhaitez participer ou en savoir plus, adressez un e-mail à [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) avec une brève description de votre cas d’utilisation.

### Configuration du réseau CDN pour Edge Delivery Services (programme bêta) {#cdn-eds-beta}

Le réseau CDN géré par Adobe offre des options de configuration flexibles, comme indiqué dans l’article [Configurer le pipeline](/help/operations/config-pipeline.md#configurations).

Désormais, en version bêta, déployez un pipeline de configuration pour des fonctionnalités telles que les sélecteurs d’origine du réseau CDN, les transformations de réponse et de requête, etc. Contactez [aemcs-cdn-config-adopter@adobe.com](mailto:aemcs-cdn-config-adopter@adobe.com) avec les détails de votre cas d’utilisation.

### Transfert de journal AEM vers d’autres destinations (Programme bêta) {#log-forwarding-beta}

Bien que les journaux puissent être téléchargés depuis Cloud Manager, de nombreuses organisations préfèrent diffuser ces journaux vers une destination de journalisation spécifique. AEM prend déjà en charge le transfert de journaux AEM et de réseau CDN vers Azure Blob Storage, Datadog, HTTPS, Elasticsearch (et OpenSearch) et Splunk. Cette fonctionnalité est configurée en libre-service et déployée à l’aide du pipeline de configuration.

Désormais, en version bêta, vous pouvez transférer les journaux AEM vers Amazon S3, Sumo Logic et votre propre compte New Relic (et non le compte fourni par Adobe). Notez que les journaux AEM (y compris Apache/Dispatcher) sont pris en charge pour ces destinations de journalisation, contrairement aux journaux de réseau CDN. Envoyez un e-mail à l’adresse [aemcs-logforwarding-beta@adobe.com](mailto:aemcs-logforwarding-beta@adobe.com) pour obtenir l’accès.

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
