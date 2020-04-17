---
title: Gestion de ressources composites
description: Découvrez comment créer des références aux actifs AEM au sein de fichiers InDesign, Adobe Illustrator et Photoshop. Découvrez également comment utiliser la fonction Visionneuse de page pour afficher les pages individuelles de fichiers de plusieurs pages, y compris les fichiers PDF, INDD, PPT, PPTX et AI.
contentOwner: AG
translation-type: ht
source-git-commit: 82dd9bd69fe994f74c7be8a571e386f0e902f6a1

---


# Gestion de ressources composites {#managing-compound-assets}

Le composant Adobe Experience Manager (AEM) Assets peut déterminer si un fichier chargé contient des références à des ressources existant déjà dans le référentiel. Cette fonctionnalité est disponible uniquement pour les types de formats pris en charge. Si le fichier chargé contient des références à des actifs AEM, un lien bidirectionnel est créé entre les ressources chargées et celles référencées.

En plus de supprimer toute redondance, le référencement des ressources AEM dans les applications Adobe Creative Cloud améliore la collaboration et accroît l’efficacité et la productivité des utilisateurs.

AEM Assets prend en charge le **référencement bidirectionnel**. Vous trouverez des ressources référencées dans la page des détails de la ressource du fichier chargé. Vous pouvez, en outre, afficher les fichiers de référencement des ressources AEM dans la page des détails de la ressource référencée.

Les références sont résolues sur la base du chemin d’accès, du document et de l’ID d’instance des ressources référencées.

## Ajout de ressources AEM Assets en tant que références dans Adobe Illustrator   {#refai}

Vous pouvez référencer des ressources AEM existantes dans un fichier Adobe Illustrator.

1. Utilisez l’[application de bureau AEM](https://docs.adobe.com/content/help/fr-FR/experience-manager-desktop-app/using/using.html) pour monter le référentiel AEM Assets en tant que lecteur sur votre ordinateur local. Dans le lecteur monté, accédez à l’emplacement de la ressource à référencer.
1. Faites glisser la ressource du volume monté jusqu’au fichier Illustrator.
1. Enregistrez le fichier Illustrator sur le lecteur monté ou [chargez-le](/help/assets/manage-digital-assets.md#uploading-assets) dans le référentiel AEM.
1. Une fois le workflow terminé, accédez à la page des détails de la ressource. Les références à des ressources AEM existantes sont répertoriées sous **Dépendances** dans la colonne **Références**.

   ![chlimage_1-84](assets/chlimage_1-84.png)

1. Les ressources référencées qui apparaissent sous **Dépendances** peuvent également être référencées par des fichiers autres que celui qui est actif. Pour afficher une liste des fichiers de référencement d’une ressource, cliquez sur son nom sous **Dépendances**.

   ![chlimage_1-85](assets/chlimage_1-85.png)

1. Dans la barre d’outils, cliquez sur l’icône **Afficher les propriétés**. Dans la page des propriétés, la liste des fichiers qui référencent la ressource en cours est visible sous la colonne **Références** dans l’onglet **De base**.

   ![chlimage_1-86](assets/chlimage_1-86.png)

## Ajout de ressources AEM Assets en tant que références dans Adobe InDesign {#add-aem-assets-as-references-in-adobe-indesign}

Pour référencer des ressources AEM dans un fichier InDesign, faites-les glisser jusqu’au fichier ou exportez le fichier InDesign en tant que fichier ZIP.

Les ressources référencées existent déjà dans AEM Assets. <!-- You can extract subassets by [configuring InDesign server](/help/assets/indesign.md). Embedded assets in an InDesign file are extracted as subassets. -->

>[!NOTE]
>
>Si le serveur InDesign est soumis à un proxy, l’aperçu des fichiers InDesign est intégré à leurs métadonnées XMP. Dans ce cas, l’extraction de miniature n’est pas explicitement requise. Toutefois, si le serveur InDesign n’est pas soumis à un proxy, les miniatures doivent être explicitement extraites pour les fichiers InDesign.

### Création de références en faisant glisser des ressources AEM   {#create-references-by-dragging-aem-assets}

Cette procédure est similaire à l’[ajout de ressources AEM en tant que références dans Adobe Illustrator](#refai).

### Création de références aux ressources AEM en exportant un fichier ZIP {#create-references-to-aem-assets-by-exporting-a-zip-file}

1. Créez un modèle de workflow.
1. Utilisez l’option Assemblage d’Adobe InDesign pour exporter le document.
Adobe InDesign peut exporter un document et les ressources liées sous la forme d’un assemblage. Dans ce cas, le dossier exporté contient un dossier Liens dans lequel se trouvent des sous-ressources dans le fichier InDesign.
1. Créez un fichier ZIP et transférez-le dans le référentiel AEM.
1. Commencez le workflow de désarchivage.
1. Une fois le workflow terminé, les références contenues dans le dossier Liens sont automatiquement référencées en tant que sous-ressources. Pour afficher la liste des ressources référencées, accédez à la page des détails de la ressource InDesign et fermez le [rail](/help/sites-cloud/authoring/getting-started/basic-handling.md#rail-selector).

## Ajout de ressources AEM Assets en tant que références dans Adobe Photoshop {#refps}

1. À l’aide d’un client WebDAV, montez AEM Assets comme lecteur.
1. Pour créer des références à des ressources AEM dans un fichier Photoshop, accédez aux ressources correspondantes sur le volume monté à l’aide de l’option Importer et lier dans Photoshop.

   ![chlimage_1-87](assets/chlimage_1-87.png)

1. Enregistrez le fichier Photoshop sur le lecteur monté ou [chargez-le](/help/assets/manage-digital-assets.md#uploading-assets) dans le référentiel AEM.
1. Une fois le worflow terminé, les références aux ressources AEM existantes sont répertoriées dans la page des détails de la ressource.

   Pour afficher les ressources référencées, fermez le [rail](/help/sites-cloud/authoring/getting-started/basic-handling.md#rail-selector) dans la page des détails de la ressource.

1. Les ressources référencées contiennent également la liste des ressources à partir desquelles elles sont référencées. Pour afficher la liste des ressources référencées, accédez à la page des détails de la ressource et fermez le [rail](/help/sites-cloud/authoring/getting-started/basic-handling.md#rail-selector).

>[!NOTE]
>
>Les ressources contenues dans des ressources composites peuvent également être référencées par ID de document et ID d’instance. Cette fonctionnalité est disponible avec les versions d’Adobe Illustrator et d’Adobe Photoshop uniquement. Pour les autres, le référencement s’effectue sur la base du chemin d’accès relatif des ressources liées dans la ressource composite principale, comme dans les versions précédentes d’AEM.

## Affichage des pages d’un fichier multipage   {#view-pages-of-a-multi-page-file}

La visionneuse d’AEM Assets vous permet d’afficher séparément les pages de fichiers multipage aux formats PDF, INDD, PPT, PPTX et AI. S’agissant d’InDesign, vous pouvez extraire des pages à l’aide du serveur InDesign. Si les aperçus des pages sont enregistrés lors de la création du fichier InDesign, le serveur InDesign n’est pas nécessaire pour l’extraction des pages.

Vous pouvez parcourir les pages individuelles d’un fichier à partir de la page de ressource. Vous pouvez utiliser les options de la barre d’outils pour annoter chaque page du fichier. Vous pouvez également utiliser l’option **Aperçu de page** pour afficher toutes les pages simultanément.

1. Dans AEM Assets, accédez au dossier qui contient le fichier de plusieurs pages.
1. Cliquez sur la ressource pour afficher sa page de ressource.

   ![chlimage_1-88](assets/chlimage_1-88.png)

1. Cliquez sur l’icône de navigation globale, puis sélectionnez **Pages** dans le menu.

   ![chlimage_1-89](assets/chlimage_1-89.png)

1. Cliquez sur les flèches gauche ou droite sous l’image pour accéder aux pages individuelles du fichier.

   ![chlimage_1-90](assets/chlimage_1-90.png)

1. Pour annoter une page, cliquez sur l’icône **Annoter** de la barre d’outils et rédigez un commentaire.

   ![chlimage_1-91](assets/chlimage_1-91.png)

1. Pour télécharger le fichier, cliquez sur l’icône **Télécharger**.

   ![chlimage_1-92](assets/chlimage_1-92.png)

1. Pour afficher toutes les pages du fichier en même temps, cliquez sur l’icône **Aperçu de page**.

   ![chlimage_1-93](assets/chlimage_1-93.png)

1. Pour voir le flux d’activités du fichier, y compris les annotations et les téléchargements, cliquez sur l’icône de navigation globale, puis sélectionnez **Chronologie** dans le menu.

   ![chlimage_1-94](assets/chlimage_1-94.png)

1. Pour afficher et modifier les propriétés des métadonnées de la page, cliquez sur l’icône **Afficher les propriétés** de la barre d’outils.

   ![chlimage_1-95](assets/chlimage_1-95.png)
