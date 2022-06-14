---
title: Gestion des listes autorisées d’adresses IP
description: Découvrez comment afficher, modifier, supprimer et vérifier l’état de vos listes autorisées IP dans Cloud Manager.
exl-id: 6efabe53-3f45-47d4-ac1f-979cae0ab33e
source-git-commit: 3080427529bb65e27721e05069012b33579fdd73
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 20%

---

# Gestion des listes autorisées d’adresses IP {#manage-ip-allow-lists}

Découvrez comment afficher, modifier, supprimer et vérifier l’état de vos listes autorisées IP dans Cloud Manager.

## Affichage et mise à jour des listes autorisées IP {#update-ip-allow-lists}

Un utilisateur de la variable **Propriétaire de l’entreprise** ou **Responsable de déploiement** peut suivre les étapes suivantes pour afficher et mettre à jour une liste autorisée IP.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.
1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.
1. Accédez à la page **Listes autorisées IP** à partir de l’écran **Environnements**.
1. Identifiez la ligne des listes autorisées IP que vous souhaitez afficher ou mettre à jour.
1. Cliquez sur le bouton représentant des points de suspension à droite de la ligne.
1. Sélectionnez l’option **Afficher et mettre à jour**.
1. Le **Afficher et mettre à jour** l’assistant affiche le nom, les adresses IP (ou les plages) qui définissent la règle, ainsi que les environnements et le service auxquels la règle est appliquée.
1. Apportez des modifications au nom ou aux adresses IP et confirmez votre envoi.

L’ajout ou la suppression d’une nouvelle plage d’adresses IP à une liste autorisée d’adresses IP l’appliquera/annule automatiquement à tous les environnements/services correspondants auxquels elle a été précédemment appliquée.

Les mises à jour ne peuvent pas être effectuées sur une liste autorisée IP alors qu’une mise à jour préalable est en cours et n’est pas terminée.

## Vérification du statut des Listes autorisées IP {#check-allow-list-status}

Pour vérifier l’état des listes autorisées IP, procédez comme suit.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.

1. Cliquez sur le bouton **État** de la liste autorisée IP du tableau sur la **Environnements** et sélectionnez la variable **LISTES AUTORISÉES IP** page.

1. Cloud Manager affiche l’état de la liste autorisée comme décrit [dans la section suivante.](#status)

### Statut d’une liste autorisée IP {#status}

[Lors de la vérification de l’état des listes autorisées IP,](#check-allow-list-status) ils peuvent avoir l’une des valeurs suivantes.

* **Appliqué** - La liste autorisée IP est correctement appliquée à un ou plusieurs environnements.

* **Mise à jour** - Une mise à jour de la liste autorisée IP est en cours, qui peut inclure une ou plusieurs applications ou une annulation de l’application de la liste.

   * Chaque application/annulation de l’application est répertoriée avec son propre état de **Non démarré**, **En cours**, **Terminer** ou **En échec**.

* **En échec** - Un ou plusieurs processus d’application ou d’annulation d’application d’une mise à jour ont échoué.
   * Chaque application et sa désapplication sont répertoriées avec son état.
      * L’état est **En échec** si une application/une annulation de l’application dans la mise à jour échoue.
      * Le statut reste le suivant : **En échec** tant que tous les échecs ne sont pas effacés.
         * Vous devez sélectionner la variable **Réessayer** en regard de l’état pour effacer l’échec.
      * Vous ne pouvez pas mettre à jour ou supprimer une liste autorisée IP avec une **En échec** statut.

* **Suppression** - Une suppression d’une liste autorisée IP est en cours.
   * La suppression implique la désapplication de la liste de tous les services.
   * Chaque désapplication est répertoriée avec son propre état de **Non démarré**, **En cours**, **Terminer** ou **En échec**.
   * Une fois l’opération de suppression terminée, la liste autorisée IP :
      * N’apparaît plus dans le tableau liste autorisée IP.
      * n’est plus appliquée sur aucun des services du programme dans Cloud Manager.

* **Échec** - Une ou plusieurs désapplications ont échoué lors d’une opération de suppression.

   * Chaque désapplication est répertoriée avec le statut **Terminer** ou **En échec**.
   * L’état est **Échec** si une application d’annulation échoue.
   * Le statut reste le suivant : **Échec** tant que tous les échecs ne sont pas effacés.
      * Vous devez sélectionner **Supprimer** dans le menu points de suspension situé à l’extrémité droite de la ligne du tableau pour effacer tout échec.
   * Vous ne pouvez pas mettre à jour une liste autorisée IP tant que l’état est **En échec**.

## Suppression d’une liste autorisée d’adresses IP {#delete-allow-list}

Un utilisateur de la variable **Propriétaire de l’entreprise** ou **Responsable de déploiement** peut suivre les étapes suivantes pour afficher et mettre à jour une liste autorisée IP.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.
1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.
1. Accédez à la page **Listes autorisées IP** à partir de l’écran **Environnements**.
1. Identifiez la ligne de la liste autorisée IP que vous souhaitez supprimer.
1. Sélectionnez le menu représentant des points de suspension à l’extrémité droite de la ligne.
1. Cliquez sur **Supprimer**.
1. Confirmez votre envoi.

La suppression d’une liste autorisée IP la annule automatiquement de tous les services et la supprime de la table.

## Configurations de réseau CDN préexistantes {#pre-existing-cdn}

Si vous disposez d’une configuration de réseau de diffusion de contenu préexistante pour vos listes autorisées IP, un message d’information s’affichera sur le **LISTE AUTORISÉE IP** , vous encourageant à ajouter ces configurations via l’interface utilisateur afin qu’elles soient visibles et configurables dans Cloud Manager.

Le message disparaît une fois que toutes les configurations d’environnement préexistantes sont migrées à l’aide de l’interface utilisateur. Il peut s’écouler entre 1 et 2 jours ouvrés avant que le message ne disparaisse.

Reportez-vous au document [Ajout d’une liste autorisée IP](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md) pour plus d’informations.

Un message similaire est également fourni dans la variable **Certificats SSL** et le **Environnements** des pages pour les environnements qui possèdent des configurations CDN préexistantes pour les certificats SSL ou les noms de domaine personnalisés.
