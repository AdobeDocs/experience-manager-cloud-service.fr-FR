---
title: Enregistrement des lecteurs dans Screens en tant que Cloud Service
description: Cette page décrit comment enregistrer des lecteurs dans Screens en tant que Cloud Service.
hide: true
hidefromtoc: true
index: false
source-git-commit: c65eeaf74ddfd81d37eb7090b84c8bf6f876dc72
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 1%

---


# Enregistrement des lecteurs dans Screens en tant que Cloud Service {#registering-players-screens-cloud}

Une fois que vous avez installé et configuré les lecteurs pour Screens en tant que Cloud Service, vous devez enregistrer les lecteurs.

## Intention {#objective}

Ce document vous aide à comprendre l’enregistrement des lecteurs dans le fournisseur de services Screens. Après lecture, vous devez :

* Découvrez comment enregistrer des lecteurs.
* Gérez vos canaux dans un projet AEM Screens, en termes de portée.

## Procédure d’enregistrement d’un lecteur Screens {#register-players}

Une fois que vous avez installé votre lecteur sur Screens en tant que Cloud Service, vous êtes prêt à enregistrer votre lecteur auprès du fournisseur de services Screens.

Pour enregistrer votre lecteur, procédez comme suit :

1. Connectez-vous au fournisseur de services Screens.

1. Accédez à **Codes d’enregistrement** sous **Gestion des lecteurs** dans le panneau de navigation de gauche, puis cliquez sur **Créer un code**.

   >[!NOTE]
   >S’il n’existe aucun code valide/non expiré, cliquez sur créer le code, saisissez un nom pour le code et choisissez les paramètres d’expiration en fonction de vos besoins.

   ![image](/help/screens-cloud/assets/player/register-player1.png)

1. Renseignez les champs suivants dans la boîte de dialogue **Créer un code d’enregistrement** :

   ![image](/help/screens-cloud/assets/player/register-player2.png)

   1. **Nom du code d’enregistrement** : Nom de votre code d’enregistrement
   1. **Expiration du code d’enregistrement** : Date d’expiration du code d’enregistrement
   1. **Limiter l’utilisation** : Active/désactive le bouton pour désactiver la limite d’utilisation de votre code d’enregistrement. Par défaut, l’option Limiter l’utilisation est désactivée.
   1. **Limite d’utilisation** : Sélectionnez le nombre correspondant à votre limite d’utilisation.

1. Cliquez sur **Créer** pour créer le code d’enregistrement. Votre lecteur s’affiche avec le code d’enregistrement dans la liste.

   ![image](/help/screens-cloud/assets/player/register-player3.png)

1. Cliquez sur la valeur située sous la colonne **CODE D’ENREGISTREMENT** pour copier la valeur dans le Presse-papiers.

1. Collez cette valeur dans le champ **Saisissez le code** dans l’onglet **Enregistrement du lecteur** de l’interface utilisateur d’administration du lecteur AEM Screens, puis cliquez sur **Enregistrer**.

   ![image](/help/screens-cloud/assets/player/register-player4.png)


1. Une fois que vous avez ajouté le code, vous verrez que le lecteur est désormais enregistré dans l’interface utilisateur d’administration du lecteur.

   ![image](/help/screens-cloud/assets/player/register-player5.png)

1. Vous devriez voir ce lecteur s’afficher dans **Lecteurs** à partir du panneau de navigation de gauche. Le code qui s’affiche dans le fournisseur de services Screens correspond au panneau **Informations système** de l’interface utilisateur d’administration sous Code du lecteur.

   ![image](/help/screens-cloud/assets/player/register-player6.png)

