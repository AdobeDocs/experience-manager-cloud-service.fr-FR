---
title: Découvrez comment rechercher et trouver des ressources dans  [!DNL Assets view] ?
description: Découvrez comment rechercher et trouver des ressources dans la vue AEM Assets. Les puissantes fonctionnalités de recherche de vous permettent de découvrir rapidement la ressource appropriée et d’améliorer la vitesse de votre contenu.
role: User
exl-id: abfe6a91-1699-436f-8bf4-0d0bf2369f46
feature: Asset Management, Publishing, Collaboration, Asset Processing
source-git-commit: 391294cf461662d145a52b6c8a366e53f39ff84a
workflow-type: tm+mt
source-wordcount: '1887'
ht-degree: 80%

---

# Rechercher des ressources dans [!DNL Assets view] {#search-assets}

>[!CONTEXTUALHELP]
>id="assets_search"
>title="Rechercher des ressources"
>abstract="Recherchez des ressources en spécifiant un mot-clé dans la barre de recherche ou en filtrant les ressources en fonction de leur statut, de leur type de fichier, de leur type MIME, de leur taille ou de leurs dates de création, de modification et d’expiration. Outre les filtres standard, vous pouvez également appliquer des filtres personnalisés. Vous pouvez enregistrer les résultats filtrés sous la forme d’une recherche enregistrée ou d’une collecte dynamique."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-assets-essentials/help/manage-collections.html?lang=fr#manage-smart-collection" text="Créer des collectes dynamiques"

[!DNL Assets view] offre des fonctionnalités de recherche efficaces, qui fonctionnent simplement par défaut. La recherche fonctionne de façon exhaustive, car il s’agit d’une recherche de type plein texte. Ses puissantes fonctionnalités de recherche vous permettent de trouver rapidement la ressource appropriée et d’améliorer la vitesse de votre contenu. [!DNL Assets view] fournit une recherche en texte intégral, ou même des capacités de recherche basées sur les métadonnées telles que les balises intelligentes, le titre, la date de création et le copyright.

Pour rechercher des ressources :

* Cliquez dans la zone de recherche située en haut de la page. Par défaut, la recherche s’effectue dans le dossier que vous êtes en train de parcourir. Utilisez l’une des méthodes suivantes :

  ![Zone de recherche](assets/search-box.png)

   * Effectuez une recherche à l’aide d’un mot-clé et changez éventuellement de dossier. Appuyez sur Entrée.

   * Commencez à travailler avec une ressource récemment consultée en la recherchant directement. Cliquez dans la zone de recherche et sélectionnez une ressource récemment consultée parmi les suggestions.

## Filtrer les résultats de la recherche {#refine-search-results}

Vous pouvez affiner les résultats de recherche pour trouver les ressources appropriées en appliquant plusieurs filtres. Ces filtres, configurés par un administrateur, sont basés sur des fichiers, des dossiers et des collections. Voir [Personnalisation des filtres de recherche](custom-search-filters.md).

![Filtres de recherche](assets/filters-panel.gif)

Vous pouvez filtrer les résultats de la recherche en fonction des paramètres suivants.

* Statut de la ressource : filtrez les résultats de recherche à l’aide de `Approved`, `Rejected` ou d’un statut de ressource `No Status`.
* Type de fichier : filtrez les résultats de la recherche selon les types de fichiers pris en charge, à savoir `Images`, `Documents` et `Videos`.
* Type MIME : filtrez un ou plusieurs formats de fichiers pris en charge. <!-- TBD:  [supported file formats](/help/using/supported-file-formats.md). -->
* Taille de l’image : fournissez une ou plusieurs dimensions minimales et maximales pour filtrer les images. Les dimensions sont fournies en pixels et ne correspondent pas à la taille de fichier des images.
* Date de création : date de création de la ressource telle qu’elle figure dans les métadonnées. Le format de date standard utilisé est `yyyy-mm-dd`.
* Date de modification : date de dernière modification des ressources. Le format de date standard utilisé est `yyyy-mm-dd`.
* Date d’expiration : filtrez les résultats de la recherche en fonction du statut d’une ressource `Expired`. En outre, vous pouvez spécifier une période d’expiration pour les ressources afin de filtrer davantage les résultats de votre recherche.
* Filtres personnalisés : [ajoutez des filtres personnalisés](#custom-filters) à l’interface utilisateur d’affichage d’Assets. Appliquez ces filtres personnalisés en plus des filtres standard pour affiner les résultats de la recherche.

Vous pouvez trier les ressources recherchées par ordre croissant ou décroissant de `Name`, `Relevance`, `Size`, `Modified` et `Created`. Les ressources recherchées sont triées en fonction de la `Relevance`, par défaut.

## Gestion des filtres personnalisés {#custom-filters}

**Autorisations requises :**  `Can Edit`, `Owner` ou administrateur.

La vue Assets permet également d’ajouter des filtres personnalisés à l’interface utilisateur. Vous pouvez ensuite appliquer ces filtres personnalisés en plus des [filtres standard](#refine-search-results) pour affiner vos résultats de recherche.

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
      <td>Filtrage des ressources à l’aide de la balise intelligente de ressource. Le nom de balise intelligente que vous indiquez dans les critères de recherche avec respect de la casse doit correspondre exactement au nom de balise intelligente de la ressource à afficher dans les résultats. Vous ne pouvez pas spécifier plusieurs balises intelligentes dans les critères de recherche.</td>
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

## Recherche IA {#ai-search}

La recherche par IA est une fonctionnalité de recherche avancée qui comprend la signification et l’intention derrière la requête d’un utilisateur ou d’une utilisatrice plutôt que de s’appuyer sur des correspondances exactes de mots-clés. Il utilise l’intelligence artificielle (IA) et le machine learning pour fournir des résultats plus précis et contextuels.

Contrairement à la recherche traditionnelle par mot-clé, qui recherche des termes exacts, la recherche par IA interprète les relations entre les mots, les concepts et l’intention de l’utilisateur. Cela permet de s’assurer que les utilisateurs et les utilisatrices trouvent ce qu’ils recherchent, même si leur requête est formulée différemment, contient des fautes de frappe ou est dans une autre langue.

Voici quelques-uns de ses principaux avantages :

* **Prise en charge multilingue** : effectuez des recherches dans plusieurs langues sans nécessiter de traduction exacte. Les utilisateurs peuvent trouver du contenu pertinent quel que soit leur langage de requête.

* **Gère les fautes d’orthographe** : interprète les fautes de frappe et d’orthographe pour garantir des résultats précis même avec une saisie imparfaite.

* **Comprend les synonymes** : fournit des résultats pour les termes et expressions associés, de sorte que les utilisateurs n’ont pas besoin de deviner le bon mot-clé.

* **Recherche contextuelle** : reconnaît l’intention derrière une requête, pas seulement les mots exacts.

### Exemples de recherche dans l’IA {#examples-ai-search}

**Exemple d’invite** : *Femme buvant du café*

La recherche traditionnelle par mot-clé recherche les correspondances exactes des métadonnées de ressource, telles que `Woman`, `drinking`, `Coffee`, et renvoie les ressources qui incluent tous ces termes dans les métadonnées.

Cependant, la recherche par l’IA correspond à des mots similaires tels que `Girl`, `Lady` dans le cas de `Woman` et `Cappuccino` et `Latte` dans le cas de `Coffee`.

De même, vous pouvez spécifier cette invite en espagnol ou mal orthographier `Woman` comme `Wman` et obtenir toujours les mêmes résultats.

![Recherche sémantique dans la vue Assets](assets/semantic-search.png)

## Rechercher des ressources à l’aide d’[!DNL Adobe Firefly] {#search-firefly}

Vous pouvez rechercher une ressource qui n’est disponible dans aucun des dossiers en utilisant la fonction de recherche de ressources [!DNL Adobe Firefly] dans [!DNL Experience Manager Assets]. Vous pouvez ainsi générer efficacement des ressources en temps réel qui ne sont pas stockées dans les dossiers de ressources.

### Avant de commencer {#search-assets-firefly-prereqs}

Vous devez disposer d’un abonnement [!DNL Adobe Express] actif.

### Générer des ressources {#generate-assets-firefly}

Pour générer de nouvelles ressources en utilisant [!DNL Adobe Firefly] :

1. Accédez à l’espace de travail [!DNL AEM Assets].

1. Saisissez le nom de la ressource dans la barre de recherche. Par exemple, vous pouvez rechercher une ressource à l’aide du mot-clé `Bugatti Type 57`. Lors de la recherche de la ressource, aucun résultat n’est renvoyé, car la ressource n’est présente dans aucun des dossiers. Pour générer des ressources à l’aide de l’IA, cliquez sur **[!UICONTROL Générer avec Firefly]**. L’écran [!DNL Adobe Firefly] s’affiche.

   ![Intégration de Firefly](assets/firefly-integration.png)

   Les nouvelles ressources sont générées. Vous pouvez également modifier la description de l’image en saisissant le nouveau prompt de texte dans la zone de description. [Découvrez comment écrire une bonne invite d’IA pour générer du contenu extraordinaire et pertinent](https://helpx.adobe.com/in/firefly/using/tips-and-tricks.html). Vous pouvez également [modifier l’image avec d’autres fonctionnalités telles que la modification du style, des dimensions de l’image, etc](https://helpx.adobe.com/in/firefly/using/text-to-image.html).

   ![Intégration de Firefly](assets/bugatti-type-57.png)

1. Sélectionnez une image à enregistrer. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les ressources dans votre dossier préféré pour un accès facile.

1. Le formulaire Enregistrer la ressource s’affiche. Indiquez les champs suivants :

   * Saisissez un nom pour le fichier dans le champ **Enregistrer sous**.
   * Sélectionnez un dossier de destination.
   * Fournissez des détails tels que le nom, les mots-clés, les canaux, la période et la zone géographique du projet ou de la campagne.

   ![Intégration de Firefly](assets/save-generated-asset.png)

1. Cliquez sur **Enregistrer comme nouvelle ressource** pour enregistrer la ou les ressources.

### Chargement de ressources {#upload-assets-firefly}

Pour télécharger la ressource générée dans le référentiel de ressources :

1. Cliquez sur **[!UICONTROL Charger]**.
1. Sélectionnez le dossier de ressources dans lequel vous devez télécharger la ressource et cliquez sur **[!UICONTROL Sélectionner le dossier]**.
   ![Charger la ressource](assets/upload-asset-firefly.jpg)

## Recherches enregistrées {#saved-search}

La fonctionnalité de recherche est assez facile à utiliser dans [!DNL Assets view]. Dans la zone de recherche, vous pouvez non seulement saisir un mot-clé et appuyer sur Entrée pour afficher les résultats, mais également retrouver rapidement vos mots-clés recherchés récemment en un seul clic.

Vous pouvez également filtrer les résultats de la recherche en fonction de critères spécifiques relatifs aux métadonnées et au type de ressources. Pour les filtres fréquemment utilisés, [!DNL Assets view] permet d’enregistrer les paramètres de recherche afin d’améliorer l’expérience de recherche. Vous pouvez ensuite sélectionner la recherche enregistrée pour l’utiliser et appliquer le filtre, en un seul clic.

Pour créer une recherche enregistrée, recherchez une ressource, appliquez un ou plusieurs filtres, puis cliquez sur **[!UICONTROL Enregistrer sous]** > **[!UICONTROL Recherche enregistrée]** dans le panneau [!UICONTROL Filtres]. Vous pouvez également cliquer sur **[!UICONTROL Enregistrer sous]** et sélectionnez **[!UICONTROL Collecte dynamique]** pour enregistrer les résultats en tant que collecte dynamique. Consultez [Créer une collecte dynamique](manage-collections.md#create-a-smart-collection) pour plus d’informations.

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

* **Rechercher une image similaire** : recherchez une ressource d’image similaire dans l’interface d’utilisation d’Assets en fonction des métadonnées et des balises intelligentes.

* **Détails** : affichez et modifiez les propriétés de la ressource.

* **Télécharger** : téléchargez une ressource.

* **Ajouter à la collection** : ajoutez la ressource sélectionnée à une collection.

* **Épingler à l’accès rapide**: [Épinglez une ressource](my-workspace-assets-view.md) pour y accéder plus rapidement lorsque vous en aurez besoin ultérieurement. Tous les éléments épinglés s’affichent dans la section **Accès rapide** de Mon espace de travail.

* **Ouvrir dans Adobe Express** : modifiez une image dans Adobe Express intégré à partir de l’écran Experience Manager Assets.

* **Modifier** : modifiez l’image à l’aide d’Adobe Express.

* **Partager le lien** : [partagez des liens](share-links-for-assets-view.md) d’une ressource avec d’autres personnes, afin qu’elles puissent y accéder et la télécharger.

* **Supprimer** : supprimez une ressource.

* **Copier** : copiez une ressource vers un autre emplacement de dossier.

* **Déplacer** : déplacez une ressource vers un autre emplacement de dossier.

* **Renommer** : renommez une ressource.

* **Copier vers les bibliothèques** : ajoutez une ressource à la bibliothèque.

* **Affecter des tâches** : affectez des tâches aux utilisateurs et utilisatrices pour une ressource.

* **Surveiller** : [surveillez les opérations](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/assets/manage/search-assets) effectuées sur une ressource.

## Configurer la page d’accueil axée sur la recherche {#configuring-search-first-homepage}

La vue Assets vous permet de sélectionner la page de destination par défaut de votre organisation. Lorsque vous utilisez l’approche axée sur la recherche pour votre page d’accueil, vous disposez également d’options pour personnaliser l’image de marque de la page en configurant les images d’arrière-plan et du logo en fonction de votre marque.

Pour configurer la page d’accueil axée sur la recherche, exécutez les étapes ci-dessous :

1. Accédez à **[!UICONTROL Paramètres]** > **[!UICONTROL Paramètres généraux]**.
1. Sélectionnez **[!UICONTROL Approche axée sur la recherche]**. La configuration de l’approche axée sur la recherche s’ouvre. Vous pouvez définir l’[alignement](#setting-alignment-search-bar) ou l’[image de l’arrière-plan et du logo](#setting-background-image-and-logo) de votre page d’accueil.

### Définir l’alignement de la barre de recherche {#setting-alignment-search-bar}

[!DNL Assets view] vous permet de modifier l’alignement de la barre de recherche. Vous pouvez afficher la barre de recherche soit au centre, soit en haut. Sélectionnez l’alignement approprié et cliquez sur **[!UICONTROL Sauvegarder]**.

![Alignement de la page d’accueil axée sur la recherche.](assets/search-first-alignment.png)

### Définir l’image d’arrière-plan et le logo de la page d’accueil {#setting-background-image-and-logo}

Vous pouvez ajouter le logo de votre marque et une image d’arrière-plan à votre page d’accueil axée sur la recherche. Procédez comme suit :

1. Accédez à la section **[!UICONTROL Image d’arrière-plan et de logo]** sous **[!UICONTROL Page d’accueil]**.
1. Cliquez sur **[!UICONTROL Remplacer]** pour parcourir les images du référentiel de ressources.
1. Cliquez sur **[!UICONTROL Enregistrer]**. [Prévisualisez](#preview-configured-homepage) vos modifications.

### Prévisualiser la page d’accueil configurée {#preview-configured-homepage}

Vous pouvez prévisualiser votre page d’accueil axée sur la recherche afin d’en vérifier la disposition et le formatage. La fonction d’**[!UICONTROL Aperçu]** permet de corriger la mise en page ou d’apporter des modifications selon les besoins. Pour prévisualiser la page d’accueil configurée, exécutez les étapes ci-dessous :

1. Cliquez sur **[!UICONTROL Paramètres généraux]** et sélectionnez **[!UICONTROL Approche axée sur la recherche]**.
1. Accédez à **[!UICONTROL Personnaliser la page d’accueil axée sur la recherche]** et cliquez sur **[!UICONTROL Aperçu]**. Activez le bouton **[!UICONTROL Thème sombre]** pour prévisualiser la page d’accueil avec un thème sombre ou clair.
1. Cliquez sur **[!UICONTROL Fermer]** pour quitter l’écran d’aperçu.

   ![Aperçu de la page d’accueil axée sur la recherche.](/help/assets/assets/search-first-preview.gif)


<!--

## Contextual Search {#contextual-search}

You can also search assets available in the repository by defining text prompts. Experience Manager Assets automatically transforms those text prompts to search filters and displays the search results. You can view and modify automatic filters using the Filters Pane to further narrow down the search results.

### Access Contextual Search {#access-contextual-search}

To access Contextual Search in Experience Manager Assets:

1. Click **[!UICONTROL Search]** in the left pane.

   ![Contextual Search](assets/access-contextual-search.png)

1. Define the text prompt in the Search text box and click **[!UICONTROL Contextual Search]**.

   ![Contextual Search text prompt](/help/assets/assets/wknd-contextual-search.png)

   [!DNL Experience Manager Assets] displays the search results.

### Supported filters {#supported-filters}

Contextual Search supports the following filters out-of-the-box. Base your text prompts on these filters to view appropriate search results.

* Image height

* Image width

* File type: image, document, video, or folder.

* MIME type: JPG, PNG, TIFF, GIF, MP4, PDF, PPTX, DOCX or XLSX

* Created date

* Modified date

* Expiration date

* Asset status: Approved, Rejected, or all

* Expired assets

### Examples for the text prompts {#text-prompts-examples}

**Example 1**

**Text Prompt**: Images created this month.

[!DNL Experience Manager Assets] applies the following filters automatically and displays the search results:

![Contextual Search Example 1](assets/contextual-search-example1.png)

**Example 2**

**Text prompt**: Images at least 200px tall and 100px wide with beach and clear sky.

[!DNL Experience Manager Assets] applies the following filters automatically and displays the search results:

![Contextual Search Example 2](assets/contextual-search-example2.png)

**Example 3**

**Text prompt**: I need images of blue sky that are 1500 and 2500 pixel height and created in the past month that is not expired and approved.

[!DNL Experience Manager Assets] applies the following filters automatically and displays the search results:

![Contextual Search Example 3](assets/contextual-search-example3.png)

The following video illustrates the end-to-end process from accessing the Contextual Search User Interface to defining text prompts, and viewing the search results.

>[!VIDEO](https://video.tv.adobe.com/v/3428407)

### Disable Contextual Search {#disable-contextual-search}

Administrators also have the option to disable Contextual Search for users in your organization. To do so, execute the following steps:

1. Navigate to **[!UICONTROL Settings]** > **[!UICONTROL General Settings]**.

1. In the [!UICONTROL Contextual Search] section, turn off the **[!UICONTROL Enable Contextual Search for your organization]** toggle to disable the Contextual Search feature for all users in your organization.  

### Contextual Search feedback {#contextual-search-feedback}

If you need to provide feedback on the Contextual Search feature, click ![Contextual Search icon](assets/do-not-localize/Smock_Help_18_N.svg)  and click the Feedback icon. Select the feedback type, specify the subject and description, and click **[!UICONTROL Submit]**.

![Contextual Search feedback](assets/contextual-search-feedback.png)

-->

## Étapes suivantes {#next-steps}

* [Regardez une vidéo pour rechercher des ressources dans la vue Assets](https://experienceleague.adobe.com/docs/experience-manager-learn/assets-essentials/basics/using.html?lang=fr)

* Faites des commentaires sur le produit en utilisant l’option [!UICONTROL Commentaires] disponible dans l’interface utilisateur de la vue Assets

* Faites des commentaires sur la documentation en utilisant les options [!UICONTROL Modifier cette page] ![Modifier la page](assets/do-not-localize/edit-page.png) ou [!UICONTROL Enregistrer un problème] ![Créer un problème GitHub](assets/do-not-localize/github-issue.png) disponibles dans la barre latérale de droite.

* Contacter l’[assistance clientèle](https://experienceleague.adobe.com/?support-solution=General&lang=fr#support)



