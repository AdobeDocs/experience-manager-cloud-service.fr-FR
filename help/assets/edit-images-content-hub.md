---
title: Modification d’images dans Content Hub à l’aide d’Adobe Express
description: Modification d’images dans Content Hub à l’aide d’Adobe Express
exl-id: c9777862-226c-4d39-87da-9c4a30437dc5
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 18%

---

# Modification d’images dans Content Hub {#edit-images-content-hub}

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

![Modification d’images dans Content Hub à l’aide d’Adobe Express](assets/edit-images-content-hub.png)

>[!AVAILABILITY]
>
>Le guide de Content Hub est désormais disponible au format PDF. Téléchargez l’intégralité du guide et utilisez l’assistant IA Adobe Acrobat pour répondre à vos requêtes.
>
>[!BADGE Guide PDF de Content Hub]{type=Informative url="https://helpx.adobe.com/content/dam/help/fr/experience-manager/aem-assets/content-hub.pdf"}

Content Hub vous permet de créer du contenu avec Adobe Express. Vous pouvez modifier du contenu existant à l’aide d’outils simples d’utilisation, produire des variations de marque avec des modèles et des éléments de marque et créer du contenu avec les dernières fonctionnalités GenAI d’Adobe Firefly.

## Prérequis {#prereqs-edit-image-content-hub}

Les utilisateurs Adobe Express et [Content Hub autorisés à remixer les ressources vers de nouvelles variations](/help/assets/deploy-content-hub.md#onboard-content-hub-users-remix-assets) peuvent modifier les images à l’aide de Content Hub.

>[!NOTE]
>
>Vous pouvez modifier des images de types de fichiers PNG et JPG/JPEG à l’aide de [!DNL Adobe Express].

## Modifier des images à l’aide d’[!DNL Adobe Express] {#edit-images-using-content-hub}

Pour modifier des images à l’aide de Content Hub :

1. Cliquez sur **[!DNL Open in Adobe Express]** disponible sur la carte de l’image à modifier. Vous pouvez également cliquer sur l’image pour en afficher les détails, puis cliquer sur le logo [!DNL Adobe Express]. L’éditeur incorporé pour Adobe Express se charge ensuite sans jamais quitter Content Hub.

   Vous pouvez tirer parti de la fonctionnalité [!DNL Adobe Express] pour effectuer toutes les actions liées à la modification d’images, telles que [redimensionner l’image](https://helpx.adobe.com/express/using/resize-image.html), [supprimer ou modifier la couleur d’arrière-plan](https://helpx.adobe.com/express/using/remove-background.html), [recadrer l’image](https://helpx.adobe.com/express/using/crop-image.html), combiner l’image à une image ou un texte généré par l’IA, etc.

1. Effectuez vos modifications et cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer la ressource modifiée dans l’un des formats suivants :

   * **[!UICONTROL PNG]** (utilisé comme format d’image de bonne qualité)
   * **[!UICONTROL JPG]** (adapté aux petits fichiers)
   * **[!UICONTROL PDF]** (adapté aux documents)

   ![Enregistrement d’image avec Adobe Express.](assets/adobe-express-save-as.png)

1. Nommez la ressource dans le champ **[!UICONTROL Enregistrer sous]**.

1. Indiquez le nom de la campagne de votre ressource à l’aide du champ **[!UICONTROL Nom de la campagne]**. Vous pouvez utiliser un nom existant ou en créer un nouveau. Le Content Hub vous offre davantage d’options au fur et à mesure que vous saisissez le nom. <!--You can define multiple Campaign names for your upload. While you are typing a name, either click anywhere else within the dialog box or press the `,` (Comma) key to register the name.-->

   Adobe recommande, en règle générale, de spécifier des valeurs dans le reste des champs afin de créer une expérience de recherche améliorée pour les ressources que vous avez chargées.

1. [Facultatif] Définissez des valeurs pour les champs **[!UICONTROL Mots-clés]**, **[!UICONTROL Canaux]**, **[!UICONTROL Période]** et **[!UICONTROL Région]**. Le balisage et le regroupement des ressources par mots-clés, canaux et emplacement permet à toutes les personnes qui utilisent le contenu approuvé de votre entreprise de trouver ces ressources et de les organiser.

1. Cliquez sur **[!UICONTROL Enregistrer en tant que nouvelle ressource]** pour enregistrer la ressource.

Les administrateurs peuvent également configurer les champs obligatoires et facultatifs qui s’affichent lors de l’ajout de ressources à Content Hub, tels que le nom de la campagne, les mots-clés, les canaux, etc. Pour plus d’informations, voir [Configuration de l’interface utilisateur de Content Hub](configure-content-hub-ui-options.md#configure-upload-options-content-hub).
