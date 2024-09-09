---
title: Parcours Dynamic Media, première partie
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
exl-id: f3472006-d5ae-4f70-af3e-44e73aee85cc
source-git-commit: 879af9e3168a1ab993eff930355c4bd200879c71
workflow-type: tm+mt
source-wordcount: '3615'
ht-degree: 90%

---

# Parcours Dynamic Media : principes de base, première partie {#dm-journey-part1}

{{work-with-dynamic-media}}

Bienvenue dans le Parcours Dynamic Media.

Ce parcours couvre les principes de base de Dynamic Media, son fonctionnement, ce qu’il peut vous apporter et la valeur qu’il apporte à votre travail et à vos clients.

**_Conditions préalables_**

* Compréhension de base des formats d’image et vidéo
* Compréhension de base du HTML et du CSS
* Compréhension de base des outils de conception tels qu’Adobe Illustrator, Adobe Photoshop, Adobe XD
* Accéder à Dynamic Media sur Experience Manager est utile mais pas obligatoire.

**_Résultats d’apprentissage attendus_**

_Première partie_

* Qu’est-ce que Dynamic Media et en quoi peut-il vous être utile ?
* Cas d’utilisation de Dynamic Media
* Circulation d’une ressource dans le système Dynamic Media

_Deuxième partie_

* Anatomie d’une URL Dynamic Media et méthode de Dynamic Media pour diffuser du contenu
* Les principes de base de la création de paramètres d’image prédéfinis pour le rendu des ressources
* Les visionneuses d’images, visionneuses à 360° et visionneuses de supports variés

**_Audience_**
Ce parcours est particulièrement adaptée pour les personnes suivantes si elles sont peu familières avec Dynamic Media dans Experience Manager :

* Administrateur
* Analyste métier
* Architecte de contenu
* Auteur de contenu
* Designer
* Développeur
* Marketing
* Gestionnaire/propriétaire de produit

>[!TIP]
>
>Pour de meilleurs résultats, Adobe vous recommande de lire et d’afficher ce Parcours Dynamic Media sur un ordinateur de bureau.

## Qu’est-ce que Dynamic Media et en quoi peut-il vous être utile ? {#dm-journey-a}

Dynamic Media vous aide à diffuser des ressources visuelles de merchandising et de marketing à la demande. Il vous permet également de créer et de diffuser des expériences de visionnage interactif, grâce notamment au zoom, à la rotation à 360° et à la vidéo. Vos ressources sont mises à l’échelle de manière dynamique pour être utilisées sur le web, les appareils mobiles et les réseaux sociaux. À l’aide d’un ensemble de ressources issues de sources originales (telles que des images, des vidéos et de la 3D), Dynamic Media génère et diffuse plusieurs variantes de ce contenu riche, en temps réel, par le biais de son réseau de diffusion de contenu (Content Delivery Network) mondial, évolutif et performant.

Dynamic Media incorpore les workflows de la gestion des ressources numériques d’Adobe Experience Manager pour simplifier et rationaliser le processus de gestion des campagnes numériques.

### Un fichier avec des possibilités infinies

L’un des points cruciaux à comprendre à propos de Dynamic Media est le concept suivant : _Un fichier de ressource principal avec des possibilités infinies_.

Pour mieux comprendre ce concept, pensez à la manière dont vous travaillez traditionnellement avec une seule ressource, telle qu’une image ou une vidéo. En règle générale, vous créez une ressource principale. Ensuite, vous créez manuellement des versions de cette même ressource pour chaque expérience, chaque appareil nécessaire, chaque page web et chaque propriété où elle est utilisée. Avec le temps, cette ressource unique peut être déclinée en 20, 30 versions ou plus, sans aucun historique de version qui leur soit attaché. Maintenant, imaginez que vous faites ça pour chaque image ou vidéo que vous avez. Le nombre de versions de ressources deviendrait rapidement un cauchemar à gérer pour la maintenance et la mise à jour, sans parler de l’augmentation des coûts de stockage.

Dynamic Media, en revanche, est fondamentalement différent des autres systèmes, car vous l’utilisez pour diffuser vos médias _dynamiquement_ à partir de ressources uniques et principales et d’appels d’URL. Les chemins d’URL Dynamic Media que vous demandez incluent des instructions indiquant au serveur de publication d’Adobe comment afficher la ressource lorsqu’elle est diffusée sur l’écran d’un client. Par exemple, en utilisant la même ressource principale unique, vous pouvez la délivrer instantanément dans un nombre illimité de rendus, et en modifier instantanément la taille, le format, la résolution, le poids, la couleur, le recadrage et les effets tels qu’un zoom.

Cette méthode de diffusion unique garantit que des expériences de qualité cohérentes sont envoyées à n’importe quel écran, quelle que soit la taille ou la bande passante. Les vidéos en taille réelle sont également optimisées pour tous les types d’écran et diffusées de manière adaptative afin d’offrir une expérience utilisateur cohérente et de qualité.

<!-- As part of building and publishing assets with Dynamic Media, you visually configure the effects that you want to apply to assets. In so doing, you are literally building the URL that correctly tells the publish server how to deliver your primary asset to the screen.  -->

![Adobe Dynamic Media diffuse la même image principale sur différents supports, dans des formats et des tailles différents.](/help/assets/dynamic-media/assets/dm-oneasset-multioutput.png)
_Adobe Dynamic Media garantit la diffusion d’expériences cohérentes et de qualité sur n’importe quel écran, quelle que soit leur taille ou leur bande passante._

Au fur et à mesure que vous lisez, vous allez en apprendre plus sur l’importance de ce concept de « Un fichier de ressource principal avec des possibilités infinies ».

### Le réseau de diffusion de contenu

Lorsque vous êtes prêt à publier une ressource image ou vidéo, elle est prise en charge par la colonne vertébrale de Dynamic Media, composée d’un puissant réseau de diffusion de premier niveau. Le réseau sert des centaines de clients dans le monde entier tous les jours. Les ressources sont distribuées sur le réseau de diffusion de contenu (CDN), hébergé par Akamai. Le réseau de diffusion de contenu est un système de services informatiques en réseau qui coopèrent de manière transparente pour diffuser du contenu, en particulier du contenu multimédia volumineux, aux utilisateurs finaux.

Dans le système du CDN, le contenu web est stocké dans des caches web sur Internet. Il est ensuite diffusé à partir du cache web vers les utilisateurs finaux afin de permettre une diffusion plus rapide. Ainsi, la première fois qu’une personne télécharge une page web, les ressources qu’elle voit sont placées dans un cache CDN. Ils sont stockés sur le serveur, de sorte que la prochaine fois qu’une personne se trouvant dans la même zone accédera à la page web, le même contenu mis en cache sera diffusé plus rapidement. Le contenu est diffusé plus rapidement car il se trouve plus près de l’utilisateur. Un réseau de diffusion de contenu accélère l’affichage des pages web, tout en réduisant la demande de bande passante sur le serveur central, car le contenu est diffusé à partir d’un réseau de cache, et non d’un serveur central dans chaque instance. Ce flux optimisé offre une meilleure expérience utilisateur, ce qui entraîne une augmentation des ventes.

<!-- USE AN IMAGE HERE? ![Content delivery network](/help/assets/assets-dm/cdn.png) -->

Historiquement, le réseau de diffusion de contenu fournit 3,5 pétaoctets de trafic aux clients chaque mois. Le système peut délivrer 52 milliards de ressources en une seule journée. Ce nombre équivaut à 864 000 images et vidéos diffusées avec succès aux clients, _toutes les secondes_.

### Imagerie dynamique

Dynamic Media s’efforce déjà d’optimiser les ressources et de s’assurer que chaque ressource est chargée rapidement sur les systèmes mobiles et de bureau, au moyen du réseau de diffusion de contenu. Pour ce faire, les paramètres d’image prédéfinis sont utilisés dans Dynamic Media pour définir la qualité de votre image. Ils définissent également le type d’image que vous envoyez, sa netteté et d’autres éléments pour différentes parties de vos expériences ou pages.

Mais pour ajouter de la valeur à Dynamic Media au-delà des paramètres d’image prédéfinis, vous pouvez utiliser l’_imagerie dynamique_.

L’imagerie dynamique offre de meilleures performances de diffusion des ressources d’image en optimisant automatiquement le format et la taille de fichier d’une image en fonction des fonctionnalités de navigateur d’un client. Il fonctionne avec vos paramètres d’image prédéfinis existants (les paramètres d’image prédéfinis sont abordés dans la deuxième partie de ce parcours) et utilise des informations lors de la diffusion.

Ces informations permettent d’encore réduire la taille du fichier image en fonction de la vitesse de connexion du navigateur et du réseau. Étant donné que les ressources d’image représentent la majeure partie du temps de chargement d’une page, l’amélioration des performances peut avoir un impact déterminant sur les indicateurs d’activité clés suivants :

* Une conversion plus élevée
* Le temps passé sur le site
* Un taux de rebond inférieur du site

En général, avec l’imagerie dynamique, vous pouvez vous attendre à une amélioration des performances de 22 à 47 % en fonction des paramètres d’image prédéfinis et des caractéristiques spécifiques de l’utilisateur final. Tout cela, en conservant la qualité de l’image comme si elle n’avait jamais été touchée.

![Imagerie dynamique](/help/assets/dynamic-media/assets/dm-smart-imaging.png)
_L’imagerie dynamique optimise automatiquement le format et la taille de fichier d’une image en fonction des capacités du navigateur et de la vitesse du réseau d’un client._

L’imagerie dynamique n’est pas activée par défaut, car elle nécessite des actions coordonnées entre vous et l’assistance technique d’Adobe Dynamic Media. En outre, l’activation de l’imagerie dynamique nécessite un effacement complet du cache du réseau de diffusion de contenu, qui se remplit ensuite avec le temps. Si vous souhaitez utiliser l’imagerie dynamique, vous pouvez demander à Adobe de l’activer en soumettant un ticket d’assistance technique. L’assistance technique vous fournit ensuite un paramètre d’URL qui vous permet de tester au préalable l’imagerie dynamique. Vous pouvez l’essayer sur n’importe quelle page ou image web afin de voir les performances obtenues et les économies réalisées. L’imagerie dynamique peut alors être activée pour l’ensemble du site.

### Visionneuses de vidéos adaptatives

Lorsqu’il y a une vidéo sur une page ou sur une page principale, vos clients ont tendance à interagir avec ce contenu plus longtemps et à rester sur la page plus longtemps, ce qui est généralement une bonne chose. Ce comportement est exposé dans les analyses que l’Adobe a effectuées. Cependant, traiter des vidéos peut être complexe. D’une part, vous avez souvent à gérer un fichier principal de taille importante. Il est complexe de déterminer la taille et la diffusion de la vidéo, le tout pour s’assurer que l’expérience s’exécute sans problème quel que soit l’appareil sur lequel elle est visionnée et quelle que soit la bande passante.

Pour résoudre ce problème, Dynamic Media vous permet de créer des _Visionneuses de vidéos adaptatives_.

Une visionneuse de vidéos adaptative regroupe les versions d’une même vidéo codées à des débits et des formats différents.

Vous commencez avec votre vidéo principale originale que vous téléchargez dans le système. Dynamic Media mesure automatiquement, ou _transcode_, cette vidéo en plusieurs vidéos. Ensuite, au moment de la diffusion, il détermine intelligemment quel écran vidéo, quelle qualité et quel format utiliser et diffuse la vidéo sur le téléphone, la tablette ou l’ordinateur de bureau.

Par exemple, sur un appareil mobile iOS, il détecte une bande passante telle que 4G, 5G ou une connexion Wi-Fi, puis sélectionne automatiquement la vidéo codée selon le débit correspondant parmi ceux disponibles dans la visionneuse de vidéos adaptative. La vidéo est diffusée en continu sur des appareils mobiles, des tablettes ou des ordinateurs de bureau.

En outre, la qualité vidéo est automatiquement changée de manière dynamique si les conditions réseau changent. De même, si un client ou une cliente passe en mode plein écran sur un bureau, la visionneuse de vidéos adaptative réagit en utilisant une meilleure résolution, améliorant ainsi l’expérience de visionnage.

L’utilisation des visionneuses de vidéos adaptatives offre une lecture fluide et de qualité aux clients qui lisent des vidéos Dynamic Media sur plusieurs écrans et appareils. Voilà qui simplifie vraiment l’usage de la vidéo.

## Cas d’utilisation de Dynamic Media {#dm-journey-b}

Vous trouverez ci-dessous des solutions et des problèmes de cas d’utilisation courants que Dynamic Media peut vous aider à résoudre pour stimuler l’engagement positif des clients, la fidélité, la conversion et un retour sur investissement accru.

### Cas pratique : l’approche des fichiers principaux

L’un des cas d’utilisation les plus importants pour Dynamic Media est également l’un des plus évidents. En d’autres termes, réduire le poids des pages et des expériences, ainsi que la taille du contenu, qu’il s’agisse d’une image ou d’une vidéo diffusée.

Vous trouverez ci-dessous un exemple type d’expérience ou de page web. Environ 90 % d’une page est constituée de médias riches, tels que des images et des vidéos, qui sont généralement des fichiers beaucoup plus lourds.

![Poids de la page de contenu](/help/assets/dynamic-media/assets/dm-content-page-weight.png)
_Poids de la page de contenu d’une page web standard._

Les 10 % restants sont constitués de code HTML et CSS et de balises spécifiques. Vous souhaitez optimiser ces 90 % du poids de cette page, et Dynamic Media peut vous y aider. Vous avez déjà lu un article sur le concept _Un fichier de ressource principal avec des possibilités infinies_. Cette approche est importante pour réduire le poids global de la page. La possibilité de prendre une ressource principale et de l’utiliser sur une page des détails du produit, une page de miniature, votre panier et votre grille de recherche représente un gain de temps considérable. Cela permet également d’assurer la cohérence entre les expériences.

![Approche des fichiers principaux](/help/assets/dynamic-media/assets/dm-onefile.png)
_Cette montre est un fichier de ressource principal unique mais avec plusieurs rendus (à ne pas confondre avec des copies) créés à la volée._

Penchons-nous de plus près sur les problèmes que Dynamic Media résout grâce à ce fichier unique et certaines des solutions offertes par cette approche.

| **Problème** | **Solution Dynamic Media** |
|---|---|
| Besoin de créer et stocker chaque ressource. | Utilisez un seul fichier image qui crée automatiquement les rendus requis uniquement au moment de la diffusion. |
| Coûts de stockage élevés. | Il n’est plus nécessaire de créer et de stocker plusieurs copies d’une ressource. |
| Difficulté à maintenir la chaîne de traçabilité. | Garantit la diffusion d’expériences optimisées et cohérentes entre les appareils. |
| Absence d’historique de version. | |
| Incohérence des expériences de la marque entre les appareils. | |
| Coût superflu de la création de ressources en double. | |

Si vous pensez à un fichier, vous créez une ressource pour chaque type d’expérience. Vous partez avec une image que vous déclinez en 20, 30 ou 40 variantes, que vous devrez en fin de compte trouver le moyen de stocker et de payer le stockage.

Vous devez ensuite vous assurer que la bonne image est utilisée dans la bonne situation, ce qui peut affecter votre capacité à maintenir la cohérence de votre marques. Et si vous ne trouvez pas d’image, vous devez revenir en arrière et dupliquer ces ressources.

Dynamic Media vous permet de créer des variantes d’images, à la volée, à partir de cette image de départ. Il vous laisse toute créativité avec cette ressource principale, ce qui vous évite de solliciter sans cesse votre graphiste ou votre studio photo pour créer du contenu supplémentaire. Vous gagnez ainsi de l’argent et du temps.

Grâce à l’approche du fichier unique, vous utilisez un seul fichier principal. Créez ensuite les versions ou les rendus requis pour l’ensemble de vos sites, propriétés et expériences, uniquement au moment où ils sont diffusés ou vus par un client. Grâce à cela, vous pouvez réduire considérablement le stockage nécessaire à vos ressources et réduire la complexité globale de votre workflow. Le système de diffusion de Dynamic Media garantit que chaque image et vidéo est optimisée, se charge rapidement et s’affiche parfaitement sur tous les écrans et appareils.

### Cas pratique : la vidéo

Un autre cas d’utilisation résolu par Dynamic Media est la vidéo. La vidéo est complexe. C’est difficile à gérer. Les fichiers vidéo sont difficiles à stocker et à déplacer en raison de leur taille.

| **Problème** | **Solution Dynamic Media** |
|---|---|
| Difficulté à gérer et diffuser des vidéos optimisées pour divers appareils. | Utilisez une seule vidéo qui prend automatiquement en charge la taille de tous les appareils. |
| Les vidéos sont bloquées ou lues en basse qualité en raison de la bande passante disponible de l’utilisateur. | Diffusez de la vidéo par le biais d’un lecteur HTML qui détecte automatiquement la bande passante disponible et adapte la qualité pour garantir une lecture fluide et une haute fidélité. |
| La création manuelle de toutes les versions d’une vidéo n’est pas réalisable et prend trop de temps pour garantir un affichage et une lecture corrects sur tous les appareils. | Économisez des heures de travail de transcodage fastidieux grâce à un workflow simplifié. |
| | Libérez du temps pour un travail à plus forte valeur ajoutée. |

Les clients se rendent dans Dynamic Media avec les problèmes suivants qu’ils espèrent résoudre :

&quot;_Mon entreprise a la vidéo, et le département a dépensé une grosse somme d&#39;argent pour la créer, mais s&#39;est abstenu de la placer sur des pages ou de la diffuser. La raison était que depuis les tests, la qualité de la vidéo ne pouvait pas être garantie, ou même si elle allait vraiment jouer. Et finalement, cela affecte la marque de l&#39;entreprise et potentiellement son rôle dans la conversion._&quot;

La solution de Dynamic Media consiste à prendre ce fichier vidéo principal et à confier à Dynamic Media la création de toutes les tailles nécessaires grâce à son processus de transcodage. Vous pouvez ensuite l’ajouter au lecteur vidéo intelligent de Dynamic Media. Ce workflow garantit que si vous utilisez cette vidéo sur votre page de destination principale ou sur une page de détails de catégorie ou de produit, elle sera diffusée de façon cohérente et avec une qualité élevée.

Voici plusieurs autres cas d’utilisation à prendre en compte.

### Cas pratique : une seule source de vérité

| **Problème** | **Solution Dynamic Media** |
|---|---|
| Des ressources numériques éparpillées dans l’organisation, compartimentées dans différentes équipes ou unités opérationnelles. | Stockez et gérez toutes les ressources numériques à un emplacement central. |
| Les membres de l’équipe téléchargent et créent des versions locales. | Les membres des équipes utilisent un seul fichier principal pour créer _et_ diffuser toutes les versions nécessaires sur différents formats d’écran et appareils ; |
| Des ressources à usage unique créées pour chaque expérience et appareil. | Élimine les ressources à usage unique, ce qui permet de gagner du temps et de l’argent lors de leur création. |

### Cas pratique : recadrage intelligent optimisé par l’IA pour les médias riches

| **Problème** | **Solution Dynamic Media** |
|---|---|
| La création manuelle d’images ou de vidéos, leur mesure et leur couper manuellement pour mettre en évidence le point focal et les afficher de manière appropriée sur toutes les tailles d’écran et tous les appareils, demandent beaucoup de temps et de main-d’oeuvre. | Utilisez le recadrage intelligent dans Dynamic Media, une fonctionnalité d’IA d’Adobe Sensei, pour détecter automatiquement le point focal d’une image ou d’une vidéo et le recadrer pour pouvoir le gérer. |
| Temps perdu qui pourrait être mieux investi pour créer des expériences à fort impact. | Capture le point ciblé prévu, quelle que soit la taille de l’écran. |
| Des ressources à usage unique créées pour chaque expérience et appareil. | Élimine les tâches manuelles fastidieuses et fournit des images et des vidéos à chargement rapide de haute qualité qui s’affichent correctement sur n’importe quel appareil ou écran. |

### Cas pratique : création de médias interactifs

| **Problème** | **Solution Dynamic Media** |
|---|---|
| Expériences clients statiques et aplaties peu engageantes, peu propices à la fidélisation ou à la conversion. | Permet aux utilisateurs non techniques d’ajouter facilement et en toute transparence des éléments interactifs tels que des zones réactives, des carrousels et des visionneuses à 360°, pour offrir des expériences plus dynamiques et attrayantes. |
| Retour sur investissement limité de ressources numériques et d’expériences client médiocres. | Améliore la conversion et le retour sur investissement générés par des expériences médias riches. |

## Circulation d’une ressource dans le système Dynamic Media {#dm-journey-c}

Vous trouverez ci-dessous un workflow type pour Dynamic Media.

![Workflow Dynamic Media](/help/assets/dynamic-media/assets/dm-workflow.png)
_Circulation d’une ressource dans le système Dynamic Media._

Tout d’abord, la phase de création a pour objectif principal de créer une ressource principale. Ces ressources principales peuvent provenir de séances photo ou de fournisseurs de vidéos, ou encore de fichiers audio que vous avez créés. Vous pouvez utiliser les applications de Creative Suite d’Adobe telles qu’Adobe InDesign, Adobe Photoshop ou Adobe Illustrator pour vous aider à élaborer le contenu.

Lorsque la phase de création est terminée, vous placez la ressource dans la solution de création en la chargeant dans Dynamic Media. Dans Dynamic Media, assurez-vous que les paramètres d’image prédéfinis et les visionneuses appropriés correspondent pour vos différentes pages web sur votre site.

Enfin, vous optimisez tout ce contenu et le publiez sur les serveurs Dynamic Media afin qu’il soit disponible pour le web, l’impression, les e-mails, les ordinateurs de bureau et les appareils mobiles.

### Chargement de ressources dans Dynamic Media

Une fois la création d’une ressource principale terminée, vous la chargez dans Dynamic Media. Le type de fichier que vous chargez, ainsi que le format et la taille du fichier, sont des attributs importants de Dynamic Media. Lors du téléchargement, vous voudrez vous assurer que vous obtenez la valeur maximale pour la prise en charge d’un fichier unique.

Par exemple, l’image de montre ci-dessous fait 4 560 x 3 020 pixels. Même s’il se peut que vous n’utilisiez jamais une image de cette taille, vous pouvez toujours la télécharger. Plus l’image est grande, meilleure est la qualité délivrée par Dynamic Media, même pour un rendu de miniature. Souvenez-vous : vous pouvez facilement _diminuer_ la résolution d’une image existante. Mais si vous essayez d’_augmenter_ la résolution d’une image, le résultat risque d’être insatisfaisant.

![Formats recommandés pour le chargement dans Dynamic Media](/help/assets/dynamic-media/assets/dm-upload-formats.png)
_Considérations relatives aux chargements de ressources._

Adobe recommande de charger des ressources dans un format sans perte. En règle générale, il est préférable d’éviter le JPEG, car lorsque vous le diffusez ou que vous continuez à enregistrer en JPEG, vous perdez peu à peu en qualité d’image. Il est préférable de démarrer avec des images de la résolution la plus élevée possible dans un format sans perte qui pourra s’adapter sur le long terme. Ces formats comprennent par exemple les fichiers TIFF ou PNG.

En ce qui concerne l’espace colorimétrique, quand on pense à un canal numérique ou à un affichage web, on pense généralement au RVB (rouge, vert, bleu).

On pense rarement à diffuser quelque chose en CMJN, on se demande même dans quel cas on pourrait faire appel au CMJN. En effet, cet espace colorimétrique est le plus souvent réservé à la diffusion d’éléments imprimés. Toutefois, Dynamic Media permet de diffuser dans les deux espaces colorimétriques.

De nombreux clients continuent à imprimer, par exemple les clubs-entrepôts. Les épiceries impriment aussi souvent des prospectus une fois par semaine. Ces clients ont besoin que leurs images soient disponibles dans les deux espaces colorimétriques. Traditionnellement, cela nécessitait deux images différentes : une en RVB et une en CMJN. Cependant, vous pouvez charger des ressources CMJN directement dans Dynamic Media et demander à Dynamic Media de diffuser automatiquement des ressources RVB par le biais d’un paramètre d’image prédéfini ou d’un profil de couleurs. Il n’est pas nécessaire de créer plusieurs versions d’un fichier, en toute cohérence avec le concept _Un fichier de ressource principal avec des possibilités infinies_.

<!-- **The Value of Renditioning??? or Demo portion** -->

### Publication et prévisualisation de ressources

Une fois les ressources chargées dans Dynamic Media, il est recommandé de les _publier_ en sélectionnant les ressources, puis en cliquant sur **[!UICONTROL Publier]** ou **[!UICONTROL Publication rapide]** dans Dynamic Media. Il est nécessaire de publier les ressources si vous avez l’intention de les utiliser dans une expérience. Une fois les ressources publiées, vous pouvez les inclure dans une page web à l’aide d’une URL générée par Dynamic Media que vous copiez ou en incorporant du code sur la page.

Outre la publication manuelle de ressources, vous pouvez configurer Dynamic Media pour publier instantanément des ressources (sans intervention de l’utilisateur) au moment de leur chargement.

Après le chargement, il existe différentes manières de prévisualiser les rendus d’une ressource dans Dynamic Media. L’aperçu des rendus peut vous donner une idée de ce qu’un client voit. Une méthode d’aperçu courante consiste à sélectionner une ressource, puis à afficher ses rendus en sélectionnant un _paramètre d’image prédéfini_ comme illustré ci-dessous.

![Prévisualisation d’un rendu d’une ressource en fonction du paramètre d’image prédéfini Grande](/help/assets/dynamic-media/assets/dm-image-preset-with-url.png)
_Prévisualisation d’un rendu d’une ressource en fonction du paramètre d’image prédéfini « Grand » sélectionné. Cliquez sur le bouton URL. Le chemin d’URL qui en résulte contient le nom du paramètre d’image prédéfini « Grand » et peut être utilisé dans une page web._

L’URL ci-dessus est en ligne ! [Faites un essai](http://s7d1.scene7.com/is/image/jpearldemo/AdobeStock_28563982?$Large$){target="_blank"}.

Pour prévisualiser une ressource, une autre méthode consiste à sélectionner la ressource image, puis à sélectionner un paramètre prédéfini de _Visionneuses_ comme illustré ci-dessous.

![Prévisualisation d’une ressource en fonction du paramètre prédéfini « ZoomVertical_light » de la visionneuse](/help/assets/dynamic-media/assets/dm-viewer-preset.png)
_Prévisualisation d’une ressource en fonction du paramètre prédéfini de visionneuse « ZoomVertical_light » sélectionné. Le pointeur de la souris (`+`) a été déplacé sur la montre pour effectuer un zoom avant. Remarquez les boutons URL et Incorporer._

Le rendu ci-dessus est en ligne ! [Faites un essai](https://s7d1.scene7.com/s7viewers/html5/ZoomVerticalViewer.html?asset=jpearldemo/AdobeStock_28563982&amp;config=jpearldemo/ZoomVertical_light){target="_blank"}.

## Facultatif - En savoir plus

La première partie de ce parcours couvrait les principes de base de diverses rubriques de Dynamic Media. Si vous souhaitez en savoir plus sur ce que vous lisez, utilisez les matériaux ci-dessous pour explorer les concepts plus en détail. Sinon, vous pouvez continuer avec la deuxième partie de votre parcours. Consultez [Étapes suivantes de ce Parcours Dynamic Media](#whats-next).

{{see-also-dm}}
<!--
_Dynamic Media Help topics_

* [Work with Dynamic Media in Experience Manager](/help/assets/dynamic-media/dynamic-media.md)
* [About Smart Imaging](/help/assets/dynamic-media/imaging-faq.md)
* [How to create Adaptive Video Sets](/help/assets/dynamic-media/video.md)
* [Best practices for optimizing the quality of your images](/help/assets/dynamic-media/best-practices-for-optimizing-the-quality-of-your-images.md)
* [How to upload assets](/help/assets/add-assets.md#upload-assets)
* [How to preview assets](/help/assets/dynamic-media/previewing-assets.md)
* [How to preview 3D assets](/help/assets/dynamic-media/previewing-3d-assets.md)
* [How to deliver Dynamic Media Assets](/help/assets/dynamic-media/delivering-dynamic-media-assets.md)
* [How to publish assets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md)
* [Work with Selective Publish in Dynamic Media](/help/assets/dynamic-media/selective-publishing.md) -->

_Tutoriels Dynamic Media_

* [Utilisation de Dynamic Media avec Experience Manager Assets](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-overview-feature-video-use.html?lang=fr)
* [Bibliothèque de contenu Adobe Experience Manager](https://experienceleague.adobe.com/?lang=fr#recommended/solutions/experience-manager) (recherchez _Dynamic Media_)

_Visionneuses Dynamic Media_

* [Démonstrations en direct](https://landing.adobe.com/en/na/dynamic-media/ctir-2755/live-demos.html) de chaque visionneuse

## Étapes suivantes de ce Parcours Dynamic Media {#whats-next}

Dans la partie II de ce parcours, vous examinez attentivement les URL de Dynamic Media pour mieux comprendre ce qui se passe lorsqu’une ressource est diffusée. Vous en apprendrez également davantage sur les principes de base de la création de paramètres d’image prédéfinis pour le rendu des ressources, ainsi que sur les visionneuses d’images, à 360° et de supports variés, et leur mode de création.

C’est parti pour le [Parcours Dynamic Media : principes de base, deuxième partie](/help/assets/dynamic-media/dm-journey-part2.md#dm-journey-d).

<!-- Live as of April 28 2022. LEAVE IN HERE https://landing.adobe.com/en/na/dynamic-media/ctir-2755/index.html -->