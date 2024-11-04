---
title: Notes de mise à jour actuelles pour  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour actuelles pour  [!DNL Adobe Experience Manager]  as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: 9bb2d38feea2690bc112611d429dad22e7bcd278
workflow-type: tm+mt
source-wordcount: '1514'
ht-degree: 58%

---

# Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour techniques de la version actuelle (la plus récente) d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes, telles que 2022 ou 2023.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Pour recevoir chaque mois une notification par e-mail concernant des informations sur les notes de mise à jour d’Experience Cloud, abonnez-vous aux [Mises à jour de produits prioritaires d’Adobe](https://www.adobe.com/subscription/priority-product-update.html).

## Date de publication {#release-date}

La date de publication de la version actuelle de [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2024.10.0) est le vendredi 31 octobre 2024. La prochaine version des fonctionnalités (2024.11.0) est prévue pour le vendredi 21 novembre 2024.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

<!-- ## Release Video {#release-video}

Have a look at the October 2024 Release Overview video for a summary of the features added in the 2024.10.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3434847?quality=12)

-->

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

**Événements de page modernisés**

Les événements de page AEM Sites suivants sont désormais disponibles en tant qu’événements consommables en externe basés sur AEM as a Cloud Service Eventing Platform. Les événements peuvent être traités par Adobe I/O pour interagir avec des processus externes.
* Page publiée
* Page non publiée
* Page supprimée

### Programme d’adoption précoce {#sites-early-adopter}

**Générer des variations**

Tirez profit de GenAI grâce à une nouvelle fonctionnalité d’AEM, [générer des variations](/help/generative-ai/generate-variations.md), maintenant accessible dans Cloud Service. La génération de variations vous permet de générer et d’adapter la création de contenu grâce à l’utilisation de l’IA générative. Contactez votre équipe Adobe en charge des comptes pour en savoir plus sur le programme.

**AEM REST OpenAPI pour la diffusion de fragments de contenu**

L’ [API REST OpenAPI pour la diffusion de fragments de contenu ](/help/headless/aem-rest-openapi-content-fragment-delivery.md) est désormais disponible pour AEM as a Cloud Service.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Fonctionnalité d’accès anticipé dans Dynamic Media {#dm-early-access}

**Sous-titres vidéo générés par l’IA**

Adobe Dynamic Media utilise l’intelligence artificielle pour générer automatiquement des sous-titres pour le contenu vidéo. Cette fonctionnalité est conçue pour améliorer l’accessibilité et l’expérience d’utilisation en fournissant des sous-titres précis en temps réel. L’IA analyse la piste audio de la vidéo pour transcrire la parole et créer des sous-titres, qui peuvent être modifiés pour plus de précision ou de personnalisation. Ces sous-titres permettent de répondre aux exigences d’accessibilité et d’améliorer l’engagement vidéo pour les audiences qui dépendent d’une prise en charge vidéo basée sur le texte ou qui préfèrent ce système.

Pour bénéficier d’un accès anticipé à la prise en charge des sous-titres générés par l’IA sur votre compte Dynamic Media, vous devez [créer et envoyer un cas d’assistance clientèle Adobe ](/help/assets/dynamic-media/video.md##enable-dash).

### Nouvelles fonctionnalités de la vue Assets {#assets-view-new-features}

**Rapports planifiés**

Les rapports peuvent désormais être générés automatiquement dans la vue Assets selon un schéma récurrent ou à une date ultérieure, ce qui réduit l’effort de découverte d’informations basées sur les données.

![Rapports planifiés -](/help/assets/assets/scheduled-reports-tab.png)

### Nouvelles fonctionnalités du hub de contenus {#content-hub-new-features}

**Gestion des droits numériques pour les ressources sous licence**

Les entreprises peuvent désormais augmenter la conformité aux licences et minimiser le risque de partager des ressources avec des conditions de licence en utilisant DRM pour les ressources sous licence pour les utilisateurs de Content Hub, ce qui oblige les utilisateurs à examiner et accepter les conditions de licence avant de pouvoir commencer à télécharger des ressources sous licence. Pour plus d’informations, voir [Gestion des ressources sous licence sur Content Hub](/help/assets/manage-licensed-assets-on-content-hub.md).

![download-multiple-license](/help/assets/assets/download-multiple-license.png)

**Configuration des métadonnées de carte de ressources**

Content Hub vous permet désormais de configurer les champs de métadonnées clés que vous devez afficher sur la carte de ressources dans un maximum de 6 champs. Pour plus d’informations, voir la section Carte de ressources dans [Configuration de Content Hub](/help/assets/configure-content-hub-ui-options.md#asset-card).

![Métadonnées clé sur la carte de ressources](/help/assets/assets/asset-card-key-metadata.png)

**Configuration de la visibilité et du téléchargement des ressources expirées**

Les administrateurs et administratrices peuvent désormais contrôler s’ils ou elles ont besoin que les ressources expirées soient visibles dans le hub de contenus. Si les ressources expirées sont rendues visibles, elles peuvent également définir si les utilisateurs peuvent les télécharger. Pour plus d’informations, reportez-vous à la section Assets expirée dans [Configuration de Content Hub](/help/assets/configure-content-hub-ui-options.md#expired-assets-content-hub).

![Ressources expirées sur le hub de contenus](/help/assets/assets/expired-assets-content-hub.png)

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

### Correctifs {#bug-fixes-cif}

* Correction des tests de l’interface d’utilisation pour qu’ils fonctionnent correctement avec les composants principaux CIF.
* Correction d’un problème en raison duquel le format des URL de catégorie ne fonctionnait pas comme prévu dans l’instance cloud.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Configuration pour contrôler les envois de formulaire {#configuration-submissions}

Pour contrôler les envois de formulaires Coral ou Foundation à des emplacements spécifiques, AEM a introduit une nouvelle configuration : `com.adobe.granite.ui.components.FormRestrict`. Cette configuration se compose de deux champs :

1. **Ajouter des chemins autorisés** : spécifie les chemins où les actions de formulaire sont autorisées.
1. **Restrict Behavior** : détermine le comportement des chemins d’accès restreints (chemins non inclus dans la liste autorisée). Vous pouvez choisir entre deux options :
   * **Popup** (par défaut) : affiche une notification contextuelle.
   * **Empêcher** : bloque l’envoi du formulaire.

>[!NOTE]
>
>Cette configuration n’est pas prise en charge pour tous les formulaires Coral ou Foundation situés sous `/apps`, `/libs`, `/mnt/overlay` et `/mnt/override`.

### Transfert de journaux en libre-service avec option de mise en réseau avancée {#log-forwarding}

Bien que les journaux AEM (y compris Apache/Dispatcher) et CDN puissent être téléchargés à partir de Cloud Manager, de nombreuses entreprises trouvent utile de diffuser ces journaux vers une destination de journalisation préférée. AEM prend désormais en charge le [transfert de journal](/help/implementing/developing/introduction/log-forwarding.md) vers Azure Blob Storage, Datadog, HTTPS, Elasticsearch (et OpenSearch) et Splunk. Les journaux d’AEM peuvent éventuellement être transférés sur des configurations réseau avancées, telles que l’utilisation d’une adresse IP dédiée.

Cette fonctionnalité est configurée par les utilisateurs en libre-service et déployée à l’aide du [pipeline de configuration](/help/operations/config-pipeline.md).

### Redirections d’URL sans pipeline pour les utilisateurs professionnels {#pipeline-free-redirects}

Les redirections côté navigateur sont utiles lorsqu’une page web a été supprimée, déplacée ou dans d’autres scénarios. Avec les [redirections d’URL sans pipeline](/help/implementing/dispatcher/pipeline-free-url-redirects.md), vous pouvez placer un fichier de mappage de réécriture Apache dans un emplacement de publication AEM, où il est automatiquement chargé — sans avoir à valider le fichier dans le contrôle source ni à lancer un pipeline Cloud Manager.

Les options de publication du fichier de réécriture incluent son chargement en tant que ressource, l’utilisation du gestionnaire de cartes de réécriture ACS Commons ou l’interaction avec une interface utilisateur personnalisée.

### Configuration du pipeline pour les RDE {#config-pipeline-rdes}

Les environnements de développement rapide sont un outil puissant pour déployer et tester rapidement le code et la configuration dans un environnement cloud. Les RDE prennent désormais en charge la [synchronisation des fichiers YAML de configuration](/help/implementing/developing/introduction/rapid-development-environments.md#deploy-config-pipeline), y compris les paramètres CDN tels que les règles de filtrage de trafic et les transformations de requête/réponse, ainsi que le transfert de journal et d’autres options de configuration. [Pour plus d’informations, consultez la liste complète](/help/operations/config-pipeline.md) des options de configuration prises en charge.

### Nouveaux profils de produit {#new-product-profiles}

Lorsqu’un nouvel environnement d’AEM est créé, les profils de produit apparaissent automatiquement dans Adobe Admin Console, ce qui permet aux administrateurs d’attribuer l’accès aux solutions et fonctionnalités sous licence.

Les nouveaux environnements incluent désormais un ensemble mis à jour de profils de produit, ce qui les rend compatibles avec les fonctionnalités futures, notamment la génération d’informations d’identification d’API dans Adobe Developer Console. Les environnements existants pourront mettre à jour leurs profils de produit dans une version ultérieure. [En savoir plus](/help/onboarding/aem-cs-team-product-profiles.md).

### Nouvelle AEM Developer Console (version bêta publique) {#aem-developer-console-beta}

Testez une [AEM Developer Console](/help/implementing/developing/introduction/aem-developer-console.md) repensée qui offre une expérience plus interactive pour le débogage du code dans les environnements cloud.

Tout le monde peut accéder à la version Beta publique en cliquant sur le bouton *Nouvelle console disponible* dans la console AEM Developer Console actuelle. Adobe recueille les commentaires. Vous pouvez les envoyer par e-mail à **<aemcs-new-devconsole-ui-beta@adobe.com>**.

![Écran de lots OSGi dans AEM Developer Console](/help/implementing/developing/introduction/assets/osgi-bundles.png)

## [!DNL Experience Manager] Guides {#guides}

Vous trouverez une liste complète des nouvelles fonctionnalités améliorées de la dernière version d’Adobe Experience Manager Guides [ici](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2410-release/2410-0-release/whats-new-2024-10-0).

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
