---
title: Application et annulation de l’application de Listes autorisées IP
description: Découvrez comment appliquer et annuler l’application de Listes autorisées IP aux environnements Cloud Manager.
exl-id: 7158496c-b0c4-4228-a306-71dc51003c57
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 593b8c704c5b016bb55ae6a25420b577044b4126
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 12%

---


# Application et annulation de l’application de Listes autorisées IP {#apply-allow-list}

Lors de l’application de Listes autorisées IP, toutes les plages d’adresses IP incluses dans la définition de la liste sont associées à un service de création ou de publication dans un environnement. L’annulation de l’application d’une liste représente l’inverse de ce processus.

{{add-cm-allowlist-frontend-pipeline}}
{{ip-allow-lists-ue}}

## Application de Listes autorisées IP {#applying}

Un utilisateur doté du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** peut suivre les étapes suivantes pour appliquer une Liste autorisée IP.

**Pour appliquer des Listes autorisées IP, procédez comme suit**

1. Connectez-vous à Cloud Manager sur [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/).
1. Sélectionnez l’organisation appropriée.
1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.
1. Dans la page **Vue d’ensemble**, accédez à l’écran **Environnements**.
1. Sur l’écran **Environnements**, accédez à la page de détails de l’environnement spécifique.
1. Accédez au tableau **Liste autorisée IP**.
1. Utilisez les champs de saisie en haut du tableau pour sélectionner la Liste autorisée IP et le service de création, de publication ou de prévisualisation auquel vous souhaitez l’appliquer.
La Liste autorisée IP doit déjà exister dans Cloud Manager pour pouvoir être appliquée. Voir [ Ajout de Listes autorisées IP ](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md).
1. Cliquez sur ![Ajouter une icône](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg) **Appliquer** et confirmez votre envoi.

## Annuler l’application des Listes autorisées IP {#un-applying}

Un utilisateur doté du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** peut suivre les étapes suivantes pour annuler l’application d’une Liste autorisée IP.

**Pour annuler l’application de Listes autorisées IP, procédez comme suit**

1. Connectez-vous à Cloud Manager sur [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/).
1. Sélectionnez l’organisation appropriée.
1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.
1. Sur la page **Aperçu**, accédez à la page **Environnements**.
1. Accédez à la page des détails de l’environnement spécifique.
1. Dans l’onglet Général , faites défiler l’écran jusqu’au tableau **Liste autorisée IP** .
1. Identifiez la ligne de la Liste autorisée IP dont vous souhaitez annuler l’application.
1. Sur le côté droit de la ligne identifiée, cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).
1. Cliquez sur **Annuler l’application**.
1. Dans la boîte de dialogue **Annuler l’application de la Liste autorisée IP**, cliquez sur **Annuler l’application**.
