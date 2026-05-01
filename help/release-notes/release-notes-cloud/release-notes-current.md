---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: 0ba0b95eac6b3a3ca0aa6ed0a816edcc63b9d50f
workflow-type: tm+mt
source-wordcount: '2009'
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

La date de publication de la version actuelle (2026.4.0) de [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le 30 avril 2026. La prochaine version des fonctionnalités (2026.5.0) est prévue pour le 28 mai 2026.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

<!-- 
## Release Video {#release-video}

Have a look at the April 2026 Release Overview video for a summary of the features added in the 2026.4.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3483060/?quality=12)
-->

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

Voir [Programmes bêta &#x200B;](/help/implementing/cloud-manager/release-notes/current.md).

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Intégration de la traduction dans l’IA {#ai-translation-integration}

Les utilisateurs d’AEM peuvent désormais tirer parti des grands modèles de langue (LLM) pour la traduction de contenu, offrant ainsi une qualité de traduction humaine à la vitesse de la traduction automatique. Tout comme les services de traduction tiers traditionnels, Azure OpenAI peut être configuré en tant que fournisseur de traduction dans AEM, avec la prise en charge de LLM supplémentaires prévue pour les prochaines versions. Les clients utilisent leurs propres licences LLM pour cette fonctionnalité. En outre, les guides de style de traduction d’entreprise peuvent être chargés vers AEM, ce qui permet d’extraire les règles de traduction pour assurer la cohérence de la marque et du style. Consultez [&#x200B; Configuration de l’intégration de la traduction d’IA &#x200B;](/help/sites-cloud/administering/translation/ai-translation-integration.md) pour plus d’informations.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

**Le gestionnaire d’accès est désormais disponible pour les applications Adobe Workfront et non Adobe**

Le gestionnaire de contenu est désormais disponible pour les applications Adobe Workfront et non Adobe (tierces), ce qui permet d’étendre la découverte intelligente des ressources et la réutilisation du contenu au-delà d’Adobe Express et d’AEM Sites. Cette version apporte aux workflows Adobe Workfront et aux applications externes l’expérience complète du gestionnaire de contenu, notamment la recherche optimisée par l’IA, les recommandations contextuelles, la découverte basée sur des résumés de campagne, l’accès aux rendus Dynamic Media, la découverte de fragments de contenu, les filtres et les métadonnées de ressources.

Vous pouvez désormais découvrir, évaluer et réutiliser des ressources approuvées par AEM Assets directement dans vos applications préférées, ce qui permet une utilisation cohérente des ressources, une efficacité améliorée et une création de contenu rationalisée à la fois dans les applications Adobe et non Adobe.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités d’AEM Forms

* **Remplacer la configuration cloud reCAPTCHA avec OSGi** 
Les identifiants de projet d’entreprise reCAPTCHA, les clés de site et les secrets que vous conservez avec vos fichiers sources peuvent être résolus sur différentes valeurs dans chaque environnement Cloud Service après [ajout du remplacement de la configuration tenant compte du contexte et déploiement via Cloud Manager](/help/forms/captcha-adaptive-forms.md#override-recaptcha-osgi).

* **Authentification basée sur les certificats** 
Les Forms adaptatives qui envoient une liste Microsoft SharePoint prennent désormais en charge l’[authentification par certificat](/help/forms/connect-forms-to-sharepoint-list.md#certificate-based-authentication) ainsi que l’authentification par URL OAuth. Pour la connexion avec certificat, enregistrez un alias de certificat et les détails du client dans AEM et Microsoft Azure.

* **Améliorations de l’éditeur de règles**

   * L’éditeur de règles de Forms adaptatif prend désormais en charge la grammaire simplifiée pour les règles [Distribuer l’événement et Activer l’événement déclencheur) pour les déclencheurs prêts à l’emploi et pour les événements personnalisés](/help/forms/rule-editor-enhancements-use-cases.md#simplified-grammar-for-ootb-and-custom-events) afin que les auteurs ne soient pas limités à la grammaire sur les déclencheurs personnalisés uniquement.
   * Lorsque les règles sur les Forms adaptatives basées sur les composants principaux incluent désormais le composant [Pièce jointe avec d’autres conditions à l’aide de la logique AND ou OR](/help/forms/rule-editor-enhancements-use-cases.md#combined-when-conditions-with-the-file-attachment-component), la règle exécute ses actions uniquement lorsque l’état de la pièce jointe et les autres vérifications sont tous évalués comme prévu.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation Nouvelles fonctionnalités {#foundation-new}

#### Outils d’IA dédiée aux IDE pour le développement Java et Dispatcher d’AEM {#ai-dev}

Les équipes Java-stack utilisent de plus en plus le développement assisté par IA dans des outils tels que Cursor, Claude Code, Visual Studio et IntelliJ pour accélérer la diffusion des fonctionnalités et améliorer la qualité du code.

Les agents de codage peuvent utiliser l’outil IDE pour générer et déboguer le code AEM et la configuration du Dispatcher. À titre d’exemple, la présentation vidéo ci-dessous montre comment créer un composant AEM à l’aide des compétences de l’agent.

Apprenez-en davantage sur [le développement local avec les outils d’IA](/help/ai-in-aem/local-development-with-ai-tools.md) et n’hésitez pas à envoyer des questions ou des commentaires par e-mail à [aemcs-ai-ide-tools-feedback@adobe.com](mailto:aemcs-ai-ide-tools-feedback@adobe.com).


>[!VIDEO](https://video.tv.adobe.com/v/3484978/?learn=on&enablevpops)

#### Serveur MCP de gouvernance d’expérience {#gov-mcp-server}

Le serveur MCP d’Experience Governance est désormais disponible pour tous. Il s’intègre aux outils de développement et aux chatbots de l’IA qui prennent en charge le protocole MCP (Model Context Protocol), ce qui vous permet de protéger l’intégrité et la conformité de la marque à l’aide d’invites en langage naturel dans votre chatbot ou votre IDE. Vous pouvez évaluer le contenu (texte, images, pages) par rapport aux règles de gouvernance de marque, et récupérer les configurations de marque et les contrôles de gouvernance disponibles.

En savoir plus sur les [serveurs AEM MCP](/help/ai-in-aem/mcp-support/using-mcp-with-aem-as-a-cloud-service.md) et l’[agent de gouvernance](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/ai-in-aem/agents/governance/overview).

#### Claude Connector {#aem-claude-connector}

Les utilisateurs Claude peuvent parcourir la [marketplace du connecteur](https://claude.ai/settings/connectors) d&#39;Anthropic pour installer en 1 clic le [connecteur Adobe Experience Manager](/help/ai-in-aem/mcp-support/setup-claude.md#aem-claude-connector). Ce serveur MCP expose un ensemble croissant d’outils permettant d’interagir avec AEM, notamment pour modifier le contenu à l’aide d’invites.

#### OIDC AEM sur la publication de nouvelles fonctionnalités {#aem-oidc-on-publish-new-features}

* Correction : les paramètres de requête de la requête originale sont perdus après l’authentification
* Redirection personnalisée après l’authentification dans l’authentification OIDC [documentation](/help/security/open-id-connect-support-for-aem-as-a-cloud-service-on-publish-tier.md#custom-redirect-after-authentication)

#### Prise en charge du service de messagerie pour l’API Microsoft Graph {#mail-service-graph-api}

Le service de messagerie AEM prend désormais en charge Microsoft® Outlook (via Microsoft 365) à l’aide de l’API Microsoft Graph. Cela s’avère particulièrement utile pour les organisations qui n’autorisent pas le protocole SMTP, qui est déjà pris en charge par le service de messagerie. Authentification via OAuth 2.0. [Découvrez comment configurer](/help/security/oauth2-support-for-mail-service.md#microsoft-graph-api).

#### Les journaux CDN peuvent être transférés à la logique Sumo {#sumo-cdn-logforwarding}

La fonctionnalité [Transfert de journal](/help/implementing/developing/introduction/log-forwarding.md#sumologic) prend désormais en charge l’envoi de journaux CDN à Sumo Logic. Auparavant, le transfert des journaux vers Sumo Logic se limitait aux journaux AEM.

### [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation Avis importants {#foundation-notices}

#### Erreurs enrichies d’authentification IMS {#ims-auth-rich-errors}

Pour faciliter le dépannage des intégrations IMS, `imsauth` a ajouté la prise en charge des *erreurs riches*.

Au lieu de renvoyer uniquement un code d’état HTTP, ces erreurs fournissent un contexte supplémentaire pour aider à diagnostiquer et à résoudre les problèmes qui peuvent bloquer l’authentification et l’accès.

#### Obsolescence des API Java {#java-api-deprecation}

Il est essentiel de supprimer l’utilisation des API obsolètes.

Depuis le **14 avril**, les pipelines Cloud Manager qui contiennent du code à l’aide d’API ciblant la suppression du 2/26/2026 **échouent lors de l’étape Qualité du code**. Les déploiements seront bloqués jusqu’à ce que l’utilisation obsolète de l’API soit supprimée. *Cela peut vous empêcher de publier des mises à jour urgentes et peut avoir un impact sur vos opérations commerciales.*

À compter du **11 juin 2026**, les environnements qui utilisent toujours ces API obsolètes **ne recevront pas de mises à jour de versions Adobe critiques** et ne seront pas soumis aux engagements standard d’Adobe en matière de performances et de disponibilité. Par conséquent, vous ne recevrez pas de nouvelles fonctionnalités ou de nouveaux correctifs, la stabilité et la disponibilité des applications peuvent être affectées négativement, et l&#39;exposition aux risques de sécurité peut encore augmenter.

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

### [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation Early Adopter Caractéristiques {#foundation-early-adopter}

#### Fonctions D’AEM Edge (Programme Beta) {#edge-functions}

[Fonctions AEM Edge](/help/implementing/developing/introduction/edge-functions.md) vous permet d’exécuter JavaScript au niveau de la couche CDN, ce qui rapproche le traitement des données de l’utilisateur final. Cela réduit la latence et permet d’obtenir des expériences réactives et dynamiques en périphérie.

Cas d’utilisation courants :

* Personnalisation du contenu en fonction de la géolocalisation, du type d’appareil ou des attributs d’utilisateur ou d’utilisatrice
* Fonctionnement en tant que middleware entre le réseau CDN et votre origine
* Remise en forme des réponses d’API tierces (et éventuellement agrégation de plusieurs réponses d’API) avant de les diffuser au navigateur
* Composition et diffusion de HTML rendu sur le serveur Edge à l’aide de contenu assemblé à partir de divers serveurs principaux
* Exposer un serveur MCP pour les assistants d’IA tels que ChatGPT et Claude pour accéder aux outils personnalisés

Nous disposons d’un nombre limité d’opportunités pour la diffusion de l’instance de publication AEM ou les projets Edge Delivery Services pour les sites de production en direct. Si vous souhaitez participer ou en savoir plus, adressez un e-mail à [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) avec une brève description de votre cas d’utilisation.

#### Dépannage du pipeline de configuration de niveau web (programme Beta) {#devagent-webtier}

Les fonctionnalités [dépannage de pipeline](/help/ai-in-aem/agents/brand-experience/development/development.md) de l’agent de développement aident les développeurs à diagnostiquer et à résoudre efficacement les problèmes dans les déploiements d’AEM as a Cloud Service. En plus de prendre en charge les pipelines Full Stack (déploiement et qualité du code), l’agent de développement prend désormais en charge le dépannage du **pipeline de configuration de niveau web** dans le cadre d’un programme bêta.

Pour demander l’accès à la version bêta, envoyez un e-mail à l’adresse [&#128279;](mailto:aem-devagent@adobe.com). Un accès préexistant aux agents dans AEM est requis.

#### Dépannage de l’IA dédiée à la réplication (programme Alpha) {#replication-ai-troubleshooting-alpha}

À l’aide de l’assistant AI dans l’instance de création AEM et d’autres interfaces, vous pouvez résoudre les problèmes liés à la réplication, tels que les files d’attente bloquées. Pour rejoindre le programme Alpha, envoyez un e-mail à l’adresse [aem-devagent@adobe.com](mailto:aem-devagent@adobe.com) pour décrire votre intérêt.

#### Outils d’IA dédiée à l’IDE pour la migration d’AEM 6.5 vers AEM Cloud Service (programme Beta) {#cm-ide-migration}

Accélérez votre migration d’AEM 6.5 vers AEM as a Cloud Service (pile Java) en utilisant l’outil d’IA dédiée à l’environnement de développement intégré pour agir sur les recommandations du rapport [Analyseur des bonnes pratiques](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md).

Envoyer un e-mail à [&#128279;](mailto:aemcs-ai-ide-tools-feedback@adobe.com) pour obtenir plus d’informations et demander l’accès à la fonctionnalité.

#### Authentification Edge pour Edge Delivery Services (programme Beta) {#edge-authentication}

L’authentification Edge vous permet de restreindre l’accès aux pages Edge Delivery Services aux personnes qui se sont authentifiées auprès de votre fournisseur d’identité (IdP). Pour ce faire, déployez un fichier YAML de configuration OpenID Connect (OIDC).

Si cela vous intéresse, envoyez un e-mail à [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) avec une brève description de votre cas d’utilisation et toute question éventuelle.

#### Déploiements en production Canary pour tester le code avant d’accepter le trafic réel (programme Beta) {#canary-beta}

Validez une build de production avec du trafic de test interne uniquement avant de l’exposer aux utilisateurs finaux. Déployez en production, acheminez uniquement le trafic Canary (à l’aide d’un en-tête spécial), surveillez le comportement, puis convertissez-le en trafic réel ou restaurez, sans affecter les clients et clientes.

Envoyez un e-mail à [aemcs-canary-deployments-beta@adobe.com](mailto:aemcs-canary-deployments-beta@adobe.com) pour demander l’accès et partager vos commentaires.

#### Instantanés pour les RDE (programme Beta) {#rde-snapshot-program}

Dans la version bêta, les environnements de développement rapide (RDE) prennent désormais en charge une fonctionnalité [pour prendre un instantané](/help/implementing/developing/introduction/rapid-development-environments.md#snapshots) de l’état actuel du code et du contenu, qui peut être restaurée ultérieurement. Cela peut s’avérer utile lors de la synchronisation du code qui peut devoir être restauré à un état précédent ou, lorsqu’au cours du développement, il est nécessaire d’alterner entre plusieurs fonctionnalités différentes. Il est également possible de restaurer uniquement le contenu modifiable en tant que point de départ connu pour les tests.

Veuillez envoyer un e-mail à [&#128279;](mailto:aemcs-rde-support@adobe.com) si cette fonctionnalité vous intéresse et si vous souhaitez faire part de vos commentaires.

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
