---
title: Vidéos interactives
description: Découvrez comment utiliser des vidéos interactives et Shoppable dans Dynamic Media.
feature: Interactive Videos
role: User
exl-id: e4859223-91de-47a1-a789-c2a9447e5f71
source-git-commit: fa6de4e383b4de628938fce455f321911cad452c
workflow-type: tm+mt
source-wordcount: '5938'
ht-degree: 73%

---

# Vidéos interactives{#interactive-videos}

Vous pouvez facilement créer des vidéos interactives, également appelées vidéos Shoppable, qui génèrent des conversions directement à partir de la vidéo. L’engagement du client avec la vidéo a lieu dans un panneau à côté du lecteur vidéo, où les miniatures des services, informations ou produits associés défilent en fonction de ce qui est présenté dans la vidéo. Les clients peuvent sélectionner la miniature et être directement liés au service, ajouter l’article à un panier pour un achat immédiat ou être liés à une page web pour plus d’informations.

Une fois la vidéo terminée, un résumé visuel de toutes les offres s’affiche pour générer un appel à l’action. Les clients ont une autre opportunité de sélectionner l’élément qu’ils souhaitent. Ces expériences concrètes et spécifiques augmentent les interactions et les conversions des clients.

Voir aussi [Images interactives](/help/assets/dynamic-media/interactive-images.md).

## Vidéos interactives à l’œuvre {#interactive-video-in-action}

Pour voir une vidéo interactive Shoppable en action, sélectionnez [Démonstrations en direct](https://landing.adobe.com/en/na/dynamic-media/ctir-2755/live-demos.html), faites défiler la page jusqu’à l’en-tête **[!UICONTROL Médias Shoppable]**, puis sélectionnez la vidéo Shoppable pour commencer la lecture.

* Pendant la lecture, lorsque les produits sont utilisés dans la vidéo, le produit identique s’affiche à droite sous forme de miniature.

* Pour suspendre la vidéo et ouvrir l’aperçu rapide du produit, sélectionnez la miniature. Par exemple, sélectionnez l’image miniature de KitchenAid dans la vidéo pour afficher une visionneuse à 360° du mixeur ou effectuez un zoom avant pour afficher les détails du mixeur.

Voir aussi [Utilisation de la vidéo interactive avec Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-interactive-video-feature-video-use.html?lang=fr#dynamic-media)

<!-- 

There was a link here that showed the video frame of an interactive video and when the reader selected the frame the video would play https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-video/AXIS/index.html. This now needs to call a new interactive video

-->

<!-- 

[A frame from an interactive, shoppable video](assets/chlimage_1-126.png) *A video frame capture from an interactive, shoppable video.*

-->

>[!NOTE]
>
>Si vous créez une vidéo interactive pour lancer une page web lorsqu’un utilisateur sélectionne une image miniature, certains périphériques empêchent l’ouverture de la page web contextuelle. Dans ce cas, modifiez le paramètre de blocage des fenêtres contextuelles sur le dispositif. Par exemple, sur un iPhone 6 Apple, accédez à **[!UICONTROL Paramètres]** > **[!UICONTROL Safari]** > **[!UICONTROL Bloquer les fenêtres contextuelles]**, puis faites glisser la commande sur **[!UICONTROL Désactivé]**. Désormais, lorsque vous lisez une vidéo interactive et sélectionnez une miniature, vous êtes invité à ouvrir la fenêtre contextuelle. Si vous acceptez, la page web s’affiche.

### Découvrez comment les vidéos interactives sont créées {#watch-how-interactive-videos-are-created}

Regardez une présentation sur [la manière dont les vidéos interactives sont créées](https://s7d5.scene7.com/s7viewers/html5/VideoViewer.html?videoserverurl=https://s7d5.scene7.com/is/content/&amp;emailurl=https://s7d5.scene7.com/s7/emailFriend&amp;serverUrl=https://s7d5.scene7.com/is/image/&amp;config=Scene7SharedAssets/Universal_HTML5_Video_social&amp;contenturl=https://s7d5.scene7.com/skins/&amp;asset=S7tutorials/InteractiveVideo) (7 minutes et 30 secondes).
(Même si la présentation vidéo est personnalisée grâce à Assets on Demand, les principes et les étapes restent compatibles avec les vidéos interactives dans Adobe Experience Manager Assets.)

### Webinaire « Succès des clients Adobe »  {#adobe-customer-success-webinar}

Le [webinaire Utiliser la vidéo interactive, le partage de lien et le partage YouTube dans les ressources du Experience Manager](https://adobecustomersuccess.adobeconnect.com/p1yxzdo4aec/) vous explique comment utiliser la vidéo interactive et d’autres fonctionnalités pour lier des événements pilotés par la conversion dans votre contenu marketing vidéo.

## Démarrage rapide : vidéos interactives {#quick-start-interactive-videos}

La description du workflow étape par étape qui suit est conçue pour vous aider à démarrer et à utiliser rapidement les vidéos interactives dans Dynamic Media.

Recherchez le titre **Exemple** dans certaines tâches de démarrage rapide. Il contient un court tutoriel reposant sur cette [page web de démonstration de démarrage qui n’est *pas encore* interactive](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-video/john-lewis/landing-0.html).

Les **exemples** permettent d’illustrer les étapes d’intégration de vidéos interactives à votre site web.

Au terme du tutoriel dans la dernière section Exemple, [votre page web de démonstration finale avec la vidéo interactive entièrement intégrée apparaît sous cette forme](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-video/john-lewis/landing-3.html).

Étapes de la vidéo interactive :

1. **(Facultatif) Identifiez les variables**  d’aperçu rapide : commencez par identifier les variables dynamiques utilisées par votre mise en oeuvre existante de l’aperçu rapide. Vous utilisez des variables pour mapper des vignettes de produit à l’aperçu rapide du produit correspondant lorsque vous créez votre vidéo interactive. Consulter [(Facultatif) Identification des variables d’aperçu rapide](#optional-identifying-quickview-variables).
   **Cette étape n’est nécessaire que si toutes les conditions suivantes sont vraies** :
• Vous souhaitez ajouter de l’interactivité à votre vidéo en déclenchant des aperçus rapides.
• Votre mise en œuvre d’Experience Manager 
*n’utilise pas* de framework d’intégration de commerce électronique pour extraire des données de produit dans Experience Manager à partir d’une solution de commerce électronique, comme IBM® WebSphere® Commerce, Elastic Path, SAP Hybris ou Intershop.

1. **(Facultatif) Créer un paramètre prédéfini de visionneuse de vidéos interactives** : personnalisez l’aspect et le comportement des différents composants qui constituent la visionneuse, comme la barre vidéo et les miniatures interactives.
Vous n’avez pas besoin de créer votre propre paramètre prédéfini de visionneuse de vidéos interactives si vous envisagez plutôt d’utiliser les paramètres de visionneuse de vidéos interactives prêts à l’emploi `Shoppable_Video_Light` ou `Shoppable_Video_Dark`.
Voir [Création d’un paramètre prédéfini de visionneuse](/help/assets/dynamic-media/managing-viewer-presets.md#creating-a-new-viewer-preset) (facultatif) et [Remarques spéciales sur la création d’un paramètre prédéfini de visionneuse interactive](/help/assets/dynamic-media/managing-viewer-presets.md#special-considerations-for-creating-an-interactive-viewer-preset).

1. **Charger une vidéo et les ressources d’image associées** : chargez une vidéo et les images associées auxquelles vous souhaitez ajouter de l’interactivité.
Voir [Chargement d’une vidéo et des ressources miniatures associées](#uploading-a-video-and-its-associated-thumbnail-assets).

1. **Ajouter de l’interactivité à votre vidéo** : ajoutez un ou plusieurs segments temporels à la vidéo. Ensuite, associez les vignettes dans ces segments temporels. Affectez chaque miniature d’image à une action telle qu’un lien hypertexte, un aperçu rapide ou un fragment d’expérience.
(La méthode de liaison basée sur une URL n’est pas possible si votre contenu interactif contient des liens avec des URL relatives, en particulier des liens vers des pages Experience Manager Sites.)
Terminez en publiant les ressources vidéo interactives. La publication crée le code intégré ou l’URL que vous copiez et appliquez à la fin dans la page d’entrée de votre site web. Voir [Ajout d’interactivité à votre vidéo](#adding-interactivity-to-your-video).
Voir [Publier les ressources](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

1. **Ajouter une vidéo interactive à votre site web ou sur votre site web dans** – Si vous utilisez Experience Manager Sites ou Experience Manager eCommerce, ou les deux, ajoutez la vidéo interactive à une page web dans Experience Manager. Faites glisser le composant Interactive Media sur la page. Voir [Ajout de ressources Dynamic Media aux pages](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).
Utilisez le code intégré ou l’URL pour intégrer votre vidéo interactive aux expériences de votre site web. Voir [Intégration d’une vidéo interactive à votre site web](#integrating-an-interactive-video-with-your-website).
Si vous utilisez un gestionnaire de contenu web (WCM) tiers, vous devez intégrer la nouvelle vidéo interactive à l’aperçu rapide existant utilisé sur votre site web. Voir [Intégration d’une vidéo interactive à un aperçu rapide existant](#integrating-an-interactive-video-with-an-existing-quickview).
   [Ajout de ressources Dynamic Media aux pages](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md)

## (Facultatif) Identification des variables d’aperçu rapide {#optional-identifying-quickview-variables}

>[!NOTE]
>
>Cette tâche n’est nécessaire que si les conditions ci-dessous sont vraies :
>
>* Vous souhaitez ajouter de l’interactivité à votre vidéo en déclenchant des aperçus rapides.
>* Votre mise en œuvre d’Experience Manager *n’utilise pas* de framework d’intégration de commerce électronique pour extraire des données de produit dans Experience Manager à partir d’une solution de commerce électronique, comme IBM® WebSphere® Commerce, Elastic Path, SAP Hybris ou Intershop. <!-- See [eCommerce concepts in Experience Manager Assets](/help/sites-administering/concepts.md).-->

>
>Si votre mise en œuvre d’Experience Manager utilise l’e-commerce, vous pouvez ignorer cette tâche et passer à la tâche suivante.

Commencez par identifier les variables dynamiques utilisées par votre mise en œuvre existante d’aperçu rapide pour faire correspondre les miniatures de produits à l’aperçu rapide des produits correspondants lors du processus de création de vidéo interactive.

Lorsque vous ajoutez des segments temporels à une vidéo, vous affectez une SKU (unité de gestion des stocks) et toute variable supplémentaire à chaque miniature que vous ajoutez à un segment. Ces variables sont utilisées ultérieurement pour afficher le produit le bon aperçu rapide.

Il est important d’identifier correctement les variables qui sont requises pour déclencher de manière unique l’Aperçu rapide d’un produit.

Il suffit parfois de consulter les informaticiens responsables de votre mise en oeuvre existante de l’aperçu rapide. Il est probable qu’ils connaissent le jeu minimal de données qui identifie l’aperçu rapide dans le système. Cependant, il est possible d’analyser le comportement existant du code en front-end.

La plupart des implémentations d’aperçu rapide utilisent le paradigme suivant :

* L’utilisateur active un élément d’interface utilisateur sur le site web. Par exemple, en sélectionnant un bouton &quot;Aperçu rapide&quot;.
* Le site web envoie une demande Ajax au serveur principal afin de charger les données ou le contenu de l’aperçu rapide, le cas échéant.
* Les données de l’aperçu rapide sont traduites en contenu en préparation du rendu sur la page web.
* Enfin, le code en front-end effectue le rendu visuel de ce contenu à l’écran.

L’approche consiste donc à visiter différentes zones de votre site web existant où l’aperçu rapide est mis en oeuvre. Ensuite, déclenchez l’aperçu rapide et acquérez l’URL Ajax envoyée par la page web pour charger les données ou le contenu de l’aperçu rapide.

Normalement, il n’est pas nécessaire d’utiliser des outils de débogage spécialisés. Les navigateurs web modernes incluent des inspecteurs web qui font un travail correct. Vous trouverez ci-dessous quelques exemples de navigateurs web qui incluent des inspecteurs web :

* Pour afficher toutes les requêtes HTTP sortantes dans Google Chrome, appuyez sur **F12** (Windows®) ou **Command+Options+I** (Mac) pour ouvrir le panneau Outils de développement, puis sélectionnez l’onglet **Réseau**.

* Dans Firefox, vous pouvez activer le plug-in Firebug en appuyant sur **F12** (Windows®) ou **Contrôle+Option+I** (Mac) et utiliser l’onglet **[!UICONTROL Réseau]**. Sinon, vous pouvez utiliser l’outil Inspecteur intégré et son onglet Réseau.

* Dans Internet Explorer, activez l’outil de débogage en appuyant sur **F12**.

Lorsque la surveillance de réseau est activée dans le navigateur, déclenchez l’aperçu rapide sur la page.

Vous trouvez maintenant l’URL Ajax d’aperçu rapide dans le journal réseau. Copiez l’URL enregistrée pour l’analyse ultérieure. En règle générale, lorsque vous déclenchez l’aperçu rapide, de nombreuses requêtes sont envoyées au serveur. En règle générale, l’URL Ajax d’aperçu rapide est l’une des premières dans la liste. Elle possède une partie de chaîne de requête complexe ou un chemin d’accès, et son type de réponse MIME est `text/html`, `text/xml` ou `text/javascript`.

Au cours de ce processus, il est important de parcourir différentes zones de votre site web, avec différentes catégories et types de produits. Cela est dû au fait que les URL d’aperçu rapide comportent des parties communes pour une catégorie de site web donnée, mais ne changent que si vous visitez une autre zone du site web.

Dans le cas le plus simple, la seule partie variable dans l’URL de l’aperçu rapide est le SKU du produit. Dans ce cas, la valeur de SKU du produit est la seule donnée requise pour ajouter des vignettes sur un segment temporel dans la vidéo interactive dans Experience Manager.

Cependant, dans les cas complexes, l’URL d’aperçu rapide comporte différents éléments variables en plus du SKU du produit, tels que l’ID de catégorie et le code couleur. Dans ce cas, chaque élément de ce type est une variable distincte dans la définition des données de miniatures dans Experience Manager.

Consultez ci-dessous les exemples d’URL d’aperçu rapide et les variables de miniatures qui en résultent :

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
    </ul> <p>La seule partie variable de l’URL est la valeur du paramètre de chaîne de requête <code>productId=</code>, et il s’agit clairement d’une valeur de SKU. Par conséquent, seuls les champs SKU des miniatures doivent être renseignés avec des valeurs comme <strong><code>866558</code></strong>, <strong><code>1196184</code></strong>, <strong><code>1081492</code></strong> et <strong><code>1898294</code></strong>.</p> </td>
  </tr>
  <tr>
    <td><p>SKU unique, trouvé dans le chemin d’accès à l’URL.</p> </td>
    <td><p>Les URL d’aperçu rapide enregistrées incluent ce qui suit :</p>
    <ul>
      <li><p><code>https://server/product/6422350843</code></p> </li>
      <li><p><code>https://server/product/1607745002</code></p> </li>
      <li><p><code>https://server/product/0086724882</code></p> </li>
    </ul> <p>La partie variable se trouve dans la dernière partie du chemin et elle devient la valeur de SKU des miniatures Experience Manager : <strong><code>6422350843</code></strong>, <strong><code>1607745002</code></strong> et <strong><code>0086724882</code></strong>.</p> </td>
  </tr>
  <tr>
    <td><p>SKU et ID de catégorie dans la chaîne de requête.</p> </td>
    <td><p>Les URL d’aperçu rapide enregistrées incluent ce qui suit :</p>
    <ul>
      <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=305466</code></p> </li>
      <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=310181</code></p> </li>
      <li><p><code>https://server/quickView/product/?category=1740148&amp;prodId=308706</code></p> </li>
    </ul> <p>Dans ce cas, l’URL comporte deux parties différentes. Le SKU est stocké dans le paramètre <code>prodId</code> et l’ID de catégorie dans le paramètre <code>category=</code>.</p> <p>Par conséquent, les définitions des miniatures sont des paires. Autrement dit, une valeur de SKU et une variable supplémentaire appelée <code>categoryId</code>. Les paires obtenues sont les suivantes :</p>
    <ul>
      <li>Le SKU est <code>305466</code> et <code>categoryId</code> est <code>1100004</code></li>
      <li>Le SKU est <code>310181</code> et <code>categoryId</code> est <code>1100004</code></li>
      <li>Le SKU est <code>308706</code> et <code>categoryId</code> est <code>1740148</code></li>
    </ul> <p> </p> </td>
  </tr>
  </tbody>
</table>

**Exemple**

Lorsque l’approche ci-dessus est appliquée à l’exemple de site web, la page web comporte différentes vignettes de produit, auxquelles est associé un bouton « AFFICHER PLUS » :

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-video/john-lewis/landing-0.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-video/john-lewis/landing-0.html)

Après avoir activé tous les aperçus rapides de produits disponibles sur la page, vous obtenez la liste suivante de demandes d’aperçu rapide effectuées au serveur principal :

* datafeed/candles-233396346.json
* datafeed/candles-233978050.json
* datafeed/candles-234024346.json
* datafeed/candles-234024356.json
* datafeed/candles-234024359.json
* datafeed/cushions-233939848.json
* datafeed/cushions-234019477.json
* datafeed/cushions-234019483.json
* datafeed/furniture-231747479.json
* datafeed/furniture-232625621.json
* datafeed/furniture-232625626.json
* datafeed/furniture-233939810.json
* datafeed/furniture-233939825.json
* datafeed/furniture-233939828.json
* datafeed/furniture-233939853.json
* datafeed/furniture-233940334.json
* datafeed/glassware-000064007.json
* datafeed/glassware-230722193.json
* datafeed/glassware-233916550.json
* datafeed/glassware-233916597.json

Lorsque vous observez les appels de serveur, vous constatez que les informations spécifiques au produit ne sont présentes que dans le chemin de la requête. Vous notez également que la chaîne de requête n’est pas du tout utilisée et que deux types de données distincts sont impliqués :

* Le premier type concerne les bougies, les coussins, les meubles et la verrerie. Vous pouvez l’appeler « catégorie de produits ».
* Le second type est un code de produit, comme 233916597. Vous pouvez considérer qu’il s’agit de la « SKU du produit ».

Compte tenu de ces informations, l’intégralité de l’URL de l’aperçu rapide suit le schéma suivant :

`/datafeed/$categoryId$-$SKU$.json`

En fonction de cette analyse, vous concluez que vous pouvez utiliser les deux variables ci-dessous pour les miniatures : `categoryId` et `SKU`.

Vous êtes maintenant prêt à charger une vidéo et les ressources de vignette associées.

## (Facultatif) Création d’un paramètre prédéfini de visionneuse de vidéos interactives {#optional-creating-an-interactive-video-viewer-preset}

Vous pouvez ignorer cette tâche et passer à la tâche suivante si vous envisagez d’utiliser les types de paramètres prédéfinis de visionneuse de vidéos interactives par défaut, prêtes à l’emploi, `Shoppable_Video_dark` ou `Shoppable_Video_light`.

Lorsqu’une miniature est sélectionnée dans l’environnement de création, un aperçu de la boîte de dialogue Aperçu rapide s’affiche.

![chlimage_1-21](assets/chlimage_1-127.png)

Vous avez la possibilité de créer votre propre paramètre prédéfini de visionneuse de vidéos interactives personnalisé. Vous pouvez déterminer, entre autres, le style de la visionneuse de vidéos, les vignettes interactives et l’affichage sous forme de grille des vignettes, qui s’affiche à la fin de la vidéo.

Un paramètre prédéfini de visionneuse de vidéo interactive restitue correctement la vidéo et tous les segments de la chronologie que vous avez ajoutés. Il utilise également un exemple d’aperçu rapide par défaut lorsque vous sélectionnez une miniature de produit en mode Aperçu afin que vous puissiez tester son interactivité avant de la publier.

Une fois le paramètre prédéfini de la visionneuse enregistré, son état est automatiquement définit sur **On** (Activé) sur la page Paramètres prédéfinis de la visionneuse. Cet état signifie qu’il est visible dans le composant Dynamic Media et chaque fois que vous prévisualisez une vidéo avec ce paramètre prédéfini. Veillez à également publier manuellement votre nouveau paramètre prédéfini de visionneuse.

Voir [Création d’un paramètre prédéfini de visionneuse](/help/assets/dynamic-media/managing-viewer-presets.md#creating-a-new-viewer-preset) pour créer votre propre paramètre prédéfini de visionneuse de vidéos interactives.

## Chargement d’une vidéo et de ses ressources miniatures associées {#uploading-a-video-and-its-associated-thumbnail-assets}

Si vous avez déjà téléchargé votre vidéo et les ressources miniatures, passez à la section [Ajout d’interactivité à votre vidéo](#adding-interactivity-to-your-video).

Si vous avez téléchargé des vidéos ou des images incorrectes ou si vous souhaitez supprimer des vidéos ou des images transférées dont vous n’avez plus besoin, voir [Suppression de ressources](/help/assets/manage-digital-assets.md#delete-assets).

Pour télécharger une vidéo et ses ressources miniatures associées :

1. Téléchargez la vidéo et les ressources miniatures associées dans le dossier ou les dossiers de votre choix.

   Voir [Chargement de ressources](/help/assets/manage-digital-assets.md).
Voir [Chargement de ressources à l’aide de la planification de tâches FTP](/help/assets/manage-digital-assets.md).

   Ajoutez maintenant l’interactivité à votre vidéo.

## Ajout d’interactivité à votre vidéo {#adding-interactivity-to-your-video}

Vous ajoutez des segments de chronologie à une vidéo à l’aide de l’éditeur visuel intégré sur la page Créer une vidéo interactive.

Une fois que vous avez ajouté des segments de montage, vous ajoutez des images de miniatures à chaque segment. Pour chaque miniature que vous ajoutez, vous lui appliquez une action. Par exemple, vous pouvez appliquer un aperçu rapide à la miniature, ou vous pouvez lui affecter un lien hypertexte ou un fragment d’expérience.

Voir [Fragments d’expérience](/help/sites-cloud/authoring/fundamentals/experience-fragments.md).

>[!NOTE]
>
>Les outils de partage sur les médias sociaux ne sont pas pris en charge dans la vidéo interactive lorsque vous incorporez la visionneuse dans un fragment d’expérience. Il est donc plutôt conseillé d’utiliser ou de créer des paramètres prédéfinis de visionneuse qui ne disposent pas d’outils de partage sur les médias sociaux. Ces paramètres prédéfinis de visionneuse vous permettent de l’incorporer dans des fragments d’expérience.

>[!NOTE]
>
>La méthode de liaison basée sur une URL n’est pas possible si votre contenu interactif contient des liens avec des URL relatives, en particulier des liens vers des pages Experience Manager Sites.

Les options Annuler et Rétablir, proches du coin supérieur droit de la page, sont prises en charge au cours de la session de création/modification actuelle.

Une fois la vidéo interactive enregistrée, elle s’ouvre immédiatement dans l’aperçu. À partir de là, vous pouvez sélectionner un paramètre prédéfini de visionneuse de vidéos interactives et lire la vidéo pour voir une représentation approximative de son aspect pour les clients.

**Pour ajouter de l’interactivité à votre vidéo :**

1. En mode Ressources, accédez à la vidéo que vous avez téléchargée et que vous souhaitez rendre interactive.
1. Utilisez l’une des méthodes suivantes :

   * Pointez sur l’image, puis sélectionnez **[!UICONTROL Sélectionner]** (icône de coche). Dans la barre d’outils, sélectionnez **[!UICONTROL Modifier]**.

   * Pointez sur l’image, puis sélectionnez **[!UICONTROL Autres actions]** (icône représentant trois points) **[!UICONTROL Modifier]**.

   * Pour l’ouvrir dans la page Affichage des détails, sélectionnez l’image. Dans la barre d’outils, sélectionnez **[!UICONTROL Modifier]**.

1. Dans la page Créer une vidéo interactive, procédez comme suit :

   * Pour commencer la lecture de la vidéo, cliquez sur le bouton **[!UICONTROL Lire]** . Lorsqu’un produit, un service ou un détail particulier que vous souhaitez mettre en surbrillance s’affiche, sélectionnez **[!UICONTROL Ajouter un segment]** dans la barre d’outils. Répétez cette opération jusqu’à ce que vous ayez atteint la fin de la vidéo.

      Vous pouvez affecter une ou plusieurs images miniatures à chaque segment de temps ajouté. Vous pouvez ensuite lier ces miniatures aux pages produit d’aperçu rapide que les clients peuvent acheter ou aux pages web pour plus d’informations.

   * Pour commencer la lecture de la vidéo, cliquez sur le bouton **[!UICONTROL Lire]** . Lorsqu’un produit, un service ou un détail particulier que vous souhaitez mettre en surbrillance s’affiche, sélectionnez **[!UICONTROL Pause]**. Sélectionnez **[!UICONTROL Ajouter un segment]**.

      Continuez la lecture et la mise en pause de la vidéo à des points de la chronologie où vous souhaitez ajouter un segment jusqu’à la fin de la vidéo.

1. (Facultatif) Faites glisser la barre sur le **[!UICONTROL curseur d’échelle de la chronologie]** vers la gauche pour effectuer un zoom avant, ou vers la droite pour effectuer un zoom arrière. Cette action permet de contrôler le niveau de détail des segments que vous avez ajoutés.

   ![chlimage_1-22](assets/chlimage_1-128.png)

   En fonction de la durée de votre vidéo, la durée du segment propose par défaut les valeurs suivantes :

   <table>
      <tbody>
        <tr>
        <td><strong>Si la durée de la vidéo est...</strong></td>
        <td><strong>Le paramètre Durée de segment propose par défaut...</strong></td>
        </tr>
        <tr>
        <td>3 minutes ou plus</td>
        <td>60 secondes</td>
        </tr>
        <tr>
        <td>2 à 3 minutes</td>
        <td>30 secondes</td>
        </tr>
        <tr>
        <td>1 à 2 minutes</td>
        <td>20 secondes<br /> </td>
        </tr>
        <tr>
        <td>30 à 60 secondes</td>
        <td>10 secondes</td>
        </tr>
        <tr>
        <td>30 secondes ou moins</td>
        <td>5 secondes</td>
        </tr>
      </tbody>
    </table>

   La chronologie vidéo utilise autant d’espace dans l’écran qu’il y a d’espace disponible. De même, lorsque vous redimensionnez la fenêtre du navigateur, les segments ajoutés conservent leur largeur appropriée.

   Pour illustration, les trois écrans ci-dessous utilisent la même vidéo. Notez que la largeur de chaque segment varie en fonction du paramètre Échelle de la chronologie.

   ![chlimage_1-23](assets/chlimage_1-129.png)

   Capture d’écran A

   La capture d’écran A ci-dessus présente l’affichage par défaut d’une vidéo de produit de 29 secondes. Le paramètre Échelle de la chronologie est défini sur la valeur par défaut de 5 secondes.

   ![chlimage_1-130](assets/chlimage_1-130.png)

   Capture d’écran B

   Sur la capture d’écran B, le curseur d’échelle de la chronologie est passé de la valeur par défaut, 5 secondes, à 3 secondes. Notez que désormais les différents horodatages d’échelle de la chronologie correspondent tous à des intervalles de 3 secondes.

   ![chlimage_1-25](assets/chlimage_1-131.png)

   Capture d’écran C

   Sur la capture d’écran C, le paramètre Échelle de la chronologie a été défini sur 8 secondes. Notez la façon dont les segments contenant les vignettes de produit se sont réduits. Le zoom arrière de cette façon s’avère utile si la vidéo est longue et que vous souhaitez pouvoir afficher un aperçu de plus de segments que la largeur de la page ne pourrait en contenir normalement.

1. (En option) Effectuez l’une des actions suivantes :

   * Pour ajuster l’heure de début et l’heure de fin d’un segment.

      Sélectionnez un segment, puis faites glisser l’ovale bleu de début ou de fin pour ajuster respectivement l’heure de début ou de fin. L’image vidéo affichée se déplace à l’heure appropriée dans la vidéo, en fonction de vos ajustements. Le déplacement du segment de la chronologie est limité en fonction des segments adjacents dans la chronologie. Le temps minimal autorisé pour un segment est d’une seconde.

      Utilisez les raccourcis de navigation ci-dessous pour vérifier et optimiser rapidement les segments de vidéo :

      * Pour rechercher la vidéo directement au début de ce segment, sélectionnez l’ovale bleu de début.
      * Pour rechercher la vidéo directement à la fin de ce segment, sélectionnez l’ovale bleu de fin.
      * Pour renvoyer la lecture vidéo au début de ce segment, sélectionnez le segment entier.

   ![chlimage_1-26](assets/chlimage_1-132.png)

   Repositionnement de la fin d’un segment de chronologie

   * Pour supprimer un segment

      Sélectionnez le dernier segment qui se trouve sur la chronologie, puis, sur la barre d’outils, sélectionnez **[!UICONTROL Supprimer le segment]**. Si plusieurs segments sont sélectionnés, la fonction Supprimer le segment est désactivée.

      Vous ne pouvez supprimer que le dernier segment. Par exemple, si vous souhaitez supprimer tous les segments de la chronologie, vous devez toujours sélectionner le dernier segment, puis sélectionner **[!UICONTROL Supprimer le segment]**.


1. Sélectionnez un segment de temps auquel vous souhaitez associer une ou plusieurs images miniatures.
1. À droite de la vidéo, sélectionnez l’onglet **[!UICONTROL Contenu]** .
1. Sous l’onglet Contenu, sélectionnez **[!UICONTROL Sélectionner les ressources]**, puis recherchez et sélectionnez toutes les ressources d’image que vous souhaitez utiliser avec votre vidéo. Les ressources sélectionnées sont ajoutées au panneau Sélecteur de ressources dans l’onglet Contenu.

1. Dans le sélecteur de ressources, sous l’onglet Contenu, effectuez l’une des actions suivantes :

   <table>
      <tbody>
        <tr>
        <td>Pour associer une miniature à un segment de chronologie sélectionné</td>
        <td><p>Sélectionnez l’image dans le panneau du sélecteur de ressources à droite.</p> <p>Vous pouvez ajouter à un segment de chronologie autant de miniatures que vous le souhaitez. Pour chaque image que vous sélectionnez, une coche s’affiche au-dessus de l’image dans le sélecteur de ressources.</p> </td>
        </tr>
        <tr>
        <td>Pour supprimer une miniature du segment de chronologie sélectionné</td>
        <td><p>Procédez de l’une des manières suivantes :</p>
          <ul>
          <li>Dans le panneau du sélecteur de ressources, sélectionnez une image avec une coche pour la désélectionner. La ressource image est supprimée du segment de la chronologie.<br /> </li>
          <li>Dans le segment de chronologie sélectionné, sélectionnez une image, puis, dans la barre d’outils, sélectionnez <strong>Supprimer le produit</strong>.</li>
          </ul> </td>
        </tr>
      </tbody>
    </table>

   ![Sélecteur de ressources](assets/chlimage_1-133.png)

   La sélection d’une image dans le panneau du sélecteur de ressources l’ajoute au segment de chronologie sélectionné.

1. Sélectionnez une seule image miniature dans l’un des segments de la chronologie, puis sélectionnez l’onglet **[!UICONTROL Actions]** .
1. Procédez de l’une des manières suivantes :
   <table> 
    <tbody> 
      <tr> 
      <td>Pour associer l’image miniature sélectionnée à un aperçu rapide</td> 
      <td><p>Sous Type d’action, sélectionnez <strong>Aperçu rapide</strong>.</p> <p>Si vous êtes un client Experience Manager Sites ou AEM eCommerce :</p> 
       <ul> 
       <li>Notez que le champ de texte Valeur SKU est prérenseigné avec la SKU du produit sélectionné (unité de gestion des stocks). Le SKU est un identifiant unique associé à chaque produit ou service spécifique que vous proposez. Le champ est renseigné automatiquement lorsque l’image est associée à un produit dans Experience Manager Commerce.</li> 
       <li>Si le SKU prérempli est incorrect, sélectionnez l’icône Sélecteur de produit (loupe) pour ouvrir la page Sélectionner un produit . Sélectionnez le produit à utiliser, puis cochez la case dans le coin supérieur droit de la page. Vous revenez à l’éditeur vidéo interactif.</li> 
       </ul> <p> Si vous <em>n’êtes pas</em> client Experience Manager Sites ou eCommerce</p> 
       <ul> 
       <li>Voir <a href="/help/assets/dynamic-media/carousel-banners.md#identifying-hotspot-and-image-map-variables">Identification des variables des zones réactives</a>. Ces variables doivent être définies.</li> 
       <li>Par défaut, ce champ SKU utilise le nom de fichier de la ressource image sans l’extension. Pour vos fichiers, si vous suivez une convention de dénomination standard basée sur la valeur de SKU, ce champ ne nécessite généralement pas de modifications supplémentaires. </li> 
       <li>Sinon, modifiez la valeur par défaut et entrez la valeur de SKU appropriée. Dans le champ de texte Valeur de SKU, entrez la SKU, qui est un identifiant unique pour chaque produit ou service que vous proposez. La valeur de SKU entrée est renseignée automatiquement dans la partie variable du modèle d’aperçu rapide afin que le système sache associer l’image sélectionnée à l’aperçu rapide d’un SKU spécifique.</li> 
       </ul> <p>(Facultatif) S’il existe d’autres variables dans l’aperçu rapide que vous devez utiliser pour identifier un produit, sélectionnez <strong>Ajouter la variable générique</strong>. Dans le champ de texte, spécifiez une variable supplémentaire. Par exemple, <code>category=Womens</code> est une variable ajoutée.</p> <p> </p> </td> 
      </tr> 
      <tr> 
      <td>Pour associer l’image miniature sélectionnée à un lien hypertexte</td> 
      <td><p>Sous Type d’action, sélectionnez <strong>Lien hypertexte</strong>, puis effectuez l’une des opérations suivantes :</p> 
       <ul> 
       <li>Si vous êtes client Sites Experience Manager, sélectionnez l’icône Sélecteur de site (dossier) pour accéder à une page web. La méthode de liaison basée sur une URL n’est pas possible si votre contenu interactif contient des liens avec des URL relatives, en particulier des liens vers des pages Experience Manager Sites.</li> 
       <li>Si vous êtes un client Dynamic Media autonome, dans le champ de texte HREF, spécifiez le chemin URL complet vers une page web liée.</li> 
       </ul> <p>Veillez à spécifier si vous souhaitez ouvrir le lien dans un nouvel onglet du navigateur ou sur l’onglet actif.</p> </td> 
      </tr> 
      <tr> 
      <td>Pour associer l’image miniature sélectionnée à un fragment d’expérience</td> 
      <td><p>Sous Type d’action, sélectionnez <strong>Fragment d’expérience</strong>, puis procédez comme suit :<p> 
       <ul> 
       <li>Si vous êtes client Sites Experience Manager, sélectionnez l’icône Rechercher (loupe) pour ouvrir la page Fragment d’expérience. Sélectionnez le fragment d’expérience à utiliser, puis sélectionnez <strong>Pour revenir au panneau Actions de la page précédente, sélectionnez </strong>dans le coin supérieur droit de la page.<br /> Voir <a href="/help/sites-cloud/authoring/fundamentals/experience-fragments.md">Fragments d’expérience</a>.</li> 
      </ul> 
       <ul> 
       <li>Indiquez la largeur et la hauteur du fragment d’expérience tel qu’il apparaît dans la vidéo.</li>
       </ul><strong>Remarque</strong> : Les outils de partage sur les médias sociaux ne sont pas pris en charge dans la vidéo interactive lorsque vous incorporez la visionneuse dans un fragment d’expérience. Il est donc plutôt conseillé d’utiliser ou de créer des paramètres prédéfinis de visionneuse qui ne disposent pas d’outils de partage sur les médias sociaux. Ces paramètres prédéfinis de visionneuse vous permettent de l’incorporer dans des fragments d’expérience.</p></tr>&lt; 
      <tr> 
      <td>Pour modifier une action déjà attribuée à une image miniature</td> 
      <td>Dans un segment de chronologie, sélectionnez une miniature dont le libellé de texte est associé à un lien de chaîne. Ce maillon de chaîne indique qu’une action lui est attribuée. Pour apporter vos modifications, sélectionnez l’onglet <strong>Actions</strong> .</td> 
      </tr> 
      <tr> 
      <td>Pour modifier le libellé de texte d’une image miniature</td> 
      <td><p>Par défaut, le libellé de texte utilise le champ de métadonnées <code>Title</code> de l’image miniature. En l’absence de <code>Title</code>, le nom de fichier de l’image miniature est utilisé à la place, mais sans l’extension.</p> <p>Pour modifier le libellé de texte d’une vignette, sous l’onglet <strong>Actions</strong>, directement sous la ressource image qui s’affiche, entrez le texte de votre choix. Consultez l’image ci-dessous.</p> <p>Le nouveau libellé n’est utilisé que par la visionneuse vidéo proprement dite et le texte des vignettes affiché dans le segment de la chronologie. La modification du libellé n’affecte pas le champ Titre des métadonnées de la miniature ni son nom de fichier.</p> </td> 
      </tr> 
      <tr> 
      <td>Pour rétablir une modification</td> 
      <td>Près du coin supérieur droit de la page, sélectionnez <strong>Annuler</strong> ou <strong>Rétablir</strong>.</td> 
      </tr> 
    </tbody> 
   </table>

   ![experiencefragment_interactivevideos](assets/experiencefragment_interactivevideos.png)

   Un nouveau libellé de texte est ajouté à la miniature.

1. Utilisez l’une des méthodes suivantes :

   * Répétez les étapes 6 à 11 pour ajouter d’autres vignettes aux segments de la chronologie dans votre vidéo.
   * Passez à l’étape 13 (facultative).

1. (Facultatif) Effectuez l’une des opérations suivantes :

   * **[!UICONTROL Fusionner le segment]** : vous pouvez combiner deux segments adjacents (avec ou sans les miniatures de produit qui leur sont affectées) dans un seul segment.

      Dans la chronologie, sélectionnez plusieurs segments contigus que vous souhaitez fusionner en un seul. Il n’y a pas de poignées de déplacement ovales de couleur bleue sur les deux segments sélectionnés dans l’image ci-dessous.

      Sélectionnez **[!UICONTROL Fusionner le segment]** dans la barre d’outils.
   ![chlimage_1-134](assets/chlimage_1-134.png)

   Fusion de deux segments sélectionnés de cinq secondes en un segment de dix secondes.

   * **[!UICONTROL Fractionner le segment]** : vous pouvez diviser un seul segment en deux segments de durée identique. Si des vignettes de produit sont déjà affectées au segment, elles sont combinées au sein du segment de gauche.

      Dans la chronologie, sélectionnez un segment que vous souhaitez diviser en deux, puis sélectionnez **[!UICONTROL Fractionner le segment]** dans la barre d’outils.

      Si plusieurs segments sont sélectionnés, la fonction **[!UICONTROL Fractionner le segment]** est désactivée.
   ![chlimage_1-135](assets/chlimage_1-135.png)

   Division d’un segment de dix secondes en deux segments d’une durée de cinq secondes.

1. Dans le coin supérieur droit de la page **[!UICONTROL Créer une vidéo interactive]**, le nom du paramètre prédéfini de visionneuse actuellement sélectionné utilisé par la vidéo s’affiche. Pour sélectionner un autre paramètre prédéfini de visionneuse, sélectionnez le nom.

   Par exemple, le paramètre prédéfini de visionneuse `Shoppable_Video_light` permet de visionner la vidéo avec une zone d’affichage blanche proche de celle-ci. La zone d’affichage est l’endroit où les miniatures sélectionnables sont affichées pendant la lecture. Le paramètre prédéfini de visionneuse `Shoppable_Video_dark` permet de lire la vidéo avec une zone d’affichage noire proche de celle-ci.

   Si vous avez créé votre propre paramètre prédéfini de visionneuse de vidéos interactives, il est possible également de l’afficher dans la liste de paramètres prédéfinis que vous pouvez sélectionner.

   Lorsque vous avez terminé, sélectionnez **[!UICONTROL Enregistrer]**.

   >[!NOTE]
   >
   >Lorsque vous enregistrez votre vidéo interactive, un fichier `.vtt` associé est automatiquement enregistré avec celle-ci. Le fichier `.vtt` est enregistré dans le dossier `_VTT` situé à la racine des **[!UICONTROL ressources]**. Le fichier et le dossier sont nécessaires pour que la lecture de votre vidéo interactive s’effectue correctement sur votre site web. Ainsi, ne déplacez pas, ne modifiez pas et ne supprimez pas le dossier `_VTT` ni son contenu.

1. Publiez la vidéo interactive. La publication crée le code intégré ou l’URL que vous copiez et appliquez à la fin dans les expériences de votre site web.

   Si vous avez ajouté l’interactivité avec des aperçus rapides, utilisez uniquement le code incorporé ; si vous avez ajouté l’interactivité grâce à des pages web connectées par liens hypertexte, vous pouvez également utiliser l’URL publiée. Notez toutefois que la méthode de liaison basée sur une URL n’est pas possible si votre contenu interactif contient des liens avec des URL relatives, en particulier des liens vers des pages Experience Manager Sites.

   Voir [Publication de ressources](publishing-dynamicmedia-assets.md).

   >[!NOTE]
   >
   >Pour publier une vidéo commerciale avec des aperçus rapides, veillez également à publier séparément chaque ressource d’image liée à la vidéo dans votre espace commercial.

   Une fois les segments de chronologie ajoutés et la vidéo interactive publiée, vous êtes prêt à l’ajouter à la page d’entrée de votre site web existant. Voir [Intégration d’une vidéo interactive à votre site web](#integrating-an-interactive-video-with-your-website).

## Publication de ressources vidéo interactives {#publishing-interactive-video-assets}

Voir [Publication de ressources](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md) pour plus d’informations sur la publication de ressources vidéo interactives.

## Intégration d’une vidéo interactive à votre site web {#integrating-an-interactive-video-with-your-website}

Une fois que vous avez téléchargé une vidéo, que vous lui avez ajouté des segments de chronologie et que vous avez publié la vidéo interactive, vous êtes prêt à l’ajouter à votre site web existant.

Si vous êtes un client Experience Manager Sites, vous pouvez ajouter la vidéo interactive en faisant glisser le composant Interactive Media dans votre page. Voir [Ajout de ressources Dynamic Media aux pages](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).

Si vous êtes un client Experience Manager Assets autonome, vous pouvez ajouter manuellement la vidéo interactive à votre site web, comme indiqué dans cette section.

1. Copiez le code intégré ou l’URL de la vidéo interactive publiée.
Voir [Incorporation de la visionneuse de vidéos ou d’images dans une page web](/help/assets/dynamic-media/embed-code.md).
Si vous avez ajouté l’interactivité avec des aperçus rapides, utilisez uniquement le code incorporé ; si vous avez ajouté l’interactivité grâce à des pages web connectées par liens hypertexte, vous pouvez également utiliser l’URL publiée. Notez toutefois que la méthode de liaison basée sur une URL n’est pas possible si votre contenu interactif contient des liens avec des URL relatives, en particulier des liens vers des pages Experience Manager Sites.

1. Dans le code de la page web cible, identifiez l’emplacement de la vidéo statique.
1. Supprimez la vidéo statique et remplacez le code par celui incorporé ou par l’URL que vous avez copié à partir d’Experience Manager Assets, en l’état.
Le code incorporé copié est défini pour un environnement réactif afin qu’il s’adapte automatiquement à la zone occupée précédemment par la vidéo statique.

>[!NOTE]
>
>À ce stade, si vous avez ajouté l’interactivité avec seulement des pages web connectées par liens hypertexte, votre travail est terminé.
>
>Toutefois, si vous avez ajouté une interactivité pour déclencher un aperçu rapide, les miniatures en regard de la vidéo interactive sont à des fins d’affichage uniquement. ils ne sont pas encore intégrés à vos aperçus rapides existants. Dans ce cas, vous devez intégrer la vidéo interactive à des aperçus rapides existants sur votre site web.

**Exemple**

En vous servant du site web de démonstration comme exemple, procédez comme suit :

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-video/john-lewis/landing-0.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-video/john-lewis/landing-0.html)

Notez que le code intégré vidéo est standard :

```xml
<style type="text/css">
 #s7video_div.s7videoviewer{
   width:100%;
   height:auto;
 }
</style>

<script type="text/javascript" src="https://demos-pub.assetsadobe.com/etc/dam/viewers/s7viewers/html5/js/VideoViewer.js"></script>
<div id="s7video_div"></div>
<script type="text/javascript">
 var s7videoviewer = new s7viewers.VideoViewer({
  "containerId" : "s7video_div",
  "params" : {
   "serverurl" : "https://adobedemo62-h.assetsadobe.com/is/image",
   "contenturl" : "https://demos-pub.assetsadobe.com/",
   "config" : "/etc/dam/presets/viewer/Video",
   "config2": "/etc/dam/presets/analytics",
   "videoserverurl": "https://gateway-na.assetsadobe.com/DMGateway/public/demoCo",
   "posterimage": "/content/dam/marketing/shoppable-video/john-lewis/shoppable-video-john-lewis-2014.mp4",
   "asset" : "/content/dam/marketing/shoppable-video/john-lewis/shoppable-video-john-lewis-2014.mp4" }
 }).init();
</script>
```

L’intégration est aussi simple que la suppression du code intégré de la vidéo et son remplacement par le code intégré de la vidéo interactive à partir d’Experience Manager. Vous pouvez afficher le résultat à l’adresse URL suivante : Même si la page contient une vidéo interactive, celle-ci n’est pas encore intégrée aux aperçus rapides existants :

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-video/john-lewis/landing-1.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-video/john-lewis/landing-1.html)

## Intégration d’une vidéo interactive dans un aperçu rapide existant {#integrating-an-interactive-video-with-an-existing-quickview}

>[!NOTE]
>
>Cette tâche ne s’applique que si vous êtes un client Experience Manager Assets autonome.

La dernière étape de ce processus consiste à intégrer votre vidéo interactive à une mise en oeuvre d’aperçu rapide existante utilisée sur votre site web. Pour ce qui est de l’intégration, il n’existe pas de solution qui fonctionne dans tous les cas. Chaque implémentation d’aperçu rapide est unique. De ce fait, une approche spécifique, impliquant l’aide d’un informaticien compétent en systèmes frontaux, est nécessaire.

L’implémentation d’aperçus rapides existante représente normalement une chaîne d’actions entre-associées qui se produisent sur la page web dans l’ordre suivant :

1. Un utilisateur déclenche un élément dans l’interface utilisateur de votre site web.
1. Le code frontal obtient une URL d’aperçu rapide basée sur l’élément d’interface utilisateur qui a été déclenché à l’étape 1.
1. Le code en front-end envoie une demande Ajax en utilisant l’URL obtenue à l’étape 2.
1. La logique du serveur principal renvoie les données ou le contenu de l’aperçu rapide correspondant au code frontal.
1. Le code frontal charge les données ou le contenu de l’aperçu rapide.
1. Le code frontal convertit éventuellement les données téléchargées de l’aperçu rapide en une représentation HTML.
1. Le code en front-end affiche une boîte de dialogue ou un panneau modal et effectue le rendu du contenu HTML à l’écran pour l’utilisateur final.

Ces appels ne représentent pas des appels d’API publics indépendants qui peuvent être appelés par la logique de page web à partir d’une étape arbitraire. Il s’agit plutôt d’un appel chaîné où chaque étape suivante est masquée dans la dernière phase (rappel) de l’étape précédente.

Au même moment que la vidéo interactive remplace l’étape 1 et partiellement l’étape 2, lorsqu’un utilisateur sélectionne une miniature dans la vidéo interactive, cette interaction utilisateur est gérée par la visionneuse. La visionneuse renvoie un événement à la page web qui contient toutes les données des miniatures ajoutées précédemment dans Experience Manager.

Dans ce type de gestionnaire d’événements, le code en front-end effectue les opérations suivantes :

* Il écoute un événement émis par la vidéo interactive.
* Il crée une URL d’aperçu rapide basée sur les données de la miniature.
* Il déclenche le processus de chargement de l’aperçu rapide depuis le serveur principal et en effectue le rendu à l’écran.

De plus, la visionneuse de vidéos interactives prend en charge le mode de fonctionnement Plein écran. L’utilisateur final déclenche des aperçus rapides en sélectionnant une miniature sans quitter le mode Plein écran. Pour bénéficier de cette fonctionnalité, vous modifiez le code frontal afin que la boîte de dialogue modale d’aperçu rapide soit associée au conteneur de la visionneuse. N’ajoutez pas l’élément BODY du document ni d’autres éléments de page web qui ne sont pas disponibles lorsque la visionneuse est en mode Plein écran. Le code qui exécute cette tâche écoute un autre rappel de visionneuse, envoyé après le chargement de la visionneuse dans la page.

Le code intégré renvoyé par Experience Manager comporte déjà un descripteur d’événement prêt à l’emploi. Il est commenté, comme dans le fragment de code mis en évidence ci-dessous :

```xml
<style type="text/css">
 #s7interactivevideo_div.s7interactivevideoviewer{
   width:100%;
   height:auto;
 }
</style>
<script type="text/javascript" src="https://demos-pub.assetsadobe.com/etc/dam/viewers/s7viewers/html5/js/InteractiveVideoViewer.js"></script>

<div id="s7interactivevideo_div"></div>
<script type="text/javascript">
 var s7interactivevideoviewer = new s7viewers.InteractiveVideoViewer({
  "containerId" : "s7interactivevideo_div",
  "params" : {
   "serverurl" : "https://adobedemo62-h.assetsadobe.com/is/image",
   "contenturl" : "https://demos-pub.assetsadobe.com/",
   "config" : "/etc/dam/presets/viewer/Shoppable_Video_light",
   "config2": "/etc/dam/presets/analytics",
   "videoserverurl": "https://gateway-na.assetsadobe.com/DMGateway/public/demoCo",
   "interactivedata": "content/dam/_VTT/marketing/shoppable-video/john-lewis/shoppable-video-john-lewis-2014.mp4.svideo.vtt",
   "VideoPlayer.contenturl": "https://adobedemo62-h.assetsadobe.com/is/content",
   "asset" : "/content/dam/marketing/shoppable-video/john-lewis/shoppable-video-john-lewis-2014.mp4" }
 })
 /* // Example of interactive video event for quickview.
   s7interactivevideoviewer.setHandlers({
   "quickViewActivate": function(inData) {
     var sku=inData.sku; //SKU for product ID
    //To pass other parameter from the hotspot, you need to add custom parameter during the hotspot setup as parameterName=value
    loadQuickView(sku); //Replace this call with your quickview plugin
    //Please refer to your quickviewer plugin for the quickview call
    },
"initComplete":function() {
    //--- Attach quickview popup to viewer container so popup will work in fullscreen mode ---
    var popup = document.getElementById('quickview_div'); // get custom quickview container
    popup.parentNode.removeChild(popup); // remove it from current DOM
    var sdkContainerId = s7interactivevideoviewer.getComponent("container").getInnerContainerId(); // get viewer container component
    var inner_container = document.getElementById(sdkContainerId);
    inner_container.appendChild(popup); //Attach custom quickview container to viewer
    }
   });
 */
 s7interactivevideoviewer.init();
</script>
```

Il suffit donc de supprimer les commentaires du fragment de code mis en évidence et de remplacer le corps des descripteurs fictifs spécifiques à cette page web.

Le code intégré standard comporte deux gestionnaires de rappel par défaut : `quickViewActivate` et `initComplete`. Le gestionnaire `quickViewActivate` se déclenche lorsqu’une miniature est sélectionnée dans la visionneuse. Utilisez-le pour intégrer la visionneuse à la logique d’activation de l’aperçu rapide. Le gestionnaire `initComplete` ne se déclenche qu’une seule fois lorsque la visionneuse se charge dans la page. Ce descripteur est utilisé pour modifier l’emplacement de la boîte de dialogue d’aperçu rapide dans le modèle objet de document (DOM) de la page web.

La procédure de construction de l’URL de l’aperçu rapide est la procédure inverse de l’identification des variables de vignette, dont nous avons parlé plus tôt dans cette rubrique. En utilisant les exemples d’URL d’aperçu rapide identifiés précédemment, vous pouvez voir comment l’URL d’aperçu rapide est créée dans chaque cas :

<table>
  <tbody>
  <tr>
    <td><p>SKU unique, trouvé dans la chaîne de requête</p> </td>
    <td><code class="code">s7interactivevideoviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/json?productId=" + inData.sku + "&amp;source=100";
      },
      });</code></td>
  </tr>
  <tr>
    <td>SKU unique, trouvé dans le chemin d’accès à l’URL</td>
    <td><code class="code">s7interactivevideoviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/product/" + inData.sku;
      },
      });</code></td>
  </tr>
  <tr>
    <td><p>SKU et ID de catégorie dans la chaîne de requête</p> </td>
    <td><code class="code">s7interactivevideoviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/quickView/product/?category=" + inData.categoryId + "&amp;prodId=" + inData.sku;
      },
      });</code></td>
  </tr>
  </tbody>
</table>

La dernière étape pour déclencher l’URL d’aperçu rapide et activer le panneau d’aperçu rapide nécessite probablement l’assistance d’un informaticien compétent de votre service informatique. Celui-ci sait comment déclencher précisément l’implémentation de l’aperçu rapide à partir de l’étape appropriée, avec une URL d’aperçu rapide prête à l’emploi.

Vous pouvez découvrir comment ces étapes sont appliquées au site web de démonstration pour l’intégration complète d’une vidéo interactive avec le code d’aperçu rapide. Plus tôt dans cette rubrique, la structure de l’URL de l’aperçu rapide a été identifiée comme suit :

```xml
/datafeed/$CategoryId$-$SKU$.json
```

Vous pouvez reconstruire facilement cette URL à l’intérieur du gestionnaire `quickViewActivate` à l’aide des champs `categoryId` et `sku` dans l’objet `inData` transmis au gestionnaire par le code de la visionneuse, comme dans l’exemple suivant :

```xml
var sku=inData.sku;
var categoryId=inData.categoryId;
var quickViewUrl = "datafeed/" + categoryId + "-" + sku + ".json";
```

Le site web de démonstration déclenche la boîte de dialogue d’aperçu rapide si vous utilisez un simple appel de la fonction `loadQuickView()`. Cette fonction n’accepte qu’un seul argument, qui est l’URL des données d’aperçu rapide. La dernière étape nécessaire à l’intégration de la vidéo interactive consiste donc à ajouter la ligne de code ci-dessous au gestionnaire `quickViewActivate` :

```xml
loadQuickView(quickViewUrl);
```

Enfin, veillez à ce que la boîte de dialogue d’aperçu rapide soit associée à l’élément de conteneur de la visionneuse. Le code intégré indique par défaut les exemples d’étapes à suivre pour bénéficier de cette fonctionnalité. Pour obtenir une référence à l’élément de conteneur de la visionneuse, vous pouvez utiliser les lignes de code ci-dessous :

```xml
var sdkContainerId = s7interactivevideoviewer.getComponent("container").getInnerContainerId(); // get viewer container component
var inner_container = document.getElementById(sdkContainerId);
```

Où `inner_container` est une référence à un élément `DIV` géré par la visionneuse. La boîte de dialogue doit être un enfant de l’élément `DIV`.

La procédure de recherche de l’élément de boîte de dialogue modale et d’association au conteneur ci-dessus dépend de chaque cas. Là encore, vous pouvez obtenir de l’aide auprès du développeur frontal, qui connaît votre mise en œuvre de l’aperçu rapide nécessaire.

Pour l’exemple de site web, la boîte de dialogue modale de l’aperçu rapide est mise en oeuvre sous la forme `DIV` avec l’ID quickview-modal associé directement au document `BODY`. Par conséquent, le code utilisé pour déplacer cette boîte de dialogue dans le conteneur de la visionneuse est aussi simple que ce qui suit :

```xml
var sdkContainerId = s7interactivevideoviewer.getComponent("container").getInnerContainerId(); // get viewer container component
var inner_container = document.getElementById(sdkContainerId);
inner_container.appendChild(document.getElementById("quickview-modal"));
```

Le code source complet se présente comme suit :

```xml
<style type="text/css">
 #s7interactivevideo_div.s7interactivevideoviewer{
   width:100%;
   height:auto;
 }
</style>
<script type="text/javascript" src="https://demos-pub.assetsadobe.com/etc/dam/viewers/s7viewers/html5/js/InteractiveVideoViewer.js"></script>

<div id="s7interactivevideo_div"></div>
<script type="text/javascript">
 var s7interactivevideoviewer = new s7viewers.InteractiveVideoViewer({
  "containerId" : "s7interactivevideo_div",
  "params" : {
   "serverurl" : "https://adobedemo62-h.assetsadobe.com/is/image",
   "contenturl" : "https://demos-pub.assetsadobe.com/",
   "config" : "/etc/dam/presets/viewer/Shoppable_Video_light",
   "videoserverurl": "https://gateway-na.assetsadobe.com/DMGateway/public/demoCo",
   "interactivedata": "content/dam/_VTT/marketing/shoppable-video/john-lewis/shoppable-video-john-lewis-2014.mp4.svideo.vtt",
   "VideoPlayer.contenturl": "https://adobedemo62-h.assetsadobe.com/is/content",
   "asset" : "/content/dam/marketing/shoppable-video/john-lewis/shoppable-video-john-lewis-2014.mp4" }
 })
 // Example of interactive video event for quickview.
   s7interactivevideoviewer.setHandlers({
   "quickViewActivate": function(inData) {
     var sku=inData.sku; //SKU for product ID
     var categoryId=inData.categoryId; //categoryId
    var quickViewUrl = "datafeed/" + categoryId + "-" + sku + ".json";
    loadQuickView(quickViewUrl);
    },
   "initComplete":function() {
    //--- Attach quickview popup to viewer container so popup will work in fullscreen mode ---
    var sdkContainerId = s7interactivevideoviewer.getComponent("container").getInnerContainerId(); // get viewer container component
    var inner_container = document.getElementById(sdkContainerId);
    inner_container.appendChild(document.getElementById("quickview-modal"));
    }
   });
 s7interactivevideoviewer.init();
</script>
```

Le dernier site web de démonstration avec la vidéo interactive totalement intégrée se présente comme suit :

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-video/john-lewis/landing-3.html](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-video/john-lewis/landing-3.html)

## Création d’une fenêtre contextuelle personnalisée® à l’aide de l’aperçu rapide {#using-quickviews-to-create-custom-pop-ups}

Voir [Création d’une fenêtre contextuelle personnalisée® à l’aide de l’aperçu rapide](/help/assets/dynamic-media/custom-pop-ups.md).
—>
