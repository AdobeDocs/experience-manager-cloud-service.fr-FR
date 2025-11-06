---
title: Notes de mise à jour de la version 2023.11.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la version 2023.11.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 19cff082-80aa-445c-9462-5e319b7fe0e9
feature: Release Information
role: Admin
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1282'
ht-degree: 57%

---

# Notes de mise à jour de la version 2023.11.0 d’[!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour de la version 2023.11.0 d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes, telles que 2021 ou 2022.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de la version actuelle d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2023.11.0) est le vendredi 30 novembre 2023. La prochaine version des fonctionnalités (2023.12.0) est prévue pour le vendredi 14 décembre 2023.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

## Vidéo de mise à jour {#release-video}

Consultez la vidéo Vue d’ensemble de la version de novembre 2023 pour obtenir un résumé des fonctionnalités ajoutées dans la version 2023.11.0 :

>[!VIDEO](https://video.tv.adobe.com/v/3425864?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Programme d’adoption précoce {#sites-early-adopter}

**[Rechercher et remplacer des chaînes dans les fragments de contenu](/help/sites-cloud/administering/content-fragments/managing.md#find-and-replace-find-and-replace)** : la console de fragments de contenu permet aux utilisateurs de remplacer facilement et intuitivement une chaîne apparaissant en même temps dans plusieurs fragments de contenu afin d’accélérer la vitesse du contenu.

![Rechercher et remplacer](/help/sites-cloud/administering/content-fragments/assets/cf-managing-find-replace.png)

Vous souhaitez tester la fonctionnalité et partager vos commentaires ? Envoyez un e-mail à **aemcs-headless-adopter@adobe.com** à partir de votre ID d’e-mail officiel pour en savoir plus sur le programme des utilisateurs et utilisatrices précoces.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de la vue Assets {#assets-view-features}

* **Éditeur Adobe Express intégré à AEM Assets** : les utilisateurs ayant accès à Express disposent désormais d’outils intégrés d’édition et de création d’images provenant d’Adobe Express et d’Adobe Firefly, disponibles directement dans AEM Assets, afin d’améliorer la réutilisation du contenu et d’accélérer sa vitesse.

  ![Affectation d’un formulaire de métadonnées à un dossier.](/help/assets/assets/adobe-express-aem-assets.png)

<!--

* **Smart tags blocklist**: Experience Manager Assets now enables you to define a list of blocked tags. These tags are automatically removed from the auto-generated smart tags when you upload assets to the repository. This capability performs tags governance and saves a lot of time as you can add a tag to the block list and AEM Assets automatically excludes it from the list of tags for any of the assets that are added to the repository.

  ![storage usage insights](/help/assets/assets/block-tags.png)

-->


* **Rapports d’utilisation du stockage dans Insights** : les administrateurs peuvent désormais afficher les rapports d’utilisation du stockage disponibles dans Insights.

  ![Informations sur l’utilisation du stockage](/help/assets/assets/storage-usage-insights.png)

* **Rechercher la première configuration de la page d’accueil** : Experience Manager Assets vous permet désormais de configurer l’expérience de la page d’accueil pour votre organisation. Si vous sélectionnez l’approche axée sur la recherche pour votre page d’accueil, vous pouvez configurer l’alignement de la barre de recherche, l’image d’arrière-plan et le logo de votre organisation.

  ![Configuration de l’approche axée sur la recherche.](/help/assets/assets/search-first-configuration.png)

### Nouvelles fonctionnalités de la version préliminaire pour la vue Administration {#admin-view-features-prerelease}

**Aperçu vidéo** : AEM Assets génère désormais des rendus d’aperçu de tous les formats vidéo pris en charge par défaut, sans avoir à configurer de profil de traitement.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités de [!DNL Experience Manager Forms] {#forms-features}

* **[Composant de case à cocher](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/checkbox.html?lang=fr)** : les formulaires adaptatifs basés sur les composants principaux peuvent désormais inclure un composant de case à cocher. Il permet aux utilisateurs et utilisatrices de faire des choix binaires, en sélectionnant ou en désélectionnant une option particulière. Il s’affiche généralement sous la forme d’une petite case sur laquelle vous pouvez cliquer ou appuyer pour basculer entre deux états : cochée et décochée. La case à cocher est un élément de formulaire courant, utilisé pour présenter un choix oui/non ou vrai/faux.

* **[Composant Conditions générales](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/terms-and-conditions.html?lang=fr)** : les formulaires adaptatifs basés sur les composants principaux peuvent désormais inclure un composant Conditions générales. Il permet aux personnes créant les formulaires d’introduire une section spécifique dans le formulaire, dans laquelle les utilisateurs et utilisatrices peuvent consulter les conditions générales ou les accords juridiques associés à l’utilisation d’un service, d’un produit ou d’une plateforme. Ce composant est conçu pour informer les utilisateurs et utilisatrices des règles, des réglementations et des obligations qu’ils acceptent en envoyant le formulaire.

  ![Composants Case à cocher, Conditions générales et Onglet vertical](/help/forms/assets/forms-components.png)

* **[Composant Onglets verticaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs.html?lang=fr)** : les formulaires adaptatifs basés sur les composants principaux peuvent désormais organiser le contenu des formulaires en une liste verticale d’onglets, ce qui assure une disposition structurée et navigable. L’utilisation d’onglets verticaux dans un formulaire peut améliorer l’expérience globale de l’utilisateur ou de l’utilisatrice en simplifiant la navigation et en améliorant l’organisation du contenu du formulaire, en particulier lorsqu’un formulaire contient plusieurs sections ou des informations complexes.



### Nouvelles fonctionnalités de la version préliminaire de [!DNL Forms] {#prerelease-features-forms}

* **[Connecter un Forms adaptatif à une liste SharePoint Microsoft®](/help/forms/configure-submit-actions-core-components.md#submit-to-sharepoint)** : AEM Forms fournit une intégration prête à l’emploi pour envoyer directement des données de formulaire à la liste SharePoint, ce qui vous permet d’exploiter les fonctionnalités des listes SharePoint. Vous pouvez configurer la liste Microsoft SharePoint en tant que source de données pour un modèle de données de formulaire et utiliser l’action d’envoi **Envoyer à l’aide du modèle de données de formulaire** pour connecter un formulaire adaptatif à la liste SharePoint.

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Programme d’adoption précoce {#forms-early-adopter}

* **Envoi d’un formulaire adaptatif au scénario Adobe Workfront Fusion** : Forms as a Cloud Service propose des options prêtes à l’emploi pour connecter facilement un formulaire adaptatif à Adobe Workfront. Cela simplifie le processus d’envoi d’un formulaire adaptatif à un scénario Adobe Workfront, ce qui permet de déclencher un scénario Workfront Fusion lors de l’envoi d’un formulaire adaptatif.

* **Prise en charge des langues de droite à gauche** : les formulaires adaptatifs reposant sur les composants principaux peuvent désormais être présentés dans une langue de droite à gauche telle que l’arabe, le persan et l’ourdou. Les langues s’écrivant de droite à gauche sont parlées par plus de 2 milliards de personnes dans le monde. L’utilisation d’un formulaire dans le langage de RTL vous permet d’étendre la portée de vos formulaires adaptatifs afin de répondre aux besoins de ces différentes audiences et d’exploiter les marchés de RTL. Dans certaines régions, il en va d’une obligation légale de fournir des formulaires dans la langue locale. En vous adaptant aux langues locales, vous vous ouvrez non seulement à une audience plus large, mais vous garantissez aussi le respect des lois et réglementations pertinentes.

  ![Prise en charge des langues de droite à gauche.](/help/forms/assets/right-to-left-language-support.png)

* **[Protégez vos documents avec les API DocAssurance (qui font partie des API de communication)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)** : les API DocAssurance vous permettent de protéger les informations sensibles en signant et en chiffrant les documents. Grâce au chiffrement, le contenu d’un document est transformé en un format illisible, ce qui garantit que seules les personnes autorisées peuvent y accéder. Cette couche renforcée de protection protège non seulement les données précieuses des yeux non autorisés, mais offre également une certaine tranquillité d’esprit. Les API Signature permettent à votre entreprise de garantir la sécurité et la confidentialité des documents Adobe PDF qu’elle diffuse et reçoit. Ce service utilise les signatures numériques et la certification pour s’assurer que seules les personnes destinataires prévues peuvent modifier les documents.

  Vous pouvez écrire à `aem-forms-ea@adobe.com` depuis votre adresse e-mail officielle pour rejoindre le programme d’adoption précoce et demander l’accès à la fonctionnalité.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Les Règles De Filtrage Du Trafic WAF Peuvent Désormais Être Sous Licence {#cdn-waf-license}

Les règles de filtrage du trafic ont été publiées en octobre et comprennent une note indiquant que la catégorie spéciale de règles de pare-feu d’application web (WAF) sera disponible plus tard dans l’année pour compléter les règles déjà disponibles pour les clients Sites et Forms. À titre de mise à jour, l’offre de protection WAF-DDoS peut désormais être sous licence.

Une fois la licence obtenue, ces règles WAF avancées peuvent être déployées sur le réseau CDN à l’aide du pipeline de configuration Cloud Manager pour ajouter un niveau supplémentaire de protection contre les attaques web.

En savoir plus sur les [ Règles de filtrage du trafic ](/help/security/traffic-filter-rules-including-waf.md), y compris WAF. Contactez votre équipe de compte AEM pour en savoir plus sur l’obtention d’une licence pour la protection WAF-DDoS ou la sécurité renforcée.

### Programme de mappage de domaines pour les utilisateurs et utilisatrices précoces {#cdn-config-early-adopter}

Outre les [ Règles de filtrage du trafic (y compris WAF)](/help/security/traffic-filter-rules-including-waf.md) récemment publiées, il est possible d’utiliser le pipeline de configuration pour déclarer et déployer d’autres types de configuration de réseau CDN. Nous aimerions en savoir plus sur vos cas d’utilisation, notamment :

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

## Problèmes connus {#known-issues}

* Impossible d’envoyer le Forms adaptatif en fonction des composants principaux. Le problème se produit pour les Forms adaptatives créées à l’aide des composants principaux versions 2.0.38 à 2.0.60.

  Pour résoudre le problème. vous pouvez passer aux composants principaux de formulaire adaptatif version 2.0.62 ou ultérieure. Pour définir une version des composants principaux de Forms adaptatif pour votre environnement, définissez les versions des dépendances `core.forms.components.version`, `core.forms.components.af.version` et `core.wcm.components.version component` dans votre référentiel Forms as a Cloud Service ou votre projet basé sur l’archétype AEM et déployez les modifications dans votre environnement Forms as a Cloud Service. Vous trouverez la dernière version des dépendances des composants principaux de Forms adaptative dans [Référentiel Git des composants principaux de Forms adaptatif](https://github.com/adobe/aem-core-forms-components#system-requirements).
