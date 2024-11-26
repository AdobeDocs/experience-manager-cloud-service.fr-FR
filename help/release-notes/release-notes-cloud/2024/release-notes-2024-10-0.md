---
title: Notes de mise à jour de la version 2024.10.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la version 2024.10.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 7a63f04f-10f0-4879-bd06-4182bb288a9b
source-git-commit: c3beecaab03c3721ad2fb70658a335d17f9a66d0
workflow-type: tm+mt
source-wordcount: '1664'
ht-degree: 100%

---

# Notes de mise à jour de la version 2024.10.0 d’[!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour de la version 2024.10.0 d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes, telles que 2022 ou 2023.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Pour recevoir chaque mois une notification par e-mail concernant des informations sur les notes de mise à jour d’Experience Cloud, abonnez-vous aux [Mises à jour de produits prioritaires d’Adobe](https://www.adobe.com/subscription/priority-product-update.html).

## Date de publication {#release-date}

La date de publication de la version actuelle d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2024.10.0) est le 31 octobre 2024. La prochaine version des fonctionnalités (2024.11.0) est prévue pour le 21 novembre 2024.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

## Vidéo de mise à jour {#release-video}

Regardez la vidéo de vue d’ensemble de la version d’octobre 2024 pour un résumé des fonctionnalités ajoutées dans la version 2024.10.0 :

>[!VIDEO](https://video.tv.adobe.com/v/3440501?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

**Modernisation des événements de page**

Les événements suivants de la page AEM Sites sont désormais accessibles en tant qu’événements externes consommables, grâce à la plateforme d’événements d’AEM as a Cloud Service. Les événements peuvent être traités via Adobe I/O pour interagir avec des processus externes.
* Page publiée
* Page non publiée
* Page supprimée

### Programme d’adoption précoce {#sites-early-adopter}

**Générer des variations**

Tirez profit de GenAI grâce à une nouvelle fonctionnalité d’AEM, [générer des variations](/help/generative-ai/generate-variations.md), maintenant accessible dans Cloud Service. La génération de variations vous permet de générer et d’adapter la création de contenu grâce à l’utilisation de l’IA générative. Contactez votre équipe Adobe en charge des comptes pour en savoir plus sur le programme.

**API AEM REST OpenAPI pour la diffusion de fragments de contenu**

L’[API AEM REST OpenAPI pour la diffusion de fragments de contenu ](/help/headless/aem-rest-openapi-content-fragment-delivery.md) est désormais disponible pour AEM as a Cloud Service.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Fonctionnalité d’accès anticipé dans Dynamic Media {#dm-early-access}

**Sous-titres vidéo générés par l’IA**

Adobe Dynamic Media utilise l’intelligence artificielle pour générer automatiquement des sous-titres pour le contenu vidéo. Cette fonctionnalité est conçue pour améliorer l’accessibilité et l’expérience d’utilisation en fournissant des sous-titres précis en temps réel. L’IA analyse la piste audio de la vidéo pour transcrire la parole et créer des sous-titres, qui peuvent être modifiés pour plus de précision ou de personnalisation. Ces sous-titres permettent de répondre aux exigences d’accessibilité et d’améliorer l’engagement vidéo pour les audiences qui dépendent d’une prise en charge vidéo basée sur le texte ou qui préfèrent ce système.

Pour bénéficier d’un accès anticipé à la prise en charge des sous-titres générés par l’IA sur votre compte Dynamic Media, vous devez [créer et envoyer un cas d’assistance clientèle Adobe ](/help/assets/dynamic-media/video.md##enable-dash).

### Nouvelles fonctionnalités de la vue Assets {#assets-view-new-features}

**Rapports planifiés**

Les rapports peuvent désormais être générés automatiquement dans la vue Assets selon un planning récurrent ou à une date ultérieure, ce qui réduit les efforts nécessaires pour obtenir des informations fondées sur des données.

![Rapports planifiés](/help/assets/assets/scheduled-reports-tab.png)

### Nouvelles fonctionnalités dans Content Hub {#content-hub-new-features}

**Digital Rights Management pour les ressources sous licence**

Grâce à DRM pour les ressources sous licence, les entreprises peuvent désormais améliorer la conformité aux licences et réduire les risques associés au partage de ressources. Les utilisateurs et les utilisatrices de Content Hub doivent d’abord examiner et accepter les conditions de licence avant de télécharger les ressources sous licence. Pour plus d’informations, consultez la section [Gestion des ressources sous licence sur Content Hub](/help/assets/manage-licensed-assets-on-content-hub.md).

![download-multiple-license](/help/assets/assets/download-multiple-license.png)

**Configuration des métadonnées de carte de ressources**

Content Hub vous permet désormais de configurer jusqu’à 6 champs de métadonnées clés à afficher sur la carte de ressources. Pour plus d’informations, consultez la section Carte de ressources dans [Configuration de Content Hub](/help/assets/configure-content-hub-ui-options.md#asset-card).

![Métadonnées clés sur la carte de ressources](/help/assets/assets/asset-card-key-metadata.png)

**Configurer la visibilité et le téléchargement des ressources expirées**

Les administrateurs et administratrices peuvent désormais contrôler s’ils ont besoin que les ressources expirées soient visibles dans Content Hub. Si les ressources expirées sont rendues visibles, les administrateurs et les administratrices peuvent également choisir de permettre ou non leur téléchargement. Pour plus d’informations, consultez la section Ressources expirées dans [Configuration de Content Hub](/help/assets/configure-content-hub-ui-options.md#expired-assets-content-hub).

![Ressources expirées sur le hub de contenus](/help/assets/assets/expired-assets-content-hub.png)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelle fonctionnalité d’AEM Forms {#forms-new-features}

* [Amélioration de l’interface d’utilisation grâce aux boutons de navigation dans les mises en page de panneau](/help/forms/rule-editor-core-components-usecases.md#navigating-among-panels-using-button) : vous pouvez désormais ajouter des boutons de navigation à vos mises en page de panneau, par exemple Onglets horizontaux, Onglets verticaux, Accordéons ou Assistant. Ces boutons optimisent la navigation en simplifiant les transitions entre les panneaux et en mettant l’accent sur le panneau sélectionné.

<!--* **Specify Display Styles for Document of Record (DoR) Components**: In an XFA file, you can now specify the display styles for Document of Record components. These styles can later be applied to the corresponding components in Adaptive Forms Editor.-->

### Nouvelles fonctionnalités de la version préliminaire d’AEM Forms {#forms-new-prerelease-features}

* [Enregistrement automatique d’un brouillon pour les formulaires adaptatifs basés sur les composants principaux](/help/forms/save-core-component-based-form-as-draft.md) : les utilisateurs et les utilisatrices peuvent désormais bénéficier d’une fonction d’enregistrement automatique, qui sauvegarde automatiquement un formulaire partiellement complété en tant que brouillon. Ces personnes peuvent revenir ultérieurement pour finir de le remplir sur le même appareil ou sur un autre. Cette fonctionnalité améliore les taux de conversion pour les organisations en réduisant l’abandon de formulaire, car les utilisateurs et utilisatrices n’ont pas besoin de recommencer à remplir le formulaire depuis le début.

* [Mise à jour simplifiée des portées d’Adobe Sign](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/forms/integrate/services/adobe-sign-integration-adaptive-forms) : vous pouvez modifier les portées d’une configuration Adobe Sign directement depuis la page Configurations d’AEM Cloud, simplifiant et accélérant ainsi la mise à jour des configurations existantes.

* [Prise en charge des fonctions asynchrones pour les formulaires adaptatifs](/help/forms/using-async-funct-in-rule-editor.md) : lorsque votre formulaire adaptatif nécessite des opérations asynchrones, comme l’attente de processus externes ou la récupération de données, vous pouvez implémenter ces opérations avec des fonctions personnalisées et les configurer dans l’éditeur de règles.

### Fonctionnalités d’accès anticipé dans AEM Forms {#forms-new-early-access-features}

Le programme d’accès anticipé d’AEM Forms vous offre une opportunité unique d’accéder de manière exclusive à des innovations de pointe et de contribuer à façonner leur développement.

Les notes de mise à jour répertorient les innovations apportées à la version actuelle. Pour obtenir la liste complète des innovations disponibles dans le cadre du programme d’accès anticipé, voir [Documentation du programme d’accès anticipé d’AEM Forms](/help/forms/early-access-ea-features.md).

#### Assistant IA d’AEM Forms

L’[IA générative pour les formulaires adaptatifs](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/forms/forms-overview/early-access-ea-features#aem-forms-ai-assistant-gen-ai) offre un nouveau niveau de puissance et de facilité à vos processus de développement de formulaires. Elle vous permet de créer de meilleurs formulaires plus rapidement que jamais auparavant.

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

### Correctifs {#bug-fixes-cif}

* Correction des tests de l’interface d’utilisation pour qu’ils fonctionnent correctement avec les composants principaux CIF.
* Correction d’un problème en raison duquel le format des URL de catégorie ne fonctionnait pas comme prévu dans l’instance cloud.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Configuration pour contrôler les envois de formulaire {#configuration-submissions}

Pour contrôler les envois de formulaires Coral ou Foundation à des emplacements spécifiques, AEM a introduit une nouvelle configuration : `com.adobe.granite.ui.components.FormRestrict`. Cette configuration se compose de deux champs :

1. **Ajouter des chemins d’accès autorisés** : spécifie les chemins où les actions de formulaire sont autorisées.
1. **Restreindre le comportement** : détermine le comportement des chemins restreints (chemins non inclus dans la liste des chemins autorisés). Faites votre choix parmi les options suivantes :
   * **Fenêtre contextuelle** (par défaut) : affiche une notification contextuelle.
   * **Empêcher** : bloque l’envoi du formulaire.

>[!NOTE]
>
>Cette configuration n’est pas prise en charge pour tous les formulaires Coral ou Foundation situés sous `/apps`, `/libs`, `/mnt/overlay` et `/mnt/override`.

### Transfert de journaux en libre-service avec option de mise en réseau avancée {#log-forwarding}

Bien que les journaux AEM (y compris Apache/Dispatcher) et CDN puissent être téléchargés depuis Cloud Manager, de nombreuses entreprises préfèrent diffuser ces journaux vers une destination de journalisation spécifique. AEM prend désormais en charge le [transfert de journaux](/help/implementing/developing/introduction/log-forwarding.md) vers Azure Blob Storage, Datadog, HTTPS, Elasticsearch (et OpenSearch) et Splunk. Les journaux d’AEM peuvent, le cas échéant, être envoyés vers des configurations réseau avancées, comme l’utilisation d’une adresse IP dédiée.

Cette fonctionnalité est configurée par les utilisateurs et les utilisatrices en libre-service et déployée à l’aide du [pipeline de configuration](/help/operations/config-pipeline.md).

### Redirections d’URL sans pipeline pour les utilisateurs et utilisatrices professionnels {#pipeline-free-redirects}

L’utilisation de redirections côté navigateur est pertinente lorsqu’une page web a été supprimée, déplacée ou dans des scénarios comparables. Avec les [redirections d’URL sans pipeline](/help/implementing/dispatcher/pipeline-free-url-redirects.md), il est possible de placer un fichier de réécriture Apache dans un emplacement de publication AEM, où il sera chargé automatiquement, sans validation dans le contrôle des sources ni lancement de pipeline Cloud Manager.

Les options pour publier le fichier de réécriture incluent son chargement en tant que ressource, l’utilisation du gestionnaire de cartes de réécriture ACS Commons ou l’interaction avec une interface d’utilisation personnalisée.

### Pipeline de configuration pour les RDE {#config-pipeline-rdes}

Les environnements de développement rapide (RDE) sont un outil puissant pour déployer et tester rapidement le code et la configuration dans un environnement cloud. Les RDE prennent désormais en charge la [synchronisation des fichiers YAML de configuration](/help/implementing/developing/introduction/rapid-development-environments.md#deploy-config-pipeline), y compris les paramètres CDN tels que les règles de filtrage du trafic et les transformations requête/réponse, ainsi que la redirection des journaux et d’autres options de configuration. Pour plus d’informations, [consultez la liste complète](/help/operations/config-pipeline.md) des options de configuration prises en charge.

### Nouveaux profils de produit {#new-product-profiles}

Lorsque qu’un nouvel environnement AEM est créé, les profils de produit apparaissent automatiquement dans Adobe Admin Console, permettant à l’équipe d’administration d’attribuer l’accès aux solutions et fonctionnalités sous licence.

Les nouveaux environnements incluent désormais un ensemble mis à jour de profils de produit, assurant leur compatibilité avec les fonctionnalités futures, comme la génération d’informations d’identification d’API dans Adobe Developer Console. Les environnements existants pourront mettre à jour leurs profils de produit dans une version ultérieure. [En savoir plus](/help/onboarding/aem-cs-team-product-profiles.md).

### Nouvelle AEM Developer Console (version bêta publique) {#aem-developer-console-beta}

Testez une [AEM Developer Console](/help/implementing/developing/introduction/aem-developer-console.md) repensée qui offre une expérience plus interactive pour le débogage du code dans les environnements cloud.

Tout le monde peut accéder à la version Beta publique en cliquant sur le bouton *Nouvelle console disponible* dans la console AEM Developer Console actuelle. Adobe recueille les commentaires. Vous pouvez les envoyer par e-mail à **<aemcs-new-devconsole-ui-beta@adobe.com>**.

![Écran de lots OSGi dans AEM Developer Console](/help/implementing/developing/introduction/assets/osgi-bundles.png)

## [!DNL Experience Manager] Guides {#guides}

Vous trouverez une liste complète des nouvelles fonctionnalités améliorées de la dernière version d’Adobe Experience Manager Guides [ici](https://experienceleague.adobe.com/fr/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2410-0-release/whats-new-2024-10-0).

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
