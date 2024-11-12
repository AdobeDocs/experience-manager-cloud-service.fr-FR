---
title: Notes de mise à jour de la version 2024.8.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la version 2024.8.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
feature: Release Information
role: Admin
exl-id: dd1d4b8f-8331-4e97-a754-37e720974db6
source-git-commit: dbe4cd619f4dc680e6fc4826f6a4fea92bab9707
workflow-type: tm+mt
source-wordcount: '1173'
ht-degree: 100%

---

# Notes de mise à jour de la version 2024.8.0 d’[!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour de la version 2024.8.0 d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes, telles que 2022 ou 2023.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Pour recevoir chaque mois une notification par e-mail concernant des informations sur les notes de mise à jour d’Experience Cloud, abonnez-vous aux [Mises à jour de produits prioritaires d’Adobe](https://www.adobe.com/subscription/priority-product-update.html).

## Date de publication {#release-date}

La date de publication de la version actuelle (2024.8.0) d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le 29 août 2024. La prochaine disponibilité des fonctionnalités (2024.9.0) est prévue pour le 26 septembre 2024.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

## Vidéo de mise à jour {#release-video}

Consultez la vidéo Vue d’ensemble de la version d’août 2024 pour un résumé des fonctionnalités ajoutées dans la version 2024.8.0 :

>[!VIDEO](https://video.tv.adobe.com/v/3433381?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités dans Experience Manager Sites {#new-feature-sites}

**Création AEM pour Edge Delivery Services**

La fonctionnalité existante [Héritage](/help/sites-cloud/authoring/universal-editor/inheritance.md) de Sites est désormais prise en charge, notamment ce qui suit :

* [AEM Launches](/help/sites-cloud/authoring/launches/overview.md)
* [MSM](/help/sites-cloud/administering/msm/overview.md) au niveau de la page

En outre, les fonctionnalités de gestion de page suivantes sont désormais prises en charge :

* Les [balises AEM](/help/sites-cloud/authoring/sites-console/tags.md) peuvent être exportées en tant que [taxonomie](/help/edge/wysiwyg-authoring/taxonomy.md) vers Edge Delivery Services.
* Les [modèles](/help/sites-cloud/authoring/universal-editor/templates.md) pour Edge Delivery Services seront bientôt disponibles.

### Programme d’adoption précoce {#sites-early-adopter}

**Générer des variations**

Tirez profit de GenAI grâce à une nouvelle fonctionnalité d’AEM, [générer des variations](/help/generative-ai/generate-variations.md), maintenant accessible dans Cloud Service. La génération de variations vous permet de générer et d’adapter la création de contenu grâce à l’utilisation de l’IA générative. Contactez votre équipe Adobe en charge des comptes pour en savoir plus sur le programme.


## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de la vue Assets {#assets-view-new-features}

**Génération d’images d’Adobe Firefly mise à jour**

Assets as a Cloud Service utilise désormais le dernier widget de Firefly qui vous permet de générer des images dans différents styles à l’aide d’Adobe Firefly. En définissant son style, sa composition, ses dimensions, etc., à l’aide de l’éditeur Firefly intégré, vous pouvez rapidement créer et enregistrer les ressources dont vous avez besoin directement dans le référentiel AEM Assets pour une utilisation immédiate.

![Génération d’images d’Adobe Firefly](/help/assets/assets/bugatti-type-57.png)

**Prise en charge des fichiers PSB**

Assets as a Cloud Service prend désormais en charge les documents Photoshop volumineux (fichiers PSB) en plus de la prise en charge des fichiers PSD existants.

### Nouvelles améliorations dans le hub de contenus {#content-hub-new-enhancements}

* Amélioration de la gestion des noms de fichier longs, extension facile du nom complet via une info-bulle.
* Amélioration des miniatures pour mieux adapter le format du contenu et couvrir une plus grande zone de contenu.
* Expérience de miniature personnalisée à partir d’AEM prise en charge avec le hub de contenus.
* Améliorations de la recherche de couleurs.
* Améliorations apportées à l’expérience d’enregistrement des configurations.
* Amélioration de la page d’informations des collections pour refléter le nom du créateur ou de la créatrice.


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

* **Génération de formulaires adaptatifs** : créez facilement des formulaires complets avec des invites d’IA générative. Notre IA générative génère automatiquement des formulaires conviviaux qui réduisent les abandons et personnalisent l’expérience.

* **Génération de panneau pour Forms** : générez des sections de formulaire adaptées à des besoins spécifiques de collecte de données. Par exemple, générez des sections pour collecter des informations sur le paiement, les préférences des clientes et clients ou les détails du voyage.

* **Modification des mises en page de formulaire** : testez différentes mises en page et conceptions à l’aide des invites d’IA générative. Testez différentes mises en page, telles que l’assistant ou les onglets, afin de trouver ce qui convient le mieux pour votre formulaire. Utilisez les invites d’IA générative afin d’optimiser vos formulaires pour la réactivité mobile et de créer des formulaires attrayants pour les utilisateurs et utilisatrices.

* **Configurer l’action d’envoi** : utilisez les invites d’IA générative pour configurer facilement une action d’envoi pour votre formulaire. Faites votre choix parmi une bibliothèque d’actions d’envoi préconfigurées ou parmi une liste d’actions d’envoi personnalisées, créées et déployées par votre propre équipe de développement.

>[!IMPORTANT]
>
> Si vous souhaitez rejoindre le programme d’accès anticipé pour toute innovation, envoyez simplement un e-mail depuis votre adresse officielle à [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) avec la liste des fonctionnalités qui vous intéressent.


## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Programmes d’adoption précoce liés à la diffusion de contenu {#foundation-early-adopter}

Envoyez un e-mail à **<aemcs-cdn-config-adopter@adobe.com>** en indiquant le programme d’adoption précoce qui vous intéresse parmi les choix ci-dessous.

#### Authentification de base sur le réseau de diffusion de contenu (programme d’adoption précoce) {#basicauth-cdn}

Protégez certaines ressources de contenu en affichant une boîte de dialogue d’authentification de base nécessitant un nom d’utilisateur ou d’utilisatrice et un mot de passe. Cette fonctionnalité cible principalement les cas d’utilisation de l’authentification légère, comme les parties prenantes de l’entreprise qui examinent le contenu, plutôt que de servir de solution complète pour les droits d’accès des utilisateurs et utilisatrices finaux. La liste des noms d’utilisateur ou d’utilisatrices et des mots de passe dans Git gérée via un fichier de configuration déployé via le pipeline de configuration, avec une référence aux variables d’environnement Cloud Manager de type secret. [En savoir plus](/help/implementing/dispatcher/cdn-credentials-authentication.md#basic-auth).

#### Redirections côté client (programme d’adoption précoce) {#client-side-redirects-early-adopter}

Configurez des redirections côté client 301/302 dans le contrôle de code source et déployez-les sur le réseau CDN. [En savoir plus](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors).<!-- and join the early adopter program by emailing **<aemcs-cdn-config-adopter@adobe.com>**. --> Notez qu’il existe déjà plusieurs autres fonctionnalités liées à la [configuration du réseau CDN](/help/implementing/dispatcher/cdn-configuring-traffic.md), y compris les transformations de requêtes et de réponses, et le routage du trafic vers les sites hors AEM.

#### Les utilisateurs et utilisatrices professionnels peuvent déclarer des redirections en dehors de Git (programme d’adoption précoce) {#apache-rewritemaps-early-adopter}

Comme pour AEM 6.5, Apache/le Dispatcher ingère des mappages de réécriture placés à un emplacement spécifique dans le référentiel de publication et les charge, sans nécessiter d’exécution de pipeline de niveau web. Cette approche permet aux utilisateurs et utilisatrices professionnels de déclarer des redirections à l’aide d’une feuille de calcul ou d’une interface d’utilisation, comme le gestionnaire de mappage de redirection ACS Commons ou une application personnalisée. <!-- Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information. -->

#### Edge Side Includes (ESI) pour le chargement de contenu dynamique (programme d’adoption précoce) {#esi-early-adopter}

Le réseau CDN géré par Adobe prend désormais en charge [Edge Side Includes (ESI)](/help/implementing/dispatcher/edge-side-includes.md), un langage de balisage pour l’assemblage de contenu web dynamique au niveau Edge. En incluant des extraits de code ESI, vous pouvez mettre en cache la page HTML globale sur le réseau CDN avec des durées de vie (TTL) plus élevées, tout en récupérant plus fréquemment de l’origine les sections plus petites qui nécessitent des mises à jour à un rythme supérieur (durées de vie moins élevées). <!--Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information.-->


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
