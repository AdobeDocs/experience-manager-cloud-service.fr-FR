---
title: Modifications notables d’Adobe Experience Manager Assets as a Cloud Service
description: Changements notables des ressources Adobe Experience Manager dans AEM Cloud Service par rapport à Adobe Experience Manager 6.5.
translation-type: tm+mt
source-git-commit: 37ff6912837ba78c90526e8f8322b9002e9a4304

---


# Modifications notables d’Experience Manager Assets as a Cloud Service {#notable-changes}

Adobe Experience Manager as a Cloud Service offre de nombreuses nouvelles fonctionnalités et possibilités de gestion pour vos projets AEM. Cependant, il existe de nombreuses différences entre les ressources Experience Manager sur site ou dans Adobe Managed Service par rapport à Experience Manager en tant que service Cloud. Ce document met en évidence les différences importantes entre les fonctionnalités Ressources. For other changes, see the generic [changes to Experience Manager as a Cloud Service](/help/release-notes/aem-cloud-changes.md).

Les principales différences par rapport à Experience Manager 6.5 se situent dans les domaines suivants :

* [Importation et transfert](#asset-ingestion)de ressources.
* [Microservices de ressources pour le traitement](#asset-microservices)cloud.
* [Suppression de l’interface utilisateur de la version classique](#classic-ui).

## Importation et transfert de ressources {#asset-ingestion}

Le transfert des ressources a été optimisé pour plus d’efficacité en permettant une meilleure mise à l’échelle de l’assimilation des ressources et des téléchargements plus rapides. Les fonctionnalités du produit (interfaces utilisateur web, clients de bureau) ont été mises à jour. Cependant, cela peut avoir un impact sur certaines personnalisations existantes.

* Experience Manager applique le principe d’accès binaire direct pour le transfert et le téléchargement et les microservices de ressources pour le traitement des ressources. Consultez la [Présentation de l’assimilation de ressources](/help/assets/asset-microservices-overview.md).
   * Transfert de ressources [avec accès binaire direct](/help/assets/asset-microservices-overview.md#asset-upload-with-direct-binary-access).
   * For technical details, see  of [direct binary upload protocol and APIs](/help/assets/developer-reference-material-apis.md#overview-binary-upload).
* Le workflow par défaut de **[!UICONTROL Mise à jour des ressources DAM]** dans les versions précédentes d’AEM n’est plus disponible. Au lieu de cela, les microservices de ressources fournissent un service évolutif et facilement disponible qui couvre la plupart du traitement des ressources par défaut (rendus, extraction de métadonnées, extraction de texte pour indexation)..
   * Consultez [Configuration et utilisation des microservices de ressources](/help/assets/asset-microservices-configure-and-use.md)
   * Pour que les étapes de workflow personnalisées soient intégrées au traitement, vous pouvez utiliser les workflows [de](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows) post-traitement..
* Assets that come in via Package Manager require manual reprocessing using the **[!UICONTROL Reprocess Asset]** action in the Assets interface.

Les rendus standard générés avec les microservices de ressources sont stockés de manière rétrocompatible dans les nœuds du référentiel de ressources (conventions d’affectation de noms identiques).

## Développement et test de microservices de ressources {#asset-microservices}

Les microservices de ressources offrent un traitement évolutif et résilient des ressources à l’aide des services cloud. Adobe gère les services cloud pour une gestion optimale des différents types de ressources et des différentes options de traitement. Les microservices de ressources permettent d’éviter la nécessité d’utiliser des outils et méthodes de rendu tiers (tels que ImageMagick) et de simplifier les configurations, tout en offrant des fonctionnalités prêtes à l’emploi pour les types de fichiers courants. Vous pouvez désormais traiter un [large éventail de types](/help/assets/file-format-support.md) de fichiers couvrant davantage de formats prêts à l’emploi que les versions précédentes d’Experience Manager. Par exemple, l’extraction de miniatures des formats PSD et PSB est désormais possible, car elle nécessitait auparavant des solutions tierces telles que ImageMagick. Vous ne pouvez pas utiliser les configurations complexes d’ImageMagick pour la configuration des Profils [!UICONTROL de] traitement. Utilisez également [!DNL Dynamic Media] pour le transcodage Fmpeg des vidéos.

Asset microservices est un service natif au cloud qui est automatiquement mis en service et câblé vers Experience Manager dans les programmes et environnements clients gérés dans Cloud Manager. Pour étendre ou personnaliser Experience Manager, les développeurs peuvent utiliser le contenu ou les ressources existants avec des rendus générés dans un environnement cloud, afin de tester et de valider leur code à l’aide, de l’affichage et du téléchargement de ressources.

To do an end-to-end validation of the code and process including asset ingestion and processing, deploy the code changes to a cloud-dev environment using [the pipeline](/help/implementing/cloud-manager/configure-pipeline.md) and test with full execution of asset microservices processing.

## Suppression de l’interface utilisateur de la version classique {#classic-ui}

L’interface utilisateur Classic n’est plus disponible dans Experience Manager as a Cloud Service. L’interface standard est l’interface utilisateur tactile.
