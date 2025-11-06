---
title: Notes de mise à jour de la version 2024.1.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la version 2024.1.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 9f5d97c6-6536-4593-acbf-cbe8bf9b5eeb
feature: Release Information
role: Admin
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1018'
ht-degree: 89%

---

# Notes de mise à jour de la version 2024.1.0 d’[!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour de la version 2024.1.0 d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes, telles que 2021 ou 2022.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de la version actuelle de [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2024.1.0) est le 25 janvier 2024. La prochaine disponibilité des fonctionnalités (2024.3.0) est prévue pour le 11 avril 2024.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

## Vidéo de mise à jour {#release-video}

Consultez la vidéo Vue d’ensemble de la version de janvier 2024 pour un résumé des fonctionnalités ajoutées dans la version 2024.1.0 :

>[!VIDEO](https://video.tv.adobe.com/v/3427041?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Extension Manager dans AEM Sites {#sites-extension-manager}

**Découvrez le nouveau gestionnaire [Extension Manager dans AEM Sites](https://developer.adobe.com/uix/docs/extension-manager/)**, permettant de personnaliser votre configuration AEM en configurant les extensions de l’interface utilisateur.

![Extension Manager dans AEM Sites.](/help/assets/sites/extension-manager/homepage.png)

L’Extension Manager dans AEM Sites permet aux personnes spécialisée dans le développement et à l’ensemble des professionnelles et professionnels d’accéder aux [extensions de l’interface utilisateur](https://developer.adobe.com/uix/docs/) intégrées avec [Adobe App Builder](https://developer.adobe.com/app-builder/), de les gérer et de les personnaliser afin d’améliorer les fonctionnalités d’AEM Sites.
Avec Extension Manager, vous pouvez :

* activer ou désactiver des extensions pour chaque instance ;
* configurer les paramètres d’extension ;
* prévisualiser les extensions et générer un lien d’aperçu partageable ;
* découvrir les fonctionnalités d’extensibilité de l’interface utilisateur au moyen de démonstrations interactives ;
* accéder aux fonctionnalités expérimentales d’Adobe par le biais d’extensions propriétaires.

Nous recherchons activement des commentaires et de nouveaux cas d’utilisation pour les extensions de l’interface utilisateur. Si vous souhaitez vous connecter, veuillez envoyer un e-mail à `uix@adobe.com`.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Fonctionnalités de la version préliminaire de la vue d’administration {#admin-view-prerelease}

**Rendus d’aperçu pour tous les types de vidéo pris en charge.**

Experience Manager Assets génère désormais par défaut des rendus d’aperçu de tous les types de vidéo pris en charge sans nécessiter de configuration de profil de traitement.

### Vue Assets {#assets-view-features}

**Liste bloquée des balises intelligentes**

Assets Essentials vous permet désormais de définir une liste bloquée contenant des mots qui ne doivent pas être ajoutés en tant que balises intelligentes aux ressources chargées dans le référentiel. Cette fonctionnalité vous aide à maintenir la conformité de la marque et réduit les efforts de modération des balises intelligentes.

![Liste bloquée des balises intelligentes.](/help/assets/assets/block-tags.png)


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Programme d’adoption précoce {#forms-early-adopter}

* **[Envoi d’un formulaire adaptatif au scénario Adobe Workfront Fusion](/help/forms/submit-adaptive-form-to-workfront-fusion.md)** : Forms as a Cloud Service propose des options prêtes à l’emploi pour connecter facilement un formulaire adaptatif à Adobe Workfront. Cela simplifie le processus d’envoi d’un formulaire adaptatif à un scénario Adobe Workfront, ce qui permet de déclencher un scénario Workfront Fusion lors de l’envoi d’un formulaire adaptatif.

* **[Prise en charge des langues de droite à gauche](/help/forms/supporting-new-language-localization-core-components.md)** : les formulaires adaptatifs reposant sur les composants principaux peuvent désormais être présentés dans une langue de droite à gauche telle que l’arabe, le persan et l’ourdou. Les langues s’écrivant de droite à gauche sont parlées par plus de 2 milliards de personnes dans le monde. L’utilisation d’un formulaire pour les langues s’écrivant de droite à gauche permet d’étendre la portée de vos formulaires adaptatifs pour répondre à ces diverses audiences et aux marchés correspondants. Dans certaines régions, il en va d’une obligation légale de fournir des formulaires dans la langue locale. En vous adaptant aux langues locales, vous vous ouvrez non seulement à une audience plus large, mais vous garantissez aussi le respect des lois et réglementations pertinentes.

  ![Prise en charge des langues de droite à gauche.](/help/forms/assets/right-to-left-language-support.png)

* **[Protégez vos documents avec les API DocAssurance (qui font partie des API de communication)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)** : les API DocAssurance vous permettent de protéger les informations sensibles en signant et en chiffrant les documents. Grâce au chiffrement, le contenu d’un document est transformé en un format illisible, ce qui garantit que seules les personnes autorisées peuvent y accéder. Cette couche renforcée de protection protège non seulement les données précieuses des yeux non autorisés, mais offre également une certaine tranquillité d’esprit. Les API Signature permettent à votre entreprise de garantir la sécurité et la confidentialité des documents Adobe PDF qu’elle diffuse et reçoit. Ce service utilise les signatures numériques et la certification pour s’assurer que seules les personnes destinataires prévues peuvent modifier les documents.

  Vous pouvez écrire à `aem-forms-early-adopter-program@adobe.com` depuis votre adresse e-mail officielle pour rejoindre le programme d’adoption précoce et demander l’accès à la fonctionnalité.

* **[Vous pouvez tirer parti du service de télémétrie opérationnelle](/help/implementing/cloud-manager/content-requests.md#real-user-monitoring-for-aem-as-a-cloud-service)** pour activer la collecte côté client pour AEM as a Cloud Service.
Le service de télémétrie opérationnelle offre un reflet plus précis des interactions des utilisateurs, assurant ainsi une mesure fiable de l’engagement du site web. Il constitue une excellente opportunité d’obtenir des informations avancées sur les performances de votre page. Il est ainsi utile pour la clientèle qui utilise un réseau CDN géré ou non par Adobe. Par ailleurs, pour les personnes utilisant un réseau CDN non géré par Adobe, il est désormais possible de créer automatiquement des rapports sur le trafic, ce qui leur évite d’avoir à partager n’importe quel rapport sur le trafic avec Adobe.

  Si vous souhaitez tester cette nouvelle fonctionnalité et partager vos commentaires, envoyez un e-mail à `aemcs-rum-adopter@adobe.com`, ainsi que votre nom de domaine pour chacun des environnements pour lesquels vous souhaitez activer la télémétrie opérationnelle à partir de votre adresse e-mail associée à votre Adobe ID. L’équipe produit Adobe activera alors le service de télémétrie opérationnelle pour vous.

## Principes de base d’[!DNL Experience Manager] as a [!DNL Cloud Service] {#foundation}

### Prise en charge de Dynatrace {#dynatrace}

La clientèle Dynatrace peut surveiller son utilisation d’AEM. [Découvrez comment](/help/implementing/cloud-manager/dynatrace.md) demander la connectivité à votre environnement Dynatrace afin de surveiller les performances de l’application. Notez que l’APM New Relic, disponible pour l’ensemble de la clientèle, cessera de collecter des données si Dynatrace est activé.

### Prise en charge de RDE pour le code en front-end à l’aide des thèmes du site et des modèles de site : programme d’adoption précoce {#rde-frontend-early-adopter}

Les [environnements de développement rapide (RDE)](/help/implementing/developing/introduction/rapid-development-environments.md) prennent désormais en charge le code en front-end basé sur les [thèmes de site](/help/sites-cloud/administering/site-creation/site-themes.md) et les [modèles de site](/help/sites-cloud/administering/site-creation/site-templates.md), pour les personnes qui adoptent la solution en avant-première. Avec les RDE, la prise en charge s’effectue à l’aide d’une directive de ligne de commande plutôt que d’un [pipeline front-end](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md). Veuillez contacter **aemcs-rde-support@adobe.com** pour essayer et fournir des commentaires.

### Programme de mappage de domaines pour les utilisateurs et utilisatrices précoces {#cdn-config-early-adopter}

Outre les [Règles de filtrage du trafic](/help/security/traffic-filter-rules-including-waf.md) récemment publiées qui incluent les règles WAF (Web Application Firewall) sous licence optionnelle, il existe une opportunité d’utiliser le pipeline de configuration pour déclarer et déployer d’[autres types de configuration du réseau CDN](/help/implementing/dispatcher/cdn-configuring-traffic.md). Rejoignez le programme des utilisateurs et utilisatrices précoces en envoyant un e-mail à **`aemcs-cdn-config-adopter@adobe.com`** pour accéder à :

* Redirections côté client 301/302
* Établier un proxy des requêtes en périphérie vers des origines arbitraires
* Transformations d’URL
* Définir ou modifier des en-têtes de requête ou de réponse
* Pages d’erreur personnalisées lorsque le réseau CDN ne peut pas atteindre AEM.

## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici](/help/implementing/cloud-manager/release-notes/current.md).

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [ici](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
