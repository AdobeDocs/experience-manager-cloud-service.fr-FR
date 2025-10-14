---
title: 'Bonnes pratiques relatives à l’optimisation de la qualité des images '
description: Découvrez les bonnes pratiques qui vous permettent d’optimiser la qualité de vos ressources d’images à l’aide de Dynamic Media.
contentOwner: Rick Brough
feature: Asset Management, Best Practices
role: User
exl-id: 2efc4a27-01d7-427f-9701-393497314402
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
workflow-type: tm+mt
source-wordcount: '1648'
ht-degree: 72%

---

# Bonnes pratiques relatives à l’optimisation de la qualité des images {#best-practices-for-optimizing-the-quality-of-your-images}

{{work-with-dynamic-media}}

L’optimisation de la qualité des images peut être un processus chronophage, car de nombreux facteurs contribuent à l’obtention de résultats acceptables. Le résultat est en partie subjectif parce que les individus perçoivent différemment la qualité de l’image. L’expérimentation structurée est essentielle.

Adobe Experience Manager inclut plus de 100 commandes de diffusion d’images Dynamic Media permettant d’affiner et d’optimiser les images et les rendus. Les instructions suivantes peuvent vous aider à rationaliser le processus et à obtenir de bons résultats rapidement à l’aide de commandes essentielles et de pratiques recommandées.

<!-- ADDED THE FOLLOWING TOPIC AS PER CQDOC-21594 -->

## Activation de l’imagerie dynamique dans Dynamic Media {#bp-enable-smart-imaging}

**Imagerie dynamique :**

* L’activation de l’imagerie dynamique dans Dynamic Media permet d’optimiser automatiquement le format, la taille et la qualité des images en fonction des fonctionnalités du navigateur client.
Vous souhaitez en savoir plus ? Accédez à [&#x200B; Imagerie dynamique &#x200B;](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/assets/dynamicmedia/imaging-faq).
* Il améliore les performances de diffusion des images en ajustant dynamiquement ces paramètres.
* Vous pouvez évaluer l’imagerie dynamique à l’aide de l’outil d’auto-évaluation [Instantané](https://snapshot.scene7.com/).

**Formats d’image :**

* Évitez d’utiliser des commandes `fmt=webp` ou `fmt=avif` explicites dans une URL, sauf si cela est spécifiquement requis pour un cas d’utilisation.
* L’imagerie dynamique sélectionne automatiquement le meilleur format, ce qui se traduit par des gains de bande passante optimaux.

**Comportement par défaut :**

* Lorsqu’aucune commande de format n’est spécifiée dans l’URL et que l’imagerie dynamique n’est pas activée, la diffusion d’images Dynamic Media utilise par défaut le format JPEG.

En choisissant en connaissance de cause les formats d’image et en activant l’imagerie dynamique, vous pouvez améliorer considérablement les performances et l’expérience utilisateur.


<!-- ADDED THE FOLLOWING TOPIC AS PER CQDOC-21594 -->

## Bonnes pratiques pour sélectionner l’image source {#bp-select-source-image}

Points essentiels à prendre en compte pour l’utilisation des images sources :

* **Format d’image Source :**
   * L’utilisation de formats sans perte tels que PNG, TIFF ou PSD garantit que la qualité de l’image reste élevée sans artefact de compression.
   * Ces formats conservent toutes les données d’origine, ce qui les rend parfaits pour l’édition et le traitement ultérieur.
* **Taille de l’image Source :**
   * Commencer avec une image haute résolution offre plus de détails et de flexibilité.
   * Lorsque des images doivent être affichées dans différentes tailles (par exemple, sur plusieurs appareils ou résolutions d’écran), une image source plus grande permet une meilleure mise à l’échelle.
   * Pour les images qui prennent en charge le zoom (comme les photos de produits), visez des dimensions d’environ 2 000 pixels ou plus sur le côté le plus long.
   * Les logos ou bannières qui ne nécessitent pas de zoom peuvent être téléchargés dans la plus grande taille nécessaire à leur utilisation prévue.

En effectuant ces choix judicieux au niveau de la source, vous pouvez contribuer de manière significative à la qualité globale de votre contenu visuel.

<!-- REMOVED TOPIC AS PER CQDOC-21594
## Best practices for image format (`&fmt=`) {#best-practices-for-image-format-fmt}

* JPG or PNG are the best choices to deliver images in good quality and with manageable size and weight.
* If no format command is supplied in the URL, Dynamic Media Image Delivery defaults to JPG for delivery.
* JPG compresses at a ratio of 10:1 and usually produces smaller image file sizes. PNG compresses at a ratio of about 2:1, except when images contain a white background. Typically though, PNG file sizes are larger than JPG files.
* JPG uses lossy compression, meaning that picture elements (pixels) are dropped during compression. PNG on the other hand uses lossless compression.
* JPG often compresses photographic images with better fidelity than synthetic images with sharp edges and contrast.
* If your images contain transparency, use PNG because JPG does not support transparency.

As a best practice for image format, start with the most common setting `&fmt=JPG`. -->

## Bonnes pratiques relatives à la taille des images {#best-practices-for-image-size}

La réduction dynamique de la taille de l’image est l’une des tâches les plus courantes. Cela implique de spécifier la taille et, éventuellement, le mode de sous-échantillonnage utilisé pour réduire l’image.

* Pour le dimensionnement des images, la meilleure méthode, mais aussi la plus simple, consiste à utiliser `&wid=<value>` et `&hei=<value>,` ou simplement `&hei=<value>`. Ces paramètres définissent automatiquement la largeur de l’image en respectant le format.
* `&resMode=<value>` contrôle l’algorithme utilisé pour le sous-échantillonnage. Commencez par `&resMode=sharp2`. Cette valeur fournit la meilleure qualité d’image. Bien que l’utilisation du sous-échantillonnage `value =bilin` soit plus rapide, elle se traduit souvent par un crénelage des artefacts.

Pour le dimensionnement des images, il est recommandé d’utiliser `&wid=<value>&hei=<value>&resMode=sharp2` ou `&hei=<value>&resMode=sharp2`.

## Bonnes pratiques relatives à l’accentuation des images {#best-practices-for-image-sharpening}

L’accentuation des images est l’aspect le plus complexe du contrôle des images du site web, processus au cours duquel de nombreuses erreurs sont commises. Prenez le temps d’en savoir plus sur le fonctionnement de l’accentuation et du masquage flou dans Experience Manager en vous référant aux ressources suivantes :

* L’article technique [Bonnes pratiques concernant la qualité d’image et l’accentuation de la netteté avec Adobe Dynamic Media Classic](/help/assets/dynamic-media/assets/sharpening_images.pdf) s’applique également à Experience Manager.

* Regarder la vidéo [Utilisation de l’accentuation d’image avec Experience Manager – Dynamic Media](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-image-sharpening-feature-video-use#dynamic-media).

Avec Experience Manager, vous pouvez accentuer les images lors de l’ingestion, lors de la diffusion, ou les deux. En général, cependant, il est préférable d’accentuer les images en utilisant une seule méthode ou l’autre, mais pas les deux. L’accentuation des images lors de la diffusion, sur une URL, vous donne généralement les meilleurs résultats.

Vous pouvez utiliser deux méthodes d’accentuation d’image :

* Accentuation simple (`&op_sharpen`) : à l’instar du filtre d’accentuation utilisé dans Photoshop, l’accentuation simple applique une accentuation de base à l’affichage final de l’image à la suite d’un redimensionnement dynamique. Cependant, cette méthode ne peut pas être configurée par l’utilisateur. La bonne pratique consiste à éviter d’utiliser `&op_sharpen`, sauf si nécessaire.
* Masquage flou (`&op_USM`) : le masquage flou est un filtre d’accentuation standard. La bonne pratique consiste à accentuer les images à l’aide de l’accentuation en suivant les instructions ci-dessous. L’accentuation permet de contrôler les trois paramètres suivants :

   * `&op_sharpen=`quantité,rayon,seuil

      * **[!UICONTROL quantité]** (0 à 5, intensité de l’effet)
      * **[!UICONTROL rayon]** (0 à 250, largeur des « lignes d’accentuation » tracées autour de l’objet accentué, mesurées en pixels.)

     Gardez à l’esprit que les paramètres rayon et montant fonctionnent l’un contre l’autre. La réduction du rayon peut être compensée par une augmentation de la quantité. Le rayon permet un contrôle plus fin, car une valeur faible accentue uniquement les pixels de contour, tandis qu’une valeur élevée accentue une bande plus large de pixels.

      * **[!UICONTROL seuil]** (0 à 255, sensibilité de l’effet)

     Ce paramètre définit l’écart recherché entre les pixels accentués et la zone environnante avant qu’ils ne soient considérés comme des pixels de contour et que le filtre les accentue. Le paramètre **[!UICONTROL seuil]** permet d’éviter les zones à l’accentuation excessive avec des couleurs similaires, telles que les tons chair. Par exemple, une valeur seuil de 12 ignore les légères variations de luminosité de la peau pour éviter d’ajouter du « bruit », tout en ajoutant un contraste sur les bords dans les zones à fort contraste, comme l’endroit où les cils rencontrent la peau.

     Pour plus d’informations sur la façon de définir ces trois paramètres, y compris les bonnes pratiques à appliquer avec le filtre, reportez-vous aux ressources suivantes :

      * L’article technique [Bonnes pratiques concernant la qualité d’image et l’accentuation de la netteté avec Adobe Dynamic Media Classic](/help/assets/dynamic-media/assets/sharpening_images.pdf) s’applique également à Experience Manager.

      * Regarder la vidéo [Utilisation de l’accentuation d’image avec Experience Manager – Dynamic Media](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-image-sharpening-feature-video-use#dynamic-media).

      * Experience Manager permet également de contrôler un quatrième paramètre : monochrome (0,1). Ce paramètre détermine si le masquage flou est appliqué séparément à chaque composante de couleur en utilisant la valeur 0, ou à la luminosité/l’intensité de l’image en utilisant la valeur 1.

Il est recommandé de commencer par le paramètre rayon d’accentuation. Les paramètres rayon avec lesquels vous pouvez commencer sont les suivants :

* **[!UICONTROL Site web]** : 0,2 à 0,3 pixel
* **[!UICONTROL Impression photographique (250 à 300 ppp)]** : 0,3 à 0,5 pixel
* **[!UICONTROL Impression offset (266 à 300 ppp)]** : 0,7 à 1,0 pixel
* **[!UICONTROL Impression sur toile (150 ppp)]** : 1,5 à 2,0 pixels

Augmentez graduellement la valeur de 1,75 à 4. Si l’accentuation ne vous convient toujours pas, augmentez le rayon d’un point décimal, puis réexécutez la quantité de 1,75 à 4. Recommencez si nécessaire.

Laissez le paramètre monochrome sur 0.

### Bonnes pratiques relatives à la compression JPEG (`&qlt=`) {#best-practices-for-jpef-compression-qlt}

* Ce paramètre contrôle la qualité du codage des JPG. Une valeur élevée produit une image de meilleure qualité, mais un fichier plus volumineux ; en revanche, une valeur faible signifie une image de qualité inférieure mais un fichier plus petit. La plage de ce paramètre est 0 à 100.
* Pour optimiser la qualité, ne définissez pas la valeur du paramètre sur 100. La différence entre un réglage de 90 ou 95 et 100 est presque imperceptible. Et pourtant, 100 augmente inutilement la taille du fichier image. En conséquence, pour optimiser la qualité, mais éviter que les fichiers image deviennent trop volumineux, définissez `qlt= value` sur 90 ou 95.
* Pour optimiser pour une petite taille de fichier image tout en conservant la qualité de l’image à un niveau acceptable, définissez la `qlt= value` sur 80. Les valeurs inférieures à 70-75 entraînent une dégradation significative de la qualité de l’image.
* Une bonne pratique pour rester dans la moyenne consiste à définir `qlt= value` sur 85.
* Utilisation du drapeau chromatique dans le paramètre `qlt=`

   * Le paramètre `qlt=` possède un deuxième paramètre qui vous permet d’activer le sous-échantillonnage chromatique RVB à l’aide de la valeur `,1` ou de le désactiver à l’aide de la valeur `,0`.
   * Pour faire simple, commencez par désactiver le sous-échantillonnage chromatique RVB (`,0`). Ce paramètre produit généralement une image de meilleure qualité, en particulier pour les images de synthèse contenant beaucoup de contours nets et un fort contraste.

La bonne pratique pour la compression JPG consiste à utiliser `&qlt=85,0`.

## Bonnes pratiques relatives au dimensionnement JPEG (`&jpegSize=`) {#best-practices-for-jpeg-sizing-jpegsize}

Le paramètre `jpegSize` est utile pour garantir qu’une image n’excède pas une certaine taille pour sa diffusion sur les appareils dont la mémoire est limitée.

* Ce paramètre est défini en kilo-octets (`jpegSize=&lt;size_in_kilobytes&gt;`). Il définit la taille maximale autorisée pour la diffusion de l’image.
* `&jpegSize=` interagit avec le paramètre de compression JPG `&qlt=`. Si la réponse JPG avec le paramètre de compression JPG spécifié (`&qlt=`) ne dépasse pas la valeur jpegSize, l’image est renvoyée avec `&qlt=` tel que défini. Sinon, la `&qlt=` est progressivement réduite jusqu’à ce que l’image corresponde à la taille maximale autorisée. Ou, jusqu’à ce que le système détermine qu’il ne peut pas tenir et renvoie une erreur.

Une bonne pratique consiste à définir `&jpegSize=` et à ajouter le paramètre `&qlt=` si vous diffusez des images JPG vers des appareils dont la mémoire est limitée.

## Résumé des bonnes pratiques {#best-practices-summary}

En règle générale, pour obtenir une qualité d’image élevée et une petite taille de fichier, commencez par la combinaison de paramètres suivante :

`fmt=jpg&qlt=85,0&resMode=sharp2&op_usm=1.75,0.3,2,0`

Cette combinaison de paramètres produit d’excellents résultats dans la plupart des cas.

Si l’image nécessite davantage d’optimisation, ajustez progressivement les paramètres d’accentuation (masquage flou) en commençant par un rayon défini sur 0,2 ou 0,3. Ensuite, augmentez graduellement la quantité de 1,75 à un maximum de 4 (équivalent à 400 % dans Photoshop). Vérifiez que le résultat souhaité est obtenu.

Si les résultats de l’accentuation ne sont toujours pas satisfaisants, augmentez le rayon par incréments décimaux. Pour chaque incrément décimal, relancez la quantité à 1,75 et augmentez-la progressivement à 4. Répétez cette procédure jusqu’à obtenir le résultat souhaité. Bien que les valeurs ci-dessus soient une approche validée par les studios de création, n’oubliez pas que vous pouvez commencer par d’autres valeurs et suivre d’autres stratégies. Que les résultats vous conviennent ou non est une question subjective, par conséquent l&#39;expérimentation structurée est la clé.

Au fur et à mesure que vous testez, les suggestions générales suivantes sont utiles pour optimiser votre workflow :

* Testez différents paramètres en temps réel, directement sur une URL.
* Gardez à l’esprit que vous pouvez regrouper les commandes de diffusion d’images Dynamic Media dans un paramètre d’image prédéfini. Il s’agit en outre d’une bonne pratique. Un paramètre d’image prédéfini est, en fait, constitué de macros de commande d’URL avec des noms de paramètres prédéfinis personnalisés tels que `$thumb_low$` et `&product_high$`. Le nom du paramètre prédéfini personnalisé dans un chemin URL appelle ces paramètres prédéfinis. Cette fonctionnalité vous aide à gérer les commandes et les paramètres de qualité pour différents modèles d’utilisation des images sur vos sites web et raccourcit la longueur globale des URL.
* Experience Manager propose également des méthodes plus élaborées permettant d’optimiser la qualité des images, par exemple en accentuant les images lors de l’ingestion. Pour affiner et optimiser les résultats de rendu, [les services de consulting d’Adobe](https://business.adobe.com/customers/consulting-services/main.html) peuvent vous aider à personnaliser vos informations et les bonnes pratiques.
