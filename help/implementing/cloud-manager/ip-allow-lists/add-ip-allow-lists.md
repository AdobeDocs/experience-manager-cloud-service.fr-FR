---
title: Ajout d’une liste d’adresses IP autorisées
description: Découvrez comment ajouter votre propre liste d’adresses IP autorisées à l’aide de Cloud Manager.
exl-id: 769be71f-5c11-4f98-8906-7a5667a25aee
source-git-commit: 97a6a7865f696f4d61a1fb4e25619caac7b68b51
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 73%

---


# Ajouter une liste d’adresses IP autorisées {#add-ip-allow-list}

Découvrez comment ajouter votre propre liste d’adresses IP autorisées à l’aide de Cloud Manager.

Une personne dotée du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** peut suivre les étapes suivantes pour ajouter une liste d’adresses IP autorisées.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Dans la **Présentation** , accédez à la **Environnements** écran.

1. Dans la **Environnements** , accédez à la **LISTES AUTORISÉES IP** page.

   ![Option de liste d’adresses IP autorisées dans le panneau latéral](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create.png)

1. Cliquez sur **Ajout d’une Liste autorisée IP**.

   ![Boîte de dialogue Ajouter une liste d’adresses IP autorisées](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create02.png)

1. Dans le **Ajout d’une Liste autorisée IP** , saisissez le nom à utiliser pour référencer la liste autorisée dans la **Nom de la Liste autorisée IP** champ .

   * Ce nom n’est donné qu’à titre d’information et doit être descriptif pour vous aider à identifier la liste.

1. Saisissez un bloc IP ou IP CIDR dans le champ **Adresse IP/CIDR**.

   * Plusieurs blocs peuvent être séparés par une virgule ou un onglet.

1. Cliquez sur **Enregistrer**.

Après l’enregistrement, la nouvelle liste d’adresses IP autorisées s’affiche sur une ligne du tableau de la page **Listes d’adresses IP autorisées**.
