---
title: Notes de mise à jour de la version 2021.6.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour de la version 2021.6.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 2c72973b-5a51-4744-bf88-50da0013ba31
feature: Release Information
role: Admin
source-git-commit: 281a8efcd18920dd926d92db9c757c0513d599fd
workflow-type: tm+mt
source-wordcount: '1432'
ht-degree: 97%

---

# Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour générales de la version actuelle (la plus récente) d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes ; par exemple, celles de 2020, 2021 et ainsi de suite.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication d’[!DNL Adobe Experience Manager] as a Cloud Service version 2021.6.0 est le 28 juin 2021.
La version suivante (2021.7.0) sera publiée le 29 juillet 2021.

## Vidéo de version {#release-video}

Regardez la vidéo [Aperçu de la version de juin 2021](https://video.tv.adobe.com/v/334296) pour un résumé des fonctionnalités ajoutées.

## Documentation XML pour AEM as a Cloud Service {#xml-documentation}

### Nouveautés {#what-is-new-xml-documentation}

* La documentation XML pour AEM as a Cloud Service est désormais GA.
* Cela permettra aux clients AEM Cloud Service existants de se procurer l’ajout de documentation XML pour importer, créer, gérer et diffuser du contenu technique sur plusieurs canaux, y compris AEM Sites.

## Cloud Manager {#cloud-manager}

Cette section présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.6.0 et 2021.5.0.

### Date de publication {#release-date-june-cm}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.6.0 est le 10 juin 2021.
La prochaine version est prévue pour le 15 juillet 2021.

### Nouveautés {#what-is-new-junecm}

* Le service de prévisualisation sera déployé de manière progressive dans tous les programmes. Les clientes et clients seront avertis dans le produit lorsque leur programme est activé pour le service d‘aperçu. Pour plus d’informations, voir [Accès au service d’aperçu](/help/implementing/cloud-manager/manage-environments.md#access-preview-service).

* Les dépendances Maven téléchargées lors de l’étape de création seront désormais mises en cache entre les exécutions de pipeline. Cette fonctionnalité sera activée pour les clients au cours des prochaines semaines.

* Le nom du programme peut maintenant être modifié à partir de la boîte de dialogue de modification du programme.

* Le nom de branche par défaut utilisé lors de la création du projet et dans la commande push par défaut dans les workflows de gestion git a été remplacé par `main`.

* L’expérience de modification d’un programme dans l’interface utilisateur a été actualisée.

* La règle de qualité `ImmutableMutableMixCheck` a été mise à jour afin de classer les nœuds `/oak:index` comme étant immuables.

* Les règles de qualité `CQBP-84` et `CQBP-84--dependencies` ont été consolidées dans une seule règle. Dans le cadre de cette consolidation, l’analyse des dépendances identifie plus précisément les problèmes des dépendances tierces qui sont déployées sur l’environnement d’exécution AEM.

* Pour éviter toute confusion, les lignes de segment de l’instance de publication d’AEM et de l’instance de publication du Dispatcher sur la page Détails de l’environnement ont été consolidées.

  ![Environnements Dispatcher](/help/implementing/cloud-manager/release-notes/assets/aem-dispatcher.png)

* Une nouvelle règle de qualité du code a été ajoutée pour valider la structure des index `damAssetLucene`. Pour plus d’informations, voir [Index Lucene Oak des ressources DAM personnalisées](/help/implementing/cloud-manager/custom-code-quality-rules.md#oakpal-damAssetLucene-sanity-check).

* La page Détails de l’environnement affiche désormais plusieurs noms de domaine pour les services de publication et de prévisualisation (le cas échéant). Voir [Détails de l’environnement](/help/implementing/cloud-manager/manage-environments.md#viewing-environment) pour plus d’informations.

### Correctifs {#bug-fixes-junecm}

* Les définitions de nœud JCR contenant une nouvelle ligne après le nom de l’élément racine n’étaient pas correctement analysées.

* L’API de liste des référentiels ne filtrait pas les référentiels supprimés.

* Un message d’erreur incorrect s’affichait lorsqu’une valeur non valide était fournie lors de l’étape de planification.

* Il peut arriver que l’utilisateur voit un statut *actif* vert en regard d’une liste d’adresses IP autorisées même si cette configuration n’a pas été déployée.

* Certaines séquences de modification de programme peuvent empêcher la création ou la modification du pipeline de production.

* Certaines séquences de modification de programme peuvent entraîner l’affichage d’un message trompeur sur la page **Aperçu** pour exécuter à nouveau la configuration du programme.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de [!DNL Assets] {#ga-features-assets}

* La fonctionnalité d’automatisation du contenu [!DNL Experience Manager Assets] permet d’utiliser les API [!DNL Adobe Creative Cloud] pour automatiser la production de ressources à grande échelle. Elle améliore la vitesse du contenu en réduisant considérablement le temps nécessaire et les itérations pour créer des variantes d’une même ressource. La fonctionnalité ne nécessite aucun code et fonctionne depuis la gestion des ressources numériques.
* La version [!DNL Adobe Asset Link] v3.0 pour [!DNL Adobe Photoshop], [!DNL Adobe Illustrator], [!DNL Adobe InDesign] et [!DNL Adobe Asset Link] v2.0 pour [!DNL Adobe XD] est publiée. Elle fournit les éléments suivants :

   * Prise en charge de [!DNL Assets Essentials].
   * Possibilité de se connecter automatiquement à [!DNL Experience Manager] en tant que [!DNL Cloud Service] ou [!DNL Assets Essentials].

<!-- TBD: Checking with PMs if AAE release should be mentioned here.
-->

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Assets] {#beta-features-assets}

* Les paramètres d’affichage sont améliorés pour permettre aux utilisateurs de choisir une vue par défaut et un paramètre de tri par défaut.
* La fonctionnalité de téléchargement de Linkshare utilise des téléchargements asynchrones qui augmentent la vitesse de téléchargement.
* Les utilisateurs peuvent rechercher et filtrer les dossiers en fonction des prédicats de propriété.
* [!DNL Experience Manager Assets] incorpore la visionneuse PDF optimisée par [!DNL Adobe Document Cloud] pour prévisualiser les documents pris en charge. Cette fonctionnalité permet aux utilisateurs de prévisualiser des fichiers PDF et d’autres fichiers multi-pages sans traitement complexe. Cela améliore la parité des fonctionnalités avec [!DNL Experience Manager] 6.5.

### Correctifs d’[!DNL Assets]  {#bugs-fixed-assets}

* Lors de l’ajout d’un propriétaire à un sous-dossier, [!DNL Assets] ajoute également le même utilisateur qu’un propriétaire du dossier parent. (CQ-4323737)
* Lors de l’ajout de ressources aux collections, si un utilisateur applique un filtre sur la recherche Collections, il ne peut pas afficher les collections dans la vue Liste. (CQ-4323181)
* Lors de la recherche de fichiers et de dossiers, si l’utilisateur applique un filtre et sélectionne [!UICONTROL Fichiers et dossiers], seuls les fichiers sont affichés, mais pas le dossier. (CQ-4319543)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités de [!DNL Sites] {#ga-features-sites}

* Publier dans le niveau de prévisualisation s’affiche désormais comme état de page dans l’interface utilisateur d’administration de Sites.
* Publier dans le niveau de prévisualisation : l’URL de prévisualisation est maintenant affichée à la fin de l’action et l’URL est conservée dans les propriétés de la page pour référence ultérieure.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouveautés d’[!DNL Forms]  {#what-is-new-forms}

* Possibilité de filtrer les colonnes personnalisées dans la boîte de réception AEM.
* Possibilité d’utiliser l’éditeur de thèmes et le calque de style de l’éditeur de formulaires adaptatifs pour appliquer un style au composant Captcha.
* Amélioration de la vitesse et de la précision de la détection automatique des sections logiques dans les formulaires PDF sources et de leur conversion en panneaux de formulaires adaptatifs correspondants.
* Ajout d’une action de déplacement pour déplacer un fichier PDF ou XDP d’un dossier à un autre.

### Fonctionnalité Beta de [!DNL Forms]  {#what-is-new-forms-prerelease}

* **[!DNL AEM Forms as a Cloud Service - Communications]** : les API de communication vous permettent de combiner des modèles XDP et des données XML pour générer des documents d’impression dans différents formats. Le service vous permet de générer des documents en mode synchrone. Les API vous permettent de créer des applications grâce auxquelles vous pouvez accomplir les actions suivantes :
   * Générer des documents de formulaire définitifs en complétant des fichiers de modèle avec des données XML.
   * Générez des formulaires de sortie dans divers formats, y compris les flux d’impression PDF non interactifs.
   * Générer des fichiers PDF d’impression à partir d’un formulaire XFA au format PDF et d’un formulaire Adobe Acrobat (AcroForm).

* **Externalisateur de données variables** : vous pouvez enregistrer les données variables des workflows AEM sur un système de stockage externe géré par votre entreprise.

Vous pouvez écrire à [!DNL formscsbeta@adobe.com] pour vous inscrire au programme Beta.

### Correctifs de [!DNL Forms] {#forms-bugs-fixed}

* Lorsqu’un champ est validé avant l’envoi des données au service principal via le modèle de données de formulaire (FDM), les validations réussissent, mais le service de modèle de données de formulaire ne parvient pas à appeler après validation.
* Lorsque vous envoyez un formulaire contenant un champ de chargement HTML standard d’un appareil iOS d’Apple, le contenu du fichier n’est parfois pas envoyé et un fichier de 0 octet est reçu à l’autre bout. Il s’agit d’un problème connu dans Apple iOS. [FB9117687](https://feedbackassistant.apple.com/feedback/9117687)

## [!DNL Experience Manager Screens] as a [!DNL Cloud Service] {#screens}

Cette section décrit les notes de mise à jour d’AEM Screens as a Cloud Service.

### Date de publication {#release-date-june-screens}

La date de publication d’AEM Screens as a Cloud Service est le 24 juin 2021.

### Nouveautés {#what-is-new-screens-june}

>[!NOTE]
>Consultez le [Guide d’AEM Screens as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/home.html?lang=fr) pour obtenir les connaissances de base requises pour réussir l’installation, la configuration et l’exécution de Screens as a Cloud Service et reportez-vous à la documentation technique des concepts détaillés.

* La gestion de l’enregistrement des appareils en masse signifie que la mise en service d’un grand nombre d’appareils de lecture est plus rapide et plus efficace.

* Amélioration des options de recherche et de filtrage pour chacune des vues d’inventaire Appareil, Affichage et Canal.

* L’instantané de la santé de l’appareil permet de gagner du temps en fournissant un état critique en un coup d’œil.

* La page Détails de l’objet offre un résumé des informations les plus pertinentes pour chaque objet de votre projet.

## Module complémentaire CIF {#cloud-services-cif}

### Nouveautés {#what-is-new-cif}

* Nouveaux types de données de référence de catégorie et de produit CIF pour les fragments de contenu (y compris prise en charge de l’interface utilisateur du sélecteur de produits/catégories)
* Nouveau composant principal de fragment de contenu Commerce
* Recherche commerciale en texte intégral prise en charge dans AEM serveur principal
* Les composants principaux de Commerce prennent en charge la collecte de données des recommandations de l’IA Adobe Commerce
* Amélioration des URL compatibles avec les moteurs de recherche pour les pages de catégorie
* Prise en charge des en-têtes HTTP personnalisés par site/configuration

## Outil de transfert de contenu {#content-transfer-tool}

### Date de publication {#release-date-ctt-latest}

La date de publication de l’outil de transfert de contenu version v1.5.4 est le 28 juin 2021.

### Nouveautés {#what-is-new-ctt-latest}

* Prise en charge d’une étape facultative [pré-copie](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html) ajoutée à l’utilisation avec le CTT. L’étape de pré-copie peut être utilisée pour accélérer considérablement les phases d’extraction et d’ingestion de l’activité de transfert de contenu lorsque l’instance d’AEM source est configurée pour utiliser un entrepôt de données Amazon S3 ou Azure Blob Storage.

* Une barrière de sécurité a été ajoutée au CTT pour empêcher les utilisateurs d’arrêter une ingestion et de potentiellement corrompre les données une fois qu’elles ont atteint le point critique pendant la phase d’ingestion.

* Les journaux d’extraction sont devenus plus descriptifs pour faciliter le dépannage.

* Ajout de messages d’état d’ingestion plus descriptifs dans l’interface utilisateur.

### Correctifs {#bug-fixes-ctt-latest}

* Lors de l’arrêt d’une ingestion sur l’instance de création, l’interface d’utilisation a remplacé une ingestion précédemment terminée sur l’instance de publication sur `STOPPED` à partir de `FINISHED`. Ce problème a été résolu.

## Analyseur des bonnes pratiques {#best-practices-analyzer}

### Date de publication {#release-date-bpa}

La date de publication de l’analyseur des bonnes pratiques v2.1.16 est le 30 juin 2021.

### Nouveautés {#what-is-new-bpa-latest}

* Possibilité de détecter et de générer des rapports sur les nœuds enfants manquants dans les dossiers situés sous `/content/dam`.

* Possibilité de détecter et de générer des rapports sur la version de l’analyseur des bonnes pratiques utilisée.

### Correctifs {#bug-fixes-bpa-latest}

* Correction d’une erreur de journalisation liée à la structure de référentiel non prise en charge (URS).
