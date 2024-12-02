---
title: Publish rapide pour AEM et Dynamic Media
description: Quick Publish dans la vue Assets vous permet de publier des ressources dans AEM et Dynamic Media simultanément ou séparément. Vous pouvez sélectionner des ressources et des dossiers et choisir de publier sur Dynamic Media ou AEM.
exl-id: 147c1c35-0d81-4458-b4ed-7541d2b0dd54
feature: Publishing, Dynamic Media
role: User
source-git-commit: 8ab19fe82fc390d28d33b17222177fd8486c8fc7
workflow-type: tm+mt
source-wordcount: '1209'
ht-degree: 2%

---

# Publier des ressources sur AEM et Dynamic Media{#Publish-Assets-to-AEM-and-Dynamic-Media}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [Bonnes pratiques relatives aux métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Fonctionnalités Dynamic Media avec OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation de développement pour AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Experience Manager Assets vous permet de publier rapidement des ressources dans Experience Manager et Dynamic Media à l’aide de la vue Assets. Cela vous permet de gérer vos ressources, puis de les publier à l’aide de la vue [Assets sans passer à la vue Admin](/help/assets/overview.md##persona-based-experiences).

La vue Experience Manager Assets offre la possibilité de publier des ressources sur AEM ou Dynamic Media, ou les deux en même temps. Vous pouvez publier des ressources lors du chargement, de la navigation et de la recherche de ressources. Toutes ces options de publication de ressources sont expliquées en détail dans cet article.

## Avant de commencer {#before-you-begin}

Configurez ces paramètres pour afficher les options de publication pour AEM et Dynamic Media :

* Pour afficher les options de publication pour Dynamic Media, configurez les paramètres suivants à l’aide de la vue Admin :

   * [ Créez une configuration de cloud Dynamic Media ](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services).
   * Définissez le mode Publish Dynamic Media au niveau du dossier. Vous pouvez configurer ces paramètres lors de la création de la configuration du cloud Dynamic Media. Pour remplacer ces paramètres au niveau du dossier, voir [Configuration d’une Publish sélective au niveau du dossier dans Dynamic Media](/help/assets/dynamic-media/selective-publishing.md).

* Pour afficher les options de publication pour AEM, vous devez configurer le point de terminaison de publication AEM pour votre environnement.

## Publish Assets pendant le chargement {#piblish-assets-during-upload}

Vous pouvez publier des ressources dans AEM et Dynamic Media lors du chargement de ressources dans un dossier. Les options de publication qui s’affichent dépendent du mode de publication de Dynamic Media défini sur le dossier dans lequel les ressources sont chargées. Le mode de publication Dynamic Media peut être défini sur :

* **Lors de l’activation :** Lorsque des ressources sont chargées dans ce dossier, vous devez publier explicitement la ressource avant qu’un lien URL/code intégré ne soit fourni.

* **Immédiat :** Lorsque des ressources sont chargées dans ce dossier, le système les ingère dans Experience Manager et fournit instantanément l’URL/le code intégré.
* **Publish sélective :** Les Assets sont publiées selon votre choix dans votre Experience Manager ou dans Dynamic Media pour une diffusion dans le domaine public.

### Mode Publish Dynamic Media défini sur Lors de l’activation {#dynamic-media-publish-mode-set-to-upon-activation}

Pour publier des ressources lors du chargement dans un dossier avec le mode Publish Dynamic Media défini sur **Lors de l’activation** :

1. Cliquez sur **Ajouter Assets** > **Parcourir** > **Parcourir les fichiers** pour accéder au dossier approprié pour charger des ressources. La section **Options Publish** affiche le **mode Publish DM** en tant que **Lors de l’activation**.
   ![Télécharger l’image lors de l’activation](/help/assets/assets/upload-uactivation.svg)
2. Sélectionnez **Publish to AEM and Dynamic Media** et cliquez sur **Télécharger**. Les ressources sont publiées simultanément sur AEM et Dynamic Media. Pour afficher l’état de publication mis à jour pour ces ressources, voir [Vérification de l’état de Publish](#check-publish-status).

### Mode Publish Dynamic Media défini sur Immédiat {#dynamic-media-publish-mode-set-to-immediate}

Pour publier des ressources lors du chargement vers un dossier dont le mode Publish de Dynamic Media est défini sur **Immédiat** :

1. Cliquez sur **Ajouter Assets** > **Parcourir** > **Parcourir les fichiers** pour accéder au dossier approprié pour charger des ressources. La section Options Publish affiche le **mode Publish DM** comme **Immédiat**.
   ![image de téléchargement de fichier - mode immédiat](/help/assets/assets/resized-image-pdf-svg-new.svg)


   Comme le mode Publish de Dynamic Media est **Immédiat**, les ressources chargées sont automatiquement publiées dans Dynamic Media lorsque vous cliquez sur **Télécharger**.

2. Sélectionnez Publish pour **AEM pour publier** les ressources chargées dans AEM et cliquez sur Télécharger.

   Si vous sélectionnez **Publish à AEM**, les ressources sont publiées sur AEM et Dynamic Media, sinon les ressources sont publiées sur Dynamic Media.

   Pour afficher l’état de publication mis à jour pour ces ressources, voir [Vérification de l’état de Publish](#check-publish-status).

### Mode Publish Dynamic Media défini sur Publish sélective {#dynamic-media-publish-mode-set-to-selective-publish}

Pour publier des ressources lors du chargement vers un dossier dont le mode Publish Dynamic Media est défini sur **Publish sélective** :

1. Cliquez sur **Ajouter Assets** > **Parcourir** > **Parcourir les fichiers** pour accéder au dossier approprié pour charger des ressources. La section Options Publish affiche le **mode Publish DM** en tant que **Publish sélective**.
   ![ Télécharger le mode de publication sélectif des images](/help/assets/assets/upload-selective.svg)

2. Sélectionnez **Publish to AEM**, **Publish to Dynamic Media** ou les deux selon vos besoins, puis cliquez sur **Télécharger**.

   Les ressources sont publiées sur AEM et Dynamic Media en fonction de votre sélection.

   Pour afficher l’état de publication mis à jour pour ces ressources, voir [Vérification de l’état de Publish](#check-publish-status).

## Ressources Publish à l’aide de la page de navigation des ressources {#publish-assets-using-asset-browse-page}

Pour publier des ressources à l’aide de la page de navigation des ressources :

1. Cliquez sur **Assets** dans la section **Assets Management** disponible dans le volet de gauche.
2. Sélectionnez une ou plusieurs ressources ou dossiers à publier, puis cliquez sur **Publish**.
3. Sélectionnez **AEM** et cliquez sur **Publish** pour publier des ressources sur AEM et Dynamic Media.
   ![ressources browse](/help/assets/assets/browse-uactivation-immediate.svg)
Vous ne pouvez pas publier un dossier dont le mode Publish de Dynamic Media est défini sur **Publication sélective.** Tous les autres dossiers ou ressources sélectionnés sont publiés sur AEM et Dynamic Media après avoir sélectionné AEM.
   ![ressources browse](/help/assets/assets/browse-selective123.svg)

## Ressources Publish à l’aide de la page des résultats de recherche {#publish-assets-using-search-results-page}

Pour publier des ressources à l’aide de la page de résultats de recherche de ressources :

1. Spécifiez les critères dans la barre de recherche et cliquez sur l’icône Rechercher pour afficher les résultats.
2. Sélectionnez les ressources à publier et cliquez sur **Publish.**
3. Sélectionnez AEM, Dynamic Media ou les deux selon vos besoins et cliquez sur **Publish.**
   ![Image de recherche](/help/assets/assets/search-mode.svg)
L’option de publication sur Dynamic Media sur la page des résultats de recherche dépend du mode Publish de Dynamic Media défini sur le dossier où la ressource est disponible dans le référentiel.

   >[!NOTE]
   >
   >Si vous sélectionnez un dossier et cliquez sur **Publish** dans la page des résultats de recherche, Experience Manager Assets affiche alors une option pour publier des ressources sur AEM et non sur Dynamic Media, quels que soient les paramètres du mode Dynamic Media Publish du dossier.

## Vérification de l’état Publish {#check-publish-status}

Pour vérifier l’état de publication d’une ressource ou d’un dossier :

1. Cliquez sur **[!UICONTROL Assets]** dans la section **[!UICONTROL Assets Management]** disponible dans le volet de gauche.
2. Passez en mode Liste à l’aide du sélecteur d’affichage. Vous pouvez afficher les propriétés des ressources, telles que la publication d’AEM, Dynamic Media Publish, le titre, la taille, les dimensions, etc.\
   Si une ressource ou un dossier n’est pas publié, l’état des colonnes **AEM Publish** et **Dynamic Media Publish** s’affiche sous la forme **S/O.**
   ![vérifier l’état de publication1](/help/assets/assets/check-publish-status1.png)
Si vous ne pouvez pas afficher les colonnes Publish et Dynamic Media Publish AEM en mode Liste :
   1. Cliquez sur ![settings](/help/assets/assets/settings-icon.svg) et sélectionnez les colonnes **Publish AEM** et **Dynamic Media Publish** dans la boîte de dialogue **Colonnes configurables**.
   2. Cliquez sur **Confirmer.** Experience Manager Assets ajoute les colonnes sélectionnées en mode Liste.

      ![Vérification de l’état de publication2](/help/assets/assets/check-publish-status2.png)

Vous pouvez également vérifier l’état de publication d’une ressource en la sélectionnant et en cliquant sur **Détails.** Les détails sont disponibles dans la section **Publish** disponible dans le volet de droite. La section **Publish** répertorie la date de publication des ressources dans Dynamic Media et AEM. Si vous devez afficher l’heure de publication des ressources, vous pouvez accéder au mode Liste et afficher ces détails.

![ Vérifiez l’état de publication 3](/help/assets/assets/check-publish-status3.png)

## Limites {#limitations}

Les fonctionnalités suivantes ne sont pas prises en charge pour l’instant lors de la publication de ressources dans AEM et Dynamic Media :

* Publish des ressources vers AEM et Dynamic Media à partir de la page Détails de la ressource.
* Visualisez les points de fin où les ressources sont publiées à l’aide de l’assistant Quick Publish.
* Ajoutez ou supprimez d’autres ressources dans l’assistant Quick Publish.
* Page pour afficher les ressources publiées.
* Permet de copier ou coller l’URL Dynamic Media au niveau de la ressource (si les ressources sont publiées dans Dynamic Media).
* Possibilité de publier des références (ressources, balises, etc.) lors de la publication sur AEM.
* Possibilité de remplacer l’état de synchronisation Dynamic Media au niveau du dossier.
* Possibilité de remplacer le mode Publish Dynamic Media au niveau du dossier
* La fonction Gérer la publication n’est pas encore prise en charge.
