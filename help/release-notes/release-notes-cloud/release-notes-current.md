---
title: Notes de mise à jour actuelles pour  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour actuelles pour  [!DNL Adobe Experience Manager]  as a Cloud Service.
translation-type: tm+mt
source-git-commit: fb0700f2b25917dd97381e0270995d7cef646edb
workflow-type: tm+mt
source-wordcount: '1574'
ht-degree: 11%

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

* **[Le composant](/help/implementing/developing/hybrid/remote-page.md)** RemotePage : Prise en charge Ajoutée de l’affichage et de la modification des SPA externes dans AEM utilisation.

* **[Modification d&#39;un SPA externe dans AEM](/help/implementing/developing/hybrid/editing-external-spa.md)** : Possibilité Ajoutée de télécharger une application autonome d’une seule page sur une instance AEM, d’ajouter des sections de contenu modifiables et d’activer la création.

<!--
### Progressive Web Apps (PWAs) {#pwa}

* [A Progressive Web App (PWA) version of a site](/help/sites-cloud/authoring/features/enable-pwa.md)  can now be enabled at the project level via simple configuration.
-->

## [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

## Nouveautés de [!DNL Assets] {#what-is-new-assets}

* Les entreprises peuvent désormais sources d&#39;actifs à l&#39;aide de [!DNL Brand Portal]. La fonction d&#39;approvisionnement des ressources tire parti de [!DNL Brand Portal] pour aider les clients à s&#39;engager auprès des utilisateurs de l&#39;agence à trouver des ressources pour de nouvelles campagnes marketing, des photos et des projets. Reportez-vous à [l’approvisionnement en ressources dans  [!DNL Brand Portal]](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html).

* Le rapport d&#39;utilisation de [!DNL Brand Portal] affiche désormais uniquement les utilisateurs principaux. Les utilisateurs inactifs ne s’affichent pas maintenant. Les utilisateurs principaux sont ceux dont le compte est affecté à un profil de produits dans le [!DNL Admin Console]. Voir [[!DNL Brand Portal] rapports](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/admin-tools/brand-portal-reports.html).

* Dans [!DNL Brand Portal], un nouveau paramètre de téléchargement est introduit, qui vous permet de créer un dossier distinct pour chaque fichier lors du téléchargement de dossiers, de collections, etc. Voir [paramètres de téléchargement](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/download/brand-portal-download-assets.html).

<!-- TBD: refine this list of features and enh. for Feb release.

Customers using the Connected Assets feature can now easily view and track assets used on remote Sites instances. This affords customers a complete view of being used across all Sites powered pages, allowing for better tracking, management, and brand consistency.  -->

## Correctifs de bogues dans [!DNL Assets] {#bug-fixes-assets}

* Lorsqu’une nouvelle version d’une ressource existante est créée après la résolution du conflit d’affectation de nom, les métadonnées de la ressource d’origine sont remplacées. (CQ-4313594)
* Lors de l’impression d’un fichier avec un texte d’annotation long, le texte de l’annotation est ajusté, même si de l’espace est disponible. (CQ-4314101)
* Lorsque plusieurs ressources sont sélectionnées pour mettre à jour les propriétés, il arrive parfois qu’une erreur se produise ou que les propriétés d’une ressource désélectionnée soient mises à jour. (CQ-4316532)
* Lorsque vous tentez d&#39;ouvrir [!UICONTROL le rail de recherche des administrateurs des ressources], la page reste vide et le fait de cliquer sur [!UICONTROL Modifier] > [!UICONTROL Paramètres] génère une erreur. (CQ-4315079)

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nouveautés {#what-is-new-commerce}

* Gestion de l&#39;expérience des produits : Enrichissez les pages du catalogue de produits individuellement avec les fragments d’expérience.

* Propriétés étendues de la console de produits pour afficher les ressources liées et les fragments d’expérience, y compris les actions permettant d’accéder rapidement au contenu associé.

* Site de référence de CIF Venia - 2021.02.24 qui comprend la dernière version des composants principaux de CIF version 1.8.0. Pour plus d&#39;informations, voir [Site de référence de CIF Venia](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.02.24).

* Publication des composants principaux CIF version 1.8.0. Reportez-vous à [Composants principaux CIF](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.8.0) pour plus de détails.

## Cloud Manager {#cloud-manager}

Cette page présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.3.0.

## Date de publication {#release-date-cm-march}

La date de publication de Cloud Manager en tant que Cloud Service 2021.3.0 dans AEM est le 11 mars 2021.


### Nouveautés {#what-is-new-march}

* Les clients disposant d’environnements avec des configurations CDN préexistantes pour les Listes autorisées IP, les certificats SSL et les noms de domaine personnalisés verront un message sur leurs configurations existantes et pourront se servir librement via l’interface utilisateur. Les utilisateurs peuvent désormais :
   * Ajouter la solution Sites à un programme existant avec Ressources (ou inversement).
   * Supprimez des sites (ou des ressources) d’un programme existant avec des sites et des ressources.
   * Ajoutez ensuite les droits de solution inutilisés à un programme existant ou en tant que nouveau Programme.

* Les utilisateurs disposant des autorisations requises peuvent désormais modifier le Programme, ce qui leur permet d’effectuer les opérations suivantes en libre-service.

* L’étiquette &quot;Mise à jour AEM Push&quot; s’affiche désormais pour les écrans d’exécution du pipeline et d’Activité.

* Si un environnement est mis en veille prolongée mais qu’une mise à jour AEM est également disponible, l’état &quot;Hébergé&quot; prévaudra sur &quot;Mise à jour disponible&quot;.

* Les utilisateurs peuvent désormais voir leur ou leurs rôles Cloud Manager en sélectionnant l’option &quot;Rôle(s) de Vue Cloud Manager&quot; après avoir accédé à l’icône Profil utilisateur (en haut à droite) de l’environnement de travail unifié.

* L&#39;étiquette &quot;Demande d&#39;approbation&quot; a été réétiquetée &quot;Approbation de production&quot; pour plus de clarté.

* Le libellé &quot;Version&quot; a été réétiqueté en &quot;Balise Git&quot; dans l’écran d’exécution du pipeline de production.

* Les étiquettes qui définissent le comportement lorsque des mesures importantes ne respectent pas le seuil défini ont été réétiquetées pour refléter leur comportement réel : Annuler immédiatement et Approuver immédiatement.

* Les listes de classe et de méthode d’obsolescence ont été mises à jour en fonction de la version `2021.3.4997.20210303T022849Z-210225` du SDK Cloud Service AEM.

* Le pipeline de production de Cloud Manager inclut désormais la fonctionnalité de test d’interface utilisateur personnalisée.

### Correctifs {#bug-fixes-cm-march}

* Le contrôle de version du package a parfois été ignoré lors de la mise à niveau AEM Push.

* Certains problèmes de qualité n&#39;ont pas été correctement détectés lorsque des paquets étaient incorporés dans d&#39;autres paquets.

* Dans des situations obscures, le nom de programme par défaut généré à l&#39;ouverture de la boîte de dialogue Ajouter le Programme peut être un duplicata d&#39;un nom de programme existant.

* Parfois, si l’utilisateur quitte la page d’exécution du pipeline immédiatement après le démarrage d’un pipeline, un message d’erreur s’affiche indiquant que l’action a échoué, bien que l’exécution ait effectivement début.

* L’étape de création a été inutilement redémarrée lorsque les compilations de clients ont généré des packs non valides.

* Il peut arriver que l’utilisateur voit un état &quot;principal&quot; vert en regard d’une Liste autorisée IP même si cette configuration n’a pas été déployée.

* Tous les pipelines de production existants seront automatiquement activés avec l’étape Contrôle de l’expérience.


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

### Date de publication {#release-date-ctt-march}

La date de publication de l’outil de transfert de contenu v1.3.0 est le 4 mars 2021.

### Nouveautés de l’outil de transfert de contenu {#what-is-new-ctt-march}

* Le CTT s’installe désormais dans `/apps` au lieu de `/libs` les signets du navigateur vers certaines pages peuvent ne plus être valides.
* Une fois le CTT installé, l’utilisateur doit parcourir un niveau supplémentaire pour accéder à la page de transfert de contenu. Voir [Utilisation de l’outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html) pour plus d’informations.

### Correctifs {#bug-fixes-ctt-march}

* Lors de la migration de contenu à partir d’un chemin d’accès spécifique, le CTT extrayait des ressources non liées. Ce problème a été résolu


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








