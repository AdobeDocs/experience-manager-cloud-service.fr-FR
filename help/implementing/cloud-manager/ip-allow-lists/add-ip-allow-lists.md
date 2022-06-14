---
title: Ajout de Listes autorisées IP
description: Découvrez comment ajouter votre propre liste autorisée IP à l’aide de Cloud Manager.
exl-id: 769be71f-5c11-4f98-8906-7a5667a25aee
source-git-commit: 378ff582435f1ab3db431a0c9c3e80a4661cccc4
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 19%

---


# Ajout d’une liste d’adresses IP autorisées {#add-ip-allow-list}

Découvrez comment ajouter votre propre liste autorisée IP à l’aide de Cloud Manager.

Un utilisateur de la variable **Propriétaire de l’entreprise** ou **Responsable de déploiement** peut suivre ces étapes pour ajouter une liste autorisée IP.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.

1. Accédez à la page **liste d’adresses IP autorisées** à partir de l’écran **Environnements**.

   ![Option listes autorisées IP dans le panneau latéral](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create.png)

1. Cliquez sur **Ajout d’une Liste autorisée IP** pour ouvrir le **Ajout d’une Liste autorisée IP** boîte de dialogue.

   ![Boîte de dialogue Ajouter une Liste autorisée IP](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create02.png)

1. Saisissez un nom à utiliser pour référencer la liste autorisée dans le champ **Nom de la Liste autorisée IP** champ .

   * Il s’agit uniquement d’informations et doit être descriptif pour vous aider à identifier la liste.

1. Saisissez un bloc IP ou IP CIDR dans la zone **Adresse IP/CIDR** champ .

   * Plusieurs blocs peuvent être séparés par une virgule ou un onglet.

1. Cliquez sur **Enregistrer** pour confirmer votre envoi.

Lors de l’enregistrement, la liste autorisée IP nouvellement créée s’affiche en ligne dans le tableau de la variable **LISTES AUTORISÉES IP** page.
