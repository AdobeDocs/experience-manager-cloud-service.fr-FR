---
title: Modifications notables d’Adobe Experience Manager Assets as a [!DNL Cloud Service]
description: Modifications notables apportées aux ressources Adobe Experience Manager dans Experience Manager [!DNL Cloud Service] par rapport à Adobe Experience Manager 6.5.
translation-type: tm+mt
source-git-commit: 0838f384b31c59fe95087e1a71741656eedcd13b
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 63%

---


# Modifications notables d’Experience Manager Assets as a [!DNL Cloud Service] {#notable-changes}

Adobe Experience Manager en tant que [!DNL Cloud Service] apporte de nombreuses nouvelles fonctionnalités et possibilités pour gérer vos projets Experience Manager. Il existe de nombreuses différences entre les ressources Experience Manager sur site ou hébergées en tant que service géré par Adobe par rapport à [!DNL Experience Manager] en tant que [!DNL Cloud Service]. Cet article souligne les différences importantes entre les fonctionnalités [!DNL Assets].

Les principales différences par rapport à [Experience Manager] 6.5 se situent dans les domaines suivants :

* [Importation, transfert et traitement](#asset-ingestion) des ressources.
* [Microservices de ressources pour le traitement natif dans le cloud](#asset-microservices).
* [Suppression de l’interface utilisateur classique](#classic-ui).

## Importation et traitement des ressources {#asset-ingestion}

Le transfert des ressources a été optimisé pour plus d’efficacité en permettant une meilleure mise à l’échelle de l’assimilation des ressources, des téléchargements plus rapides, un traitement plus rapide à l’aide de microservices et l’assimilation en masse. Les fonctionnalités du produit (interfaces utilisateur web, clients de bureau) ont été mises à jour. Cela peut toutefois avoir un impact sur une personnalisation existante.

* Experience Manager applique le principe d’accès binaire direct pour le transfert et le téléchargement et les microservices de ressources pour le traitement des ressources. Consultez la [Présentation de l’assimilation de ressources](/help/assets/asset-microservices-overview.md).
   * Chargement de ressources [avec accès binaire direct](/help/assets/asset-microservices-overview.md#asset-upload-with-direct-binary-access).
   * Pour plus d’informations techniques, reportez-vous à la section sur le [protocole de chargement de binaire direct et les API](/help/assets/developer-reference-material-apis.md#upload-binary).
   * Pour une comparaison des méthodes d’API disponibles pour les opérations CRUD de base, voir [APIs and asset operations](/help/assets/developer-reference-material-apis.md#use-cases-and-apis).
* Le flux de travaux par défaut **[!UICONTROL Mise à jour des ressources DAM]** dans les versions précédentes de [!DNL Experience Manager] n&#39;est plus disponible. Au lieu de cela, les microservices de ressources offrent un service évolutif et facilement disponible qui couvre la plupart du traitement des ressources par défaut (rendus, extraction de métadonnées et extraction de texte pour l’indexation).
   * Consultez [Configuration et utilisation des microservices de ressources](/help/assets/asset-microservices-configure-and-use.md)
   * Pour que les étapes de workflow personnalisées soient intégrées au traitement, vous pouvez utiliser les workflows [de](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows) post-traitement..
* Les ressources qui arrivent par le biais du gestionnaire de modules nécessitent un retraitement manuel à l’aide de l’action **[!UICONTROL Retraiter les ressources]** dans l’interface Assets.

Les rendus standard générés avec les microservices de ressources sont stockés de manière rétrocompatible dans les nœuds du référentiel de ressources (conventions d’affectation de noms identiques).

## Développement et test de microservices de ressources {#asset-microservices}

Les microservices de ressources offrent un traitement évolutif et résilient des ressources à l’aide des services cloud. Adobe gère les services cloud pour un traitement optimal des différents types de ressources et des options de traitement. L’utilisation des microservices de ressources permet de se passer d’outils et de méthodes de rendu tiers (comme ImageMagick) et de simplifier les configurations, tout en fournissant des fonctionnalités prêtes à l’emploi pour les types de fichiers courants. Vous pouvez désormais traiter un [large éventail de types de fichiers](/help/assets/file-format-support.md), dans des formats prêts à l’emploi plus nombreux que les versions précédentes d’Experience Manager. Par exemple, l’extraction de miniatures des formats PSD et PSB est désormais possible, car elle nécessitait auparavant des solutions tierces telles qu’ImageMagick. Vous ne pouvez pas utiliser les configurations complexes d’ImageMagick pour la configuration des [!UICONTROL Profils de traitement]. Utilisez [!DNL Dynamic Media] pour le transcodage Fmpeg avancé des vidéos et des profils de traitement pour [le transcodage de base des vidéos MP4](/help/assets/manage-video-assets.md#transcode-video).

Les microservices de ressources, natifs dans le cloud, sont automatiquement mis en service et connectés à Experience Manager dans les programmes et environnements clients gérés dans Cloud Manager. Pour étendre ou personnaliser Experience Manager, les développeurs peuvent utiliser le contenu existant ou les ressources dont les rendus sont générés dans un environnement cloud, afin de tester et valider leur code avec des ressources (en les utilisant, les affichant et les téléchargeant).

Pour effectuer une validation de bout en bout du code et du processus, y compris l’ingestion et le traitement des ressources, déployez les modifications de code dans un environnement de développement cloud à l’aide [du pipeline](/help/implementing/cloud-manager/configure-pipeline.md) et testez-les avec l’exécution complète du traitement des microservices de ressources.

## Suppression de l’interface utilisateur classique {#classic-ui}

L’interface utilisateur classique n’est plus disponible dans Experience Manager as a [!DNL Cloud Service]. L’interface standard est l’interface utilisateur tactile.

>[!MORELIKETHIS]
>
>* [Un  [!DNL Adobe Experience Manager] toas d&#39;introduction [!DNL Cloud Service]](/help/overview/introduction.md)
>* [présentation de  [!DNL Experience Manager] as a [!DNL Cloud Service] - Nouveautés et différences](/help/overview/what-is-new-and-different.md)
>* [architecture](/help/core-concepts/architecture.md) de [!DNL Experience Manager] en tant que [!DNL Cloud Service]
>* [Changements notables  [!DNL Experience Manager] en tant que [!DNL Cloud Service]](/help/release-notes/aem-cloud-changes.md)
>* [Changements notables  [!DNL Experience Manager Sites] en tant que [!DNL Cloud Service]](/help/sites-cloud/sites-cloud-changes.md)
>* [[!DNL Experience Manager] as a [!DNL Cloud Service] Tutoriels](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/overview.html)

