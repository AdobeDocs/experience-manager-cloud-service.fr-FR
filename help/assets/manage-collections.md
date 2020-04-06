---
title: Gestion des collections de ressources numériques
description: Comprenez le concept de collecte dans Adobe Experience Manager Assets. Découvrez comment créer, gérer, modifier et partager des collections avec d’autres utilisateurs.
contentOwner: AG
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 8aa693387183e65434da300ccf08f394b48ed9ba

---


# Gestion des collections {#manage-collections}

Une collection est un ensemble de ressources dans les ressources d’Adobe Experience Manager. Vous pouvez utiliser des collections pour partager des ressources entre utilisateurs. Il peut s’agir d’une collection statique ou d’une collection dynamique basée sur les résultats de la recherche.

Contrairement aux dossiers, une collection peut inclure des fichiers provenant de différents emplacements. Vous pouvez partager des ressources avec plusieurs utilisateurs dont les niveaux de privilèges sont différents (modification, affichage, etc.).

Vous pouvez partager plusieurs collections avec un utilisateur. Chaque collection contient des références aux ressources. L’intégrité du référentiel des ressources est préservée dans les collections.

Selon la façon dont elles rassemblent les ressources, les collections sont des types suivants :

* Collection contenant une liste de référence statique de ressources, dossiers et autres collections

* Collection dynamique qui comprend dynamiquement des ressources en fonction de critères de recherche.

## Access the collections console {#navigate-the-collections-console}

Pour ouvrir la console **[!UICONTROL Collections]**, procédez comme suit :

Pour ouvrir les **[!UICONTROL collections]**, appuyez ou cliquez sur le logo d’Experience Manager. From the navigation page, go to **[!UICONTROL Assets]** > **[!UICONTROL Collections]**.

## Création d’une collection {#create-a-collection}

Vous pouvez créer une collection contenant des [références statiques](#create-a-collection-with-static-references) ou reposant sur un [filtre de critères de recherche](#create-a-smart-collection). Vous pouvez également créer une collection à partir d’une Lightbox.

### Création d’une collection avec des références statiques {#create-a-collection-with-static-references}

Vous pouvez créer une collection avec des références statiques, par exemple, une collection avec des références aux ressources, aux dossiers, aux collections, aux visionneuses à 360° et aux visionneuses d’images.

1. Accédez à la console **[!UICONTROL Collections]**.
1. Dans la barre d’outils, appuyez/cliquez sur **[!UICONTROL Créer]**.
1. Sur la page **[!UICONTROL Créer une collection]**, saisissez un titre et une description facultative pour la collection.
1. Ajoutez des membres à la collection et affectez les autorisations appropriées. Vous pouvez également sélectionner **[!UICONTROL Collection publique]** pour permettre à tous les utilisateurs d’accéder à la collection.

   >[!NOTE]
   >
   >Pour permettre aux membres de partager des collections avec d’autres utilisateurs, vous devez accorder les autorisations de lecture au groupe `dam-users` dans le chemin `home/users`. Donnez l’autorisation aux utilisateurs à l’emplacement `/content/dam/collections` afin de leur permettre d’afficher les collections dans les listes contextuelles. Vous pouvez également intégrer l’utilisateur au groupe `dam-users`.

1. (Facultatif) Ajoutez une image de miniature pour la collection.
1. Appuyez/cliquez sur **[!UICONTROL Créer]**, puis sur **[!UICONTROL OK]** pour fermer la boîte de dialogue. Une collection avec le titre et les propriétés spécifiés s’ouvre dans la console Collections.

   >[!NOTE]
   >
   >Experience Manager Assets vous permet de créer un de révision pour une collection similaire à la manière dont vous créez des  de révision pour un dossier de ressources.

   Pour ajouter des ressources à la collection, accédez à l’interface utilisateur Assets. Pour plus d’informations, voir [Ajout de ressources à une collection](#add-assets-to-a-collection).

### Create collections using dropzone {#create-collections-using-dropzone}

Vous pouvez faire glisser des ressources de l’interface utilisateur Assets jusqu’à une collection. Vous pouvez également créer une copie d’une collection et faire glisser les ressources jusqu’à celle-ci.

1. Dans l’interface utilisateur Ressources, sélectionnez les ressources à ajouter à une collection.
1. Faites glisser les ressources jusqu’à la zone **[!UICONTROL Déposer dans la collection]**. Vous pouvez également appuyer/cliquer sur l’icône **[!UICONTROL À la collection]** de la barre d’outils.
1. Sur la page **[!UICONTROL Ajouter à la collection]**, appuyez/cliquez sur l’icône **[!UICONTROL Créer une collection]** dans la barre d’outils. Si vous souhaitez ajouter les ressources à une collection existante, sélectionnez-la dans la page, puis appuyez/cliquez sur **[!UICONTROL Ajouter]**. Par défaut, la collection la plus récemment mise à jour est sélectionnée.
1. Dans la boîte de dialogue **[!UICONTROL Créer une collection]**, indiquez le nom de la collection. Si vous souhaitez que la collection soit accessible à tous les utilisateurs, sélectionnez **[!UICONTROL Collection publique]**.
1. Appuyez/cliquez sur **[!UICONTROL Continuer]** pour créer la collection.

### Création d’une collection dynamique {#create-a-smart-collection}

Une collection dynamique utilise des critères de recherche pour rassembler les ressources de manière dynamique. Vous pouvez créer une collection dynamique en utilisant uniquement des fichiers ou en utilisant des fichiers et des dossiers.

1. Accédez à l’IU d’Assets et appuyez/cliquez sur l’icône **[!UICONTROL Rechercher]**.
1. Saisissez le mot-clé dans la boîte de dialogue d’omni-recherche et appuyez sur entrée. Appuyez/cliquez sur l’icône GlobalNav pour afficher le panneau Filtres et pour appliquer un filtre de recherche à partir du panneau Recherche.
1. Dans la liste **[!UICONTROL Fichiers et dossiers]**, sélectionnez **[!UICONTROL Fichiers]**.
1. Appuyez/cliquez sur **[!UICONTROL Enregistrer la collection dynamique]**.
1. Spécifiez le nom de la collection. Sélectionnez **[!UICONTROL Public]** pour ajouter le groupe Utilisateurs DAM avec le rôle Observateur à la collection dynamique.

   >[!NOTE]
   >
   >Si vous sélectionnez **[!UICONTROL Public]**, la collection dynamique est disponible pour chaque personne possédant le rôle de propriétaire une fois que vous la créez. Si vous désactivez la case à cocher **[!UICONTROL Public]**, le groupe Utilisateurs DAM n’est plus associé à la collection dynamique.

1. Appuyez/cliquez sur **[!UICONTROL Enregistrer]** pour créer la collection dynamique, puis fermez le message afin de terminer le processus. La nouvelle collection dynamique est également ajoutée à la liste **[!UICONTROL Recherches enregistrées]**.
Le libellé du bouton **[!UICONTROL Créer une collection dynamique]** se transforme en **[!UICONTROL Modifier la collection dynamique]**. Pour modifier les paramètres de la collection dynamique, sélectionnez **[!UICONTROL Fichiers]** dans la liste **[!UICONTROL Fichiers et dossiers]**. Ensuite, appuyez/cliquez sur le bouton **[!UICONTROL Modif. collection dynam]**.

## Ajout de ressources à une collection {#add-assets-to-a-collection}

Vous pouvez ajouter des ressources à une collection qui comporte une liste de ressources ou de dossiers référencés.

>[!NOTE]
>
>Les collections dynamiques utilisent une requête de recherche pour rassembler les ressources. Pour cette raison, les références statiques aux ressources et dossiers ne s’appliquent pas à celles-ci.

1. Dans l’IU AEM, accédez à l’emplacement de la ressource que vous souhaitez ajouter à une collection.
1. Sélectionnez la ressource et appuyez/cliquez sur l’icône **[!UICONTROL À la collection]** dans la barre d’outils. Vous pouvez également faire glisser la ressource jusqu’à la zone **[!UICONTROL Déposer dans la collection]**. Relâchez le bouton de la souris lorsque la zone de dépôt devient active et que le libellé se transforme en **[!UICONTROL Déposer pour ajouter]**.
1. Sur la page **[!UICONTROL Ajouter à la collection]**, sélectionnez la collection à laquelle vous souhaitez ajouter la ressource.
1. Appuyez/cliquez sur **[!UICONTROL Ajouter]**, puis fermez le message de confirmation. La ressource est ajoutée à la collection.

## Modification d’une collection dynamique {#edit-a-smart-collection}

Les collections dynamiques sont créées en enregistrant une recherche afin que vous puissiez modifier leur contenu en changeant les paramètres de recherche de la [recherche enregistrée](#saved-searches).

1. Dans l’IU d’Assets, appuyez/cliquez sur l’icône **[!UICONTROL Rechercher]** de la barre d’outils.
1. Avec le curseur dans la zone Omnisearch, appuyez sur la touche Entrée.
1. Appuyez/cliquez sur l’icône de navigation globale pour afficher le panneau Filtres.
1. Dans la liste **[!UICONTROL Recherches enregistrées]**, sélectionnez la collection dynamique que vous souhaitez modifier. Le panneau de recherche affiche les filtres configurés pour la recherche enregistrée.
1. Dans la liste **[!UICONTROL Fichiers et dossiers]**, sélectionnez **[!UICONTROL Fichiers]**.
1. Modifiez un ou plusieurs filtres selon vos besoins. Appuyez/cliquez sur **[!UICONTROL Modif. collection dynam]**. Vous pouvez également modifier le nom de la collection dynamique.
1. Appuyez/cliquez sur **[!UICONTROL Enregistrer]**. La boîte de dialogue **[!UICONTROL Modif. collection dynam.]** s’affiche.
1. Appuyez/cliquez sur **[!UICONTROL Remplacer]** pour remplacer la collection dynamique d’origine par la collection modifiée. Sinon, sélectionnez **[!UICONTROL Enregistrer sous]** pour enregistrer la collection modifiée séparément.
1. Dans la boîte de dialogue de confirmation, appuyez/cliquez sur **[!UICONTROL Enregistrer]** pour terminer le processus.

## Affichage et modification des métadonnées {#view-and-edit-collection-metadata}

Les métadonnées de collection incluent les données sur la collection, notamment toute balise qui est ajoutée.

1. Dans la console Collections, sélectionnez une collection, puis appuyez/cliquez sur l’icône **[!UICONTROL Propriétés]** dans la barre d’outils.
1. Sur la page **[!UICONTROL Métadonnées de collection]**, affichez les métadonnées de collection à partir des onglets **[!UICONTROL De base]** et **Avancé**.
1. Modifiez les métadonnées suivant les besoins, puis appuyez/cliquez sur l’icône **[!UICONTROL Enregistrer et fermer]** de la barre d’outils pour enregistrer les modifications.

### Modification en masse des métadonnées de collection {#edit-collection-metadata-in-bulk}

Vous pouvez modifier simultanément les métadonnées de plusieurs collections. Cette fonctionnalité vous aide à répliquer rapidement des métadonnées communes dans plusieurs collections.

1. Dans la console Collections, sélectionnez au moins deux collections dont vous souhaitez modifier les métadonnées.
1. Dans la barre d’outils, appuyez/cliquez sur l’icône **[!UICONTROL Propriétés]**.
1. Sur la page **[!UICONTROL Métadonnées de collection]**, modifiez les métadonnées sous **[!UICONTROL De base]** et **[!UICONTROL Avancé]**, selon les besoins.
1. Appuyez/cliquez sur **[!UICONTROL Enregistrer et fermer]** dans la barre d’outils, puis fermez la boîte de dialogue de confirmation pour terminer le processus.
1. Pour ajouter les nouvelles métadonnées avec les métadonnées existantes, sélectionnez le mode **[!UICONTROL Ajouter]**. Si vous ne sélectionnez pas cette option, les nouvelles métadonnées remplacent les métadonnées existantes dans les champs. Appuyez/cliquez sur **[!UICONTROL Envoyer]**.

   >[!NOTE]
   >
   >Le mode d’ajout fonctionne uniquement avec les champs pouvant contenir plusieurs valeurs. Pour les champs ne pouvant contenir qu’une seule valeur, les nouvelles métadonnées ne sont pas ajoutées à la valeur existante dans le champ, même si vous sélectionnez **[!UICONTROL Mode d’ajout]**.

## Recherche {#searching}

La fonctionnalité Recherche des collections prend en charge à la fois la [recherche de collections](#search-collections) et la [recherche de ressources dans une collection](#search-within-collections).

### Recherche de collections {#search-collections}

Vous pouvez effectuer des recherches dans des collections à partir de la console Collections. Lorsque vous effectuez des recherches avec des mots-clés dans la zone Omnisearch, AEM Assets recherche les noms des collections, les métadonnées et les balises ajoutées aux collections.

Si vous recherchez des collections à partir du niveau supérieur, seules les collections individuelles sont renvoyées dans les résultats de recherche. Les ressources ou dossiers à l’intérieur des collections sont exclus. Dans tous les autres cas (par exemple, dans une collection individuelle ou dans une hiérarchie de dossiers), tous les fichiers, dossiers et collections appropriés sont renvoyés.

### Recherche dans les collections {#search-within-collections}

Dans la console Collections, appuyez/cliquez sur une collection pour l’ouvrir.

Dans une collection, la recherche AEM Assets se limite aux ressources (ainsi qu’aux balises et métadonnées) de la collection en cours d’affichage. Lorsque vous effectuez une recherche dans un dossier, toutes les ressources correspondantes et les dossiers enfants du dossier actif sont renvoyés. Lorsque vous effectuez une recherche dans une collection, seuls les ressources, dossiers et autres collections correspondant aux membres directs de la collection sont renvoyés.

## Modification des paramètres d’une collection {#edit-collection-settings}

Vous pouvez modifier les paramètres d’une collection, tels que le titre et la description, ou ajouter des membres à une collection.

1. Sélectionnez une collection et appuyez/cliquez sur l’icône **[!UICONTROL Paramètres]** dans la barre d’outils. Vous pouvez également utiliser l’action rapide **[!UICONTROL Paramètres]** à partir de la miniature de la collection.
1. Modifiez les paramètres de la collection sur la page **[!UICONTROL Paramètres de la collection]**. Vous pouvez par exemple modifier le titre, les descriptions, les membres et les autorisations de la collection, comme décrit dans [Ajout de collections](#create-a-collection).
1. Appuyez/cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les modifications.

## Suppression d’une collection {#delete-a-collection}

1. Dans la console Collections, sélectionnez une ou plusieurs collections, puis appuyez/cliquez sur l’icône de suppression dans la barre d’outils.
1. Dans la boîte de dialogue, appuyez/cliquez sur **[!UICONTROL Supprimer]** pour confirmer la suppression.

   >[!NOTE]
   >
   >Vous pouvez également supprimer les collections dynamiques en [supprimant les recherches enregistrées](#saved-searches).

## Téléchargement d’une collection {#download-a-collection}

Lorsque vous téléchargez une collection, la hiérarchie complète des ressources dans la collection est téléchargée, y compris les dossiers et les collections enfants.

1. Dans la console Collections, sélectionnez une ou plusieurs collections à télécharger.
1. Dans la barre d’outils, appuyez/cliquez sur l’icône de téléchargement.
1. Dans la boîte de dialogue **[!UICONTROL Télécharger]**, appuyez/cliquez sur **[!UICONTROL Télécharger]**. Si vous souhaitez télécharger les rendus des ressources dans la collection, sélectionnez **[!UICONTROL Rendus]**. Sélectionnez l’option **[!UICONTROL Courrier électronique]** pour envoyer une notification électronique au propriétaire de la collection.

   Lorsque vous sélectionnez une collection à télécharger, l’ensemble de la hiérarchie de dossiers sous cette collection est téléchargé. Pour inclure chaque collection que vous téléchargez (y compris les ressources figurant dans des collections enfant imbriquées dans la collection parent) dans un dossier individuel, sélectionnez **[!UICONTROL Créer un dossier distinct pour chaque ressource]**.

## Modification des propriétés de métadonnées de plusieurs collections {#editing-metadata-properties-of-multiple-collections}

Adobe Enterprise Manager (AEM) Assets vous permet de modifier en masse les métadonnées de nombreuses collections. Utilisez la page [!UICONTROL Propriétés] pour effectuer des modifications sur les métadonnées sur plusieurs collections, par exemple pour modifier les propriétés des métadonnées en une valeur commune, ainsi que pour ajouter ou modifier des balises.

Pour personnaliser la page [!UICONTROL Propriétés] de métadonnées, notamment ajouter, modifier et supprimer des propriétés de métadonnées, utilisez l’éditeur de schéma.

>[!NOTE]
>
>Les méthodes de modification en masse fonctionnent pour les ressources disponibles dans une collection. Pour les ressources disponibles dans plusieurs dossiers ou correspondant à un critère commun, il est possible de mettre à jour [les métadonnées en masse après une recherche](/help/assets/search-assets.md#metadataupdates).

1. Dans la console Collections, sélectionnez les collections à modifier.
1. Sur la barre d’outils, appuyez/cliquez sur **[!UICONTROL Propriétés]** pour ouvrir la page [!UICONTROL Propriétés] des collections sélectionnées.
1. Modifiez les propriétés de métadonnées des collections sélectionnées dans les différents onglets.

   >[!NOTE]
   >
   >Les métadonnées que vous ajoutez pour les collections sélectionnées remplacent les métadonnées précédentes de ces collections, à l’exception des balises. Toutes les balises que vous ajoutez dans le champ **[!UICONTROL Balises]** sont ajoutées à la liste existante des balises dans les métadonnées.

1. Pour afficher les propriétés de métadonnées associées à une collection spécifique, désélectionnez les autres collections dans la liste des collections. Les champs de l’éditeur de métadonnées sont renseignés avec les métadonnées de la collection particulière.

   >[!NOTE]
   >
   >* Dans la page des propriétés de collection, vous pouvez supprimer des collections de la liste des collections en les désélectionnant. La liste des collections contient toutes les collections sélectionnées par défaut. Les métadonnées des collections que vous supprimez ne sont pas mises à jour.
   >* En haut de la liste, cochez la case située en regard de l’option **[!UICONTROL Titre]** pour passer de la sélection des collections à l’effacement de la liste, et inversement.


1. Enregistrez les modifications.

## Création de collections imbriquées {#create-nested-collections}

Vous pouvez ajouter une collection à une autre collection, créant ainsi une collection imbriquée.

1. From the Collections console, select the desired collection or group of collections, and tap or click **[!UICONTROL To Collection]** in the toolbar.
1. Sur la page **[!UICONTROL Ajouter à la collection]**, sélectionnez la collection à laquelle vous souhaitez ajouter la collection.

   >[!NOTE]
   >
   >La collection mise le plus récemment à jour est sélectionnée par défaut sur la page **[!UICONTROL Ajouter à la collection]**.

1. Appuyez/cliquez sur **[!UICONTROL Ajouter]**. Un message confirme l’ajout de la collection à la collection cible sur la page **[!UICONTROL Sélectionner la destination]**. Fermez le message pour terminer le processus.

>[!NOTE]
>
>Les collections dynamiques ne peuvent pas être imbriquées. En d’autres termes, elles ne peuvent pas comporter d’autres collections.

## Recherches enregistrées    {#saved-searches}

Dans l’interface utilisateur d’Assets, vous pouvez rechercher ou filtrer des ressources selon des règles, critères de recherche ou facettes de recherche personnalisées. Si vous enregistrez ces éléments en tant que **[!UICONTROL recherches enregistrées]**, vous pouvez y accéder ultérieurement à partir de la liste **[!UICONTROL Recherches enregistrées]** du panneau Filtrer. La création d’une recherche enregistrée entraîne celle d’une collection dynamique.

Les recherches enregistrées sont créées lorsque vous créez une collection dynamique. Les collections dynamiques sont automatiquement ajoutées à la liste **[!UICONTROL Recherches enregistrées]**. La requête Recherches enregistrées de la collection est enregistrée dans la propriété `dam:query` de CRXDE à l’emplacement relatif `/content/dam/collections/`.

>[!NOTE]
>
>Vous pouvez partager les collections dynamiques comme s’il s’agissait de collections statiques.

La modification des recherches enregistrées est identique à celle des collections dynamiques. Pour plus d’informations, voir [Modification d’une collection dynamique](#edit-a-smart-collection).

Pour supprimer des recherches enregistrées, procédez comme suit :

1. Dans l’interface utilisateur Ressources, appuyez/cliquez sur l’icône de recherche dans la barre d’outils.

1. Avec le curseur dans le champ Omnisearch, appuyez sur la touche Entrée.
1. Appuyez ou cliquez sur l’icône de navigation globale afin d’afficher le panneau Filtres.
1. Dans la liste **[!UICONTROL Recherches enregistrées]**, appuyez/cliquez sur l’icône **[!UICONTROL Supprimer]** en regard de la collection dynamique à supprimer.
1. Dans la boîte de dialogue, appuyez/cliquez sur **[!UICONTROL Supprimer]** pour supprimer la recherche enregistrée.

## Execute a workflow on a collection {#run-a-workflow-on-a-collection}

Vous pouvez exécuter un workflow pour les ressources d’une collection. Si la collection contient des collections imbriquées, le workflow s’exécute également sur les ressources de ces dernières. Toutefois, si la collection et les collections imbriquées contiennent des ressources en double, le workflow ne s’exécute qu’une seule fois pour ces ressources.

1. Dans la console Collections, sélectionnez une collection sur laquelle exécuter un workflow.
1. Appuyez/cliquez sur l’icône de navigation globale, puis sélectionnez **[!UICONTROL Chronologie]** dans la liste.
1. Dans la chronologie, cliquez ou appuyez sur l’icône en forme de signe d’insertion en bas, puis appuyez/cliquez sur **[!UICONTROL Démarrer le workflow]**.
1. Dans la section **[!UICONTROL Démarrer le workflow]**, sélectionnez un modèle de workflow dans la liste. Par exemple, sélectionnez le modèle **[!UICONTROL Ressources de mise à jour de DAM]**.
1. Saisissez un titre pour le workflow, puis appuyez/cliquez sur **[!UICONTROL Démarrer]**.
1. Dans la boîte de dialogue, appuyez/cliquez sur **[!UICONTROL Poursuivre]**. Le workflow s’exécute sur toutes les ressources de la collection.

>[!MORELIKETHIS]
>
>* [Création d’une tâche de révision pour les collections](/help/assets/bulk-approval.md)

