---
title: Éditeur de page et éditeur universel
description: L’éditeur de page reste pris en charge par Adobe, mais l’éditeur universel offre des possibilités intéressantes pour vos nouveaux projets.
feature: Developing
role: Admin, Architect, Developer
exl-id: 0a13fb52-623e-4aff-b254-186d8d117e4d
source-git-commit: 9da4c90c56b7a82a41604173100ad6503a4a06d0
workflow-type: tm+mt
source-wordcount: '1069'
ht-degree: 3%

---

# Éditeur de page et éditeur universel {#page-editor-universal-editor}

L’éditeur de page reste pris en charge par Adobe, mais l’éditeur universel offre des possibilités intéressantes pour vos nouveaux projets.

## Contexte {#background}

Adobe a introduit l’[éditeur universel](/help/implementing/universal-editor/introduction.md) en 2024 en tant qu’éditeur rationalisé adoptant une approche de développement moderne basée sur JavaScript. L’éditeur universel offre une vision d’Adobe pour une expérience visuelle de création de contenu transparente et extensible.

Reconnaissant la richesse des fonctionnalités de l’[éditeur de page](/help/sites-cloud/authoring/page-editor/introduction.md) et les innombrables projets qui y ont investi au cours de la longue histoire d’AEM, Adobe continue à prendre entièrement en charge l’éditeur de page, bien que l’innovation se concentre sur l’éditeur universel.

## Recommandation {#recommendation}

Bien qu’il se réduise rapidement, il reste un écart de fonctionnalité entre l’éditeur universel et l’éditeur de page ([une comparaison des fonctionnalités est disponible dans la section suivante](#feature-comparison)).

En règle générale :

* **Les nouveaux projets** doivent utiliser l’éditeur universel par défaut.
* **Projets existants** devez continuer à utiliser l’éditeur de page et tenir compte de l’éditeur universel lors du démarrage d’Edge Delivery ou d’efforts découplés.

**L’éditeur choisi doit être entièrement adapté aux besoins de votre projet individuel.**

## Comparaison des fonctionnalités {#feature-comparison}

Comme l’écart de fonctionnalités entre les deux éditeurs diminue constamment, veillez à consulter les [ notes de mise à jour de l’éditeur universel ](/help/release-notes/universal-editor/current.md) pour connaître les derniers développements.

### Diffusion {#delivery}

|  | Éditeur de page | Remarques | Éditeur universel | Remarques |
|---|---|---|---|---|
| [Publier la diffusion](/help/sites-cloud/authoring/author-publish.md) | [!BADGE Disponible]{type=Positive} | Recommandé pour une utilisation avec les composants principaux et les projets AEM traditionnels | [!BADGE Indisponible]{type=Negative} | Les pages AEM traditionnelles reposent généralement sur plusieurs fonctionnalités spécifiques à l’éditeur de page, qui sont difficiles à répliquer en l’état avec l’éditeur universel. |
| [Edge Delivery](/help/edge/overview.md) | [!BADGE Indisponible]{type=Negative} |  | [!BADGE Disponible]{type=Positive} |  |
| [ Diffusion découplée ](/help/headless/introduction.md) | [!BADGE Partiellement disponible]{type=Caution} | Uniquement avec [l’éditeur de SPA](/help/implementing/developing/hybrid/introduction.md) qui a été [obsolète](/help/implementing/developing/hybrid/spa-editor-deprecation.md) en faveur de l’éditeur universel | [!BADGE Disponible]{type=Positive} | L’éditeur universel permet aux développeurs d’apporter leur propre application web sans imposer d’exigences de framework spécifiques ou de contraintes d’implémentation. |

### Persistance {#persistence}

|  | Éditeur de page | Remarques | Éditeur universel | Remarques |
|---|---|---|---|---|
| Modification des composants de page | [!BADGE Disponible]{type=Positive} |  | [!BADGE Disponible]{type=Positive} |  |
| Modification de [fragments de contenu](/help/assets/content-fragments/content-fragments.md) | [!BADGE Indisponible]{type=Negative} |  | [!BADGE Disponible]{type=Positive} | Inclure de nouveaux fragments et réorganiser leur ordre |

### Fonctionnalités {#capabilities}

|  | Éditeur de page | Remarques | Éditeur universel | Remarques |
|---|---|---|---|---|
| Modèles de page | [!BADGE Disponible]{type=Positive} |  | [!BADGE Disponible]{type=Positive} | L’éditeur universel est indépendant du système de modèles utilisé. Cependant, le modèle d’implémentation type favorise les modèles définis par le développeur, car l’outil frontal moderne permet aux développeurs et aux développeuses de définir et de gérer plus facilement la logique de modèle directement dans le code. |
| Modification de WYSIWYG | [!BADGE Disponible]{type=Positive} | Limité à pages | [!BADGE Disponible]{type=Positive} | Pages et fragments de contenu pris en charge |
| [Générer des variations](/help/generative-ai/generate-variations.md) | [!BADGE Indisponible]{type=Negative} |  | [!BADGE Disponible]{type=Positive} | [Disponible en tant qu’extension](/help/implementing/universal-editor/extending.md) |
| Insérer un nouveau bloc | [!BADGE Disponible]{type=Positive} |  | [!BADGE Disponible]{type=Positive} |  |
| Réorganiser le bloc | [!BADGE Disponible]{type=Positive} | Possible avec un glisser-déposer contextuel, mais pas dans le panneau latéral « arborescence » | [!BADGE Disponible]{type=Positive} | Possible par glisser-déposer dans le panneau latéral « vue d’arborescence », mais pas encore en contexte (prévu) |
| Bloc Couper/Copier-Coller | [!BADGE Disponible]{type=Positive} |  | [!BADGE Indisponible]{type=Negative} | Planifiés |
| Application de styles | [!BADGE Disponible]{type=Positive} | Les styles peuvent être appliqués aux composants à l’aide [du système de style](/help/sites-cloud/authoring/page-editor/style-system.md). | [!BADGE Disponible]{type=Positive} | Les styles peuvent être appliqués à l’aide des propriétés standard du composant (ou du fragment de contenu). Le même sélecteur de style n’est pas disponible dans l’éditeur universel, mais il est possible d’obtenir une expérience utilisateur très similaire à l’aide d’un widget à sélection multiple. |
| Appliquer la mise en page | [!BADGE Disponible]{type=Positive} | Sites doit implémenter la [grille réactive AEM](/help/implementing/developing/introduction/responsive-design.md) pour permettre aux auteurs de redimensionner les composants sur trois points d’arrêt prédéfinis. | [!BADGE Disponible]{type=Positive} | Les mises en page peuvent être appliquées à l’aide des propriétés de composant standard (ou de fragment de contenu). Toutefois, la grille réactive n’est pas prise en charge. |
| Annuler-rétablir | [!BADGE Disponible]{type=Positive} |  | [!BADGE Indisponible]{type=Negative} | Planifiés |
| Publier (également pour la prévisualisation) | [!BADGE Disponible]{type=Positive} |  | [!BADGE Disponible]{type=Positive} |  |
| [Démarrer le workflow](/help/sites-cloud/authoring/workflows/overview.md) | [!BADGE Disponible]{type=Positive} |  | [!BADGE Disponible]{type=Positive} | Disponible en tant qu’extension |
| Commentaire | [!BADGE Disponible]{type=Positive} | Utilisation de [annotations](/help/sites-cloud/authoring/page-editor/annotations.md) | [!BADGE Indisponible]{type=Negative} | Planifiés |
| Intégration de Workfront | [!BADGE Indisponible]{type=Negative} |  | [!BADGE Disponible]{type=Positive} | Disponible en tant qu’extension |
| [ MSM et lancements ](/help/sites-cloud/administering/msm-and-translation.md) | [!BADGE Disponible]{type=Positive} |  | [!BADGE Disponible]{type=Positive} | Disponible pour les pages en tant qu’extension |
| Expérimentation et personnalisation | [!BADGE Disponible]{type=Positive} | Utilisation du [mode cible](/help/sites-cloud/authoring/personalization/targeted-content.md) | [!BADGE Disponible]{type=Positive} | Disponible en tant qu’extension pour Edge Delivery Services |
| Arborescence de contenu | [!BADGE Disponible]{type=Positive} |  | [!BADGE Disponible]{type=Positive} | Permet également de réorganiser l’arborescence |
| Simulation d’appareil | [!BADGE Disponible]{type=Positive} | [Les appareils configurés peuvent être simulés](/help/sites-cloud/administering/responsive-layout.md) mais l’utilisateur ne peut pas saisir manuellement d’autres dimensions d’écran à simuler. | [!BADGE Disponible]{type=Positive} | [Il est possible de saisir manuellement toutes les dimensions d’écran à simuler](/help/sites-cloud/authoring/universal-editor/navigation.md#emulator) mais les points d’arrêt par défaut ne peuvent pas être configurés. |
| [Verrouillage de page](/help/sites-cloud/authoring/sites-console/managing-pages.md) | [!BADGE Disponible]{type=Positive} |  | [!BADGE Disponible]{type=Positive} | Respecte le statut de verrouillage défini dans la console Sites avec l’extension disponible pour verrouiller/déverrouiller des pages à partir de l’éditeur |
| [Propriétés de la page](/help/sites-cloud/authoring/sites-console/page-properties.md) | [!BADGE Disponible]{type=Positive} |  | [!BADGE Disponible]{type=Positive} | Disponible auprès de l’administrateur du site, avec extension pour accéder également aux propriétés des pages à partir de l’éditeur |
| Propriétés multi-champs | [!BADGE Disponible]{type=Positive} |  | [!BADGE Indisponible]{type=Negative} | Planifiés |
| [DAM distant](/help/assets/dynamic-media-open-apis-overview.md) | [!BADGE Disponible]{type=Positive} |  | [!BADGE Disponible]{type=Positive} |  |
| [Contrôle de version des pages](/help/sites-cloud/authoring/sites-console/page-versions.md) | [!BADGE Disponible]{type=Positive} |  | [!BADGE Disponible]{type=Positive} |  |
| [TimeWarp](/help/sites-cloud/authoring/sites-console/page-versions.md#timewarp) et [Diff View](/help/sites-cloud/authoring/sites-console/page-diff.md) | [!BADGE Disponible]{type=Positive} |  | [!BADGE Indisponible]{type=Negative} | Planifiés |
| Afficher dans l’administrateur | [!BADGE Disponible]{type=Positive} |  | [!BADGE Disponible]{type=Positive} | Disponible en tant qu’extension pour les pages |
| Affichage du statut de la page | [!BADGE Disponible]{type=Positive} |  | [!BADGE Indisponible]{type=Negative} | Disponible dans la console Sites |
| Extensibilité | [!BADGE Disponible]{type=Positive} | En tant que recouvrements AEM | [!BADGE Disponible]{type=Positive} | Comme des points d’extension clairement définis utilisant App Builder et très peu de connaissances spécifiques à AEM |

## Adoption de l’éditeur universel {#adopt-ue}

L’éditeur universel offre de nombreux avantages, ce qui en fait une excellente solution pour les nouveaux projets.

* **Modification visuelle :** comme pour l’éditeur de page, les auteurs peuvent modifier le contenu directement dans l’aperçu et voir instantanément comment leurs modifications affectent l’expérience du visiteur.
* **Préparation à l’avenir :** la feuille de route d’AEM donne la priorité à l’éditeur universel en tant qu’éditeur visuel. Son adoption garantit l’accès aux dernières innovations et améliorations.
* **Intégration plus simple :** aucun SDK spécifique à AEM n’est nécessaire pour utiliser l’éditeur universel, ce qui réduit le verrouillage de tech stack.
* **Apportez votre propre application :** l’éditeur universel prend en charge n’importe quelle structure ou architecture web, ce qui permet l’adoption sans nécessiter de refactorisation complexe.
* **Extensibilité :** l’éditeur universel bénéficie d’un cadre d’extension [ robuste,](/help/implementing/universal-editor/extending.md) qui comprend des intégrations à GenAI, Workfront, etc.

### Migration vers l’éditeur universel {#migrate-ue}

Il n’existe pas de chemin de migration direct de l’éditeur de page vers l’éditeur universel. Cela est dû à des différences fondamentales entre les deux technologies.

* L’éditeur universel ne réintroduit pas de fonctionnalités telles que l’éditeur de modèles, le système de style ou la grille réactive.
   * Ces cas d’utilisation peuvent désormais être gérés plus efficacement avec un CSS front-end et JavaScript allégés dans les projets Edge Delivery Services ou découplés.
* Comme l’éditeur universel est un éditeur en tant que service, il ne peut pas permettre aux personnes en charge de l’implémentation d’injecter des éléments CSS ou JS dans les boîtes de dialogue des composants.
   * Cela empêche la conversion automatique des boîtes de dialogue de composant à partir de l’éditeur de page.
   * Cela affecte de nombreux domaines des boîtes de dialogue, tels que les widgets personnalisés, la validation des champs, l’affichage/le masquage des règles et les personnalisations basées sur des modèles.
      * Bien que de telles fonctionnalités soient toujours possibles, l’éditeur universel les résout par le biais de la configuration, au lieu d’un JavaScript personnalisé déployé dans les boîtes de dialogue.

Bien que l’éditeur universel puisse techniquement activer la modification des pages pour les projets AEM traditionnels (par exemple, créés avec les composants principaux), ces sites reposent généralement sur plusieurs fonctionnalités spécifiques à l’éditeur de page, telles que le système de style, la grille réactive, les modèles modifiables et le code JavaScript personnalisé dans les boîtes de dialogue.

Dans la mesure où l’éditeur universel suit une approche plus rationalisée et moderne qui ne prend pas en charge ces fonctionnalités héritées, la migration de ces sites nécessiterait une refactorisation importante. Pour cette raison, **la migration des sites de l’éditeur de page vers l’éditeur universel n’est recommandée que pour les projets qui passent à Edge Delivery Services.**
