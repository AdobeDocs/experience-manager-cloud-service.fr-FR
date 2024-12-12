---
title: Gestion des paramètres d’image prédéfinis
description: Découvrez les paramètres d’image prédéfinis et comment les créer, les modifier et les gérer.
contentOwner: Rick Brough
feature: Image Presets,Viewers,Renditions
role: User
exl-id: a53f40ab-0e27-45f8-9142-781c077a04cc
source-git-commit: baffc15d482ad3b57337c1ee5fe3e622253ae8cb
workflow-type: tm+mt
source-wordcount: '3550'
ht-degree: 72%

---

# Gestion des paramètres d’image prédéfinis{#managing-image-presets}

Les paramètres d’image prédéfinis permettent à Adobe Experience Manager Assets de diffuser des images dynamiquement dans différentes tailles, dans différents formats ou avec d’autres propriétés d’image générées dynamiquement. Chaque paramètre d’image prédéfini représente un ensemble prédéfini de commandes de dimensionnement et de mise en forme pour l’affichage des images. Lorsque vous créez un paramètre d’image prédéfini, vous choisissez une taille pour la diffusion de l’image. Vous pouvez également choisir des commandes de mise en forme afin d’optimiser l’apparence de l’image lors de sa diffusion.

Les administrateurs peuvent créer des paramètres prédéfinis pour l’exportation de fichiers. Les utilisateurs peuvent choisir un paramètre prédéfini lors de l’exportation d’images, qui reformate également les images selon les spécifications définies par l’administrateur.

Vous pouvez également créer des paramètres d’image prédéfinis réactifs. Si vous appliquez un paramètre d’image prédéfini réactif à vos ressources, il change en fonction de l’appareil ou de la taille d’écran sur lequel elles sont affichées. Vous pouvez configurer les paramètres d’image prédéfinis pour qu’ils utilisent le CMJN dans l’espace colorimétrique, en plus du RGB ou du gris.

Cette section décrit comment créer, modifier et gérer généralement les paramètres d’image prédéfinis. Vous pouvez appliquer un paramètre d’image prédéfini à une image lorsque vous la prévisualisez. Voir [Application de paramètres prédéfinis d’image](/help/assets/dynamic-media/image-presets.md).

>[!NOTE]
>
>L’imagerie dynamique fonctionne avec vos paramètres d’image prédéfinis existants et utilise des informations à la dernière milliseconde de la diffusion pour réduire davantage la taille du fichier image en fonction de la vitesse de connexion du navigateur ou du réseau. Voir [Imagerie numérique](/help/assets/dynamic-media/imaging-faq.md) pour plus d’informations.

## En savoir plus sur les paramètres prédéfinis d’image {#understanding-image-presets}

Tout comme une macro, un paramètre d’image prédéfini est un ensemble prédéfini de commandes de dimensionnement et de formatage enregistrées sous un nom. Pour comprendre le fonctionnement des paramètres d’image prédéfinis, supposons que votre site web exige que chaque image du produit s’affiche dans des tailles différentes, des formats différents et des taux de compression différents pour diffusion sur les ordinateurs de bureau et les appareils mobiles.

Vous pouvez créer deux paramètres d’image prédéfinis : 500 x 500 pixels pour l’ordinateur de bureau et 150 x 150 pixels pour les appareils mobiles. Vous créez deux paramètres d’image prédéfinis, l’un appelé `Enlarge` pour afficher des images à 500 x 500 pixels et l’autre appelé `Thumbnail` pour afficher des images à 150 x 150 pixels. Pour diffuser des images à la taille `Enlarge` et `Thumbnail`, l’Experience Manager trouve la définition des `Enlarge Image Preset` et `Thumbnail Image Preset`. Ensuite, Experience Manager génère de manière dynamique une image dont la taille et le format correspondent à chaque paramètre d’image prédéfini.

Les images dont la taille est réduite lorsqu’elles sont diffusées dynamiquement peuvent perdre en netteté et en détail. C’est pourquoi chaque paramètre d’image prédéfini contient des commandes de mise en forme pour optimiser une image lorsqu’elle est diffusée à une taille spécifique. Ces commandes garantissent que vos images sont nettes et claires lorsqu’elles sont diffusées sur votre site web ou dans votre application.

Les administrateurs et administratrices peuvent créer des paramètres d’image prédéfinis. Pour créer un paramètre d’image prédéfini, vous pouvez partir de zéro ou partir d’un paramètre existant et l’enregistrer sous un nouveau nom.

## Gestion des paramètres d’image prédéfinis {#managing-image-presets-1}

Pour gérer vos paramètres d’image prédéfinis dans Experience Manager, sélectionnez le logo de l’Experience Manager afin d’accéder à la console de navigation globale, puis sélectionnez l’icône Outils et accédez à **[!UICONTROL Assets]** > **[!UICONTROL Paramètres d’image prédéfinis]**.

![6_5_tools-assets-imagepresets](assets/6_5_tools-assets-imagepresets.png)

>[!NOTE]
>
>Tous les paramètres d’image prédéfinis que vous créez sont également disponibles en tant que rendus dynamiques lorsque vous prévisualisez ou diffusez des ressources.
>
>Vous n’avez *pas besoin de publier les paramètres d’image prédéfinis, car les paramètres d’image prédéfinis sont automatiquement publiés.*
>
>Voir [Publication de paramètres d’image prédéfinis](#publishing-image-presets).

>[!NOTE]
>
>Le système affiche différents rendus lorsque vous sélectionnez **[!UICONTROL Rendus]** dans l’affichage des détails d’une ressource. Vous pouvez augmenter ou diminuer le nombre de paramètres d’image prédéfinis qui s’affichent. Voir [Augmentation du nombre de paramètres prédéfinis d’image affichés](#increasing-or-decreasing-the-number-of-image-presets-that-display).

### Formats de fichiers Adobe Illustrator (AI), PostScript® (EPS) et PDF {#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats}

Si vous avez l’intention de prendre en charge l’ingestion de fichiers AI, EPS et PDF afin de pouvoir générer des rendus dynamiques de ces formats de fichiers, passez en revue les informations suivantes avant de créer des paramètres d’image prédéfinis.

Le format de fichier d’Adobe Illustrator est une variante du format PDF. Les principales différences, dans le contexte de Experience Manager Assets, sont les suivantes :

* Les documents Adobe Illustrator se composent d’une seule page avec plusieurs calques. Chaque calque est extrait sous la forme d’une sous-ressource PNG sous la ressource Illustrator principale.
* Les documents PDF se composent d’une ou de plusieurs pages. Chaque page est extraite sous la forme d’une sous-ressource PDF d’une seule page sous le document PDF multi-pages principal.

Le composant `Create Sub Asset process` crée les sous-ressources dans le workflow `DAM Update Asset` global. Pour voir ce composant de processus dans le processus, accédez à **[!UICONTROL Outils]** > **[!UICONTROL Processus]** > **[!UICONTROL Modèles]** > **[!UICONTROL Ressource de mise à jour de gestion des actifs numériques]** > **[!UICONTROL Modifier]**.

<!-- See also [Viewing pages of a multi-page file](/help/assets/manage-linked-subassets.md#view-pages-of-a-multi-page-file). -->

Vous pouvez afficher les sous-ressources ou les pages lorsque vous ouvrez la ressource, sélectionnez le menu Contenu et sélectionnez **[!UICONTROL Sous-ressources]** ou **[!UICONTROL Pages]**. Les sous-ressources sont des ressources à part entière. Le composant de workflow `Create Sub Asset` extrait les pages du PDF. Elles sont ensuite stockées sous les noms `page1.pdf`, `page2.pdf`, etc. sous la ressource principale. Une fois qu’elles sont stockées, le workflow `DAM Update Asset` les traite.

Pour utiliser Dynamic Media afin de prévisualiser et de générer des rendus dynamiques pour des fichiers AI, EPS ou PDF, les étapes de traitement suivantes doivent être exécutées :

1. Dans le workflow `DAM Update Asset`, le composant de processus `Rasterize PDF/AI Image Preview Rendition` pixellise la première page de la ressource d’origine, à l’aide de la résolution configurée, dans un rendu `cqdam.preview.png`.

1. Le composant de processus `Dynamic Media Process Image Assets` du workflow optimise le rendu `cqdam.preview.png` dans un fichier PTIFF.

>[!NOTE]
>
>L’étape **[!UICONTROL Miniatures EPS]** du workflow Ressource de mise à jour de gestion des actifs numériques (DAM) génère des miniatures pour les fichiers EPS.

#### Propriétés des métadonnées de ressource PDF/AI/EPS {#pdf-ai-eps-asset-metadata-properties}

| **Propriété de métadonnées** | **Description** |
|---|---|
| `dam:Physicalwidthininches` | Largeur du document en pouces. |
| `dam:Physicalheightininches` | Hauteur du document en pouces. |

Vous accédez aux options des composants de processus `Rasterize PDF/AI Image Preview Rendition` par le biais du workflow `DAM Update Asset`.

Sélectionnez Adobe Experience Manager dans le coin supérieur gauche, puis cliquez sur **[!UICONTROL Outils]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modèles]**. Dans la page Modèles de workflow, sélectionnez **[!UICONTROL Ressource de mise à jour DAM]** puis, dans la barre d’outils, sélectionnez **[!UICONTROL Modifier]**. Sur la page du workflow Ressources de mise à jour de gestion des actifs numériques , double-sélectionnez le composant de processus `Rasterize PDF/AI Image Preview Rendition` pour ouvrir la boîte de dialogue Propriétés des étapes .

#### Options Pixelliser le rendu d’aperçus d’image PDF/AI {#rasterize-pdf-ai-image-preview-rendition-options}

![Arguments pour pixelliser le workflow PDF ou AI](assets/rasterize_pdf_ai_image_preview.png)

Arguments pour pixelliser le workflow PDF ou AI

| Argument de processus | Paramètre par défaut | Description |
|---|---|---|
| Types MIME | application/pdf<br>application/postscript<br>application/illustrator | Liste des types MIME de documents considérés comme des documents PDF ou Illustrator. |
| Largeur max. | 2048 | Largeur maximale du rendu d’aperçu généré, en pixels. |
| Hauteur max. | 2048 | Hauteur maximale du rendu d’aperçu généré, en pixels. |
| Résolution | 72 | Résolution de pixellisation de la première page, en ppp (pixels par pouce). |

À l’aide des arguments de processus par défaut, la première page d’un document PDF/AI est pixellisée à 72 ppp et l’image de prévisualisation générée est dimensionnée à 2 048 x 2 048 pixels. Pour un déploiement standard, vous pouvez augmenter la résolution sur une valeur minimale de 150 ppp ou plus. Par exemple, un document de format Lettre US à 300 ppp doit avoir une largeur et une hauteur maximales de 2 550 x 3 300 pixels, respectivement.

Largeur max. et Hauteur max. limitent la résolution à laquelle la pixellisation doit être effectuée. Par exemple, si vous ne modifiez pas les valeurs maximales et que la résolution est définie sur 300 ppi, un document de lettre américaine est pixellisé à 186 ppi. En d’autres termes, le document fait 1 581 x 2 046 pixels.

Une valeur maximale est définie pour le composant de processus `Rasterize PDF/AI Image Preview Rendition`, afin de s’assurer qu’il ne crée pas d’images exagérément grandes en mémoire. Ces images volumineuses peuvent, en effet, dépasser la capacité de mémoire allouée à la machine virtuelle Java™ (JVM). Il faut veiller à fournir suffisamment de mémoire à la machine virtuelle Java pour gérer le nombre configuré de workflows parallèles, de sorte que chacun d’eux soit en mesure de créer une image à la taille maximale configurée.

### Format de fichier InDesign (INDD) {#indesign-indd-file-format}

Si vous avez l’intention de prendre en charge l’ingestion de fichiers INDD afin de pouvoir générer le rendu dynamique de ce format de fichier, passez en revue les informations suivantes avant de créer des paramètres d’image prédéfinis.

Dans le cas des fichiers InDesign, les sous-ressources ne sont extraites que si Adobe InDesign Server est intégré à Experience Manager. Les ressources référencées sont liées en fonction de leurs métadonnées. InDesign Server n’est pas nécessaire pour la liaison. Cependant, les ressources référencées doivent être présentes dans Experience Manager avant que les fichiers InDesign soient traités, pour que les liens soient créés entre les fichiers InDesign et les ressources référencées.

<!-- See [Integrate Experience Manager Assets with InDesign Server](/help/assets/indesign.md). -->

Le composant Extraction de médias du workflow `DAM Update Asset` exécute plusieurs scripts d’extension préconfigurés pour traiter des fichiers InDesign.

![Chemins ExtendScript dans les arguments du processus Extraction de médias](/help/assets/dynamic-media/assets/6_5_mediaextractionprocess.png)

Chemins ExtendScript dans les arguments du composant de processus Extraction de médias dans le workflow Ressource de mise à jour de gestion des actifs numériques.

Les scripts suivants sont utilisés par l’intégration Dynamic Media :


| Nom ExtendScript | Valeur par défaut | Description |
|---|---|---|
| ThumbnailExport.jsx | Oui | Génère un rendu `thumbnail.jpg` de 300 PPP optimisé et transformé en rendu PTIFF par le composant de processus `Dynamic Media Process Image Assets`. |
| JPEGPagesExport.jsx | Oui | Génère une sous-ressource JPEG de 300 PPP pour chaque page. Une sous-ressource JPEG est une véritable ressource stockée sous la ressource InDesign. Le workflow `DAM Update Asset` l’optimise et le convertit en PTIFF. |
| PDFPagesExport.jsx | Non | Génère une sous-ressource PDF pour chaque page. La sous-ressource PDF est traitée comme indiqué précédemment. Étant donné que le PDF ne contient qu’une seule page, aucune sous-ressource n’est générée. |

### Configuration de la taille de la miniature de l’image {#configuring-image-thumbnail-size}

Vous pouvez définir la taille des miniatures en configurant ces paramètres dans le workflow **[!UICONTROL Ressource de mise à jour de gestion des actifs numériques (DAM)]**. Le workflow comprend deux étapes au cours desquelles vous pouvez configurer la taille de miniature des ressources d’images. Un fichier (**[!UICONTROL Ressources d’image du processus de média dynamique]**) est utilisé pour les ressources d’images dynamiques. L’autre (**[!UICONTROL Miniatures des processus]**) est utilisé pour la génération de miniatures statiques ou lorsque tous les autres processus ne génèrent pas de miniatures. Quoi qu’il en soit, *les deux* doivent avoir les mêmes paramètres.

L’étape **[!UICONTROL Dynamic Media Process Image Assets]** utilise le serveur d’images pour générer des miniatures, indépendamment de la configuration appliquée à l’étape **[!UICONTROL Process Thumbnails]**. La génération de miniatures en passant par l’étape **[!UICONTROL Miniatures des processus]** constitue la méthode la plus lente et la plus gourmande en mémoire.

Le dimensionnement des miniatures est défini au format suivant :**[!UICONTROL largeur:height:centrer]**, par exemple `80:80:false`. La largeur et la hauteur déterminent la taille en pixels de la miniature. La valeur « centrer » est soit false soit true. Si elle est définie sur true, elle indique que la miniature a exactement la taille spécifiée dans la configuration. Si l’image redimensionnée est plus petite, elle est centrée dans la miniature.

>[!NOTE]
>
>* La taille des miniatures pour les fichiers EPS est configurée à l’étape **[!UICONTROL Miniatures EPS]**, dans l’onglet **[!UICONTROL Arguments]** sous Miniatures.
>
>* Les tailles des miniatures pour les vidéos sont configurées à l’étape **[!UICONTROL Miniatures FFmpeg]**, dans l’onglet **[!UICONTROL Processus]** sous **[!UICONTROL Arguments]**.
>

**Pour configurer la taille de la miniature de l’image :**

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modèles]** > **[!UICONTROL Ressource de mise à jour de gestion des actifs numériques]** > **[!UICONTROL Modifier]**.
1. Sélectionnez l’étape **[!UICONTROL Ressources d’image du processus de média dynamique]**, puis sélectionnez l’onglet **[!UICONTROL Miniatures]**. Modifiez la taille de la miniature, si nécessaire, puis sélectionnez **[!UICONTROL OK]**.

   ![6_5_dynamicmediaprocessimageassets-thumbnailstab](assets/6_5_dynamicmediaprocessimageassets-thumbnailstab.png)

1. Sélectionnez l’étape **[!UICONTROL Miniatures des processus]**, puis sélectionnez l’onglet **[!UICONTROL Miniatures]**. Modifiez la taille de la miniature, si nécessaire, puis sélectionnez **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Les valeurs de l’argument des miniatures de l’étape **[!UICONTROL Miniatures des processus]** doivent correspondre à l’argument des miniatures de l’étape **[!UICONTROL Ressources d’image du processus Dynamic Media]**.

1. Sélectionnez **[!UICONTROL Enregistrer]** pour enregistrer les modifications apportées au workflow.

### Augmentation du nombre de paramètres prédéfinis d’image affichés {#increasing-or-decreasing-the-number-of-image-presets-that-display}

Les paramètres d’image prédéfinis que vous créez sont disponibles sous la forme de rendus dynamiques lorsque vous prévisualisez des ressources. Experience Manager affiche différents rendus dynamiques lors de l’affichage d’un fichier à partir de **[!UICONTROL Affichage des détails > Rendus]**. Vous pouvez augmenter ou diminuer la limite des rendus affichés.

**Pour augmenter ou diminuer le nombre de paramètres prédéfinis d’image affichés :**

1. Accédez à CRXDE Lite ([https://localhost:4502/crx/de](https://localhost:4502/crx/de)).
1. Accédez au nœud de liste des paramètres d’image prédéfinis à l’adresse `/libs/dam/gui/coral/content/commons/sidepanels/imagepresetsdetail/imgagepresetslist`

   ![increase_decreasethenumberofimagepresetsthatdisplay](assets/increase_decreasethenumberofimagepresetsthatdisplay.png)

1. Dans la propriété **[!UICONTROL limit]**, définissez la valeur de votre choix dans la colonne **[!UICONTROL Valeur]** ; par défaut, elle est définie sur 15.
1. Accédez à la source de données des paramètres d’image prédéfinis à l’adresse `/libs/dam/gui/coral/content/commons/sidepanels/imagepresetsdetail/imgagepresetslist/datasource`

   ![chlimage_1-495](assets/chlimage_1-495.png)

1. Dans la propriété de limite, remplacez le nombre par le nombre souhaité, par exemple, `{empty requestPathInfo.selectors[1] ? "20" : requestPathInfo.selectors[1]}`.
1. Sélectionnez **[!UICONTROL Enregistrer tout]**.

### Création de paramètres d’image prédéfinis {#creating-image-presets}

Créez des paramètres d’image prédéfinis afin de pouvoir appliquer les paramètres de manière cohérente sur les images lorsque vous prévisualisez ou publiez.

>[!NOTE]
>
>Si vous utilisez Internet Explorer 9, un paramètre prédéfini nouvellement créé n’apparaît pas immédiatement dans la liste après l’enregistrement. Pour contourner ce problème, désactivez le cache d’Internet Explorer 9.

Si vous avez l’intention de prendre en charge l’ingestion de fichiers AI, PDF et EPS afin de pouvoir générer le rendu dynamique de ces formats de fichiers, passez en revue les informations suivantes avant de créer des paramètres d’image prédéfinis.

Voir [Formats de fichiers Adobe Illustrator (AI), PostScript® (EPS) et PDF](#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats).

Si vous avez l’intention de prendre en charge l’ingestion de fichiers INDD afin de pouvoir générer le rendu dynamique de ce format de fichier, passez en revue les informations suivantes avant de créer des paramètres d’image prédéfinis.

Voir [Format de fichier InDesign (INDD)](#indesign-indd-file-format).

**Pour créer des paramètres d’image prédéfinis :**

1. Dans Experience Manager, sélectionnez le logo Experience Manager pour accéder à la console de navigation globale, puis accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Paramètres d’image prédéfinis]**.
1. Sélectionnez **[!UICONTROL Créer]**.

   ![chlimage_1-496](assets/chlimage_1-496.png)

   >[!NOTE]
   >
   >Pour rendre ce paramètre d’image prédéfini réactif, effacez les valeurs des champs **[!UICONTROL width]** et **[!UICONTROL height]** et laissez-les vides.

1. Dans la fenêtre **[!UICONTROL Modifier le paramètre d’image prédéfini]**, saisissez les valeurs adéquates dans les onglets **[!UICONTROL De base]** et **[!UICONTROL Avancé]**, notamment un nom. Les options sont décrites dans [Options d’image prédéfinies](#image-preset-options). Les paramètres prédéfinis s’affichent dans le volet de gauche et peuvent être utilisés à la volée avec d’autres ressources.

   ![6_5_imagepreset-edit](assets/6_5_imagepreset-edit.png)

1. Sélectionnez **[!UICONTROL Enregistrer]**.

### Création d’un paramètre d’image prédéfini réactif {#creating-a-responsive-image-preset}

Pour créer un paramètre d’image prédéfini réactif, suivez les étapes de la section [Création de paramètres d’image prédéfinis](#creating-image-presets). Lorsque vous saisissez la hauteur et la largeur dans la fenêtre **[!UICONTROL Modifier le paramètre d’image prédéfini]**, effacez les valeurs et laissez-les vides.

Si vous ne les laissez pas vides, cela indique à l’Experience Manager que ce paramètre d’image prédéfini est réactif. Vous pouvez, le cas échéant, ajuster les autres valeurs.

>[!NOTE]
>
>Pour afficher les boutons **[!UICONTROL URL]** et **[!UICONTROL RESS]** lors de l’application d’un paramètre d’image prédéfini à une ressource, la ressource doit être publiée.
>
>![chlimage_1-79](assets/chlimage_1-498.png)
>
>Les paramètres d’image prédéfinis et les ressources images sont automatiquement publiés.

### Options des paramètres prédéfinis d’image {#image-preset-options}

Lorsque vous créez ou modifiez des paramètres d’image prédéfinis, vous disposez des options décrites dans cette section. En outre, Adobe recommande les options suivantes (correspondant aux « bonnes pratiques ») pour commencer :

* **[!UICONTROL Format]** (onglet **[!UICONTROL De base]**) : sélectionnez **[!UICONTROL JPEG]** ou un autre format adapté à vos exigences. Tous les navigateurs web prennent en charge le format d’image JPEG ; il offre un bon compromis entre les petites tailles de fichiers et la qualité de l’image. Cependant, les images au format JPEG utilisent un schéma de compression avec perte qui peut introduire des artefacts d’image indésirables si le paramètre de compression est trop bas. C’est pourquoi Adobe recommande de définir la qualité de compression sur 75. Ce paramètre offre un bon équilibre entre la qualité d’image et la taille de fichier réduite.

* **[!UICONTROL Activer l’accentuation simple]** : ne sélectionnez pas l’option **[!UICONTROL Activer l’accentuation simple]** (ce filtre d’accentuation est moins précis que les paramètres Accentuation).

* **[!UICONTROL Accentuation : Mode Rééchantillonnage]** : sélectionnez l’option **[!UICONTROL Sharp2]**.

#### Options de l’onglet De base {#basic-tab-options}

| Champ | Description |
| --- | --- |
| **Nom** | Entrez un nom descriptif sans espaces. Pour aider les utilisateurs à identifier ce paramètre d’image prédéfini, incluez la spécification de taille d’image dans le nom. |
| **Largeur et hauteur** | Saisissez en pixels la taille à laquelle l’image est diffusée. La largeur et la hauteur doivent être supérieures à 0 pixel. Si l’une des valeurs est 0, aucun paramètre prédéfini n’est créé. Si les deux valeurs sont vides, un paramètre d’image prédéfini réactif est créé. |
| **Format** | Sélectionnez un format dans le menu.<br>Choisir **JPEG** offre les autres options suivantes :<br>• **Qualité** - L’échelle de qualité JPEG s’étend de 1 à 100. L’échelle est visible lorsque vous faites glisser le curseur.<br> ・ **Activer le sous-échantillonnage de la chrominance JPG** - Comme l’oeil est moins sensible aux informations colorimétriques à haute fréquence qu’à la luminance à haute fréquence, les images de JPEG divisent les informations d’image en composantes de luminance et de couleur. Lorsqu’une image de JPEG est compressée, le composant de luminance est conservé à pleine résolution, tandis que les composants de couleur sont sous-échantillonnés en calculant la moyenne entre des groupes de pixels. Le sous-échantillonnage réduit le volume de données à un demi-tiers ou à un tiers avec un impact minimal sur la qualité perçue. Le sous-échantillonnage ne s’applique pas aux images en niveaux de gris. Cette technique permet de réduire le niveau de compression utile pour les images à fort contraste (par exemple, les images avec du texte superposé).<br><br>Choisir **GIF** ou **GIF avec couche alpha** offre les options supplémentaires de **Quantification de couleurs GIF** suivantes :<br>• **Type** : Sélectionnez **Adaptatif** (par défaut), **Web** ou **Macintosh**. Si vous sélectionnez **GIF avec couche alpha**, l’option Macintosh n’est pas disponible.<br>• **Juxtaposition** : sélectionnez **Diffus** ou **Désactivé**.<br>• **Nombre de couleurs** : saisissez un nombre compris entre 2 et 256.<br> ・ **Liste de couleurs** - Entrez une liste séparée par des virgules. Par exemple, pour blanc, gris et noir, saisissez `000000,888888,ffffff`.<br><br>Si vous sélectionnez **PDF**, **TIFF** ou **TIFF avec couche alpha**, cette option supplémentaire est proposée :<br>• **Compression** : Sélectionnez un algorithme de compression. Les options d’algorithme pour le format PDF sont **Aucun**, **Zip** et **Jpeg**. Les options pour le format TIFF sont **Aucun**, **LZW**, **Jpeg** et **Zip**. Les options pour le format TIFF avec couche alpha sont **Aucun**, **LZW** et **Zip**.<br><br>Aucune option supplémentaire n’est fournie si vous sélectionnez **PNG**, **PNG avec couche alpha** ou **EPS**. |
| **Accentuation** | Sélectionnez l’option **Activer l’accentuation simple** pour appliquer un filtre d’accentuation de base à l’image à l’issue des opérations de mise à l’échelle. L’accentuation peut compenser le flou produit lors de l’affichage d’une image à une taille différente. |

#### Options de l’onglet Avancé {#advanced-tab-options}

<table>
 <tbody>
  <tr>
   <td><strong>Champ</strong></td>
   <td><strong>Description</strong></td>
  </tr>
  <tr>
   <td><strong>Espace colorimétrique</strong></td>
   <td>Sélectionnez l’espace colorimétrique <strong>RVB, CMJN</strong> ou <strong>Niveaux de gris</strong>.</td>
  </tr>
  <tr>
   <td><strong>Profil colorimétrique</strong></td>
   <td>Sélectionnez le profil de l’espace colorimétrique de sortie dans lequel vous souhaitez que la ressource soit convertie s’il diffère du profil en cours d’utilisation.</td>
  </tr>
  <tr>
   <td><strong>Intention de rendu</strong></td>
   <td>Vous pouvez remplacer l’intention de rendu par défaut. Les intentions de rendu déterminent ce qui arrive aux couleurs qui ne peuvent pas être reproduites dans le profil colorimétrique cible (hors gamme). L’intention de rendu est ignorée si elle n’est pas compatible avec le profil ICC.
    <ul>
     <li>Sélectionnez <strong>Perception</strong> pour compresser la gamme totale d’un espace colorimétrique dans un autre lorsqu’une ou plusieurs couleurs de l’image d’origine se situent en dehors de la gamme de l’espace colorimétrique de destination.</li>
     <li>Sélectionnez <strong>Colorimétrie relative</strong> lorsqu’une couleur de l’espace colorimétrique actuel se situe hors de la gamme des couleurs dans l’espace cible. Et vous voulez le mapper à la gamme de couleurs la plus proche sans modifier d'autres couleurs. </li>
     <li>Sélectionnez <strong>Saturation</strong> si vous voulez reproduire la saturation des couleurs de l’image d’origine lors de sa conversion dans l’espace colorimétrique cible. </li>
     <li>Sélectionnez <strong>Colorimétrie absolue</strong> pour faire correspondre exactement les couleurs sans aucun ajustement pour le point blanc ou noir qui altérerait la luminosité de l’image.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Compensation du point noir</strong></td>
   <td>Sélectionnez cette option si le profil de sortie prend en charge cette fonctionnalité. La compensation du point noir est ignorée si elle n’est pas compatible avec le profil ICC spécifié.</td>
  </tr>
  <tr>
   <td><strong>Tramage</strong></td>
   <td>Sélectionnez cette option pour éviter ou réduire d’éventuels artefacts de bandes de couleurs. </td>
  </tr>
  <tr>
   <td><strong>Type d’accentuation</strong></td>
   <td><p>Sélectionnez <strong>Aucun</strong>, <strong>Accentuer</strong> ou <strong>Accentuation</strong>. </p>
    <ul>
     <li>Sélectionnez <strong>Aucun</strong> si vous souhaitez désactiver l’accentuation.</li>
     <li>Sélectionnez l’option <strong>Accentuer</strong> pour appliquer un filtre d’accentuation de base à l’image à l’issue des opérations de mise à l’échelle. L’accentuation peut compenser le flou produit lors de l’affichage d’une image à une taille différente. </li>
     <li>Sélectionnez <strong> Accentuation</strong> si vous souhaitez affiner l’effet d’un filtre d’accentuation sur l’image finale à résolution réduite. Vous pouvez contrôler l’intensité de l’effet, son rayon (mesuré en pixels) et un seuil de contraste qui est ignoré. Cet effet utilise les mêmes options que le filtre Photoshop « Accentuation ».</li>
    </ul> <p>L’option <strong>Accentuation</strong> propose les options suivantes :</p>
    <ul>
     <li><strong>Quantité</strong> : contrôle le degré de contraste appliqué aux pixels de contour. La valeur réelle par défaut est de 1,0. Pour les images à haute résolution, vous pouvez l’augmenter jusqu’à 5,0. Envisagez la quantité comme une mesure de l’intensité du filtre.</li>
     <li><strong>Rayon</strong> : détermine le nombre de pixels entourant les pixels de contour qui affectent l’accentuation. Pour les images haute résolution, entrez un nombre réel compris entre 1 et 2. Une valeur faible accentue uniquement les pixels de contour. Une valeur élevée accentue une bande plus large de pixels. La valeur correcte dépend de la taille de l’image.</li>
     <li><strong>Seuil</strong> : détermine la plage de contraste à ignorer lorsque le filtre Accentuation est appliqué. En d’autres termes, cette option définit le degré d’accentuation des pixels qui doit différer de la zone environnante pour être considérée comme des pixels de contour et une accentuation. Pour éviter d’introduire du bruit, essayez des valeurs comprises entre 2 et 20. </li>
     <li><strong>Appliquer à</strong> : détermine si l’accentuation s’applique à chaque couleur ou à la luminosité.</li>
    </ul>
    <div>
      L’accentuation est décrite dans la vidéo
     <a href="https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-image-sharpening-feature-video-use#dynamic-media">Utilisation de l’accentuation des images avec Experience Manager Dynamic Media</a>, dans la rubrique d’aide en ligne <a href="https://experienceleague.adobe.com/en/docs/dynamic-media-classic/using/master-files/sharpening-image#master-files">Accentuation d’une image</a> et dans le fichier téléchargeable au format PDF <a href="https://experienceleague.adobe.com/docs/dynamic-media-classic/assets/s7_sharpening_images.pdf">Bonnes pratiques pour l’accentuation des images dans Dynamic Media Classic</a>.
    </div> </td>
  </tr>
  <tr>
   <td><strong>Mode Rééchantillonnage</strong></td>
   <td>Sélectionnez une option <strong>Mode Rééchantillonnage</strong>. Ces options accentuent l’image lorsque sa résolution est réduite :
    <ul>
     <li><strong>Bilinéaire</strong> : il s’agit de la méthode de rééchantillonnage la plus rapide. Certains artefacts de crénelage sont visibles.</li>
     <li><strong>Bicubique</strong> : accroît l’utilisation du processeur, mais produit des images plus nettes avec des artefacts de crénelage plus discrets.</li>
     <li><strong>Sharp2</strong> : cette méthode peut produire des images légèrement plus nettes que celles obtenues avec l’option Bicubique, en sollicitant toutefois davantage le processeur.</li>
     <li><strong>Bi-Sharp</strong> : permet de sélectionner le rééchantillonneur Photoshop par défaut utilisé pour réduire la taille de l’image ; cette option se nomme <strong>Bicubique plus net</strong> dans Adobe Photoshop.</li>
     <li><strong>Chaque couleur</strong> et <strong>Luminosité</strong> – Chaque méthode peut être basée sur la couleur ou la luminosité. Par défaut, l’option <strong>Chaque couleur</strong> est sélectionnée.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Résolution d’impression</strong></td>
   <td>Choisissez une résolution d’impression pour cette image ; 72 pixels est la valeur par défaut.</td>
  </tr>
  <tr>
   <td><strong>Modificateur d’image</strong></td>
   <td><p>Au-delà des paramètres d’image courants disponibles dans l’IU, Dynamic Media prend en charge de nombreuses modifications d’image avancées que vous pouvez spécifier dans le champ <strong>Modificateurs d’images</strong>. Ces paramètres sont définis dans la <a href="https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/syntax-and-features/image-serving-http/c-command-overview">référence des commandes du protocole de serveur d’images</a>.</p> <p>Important : La fonctionnalité suivante répertoriée dans l’API n’est pas prise en charge :</p>
    <ul>
     <li>Commandes de base de création de modèles et de rendu de texte : <code>text= textAngle= textAttr= textFlowPath= textFlowXPath= textPath=</code> et <code>textPs=</code></li>
     <li>Commandes de localisation : <code>locale=</code> et <code>req=xlate</code></li>
     <li><code>req=set</code> n’est pas disponible pour l’utilisation générale.</li>
     <li><code>req=mbrset</code></li>
     <li><code>req=saveToFile</code></li>
     <li><code>req=targets</code></li>
     <li><code>template=</code></li>
     <li>Services Dynamic Media non essentiels : SVG, rendu d’image et impression en ligne</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

### Définition des options de paramètre d’image prédéfini à l’aide des modificateurs d’image {#defining-image-preset-options-with-image-modifiers}

Outre les options disponibles dans les onglets De base et Avancé, vous pouvez définir des modificateurs d’image pour vous donner plus d’options lors de la définition de paramètres d’image prédéfinis. Le rendu des images repose sur l’API de rendu d’images de Dynamic Media et est défini en détail dans la [Référence du protocole HTTP](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-rendering-api/http-protocol-reference/c-ir-introduction#image-rendering-api).

Vous trouverez ci-dessous des exemples de tâches que vous pouvez exécuter à l’aide des modificateurs d’image.

>[!NOTE]
>
>Certains modificateurs d’image [ne peuvent pas être utilisés dans Experience Manager](#advanced-tab-options).

* [op_invert](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-op-invert) : inverse chaque composant de couleur pour générer un effet d’image négative.

  ```xml {.line-numbers}
  &op_invert=1
  ```

  ![6_5_imagepreset-edit-invert](assets/6_5_imagepreset-edit-invert.png)

* [op_blur](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-op-blur) : applique un effet de flou à l’image.

  ```xml {.line-numbers}
  &op_blur=7
  ```

  ![6_5_imagepreset-edit-blur](assets/6_5_imagepreset-edit-blur.png)

* Commandes combinées : op_blur et op-invert

  ```xml {.line-numbers}
  &op_invert=1&op_blur=7
  ```

  ![chlimage_1-80](assets/chlimage_1-501.png)

* [op_brightness](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-op-brightness) : augmente ou diminue la luminosité.

  ```xml {.line-numbers}
  &op_brightness=58
  ```

  ![6_5_imagepreset-edit-brightness](assets/6_5_imagepreset-edit-brightness.png)

* [opac](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-opac) : permet de régler l’opacité de l’image. Cet attribut vous permet de diminuer l’opacité du premier plan.

  ```xml {.line-numbers}
  opac=29
  ```

  ![6_5_imagepreset-edit-opacity](assets/6_5_imagepreset-edit-opacity.png)

### Modification des paramètres d’image prédéfinis {#modifying-image-presets}

1. Dans Experience Manager, sélectionnez le logo Experience Manager pour accéder à la console de navigation globale, puis accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Paramètres d’image prédéfinis]**.

   ![6_5_imagepreset-editpreset](assets/6_5_imagepreset-editpreset.png)

1. Sélectionnez un paramètre prédéfini, puis **[!UICONTROL Modifier]**. La fenêtre **[!UICONTROL Modifier le paramètre d’image prédéfini]** s’ouvre.
1. Apportez des modifications, puis sélectionnez **[!UICONTROL Enregistrer]** pour les enregistrer ou sur **[!UICONTROL Annuler]** pour les annuler.

### Publication de paramètres d’image prédéfinis {#publishing-image-presets}

Les paramètres d’image prédéfinis sont automatiquement publiés.

### Suppression de paramètres d’image prédéfinis {#deleting-image-presets}

1. Dans Experience Manager, sélectionnez le logo Experience Manager pour accéder à la console de navigation globale, puis sélectionnez l’icône Outils.
1. Accédez à **[!UICONTROL Ressources]** > **[!UICONTROL Paramètres d’image prédéfinis]**.
1. Sélectionnez un paramètre prédéfini, puis sélectionnez **[!UICONTROL Supprimer]**. Dynamic Media vous invite à confirmer la suppression. Sélectionnez **[!UICONTROL Supprimer]** pour supprimer ou sélectionnez **[!UICONTROL Annuler]** pour revenir aux paramètres d’image prédéfinis.
