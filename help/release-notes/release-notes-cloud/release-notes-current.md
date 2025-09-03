---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: 0d2164920ca44ee6c872fdfe2090760a1506215d
workflow-type: tm+mt
source-wordcount: '1961'
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

La date de publication de la version actuelle (2025.8.0) d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le vendredi 28 août 2025. La prochaine disponibilité des fonctionnalités (2025.9.0) est prévue pour le vendredi 25 septembre 2025.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

<!-- 

## Release Video {#release-video}

Have a look at the July 2025 Release Overview video for a summary of the features added in the 2025.7.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440920?quality=12)

-->

## Experience Hub {#experience-hub}

[Experience Hub](/help/experience-hub.md) est votre point de départ centralisé pour accéder à toutes les fonctionnalités d’AEM. Il est personnalisé en fonction de votre personnage utilisateur et des licences disponibles, ce qui permet à chaque utilisateur d’accomplir efficacement ses résultats.

## Assistant AI dans AEM {#AI-assistant}

L’[assistant AI](/help/implementing/cloud-manager/ai-assistant-in-aem.md) pour AEM offre une interface conversationnelle conçue pour vous apporter des réponses instantanées à vos questions sur les produits AEM (*disponible pour tous les utilisateurs*) et automatiser la création de tickets d’assistance (*disponible pour les administrateurs de l’assistance*). Il est directement incorporé à AEM et accessible à partir de l’interface utilisateur d’AEM Experience Hub, de Cloud Manager et de l’instance de création.

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités d’Experience Manager Sites {#enhancements-sites}

* Dans l’UI d’administration des fragments de contenu, vous pouvez désormais afficher le statut des workflows pour les fragments de contenu, avec des informations détaillées sur les workflows passés et en cours d’exécution pour un fragment sélectionné.
* Les performances d’ouverture des fragments de contenu dans le nouvel éditeur de fragments de contenu ont été augmentées de 25 % dans les scénarios courants, car les fragments sont ouverts via UUID plutôt que par chemin d’accès.
* Lors de la copie de fragments de contenu avec des fragments référencés, les copies des fragments référencés sont désormais stockées au même emplacement que la copie du fragment parent.
* Vous pouvez désormais configurer un espace de travail personnalisé dans les paramètres des dossiers pour exporter les fragments de contenu vers l’espace de travail configuré dans Adobe Target.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités dans Content Hub {#new-features-content-hub}

**Recherche en bloc via les propriétés du filtre**

Content Hub permet désormais de découvrir plus rapidement les ressources dont vous avez besoin. Grâce à la nouvelle fonctionnalité de recherche en bloc, vous pouvez saisir plusieurs valeurs pour n’importe quelle propriété de filtre, séparée par un délimiteur (par exemple, plusieurs ID de SKU), et récupérer instantanément toutes les ressources correspondantes à l’aide d’une seule recherche.

### Nouvelles fonctionnalités de Dynamic Media avec OpenAPI {#new-features-dynamic-media-with-openapi}

**DM compatible avec l’optimisation du moteur de recherche (SEO) avec des URL OpenAPI**

Créez des URL Vanity pour la diffusion de ressources dans DM avec OpenAPI, en remplaçant les UUID générés par le système longs par des identifiants courts et lisibles. Cela rend les liens plus conviviaux et mieux alignés sur votre marque ou vos campagnes. Les URL de redirection vers un microsite sont automatiquement résolues sur l’UUID de ressource d’origine au moment de l’exécution sans interrompre les workflows existants.

>[!NOTE]
>
>Cette fonctionnalité sera disponible en tant que fonctionnalité à disponibilité limitée le 10 septembre. Vous pouvez [créer et envoyer un dossier de support Adobe](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html) pour l’activer pour votre déploiement.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités de Experience Manager Forms {#new-features-forms}

**Composant Entrée De Date Et D’Heure**

Un composant [Date et heure](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/date-time-component) est désormais disponible, ce qui permet aux utilisateurs et aux utilisatrices de sélectionner à la fois la date et l’heure à l’aide d’une interface de calendrier et d’horloge, ou en saisissant manuellement des valeurs dans un format pris en charge.

**Amélioration de la gestion des erreurs pour les chargements de fichiers**

Le composant [ Pièce jointe ](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/file-attachment#basic-tab) valide désormais automatiquement le type de fichier chargé par rapport à la liste autorisée. Si un utilisateur télécharge un fichier dans un format non pris en charge, le formulaire affiche une erreur lors de l’envoi. Le composant vérifie également le contenu du fichier pour valider son type, ce qui améliore la sécurité globale du formulaire.

**Réponse d’erreur spécifiée pour l’action d’envoi personnalisée**

Lorsqu’une [action d’envoi personnalisée](/help/forms/custom-submit-action-troubleshooting.md) rencontre une erreur non gérée, le système renvoie le code d’erreur 502. Cela permet d’identifier que le problème est lié à l’action d’envoi personnalisée, ce qui facilite le débogage.

**Exclusion des champs masqués du document d’enregistrement**

Une nouvelle propriété permet d’exclure les champs masqués du [document d’enregistrement](/help/forms/generate-document-of-record-core-components.md#document-of-record-settings). Par défaut, cette option n’est pas sélectionnée et s’applique à tous les champs de formulaire.


### Fonctionnalités de version préliminaire d’AEM Forms

**Générer et synchroniser des rendus AFP**

Vous pouvez désormais utiliser l’[API de communication AEM Forms](/help/forms/document-generation-afp-api.md) pour convertir un fichier XDP au format AFP. L&#39;AFP est un format haute performance largement utilisé dans l&#39;impression d&#39;entreprise à grande échelle.

**Améliorations apportées à l’éditeur de règles**

* [Méthode de validation dans la liste de fonctions](/help/forms/rule-editor-enhancements-use-cases.md#validate-method-in-function-list) : les méthodes de validation et de réinitialisation prennent désormais en charge l’exécution au niveau du panneau, du champ et du formulaire. Auparavant, elles n’étaient prises en charge qu’au niveau du formulaire.
* [Prise en charge moderne de JavaScript](/help/forms/rule-editor-core-components-difference-tables.md) : la prise en charge des fonctionnalités ECMAScript 2019 et versions ultérieures a été ajoutée pour les fonctions personnalisées, ce qui vous permet d’écrire du code plus efficace, modulaire et réutilisable.
* [Option Télécharger le document d’enregistrement dans l’éditeur de règles](/help/forms/rule-editor-enhancements-use-cases.md#downloaddor-as-ootb-fuction-in-rule-editor) : une fonction permettant de télécharger le document d’enregistrement a été ajoutée en tant qu’option prête à l’emploi dans l’éditeur de règles.

  ![ Document d’enregistrement ](/help/forms/assets/document-of-record-rn.gif)

* [Variables dynamiques dans l’éditeur de règles](/help/forms/rule-editor-enhancements-use-cases.md#support-for-dynamic-variables-in-rules) : vous pouvez désormais utiliser des variables dynamiques (temporaires) dans l’éditeur de règles pour une plus grande flexibilité dans la définition des conditions et des actions. Les champs masqués ne sont plus nécessaires pour stocker des valeurs temporaires.
* [Prise en charge des règles basées sur un événement personnalisé](/help/forms/rule-editor-enhancements-use-cases.md#custom-event-based-rules-support) : vous pouvez désormais définir des événements personnalisés et déclencher des règles basées sur ces événements.
* [Règles de panneau répétables basées sur le contexte](/help/forms/rule-editor-enhancements-use-cases.md#context-based-rule-execution-for-repeatable-panels) : dans les panneaux répétables, les règles sont désormais exécutées en fonction du contexte, au lieu d’être appliquées uniquement à la dernière instance de panneau.
* [Règles déclenchées par des paramètres](/help/forms/rule-editor-enhancements-use-cases.md#url-and-browser-parameter-based-rules-in-adaptive-forms) : l’éditeur de règles prend désormais en charge l’exécution de règles en fonction des paramètres de requête, des paramètres UTM ou des paramètres de navigateur.
* [Fonctions personnalisées spécifiques aux formulaires](/help/edge/docs/forms/universal-editor/rule-editor-universal-editor.md#organizing-custom-functions-across-different-forms) : Edge Delivery Services Forms prend désormais en charge les scripts de fonction personnalisée spécifiques aux formulaires, offrant ainsi une plus grande flexibilité dans la gestion de la logique réutilisable.
* [Imports statiques pour les fonctions personnalisées ](/help/edge/docs/forms/universal-editor/rule-editor-universal-editor.md#static-imports-for-custom-functions) : l’éditeur de règles de l’éditeur universel prend désormais en charge les importations statiques, ce qui permet aux développeurs et aux développeuses d’organiser, de partager et de réutiliser des fonctions dans plusieurs formulaires.

### Nouvelles fonctionnalités d’accès anticipé d’AEM Forms {#forms-new-early-access-features}

Le programme d’accès anticipé d’AEM Forms offre une opportunité unique d’accéder de manière exclusive à des innovations de pointe et de contribuer à façonner leur développement.

Ces notes de mise à jour répertorient les innovations apportées à la version actuelle. Pour obtenir la liste complète des innovations disponibles dans le cadre du programme d’accès anticipé, consultez [Documentation du programme d’accès anticipé d’AEM Forms](/help/forms/early-access-ea-features.md).

**Composant Signature tactile**

Vous pouvez désormais utiliser le [composant Signature tactile](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/scribble-signature) pour aider les utilisateurs et les utilisatrices à ajouter leurs signatures à un formulaire, comme dans un formulaire d’accord. Le composant permet aux utilisateurs de tracer leur signature directement dans le formulaire à l’aide d’une souris, d’un stylet ou d’un écran tactile.

**Intégration directe de l’API dans l’éditeur de règles**

Le Forms adaptatif prend désormais en charge l’intégration [API directe](/help/forms/api-integration-in-rule-editor.md) dans l’éditeur visuel de règles sans avoir besoin de modèle de données de formulaire. Les auteurs peuvent configurer des API à l’aide d’une importation d’URL ou cURL, mapper des paramètres d’entrée/sortie et sécuriser les appels avec authentification.

<!--
**Forms Optimization opportunities**

Forms Optimization uses AI to analyze your forms and suggest improvements for better performance. It highlights forms with low engagement, flags accessibility issues, and generates AI-powered variations to help increase conversion rates and compliance with WCAG standards.

>[!VIDEO](https://video.tv.adobe.com/v/3469472/) 

Key optimization opportunities include:

* Increasing visibility for forms with low views
* Improving completion rates for forms with low conversions
* Addressing accessibility compliance issues
* Streamlining navigation to enhance user experience

With Forms Optimization, you get automated, data-driven recommendations and variations, making it easier to boost engagement and ensure your forms are effective and inclusive. -->

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Mise à jour de la compilation JavaScript {#javascript-compilation}

La compilation JavaScript de la bibliothèque côté client (clientlibs) par défaut cible désormais ECMASCRIPT_2018 au lieu de ECMASCRIPT5. Bien que remplaçable dans le passé, cette mise à jour permet d’améliorer les performances, la syntaxe JavaScript moderne et les fonctionnalités par défaut.

### Obsolescence prochaine de l’API Java {#java-api-deprecation}

Plusieurs API obsolètes ciblent la suppression le 31 août et ne doivent donc plus être référencées. Début septembre, des notifications du Centre d’actions seront envoyées si l’utilisation de l’API est détectée. Après le 25 septembre, des notifications s’afficheront pendant les builds de Cloud Manager pour renforcer l’importance de la suppression de l’utilisation. Voir l’article [obsolescence](/help/release-notes/deprecated-removed-features.md#aem-apis) pour plus d’informations, mais pour plus de commodité, ces API sont répertoriées ci-dessous :

<details>
  <summary>Développez pour afficher les éléments obsolètes de l’API Java</summary>

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

</details>

<!--
OSGi properties:

* `org.apache.sling.commons.log.LogManager` (all properties)
* `org.apache.sling.commons.log.LogManager.factory.config` (`org.apache.sling.commons.log.file`, `org.apache.sling.commons.log.pattern`)
* 

-->

### Obsolescence de l’exécution Java 11 {#java11-runtime-deprecation}

L’*exécution Java 11* est désormais obsolète et la plupart des environnements ont déjà été mis à niveau vers l’**exécution Java 21** plus performante.

Si votre environnement n’a pas pu être mis à niveau en raison de dépendances non prises en charge (voir les [Exigences d’exécution Java 21](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements)), vous avez dû recevoir un e-mail d’Adobe contenant les étapes spécifiques à réaliser. Veillez à ce que toutes les mises à jour requises soient terminées au **1er octobre 2025**, afin que votre environnement puisse être mis à niveau sans interruption.

Remarque : la version de l’exécution est distincte de la version de build de votre code. Bien que nous recommandions la création de versions avec Java 21, les versions Java 11 sont toujours prises en charge pour l’instant. Un avis d’obsolescence distinct pour les versions Java 11 sera partagé ultérieurement.

### Application de la politique de configuration des journaux AEM Java {#logconfig-policy}

Comme indiqué dans les notes de mise à jour d’avril, les journaux Java d’AEM doivent respecter un format standard pour assurer une surveillance fiable dans tous les environnements de la clientèle. Les configurations de journal personnalisées, telles que les modifications apportées à la mise en forme du journal, aux fichiers de sortie ou aux niveaux de journal par défaut, ne sont plus prises en charge. Les journaux doivent rester dirigés vers les fichiers par défaut et les niveaux de journal par défaut du code de produit AEM doivent être conservés. Consultez toutes les informations dans [l’article Journalisation](/help/implementing/developing/introduction/logging.md#configuration-loggers).

À compter du **25 septembre**, tous les remplacements de journalisation personnalisée non pris en charge seront ignorés. D’après notre analyse, la plupart des clientes et clients ne seront pas affectés et Adobe a contacté ceux dont la configuration actuelle peut être affectée.

Passez en revue et mettez à jour tous les processus en aval qui reposent sur un comportement de journalisation personnalisé. Par exemple :

* Si votre système de transfert de journal attend un format de journal personnalisé, vous devrez peut-être adapter vos règles d’ingestion.
* Si vous avez précédemment réduit le niveau de détail du journal en modifiant les niveaux de journal, sachez que le retour aux niveaux par défaut peut augmenter le volume du journal.

### Edge Computing (programme Beta) {#edge-computing}

L’informatique de périphérie permet d’exécuter JavaScript sur la couche de réseau CDN, ce qui rapproche le traitement des données de l’utilisateur final ou l’utilisatrice finale. Cela réduit la latence et permet d’obtenir des expériences réactives et dynamiques en périphérie.

Cas d’utilisation courants :

* Authentification des utilisateurs et utilisatrices auprès d’un fournisseur d’identités avant d’accorder l’accès au contenu
* Personnalisation du contenu en fonction de la géolocalisation, du type d’appareil ou des attributs d’utilisateur ou d’utilisatrice
* Fonctionnement en tant que middleware entre le réseau CDN et votre origine
* Reformatage des réponses provenant d’API tierces (et éventuellement agrégation de plusieurs réponses d’API) avant de les diffuser au navigateur
* Composition et diffusion de HTML rendu sur le serveur Edge à l’aide de contenu assemblé à partir de divers serveurs principaux
* Exposition d’un serveur MCP pour les LLM tels que ChatGPT et Claude pour accéder aux outils personnalisés

Nous disposons d’un nombre limité d’opportunités pour la diffusion de l’instance de publication AEM ou les projets Edge Delivery Services pour les sites de production en direct. Si vous souhaitez participer ou en savoir plus, adressez un e-mail à [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) avec une brève description de votre cas d’utilisation.

### Configuration du réseau CDN pour Edge Delivery Services (programme Beta) {#cdn-eds-beta}

Le réseau CDN géré par Adobe offre des options de configuration flexibles, comme indiqué dans l’article [Configurer le pipeline](/help/operations/config-pipeline.md#configurations).

Désormais, en version bêta, vous pouvez déployer un pipeline de configuration pour les fonctionnalités, y compris les sélecteurs d’origine du réseau CDN, les transformations de réponse et de requête, le transfert de journal CDN, etc. Contactez [aemcs-cdn-config-adopter@adobe.com](mailto:aemcs-cdn-config-adopter@adobe.com) avec les détails de votre cas d’utilisation.

### Instantanés pour les environnements de développement rapide (programme alpha) {#rde-snapshot-program}

En version alpha, les environnements de développement rapide (RDE) prennent désormais en charge une fonctionnalité permettant de capturer un instantané de l’état actuel du code et du contenu, qui peut être restauré ultérieurement. Cela peut s’avérer utile lors de la synchronisation du code qui peut devoir être restauré à un état précédent ou, lorsqu’au cours du développement, il est nécessaire d’alterner entre plusieurs fonctionnalités différentes. Il est également possible de restaurer uniquement le contenu modifiable en tant que point de départ connu pour les tests.

Vous pouvez envoyer un e-mail à l’adresse [aemcs-rde-support@adobe.com](mailto:aemcs-rde-support@adobe.com) si vous souhaitez nous faire part de vos commentaires sur cette fonctionnalité.

### Transfert de journal AEM vers d’autres destinations (Programme Beta) {#log-forwarding-beta}

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
