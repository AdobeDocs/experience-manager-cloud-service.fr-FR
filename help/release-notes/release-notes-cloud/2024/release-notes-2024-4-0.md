---
title: Notes de mise à jour de la version 2024.4.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la version 2024.4.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 153a3172-676f-4434-94d4-12fab8e17734
feature: Release Information
role: Admin
source-git-commit: 8be0a9894bb5b3a138c0ec40a437d6c8e4bc7e25
workflow-type: tm+mt
source-wordcount: '2699'
ht-degree: 95%

---

# Notes de mise à jour de la version 2024.4.0 d’[!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour de la version 2024.4.0 d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes, telles que 2021 ou 2022.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de la version actuelle (2024.4.0) d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le 25 avril 2024. La prochaine disponibilité des fonctionnalités (2024.5.0) est prévue pour le 30 mai 2024.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

## Vidéo de mise à jour {#release-video}

Consultez la vidéo de vue d’ensemble de la version d’avril 2024 pour obtenir un résumé des fonctionnalités ajoutées dans la version 2024.4.0 :

>[!VIDEO](https://video.tv.adobe.com/v/3446306?quality=12&captions=fre_fr)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Programme d’adoption précoce {#sites-early-adopter}

**Générer des variations**

Tirez profit de GenAI grâce à une nouvelle fonctionnalité d’AEM, [générer des variations](/help/generative-ai/generate-variations.md), maintenant accessible dans Cloud Service. La génération de variations vous permet de générer et d’adapter la création de contenu grâce à l’utilisation de l’IA générative. Contactez votre équipe Adobe en charge des comptes pour en savoir plus sur le programme.

**Explorer les ressources dans la console de fragments de contenu**

Les auteurs et les autrices de contenu peuvent désormais parcourir, afficher et agir sur les images et d’autres ressources sans avoir à quitter la console de fragments de contenu.

![Explorer des ressources](/help/sites-cloud/administering/content-fragments/assets/cf-console-assets-browse.png)

Vous souhaitez tester la fonctionnalité et partager vos commentaires ? Envoyez un e-mail à aemcs-headless-adopter@adobe.com à partir de votre ID d’e-mail officiel pour en savoir plus le programme d’adoption précoce.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de la vue Assets {#assets-view-new-features}


**Recherche contextuelle**

Désormais, vous pouvez également [rechercher des ressources disponibles dans le référentiel en définissant des invites de texte](/help/assets/search-assets-view.md#contextual-search). Experience Manager Assets transforme automatiquement ces invites de texte en filtres de recherche et affiche les résultats de la recherche. Vous pouvez afficher et modifier des filtres automatiques à l’aide du volet Filtres pour affiner davantage les résultats de la recherche.

![Recherche contextuelle](/help/assets/assets/contextual-search-text-prompt1.png)

**Actions rapides sur les vidéos express**

Experience Manager Assets comprend désormais des [outils d’édition vidéo simples et intuitifs optimisés par Adobe Express](/help/assets/edit-videos-assets-view.md) pour augmenter la réutilisation du contenu et accélérer sa vitesse de diffusion. Les options de retouche incluent le rognage, le recadrage, le redimensionnement d’une vidéo, ainsi que la conversion d’un fichier MP4 en fichier GIF.

![Recadrage vidéo avec Adobe Express](/help/assets/assets/adobe-express-crop-video.png)

**Rendus dynamiques**

Vous pouvez désormais [afficher et télécharger des rendus dynamiques (recadrages intelligents inclus)](/help/assets/renditions.md) dans Experience Manager Assets. Les rendus dynamiques sont des versions personnalisées des ressources d’image créées en temps réel pour répondre à des besoins spécifiques, tels que le redimensionnement des images en fonction de la résolution de l’appareil ou le recadrage pour adapter différentes proportions. Ces rendus permettent aux entreprises de proposer des expériences personnalisées et optimisées pour des besoins d’audience divers.

![Rendus dynamiques](/help/assets/assets/preset_smart_crop.png)

**Changement statique du nom des ressources et des dossiers**

Experience Manager Assets offre désormais une expérience client simplifiée [en permettant de renommer une ressource ou un dossier en un seul clic](/help/assets/manage-organize-assets-view.md).

**Affecter un formulaire de métadonnées à plusieurs dossiers ou le supprimer de ceux-ci**

Vous pouvez désormais [affecter un formulaire de métadonnées à plusieurs dossiers ou le supprimer de ceux-ci](/help/assets/metadata-assets-view.md#assign-metadata-form-to-a-folder).

### Nouvelles fonctionnalités de la vue d’administration {#admin-view-new-features}

**Configuration du partage de lien**

Une nouvelle expérience client améliorée pour la [création de partages de lien](/help/assets/share-assets.md) ainsi qu’un tout nouvel ensemble de configurations qui permet aux administrateurs et administratrices de personnaliser le comportement par défaut de cette fonctionnalité pour vos utilisateurs et utilisatrices.

![Configuration du partage de lien](/help/assets/assets/config-email-service.png)



## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Nouvelles fonctionnalités d’AEM Forms {#forms-new-features}

* **Éditeur de règles visuel amélioré pour les formulaires adaptatifs basés sur les composants principaux** : cette version introduit une mise à niveau significative de l’éditeur de règles visuel pour les formulaires adaptatifs basés sur les composants principaux. Cette version introduit une mise à niveau significative de l’éditeur de règles visuel pour les formulaires adaptatifs basés sur les composants principaux. Cette mise à jour porte sur la rationalisation des interactions avec des fonctions personnalisées, ce qui vous permet de créer des formulaires plus robustes et efficaces.

  Vous pouvez désormais rationaliser les interactions de fonctions personnalisées en :

   * [utilisant de nouvelles annotations pour fournir des définitions de fonction plus claires](/help/forms/create-and-use-custom-functions.md#supported-javascript-annotations-for-custom-function) ;
   * [utilisant des mécanismes de mise en cache pour les fonctions personnalisées, ce qui accélère les performances du formulaire](/help/forms/create-and-use-custom-functions.md#caching-support-for-custom-function) ;
   * [utilisant en toute transparence des objets globaux dans des fonctions personnalisées](/help/forms/create-and-use-custom-functions.md#field-and-global-scope-objects-in-custom-functions) ;
   * [définissant et en utilisant des paramètres facultatifs dans des fonctions personnalisées](/help/forms/create-and-use-custom-functions.md#parameter).

  Cette mise à jour introduit également les améliorations suivantes aux fonctionnalités de l’éditeur de règles. Vous pouvez :

   * implémenter une logique [« when-then-else »](/help/forms/rule-editor-core-components.md#when) (lorsque-alors-sinon) puissante pour l’exécution conditionnelle ;
   * tirer profit de fonctionnalités JavaScript modernes telles que les fonctions let et arrow (prise en charge d’ES10) ;
   * valider ou réinitialiser non seulement des champs, mais également des panneaux et des formulaires entiers, en optimisant le contrôle sur les interactions des utilisateurs et utilisatrices.

  Ces améliorations offrent une expérience plus intuitive et plus puissante pour l’élaboration de règles et de fonctions personnalisées dans l’éditeur de règles visuel.

* **[Créer plusieurs versions d’un formulaire adaptatif](/help/forms/add-comments-annotations-versioning-adaptive-form-core-components.md)** : vous pouvez désormais gérer facilement les variations de formulaires existants. Cela simplifie la gestion de versions et facilite la comparaison pour l’optimisation des formulaires, le tout au sein d’un seul workflow simplifié.

* **[Comparer des formulaires adaptatifs](/help/forms/compare-forms.md)** : vous pouvez désormais comparer facilement deux formulaires pour identifier les différences entre eux. Cela facilite la collaboration en permettant aux personnes membres de l’équipe de comparer les révisions et de discuter efficacement des changements.

* **Améliorations de l’accessibilité pour le composant Signature tactile** : cette mise à jour introduit des améliorations importantes de l’accessibilité au composant Signature tactile :

  **Navigation au clavier améliorée :**
   * En appuyant sur la touche de tabulation, les utilisateurs et utilisatrices peuvent parcourir tous les éléments interactifs dans la boîte de dialogue de signature.
   * Signer avec un pinceau ou un clavier et appuyer sur la touche Entrée entraîne la fermeture de la boîte de dialogue.
   * Le focus reste sur la commande de signature après avoir signé et cliqué sur « OK ».

  **Fonctionnalité Effacer la signature :**

   * Une icône en forme de croix claire pour effacer la signature est accessible via la touche de tabulation.
   * La boîte de dialogue de confirmation « Effacer la signature » est également accessible via la navigation à l’aide de la touche de tabulation.

  **Libellés et contrôles améliorés :**
   * Le libellé du bouton de signature au clavier est désormais plus clair, et utilise « aria-label » pour annoncer la fonctionnalité (par exemple, « aria-label=&#39;Signer à l’aide du clavier&#39; »).
   * Un contraste amélioré permet de distinguer facilement tous les contrôles de la signature tactile.
   * Le bouton OK/coche indique désormais visuellement quand il est inactif.

  **Retour audio de signature pour les lecteurs d’écran :**
   * Lorsqu’une signature est saisie, les utilisateurs et les utilisatrices du lecteur d’écran peuvent entendre le texte utilisé pour créer la signature.

Cette mise à jour offre une expérience plus inclusive aux utilisateurs et utilisatrices présentant un handicap en améliorant la navigation, la clarté et le retour audio pour le composant Signature tactile.

### Programme d’adoption précoce {#forms-early-adopter}

* **[Envoi d’un formulaire adaptatif à un scénario Adobe Workfront Fusion](/help/forms/submit-adaptive-form-to-workfront-fusion.md)** : Forms as a Cloud Service propose une option prête à l’emploi pour connecter facilement un formulaire adaptatif à Adobe Workfront. Cela simplifie le processus d’envoi d’un formulaire adaptatif à un scénario Adobe Workfront, ce qui permet de déclencher un scénario Workfront Fusion lors de l’envoi d’un formulaire adaptatif.

  <br/> ![Adobe Workfront](/help/forms/assets/adobe-workfront.png) <br/> Avec le connecteur Adobe Workfront Fusion, vous pouvez concevoir des workflows qui sont déclenchés automatiquement lors de l’envoi d’un formulaire adaptatif. Par exemple, envisagez un scénario où un workflow est lancé pour affecter à une personne spécifique la tâche de révision des données envoyées, ce qui permet d’approuver ou de rejeter une application en fonction des informations capturées par le biais du formulaire adaptatif. Cette intégration rationalisée améliore l’efficacité et offre un nouveau niveau d’automatisation à vos processus de workflow.

* **[Reader Extension Service](/help/forms/aem-forms-cloud-service-communications-introduction.md#reader-extension-service)** : les API de communication d’AEM Forms ont introduit Reader Extension Service pour vous permettre d’ajouter des fonctionnalités telles que le remplissage de formulaires et les commentaires dans des PDF standard, ce qui les rend interactifs pour les utilisateurs et les utilisatrices disposant de la version gratuite d’Adobe Reader.

* [Prise en charge des langues de droite à gauche](/help/forms/supporting-new-language-localization-core-components.md) : les formulaires adaptatifs reposant sur les composants principaux peuvent désormais être présentés dans une langue de droite à gauche telle que l’arabe, le persan et l’ourdou. Les langues s’écrivant de droite à gauche sont parlées par plus de 2 milliards de personnes dans le monde. L’utilisation d’un formulaire pour les langues s’écrivant de droite à gauche permet d’étendre la portée de vos formulaires adaptatifs pour répondre à ces diverses audiences et aux marchés correspondants. Dans certaines régions, il en va d’une obligation légale de fournir des formulaires dans la langue locale. En vous adaptant aux langues locales, vous vous ouvrez non seulement à un public plus large, mais vous garantissez aussi le respect des lois et réglementations pertinentes.

* **[Protégez vos documents avec les API DocAssurance (qui font partie des API de communication)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)** : les API DocAssurance vous permettent de protéger les informations sensibles en signant et en chiffrant les documents. Grâce au chiffrement, le contenu d’un document est transformé en un format illisible, ce qui garantit que seules les personnes autorisées peuvent y accéder. Cette couche renforcée de protection protège non seulement les données précieuses des yeux non autorisés, mais offre également une certaine tranquillité d’esprit. Les API Signature permettent à votre entreprise de garantir la sécurité et la confidentialité des documents Adobe PDF qu’elle diffuse et reçoit. Ce service utilise les signatures numériques et la certification pour s’assurer que seules les personnes destinataires prévues peuvent modifier les documents.

  Vous pouvez écrire à `aem-forms-ea@adobe.com` depuis votre adresse e-mail officielle pour rejoindre le programme d’adoption précoce et demander l’accès à la fonctionnalité.

* **[Vous pouvez tirer parti du service de télémétrie opérationnelle](/help/implementing/cloud-manager/content-requests.md#real-user-monitoring-for-aem-as-a-cloud-service)** pour activer la collecte côté client pour AEM as a Cloud Service.
Le service de télémétrie opérationnelle offre un reflet plus précis des interactions des utilisateurs, assurant ainsi une mesure fiable de l’engagement du site web. Il constitue une excellente opportunité d’obtenir des informations avancées sur les performances de votre page. Il est ainsi utile pour la clientèle qui utilise un réseau CDN géré ou non par Adobe. Par ailleurs, pour les personnes utilisant un réseau CDN non géré par Adobe, il est désormais possible de créer automatiquement des rapports sur le trafic, ce qui leur évite d’avoir à partager n’importe quel rapport sur le trafic avec Adobe.

  Si vous souhaitez tester cette nouvelle fonctionnalité et partager vos commentaires, envoyez un e-mail à `aemcs-rum-adopter@adobe.com`, ainsi que votre nom de domaine pour chacun des environnements pour lesquels vous souhaitez activer la télémétrie opérationnelle à partir de votre adresse e-mail associée à votre Adobe ID. L’équipe produit Adobe activera alors le service de télémétrie opérationnelle pour vous.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Mappage de domaine {#cdn-config}

Configurez le trafic sur le réseau CDN d’Adobe comme suit :

* [Transformations des demandes](/help/implementing/dispatcher/cdn-configuring-traffic.md#request-transformations) : modifiez l’aspect des demandes entrantes, y compris les chemins, les paramètres de requête et les en-têtes HTTP avant qu’elles ne soient acheminées vers AEM.
* [Transformations des réponses](/help/implementing/dispatcher/cdn-configuring-traffic.md#response-transformations) : modifiez les en-têtes HTTP des réponses sortantes avant qu’elles ne soient présentées au navigateur.
* [Sélecteurs d’origine](/help/implementing/dispatcher/cdn-configuring-traffic.md#response-transformations#origin-selectors) : acheminez le trafic via le réseau CDN vers des sites et applications en dehors d’AEM.

Une fois ces règles déclarées dans le contrôle de code source (git), vous pouvez les déployer sur le réseau CDN à l’aide du pipeline de configuration de Cloud Manager. Voir également la fonctionnalité de redirections côté client dans la section relative à l’adoption précoce ci-dessous.

### Personnaliser les pages d’erreur du réseau CDN {#cdn-error-pages}

Dans le cas improbable où le réseau CDN ne pourrait pas acheminer le trafic vers l’origine d’AEM, une page d’erreur personnalisée peut être déclarée, en remplacement de la version générique. [En savoir plus](/help/implementing/dispatcher/cdn-error-pages.md) sur la manière de présenter les pages d’erreur de la marque.

### Programmes d’adoption précoce {#foundation-early-adopter}

#### Redirections côté serveur (programme destiné aux utilisateurs et utilisatrices précoces) {#server-side-redirects-early-adopter}

Configurez les redirections côté serveur 301/302 dans le contrôle de code source et déployez-les sur le réseau CDN. [En savoir plus](/help/implementing/dispatcher/cdn-configuring-traffic.md#server-side-redirectors) et rejoindre le programme d’adoption précoce en envoyant un e-mail à **<aemcs-cdn-config-adopter@adobe.com>**.

#### Alertes relatives aux règles de filtrage du trafic (programme d’adoption précoce) {#traffic-filter-rules-alerts-early-adopter}

Les [Règles de filtrage du trafic](/help/security/traffic-filter-rules-including-waf.md) récemment publiées qui incluent les règles WAF (Web Application Firewall) sous licence optionnelle vous permettent de configurer le trafic qui doit être autorisé ou refusé.

Vous pouvez maintenant envoyer un e-mail à **<aemcs-cdn-config-adopter@adobe.com>** pour rejoindre le programme d’adoption précoce pour pouvoir recevoir une alerte chaque fois que vos règles de filtrage du trafic sont déclenchées. Les notifications par e-mail du Centre d’actions vous tiendront au courant lorsque certaines conditions de trafic se produisent afin que vous puissiez prendre les mesures appropriées.

#### Ingestion d’exécution d’Apache/du Dispatcher des mappages de réécriture (programme d’adoption précoce) {#apache-rewritemaps-early-adopter}

Comme pour AEM 6.5, Apache/le Dispatcher ingère des mappages de réécriture placées à un emplacement spécifique dans le référentiel de publication et les charge, sans nécessiter d’exécution de pipeline de niveau web. Un utilisateur professionnel ou une utilisatrice professionnelle peut ainsi déclarer des redirections à l’aide d’une interface utilisateur, comme celle proposée par le gestionnaire de mappage de redirection ACS Commons. Contactez **<aemcs-cdn-config-adopter@adobe.com>** pour plus d’informations.

#### Edge Side Includes (ESI) pour le chargement de contenu dynamique (programme d’adoption précoce) {#esi-early-adopter}

Le réseau CDN géré par Adobe prend désormais en charge Edge Side Includes (ESI), un langage de balisage pour l’assemblage de contenu web dynamique au niveau Edge. En incluant des extraits de code ESI, vous pouvez mettre en cache la page HTML globale sur le réseau CDN avec des TTL plus élevés, tout en récupérant plus fréquemment de l’origine les sections plus petites qui nécessitent des mises à jour à un rythme supérieur (TTL moins élevés). Veuillez contacter **<aemcs-cdn-config-adopter@adobe.com>** pour plus d’informations.

#### Prise en charge du RDE pour le code en front-end à l’aide des thèmes du site et des modèles de site (programme d’adoption précoce) {#rde-frontend-early-adopter}

Les [environnements de développement rapide (RDE)](/help/implementing/developing/introduction/rapid-development-environments.md) prennent désormais en charge le code en front-end basé sur les [thèmes de site](/help/sites-cloud/administering/site-creation/site-themes.md) et les [modèles de site](/help/sites-cloud/administering/site-creation/site-templates.md), pour les utilisateurs et utilisatrices bénéficiant de l’adoption précoce. Avec les RDE, la prise en charge s’effectue à l’aide d’une directive de ligne de commande plutôt que d’un [pipeline front-end](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md). Veuillez contacter **<aemcs-rde-support@adobe.com>** pour essayer cette fonctionnalité et fournir des commentaires.

#### Amélioration de la journalisation des RDE (programme d’adoption précoce) {#rde-logging-early-adopter}

Lors du débogage du code dans un [environnement de développement rapide (RDE)](/help/implementing/developing/introduction/rapid-development-environments.md), les développeurs et développeuses peuvent désormais configurer et diffuser plus efficacement les journaux à l’aide de la ligne de commande, et cela sans modifier les propriétés OSGi dans la gestion de versions. Les fonctionnalités incluent les suivantes :

* déclarer des niveaux de journal par niveau de package ou de classe ;
* personnaliser le format de sortie du journal ;
* diffuser plusieurs journaux en parallèle.

Veuillez contacter **<aemcs-rde-support@adobe.com>** pour essayer cette fonctionnalité et fournir des commentaires.

## [!DNL Experience Manager] Guides {#guides}

### Possibilité de traduire du contenu dans plusieurs langues à l’aide de groupes de langues préconfigurés

Experience Manager Guides permet désormais de créer des groupes de langues et de traduire facilement votre contenu dans plusieurs langues. Cette fonctionnalité permet d’organiser et de gérer les traductions en fonction des besoins de votre organisation.

Par exemple, si vous devez traduire votre contenu pour certains pays d’Europe, vous pouvez créer un groupe de langues pour les langues européennes telles que l’anglais (EN), le français (FR), l’allemand (DE), l’espagnol (ES) et l’italien (IT).

![Panneau de traduction](/help/release-notes/assets/guides/translation-languages-2404.png)

*Sélectionnez les groupes de langues ou les langues que vous souhaitez utiliser pour traduire vos documents.*

>[!NOTE]
>
>Si le dossier cible d’une langue est manquant ou si la langue cible est identique à la langue source, elle est grisée et un signe d’avertissement est affiché.

En tant qu’administrateur ou administratrice, vous pouvez créer des groupes de langues et les configurer sur plusieurs profils de dossiers. En tant qu’auteur ou autrice, vous pouvez afficher les groupes de langues configurés sur votre profil de dossier.


Dans l’ensemble, la création de groupes de langues renforce l’efficacité et la productivité des projets de traduction, améliorant ainsi le processus de localisation dans plusieurs langues.


Découvrir comment [traduire des documents à partir de l’éditeur web](https://experienceleague.adobe.com/fr/docs/experience-manager-guides/using/user-guide/author-content/create-preview-topics/author-content-aem-guides/work-with-web-editor/translate-documents-web-editor)

### Expérience redéfinie pour la recherche et le filtrage de fichiers dans la vue du référentiel

Le filtrage des fichiers est maintenant amélioré. La redéfinition de la fonctionnalité de filtrage des fichiers facilite les recherches et la navigation dans les fichiers.

![Recherche de fichiers dans la vue du référentiel](/help/release-notes/assets/guides/repository-filter-search-2404.png)

*Rechercher des fichiers contenant le texte « `general purpose.`* »

Profitez d’avantages tels qu’un accès plus rapide aux fichiers importants et une interface utilisateur plus intuitive. Votre expérience de recherche devient plus fluide et plus efficace.

![Filtre de recherche rapide](/help/release-notes/assets/guides/repository-filter-search-quick.png)

*Utilisez les filtres rapides pour rechercher des fichiers DITA et non DITA.*

En savoir plus sur la fonction **Filtrer la recherche** dans la section [Panneau de gauche](https://experienceleague.adobe.com/fr/docs/experience-manager-guides/using/user-guide/author-content/create-preview-topics/author-content-aem-guides/work-with-web-editor/web-editor-features#id2051EA0M0HS).

### Améliorations apportées aux connecteurs de sources de données

Les améliorations suivantes ont été apportées aux connecteurs de sources de données dans la version 2024.4.0 :

#### Se connecter aux sources de données Salsify, Akeneo et Microsoft Azure DevOps (ADO) Boards

Outre les connecteurs prêts-à-l’emploi existants, Experience Manager Guides fournit également des connecteurs pour les sources de données Salsify, Akeneo et Microsoft Azure DevOps (ADO) Boards. En tant qu’administrateur ou administratrice, vous pouvez télécharger et installer ces connecteurs. Configurez ensuite les connecteurs installés.

#### Copier et coller l’exemple de requête pour créer un extrait de contenu ou une rubrique

Vous pouvez facilement copier et coller un exemple de requête de données dans le générateur pour créer un extrait de contenu ou une rubrique. Grâce à cette fonction, vous n’avez pas à mémoriser la syntaxe ni à créer une requête manuellement. Au lieu de saisir une requête manuellement, vous pouvez copier et coller un exemple de requête, le modifier et l’utiliser pour récupérer des données selon vos besoins.

![Boîte de dialogue Insérer un extrait de contenu](/help/release-notes/assets/guides/insert-content-snippet.png)

*Copiez et modifiez un exemple de requête pour créer l’extrait de contenu.*

#### Se connecter aux fichiers de données JSON à l’aide d’un connecteur de fichier


Désormais, en tant qu’administrateur ou administratrice, vous pouvez configurer un connecteur de fichier JSON pour qu’il utilise les fichiers de données JSON comme source de données. Utilisez le connecteur pour importer les fichiers JSON de votre ordinateur ou d’Adobe Experience Manager Assets. Ensuite, en tant qu’auteur ou autrice, vous pouvez créer des extraits de contenu ou des rubriques à l’aide des générateurs.

Cette fonctionnalité vous permet d’utiliser les données stockées dans vos fichiers JSON et de les réutiliser dans divers extraits de code. Le contenu est également mis à jour de manière dynamique à chaque fois que vous actualisez les fichiers JSON.

#### Configurer plusieurs URL de ressources pour un connecteur afin de créer des extraits de contenu ou des rubriques

En tant qu’administrateur ou administratrice, vous pouvez configurer plusieurs URL de ressources pour certains connecteurs tels que Generic REST Client, Salsify, Akeneo et Microsoft Azure DevOps (ADO) Boards.
Ensuite, en tant qu’auteur ou autrice, connectez-vous aux sources de données pour créer des extraits de contenu ou des rubriques à l’aide des générateurs. Cette fonctionnalité est pratique, car vous n’avez pas à créer de source de données pour chaque URL. Cela vous permet de récupérer rapidement des données à partir d’une ressource pour une source de données spécifique dans un extrait de contenu ou une rubrique unique. Consultez plus de détails sur les connecteurs de sources de données et sur la façon de [configurer un connecteur de source de données à partir de l’interface utilisateur](https://experienceleague.adobe.com/fr/docs/experience-manager-guides/using/install-guide/cs-ig/web-editor-configs-cs/conf-data-source-connector-tools). Découvrez comment [utiliser les données de votre source de données](https://experienceleague.adobe.com/fr/docs/experience-manager-guides/using/user-guide/author-content/create-preview-topics/author-content-aem-guides/work-with-web-editor/web-editor-content-snippet).

Pour plus d’informations sur les nouvelles fonctionnalités et améliorations, consultez les informations sur les versions de [Experience Manager Guides](https://experienceleague.adobe.com/fr/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici](/help/implementing/cloud-manager/release-notes/current.md).

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [ici](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
