---
title: Notes de mise à jour de la version 2024.7.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la version 2024.7.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 6194df9d-8c3c-4c7f-be59-099b970a565a
source-git-commit: 7c195e5640f828d2c59dbabd8f29127692788576
workflow-type: tm+mt
source-wordcount: '1626'
ht-degree: 76%

---

# Notes de mise à jour de la version 2024.7.0 d’[!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour de la version 2024.7.0 d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes, telles que 2022 ou 2023.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Pour recevoir chaque mois une notification par e-mail concernant des informations sur les notes de mise à jour d’Experience Cloud, abonnez-vous aux [Mises à jour de produits prioritaires d’Adobe](https://www.adobe.com/subscription/priority-product-update.html).

## Date de publication {#release-date}

La date de publication de la version actuelle (2024.7.0) d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le 25 juillet 2024. La prochaine disponibilité des fonctionnalités (2024.8.0) est prévue pour le 29 août 2024.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

## Vidéo de mise à jour {#release-video}

Consultez la vidéo Vue d’ensemble de la version de juillet 2024 pour obtenir un résumé des fonctionnalités ajoutées dans la version 2024.7.0 :

>[!VIDEO](https://video.tv.adobe.com/v/3431707?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités dans Experience Manager Sites {#new-feature-sites}

### Programme d’adoption précoce {#sites-early-adopter}

**Générer des variations**

Tirez profit de GenAI grâce à une nouvelle fonctionnalité d’AEM, [générer des variations](/help/generative-ai/generate-variations.md), maintenant accessible dans Cloud Service. La génération de variations vous permet de générer et d’adapter la création de contenu grâce à l’utilisation de l’IA générative. Contactez votre équipe Adobe en charge des comptes pour en savoir plus sur le programme.

**Explorer les ressources dans la console de fragments de contenu**

Les auteurs et les autrices de contenu peuvent désormais parcourir, afficher et agir sur les images et d’autres ressources sans avoir à quitter la console de fragments de contenu.

![Explorer des ressources](/help/sites-cloud/administering/content-fragments/assets/cf-console-assets-browse.png)

Vous souhaitez tester la fonctionnalité et partager vos commentaires ? Envoyez un e-mail à aemcs-headless-adopter@adobe.com à partir de votre ID d’e-mail officiel pour en savoir plus le programme d’adoption précoce.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

**Charger les ressources avec le sélecteur de ressources**

Le sélecteur de ressources permet désormais aux auteurs de contenu de charger les ressources finales directement à partir du sélecteur, en les faisant glisser ou en les parcourant depuis le système de fichiers local. Cette fonctionnalité permet de charger les ressources finales dans la gestion des ressources numériques à partir de l’application de votre choix.

### Fonctionnalité d’accès anticipé dans Dynamic Media {#dm-early-access}

**Sous-titres vidéo générés par l’IA**

Les sous-titres vidéo générés par l’IA dans Adobe Dynamic Media utilisent une intelligence artificielle pour générer automatiquement des sous-titres pour le contenu vidéo. Cette fonctionnalité est conçue pour améliorer l’accessibilité et améliorer l’expérience de l’utilisateur en fournissant des sous-titres précis en temps réel. L’IA analyse la piste audio de la vidéo pour transcrire la parole et créer des sous-titres, qui peuvent être modifiés à des fins de précision ou de personnalisation. Ces sous-titres permettent de répondre aux exigences d’accessibilité et d’améliorer l’engagement vidéo pour les audiences qui dépendent ou préfèrent la prise en charge vidéo textuelle.

Pour bénéficier d’un accès anticipé à la prise en charge des sous-titres générés par l’IA sur votre compte Dynamic Media, [ créez et envoyez un cas d’assistance clientèle Adobe ](/help/assets/dynamic-media/video.md##enable-dash).

### Nouvelles fonctionnalités de la vue Assets {#assets-view-new-features}

**Intégration des informations de traçabilité du contenu**

Experience Manager Assets prend désormais en charge les informations de traçabilité du contenu pour les formats d’image pris en charge. Cette fonctionnalité fournit des informations sur la traçabilité de la ressource et sur sa création, y compris si elle a été modifiée à l’aide de GenAI.

![Informations de traçabilité du contenu](/help/assets/assets/content-credentials.png)

**Prévisualisations du contenu du dossier**

Experience Manager Assets affiche désormais des aperçus visuels du contenu du dossier sur la miniature du dossier lors de la navigation ou de la recherche de contenu, ce qui améliore la visibilité des ressources disponibles dans le référentiel AEM Assets.

<!--


**Content Credentials**

Content Credentials feature in Assets view now provides detailed asset provenance data adhered to an asset. This helps to trace the enroute edits along the asset's lifecycle to prevent users from deception through deliberately tempered assets. This ensures content authenticity among users and fosters trust through transparency.

When looking at the asset details, any image with content credentials added, such as those created with GenAI, displays the manifest details in a dedicated panel. If the asset is downloaded, published, or shared, the credentials remain intact with the asset.

![check publish status1](/help/release-notes/assets/content-credentials.png)

-->

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités d’AEM Forms {#forms-new-prerelease-features}

#### Éditeur de règles visuel amélioré pour les formulaires adaptatifs basés sur les composants principaux

Les auteurs de formulaires adaptatifs peuvent utiliser des champs de formulaire répétables et des fonctions d’éditeur de règles visuelles prêtes à l’emploi pour créer une logique métier complexe dans les formulaires sans avoir besoin de personnalisation ni de prise en charge de la part de l’équipe de développement.

### Fonctionnalités d’accès anticipé dans AEM Forms {#forms-new-early-access-features}

Le programme d’accès anticipé d’AEM Forms vous offre une opportunité unique d’accéder de manière exclusive à des innovations de pointe avant toute autre personne et de contribuer à façonner leur développement. Le programme offre l’accès à de multiples innovations.

Les notes de mise à jour répertorient les innovations apportées à la version actuelle. Pour obtenir la liste complète des innovations disponibles dans le cadre du programme d’accès anticipé, voir [Documentation du programme d’accès anticipé d’AEM Forms](/help/forms/early-access-ea-features.md).

#### Créer des formulaires adaptatifs à l’aide de l’éditeur universel

Tirez parti de l’[éditeur universel](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/introduction) d’Adobe Experience Manager pour créer des formulaires adaptatifs à l’aide du glisser-déposer WYSIWYG fourni via le service Edge Delivery pour les expériences d’inscription découplées et couplées. Les auteurs de formulaires adaptatifs peuvent facilement créer et lancer des expériences pour les variantes des formulaires dans les pages web. Cette fonctionnalité leur permet de déterminer les expériences les plus performantes pour les utilisateurs finaux.

>[!IMPORTANT]
>
> Si vous souhaitez rejoindre le programme d’accès anticipé Adobe pour n’importe quelle innovation d’accès anticipé, envoyez simplement un e-mail à partir de votre adresse officielle à [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) pour demander l’accès. Vous pouvez demander l’accès à toutes les innovations ou à certaines d’entre elles.

## Principes de base d’[!DNL Experience Manager] as a [!DNL Cloud Service] {#foundation}

### Purger le contenu sur le réseau CDN avec une clé API en libre-service {#purge-cdn}

La définition de la durée de vie (TTL) à l’aide de l’en-tête de contrôle du cache HTTP est une approche efficace pour équilibrer les performances de diffusion du contenu et l’actualisation du contenu. Cependant, dans les cas où il est essentiel de diffuser du contenu mis à jour immédiatement, il peut être bénéfique de purger directement le cache CDN.

[Découvrez comment](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token) utiliser en libre-service la configuration d’un jeton API de purge à l’aide du pipeline de configuration Cloud Manager, afin que vous puissiez [appeler les API de purge](/help/implementing/dispatcher/cdn-cache-purge.md), avec l’une de ces variations :

* URL unique
* Plusieurs URL à l’aide d’une balise
* Purge complète du cache du réseau CDN

### Configuration en libre-service de X-AEM-Edge-Key pour le réseau CDN géré par la clientèle {#customermanaged-keys}

Auparavant, un ticket d’assistance était nécessaire pour générer la clé X-AEM-Edge-Key requise pour la configuration d’un réseau CDN géré par le client ou la cliente. Ce workflow est désormais en libre-service en déclarant la valeur de clé dans un fichier de configuration déployé à l’aide du pipeline de configuration, supprimant tout délai lors de l’intégration d’un nouvel environnement. [En savoir plus](/help/implementing/dispatcher/cdn-credentials-authentication.md#CDN-HTTP-value).

### Alertes sur les règles de filtrage du trafic {#traffic-filter-rules-alerts}

Les règles de filtrage du trafic, qui incluent les règles WAF (Web Application Firewall) (Pare-feu d’applications web) facultatives, vous permettent de configurer le trafic à bloquer.

Désormais, vous pouvez [vous abonner aux alertes](/help/security/traffic-filter-rules-including-waf.md#traffic-filter-rules-alerts) chaque fois que vos règles de filtre de trafic sont déclenchées. Les notifications par e-mail du centre d’actions vous tiennent au courant lorsque certaines conditions de trafic se produisent afin que vous puissiez prendre les mesures appropriées.

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

### Programme d’adoption précoce des notifications du centre d’actions liées à l’intégrité du contenu {#actions-center-notifications}

Le [centre d’actions](/help/operations/actions-center.md) envoie des notifications par e-mail lorsque des incidents importants se produisent ou si quelque chose est observée sur votre code ou configuration où vous devez prendre des mesures proactives. Adobe a désormais introduit plusieurs nouveaux types de notifications associées à l’intégrité de votre contenu. Cette fonctionnalité est disponible par le biais d’un programme d’adoption précoce. Pour participer, contactez l’assistance clientèle Adobe.

#### Les pages contiennent un grand nombre de nœuds {#page-nodes}

Un grand nombre de nœuds peut dégrader les performances de rendu et réduire les temps de chargement des pages. Recevez une notification proactive par l’intermédiaire du centre d’actions lorsqu’un grand nombre de nœuds est détecté sur une page. Cela vous permet ainsi de prendre les mesures nécessaires pour réduire le nombre total de nœuds dans une page.

#### Grand nombre d’instances de workflows en cours d’exécution {#running-workflows}

Les performances du moteur de workflow sont affectées lorsqu’un grand nombre de workflows sont en cours d’exécution dans l’environnement de création. Vous recevez une notification proactive via le centre d’actions lorsqu’un grand nombre d’instances de workflow en cours d’exécution sont détectées. Ce processus vous permet de configurer un traitement de purge afin d’arrêter les workflows inutiles en cours d’exécution.

#### Utilisateurs et utilisatrices ajoutés directement aux groupes personnalisés {#users-customgroups}

Vous recevez une notification proactive par le biais du centre d’actions lorsque des utilisateurs et utilisatrices sont ajoutés directement à des groupes personnalisés. Ce processus vous permet de suivre les bonnes pratiques IMS en ajoutant des utilisateurs et utilisatrices aux groupes IMS appropriés, puis en incluant ces groupes IMS en tant que membres des groupes AEM.

#### Contenu JCR manquant {#jcr-content}

Le centre d’actions vous avertit de manière proactive lorsque le contenu JCR manquant est détecté. Cette approche permet d’ajouter le contenu manquant et d’éviter l’échec de certaines fonctionnalités d’AEM Assets.

#### Workflows terminés non purgés {#workflows}

Le centre d’actions vous avertit de manière proactive que les workflows terminés depuis plus de 90 jours n’ont pas été purgés. Cette approche permet d’améliorer les performances de votre moteur de workflow en réduisant le nombre d’instances de workflow.

#### Ressource Sling manquante {#sling-resource}

Le centre d’actions vous avertit de manière proactive lorsqu’une ressource Sling manquante est détectée. Cette approche permet d’ajouter la ressource manquante et d’éviter l’échec de certaines fonctionnalités d’AEM Assets.

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
