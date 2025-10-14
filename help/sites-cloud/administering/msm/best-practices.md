---
title: Bonnes pratiques MSM
description: Découvrez les bonnes pratiques compilées par les équipes d’ingénierie et de recherche d’Adobe pour vous aider à maîtriser AEM Multi Site Manager (MSM).
feature: Multi Site Manager
role: Admin
exl-id: 61b8ded8-3b9e-423f-85a9-7280e1a721cc
solution: Experience Manager Sites
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '1414'
ht-degree: 93%

---

# Bonnes pratiques MSM {#msm-best-practices}

## Général {#general}

MSM est une structure configurable pour automatiser le déploiement de contenu. Les mises en œuvre impliquent souvent des parties importantes d’un site web, ainsi que plusieurs organisations et zones géographiques. Il est donc vivement recommandé de planifier les mises en œuvre MSM avec autant de soin que vous planifiez votre site web :

* **Planifiez la structure et les flux de contenu** avec soin avant de commencer la mise en œuvre.
* **Personnalisez autant que nécessaire, mais le moins possible.** Bien que MSM prenne en charge un haut degré de personnalisation (par exemple, les configurations de déploiement), la meilleure pratique pour favoriser les performances, la fiabilité et l’amélioration de votre site web est généralement de minimiser la personnalisation.
* Établissez un modèle de **gouvernance** dès le début et formez les utilisateurs en conséquence, afin de garantir la réussite. Du point de vue de la gouvernance, une bonne pratique consiste à **minimiser l’autorité des producteurs du contenu** sur l’allocation/l’association du contenu à d’autres utilisateurs locaux et à leurs Live Copies respectives. Cela est dû au fait que les héritages par enchaînement non gouvernés peuvent considérablement augmenter la complexité d’une structure MSM et dégrader ses performances et sa stabilité.
* Une fois qu’un plan existe pour la structure, les flux de contenu, l’automatisation et la gouvernance, **prototypez et testez intégralement le système**, avant de commencer la mise en œuvre en direct.
* Gardez à l’esprit que les **intégrateurs système de premier plan et les consultants Adobe** possèdent une expérience approfondie dans la planification et la mise en œuvre de l’automatisation de contenu avec MSM. Ils peuvent donc vous aider lors du lancement de votre projet MSM et tout au long de sa mise en œuvre.

## Configurations de plan directeur et de sources Live Copy {#live-copy-sources-and-blueprint-configurations}

N’oubliez pas qu’une Live Copy peut être créée avec des [pages ordinaires](creating-live-copies.md#creating-a-live-copy-of-a-page) ou une [configuration de plan directeur](creating-live-copies.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration). Les deux cas d’utilisation sont valides.

Les avantages supplémentaires liés à l’utilisation d’une configuration de plan directeur sont les suivants :

* ermet à l’auteur ou à l’autrice d’utiliser l’option **Déploiement** sur un plan directeur afin de pousser explicitement les modifications vers les Live Copies qui héritent de ce plan directeur ;
* permet à l’auteur ou à l’autrice d’utiliser **Créer un site** afin de pouvoir sélectionner facilement les langues et configurer la structure de la Live Copy ;
* définit une configuration de déploiement par défaut pour les Live Copies partageant une relation avec le plan directeur.

Dans le cas où aucune configuration de plan directeur n’est référencée, les déploiements peuvent uniquement être lancés à partir des Live Copies elles-mêmes, en extrayant essentiellement le contenu de la source.

Lors de la création d’un site avec Live Copy, il est avantageux de créer des configurations de plan directeur pour garantir la disponibilité de l’ensemble complet des fonctionnalités MSM.

>[!NOTE]
>
>Les groupes d’utilisateurs et d’utilisatrices fermés dans l’onglet Autorisations ne peuvent pas être déployés dans des Live Copies à partir de plans directeurs. Veuillez en tenir compte lors de la configuration de la Live Copy.

## Composants et synchronisation de conteneur {#components-and-container-synchronization}

En général, la règle de déploiement dans MSM concernant la synchronisation des composants est la suivante :

* Les composants sont déployés en synchronisant toutes les ressources contenues dans le plan directeur.
* Les conteneurs ne synchronisent que la ressource active.

Cela signifie que les composants sont traités comme un agrégat et, dans un déploiement, le composant lui-même et tous ses enfants sont remplacés par ceux des plans directeurs. Cela signifie que si une ressource est ajoutée localement à un tel composant, elle est perdue par rapport au contenu du plan directeur lors du déploiement.

Pour prendre en charge l’imbrication des composants de façon à ce que les composants ajoutés localement soient conservés dans un déploiement, le composant doit être déclaré en tant que conteneur.

>[!NOTE]
>
>Ajoutez la propriété `cq:isContainer` au composant pour le désigner en tant que conteneur.

## Créer un site {#create-site}

Notez qu’AEM propose deux méthodes principales pour créer des Live Copies :

* Lors de la [création d’une Live Copy](creating-live-copies.md#creating-a-live-copy-of-a-page) – Cela peut être considéré comme une approche plus générique, qui vous permet de créer des Live Copies de n’importe quelle page. La structure de contenu d’une Live Copy correspond exactement à la source.

* Lors de la [création d’un site](creating-live-copies.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration) – Il s’agit d’une approche plus spécialisée, principalement pour créer des sites web avec une structure multilingue.

Voici quelques points à garder à l’esprit lors de la création d’un site :

* Pour créer un site, vous avez besoin d’une [configuration de plan directeur](creating-live-copies.md#managing-blueprint-configurations).
* Pour permettre la sélection des chemins de langue afin de créer un site, les racines de langue correspondantes doivent exister dans le plan directeur (source).
* Une fois qu’un [site a été créé comme une Live Copy](creating-live-copies.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration) (en sélectionnant **Créer**, puis **Site**), les deux premiers niveaux de cette Live Copy sont *peu profonds*. Les enfants de la page n’appartiennent pas à la relation activée, mais un déploiement descend toujours si une relation activée correspondant au déclencheur est détectée.

Nous vous conseillons d’éviter :

* d’ajouter manuellement des langues dans le plan directeur (sous le premier niveau) ;
* d’ajouter manuellement du contenu directement sous la racine de la langue n’entraîne pas l’envoi automatique de ce nouveau contenu à la Live Copy au moment du déploiement.

## MSM et sites web multilingues {#msm-and-multilingual-websites}

MSM peut aider à la création de sites web multilingues de deux façons :

Lors de la création de gabarits de langue, gardez à l’esprit les points suivants :

* Bien que MSM lui-même **ne fournisse pas la traduction de contenu**, il peut être intégré à des connecteurs de traduction tiers qui proposent ce service. Notez les points suivants :
   * MSM vous permet d’annuler l’héritage au niveau de la page et/ou du composant. Cela évite de remplacer le contenu traduit (dans une Live Copy, avec le contenu pas encore traduit d’un plan directeur) lors du déploiement suivant.
      * Certains connecteurs de traduction tiers automatisent cette gestion des héritages MSM.
      * Contactez votre prestataire de services de traduction pour plus d’informations.
      * Une autre méthode pour créer et traduire les gabarits de langue consiste à utiliser des copies de langue conjointement à la structure d’intégration de traduction prête à l’emploi d’AEM.

Pour plus d’informations, consultez les sections [Traduction du contenu des sites multilingues](/help/sites-cloud/administering/translation/overview.md) et [Bonnes pratiques de traduction](/help/sites-cloud/administering/translation/best-practices.md).

## Modifications et déploiements de structures {#structure-changes-and-rollouts}

Les modifications apportées à la structure du contenu dans un plan directeur/une arborescence source sont répercutées différemment dans une Live Copy. Cela dépend du type de modification :

* La **création** de pages dans un plan directeur entraîne la création des pages correspondantes dans des Live Copies après déploiement avec la configuration de déploiement standard.
* La **suppression** de pages dans un plan directeur entraîne la suppression des pages correspondantes dans les Live Copies après déploiement avec la configuration de déploiement standard.
* Le **déplacement** de pages dans un plan directeur **n’entraîne pas** le déplacement des pages correspondantes dans des Live Copies après déploiement avec la configuration de déploiement standard :
   * La raison de ce comportement est que le déplacement d’une page comprend implicitement une suppression de page. Cela peut provoquer un comportement inattendu lors de la publication, la suppression des pages sur l’instance de création désactivant automatiquement le contenu correspondant sur l’instance de publication. Cela peut également avoir un effet de bord sur les éléments associés, comme les liens, les signets, etc.
      * L’héritage de contenu dans les pages de Live Copies respectives est mis à jour pour refléter le nouvel emplacement de leurs sources dans le plan directeur.
      * Pour réaliser un déplacement de page d’un plan directeur vers des Live Copies, prenez en compte les bonnes pratiques [déplacement de page].(#page-move)

### Bonnes pratiques de déplacement de page {#page-move}

Lorsque vous envisagez de déplacer des pages dans une Live Copy, tenez compte des bonnes pratiques suivantes.

>[!NOTE]
>
>Ces actions ne fonctionnent uniquement avec le [déclencheur En cas de déploiement](live-copy-sync-config.md#rollout-triggers).

1. Créez une configuration de déploiement personnalisée.
   * Cette nouvelle configuration doit inclure l’action `PageMoveAction`.
   * N’ajoutez pas d’autres actions à cette configuration.
1. Placez la nouvelle configuration.
   * Pour déployer entièrement le déplacement de page tout en supprimant les pages respectives de leur ancien emplacement dans la Live Copy :
      * Placez la configuration créée avant la configuration de déploiement standard. La configuration de déploiement standard se charge de supprimer les pages de leurs anciens emplacements.
      * Pour déployer le déplacement de page tout en conservant les pages respectives à leurs anciens emplacements dans les Live Copies (ce qui revient essentiellement à dupliquer le contenu) :
         * Placez la configuration créée après la configuration de déploiement standard. Cela permet de s’assurer qu’aucun contenu n’est supprimé dans la Live Copy ni désactivé sur l’instance de publication.

## Personnalisation des déploiements {#customizing-rollouts}

Les configurations de déploiement MSM sont fortement personnalisables. L’automatisation des déploiements peut avoir d’importantes conséquences. En règle générale, il est recommandé de vous préparer soigneusement avant de vous engager dans les activités suivantes :

* Automatisation des déploiements, par exemple avec des [déclencheurs onModify](#onmodify)
* Personnalisation des [propriétés ou des types de nœuds](#node-types-properties)
* Démarrage des workflows suivants
* Activation de contenu dans le cadre de déploiements

### onModify {#onmodify}

Lorsque vous utilisez le [déclencheur de déploiement](live-copy-sync-config.md#rollout-triggers) `onModify`, vous devez prendre en compte les points suivants :

* L’automatisation des déploiements avec des déclencheurs `onModify` peut avoir un impact négatif sur les performances de création, car ils déclenchent des déploiements après chaque modification de page.
* Le résultat du déploiement peut différer de celui attendu, car :
   * Vous ne pouvez pas spécifier l’ordre des événements de modification résultants.
   * L’architecture basée sur des événements ne peut pas garantir la séquence des événements transmis au Gestionnaire de déploiement.
* L’utilisation d’une telle configuration de déploiement peut entraîner des conflits de validation si des mises à jour simultanées de la même ressource se produisent.

Par conséquent, il est recommandé d’utiliser uniquement les déclencheurs `onModify` si les avantages du lancement de déploiement automatique l’emportent sur les problèmes de performance potentiels.

### Types/propriétés de nœuds {#node-types-properties}

En plus de personnaliser les actions de déploiement, MSM vous permet de personnaliser les propriétés des nœuds qui sont déployés. La configuration OSGi [MSM vous permet d’exclure des types &#x200B;](live-copy-sync-config.md#excluding-properties-and-node-types-from-synchronization) nœuds de la copie de la source vers la Live Copy.

## Informations supplémentaires {#further-information}

Reportez-vous aux articles suivants pour plus d’informations sur MSM et la Live Copy.

* [Création et synchronisation de Live Copies](creating-live-copies.md)
* [Console Aperçu de Live Copy](live-copy-overview.md)
* [Configuration de la synchronisation des Live Copies](live-copy-sync-config.md)
* [Conflits de déploiement de MSM](rollout-conflicts.md)
