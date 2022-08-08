---
title: Ajout d’une liste d’adresses IP autorisées
description: Découvrez comment ajouter votre propre liste d’adresses IP autorisées à l’aide de Cloud Manager.
exl-id: 769be71f-5c11-4f98-8906-7a5667a25aee
source-git-commit: 378ff582435f1ab3db431a0c9c3e80a4661cccc4
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 100%

---


# Ajout d’une liste d’adresses IP autorisées {#add-ip-allow-list}

Découvrez comment ajouter votre propre liste d’adresses IP autorisées à l’aide de Cloud Manager.

Un utilisateur doté du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** peut suivre les étapes suivantes pour ajouter une liste d’adresses IP autorisées.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.

1. Accédez à la page **Liste d’adresses IP autorisées** à partir de l’écran **Environnements**.

   ![Option de liste d’adresses IP autorisées dans le panneau latéral](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create.png)

1. Cliquez sur **Ajouter une liste d’adresses IP autorisées** pour ouvrir la boîte de dialogue **Ajouter la liste d’adresses IP autorisées**.

   ![Boîte de dialogue Ajouter une liste d’adresses IP autorisées](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create02.png)

1. Entrez le nom que vous souhaitez utiliser comme référence pour la liste autorisée dans le champ **Nom de la liste d’adresses IP autorisées**.

   * Il n’est donné qu’à titre d’information et doit être descriptif pour vous aider à identifier la liste.

1. Saisissez un bloc IP ou IP CIDR dans le champ **Adresse IP/CIDR**.

   * Plusieurs blocs peuvent être séparés par une virgule ou un onglet.

1. Cliquez sur **Enregistrer** pour confirmer l’envoi.

Lors de l’enregistrement, la nouvelle liste d’adresses IP autorisées s’affiche sur une ligne du tableau de la page **Listes d’adresses IP autorisées**.
