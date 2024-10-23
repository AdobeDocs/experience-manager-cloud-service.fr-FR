---
title: Installation et configuration des lecteurs dans Screens as a Cloud Service
description: Cette page décrit comment installer et configurer des lecteurs dans Screens as a Cloud Service.
exl-id: a022738a-c543-4629-a244-f70fa294fe7f
feature: Developing Screens
role: Admin, Developer, User
source-git-commit: 53086e2ec6d9d962a8f1cb1cc40f0601da74ac63
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 95%

---

# Installation et configuration des lecteurs dans Screens as a Cloud Service {#installing-players-screens-cloud}

Cette section décrit comment installer des lecteurs AEM Screens enregistrés sur des instances d’AEM on-premise. De plus, vous devez réinitialiser le lecteur existant sur les paramètres d’usine, puis enregistrer le nouveau lecteur par rapport à AEM Screens as a Cloud Service.

## Objectif {#objective}

Ce document vous aide à comprendre comment configurer votre lecteur avant d’enregistrer les lecteurs. Après lecture, vous devriez être en mesure de comprendre :

* où installer les lecteurs et à partir d’où
* Comment mettre à jour le lecteur en mode cloud

## La procédure de définition du lecteur en mode cloud {#cloud-mode-setup}

Une fois que vous avez téléchargé le dernier lecteur à partir de [Téléchargements du lecteur AEM Screens](https://download.macromedia.com/screens/), vous disposez de tous les éléments pour mettre à jour votre lecteur en mode cloud.

Pour mettre à jour votre lecteur, procédez comme suit :

1. Ouvrez le lecteur AEM Screens.

   >[!NOTE]
   >Vous pouvez choisir de tester avec des appareils dédiés ou avec une extension web sur votre propre lecteur.

1. Cliquez sur l’onglet **Configuration**, puis sur le bouton **Aux paramètres d’usine** sous l’option **Réinitialiser**.

   ![Bouton À la fabrique sous Option de réinitialisation](/help/screens-cloud/assets/player/installplayer-2.png)

1. Cliquez sur **Confirmer** pour réinitialiser votre lecteur.

1. Toujours à partir de l’onglet **Configuration**, cliquez sur le bouton **Passer en mode cloud** sous l’option **Activer le mode d’exécution**.

   ![Bouton Passer en mode cloud sous l’option Activer/désactiver le mode d’exécution](/help/screens-cloud/assets/player/installplayer-1.png)

1. Le fait de cliquer sur **Confirmer** qui s’affiche lorsque vous passez en mode cloud annule l’enregistrement du lecteur.

## Suivi de base de la lecture {#playback-monitoring}

Le lecteur signale différentes mesures de lecture pour chaque `ping` qui correspond par défaut à 30 secondes. Sur la base de ces mesures, Adobe peut détecter différents cas de figure, tels que des problèmes de lecture bloquée, d’écran vide et de planification. Cette détection permet de comprendre et de résoudre les problèmes liés à l’appareil et d’accélérer ainsi l’examen des problèmes et les mesures correctives.

La surveillance de base de la lecture dans un lecteur AEM Screens nous permet d’effectuer les opérations suivantes :

* Surveiller à distance si un lecteur lit correctement le contenu

* Améliorer la réactivité des écrans vierges ou des expériences rompues dans ce champ

* Réduit le risque d’afficher une expérience rompue à l’utilisateur.

### Présentation des propriétés {#understand-properties}

Les propriétés suivantes sont incluses dans chaque `ping` :

| Propriété | Description |
|---|---|
| id {string} | identifiant du lecteur |
| activeChannel {string} | chemin du canal en cours de lecture ou valeur nulle si rien n’est planifié |
| activeElements {string} | chaîne séparée par des virgules, éléments actuellement visibles dans tous les canaux de séquence de lecture (plusieurs dans le cas d’une disposition multizone) |
| isDefaultContent {boolean} | true si le canal de lecture est considéré comme un canal par défaut ou de secours (c’est-à-dire qu’il a la priorité 1 et aucune planification) |
| hasContentChanged {boolean} | true si le contenu a changé au cours des 5 dernières minutes, false dans le cas contraire |
| lastContentChange {string} | date et heure de la dernière modification du contenu |

>[!NOTE]
>
>Vous pouvez éventuellement activer une propriété plus avancée à partir des préférences du lecteur (activer la surveillance de lecture) :
>
>| Propriété | Description |
>|---|---|
>| isContentRendering {boolean} | true si le GPU peut confirmer qu’il lit du contenu réel (en fonction de l’analyse des pixels) |

### Limites {#limitations}

Vous trouverez ci-dessous quelques limitations au suivi de base de la lecture :

* Le lecteur signale son propre état de lecture au serveur ; il nécessite donc une connexion principale.

* La propriété `isContentRendering` vérifiant le GPU nécessite actuellement trop de ressources pour être activée par défaut et nécessite une inclusion explicite dans les préférences du lecteur. Il est recommandé de ne pas l’utiliser avec les vidéos en production.

* Cette fonctionnalité est uniquement prise en charge pour les canaux de séquence et ne couvre pas encore le cas d’utilisation des canaux interactifs (SPA).

* Les mesures ne sont pas encore entièrement accessibles aux clientes et aux clients ; Adobe travaille à la mise en place prochaine d’un mécanisme de création de rapports et d’alerte de type tableau de bord.

## Prochaines étapes {#whats-next}

Maintenant que vous avez installé et configuré le lecteur en mode cloud, continuez votre parcours Screens as a Cloud Service. Voir [Enregistrement des lecteurs dans Screens as a Cloud Service](/help/screens-cloud/managing-players-registration/registering-players-screens-cloud.md) du fournisseur de services Screens.
