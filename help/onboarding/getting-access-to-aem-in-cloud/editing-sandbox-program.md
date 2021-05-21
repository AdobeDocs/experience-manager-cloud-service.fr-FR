---
title: 'Modification d’un programme Sandbox '
description: Modification d’un programme Sandbox
exl-id: e4545f7e-5329-40ad-81bb-a383c68f5d66
source-git-commit: ee12a6a81a6852d9ffff674cea69e36c37c0ea65
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 46%

---

# Modification d’un programme Sandbox {#create-sandbox-program}

Les utilisateurs disposant des autorisations requises peuvent désormais modifier un programme de production, ce qui leur permet d’effectuer les opérations suivantes en libre-service :

* Ajoutez la solution Sites à un programme existant avec Assets (ou vice versa).
* Supprimer Sites (ou Assets) d’un programme existant contenant à la fois Sites et Assets.
* Ajouter un deuxième droit non utilisé sur une solution à un programme existant ou à titre de nouveau programme.

   >[!NOTE]
   >Un utilisateur doté du rôle Propriétaire de l’entreprise doit être connecté pour pouvoir modifier le programme.

Pour modifier un programme Sandbox, procédez comme suit :

1. Cliquez sur l’option **Modifier le programme** de la page *Aperçu* de Cloud Manager.

   ![](assets/edit-program-overview.png)

1. La page **Modifier le programme** affiche deux onglets **Général** et **Solutions et modules complémentaires**.

   Accédez à l’onglet **Général** pour modifier la description du programme.

   ![](assets/edit-program-general.png)

   L’onglet **Solutions et modules complémentaires** affiche deux options, telles que **Sites** et **Ressources** pour les programmes Production et Sandbox. Vous pouvez également sélectionner l’option de module complémentaire **Commerce**, disponible sous **Sites**, comme illustré dans la figure ci-dessous.

   ![](assets/edit-prg.png)

   >[!NOTE]
   >Au moins une solution doit être sélectionnée pour un programme, c’est-à-dire que l’utilisateur n’est pas autorisé à désélectionner toutes les solutions pendant le workflow Modifier le programme.

1. Cliquez sur **Enregistrer** pour terminer le processus de modification du programme.


## Considérations relatives à la modification d’un programme {#considerations-editing}

Quelques considérations doivent être prises en compte lors de la modification d’un programme :

* Au moins une solution doit être sélectionnée pour un programme, c’est-à-dire que l’utilisateur n’est pas autorisé à désélectionner toutes les solutions pendant le workflow Modifier le programme.

* Lorsque vous cliquez sur le bouton **Enregistrer** et que des modifications ont été apportées à la sélection des solutions, les mises à jour des solutions apportées aux environnements prendront effet après le prochain déploiement.
