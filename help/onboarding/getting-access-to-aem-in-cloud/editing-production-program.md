---
title: 'Modification d’un Programme de production '
description: Modification d’un Programme de production
exl-id: 745c10af-f0a0-49e9-bb79-3fd058fad16c
translation-type: tm+mt
source-git-commit: 6a5882a942511a07b9dcdd2e2bf47eb311235f92
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# Modification d&#39;un Programme de production {#create-production-program}

Les utilisateurs disposant des autorisations requises peuvent désormais modifier un programme de production, ce qui leur permet d’effectuer les opérations suivantes en libre-service :

* Ajouter la solution Sites à un programme existant avec Ressources (ou inversement).
* Supprimez des sites (ou des ressources) d’un programme existant avec des sites et des ressources.
* Ajoutez ensuite les droits de solution inutilisés à un programme existant ou en tant que nouveau Programme.

   >[!NOTE]
   >Un utilisateur du rôle Propriétaire de l&#39;entreprise doit être connecté pour pouvoir modifier le programme.

Pour modifier un programme de production, procédez comme suit :

1. Accédez à la page **Modifier le Programme** à partir de la page *Aperçu* de Cloud Manager.

1. La page **Modifier le Programme** affiche trois options (**Sites**, **Commerce** et **Actifs**) pour les programmes Production et Sandbox.

   ![](assets/edit-prg.png)


## Considérations relatives à la modification d’un Programme {#considerations-editing}

Peu de considérations doivent être examinées lors de la modification d’un programme :

* Au moins une solution doit être sélectionnée pour un Programme, c&#39;est-à-dire que l&#39;utilisation ne sera pas autorisée à désélectionner toutes les solutions pendant le processus de modification du programme.

* Cliquez sur le bouton **Enregistrer**, si les solutions sélectionnées ont changé, les mises à jour des solutions apportées aux environnements prendront effet après le prochain déploiement.
