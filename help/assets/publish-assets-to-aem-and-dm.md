---
title: Publication rapide sur AEM et Dynamic Media
description: La publication rapide est une fonctionnalité de la nouvelle interface utilisateur ou de la nouvelle vue de ressources. Cette fonctionnalité offre aux utilisateurs la possibilité de publier rapidement sur AEM et Dynamic Media simultanément ou individuellement . Cela signifie qu’après avoir sélectionné les ressources et les dossiers, les utilisateurs peuvent choisir de publier sur Dynamic Media ou Publier sur AEM. La fonction de publication rapide permet à la nouvelle interface utilisateur de publier des ressources et des dossiers dans Dynamic Media et AEM.
source-git-commit: f3b600fc3d9c519158b6b90bd9a9f881724934de
workflow-type: tm+mt
source-wordcount: '1216'
ht-degree: 0%

---


# Publication de ressources sur AEM et Dynamic Media{#Publish-Assets-to-AEM-and-Dynamic-Media}

Experience Manager Assets vous permet de publier rapidement des ressources dans Experience Manager et Dynamic Media à l’aide de la vue Assets. Cela vous permet de gérer vos ressources, puis de les publier à l’aide de [Mode Ressources sans passer à la vue Admin](/help/assets/overview.md##persona-based-experiences).

La vue Experience Manager Assets offre la possibilité de publier des ressources sur AEM ou Dynamic Media, ou les deux en même temps. Vous pouvez publier des ressources lors du chargement, de la navigation et de la recherche de ressources. Toutes ces options de publication de ressources sont expliquées en détail dans cet article.

## Avant de commencer {#before-you-begin}

Configurez ces paramètres pour afficher les options de publication pour AEM et Dynamic Media :

* Pour afficher les options de publication pour Dynamic Media, configurez les paramètres suivants à l’aide de la vue d’administration :

   * [Création d’une configuration cloud Dynamic Media](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services).
   * Définissez le mode de publication Dynamic Media au niveau du dossier. Vous pouvez configurer ces paramètres lors de la création de la configuration cloud Dynamic Media. Pour remplacer ces paramètres au niveau du dossier, voir [Configuration de la publication sélective au niveau du dossier dans Dynamic Media](/help/assets/dynamic-media/selective-publishing.md).

* Pour afficher les options de publication pour AEM, vous devez configurer le point de terminaison de publication AEM pour votre environnement.

## Publier les ressources pendant le chargement {#piblish-assets-during-upload}

Vous pouvez publier des ressources dans AEM et Dynamic Media lors du chargement de ressources dans un dossier. Les options de publication qui s’affichent dépendent du mode de publication de Dynamic Media défini sur le dossier dans lequel les ressources sont chargées. Le mode de publication Dynamic Media peut être défini sur :

* **Lors de l’activation :** Lorsque des ressources sont chargées dans ce dossier, vous devez d’abord publier explicitement la ressource avant qu’un lien URL/code intégré ne soit fourni.

* **Immédiat :** Lorsque des ressources sont chargées dans ce dossier, le système les ingère dans Experience Manager et fournit instantanément l’URL/le code intégré.
* **Publication sélective :** Les ressources sont publiées, au choix, dans le Experience Manager ou dans Dynamic Media, pour diffusion dans le domaine public.

### Mode de publication Dynamic Media défini sur Lors de l’activation {#dynamic-media-publish-mode-set-to-upon-activation}

Pour publier des ressources lors du chargement dans un dossier avec le mode de publication Dynamic Media défini sur **Lors de l’activation**:

1. Cliquez sur **Ajouter des ressources** > **Parcourir** > **Parcourir les fichiers** pour accéder au dossier approprié afin de charger des ressources. La variable **Options de publication** affiche la section **Mode de publication DM** as **Lors de l’activation**.
   ![Télécharger l’image lors de l’activation](/help/assets/assets/upload-upon-activation.png)
2. Sélectionner **Publication sur AEM et Dynamic Media** et cliquez sur **Télécharger**. Les ressources sont publiées simultanément sur AEM et Dynamic Media. Pour afficher l’état de publication mis à jour pour ces ressources, voir [Vérification de l’état de publication](#check-publish-status).

### Mode de publication Dynamic Media défini sur Immédiat {#dynamic-media-publish-mode-set-to-immediate}

Pour publier des ressources lors du chargement dans un dossier avec le mode de publication Dynamic Media défini sur **Immédiat**:

1. Cliquez sur **Ajouter des ressources** > **Parcourir** > **Parcourir les fichiers** pour accéder au dossier approprié afin de charger des ressources. La section Options de publication affiche le **Mode de publication DM** as **Immédiat**.
   ![image de téléchargement de fichier - mode immédiat](/help/assets/assets/upload-immediate-mode.png)
Comme le mode de publication Dynamic Media est **Immédiat**, les ressources chargées sont automatiquement publiées dans Dynamic Media lorsque vous cliquez sur **Télécharger**.

2. Sélectionnez Publier sur **AEM de publication** Accédez aux ressources chargées dans AEM et cliquez sur Télécharger.

   Si vous sélectionnez **Publier sur AEM**, les ressources sont publiées sur AEM et Dynamic Media, sinon elles le sont sur Dynamic Media.

   Pour afficher l’état de publication mis à jour pour ces ressources, voir [Vérification de l’état de publication](#check-publish-status).

### Mode de publication Dynamic Media défini sur Publication sélective {#dynamic-media-publish-mode-set-to-selective-publish}

Pour publier des ressources lors du chargement dans un dossier avec le mode de publication Dynamic Media défini sur **Publication sélective**:

1. Cliquez sur **Ajouter des ressources** > **Parcourir** > **Parcourir les fichiers** pour accéder au dossier approprié afin de charger des ressources. La section Options de publication affiche le **Mode de publication DM** as **Publication sélective**.
   ![télécharger le mode de publication sélectif des images](/help/assets/assets/upload-image-selective-publish-mode.png)

2. Sélectionner **Publier sur AEM**, **Publication sur Dynamic Media**, ou les deux selon vos besoins, puis cliquez sur **Télécharger**.

   Les ressources sont publiées sur AEM et Dynamic Media en fonction de votre sélection.

   Pour afficher l’état de publication mis à jour pour ces ressources, voir [Vérification de l’état de publication](#check-publish-status).

## Publication de ressources à l’aide de la page de navigation des ressources {#publish-assets-using-asset-browse-page}

Pour publier des ressources à l’aide de la page de navigation des ressources :

1. Cliquez sur **Ressources** dans le **Gestion des ressources** dans le volet de gauche.
2. Sélectionnez la ou les ressources ou le ou les dossiers à publier, puis cliquez sur **Publier**.
3. Sélectionner **AEM** et cliquez sur **Publier** pour publier des ressources dans AEM et Dynamic Media.
   ![navigation dans les ressources](/help/assets/assets/assets-browse-1.png)
Vous ne pouvez pas publier un dossier dont le mode de publication Dynamic Media est défini sur **Publication sélective.** Tous les autres dossiers ou ressources sélectionnés sont publiés sur AEM et Dynamic Media après avoir sélectionné AEM.
   ![navigation dans les ressources](/help/assets/assets/assets-browse-2.png)

## Publication de ressources à l’aide de la page des résultats de recherche {#publish-assets-using-search-results-page}

Pour publier des ressources à l’aide de la page de résultats de recherche de ressources :

1. Spécifiez les critères dans la barre de recherche et cliquez sur l’icône Rechercher pour afficher les résultats.
2. Sélectionnez les ressources à publier, puis cliquez sur **Publiez.**
3. Sélectionnez AEM, Dynamic Media ou les deux selon vos besoins, puis cliquez sur **Publiez.**
   ![image de recherche](/help/assets/assets/search-image1.png)
L’option de publication sur Dynamic Media sur la page des résultats de recherche dépend du mode de publication de Dynamic Media défini sur le dossier où la ressource est disponible dans le référentiel.

   >[!NOTE]
   >
   >Si vous sélectionnez un dossier et cliquez sur **Publier** sur la page des résultats de recherche, Experience Manager Assets affiche une option pour publier des ressources sur AEM et non sur Dynamic Media, quels que soient les paramètres du mode de publication Dynamic Media du dossier.

## Vérification de l’état de publication {#check-publish-status}

Pour vérifier l’état de publication d’une ressource ou d’un dossier :

1. Cliquez sur **[!UICONTROL Ressources]** dans le **[!UICONTROL Gestion des ressources]** dans le volet de gauche.
2. Passez en mode Liste à l’aide du sélecteur de mode. Vous pouvez afficher les propriétés des ressources, telles que Publier AEM, Publier Dynamic Media, Titre, Taille, Dimensions, etc.\
   Si une ressource ou un dossier n’est pas publié, l’état de la variable **AEM Publication** et **Publication Dynamic Media** s’affiche sous la forme **S.O.**
   ![vérification de la publication status1](/help/assets/assets/check-publish-status1.png)
Si vous ne pouvez pas afficher les colonnes Publication AEM et Publication Dynamic Media en mode Liste :
   1. Cliquez sur ![paramètres](/help/assets/assets/settings-icon.svg) et sélectionnez **AEM Publication** et **Publication Dynamic Media** des colonnes **Colonnes configurables** boîte de dialogue.
   2. Cliquez sur **Confirmez.** Experience Manager Assets ajoute les colonnes sélectionnées en mode Liste.

      ![vérification de l’état de publication 2](/help/assets/assets/check-publish-status2.png)

Vous pouvez également vérifier l’état de publication d’une ressource en la sélectionnant et en cliquant sur **Détails.** Les détails sont disponibles dans la section **Publier** dans le volet de droite. La variable **Publier** Cette section répertorie la date à laquelle les ressources sont publiées dans Dynamic Media et AEM. Si vous devez afficher l’heure de publication des ressources, vous pouvez accéder au mode Liste et afficher ces détails.

![vérification de l’état de publication 3](/help/assets/assets/check-publish-status3.png)

## Limites {#limitations}

Les fonctionnalités suivantes ne sont pas prises en charge pour l’instant lors de la publication de ressources dans AEM et Dynamic Media :

* Publiez des ressources dans AEM et Dynamic Media à partir de la page Détails de la ressource.
* Visualisez les points de terminaison où les ressources sont publiées à l’aide de l’assistant Publication rapide .
* Ajoutez ou supprimez d’autres ressources dans l’assistant Publication rapide.
* Page pour afficher les ressources publiées.
* Permet de copier ou coller l’URL Dynamic Media au niveau de la ressource (si les ressources sont publiées dans Dynamic Media).
* Possibilité de publier des références (ressources, balises, etc.) lors de la publication sur AEM.
* Possibilité de remplacer l’état de synchronisation Dynamic Media au niveau du dossier.
* Possibilité de remplacer le mode de publication Dynamic Media au niveau du dossier.