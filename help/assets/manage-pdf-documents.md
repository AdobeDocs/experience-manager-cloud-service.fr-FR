---
title: Effectuez la gestion de vos documents PDF dans [!DNL Adobe Experience Manager].
description: Effectuez la gestion de vos documents PDF dans [!DNL Adobe Experience Manager] as a [!DNL Cloud Service].
feature: Asset Management
role: User, Admin
exl-id: 29660869-6902-4093-845b-cd629be59d4d
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '835'
ht-degree: 85%

---

# Gérer les documents PDF dans Experience Manager Assets as a Cloud Service {#add-assets-to-experience-manager}

Experience Manager Assets s’intègre de manière transparente à la visionneuse Document Cloud PDF, qui vous permet de prévisualiser plusieurs pages d’un document PDF. En outre, vous pouvez également utiliser les fonctionnalités avancées de la visionneuse de fichiers PDF Document Cloud, telles que les annotations, la recherche de texte, la navigation dans le document PDF à l’aide de signets et de miniatures et bien plus encore sans quitter l’application. Experience Manager Assets vous permet également de télécharger des documents dans d’autres formats pris en charge et de les prévisualiser au format PDF.

L’intégration d’AEM Assets à la visionneuse PDF Document Cloud offre les avantages suivants :

* [Prise en charge des composants de la visionneuse PDF Document Cloud](#pdf-doc-cloud)
* [Prise en charge de la prévisualisation de plusieurs pages et des annotations pour la ressource PDF](#multi-page)
* [Prise en charge de la prévisualisation de plusieurs pages pour les documents dans d’autres formats](#multi-format)

>[!TIP]
>
> Si vous ne parvenez pas à obtenir la prévisualisation de plusieurs pages d’un document PDF précédemment téléchargé, sélectionnez le PDF et cliquez sur ![Retraiter](/help/assets/assets/Reprocess.svg) **Retraiter Assets**.

## Prise en charge des composants de la visionneuse PDF Document Cloud {#pdf-doc-cloud}

La visionneuse PDF native Document Cloud possède les composants suivants dans AEM Assets :

* **Visionneuse PDF à l’aide de miniatures de page** : la vue Miniature fournit une prévisualisation des pages d’un document PDF dans un format réduit. Les miniatures vous permettent d’accéder directement à la page souhaitée. Vous pouvez accéder aux miniatures du document PDF sélectionné via l’icône ![miniature](/help/assets/assets/thumbnail.svg) dans le volet gauche.

* **Visionneuse PDF à l’aide de signets** : le signet consiste en un lien direct vers une section du document. Vous pouvez accéder aux signets du document PDF sélectionné via l’icône ![signet](/help/assets/assets/bookmark.svg) dans le volet gauche.

* **Recherche dans le PDF** : l’icône de recherche ![recherche](/help/assets/assets/Search.svg) vous permet de rechercher du texte dans le document PDF.

* **Page précédente/Page suivante** : utilisez l’icône de page précédente ![Page précédente](/help/assets/assets/ArrowUp.svg) ou de page suivante ![Page suivante](/help/assets/assets/ArrowDown.svg) pour faire défiler le document.

* **Zoom arrière/Zoom avant** : utilisez le zoom arrière ![Zoom arrière](/help/assets/assets/Zoom-out.svg) ou Zoom avant ![Zoom avant](/help/assets/assets/zoom-in.svg) pour atteindre la section souhaitée du document.

* **Page entière**: utilisez les dimensions de largeur ou de hauteur pour adapter le document à la taille de votre écran.

* **Ancrer/détacher le document PDF** : cette option vous pernet d’ancrer ou de détacher les composants de la visionneuse PDF native.

## Prise en charge de la prévisualisation de plusieurs pages et des annotations pour la ressource PDF {#multi-page}

Adobe Experience Manager Assets permet de prévisualiser un document PDF composé de plusieurs pages. Pour prévisualiser plusieurs pages d’un document PDF, procédez comme suit :

1. Suivez la procédure afin de [télécharger des ressources dans AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/add-assets.html?lang=fr).
1. Accédez au document PDF que vous souhaitez télécharger et prévisualiser.
1. Ouvrez le document.
1. La visionneuse de documents PDF se charge par défaut. Vous pouvez également sélectionner Rendu PDF dans le panneau Rendu.
1. Dans la liste déroulante Rendus, sélectionnez **Tous les rendus**.

Vous pouvez également ajouter des [annotations](#pdf-annotations) au document PDF lors d’une prévisualisation de plusieurs pages.

>[!NOTE]
>
> La taille maximale d’une ressource prévisualisable est de 100 Mo.

>[!VIDEO](https://video.tv.adobe.com/v/3409355)

<!--
![Multi-page Preview](/help/assets/assets/multi-page.png)
-->

**Annotations PDF{#pdf-annotations}**

Experience Manager Assets permet d’ajouter des commentaires à un document PDF. Un document PDF peut comporter plusieurs annotations.

Pour annoter un document PDF, procédez comme suit :

1. Accédez à l’interface d’Assets, puis sélectionnez le document PDF à annoter. La visionneuse PDF native s’ouvre à droite et affiche une prévisualisation du document PDF sélectionné.
1. Cliquez sur **Annoter** dans le menu supérieur.
Les documents PDF prennent en charge les annotations suivantes :

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
            <td> <img src="/help/assets/assets/Text.svg"> Zone de texte </td>
            <td> Sélectionnez Zone de texte pour saisir le texte. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/Note.svg"> Notes autocollantes </td>
            <td> Ajoutez un petit texte ou un rappel à une section spécifique du PDF. </td>
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
            <td> Sélectionnez le texte à barrer. </td>
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

>[!NOTE]
>
>Les annotations que vous ajoutez au document PDF sont disponibles en mode Aperçu. Toutefois, les annotations ne s’affichent pas lorsque vous téléchargez ou imprimez le document PDF.

## Prise en charge de la prévisualisation de plusieurs pages pour les documents dans d’autres formats {#multi-format}

Outre les documents au format PDF, vous pouvez également prévisualiser plusieurs pages de documents dans d’autres formats. Les types de formats de documents pris en charge sont les suivants : TXT, RTF, DOC, DOCX, PPT, PPTX, XLS et XLSX. Experience Manager Assets convertit automatiquement ces formats de document au format PDF, pouvant alors bénéficier de la fonctionnalité de prévisualisation.

![Prévisualiser plusieurs pages de documents dans d’autres formats](/help/assets/assets/multi-page-other-formats.png)

Pour prévisualiser plusieurs pages dans d’autres formats de documents pris en charge, procédez comme suit :

1. Suivez la procédure afin de [télécharger des ressources dans AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/add-assets.html?lang=fr).
1. Accédez au document que vous souhaitez télécharger et prévisualiser.
1. Ouvrez le document.
1. Sélectionnez PDF dans la section statique du panneau gauche. Le panneau droit affiche la prévisualisation de plusieurs pages d’une ressource. Sélectionnez une miniature dans le panneau gauche pour choisir la page à prévisualiser.

>[!NOTE]
>
> * La taille maximale d’une ressource prévisualisable est de 100 Mo.
> * La taille maximale des fichiers XLS ou XLSX pouvant être prévisualisés est de 20 Mo.

**Voir également**

* [Traduire les ressources](translate-assets.md)
* [API HTTP Assets](mac-api-assets.md)
* [Formats de fichiers pris en charge par Assets](file-format-support.md)
* [Rechercher des ressources](search-assets.md)
* [Ressources connectées](use-assets-across-connected-assets-instances.md)
* [Rapports de ressources](asset-reports.md)
* [Schémas de métadonnées](metadata-schemas.md)
* [Télécharger des ressources](download-assets-from-aem.md)
* [Gestion des métadonnées](manage-metadata.md)
* [Facettes de recherche](search-facets.md)
* [Gérer les collections](manage-collections.md)
* [Import des métadonnées en bloc](metadata-import-export.md)
* [Publier des ressources sur AEM et Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
