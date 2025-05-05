---
title: Notes de mise à jour de la version 2021.1.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour d’[!DNL Adobe Experience Manager] as a Cloud Service version 2021.1.0.
exl-id: cd639736-6e3d-4b69-b8ae-11e4e6490535
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '791'
ht-degree: 92%

---


# Notes de mise à jour pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante présente les notes de mise à jour générales d’[!DNL Experience Manager] as a Cloud Service.

## Date de publication {#release-date}

La date de publication d’[!DNL Adobe Experience Manager] as a Cloud Service version 2021.1.0 est le 3 février 2021.
La version suivante (2021.2.0) sera publiée le 25 février 2021.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

* **[API HTTP de fragment de contenu](/help/assets/content-fragments/assets-api-content-fragments.md)** : ajoutez la possibilité d’ajouter ou de mettre à jour et de supprimer des variations de fragments de contenu à l’aide de l’API HTTP.

* **[API GraphQL pour la diffusion de fragments de contenu](/help/headless/graphql-api/content-fragments.md)** : possibilité de requête de fragments de contenu à l’aide de la syntaxe GraphQL et de schémas basés sur des modèles de fragments de contenu, pour une sortie au format JSON.

* **[Prise en charge de l’authentification pour les demandes d’API GraphQL](/help/headless/security/authentication.md)** : capacité à authentifier les demandes d’API GraphQL avec des jetons d’accès pour les API côté serveur.

* Amélioration de la sortie JSON à partir de l’API GraphQL, notamment la possibilité de générer du texte enrichi au format JSON et dans différentes langues.

* Prise en charge de l’imbrication de modèles de fragments de contenu pour permettre la création de structures de fragments de contenu imbriquées, par le biais de types de données de référence de fragments de contenu dédiés ou de références de fragments de contenu insérées dans des champs de texte multilignes.

* D’autres règles de validation sont disponibles dans les types de données du modèle Fragment de contenu, notamment « unique », « obligatoire » et « traduisible ».

* Possibilité de baliser les modèles de fragments de contenu et d’autoriser la création de fragments de contenu dans un dossier avec des politiques par balises ou chemins d’accès.

* Améliorations de la convivialité de l’éditeur de fragment de contenu, notamment l’action de publication et l’affichage du modèle sur lequel est basé un fragment.

* Possibilité de prévisualisation de la sortie JSON directement dans l’éditeur de fragment de contenu.


## [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

* [!DNL Experience Manager] as a [!DNL Cloud Service] étend la fonctionnalité de balises intelligentes pour prendre en charge l’identification des mots-clés et des entités dans les ressources textuelles. Le texte est identifié, indexé et mis à disposition sous la forme de métadonnées pour améliorer l’expérience de recherche sans avoir besoin d’une configuration. Voir [Balises intelligentes](/help/assets/smart-tags.md).

* Le format de fichier MXF est désormais pris en charge. Voir [Formats de fichiers pris en charge](/help/assets/file-format-support.md#video-formats).

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nouveautés {#what-is-new-commerce}

* Gestion de l’expérience des produits : nouvel onglet de propriétés Commerce pour les ressources et les fragments d’expérience. Cet onglet permet de lier des produits/catégories à des ressources et fragments d’expérience. L’onglet affiche également des données en temps réel pour les produits/catégories liés ainsi qu’un lien permettant d’afficher des détails dans la console du produit.

* Publication CIF site de référence Venia - 2021.02.02 qui comprend la dernière version de CIF Core Components v1.7.0. Pour plus d’informations, voir [CIF site de référence Venia](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.02.02) .

* Publication CIF composants principaux v1.7.0. Pour plus d’informations, voir [CIF Core Components](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.7.0) .

## Cloud Manager {#cloud-manager}

### Date de publication {#release-date-cm}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.1.0 est le 14 janvier 2021.

### Correctifs {#bug-fixes-cloud-manager}

* L’instance de production de ressources peut occasionnellement afficher le statut de Brand Portal sur la page de détails **Environnements** comme étant *En attente* sans permettre à l’utilisateur d’effectuer une action.

* Lors d’une réactivation après mise en veille dans Cloud Manager, un message d’échec s’affichait parfois, même lorsque la réactivation était correctement lancée.

* Les rares cas d’échec rencontrés lors de la création ou de la suppression d’environnements ont été résolus.

## Outils de refactorisation du code {#code-refactoring-tools}

### Nouveautés d’[!DNL Code Refactoring Tools]  {#what-is-new-crt}

* Publication de la nouvelle version du plug-in AIO-CLI. La dernière version de ce plug-in comprend des correctifs pour le Dispatcher Converter et le Repository Modernizer AEM et prend également en charge un nouvel utilitaire : Index Converter. Voir [Expérience unifiée](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html?lang=fr#benefits) pour en savoir plus sur ce module externe.

* Index Converter est un utilitaire qui permet de transformer les définitions d’index OAK personnalisées d’un client en définitions d’index OAK compatibles avec AEM as a Cloud Service. Pour plus d’informations, voir [Convertisseur d’index](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter) .

* Nouvelle fonctionnalité ajoutée à [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) qui crée un package distinct `ui.config` contenant toutes les configurations OSGi.

### Correctifs {#crt-bug-fixes}

* Plusieurs correctifs de bogues ont été apportés aux outils Dispatcher Converter et Repository Modernizer d’AEM. Voir [Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter) et [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer).

## AEM as a Cloud Service Foundation {#aem-as-a-cloud-service-foundation}

### Nouveautés {#what-is-new-foundation}

* Appels d’API authentifiés de serveur à serveur : générez les jetons d’accès appropriés pour effectuer des appels d’API authentifiés de serveur à serveur entre vos applications externes et les environnements AEM as a Cloud Service. Pour en savoir plus, accédez à la [documentation](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) ou consultez le [tutoriel](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=fr#authentication).

### Analyseurs de build de SDK {#sdk-build-analyzers}

Le plug-in Build Analyzer Maven du SDK AEM as a Cloud Service détecte des problèmes dans un projet Maven, y compris les dépendances manquantes. Il permet aux développeurs d’identifier des problèmes au cours du développement local, bien avant leur déploiement dans les environnements cloud avec Cloud Manager.

Deux nouveaux analyseurs ont été ajoutés pour cette version :

* repoinit analyzer
* bundle-nativecode

Pour plus d’informations, voir la documentation [ici](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=fr#developing).

## Outils de transition vers le cloud {#code-transition-tools}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu v1.2.2 est le 1er février 2021.

### Nouveautés de [!DNL Content Transfer Tool]  {#what-is-new-ctt}

* Fonctionnalité et interface utilisateur nouvelles ajoutées à l’outil de transfert de contenu – Outil de mappage des utilisateurs. Cette fonctionnalité mappe automatiquement les utilisateurs et les groupes existants avec leur identifiant IMS (Identity Management System) Adobe au cours de l’activité de migration de contenu. Pour plus d’informations, consultez [Utilisation de l’outil de mappage des utilisateurs](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=fr).
* L’outil de transfert de contenu assure désormais la migration de tous les groupes et utilisateurs référencés dans le jeu de migration, y compris les enfants.
* Les utilisateurs sont autorisés à sélectionner certains chemins sous `/etc` lors de la création de jeux de migration.
