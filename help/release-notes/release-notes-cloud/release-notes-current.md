---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: 07b957374dcc513050c48bb320e8d639385c3344
workflow-type: tm+mt
source-wordcount: '2350'
ht-degree: 90%

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

La date de publication de la version actuelle (2025.7.0) d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le 7 août 2025. La prochaine disponibilité des fonctionnalités (2025.8.0) est prévue pour le 28 août 2025.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

<!-- 

## Release Video {#release-video}

Have a look at the July 2025 Release Overview video for a summary of the features added in the 2025.7.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440920?quality=12)

-->

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités d’Experience Manager Sites {#enhancements-sites}

* Vous pouvez désormais copier des fragments de contenu avec des fragments référencés (enfants) en une seule opération. Cela permet de réutiliser des structures de fragments de contenu existantes pour créer du contenu.
* Dans l’UI d’administration des fragments de contenu, vous pouvez désormais afficher le statut des workflows pour les fragments de contenu, avec des informations détaillées sur les workflows passés et en cours d’exécution pour un fragment sélectionné.
* Le changement de nom ou le déplacement d’une page source de Live Copy déclenchent désormais la republication d’une page Live Copy renommée ou déplacée en conséquence.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

**Ajouter des formes aux modèles Dynamic Media**

Vous pouvez désormais [ajouter des calques de forme aux modèles Dynamic Media](/help/assets/dynamic-media/dynamic-media-templates.md#add-shapes-to-the-canvas) dans Experience Manager Assets. Tout comme les calques d’image et de texte, les calques de forme prennent en charge les paramètres des mises à jour en temps réel via l’URL du modèle. Vous pouvez également inclure des liens d’appel à l’action (CTA) vers des formes dans vos modèles.

![Ajouter des formes aux modèles Dynamic Media](/help/assets/assets/enable-uniform-radius-shape.png)

**Améliorations des métadonnées générées par l’IA**

AEM Assets permet désormais de [configurer l’affichage des titres des ressources en mode Carte ou Liste](/help/assets/smart-tags.md#configure-ai-generated-titles) sur la page de navigation dans les ressources. Vous pouvez choisir d’afficher le titre de la ressource que vous avez défini, le titre généré à l’aide de l’IA ou le titre généré par l’IA uniquement s’il n’existe aucun titre pour la ressource.

![Configurer les titres générés par l’IA](/help/assets/assets/configure-title-ai-generated.png)

Vous pouvez désormais également choisir de désactiver les métadonnées générées par l’IA au niveau du dossier.

### Nouvelles fonctionnalités dans Content Hub {#new-features-content-hub}

**Amélioration de la flexibilité du branding dans le hub de contenus**

En s’appuyant sur les fonctionnalités de personnalisation existantes, le hub de contenus permet désormais aux administrateurs et administratrices d’adapter davantage leur déploiement en ajoutant des images de logo personnalisées. La prise en charge du format de fichier TIFF a également été ajoutée pour les images de bannière et de logo, ce qui permet une plus grande flexibilité de conception.

**Partage plus intelligent avec des liens portant des titres**

Vous pouvez désormais ajouter un titre lorsque vous générez un lien partagé, que ce soit à partir de la vue des détails de la ressource ou après avoir sélectionné une ou plusieurs ressources. Cela permet aux personnes destinataires d’identifier facilement la finalité de chaque lien, en particulier lorsqu’elles reçoivent plusieurs ressources partagées.

![lien privé et public](/help/assets/assets/shared-link-for-assets.png)

**Amélioration de la navigation dans les filtres**

Le hub de contenus comprend désormais une option **Tout afficher** dans les filtres, ce qui permet d’afficher toutes les facettes disponibles ainsi que le nombre de ressources, en partant de la limite actuelle de dix facettes maximum. L’amélioration des fonctionnalités de recherche et de tri au sein de chaque filtre facilite la découverte et la gestion plus efficaces des ressources.

### Application de bureau AEM version 3.0.0 {#desktop-app-release-3.0.0}

Bénéficiez du chargement automatisé des nouveaux fichiers et dossiers, d’opérations de fichiers améliorées, d’une découverte des ressources plus intelligente et d’une intégration transparente à AEM, ce qui rend la gestion de contenu plus rapide, plus claire et plus intuitive.

Pour obtenir la liste complète des fonctionnalités, voir la section [Notes de mise à jour de l’application de bureau](https://experienceleague.adobe.com/fr/docs/experience-manager-desktop-app/using/release-notes).

### Nouvelles fonctionnalités de Dynamic Media avec OpenAPI {#new-features-dynamic-media-with-openapi}

**Aperçu des ressources avant publication**

[!DNL Dynamic Media with OpenAPI capabilities] permet désormais de prévisualiser les ressources directement dans les pages de création [!DNL AEM Sites] avant qu’elles ne soient rendues publiques. Partagez les pages d’aperçu avec les personnes concernées pour recueillir leurs commentaires sur la qualité visuelle et la conformité avec le contexte. Au cours du cycle de révision, vous pouvez créer et gérer plusieurs versions des ressources avant de les finaliser pour publication.

**Amélioration de l’imagerie dynamique pour les demandes d’image OpenAPI**

Toutes les demandes d’image OpenAPI exploitent désormais pleinement l’imagerie dynamique avec une logique de promotion automatique et de secours. Cette amélioration optimise les images en fonction des conditions de l’appareil et du réseau, ce qui accélère le chargement des pages et réduit l’utilisation de la bande passante, tout en préservant la qualité visuelle.


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités d’AEM Forms {#forms-new-features}

* **Éditeur universel pour les formulaires adaptatifs et les fragments de formulaire**

  L’[éditeur universel](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) prend désormais en charge la création de formulaires adaptatifs et de fragments de formulaire réutilisables. Les auteurs et autrices peuvent créer des formulaires visuellement, configurer des actions d’envoi et ajouter une validation reCAPTCHA, le tout dans un environnement de création WYSIWYG simplifié. Cette fonctionnalité accélère la création de formulaires, améliore la cohérence et accroît la protection contre le spam et les abus automatisés.

  ![Éditeur universel](/help/edge/docs/forms/universal-editor/assets/universal-editor.png){width=80%, align-center}


* **Configurer le service d’envoi de formulaire pour les formulaires Edge Delivery Services**

  Le service d’envoi [Forms](/help/forms/forms-submission-service.md) vous permet de stocker facilement des données des envois de formulaires adaptatifs directement dans des plateformes de feuilles de calcul populaires telles que Google Sheets, Microsoft OneDrive ou SharePoint. Cette intégration simplifie la gestion des données en permettant l’envoi direct des données de formulaire à la feuille de calcul de votre choix, en éliminant le transfert manuel de données et en réduisant les erreurs. Les principaux avantages sont les suivants :

   * **Intégration directe :** configurez vos formulaires pour envoyer des données directement à une feuille de calcul spécifiée.
   * **Mappage de données personnalisé :** mappez les champs de formulaire aux colonnes de feuille de calcul correspondantes pour un stockage organisé.
   * **Contrôle d’accès :** profitez des autorisations de feuille de calcul existantes pour gérer les personnes qui peuvent accéder aux données envoyées ou les modifier.

* **Générer et synchroniser des rendus AFP à partir de formulaires adaptatifs**

  L’[API de synchronisation de sortie AFP](/help/forms/document-generation-afp-api.md) permet aux administrateurs, administratrices, utilisateurs et utilisatrices de générer une sortie AFP (présentation de fonction avancée) à partir de formulaires adaptatifs et de synchroniser la sortie avec des systèmes ou des emplacements de stockage externes. AFP est un format de document haute performance optimisé pour l’impression, souvent utilisé dans les environnements d’entreprise à grande échelle.

* **Prise en charge du mappage automatique pour les fragments de formulaire adaptatif**

  Les Forms adaptatives prennent désormais en charge [mappage automatique des fragments de formulaire adaptatif](/help/forms/adaptive-form-fragments-core-components.md#auto-mapping-support-for-fragments-in-an-adaptive-form). Grâce à cette amélioration, les fragments correspondants sont automatiquement insérés lorsque les objets de schéma s’alignent sur une structure de fragment définie. Il simplifie la création de formulaires, améliore la réutilisation des fragments et assure la cohérence entre les formulaires intégrés aux données.

* **Titre de formulaire personnalisé dans le document d’enregistrement**

  Les auteurs peuvent désormais définir un [ titre de formulaire personnalisé dans le document d’enregistrement](/help/forms/generate-document-of-record-core-components.md#customize-the-branding-information-in-document-of-record) en modifiant le titre du formulaire personnalisé. Le titre personnalisé apparaît dans l’en-tête de PDF, les propriétés du document de PDF et comme titre d’affichage initial à l’ouverture du PDF, ce qui permet d’assurer une identification claire et une valorisation de marque cohérente.

* **Amélioration de la gestion des erreurs pour les types de fichiers restreints**

  [La gestion des erreurs pour les types de fichiers restreints](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/file-attachment#validation-tab) est désormais prise en charge, ce qui bloque les chargements de fichiers non pris en charge. Lorsque les utilisateurs tentent d’envoyer un fichier en modifiant son type dans un format non pris en charge, le formulaire renvoie une erreur lors de l’envoi.


<!--
### Pre-release features in AEM Forms {#forms-new-pre-release-features}

**Enhancements in Rule Editor**

* The `validate` / `reset` method in the function list now supports validation at the panel, field, and form levels.
* Client-side custom function parsing now supports ES10+ JavaScript features and static imports.
* The button to download Document of Record (DoR) is now available as an out-of-the-box (OOTB) option in the rule editor.
* Rules now support the use of dynamic variables.
* Custom event-based rules are now supported.
* Repeatable panel rules are now executed based on context, rather than only on the last panel instance.
* Rules can now be triggered based on query parameters, UTM parameters, and browser parameters.
* Form-specific custom function scripts are now supported for Adaptive Forms in Edge Delivery Services.

### New Early Access Features in AEM Forms {#forms-new-early-access-features}

The AEM Forms Early Access Program offers a unique opportunity for you to get exclusive access to cutting-edge innovations and help shape their development.

These release notes list the innovations delivered in the current release. For the complete list of innovations available under the Early Access Program, see [AEM Forms Early Access Program documentation](/help/forms/early-access-ea-features.md). 


**Forms Optimization opportunities**

Forms Optimization uses AI to analyze your forms and suggest improvements for better performance. It highlights forms with low engagement, flags accessibility issues, and generates AI-powered variations to help increase conversion rates and compliance with WCAG standards.

>[!VIDEO](https://video.tv.adobe.com/v/3469472/) 

Key optimization opportunities include:

* Increasing visibility for forms with low views
* Improving completion rates for forms with low conversions
* Addressing accessibility compliance issues
* Streamlining navigation to enhance user experience

With Forms Optimization, you get automated, data-driven recommendations and variations, making it easier to boost engagement and ensure your forms are effective and inclusive. -->

**Éditeur de règles pour l’éditeur de communications interactives**

Créez des actions dynamiques, basées sur les données, directement dans vos documents à l’aide d’une interface intuitive de type pointer-cliquer. Définissez facilement une logique conditionnelle, automatisez les workflows et personnalisez le contenu sans écrire de code.

**Interface de ligne de commande d’AEM Forms Scaffolder pour les composants personnalisés**

>[!VIDEO](https://video.tv.adobe.com/v/3470514/aem-forms scaffolding-aem-custom component generator-aem-forms cli-aem-forms custom component-aem-forms development tool)

Accélérez votre développement Edge Delivery Services d’AEM Forms avec cet outil d’interface de ligne de commande. Générez instantanément le code et les connexions nécessaires pour lancer rapidement le développement de composants personnalisés, sans tracas.

**Outil d’intégration d’API pour les données de formulaire dynamique**

L’outil d’intégration d’API permet aux créateurs et créatrices de formulaires de créer des formulaires dynamiques et intelligents qui récupèrent et renseignent automatiquement les données des API REST externes en fonction des interactions d’utilisation. Cette fonctionnalité d’intégration sans code transforme les formulaires statiques en interfaces réactives de collecte de données.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Mode Nœud pour la gestion des autorisations {#node-view}

AEM introduit la gestion des autorisations pour Node View. La fonctionnalité principale reste la même que celle de l’interface utilisateur classique, mais elle est plus conviviale et plus efficace. Voir l’article [ dédié](/help/security/touch-ui-principal-view.md) pour plus d’informations.

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

L’*exécution Java 11 **&#x200B; est désormais obsolète et la plupart des environnements ont déjà été mis à niveau vers l’**&#x200B;exécution Java 21** plus performante.

Si votre environnement n’a pas pu être mis à niveau en raison de dépendances non prises en charge (voir les [Exigences d’exécution Java 21](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements)), vous avez dû recevoir un e-mail d’Adobe contenant les étapes spécifiques à réaliser. Veillez à ce que toutes les mises à jour requises soient terminées d’ici le **28 août 2025**, afin que votre environnement puisse être mis à niveau sans interruption.

Remarque : la version de l’exécution est distincte de la version de build de votre code. Bien que nous recommandions la création de versions avec Java 21, les versions Java 11 sont toujours prises en charge pour l’instant. Un avis d’obsolescence distinct pour les versions Java 11 sera partagé ultérieurement.

### Application de la politique de configuration des journaux AEM Java {#logconfig-policy}

Comme indiqué dans les notes de mise à jour d’avril, les journaux Java d’AEM doivent respecter un format standard pour assurer une surveillance fiable dans tous les environnements de la clientèle. Les configurations de journal personnalisées, telles que les modifications apportées à la mise en forme du journal, aux fichiers de sortie ou aux niveaux de journal par défaut, ne sont plus prises en charge. Les journaux doivent rester dirigés vers les fichiers par défaut et les niveaux de journal par défaut du code de produit AEM doivent être conservés. Consultez toutes les informations dans [l’article Journalisation](/help/implementing/developing/introduction/logging.md#configuration-loggers).

À compter de **fin août**, tous les remplacements de journalisation personnalisée non pris en charge seront ignorés. D’après notre analyse, la plupart des clientes et clients ne seront pas affectés et Adobe a contacté ceux dont la configuration actuelle peut être affectée.

Passez en revue et mettez à jour tous les processus en aval qui reposent sur un comportement de journalisation personnalisé. Par exemple :

* Si votre système de transfert de journal attend un format de journal personnalisé, vous devrez peut-être adapter vos règles d’ingestion.
* Si vous avez précédemment réduit le niveau de détail du journal en modifiant les niveaux de journal, sachez que le retour aux niveaux par défaut peut augmenter le volume du journal.

### Purge par défaut des anciennes versions et des journaux d’audit {#mt-defaults}

Actuellement, les tâches de maintenance de purge* des versions de contenu et des journaux d’audit sont désactivées par défaut. Par conséquent, les données ne sont supprimées que si elles sont configurées explicitement.

Toutefois, pour optimiser les performances du référentiel, la purge sera activée par défaut à une date annoncée ultérieurement, conformément à ces instructions :

#### Versions du contenu {#mt-content}

* *Nouveaux environnements** (créés après une date à venir, qui sera communiquée ultérieurement)
   * Les versions de plus de *30 jours** seront régulièrement supprimées.
   * Les cinq versions les plus récentes des 30 derniers jours sont conservées, tout comme la version la plus récente et la version actuelle, quelle que soit leur ancienneté.

* *Environnements existants** (créés avant cette date à venir) :
   * Les versions antérieures à *7 ans** seront régulièrement supprimées.
   * Toutes les versions des 7 dernières années sont conservées.
   * Ce seuil élevé par défaut empêche la suppression involontaire de données récentes. Cependant, il est recommandé de configurer des valeurs plus faibles pour optimiser les performances du référentiel.

* Vous pouvez modifier ces valeurs par défaut via la configuration YAML, déployée à l’aide du pipeline de configuration.

#### Journal d’audit {#mt-auditlogs}

* *Nouveaux environnements** (créés après une date à venir, qui sera communiquée séparément) :
   * Les journaux d’audit de réplication, de gestion des ressources numériques et de page datant de plus de *7 jours** seront régulièrement supprimés.
   * Tous les événements sont consignés par défaut.

* *Environnements existants** (créés avant cette date à venir) :
   * Les journaux d’audit de réplication, de gestion des ressources numériques et de page datant de plus de *7 ans** seront régulièrement supprimés.
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
* Composition et diffusion de HTML rendu sur le serveur Edge à l’aide de contenu assemblé à partir de divers serveurs principaux
* Exposition d’un serveur MCP pour les LLM tels que ChatGPT et Claude pour accéder aux outils personnalisés

Nous disposons d’un nombre limité d’opportunités pour la diffusion de l’instance de publication AEM ou les projets Edge Delivery Services pour les sites de production en direct. Si vous souhaitez participer ou en savoir plus, adressez un e-mail à [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) avec une brève description de votre cas d’utilisation.

### Configuration du réseau CDN pour Edge Delivery Services (programme bêta) {#cdn-eds-beta}

Le réseau CDN géré par Adobe offre des options de configuration flexibles, comme indiqué dans l’article [Configurer le pipeline](/help/operations/config-pipeline.md#configurations).

Désormais, en version bêta, déployez un pipeline de configuration pour des fonctionnalités telles que les sélecteurs d’origine du réseau CDN, les transformations de réponse et de requête, le transfert des journaux du réseau CDN, etc. Contactez [aemcs-cdn-config-adopter@adobe.com](mailto:aemcs-cdn-config-adopter@adobe.com) avec les détails de votre cas d’utilisation.

### Instantanés pour les environnements de développement rapide (programme alpha) {#rde-snapshot-beta}

En version alpha, les environnements de développement rapide (RDE) prennent désormais en charge une fonctionnalité permettant de capturer un instantané de l’état actuel du code et du contenu, qui peut être restauré ultérieurement. Cela peut s’avérer utile lors de la synchronisation du code qui peut devoir être restauré à un état précédent ou, lorsqu’au cours du développement, il est nécessaire d’alterner entre plusieurs fonctionnalités différentes. Il est également possible de restaurer uniquement le contenu modifiable en tant que point de départ connu pour les tests.

Vous pouvez envoyer un e-mail à l’adresse [aemcs-rde-support@adobe.com](mailto:aemcs-rde-support@adobe.com) si vous souhaitez nous faire part de vos commentaires sur cette fonctionnalité.

### Transfert de journal AEM vers d’autres destinations (Programme bêta) {#log-forwarding-beta}

Bien que les journaux puissent être téléchargés depuis Cloud Manager, de nombreuses organisations préfèrent diffuser ces journaux vers une destination de journalisation spécifique. AEM prend déjà en charge le transfert de journaux AEM et de réseau CDN vers Azure Blob Storage, Datadog, HTTPS, Elasticsearch (et OpenSearch) et Splunk. Cette fonctionnalité est configurée en libre-service et déployée à l’aide du pipeline de configuration.

Désormais, en version bêta, vous pouvez transférer les journaux AEM vers Amazon S3, Sumo Logic et votre propre compte New Relic (mais pas le compte fourni par Adobe). Notez que les journaux AEM (y compris Apache/Dispatcher) sont pris en charge pour ces destinations de journalisation, contrairement aux journaux de réseau CDN. Envoyez un e-mail à l’adresse [aemcs-logforwarding-beta@adobe.com](mailto:aemcs-logforwarding-beta@adobe.com) pour obtenir l’accès.

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
