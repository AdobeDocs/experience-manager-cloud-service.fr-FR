---
title: Contrôle du statut de liste autorisée IP
description: Contrôle du statut de liste autorisée IP
translation-type: tm+mt
source-git-commit: e6a8d69ea87ac56a51cde2f131c4accff1bea527
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 81%

---


# Contrôle du statut de liste autorisée IP {#check-allow-list-status}

Suivez les étapes ci-dessous pour déterminer le statut des mises à jour de votre Liste autorisée IP :

1. Cliquez sur l&#39;icône État de la Liste autorisée IP dans le tableau de l&#39;écran **Environnements** et sélectionnez **Listes autorisées IP**.

1. Cloud Manager affiche l’un des états suivants, comme indiqué dans la section ci-dessous.

## Statut d’une liste autorisée IP {#status}

Voici les définitions de statut qui apparaîtront dans une liste autorisée IP :

* **Appliqué** : liste autorisée IP appliquée aux environnements.  Les environnements et le service sont visibles comme le montre l’image ci-dessous.

* **Mise à jour** : une mise à jour de la Liste autorisée IP qui peut inclure une ou plusieurs applications ou annulations est en cours. Chaque application et annulation est répertoriée avec Non démarré/En cours/Terminé ou Échec.

* **Échec** : échec d’un ou plusieurs processus d’application ou d’annulation dans une mise à jour. Chaque application et annulation est répertoriée avec Terminé ou Échec.
   * L’état est Échec, même en cas d’échec d’une application/annulation dans la mise à jour.
   * L&#39;état restera Échec jusqu&#39;à ce que tous les échecs soient effacés. L’utilisateur doit sélectionner l’icône de nouvelle tentative en regard de l’état pour effacer l’échec.
   * L’utilisateur ne peut pas mettre à jour ni supprimer la Liste autorisée IP tant que l’état est Échec.

* **Suppression** : la demande de suppression est en cours. Cela implique l’annulation de l’application de tous les services. Chaque annulation est répertoriée avec Non commencé/En cours/Terminé ou Échec.
Une fois l’opération de suppression terminée, la Liste autorisée IP :
   * N’apparaît plus dans le tableau Liste autorisée IP.
   * Ne plus être appliqué à un service du programme dans Cloud Manager.

* **Échec de la suppression** : échec d’un ou plusieurs processus d’annulation d’application dans une opération de suppression. Chaque annulation sera répertoriée avec Terminé ou Échec.

   * L’état est Échec de la suppression, même en cas d’échec d’une annulation de l’application.
   * L’état reste Échec de la suppression jusqu’à ce que tous les échecs soient effacés. L’utilisateur doit sélectionner Supprimer dans le menu **...** à l’extrémité droite de la ligne du tableau pour effacer tout échec.
   * L’utilisateur ne sera pas autorisé à mettre à jour la Liste autorisée IP tant que l’état est Échec.

