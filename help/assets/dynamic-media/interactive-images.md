---
title: Images interactives
description: Découvrir comment utiliser les images interactives dans Dynamic Media.
contentOwner: Rick Brough
feature: Interactive Images
role: User
exl-id: 89eef5e6-d508-4f33-b54e-24d4df49f8c3
source-git-commit: c82f84fe99d8a196adebe504fef78ed8f0b747a9
workflow-type: tm+mt
source-wordcount: '4118'
ht-degree: 95%

---

# Images interactives{#interactive-images}

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

Vous pouvez facilement créer des expériences riches et attrayantes pour vos clients à partir d’images statiques en ajoutant des zones réactives « shoppable » aux images par glisser-déposer. Les zones réactives Shoppable rassemblent des informations supplémentaires sur un produit ou un service avec une fonctionnalité directe de point de vente de type « Ajouter au panier » ou « Acheter ». Les clients peuvent sélectionner ces zones réactives qui pointent directement vers le produit ou le service, l’ajoutent à un panier ou pointent vers une page web. Les expériences directes de ce type augmentent l’engagement et les conversions des clients sur votre site web.

Voici une bannière publicitaire avec une fenêtre pop-up d’aperçu rapide. L’utilisateur active l’aperçu rapide en appuyant sur le cercle ou la « zone réactive » du modèle.

![chlimage_1-152](assets/chlimage_1-368.png)

Voir [les images interactives en action](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion-QVzoom/index2-shoppable.html?lang=fr) sur la page web illustrée ci-dessus.

## Découvrir comment les bannières d’images interactives sont créées {#watch-how-interactive-image-banners-are-created}

Regardez une présentation détaillée concernant [les méthodes de création de bannières d’images interactives](https://s7d5.scene7.com/s7viewers/html5/VideoViewer.html?videoserverurl=https://s7d5.scene7.com/is/content/&amp;emailurl=https://s7d5.scene7.com/s7/emailFriend&amp;serverUrl=https://s7d5.scene7.com/is/image/&amp;config=Scene7SharedAssets/Universal_HTML5_Video_social&amp;contenturl=https://s7d5.scene7.com/skins/&amp;asset=S7tutorials/InteractiveCarouselBanner) (10 minutes et 33 secondes). Apprenez également à prévisualiser, modifier et diffuser des bannières d’images interactives.

## Démarrage rapide : images interactives {#quick-start-interactive-images}

La description suivante du workflow étape par étape est conçue pour vous aider à mettre en route rapidement les images interactives dans Adobe Experience Manager Assets.

Recherchez le titre **Exemple** dans certaines tâches de démarrage rapide. Il contient un court tutoriel reposant sur [l’exemple de page web suivant qui ne contient pas encore d’images interactives](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html?lang=fr).



Le tutoriel permet d’illustrer les étapes d’intégration de vidéos interactives à votre site web.

Étapes des images interactives :

1. **(Facultatif) Identification des variables de zone réactive**. Si vous utilisez Adobe Experience Manager Assets et Dynamic Media de manière autonome, identifiez les variables dynamiques utilisées dans votre mise en œuvre d’aperçu rapide existante. Cela vous permet de saisir des données de zone réactive lors de la création de l’image interactive. Voir [(Facultatif) Identification des variables de zone réactive](#optional-identifying-hotspot-variables).
Cependant, si vous utilisez Experience Manager Sites ou Experience Manager eCommerce, ou les deux, cette étape n’est pas nécessaire.

1. **(Facultatif) Création d’un paramètre prédéfini de visionneuse d’images interactives**. Personnalisez l’image utilisée pour représenter les zones réactives. Vous n’avez pas besoin de créer votre propre paramètre prédéfini de visionneuse d’images interactives si vous envisagez plutôt d’utiliser le paramètre prédéfini de visionneuse d’images interactives prêt à l’emploi `Shoppable_Banner`.
Voir [(Facultatif) Création d’un paramètre prédéfini de visionneuse d’images interactives](/help/assets/dynamic-media/managing-viewer-presets.md#creating-a-new-viewer-preset).

1. **Chargez une bannière d’image**. Chargez les bannières d’images que vous souhaitez rendre interactives.
Voir [Chargement d’une bannière d’image](#uploading-an-image-banner).

1. **Ajout de zones réactives à une bannière d’image**. Ajoutez une ou plusieurs zones réactives sur une bannière d’image. Associez chacune de ces zones à une action telle qu’un lien hypertexte, un aperçu rapide ou un fragment d’expérience. Après avoir ajouté des zones réactives, vous terminez cette tâche en publiant l’image interactive.
Voir [Ajout de zones réactives à une bannière d’image](#adding-hotspots-to-an-image-banner).
Voir [Prévisualisation d’images interactives](#optional-previewing-interactive-images) – Facultatif. Si vous le souhaitez, vous pouvez afficher une représentation de votre bannière Shoppable et tester son interactivité.
Voir [Publication de ressources](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md) pour obtenir des informations sur la publication de ressources d’images interactives.

1. **Ajout d’une image interactive à votre site web ou à votre site web dans Experience Manager**. Si vous utilisez Sites, eCommerce ou les deux, vous pouvez ajouter des images interactives directement à une page web dans Experience Manager. Faites glisser le composant Interactive Media sur la page. Reportez-vous à [Ajout de ressources Dynamic Media aux pages](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).
Si vous utilisez Experience Manager Assets et Dynamic Media en mode autonome, copiez le code incorporé sur votre site web. Ensuite, intégrez-le à votre aperçu rapide existant. Voir [Intégration d’une image interactive à votre site web](#integrating-an-interactive-image-with-your-website).
Si vous utilisez un gestionnaire de contenu web tiers, intégrez la nouvelle vidéo interactive à l’aperçu rapide existant utilisé sur votre site web. Reportez-vous à la section [Intégration d’une image interactive dans un aperçu rapide existant](#integrating-an-interactive-image-with-an-existing-quickview).

## (Facultatif) Identification des variables de zone réactive {#optional-identifying-hotspot-variables}

>[!NOTE]
>
>Cette tâche n’est nécessaire que si les conditions ci-dessous sont vraies :
>
>* Vous souhaitez ajouter de l’interactivité à votre image en déclenchant des aperçus rapides.
>* Votre implémentation d’Experience Manager n’utilise *pas* de structure d’intégration eCommerce pour extraire les données de produit dans Experience Manager à partir de toute solution d’e-commerce. De telles solutions peuvent inclure IBM WebSphere® Commerce, Elastic Path, SAP Hybris ou Intershop.
>
>Si votre mise en œuvre d’Experience Manager utilise l’e-commerce, vous pouvez ignorer cette tâche et passer à la tâche suivante.

Commencez par identifier les variables dynamiques utilisées par votre mise en œuvre de l’aperçu rapide existant afin de pouvoir entrer les données de zone réactive pour créer l’image interactive.

Lorsque vous ajoutez des zones réactives à une image de bannière dans Experience Manager Assets, affectez-leur un SKU (Stock Keeping Unit). Le SKU est un identifiant unique associé à chaque produit ou service spécifique que vous proposez. Ajoutez également des variables supplémentaires facultatives à chaque zone réactive. Ces variables de zones réactives sont utilisées ultérieurement pour faire correspondre ces zones réactives avec du contenu d’aperçu rapide.

Il est important d’identifier correctement le nombre et le type de variables à associer aux données de zone réactive. Chaque zone réactive ajoutée à une image de bannière doit comporter suffisamment d’informations pour identifier clairement le produit sur le système principal existant.

Il existe différentes manières d’identifier un jeu de variables à utiliser pour les données des zones réactives.

Il suffit parfois de consulter les spécialistes informatiques chargés de la mise en œuvre de l’aperçu rapide existant. Ces personnes sont susceptibles de connaître les données minimum nécessaires pour identifier l’aperçu rapide dans le système. Cependant, il est également possible d’analyser le comportement existant du code en front-end.

La plupart des implémentations d’aperçu rapide utilisent le modèle suivant :

* L’utilisateur active un élément d’interface utilisateur sur le site web. Par exemple, en sélectionnant un bouton « Aperçu rapide ».
* Le site Web envoie une requête Ajax au serveur principal afin de charger les données ou le contenu de l’aperçu rapide, le cas échéant.
* Les données de l’aperçu rapide sont traduites en contenu en préparation du rendu sur la page Web.
* Enfin, le code en front-end effectue le rendu visuel de ce contenu à l’écran.

L’approche consiste ensuite à visiter différentes zones du site web existant dans lequel la fonction Aperçu rapide est implémentée. Ensuite, déclenchez l’aperçu rapide et capturez l’URL Ajax envoyée par la page web pour charger les données ou le contenu de l’aperçu rapide.

Normalement, il n’est pas nécessaire d’utiliser des outils de débogage spécialisés. Les navigateurs web modernes incluent des inspecteurs web qui font un travail correct. Vous trouverez ci-dessous quelques exemples de navigateurs web qui incluent des inspecteurs web :

* Pour voir toutes les demandes HTTP sortantes dans Google Chrome, appuyez sur F12 pour ouvrir le panneau Outils de développement, puis sélectionnez l’onglet Réseau.
Sur Mac, appuyez sur Commande+Option+I pour ouvrir le panneau Outils de développement, puis sélectionnez l’onglet Réseau.

* Dans Firefox, vous pouvez activer le plug-in Firebug en appuyant sur F12 et en utilisant son onglet Net. Vous pouvez également utiliser l’outil Inspecteur intégré et son onglet Réseau.
Sur Mac, appuyez sur Commande+Option+I pour ouvrir le panneau Outils de développement, puis sélectionnez l’onglet Inspecteur.

Lorsque la surveillance de réseau est activée dans le navigateur, déclenchez l’aperçu rapide sur la page.

Vous trouvez maintenant l’URL Ajax d’aperçu rapide dans le journal réseau. Copiez l’URL enregistrée pour l’analyse ultérieure. Généralement, lorsque vous déclenchez l’aperçu rapide, plusieurs requêtes sont envoyées au serveur. En règle générale, l’URL Ajax d’aperçu rapide est l’une des premières dans la liste. Elle possède une partie de chaîne de requête complexe ou un chemin d’accès, et son type de réponse MIME est `text/html`, `text/xml` ou `text/javascript`.

Au cours de ce processus, il est important de parcourir différentes zones de votre site web, avec différentes catégories et types de produits. En effet, les URL d’aperçu rapide peuvent comporter des parties communes pour une catégorie donnée du site web. Cependant, elles ne changent que si vous visitez une autre zone du site web.

Dans le cas le plus simple, la seule partie variable dans l’URL de l’aperçu rapide est le SKU du produit. Dans ce cas, la valeur du code SKU est la seule donnée dont vous avez besoin pour ajouter des zones réactives ou des zones cliquables à l’image de bannière.

Toutefois, dans des cas complexes, l’URL d’aperçu rapide comporte différents éléments variables en plus du SKU. Par exemple, les éléments variables peuvent inclure l’ID de catégorie, le code couleur et le code de taille. Dans ce cas, chaque élément est une variable distincte dans votre définition de données d’images interactives dans la fonctionnalité d’image interactive publicitaire d’Experience Manager Assets.

Consultez les exemples d’URL d’aperçu rapide et les variables de zone réactive qui en résultent ci-dessous :

<table>
  <tbody>
  <tr>
    <td><p>SKU unique, trouvé dans la chaîne de requête.</p> </td>
    <td><p>Les URL d’aperçu rapide enregistrées incluent ce qui suit :</p>
    <ul>
      <li><p><code>https://server/json?productId=866558&amp;source=100</code></p> </li>
      <li><p><code>https://server/json?productId=1196184&amp;source=100</code></p> </li>
      <li><p><code>https://server/json?productId=1081492&amp;source=100</code></p> </li>
      <li><p><code>https://server/json?productId=1898294&amp;source=100</code></p> </li>
    </ul> <p>La seule partie variable de l’URL est la valeur du paramètre de chaîne de requête productId =, et il s’agit clairement d’une valeur de SKU. Par conséquent, seuls les champs SKU des zones réactives doivent être renseignés avec des valeurs comme <strong><code>866558</code></strong>, <strong><code>1196184</code></strong>, <strong><code>1081492</code></strong> et <strong><code>1898294</code></strong>.</p> </td>
  </tr>
  <tr>
    <td><p>SKU unique, trouvé dans le chemin d’accès à l’URL.</p> </td>
    <td><p>Les URL d’aperçu rapide enregistrées incluent ce qui suit :</p>
    <ul>
      <li><p><code>https://server/product/6422350843</code></p> </li>
      <li><p><code>https://server/product/1607745002</code></p> </li>
      <li><p><code>https://server/product/0086724882</code></p> </li>
    </ul> <p>La partie variable se trouve dans la dernière partie du chemin et elle devient la valeur de SKU des zones réactives : <strong><code>6422350843</code></strong>, <strong><code>1607745002</code></strong> et <strong><code>0086724882</code></strong>.</p> </td>
  </tr>
  <tr>
    <td><p>SKU et ID de catégorie dans la chaîne de requête.</p> </td>
    <td><p>Les URL d’aperçu rapide enregistrées incluent ce qui suit :</p>
    <ul>
      <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=305466</code></p> </li>
      <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=310181</code></p> </li>
      <li><p><code>https://server/quickView/product/?category=1740148&amp;prodId=308706</code></p> </li>
    </ul> <p>Dans ce cas, l’URL comporte deux parties différentes. Le SKU est stocké dans le paramètre <code>prodId</code> et l’ID de catégorie<code></code> dans le paramètre <code>category=</code>.</p> <p>Les zones réactives sont définies sous forme de paires. Autrement dit, une valeur de SKU et une variable supplémentaire appelée « <code>categoryId</code> ». Les paires obtenues sont les suivantes :</p>
    <ul>
      <li><p>Le SKU est <strong><code>305466</code></strong> et <code>categoryId</code> est <code>1100004</code>.</p> </li>
      <li><p>Le SKU est <strong><code>310181</code></strong> et <code>categoryId</code> est <strong><code>1100004</code></strong>.</p> </li>
      <li><p>Le SKU est <strong><code>308706</code></strong> et <code>categoryId</code> est <strong><code>1740148</code></strong>.</p> </li>
    </ul> <p> </p> </td>
  </tr>
  </tbody>
</table>

**Exemple**

Vous pouvez appliquer la même approche utilisée dans les trois exemples ci-dessus à la [page web de démonstration](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html?lang=fr).

La page web de démonstration présente plusieurs vignettes de produit, chacune d’entre elles disposant d’un bouton d’aperçu rapide libellé « Plus ». À l’aide de l’outil de débogage de votre navigateur web toujours activé, sélectionnez chaque bouton et notez les URL d’aperçu rapide enregistrées. Une fois que vous avez activé l’aperçu rapide des quatre produits disponibles sur la page, vous obtenez la liste suivante de demandes d’aperçu rapide exécutées en arrière-plan :

* `/datafeed/Male-Windbreaker.json`
* `/datafeed/Male-SimpleHenley.json`
* `/datafeed/Male-CamoPullover.json`
* `/datafeed/Female-QuiltedDownJacket.json`

Lorsque vous observez ces appels de serveur, vous pouvez constater que les informations spécifiques au produit ne sont présentes que dans le chemin de la requête. Vous notez également que la chaîne de requête n’est pas du tout utilisée et que deux types de données distincts sont impliqués :

* Le premier type est Masculin ou Féminin. Vous pouvez l’appeler « catégorie de produits ».
* Le second type est le nom du produit, tel que CamoPullover, qui est normalement le SKU du produit.

Compte tenu de ces informations, l’intégralité de l’URL de l’aperçu rapide suit le schéma suivant :

`/datafeed/$categoryId$-$SKU$.json`

Sur la base de cette analyse, vous utiliseriez `categoryId` et `SKU` pour les zones réactives.

Vous êtes à présent prêt à charger une bannière d’image et à y ajouter des zones réactives à l’aide de la fonctionnalité d’images interactives Shoppable d’Experience Manager Assets.

## (Facultatif) Création d’un paramètre prédéfini de visionneuse d’images interactives {#optional-creating-an-interactive-image-viewer-preset}

Vous pouvez choisir d’utiliser la valeur par défaut, le paramètre prédéfini de visionneuse d’images interactives, appelé « `Shoppable_Banner` », qui est fourni avec Experience Manager Assets. Vous pouvez également créer votre propre paramètre prédéfini de visionneuse personnalisé à utiliser avec les images interactives.

Lorsque vous créez un paramètre prédéfini de visionneuse d’images interactives, vous pouvez déterminer l’aspect des zones réactives de la bannière d’image. Dans le cadre de la création du paramètre prédéfini de visionneuse, vous pouvez choisir d’utiliser une image de zone réactive provenant d’une galerie d’images prédéfinies.

Une fois que vous avez enregistré le paramètre prédéfini de visionneuse, il est activé automatiquement dans la page de liste Paramètre prédéfini de visionneuse dans Experience Manager Assets. Cette fonctionnalité signifie qu’elle est visible dans le composant Interactive Media et chaque fois que vous affichez une ressource. Cependant, pour *diffuser* une bannière interactive avec ce paramètre prédéfini de visionneuse, *publiez* également votre paramètre prédéfini de visionneuse. Cette règle s’applique aux paramètres prédéfinis de visionneuse personnalisés ou prêts à l’emploi.

**Pour créer un paramètre prédéfini de la visionneuse pour les images interactives:**

1. Dans le rail de gauche, accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Paramètres visionneuse]**.
1. Dans le coin supérieur droit de la page, sélectionnez **[!UICONTROL Créer]**.
1. Dans la boîte de dialogue Nouveau paramètre prédéfini de la visionneuse, saisissez un nom pour décrire le paramètre prédéfini de visionneuse de bannières interactives.

   Ce titre s’affiche dans la page liste des paramètres prédéfinis de la visionneuse après l’enregistrement.

1. Dans le menu déroulant Type de média enrichi, sélectionnez **[!UICONTROL Image interactive]**.
1. Sélectionnez **[!UICONTROL Créer]**.
1. Sur la page Modifier le paramètre prédéfini de la visionneuse, sélectionnez l’onglet **[!UICONTROL Aspect]**.
1. Utilisez l’une des méthodes suivantes :

   * Pour charger votre propre image de zone réactive à utiliser sur des images, sélectionnez l’icône Sélecteur de ressources. Dans la page Sélectionner le contenu, accédez à l’image de zone réactive que vous souhaitez utiliser et sélectionnez-la. Sélectionnez l’icône représentant une coche dans le coin supérieur droit.
   * Pour sélectionner une image de zone réactive prédéfinie, sélectionnez l’icône Galerie de zones réactives. Dans la palette de la galerie de zones réactives, sélectionnez l’image de zone réactive que vous souhaitez utiliser.

1. Dans le coin supérieur droit de la page, sélectionnez **[!UICONTROL Enregistrer]**.

   Assurez-vous de publier le nouveau paramètre prédéfini de la visionneuse.

   Voir [Publication de paramètres de visionneuse prédéfinis](/help/assets/dynamic-media/managing-viewer-presets.md#publishing-viewer-presets).

   Vous êtes désormais prêt à charger une bannière d’image.

## Chargez une bannière d’image {#uploading-an-image-banner}

Si vous avez déjà chargé les images que vous souhaitez utiliser, passez à l’étape suivante [Ajout de zones réactives à une bannière d’image](#adding-hotspots-to-an-image-banner).

**Pour charger une bannière d’image :**

1. Chargez les bannières d’images que vous souhaitez rendre interactives.

   Voir la section [Chargement des ressources](/help/assets/manage-digital-assets.md#uploading-assets).

   Vous êtes maintenant prêt à ajouter des zones réactives à la bannière d’image. Reportez-vous à la tâche suivante ci-dessous.

## Ajout de zones réactives à une bannière d’image {#adding-hotspots-to-an-image-banner}

Vous pouvez ajouter des zones réactives à une bannière d’image à l’aide de l’éditeur dans la page Gestion des zones réactives.

Lorsque vous ajoutez des zones réactives, vous pouvez les définir comme un écran pop-up d’aperçu rapide, un lien hypertexte ou un fragment d’expérience.

Voir [Fragments d’expérience](/help/sites-cloud/authoring/fragments/content-fragments.md).

>[!NOTE]
>
>Les outils de partage sur les réseaux sociaux ne sont pas pris en charge dans l’image interactive lorsque vous incorporez la visionneuse dans un fragment d’expérience. Utilisez ou créez plutôt des paramètres prédéfinis de visionneuse qui ne comportent pas d’outils de partage sur les réseaux sociaux. Ces paramètres prédéfinis de visionneuse vous permettent de l’incorporer dans des fragments d’expérience.

Les options Annuler et Rétablir, proches du coin supérieur droit de la page, sont prises en charge au cours de la session de création/modification actuelle.

Lorsque vous avez fini de créer votre image interactive, vous pouvez utiliser l’aperçu pour afficher une représentation de votre image interactive telle qu’elle s’affiche pour les clients.

Voir [(Facultatif) Aperçu des images interactives](#optional-previewing-interactive-images).

>[!NOTE]
>
>Lorsque vous ajoutez des zones réactives à une image dans une image interactive ou une bannière de carrousel, les informations de ces zones sont stockées au même emplacement de métadonnées. Cet emplacement dépend de l’emplacement de l’image, qu’il s’agisse d’une image interactive ou d’une bannière de carrousel. Cette fonctionnalité signifie que vous pouvez réutiliser facilement la même image (avec ses données de zone réactive définies) dans les visionneuses.
>
>Notez cependant que les bannières de carrousel prennent en charge les images à zones cliquables, qui peuvent également contenir des zones réactives. Les images interactives n’en comportent pas. Gardez cela en tête si vous envisagez de créer une image interactive ou une bannière de carrousel qui utilise la même image. Vous pouvez créer des images interactives et des bannières de carrousel en utilisant des copies distinctes de la même image à la place.
>
>Voir aussi [Bannières de carrousel](/help/assets/dynamic-media/carousel-banners.md).

>[!NOTE]
>
>Si vous modifiez des images interactives avec des zones réactives et que vous recadrez l’image, les zones réactives sont supprimées.

**Pour ajouter des zones réactives à une bannière d’image :**

1. Dans la vue Ressources, accédez à la bannière d’image que vous avez chargée et que vous souhaitez rendre interactive.
1. Utilisez l’une des méthodes suivantes :

   * Pointez sur l’image, puis sélectionnez **[!UICONTROL Sélectionner]** (icône de coche). Dans la barre d’outils, sélectionnez **[!UICONTROL Modifier]**.

   * Pointez sur l’image, puis sélectionnez **[!UICONTROL Autres actions]** (icône représentant des points de suspension) > **[!UICONTROL Modifier]**.

   * Pour l’ouvrir dans la page Affichage des détails, sélectionnez l’image. Dans la barre d’outils, sélectionnez **[!UICONTROL Modifier]**.

1. Près du coin supérieur gauche de la page, sélectionnez **[!UICONTROL Ajouter une zone réactive]** (icône Appuyer avec le doigt) pour ouvrir la page de gestion des zones réactives.
1. Dans le coin supérieur gauche de la page, sélectionnez **[!UICONTROL Zone réactive]**.

   1. Dans le coin supérieur gauche de la page de gestion des zones réactives, sélectionnez **[!UICONTROL Zone réactive]**.
   1. Sur l’image, sélectionnez un emplacement où vous souhaitez que la zone réactive s’affiche. Si nécessaire, faites glisser la zone réactive pour en ajuster l’emplacement. Vous pouvez également utiliser les touches fléchées du clavier pour contrôler la position d’une zone réactive sélectionnée.
   1. Ajoutez des zones réactives supplémentaires si nécessaire en répétant les étapes a et b.
   1. (Facultatif) Pour supprimer une zone réactive, sélectionnez-la sur l’image, puis sélectionnez **[!UICONTROL Supprimer]** (icône corbeille) sous l’en-tête **[!UICONTROL Zone réactive]**.

1. Dans le champ de texte Nom, saisissez le nom de la zone réactive. Ce nom apparaît également dans la liste déroulante Zone réactive sélectionnée.
1. Utilisez l’une des méthodes suivantes :

   * Sélectionnez **[!UICONTROL Aperçu rapide]**.

      * Si vous êtes client Experience Manager Sites ou eCommerce, sélectionnez l’icône de sélecteur de produit (loupe) afin d’afficher la page Sélectionner un produit. Sélectionnez le produit à utiliser, puis sélectionnez **Sélectionner** dans le coin supérieur droit de la page. Vous voici de retour dans la page de gestion des zones réactives.
      * Si vous *n’êtes pas* client Experience Manager Sites ou eCommerce :

         * Consultez [Identification des variables de zone réactive](#optional-identifying-hotspot-variables) ; vous devez définir ces variables.
         * Ensuite, entrez manuellement la valeur de SKU. Dans le champ de texte Valeur du SKU, saisissez le SKU du produit. La valeur SKU saisie renseigne automatiquement la partie variable du modèle d’aperçu rapide. Cela garantit que le système peut associer la zone réactive à l’aperçu rapide d’un SKU en particulier.
         * (Facultatif) S’il existe d’autres variables dans l’aperçu rapide que vous utilisez généralement pour identifier un produit, sélectionnez **[!UICONTROL Ajouter la variable générique]**. Dans le champ de texte, spécifiez une variable supplémentaire. Par exemple, `category=Mens` est une variable ajoutée.

   * Sélectionnez **[!UICONTROL Lien hypertexte]**.

      * Si vous êtes client Experience Manager Sites, sélectionnez l’icône Sélecteur de site (dossier). Accédez à une URL. La méthode de liaison basée sur une URL n’est pas possible si votre contenu interactif contient des liens avec des URL relatives, en particulier des liens vers des pages Experience Manager Sites.
      * Si vous êtes un client ou une cliente autonome, dans le champ de texte HREF, spécifiez le chemin URL complet vers une page web liée.

   Veillez à spécifier si vous souhaitez ouvrir le lien dans un nouvel onglet du navigateur (paramètre par défaut recommandé) ou dans le même onglet.

   Pour plus d’informations, voir [Utilisation de sélecteurs](/help/assets/dynamic-media/working-with-selectors.md).

   * Sélectionnez **[!UICONTROL Fragment d’expérience]**.

      * Si vous êtes client Experience Manager Sites, sélectionnez l’icône Rechercher (loupe) afin d’ouvrir la page Fragment d’expérience. Sélectionnez le fragment d’expérience que vous souhaitez utiliser. Sélectionnez ensuite **[!UICONTROL Sélectionner]** dans le coin supérieur droit de la page. Vous voici de retour dans la page de gestion des zones réactives.
Voir [Fragments d’expérience](/help/sites-cloud/authoring/fragments/content-fragments.md).

      * Indiquez la largeur et la hauteur du fragment d’expérience tel que vous souhaitez qu’il apparaisse dans la bannière.

        >[!NOTE]
        >
        >Les outils de partage sur les réseaux sociaux ne sont pas pris en charge dans l’image interactive lorsque vous incorporez la visionneuse dans un fragment d’expérience. Utilisez ou créez plutôt des paramètres prédéfinis de visionneuse qui ne comportent pas d’outils de partage sur les réseaux sociaux. Ces paramètres prédéfinis de visionneuse vous permettent de l’incorporer dans des fragments d’expérience.

1. Sélectionnez **[!UICONTROL Enregistrer]** pour enregistrer vos modifications et revenir à la page du navigateur.
1. Publiez l’image interactive. La publication fournit la bannière via le cloud et génère également un code incorporé qui vous permet de l’intégrer à un autre site web.

   Voir [Publication de ressources](/help/assets/manage-digital-assets.md#publish-assets).

   Une fois que vous avez ajouté des zones réactives et publié l’image interactive, vous êtes prêt à l’ajouter à votre site web.

   Voir [Intégration d’une image interactive à votre site web](#integrating-an-interactive-image-with-your-website).

   >[!NOTE]
   >
   >Si vous modifiez des images interactives avec des zones réactives et que vous recadrez l’image, les zones réactives sont supprimées.

### (Facultatif) Aperçu des images interactives {#optional-previewing-interactive-images}

Vous pouvez utiliser la prévisualisation pour afficher une représentation de l’aspect de votre image interactive telle qu’elle apparaîtra à vos clients. La prévisualisation vous permet également de tester les zones réactives de l’image afin de vous assurer qu’elles se comportent comme prévu.

Lorsque vous êtes satisfait de l’image interactive, vous pouvez la publier.
Voir [Incorporation de la visionneuse de vidéos ou d’images dans une page web](/help/assets/dynamic-media/embed-code.md).
Consultez [Liaison d’URL à une application web](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md). La méthode de liaison basée sur une URL n’est pas possible si votre contenu interactif contient des liens avec des URL relatives, en particulier des liens vers des pages Experience Manager Sites.
Voir [Ajout de ressources Dynamic Media aux pages](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).

**Pour prévisualiser des images interactives :**

1. En mode Ressources, accédez à une image interactive existante que vous avez créée et sélectionnez-la pour la prévisualiser.
1. Près du coin supérieur gauche de la page de prévisualisation, dans la liste déroulante Contenu, sélectionnez **[!UICONTROL Visionneuses]**.
1. Dans la liste Visionneuse, sélectionnez **[!UICONTROL Shoppable_Banner]** ou sur le nom du paramètre prédéfini de visionneuse d’images interactives que vous avez créé.
1. Pour tester les actions associées aux zones réactives, sélectionnez-les sur l’image.

## Publication des ressources d’images interactives {#publishing-interactive-image-assets}

Voir [Publication de ressources](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md) pour obtenir des informations sur la publication de ressources d’images interactives.

## Intégration d’une image interactive à votre site web {#integrating-an-interactive-image-with-your-website}

Lorsque vous chargez une image de bannière, que vous ajoutez des zones réactives à l’image et que vous publiez l’image interactive, vous pouvez l’ajouter dans une page de votre site web.

Si vous êtes un client Experience Manager Sites, vous pouvez ajouter l’image interactive en faisant glisser le composant Interactive Media dans votre page. Voir [Ajout de ressources Dynamic Media aux pages](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).

Si vous êtes un client Experience Manager Assets autonome, vous pouvez ajouter manuellement l’image interactive à votre site web, comme indiqué dans cette section.

1. Copiez le code intégré de l’image interactive publiée.
Voir [Incorporation de la visionneuse de vidéos ou d’images dans une page web](/help/assets/dynamic-media/embed-code.md).

1. Ajoutez le code intégré copié à l’emplacement souhaité dans la page web.
Le code intégré copié est défini pour un environnement réactif afin qu’il s’adapte automatiquement à la zone qui lui est affectée.

**Exemple**

En prenant comme exemple le [site web de démonstration](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html?lang=fr), notez que l’image des trois personnes est une balise `IMG` statique :

```xml {.line-numbers}
<img class="img-responsive" width="100%" title="Hero Image 2" alt="Hero Image 2" src="images/shoppable-banner.jpg">
```

L’intégration revient simplement à supprimer la balise `IMG` et à la remplacer par le code intégré copié à partir d’Experience Manager Assets. Vous pouvez voir que le résultat [montre l’image interactive Shoppable sur la page avec trois zones réactives en cercle](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-1.html?lang=fr).

>[!NOTE]
>
>À ce stade, les zones réactives de l’image interactive Shoppable du site web de démonstration sont en mode affichage uniquement. Elles ne sont pas encore intégrées aux aperçus rapides existants.

Pour appliquer un « recadrage » à une image interactive shoppable pour rendre plus réactif votre environnement, ajoutez l’attribut de configuration Image interactive `ZoomView.iscommand` au chemin d’accès. Dans ce cas, le composant `ZoomView` est appelé et `iscommand` est la commande de diffusion d’image de recadrage que vous appliquez.

Voir l’attribut de configuration [ZoomView.iscommand](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/command-reference-configuration-attributes-interactive-images/r-html5-aem-interactive-image-config-attrib-zoomview-iscommand.html?lang=fr).

Voir la commande de service d’images [crop](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-crop.html?lang=fr).

Vous pouvez désormais intégrer l’image interactive à un aperçu rapide existant de votre site web.

## Intégration d’une image interactive dans un aperçu rapide existant {#integrating-an-interactive-image-with-an-existing-quickview}

>[!NOTE]
>
>Cette tâche ne s’applique que si vous êtes un client Experience Manager Assets autonome.

La dernière étape de cette procédure intègre l’image interactive à un aperçu rapide existant sur votre site web. Pour ce qui est de l’intégration, il n’existe pas de solution qui fonctionne dans tous les cas. Chaque mise en œuvre d’aperçu rapide est unique et une approche spécifique est donc nécessaire. Ainsi, il est utile de faire appel à l’assistance d’un informaticien responsable du front-end.

L’implémentation d’aperçus rapides existante représente normalement une chaîne d’actions interdépendantes qui se produisent sur la page web dans l’ordre suivant :

1. Un utilisateur déclenche un élément dans l’interface utilisateur de votre site web.
1. Le code en front-end obtient une URL d’aperçu rapide basée sur l’élément d’interface utilisateur qui a été déclenché à l’étape 1.
1. Le code en front-end envoie une demande Ajax en utilisant l’URL obtenue à l’étape 2.
1. La logique du serveur principal renvoie les données ou le contenu de l’aperçu rapide correspondant au code en front-end.
1. Le code en front-end charge les données ou le contenu de l’aperçu rapide.
1. Facultativement, le code en front-end convertit les données chargées de l’aperçu rapide en une représentation HTML.
1. Le code en front-end affiche une boîte de dialogue ou un panneau modal et effectue le rendu du contenu HTML à l’écran pour l’utilisateur.

Ces appels ne représentent pas nécessairement des appels d’API publics indépendants qui sont appelés en suivant la logique de la page web à partir d’une étape arbitraire. Il s’agit plutôt d’un appel chaîné où chaque étape suivante est masquée dans la dernière phase (rappel) de l’étape précédente.

Lorsque l’image interactive shoppable remplace l’étape 1 et partiellement l’étape 2, l’utilisateur touche une zone réactive à l’intérieur de l’image shoppable. Cette interaction utilisateur est gérée par le lecteur de contenu. La visionneuse renvoie un événement à la page web qui contient toutes les données des zones réactives ajoutées précédemment dans Experience Manager Assets.

Dans ce type de gestionnaire d’événements, le code en front-end effectue les opérations suivantes :

* Il écoute un événement émis par l’image interactive d’achat.
* Il construit une URL d’aperçu rapide en fonction des données de la zone réactive.
* Il déclenche le processus de chargement de l’aperçu rapide depuis le serveur principal et en effectue le rendu à l’écran.

Le code intégré renvoyé par Experience Manager comporte déjà un descripteur d’événement prêt à l’emploi, qui est commenté, comme vous pouvez le constater, dans le fragment de code mis en surbrillance ci-dessous :

```xml {.line-numbers}
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
                    //To pass other parameter from the hotspot, add custom parameter during the hotspot setup as parameterName=value
                    loadQuickView(sku); //Replace this call with your Quickview plugin
                    //See your Quickviewer plugin for the Quickview call
                 },
             });
        */
        s7interactiveimageviewer.init();
```

Il suffit donc de supprimer les commentaires du code et de remplacer le corps factice du gestionnaire par le code spécifique à la page web.

Le processus de création de l’URL d’aperçu rapide est l’opposé du processus utilisé pour identifier les variables des zones réactives décrit précédemment.

Voir [Identification des variables des zones réactives](#optional-identifying-hotspot-variables).

En utilisant nos exemples précédents d’URL d’aperçu rapide, vous pouvez voir, dans les exemples suivants, comment l’URL est créée dans chaque cas :

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

La dernière étape pour déclencher l’URL d’aperçu rapide et activer le panneau d’aperçu rapide nécessite l’assistance d’une personne disposant des compétences front-end nécessaires. Cette personne sait comment déclencher précisément l’implémentation de l’aperçu rapide à l’aide de l’étape appropriée, avec une URL d’aperçu rapide prête à l’emploi.

Vous pouvez découvrir comment ces étapes sont appliquées au site web de démonstration pour l’intégration complète d’une image interactive publicitaire avec le code d’aperçu rapide. Plus tôt, la structure de l’URL de l’aperçu rapide a été identifiée comme suit :

```xml {.line-numbers}
/datafeed/$categoryId$-$SKU$.json
```

Pour reconstruire cette URL dans le gestionnaire `quickViewActivate`, vous pouvez utiliser les champs `categoryId` et `SKU`. Ces champs sont disponibles dans l’objet `inData` transmis au gestionnaire par le code du lecteur :

```xml {.line-numbers}
var sku=inData.sku;
var categoryId=inData.categoryId;
var quickViewUrl = "datafeed/" + categoryId + "-" + sku + ".json";
```

Le site web de démonstration déclenche la boîte de dialogue d’aperçu rapide si vous utilisez un simple appel de la fonction `loadQuickView()`. Cette fonction n’accepte qu’un seul argument, qui est l’URL des données d’aperçu rapide. Ainsi, la dernière étape nécessaire pour intégrer l’image interactive Shoppable consiste à ajouter la ligne de code ci-dessous au gestionnaire `quickViewActivate` :

```xml {.line-numbers}
loadQuickView(quickViewUrl);
```

Voici le code source complet :

```xml {.line-numbers}
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

Le [site web de démonstration final avec l’image interactive entièrement intégrée](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-3.html?lang=fr).

## Création de pop-ups personnalisés à l’aide de l’aperçu rapide {#using-quickviews-to-create-custom-pop-ups}

Voir [Création de fenêtres pop-up personnalisées à l’aide de l’aperçu rapide](/help/assets/dynamic-media/custom-pop-ups.md).
