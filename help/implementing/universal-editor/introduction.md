---
title: Présentation de l’éditeur visuel universel
description: Découvrez comment l’éditeur visuel universel (également appelé Editeur universel) permet de modifier n’importe quelle expérience sans tête et en mode plein écran. Découvrez comment cela peut aider les auteurs de contenu à offrir des expériences exceptionnelles, à accroître leur vitesse de diffusion du contenu et à offrir une expérience de développement dernier cri.
exl-id: d4fc2384-a0f5-4a6f-9572-62749786be4c
source-git-commit: 9cff6e94b38016f008fd8177be2e071a530d80b6
workflow-type: tm+mt
source-wordcount: '934'
ht-degree: 0%

---

# Présentation de l’éditeur visuel universel {#introduction}

Découvrez comment l’éditeur visuel universel (également appelé Editeur universel) permet de modifier n’importe quelle expérience sans tête et en mode plein écran. Découvrez comment cela peut aider les auteurs de contenu à offrir des expériences exceptionnelles, à accroître leur vitesse de diffusion du contenu et à offrir une expérience de développement dernier cri.

## Contexte {#background}

L’éditeur de page a été l’outil le plus puissant pour l’auteur de contenu AEM. L’éditeur de page offre une expérience de création WYSIWYG intuitive, visuelle et contextuelle qui nécessite une formation minimale et montre aux auteurs exactement comment le contenu apparaîtra.

Cependant, l’éditeur de page ne peut modifier que le contenu, la structure et les composants de la page qui y sont AEM. Le contenu d’aujourd’hui, cependant, provient rarement d’un seul emplacement. L’éditeur universel offre la même expérience de modification statique que l’éditeur de page, mais pour tout aspect de contenu dans n’importe quelle mise en oeuvre.

## Vraiment universel {#universal}

L’éditeur universel peut être instrumenté pour n’importe quelle mise en oeuvre, pour n’importe quel contenu et pour n’importe quel aspect du contenu.

![Qu&#39;est-ce qui rend universel ?](assets/universal.png)

### Toute implémentation {#any-implementation}

Comme les expériences peuvent être créées de différentes manières, toute mise en oeuvre peut tirer parti de l’éditeur universel afin que les auteurs puissent effectuer des modifications contextuelles.

Les utilisateurs pensent souvent qu’une mise en oeuvre sans interface limite les auteurs à modifier tout le contenu dans une interface utilisateur de formulaire, mais ce n’est pas le cas avec l’éditeur universel.

Les exigences d’une mise en oeuvre pour tirer parti d’Universal Editor sont très simples et prennent en charge :

* **N’importe quelle architecture** - Rendu côté serveur, rendu côté serveur, rendu côté client, etc.
* **N’importe quel framework** - AEM Vanilla, ou tout framework tiers comme React, Next.js, Angular, etc.
* **N’importe quel hébergement** - Peut être hébergé localement sur AEM, ou sur un domaine distant

### Tout contenu {#any-content}

Un auteur de contenu doit avoir la même expérience puissante d’édition que celle proposée auparavant par l’éditeur de page d’AEM. Mais l’éditeur universel permet aux auteurs de contenu de modifier **any** contenu visuellement et dans le contexte et prend en charge :

* **AEM des structures de page** - Imbriqué `cq:Components` de `cq:Pages`, y compris les fragments d’expérience
* **AEM de fragments de contenu** - Modifiez le contenu des fragments de contenu tels qu’ils apparaissent dans le contexte de l’expérience.
* **Documents** - La preuve de concepts a montré que les documents Word, Excel, Google Docs ou Markdown peuvent également être modifiés de la même manière (il s’agit de travaux en cours).

### N’importe quel aspect {#any-aspect}

Pour un auteur de contenu, le contenu ne concerne pas seulement les informations contenues, mais aussi leur rendu et leur réception. Le contenu est fourni avec des métadonnées et des règles d’instrumentation supplémentaires, que l’éditeur universel peut comprendre et modifier, notamment :

* **Application de la mise en page et du style** - En utilisant un système de style, le professionnel du marketing et l’auteur de contenu peuvent appliquer différents styles à leur contenu et créer différentes mises en page pour le contenu, telles que des colonnes, des carrousels, des onglets, des accordéons, etc.

## Valeur  {#value}

En découplant l’expérience d’édition de contenu d’un système de diffusion de contenu spécifique, l’éditeur devient véritablement universel et flexible, ce qui permet à l’auteur de contenu de diffuser des expériences exceptionnelles, d’augmenter la vitesse du contenu et d’offrir une expérience de développement à la pointe de la technologie.

![La valeur de l’éditeur universel](assets/value.png)

* **Diffuser des expériences exceptionnelles** - Afin de permettre aux utilisateurs de créer une expérience attrayante pour les visiteurs, l’éditeur universel permet aux utilisateurs de créer et de modifier le contenu dans le contexte de l’aperçu. Cela leur permet de créer du contenu adapté à la conception de l’expérience et qui constitue un parcours significatif pour les visiteurs.
* **Augmentation de la vitesse du contenu** - Pour rationaliser le processus de gestion des utilisateurs, l’éditeur universel permet de modifier le contenu dans l’aperçu afin de guider les utilisateurs en n’affichant que les options pertinentes pour ce contexte et en rendant le processus indépendant des sources de contenu.
* **Expérience de développement dernier cri** - Pour prendre en charge les environnements d’applications hétérogènes réels, l’éditeur universel est complètement découplé et indépendant de la technologie, ce qui permet aux développeurs d’utiliser leur pile technologique préférée pour mettre en oeuvre l’expérience.

## Éditeur visuel universel et éditeur de fragment de contenu {#universal-editor-content-fragment-editor}

À première vue, il peut sembler que l’éditeur visuel universel et l’éditeur de fragment de contenu offrent des fonctionnalités de modification similaires. Toutefois, ces éditeurs offrent des fonctionnalités très différentes et effectuent différents travaux de la part du spécialiste marketing.

### Éditeur de fragment de contenu {#content-fragment-editor}

Un professionnel du marketing souhaite créer du contenu sans avoir à se soucier de sa mise en page, de sorte qu’il puisse être réutilisé dans de nombreux contextes d’expérience.

* La tâche sous-jacente à accomplir est de mettre à l’échelle la stratégie de contenu.

### Éditeur visuel universel {#universal-editor}

Un professionnel du marketing souhaite créer du contenu adapté à la mise en page d’un contexte donné pour offrir une expérience exceptionnelle.

* La tâche sous-jacente à accomplir est de communiquer de manière convaincante avec les lecteurs.

## Feuille de route {#road-map}

Il est important de noter que l’éditeur universel est un travail en cours et que certaines des fonctionnalités présentées dans ce document sont une vision de l’éditeur final et ne sont pas nécessairement représentatives de ses capacités actuelles.

Veuillez contacter votre Adobe pour plus d’informations sur les prochaines fonctionnalités prévues pour l’éditeur universel.

## Ressources supplémentaires {#additional-resources}

Pour en savoir plus sur Universal Editor, consultez ces documents.

* [Création de contenu avec l’éditeur universel](authoring.md) - Découvrez à quel point il est facile et intuitif pour les auteurs de contenu de créer du contenu à l’aide de l’éditeur universel.
* [Publication de contenu avec l’éditeur universel](publishing.md) - Découvrez comment l’éditeur visuel universel publie du contenu et comment vos applications peuvent gérer le contenu publié.
* [Prise en main d’Universal Editor dans AEM](getting-started.md) - Découvrez comment accéder à l’éditeur universel et comment commencer à instrumenter votre première application AEM pour l’utiliser.
* [Architecture d’éditeur universelle](architecture.md) - Découvrez l’architecture d’Universal Editor et le flux de données entre ses services et calques.
* [Attributs et types](attributes-types.md) - Découvrez les attributs et les types de données requis par Universal Editor.
* [Authentification de l’éditeur universel](authentication.md) - Découvrez comment l’éditeur universel s’authentifie.
