---
title: Ajout de Listes autorisées IP
description: Découvrez comment ajouter vos propres Listes autorisées IP à l’aide de Cloud Manager.
exl-id: 769be71f-5c11-4f98-8906-7a5667a25aee
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 40a76e39750d6dbeb03c43c8b68cddaf515a2614
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 14%

---


# Ajouter une liste d’adresses IP autorisées {#add-ip-allow-list}

Découvrez comment ajouter votre propre Liste autorisée IP à l’aide de Cloud Manager.

Un utilisateur possédant le rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** peut suivre ces étapes pour ajouter une Liste autorisée IP.

{{add-cm-allowlist-frontend-pipeline}}

{{ip-allow-lists-ue}}

**Pour ajouter une Liste autorisée IP :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.

1. Sur la page **Aperçu du programme**, à l’aide du menu de gauche (vous devrez peut-être cliquer sur l’icône ![Afficher le menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) dans le coin supérieur gauche pour afficher le menu), cliquez sur ![Icône Liste des tâches](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TaskList_18_N.svg) **Listes autorisées IP**.

   ![Option de Listes autorisées IP dans le menu de gauche](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create.png)

1. Dans le coin supérieur droit de la page Listes autorisées IP, cliquez sur **Ajouter une Liste autorisée IP**.

   ![Boîte de dialogue Ajouter une liste d’adresses IP autorisées](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create02.png)

1. Dans la boîte de dialogue **Ajouter une Liste autorisée IP**, dans le champ **Nom de Liste autorisée IP**, saisissez un nom que vous souhaitez utiliser pour référencer la Liste autorisée IP. Ce nom est informatif uniquement. Assurez-vous qu’il est suffisamment descriptif pour vous aider à identifier la liste.

1. Dans le champ **IP address / CIDR** , saisissez un bloc IP ou IP CIDR. Séparez plusieurs blocs par une virgule ou un onglet.

1. Cliquez sur **Enregistrer**.

Après l’enregistrement, la Liste autorisée IP nouvellement créée apparaît en ligne dans le tableau de la page **Listes autorisées IP**.

