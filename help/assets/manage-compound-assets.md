---
title: Gestion des ressources composées
description: Découvrez comment créer des références à des ressources AEM à partir de fichiers Adobe Indesign, Adobe Illustrator et Adobe Photoshop. Découvrez également comment utiliser la fonctionnalité de visionneuse de pages pour afficher des pages individuelles de fichiers de plusieurs pages, y compris des fichiers PDF, INDD, PPT, PPTX et AI.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Gestion de ressources composites {#managing-compound-assets}

Le composant Adobe Experience Manager (AEM) Assets peut déterminer si un fichier chargé contient des références à des ressources existant déjà dans le référentiel. Cette fonctionnalité est disponible uniquement pour les types de format pris en charge. Si le fichier chargé contient des références à des actifs AEM, un lien bidirectionnel est créé entre les ressources chargées et celles référencées.

En plus de supprimer toute redondance, le référencement des ressources AEM dans les applications Adobe Creative Cloud améliore la collaboration et accroît l’efficacité et la productivité des utilisateurs.

AEM Assets supports **bidirectional referencing**. Vous trouverez des ressources référencées dans la page des détails de la ressource du fichier chargé. Vous pouvez, en outre, afficher les fichiers de référencement des ressources AEM dans la page des détails de la ressource référencée.

Les références sont résolues sur la base du chemin d’accès, du document et de l’ID d’instance des ressources référencées.

## Ajout de ressources AEM Assets en tant que références dans Adobe Illustrator {#refai}

Vous pouvez référencer des ressources AEM existantes dans un fichier Adobe Illustrator.

Pour ajouter des ressources numériques, utilisez l’application [de bureau](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html#upload-and-add-new-assets-to-aem) AEM ou [téléchargez-les à l’aide de l’interface utilisateur d’AEM](/help/assets/manage-digital-assets.md#uploading-assets) .

Une fois le processus terminé, accédez à la page des détails de la ressource. Les références à des ressources AEM existantes sont répertoriées sous **Dépendances** dans la colonne **Références.** The referenced assets that appear under **Dependencies** can also be referenced by files other than the current one.

Pour afficher une liste des fichiers de référencement d’une ressource, cliquez sur son nom sous **Dépendances**. Click the **View Properties** icon from the toolbar. Dans la page des propriétés, la liste des fichiers qui référencent l’actif en cours est visible sous la colonne **Références** dans l’onglet **De base**.

## Ajout de ressources AEM Assets en tant que références dans Adobe InDesign {#add-aem-assets-as-references-in-adobe-indesign}

Pour référencer des fichiers AEM depuis un fichier InDesign, faites glisser les fichiers AEM vers le fichier InDesign ou exportez le fichier InDesign sous forme de fichier ZIP.

Les ressources référencées existent déjà dans AEM Assets. Vous pouvez extraire des sous-ressources en configurant le serveur Adobe InDesign. Les ressources intégrées à un fichier InDesign sont extraites sous la forme de sous-ressources.

>[!NOTE]
>
>Si le serveur InDesign est soumis à un proxy, l’aperçu des fichiers InDesign est intégré à leurs métadonnées XMP. Dans ce cas, l’extraction de miniature n’est pas explicitement requise. Toutefois, si le serveur InDesign n’est pas soumis à un proxy, les miniatures doivent être explicitement extraites pour les fichiers InDesign.

### Create references by dragging AEM assets {#create-references-by-dragging-aem-assets}

The procedure is similar to [Adding AEM assets as references in Adobe Illustrator](#refai).

### Création de références aux ressources en exportant un fichier ZIP {#create-references-to-aem-assets-by-exporting-a-zip-file}

1. Créer un processus.
1. Utilisez l’option Assemblage d’Adobe InDesign pour exporter le document.
Adobe InDesign peut exporter un document et les ressources liées sous la forme d’un assemblage. Dans ce cas, le dossier exporté contient un dossier Liens dans lequel se trouvent des sous-ressources dans le fichier InDesign.
1. Créez un fichier ZIP et transférez-le dans le référentiel AEM.
1. Commencez le workflow de désarchivage.
1. Une fois le processus terminé, les références contenues dans le dossier Links sont automatiquement référencées en tant que sous-ressources. Pour afficher la liste des ressources référencées, accédez à la page des détails de la ressource.

## Ajout de ressources AEM Assets en tant que références dans Adobe Photoshop {#refps}

Pour ajouter des ressources numériques, utilisez l’application [de bureau](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html#upload-and-add-new-assets-to-aem) AEM ou [téléchargez-les à l’aide de l’interface utilisateur d’AEM](/help/assets/manage-digital-assets.md#uploading-assets) .

Une fois le processus terminé, les références aux ressources AEM existantes sont répertoriées dans la page des détails de la ressource. Les ressources référencées contiennent également la liste des ressources à partir desquelles elles sont référencées. Pour afficher la liste des ressources référencées, accédez à la page des détails des ressources.

>[!NOTE]
>
>Les ressources des ressources composées peuvent également être référencées en fonction de leur ID de document et de leur ID d’instance. Cette fonctionnalité est disponible avec les versions d’Adobe Illustrator et d’Adobe Photoshop uniquement. Pour les autres, le référencement s’effectue sur la base du chemin d’accès relatif des ressources liées dans la ressource composite principale, comme dans les versions précédentes d’AEM.

## Affichage des pages d’un fichier multipage {#view-pages-of-a-multi-page-file}

La visionneuse d’AEM Assets vous permet d’afficher séparément les pages de fichiers multipage aux formats PDF, INDD, PPT, PPTX et AI. S’agissant d’InDesign, vous pouvez extraire des pages à l’aide du serveur InDesign. Si les aperçus des pages sont enregistrés lors de la création du fichier InDesign, le serveur InDesign n’est pas nécessaire pour l’extraction des pages.

Vous pouvez parcourir les pages individuelles d’un fichier à partir de la page de ressource. Vous pouvez utiliser les options de la barre d’outils pour annoter chaque page du fichier. You can also use the **Page Overview** option to view all the pages simultaneously.

1. Dans AEM Assets, accédez au dossier qui contient le fichier de plusieurs pages.
1. Cliquez sur la ressource pour afficher sa page de ressource.
1. Cliquez sur l’icône de navigation globale, puis sélectionnez **Pages** dans le menu.
1. Cliquez sur les flèches gauche ou droite sous l’image pour accéder aux pages individuelles du fichier.
1. To annotate a page, click the **Annotate** icon from the toolbar and add a comment.
1. To download the file, click the **Download** icon.
1. To view all pages of the file simultaneously, click the **Page Overview** icon.
1. To view the activity stream for the file, including annotations and downloads, click the AEM icon and then choose **Timeline** from the menu.
1. To view and edit the metadata properties of the page, click the **View Properties** icon from the toolbar.
