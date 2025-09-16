---
title: Présentation de l’éditeur universel
description: L’éditeur universel est un outil de création visuel moderne conçu pour permettre à votre département marketing de produire des expériences web marquantes.
exl-id: d4fc2384-a0f5-4a6f-9572-62749786be4c
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 08997c760bf1d609dce1dd17de0c549a26083917
workflow-type: ht
source-wordcount: '948'
ht-degree: 100%

---


# Présentation de l’éditeur universel {#introduction}

L’éditeur universel est un outil de création visuel moderne conçu pour permettre à votre département marketing de produire des expériences web marquantes.

## Vue d’ensemble {#overview}

L’éditeur universel est un éditeur visuel polyvalent qui fait partie d’Adobe Experience Manager Sites. Il permet aux créateurs et créatrices d’effectuer une modification de type « ce que vous voyez est ce que vous obtiendrez » (what-you-see-is-what-you-get, WYSIWYG) de n’importe quelle expérience couplée ou découplée. Il offre les fonctionnalités suivantes :

* **Modification instantanée** : les créateurs et créatrices peuvent modifier du contenu directement dans l’expérience de prévisualisation, ce qui élimine la nécessité de localiser chaque source de contenu et d’y accéder.
* **Modification visuelle** : pendant qu’ils apportent des modifications, les créateurs et créatrices voient instantanément comment elles affectent l’expérience réelle du visiteur, ce qui réduit les points de friction.
* **Options détectables** : des options clairement étiquetées et une interface d’utilisation intuitive permettent aux créateurs et créatrices de configurer facilement des métadonnées et de composer des mises en page.
* **Non technique** : aucune expertise particulière n’est nécessaire pour effectuer des modifications. Les directives de la marque de l’entreprise sont automatiquement appliquées, ce qui facilite la mise à l’échelle des tâches de contenu au sein de votre organisation.
* **Intégration et extensibilité** : entièrement intégrés à AEM, les [points d’extension](#extensibility) flexibles de l’éditeur universel permettent d’unifier tous les outils essentiels dans une seule interface cohérente. Des fonctionnalités optimisées par l’IA aux extensions personnalisées adaptées aux besoins de votre entreprise, il permet aux équipes de rationaliser les workflows et d’améliorer la productivité sans effort.

En résumé :

* **Les créateurs et créatrices bénéficient** de la flexibilité de l’éditeur universel, car il assure une modification visuelle uniforme pour toutes les formes de contenu d’AEM.
* **Les développeurs bénéficient** de la polyvalence de l’éditeur universel, car il permet un véritable découplage de la mise en œuvre.

En tant que véritable éditeur en tant que service et plus flexible dans l’ensemble, l’éditeur universel a pour but de remplacer à terme l’[éditeur de page.](/help/sites-cloud/authoring/page-editor/introduction.md)

## Architectures prises en charge {#supported-architectures}

L’éditeur universel prend en charge les deux principales configurations d’AEM suivantes :

1. **[Edge Delivery Services](/help/edge/overview.md)** : il s’agit de l’approche privilégiée pour sa simplicité, son délai rapide d’obtention de résultats et ses performances améliorées.
1. **[Implémentations découplées](/help/headless/introduction.md)** : si vous disposez déjà d’un projet découplé ou si vous avez des exigences spécifiques en matière de rendu découplé, l’éditeur universel permet une modification visuelle de niveau professionnel sans avoir à refactoriser l’ensemble du projet. Il est compatible avec pratiquement n’importe quelle architecture (SSR, CSR), framework web (Next.js, React, Astro, etc.) et modèles d’hébergement (« Bring Your Own App », BYOA).

>[!TIP]
>
>Pour plus d’informations sur les architectures prises en charge, consultez le document [Cas d’utilisation de l’éditeur universel et parcours d’apprentissage](/help/implementing/universal-editor/use-cases.md).

## Versions d’AEM prises en charge {#aem-versions}

L’éditeur universel est pris en charge par :

* AEM as a Cloud Service (version `2023.8.13099` ou ultérieure)
* [AEM 6.5 LTS](https://experienceleague.adobe.com/fr/docs/experience-manager-65-lts/content/implementing/developing/headless/universal-editor/introduction)
   * Les hébergements sur site et AMS sont pris en charge.
* [AEM 6.5](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/implementing/developing/headless/universal-editor/introduction)
   * Les hébergements sur site et AMS sont pris en charge.

Cette documentation concerne l’utilisation de l’éditeur universel avec AEM as a Cloud Service.

## Fonctionnalités {#features}

L’éditeur universel offre de nombreuses fonctionnalités pour prendre en charge un large éventail de cas d’utilisation pour une gestion de contenu efficace.

* **[WYSIWYG](/help/sites-cloud/authoring/universal-editor/authoring.md)** : effectuez des modifications de type « ce que vous voyez et ce que vous obtenez » de toute forme de contenu web, y compris du texte brut, du texte enrichi, des médias et des métadonnées.
* **[Composition](/help/sites-cloud/authoring/universal-editor/authoring.md#editing-content)** : créez, modifiez, réorganisez, imbriquez ou supprimez des blocs de contenu de différents types (titres, boutons, teasers, sections, intégration, etc.).
* **[Mise en page](/help/sites-cloud/authoring/universal-editor/templates.md)** : utilisez des modèles de page, appliquez des styles visuels et composez des mises en page avec des blocs tels que des colonnes, des carrousels et des accordéons.
* **[Simulation d’appareil](/help/sites-cloud/authoring/universal-editor/navigation.md#emulator)** : prévisualisez et optimisez le contenu pour différents appareils des visiteurs lors de la modification.
* **Omnicanal** : réutilisez du contenu structuré et non structuré sur plusieurs canaux.
* **[Localisation](/help/sites-cloud/authoring/universal-editor/inheritance.md)** : rationalisez les workflows de traduction de contenu et gérez efficacement le contenu localisé hérité avec Multi-Site Manager.
* **Cohérence** : garantissez la conformité aux directives de la marque et l’uniformité de l’ensemble du contenu.
* **Sécurité** : [appliquez le contrôle d’accès](/help/implementing/universal-editor/authentication.md), protégez l’intégrité du contenu et suivez les modifications grâce à un [contrôle de version performant.](/help/sites-cloud/authoring/sites-console/page-versions.md)
* **[Publication](/help/sites-cloud/authoring/universal-editor/publishing.md)** : intégrez les workflows de révision, d’approbation et de publication directement dans l’éditeur.
* **Unifié** : s’intègre entièrement aux outils AEM tels que la [console Sites](/help/sites-cloud/authoring/sites-console/introduction.md), l’[éditeur de fragment de contenu](/help/sites-cloud/administering/content-fragments/overview.md), etc., pour une expérience de création uniforme.

## Extensibilité {#extensibility}

L’éditeur universel n’est pas uniquement très performant et prêt à l’emploi, il offre également des possibilités d’extension.

* Les **extensions** sont nombreuses et prêtes à l’emploi pour répondre à divers besoins, tels que la prise en charge de workflows, la génération de variantes et l’activation d’expérimentations, pour n’en citer que quelques-unes.
* **Une interface d’utilisation extensible** permet de créer vos propres extensions en utilisant les mêmes cadres sous-jacents que ceux exploités par les extensions prêtes à l’emploi, offrant une flexibilité optimale pour s’adapter aux besoins de votre projet.
* **Les points d’extension**, tels que les blocs, les types de données personnalisés et les événements, permettent une intégration transparente des besoins métier personnalisés au-delà de l’interface utilisateur.

>[!TIP]
>
>Pour plus d’informations sur l’extensibilité de l’éditeur universel, consultez le document [Extension de l’éditeur universel.](/help/implementing/universal-editor/extending.md)

## Éditeur universel et éditeur de fragments de contenu {#universal-editor-content-fragment-editor}

À première vue, on peut croire que l’éditeur universel et l’éditeur de fragments de contenu proposent des fonctionnalités de modification similaires. Toutefois, ces éditeurs proposent des fonctionnalités très différentes et effectuent différents travaux d’un professionnel ou d’une professionnelle du marketing.

### Éditeur de fragment de contenu {#content-fragment-editor}

Un professionnel ou une professionnelle du marketing souhaite créer du contenu sans avoir à se soucier de sa mise en page, de sorte qu’il puisse être réutilisé dans de nombreux contextes d’expérience.

* La tâche sous-jacente à accomplir est de mettre à l’échelle la stratégie de contenu.

### Éditeur universel {#universal-editor}

Un professionnel ou une professionnelle du marketing souhaite créer du contenu adapté à la mise en page d’un contexte donné pour proposer une expérience exceptionnelle.

* La tâche sous-jacente à accomplir est de communiquer de manière convaincante avec les lecteurs.

## Limites {#limitations}

Lorsque vous explorez l’éditeur universel et commencez à l’implémenter dans vos propres projets, veuillez garder à l’esprit les limitations suivantes.

* Pas plus de 25 ressources AEM (fragments de contenu, pages, fragments d’expérience, ressources, etc.) ne doivent être référencées comme instrumentation sur une seule page.
* AEM as a Cloud Service, [ AEM 6.5 LTS](https://experienceleague.adobe.com/fr/docs/experience-manager-65-lts/content/implementing/developing/headless/universal-editor/introduction) et [ AEM 6.5](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/implementing/developing/headless/universal-editor/introduction) sont les seuls environnements AEM pris en charge côté back-end.
* Une version `2023.8.13099` ou supérieure est requise pour AEM as a Cloud Service.
* Les responsables du contenu doivent disposer de leurs propres comptes individuels Experience Cloud.
* Dans le cadre d’AEM, l’éditeur universel [prend en charge les mêmes navigateurs de bureau qu’AEM.](/help/overview/supported-platforms.md)
   * Les versions mobiles de ces navigateurs ne sont pas prises en charge.

{{ip-allow-lists-ue}}

## Étapes suivantes {#next-steps}

Consultez le document [Cas d’utilisation de l’éditeur universel et parcours d’apprentissage](/help/implementing/universal-editor/use-cases.md) pour en savoir plus sur les cas d’utilisation courants de l’éditeur universel et découvrir les ressources de documentation appropriées pour vous aider dans votre projet.
