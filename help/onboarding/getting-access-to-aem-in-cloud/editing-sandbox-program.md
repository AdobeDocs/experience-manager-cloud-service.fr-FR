---
title: 'Modification d’un programme Sandbox '
description: Modification d’un programme Sandbox
exl-id: e4545f7e-5329-40ad-81bb-a383c68f5d66
source-git-commit: ee12a6a81a6852d9ffff674cea69e36c37c0ea65
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Modification d’un programme Sandbox {#create-sandbox-program}

Les utilisateurs disposant des autorisations requises peuvent désormais modifier un programme de production, ce qui leur permet d’effectuer les opérations suivantes en libre-service :

* Ajoutez la solution Sites à un programme existant avec Assets (ou vice versa).
* Supprimez Sites (ou Assets) d’un programme existant avec Sites et Assets.
* Ajoutez le deuxième droit de solution inutilisé à un programme existant ou en tant que nouveau programme.

   >[!NOTE]
   >Un utilisateur possédant le rôle Propriétaire de l’entreprise doit être connecté pour pouvoir modifier le programme.

Pour modifier un programme Sandbox, procédez comme suit :

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


## Considérations lors de la modification d’un programme {#considerations-editing}

Peu de considérations doivent être prises en compte lors de la modification d’un programme :

* Au moins une solution doit être sélectionnée pour un programme, c’est-à-dire que l’utilisateur n’est pas autorisé à désélectionner toutes les solutions pendant le workflow Modifier le programme.

* En cliquant sur le bouton **Enregistrer**, si les solutions sélectionnées ont changé, les mises à jour des solutions aux environnements prendront effet après le prochain déploiement.
