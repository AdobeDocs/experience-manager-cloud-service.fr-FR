---
title: Notes de mise à jour actuelles de  [!DNL Adobe Experience Manager] en tant que Cloud Service.
description: Notes de mise à jour actuelles de  [!DNL Adobe Experience Manager] en tant que Cloud Service.
translation-type: tm+mt
source-git-commit: cd392473d4e8ebee20b41c6c979121fe81819a40
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 11%

---


# Notes de mise à jour pour [!DNL Adobe Experience Manager] as a Cloud Service  {#release-notes}

La section suivante décrit les Notes de mise à jour générales de [!DNL Experience Manager] en tant que Cloud Service.

## Date de publication {#release-date}

La date de publication de [!DNL Adobe Experience Manager] en tant que Cloud Service 2021.1.0 est le 3 février 2021.
La version suivante (2021.2.0) sera publiée le 25 février 2021.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service{#sites}

* **[API](/help/assets/content-fragments/assets-api-content-fragments.md)** HTTP de fragment de contenu : Ajoutez la possibilité d’ajouter/de mettre à jour et de supprimer des variations de fragments de contenu à l’aide de l’API HTTP.

* **[API GraphQL pour la Diffusion](/help/assets/content-fragments/graphql-api-content-fragments.md)** de fragments de contenu : Possibilité de requête de fragments de contenu à l’aide de la syntaxe GraphQL et de schémas basés sur des modèles de fragments de contenu, pour une sortie au format JSON.

* **[Prise en charge de l’authentification pour les demandes](/help/assets/content-fragments/graphql-authentication-content-fragments.md)** d’API GraphQL : Capacité à authentifier les demandes d’API GraphQL avec des jetons d&#39;accès pour les API côté serveur.

* Amélioration de la sortie JSON à partir de l’API GraphQL, notamment la possibilité de générer du texte enrichi au format JSON et dans les paramètres régionaux.

* Prise en charge de l’imbrication de modèles de fragments de contenu pour permettre la création de structures de fragments de contenu imbriquées, par le biais de types de données de référence de fragments de contenu dédiés ou de références de fragments de contenu insérées dans des champs de texte multilignes.

* D’autres règles de validation sont disponibles dans les types de données du modèle Fragment de contenu, notamment &quot;unique&quot;, &quot;obligatoire&quot; et &quot;traduisible&quot;.

* Possibilité de baliser les modèles de fragments de contenu et d’autoriser la création de fragments de contenu dans un dossier avec des stratégies par balises ou chemins d’accès.

* Améliorations de la convivialité de l’éditeur de fragments de contenu, notamment l’action de publication et l’affichage du modèle sur lequel un fragment est basé.

* Possibilité de prévisualisation de la sortie JSON directement dans l’éditeur de fragments de contenu.


## [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

* [!DNL Experience Manager] comme a  [!DNL Cloud Service] étendu la fonctionnalité Balises actives pour prendre en charge l’identification des mots-clés et des entités dans les ressources textuelles. Le texte est identifié, indexé et mis à disposition en tant que métadonnées pour améliorer l&#39;expérience de recherche sans avoir besoin d&#39;aucune configuration. Voir [Balises dynamiques](/help/assets/smart-tags.md).

* Le format de fichier MXF est désormais pris en charge. Voir [formats de fichier pris en charge](/help/assets/file-format-support.md#video-formats).

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nouveautés {#what-is-new-commerce}

* Gestion de l&#39;expérience des produits : Nouvel onglet Propriétés Commerce pour les ressources et les fragments d’expérience. Cet onglet vous permet de lier des produits/catégories aux ressources et aux fragments d’expérience. L’onglet affiche également des données en temps réel pour les produits/catégories liés et un lien permettant d’afficher des détails dans la console du produit.

* Site de référence de CIF Venia - 2021.02.02 qui comprend la dernière version des composants principaux de CIF version 1.7.0. Pour plus d&#39;informations, consultez [Site de référence de CIF Venia](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.02.02).

* Publication des composants principaux CIF version 1.7.0. Reportez-vous à [Composants principaux CIF](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.7.0) pour plus de détails.

## Cloud Manager {#cloud-manager}

### Date de publication {#release-date-cm}

La date de publication de Cloud Manager en tant que Cloud Service 2021.1.0 est le 14 janvier 2021.

### Correctifs {#bug-fixes-cloud-manager}

* L’instance de production de ressources peut, à l’occasion, afficher l’état du portail de la marque sur la page de détails **Environnements** sous la forme *En attente* sans permettre à l’utilisateur d’effectuer une action.

* Lors du déclenchement d’une désactivation de l’hibernation à partir de Cloud Manager, un message d’échec s’affichait parfois, même lorsque la désactivation de l’hibernation était correctement lancée.

* Les rares cas d&#39;échec rencontrés lors de la création ou de la suppression d&#39;environnements ont été résolus.

## Outils de refactorisation du code {#code-refactoring-tools}

### Nouveautés de [!DNL Code Refactoring Tools] {#what-is-new-crt}

* Nouvelle version du module externe AIO-CLI publiée. La dernière version de ce module comprend des correctifs pour AEM Dispatcher Converter et Repository Modernizer et prend également en charge un nouvel utilitaire - Index Converter. Consultez [Expérience unifiée](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html?lang=en#benefits) pour en savoir plus sur ce module externe.

* Index Converter est un utilitaire qui permet de transformer les définitions d&#39;index OAK personnalisées d&#39;un client en AEM en définitions d&#39;index OAK compatibles avec les Cloud Service. Pour plus d&#39;informations, consultez [Index Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter).

* Nouvelle fonctionnalité ajoutée à [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) qui crée un package distinct `ui.config` qui contient toutes les configurations OSGi.

### Correctifs {#crt-bug-fixes}

* Plusieurs correctifs de bogues ont été apportés aux outils  Dispatcher Converter et Repository Modernizer. Veuillez vous reporter à [AEM Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter) et [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer).

## aem en tant que fondation Cloud Service {#aem-as-a-cloud-service-foundation}

### Nouveautés {#what-is-new-foundation}

* Appels d&#39;API authentifiés serveur à serveur : générez les jetons d&#39;accès appropriés pour effectuer des appels d&#39;API authentifiés serveur à serveur entre vos applications externes et AEM en tant qu&#39;environnements Cloud Service. Pour en savoir plus, lisez [la documentation](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) ou consultez le [didacticiel](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=en#authentication).

### Analyseurs de génération de SDK {#sdk-build-analyzers}

L’AEM en tant que module externe expert de création de SDK Cloud Service détecte des problèmes dans un projet expert, y compris les dépendances manquantes. Il permet aux développeurs de découvrir des problèmes au cours du développement local, bien avant leur déploiement dans les environnements Cloud avec Cloud Manager.

Deux nouveaux analyseurs ont été ajoutés pour cette version :

* analyseur repointeur
* bundle-nativecode

Pour plus d&#39;informations, consultez la documentation [ici](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=en#developing).

## Outils de transition vers le cloud {#code-transition-tools}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu v1.2.2 est le 01 février 2021.

### Nouveautés de [!DNL Content Transfer Tool] {#what-is-new-ctt}

* Nouvelle fonctionnalité et interface utilisateur ajoutées à l’outil de transfert de contenu - Outil de mappage des utilisateurs. Cette fonctionnalité mappe automatiquement les utilisateurs et les groupes existants à leurs identifiants système Identity Management Adobe dans le cadre de l’activité de migration de contenu. Pour plus d&#39;informations, consultez [Utilisation de l&#39;outil de mappage utilisateur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html).
* L’outil de transfert de contenu migre désormais tous les groupes et utilisateurs référencés dans le jeu de migration, y compris les enfants.
* Les utilisateurs sont autorisés à sélectionner certains chemins sous `/etc` lors de la création de jeux de migration.
