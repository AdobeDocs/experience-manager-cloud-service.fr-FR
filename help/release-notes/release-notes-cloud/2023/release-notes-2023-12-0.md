---
title: Notes de mise à jour de la version 2023.12.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la version 2023.12.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: b36add58-a2ba-4299-94be-e0026e9c553c
feature: Release Information
role: Admin
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '828'
ht-degree: 75%

---

# Notes de mise à jour de la version 2023.12.0 d’[!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour de la version 2023.12.0 d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes, telles que 2021 ou 2022.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de la version actuelle (2023.12.0) d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le vendredi 14 décembre 2023. La prochaine version des fonctionnalités (2024.1.0) est prévue pour le jeudi 25 janvier 2023.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

<!-- 

## Release Video {#release-video}

Have a look at the December 2023 Release Overview video for a summary of the features added in the 2023.12.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3425864?quality=12)

-->

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Programme d’adoption précoce {#sites-early-adopter}

**Vous pouvez tirer parti du [service de télémétrie opérationnelle](/help/implementing/cloud-manager/content-requests.md#real-user-monitoring-for-aem-as-a-cloud-service)** pour activer la collecte côté client pour AEM as a Cloud Service.

Le service opérationnel de données télémétriques offre une réflexion plus précise des interactions des utilisateurs, assurant ainsi une mesure fiable de l’engagement du site web. Il constitue une excellente opportunité d’obtenir des informations avancées sur les performances de votre page. Il est ainsi utile pour la clientèle qui utilise un réseau CDN géré ou non par Adobe. Par ailleurs, pour les personnes utilisant un réseau CDN non géré par Adobe, il est désormais possible de créer automatiquement des rapports sur le trafic, ce qui leur évite d’avoir à partager n’importe quel rapport sur le trafic avec Adobe.

Si vous souhaitez tester cette nouvelle fonctionnalité et partager vos commentaires, envoyez un e-mail à `aemcs-rum-adopter@adobe.com`, ainsi que votre nom de domaine pour l’environnement de production, d’évaluation et de développement, à partir de l’adresse e-mail associée à votre Adobe ID. L’équipe produit d’Adobe activera alors le service de données télémétriques opérationnelles pour vous.


## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de la vue Assets {#assets-view-features}

**Créer des images GenAI avec Adobe Firefly**

Créez des images à partir de requêtes de recherche avec une intégration de la fonctionnalité « du texte à l’image » d’Adobe Firefly (nécessite une licence Adobe Firefly).

![Intégration des ressources Firefly](/help/assets/assets/assets-firefly-integration.png)

**Rechercher des images similaires**

Vous pouvez désormais facilement rechercher du contenu en sélectionnant une image et en affichant des images similaires dans le référentiel Experience Manager Assets.

<!--

* **Smart tags blocklist**: Experience Manager Assets now enables you to define a list of blocked tags. These tags are automatically removed from the auto-generated smart tags when you upload assets to the repository. This capability performs tags governance and saves a lot of time as you can add a tag to the block list and AEM Assets automatically excludes it from the list of tags for any of the assets that are added to the repository.

  ![storage usage insights](/help/assets/assets/block-tags.png)


**Video Preview**: AEM Assets now generates preview renditions of all supported video formats by default, without the need to configure a processing profile.

-->

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités de [!DNL Experience Manager Forms] {#forms-features}

* **[Connexion d’un formulaire adaptatif à une liste Microsoft® SharePoint](/help/forms/configure-submit-actions-core-components.md#submit-to-sharepoint)** : AEM Forms assure une intégration prête à l’emploi pour envoyer les données de formulaire directement à la liste SharePoint, ce qui vous permet d’utiliser les fonctionnalités des listes SharePoint. Vous pouvez configurer la liste Microsoft SharePoint en tant que source de données pour un modèle de données de formulaire et utiliser l’action d’envoi **Envoyer à l’aide du modèle de données de formulaire** pour connecter un formulaire adaptatif à la liste SharePoint.

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Programme d’adoption précoce {#forms-early-adopter}

* **[Envoi d’un formulaire adaptatif au scénario Adobe Workfront Fusion](/help/forms/submit-adaptive-form-to-workfront-fusion.md)** : Forms as a Cloud Service propose des options prêtes à l’emploi pour connecter facilement un formulaire adaptatif à Adobe Workfront. Cela simplifie le processus d’envoi d’un formulaire adaptatif à un scénario Adobe Workfront, ce qui permet de déclencher un scénario Workfront Fusion lors de l’envoi d’un formulaire adaptatif.

* **[Prise en charge des langues de droite à gauche](/help/forms/supporting-new-language-localization-core-components.md)** : les formulaires adaptatifs reposant sur les composants principaux peuvent désormais être présentés dans une langue de droite à gauche telle que l’arabe, le persan et l’ourdou. Les langues s’écrivant de droite à gauche sont parlées par plus de 2 milliards de personnes dans le monde. L’utilisation d’un formulaire pour les langues s’écrivant de droite à gauche permet d’étendre la portée de vos formulaires adaptatifs pour répondre à ces diverses audiences et aux marchés correspondants. Dans certaines régions, il en va d’une obligation légale de fournir des formulaires dans la langue locale. En vous adaptant aux langues locales, vous vous ouvrez non seulement à une audience plus large, mais vous garantissez aussi le respect des lois et réglementations pertinentes.

  ![Prise en charge des langues de droite à gauche.](/help/forms/assets/right-to-left-language-support.png)

* **[Protégez vos documents avec les API DocAssurance (qui font partie des API de communication)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)** : les API DocAssurance vous permettent de protéger les informations sensibles en signant et en chiffrant les documents. Grâce au chiffrement, le contenu d’un document est transformé en un format illisible, ce qui garantit que seules les personnes autorisées peuvent y accéder. Cette couche renforcée de protection protège non seulement les données précieuses des yeux non autorisés, mais offre également une certaine tranquillité d’esprit. Les API Signature permettent à votre entreprise de garantir la sécurité et la confidentialité des documents Adobe PDF qu’elle diffuse et reçoit. Ce service utilise les signatures numériques et la certification pour s’assurer que seules les personnes destinataires prévues peuvent modifier les documents.

  Vous pouvez écrire à `aem-forms-ea@adobe.com` depuis votre adresse e-mail officielle pour rejoindre le programme d’adoption précoce et demander l’accès à la fonctionnalité.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Programme de mappage de domaines pour les utilisateurs et utilisatrices précoces {#cdn-config-early-adopter}

Outre les [&#x200B; Règles de filtrage du trafic &#x200B;](/help/security/traffic-filter-rules-including-waf.md) récemment publiées, qui incluent les règles de pare-feu d’application web (WAF) sous licence facultative, vous pouvez utiliser le pipeline de configuration pour déclarer et déployer d’autres types de configuration de réseau CDN. Nous aimerions en savoir plus sur vos cas d’utilisation, notamment :

* Redirections côté client 301/302
* Établier un proxy des requêtes en périphérie vers des origines arbitraires
* Transformations d’URL
* Définir ou modifier des en-têtes de requête ou de réponse
* Pages d’erreur personnalisées lorsque le réseau CDN ne peut pas atteindre AEM.
* authentification par nom d’utilisateur/mot de passe
* toute autre configuration CDN utile

Envoyez un e-mail à **aemcs-cdn-config-adopter@adobe.com** à partir de votre ID d’e-mail officiel avec vos commentaires.

## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici](/help/implementing/cloud-manager/release-notes/current.md).

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [ici](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
