---
title: Modifications notables apportées à [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service]
description: Modifications notables apportées à [!DNL Adobe Experience Manager Assets] in [!DNL Experience Manager] as a [!DNL Cloud Service] par rapport à [!DNL Adobe Experience Manager 6.5].
translation-type: tm+mt
source-git-commit: 201abba4352362b1bb97b6a25bd84f95e8ed8483
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 57%

---


# Modifications notables apportées à [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#notable-changes}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] offre de nombreuses nouvelles fonctionnalités et possibilités de gestion pour vos projets Experience Manager. Il existe de nombreuses différences entre [!DNL Experience Manager Assets] sur site ou hébergé sous la forme Adobe Managed Service par rapport à [!DNL Experience Manager] as a [!DNL Cloud Service]. Ce article met en évidence les différences importantes entre les fonctionnalités d’[!DNL Assets]

Les principales différences par rapport à [Experience Manager] 6.5 se situent dans les domaines suivants :

* [Ingestion, chargement et traitement de ressources](#asset-ingestion).
* [Microservices de ressources pour le traitement natif dans le cloud](#asset-microservices).
* [Suppression de l’interface utilisateur classique](#classic-ui).

## Ingestion et traitement de ressources {#asset-ingestion}

Le chargement des ressources est optimisé pour bénéficier d’une meilleure efficacité en permettant une évolutivité plus performante de l’ingestion, des chargements plus rapides, un traitement accéléré grâce aux microservices et une ingestion en masse. Les fonctionnalités du produit (interfaces utilisateur web, clients de bureau) ont été mises à jour. Cela peut également avoir un impact sur certaines personnalisations existantes.

* [!DNL Experience Manager] utilise le principe d’accès binaire direct pour charger et télécharger des ressources, ainsi que des microservices de ressources pour les traiter. Voir [Présentation des microservices](/help/assets/asset-microservices-overview.md).
   * Chargement de ressources [avec accès binaire direct](/help/assets/asset-microservices-overview.md#asset-upload-with-direct-binary-access).
   * Pour plus d’informations techniques, reportez-vous à la section sur le [protocole de chargement de binaire direct et les API](/help/assets/developer-reference-material-apis.md#upload-binary).
   * Pour une comparaison des méthodes d’API disponibles pour les opérations CRUD de base, voir [API et opérations relatives aux ressources](/help/assets/developer-reference-material-apis.md#use-cases-and-apis).
* Le workflow par défaut de **[!UICONTROL Mise à jour des ressources DAM]** des versions précédentes d’[!DNL Experience Manager] n’est plus disponible. Au lieu de cela, les microservices de ressources fournissent un service évolutif et facilement disponible qui couvre la plupart du traitement des ressources par défaut (rendus, extraction de métadonnées, extraction de texte pour indexation).
   * Voir [Configuration et utilisation des microservices de ressources](/help/assets/asset-microservices-configure-and-use.md)
   * Pour que les étapes de workflow personnalisées soient intégrées au traitement, vous pouvez utiliser les [workflows de post-traitement](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows)..

Les rendus standard générés avec les microservices de ressources sont stockés de manière rétrocompatible dans les noeuds du référentiel de ressources en appliquant les mêmes conventions d’affectation de nom.

## Développement et test de microservices de ressources {#asset-microservices}

Les microservices de ressources offrent un traitement évolutif et résilient des ressources à l’aide des services cloud. Adobe gère les services cloud pour un traitement optimal des différents types de ressources et des options de traitement. L’utilisation des microservices de ressources permet de se passer d’outils et de méthodes de rendu tiers (comme ImageMagick) et de simplifier les configurations, tout en fournissant des fonctionnalités prêtes à l’emploi pour les types de fichiers courants. Vous pouvez désormais traiter un [large éventail de types de fichiers](/help/assets/file-format-support.md), dans des formats prêts à l’emploi plus nombreux que les versions précédentes d’Experience Manager. Par exemple, l’extraction de miniatures des formats PSD et PSB est désormais possible ; elle nécessitait auparavant des solutions tierces telles qu’ImageMagick. Vous ne pouvez pas utiliser les configurations complexes d’ImageMagick pour la configuration des [!UICONTROL Profils de traitement]. Utilisez [!DNL Dynamic Media] pour le transcodage FFmpeg avancé des vidéos et les profils de traitement pour le [transcodage de base des vidéos MP4](/help/assets/manage-video-assets.md#transcode-video).

Asset microservices est un service natif au cloud qui est automatiquement mis en service et connecté à [!DNL Experience Manager] dans les programmes et environnements clients gérés dans Cloud Manager. Pour étendre ou personnaliser [!DNL Experience Manager], les développeurs peuvent utiliser le contenu ou les ressources existants avec des rendus générés dans un environnement cloud, afin de tester et de valider leur code à l’aide, de l’affichage et du téléchargement des ressources.

Pour effectuer une validation de bout en bout du code et du processus, y compris l’ingestion et le traitement des ressources, déployez les modifications de code dans un environnement de développement cloud à l’aide [du pipeline](/help/implementing/cloud-manager/configure-pipeline.md) et testez-les avec l’exécution complète du traitement des microservices de ressources.


## Parité des fonctionnalités avec [!DNL Experience Manager] 6.5 {#cloud-service-feature-status}

[!DNL Experience Manager] as a  [!DNL Cloud Service] introduit de nombreuses nouvelles fonctionnalités et des méthodes plus performantes pour que les fonctionnalités existantes fonctionnent. Cependant, lorsque vous passez de [!DNL Experience Manager] 6.5 à [!DNL Experience Manager] en tant que [!DNL Cloud Service], vous remarquerez peut-être que certaines fonctionnalités fonctionnent différemment, ne sont pas disponibles ou sont disponibles partiellement. Voici une liste de ces fonctionnalités :

| Fonction ou cas d’utilisation | État dans [!DNL Experience Manager] en tant que [!DNL Cloud Service] | Commentaires |
|-----|-----|-----|
| [Détection des ressources de duplicata](/help/assets/manage-digital-assets.md#detect-duplicate-assets) | Fonctionne différemment. | Voir [comment il fonctionnait dans [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/duplicate-detection.html). |
| [Pour les rendus FPO (Placement uniquement)](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/configure-aem-assets-for-asset-link.ug.html#configfporendition) | Fonctionne différemment |  |
| Écriture différée des métadonnées | Pas de prise en charge. | Voir [écriture différée des métadonnées dans [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/xmp-writeback.html). |
| Traitement des fichiers transférés à l’aide de Package Manager | Il faut une intervention manuelle. | Retraiter manuellement à l’aide de l’action **[!UICONTROL Retraiter l’actif]**. |
| Détection du type MIME | Pas de prise en charge. | Si vous téléchargez un fichier numérique sans extension ou avec une extension incorrecte, il se peut qu’il ne soit pas traité comme vous le souhaitez. Les utilisateurs peuvent toujours stocker les fichiers binaires sans extension dans la gestion des actifs numériques. Voir [détection de type MIME dans [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/detect-asset-mime-type-with-tika.html). |
| Génération de sous-ressources pour les ressources composées | Pas de prise en charge. | Les cas d&#39;utilisation à charge ne sont pas satisfaits. Par exemple, l’annotation des fichiers PDF de plusieurs pages est affectée. Voir [création de sous-ressources dans  [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/managing-linked-subassets.html#generate-subassets). |
| Page d&#39;accueil | Pas de prise en charge. | Voir [[!DNL Assets] Home Page experience in [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/assets-home-page.html) |
| Extraction de fichiers de l’archive ZIP | Pas de prise en charge. | Voir [extraction ZIP dans  [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-assets.htmln#extractzip). |
| IU classique | Pas de prise en charge. | Seule l’interface utilisateur tactile est disponible. |

>[!MORELIKETHIS]
>
>Les ressources suivantes sont disponibles pour [!DNL Experience Manager] en tant que [!DNL Cloud Service] :
>
>* [Une introduction](/help/overview/introduction.md)
>* [Nouveautés et différences](/help/overview/what-is-new-and-different.md)
>* [L&#39;architecture](/help/core-concepts/architecture.md)
>* [Modifications notables](/help/release-notes/aem-cloud-changes.md)
>* [Modifications notables [!DNL Sites]](/help/sites-cloud/sites-cloud-changes.md)
>* [Didacticiels vidéo](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/overview.html?lang=fr)

