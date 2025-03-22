---
title: Utiliser des ressources 3D dans Dynamic Media
description: Découvrez comment utiliser des ressources 3D dans Dynamic Media.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS and Experience Manager as a Cloud Service
topic-tags: introduction
content-type: reference
feature: 3D Assets
role: User
exl-id: 82084ba7-1302-4cbd-8626-d77b3aaa4ed1
source-git-commit: c82f84fe99d8a196adebe504fef78ed8f0b747a9
workflow-type: tm+mt
source-wordcount: '2298'
ht-degree: 98%

---

# Utiliser des ressources 3D dans Dynamic Media {#working-with-three-d-assets-dm}

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

Dynamic Media permet de charger, gérer, afficher et diffuser des ressources 3D sous la forme d’expériences immersives.

* Publication en un clic (à l’aide de l’option **[!UICONTROL Publication rapide]** dans la barre d’outils) de ressources 3D pour générer une URL.
* Prise en charge optimisée de l’affichage de ressources 3D avec le paramètre prédéfini de visionneuse Dimensionnel de haute qualité et interactive, optimisée par Adobe Dimension.
* Ajout aisé de ressources 3D à vos pages [!DNL Adobe Experience Manager Sites] grâce au composant de gestion du contenu web Média 3D.

Aucune installation supplémentaire n’est nécessaire pour utiliser des ressources 3D dans Dynamic Media.

![Chaussure en 3D](/help/assets/dynamic-media/assets/3d-dimensional-viewer-quickpublish-url-embed2a.png)

<!-- See also [Dynamic Media 3D Release Notes](/help/release-notes/aem3d-release-notes.md). -->

## Formats 3D pris en charge par Dynamic Media {#supported-three-d-file-formats-in-dm}

Dynamic Media prend en charge les formats de fichiers 3D suivants :

Voir aussi [Formats 3D pris en charge par Experience Manager Assets](/help/assets/file-format-support.md#support-3d-formats)

| Extension de fichier 3D | Format de fichier | Type MIME | Remarques |
|---|---|---|---|
| GLB | Transmission GL binaire | model/gltf-binary | Inclut les matières et les textures dans une seule ressource. |
| OBJ | Fichier d’objet 3D WaveFront | application/x-tgif |  |
| STL | Stéréolithographie | application/vnd.ms-pki.stl |  |
| USDZ | Fichier zip de description de scène universelle | model/vnd.usdz+zip | *Prise en charge de l’ingestion uniquement ; aucun affichage ni interaction n’est disponible.* USDZ est un format 3D propriétaire qui peut être visualisé en mode natif à l’aide de Safari ou iOS. |

Le composant 3D Media WCM et l’aperçu 3D sur la page Détails d’une ressource ne sont pas compatibles avec la dernière version de Chrome (97.x). Pour utiliser des ressources 3D, utilisez plutôt Firefox ou Safari ou une version antérieure de Chrome (96.x).

## Démarrage rapide : ressources 3D dans Dynamic Media {#quick-start-three-d}

La description du workflow étape par étape qui suit est conçue pour vous aider à démarrer et à utiliser rapidement des ressources 3D dans Dynamic Media.

Avant d’utiliser ces ressources 3D dans Dynamic Media, vérifiez que l’administrateur [!DNL Experience Manager] a activé et configuré les services cloud Dynamic Media.

Voir [Configuration des Cloud Services Dynamic Media](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services).

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

1. **Publication de ressources 3D**

   * [Publication de ressources 3D Dynamic Media statiques](#publishing-three-d-assets)
   * [Autres méthodes de publication de ressources 3D Dynamic Media à l’aide de la visionneuse Dimensionnel](#alternate-publish-methods)

## À propos de l’affichage et des interactions avec des ressources 3D {#viewing-three-d-assets}

Cette section décrit deux manières différentes d’afficher des ressources 3D et d’interagir avec elles : dans la page des détails de la ressource et dans le composant Média 3D de Sites.

La visionneuse 3D interactive comprend, entre autres, un ensemble de contrôles de caméra interactifs qui permettent d’orbiter, de zoomer et de faire un panoramique sur la ressource 3D.

Le délai nécessaire pour ouvrir une ressource 3D dans la page de détails de la ressource dépend de plusieurs facteurs. Ces facteurs sont notamment :

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

**Pour afficher et interagir avec une ressource 3D à l’aide de la page des détails de la ressource :**

1. Assurez-vous d’avoir chargé des ressources 3D dans [!DNL Experience Manager].

   Voir [Chargement de ressources 3D pour utilisation dans Dynamic Media](/help/assets/add-assets.md#upload-assets).

1. Dans [!DNL Experience Manager], sur la page de **[!UICONTROL navigation]**, sélectionnez **[!UICONTROL Ressources > Fichiers]**.
1. Dans l’angle supérieur droit de la page, dans la liste déroulante **[!UICONTROL Vue]**, appuyez sélectionnez **[!UICONTROL Mode Carte]**.
1. Accédez à une ressource 3D que vous souhaitez afficher.
1. Pour ouvrir la ressource dans la page Détails, sélectionnez la carte de la ressource 3D.
1. Sur la page des détails de la ressource 3D, effectuez l’une des opérations suivantes :

   | Mode | Description | Action de souris | Action de l’écran tactile |
   | --- | --- | --- | --- |
   | **Faire pivoter la caméra** | Faites tourner la vue autour de la scène 3D et des objets. | Clic gauche + glisser. | Appuyez avec un seul doigt + glisser. |
   | **Effectuer un panoramique avec la caméra** | Vous pouvez effectuer un panoramique vers la gauche, la droite, le haut ou le bas. | Clic droit + glisser. | Appuyez avec deux doigts + glisser. |
   | **Faire un zoom avec la caméra** | Se déplacer dans et hors des zones de la scène 3D. | Roue de défilement. | Appuyer avec deux doigts en les rapprochant. |
   | **Recentrer la caméra** | Recentrez la caméra sur un point d’un objet dans la scène 3D. | Double-cliquer. | Double-sélectionner. |
   | **Réinitialiser** | Près du coin inférieur droit de la page, sélectionnez l’icône Réinitialiser pour rétablir le point d’affichage cible au centre du fichier 3D. De plus, Réinitialiser rapproche ou éloigne l’angle de vue pour afficher la ressource dans son intégralité et à une taille raisonnable. |   |   |
   | **Mode Plein écran** | Pour passer en mode Plein écran, dans le coin inférieur droit de la page, sélectionnez l’icône Plein écran. |   |   |

1. Dans l’angle supérieur droit de la page, sélectionnez **[!UICONTROL Fermer]** pour revenir à la page Ressources.

## Afficher et interagir avec une ressource 3D dans un composant Média 3D {#interacting-with-asset-inside-three-d-media-component}

Lorsqu’une page web est en mode **[!UICONTROL Édition]**, aucune interaction n’est possible avec une ressource 3D. Pour rendre la ressource interactive, vous pouvez utiliser la fonction **[!UICONTROL Aperçu]**. Vous pouvez ainsi afficher la page web dans l’éditeur de page avec un accès complet aux fonctionnalités du composant Média 3D.

>[!IMPORTANT]
>
>Vous ne pouvez accomplir cette tâche qu’après avoir ajouté un composant Média 3D à une page web et y avoir affecté une ressource 3D. Voir [Ajout du composant Média 3D à une page web](#adding-the-three-d-media-component-to-a-web-page) et [Affectation d’une ressource 3D à un composant Média 3D](#assigning-a-three-d-asset-to-the-component).

Voir aussi [Prévisualisation de ressources à l’aide de l’interface logicielle](/help/assets/dynamic-media/previewing-assets.md).

**Pour afficher et interagir avec une ressource 3D dans un composant Média 3D :**

1. Lorsqu’une page web est en mode **[!UICONTROL Édition]**, effectuez l’une des opérations suivantes :

   * Près de l’angle supérieur droit de la page, cliquez sur **[!UICONTROL Aperçu]** pour passer en mode **[!UICONTROL Aperçu]**.
   * Supprimez `/editor.html` de l’URL de la page dans le navigateur.

   ![Ressource 3D affichée dans le composant Média 3D](/help/assets/dynamic-media/assets/3d-asset-in-3d-mediaa.png)
Ressource 3D entièrement interactive affichée en mode **[!UICONTROL Aperçu]**.

1. En mode **[!UICONTROL Aperçu]**, effectuez l’une des opérations suivantes :

   | Mode | Description | Action de souris | Action de l’écran tactile |
   | --- | --- | --- | --- |
   | **Faire pivoter la caméra** | Faites tourner la vue autour de la scène 3D et des objets. | Clic gauche + glisser. | Appuyez avec un seul doigt + glisser. |
   | **Effectuer un panoramique avec la caméra** | Vous pouvez effectuer un panoramique vers la gauche, la droite, le haut ou le bas. | Clic droit + glisser. | Appuyez avec deux doigts + glisser. |
   | **Faire un zoom avec la caméra** | Se déplacer dans et hors des zones de la scène 3D. | Roue de défilement. | Appuyer avec deux doigts en les rapprochant. |
   | **Recentrer la caméra** | Recentrez la caméra sur un point d’un objet dans la scène 3D. | Double-cliquer. | Double-sélectionner. |
   | **Réinitialiser** | Près du coin inférieur droit de la page, sélectionnez l’icône Réinitialiser pour rétablir le point d’affichage cible au centre du fichier 3D. De plus, Réinitialiser rapproche ou éloigne l’angle de vue pour afficher la ressource dans son intégralité et à une taille raisonnable. |   |   |
   | **Mode Plein écran** | Pour passer en mode Plein écran, dans le coin inférieur droit de la page, sélectionnez l’icône Plein écran. |   |   |

## À propos de l’utilisation du composant Média 3D {#working-with-three-d-media-component}

Dynamic Media contient un composant Média 3D Dynamic Media que vous pouvez utiliser dans [!DNL Experience Manager Sites] pour activer l’affichage interactif de modèles 3D dans vos pages web.

* [Ajout du composant Média 3D au modèle de page](#adding-three-d-media-component-to-page-template)
* [Ajout du composant Média 3D à une page web](#adding-the-three-d-media-component-to-a-web-page)
   * [Facultatif- Configuration du composant Média 3D](#configuring-the-three-d-component)
* [Affectation d’une ressource 3D au composant Média 3D](#assigning-a-three-d-asset-to-the-component)

## Ajout du composant Média 3D au modèle de page {#adding-three-d-media-component-to-page-template}

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Général]** > **[!UICONTROL Modèles]**.
1. Accédez au modèle de page dans lequel vous souhaitez activer le composant 3D, puis sélectionnez le modèle.
1. Pour ouvrir le modèle, sélectionnez **[!UICONTROL Modifier]**.
1. Près de l’angle supérieur droit de la page, dans le menu déroulant, sélectionnez le mode **[!UICONTROL Structure]**, s’il n’est pas déjà actif.

   ![3d-media-component-structure](/help/assets/dynamic-media/assets/3d-media-component-structurea.png)

1. Pour sélectionner une zone vide et ouvrir sa barre d’outils associée, sélectionnez la zone vide dans la région **[!UICONTROL Conteneur de mise en page]**.
1. Dans la barre d’outils, sélectionnez l’icône **[!UICONTROL Politique]** pour ouvrir l’**[!UICONTROL Éditeur de politiques]**.
1. Dans la section **[!UICONTROL Propriétés]**, sous l’onglet **[!UICONTROL Composants autorisés]**, faites défiler l’écran jusqu’à **[!UICONTROL Dynamic Media]**, puis développez la liste et cochez la case **[!UICONTROL Média 3D]**.
1. Sélectionnez **[!UICONTROL Terminé]** pour enregistrer les modifications et fermer l’**[!UICONTROL Éditeur de politiques]**.

   Vous pouvez maintenant incorporer le composant Média 3D Dynamic Media dans toutes les pages qui utilisent ce modèle.

## Ajout du composant Média 3D à une page web {#adding-the-three-d-media-component-to-a-web-page}

Si vous utilisez [!DNL Experience Manager] comme système de gestion de contenu web, vous pouvez ajouter des ressources 3D à vos pages web au moyen du composant Média 3D.

Voir aussi [Ajout de ressources Dynamic Media à des pages](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).

1. Ouvrez [!DNL Experience Manager Sites] et sélectionnez la page web à laquelle vous souhaitez ajouter le composant Média 3D Dynamic Media.
1. Pour ouvrir la page dans l’éditeur de page, sélectionnez l’icône **[!UICONTROL Modifier]** (crayon). Assurez-vous que le mode d’**[!UICONTROL édition]** est sélectionné près de l’angle supérieur droit de la page.

   ![3d-media-component-add](/help/assets/dynamic-media/assets/3d-media-component-edita.png)

1. Dans la barre d’outils, sélectionnez l’icône du panneau latéral pour déclencher ou « activer » l’affichage du panneau.

1. Dans le panneau latéral, sélectionnez l’icône + pour ouvrir la liste **[!UICONTROL Composants]**.

   ![3d-media-component-drag-drop](/help/assets/dynamic-media/assets/3d-assets-filtera.png)

1. Faites glisser le composant **[!UICONTROL Média 3D]** depuis la liste **[!UICONTROL Composants]** vers l’emplacement de la page où vous souhaitez qu’apparaisse la visionneuse 3D.

Vous êtes maintenant prêt à affecter une ressource 3D au composant.

Consultez [Affecter une ressource 3D au composant Média 3D](#assigning-a-three-d-asset-to-the-component)

### Facultatif- Configuration du composant Média 3D {#configuring-the-three-d-component}

1. Dans l’éditeur de pages [!DNL Experience Manager Sites], sélectionnez le composant **[!UICONTROL Visionneuse de médias 3D]** déjà ajouté à la page.
1. Pour ouvrir la boîte de dialogue de configuration du composant, sélectionnez l’icône **[!UICONTROL Configuration]** (clé à molette).

   ![3d-media-component-config](/help/assets/dynamic-media/assets/3d-media-component-configa.png)

1. Dans la boîte de dialogue Média 3D, dans la liste déroulante Paramètre prédéfini de la visionneuse, sélectionnez **[!UICONTROL Dimensionnel]** pour affecter au composant le paramètre prédéfini de la visionneuse Dimensionnel.

   ![3d-media-component-edit-config](/help/assets/dynamic-media/assets/3d-media-component-edit-configa.png)

1. Dans l’angle supérieur droit, sélectionnez la coche pour enregistrer vos modifications.

## Affectation d’une ressource 3D au composant Média 3D {#assigning-a-three-d-asset-to-the-component}

Après avoir ajouté un composant Média 3D à une page web, vous pouvez lui affecter une ressource 3D.

Voir [Ajouter le composant Média 3D à une page web](#adding-the-three-d-media-component-to-a-web-page).

1. Dans l’éditeur de pages [!DNL Experience Manager Sites], cliquez sur l’icône **[!UICONTROL Ressources]** pour ouvrir **[!UICONTROL Ressources]** dans le panneau latéral.
1. Dans la liste déroulante, sélectionnez **[!UICONTROL 3D]** pour afficher uniquement les types de fichiers de ressources 3D.
1. Dans le panneau latéral, recherchez ou faites défiler l’écran jusqu’à atteindre la ressource 3D que vous souhaitez afficher sur la page en cours de modification.
1. Faites glisser la ressource 3D à partir du panneau latéral Ressources et déposez-le sur le composant **[!UICONTROL Média 3D]** que vous avez précédemment ajouté à la page.

   ![Affectation d’une ressource 3D au composant Média 3D](/help/assets/dynamic-media/assets/3d-asset-adda.png)

>[!NOTE]
>
>Lorsqu’une page web est en mode [!DNL Experience Manager Sites] **[!UICONTROL Édition]**, le composant Média 3D affiche la ressource 3D, mais aucune interaction avec elle n’est possible. Pour rendre la ressource interactive, vous pouvez utiliser la fonction **[!UICONTROL Aperçu]**. Vous pouvez ainsi afficher la page web dans l’éditeur de page avec un accès complet aux fonctionnalités du composant Média 3D.

## Publication de ressources 3D Dynamic Media statiques {#publishing-three-d-assets}

Dynamic Media accepte différents formats de fichiers 3D pris en charge en tant que *contenu statique* dans Dynamic Media. La notion de contenu statique signifie que vous pouvez charger et publier des ressources 3D, mais que les fonctions d’imagerie *dynamique* ou de retouche d’images associées à la ressource 3D ne sont pas prises en charge. En effet, Dynamic Media Imaging Server ne reconnaît pas les formats 3D. Ainsi, après avoir publié une ressource 3D dans Dynamic Media, vous disposez d’une URL instantanée que vous pouvez copier. L’URL de la ressource 3D suit la structure d’URL Dynamic Media habituelle. Cependant, vous ne pouvez pas modifier les paramètres de l’URL de la ressource, contrairement aux ressources d’images traditionnelles de Dynamic Media.

Voir également [Obtenir une URL pour une ressource statique](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-a-static-asset).

En **[!UICONTROL mode Carte]**, une petite icône en forme de globe apparaît directement sous le nom d’une ressource, et à gauche de ses informations de date et d’heure, pour indiquer qu’elle est publiée. Dans la vue **[!UICONTROL Liste]**, une colonne **[!UICONTROL Publié]** indique les ressources qui sont publiées et celles qui ne le sont pas.

Si vous utilisez [!DNL Experience Manager] comme système de gestion de contenu web, utilisez cette méthode de publication pour ajouter directement les ressources 3D Dynamic Media dans votre page web.

Voir aussi [Publication de ressources Dynamic Media](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

Voir aussi [Publier des pages](/help/sites-cloud/authoring/sites-console/publishing-pages.md).

**Pour publier des ressources 3D Dynamic Media statiques, suivez les étapes suivantes :**

1. Ouvrez une ressource 3D (format de fichier GLB, OBJ ou STL).
1. Sur la page de Détails, dans la barre d’outils, sélectionnez **[!UICONTROL Publication rapide]**.

   ![3d-asset-quick-publish](/help/assets/dynamic-media/assets/3d-asset-quick-publisha.png)

1. Sélectionnez **[!UICONTROL Fermer]** pour quitter la boîte de dialogue et revenir à la page des détails de la ressource.
1. Dans la liste déroulante située à gauche du nom de fichier de la ressource 3D, sélectionnez **[!UICONTROL Rendus]**.

   ![3d-asset-renditions](/help/assets/dynamic-media/assets/3d-asset-renditionsa.png)

1. Sélectionnez **[!UICONTROL original]**. Lorsqu’une ressource 3D est publiée (ou « activée »), le bouton **[!UICONTROL URL]** s’affiche à proximité de l’angle inférieur gauche de la page si toutes les conditions de la ressource 3D suivantes sont remplies :
   * La ressource 3D est dans un format pris en charge (GLB, OBJ, STL et USDZ).
   * La ressource 3D a été ingérée dans le système IPS (Image Production System).
   * La ressource 3D est publiée.

   ![3d-asset-url](/help/assets/dynamic-media/assets/3d-asset-urla.png)

1. Pour afficher l’URL de production directe de la ressource 3D que vous pouvez copier et utiliser dans des pages web, sélectionnez **[!UICONTROL URL]**.

### Autres méthodes de publication de ressources 3D Dynamic Media à l’aide de la visionneuse Dimensionnel {#alternate-publish-methods}

Utilisez les deux méthodes suivantes pour publier des ressources 3D Dynamic Media si *vous n’utilisez pas* comme système de gestion de contenu web.[!DNL Experience Manager]

* **[!UICONTROL URL]** : utilisez **[!UICONTROL URL]** si vous avez recours à un système de gestion de contenu web tiers et que vous souhaitez lier des ressources 3D Dynamic Media à vos pages web à l’aide de la visionneuse Dimensionnel.

  Voir [Liaison d’URL à une application web](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-an-asset).

* **[!UICONTROL Incorporer]** : utilisez l’option **[!UICONTROL Incorporer]** si vous souhaitez afficher une ressource 3D Dynamic Media incorporée dans une page web à l’aide de la visionneuse Dimensionnel. Vous copiez le code intégré dans le presse-papiers pour pouvoir le coller dans vos pages web. Vous ne pouvez pas modifier le code dans la boîte de dialogue **[!UICONTROL Incorporer]**.

  Voir [Intégration de la visionneuse de vidéos ou d’images Dynamic Media, ou de la visionneuse Dimensionnel dans une page web](/help/assets/dynamic-media/embed-code.md#embedding-the-video-or-image-viewer-on-a-web-page).
