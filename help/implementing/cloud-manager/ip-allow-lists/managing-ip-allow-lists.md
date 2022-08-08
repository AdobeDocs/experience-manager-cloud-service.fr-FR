---
title: Gestion des listes d’adresses IP autorisées
description: Découvrez comment afficher, modifier, supprimer et vérifier l’état de vos listes d’adresses IP autorisées dans Cloud Manager.
exl-id: 6efabe53-3f45-47d4-ac1f-979cae0ab33e
source-git-commit: 3080427529bb65e27721e05069012b33579fdd73
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 100%

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
1. L’assistant **Afficher et mettre à jour** affiche le nom, les adresses (ou les plages) IP qui définissent la règle, ainsi que les environnements et le service auxquels la règle est appliquée.
1. Apportez des modifications au nom ou aux adresses IP et confirmez votre envoi.

L’ajout ou la suppression d’une nouvelle plage d’adresses IP à une liste d’adresses IP autorisées l’appliquera ou annulera automatiquement son application à tous les environnements et services correspondants auxquels elle a été précédemment appliquée.

Les mises à jour ne peuvent pas être apportées à une liste d’adresses IP autorisées alors qu’une mise à jour précédente est en cours et n’est pas terminée.

## Vérification de la liste d’adresses IP autorisées {#check-allow-list-status}

Pour vérifier le statut des listes d’adresses IP autorisées, procédez comme suit.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.

1. Cliquez sur l’icône **Statut** de la liste d’adresses IP autorisées dans le tableau de l’écran **Environnements** et sélectionnez la page **Listes d’adresses IP autorisées**.

1. Cloud Manager affiche le statut de la liste autorisée comme décrit [dans la section suivante.](#status)

### Statut d’une liste d’adresses IP autorisées {#status}

[Lors de la vérification du statut des listes d’adresses IP autorisées](#check-allow-list-status), ceux-ci peuvent avoir l’une des valeurs suivantes.

* **Appliquée** - La liste d’adresses IP autorisées est correctement appliquée à un ou plusieurs environnements.

* **Mise à jour en cours** - Une mise à jour de la liste d’adresses IP autorisées est en cours, qui peut inclure une ou plusieurs applications ou une annulation de l’application de la liste.

   * Chaque application ou annulation de l’application est répertoriée avec son propre statut, à savoir **Non démarrée**, **En cours**, **Terminée** ou **En échec**.

* **En échec** - Échec d’un ou de plusieurs processus d’application ou d’annulation dans une mise à jour.
   * Chaque application et annulation d’application est répertoriée avec son statut.
      * Le statut est défini comme **En échec** si une application ou une annulation de l’application dans la mise à jour échoue.
      * Le statut reste sur **En échec** jusqu’à ce que tous les échecs soient effacés.
         * Vous devez sélectionner l’icône **Réessayer** en face du statut pour effacer l’échec.
      * Vous ne pouvez pas mettre à jour ou supprimer une liste d’adresses IP autorisées avec un statut **En échec**.

* **Suppression en cours** - La suppression d’une liste d’adresses IP autorisées est en cours.
   * La suppression implique l’annulation de l’application de la liste de tous les services.
   * Chaque annulation de l’application est répertoriée avec son propre statut, à savoir **Non démarrée**, **En cours**, **Terminée** ou **En échec**.
   * Une fois l’opération de suppression terminée, la liste d’adresses IP autorisées :
      * n’apparaît plus dans le tableau Liste d’adresses IP autorisées ;
      * n’est plus appliquée sur aucun des services du programme dans Cloud Manager.

* **Suppression de l’échec** - Une ou plusieurs annulations d’application ont échoué lors d’une opération de suppression.

   * Chaque annulation d’application est répertoriée avec le statut **Terminée** ou **En échec**.
   * Le statut est **Échec de la suppression** en cas d’échec d’une annulation de l’application.
   * Le statut reste **Échec de la suppression** jusqu’à ce que tous les échecs soient effacés.
      * L’utilisateur doit sélectionner **Supprimer** dans le menu ... tout à droite de la ligne du tableau pour effacer tout échec.
   * Vous ne pouvez pas mettre à jour une liste d’adresses IP autorisées tant que son statut est **En échec**.

## Suppression d’une liste d’adresses IP autorisées {#delete-allow-list}

Un utilisateur doté du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** peut suivre les étapes suivantes pour afficher et mettre à jour une liste d’adresses IP autorisées.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.
1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.
1. Accédez à la page **Listes d’adresses IP autorisées** à partir de l’écran **Environnements**.
1. Identifiez la ligne de la liste d’adresses IP autorisées que vous souhaitez supprimer.
1. Sélectionnez le menu ... tout à droite de la ligne.
1. Cliquez sur **Supprimer**.
1. Confirmez votre envoi.

La suppression d’une liste d’adresses IP autorisées annule automatiquement son application de tous les services et la supprime de la table.

## Configurations de réseau CDN préexistantes {#pre-existing-cdn}

Si vous disposez d’une configuration de réseau CDN préexistante pour vos listes d’adresses IP autorisées, un message d’information s’affichera dans la page des **listes d’adresses IP autorisées**, vous encourageant à ajouter ces configurations via l’interface utilisateur afin qu’elles soient visibles et configurables dans Cloud Manager.

Le message disparaît une fois que toutes les configurations d’environnement préexistantes sont migrées à l’aide de l’interface utilisateur. Il peut s’écouler entre 1 et 2 jours ouvrés avant que le message ne disparaisse.

Consultez le document [Ajout d’une liste d’adresses IP autorisées](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md) pour plus d’informations.

Un message similaire est également fourni dans les pages **Certificats SSL** et **Environnements** pour les environnements qui possèdent des configurations CDN préexistantes pour les certificats SSL ou les noms de domaine personnalisés.
