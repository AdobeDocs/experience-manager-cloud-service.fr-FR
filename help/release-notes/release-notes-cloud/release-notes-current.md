---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
translation-type: tm+mt
source-git-commit: 9743b5a80a8554e375561093e8554455b3a6b8f5
workflow-type: tm+mt
source-wordcount: '1588'
ht-degree: 13%

---

# Notes de mise à jour actuelles pour[!DNL Adobe Experience Manager]as a Cloud Service {#release-notes}

La section suivante décrit les Notes de mise à jour générales de la version actuelle (dernière) de [!DNL Experience Manager] en tant que Cloud Service.

>[!NOTE]
>A partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes ; par exemple, pour ceux de 2020, 2021 et ainsi de suite.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d&#39;informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de [!DNL Adobe Experience Manager] en tant que Cloud Service 2021.3.0 est le 25 mars 2021.
La version suivante (2021.4.0) sera publiée le 29 avril 2021.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

* Il est désormais possible d’activer [une version d’application web progressive (PWA) d’un site](/help/sites-cloud/authoring/features/enable-pwa.md) au niveau du projet grâce à une configuration simple.
* Extensions du modèle de fragment de contenu : permet désormais de définir des types de données de texte multiligne comme des listes à champs multiples.
* Améliorations de l’environnement de l’éditeur de fragments de contenu : les fragments enfants imbriqués s’affichent désormais dans un chemin de navigation et la vue des actions de publication, d’enregistrement et d’enregistrement et de sortie a été améliorée.

## [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouveautés de [!DNL Assets] {#what-is-new-assets}

<!-- TBD: refine this list of features and enh. for Feb release.

Customers using the Connected Assets feature can now easily view and track assets used on remote Sites instances. This affords customers a complete view of being used across all Sites powered pages, allowing for better tracking, management, and brand consistency.  

Indicators for expired, approved, and rejected statuses now available for assets in Column view.

Ability to select a root path. select if a minimum number of tags is required. 

Add a Boolean or radio widget type to metadata schema setup. -->

* [!DNL Experience Manager] étend la fonctionnalité Ressources connectées pour prendre en charge l’utilisation d’ [!DNL Dynamic Media] images dans les composants principaux pris en charge. Voir [utiliser les ressources connectées](/help/assets/use-assets-across-connected-assets-instances.md).
* Les administrateurs de Experience Manager peuvent planifier des acquisitions de ressources en vrac à une date ou une heure spécifique. En outre, les administrateurs peuvent planifier des ingérations récurrentes en fonction de la date et de l’heure. Voir [importation de ressources en vrac](/help/assets/add-assets.md#asset-bulk-ingestor).

### Correctifs de bogues dans [!DNL Assets] {#bug-fixes-assets}

* La page de copyright ne s’affiche pas lorsque vous tentez de télécharger plusieurs fichiers gérés par des droits d’auteur. (CQ-4314403)
* Lorsque vous choisissez de modifier un fichier INDD, la résolution change de manière inattendue. (CQ-4317376)
* Seule la dernière page du modèle d’InDesign figure dans le rendu PDF. (CQ-4317305)
* L’ouverture du sélecteur de balises est longue lorsque celui-ci fait partie d’un schéma de métadonnées complexe. (CQ-4316426)
* Lors du téléchargement d’un fichier portant le même nom de fichier qu’un fichier existant, la boîte de dialogue de conflit de noms ne s’affiche pas pour inviter l’utilisateur à créer une version. (CQ-4315424)
* Les propriétés des métadonnées du dossier peuvent être définies et enregistrées dans le menu contextuel de la page Propriétés d’un dossier. Bien que la sélection soit enregistrée dans le référentiel, elle ne s’affiche pas lorsque les propriétés de métadonnées du dossier sont à nouveau ouvertes. (CQ-4314429)
* Les fichiers dont les noms contiennent des espaces ou des caractères spéciaux sont téléchargés à l’aide du navigateur. (CQ-4318381)

## [!DNL Adobe Experience Manager Forms] comme  [!DNL Cloud Service] {#forms}

AEM Forms a aidé de nombreuses organisations à offrir d&#39;excellentes expériences d&#39;inscription et d&#39;inscription au programme au fil des ans. Ces expériences ont aidé les entreprises à convertir les pistes en ventes, à traiter les données client capturées, à proposer des expériences réactives basées sur le profil d’audience, etc. AEM Forms est désormais disponible en tant que service cloud.

Vous pouvez utiliser [AEM Forms en tant que Cloud Service](https://experienceleague.corp.adobe.com/docs/experience-manager-forms-cloud-service/forms/home.html) pour créer des formulaires numériques, connecter des formulaires à des sources de données existantes, intégrer des formulaires à Adobe Sign pour ajouter des signatures électroniques aux formulaires, générer un Document d’enregistrement (DE) pour archiver les formulaires envoyés en tant que fichiers PDF. Le service peut également convertir vos PDF forms existants en formulaires numériques. Outre les fonctionnalités standard d’AEM Forms, le service offre plusieurs fonctionnalités natives du cloud, telles que la mise à l’échelle automatique, un temps d’arrêt zéro pour les mises à niveau et un environnement de développement natif du cloud. Lisez [ce billet de blog](https://blog.adobe.com/en/publish/2021/03/11/experience-manager-forms-as-a-cloud-service.html) pour en savoir plus sur les capacités et les fonctionnalités de AEM Forms en tant que Cloud Service.

Vous pouvez contacter votre représentant d’Adobe pour une démonstration ou pour vous inscrire au service.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nouveautés {#what-is-new-commerce}

* Prise en charge de Magento 2.4.2

* Le composant des détails du produit peut désormais être utilisé et configuré sur n’importe quelle page de contenu.

* Publication du site de référence de CIF Venia – 2021.03.25 qui comprend les derniers composants principaux de CIF version 1.9.0. Pour plus d’informations, consultez [Site de référence de CIF Venia](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.03.25).

* Publication des composants principaux CIF version 1.9.0. Reportez-vous à [Composants principaux CIF](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.9.0) pour plus de détails.


## Cloud Manager {#c-manager}

Cette section décrit les Notes de mise à jour de Cloud Manager dans AEM en tant que Cloud Service 2021.4.0 et 2021.3.0.

### Date de publication {#release-date-cm-april}

La date de publication de Cloud Manager en tant que Cloud Service 2021.4.0 est le 08 avril 2021.
La prochaine version est prévue pour le 6 mai 2021.

### Nouveautés {#what-is-new-april}

* L’interface utilisateur met à jour les workflows d’Ajoute et de modification de Programme pour les rendre plus intuitifs.

* Un utilisateur disposant des autorisations requises peut désormais envoyer le point de terminaison du commerce via l’interface utilisateur.

* Les variables d’Environnement peuvent désormais être étendues à un service spécifique, qu’il s’agisse de l’auteur ou de la publication. Requiert AEM version `2021.03.5104.20210328T185548Z` ou supérieure.

* Le bouton **Gérer Git** s&#39;affiche sur la carte Pipelines même si aucun pipeline n&#39;a été configuré.

* La version de l’archétype de projet AEM utilisée par Cloud Manager a été mise à jour vers la version 27.

* Les projets de la console de développement des Adobes I/O créés par Cloud Manager ne peuvent plus être modifiés ou supprimés involontairement.

* Lorsqu’un utilisateur ajoute un nouvel environnement, il est informé qu’une fois qu’un environnement est créé, il ne peut plus être déplacé dans une autre région.

* Les variables d’Environnement peuvent désormais être étendues à un service spécifique, qu’il s’agisse de l’auteur ou de la publication. Requiert AEM version 2021.03.5104.20210328T185548Z ou supérieure.

* Le message d&#39;erreur lors du démarrage d&#39;un pipeline lorsqu&#39;un environnement a été supprimé a été clarifié.

* Les lots OSGi fournis par les projets Eclipse sont maintenant exclus de la règle `CQBP-84--dependencies`.

### Correctifs {#bug-fixes-cm-april}

* Lors de la modification de la page de contrôle d’expérience d’un pipeline, un chemin d’entrée commençant par une barre oblique `( / )` n’entraîne plus l’blocage de l’étape dans l’état en attente.

* Lors de la création d&#39;un nouveau pipeline de production, si aucun remplacement de contrôle du contenu n&#39;est ajouté par l&#39;utilisateur, la page d&#39;accueil par défaut n&#39;a pas été contrôlée.

* La gravité des problèmes de `CloudServiceIncompatibleWorkflowProcess` était incorrecte dans le fichier CSV de publication téléchargeable.

* La vérification `Runmode` produisait des faux positifs sur les noeuds non-dossiers.


### Date de publication {#release-date-cm-march}

La date de publication de Cloud Manager en tant que Cloud Service 2021.3.0 dans AEM est le 11 mars 2021.

### Nouveautés {#what-is-new-march}

* Les clients disposant d’environnements avec des configurations de nom de domaine personnalisé préexistantes pour [Listes autorisées IP](/help/implementing/cloud-manager/ip-allow-lists/check-ip-allow-list-status.md#pre-existing-cdn), [certificats SSL](/help/implementing/cloud-manager/managing-ssl-certifications/check-status-ssl-certificate.md#pre-existing-cdn) et [Noms de domaine personnalisés](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#pre-existing-cdn) verront un message sur leurs configurations existantes et pourront se servir eux-mêmes via l’interface utilisateur.

* Les utilisateurs disposant des autorisations requises peuvent désormais modifier un Programme, ce qui leur permet d’effectuer les opérations suivantes en libre-service :

   * Ajouter la solution Sites à un programme existant avec Ressources ou inversement.
   * Supprimez des sites ou des ressources d’un programme existant avec des sites et des ressources.
   * Ajoutez ensuite les droits de solution inutilisés à un programme existant ou en tant que nouveau Programme.

* **Le** libellé de mise à jour Push AEM sera désormais affiché pour les écrans  ** d’exécution de pipeline et  ** d’activité.

* Si un environnement est mis en veille prolongée, mais qu&#39;une mise à jour AEM est également disponible, l&#39;état **Hibernated** prévaudra sur **Mise à jour disponible**.

* Les utilisateurs peuvent désormais voir leur ou leurs rôles Cloud Manager en sélectionnant l’option &quot;Rôle(s) de Vue Cloud Manager&quot; après avoir accédé à l’icône Profil utilisateur (en haut à droite) de l’environnement de travail unifié.

* Pour plus de clarté, l&#39;étiquette **Demande d&#39;approbation** a été réétiquetée à **Approbation de production**.

* Le libellé **Version** a été réétiqueté en **Balise Git** dans l&#39;écran d&#39;exécution du pipeline de production.

* Les étiquettes qui définissent le comportement lorsque des mesures importantes ne respectent pas le seuil défini ont été réétiquetées pour refléter leur comportement réel : **Annuler immédiatement** et **Approuver immédiatement**.

* Les listes de classe et de méthode d’obsolescence ont été mises à jour en fonction de la version `2021.3.4997.20210303T022849Z-210225` du SDK Cloud Service AEM.

* Le pipeline de production de Cloud Manager inclut désormais la fonctionnalité [Tests d’interface utilisateur personnalisés](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing).

### Correctifs {#bug-fixes-cm-march}

* Le contrôle de version du package a parfois été ignoré lors de la mise à niveau AEM Push.

* Certains problèmes de qualité n&#39;ont pas été correctement détectés lorsque des paquets étaient incorporés dans d&#39;autres paquets.

* Dans des situations obscures, le nom de programme par défaut généré à l&#39;ouverture de la boîte de dialogue Ajouter le Programme peut être un duplicata d&#39;un nom de programme existant.

* Parfois, si l’utilisateur quitte la page d’exécution du pipeline immédiatement après le démarrage d’un pipeline, un message d’erreur s’affiche indiquant que l’action a échoué, bien que l’exécution ait effectivement début.

* L’étape de création a été inutilement redémarrée lorsque les compilations de clients ont généré des packs non valides.

* Il peut arriver que l’utilisateur voit un état &quot;principal&quot; vert en regard d’une Liste autorisée IP même si cette configuration n’a pas été déployée.

* Tous les pipelines de production existants seront automatiquement activés avec l’étape Contrôle de l’expérience.

## Outil de transfert de contenu {#content-transfer-tool}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu v1.3.4 est le 19 mars 2021.

### Correctifs {#bug-fixes-ctt}

* CTT ignorait le contenu des dossiers portant le même nom, mais avec un trait d’union dans le nom. Ce problème a été résolu.

### Date de publication {#release-date-ctt-march}

La date de publication de l’outil de transfert de contenu v1.3.0 est le 4 mars 2021.

### Nouveautés de l’outil de transfert de contenu {#what-is-new-ctt-march}

* Le CTT s’installe désormais dans `/apps` au lieu de `/libs` les signets du navigateur vers certaines pages peuvent ne plus être valides.
* Une fois le CTT installé, l’utilisateur doit parcourir un niveau supplémentaire pour accéder à la page de transfert de contenu. Voir [Utilisation de l’outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html) pour plus d’informations.

### Correctifs {#bug-fixes-ctt-march}

* Lors de la migration de contenu à partir d’un chemin d’accès spécifique, le CTT extrayait des ressources non liées. Ce problème a été résolu

## Analyseur de bonnes pratiques {#best-practices-analyzer}

### Date de publication {#release-date-bpa}

La date de publication pour la version 2.1.12 de Best Practices Analyzer est le 12 avril 2021.

### Correctifs {#bug-fixes-bpa-april}

* Des lignes de duplicata ont été vues dans le BPA rapporté. Ce problème a été résolu.
* L&#39;interface utilisateur BPA de AEM version 6.4.2 affichait une erreur JS qui désactivait le bouton Générer le rapport. Ce problème a été résolu


## Outils de refactorisation du code {#code-refactoring-tools}

### Nouveautés des outils de refactorisation de code {#what-is-new-crt}

* Nouvelles fonctionnalités et améliorations de Repository Modernizer. Reportez-vous à la [ressource GitHub : Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) pour la dernière version.
   * Normalisez les configurations OSGi (à l’exception des configurations RepoInit) au format .cfg.json préféré.
   * Renommez les dossiers de configuration OSGi au format spécifié.
   * Générez le projet ui.apps.structure.
   * Créez le module d&#39;analyse.

* Nouvelles fonctionnalités et améliorations pour Dispatcher Converter. Reportez-vous à la [ressource GitHub : Convertisseur de répartiteur](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter)
   * Création de fichiers distincts pour différentes inclusions au lieu de mettre en file d’attente le contenu.
   * Capacité à gérer à la fois le chemin d’accès des dossiers vhosts et le chemin d’accès aux fichiers vhost.
   * Génération de fichiers de batterie avec des configurations client importantes dans une plage de 600 et plus.
