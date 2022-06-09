---
title: Balises de couleur pour les images
description: Experience Manager Assets permet de distinguer les couleurs d’une image et de les appliquer automatiquement sous forme de balises. Vous pouvez ensuite utiliser ces balises pour rechercher et filtrer des images.
source-git-commit: 74c13efe99b50ba08d9dc38c246de71482a536a0
workflow-type: tm+mt
source-wordcount: '1097'
ht-degree: 12%

---


# Balises de couleur pour les images {#color-tag-images}

![Bannière de balisage colorimétrique](assets/banner-image.png)

Experience Manager Assets utilise les fonctionnalités d’Adobe Sensei AI pour distinguer les couleurs d’une image et les appliquer automatiquement sous forme de balises lors de l’ingestion. Ces balises permettent d’améliorer l’expérience de recherche en fonction de la composition des couleurs de l’image.

Vous pouvez configurer le nombre de couleurs, comprises entre 1 et 4, qui sont balisées vers une image afin de pouvoir rechercher ultérieurement des images en fonction de ces couleurs. Experience Manager Assets applique les balises en fonction de la couverture colorimétrique d’une image. Vous pouvez également configurer le format d’affichage d’une balise de couleur.

>[!NOTE]
>
>Cette fonctionnalité est disponible dans le canal de version préliminaire. Pour plus d’informations sur l’activation de cette fonctionnalité dans votre environnement, consultez la [documentation sur les canaux de version préliminaire](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=fr#enable-prerelease).

La figure suivante illustre l’ordre des tâches que vous effectuez pour configurer et gérer le balisage colorimétrique des images dans Experience Manager Assets :

![Balisage des couleurs](assets/color-tagging-dfd.gif)

## Formats de fichiers pris en charge {#supported-file-formats-color-tags}

| Format de fichier | Extension | Type MIME | Espace colorimétrique d’entrée | Taille maximale de fichier source prise en charge | Résolution maximale de la taille de fichier prise en charge |
|---|---|---|---|---|---|
| JPEG | .jpg, .jpeg | image/jpeg | sRVB | 15 Go | 2 000 px X 2 000 px |
| PNG | .png | image/png | sRVB | 15 Go | 2 000 px X 2 000 px |
| TIFF | .tif, .tiff | image/tiff | sRVB | 4 Go (limitée par les spécifications de format | 2 000 px X 2 000 px |
| PSD | .psd | image/vnd.adobe.photoshop | sRVB | 2 Go (limité par les spécifications de format) | 2 000 px X 2 000 px |
| GIF | .gif | image/gif | sRVB | 15 Go | 2 000 px X 2 000 px |
| BMP | .bmp | image/bmp | sRVB | 4 Go (limité par les spécifications de format) | 2 000 px X 2 000 px |

## Gestion des propriétés de balisage des couleurs {#manage-color-tagging-properties}

Pour gérer les propriétés de balisage des couleurs pour les images :

1. Accédez à **[!UICONTROL Outils > Ressources > Balisage des couleurs]**.

   ![Propriétés du balisage colorimétrique](assets/color-tag-settings.png)

1. Spécifiez le format d’affichage de la balise de couleur dans le **[!UICONTROL Format d’affichage]** champ . Les options possibles incluent le nom de la couleur, le RGB ou le format HEX.

1. Spécifiez le nombre de couleurs à baliser pour les images dans le **[!UICONTROL Limite]** champ . Ces couleurs s’affichent lorsque vous affichez les propriétés d’une image.  Vous pouvez définir un nombre compris entre un et quarante dans ce champ. La valeur par défaut de ce champ est de dix couleurs.

1. Indiquez le pourcentage de couverture colorimétrique minimal pour inclure une balise de couleur dans les résultats de recherche dans la variable **[!UICONTROL Seuil de couverture/de dominance %]** champ . Par exemple, si la couverture de la couleur rouge dans une image est de 10 % et que vous définissez 9 % dans ce champ, l’image est incluse lorsque vous recherchez des images de couleur rouge. Cependant, si la couverture de la couleur rouge dans une image est de 10 % et que vous définissez 11 % dans ce champ, l’image n’est pas incluse lorsque vous recherchez des images de couleur rouge.

   Dans ce champ, vous pouvez indiquer un nombre compris entre cinq et cent. La valeur par défaut est onze.

   >[!NOTE]
   >
   >Adobe recommande d’utiliser une valeur proche de la valeur par défaut dans ce champ. La définition d’une valeur numérique élevée pour ce champ (par exemple, supérieure à 25) peut renvoyer très peu de résultats de recherche. De même, la définition d’une valeur numérique faible (par exemple, inférieure à 6) peut renvoyer un trop grand nombre de résultats de recherche, ce qui peut ne pas être utile.

1. Cliquez sur **[!UICONTROL Enregistrer]**.


   >[!VIDEO](https://video.tv.adobe.com/v/340108)


### Désactiver le balisage des couleurs {#disable-color-tagging}

Le balisage colorimétrique des images est activé par défaut. Vous pouvez désactiver le balisage des couleurs au niveau du dossier. Tous les dossiers enfants héritent des propriétés de balisage des couleurs du dossier parent.

Pour désactiver le balisage des couleurs au niveau du dossier :

1. Accédez à **[!UICONTROL Adobe Experience Manager > Ressources > Fichiers]**.

1. Sélectionnez le dossier et cliquez sur **[!UICONTROL Propriétés]**.

1. Dans le **[!UICONTROL Traitement des ressources]** , accédez à la **[!UICONTROL Balises de couleur pour les images]** dossier. Sélectionnez l’une des valeurs suivantes dans la liste déroulante :

   * Hérité : le dossier hérite des options d’activation ou de désactivation du dossier parent.

   * Activer : active le balisage colorimétrique pour le dossier sélectionné.

   * Désactiver : désactive le balisage colorimétrique pour le dossier sélectionné.

   ![Paramètres de balisage des couleurs](assets/color-tags-folder.png)

## Configuration du schéma de métadonnées pour ajouter le composant Balises de couleur intelligente {#configure-metadata-schema}

Les schémas de métadonnées contiennent des champs spécifiques pour des informations spécifiques à renseigner. Il contient également des informations de mise en page pour afficher les champs de métadonnées de manière conviviale. Les propriétés de métadonnées incluent le titre, la description, les types MIME, les balises, etc. Vous pouvez utiliser l’éditeur de [!UICONTROL formulaires de schéma de métadonnées] pour modifier des schémas existants ou ajouter des schémas de métadonnées personnalisés.

>[!NOTE]
>
>Le champ Balise de couleur intelligente est disponible dans le schéma de métadonnées par défaut. Si vous utilisez un schéma de métadonnées personnalisé, configurez votre schéma pour ajouter un champ de balise de couleur intelligente.

Pour ajouter le composant Balises de couleur intelligente à l’éditeur de formulaire de schéma de métadonnées :

1. Accédez à **[!UICONTROL Outils > Ressources > Schémas de métadonnées]**.

1. Sélectionnez le nom du schéma et cliquez sur **[!UICONTROL Modifier]**.

1. Faire glisser **[!UICONTROL Balises de couleur intelligente]** de la **[!UICONTROL Créer un formulaire]** à l’onglet **[!UICONTROL Éditeur de formulaire de schéma de métadonnées]**.

1. Cliquez sur le bouton **[!UICONTROL Champ de balise de couleur intelligente]** dans le **[!UICONTROL Éditeur de formulaire de schéma de métadonnées]**.

1. Spécifiez une valeur appropriée dans la variable **[!UICONTROL Libellé du champ]** dans le champ **[!UICONTROL Paramètres]**  .

1. Cliquez sur **[!UICONTROL Enregistrer]**.

   >[!VIDEO](https://video.tv.adobe.com/v/340124)


## Affichage des balises de couleur intelligente pour les images {#view-color-tags}

Pour afficher les balises de couleur intelligente pour les images :

1. Accédez à **[!UICONTROL Adobe Experience Manager > Ressources > Fichiers]**.

1. Cliquez sur le dossier approprié et sélectionnez l’image.

1. Sélectionner **[!UICONTROL Propriétés]** et affichez les balises dans le **[!UICONTROL Balises de couleur intelligente]** champ .

   ![Affichage des balises de couleur](assets/view-color-tags.png)

   Pointez la souris sur une balise de couleur pour afficher **[!UICONTROL Seuil de couverture/de dominance %]** d’une couleur dans une image.

## Configuration du prédicat de couleur AEM Assets {#configure-search-predicate}

Vous pouvez configurer le filtre de recherche des images. Vous pouvez ensuite baser vos critères de recherche sur une couleur spécifique pour filtrer les résultats.

>[!NOTE]
>
>Configurez le prédicat de couleur AEM Assets uniquement si vous n’utilisez pas le formulaire de recherche par défaut.

Pour configurer le filtre de recherche, créez un prédicat de couleur de ressource à l’aide du rail de recherche d’administrateurs de ressources.

Pour configurer le filtre de recherche, procédez comme suit :

1. Accédez à **[!UICONTROL Outils > Général > Rechercher dans Forms]**.

1. Sélectionner **[!UICONTROL Rail de recherche d’administrateurs de ressources]** et cliquez sur **[!UICONTROL Modifier]**.

1. Faire glisser **[!UICONTROL Prédicat de couleur de la ressource]** de la **[!UICONTROL Sélectionner un prédicat]** à l’onglet **[!UICONTROL Éditeur de formulaire de recherche]**.

1. Spécifiez une valeur appropriée dans la variable **[!UICONTROL Libellé du champ]** dans le champ **[!UICONTROL Paramètres]**  .

1. Pour enregistrer les paramètres, cliquez sur **[!UICONTROL Terminé]**.

   >[!VIDEO](https://video.tv.adobe.com/v/340110)

## Recherche d’images en fonction des couleurs {#search-images-based-on-colors}

>[!VIDEO](https://video.tv.adobe.com/v/340761)

Après avoir configuré toutes les propriétés de balisage des couleurs et [configuration du prédicat colorimétrique Assets](#search-images-based-on-colors), vous pouvez rechercher des images en fonction d’une couleur comme filtre.

Pour rechercher des images en fonction des couleurs :

1. Accédez à **[!UICONTROL Ressources > Fichiers]**.

1. Sélectionner **[!UICONTROL Filtrer]** dans la liste déroulante.
   ![Filtrage des ressources](assets/filter-assets.png)

1. Sélectionnez la [Prédicat de couleur AEM Assets](#configure-search-predicate).

1. Faites glisser le sélecteur de couleurs pour sélectionner la couleur appropriée. La couleur sélectionnée s’affiche dans le champ en lecture seule disponible sous le sélecteur de couleurs. Vous pouvez sélectionner RGB ou HEX comme format d’affichage de la couleur.

   ![Sélecteur de couleurs](assets/color-picker-color-tags.png)

   Vous pouvez filtrer les images en fonction de la sélection d’une couleur. Les images dont la couleur sélectionnée fait partie des balises de couleur intelligente et au-dessus de la balise [Couverture/seuil de dominance %](#manage-color-tagging-settings) s’affiche dans le volet de droite.

1. Cliquez sur x dans la barre de recherche pour effacer le filtre.




