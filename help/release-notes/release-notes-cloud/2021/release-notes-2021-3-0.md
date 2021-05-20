---
title: Notes de mise à jour de la version 2021.3.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour d’[!DNL Adobe Experience Manager] as a Cloud Service version 2021.3.0.
source-git-commit: 63b7c11683425cc20851ee5a16ee099511429b17
workflow-type: tm+mt
source-wordcount: '1318'
ht-degree: 14%

---


# Notes de mise à jour actuelles pour[!DNL Adobe Experience Manager]as a Cloud Service {#release-notes}

La section suivante présente les notes de mise à jour générales de la version actuelle (la plus récente) de [!DNL Experience Manager] en tant que Cloud Service.

>[!NOTE]
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes. par exemple, pour ceux de 2020, 2021 et ainsi de suite.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de [!DNL Adobe Experience Manager] en tant que Cloud Service 2021.3.0 est le 25 mars 2021.
La version suivante (2021.4.0) sera publiée le 29 avril 2021.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

* Il est désormais possible d’activer [une version d’application web progressive (PWA) d’un site](/help/sites-cloud/authoring/features/enable-pwa.md) au niveau du projet grâce à une configuration simple.
* Extensions de modèle de fragment de contenu : permettent désormais de définir des types de données de texte multiligne en tant que listes à champs multiples.
* Améliorations de l’expérience utilisateur de l’éditeur de fragments de contenu : les fragments enfants imbriqués s’affichent désormais dans le chemin de navigation et offrent une vue améliorée des actions de publication, d’enregistrement et d’enregistrement et de sortie.

## [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouveautés de [!DNL Assets] {#what-is-new-assets}

<!-- TBD: refine this list of features and enh. for Feb release.

Customers using the Connected Assets feature can now easily view and track assets used on remote Sites instances. This affords customers a complete view of being used across all Sites powered pages, allowing for better tracking, management, and brand consistency.  

Indicators for expired, approved, and rejected statuses now available for assets in Column view.

Ability to select a root path. select if a minimum number of tags is required. 

Add a Boolean or radio widget type to metadata schema setup. -->

* [!DNL Experience Manager] étend la fonctionnalité Ressources connectées pour prendre en charge l’utilisation des  [!DNL Dynamic Media] images dans les composants principaux pris en charge. Voir [Utilisation des ressources connectées](/help/assets/use-assets-across-connected-assets-instances.md).
* Les administrateurs de Experience Manager peuvent planifier des assimilations de ressources en masse à une date ou une heure spécifique. En outre, les administrateurs peuvent planifier des ingérations récurrentes en fonction de la date et de l’heure. Voir [ingestion de ressources en bloc](/help/assets/add-assets.md#asset-bulk-ingestor).

### Correctifs de bogues dans [!DNL Assets] {#bug-fixes-assets}

* La page de copyright ne s’affiche pas lorsque vous tentez de télécharger plusieurs ressources gérées par les droits d’auteur. (CQ-4314403)
* Lorsque vous choisissez de modifier un fichier INDD, la résolution change de manière inattendue. (CQ-4317376)
* Seule la dernière page du modèle d’InDesign figure dans le rendu PDF. (CQ-4317305)
* L’ouverture du sélecteur de balises prend du temps lorsque le sélecteur fait partie d’un schéma de métadonnées complexe. (CQ-4316426)
* Lors du téléchargement d’une ressource portant le même nom de fichier que celui existant, la boîte de dialogue de conflit de noms ne s’affiche pas pour inviter l’utilisateur à créer une version. (CQ-4315424)
* Les propriétés de métadonnées de dossier peuvent être définies et enregistrées à partir du menu contextuel dans la page Propriétés d’un dossier. Bien que la sélection soit enregistrée dans le référentiel, elle ne s’affiche pas lorsque les propriétés de métadonnées du dossier sont à nouveau ouvertes. (CQ-4314429)
* Les ressources dont le nom de fichier contient des espaces ou des caractères spéciaux sont téléchargées à l’aide du navigateur. (CQ-4318381)

## [!DNL Adobe Experience Manager Forms] as a  [!DNL Cloud Service] {#forms}

AEM Forms a aidé de nombreuses entreprises à offrir de superbes expériences d’intégration et d’inscription au cours des années. Ces expériences ont permis aux entreprises de convertir des prospects en ventes, de traiter des données client capturées, de fournir des expériences réactives en fonction du profil d’audience, etc. Désormais, AEM Forms est disponible en tant que service cloud.

Vous pouvez utiliser [AEM Forms as aCloud Service](https://experienceleague.corp.adobe.com/docs/experience-manager-forms-cloud-service/forms/home.html) pour créer des formulaires numériques, connecter des formulaires à des sources de données existantes, intégrer des formulaires à Adobe Sign pour ajouter des signatures électroniques aux formulaires, générer un document d’enregistrement (DoR) afin d’archiver les formulaires envoyés sous forme de fichiers PDF. Le service peut également convertir vos PDF forms existants en formulaires numériques. Outre les fonctionnalités AEM Forms standard, le service propose plusieurs fonctionnalités natives dans le cloud, telles que la mise à l’échelle automatique, le zéro temps d’arrêt pour les mises à niveau et l’environnement de développement natif dans le cloud. Lisez [cet article de blog](https://blog.adobe.com/en/publish/2021/03/11/experience-manager-forms-as-a-cloud-service.html) pour en savoir plus sur les fonctionnalités d’AEM Forms en tant que Cloud Service.

Vous pouvez contacter votre représentant d’Adobe pour une démonstration ou pour vous inscrire au service.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nouveautés {#what-is-new-commerce}

* Prise en charge de Magento 2.4.2

* Le composant Détails du produit peut désormais être utilisé et configuré sur n’importe quelle page de contenu.

* Publication du site de référence de CIF Venia – 2021.03.25 qui comprend les derniers composants principaux de CIF version 1.9.0. Pour plus d’informations, consultez [Site de référence de CIF Venia](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.03.25).

* Publication des composants principaux CIF version 1.9.0. Reportez-vous à [Composants principaux CIF](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.9.0) pour plus de détails.


## Cloud Manager {#cloud-manager}

Cette section présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service 2021.3.0.

## Date de publication {#release-date-cm-march}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.3.0 est le 11 mars 2021.
La prochaine version est prévue pour le 8 avril 2021.

### Nouveautés {#what-is-new-march}

* Les clients avec des environnements avec des configurations de nom de domaine personnalisé préexistantes pour les [Listes autorisées IP](/help/implementing/cloud-manager/ip-allow-lists/check-ip-allow-list-status.md#pre-existing-cdn), [certificats SSL](/help/implementing/cloud-manager/managing-ssl-certifications/check-status-ssl-certificate.md#pre-existing-cdn) et [Noms de domaine personnalisés](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#pre-existing-cdn) verront un message sur leurs configurations existantes précédemment et pourront se mettre en libre-service via l’interface utilisateur.

* Les utilisateurs disposant des autorisations requises peuvent désormais modifier un programme, ce qui leur permet d’effectuer les opérations suivantes en libre-service :

   * Ajoutez la solution Sites à un programme existant avec Assets ou inversement.
   * Supprimez Sites ou Assets d’un programme existant avec Sites et Assets.
   * Ajoutez le deuxième droit de solution inutilisé à un programme existant ou en tant que nouveau programme.

* **AEM** le libellé de mise à jour push s’affiche désormais pour les écrans d’ *exécution de* pipeline et d’ ** activité.

* Si un environnement est mis en veille, mais qu’une mise à jour d’AEM est également disponible, l’état **Hibernated** prévaudra sur **Mettre à jour disponible**.

* Les utilisateurs peuvent désormais voir leurs rôles Cloud Manager en sélectionnant l’option &quot;Afficher les rôles Cloud Manager&quot; après avoir accédé à l’icône Profil utilisateur (en haut à droite) de Shell unifié.

* Le libellé **Demande d’approbation** a été renommé **Approbation de production** pour plus de clarté.

* Le libellé **Version** a été renommé **Balise Git** dans l’écran d’exécution du pipeline de production.

* Les étiquettes qui définissent le comportement lorsque des mesures importantes ne correspondent pas au seuil défini ont été réétiquetées afin de refléter leur comportement réel : **Annuler immédiatement** et **Approuver immédiatement**.

* Les listes d’obsolescence des classes et des méthodes ont été mises à jour en fonction de la version `2021.3.4997.20210303T022849Z-210225` du SDK Cloud Service AEM.

* Le pipeline de production de Cloud Manager comprend désormais la fonctionnalité [Tests d’interface utilisateur personnalisés](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing) .

### Correctifs {#bug-fixes-cm-march}

* Le contrôle de version des packages a été parfois ignoré lors de la mise à niveau AEM push.

* Certains problèmes de qualité n’ont pas été correctement découverts lorsque des modules étaient incorporés dans d’autres modules.

* Dans des cas obscurs, le nom de programme par défaut généré lors de l’ouverture de la boîte de dialogue Ajouter un programme peut être un doublon d’un nom de programme existant.

* Parfois, si l’utilisateur quitte la page d’exécution du pipeline immédiatement après le démarrage d’un pipeline, un message d’erreur s’affiche indiquant que l’action a échoué, bien que l’exécution ait réellement commencé.

* L’étape de création a été inutilement redémarrée lorsque les compilations de clients ont entraîné des packages non valides.

* Parfois, l’utilisateur peut voir un état &quot;principal&quot; vert en regard d’une Liste autorisée IP même lorsque cette configuration n’a pas été déployée.

* Tous les pipelines de production existants seront automatiquement activés avec l’étape Contrôle de l’expérience.

## Outil de transfert de contenu {#content-transfer-tool}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu v1.3.4 est le 19 mars 2021.

### Correctifs {#bug-fixes-ctt}

* CTT ignorait le contenu des dossiers portant le même nom, mais dont le nom comportait un trait d’union. Ce problème a été résolu.

### Date de publication {#release-date-ctt-march}

La date de publication de l’outil de transfert de contenu v1.3.0 est le 4 mars 2021.

### Nouveautés de l’outil de transfert de contenu {#what-is-new-ctt-march}

* Le CTT installe désormais sur `/apps` au lieu des `/libs` signets du navigateur vers certaines pages qui ne sont plus valides.
* Lorsque CTT est installé, l’utilisateur doit parcourir un niveau supplémentaire pour accéder à la page Transfert de contenu. Voir [Utilisation de l’outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html) pour plus d’informations.

### Correctifs {#bug-fixes-ctt-march}

* Lors de la migration du contenu à partir d’un chemin spécifique, CTT extrayait des ressources non liées. Ce problème a été résolu

## Analyseur de bonnes pratiques {#best-practices-analyzer}

### Date de publication {#release-date-bpa}

La date de publication de la version 2.1.8 de l’analyseur des bonnes pratiques est le 22 mars 2021.

### Nouveautés de l’analyseur des bonnes pratiques {#what-is-new-bpa}

* Possibilité de filtrer les résultats d’ACS Commons du rapport BPA dans l’interface utilisateur, ainsi que du rapport exporté sous la forme d’un fichier CSV.

## Outils de refactorisation du code {#code-refactoring-tools}

### Nouveautés des outils de refactorisation du code {#what-is-new-crt}

* Nouvelles fonctionnalités et améliorations de Repository Modernizer. Voir [Ressource GitHub : Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) pour la dernière version.
   * Normalisez les configurations OSGi (à l’exception des configurations RepoInit) au format .cfg.json préféré.
   * Renommez les dossiers de configuration OSGi au format spécifié.
   * Générez le projet ui.apps.structure .
   * Créez le module d&#39;analyse.

* Nouvelles fonctionnalités et améliorations pour le convertisseur du Dispatcher. Voir [Ressource GitHub : Convertisseur du Dispatcher](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter)
   * Création de fichiers distincts pour différentes inclusions au lieu de mettre le contenu en file d’attente.
   * Possibilité de gérer à la fois le chemin d’accès au dossier des hôtes (vhosts) et le chemin d’accès aux fichiers vhost (vhost).
   * Génération de fichiers de fermes avec de grandes configurations client dans une plage de 600 et plus.
