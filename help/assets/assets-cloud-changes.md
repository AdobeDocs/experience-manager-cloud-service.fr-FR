---
title: Modifications notables apportées à [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service]
description: Modifications notables apportées à [!DNL Adobe Experience Manager Assets] dans [!DNL Experience Manager] as a [!DNL Cloud Service] par rapport à [!DNL Adobe Experience Manager] 6.5.
feature: Release Information
role: User, Leader, Architect, Admin
exl-id: 93e7dbcd-016e-4ef2-a1cd-c554efb5ad34
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '1052'
ht-degree: 81%

---

# Modifications notables apportées à [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#notable-changes}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime et Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouvelle</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>Intégration d’AEM Assets à Edge Delivery Services</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>Extensibilité de l’interface utilisateur</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Activation de Dynamic Media Prime et Ultimate</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>Bonnes pratiques de recherche</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>Bonnes pratiques relatives aux métadonnées</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Hub de contenus</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>Fonctionnalités Dynamic Media avec OpenAPI</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>Documentation de développement pour AEM Assets</b></a>
        </td>
    </tr>
</table>

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] offre de nombreuses nouvelles fonctionnalités et possibilités de gestion pour vos projets Experience Manager. Il existe de nombreuses différences entre [!DNL Experience Manager Assets] sur site ou hébergé sous la forme Adobe Managed Service par rapport à [!DNL Experience Manager] as a [!DNL Cloud Service]. Ce article met en évidence les différences importantes entre les fonctionnalités d’[!DNL Assets]

Les principales différences par rapport à [!DNL Experience Manager] 6.5 se situent dans les domaines suivants :

* [Ingestion, chargement et traitement de ressources](#asset-ingestion).
* [Microservices de ressources pour le traitement natif dans le cloud](#asset-microservices).
* [Suppression de l’interface utilisateur classique](#classic-ui).

## Ingestion, traitement et distribution des ressources {#asset-ingestion-distribution}

Le chargement des ressources est optimisé pour bénéficier d’une meilleure efficacité en permettant une évolutivité plus performante de l’ingestion, des chargements plus rapides, un traitement accéléré grâce aux microservices et une ingestion en masse. Les fonctionnalités du produit (interfaces utilisateur web, clients de bureau) ont été mises à jour. En outre, ces éléments peuvent avoir un impact sur certaines personnalisations existantes.

* [!DNL Experience Manager] utilise le principe d’accès binaire direct pour charger et télécharger des ressources, ainsi que des microservices de ressources pour les traiter. Consultez la [présentation des microservices](/help/assets/asset-microservices-overview.md).
   * Chargement de ressources [avec accès binaire direct](/help/assets/asset-microservices-overview.md#asset-upload-with-direct-binary-access).
   * Pour plus d’informations techniques, reportez-vous à la section sur le [protocole de chargement de binaire direct et les API](/help/assets/developer-reference-material-apis.md#upload-binary).
   * Pour une comparaison des méthodes d’API disponibles pour les opérations CRUD de base, voir [API et opérations relatives aux ressources](/help/assets/developer-reference-material-apis.md#use-cases-and-apis).
* Le workflow par défaut de **[!UICONTROL Mise à jour des ressources DAM]** des versions précédentes d’[!DNL Experience Manager] n’est plus disponible. Au lieu de cela, les microservices de ressources fournissent un service évolutif et facilement disponible qui couvre la plupart du traitement des ressources par défaut (rendus, extraction de métadonnées, extraction de texte pour indexation).
   * Voir [Configuration et utilisation des microservices de ressources](/help/assets/asset-microservices-configure-and-use.md)
   * Pour disposer d’étapes de workflow personnalisées dans le traitement, vous pouvez utiliser les [workflows de post-traitement](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows).

* Les composants de site web qui diffusent un fichier binaire sans transformation peuvent utiliser le téléchargement direct. Le servlet GET Sling est mis à jour pour activer cette fonctionnalité par défaut. Les composants de site web qui diffusent un fichier binaire avec une certaine transformation (par exemple, le redimensionner via un servlet) peuvent continuer à fonctionner en l’état.

Les rendus standard générés avec les microservices de ressources sont stockés de manière rétrocompatible dans les nœuds du référentiel de ressources à l’aide de conventions d’affectation de noms identiques.

## Développement et test de microservices de ressources {#asset-microservices}

Les microservices de ressources offrent un traitement évolutif et résilient des ressources à l’aide des services cloud. Adobe gère les services cloud pour un traitement optimal des différents types de ressources et des options de traitement. L’utilisation des microservices de ressources permet de se passer d’outils et de méthodes de rendu tiers (comme [!DNL ImageMagick]) et de simplifier les configurations, tout en fournissant des fonctionnalités prêtes à l’emploi pour les types de fichiers courants. Vous pouvez désormais traiter un [large éventail de types de fichiers](/help/assets/file-format-support.md), dans des formats prêts à l’emploi plus nombreux que les versions précédentes d’Experience Manager. Par exemple, l’extraction de miniatures des formats PSD et PSB est désormais possible ; elle nécessitait auparavant des solutions tierces telles qu’[!DNL ImageMagick]. Vous ne pouvez pas utiliser les configurations complexes de [!DNL ImageMagick] pour les [!UICONTROL Profils de traitement]. Utilisez [!DNL Dynamic Media] pour le transcodage FFmpeg avancé des vidéos et les profils de traitement pour le [transcodage de base des vidéos MP4](/help/assets/manage-video-assets.md#transcode-video).

Les microservices de ressources, natifs dans le cloud, sont automatiquement mis en service et connectés à [!DNL Experience Manager] dans les programmes et environnements clients gérés dans Cloud Manager. Pour étendre ou personnaliser les [!DNL Experience Manager], les développeurs peuvent utiliser du contenu existant ou des ressources dont les rendus sont générés dans un environnement cloud. Cette fonctionnalité leur permet de tester et de valider leur code à l’aide de ressources, de les afficher ou de les télécharger.

Pour effectuer une validation de bout en bout du code et du processus, y compris l’ingestion et le traitement des ressources, déployez les modifications de code dans un environnement de développement cloud à l’aide [du pipeline](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) et testez-les avec l’exécution complète du traitement des microservices de ressources.

## Parité des fonctionnalités avec [!DNL Experience Manager] 6.5 {#cloud-service-feature-status}

[!DNL Experience Manager] as a [!DNL Cloud Service] introduit de nombreuses nouvelles fonctionnalités et des méthodes plus performantes pour que les fonctionnalités existantes fonctionnent. Cependant, lorsque vous passez de [!DNL Experience Manager] 6.5 à [!DNL Experience Manager] as a [!DNL Cloud Service], vous pouvez remarquer que certaines fonctionnalités fonctionnent différemment, ne sont pas disponibles ou ne sont que partiellement disponibles. Voici une liste de ces fonctionnalités. Consultez également la section [Fonctionnalités obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

| Fonctions ou cas d’utilisation | Statut dans [!DNL Experience Manager] as a [!DNL Cloud Service] | Commentaires |
|-----|-----|-----|
| [Détection des doublons de ressources ](/help/assets/detect-duplicate-assets.md) | Cela fonctionne différemment | Renseignez-vous sur [son fonctionnement dans [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/assets/managing/duplicate-detection). |
| [Pour les rendus FPO (avec positionnement uniquement)](/help/assets/configure-fpo-renditions.md) | Cela fonctionne différemment | Les profils de traitement utilisent les microservices de ressources pour générer des rendus FPO. Dans Experience Manager 6.5, une solution tierce telle qu’[!DNL ImageMagick] était disponible pour générer les rendus. |
| Écriture différée des métadonnées | Cela fonctionne différemment | Désactivé par défaut. Activez le lanceur de processus correspondant si nécessaire. Les microservices de ressources gèrent l’écriture différée. |
| Traitement des ressources chargées à l’aide du gestionnaire de packages | Cela nécessite une intervention manuelle | Retraitez manuellement les ressources à l’aide de l’action **[!UICONTROL Retraiter la ressource]**. |
| Détection du type MIME | Pas de prise en charge. | Si vous chargez une ressource numérique sans extension ou avec une extension incorrecte, elle peut ne pas être traitée comme vous le souhaitez. Les utilisateurs peuvent toujours stocker les fichiers binaires sans extension dans le module DAM. Voir la section [Détection de type MIME dans [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/assets/administer/detect-asset-mime-type-with-tika). |
| Génération de sous-ressources pour des ressources composites | Pas de prise en charge. | Les cas d’utilisation dépendants tels que les annotations peuvent ne pas être remplis. Voir la section [Création de sous-ressources dans [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/assets/managing/managing-linked-subassets#generate-subassets). L’aperçu PDF de certains types de fichiers est disponible à partir de la [version 2021.7.0](/help/release-notes/release-notes-cloud/release-notes-current.md). |
| Modifier les images | Non pris en charge. | La modification de ressources n’est pas prise en charge dans Experience Manager as a Cloud Service. Voir [comment cela fonctionnait dans Experience Manager 6.5](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/assets/managing/manage-assets#editing-images). |
| Page d’accueil | Non pris en charge. | Voir [[!DNL Assets]  Expérience de page d’accueil dans  [!DNL Experience Manager]  6.5](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/assets/using/assets-home-page) |
| Extraction de ressources à partir de l’archive ZIP | Non pris en charge. | Voir la section [Extraction de fichiers ZIP dans [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/assets/managing/manage-assets#extractzip). |
| Évaluations des ressources | Non pris en charge. | Le widget d’évaluation dans l’éditeur de schéma de métadonnées n’est pas pris en charge. |
| Filtre de disposition du contenu | Non pris en charge. | Un cas d’utilisation courant de `ContentDispositionFilter` consiste à permettre aux administrateurs de configurer des [!DNL Experience Manager] pour qu’ils diffusent des fichiers HTML et qu’ils ouvrent des fichiers PDF en ligne au lieu de les télécharger. Sur les instances de publication, vous pouvez gérer la disposition à l’aide de la configuration Dispatcher. Sur les instances de création, Adobe ne recommande pas de modifier l’en-tête de disposition du contenu. Voir [Filtre de disposition du contenu dans [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/security/content-disposition-filter). |
| Modèle de séance photo du produit | Non pris en charge. | Voir [Modèle de séance photo du produit dans [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/sites/authoring/projects/managing-product-information). |
| Traduction intelligente | Non pris en charge. | La traduction intelligente n’est pas prise en charge dans [!DNL Experience Manager] as a [!DNL Cloud Service]. |
| WebDAV | Non pris en charge. | Pour obtenir des alternatives, consultez Intégration de [[!DNL Creative Cloud] ](/help/assets/aem-cc-integration-best-practices.md) ou les [Documents de référence pour les développeurs](/help/assets/developer-reference-material-apis.md). |
| Interface utilisateur classique | Non pris en charge. | Seule une interface utilisateur tactile est disponible. |

**Voir également**

* [Traduire les ressources](translate-assets.md)
* [API HTTP Assets](mac-api-assets.md)
* [Formats de fichiers pris en charge par Assets](file-format-support.md)
* [Rechercher des ressources](search-assets.md)
* [Ressources connectées](use-assets-across-connected-assets-instances.md)
* [Rapports de ressources](asset-reports.md)
* [Schémas de métadonnées](metadata-schemas.md)
* [Télécharger des ressources](download-assets-from-aem.md)
* [Gestion des métadonnées](manage-metadata.md)
* [Facettes de recherche](search-facets.md)
* [Gérer les collections](manage-collections.md)
* [Import des métadonnées en bloc](metadata-import-export.md)
* [Publier des ressources sur AEM et Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>Les ressources suivantes sont disponibles pour [!DNL Experience Manager] as a [!DNL Cloud Service] :
>
>* [Liste des fonctionnalités obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md)
>* [Une introduction](/help/overview/introduction.md)
>* [Nouveautés et différences](/help/overview/what-is-new-and-different.md)
>* [L’architecture](/help/overview/architecture.md)
>* [Modifications notables](/help/release-notes/aem-cloud-changes.md)
>* [Modifications notables [!DNL Sites]](/help/sites-cloud/sites-cloud-changes.md)
>* [Tutoriels vidéo](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/overview)
