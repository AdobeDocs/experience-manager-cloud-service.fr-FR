---
title: Affectation d’un canal à un affichage dans Screens as a Cloud Service
description: Cette page décrit comment attribuer un canal à un affichage dans Screens as a Cloud Service.
exl-id: ba001c18-7b05-4ae2-aa7f-9ebb320fedd0
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 62%

---

# Affectation d’un canal à un affichage dans Screens as a Cloud Service {#assign-channel-displays-screens-cloud}

Une fois la configuration du projet terminée, vous devez attribuer le canal à un affichage pour afficher le contenu.

## Objectif {#objective}

Ce document vous aide à comprendre comment attribuer un canal à un affichage, une fois que votre affichage est prêt et que vous avez ajouté du contenu à votre canal et que vous l’avez publié. Après lecture, vous devriez être en mesure de comprendre comment attribuer un canal à un affichage à partir du fournisseur de services Screens.

## Prérequis {#prerequisites}

Avant d’exécuter les étapes ci-dessous pour attribuer un canal à un affichage, vous devez avoir terminé l’apprentissage des éléments suivants :

* Création et gestion des affichages
* Création et gestion des canaux

## Étapes d’attribution d’un canal à un affichage {#assign-channel-to-display}

Suivez les étapes ci-dessous pour attribuer un canal à un affichage :

1. Accédez au fournisseur de services Screens et sélectionnez **Affichages** dans le panneau de navigation de gauche.

1. Cliquez sur **Attribuer le canal** à l’affichage.

   ![image](/help/screens-cloud/assets/display/assignchannel-1.png)

1. Renseignez les champs suivants à partir de la boîte de dialogue **Attribuer un canal**.

   ![image](/help/screens-cloud/assets/display/assignchannel-2.png)

   1. Sélectionnez le nom du canal dans la liste déroulante.
   1. Choisissez la priorité.

      >[!NOTE]
      >La priorité est utilisée pour contrôler les attributions au cas où plusieurs d’entre elles correspondent aux critères de lecture. Celui qui a la valeur la plus élevée a toujours la priorité sur les valeurs les plus faibles. Par exemple, s’il existe deux canaux A et B. A a une priorité de 1 et B a une priorité de 2, alors le canal B s’affiche, car il a une priorité plus élevée que A.

   1. Sélectionnez la date de début et la date de fin dans **Activation**.

1. Cliquez sur **+ Ajouter une périodicité** pour ajouter un planning de périodicité pour votre canal.

   ![image](/help/screens-cloud/assets/create-content/recurrence-1.png)

   >[!NOTE]
   >Vous pouvez ajouter plusieurs plannings de périodicité à votre canal. Les plannings de périodicité introduisent des tranches horaires qui vous permettent de définir une planification globale avec plusieurs canaux qui s’exécutent à des moments spécifiques de la journée et de réutiliser simultanément ces tranches horaires pour tous vos affichages.

   Vous pouvez configurer les options suivantes :

   * **Nom** : intitulé de votre planning de périodicité.
   * **Répéter** : indiquez si la planification s’exécute de manière quotidienne, hebdomadaire, mensuelle ou annuelle.
   * **Début** : heure de début de votre planning.
   * **Fin** : heure de fin de votre planning. Vous pouvez le définir par heure ou par durée.
   * **Heure**: Le planning se termine à une heure spécifiée.
   * **Durée** : le planning s’exécute pendant une durée particulière en heures ou en minutes.

1. Cliquez sur **Créer**. Vous pouvez constater qu’un canal est affecté pour cet affichage, comme illustré dans la figure ci-dessous.

   ![image](/help/screens-cloud/assets/display/assignchannel-3.png)


## Et après ? {#whats-next}

Maintenant que vous avez attribué le canal à un affichage, vous devez continuer votre parcours Screens as a Cloud Service en consultant le document [Installation et configuration du lecteur Screens pour AEM as a Cloud Service](/help/screens-cloud/managing-players-registration/installing-screens-cloud-player.md).
