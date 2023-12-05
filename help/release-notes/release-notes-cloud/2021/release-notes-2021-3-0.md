---
title: Notes de mise à jour de la version 2021.3.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
description: « Notes de mise à jour d’[!DNL Adobe Experience Manager] as a Cloud Service version 2021.3.0. »
exl-id: 0c07364c-ba25-4081-8e35-3c1c84ed556f
source-git-commit: abe5f8a4b19473c3dddfb79674fb5f5ab7e52fbf
workflow-type: tm+mt
source-wordcount: '1271'
ht-degree: 87%

---

# Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour générales de la version actuelle (la plus récente) d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes ; par exemple, celles de 2020, 2021 et ainsi de suite.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication d’[!DNL Adobe Experience Manager] as a Cloud Service version 2021.3.0 est le 25 mars 2021.
La version suivante (2021.4.0) sera publiée le 29 avril 2021.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

* Il est désormais possible d’activer [une version d’application web progressive (PWA) d’un site](/help/sites-cloud/authoring/features/enable-pwa.md) au niveau du projet grâce à une configuration simple.
* Extensions de modèle de fragment de contenu : elles permettent désormais de définir des types de données de texte multiligne en tant que listes à champs multiples.
* Améliorations de l’expérience utilisateur de l’éditeur de fragments de contenu : les fragments enfants imbriqués s’affichent désormais dans le chemin de navigation et offrent une vue améliorée des actions (publication, enregistrement, enregistrement et sortie).

## [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouveautés d’[!DNL Assets]  {#what-is-new-assets}

<!-- TBD: refine this list of features and enh. for Feb release.

Customers using the Connected Assets feature can now easily view and track assets used on remote Sites instances. This affords customers a complete view of being used across all Sites powered pages, allowing for better tracking, management, and brand consistency.  

Indicators for expired, approved, and rejected statuses now available for assets in Column view.

Ability to select a root path. select if a minimum number of tags is required. 

Add a Boolean or radio widget type to metadata schema setup. -->

* [!DNL Experience Manager] étend la fonctionnalité Ressources connectées pour prendre en charge l’utilisation des images [!DNL Dynamic Media] dans les composants principaux pris en charge. Voir [Utilisation des ressources connectées](/help/assets/use-assets-across-connected-assets-instances.md).
* Les administrateurs d’Experience Manager peuvent planifier des ingestions de ressources en masse à une date ou une heure spécifique. En outre, ils peuvent planifier des ingestions récurrentes en fonction de la date et de l’heure. Voir la section [Ingestion de ressources en bloc](/help/assets/add-assets.md#asset-bulk-ingestor).

### Bogues corrigés dans [!DNL Assets] {#bug-fixes-assets}

* La page de copyright ne s’affiche pas lorsque vous tentez de télécharger plusieurs ressources assorties de droits d’auteur. (CQ-4314403)
* Lorsque vous choisissez de modifier un fichier INDD, la résolution change de manière inattendue. (CQ-4317376)
* Seule la dernière page du modèle InDesign figure dans le rendu PDF. (CQ-4317305)
* L’ouverture du sélecteur de balises prend du temps lorsque le sélecteur fait partie d’un schéma de métadonnées complexe. (CQ-4316426)
* Lors du chargement d’une ressource portant le même nom de fichier que celui existant, la boîte de dialogue de conflit de noms ne s’affiche pas pour inviter l’utilisateur à créer une version. (CQ-4315424)
* Les propriétés de métadonnées de dossier peuvent être définies et enregistrées à partir du menu contextuel dans la page Propriétés d’un dossier. Bien que la sélection soit enregistrée dans le référentiel, elle ne s’affiche pas lorsque les propriétés des métadonnées de dossier sont à nouveau ouvertes. (CQ-4314429)
* Les ressources dont le nom de fichier contient des espaces ou des caractères spéciaux sont chargées à l’aide du navigateur. (CQ-4318381)

## [!DNL Adobe Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

AEM Forms a aidé de nombreuses entreprises à produire de superbes expériences d’intégration et d’inscription au cours des années. Ces expériences ont permis à ces entreprises de convertir des prospects en ventes, de traiter des données client capturées, de fournir des expériences réactives en fonction du profil d’audience, etc. Désormais, AEM Forms est disponible en tant que service cloud.

Vous pouvez utiliser [AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/home.html?lang=fr) pour créer des formulaires numériques, connecter des formulaires à des sources de données existantes, intégrer des formulaires avec Adobe Sign pour ajouter des signatures électroniques aux formulaires, générer un document d’enregistrement pour archiver les formulaires envoyés sous forme de fichiers PDF. Le service peut également convertir vos formulaires PDF existants en versions numériques. Outre les fonctionnalités AEM Forms standard, le service propose plusieurs fonctionnalités natives dans le cloud, telles que la mise à l’échelle automatique, le zéro temps d’arrêt pour les mises à niveau et l’environnement de développement natif dans le cloud.

Vous pouvez contacter votre représentant Adobe pour une démonstration ou pour vous abonner au service.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nouveautés {#what-is-new-commerce}

* Prise en charge d’Adobe Commerce 2.4.2

* Le composant Détails du produit peut désormais être utilisé et configuré sur n’importe quelle page de contenu.

* Publication CIF site de référence Venia - 2021.03.25 qui comprend la dernière version de CIF Core Components v1.9.0. Voir [Site de référence Venia CIF](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.03.25) pour plus d’informations.

* Publication CIF composants principaux v1.9.0. Voir [CIF composants principaux](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.9.0) pour plus d’informations.


## Cloud Manager {#cloud-manager}

Cette section présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.3.0.

## Date de publication {#release-date-cm-march}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.3.0 est le 11 mars 2021.
La prochaine version est prévue pour le 8 avril 2021.

### Nouveautés {#what-is-new-march}

* Clients avec des environnements avec des configurations de nom de domaine personnalisé préexistantes pour [LISTES AUTORISÉES IP](/help/implementing/cloud-manager/ip-allow-lists/managing-ip-allow-lists.md#pre-existing-cdn), [Certificats SSL](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md#pre-existing-cdn) et [Noms de domaine personnalisés](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#pre-existing-cdn) consultez un message à propos de leurs configurations existantes et peuvent être en libre-service au moyen de l’interface utilisateur .

* Les utilisateurs et utilisatrices disposant des autorisations requises peuvent désormais modifier un programme, ce qui leur permet d’effectuer les opérations suivantes en libre-service :

   * Ajoutez la solution Sites à un programme existant avec Assets ou inversement.
   * Supprimer Sites ou Assets d’un programme existant contenant à la fois Sites et Assets.
   * Ajouter un deuxième droit non utilisé sur une solution à un programme existant ou à titre de nouveau programme.

* Le libellé **Mise à jour Push AEM** sera désormais affiché pour les écrans *Exécution du pipeline* et *Activité*.

* Si un environnement est mis en veille prolongée, mais qu’une mise à jour AEM est également disponible, l’état **En veille** prévaudra sur **Mise à jour disponible**.

* Les utilisateurs peuvent désormais voir leur(s) rôle(s) Cloud Manager en sélectionnant l’option Afficher les rôles de Cloud Manager après avoir accédé à l’icône de Profil utilisateur (en haut à droite) du shell unifié.

* Pour plus de clarté, l’étiquette **Application à approuver** a été réétiquetée à **Approbation de production**.

* Le libellé **Version** a été renommé **Balise Git** dans l’écran d’exécution du pipeline de production.

* Les libellés qui définissent le comportement lorsque des mesures importantes ne respectent pas le seuil défini ont été réétiquetées afin de refléter leur comportement réel : **Annuler immédiatement** et **Approuver immédiatement**.

* Les listes de classe et de méthode d’obsolescence ont été mises à jour en fonction de la version `2021.3.4997.20210303T022849Z-210225` du SDK AEM Cloud Service.

* Le pipeline de production de Cloud Manager inclut désormais la fonctionnalité de [test d’interface utilisateur personnalisée](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing).

### Correctifs {#bug-fixes-cm-march}

* Le contrôle de version du package était parfois ignoré lors d’une mise à niveau Push d’AEM.

* Certains problèmes de qualité n’étaient pas été correctement détectés lorsque des packages étaient incorporés dans d’autres packages.

* Dans des situations obscures, le nom de programme par défaut généré à l’ouverture de la boîte de dialogue Ajouter le programme pouvait être un doublon d’un nom de programme existant.

* Parfois, si l’utilisateur quitte la page d’exécution du pipeline immédiatement après le démarrage d’un pipeline, un message d’erreur s’affiche indiquant que l’action a échoué, bien que l’exécution ait effectivement démarré.

* L’étape de création était inutilement redémarrée lorsque les compilations de clients généraient des packages non valides.

* Il peut arriver que l’utilisateur voit un état « actif » vert en regard d’une liste d’adresses IP autorisées même si cette configuration n’a pas été déployée.

* Tous les pipelines de production existants sont automatiquement activés avec l’étape d’audit de l’expérience.

## Outil de transfert de contenu {#content-transfer-tool}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu version v1.3.4 est le 19 mars 2021.

### Correctifs {#bug-fixes-ctt}

* CTT ignorait le contenu des dossiers portant le même nom, mais dont le nom comportait un trait d’union. Ce problème a été résolu.

### Date de publication {#release-date-ctt-march}

La date de publication de l’outil de transfert de contenu version v1.3.0 est le 4 mars 2021.

### Nouveautés de l’outil de transfert de contenu {#what-is-new-ctt-march}

* L’outil de transfert de contenu (CTT) s’installe désormais dans `/apps` au lieu de `/libs` ; les signets du navigateur vers certaines pages ne sont plus nécessairement valides.
* Une fois CTT installé, l’utilisateur doit parcourir un niveau supplémentaire pour accéder à la page de transfert de contenu. Voir [Utilisation de l’outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=fr) pour plus d’informations.

### Correctifs {#bug-fixes-ctt-march}

* Lors de la migration de contenus à partir d’un chemin d’accès spécifique, CTT extrayait des ressources non liées. Ce problème a été résolu

## Analyseur des bonnes pratiques {#best-practices-analyzer}

### Date de publication {#release-date-bpa}

La date de publication de l’analyseur de bonnes pratiques v2.1.8 est le 22 mars 2021.

### Nouveautés de l’analyseur de bonnes pratiques {#what-is-new-bpa}

* Possibilité de filtrer les résultats d’ACS Commons du rapport BPA dans l’interface utilisateur et du rapport exporté en tant que fichier CSV.

## Outils de refactorisation du code {#code-refactoring-tools}

### Nouveautés des outils de refactorisation du code {#what-is-new-crt}

* Nouvelles fonctionnalités et améliorations de Repository Modernizer. Voir [Ressource GitHub : Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) pour la dernière version.
   * Normalisez les configurations OSGi (à l’exception des configurations RepoInit) au format .cfg.json préféré.
   * Renommez les dossiers de configuration OSGi au format spécifié.
   * Générez le projet ui.apps.structure.
   * Créez le module d’analyse.

* Nouvelles fonctionnalités et améliorations pour Dispatcher Converter. Voir [Ressource GitHub : convertisseur du Dispatcher](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter)
   * Création de fichiers distincts pour différentes inclusions au lieu de mettre le contenu en file d’attente.
   * Capacité à gérer à la fois le chemin d’accès des dossiers vhosts et le chemin d’accès aux fichiers vhost.
   * Génération de fichiers en batterie avec des configurations client importantes dans une plage de 600 et plus.
