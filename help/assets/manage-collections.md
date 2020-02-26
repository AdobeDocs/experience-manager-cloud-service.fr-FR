---
title: Gestion des collections de ressources numériques
description: Comprenez le concept de collecte dans Adobe Experience Manager Assets. Découvrez comment créer, gérer, modifier et partager des collections avec d’autres utilisateurs.
contentOwner: AG
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 8aa693387183e65434da300ccf08f394b48ed9ba

---


# Gestion des collections {#manage-collections}

Une collection est un ensemble de ressources dans les ressources d’Adobe Experience Manager. Vous pouvez utiliser des collections pour partager des ressources entre utilisateurs. Le jeu peut être une collection statique ou dynamique basée sur les résultats de la recherche.

Contrairement aux dossiers, une collection peut inclure des fichiers provenant de différents emplacements. Vous pouvez partager des ressources avec plusieurs utilisateurs dont les niveaux de privilèges sont différents (modification, affichage, etc.).

Vous pouvez partager plusieurs collections avec un utilisateur. Chaque collection contient des références aux ressources. L’intégrité du référentiel des ressources est préservées dans les collections.

Selon la façon dont elles rassemblent les ressources, les collections sont des types suivants :

* Collection contenant une liste de référence statique de ressources, de dossiers et d’autres collections.

* Collection dynamique qui comprend dynamiquement des ressources en fonction de critères de recherche.

## Accès à la console des collections {#navigate-the-collections-console}

Pour ouvrir la console **[!UICONTROL Collections]**, procédez comme suit :

Pour ouvrir les **[!UICONTROL collections]**, appuyez ou cliquez sur le logo d’Experience Manager. From the navigation page, go to **[!UICONTROL Assets]** > **[!UICONTROL Collections]**.

## Création d’une collection {#create-a-collection}

You can create a collection either with [static references](#create-a-collection-with-static-references) or based on a [search criteria-based filter](#create-a-smart-collection). Vous pouvez également créer une collection à partir d’une Lightbox.

### Create a collection with static references {#create-a-collection-with-static-references}

Vous pouvez créer une collection avec des références statiques, par exemple, une collection avec des références aux ressources, aux dossiers, aux collections, aux visionneuses à 360° et aux visionneuses d’images.

1. Accédez à la console **[!UICONTROL Collections]**.
1. From the toolbar, tap/click **[!UICONTROL Create]**.
1. Sur la page **[!UICONTROL Créer une collection]**, saisissez un titre et une description facultative pour la collection.
1. Ajoutez des membres à la collection et affectez les autorisations appropriées. Vous pouvez également sélectionner **[!UICONTROL Collection publique]** pour permettre à tous les utilisateurs d’accéder à la collection.

   >[!NOTE]
   >
   >Pour permettre aux membres de partager des collections avec d’autres utilisateurs, vous devez accorder les autorisations de lecture au groupe `dam-users` dans le chemin `home/users`. Give permission to the users at `/content/dam/collections` location to allow the users to view the Collections in pop up lists. Vous pouvez également intégrer l’utilisateur au groupe `dam-users`.

1. (Facultatif) Ajoutez une image de miniature pour la collection.
1. Appuyez/cliquez sur **[!UICONTROL Créer]**, puis sur **[!UICONTROL OK]** pour fermer la boîte de dialogue. Une collection avec le titre et les propriétés spécifiés s’ouvre dans la console Collections.

   >[!NOTE]
   >
   >Experience Manager Assets vous permet de créer des tâches de révision pour une collection, comme vous le faites pour créer des tâches de révision pour un dossier de ressources.

   Pour ajouter des ressources à la collection, accédez à l’interface utilisateur Assets. For details, see [Add assets to a collection](#add-assets-to-a-collection).

### Create collections using dropzone {#create-collections-using-dropzone}

Vous pouvez faire glisser des ressources de l’interface utilisateur Assets jusqu’à une collection. Vous pouvez également créer une copie d’une collection et faire glisser les ressources jusqu’à celle-ci.

1. Dans l’interface utilisateur Ressources, sélectionnez les ressources à ajouter à une collection.
1. Drag the assets to the **[!UICONTROL Drop in Collection]** zone. Vous pouvez également appuyer/cliquer sur l’icône **[!UICONTROL À la collection]** de la barre d’outils.
1. Sur la page **[!UICONTROL Ajouter à la collection]**, appuyez/cliquez sur l’icône **[!UICONTROL Créer une collection]** de la barre d’outils. Si vous souhaitez ajouter les ressources à une collection existante, sélectionnez-la dans la page, puis appuyez/cliquez sur **[!UICONTROL Ajouter]**. Par défaut, la collection la plus récemment mise à jour est sélectionnée.
1. Dans la boîte de dialogue **[!UICONTROL Créer une collection]**, indiquez le nom de la collection. Si vous souhaitez que la collection soit accessible à tous les utilisateurs, sélectionnez **[!UICONTROL Collection publique]**.
1. Tap/click **[!UICONTROL Continue]** to create the collection.

### Création d’une collection dynamique {#create-a-smart-collection}

Une collection dynamique utilise des critères de recherche pour rassembler les ressources de manière dynamique. Vous pouvez créer une collection dynamique en utilisant uniquement des fichiers ou en utilisant des fichiers et des dossiers.

1. Accédez à l’interface utilisateur d’Assets, puis appuyez/cliquez sur l’icône **[!UICONTROL Rechercher]**.
1. Saisissez le mot-clé dans la boîte de dialogue d’omni-recherche et appuyez sur entrée. Appuyez/cliquez sur l’icône GlobalNav pour afficher le panneau Filtres et pour appliquer un filtre de recherche à partir du panneau Recherche.
1. Dans la liste **[!UICONTROL Fichiers et dossiers]**, sélectionnez **[!UICONTROL Fichiers]**.
1. Appuyez/cliquez sur **[!UICONTROL Enregistrer la collection dynamique]**.
1. Spécifiez le nom de la collection. Sélectionnez **[!UICONTROL Public]** pour ajouter le groupe Utilisateurs DAM avec le rôle Observateur à la collection dynamique.

   >[!NOTE]
   >
   >If you select **[!UICONTROL Public]**, the smart collection becomes available to everyone with the Owner role after you create it. Si vous désactivez la case à cocher **[!UICONTROL Public]**, le groupe Utilisateurs DAM n’est plus associé à la collection dynamique.

1. Appuyez/cliquez sur **[!UICONTROL Enregistrer]** pour créer la collection dynamique, puis fermez la boîte de message pour terminer le processus. La nouvelle collection dynamique est également ajoutée à la liste **[!UICONTROL Recherches enregistrées]**.
Le libellé du bouton **[!UICONTROL Créer une sélection intelligente]** devient **[!UICONTROL Modifier la sélection intelligente]**. Pour modifier les paramètres de la collecte dynamique, sélectionnez **[!UICONTROL Fichiers]** dans la liste **[!UICONTROL Fichiers et dossiers]**. Appuyez/cliquez ensuite sur le bouton **[!UICONTROL Modifier la sélection intelligente]**.

## Add assets to a collection {#add-assets-to-a-collection}

Vous pouvez ajouter des ressources à une collection qui comporte une liste de ressources ou de dossiers référencés.

>[!NOTE]
>
>Les collections dynamiques utilisent une requête de recherche pour rassembler les ressources. Pour cette raison, les références statiques aux ressources et dossiers ne s’appliquent pas à celles-ci.

1. Dans l’IU AEM, accédez à l’emplacement de la ressource que vous souhaitez ajouter à une collection.
1. Sélectionnez la ressource et appuyez/cliquez sur l’icône **[!UICONTROL À la collection]** dans la barre d’outils. Alternatively, you can drag the asset to the **[!UICONTROL Drop in Collection]** zone. Release the mouse button when the drop zone becomes active and its label changes to **[!UICONTROL Drop to Add]**.
1. In the **[!UICONTROL Add To Collection]** page, select the collection to which you want to add the asset.
1. Appuyez/cliquez sur **[!UICONTROL Ajouter]**, puis fermez le message de confirmation. La ressource est ajoutée à la collection.

## Modification d’une collection dynamique {#edit-a-smart-collection}

Smart collections are built by saving a search so you can alter their content by modifying the search parameters of the [saved search](#saved-searches).

1. In the Assets user interface, tap/click the **[!UICONTROL Search]** icon from the toolbar.
1. Avec le curseur dans la zone Omnisearch, appuyez sur la touche Entrée.
1. Appuyez/cliquez sur l’icône de navigation globale pour afficher le panneau Filtres.
1. Dans la liste **[!UICONTROL Recherches enregistrées]**, sélectionnez la collection dynamique à modifier. Le panneau Rechercher affiche les filtres configurés pour la recherche enregistrée.
1. Dans la liste **[!UICONTROL Fichiers et dossiers]**, sélectionnez **[!UICONTROL Fichiers]**.
1. Modifiez un ou plusieurs filtres selon vos besoins. Tap/click **[!UICONTROL Edit Smart Collection]**. Vous pouvez également modifier le nom de la collection dynamique.
1. Appuyez/cliquez sur **[!UICONTROL Enregistrer]**. La boîte de dialogue **[!UICONTROL Modif. collection dynam.]** s’affiche.
1. Appuyez/cliquez sur **[!UICONTROL Remplacer]** pour remplacer la collection dynamique d’origine par la collection modifiée. Sinon, sélectionnez **[!UICONTROL Enregistrer sous]** pour enregistrer la collection modifiée séparément.
1. Dans la boîte de dialogue de confirmation, appuyez/cliquez sur **[!UICONTROL Enregistrer]** pour terminer le processus.

## View and edit collection metadata {#view-and-edit-collection-metadata}

Les métadonnées de collection incluent les données sur la collection, notamment toute balise qui est ajoutée.

1. From the Collections console, select a collection and tap/click the **[!UICONTROL Properties]** icon from the toolbar.
1. Dans la page **[!UICONTROL Métadonnées de la collection]**, affichez les métadonnées de la collection à partir des onglets **[!UICONTROL Simple]** et **Avancé**.
1. Modify the metadata, as necessary, and then tap/click **[!UICONTROL Save &amp; Close]** from the toolbar to save the changes.

### Edit collection metadata in bulk {#edit-collection-metadata-in-bulk}

Vous pouvez modifier simultanément les métadonnées de plusieurs collections. Cette fonctionnalité vous aide à répliquer rapidement des métadonnées communes dans plusieurs collections.

1. Dans la console Collections, sélectionnez au moins deux collections dont vous souhaitez modifier les métadonnées.
1. From the toolbar, tap/click the **[!UICONTROL Properties]** icon.
1. Dans la page **[!UICONTROL Métadonnées de collection]**, modifiez les métadonnées sous les onglets **[!UICONTROL Simple]** et **[!UICONTROL Avancé]**, si nécessaire.
1. Tap/click **[!UICONTROL Save &amp; Close]** from the toolbar, and then close the confirmation dialog to complete the process.
1. Pour ajouter les nouvelles métadonnées avec les métadonnées existantes, sélectionnez le mode **[!UICONTROL Ajouter]**. Si vous ne sélectionnez pas cette option, les nouvelles métadonnées remplacent les métadonnées existantes dans les champs. Appuyez/cliquez sur **[!UICONTROL Envoyer]**.

   >[!NOTE]
   >
   >Le mode d’ajout fonctionne uniquement pour les champs qui peuvent contenir plusieurs valeurs. Pour les champs qui ne peuvent contenir qu’une seule valeur, les nouvelles métadonnées ne sont pas ajoutées à la valeur existante dans le champ, même si vous sélectionnez le mode **[!UICONTROL Ajouter]**.

## Recherche {#searching}

The Search feature within Collections supports both [Search for collections](#search-collections) and [Search for assets within a Collection](#search-within-collections).

### Rechercher des collections {#search-collections}

Vous pouvez effectuer des recherches dans des collections à partir de la console Collections. Lorsque vous effectuez des recherches avec des mots-clés dans la zone Omnisearch, AEM Assets recherche les noms des collections, les métadonnées et les balises ajoutées aux collections.

Si vous recherchez des collections à partir du niveau supérieur, seules les collections individuelles sont renvoyées dans les résultats de recherche. Les ressources ou dossiers à l’intérieur des collections sont exclus. Dans tous les autres cas (par exemple, dans une collection individuelle ou dans une hiérarchie de dossiers), tous les fichiers, dossiers et collections appropriés sont renvoyés.

### Rechercher dans les collections {#search-within-collections}

Dans la console Collections, appuyez/cliquez sur une collection pour l’ouvrir.

Dans une collection, la recherche se limite aux ressources (ainsi qu’aux balises et métadonnées) de la collection en cours d’affichage. Lorsque vous effectuez une recherche dans un dossier, tous les fichiers correspondants et les dossiers enfants du dossier actif sont renvoyés. Lorsque vous effectuez une recherche dans une collection, seuls les fichiers, dossiers et autres collections correspondant aux membres directs de la collection sont renvoyés.

## Modifier les paramètres de la collection {#edit-collection-settings}

Vous pouvez modifier les paramètres d’une collection, tels que le titre et la description, ou ajouter des membres à une collection.

1. Select a collection, and tap/click the **[!UICONTROL Settings]** icon in the toolbar. Vous pouvez également utiliser l’action rapide **[!UICONTROL Paramètres]** à partir de la miniature de la collection.
1. Modifiez les paramètres de la collection dans la page **[!UICONTROL Paramètres de la collection]**. Par exemple, modifiez le titre, les descriptions, les membres et les autorisations de la collection, comme expliqué dans la section [Ajouter des collections](#create-a-collection).
1. Tap/click **[!UICONTROL Save]** to save the changes.

## Suppression d’une collection {#delete-a-collection}

1. Dans la console Collections, sélectionnez une ou plusieurs collections et appuyez/cliquez sur l’icône Supprimer dans la barre d’outils.
1. In the dialog, tap/click **[!UICONTROL Delete]** to confirm the delete action.

   >[!NOTE]
   >
   >You can also delete Smart collections by [delete saved searches](#saved-searches).

## Téléchargement d’une collection {#download-a-collection}

Lorsque vous téléchargez une collection, l’intégralité de la hiérarchie des ressources de la collection est téléchargée, y compris les dossiers et les collections enfants.

1. Dans la console Collections, sélectionnez une ou plusieurs collections à télécharger.
1. Dans la barre d’outils, appuyez/cliquez sur l’icône de téléchargement.
1. Dans la boîte de dialogue **[!UICONTROL Télécharger]**, appuyez/cliquez sur **[!UICONTROL Télécharger]**. Si vous souhaitez télécharger les rendus des ressources dans la collection, sélectionnez **[!UICONTROL Rendus]**. Sélectionnez l’option **[!UICONTROL Courrier électronique]** pour envoyer une notification électronique au propriétaire de la collection.

   Lorsque vous sélectionnez une collection à télécharger, l’ensemble de la hiérarchie de dossiers sous cette collection est téléchargé. To include each collection you download (including assets in child collections nested under the parent collection) in an individual folder, select **[!UICONTROL Create separate folder for each asset]**.

## Edit metadata properties of multiple collections {#editing-metadata-properties-of-multiple-collections}

Les ressources d’Adobe Enterprise Manager (AEM) vous permettent de modifier en bloc les métadonnées de nombreuses collections. Utilisez la page [!UICONTROL Propriétés] pour effectuer des modifications de métadonnées sur plusieurs collections, par exemple pour modifier les propriétés des métadonnées en une valeur commune ou ajouter ou modifier des balises.

To customize the metadata [!UICONTROL Properties] page, including adding, modifying, deleting metadata properties, use the Schema editor.

>[!NOTE]
>
>Les méthodes de modification en masse fonctionnent pour les ressources disponibles dans une collection. Pour les ressources disponibles dans plusieurs dossiers ou correspondant à un critère commun, il est possible de mettre à jour [les métadonnées en masse après une recherche](/help/assets/search-assets.md#metadataupdates).

1. Dans la console des collections, sélectionnez les collections à modifier.
1. From the toolbar, tap/click **[!UICONTROL Properties]** to open the [!UICONTROL Properties] page for the selected collections.
1. Modifiez les propriétés de métadonnées des collections sélectionnées dans les différents onglets.

   >[!NOTE]
   >
   >Les métadonnées que vous ajoutez pour les collections sélectionnées remplacent les métadonnées précédentes de ces collections, à l’exception des balises. Any tags you add in the **[!UICONTROL Tags]** field, are appended to the existing list of tags in the metadata.

1. Pour afficher les propriétés de métadonnées associées à une collection spécifique, désélectionnez les autres collections dans la liste des collections. Les champs de l’éditeur de métadonnées sont renseignés avec les métadonnées de la collection particulière.

   >[!NOTE]
   >
   >* Dans la page des propriétés de collection, vous pouvez supprimer des collections de la liste des collections en les désélectionnant. La liste des collections contient toutes les collections sélectionnées par défaut. Les métadonnées des collections que vous supprimez ne sont pas mises à jour.
   >* At the top of the list, select the check box near **[!UICONTROL Title]** to toggle between selecting the collections and clearing the list.


1. Enregistrez les modifications.

## Création de collections imbriquées {#create-nested-collections}

Vous pouvez ajouter une collection à une autre collection, créant ainsi une collection imbriquée.

1. From the Collections console, select the desired collection or group of collections, and tap or click **[!UICONTROL To Collection]** in the toolbar.
1. Sur la page **[!UICONTROL Ajouter à la collection]**, sélectionnez la collection à laquelle vous souhaitez ajouter la collection.

   >[!NOTE]
   >
   >The most recently updated collection is selected by default in the **[!UICONTROL Add To Collection]** page.

1. Appuyez/cliquez sur **[!UICONTROL Ajouter]**. Un message confirme l’ajout de la collection à la collection cible sur la page **[!UICONTROL Sélectionner la destination]**. Fermez le message pour terminer le processus.

>[!NOTE]
>
>Les collections dynamiques ne peuvent pas être imbriquées. En d’autres termes, elles ne peuvent pas comporter d’autres collections.

## Recherches enregistrées {#saved-searches}

L’interface utilisateur d’Assets vous permet de rechercher ou de filtrer des ressources en fonction de règles, de critères de recherche ou de facettes de recherche personnalisées. Si vous les enregistrez en tant que **[!UICONTROL recherches enregistrées]**, vous pourrez y accéder ultérieurement à partir de la liste **[!UICONTROL Recherches enregistrées]** du panneau Filtre. La création d’une recherche enregistrée crée également une collection dynamique.

Les recherches enregistrées sont créées lorsque vous créez une collection dynamique. Les collections dynamiques sont automatiquement ajoutées à la liste **[!UICONTROL Recherches enregistrées]**. La requête Recherches enregistrées pour la collection est enregistrée dans la `dam:query` propriété CRXDE à l’emplacement relatif `/content/dam/collections/`.

>[!NOTE]
>
>Vous pouvez partager les collections dynamiques comme s’il s’agissait de collections statiques.

La modification des recherches enregistrées est identique à celle des collections dynamiques. For details, see [Edit a smart collection](#edit-a-smart-collection).

Pour supprimer des recherches enregistrées, procédez comme suit :

1. Dans l’interface utilisateur Ressources, appuyez/cliquez sur l’icône de recherche dans la barre d’outils.

1. Avec le curseur dans le champ Omnisearch, appuyez sur la touche Entrée.
1. Appuyez ou cliquez sur l’icône de navigation globale afin d’afficher le panneau Filtres.
1. Dans la liste **[!UICONTROL Recherches enregistrées]**, appuyez/cliquez sur **[!UICONTROL Supprimer]** en regard de la collecte dynamique à supprimer.
1. In the dialog, tap/click **[!UICONTROL Delete]** to delete the saved search.

## Execute a workflow on a collection {#run-a-workflow-on-a-collection}

Vous pouvez exécuter un processus pour les ressources d’une collection. Si la collection contient des collections imbriquées, le processus s’exécute également sur les ressources de ces dernières. Toutefois, si la collection et les collections imbriquées contiennent des ressources en double, le processus ne s’exécute qu’une seule fois pour ces ressources.

1. Dans la console Collections, sélectionnez une collection sur laquelle exécuter un processus.
1. Tap/click the GlobalNav icon, and choose **[!UICONTROL Timeline]** from the list.
1. Dans le journal, cliquez ou appuyez sur l’icône en forme de signe circonflexe située en bas, puis appuyez/cliquez sur **[!UICONTROL Démarrer le processus]**.
1. Dans la section **[!UICONTROL Démarrer le processus]**, sélectionnez un modèle de processus dans la liste. Par exemple, sélectionnez le modèle **[!UICONTROL Ressources de mise à jour de DAM]**.
1. Saisissez un titre pour le workflow, puis appuyez/cliquez sur **[!UICONTROL Démarrer]**.
1. Dans la boîte de dialogue, appuyez/cliquez sur **[!UICONTROL Poursuivre]**. Le processus s’exécute sur toutes les ressources de la collection.

>[!MORELIKETHIS]
>
>* [Création d’une tâche de révision pour les collections](/help/assets/bulk-approval.md)

