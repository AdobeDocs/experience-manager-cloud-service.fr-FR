---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: eae7609f3f35f17a6c31cf242b6b0cc2d464a3fb
workflow-type: tm+mt
source-wordcount: '1961'
ht-degree: 35%

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

La date de publication de la version actuelle d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2026.2.0) est le mercredi 3 mars 2026. La prochaine disponibilité des fonctionnalités (2026.3.0) est prévue pour le vendredi 26 mars 2026.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

## Vidéo de mise à jour {#release-video}

Consultez la vidéo Aperçu de la mise à jour de février 2026 pour un résumé des fonctionnalités ajoutées dans la version 2026.2.0 :

>[!VIDEO](https://video.tv.adobe.com/v/3480399/?quality=12)


## Programmes AEM Beta {#aem-beta-programs}

Les programmes bêta Adobe Experience Manager (AEM) permettent aux clients d’accéder aux fonctionnalités et au code de version préliminaire, de faire part de leurs commentaires et de guider l’avenir d’AEM.

>[!IMPORTANT]
>
>Les versions de Beta peuvent contenir des défauts et sont fournies « EN L’ÉTAT » sans garantie d’aucune sorte. Adobe n’a aucune obligation de tenir à jour, corriger, mettre à jour, modifier, remplacer ou prendre en charge (par le biais des services d’assistance Adobe ou d’une autre manière) les versions bêta. Adobe conseille aux clients d’être prudent et de ne pas se fier au bon fonctionnement ou aux performances des versions bêta, ni à la documentation ou aux documents d’accompagnement. Les fonctionnalités et API de la version bêta peuvent être modifiées sans préavis. Par conséquent, toute utilisation des versions bêta s’effectue entièrement aux risques et périls du client.

**Avantages de la participation**
L’accès anticipé aux fonctionnalités développées par Adobe permet aux clients et aux partenaires de faire part de leurs commentaires et de façonner le développement des produits. Cela les aide également à se préparer à adopter de nouvelles fonctionnalités avant leur disponibilité générale.

**Programmes bêta actuels**
Les sections suivantes répertorient les programmes bêta actifs.

### Agents dans AEM {#agents-in-aem}

Si vous souhaitez explorer les nouvelles et puissantes fonctionnalités d’AEM dans les domaines de la production, de la gouvernance, de l’optimisation, de la découverte et du développement, [découvrez comment y accéder ici.](/help/ai-in-aem/agents/overview.md)

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

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

**Gestionnaire de contenu pour accéder à AEM Assets dans Adobe Express**

[Le gestionnaire d’accès est désormais disponible dans Adobe Express](/help/assets/native-integration-adobe-express.md) et permet une découverte intelligente des ressources pour AEM Assets directement dans l’interface Express. Le gestionnaire de contenu fournit des recommandations contextuelles basées sur le contenu de la zone de travail et des résumés de campagne, prend en charge les recherches optimisées par l’IA, active la prise en charge native des rendus prêts pour le canal à la volée optimisés par Dynamic Media, et bien d’autres fonctionnalités. Content Advisor transforme la manière dont vous découvrez et utilisez les ressources approuvées, vous permettant de trouver plus rapidement le contenu approprié afin de rationaliser vos workflows créatifs.

### Nouvelles fonctionnalités de Dynamic Media avec OpenAPI {#dynamic-media-openAPI-new-features}

**Contrôle d’accès basé sur les attributs (ABAC) pour Dynamic Media avec OpenAPI**

Le contrôle d’accès basé sur les attributs (ABAC) permet aux administrateurs de contrôler l’accès à Dynamic Media avec des ressources OpenAPI à l’aide de règles pilotées par les métadonnées. Les administrateurs peuvent définir des règles pour les groupes d’utilisateurs en fonction des métadonnées des ressources afin de déterminer quelles ressources sont visibles pour des groupes spécifiques. Lorsque les métadonnées d’une ressource correspondent aux conditions définies, l’accès est automatiquement accordé. Cette fonctionnalité aide les entreprises à appliquer une meilleure gouvernance, en veillant à ce que les utilisateurs puissent uniquement afficher et travailler avec Dynamic Media avec des ressources OpenAPI pertinentes pour leur rôle ou leurs autorisations.

>[!NOTE]
>
>Le contrôle d’accès basé sur les attributs (ABAC) pour Dynamic Media avec OpenAPI est une fonctionnalité à disponibilité limitée. Vous pouvez l’activer en créant un [&#x200B; ticket d’assistance &#x200B;](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html).

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Fonctionnalités d’accès anticipé d’AEM Forms {#forms-early-access-features}

**Afficher les libellés pour la liste déroulante à sélection multiple dans Submission PDF**
Les composants de liste déroulante à sélection multiple dans le Forms adaptatif effectuent désormais le rendu de leurs libellés d’affichage sélectionnés dans la [PDF d’envoi générée](/help/forms/generate-document-of-record-core-components.md), en s’assurant que le document reflète précisément ce que les utilisateurs voient sur le formulaire.

**Amélioration de l’accessibilité des composants de case à cocher, de bouton radio et de panneau**
Les composants principaux de Forms adaptatifs introduisent le balisage sémantique compatible avec WCAG 2.2 pour les [groupes de cases à cocher (v2)](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/checkbox-group), [groupes de boutons radio (v2)](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/radio-button) et le [composant de panneau](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel). Ces composants exploitent les éléments HTML `<fieldset>` et `<legend>` pour établir des relations significatives entre les libellés de groupe et leurs options, ce qui permet une interprétation précise par les lecteurs d’écran et d’autres technologies d’assistance.

**Prise en charge des versions dans Forms Manager**
Forms Manager [prend désormais en charge le contrôle de version pour les Forms adaptatifs (composants principaux et composants de base)](/help/forms/manage-form-versions-forms-manager.md), les fragments de formulaire, les thèmes, les modèles XDP et les ressources binaires. Créez des versions, affichez l’historique complet des versions et restaurez les états précédents de vos ressources de formulaire directement à partir de la console Forms et documents.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation Nouvelles fonctionnalités {#foundation-new}

#### Suspendre les mises à jour de maintenance automatiques {#pause-updates}

Journées de mise en production, événements en direct, pic de ventes : pas d’erreur possible. [Nos nouvelles fonctionnalités en libre-service](/help/implementing/deploying/quiet-hours-update-free-periods.md) permettent de suspendre les mises à jour de maintenance automatique afin que vos équipes restent concentrées.

* Heures calmes : bloquez la maintenance automatique pendant des plages horaires définies chaque jour. Idéal pour les heures de travail, les exécutions de nuit ou les migrations du matin.
* Période sans mise à jour : bloquez la maintenance automatique pendant une semaine entière. Idéal pour les lancements, les promotions ou les périodes de verrouillage annuels.

#### Dépannage du pipeline de qualité du code avec l’agent de développement {#devagent-codequality}

Les fonctionnalités de dépannage du pipeline de l’agent de développement aident les développeurs à diagnostiquer et à résoudre plus efficacement les problèmes liés aux déploiements d’AEM as a Cloud Service.

Précédemment axé sur l’étape **Créer et tester l’unité**, le dépannage de pipeline prend désormais en charge l’étape **Analyse de code** dans les pipelines Déploiement de pile complète et Qualité du code.

L’étape d’analyse du code évalue le code par rapport aux règles de qualité, détecte les vulnérabilités de sécurité et génère des rapports de qualité détaillés. Si cette étape échoue, vous pouvez utiliser l’assistant AI pour demander à l’agent de développement une analyse de la cause première ainsi que des conseils de correction recommandés.

En savoir plus sur l’[agent de développement](/help/ai-in-aem/agents/brand-experience/development/development.md) et le dépannage du pipeline.

### [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation Avis importants {#foundation-notices}

#### Obsolescence des API Java {#java-api-deprecation}

Les API obsolètes ciblant la suppression du 2/26/2026 ne doivent plus être utilisées dans le code. Pour empêcher les blocs de déploiement, supprimez l’utilisation de l’API avant le 30 mars 2026. Dates importantes :

* **À compter du 26 janvier 2026** : les e-mails de notification du Centre de maintenance sont envoyés comme rappel pour supprimer l’utilisation de ces API.
* **26 février 2026** : les pipelines Cloud Manager qui contiennent du code à l’aide de ces API seront **mis en pause** pendant l’étape **Qualité du code**. Un responsable de déploiement, un chef de projet ou un propriétaire d’entreprise peut contourner le problème pour autoriser le pipeline à continuer. *Cela peut ralentir votre capacité à valider et à publier les modifications de code.*
* **30 mars 2026** : les pipelines Cloud Manager qui contiennent du code à l’aide de ces API échoueront **&#x200B;**&#x200B;lors de l’étape **Qualité du code**. Les déploiements seront bloqués jusqu’à ce que l’utilisation obsolète de l’API soit supprimée. *Cela peut vous empêcher de publier des mises à jour urgentes et peut avoir un impact sur vos opérations commerciales.*
* **4 mai 2026** : les environnements qui utilisent toujours des API obsolètes **ne recevront pas de mises à jour de versions Adobe critiques** et ne sont pas soumis aux engagements standard d’Adobe en matière de performances et de disponibilité. Par conséquent, vous ne recevrez pas de nouvelles fonctionnalités ou de nouveaux correctifs, la stabilité et la disponibilité des applications peuvent être affectées négativement et l&#39;exposition aux risques de sécurité peut encore augmenter.

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
* `org.apache.jackrabbit.oak.plugins.memory`

+++

<!--
OSGi properties:

* `org.apache.sling.commons.log.LogManager` (all properties)
* `org.apache.sling.commons.log.LogManager.factory.config` (`org.apache.sling.commons.log.file`, `org.apache.sling.commons.log.pattern`)
* 

-->

### [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation Early Adopter Caractéristiques {#foundation-early-adopter}

#### Fonctions D’AEM Edge (Programme Beta) {#edge-functions}

AEM Edge Functions vous permet d’exécuter JavaScript au niveau de la couche CDN, ce qui rapproche le traitement des données de l’utilisateur final. Cela réduit la latence et permet d’obtenir des expériences réactives et dynamiques en périphérie.

Cas d’utilisation courants :

* Personnalisation du contenu en fonction de la géolocalisation, du type d’appareil ou des attributs d’utilisateur ou d’utilisatrice
* Fonctionnement en tant que middleware entre le réseau CDN et votre origine
* Remise en forme des réponses d’API tierces (et éventuellement agrégation de plusieurs réponses d’API) avant de les diffuser au navigateur
* Composition et diffusion de HTML rendu sur le serveur Edge à l’aide de contenu assemblé à partir de divers serveurs principaux
* Exposition d’un serveur MCP pour les LLM tels que ChatGPT et Claude pour accéder aux outils personnalisés

Nous disposons d’un nombre limité d’opportunités pour la diffusion de l’instance de publication AEM ou les projets Edge Delivery Services pour les sites de production en direct. Si vous souhaitez participer ou en savoir plus, adressez un e-mail à [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) avec une brève description de votre cas d’utilisation.

#### Serveur MCP Cloud Manager (programme Beta) {#cm-mcp-server}

>[!VIDEO](https://video.tv.adobe.com/v/3480340/?quality=12)

Les IDE modernes utilisent le protocole MCP (Model Context Protocol) pour permettre aux modèles de langage volumineux (LLM) d’appeler les outils exposés par les serveurs MCP. Au lieu d’intégrer directement les spécifications d’API de bas niveau, l’équipe de développement peut simplement décrire son intention en langage naturel.

Désormais disponible en version bêta, le serveur Cloud Manager MCP vous permet d’interagir avec les API Cloud Manager directement depuis votre IDE à l’aide d’invites. Les scénarios pris en charge comprennent l’exécution des pipelines, la vérification du statut de l’environnement, etc.

En savoir plus sur les [serveurs AEM MCP](/help/ai-in-aem/mcp-support/using-mcp-with-aem-as-a-cloud-service.md). Pour demander l’accès au serveur MCP Cloud Manager en version bêta, envoyez un e-mail à l’adresse [aemcs-mcp-feedback@adobe.com](mailto:aemcs-mcp-feedback@adobe.com) et joignez une description de votre cas d’utilisation.

#### Dépannage du pipeline de configuration de niveau web avec l’agent de développement (programme Beta) {#devagent-webtier}

Les fonctionnalités [dépannage de pipeline](/help/ai-in-aem/agents/brand-experience/development/development.md) de l’agent de développement aident les développeurs à diagnostiquer et à résoudre efficacement les problèmes dans les déploiements d’AEM as a Cloud Service. En plus de prendre en charge les pipelines Full Stack (déploiement et qualité du code), l’agent de développement prend désormais en charge le dépannage du **pipeline de configuration de niveau web** dans le cadre d’un programme bêta.

Pour demander l’accès à la version bêta, envoyez un e-mail à l’adresse [aem-devagent@adobe.com](mailto:aem-devagent@adobe.com). Un accès préexistant aux agents dans AEM est requis.

>[!NOTE]
>
>Disponible en tant que fonctionnalité de responsabilité le 25 septembre.
>Envoyez un e-mail à [aemcs-update-free@adobe.com](mailto:aemcs-update-free@adobe.com) pour l’activer dans vos programmes.
>

#### Outils d’IA dédiée à l’IDE pour le développement AEM Java et Dispatcher (programme Beta) {#ai-dev-beta}

Les équipes Java-stack utilisent de plus en plus le développement assisté par IA dans des outils tels que Cursor, Claude Code, Visual Studio et IntelliJ pour accélérer la diffusion des fonctionnalités et améliorer la qualité du code. Rejoignez la version bêta pour :

* Partagez des expériences concrètes pour façonner les futures fonctionnalités d’IA prises en charge par Adobe
* Testez les outils de l’IDE qui peuvent être utilisés par les agents de l’IA pour générer et déboguer le code AEM et la configuration du Dispatcher.

Envoyer un courrier électronique à l’adresse [aemcs-java-adopter@adobe.com](mailto:aemcs-java-adopter@adobe.com) pour plus d’informations.

#### Outils d’IA dédiée à l’IDE pour la migration d’AEM 6.5 vers AEM Cloud Service (programme Alpha) {#cm-ide-migration}

Accélérez votre migration d’AEM 6.5 vers AEM as a Cloud Service (pile Java) en utilisant l’outil d’IA dédiée à l’environnement de développement intégré pour agir sur les recommandations du rapport [Analyseur des bonnes pratiques](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md).

Envoyer un courrier électronique à l’adresse [aem-devagent@adobe.com](mailto:aem-devagent@adobe.com) pour plus d’informations.

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
