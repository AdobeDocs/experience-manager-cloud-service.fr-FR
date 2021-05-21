---
title: Modifications notables apportées à [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service]
description: Modifications notables apportées à  [!DNL Adobe Experience Manager Assets] in [!DNL Experience Manager] as a [!DNL Cloud Service] par rapport à [!DNL Adobe Experience Manager 6.5].
feature: Informations sur la version
role: Business Practitioner,Leader,Architect,Administrator
exl-id: 93e7dbcd-016e-4ef2-a1cd-c554efb5ad34
source-git-commit: 1fa5b6e183cf9c292cd5485e20a2406576a40319
workflow-type: tm+mt
source-wordcount: '778'
ht-degree: 73%

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

Les rendus standard générés avec les microservices de ressources sont stockés de manière rétrocompatible dans les noeuds du référentiel de ressources en utilisant les mêmes conventions d’affectation de noms.

## Développement et test de microservices de ressources {#asset-microservices}

Les microservices de ressources offrent un traitement évolutif et résilient des ressources à l’aide des services cloud. Adobe gère les services cloud pour un traitement optimal des différents types de ressources et des options de traitement. L’utilisation des microservices de ressources permet de se passer d’outils et de méthodes de rendu tiers (comme ImageMagick) et de simplifier les configurations, tout en fournissant des fonctionnalités prêtes à l’emploi pour les types de fichiers courants. Vous pouvez désormais traiter un [large éventail de types de fichiers](/help/assets/file-format-support.md), dans des formats prêts à l’emploi plus nombreux que les versions précédentes d’Experience Manager. Par exemple, l’extraction de miniatures des formats PSD et PSB est désormais possible ; elle nécessitait auparavant des solutions tierces telles qu’ImageMagick. Vous ne pouvez pas utiliser les configurations complexes d’ImageMagick pour la configuration des [!UICONTROL Profils de traitement]. Utilisez [!DNL Dynamic Media] pour le transcodage FFmpeg avancé des vidéos et les profils de traitement pour le [transcodage de base des vidéos MP4](/help/assets/manage-video-assets.md#transcode-video).

Les microservices de ressources, natifs dans le cloud, sont automatiquement mis en service et connectés à [!DNL Experience Manager] dans les programmes et environnements clients gérés dans Cloud Manager. Pour étendre ou personnaliser[!DNL Experience Manager], les développeurs peuvent utiliser le contenu existant ou les ressources dont les rendus sont générés dans un environnement cloud, afin de tester et valider leur code avec des ressources (en les utilisant, les affichant et les téléchargeant).

Pour effectuer une validation de bout en bout du code et du processus, y compris l’ingestion et le traitement des ressources, déployez les modifications de code dans un environnement de développement cloud à l’aide [du pipeline](/help/implementing/cloud-manager/configure-pipeline.md) et testez-les avec l’exécution complète du traitement des microservices de ressources.


## Parité des fonctionnalités avec [!DNL Experience Manager] 6.5 {#cloud-service-feature-status}

[!DNL Experience Manager] as a  [!DNL Cloud Service] introduit de nombreuses nouvelles fonctionnalités et des méthodes plus performantes pour que les fonctionnalités existantes fonctionnent. Cependant, lorsque vous passez de [!DNL Experience Manager] 6.5 à [!DNL Experience Manager] en tant que [!DNL Cloud Service], vous pouvez remarquer que certaines fonctionnalités fonctionnent différemment, ne sont pas disponibles ou sont partiellement disponibles. Voici une liste de ces fonctionnalités. En outre, voir la section [Fonctionnalités obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

| Fonction ou cas d’utilisation | État dans [!DNL Experience Manager] en tant que [!DNL Cloud Service] | Commentaires |
|-----|-----|-----|
| [Dupliquer la détection des ressources](/help/assets/manage-digital-assets.md#detect-duplicate-assets) | Fonctionne différemment. | Voir [son fonctionnement dans  [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/duplicate-detection.html?lang=fr). |
| [Pour les rendus FPO (Placement uniquement)](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/configure-aem-assets-for-asset-link.ug.html#configfporendition) | Fonctionnement différent |  |
| Écriture différée des métadonnées | Fonctionnement différent | Désactivé par défaut. Activez le lanceur de workflow correspondant si nécessaire. L’écriture différée est gérée par les microservices de ressources. |
| Traitement des ressources chargées à l’aide du gestionnaire de modules | Nécessite une intervention manuelle. | Retraiter manuellement à l’aide de l’action **[!UICONTROL Retraiter la ressource]**. |
| Détection du type MIME | Pas de prise en charge. | Si vous chargez une ressource numérique sans extension ou avec une extension incorrecte, elle peut ne pas être traitée comme vous le souhaitez. Les utilisateurs peuvent toujours stocker les fichiers binaires sans extension dans le module DAM. Voir la section [Détection de type MIME dans [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/detect-asset-mime-type-with-tika.html?lang=fr). |
| Génération de sous-ressources pour les ressources composites | Pas de prise en charge. | Les cas d’utilisation dépendants ne sont pas remplis. Par exemple, l’annotation de fichiers PDF de plusieurs pages est affectée. Voir la section [Création de sous-ressources dans [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/managing-linked-subassets.html?lang=fr#generate-subassets). |
| Page d’accueil | Pas de prise en charge. | Voir la section [[!DNL Assets] Home Page experience in [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/assets-home-page.html?lang=fr) |
| Extraction de ressources à partir de l’archive ZIP | Pas de prise en charge. | Voir la section [extraction ZIP dans [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-assets.html#extractzip). |
| IU classique | Pas de prise en charge. | Seule l’IU tactile est disponible. |

>[!MORELIKETHIS]
>
>Les ressources suivantes sont disponibles pour [!DNL Experience Manager] as a [!DNL Cloud Service] :
>
>* [Liste des fonctionnalités obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md)
* [Une introduction](/help/overview/introduction.md)
* [Nouveautés et différences](/help/overview/what-is-new-and-different.md)
* [L’architecture](/help/core-concepts/architecture.md)
* [Modifications notables](/help/release-notes/aem-cloud-changes.md)
* [Modifications notables [!DNL Sites]](/help/sites-cloud/sites-cloud-changes.md)
* [Tutoriels vidéo](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/overview.html?lang=fr)

