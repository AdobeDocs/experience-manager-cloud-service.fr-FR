---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: b7e8fd902bb2fe98e183b7d987b87fee69e48337
workflow-type: tm+mt
source-wordcount: '1865'
ht-degree: 24%

---

# Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour techniques de la version actuelle (la plus récente) d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes, telles que 2021 ou 2022.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de la version actuelle (2024.5.0) d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le vendredi 30 mai 2024. La prochaine mise à jour des fonctionnalités (2024.6.0) est prévue pour le vendredi 27 juin 2024.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

## Vidéo de mise à jour {#release-video}

Consultez la vidéo Aperçu de la version de mai 2024 pour obtenir un résumé des fonctionnalités ajoutées dans la version 2024.5.0 :

>[!VIDEO](https://video.tv.adobe.com/v/3429503?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités de Sites {#sites-new-features}

**Création AEM pour Edge Delivery Services**

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

**Publication de ressources dans AEM et Dynamic Media**

Experience Manager Assets vous permet désormais de rapidement [publication de ressources dans Experience Manager et Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md) à l’aide de la vue Assets sans passer à la vue Admin. Vous pouvez publier des ressources lors du chargement, de la navigation et de la recherche de ressources.

![vérification de la publication status1](/help/assets/assets/check-publish-status1.png)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Nouvelles fonctionnalités de préversion d’AEM Forms {#forms-new-prerelease-features}

#### Éditeur de règles visuel amélioré pour Forms adaptatif basé sur les composants principaux

Cette version introduit une mise à niveau significative de l’éditeur de règles visuel pour les formulaires adaptatifs basés sur les composants principaux. Vous pouvez maintenant effectuer les tâches suivantes :

* Créez des règles dans l’éditeur de règles visuel pour [remplacer les messages de succès/d’échec d’envoi de formulaire par défaut](/help/forms/create-and-use-custom-functions.md#use-case-override-form-submission-success-and-error-handlers).

* Dans l’éditeur de règles de Forms adaptatif, ajout de la possibilité de [sélectionner différents types de champs pour l’opération WHEN ;](/help/forms/rule-editor-core-components.md#allowed-multiple-fields-in-when).

* Un auteur de formulaires peut désormais appliquer des fonctions personnalisées à [prétraitement des données avant envoi](/help/forms/create-and-use-custom-functions.md#use-case-submit-altered-data-to-the-server).

* Utilisez la variable [**Enregistrer en tant que brouillon**](/help/forms/save-core-component-based-form-as-draft.md) pour enregistrer des formulaires partiellement remplis en vue d’un envoi ultérieur. Cela s’avère utile lorsque les utilisateurs doivent interrompre le remplissage d’un formulaire et y revenir ultérieurement.



### Fonctionnalités d’adoption précoce dans AEM Forms {#forms-new-early-adopter-features}

Le programme d’adoption précoce d’AEM Forms vous offre une opportunité unique d’accéder de manière exclusive à des innovations de pointe avant tout autre utilisateur et de contribuer à façonner leur développement.
Le programme offre l&#39;accès à de multiples innovations.

Les notes de mise à jour répertorient les innovations mises en oeuvre dans la version actuelle. Pour obtenir la liste complète des innovations disponibles dans le cadre du Programme des primo-adopteurs, voir [Documentation du programme d’adoption précoce d’AEM Forms](/help/forms/early-adopter-ea-features.md).

#### Amélioration des méthodes de protection des robots

AEM Forms a amélioré ses fonctionnalités de sécurité en ajoutant la prise en charge de deux solutions CAPTCHA populaires : Cloudflare Turnstile et Captcha. Cela vient s’ajouter au reCAPTCHA de Google déjà disponible, offrant ainsi aux utilisateurs plus de choix et de flexibilité pour protéger leurs formulaires contre les robots et les spams envoyés.

* **Cloudflare Turnstile**: ce CAPTCHA sans friction vérifie les utilisateurs par le biais d’un simple défi qui ne nécessite pas d’interaction explicite. Il s’intègre de manière transparente à vos formulaires, améliorant ainsi l’expérience utilisateur.
* **Captcha**: ce CAPTCHA axé sur la confidentialité offre une alternative conviviale qui met l’accent sur la confidentialité des données. Il vise à trouver un équilibre entre la sécurité et l’expérience utilisateur.
* **Google reCAPTCHA**: AEM Forms continue à prendre en charge reCAPTCHA v2 et reCAPTCHA Enterprise, offrant ainsi une solution fiable et bien établie.

En proposant plusieurs options CAPTCHA, AEM Forms vous permet de sélectionner la solution qui correspond le mieux à vos besoins.

Prêt à intégrer l’une de ces solutions CAPTCHA à votre Forms adaptatif ? Notre documentation fournit des instructions détaillées pour chaque : [Cloudflare Turnstile](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/integrate-adaptive-forms-turnstile-core-components), [Captcha](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/integrate-adaptive-forms-hcaptcha-core-components), et [Google reCAPTCHA](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/captcha-adaptive-forms-core-components).


### Service Forms

Le service Forms génère des PDF forms interactifs pour la capture de données. Il peut également être utilisé pour importer ou exporter des données vers et depuis un formulaire de PDF interactif existant et valider les données envoyées. Voici une répartition de ses fonctionnalités :

* **Rendu de Forms**: générez un formulaire de PDF interactif à partir d’un modèle créé à l’aide d’AEM Forms Designer et éventuellement de données XML. Cela génère essentiellement un formulaire de PDF à remplir, éventuellement prérempli avec des données.
* **Extraction et importation de données**: importez des données dans un formulaire de PDF existant et extrayez des données d’un formulaire de PDF rempli. Les formats de données XDP et XML sont pris en charge et l’importation dans des PDF forms non XFA (également appelés AcroForms) prend également en charge les données FDF et XFDF.
* **Validation des données**: validez les données envoyées, au format XDP ou XML, par rapport à un modèle créé à l’aide d’AEM Forms Designer.

>[!IMPORTANT]
>
> Si vous souhaitez rejoindre notre programme d&#39;adoption précoce pour n&#39;importe quelle innovation d&#39;adoption précoce, envoyez simplement un email depuis votre adresse officielle à [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) pour demander l’accès. Vous pouvez demander l’accès à l’ensemble ou à toute innovation spécifique.


## Principes de base d’[!DNL Experience Manager] as a [!DNL Cloud Service] {#foundation}

### Prise en charge des informations d’identification OAuth serveur à serveur pour les intégrations d’AEM à d’autres solutions d’Adobe {#S2S-OAuth-credentials}

La console Adobe Developer permet de générer des informations d’identification pour accéder à diverses API. L’un de ces types d’informations d’identification, les informations d’identification du compte de service (JWT), a été abandonné au profit des informations d’identification OAuth serveur à serveur, qu’AEM Cloud Service prend désormais en charge pour les intégrations à d’autres solutions d’Adobe telles qu’Adobe Analytics et Adobe Target.

[En savoir plus sur l’obsolescence](/help/security/jwt-credentials-deprecation-in-adobe-developer-console.md) et [découvrez comment utiliser l’interface utilisateur de création d’AEM](/help/security/setting-up-ims-integrations-for-aem-as-a-cloud-service.md) pour configurer des intégrations avec d’autres solutions Adobe.

### Pic de trafic des alertes d’origine {#traffic-spike-origin}

[Recevoir des notifications proactives](/help/security/traffic-filter-rules-including-waf.md#traffic-spike-at-origin-alert) à travers le centre d’actions lorsque les schémas de trafic à l’origine indiquent une attaque DDoS, ce qui vous permet d’étudier et de configurer des règles de filtrage du trafic.

### Nouvelles fonctionnalités des RDE {#RDE-new-features}

[Environnements de développement rapide (RDE)](/help/implementing/developing/introduction/rapid-development-environments.md) permettent aux développeurs de déployer, réviser et tester rapidement les modifications dans le cloud. Plusieurs nouvelles fonctionnalités seront déployées au cours du mois de juin. Nous vous invitons également à vous engager directement auprès des ingénieurs Adobes au [Canal de discorde RDE](https://discord.com/channels/1131492224371277874/1245304281184079872).


#### Prise en charge de RDE pour le code frontal à l’aide des thèmes du site et des modèles de site {#rde-frontend}

[Les RDE prennent désormais en charge le code frontal.](/help/implementing/developing/introduction/rapid-development-environments.md#deploying-themes-to-rde) basé sur [thèmes du site](/help/sites-cloud/administering/site-creation/site-themes.md) et [modèles de site](/help/sites-cloud/administering/site-creation/site-templates.md), pour les utilisateurs qui ont adopté l’heure. Avec les RDE, cela se fait à l’aide d’une directive de ligne de commande, plutôt que d’une [pipeline front-end](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md).

#### Amélioration de la journalisation des RDE {#rde-logging}

Lors du débogage du code dans un RDE, les développeurs peuvent désormais [configurer et diffuser des journaux plus efficacement](/help/implementing/developing/introduction/rapid-development-environments.md#rde-logging), à l’aide de la ligne de commande, et sans modifier les propriétés OSGI dans le contrôle de version. Les fonctionnalités incluent les suivantes :

* déclaration des niveaux de journal à un niveau par package ou classe
* personnalisation du format de sortie du journal
* diffusion en continu de plusieurs journaux en parallèle

#### Améliorations de l’interface de ligne de commande de RDE {#rde-cli-enhancements}

L’interface de ligne de commande RDE comporte de nouvelles fonctionnalités qui améliorent l’expérience du développeur :

* [la commande de configuration est interactive](/help/implementing/developing/introduction/rapid-development-environments.md#installing-the-rde-command-line-tools-interactive), ce qui facilite le choix entre les organisations, les programmes et les environnements. Il est également désormais possible de remplacer ces valeurs sur la ligne de commande.
* [mode silencieux](/help/implementing/developing/introduction/rapid-development-environments.md#global-flags) pour une sortie moins détaillée.
* [mode json](/help/implementing/developing/introduction/rapid-development-environments.md#global-flags) pour une sortie utile lorsqu’elle est appelée par programmation.

### Nouvelles notifications du centre d’actions {#actions-center-notifications}

[Centre d’actions](/help/operations/actions-center.md) envoie des notifications par e-mail lorsque des incidents importants se produisent ou si nous observons quelque chose sur votre code ou configuration où vous devez prendre des mesures proactives. Il existe trois nouveaux types de notification :

* trop de connexions sortantes via une infrastructure réseau avancée
* utilisation d’un format de mappage d’utilisateur de service obsolète
* une attaque DDoS potentielle est en cours

### Programmes d’adoption précoce {#foundation-early-adopter}

Email **<aemcs-cdn-config-adopter@adobe.com>**, indiquant à quel programme d’adoption précoce en dessous duquel vous êtes intéressé.

#### Purger le contenu sur le réseau de diffusion de contenu avec une clé d’API en libre-service (programme d’adoption précoce) {#purge-cdn}

Enregistrez une clé API de purge CDN en libre-service et utilisez-la pour invalider le contenu sur le CDN, de manière globale ou pour une ou plusieurs ressources. [En savoir plus](/help/implementing/dispatcher/cdn-cache-purge.md).

<!-- Email **<aemcs-cdn-config-adopter@adobe.com>** with a request to be an early adopter. -->

#### Création en libre-service de X-AEM-Edge-Key pour le réseau de diffusion de contenu géré par le client (BYOCDN) (programme des Adopteurs précoces) {#byocdn-keys}

Auparavant, un ticket d’assistance était nécessaire pour générer la clé X-AEM-Edge-Key requise pour la configuration d’un réseau de diffusion de contenu géré par le client. Vous pouvez désormais y parvenir en libre-service par le biais d’un fichier de configuration déployé à l’aide du pipeline de configuration, supprimant tout délai nécessaire à l’intégration d’un nouvel environnement. [En savoir plus](/help/implementing/dispatcher/cdn-credentials-authentication.md#CDN-HTTP-value).

<!-- Email **<aemcs-cdn-config-adopter@adobe.com>** with a request to be an early adopter. -->

#### Redirections côté client (programme d’adoption précoce) {#client-side-redirects-early-adopter}

Configurez des redirections côté client 301/302 dans le contrôle de code source et déployez-les sur le réseau CDN. [En savoir plus](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors).<!-- and join the early adopter program by emailing **<aemcs-cdn-config-adopter@adobe.com>**. --> Notez qu’il existe déjà plusieurs autres fonctionnalités liées à [Configuration du réseau CDN](/help/implementing/dispatcher/cdn-configuring-traffic.md), y compris les transformations de requêtes et de réponses, et le routage du trafic vers les sites hors AEM.

#### Alertes relatives aux règles de filtrage du trafic (programme d’adoption précoce) {#traffic-filter-rules-alerts-early-adopter}

Les [Règles de filtrage du trafic](/help/security/traffic-filter-rules-including-waf.md) récemment publiées qui incluent les règles WAF (Web Application Firewall) sous licence optionnelle vous permettent de configurer le trafic qui doit être autorisé ou refusé.

Rejoignez le programme des premiers adopteurs afin que vous puissiez être alerté chaque fois que vos règles de filtre de trafic sont déclenchées. Les notifications par e-mail du Centre d’actions vous tiendront au courant lorsque certaines conditions de trafic se produisent afin que vous puissiez prendre les mesures appropriées.

#### Les utilisateurs professionnels peuvent déclarer des redirections en dehors de Git (Programme des adopteurs précoces). {#apache-rewritemaps-early-adopter}

Comme pour AEM 6.5, Apache/le Dispatcher ingère des mappages de réécriture placées à un emplacement spécifique dans le référentiel de publication et les charge, sans nécessiter d’exécution de pipeline de niveau web. Cela permet à un utilisateur chargé de la conception de rapports de déclarer des redirections à l’aide d’une feuille de calcul ou d’une interface utilisateur, telles que celles proposées par le gestionnaire de cartes de redirection ACS Commons ou créées dans le cadre d’une application client. <!-- Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information. -->

#### Edge Side Includes (ESI) pour le chargement de contenu dynamique (programme d’adoption précoce) {#esi-early-adopter}

Le réseau de diffusion de contenu géré par Adobe prend désormais en charge [Inclusions Edge Side (ESI)](/help/implementing/dispatcher/edge-side-includes.md): langage de balisage pour l’assemblage de contenu web dynamique de niveau périphérie. En incluant des fragments de code ESI, vous pouvez mettre en cache la page de HTML globale sur le réseau de diffusion de contenu avec des TTL plus élevés, tout en récupérant plus souvent à partir de l’origine les sections plus petites qui nécessitent des mises à jour de cadence plus élevées (TTL moins élevées). <!--Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information.-->

#### Service de données de surveillance des utilisateurs réels (RUM) (Programme des premiers adopteurs)

* **[Le service de données de surveillance à usage réel (RUM) est désormais GA](/help/implementing/cloud-manager/content-requests.md#real-user-monitoring-for-aem-as-a-cloud-service)** activation de la collecte de données côté client pour AEM as a Cloud Service.
Le service de surveillance de l’utilisation réelle , la collection côté client, offre un reflet plus précis des interactions, assurant une mesure fiable de l’engagement du site web. Il permet aux clients disposant d’informations avancées sur le trafic et les performances de leur page. C’est une excellente occasion d’en savoir plus sur les performances de votre page et d’obtenir des informations pour l’améliorer.

## [!DNL Experience Manager] Guides {#guides}

* **Publication d’une rubrique ou de ses éléments sur un fragment d’expérience**
Désormais, les guides du Experience Manager vous permettent de publier une rubrique ou ses éléments dans un fragment d’expérience. Un fragment d’expérience est une unité de contenu modulaire qui intègre à la fois le contenu et la mise en page.  Les fragments d’expérience sont essentiels et peuvent vous aider à créer des expériences cohérentes et attrayantes.
* **Possibilité de transmettre les métadonnées de la ressource de rubrique à la sortie du PDF natif.**
Vous pouvez ajouter les métadonnées de la ressource de rubrique lors de la génération de la sortie de l’PDF natif. Cette fonctionnalité vous permet d’ajouter des métadonnées spécifiques pour différentes rubriques, telles que le titre et l’auteur de la rubrique, dans les en-têtes et pieds de page de la page de la rubrique.

Pour plus d’informations sur les nouvelles fonctionnalités et les problèmes améliorés résolus dans la version, consultez la [Feuille de route de la publication des guides du Experience Manager](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici](/help/implementing/cloud-manager/release-notes/current.md).

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [ici](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
