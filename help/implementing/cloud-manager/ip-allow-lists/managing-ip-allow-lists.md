---
title: Gestion des listes d’adresses IP autorisées
description: Découvrez comment afficher, modifier, supprimer et vérifier l’état de vos listes d’adresses IP autorisées dans Cloud Manager.
exl-id: 6efabe53-3f45-47d4-ac1f-979cae0ab33e
source-git-commit: 5311ba7f001201fc94c73fa52bc7033716c1ba78
workflow-type: tm+mt
source-wordcount: '802'
ht-degree: 57%

---

# Gestion des listes d’adresses IP autorisées {#manage-ip-allow-lists}

Découvrez comment afficher, modifier, supprimer et vérifier l’état de vos listes d’adresses IP autorisées dans Cloud Manager.

## Affichage et mise à jour des listes d’adresses IP autorisées {#update-ip-allow-lists}

Un utilisateur doté du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** peut suivre les étapes suivantes pour afficher et mettre à jour une liste d’adresses IP autorisées.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.
1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.
1. Accédez à la page **Listes d’adresses IP autorisées** à partir de l’écran **Environnements**.
1. Identifiez la ligne des listes d’adresses IP autorisées que vous souhaitez afficher ou mettre à jour.
1. Cliquez sur le bouton représentant des points de suspension à droite de la ligne.
1. Sélectionnez l’option **Afficher et mettre à jour**.
1. Le **Afficher et mettre à jour** L’assistant affiche le nom, les adresses IP (ou les plages) qui définissent la règle, ainsi que les environnements et le service auxquels la règle est appliquée.
1. Modifiez le nom ou les adresses IP, suivant vos besoins, et confirmez votre envoi.

L’ajout ou la suppression d’une nouvelle plage d’adresses IP à une liste d’adresses IP autorisées l’appliquera ou annulera automatiquement son application à tous les environnements et services correspondants auxquels elle a été précédemment appliquée.

Les mises à jour ne peuvent pas être apportées à une liste autorisée IP alors qu’une mise à jour préalable est en cours et n’est pas terminée.

## Vérification de la liste d’adresses IP autorisées {#check-allow-list-status}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.

1. Cliquez sur l’icône **Statut** de la liste d’adresses IP autorisées dans le tableau de l’écran **Environnements** et sélectionnez la page **Listes d’adresses IP autorisées**.

1. Cloud Manager affiche l’état de la liste autorisée, comme décrit [dans la section suivante.](#status)

### Statut d’une liste d’adresses IP autorisées {#status}

[Lors de la vérification du statut des listes d’adresses IP autorisées](#check-allow-list-status), ceux-ci peuvent avoir l’une des valeurs suivantes.

* **Appliquée** - La liste d’adresses IP autorisées est correctement appliquée à un ou plusieurs environnements.

* **Mise à jour** - Une mise à jour de la liste autorisée IP est en cours, qui peut inclure une ou plusieurs applications ou la non-application de la liste.

   * Chaque application ou annulation de l’application est répertoriée avec son propre statut, à savoir **Non démarrée**, **En cours**, **Terminée** ou **En échec**.

* **En échec** - Un ou plusieurs processus d’application ou de désapplication d’une mise à jour ont échoué.
   * Chaque application et désapplication sont répertoriées avec son état.
      * Le statut est défini comme **En échec** si une application ou une annulation de l’application dans la mise à jour échoue.
      * L’état reste tel que **En échec** tant que tous les échecs ne sont pas effacés.
         * Sélectionnez la **Réessayer** en regard de l’état afin que vous puissiez effacer l’échec.
      * Vous ne pouvez pas mettre à jour ou supprimer une liste autorisée IP avec une **En échec** statut.

* **Suppression en cours** - La suppression d’une liste d’adresses IP autorisées est en cours.
   * La suppression implique la désapplication de la liste de tous les services.
   * Chaque désapplication est répertoriée avec son propre état : **Non démarré**, **En cours**, **Terminer** ou **En échec**.
   * Une fois l’opération de suppression terminée, la liste d’adresses IP autorisées :
      * n’apparaît plus dans le tableau Liste d’adresses IP autorisées ;
      * n’est plus appliquée sur aucun des services du programme dans Cloud Manager.

* **Échec** - Une ou plusieurs désapplications ont échoué lors d’une opération de suppression.

   * Chaque désapplication est répertoriée avec le statut **Terminer** ou **En échec**.
   * L’état devient **Échec** si une désapplication échoue.
   * L’état reste tel que **Échec** tant que tous les échecs ne sont pas effacés.
      * Sélectionner **Supprimer** dans le menu points de suspension situé à l’extrémité droite de la ligne du tableau, afin que vous puissiez supprimer tout échec.
   * Vous ne pouvez pas mettre à jour une liste autorisée IP lorsque l’état est **En échec**.

## Suppression d’une liste d’adresses IP autorisées {#delete-allow-list}

Un utilisateur doté du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** peut suivre les étapes suivantes pour afficher et mettre à jour une liste d’adresses IP autorisées.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.
1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.
1. Accédez à la page **Listes d’adresses IP autorisées** à partir de l’écran **Environnements**.
1. Identifiez la ligne de la liste d’adresses IP autorisées que vous souhaitez supprimer.
1. Sélectionnez le menu ... tout à droite de la ligne.
1. Cliquez sur **Supprimer**.
1. Confirmez votre envoi.

La suppression d’une liste autorisée IP la annule automatiquement de tous les services et la supprime du tableau.

## Configurations de réseau CDN préexistantes {#pre-existing-cdn}

Si vous disposez d’une configuration de réseau de diffusion de contenu préexistante pour vos listes autorisées IP, un message informatif s’affiche sur la page **LISTE AUTORISÉE IP** page. Le message vous invite à ajouter ces configurations au moyen de l’interface utilisateur afin qu’elles soient visibles et configurables dans Cloud Manager.

Le message disparaît une fois que toutes les configurations d’environnement préexistantes sont migrées à l’aide de l’interface utilisateur. Il peut s’écouler entre 1 et 2 jours ouvrés avant que le message ne disparaisse.

Voir [Ajout d’une liste autorisée IP](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md) pour plus d’informations.

Un message similaire est également fourni dans les pages **Certificats SSL** et **Environnements** pour les environnements qui possèdent des configurations CDN préexistantes pour les certificats SSL ou les noms de domaine personnalisés.
