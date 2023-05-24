---
title: Création et gestion de révisions dans des formulaires
seo-title: Creating and managing reviews in forms
description: Une révision est un mécanisme qui permet à un ou plusieurs réviseurs de commenter un formulaire.
seo-description: A Review is a mechanism that allows one or more reviewers to comment on a form.
topic-tags: forms-manager
source-git-commit: 3efd7d81424369ce6430802373129ab91b7356ab
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 29%

---

# Création et gestion de révisions des formulaires{#creating-and-managing-reviews-to-forms}

## Révision {#review}

Une révision est un mécanisme qui permet à un ou plusieurs réviseurs de commenter des formulaires.

## Configuration d’une révision {#setting-up-a-review}

1. Accédez à l’explorateur de formulaires et sélectionnez un formulaire à réviser.
1. Si aucune révision du formulaire n’est en cours, une **Commencer la révision** ![aem6forms_review_chat_comment](assets/aem6forms_review_chat_comment.png) s’affiche dans la barre Action. Cliquez sur le bouton **Commencer la révision** ![aem6forms_review_chat_comment](assets/aem6forms_review_chat_comment.png) icône .
1. Saisissez les informations suivantes :

   * **Titre**: Obligatoire, peut contenir des caractères alphanumériques, des tirets et des traits de soulignement.
   * **Description**: Description facultative de l’objectif/du contenu à réviser.
   * **Deadline**: (Facultatif) la date de fin de la révision. Une fois l’échéance passée, la tâche est indiquée comme étant « En retard ».
   * **Nom du réviseur**: Un minimum de un est obligatoire. Utilisez la liste déroulante pour ajouter des réviseurs, en saisissant une liste de noms de tous les noms correspondants. sélectionnez un nom, puis cliquez sur **Ajouter**. Dans la section suivante du **Réviseurs** affiche le nom de tous les réviseurs.

1. Cliquez sur le bouton **Début** pour commencer une révision.

   >[!NOTE]
   >
   >* L’administrateur peut accéder à tous les groupes associés aux utilisateurs du formulaire.
   >* Le groupe Utilisateurs et utilisatrices de service ne peut pas être sélectionné pour la révision.


### Actions survenant lorsqu’une révision est configurée {#actions-that-occur-when-a-review-is-set-up}

Cette section décrit ce qui se produit lorsqu’une révision est créée ou configurée.

1. Une tâche de révision est créée et affectée à la personne qui vient d’être ajoutée.
1. Une tâche de révision est affectée à tous les réviseurs. La tâche apparaît dans la section Notifications. Un réviseur peut cliquer sur une notification ou accéder à la boîte de réception pour afficher la tâche. Le réviseur peut cliquer pour ouvrir la tâche de révision, afficher le formulaire et commencer à ajouter des commentaires.

   ![Alerte de notification du réviseur](assets/review-notification-img.png)

   Alerte de notification du réviseur

1. La zone de commentaire est accessible aux réviseurs du formulaire. D&#39;autres peuvent lire les commentaires mais ne les ajoutent pas.

## Gestion d’une révision {#managing-a-review}

>[!NOTE]
>
>* Seules les révisions en cours peuvent être modifiées.
>* Les révisions terminées ne peuvent pas être modifiées.


1. Accédez à l’onglet Formulaires et sélectionnez un formulaire.

1. Si une révision d’un formulaire est en cours et que vous en êtes l’initiateur, une **Gérer la révision** ![aem6forms_review_chat_comment](assets/aem6forms_review_chat_comment.png) s’affiche dans la barre d’actions. Seul l’initiateur de la révision peut gérer (mettre à jour/terminer) la révision.

   Cliquez sur le bouton **Gérer la révision** ![aem6forms_review_chat_comment](assets/aem6forms_review_chat_comment.png)icône .

   Cette icône est désactivée pour les utilisateurs autres que l’initiateur.

1. Vous obtenez maintenant un écran qui affiche des informations :

   * **Nom de la révision** : ce champ ne peut pas être modifié.

   * **Description de la révision** : ce champ peut être modifié.

   * **Échéance** : ce champ peut être modifié. Vous pouvez modifier l’échéance selon n’importe quelle date et heure au-delà de la date et de l’heure actuelles.

   * **Réviseurs**: Disponible pour modification. Vous pouvez ajouter ou supprimer des réviseurs. Si une tâche est en retard, vous ne pouvez ajouter des réviseurs qu&#39;après avoir prolongé l&#39;échéance au-delà de la date actuelle.

1. Pour mettre fin à la révision, cliquez sur **Fin**.

### Actions survenant lorsqu’une révision est modifiée {#actions-that-occur-when-a-review-is-modified}

Cette section décrit ce qui se passe dans **Mise à jour/fin de révision**:

1. Si la description de la révision est modifiée, la tâche correspondante des réviseurs et de l’initiateur est mise à jour.
1. Si la date limite de révision est modifiée, la tâche correspondante pour les réviseurs est mise à jour avec la nouvelle date.

1. Si un réviseur est supprimé :

   ![Suppression d’un réviseur](assets/removeduser.png)

   Suppression d’un réviseur

   1. Si elle est incomplète, la tâche affectée est arrêtée.
   1. Le réviseur ou la réviseuse ne peut plus ajouter de commentaires dans le formulaire.

1. Si un réviseur est ajouté :

   ![Ajout d’un réviseur](assets/addedreviewer.png)

   Ajout d’un réviseur

   1. Une tâche de révision est créée et affectée au réviseur qui vient d’être ajouté.
   1. Le nouveau réviseur ou la nouvelle réviseuse peut ajouter des commentaires à propos du formulaire.

1. Lorsqu’une révision est terminée :

   1. **Réviseurs**: Pour chaque validant, la tâche incomplète associée à la révision est terminée. La tâche n’apparaît plus comme &quot;En attente&quot; dans la section Notifications du réviseur.
   1. **Initiateur**: La tâche affectée à l’initiateur de la révision est marquée comme étant terminée. La tâche est supprimée de la section Notification de l’initiateur de la révision.
   1. **Tous**: La révision s’affiche dans la section Révisions précédentes . Aucun autre commentaire ne peut être ajouté.
   ![Révision terminée](assets/review-complete-imgg.png).
