---
title: Changements notables dans  [!DNL Adobe Experience Manager Assets] en tant que  [!DNL Cloud Service]
description: Modifications notables apportées à  [!DNL Adobe Experience Manager Assets] in [!DNL Experience Manager] as a [!DNL Cloud Service] par rapport à [ !DNL Adobe Experience Manager 6.5.
translation-type: tm+mt
source-git-commit: ed449eea146ec18bdc4d25ae4938f9a36180037d
workflow-type: tm+mt
source-wordcount: '605'
ht-degree: 46%

---


# Modifications notables apportées à [!DNL Experience Manager Assets] en tant que [!DNL Cloud Service] {#notable-changes}

[!DNL Adobe Experience Manager] comme a  [!DNL Cloud Service] apporte de nombreuses nouvelles fonctionnalités et possibilités pour gérer vos projets Experience Manager. Il existe de nombreuses différences entre [!DNL Experience Manager Assets] sur site ou hébergé en tant que service géré par Adobe par rapport à [!DNL Experience Manager] en tant que [!DNL Cloud Service]. Cet article souligne les différences importantes entre les fonctionnalités [!DNL Assets].

Les principales différences par rapport à [Experience Manager] 6.5 se situent dans les domaines suivants :

* [Importation, transfert et traitement](#asset-ingestion) des ressources.
* [Microservices de ressources pour le traitement natif dans le cloud](#asset-microservices).
* [Suppression de l’interface utilisateur classique](#classic-ui).

## Importation et traitement des ressources {#asset-ingestion}

Le transfert des ressources est optimisé pour une efficacité optimale en permettant une meilleure mise à l’échelle de l’assimilation, des téléchargements plus rapides, un traitement plus rapide à l’aide de microservices et l’assimilation en masse. Les fonctionnalités du produit (interfaces utilisateur Web, clients de bureau) sont mises à jour. Cela peut également avoir un impact sur certaines personnalisations existantes.

* [!DNL Experience Manager] utilise le principe d’accès binaire direct pour télécharger et télécharger des ressources et utilise des microservices de ressources pour traiter des ressources. Voir [présentation des microservices](/help/assets/asset-microservices-overview.md).
   * Chargement de ressources [avec accès binaire direct](/help/assets/asset-microservices-overview.md#asset-upload-with-direct-binary-access).
   * Pour plus de détails techniques, voir [protocole de téléchargement binaire direct et API](/help/assets/developer-reference-material-apis.md#upload-binary).
   * Pour une comparaison des méthodes d’API disponibles pour les opérations CRUD de base, voir [APIs and asset operations](/help/assets/developer-reference-material-apis.md#use-cases-and-apis).
* Le flux de travaux par défaut **[!UICONTROL Mise à jour des ressources DAM]** dans les versions précédentes de [!DNL Experience Manager] n&#39;est plus disponible. Au lieu de cela, les microservices de ressources offrent un service évolutif et facilement disponible qui couvre la plupart du traitement des ressources par défaut (rendus, extraction de métadonnées et extraction de texte pour l’indexation).
   * Voir [configuration et utilisation des microservices de ressources](/help/assets/asset-microservices-configure-and-use.md)
   * Pour que les étapes de workflow personnalisées soient intégrées au traitement, vous pouvez utiliser les [workflows de post-traitement](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows)..
* Les ressources téléchargées à l’aide de Package Manager doivent être retraitées manuellement à l’aide de l’action **[!UICONTROL Retraiter l’actif]** de l’interface [!DNL Assets].
* Un fichier numérique sans extension ou avec une extension incorrecte n’est pas traité comme vous le souhaitez. Par exemple, lors du transfert de ces ressources, rien ne se produit ou un profil de traitement incorrect peut s’appliquer à la ressource. Les utilisateurs peuvent toujours stocker les fichiers binaires dans le module DAM.

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
>* [[!DNL Experience Manager] as a [!DNL Cloud Service] Tutoriels](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/overview.html?lang=fr)

