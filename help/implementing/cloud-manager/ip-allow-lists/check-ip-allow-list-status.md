---
title: Contrôle du statut de liste autorisée IP
description: Contrôle du statut de liste autorisée IP
exl-id: 5ddea04f-3720-4663-90a8-9399019bfcbe
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: ht
source-wordcount: '463'
ht-degree: 100%

---

# Contrôle du statut de liste autorisée IP {#check-allow-list-status}

Suivez les étapes ci-dessous pour déterminer le statut des mises à jour de votre Liste autorisée IP :

1. Cliquez sur l’icône Statut de la liste d’adresses IP autorisées dans le tableau de l’écran **Environnements** et sélectionnez **Listes autorisées d’adresses IP**.

1. Cloud Manager affiche l’un des statuts suivants, comme indiqué dans la section ci-dessous.

## Statut d’une liste autorisée IP {#status}

Voici les définitions de statut qui apparaîtront dans une liste autorisée IP :

* **Appliqué** : liste autorisée IP appliquée aux environnements.  Les environnements et le service sont visibles comme le montre l’image ci-dessous.

* **Mise à jour** : une mise à jour de la Liste autorisée IP qui peut inclure une ou plusieurs applications ou annulations est en cours. Chaque application et annulation est répertoriée avec Non démarré/En cours/Terminé ou Échec.

* **Échec** : échec d’un ou plusieurs processus d’application ou d’annulation dans une mise à jour. Chaque application et annulation est répertoriée avec Terminé ou Échec.
   * Le statut est sur Échec, même en cas d’échec d’une application/annulation dans la mise à jour.
   * Le statut reste sur Échec jusqu’à ce que tous les échecs soient effacés. L’utilisateur doit sélectionner l’icône Réessayer en face du statut pour effacer l’échec.
   * L’utilisateur ne peut pas mettre à jour ni supprimer la Liste autorisée IP tant que le statut est sur Échec.

* **Suppression** : la demande de suppression est en cours. Cela implique l’annulation de l’application de tous les services. Chaque annulation est répertoriée avec Non commencé/En cours/Terminé ou Échec.
Une fois l’opération de suppression terminée, la liste autorisée IP :
   * n’apparaît plus dans le tableau Liste autorisée IP ;
   * n’est plus appliquée sur aucun des services du programme dans Cloud Manager.

* **Échec de la suppression** : échec d’un ou plusieurs processus d’annulation d’application dans une opération de suppression. Chaque annulation sera répertoriée avec Terminé ou Échec.

   * Le statut est sur Échec de la suppression, même en cas d’échec d’une annulation de l’application.
   * Le statut reste sur Échec de la suppression jusqu’à ce que tous les échecs soient effacés. L’utilisateur doit sélectionner Supprimer dans le menu **...** à l’extrémité droite de la ligne du tableau pour effacer tout échec.
   * L’utilisateur ne sera pas autorisé à mettre à jour la Liste autorisée IP tant que le statut est sur Échec.

## Configurations de réseau de diffusion de contenu préexistantes pour les listes autorisées IP {#pre-existing-cdn}

Les clients disposant d’environnements qui incluent des configurations CDN préexistantes pour les listes autorisées d’adresses IP, des certificats SSL ou des noms de domaines personnalisés voient le message suivant dans les pages de détails **Liste autorisée d’adresses IP** et **Environnement**. Le message affiché dans l’interface utilisateur disparaît une fois que le client a effectué la migration complète de toutes les configurations d’environnement préexistantes via l’interface utilisateur et il peut s’écouler entre 1 et 2 jours ouvrés avant que le message ne disparaisse.

>[!NOTE]
>Pour afficher et gérer les configurations préexistantes, elles doivent être ajoutées via l’interface utilisateur. Pour plus d’informations, voir [Ajout d’une liste autorisée d’adresses IP](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md).

![](/help/implementing/cloud-manager/assets/ip-allow-list-message1.png)

![](/help/implementing/cloud-manager/assets/ip-allow-list-message2.png)
