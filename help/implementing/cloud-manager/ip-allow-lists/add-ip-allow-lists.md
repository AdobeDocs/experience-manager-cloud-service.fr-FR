---
title: Ajout d’une liste d’adresses IP autorisées
description: Découvrez comment ajouter votre propre liste autorisée IP à l’aide de Cloud Manager.
exl-id: 769be71f-5c11-4f98-8906-7a5667a25aee
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 40%

---


# Ajout d’une liste d’adresses IP autorisées {#add-ip-allow-list}

Découvrez comment ajouter votre propre liste autorisée IP à l’aide de Cloud Manager.

Un utilisateur de la variable **Propriétaire de l’entreprise** ou **Responsable de déploiement** pour ajouter une liste autorisée IP, vous pouvez suivre les étapes suivantes.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.

1. Accédez à la page **Liste d’adresses IP autorisées** à partir de l’écran **Environnements**.

   ![Option de liste d’adresses IP autorisées dans le panneau latéral](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create.png)

1. Cliquez sur **Ajout d’une Liste autorisée IP** pour ouvrir le **Ajout d’une Liste autorisée IP** de la boîte de dialogue

   ![Boîte de dialogue Ajouter une Liste autorisée IP](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create02.png)

1. Saisissez un nom que vous souhaitez utiliser pour référencer la liste autorisée dans le champ **Nom de la Liste autorisée IP** champ .

   * Ce nom est fourni à titre d’information uniquement et doit être descriptif pour vous aider à identifier la liste.

1. Saisissez un bloc IP ou IP CIDR dans le champ **Adresse IP/CIDR**.

   * Plusieurs blocs peuvent être séparés par une virgule ou un onglet.

1. Cliquez sur **Enregistrer** pour confirmer l’envoi.

Après l’enregistrement, la liste autorisée IP nouvellement créée apparaît sous la forme d’une ligne dans le tableau de la variable **LISTES AUTORISÉES IP** page.
