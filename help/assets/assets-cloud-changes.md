---
title: Modifications notables d’Adobe Experience Manager Assets as a Cloud Service
description: Modifications notables d’Adobe Experience Manager Assets dans AEM Cloud Service par rapport à Experience Manager 6.5
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Modifications notables d’Experience Manager Assets as a Cloud Service {#notable-changes}

Adobe Experience Manager as a Cloud Service offre de nombreuses nouvelles fonctionnalités et possibilités de gestion pour vos projets AEM. Cependant, il existe plusieurs différences entre les ressources Experience Manager sur site ou dans Adobe Managed Service par rapport à Experience Manager as a Cloud Service. Ce document met en lumière les différences importantes.

>[!NOTE]
>
>Ce document met en évidence les modifications notables apportées à Experience Manager Assets as a Cloud Service. Consultez les [modifications génériques apportées à Experience Manager as a Cloud Service](/help/release-notes/aem-cloud-changes.md).

Les principales différences par rapport à Experience Manager 6.5 se situent dans les domaines suivants :

* [L’importation de ressources](#asset-ingestion)
* [Suppression de l’interface utilisateur de la version classique](#classic-ui)

## Importation de ressources {#asset-ingestion}

Le transfert des ressources a été optimisé pour être plus efficace, ce qui permet une meilleure mise à l’échelle de l’assimilation des ressources et des téléchargements plus rapides. Les fonctionnalités du produit (interfaces utilisateur web, clients de bureau) ont été mises à jour. Cela peut toutefois avoir un impact sur certains codes personnalisés existants.

* Experience Manager applique le principe d’accès binaire direct pour le transfert et le téléchargement et les microservices de ressources pour le traitement des ressources. Consultez la [Présentation de l’assimilation de ressources](/help/assets/asset-microservices-overview.md)
   * Transfert de ressources [avec accès binaire direct](/help/assets/asset-microservices-overview.md#asset-upload-with-direct-binary-access)
   * Pour plus d’informations techniques, reportez-vous à la section sur le protocole de téléchargement binaire [direct et les API.](/help/assets/developer-reference-material-apis.md#overview-binary-upload)
* Le workflow par défaut de **[!UICONTROL Mise à jour des ressources DAM]** dans les versions précédentes d’AEM n’est plus disponible. Au lieu de cela, les microservices de ressources fournissent un service évolutif et facilement disponible qui couvre la plupart du traitement des ressources par défaut (rendus, extraction de métadonnées, extraction de texte pour indexation).
   * Consultez [Configuration et utilisation des microservices de ressources](/help/assets/asset-microservices-configure-and-use.md)
   * Pour que les étapes de workflow personnalisées soient intégrées au traitement, vous pouvez utiliser les workflows [de](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows) post-traitement.
* Les ressources qui arrivent par le biais de Package Manager nécessitent un retraitement manuel à l’aide de l’action **[!UICONTROL Retraiter les ressources]** dans l’interface d’Assets.

Les rendus standard générés avec les microservices de ressources sont stockés de manière rétrocompatible dans les nœuds du référentiel de ressources (conventions d’affectation de noms identiques).

## Développement et test de microservices de ressources {#developing-testing-asset-microservices}

Les microservices de ressources sont un Cloud Service natif qui est automatiquement mis en service et connecté à Experience Manager dans les programmes et environnements clients gérés dans Cloud Manager. Les développeurs qui travaillent à étendre Experience Manager ou à permettre sa personnalisation peuvent utiliser le contenu existant (ou les ressources dont les rendus sont générés dans un environnement cloud) pour tester et valider leur code à l’aide, de l’affichage et du téléchargement des ressources.

Pour effectuer une validation de bout en bout du code et du processus, y compris l’assimilation et le traitement des ressources, déployez les modifications de code dans un environnement de développement cloud à l’aide du pipeline et testez-les avec l’exécution complète du traitement des microservices de ressources.

## Suppression de l’interface utilisateur de la version classique {#classic-ui}

L’interface utilisateur Classic n’est plus disponible dans Experience Manager as a Cloud Service.
