---
title: Affichage et gestion des rendus dans Experience Manager Assets
description: Découvrez comment AEM Assets et Dynamic Media simplifient la gestion efficace des images avec des rendus d’image statiques et dynamiques.
exl-id: 006dc493-c400-4d0f-b314-c1978582b7fb
feature: Renditions
role: User
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 2%

---

# Affichage et gestion des rendus dans Experience Manager Assets{#renditions}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [ Bonnes pratiques en matière de métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Dynamic Media avec fonctionnalités OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation destinée aux développeurs AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Les rendus dans Adobe Experience Manager (AEM) sont des versions personnalisées des ressources numériques, telles que les images, conçues pour différents appareils et plateformes afin d’assurer des performances optimales. AEM facilite la création et la gestion de ces rendus, ce qui améliore l’expérience utilisateur. Vous pouvez créer des miniatures, optimiser les images pour le web ou mobile, ajouter des filigranes, afficher et télécharger des rendus dynamiques ou de recadrage intelligent, et bien plus encore.

Les paramètres d’image prédéfinis Dynamic Media et les rendus de recadrage intelligent favorisent une gestion systématique des images en phase avec les normes de la marque, ce qui optimise la cohésion de la marque. Cela simplifie le processus de localisation et d’utilisation rapide des rendus d’image dynamiques si nécessaire sans accès administrateur.

Les rendus sont classés comme statiques et dynamiques, chaque type présentant des fonctionnalités et des fonctionnalités uniques qui sont expliquées plus en détail.

## Rendus statiques {#static-renditions}

Les rendus statiques sont des versions prégénérées de ressources numériques, généralement créées lors de l’assimilation ou de la modification de ressources. Ces rendus sont optimisés à des fins et plateformes spécifiques, telles que les miniatures web, les formats compatibles avec les appareils mobiles pour le responsive design ou les versions haute résolution pour l’impression, ce qui garantit une expérience efficace et cohérente.
Découvrez [comment afficher et télécharger](#view-dynamic-renditions) rendus statiques dans [!DNL Experience Manager Assets].

## Rendus dynamiques {#dynamic-renditions}

Les rendus dynamiques sont des versions personnalisées des ressources créées en temps réel pour répondre à des besoins spécifiques, tels que le redimensionnement des images en fonction de la résolution de l’appareil ou le recadrage pour s’adapter à différents formats.
Ces rendus permettent aux entreprises de fournir des expériences personnalisées et optimisées à divers besoins d’audience. Vous pouvez afficher et télécharger des rendus dynamiques dans [!DNL Experience Manager Assets].

### Avant de commencer

* Vous devez être un utilisateur Dynamic Media sous licence AEM.

* Utilisez [!UICONTROL Admin view] pour configurer :
   * [Profils d’image avec recadrage intelligent](/help/assets/dynamic-media/image-profiles.md#creating-image-profiles)
   * [Paramètres d’image prédéfinis](/help/assets/dynamic-media/managing-image-presets.md)

  Vous pouvez [changer de vue](/help/assets/assets-view-introduction.md#how-to-access-assets-view) ultérieurement pour prévisualiser les rendus dynamiques dans la vue Assets.

### Affichage et téléchargement de rendus dynamiques {#view-renditions}

Pour afficher ou télécharger les rendus dynamiques des images dans [!DNL Experience Manager Assets], procédez comme suit :

1. Accédez à **[!UICONTROL Gestion Assets]** > **[!UICONTROL Assets]**.

1. Accédez au dossier de ressources approprié.

1. Cliquez sur l&#39;image à afficher, puis sur **[!UICONTROL Details]**.

1. Dans le menu de droite, cliquez sur **[!UICONTROL Rendus]**. <br> Le panneau **[!UICONTROL Rendus]** s’ouvre avec les rendus **[!UICONTROL Dynamique]** et **[!UICONTROL Recadrage intelligent]** disponibles.

   ![rendus dynamiques](assets/preset_smart_crop.png)
   <!-- ![dynamic renditions](assets/preset_smart_crop_view.png) -->

1. Cliquez sur le rendu que vous devez afficher ou télécharger.

1. Cliquez sur l’icône ![télécharger](assets/do-not-localize/download-icon.png) en regard du rendu dynamique que vous devez télécharger. <br> Vous pouvez également sélectionner le rendu d’image, puis cliquer sur l’option **[!UICONTROL Télécharger le rendu]** en bas de la page.

   Vous pouvez cliquer sur l’icône ![Télécharger l’icône](assets/do-not-localize/download-icon.png) disponible en haut de la section **[!UICONTROL Recadrage intelligent]** pour télécharger tous les rendus de recadrage intelligent pour cette ressource.

>[!NOTE]
>
>Les rendus dynamiques ne sont visibles que si les ressources sont chargées à partir de la vue Admin.
