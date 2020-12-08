---
title: Affichage et mise à jour - Listes autorisées IP dans le Gestionnaire de commandes
description: Affichage et mise à jour - Listes autorisées IP dans le Gestionnaire de commandes
translation-type: tm+mt
source-git-commit: b353de1a58eb8c31de7289677a589cf192ebc0b9
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---


# Affichage et mise à jour des Listes autorisées IP {#view-update}

Vous pouvez vue et mettre à jour des Listes autorisées IP dans les cas suivants :

* Dans le menu Vue et mise à jour pour simplement vue les détails d’une ou de plusieurs Listes autorisées IP.
* Pour modifier un ou plusieurs des éléments suivants :
   * Plages IP dans la définition du nom de la règle
   * Nom convivial de la règle de Liste autorisée IP

## Mettre à jour la Liste autorisée IP {#update-ip-allow-lists}


Un utilisateur du rôle Propriétaire de l&#39;entreprise ou Deployment Manager doit être connecté pour pouvoir mettre à jour une Liste autorisée IP.

>[!NOTE]
>L&#39;Assistant Vue et mise à jour affiche le nom, les adresses IP ou les plages d&#39;adresses IP qui définissent la règle. En outre, il affiche les environnements et le service sur lesquels la règle est appliquée.

Suivez les étapes ci-dessous pour mettre à jour une Liste autorisée IP :

1. Accédez à la page Liste autorisée IP à partir de l’écran Environnements.
1. Identifiez la ligne où est répertoriée la règle de Liste autorisée IP que vous souhaitez vue/mettre à jour.
1. Sélectionnez **...** à l&#39;extrémité droite de la ligne.
1. Sélectionnez l’option Vue et mise à jour.
1. Apportez des modifications au nom ou à l’adresse IP et confirmez votre envoi.

## Considérations importantes lors de l’Ajoute, de la mise à jour ou de la suppression de Listes autorisées IP {#considerations}

* Si vous Ajoutez une nouvelle plage d&#39;adresses IP à la Liste autorisée IP, elle sera automatiquement appliquée à tous les environnements-services correspondants.
* La suppression d&#39;une plage d&#39;adresses IP de la Liste autorisée d&#39;adresses IP annule automatiquement son application de tous les services environnements correspondants.
* Les mises à jour ne peuvent pas être apportées à une Liste autorisée IP alors qu’une mise à jour précédente est en cours et n’est pas terminée.
* Les mises à jour ne peuvent pas être apportées à une Liste autorisée IP en cas d’erreur provenant d’une mise à jour antérieure. Toute erreur doit être corrigée en tentant de relancer la mise à jour.
Pour en savoir plus, consultez la section Vérification du statut de la Liste autorisée IP.