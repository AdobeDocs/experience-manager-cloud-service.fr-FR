---
title: Changements notables dans les ressources d’Adobe Experience Manager en tant que service Cloud
description: Modifications notables apportées aux ressources Adobe Experience Manager dans le service AEM Cloud par rapport à Adobe Experience Manager 6.5.
translation-type: tm+mt
source-git-commit: ab79c3dabb658e242df08ed065ce99499c9b7357

---


# Notable changes to Experience Manager Assets as a Cloud Service {#notable-changes}

Adobe Experience Manager en tant que service Cloud offre de nombreuses nouvelles fonctionnalités et possibilités de gestion de vos projets AEM. Cependant, il existe de nombreuses différences entre les ressources Experience Manager sur site ou dans Adobe Managed Service par rapport à Experience Manager en tant que service Cloud. Ce  souligne les différences importantes.

>[!NOTE]
>
>Ce met en évidence les modifications notables apportées aux ressources Experience Manager en tant que service Cloud. Voir les [modifications génériques apportées à Experience Manager en tant que service](/help/release-notes/aem-cloud-changes.md)Cloud.

Les principales différences par rapport à Experience Manager 6.5 se situent dans les domaines suivants :

* [Importation de ressources](#asset-ingestion)
* [Suppression de l’interface utilisateur classique](#classic-ui)

## Importation de ressources {#asset-ingestion}

Le transfert des ressources a été optimisé pour plus d’efficacité en permettant une meilleure mise à l’échelle de l’assimilation des ressources et des téléchargements plus rapides. Les fonctionnalités du produit (interfaces utilisateur Web, clients de bureau) ont été mises à jour. Cela peut toutefois avoir un impact sur une certaine personnalisation existante.

* Experience Manager applique le principe d’accès binaire direct pour le transfert et le téléchargement et les microservices de ressources pour le traitement des ressources. Voir [Présentation de l’assimilation](/help/assets/asset-microservices-overview.md)de ressources.
   * Transfert de ressources [avec accès](/help/assets/asset-microservices-overview.md#asset-upload-with-direct-binary-access)binaire direct.
   * Pour plus d’informations techniques, reportez-vous à la section sur le protocole de téléchargement binaire [direct et les API](/help/assets/developer-reference-material-apis.md#overview-binary-upload).
* La mise à jour **[!UICONTROL par défaut des ressources]** DAM du processus dans les versions précédentes d’AEM n’est plus disponible. Au lieu de cela, les microservices de ressources fournissent un service évolutif et facilement disponible qui couvre la plupart du traitement des ressources par défaut (rendus, métadonnées  , texte  pour l’indexation).
   * Voir [Configuration et utilisation des microservices de ressources](/help/assets/asset-microservices-configure-and-use.md)
   * Pour que les étapes de flux de travail personnalisées soient incluses dans le traitement, vous pouvez utiliser les [de post-traitement du](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows) .
* Les ressources introduites via Package Manager nécessitent un retraitement manuel à l’aide de l’action **[!UICONTROL Retraiter les ressources]** dans l’interface Ressources.

Les rendus standard générés avec les microservices de ressources sont stockés de manière rétrocompatible dans les noeuds du référentiel de ressources (conventions d’affectation de nom identiques).

## Développement et test de microservices de ressources {#developing-testing-asset-microservices}

Les microservices de ressources sont un service cloud natif qui est automatiquement mis en service et connecté à Experience Manager dans les  de clients et  les  gérés dans Cloud Manager. Les développeurs qui travaillent à étendre Experience Manager ou à personnaliser peuvent utiliser le contenu existant (ou les ressources dont les rendus sont générés dans un Cloud  ) pour tester et valider leur code à l’aide, de l’affichage et du téléchargement de ressources.

Pour effectuer une validation de bout en bout du code et du processus, y compris l’assimilation et le traitement des ressources, déployez les modifications de code dans un de développement cloud  à l’aide du pipeline et testez avec l’exécution complète du traitement des microservices de ressources.

## Suppression de l’interface utilisateur classique {#classic-ui}

L’interface utilisateur classique n’est plus disponible dans Experience Manager en tant que service Cloud.
