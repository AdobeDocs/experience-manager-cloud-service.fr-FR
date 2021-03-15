---
title: Utilisation de vues rapides pour créer des fenêtres contextuelles personnalisées
description: La vue rapide par défaut est utilisée dans les expériences de commerce électronique où une fenêtre contextuelle s’affiche avec les informations sur le produit pour générer un achat. Vous pouvez déclencher le contenu personnalisé à afficher dans les fenêtres contextuelles.
translation-type: tm+mt
source-git-commit: ad626d9722f1942249197d96aa5fac3d8f7ed947
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 45%

---


# Utilisation de vues rapides pour créer des fenêtres contextuelles personnalisées {#using-quickviews-to-create-custom-pop-ups}

La vue rapide par défaut est utilisée dans les expériences de commerce électronique où une fenêtre contextuelle s’affiche avec les informations sur le produit pour générer un achat. Cependant, vous pouvez déclencher le contenu personnalisé à afficher dans les fenêtres contextuelles. En fonction de la visionneuse que vous utilisez, les clients peuvent appuyer sur une zone réactive, une image miniature ou une zone cliquable pour afficher des informations ou du contenu associé.

Les vues rapides sont prises en charge par les lecteurs suivants dans Dynamic Media :

* Images interactives (zones réactives cliquables)
* Vidéo interactive (miniatures cliquables pendant la lecture vidéo)
* Bannières carrousel (zones réactives cliquables ou zones cliquables)

Bien que les fonctionnalités de chaque lecteur diffèrent, le processus de création d’une vue rapide est le même pour les trois lecteurs pris en charge.

**Pour utiliser des vues rapides pour créer des fenêtres contextuelles personnalisées**

1. Créez une vue rapide pour un fichier téléchargé.

   En règle générale, vous créez une vue rapide lorsque vous modifiez un fichier en vue de l’utiliser avec la visionneuse que vous utilisez.

   <table>
    <tbody>
    <tr>
    <td><strong>Visionneuse utilisée</strong></td>
    <td><strong>Pour créer la vue rapide, procédez comme suit :</strong></td>
    </tr>
    <tr>
    <td>Images interactives</td>
    <td><a href="/help/assets/dynamic-media/interactive-images.md#adding-hotspots-to-an-image-banner" target="_blank">Ajout de zones réactives à une bannière d’image</a>.</td>
    </tr>
    <tr>
    <td>Vidéos interactives</td>
    <td><a href="/help/assets/dynamic-media/interactive-videos.md#adding-interactivity-to-your-video" target="_blank">Ajout d’interactivité à votre vidéo</a>.</td>
    </tr>
    <tr>
    <td>Bannières de carrousel</td>
    <td><a href="/help/assets/dynamic-media/carousel-banners.md#adding-hotspots-or-image-maps-to-an-image-banner" target="_blank">Ajout de zones réactives ou de zones cliquables à une bannière</a>.<br /> </td>
    </tr>
    </tbody>
   </table>

1. Obtenez le code d’intégration de visionneuse afin d’intégrer la visionneuse à votre site web.

   <table>
    <tbody>
    <tr>
    <td><strong>Visionneuse utilisée</strong><br /> </td>
    <td><strong>Pour intégrer la visionneuse à votre site Web, procédez comme suit :</strong></td>
    </tr>
    <tr>
    <td>Image interactive</td>
    <td><a href="/help/assets/dynamic-media/interactive-images.md#integrating-an-interactive-image-with-your-website" target="_blank">Intégration d’une image interactive à votre site web</a>.<br /> </td>
    </tr>
    <tr>
    <td>Vidéo interactive<br /> </td>
    <td><a href="/help/assets/dynamic-media/interactive-videos.md#integrating-an-interactive-video-with-your-website" target="_blank">Intégration d’une vidéo interactive à votre site web</a>.<br /> </td>
    </tr>
    <tr>
    <td>Bannière de carrousel</td>
    <td><a href="/help/assets/dynamic-media/carousel-banners.md#adding-a-carousel-banner-to-your-website-page" target="_blank">Ajout d’une bannière de carrousel à votre page web</a>.<br /> </td>
    </tr>
    </tbody>
   </table>

1. La visionneuse que vous utilisez doit savoir comment utiliser la vue rapide.

   Le lecteur utilise un gestionnaire appelé `QuickViewActive`.

   **Exemple** Supposons que vous utilisiez le code d’intégration suivant dans votre page web pour une image interactive :

   ![chlimage_1-291](assets/chlimage_1-291.png)

   Le gestionnaire est chargé dans la visionneuse à l’aide de `setHandlers` :

   `*viewerInstance*.setHandlers({ *handler 1*, *handler 2*}, ...`

   **A l’aide de l’exemple de code incorporé ci-dessus, vous disposez du code suivant :**

   ```xml
   s7interactiveimageviewer.setHandlers({
       quickViewActivate": function(inData) {
           var sku=inData.sku;
           var genericVariable1=inData.genericVariable1;
           var genericVariable2=inData.genericVariable2;
          loadQuickView(sku,genericVariable1,genericVariable2);
       }
   })
   ```

   Pour en savoir plus sur la méthode `setHandlers()`, rendez-vous sur la page suivante :

   * Visionneuse d’images interactive : [sethandlers](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/jsapi-interactive-image/r-html5-aem-int-image-viewer-javascriptapiref-sethandlers.html?lang=fr)
   * Visionneuse de vidéos interactive : [sethandlers](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/jsapi-interactive-video/r-html5-aem-int-video-javascriptapiref-sethandlers.html?lang=fr)

1. Configurez maintenant le gestionnaire `quickViewActivate`.

   Le gestionnaire `quickViewActivate` contrôle les vues rapides dans le lecteur. Le gestionnaire contient la liste de variable et les appels de fonction à utiliser avec la vue rapide. Le code incorporé fournit le mappage pour le jeu de variables SKU dans la vue rapide. Il effectue également un exemple d&#39;appel de fonction `loadQuickView`.

   **Variables**
mappingMap à utiliser dans votre page Web pour la valeur SKU et les variables génériques contenues dans la vue rapide :

   `var *variable1*= inData.*quickviewVariable*`

   Le code d’intégration fourni comporte un exemple de mise en correspondance pour la variable SKU :

   `var sku=inData.sku`

   Faites également correspondre d’autres variables de la vue rapide, comme dans l’exemple suivant :

   ```
   var <i>variable2</i>= inData.<i>quickviewVariable2</i>
    var <i>variable3</i>= inData.<i>quickviewVariable3</i>
   ```

   **Fonction**
callLe gestionnaire nécessite également un appel de fonction pour que la vue rapide fonctionne. La fonction est supposée être accessible par votre page hôte. Le code d’intégration fournit un exemple d’appel de fonction :

   `loadQuickView(sku)`

   L’exemple d’appel de fonction suppose que la fonction `loadQuickView()` existe et qu’elle est accessible.

   Pour en savoir plus sur la méthode `quickViewActivate`, rendez-vous sur la page suivante :

   * Visionneuse d’images interactive – [Rappels d’événement](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-event-callbacks.html?lang=fr)
   * Visionneuse de vidéos interactive – [Rappels d’événement](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video-event-callbacks.html?lang=fr)
   * Prise en charge de données interactives dans la visionneuse de vidéos interactive – [Prise en charge de données interactives](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video-int-data-support.html?lang=fr)

1. Procédez comme suit :

   * Décommentez la section setHandlers du code d’intégration.
   * Faites correspondre les variables supplémentaires contenues dans la vue rapide.

      * Mettez à jour l&#39;appel `loadQuickView(sku,*var1*,*var2*)` si vous ajoutez d&#39;autres variables.
   * Créez une fonction `loadQuickView` () simple sur la page, à l’extérieur de la visionneuse.

      Par exemple, les éléments suivants écrivent la valeur du SKU dans la console du navigateur :

   ```xml
   function loadQuickView(sku){
       console.log ("quickview sku value is " + sku);
   }
   ```

   * Chargez une page HTML de test sur un serveur web et ouvrez-la.

      Les variables de la vue rapide sont mises en correspondance. L&#39;appel de fonction est en place. Et la console du navigateur écrit la valeur de la variable dans la console du navigateur. Il effectue cette opération à l’aide de la fonction d’exemple fournie.



1. Vous pouvez désormais utiliser une fonction pour appeler une fenêtre contextuelle simple dans la vue rapide. L’exemple suivant utilise une balise `DIV` pour une fenêtre contextuelle.
1. Mettez en forme la balise `DIV` de la fenêtre contextuelle comme suit. Ajoutez un style supplémentaire selon vos besoins.

   ```xml
   <style type="text/css">
       #quickview_div{
           position: absolute;
           z-index: 99999999;
           display: none;
       }
   </style>
   ```

1. Placez la balise `DIV` de la fenêtre contextuelle dans le corps de la page HTML.

   L’un des éléments est défini avec un identifiant mis à jour avec la valeur SKU lorsque l’utilisateur appelle une vue rapide. L’exemple comprend également un bouton unique pour masquer à nouveau la fenêtre contextuelle une fois qu’elle devient visible.

   ```xml
   <div id="quickview_div" >
       <table>
           <tr><td><input id="btnClosePopup" type="button" value="Close"        onclick='document.getElementById("quickview_div").style.display="none"' /><br /></td></tr>
           <tr><td>SKU</td><td><input type="text" id="txtSku" name="txtSku"></td></tr>
       </table>
   </div>
   ```

1. Pour mettre à jour la valeur SKU dans la fenêtre contextuelle, ajoutez une fonction. Rendez la fenêtre contextuelle visible en remplaçant la fonction simple créée à l’étape 5 par ce qui suit :

   ```xml
   <script type="text/javascript">
       function loadQuickView(sku){
           document.getElementById("txtSku").setAttribute("value",sku); // write sku value
           document.getElementById("quickview_div").style.display="block"; // show popup
       }
   </script>
   ```

1. Téléchargez une page HTML de test sur votre serveur web et ouvrez-la. Le lecteur affiche la fenêtre contextuelle `DIV` lorsqu’un utilisateur appelle une vue rapide.
1. **Affichage de la fenêtre contextuelle personnalisée en mode plein écran**

   Certaines visionneuses, comme la visionneuse de vidéos interactives, prennent en charge l’affichage en mode plein écran. Toutefois, l’utilisation de la fenêtre contextuelle comme décrit dans les étapes précédentes provoque l’affichage de celle-ci derrière la visionneuse en mode plein écran.

   Pour afficher la fenêtre contextuelle en mode standard et plein écran, joignez-la au conteneur de la visionneuse. Dans ce cas, utilisez une deuxième méthode de gestionnaire, `initComplete`.

   Le gestionnaire `initComplete` est appelé une fois la visionneuse initialisée.

   ```xml
   "initComplete":function() { code block }
   ```

   Pour en savoir plus sur la méthode `init()`, rendez-vous sur la page suivante :

   * Visionneuse d’image interactive – [init](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/jsapi-interactive-image/r-html5-aem-int-image-viewer-javascriptapiref-init.html?lang=fr)
   * Visionneuse de vidéo interactive – [init](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/jsapi-interactive-video/r-html5-aem-int-video-javascriptapiref-init.html?lang=fr)

1. Pour associer la fenêtre contextuelle (décrite dans les étapes précédentes) à la visionneuse, utilisez le code suivant :

   ```xml
   "initComplete":function() {
       var popup = document.getElementById('quickview_div');
       popup.parentNode.removeChild(popup);
       var sdkContainerId = s7interactivevideoviewer.getComponent("container").getInnerContainerId();
       var inner_container = document.getElementById(sdkContainerId);
       inner_container.appendChild(popup);
   }
   ```

   Dans le code ci-dessus, vous avez effectué les opérations suivantes :

   * Identification de la fenêtre contextuelle personnalisée.
   * Suppression de celle-ci du DOM.
   * Identification du conteneur de la visionneuse.
   * Association de la fenêtre contextuelle au conteneur de la visionneuse.

1. L’intégralité du code setHandlers est similaire à ce qui suit (la visionneuse de vidéos interactives a été utilisée) :

   ```xml
   s7interactivevideoviewer.setHandlers({
       "quickViewActivate": function(inData) {
           var sku=inData.sku;
           loadQuickView(sku);
   
       },
       "initComplete":function() {
           var popup = document.getElementById('quickview_div'); // get custom quick view container
           popup.parentNode.removeChild(popup); // remove it from current DOM
           var sdkContainerId = s7interactivevideoviewer.getComponent("container").getInnerContainerId();
           var inner_container = document.getElementById(sdkContainerId);
           inner_container.appendChild(popup);
       }
   });
   ```

1. Une fois les gestionnaires chargés, vous initialisez la visionneuse :

   `*viewerInstance.*init()`

   **Exemple** Cet exemple utilise la visionneuse d’images interactives.

   `s7interactiveimageviewer.init()`

   Après avoir incorporé la visionneuse dans votre page hôte, assurez-vous que l’instance de visionneuse est créée. Veillez également à ce que les gestionnaires soient chargés avant l’appel de la visionneuse à l’aide de `init()`.

