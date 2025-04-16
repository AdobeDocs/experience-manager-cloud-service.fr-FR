---
title: Ajout de Listes autorisées IP
description: Découvrez comment ajouter vos propres Listes autorisées IP à l’aide de Cloud Manager.
exl-id: 769be71f-5c11-4f98-8906-7a5667a25aee
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 328ae6d1866a7089fb291d4872d27dc5fa1d4caa
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 14%

---


# Ajouter une liste d’adresses IP autorisées {#add-ip-allow-list}

Découvrez comment ajouter votre propre Liste autorisée IP à l’aide de Cloud Manager.

Un utilisateur doté du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** peut suivre les étapes suivantes pour ajouter une Liste autorisée IP.

{{add-cm-allowlist-frontend-pipeline}}

**Pour ajouter une Liste autorisée IP, procédez comme suit**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.

1. Sur la page **Aperçu du programme**, dans le menu de gauche (il se peut que vous deviez cliquer sur ![Afficher l’icône du menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) dans le coin supérieur gauche pour afficher le menu), cliquez sur ![Icône de la liste des tâches](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TaskList_18_N.svg) **Listes autorisées IP**.

   ![Option Listes autorisées IP dans le menu de gauche](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create.png)

1. Dans le coin supérieur droit de la page Listes autorisées IP, cliquez sur **Ajouter une Liste autorisée IP**.

   ![Boîte de dialogue Ajouter une liste d’adresses IP autorisées](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create02.png)

1. Dans la boîte de dialogue **Ajouter une Liste autorisée IP**, dans le champ **Nom de la Liste autorisée IP**, saisissez le nom que vous souhaitez utiliser pour référencer la Liste autorisée IP. Ce nom est fourni uniquement à titre d’information. Assurez-vous qu’elle est suffisamment descriptive pour vous aider à identifier la liste.

1. Dans le champ **Adresse IP / CIDR** , saisissez un bloc IP ou CIDR IP. Séparez plusieurs blocs par une virgule ou un onglet.

1. Cliquez sur **Enregistrer**.

Après l’enregistrement, la nouvelle Liste autorisée IP s’affiche sur une ligne du tableau de la page **Listes autorisées IP**.

