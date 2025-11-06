---
title: Gérer les listes d’adresses IP autorisées
description: Découvrez comment afficher, modifier, supprimer et vérifier le statut des Listes autorisées IP dans Cloud Manager.
exl-id: 6efabe53-3f45-47d4-ac1f-979cae0ab33e
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 19%

---

# Gérer les listes d’adresses IP autorisées {#manage-ip-allow-lists}

Découvrez comment afficher, modifier, supprimer et vérifier le statut des Listes autorisées IP dans Cloud Manager.

## Affichage et mise à jour des Listes autorisées IP {#update-ip-allow-lists}

Un utilisateur doté du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** peut suivre les étapes suivantes pour afficher et mettre à jour une Liste autorisée IP.

**Pour afficher et mettre à jour des Listes autorisées IP, procédez comme suit**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.
1. Sur la page **Aperçu**, dans le menu de gauche, sous **Services**, cliquez sur ![Icône de liste de tâches](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TaskList_18_N.svg) **Listes autorisées IP**.
1. Identifiez la ligne des Listes autorisées IP que vous souhaitez afficher ou mettre à jour.
1. Cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) à l’extrémité droite de la ligne.
1. Dans le menu déroulant, cliquez sur **Afficher et mettre à jour**.
La boîte de dialogue **Afficher et mettre à jour la Liste autorisée IP** affiche le nom, les adresses IP (ou les plages d’adresses IP) qui définissent la règle, ainsi que les environnements et les services auxquels la règle est appliquée.
1. Modifiez le nom ou les adresses IP, selon vos besoins.

   L’ajout ou la suppression d’une nouvelle plage d’adresses IP à une Liste autorisée IP l’applique/annule automatiquement son application à tous les environnements/services correspondants auxquels elle a été précédemment appliquée.

   Les mises à jour ne peuvent pas être apportées à une Liste autorisée IP lorsqu’une mise à jour précédente est en cours et n’est pas terminée.

1. Cliquez sur **Mettre à jour**.

## Vérification de l’état des Listes autorisées IP {#check-allow-list-status}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Sur la page **Aperçu**, dans le menu de gauche, sous **Services**, cliquez sur ![Icône de liste de tâches](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TaskList_18_N.svg) **Listes autorisées IP**.

1. Dans la colonne **Statut** du tableau Listes autorisées IP , placez le pointeur de la souris sur une Liste autorisée IP verte (en cours d’utilisation) pour afficher un ou plusieurs services qui lui sont appliqués.

   Les valeurs de statut affichées dans le tableau ont la signification suivante :

   | Statut de la Liste autorisée IP | Description |
   | --- | --- |
   | Appliqué | La Liste autorisée IP a été correctement appliquée à un ou plusieurs environnements. |
   | Mise à jour en cours | Une mise à jour de la Liste autorisée IP est en cours, qui peut inclure une ou plusieurs applications ou une annulation de l’application de la liste. Chaque application ou annulation de l’application est répertoriée avec son propre statut, à savoir **Non démarrée**, **En cours**, **Terminée** ou **En échec**. |
   | Échec | Échec d&#39;un ou de plusieurs processus d&#39;application ou d&#39;annulation d&#39;une mise à jour.<br>· Chaque application et annulation d’application est répertoriée avec son statut.<br>· Le statut est **Échec** si une application ou une annulation de l’application dans la mise à jour échoue. Le statut reste sur **En échec** jusqu’à ce que tous les échecs soient effacés.<br>· Cliquez sur l’icône **Réessayer** en regard du statut pour effacer l’échec.<br>· Vous ne pouvez pas mettre à jour ou supprimer une Liste autorisée IP avec un statut **Échec**. |
   | Suppression en cours | Une suppression de Liste autorisée IP est en cours.<br>· La suppression implique l’annulation de l’application de la liste de tous les services.<br>· Chaque annulation d’application est répertoriée avec son propre statut, à savoir **Non démarrée** **En cours**, **Terminée** ou **En échec**.<br>· Une fois l’opération de suppression terminée, la Liste autorisée IP n’apparaît pas dans le tableau Liste autorisée IP . En outre, la Liste autorisée IP n’est appliquée à aucun service du programme dans Cloud Manager. |
   | Échec de la suppression | Une ou plusieurs annulations d’application ont échoué lors d’une opération de suppression.<br>· Chaque annulation d’application est répertoriée avec le statut **Terminée** ou **En échec**.<br>· Le statut devient **Échec de la suppression** si une annulation de l’application échoue. Le statut reste **Échec de la suppression** jusqu’à ce que tous les échecs soient effacés. À l’extrémité droite de la ligne du tableau, cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) puis, dans le menu déroulant, cliquez sur **Supprimer** pour effacer tout échec.<br>· Vous ne pouvez pas mettre à jour une Liste autorisée IP tant que son statut est **Échec**. |

## Suppression d’une Liste autorisée IP {#delete-allow-list}

Lorsque vous supprimez une Liste autorisée IP, la liste est automatiquement annulée de tous les services et supprimée du tableau des Listes autorisées IP.

Un utilisateur doté du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** peut suivre les étapes suivantes pour afficher et mettre à jour une Liste autorisée IP.

**Pour supprimer une Liste autorisée IP, procédez comme suit**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.
1. Sur la page **Aperçu**, dans le menu de gauche, sous **Services**, cliquez sur ![Icône de liste de tâches](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TaskList_18_N.svg) **Listes autorisées IP**.
1. Identifiez la ligne de la Liste autorisée IP que vous souhaitez supprimer, puis cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) à l’extrémité droite de la ligne, puis cliquez sur **Supprimer**.
1. Dans la boîte de dialogue **Supprimer la Liste autorisée IP**, cliquez sur **Supprimer**.

## Configurations de réseau CDN préexistantes {#pre-existing-cdn}

Si vous disposez d’une configuration préexistante de réseau CDN (réseau de diffusion de contenu) pour vos Listes autorisées IP, un message d’information s’affiche sur la page **Liste autorisée IP**. Le message vous invite à ajouter ces configurations au moyen de l’interface utilisateur afin qu’elles soient visibles et configurables dans Cloud Manager.

Le message disparaît une fois que toutes les configurations d’environnement préexistantes sont migrées à l’aide de l’interface utilisateur. Il peut s’écouler entre 1 et 2 jours ouvrés avant que le message ne disparaisse.

Voir [Ajouter une Liste autorisée IP](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md) pour plus d’informations.

Un message similaire est également fourni dans les pages **Certificats SSL** et **Environnements** pour les environnements qui possèdent des configurations CDN préexistantes pour les certificats SSL ou les noms de domaine personnalisés.
