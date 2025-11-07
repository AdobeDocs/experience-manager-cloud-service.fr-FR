---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: a5e20bd3ee4d332b46bdff2fbf5222c9a9fead2f
workflow-type: tm+mt
source-wordcount: '1871'
ht-degree: 60%

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

La date de publication de la version actuelle d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2025.10.0) est le vendredi 30 octobre 2025. La prochaine version des fonctionnalités (2025.11.0) est prévue pour le vendredi 20 novembre 2025.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

<!-- 

## Release Video {#release-video}

Have a look at the July 2025 Release Overview video for a summary of the features added in the 2025.7.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440920?quality=12)

-->

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités d’Experience Manager Sites {#new-sites}

* [Lancements pour les fragments de contenu](/help/sites-cloud/administering/content-fragments/launches-for-content-fragments.md) : les auteurs de contenu peuvent désormais créer et planifier des variations futures de contenu structuré à l’aide de lancements pour les fragments de contenu. La nouvelle console Fragments de contenu permet de créer, de modifier, de gérer et de planifier les lancements de fragments de contenu sous la forme de branches pour le contenu futur qui peut être synchronisé avec la branche source. Une nouvelle vue Diff offre une vue d’ensemble claire de toutes les modifications de contenu avant de valider un lancement pour une publication ultérieure.

* L’[&#x200B; Éditeur de modèle de contenu pour les fragments de contenu AEM](/help/sites-cloud/administering/content-fragments/content-fragment-models.md) a été modernisé afin de s’aligner sur les autres interfaces basées sur React Spectrum dans AEM. L’implémentation de son interface d’utilisation et son modèle d’extensibilité sont désormais alignés sur l’éditeur de fragments de contenu et l’éditeur universel. Le nouvel éditeur de modèles s’ouvre désormais par défaut à partir de la nouvelle interface d’administration des modèles de contenu. L’ouverture d’un modèle de contenu dans l’interface d’utilisation tactile ouvre l’éditeur de l’interface d’utilisation tactile et propose de tester le nouvel éditeur.

<!--

### New Features in Content Hub {#new-features-content-hub}

**Mark Collections as Favourites**

You can now mark collections as Favorites in Content Hub, making it easier to organize and retrieve them. Once added, your favourite collections are conveniently available from the **Favourites** tab on the Content Hub home page.

**Pin collections for quick access**

Content Hub Administrators can now pin collections in Content Hub for quick access. Pinned collections are displayed in a dedicated **Pinned** section on the Collections home page, making it easier to keep important collections within reach.

>[!NOTE]
>
>These features are available as Limited Availability features. You can [create and submit an Adobe Customer Support case](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html) to enable it for your deployment.

-->

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités d’Experience Manager Forms {#new-features-forms}

**Éditeur universel pour les formulaires adaptatifs et les fragments de formulaire**

L’éditeur universel offre désormais une expérience de création unifiée pour créer des Forms adaptatifs et des fragments de formulaire réutilisables. Les auteurs peuvent concevoir des formulaires visuellement dans un environnement WYSIWYG intuitif, en tirant parti d’extensions puissantes et de fonctionnalités d’envoi complètes. L’éditeur intègre la validation reCAPTCHA pour une sécurité renforcée, fournit des services de préremplissage pour réduire la saisie manuelle et prend en charge le responsive design sur tous les appareils.

**Extensions disponibles :**

* **Éditeur de règles** : l’éditeur de règles visuel permet aux auteurs de formulaires d’ajouter un comportement dynamique aux champs de formulaire sans codage, sans prendre en charge les règles pilotées par un événement, la validation instantanée et la gestion des erreurs.
* **Propriétés du formulaire** : assistant permettant aux utilisateurs de configurer des actions d’envoi, un service de préremplissage, un message de remerciement et d’autres comportements liés aux formulaires directement dans l’éditeur.
* **Source de données de formulaire et référence de liaison** : l’extension de source de données permet aux auteurs de formulaires d’ajouter des composants associés à un modèle de données directement dans un formulaire adaptatif et de sélectionner une référence de liaison dans une sélection d’arborescence pour tous les composants.

**Actions Envoyer prises en charge :**

L’éditeur universel prend en charge un large éventail de workflows d’envoi, notamment l’action d’envoi personnalisée, l’envoi à Microsoft SharePoint, l’envoi à Microsoft OneDrive, l’envoi au stockage Azure Blob, l’envoi au point d’entrée REST, l’appel à un workflow AEM, l’appel à un flux Power Automate, l’envoi à Marketo Engage, l’envoi à Adobe Experience Platform (AEP), l’envoi à une feuille de calcul, l’envoi à l’aide du modèle de données de formulaire (FDM), l’envoi à Workfront Fusion et l’envoi d’e-mails.

Pour plus d’informations, consultez la documentation [Éditeur universel pour Edge Delivery Services for Forms](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md). Pour plus d’informations sur la configuration des actions d’envoi, voir [&#x200B; Action d’envoi de formulaire adaptatif](/help/edge/docs/forms/universal-editor/submit-action.md).

<!-- ### Pre-Release features in AEM Forms 

**Rule Editor Enhancements**

The Rule Editor now supports enhanced navigation and allows use of function and mathematical expressions in input parameters.

**Enhanced Navigation with Event Payload Support**
 
The `Navigate To` action in the Invoke Service handlers now supports `EVENT_PAYLOAD`, enabling form authors to configure follow-up actions based on event responses. This enhancement offers greater flexibility in designing post-submission workflows, ensuring smoother transitions and more personalized user experiences. For more information, see [Enhanced Navigation with Event Payload Support](/help/forms/invoke-service-enhancements-rule-editor.md#use-case-5-use-event-payload-in-navigate-to-action-in-invoke-service).

**Function and Mathematical Expression Support in Input Parameters**
 
Input parameters now support both function calls and mathematical expressions, enabling form authors to pass dynamically computed values directly. This enhancement streamlines rule configurations, eliminates the need for extra fields, and makes forms more adaptable to complex logic and calculation-driven scenarios. For more information, see [Function and Mathematical Expression Support in Input Parameters](/help/forms/rule-editor-core-components-user-interface.md#function-and-mathematical-expression-support-in-input-parameters). -->

### Nouvelles fonctionnalités d’accès anticipé d’AEM Forms {#forms-new-early-access-features}

Le programme d’accès anticipé d’AEM Forms offre une opportunité unique d’accéder de manière exclusive à des innovations de pointe et de contribuer à façonner leur développement.

Ces notes de mise à jour répertorient les innovations apportées à la version actuelle. Pour obtenir la liste complète des innovations disponibles dans le cadre du programme d’accès anticipé, consultez [Documentation du programme d’accès anticipé d’AEM Forms](/help/forms/early-access-ea-features.md).

#### Améliorations de la communication interactive

##### Verrouillage de modèle

Verrouillez le contenu et les éléments de disposition dans les modèles pour maintenir l’intégrité de la marque et empêcher toute modification non autorisée. Cela permet d’assurer la cohérence de la conception dans toutes les communications.

##### Prise en charge des débordements de contenu

Présentation de l’option « Autoriser les sauts de page dans le contenu » pour les mises en page fluides. Cette amélioration permet une modification lisse de plusieurs pages et une meilleure gestion du texte pour les documents complexes.

##### Modification de fichier XDP

L’éditeur de communication interactive prend désormais en charge la modification XDP, y compris l’intégration de fragments. Vous pouvez désormais modifier les fichiers XDP dans un navigateur au lieu de Forms Designer qui s’exécute uniquement sur l’ordinateur de bureau Microsoft Windows.

##### Numérotation dynamique de page

Affichez automatiquement la mention « N° de page # de ## » sur les gabarits pour une pagination claire et cohérente dans les documents de plusieurs pages.

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

**Suspendre les mises à jour de maintenance automatique**

Journées de mise en production, événements en direct, pic de ventes : pas d’erreur possible. [Nos nouvelles fonctionnalités en libre-service](/help/implementing/deploying/quiet-hours-update-free-periods.md) permettent de suspendre les mises à jour de maintenance automatique afin que vos équipes restent concentrées.

* Heures calmes : bloquez la maintenance automatique pendant des plages horaires définies chaque jour. Idéal pour les heures de travail, les exécutions de nuit ou les migrations du matin.
* Période sans mise à jour : bloquez la maintenance automatique pendant une semaine entière. Idéal pour les lancements, les promotions ou les périodes de verrouillage annuels.

>[!NOTE]
>
>En disponibilité limitée à partir du 25 septembre.
>Envoyez un e-mail à [aemcs-update-free@adobe.com](mailto:aemcs-update-free@adobe.com) pour l’activer dans vos programmes.

### Transfert de journal AEM vers d’autres destinations {#log-forwarding}

Il est désormais possible de transférer les journaux AEM vers Amazon S3, Sumo Logic, Dynatrace et votre propre compte New Relic (et non le compte fourni par Adobe). Notez que les journaux AEM (y compris Apache/Dispatcher) sont pris en charge pour ces destinations de journalisation, mais pas les journaux CDN.

Consultez l’ensemble complet des [destinations de transfert de journal prises en charge](/help/implementing/developing/introduction/log-forwarding.md).

### Configuration du pipeline pour Edge Delivery Services {#config-pipeline-eds}

Les pipelines de configuration sont désormais pris en charge pour les sites créés avec Edge Delivery Services, étendant cette fonctionnalité au-delà de la seule diffusion de création AEM et de publication AEM. Vous pouvez utiliser les Pipelines de configuration pour gérer des paramètres tels que la configuration du réseau CDN, y compris les règles de filtrage du trafic et les sélecteurs d’origine. Consultez [Configurations prises en charge](/help/operations/config-pipeline.md#configurations).

Les pipelines de configuration d’Edge Delivery prennent également en charge les secrets via les variables de pipeline Cloud Manager.

Voir [Ajouter un pipeline Edge Delivery](/help/implementing/cloud-manager/configuring-pipelines/configuring-edge-delivery-pipeline.md).

### Obsolescences prochaines de l’API Java {#java-api-deprecation}

Plusieurs API obsolètes seront supprimées le 31 août et ne doivent donc plus être utilisées. Vous recevrez des notifications du centre d’actions si l’utilisation d’une API obsolète est détectée dans votre code. Après le 13 novembre, des notifications s’afficheront pendant les builds de Cloud Manager pour renforcer l’importance d’arrêter d’utiliser ces API. Pour plus d’informations, consultez l’[article sur l’obsolescence](/help/release-notes/deprecated-removed-features.md#aem-apis), mais pour plus de commodité, ces API sont répertoriées ci-dessous :

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

### Obsolescence de Java 11 Runtime {#java11-runtime-deprecation}

Adobe a mis à niveau les environnements **d’évaluation** et **de production** vers l’exécution Java 21 **hautes performances** le 14 octobre 2025. À compter de fin janvier, ni le SDK AEM Cloud Service ni les environnements cloud ne fonctionneront avec l’exécution Java 11.

>[!NOTE]
>
> Pour tirer parti des dernières optimisations des performances et améliorations du langage, il est recommandé de créer avec Java 17 ou Java 21 (recommandé). La création avec Java 8 et Java 11 reste prise en charge pour l’instant, mais sera abandonnée dans une prochaine version. Une communication distincte sera émise avant l’obsolescence. Voir la section *exigences en matière de temps de création* de [cet article](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements).
>

### Application de la politique de configuration des journaux AEM Java {#logconfig-policy}

Comme indiqué dans les notes de mise à jour d’avril, les journaux Java d’AEM doivent respecter un format standard pour assurer une surveillance fiable dans tous les environnements de la clientèle. Les configurations de journal personnalisées, telles que les modifications apportées à la mise en forme du journal, aux fichiers de sortie ou aux niveaux de journal par défaut, ne sont plus prises en charge. Les journaux doivent rester dirigés vers les fichiers par défaut et les niveaux de journal par défaut du code de produit AEM doivent être conservés. Consultez toutes les informations dans [l’article Journalisation](/help/implementing/developing/introduction/logging.md#configuration-loggers).

À compter du **20 novembre**, tous les remplacements de journalisation personnalisée non pris en charge seront ignorés. D’après notre analyse, la plupart des clientes et clients ne seront pas affectés et Adobe a contacté ceux dont la configuration actuelle peut être affectée.

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

### Authentification Edge pour Edge Delivery Services (programme Beta) {#edge-authentication}

L’authentification Edge vous permet de restreindre l’accès aux pages Edge Delivery Services aux personnes qui se sont authentifiées auprès de votre fournisseur d’identité (IdP). Pour ce faire, déployez un fichier YAML de configuration OpenID Connect (OIDC).

Si cela vous intéresse, envoyez un e-mail à [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) avec une brève description de votre cas d’utilisation et toute question éventuelle.

<!--
### CDN Configuration for Edge Delivery Services (Beta Program) {#cdn-eds-beta}

The Adobe-Managed CDN offers flexible configuration options, as described in the [Config Pipeline article](/help/operations/config-pipeline.md#configurations). 

Now in beta, youcan deploy a config pipeline for features including CDN origin selectors, response and request transformations, CDN log forwarding and more. Please reach out to [aemcs-cdn-config-adopter@adobe.com](mailto:aemcs-cdn-config-adopter@adobe.com) with the details of your use case.

-->

### Déploiements en production Canary pour tester le code avant d’accepter le trafic réel (programme Beta) {#canary-beta}

Validez une build de production avec du trafic de test interne uniquement avant de l’exposer aux utilisateurs finaux. Déployez en production, acheminez uniquement le trafic Canary (à l’aide d’un en-tête spécial), surveillez le comportement, puis convertissez-le en trafic réel ou restaurez, sans affecter les clients et clientes.

Déployez vos versions de code en production, mais limitez-les au trafic de test interne uniquement avant de décider d’accepter le trafic réel ou de restaurer.

Envoyez un e-mail à [aemcs-canary-deployments-beta@adobe.com](mailto:aemcs-canary-deployments-beta@adobe.com) pour demander l’accès et partager vos commentaires.


### Réponses de l’IA - Réponses plus intelligentes et contextuelles pour AEM Sites (programme Beta) {#ai-answers-beta}

AI Answers offre une nouvelle manière à vos visiteurs d’interagir avec votre contenu. Optimisée par la technologie RAG (Retrieval-Augmentated Generation), elle utilise vos données gérées par AEM pour fournir des réponses précises et cohérentes avec la marque directement dans vos expériences digitales.

Dans le cadre de cette version bêta, vous pouvez explorer en toute sécurité les réponses de l’IA dans votre environnement AEM Cloud Service. Cette approche vous permet de valider les performances, la précision et l’expérience globale avant de la rendre disponible pour votre audience en direct. Une fois validée, vous pouvez promouvoir votre expérience de réponses de l’IA en production complète.

Pour demander l’accès à la version bêta ou partager vos commentaires, contactez [feedback-ai-answers@adobe.com](mailto:feedback-ai-answers@adobe.com).


### Instantanés pour les environnements de développement rapide (programme alpha) {#rde-snapshot-program}

En version alpha, les environnements de développement rapide (RDE) prennent désormais en charge une fonctionnalité permettant de capturer un instantané de l’état actuel du code et du contenu, qui peut être restauré ultérieurement. Cela peut s’avérer utile lors de la synchronisation du code qui peut devoir être restauré à un état précédent ou, lorsqu’au cours du développement, il est nécessaire d’alterner entre plusieurs fonctionnalités différentes. Il est également possible de restaurer uniquement le contenu modifiable en tant que point de départ connu pour les tests.

Vous pouvez envoyer un e-mail à l’adresse [aemcs-rde-support@adobe.com](mailto:aemcs-rde-support@adobe.com) si vous souhaitez nous faire part de vos commentaires sur cette fonctionnalité.

### Surveillance étendue des performances des applications (APM) (programme Alpha) {#apm-alpha}

Pour des raisons d’observabilité, AEM Cloud Service prend actuellement en charge [New Relic One](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/user-access-new-relic) fourni par Adobe et [Dynatrace](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/dynatrace) géré par le client. Pendant que nous étudions la prise en charge d’options APM supplémentaires, veuillez nous envoyer un e-mail à l’adresse [aemcs-apm-beta@adobe.com](mailto:aemcs-apm-beta@adobe.com) en indiquant votre fournisseur ou technologie préféré, ainsi que les cas d’utilisation.

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
