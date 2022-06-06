---
title: 'Création de programmes de production '
description: Découvrez comment utiliser Cloud Manager pour créer votre propre programme de production afin d’héberger le trafic en direct.
exl-id: 4ccefb80-de77-4998-8a9d-e68d29772bb4
source-git-commit: cf6941759dfc1e50928009490c7c518a89ed093e
workflow-type: ht
source-wordcount: '362'
ht-degree: 100%

---


# Création de programmes de production {#create-production-program}

Un programme de production est destiné à un utilisateur qui connaît AEM et Cloud Manager et qui est prêt à se lancer dans l’écriture, la compilation et le test de code en vue de le déployer pour héberger du trafic en direct.

Découvrez-en plus sur les types de programme dans le document [Présentation des programmes et des types de programme.](program-types.md)

## Tutoriels vidéo {#video-tutorials}

Vous pouvez regarder ces deux tutoriels vidéo pour apprendre à créer un programme dans Cloud Manager ou [suivre nos instructions documentées.](#create)

>[!VIDEO](https://video.tv.adobe.com/v/334953)

>[!VIDEO](https://video.tv.adobe.com/v/334954)

## Création d’un programme de production {#create}

Pour créer un programme de production, procédez comme suit.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Cliquez sur **Ajouter un programme** dans le coin supérieur droit de l’écran.

   ![Page de destination de Cloud Manager](assets/first_timelogin1.png)

1. Sélectionnez **Configuration pour la production** dans l’assistant de création de programme pour créer un programme de production. Vous pouvez accepter le nom de programme par défaut ou le modifier avant de sélectionner **Créer**.

   ![Assistant de création de programme](assets/create-prod1.png)

1. Dans l’onglet suivant, sélectionnez les solutions à inclure dans le programme.

   ![Solutions sélectionnées](assets/setup-prod-select.png)

1. Cliquez sur le chevron situé avant les noms des solutions pour afficher les modules complémentaires facultatifs, tels que la sélection de l’option de module complémentaire **Commerce** sous **Sites**.

   ![Sélectionner les modules complémentaires](assets/setup-prod-commerce.png)

1. Lorsque vos solutions et modules complémentaires sont sélectionnés, cliquez sur **Créer**.

Votre programme est créé par Cloud Manager, s’affiche et peut être sélectionné dans la page de destination.

![Aperçu de Cloud Manager](assets/navigate-cm.png)

## Accès à votre programme {#acessing}

1. Une fois que la carte du programme s’affiche sur la page de destination, sélectionnez le bouton représentant des points de suspension pour afficher les options de menu disponibles.

   ![Aperçu du programme](assets/program-overview.png)

1. Sélectionnez **Cloud Manager** pour accéder à la page **Aperçu** de Cloud Manager.

1. La carte principale d’appel à l’action de la page d’aperçu vous guide tout au long de la création d’un environnement, d’un pipeline hors production et, enfin, d’un pipeline de production.

   ![Aperçu du programme](assets/set-up-prod5.png)

Si, à tout moment, vous devez passer à un autre programme ou revenir à la page d’aperçu pour créer un autre programme, cliquez sur le nom de votre programme dans le coin supérieur gauche de l’écran pour afficher l’option **Accéder à**.

![Accéder à ](assets/create-program-a1.png)

>[!NOTE]
>
>Contrairement à un [programme Sandbox,](introduction-sandbox-programs.md#auto-creation) un programme de production nécessite que l’utilisateur possédant le rôle Cloud Manager approprié crée le projet et ajoute un environnement via l’interface utilisateur en libre-service.
