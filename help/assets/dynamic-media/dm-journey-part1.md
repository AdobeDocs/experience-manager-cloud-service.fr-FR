---
title: parcours Dynamic Media
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
source-git-commit: b830c6e2f86b92b03cb9c03e94ae2bb2e3bda444
workflow-type: tm+mt
source-wordcount: '3485'
ht-degree: 1%

---


# parcours Dynamic Media : Principes de base, première partie {#dm-journey-part1}

Bienvenue dans le Parcours Dynamic Media.

Ce parcours couvre les principes de base de Dynamic Media, son fonctionnement, ce qu’il peut vous apporter et la valeur qu’il apporte à votre travail et à vos clients.

**_Conditions préalables_**

* Compréhension de base des formats d’image et vidéo
* Compréhension de base du HTML et de la page CSS
* Compréhension de base des outils de conception tels qu’Adobe Illustrator, Adobe Photoshop, Adobe XD
* L’accès à Dynamic Media sur Experience Manager est utile, mais n’est pas obligatoire.

**_Ce que vous pouvez attendre d’apprendre_**

*Partie I*
* Qu’est-ce que Dynamic Media et comment peut-il vous aider ?
* Cas d’utilisation de Dynamic Media
* Circulation d’une ressource dans le système Dynamic Media

*Partie II*
* Anatomie d’une URL Dynamic Media et manière dont Dynamic Media diffuse du contenu
* Principes de base de la création de paramètres d’image prédéfinis pour le rendu des ressources
* Visionneuses d’images, à 360° et de supports variés

**_Audience_**
Le public qui convient le mieux aux lecteurs de ce parcours est le suivant, qui découvrent Dynamic Media sur Experience Manager :

* Administrateur
* Analyste métier
* Architecte de contenu
* Auteur de contenu
* Designer
* Développeur
* Marketing
* Gestionnaire/propriétaire de produit

## Qu’est-ce que Dynamic Media et comment peut-il vous aider ? {#dm-journey-a}

Dynamic Media vous aide à diffuser des ressources visuelles de marchandisage et de marketing à la demande. Il vous permet également de créer et de diffuser des expériences de visionnage interactif, notamment le zoom, la rotation à 360 degrés et la vidéo. Vos ressources sont mises à l’échelle de manière dynamique pour une utilisation sur le web, les appareils mobiles et les réseaux sociaux. À l’aide d’un ensemble de ressources Principales (telles que des images, des vidéos et de la 3D), Dynamic Media génère et diffuse plusieurs variantes de ce contenu riche, en temps réel, par le biais de son réseau de diffusion de contenu mondial, évolutif et performant (Content Delivery Network).

Dynamic Media intègre les workflows de la solution de gestion des actifs numériques Adobe Experience Manager Assets afin de simplifier et rationaliser le processus de gestion des campagnes numériques.

### Un fichier avec des possibilités infinies

Le concept de *Un Principal fichier de ressource avec des possibilités infinies*.

Pour mieux comprendre ce concept, pensez à la manière dont vous travaillez traditionnellement avec une seule ressource, telle qu’une image ou une vidéo. En règle générale, vous créez une ressource Principale. Ensuite, vous créez manuellement des versions de cette même ressource pour chaque expérience, chaque appareil nécessaire, chaque page web et chaque propriété où elle est utilisée. Avec le temps, cette ressource unique peut atteindre 20, 30 ou plus, sans aucun historique de version. Maintenant, imaginez que vous faites ça pour chaque image ou vidéo que vous avez. Le nombre de versions de ressources deviendrait rapidement écrasant pour la maintenance et la mise à jour, sans parler de l’augmentation des coûts de stockage.

Dynamic Media, en revanche, est fondamentalement différent des autres systèmes, car vous l’utilisez pour diffuser vos médias. *dynamiquement* à partir de ressources uniques et Principales et d’appels d’URL. Les chemins d’URL Dynamic Media que vous demandez incluent des instructions indiquant au serveur de publication d’Adobe comment afficher la ressource lorsqu’elle est diffusée sur l’écran d’un client. Par exemple, en utilisant la même ressource Principale unique, vous pouvez la faire livrer instantanément dans un nombre illimité de rendus, en modifiant la taille, le format, la résolution, le poids, la couleur, le recadrage et les effets tels qu’un zoom.

Cette méthode de diffusion unique garantit que des expériences de qualité cohérentes sont envoyées à n’importe quel écran, quelle que soit la taille ou la bande passante. Les vidéos en taille réelle sont également optimisées pour tous les types d’écran et diffusées de manière adaptative afin d’offrir une expérience utilisateur cohérente et de qualité.

<!-- As part of building and publishing assets with Dynamic Media, you visually configure the effects that you want to apply to assets. In so doing, you are literally building the URL that correctly tells the publish server how to deliver your primary asset to the screen.  -->

![Adobe Dynamic Media diffuse la même Principale image sur différents supports, dans des formats et des tailles différents.](/help/assets/assets-dm/dm-oneasset-multioutput.png)
*Adobe Dynamic Media garantit la cohérence et la qualité des expériences diffusées sur n’importe quel écran, quelle que soit leur taille ou leur bande passante.*

Au fur et à mesure que vous lisez, vous allez en apprendre plus sur l&#39;importance de ce concept de &quot;un Principal fichier de ressource, des possibilités infinies&quot;.

### Le réseau de diffusion de contenu

Lorsque vous êtes prêt à publier une ressource image ou vidéo, elle est prise en charge par la colonne vertébrale de Dynamic Media, composée d’un puissant réseau de diffusion de premier niveau. Le réseau sert des centaines de clients dans le monde entier tous les jours. Les ressources sont distribuées sur le réseau de diffusion de contenu (CDN), hébergé par Akamai. Le réseau de diffusion de contenu est un système de services informatiques en réseau qui coopèrent de manière transparente pour diffuser du contenu, en particulier du contenu multimédia volumineux, aux utilisateurs finaux.

Dans le système CDN, le contenu web est stocké dans des caches web sur Internet. Elle est ensuite diffusée à partir du cache web vers les utilisateurs finaux afin de permettre une diffusion plus rapide. Ainsi, la première fois qu’une personne télécharge une page web, les ressources qu’elle voit sont placées dans un cache CDN. Ils sont stockés sur le serveur, de sorte que la prochaine fois qu’une personne se trouvant dans la même zone accédera à la page web, le même contenu de cache sera diffusé plus rapidement. Le contenu est diffusé plus rapidement, car il se trouve plus près de l’utilisateur final. Un réseau de diffusion de contenu accélère l’affichage des pages web, tout en réduisant la demande de bande passante sur le serveur central, car le contenu est diffusé à partir d’un réseau de cache, et non d’un serveur central dans chaque instance. Ce flux optimisé offre une meilleure expérience utilisateur, ce qui entraîne une augmentation des ventes.

<!-- USE AN IMAGE HERE? ![Content delivery network](/help/assets/assets-dm/cdn.png) -->

Historiquement, le réseau de diffusion de contenu fournit 3,5 pétaoctets de trafic aux clients, chaque mois. Le système peut fournir 52 milliards d’actifs en une seule journée. Ce nombre équivaut à 864 000 images et vidéos diffusées avec succès aux clients, *toutes les secondes*.

### Imagerie dynamique

Dynamic Media s’efforce déjà d’optimiser les ressources et de s’assurer que chaque ressource est chargée rapidement sur les systèmes mobiles et de bureau, au moyen du réseau de diffusion de contenu. Pour ce faire, les paramètres d’image prédéfinis sont utilisés dans Dynamic Media pour définir la qualité de votre image. Ils définissent également le type d’image que vous envoyez, sa netteté et d’autres éléments pour différentes parties de vos expériences ou pages.

Mais pour ajouter de la valeur à Dynamic Media au-delà des paramètres d’image prédéfinis, il existe des *Imagerie dynamique*.

L’imagerie dynamique offre de meilleures performances de diffusion des ressources d’image en optimisant automatiquement le format et la taille de fichier d’une image en fonction des fonctionnalités de navigateur d’un client. Il fonctionne avec vos paramètres d’image prédéfinis existants (vous en lirez plus ultérieurement sur les paramètres d’image prédéfinis) et utilise des informations lors de la diffusion.

Cette intelligence réduit davantage la taille du fichier image en fonction de la vitesse de connexion du navigateur et du réseau. Étant donné que les ressources d’image représentent la majeure partie du temps de chargement d’une page, l’amélioration des performances peut avoir un impact complet sur les indicateurs métier clés, tels que :

* Conversion plus élevée
* Durée de la visite du site
* Taux de rebond inférieur du site

Dans l’ensemble, avec l’imagerie dynamique, vous pouvez vous attendre à une amélioration des performances de 22 à 47 % en fonction des paramètres d’image prédéfinis et des caractéristiques spécifiques de l’utilisateur final. Tout en conservant la qualité de l’image comme si elle n’avait jamais été touchée.

![Imagerie dynamique](/help/assets/assets-dm/dm-smart-imaging.png)
*L’imagerie dynamique optimise automatiquement le format et la taille de fichier d’une image en fonction des fonctionnalités de navigateur et de la vitesse du réseau d’un client.*

L’imagerie dynamique n’est pas activée par défaut, car elle nécessite un effort coordonné entre vous et l’assistance technique d’Adobe Dynamic Media. En outre, l’activation de l’imagerie dynamique nécessite un effacement complet du cache du réseau de diffusion de contenu, qui est ensuite complété avec le temps. Si vous souhaitez utiliser l’imagerie dynamique, vous pouvez demander à Adobe de l’activer en soumettant un ticket d’assistance technique. Le support technique vous fournit ensuite un paramètre d’URL qui vous permet de tester au préalable l’imagerie dynamique. Vous pouvez l’essayer sur n’importe quelle page web ou image afin de voir les performances obtenues et les économies réalisées. L’imagerie dynamique peut alors être activée pour l’ensemble du site.

En savoir plus sur [Imagerie dynamique](/help/assets/dynamic-media/imaging-faq.md)

### Visionneuses de vidéos adaptatives

Lorsqu’il y a une vidéo sur une page, ou une page principale, vos clients ont tendance à interagir avec ce contenu plus longtemps et à rester sur la page plus longtemps, ce qui est généralement une bonne chose. Ce comportement a été démontré par les analyses que l’Adobe a effectuées. Cependant, la vidéo peut être complexe. D&#39;une part, vous avez souvent un grand fichier Principal. Il est complexe de déterminer la taille et la diffusion de la vidéo, le tout pour s’assurer que l’expérience s’exécute sans problème quel que soit l’appareil sur lequel elle est vue et quelle que soit la bande passante.

Pour résoudre ce problème, Dynamic Media vous permet de créer des *Visionneuses de vidéos adaptatives*.

![Visionneuse de vidéos adaptative](/help/assets/dynamic-media/assets/dm-adaptive-video.png)
*Une visionneuse de vidéos adaptative regroupe les versions d’une même vidéo codées à des débits et des formats différents.*

Vous commencez avec votre Principale vidéo originale que vous téléchargez dans le système. Tailles automatiques de Dynamic Media ou *transcodes*, cette vidéo en plusieurs vidéos. Ensuite, au moment de la diffusion, il détermine intelligemment quel écran vidéo, quelle qualité et quel format utiliser et le diffuse sur le téléphone, la tablette ou l’ordinateur de bureau.

Par exemple, sur un appareil mobile iOS, il détecte une bande passante telle que 4G, 5G ou une connexion Wi-Fi, puis sélectionne automatiquement la vidéo codée selon le débit correspondant parmi ceux disponibles dans la visionneuse de vidéos adaptative. La vidéo est diffusée en continu sur des appareils mobiles, des tablettes ou des ordinateurs de bureau.

En outre, la qualité vidéo est automatiquement changée de manière dynamique si les conditions réseau changent. De plus, si un client passe en mode Plein écran sur un bureau, la visionneuse de vidéos adaptative répond en utilisant une meilleure résolution, améliorant ainsi l’expérience de visionnage du client.

L’utilisation de visionneuses de vidéos adaptatives permet une lecture fluide et de haute qualité pour les clients qui lisent des vidéos Dynamic Media sur plusieurs écrans et appareils. Ça retire vraiment la complexité de la vidéo.

<!-- X-REF to videos chapter.  -->

## Cas d’utilisation de Dynamic Media {#dm-journey-b}

Vous trouverez ci-dessous des solutions et des problèmes de cas d’utilisation courants que Dynamic Media peut vous aider à résoudre pour stimuler l’engagement positif des clients, la fidélité, la conversion et un retour sur investissement accru.

### Cas pratique : Approche Principale des fichiers

L’un des cas d’utilisation les plus importants pour Dynamic Media est également l’un des plus évidents. C’est-à-dire réduire le poids des pages et des expériences, ainsi que la taille du contenu, qu’il s’agisse d’une image ou d’une vidéo, qui est diffusé.

Vous trouverez ci-dessous une expérience ou une page web type. Environ 90 % d’une page est constituée de médias riches, tels que des images et des vidéos, qui sont généralement des fichiers beaucoup plus lourds.

![Poids de la page de contenu](/help/assets/dynamic-media/assets/dm-content-page-weight.png)
*Poids de page de contenu d’une page web standard.*

Les 10 % restants sont HTML, code CSS et balises spécifiques. Vous souhaitez optimiser le poids de 90 % de cette page et Dynamic Media vous aide à réaliser cet effort. Vous avez déjà lu un article sur le concept de *Un Principal fichier de ressource avec des possibilités infinies*. Cette approche est importante pour réduire le poids global de la page. La possibilité de prendre une ressource Principale et de l’utiliser sur une page des détails du produit, une page miniature, votre panier et votre grille de recherche est un gain de temps considérable. Et cela assure également la cohérence entre les expériences.

![Approche Principale des fichiers](/help/assets/dynamic-media/assets/dm-onefile.png)
*Un fichier avec plusieurs rendus créés à la volée.*

Regardons de plus près les problèmes que Dynamic Media résout avec le fichier unique et certaines des solutions à cette approche.

| **Problème** | **Solution Dynamic Media** |
|---|---|
| Créez et stockez chaque ressource. | Utilisez un seul fichier image, créant automatiquement les rendus requis uniquement au moment de la diffusion. |
| Coûts de stockage élevés. | Il n’est plus nécessaire de créer et de stocker plusieurs rendus d’une ressource. |
| Difficulté à maintenir la chaîne de garde à vue. | Garantit la diffusion d’expériences optimisées pour les appareils et cohérentes. |
| Aucun historique de version. |  |
| Expériences de marque incohérentes sur tous les appareils. |  |
| Coût superflu de la création de ressources en double. |  |

Lorsque vous réfléchissez à un fichier, vous créez une ressource pour chaque type d’expérience. Vous pouvez avoir une image de départ, puis vous devez créer 20, 30 ou 40 variantes de cette image, que vous devez en fin de compte stocker et payer pour ce stockage.

Vous devez également vous assurer que la bonne image est utilisée, ce qui peut affecter votre capacité à homogénéiser vos marques. Et si vous ne trouvez pas d’image, vous devez revenir en arrière et dupliquer ces ressources.

Dynamic Media vous permet de créer des variantes d’images, à la volée, à partir de cette image de départ. Il vous permet d’être créatif avec cette Principale ressource et de ne pas avoir à aller et venir avec votre graphiste ou studio photo pour créer du contenu supplémentaire. Et c&#39;est de l&#39;argent et du temps économisé.

Avec l’approche d’un seul fichier, vous utilisez un seul fichier Principal. Créez ensuite les versions ou rendus requis sur l’ensemble de vos sites, propriétés et expériences, uniquement au moment où ils sont diffusés ou vus par un client. Cette efficacité peut réduire considérablement la quantité de stockage nécessaire à vos ressources et réduire la complexité globale de votre workflow. Avec le système de diffusion de Dynamic Media, il garantit que chaque image et vidéo est optimisée, se charge rapidement et s’affiche parfaitement sur tous les écrans et appareils.

### Cas pratique : Vidéo

Un autre cas d’utilisation que Dynamic Media résout pour est la vidéo. La vidéo est complexe. C&#39;est difficile à gérer. Les fichiers vidéo sont difficiles à stocker et à déplacer en raison de leur taille de fichier inhérente.

| **Problème** | **Solution Dynamic Media** |
|---|---|
| Difficulté à gérer et diffuser des vidéos optimisées pour divers appareils. | Utilisez une seule vidéo qui prend automatiquement en charge la taille de tous les appareils. |
| Les vidéos sont bloquées ou lues en basse qualité en raison de la bande passante disponible pour l’utilisateur final. | Diffusez de la vidéo par le biais d’un lecteur de HTML qui détecte automatiquement la bande passante disponible et adapte la qualité pour garantir une lecture fluide et une haute fidélité. |
| La création manuelle de toutes les versions d’une vidéo n’est pas réalisable et prend du temps pour garantir un affichage et une lecture corrects sur tous les appareils. | Éliminez les heures de travail fastidieux de transcodage grâce à un workflow simplifié. |
|  | Libérez du temps pour un travail à plus forte valeur ajoutée. |

Les clients se rendent dans Dynamic Media avec le problème suivant qu’ils espèrent résoudre :

&quot;*Nous avons la vidéo, et nous avons dépensé beaucoup d&#39;argent pour la créer. Mais nous avons évité de le placer sur des pages, ou de le diffuser, parce que de nos tests, nous ne pouvons vraiment pas garantir la qualité de la vidéo, ou si elle va vraiment jouer. Et finalement, cela affecte nos marques et potentiellement notre rôle même dans la conversion.*&quot;

La solution de Dynamic Media consiste à prendre ce Principal fichier vidéo et à laisser Dynamic Media créer toutes les tailles grâce à son processus de transcodage. Ensuite, ajoutez-le au lecteur vidéo intelligent de Dynamic Media. Ce workflow garantit que si vous utilisez cette vidéo sur votre page d’entrée principale, ou sur une page de détails de catégorie ou de produit, elle sera cohérente tout au long de la vidéo et sera diffusée avec une qualité élevée.

Voici plusieurs autres cas d’utilisation à prendre en compte.

### Cas pratique : Une seule source de vérité

| **Problème** | **Solution Dynamic Media** |
|---|---|
| Ressources numériques dispersées dans l’organisation, réparties dans différentes équipes ou unités opérationnelles. | Stockez et gérez toutes les ressources numériques à un emplacement central. |
| Les membres de l’équipe téléchargent et créent des versions locales. | Les membres de l’équipe utilisent un seul fichier Principal pour créer *et* diffuser toutes les versions nécessaires sur différents formats d’écran et appareils ; |
| Ressources à usage unique créées pour chaque expérience et périphérique. | Élimine les actifs à usage unique, ce qui permet de gagner du temps et de l&#39;argent en les créant. |

### Cas pratique : Recadrage intelligent optimisé par l’IA pour les médias riches

| **Problème** | **Solution Dynamic Media** |
|---|---|
| La création manuelle d’images ou de vidéos, leur mesure et leur couper manuellement pour mettre en évidence le point focal et les afficher de manière appropriée sur toutes les tailles d’écran et tous les appareils demandent beaucoup de temps et de main d’oeuvre. | Utilise le recadrage intelligent dans Dynamic Media, une fonctionnalité d’IA d’Adobe Sensei, pour détecter automatiquement le point focal d’une image ou d’une vidéo, puis le recadrer pour le gérer. |
| Perte de temps qui pourrait être plus utile pour créer des expériences à fort impact. | Capture le point ciblé prévu, quelle que soit la taille de l’écran. |
| Ressources à usage unique créées pour chaque expérience et périphérique. | Élimine les tâches manuelles fastidieuses et fournit des images et des vidéos à chargement rapide de haute qualité qui s’affichent correctement sur n’importe quel appareil ou écran. |

### Cas pratique : Création de médias interactifs

| **Problème** | **Solution Dynamic Media** |
|---|---|
| Expériences clients statiques et aplaties qui n’engagent pas, n’engendrent pas de fidélité ou ne génèrent pas de conversion. | Permet aux utilisateurs non techniques d’ajouter facilement et en toute transparence des éléments interactifs tels que des zones réactives, des carrousels et des visionneuses à 360° pour offrir des expériences plus dynamiques et attrayantes. |
| Retour sur investissement limité des ressources numériques et expériences client médiocres. | Génère des conversions et des retours sur investissement à partir d’expériences multimédias riches. |

## Circulation d’une ressource dans le système Dynamic Media {#dm-journey-c}

Vous trouverez ci-dessous un workflow type pour Dynamic Media.

![Workflow Dynamic Media](/help/assets/dynamic-media/assets/dm-workflow.png)
*Circulation d’une ressource dans le système Dynamic Media.*

Vous commencez par la phase de création avec l’objectif principal d’avoir votre Principale ressource à la fin. Ces Principales ressources peuvent provenir de séances photo, de vendeurs de vidéos ou de fichiers audio que vous avez créés. Vous pouvez utiliser les applications de Creative Suite d’Adobe telles qu’Adobe InDesign, Adobe Photoshop, Adobe Illustrator pour vous aider à élaborer le contenu.

Lorsque la partie de création est terminée, vous placez la ressource dans la solution de création en la chargeant dans Dynamic Media. Dans Dynamic Media, assurez-vous que les paramètres d’image prédéfinis et les visionneuses appropriés sont alignés pour vos différentes pages web sur votre site.

Enfin, vous optimisez tout ce contenu et le publiez sur les serveurs Dynamic Media afin qu’il soit disponible pour le web, l’impression, le courrier électronique, les ordinateurs de bureau et les appareils mobiles.

### Chargement de ressources dans Dynamic Media

Une fois la création d’une ressource Principale terminée, vous la chargez dans Dynamic Media. Le type de fichier que vous chargez, ainsi que le format et la taille du fichier, sont des attributs importants de Dynamic Media. C’est au moment du téléchargement que vous souhaitez vous assurer que vous obtenez la valeur maximale de la prise en charge d’un seul fichier.

Par exemple, l’image de montre ci-dessous fait 4 560 x 3 020 pixels. Et bien que vous ne puissiez jamais utiliser une image de cette taille, vous pouvez toujours la télécharger. Plus l’image est grande, meilleure est la qualité que Dynamic Media peut fournir, même jusqu’à un rendu miniature. Souvenez-vous : vous pouvez facilement *diminution* résolution d’une image existante. Mais si vous essayez *augmenter* la résolution d&#39;une image, le résultat risque d&#39;être insatisfaisant.

![Formats recommandés pour le chargement dans Dynamic Media](/help/assets/dynamic-media/assets/dm-upload-formats.png)
*Considérations relatives aux chargements de ressources.*

Adobe recommande de charger des ressources dans un format sans perte. En règle générale, il est préférable d’éviter le JPEG, car lorsque vous diffusez le JPEG ou que vous continuez à enregistrer le JPEG, vous commencez à perdre la qualité de l’image au fil du temps. Vous souhaitez commencer avec les images à résolution la plus élevée dans un format sans perte avec lequel vous pouvez vivre. Ce format est généralement un fichier TIFF ou PNG.

En ce qui concerne l’espace colorimétrique, lorsque vous pensez à un canal numérique ou à un affichage web, vous pensez généralement au RGB (rouge, vert, bleu).

La plupart ne songeraient jamais à livrer quelque chose en CMJN ou à savoir pourquoi vous pourriez même vouloir livrer dans CMJN. Cela est dû au fait que cet espace colorimétrique est le plus souvent utilisé pour diffuser des éléments imprimés. Toutefois, Dynamic Media peut fournir des données dans les deux espaces colorimétriques.

Il y a de nombreux clients qui font encore de l&#39;impression, comme des clubs de gros d&#39;entrepôt. Et il y a les épiceries qui impriment souvent des prospectus une fois par semaine. Ces clients exigent que leurs images soient dans les deux espaces colorimétriques. Traditionnellement, cela nécessitait deux images différentes : un en RGB et un en CMJN. Cependant, vous pouvez charger des ressources CMJN directement dans Dynamic Media et demander à Dynamic Media de diffuser des ressources RGB par le biais d’un paramètre d’image prédéfini ou d’un profil de couleurs automatiquement. Il n’est pas nécessaire de créer plusieurs versions d’un fichier, ce qui permet de conserver le concept de *Un Principal fichier de ressource avec des possibilités infinies*.

XREF POUR TÉLÉCHARGER DES RESSOURCES DANS DYNAMIC MEDIA

<!-- **The Value of Renditioning??? or Demo portion** -->

### Publication et prévisualisation de ressources

Une fois les ressources chargées dans Dynamic Media, il est recommandé de *publier* en sélectionnant les ressources, puis en cliquant sur **[!UICONTROL Publier]** ou **[!UICONTROL Publication rapide]** dans Dynamic Media. La publication des ressources est nécessaire si vous avez l’intention de les utiliser dans une expérience. Une fois les ressources publiées, vous pouvez les inclure dans une page web à l’aide d’une URL générée par Dynamic Media que vous copiez ou en incorporant du code sur la page.

Outre la publication manuelle de ressources, vous pouvez configurer Dynamic Media afin de publier instantanément des ressources (sans intervention de l’utilisateur) au moment du chargement.

Voir [Publication de ressources Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/publishing-dynamicmedia-assets.html?lang=en).

Après le chargement, il existe différentes manières de prévisualiser les rendus d’une ressource dans Dynamic Media. L’aperçu des rendus peut vous donner une idée de ce qu’un client voit. Une méthode d’aperçu courante consiste à sélectionner une ressource, puis à afficher ses rendus en sélectionnant une *paramètre d’image prédéfini* comme illustré ci-dessous.

![Prévisualisation d’un rendu d’une ressource en fonction du paramètre d’image prédéfini Grande](/help/assets/dynamic-media/assets/dm-image-preset-with-url.png)
*Prévisualisation d’un rendu d’une ressource en fonction du paramètre d’image prédéfini &quot;Grand&quot; sélectionné. Cliquez sur le bouton URL . Le chemin d’accès URL qui en résulte peut être utilisé dans une page web.*

L’URL ci-dessus est en ligne ! [Essayez](http://s7d1.scene7.com/is/image/jpearldemo/AdobeStock_28563982?$Large$).

Pour prévisualiser une ressource, une autre méthode consiste à sélectionner la ressource image, puis à sélectionner une *Visionneuses* prédéfini comme illustré ci-dessous.

![Prévisualisation d’une ressource en fonction du paramètre prédéfini de la visionneuse Zoom sur la lumière verticale](/help/assets/dynamic-media/assets/dm-viewer-preset.png)
*Prévisualisation d’une ressource en fonction du paramètre prédéfini de visionneuse &quot;ZoomVertical_light&quot; sélectionné. Le pointeur de la souris (`+`) a été déplacé sur la montre pour effectuer un zoom avant. Notez les boutons URL et Incorporer .*

Le rendu ci-dessus est en ligne ! [Essayez](https://s7d1.scene7.com/s7viewers/html5/ZoomVerticalViewer.html?asset=jpearldemo/AdobeStock_28563982&amp;config=jpearldemo/ZoomVertical_light).

Examinons ces URL un peu plus près pour mieux comprendre ce qui se passe.

Emmenez-moi [parcours Dynamic Media : Principes de base, deuxième partie](/help/assets/dynamic-media/dm-journey-part2.md#dm-journey-d).





