---
title: Gérer les listes d’adresses IP autorisées
description: Découvrez comment afficher, modifier, supprimer et vérifier l’état des Listes autorisées IP dans Cloud Manager.
exl-id: 6efabe53-3f45-47d4-ac1f-979cae0ab33e
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 40a76e39750d6dbeb03c43c8b68cddaf515a2614
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 19%

---

# Gérer les listes d’adresses IP autorisées {#manage-ip-allow-lists}

Découvrez comment afficher, modifier, supprimer et vérifier l’état des Listes autorisées IP dans Cloud Manager.

## Affichage et mise à jour des Listes autorisées IP {#update-ip-allow-lists}

Un utilisateur possédant le rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** peut suivre ces étapes pour afficher et mettre à jour une Liste autorisée IP.

**Pour afficher et mettre à jour des Listes autorisées IP :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.
1. Sur la page **Overview** , dans le menu de gauche, sous **Services**, cliquez sur l’icône ![Task list](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TaskList_18_N.svg) **Listes autorisées IP**.
1. Identifiez la ligne des Listes autorisées IP que vous souhaitez afficher ou mettre à jour.
1. Cliquez sur ![Icône supplémentaire](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) à droite de la ligne.
1. Dans le menu déroulant, cliquez sur **Afficher et mettre à jour**.
La boîte de dialogue **Afficher et mettre à jour la Liste autorisée IP** affiche le nom, les adresses IP (ou les plages) qui définissent la règle, ainsi que les environnements et services auxquels la règle est appliquée.
1. Modifiez le nom ou les adresses IP selon vos besoins.

   L’ajout ou la suppression d’une nouvelle plage d’adresses IP à une Liste autorisée d’adresses IP l’applique/annule automatiquement à tous les environnements/services correspondants auxquels elle a été précédemment appliquée.

   Les mises à jour ne peuvent pas être apportées à une Liste autorisée IP alors qu’une mise à jour préalable est en cours et n’est pas terminée.

1. Cliquez sur **Mettre à jour**.

## Vérification de l’état des Listes autorisées IP {#check-allow-list-status}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Sur la page **Overview** , dans le menu de gauche, sous **Services**, cliquez sur l’icône ![Task list](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TaskList_18_N.svg) **Listes autorisées IP**.

1. Dans la colonne **Status** de la table des Listes autorisées IP, placez le pointeur de la souris sur une Liste autorisée IP verte (en cours d’utilisation) pour voir un ou plusieurs services qui lui sont appliqués.

   Les valeurs d’état affichées dans le tableau ont les significations suivantes :

   | État de la Liste autorisée IP | Description |
   | --- | --- |
   | Appliqué | La Liste autorisée IP est correctement appliquée à un ou plusieurs environnements. |
   | Mise à jour en cours | Une mise à jour de la Liste autorisée IP est en cours, qui peut inclure une ou plusieurs applications ou la non-application de la liste. Chaque application ou annulation de l’application est répertoriée avec son propre statut, à savoir **Non démarrée**, **En cours**, **Terminée** ou **En échec**. |
   | Échec | Un ou plusieurs processus d’application ou de désapplication d’une mise à jour ont échoué.<br> ・ Chaque application et désapplication est répertoriée avec son état.<br> ・ l’état est **Failed** si une application/une application non-applicative échoue dans la mise à jour. Le statut reste sur **En échec** jusqu’à ce que tous les échecs soient effacés.<br> ・ Cliquez sur l’icône **Retry** en regard de l’état pour effacer l’échec.<br> ・ Vous ne pouvez pas mettre à jour ou supprimer une Liste autorisée IP avec l’état **Failed**. |
   | Suppression en cours | Une suppression d’une Liste autorisée IP est en cours.<br> ・ La suppression implique l’annulation de l’application de la liste à tous les services.<br> ・ Chaque désapplication est répertoriée avec son propre état : **Non démarré**, **En cours**, **Terminé** ou **Échec**.<br> ・ Une fois l’opération de suppression terminée, la Liste autorisée IP n’apparaît pas dans la table des Listes autorisées IP. En outre, la Liste autorisée IP n’est appliquée à aucun service du programme dans Cloud Manager. |
   | Échec | Une ou plusieurs désapplications ont échoué lors d’une opération de suppression.<br> ・ Chaque désapplication est répertoriée avec l’état **Complete** ou **Failed**.<br> ・ l’état devient **Échec de la suppression** si une désapplication échoue. L’état reste **Échec de la suppression** jusqu’à ce que tous les échecs soient effacés. À l’extrémité droite de la ligne du tableau, cliquez sur ![Icône More](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg), puis, dans le menu déroulant, cliquez sur **Supprimer** pour effacer tout échec.<br> ・ Vous ne pouvez pas mettre à jour une Liste autorisée IP lorsque l’état est **Failed**. |

## Suppression d’une Liste autorisée IP {#delete-allow-list}

Lorsque vous supprimez une Liste autorisée IP, elle annule automatiquement la liste de tous les services et la supprime du tableau Liste autorisée IP.

Un utilisateur possédant le rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** peut suivre ces étapes pour afficher et mettre à jour une Liste autorisée IP.

**Pour supprimer une Liste autorisée IP :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.
1. Sur la page **Overview** , dans le menu de gauche, sous **Services**, cliquez sur l’icône ![Task list](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TaskList_18_N.svg) **Listes autorisées IP**.
1. Identifiez la ligne de la Liste autorisée IP que vous souhaitez supprimer, puis cliquez sur ![Icône More](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) à droite de la ligne, puis sur **Supprimer**.
1. Dans la boîte de dialogue **Supprimer la Liste autorisée IP**, cliquez sur **Supprimer**.

## Configurations CDN préexistantes {#pre-existing-cdn}

Si vous disposez d’une configuration de réseau de diffusion de contenu (CDN) préexistante pour vos Listes autorisées IP, un message informatif s’affiche sur la page **Liste autorisée IP**. Le message vous invite à ajouter ces configurations au moyen de l’interface utilisateur afin qu’elles soient visibles et configurables dans Cloud Manager.

Le message disparaît une fois que toutes les configurations d’environnement préexistantes sont migrées à l’aide de l’interface utilisateur. Il peut s’écouler entre 1 et 2 jours ouvrés avant que le message ne disparaisse.

Pour plus d’informations, voir [Ajout d’une Liste autorisée IP](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md) .

Un message similaire est également fourni dans les pages **Certificats SSL** et **Environnements** pour les environnements qui possèdent des configurations CDN préexistantes pour les certificats SSL ou les noms de domaine personnalisés.
