---
title: Enregistrement de lecteurs dans Screens as a Cloud Service
description: Cette page décrit comment enregistrer des lecteurs dans Screens as a Cloud Service.
source-git-commit: b9b27c09b1f4a1799a8c974dfb846295664be998
workflow-type: ht
source-wordcount: '395'
ht-degree: 100%

---


# Enregistrement de lecteurs dans Screens as a Cloud Service {#registering-players-screens-cloud}

Une fois que vous avez installé et configuré des lecteurs pour Screens as a Cloud Service, vous devez enregistrer les lecteurs.

## Objectif {#objective}

Ce document vous aide à comprendre l’enregistrement des lecteurs dans le fournisseur de services Screens. Après lecture, vous devriez être en mesure de :

* comprendre comment enregistrer des lecteurs
* terminer le processus d’enregistrement auprès du fournisseur de services Screens

## Procédure d’enregistrement d’un lecteur Screens {#register-players}

Une fois que vous avez installé votre lecteur sur Screens as a Cloud Service, vous êtes prêt à enregistrer votre lecteur auprès du fournisseur de services Screens.

Pour enregistrer votre lecteur, procédez comme suit :

1. Connectez-vous au fournisseur de services Screens.

1. Accédez à **Codes d’enregistrement** sous **Gestion des lecteurs** dans le panneau de navigation de gauche, puis cliquez sur **Créer un code**.

   >[!NOTE]
   >S’il n’existe aucun code valide/non expiré, cliquez sur Créer un code, saisissez un nom pour le code et choisissez les paramètres d’expiration en fonction de vos besoins.

   ![image](/help/screens-cloud/assets/player/register-player1.png)

1. Renseignez les champs suivants dans la boîte de dialogue **Créer un code d’enregistrement** :

   ![image](/help/screens-cloud/assets/player/register-player2.png)

   1. **Nom du code d’enregistrement** : nom de votre code d’enregistrement
   1. **Expiration du code d’enregistrement** : date d’expiration du code d’enregistrement
   1. **Limiter l’utilisation** : basculez le bouton pour activer ou désactiver la limite d’utilisation de votre code d’enregistrement. Par défaut, l’option Limiter l’utilisation est désactivée.
   1. **Limite d’utilisation** : sélectionnez le nombre correspondant à votre limite d’utilisation.

1. Cliquez sur **Créer** pour créer le code d’enregistrement. Votre lecteur s’affiche avec le code d’enregistrement dans la liste.

   ![image](/help/screens-cloud/assets/player/register-player3.png)

1. Cliquez sur la valeur située sous la colonne **CODE D’ENREGISTREMENT** pour copier la valeur dans le presse-papiers.

1. Collez cette valeur dans le champ **Saisir le code** dans l’onglet **Enregistrement du lecteur** de l’interface utilisateur d’administration du lecteur AEM Screens, puis cliquez sur **Enregistrer**.

   ![image](/help/screens-cloud/assets/player/register-player4.png)


1. Une fois que vous avez ajouté le code, vous verrez que le lecteur est désormais enregistré dans l’interface utilisateur d’administration du lecteur.

   ![image](/help/screens-cloud/assets/player/register-player5.png)

1. Vous devriez voir ce lecteur s’afficher dans **Lecteurs** à partir du panneau de navigation de gauche. Le code qui s’affiche dans le fournisseur de services Screens correspond au panneau **Informations système** de l’interface utilisateur d’administration sous Code du lecteur.

   ![image](/help/screens-cloud/assets/player/register-player6.png)

## Et après ? {#whats-next}

Maintenant que vous avez installé et configuré le lecteur en mode cloud, vous devez continuer votre parcours Screens as a Cloud Service en consultant le document [Attribution du lecteur à un affichage dans Screens as a Cloud Service](/help/screens-cloud/managing-players-registration/assigning-player-display.md) du fournisseur de services Screens.