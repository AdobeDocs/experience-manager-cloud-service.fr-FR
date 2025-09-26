---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: 3eda41b89847e1011d818922826b745b880e4977
workflow-type: tm+mt
source-wordcount: '1905'
ht-degree: 48%

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

La date de publication de la version actuelle (2025.9.0) d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le vendredi 25 septembre 2025. La prochaine disponibilité des fonctionnalités (2025.10.0) est prévue pour le vendredi 30 octobre 2025.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

<!-- 

## Release Video {#release-video}

Have a look at the July 2025 Release Overview video for a summary of the features added in the 2025.7.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440920?quality=12)

-->

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités de la version préliminaire de Experience Manager Sites {#prerelease-sites}

L’éditeur de modèle de contenu pour les fragments de contenu AEM a été modernisé afin de s’aligner sur les autres interfaces basées sur React Spectrum dans AEM. Son implémentation de l’interface utilisateur et son modèle d’extensibilité sont désormais cohérents avec l’éditeur de fragments de contenu et l’éditeur universel. Le nouvel éditeur de modèle est désormais la valeur par défaut lorsqu’il est ouvert à partir de la nouvelle interface d’administration du modèle de contenu. L’ouverture d’un modèle de contenu dans l’interface utilisateur tactile ouvre l’éditeur d’interface utilisateur tactile et propose de tester le nouvel éditeur.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de la vue Assets {#new-features-assets-view}

**Mise en forme de texte améliorée avec des sous-chaînes dans les modèles Dynamic Media**

Vous pouvez désormais appliquer une mise en forme aux sous-chaînes dans les calques de texte de modèle Dynamic Media. Un mot ou une expression sélectionné est traité comme un calque distinct, ce qui vous permet d’ajuster sa police, sa taille, sa couleur, etc. Le calque de sous-chaîne est paramétré afin que vous puissiez le mettre à jour en temps réel à l’aide de l’URL de diffusion du modèle

### Nouvelles fonctionnalités de Dynamic Media avec OpenAPI {#new-features-dynamic-media-with-openapi}

**DM adapté au SEO avec des URL OpenAPI**

Créez des URL de redirection pour la diffusion de ressources dans DM avec OpenAPI, en remplaçant les UUID générés par le système longs par des identifiants courts et lisibles. Cela adapte les liens au SEO et les aligne davantage sur votre marque ou vos campagnes. Les URL de redirection sont automatiquement résolues sur l’UUID de ressource d’origine au moment de l’exécution sans interrompre les workflows existants.

>[!NOTE]
>
>Cette fonctionnalité est disponible en tant que fonctionnalité à disponibilité limitée. Vous pouvez [créer et envoyer un dossier d’assistance client Adobe](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html) pour l’activer pour votre déploiement.

<!--

### New Features in Content Hub {#new-features-content-hub}

**Mark Collections as Favourites**

You can now mark collections as Favorites in Content Hub, making it easier to organize and retrieve them. Once added, your favourite collections are conveniently available from the **Favourites** tab on the Content Hub home page.

**Pin collections for quick access**

Content Hub Administrators can now pin collections in Content Hub for quick access. Pinned collections are displayed in a dedicated **Pinned** section on the Collections home page, making it easier to keep important collections within reach.

>[!NOTE]
>
>These features are available as Limited Availability features. You can [create and submit an Adobe Customer Support case](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html) to enable it for your deployment.

-->

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités d’Experience Manager Forms {#new-features-forms}

**Étape Appeler le processus de modèle de données de formulaire pour les pièces jointes de liste SharePoint**

L’étape Invoquer le modèle de données de formulaire prend désormais en charge la gestion des métadonnées côté workflow pour les tableaux de pièces jointes codés en Base64 dans les modèles de données de formulaire basés sur une liste SharePoint. Grâce à cette amélioration, l’étape du workflow peut transmettre, stocker et récupérer des métadonnées telles que le nom du fichier, le type MIME et les propriétés personnalisées pour chaque pièce jointe. Cette fonctionnalité permet une gestion des données plus complète et une intégration en aval transparente. Pour plus d’informations, consultez [Prise en charge améliorée dans l’étape de workflow Appeler le modèle de données de formulaire pour les pièces jointes de la liste SharePoint](/help/forms/aem-forms-workflow-step-reference.md#invoke-form-data-model-fdm-service-step).

### Fonctionnalités de version préliminaire dans AEM Forms

**Améliorations de l’éditeur de règles**

L’éditeur de règles prend désormais en charge la navigation améliorée et permet l’utilisation de fonctions et d’expressions mathématiques dans les paramètres d’entrée.

**Navigation améliorée avec prise en charge de la payload d’événement**

L’action `Navigate To` dans les gestionnaires de service d’appel prend désormais en charge `EVENT_PAYLOAD`, ce qui permet aux auteurs de formulaires de configurer des actions de suivi en fonction des réponses d’événement. Cette amélioration offre une plus grande flexibilité dans la conception des workflows après envoi, assurant des transitions plus fluides et des expériences utilisateur plus personnalisées. Pour plus d’informations, voir [Navigation améliorée avec prise en charge de la payload d’événement](/help/forms/invoke-service-enhancements-rule-editor.md#use-case-5-use-event-payload-in-navigate-to-action-in-invoke-service).

**Prise en charge des fonctions et des expressions mathématiques dans les paramètres d’entrée**

Les paramètres d’entrée prennent désormais en charge les appels de fonction et les expressions mathématiques, ce qui permet aux auteurs de formulaires de transmettre directement des valeurs calculées dynamiquement. Cette amélioration simplifie les configurations de règle, élimine le besoin de champs supplémentaires et rend les formulaires plus adaptables à des scénarios complexes logiques et pilotés par les calculs. Pour plus d’informations, voir [Prise en charge des fonctions et des expressions mathématiques dans les paramètres d’entrée](/help/forms/rule-editor-core-components-user-interface.md#function-and-mathematical-expression-support-in-input-parameters).

### Nouvelles fonctionnalités d’accès anticipé d’AEM Forms {#forms-new-early-access-features}

Le programme d’accès anticipé d’AEM Forms offre une opportunité unique d’accéder de manière exclusive à des innovations de pointe et de contribuer à façonner leur développement.

Ces notes de mise à jour répertorient les innovations apportées à la version actuelle. Pour obtenir la liste complète des innovations disponibles dans le cadre du programme d’accès anticipé, consultez [Documentation du programme d’accès anticipé d’AEM Forms](/help/forms/early-access-ea-features.md).

Aperçu de **PDF dans l’éditeur de communication interactive**

Les utilisateurs et utilisatrices peuvent prévisualiser les PDF des communications interactives sans données, avec des fichiers de données JSON locaux ou avec des données provenant d’un modèle de données, ce qui permet des tests flexibles pilotés par les données. Pour plus d’informations, voir Aperçu de [PDF dans l’éditeur de communication interactive](/help/forms/interactive-communication/pdf-preview-in-interactive-communication-editor-with-different-data-options.md).

**Prise en charge des polices personnalisées dans la communication interactive**

La fonction Polices personnalisées permet aux utilisateurs d’incorporer des polices personnalisées ou approuvées par l’organisation dans les communications interactives, assurant ainsi un rendu PDF cohérent et de marque sur tous les appareils et plateformes. Pour plus d’informations, voir [Prise en charge des polices personnalisées dans la communication interactive](/help/forms/interactive-communication/add-custom-fonts-to-interactive-communication-editor.md).

**Importer et exporter des communications interactives**

Cette fonctionnalité permet la migration et la réutilisation des communications interactives dans différents environnements. Vous pouvez désormais exporter une communication interactive avec ses fragments et modèles de données associés depuis un environnement et l’importer dans un autre. Pour plus d’informations, voir [Importer et exporter des communications interactives](/help/forms/interactive-communication/import-and-export-interactive-communications.md).

<!--
**Forms Optimization opportunities**

Forms Optimization uses AI to analyze your forms and suggest improvements for better performance. It highlights forms with low engagement, flags accessibility issues, and generates AI-powered variations to help increase conversion rates and compliance with WCAG standards.

>[!VIDEO](https://video.tv.adobe.com/v/3469472/) 

Key optimization opportunities include:

* Increasing visibility for forms with low views
* Improving completion rates for forms with low conversions
* Addressing accessibility compliance issues
* Streamlining navigation to enhance user experience

With Forms Optimization, you get automated, data-driven recommendations and variations, making it easier to boost engagement and ensure your forms are effective and inclusive. 
-->

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Nouvelles fonctionnalités de la gestion des versions {#new-features-release-management}

**Suspendre les mises à jour de maintenance automatiques**

Journées de mise en production, événements en direct, pic des ventes : ces moments sont incontournables. [Nos nouvelles fonctionnalités en libre-service](/help/implementing/deploying/quiet-hours-update-free-periods.md) arrêtez les mises à jour de maintenance automatique lorsque cela est important, afin que vos équipes restent concentrées.

* Heures calmes : bloquez la maintenance automatique pendant les heures définies chaque jour. Idéal pour les heures de travail, les courses nocturnes ou les coupures matinales.
* Période sans mise à jour : bloque la maintenance automatique pendant une semaine complète. Utilisez-le pour les lancements, les promotions ou les gels annuels.

>[!NOTE]
>
>Disponible en tant que fonctionnalité à disponibilité limitée le 25 septembre.
>&#x200B;>Envoyez [aemcs-update-free@adobe.com](mailto:aemcs-update-free@adobe.com) par e-mail pour l’activer dans vos programmes.

### Nouvelle version des outils de développement AEM pour Eclipse {#aem-develeper-tools-for-eclipse}

La version 1.4.0 des outils de développement AEM pour Eclipse a été publiée. Cette version ajoute la prise en charge d’Eclipse IDE 2022-12 ou version ultérieure et a été validée avec la version actuelle (2025-09). L’outil fonctionne désormais avec les versions modernes de l’archétype de projet AEM et incorpore des améliorations de l’outil Sling IDE Tooling 1.3.0.

Installez à partir d’[Eclipse Marketplace](https://marketplace.eclipse.org/content/aem-developer-tools-eclipse) et consultez la page [Outils de développement AEM](https://eclipse.adobe.com) pour plus d’informations.

### Obsolescences prochaines de l’API Java {#java-api-deprecation}

Plusieurs API obsolètes ont été marquées pour suppression le 31 août et ne doivent donc plus être référencées. Vous recevrez des notifications du Centre de maintenance si une utilisation obsolète de l’API est détectée dans votre code. Après le 13 novembre, des notifications s’afficheront pendant les builds de Cloud Manager pour renforcer l’importance de la suppression de cette utilisation. Pour plus d’informations, consultez l’[article sur l’obsolescence](/help/release-notes/deprecated-removed-features.md#aem-apis), mais pour plus de commodité, ces API sont répertoriées ci-dessous :

+++ Développer pour afficher les éléments obsolètes de l’API Java

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

+++

<!--
OSGi properties:

* `org.apache.sling.commons.log.LogManager` (all properties)
* `org.apache.sling.commons.log.LogManager.factory.config` (`org.apache.sling.commons.log.file`, `org.apache.sling.commons.log.pattern`)
* 

-->

### Obsolescence de l’exécution Java 11 {#java11-runtime-deprecation}

Le *runtime Java 11* est obsolète et la plupart des environnements ont déjà été mis à niveau vers le **runtime Java 21**, plus performant.

Si votre environnement n’a pas pu être mis à niveau en raison de dépendances non prises en charge (voir les [exigences d’exécution Java 21](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements)), vous devriez avoir reçu un e-mail d’Adobe contenant les étapes suivantes. Comme décrit ici, Adobe a mis à niveau vos environnements **Dev** et **RDE** le **18 septembre 2025** afin que vous puissiez valider votre site et vos processus et résoudre tous les problèmes. Les mises à niveau de **Évaluation** et **Production** auront lieu le **14 octobre 2025**.

>[!NOTE]
>
>La version d’exécution est distincte de la version de build de votre code. Bien que nous recommandions la création de builds avec Java 21, les builds Java 11 sont toujours acceptés pour l’instant. Un avis d’obsolescence distinct pour les versions Java 11 sera partagé ultérieurement.

### Application de la politique de configuration des journaux AEM Java {#logconfig-policy}

Comme indiqué dans les notes de mise à jour d’avril, les journaux Java d’AEM doivent respecter un format standard pour assurer une surveillance fiable dans tous les environnements de la clientèle. Les configurations de journal personnalisées, telles que les modifications apportées à la mise en forme du journal, aux fichiers de sortie ou aux niveaux de journal par défaut, ne sont plus prises en charge. Les journaux doivent rester dirigés vers les fichiers par défaut et les niveaux de journal par défaut du code de produit AEM doivent être conservés. Consultez toutes les informations dans [l’article Journalisation](/help/implementing/developing/introduction/logging.md#configuration-loggers).

À compter du **30 octobre**, tous les remplacements de journalisation personnalisée non pris en charge seront ignorés. D’après notre analyse, la plupart des clientes et clients ne seront pas affectés et Adobe a contacté ceux dont la configuration actuelle peut être affectée.

Passez en revue et mettez à jour tous les processus en aval qui reposent sur un comportement de journalisation personnalisé. Par exemple :

* Si votre système de transfert de journal attend un format de journal personnalisé, vous devrez peut-être adapter vos règles d’ingestion.
* Si vous avez précédemment réduit le niveau de détail du journal en modifiant les niveaux de journal, sachez que le retour aux niveaux par défaut peut augmenter le volume du journal.

### Informatique de périphérie (programme Beta) {#edge-computing}

L’informatique de périphérie permet d’exécuter JavaScript sur la couche de réseau CDN, ce qui rapproche le traitement des données de l’utilisateur final ou l’utilisatrice finale. Cela réduit la latence et permet d’obtenir des expériences réactives et dynamiques en périphérie.

Cas d’utilisation courants :

* Personnalisation du contenu en fonction de la géolocalisation, du type d’appareil ou des attributs d’utilisateur ou d’utilisatrice
* Fonctionnement en tant que middleware entre le réseau CDN et votre origine
* Remise en forme des réponses d’API tierces (et éventuellement agrégation de plusieurs réponses d’API) avant de les diffuser au navigateur
* Composition et diffusion de HTML rendu sur le serveur Edge à l’aide de contenu assemblé à partir de divers serveurs principaux
* Exposition d’un serveur MCP pour les LLM tels que ChatGPT et Claude pour accéder aux outils personnalisés

Nous disposons d’un nombre limité d’opportunités pour la diffusion de l’instance de publication AEM ou les projets Edge Delivery Services pour les sites de production en direct. Si vous souhaitez participer ou en savoir plus, adressez un e-mail à [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) avec une brève description de votre cas d’utilisation.

### Authentification Edge pour Edge Delivery Services (programme Beta) {#edge-authentication}

L’authentification Edge vous permet de restreindre l’accès aux pages Edge Delivery Services à ceux qui se sont authentifiés auprès de votre fournisseur d’identité (IdP). Pour ce faire, déployez un fichier YAML de configuration OpenID Connect (OIDC) .

Si vous êtes intéressé, veuillez envoyer un e-mail à [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) avec une brève description de votre cas d’utilisation et toute question que vous pourriez avoir.

En dehors de Edge Delivery Services, notez que nous avons publié cette année une fonctionnalité permettant de configurer Open ID Connect [pour les projets de publication de niveau Service Cloud AEM](/help/security/open-id-connect-support-for-aem-as-a-cloud-service-on-publish-tier.md) afin de sécuriser les pages AEM.

<!--
### CDN Configuration for Edge Delivery Services (Beta Program) {#cdn-eds-beta}

The Adobe-Managed CDN offers flexible configuration options, as described in the [Config Pipeline article](/help/operations/config-pipeline.md#configurations). 

Now in beta, youcan deploy a config pipeline for features including CDN origin selectors, response and request transformations, CDN log forwarding and more. Please reach out to [aemcs-cdn-config-adopter@adobe.com](mailto:aemcs-cdn-config-adopter@adobe.com) with the details of your use case.

-->

### Instantanés pour les environnements de développement rapide (programme alpha) {#rde-snapshot-program}

En version alpha, les environnements de développement rapide (RDE) prennent désormais en charge une fonctionnalité permettant de capturer un instantané de l’état actuel du code et du contenu, qui peut être restauré ultérieurement. Cela peut s’avérer utile lors de la synchronisation du code qui peut devoir être restauré à un état précédent ou, lorsqu’au cours du développement, il est nécessaire d’alterner entre plusieurs fonctionnalités différentes. Il est également possible de restaurer uniquement le contenu modifiable en tant que point de départ connu pour les tests.

Vous pouvez envoyer un e-mail à l’adresse [aemcs-rde-support@adobe.com](mailto:aemcs-rde-support@adobe.com) si vous souhaitez nous faire part de vos commentaires sur cette fonctionnalité.

### Transfert de journal AEM vers d’autres destinations (Programme Beta) {#log-forwarding-beta}

Bien que les journaux puissent être téléchargés depuis Cloud Manager, de nombreuses organisations préfèrent diffuser ces journaux vers une destination de journalisation spécifique. AEM prend déjà en charge le transfert de journaux AEM et de réseau CDN vers Azure Blob Storage, Datadog, HTTPS, Elasticsearch (et OpenSearch) et Splunk. Cette fonctionnalité est configurée en libre-service et déployée à l’aide du pipeline de configuration.

Désormais, en version bêta, vous pouvez transférer les journaux AEM vers Amazon S3, Sumo Logic et votre propre compte New Relic (mais pas le compte fourni par Adobe). Notez que les journaux AEM (y compris Apache/Dispatcher) sont pris en charge pour ces destinations de journalisation, contrairement aux journaux de réseau CDN. Envoyez un e-mail à l’adresse [aemcs-logforwarding-beta@adobe.com](mailto:aemcs-logforwarding-beta@adobe.com) pour obtenir l’accès.

Pour en savoir plus, consultez la [documentation sur le transfert de journaux](/help/implementing/developing/introduction/log-forwarding.md).

### Surveillance étendue des performances des applications (APM) (programme Alpha) {#apm-alpha}

Pour des raisons d’observabilité, AEM Cloud Service prend actuellement en charge [New Relic One](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/user-access-new-relic) fourni par Adobe et [Dynatrace](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/dynatrace) géré par le client. Alors que nous explorons la prise en charge d’options APM supplémentaires, veuillez nous envoyer un e-mail à l’adresse [aemcs-apm-beta@adobe.com](mailto:aemcs-apm-beta@adobe.com) en indiquant votre fournisseur ou technologie préféré, ainsi que les cas d’utilisation.


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
