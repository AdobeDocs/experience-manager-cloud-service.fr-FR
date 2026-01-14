---
title: Bonnes pratiques relatives à Dynamic Media
description: Découvrez les bonnes pratiques relatives à l’utilisation d’images et de vidéos dans Dynamic Media ainsi que les bonnes pratiques relatives aux visionneuses Dynamic Media.
contentOwner: Rick Brough
products: Experience Manager as a Cloud Service
topic-tags: introduction,administering
content-type: reference
feature: Adaptive Streaming, Best Practices, Smart Imaging, Image Profiles, Rulesets, Viewers, Smart Crop, SEO Optimization, Publishing, Video, Renditions, Asset Management
role: User, Admin
mini-toc-levels: 4
exl-id: 39e491bb-367d-4c72-b4ca-aab38d513ac5
source-git-commit: 281a8efcd18920dd926d92db9c757c0513d599fd
workflow-type: tm+mt
source-wordcount: '4048'
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

{{see-also-dm}}

Les entreprises sont confrontées à une explosion de canaux et d’appareils pour interagir avec les utilisateurs. Le parcours client couvre les magasins physiques, le web, les appareils mobiles, les médias sociaux, les e-mails et le commerce. Pour répondre à cette demande, Dynamic Media sur Adobe Experience Manager (AEM) offre une solution complète. Il optimise la diffusion des ressources, gère la personnalisation et garantit des expériences cohérentes, performantes et alignées sur la marque sur les canaux et les appareils.

Voici quelques-uns des principes clés de Dynamic Media :

* **Approche de fichier unique :** avec Dynamic Media, vous stockez un fichier source principal et toutes les variations de taille et tous les effets visuels sont créés et optimisés dynamiquement au moment de la diffusion. Cette approche permet de réduire les coûts de stockage et d’éliminer la complexité des workflows.
* **Vraiment global :** l’imagerie dynamique, appliquée pendant la diffusion du contenu, réduit considérablement la taille de l’image et le poids de la page sans compromettre la qualité visuelle. Il est optimisé pour la bande passante du réseau et les rapports pixel d’appareil.
* **Optimisé par l’IA :** recadrage intelligent, une fonctionnalité pilotée par l’IA, automatise le recadrage des points ciblés des images et des vidéos. Il élimine l’effort manuel et s’adapte efficacement à l’utilisation en entreprise.
* **Vidéo facile :** chargez des vidéos issues de sources originales dans Dynamic Media et diffusez-les de manière adaptative sur plusieurs langues avec un son descriptif.
* **Bibliothèque de visionneuses Experience Manager :** personnalisez et marquez les visionneuses d’expériences pour les images et les vidéos. Ces visionneuses s’intègrent de manière transparente à vos expériences digitales.
* **Prise en charge des formats émergents :** Dynamic Media permet de diffuser des expériences 3D et panoramiques.

À mesure que vous explorez le [Parcours Dynamic Media](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/assets/dynamicmedia/dm-journey/dm-journey-part1), une révision de la liste consolidée des bonnes pratiques ci-dessous peut vous aider à tirer le meilleur parti de ses fonctionnalités. Adaptez ces bonnes pratiques Dynamic Media à votre contexte et aux exigences de votre projet spécifiques afin d’optimiser vos expériences sur l’ensemble des canaux et appareils.

<!-- In Dynamic Media on AEM, there are sets of methods, techniques, and guidelines that can help you maximize the potential of your rich media content. These best practices can lead to optimal results and increase efficiency in your use of Dynamic Media. They represent the most efficient and effective courses of action in a particular situation. They also unlock high value for your audience and deliver high-quality, engaging content. -->

>[!IMPORTANT]
>
>Les bonnes pratiques relatives à Dynamic Media décrites dans cet article peuvent évoluer au fil du temps à mesure que de nouvelles technologies émergent dans Dynamic Media. Les informations ci-dessous sont à jour pour la dernière version de Dynamic Media.


## Ingestion de ressources dans Dynamic Media

**Analyse de rentabilité :** *gérez efficacement d’importants volumes de ressources et assurez-vous que seul le contenu pertinent et approuvé est diffusé aux utilisateurs finaux.*

Rationalisez la gestion d’un grand nombre de ressources de manière efficace. Assurez-vous que seul le contenu autorisé approprié atteint vos utilisateurs finaux à l’aide des fonctionnalités **Synchronisation sélective** et **Publication sélective** de Dynamic Media.

* **Synchronisation sélective :**
Une fonctionnalité proactive qui vous permet de choisir les ressources à synchroniser avec Dynamic Media. Par exemple, vous pouvez décider de synchroniser uniquement les dossiers contenant des ressources qui ont reçu l’approbation finale. Ce workflow vous permet de contrôler quelles ressources sont en cours de préparation pour la diffusion à vos clients.

* **Publication sélective :**
Après la synchronisation de vos ressources, la publication sélective vous permet de contrôler quelles ressources sont visibles pour vos clients. Cela signifie que vous pouvez déterminer les ressources approuvées qui sont réellement diffusées par l’intermédiaire de vos canaux, afin de vous assurer que vos clients ne voient que le contenu le meilleur et le plus pertinent.

Ces deux bonnes pratiques vous aident à mieux contrôler, gouverner et optimiser la productivité de votre contenu multimédia enrichi.

Vous souhaitez en savoir plus ? Accédez à [Configuration de la publication sélective au niveau des dossiers dans Dynamic Media](/help/assets/dynamic-media/selective-publishing.md).


## Visionneuses Dynamic Media

Les bonnes pratiques relatives aux visionneuses Dynamic Media sont des instructions essentielles conçues pour optimiser les performances, les fonctionnalités et l’expérience utilisateur des ressources Dynamic Media sur AEM. Ces pratiques garantissent que les ressources sont correctement synchronisées, publiées et configurées afin d’utiliser toutes les fonctionnalités de Dynamic Media.

En suivant ces bonnes pratiques, vous pouvez obtenir une intégration transparente, une gestion efficace des ressources et des interactions améliorées des observateurs. La synchronisation des ressources, l’utilisation du recadrage intelligent et le respect des directives d’inclusion de fichiers JavaScript sont autant de pratiques importantes. Ces recommandations permettent de maintenir l’intégrité et la fiabilité de la diffusion multimédia sur différentes plateformes et appareils.

* **Synchroniser la visionneuse Assets :**
Assurez-vous que toutes les ressources de la visionneuse sont synchronisées avec Dynamic Media avant d’utiliser le lecteur.

   * Accédez à la page du gestionnaire d’échantillons à l’adresse `/libs/dam/gui/content/s7dam/samplemanager/samplemanager`. Cette page vous permet de resynchroniser les ressources d’une visionneuse, y compris les icônes prêtes à l’emploi, les fichiers CSS et les paramètres prédéfinis.
   * Si vous rencontrez des problèmes avec les visionneuses, consultez l’article [ Dépannage des visionneuses Dynamic Media ](/help/assets/dynamic-media/troubleshoot-dm.md#viewers).

* **Publier Assets :**
Assurez-vous que les ressources sont publiées avant de les afficher dans les visionneuses de diffusion.
* **La Lecture Automatique Des Vidéos Est Désactivée :**
Pour la fonctionnalité de lecture automatique dans les vidéos, utilisez les paramètres vidéo en mode silencieux, car les navigateurs limitent la lecture des vidéos avec le volume.
* **Recadrage intelligent :**
Utilisez le composant Image v3 pour le recadrage intelligent afin d’améliorer la présentation des ressources d’image.
* **Inclusion de fichier JavaScript :**
Incluez uniquement le fichier JavaScript de la visionneuse principale sur votre page. Évitez de référencer d’autres fichiers JavaScript que la logique d’exécution de la visionneuse peut télécharger. Plus précisément, ne liez pas directement à la bibliothèque de `Utils.js` SDK HTML5 à partir du chemin de contexte `/s7viewers` (connu sous le nom d’inclusion SDK consolidée). La logique de la visionneuse gère l’emplacement des bibliothèques de visionneuse d’exécution `Utils.js` ou similaires, qui peuvent changer entre les versions. Adobe ne conserve pas les anciennes versions des inclusions de visionneuse secondaire sur le serveur. Par conséquent, le fait de les référencer directement peut interrompre la fonctionnalité de la visionneuse dans les futures mises à jour.
* **Instructions d’incorporation :**
Utilisez la documentation pour obtenir des instructions d’intégration spécifiques à chaque visionneuse.
Vous souhaitez en savoir plus ? Accédez à [Visionneuses pour AEM Assets](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/c-html5-s7-aem-asset-viewers).
* **Tutoriel et exemples SDK :**
Consultez le [Tutoriel sur la visionneuse SDK](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/library/c-tutorial) et [les exemples d’applications HTML5 SDK](https://s7d9.scene7.com/s7sdk/2024.5/docs/jsdoc/index.html) pour une compréhension approfondie des API des composants SDK.


## Préparation des ressources pour la diffusion

### Organisation des ressources

**Business case :** *Organisez efficacement les ressources pour rationaliser les workflows.*

Pour une organisation efficace des ressources qui simplifie les workflows, utilisez une ou plusieurs des bonnes pratiques suivantes :

* **Organisation des ressources dans des dossiers :**
L’organisation efficace des ressources implique de les classer dans des dossiers, comme l’organisation des fichiers sur un ordinateur. Pour un traitement des ressources efficace, il est essentiel de nommer, de structurer les sous-dossiers et de gérer les fichiers au sein de ces dossiers. L’implémentation de conventions de nommage systématiques et de pratiques relatives aux métadonnées optimise l’utilité de votre référentiel de ressources numériques.
Vous souhaitez en savoir plus ? Accédez à [Organisation des ressources dans des dossiers](/help/assets/organize-assets.md#organize-using-folders).
* **Organisation des ressources à l’aide de balises :**
Le balisage des ressources améliore la recherche, la création de collections et le classement des recherches. L’IA d’Adobe utilise un algorithme d’auto-apprentissage pour le balisage précis, ce qui permet de récupérer rapidement les ressources. L’IA d’Adobe reconnaît et attribue également les balises pertinentes aux ressources, y compris les balises personnalisées, ce qui simplifie la gestion des ressources grâce au balisage descriptif automatique.
Vous souhaitez en savoir plus ? Accédez à [ Organisation des ressources à l’aide de balises ](/help/assets/organize-assets.md#use-tags-to-organize-assets).
* **Organisation des ressources sous forme de collections :**
Dynamic Media et Experience Manager Assets permettent la création, la modification et le partage efficaces de collections de ressources entre les utilisateurs. Vous pouvez établir différents types de collections, notamment des listes statiques et des compilations dynamiques basées sur des recherches. Ces types de collections peuvent être partagés à différents emplacements avec des droits d’accès et de modification personnalisables.
Vous souhaitez en savoir plus ? Accédez à [Organisation des ressources sous forme de collections](/help/assets/manage-collections.md).
* **Organisation des ressources à l’aide de profils :**
Un profil de traitement automatise la gestion des ressources dans les dossiers désignés, ce qui simplifie l’organisation. La normalisation des métadonnées, des noms de fichiers et des structures de dossiers permet une application cohérente et précise de ces profils à mesure que votre collection de ressources numériques se développe.
Vous souhaitez en savoir plus ? Accédez à [Organisation des ressources à l’aide de profils](/help/assets/organize-assets.md#organize-to-use-profiles).



### Optimiser la qualité des images

**Analyse de rentabilité :** *Obtenez des images de bonne qualité à partir de Dynamic Media.*

L’amélioration de la qualité d’image nécessite une attention particulière à divers facteurs. Ce processus peut être long. Cependant, il existe des pratiques éprouvées qui peuvent vous aider à obtenir des résultats souhaitables. Parmi ces bonnes pratiques, citons notamment la manière d’obtenir un dimensionnement et un accentuation optimaux des images, ainsi que les meilleurs formats d’image à utiliser.

Vous souhaitez en savoir plus ? Accédez à [Bonnes pratiques pour optimiser la qualité de vos images](/help/assets/dynamic-media/best-practices-for-optimizing-the-quality-of-your-images.md).

Comme la perception de la qualité de l’image varie d’une personne à l’autre, une approche systématique de l’expérimentation est parfois essentielle pour obtenir des résultats souhaitables. Adobe Experience Manager facilite ce processus avec plus de 100 commandes Dynamic Media pour l’amélioration des images.

Vous souhaitez en savoir plus ? Regardez [instantané Dynamic Media](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-snapshot) (3 minutes, 17 secondes).

Pour évaluer l’impact de ces différentes commandes sur la qualité d’image, vous pouvez charger une image dans Dynamic Media, utiliser l’interface de l’outil à l’URL spécifiée et appliquer les commandes que vous souhaitez tester.

Envie de l&#39;essayer ? Launch [instantané Dynamic Media](https://snapshot.scene7.com/)

### Normaliser les styles appliqués aux images

**Analyse de rentabilité :** *normaliser efficacement le style et la transformation appliqués à mes ressources d’image.*

Utilisez régulièrement les paramètres d’image prédéfinis dans Dynamic Media afin d’ajuster de manière cohérente et dynamique les tailles, les formats et les propriétés des images. Considérez un paramètre prédéfini d’image comme une macro : il s’agit d’un ensemble nommé de commandes pour le dimensionnement et la mise en forme. Par exemple, si votre site a besoin d’images de produit dans différents formats et tailles, avec une compression spécifique pour les ordinateurs de bureau et les appareils mobiles, les paramètres d’image prédéfinis automatisent efficacement ce processus.

Envie de l&#39;essayer ? Accédez à [Principes de base de la création de paramètres d’image prédéfinis pour le rendu des ressources](/help/assets/dynamic-media/dm-journey-part2.md#dm-journey-e)

### Réglage de la mise au point et du cadrage des images et des vidéos

**Analyse de rentabilité :** *Assurez-vous que le principal point ciblé de mes images ou vidéos reste ciblé sur tous les appareils.*

Le recadrage intelligent est une fonctionnalité de Dynamic Media qui utilise l’IA d’Adobe, l’IA d’Adobe et la structure de machine learning pour automatiser le recadrage des images et des vidéos. Il détecte et se concentre intelligemment sur le sujet principal ou le point ciblé d’une image ou d’une vidéo. Cette intelligence permet de s’assurer que le point focal est conservé sur différents formats d’écran sur les ordinateurs de bureau et les appareils mobiles.

Il est recommandé de créer un profil d’image avec le recadrage intelligent. Dans le profil, vous pouvez définir différentes tailles d’écran et laisser l’IA dédiée à Adobe faire le reste, en veillant à ce que vos images et vidéos soient toujours optimisées pour l’appareil de la visionneuse.

Vous souhaitez en savoir plus ? Regardez les vidéos [Utilisation du recadrage intelligent avec AEM Assets Dynamic Media](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/assets/dynamic-media/images/smart-crop-feature-video-use) (6 minutes, 35 secondes) et [Utilisation du recadrage intelligent Dynamic Media pour la vidéo](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/assets/dynamic-media/video/dynamic-media-smart-crop-video) (6 minutes, 22 secondes).

### Améliorer les classements SEO

**Analyse de rentabilité :** *Configurez Dynamic Media pour obtenir de meilleurs classements SEO.*

Suivez régulièrement les recommandations suivantes pour vous assurer que vos images contribuent efficacement à votre stratégie globale d’optimisation du moteur de recherche (SEO).

* **Noms de fichiers image significatifs :**
Utilisez des noms de fichier descriptifs qui reflètent le contenu de l’image. Par exemple :

   * Utilisez `myCompany-Silver-Wrist-Watch`
   * *éviter* `myCompany_Silver_Wrist_Watch` ou `myCompanySilverWristWatch`

  Cela permet aux moteurs de recherche de comprendre le contexte de l’image et améliore l’optimisation du moteur de recherche. Google préfère les tirets aux traits de soulignement ou aux espaces dans un nom de fichier. Évitez également de concaténer des mots dans un nom de fichier.
* **Domaine personnalisé :**
Implémentez un domaine personnalisé qui inclut votre société ou votre nom de marque pour renforcer la reconnaissance et la confiance de la marque. Par exemple :

   * Utilisez `http://images.mycompany.com/is/image/companyname/`
   * *éviter* `https://s7d1.scene7.com/is/image/folder/AdobeStock_28563982`

* **Structure de dossiers compatible avec l’optimisation du moteur de recherche :**
Organisez vos images dans une structure de dossiers qui inclut le nom de votre société ou de votre marque pour une meilleure indexation, comme `http://images.mycompany.com/is/image/companyname/`.
* **Ensembles de règles Dynamic Media :**
Découvrez comment transformer de manière conditionnelle des URL en fonction de divers facteurs, ce qui améliore l’optimisation du moteur de recherche et l’expérience utilisateur.
Vous souhaitez en savoir plus ? Accédez à [Utilisation d’ensembles de règles pour transformer des URL](/help/assets/dynamic-media/using-rulesets-to-transform-urls.md).
* **Imagerie dynamique et recadrage intelligent :**
Utilisez les fonctionnalités d’imagerie dynamique et de recadrage intelligent de Dynamic Media pour diffuser des images optimisées et réactives. Cela permet non seulement d’améliorer les temps de chargement des pages, mais contribue également positivement aux classements SEO.
Vous souhaitez en savoir plus ? Accédez à [Imagerie dynamique](/help/assets/dynamic-media/imaging-faq.md) ou regardez [Utilisation du recadrage intelligent avec AEM Assets Dynamic Media](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/assets/dynamic-media/images/smart-crop-feature-video-use) (6 minutes, 35 secondes).

N’oubliez pas que ces bonnes pratiques s’alignent parfaitement sur les bonnes pratiques d’optimisation du moteur de recherche des images Google. Ces pratiques soulignent l’importance de fournir du contexte et de la clarté aux moteurs de recherche par le biais de conventions de nommage appropriées, de données structurées et d’une diffusion d’images optimisée.

Vous souhaitez en savoir plus ? Accédez à [ Bonnes pratiques relatives à la structure d’URL pour Google ](https://developers.google.com/search/docs/crawling-indexing/url-structure) et [Bonnes pratiques d’optimisation du moteur de recherche d’image Google](https://developers.google.com/search/docs/appearance/google-images)

### Amélioration dynamique des images et création d’effets visuels à l’aide de commandes

**Analyse de rentabilité :** *appliquer des effets visuels riches aux images.*

Dynamic Media propose une suite de commandes pour améliorer les images et créer des effets visuels de manière dynamique, sans avoir besoin de plusieurs ressources statiques. Vous trouverez ci-dessous de brèves explications de certains de ces processus et quelques exemples pour vous guider :

#### Effets dans l’image source

| Tâche | Que faire |
| --- | --- |
| **Chargez et publiez votre image d’origine** | <ul><li> Commencez par charger l’image d’origine dans Dynamic Media.</li><li> Assurez-vous qu’il est publié et accessible par le biais d’une URL.</li><li> Dans cet exemple, une image animée d’une montre avec un arrière-plan blanc (appelons-la « Image X ») est chargée dans Dynamic Media.<br>[https://s7g2.scene7.com/is/image/genaibeta/watch-silver-offer](https://s7g2.scene7.com/is/image/genaibeta/watch-silver-offer)</li></ul> |
| **Créer un masque** | <ul><li> Développez un masque qui définit le sujet (la zone où vous souhaitez appliquer des effets) et l&#39;arrière-plan (la zone à modifier).<br>[https://s7g2.scene7.com/is/image/genaibeta/watch-silver-offer-maskps](https://s7g2.scene7.com/is/image/genaibeta/watch-silver-offer-maskps)</li><li> Les masques sont généralement des images en niveaux de gris, où le blanc représente le sujet et le noir représente l’arrière-plan. Vous pouvez créer des masques à l’aide d’outils comme Adobe Photoshop.<br>Vous souhaitez en savoir plus ? Accédez à [ Création et modification d’un masque rapide dans Photoshop ](https://helpx.adobe.com/in/photoshop/using/create-temporary-quick-mask.html).</li><li> Pour « Image X », créez un masque qui décrit précisément le sujet que vous souhaitez améliorer. Par exemple, une personne, un objet, etc.</li></ul> |
| **Application de commandes URL Dynamic Media pour les effets** | Une fois que vous disposez de votre masque, utilisez les commandes d’URL pour appliquer des effets tels qu’une lueur extérieure ou modifiez la couleur d’arrière-plan en « Image X ». Voici deux exemples :<ul><li> **Effet de lueur extérieure :**<br> pour ajouter un effet de lueur extérieure le long de la limite de l’objet, modifiez l’URL comme suit :<br>[https://s7g10.scene7.com/is/image/genaibeta/watch-silver-offer?mask=watch-silver-offer-maskps&amp;maskUse=invert&amp;effect=-1&amp;pos=100,100&amp;op_blur=75&amp;op_grow=1&amp;opac=25](https://s7g10.scene7.com/is/image/genaibeta/watch-silver-offer?mask=watch-silver-offer-maskps&maskUse=invert&effect=-1&pos=100,100&op_blur=75&op_grow=1&opac=25)<br>Dans cette URL, les paramètres `op_blur`, `op_grow` et `opac` créent l’effet de lueur extérieure.</li><li> **Modification de la couleur d’arrière-plan :**<br> Pour modifier la couleur d’arrière-plan, utilisez l’URL avec une valeur de couleur d’arrière-plan différente :<br>[https://s7g10.scene7.com/is/image/genaibeta/watch-silver-offer?mask=watch-silver-offer-maskps&amp;maskUse=invert&amp;maskUse=invert&amp;color=255,255,0](https://s7g10.scene7.com/is/image/genaibeta/watch-silver-offer?mask=watch-silver-offer-maskps&maskUse=invert&maskUse=invert&color=255,255,0)<br> Dans cet exemple, `color=255,255,0` définit la couleur d’arrière-plan sur jaune. Modifiez l’arrière-plan avec une couleur spécifique pour l’impact visuel.</li></ul> |

#### Ajout d’une bordure d’image

Dynamic Media vous permet de manipuler des images directement par le biais d’URL. Il s’agit ainsi d’un outil puissant pour créer des expériences digitales dynamiques. Voici quelques exemples. Commençons par l’URL de l’image d’origine suivante : [https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel](https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel).

| Tâche | Que faire |
| --- | --- |
| **Bordure blanche** | Pour ajouter une bordure blanche, utilisez l’URL suivante :<br>[https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&amp;extend=10,10,10,10](https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&extend=10,10,10,10)<br>Dans cette URL, le paramètre `extend=10,10,10,10` spécifie la taille de la bordure de dix pixels sur tous les côtés. |
| **Flou le long de la bordure blanche** | Pour ajouter un effet de flou le long de la bordure blanche, vous pouvez modifier l’URL comme suit :<br>[https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&amp;extend=10,10,10,10&amp;effect=-1&amp;op_blur=60&amp;color=0,0,0](https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&extend=10,10,10,10&effect=-1&op_blur=60&color=0,0,0)<br>Dans cette URL, le paramètre `effect=-1` applique l’effet de flou et contrôle `op_blur=60` l’intensité du flou. |
| **Effet Ombre portée le long de la limite extérieure** | Pour ajouter un effet d&#39;ombre portée le long de la limite extérieure, utilisez cette URL :<br>[https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&amp;extend=10,10,10,10&amp;effect=-1&amp;$shadow$&amp;color=0,0,0](https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&extend=10,10,10,10&effect=-1&$shadow$&color=0,0,0)<br>Le paramètre `$shadow$` crée l&#39;effet d&#39;ombre et `color=0,0,0` définit la couleur d&#39;ombre sur le noir. |

N’hésitez pas à tester ces URL pour obtenir les effets visuels souhaités.

#### Création de superpositions d’images

Si vous souhaitez superposer un logo ou une icône sur une image existante, Dynamic Media offre un moyen simple d’y parvenir à l’aide de commandes d’URL. Démontons les marches.

| Étape | Que faire |
| --- | --- |
| **Charger et publier l’image de base** | Tout d’abord, chargez et publiez l’image de base sur laquelle vous souhaitez superposer le logo ou l’icône. Vous pouvez utiliser n’importe quelle image comme base.<br>Par exemple, voici une image de base :<br>[https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa](https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa). |
| **Charger et publier le logo ou l’image de l’icône** | Ensuite, chargez et publiez l’image à superposer sur l’image de base. Cette image doit être un fichier PNG transparent avec le logo ou l’icône à superposer.<br>Voici l’image PNG transparente d’un objet étoile avec des effets de transparence qui va être superposée :<br>[https://s7g2.scene7.com/is/image/genaibeta/decorate-star](https://s7g2.scene7.com/is/image/genaibeta/decorate-star) |
| **Application de l’URL Dynamic Media** | Créez à présent une URL Dynamic Media qui combine l’image de base et le logo ou l’image d’icône. Vous pouvez utiliser des commandes d’URL pour obtenir cet effet.<br>La structure de l’URL ressemble à ce qui suit :<br>[https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa?layer=1&amp;src=decorate-star&amp;scale=1.25&amp;posN=0.33,-.25&amp;fmt=png](https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa?layer=1&src=decorate-star&scale=1.25&posN=0.33,-.25&fmt=png)<br>où la ressource<ul><li> `hotspotRetailBaseImage` est l’image de base.</li><li> `starxp` est l’image du logo/de l’icône.</li><li> `layer=1` indique que le logo ou l’icône doit être superposé sur l’image de base.</li><li> `scale=1.25` ajuste la taille du logo/de l’icône.</li><li> `posN=0.33,-.25` détermine la position du logo/de l’icône par rapport à l’image de base.</li><li> `fmt=png` garantit que la sortie est au format PNG.</li></ul> |

Que savoir de plus ? Accédez à [src](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-src) pour plus d’informations sur la commande `src` et d’autres commandes d’URL Dynamic Media.


#### Recouvrement de texte promotionnel

Vous trouverez ci-dessous la procédure à suivre pour superposer un message texte promotionnel sur une image à l’aide d’HTML et de CSS.

| Étape | Que faire |
| --- | --- |
| **Charger et publier l’image de base** | Tout d’abord, chargez et publiez l’image de base sur laquelle vous souhaitez superposer le texte. Vous pouvez utiliser n’importe quelle image de votre choix. Par exemple, voici un exemple d’image de base :<br>[https://s7g2.scene7.com/is/image/genaibeta/leather-sofa](https://s7g2.scene7.com/is/image/genaibeta/leather-sofa)<br> |
| **Application d’opérateurs de texte Dynamic Media** | Avec Dynamic Media, vous pouvez appliquer des opérateurs de texte pour superposer du texte dynamique directement sur l’image. L’exemple d’URL suivant illustre cette fonctionnalité :<br>[https://s7g10.scene7.com/is/image/genaibeta/leather-sofa?layer=1&amp;posN=-0.3,-0.455&amp;text=%7b\rtf1\ansi%7b\fonttbl%7b\f0+Arial;%7d%7d%7b\colortbl+\red255\green255\blue255;%7d\copyfit1000\vertalc\qc%7b\cf0\fs42+New+Collection%7d%7d&amp;size=370,70&amp;textAttr=130&amp;bgcolor=FF3333&amp;wid=600&amp;hei=600](https://s7g10.scene7.com/is/image/genaibeta/leather-sofa?layer=1&posN=-0.3,-0.455&text=%7b\rtf1\ansi%7b\fonttbl%7b\f0+Arial;%7d%7d%7b\colortbl+\red255\green255\blue255;%7d\copyfit1000\vertalc\qc%7b\cf0\fs42+New+Collection%7d%7d&size=370,70&textAttr=130&bgcolor=FF3333&wid=600&hei=600) |

#### Redimensionnement et recadrage pour divers cas d’utilisation

##### Concepts de base du redimensionnement d’image

Le redimensionnement de l’image implique la modification des dimensions, de la résolution et de la taille du fichier d’une image. Voici quelques points clés à prendre en compte :

* **Composition en pixels :**
Les images numériques se composent de petits points appelés pixels. Lorsqu’une image est créée, elle comporte un nombre spécifique de pixels. Le redimensionnement implique l’ajout ou la soustraction de pixels pour modifier les dimensions, la résolution et la taille du fichier de l’image.
* **Format :**
Le maintien du rapport d’aspect (la relation entre la largeur et la hauteur) est essentiel pour éviter toute distorsion. Que vous agrandissiez (mise à l’échelle) ou réduisiez (mise à l’échelle) une image, la préservation des proportions garantit la cohérence visuelle.
* **Considérations de qualité :**
Le redimensionnement peut avoir un impact sur la qualité de l’image. Évitez une augmentation drastique de l’échelle, car elle peut entraîner une pixellisation. Envisagez plutôt de reproduire l’image à une taille et une résolution plus grandes. Pour les images plus petites, utilisez les outils appropriés pour conserver la résolution.

##### Recadrage et redimensionnement

Le recadrage et le redimensionnement sont des techniques de Dynamic Media qui vous permettent de transformer des images en fonction de divers cas d’utilisation, que ce soit pour créer des miniatures, des images d’affichage de produit ou des bannières.

* **Recadrage:**
Supprime une partie d’une image pour modifier sa composition et son encadrement. Il ne modifie pas les dimensions globales, mais se concentre sur un domaine spécifique.
* **Redimensionnement :**
Ajuste les dimensions, la résolution et la taille de fichier de l’image entière tout en conservant les proportions.

Explorons un cas d’utilisation qui implique l’image de salon suivante :

* **Image originale du salon :**
  [https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa](https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa)
* **Miniature (200 px x 200 px) :**
Une version plus petite adaptée au chargement ou à l’affichage rapide.
  [https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=200&amp;hei=200&amp;fit=crop](https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=200&hei=200&fit=crop)
* **Miniature avec recadrage (200 px x 200 px) :**
Recadré pour se concentrer sur la zone du canapé.
  [https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=200&amp;hei=200&amp;cropN=.24,.24,.6,.72&amp;fit=crop](https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=200&hei=200&cropN=.24,.24,.6,.72&fit=crop)
* **Image d’affichage du produit (800 px x 600 px) :**
Recadré et redimensionné pour mettre en valeur le canapé.
  [https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=800&amp;hei=600&amp;cropN=.24,.24,.6,.72&amp;fit=crop](https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=800&hei=600&cropN=.24,.24,.6,.72&fit=crop)
* **Bannière (1 720 px x 820 px) :**
Dérivé de l&#39;image originale, soulignant la pièce.
  [https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=1720&amp;hei=820&amp;cropN=0,.1,1,1&amp;fit=crop](https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=1720&hei=820&cropN=0,.1,1,1&fit=crop)

N’hésitez pas à explorer ces variations en fonction de vos besoins spécifiques.
Vous souhaitez en savoir plus sur les commandes disponibles dans une URL ? Accédez à [ Référence des commandes ](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference).

### Diffusion d’images GIF

**Analyse de rentabilité :** *Diffusion de GIF à l’aide de Dynamic Media*

Vous pouvez charger et diffuser des GIF via Dynamic Media. Pour effectuer le rendu d’un GIF animé, remplacez `is/image` par `is/content` dans l’URL. Par exemple, si vous avez chargé `abc.gif`, utilisez ce qui suit :

* Ce chemin d’accès à l’URL génère une vue statique du GIF :

  ```
  https://your.domain.com/is/image/yourfolder/abc
  ```

* Ce chemin d’accès à l’URL effectue le rendu de la vue d’animation du GIF :

  ```
  https://your.domain.com/is/content/yourfolder/abc
  ```

>[!NOTE]
>
>Lors de l’utilisation de `is/content` dans le chemin URL, les commandes de transformation d’image ne sont pas appliquées à la ressource.

### Publier une vidéo pour mon site web

**Business case :** *publiez rapidement une vidéo pour un site marketing.*

* **Sélectionnez un profil vidéo :**
Tout d’abord, dans Dynamic Media, vous devez sélectionner un profil vidéo approprié. Vous pouvez choisir le profil *Codage vidéo adaptatif* disponible dans AEM Assets sous Profils vidéo. Ces paramètres de codage prédéfinis garantissent que votre vidéo est optimisée pour la lecture sur différents appareils et conditions de bande passante. Vous pouvez également créer votre propre profil de vidéo adaptative.
* **Attribuer le profil :**
Attribuez le profil vidéo choisi aux dossiers dans lesquels votre vidéo va être chargée. Cette étape permet de s’assurer que les paramètres de codage corrects sont appliqués pendant le processus de chargement.
* **Chargez la vidéo d’origine :**
Chargez le fichier vidéo d’origine. Assurez-vous qu’il s’agit d’une vidéo haute résolution de bonne qualité. Plus la vidéo source est bonne, meilleur est le résultat final.
* **Prévisualisation et publication :**
Prévisualisez la vidéo pour vous assurer que tout se présente comme prévu. Une fois satisfait, procédez à la publication. Cette étape rend la vidéo accessible à votre audience.
* **Lien ou incorporation :**
Après la publication, vous disposez de deux options.

   * **Lien direct :**
Utilisez l’URL fournie pour créer un lien direct vers la vidéo. Créez des liens hypertexte appropriés sur votre site marketing.
   * **Incorporer la vidéo :**
Copiez le code incorporé fourni et collez-le dans l’HTML de votre page web où vous souhaitez que la vidéo apparaisse. Cela permet à la vidéo d’être lue directement sur votre site.

Vous souhaitez en savoir plus ? Accédez à [ Vidéo ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/video).

### Configurer des vidéos pour une qualité et un engagement optimaux

**Analyse de rentabilité :** *configurez les vidéos pour une qualité et un engagement optimaux.*

Pour garantir une qualité optimale et un engagement optimal de vos vidéos, pensez à mettre en œuvre une combinaison des bonnes pratiques suivantes :

* **Utilisation de la visionneuse de vidéos HTML5 intégrée :**
Les paramètres prédéfinis de la visionneuse de vidéos HTML5 Dynamic Media sont des lecteurs vidéo fiables. Utilisez-les pour éviter les problèmes courants associés à la lecture vidéo HTML5 et aux appareils mobiles.
Ces paramètres prédéfinis relèvent des défis tels que la diffusion en continu à débit adaptatif et la portée limitée du navigateur de bureau.
Vous souhaitez en savoir plus ? Accédez à [Bonne pratique : utilisation de la visionneuse de vidéos HTML 5](/help/assets/dynamic-media/video.md#best-practice-using-the-html-video-viewer).

* **Utiliser des profils vidéo Dynamic Media :**
Les profils vidéo de Dynamic Media permettent une gestion vidéo efficace, une qualité cohérente et une diffusion en continu adaptative.
Vous souhaitez en savoir plus ? Accédez à [Profils vidéo Dynamic Media](/help/assets/dynamic-media/video-profiles.md).

* **Suivez les bonnes pratiques en matière de codage vidéo :**
Appliquez des profils de codage vidéo qui conservent la qualité vidéo d’origine sans réduction excessive lors du codage.
Vous souhaitez en savoir plus ? Accédez à [Bonnes pratiques relatives au codage des vidéos](/help/assets/dynamic-media/video.md#best-practices-for-encoding-videos).

* **Adoptez la diffusion en continu adaptative au lieu de la diffusion en continu progressive :**
La diffusion en continu adaptative ajuste la qualité vidéo en fonction de la vitesse de connexion Internet et des caractéristiques de l’appareil de la visionneuse.
Il utilise des protocoles tels qu’HLS (HTTP Live Streaming) ou DASH (`Dynamic Adaptive Streaming over HTTP`) pour garantir une qualité de lecture optimale.
Contrairement au streaming progressif, qui diffuse les vidéos de manière linéaire, le streaming adaptatif réduit la mise en mémoire tampon et offre une expérience de visionnage transparente.

### Internationalisation de vidéos pour une consommation multilingue

**Analyse de rentabilité :** *préparer les vidéos pour une utilisation multilingue.*

L’internationalisation des vidéos pour une consommation multilingue est essentielle pour atteindre un public mondial. Dynamic Media propose des fonctionnalités qui peuvent vous aider à atteindre cet objectif.

* **Chargez vos vidéos :**
   * Créez tout d’abord un profil de codage vidéo. Vous pouvez utiliser le profil de codage de vidéo adaptative prédéfini fourni avec Dynamic Media ou créer votre propre profil personnalisé.
   * Associez le profil de traitement vidéo à un ou plusieurs dossiers dans lesquels vous chargez vos vidéos issues de sources originales.
   * Chargez les vidéos issues de sources originales dans ces dossiers. Dynamic Media les encode en fonction du profil de traitement vidéo attribué.
   * Dynamic Media prend principalement en charge les vidéos courtes (jusqu’à 30 minutes) avec une résolution minimale supérieure à 25 × 25. Les fichiers vidéo de 15 Go maximum chacun peuvent être chargés1.

* **Gérer vos vidéos :**
   * Organisez, parcourez et recherchez des ressources vidéo dans AEM.
   * Prévisualisation et publication des ressources vidéo.
   * Affichez la vidéo source et ses rendus codés, ainsi que les miniatures associées.
   * Modifiez les propriétés vidéo, telles que le titre, la description et les balises2.

* **Localisation:**
   * Pour chaque zone géographique/langue cible, créez des pistes audio et des sous-titres.
   * Ajoutez ces pistes audio et de sous-titres à vos vidéos à partir de l’interface d’AEM.
   * Lorsque les utilisateurs lisent les vidéos, ils peuvent sélectionner leur langue préférée pour l’audio et les sous-titres.

* **Publication:**
   * Si vous utilisez AEM comme système de gestion de contenu web (WCM), vous pouvez ajouter directement des vidéos à vos pages web.
   * Si vous utilisez un système de gestion de contenu web tiers, vous pouvez lier ou incorporer des vidéos dans vos pages web à l’aide d’URL ou de codes incorporés.

Vous souhaitez en savoir plus ? Accédez à [À propos de la prise en charge des légendes multiples et des pistes audio pour les vidéos dans Dynamic Media](/help/assets/dynamic-media/video.md#about-msma).


## Diffusion de ressources aux clients

### Optimisation de la taille des images et réduction du temps de chargement des pages

**Analyse de rentabilité :** *optimisez la taille des images pour n’importe quel navigateur ou écran et réduisez le temps de chargement des pages.*

L’imagerie dynamique Dynamic Media est un outil puissant qui améliore les performances de diffusion des images en optimisant automatiquement le format, la taille et la qualité de l’image en fonction des fonctionnalités du navigateur du client.

Adobe vous recommande d’utiliser les fonctionnalités d’imagerie dynamique plutôt que de définir manuellement le format de l’image sur `webp` ou `avif`. La raison est la suivante :

* **Compatibilité des navigateurs :**
L’imagerie dynamique garantit que le format de l’image diffusée est compatible avec le navigateur de l’utilisateur.
* **Compression optimale :**
Il sélectionne le meilleur format de compression en fonction du navigateur spécifique, des conditions du réseau et de la résolution d’écran.
* **Formats modernes :**
Bien que `avif` soit un format plus récent offrant une meilleure compression, il n’est pas encore universellement pris en charge sur tous les navigateurs.
* **Bonnes pratiques :**
Pour garantir le meilleur format optimisé pour le web, vous pouvez faire confiance à l’imagerie dynamique pour sélectionner le format plutôt que d’utiliser manuellement les commandes `fmt=webp` ou `fmt=avif`.

Grâce à l’imagerie dynamique, vous pouvez vous assurer que vos images sont diffusées de la manière la plus efficace possible, en les adaptant à l’environnement de navigation de chaque utilisateur. Cette approche simplifie le processus et peut améliorer les performances en termes de temps de chargement des images et d’expérience utilisateur globale.

Vous souhaitez en savoir plus ? Accédez à [ Imagerie dynamique ](/help/assets/dynamic-media/imaging-faq.md).

### Publier la diffusion des ressources auprès des clients

**Analyse de rentabilité :** *Après la publication d’un nouveau contenu ou le remplacement d’un contenu existant, comment peut-on s’assurer que les modifications apparaissent immédiatement sur le réseau CDN ?*

Le réseau de diffusion de contenu (CDN) met en cache des ressources Dynamic Media pour une diffusion rapide aux clients. Lorsque des mises à jour sont apportées à ces ressources, il est important que les modifications prennent effet immédiatement sur le site web. En purgeant ou en invalidant le cache du réseau CDN, les ressources diffusées par Dynamic Media peuvent être mises à jour rapidement. Cette approche élimine la nécessité d’attendre l’expiration du cache en fonction de la valeur TTL (Time To Live) , généralement définie sur dix heures. Selon votre cas d’utilisation spécifique, vous pouvez mettre à jour les paramètres de durée de vie (TTL) du réseau CDN en conséquence.

Vous souhaitez en savoir plus ? Accédez à [Invalidation du cache du réseau CDN par le biais de Dynamic Media](/help/assets/dynamic-media/invalidate-cdn-cache-dynamic-media.md).

