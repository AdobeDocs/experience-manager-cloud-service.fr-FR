---
title: Meilleures pratiques MSM
description: Découvrez les meilleures pratiques compilées par les équipes d'ingénierie et de conseil en Adobe pour vous aider à maîtriser les opérations liées à l'AEM Gestionnaire de sites multiples.
feature: Multi Site Manager
role: Administrator
translation-type: tm+mt
source-git-commit: 0f2b7176b44bb79bdcd1cecf6debf05bd652a1a1
workflow-type: tm+mt
source-wordcount: '1413'
ht-degree: 33%

---


# Meilleures pratiques MSM {#msm-best-practices}

## Général {#general}

MSM est une structure configurable pour automatiser le déploiement de contenu. Les mises en œuvre impliquent souvent des parties importantes d’un site web, ainsi que plusieurs organisations et zones géographiques. Il est donc vivement recommandé de planifier les mises en œuvre MSM avec autant d’attention que lorsque vous planifiez votre site web :

* Soigneusement **planifier la structure et les flux de contenu** avant de commencer la mise en oeuvre.
* **Personnalisez autant que nécessaire, mais le moins possible.** Bien que MSM prenne en charge un haut degré de personnalisation (par exemple, les configurations de déploiement), la meilleure pratique pour les performances, la fiabilité et la mise à niveau de votre site Web consiste généralement à minimiser la personnalisation.
* Établir rapidement un modèle de **gouvernance** et former les utilisateurs en conséquence afin d&#39;assurer la réussite. Une bonne pratique d&#39;un point de vue de gouvernance consiste à **minimiser l&#39;autorité dont disposent les producteurs de contenu locaux** pour allouer/connecter du contenu à d&#39;autres utilisateurs locaux et à leurs Live Copies respectives. En effet, les héritages enchaînés et non gouvernés peuvent considérablement accroître la complexité d&#39;une structure de gestion multivariée et compromettre ses performances et sa fiabilité.
* Une fois qu&#39;un plan existe pour votre structure, vos flux de contenu, l&#39;automatisation et la gouvernance, **prototype et testez minutieusement votre système** avant de commencer une mise en oeuvre.
* Gardez à l&#39;esprit que **Adobe Consulting et les principaux intégrateurs système** ont une expérience approfondie de la planification et de l&#39;implémentation de l&#39;automatisation du contenu avec MSM, afin qu&#39;ils puissent vous aider à la fois à démarrer votre projet MSM et tout au long de sa mise en oeuvre.

## Sources de Live Copy et configurations de plan directeur {#live-copy-sources-and-blueprint-configurations}

Gardez à l’esprit qu’une Live Copy peut être créée à l’aide de [pages régulières](creating-live-copies.md#creating-a-live-copy-of-a-page) ou d’une [configuration de plan directeur](creating-live-copies.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration). Les deux cas d’utilisation sont valides.

Les avantages de l’utilisation d’une configuration de plan directeur sont qu’elle :

* Permettre à l&#39;auteur d&#39;utiliser l&#39;option **Déploiement** sur un schéma afin d&#39;envoyer explicitement les modifications aux Live Copies qui héritent de ce schéma.
* Permet à l’auteur d’utiliser **Créer un site** afin de sélectionner facilement les langues et de configurer la structure de la Live Copy.
* Définissez une configuration de déploiement par défaut pour les Live Copies qui ont une relation avec le plan.

Dans le cas où une configuration de plan directeur n&#39;est pas référencée, les déploiements ne peuvent être lancés qu&#39;à partir des Live Copies elles-mêmes, extrayant essentiellement le contenu de la source.

Lors de la création d’un site avec Live Copy, il est avantageux de créer des configurations de plan afin de garantir la disponibilité de l’ensemble complet des fonctionnalités MSM.

## Composants et synchronisation de conteneur {#components-and-container-synchronization}

En général, la règle de déploiement dans MSM concernant la synchronisation des composants est la suivante :

* Les composants sont déployés en synchronisant toutes les ressources contenues dans le plan directeur.
* Les conteneurs synchronisent uniquement la ressource actuelle.

Cela signifie que les composants sont traités comme un agrégat et, dans un déploiement, le composant lui-même et tous ses enfants sont remplacés par ceux des plans directeurs. Cela signifie que si une ressource est ajoutée à un composant en local, elle sera perdue au profit du contenu du plan directeur lors du déploiement.

Pour prendre en charge l’imbrication des composants de façon à ce que les composants ajoutés localement soient conservés dans un déploiement, le composant doit être déclaré en tant que conteneur.

>[!NOTE]
>
>Ajoutez la propriété `cq:isContainer` au composant pour le désigner en tant que conteneur.

## Créer un site {#create-site}

Notez que AEM utilise deux méthodes principales pour créer des Live Copies :

* Lorsque [création d’une Live Copy](creating-live-copies.md#creating-a-live-copy-of-a-page), cette méthode peut être considérée comme l’approche la plus générique, vous permettant de créer des Live Copies à partir de n’importe quelle page. La structure de contenu d’une Live Copy correspond exactement à la source.

* Lorsque [créer un site](creating-live-copies.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration) - Il s&#39;agit d&#39;une approche plus spécialisée, principalement pour la création de sites Web avec une structure multilingue.

Voici quelques points à prendre en compte lors de la création d’un site :

* Pour créer un nouveau site, vous devez disposer d&#39;une configuration de plan directeur [](creating-live-copies.md#managing-blueprint-configurations).
* Pour permettre la sélection des chemins de langue à créer dans un nouveau site, les racines de langue correspondantes doivent exister dans le plan directeur (source).
* Une fois qu&#39;un [nouveau site a été créé en tant que Live Copy](creating-live-copies.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration) (en utilisant **Créer**, puis **Site**), les deux premiers niveaux de cette Live Copy sont *peu profonds*. Les enfants de la page n’appartiennent pas à la relation activée, mais un déploiement descend toujours si une relation activée correspondant au déclencheur est détectée.

A éviter :

* Ajout manuel de langues dans le plan directeur (sous le premier niveau).
* L’ajout manuel de contenu directement sous la racine de la langue n’entraîne pas l’envoi automatique de ce nouveau contenu à la Live Copy au moment du déploiement.

## MSM et sites web multilingues {#msm-and-multilingual-websites}

MSM peut aider à la création de sites web multilingues de deux façons :

Lors de la création de gabarits de langue, gardez à l’esprit les points suivants :

* Bien que MSM lui-même **ne fournisse pas la traduction de contenu**, il peut être intégré à des connecteurs de traduction tiers qui proposent ce service. Veuillez noter que :
   * MSM vous permet d&#39;annuler l&#39;héritage au niveau de la page et/ou du composant. Cela permet d’éviter d’écraser le contenu traduit (à partir d’une Live Copy, avec le contenu non encore traduit d’un schéma) lors du prochain déploiement.
      * Certains connecteurs de traduction tiers automatisent cette gestion des héritages MSM.
      * Contactez votre prestataire de services de traduction pour plus d’informations.
      * Une autre méthode pour créer et traduire les gabarits de langue est d’utiliser des copies de langue conjointement à la structure d’intégration de traduction prête à l’emploi d’AEM.

Pour plus d’informations, voir [Traduction du contenu des sites multilingues](/help/sites-cloud/administering/translation/overview.md) et [Meilleures pratiques de traduction.](/help/sites-cloud/administering/translation/best-practices.md)

## Modifications de structure et déploiements {#structure-changes-and-rollouts}

Les modifications apportées à la structure de contenu dans un plan directeur/une arborescence source sont répercutées différemment dans une Live Copy. Cela dépend du type de modification :

* **La** création de pages dans un plan directeur entraîne la création de pages correspondantes dans des Live Copies après le déploiement avec la configuration de déploiement standard.
* **La** suppression de pages dans un plan directeur entraîne la suppression des pages correspondantes des Live Copies après le déploiement avec une configuration de déploiement standard.
* **Le** déplacement de pages dans un plan directeur  **** n&#39;entraîne pas le déplacement des pages correspondantes dans les Live Copies après le déploiement avec la configuration de déploiement standard :
   * La raison de ce comportement est que le déplacement d’une page comprend implicitement une suppression de page. Cela peut entraîner un comportement inattendu lors de la publication, car la suppression de pages sur l’auteur désactive automatiquement le contenu correspondant lors de la publication. Cela peut également avoir un effet supplémentaire sur les éléments connexes, tels que les liens, les signets et d’autres.
      * L&#39;héritage de contenu dans les pages Live Copy respectives est mis à jour pour refléter le nouvel emplacement de leurs sources dans le plan directeur.
      * Pour réaliser pleinement le déplacement d&#39;une page d&#39;un modèle vers des Live Copies, tenez compte des [bonnes pratiques de déplacement de page.](#page-move)

### Meilleures pratiques de déplacement de page {#page-move}

Lorsque vous envisagez de déplacer des pages dans une Live Copy, tenez compte des bonnes pratiques suivantes.

>[!NOTE]
>
>Les éléments suivants fonctionnent uniquement avec le déclencheur [Au déploiement](live-copy-sync-config.md#rollout-triggers).

1. Créez une configuration de déploiement personnalisée.
   * Cette nouvelle configuration doit inclure l&#39;action `PageMoveAction`.
   * N’ajoutez pas d’autres actions à cette configuration.
1. Positionnez la nouvelle configuration.
   * Pour déployer complètement le déplacement de la page tout en supprimant les pages respectives à leur ancien emplacement dans la Live Copy :
      * Placez la configuration que vous venez de créer avant la configuration de déploiement standard. La configuration de déploiement standard prend en charge la suppression des pages dans leurs anciens emplacements.
      * Pour déployer le déplacement de la page tout en conservant les pages respectives à leur ancien emplacement dans les Live Copies (essentiellement en dupliquant le contenu) :
         * Placez la configuration que vous venez de créer après la configuration de déploiement standard. Ainsi, aucun contenu n’est supprimé dans Live Copy ou désactivé de la publication.

## Personnalisation des déploiements {#customizing-rollouts}

Les configurations de déploiement MSM sont fortement personnalisables. Vous devez savoir que l’automatisation des déploiements peut avoir des conséquences importantes. En règle générale, il est recommandé de planifier soigneusement avant de vous engager dans les activités suivantes :

* Automatisation des déploiements, par exemple avec des déclencheurs [onModify](#onmodify)
* Personnalisation des [types de noeud/propriétés](#node-types-properties)
* Démarrage des workflows suivants
* Activation de contenu dans le cadre de déploiements

### onModify {#onmodify}

Lorsque vous utilisez le [déclencheur de déploiement](live-copy-sync-config.md#rollout-triggers) `onModify`, vous devez prendre en compte les points suivants :

* L&#39;automatisation des déploiements avec des déclencheurs `onModify` peut avoir un impact négatif sur les performances de création, car elles déclenchent des déploiements après chaque modification de page.
* Le résultat du déploiement peut différer du résultat attendu pour les raisons suivantes :
   * Vous ne pouvez pas spécifier l’ordre des événements de modification résultants.
   * L’architecture basée sur les événements ne peut pas garantir la séquence des événements transmise au gestionnaire de déploiements.
* L’utilisation d’une telle configuration de déploiement est susceptible d’entraîner des conflits de validation en cas de mises à jour simultanées de la même ressource.

Par conséquent, il est recommandé d’utiliser uniquement les déclencheurs `onModify` si les avantages du lancement automatique du déploiement l’emportent sur les problèmes de performances potentiels.

### Types/propriétés de nœuds {#node-types-properties}

Outre la personnalisation des actions de déploiement, MSM vous permet également de personnaliser les propriétés de noeud en cours de déploiement. La configuration [MSM OSGi vous permet d’exclure les types de noeud](live-copy-sync-config.md#excluding-properties-and-node-types-from-synchronization) de la copie de la source vers Live Copy.

## Informations supplémentaires {#further-information}

Reportez-vous aux articles suivants pour plus d’informations sur MSM et Live Copy.

* [Création et synchronisation de Live Copies](creating-live-copies.md)
* [Console Aperçu de la Live Copy](live-copy-overview.md)
* [Configuration de la synchronisation des Live Copies](live-copy-sync-config.md)
* [Conflits de déploiement dans MSM](rollout-conflicts.md)
