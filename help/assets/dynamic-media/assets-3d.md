---
title: Utilisation de ressources 3D dans Dynamic Media
description: Découvrez comment utiliser des ressources 3D dans Dynamic Media.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS and Experience Manager as a Cloud Service
topic-tags: introduction
content-type: reference
feature: Ressources 3D
role: Business Practitioner
exl-id: 82084ba7-1302-4cbd-8626-d77b3aaa4ed1
translation-type: tm+mt
source-git-commit: 1fe6ce1259972c1805d934327aa2f24cdcdc0bc8
workflow-type: tm+mt
source-wordcount: '2248'
ht-degree: 75%

---

# Utilisation de ressources 3D dans Dynamic Media {#working-with-three-d-assets-dm}

Dynamic Media permet de charger, gérer, afficher et diffuser des ressources 3D sous la forme d’expériences immersives.

* Publication en un clic (à l’aide de l’option **[!UICONTROL Publication rapide]** dans la barre d’outils) de ressources 3D pour générer une URL.
* Prise en charge optimisée de l’affichage de ressources 3D avec le paramètre prédéfini de visionneuse Dimensionnel de haute qualité et interactive, optimisée par Adobe Dimension.
* Le composant WCM 3D Media vous permet d’ajouter facilement des ressources 3D à vos pages Adobe Experience Manager Sites.

Aucune installation supplémentaire n’est nécessaire pour utiliser des ressources 3D dans Dynamic Media.

![Chaussure en 3d](/help/assets/dynamic-media/assets/3d-dimensional-viewer-quickpublish-url-embed2a.png)

<!-- See also [Dynamic Media 3D Release Notes](/help/release-notes/aem3d-release-notes.md). -->

## Formats 3D pris en charge par Dynamic Media {#supported-three-d-file-formats-in-dm}

Dynamic Media prend en charge les formats de fichiers 3D suivants :

Voir aussi [Formats 3D pris en charge](/help/assets/file-format-support.md#support-3d-formats)

| Extension de fichier 3D | Format de fichier | Type MIME | Remarques |
|---|---|---|---|
| GLB | Transmission GL binaire | model/gltf-binary | Inclut les matières et les textures dans une seule ressource. |
| OBJ | Fichier d’objet 3D WaveFront | application/x-tgif |  |
| STL | Stéréolithographie | application/vnd.ms-pki.stl |  |
| USDZ | Fichier zip de description de scène universelle | model/vnd.usdz+zip | *Prise en charge de l’ingestion uniquement ; aucun affichage ni interaction n’est disponible.* USDZ est un format 3D propriétaire qui peut être visualisé en mode natif à l’aide de Safari ou iOS. |

## Démarrage rapide : ressources 3D dans Dynamic Media {#quick-start-three-d}

La description du workflow étape par étape qui suit est conçue pour vous aider à démarrer et à utiliser rapidement des ressources 3D dans Dynamic Media.

Avant d’utiliser ces ressources 3D dans Dynamic Media, vérifiez que l’administrateur Experience Manager a activé et configuré les Cloud Services Dynamic Media.

Voir [Configuration des Cloud Services Dynamic Media](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services).

1. **Chargement de ressources 3D**

   * [Chargement de ressources 3D pour utilisation dans Dynamic Media](/help/assets/add-assets.md#upload-assets)
   * [Formats de ressources 3D pris en charge pour le chargement dans Dynamic Media](#supported-three-d-file-formats-in-dm)

1. **Gestion des ressources 3D**

   * Organisation et recherche des ressources 3D

      * [Organisation des ressources numériques](/help/assets/organize-assets.md)
      * [Recherche de ressources 3D](/help/assets/search-assets.md)
   * Affichage de ressources 3D

      * [Affichage et interaction avec des ressources 3D](#viewing-three-d-assets)
      * [Gestion du paramètre prédéfini de la visionneuse Dimensionnel](/help/assets/dynamic-media/managing-viewer-presets.md)
   * Utilisation des métadonnées des ressources 3D

      * [Gestion des métadonnées des ressources numériques](/help/assets/manage-digital-assets.md#editing-properties)
      * [Schémas de métadonnées](/help/assets/metadata-schemas.md)



1. **Publication de ressources 3D**

   * [Publication de ressources 3D Dynamic Media statiques](#publishing-three-d-assets)
   * [Autres méthodes de publication de ressources 3D Dynamic Media à l’aide de la visionneuse Dimensionnel](#alternate-publish-methods)

## À propos de l’affichage et des interactions avec des ressources 3D {#viewing-three-d-assets}

Cette section décrit deux manières différentes d’afficher des ressources 3D et d’interagir avec elles : dans la page des détails de la ressource et dans le composant Média 3D de Sites.

La visionneuse 3D interactive comprend, entre autres, un ensemble de contrôles de caméra interactifs qui permettent d’orbiter, de zoomer et de faire un panoramique sur la ressource 3D.

Le temps nécessaire pour ouvrir un fichier 3D dans la vue de page Détails du fichier dépend de plusieurs facteurs. Ces facteurs sont notamment :

* La bande passante sur le serveur.
* Les latences sur le serveur.
* La complexité de l’image.

De plus, les capacités de l’ordinateur client, par exemple un poste de travail, un ordinateur portable ou un appareil mobile tactile, doivent être prises en compte lorsque vous manipulez la caméra de manière interactive. Un système relativement puissant avec de bonnes capacités graphiques peut rendre l’expérience interactive d’affichage en 3D plus fluide et plus favorable.

>[!TIP]
>
>Vous pouvez ouvrir le paramètre prédéfini de visionneuse Dimensionnel dans l’éditeur de paramètres prédéfinis de la visionneuse pour vous entraîner à naviguer dans une ressource 3D sans avoir à charger un fichier 3D au préalable. Ce paramètre prédéfini comporte une ressource 3D intégrée avec laquelle vous pouvez interagir.
>
>Voir [Gestion des paramètres prédéfinis de visionneuse](/help/assets/dynamic-media/managing-viewer-presets.md).

## Affichage et interaction avec une ressource 3D à l’aide de la page des détails de la ressource {#viewing-three-d-assets-from-asset-details-page}

Voir aussi [Prévisualisation de ressources à l’aide de l’interface logicielle](/help/assets/dynamic-media/previewing-assets.md).

**Pour afficher et interagir avec une ressource 3D à l’aide de la page des détails de la ressource:**

1. Assurez-vous d’avoir chargé des ressources 3D dans Experience Manager.

   Voir [Chargement de ressources 3D pour utilisation dans Dynamic Media](/help/assets/add-assets.md#upload-assets).

1. Dans Experience Manager, sur la page **[!UICONTROL Navigation]**, appuyez sur **[!UICONTROL Ressources > Fichiers]**.
1. Dans l’angle supérieur droit de la page, dans la liste déroulante **[!UICONTROL Vue]**, appuyez sur **[!UICONTROL Mode Carte]**.
1. Accédez à une ressource 3D que vous souhaitez afficher.
1. Pour ouvrir le fichier dans la page Détails, appuyez sur la carte du fichier 3D.
1. Dans la page Détails de la ressource 3D, effectuez l&#39;une des opérations suivantes :

   | Mode | Description | Action de souris | Action de l’écran tactile |
   | --- | --- | --- | --- |
   | **Tournez votre appareil photo** | Faites tourner la vue autour de la scène 3D et des objets. | Cliquez avec le bouton gauche et faites glisser. | Appuyez sur un seul doigt et faites glisser. |
   | **Panoramique de l’appareil photo** | Déplacez votre vue vers la gauche, la droite, vers le haut ou vers le bas. | Cliquez avec le bouton droit de la souris et faites glisser. | Appuyez sur deux doigts et faites glisser. |
   | **Zoom de la caméra** | Déplacez-vous dans ou hors des zones de la scène 3D. | Roue de défilement. | Pincement à deux doigts. |
   | **Recentrer votre caméra** | Recentrez votre caméra sur un objet de la scène 3D. | Double-cliquer. | Double appui. |
   | **Réinitialiser** | Près du coin inférieur droit de la page, appuyez sur l&#39;icône Réinitialiser pour rétablir le point de cible de vue au centre de la ressource 3D. De plus, Réinitialiser rapproche ou éloigne l’angle de vue pour afficher la ressource dans son intégralité et à une taille raisonnable. |  |  |
   | **Mode Plein écran** | Pour passer en mode plein écran, dans le coin inférieur droit de la page, appuyez sur l’icône Plein écran. |  |  |

1. Dans l’angle supérieur droit de la page, appuyez sur **[!UICONTROL Fermer]** pour revenir à la page Ressources.

## Affichage et interaction avec une ressource 3D dans un composant Média 3D {#interacting-with-asset-inside-three-d-media-component}

Lorsqu’une page web est en mode **[!UICONTROL Édition]**, aucune interaction n’est possible avec une ressource 3D. Pour rendre la ressource interactive, vous pouvez utiliser la fonction **[!UICONTROL Aperçu]**. Vous pouvez ainsi afficher la page web dans l’éditeur de page avec un accès complet aux fonctionnalités du composant Média 3D.

>[!IMPORTANT]
>
>Vous ne pouvez accomplir cette tâche qu’après avoir ajouté un composant Média 3D à une page web et y avoir affecté une ressource 3D. Voir [Ajout du composant Média 3D à une page web](#adding-the-three-d-media-component-to-a-web-page) et [Affectation d’une ressource 3D à un composant Média 3D](#assigning-a-three-d-asset-to-the-component).

Voir aussi [Prévisualisation de ressources à l’aide de l’interface logicielle](/help/assets/dynamic-media/previewing-assets.md).

**Pour afficher et interagir avec une ressource 3D dans un composant Média 3D:**

1. Lorsqu’une page web est en mode **[!UICONTROL Édition]**, effectuez l’une des opérations suivantes :

   * Près de l’angle supérieur droit de la page, cliquez sur **[!UICONTROL Prévisualisation]** pour passer en mode **[!UICONTROL Prévisualisation]**.
   * Supprimez `/editor.html` de l’URL de la page dans le navigateur.

Ressource 3D entièrement interactive affichée en mode Aperçu    ![Ressource 3D affichée dans le composant Média 3D](/help/assets/dynamic-media/assets/3d-asset-in-3d-mediaa.png)
Ressource 3D entièrement interactive affichée en mode **[!UICONTROL Aperçu]**.

1. En mode **[!UICONTROL Aperçu]**, effectuez l’une des opérations suivantes :

   | Mode | Description | Action de souris | Action de l’écran tactile |
   | --- | --- | --- | --- |
   | **Tournez votre appareil photo** | Faites tourner la vue autour de la scène 3D et des objets. | Cliquez avec le bouton gauche et faites glisser. | Appuyez sur un seul doigt et faites glisser. |
   | **Panoramique de l’appareil photo** | Déplacez votre vue vers la gauche, la droite, vers le haut ou vers le bas. | Cliquez avec le bouton droit de la souris et faites glisser. | Appuyez sur deux doigts et faites glisser. |
   | **Zoom de la caméra** | Déplacez-vous dans ou hors des zones de la scène 3D. | Roue de défilement. | Pincement à deux doigts. |
   | **Recentrer votre caméra** | Recentrez votre caméra sur un objet de la scène 3D. | Double-cliquer. | Double appui. |
   | **Réinitialiser** | Près du coin inférieur droit de la page, appuyez sur l&#39;icône Réinitialiser pour rétablir le point de cible de vue au centre de la ressource 3D. De plus, Réinitialiser rapproche ou éloigne l’angle de vue pour afficher la ressource dans son intégralité et à une taille raisonnable. |  |  |
   | **Mode Plein écran** | Pour passer en mode plein écran, dans le coin inférieur droit de la page, appuyez sur l’icône Plein écran. |  |  |

## À propos de l’utilisation du composant Média 3D {#working-with-three-d-media-component}

Dynamic Media contient un composant Média 3D Dynamic Media que vous pouvez utiliser dans Experience Manager Sites pour activer l’affichage interactif de modèles 3D dans vos pages web.

* [Ajout du composant Média 3D au modèle de page](#adding-three-d-media-component-to-page-template)
* [Ajout du composant Média 3D à une page web](#adding-the-three-d-media-component-to-a-web-page)
   * [Facultatif - Configuration du composant Média 3D](#configuring-the-three-d-component)
* [Affectation d’une ressource 3D au composant Média 3D](#assigning-a-three-d-asset-to-the-component)

## Ajout du composant Média 3D au modèle de page {#adding-three-d-media-component-to-page-template}

1. Accédez à **[!UICONTROL Outils > Général > Modèles]**.
1. Accédez au modèle de page dans lequel vous souhaitez activer le composant 3D, puis sélectionnez le modèle.
1. Pour ouvrir le modèle, appuyez sur **[!UICONTROL Modifier]**.
1. Près de l’angle supérieur droit de la page, dans le menu déroulant, sélectionnez le mode **[!UICONTROL Structure]**, s’il n’est pas déjà principal.

   ![3d-media-component-structure](/help/assets/dynamic-media/assets/3d-media-component-structurea.png)

1. Pour sélectionner une zone vide et ouvrir sa barre d’outils associée, appuyez sur la zone vide de la région **[!UICONTROL Conteneur de mise en page]**.
1. Dans la barre d’outils, appuyez sur l’icône **[!UICONTROL Stratégie]** pour ouvrir l’**[!UICONTROL Éditeur de stratégies]**.
1. Dans la section **[!UICONTROL Propriétés]**, sous l’onglet **[!UICONTROL Composants autorisés]**, faites défiler l’écran jusqu’à **[!UICONTROL Dynamic Media]**, puis développez la liste et cochez la case **[!UICONTROL Média 3D]**.
1. Appuyez sur **[!UICONTROL Terminé]** pour enregistrer les modifications et fermer l’**[!UICONTROL Éditeur de stratégies]**.

   Vous pouvez maintenant incorporer le composant Média 3D Dynamic Media dans toutes les pages qui utilisent ce modèle.

## Ajout du composant Média 3D à une page web {#adding-the-three-d-media-component-to-a-web-page}

Si vous utilisez le Experience Manager comme système de gestion de contenu Web, vous pouvez ajouter des ressources 3D à vos pages Web au moyen du composant Média 3D.

Voir aussi [Ajout de ressources Dynamic Media aux pages](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).

1. Ouvrez Experience Manager Sites et sélectionnez la page web à laquelle vous souhaitez ajouter le composant Média 3D Dynamic Media.
1. Pour ouvrir la page dans l’éditeur de page, appuyez sur l’icône **[!UICONTROL Modifier]** (représentant un crayon). Assurez-vous que le mode **[!UICONTROL Modifier]** est sélectionné près de l’angle supérieur droit de la page.

   ![3d-media-component-add](/help/assets/dynamic-media/assets/3d-media-component-edita.png)

1. Dans la barre d’outils, appuyez sur l’icône du panneau latéral pour déclencher ou « activer » l’affichage du panneau.

1. Dans le panneau latéral, appuyez sur l’icône + pour ouvrir la liste **[!UICONTROL Composants]**.

   ![3d-media-component-drag-drop](/help/assets/dynamic-media/assets/3d-assets-filtera.png)

1. Faites glisser le composant **[!UICONTROL Média 3D]** depuis la liste **[!UICONTROL Composants]** vers l’emplacement de la page où vous souhaitez qu’apparaisse la visionneuse 3D.

Vous êtes maintenant prêt à affecter une ressource 3D au composant.

Voir [Affectation d’un fichier 3D au composant Média 3D](#assigning-a-three-d-asset-to-the-component)

### Facultatif - Configuration du composant Média 3D {#configuring-the-three-d-component}

1. Dans l’éditeur de pages d’Experience Manager Sites, sélectionnez le composant **[!UICONTROL Visionneuse de médias 3D]** déjà ajouté à la page.
1. Pour ouvrir la boîte de dialogue de configuration du composant, appuyez sur l&#39;icône **[!UICONTROL Configuration]** (clé à molette).

   ![3d-media-component-config](/help/assets/dynamic-media/assets/3d-media-component-configa.png)

1. Dans la boîte de dialogue Média 3D, dans la liste déroulante Paramètre prédéfini de la visionneuse, sélectionnez **[!UICONTROL Dimensionnel]** pour affecter au composant le paramètre prédéfini de la visionneuse Dimensionnel.

   ![3d-media-component-edit-config](/help/assets/dynamic-media/assets/3d-media-component-edit-configa.png)

1. Dans l’angle supérieur droit, appuyez sur la coche pour enregistrer vos modifications.

## Affectation d’une ressource 3D au composant Média 3D {#assigning-a-three-d-asset-to-the-component}

Après avoir ajouté un composant Média 3D à une page web, vous pouvez lui affecter une ressource 3D.

Voir [Ajout du composant Média 3D à une page web](#adding-the-three-d-media-component-to-a-web-page).

1. Dans l’éditeur de pages d’Experience Manager Sites, cliquez sur l’icône **[!UICONTROL Ressources]** pour ouvrir **[!UICONTROL Ressources]** dans le panneau latéral.
1. Dans la liste déroulante, sélectionnez **[!UICONTROL 3D]** pour afficher uniquement les types de fichiers de ressources 3D.
1. Dans le panneau latéral, recherchez ou faites défiler l’écran jusqu’à atteindre la ressource 3D que vous souhaitez afficher sur la page en cours de modification.
1. Faites glisser la ressource 3D à partir du panneau latéral Ressources et déposez-le sur le composant **[!UICONTROL Média 3D]** que vous avez précédemment ajouté à la page.

   ![Affectation d’une ressource 3D au composant Média 3D](/help/assets/dynamic-media/assets/3d-asset-adda.png)

>[!NOTE]
>
>Lorsqu’une page web est en mode **[!UICONTROL Édition]** dans Experience Manager Sites, le composant Média 3D affiche la ressource 3D, mais aucune interaction avec elle n’est possible. Pour rendre la ressource interactive, vous pouvez utiliser la fonction **[!UICONTROL Aperçu]**. Vous pouvez ainsi afficher la page web dans l’éditeur de page avec un accès complet aux fonctionnalités du composant Média 3D.

## Publication de ressources 3D Dynamic Media statiques {#publishing-three-d-assets}

Dynamic Media accepte divers formats de fichier 3D pris en charge en tant que *contenu statique* dans Dynamic Media. La notion de contenu statique signifie que vous pouvez charger et publier des ressources 3D, mais que les fonctions d’imagerie *dynamique* ou de retouche d’images associées à la ressource 3D ne sont pas prises en charge. En effet, Dynamic Media Imaging Server ne reconnaît pas les formats 3D. Ainsi, après avoir publié une ressource 3D dans Dynamic Media, vous disposez d’une URL instantanée que vous pouvez copier. L’URL de la ressource 3D suit la structure d’URL Dynamic Media habituelle. Cependant, vous ne pouvez pas modifier les paramètres de l’URL de la ressource, contrairement aux ressources d’images traditionnelles de Dynamic Media.

Voir également [Obtention d’une URL pour une ressource statique](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-a-static-asset).

En **[!UICONTROL mode Carte]**, une petite icône en forme de globe apparaît directement sous le nom d’une ressource, et à gauche de ses informations de date et d’heure, pour indiquer qu’elle est publiée. En **[!UICONTROL mode Liste]**, une colonne **[!UICONTROL Publié]** indique les ressources qui sont publiées et celles qui ne le sont pas.

Si vous utilisez Experience Manager comme système de gestion de contenu web, utilisez cette méthode de publication pour ajouter directement les ressources 3D Dynamic Media dans votre page web.

Voir aussi [Publication de ressources Dynamic Media](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

Voir aussi [Publication de pages](/help/sites-cloud/authoring/fundamentals/publishing-pages.md).

**Pour publier des ressources 3D Dynamic Media statiques:**

1. Ouvrez un fichier 3D (format de fichier GLB, OBJ ou STL).
1. Sur la page Détails, sur la barre d’outils, appuyez sur **[!UICONTROL Publication rapide]**.

   ![3d-asset-quick-publish](/help/assets/dynamic-media/assets/3d-asset-quick-publisha.png)

1. Appuyez sur **[!UICONTROL Fermer]** pour quitter la boîte de dialogue et revenir à la page des détails de la ressource.
1. Dans la liste déroulante située à gauche du nom de fichier de la ressource 3D, appuyez sur **[!UICONTROL Rendus]**.

   ![3d-asset-renditions](/help/assets/dynamic-media/assets/3d-asset-renditionsa.png)

1. Appuyez sur **[!UICONTROL original]**. Lorsqu’un fichier 3D est publié (ou &quot;activé&quot;), le bouton **[!UICONTROL URL]** s’affiche près du coin inférieur gauche de la page si toutes les conditions d’actif 3D suivantes sont remplies :
   * La ressource 3D est dans un format pris en charge (GLB, OBJ, STL et USDZ).
   * La ressource 3D a été ingérée dans le système IPS (Image Production System).
   * La ressource 3D est publiée.

   ![3d-asset-url](/help/assets/dynamic-media/assets/3d-asset-urla.png)

1. Pour afficher l’URL de production directe du fichier 3D que vous pouvez copier et utiliser sur des pages Web, appuyez sur **[!UICONTROL URL]**.

### Autres méthodes de publication de ressources 3D Dynamic Media à l’aide de la visionneuse Dimensionnel {#alternate-publish-methods}

Utilisez les deux méthodes suivantes pour publier des ressources 3D Dynamic Media si *vous n’utilisez pas* Experience Manager comme système de gestion de contenu web.

* **[!UICONTROL URL]**  - Utilisez  **** URL si vous utilisez un système de gestion de contenu Web tiers et souhaitez lier des ressources Dynamic Media 3D à vos pages Web à l’aide de la visionneuse Dimensional.

   Voir [Liaison d’URL à une application web](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-an-asset).

* **[!UICONTROL Incorporer]**  - Utilisez l’option  **** Incorporer lorsque vous souhaitez vue d’un fichier Dynamic Media 3D incorporé à une page Web à l’aide de la visionneuse Dimensional. Vous copiez le code intégré dans le presse-papiers pour pouvoir le coller dans vos pages web. Vous ne pouvez pas modifier le code dans la boîte de dialogue **[!UICONTROL Incorporer]**.

   Voir [Intégration de la visionneuse de vidéos ou d’images Dynamic Media, ou de la visionneuse Dimensionnel dans une page web](/help/assets/dynamic-media/embed-code.md#embedding-the-video-or-image-viewer-on-a-web-page).
