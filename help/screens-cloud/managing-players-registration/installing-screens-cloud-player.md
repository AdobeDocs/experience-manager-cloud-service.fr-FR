---
title: Installation et configuration des lecteurs dans Screens en tant que Cloud Service
description: Cette page décrit comment installer et configurer des lecteurs dans Screens en tant que Cloud Service.
source-git-commit: 1fc06f987bb40d940bbec9c37e6d58c2c1ca9266
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 1%

---


# Installation et configuration des lecteurs dans Screens en tant que Cloud Service {#installing-players-screens-cloud}

Cette section décrit comment installer des lecteurs AEM Screens enregistrés sur des instances d’AEM on-premise. De plus, vous devez réinitialiser le lecteur existant en usine, puis enregistrer le nouveau lecteur par rapport à AEM Screens en tant que Cloud Service.

## Objectif {#objective}

Ce document vous aide à comprendre comment configurer votre lecteur avant d’enregistrer les lecteurs. Après lecture, vous devriez être en mesure de comprendre :

* où installer les lecteurs à partir de
* Comment mettre à jour le lecteur en mode cloud

## Procédure de définition du lecteur en mode cloud {#cloud-mode-setup}

Une fois que vous avez téléchargé le dernier lecteur à partir des [Téléchargements du lecteur AEM Screens](https://download.macromedia.com/screens/), vous êtes prêt à mettre à jour votre lecteur en mode cloud.

Pour mettre à jour votre lecteur, procédez comme suit :

1. Ouvrez le lecteur AEM Screens.

   >[!NOTE]
   >Vous pouvez choisir de tester avec des périphériques matériels dédiés ou avec une extension web sur votre propre lecteur.

1. Cliquez sur l’onglet **Configuration** et cliquez sur le bouton **To Factory** sous l’option **Réinitialiser**.

   ![image](/help/screens-cloud/assets/player/installplayer-2.png)

1. Cliquez sur **Confirmer** pour réinitialiser votre lecteur.

1. Toujours à partir de l’onglet **Configuration** et cliquez sur le bouton **Passer en mode cloud** sous l’option **Activer le mode d’exécution**.

   ![image](/help/screens-cloud/assets/player/installplayer-1.png)

1. Cliquez sur **Confirmer** qui s’affiche lorsque vous passez en mode cloud, annule l’enregistrement du lecteur.

## Surveillance de lecture de base {#playback-monitoring}

Le lecteur signale différentes mesures de lecture pour chaque `ping` qui correspond par défaut à 30 secondes. Selon les mesures, vous pouvez détecter différents cas de périphérie, tels que des problèmes de blocage, d’écran vide et de planification. Vous pouvez ainsi comprendre et résoudre les problèmes liés à l’appareil et accélérer ainsi les enquêtes et les mesures correctives.

La surveillance de base de la lecture dans un lecteur AEM Screens vous permet d’effectuer les opérations suivantes :

* Surveillez à distance si un lecteur lit correctement le contenu

* Améliorer la réactivité des écrans vierges ou des expériences rompues dans le champ

* Réduire le risque d’afficher une expérience rompue à l’utilisateur final

### Présentation des propriétés {#understand-properties}

Les propriétés suivantes sont incluses dans chaque `ping` :

| Propriété | Description |
|---|---|
| id {string} | l’identifiant du lecteur |
| activeChannel {string} | chemin du canal en cours de lecture ou valeur nulle si rien n’est planifié |
| activeElements {string} | chaîne séparée par des virgules, éléments actuellement visibles dans tous les canaux de séquence de lecture (plusieurs dans le cas d’une disposition multizone) |
| isDefaultContent {boolean} | true si le canal de lecture est considéré comme un canal par défaut ou de secours (c’est-à-dire qu’il a la priorité 1 et aucun planning) |
| hasContentChanged {boolean} | true si le contenu a changé au cours des 5 dernières minutes, false dans le cas contraire |
| lastContentChange {string} | date et heure de la dernière modification du contenu |

>[!NOTE]
>Vous pouvez éventuellement activer une propriété plus avancée à partir des préférences du lecteur (activer la surveillance de lecture), à savoir :
>|Property|Description|
>|—|—|
>|isContentRendering {boolean}|true si le GPU peut confirmer qu’il lit du contenu réel (en fonction de l’analyse des pixels)|

### Restrictions {#limitations}

Vous trouverez ci-dessous quelques limites à la surveillance de lecture de base :

* Comme le lecteur signale son propre état de lecture au serveur, il a besoin d’une principale connexion.

* La propriété `isContentRendering` qui vérifie le GPU nécessite actuellement de nombreuses ressources pour être activée par défaut et nécessite une inclusion explicite dans les préférences du lecteur. Il est recommandé de ne pas l’utiliser conjointement avec les vidéos.

* Pris en charge pour les canaux de séquence.

## Et après ? {#whats-next}

Maintenant que vous avez installé et configuré le lecteur en mode cloud, vous devez continuer votre parcours Screens en tant que Cloud Service en consultant le document [Enregistrement des lecteurs dans Screens en tant que Cloud Service](/help/screens-cloud/managing-players-registration/registering-players-screens-cloud.md) du fournisseur de services Screens.