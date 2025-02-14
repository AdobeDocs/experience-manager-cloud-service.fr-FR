---
title: Présentation de l’éditeur universel
description: Découvrez comment l’éditeur universel active la modification ce que vous voyez est ce que vous obtenez (WYSIWYG) de n’importe quelle expérience couplée et découplée. Découvrez comment cela peut aider les créateurs et les créatrices de contenu à proposer des expériences exceptionnelles, à accroître la vitesse de leur contenu et à offrir une expérience de développement à la pointe de la technologie.
exl-id: d4fc2384-a0f5-4a6f-9572-62749786be4c
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 2947c4cb1fad7e1c7635a0e423a4adfe23013f79
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 49%

---


# Présentation de l’éditeur universel {#introduction}

L’éditeur universel est un éditeur visuel polyvalent qui fait partie d’Adobe Experience Manager Sites. Il permet aux auteurs d’effectuer une modification ce que vous voyez est ce que vous obtenez (WYSIWYG) de n’importe quelle expérience couplée ou découplée. Découvrez comment cela peut aider les créateurs et les créatrices de contenu à proposer des expériences exceptionnelles et à offrir une liberté inégalée aux développeurs et aux développeuses.

## Contexte {#background}

L’éditeur universel offre une expérience de création contextuelle efficace et intuitive qui nécessite une formation minimale. Grâce à cela, les auteurs et autrices peuvent gérer leur contenu directement dans le contexte de l’expérience web, exactement comme il apparaîtra aux visiteurs et aux visiteuses. Étant un véritable éditeur en tant que service et globalement plus flexible, il a l’intention de remplacer à terme l’éditeur de page.

Les auteurs bénéficient de la flexibilité de l’éditeur universel, car il prend en charge la même modification visuelle cohérente pour tous les types de contenu AEM : la modification statique et la composition de mise en page sont possibles de la même manière pour les fragments de contenu et les composants de page. Les deux formes de contenu peuvent même être modifiées lors d’une affichage côte à côte dans une expérience web, sans que les auteurs aient à changer de contexte. Il s’agit d’une amélioration considérable par rapport aux éditeurs précédents d’AEM qui ne prenaient en charge qu’un seul type de contenu.

Les développeurs bénéficient de la polyvalence de l’éditeur universel, car il prend également en charge le véritable découplage de la mise en œuvre. Il permet aux développeurs d’utiliser quasiment n’importe quel framework ou architecture de leur choix, sans imposer de contraintes de SDK ou de technologie. Cette flexibilité permet même d’instrumenter facilement les applications web existantes pour l’éditeur universel sans avoir à les reconfigurer.

## Vraiment universel {#universal}

L’éditeur universel peut être instrumenté pour n’importe quelle mise en œuvre, pour n’importe quel contenu et pour n’importe quel aspect du contenu.

![Qu’est-ce qui le rend universel ?](assets/universal.png)

### N’importe quelle mise en œuvre {#any-implementation}

Comme les expériences peuvent être créées de différentes manières, toute mise en œuvre peut utiliser l’éditeur universel afin que les créateurs et les créatrices puissent effectuer des modifications contextuelles.

Les utilisateurs et les utilisatrices pensent souvent qu’une implémentation découplée limite les créateurs et les créatrices à modifier tout le contenu dans une interface utilisateur de formulaire, mais ce n’est pas le cas avec l’éditeur universel

Les exigences d’une mise en œuvre pour utiliser l’éditeur universel sont très simples et prennent en charge :

* **N’importe quelle architecture** - Rendu côté serveur, rendu côté périphérie, rendu côté client, etc.
* **N’importe quel framework** - AEM Vanilla, ou tout framework tiers comme React, Next.js, Angular, etc.
* **N’importe quel hébergement** - Peut être hébergé localement sur AEM ou sur un domaine distant

### Tout contenu {#any-content}

Un créateur ou une créatrice de contenu doit avoir la même expérience puissante d’édition que celle proposée auparavant par l’éditeur de page d’AEM. Mais l’éditeur universel permet aux créateurs et créatrices de contenu de modifier **tout** contenu visuellement et dans le contexte et prend en charge :

* **Structures de page AEM** - `cq:Components` imbriqués de `cq:Pages`, y compris les fragments d’expérience
* **Fragments de contenu AEM** - Modifiez le contenu des fragments de contenu tels qu’ils apparaissent dans le contexte de l’expérience.
* **Documents** - La démonstration de faisabilité a montré que les documents Word, Excel, Google Docs ou Markdown peuvent également être modifiés de la même manière (travaux en cours).

### N’importe quel aspect {#any-aspect}

Pour un créateur ou une créatrice de contenu, le contenu ne concerne pas seulement les informations contenues, mais aussi leur rendu et leur réception. Le contenu est fourni avec des métadonnées et des règles d’instrumentation supplémentaires, que l’éditeur universel peut comprendre et modifier, notamment :

* **Application de la mise en page et du style** - En utilisant un système de style, le professionnel ou la professionnelle du marketing et le créateur ou la créatrice de contenu peuvent appliquer différents styles à leur contenu et créer différentes mises en page pour le contenu, telles que des colonnes, des carrousels, des onglets, des accordéons, etc.

## Valeur {#value}

En découplant l’expérience d’édition de contenu d’un système de diffusion de contenu spécifique, l’éditeur devient véritablement universel et flexible, ce qui permet au créateur ou à la créatrice de contenu de diffuser des expériences exceptionnelles, d’augmenter la vitesse du contenu et de proposer une expérience de développement à la pointe de la technologie.

![Valeur de l’éditeur universel](assets/value.png)

* **Diffusion d’expériences exceptionnelles** - Afin de permettre aux utilisateurs et aux utilisatrices de créer une expérience attrayante pour les visiteurs et les visiteuses, l’éditeur universel leur permet de créer et de modifier le contenu dans le contexte de l’aperçu. Cela leur permet de créer du contenu adapté à la conception de l’expérience, ce qui constitue un parcours significatif pour les visiteurs et les visiteuses.
* **Augmentation de la vitesse du contenu** - Pour rationaliser le processus de gestion des utilisateurs et des utilisatrices, l’éditeur universel permet de modifier le contenu dans l’aperçu afin de guider les utilisateurs et lesutilisatrices en n’affichant que les options pertinentes pour ce contexte et en rendant le processus indépendant des sources de contenu.
* **Expérience de développement à la pointe de la technologie** - Pour prendre en charge les environnements d’applications hétérogènes réels, l’éditeur universel est complètement découplé et indépendant de la technologie, ce qui permet aux développeurs et aux développeuses d’utiliser leur pile technologique préférée pour mettre en œuvre l’expérience.

## Éditeur universel et éditeur de fragment de contenu {#universal-editor-content-fragment-editor}

À première vue, il peut sembler que l’éditeur universel et l’éditeur de fragment de contenu fournissent des fonctionnalités de modification similaires. Toutefois, ces éditeurs proposent des fonctionnalités très différentes et effectuent différents travaux d’un professionnel ou d’une professionnelle du marketing.

### Éditeur de fragment de contenu {#content-fragment-editor}

Un professionnel ou une professionnelle du marketing souhaite créer du contenu sans avoir à se soucier de sa mise en page, de sorte qu’il puisse être réutilisé dans de nombreux contextes d’expérience.

* La tâche sous-jacente à accomplir est de mettre à l’échelle la stratégie de contenu.

### Éditeur universel {#universal-editor}

Un professionnel ou une professionnelle du marketing souhaite créer du contenu adapté à la mise en page d’un contexte donné pour proposer une expérience exceptionnelle.

* La tâche sous-jacente à accomplir est de communiquer de manière convaincante avec les lecteurs.

## Limites {#limitations}

Pendant que vous explorez l’éditeur universel et que vous progressez dans sa mise en œuvre dans vos propres projets, gardez à l’esprit les limites suivantes.

* Pas plus de 25 ressources AEM (fragments de contenu, pages, fragments d’expérience, Assets, etc.) ne doivent être référencées en tant qu’instrumentation sur une seule page.
* AEM as a Cloud Service et [AEM 6.5](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/implementing/developing/headless/universal-editor/introduction) sont les seuls serveurs principaux AEM pris en charge.
* La version `2023.8.13099` ou ultérieure d’AEM as a Cloud Service est requise.
* Les auteurs de contenu doivent disposer de leurs propres comptes Experience Cloud.
* Dans le cadre d’AEM, l’éditeur universel [prend en charge les mêmes navigateurs de bureau qu’AEM.](/help/overview/supported-platforms.md)
   * Les versions mobiles de ces navigateurs ne sont pas prises en charge.

{{ue-ip-allow-lists}}

## Étapes suivantes {#next-steps}

Consultez le document [Cas d’utilisation de l’éditeur universel et parcours d’apprentissage](/help/implementing/universal-editor/use-cases.md) pour en savoir plus sur les cas d’utilisation courants de l’éditeur universel et découvrir les ressources de documentation appropriées pour vous aider dans votre projet.
