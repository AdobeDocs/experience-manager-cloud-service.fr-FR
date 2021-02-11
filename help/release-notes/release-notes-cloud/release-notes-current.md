---
title: Notes de mise à jour actuelles pour  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour actuelles pour  [!DNL Adobe Experience Manager]  as a Cloud Service.
translation-type: tm+mt
source-git-commit: d20a729712c1dbd48150f813419b57c49074b492
workflow-type: tm+mt
source-wordcount: '978'
ht-degree: 17%

---


# Notes de mise à jour pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante présente les notes de mise à jour générales d’[!DNL Experience Manager] as a Cloud Service.

## Date de publication {#release-date}

La date de publication de [!DNL Adobe Experience Manager] en tant que Cloud Service 2021.1.0 est le 3 février 2021.
La version suivante (2021.2.0) sera publiée le 25 février 2021.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### Gestion de contenu en mode sans affichage {#headless}

* **[API GraphQL pour la Diffusion](/help/assets/content-fragments/graphql-api-content-fragments.md)** de fragments de contenu : Possibilité de requête de fragments de contenu à l’aide de la syntaxe GraphQL et de schémas basés sur des modèles de fragments de contenu, pour une sortie au format JSON.

* **[Prise en charge de l’authentification pour les demandes](/help/assets/content-fragments/graphql-authentication-content-fragments.md)** d’API GraphQL : Capacité à authentifier les demandes d’API GraphQL avec des jetons d&#39;accès pour les API côté serveur.

* **[Le composant](/help/implementing/developing/hybrid/remote-page.md)** RemotePage : Prise en charge Ajoutée de l’affichage et de la modification des SPA externes dans AEM utilisation.

* **[Modification d&#39;un SPA externe dans AEM](/help/implementing/developing/hybrid/editing-external-spa.md)** : Possibilité Ajoutée de télécharger une application autonome d’une seule page sur une instance AEM, d’ajouter des sections de contenu modifiables et d’activer la création.

* Amélioration de la sortie JSON à partir de l’API GraphQL, notamment la possibilité de générer du texte enrichi au format JSON et dans les paramètres régionaux.

* Prise en charge de l’imbrication de modèles de fragments de contenu pour permettre la création de structures de fragments de contenu imbriquées, par le biais de types de données de référence de fragments de contenu dédiés ou de références de fragments de contenu insérées dans des champs de texte multilignes.

* D’autres règles de validation sont disponibles dans les types de données du modèle Fragment de contenu, notamment &quot;unique&quot;, &quot;obligatoire&quot; et &quot;traduisible&quot;.

* Possibilité de baliser les modèles de fragments de contenu et d’autoriser la création de fragments de contenu dans un dossier avec des stratégies par balises ou chemins d’accès.

* Améliorations de la convivialité de l’éditeur de fragments de contenu, notamment l’action de publication et l’affichage du modèle sur lequel un fragment est basé.

* Possibilité de prévisualisation de la sortie JSON directement dans l’éditeur de fragments de contenu.

<!--
### Progressive Web Apps (PWAs) {#pwa}

* [A Progressive Web App (PWA) version of a site](/help/sites-cloud/authoring/features/enable-pwa.md)  can now be enabled at the project level via simple configuration.
-->

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

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.2.0 est le 11 février 2021.

### Nouveautés {#what-is-new-cloud-manager}

* Le pipeline de production de Cloud Manager inclut désormais la fonctionnalité de test d’interface utilisateur personnalisée.

* Les clients du module Ressources peuvent désormais choisir quand et où déployer leur instance de portail de marque en libre-service via l’interface utilisateur de Cloud Manager. Pour un programme standard (non sandbox) avec la solution Ressources, le portail de marque peut désormais être mis en service sur l’environnement de production. L’approvisionnement ne peut être effectué qu’une seule fois sur l’environnement Production.

* L&#39;archétype de projet AEM utilisé dans Project and Sandbox Creation a été mis à jour vers la version 25.

* La liste des API obsolètes identifiées lors de l’analyse du code a été affinée afin d’inclure d’autres classes et méthodes obsolètes dans les dernières versions du SDK Cloud Service.

* Profil SonarQube pour Cloud Manager mis à jour pour supprimer la règle Sonar squid:S2142. Ceci ne sera plus en conflit avec les contrôles Interruption du thread.

* L’interface utilisateur de Cloud Manager informe l’utilisateur qui ne peut pas temporairement ajouter/mettre à jour le nom de domaine car l’environnement associé dispose soit d’un pipeline en cours d’exécution qui lui est associé, soit de l’étape d’approbation en attente.

* Les propriétés définies dans les fichiers `pom.xml` client précédés du préfixe Sonar seront désormais supprimées dynamiquement afin d’éviter les échecs d’analyse de la génération et de la qualité.

* L’interface utilisateur de Cloud Manager informe l’utilisateur qui ne peut pas sélectionner de certificat SSL pour le moment s’il est utilisé par un nom de domaine en cours de déploiement.

### Correctifs {#bug-fixes-cloud-manager}

* La correspondance d’un certificat SSL avec un nom de domaine n’est plus sensible à la casse.

* L’interface utilisateur de Cloud Manager informe désormais un utilisateur si les clés privées du certificat ne respectent pas la limite de 2 048 bits avec un message d’erreur approprié.

* L’interface utilisateur de Cloud Manager informe l’utilisateur qui ne peut pas sélectionner de certificat SSL pour le moment s’il est utilisé par un nom de domaine en cours de déploiement.

* Dans certains cas, un problème interne peut bloquer la suppression d’environnement.

* Certains échecs de pipeline étaient incorrectement signalés comme des erreurs de pipeline.

## aem en tant que fondation Cloud Service {#aem-as-a-cloud-service-foundation}

### Nouveautés {#what-is-new-foundation}

* Appels d&#39;API authentifiés serveur à serveur : générez les jetons d&#39;accès appropriés pour effectuer des appels d&#39;API authentifiés serveur à serveur entre vos applications externes et AEM en tant qu&#39;environnements Cloud Service. Pour en savoir plus, lisez [la documentation](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) ou consultez le [didacticiel](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=en#authentication).

### Analyseurs de build de SDK {#sdk-build-analyzers}

Le plug-in Build Analyzer Maven du SDK AEM as a Cloud Service détecte des problèmes dans un projet Maven, y compris les dépendances manquantes. Il permet aux développeurs d’identifier des problèmes au cours du développement local, bien avant leur déploiement dans les environnements Cloud avec Cloud Manager.

Deux nouveaux analyseurs ont été ajoutés pour cette version :

* analyseur repointeur
* bundle-nativecode

Pour plus d&#39;informations, consultez la documentation [ici](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=fr#developing).

## Outils de transition vers le cloud {#code-transition-tools}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu v1.2.2 est le 01 février 2021.

### Nouveautés de [!DNL Content Transfer Tool] {#what-is-new-ctt}

* Nouvelle fonctionnalité et interface utilisateur ajoutées à l’outil de transfert de contenu - Outil de mappage des utilisateurs. Cette fonctionnalité mappe automatiquement les utilisateurs et les groupes existants à leurs identifiants système Identity Management Adobe dans le cadre de l’activité de migration de contenu. Pour plus d&#39;informations, consultez [Utilisation de l&#39;outil de mappage utilisateur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html).
* L’outil de transfert de contenu migre désormais tous les groupes et utilisateurs référencés dans le jeu de migration, y compris les enfants.
* Les utilisateurs sont autorisés à sélectionner certains chemins sous `/etc` lors de la création de jeux de migration.
