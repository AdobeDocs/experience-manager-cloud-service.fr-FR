---
title: Publication rapide sur AEM et Dynamic Media
description: La publication rapide en mode Assets vous permet de publier des ressources dans AEM et Dynamic Media simultanément ou séparément. Vous pouvez sélectionner des ressources et des dossiers et choisir de les publier dans Dynamic Media ou AEM.
exl-id: 147c1c35-0d81-4458-b4ed-7541d2b0dd54
feature: Publishing, Dynamic Media
role: User
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '1240'
ht-degree: 2%

---

# Publier des ressources sur AEM et Dynamic Media{#Publish-Assets-to-AEM-and-Dynamic-Media}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime et Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouvelle</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>Intégration d’AEM Assets à Edge Delivery Services</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>Extensibilité de l’interface utilisateur</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Activation de Dynamic Media Prime et Ultimate</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>Bonnes pratiques de recherche</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>Bonnes pratiques relatives aux métadonnées</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Hub de contenus</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>Fonctionnalités Dynamic Media avec OpenAPI</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>Documentation de développement pour AEM Assets</b></a>
        </td>
    </tr>
</table>

Experience Manager Assets vous permet de publier rapidement des ressources dans Experience Manager et Dynamic Media à l’aide de la vue Assets. Vous pouvez ainsi gérer vos ressources, puis les publier à l’aide de la vue Assets [sans passer à la vue Administration](/help/assets/overview.md##persona-based-experiences).

La vue Experience Manager Assets offre la possibilité de publier des ressources dans AEM ou Dynamic Media, ou les deux en même temps. Vous pouvez publier des ressources lors du chargement, de la navigation et de la recherche de ressources. Toutes ces options de publication de ressources sont expliquées en détail dans cet article.

## Avant de commencer {#before-you-begin}

Configurez ces paramètres pour afficher les options de publication pour AEM et Dynamic Media :

* Pour afficher les options de publication de Dynamic Media, configurez les paramètres suivants à l’aide de la vue Administration :

   * [Créez une configuration de cloud Dynamic Media](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services).
   * Définissez le mode de publication Dynamic Media au niveau du dossier. Vous pouvez également configurer ces paramètres lors de la création de la configuration du cloud Dynamic Media. Pour remplacer ces paramètres au niveau du dossier, voir [Configuration de la publication sélective au niveau du dossier dans Dynamic Media](/help/assets/dynamic-media/selective-publishing.md).

* Pour afficher les options de publication d’AEM, vous devez configurer le point d’entrée de publication AEM pour votre environnement.

## Publication d’Assets lors du chargement {#piblish-assets-during-upload}

Vous pouvez publier des ressources dans AEM et Dynamic Media lors du chargement de ressources vers un dossier. Les options de publication qui s’affichent dépendent des paramètres du mode de publication Dynamic Media du dossier dans lequel les ressources sont chargées. Le mode de publication Dynamic Media peut être défini sur :

* **Lors de l’activation :** lorsque des ressources sont chargées dans ce dossier, vous devez d’abord les publier explicitement avant de fournir un lien d’URL/d’incorporation.

* **Immédiat :** lorsque des ressources sont chargées dans ce dossier, le système les ingère dans Experience Manager et fournit instantanément l’URL/le code intégré.
* **Publication sélective :** les Assets sont publiées, au choix, dans Experience Manager ou Dynamic Media, pour diffusion dans le domaine public.

### Mode de publication Dynamic Media défini sur Lors de l’activation {#dynamic-media-publish-mode-set-to-upon-activation}

Pour publier des ressources lors de leur chargement dans un dossier dont le mode de publication Dynamic Media est défini sur **Lors de l’activation** :

1. Cliquez sur **Ajouter Assets** > **Parcourir** > **Parcourir les fichiers** pour accéder au dossier approprié pour charger des ressources. La section **Options de publication** affiche le **mode de publication DM** sous la forme **Lors de l’activation**.
   ![Charger l’image lors de l’activation](/help/assets/assets/upload-uactivation.svg)
2. Sélectionnez **Publier vers AEM et Dynamic Media**, puis cliquez sur **Télécharger**. Les ressources sont publiées simultanément sur AEM et Dynamic Media. Pour afficher le statut de publication mis à jour de ces ressources, voir [Vérification du statut de publication](#check-publish-status).

### Mode de publication Dynamic Media défini sur Immédiat {#dynamic-media-publish-mode-set-to-immediate}

Pour publier des ressources lors de leur chargement dans un dossier dont le mode de publication Dynamic Media est défini sur **Immédiat** :

1. Cliquez sur **Ajouter Assets** > **Parcourir** > **Parcourir les fichiers** pour accéder au dossier approprié pour charger des ressources. La section **Options de publication** affiche le **mode de publication DM** en tant que **Immédiat**.
   ![image de chargement de fichier - mode immédiat](/help/assets/assets/resized-image-pdf-svg-new.svg)


   Comme le mode de publication Dynamic Media est **Immédiat**, les ressources chargées sont automatiquement publiées sur Dynamic Media lorsque vous cliquez sur **Charger**.

2. Sélectionnez **Publier vers AEM** pour publier les ressources chargées dans AEM, puis cliquez sur Télécharger.

   Si vous sélectionnez **Publier vers AEM**, les ressources sont publiées dans AEM et Dynamic Media, sinon elles sont publiées dans Dynamic Media.

   Pour afficher le statut de publication mis à jour de ces ressources, voir [Vérification du statut de publication](#check-publish-status).

### Mode de publication Dynamic Media défini sur Publication sélective {#dynamic-media-publish-mode-set-to-selective-publish}

Pour publier des ressources lors du chargement dans un dossier avec le mode de publication Dynamic Media défini sur **Publication sélective** :

1. Cliquez sur **Ajouter Assets** > **Parcourir** > **Parcourir les fichiers** pour accéder au dossier approprié pour charger des ressources. La section **Options de publication** affiche le **mode de publication DM** en tant que **publication sélective**.
   ![mode de publication sélective des images de chargement](/help/assets/assets/upload-selective.svg)

2. Sélectionnez **Publier vers AEM**, **Publier vers Dynamic Media**, ou les deux selon vos besoins, puis cliquez sur **Télécharger**.

   Les ressources sont publiées dans AEM et Dynamic Media en fonction de votre sélection.

   Pour afficher le statut de publication mis à jour de ces ressources, voir [Vérification du statut de publication](#check-publish-status).

## Publication de ressources à l’aide de la page de navigation des ressources {#publish-assets-using-asset-browse-page}

Pour publier des ressources à l’aide de la page de navigation des ressources :

1. Cliquez sur **Assets** dans la section **Gestion d’Assets** disponible dans le volet de gauche.
2. Sélectionnez une ou plusieurs ressources ou un ou plusieurs dossiers à publier, puis cliquez sur **Publier**.
3. Sélectionnez **AEM** puis cliquez sur **Publier** pour publier des ressources dans AEM et Dynamic Media.
   ![navigation des ressources](/help/assets/assets/browse-uactivation-immediate.svg)
Vous ne pouvez pas publier un dossier dont le mode de publication Dynamic Media est défini sur Publication sélective **.** Tous les autres dossiers ou ressources sélectionnés sont publiés sur AEM et Dynamic Media après avoir sélectionné AEM.
   ![navigation des ressources](/help/assets/assets/browse-selective123.svg)

## Publication de ressources à l’aide de la page des résultats de recherche {#publish-assets-using-search-results-page}

Pour publier des ressources à l’aide de la page des résultats de recherche de ressources :

1. Spécifiez les critères dans la barre de recherche et cliquez sur l’icône de recherche pour afficher les résultats.
2. Sélectionnez les ressources à publier, puis cliquez sur **Publier.**
3. Sélectionnez AEM, Dynamic Media ou les deux selon vos besoins, puis cliquez sur **Publier.**
   ![rechercher une image](/help/assets/assets/search-mode.svg)
L’option de publication sur Dynamic Media dans la page des résultats de recherche dépend du Mode de publication Dynamic Media défini sur le dossier dans lequel la ressource est disponible dans le référentiel.

   >[!NOTE]
   >
   >Si vous sélectionnez un dossier et cliquez sur **Publier** dans la page des résultats de recherche, Experience Manager Assets affiche une option permettant de publier des ressources dans AEM et non dans Dynamic Media, quels que soient les paramètres du mode de publication Dynamic Media pour le dossier.

## Vérification du statut de publication {#check-publish-status}

Pour vérifier l’état de publication d’une ressource ou d’un dossier :

1. Cliquez sur **[!UICONTROL Assets]** dans la section **[!UICONTROL Gestion d’Assets]** disponible dans le volet de gauche.
2. Basculez vers la vue Liste à l’aide du sélecteur de vues. Vous pouvez afficher les propriétés de la ressource, telles que la publication AEM, la publication Dynamic Media, le titre, la taille, les dimensions, etc.\
   Si une ressource ou un dossier n’est pas publié, le statut des colonnes **Publication AEM** et **Publication Dynamic Media** s’affiche sous la forme **S.O.**
   ![vérifier le statut de publication1](/help/assets/assets/check-publish-status1.png)
Si vous ne pouvez pas afficher les colonnes Publication AEM et Publication Dynamic Media dans la vue Liste :
   1. Cliquez sur ![paramètres](/help/assets/assets/settings-icon.svg) et sélectionnez **Publication AEM** et **Publication Dynamic Media** colonnes dans la boîte de dialogue **Colonnes configurables**.
   2. Cliquez sur **Confirmer.** Experience Manager Assets ajoute les colonnes sélectionnées à la vue Liste .

      ![vérifiez le statut de publication2](/help/assets/assets/check-publish-status2.png)

Vous pouvez également vérifier le statut de publication d’une ressource en la sélectionnant et en cliquant sur **Détails.** Les détails sont disponibles dans la section **Publier** disponible dans le volet de droite. La section **Publication** indique la date de publication des ressources dans Dynamic Media et AEM. Si vous devez afficher l’heure de publication des ressources, vous pouvez accéder à la vue Liste et consulter ces détails.

![vérifiez l’état de publication 3](/help/assets/assets/check-publish-status3.png)

## Limites {#limitations}

Les fonctionnalités suivantes ne sont pas prises en compte pour l’instant lors de la publication de ressources dans AEM et Dynamic Media :

* Publiez des ressources dans AEM et Dynamic Media à partir de la page des détails de la ressource.
* Visualisez les points d’entrée où les ressources sont publiées à l’aide de l’assistant Publication rapide.
* Ajouter ou supprimer d’autres ressources dans l’assistant de publication rapide.
* Une page pour afficher les ressources publiées.
* Possibilité de copier ou coller l’URL Dynamic Media au niveau d’une ressource (si les ressources sont publiées sur Dynamic Media).
* Possibilité de publier des références (ressources, balises, etc.) lors de la publication sur AEM.
* Possibilité de remplacer le statut de synchronisation de Dynamic Media au niveau du dossier.
* Possibilité de remplacer le mode de publication Dynamic Media au niveau du dossier
* Gérer la publication n’est pas encore pris en charge.
