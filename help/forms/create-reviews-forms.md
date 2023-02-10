---
title: Création et gestion de révisions dans les formulaires
seo-title: Creating and managing reviews in forms
description: Une révision est un mécanisme permettant à un ou plusieurs réviseurs d’ajouter des commentaires sur un élément disponible dans un formulaire.
seo-description: A Review is a mechanism that allows one or more reviewers to comment on an asset that is available in a form.
topic-tags: forms-manager
source-git-commit: 400e9fa0263b3e9bdae10dc80d524b291f99496d
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 64%

---

# Création et gestion de révisions des actifs d’un formulaire{#creating-and-managing-reviews-for-assets-in-forms}

## Révision {#review}

Une révision est un mécanisme qui permet à un ou plusieurs réviseurs de commenter un actif disponible dans un formulaire.

## Configuration d’une révision {#setting-up-a-review}

1. Accédez à l’onglet Formulaires et sélectionnez un formulaire.
1. Si aucune révision du formulaire n’est en cours, une vérification de démarrage ![aem6forms_review_chat_comment](assets/aem6forms_review_chat_comment.png) s’affiche dans la barre Action. Cliquez sur Commencer la révision . ![aem6forms_review_chat_comment](assets/aem6forms_review_chat_comment.png) icône .
1. Saisissez les informations suivantes :

   * Titre : Obligatoire, il peut contenir des caractères alphanumériques, des tirets ou des traits de soulignement.
   * Description : Description facultative de l’objectif/du contenu à réviser.
   * Date limite : (Facultatif) la date de fin de la révision. Une fois l’échéance passée, la tâche est indiquée comme étant « Overdue » (En retard).
   * Réviseurs : au moins un réviseur doit être indiqué. La saisie d’un nom de groupe ou d’utilisateur répertorie tous les noms correspondants, à l’exception du groupe d’utilisateurs du service. sélectionnez un nom, puis cliquez sur Ajouter.

1. Cliquez sur Démarrer pour lancer une révision.

>[!NOTE]
>
>* L’administrateur peut accéder à tous les groupes associés aux utilisateurs du formulaire.
>* Le groupe Utilisateurs du service ne peut pas être sélectionné pour révision.


### Actions survenant lorsqu’une révision est configurée {#actions-that-occur-when-a-review-is-set-up}

Cette section décrit ce qui se produit lorsqu’une révision est créée ou configurée.

1. Une nouvelle tâche de révision est créée et affectée au réviseur sélectionné.
1. Tous les réviseurs se voient affecter une tâche de révision. La tâche apparaît dans leur section Notification. Le réviseur peut soit cliquer sur une notification, soit accéder à la boîte de réception pour afficher la tâche. Le réviseur peut cliquer pour ouvrir la tâche de révision, afficher le formulaire et commencer à ajouter des commentaires.

   ![Alerte de notification du réviseur](assets/review-notification-img.png)

   Alerte de notification du réviseur

1. La zone de commentaire est accessible aux réviseurs du formulaire. Les autres utilisateurs peuvent voir les commentaires, mais ne sont pas habilités à en rédiger.

## Gestion d’une révision {#managing-a-review}

>[!NOTE]
>
>Seules les révisions en cours peuvent être modifiées. La modification des révisions terminées est donc impossible.

1. Accédez à l’onglet Formulaires et sélectionnez un formulaire.

1. Si une révision de ressource est en cours et que vous en êtes l’initiateur, l’icône Gérer la révision ![aem6forms_review_chat_comment](assets/aem6forms_review_chat_comment.png) s’affiche dans la barre Action. Seul l’initiateur de la révision peut gérer (mettre à jour/terminer) la révision.

   Cliquez sur l’icône Gérer la révision ![aem6forms_review_chat_comment](assets/aem6forms_review_chat_comment.png).

   Cette icône est désactivée pour les utilisateurs autres que l’initiateur.

1. Un écran affiche alors les informations suivantes :

   * **Titre**: Ne peut pas être modifié.

   * **Description**: Disponible pour modification.

   * **Deadline**: Disponible pour modification. Vous pouvez modifier l’échéance selon n’importe quelle date et heure au-delà de la date et de l’heure actuelles.

   * **Nom du réviseur**: Disponible pour modification. Vous pouvez ajouter ou supprimer des réviseurs. Si une tâche est échue, vous ne pourrez ajouter des réviseurs qu’après avoir étendu l’échéance au-delà de la date actuelle.

1. Modifiez les champs nécessaires, puis cliquez sur Terminé.

   ![État Mis à jour de la révision dans le Gestionnaire des tâches](assets/manage-review-img.png)

   État Mis à jour de la révision dans le Gestionnaire des tâches

1. Pour mettre fin à la révision, cliquez sur Terminer la révision.

### Action survenant lorsqu’une révision est modifiée {#actions-that-occur-when-a-review-is-modified}

Cette section décrit ce qui se passe lors de la mise à jour/de la fin de la révision :

1. Si la description de la révision est modifiée, la tâche correspondante des réviseurs et de l’initiateur est mise à jour.
1. Si l’échéance de la révision est modifiée, la nouvelle date est appliquée à la tâche correspondante pour les réviseurs.

1. Si un réviseur est supprimé :

   ![Suppression d’un réviseur](assets/removeduser.png)

   Suppression d’un réviseur

   1. Si la tâche affectée est incomplète, elle est terminée.
   1. Le réviseur ne peut plus commenter le formulaire.

1. Si un réviseur est ajouté :

   ![Ajout d’un réviseur](assets/addedreviewer.png)

   Ajout d’un réviseur

   1. Une tâche de révision est créée et affectée au réviseur qui vient d’être ajouté.
   1. Le nouveau réviseur peut ajouter des commentaires sur le formulaire.

1. Lorsqu’une révision est terminée :

   1. **Réviseurs** : pour chaque réviseur, il est mis fin à la tâche incomplète associée à la révision. La tâche n’apparaît plus avec l’état « Pending » (En attente) dans la section Notifications du réviseur.
   1. **Initiateur** : la tâche affectée à l’initiateur de la révision est marquée comme étant terminée. La tâche est supprimée de la section de notification de l’initiateur de la révision.
   1. **Tous** : la révision s’affiche dans la section des révisions précédentes. Plus aucun commentaire ne peut être ajouté.
      ![fin de la révision](assets/review-complete-imgg.png)


