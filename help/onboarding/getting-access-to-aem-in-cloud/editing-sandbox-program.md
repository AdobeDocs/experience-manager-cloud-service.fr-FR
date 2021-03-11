---
title: 'Modification d''un Programme de sandbox '
description: 'Modification d''un Programme de sandbox '
translation-type: tm+mt
source-git-commit: 78bc94f7e3dab37b7f83f480ef5438165e1897bc
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---


# Modification d&#39;un Programme Sandbox {#create-sandbox-program}

Les utilisateurs disposant des autorisations requises peuvent désormais modifier un programme de production, ce qui leur permet d’effectuer les opérations suivantes en libre-service :

* Ajouter la solution Sites à un programme existant avec Ressources (ou inversement).
* Supprimez des sites (ou des ressources) d’un programme existant avec des sites et des ressources.
* Ajoutez ensuite les droits de solution inutilisés à un programme existant ou en tant que nouveau Programme.

   >[!NOTE]
   >Un utilisateur du rôle Propriétaire de l&#39;entreprise doit être connecté pour pouvoir modifier le programme.

Pour modifier un programme Sandbox, procédez comme suit :

1. Accédez à la page **Modifier le Programme**.

1. La page **Modifier le Programme** affiche deux onglets (Général et Solutions) pour les programmes Production et Sandbox.
   ![](assets/edit-program.png)

   >[!NOTE]
   >Bien que les sites et les ressources soient affichés, l&#39;un d&#39;eux peut être désactivé en fonction de ce qui a été acheté et inutilisé. En particulier, si l&#39;entreprise ne dispose pas de droits inutilisés pour une solution particulière, cette solution est affichée mais désactivée.

## Considérations relatives à la modification d’un Programme {#considerations-editing}

Peu de considérations doivent être examinées lors de la modification d’un programme :

* Au moins une solution doit être sélectionnée pour un Programme, c&#39;est-à-dire que l&#39;utilisation ne sera pas autorisée à désélectionner toutes les solutions pendant le processus de modification du programme.

* Cliquez sur le bouton **Enregistrer**, si les solutions sélectionnées ont changé, les mises à jour des solutions apportées aux environnements prendront effet après le prochain déploiement.