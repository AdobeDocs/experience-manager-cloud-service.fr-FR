---
title: Gérer les listes d’adresses IP autorisées
description: Découvrez comment afficher, modifier, supprimer et vérifier l’état des Listes autorisées IP dans Cloud Manager.
exl-id: 6efabe53-3f45-47d4-ac1f-979cae0ab33e
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f4c6331491bb08e81964476ad58065c1ee022967
workflow-type: tm+mt
source-wordcount: '812'
ht-degree: 44%

---

# Gérer les listes d’adresses IP autorisées {#manage-ip-allow-lists}

Découvrez comment afficher, modifier, supprimer et vérifier l’état des Listes autorisées IP dans Cloud Manager.

## Affichage et mise à jour des Listes autorisées IP {#update-ip-allow-lists}

Un utilisateur possédant le rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** peut suivre ces étapes pour afficher et mettre à jour une Liste autorisée IP.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.
1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.
1. Accédez à l’écran **Environnements** à partir de la page **Vue d’ensemble**.
1. Accédez à la page **Listes d’adresses IP autorisées** à partir de l’écran **Environnements**.
1. Identifiez la ligne des Listes autorisées IP que vous souhaitez afficher ou mettre à jour.
1. Cliquez sur le bouton représentant des points de suspension à droite de la ligne.
1. Sélectionnez l’option **Afficher et mettre à jour**.
1. L’assistant **Afficher et mettre à jour** affiche le nom, les adresses IP (ou les plages) qui définissent la règle, ainsi que les environnements et services auxquels la règle est appliquée.
1. Modifiez le nom ou les adresses IP, suivant vos besoins, et confirmez votre envoi.

L’ajout ou la suppression d’une nouvelle plage d’adresses IP à une Liste autorisée d’adresses IP l’applique/annule automatiquement à tous les environnements/services correspondants auxquels elle a été précédemment appliquée.

Les mises à jour ne peuvent pas être apportées à une Liste autorisée IP alors qu’une mise à jour préalable est en cours et n’est pas terminée.

## Vérification de l’état des Listes autorisées IP {#check-allow-list-status}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à l’écran **Environnements** à partir de la page **Vue d’ensemble**.

1. Cliquez sur l’icône **Status** de la Liste autorisée IP dans la table de l’écran **Environments** (Environnements) et sélectionnez la page **Listes autorisées IP**.

1. Cloud Manager affiche l’état de la Liste autorisée comme décrit [dans la section suivante](#status).

### Statut d’une liste d’adresses IP autorisées {#status}

[Lors de la vérification de l’état des Listes autorisées IP](#check-allow-list-status), elles peuvent avoir l’une des valeurs suivantes.

* **Appliqué** - La Liste autorisée IP est correctement appliquée à un ou plusieurs environnements.

* **Mise à jour** - Une mise à jour de la Liste autorisée IP est en cours, qui peut inclure une ou plusieurs applications ou une désapplication de la liste.

   * Chaque application ou annulation de l’application est répertoriée avec son propre statut, à savoir **Non démarrée**, **En cours**, **Terminée** ou **En échec**.

* **En échec** : échec d’un ou de plusieurs processus d’application ou d’annulation dans une mise à jour.
   * Chaque application et annulation d’application est répertoriée avec son statut.
      * Le statut est défini comme **En échec** si une application ou une annulation de l’application dans la mise à jour échoue.
      * Le statut reste sur **En échec** jusqu’à ce que tous les échecs soient effacés.
         * Sélectionnez l’icône **Réessayer** en regard du statut afin que vous puissiez effacer l’échec.
      * Vous ne pouvez pas mettre à jour ou supprimer une Liste autorisée IP avec l’état **Failed** .

* **Suppression** - Une suppression d’une Liste autorisée IP est en cours.
   * La suppression implique l’annulation de l’application de la liste de tous les services.
   * Chaque annulation de l’application est répertoriée avec son propre statut, à savoir **Non démarrée**, **En cours**, **Terminée** ou **En échec**.
   * Une fois l’opération de suppression terminée :
      * La Liste autorisée IP n’apparaît pas dans le tableau Liste autorisée IP.
      * La Liste autorisée IP n’est appliquée à aucun service du programme dans Cloud Manager.

* **Échec de la suppression** : une ou plusieurs annulations d’application ont échoué lors d’une opération de suppression.

   * Chaque annulation d’application est répertoriée avec le statut **Terminée** ou **En échec**.
   * Le statut devient **Échec de la suppression** si une annulation d’application échoue.
   * L’état reste **Échec de la suppression** jusqu’à ce que tous les échecs soient effacés. À l’extrémité droite de la ligne du tableau, cliquez sur le menu représentant des points de suspension, puis cliquez sur **Supprimer** pour effacer tout échec.
   * Vous ne pouvez pas mettre à jour une Liste autorisée IP lorsque l’état est **Failed**.

## Suppression d’une Liste autorisée IP {#delete-allow-list}

Un utilisateur possédant le rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** peut suivre ces étapes pour afficher et mettre à jour une Liste autorisée IP.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.
1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.
1. Accédez à la page **Listes d’adresses IP autorisées** à partir de l’écran **Environnements**.
1. Identifiez la ligne de la Liste autorisée IP que vous souhaitez supprimer.
1. Sélectionnez le menu ... tout à droite de la ligne.
1. Cliquez sur **Supprimer**.
1. Confirmez votre envoi.

La suppression d’une Liste autorisée IP la annule automatiquement de tous les services et la supprime du tableau.

## Configurations CDN préexistantes {#pre-existing-cdn}

Si vous disposez d’une configuration de réseau de diffusion de contenu (CDN) préexistante pour vos Listes autorisées IP, un message informatif s’affiche sur la page **Liste autorisée IP**. Le message vous invite à ajouter ces configurations au moyen de l’interface utilisateur afin qu’elles soient visibles et configurables dans Cloud Manager.

Le message disparaît une fois que toutes les configurations d’environnement préexistantes sont migrées à l’aide de l’interface utilisateur. Il peut s’écouler entre 1 et 2 jours ouvrés avant que le message ne disparaisse.

Pour plus d’informations, voir [Ajout d’une Liste autorisée IP](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md) .

Un message similaire est également fourni dans les pages **Certificats SSL** et **Environnements** pour les environnements qui possèdent des configurations CDN préexistantes pour les certificats SSL ou les noms de domaine personnalisés.
