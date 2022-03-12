---
title: Bannières de carrousel
description: Découvrez comment utiliser des bannières de carrousel dans Dynamic Media.
feature: Carousel Banners
role: User
exl-id: 34541302-6610-4f5e-af93-c95328dda910
source-git-commit: 24a4a43cef9a579f9f2992a41c582f4a6c775bf3
workflow-type: tm+mt
source-wordcount: '4535'
ht-degree: 100%

---

# Bannières de carrousel{#carousel-banners}

Les bannières de carrousel permettent aux spécialistes du marketing de susciter la conversion en créant facilement du contenu publicitaire interactif et alterné et en le diffusant sur tous les écrans.

La création et la modification du contenu présenté sur les bannières publicitaires peuvent prendre beaucoup de temps et réduire votre capacité à publier rapidement du contenu nouveau ou plus ciblé. Les bannières de carrousel vous permettent de créer ou de modifier rapidement des bannières rotatives et d’ajouter des éléments interactifs, tels que des liens de zones réactives vers les détails du produit ou les ressources connexes. Vous pouvez les diffuser sur n’importe quel écran, ce qui vous permet de diffuser plus rapidement du contenu promotionnel sur le marché.

Les bannières de carrousel sont signalées par une bannière contenant le mot **[!UICONTROL CAROUSELSET]** :

![chlimage_1-438](assets/chlimage_1-438.png)

Sur votre site web, la bannière de carrousel peut se présenter comme suit :

![chlimage_1-439](assets/chlimage_1-439.png)

Vous pouvez parcourir les images cliquant sur les numéros. De plus, les diapositives alternent automatiquement selon un intervalle personnalisable. Les images d’une bannière de carrousel prennent en charge les zones réactives et les zones cliquables. Les utilisateurs peuvent sélectionner un lien hypertexte ou accéder à une fenêtre Aperçu rapide.

Dans cet exemple, un utilisateur a sélectionné une zone cliquable et a accédé à la fenêtre d’aperçu rapide pour les gants :

![chlimage_1-440](assets/chlimage_1-440.png)

## Vidéo sur la création de bannières de carrousel {#watch-how-carousel-banners-are-created}

Regardez une présentation sur [la manière dont les bannières de carrousel sont créées](https://s7d5.scene7.com/s7viewers/html5/VideoViewer.html?videoserverurl=https://s7d5.scene7.com/is/content/&amp;emailurl=https://s7d5.scene7.com/s7/emailFriend&amp;serverUrl=https://s7d5.scene7.com/is/image/&amp;config=Scene7SharedAssets/Universal_HTML5_Video_social&amp;contenturl=https://s7d5.scene7.com/skins/&amp;asset=S7tutorials/InteractiveCarouselBanner) (Durée : 10 minutes et 33 secondes). Vous apprendrez également à prévisualiser, modifier et diffuser des bannières de carrousel.

>[!NOTE]
>
>Les utilisateurs non administrateurs doivent être ajoutés au groupe **[!UICONTROL dam-users]** de façon à pouvoir créer ou modifier des bannières de carrousel. Si vous rencontrez des problèmes lors de la création ou de la modification des bannières, contactez votre administrateur système pour qu’il vous ajoute au groupe **d[!UICONTROL am-users]**.

## Démarrage rapide : bannières de carrousel {#quick-start-carousel-banners}

Pour démarrer rapidement :

1. [Identifiez les variables de zone réactive et de zone cliquable](#identifying-hotspot-and-image-map-variables) (seulement pour les clients qui utilisent Adobe Experience Manager Assets et Dynamic Media).

   Commencez en identifiant les variables dynamiques utilisées par l’implémentation de l’aperçu rapide existant. Cela vous permet de saisir correctement les zones réactives et les données de zone cliquable pendant le processus de création de bannières de carrousel dans Experience Manager Assets.

<!-- LEAVE; COMMERCE BEING ADDED AGAIN IN THE FUTURE

   >[!NOTE]
   >
   >If you are an Experience Manager Sites or Ecommerce customer, you can use the built-in feature to navigate to product pages and lookup the existing skus in the product catalog. You do not need to manually enter hotspot or image map variables.
   >
   >
   >If you are an Experience ManagerAssets and Dynamic Media customer, you will manually enter data for hotspots and image maps, and then integrate the published URL or Embed code with your third-party content management system.

-->

1. Facultatif : [créez un paramètre prédéfini d’ensemble de carrousel](/help/assets/dynamic-media/managing-viewer-presets.md), au besoin.

   Si vous êtes administrateur, vous pouvez personnaliser le comportement et l’apparence du carrousel en créant votre propre paramètre prédéfini de visionneuse de carrousel. L’avantage principal est que vous pouvez réutiliser ce paramètre prédéfini de visionneuse personnalisé pour plusieurs carrousels. Cependant, les utilisateurs ont également la possibilité de personnaliser le comportement et l’apparence du carrousel directement lors de sa création. Cette approche est recommandée lorsque vous souhaitez une conception très spécifique pour un carrousel donné.

1. [Chargez une bannière d’image](#uploading-image-banners).

   Chargez les bannières d’images que vous souhaitez rendre interactives.

1. [Créez un ensemble de carrousels](#creating-carousel-sets).

   Dans les ensembles de carrousels, les utilisateurs parcourent les images de bannière et sélectionnent les zones réactives ou cliquables pour accéder au contenu approprié.

   Pour créer un ensemble de carrousel dans Assets, sélectionnez **[!UICONTROL Créer]**, puis sélectionnez **[!UICONTROL Ensembles de carrousels]**. Ajoutez des ressources aux diapositives et sélectionnez **[!UICONTROL Enregistrer]**. Vous pouvez également modifier l’apparence et le comportement du carrousel directement dans l’éditeur.

1. [Ajoutez des zones réactives ou cliquables dans une bannière d’image](#adding-hotspots-or-image-maps-to-an-image-banner).

   Ajoutez une ou plusieurs zones réactives ou zones cliquables sur une bannière d’images. Ensuite, associez chacun d’entre eux à une action telle qu’un lien, un aperçu rapide ou un fragment d’expérience. Une fois que vous avez ajouté des zones réactives ou des zones cliquables, vous terminez cette tâche en modifiant l’ensemble de carrousel. La publication crée le code intégré que vous copiez et appliquez à la page d’entrée de votre site web.

   Voir [(Facultatif) Aperçu des bannières de carrousel](#optional-previewing-carousel-banners). Si vous le souhaitez, vous pouvez afficher une représentation de l’ensemble de carrousel et tester son interactivité.

1. [Publiez les bannières de carrousel](#publishing-carousel-banners).

   Vous publiez un ensemble de carrousel comme vous le feriez pour d’autres ressources. Dans Ressources, accédez à l’ensemble de carrousel, sélectionnez-le et sélectionnez **[!UICONTROL Publier]**. La publication d’un ensemble de carrousel active l’URL et la chaîne incorporée.

1. Utilisez l’une des méthodes suivantes :

   * [Ajoutez une bannière de carrousel à votre page web.](#adding-a-carousel-banner-to-your-website-page)Vous pouvez ajouter le code intégré ou l’URL de la bannière de carrousel que vous avez copié sur la page web.

      * [Intégrez la bannière de carrousel à un aperçu rapide existant](#integrating-the-carousel-banner-with-an-existing-quickview). Si vous utilisez un système de gestion de contenu web externe, vous devez intégrer la nouvelle bannière de carrousel à la mise en œuvre de l’aperçu rapide existant sur votre site web.
   * [Ajoutez une bannière de carrousel à votre site web dans Experience Manager](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md). Si vous êtes client Experience Manager Sites, vous pouvez ajouter l’ensemble de carrousel directement dans la page à l’aide du composant Interactive Media.


Si vous devez modifier des ensembles de carrousels, consultez [Modification d’ensembles de carrousels](#editing-carousel-sets). De plus, vous pouvez afficher et modifier les [propriétés d’un ensemble de carrousel](/help/assets/manage-digital-assets.md#editing-properties).

## Identification des variables de zone réactive et de zone cliquable {#identifying-hotspot-and-image-map-variables}

Commencez en identifiant les variables dynamiques utilisées par l’implémentation de l’aperçu rapide existant. Cette méthode vous permet de saisir correctement les zones réactives ou les données de zone cliquable pendant le processus de création de l’ensemble de carrousel dans Experience Manager Assets.

Lorsque vous ajoutez des zones réactives ou des zones cliquables à une image de bannière, vous affectez un SKU (Stock Keeping Unit). Vous pouvez également affecter des variables supplémentaires facultatives à chaque zone réactive ou zone cliquable. Ces variables sont utilisées, par la suite, pour faire correspondre les zones réactives ou les zones cliquables au contenu de l’aperçu rapide.

<!-- LEAVE; COMMERCE BEING ADDED LATER

>[!NOTE]
>
>If you are an Experience Manager Sites and/or Experience Manager Ecommerce customer, skip this step. You do not need to manually identify hotspot or image map variables; you can use the integration with Ecommerce for product integration. See information on [setting up eCommerce](/help/sites-cloud/administering/generic.md). In addition, you can use the Interactive component and add it to your web page.
>
>If you are an Experience Manager Assets or Media customer, you publish the URL or Embed code and then integrate with your third-party content management system and identify hotspots and image maps manually.

-->

Il est important d’identifier correctement le nombre et le type des variables à associer aux données des zones réactives ou des zones cliquables. Chaque zone réactive ou zone cliquable ajoutée à une image de bannière doit comporter suffisamment d’informations pour identifier clairement le produit sur le système back-end existant. En même temps, assurez-vous que chaque zone réactive ou zone cliquable ne comporte pas plus de données que nécessaire. Cela rendrait la procédure de saisie des données trop complexe et favoriserait les erreurs de gestion des zones réactives ou des zones cliquables.

Il existe différentes façons d’identifier une série de variables à utiliser pour les données de zone réactive ou de zone cliquable.

Il suffit parfois de consulter les spécialistes informatiques chargés de la mise en œuvre de l’aperçu rapide existant. Ils sont susceptibles de connaître l’ensemble minimal de données permettant d’identifier l’aperçu rapide dans le système. Cependant, il est possible d’analyser le comportement existant du code en front-end.

La plupart des implémentations d’aperçu rapide utilisent le modèle suivant :

* L’utilisateur active un élément d’interface utilisateur sur le site web. Par exemple, en sélectionnant un bouton **[!UICONTROL Aperçu rapide]**.
* Le site web envoie une demande Ajax au serveur back-end afin de charger les données ou le contenu de l’aperçu rapide, le cas échéant.
* Les données de l’aperçu rapide sont traduites en contenu en préparation du rendu sur la page web.
* Enfin, le code en front-end effectue le rendu visuel de ce contenu à l’écran.

L’approche consiste ensuite à visiter différentes zones du site web existant dans lequel la fonction Aperçu rapide est implémentée. Ensuite, déclenchez l’aperçu rapide et capturez l’URL Ajax envoyée par la page web pour charger les données ou le contenu de cet aperçu.

Normalement, il n’est pas nécessaire d’utiliser des outils de débogage spécialisés. Les navigateurs web modernes incluent des inspecteurs web qui font un travail correct. Vous trouverez ci-dessous quelques exemples de navigateurs web qui incluent des inspecteurs web :

* Pour afficher toutes les requêtes HTTP sortantes dans Google Chrome, appuyez sur la touche F12 (Windows®) ou Commande-Option-I (Mac) pour ouvrir le panneau de l’outil de développement. Sélectionnez l’onglet Réseau.
* Dans Firefox, vous pouvez activer le module externe Firebug en appuyant sur F12 (Windows®) ou sur Commande-Option-I (Mac). Utilisez l’onglet Réseau ou encore l’outil Inspecteur intégré et son onglet Réseau.

Lorsque la surveillance de réseau est activée dans le navigateur, déclenchez l’aperçu rapide sur la page.

Vous trouvez maintenant l’URL Ajax d’aperçu rapide dans le journal réseau. Copiez l’URL enregistrée pour l’analyse ultérieure. Généralement, lorsque vous déclenchez l’aperçu rapide, plusieurs requêtes sont envoyées au serveur. En règle générale, l’URL Ajax d’aperçu rapide est l’une des premières dans la liste. Elle possède une partie de chaîne de requête complexe ou un chemin d’accès, et son type de réponse MIME est `text/html`, `text/xml` ou `text/javascript`.

Au cours de ce processus, il est important de parcourir différentes zones de votre site web, avec différentes catégories et types de produits. C’est pourquoi les URL d’aperçu rapide peuvent avoir des parties communes pour une catégorie de site web donnée, mais ne changent que si vous visitez une autre zone du site web.

Dans le cas le plus simple, la seule partie variable dans l’URL de l’aperçu rapide est le SKU du produit. Dans ce cas, la valeur de la SKU est la seule donnée dont vous avez besoin pour ajouter des zones réactives ou des zones cliquables à l’image de bannière.

Toutefois, dans des cas complexes, l’URL d’aperçu rapide comporte différents éléments variables en plus du SKU. Certains de ces éléments incluent l’ID de la catégorie, le code couleur, le code de taille, etc. Dans ce cas, chaque élément est une variable distincte dans la définition des données de zone réactive ou de zone cliquable dans la fonction de bannière de carrousel.

Consultez les exemples d’URL d’aperçu rapide ci-dessous et les variables de zone réactive et de zone cliquable obtenues :

<table>
 <tbody>
  <tr>
   <td>SKU unique, trouvé dans la chaîne de requête.</td>
   <td><p>Les URL d’aperçu rapide enregistrées incluent ce qui suit :</p>
    <ul>
     <li><p><code>https://server/json?productId=866558&amp;source=100</code></p> </li>
     <li><p><code>https://server/json?productId=1196184&amp;source=100</code></p> </li>
     <li><p><code>https://server/json?productId=1081492&amp;source=100</code></p> </li>
     <li><p><code>https://server/json?productId=1898294&amp;source=100</code></p> </li>
    </ul> <p>La seule partie variable de l’URL est la valeur du paramètre de chaîne de requête <code>productId=</code>, et il s’agit clairement d’une valeur de SKU. Par conséquent, il suffit d’indiquer dans les champs de SKU des zones réactives ou cliquables des valeurs telles que <code>866558,</code> <code>1196184,</code> <code>1081492,</code> <code>1898294.</code></p> </td>
  </tr>
  <tr>
   <td>SKU unique, trouvé dans le chemin d’accès à l’URL.</td>
   <td><p>Les URL d’aperçu rapide enregistrées incluent ce qui suit :</p>
    <ul>
     <li><p><code>https://server/product/6422350843</code></p> </li>
     <li><p><code>https://server/product/1607745002</code></p> </li>
     <li><p><code>https://server/product/0086724882</code></p> </li>
    </ul> <p>La partie variable se trouve dans la dernière partie du chemin et elle devient la valeur de SKU des zones réactives/cliquables : <strong><code>6422350843</code>, <code>1607745002,</code> </strong><code>0086724882.</code>.</p> </td>
  </tr>
  <tr>
   <td>SKU et ID de catégorie dans la chaîne de requête.</td>
   <td><p>Les URL d’aperçu rapide enregistrées incluent ce qui suit :</p>
    <ul>
     <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=305466</code></p> </li>
     <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=310181</code></p> </li>
     <li><p><code>https://server/quickView/product/?category=1740148&amp;prodId=308706</code></p> </li>
    </ul> <p>Dans ce cas, l’URL comporte deux parties différentes. Le SKU est stocké dans le paramètre <code>prodId</code> et l’ID de catégorie est stocké dans le paramètre <code>category=</code>.</p> <p>En tant que telles, les définitions zone réactive/zone cliquable sont des paires. Autrement dit, une valeur de SKU et une variable supplémentaire appelée « <code>categoryId</code> ». Les paires obtenues sont les suivantes :</p>
    <ul>
     <li><p>Le SKU est <strong><code>305466</code></strong> et <code>categoryId</code> est <code>1100004</code>.</p> </li>
     <li><p>Le SKU est <strong><code>310181</code></strong> et <code>categoryId</code> est <strong><code>1100004</code></strong>.</p> </li>
     <li><p>Le SKU est <strong><code>308706</code></strong> et <code>categoryId</code> est <strong><code>1740148</code></strong>.</p> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## Chargement des bannières d’image {#uploading-image-banners}

Si vous avez déjà chargé les images à utiliser, passez à l’étape suivante, [Création d’ensembles de carrousels](#creating-carousel-sets). Les images utilisées dans le carrousel doivent être chargées une fois que Dynamic Media a été activé.

Pour charger des bannières d’image, voir [Chargement de ressources](/help/assets/manage-digital-assets.md).

## Création d’ensembles de carrousels {#creating-carousel-sets}

>[!NOTE]
>
>Les utilisateurs non administrateurs doivent être ajoutés au groupe **[!UICONTROL dam-users]** de façon à pouvoir créer ou modifier des bannières de carrousel. Si vous rencontrez des problèmes lors de la création ou de la modification des bannières, contactez votre administrateur système pour qu’il vous ajoute au groupe **[!UICONTROL DAM-users]**.

**Pour créer des ensembles de carrousels :**

1. Dans Ressources, cherchez le dossier dans lequel vous souhaitez créer l’ensemble de carrousel, puis accédez à **[!UICONTROL Créer > Ensemble de carrousel]**.
1. Dans la page de l’éditeur de bannière de carrousel, sélectionnez **[!UICONTROL ouvrir le sélecteur de ressources]** pour sélectionner l’image de votre première diapositive.

   Dans la page de l’éditeur de bannières de carrousel, effectuez l’une des actions suivantes :

   * Dans le coin supérieur gauche de la page, sélectionnez l’icône **[!UICONTROL Ajouter une diapositive]**.

   * Près du milieu de la page, sélectionnez **[!UICONTROL Appuyer pour ouvrir le sélecteur de ressources]**.

   Sélectionnez pour sélectionner les ressources à inclure dans votre ensemble de carrousel. Les ressources sélectionnées sont cochées. Lorsque vous avez terminé, en haut à droite de la page, sélectionnez **[!UICONTROL Sélectionner]**.

   Le sélecteur de ressources vous permet de rechercher des ressources en saisissant un mot-clé, puis sélectionnant **[!UICONTROL Retour]**. Vous pouvez également appliquer des filtres pour affiner vos résultats de recherche. Vous pouvez filtrer par chemin, collection, type de fichier et balise. Sélectionnez le filtre, puis sélectionnez l’icône **[!UICONTROL Filtre]** de la barre d’outils. Modifiez l’affichage en sélectionnant l’icône Affichage et en sélectionnant **[!UICONTROL Mode Colonnes]**, **[!UICONTROL Mode Carte]** ou **[!UICONTROL Mode Liste]**.

   Pour plus d’informations, voir [Utilisation de sélecteurs](/help/assets/dynamic-media/working-with-selectors.md).

1. Continuez à ajouter des diapositives jusqu’à ce que vous ayez ajouté toutes les images à faire pivoter dans l’ensemble de carrousel.
1. (En option) Effectuez l’une des actions suivantes :

   * Si nécessaire, faites glisser les diapositives pour réorganiser la liste des images à insérer.
   * Pour supprimer une image, sélectionnez-la, puis sélectionnez **[!UICONTROL Supprimer la diapositive]** dans la barre d’outils.

   * Pour appliquer un préréglage, à proximité du coin supérieur droit de la page, sélectionnez la liste déroulante de paramètres prédéfinis, puis sélectionnez un paramètre prédéfini à appliquer à l’ensemble simultanément.

   Pour supprimer une diapositive, sélectionnez-la. Dans la barre d’outils, sélectionnez **[!UICONTROL Supprimer la diapositive]**. Pour déplacer une diapositive, sélectionnez l’icône Réorganiser et déplacez jusqu’à l’emplacement souhaité.

1. Une fois que vous avez ajouté les images aux diapositives, vous pouvez ajouter à votre image une zone réactive, une zone cliquable, ou les deux. Voir [Ajout de zones réactives ou cliquables dans une bannière d’image](#adding-hotspots-or-image-maps-to-an-image-banner).
1. Vous pouvez modifier le design visuel et le comportement des ensembles de carrousels. Sélectionnez les onglets **[!UICONTROL Comportement]** et **[!UICONTROL Apparence]** si vous souhaitez ajuster l’affichage de la bannière de carrousel ou le comportement de composants spécifiques. Pour plus d’informations sur l’utilisation de l’éditeur de visionneuses, reportez-vous à la section [Gestion des paramètres prédéfinis de visionneuse](/help/assets/dynamic-media/viewer-presets.md).

   >[!NOTE]
   >
   >Pour les bannières de carrousel, vous pouvez ajuster les éléments suivants :
   >
   >* Durée pendant laquelle une image est affichée. Par défaut, chaque image s’affiche pendant 9 secondes.
   >* Animation. Par défaut, la transition entre chaque diapositive est un fondu. Vous pouvez prévoir une transition affichant une diapositive.
   >* Style des boutons. Les utilisateurs peuvent faire alterner les bannières en sélectionnant chaque point ou numéro. Vous pouvez modifier l’emplacement d’affichage des boutons de définition des indicateurs (et s’ils sont de style numérique ou en pointillé) et leur taille.
   >* Modification du style de mise en évidence d’une zone cliquable ou de l’icône utilisée pour les zones réactives.
   >* Avant de modifier un paramètre prédéfini de visionneuse, choisissez le style sur laquelle vous souhaitez fonder ce paramètre. Sans cela, lorsque vous commencerez à modifier le paramètre prédéfini de visionneuse, vous perdrez toutes les modifications si vous changez de paramètre prédéfini..


   Vous pouvez également prévisualiser l’aspect de la bannière de carrousel. Voir [(Facultatif) Aperçu des bannières de carrousel](#optional-previewing-carousel-banners).

1. Lorsque vous avez terminé, sélectionnez **[!UICONTROL Enregistrer]**.

## Ajout de zones réactives ou cliquables dans une bannière d’image {#adding-hotspots-or-image-maps-to-an-image-banner}

Vous pouvez ajouter des zones réactives ou des zones cliquables à une bannière à l’aide de l’éditeur d’ensemble de carrousel.

Lorsque vous ajoutez des zones réactives ou cliquables, vous pouvez les définir comme un écran contextuel d’aperçu rapide, un lien hypertexte ou un fragment d’expérience.

Voir [Fragment d’expérience](/help/sites-cloud/authoring/fundamentals/experience-fragments.md).

>[!NOTE]
>
>Les outils de partage sur les médias sociaux ne sont pas pris en charge dans la bannière de carrousel lorsque vous incorporez la visionneuse dans un fragment d’expérience.
>
>Pour contourner ce problème, vous pouvez utiliser ou créer des paramètres prédéfinis de visionneuse qui ne disposent pas d’outils de partage sur les médias sociaux. Ces paramètres prédéfinis de visionneuse vous permettent de l’incorporer dans des fragments d’expérience.

À mesure que vous ajoutez des zones réactives ou des zones cliquables à une image, pensez à enregistrer votre travail. Les options Annuler et Rétablir, proches du coin supérieur droit de la page, sont prises en charge au cours de la session de création/modification actuelle.

Lorsque vous avez fini de créer votre bannière de carrousel, vous pouvez utiliser l’aperçu pour afficher une représentation de votre bannière de carrousel telle qu’elle s’affiche pour les clients.

Voir [(Facultatif) Aperçu des bannières de carrousel](#optional-previewing-carousel-banners).

>[!NOTE]
>
>Lorsque vous ajoutez des zones réactives à une bannière d’images, les informations de ces zones réactives sont stockées au même emplacement de métadonnées que celles de l’image. Ce point est vrai, qu’il s’agisse d’une image interactive ou d’une bannière de carrousel. Cette fonctionnalité signifie que vous pouvez réutiliser facilement la même image (avec ses données de zone réactive définies) dans les visionneuses.
>Notez cependant que les bannières de carrousel prennent en charge les images à zones cliquables, qui peuvent également contenir des zones réactives. Les images interactives n’en comportent pas. Pensez-y si vous envisagez de créer une image interactive ou une bannière de carrousel qui utilise la même image. Envisagez de créer des images interactives et des bannières de carrousel en utilisant des copies distinctes de la même image à la place.

>[!NOTE]
>Si vous modifiez des images interactives avec des zones réactives et que vous recadrez l’image, les zones réactives sont supprimées.

<!-- See also [Adding Image Maps](/help/assets/image-maps.md). -->

**Pour ajouter des zones réactives ou cliquables à une bannière d’image :**

1. À partir de Ressources, accédez à l’ensemble de carrousel auquel vous souhaitez ajouter de l’interactivité.
1. Sélectionnez l’ensemble de carrousel et sélectionnez **[!UICONTROL Modifier]**. L’éditeur de visionneuses de carrousel s’affiche.
1. Sélectionnez la diapositive à laquelle vous souhaitez ajouter de l’interactivité.
1. Dans le coin supérieur gauche de la page, sélectionnez **[!UICONTROL Zone réactive]** ou **[!UICONTROL Zone cliquable]**.
1. Effectuez l’une des opérations suivantes :

   * Pour les zones réactives : sur l’image, sélectionnez un emplacement où vous souhaitez que la zone réactive apparaisse.
   * Pour les zones cliquables : sur l’image, faites glisser depuis le coin supérieur gauche vers le coin inférieur droit pour créer la zone cliquable. Vous pouvez ajuster la taille de la zone cliquable en faisant glisser les coins.

   Si nécessaire, faites glisser la zone réactive ou la zone cliquable vers un nouvel emplacement. Vous pouvez également utiliser les touches fléchées du clavier pour contrôler la position d’une zone réactive sélectionnée. Ajoutez plus de zones réactives ou cliquables si nécessaire.

   Pour supprimer une zone réactive ou une zone cliquable, sélectionnez l’onglet **[!UICONTROL Actions]**. Sous l’en-tête **[!UICONTROL Cartes et zone réactives]**, dans la liste déroulante **[!UICONTROL Type sélectionné]**, sélectionnez le nom de la zone réactive ou de l’image cliquable à supprimer. Sélectionnez l’icône **[!UICONTROL Corbeille]** en regard du menu, puis sélectionnez **[!UICONTROL Supprimer]**.

1. Dans le champ de texte Nom, entrez le nom de la zone réactive ou de la zone cliquable. Ce nom s’affiche également dans la liste déroulante **[!UICONTROL Cartes et zones réactives]**. Le fait de fournir un nom facilite l’identification de la zone réactive ou de la zone cliquable si vous décidez de le modifier ultérieurement.
1. Effectuez l’une des actions disponibles sur l’onglet **[!UICONTROL Actions]** :

   * Sélectionnez **[!UICONTROL Aperçu rapide]**.

      * Si vous êtes un client Experience Manager Sites <!-- and Ecommerce-->, sélectionnez l’icône de sélecteur de produit (loupe) afin d’afficher la page Sélectionner un produit. Pour revenir à l’éditeur de bannières de carrousel, sélectionnez le produit que vous souhaitez utiliser, puis sélectionnez la case à cocher située dans l’angle supérieur droit de la page.
      * Si vous n’êtes pas un client Experience Manager Sites <!-- or Ecommerce --> :

         * Définissez des variables. Voir [Identification des variables des zones réactives](#identifying-hotspot-and-image-map-variables).
         * Ensuite, entrez manuellement la valeur de SKU. Dans le champ de texte Valeur de SKU, entrez la SKU, qui est un identifiant unique pour chaque produit ou service que vous proposez. La valeur SKU saisie renseigne automatiquement la partie variable du modèle d’aperçu rapide. Le système sait désormais associer la zone réactive sélectionnée avec l’aperçu rapide d’un SKU en particulier.
         * (Facultatif) S’il existe d’autres variables dans l’aperçu rapide que vous devez utiliser pour identifier un produit, sélectionnez **[!UICONTROL Ajouter la variable générique]**. Dans le champ de texte, spécifiez une variable supplémentaire. Par exemple, category=Mens est une variable ajoutée.

         * Pour plus d’informations, voir [Utilisation de sélecteurs](/help/assets/dynamic-media/working-with-selectors.md).
   * Sélectionnez **[!UICONTROL Lien hypertexte]**.

      * Si vous êtes client Experience Manager Sites, sélectionnez l’icône Sélecteur de site (dossier) pour accéder à une URL.

         >[!NOTE]
         >La méthode de liaison basée sur une URL n’est pas possible si votre contenu interactif contient des liens avec des URL relatives, en particulier des liens vers des pages Experience Manager Sites.

      * Si vous êtes un client autonome, dans la zone de texte href, spécifiez le chemin URL complet vers une page web liée.

   Veillez à spécifier si vous souhaitez ouvrir le lien dans un nouvel onglet du navigateur (paramètre par défaut recommandé) ou dans le même onglet.

   Pour plus d’informations, voir [Utilisation de sélecteurs](/help/assets/dynamic-media/working-with-selectors.md).

   * Sélectionnez **[!UICONTROL Fragment d’expérience]**.

      * Si vous êtes client Experience Manager Sites, sélectionnez l’icône Rechercher (loupe) afin d’ouvrir la page Fragment d’expérience. Pour revenir à la page de gestion des zones réactives, sélectionnez le fragment d’expérience à utiliser, puis sélectionnez **[!UICONTROL Sélectionner]** dans le coin supérieur droit de la page.
Voir [Fragments d’expérience](/help/sites-cloud/authoring/fundamentals/experience-fragments.md).

      * Indiquez la largeur et la hauteur du fragment d’expérience tel qu’il apparaît dans la bannière.

         >[!NOTE]
         >Les outils de partage sur les médias sociaux ne sont pas pris en charge dans la bannière de carrousel lorsque vous incorporez la visionneuse dans un fragment d’expérience.
         >Pour contourner ce problème, vous pouvez utiliser ou créer des paramètres prédéfinis de visionneuse qui ne disposent pas d’outils de partage sur les médias sociaux. Ces paramètres prédéfinis de visionneuse vous permettent de l’incorporer dans des fragments d’expérience.

   ![experience_fragment-carouselbanner](assets/experience_fragment-carouselbanner.png)

   Vous pouvez également prévisualiser l’aspect de la bannière de carrousel. Voir [(Facultatif) Aperçu des bannières de carrousel](#optional-previewing-carousel-banners).

1. Sélectionnez **[!UICONTROL Enregistrer]**.
1. Publiez l’ensemble de carrousel. La publication crée le code intégré ou l’URL que vous pouvez utiliser dans votre page web. Si vous êtes un client Sites Experience Manager, ajoutez l’ensemble de carrousel directement à votre page web.

   Voir [Publication de ressources](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

   Voir [Ajout d’un ensemble de carrousel à la page d’entrée de votre site web](#adding-a-carousel-banner-to-your-website-page).

## Modification d‘ensembles de carrousels {#editing-carousel-sets}

>[!NOTE]
>Les utilisateurs non administrateurs doivent être ajoutés au groupe **[!UICONTROL dam-users]** de façon à pouvoir créer ou modifier des bannières de carrousel. Si vous rencontrez des problèmes lors de la création ou de la modification des bannières, contactez votre administrateur système pour qu’il vous ajoute au groupe **[!UICONTROL DAM-users]**.

Vous pouvez effectuer diverses tâches de modification sur les visionneuses de carrousel, telles que :

* Ajouter des diapositives à l’ensemble de carrousel. Voir également [Utilisation de sélecteurs](/help/assets/dynamic-media/working-with-selectors.md).
* Réorganiser les diapositives dans l’ensemble de carrousel.
* Supprimer des ressources de l’ensemble de carrousel.
* Appliquer des paramètres prédéfinis de visionneuse.
* Supprimer l’ensemble de carrousel.
* Ajouter ou modifier des zones réactives et des zones cliquables. Voir également [Utilisation de sélecteurs](/help/assets/dynamic-media/working-with-selectors.md).

**Pour modifier des ensembles de carrousels :**

1. Effectuez l’une des opérations suivantes :

   * Pointez sur une ressource d’ensemble de carrousel, puis sélectionnez **[!UICONTROL Modifier]** (icône crayon).
   * Pointez sur une ressource d’ensemble de carrousel, sélectionnez **[!UICONTROL Sélectionner]** (icône représentant une coche), puis, sur la barre d’outils, sélectionnez **[!UICONTROL Modifier]**.

   * Sélectionnez une ressource de l’ensemble de carrousel, puis, dans le coin supérieur gauche de la page, sélectionnez **[!UICONTROL Modifier]** (icône en forme de crayon).

1. Pour modifier l’ensemble de carrousel, effectuez l’une des opérations suivantes :

   * Pour ajouter une diapositive, sélectionnez l’icône **[!UICONTROL Ajouter une diapositive]**. Accédez à la ressource que vous souhaitez ajouter à cette diapositive, puis sélectionnez la case à cocher.
   * Pour réorganiser les diapositives, faites glisser une diapositive vers un nouvel emplacement (sélectionnez l’icône Réorganiser pour déplacer les éléments).
   * Pour ajouter une zone réactive ou une zone cliquable, sélectionnez l’icône Zone réactive ou Zone cliquable et reportez-vous à la section [Ajout de zones réactives et de zones cliquables](#adding-hotspots-or-image-maps-to-an-image-banner).
   * Pour modifier l’aspect ou le comportement de l’ensemble de carrousel, sélectionnez l’onglet **[!UICONTROL Apparences]** ou l’onglet **[!UICONTROL Comportement]**, puis définissez les options de votre choix.
   * Pour modifier des zones réactives ou des zones cliquables, sélectionnez une zone réactive ou une zone cliquable dans la diapositive concernée. Sous l’onglet **[!UICONTROL Actions]**, apportez vos modifications.
   * Pour supprimer une diapositive, sélectionnez-la, puis sélectionnez **[!UICONTROL Supprimer la diapositive]** dans la barre d’outils.
   * Pour appliquer un paramètre prédéfini, à proximité du coin supérieur droit de la page, sélectionnez la liste déroulante **[!UICONTROL Paramètre prédéfini]**, puis sélectionnez un paramètre prédéfini de visionneuse.
   * Pour supprimer un ensemble de carrousel en entier, accédez-y, sélectionnez-le et sélectionnez **[!UICONTROL Supprimer]**.

   >[!NOTE]
   >Si vous modifiez des images interactives avec des zones réactives et que vous recadrez l’image, les zones réactives sont supprimées.

## (Facultatif) Aperçu des bannières de carrousel {#optional-previewing-carousel-banners}

Vous pouvez utiliser l’aperçu pour afficher la bannière de carrousel à l’intention des clients. L’utilisation de la Prévisualisation vous permet également de tester les zones réactives et cliquables de la bannière du carrousel afin de vous assurer qu’elles se comportent comme prévu.

Lorsque vous êtes satisfait de la bannière de carrousel, vous pouvez la publier.
Voir [Incorporation de la visionneuse de vidéos ou d’images dans une page web](/help/assets/dynamic-media/embed-code.md).
Voir [Liaison d’URL à une application web](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md). La méthode de liaison basée sur une URL n’est pas possible si votre contenu interactif contient des liens avec des URL relatives, en particulier des liens vers des pages Experience Manager Sites.
Voir [Ajout de ressources Dynamic Media aux pages](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).

Vous pouvez afficher un aperçu des bannières de carrousel dans l’éditeur de carrousel (méthode recommandée) ou dans la liste **[!UICONTROL Visionneuses]**.

**Pour prévisualiser de façon facultative les bannières de carrousel :**

1. Dans **[!UICONTROL Ressources]**, accédez à une bannière de carrousel que vous avez créée et sélectionnez pour l’afficher.
1. Sélectionnez **[!UICONTROL Modifier]**.
1. Dans la liste des paramètres prédéfinis de visionneuse dans le coin supérieur droit de la barre d’outils, sélectionnez une visionneuse pour afficher un aperçu de la bannière de carrousel.

   ![experience_fragment-carouselbanner-viewerdropdown](assets/experience_fragment-carouselbanner-viewerdropdown.png)

1. Sélectionnez **[!UICONTROL Aperçu]**.
1. Pour tester les actions associées, sélectionnez les zones réactives ou cliquables de l’image.

**Pour afficher un aperçu des bannières de carrousel à partir de la liste Visionneuses :**

1. Dans **[!UICONTROL Ressources]**, accédez à une bannière de carrousel que vous avez créée et sélectionnez pour l’afficher.
1. Dans le coin supérieur gauche de la page Aperçu, sélectionnez l’icône Contenu.
1. Dans la liste **[!UICONTROL Visionneuses]** du panneau situé du côté gauche de la page, sélectionnez le nom du paramètre prédéfini de visionneuse de bannière de carrousel que vous souhaitez utiliser.
1. Pour tester les actions associées, sélectionnez les zones réactives ou cliquables de l’image.

## Publiez les bannières de carrousel {#publishing-carousel-banners}

Pour utiliser le carrousel, vous devez le publier. La publication d’un ensemble de carrousel active l’URL et le code intégré. Elle publie également le carrousel sur le cloud Dynamic Media intégré au CDN pour un débit évolutif et performant.

>[!NOTE]
>Si vous utilisez une image interactive existante avec des zones réactives pour la bannière de carrousel, vous devez publier l’image interactive séparément après avoir publié la bannière de carrousel.
>De plus, si vous modifiez une image interactive publiée existante que vous utilisez dans une bannière de carrousel, publiez l’image interactive pour que ces modifications se répercutent sur la bannière de carrousel.

Voir [Publication de ressources Dynamic Media](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md) pour savoir comment publier des bannières de carrousel.

## Ajoutez une bannière de carrousel à votre page web. {#adding-a-carousel-banner-to-your-website-page}

Après avoir téléchargé des images de bannière pour créer un carrousel, ajouté des zones réactives ou des zones cliquables, ou les deux, à la bannière. Publié l’ensemble de carrousel. Vous êtes maintenant prêt à l’ajouter à votre page de site web existante.

>[!NOTE]
>Si vous êtes client Experience Manager Sites, vous pouvez ajouter la bannière de carrousel directement dans votre page en faisant glisser le composant Interactive Media dans votre page. Voir [Ajout de ressources Dynamic Media aux pages](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).

Cependant, si vous êtes un client Experience Manager Assets autonome, vous pouvez ajouter manuellement la bannière du carrousel à la page d’entrée de votre site web.

1. Copiez le code intégré de l’ensemble de carrousel.
Voir [Incorporation de la visionneuse de vidéos ou d’images dans une page web](/help/assets/dynamic-media/embed-code.md).

1. Ajoutez le code incorporé que vous avez copié à partir d’Experience Manager Assets sur votre page web.
Le code intégré copié est réactif et s’adapte donc automatiquement à la zone d’incorporation de la page.

## Intégration de la bannière de carrousel à un aperçu rapide existant {#integrating-the-carousel-banner-with-an-existing-quickview}

Remarque : Cette étape ne vous concerne que si vous êtes un client Experience Manager Assets autonome.

La dernière étape de cette procédure consiste à intégrer la bannière de carrousel à la mise en œuvre d’un aperçu rapide existant à votre site web. Chaque mise en œuvre de l’aperçu rapide est unique, et une approche spécifique est nécessaire, ce qui implique généralement l’assistance d’un informaticien compétent en systèmes frontaux.

L’implémentation d’aperçus rapides existante représente normalement une chaîne d’actions entre-associées qui se produisent sur la page web dans l’ordre suivant :

1. Un utilisateur déclenche un élément dans l’interface utilisateur de votre site web.
1. Le code en front-end obtient une URL d’aperçu rapide basée sur l’élément d’interface utilisateur qui a été déclenché à l’étape 1.
1. Le code en front-end envoie une demande Ajax en utilisant l’URL obtenue à l’étape 2.
1. La logique du serveur principal renvoie les données ou le contenu de l’aperçu rapide correspondant au code en front-end.
1. Le code en front-end charge les données ou le contenu de l’aperçu rapide.
1. Facultativement, le code en front-end convertit les données chargées de l’aperçu rapide en une représentation HTML.
1. Le code en front-end affiche une boîte de dialogue ou un panneau modal et effectue le rendu du contenu HTML à l’écran pour l’utilisateur final.

Ces appels ne représentent pas des appels d’API publics indépendants qui peuvent être appelés par la logique de page web à partir d’une étape arbitraire. Il s’agit plutôt d’un appel chaîné où chaque étape suivante est masquée dans la dernière phase (rappel) de l’étape précédente.

Alors que la bannière de carrousel remplace l’étape 1, et partiellement l’étape 2, lorsqu’un utilisateur sélectionne une zone réactive ou une zone cliquable, cette interaction est gérée par la visionneuse. La visionneuse renvoie un événement dans la page web qui contient les données de toutes les zones réactives ou les zones cliquables ajoutées précédemment.

Dans ce type de gestionnaire d’événements, le code en front-end effectue les opérations suivantes :

* Écoute un événement émis par la bannière de carrousel.
* Crée une URL d’aperçu rapide d’après les données des zones réactives ou des zones cliquables.
* Déclenche le processus de chargement de l’aperçu rapide depuis le serveur principal et en effectue le rendu à l’écran.

Un gestionnaire d’événements prêt à l’emploi et commenté est déjà en place pour le code intégré renvoyé par Experience Manager Assets.

Il suffit donc de supprimer les commentaires du code et de remplacer le corps factice du gestionnaire par le code spécifique à la page web.

La création de l’URL d’aperçu rapide est l’inverse de l’identification des variables de zone réactive et de zone cliquable décrite précédemment.

Voir [Identification des variables de zone réactive et de zone cliquable](#identifying-hotspot-and-image-map-variables).

La dernière étape permettant de déclencher l’URL d’aperçu rapide et d’activer le panneau d’aperçu rapide requiert très probablement l’aide d’un expert informatique. Ce type d’expert sait comment déclencher avec précision l’implémentation d’aperçus rapides à partir de l’étape appropriée, en disposant d’une URL d’aperçu rapide prête à l’emploi.

## Création d’une fenêtre contextuelle personnalisée Windows® à l’aide de l’aperçu rapide {#using-quickviews-to-create-custom-pop-ups}

Voir [Création d’une fenêtre contextuelle personnalisée Windows® à l’aide de l’aperçu rapide](/help/assets/dynamic-media/custom-pop-ups.md).
