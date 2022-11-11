---
title: Gestion des documents PDF dans [!DNL Adobe Experience Manager].
description: Gestion des documents PDF dans [!DNL Adobe Experience Manager] as a [!DNL Cloud Service].
feature: Asset Management
role: User,Admin
source-git-commit: 9a600fb744c7064274fb4d849a5e01de2b83f575
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 0%

---

# Gestion des documents de PDF dans Experience Manager Assets as a Cloud Service {#add-assets-to-experience-manager}

Experience Manager Assets s’intègre de manière transparente à la visionneuse Document Cloud PDF, ce qui vous permet de prévisualiser plusieurs pages d’un document PDF. En outre, vous pouvez également utiliser des fonctionnalités de visionneuse de PDF de Document Cloud avancées telles que les annotations, la recherche de texte, la navigation dans le document du PDF à l’aide de signets et de miniatures, et bien plus sous le même toit. Experience Manager Assets vous permet également de charger des documents dans d’autres formats pris en charge et de les prévisualiser dans un format PDF.

La visionneuse de PDF de Document Cloud bénéficie à AEM Assets de différentes manières :
* [Prise en charge des composants de la visionneuse de Documents Cloud de PDF](#pdf-doc-cloud)
* [Prise en charge de l’aperçu de plusieurs pages et des annotations pour les ressources du PDF](#multi-page)
* [Prise en charge de l’aperçu de plusieurs pages pour les documents dans d’autres formats](#multi-format)

> Conseil
> Si vous ne parvenez pas à obtenir l’aperçu de plusieurs pages d’un document de PDF précédemment téléchargé, sélectionnez le PDF et cliquez sur **![Retraiter](/help/assets/assets/Reprocess.svg) Retraiter les ressources**.

## Prise en charge des composants de la visionneuse de Documents Cloud de PDF {#pdf-doc-cloud}

La visionneuse Doc Cloud du PDF natif comporte les composants suivants dans AEM Assets :

* **Visionneuse de PDF à l’aide de miniatures de page** Le mode Miniature est un petit aperçu des pages d’un document de PDF. Les miniatures vous permettent d’accéder directement à la page souhaitée. Vous pouvez accéder aux miniatures du document de PDF sélectionné via ![thumbnail](/help/assets/assets/thumbnail.svg) dans le volet de gauche.

* **Visionneuse de PDF utilisant des signets** Le signet est un lien direct qui vous permet d’accéder au contenu du document. Vous pouvez accéder aux signets du document de PDF sélectionné via ![signet](/help/assets/assets/bookmark.svg) dans le volet de gauche.

* **Recherche dans le PDF** Vous pouvez utiliser la recherche ![search](/help/assets/assets/Search.svg) pour rechercher le texte dans le document du PDF.

* **Monter/descendre de page** Utiliser la page vers le haut ![Page précédente](/help/assets/assets/ArrowUp.svg) ou Page suivante ![Page suivante](/help/assets/assets/ArrowDown.svg) pour faire défiler le document.

* **Zoom arrière/Zoom avant** Utiliser le zoom arrière ![Zoom arrière](/help/assets/assets/ZoomOut.svg) ou Zoom avant ![Zoom avant](/help/assets/assets/ZoomIn.svg) pour diffuser le document.

* **Page Ajustée** Utilisez les dimensions de largeur ou de hauteur pour adapter le document à la taille de votre écran.

* **Dock/Undock PDF** Vous pouvez ancrer ou détacher les composants de la visionneuse de PDF native à l’aide de cette option.

## Prise en charge de l’aperçu de plusieurs pages et des annotations pour les ressources du PDF {#multi-page}

Adobe Experience Manager Assets vous permet de prévisualiser un document de PDF constitué de plusieurs pages. Pour prévisualiser plusieurs pages d’un document de PDF, tenez compte des étapes suivantes :

1. Suivez les étapes pour [chargement de ressources dans AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/add-assets.html?lang=en).
1. Parcourez le document du PDF que vous souhaitez charger et prévisualiser.
1. Ouvrez le document.
1. La visionneuse de documents du PDF se charge par défaut. Vous pouvez également sélectionner Rendu du PDF sous le panneau Rendu .
1. Sous la liste déroulante Rendus , sélectionnez **Tous les rendus**.

Vous pouvez également appliquer des [annotations](#pdf-annotations) au document PDF dans un aperçu de plusieurs pages.

> REMARQUE
> La taille maximale d’une ressource que vous pouvez prévisualiser est de 100 Mo.

>[!VIDEO](https://video.tv.adobe.com/v/3409355)

<!--
![Multi-page Preview](/help/assets/assets/multi-page.png)
-->

**Annotations PDF{#pdf-annotations}**

Experience Manager Assets vous permet d’ajouter des commentaires à un document de PDF. Un document de PDF peut comporter plusieurs annotations.

Pour annoter un document PDF, procédez comme suit :
1. Accédez à l’interface Assets, puis au document du PDF que vous souhaitez annoter. La visionneuse de PDF native s’ouvre à droite et affiche l’aperçu du document de PDF sélectionné.
1. Cliquez sur **Annoter** dans le menu supérieur.
Vous trouverez ci-dessous les annotations qui peuvent être appliquées à un document de PDF :

<table>
        <tr>
             <th> Annotation </th>
            <th> Description </th>
        </tr>
        <tr>
           <td> <img src="/help/assets/assets/Comment.svg"> Commentaire </td>
            <td> Sélectionnez Commentaire pour exprimer une observation. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/Text.svg"> Textbox </td>
            <td> Sélectionnez Zone de texte pour saisir le texte. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/Note.svg"> Remarques persistantes </td>
            <td> Ajoutez un petit texte ou un rappel que vous pouvez ajouter à une zone spécifique du PDF. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/Comment.svg"> Surligneur de texte </td>
            <td> Sélectionnez le texte à mettre en surbrillance dans différentes couleurs. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/TextUnderline.svg"> Texte souligné </td>
            <td> Sélectionnez le texte à souligner. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/TextStrikethrough.svg"> Barré </td>
            <td> Sélectionnez le texte que vous souhaitez barrer. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/Draw.svg"> Dessin </td>
            <td> Insérez une illustration visuelle dans le PDF. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/Erase.svg"> Effacer le dessin </td>
             <td> Supprimez ou annulez le dessin. </td>
        </tr>
    </table>

## Prise en charge de l’aperçu de plusieurs pages pour les documents dans d’autres formats {#multi-format}

Outre les documents du PDF, vous pouvez également prévisualiser plusieurs pages pour les documents de types différents. Les types de format de document pris en charge sont TXT, RTF, DOC, DOCX, PPT, PPTX, XLS et XLSX. Experience Manager Assets convertit automatiquement ces formats de document dans un format de PDF et les rend disponibles pour la prévisualisation.

![Aperçu multi-page de documents dans d’autres formats](/help/assets/assets/multi-page-other-formats.png)

Pour l’aperçu de plusieurs pages dans d’autres formats de document pris en charge, procédez comme suit :
1. Suivez les étapes pour [chargement de ressources dans AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/add-assets.html?lang=en).
1. Parcourez le document que vous souhaitez charger et prévisualiser.
1. Ouvrez le document.
1. Sélectionnez PDF sous la section statique dans le panneau de gauche. Le panneau de droite affiche l’aperçu de plusieurs pages d’une ressource. Sélectionnez une miniature dans le panneau de gauche pour choisir la page à prévisualiser.

> REMARQUE
> * La taille maximale d’une ressource que vous pouvez prévisualiser est de 100 Mo.
> * La taille maximale des fichiers XLS ou XLSX à prévisualiser est de 20 Mo.
> 

