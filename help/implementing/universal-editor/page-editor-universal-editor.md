---
title: Éditeur de page et éditeur universel
description: L’éditeur de page continue d’être pris en charge par Adobe, mais l’éditeur universel offre des possibilités intéressantes pour vos nouveaux projets.
feature: Developing
role: Admin, Architect, Developer
exl-id: 0a13fb52-623e-4aff-b254-186d8d117e4d
source-git-commit: fd52e51c336e65ae698c5102cbe00b90e7038b5e
workflow-type: tm+mt
source-wordcount: '1068'
ht-degree: 99%

---

# Éditeur de page et éditeur universel {#page-editor-universal-editor}

L’éditeur de page continue d’être pris en charge par Adobe, mais l’éditeur universel offre des possibilités intéressantes pour vos nouveaux projets.

## Contexte {#background}

Adobe a introduit l’[éditeur universel](/help/implementing/universal-editor/introduction.md) en 2024 en tant qu’éditeur rationalisé adoptant une approche de développement moderne basée sur JavaScript. L’éditeur universel constitue la vision d’Adobe pour une expérience visuelle de création de contenu transparente et extensible.

Reconnaissant la richesse des fonctionnalités de l’[éditeur de page](/help/sites-cloud/authoring/page-editor/introduction.md) et les innombrables projets qui y ont été investis au cours de la longue histoire d’AEM, Adobe continue à prendre entièrement en charge l’éditeur de page, bien que l’innovation se concentre sur l’éditeur universel.

## Recommandation {#recommendation}

Bien qu’il se réduise rapidement, il reste un écart de fonctionnalité entre l’éditeur universel et l’éditeur de page ([une comparaison des fonctionnalités est disponible dans la section suivante](#feature-comparison)).

En règle générale :

* Les **nouveaux projets** doivent utiliser l’éditeur universel par défaut.
* Les **projets existants** devez continuer à utiliser l’éditeur de page et tenir compte de l’éditeur universel lors des efforts dans Edge Delivery ou découplés.

**L’éditeur choisi doit être entièrement adapté aux besoins de votre projet.**

## Comparaison des fonctionnalités {#feature-comparison}

L’écart de fonctionnalités entre les deux éditeurs se réduisant constamment, veillez à consulter les [notes de mise à jour de l’éditeur universel](/help/release-notes/universal-editor/current.md) pour connaître les derniers développements.

### Diffusion {#delivery}

|  | Éditeur de page | Notes | Éditeur universel | Notes |
|---|---|---|---|---|
| [Diffusion Publier](/help/sites-cloud/authoring/author-publish.md) | [!BADGE Disponible]{type=Positive} | Recommandé pour une utilisation avec les composants principaux et les projets AEM traditionnels. | [!BADGE Non disponible]{type=Negative} | Les pages AEM traditionnelles reposent généralement sur plusieurs fonctionnalités spécifiques à l’éditeur de page, qui sont difficiles à répliquer telles quelles avec l’éditeur universel. |
| [Diffusion Edge](/help/edge/overview.md) | [!BADGE Non disponible]{type=Negative} |  | [!BADGE Disponible]{type=Positive} |  |
| [Diffusion découplée](/help/headless/introduction.md) | [!BADGE Partiellement disponible]{type=Caution} | Uniquement avec [l’éditeur de SPA](/help/implementing/developing/hybrid/introduction.md) qui a été [abandonné](/help/implementing/developing/hybrid/spa-editor-deprecation.md) en faveur de l’éditeur universel. | [!BADGE Disponible]{type=Positive} | L’éditeur universel permet aux développeurs et développeuses d’apporter leur propre application web sans imposer d’exigences de cadre ou de contraintes de mise en œuvre spécifiques. |

### Persistance {#persistence}

|  | Éditeur de page | Notes | Éditeur universel | Notes |
|---|---|---|---|---|
| Modification des composants de la page | [!BADGE Disponible]{type=Positive} |  | [!BADGE Disponible]{type=Positive} |  |
| Modification des [fragments de contenu](/help/assets/content-fragments/content-fragments.md) | [!BADGE Non disponible]{type=Negative} |  | [!BADGE Disponible]{type=Positive} | Ajout de l’insertion de nouveaux fragments et de leur réorganisation |

### Fonctionnalités {#capabilities}

|  | Éditeur de page | Notes | Éditeur universel | Notes |
|---|---|---|---|---|
| Modèles de page | [!BADGE Disponible]{type=Positive} |  | [!BADGE Disponible]{type=Positive} | L’éditeur universel est indépendant du système de modèle utilisé. Cependant, le modèle de mise en œuvre type favorise les modèles définis par le développeur ou la développeuse, car l’outil front-end moderne permet aux développeurs et aux développeuses de définir et de gérer plus facilement la logique de modèle directement dans le code. |
| Modification WYSIWYG | [!BADGE Disponible]{type=Positive} | Limité à Pages | [!BADGE Disponible]{type=Positive} | Prise en charge des pages et des fragments de contenu |
| [Générer des variations](/help/generative-ai/generate-variations.md) | [!BADGE Non disponible]{type=Negative} |  | [!BADGE Disponible]{type=Positive} | [Disponible en tant qu’extension](/help/implementing/universal-editor/extending.md) |
| Insérer un nouveau bloc | [!BADGE Disponible]{type=Positive} |  | [!BADGE Disponible]{type=Positive} |  |
| Réorganiser le bloc | [!BADGE Disponible]{type=Positive} | Possible avec un glisser-déposer contextuel, mais pas dans le panneau latéral « arborescence ». | [!BADGE Disponible]{type=Positive} | Possible par glisser-déposer dans le panneau latéral « arborescence », mais pas encore en contexte (prévu). |
| Couper/Copier-coller le bloc | [!BADGE Disponible]{type=Positive} |  | [!BADGE Non disponible]{type=Negative} | Prévu |
| Appliquer des styles | [!BADGE Disponible]{type=Positive} | Des styles peuvent être appliqués aux composants à l’aide [du système de style](/help/sites-cloud/authoring/page-editor/style-system.md). | [!BADGE Disponible]{type=Positive} | Des styles peuvent être appliqués à l’aide des propriétés de composant (ou de fragment de contenu) classiques. Le même sélecteur de style n’est pas disponible dans l’éditeur universel, mais il est possible d’obtenir une expérience d’utilisation très similaire à l’aide d’un widget à sélections multiples. |
| Appliquer une mise en page | [!BADGE Disponible]{type=Positive} | Les sites doit implémenter la [grille réactive AEM](/help/implementing/developing/introduction/responsive-design.md) pour permettre aux créateurs et créatrices de redimensionner les composants sur trois points d’arrêt prédéfinis. | [!BADGE Disponible]{type=Positive} | Des mises en page peuvent être appliquées à l’aide des propriétés de composant (ou de fragment de contenu) classiques. La grille réactive n’est toutefois pas prise en charge. |
| Annuler-rétablir | [!BADGE Disponible]{type=Positive} |  | [!BADGE Disponible]{type=Positive} |  |
| Publier (également en prévisualisation) | [!BADGE Disponible]{type=Positive} |  | [!BADGE Disponible]{type=Positive} |  |
| [Démarrer le workflow](/help/sites-cloud/authoring/workflows/overview.md) | [!BADGE Disponible]{type=Positive} |  | [!BADGE Disponible]{type=Positive} | Disponible en tant qu’extension |
| Commentaires | [!BADGE Disponible]{type=Positive} | Utilisation d’[annotations](/help/sites-cloud/authoring/page-editor/annotations.md) | [!BADGE Non disponible]{type=Negative} | Prévu |
| Intégration Workfront | [!BADGE Non disponible]{type=Negative} |  | [!BADGE Disponible]{type=Positive} | Disponible en tant qu’extension |
| [MSM et Lancements](/help/sites-cloud/administering/msm-and-translation.md) | [!BADGE Disponible]{type=Positive} |  | [!BADGE Disponible]{type=Positive} | Disponible pour les pages en tant qu’extension |
| Expérimentation et personnalisation | [!BADGE Disponible]{type=Positive} | Utilisation du [mode cible](/help/sites-cloud/authoring/personalization/targeted-content.md) | [!BADGE Disponible]{type=Positive} | Disponible en tant qu’extension pour Edge Delivery Services |
| Arborescence de contenu | [!BADGE Disponible]{type=Positive} |  | [!BADGE Disponible]{type=Positive} | Permet également de réorganiser dans l’arborescence. |
| Simulation d’appareil | [!BADGE Disponible]{type=Positive} | [Les appareils configurés peuvent être simulés](/help/sites-cloud/administering/responsive-layout.md) mais l’utilisateur ou l’utilisatrice ne peut pas saisir manuellement d’autres dimensions d’écran à simuler. | [!BADGE Disponible]{type=Positive} | [Il est possible de saisir manuellement toutes les dimensions d’écran à simuler](/help/sites-cloud/authoring/universal-editor/navigation.md#emulator) mais les points d’arrêt par défaut ne peuvent pas être configurés. |
| [Verrouillage de page](/help/sites-cloud/authoring/sites-console/managing-pages.md) | [!BADGE Disponible]{type=Positive} |  | [!BADGE Disponible]{type=Positive} | Respecte le statut de verrouillage défini dans la console Sites avec l’extension disponible pour verrouiller/déverrouiller des pages à partir de l’éditeur. |
| [Propriétés de la page](/help/sites-cloud/authoring/sites-console/edit-page-properties.md) | [!BADGE Disponible]{type=Positive} |  | [!BADGE Disponible]{type=Positive} | Disponible auprès de l’administrateur ou l’administratrice du site, avec l’extension pour accéder également aux propriétés des pages à partir de l’éditeur. |
| Propriétés des champs multiples | [!BADGE Disponible]{type=Positive} |  | [!BADGE Non disponible]{type=Negative} | Prévu |
| [DAM à distance](/help/assets/dynamic-media-open-apis-overview.md) | [!BADGE Disponible]{type=Positive} |  | [!BADGE Disponible]{type=Positive} |  |
| [Contrôle de version de la page](/help/sites-cloud/authoring/sites-console/page-versions.md) | [!BADGE Disponible]{type=Positive} |  | [!BADGE Disponible]{type=Positive} |  |
| [Distorsion du temps](/help/sites-cloud/authoring/sites-console/page-versions.md#timewarp) et [Affichage des différences](/help/sites-cloud/authoring/sites-console/page-diff.md) | [!BADGE Disponible]{type=Positive} |  | [!BADGE Non disponible]{type=Negative} | Prévu |
| Afficher en administrateur ou administratrice | [!BADGE Disponible]{type=Positive} |  | [!BADGE Disponible]{type=Positive} | Disponible en tant qu’extension pour les pages |
| Afficher le statut de la page | [!BADGE Disponible]{type=Positive} |  | [!BADGE Non disponible]{type=Negative} | Disponible dans la console Sites |
| Extensibilité | [!BADGE Disponible]{type=Positive} | En tant que recouvrements AEM | [!BADGE Disponible]{type=Positive} | En tant que points d’extension clairement définis utilisant App Builder et très peu de connaissances spécifiques à AEM. |

## Adoption de l’éditeur universel {#adopt-ue}

L’éditeur universel offre de nombreux avantages, ce qui en fait une excellente solution pour les nouveaux projets.

* **Modification visuelle :** comme pour l’éditeur de page, les créateurs et créatrices peuvent modifier le contenu directement dans l’aperçu et voir instantanément comment leurs modifications affectent l’expérience du visiteur ou de la visiteuse.
* **Pérennisation :** feuille de route d’AEM donne la priorité à l’éditeur universel en tant qu’éditeur visuel. Son adoption garantit l’accès aux dernières innovations et améliorations.
* **Intégration plus simple :** aucun SDK spécifique à AEM n’est nécessaire pour utiliser l’éditeur universel, ce qui réduit le verrouillage de tech stack.
* **Utilisez votre propre application :** l’éditeur universel prend en charge n’importe quelle structure ou architecture web, ce qui permet l’adoption sans nécessiter de refactorisation complexe.
* **Extensibilité :** l’éditeur universel bénéficie d’un [cadre d’extension](/help/implementing/universal-editor/extending.md) robuste qui comprend des intégrations à GenAI, Workfront, etc.

### Migration vers l’éditeur universel {#migrate-ue}

Il n’existe pas de chemin de migration direct de l’éditeur de page vers l’éditeur universel. Cela est dû à des différences fondamentales entre les deux technologies.

* L’éditeur universel ne réintroduit pas de fonctionnalités telles que l’éditeur de modèles, le système de style ou la grille réactive.
   * Ces cas d’utilisation peuvent désormais être gérés plus efficacement avec un CSS front-end et JavaScript allégés dans les projets Edge Delivery Services ou découplés.
* Comme l’éditeur universel est un éditeur en tant que service, il ne peut pas permettre aux personnes en charge de l’implémentation d’injecter des éléments CSS ou JS dans les boîtes de dialogue des composants.
   * Cela empêche la conversion automatique des boîtes de dialogue des composants à partir de l’éditeur de page.
   * Cela affecte de nombreux domaines des boîtes de dialogue, tels que les widgets personnalisés, la validation des champs, l’affichage/le masquage des règles et les personnalisations basées sur des modèles.
      * Bien que de telles fonctionnalités soient toujours possibles, l’éditeur universel les résout par le biais de la configuration, au lieu d’un JavaScript personnalisé déployé dans les boîtes de dialogue.

Bien que l’éditeur universel puisse techniquement activer la modification des pages pour les projets AEM traditionnels (par exemple, créés avec les composants principaux), ces sites reposent généralement sur plusieurs fonctionnalités spécifiques à l’éditeur de page, telles que le système de style, la grille réactive, les modèles modifiables et le code JavaScript personnalisé dans les boîtes de dialogue.

Dans la mesure où l’éditeur universel suit une approche plus rationalisée et moderne qui ne prend pas en charge ces fonctionnalités héritées, la migration de ces sites nécessiterait une refactorisation importante. Pour cette raison, **la migration des sites de l’éditeur de page vers l’éditeur universel n’est recommandée que pour les projets qui passent à Edge Delivery Services.**
