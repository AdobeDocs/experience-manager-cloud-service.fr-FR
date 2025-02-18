---
title: Présentation de l’éditeur universel
description: L’éditeur universel est un outil de création visuel moderne conçu pour permettre à votre organisation marketing de produire des expériences web percutantes.
exl-id: d4fc2384-a0f5-4a6f-9572-62749786be4c
feature: Developing
role: Admin, Architect, Developer
source-git-commit: ae962d89b842b0708c1ac8633bb49c86cb2edfda
workflow-type: tm+mt
source-wordcount: '949'
ht-degree: 11%

---


# Présentation de l’éditeur universel {#introduction}

L’éditeur universel est un outil de création visuel moderne conçu pour permettre à votre organisation marketing de produire des expériences web percutantes.

## Vue d’ensemble {#overview}

L’éditeur universel est un éditeur visuel polyvalent qui fait partie d’Adobe Experience Manager Sites. Il permet aux auteurs d’effectuer une modification ce que vous voyez est ce que vous obtenez (WYSIWYG) de n’importe quelle expérience couplée ou découplée. Il offre :

* **Modification instantanée** : les auteurs peuvent modifier du contenu directement dans l’expérience de prévisualisation, ce qui élimine la nécessité de localiser les sources de contenu individuelles et d’y accéder.
* **Modification visuelle** : pendant qu’ils apportent des modifications, les auteurs voient instantanément comment elles affectent l’expérience réelle du visiteur, ce qui réduit les frictions.
* **Options détectables** : des options clairement étiquetées et une interface utilisateur intuitive permettent aux auteurs de configurer facilement des métadonnées et de composer des mises en page.
* **Non technique** : aucune expertise spécialisée n’est nécessaire pour effectuer des modifications. Les directives de la marque de l’entreprise sont automatiquement appliquées, ce qui facilite la mise à l’échelle des tâches de contenu dans l’ensemble de votre organisation.
* **Intégration et extensibilité** : entièrement intégrés à AEM, les [points d’extension](#extensibility) flexibles de l’éditeur universel permettent d’unifier tous les outils essentiels dans une seule interface cohérente. Des fonctionnalités optimisées par l&#39;IA aux extensions personnalisées adaptées à vos besoins professionnels uniques, elle permet aux équipes de rationaliser les workflows et d&#39;améliorer la productivité sans effort.

En résumé :

* **Les créateurs et créatrices bénéficient** la flexibilité de l’éditeur universel, car il prend en charge la même modification visuelle cohérente pour toutes les formes de contenu AEM.
* **Les développeurs bénéficient** de la polyvalence de l’éditeur universel, car il prend en charge le véritable découplage de la mise en œuvre.

En tant que véritable éditeur en tant que service et plus flexible dans l’ensemble, l’éditeur universel a l’intention de remplacer à terme l’[éditeur de page.](/help/sites-cloud/authoring/page-editor/introduction.md)

## Architectures prises en charge {#supported-architectures}

L’éditeur universel prend en charge les deux principales configurations d’AEM suivantes :

1. **[Edge Delivery Services](/help/edge/overview.md)** : il s’agit de l’approche privilégiée pour sa simplicité, son délai d’évaluation plus rapide et ses performances améliorées.
1. **[Implémentations découplées](/help/headless/introduction.md)** : si vous disposez déjà d’un projet découplé ou si vous avez des exigences spécifiques en matière de rendu découplé, l’éditeur universel permet une modification visuelle de niveau professionnel sans avoir à refactoriser l’ensemble du projet. Il est compatible avec pratiquement n’importe quelle architecture (SSR, CSR), framework web (Next.js, React, Astro, etc.) et modèles d’hébergement (« apportez votre propre application »).

>[!TIP]
>
>Consultez le document [Cas d’utilisation de l’éditeur universel et parcours d’apprentissage](/help/implementing/universal-editor/use-cases.md) pour plus d’informations sur les architectures prises en charge.

## Versions d’AEM prises en charge {#aem-versions}

L’éditeur universel est pris en charge par :

* AEM as a Cloud Service (version `2023.8.13099` ou ultérieure)
* AEM 6.5 (pack de services 21 ou 22 plus un pack de fonctionnalités)

Cette documentation est destinée à l’utilisation de l’éditeur universel avec AEM as a Cloud Service. Pour utiliser l’éditeur universel avec AEM 6.5, [consultez la documentation d’AEM 6.5](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/developing/headless/universal-editor/introduction?lang=en).

## Fonctions {#features}

L’éditeur universel offre de nombreuses fonctionnalités pour prendre en charge un large éventail de cas d’utilisation pour une gestion de contenu efficace.

* **[WYSIWYG](/help/sites-cloud/authoring/universal-editor/authoring.md)** : effectuez la modification de ce que vous voyez et de ce que vous obtenez de tout type de contenu web, y compris du texte brut, du texte enrichi, des médias et des métadonnées.
* **[Composition](/help/sites-cloud/authoring/universal-editor/authoring.md#editing-content)** : création, modification, réorganisation, imbrication ou suppression de blocs de contenu de différents types (titres, boutons, teasers, sections, intégration, etc.).
* **[Disposition](/help/sites-cloud/authoring/universal-editor/templates.md)** : utilisez des modèles de page, appliquez des styles visuels et composez des mises en page avec des blocs tels que des colonnes, des carrousels et des accordéons.
* **[Simulation d’appareil](/help/sites-cloud/authoring/universal-editor/navigation.md#emulator)** : prévisualisez et optimisez le contenu pour différents appareils visiteur lors de la modification.
* **Omnicanal** : réutilisez du contenu structuré et non structuré sur plusieurs canaux.
* **[Localisation](/help/sites-cloud/authoring/universal-editor/inheritance.md)** : rationalisez les workflows de traduction de contenu et gérez efficacement l’héritage de contenu localisé avec Multi-Site Manager.
* **Cohérence** : garantissez la conformité aux directives de la marque et conservez l’uniformité de l’ensemble du contenu.
* **Sécurité** : [Appliquez le contrôle d’accès](/help/implementing/universal-editor/authentication.md) protégez l’intégrité du contenu et suivez les modifications grâce à un [contrôle de version robuste.](/help/sites-cloud/authoring/sites-console/page-versions.md)
* **[Publication](/help/sites-cloud/authoring/universal-editor/publishing.md)** : intégrez les workflows de révision, d’approbation et de publication directement dans l’éditeur.
* **Unifié** : s’intègre entièrement aux outils AEM tels que [la console Sites](/help/sites-cloud/authoring/sites-console/introduction.md) [l’éditeur de fragment de contenu](/help/sites-cloud/administering/content-fragments/overview.md) etc., offrant ainsi une expérience de création cohérente.

## Extensibilité {#extensibility}

L’éditeur universel n’est pas seulement très performant et prêt à l’emploi, il offre également un certain nombre de possibilités d’extension.

* Les **extensions** sont nombreuses et prêtes à l’emploi pour prendre en charge des exigences telles que la prise en charge des workflows, la génération de variations et l’activation de l’expérimentation, pour n’en citer que quelques-unes.
* **Une interface utilisateur extensible** vous permet de créer vos propres extensions à l’aide des mêmes frameworks que ceux des extensions prêtes à l’emploi. Vous bénéficiez ainsi d’une flexibilité optimale pour vous adapter aux besoins de votre projet.
* **Points d’extension** tels que les blocs, les types de données personnalisés et les événements, permettent une intégration transparente des besoins commerciaux personnalisés au-delà de l’interface utilisateur.

>[!TIP]
>
>Pour plus d’informations sur l’extensibilité de l’éditeur universel, consultez le document [Extension de l’éditeur universel.](/help/implementing/universal-editor/extending.md)

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
* Une version `2023.8.13099` ou supérieure est requise pour AEM as a Cloud Service.
* Les auteurs de contenu doivent disposer de leurs propres comptes Experience Cloud.
* Dans le cadre d’AEM, l’éditeur universel [prend en charge les mêmes navigateurs de bureau qu’AEM.](/help/overview/supported-platforms.md)
   * Les versions mobiles de ces navigateurs ne sont pas prises en charge.

{{ue-ip-allow-lists}}

## Étapes suivantes {#next-steps}

Consultez le document [Cas d’utilisation de l’éditeur universel et parcours d’apprentissage](/help/implementing/universal-editor/use-cases.md) pour en savoir plus sur les cas d’utilisation courants de l’éditeur universel et découvrir les ressources de documentation appropriées pour vous aider dans votre projet.
