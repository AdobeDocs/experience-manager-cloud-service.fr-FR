---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: 401eaaaa0bb8dad054c7105533cbd4486964c484
workflow-type: tm+mt
source-wordcount: '2269'
ht-degree: 49%

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

La date de publication de la version actuelle (2025.7.0) d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le vendredi 7 août 2025. La prochaine disponibilité des fonctionnalités (2025.8.0) est prévue pour le vendredi 28 août 2025.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

<!-- 

## Release Video {#release-video}

Have a look at the July 2025 Release Overview video for a summary of the features added in the 2025.7.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440922?quality=12&captions=fre_fr)

-->

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités d’Experience Manager Sites {#enhancements-sites}

* Vous pouvez désormais copier des fragments de contenu avec des fragments référencés (enfants) en une seule opération. Cela permet de réutiliser les structures de fragment de contenu existantes pour créer du contenu.
* Dans l’interface d’administration des fragments de contenu, vous pouvez désormais afficher le statut des workflows pour les fragments de contenu, avec des informations détaillées sur les workflows passés et en cours d’exécution pour un fragment sélectionné.
* Le changement de nom ou le déplacement d’une page source de Live Copy déclenchent désormais la republication d’une page Live Copy renommée ou déplacée en conséquence.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

**Ajouter des formes aux modèles Dynamic Media**

Vous pouvez désormais [ajouter des calques de forme aux modèles Dynamic Media](/help/assets/dynamic-media/dynamic-media-templates.md#add-shapes-to-the-canvas) dans Experience Manager Assets. Tout comme les calques d’image et de texte, les calques de forme prennent en charge les paramètres des mises à jour en temps réel via l’URL du modèle. Vous pouvez également inclure des liens call-to-action (CTA) vers des formes dans vos modèles.

![Ajout de formes aux modèles Dynamic Media](/help/assets/assets/enable-uniform-radius-shape.png)

**Améliorations des métadonnées générées par l’IA**

AEM Assets vous permet désormais de [configurer l’affichage des titres des ressources en mode Carte ou Liste](/help/assets/smart-tags.md#configure-ai-generated-titles) sur la page de navigation des ressources. Vous pouvez choisir d’afficher le titre de la ressource que vous avez défini, le titre généré à l’aide de l’IA ou le titre généré par l’IA uniquement s’il n’existe aucun titre pour la ressource.

![Configurer les titres générés par l’IA](/help/assets/assets/configure-title-ai-generated.png)

Vous pouvez désormais également choisir de désactiver les métadonnées générées par l’IA au niveau du dossier.

### Nouvelles fonctionnalités dans Content Hub {#new-features-content-hub}

**Amélioration de la flexibilité de l’image de marque dans Content Hub**

En s’appuyant sur les fonctionnalités de personnalisation existantes, Content Hub permet désormais aux administrateurs d’adapter davantage leur déploiement en ajoutant des images de logo personnalisées. La prise en charge du format de fichier TIFF a également été ajoutée pour les images de bannière et de logo, ce qui permet une plus grande flexibilité de conception.

**Partage plus intelligent avec des liens intitulés**

Vous pouvez désormais ajouter un titre lors de la génération d’un lien partagé, que ce soit à partir de la vue des détails de la ressource ou après avoir sélectionné une ou plusieurs ressources. Cela permet aux destinataires d’identifier facilement la finalité de chaque lien, en particulier lors de la réception de plusieurs ressources partagées.

![lien privé et public](/help/assets/assets/shared-link-for-assets.png)

**Navigation de filtre améliorée**

Content Hub comprend désormais une option **Tout afficher** dans les filtres, ce qui permet aux utilisateurs d’afficher toutes les facettes disponibles ainsi que le nombre de ressources, à partir de la limite actuelle de dix facettes maximum. L’amélioration des fonctionnalités de recherche et de tri de chaque filtre facilite la découverte et la gestion plus efficaces des ressources.

### Application de bureau AEM version 3.0.0 {#desktop-app-release-3.0.0}

Bénéficiez du chargement automatisé de nouveaux fichiers et dossiers, d’opérations de fichiers améliorées, d’une découverte de ressources plus intelligente et d’une intégration transparente à AEM, ce qui rend la gestion de contenu plus rapide, plus claire et plus intuitive.

Pour obtenir la liste complète des fonctionnalités, voir [Notes de mise à jour de l’application de bureau](https://experienceleague.adobe.com/fr/docs/experience-manager-desktop-app/using/release-notes).

### Nouvelles fonctionnalités de Dynamic Media avec OpenAPI {#new-features-dynamic-media-with-openapi}

**Aperçu des ressources avant publication**

[!DNL Dynamic Media with OpenAPI capabilities] permet désormais de prévisualiser les ressources directement dans [!DNL AEM Sites] pages de création avant de les rendre publiques. Partagez des pages d’aperçu avec les parties prenantes pour recueillir leurs commentaires sur la qualité visuelle et l’ajustement contextuel. Au cours du cycle de révision, vous pouvez créer et gérer plusieurs versions de ressources avant de les finaliser pour publication.

**Amélioration de l’imagerie dynamique pour les demandes d’image OpenAPI**

Toutes les demandes d’image OpenAPI exploitent désormais entièrement l’imagerie dynamique avec une logique de promotion automatique et de secours. Cette amélioration optimise les images en fonction des conditions de l’appareil et du réseau, ce qui accélère le chargement des pages et réduit l’utilisation de la bande passante, tout en préservant la qualité visuelle.


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités d’AEM Forms {#forms-new-features}

**Éditeur universel pour les Forms adaptatifs et les fragments de formulaire**

L’[éditeur universel](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) prend désormais en charge la création de Forms adaptatifs et de fragments de formulaire réutilisables. Les auteurs et autrices peuvent créer des formulaires visuellement, configurer des actions d’envoi et ajouter une validation reCAPTCHA, le tout dans un environnement de création WYSIWYG simplifié. Cette fonctionnalité accélère la création de formulaires, améliore la cohérence et accroît la protection contre le spam et les abus automatisés.

![Éditeur universel](/help/edge/docs/forms/universal-editor/assets/universal-editor.png){width=80%, align-center}


**Service d’envoi Forms pour Edge Delivery Services Forms**

Voir [Service d’envoi Forms](/help/forms/forms-submission-service.md). vous permet de stocker en toute transparence les données des envois de formulaires adaptatifs directement dans des plateformes de feuilles de calcul populaires telles que Google Sheets, Microsoft OneDrive ou SharePoint. Cette intégration rationalise la gestion des données en permettant l’envoi direct des données de formulaire à la feuille de calcul de votre choix, ce qui élimine le transfert manuel de données et réduit les erreurs.

Les principaux avantages sont les suivants :

* **Intégration directe :** configurez vos formulaires pour envoyer directement des données à une feuille de calcul spécifiée.
* **Mappage de données personnalisé :** mappez les champs de formulaire aux colonnes de feuille de calcul correspondantes pour le stockage organisé.
* **Contrôle d’accès :** utilisez les autorisations de feuille de calcul existantes pour gérer qui peut accéder aux données envoyées ou les modifier.

**Génération et synchronisation de rendus AFP à partir de Forms adaptatif**

L’[API de synchronisation de sortie AFP](/help/forms/document-generation-afp-api.md) permet aux administrateurs et aux utilisateurs de générer une sortie AFP (présentation de fonction avancée) à partir du Forms adaptatif et de synchroniser la sortie avec des systèmes ou des emplacements de stockage externes. AFP est un format de document haute performance optimisé pour l’impression, souvent utilisé dans les environnements d’entreprise à grande échelle.

<!-- ### New pre-release features in AEM Forms {#forms-new-pre-release-features}

**Enhancements in Rule Editor**

* The `validate` method in the function list now supports validation at the panel, field, and form levels.
* Client-side custom function parsing now supports ES10+ JavaScript features and static imports.
* The button to download Document of Record (DoR) is now available as an out-of-the-box (OOTB) option in the rule editor.
* Rules now support the use of dynamic variables.
* Custom event-based rules are now supported.
* Repeatable panel rules are now executed based on context, rather than only on the last panel instance.
* Rules can now be triggered based on query parameters, UTM parameters, and browser parameters.
* Form-specific custom function scripts are now supported for Adaptive Forms in Edge Delivery Services.

 -->

### Nouvelles fonctionnalités d’accès anticipé dans AEM Forms {#forms-new-early-access-features}

Le programme d’accès anticipé d’AEM Forms vous offre une opportunité unique d’obtenir un accès exclusif aux innovations de pointe et de contribuer à façonner leur développement.

Ces notes de mise à jour répertorient les innovations de la version actuelle. Pour obtenir la liste complète des innovations disponibles dans le cadre du programme d’accès anticipé, voir [Documentation du programme d’accès anticipé d’AEM Forms](/help/forms/early-access-ea-features.md).


<!-- **Forms Optimization opportunities**

Forms Optimization uses AI to analyze your forms and suggest improvements for better performance. It highlights forms with low engagement, flags accessibility issues, and generates AI-powered variations to help increase conversion rates and compliance with WCAG standards.

>[!VIDEO](https://video.tv.adobe.com/v/3469472/) 

Key optimization opportunities include:

* Increasing visibility for forms with low views
* Improving completion rates for forms with low conversions
* Addressing accessibility compliance issues
* Streamlining navigation to enhance user experience

With Forms Optimization, you get automated, data-driven recommendations and variations, making it easier to boost engagement and ensure your forms are effective and inclusive. -->

**Éditeur de règles pour l’éditeur de communications interactives**

Créez des actions dynamiques basées sur les données directement dans vos documents à l’aide d’une interface intuitive de type pointer-cliquer. Définissez facilement une logique conditionnelle, automatisez les workflows et personnalisez le contenu sans écrire de code.

**Interface de ligne de commande AEM Forms Scaffolder pour les composants personnalisés**

>[!VIDEO](https://video.tv.adobe.com/v/3470514/aem-forms scaffolding-aem-custom component generator-aem-forms cli-aem-forms custom component-aem-forms development tool)

Accélérez votre développement AEM Forms Edge Delivery Services avec cet outil d’interface de ligne de commande. Générez instantanément le code et le câblage nécessaires pour lancer le développement de composants personnalisés, sans tracas.

**Outil d’intégration d’API pour les données de formulaire dynamique**

L’outil d’intégration d’API permet aux auteurs de formulaires de créer des formulaires dynamiques et intelligents qui récupèrent et renseignent automatiquement les données des API REST externes en fonction des interactions utilisateur. Cette fonctionnalité d’intégration sans code transforme les formulaires statiques en interfaces réactives de collecte de données.

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

Le **runtime Java 11*- est désormais obsolète et la plupart des environnements ont déjà été mis à niveau vers le runtime &#x200B;** Java 21** plus performant.

Si votre environnement n’a pas pu être mis à niveau en raison de dépendances non prises en charge (voir les [Exigences d’exécution Java 21](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements)), vous avez dû recevoir un e-mail d’Adobe contenant les étapes spécifiques à réaliser. Veillez à ce que toutes les mises à jour requises soient terminées d’ici le **28 août 2025**, afin que votre environnement puisse être mis à niveau sans interruption.

Remarque : la version de l’exécution est distincte de la version de build de votre code. Bien que nous recommandions la création de versions avec Java 21, les versions Java 11 sont toujours prises en charge pour l’instant. Un avis d’obsolescence distinct pour les versions Java 11 sera partagé ultérieurement.

### Application de la politique de configuration des journaux AEM Java {#logconfig-policy}

Comme indiqué dans les notes de mise à jour d’avril, les journaux Java d’AEM doivent respecter un format standard pour assurer une surveillance fiable dans tous les environnements de la clientèle. Les configurations de journal personnalisées, telles que les modifications apportées à la mise en forme du journal, aux fichiers de sortie ou aux niveaux de journal par défaut, ne sont plus prises en charge. Les journaux doivent rester dirigés vers les fichiers par défaut et les niveaux de journal par défaut du code de produit AEM doivent être conservés. Consultez toutes les informations dans [l’article Journalisation](/help/implementing/developing/introduction/logging.md#configuration-loggers).

À compter de **fin août**, tous les remplacements de journalisation personnalisée non pris en charge seront ignorés. D’après notre analyse, la plupart des clientes et clients ne seront pas affectés et Adobe a contacté ceux dont la configuration actuelle peut être affectée.

Passez en revue et mettez à jour tous les processus en aval qui reposent sur un comportement de journalisation personnalisé. Par exemple :

* Si votre système de transfert de journal attend un format de journal personnalisé, vous devrez peut-être adapter vos règles d’ingestion.
* Si vous avez précédemment réduit le niveau de détail du journal en modifiant les niveaux de journal, sachez que le retour aux niveaux par défaut peut augmenter le volume du journal.

### Purge par défaut des anciennes versions et des journaux d’audit {#mt-defaults}

Actuellement, les versions de contenu et les journaux d’audit ont leurs *tâches de maintenance de purge- associées désactivées par défaut et aucune donnée n’est donc supprimée sauf configuration explicite.

Toutefois, pour optimiser les performances du référentiel, la purge sera activée par défaut à une date annoncée ultérieurement, en suivant ces instructions :

#### Versions du contenu {#mt-content}

* **Nouveaux environnements*- (créé après une date à venir (à communiquer ultérieurement)
   * Les versions antérieures à **30 jours*- seront régulièrement supprimées.
   * Les cinq versions les plus récentes des 30 derniers jours sont conservées, tout comme la version la plus récente et la version actuelle, quel que soit leur ancienneté.

* **Environnements existants*- (créés avant cette date à venir) :
   * Les versions antérieures à **7 ans*- seront régulièrement supprimées.
   * Toutes les versions des 7 dernières années sont conservées.
   * Ce seuil élevé par défaut empêche la suppression involontaire de données récentes. Cependant, il est recommandé de configurer des valeurs plus faibles pour optimiser les performances du référentiel.

* Vous pouvez modifier ces valeurs par défaut via la configuration YAML, déployée à l’aide du pipeline de configuration.

#### Journal d’audit {#mt-auditlogs}

* **Nouveaux environnements*- (créés après une date à venir, qui sera communiquée séparément) :
   * Les journaux d’audit de réplication, de gestion des ressources numériques et de page datant de plus de **7 jours* seront régulièrement supprimés.
   * Tous les événements sont consignés par défaut.

* **Environnements existants*- (créés avant cette date à venir) :
   * Les journaux d’audit de réplication, de gestion des ressources numériques et de pages de plus de **7 ans* seront régulièrement supprimés.
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
* Exposer un serveur MCP pour les LLM tels que ChatGPT et Claude pour accéder aux outils personnalisés

Nous disposons d’un nombre limité d’opportunités pour la diffusion de l’instance de publication AEM ou les projets Edge Delivery Services pour les sites de production en direct. Si vous souhaitez participer ou en savoir plus, adressez un e-mail à [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) avec une brève description de votre cas d’utilisation.

### Configuration du réseau CDN pour Edge Delivery Services (programme bêta) {#cdn-eds-beta}

Le réseau CDN géré par Adobe offre des options de configuration flexibles, comme indiqué dans l’article [Configurer le pipeline](/help/operations/config-pipeline.md#configurations).

Désormais en version bêta, déployez un pipeline de configuration pour des fonctionnalités telles que les sélecteurs d’origine du réseau CDN, les transformations de réponse et de requête, le transfert de journal CDN, etc. Contactez [aemcs-cdn-config-adopter@adobe.com](mailto:aemcs-cdn-config-adopter@adobe.com) avec les détails de votre cas d’utilisation.

### Instantanés pour les RDE (programme Alpha) {#rde-snapshot-beta}

Dans la version Alpha, les environnements de développement rapide (RDE) prennent désormais en charge une fonctionnalité permettant de prendre un instantané de l’état actuel du code et du contenu, qui peut être restauré ultérieurement. Cela peut s’avérer utile lors de la synchronisation du code qui doit être rétabli ou lors du passage d’une fonctionnalité à l’autre. Il est également possible de restaurer uniquement le contenu modifiable en tant que point de départ connu pour les tests.

Veuillez envoyer un e-mail à [aemcs-rde-support@adobe.com](mailto:aemcs-rde-support@adobe.com) pour faire part de vos commentaires sur cette fonctionnalité.

### Transfert de journal AEM vers d’autres destinations (Programme bêta) {#log-forwarding-beta}

Bien que les journaux puissent être téléchargés depuis Cloud Manager, de nombreuses organisations préfèrent diffuser ces journaux vers une destination de journalisation spécifique. AEM prend déjà en charge le transfert de journaux AEM et de réseau CDN vers Azure Blob Storage, Datadog, HTTPS, Elasticsearch (et OpenSearch) et Splunk. Cette fonctionnalité est configurée en libre-service et déployée à l’aide du pipeline de configuration.

Désormais, en version bêta, vous pouvez transférer les journaux AEM vers Amazon S3, Sumo Logic, Dynatrace et votre propre compte New Relic (et non le compte fourni par Adobe). Notez que les journaux AEM (y compris Apache/Dispatcher) sont pris en charge pour ces destinations de journalisation, contrairement aux journaux de réseau CDN. Envoyez un e-mail à l’adresse [aemcs-logforwarding-beta@adobe.com](mailto:aemcs-logforwarding-beta@adobe.com) pour obtenir l’accès.

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
