---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: ac7af61751c3cf751a7370b454855c5361fabe02
workflow-type: tm+mt
source-wordcount: '1428'
ht-degree: 29%

---

# Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour techniques de la version actuelle (la plus récente) d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes, telles que 2021 ou 2022.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de la version actuelle (2023.11.0) d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le vendredi 30 novembre 2023. La prochaine mise à jour des fonctionnalités (2023.12.0) est prévue pour le vendredi 14 décembre 2023.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

## Vidéo de mise à jour {#release-video}

Regardez la vidéo Présentation de la version de novembre 2023 pour un résumé des fonctionnalités ajoutées à la version 2023.11.0 :

>[!VIDEO](https://video.tv.adobe.com/v/3425864?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Programme d&#39;adoption précoce {#sites-early-adopter}

**Vous pouvez utiliser la variable [Service de données de surveillance des utilisateurs réels (RUM)](/help/implementing/cloud-manager/content-requests.md#real-user-monitoring-for-aem-as-a-cloud-service)** pour activer la collecte côté client pour AEM as a Cloud Service.

Le service de données de surveillance des utilisateurs réels (RUM) offre un reflet plus précis des interactions des utilisateurs, assurant une mesure fiable de l’engagement du site web. C’est une excellente opportunité d’obtenir des informations avancées sur les performances de votre page. Bien que cela soit bénéfique pour les clients qui utilisent un réseau de diffusion de contenu géré par l’Adobe ou un réseau de diffusion de contenu non géré par l’Adobe. En outre, pour les clients qui utilisent un réseau de diffusion de contenu non géré par un Adobe, les rapports de trafic automatisés peuvent désormais être activés pour eux, ce qui évite d’avoir à partager n’importe quel rapport de trafic avec un Adobe.

Si vous souhaitez tester cette nouvelle fonctionnalité et partager vos commentaires, envoyez un e-mail à `aemcs-rum-adopter@adobe.com`, ainsi que le nom de domaine de l’environnement de production, d’évaluation et de développement à partir de l’adresse électronique associée à votre Adobe ID. L’équipe produit d’Adobe activera alors le service de données de surveillance des utilisateurs réels (RUM) pour vous.

**[Recherche et remplacement de chaînes dans des fragments de contenu](/help/sites-cloud/administering/content-fragments/managing.md#find-and-replace-find-and-replace)**: la console de fragments de contenu offre aux utilisateurs un moyen simple et intuitif de remplacer une chaîne apparaissant simultanément dans plusieurs fragments de contenu afin d’accélérer la vitesse du contenu.

![Rechercher et remplacer](/help/sites-cloud/administering/content-fragments/assets/cf-managing-find-replace.png)

Vous souhaitez tester la fonctionnalité et partager vos commentaires ? Envoi d’un courrier électronique à **aemcs-headless-adopter@adobe.com** à partir de votre ID de courrier électronique officiel pour en savoir plus sur le programme des premiers adopteurs.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de la vue Assets {#assets-view-features}

* **Éditeur d’Adobe Express intégré dans AEM Assets**: les utilisateurs ayant accès à Express disposent désormais d’outils intégrés d’édition et de création d’images d’Adobe Express et d’Adobe Firefly disponibles directement dans AEM Assets pour améliorer la réutilisation du contenu et accélérer la vitesse de diffusion du contenu.

  ![affecter un formulaire de métadonnées à un dossier](/help/assets/assets/adobe-express-aem-assets.png)

<!--

* **Smart tags blocklist**: Experience Manager Assets now enables you to define a list of blocked tags. These tags are automatically removed from the auto-generated smart tags when you upload assets to the repository. This capability performs tags governance and saves a lot of time as you can add a tag to the block list and AEM Assets automatically excludes it from the list of tags for any of the assets that are added to the repository.

  ![storage usage insights](/help/assets/assets/block-tags.png)

-->


* **Rapports sur l’utilisation du stockage dans Insights**: les administrateurs ont désormais la possibilité d’afficher les rapports sur l’utilisation du stockage disponibles dans le cadre d’ Insights .

  ![informations sur l’utilisation du stockage](/help/assets/assets/storage-usage-insights.png)

* **Recherche de la première configuration de page d’accueil**: Experience Manager Assets vous permet désormais de configurer l’expérience de la page d’accueil pour votre entreprise. Si vous sélectionnez d’abord la recherche comme page d’accueil, vous pouvez configurer l’alignement de la barre de recherche, l’image d’arrière-plan et le logo de votre entreprise.

  ![première configuration de recherche](/help/assets/assets/search-first-configuration.png)

### Nouvelles fonctionnalités de la version préliminaire pour la vue d’administrateur {#admin-view-features-prerelease}

**Aperçu vidéo**: AEM Assets génère désormais par défaut des rendus d’aperçu de tous les formats vidéo pris en charge, sans avoir à configurer de profil de traitement.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités de [!DNL Experience Manager Forms] {#forms-features}

* **[Composant de case à cocher](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/checkbox.html?lang=fr)** : les formulaires adaptatifs basés sur les composants principaux peuvent désormais inclure un composant de case à cocher. Il permet aux utilisateurs et utilisatrices de faire des choix binaires, en sélectionnant ou en désélectionnant une option particulière. Il s’affiche généralement sous la forme d’une petite case sur laquelle vous pouvez cliquer ou appuyer pour basculer entre deux états : cochée et décochée. La case à cocher est un élément de formulaire courant, utilisé pour présenter un choix oui/non ou vrai/faux.

* **[Composant Conditions générales](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/terms-and-conditions.html?lang=fr)** : les formulaires adaptatifs basés sur les composants principaux peuvent désormais inclure un composant Conditions générales. Il permet aux personnes créant les formulaires d’introduire une section spécifique dans le formulaire, dans laquelle les utilisateurs et utilisatrices peuvent consulter les conditions générales ou les accords juridiques associés à l’utilisation d’un service, d’un produit ou d’une plateforme. Ce composant est conçu pour informer les utilisateurs et utilisatrices des règles, des réglementations et des obligations qu’ils acceptent en envoyant le formulaire.

  ![Composants des onglets Case à cocher, Termes et conditions et Vertical](/help/forms/assets/forms-components.png)

* **[Composant Onglets verticaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs.html?lang=fr)** : les formulaires adaptatifs basés sur les composants principaux peuvent désormais organiser le contenu des formulaires en une liste verticale d’onglets, ce qui assure une disposition structurée et navigable. L’utilisation d’onglets verticaux dans un formulaire peut améliorer l’expérience globale de l’utilisateur ou de l’utilisatrice en simplifiant la navigation et en améliorant l’organisation du contenu du formulaire, en particulier lorsqu’un formulaire contient plusieurs sections ou des informations complexes.



### Nouvelles fonctionnalités de la version préliminaire d’[!DNL Forms] {#prerelease-features-forms}

* **[Connexion d’un formulaire adaptatif à une liste Microsoft® SharePoint](/help/forms/configure-submit-actions-core-components.md#submit-to-sharepoint)** : AEM Forms assure une intégration prête à l’emploi pour envoyer les données de formulaire directement à la liste SharePoint, ce qui vous permet d’utiliser les fonctionnalités des listes SharePoint. Vous pouvez configurer Microsoft SharePoint List en tant que source de données pour un modèle de données de formulaire et utiliser la variable **Envoyer à l’aide du modèle de données de formulaire** Action d’envoi pour connecter un formulaire adaptatif à une liste SharePoint.

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Programme d&#39;adoption précoce {#forms-early-adopter}

* **[Envoyer un formulaire adaptatif au scénario de fusion Adobe Workfront](/help/forms/submit-adaptive-form-to-workfront-fusion.md)**: Forms as a Cloud Service propose des options prêtes à l’emploi pour connecter facilement un formulaire adaptatif à Adobe Workfront. Cela simplifie le processus d’envoi d’un formulaire adaptatif à un scénario Adobe Workfront, ce qui vous permet de déclencher un scénario de fusion Workfront lors de l’envoi d’un formulaire adaptatif.

* **[Prise en charge des langues de droite à gauche](/help/forms/supporting-new-language-localization-core-components.md)**: les Forms adaptatives reposant sur les composants principaux peuvent désormais être présentées dans une langue de droite à gauche (RTL) telle que l’arabe, le persan et l’ourdou. Les langues de la durée de vie sont parlées par plus de 2 milliards de personnes dans le monde. L’utilisation d’un formulaire en langage RTL vous permet d’étendre la portée de vos formulaires adaptatifs pour répondre à ces diverses audiences et les sélectionner dans les marchés RTL. Dans certaines régions, il est également légal de fournir des formulaires dans la langue locale. En s&#39;adaptant aux langues locales, vous ouvrez non seulement les portes à un public plus large, mais vous garantissez également le respect des lois et réglementations pertinentes.

  ![Prise en charge de la langue de droite à gauche](/help/forms/assets/right-to-left-language-support.png)

* **[Protect de vos documents avec les API DocAssurance (partie des API de communication)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: les API DocAssurance vous permettent de protéger les informations sensibles en signant et en chiffrant les documents. Grâce au chiffrement, le contenu d’un document est transformé en un format illisible, ce qui garantit que seuls les utilisateurs autorisés peuvent y accéder. Cette couche renforcée de protection protège non seulement les données précieuses des yeux non autorisés, mais offre également une certaine tranquillité d’esprit. Les API Signature permettent à votre entreprise de protéger la sécurité et la confidentialité des documents Adobe PDF qu’elle distribue et reçoit. Ce service utilise les signatures numériques et la certification pour s’assurer que seuls les destinataires prévus peuvent modifier les documents.

  Vous pouvez écrire sur `aem-forms-early-adopter-program@adobe.com` de votre e-mail officiel pour rejoindre le programme des premiers adopteurs et demander l’accès à la fonctionnalité.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Les règles de filtre de trafic WAF peuvent désormais être sous licence {#cdn-waf-license}

Les règles de filtrage du trafic ont été publiées en octobre et incluent une note indiquant que la catégorie spéciale des règles de pare-feu d’applications web (WAF) serait disponible plus tard dans l’année pour compléter les règles déjà disponibles pour les clients Sites et Forms. À titre de mise à jour, l’offre de protection WAF-DDoS peut désormais être mise sous licence.

Une fois sous licence, ces règles WAF avancées peuvent être déployées sur le réseau de diffusion de contenu à l’aide du pipeline de configuration de Cloud Manager pour ajouter une couche supplémentaire de protection contre les attaques web.

En savoir plus [Règles de filtrage du trafic](/help/security/traffic-filter-rules-including-waf.md), y compris WAF. Contactez votre équipe de compte AEM au sujet de la licence de la protection WAF-DDoS ou de la sécurité renforcée.

### Programme d’adoption précoce de la configuration CDN {#cdn-config-early-adopter}

Outre la version récemment publiée [Règles de filtre de trafic (y compris WAF)](/help/security/traffic-filter-rules-including-waf.md), il est possible d’utiliser le pipeline de configuration pour déclarer et déployer d’autres types de configuration CDN. Nous aimerions bien connaître vos cas pratiques, notamment :
* 301/302 redirections côté client
* proxy des requêtes en périphérie vers des origines arbitraires
* Conversion d’URL
* définition ou modification des en-têtes de requête ou de réponse
* pages d’erreur personnalisées lorsque le réseau de diffusion de contenu ne peut pas atteindre AEM
* authentification par nom d’utilisateur/mot de passe
* toute autre configuration CDN utile

Envoi d’un courrier électronique à **aemcs-cdn-config-adopter@adobe.com** de votre e-mail officiel avec vos commentaires.

## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici](/help/implementing/cloud-manager/release-notes/current.md).

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [ici](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).

## Problèmes connus {#known-issues}

* Impossible d’envoyer le Forms adaptatif en fonction des composants principaux. Le problème se produit pour les Forms adaptatives créées à l’aide des versions 2.0.38 à 2.0.60 des composants principaux.

  Pour résoudre le problème. vous pouvez passer à la version 2.0.62 ou ultérieure des composants principaux de formulaire adaptatif. Pour définir une version des composants principaux de Forms adaptatif pour votre environnement, [Définissez les versions du composant core.forms.components.version, core.forms.components.af.version et core.wcm.components.version .](/help/forms/enable-adaptive-forms-core-components.md#2-add-adaptive-forms-core-components-dependencies-to-your-git-repository) les dépendances dans votre projet Forms as a Cloud Service ou basé sur AEM Archetype et [déployer les modifications dans votre environnement Forms as a Cloud Service ;](/help/forms/enable-adaptive-forms-core-components.md#build-and-deploy-updated-code-on-an-aem-forms-as-a-cloud-service-environment). Vous trouverez la dernière version des dépendances des composants principaux de Forms adaptatif à l’adresse [Référentiel Git des composants principaux de Forms adaptatif](https://github.com/adobe/aem-core-forms-components#system-requirements).
