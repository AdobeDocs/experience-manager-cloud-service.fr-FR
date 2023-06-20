---
title: Application et annulation de l’application de listes d’adresses IP autorisées
description: Découvrez comment appliquer et annuler des listes autorisées IP aux environnements.
exl-id: 7158496c-b0c4-4228-a306-71dc51003c57
source-git-commit: 5311ba7f001201fc94c73fa52bc7033716c1ba78
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 55%

---


# Application et annulation de l’application de listes d’adresses IP autorisées {#apply-allow-list}

Lors de l’application d’une liste autorisée IP, toutes les plages d’adresses IP incluses dans la définition de la liste sont associées à un service de création ou de publication au sein d’un environnement. L’annulation de l’application d’une liste constitue l’inverse de ce processus.

## Application de listes d’adresses IP autorisées {#applying}

Un utilisateur doté du rôle **Propriétaire de l’entreprise** ou **Responsable du déploiement** peut suivre les étapes suivantes pour appliquer une liste d’adresses IP autorisées.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.
1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.
1. Accédez à la page d’information sur chaque environnement à l’aide de l’écran **Environnements** et accédez au tableau **Liste d’adresses IP autorisées**.
1. Utilisez les champs de saisie en haut du tableau pour sélectionner la liste autorisée IP et le service de création ou de publication auquel vous souhaitez appliquer la .
   * La Liste autorisée IP doit exister dans Cloud Manager pour l’appliquer.
1. Cliquez sur **Appliquer** et confirmez votre soumission.

## Annulation de l’application de listes autorisées {#un-applying}

Un utilisateur de la variable **Propriétaire de l’entreprise** ou **Responsable de déploiement** peut suivre les étapes suivantes pour annuler l’application d’une liste autorisée IP.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.
1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.
1. Accédez à la page d’information sur chaque environnement à l’aide de l’écran **Environnements** et accédez au tableau **Liste d’adresses IP autorisées**.
1. Identifiez la ligne de la liste autorisée IP que vous souhaitez annuler.
1. Sélectionnez le bouton représentant des points de suspension à l’extrémité droite de la ligne.
1. Sélectionnez l’option **Annuler l’application** et confirmez votre envoi.
