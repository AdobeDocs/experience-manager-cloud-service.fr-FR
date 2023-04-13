---
title: Création et gestion de révisions dans des formulaires
seo-title: Creating and managing reviews in forms
description: Une révision est un mécanisme permettant à un ou plusieurs réviseurs d’ajouter des commentaires sur un élément disponible dans un formulaire.
seo-description: A Review is a mechanism that allows one or more reviewers to comment on an asset that is available in a form.
topic-tags: forms-manager
source-git-commit: 400e9fa0263b3e9bdae10dc80d524b291f99496d
workflow-type: ht
source-wordcount: '670'
ht-degree: 100%

---

# Création et gestion de révisions des actifs d’un formulaire{#creating-and-managing-reviews-for-assets-in-forms}

## Révision {#review}

Une révision est un mécanisme permettant à un ou plusieurs réviseurs ou réviseuses d’ajouter des commentaires sur un élément disponible dans un formulaire.

## Configuration d’une révision {#setting-up-a-review}

1. Accédez à l’onglet Formulaires et sélectionnez un formulaire.
1. Si aucune révision n’est en cours dans le formulaire, l’icône de démarrage d’une révision ![aem6forms_review_chat_comment](assets/aem6forms_review_chat_comment.png) s’affiche dans la barre Action. Cliquez sur l’icône de démarrage d’une révision ![aem6forms_review_chat_comment](assets/aem6forms_review_chat_comment.png).
1. Saisissez les informations suivantes :

   * Titre : (obligatoire). Il peut contenir des caractères alphanumériques, des tirets ou des traits de soulignement.
   * Description : (factultative). Description de la finalité ou du contenu de la révision.
   * Echéance : (facultative). Date de fin de la révision. Une fois l’échéance passée, la tâche est indiquée comme étant « En retard ».
   * Réviseurs : au moins un réviseur doit être indiqué. La saisie d’un nom de groupe ou d’utilisateur/utilisatrice répertorie tous les noms correspondants, à l’exception du groupe d’utilisateurs ou d’utilisatices du service. Sélectionnez un nom, puis cliquez sur Ajouter.

1. Cliquez sur Démarrer pour lancer une révision.

>[!NOTE]
>
>* L’administrateur ou l’administratrice peut accéder à tous les groupes associés aux utilisateurs et utilisatrices du formulaire.
>* Le groupe Utilisateurs et utilisatrices de service ne peut pas être sélectionné pour la révision.


### Actions survenant lorsqu’une révision est configurée {#actions-that-occur-when-a-review-is-set-up}

Cette section décrit ce qui se produit lorsqu’une révision est créée ou configurée.

1. Une tâche de révision est créée et affectée à la personne qui vient d’être ajoutée.
1. Tous les réviseurs se voient affecter une tâche de révision. La tâche apparaît dans leur section Notification. Le réviseur peut soit cliquer sur une notification, soit accéder à la boîte de réception pour afficher la tâche. Le réviseur peut cliquer pour ouvrir la tâche de révision, afficher le formulaire et commencer à ajouter des commentaires.

   ![Alerte de notification du réviseur](assets/review-notification-img.png)

   Alerte de notification du réviseur

1. La zone de commentaire est accessible aux personnes effectuant la révision du formulaire. Les autres utilisateurs et utilisatrices peuvent voir les commentaires, mais ne sont pas habilités à en rédiger.

## Gestion d’une révision {#managing-a-review}

>[!NOTE]
>
>Seules les révisions en cours peuvent être modifiées. La modification des révisions terminées est donc impossible.

1. Accédez à l’onglet Formulaires et sélectionnez un formulaire.

1. Si une révision de ressource est en cours et que vous en êtes l’initiateur, l’icône Gérer la révision ![aem6forms_review_chat_comment](assets/aem6forms_review_chat_comment.png) s’affiche dans la barre Action. Seule la personne initiant la révision peut gérer (mettre à jour/terminer) la révision.

   Cliquez sur l’icône Gérer la révision ![aem6forms_review_chat_comment](assets/aem6forms_review_chat_comment.png).

   Cette icône est désactivée pour les utilisateurs autres que l’initiateur.

1. Un écran affiche alors les informations suivantes :

   * **Titre** : ne peut pas être modifié.

   * **Description** : peut être modifiée.

   * **Échéance** : peut être modifiée. Vous pouvez modifier l’échéance selon n’importe quelle date et heure au-delà de la date et de l’heure actuelles.

   * **Nom du réviseur** : peut être modifié. Vous pouvez ajouter ou supprimer des réviseurs. Si une tâche est échue, vous ne pourrez ajouter des réviseurs qu’après avoir étendu l’échéance au-delà de la date actuelle.

1. Modifiez les champs nécessaires, puis cliquez sur Terminé.

   ![État Mis à jour de la révision dans le Gestionnaire des tâches](assets/manage-review-img.png)

   État Mis à jour de la révision dans le Gestionnaire des tâches

1. Pour mettre fin à la révision, cliquez sur Terminer la révision.

### Actions survenant lorsqu’une révision est modifiée {#actions-that-occur-when-a-review-is-modified}

Cette section décrit ce qui se produit lorsque vous modifiez ou mettez fin à une révision :

1. Si la description de la révision est modifiée, la tâche correspondante des réviseurs/réviseuses et de la personne ayant lancé la révision est mise à jour.
1. Si l’échéance de la révision est modifiée, la nouvelle date est appliquée à la tâche correspondante pour les réviseurs.

1. Si un réviseur est supprimé :

   ![Suppression d’un réviseur](assets/removeduser.png)

   Suppression d’un réviseur

   1. Si la tâche affectée est incomplète, elle est terminée.
   1. Le réviseur ou la réviseuse ne peut plus ajouter de commentaires dans le formulaire.

1. Si un réviseur est ajouté :

   ![Ajout d’un réviseur](assets/addedreviewer.png)

   Ajout d’un réviseur

   1. Une tâche de révision est créée et affectée au réviseur qui vient d’être ajouté.
   1. Le nouveau réviseur ou la nouvelle réviseuse peut ajouter des commentaires à propos du formulaire.

1. Lorsqu’une révision est terminée :

   1. **Réviseurs** : pour chaque réviseur, il est mis fin à la tâche incomplète associée à la révision. La tâche n’apparaît plus avec l’état « Pending » (En attente) dans la section Notifications du réviseur.
   1. **Initiateur** : la tâche affectée à l’initiateur de la révision est marquée comme étant terminée. La tâche est supprimée de la section de notification de l’initiateur de la révision.
   1. **Tous** : la révision s’affiche dans la section des révisions précédentes. Plus aucun commentaire ne peut être ajouté.
      ![Révision terminée](assets/review-complete-imgg.png).


