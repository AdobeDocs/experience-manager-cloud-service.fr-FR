---
title: Ajout de Listes autorisées IP
description: Découvrez comment ajouter vos propres Listes autorisées IP à l’aide de Cloud Manager.
exl-id: 769be71f-5c11-4f98-8906-7a5667a25aee
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: 8422eeb1538c7d3fc64bf4769cb577c894c85769
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 6%

---


# Ajouter une liste d’adresses IP autorisées {#add-ip-allow-list}

Configurez votre Liste autorisée IP à l’aide de Cloud Manager.

Pour ajouter une Liste autorisée IP, un utilisateur doté du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** peut suivre les étapes suivantes.

{{add-cm-allowlist-frontend-pipeline}}
{{ip-allow-lists-ue}}

**Pour ajouter une Liste autorisée IP, procédez comme suit**

{{sign-in-to-cloud-manager}}

1. Dans la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez un programme.

1. Sur la page **Aperçu du programme**, dans le menu de navigation de gauche (si nécessaire, cliquez sur ![Icône Afficher le menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) dans le coin supérieur gauche pour afficher le menu), cliquez sur ![Icône de la liste des tâches](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TaskList_18_N.svg) **Listes autorisées IP**.

   ![Option Listes autorisées IP dans le menu de gauche](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create.png)

1. Dans le coin supérieur droit de la page Listes autorisées IP, cliquez sur **Ajouter une Liste autorisée IP**.

   ![Boîte de dialogue Ajouter une liste d’adresses IP autorisées](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create02.png)

1. Dans la boîte de dialogue **Ajouter une Liste autorisée IP**, dans le champ **Nom de la Liste autorisée IP**, saisissez le nom que vous souhaitez utiliser pour référencer la Liste autorisée IP. Ce nom est fourni uniquement à titre d’information. Assurez-vous qu’elle est suffisamment descriptive pour vous aider à identifier la liste.

1. Dans le champ **Adresse IP / CIDR** , saisissez jusqu’à 50 adresses IP ou blocs CIDR. Vous pouvez les ajouter de l’une des façons suivantes :

   * Une par une : saisissez une adresse, puis appuyez sur `Enter`. Répétez l’opération pour chaque adresse supplémentaire.
   * Multiple simultanément : saisissez les adresses séparées par des virgules (,) ou des tabulations, puis appuyez sur `Enter` pour traiter chaque adresse.

1. Après avoir saisi la dernière adresse IP ou le dernier bloc CIDR, appuyez sur `Enter` pour confirmer l’entrée. L’entrée n’est validée qu’après avoir appuyé sur `Enter` et le bouton **Enregistrer** devient actif.

1. Cliquez sur **Enregistrer**.

Après l’enregistrement, la nouvelle Liste autorisée IP s’affiche sur une ligne du tableau de page **Listes autorisées IP**.

