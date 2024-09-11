---
title: Parcours dans Dynamic Media, partie II
description: Le Parcours Dynamic Media couvre les principes de base de Dynamic Media, son fonctionnement, ce qu’il peut vous apporter et la valeur qu’il représente pour votre travail et vos clients.
contentOwner: Rick Brough
products: Experience Manager as a Cloud Service
topic-tags: introduction,administering
content-type: reference
feature: Image Profiles,Best Practices
role: User, Admin
mini-toc-levels: 4
hide: false
hidefromtoc: false
exl-id: cdca41ad-a2cd-4f68-aaa4-5eec33c30f0b
source-git-commit: d16a2dbe5cf2ab6d42af661b6ab2b9845612304f
workflow-type: tm+mt
source-wordcount: '2621'
ht-degree: 97%

---

# Parcours Dynamic Media : principes de base, deuxième partie  {#dm-journey-part2}

{{see-also-dm}}

Bienvenue dans le Parcours Dynamic Media : principes de base, deuxième partie, au cours duquel vous devriez vous familiariser avec les éléments suivants :

* L’anatomie d’une URL Dynamic Media et la manière dont Dynamic Media diffuse du contenu
* Les principes de base de la création de paramètres d’image prédéfinis pour le rendu des ressources
* Les visionneuses d’images, visionneuses à 360° et visionneuses de supports variés

Consultez également le [Parcours Dynamic Media ; principes de base, première partie](/help/assets/dynamic-media/dm-journey-part1.md).

>[!TIP]
>
>Pour de meilleurs résultats, Adobe vous recommande de lire et d’afficher ce Parcours Dynamic Media sur un ordinateur de bureau.

## Anatomie d’une URL Dynamic Media et méthode de Dynamic Media pour diffuser du contenu {#dm-journey-d}

Une fois vos ressources Dynamic Media chargées et publiées, vous pouvez copier l’URL générée d’une ressource et la coller dans votre navigateur pour voir comment elle apparaîtra pour un client. L’URL copiée suivante d’une image de montre est découpée par couleur afin de faciliter la lecture et la compréhension.

![Anatomie d’une URL Dynamic Media](/help/assets/dynamic-media/assets/dm-colored-url.png)
_Anatomie d’une URL Dynamic Media_

La première partie de l’URL, en rouge, fait référence au domaine du serveur lui-même. Dans ce cas, Dynamic Media s’exécute sur un domaine de serveur générique : `https://s7d1.scene7.com/is/image/`. Il est facile de regarder un ensemble d’images et de comprendre si elles sont diffusées par Dynamic Media uniquement en observant le domaine du serveur. L’URL devrait être assez constante. Certains clients Dynamic Media ont toutefois basculé vers un domaine de serveur dédié, auquel cas cela peut être `name-of-your-company.scene7.com`. Un domaine de serveur dédié est requis pour l’imagerie dynamique.

Le nom du compte correspond à la partie violette. Dans ce cas, le compte s’appelle `jpearldemo`.

L’identifiant ou le nom de la ressource, `AdobeStock_28563982`, est en vert. Notez que la ressource n’a _aucune_ extension de fichier, que ce soit `.png` ou `.jpg`. Lorsque des ressources sont ingérées dans Dynamic Media, l’extension de fichier est supprimée et un autre type de fichier est créé : un fichier pyramide TIFF. Le TIFF pyramide permet à Dynamic Media de créer rapidement des rendus à la volée.

Enfin, les paramètres de traitement des images, `?wid=1000&fmt=jpeg&qlt=85`, sont indiqués en jaune à la fin.

L’intégralité du chemin de l’URL est actif. [Faites un essai](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock_28563982?wid=1000&amp;fmt=jpeg&amp;qlt=85){target="_blank"}.

La fenêtre de votre navigateur reste ouverte sur l’URL Dynamic Media et l’image de surveillance. Regardons de plus près comment créer des rendus de l’image en modifiant simplement l’URL.

### Rendu de l’image de montre via l’URL

Supprimez d’abord manuellement uniquement les règles de traitement des images dans le chemin de l’URL ; laissez le nom du serveur, le nom du compte et l’identifiant de ressource ou le nom de l’image. [Faites un essai](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock_28563982){target="_blank"}.

Ajoutez maintenant un paramètre de traitement d’image à la fin de l’URL. Dans le champ URL, à droite du nom de l’image, saisissez `?wid=500`, puis appuyez sur **[!UICONTROL Entrée]**. [Faites un essai](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock%5F28563982?wid=500){target="_blank"}.

Notez qu’un nouveau rendu de la montre est généré. Il est essentiel de comprendre, à partir de cet exercice simple de modification de la largeur de l’image, que l’image vue est entièrement générée de manière dynamique.

Maintenant, remplacez la valeur de largeur de `500` pixels par `1000` pixels, puis appuyez sur **[!UICONTROL Entrée]**. [Faites un essai](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock%5F28563982?wid=1000){target="_blank}.
Dès que vous appuyez sur **[!UICONTROL Entrée]**, le navigateur revient au serveur d’images Dynamic Media. Il génère un nouveau rendu de la montre, en fonction de la nouvelle valeur de largeur que vous venez de saisir, puis renvoie la nouvelle image au navigateur et la met en cache.

Dynamic Media propose de nombreux paramètres de traitement des images que vous pouvez utiliser pour affiner vos ressources d’image sur les pages web. Vous pouvez [consulter une liste d’entre eux ici](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html?lang=fr).

Essayez maintenant d’ajouter un paramètre de rotation à l’image de montre. Et la fin du chemin de l’URL, qui suit immédiatement `wid=1000`, saisissez `&rotate=90`, puis appuyez sur **[!UICONTROL Entrée]**. [Faites un essai](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock%5F28563982?wid=1000&amp;rotate=90){target="_blank"}.

La montre est encore légèrement inclinée à gauche. Remplacez la valeur de rotation de `90` par `92`, puis appuyez sur **[!UICONTROL Entrée]**. [Faites un essai](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock%5F28563982?wid=1000&amp;rotate=9){target="_blank"}.

Encore une fois, au moment où vous appuyez **[!UICONTROL Entrée]**, un nouveau rendu de la montre est généré presque instantanément. Voilà le type de performances auxquelles vous pouvez vous attendre, ce qui explique pourquoi Dynamic Media peut envoyer plus de 800 000 requêtes d’image, _par seconde_, lors d’un week-end chargé ou d’un jour férié majeur.

Bien qu’il soit possible de modifier les paramètres de traitement des images dans une URL image par image, cette méthode n’est pas efficace, en particulier si vous avez des dizaines de milliers d’images pour votre site web. Nous recommandons d’utiliser des paramètres d’image prédéfinis.

## Les principes de base de la création de paramètres d’image prédéfinis pour le rendu des ressources {#dm-journey-e}

Il existe plusieurs façons et de nombreux emplacements pour créer une image ou rendre disponible une image. Traditionnellement, un créatif accède à Adobe Photoshop et enregistre chacun de ces différents rendus sous forme d’images statiques.

![Images statiques](/help/assets/dynamic-media/assets/dm-static-images.png)
_Méthode acceptable : images statiques créées chacune manuellement._

Maintenant imaginez que le directeur artistique regarde les images et dise :

_« Je voulais vraiment que sur cette photo la grande aiguille pointe vers le quatre et la petite main vers le 1, pour que l’on voie mieux le cadran »._

Le créatif devra redémarrer toutes les nouvelles images statiques.

Toutefois, avec Dynamic Media, si vous disposez de paramètres d’image prédéfinis différents, vous pouvez utiliser ces images où vous en avez besoin. Ce sont les paramètres d’image prédéfinis qui appliquent les normes.

![Approche de fichiers principaux](/help/assets/dynamic-media/assets/dm-onefile.png)
_Méthode recommandée : un fichier avec plusieurs rendus créés à la volée à l’aide de paramètres d’image prédéfinis, par exemple `Search_Grid` et `Thumbnail`._

| **Pourquoi utiliser les paramètres d’image prédéfinis ?** | |
|---|---|
| Standard | Les paramètres d’image prédéfinis imposent un traitement d’image standard sur toutes les images demandées. |
| Gestion des modifications | Si vous devez modifier le traitement des images, vous devez simplement modifier le paramètre du paramètre d’image prédéfini existant. La définition mise à jour est automatiquement propagée à toutes les requêtes. |

Pour chaque emplacement pour lequel vous avez besoin d’un type d’image particulier, par exemple :

* une page des détails du produit,
* une grille de recherche,
* une miniature,
* une carte d’achat ou encore
* une image à forte identification.

Vous souhaitez que cette image soit diffusée avec les mêmes paramètres partout où elle sera utilisée.

Penchons nous un instants sur la manière dont un paramètre d’image prédéfini est créé dans Dynamic Media.

![Création d’un paramètre d’image prédéfini à partir de l’onglet De base](/help/assets/dynamic-media/assets/dm-image-preset-basictab.png)
_Création d’un paramètre d’image prédéfini à partir de l’onglet De base_

Dans l’exemple ci-dessus, vous pouvez constater qu’un nouveau paramètre d’image prédéfini a été créé avec le nom _Medium_. Dynamic Media utilise un exemple d’image d’usine, un sac à dos, pour vous aider à voir les caractéristiques du paramètre d’image prédéfini au fur et à mesure de sa création.

Le paramètre prédéfini de l’image _Medium_ est de 500 pixels de large et de 800 pixels de haut. Dans la première partie de ce Parcours, vous avez appris comment diffuser des ressources dans différents formats. Dans le menu déroulant **[!UICONTROL Format]**, vous pouvez choisir de diffuser des ressources sous la forme de JPEG, PNG, TIFF ou de plusieurs autres formats. Vous avez une certaine marge de manœuvre.

Sélectionnez l’onglet **[!UICONTROL Avancé]** pour accéder aux options relatives à l’espace colorimétrique de la ressource. En fonction du format que vous avez sélectionné dans l’onglet **[!UICONTROL De base]** (dans l’exemple ci-dessus, JPEG a été sélectionné), vous pouvez diffuser des ressources en RVB, niveaux de gris ou CMJN. Dans le menu déroulant **[!UICONTROL Profil colorimétrique]**, vous pouvez sélectionner comment diffuser une ressource image CMJN pour l’utiliser pour l’impression. Notez également que vous pouvez appliquer d’autres paramètres pour accentuer vos images. Dans ce cas, le paramètre **[!UICONTROL Accentuation]** a été appliqué.

![Création d’un paramètre d’image prédéfini en sélectionnant des options dans l’onglet Avancé](/help/assets/dynamic-media/assets/dm-image-preset-advancedtab.png)
_Création d’un paramètre d’image prédéfini en sélectionnant des options dans l’onglet Avancé_

Vous vous rappelez que, dans le chapitre précédent [Anatomie d’une URL Dynamic Media](#dm-journey-d), vous avez lu des informations sur l’URL Dynamic Media et sur la manière dont elle est créée. Dans la boîte de dialogue **[!UICONTROL Modificateur d’image]**, vous pouvez saisir les paramètres de traitement d’image supplémentaires de votre choix dans la zone de texte. Les paramètres sont inclus dans le nom du paramètre prédéfini de l’URL lors de la diffusion de vos images, à l’aide du paramètre prédéfini. Dans la capture d’écran ci-dessus, le paramètre `bgc=451B15` a été ajouté. En réalité, une couleur de fond marron foncé a été ajoutée.

Vous pouvez considérer un paramètre d’image prédéfini comme une recette pour vos images. Il va fournir n&#39;importe quelle image qui utilise le paramètre prédéfini de manière cohérente à chaque fois ; il va être le même. Le paramètre `&op_brightness=+10` a également été ajouté pour augmenter légèrement la luminosité.

Lorsque vous avez terminé, vous enregistrez le paramètre prédéfini, qui est désormais disponible pour toutes les images dont vous disposez. Dans ce cas, vous souhaitez appliquer le paramètre d&#39;image prédéfini _Medium_ à une image d&#39;un bol de chocolat liquide.

![Application du paramètre d’image prédéfini *Medium* pour générer un rendu d’image](/help/assets/dynamic-media/assets/dm-medium-image-preset.png)
_Application du paramètre d’image prédéfini Medium pour générer un rendu d’image_

Vous copiez l’URL puis la collez dans votre navigateur pour vérifier l’aspect de l’image. [Faites un essai](http://s7d1.scene7.com/is/image/jpearldemo/AdobeStock_74043302?$Medium$){target="_blank"}.

Dans votre navigateur, notez que le nom du paramètre d’image prédéfini _Medium_ est présent dans le chemin d’accès URL complet.

Vous pouvez voir le type de clarté affiché dans l’image. Cette qualité est en partie due à la façon dont la casserole de chocolat a été photographiée. Mais c’est aussi parce qu’avec Dynamic Media vous pouvez stocker des images plus grandes que celles diffusées sur les canaux numériques.

Si tout vous paraît satisfaisant pour votre image de casserole de chocolat, vous collez l’URL dans vos pages web où vous souhaitez que l’image apparaisse sur votre site web.

Si vous regardez à nouveau l’image de la montre ci-dessous, vous pouvez voir qu’il existe un paramètre d’image prédéfini `Cart`, un préréglage `Grid`, un préréglage `Large`, un préréglage `PDP-page` (page Détails du produit), et plusieurs autres.

![Paramètres prédéfinis d’image statiques et dynamiques](/help/assets/dynamic-media/assets/dm-image-presets.png)
_Paramètres d’image prédéfinis statiques et dynamiques L’image de la montre a été rendue à l’aide du paramètre d’image prédéfini `PDP-page`._

Mais qu’en est-il si vous devez changer une image sur votre site web ? Supposons, par exemple, que vous ayez effectué quelques tests et que vous ayez trouvé que l’image de 120 x 120 (le paramètre d’image prédéfini `Cart`) n’est pas reçue aussi bien que vous le pensiez. Vous devez agrandir l’image en augmentant la largeur à 175 pixels et la hauteur à 175 pixels. Traditionnellement, vous deviez aller dans Adobe Photoshop et recréer toutes ces images de panier. Toutefois, avec Dynamic Media, il vous suffit de modifier le paramètre d’image prédéfini en mettant à jour les valeurs Largeur et Hauteur sur 175 et d’enregistrer votre paramètre prédéfini, comme illustré dans l’exemple ci-dessous.

![Modification d’un paramètre d’image prédéfini](/help/assets/dynamic-media/assets/dm-edit-image-preset.png)
_Modification de la largeur et de la hauteur du paramètre d’image prédéfini `Cart`._

Après avoir modifié votre paramètre d’image prédéfini et vidé le cache, toutes les images sont mises à jour et _sans changer_ les URL utilisées avec ce paramètre prédéfini, quelles qu’elles soient. Cela signifie que vous n’aurez pas à gérer de lien rompu et ou de redirection de page web.

## Les visionneuses d’images, à 360° et de supports variés {#dm-journey-f}

Parmi les utilisations les plus courantes de Dynamic Media figure la possibilité de créer des visionneuses d’images, à 360° et de supports variés.

Les visionneuses d’images sont généralement composées d’une série de ressources d’image présentées comme une seule entité. Ces ensembles offrent aux utilisateurs une expérience de visionnage intégrée en leur permettant d’afficher différentes vues d’un élément en cliquant sur une miniature. Les visionneuses d’images permettent de présenter différentes vues d’un élément et offrent des outils pour zoomer et examiner les images de plus près. [Afficher une visionneuse d’images appelée « Running » utilisant la visionneuse Fenêtre déroulante](https://s7d1.scene7.com/s7viewers/html5/FlyoutViewer.html?asset=jpearldemo/Running)

Dans Dynamic Media, vous pouvez voir plusieurs images de chaussures de course. Il s’agit d’une série de produits que les ventes et le marketing souhaitent voir les clients comme une seule présentation ; une visionneuse d’images.

![Création d’une visionneuse d’images](/help/assets/dynamic-media/assets/dm-create-image-set.png)
_Début de la création d’une visionneuse d’images_

Pour créer la visionneuse d’images, choisissez **[!UICONTROL Visionneuse d’images]** dans le menu déroulant **[!UICONTROL Créer]**. Notez que le menu contient également des options pour créer une **[!UICONTROL visionneuse de supports variés]**, une **[!UICONTROL visionneuse à 360°]** et une **[!UICONTROL visionneuse de carrousel]**. Vous créez ces visionneuses de la même manière qu’une visionneuse d’images.

Une visionneuse de supports variés peut contenir des images, des visionneuses d’échantillons, des visionneuses à 360°, et des visionneuses des vidéos et de vidéos adaptatives. [Faites un essai](https://s7d9.scene7.com/s7viewers/html5/MixedMediaViewer.html?asset=Scene7SharedAssets/Mixed_Media_Set_Sample). Une visionneuse à 360° simule l’action consistant à faire pivoter un objet pour l’examiner. Les visionneuses à 360° permettent d’afficher des détails visuels importants sous n’importe quel angle. [Faites un essai](https://s7d9.scene7.com/s7viewers/html5/SpinViewer.html?asset=Scene7SharedAssets/SpinSet_Sample&amp;stagesize=500,400){target="_blank"}.

La création d’une visionneuse d’images est simple. Il vous suffit d’ajouter les ressources d’image que vous souhaitez inclure dans la visionneuse.

![Création d’une visionneuse d’images](/help/assets/dynamic-media/assets/dm-create-image-set-add-assets.png)
_L’éditeur de visionneuse d’images vous permet d’ajouter des ressources d’image et de réorganiser leur aspect dans la visionneuse._

Vous devez donner un nom à la visionneuse. Choisissez le nom avec soin, car vous ne pourrez pas le modifier plus tard ! Dans l’exemple ci-dessus, la visionneuse est appelée `Running`. Lorsque vous avez terminé, vous enregistrez la visionneuse.

Et voici la visionneuse d’images `Running` dans Experience Manager Assets.

![La visionneuse d’images Running dans Experience Manager Assets, en mode Carte](/help/assets/dynamic-media/assets/dm-image-set.png)
_La visionneuse d’images `Running` dans Experience Manager Assets, en mode Carte._

Après avoir créé une visionneuse d’images, de supports variés, à 360° ou de tout autre média interactif, vous voudrez voir comment elle s’affiche et se comporte pour un client. Dynamic Media dispose de nombreuses visionneuses intégrées qui vous permettent de le faire.

Vous commencez en sélectionnant la visionneuse d’images créée pour l’ouvrir dans un aperçu, comme illustré dans l’exemple suivant.

![La visionneuse d’images Running dans l’aperçu, avec l’option Visionneuses sélectionnée](/help/assets/dynamic-media/assets/dm-image-set-viewer.png)
_La visionneuse d’images `Running` d’images dans l’aperçu, avec l’option Visionneuses sélectionnée._

Dans l’aperçu, vous pouvez sélectionner les échantillons de chaussures de course et effectuer un zoom avant ou arrière sur les chaussures. Pour appliquer une visionneuse, sélectionnez **[!UICONTROL Visionneuses]** dans le menu déroulant.

![La visionneuse d’images Running utilisant la visionneuse Fenêtre déroulante](/help/assets/dynamic-media/assets/dm-image-set-flyout-viewer.png)
_La visionneuse d’images `Running` utilisant la visionneuse Fenêtre déroulante._

Dans ce cas, l’observateur `Flyout` a été sélectionné. À ce stade, vous pouvez prévisualiser la visionneuse d’images dans l’observateur. Mais il est préférable de l’afficher dans votre navigateur, de la même manière que le verrait un client. Vous pouvez sélectionner **[!UICONTROL URL]** dans le coin inférieur gauche, puis copier l’URL et la coller dans votre navigateur. [Faites un essai](https://s7d1.scene7.com/s7viewers/html5/FlyoutViewer.html?asset=jpearldemo/Running&amp;config=jpearldemo/Flyout){target="_blank"}.

L’URL unique vous permet d’utiliser la visionneuse d’images et l’observateur in situ sur votre site web. Vous avez peut-être remarqué dans l’exemple précédent la mention **[!UICONTROL Incorporer]** à droite du bouton URL. En sélectionnant **[!UICONTROL Incorporer]**, vous pouvez copier le code de cette visionneuse d’images ou cet observateur et l’ajouter à une page web ou à un composant Experience Manager Sites.

La visionneuse Fenêtre déroulante est une visionneuse prête à l’emploi par défaut dont vous pouvez modifier les propriétés. Vous pouvez également, de la même manière que vous créez un paramètre d’image prédéfini, créer votre propre observateur personnalisé.

Maintenant, supposons que votre équipe de vente et de marketing n’aime pas la visionneuse Fenêtre déroulante. Ils aiment la fonction de zoom, mais souhaitent que les clients voient l’effet de zoom directement sur les chaussures. Dans ce cas, il vous suffit d’appliquer la visionneuse Zoom intégré à la visionneuse d’images, puis de copier et coller son URL dans votre navigateur pour voir comment elle se comporte. [Faites un essai](https://s7d1.scene7.com/s7viewers/html5/FlyoutViewer.html?asset=jpearldemo/Running&amp;config=jpearldemo/InlineZoom){target="_blank"}.

Lorsque vous déplacez le pointeur de la souris sur la chaussure, vous effectuez un zoom avant sur cette image, et vous pouvez voir plus de détails en déplaçant le pointeur. Ce niveau de détail est proportionnel à la taille de l’image qui a été initialement téléchargée dans Dynamic Media.

Que ce soit en tant que consommateur ou dans votre vie professionnelle, vous verrez des exemples de ce type sur différents sites web. Maintenant que vous connaissez l’envers du décor, vous savez comment tirer parti de la puissance de Dynamic Media pour votre travail et le site web de votre entreprise.

Vous venez de lire des articles sur les visionneuses d’images et les visionneuses. Penchons-nous sur deux autres visionneuses et essayons-les sur des ressources uniques. Pour réinitialiser la visionneuse, cliquez sur le bouton **[!UICONTROL Actualiser]** dans le coin inférieur gauche.

<!-- LEAVE THIS HIDDEN PATH IN THE DOCUMENTATION FOR DEMO PURPOSES [Flyout viewer with image set](http://www.partycity.com/girls-little-old-lady-costume-P750948.html) -->

* Visionneuse `ZoomVertical_dark` appliquée à une ressource image. [Faites un essai](https://s7d1.scene7.com/s7viewers/html5/ZoomVerticalViewer.html?asset=jpearldemo/AdobeStock_96311480&amp;config=jpearldemo/ZoomVertical_dark){target="_blank"}.
* Visionneuse `Zoom_light` appliquée à une image. [Faites un essai](https://s7d1.scene7.com/s7viewers/html5/BasicZoomViewer.html?asset=jpearldemo/AdobeStock_38827423&amp;config=jpearldemo/Zoom_light){target="_blank"}.

## Facultatif - En savoir plus

Si vous souhaitez en savoir plus, lisez les documents ci-dessous pour explorer ces concepts plus en détail. Sinon, votre Parcours Dynamic Media est terminé !

<!--
_Dynamic Media Help topics_

* [How to create image presets](/help/assets/dynamic-media/image-presets.md)
* A list of [image processing parameters](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html) that you can use in the Image Modifier field when you create an image preset
* [How to preview assets](/help/assets/dynamic-media/previewing-assets.md)
* [How to preview 3D assets](/help/assets/dynamic-media/previewing-3d-assets.md)
* [How to create Image sets](/help/assets/dynamic-media/image-sets.md)
* [How to create Spin sets](/help/assets/dynamic-media/spin-sets.md)
* [How to create Mixed Media sets](/help/assets/dynamic-media/mixed-media-sets.md) -->

_Tutoriels Dynamic Media_

* [Utilisation de Dynamic Media avec Experience Manager Assets](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-overview-feature-video-use.html?lang=fr)
* [Bibliothèque de contenu Adobe Experience Manager](https://experienceleague.adobe.com/?lang=fr#recommended/solutions/experience-manager) (recherchez _Dynamic Media_)

_Visionneuses Dynamic Media_

* [Démonstrations en direct](https://landing.adobe.com/en/na/dynamic-media/ctir-2755/live-demos.html) de chaque visionneuse

<!-- Live as of April 28 2022. LEAVE IN HERE https://landing.adobe.com/en/na/dynamic-media/ctir-2755/index.html -->