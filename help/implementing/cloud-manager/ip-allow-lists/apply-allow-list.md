---
title: Application et annulation de l’application de listes d’adresses IP autorisées
description: Découvrez comment appliquer et annuler l’application de listes d’adresses IP autorisées aux environnements.
exl-id: 7158496c-b0c4-4228-a306-71dc51003c57
source-git-commit: 90250c13c5074422e24186baf78f84c56c9e3c4f
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 81%

---


# Application et annulation de l’application de listes d’adresses IP autorisées {#apply-allow-list}

Lors de l’application d’une liste d’adresses IP autorisées, toutes les plages d’adresses IP comprises dans la définition de la liste sont associées à un service de création ou de publication dans un environnement. L’annulation de l’application d’une liste représente l’inverse de ce processus.

## Application de listes d’adresses IP autorisées {#applying}

Un utilisateur doté du rôle **Propriétaire de l’entreprise** ou **Responsable du déploiement** peut suivre les étapes suivantes pour appliquer une liste d’adresses IP autorisées.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur le **[Mes programmes](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#my-programs)** sélectionnez le programme.
1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.
1. Accédez à la page d’information sur chaque environnement à l’aide de l’écran **Environnements** et accédez au tableau **Liste d’adresses IP autorisées**.
1. Utilisez les champs de saisie en haut du tableau pour sélectionner la liste autorisée IP et le service de création ou de publication auquel vous souhaitez l’appliquer.
   * La liste d’adresses IP autorisées doit exister dans Cloud Manager afin de pouvoir être appliquée.
1. Cliquez sur **Appliquer** et confirmez votre soumission.

## Annulation de l’application de listes autorisées {#un-applying}

Une personne dotée du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** peut suivre les étapes suivantes pour ajouter une liste d’adresses IP autorisées.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.
1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.
1. Accédez à la page d’information sur chaque environnement à l’aide de l’écran **Environnements** et accédez au tableau **Liste d’adresses IP autorisées**.
1. Identifiez la ligne de la liste autorisée IP que vous souhaitez annuler.
1. Sélectionnez le bouton représentant des points de suspension à l’extrémité droite de la ligne.
1. Sélectionnez l’option **Annuler l’application** et confirmez votre envoi.
