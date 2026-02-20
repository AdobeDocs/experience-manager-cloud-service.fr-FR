---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: cf45f9e6d89e0a166c09989b0fc8e793a54ce9ff
workflow-type: tm+mt
source-wordcount: '1886'
ht-degree: 43%

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

La date de publication de la version actuelle de [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2026.1.0) est le vendredi 29 janvier 2026. La prochaine version des fonctionnalités (2026.2.0) est prévue pour le vendredi 26 février 2026.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

## Vidéo de mise à jour {#release-video}

Consultez la vidéo Vue d’ensemble de la version de janvier 2026 pour un résumé des fonctionnalités ajoutées dans la version 2026.1.0 :

>[!VIDEO](https://video.tv.adobe.com/v/3479789/?quality=12)


## Programmes AEM Beta {#aem-beta-programs}

Les programmes bêta Adobe Experience Manager (AEM) permettent aux clients d’accéder aux fonctionnalités et au code de version préliminaire, de faire part de leurs commentaires et de guider l’avenir d’AEM.

>[!IMPORTANT]
>
>Les versions de Beta peuvent contenir des défauts et sont fournies « EN L’ÉTAT » sans garantie d’aucune sorte. Adobe n’a aucune obligation de tenir à jour, corriger, mettre à jour, modifier, remplacer ou prendre en charge (par le biais des services d’assistance Adobe ou d’une autre manière) les versions bêta. Adobe conseille aux clients d’être prudent et de ne pas se fier au bon fonctionnement ou aux performances des versions bêta, ni à la documentation ou aux documents d’accompagnement. Les fonctionnalités et API de la version bêta peuvent être modifiées sans préavis. Par conséquent, toute utilisation des versions bêta s’effectue entièrement aux risques et périls du client.

**Avantages de la participation**
L’accès anticipé aux fonctionnalités développées par Adobe permet aux clients et aux partenaires de faire part de leurs commentaires et de façonner le développement des produits. Cela les aide également à se préparer à adopter de nouvelles fonctionnalités avant leur disponibilité générale.

**Programmes bêta actuels**
Les sections suivantes répertorient les programmes bêta actifs.

<!--
### Agents in AEM (Explorer program) {#agents-in-aem-beta-program}

Gain early access to powerful, new AEM agentic capabilities across production, governance, optimization, discovery, and development. Your feedback directly shapes Adobe's roadmap and final features. See [Overview of Agents in AEM](/help/ai-in-aem/agents/overview.md) to learn more.

This program typically lasts 4-6 weeks, but can be tailored to be flexible around your ability to actively participate. 

To opt in to participate in this program, email [aemagentsteam@adobe.com](mailto:aemagentsteam@adobe.com) and include the following details to the extent possible:

* Names and Adobe ID's of team members who will actively use agents.
* List Specific agents that you or your team will want to use. Or simply say "All Agents."

Customers selected for participation will be notified directly by Adobe. Participation is subject to eligibility considerations, including customer licensing and limited program capacity. While not all requests can be accommodated initially, additional customers may be considered in future beta waves.
-->

### AEM Foundation (programmes Beta) {#aem-foundation-beta-programs}

Voir [Programmes bêta AEM Foundation](#foundation-early-adopter).

### Cloud Manager (programmes Beta) {#cloud-manager-beta-programs}

Voir [Programmes bêta Cloud Manager](/help/implementing/cloud-manager/release-notes/current.md).

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Serveur MCP de contenu {#content-MCP}

Le Cloud Service AEM comprend désormais des **serveurs Content MCP**, offrant un moyen normalisé pour les expériences optimisées par l’IA de travailler avec le contenu AEM via des outils compatibles avec MCP.

Les développeurs et les utilisateurs expérimentés travaillant dans les applications de chat et les plateformes d’agent peuvent connecter AEM à des copilotes et des automatisations personnalisés, de sorte que le travail de contenu fasse partie des workflows commerciaux de bout en bout.

AEM propose deux serveurs :

1. **Serveur MCP de contenu en lecture seule** pour récupérer du contenu en toute sécurité
1. **Serveur MCP de contenu en lecture/écriture** - pour apporter des modifications au contenu

Ces serveurs MCP comprennent des outils permettant d’utiliser **Pages**, **Fragments de contenu** et **Assets** et peuvent être utilisés à partir des clients MCP suivants : **ChatGPT**, **Claude**, **Cursor** et **Microsoft Copilot Studio**.

En savoir plus dans [Utilisation de MCP avec AEM Cloud Service](/help/ai-in-aem/mcp-support/using-mcp-with-aem-as-a-cloud-service.md). Pour toute question ou commentaire, envoyez un e-mail à l’adresse [aemcs-mcp-feedback@adobe.com](mailto:aemcs-mcp-feedback@adobe.com).

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

**Recherche optimisée par l&#39;IA**

Recherche optimisée par l&#39;IA offre une expérience de recherche intelligente et contextuelle qui va au-delà de la correspondance de mots-clés traditionnelle en comprenant la signification et l’intention derrière les requêtes des utilisateurs. Optimisé par l’IA et le machine learning, il fournit des résultats plus précis même lorsque les requêtes sont formulées différemment, contiennent des fautes d’orthographe, utilisent des synonymes ou sont envoyées dans différentes langues, ce qui permet aux utilisateurs et aux utilisatrices de trouver plus rapidement et avec moins d’efforts du contenu pertinent.

Pour plus d’informations, voir Recherche optimisée par l&#39;IA dans la vue Assets [&#128279;](/help/assets/search-assets-view.md#ai-search) et [vue Admin](/help/assets/search-assets.md#ai-search).

**Application de bureau version 3.0.1**

[L’application de bureau 3.0.1 (20 décembre 2025)](https://experienceleague.adobe.com/fr/docs/experience-manager-desktop-app/using/release-notes) améliore la fiabilité, les performances et la stabilité des workflows clés. Cette version assure la cohérence de l’affectation des noms de dossier en résolvant les problèmes de synchronisation avec l’auteur AEM, permet une utilisation ininterrompue de l’application lors des transferts actifs, améliore la réactivité de l’interface utilisateur par le biais d’un traitement asynchrone, optimise les transferts de fichiers volumineux avec pagination et résout les problèmes de stabilité, notamment les redémarrages et les blocages du serveur de création lors de téléchargements et de chargements de dossiers volumineux.

**Version Adobe Asset Link CEP 2026.01.0**

[Adobe Asset Link CEP 2026.01.0](https://helpx.adobe.com/fr/enterprise/using/adobe-asset-link.html) introduit une nouvelle option Rétablir les liens manquants dans InDesign qui rétablit automatiquement les liens d’autres ressources manquantes à partir du même dossier AEM. Cette fonctionnalité fait correspondre les ressources en fonction du nom de fichier, ce qui réduit considérablement les efforts manuels lors de la restauration des liens rompus.


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

**Améliorations apportées à l’espace réservé de la note de bas de page dans le Forms adaptatif (composants de base)**

* Ajout de la fonction [prise en charge multiligne avec sauts de ligne](/help/forms/footnotes-richtextsupport.md), qui permet une présentation plus claire et plus expressive du contenu de la note de bas de page.
* Les notes de bas de page restent désormais visibles de manière permanente dans l’espace réservé de note de bas de page, quelle que soit la visibilité des panneaux associés, ce qui garantit un accès cohérent aux informations essentielles.
  ![Note de bas de page descriptive.](/help/forms/assets/footnote-description.png){height=50%}

### Nouvelles fonctionnalités d’accès anticipé d’AEM Forms {#forms-new-early-access-features}

**Récupérer des valeurs d’un tableau JSON**

Fonctionnalités étendues des fonctions personnalisées pour [extraire des valeurs des tableaux JSON](/help/forms/invoke-service-enhancements-rule-editor.md#retrieve-property-values-from-a-json-array), reçues via un appel API, et les lier directement aux champs de formulaire adaptatif. Vous pouvez désormais développer une logique commerciale et des règles avec un mappage de données manuel minimal.

**Exécutez l’interface utilisateur associée sur une instance de publication**

Vous pouvez désormais exécuter l’[interface utilisateur associée](/help/forms/interactive-communication/associate-ui-in-interactive-communication-editor.md) directement sur les instances de publication. Cela permet à vos agents d’accéder à l’interface utilisateur associée et de personnaliser facilement les communications de vos clients.

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

### [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation Avis importants {#foundation-notices}

#### Obsolescence des API Java {#java-api-deprecation}

Les API obsolètes ciblant la suppression du 2/26/2026 ne doivent plus être utilisées dans le code. Pour empêcher les blocs de déploiement, supprimez l’utilisation de l’API avant le 26 mars 2026. Dates importantes :

* **À compter du 26 janvier 2026** : les e-mails de notification du Centre d’actions sont envoyés **chaque semaine par environnement** comme rappel pour supprimer l’utilisation de ces API.
* **26 février 2026** : les pipelines Cloud Manager qui contiennent du code à l’aide de ces API seront **mis en pause** pendant l’étape **Qualité du code**. Un responsable de déploiement, un chef de projet ou un propriétaire d’entreprise peut contourner le problème pour autoriser le pipeline à continuer.
* **26 mars 2026** : les pipelines Cloud Manager qui contiennent du code à l’aide de ces API échoueront **&#x200B;**&#x200B;pendant l’étape **Qualité du code**, **blocage des déploiements** du nouveau code jusqu’à ce que l’utilisation soit supprimée.
* **30 avril 2026** : les environnements qui utilisent toujours ces API peuvent **ne plus recevoir de mises à jour critiques de versions d’Adobe**.

Pour plus d’informations, consultez l’[article sur l’obsolescence](/help/release-notes/deprecated-removed-features.md#aem-apis), mais pour plus de commodité, ces API sont répertoriées ci-dessous :

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

#### Obsolescence de Java 11 Runtime {#java11-runtime-deprecation}

Adobe a mis à niveau les environnements **d’évaluation** et **de production** vers l’exécution Java 21 **hautes performances** le 14 octobre 2025. À compter du **9 février** (déploiement progressif jusqu’au 11 février), ni le SDK AEM Cloud Service ni les environnements cloud ne fonctionneront avec l’exécution Java 11.

>[!NOTE]
>
> Pour tirer parti des dernières optimisations des performances et améliorations du langage, il est recommandé de créer avec Java 17 ou Java 21 (recommandé). La création avec Java 8 et Java 11 reste prise en charge pour l’instant, mais sera abandonnée dans une prochaine version. Une communication distincte sera émise avant l’obsolescence. Voir la section *exigences en matière de temps de création* de [cet article](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements).
>

#### Application de la politique de configuration des journaux AEM Java {#logconfig-policy}

Les journaux Java d’AEM doivent respecter un format standard pour assurer une surveillance fiable dans tous les environnements client. Les configurations de journal personnalisées, telles que les modifications apportées à la mise en forme du journal, aux fichiers de sortie ou aux niveaux de journal par défaut, ne sont plus prises en charge. Les journaux doivent rester dirigés vers les fichiers par défaut et les niveaux de journal par défaut du code de produit AEM doivent être conservés. Consultez toutes les informations dans [l’article Journalisation](/help/implementing/developing/introduction/logging.md#configuration-loggers).

Tous les remplacements de journalisation personnalisée non pris en charge *sont désormais ignorés*. La plupart des clients n’ont pas été affectés et Adobe a contacté les clients dont la configuration actuelle peut être affectée.

Passez en revue et mettez à jour tous les processus en aval qui reposent sur un comportement de journalisation personnalisé. Par exemple :

* Si votre système de transfert de journal attend un format de journal personnalisé, vous devrez peut-être adapter vos règles d’ingestion.
* Si vous avez précédemment réduit le niveau de détail du journal en modifiant les niveaux de journal, sachez que le retour aux niveaux par défaut peut augmenter le volume du journal.

### [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation Early Adopter Caractéristiques {#foundation-early-adopter}

#### Suspendre les mises à jour de maintenance automatiques {#pause-updates}

Journées de mise en production, événements en direct, pic de ventes : pas d’erreur possible. [Nos nouvelles fonctionnalités en libre-service](/help/implementing/deploying/quiet-hours-update-free-periods.md) permettent de suspendre les mises à jour de maintenance automatique afin que vos équipes restent concentrées.

* Heures calmes : bloquez la maintenance automatique pendant des plages horaires définies chaque jour. Idéal pour les heures de travail, les exécutions de nuit ou les migrations du matin.
* Période sans mise à jour : bloquez la maintenance automatique pendant une semaine entière. Idéal pour les lancements, les promotions ou les périodes de verrouillage annuels.

>[!NOTE]
>
>En disponibilité limitée à partir du 25 septembre.
>Envoyez un e-mail à [aemcs-update-free@adobe.com](mailto:aemcs-update-free@adobe.com) pour l’activer dans vos programmes.
>

#### Fonctions D’AEM Edge (Programme Beta) {#edge-functions}

Les fonctions AEM Edge (appelées *Edge Computing* dans les notes de mise à jour précédentes) vous permettent d’exécuter JavaScript au niveau de la couche CDN, ce qui rapproche le traitement des données de l’utilisateur final. Cela réduit la latence et permet d’obtenir des expériences réactives et dynamiques en périphérie.

Cas d’utilisation courants :

* Personnalisation du contenu en fonction de la géolocalisation, du type d’appareil ou des attributs d’utilisateur ou d’utilisatrice
* Fonctionnement en tant que middleware entre le réseau CDN et votre origine
* Remise en forme des réponses d’API tierces (et éventuellement agrégation de plusieurs réponses d’API) avant de les diffuser au navigateur
* Composition et diffusion de HTML rendu sur le serveur Edge à l’aide de contenu assemblé à partir de divers serveurs principaux
* Exposition d’un serveur MCP pour les LLM tels que ChatGPT et Claude pour accéder aux outils personnalisés

Nous disposons d’un nombre limité d’opportunités pour la diffusion de l’instance de publication AEM ou les projets Edge Delivery Services pour les sites de production en direct. Si vous souhaitez participer ou en savoir plus, adressez un e-mail à [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) avec une brève description de votre cas d’utilisation.

#### Authentification Edge pour Edge Delivery Services (programme Beta) {#edge-authentication}

L’authentification Edge vous permet de restreindre l’accès aux pages Edge Delivery Services aux personnes qui se sont authentifiées auprès de votre fournisseur d’identité (IdP). Pour ce faire, déployez un fichier YAML de configuration OpenID Connect (OIDC).

Si cela vous intéresse, envoyez un e-mail à [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) avec une brève description de votre cas d’utilisation et toute question éventuelle.

#### Déploiements en production Canary pour tester le code avant d’accepter le trafic réel (programme Beta) {#canary-beta}

Validez une build de production avec du trafic de test interne uniquement avant de l’exposer aux utilisateurs finaux. Déployez en production, acheminez uniquement le trafic Canary (à l’aide d’un en-tête spécial), surveillez le comportement, puis convertissez-le en trafic réel ou restaurez, sans affecter les clients et clientes.

Déployez vos versions de code en production, mais limitez-les au trafic de test interne uniquement avant de décider d’accepter le trafic réel ou de restaurer.

Envoyez un e-mail à [aemcs-canary-deployments-beta@adobe.com](mailto:aemcs-canary-deployments-beta@adobe.com) pour demander l’accès et partager vos commentaires.

#### Instantanés pour les RDE (programme Beta) {#rde-snapshot-program}

Dans la version bêta, les environnements de développement rapide (RDE) prennent désormais en charge une fonctionnalité permettant de prendre un instantané de l’état actuel du code et du contenu, qui peut être restauré ultérieurement. Cela peut s’avérer utile lors de la synchronisation du code qui peut devoir être restauré à un état précédent ou, lorsqu’au cours du développement, il est nécessaire d’alterner entre plusieurs fonctionnalités différentes. Il est également possible de restaurer uniquement le contenu modifiable en tant que point de départ connu pour les tests.

Veuillez envoyer un e-mail à [aemcs-rde-support@adobe.com](mailto:aemcs-rde-support@adobe.com) si cette fonctionnalité vous intéresse et si vous souhaitez faire part de vos commentaires.

#### Outils d’IA pour les IDE pour le développement AEM Java et Dispatcher (programme Beta) {#ai-dev-beta}

Les équipes Java-stack utilisent de plus en plus le développement assisté par IA dans des outils tels que Cursor, Claude Code, Visual Studio et IntelliJ pour accélérer la diffusion des fonctionnalités et améliorer la qualité du code. Rejoignez la version bêta pour :

* Partagez des expériences concrètes pour façonner les futures fonctionnalités d’IA prises en charge par Adobe
* Testez les outils de l’IDE qui peuvent être utilisés par les agents de l’IA pour générer et déboguer le code AEM et la configuration du Dispatcher.

Envoyer un courrier électronique à l’adresse [aemcs-java-adopter@adobe.com](mailto:aemcs-java-adopter@adobe.com) pour plus d’informations.

#### Surveillance étendue des performances des applications (APM) (programme Alpha) {#apm-alpha}

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
