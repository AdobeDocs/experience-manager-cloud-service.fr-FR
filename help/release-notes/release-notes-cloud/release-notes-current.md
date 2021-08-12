---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: 3f16144a95bdb3da08c15f15613031cdd069a977
workflow-type: tm+mt
source-wordcount: '1406'
ht-degree: 20%

---


# Notes de mise à jour actuelles pour[!DNL Adobe Experience Manager]as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour générales de la version actuelle (la plus récente) d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes. par exemple, pour ceux de 2020, 2021, etc.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de la version actuelle de [!DNL Adobe Experience Manager] en tant que [!DNL Cloud Service] (2021.7.0) est le 29 juillet 2021.
La version suivante (2021.8.0) date du 26 août 2021.

## Vidéo de publication {#release-video}

Regardez la vidéo [Aperçu de la version de juillet 2021](https://video.tv.adobe.com/v/335580) pour un résumé des fonctionnalités ajoutées.

## [!DNL Experience Manager] comme  [!DNL Cloud Service] fondation {#foundation}

### Nouveautés {#what-is-new-foundation}

* Configuration Dispatcher plus flexible : Les projets peuvent être plus facilement organisés. Par exemple, vous pouvez désormais inclure plusieurs fichiers de règle de réécriture qui reflètent la structure de votre site. [Découvrez ](/help/implementing/dispatcher/disp-overview.md#validation-debug) ce mode flexible, notamment comment structurer votre configuration Dispatcher pour en tirer parti.
* L’interface utilisateur de réplication de l’arborescence sous l’onglet &quot;Distribute&quot; de l’agent de réplication doit être considérée comme obsolète et doit être supprimée après le 30 septembre. [Découvrez ](/help/operations/replication.md#tree-activation) les stratégies de réplication alternatives.
* Le lot `org.apache.sling.datasource-1.0.4.jar` pour la prise en charge de la source de données Sling a été supprimé, car il présente des fonctionnalités obsolètes et n’est pas utilisé par les clients.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de [!DNL Assets] {#assets-features}

* La fonctionnalité d’automatisation du contenu permet à [!DNL Experience Manager Assets] d’exploiter les API [!DNL Adobe Creative Cloud] pour automatiser la production de ressources à grande échelle. Elle améliore la vitesse du contenu en réduisant considérablement le temps nécessaire et les itérations pour créer des variantes d’une même ressource. La fonctionnalité ne nécessite aucune programmation et ne fonctionne pas dans la gestion des ressources numériques. Voir [génération de variantes de ressources à l’aide de l’intégration de Creative Cloud](/help/assets/cc-api-integration.md).

* [!DNL Experience Manager Assets] inclut la visionneuse  [!DNL Document Cloud] PDF pour prévisualiser les documents PDF en mode natif. Cette fonctionnalité permet aux utilisateurs de prévisualiser des fichiers PDF de plusieurs pages sans traitement ni conversion de fichiers. Cette fonctionnalité améliore la parité avec [!DNL Experience Manager] 6.5. Les commandes disponibles dans la visionneuse incluent le zoom, la navigation vers les pages, la désancrage des commandes et l’affichage en plein écran. La casse des utilisateurs permet également de prévisualiser et d’accéder aux pages et aux signets. Les commentaires sur le fichier lui-même sont pris en charge et l’ajout de commentaires et d’annotations sur le contenu du fichier PDF sera ajouté dans une version ultérieure.

   ![Aperçu des fichiers PDF dans à  [!DNL Experience Manager] l’aide de la visionneuse PDF](/help/assets/assets/preview-pdf-file-viewer.png)

* La fonctionnalité de téléchargement de Linkshare utilise des téléchargements asynchrones qui augmentent la vitesse de téléchargement. Voir [Téléchargement des ressources partagées à l’aide du partage de liens](/help/assets/download-assets-from-aem.md#link-share-download).

   ![Boîte de réception de téléchargement](/help/assets/assets/download-inbox.png)

* Les paramètres d’affichage sont améliorés pour permettre aux utilisateurs de choisir une vue par défaut et un paramètre de tri par défaut.

   ![Définition de l’affichage par défaut dans les paramètres  [!UICONTROL d’affichage]](/help/assets/assets/view-settings-for-defaults.png)

* Les utilisateurs peuvent rechercher et filtrer les dossiers en fonction des prédicats de propriété.

   ![Filtrage des dossiers de recherche à l’aide de prédicats de recherche](/help/assets/assets/search-folders-via-predicates.png)

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Assets] {#assets-prerelease-features}

<!-- TBD: Not sure about GA of these enh. Shall check with the team.

* A user experience enhancements displays the number of assets present in a folder. For more than 1000 assets in a folder, [!DNL Assets] displays 1000+.

  ![Number of assets in a folder are displayed on the interface](/help/assets/assets/browse-folder-number-of-assets.png)

* You can directly apply a metadata schemas to a folder in its [!UICONTROL Properties].

  ![Add metadata schema from folder properties](/help/assets/assets/metadata-schema-folder-properties.png)
-->

* Lorsque vous partagez des ressources numériques sous la forme d’un lien, les utilisateurs peuvent copier l’URL dans le Presse-papiers. Cette amélioration vous permet de partager vos ressources plus rapidement et plus facilement.

### Correctifs d’[!DNL Assets]  {#assets-bugs-fixed}

L’API `com.day.cq.dam.api.collection.SmartCollection` n’est pas disponible dans [!DNL Experience Manager] sous la forme [!DNL Cloud Service]. (CQ-4326322)

## [!DNL Experience Manager Forms] as a  [!DNL Cloud Service] {#forms}

### Nouveautés d’[!DNL Forms]  {#what-is-new-forms}

* Vous pouvez désormais utiliser le service Automated forms conversion pour [convertir les PDF forms en français, en allemand et en espagnol](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?#language-specific-meta-model) en formulaires adaptatifs.
* Ajout d’un panneau distinct à l’éditeur de modèles pour afficher les erreurs liées aux composants de formulaire adaptatif. Cela permet de consolider toutes les erreurs de formulaire adaptatif à un seul emplacement et de réduire le temps de résolution.

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Forms] {#beta-features-forms}

* **[!DNL AEM Forms as a Cloud Service - Communications]**:  [Communication ](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/aem-forms-cloud-service-communications.html) APIshelp vous permet de combiner des modèles XDP et des données XML pour générer des documents d’impression dans différents formats. Le service vous permet de générer des documents en mode synchrone. Les API vous permettent de créer des applications qui vous permettent :
   * Générer des documents en renseignant les fichiers de modèle avec des données XML.
   * Générez des formulaires de sortie dans divers formats, y compris les flux d’impression PDF non interactifs.
   * Générez des fichiers PDF d’impression à partir d’un formulaire XFA au format PDF et d’un formulaire Adobe Acrobat.

* **Externalisateur de données variables** : vous pouvez enregistrer les données variables des workflows AEM sur un système de stockage externe géré par votre entreprise.

* **Document d’enregistrement** basé sur Acrobat : Vous pouvez également  [utiliser Adobe Acrobat Form PDF (Acrobat PDF)](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/generate-document-of-record-for-non-xfa-based-adaptive-forms.html)  comme modèle de document d’enregistrement en plus du modèle de formulaire basé sur XFA.

* **Connecteur** de magasin de données Microsoft Azure : Vous pouvez désormais  [connecter le modèle de données de formulaire au stockage Microsoft Azure](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/use-form-data-model/configure-azure-storage.html). Il vous permet de récupérer et de stocker des données de formulaire adaptatif dans le stockage Microsoft Azure en tant que BLOB.

## Module complémentaire CIF {#cloud-services-cif}

### Nouveautés {#what-is-new-cif}

* Composants principaux CIF v2
   * Simplification et amélioration des configurations pour l’URL PDP/PLP et l’optimisation du référencement
   * Indicateur visuel pour les données de produits intermédiaires en mode création pour une meilleure visibilité des modifications à venir
   * Nouveau composant sitemap pour les pages de contenu et de commerce

* Prise en charge de la [recommandation de produit Adobe Commerce Sensei, optimisée par Adobe Sensei](https://business.adobe.com/products/magento/product-recommendations.html) dans AEM Storefront à l’aide de recommandations prédéfinies ou créées à la volée

## [!DNL Experience Manager Screens] as a  [!DNL Cloud Service] {#screens}

### Correctifs {#bug-fixes-screens}

* Les paramètres du fournisseur de contenu sont désormais validés lors de la création ou de la mise à jour.

* Toutes les vues d’affichage comportent une colonne de dossiers.

* Vous pouvez développer la structure de contenu Screens.

* `bulk-offline-update-service` ne comportait aucune autorisation pour certains environnements.

* Mise à jour du lien d’aide afin qu’il corresponde à la nouvelle documentation cloud screens.

* Déattribuez des listes de lecture et désactivez la suppression des listes de lecture auxquelles un ou plusieurs lecteurs sont affectés. Cela fonctionne désormais.

* Le lecteur retélécharge désormais les ressources lorsque le cache &quot;ALL&quot; est effacé.

* La planification des répétitions fonctionne maintenant si l’*heure de fin* est définie pour le jour suivant.

* `Back&Forward` fonctionne désormais dans Screens en tant qu’interface utilisateur de Cloud Service.

* Les balises portant le même nom mais avec des espaces de noms différents n’ont pas pu être créés auparavant.

## Documentation XML pour Experience Manager en tant que Cloud Service {#xml-documentation}

### Nouveautés {#what-is-new-xml-documentation}

XML Documentation pour Experience Manager as a Cloud Service est disponible en général. Il permet aux clients Experience Manager en tant que Cloud Service de se procurer le module complémentaire de documentation XML pour importer, créer, gérer et diffuser du contenu technique sur plusieurs canaux, y compris les sites Experience Manager.

## Cloud Manager {#cloud-manager}

Cette section présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.7.0.

### Date de publication {#release-cm-july}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.7.0 est le 15 juillet 2021.
La prochaine version est prévue pour le 12 août 2021.

### Nouveautés {#what-is-new-cm-july}

* Les clients peuvent désormais utiliser les JDK Azul 8 et 11 pour leurs processus de génération Cloud Manager et peuvent choisir d’utiliser un de ces JDK pour les plug-ins Maven compatibles avec les chaînes d’outils *ou* pour l’exécution du processus Maven complet.

* L’adresse IP sortante sera désormais consignée dans le fichier journal de l’étape de génération.

* Les environnements d’évaluation et de production exécutant d’anciennes versions d’AEM signalent désormais l’état de **Mise à jour disponible**.

* Le nombre maximal de certificats SSL pris en charge est passé à 20 par programme.

* Le nombre maximal de domaines pouvant être configurés a été porté à 500 par environnement.

* Les boutons **Gérer Git** ont été renommés **Accéder aux informations Git** et le visuel de la boîte de dialogue a été rafraîchi.

* L’archétype de projet AEM utilisé par Cloud Manager a été mis à jour à la version 28.

### Correctifs {#bug-fixes-cm-july}

* Dans certains cas, l’aperçu n’était pas une option disponible lors de la liaison d’une Liste autorisée IP à un environnement.

* La navigation manuelle vers la page des détails de l’exécution pour une exécution non existante n’affichait pas d’erreur, mais simplement un écran de chargement sans fin.

* Le message d’erreur affiché lorsque le nombre maximal de certificats SSL a été atteint n’était pas utile.

* Dans certains cas, il peut y avoir une incohérence dans la version affichée dans la carte de pipeline de la page **Aperçu**.

* L’assistant d’ajout de programme indiquait de manière incorrecte que le nom ne peut pas être modifié après la création.

### Problèmes connus {#known-issues-cm-july}

Les clients basculant sur les JDK Azul doivent savoir que toutes les applications existantes ne seront pas compilées sans erreur sur le JDK Azul. Il est vivement recommandé d’exécuter un test local avant de basculer.

## Outil de transfert de contenu {#content-transfer-tool}

### Date de publication {#release-date-ctt-latest}

La date de publication de l’outil de transfert de contenu v1.5.6 est le 11 août 2021.

### Correctifs {#bug-fixes-ctt}

* Dans certains cas, tous les utilisateurs n’ont pas été migrés vers l’instance cible. Pour obtenir ce correctif, CTT v1.5.6 est requis avec aem-ethos-tools 1.2.354 ou version ultérieure sur l’AEM cible en tant qu’instance de Cloud Service.

* Le bouton **Arrêter l’ingestion** était désactivé lors de l’ingestion vers l’instance de publication. Cela n’est pas nécessaire, car il n’existe aucune étape de restauration de mongo pendant l’ingestion de publication.

* CTT n’a pas nettoyé le répertoire `/tmp` après une extraction réussie. Cela entraînait parfois des problèmes d’espace disque.


## Cloud Accelerated Manager {#cam}

### Date de publication {#release-date-july-cam}

La date de publication de Cloud Acceleration Manager est le 15 juillet 2021.

### Nouveautés {#what-is-new-cam}

Cloud Acceleration Manager est une application cloud conçue pour guider vos équipes informatiques tout au long du parcours de transition, de la planification à la mise en ligne sur Cloud Service. Configurez vos équipes pour une migration réussie avec les bonnes pratiques, conseils, documentation et outils recommandés par l’Adobe pour vous aider à chaque phase du parcours à AEM en tant que Cloud Service. En savoir plus [ici](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/getting-started-cam.html?lang=en).

>[!NOTE]
>
> Consultez cette [vidéo de démonstration de Cloud Acceleration Manager](https://video.tv.adobe.com/v/335547).
