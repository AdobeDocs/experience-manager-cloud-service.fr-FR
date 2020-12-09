---
title: Vérification du statut de la Liste autorisée IP
description: Vérification du statut de la Liste autorisée IP
translation-type: tm+mt
source-git-commit: b9b2591ce25040b108484984851308bc80eee958
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---


# Vérification du statut de la Liste autorisée IP {#check-allow-list-status}

Suivez les étapes ci-dessous pour déterminer l’état des mises à jour de votre Liste autorisée IP :

1. Cliquez sur l’icône Etat de la Liste autorisée IP dans le tableau de la page Environnements > Liste autorisée IP.

1. Cloud Manager affiche l’un des états suivants, comme mentionné dans la section ci-dessous.

## État d&#39;une Liste autorisée IP {#status}

Voici les définitions de statut qui apparaîtront dans une Liste autorisée IP :

* **Appliqué** : LISTE AUTORISÉE IP appliquée aux environnements.  Les environnements et le service sont visibles comme le montre l&#39;image ci-dessous.

* **Mise à jour** : Une mise à jour de la Liste autorisée IP, qui peut inclure une ou plusieurs demandes ou demandes annulées, est en cours de traitement. Chaque application et annulation de la demande sont répertoriées avec Non démarré/En cours/Terminé ou Échec.

* **Échec** : Échec d&#39;un ou plusieurs processus d&#39;application ou d&#39;annulation d&#39;application dans une mise à jour. Chaque application et annulation de la demande sont répertoriées avec l&#39;option Terminé ou Échec.

   >[!NOTE]
   > * L&#39;état sera Échec, même si une application/annulation de l&#39;application échoue dans la mise à jour.
   >* L&#39;état restera Échec jusqu&#39;à ce que tous les échecs soient effacés.L&#39;utilisateur doit sélectionner l&#39;icône Réessayer en regard de l&#39;état pour effacer l&#39;échec.
   >* L&#39;utilisateur ne pourra pas mettre à jour ou supprimer la Liste autorisée IP tant que l&#39;état est Échec.


* **Suppression** : La demande de suppression est en cours. Cela implique la non-application de tous les services. Chaque Annulation sera répertoriée avec Non commencée/En cours/Terminée ou Échec.

   >[!NOTE]
   >Une fois l&#39;opération de suppression terminée, la Liste autorisée IP :
   >* N’apparaît plus dans le tableau Liste autorisée IP >* Ne s’applique plus à aucun service du programme dans Cloud Manager.


* **Échec** de la suppression : Échec d&#39;un ou plusieurs processus d&#39;annulation d&#39;application dans une opération de suppression. Chaque Annulation sera répertoriée avec Terminé ou Echec.

   >[!NOTE]
   >* L’état de la suppression sera Échec, même si l’annulation de l’application échoue.
   >* L&#39;état restera Échec de la suppression jusqu&#39;à ce que tous les échecs soient effacés. L&#39;utilisateur doit sélectionner Supprimer dans le **...le menu** situé à l&#39;extrémité droite de la ligne du tableau pour effacer tout échec.
   >* L&#39;utilisateur ne sera pas autorisé à mettre à jour la Liste autorisée IP tant que l&#39;état est Échec.


