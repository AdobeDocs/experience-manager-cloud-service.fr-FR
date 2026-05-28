---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: ccca1d88486ff1c1ac2e9272287ce74bc0ac10b1
workflow-type: tm+mt
source-wordcount: '2225'
ht-degree: 28%

---

# Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour techniques de la version actuelle (la plus récente) d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes telles que 2024 ou 2025.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Pour recevoir chaque mois une notification par e-mail concernant des informations sur les notes de mise à jour d’Experience Cloud, abonnez-vous aux [Mises à jour de produits prioritaires d’Adobe](https://www.adobe.com/subscription/priority-product-update.html).

## Date de publication {#release-date}

La date de publication de la version actuelle (2026.5.0) de [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le 28 mai 2026. La prochaine version des fonctionnalités (2026.6.0) est prévue pour le 25 juin 2026.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

<!-- 

## Release Video {#release-video}

Have a look at the May 2026 Release Overview video for a summary of the features added in the 2026.5.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3491492/?captions=fre_fr&quality=12)

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

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités dans Content Hub {#new-features-content-hub}

**Recherche optimisée par l&#39;IA**

AEM Assets Content Hub comprend désormais Recherche optimisée par l&#39;IA, une fonctionnalité de recherche avancée qui permet de comprendre la signification et l’intention des requêtes des utilisateurs et utilisatrices au lieu de se fier uniquement à des correspondances exactes de mots-clés. Recherche optimisée par l&#39;IA fournit des résultats plus précis et contextuels en reconnaissant les relations entre les mots, les concepts et l’intention de l’utilisateur. Il prend en charge les requêtes multilingues, gère les fautes d’orthographe et les fautes de frappe, comprend les synonymes et affiche les ressources pertinentes même lorsque les utilisateurs n’utilisent pas les termes exacts des métadonnées.

Par exemple, une recherche de `Woman drinking coffee` peut également renvoyer des ressources balisées avec des termes associés, tels que `Lady`, `Girl`, `Latte` ou `Cappuccino`.

Les administrateurs peuvent activer ou désactiver Recherche optimisée par l&#39;IA dans Content Hub à l’aide du menu Configurations en sélectionnant Recherche optimisée par l&#39;IA ou la recherche traditionnelle par mot-clé.


**Options de tri personnalisé**

Content Hub permet désormais aux administrateurs d’activer les champs de métadonnées personnalisés en tant qu’options de tri sur la page d’accueil de Content Hub. Outre les options de tri par défaut, Taille, Modifié, Nom et Pertinence, les administrateurs peuvent configurer des champs de métadonnées spécifiques à l’entreprise tels que le canal, la région, le SKU ou la campagne pour aider les utilisateurs à organiser plus efficacement les résultats de la recherche.

**Prise en charge des événements de recherche et de téléchargement de ressources pour les API de diffusion**

Les API de diffusion AEM Assets prennent désormais en charge la recherche de ressources et les événements de téléchargement de ressources, ce qui permet aux entreprises de suivre et de répondre à la manière dont les ressources sont découvertes et utilisées dans les applications et expériences connectées. Ces événements permettent d’améliorer la visibilité sur les modèles d’utilisation des ressources, de prendre en charge les workflows d’analyse et de création de rapports et de simplifier les intégrations aux systèmes externes et les processus d’automatisation.

Grâce aux informations basées sur les événements, les équipes peuvent mieux comprendre l’engagement du contenu et créer des workflows de ressources numériques plus connectés. Pour plus d’informations, consultez la [documentation de l’API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/asset_downloaded).

>[!IMPORTANT]
>
>Ces fonctionnalités sont disponibles en tant que fonctionnalités à disponibilité limitée. Vous pouvez [créer et envoyer un dossier d’assistance client Adobe](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html) pour l’activer pour votre déploiement.

### Nouvelles fonctionnalités de Dynamic Media avec OpenAPI {#new-features-dynamic-media-openapi}

**Recadrage intelligent de vidéo**

Dynamic Media avec les fonctionnalités OpenAPI prennent désormais en charge les recadrages intelligents de vidéos pour les ressources vidéo dans AEM Assets. Les recadrages intelligents vidéo utilisent une analyse optimisée par l’IA pour garder automatiquement le sujet principal ciblé sur différents proportions et appareils, ce qui permet d’offrir des expériences de visionnage optimisées sur le web et les appareils mobiles. Une fois qu’elles sont activées et configurées par les administrateurs, les entreprises peuvent générer des sorties vidéo recadrées intelligentes pour les ressources approuvées et fournir de manière dynamique les images les plus appropriées pendant la lecture.

**Prise en charge des légendes et des pistes audio multiples pour les vidéos**

Dynamic Media avec les fonctionnalités OpenAPI prennent désormais en charge plusieurs légendes et plusieurs pistes audio pour les ressources vidéo. Il permet aux entreprises de diffuser des expériences vidéo localisées et accessibles à un public international en associant plusieurs sous-titres et pistes audio spécifiques à la langue à une seule vidéo principale. Les auteurs peuvent gérer efficacement ces suivis à partir d’une interface unifiée, ce qui simplifie la diffusion de contenu multilingue et prend en charge les exigences d’accessibilité régionales.

>[!IMPORTANT]
>
>Ces fonctionnalités sont disponibles en tant que fonctionnalités à disponibilité limitée. Vous pouvez [créer et envoyer un dossier d’assistance client Adobe](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html) pour l’activer pour votre déploiement.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités d’AEM Forms

* **Prise en charge du contrôle de version dans Forms Manager**
Forms Manager [prend désormais en charge le contrôle de version pour les Forms adaptatifs (composants principaux et composants de base)](/help/forms/manage-form-versions-forms-manager.md), les fragments de formulaire, les thèmes, les modèles XDP et les ressources binaires. Créez des versions, affichez l’historique complet des versions et restaurez les états précédents de vos ressources de formulaire directement à partir de la console Forms et documents.

* **Remplacer la configuration cloud reCAPTCHA avec OSGi** 
Les identifiants de projet d’entreprise reCAPTCHA, les clés de site et les secrets que vous conservez avec vos fichiers sources peuvent être résolus sur différentes valeurs dans chaque environnement Cloud Service après [ajout du remplacement de la configuration tenant compte du contexte et déploiement via Cloud Manager](/help/forms/captcha-adaptive-forms.md#override-recaptcha-osgi).

* **Authentification basée sur les certificats** 
Les Forms adaptatives qui envoient une liste Microsoft SharePoint prennent désormais en charge l’[authentification par certificat](/help/forms/connect-forms-to-sharepoint-list.md#certificate-based-authentication) ainsi que l’authentification par URL OAuth. Pour la connexion avec certificat, enregistrez un alias de certificat et les détails du client dans AEM et Microsoft Azure.

* **Améliorations de l’éditeur de règles**

   * L’éditeur de règles de Forms adaptatif prend désormais en charge la grammaire simplifiée pour les règles [Distribuer l’événement et Activer l’événement déclencheur) pour les déclencheurs prêts à l’emploi et pour les événements personnalisés](/help/forms/rule-editor-enhancements-use-cases.md#simplified-grammar-for-ootb-and-custom-events) afin que les auteurs ne soient pas limités à la grammaire sur les déclencheurs personnalisés uniquement.
   * Lorsque les règles sur les Forms adaptatives basées sur les composants principaux incluent désormais le composant [Pièce jointe avec d’autres conditions à l’aide de la logique AND ou OR](/help/forms/rule-editor-enhancements-use-cases.md#combined-when-conditions-with-the-file-attachment-component), la règle exécute ses actions uniquement lorsque l’état de la pièce jointe et les autres vérifications sont tous évalués comme prévu.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation Nouvelles fonctionnalités {#foundation-new}

#### Migration de code assisté par l’IA vers AEM as a Cloud Service {#aem-ide-cs-migration}

Accélérez votre migration d’AEM 6.5 (ou version antérieure) vers AEM as a Cloud Service (Java-stack) en utilisant l’outil IDE AI pour agir sur les recommandations du rapport de l’analyseur de bonnes pratiques.

En savoir plus sur [l’outil d’IA dédiée à l’IDE pour la migration vers le cloud](/help/journey-migration/cloud-migration-skill/overview-cloud-migration-skill.md) et sur d’autres [le développement local avec les outils d’IA](/help/ai-in-aem/local-development-with-ai-tools.md) (compétences des agents et serveurs MCP locaux).

>[!VIDEO](https://video.tv.adobe.com/v/3491440/?captions=fre_fr&quality=12)

#### Modifications de l’affichage du statut de la file d’attente de réplication {#replication-queue-status-display}

Dans l’interface utilisateur de création, les agents de réplication affichent désormais deux files d’attente consolidées (**persistantes** et **entièrement publiées**) au lieu de files d’attente distinctes par capsule de publication, ce qui réduit la complexité tout en reflétant la mise à l’échelle automatique du niveau de publication.

En savoir plus sur les [&#x200B; Files d’attente de réplication &#x200B;](/help/operations/replication.md#replication-queues).

![Files d’attente de réplication affichant les files d’attente &#x200B;](/help/operations/assets/replication-queues.png " réplication persistantes et entièrement publiées")

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

#### Gestion des heures creuses et mise à jour des périodes de disponibilité avec l’assistant AEM AI (disponibilité limitée) {#quiet-hours-ai}

Vous pouvez désormais afficher, créer et modifier des heures creuses et mettre à jour des périodes libres directement via l’assistant AEM AI.
L’avantage clé est la réduction des erreurs de planification. Lorsque vous effectuez une demande, l’assistant vous guide tout au long des étapes possibles et signale les limites qui s’appliquent, telles que la limite de trois périodes, l’intervalle obligatoire d’une semaine entre les périodes et les fenêtres d’exclusion de la maintenance planifiée que vous ne pouvez pas planifier. Ainsi, au lieu de découvrir une contrainte après une configuration ayant échoué, les propriétaires d’entreprise et les responsables de déploiement sont dirigés vers un planning valide dans la même conversation. Cela permet de protéger les fenêtres d’activité critiques contre les mises à jour de maintenance automatique tout en réduisant les allers-retours et les erreurs de configuration.

#### Instantanés pour les RDE (programme *Public Beta*) {#rde-snapshot-program}

Dans la version bêta publique (début juin), les environnements de développement rapide (RDE) prennent désormais en charge une fonctionnalité [pour prendre un instantané](/help/implementing/developing/introduction/rapid-development-environments.md#snapshots) de l’état actuel du code et du contenu, qui peut être restaurée ultérieurement. Cela peut s’avérer utile lors de la synchronisation du code qui peut devoir être restauré à un état précédent ou, lorsqu’au cours du développement, il est nécessaire d’alterner entre plusieurs fonctionnalités différentes. Il est également possible de restaurer uniquement le contenu modifiable en tant que point de départ connu pour les tests.

Début juin, la mise à jour vers les derniers plug-ins aio activera cette fonctionnalité.

*En utilisant le Beta d’instantanés du RDE, vous reconnaissez qu’il est toujours en cours de développement et que vous ne devez pas vous fier au bon fonctionnement de la technologie ou à la disponibilité des données. Bien que nous ayons largement testé cette fonctionnalité, il existe une petite possibilité que votre RDE devienne instable. Si cela se produit, une réinitialisation la restaurera à un état de fonctionnement.*


#### Fonctions D’AEM Edge (Programme Beta) {#edge-functions}

[Fonctions AEM Edge](/help/implementing/developing/introduction/edge-functions.md) vous permet d’exécuter JavaScript au niveau de la couche CDN, ce qui rapproche le traitement des données de l’utilisateur final. Cela réduit la latence et permet d’obtenir des expériences réactives et dynamiques en périphérie.

Cas d’utilisation courants :

* Personnalisation du contenu en fonction de la géolocalisation, du type d’appareil ou des attributs d’utilisateur ou d’utilisatrice
* Fonctionnement en tant que middleware entre le réseau CDN et votre origine
* Remise en forme des réponses d’API tierces (et éventuellement agrégation de plusieurs réponses d’API) avant de les diffuser au navigateur
* Composition et diffusion de HTML rendu sur le serveur Edge à l’aide de contenu assemblé à partir de divers serveurs principaux

Rejoignez la version bêta pour la diffusion de publication AEM ou les projets Edge Delivery Services pour les sites de production en direct. Si vous souhaitez participer ou en savoir plus, adressez un e-mail à [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) avec une brève description de votre cas d’utilisation.

#### Dépannage du pipeline de configuration de niveau web (programme Beta) {#devagent-webtier}

Les fonctionnalités [dépannage de pipeline](/help/ai-in-aem/agents/brand-experience/development/development.md) de l’agent de développement aident les développeurs à diagnostiquer et à résoudre efficacement les problèmes dans les déploiements d’AEM as a Cloud Service. En plus de prendre en charge les pipelines Full Stack (déploiement et qualité du code), l’agent de développement prend désormais en charge le dépannage du **pipeline de configuration de niveau web** dans le cadre d’un programme bêta.

Pour demander l’accès à la version bêta, envoyez un e-mail à l’adresse [&#128279;](mailto:aem-devagent@adobe.com). Un accès préexistant aux agents dans AEM est requis.

#### Dépannage de l’IA dédiée à la réplication (programme Beta) {#replication-ai-troubleshooting-alpha}

À l’aide de l’assistant AI dans l’instance de création AEM et d’autres interfaces, vous pouvez résoudre les problèmes liés à la réplication, tels que les files d’attente bloquées. Pour rejoindre le programme Beta, envoyez un e-mail à l’adresse [aem-devagent@adobe.com](mailto:aem-devagent@adobe.com) pour décrire votre intérêt.

#### Authentification Edge pour Edge Delivery Services (programme Beta) {#edge-authentication}

L’authentification Edge vous permet de restreindre l’accès aux pages Edge Delivery Services aux personnes qui se sont authentifiées auprès de votre fournisseur d’identité (IdP). Pour ce faire, déployez un fichier YAML de configuration OpenID Connect (OIDC).

Si cela vous intéresse, envoyez un e-mail à [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) avec une brève description de votre cas d’utilisation et toute question éventuelle.

#### Déploiements en production Canary pour tester le code avant d’accepter le trafic réel (programme Beta) {#canary-beta}

Validez une build de production avec du trafic de test interne uniquement avant de l’exposer aux utilisateurs finaux. Déployez en production, acheminez uniquement le trafic Canary (à l’aide d’un en-tête spécial), surveillez le comportement, puis convertissez-le en trafic réel ou restaurez, sans affecter les clients et clientes.

Envoyez un e-mail à [aemcs-canary-deployments-beta@adobe.com](mailto:aemcs-canary-deployments-beta@adobe.com) pour demander l’accès et partager vos commentaires.

#### Détection des problèmes de code dans AEM et correction automatique via l’agent IDE AI (programme Alpha) {#ide-ai-aemcode-issues}

Les équipes Java-stack utilisant le développement assisté par [IA](/help/ai-in-aem/local-development-with-ai-tools.md) dans des outils tels que Cursor, Claude Code, Visual Studio et IntelliJ peuvent désormais aller plus loin : une nouvelle compétence d’agent IDE détecte et corrige automatiquement les problèmes directement dans votre base de code AEM, réduisant ainsi les cycles de révision et détectant les problèmes plus tôt dans le développement.

Cette fonctionnalité est en version Alpha. Rejoignez le programme pour l’essayer et partager vos commentaires avec l’équipe sur [&#128279;](mailto:aemcs-ai-ide-tools-feedback@adobe.com).

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
