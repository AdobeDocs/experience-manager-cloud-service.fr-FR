---
title: Qu’est-ce qu’un CMS Headless ?
description: Découvrez les CMS découplés. Comment fonctionnent-ils ? Quelles sont les alternatives et les différences ? Pourquoi souhaiteriez-vous utiliser un CMS découplé ?
exl-id: 53f24f69-ad49-4b8e-9a91-36cd64c1f2b9
source-git-commit: 5663b1224dddcb2db9e0ca139bb8cf6b43787fab
workflow-type: ht
source-wordcount: '742'
ht-degree: 100%

---

# Qu’est-ce qu’un CMS Headless ? {#what-is-a-headless-cms}

La gestion de contenu découplé est une évolution clé de la conception Web actuelle qui découple les applications frontales côté client du système de gestion de contenu principal. Un CMS découplé est donc responsable des services de gestion de contenu (principal), ainsi que des mécanismes permettant aux applications (frontales) d’accéder à ce contenu.

Mais que signifie vraiment ce terme ? Nous vous proposons ici une introduction (très rapide) aux concepts clés.

## Qu’est-ce qu’un système de gestion de contenu (CMS) ? {#content-management-system}

Commençons par les principes de base : qu’est-ce qu’un système de gestion de contenu ?

Un système de gestion de contenu (CMS) stocke, gère et diffuse le contenu utilisé pour fournir vos expériences en ligne.

## CMS traditionnel {#traditional-cms}

Traditionnellement, un CMS inclut à la fois la fonctionnalité principale de stockage et de diffusion de contenu, ainsi que la technologie frontale utilisée pour générer le balisage d’une expérience que votre navigateur affichera (couche de présentation).

Très puissant, vous permettant de contrôler entièrement le contenu et la mise en forme, mais sans la flexibilité nécessaire dans l’environnement en rapide évolution d’aujourd&#39;hui. par exemple, pour jouer le rôle d’interface avec des applications externes.

## CMS découplé {#headless-cms}

Avec un système de gestion de contenu découplé, le serveur principal et frontal sont désormais découplés.

La partie découplée est le serveur principal du contenu, car un système de gestion de contenu (CMS) découplé est un système de gestion de contenu back-end uniquement créé dès le départ comme un référentiel de contenu qui rend ce dernier accessible via une API pour l’afficher sur n’importe quel appareil.

Le serveur frontal, qui est développé et géré indépendamment, récupère du contenu du serveur principal découplé à l’aide d’une API de diffusion de contenu, généralement au format JSON. Par exemple, il peut s’agir d’une application React ou Angular (application d’une seule page (SPA)).

Un serveur principal CMS découplé nécessite généralement que le contenu soit structuré en fonction d’un modèle ou d’un schéma. Cela facilite la tâche aux applications clientes qui demandent du contenu approprié pour le rendu d’une expérience. Certains CMS peuvent présenter du contenu structuré et non structuré au format JSON.

Une caractéristique clé de cette topologie est que le contenu diffusé par le CMS découplé au format JSON est du contenu pur, sans informations de conception ou de mise en page. Dans une implémentation CMS découplé, toute mise en forme et mise en page sont conservées par l’application frontale découplée.

L’un des principaux avantages d’une topologie CMS découplée réside dans la possibilité de réutiliser du contenu sur plusieurs canaux, ce qui permet d’utiliser différentes implémentations frontales côté client. Cela peut rendre le processus de développement frontal plus efficace. Mais cela signifie également que le processus de développement de l’expérience frontale peut devenir très codé et centré sur l’informatique qui en est essentiellement propriétaire.

## API de diffusion de contenu {#content-delivery-apis}

Un CMS découplé peut fournir un ou plusieurs moyens de présentation du contenu aux applications côté client. Les API HTTP REST les plus courantes, les API GraphQL ou les deux.

Bien qu’une API REST puisse sembler souvent un moyen plus facile de faire une requête de contenu (par exemple, en fournissant du code JSON pour tout contenu correspondant à un critère), elle fournit généralement trop de contenu à une application cliente. Le client peut alors avoir besoin d’analyser et de filtrer le contenu réellement nécessaire au rendu.

GraphQL est en revanche un mécanisme plus ciblé permettant aux applications clientes de rechercher exactement le contenu nécessaire pour effectuer le rendu d’une expérience.

## CMS de piles pleines {#fullstack-cms}

Un CMS avec pile pleine représente généralement la topologie traditionnelle pour la gestion et la diffusion de contenu, en incluant la technologie principale et la technologie frontale pour le rendu des expériences. La diffusion de contenu dans un CMS avec pile pleine survient généralement sur les API de diffusion de contenu interne. La fonctionnalité frontale est généralement spécifique au CMS avec pile pleine. Ce couplage de la technologie frontale avec le serveur principal de contenu permet la création d’expérience WYSIWYG (ce que vous voyez est ce que vous obtenez) comme avantage clé.

## CMS hybride {#hybrid-cms}

Une évolution moderne du CMS avec pile pleine peut être un CMS hybride. Cela permet de combiner le meilleur des deux mondes :

* un développement frontal efficace sur tous les canaux à l’aide d’outils frontaux modernes,
* tout en conservant la création d’expérience « WYSIWYG » afin d’autonomiser les utilisateurs non techniques et d’éviter que l’informatique ne devienne un goulot d’étranglement pour la gestion de contenu et d’expérience entre les entreprises.

Pour ce faire, il faut adopter des structures frontales modernes, telles que React, mais aussi maintenir un minimum de couplage avec le serveur principal de contenu.

## CMS découplé {#decoupled-cms}

Bien que le terme CMS découplé soit parfois utilisé indépendamment, il décrit essentiellement un serveur principal CMS découplé en soulignant sa caractéristique clé qui réside dans le découplage de l’application frontale côté client.

## CMS découplé {#headful-cms}

Il s’agit d’un autre terme pour un CMS traditionnel.

## Informations complémentaires {#further-reading}

Vous pouvez en savoir plus sur l’utilisation d’AEM dans une topologie CMS découplé ici :

* [Présentation d’Adobe Experience Manager en tant que CMS découplé](/help/headless/introduction.md)
