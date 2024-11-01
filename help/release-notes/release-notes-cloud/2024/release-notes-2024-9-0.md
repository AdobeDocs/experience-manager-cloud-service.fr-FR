---
title: Notes de mise à jour de la version 2024.9.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la version 2024.9.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
feature: Release Information
role: Admin
source-git-commit: 0c4db1b70aa665e1802a316ece26db1e06f40b24
workflow-type: tm+mt
source-wordcount: '1324'
ht-degree: 91%

---

# Notes de mise à jour de la version 2024.9.0 d’[!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour de la version 2024.9.0 d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes, telles que 2022 ou 2023.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Pour recevoir chaque mois une notification par e-mail concernant des informations sur les notes de mise à jour d’Experience Cloud, abonnez-vous aux [Mises à jour de produits prioritaires d’Adobe](https://www.adobe.com/subscription/priority-product-update.html).

## Date de publication {#release-date}

La date de publication de la version actuelle (2024.9.0) d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le 26 septembre 2024. La prochaine disponibilité des fonctionnalités (2024.10.0) est prévue pour le 31 octobre 2024.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

## Vidéo de mise à jour {#release-video}

Consultez la vidéo Vue d’ensemble de la version de septembre 2024 pour obtenir un résumé des fonctionnalités ajoutées dans la version 2024.9.0 :

>[!VIDEO](https://video.tv.adobe.com/v/3434847?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités dans Experience Manager Sites {#new-feature-sites}

#### Gestion des traductions {#translation-management}

Les workflows de traduction et les actions d’API AEM déclenchent désormais des événements fournissant des informations sur les modifications de l’état des tâches de traduction. Les personnes peuvent s’abonner à ces événements par le biais d’Adobe Developer Console. Voir [ici](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/translation/) pour plus d’informations sur l’API de gestion de traduction AEM.

### Programme d’adoption précoce {#sites-early-adopter}

**Générer des variations**

Tirez profit de GenAI grâce à une nouvelle fonctionnalité d’AEM, [générer des variations](/help/generative-ai/generate-variations.md), maintenant accessible dans Cloud Service. La génération de variations vous permet de générer et d’adapter la création de contenu grâce à l’utilisation de l’IA générative. Contactez votre équipe Adobe en charge des comptes pour en savoir plus sur le programme.


## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Fonctionnalité d’accès anticipé dans Dynamic Media {#dm-early-access}

**Sous-titres vidéo générés par l’IA**

Adobe Dynamic Media utilise l’intelligence artificielle pour générer automatiquement des sous-titres pour le contenu vidéo. Cette fonctionnalité est conçue pour améliorer l’accessibilité et l’expérience d’utilisation en fournissant des sous-titres précis en temps réel. L’IA analyse la piste audio de la vidéo pour transcrire la parole et créer des sous-titres, qui peuvent être modifiés pour plus de précision ou de personnalisation. Ces sous-titres permettent de répondre aux exigences d’accessibilité et d’améliorer l’engagement vidéo pour les audiences qui dépendent d’une prise en charge vidéo basée sur le texte ou qui préfèrent ce système.

Pour bénéficier d’un accès anticipé à la prise en charge des sous-titres générés par l’IA sur votre compte Dynamic Media, vous devez [créer et envoyer un cas d’assistance clientèle Adobe ](/help/assets/dynamic-media/video.md##enable-dash).

### Nouvelles fonctionnalités du sélecteur de ressources {#asset-selector-new-features}

Le sélecteur de ressources prend désormais en charge la navigation dans les collections pour trouver la ressource souhaitée.
![Collections du sélecteur de ressources](/help/assets/assets/collections-rail-modal-view.png)

### Nouvelles fonctionnalités du hub de contenus {#content-hub-new-features}

Les administrateurs et administratrices peuvent désormais contrôler s’ils ou elles ont besoin que les ressources expirées soient visibles dans le hub de contenus. Si les ressources expirées sont rendues visibles, les administrateurs et administratrices peuvent également définir si les personnes peuvent les télécharger.

![Ressources expirées sur le hub de contenus](/help/assets/assets/view-download-expired-assets.png)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités de la version préliminaire d’AEM Forms {#forms-new-prerelease-features}

#### Enregistrement automatique d’un brouillon pour les formulaires adaptatifs basés sur les composants principaux

Les utilisateurs et utilisatrices peuvent désormais bénéficier d’une fonctionnalité d’enregistrement automatique qui enregistre automatiquement un formulaire partiellement rempli en tant que brouillon. Ces personnes peuvent revenir ultérieurement pour finir de le remplir sur le même appareil ou sur un autre. Cette fonctionnalité améliore les taux de conversion pour les organisations en réduisant l’abandon de formulaire, car les utilisateurs et utilisatrices n’ont pas besoin de recommencer à remplir le formulaire depuis le début.


### Fonctionnalités d’accès anticipé dans AEM Forms {#forms-new-early-access-features}

Le programme d’accès anticipé d’AEM Forms vous offre une opportunité unique d’accéder de manière exclusive à des innovations de pointe et de contribuer à façonner leur développement.

Les notes de mise à jour répertorient les innovations apportées à la version actuelle. Pour obtenir la liste complète des innovations disponibles dans le cadre du programme d’accès anticipé, voir [Documentation du programme d’accès anticipé d’AEM Forms](/help/forms/early-access-ea-features.md).

#### Assistant IA d’AEM Forms

L’IA générative pour les formulaires adaptatifs offre un nouveau niveau de puissance et de facilité à vos processus de développement de formulaires. Elle vous permet de créer de meilleurs formulaires plus rapidement que jamais auparavant.

![Assistant IA générative, formulaires adaptatifs](/help/forms/assets/generative-ai-assistant.png)

Les fonctionnalités de l’IA générative proposées sont les suivantes :

* **Assistant IA pour les requêtes de produits** : obtenez des réponses instantanées à vos question sur les formulaires AEM. L’assistant IA sert de base de connaissances personnelle, fournissant des recommandations et des conseils pertinents directement au sein de la plateforme.

* **Génération de formulaires adaptatifs** : créez facilement des formulaires complets avec des invites d’IA générative. L’IA générative d’Adobe génère automatiquement des formulaires conviviaux qui réduisent les abandons et personnalisent l’expérience.

* **Génération de panneau pour Forms** : générez des sections de formulaire adaptées à des besoins spécifiques de collecte de données. Par exemple, générez des sections pour collecter des informations sur le paiement, les préférences des clientes et clients ou les détails du voyage.

* **Modification des mises en page de formulaire** : testez différentes mises en page et conceptions à l’aide des invites d’IA générative. Testez différentes mises en page, telles que l’assistant ou les onglets, afin de trouver ce qui convient le mieux pour votre formulaire. Utilisez les invites d’IA générative afin d’optimiser vos formulaires pour la réactivité mobile et de créer des formulaires attrayants pour les utilisateurs et utilisatrices.

* **Configurer l’action d’envoi** : utilisez les invites d’IA générative pour configurer facilement une action d’envoi pour votre formulaire. Faites votre choix parmi une bibliothèque d’actions d’envoi préconfigurées ou parmi une liste d’actions d’envoi personnalisées, créées et déployées par votre propre équipe de développement.

>[!IMPORTANT]
>
> Vous souhaitez adhérer au Programme d’accès anticipé pour des formulaires innovants ? Envoyez un e-mail depuis votre adresse officielle à [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) avec la liste des fonctionnalités qui vous intéressent.

## Module complémentaire CIF {#cloud-services-cif}

### Améliorations {#improvements-fixes-cif}

* Rendre la limite de catégorie personnalisable.

### Correctifs {#bug-fixes-cif}

* Les champs Commerce ne sont pas correctement intégrés à l’éditeur de schéma de métadonnées Assets.
* Problème de glisser-déposer pour le multichamp Produits du carrousel.
* Problème de glisser-déposer pour le multichamp Catégorie de carrousel.
* Le fait de cliquer ne fonctionne pas pour les menus dans les Informations sur la page de l’éditeur de catégories et de produits.
* Le numéro de commande n’est pas visible dans la page de confirmation de commande.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Edge Side Includes (ESI) pour le chargement de contenu dynamique {#esi}

Le réseau CDN géré par Adobe prend désormais en charge [Edge Side Includes (ESI)](/help/implementing/dispatcher/edge-side-includes.md), un langage de balisage pour l’assemblage de contenu web dynamique au niveau Edge. En incluant des extraits de code ESI, vous pouvez mettre en cache la page HTML globale sur le réseau CDN avec des TTL plus élevés, tout en récupérant plus fréquemment de l’origine les sections plus petites qui nécessitent des mises à jour à un rythme supérieur (TTL moins élevés). Cette fonctionnalité sera déployée progressivement.

### Authentification de base sur le réseau de diffusion de contenu {#basicauth-cdn}

Protégez certaines ressources de contenu en affichant une boîte de dialogue d’authentification de base nécessitant un nom d’utilisateur ou d’utilisatrice et un mot de passe. Cette fonctionnalité cible principalement les cas d’utilisation de l’authentification légère, comme les parties prenantes de l’entreprise qui examinent le contenu, plutôt que de servir de solution complète pour les droits d’accès des utilisateurs et utilisatrices finaux. La liste des noms d’utilisateur et mots de passe est gérée par le biais d’un fichier de configuration dans Git déployé via le pipeline de configuration, avec une référence aux variables d’environnement Cloud Manager de type secret. [En savoir plus](/help/implementing/dispatcher/cdn-credentials-authentication.md#basic-auth).

### Redirections côté client {#client-side-redirects}

Déclarez les [redirections de navigateur](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors) dans un fichier de configuration Git déployé et évalué sur le réseau de diffusion de contenu. Cela peut s’avérer utile dans le cas de scénarios tels que la suppression de pages, la modification de la structure du site et l’optimisation de l’optimisation pour les moteurs de recherche.

### Nouvelle AEM Developer Console (version bêta publique) {#aem-developer-console-beta}

Testez une [AEM Developer Console](/help/implementing/developing/introduction/aem-developer-console.md) repensée qui offre une expérience plus interactive pour le débogage du code dans les environnements cloud.

Tout le monde peut accéder à la version Beta publique en cliquant sur le bouton *Nouvelle console disponible* dans la console AEM Developer Console actuelle. Adobe recueille les commentaires. Vous pouvez les envoyer par e-mail à **<aemcs-new-devconsole-ui-beta@adobe.com>**.

![Écran de lots OSGi dans AEM Developer Console](/help/implementing/developing/introduction/assets/osgi-bundles.png)

### Les utilisateurs et utilisatrices professionnels peuvent déclarer des redirections en dehors de Git (programme d’adoption précoce) {#apache-rewritemaps-early-adopter}

Comme pour AEM 6.5, Apache/le Dispatcher ingère des mappages de réécriture placés à un emplacement spécifique dans le référentiel de publication et les charge, sans nécessiter d’exécution de pipeline de niveau web. Cette approche permet aux utilisateurs et aux utilisatrices professionnels de déclarer des redirections à l’aide d’une feuille de calcul ou d’une interface d’utilisation, comme le gestionnaire de mappage de redirection ACS Commons ou une application personnalisée. Pour rejoindre le programme d’adoption précoce, envoyez un e-mail à **<aemcs-cdn-config-adopter@adobe.com>**.

### Pipeline de configuration des RDE (programme d’adoption précoce) {#config-pipeline-rdes-early-adopter}

Le [pipeline de configuration](/help/operations/config-pipeline.md) est utilisé pour déployer les configurations de fichiers yaml, y compris les options CDN (règles de filtrage du trafic, transformations de requête/réponse, etc.). Rejoignez le programme d’adoption précoce en envoyant un e-mail à **<aemcs-cdn-config-adopter@adobe.com>** pour déployer ces mêmes configurations dans des RDE (Rapid Development Environments) qui utilisent une interface de ligne de commande.

## [!DNL Experience Manager] Guides {#guides}

Vous trouverez une liste complète des nouvelles fonctionnalités améliorées de la dernière version d’Adobe Experience Manager Guides [ici](https://experienceleague.adobe.com/fr/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2406-release/whats-new-2024-06-0).

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
