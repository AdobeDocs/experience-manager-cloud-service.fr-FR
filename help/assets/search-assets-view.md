---
title: Découvrez comment rechercher des ressources dans [!DNL Assets view]?
description: Découvrez comment rechercher et découvrir des ressources dans la vue AEM Assets. La puissante fonctionnalité de recherche vous permet de découvrir rapidement la ressource appropriée et d’améliorer la vitesse de votre contenu.
role: User
exl-id: be9597a3-056c-436c-a09e-15a03567c85a
source-git-commit: 6fb2701fc2a4dc1cb9e8ea31134f0b3f2bb6bdf9
workflow-type: tm+mt
source-wordcount: '1470'
ht-degree: 65%

---

# Recherche de ressources dans [!DNL Assets view] {#search-assets}

>[!CONTEXTUALHELP]
>id="assets_search"
>title="Rechercher des ressources"
>abstract="Recherchez des ressources en spécifiant un mot-clé dans la barre de recherche ou en filtrant les ressources en fonction de leur statut, de leur type de fichier, de leur type MIME, de leur taille ou de leurs dates de création, de modification et d’expiration. Outre les filtres standard, vous pouvez également appliquer des filtres personnalisés. Vous pouvez enregistrer les résultats filtrés sous la forme d’une recherche enregistrée ou d’une collecte dynamique."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-assets-essentials/help/manage-collections.html?lang=fr#manage-smart-collection" text="Créer des collectes dynamiques"

[!DNL Assets view] offre des fonctionnalités de recherche efficaces, qui fonctionnent simplement par défaut. La recherche fonctionne de façon exhaustive car il s’agit d’une recherche de type plein texte. Ses puissantes fonctionnalités de recherche vous permettent de trouver rapidement la ressource appropriée et d’améliorer la vitesse de votre contenu. [!DNL Assets view] fournit une recherche plein texte, ou même des capacités de recherche basées sur les métadonnées telles que les balises intelligentes, le titre, la date de création et le copyright.

Pour rechercher des ressources,

* Cliquez dans la zone de recherche située en haut de la page. Par défaut, la recherche s’effectue dans le dossier que vous êtes en train de parcourir. Utilisez l’une des méthodes suivantes :

  ![Zone de recherche](assets/search-box.png)

   * Effectuez une recherche à l’aide d’un mot-clé ou vous pouvez changer de dossier. Appuyez sur Entrée.

   * Commencez à travailler avec une ressource récemment consultée en la recherchant directement. Cliquez dans la zone de recherche et sélectionnez une ressource récemment consultée parmi les suggestions.

## Recherche de ressources à l’aide d’Adobe Firefly

Si vous recherchez une ressource non disponible dans l’un des dossiers de ressources, utilisez la variable [!UICONTROL Adobe Firefly] fonctionnalité de recherche de ressources dans [!UICONTROL Adobe Experience Manager Assets]. Il vous permet de rechercher efficacement des ressources qui ne sont peut-être pas stockées dans les dossiers désignés. Cette fonctionnalité est actuellement accessible uniquement aux utilisateurs disposant du droit express. <br> Par exemple, vous pouvez rechercher une ressource à l’aide du mot-clé `Bugatti Type 57`. Lors de la recherche de `Bugatti Type 57`, aucun résultat n’est trouvé.

![Intégration de Firefly](assets/firefly-integration.jpg)
*Figure : Aucun résultat trouvé pour le type Bugatti 57 dans le dossier de ressources.*

Dans la barre de recherche, saisissez le nom de la ressource, puis cliquez sur **[!UICONTROL Générer]**.

![Intégration de Firefly](assets/bugatti-type-57.jpg)
*Figure : Ressources de référence recherchées à l’aide de la fonctionnalité de recherche de ressources d’Adobe Firefly.*

Les exemples de ressources s’affichent à l’écran. Vous pouvez charger ces ressources dans le dossier de votre choix pour un accès facile.

## Filtrer les résultats de la recherche {#refine-search-results}

Vous pouvez filtrer les résultats de la recherche en fonction des paramètres suivants.

![Filtres de recherche](assets/filters1.png)

*Image : filtrage des ressources recherchées en fonction de divers paramètres.*

* Statut de la ressource : filtrez les résultats de recherche à l’aide de `Approved`, `Rejected` ou d’un statut de ressource `No Status`.

* Type de fichier : filtrez les résultats de la recherche selon les types de fichiers pris en charge, à savoir `Images`, `Documents` et `Videos`.
* Type MIME : filtrez un ou plusieurs formats de fichiers pris en charge. <!-- TBD:  [supported file formats](/help/assets/supported-file-formats-assets-view.md). -->
* Taille de l’image : fournissez une ou plusieurs dimensions minimales et maximales pour filtrer les images. Les dimensions sont fournies en pixels et ne correspondent pas à la taille de fichier des images.
* Date de création : date de création de la ressource telle qu’elle figure dans les métadonnées. Le format de date standard utilisé est `yyyy-mm-dd`.
* Date de modification : date de dernière modification des ressources. Le format de date standard utilisé est `yyyy-mm-dd`.

* Date d’expiration : filtrez les résultats de la recherche en fonction du statut d’une ressource `Expired`. En outre, vous pouvez spécifier une période d’expiration pour les ressources afin de filtrer davantage les résultats de votre recherche.

* Filtres personnalisés : [ajoutez des filtres personnalisés](#custom-filters) à l’interface utilisateur de la vue Assets. Appliquez ces filtres personnalisés en plus des filtres standard pour affiner les résultats de la recherche.

Vous pouvez trier les ressources recherchées par ordre croissant ou décroissant de `Name`, `Relevancy`, `Size`, `Modified` et `Created`.

## Gestion des filtres personnalisés {#custom-filters}

**Autorisations requises :**  `Can Edit`, `Owner` ou administrateur.

La vue Assets vous permet également d’ajouter des filtres personnalisés à l’interface utilisateur. Vous pouvez ensuite appliquer ces filtres personnalisés en plus des [filtres standard](#refine-search-results) pour affiner vos résultats de recherche.

La vue Assets fournit les filtres personnalisés suivants :

<table>
    <tbody>
     <tr>
      <th><strong>Nom de filtre personnalisé</strong></th>
      <th><strong>Description</strong></th>
     </tr>
     <tr>
      <td>Titre</td>
      <td>Filtrage des ressources à l’aide du titre de la ressource. Le titre que vous indiquez dans les critères de recherche sensibles à la casse doit correspondre au titre exact de la ressource à afficher dans les résultats.</td>
     </tr>
     <tr>
      <td>Nom</td>
      <td>Filtrez les ressources à l’aide du nom de fichier de la ressource. Le nom que vous indiquez dans les critères de recherche sensibles à la casse doit correspondre au nom de fichier exact de la ressource à afficher dans les résultats.</td>
     </tr>
     <tr>
      <td>Taille de ressource</td>
      <td>Filtrez les ressources en définissant une plage de taille de fichier, en octets, dans les critères de recherche pour afficher une ressource dans les résultats.</td>
     </tr>
     <tr>
      <td>Balises prédites</td>
      <td>Filtrage des ressources à l’aide de la balise dynamique de ressource. Le nom de balise dynamique que vous indiquez dans les critères de recherche sensibles à la casse doit correspondre exactement au nom de balise dynamique de la ressource à afficher dans les résultats. Vous ne pouvez pas spécifier plusieurs balises dynamiques dans les critères de recherche.</td>
     </tr>    
    </tbody>
   </table>

<!--
   You can use a wildcard operator (*) to enable Assets view to display assets in the results that partially match the search criteria. For example, if you define <b>ma*</b> as the search criteria, Assets view displays assets with title, such as, market, marketing, man, manchester, and so on in the results.

   You can use a wildcard operator (*) to enable Assets view to display assets in the results that partially match the search criteria.

   You can use a wildcard operator (*) to enable Assets view to display assets in the results that partially match the search criteria. You can specify multiple smart tags separated by a comma in the search criteria.

   -->

### Ajout de filtres personnalisés {#add-custom-filters}

Pour ajouter des filtres personnalisés :

1. Cliquez sur **[!UICONTROL Filtres]**.

1. Dans la section **[!UICONTROL Filtres personnalisés]**, cliquez sur **[!UICONTROL Modifier]** ou **[!UICONTROL Ajouter des filtres]**.

   ![Ajout de filtres personnalisés](assets/add-custom-filters.png)

1. Dans la boîte de dialogue **[!UICONTROL Gestion des filtres personnalisés]**, sélectionnez les filtres à ajouter à la liste de filtres existants. Sélectionnez **[!UICONTROL Filtres personnalisés]** pour sélectionner tous les filtres.

1. Cliquez sur **[!UICONTROL Confirmer]** pour ajouter les filtres à l’interface utilisateur.

### Suppression de filtres personnalisés {#remove-custom-filters}

Pour supprimer des filtres personnalisés :

1. Cliquez sur **[!UICONTROL Filtres]**.

1. Dans la section **[!UICONTROL Filtres personnalisés]**, cliquez sur **[!UICONTROL Modifier]**.

1. Sans la boîte de dialogue **[!UICONTROL Gestion des filtres personnalisés]**, désélectionnez les filtres que vous devez supprimer de la liste des filtres existants.

1. Cliquez sur **[!UICONTROL Confirmer]** pour supprimer les filtres de l’interface utilisateur.

## Recherches enregistrées {#saved-search}

La fonctionnalité de recherche est assez facile à utiliser dans [!DNL Assets view]. Dans la zone de recherche, vous pouvez simplement saisir un mot-clé et appuyer sur Retour pour afficher les résultats. Vous pouvez également rechercher rapidement vos mots-clés récemment recherchés en un seul clic.

Vous pouvez également filtrer les résultats de la recherche en fonction de critères spécifiques relatifs aux métadonnées et au type de ressources. Pour les filtres fréquemment utilisés, [!DNL Assets view] permet d’enregistrer les paramètres de recherche afin d’améliorer l’expérience de recherche. Vous pouvez ensuite sélectionner la recherche enregistrée pour l’utiliser et appliquer le filtre, en un seul clic.

Pour créer une recherche enregistrée, recherchez une ressource, appliquez un ou plusieurs filtres, puis cliquez sur **[!UICONTROL Enregistrer sous]** > **[!UICONTROL Recherche enregistrée]** dans le panneau [!UICONTROL Filtres]. Vous pouvez également cliquer sur **[!UICONTROL Enregistrer sous]** et sélectionnez **[!UICONTROL Collecte dynamique]** pour enregistrer les résultats en tant que collecte dynamique. Consultez [Créer une collecte dynamique](manage-collections-assets-view.md#create-a-smart-collection) pour plus d’informations.

![Créer une collecte dynamique](assets/create-smart-collection.png)

<!-- TBD: Search behavior. Full-text search. Ranking and rank boosts. Hidden assets.
Report poor UX that users can only save a filtered search and not a simple search.
.
Are other supported files fully indexed and support full-text search? Eg. audio/videos files can at best have metadata indexed.
Anything about ranking of assets displayed in search results?

What about temporarily hiding an asset (suspending search on it) from the search results? If an asset is undergoing review collaboration, should it be used by others? Should it be hidden in search?

When userA is searching and userB add an asset that matches search results, will the asset display in search as soon as userA refreshes the page? Assuming indexing is near real-time. May not be so for bulk uploads.
-->

## Utiliser des résultats de recherche {#work-with-search-results}

Vous pouvez sélectionner les ressources qui s’affichent dans les résultats de recherche et effectuer les opérations suivantes :

* **Rechercher une image similaire**: recherchez une ressource image similaire dans l’interface utilisateur Assets en fonction des métadonnées et des balises intelligentes.

* **Détails** : affichez et modifiez les propriétés de la ressource.

* **Télécharger** : téléchargez une ressource.

* **Ajouter à la collection** : ajoutez la ressource sélectionnée à une collection.

* **Épingler à l’accès rapide**: [Épinglez une ressource](my-workspace-assets-view.md) pour y accéder plus rapidement lorsque vous en aurez besoin ultérieurement. Tous les éléments épinglés s’affichent dans la section **Accès rapide** de Mon espace de travail.

* **Ouvrir dans Adobe Express**: modifiez une image dans l’Adobe Express intégré à partir de l’écran Adobe Experience Manager Assets.

* **Modifier**: modifiez l’image à l’aide de Adobe Express.

* **Partager le lien** : [partagez des liens](share-links-for-assets-view.md) d’une ressource avec d’autres personnes utilisatrices, afin qu’elles puissent y accéder et la télécharger.

* **Supprimer** : supprimez une ressource.

* **Copier** : copiez une ressource vers un autre emplacement de dossier.

* **Déplacer** : déplacez une ressource vers un autre emplacement de dossier.

* **Renommer** : renommez une ressource.

* **Copier vers les bibliothèques**: ajoutez une ressource à la bibliothèque.

* **Affecter des tâches** : affectez des tâches aux utilisateurs et utilisatrices pour une ressource.

* **Surveiller** : [surveillez les opérations](manage-notifications-assets-view.md) effectuées sur une ressource.

## Configuration de la première page d’accueil de la recherche {#configuring-search-first-homepage}

Experience Manager Assets vous permet de sélectionner la page d’entrée par défaut de votre entreprise. Lors de l’utilisation de la fonction Rechercher d’abord comme page d’accueil, vous avez également la possibilité de personnaliser l’identité graphique de la page en configurant les images d’arrière-plan et de logo en fonction de votre marque.

Pour configurer la première page d’accueil de la recherche, procédez comme suit :

1. Accédez à **[!UICONTROL Paramètres]** > **[!UICONTROL Paramètres généraux]**.
1. Sélectionner **[!UICONTROL Recherche d’abord]**. Il ouvre ensuite la première configuration associée à la recherche. Vous pouvez définir [alignement](#setting-alignment-search-bar) ou [définir l’image d’arrière-plan et de logo ;](#setting-background-image-and-logo) de votre page d’accueil.

### Alignement de la barre de recherche {#setting-alignment-search-bar}

[!DNL Assets view] permet de modifier l’alignement de la barre de recherche. Vous pouvez faire apparaître la barre de recherche au centre ou en haut. Sélectionnez l’alignement approprié et cliquez sur **[!UICONTROL Enregistrer]**.

![Recherche de l’alignement de la première page d’accueil](assets/search-first-alignment.png)

### Définition de l’image d’arrière-plan et du logo de la page d’accueil {#setting-background-image-and-logo}

Vous pouvez ajouter le logo de la marque et l’image d’arrière-plan à la première page d’accueil de votre recherche. Procédez comme suit :

1. Accédez à **[!UICONTROL Image d’arrière-plan et logo]** section sous **[!UICONTROL Page d’accueil]**.
1. Cliquez sur **[!UICONTROL Remplacer]** pour parcourir les images du référentiel de ressources existant.
1. Cliquez sur **[!UICONTROL Enregistrer]**. [Aperçu](#preview-configured-homepage) les modifications pour passer en revue les modifications.

### Aperçu de la page d’accueil configurée {#preview-configured-homepage}

Vous pouvez prévisualiser pour vérifier la mise en page et le formatage de la première page d’accueil de la recherche. Utilisation **[!UICONTROL Aperçu]**, vous pouvez corriger la mise en page ou apporter des modifications en fonction des besoins. Pour prévisualiser la page d’accueil configurée, procédez comme suit :

1. Cliquez sur **[!UICONTROL Paramètres généraux]** et sélectionnez **[!UICONTROL Recherche d’abord]**.
1. Accédez à **[!UICONTROL Personnalisation de la première page d’accueil de la recherche]** et cliquez sur **[!UICONTROL Aperçu]**. Basculer **[!UICONTROL Thème sombre]** pour prévisualiser la page d’accueil sur un thème sombre ou clair.
1. Cliquez sur **[!UICONTROL Fermer]** pour fermer l’écran de prévisualisation.

   ![Recherche de l’aperçu de la première page d’accueil](assets/search-first-preview.gif)

## Étapes suivantes {#next-steps}

* [Regardez une vidéo pour rechercher des ressources dans la vue Assets](https://experienceleague.adobe.com/docs/experience-manager-learn/assets-essentials/basics/using.html?lang=fr)

* Faites des commentaires sur le produit en utilisant l’option [!UICONTROL Commentaires] disponible dans l’interface utilisateur de la vue Assets

* Faites des commentaires sur la documentation en utilisant l’option [!UICONTROL Modifier cette page] ![modifier la page](assets/do-not-localize/edit-page.png) ou [!UICONTROL Enregistrer un problème] ![créer un problème GitHub](assets/do-not-localize/github-issue.png) disponible dans la barre latérale droite.

* Contactez l’[assistance clientèle](https://experienceleague.adobe.com/?support-solution=General&amp;lang=fr#support).
