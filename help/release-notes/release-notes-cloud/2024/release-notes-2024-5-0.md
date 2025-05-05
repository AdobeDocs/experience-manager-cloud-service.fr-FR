---
title: Notes de mise à jour de la version 2024.5.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la version 2024.5.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 7b7a27f9-ba57-4eb2-9fcb-653b5213af04
source-git-commit: a8c74573134597e83c2720de3b2a0f75ff7896a2
workflow-type: tm+mt
source-wordcount: '1949'
ht-degree: 99%

---

# Notes de mise à jour de la version 2024.5.0 d’[!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour de la version 2024.5.0 d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes, telles que 2022 ou 2023.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de la version actuelle (2024.5.0) d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le 30 mai 2024. La prochaine mise à jour des fonctionnalités (2024.6.0) est prévue pour le 27 juin 2024.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

## Vidéo de mise à jour {#release-video}

Consultez la vidéo Vue d’ensemble de la version de mai 2024 pour obtenir un résumé des fonctionnalités ajoutées dans la version 2024.5.0 :

>[!VIDEO](https://video.tv.adobe.com/v/3448064?quality=12&captions=fre_fr)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités de Sites {#sites-new-features}

#### Intégration de la traduction AEM {#translation-integration}

Les actions et les workflows de traduction de contenu déclenchent désormais des événements pour permettre le suivi des étapes et des états de processus pertinents à partir d’applications externes. Les événements suivants sont en cours de génération. Les personnes pourront s’abonner aux événements à l’aide d’Adobe Developer Console.

* `TRANSLATION_JOB_CREATED`
* `TRANSLATION_JOB_CONTENT_ADDITION_STARTED`
* `TRANSLATION_JOB_CONTENT_ADDITION_COMPLETED`
* `TRANSLATION_JOB_CONTENT_DELETION_STARTED`
* `TRANSLATION_JOB_CONTENT_DELETION_COMPLETED`
* `TRANSLATION_JOB_COMMITTED_FOR_TRANSLATION`
* `TRANSLATION_JOB_READY_FOR_REVIEW`
* `TRANSLATION_JOB_APPROVED`
* `TRANSLATION_JOB_COMPLETED`
* `TRANSLATION_JOB_CANCELLED`
* `TRANSLATION_JOB_ERROR`

#### Service de surveillance des utilisateurs et utilisatrices en temps réel (RUM) {#real-use-monitoring}

* **[Le service de données Real User Monitoring (surveillance des utilisateurs et utilisatrices en temps réel, RUM) est désormais en disponibilité générale](/help/implementing/cloud-manager/content-requests.md#real-user-monitoring-for-aem-as-a-cloud-service)**. Il permet la collecte de données côté client pour AEM as a Cloud Service.
Le service de surveillance des utilisateurs et utilisatrices en temps réel (RUM) et sa collecte côté client offrent un reflet plus précis des interactions, assurant ainsi une mesure fiable de l’engagement du site web. Il dote la clientèle d’informations avancées sur le trafic et les performances de leurs pages. Il permet d’approfondir les performances de vos pages et d’obtenir des informations pour les améliorer.

#### Création AEM pour Edge Delivery Services {#edge-enhancements}

Stabilité améliorée et différentes améliorations pour une meilleure expérience de création.

### Programme d’adoption précoce {#sites-early-adopter}

**Générer des variations**

Tirez profit de GenAI grâce à une nouvelle fonctionnalité d’AEM, [générer des variations](/help/generative-ai/generate-variations.md), maintenant accessible dans Cloud Service. La génération de variations vous permet de générer et d’adapter la création de contenu grâce à l’utilisation de l’IA générative. Contactez votre équipe Adobe en charge des comptes pour en savoir plus sur le programme.

**Explorer les ressources dans la console de fragments de contenu**

Les auteurs et les autrices de contenu peuvent désormais parcourir, afficher et agir sur les images et d’autres ressources sans avoir à quitter la console de fragments de contenu.

![Explorer des ressources](/help/sites-cloud/administering/content-fragments/assets/cf-console-assets-browse.png)

Vous souhaitez tester la fonctionnalité et partager vos commentaires ? Envoyez un e-mail à aemcs-headless-adopter@adobe.com à partir de votre ID d’e-mail officiel pour en savoir plus le programme d’adoption précoce.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de la vue d’administration {#admin-view-new-features}

* WebM est désormais un fichier de sortie pris en charge dans le profil de traitement pour la vidéo.
* MP4 est désormais pris en charge dans l’intégration native d’AEM dans Express (import et export).

### Nouvelles fonctionnalités de la vue Assets {#assets-view-new-features}

**Publier des ressources sur AEM et Dynamic Media**

Experience Manager Assets vous permet désormais de rapidement [publier des ressources dans Experience Manager et Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md) à l’aide de la vue Assets sans passer à la vue Admin. Vous pouvez publier des ressources lors du chargement, de la navigation et de la recherche de ressources.

![check publish status1](/help/assets/assets/check-publish-status1.png)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Nouvelles fonctionnalités de la version préliminaire d’AEM Forms {#forms-new-prerelease-features}

#### Éditeur de règles visuel amélioré pour les formulaires adaptatifs basés sur les composants principaux

Cette version introduit une mise à niveau significative de l’éditeur de règles visuel pour les formulaires adaptatifs basés sur les composants principaux. Vous pouvez maintenant effectuer les tâches suivantes :

* Créez des règles dans l’éditeur de règles visuel pour [remplacer les messages de succès/d’échec d’envoi de formulaire par défaut](/help/forms/create-and-use-custom-functions.md#use-case-override-form-submission-success-and-error-handlers).

* Dans l’éditeur de règles des formulaires adaptatifs, ajout de la possibilité de [sélectionner différents types de champs pour l’opération WHEN (lorsque)](/help/forms/rule-editor-core-components.md#allowed-multiple-fields-in-when).

* FORMS-12052 : un auteur ou une autrice de formulaire peut désormais appliquer des fonctions personnalisées pour [prétraiter les données avant l’envoi](/help/forms/create-and-use-custom-functions.md#use-case-submit-altered-data-to-the-server).

* Utilisez la fonctionnalité [**Enregistrer en tant que brouillon**](/help/forms/save-core-component-based-form-as-draft.md) pour enregistrer des formulaires partiellement remplis en vue d’un envoi ultérieur. Cela s’avère utile lorsque les utilisateurs et utilisatrices doivent interrompre le remplissage d’un formulaire et y revenir ultérieurement.



### Fonctionnalités d’accès anticipé dans AEM Forms {#forms-new-early-access-features}

Le programme d’accès anticipé d’AEM Forms vous offre une opportunité unique d’accéder de manière exclusive à des innovations de pointe avant toute autre personne et de contribuer à façonner leur développement. Le programme offre l’accès à de multiples innovations.

Les notes de mise à jour répertorient les innovations apportées à la version actuelle. Pour obtenir la liste complète des innovations disponibles dans le cadre du programme d’accès anticipé, voir [Documentation du programme d’accès anticipé d’AEM Forms](/help/forms/early-access-ea-features.md).

#### Amélioration des méthodes de protection des robots

AEM Forms a amélioré ses fonctionnalités de sécurité en ajoutant la prise en charge de deux solutions Captcha populaires : Cloudflare Turnstile et hCaptcha. Cela vient s’ajouter au reCAPTCHA de Google déjà disponible, offrant ainsi aux utilisateurs et utilisatrices plus de choix et de flexibilité pour protéger leurs formulaires contre les robots et les spams envoyés.

* **Cloudflare Turnstile** : ce Captcha sans friction vérifie les utilisateurs et utilisatrices par le biais d’un simple défi qui ne nécessite pas d’interaction explicite. Il s’intègre de manière transparente à vos formulaires, améliorant ainsi l’expérience client.
* **hCaptcha** : ce Captcha axé sur la confidentialité offre une alternative conviviale qui met l’accent sur la confidentialité des données. Il vise à trouver un équilibre entre la sécurité et l’expérience client.
* **Google reCAPTCHA** : AEM Forms continue à prendre en charge reCAPTCHA v2 et reCAPTCHA Enterprise, offrant ainsi une solution fiable et bien établie.

En proposant plusieurs options de Captcha, AEM Forms vous permet de sélectionner la solution qui correspond le mieux à vos besoins.

Vous souhaitez intégrer l’une de ces solutions Captcha à vos formulaires adaptatifs ? Notre documentation fournit des instructions détaillées pour [Cloudflare Turnstile](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/integrate-adaptive-forms-turnstile-core-components), [hCaptcha](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/integrate-adaptive-forms-hcaptcha-core-components), et [Google reCAPTCHA](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/captcha-adaptive-forms-core-components).


### Service Forms

Le service Forms génère des formulaires PDF interactifs pour la capture de données. Il peut également être utilisé pour importer ou exporter des données vers et à partir d’un formulaire PDF interactif existant et valider les données envoyées. Voici une répartition de ses fonctionnalités :

* **Rendu de Forms** : générez un formulaire PDF interactif à partir d’un modèle créé à l’aide d’AEM Forms Designer et éventuellement de données XML. Cela génère essentiellement un formulaire PDF à remplir, éventuellement prérempli avec des données.
* **Extraction et import des données** : importez des données dans un formulaire PDF existant et extrayez des données d’un formulaire PDF rempli. Les formats de données XDP et XML sont pris en charge, et l’import dans des formulaires PDF non XFA (également appelés AcroForms) prend également en charge les données FDF et XFDF.
* **Validation des données** : validez les données envoyées, au format XDP ou XML, par rapport à un modèle créé à l’aide d’AEM Forms Designer.

>[!IMPORTANT]
>
> Si vous souhaitez rejoindre notre programme d’accès anticipé pour n’importe quelle innovation d’accès anticipé, envoyez simplement un e-mail à partir de votre adresse officielle à [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) pour demander l’accès. Vous pouvez demander l’accès à toutes les innovations ou à certaines d’entre elles.


## Principes de base d’[!DNL Experience Manager] as a [!DNL Cloud Service] {#foundation}

### Prise en charge des informations d’identification OAuth serveur à serveur pour les intégrations d’AEM à d’autres solutions Adobe {#S2S-OAuth-credentials}

Adobe Developer Console permet de générer des informations d’identification pour accéder à diverses API. L’un de ces types d’informations d’identification, les informations d’identification du compte de service (JWT), a été abandonné au profit des informations d’identification OAuth serveur à serveur, qu’AEM Cloud Service prend désormais en charge pour les intégrations à d’autres solutions Adobe telles qu’Adobe Analytics et Adobe Target.

[Découvrez l’obsolescence](/help/security/jwt-credentials-deprecation-in-adobe-developer-console.md) et [comment utiliser l’interface d’utilisation de création d’AEM](/help/security/setting-up-ims-integrations-for-aem-as-a-cloud-service.md) pour configurer des intégrations à d’autres solutions Adobe.

### Alertes de pic de trafic à l’origine {#traffic-spike-origin}

[Recevez des notifications proactives](/help/security/traffic-filter-rules-including-waf.md#traffic-spike-at-origin-alert) à travers le centre d’actions lorsque les schémas de trafic à l’origine indiquent une attaque DDoS, ce qui vous permet d’étudier et de configurer des règles de filtrage du trafic.

### Nouvelles fonctionnalités pour les RDE {#RDE-new-features}

Les [environnements de développement rapide (RDE)](/help/implementing/developing/introduction/rapid-development-environments.md) permettent à l’équipe de développement de déployer, réviser et tester rapidement les modifications en mode cloud. Plusieurs nouvelles fonctionnalités seront déployées au cours du mois de juin. Nous vous invitons également à contacter directement l’équipe d’ingénierie Adobe dans le [canal Discord des RDE](https://discord.com/channels/1131492224371277874/1245304281184079872).


#### Prise en charge de RDE pour le code en front-end à l’aide des thèmes et modèles de site {#rde-frontend}

Les [RDE prennent désormais en charge le code en front-end](/help/implementing/developing/introduction/rapid-development-environments.md#deploying-themes-to-rde) basé sur les [thèmes de site](/help/sites-cloud/administering/site-creation/site-themes.md) et les [modèles de site](/help/sites-cloud/administering/site-creation/site-templates.md), pour les utilisateurs et utilisatrices bénéficiant de l’adoption précoce. Avec les RDE, la prise en charge s’effectue à l’aide d’une directive de ligne de commande plutôt que d’un [pipeline front-end](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md).

#### Amélioration de la journalisation des RDE {#rde-logging}

Lors du débogage du code dans un RDE, les développeurs et développeuses peuvent désormais [configurer et diffuser de manière plus productive les journaux](/help/implementing/developing/introduction/rapid-development-environments.md#rde-logging) à l’aide de la ligne de commande, et cela sans modifier les propriétés OSGi dans le contrôle de versions. Les fonctionnalités incluent les suivantes :

* Déclarer des niveaux de journal par niveau de package ou de classe
* Personnaliser le format de sortie du journal
* Diffuser plusieurs journaux en parallèle

#### Améliorations de l’interface de ligne de commande de RDE {#rde-cli-enhancements}

L’interface de ligne de commande RDE comporte de nouvelles fonctionnalités qui améliorent l’expérience de l’équipe de développement :

* [La commande de configuration est interactive](/help/implementing/developing/introduction/rapid-development-environments.md#installing-the-rde-command-line-tools-interactive), ce qui facilite le choix entre les organisations, les programmes et les environnements. Il est également désormais possible de remplacer ces valeurs sur la ligne de commande.
* [Mode silencieux](/help/implementing/developing/introduction/rapid-development-environments.md#global-flags) pour une sortie moins détaillée.
* [Mode json](/help/implementing/developing/introduction/rapid-development-environments.md#global-flags) pour une sortie utile lorsqu’elle est appelée par programmation.

### Nouvelles notifications du centre d’actions {#actions-center-notifications}

Le [centre d’actions](/help/operations/actions-center.md) envoie des notifications par e-mail lorsque des incidents importants se produisent ou si nous observons quelque chose sur votre code ou configuration où vous devez prendre des mesures proactives. Il existe trois nouveaux types de notification :

* Trop de connexions sortantes via une infrastructure réseau avancée
* Utilisation d’un format de mappage d’utilisateurs et d’utilisatrices de service obsolète
* Attaque DDoS potentielle en cours

### Programmes d’adoption précoce {#foundation-early-adopter}

Envoyez un e-mail à **<aemcs-cdn-config-adopter@adobe.com>**, indiquant le programme d’adoption précoce qui vous intéresse parmi les choix ci-dessous.

#### Purger le contenu sur le réseau CDN avec une clé API en libre-service (programme d’adoption précoce) {#purge-cdn}

Enregistrez une clé API de purge de réseau CDN en libre-service et utilisez-la pour invalider le contenu au niveau du réseau CDN, soit globalement, soit pour une ou plusieurs ressources. [En savoir plus](/help/implementing/dispatcher/cdn-cache-purge.md).

<!-- Email **<aemcs-cdn-config-adopter@adobe.com>** with a request to be an early adopter. -->

#### Création en libre-service d’une clé X-AEM-Edge-Key pour le réseau CDN géré par le client ou la cliente (BYOCDN) (programme d’adoption précoce) {#byocdn-keys}

Auparavant, un ticket d’assistance était nécessaire pour générer la clé X-AEM-Edge-Key requise pour la configuration d’un réseau CDN géré par le client ou la cliente. Vous pouvez désormais y parvenir en libre-service par le biais d’un fichier de configuration déployé à l’aide du pipeline de configuration, supprimant tout délai nécessaire à l’intégration d’un nouvel environnement. [En savoir plus](/help/implementing/dispatcher/cdn-credentials-authentication.md#CDN-HTTP-value).

<!-- Email **<aemcs-cdn-config-adopter@adobe.com>** with a request to be an early adopter. -->

#### Redirections côté serveur (programme destiné aux utilisateurs et utilisatrices précoces) {#server-side-redirects-early-adopter}

Configurez les redirections côté serveur 301/302 dans le contrôle de code source et déployez-les sur le réseau CDN. [En savoir plus](/help/implementing/dispatcher/cdn-configuring-traffic.md#server-side-redirectors).<!-- and join the early adopter program by emailing **<aemcs-cdn-config-adopter@adobe.com>**. --> Notez qu’il existe déjà plusieurs autres fonctionnalités liées à la [configuration du réseau CDN](/help/implementing/dispatcher/cdn-configuring-traffic.md), y compris les transformations de requêtes et de réponses, et le routage du trafic vers les sites hors AEM.

#### Alertes relatives aux règles de filtrage du trafic (programme d’adoption précoce) {#traffic-filter-rules-alerts-early-adopter}

Les [Règles de filtrage du trafic](/help/security/traffic-filter-rules-including-waf.md) récemment publiées qui incluent les règles WAF (Web Application Firewall) sous licence optionnelle vous permettent de configurer le trafic qui doit être autorisé ou refusé.

Rejoignez le programme d’adoption précoce pour pouvoir recevoir une alerte chaque fois que vos règles de filtrage du trafic sont déclenchées. Les notifications par e-mail du centre d’actions vous tiendront au courant lorsque certaines conditions de trafic se produisent afin que vous puissiez prendre les mesures appropriées.

#### Les utilisateurs et utilisatrices professionnels peuvent déclarer des redirections en dehors de Git (programme d’adoption précoce). {#apache-rewritemaps-early-adopter}

Comme pour AEM 6.5, Apache/le Dispatcher ingère des mappages de réécriture placées à un emplacement spécifique dans le référentiel de publication et les charge, sans nécessiter d’exécution de pipeline de niveau web. Un utilisateur professionnel ou une utilisatrice professionnelle peut ainsi déclarer des redirections à l’aide d’une feuille de calcul ou d’une interface d’utilisation, comme celle proposée par le gestionnaire de mappage de redirection ACS Commons ou créée dans le cadre d’une application cliente. <!-- Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information. -->

#### Edge Side Includes (ESI) pour le chargement de contenu dynamique (programme d’adoption précoce) {#esi-early-adopter}

Le réseau CDN géré par Adobe prend désormais en charge [Edge Side Includes (ESI)](/help/implementing/dispatcher/edge-side-includes.md), un langage de balisage pour l’assemblage de contenu web dynamique au niveau Edge. En incluant des extraits de code ESI, vous pouvez mettre en cache la page HTML globale sur le réseau CDN avec des durées de vie (TTL) plus élevées, tout en récupérant plus fréquemment de l’origine les sections plus petites qui nécessitent des mises à jour à un rythme supérieur (durées de vie moins élevées). <!--Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information.-->

## [!DNL Experience Manager] Guides {#guides}

* **Publier une rubrique ou ses éléments sur un fragment d’expérience**
Désormais, Experience Manager Guides vous permet de publier une rubrique ou ses éléments dans un fragment d’expérience. Un fragment d’expérience est une unité de contenu modulaire qui intègre à la fois le contenu et la mise en page.  Les fragments d’expérience sont essentiels, en ce qu’ils peuvent vous aider à créer des expériences cohérentes et attrayantes.
* **Possibilité de transmettre les métadonnées de la ressource de rubrique à la sortie du PDF natif**
Vous pouvez ajouter les métadonnées de la ressource de rubrique lors de la génération de la sortie du PDF natif. Cette fonctionnalité vous permet d’ajouter des métadonnées spécifiques pour différentes rubriques, telles que le titre et l’auteur ou l’autrice de la rubrique, dans les en-têtes et pieds de page de la page de la rubrique.

Pour plus d’informations sur les fonctionnalités nouvelles et améliorées, ainsi que sur les problèmes résolus dans la version, consultez la [Feuille de route de publication d’Experience Manager Guides](https://experienceleague.adobe.com/fr/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici](/help/implementing/cloud-manager/release-notes/current.md).

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [ici](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).

## Notes de mise à jour dʼExperience Cloud {#experience-cloud}

Vous trouverez des informations sur les versions d’autres applications Experience Cloud [ici](https://experienceleague.adobe.com/fr/docs/release-notes/experience-cloud/current).
Pour recevoir chaque mois une notification par e-mail concernant des informations sur les notes de mise à jour d’Experience Cloud, abonnez-vous aux [Mises à jour de produits prioritaires d’Adobe](https://www.adobe.com/subscription/priority-product-update.html).
