---
title: Bonnes pratiques relatives à Dynamic Media
description: Découvrez les bonnes pratiques relatives à l’utilisation des images et des vidéos dans Dynamic Media, ainsi que les bonnes pratiques relatives aux visionneuses Dynamic Media.
contentOwner: Rick Brough
products: Experience Manager as a Cloud Service
topic-tags: introduction,administering
content-type: reference
feature: Adaptive Streaming, Best Practices, Smart Imaging, Image Profiles, Rulesets, Viewers, Smart Crop, SEO Optimization, Publishing, Video, Renditions, Asset Management
role: User, Admin
mini-toc-levels: 4
exl-id: 39e491bb-367d-4c72-b4ca-aab38d513ac5
source-git-commit: 6ad46350906c3b8a36a8e361714fa5fffdbf8e82
workflow-type: tm+mt
source-wordcount: '4118'
ht-degree: 0%

---

# Bonnes pratiques relatives à Dynamic Media{#about-dm-best-practices}

<!--**Organizations today must connect with their customers through an ever-growing array of channels and devices.** The customer experience spans physical stores, websites, mobile apps, social media, email, and e-commerce platforms. This diversity requires organizations to create many more versions of each piece of content. Personalization adds complexity by increasing the number of variations needed for each item. Despite budget constraints for content creation, there's still a need to produce more campaigns in the same timeframe, on a global scale. AEM Dynamic Media offers a comprehensive set of tools to meet these challenges, providing consistent, personalized, high-performance, and optimized brand experiences across all channels and devices. 

Key Features of AEM Dynamic Media:

* **Single File Approach:** Save on storage costs by storing just one master file. AEM Dynamic Media generates all size variations and visual effects on-demand, at the time of delivery, eliminating workflow complexity and last-minute creative changes.
* **Global Reach:** With Smart Imaging, images are automatically optimized during delivery, significantly reducing file size and page weight without sacrificing visual quality. This optimization is tailored for network bandwidth and device pixel ratio.
* **AI-Powered Efficiency:** Smart Crop uses AI to automate the cropping of images and videos, focusing on points of interest. This feature saves countless hours of manual editing and is designed for large-scale enterprise production.
* **Video Made Simple:** Upload a master video file and AEM Dynamic Media will adaptively stream it in multiple languages and with descriptive audio, ensuring a broad reach.
* **Customizable Experience Viewer:** Select, customize, and brand the experience viewers for images and videos with ease. These viewers can be seamlessly integrated into any digital experience.
* **Support for Emerging Formats:** AEM Dynamic Media is also your solution for delivering immersive 3D and panoramic experiences.

In the accompanying guide, you'll find a comprehensive list of best practices for maximizing the benefits of AEM Dynamic Media. As you embark on your Dynamic Media journey, make sure to consult these expert recommendations and resources.

Stage Business Problem Best Practice Recommendation: This section will outline specific business challenges and provide targeted best practices and recommendations to address them effectively. -->

{{work-with-dynamic-media}}

Les entreprises sont confrontées à une explosion de canaux et d’appareils pour interagir avec les utilisateurs. Le parcours client s’étend sur les magasins physiques, le web, les appareils mobiles, les médias sociaux, les courriers électroniques et le commerce. Pour répondre à cette demande, Dynamic Media on Adobe Experience Manager (AEM) offre une solution complète. Il optimise la diffusion des ressources, gère la personnalisation et assure des expériences cohérentes, performantes et alignées sur la marque sur les canaux et les appareils.

Voici quelques-uns des principes clés de Dynamic Media :

* **Approche à fichier unique :** avec Dynamic Media, vous stockez un fichier source principal, et toutes les variations de taille et tous les effets visuels sont créés et optimisés dynamiquement au moment de la diffusion. Cette approche permet d’économiser les coûts de stockage et élimine la complexité des workflows.
* **Véritablement global :** L’imagerie dynamique, appliquée lors de la diffusion du contenu, réduit considérablement la taille de l’image et le poids de la page sans compromettre la qualité visuelle. Il est optimisé pour la bande passante du réseau et les rapports pixels de l’appareil.
* **Fonctionnalité optimisée par l’IA :** le recadrage intelligent, une fonctionnalité pilotée par l’IA, automatise le recadrage d’image et de point d’intérêt vidéo. Il élimine les efforts manuels et les échelles efficaces pour une utilisation en entreprise.
* **Vidéo simple :** Téléchargez des vidéos sources originales dans Dynamic Media et diffusez-les de manière adaptative dans plusieurs langues avec un audio descriptif.
* **Bibliothèque de la visionneuse d’expériences :** personnalisez et marquez les visionneuses d’expériences pour les images et les vidéos. Ces visionneuses s’intègrent de manière transparente à vos expériences numériques.
* **Prise en charge du format émergent :** Dynamic Media permet la diffusion d’expériences 3D et panoramiques.

En explorant le [Parcours Dynamic Media](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/assets/dynamicmedia/dm-journey/dm-journey-part1), consultez la liste consolidée des bonnes pratiques ci-dessous pour tirer le meilleur parti de ses fonctionnalités. Adaptez ces bonnes pratiques Dynamic Media à votre contexte spécifique et aux exigences de vos projets afin d’optimiser vos expériences sur les canaux et les périphériques.

<!-- In Dynamic Media on AEM, there are sets of methods, techniques, and guidelines that can help you maximize the potential of your rich media content. These best practices can lead to optimal results and increase efficiency in your use of Dynamic Media. They represent the most efficient and effective courses of action in a particular situation. They also unlock high value for your audience and deliver high-quality, engaging content. -->

>[!IMPORTANT]
>
>Les bonnes pratiques Dynamic Media décrites dans cet article peuvent évoluer au fil du temps à mesure que de nouvelles technologies apparaissent dans Dynamic Media. Les informations ci-dessous sont à jour pour la dernière version de Dynamic Media.


## Ingestion de ressources dans Dynamic Media

**Analyse de cas :** *Gérez efficacement de grands volumes de ressources et assurez-vous que seul le contenu pertinent et approuvé est diffusé aux utilisateurs finaux.*

Simplifiez efficacement la gestion d’un grand nombre de ressources. Assurez-vous que seul le contenu approprié et autorisé atteint vos utilisateurs finaux en utilisant les fonctionnalités de **synchronisation sélective** et de **Publish sélective** de Dynamic Media.

* **Synchronisation sélective :**
Fonctionnalité proactive qui vous permet de choisir les ressources à synchroniser avec Dynamic Media. Par exemple, vous pouvez décider de ne synchroniser que les dossiers contenant les ressources qui ont reçu l’approbation finale. Ce workflow vous permet de contrôler quelles ressources sont préparées pour la diffusion à vos clients.

* **Publication sélective :**
Une fois vos ressources synchronisées, le Publish sélectif vous permet de contrôler quelles ressources sont visibles par vos clients. Grâce à cette fonctionnalité, vous pouvez déterminer les ressources approuvées qui sont réellement diffusées par le biais de vos canaux, en veillant à ce que vos clients ne voient que le contenu le plus pertinent et le meilleur.

Ces deux bonnes pratiques vous aident à mieux contrôler, gérer et optimiser la productivité de votre contenu multimédia.

Vous souhaitez en savoir plus ? Accédez à [Configurer le Publish sélectif au niveau du dossier dans Dynamic Media](/help/assets/dynamic-media/selective-publishing.md).


## Visionneuses Dynamic Media

Les bonnes pratiques relatives aux visionneuses Dynamic Media sont des directives essentielles conçues pour optimiser les performances, les fonctionnalités et l’expérience utilisateur des ressources Dynamic Media sur AEM. Ces pratiques garantissent que les ressources sont correctement synchronisées, publiées et configurées pour utiliser toutes les fonctionnalités de Dynamic Media.

En suivant ces bonnes pratiques, vous pouvez obtenir une intégration transparente, une gestion efficace des ressources et des interactions de visionneuse améliorées. La synchronisation des ressources, l’utilisation du recadrage intelligent et le respect des directives d’inclusion de fichier JavaScript sont des pratiques importantes. Ces recommandations permettent de maintenir l’intégrité et la fiabilité de la diffusion multimédia sur différentes plateformes et différents appareils.

* **Synchroniser la visionneuse Assets :**
Assurez-vous que toutes les ressources de visionneuse sont synchronisées avec Dynamic Media avant d’utiliser le lecteur.

   * Accédez à la page du gestionnaire d’exemples à l’adresse `/libs/dam/gui/content/s7dam/samplemanager/samplemanager`. Cette page vous permet de resynchroniser les ressources d’une visionneuse, y compris les icônes d’usine, les fichiers CSS et les paramètres prédéfinis.
   * Si vous rencontrez des problèmes de visionneuse, reportez-vous à l’article [Dépannage des visionneuses Dynamic Media](/help/assets/dynamic-media/troubleshoot-dm.md#viewers) .

* **Publish Assets :**
Assurez-vous que les ressources sont publiées avant de les afficher dans les visionneuses de diffusion.
* **Vidéos de lecture automatique coupées :**
Pour la fonctionnalité de lecture automatique des vidéos, utilisez les paramètres vidéo muets, car les navigateurs limitent la lecture des vidéos avec le volume.
* **Recadrage intelligent :**
Utilisez le composant Image v3 pour le recadrage intelligent afin d’améliorer la présentation des ressources d’image.
* **Inclusion de fichier JavaScript :**
N’incluez que le fichier JavaScript de la visionneuse principale sur votre page. Évitez de référencer des fichiers JavaScript supplémentaires que la logique d’exécution de la visionneuse peut télécharger. En particulier, ne liez pas directement à la bibliothèque `Utils.js` du SDK HTML5 à partir du chemin d’accès au contexte `/s7viewers` (appelé inclusion du SDK consolidé). La logique de la visionneuse gère l’emplacement de `Utils.js` ou de bibliothèques de visionneuses d’exécution similaires, qui peuvent changer d’une version à l’autre. Adobe ne conserve pas les anciennes versions de la visionneuse secondaire incluses sur le serveur. Par conséquent, leur référencement direct peut interrompre la fonctionnalité de la visionneuse lors des futures mises à jour.
* **Instructions d’incorporation :**
Utilisez la documentation pour incorporer des directives spécifiques à chaque visionneuse.
Vous souhaitez en savoir plus ? Accédez à [Visionneuses pour AEM Assets](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/c-html5-s7-aem-asset-viewers).
* **Tutoriel du SDK et exemples :**
Passez en revue les [exemples d’applications du SDK de la visionneuse](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/library/c-tutorial) et [exemples d’applications du SDK HTML5](https://s7d9.scene7.com/s7sdk/2024.5/docs/jsdoc/index.html) pour une compréhension approfondie des API de composants du SDK.


## Préparation des ressources pour la diffusion

### Organisation de vos ressources

**Analyse de cas :** *Organisez efficacement les ressources pour rationaliser les workflows.*

Pour une organisation efficace des ressources qui rationalise les workflows, utilisez une ou plusieurs des bonnes pratiques suivantes :

* **Organiser les ressources dans les dossiers :**
L’organisation efficace des ressources implique de les classer dans des dossiers, comme l’organisation de fichiers sur un ordinateur. Pour un traitement efficace des ressources, il est essentiel de nommer correctement les sous-dossiers, de les structurer et de gérer les fichiers au sein de ces dossiers. La mise en oeuvre de conventions d’affectation de noms et de pratiques de métadonnées systématiques optimise l’utilité de votre référentiel de ressources numériques.
Vous souhaitez en savoir plus ? Accédez à [Organiser les ressources dans les dossiers](/help/assets/organize-assets.md#organize-using-folders).
* **Organiser les ressources à l’aide de balises :**
Le balisage des ressources améliore la recherche, la création de collections et le classement des recherches. Adobe Sensei AI utilise un algorithme d’auto-apprentissage pour le balisage précis, ce qui permet la récupération rapide des ressources. Adobe Sensei reconnaît et attribue également des balises pertinentes, y compris des balises personnalisées, aux ressources, ce qui simplifie la gestion des ressources avec un balisage automatique et descriptif.
Vous souhaitez en savoir plus ? Accédez à [Organiser les ressources à l’aide des balises](/help/assets/organize-assets.md#use-tags-to-organize-assets).
* **Organiser les ressources en tant que collections :**
Dynamic Media ainsi que Experience Manager Assets permettent de créer, modifier et partager efficacement des collections de ressources entre les utilisateurs. Vous pouvez définir différents types de collections, notamment des listes statiques et des compilations dynamiques basées sur des recherches. Ces types de collections peuvent être partagés à différents emplacements avec des droits d’accès et de modification personnalisables.
Vous souhaitez en savoir plus ? Accédez à [Organiser les ressources en tant que collections](/help/assets/manage-collections.md).
* **Organiser les ressources à l’aide des profils :**
Un profil de traitement automatise la gestion des ressources dans les dossiers désignés, ce qui rationalise l’organisation. La normalisation des métadonnées, des noms de fichier et des structures de dossiers permet d’appliquer ces profils de manière cohérente et précise au fur et à mesure que votre collection de ressources numériques se développe.
Vous souhaitez en savoir plus ? Accédez à [Organiser les ressources à l’aide des profils](/help/assets/organize-assets.md#organize-to-use-profiles).



### Optimiser la qualité des images

**Analyse de cas :** *Obtenez des images de qualité à partir de Dynamic Media.*

L’amélioration de la qualité d’image nécessite une prise en compte attentive de divers facteurs. Ce processus peut prendre beaucoup de temps. Cependant, certaines pratiques éprouvées peuvent vous aider à obtenir des résultats souhaitables. Certaines de ces bonnes pratiques incluent la manière d’obtenir un dimensionnement d’image optimal, l’accentuation des images et les meilleurs formats d’image à utiliser.

Vous souhaitez en savoir plus ? Accédez à [Bonnes pratiques pour optimiser la qualité de vos images](/help/assets/dynamic-media/best-practices-for-optimizing-the-quality-of-your-images.md).

Comme la perception de la qualité de l’image varie d’une personne à l’autre, une approche systématique de l’expérimentation est parfois essentielle pour obtenir des résultats désirables. Adobe Experience Manager facilite ce processus avec plus de 100 commandes Dynamic Media pour améliorer l’image.

Vous souhaitez en savoir plus ? Regardez [Dynamic Media Snapshot](https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-snapshot) (3 minutes, 17 secondes).

Pour évaluer l’impact de ces différentes commandes sur la qualité de l’image, vous pouvez télécharger une image vers Dynamic Media, utiliser l’interface de l’outil à l’URL spécifiée et appliquer les commandes que vous souhaitez tester.

Vous voulez essayer ? Lancer [Dynamic Media Snapshot](https://snapshot.scene7.com/)

### Normalisation des styles appliqués aux images

**Analyse de cas :** *Normalisez efficacement le style et la transformation appliqués à mes ressources d’image.*

Utilisez régulièrement des paramètres d’image prédéfinis dans Dynamic Media afin de pouvoir ajuster de manière cohérente et dynamique les tailles, les formats et les propriétés des images. Considérez un paramètre d’image prédéfini comme une macro : il s’agit d’un ensemble nommé de commandes de dimensionnement et de formatage. Par exemple, si votre site a besoin d’images de produits de tailles et de formats différents, avec une compression spécifique pour les ordinateurs de bureau et les appareils mobiles, les paramètres d’image prédéfinis automatisent ce processus de manière efficace.

Vous voulez essayer ? Accédez à [Principes de base de la création de paramètres d’image prédéfinis pour effectuer le rendu des ressources](/help/assets/dynamic-media/dm-journey-part2.md#dm-journey-e)

### Ajuster la mise au point et le cadre des images et des vidéos

**Analyse de cas :** *Assurez-vous que le principal point ciblé de mes images ou vidéos reste ciblé sur tous les appareils.*

Le recadrage intelligent est une fonctionnalité de Dynamic Media qui utilise Adobe Sensei, l’IA d’Adobe et le framework d’apprentissage automatique, pour automatiser le recadrage des images et des vidéos. Il détecte intelligemment le sujet principal ou le point ciblé d’une image ou d’une vidéo et s’y concentre de manière intelligente. Cette intelligence garantit que le point focal est conservé sur différentes tailles d’écran sur les ordinateurs de bureau et les appareils mobiles.

Il est recommandé de créer un profil d’image avec recadrage intelligent. Dans le profil, vous pouvez définir différentes tailles d’écran et laisser Adobe Sensei effectuer le reste, en vous assurant que vos images et vidéos sont toujours optimisées pour l’appareil de la visionneuse.

Vous souhaitez en savoir plus ? Regardez la vidéo [Utilisation du recadrage intelligent avec AEM Assets Dynamic Media](https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/images/smart-crop-feature-video-use) (6 minutes, 35 secondes) et [Utilisation du recadrage intelligent Dynamic Media pour la vidéo](https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/video/dynamic-media-smart-crop-video) (6 minutes, 22 secondes).

### Amélioration des classements SEO

**Analyse de cas :** *Configurez Dynamic Media pour obtenir des classements SEO améliorés.*

Appliquez régulièrement les recommandations suivantes pour vous assurer que vos images contribuent efficacement à votre stratégie d’optimisation pour les moteurs de recherche globale.

* **Noms de fichiers image significatifs :**
Utilisez des noms de fichier descriptifs qui reflètent le contenu de l’image. Par exemple :

   * Utilisez `myCompany-Silver-Wrist-Watch`
   * ** `myCompany_Silver_Wrist_Watch` ou `myCompanySilverWristWatch`

  Cela permet aux moteurs de recherche de comprendre le contexte de l’image et améliore l’optimisation du référencement. Google préfère les tirets aux traits de soulignement ou aux espaces dans le nom d’un fichier. Évitez également de concaténer des mots dans un nom de fichier.
* **Domaine personnalisé :**
Implémentez un domaine personnalisé qui inclut le nom de votre société ou marque pour renforcer la reconnaissance et la confiance de la marque. Par exemple :

   * Utilisez `http://images.mycompany.com/is/image/companyname/`
   * ** `https://s7d1.scene7.com/is/image/folder/AdobeStock_28563982`

* **Structure de dossiers compatible avec l’optimisation pour les moteurs de recherche :**
Organisez vos images dans une structure de dossiers qui inclut le nom ou la marque de votre société pour une meilleure indexation, par exemple `http://images.mycompany.com/is/image/companyname/`.
* **Jeux de règles Dynamic Media :**
Découvrez comment transformer de manière conditionnelle les URL en fonction de divers facteurs, ce qui améliore l’optimisation du référencement et l’expérience utilisateur.
Vous souhaitez en savoir plus ? Accédez à [Utiliser des ensembles de règles pour transformer les URL](/help/assets/dynamic-media/using-rulesets-to-transform-urls.md).
* **Imagerie dynamique et recadrage intelligent :**
Utilisez les fonctionnalités d’imagerie dynamique et de recadrage intelligent de Dynamic Media pour diffuser des images optimisées et réactives. Cela permet non seulement d’améliorer les temps de chargement des pages, mais contribue également de manière positive aux classements SEO.
Vous souhaitez en savoir plus ? Accédez à [Smart Imaging](/help/assets/dynamic-media/imaging-faq.md) ou regardez [Utilisation du recadrage intelligent avec AEM Assets Dynamic Media](https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/images/smart-crop-feature-video-use) (6 minutes, 35 secondes).

N’oubliez pas que ces bonnes pratiques s’alignent bien sur les bonnes pratiques d’optimisation du référencement des images de Google. Ces pratiques mettent l’accent sur l’importance de fournir un contexte et une clarté aux moteurs de recherche par le biais de conventions d’affectation de noms appropriées, de données structurées et d’une diffusion d’images optimisée.

Vous souhaitez en savoir plus ? Accédez à [Bonnes pratiques de structure d’URL pour Google](https://developers.google.com/search/docs/crawling-indexing/url-structure) et [Bonnes pratiques relatives à l’optimisation pour les moteurs de recherche d’images Google](https://developers.google.com/search/docs/appearance/google-images)

### Améliorez dynamiquement les images et créez des effets visuels à l’aide de commandes

**Analyse de cas :** *Appliquez des effets visuels riches aux images.*

Dynamic Media propose une suite de commandes permettant d’améliorer les images et de créer des effets visuels de manière dynamique, sans avoir besoin de plusieurs ressources statiques. Vous trouverez ci-dessous une brève explication de quelques-uns de ces processus et quelques exemples pour vous guider :

#### Effets dans l’image source

| Tâche | Que faire |
| --- | --- |
| **Télécharger et publier votre image d&#39;origine** | ・ Commencez par télécharger l’image d’origine dans Dynamic Media.<br> ・ Assurez-vous qu’il est publié et accessible via une URL.<br> ・ Dans cet exemple, une image de stock d’une montre avec un arrière-plan blanc (appelons-la &quot;Image X&quot;) est téléchargée vers Dynamic Media.<br>[https://s7g2.scene7.com/is/image/genaibeta/watch-silver-offer](https://s7g2.scene7.com/is/image/genaibeta/watch-silver-offer) |
| **Créer un masque** | ・ Développer un masque qui définit le sujet (la zone dans laquelle vous souhaitez appliquer des effets) et l&#39;arrière-plan (la zone que vous souhaitez modifier).<br>[https://s7g2.scene7.com/is/image/genaibeta/watch-silver-offer-maskps](https://s7g2.scene7.com/is/image/genaibeta/watch-silver-offer-maskps)<br> ・ les masques sont généralement des images en niveaux de gris, où le blanc représente l’objet et le noir représente l’arrière-plan. Vous pouvez créer des masques à l’aide d’outils tels qu’Adobe Photoshop.<br>Vous souhaitez en savoir plus ? Accédez à [Création et modification d’un masque rapide dans Photoshop](https://helpx.adobe.com/in/photoshop/using/create-temporary-quick-mask.html).<br> ・ Pour &quot;Image X&quot;, créez un masque qui décrit précisément le sujet que vous souhaitez améliorer. Par exemple, une personne, un objet, etc. |
| **Appliquer les commandes URL Dynamic Media pour les effets** | Une fois que vous avez votre masque, utilisez les commandes URL pour appliquer des effets tels que des ombres portées ou modifiez la couleur d’arrière-plan en &quot;Image X&quot;. Voici deux exemples :<br><br> ・ **Effet ombre portée :**<br> Pour ajouter un effet ombre portée le long de la limite du sujet, modifiez l’URL comme suit :<br>[https://s7g10.scene7.com/is/image/genaibeta/watch-silver-offer?mask=watch-silver-offer-maskps&amp;maskUse=invert&amp;effect=-1&amp;pos=100,100&amp;op_blur=75&amp;op_grow=1&amp;opac=25](https://s7g10.scene7.com/is/image/genaibeta/watch-silver-offer?mask=watch-silver-offer-maskps&amp;maskUse=invert&amp;effect=-1&amp;pos=100,100&amp;op_blur=75&amp;op_grow=1&amp;opac=25)<br>Dans cette URL, le paramètre `$shadow$` crée l’effet ombre, et `color=0,0,0` définit la couleur ombre sur noir.<br> ・ **Changement de couleur d’arrière-plan :**<br> Pour modifier la couleur d’arrière-plan, utilisez l’URL avec une autre valeur de couleur d’arrière-plan :<br>[https://s7g10.scene7.com/is/image/genaibeta/watch-silver-offer?mask=watch-silver-offer-maskps&amp;maskUse=invert&amp;maskUse=invert&amp;color=255,255,0](https://s7g10.scene7.com/is/image/genaibeta/watch-silver-offer?mask=watch-silver-offer-maskps&amp;maskUse=invert&amp;maskUse=invert&amp;color=255,255,0)<br> Dans cet exemple, `color=255,255,0` définit la couleur d’arrière-plan sur jaune. Modifiez l’arrière-plan d’une couleur spécifique pour l’impact visuel. |

#### Ajouter une bordure d’image

Dynamic Media vous permet de manipuler des images directement via des URL, ce qui en fait un outil puissant pour créer des expériences numériques dynamiques. Voici quelques exemples. Commençons par l’URL de l’image d’origine suivante : [https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel](https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel).

| Tâche | Que faire |
| --- | --- |
| **Bordure blanche** | Pour ajouter une bordure blanche, utilisez l’URL suivante :<br>[https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&amp;extend=10,10,10,10](https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&amp;extend=10,10,10,10)<br>Dans cette URL, le paramètre `extend=10,10,10,10` spécifie la taille de bordure de dix pixels sur tous les côtés. |
| **Goutte le long de la bordure blanche** | Pour ajouter un effet de flou le long de la bordure blanche, vous pouvez modifier l’URL comme suit :<br>[https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&amp;extend=10,10,10,10&amp;effect=-1&amp;op_blur=60&amp;color=0,0,0](https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&amp;extend=10,10,10,10&amp;effect=-1&amp;op_blur=60&amp;color=0,0,0)<br>Dans cette URL, le paramètre `effect=-1` applique l’effet de flou, et `op_blur=60` contrôle l’intensité du flou. |
| **Déposer l’effet d’ombre le long de la limite extérieure** | Pour ajouter un effet d’ombre portée le long de la limite extérieure, utilisez cette URL :<br>[https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&amp;extend=10,10,10,10&amp;effect=-1&amp;$shadow$&amp;color=0,0,0](https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&amp;extend=10,10,10,10&amp;effect=-1&amp;$shadow$&amp;color=0,0,0)<br>Le paramètre `$shadow$` crée l’effet d’ombre, et `color=0,0,0` définit la couleur d’ombre sur le noir. |

N’hésitez pas à tester ces URL pour obtenir les effets visuels souhaités.

#### Création d’incrustations d’image

Si vous souhaitez superposer un logo ou une icône à une image existante, Dynamic Media offre une méthode simple pour y parvenir à l’aide des commandes d’URL. Faisons tomber les marches.

| Étape | Que faire |
| --- | --- |
| **Télécharger et publier l’image de base** | Tout d’abord, téléchargez et publiez l’image de base sur laquelle vous souhaitez superposer le logo ou l’icône. Vous pouvez utiliser n’importe quelle image comme base.<br>Par exemple, voici une image de base :<br>[https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa](https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa). |
| **Télécharger et publier le logo ou l&#39;image d&#39;icône** | Ensuite, téléchargez et publiez l’image que vous souhaitez superposer sur l’image de base. Cette image doit être un fichier PNG transparent avec le logo ou l’icône à superposer.<br>Voici l’image PNG transparente d’un objet étoile avec des effets de transparence qui vont être superposés :<br>[https://s7g2.scene7.com/is/image/genaibeta/decorate-star](https://s7g2.scene7.com/is/image/genaibeta/decorate-star) |
| **Appliquer l’URL Dynamic Media** | Créez maintenant une URL Dynamic Media qui combine l’image de base et le logo ou l’image d’icône. Pour ce faire, vous pouvez utiliser des commandes URL.<br>La structure d’URL ressemble à quelque chose comme ceci :<br>[https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa?layer=1&amp;src=decorate-star&amp;scale=1.25&amp;posN=0.33,-.25&amp;fmt=png](https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa?layer=1&amp;src=decorate-star&amp;scale=1.25&amp;posN=0.33,-.25&amp;fmt=png)<br>où la ressource<br> ・ `hotspotRetailBaseImage` est l’image de base.<br> ・ `starxp` est l&#39;image logo/icône.<br> ・ `layer=1` indique que le logo ou l’icône doit être superposé sur l’image de base.<br> ・ `scale=1.25` ajuste la taille du logo/de l&#39;icône.<br> ・ `posN=0.33,-.25` détermine la position du logo/de l’icône par rapport à l’image de base.<br> ・ `fmt=png` garantit que la sortie est au format PNG. |

Que savoir plus ? Accédez à [src](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-src) pour plus d’informations sur la commande `src` et les autres commandes d’URL Dynamic Media.


#### Recouvrement du texte promotionnel

Vous trouverez ci-dessous les étapes de superposition d’un message promotionnel sur une image à l’aide d’HTML et de CSS.

| Étape | Que faire |
| --- | --- |
| **Télécharger et publier l’image de base** | Tout d’abord, téléchargez et publiez l’image de base sur laquelle vous souhaitez superposer le texte. Vous pouvez utiliser n’importe quelle image de votre choix. Par exemple, voici un exemple d’image de base :<br>[https://s7g2.scene7.com/is/image/genaibeta/leather-sofa](https://s7g2.scene7.com/is/image/genaibeta/leather-sofa)<br> |
| **Appliquer les opérateurs de texte Dynamic Media** | Dynamic Media vous permet d’appliquer des opérateurs de texte pour superposer du texte dynamique directement sur l’image. L’exemple d’URL suivant illustre cette fonctionnalité :<br>[https://s7g10.scene7.com/is/image/genaibeta/leather-sofa?layer=1&amp;posN=-0.3,-0.455&amp;text=%7b\rtf1\ansi%7b\fonttbl%7b\f0+Arial;%7d%7d%7b\colortbl+\red255\green255\blue255;%7d\copyfit1000\vertalc\qc%7b\cf0\fs42+New+Collection%7d%7d&amp;size=370,70&amp;textAttr=13 0&amp;bgcolor=FF333&amp;wid=600&amp;hei=600](https://s7g10.scene7.com/is/image/genaibeta/leather-sofa?layer=1&amp;posN=-0.3,-0.455&amp;text=%7b\rtf1\ansi%7b\fonttbl%7b\f0+Arial;%7d%7d%7b\colortbl+\red255\green255\blue255;%7d\copyfit1000\vertalc\qc%7b\cf0\fs42+New+Collection%7d%7d&amp;size=370,70&amp;textAttr=130&amp;bgcolor=FF3 333&amp;wid=600&amp;hei=600) |

#### Redimensionnement et recadrage pour divers cas d’utilisation

##### Principes de base du redimensionnement des images

Le redimensionnement de l’image implique de modifier les dimensions, la résolution et la taille de fichier d’une image. Voici quelques points essentiels à prendre en compte :

* **Composition en pixels :**
Les images numériques se composent de petits points appelés pixels. Lorsqu’une image est créée, elle présente un nombre spécifique de pixels. Le redimensionnement implique l’ajout ou la soustraction de pixels pour modifier les dimensions, la résolution et la taille de fichier de l’image.
* **Format :**
Le maintien du rapport L/H (relation entre largeur et hauteur) est essentiel pour éviter la distorsion. Si vous agrandissez (mise à l’échelle) ou réduisez (mise à l’échelle) une image, la conservation des proportions garantit la cohérence visuelle.
* **Considérations sur la qualité :**
Le redimensionnement peut avoir une incidence sur la qualité de l’image. Évitez la mise à l’échelle drastique, car elle peut conduire à la pixellisation. Envisagez plutôt de reproduire l’image à une taille et une résolution plus grandes. Pour les images plus petites, utilisez les outils appropriés pour maintenir la résolution.

##### Recadrage et redimensionnement

Le recadrage et le redimensionnement sont des techniques de Dynamic Media qui vous permettent de transformer des images en fonction de divers cas d’utilisation, qu’il s’agisse de créer des miniatures, des images d’affichage de produit ou des bannières.

* **Recadrage :**
Cela implique la suppression d’une partie d’une image pour modifier sa composition et sa mise en forme. Elle ne modifie pas les dimensions globales, mais se concentre sur un domaine spécifique.
* **Redimensionnement :**
Ajuste les dimensions, la résolution et la taille de fichier de l’image entière tout en conservant les proportions.

Examinons un cas pratique qui implique l’image suivante du salon :

* **Image originale du salon :**
  [https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa](https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa)
* **Miniature (200 px 200 px) :**
Version plus petite adaptée au chargement ou à l’affichage rapide.
  [https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=200&amp;hei=200&amp;fit=crop](https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=200&amp;hei=200&amp;fit=crop)
* **Miniature avec recadrage (200 px 200 px) :**
Recadré pour se concentrer sur le canapé.
  [https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=200&amp;hei=200&amp;cropN=.24,.24,.6,.72&amp;fit=crop](https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=200&amp;hei=200&amp;cropN=.24,.24,.6,.72&amp;fit=crop)
* **Image d’affichage du produit (800 px 600 px) :**
Recadré et redimensionné pour présenter le canapé.
  [https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=800&amp;hei=600&amp;cropN=.24,.24,.6,.72&amp;fit=crop](https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=800&amp;hei=600&amp;cropN=.24,.24,.6,.72&amp;fit=crop)
* **Bannière (1720 px 820 px) :**
Dérivé de l&#39;image originale, mettant l&#39;accent sur la pièce.
  [https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=1720&amp;hei=820&amp;cropN=0,.1,1,1&amp;fit=crop](https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=1720&amp;hei=820&amp;cropN=0,.1,1,1&amp;fit=crop)

N’hésitez pas à explorer ces variations en fonction de vos besoins spécifiques.
Vous souhaitez en savoir plus sur les commandes disponibles dans une URL ? Accédez à [Référence de commande](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference).

### Diffuser des images de GIF

**Analyse de cas :** *Diffusion de GIFs à l’aide de Dynamic Media*

Vous pouvez charger et diffuser des GIFs via Dynamic Media. Pour effectuer le rendu d’un GIF animé, remplacez `is/image` par `is/content` dans l’URL. Par exemple, si vous avez téléchargé `abc.gif`, utilisez les éléments suivants :

* Ce chemin d’accès URL affiche une vue statique du GIF :

  ```
  https://your.domain.com/is/image/yourfolder/abc
  ```

* Ce chemin d’URL effectue le rendu de la vue d’animation du GIF :

  ```
  https://your.domain.com/is/content/yourfolder/abc
  ```

>[!NOTE]
>
>Lors de l’utilisation de `is/content` dans le chemin d’URL, les commandes de transformation d’image ne sont pas appliquées à la ressource.

### Publish d’une vidéo pour mon site web

**Analyse de cas :** *Publiez rapidement une vidéo pour un site marketing.*

* **Sélectionner un profil vidéo :**
Tout d’abord, dans Dynamic Media, vous devez sélectionner un profil vidéo approprié. Vous pouvez opter pour le profil *Codage vidéo adaptatif* disponible dans AEM Assets sous Profils vidéo. Ces paramètres de codage prédéfinis garantissent que votre vidéo est optimisée pour la lecture sur divers appareils et conditions de bande passante. Vous pouvez également créer votre propre profil de vidéo adaptative.
* **Attribuer le profil :**
Affectez le profil vidéo sélectionné aux dossiers dans lesquels la vidéo va être chargée. Cette étape permet de s’assurer que les paramètres de codage corrects sont appliqués pendant le processus de téléchargement.
* **Télécharger la vidéo d’origine :**
Téléchargez le fichier vidéo d’origine. Assurez-vous que c&#39;est une vidéo haute résolution de bonne qualité. Plus la vidéo source est bonne, plus le résultat final est bon.
* **Aperçu et publication :**
Prévisualisez la vidéo afin de vous assurer que tout se présente comme prévu. Une fois satisfait, allez-y et publiez-le. Cette étape rend la vidéo accessible à votre audience.
* **Lien ou intégration :**
Après la publication, vous disposez de deux options.

   * **Lien direct :**
Utilisez l’URL fournie pour créer un lien direct vers la vidéo. Liez-le de manière appropriée sur votre site marketing.
   * **Incorporer la vidéo :**
Copiez le code incorporé fourni et collez-le dans l’HTML de votre page web où vous souhaitez que la vidéo apparaisse. Cela permet à la vidéo d’être lue directement sur votre site.

Vous souhaitez en savoir plus ? Accédez à [Vidéo](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/video).

### Configuration de vidéos pour une qualité optimale et un engagement

**Analyse de cas :** *Configurez des vidéos pour la meilleure qualité et la meilleure interaction.*

Pour garantir la qualité et l’engagement optimales de vos vidéos, pensez à mettre en oeuvre une combinaison des stratégies de bonnes pratiques suivantes :

* **Utilisation de la visionneuse vidéo HTML5 intégrée :**
Les paramètres prédéfinis de la visionneuse vidéo Dynamic Media HTML5 sont des lecteurs vidéo fiables. Utilisez-les pour éviter les problèmes courants liés à la lecture vidéo et aux appareils mobiles HTML5.
Ces paramètres prédéfinis répondent à des défis tels que la diffusion en continu à débit adaptatif et la portée limitée du navigateur de bureau.
Vous souhaitez en savoir plus ? Accédez à [Bonne pratique : utilisation de la visionneuse de vidéos HTML 5](/help/assets/dynamic-media/video.md#best-practice-using-the-html-video-viewer).

* **Utiliser des profils vidéo Dynamic Media :**
Les profils vidéo dans Dynamic Media permettent une gestion efficace de la vidéo, une qualité cohérente et une diffusion en continu adaptative.
Vous souhaitez en savoir plus ? Accédez à [Profils vidéo Dynamic Media](/help/assets/dynamic-media/video-profiles.md).

* **Suivez les bonnes pratiques relatives au codage vidéo :**
Appliquez des profils de codage vidéo qui conservent la qualité de la vidéo d’origine sans mise à l’échelle excessive lors du codage.
Vous souhaitez en savoir plus ? Accédez à [Bonnes pratiques pour le codage des vidéos](/help/assets/dynamic-media/video.md#best-practices-for-encoding-videos).

* **Adoptez la diffusion en continu adaptative au lieu de la diffusion en continu progressive :**
La diffusion en continu adaptative ajuste la qualité vidéo en fonction de la vitesse de connexion Internet de la visionneuse et des fonctionnalités de l’appareil.
Il utilise des protocoles tels que HLS (HTTP Live Streaming) ou DASH (`Dynamic Adaptive Streaming over HTTP`) pour garantir une qualité de lecture optimale.
Contrairement à la diffusion en continu progressive, qui fournit des vidéos de manière linéaire, la diffusion en continu adaptative réduit la mise en mémoire tampon et offre une expérience de visionnage transparente.

* **Activer DASH sur votre compte (Digital Adaptive Streaming over HTTP) :**
DASH diffuse dynamiquement le contenu vidéo par le biais de la diffusion en continu adaptative.
Pour activer DASH, créez un ticket d’assistance pour votre environnement.
Vous souhaitez en savoir plus ? Accédez à [Activer DASH sur votre compte Dynamic Media](/help/assets/dynamic-media/video.md#enable-dash).

### Internationalisation de vidéos pour une utilisation multilingue

**Analyse de cas :** *Préparer les vidéos à la consommation multilingue.*

L&#39;internationalisation des vidéos destinées à une consommation multilingue est essentielle pour atteindre une audience mondiale. Dynamic Media fournit des fonctionnalités qui peuvent vous aider à atteindre cet objectif.

* **Télécharger vos vidéos :**
   * Créez tout d’abord un profil de codage vidéo. Vous pouvez utiliser le profil de codage vidéo adaptatif prédéfini fourni avec Dynamic Media ou créer votre propre profil personnalisé.
   * Associez le profil de traitement vidéo à un ou plusieurs dossiers dans lesquels vous chargez les vidéos issues de sources originales.
   * Chargez les vidéos issues de sources originales dans ces dossiers. Dynamic Media les code en fonction du profil de traitement vidéo affecté.
   * Dynamic Media prend principalement en charge les vidéos courtes (jusqu’à 30 minutes) avec une résolution minimale supérieure à 25 × 25. Les fichiers vidéo jusqu’à 15 Go chacun peuvent être téléchargés1.

* **Gérer vos vidéos :**
   * Organisez, parcourez et recherchez des ressources vidéo dans AEM.
   * Prévisualisez et publiez des ressources vidéo.
   * Affichez la vidéo source et ses rendus codés avec les miniatures associées.
   * Modifiez les propriétés vidéo telles que le titre, la description et les balises2.

* **Localisation :**
   * Pour chaque zone géographique/langue cible, créez des pistes audio et des sous-titres.
   * Ajoutez ces pistes audio et de sous-titres à vos vidéos à partir de l’interface AEM.
   * Lorsque les utilisateurs lisent les vidéos, ils peuvent sélectionner la langue de leur choix pour l’audio et les sous-titres.

* **Publication :**
   * Si vous utilisez AEM comme système de gestion de contenu web (WCM), vous pouvez directement ajouter des vidéos à vos pages web.
   * Si vous utilisez un système WCM tiers, vous pouvez lier ou incorporer des vidéos dans vos pages web à l’aide d’URL ou de codes incorporés.

Vous souhaitez en savoir plus ? Accédez à [À propos de la prise en charge de plusieurs sous-titres et pistes audio pour les vidéos dans Dynamic Media](/help/assets/dynamic-media/video.md#about-msma) ou regardez [Ajouter plusieurs sous-titres et pistes audio à une vidéo](https://delivery-p106302-e1008131.adobeaemcloud.com/adobe/assets/urn:aaid:aem:daf9a222-9f7f-4333-b167-98cb4c63a1f8/play) (1 minute, 41 secondes).


## Diffuser des ressources aux clients

### Optimisation des tailles d’image et réduction des temps de chargement des pages

**Analyse de cas :** *Optimisez la taille des images pour n’importe quel navigateur ou écran et réduisez le temps de chargement des pages.*

L’imagerie dynamique Dynamic Media est un puissant outil qui améliore les performances de diffusion des images en optimisant automatiquement le format, la taille et la qualité de l’image en fonction des fonctionnalités du navigateur du client.

Adobe recommande d’utiliser les fonctionnalités de l’imagerie dynamique plutôt que de définir manuellement le format de l’image sur `webp` ou `avif`. La raison est la suivante :

* **Compatibilité du navigateur :**
L’imagerie dynamique garantit que le format d’image diffusé est compatible avec le navigateur de l’utilisateur.
* **Compression optimale :**
Il sélectionne le meilleur format de compression en fonction des conditions réseau et de la résolution d’écran du navigateur.
* **Formats modernes :**
Bien que `avif` soit un format plus récent offrant une meilleure compression, il n’est pas encore universellement pris en charge sur tous les navigateurs.
* **Bonnes pratiques :**
Pour garantir le meilleur format optimisé pour le web, vous pouvez faire confiance à l’imagerie dynamique pour effectuer la sélection du format plutôt que manuellement à l’aide des commandes `fmt=webp` ou `fmt=avif`.

Grâce à l’imagerie dynamique, vous pouvez vous assurer que vos images sont diffusées de la manière la plus efficace possible, en fonction de l’environnement de navigation de chaque utilisateur. Cette approche simplifie le processus et peut améliorer les performances en termes de temps de chargement des images et d’expérience utilisateur globale.

Vous souhaitez en savoir plus ? Accédez à [Smart Imaging](/help/assets/dynamic-media/imaging-faq.md).

### Diffusion des ressources aux clients

**Analyse de cas :** *Après la publication d’un nouveau contenu ou le remplacement d’un contenu existant, comment peut-on s’assurer que les modifications apparaissent immédiatement sur le réseau de diffusion de contenu ?*

Le réseau de diffusion de contenu (CDN) met en cache des ressources Dynamic Media pour une diffusion rapide aux clients. Lorsque des mises à jour sont apportées à ces ressources, il est important que les modifications prennent effet immédiatement sur le site web. En purgeant ou en invalidant le cache CDN, les ressources diffusées par Dynamic Media peuvent être mises à jour rapidement. Cette approche élimine la nécessité d’attendre que le cache arrive à expiration en fonction de la valeur TTL (Time To Live), généralement définie sur dix heures. Selon votre cas d’utilisation spécifique, vous pouvez mettre à jour les paramètres TTL (durée de vie) du réseau CDN en conséquence.

Vous souhaitez en savoir plus ? Accédez à [Invalider le cache CDN au moyen de Dynamic Media](/help/assets/dynamic-media/invalidate-cdn-cache-dynamic-media.md).
