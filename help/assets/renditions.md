---
title: Affichage et gestion des rendus dans Experience Manager Assets
description: Découvrez comment AEM Assets et Dynamic Media simplifient la gestion efficace des images avec des rendus d’image statiques et dynamiques.
exl-id: 006dc493-c400-4d0f-b314-c1978582b7fb
source-git-commit: 4627eb00ba910d1ad2920db15a87761bd7e4a0c0
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 1%

---

# Affichage et gestion des rendus dans Experience Manager Assets{#renditions}

Les rendus dans Adobe Experience Manager (AEM) sont des versions personnalisées des ressources numériques, telles que les images, conçues pour différents appareils et plateformes afin d’assurer des performances optimales. AEM facilite la création et la gestion de ces rendus, ce qui améliore l’expérience utilisateur. Vous pouvez créer des miniatures, optimiser les images pour le web ou mobile, ajouter des filigranes, afficher et télécharger des rendus dynamiques ou de recadrage intelligent, et bien plus encore.

Les paramètres d’image prédéfinis Dynamic Media et les rendus de recadrage intelligent favorisent une gestion systématique des images en phase avec les normes de la marque, ce qui optimise la cohésion de la marque. Cela simplifie le processus de localisation et d’utilisation rapide des rendus d’image dynamiques si nécessaire sans accès administrateur.

Les rendus sont classés comme statiques et dynamiques, chaque type présentant des fonctionnalités et des fonctionnalités uniques qui sont expliquées plus en détail.

## Rendus statiques {#static-renditions}

Les rendus statiques sont des versions prégénérées de ressources numériques, généralement créées lors de l’assimilation ou de la modification de ressources. Ces rendus sont optimisés à des fins et plateformes spécifiques, telles que les miniatures web, les formats compatibles avec les appareils mobiles pour le responsive design ou les versions haute résolution pour l’impression, ce qui garantit une expérience efficace et cohérente.
Formation [affichage et téléchargement](#view-dynamic-renditions) rendus statiques dans [!DNL Experience Manager Assets].

## Rendus dynamiques {#dynamic-renditions}

Les rendus dynamiques sont des versions personnalisées des ressources créées en temps réel pour répondre à des besoins spécifiques, tels que le redimensionnement des images en fonction de la résolution de l’appareil ou le recadrage pour s’adapter à différents formats.
Ces rendus permettent aux entreprises de fournir des expériences personnalisées et optimisées à divers besoins d’audience. Vous pouvez afficher et télécharger des rendus dynamiques dans [!DNL Experience Manager Assets].

### Avant de commencer

* Vous devez être un utilisateur Dynamic Media sous licence AEM.

* Utilisation [!UICONTROL Vue Admin] pour configurer :
   * [Recadrage intelligent de profils d’image](/help/assets/dynamic-media/image-profiles.md#creating-image-profiles)
   * [Paramètres d’image prédéfinis](/help/assets/dynamic-media/managing-image-presets.md)

  Vous pouvez [changer la vue](/help/assets/assets-view-introduction.md#how-to-access-assets-view) plus tard pour prévisualiser les rendus dynamiques dans la vue Assets.

### Affichage et téléchargement de rendus dynamiques {#view-renditions}

Pour afficher ou télécharger des rendus dynamiques dans [!DNL Experience Manager Assets], procédez comme suit :

1. Accédez à **[!UICONTROL Gestion des ressources]** > **[!UICONTROL Ressources]**.

1. Accédez au dossier de ressources approprié.

1. Cliquez sur l’image à afficher, puis cliquez sur **[!UICONTROL Détails]**.

1. Dans le menu de droite, cliquez sur **[!UICONTROL Rendus]**. <br> La variable **[!UICONTROL Rendus]** s’ouvre avec le panneau disponible **[!UICONTROL Dynamique]** et **[!UICONTROL Recadrage intelligent]** rendus.

   ![rendus dynamiques](assets/preset_smart_crop.png)
   <!-- ![dynamic renditions](assets/preset_smart_crop_view.png) -->

1. Cliquez sur le rendu que vous devez afficher ou télécharger.

1. Cliquez sur le bouton ![icône de téléchargement](assets/do-not-localize/download-icon.png) en regard du rendu dynamique à télécharger. <br> Vous pouvez également sélectionner le rendu d’image, puis cliquer sur **[!UICONTROL Télécharger le rendu]** en bas de l’écran.

   Vous pouvez cliquer sur le bouton ![icône de téléchargement](assets/do-not-localize/download-icon.png) icône disponible en haut de **[!UICONTROL Recadrage intelligent]** section rendus pour télécharger tous les rendus de recadrage intelligent disponibles pour cette ressource.

>[!NOTE]
>
>Les rendus dynamiques ne sont visibles que si les ressources sont chargées à partir de la vue Admin.