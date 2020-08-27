---
title: Modifications notables d’Adobe Experience Manager Assets as a Cloud Service
description: Modifications notables d’Adobe Experience Manager Assets dans AEM Cloud Service par rapport à Adobe Experience Manager 6.5.
translation-type: tm+mt
source-git-commit: 2f5925613219a475a4e7d780f7d2bb3da8148e31
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 96%

---


# Modifications notables d’Experience Manager Assets as a Cloud Service {#notable-changes}

Adobe Experience Manager as a Cloud Service offre de nombreuses nouvelles fonctionnalités et possibilités de gestion pour vos projets AEM. Cependant, il existe de nombreuses différences entre les ressources Experience Manager Assets On-Premise ou dans Adobe Managed Service par rapport à Experience Manager as a Cloud Service. Ce document met en évidence les différences importantes entre les fonctionnalités d’Assets.

Les principales différences par rapport à Experience Manager 6.5 se situent dans les domaines suivants :

* [Ingestion et chargement de ressources](#asset-ingestion).
* [Microservices de ressources pour le traitement](#asset-microservices)natif du cloud.
* [Suppression de l’interface utilisateur classique](#classic-ui).

>[!NOTE]
>
>Ce document met en évidence les modifications notables apportées à AEM Assets. Pour les modifications générales apportées à AEM as a Cloud Service et à d’autres modules, voir :
>
>* [Introduction à Adobe Experience Manager as a Cloud Service](/help/overview/introduction.md)
>* [Présentation d’AEM as a Cloud Service – Nouveautés et différences](/help/overview/what-is-new-and-different.md)
>* [Architecture](/help/core-concepts/architecture.md) d’Adobe Experience Manager as a Cloud Service
>* [Modifications notables apportées à AEM as a Cloud Service (notes de mise à jour)](/help/release-notes/aem-cloud-changes.md)
>* [Modifications notables apportées à AEM Sites as a Cloud Service](/help/sites-cloud/sites-cloud-changes.md)
>* [Tutoriels sur Adobe Experience Manager as a Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/overview.html)


## Ingestion et chargement de ressources {#asset-ingestion}

Le chargement des ressources a été optimisé en permettant une meilleure mise à l’échelle de l’ingestion des ressources et des chargements plus rapides. Les fonctionnalités du produit (interfaces utilisateur web, clients de bureau) ont été mises à jour. Cela peut toutefois avoir un impact sur une personnalisation existante.

* Experience Manager applique le principe d’accès binaire direct pour le transfert et le téléchargement et les microservices de ressources pour le traitement des ressources. Consultez la [Présentation de l’assimilation de ressources](/help/assets/asset-microservices-overview.md).
   * Chargement de ressources [avec accès binaire direct](/help/assets/asset-microservices-overview.md#asset-upload-with-direct-binary-access).
   * Pour plus d’informations techniques, reportez-vous à la section sur le [protocole de chargement de binaire direct et les API](/help/assets/developer-reference-material-apis.md#upload-binary).
* Le workflow par défaut de **[!UICONTROL Mise à jour des ressources DAM]** dans les versions précédentes d’AEM n’est plus disponible. Au lieu de cela, les microservices de ressources fournissent un service évolutif et facilement disponible qui couvre la plupart du traitement des ressources par défaut (rendus, extraction de métadonnées, extraction de texte pour indexation)..
   * Consultez [Configuration et utilisation des microservices de ressources](/help/assets/asset-microservices-configure-and-use.md)
   * Pour que les étapes de workflow personnalisées soient intégrées au traitement, vous pouvez utiliser les workflows [de](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows) post-traitement..
* Les ressources qui arrivent par le biais du gestionnaire de modules nécessitent un retraitement manuel à l’aide de l’action **[!UICONTROL Retraiter les ressources]** dans l’interface Assets.

Les rendus standard générés avec les microservices de ressources sont stockés de manière rétrocompatible dans les nœuds du référentiel de ressources (conventions d’affectation de noms identiques).

## Développement et test de microservices de ressources {#asset-microservices}

Les microservices de ressources offrent un traitement évolutif et résilient des ressources à l’aide des services cloud. Adobe gère les services cloud pour un traitement optimal des différents types de ressources et des options de traitement. L’utilisation des microservices de ressources permet de se passer d’outils et de méthodes de rendu tiers (comme ImageMagick) et de simplifier les configurations, tout en fournissant des fonctionnalités prêtes à l’emploi pour les types de fichiers courants. Vous pouvez désormais traiter un [large éventail de types de fichiers](/help/assets/file-format-support.md), dans des formats prêts à l’emploi plus nombreux que les versions précédentes d’Experience Manager. Par exemple, l’extraction de miniatures des formats PSD et PSB est désormais possible, car elle nécessitait auparavant des solutions tierces telles qu’ImageMagick. Vous ne pouvez pas utiliser les configurations complexes d’ImageMagick pour la configuration des [!UICONTROL Profils de traitement]. Utilisation [!DNL Dynamic Media] pour le transcodage FFmpeg des vidéos et utilisation de profils de traitement pour le transcodage de [base des vidéos](/help/assets/manage-video-assets.md#transcode-video)MP4.

Les microservices de ressources, natifs dans le cloud, sont automatiquement mis en service et connectés à Experience Manager dans les programmes et environnements clients gérés dans Cloud Manager. Pour étendre ou personnaliser Experience Manager, les développeurs peuvent utiliser le contenu existant ou les ressources dont les rendus sont générés dans un environnement cloud, afin de tester et valider leur code avec des ressources (en les utilisant, les affichant et les téléchargeant).

Pour effectuer une validation de bout en bout du code et du processus, y compris l’ingestion et le traitement des ressources, déployez les modifications de code dans un environnement de développement cloud à l’aide [du pipeline](/help/implementing/cloud-manager/configure-pipeline.md) et testez-les avec l’exécution complète du traitement des microservices de ressources.

## Suppression de l’interface utilisateur classique {#classic-ui}

L’interface utilisateur classique n’est plus disponible dans Experience Manager as a Cloud Service. L’interface standard est l’interface utilisateur tactile.
