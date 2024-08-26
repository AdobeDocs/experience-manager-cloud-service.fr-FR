---
title: Ajout de Listes autorisées IP
description: Découvrez comment ajouter vos propres Listes autorisées IP à l’aide de Cloud Manager.
exl-id: 769be71f-5c11-4f98-8906-7a5667a25aee
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 1415d07235641262814e81362c806572bcf582ba
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 12%

---


# Ajouter une liste d’adresses IP autorisées {#add-ip-allow-list}

Découvrez comment ajouter votre propre Liste autorisée IP à l’aide de Cloud Manager.

Un utilisateur possédant le rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** peut suivre ces étapes pour ajouter une Liste autorisée IP.

{{add-cm-allowlist-frontend-pipeline}}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.

1. Sur la page **Aperçu du programme** , à l’aide du panneau latéral sur le côté gauche (vous devrez peut-être cliquer sur l’icône de hamburger dans le coin supérieur gauche pour afficher le panneau), cliquez sur **Listes autorisées IP**.

   ![Option de Listes autorisées IP dans le panneau latéral](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create.png)

1. Dans le coin supérieur droit de la page Listes autorisées IP, cliquez sur **Ajouter une Liste autorisée IP**.

   ![Boîte de dialogue Ajouter une liste d’adresses IP autorisées](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create02.png)

1. Dans la boîte de dialogue **Ajouter une Liste autorisée IP**, dans le champ **Nom de Liste autorisée IP**, saisissez un nom que vous souhaitez utiliser pour référencer la Liste autorisée IP. Ce nom est informatif uniquement. Assurez-vous qu’il est suffisamment descriptif pour vous aider à identifier la liste.

1. Dans le champ **IP address / CIDR** , saisissez un bloc IP ou IP CIDR. Séparez plusieurs blocs par une virgule ou un onglet.

1. Cliquez sur **Enregistrer**.

Après l’enregistrement, la Liste autorisée IP nouvellement créée apparaît en ligne dans le tableau de la page **Listes autorisées IP**.

## Ajout de la Liste autorisée IP Cloud Manager {#add-cm-allowlist}

Le pipeline front-end requiert que la Liste autorisée IP Cloud Manager suivante soit ajoutée au préalable.

**Liste autorisée IP Cloud Manager**

`52.254.106.192/28,20.186.185.181,52.254.106.240/28,52.254.107.128/28,52.254.105.192/28,52.254.106.176/28,20.186.185.227,52.254.106.144/28,52.254.107.64/28,20.186.185.239,20.22.83.112,52.254.107.80/28,52.254.107.144/28,52.254.106.224/28,20.14.241.153,52.254.107.0/28,52.254.107.32/28,52.254.106.208/28,40.70.154.136/29,52.254.106.160/28,52.254.107.16/28,52.254.106.0/28,4.152.211.251`

Pour éviter toute interruption de l’exécution du pipeline front-end, assurez-vous que cette Liste autorisée IP Cloud Manager est ajoutée, puis appliquée au service Auteur de l’environnement *avant* d’activer le pipeline.

**Pour ajouter la Liste autorisée IP Cloud Manager :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.

1. Sur la page **Aperçu du programme** , à l’aide du panneau latéral sur le côté gauche (vous devrez peut-être cliquer sur l’icône de hamburger dans le coin supérieur gauche pour afficher le panneau), cliquez sur **Listes autorisées IP**.

1. Dans le coin supérieur droit de la page Listes autorisées IP, cliquez sur **Ajouter une Liste autorisée IP**.

1. Dans la boîte de dialogue **Ajouter une Liste autorisée IP**, dans le champ **Nom de Liste autorisée IP**, saisissez *`Cloud Manager`*.

1. Copiez le bloc des adresses de Liste autorisée IP de Cloud Manager ci-dessus. Chaque adresse est déjà séparée par une virgule.

1. Dans la boîte de dialogue **Ajouter une Liste autorisée IP** , collez le bloc dans le champ **Adresse IP / CIDR** .

1. Placez le curseur juste après la première virgule dans la liste des adresses et appuyez sur **Entrée**.

1. Cliquez sur **Enregistrer**.

Maintenant, [appliquez la Liste autorisée IP Cloud Manager](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) à vos environnements de programme.



