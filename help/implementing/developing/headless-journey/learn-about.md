---
title: En savoir plus sur le développement CMS sans affichage
description: Dans cette partie du Parcours de développement AEM sans tête, découvrez la technologie sans tête et pourquoi vous l’utiliseriez.
hide: true
hidefromtoc: true
index: false
exl-id: d96f02b3-d650-4b9e-addf-409d31c80372
source-git-commit: 9e06419f25800199dea92b161bc393e6e9670697
workflow-type: tm+mt
source-wordcount: '1637'
ht-degree: 0%

---

# En savoir plus sur le développement CMS sans affichage {#learn-about}

>[!CAUTION]
>
>OUTDATED - Ce contenu de brouillon a été remplacé par la nouvelle [documentation du Parcours développeur sans affichage.](/help/journey-headless/developer/overview.md)

Dans cette partie du [Parcours de développement AEM sans affichage, ](overview.md) découvrez la technologie sans interface et pourquoi vous l’utiliseriez.

## Intention {#objective}

Ce document vous aide à comprendre la diffusion de contenu sans interface utilisateur graphique et pourquoi elle doit être utilisée. Après lecture, vous devez :

* Présentation des concepts de base et de la terminologie de la diffusion de contenu sans interface utilisateur
* Comprendre pourquoi et quand l’absence de tête est requise
* Découvrez à un haut niveau comment les concepts sans interface sont utilisés et comment ils interagissent

## Diffusion de contenu complète {#full-stack}

Depuis l’émergence des systèmes de gestion de contenu (CMS) à grande échelle et faciles d’utilisation, les entreprises les utilisent comme un emplacement central pour la gestion des messages, des marques et des communications. L’utilisation du CMS comme point central pour administrer les expériences a amélioré l’efficacité en éliminant la nécessité de dupliquer les tâches dans des systèmes disparates.

![Le CMS classique à pile complète](assets/full-stack.png)

Dans un CMS en pile complète, toutes les fonctionnalités de manipulation de votre contenu se trouvent dans le CMS. Les fonctionnalités du système constituent différents composants de la pile CMS. La solution de pile complète présente de nombreux avantages.

* Vous avez un seul système à gérer.
* Le contenu est géré de manière centralisée.
* Tous les services du système sont intégrés.
* La création de contenu est transparente.

Ainsi, si vous souhaitez ajouter un nouveau canal ou prendre en charge de nouveaux types d’expériences, vous pouvez insérer un ou plusieurs nouveaux composants dans votre pile et vous n’avez qu’un seul emplacement pour apporter vos modifications.

![Ajout d’un nouveau canal à la pile](assets/adding-channel.png)

La complexité des dépendances au sein de la pile devient rapidement visible, car vous constatez que d’autres éléments de la pile peuvent avoir besoin d’être ajustés pour tenir compte des modifications.

## Limites de diffusion complète {#limits}

L’approche de pile complète crée par nature un silo où toutes les expériences se trouvent dans un seul système. Les modifications ou les ajouts à un composant du silo nécessitent des modifications à d’autres composants, ce qui peut entraîner des modifications coûteuses et chronophages.

Cela est particulièrement vrai pour le système de présentation, qui dans les configurations traditionnelles, est souvent étroitement lié au CMS. Tout nouveau canal signifie généralement une mise à jour du système de présentation, ce qui peut affecter tous les autres canaux.

![La complexité augmente à mesure que les canaux sont ajoutés à une pile](assets/presentation-complexity.png)

Les limites de ce silo naturel peuvent apparaître lorsque vous consacrez plus d’efforts à coordonner les modifications sur tous les composants de votre pile.

Les utilisateurs attendent un engagement quel que soit la plateforme ou le point de contact, ce qui nécessite une certaine agilité dans la manière dont vous diffusez vos expériences.  Cette approche multicanal est la norme des expériences numériques et une approche entièrement empilée peut dans certaines circonstances s’avérer inflexible.

## La tête en tête {#the-head}

L’en-tête de tout système est généralement le moteur de rendu de sortie de ce système, généralement sous la forme d’une interface utilisateur graphique ou d’une autre sortie graphique.

Un serveur sans tête, par exemple, est susceptible de se trouver assis dans une salle de serveur quelque part et n’a pas de moniteur connecté. Pour y accéder, vous devez vous y connecter à distance. Dans ce cas, le moniteur est l’en-tête lorsqu’il s’occupe du rendu de la sortie du serveur. En tant que consommateur du service, fournissez votre propre tête (le moniteur) lorsque vous vous connectez à distance à celui-ci.

Lorsque nous parlons d’un CMS sans tête, le CMS gère le contenu et continue de le diffuser aux consommateurs. Cependant, en ne diffusant que le **contenu** d’une manière normalisée, un CMS sans tête omet le rendu de sortie final, laissant la **présentation** du contenu au service consommateur.

![CMS découplé](assets/headless-cms.png)

Les services consommateurs, qu’il s’agisse d’expériences AR, d’un webshop, d’expériences mobiles, d’applications web progressives (PWA), etc., récupèrent du contenu du CMS sans interface utilisateur graphique et fournissent leur propre rendu. Ils s&#39;occupent de vous donner la tête pour votre contenu.

Si vous omettez l’en-tête, le CMS est simplifié en supprimant la complexité. Cela permet également de transférer la responsabilité du rendu du contenu aux services qui ont réellement besoin du contenu et qui sont souvent mieux adaptés à ce rendu.

## Découplage {#decoupling}

La diffusion sans affichage est possible en exposant un ensemble d’interfaces de programmation d’applications (API) robustes et flexibles dans lesquelles toutes vos expériences peuvent s’appuyer. L’API sert de langage commun entre les services, les liant au niveau du contenu par le biais d’une diffusion de contenu normalisée, mais leur permettant de mettre en oeuvre leurs propres solutions.

Headless est un exemple de découplage de votre contenu de sa présentation. Ou, dans un sens plus générique, en découplant le front-end du back-end de votre pile de services. Dans une configuration sans interface utilisateur, le système de présentation (la tête) est découplé de la gestion de contenu (la queue). Les deux interagissent uniquement par le biais d’appels API.

Ce découplage signifie que chaque service consommateur (le front-end) peut créer son expérience en fonction du même contenu diffusé via les API, ce qui garantit la réutilisation et la cohérence du contenu. Les services de consommation peuvent alors mettre en oeuvre leurs propres systèmes de présentation, ce qui permet à la pile de gestion de contenu (back-end) de se dimensionner facilement horizontalement.

## Les fondements technologiques {#technology}

Une approche sans interface vous permet de créer une pile de technologies qui peut s’adapter facilement et rapidement aux futurs besoins d’expérience numérique.

Dans le passé, les API pour les CMS étaient généralement basées sur REST. Le transfert d’état de représentation (REST) fournit des ressources sous forme de texte sans état. Cela permet de lire et de modifier les ressources à l’aide d’un ensemble d’opérations prédéfini. REST a permis une grande interopérabilité entre les services sur le web en assurant une représentation sans état du contenu.

Des API REST robustes sont toujours nécessaires. Toutefois, les requêtes REST peuvent être volumineuses et détaillées. Si plusieurs consommateurs effectuent des appels REST pour tous vos canaux, cela peut avoir une incidence sur la diversité des composés et les performances.

La diffusion de contenu sans affichage utilise souvent les API GraphQL. GraphQL permet un transfert sans état similaire, mais permet des requêtes plus ciblées, réduisant le nombre total de requêtes requises et améliorant les performances. Il est courant de voir les solutions utiliser un mélange de REST et de GraphQL, en choisissant essentiellement le meilleur outil pour la tâche à accomplir.

Quelle que soit l’API choisie, en définissant un système sans tête basé sur des API courantes, vous pouvez tirer parti du dernier navigateur et d’autres technologies web telles que les applications web progressives (PWA). Les API créent une interface standard facilement extensible et adaptable.

En règle générale, le contenu est rendu côté client. Cela signifie normalement qu’une personne appelle votre contenu sur un appareil mobile, que votre CMS le diffuse, puis que l’appareil mobile (le client) est responsable du rendu du contenu que vous avez fourni. Si l’appareil est vieux ou lent, votre expérience numérique est également lente.

Le découplage du contenu de la présentation permet de mieux contrôler ces problèmes de performances côté client. Le rendu côté serveur (SSR) transfère la responsabilité du rendu du contenu du navigateur du client vers le serveur. Cela vous permet, en tant que fournisseur du contenu, d’offrir un niveau de performance garanti à votre audience si c’est ce qui est requis.

## Les défis organisationnels {#organization}

Headless vous offre toute la flexibilité nécessaire pour offrir vos expériences numériques. Mais cette flexibilité peut également présenter son propre défi.

Disposer de nombreuses chaînes différentes peut signifier qu&#39;elles ont chacune leur propre système de présentation. Même s’ils consomment tous le même contenu via les mêmes API, l’expérience peut être différente en raison des différentes présentations. L’attention et l’attention doivent être accordées pour assurer la cohérence de l’expérience client.

En implémentant des systèmes de conception soignés, en partageant des bibliothèques de modèles et en exploitant des composants de conception réutilisables ainsi que des structures côté client ouvertes et établies, des expériences homogènes peuvent être assurées, mais cela doit être planifié.

## L&#39;avenir est sans tête et l&#39;avenir est maintenant {#future}

Les expériences numériques continueront à définir la manière dont les marques interagissent avec les clients. Ce qui est passionnant dans la conception sans interface, c’est la flexibilité qu’elle nous offre pour répondre à l’évolution des attentes des clients.

Il est impossible de prédire l&#39;avenir, mais l&#39;absence de tête vous donne l&#39;agilité de réagir à ce que l&#39;avenir apporte.

## AEM et sans affichage {#aem-and-headless}

Au fur et à mesure de ce parcours de développement, vous découvrirez comment AEM prend en charge la diffusion sans interface en même temps que ses fonctionnalités de diffusion avec pile complète.

En tant que leader du secteur de la gestion de l’expérience numérique, Adobe se rend compte que la solution idéale aux défis du monde réel auxquels les créateurs d’expériences sont confrontés est rarement un choix binaire. C’est pourquoi AEM ne prend pas seulement en charge les deux modèles, mais permet également de manière unique la combinaison hybride transparente des deux, alliant les avantages d’une pile complète et sans tête, pour vous aider à mieux servir les consommateurs de votre contenu, où qu’ils se trouvent.

Ce parcours se concentre sur le modèle de diffusion de contenu sans affichage uniquement. Cependant, une fois que vous disposez de ces connaissances fondamentales, vous pouvez explorer plus en détail la manière d’exploiter la puissance des deux modèles.

## Suite {#what-is-next}

Merci d&#39;être parti de votre parcours AEM sans tête ! Maintenant que vous avez lu ce document, vous devez :

* Découvrez les concepts de base et la terminologie de la diffusion de contenu sans interface utilisateur.
* Comprendre pourquoi et quand l’absence de tête est requise.
* Découvrez à un haut niveau comment les concepts sans tête sont utilisés et comment ils interagissent.

Tirez parti de ces connaissances et continuez votre parcours sans tête AEM en consultant le document [Prise en main d’AEM sans tête en tant que Cloud Service](getting-started.md) dans lequel vous apprendrez à configurer les outils nécessaires et comment commencer à réfléchir à la manière dont l’utilisation d’un contenu sans tête et ses conditions préalables sont abordées.

## Ressources supplémentaires {#additional-resources}

Bien qu’il soit recommandé de passer à la partie suivante du parcours de développement sans interface utilisateur en consultant le document [Prise en main d’AEM sans interface en tant que Cloud Service,](getting-started.md) les ressources facultatives suivantes approfondissent certains concepts mentionnés dans ce document, mais elles ne sont pas requises pour continuer sur le parcours sans interface.

* [Présentation de l’architecture d’Adobe Experience Manager as a Cloud Service](/help/core-concepts/architecture.md)  - Présentation d’AEM en tant que structure de Cloud Service
* [AEM Tutorials sans affichage](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=fr)  : utilisez ces tutoriels pratiques pour découvrir comment utiliser les différentes options de diffusion de contenu vers des points de terminaison sans interface avec AEM et choisissez ce qui vous convient.
