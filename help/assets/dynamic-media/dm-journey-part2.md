---
title: parcours Dynamic Media, Partie II
description: 'Le Parcours Dynamic Media couvre les principes de base de Dynamic Media, son fonctionnement, ce qu’il peut vous apporter et la valeur qu’il apporte à votre travail et à vos clients. '
contentOwner: Rick Brough
products: Experience Manager as a Cloud Service
topic-tags: introduction,administering
content-type: reference
feature: Image Profiles
role: User, Admin
mini-toc-levels: 4
hide: false
hidefromtoc: false
source-git-commit: dc290be237c938af59960834b32269a1f6c5bd97
workflow-type: tm+mt
source-wordcount: '2716'
ht-degree: 0%

---


# parcours Dynamic Media : Principes de base, deuxième partie  {#dm-journey-part2}

Bienvenue dans le Parcours Dynamic Media : Principes de base, partie II où vous pouvez vous attendre à apprendre les éléments suivants :

* Anatomie d’une URL Dynamic Media et manière dont Dynamic Media diffuse du contenu
* Principes de base de la création de paramètres d’image prédéfinis pour le rendu des ressources
* Visionneuses d’images, à 360° et de supports variés

Voir aussi [parcours Dynamic Media ; Principes de base, première partie](/help/assets/dynamic-media/dm-journey-part1.md).

## Anatomie d’une URL Dynamic Media et manière dont Dynamic Media diffuse du contenu {#dm-journey-d}

Une fois vos ressources Dynamic Media chargées et publiées, vous pouvez copier l’URL générée d’une ressource et la coller dans votre navigateur pour voir comment la ressource apparaîtra pour un client. L’URL copiée suivante pour une image de montre est ventilée par couleur afin de faciliter la lecture et la compréhension.

![Anatomie d’une URL Dynamic Media](/help/assets/dynamic-media/assets/dm-colored-url.png)
*Anatomie d’une URL Dynamic Media.*

La première partie de l’URL en rouge fait référence au domaine du serveur lui-même. Dans ce cas, Dynamic Media s’exécute sur un domaine de serveur générique : `https://s7d1.scene7.com/is/image/`. Il est facile de regarder un ensemble d’images et de comprendre si elles sont diffusées par Dynamic Media uniquement en observant le domaine du serveur. L&#39;URL va être assez cohérente. Certains clients Dynamic Media ont toutefois basculé vers un domaine de serveur dédié où il peut être `name-of-your-company.scene7.com`. Un domaine de serveur dédié est requis pour l’imagerie dynamique.

Le nom du compte est la partie violette. Dans ce cas, le compte est appelé `jpearldemo`.

L’identifiant ou le nom de la ressource, `AdobeStock_28563982` est en vert. Notez que la ressource possède *non* extension de fichier, par exemple `.png` ou `.jpg`. Lorsque des ressources sont ingérées dans Dynamic Media, l’extension de fichier est supprimée et un autre type de fichier est créé : un fichier pyramid-TIFF. Le TIFF pyramique permet à Dynamic Media de créer rapidement des rendus à la volée.

Enfin, il existe des paramètres de traitement des images, `?wid=1000&fmt=jpeg&qlt=85`, indiqué en jaune à la fin.

L’intégralité du chemin de l’URL est actif. [Essayez](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock_28563982?wid=1000&amp;fmt=jpeg&amp;qlt=85).
La fenêtre de votre navigateur reste ouverte sur l’URL Dynamic Media et l’image de surveillance. Regardons de plus près comment créer des rendus de l’image en modifiant simplement l’URL.

### Rendu de l’image de montre via l’URL

Supprimez d’abord manuellement uniquement les règles de traitement des images dans le chemin de l’URL ; laissez le nom du serveur, le nom du compte et l’identifiant de ressource ou le nom de l’image. [Essayez](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock_28563982)

Ajoutez maintenant un paramètre de traitement d’image à la fin de l’URL. Dans le champ URL, à droite du nom de l’image, saisissez `?wid=500`, puis appuyez sur **[!UICONTROL Entrée]**. [Essayez](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock%5F28563982?wid=500).

Notez qu’un nouveau rendu de la montre est généré. Il est essentiel de comprendre, à partir de cet exercice simple de modification de la largeur de l’image, que l’image vue est générée de manière dynamique à 100 %.

Maintenant, modifiez la valeur de largeur de `500` pixel vers `1000` pixels, puis appuyez sur **[!UICONTROL Entrée]**. [Essayez](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock%5F28563982?wid=1000).
Dès que vous appuyez **[!UICONTROL Entrée]**, le navigateur revient au serveur d’images Dynamic Media. Il génère un nouveau rendu de la montre, en fonction de la nouvelle valeur de largeur que vous venez de saisir, puis renvoie la nouvelle image au navigateur et la met en cache.

Dynamic Media propose de nombreux paramètres de traitement des images que vous pouvez utiliser pour affiner vos ressources d’image sur les pages web. Vous pouvez [voir une liste d&#39;entre eux ici](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html?lang=en).

Essayez maintenant d’ajouter un paramètre de rotation à l’image de montre. Et la fin du chemin de l’URL, qui suit immédiatement `wid=1000`, type `&rotate=90`, puis appuyez sur **[!UICONTROL Entrée]**. [Essayez](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock%5F28563982?wid=1000&amp;rotate=90).

La montre est encore légèrement biaisée à gauche. Modifier la valeur de rotation de `90` to `92`, puis appuyez sur **[!UICONTROL Entrée]**. [Essayez](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock%5F28563982?wid=1000&amp;rotate=9)

Encore une fois, au moment où vous appuyez **[!UICONTROL Entrée]**, un nouveau rendu de la montre est généré presque instantanément. Vous pouvez voir le type de performances que vous obtenez, ce qui explique pourquoi Dynamic Media peut envoyer plus de 800 000 demandes d’image, *par seconde*, lors d’un week-end chargé ou d’un jour férié majeur.

Bien qu’il soit possible de modifier les paramètres de traitement des images dans une URL image par image, cette méthode n’est pas efficace, en particulier si vous avez des dizaines de milliers d’images qui constituent votre site web. Une meilleure approche consiste à utiliser des paramètres d’image prédéfinis.

## Principes de base de la création de paramètres d’image prédéfinis pour le rendu des ressources {#dm-journey-e}

Il existe plusieurs façons et emplacements où vous souhaitez créer une image ou rendre disponible une image. Traditionnellement, un créatif accède à Adobe Photoshop et enregistre chacun de ces différents rendus sous forme d’images statiques.

![Images statiques](/help/assets/dynamic-media/assets/dm-static-images.png)
*Bon : images statiques, chacune créée manuellement.*

Maintenant imaginez que Creative Director regarde les images et dit : *&quot;Je voulais vraiment que cette photo montre la grande main pointant vers le quatre, et la petite main pointant vers le 1 pour faciliter la vue.&quot;*

Le créatif devra redémarrer toutes ces nouvelles images statiques.

Toutefois, avec Dynamic Media, si vous disposez de paramètres d’image prédéfinis différents, vous pouvez utiliser ces images où vous en avez besoin. Les paramètres d’image prédéfinis appliquent les normes.

![Approche Principale des fichiers](/help/assets/dynamic-media/assets/dm-onefile.png)
*Meilleur : un fichier avec plusieurs rendus créés à la volée à l’aide de paramètres d’image prédéfinis, tels que `Search_Grid` et `Thumbnail`.*

| **Pourquoi utiliser les paramètres d’image prédéfinis ?** |  |
|---|---|
| Normes | Les paramètres d’image prédéfinis imposent un traitement de traitement d’image standard sur toutes les images demandées. |
| Gestion des modifications | Si vous devez modifier le traitement des images, vous devez simplement modifier le paramètre du paramètre d’image prédéfini existant. La définition mise à jour est automatiquement propagée à toutes les requêtes. |

Chaque emplacement dont vous avez besoin pour un type d’image particulier, par exemple :

* une page des détails du produit,
* grille de recherche,
* thumbnail,
* carte d’achat ou
* image hero

Vous souhaitez que cette image soit diffusée avec les mêmes paramètres partout où elle sera utilisée.

Pendant un instant, regardons comment un paramètre d’image prédéfini est créé dans Dynamic Media.

![Création d’un paramètre d’image prédéfini à partir de l’onglet De base](/help/assets/dynamic-media/assets/dm-image-preset-basictab.png)
*Création d’un paramètre d’image prédéfini à partir de l’onglet De base.*

Dans l’exemple ci-dessus, vous pouvez constater qu’un nouveau paramètre d’image prédéfini a été créé avec le nom . *Volume moyen*. Dynamic Media utilise un exemple d’image d’usine, le sac à dos, pour vous aider à voir les caractéristiques du paramètre d’image prédéfini au fur et à mesure de sa création.

Le *Volume moyen* la largeur du paramètre d’image prédéfini est de 500 pixels et sa hauteur est de 800 pixels. Dans la partie I de ce Parcours, vous lisez comment diffuser des ressources dans différents formats. Dans la **[!UICONTROL Format]** dans le menu déroulant, vous pouvez choisir de diffuser des ressources sous la forme de JPEG, PNG, TIFF ou de plusieurs autres formats. Vous avez de la flexibilité ici.

En sélectionnant le **[!UICONTROL Avancé]** vous donne les options relatives à l’espace colorimétrique de la ressource. Selon le format que vous avez sélectionné dans la variable **[!UICONTROL De base]** onglet : dans l’exemple ci-dessus, JPEG a été sélectionné. Vous pouvez diffuser des ressources en RGB, niveaux de gris ou CMJN. Dans la **[!UICONTROL Profil colorimétrique]** dans le menu déroulant, vous pouvez sélectionner comment diffuser une ressource image CMJN à utiliser pour l’impression. Notez également que vous pouvez appliquer d’autres paramètres pour accentuer vos images. Dans ce cas, **[!UICONTROL Accentuation]** a été appliquée.

![Création d’un paramètre d’image prédéfini en sélectionnant des options dans l’onglet Avancé](/help/assets/dynamic-media/assets/dm-image-preset-advancedtab.png)
*Pour créer un paramètre d’image prédéfini, sélectionnez des options dans l’onglet Avancé .*

Vous vous rappelez dans [Anatomie d’une URL Dynamic Media](#dm-journey-d) plus tôt, vous avez lu des informations sur l’URL Dynamic Media et la manière dont elle est créée. Le **[!UICONTROL Modificateur d’image]** vous pouvez saisir les paramètres de traitement d’image supplémentaires de votre choix dans la zone de texte. Les paramètres sont inclus dans le nom du paramètre prédéfini de l’URL lors de la diffusion de vos images, à l’aide du paramètre prédéfini . Dans la capture d’écran ci-dessus, le paramètre `bgc=451B15` a été ajouté. C&#39;est-à-dire qu&#39;une couleur de fond marron foncé a été ajoutée.

Vous pouvez considérer un paramètre d’image prédéfini comme une recette pour vos images. Il fournira toutes les images qui utilisent le paramètre prédéfini de manière cohérente à chaque fois ; ce sera la même chose. Le paramètre `&op_brightness=+10` a également été ajouté pour augmenter légèrement la luminosité.

Lorsque vous avez terminé, vous enregistrez le paramètre prédéfini, qui est désormais disponible pour toutes les images que vous avez. Dans ce cas, nous souhaitons appliquer la variable *Volume moyen* image prédéfinie en image d&#39;un bol de chocolat liquide.

![Application du paramètre d’image prédéfini *Volume moyen* pour générer un rendu d’image](/help/assets/dynamic-media/assets/dm-medium-image-preset.png)
*Application du paramètre d’image prédéfini* Volume moyen *pour générer un rendu d’image.*

Vous copiez l’URL, puis collez-la dans votre navigateur pour vérifier l’aspect de l’image. [Essayez](http://s7d1.scene7.com/is/image/jpearldemo/AdobeStock_74043302?$Medium$). Dans votre navigateur, notez le nom du paramètre d’image prédéfini. *Volume moyen* dans le chemin d’accès URL complet.

Vous pouvez voir le type de clarté affiché dans l’image. Cette qualité est en partie due à la façon dont le bol de chocolat a été tiré. En outre, c’est en partie parce qu’avec Dynamic Media, vous pouvez stocker des images plus grandes que celles diffusées aux canaux numériques.

Si tout semble satisfaisant pour votre bol de chocolat, vous collez l’URL dans vos pages web où vous souhaitez que l’image apparaisse sur votre site web.

Si vous regardez à nouveau l’image de la montre ci-dessous, vous pouvez voir qu’il existe une `Cart` paramètre d’image prédéfini, un `Grid` preset, un `Large` preset, un `PDP-page` (Page Détails du produit) prédéfinie, et plusieurs autres.

![Paramètres prédéfinis d’image statiques et dynamiques](/help/assets/dynamic-media/assets/dm-image-presets.png)
*Paramètres d’image prédéfinis statiques et dynamiques. L’image de la montre a été rendue à l’aide de la fonction `PDP-page` paramètre d’image prédéfini.*

Mais qu&#39;en est-il si vous devez changer une image sur votre site web ? Supposons, par exemple, que vous ayez effectué quelques tests et que vous ayez trouvé que l’image de 120 x 120 (la variable `Cart` paramètre d’image prédéfini) n’est pas reçu aussi bien que vous le pensiez. Vous devez agrandir l’image en augmentant la largeur à 175 pixels et la hauteur à 175 pixels. Traditionnellement, vous devez aller dans Adobe Photoshop et recréer toutes ces images de panier. Toutefois, avec Dynamic Media, il vous suffit de modifier le paramètre d’image prédéfini en mettant à jour les valeurs Largeur et Hauteur à 175 et d’enregistrer votre paramètre prédéfini, comme illustré dans l’exemple ci-dessous.

![Modification d’un paramètre d’image prédéfini](/help/assets/dynamic-media/assets/dm-edit-image-preset.png)
*Modification de la largeur et de la hauteur de `Cart` paramètre d’image prédéfini.*

Après avoir modifié votre paramètre d’image prédéfini et vidé le cache, toutes les images sont mises à jour et toutes les URL utilisées avec ce paramètre prédéfini, procédez comme suit : *not* changez n’importe où. Cela signifie qu’aucun lien n’est rompu et qu’aucune redirection de page web n’est nécessaire.

## Visionneuses d’images, à 360° et de supports variés {#dm-journey-f}

Certaines des utilisations les plus courantes de Dynamic Media sont la possibilité de créer des visionneuses d’images, à 360° et de supports variés.

Les visionneuses d’images sont généralement composées d’une série de ressources d’image présentées comme une seule entité. Ces types de visionneuses offrent aux utilisateurs une expérience de visionnage intégrée, dans laquelle ils peuvent visualiser différentes vues d’un élément en cliquant sur une miniature. Les visionneuses d’images vous permettent de présenter d’autres vues d’un élément et la visionneuse propose des outils de zoom pour examiner les images de plus près. [Afficher une visionneuse d’images appelée &quot;En cours d’exécution&quot; qui utilise la visionneuse déroulante](https://s7d1.scene7.com/s7viewers/html5/FlyoutViewer.html?asset=jpearldemo/Running).

Ici à l&#39;intérieur de Dynamic Media, vous pouvez voir plusieurs images de chaussures de course. Il s’agit d’une série de produits que les ventes et le marketing veulent que les clients considèrent comme une seule présentation ; une visionneuse d’images.

![Création d’une visionneuse d’images](/help/assets/dynamic-media/assets/dm-create-image-set.png)
*Démarrage de la création d’une visionneuse d’images.*

Pour créer la visionneuse d’images, choisissez **[!UICONTROL Visionneuse d’images]** de la **[!UICONTROL Créer]** menu déroulant. Notez que le menu contient également des options pour créer une **[!UICONTROL Visionneuse de médias mixtes]**, un **[!UICONTROL Visionneuse à 360°]**, et a **[!UICONTROL Ensemble de carrousel]**. Vous créez ces visionneuses de la même manière qu’une visionneuse d’images.

Une visionneuse de médias mixtes peut contenir des images, des visionneuses d’échantillons, des visionneuses à 360°, des vidéos et des visionneuses de vidéos adaptatives. [Essayez](https://s7d9.scene7.com/s7viewers/html5/MixedMediaViewer.html?asset=Scene7SharedAssets/Mixed_Media_Set_Sample). Une visionneuse à 360° simule l’action réelle consistant à tourner un objet pour l’examiner. Les visionneuses à 360° permettent d’afficher des détails visuels clés sous n’importe quel angle. [Essayez](https://s7d9.scene7.com/s7viewers/html5/SpinViewer.html?asset=Scene7SharedAssets/SpinSet_Sample&amp;stagesize=500,400).

La création d’une visionneuse d’images est simple. Il vous suffit d’ajouter les ressources d’image que vous souhaitez inclure dans la visionneuse.

![Création d’une visionneuse d’images](/help/assets/dynamic-media/assets/dm-create-image-set-add-assets.png)
*L’éditeur de visionneuse d’images vous permet d’ajouter des ressources d’image et de réorganiser leur aspect dans la visionneuse.*

Vous devez donner un nom à la visionneuse. Choisissez le nom avec soin car vous ne pourrez pas le modifier plus tard ! Dans l’exemple ci-dessus, la visionneuse est appelée `Running`. Lorsque vous avez terminé, vous enregistrez la visionneuse.

Et voici le `Running` Visionneuse d’images dans Experience Manager Assets.

![L’ensemble d’images en cours d’exécution dans Experience Manager Assets, mode Carte](/help/assets/dynamic-media/assets/dm-image-set.png)
*Le `Running` Visionneuse d’images dans Experience Manager Assets en mode Carte.*

Après avoir créé une visionneuse d’images, de supports variés, de visionneuse à 360° ou tout autre média interactif, vous souhaitez voir comment elle s’affiche et se comporte pour un client. Dynamic Media dispose de nombreuses visionneuses intégrées qui vous permettent de le faire.

Vous commencez par sélectionner la visionneuse d’images créée pour l’ouvrir dans un aperçu comme illustré dans l’exemple suivant.

![La visionneuse d’images en cours d’exécution dans l’aperçu avec l’option Visionneuses sélectionnée](/help/assets/dynamic-media/assets/dm-image-set-viewer.png)
*Le `Running` L’option Visionneuse d’images dans l’aperçu avec visionneuses est sélectionnée.*

Dans l’aperçu, vous pouvez sélectionner les échantillons de chaussures de course et effectuer un zoom avant ou arrière sur les chaussures. Pour appliquer une visionneuse à la visionneuse, sélectionnez **[!UICONTROL Visionneuses]** dans le menu déroulant.

![La visionneuse d’images en cours d’exécution avec la visionneuse déroulante qui lui est appliquée](/help/assets/dynamic-media/assets/dm-image-set-flyout-viewer.png)
*Le `Running` Visionneuse d’images à l’aide de la visionneuse déroulante qui lui est appliquée.*

Dans ce cas, la variable `Flyout` la visionneuse a été sélectionnée. À ce stade, vous pouvez prévisualiser la visionneuse d’images dans la visionneuse. Mais il est préférable de le voir dans votre navigateur, juste comme le voit un client. Vous pouvez sélectionner **[!UICONTROL URL]** dans le coin inférieur gauche, copiez l’URL et collez-la dans votre navigateur. [Essayez](https://s7d1.scene7.com/s7viewers/html5/FlyoutViewer.html?asset=jpearldemo/Running&amp;config=jpearldemo/Flyout).

L’URL unique vous permet d’utiliser la visionneuse d’images et la visionneuse à l’endroit où vous en avez besoin sur votre site web. Vous avez peut-être remarqué dans l’exemple précédent que : **[!UICONTROL Incorporer]** se trouve à droite du bouton URL. En sélectionnant **[!UICONTROL Incorporer]**, vous pouvez copier le code de cette visionneuse/visionneuse d’images et l’ajouter à une page web ou à un composant Experience Manager Sites.

La visionneuse déroulante est une visionneuse prête à l’emploi par défaut dont vous pouvez modifier les propriétés. Ou, tout comme vous créez un paramètre d’image prédéfini, vous pouvez créer votre propre visionneuse personnalisée.

Maintenant, supposons que votre équipe de vente et de marketing n&#39;aime pas la visionneuse déroulante. Ils aiment la fonction de zoom, mais souhaitent que les clients voient l’effet de zoom directement sur les chaussures. Dans ce cas, il vous suffit d’appliquer la visionneuse InlineZoom à la visionneuse d’images, puis de copier et coller son URL dans votre navigateur pour voir comment elle se comporte. [Essayez](https://s7d1.scene7.com/s7viewers/html5/FlyoutViewer.html?asset=jpearldemo/Running&amp;config=jpearldemo/InlineZoom).

Lorsque vous déplacez le pointeur de la souris sur la chaussure, vous effectuez un zoom avant sur cette image, et vous pouvez voir plus de détails lorsque vous déplacez le pointeur. Et la raison en est simplement la taille de l&#39;image qui a été initialement téléchargée dans Dynamic Media.

Quand vous envisagez de vivre en tant que consommateur, ou quand vous travaillez dans votre rôle quotidien, et quand vous allez sur différents sites web, vous voyez des choses comme ça. Pensez à la façon dont cela est fait, et comment utiliser la puissance de Dynamic Media dans votre propre travail et sur le site web de votre entreprise.

Vous lisez un peu sur les visionneuses d’images et les visionneuses. Regardons deux autres visionneuses et essayons-les sur des ressources uniques. Pour réinitialiser la visionneuse, cliquez sur le bouton **[!UICONTROL Actualiser]** dans le coin inférieur gauche.

<!-- LEAVE THIS HIDDEN PATH IN THE DOCUMENTATION FOR DEMO PURPOSES [Flyout viewer with image set](http://www.partycity.com/girls-little-old-lady-costume-P750948.html) -->

* `ZoomVertical_dark` visionneuse appliquée à une ressource image. [Essayez](https://s7d1.scene7.com/s7viewers/html5/ZoomVerticalViewer.html?asset=jpearldemo/AdobeStock_96311480&amp;config=jpearldemo/ZoomVertical_dark).
* `Zoom_light` visionneuse appliquée à une image. [Essayez](https://s7d1.scene7.com/s7viewers/html5/BasicZoomViewer.html?asset=jpearldemo/AdobeStock_38827423&amp;config=jpearldemo/Zoom_light).





