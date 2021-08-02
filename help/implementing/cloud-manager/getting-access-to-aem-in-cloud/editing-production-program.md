---
title: 'Modification d’un programme de production '
description: Modification d’un programme de production
exl-id: 745c10af-f0a0-49e9-bb79-3fd058fad16c
source-git-commit: 09d5d125840abb6d6cc5443816f3b2fe6602459f
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 96%

---

# Modification d’un programme de production {#create-production-program}

Les utilisateurs disposant des autorisations requises peuvent désormais modifier un programme de production, ce qui leur permet d’effectuer les opérations suivantes en libre-service :

* Ajouter la solution Sites à un programme existant avec Assets (ou inversement).
* Supprimer Sites (ou Assets) d’un programme existant contenant à la fois Sites et Assets.
* Ajouter un deuxième droit non utilisé sur une solution à un programme existant ou à titre de nouveau programme.

   >[!NOTE]
   >Un utilisateur doté du rôle Propriétaire de l’entreprise doit être connecté pour pouvoir modifier le programme.

Pour modifier un programme de production, procédez comme suit :

1. Cliquez sur l’option **Modifier le programme** de la page *Aperçu* de Cloud Manager.

   ![](assets/edit-program-overview.png)

1. La page **Modifier le programme** affiche deux onglets **Général** et **Solutions et modules complémentaires**.

   Accédez à l’onglet **Général** pour modifier la description du programme.

   ![](assets/edit-program-prod1.png)

   L’onglet **Solutions et modules complémentaires** affiche deux options, telles que **Sites** et **Ressources** pour les programmes Production et Sandbox. Vous pouvez également sélectionner l’option de module complémentaire **Commerce**, disponible sous **Sites**, comme illustré dans la figure ci-dessous.

   ![](assets/edit-prg.png)

   >[!NOTE]
   >Au moins une solution doit être sélectionnée pour un programme, ce qui signifie que l’utilisateur ne sera pas autorisé à désélectionner toutes les solutions pendant le processus de modification du programme.

1. Cliquez sur **Mettre à jour** pour terminer le processus de modification du programme.


## Considérations relatives à la modification d’un programme {#considerations-editing}

Quelques considérations doivent être prises en compte lors de la modification d’un programme :

* Au moins une solution doit être sélectionnée pour un programme, ce qui signifie que l’utilisateur ne sera pas autorisé à désélectionner toutes les solutions pendant le processus de modification du programme.

* Lorsque vous cliquez sur le bouton **Enregistrer** et que des modifications ont été apportées à la sélection des solutions, les mises à jour des solutions apportées aux environnements prendront effet après le prochain déploiement.
