---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: 1e5a32625377cb564c859a6fdaf1ecef6ebebe9e
workflow-type: tm+mt
source-wordcount: '1865'
ht-degree: 45%

---

# Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour techniques de la version actuelle (la plus récente) d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes, telles que 2022 ou 2023.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de la version actuelle (2024.6.0) d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le vendredi 27 juin 2024. La prochaine disponibilité des fonctionnalités (2024.7.0) est prévue pour le vendredi 25 juillet 2024.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

<!--  ## Release Video {#release-video}

Have a look at the June 2024 Release Overview video for a summary of the features added in the 2024.6.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3429503?quality=12)

-->

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelle fonctionnalité dans Experience Manager Sites {#new-feature-sites}

**Service de données de surveillance d’utilisation réelle (RUM)** {#real-use-monitoring}

La variable [Service de données de surveillance d’utilisation réelle (RUM)](https://git.corp.adobe.com/AdobeDocs/experience-manager-cloud-service.en/blob/shwetad-patch-1/help/implementing/cloud-manager/content-requests.md#real-user-monitoring-for-aem-as-a-cloud-service) est désormais disponible en général, ce qui permet la collecte de données côté client pour AEM as a Cloud Service. Ce service reflète plus précisément les interactions des utilisateurs, ce qui garantit une mesure fiable de l’engagement du site web. Il offre aux clients des informations avancées sur le trafic et les performances de leurs pages, ce qui leur offre une occasion précieuse de comprendre et d’améliorer les performances de ces pages.

### Programme d’adoption précoce {#sites-early-adopter}

**Générer des variations**

Tirez profit de GenAI grâce à une nouvelle fonctionnalité d’AEM, [générer des variations](/help/generative-ai/generate-variations.md), maintenant accessible dans Cloud Service. La génération de variations vous permet de générer et d’adapter la création de contenu grâce à l’utilisation de l’IA générative. Contactez votre équipe Adobe en charge des comptes pour en savoir plus sur le programme.

**Explorer les ressources dans la console de fragments de contenu**

Les auteurs et les autrices de contenu peuvent désormais parcourir, afficher et agir sur les images et d’autres ressources sans avoir à quitter la console de fragments de contenu.

![Explorer des ressources](/help/sites-cloud/administering/content-fragments/assets/cf-console-assets-browse.png)

Vous souhaitez tester la fonctionnalité et partager vos commentaires ? Envoyez un e-mail à aemcs-headless-adopter@adobe.com à partir de votre ID d’e-mail officiel pour en savoir plus le programme d’adoption précoce.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de Experience Manager Assets {#new-features-assets}



**Content Hub**

Content Hub est disponible dans le cadre de Experience Manager Assets as a Cloud Service pour démocratiser l’accès au contenu de marque pour les organisations et leurs partenaires commerciaux. Avec Content Hub, vous pouvez facilement rechercher et distribuer des ressources, les réutiliser et créer de nouvelles variations de marque et accélérer l’activation à grande échelle.

![Interface utilisateur de Content Hub](/help/release-notes/assets/content-hub-ui.png)

**Dynamic Media avec fonctionnalités OpenAPI**

Les fonctionnalités Dynamic Media avec OpenAPI étendent la gestion des actifs numériques sur les applications Adobe et tierces, ce qui permet d’accéder à sur les ressources numériques approuvées par la marque, dans n’importe quel canal, via le sélecteur de ressources ou la pile OpenAPI. Principes clés : aucune copie binaire, les ressources ne sont optimisées et transformées à la périphérie pour des performances rapides, une diffusion publique ou sécurisée des ressources.

![Nouveau diagramme de flux de données Dynamic Media](/help/assets/assets/dm-openapi-dfd.png)


### Nouvelles fonctionnalités de la vue Assets {#assets-view-new-features}

**D’autres options sont disponibles dans le tableau de bord Assets Insights**

Le décompte des ressources par type et taille de ressource est désormais disponible dans le tableau de bord Statistiques sur Assets . Ces options fournissent des données en temps réel dans votre environnement de vue Assets. Elles détaillent le nombre et le pourcentage de ressources par tranche de taille et type de ressource.

<!--


**Content Credentials**

Content Credentials feature in Assets view now provides detailed asset provenance data adhered to an asset. This helps to trace the enroute edits along the asset's lifecycle to prevent users from deception through deliberately tempered assets. This ensures content authenticity among users and fosters trust through transparency.

When looking at the asset details, any image with content credentials added, such as those created with GenAI, displays the manifest details in a dedicated panel. If the asset is downloaded, published, or shared, the credentials remain intact with the asset.

![check publish status1](/help/release-notes/assets/content-credentials.png)

-->

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Nouvelles fonctionnalités d’AEM Forms {#forms-new-prerelease-features}

#### Éditeur de règles visuel amélioré pour les formulaires adaptatifs basés sur les composants principaux

Cette version apporte une mise à niveau importante à l’éditeur de règles visuel pour les formulaires adaptatifs basés sur les composants principaux. Vous pouvez maintenant effectuer les tâches suivantes :

* Créez des règles dans l’éditeur de règles visuel pour [remplacer les messages de succès/d’échec d’envoi de formulaire par défaut ;](/help/forms/create-and-use-custom-functions.md#use-case-override-form-submission-success-and-error-handlers).

* Dans l’éditeur de règles des formulaires adaptatifs, ajout de la possibilité de [sélectionner différents types de champs pour l’opération WHEN (lorsque)](/help/forms/rule-editor-core-components.md#allowed-multiple-fields-in-when).

* FORMS-12052 : un auteur ou une autrice de formulaire peut désormais appliquer des fonctions personnalisées pour [prétraiter les données avant l’envoi](/help/forms/create-and-use-custom-functions.md#use-case-submit-altered-data-to-the-server).

* Utilisez la fonctionnalité [**Enregistrer en tant que brouillon**](/help/forms/save-core-component-based-form-as-draft.md) pour enregistrer des formulaires partiellement remplis en vue d’un envoi ultérieur. Cette fonctionnalité est utile dans les cas où les utilisateurs doivent interrompre le remplissage d’un formulaire et y revenir ultérieurement.

### Fonctionnalités d’accès anticipé dans AEM Forms {#forms-new-early-access-features}

Le programme d’accès anticipé d’AEM Forms vous offre une occasion unique d’accéder de manière exclusive à des innovations de pointe avant n’importe qui d’autre et d’aider à façonner leur développement. Le programme offre l’accès à de multiples innovations.

Cette note de mise à jour répertorie les innovations proposées dans la version actuelle. Pour obtenir la liste complète des innovations disponibles dans le cadre du programme Accès anticipé, voir [Documentation du programme d’accès anticipé AEM Forms](/help/forms/early-access-ea-features.md).

#### Amélioration des méthodes de protection des robots

AEM Forms a amélioré ses fonctionnalités de sécurité en ajoutant la prise en charge de deux solutions Captcha populaires : Cloudflare Turnstile et hCaptcha. Cette fonctionnalité complète le reCAPTCHA Google existant, offrant ainsi aux utilisateurs des options supplémentaires. Elle offre une plus grande flexibilité pour protéger leurs formulaires des envois de robots et de spam.

* **Cloudflare Turnstile**: ce CAPTCHA sans friction vérifie les utilisateurs par le biais d’un simple défi qui ne nécessite pas d’interaction explicite. Il s’intègre de manière transparente à vos formulaires, améliorant ainsi l’expérience client.
* **hCaptcha** : ce Captcha axé sur la confidentialité offre une alternative conviviale qui met l’accent sur la confidentialité des données. Il vise à trouver un équilibre entre la sécurité et l’expérience client.
* **Google reCAPTCHA** : AEM Forms continue à prendre en charge reCAPTCHA v2 et reCAPTCHA Enterprise, offrant ainsi une solution fiable et bien établie.

En proposant plusieurs options de Captcha, AEM Forms vous permet de sélectionner la solution qui correspond le mieux à vos besoins.

Prêt à intégrer l’une de ces solutions CAPTCHA à votre Forms adaptatif ? La documentation d’Adobe fournit des instructions détaillées pour chacun d’eux : [Cloudflare Turnstile](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/integrate-adaptive-forms-turnstile-core-components), [Captcha](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/integrate-adaptive-forms-hcaptcha-core-components), et [Google reCAPTCHA](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/captcha-adaptive-forms-core-components).


### Service Forms

Le service Forms génère des formulaires PDF interactifs pour la capture de données. Il peut également être utilisé pour importer ou exporter des données vers et à partir d’un formulaire PDF interactif existant et valider les données envoyées. Voici une répartition de ses fonctionnalités :

* **Rendu de Forms** : générez un formulaire PDF interactif à partir d’un modèle créé à l’aide d’AEM Forms Designer et éventuellement de données XML. Cette fonctionnalité produit un formulaire de PDF à remplir éventuellement prérempli avec des données.
* **Extraction et import des données** : importez des données dans un formulaire PDF existant et extrayez des données d’un formulaire PDF rempli. Les formats de données XDP et XML sont pris en charge, et l’import dans des formulaires PDF non XFA (également appelés AcroForms) prend également en charge les données FDF et XFDF.
* **Validation des données** : validez les données envoyées, au format XDP ou XML, par rapport à un modèle créé à l’aide d’AEM Forms Designer.

>[!IMPORTANT]
>
> Si vous souhaitez rejoindre le Programme d’accès anticipé de l’Adobe pour toute innovation en matière d’accès anticipé, envoyez simplement un e-mail de votre adresse officielle à [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) pour demander l’accès. Vous pouvez demander l’accès à toutes les innovations ou à certaines d’entre elles.


## Principes de base d’[!DNL Experience Manager] as a [!DNL Cloud Service] {#foundation}

### Programme d’adoption précoce du centre d’actions liées à la santé du contenu Notifications {#actions-center-notifications}

[Centre d’actions](/help/operations/actions-center.md) envoie des notifications par e-mail lorsque des incidents importants se produisent, ou si un élément est remarqué concernant votre code ou votre configuration et que vous devez prendre des mesures proactives. Adobe a désormais introduit plusieurs nouveaux types de notifications associées à l’intégrité de votre contenu. Cette fonctionnalité est disponible par le biais d’un programme d’adoption précoce. Pour participer, contactez l’assistance clientèle Adobe.

#### Les pages contiennent un grand nombre de noeuds {#page-nodes}

Un grand nombre de noeuds peut dégrader les performances de rendu et réduire les temps de chargement des pages. Recevez une notification proactive par l’intermédiaire du centre d’actions lorsqu’un grand nombre de noeuds est détecté sur une page, ce qui vous permet de prendre les mesures nécessaires pour réduire le nombre total de noeuds dans une page.

#### Grand nombre d’instances de workflow en cours d’exécution {#running-workflows}

Les performances du moteur de workflow sont affectées lorsqu’un grand nombre de workflows sont en cours d’exécution dans l’environnement de création. Vous recevez une notification proactive via le centre d’actions lorsqu’un grand nombre d’instances de workflow en cours d’exécution sont détectées. Ce processus vous permet de configurer une tâche de purge afin d’arrêter les workflows inutiles en cours d’exécution.

#### Utilisateurs ajoutés directement aux groupes personnalisés {#users-customgroups}

Vous recevez une notification proactive par le biais d’Actions Center lorsque des utilisateurs sont ajoutés directement à des groupes personnalisés. Ce processus vous permet de suivre les bonnes pratiques IMS en ajoutant des utilisateurs aux groupes IMS appropriés, puis en incluant ces groupes IMS en tant que membres des groupes AEM.

#### Contenu JCR manquant {#jcr-content}

Actions Center vous avertit de manière proactive lorsque le contenu JCR manquant est détecté. Cette méthode permet d&#39;ajouter le contenu manquant et d&#39;éviter l&#39;échec de certaines fonctionnalités d&#39;AEM Assets.

#### Workflows terminés non purgés {#workflows}

Le Centre d’actions vous avertit de manière proactive que les workflows terminés depuis plus de 90 jours n’ont pas été purgés. Cette approche permet d’améliorer les performances de votre moteur de workflow en réduisant le nombre d’instances de workflow.

#### Ressource Sling manquante {#sling-resource}

Actions Center vous avertit de manière proactive lorsqu’une ressource Sling manquante est détectée. Cette méthode permet d&#39;ajouter la ressource manquante et d&#39;éviter l&#39;échec de certaines fonctionnalités d&#39;AEM Assets.

### Programmes d&#39;adoption précoce liés à la diffusion de contenu {#foundation-early-adopter}

Envoyez un e-mail à **<aemcs-cdn-config-adopter@adobe.com>**, indiquant le programme d’adoption précoce qui vous intéresse parmi les choix ci-dessous.

#### Authentification de base sur le réseau de diffusion de contenu (programme des premiers adopteurs) {#basicauth-cdn}

Protect de certaines ressources de contenu en affichant une boîte de dialogue d’authentification de base nécessitant un nom d’utilisateur et un mot de passe. Cette fonctionnalité cible principalement les cas d’utilisation de l’authentification légère, comme les parties prenantes de l’entreprise qui examinent le contenu, plutôt que de servir de solution complète pour les droits d’accès des utilisateurs finaux. La liste des noms d’utilisateur et des mots de passe dans Git géré via un fichier de configuration déployé via le pipeline de configuration, avec une référence aux variables d’environnement Cloud Manager de type secret. [En savoir plus](/help/implementing/dispatcher/cdn-credentials-authentication.md#basic-auth).

#### Purger le contenu sur le réseau de diffusion de contenu avec une clé API en libre-service (programme Adopteur anticipé) {#purge-cdn}

Enregistrez une clé API de purge de réseau CDN en libre-service et utilisez-la pour invalider le contenu au niveau du réseau CDN, soit globalement, soit pour une ou plusieurs ressources. [En savoir plus](/help/implementing/dispatcher/cdn-cache-purge.md).

<!-- Email **<aemcs-cdn-config-adopter@adobe.com>** with a request to be an early adopter. -->

#### Création en libre-service de la clé X-AEM-Edge pour le réseau de diffusion de contenu géré par le client (BYOCDN) (programme des Adopteurs anticipés) {#byocdn-keys}

Auparavant, un ticket d’assistance était nécessaire pour générer la clé X-AEM-Edge-Key requise pour la configuration d’un réseau CDN géré par le client ou la cliente. Ce résultat peut désormais être obtenu en libre-service via un fichier de configuration déployé à l’aide du pipeline de configuration, supprimant tout délai lors de l’intégration d’un nouvel environnement. [En savoir plus](/help/implementing/dispatcher/cdn-credentials-authentication.md#CDN-HTTP-value).

<!-- Email **<aemcs-cdn-config-adopter@adobe.com>** with a request to be an early adopter. -->

#### Redirections côté client (programme Adopteur anticipé) {#client-side-redirects-early-adopter}

Configurez des redirections côté client 301/302 dans le contrôle de code source et déployez-les sur le réseau CDN. [En savoir plus](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors).<!-- and join the early adopter program by emailing **<aemcs-cdn-config-adopter@adobe.com>**. --> Notez qu’il existe déjà plusieurs autres fonctionnalités liées à la [configuration du réseau CDN](/help/implementing/dispatcher/cdn-configuring-traffic.md), y compris les transformations de requêtes et de réponses, et le routage du trafic vers les sites hors AEM.

#### Alertes relatives aux règles de filtrage du trafic (programme d’adoption précoce) {#traffic-filter-rules-alerts-early-adopter}

Les [Règles de filtrage du trafic](/help/security/traffic-filter-rules-including-waf.md) récemment publiées qui incluent les règles WAF (Web Application Firewall) sous licence optionnelle vous permettent de configurer le trafic qui doit être autorisé ou refusé.

Rejoignez le programme d’adoption précoce pour pouvoir recevoir une alerte chaque fois que vos règles de filtrage du trafic sont déclenchées. Les notifications électroniques du centre d’actions vous tiennent informé lorsque certaines conditions de trafic se produisent afin que vous puissiez prendre les mesures appropriées.

#### Les Utilisateurs De L’Entreprise Peuvent Déclarer Les Redirections En Dehors De Git (Programme Des Adopteurs Anticipés) {#apache-rewritemaps-early-adopter}

Comme pour AEM 6.5, Apache/dispatcher ingère des mappages de réécriture placés à un emplacement spécifique dans le référentiel de publication, puis les charge, sans nécessiter d’exécution de pipeline de niveau web. Cette approche permet aux utilisateurs professionnels de déclarer des redirections à l’aide d’une feuille de calcul ou d’une interface utilisateur, comme le gestionnaire de cartes de redirection ACS Commons ou une application personnalisée. <!-- Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information. -->

#### Edge Side Includes (ESI) pour le chargement de contenu dynamique (programme d’adoption précoce) {#esi-early-adopter}

Le réseau CDN géré par Adobe prend désormais en charge [Edge Side Includes (ESI)](/help/implementing/dispatcher/edge-side-includes.md), un langage de balisage pour l’assemblage de contenu web dynamique au niveau Edge. En incluant des extraits de code ESI, vous pouvez mettre en cache la page HTML globale sur le réseau CDN avec des durées de vie (TTL) plus élevées, tout en récupérant plus fréquemment de l’origine les sections plus petites qui nécessitent des mises à jour à un rythme supérieur (durées de vie moins élevées). <!--Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information.-->

## [!DNL Experience Manager] Guides {#guides}

Vous trouverez une liste complète des nouvelles fonctionnalités améliorées de la dernière version d’Adobe Experience Manager Guides [ici](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2406-release/whats-new-2024-06-0).

## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici](/help/implementing/cloud-manager/release-notes/current.md).

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [ici](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).

## Notes de mise à jour dʼExperience Cloud {#experience-cloud}

Vous trouverez des informations sur les versions d’autres applications Experience Cloud [ici](https://experienceleague.adobe.com/fr/docs/release-notes/experience-cloud/current).
Pour recevoir chaque mois une notification par e-mail concernant des informations sur les notes de mise à jour d’Experience Cloud, abonnez-vous aux [Mises à jour de produits prioritaires d’Adobe](https://www.adobe.com/subscription/priority-product-update.html).
