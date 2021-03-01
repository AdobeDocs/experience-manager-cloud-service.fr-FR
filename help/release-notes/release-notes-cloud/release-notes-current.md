---
title: Notes de mise à jour actuelles pour  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour actuelles pour  [!DNL Adobe Experience Manager]  as a Cloud Service.
translation-type: tm+mt
source-git-commit: 7c9eea58b8e42902842f5e9658f0fa677f1dc51d
workflow-type: tm+mt
source-wordcount: '1064'
ht-degree: 9%

---


# Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante décrit les Notes de mise à jour générales de la version actuelle (dernière) de [!DNL Experience Manager] en tant que Cloud Service.

>[!NOTE]
>A partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes ; par exemple, pour ceux de 2020, 2021 et ainsi de suite.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d&#39;informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de [!DNL Adobe Experience Manager] en tant que Cloud Service 2021.2.0 est le 25 février 2021.
La version suivante (2021.3.0) sera publiée le 25 mars 2021.

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

## Nouveautés de [!DNL Assets] {#what-is-new-assets}

* Dans [!DNL Brand Portal], un nouveau paramètre de téléchargement est introduit, qui vous permet de créer un dossier distinct pour chaque fichier lors du téléchargement de dossiers, de collections, etc. voir [paramètres de téléchargement](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/download/brand-portal-download-assets.html).

<!-- TBD: refine this list of features and enh. for Feb release.

Customers using the Connected Assets feature can now easily view and track assets used on remote Sites instances. This affords customers a complete view of being used across all Sites powered pages, allowing for better tracking, management, and brand consistency.  -->

## Correctifs de bogues dans [!DNL Assets] {#bug-fixes-assets}

* Lorsqu’une nouvelle version d’une ressource existante est créée après la résolution du conflit d’affectation de nom, les métadonnées de la ressource d’origine sont remplacées. (CQ-4313594)
* Lors de l’impression d’un fichier avec un texte d’annotation long, le texte de l’annotation est ajusté, même si de l’espace est disponible. (CQ-4314101)
* Lorsque plusieurs ressources sont sélectionnées pour mettre à jour les propriétés, il arrive parfois qu’une erreur se produise ou que les propriétés d’une ressource désélectionnée soient mises à jour. (CQ-4316532)
* Lorsque vous tentez d&#39;ouvrir [!UICONTROL le rail de recherche des administrateurs des ressources], la page reste vide et le fait de cliquer sur [!UICONTROL Modifier] > [!UICONTROL Paramètres] génère une erreur. (CQ-4315079)

## Cloud Manager {#cloud-manager}

### Date de publication {#release-date-cm}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.2.0 est le 11 février 2021.

### Nouveautés {#what-is-new-cloud-manager}


* Les clients du module Ressources peuvent désormais choisir quand et où déployer leur instance de portail de marque en libre-service via l’interface utilisateur de Cloud Manager. Pour un programme standard (non sandbox) avec la solution Ressources, le portail de marque peut désormais être mis en service sur l’environnement de production. L’approvisionnement ne peut être effectué qu’une seule fois sur l’environnement Production.

* L&#39;archétype de projet AEM utilisé dans Project and Sandbox Creation a été mis à jour vers la version 25.

* La liste des API obsolètes identifiées lors de l’analyse du code a été affinée afin d’inclure d’autres classes et méthodes obsolètes dans les dernières versions du SDK Cloud Service.

* Profil SonarQube pour Cloud Manager mis à jour pour supprimer la règle Sonar squid:S2142. Ceci ne sera plus en conflit avec les contrôles Interruption du thread.

* L’interface utilisateur de Cloud Manager informe l’utilisateur qui ne peut pas temporairement ajouter/mettre à jour le nom de domaine car l’environnement associé dispose soit d’un pipeline en cours d’exécution qui lui est associé, soit de l’étape d’approbation en attente.

* Les propriétés définies dans les fichiers `pom.xml` client précédés d&#39;un sonar seront désormais supprimées dynamiquement afin d&#39;éviter les échecs d&#39;analyse de la génération et de la qualité.

* L’interface utilisateur de Cloud Manager informe l’utilisateur qui ne peut pas sélectionner de certificat SSL pour le moment s’il est utilisé par un nom de domaine en cours de déploiement.

* Des règles de qualité de code supplémentaires ont été ajoutées pour couvrir les problèmes de compatibilité des Cloud Service.

### Correctifs {#bug-fixes-cloud-manager}

* La correspondance d’un certificat SSL avec un nom de domaine n’est plus sensible à la casse.

* L’interface utilisateur de Cloud Manager informe désormais un utilisateur si les clés privées du certificat ne respectent pas la limite de 2 048 bits avec un message d’erreur approprié.

* L’interface utilisateur de Cloud Manager informe l’utilisateur qui ne peut pas sélectionner de certificat SSL pour le moment s’il est utilisé par un nom de domaine en cours de déploiement.

* Dans certains cas, un problème interne peut bloquer la suppression d’environnement.

* Certains échecs de pipeline étaient incorrectement signalés comme des erreurs de pipeline.

## Outil de transfert de contenu {#content-transfer-tool}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu v1.2.4 est le 10 février 2021.

### Correctifs {#bug-fixes-ctt}

* Lors du mappage de plusieurs utilisateurs, les ID IMS de certains utilisateurs étaient incorrectement mappés. Ce problème a été résolu.

### Date de publication {#release-date-ctt-feb}

La date de publication de l’outil de transfert de contenu v1.2.2 est le 01 février 2021.

### Nouveautés de l’outil de transfert de contenu {#what-is-new-ctt}

* Nouvelle fonctionnalité et interface utilisateur ajoutées à l’outil de transfert de contenu - Outil de mappage des utilisateurs. Cette fonctionnalité mappe automatiquement les utilisateurs et groupes existants à leurs identifiants système Identity Management Adobe dans le cadre de l’activité de migration de contenu.
Pour plus d&#39;informations, consultez [Utilisation de l&#39;outil de mappage utilisateur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html).
* L’outil de transfert de contenu migre désormais tous les groupes et utilisateurs référencés dans le jeu de migration, y compris les enfants.
* Les utilisateurs sont autorisés à sélectionner certains chemins sous `/etc` lors de la création de jeux de migration.

## Analyseur de bonnes pratiques {#best-practices-analyzer}

### Date de publication {#release-date-bpa}

La date de publication de la version 2.1.2 de Best Practices Analyzer est le 18 février 2021.

### Nouveautés de l’analyseur des meilleures pratiques {#what-is-new-bpa}

* Capacité à détecter l’utilisation de l’implémentation AEM Forms et AEM Forms et à indiquer les zones pertinentes pour la migration vers AEM Forms en tant que Cloud Service.
* Capacité à détecter et à générer des rapports sur l’utilisation et le nombre de composants et de modèles personnalisés.
* Capacité à détecter le type de stockage de noeuds et de stockage de données utilisé.
* Capacité à détecter l&#39;utilisation de Dynamic Media.
* Capacité à détecter la version Java utilisée.

## Outils de refactorisation du code {#code-refactoring-tools}

### Nouveautés des outils de refactorisation de code {#what-is-new-crt}

* Nouvelle version du module externe AIO-CLI publiée. La dernière version de ce module comprend plusieurs correctifs pour Repository Modernizer.
Consultez [Expérience unifiée](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html?lang=en#benefits) pour en savoir plus sur ce module externe.

### Correctifs {#bug-fixes-crt}

* Plusieurs correctifs de bogues ont été apportés à Repository Modernizer.
Reportez-vous à la [ressource GitHub : aem-cloud-service-source-migration](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) pour plus d’informations.








