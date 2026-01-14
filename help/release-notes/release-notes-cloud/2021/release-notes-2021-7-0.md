---
title: Notes de mise à jour de la version 2021.7.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour de la version 2021.7.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 848f6a29-2e0f-4976-8ed7-6b7f69408c1b
feature: Release Information
role: Admin
source-git-commit: 281a8efcd18920dd926d92db9c757c0513d599fd
workflow-type: tm+mt
source-wordcount: '1292'
ht-degree: 58%

---

# Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour générales de la version actuelle (la plus récente) d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes, par exemple celles de 2020 et 2021.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de la version actuelle de [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2021.7.0) est le 29 juillet 2021.
La version suivante (2021.8.0) date du 26 août 2021.

## Vidéo de publication {#release-video}

Regardez la vidéo [Aperçu de la version de juillet 2021](https://video.tv.adobe.com/v/335580) pour un résumé des fonctionnalités ajoutées.

## Experience Manager Foundation as a Cloud Service {#foundation}

### Nouveautés {#what-is-new-foundation}

* Configuration de Dispatcher plus flexible : les projets peuvent être plus facilement organisés. Par exemple, vous pouvez désormais inclure plusieurs fichiers de règle de réécriture qui reflètent la structure de votre site. [En savoir plus sur](/help/implementing/dispatcher/disp-overview.md#validation-debug) ce mode flexible, notamment sur la manière de structurer votre configuration Dispatcher afin que vous puissiez en tirer parti.
* L’interface utilisateur de la réplication d’arborescence sous l’onglet « Distribuer » de l’agent de réplication doit être considérée obsolète et a été supprimée après le 30 septembre 2021. [Découvrez](/help/operations/replication.md#tree-activation) les stratégies de réplication alternatives.
* L’offre groupée `org.apache.sling.datasource-1.0.4.jar` pour la prise en charge de la source de données Sling a été supprimée car elle présente des fonctionnalités obsolètes et n’est pas utilisée par les clients.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de [!DNL Assets] {#assets-features}

* La fonctionnalité d’automatisation du contenu [!DNL Experience Manager Assets] permet d’utiliser les API [!DNL Adobe Creative Cloud] pour automatiser la production de ressources à grande échelle. Elle améliore la vitesse du contenu en réduisant considérablement le temps et les itérations requis pour créer des variantes d’une même ressource. La fonctionnalité ne nécessite aucune programmation et ne fonctionne pas dans la gestion des ressources numériques. Voir [génération de variantes de ressources à l’aide de l’intégration de Creative Cloud](/help/assets/cc-api-integration.md).

* [!DNL Experience Manager Assets] inclut la visionneuse PDF [!DNL Document Cloud] pour prévisualiser les documents PDF en mode natif. Cette fonctionnalité permet aux utilisateurs de prévisualiser des fichiers PDF de plusieurs pages sans traitement ni conversion de fichiers. Cette fonctionnalité améliore la parité avec [!DNL Experience Manager] 6.5. Les commandes disponibles dans la visionneuse incluent le zoom, la navigation vers les pages, le désancrage des commandes et l’affichage en plein écran. Les utilisateurs peuvent également prévisualiser des pages et des signets, et y accéder. Les commentaires sur le fichier lui-même sont pris en charge. Des commentaires et des annotations sur le contenu du fichier PDF sont prévus pour une version ultérieure.

  ![Aperçu des fichiers PDF dans [!DNL Experience Manager] à l’aide de la visionneuse PDF](/help/assets/assets/preview-pdf-file-viewer.png)

* La fonctionnalité de téléchargement Partage de liens utilise des téléchargements asynchrones qui augmentent la vitesse de téléchargement. Pour plus d’informations, voir [Téléchargement de ressources partagées à l’aide du partage de liens](/help/assets/download-assets-from-aem.md#link-share-download).

  ![Boîte de réception de téléchargement](/help/assets/assets/download-inbox.png)

* Les paramètres d’affichage sont améliorés pour permettre aux utilisateurs de choisir une vue par défaut et un paramètre de tri par défaut.

  ![Définition de l’affichage par défaut dans les [!UICONTROL Paramètres d’affichage]](/help/assets/assets/view-settings-for-defaults.png)

* Les utilisateurs peuvent rechercher et filtrer les dossiers en fonction des prédicats de propriété.

  ![Filtrage des dossiers de recherche à l’aide de prédicats de recherche](/help/assets/assets/search-folders-via-predicates.png)

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Assets] {#assets-prerelease-features}

<!-- TBD: Not sure about GA of these enh. Shall check with the team.

* A user experience enhancements displays the number of assets present in a folder. For more than 1000 assets in a folder, [!DNL Assets] displays 1000+.

  ![Number of assets in a folder are displayed on the interface](/help/assets/assets/browse-folder-number-of-assets.png)

* You can directly apply a metadata schemas to a folder in its [!UICONTROL Properties].

  ![Add metadata schema from folder properties](/help/assets/assets/metadata-schema-folder-properties.png)
-->

* Lorsque vous partagez des ressources numériques sous la forme d’un lien, les utilisateurs peuvent copier l’URL dans le presse-papiers. Cette amélioration vous permet de partager des ressources plus rapidement et plus facilement.

### Correctifs d’[!DNL Assets]  {#assets-bugs-fixed}

L’API `com.day.cq.dam.api.collection.SmartCollection` n’est pas disponible dans [!DNL Experience Manager] as a [!DNL Cloud Service]. (CQ-4326322)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouveautés de [!DNL Forms] {#what-is-new-forms}

* Vous pouvez désormais utiliser le service de conversion automatisée de formulaires pour [convertir les PDF forms en français, en allemand et en espagnol](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=fr#language-specific-meta-model) en formulaires adaptatifs.
* Ajout d’un panneau distinct à l’éditeur de modèles pour afficher les erreurs liées aux composants de formulaire adaptatif. Cela permet de consolider toutes les erreurs de formulaire adaptatif à un seul emplacement et de réduire le temps de résolution.

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Forms] {#beta-features-forms}

* **[!DNL AEM Forms as a Cloud Service - Communications]** : les [API de communication](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications.html) vous permettent de combiner des modèles XDP et des données XML pour générer des documents d’impression dans différents formats. Le service vous permet de générer des documents en mode synchrone. Les API vous permettent de créer des applications grâce auxquelles vous pouvez accomplir les actions suivantes :
   * Générer des documents en complétant des fichiers de modèle avec des données XML
   * Générer des formulaires de sortie dans divers formats, y compris les flux d’impression PDF non interactifs
   * Générer des fichiers PDF d’impression à partir d’un formulaire XFA au format PDF et d’un formulaire Adobe Acrobat

* **Externalisateur de données variables** : vous pouvez enregistrer les données variables des workflows AEM sur un système de stockage externe géré par votre entreprise.

* **Document d’enregistrement basé sur Acrobat** : vous pouvez également [utiliser Adobe Acrobat Form PDF (Acroform PDF)](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/generate-document-of-record-for-non-xfa-based-adaptive-forms) comme modèle de document d’enregistrement en plus du modèle de formulaire basé sur XFA.

* **Connecteur de magasin de données Azure Microsoft®** : vous pouvez désormais [connecter le modèle de données de formulaire au stockage Azure Microsoft®](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-azure-storage.html). Il vous permet de récupérer et de stocker des données de formulaire adaptatif dans le stockage Azure Microsoft® en tant qu’objet BLOB.

## Module complémentaire CIF {#cloud-services-cif}

### Nouveautés {#what-is-new-cif}

* Composants principaux CIF v2
   * Simplification et amélioration des configurations pour URL PDP/PLP et SEO
   * Indicateur visuel pour les données de produits évaluées en mode création pour une meilleure visibilité des modifications à venir
   * Nouveau composant sitemap pour pages de contenu et de commerce

* Prise en charge de la recommandation de produit [Adobe Commerce AI, optimisée par l’IA d’Adobe](https://business.adobe.com/ai/adobe-genai.html) dans le storefront AEM à l’aide de recommandations prédéfinies ou créées à la volée

## [!DNL Experience Manager Screens] as a [!DNL Cloud Service] {#screens}

### Correctifs {#bug-fixes-screens}

* Les paramètres du fournisseur de contenu sont désormais validés lors de la création ou de la mise à jour.

* Toutes les vues d’affichage comportent une colonne de dossiers.

* Vous pouvez développer la structure de contenu Screens.

* `bulk-offline-update-service` ne comportait aucune autorisation pour certains environnements.

* Mise à jour du lien d’aide afin qu’il corresponde à la nouvelle documentation cloud de Screens.

* Le fait de désattribuer des listes de lecture et de désactiver la suppression des listes de lecture auxquelles des lecteurs sont affectés fonctionne désormais.

* Le lecteur retélécharge désormais Assets lorsque le cache « ALL » est effacé.

* La planification des répétitions fonctionne maintenant si l’*heure de fin* est définie pour le jour suivant.

* `Back&Forward` fonctionne désormais dans Screens en tant qu’interface utilisateur de Cloud Service.

* Auparavant, les balises portant le même nom mais avec des espaces de noms différents ne pouvaient pas être créées.

## Documentation XML pour Experience Manager as a Cloud Service {#xml-documentation}

### Nouveautés {#what-is-new-xml-documentation}

La documentation XML pour Experience Manager as a Cloud Service est disponible de façon générale. Il permet aux clients d’Experience Manager as a Cloud Service de se procurer un module complémentaire XML Documentation pour importer, créer, gérer et diffuser du contenu technique sur plusieurs canaux, y compris Experience Manager Sites.

## Cloud Manager {#cloud-manager}

Cette section présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.7.0.

### Date de publication {#release-cm-july}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.7.0 est le 15 juillet 2021.
La prochaine version est prévue pour le 12 août 2021.

### Nouveautés {#what-is-new-cm-july}

* Les clients peuvent désormais utiliser les JDK Azul 8 et 11 pour leurs processus de création Cloud Manager et peuvent choisir d’utiliser l’un de ces JDK pour les plug-ins Maven compatibles avec les chaînes d’outils *ou* l’exécution du processus Maven entier.

* L’adresse IP sortante est désormais consignée dans le fichier journal de l’étape de création.

* Les environnements d’évaluation et de production exécutant d’anciennes versions d’AEM signalent désormais l’état de **Mise à jour disponible**.

* Le nombre maximal de certificats SSL pris en charge est passé à 20 par programme.

* Le nombre maximal de domaines pouvant être configurés a été porté à 500 par environnement.

* Le bouton **Gérer Git** a été renommé **Accéder aux informations Git** et le visuel de la boîte de dialogue a été rafraîchi.

* L’archétype de projet AEM utilisé par Cloud Manager a été mis à jour à la version 28.

### Correctifs {#bug-fixes-cm-july}

* Dans certains cas, l’aperçu n’était pas une option disponible lors de la liaison d’une liste autorisée IP à un environnement.

* La navigation manuelle vers la page des détails de l’exécution pour une exécution non existante n’affichait pas d’erreur, mais simplement un écran de chargement sans fin.

* Le message d’erreur affiché lorsque le nombre maximal de certificats SSL a été atteint n’était pas utile.

* Dans certains cas, il pouvait y avoir une incohérence dans la version affichée dans la carte de pipeline de la page **Aperçu**.

* L’assistant Ajouter un programme a indiqué à tort que le nom ne peut pas être modifié après la création.

### Problèmes connus {#known-issues-cm-july}

Les clients passant aux JDK Azul doivent savoir que toutes les applications existantes ne sont pas compilées sans erreur sur le JDK Azul. Adobe vous recommande de tester localement avant de basculer.

## Cloud Acceleration Manager {#cam}

### Date de publication {#release-date-july-cam}

La date de publication de la mise à jour de Cloud Acceleration Manager est le 15 juillet 2021.

### Nouveautés {#what-is-new-cam}

Cloud Acceleration Manager est une application cloud conçue pour guider vos équipes informatiques tout au long du parcours de transition, de la planification à la mise en ligne sur Cloud Service. Préparez votre équipe à une migration réussie grâce aux bonnes pratiques, aux conseils, à la documentation et aux outils recommandés par Adobe pour vous aider à chaque phase du parcours vers AEM as a Cloud Service. En savoir plus [ici](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/getting-started-cam.html?lang=fr).

>[!NOTE]
>
> Regardez cette vidéo de démonstration de [Cloud Acceleration Manager](https://video.tv.adobe.com/v/335547).
