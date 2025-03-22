---
title: Gestion des collections de ressources numériques
description: Découvrez le concept de collection dans Adobe Experience Manager Assets. Apprenez à créer, gérer, modifier et partager des collections avec d’autres utilisateurs.
contentOwner: AG
mini-toc-levels: 1
feature: Collections, Asset Management
role: User
exl-id: b0798adc-56a4-4577-b4ee-8d1fca3bff09
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '2444'
ht-degree: 81%

---

# Gérer les collections {#manage-collections}

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

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-collections.html?lang=fr) |
| AEM as a Cloud Service | Cet article |

Une collection est un ensemble de ressources dans Adobe Experience Manager Assets. Vous pouvez utiliser des collections pour partager des ressources entre utilisateurs. Il peut s’agir d’une collection statique ou dynamique basée sur les résultats de la recherche.

Contrairement aux dossiers, une collection peut comporter des ressources provenant de différents emplacements. Vous pouvez partager des collections avec plusieurs utilisateurs et utilisatrices auxquels sont attribués différents niveaux de privilèges, notamment l’affichage, la modification, etc.

Vous pouvez partager plusieurs collections avec un utilisateur ou une utilisatrice. Chaque collection contient des références aux ressources. L’intégrité du référentiel des ressources est préservée dans les collections.

Les collections sont composées des types suivants, en fonction de la manière dont elles collectent les ressources :

* Collection contenant une liste de référence statique de ressources, dossiers et autres collections

* Collection dynamique qui rassemble de manière dynamique des ressources selon des critères de recherche

## Accès à la console Collections {#navigate-the-collections-console}

Pour ouvrir la console **[!UICONTROL Collections]**, procédez comme suit :

Pour ouvrir l’**[!UICONTROL Collections]**, sélectionnez le logo Experience Manager. Sur la page de navigation, accédez à **[!UICONTROL Ressources]** > **[!UICONTROL Collections]**.

## Création d’une collection {#create-a-collection}

Vous pouvez créer une collection contenant des [références statiques](#create-a-collection-with-static-references) ou reposant sur un [filtre de critères de recherche](#create-a-smart-collection). Vous pouvez également créer une collection à partir d’une Lightbox.

### Création d’une collection avec des références statiques {#create-a-collection-with-static-references}

Vous pouvez créer une collection avec des références statiques, par exemple une collection avec des références à des ressources, des dossiers, des collections, des visionneuses à 360° et des visionneuses d’images.

1. Accédez à la console **[!UICONTROL Collections]**.
1. Dans la barre d’outils, sélectionnez **[!UICONTROL Créer]**.
1. Sur la page **[!UICONTROL Créer une collection]**, saisissez un titre et une description facultative de la collection.
1. Ajoutez des membres à la collection et affectez les autorisations appropriées. Vous pouvez également sélectionner **[!UICONTROL Collection publique]** pour permettre à tous les utilisateurs d’accéder à la collection.

   >[!NOTE]
   >
   >Pour permettre aux membres de partager des collections avec d’autres utilisateurs, vous devez accorder les autorisations de lecture au groupe `dam-users` dans le chemin `home/users`. Donnez l’autorisation aux utilisateurs à l’emplacement `/content/dam/collections` afin de leur permettre d’afficher les collections dans les listes contextuelles. Vous pouvez également intégrer l’utilisateur au groupe `dam-users`.

1. (Facultatif) Ajoutez une image de miniature pour la collection.
1. Sélectionnez **[!UICONTROL Créer]**, puis sélectionnez **[!UICONTROL OK]** pour fermer la boîte de dialogue. Une collection avec le titre et les propriétés spécifiés s’ouvre dans la console Collections.

   >[!NOTE]
   >
   >Experience Manager Assets vous permet de créer des tâches de révision pour une collection de la même façon que vous créez des tâches de révision pour un dossier de ressources.

   Pour ajouter des ressources à la collection, accédez à l’interface utilisateur Assets. Pour plus d’informations, consultez la section [Ajout de ressources à une collection](#add-assets-to-a-collection).

### Création de collections à l’aide de la zone de dépôt {#create-collections-using-dropzone}

Vous pouvez faire glisser des ressources de l’interface utilisateur Assets jusqu’à une collection. Vous pouvez également créer une copie d’une collection et faire glisser les ressources jusqu’à celle-ci.

1. Dans l’interface utilisateur Assets, sélectionnez les ressources à ajouter à une collection.
1. Faites glisser les ressources jusqu’à la zone **[!UICONTROL Déposer dans la collection]**. Vous pouvez également sélectionner l’icône **[!UICONTROL À la collection]** dans la barre d’outils.
1. Sur la page **[!UICONTROL Ajouter à la collection]**, sélectionnez l’icône **[!UICONTROL Créer une collection]** dans la barre d’outils. Si vous souhaitez ajouter les ressources à une collection existante, sélectionnez-la dans la page, puis sélectionnez **[!UICONTROL Ajouter]**. Par défaut, la collection la plus récemment mise à jour est sélectionnée.
1. Dans la boîte de dialogue **[!UICONTROL Créer une collection]**, indiquez le nom de la collection. Si vous souhaitez que la collection soit accessible à tous les utilisateurs, sélectionnez **[!UICONTROL Collection publique]**.
1. Sélectionnez **[!UICONTROL Continuer]** pour créer la collection.

### Création d’une collection dynamique {#create-a-smart-collection}

Une collection dynamique utilise des critères de recherche pour rassembler les ressources de manière dynamique. Vous pouvez créer une collection dynamique en utilisant uniquement des fichiers et non pas des dossiers ou des fichiers et des dossiers.

1. Accédez à l’interface utilisateur d’Assets, puis sélectionnez l’icône **[!UICONTROL Rechercher]**.
1. Saisissez le mot-clé dans la boîte de dialogue Omni-recherche et sélectionnez `Enter`. Sélectionnez l’icône de navigation globale pour afficher le panneau Filtres et appliquer un filtre de recherche à partir du panneau de recherche.
1. Dans la liste **[!UICONTROL Fichiers et dossiers]**, sélectionnez **[!UICONTROL Fichiers]**.
1. Sélectionnez **[!UICONTROL Enregistrer la collection dynamique]**.
1. Attribuez un nom à la collection. Sélectionnez **[!UICONTROL Public]** pour ajouter le groupe Utilisateurs DAM avec le rôle Observateur à la collection dynamique.

   >[!NOTE]
   >
   >Si vous sélectionnez **[!UICONTROL Public]**, la collection dynamique est disponible pour chaque personne possédant le rôle de propriétaire une fois que vous la créez. Si vous désactivez l’option **[!UICONTROL Public]**, le groupe Utilisateurs DAM n’est plus associé à la collection dynamique.

1. Sélectionnez **[!UICONTROL Enregistrer]** pour créer la collection dynamique, puis fermez la boîte de message pour terminer le processus. La nouvelle collection dynamique est également ajoutée à la liste **[!UICONTROL Recherches enregistrées]**.
Le libellé du bouton **[!UICONTROL Créer une collection dynamique]** se transforme en **[!UICONTROL Modifier la collection dynamique]**. Pour modifier les paramètres de la collection dynamique, sélectionnez **[!UICONTROL Fichiers]** dans la liste **[!UICONTROL Fichiers et dossiers]**. Sélectionnez ensuite le bouton **[!UICONTROL Modifier la sélection dynamique]**.

## Ajout de ressources à une collection {#add-assets-to-a-collection}

Vous pouvez ajouter des ressources à une collection qui comporte une liste de ressources ou de dossiers référencés.

>[!NOTE]
>
>Les collections dynamiques utilisent une requête de recherche pour renseigner les ressources. Par conséquent, les références statiques aux ressources et aux dossiers ne s’y appliquent pas.

1. Dans l’interface utilisateur d’Assets, accédez à l’emplacement de la ressource à ajouter à une collection.
1. Sélectionnez la ressource et sélectionnez l’icône **[!UICONTROL À la collection]** dans la barre d’outils. Vous pouvez également faire glisser la ressource jusqu’à la zone **[!UICONTROL Déposer dans la collection]**. Relâchez le bouton de la souris lorsque la zone de dépôt devient active et que le libellé se transforme en **[!UICONTROL Déposer pour ajouter]**.
1. Sur la page **[!UICONTROL Ajouter à la collection]**, sélectionnez la collection à laquelle vous souhaitez ajouter la ressource.
1. Sélectionnez **[!UICONTROL Ajouter]**, puis fermez le message de confirmation. La ressource est ajoutée à la collection.

## Modification d’une collection dynamique {#edit-a-smart-collection}

Les collections dynamiques sont créées en enregistrant une recherche afin que vous puissiez modifier leur contenu en changeant les paramètres de recherche de la [recherche enregistrée](#saved-searches).

1. Dans l’interface utilisateur d’Assets, sélectionnez l’icône **[!UICONTROL Rechercher]** dans la barre d’outils.
1. Placez le curseur dans la zone Omnisearch et sélectionnez la touche `Enter`.
1. Sélectionnez l’icône de navigation globale pour afficher le panneau Filtres .
1. Dans la liste **[!UICONTROL Recherches enregistrées]**, sélectionnez la collection dynamique que vous souhaitez modifier. Le panneau de recherche affiche les filtres configurés pour la recherche enregistrée.
1. Dans la liste **[!UICONTROL Fichiers et dossiers]**, sélectionnez **[!UICONTROL Fichiers]**.
1. Modifiez un ou plusieurs filtres selon vos besoins. Sélectionnez **[!UICONTROL Modifier la collection dynamique]**. Vous pouvez également modifier le nom de la collection dynamique.
1. Sélectionnez **[!UICONTROL Enregistrer]**. La boîte de dialogue **[!UICONTROL Modification de la collection dynamique]** s’affiche.
1. Sélectionnez **[!UICONTROL Remplacer]** pour remplacer la collection dynamique d’origine par la collection modifiée. Sinon, sélectionnez **[!UICONTROL Enregistrer sous]** pour enregistrer la collection modifiée séparément.
1. Dans la boîte de dialogue de confirmation, sélectionnez **[!UICONTROL Enregistrer]** pour terminer le processus.

## Affichage et modification des métadonnées {#view-and-edit-collection-metadata}

Les métadonnées de collection incluent les données sur la collection, notamment toute balise qui est ajoutée.

1. Dans la console Collections, sélectionnez une collection, puis l’icône **[!UICONTROL Propriétés]** dans la barre d’outils.
1. Sur la page **[!UICONTROL Métadonnées de collection]**, affichez les métadonnées de collection à partir des onglets **[!UICONTROL De base]** et **Avancé**.
1. Modifiez les métadonnées, si nécessaire, puis sélectionnez **[!UICONTROL Enregistrer et fermer]** dans la barre d’outils pour enregistrer les modifications.

### Modification en masse des métadonnées de collection {#edit-collection-metadata-in-bulk}

Vous pouvez modifier les métadonnées de plusieurs collections simultanément. Cette fonctionnalité vous permet de répliquer rapidement des métadonnées communes dans plusieurs collections.

1. Dans la console Collections, sélectionnez au moins deux collections pour lesquelles vous souhaitez modifier les métadonnées.
1. Dans la barre d’outils, sélectionnez l’icône **[!UICONTROL Propriétés]**.
1. Sur la page **[!UICONTROL Métadonnées de collection]**, modifiez les métadonnées sous **[!UICONTROL De base]** et **[!UICONTROL Avancé]**, selon les besoins.
1. Sélectionnez **[!UICONTROL Enregistrer et fermer]** dans la barre d’outils, puis fermez la boîte de dialogue de confirmation pour terminer le processus.
1. Pour ajouter les nouvelles métadonnées avec les métadonnées existantes, sélectionnez le mode **[!UICONTROL Ajouter]**. Si vous ne sélectionnez pas cette option, les nouvelles métadonnées remplacent les métadonnées existantes dans les champs. Sélectionnez **[!UICONTROL Envoyer]**.

   >[!NOTE]
   >
   >Le mode d’ajout fonctionne uniquement avec les champs pouvant contenir plusieurs valeurs. Pour les champs ne pouvant contenir qu’une seule valeur, les nouvelles métadonnées ne sont pas ajoutées à la valeur existante dans le champ, même si vous sélectionnez **[!UICONTROL Mode d’ajout]**.

## Rechercher {#searching}

La fonctionnalité Recherche des collections prend en charge à la fois la [recherche de collections](#search-collections) et la [recherche de ressources dans une collection](#search-within-collections).

### Recherche de collections {#search-collections}

Vous pouvez effectuer des recherches dans des collections à partir de la console Collections. Lorsque vous effectuez des recherches avec des mots-clés dans la zone Omni-recherche, [!DNL Experience Manager Assets] recherche les noms des collections, les métadonnées et les balises ajoutées aux collections.

Si vous recherchez des collections à partir du niveau supérieur, seules les collections individuelles sont renvoyées dans les résultats de recherche. Les ressources ou dossiers à l’intérieur des collections sont exclus. Dans tous les autres cas (par exemple, dans une collection individuelle ou dans une hiérarchie de dossiers), l’ensemble des ressources, des dossiers et des collections appropriés est renvoyé.

### Recherche dans les collections {#search-within-collections}

Dans la console Collections, sélectionnez une collection pour l’ouvrir.

Dans une collection, la recherche [!DNL Experience Manager] se limite aux ressources (ainsi qu’aux balises et métadonnées) de la collection en cours d’affichage. Lorsque vous effectuez une recherche dans un dossier, toutes les ressources correspondantes et les dossiers enfants du dossier actif sont renvoyés. Lorsque vous effectuez une recherche dans une collection, seuls les ressources, dossiers et autres collections correspondant aux membres directs de la collection sont renvoyés.

## Modification des paramètres d’une collection {#edit-collection-settings}

Vous pouvez modifier les paramètres d’une collection, tels que le titre et la description, ou ajouter des membres à une collection.

1. Sélectionnez une collection, puis l’icône **[!UICONTROL Paramètres]** dans la barre d’outils. Vous pouvez également utiliser l’action rapide **[!UICONTROL Paramètres]** à partir de la miniature de la collection.
1. Modifiez les paramètres de la collection sur la page **[!UICONTROL Paramètres de la collection]**. Vous pouvez par exemple modifier le titre, les descriptions, les membres et les autorisations de la collection, comme décrit dans [Ajout de collections](#create-a-collection).
1. Sélectionnez **[!UICONTROL Enregistrer]** pour enregistrer les modifications.

## Suppression d’une collection {#delete-a-collection}

1. Dans la console Collections , sélectionnez une ou plusieurs collections, puis sélectionnez l’icône de suppression dans la barre d’outils.
1. Dans la boîte de dialogue, sélectionnez **[!UICONTROL Supprimer]** pour confirmer la suppression.

   >[!NOTE]
   >
   >Vous pouvez également supprimer les collections dynamiques en [supprimant les recherches enregistrées](#saved-searches).

## Téléchargement d’une collection {#download-a-collection}

Lorsque vous téléchargez une collection, la hiérarchie complète des ressources dans la collection est téléchargée, y compris les dossiers et les collections enfants.

1. Dans la console Collections, sélectionnez une ou plusieurs collections à télécharger.
1. Dans la barre d’outils, sélectionnez l’icône de téléchargement.
1. Dans la boîte de dialogue **[!UICONTROL Télécharger]**, sélectionnez **[!UICONTROL Télécharger]**. Si vous souhaitez télécharger les rendus des ressources dans la collection, sélectionnez **[!UICONTROL Rendus]**. <!-- Select the **[!UICONTROL Email]** option to send an email notification to the owner of the collection. -->

   Lorsque vous sélectionnez une collection à télécharger, l’ensemble de la hiérarchie de dossiers sous cette collection est téléchargé. Pour inclure chaque collection que vous téléchargez (y compris les ressources figurant dans des collections enfant imbriquées dans la collection parent) dans un dossier individuel, sélectionnez **[!UICONTROL Créer un dossier distinct pour chaque ressource]**.

## Modification des propriétés de métadonnées de plusieurs collections {#editing-metadata-properties-of-multiple-collections}

Adobe Enterprise Manager Assets vous permet de modifier en masse les métadonnées de nombreuses collections. Utilisez la page [!UICONTROL Propriétés] pour effectuer des modifications sur les métadonnées sur plusieurs collections, par exemple pour modifier les propriétés des métadonnées en une valeur commune, ainsi que pour ajouter ou modifier des balises.

Pour personnaliser la page [!UICONTROL Propriétés] de métadonnées, notamment ajouter, modifier et supprimer des propriétés de métadonnées, utilisez l’éditeur de schéma.

>[!NOTE]
>
>Les méthodes de modification en masse fonctionnent pour les ressources disponibles dans une collection. Pour les ressources disponibles dans plusieurs dossiers ou correspondant à un critère commun, il est possible de mettre à jour [les métadonnées en masse après une recherche](/help/assets/search-assets.md#metadata-updates).

1. Dans la console Collections, sélectionnez les collections à modifier.
1. Dans la barre d’outils, sélectionnez **[!UICONTROL Propriétés]** pour ouvrir la page [!UICONTROL Propriétés] pour les collections sélectionnées.
1. Modifiez les propriétés de métadonnées des collections sélectionnées dans les différents onglets.

   >[!NOTE]
   >
   >Les métadonnées que vous ajoutez pour les collections sélectionnées remplacent les métadonnées précédentes de ces collections, à l’exception des balises. Toutes les balises que vous ajoutez dans le champ **[!UICONTROL Balises]** sont ajoutées à la liste existante des balises dans les métadonnées.

1. Pour afficher les propriétés de métadonnées associées à une collection spécifique, désélectionnez les autres collections dans la liste. Les champs de l’éditeur de métadonnées sont renseignés avec les métadonnées de la collection particulière.

   >[!NOTE]
   >
   >* Dans la page des propriétés de collection, vous pouvez supprimer des collections de la liste des collections en les désélectionnant. La liste des collections contient toutes les collections sélectionnées par défaut. Les métadonnées des collections que vous supprimez ne sont pas mises à jour.
   >* En haut de la liste, cochez la case située en regard de l’option **[!UICONTROL Titre]** pour passer de la sélection des collections à l’effacement de la liste, et inversement.

1. Enregistrez les modifications.

## Création de collections imbriquées {#create-nested-collections}

Vous pouvez ajouter une collection à une autre collection, créant ainsi une collection imbriquée.

1. Dans la console Collections, sélectionnez la collection ou le groupe de collections souhaité, puis sélectionnez **[!UICONTROL À la collection]** dans la barre d’outils.
1. Sur la page **[!UICONTROL Ajouter à la collection]**, sélectionnez la collection à laquelle vous souhaitez ajouter la collection.

   >[!NOTE]
   >
   >La collection mise le plus récemment à jour est sélectionnée par défaut sur la page **[!UICONTROL Ajouter à la collection]**.

1. Sélectionnez **[!UICONTROL Ajouter]**. Un message confirme l’ajout de la collection à la collection cible sur la page **[!UICONTROL Sélectionner la destination]**. Fermez le message pour terminer le processus.

>[!NOTE]
>
>Les collections dynamiques ne peuvent pas être imbriquées. En d’autres termes, les collections dynamiques ne peuvent pas contenir d’autres collections.

## Recherches enregistrées {#saved-searches}

Dans l’interface utilisateur d’Assets, vous pouvez rechercher ou filtrer des ressources selon des règles, critères de recherche ou facettes de recherche personnalisées. Si vous enregistrez ces éléments en tant que **[!UICONTROL recherches enregistrées]**, vous pouvez y accéder ultérieurement à partir de la liste **[!UICONTROL Recherches enregistrées]** du panneau Filtrer. La création d’une recherche enregistrée entraîne celle d’une collection dynamique.

Les recherches enregistrées sont créées lorsque vous créez une collection dynamique. Les collections dynamiques sont automatiquement ajoutées à la liste **[!UICONTROL Recherches enregistrées]**. La requête Recherches enregistrées de la collection est enregistrée dans la propriété `dam:query` de CRXDE à l’emplacement relatif `/content/dam/collections/`. Les recherches que vous pouvez enregistrer et les recherches enregistrées affichées dans la liste ne sont pas limitées.

>[!NOTE]
>
>Vous pouvez partager les collections dynamiques comme s’il s’agissait de collections statiques.

La modification des recherches enregistrées est identique à celle des collections dynamiques. Pour plus d’informations, voir [Modification d’une collection dynamique](#edit-a-smart-collection).

Pour supprimer des recherches enregistrées, procédez comme suit :

1. Dans l’interface utilisateur d’Assets, sélectionnez l’icône de recherche dans la barre d’outils.

1. Placez le curseur dans le champ Omnisearch et appuyez sur la touche `Enter`.
1. Sélectionnez l’icône de navigation globale pour afficher le panneau Filtres .
1. Dans la liste **[!UICONTROL Recherches enregistrées]**, sélectionnez **[!UICONTROL Supprimer]** en regard de la collection dynamique à supprimer.
1. Dans la boîte de dialogue, sélectionnez **[!UICONTROL Supprimer]** pour supprimer la recherche enregistrée.

## Exécution d’un workflow sur une collection {#run-a-workflow-on-a-collection}

Vous pouvez exécuter un workflow pour les ressources d’une collection. Si la collection contient des collections imbriquées, le workflow s’exécute également sur les ressources de ces dernières. Toutefois, si la collection et les collections imbriquées contiennent des ressources en double, le workflow ne s’exécute qu’une seule fois pour ces ressources.

1. Dans la console Collections, sélectionnez une collection sur laquelle exécuter un workflow.
1. Sélectionnez l’icône de navigation globale, puis choisissez **[!UICONTROL Chronologie]** dans la liste.
1. Dans la chronologie, sélectionnez l’icône de signe d’insertion en bas, puis sélectionnez **[!UICONTROL Démarrer le workflow]**.
1. Dans la section **[!UICONTROL Démarrer le workflow]**, sélectionnez un modèle de workflow dans la liste. Par exemple, sélectionnez le modèle **[!UICONTROL Ressources de mise à jour de DAM]**.
1. Saisissez un titre pour le workflow, puis sélectionnez **[!UICONTROL Démarrer]**.
1. Dans la boîte de dialogue, sélectionnez **[!UICONTROL Continuer]**. Le workflow s’exécute sur toutes les ressources de la collection.

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
* [Import des métadonnées en bloc](metadata-import-export.md)
* [Publier des ressources sur AEM et Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [Créer une tâche de révision pour les collections](/help/assets/bulk-approval.md)
