---
title: Comment gérer  [!DNL Dynamic Media]  modèles ?
description: Découvrez comment créer  [!DNL Dynamic Media]  modèles à l’aide d’un éditeur de modèles WYSIWYG et inclure plusieurs calques d’images et de texte pour créer rapidement des bannières et des prospectus et les utiliser dans des applications en aval.
hide: true
role: User
exl-id: 07de648e-4ae2-4524-8e05-3cf10bb6006d
source-git-commit: e1c571c4798152732d78b8a2c823d5da9664cb9e
workflow-type: tm+mt
source-wordcount: '3165'
ht-degree: 1%

---

# [!DNL Dynamic Media] modèles{#dynamic-media-templates}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime et Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>Intégration d’AEM Assets à Edge Delivery Services</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>Extensibilité de l’IU</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Activer Dynamic Media Prime et Ultimate</b></a>
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

Créez des modèles personnalisables en temps réel pour vos bannières et prospectus à l’aide de [!DNL Dynamic Media] templates, un éditeur de modèles WYSIWYG. Publiez votre modèle de [!DNL Dynamic Media] et utilisez-le dans les applications en aval. Un modèle de [!DNL Dynamic Media] comprend des calques d’image et de texte. Ajoutez des paramètres aux calques d’image et de texte du modèle et utilisez [[!DNL Dynamic Media] URL](https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/wysiwyg/storage/catalog-urls-dynamic-media) pour repositionner et redimensionner le calque et mettre à jour son contenu en temps réel.

Voici quelques-unes des principales fonctionnalités :

* **[!DNL Dynamic Media]WYSIWYG Template Editor** : créez des bannières personnalisables avec des calques d’image et de texte.
* **Paramétrage des couches :** permet de définir des paires clé-valeur dynamiques pour les couches afin d’activer les mises à jour en temps réel.
* Prise en charge des URL **[!DNL Dynamic Media]:** utilisez des URL [!DNL Dynamic Media] pour les modèles, en intégrant des valeurs personnalisées provenant d’applications propriétaires ou tierces.
* **Layer Visibility Control :** permet de masquer ou d’afficher les calques de manière dynamique selon les besoins.
* **Redimensionnement intelligent du texte :** permet d’ajuster automatiquement la taille du texte aux zones désignées.

Voici quelques-uns des principaux avantages des modèles de [!DNL Dynamic Media] :

* **Optimisez le Personalization 1:1:** Personnalisez le contenu en fonction des signaux client en temps réel.
* **Réduire les efforts manuels :** automatiser et accélérer la création et la gestion de contenu.
* **Assurer des expériences omnicanal cohérentes :** maintenir la cohérence de la marque sur l’ensemble des canaux.
* **Réutiliser efficacement le contenu :** évitez le contenu à usage unique et mettez à l’échelle avec des modèles dynamiques paramétrés.
* **Réduire les risques :** mettez à jour les prix, les remises et les liens en temps réel.
* **Améliorez l’engagement client :** générez des expériences interactives et pertinentes du point de vue contextuel.

>[!NOTE]
>
>Les clients et clientes disposant d’abonnements au SKU de sécurité renforcée ne peuvent utiliser aucune fonctionnalité [!DNL Dynamic Media], y compris les modèles de [!DNL Dynamic Media], sur ce programme de Cloud Services.

Découvrez comment créer un modèle de [!DNL Dynamic Media] étape par étape dans cette vidéo.
>[!VIDEO](https://video.tv.adobe.com/v/3443281)

## Avant de commencer{#prerequisites-for-dynamic-media-wysiwyg-template}

Remplissez les conditions suivantes pour créer un modèle de [!DNL Dynamic Media] et générer son URL de diffusion :

1. Accès à [!DNL Dynamic Media].
1. Sur la page d’accueil [!DNL Assets View], vous disposez d’un dossier dans **[!UICONTROL Dynamic Media Assets]** pour enregistrer votre modèle. [Créez un dossier](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/add-delete-assets-view) dans ![Assets](/help/assets/assets/Asset-icon.svg)**[!UICONTROL Assets ]**pour répliquer ce dossier dans**[!UICONTROL  Dynamic Media Assets ]**.
1. [Synchronisez les images disponibles dans votre [!DNL AEM Assets] instance avec  [!DNL Dynamic Media]  pour les utiliser afin de créer le modèle](/help/assets/dynamic-media/config-dm.md).
1. Publiez les images à utiliser lors de la création du modèle pour générer l’URL de diffusion du modèle après sa création. L’URL de diffusion peut être utilisée dans les applications en aval.
1. Pour utiliser une autre police que la police [!UICONTROL Adobe Sans F2] par défaut dans le calque de texte du modèle, [chargez et publiez le fichier de police simultanément dans AEM et Dynamic Media](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/publish-assets-to-aem-and-dm?lang=en#dynamic-media-publish-mode-set-to-upon-activation). [Les formats de fichiers de polices pris en charge sont AEM, OTF, PFB, PFM, PhotoFont, TTC, TTF](https://experienceleague.adobe.com/en/docs/dynamic-media-classic/using/upload-publish/uploading-files#supported-asset-file-formats). Veillez également à [retraiter](/help/assets/reprocessing-assets-view.md) les polices existantes pour les utiliser. Voir [Polices](https://experienceleague.adobe.com/en/docs/dynamic-media-classic/using/support-files/fonts) pour plus d’informations.<!--(On [!DNL Assets View] home page, click ![Assets](/help/assets/assets/Asset-icon.svg)**[!UICONTROL Assets]**, navigate to the font file location, select the font file one at a time and click ![Reprocess](/help/assets/assets/Refresh-docs.svg)**[!UICONTROL Reprocess]**)-->
1. vérifiez les points suivants dans l’interface utilisateur tactile :
   * Sur la page **[!UICONTROL Modifier [!DNL Dynamic Media] configuration]**, **[!UICONTROL [!DNL Dynamic Media]mode de synchronisation]** défini sur **[!UICONTROL Désactivé par défaut]** n’est pas appliqué à tous les dossiers AEM (**[!UICONTROL Synchroniser tout le contenu]** est décoché). Voir [Configuration de Dynamic Media Cloud Service](/help/assets/dynamic-media/config-dm.md) pour plus d’informations.
   * **[!UICONTROL [!DNL Dynamic Media]mode de synchronisation]** est défini sur **[!UICONTROL Activer pour les sous-dossiers]** pour le dossier ou sous-dossier de destination dans lequel vous enregistrerez le modèle après sa création. Voir [Configuration [!DNL Dynamic Media] Cloud Service](/help/assets/dynamic-media/config-dm.md) pour plus d&#39;informations.

## Créer [!DNL Dynamic Media] modèle{#how-to-create-dynamic-media-template}

Pour créer un modèle de [!DNL Dynamic Media], procédez comme suit :
<!--
1. Navigate to your [!DNL Assets View] and [create a folder](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/add-delete-assets-view) in ![Assets](/help/assets/assets/Asset-icon.svg)**[!UICONTROL Assets]**. The folder tree in ![Assets](/help/assets/assets/Asset-icon.svg)**[!UICONTROL Assets]** replicates in **[!UICONTROL Dynamic Media Assets]**. Save your [!DNL Dynamic Media] template in this [!UICONTROL Dynamic Media Assets] folder.
1. Select ![Assets](/help/assets/assets/Asset-icon.svg)**[!UICONTROL Assets]** and [upload and publish your images to [!DNL AEM] and [!DNL Dynamic Media] simultaneously](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/publish-assets-to-aem-and-dm#dynamic-media-publish-mode-set-to-upon-activation) to use them in creating the template. Publishing images is required to generate the template's delivery URL, after creating the template. The delivery URL can be used in downstream applications.
1. [Execute these asset uploading and publishing steps](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/publish-assets-to-aem-and-dm?lang=en#dynamic-media-publish-mode-set-to-upon-activation) to upload and publish a font file to AEM and Dynamic Media simultaneously to use it in creating the template. [!UICONTROL Adobe Sans F2] is the only default font available in the text layer. [The supported font file formats are, AFM, OTF, PFB, PFM, PhotoFont, TTC, TTF](https://experienceleague.adobe.com/en/docs/dynamic-media-classic/using/upload-publish/uploading-files#supported-asset-file-formats). Ensure to [reprocess](/help/assets/reprocessing-assets-view.md) the existing fonts to use them in creating the template (On [!DNL Assets View] home page, click ![Assets](/help/assets/assets/Asset-icon.svg)**[!UICONTROL Assets]**, navigate to the font file location, select the font file one at a time and click ![Reprocess](/help/assets/assets/Refresh-docs.svg)**[!UICONTROL Reprocess]**). See [Fonts](https://experienceleague.adobe.com/en/docs/dynamic-media-classic/using/support-files/fonts) to know more about fonts.
-->
1. [Créer une zone de travail vierge](#create-a-canvas)
1. [Ajouter des images à la zone de travail](#add-images-to-the-canvas)
1. [Ajouter des calques de texte à la zone de travail](#add-text-to-the-canvas)
1. [Modifier ou supprimer un calque](#edit-or-delete-a-layer)
1. [Calques de paramètres](#parameterise-a-layer)

### Créer une zone de travail vierge{#create-a-canvas}

Pour créer une zone de travail vide, procédez comme suit :

1. Accédez à [!DNL Assets View], sélectionnez **[!UICONTROL Dynamic Media Assets]** disponible dans le panneau de gauche et accédez à votre dossier pour enregistrer votre modèle dans ce dossier.

   ![Modèles Dynamic Media](/help/assets/assets/DM-Assets1.png)

1. Sélectionnez **[!UICONTROL Créer un modèle]**. La boîte de dialogue **[!UICONTROL Nouveau modèle]** s’affiche.
   ![comment créer des modèles dynamiques qui peuvent être personnalisés en temps réel ](/help/assets/assets/new-template.png)
   >[!NOTE]
   >
   >  Le modèle est enregistré à l’emplacement où vous l’avez créé. Sur [!DNL Assets View] page d’accueil, sélectionnez **[!UICONTROL Dynamic Media Assets]** et cliquez sur **[!UICONTROL Créer un modèle]** pour enregistrer le modèle dans le dossier racine **[!UICONTROL Dynamic Media Assets]**.

1. Indiquez un nom de modèle, définissez la largeur et la hauteur de la zone de travail, puis cliquez sur **[!UICONTROL Créer]**. Une zone de travail vierge s’affiche avec des options de menu des deux côtés à utiliser pour créer le modèle. Pointez sur les options de menu pour afficher leur info-bulle.
   ![ modèle personnalisable en temps réel ](/help/assets/assets/blank-canvas-page.png)

   >[!NOTE]
   >
   > La plage de largeur et de hauteur autorisée va de 50 à 5 000.

**Options de menu dans le volet de droite :** utilisez ces options pour ajouter les calques d’images et de texte nécessaires à la zone de travail.

* ![Modèles DM](/help/assets/assets/add-image.svg) : cliquez pour ajouter des images à la zone de travail.
* ![modèles personnalisables](/help/assets/assets/add-text.svg) : cliquez pour ajouter des textes à la zone de travail.
* ![modèles personnalisables](/help/assets/assets/show-layers-list.svg) : cliquez pour afficher la liste de tous les calques (image et texte) sur la zone de travail. Chaque image et texte ajouté à la zone de travail est représenté sous la forme d’un calque distinct.

**Options de menu dans le volet de gauche :** utilisez ces options pour les actions suivantes de l’éditeur commun.

* ![Modèles DM](/help/assets/assets/layer-selector.svg) : sélectionnez ![Modèles DM](/help/assets/assets/layer-selector.svg) et cliquez sur un calque sur la zone de travail pour le sélectionner.
* ![modèles prenant en charge la personnalisation](/help/assets/assets/bring-forward.svg) : cliquez sur ![modèles prenant en charge la personnalisation](/help/assets/assets/bring-forward.svg) ou utilisez le raccourci clavier **Ctrl** + **]** (Windows) ou **Cmd** + **]** (Mac) pour avancer un calque sélectionné.
* ![comment créer un modèle qui peut être personnalisé facilement ](/help/assets/assets/send-backward.svg) : cliquez sur ![comment créer un modèle qui peut être personnalisé facilement](/help/assets/assets/send-backward.svg) ou utilisez un raccourci clavier, **Ctrl** + **[** (Windows) ou **Cmd** + **[** (Mac) pour envoyer un calque sélectionné vers l’arrière.
* ![créez un modèle qui peut être personnalisé instantanément](/help/assets/assets/undo.svg) : cliquez sur ![créer un modèle qui peut être personnalisé instantanément](/help/assets/assets/undo.svg) ou utilisez un raccourci clavier, **Ctrl** + **Z** (Windows) ou **Cmd** + **Z** (Mac) pour annuler la dernière action.
* ![modèle pour créer rapidement des bannières](/help/assets/assets/redo.svg) : cliquez sur ![modèle pour créer rapidement des bannières](/help/assets/assets/redo.svg) ou utilisez le raccourci clavier **Ctrl** + **Y** (Windows) ou **Cmd** + **Y** (Mac) pour rétablir la dernière action.
* ![modèle pour créer rapidement des prospectus](/help/assets/assets/zoom-in.svg) : cliquez sur ![modèle pour créer rapidement des prospectus](/help/assets/assets/zoom-in.svg) ou utilisez le raccourci clavier **Ctrl** + **+** (Windows) ou **Cmd** + **+** (Mac) pour effectuer un zoom sur la zone de travail.
* ![modèle pour créer rapidement des bannières](/help/assets/assets/Zoom-out.svg) : cliquez sur ![modèle pour créer rapidement des bannières](/help/assets/assets/Zoom-out.svg) ou utilisez le raccourci clavier **Ctrl** + **-** (Windows) ou **Cmd** + **-** (Mac) pour effectuer un zoom arrière sur la zone de travail.
* Appuyez sur **Retour arrière** ou **Supprimer** pour supprimer le calque sélectionné si aucun texte ou propriété n’est modifié.

Cliquez sur ![modèle pour créer rapidement des prospectus](/help/assets/assets/show-layers-list.svg) et sélectionnez d’autres options (![](/help/assets/assets/three-dots.svg)) sur le calque Zone de travail pour modifier les dimensions de la zone de travail à tout moment lors de la création du modèle.
![](/help/assets/assets/edit-canvas1.png)

>[!NOTE]
>
> Les modèles autorisent un maximum de 20 calques, Zone de travail incluse.

### Ajouter des images à la zone de travail{#add-images-to-the-canvas}

Pour ajouter des images à la zone de travail, procédez comme suit :

1. Cliquez sur ![créer une bannière en un rien de temps](/help/assets/assets/add-image.svg) pour ouvrir le panneau [Sélecteur de ressources](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/manage/asset-selector/overview-asset-selector). Le panneau affiche les images de votre instance AEM Assets synchronisées avec [!DNL Dynamic Media].
1. Parcourez le panneau ou utilisez des mots-clés dans la barre de recherche pour trouver une image spécifique.
1. Faites glisser et déposez une image sur la zone de travail pour l’utiliser. Pour redimensionner ou repositionner un calque sur la zone de travail, reportez-vous au [**[!UICONTROL panneau Propriétés]**](#reposition-resize-delete-a-layer).
   ![créez une bannière en quelques secondes](/help/assets/assets/add-image-to-canvas.png)

### Ajouter des calques de texte à la zone de travail{#add-text-to-the-canvas}

Pour ajouter des calques de texte à la zone de travail, procédez comme suit :

1. Cliquez sur ![création rapide de nouvelles bannières](/help/assets/assets/add-text.svg) pour ajouter un calque de texte à la zone de travail et ouvrir le panneau Propriétés.
1. Sélectionnez le calque et cliquez sur le texte pour le mettre à jour.
1. Sélectionnez **[!UICONTROL Redimensionnement intelligent du texte]** dans le panneau Propriétés pour ajuster automatiquement la longueur du texte et la taille de police afin qu’ils s’adaptent de manière optimale à la zone désignée.
   ![meilleures bannières personnalisables](/help/assets/assets/add-text-layer.png)

Pour repositionner, redimensionner, faire pivoter ou supprimer le calque, reportez-vous au [**[!UICONTROL panneau Propriétés]**](#reposition-resize-delete-a-layer). Mettez en forme votre texte selon la police, la taille, la couleur, le style et l’alignement requis (dans le calque) en modifiant leurs valeurs dans les champs respectifs sous la section **[!UICONTROL Texte]** du panneau. Le champ **[!UICONTROL Famille de polices]** affiche la police par défaut [!UICONTROL Adobe Sans F2], les polices existantes retraitées et les polices nouvellement chargées et publiées. Pour plus d’informations, reportez-vous au point 5 de la section [Avant de commencer](#prerequisites-for-dynamic-media-wysiwyg-template) ci-dessus.

### Modifier ou supprimer un calque {#edit-or-delete-a-layer}

Pour modifier ou supprimer un calque de zone de travail, procédez comme suit :

1. Cliquez sur ![Modèles prenant en charge les mises à jour dynamiques](/help/assets/assets/show-layers-list.svg) et sélectionnez le calque dans la zone de travail ou dans la liste Calques.
1. Cliquez sur **[!UICONTROL autres options]** (![modèles avec prise en charge des mises à jour en temps réel](/help/assets/assets/three-dots.svg)) pour modifier ou supprimer le calque.
1. Cliquez sur **[!UICONTROL Supprimer]** pour supprimer le calque.
1. Cliquez sur **[!UICONTROL Modifier]** pour modifier le calque à l’aide du [**[!UICONTROL panneau Propriétés]**](#reposition-resize-delete-a-layer).
   ![création rapide de bannières](/help/assets/assets/dm-templates/edit-delete-layer.png)

### Panneau Propriétés{#properties-panel}

Pour accéder au panneau des propriétés d’un calque :

1. Cliquez sur ![création rapide de contenu](/help/assets/assets/show-layers-list.svg).
1. Sélectionnez le calque dans la liste.

Ce panneau affiche la position du point central du calque sur le plan de la zone de travail (valeurs X et Y) et les dimensions du calque (largeur et hauteur), ainsi que les options de mise en forme du texte.

![création rapide de contenu](/help/assets/assets/properties-panel.png)

Dans le panneau des propriétés d’un calque, sélectionnez un autre calque sur la zone de travail pour accéder à son panneau des propriétés.


#### Repositionnement, redimensionnement, rotation ou suppression d’un calque{#reposition-resize-delete-a-layer}

Pour modifier un calque de texte ou d’image, reportez-vous aux actions courantes de modification de calque suivantes :

* **Repositionner le calque :** faites glisser le calque pour le déplacer n’importe où sur la zone de travail. Cette action met à jour les valeurs X et Y dans le panneau des propriétés.
* **Redimensionner le calque :** sélectionnez le calque et faites glisser ses poignées de bordure pour le redimensionner. Cette action met à jour les valeurs W (largeur) et H (hauteur) dans le panneau des propriétés.
* **Faire pivoter le calque :** faites glisser la poignée carrée placée verticalement au-dessus du calque pour la faire pivoter autour de son centre. Cette action met à jour les valeurs d’angle dans le panneau Propriétés.
* **Supprimer le calque :** appuyez sur **Retour arrière** ou **supprimer**, puis cliquez sur **[!UICONTROL Confirmer]** pour supprimer un calque sélectionné.

#### Options de formatage du texte{#text-formatting-options-on-properties-panel}

Mettez en forme votre texte selon la police, la taille, la couleur, le style et l’alignement requis (dans le calque) en modifiant leurs valeurs dans les champs respectifs sous la section **[!UICONTROL Texte]** du panneau.
Veillez à inclure **[!UICONTROL Redimensionnement de texte intelligent]**. [!UICONTROL Redimensionnement intelligent de texte] fonctionne sur l’algorithme [Copyfit](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/text-formatting/r-copy-fitting) pour remplir de manière optimale le texte dans la zone de texte, empêcher le débordement du texte et réduire l’espace supplémentaire au bas du texte.

![ création de contenu en un rien de temps ](/help/assets/assets/smart-text-resize.png)

### Calques de paramètres {#parameterise-a-layer}

Après avoir créé un modèle avec plusieurs calques d’images et de textes, paramétrez les calques sélectionnés. Lorsqu’un calque ou sa propriété est paramétré, il obtient une paire clé-valeur (également appelée paramètre ). Ce paramètre peut être inclus dans l’URL du modèle pour mettre à jour la position, la taille ou le contenu du calque en temps réel, ce qui se traduit par une personnalisation du modèle en un rien de temps.

Pour paramétrer un calque :

1. Cliquez sur ![création instantanée de contenu](/help/assets/assets/show-layers-list.svg), sélectionnez un calque et cliquez sur **[!UICONTROL Paramètres]**. Le panneau **[!UICONTROL Paramètres]** s’affiche.
1. Activez le bouton (bascule) **[!UICONTROL Inclure le paramètre]** pour paramétrer une propriété. Voir [Option du panneau Paramètres](#parameterisation-options-or-allowed-parameters) pour connaître le comportement de la propriété après le paramétrage.
1. **Facultatif :** renommez le nom du paramètre. Un nom de paramètre comporte un nom de calque suivi d’un suffixe. Pour un calque sélectionné, toutes ses propriétés paramétrées partagent le même nom de calque suivi d’un suffixe variable. Renommez le nom du calque en suivant la convention de nommage sémantique de sorte que, lorsque vous incluez le paramètre dans l’URL, le nom du paramètre explique lui-même le contenu du calque ou son objectif.
1. Cliquez sur **[!UICONTROL Enregistrer]**.
   ![création instantanée de contenu](/help/assets/assets/parameterise-a-layer.png)
Pour basculer entre le panneau Paramètres d’un calque d’image et de texte, sélectionnez le calque sur la zone de travail et cliquez sur **[!UICONTROL Paramètres]**.

#### Option du panneau Paramètres {#parameterisation-options-or-allowed-parameters}

Les propriétés paramétrées peuvent être incluses en tant que paramètres d’URL dans l’URL du modèle pour modifier le modèle en temps réel à l’aide de l’URL.

**Paramètres d’image :**

**[!UICONTROL X]:** Inclure pour déplacer le calque horizontalement le long de son axe central, parallèlement à l’axe X du plan du modèle, en modifiant la valeur du paramètre dans l’URL.
**[!UICONTROL Y]:** Inclure pour déplacer le calque verticalement le long de sa ligne centrale, parallèlement à l’axe Y du plan du modèle, en modifiant la valeur du paramètre dans l’URL.
**[!UICONTROL Largeur] :** permet d’ajuster la largeur du calque en modifiant la valeur du paramètre dans l’URL.
**[!UICONTROL Hauteur] :** permet d’ajuster la hauteur du calque en modifiant la valeur du paramètre dans l’URL.
**[!UICONTROL Masquer] :** permet d’inclure pour masquer ou afficher le calque dans le modèle à l’aide des options 0 (afficher) et 1 (masquer).
**[!UICONTROL Source]:** Inclure pour remplacer l’image du calque par une nouvelle image en modifiant le chemin d’accès à l’image dans la valeur du paramètre dans l’URL.

**Paramètres de formatage du texte :**

Insérez les paramètres ci-dessous pour modifier le texte, sa police, sa couleur et sa taille à partir de l’URL en mettant à jour les valeurs de paramètre dans l’URL.

**[!UICONTROL Texte]:** Inclure pour mettre à jour le texte de l’URL.
**[!UICONTROL Famille de polices] :** permet d’inclure pour mettre à jour la police du texte à partir de l’URL.
**[!UICONTROL Taille de police] :** permet d’inclure pour mettre à jour la taille de police du texte à partir de l’URL.
**[!UICONTROL Couleur du texte] :** incluez pour mettre à jour la couleur de police du texte à partir de l’URL.

### Regroupez les calques pour contrôler leur visibilité simultanément{#group-layers}

Pour conserver la flexibilité de vos modèles, vous pouvez également utiliser un seul nom de paramètre pour contrôler plusieurs calques. Cette stratégie est utile pour le paramètre de visibilité (masquer ou afficher les calques), afin de mettre à jour la conception ou les graphiques d’un seul modèle.

Pour attribuer le même nom aux paramètres de masquage (![création rapide de contenu](/help/assets/assets/Visibility-icon.svg)) de plusieurs calques, procédez comme suit pour masquer ou afficher les calques simultanément.

1. Accédez au [**[!UICONTROL panneau Propriétés]**](#parameterise-a-layer) d’un calque.
1. Activez/désactivez le paramètre **[!UICONTROL Masquer]** s’il n’est pas paramétré précédemment.
1. **Facultatif :** renommez le paramètre **[!UICONTROL Masquer]**.
1. Copiez le nom du paramètre **[!UICONTROL Masquer]**.
1. Accédez au panneau Paramètre des autres calques en les sélectionnant dans la zone de travail et en activant/désactivant leur paramètre **[!UICONTROL Masquer]** s’il n’est pas paramétré.
1. Remplacez leur nom **[!UICONTROL Masquer le paramètre]** par le nom copié.
1. Cliquez sur **[!UICONTROL Enregistrer]** pour regrouper les calques.
1. Exécutez les étapes 3 et 4 de la section [**[!UICONTROL Prévisualisation et publication]**](#preview-and-publish-template-and-copy-template-deliver-url) pour afficher vos modifications.

## Prévisualiser et publier le modèle pour copier l’URL de diffusion{#preview-and-publish-template-and-copy-template-deliver-url}

Procédez comme suit pour prévisualiser et publier le modèle et copier l’URL de diffusion :

1. Sur la page Zone de travail, cliquez sur **[!UICONTROL Aperçu]**. Vous pouvez également accéder à **[!UICONTROL Vue Assets]** **>** **[!UICONTROL Dynamic Media Assets]** **>** rechercher et sélectionner votre modèle **>** cliquer sur **[!UICONTROL Modifier le modèle]**>**>** cliquer sur **[!UICONTROL Preview]**. La page d’aperçu affiche le modèle, ses paramètres (calques et propriétés paramétrés), l’état de publication et l’option **[!UICONTROL Publier]**.
1. Sélectionnez des paramètres dans le panneau **[!UICONTROL Paramètres du modèle]** pour modifier leurs valeurs et mettre instantanément à jour le contenu, la taille, la position ou le formatage textuel du calque de modèle correspondant dans l’aperçu. Par exemple :
   1. Sélectionnez un calque de texte et modifiez son texte ou
   1. Sélectionnez un calque d’image, cliquez sur ![création de contenu à la volée](/help/assets/assets/add-image.svg), sélectionnez une image dans le sélecteur de ressources, puis cliquez sur **[!UICONTROL Actualiser]**.

   Le modèle est immédiatement mis à jour, affichant le texte modifié et remplaçant l’image précédente par la nouvelle. En outre, la valeur du paramètre d’image reflète le nouveau chemin d’accès à l’image. De même, vous pouvez redimensionner un calque en ajustant ses valeurs, et les modifications sont appliquées au modèle en temps réel.
1. Sélectionnez le paramètre **[!UICONTROL Masquer]** pour les calques [groupés](#group-layers) dans la liste pour les afficher ou les masquer ensemble dans le modèle.
1. **Facultatif :** modifiez la valeur du paramètre **[!UICONTROL Masquer]** comprise entre 0 et 1 et cliquez sur **[!UICONTROL Actualiser]** pour afficher les modifications. Les calques ayant le même paramètre **[!UICONTROL Masquer]** masquent ou s’affichent ensemble. De même, vous pouvez contrôler la visibilité des calques à partir de l’URL.

   ![création de contenu à la volée](/help/assets/assets/dm-templates-publish-status.png)
Vous pouvez également activer le bouton (bascule) **[!UICONTROL Inclure tous les paramètres]** pour modifier toutes les valeurs de paramètre affichées et voir les mises à jour dans l’aperçu du modèle.
   <br>
1. Pour publier le modèle à partir de la page d’aperçu, cliquez sur **[!UICONTROL Publier]** et confirmez la publication. Un message **[!UICONTROL Publication terminée]** s’affiche et le statut de publication est mis à jour sur **[!UICONTROL Publié]**.

### Copier l’URL de diffusion

Les paramètres sélectionnés sur la page **[!UICONTROL Aperçu]** deviennent les paramètres d’URL dans l’URL du modèle.

Assurez-vous que les images du modèle sont déjà publiées sur AEM et Dynamic Media pour générer l’URL de diffusion du modèle.

Pour copier l&#39;URL de diffusion du modèle, procédez comme suit :

1. Cliquez sur **[!UICONTROL Copier l’URL]**. La boîte de dialogue **[!UICONTROL Copier l’URL]** s’affiche. Sélectionnez et copiez l’URL affichée. Le premier paramètre de l’URL commence après un point d’interrogation **([!UICONTROL  ?])** et une paire clé-valeur commence par **[!UICONTROL $]** et se termine par **[!UICONTROL &amp;]**. La clé et la valeur sont séparées par un signe égal **([!UICONTROL =])**, avec la clé à gauche et la valeur à droite.
1. Collez cette URL dans l’onglet de votre navigateur et affichez votre modèle dynamique. Personnalisez le modèle en temps réel en mettant à jour la valeur du paramètre requis (valeur de la clé) dans l’URL directement, comme illustré à l’[étape 2](#preview-and-publish-template-and-copy-template-deliver-url) de la section **Prévisualisation et publication**.
1. Utilisez cette URL pour un merchandising rapide de vos produits ou services. Vous pouvez partager cette URL avec vos clients ou l’intégrer à votre site web ou à toute application tierce en aval pour afficher la bannière et y apporter des mises à jour en temps réel afin de refléter les offres en cours.

## Effectuer des mises à jour en temps réel sur le modèle à partir de l’URL{#update-the-template-from-the-url}

Modifier des paramètres directement dans l’URL peut s’avérer fastidieux. Pour simplifier :

1. Copiez l’URL et collez-la dans un bloc-notes.
1. Utilisez Cmd+F (Mac) ou Ctrl+F (Windows) pour rechercher et modifier les valeurs de paramètre. Par exemple :
   * Recherchez et remplacez les chemins d’accès des calques d’image.
   * Recherchez les coordonnées [paramétrées](#parameterise-a-layer), la largeur et la hauteur du calque pour ajuster leurs valeurs.
   * Modifiez le texte, la police, la couleur, la taille ou l’alignement des calques de texte.
   * Modifiez les valeurs de visibilité comprises entre 0 et 1.

Collez cette URL mise à jour dans votre navigateur pour afficher les modifications.

## Modification du modèle{#edit-the-template}

Modifiez le modèle en procédant comme suit :

1. Sur la [!DNL Assets view], cliquez sur **[!UICONTROL Dynamic Media Assets]**.
2. Accédez à l’emplacement du modèle.
3. Sélectionnez le modèle.
4. Cliquez sur **[!UICONTROL Modifier le modèle]**. La zone de travail de modèle affiche le modèle et la liste de tous ses calques dans le panneau Calques. Commencez à modifier le modèle en fonction de vos besoins.

## Ajoutez un lien Appel à l’action (CTA) à votre calque de modèle{#add-CTA-in-dynamic-media-templates}

Transformez n’importe quel calque d’image ou de texte de votre modèle de [!DNL Dynamic Media] en lien hypertexte en y ajoutant un lien CTA qui dirige les utilisateurs vers une page cible.

Pour ajouter un lien CTA à une couche, procédez comme suit :

1. Accédez à l’emplacement de votre modèle, sélectionnez le modèle et cliquez sur ![modifier](/help/assets/assets/edit-pen-icon.svg) **[!UICONTROL Modifier le modèle]**. Le modèle s’affiche sur la zone de travail.
1. Sélectionnez le calque de modèle et [accédez à son panneau Propriétés](#edit-or-delete-a-layer) pour y ajouter un lien CTA.
1. Dans le panneau des propriétés, sélectionnez **[!UICONTROL Ajouter un CTA]**, spécifiez l’URL de destination dans le champ **[!UICONTROL URL]** et cliquez sur **[!UICONTROL Enregistrer]**.

   ![ajouter CTA](/help/assets/assets/add-cta.png)

1. Cliquez sur **[!UICONTROL Aperçu]** et sélectionnez **[!UICONTROL Publier]** pour publier votre modèle, s’il n’a pas été publié auparavant.
1. Accédez au dossier dans lequel ce modèle est enregistré, sélectionnez-le et cliquez sur ![page de détails](/help/assets/assets/details-page-icon.svg) **[!UICONTROL Détails]**.
1. Cliquez sur **[!UICONTROL Copier les options]** et sélectionnez **[!UICONTROL Copier le code intégré]**. Veillez à publier les images du modèle dans [!DNL AEM and Dynamic Media] pour copier le code incorporé.

   ![copier le code incorporé](/help/assets/assets/copy-options1.png)

   Voici un exemple de code intégré :

   ```json
    <div class="adobe-dynamicmedia-template-embed-container">
    <img id="<Image ID>>" src="<Image Source>>" alt="adobe dynamicmedia template" usemap="#adobe-dynamicmedia-template-map" width="800" height="300">
    <map name="adobe-dynamicmedia-template-map">
    <area shape="rect" coords="417,-60,817,340" href="https://business.adobe.com/products.html" alt="Layer with CTA" title="https://business.adobe.com/products.html" target="_blank">
    <area shape="rect" coords="6,206.57,129,231.43" href="https://business.adobe.com/products.html" alt="Layer with CTA" title="https://business.adobe.com/products.html" target="_blank">
    </map>
    </div>
   ```

1. Ajoutez le code intégré copié au fichier HTML de votre site et exécutez-le dans votre navigateur pour afficher le modèle.

Cliquez sur l’élément CTA sur le modèle pour accéder à la page de destination.

Regardez cette vidéo détaillée pour découvrir comment ajouter un lien CTA à un calque de modèle.

>[!VIDEO](https://video.tv.adobe.com/v/3457616)

## Points importants à noter {#important-points-to-note}

* Après avoir créé un modèle avec des calques d’image paramétrés pour les mises à jour dynamiques, assurez-vous que les images destinées aux futures mises à jour partagent les mêmes dimensions que les images paramétrées. Cela permet de s’assurer que les images s’intègrent parfaitement aux calques sans déborder ou laisser d’espaces vides. Actuellement, le modèle ne prend pas en charge les ajustements de dimension automatiques pour ajuster les images dans les calques.
* Il n’existe aucune prise en charge de sous-chaînes dans un calque de texte. Impossible d’appliquer différentes propriétés de police à la sous-chaîne d’un calque de texte.
* La prise en charge de plusieurs entreprises [!DNL Dynamic Media] n’est actuellement pas disponible avec les modèles [!DNL Dynamic Media].
* En cas de copie ou de déplacement, le sélecteur de destination affiche tous les dossiers (y compris les dossiers synchronisés non [!DNL Dynamic Media]). En outre, à l’heure actuelle, elle n’affiche pas les ressources du modèle de [!DNL Dynamic Media] (il s’agit dans les deux cas de limitations du sélecteur de destination).
* Toute opération de mise à jour sur un dossier (par exemple, Publication ou Suppression) à partir de la section Assets a un impact sur les modèles de [!DNL Dynamic Media] disponibles dans ce dossier.
* La corbeille ne fonctionne pas pour les modèles [!DNL Dynamic Media]. Si une ressource est déplacée vers la corbeille, puis restaurée, elle est restaurée dans AEM, mais pas en [!DNL Dynamic Media]. Il en va de même pour les modèles [!DNL Dynamic Media].

## Voir également

1. Explorez [[!DNL Dynamic Media]  et ses fonctionnalités](/help/assets/dynamic-media/dynamic-media.md)
1. Explorer [[!DNL Dynamic Media] avec les fonctionnalités OpenAPI](/help/assets/dynamic-media-open-apis-overview.md)