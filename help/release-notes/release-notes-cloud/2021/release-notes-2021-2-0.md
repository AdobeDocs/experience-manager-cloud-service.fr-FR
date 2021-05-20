---
title: Notes de mise à jour de la version 2021.2.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour d’[!DNL Adobe Experience Manager] as a Cloud Service version 2021.2.0.
exl-id: 88dac54b-cc12-44a0-b429-6e691221f806
source-git-commit: b842f70bd53676d23229e24edb4a957ff7613824
workflow-type: tm+mt
source-wordcount: '1237'
ht-degree: 39%

---


# Notes de mise à jour pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante présente les notes de mise à jour générales d’[!DNL Experience Manager] as a Cloud Service.

## Date de publication {#release-date}

La date de publication d’[!DNL Adobe Experience Manager] as a Cloud Service version 2021.2.0 est le 25 février 2021.
La version suivante (2021.3.0) sera publiée le 25 mars 2021.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### Gestion de contenu découplé {#headless}

* **[API GraphQL pour la diffusion de fragments de contenu](/help/assets/content-fragments/graphql-api-content-fragments.md)** : possibilité de requête de fragments de contenu à l’aide de la syntaxe GraphQL et de schémas basés sur des modèles de fragments de contenu, pour une sortie au format JSON.

* **[Prise en charge de l’authentification pour les demandes d’API GraphQL](/help/assets/content-fragments/graphql-authentication-content-fragments.md)** : capacité à authentifier les demandes d’API GraphQL avec des jetons d’accès pour les API côté serveur.

* **[Composant RemotePage](/help/implementing/developing/hybrid/remote-page.md)** : ajout de la prise en charge de l’affichage et de la modification des SPA externes dans AEM.

* **[Modification d’une SPA externe dans AEM](/help/implementing/developing/hybrid/editing-external-spa.md)** : ajout de la possibilité de charger une application sur une seule page dans une instance AEM, d’ajouter des sections de contenu modifiables et d’activer la création.

* Amélioration de la sortie JSON à partir de l’API GraphQL, notamment la possibilité de générer du texte enrichi au format JSON et dans différentes langues.

* Prise en charge de l’imbrication de modèles de fragments de contenu pour permettre la création de structures de fragments de contenu imbriquées, par le biais de types de données de référence de fragments de contenu dédiés ou de références de fragments de contenu insérées dans des champs de texte multilignes.

* D’autres règles de validation sont disponibles dans les types de données du modèle Fragment de contenu, notamment « unique », « obligatoire » et « traduisible ».

* Possibilité de baliser les modèles de fragments de contenu et d’autoriser la création de fragments de contenu dans un dossier avec des stratégies par balises ou chemins d’accès.

* Améliorations de la convivialité de l’éditeur de fragment de contenu, notamment l’action de publication et l’affichage du modèle sur lequel est basé un fragment.

* Possibilité de prévisualisation de la sortie JSON directement dans l’éditeur de fragment de contenu.

<!--
### Progressive Web Apps (PWAs) {#pwa}

* [A Progressive Web App (PWA) version of a site](/help/sites-cloud/authoring/features/enable-pwa.md)  can now be enabled at the project level via simple configuration.
-->

## [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

## Nouveautés de [!DNL Assets] {#what-is-new-assets}

* Les ressources peuvent être sources à l’aide de [!DNL Experience Manager Assets Brand Portal]. Il permet d’obtenir des ressources auprès des utilisateurs de l’agence pour de nouvelles campagnes marketing, séances photo et projets.

* [!DNL Experience Manager Assets] as a  [!DNL Cloud Service] a le droit d’avoir une  [!DNL Brand Portal] instance préconfigurée. L’utilisateur [!DNL Cloud Manager] peut activer [!DNL Brand Portal] sur [!DNL Experience Manager Assets] sous la forme [!DNL Cloud Service]. Voir [Activation de Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/brand-portal/configure-aem-assets-with-brand-portal.html?lang=fr).

* Les entreprises peuvent désormais sources des ressources à l’aide de [!DNL Brand Portal]. La fonction d’approvisionnement des ressources exploite [!DNL Brand Portal] pour aider les clients à interagir avec les utilisateurs de l’agence pour sources de ressources pour de nouvelles campagnes marketing, séances photo et projets. Voir [approvisionnement des ressources dans [!DNL Brand Portal]](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html).

* Le rapport d’utilisation [!DNL Brand Portal] affiche désormais uniquement les utilisateurs principaux. Les utilisateurs inactifs ne s’affichent pas maintenant. Les utilisateurs principaux sont ceux dont le compte est affecté à un profil de produit dans la balise [!DNL Admin Console]. Voir [[!DNL Brand Portal] rapports](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/admin-tools/brand-portal-reports.html).

* Dans [!DNL Brand Portal], un nouveau paramètre de téléchargement est ajouté. Il permet de créer un dossier distinct pour chaque ressource lors du téléchargement de dossiers, de collections, etc. Consultez [Paramètres de téléchargement](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/download/brand-portal-download-assets.html).

## Correctifs de bogues dans [!DNL Assets] {#bug-fixes-assets}

* Lorsque plusieurs ressources sont sélectionnées pour mettre à jour les propriétés, une erreur se produit parfois ou les propriétés d’une ressource désélectionnée sont mises à jour. (CQ-4316532)
* Lorsque vous essayez d’ouvrir [!UICONTROL Rail de recherche d’administrateurs de ressources], la page reste vide et cliquez sur [!UICONTROL Modifier] > [!UICONTROL Paramètres] génère une erreur. (CQ-4315079)
* Lorsqu’une nouvelle version d’une ressource existante est créée après la résolution du conflit de dénomination, les métadonnées de la ressource d’origine sont écrasées. (CQ-4313594)
* Lorsqu’une ressource contenant du texte d’annotation long est imprimée, le texte de l’annotation est ajusté, même si de l’espace est disponible. (CQ-4314101)

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nouveautés {#what-is-new-commerce}

* Gestion de l’expérience du produit : Enrichissez les pages du catalogue de produits individuellement avec les fragments d’expérience.

* Étendez les propriétés de la console de produit pour afficher les ressources liées et les fragments d’expérience, y compris l’action permettant d’accéder rapidement au contenu associé.

* Publication du site de référence de CIF Venia – 2021.02.24 qui comprend les derniers composants principaux de CIF version 1.8.0. Pour plus d’informations, consultez [Site de référence de CIF Venia](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.02.24).

* Publication des composants principaux CIF version 1.8.0. Reportez-vous à [Composants principaux CIF](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.8.0) pour plus de détails.

## Cloud Manager {#cloud-manager}

### Date de publication {#release-date-cm}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.2.0 est le 11 février 2021.

### Nouveautés {#what-is-new-cloud-manager}


* Les clients Assets pourront désormais choisir quand et où déployer leur instance Brand Portal en libre-service via l’interface utilisateur de Cloud Manager. Pour un programme ordinaire (autre qu’un environnement de test) avec la solution Assets, Brand Portal peut désormais être configuré dans l’environnement de production. La mise en service ne peut être effectuée qu’une seule fois dans l’environnement de production.

* L’archétype de projet AEM utilisé dans Project et Sandbox Creation a été mis à jour vers la version 25.

* La liste des API obsolètes identifiées lors de l’analyse du code a été affinée afin d’inclure d’autres classes et méthodes obsolètes dans les dernières versions du SDK Cloud Service.

* Profil SonarQube pour Cloud Manager mis à jour afin de supprimer la règle Sonar squid:S2142. Cela n’entre plus en conflit avec les contrôles d’interruption de threads.

* L’interface utilisateur de Cloud Manager informera l’utilisateur qui ne pourra pas ajouter/mettre à jour temporairement le nom de domaine, car l’environnement associé est associé à un pipeline en cours d’exécution ou est actuellement en attente de l’étape d’approbation.

* Les propriétés définies dans les fichiers `pom.xml` clients avec le préfixe sonar seront désormais supprimées dynamiquement afin d’éviter les échecs d’analyse de génération et de qualité.

* L’interface utilisateur de Cloud Manager informe l’utilisateur qui ne peut pas sélectionner de certificat SSL pour le moment s’il est utilisé par un nom de domaine en cours de déploiement.

* Des règles de qualité du code supplémentaires ont été ajoutées pour couvrir les problèmes de compatibilité du Cloud Service.

### Correctifs {#bug-fixes-cloud-manager}

* La correspondance d’un certificat SSL avec un nom de domaine n’est plus sensible à la casse.

* L’interface utilisateur de Cloud Manager informe désormais un utilisateur si le certificat de clés privées ne respecte pas la limite de 2 048 bits avec un message d’erreur approprié.

* L’interface utilisateur de Cloud Manager informe l’utilisateur qui ne peut pas sélectionner de certificat SSL pour le moment s’il est utilisé par un nom de domaine en cours de déploiement.

* Dans certains cas, un problème interne peut entraîner le blocage de la suppression de l’environnement.

* Certains échecs de pipeline étaient incorrectement signalés comme des erreurs de pipeline.

## Outil de transfert de contenu {#content-transfer-tool}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu v1.2.4 est le 10 février 2021.

### Correctifs {#bug-fixes-ctt}

* Lors du mappage de plusieurs utilisateurs, les identifiants IMS de certains utilisateurs étaient incorrectement mappés. Ce problème a été résolu.

### Date de publication {#release-date-ctt-feb}

La date de publication de l’outil de transfert de contenu v1.2.2 est le 1er février 2021.

### Nouveautés de l’outil de transfert de contenu {#what-is-new-ctt}

* Fonctionnalité et interface utilisateur nouvelles ajoutées à l’outil de transfert de contenu - Outil de mappage des utilisateurs. Cette fonctionnalité mappe automatiquement les utilisateurs et les groupes existants avec leur identifiant IMS (Identity Management System) Adobe au cours de l’activité de migration de contenu.
Pour plus d’informations, consultez [Utilisation de l’outil de mappage des utilisateurs](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=fr).
* L’outil de transfert de contenu assure désormais la migration de tous les groupes et utilisateurs référencés dans le jeu de migration, y compris les enfants.
* Les utilisateurs sont autorisés à sélectionner certains chemins sous `/etc` lors de la création de jeux de migration.

## Analyseur de bonnes pratiques {#best-practices-analyzer}

### Date de publication {#release-date-bpa}

La date de publication de la version 2.1.2 de l’analyseur des bonnes pratiques est le 18 février 2021.

### Nouveautés de l’analyseur des bonnes pratiques {#what-is-new-bpa}

* Possibilité de détecter l’utilisation de l’implémentation d’AEM Forms et d’AEM Forms et d’indiquer les zones pertinentes pour la migration vers AEM Forms as a Cloud Service.
* Possibilité de détecter et de générer des rapports sur l’utilisation et le nombre de composants et de modèles personnalisés.
* Possibilité de détecter le type de magasin de noeuds et de magasin de données utilisé.
* Capacité à détecter l’utilisation de Dynamic Media.
* Possibilité de détecter la version Java utilisée.

## Outils de refactorisation du code {#code-refactoring-tools}

### Nouveautés des outils de refactorisation du code {#what-is-new-crt}

* Publication de la nouvelle version du plug-in AIO-CLI. La dernière version de ce module comprend plusieurs correctifs pour Repository Modernizer.
Pour en savoir plus sur ce module, voir [Expérience unifiée](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html?lang=fr#benefits) .

### Correctifs {#bug-fixes-crt}

* Plusieurs correctifs ont été apportés sur Repository Modernizer.
Voir [Ressource GitHub : aem-cloud-service-source-migration](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) pour plus d’informations.
