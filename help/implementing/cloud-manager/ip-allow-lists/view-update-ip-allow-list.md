---
title: Affichage et mise à jour - Listes autorisées IP dans Cloud Manager
description: Affichage et mise à jour - Listes autorisées IP dans Cloud Manager
translation-type: tm+mt
source-git-commit: 7fdfa626147a72f3d7fb98b89a19a871fc7a13ca
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 83%

---


# Affichage et mise à jour d&#39;une Liste autorisée IP {#view-update}

Vous pouvez afficher et mettre à jour des listes autorisées IP dans les cas suivants :

* Pour afficher et mettre à jour le menu pour afficher simplement les détails d’une ou de plusieurs listes autorisées IP.
* Pour modifier l’un ou plusieurs des éléments suivants :
   * Plages IP dans la définition du nom de la règle
   * Nom convivial de la règle de liste autorisée IP

## Mise à jour de la liste autorisée d’adresses IP {#update-ip-allow-lists}


Un utilisateur ayant le rôle Propriétaire de l’entreprise ou Responsable du déploiement doit être connecté pour pouvoir mettre à jour une Liste autorisée IP.

>[!NOTE]
>L’assistant d’affichage et de mise à jour affiche le nom, les adresses IP ou les plages d’adresses IP qui définissent la règle. En outre, il affiche les environnements et le service auxquels s’applique la règle.

Respectez les étapes ci-dessous pour mettre à jour une liste autorisée IP :

1. Accédez à la page **Listes autorisées IP** à partir de l’écran **Environnements**.
1. Identifiez la ligne où est répertoriée la règle de liste autorisée d’adresses IP que vous souhaitez afficher/mettre à jour.
1. Sélectionnez le menu **...** tout à fait à droite de la ligne.
1. Sélectionnez l&#39;option **Vue et mise à jour**.
1. Apportez des modifications au nom ou aux adresses IP et confirmez votre envoi.

## Considérations importantes lors de l’ajout, de la mise à jour ou de la suppression de listes autorisées IP {#considerations}

* L’ajout d’une nouvelle plage d’adresses IP à la liste autorisée d’adresses IP entraîne son application automatique à tous les environnements-services correspondants.
* La suppression d’une plage d’adresses IP de la liste autorisée d’adresses IP annule automatiquement son application de tous les services environnements correspondants.
* Les mises à jour ne peuvent pas être apportées à une Liste autorisée d’adresses IP alors qu’une mise à jour précédente est en cours et n’est pas terminée.
* Les mises à jour ne peuvent pas être apportées à une liste autorisée d’adresses IP en cas d’erreur provenant d’une mise à jour antérieure. Toute erreur doit être corrigée en tentant de relancer la mise à jour.
Consultez [Vérification du statut de la Liste autorisée IP](/help/implementing/cloud-manager/ip-allow-lists/check-ip-allow-list-status.md) pour en savoir plus.