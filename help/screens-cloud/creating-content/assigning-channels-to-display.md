---
title: Affectation d’un canal à un affichage dans Screens en tant que Cloud Service
description: Cette page décrit comment attribuer un canal à un affichage dans Screens en tant que Cloud Service.
hide: true
hidefromtoc: true
index: false
source-git-commit: 2ce9c1c30569edb59a0dcc8c241391e5e177b14c
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 40%

---


# Affectation d’un canal à un affichage dans Screens en tant que Cloud Service {#assign-channel-displays-screens-cloud}

Une fois le projet configuré, vous devez attribuer le canal à un affichage pour afficher le contenu.

## Intention {#objective}

Ce document vous aide à comprendre comment attribuer un canal à un affichage, une fois que votre affichage est prêt et que vous avez ajouté du contenu à votre canal et que vous l’avez publié. Après avoir lu, vous devriez être en mesure d’attribuer un canal à un affichage à partir du fournisseur de services Screens.

## Prérequis {#prerequisites}

Avant d’exécuter les étapes ci-dessous pour attribuer un canal à un affichage, vous devez avoir terminé l’apprentissage :

* Création et gestion des affichages
* Création et gestion des canaux

## Étapes pour attribuer un canal à un affichage {#assign-channel-to-display}

Suivez les étapes ci-dessous pour attribuer un canal à un affichage :

1. Accédez à Fournisseur de services Screens et sélectionnez **Affichages** dans le panneau de navigation de gauche.

1. Cliquez sur **Attribuer le canal** à l’affichage.

   ![image](/help/screens-cloud/assets/display/assignchannel-1.png)

1. Renseignez les champs suivants à partir de la boîte de dialogue **Attribuer un canal** .

   ![image](/help/screens-cloud/assets/display/assignchannel-2.png)

   1. Sélectionnez le nom du canal dans la liste déroulante.
   1. Choisissez la priorité.

      >[!NOTE]
      >La priorité est utilisée pour contrôler les attributions au cas où plusieurs d’entre elles correspondent aux critères de lecture. Celle présentant la valeur la plus élevée est toujours prioritaire par rapport aux valeurs plus faibles. Par exemple, s’il existe deux canaux A et B, A ayant une priorité de 1 et B une priorité de 2, alors le canal B est affiché, car il présente une priorité supérieure à celle de A.
   1. Sélectionnez la date de début et la date de fin dans **Activation**.

1. Cliquez sur **+ Ajouter une périodicité** pour ajouter un planning de périodicité pour votre canal.

   ![image](/help/screens-cloud/assets/create-content/recurrence-1.png)

   >[!NOTE]
   >Vous pouvez ajouter plusieurs plannings de périodicité à votre canal. Les plannings de périodicité s’accompagnent de tranches horaires, ce qui permet de définir une planification globale avec plusieurs canaux qui s’exécutent à des moments spécifiques de la journée et de réutiliser simultanément cette configuration pour tous vos affichages.

   Vous pouvez configurer les options suivantes :

   * **Nom** : intitulé de votre planning de périodicité.
   * **Répéter** : indiquez si la planification s’exécute de manière quotidienne, hebdomadaire, mensuelle ou annuelle.
   * **Début** : heure de début de votre planning.
   * **Fin** : heure de fin de votre planning. Vous pouvez le définir par heure ou par durée.
   * **Heure** : le planning se terminera à une heure définie.
   * **Durée** : le planning s’exécute pendant une durée particulière en heures ou en minutes.

1. Cliquez sur **Créer** et vous verrez maintenant le canal attribué à cet affichage, comme illustré dans la figure ci-dessous.

   ![image](/help/screens-cloud/assets/display/assignchannel-3.png)


## Suite {#whats-next}

Maintenant que vous avez attribué le canal à un affichage, vous devez continuer votre parcours Screens en tant que Cloud Service en consultant le document [Installation et configuration du lecteur Screens pour AEM en tant que Cloud Service](/help/screens-cloud/managing-players-registration/installing-screens-cloud-player.md).
