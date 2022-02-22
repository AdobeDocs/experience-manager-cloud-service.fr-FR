---
title: 'Création de programmes de production '
description: Découvrez comment utiliser Cloud Manager pour créer votre propre programme de production afin d’héberger le trafic en direct.
exl-id: 4ccefb80-de77-4998-8a9d-e68d29772bb4
source-git-commit: cf6941759dfc1e50928009490c7c518a89ed093e
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 2%

---


# Création de programmes de production {#create-production-program}

Un programme de production est destiné à un utilisateur familiarisé avec AEM et Cloud Manager et prêt à commencer à écrire, créer et tester du code dans le but de le déployer pour héberger le trafic en direct.

En savoir plus sur les types de programme dans le document [Présentation des types de programme et de programme.](program-types.md)

## Tutorials vidéo {#video-tutorials}

Vous pouvez regarder ces deux tutoriels vidéo pour apprendre à créer un programme dans Cloud Manager ou [suivez nos instructions documentées.](#create)

>[!VIDEO](https://video.tv.adobe.com/v/334953)

>[!VIDEO](https://video.tv.adobe.com/v/334954)

## Création d’un programme de production {#create}

Pour créer un programme de production, procédez comme suit.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Cliquez sur **Ajout d’un programme** dans le coin supérieur droit de l’écran.

   ![Page d’entrée de Cloud Manager](assets/first_timelogin1.png)

1. Sélectionner **Configuration pour la production** dans l’assistant Créer un programme pour créer un programme de production. Vous pouvez accepter le nom du programme par défaut ou le modifier avant de sélectionner **Créer**.

   ![Créer l&#39;assistant de programme](assets/create-prod1.png)

1. Dans l&#39;onglet suivant, sélectionnez les solutions à inclure dans le programme.

   ![Solutions sélectionnées](assets/setup-prod-select.png)

1. Cliquez sur le chevron situé avant les noms des solutions pour afficher les modules complémentaires facultatifs, tels que la sélection de la variable **Commerce** option de module complémentaire sous **Sites**.

   ![Sélectionner les modules complémentaires](assets/setup-prod-commerce.png)

1. Lorsque vos solutions et modules complémentaires sont sélectionnés, cliquez sur **Créer**.

Votre programme est créé par Cloud Manager et s’affiche et peut être sélectionné sur la page d’entrée.

![Présentation de Cloud Manager](assets/navigate-cm.png)

## Accès à votre programme {#acessing}

1. Une fois que la carte du programme s’affiche sur la landing page, cliquez sur le bouton représentant des points de suspension pour afficher les options de menu disponibles.

   ![Présentation du programme](assets/program-overview.png)

1. Sélectionner **Aperçu du programme** pour accéder au **Présentation** page.

1. La carte principale d’appel à l’action de la page d’aperçu vous guide tout au long de la création d’un environnement, d’un pipeline hors production et, enfin, d’un pipeline de production.

   ![Présentation du programme](assets/set-up-prod5.png)

Si, à tout moment, vous devez passer à un autre programme ou revenir à la page d’aperçu pour créer un autre programme, cliquez sur le nom de votre programme dans le coin supérieur gauche de l’écran pour afficher la variable **Accédez à** .

![Accédez à ](assets/create-program-a1.png).

>[!NOTE]
>
>Contrairement à un [programme sandbox,](introduction-sandbox-programs.md#auto-creation) un programme de production nécessite que l’utilisateur possédant le rôle Cloud Manager approprié crée le projet et ajoute un environnement via l’interface utilisateur en libre-service.
