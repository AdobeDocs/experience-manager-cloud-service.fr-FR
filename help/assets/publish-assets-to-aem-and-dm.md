---
title: Publication rapide vers  [!DNL AEM and Dynamic Media]
description: La fonction Publication rapide dans vous  [!DNL Assets view]  de publier des ressources simultanément ou  [!DNL AEM and Dynamic Media] . Vous pouvez sélectionner des ressources et des dossiers et choisir de publier vers  [!DNL Dynamic Media]  ou  [!DNL AEM].
exl-id: 147c1c35-0d81-4458-b4ed-7541d2b0dd54
feature: Publishing, [!DNL Dynamic Media]
role: User
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1053'
ht-degree: 0%

---

# Publication d’Assets sur [!DNL AEM and Dynamic Media]{#Publish-Assets-to-AEM-and-Dynamic-Media}

[!DNL Experience Manager Assets] vous permet de publier rapidement des ressources dans [!DNL Experience Manager] et [!DNL Dynamic Media] à l’aide de l’[!DNL Assets view] . Cela vous permet de gérer vos ressources, puis de les publier à l’aide du [[!DNL Assets view]  sans passer par le  [!DNL Admin view]](/help/assets/overview.md##persona-based-experiences).

[!DNL Experience Manager Assets view] offre la possibilité de publier des ressources en [!DNL AEM] ou en [!DNL Dynamic Media], ou les deux en même temps. Vous pouvez publier des ressources lors du chargement, de la navigation et de la recherche de ressources. Toutes ces options de publication de ressources sont expliquées en détail dans cet article.

## Avant de commencer {#before-you-begin}

Configurez ces paramètres pour afficher les options de publication des [!DNL AEM and Dynamic Media] :

* Pour afficher les options de publication de [!DNL Dynamic Media], configurez les paramètres suivants à l’aide de la vue Administration :

   * [Créez une configuration  [!DNL Dynamic Media]  cloud](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services).
   * Définissez le mode de publication [!DNL Dynamic Media] au niveau du dossier. Vous pouvez également configurer ces paramètres lors de la création de la configuration [!DNL Dynamic Media] Cloud. Pour remplacer ces paramètres au niveau du dossier, voir [Configuration de la publication sélective au niveau du dossier dans [!DNL Dynamic Media]](/help/assets/dynamic-media/selective-publishing.md).

* Pour afficher les options de publication de [!DNL AEM], vous devez configurer le point d’entrée de publication [!DNL AEM] pour votre environnement.

## Publication d’Assets lors du chargement {#piblish-assets-during-upload}

Vous pouvez publier des ressources dans [!DNL AEM and Dynamic Media] lors du chargement de ressources dans un dossier. Les options de publication qui s’affichent dépendent des paramètres du mode de publication [!DNL Dynamic Media] du dossier dans lequel les ressources sont chargées. [!DNL Dynamic Media] mode de publication peut être défini sur :

* **[!UICONTROL Lors de l’activation] :** lorsque des ressources sont chargées dans ce dossier, vous devez d’abord les publier explicitement avant de fournir un lien d’URL/d’incorporation.

* **[!UICONTROL Immédiat] :** lorsque des ressources sont chargées dans ce dossier, le système les ingère dans Experience Manager et fournit instantanément l’URL/le code intégré.
* **[!UICONTROL Publication sélective] :** les Assets sont publiées selon votre choix [!DNL Experience Manager] ou à [!DNL Dynamic Media] pour diffusion dans le domaine public.

### [!UICONTROL &#x200B; Mode de publication Dynamic Media &#x200B;] défini sur [!UICONTROL Lors de l’activation] {#dynamic-media-publish-mode-set-to-upon-activation}

Pour publier des ressources lors de leur chargement dans un dossier dont le [!DNL Dynamic Media Publish Mode] est défini sur **[!UICONTROL Lors de l’activation]** :

1. Cliquez sur **[!UICONTROL Ajouter Assets]** > **[!UICONTROL Parcourir]** > **[!UICONTROL Parcourir les fichiers]** pour accéder au dossier approprié pour charger des ressources. La section **[!UICONTROL Options de publication]** affiche le **[!UICONTROL mode de publication DM]** sous la forme **[!UICONTROL Lors de l’activation]**.

   ![Charger l’image lors de l’activation](/help/assets/assets/upload-uactivation.svg)

1. Sélectionnez **[!UICONTROL Publier vers AEM et Dynamic Media]**, puis cliquez sur **[!UICONTROL Télécharger]**. Les ressources sont publiées en même temps sur [!DNL AEM and Dynamic Media]. Pour afficher le statut de publication mis à jour de ces ressources, voir [Vérification du statut de publication](#check-publish-status).

### [!UICONTROL Mode de publication Dynamic Media] défini sur [!UICONTROL Immédiat] {#dynamic-media-publish-mode-set-to-immediate}

Pour publier des ressources lors de leur chargement dans un dossier dont le [!UICONTROL Mode de publication Dynamic Media] est défini sur **[!UICONTROL Immédiat]** :

1. Cliquez sur **[!UICONTROL Ajouter Assets]** > **[!UICONTROL Parcourir]** > **[!UICONTROL Parcourir les fichiers]** pour accéder au dossier approprié pour charger des ressources. La section **[!UICONTROL Options de publication]** affiche le **[!UICONTROL mode de publication DM]** en tant que **[!UICONTROL Immédiat]**.

   ![image de chargement de fichier - mode immédiat](/help/assets/assets/resized-image-pdf-svg-new.svg)

   Étant donné que le [!UICONTROL mode de publication Dynamic Media] est **[!UICONTROL immédiat]**, les ressources chargées sont automatiquement publiées sur [!DNL Dynamic Media] lorsque vous cliquez sur **[!UICONTROL Télécharger]**.

1. Sélectionnez **Publier vers AEM** pour publier les ressources chargées dans [!DNL AEM] et cliquez sur **[!UICONTROL Télécharger]**.

   Si vous sélectionnez **Publier vers AEM**, les ressources sont publiées sur [!DNL AEM and Dynamic Media], sinon elles sont publiées sur [!DNL Dynamic Media].

   Pour afficher le statut de publication mis à jour de ces ressources, voir [Vérification du statut de publication](#check-publish-status).

### [!UICONTROL &#x200B; Mode de publication Dynamic Media &#x200B;] défini sur [!UICONTROL &#x200B; Publication sélective &#x200B;] {#dynamic-media-publish-mode-set-to-selective-publish}

Pour publier des ressources lors du chargement dans un dossier avec le [!UICONTROL mode de publication Dynamic Media] défini sur **[!UICONTROL Publication sélective]** :

1. Cliquez sur **[!UICONTROL Ajouter Assets]** > **[!UICONTROL Parcourir]** > **[!UICONTROL Parcourir les fichiers]** pour accéder au dossier approprié pour charger des ressources. La section **[!UICONTROL Options de publication]** affiche le **[!UICONTROL mode de publication DM]** en tant que **[!UICONTROL publication sélective]**.

![mode de publication sélective des images de chargement](/help/assets/assets/upload-selective.svg)

1. Sélectionnez **[!UICONTROL Publier vers AEM]**, **[!UICONTROL Publier vers Dynamic Media]**, ou les deux selon vos besoins, puis cliquez sur **Télécharger**.

   Les ressources sont publiées dans [!DNL AEM and Dynamic Media] en fonction de votre sélection.

   Pour afficher le statut de publication mis à jour de ces ressources, voir [Vérification du statut de publication](#check-publish-status).

## Publication de ressources à l’aide de la page de navigation des ressources {#publish-assets-using-asset-browse-page}

Pour publier des ressources à l’aide de la page de navigation des ressources :

1. Cliquez sur **[!UICONTROL Assets]** dans la section **[!UICONTROL Gestion d’Assets]** disponible dans le volet de gauche.
1. Sélectionnez une ou plusieurs ressources ou un ou plusieurs dossiers à publier, puis cliquez sur **[!UICONTROL Publier]**.
1. Sélectionnez **[!UICONTROL AEM]** puis cliquez sur **[!UICONTROL Publier]** pour publier des ressources dans [!DNL AEM and Dynamic Media].

   ![navigation des ressources](/help/assets/assets/browse-uactivation-immediate.svg)

   Vous ne pouvez pas publier un dossier dont le mode de publication [!DNL Dynamic Media] est défini sur **[!UICONTROL Publication sélective]**. Tous les autres dossiers ou ressources sélectionnés sont publiés sur [!DNL AEM and Dynamic Media] après avoir sélectionné [!DNL AEM].

   ![navigation des ressources](/help/assets/assets/browse-selective123.svg)

## Publication de ressources à l’aide de la page des résultats de recherche {#publish-assets-using-search-results-page}

Pour publier des ressources à l’aide de la page des résultats de recherche de ressources :

1. Spécifiez les critères dans la barre de recherche et cliquez sur l’icône de recherche pour afficher les résultats.
1. Sélectionnez les ressources à publier, puis cliquez sur **[!UICONTROL Publier].**
1. Sélectionnez [!DNL AEM, Dynamic Media] ou les deux selon vos besoins et cliquez sur **[!UICONTROL Publier]**.

   ![rechercher une image](/help/assets/assets/search-mode.svg)

   L’option de publication sur [!DNL Dynamic Media] dans la page des résultats de la recherche dépend du Mode de publication [!DNL Dynamic Media] défini sur le dossier dans lequel la ressource est disponible dans le référentiel.

   >[!NOTE]
   >
   >Si vous sélectionnez un dossier et cliquez sur **[!UICONTROL Publier]** dans la page des résultats de recherche, [!DNL Experience Manager Assets] affiche une option permettant de publier des ressources dans [!DNL AEM] et non [!DNL Dynamic Media], quels que soient les paramètres du mode de publication [!DNL Dynamic Media] pour le dossier.

## Vérification du statut de publication {#check-publish-status}

Pour vérifier l’état de publication d’une ressource ou d’un dossier :

1. Cliquez sur **[!UICONTROL Assets]** dans la section **[!UICONTROL Gestion d’Assets]** disponible dans le volet de gauche.
1. Basculez vers la vue Liste à l’aide du sélecteur de vues. Vous pouvez afficher les propriétés de la ressource, telles que [!UICONTROL Publication AEM], [!UICONTROL Publication Dynamic Media], [!UICONTROL titre], [!UICONTROL taille], [!UICONTROL dimensions], etc.

   Si une ressource ou un dossier n’est pas publié, le statut des colonnes **[!UICONTROL Publication AEM]** et **[!UICONTROL Publication Dynamic Media]** s’affiche sous la forme **[!UICONTROL N/A]**.

   ![check publish status1](/help/assets/assets/check-publish-status1.png)

   Si vous ne pouvez pas afficher les colonnes Publication [!DNL AEM] et Publication [!DNL Dynamic Media] dans la vue Liste :

   1. Cliquez sur ![paramètres](/help/assets/assets/settings-icon.svg) et sélectionnez **[!UICONTROL Publication AEM]** et **[!UICONTROL Publication Dynamic Media]** colonnes dans la boîte de dialogue **[!UICONTROL Colonnes configurables]**.
   1. Cliquez sur **[!UICONTROL Confirmer]**. [!DNL Experience Manager Assets] ajoute les colonnes sélectionnées à la vue Liste.

      ![vérifiez le statut de publication2](/help/assets/assets/check-publish-status2.png)

Vous pouvez également vérifier le statut de publication d’une ressource en la sélectionnant et en cliquant sur **[!UICONTROL Détails]**. Les détails sont disponibles dans la section **[!UICONTROL Publier]** disponible dans le volet de droite. La section **[!UICONTROL Publication]** indique la date à laquelle les ressources sont publiées sur [!DNL Dynamic Media] et [!DNL AEM]. Si vous devez afficher l’heure de publication des ressources, vous pouvez accéder à la vue Liste et consulter ces détails.

![vérifiez l’état de publication 3](/help/assets/assets/check-publish-status3.png)

## Limites {#limitations}

Les fonctionnalités suivantes ne sont pas prises en compte pour l’instant lors de la publication de ressources dans [!DNL AEM and Dynamic Media] :

* Publiez des ressources dans [!DNL AEM and Dynamic Media] à partir du [!DNL Asset details page].
* Visualisez les points d’entrée où les ressources sont publiées à l’aide de l’assistant Publication rapide.
* Ajouter ou supprimer d’autres ressources dans l’assistant de publication rapide.
* Une page pour afficher les ressources publiées.
* Possibilité de copier ou coller [!DNL Dynamic Media] URL au niveau d’une ressource (si les ressources sont publiées sur [!DNL Dynamic Media]).
* Possibilité de publier des références (ressources, balises, etc.) lors de la publication sur [!DNL AEM].
* Possibilité de remplacer [!DNL Dynamic Media] statut de synchronisation au niveau du dossier.
* Possibilité de remplacer [!DNL Dynamic Media] mode de publication au niveau du dossier
* Gérer la publication n’est pas encore pris en charge.
