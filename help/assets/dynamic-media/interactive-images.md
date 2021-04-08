---
title: Images interactives
description: Découvrir comment utiliser les images interactives dans Dynamic Media.
feature: Images interactives
topic: Professionnel
role: Business Practitioner
exl-id: 89eef5e6-d508-4f33-b54e-24d4df49f8c3
translation-type: tm+mt
source-git-commit: 6b232ab512a6faaf075faa55c238dfb10c00b100
workflow-type: tm+mt
source-wordcount: '4249'
ht-degree: 45%

---

# Images interactives {#interactive-images}

Vous pouvez facilement rendre les images statiques riches et attrayantes pour les clients en faisant glisser et en déplaçant des zones réactives &quot;susceptibles d’être visitées&quot; sur une image. Les points d&#39;accès disponibles dans les magasins combinent des informations supplémentaires sur un produit ou un service avec une fonctionnalité directe, au point de vente, &quot;Ajouter au panier&quot; ou &quot;Acheter&quot;. Les clients peuvent appuyer sur ces zones réactives qui pointent directement vers le produit ou le service, l’ajouter à un panier ou être liées à une page Web. Les expériences directes de ce type augmentent l’engagement et les conversions des clients sur votre site Web.

Vous trouverez ci-dessous une bannière modifiable avec une fenêtre contextuelle vue rapide. Un utilisateur active la vue rapide en appuyant sur le cercle ou la zone réactive sur le modèle.

![chlimage_1-152](assets/chlimage_1-368.png)

Voir [les images interactives en action](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion-QVzoom/index2-shoppable.html) sur la page web illustrée ci-dessus.

## Découvrir comment les bannières d’images interactives sont créées {#watch-how-interactive-image-banners-are-created}

Visionnez une présentation vidéo de 10 minutes et 33 secondes sur la [création de bannières d’images interactives](https://s7d5.scene7.com/s7viewers/html5/VideoViewer.html?videoserverurl=https://s7d5.scene7.com/is/content/&amp;emailurl=https://s7d5.scene7.com/s7/emailFriend&amp;serverUrl=https://s7d5.scene7.com/is/image/&amp;config=Scene7SharedAssets/Universal_HTML5_Video_social&amp;contenturl=https://s7d5.scene7.com/skins/&amp;asset=S7tutorials/InteractiveCarouselBanner). Vous apprendrez également à prévisualisation, modifier et diffuser des bannières d’images interactives.

## Démarrage rapide : images interactives {#quick-start-interactive-images}

La description suivante du workflow étape par étape est conçue pour vous aider à mettre en route rapidement les images interactives dans AEM Assets.

Recherchez le titre **Exemple** dans certaines tâches de démarrage rapide. Il contient un court tutoriel reposant sur [l’exemple de page web suivant qui ne contient pas encore d’images interactives](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-0.html).



Le tutoriel permet d’illustrer les étapes d’intégration d’images interactives à votre site web.

Étapes des images interactives :

1. **(Facultatif) Identification des variables de zone réactive**. Si vous utilisez Adobe Experience Manager Assets et Dynamic Media de manière autonome, identifiez les variables dynamiques utilisées dans votre mise en oeuvre de vue rapide existante. Cela vous permet de saisir des données de zone réactive lors de la création de l’image interactive. Voir [(Facultatif) Identification des variables de zone réactive](#optional-identifying-hotspot-variables).
Cependant, si vous utilisez AEM Sites ou AEM eCommerce, ou les deux, cette étape n’est pas nécessaire.

1. **(Facultatif) Création d’un paramètre prédéfini** de visionneuse d’images interactive. Personnalisez l’image graphique utilisée pour représenter les zones réactives. Vous n’avez pas besoin de créer votre propre paramètre prédéfini de visionneuse d’images interactives si vous envisagez plutôt d’utiliser le paramètre prédéfini de visionneuse d’images interactives prêt à l’emploi `Shoppable_Banner`.
Voir [(Facultatif) Création d’un paramètre prédéfini de visionneuse d’images interactives](/help/assets/dynamic-media/managing-viewer-presets.md#creating-a-new-viewer-preset).

1. **Téléchargement d’une bannière** d’image. Téléchargez des bannières d’image que vous souhaitez rendre interactives. Voir  [Téléchargement d’une bannière](#uploading-an-image-banner) d’image.

1. **Ajouter des zones réactives à une bannière** d’image. Ajoutez une ou plusieurs zones réactives sur une bannière d’image. Associez chacun à une action telle qu’un hyperlien, une vue rapide ou un fragment d’expérience. Après avoir ajouté des zones réactives, vous terminez cette tâche en publiant l’image interactive.
Voir [Ajout de zones réactives à une bannière d’image](#adding-hotspots-to-an-image-banner).
Voir [Prévisualisation d’images interactives](#optional-previewing-interactive-images) – Facultatif. Si vous le souhaitez, vous pouvez afficher une représentation de votre bannière Shoppable et tester son interactivité.
Voir [Publication de ressources](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md) pour obtenir des informations sur la publication de ressources d’images interactives.

1. **Ajouter une image interactive à votre site Web ou à votre site Web en Experience Manager**. Si vous utilisez Sites, eCommerce ou les deux, vous pouvez ajouter des images interactives directement à une page Web en Experience Manager. Faites glisser le composant Interactive Media sur la page. Reportez-vous à la section [Ajout de ressources Dynamic Media aux pages](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).
Si vous utilisez les ressources Experience Manager et Dynamic Media en mode autonome, copiez le code incorporé sur votre site Web. Ensuite, intégrez-la à votre vue rapide existante. Voir [Intégration d’une image interactive à votre site web](#integrating-an-interactive-image-with-your-website).
Si vous utilisez un gestionnaire de contenu Web tiers, intégrez la nouvelle vidéo interactive à la vue rapide existante utilisée sur votre site Web. Voir [Intégration d’une image interactive à une vue rapide ](#integrating-an-interactive-image-with-an-existing-quickview) existante.

## (Facultatif) Identification des variables de zone réactive {#optional-identifying-hotspot-variables}

>[!NOTE]
>
>Cette tâche n’est nécessaire que si les conditions ci-dessous sont vraies :
>
>* Vous souhaitez ajouter de l’interactivité à votre image en déclenchant des vues rapides.
>* Votre implémentation de Experience Manager n&#39;utilise *pas* une structure d&#39;intégration eCommerce pour extraire les données de produit dans le Experience Manager à partir de toute solution de commerce électronique. Ces solutions comprennent IBM WebSphere® Commerce, Elastic Path, hybris ou Intershop.

>
>
Si votre mise en œuvre d’AEM utilise l’e-commerce, vous pouvez ignorer cette tâche et passer à la tâche suivante.

Début en identifiant les variables dynamiques utilisées par votre implémentation de vue rapide existante afin que vous puissiez entrer des données de zone réactive pour créer l’image interactive.

Lorsque vous ajoutez des zones réactives à une image de bannière dans les ressources du Experience Manager, affectez un SKU (Stock Keeping Unit). Le SKU est un identifiant unique pour chaque produit ou service spécifique que vous avez offre. Ajoutez également des variables supplémentaires facultatives à chaque zone réactive. Ces variables de zone réactive sont utilisées ultérieurement pour faire correspondre les zones réactives au contenu de la vue rapide.

Il est important d’identifier correctement le nombre et le type de variables à associer aux données de zone réactive. Chaque zone réactive ajoutée à une image de bannière doit comporter suffisamment d’informations pour identifier clairement le produit sur le système principal existant.

Il existe différentes manières d’identifier un jeu de variables à utiliser pour les données des zones réactives.

Il suffit parfois de consulter les spécialistes informatiques chargés de la mise en oeuvre de la vue rapide existante. Ces personnes sont susceptibles de connaître l&#39;ensemble minimum de données nécessaires pour identifier la vue rapide dans le système. Cependant, il est également possible d&#39;analyser simplement le comportement existant du code frontal.

La plupart des implémentations de vue rapide utilisent le modèle suivant :

* L’utilisateur active un élément d’interface utilisateur sur le site Web. Par exemple, cliquez sur un bouton &quot;vue rapide&quot;.
* Le site Web envoie une requête Ajax au serveur principal pour charger les données ou le contenu de la vue rapide, si nécessaire.
* Les données de la vue rapide sont traduites dans le contenu en vue du rendu sur la page Web.
* Enfin, le code frontal effectue le rendu visuel de ce contenu à l’écran.

L’approche consiste ensuite à visiter différentes zones du site Web existant où la fonction vue rapide est mise en oeuvre. Ensuite, déclenchez la vue rapide et capturez l’URL Ajax envoyée par la page Web pour charger les données ou le contenu de la vue rapide.

Normalement, il n’est pas nécessaire d’utiliser des outils de débogage spécialisés. Les navigateurs web modernes incluent des inspecteurs web qui font un travail correct. Vous trouverez ci-dessous quelques exemples de navigateurs web qui incluent des inspecteurs web :

* Pour voir toutes les demandes HTTP sortantes dans Google Chrome, appuyez sur F12 pour ouvrir le panneau Outils de développement, puis cliquez sur l’onglet Réseau.
Sur Mac, appuyez sur Commande+Option+I pour ouvrir le panneau Outils de développement, puis cliquez sur l’onglet Réseau.

* Dans Firefox, vous pouvez activer le module externe Firebug en appuyant sur F12 et en utilisant son onglet Net. Vous pouvez également utiliser l’outil Inspecteur intégré et son onglet Réseau.
Sur Mac, appuyez sur Commande+Option+I pour ouvrir le panneau Outils de développement, puis cliquez sur l’onglet Inspecteur.

Lorsque la surveillance du réseau est activée dans le navigateur, déclenchez la vue rapide sur la page.

Recherchez maintenant l’URL Ajax de vue rapide dans le journal réseau et copiez l’URL enregistrée pour une analyse ultérieure. En général, lorsque vous déclenchez la vue rapide, de nombreuses requêtes sont envoyées au serveur. En règle générale, l’URL Ajax de la vue rapide est l’une des premières de la liste. Elle possède une partie de chaîne de requête complexe ou un chemin d’accès, et son type de réponse MIME est `text/html`, `text/xml` ou `text/javascript`.

Au cours de ce processus, il est important de visiter différentes zones de votre site Web, avec différentes catégories et différents types de produits. La raison en est que les URL de vue rapide peuvent comporter des parties communes pour une catégorie de site Web donnée. Cependant, elles ne changent que si vous visitez une autre zone du site Web.

Dans le cas le plus simple, la seule partie variable de l’URL de vue rapide est le SKU du produit. Dans ce cas, la valeur SKU est la seule donnée dont vous avez besoin pour ajouter des zones réactives à l’image de la bannière.

Toutefois, dans des cas complexes, l’URL de vue rapide comporte différents éléments variables en plus du SKU. Par exemple, des éléments variables peuvent inclure l’ID de catégorie, le code de couleur et le code de taille. Dans de tels cas, chaque élément est une variable distincte dans votre définition des données de zone réactive dans la fonction d’image interactive pouvant faire l’objet d’un achat dans les ressources du Experience Manager.

Examinez les exemples suivants d’URL de vue rapide et les variables de zone réactive qui en résultent :

<table>
  <tbody>
  <tr>
    <td><p>SKU unique, trouvé dans la chaîne de requête.</p> </td>
    <td><p>Les URL de vue rapide enregistrées sont les suivantes :</p>
    <ul>
      <li><p><code>https://server/json?productId=866558&amp;source=100</code></p> </li>
      <li><p><code>https://server/json?productId=1196184&amp;source=100</code></p> </li>
      <li><p><code>https://server/json?productId=1081492&amp;source=100</code></p> </li>
      <li><p><code>https://server/json?productId=1898294&amp;source=100</code></p> </li>
    </ul> <p>La seule partie variable de L’URL est la valeur du paramètre de chaîne de requête productId =, et il s’agit clairement d’une valeur de SKU. Par conséquent, les zones réactives n’ont besoin que de champs SKU renseignés avec des valeurs telles que <strong><code>866558</code></strong>, <strong><code>1196184</code></strong>, <strong><code>1081492</code></strong>, <strong><code>1898294</code></strong>.</p> </td>
  </tr>
  <tr>
    <td><p>SKU unique, trouvé dans le chemin d’accès à l’URL.</p> </td>
    <td><p>Les URL de vue rapide enregistrées sont les suivantes :</p>
    <ul>
      <li><p><code>https://server/product/6422350843</code></p> </li>
      <li><p><code>https://server/product/1607745002</code></p> </li>
      <li><p><code>https://server/product/0086724882</code></p> </li>
    </ul> <p>La partie variable se trouve dans la dernière partie du chemin et elle devient la valeur de SKU des zones réactives : <strong><code>6422350843</code></strong>, <strong><code>1607745002</code></strong> et <strong><code>0086724882</code></strong>.</p> </td>
  </tr>
  <tr>
    <td><p>SKU et ID de catégorie dans la chaîne de requête.</p> </td>
    <td><p>Les URL de vue rapide enregistrées sont les suivantes :</p>
    <ul>
      <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=305466</code></p> </li>
      <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=310181</code></p> </li>
      <li><p><code>https://server/quickView/product/?category=1740148&amp;prodId=308706</code></p> </li>
    </ul> <p>Dans ce cas, l’URL comporte deux parties différentes. Le SKU est stocké dans le paramètre <code>prodId</code> et l’ID de catégorie<code></code> dans le paramètre <code>category=</code>.</p> <p>Ainsi, les définitions des zones réactives sont des paires. Autrement dit, une valeur SKU et une variable supplémentaire appelée <code>categoryId</code>. Les paires obtenues sont les suivantes :</p>
    <ul>
      <li><p>Le SKU est <strong><code>305466</code></strong> et <code>categoryId</code> est <code>1100004</code>.</p> </li>
      <li><p>Le SKU est <strong><code>310181</code></strong> et <code>categoryId</code> est <strong><code>1100004</code></strong>.</p> </li>
      <li><p>Le SKU est <strong><code>308706</code></strong> et <code>categoryId</code> est <strong><code>1740148</code></strong>.</p> </li>
    </ul> <p> </p> </td>
  </tr>
  </tbody>
</table>

**Exemple**

Vous pouvez appliquer la même approche utilisée dans les trois exemples ci-dessus à la [page web de démonstration](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-0.html).

La page Web de démonstration comporte plusieurs miniatures de produit, chacune comportant un bouton de vue rapide intitulé &quot;En savoir plus&quot;. L’outil de débogage de votre navigateur Web étant toujours activé, cliquez sur chaque bouton et notez les URL de vue rapide enregistrées. Une fois que vous avez activé les quatre vues rapides de produits disponibles sur la page, vous disposez de la liste suivante de demandes de vue rapide envoyées au serveur principal :

* `/datafeed/Men-Windbreaker.json`
* `/datafeed/Men-SimpleHenley.json`
* `/datafeed/Men-CamoPullover.json`
* `/datafeed/Women-QuiltedDownJacket.json`

En examinant les appels au serveur, vous pouvez voir que les informations spécifiques au produit ne sont présentes que dans le chemin d’accès à la demande. Vous notez également que la chaîne de requête n’est pas du tout utilisée et que deux types de données distincts sont impliqués :

* Le premier type correspond au sexe, Homme ou Femme. Vous pouvez l’appeler « catégorie de produits ».
* Le second type est le nom du produit, tel que CamoPullover, qui est probablement le SKU du produit.

Compte tenu de ces informations, l’URL complète de la vue rapide a le modèle suivant :

`/datafeed/$categoryId$-$SKU$.json`

Sur la base de cette analyse, vous utiliseriez `categoryId` et `SKU` pour les zones réactives.

Vous êtes à présent prêt à charger une bannière d’image et à y ajouter des zones réactives à l’aide de la fonctionnalité d’images interactives Shoppable d’AEM Assets.

## (Facultatif) Création d’un paramètre prédéfini de visionneuse d’images interactives {#optional-creating-an-interactive-image-viewer-preset}

Vous pouvez choisir d’utiliser la valeur par défaut, le paramètre prédéfini de visionneuse d’images interactives, appelé « `Shoppable_Banner` », qui est fourni avec AEM Assets. Vous pouvez également créer votre propre paramètre prédéfini de visionneuse personnalisé à utiliser avec les images interactives.

Lorsque vous créez un paramètre prédéfini de visionneuse d’images interactives, vous pouvez déterminer l’aspect des zones réactives de la bannière d’image. Dans le cadre de la création du paramètre prédéfini de visionneuse, vous pouvez choisir d’utiliser une image de zone réactive provenant d’une galerie d’images prédéfinies.

Une fois que vous avez enregistré le paramètre prédéfini de visionneuse, il est activé automatiquement dans la page de liste Paramètre prédéfini de visionneuse dans AEM Assets. Cette fonctionnalité signifie qu’elle est visible dans le composant Interactive Media et chaque fois que vous affichez une ressource. Cependant, pour *diffuser* une bannière interactive avec ce paramètre prédéfini de visionneuse, *publier* également votre paramètre prédéfini de visionneuse. Cette règle s’applique aux paramètres prédéfinis de visionneuse personnalisés ou prêts à l’emploi.

**Pour créer un paramètre prédéfini de la visionneuse pour les images interactives**

1. Dans le rail de gauche, appuyez sur **[!UICONTROL Outils > Ressources > Paramètres visionneuse]**.
1. Dans le coin supérieur droit de la page, appuyez sur **[!UICONTROL Créer]**.
1. Dans la boîte de dialogue Nouveau paramètre prédéfini de la visionneuse, saisissez un nom pour décrire le paramètre prédéfini de visionneuse de bannières interactives.

   Ce titre s’affiche dans la page liste des paramètres prédéfinis de la visionneuse après l’enregistrement.

1. Dans le menu déroulant Type de média enrichi, sélectionnez **[!UICONTROL Image interactive]**.
1. Appuyez sur **[!UICONTROL Créer]**.
1. Sur la page Modifier le paramètre prédéfini de la visionneuse, appuyez sur l’onglet **[!UICONTROL Aspect]**.
1. Utilisez l’une des méthodes suivantes :

   * Pour télécharger votre propre image de zone réactive à utiliser sur les images, appuyez sur l’icône Sélecteur de ressources. Dans la page Sélectionner le contenu, accédez à l’image de zone réactive que vous souhaitez utiliser et sélectionnez-la. Appuyez sur l’icône représentant une coche dans le coin supérieur droit.
   * Pour sélectionner une image de zone réactive prédéfinie, appuyez sur l’icône Galerie de zones réactives. Dans la palette Galerie des zones réactives, appuyez sur l’image de zone réactive que vous souhaitez utiliser.

1. Dans le coin supérieur droit de la page, appuyez sur **[!UICONTROL Enregistrer]**.

   Assurez-vous de publier le nouveau paramètre prédéfini de la visionneuse.

   Voir [Publication de paramètres de visionneuse prédéfinis](/help/assets/dynamic-media/managing-viewer-presets.md#publishing-viewer-presets).

   Vous êtes désormais prêt à charger une bannière d’image.

## Chargement d’une bannière d’image  {#uploading-an-image-banner}

Si vous avez déjà chargé les images que vous souhaitez utiliser, passez à l’étape suivante [Ajout de zones réactives à une bannière d’image](#adding-hotspots-to-an-image-banner).

**Pour charger une bannière d’image**

1. Chargez les bannières d’images que vous souhaitez rendre interactives.

   Voir la section [Chargement des ressources](/help/assets/manage-digital-assets.md#uploading-assets).

   Vous êtes maintenant prêt à ajouter des zones réactives à la bannière d’image. Reportez-vous à la tâche suivante ci-dessous.

## Ajout de zones réactives à une bannière d’image  {#adding-hotspots-to-an-image-banner}

Vous pouvez ajouter des zones réactives à une bannière d’image à l’aide de l’éditeur dans la page Gestion des zones réactives.

Lorsque vous ajoutez des zones réactives, vous pouvez les définir comme une fenêtre contextuelle de vue rapide, comme un hyperlien ou un fragment d’expérience.

Voir [Fragments d’expérience](/help/sites-cloud/authoring/fundamentals/experience-fragments.md).

>[!NOTE]
>
>Les outils de partage de médias sociaux dans l’image interactive ne sont pas pris en charge lorsque vous incorporez la visionneuse dans un fragment d’expérience. Utilisez ou créez plutôt des paramètres prédéfinis de visionneuse qui ne comportent pas d’outils de partage sur les réseaux sociaux. Ces paramètres prédéfinis de visionneuse vous permettent de l’incorporer dans des fragments d’expérience.

Les options Annuler et Rétablir, proches du coin supérieur droit de la page, sont prises en charge au cours de la session de création/modification actuelle.

Lorsque vous avez terminé de créer votre image interactive, vous pouvez utiliser la Prévisualisation pour voir comment votre image interactive s’affiche pour les clients.

Reportez-vous à la section [(Facultatif) Aperçu des images interactives](#optional-previewing-interactive-images).

>[!NOTE]
>
>Lorsque vous ajoutez des zones réactives à une image dans une image interactive ou une bannière de carrousel, les informations de ces zones sont stockées au même emplacement de métadonnées. Cet emplacement dépend de l’emplacement de l’image, qu’il s’agisse d’une image interactive ou d’une bannière de carrousel. Cela signifie que vous pouvez facilement réutiliser la même image (ainsi que ses données de zone réactive définies) dans l’une ou l’autre visionneuse.
Notez cependant que les bannières de carrousel prennent en charge les images à zones cliquables, qui peuvent également contenir des zones réactives. Les images interactives n’en comportent pas. Gardez cette idée à l’esprit si vous avez l’intention de créer une image interactive ou une bannière de carrousel qui utilise la même image. Vous pouvez créer des images interactives et des bannières de carrousel à l’aide de copies distinctes de la même image.
Voir aussi [Bannières de carrousel](/help/assets/dynamic-media/carousel-banners.md).

>[!NOTE]
Si vous modifiez des images interactives avec des zones réactives et que vous recadrez l’image, les zones réactives sont supprimées.

**Pour ajouter des zones réactives à une bannière d’image**

1. En mode Ressources, accédez à la bannière d’image à laquelle vous souhaitez ajouter de l’interactivité.
1. Utilisez l’une des méthodes suivantes :

   * Pointez sur l’image, puis appuyez sur la touche **[!UICONTROL Sélectionner]** (icône de coche). Dans la barre d’outils, appuyez sur **[!UICONTROL Modifier]**.

   * Pointez sur l’image, puis appuyez sur **[!UICONTROL Autres actions]** (icône représentant des points de suspension) > **[!UICONTROL Modifier]**.

   * Pour l’ouvrir dans la page Vue des détails, appuyez sur l’image. Dans la barre d’outils, appuyez sur **[!UICONTROL Modifier]**.

1. Près du coin supérieur gauche de la page, appuyez sur **[!UICONTROL Ajouter une zone réactive]** (icône d’appui à l’aide du doigt) pour ouvrir la page de gestion des zones réactives.
1. Dans le coin supérieur gauche de la page, appuyez sur **[!UICONTROL Zone réactive]**.

   1. Dans le coin supérieur gauche de la page de gestion des zones réactives, appuyez sur **[!UICONTROL Zone réactive]**.
   1. Sur l’image, appuyez sur un emplacement où vous souhaitez que la zone réactive s’affiche. Si nécessaire, faites glisser la zone réactive pour en ajuster l’emplacement. Vous pouvez également utiliser les touches fléchées du clavier pour contrôler la position d’une zone réactive sélectionnée.
   1. Ajoutez davantage de zones réactives si nécessaire en répétant les étapes a et b.
   1. (Facultatif) Pour supprimer une zone réactive, sélectionnez-la sur l’image, puis appuyez sur **[!UICONTROL Supprimer]** (icône de corbeille) sous l’en-tête **[!UICONTROL Zones réactives]**.

1. Dans le champ de texte Nom, entrez le nom de la zone réactive. Ce nom s’affiche également dans la liste déroulante Zone réactive sélectionnée.
1. Utilisez l’une des méthodes suivantes :

   * Appuyez sur **[!UICONTROL vue rapide]**.

      * Si vous êtes client AEM Sites ou AEM eCommerce, appuyez ou cliquez sur l’icône de sélecteur de produit (loupe) afin d’afficher la page Sélectionner un produit. Appuyez sur le produit à utiliser, puis appuyez sur **Sélectionner** dans le coin supérieur droit de la page. Vous revenez à la page de gestion des zones réactives.
      * Si vous n&#39;êtes *pas* un client Sites ou Commerce Experience Manager

         * Voir [Identification des variables de zone réactive](#optional-identifying-hotspot-variables); vous devez définir ces variables.
         * Ensuite, entrez manuellement la valeur de SKU. Dans le champ Valeur du SKU, saisissez le SKU du produit. La valeur SKU saisie renseigne automatiquement la partie variable du modèle de vue rapide. Il s’assure que le système sait associer la zone réactive avec la vue rapide d’un SKU particulier.
         * (Facultatif) Si d’autres variables de la vue rapide sont utilisées pour identifier un produit, appuyez sur **[!UICONTROL Ajouter la variable générique]**. Dans le champ de texte, spécifiez une variable supplémentaire. Par exemple, `category=Mens` est une variable ajoutée.
   * Appuyez sur **[!UICONTROL Lien hypertexte]**.

      * Si vous êtes un client Sites Experience Manager, appuyez sur l&#39;icône Sélecteur de site (dossier). Accédez à une URL. La méthode de liaison basée sur des URL n’est pas possible si votre contenu interactif comporte des liens avec des URL relatives, en particulier des liens vers des pages de sites Experience Manager.
      * Si vous êtes un client autonome, dans le champ de texte HREF, spécifiez l’URL complète vers une page web liée.

   Veillez à spécifier si vous souhaitez ouvrir le lien dans un nouvel onglet du navigateur (paramètre par défaut recommandé) ou dans le même onglet.

   Pour plus d’informations, voir [Utilisation de sélecteurs](/help/assets/dynamic-media/working-with-selectors.md).

   * Appuyez sur **[!UICONTROL Fragment d’expérience]**.

      * Si vous êtes client AEM Sites, appuyez ou cliquez sur l’icône Rechercher (loupe) afin d’ouvrir la page Fragment d’expérience. Appuyez sur le fragment d’expérience que vous souhaitez utiliser. Appuyez ensuite sur **[!UICONTROL Sélectionner]** dans le coin supérieur droit de la page. Vous revenez à la page de gestion des zones réactives.
Voir [Fragments d’expérience](/help/sites-cloud/authoring/fundamentals/experience-fragments.md).

      * Indiquez la largeur et la hauteur du fragment d’expérience tel qu’il doit apparaître sur la bannière.

         >[!NOTE]
         Les outils de partage de médias sociaux dans l’image interactive ne sont pas pris en charge lorsque vous incorporez la visionneuse dans un fragment d’expérience. Utilisez ou créez plutôt des paramètres prédéfinis de visionneuse qui ne comportent pas d’outils de partage sur les réseaux sociaux. Ces paramètres prédéfinis de visionneuse vous permettent de l’incorporer dans des fragments d’expérience.



1. Appuyez sur **[!UICONTROL Enregistrer]** pour enregistrer vos modifications et revenir à la page du navigateur.
1. Publiez l’image interactive. La publication fournit la bannière via le cloud et génère également du code incorporé qui vous permet de l’intégrer à un site Web tiers.

   Voir [Publication de ressources](/help/assets/manage-digital-assets.md#publish-assets).

   Une fois que vous avez ajouté des zones réactives et publié l’image interactive, vous êtes prêt à l’ajouter à votre site web.

   Voir [Intégration d’une image interactive à votre site web](#integrating-an-interactive-image-with-your-website).

   >[!NOTE]
   Si vous modifiez des images interactives avec des zones réactives et que vous recadrez l’image, les zones réactives sont supprimées.

### (Facultatif) Aperçu des images interactives  {#optional-previewing-interactive-images}

Vous pouvez utiliser la Prévisualisation pour afficher une représentation de l’aspect de votre image interactive pour les clients. Prévisualisation vous permet également de tester les zones réactives de l’image afin de vous assurer qu’elles se comportent comme prévu.

Lorsque vous êtes satisfait de l’image interactive, vous pouvez la publier.
Voir [Incorporation de la visionneuse de vidéos ou d’images dans une page web](/help/assets/dynamic-media/embed-code.md).
Voir [Liaison d’URL à une application web](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md). La méthode de liaison basée sur une URL n’est pas possible si votre contenu interactif contient des liens avec des URL relatives, en particulier des liens vers des pages AEM Sites.
Reportez-vous à la section [Ajout de ressources Dynamic Media aux pages](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).

**Pour prévisualiser des images interactives**

1. En mode Ressources, accédez à une image interactive existante que vous avez créée et appuyez pour la prévisualiser.
1. Près du coin supérieur gauche de la page de prévisualisation, dans la liste déroulante Contenu, appuyez sur **[!UICONTROL Visionneuses]**.
1. Dans la liste Visionneuse, appuyez sur **[!UICONTROL Shoppable_Banner]** ou sur le nom du paramètre prédéfini de visionneuse d’images interactives que vous avez créé.
1. Pour tester les actions associées des zones réactives, appuyez sur ces zones réactives dans l’image.

## Publication des ressources d’images interactives {#publishing-interactive-image-assets}

Voir [Publication de ressources](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md) pour obtenir des informations sur la publication de ressources d’images interactives.

## Intégration d’une image interactive à votre site web {#integrating-an-interactive-image-with-your-website}

Une fois que vous avez téléchargé une image de bannière, ajouté des zones réactives et publié l’image interactive, vous êtes prêt à l’ajouter à votre page de site Web.

Si vous êtes client AEM Sites, vous pouvez ajouter l’image interactive en faisant glisser le composant Interactive Media dans votre page. Reportez-vous à la section [Ajout de ressources Dynamic Media aux pages](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).

Si vous êtes client AEM Assets autonome, vous pouvez ajouter manuellement l’image interactive à votre site web, comme indiqué dans cette section.

1. Copiez le code intégré de l’image interactive publiée.
Voir [Incorporation de la visionneuse de vidéos ou d’images dans une page web](/help/assets/dynamic-media/embed-code.md).

1. Ajoutez le code intégré copié à l’emplacement souhaité dans la page web.
Le code incorporé copié est défini pour un environnement réactif afin qu’il s’adapte automatiquement à la zone affectée.

**Exemple**

En utilisant le [site Web de démonstration comme exemple](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-0.html), notez que l&#39;image des trois individus est une balise statique `IMG` :

```xml
<img class="img-responsive" width="100%" title="Hero Image 2" alt="Hero Image 2" src="images/shoppable-banner.jpg">
```

L’intégration revient simplement à supprimer la balise `IMG` et à la remplacer par le code intégré copié à partir d’AEM Assets. Vous pouvez voir que le résultat [affiche l’image interactive pouvant être consultée sur la page avec trois zones réactives de cercle ](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-1.html).

>[!NOTE]
A ce stade, les zones réactives de l&#39;image interactive du site web de démonstration sont uniquement destinées à l&#39;affichage. Ils ne sont pas encore intégrés aux vues rapides existantes.

Pour appliquer un &quot;recadrage&quot; à une image interactive pouvant faire l’objet d’un achat pour un environnement réactif, ajoutez l’attribut de configuration Image interactive `ZoomView.iscommand` au chemin d’accès. Dans ce cas, le composant `ZoomView` est appelé et `iscommand` est la commande de diffusion d&#39;image de recadrage que vous appliquez.

Voir l’attribut de configuration [ZoomView.iscommand](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/command-reference-configuration-attributes-interactive-images/r-html5-aem-interactive-image-config-attrib-zoomview-iscommand.html?lang=fr).

Voir la commande de service d’images [crop](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-crop.html?lang=fr).

Vous êtes maintenant prêt à intégrer l’image interactive à une vue rapide existante sur votre site Web.

## Intégration d’une image interactive à une vue rapide {#integrating-an-interactive-image-with-an-existing-quickview} existante

>[!NOTE]
Cette tâche ne s’applique que si vous êtes un client AEM Assets autonome.

La dernière étape de ce processus consiste à intégrer l’image interactive à une mise en oeuvre de vue rapide existante sur votre site Web. Pour ce qui est de l’intégration, il n’existe pas de solution qui fonctionne dans tous les cas. Chaque mise en oeuvre de vue rapide est unique et une approche spécifique est nécessaire. Il est donc utile de faire appel à l&#39;assistance d&#39;un informaticien principal.

L’implémentation de la vue rapide existante représente normalement une chaîne d’actions interdépendantes qui se produisent sur la page Web dans l’ordre suivant :

1. Un utilisateur déclenche un élément dans l’interface utilisateur de votre site web.
1. Le code principal obtient une URL de vue rapide en fonction de l’élément d’interface utilisateur qui a été déclenché à l’étape 1.
1. Le code frontal envoie une demande Ajax en utilisant l’URL obtenue à l’étape 2.
1. La logique d’arrière-plan renvoie les données ou le contenu de vue rapide correspondants au code d’avant-plan.
1. Le code principal charge les données ou le contenu de la vue rapide.
1. Le code principal peut éventuellement convertir les données de vue rapide chargées en une représentation HTML.
1. Le code en front-end affiche une boîte de dialogue ou un panneau modal et effectue le rendu du contenu HTML à l’écran pour l’utilisateur final.

Ces appels ne représentent pas nécessairement des appels d’API publics indépendants qui sont appelés par la logique de page Web à partir d’une étape arbitraire. Il s’agit plutôt d’un appel chaîné où chaque étape suivante est masquée dans la dernière phase (rappel) de l’étape précédente.

Lorsque l’image interactive pouvant faire l’objet d’un achat remplace l’étape 1 et l’étape 2 partielle, l’utilisateur touche une zone réactive à l’intérieur de l’image pouvant faire l’objet d’un achat. Cette interaction utilisateur est gérée par le lecteur de contenu. Le lecteur renvoie un événement à la page Web qui contient toutes les données de zone réactive précédemment ajoutées à AEM Assets.

Dans ce type de gestionnaire d’événements, le code frontal effectue les opérations suivantes :

* Il écoute un événement émis par l’image interactive Shoppable.
* Construit une URL de vue rapide en fonction des données de zone réactive.
* Déclenche le processus de chargement de la vue rapide à partir de l’arrière-plan et de son rendu à l’écran pour affichage.

Le code incorporé renvoyé par Experience Manager Assets dispose d’un gestionnaire de événement prêt à l’emploi qui est commenté, comme le montre le fragment de code mis en surbrillance suivant :

```xml
        var s7interactiveimageviewer = new s7viewers.InteractiveImage({
            "containerId" : "s7interactiveimage_div",
            "params" : {
                "serverurl" : "https://aodmarketingna.assetsadobe.com/is/image",
                "contenturl" : "https://aodmarketingna.assetsadobe.com/",
                "config" : "/etc/dam/presets/viewer/Shoppable_Media",
                "asset" : "/content/dam/mac/aodmarketingna/shoppable-banner/shoppable-banner.jpg" }
        })
        /* // Example of interactive image event for Quickview.
             s7interactiveimageviewer.setHandlers({
                "quickViewActivate": function(inData) {
                    var sku=inData.sku; //SKU for product ID
                    //To pass other parameter from the hotspot, you will need to add custom parameter during the hotspot setup as parameterName=value
                    loadQuickView(sku); //Replace this call with your Quickview plugin
                    //Please refer to your Quickviewer plugin for the Quickview call
                 },
             });
        */
        s7interactiveimageviewer.init();
```

Il suffit donc de supprimer les commentaires du code et remplacer le corps factice du gestionnaire par le code spécifique à la page web.

Le processus de création de l’URL de vue rapide est l’opposé du processus utilisé pour identifier les variables de zone réactive couvertes précédemment.

Voir [Identification des variables des zones réactives](#optional-identifying-hotspot-variables).

Les exemples précédents d’URL de vue rapide vous permettent de voir dans les exemples suivants comment l’URL de vue rapide est construite dans chaque cas :

<table>
 <tbody>
  <tr>
   <td><p>SKU unique, trouvé dans la chaîne de requête</p> </td>
   <td><code class="code">s7interactiveimageviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/json?productId=" + inData.sku + "&amp;amp;source=100";
      },
      });</code></td>
  </tr>
  <tr>
   <td><p>SKU unique, trouvé dans le chemin d’accès à l’URL</p> </td>
   <td><code class="code">s7interactiveimageviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/product/" + inData.sku;
      },
      });</code></td>
  </tr>
  <tr>
   <td><p>SKU et ID de catégorie dans la chaîne de requête</p> </td>
   <td><code class="code">s7interactiveimageviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/quickView/product/?category=" + inData.categoryId + "&amp;amp;prodId=" + inData.sku;
      },
      });</code></td>
  </tr>
 </tbody>
</table>

La dernière étape pour déclencher l’URL de vue rapide et activer le panneau vue rapide requiert l’assistance d’un informaticien principal de votre entreprise. Ils disposent des connaissances nécessaires pour savoir comment déclencher avec précision l’implémentation de la vue rapide à partir de l’étape appropriée, en disposant d’une URL de vue rapide prête à l’emploi.

Vous pouvez voir comment ces étapes sont appliquées au site Web de démonstration afin d’intégrer pleinement une image interactive pouvant faire l’objet d’un achat au code de vue rapide. Auparavant, la structure de l’URL de vue rapide était identifiée comme suit :

```xml
/datafeed/$categoryId$-$SKU$.json
```

Pour reconstruire cette URL dans le gestionnaire `quickViewActivate`, vous pouvez utiliser les champs `categoryId` et `SKU`. Ces champs sont disponibles dans l’objet `inData` transmis au gestionnaire par le code du lecteur :

```xml
var sku=inData.sku;
var categoryId=inData.categoryId;
var quickViewUrl = "datafeed/" + categoryId + "-" + sku + ".json";
```

Le site Web de démonstration déclenche la boîte de dialogue vue rapide en utilisant un simple appel de fonction `loadQuickView()`. Cette fonction ne prend qu’un seul argument, à savoir l’URL des données de vue rapide. Ainsi, la dernière étape pour intégrer l&#39;image interactive stockée consiste à ajouter la ligne de code suivante au gestionnaire `quickViewActivate` :

```xml
loadQuickView(quickViewUrl);
```

Voici le code source complet :

```xml
 var s7interactiveimageviewer = new s7viewers.InteractiveImage({
  "containerId" : "s7interactiveimage_div",
  "params" : {
   "serverurl" : "https://aodmarketingna.assetsadobe.com/is/image",
   "contenturl" : "https://aodmarketingna.assetsadobe.com/",
   "config" : "/etc/dam/presets/viewer/Shoppable_Media",
   "asset" : "/content/dam/mac/aodmarketingna/shoppable-banner/shoppable-banner.jpg" }
 })
   s7interactiveimageviewer.setHandlers({
   "quickViewActivate": function(inData) {
     var sku=inData.sku;
     var categoryId=inData.categoryId;
    var quickViewUrl = "datafeed/" + categoryId + "-" + sku + ".json";
    loadQuickView(quickViewUrl);
    },
   });
 s7interactiveimageviewer.init();
```

Le [site web de démonstration final avec l’image interactive entièrement intégrée](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-3.html).

## Utilisation de vues rapides pour créer des fenêtres contextuelles personnalisées {#using-quickviews-to-create-custom-pop-ups}

Voir [Utilisation de vues rapides pour créer des fenêtres contextuelles personnalisées](/help/assets/dynamic-media/custom-pop-ups.md).
