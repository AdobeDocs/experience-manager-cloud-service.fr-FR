---
title: Changements notables dans  [!DNL Adobe Experience Manager Assets] en tant que  [!DNL Cloud Service]
description: Modifications notables apportées à  [!DNL Adobe Experience Manager Assets] in [!DNL Experience Manager] as a [!DNL Cloud Service] par rapport à [ !DNL Adobe Experience Manager 6.5.
translation-type: tm+mt
source-git-commit: 6dc6445e4019664525629fe2204d255cfee37a81
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 26%

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
* L’écriture différée des métadonnées n’est pas prise en charge. Voir [écriture différée des métadonnées dans [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/xmp-writeback.html).
* Les ressources transférées à l’aide de Package Manager doivent être retraitées manuellement à l’aide de l’action **[!UICONTROL Retraiter l’actif]** de l’interface utilisateur [!DNL Assets].
* [!DNL Assets] ne détecte pas automatiquement le type MIME des ressources téléchargées. Un fichier numérique sans extension ou avec une extension incorrecte n’est pas traité comme vous le souhaitez. Par exemple, lors du transfert de ces ressources, rien ne se produit ou un profil de traitement incorrect peut s’appliquer à la ressource. Les utilisateurs peuvent toujours stocker les fichiers binaires sans extension dans la gestion des actifs numériques. Voir [détection de type MIME dans [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/detect-asset-mime-type-with-tika.html).
* [!DNL Experience Manager] car ne  [!DNL Cloud Service] génère pas de sous-ressources pour les actifs composés. Voir [création de sous-ressources dans  [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/managing-linked-subassets.html#generate-subassets).
* [!DNL Assets] L’expérience de page d&#39;accueil n’est pas disponible. Voir [[!DNL Assets] Home Page experience in [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/assets-home-page.html).
* La détection des actifs de duplicata fonctionne différemment de [comment elle fonctionnait dans [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/duplicate-detection.html).
* Pour les rendus FPO (placement uniquement), les rendus sont générés différemment par rapport aux versions [!DNL Experience Manager] précédentes. Voir [Rendu FPO pour [!DNL Experience Manager] sous la forme  [!DNL Cloud Service]](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/configure-aem-assets-for-asset-link.ug.html).
* Lorsqu’une archive ZIP est téléchargée, [!DNL Experience Manager] en tant que [!DNL Cloud Service] n’extrait pas les ressources regroupées dans l’archive. Voir [extraction ZIP dans  [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-assets.htmln#extractzip).

Les rendus standard générés avec les microservices de ressources sont stockés de manière rétrocompatible dans les noeuds du référentiel de ressources en appliquant les mêmes conventions d’affectation de nom.

## Développement et test de microservices de ressources {#asset-microservices}

Les microservices de ressources offrent un traitement évolutif et résilient des ressources à l’aide des services cloud. Adobe gère les services cloud pour un traitement optimal des différents types de ressources et des options de traitement. L’utilisation des microservices de ressources permet de se passer d’outils et de méthodes de rendu tiers (comme ImageMagick) et de simplifier les configurations, tout en fournissant des fonctionnalités prêtes à l’emploi pour les types de fichiers courants. Vous pouvez désormais traiter un [large éventail de types de fichiers](/help/assets/file-format-support.md), dans des formats prêts à l’emploi plus nombreux que les versions précédentes d’Experience Manager. Par exemple, l’extraction de miniatures des formats PSD et PSB est désormais possible, car elle nécessitait auparavant des solutions tierces telles qu’ImageMagick. Vous ne pouvez pas utiliser les configurations complexes d’ImageMagick pour la configuration des [!UICONTROL Profils de traitement]. Utilisez [!DNL Dynamic Media] pour le transcodage Fmpeg avancé des vidéos et des profils de traitement pour [le transcodage de base des vidéos MP4](/help/assets/manage-video-assets.md#transcode-video).

Asset microservices est un service natif au cloud qui est automatiquement mis en service et connecté à [!DNL Experience Manager] dans les programmes et environnements clients gérés dans Cloud Manager. Pour étendre ou personnaliser [!DNL Experience Manager], les développeurs peuvent utiliser le contenu ou les ressources existants avec des rendus générés dans un environnement cloud, afin de tester et de valider leur code à l’aide, de l’affichage et du téléchargement des ressources.

Pour effectuer une validation de bout en bout du code et du processus, y compris l’ingestion et le traitement des ressources, déployez les modifications de code dans un environnement de développement cloud à l’aide [du pipeline](/help/implementing/cloud-manager/configure-pipeline.md) et testez-les avec l’exécution complète du traitement des microservices de ressources.

## Suppression de l’interface utilisateur classique {#classic-ui}

L’interface utilisateur classique n’est plus disponible dans [!DNL Experience Manager] en tant que [!DNL Cloud Service]. Seule l’interface utilisateur tactile est disponible.

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

