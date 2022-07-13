---
title: Qu’est-ce qu’un CMS sans affichage ?
description: Découvrez le CMS sans affichage. Comment fonctionnent-ils ? Quelles sont les alternatives et les différences ? Pourquoi souhaitez-vous utiliser un CMS sans affichage ?
exl-id: 53f24f69-ad49-4b8e-9a91-36cd64c1f2b9
source-git-commit: bd333d17f96e74227ac148be7164986ea11a0a23
workflow-type: tm+mt
source-wordcount: '754'
ht-degree: 6%

---

# Qu’est-ce qu’un CMS sans affichage ? {#what-is-a-headless-cms}

La gestion de contenu sans affichage est un développement clé de la conception web actuelle qui découple les applications frontales côté client du système de gestion de contenu principal. Un CMS sans interface est donc responsable des services de gestion de contenu (principal), ainsi que des mécanismes permettant aux applications (frontales) d’accéder à ce contenu.

Mais que signifie vraiment ce terme ? Nous vous proposons ici une introduction (très rapide) aux concepts clés.

## Qu’est-ce qu’un système de gestion de contenu (CMS) ? {#content-management-system}

Commençons par les principes de base : qu’est-ce qu’un système de gestion de contenu ?

Un système de gestion de contenu (CMS) stocke, gère et diffuse le contenu utilisé pour fournir vos expériences en ligne.

## CMS traditionnel {#traditional-cms}

Traditionnellement, un CMS inclut à la fois la fonctionnalité principale de stockage et de diffusion de contenu, ainsi que la technologie frontale utilisée pour générer le balisage d’une expérience que votre navigateur affichera (couche de présentation).

Très puissant, vous permettant de contrôler entièrement le contenu et la mise en forme, mais sans la flexibilité nécessaire dans l&#39;environnement en rapide évolution d&#39;aujourd&#39;hui. par exemple, lors de l’interface avec des applications externes.

## CMS découplé {#headless-cms}

Avec un système de gestion de contenu sans interface, le serveur principal et le front-end sont désormais découplés.

La partie sans tête est le serveur principal du contenu.

* « *Un système de gestion de contenu découplé, ou CMS découplé, est un système de gestion de contenu (CMS) back-end uniquement créé dès le départ comme un référentiel de contenu qui rend le contenu accessible via une API pour l’afficher sur n’importe quel appareil.* »

   Voir [Wikipedia](https://en.wikipedia.org/wiki/Headless_content_management_system).

Le serveur frontal, qui est développé et géré indépendamment, récupère du contenu du serveur principal sans interface à l’aide d’une API de diffusion de contenu, généralement au format JSON. Par exemple, il peut s’agir d’une application React ou Angular (application d’une seule page (SPA)).

Un serveur principal CMS sans interface nécessite généralement que le contenu soit structuré en fonction d’un modèle ou d’un schéma. Cela facilite les applications clientes qui demandent le contenu approprié pour le rendu d’une expérience. Certains CMS peuvent présenter du contenu structuré et non structuré au format JSON.

Une caractéristique clé de cette topologie est que le contenu diffusé par le CMS sans tête au format JSON est du contenu pur, sans informations de conception ou de mise en page. Dans une mise en oeuvre CMS sans interface utilisateur graphique, toute la mise en forme et la mise en page sont conservées par l’application frontale découplée.

L’un des principaux avantages d’une topologie CMS sans interface réside dans la possibilité de réutiliser du contenu sur plusieurs canaux, qui peut utiliser différentes implémentations frontales côté client. Cela peut rendre le processus de développement frontal plus efficace. Mais cela signifie également que le processus de développement de l’expérience frontale peut devenir très codé et centré sur l’informatique, et que l’informatique en est propriétaire.

## API de diffusion de contenu {#content-delivery-apis}

Un CMS sans tête peut fournir un ou plusieurs moyens d’exposer du contenu aux applications côté client. API HTTP REST les plus courantes, API GraphQL ou les deux.

Bien qu’une API REST puisse sembler souvent un moyen plus facile de demander du contenu (par exemple, en fournissant du code JSON pour tout le contenu correspondant à un critère), elle fournit généralement trop de contenu à une application cliente. Cela peut entraîner la nécessité pour le client d’analyser et de filtrer le contenu réellement nécessaire au rendu.

GraphQL est en revanche un mécanisme plus ciblé permettant aux applications clientes de rechercher exactement le contenu nécessaire pour effectuer le rendu d’une expérience.

## Gestion de contenu complète {#fullstack-cms}

Un CMS avec pile complète représente généralement la topologie traditionnelle pour la gestion et la diffusion de contenu, en incluant la technologie d’arrière-plan et la technologie frontale pour le rendu des expériences. La diffusion de contenu dans un CMS en pile complète survient généralement sur les API de diffusion de contenu interne. La fonctionnalité front-end est généralement spécifique au CMS de la pile complète. Ce couplage de la technologie frontale avec l’arrière-plan de contenu permet la création d’expérience WYSIWYG (What-you-see-c-est-ce-que-vous-obtenez) comme avantage clé.

## CMS hybride {#hybrid-cms}

Une évolution moderne du CMS à pile complète peut être un CMS hybride. Cela permet de combiner le meilleur des deux mondes :

* un développement frontal efficace sur tous les canaux à l&#39;aide d&#39;outils frontend modernes,
* tout en conservant la création d’expérience WYSIWYG afin d’autonomiser les utilisateurs non techniques et d’éviter que l’informatique ne devienne un goulot d’étranglement pour la gestion de contenu et d’expérience entre les organisations.

Pour ce faire, il faut adopter des structures front-end modernes, telles que React, mais il faut maintenir un minimum de couplage avec le serveur principal de contenu.

## CMS découplé {#decoupled-cms}

Bien que le terme CMS découplé soit parfois utilisé indépendamment, il décrit essentiellement un serveur principal CMS sans tête en soulignant sa caractéristique principale d’être découplé de l’application frontale côté client.

## CMS en tête {#headful-cms}

Il s’agit d’un autre terme pour un CMS traditionnel.

## Informations complémentaires {#further-reading}

Vous pouvez en savoir plus sur l’utilisation des AEM dans une topologie CMS sans interface utilisateur ici :

* [Présentation d’Adobe Experience Manager as a Headless CMS](/help/headless/introduction.md)
