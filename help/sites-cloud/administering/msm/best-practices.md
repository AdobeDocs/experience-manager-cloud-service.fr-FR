---
title: Meilleures pratiques MSM
description: Découvrez les bonnes pratiques compilées par les équipes d’ingénierie et de conseil d’Adobe pour vous aider à prendre en main AEM Multi Site Manager.
feature: Multi Site Manager
role: Administrator
exl-id: 61b8ded8-3b9e-423f-85a9-7280e1a721cc
source-git-commit: 184de9c1391ade3abbf2c6d73f09a324e6fa7e3e
workflow-type: tm+mt
source-wordcount: '1436'
ht-degree: 33%

---

# Meilleures pratiques MSM {#msm-best-practices}

## Général {#general}

MSM est une structure configurable pour automatiser le déploiement de contenu. Les mises en œuvre impliquent souvent des parties importantes d’un site web, ainsi que plusieurs organisations et zones géographiques. Il est donc vivement recommandé de planifier les mises en œuvre MSM avec autant d’attention que lorsque vous planifiez votre site web :

* Planifiez soigneusement **la structure et les flux de contenu** avant de commencer la mise en oeuvre.
* **Personnalisez autant que nécessaire, mais le moins possible.** Bien que MSM prenne en charge un haut degré de personnalisation (par exemple, des configurations de déploiement), la meilleure pratique pour les performances, la fiabilité et la mise à niveau de votre site web est généralement de minimiser la personnalisation.
* Créez rapidement un modèle de **gouvernance** et formez les utilisateurs en conséquence, afin d’assurer le succès. Une bonne pratique du point de vue de la gouvernance consiste à **minimiser l’autorité des producteurs de contenu locaux** pour allouer/connecter du contenu à d’autres utilisateurs locaux et à leurs Live Copies respectives. En effet, les héritages enchaînés non gouvernés peuvent considérablement accroître la complexité d’une structure MSM et compromettre ses performances et sa fiabilité.
* Une fois qu’un plan existe pour votre structure, vos flux de contenu, l’automatisation et la gouvernance, **prototypez et testez minutieusement votre système** avant de commencer une mise en oeuvre en direct.
* Gardez à l’esprit que les **conseillers en Adobe et les principaux intégrateurs système** ont une expérience approfondie de la planification et de la mise en oeuvre de l’automatisation du contenu avec MSM, afin qu’ils puissent vous aider à prendre en main votre projet MSM et tout au long de sa mise en oeuvre.

## Sources de Live Copy et configurations de plan directeur {#live-copy-sources-and-blueprint-configurations}

Gardez à l’esprit qu’une Live Copy peut être créée à l’aide des [pages ordinaires](creating-live-copies.md#creating-a-live-copy-of-a-page) ou d’une [configuration de plan directeur](creating-live-copies.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration). Les deux cas d’utilisation sont valides.

Les avantages de l’utilisation d’une configuration de plan directeur sont qu’elle :

* Autoriser l’auteur à utiliser l’option **Déploiement** sur un plan directeur afin de pousser explicitement les modifications apportées aux Live Copies qui héritent de ce plan directeur.
* Autoriser l’auteur à utiliser **Créer un site** afin de sélectionner facilement des langues et de configurer la structure de la Live Copy.
* Définissez une configuration de déploiement par défaut pour les Live Copies ayant une relation avec le plan directeur.

Si aucune configuration de plan directeur n’est référencée, les déploiements ne peuvent être lancés qu’à partir des Live Copies elles-mêmes, extrayant essentiellement le contenu de la source.

Lors de la création d’un site avec Live Copy, il est avantageux de créer des configurations de plan directeur pour assurer la disponibilité de l’ensemble de fonctionnalités MSM complet.

>[!NOTE]
>
> Notez que les groupes d’utilisateurs fermés dans l’onglet Autorisations ne peuvent pas être déployés sur des Live Copies à partir de plans directeurs. Veuillez en tenir compte lors de la configuration de Live Copy.

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

Notez que AEM propose deux méthodes principales pour créer des Live Copies :

* Lorsque [création d’une Live Copy](creating-live-copies.md#creating-a-live-copy-of-a-page) : cette méthode peut être considérée comme l’approche plus générique, qui vous permet de créer des Live Copies à partir de n’importe quelle page. La structure de contenu d’une Live Copy correspond exactement à la source.

* Lorsque [création d’un site](creating-live-copies.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration), il s’agit d’une approche plus spécialisée, principalement pour la création de sites web avec une structure multilingue.

Voici quelques points à prendre en compte lors de la création d’un site :

* Pour créer un site, vous avez besoin d’une [configuration de plan directeur](creating-live-copies.md#managing-blueprint-configurations).
* Pour permettre la sélection des chemins de langue à créer dans un nouveau site, les racines de langue correspondantes doivent exister dans le plan directeur (source).
* Une fois qu’un [nouveau site a été créé en tant que Live Copy](creating-live-copies.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration) (à l’aide de **Créer**, puis **Site**), les deux premiers niveaux de cette Live Copy sont *superficiels*. Les enfants de la page n’appartiennent pas à la relation activée, mais un déploiement descend toujours si une relation activée correspondant au déclencheur est détectée.

Il est utile d’éviter :

* Ajouter manuellement des langues dans le plan directeur (sous le premier niveau).
* L’ajout manuel de contenu directement sous la racine de langue, car cela n’entraîne pas l’acheminement automatique de ce nouveau contenu vers la Live Copy au moment du déploiement.

## MSM et sites web multilingues {#msm-and-multilingual-websites}

MSM peut aider à la création de sites web multilingues de deux façons :

Lors de la création de gabarits de langue, tenez compte des points suivants :

* Bien que MSM lui-même **ne fournisse pas la traduction de contenu**, il peut être intégré à des connecteurs de traduction tiers qui proposent ce service. Veuillez noter que :
   * MSM vous permet d’annuler l’héritage au niveau de la page et/ou du composant. Cela permet d’éviter le remplacement du contenu traduit (d’une Live Copy, avec du contenu non encore traduit d’un plan directeur) lors du déploiement suivant.
      * Certains connecteurs de traduction tiers automatisent cette gestion des héritages MSM.
      * Contactez votre prestataire de services de traduction pour plus d’informations.
      * Une autre méthode pour créer et traduire les gabarits de langue est d’utiliser des copies de langue conjointement à la structure d’intégration de traduction prête à l’emploi d’AEM.

Pour plus d’informations, voir [Traduction du contenu des sites multilingues](/help/sites-cloud/administering/translation/overview.md) et [Meilleures pratiques de traduction.](/help/sites-cloud/administering/translation/best-practices.md)

## Modifications de structure et déploiements {#structure-changes-and-rollouts}

Les modifications apportées à la structure de contenu dans un plan directeur/une arborescence source sont répercutées différemment dans une Live Copy. Cela dépend du type de modification :

* **** La création de pages dans un plan directeur entraîne la création de pages correspondantes dans des Live Copies après déploiement avec la configuration de déploiement standard.
* **** La suppression de pages dans un plan directeur entraîne la suppression des pages correspondantes des Live Copies après déploiement avec la configuration de déploiement standard.
* **** Le déplacement de pages dans un plan directeur  **** n’entraîne pas le déplacement des pages correspondantes dans des Live Copies après déploiement avec la configuration de déploiement standard :
   * La raison de ce comportement est que le déplacement d’une page comprend implicitement une suppression de page. Cela peut entraîner un comportement inattendu lors de la publication, car la suppression de pages sur l’auteur désactive automatiquement le contenu correspondant lors de la publication. Cela peut également avoir un effet supplémentaire sur les éléments associés, tels que les liens, les signets et autres.
      * L’héritage du contenu dans les pages Live Copy respectives est mis à jour pour refléter le nouvel emplacement de leurs sources dans le plan directeur.
      * Pour réaliser pleinement un déplacement de page d’un plan directeur vers des Live Copies, tenez compte des [bonnes pratiques de déplacement de page.](#page-move)

### Bonnes pratiques de déplacement de page {#page-move}

Lorsque vous envisagez de déplacer des pages dans une Live Copy, tenez compte des bonnes pratiques suivantes.

>[!NOTE]
>
>Les éléments suivants fonctionnent uniquement avec le déclencheur [Au déploiement](live-copy-sync-config.md#rollout-triggers).

1. Créez une configuration de déploiement personnalisée.
   * Cette nouvelle configuration doit inclure l’action `PageMoveAction`.
   * N’ajoutez pas d’autres actions à cette configuration.
1. Positionnez la nouvelle configuration.
   * Pour déployer entièrement le déplacement de page tout en supprimant les pages respectives à leur ancien emplacement dans la Live Copy :
      * Placez la configuration que vous venez de créer avant la configuration de déploiement standard. La configuration de déploiement standard s’occupe de la suppression des pages dans leurs anciens emplacements.
      * Pour déployer le déplacement de la page tout en conservant les pages respectives à leurs anciens emplacements dans les Live Copies (en dupliquant essentiellement le contenu) :
         * Placez la configuration que vous venez de créer après la configuration de déploiement standard. Cela permet de s’assurer qu’aucun contenu n’est supprimé dans la Live Copy ou désactivé de la publication.

## Personnalisation des déploiements {#customizing-rollouts}

Les configurations de déploiement MSM sont fortement personnalisables. Vous devez savoir que l’automatisation des déploiements peut avoir des conséquences importantes. Il est recommandé de planifier très soigneusement avant de vous engager dans les activités suivantes :

* Automatisation des déploiements tels que avec les déclencheurs [onModify](#onmodify)
* Personnalisation des [types/propriétés de noeud](#node-types-properties)
* Démarrage des workflows suivants
* Activation du contenu dans le cadre de déploiements

### onModify {#onmodify}

Lorsque vous utilisez le [déclencheur de déploiement](live-copy-sync-config.md#rollout-triggers) `onModify`, vous devez prendre en compte les points suivants :

* L’automatisation des déploiements avec des déclencheurs `onModify` peut avoir un impact négatif sur les performances de création, car ils déclenchent des déploiements après chaque modification de page.
* Le résultat du déploiement peut différer du résultat attendu pour les raisons suivantes :
   * Vous ne pouvez pas spécifier l’ordre des événements de modification résultants.
   * L’architecture basée sur les événements ne peut pas garantir la séquence des événements transmise au gestionnaire de déploiements.
* L’utilisation d’une telle configuration de déploiement est susceptible d’entraîner des conflits de validation en cas de mises à jour simultanées de la même ressource.

Par conséquent, il est recommandé d’utiliser uniquement les déclencheurs `onModify` si les avantages du lancement du déploiement automatique l’emportent sur les problèmes de performances potentiels.

### Types/propriétés de nœuds {#node-types-properties}

Outre la personnalisation des actions de déploiement, MSM vous permet de personnaliser les propriétés de noeud en cours de déploiement. La configuration [MSM OSGi vous permet d’exclure les types de noeuds](live-copy-sync-config.md#excluding-properties-and-node-types-from-synchronization) de la copie de la source vers la Live Copy.

## Informations supplémentaires {#further-information}

Reportez-vous aux articles suivants pour plus d’informations sur MSM et Live Copy.

* [Création et synchronisation de Live Copies](creating-live-copies.md)
* [Console Aperçu de la Live Copy](live-copy-overview.md)
* [Configuration de la synchronisation de Live Copies](live-copy-sync-config.md)
* [Conflits de déploiement de MSM](rollout-conflicts.md)
