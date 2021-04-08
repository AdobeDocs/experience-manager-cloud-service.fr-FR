---
title: 'Modification d’un Programme de production '
description: Modification d’un Programme de production
exl-id: 745c10af-f0a0-49e9-bb79-3fd058fad16c
translation-type: tm+mt
source-git-commit: 9de1b85f8909709c08cb7358414c18c813aac684
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Modification d&#39;un Programme de production {#create-production-program}

Les utilisateurs disposant des autorisations requises peuvent désormais modifier un programme de production, ce qui leur permet d’effectuer les opérations suivantes en libre-service :

* Ajouter la solution Sites à un programme existant avec Ressources (ou vice versa).
* Supprimez des sites (ou des ressources) d’un programme existant avec des sites et des ressources.
* Ajoutez ensuite les droits de solution inutilisés à un programme existant ou en tant que nouveau Programme.

   >[!NOTE]
   >Un utilisateur du rôle Propriétaire de l&#39;entreprise doit être connecté pour pouvoir modifier le programme.

Pour modifier un programme de production, procédez comme suit :

1. Cliquez sur l&#39;option **Modifier le programme** de la page *Aperçu* de Cloud Manager.

   ![](assets/edit-program-overview.png)

1. La page **Modifier le Programme** affiche deux onglets **Général** et **Solutions et Ajoutes**.

   Accédez à l&#39;onglet **Général** pour modifier la description du programme.

   ![](assets/edit-program-general.png)

   L&#39;onglet **Solutions &amp; Ajoutes-ons** affiche deux options, telles que **Sites** et **Actifs** pour les programmes Production et Sandbox. Vous pouvez également sélectionner l&#39;option de module complémentaire **Commerce**, disponible sous **Sites**, comme illustré dans la figure ci-dessous.

   ![](assets/edit-prg.png)

   >[!NOTE]
   >Au moins une solution doit être sélectionnée pour un Programme, c’est-à-dire que l’utilisateur n’est pas autorisé à désélectionner toutes les solutions pendant le processus de modification du programme.

1. Cliquez sur **Enregistrer** pour terminer le processus de modification du programme.


## Considérations relatives à la modification d’un Programme {#considerations-editing}

Peu de considérations doivent être examinées lors de la modification d’un programme :

* Au moins une solution doit être sélectionnée pour un Programme, c’est-à-dire que l’utilisateur n’est pas autorisé à désélectionner toutes les solutions pendant le processus de modification du programme.

* Cliquez sur le bouton **Enregistrer**, si les solutions sélectionnées ont changé, les mises à jour des solutions apportées aux environnements prendront effet après le prochain déploiement.
