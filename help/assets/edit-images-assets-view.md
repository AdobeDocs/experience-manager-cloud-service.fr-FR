---
title: Modification des images
description: Modifiez les images à l’aide des options optimisées d’ [!DNL Adobe Photoshop Express] et enregistrez les images mises à jour sous forme de versions.
role: User
exl-id: fc21a6ee-bf23-4dbf-86b0-74695a315b2a
source-git-commit: 30b8c9b8eaee6292323dde4b436c29fe8290c910
workflow-type: tm+mt
source-wordcount: '896'
ht-degree: 94%

---

# Modifier des images dans [!DNL Assets view] {#edit-images}

[!DNL Assets view] fournit des options de modification conviviales, optimisées par [!DNL Adobe Express] et [!DNL Adobe Photoshop Express]. Les actions de modification disponibles à l’aide d’[!DNL Adobe Express] sont Redimensionner l’image, Supprimer l’arrière-plan, Recadrer l’image et Convertir le JPEG en PNG.

Après avoir modifié une image, vous pouvez enregistrer la nouvelle image en tant que nouvelle version de cette image. Le contrôle de version vous permet de revenir ultérieurement à la ressource d’origine, si nécessaire. Pour modifier une image, [ouvez son aperçu](/help/assets/navigate-assets-view.md) et cliquez sur **[!UICONTROL Modifier l’image]**.

>[!NOTE]
>
>Vous pouvez modifier les images des types de fichiers PNG et JPEG à l’aide d’[!DNL Adobe Express].

<!--The editing actions that are available are Spot healing, Crop and straighten, Resize image, and Adjust image.-->

## Modifier des images à l’aide d’Adobe Express {#edit-using-express}

>[!CONTEXTUALHELP]
>id="assets_express_integration"
>title="Intégration d’Adobe Express"
>abstract="Des outils simples et intuitifs d’édition d’images optimisés par Adobe Express sont disponibles directement dans AEM Assets pour augmenter la réutilisation du contenu et accélérer sa vitesse de diffusion."

### Redimensionnement de l’image {#resize-image-using-express}

Le redimensionnement d’une image à une taille spécifique est un cas d’utilisation courant. [!DNL Assets view] permet de redimensionner rapidement l’image pour l’adapter aux tailles de photo courantes en fournissant de nouvelles résolutions précalculées pour des tailles de photo spécifiques. Pour redimensionner l’image à l’aide d’[!DNL Assets view], procédez comme suit :

1. Sélectionnez une image, puis cliquez sur **Modifier**.
2. Cliquez sur **[!DNL Resize Image]** dans les actions rapides disponibles dans le volet de gauche.
3. Sélectionnez la plateforme de médias sociaux appropriée dans la liste déroulante **[!UICONTROL Redimensionner pour]** et sélectionnez la taille de l’image parmi les options qui s’affichent.
4. Mettez l’image à l’échelle, le cas échéant, à l’aide du champ **[!UICONTROL Échelle d’image]**.
5. Cliquez sur **[!DNL Apply]** pour appliquer vos modifications.
   ![Modification d’images avec Adobe Express.](assets/adobe-express-resize-image.png)

   Votre image modifiée peut être téléchargée. Vous pouvez enregistrer la ressource modifiée en tant que nouvelle version de la même ressource ou l’enregistrer en tant que nouvelle ressource.
   ![Enregistrement d’image avec Adobe Express.](assets/adobe-express-resize-save.png)

### Supprimer l’arrière-plan {#remove-background-using-express}

Vous pouvez supprimer l’arrière-plan d’une image en quelques étapes simples, comme indiqué ci-dessous :

1. Sélectionnez une image, puis cliquez sur **Modifier**.
2. Cliquez sur **[!DNL Remove Background]** dans les actions rapides disponibles dans le volet de gauche. Experience Manager Assets affiche l’image sans arrière-plan.
3. Cliquez sur **[!DNL Apply]** pour appliquer vos modifications.
   ![Enregistrement d’image avec Adobe Express.](assets/adobe-express-remove-background.png)

   Votre image modifiée peut être téléchargée. Vous pouvez enregistrer la ressource modifiée en tant que nouvelle version de la même ressource ou l’enregistrer en tant que nouvelle ressource.

### Recadrer l’image {#crop-image-using-express}

La transformation d’une image en taille parfaite est facile à l’aide des actions rapides d’[!DNL Adobe Express] intégrées.

1. Sélectionnez une image, puis cliquez sur **Modifier**.
2. Cliquez sur **[!DNL Crop Image]** dans les actions rapides disponibles dans le volet de gauche.
3. Faites glisser les poignées sur les coins de l’image pour créer le recadrage souhaité.
4. Cliquez sur **[!DNL Apply]**.
   ![Enregistrement d’image avec Adobe Express.](assets/adobe-express-crop-image.png)
L’image recadrée peut être téléchargée. Vous pouvez enregistrer la ressource modifiée en tant que nouvelle version de la même ressource ou l’enregistrer en tant que nouvelle ressource.

### Convertir le JPEG en PNG {#convert-jpeg-to-png-using-express}

Vous pouvez rapidement convertir une image JPEG au format PNG à l’aide d’Adobe Express. Procédez comme suit :

1. Sélectionnez une image, puis cliquez sur **Modifier**.
2. Cliquez sur **[!DNL JPEG to PNG]** dans les actions rapides disponibles dans le volet de gauche.
   ![Conversion d’un PNG avec Adobe Express.](assets/adobe-express-convert-image.png)
3. Cliquez sur **[!UICONTROL Télécharger]**.

### Limites {#limitations-adobe-express}

* Résolution d’image prise en charge : minimum de 50 pixels, maximum de 6 000 pixels par dimension

* Taille de fichier maximale : 17 Mo

## Modifier des images à l’aide d’[!DNL Adobe Photoshop Express] {#edit-using-photoshop-express}

<!--
After editing an image, you can save the new image as a new version. Versioning helps you to revert to the original asset later, if needed. To edit an image, [open its preview](//help/navigate-assets-view.md#preview-assets) and click **[!UICONTROL Edit Image]** ![edit icon](assets/do-not-localize/edit-icon.png) from the rail on the right.

![Options to edit an image](assets/edit-image2.png)

*Figure: The options to edit images are powered by [!DNL Adobe Photoshop Express].*
-->

### Supprimer les imperfections des images {#spot-heal-images-using-photoshop-express}

S’il existe des petites taches ou des éléments indésirables mineurs sur une image, vous pouvez modifier et supprimer ces zones grâce à la fonction de suppression des imperfections fournie par Adobe Photoshop.

Le pinceau échantillonne la zone retouchée et fait en sorte que les pixels réparés se fondent de manière transparente dans le reste de l’image. Utilisez une taille de pinceau légèrement supérieure à celle de la zone à corriger.

![Option de modification de suppression des imperfections](assets/edit-spot-healing.png)

<!-- 
TBD: See if we should give backlinks to PS docs for these concepts.
For more information about how Spot Healing works in Photoshop, see [retouching and repairing photos](https://helpx.adobe.com/photoshop/using/retouching-repairing-images.html). 
-->

### Recadrer et redresser des images {#crop-straighten-images-using-photoshop-express}

Grâce à l’option de recadrage et de redressement des images, vous pouvez effectuer un recadrage de base, faire pivoter l’image, la retourner horizontalement ou verticalement, puis la recadrer selon les dimensions les plus adaptées pour les sites web des réseaux de médias sociaux les plus populaires.

Pour enregistrer vos modifications, cliquez sur **[!UICONTROL Recadrer l’image]**. Après modification, vous pouvez enregistrer la nouvelle image dans une nouvelle version.

![Option de recadrage et de redressement](assets/edit-crop-straighten.png)

De nombreuses options par défaut vous permettent de recadrer votre image selon les proportions qui conviennent le mieux aux différents profils et publications de médias sociaux.

### Redimensionnement de l’image {#resize-image-using-photoshop-express}

Vous pouvez afficher en centimètres ou pouces les tailles de photo courantes pour en connaître les dimensions. Par défaut, la méthode de redimensionnement conserve les proportions de l’image. Pour modifier manuellement les proportions, cliquez sur ![](assets/do-not-localize/lock-closed-icon.png).

Saisissez les dimensions et cliquez sur **[!UICONTROL Redimensionner l’image]** pour la redimensionner. Avant d’enregistrer les modifications dans une nouvelle version, vous pouvez annuler toutes les modifications effectuées avant de les enregistrer en cliquant sur [!UICONTROL Annuler] ou modifier une étape du processus de modification en particulier en cliquant sur [!UICONTROL Rétablir].

![Options de redimensionnement d’une image](assets/resize-image.png)

### Modifier l’image {#adjust-image-using-photoshop-express}

[!DNL Assets view] permet d’ajuster en autres la couleur, le ton et le contraste d’une image, en quelques clics seulement. Cliquez sur **[!UICONTROL Ajuster l’image]** dans la fenêtre d’édition. Les options suivantes sont disponibles dans la barre latérale droite :

* **Populaires** : [!UICONTROL Accentuation du contraste et des détails], [!UICONTROL Désaturation du contraste], [!UICONTROL Vieillissement de la photo], [!UICONTROL Noir et blanc doux] et [!UICONTROL Noir et blanc sépia].
* **Couleur** : [!UICONTROL Naturel], [!UICONTROL Brillant], [!UICONTROL Contraste élevé], [!UICONTROL Contraste et détails élevés], [!UICONTROL Satiné] et [!UICONTROL Mat].
* **Création** : [!UICONTROL Contraste désaturé], [!UICONTROL Lumière froide], [!UICONTROL Turquoise et rouge], [!UICONTROL Brume légère], [!UICONTROL Effet vintage], [!UICONTROL Contraste chaud], [!UICONTROL Plat et vert], [!UICONTROL Touche de rouge mat], [!UICONTROL Ombré chaud] et [!UICONTROL Photo vieillie].
* **Noir et blanc** : [!UICONTROL Noir et blanc Paysage], [!UICONTROL Noir et blanc Contraste saturé], [!UICONTROL Noir et blanc punchy], [!UICONTROL Noir et blanc Contraste désaturé], [!UICONTROL Noir et blanc plat], [!UICONTROL Noir et blanc doux], [!UICONTROL Noir et blanc infrarouge], [!UICONTROL Noir et blanc effet sélénium], [!UICONTROL Noir et blanc effet sépia] et [!UICONTROL Noir et blanc en désaturation partielle].
* **Vignettage** : [!UICONTROL Désactivé], [!UICONTROL Léger], [!UICONTROL Moyen] et [!UICONTROL Appuyé].

![Réglage de l’image au travers des différentes modifications](assets/adjust-image.png)

<!--
TBD: Insert a video of the available social media options.
-->

### Étapes suivantes {#next-steps}

* Faites des commentaires sur le produit en utilisant l’option [!UICONTROL Commentaires] disponible dans l’interface utilisateur de la vue Assets

* Faites des commentaires sur la documentation en utilisant l’option [!UICONTROL Modifier cette page] ![modifier la page](assets/do-not-localize/edit-page.png) ou [!UICONTROL Enregistrer un problème] ![créer un problème GitHub](assets/do-not-localize/github-issue.png) disponible dans la barre latérale droite.

* Contactez l’[assistance clientèle](https://experienceleague.adobe.com/?support-solution=General&amp;lang=fr#support).

>[!MORELIKETHIS]
>
>* [Affichage de l’historique des versions d’une ressource](/help/assets/navigate-assets-view.md)
