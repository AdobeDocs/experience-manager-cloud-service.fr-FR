---
title: 'Création de programmes Sandbox '
description: Découvrez comment utiliser Cloud Manager pour créer votre propre programme d’environnement de test à des fins de formation, de démonstration, de point de vente ou à d’autres fins hors production.
exl-id: 10011392-3059-4bb0-88db-0af1d390742e
source-git-commit: cf6941759dfc1e50928009490c7c518a89ed093e
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 1%

---

# Création de programmes Sandbox {#create-sandbox-program}

Un programme d’environnement de test est généralement créé à des fins de formation, d’exécution de démonstrations, d’activation, de points ciblés ou de documentation et n’est pas destiné à transporter du trafic en direct.

En savoir plus sur les types de programme dans le document [Présentation des types de programme et de programme.](program-types.md)

## Création d’un programme Sandbox {#create}

Pour créer un programme Sandbox, procédez comme suit.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Dans la page d’entrée de Cloud Manager, cliquez sur **Ajout d’un programme** dans le coin supérieur droit de l’écran.

   ![Page d’entrée Cloud Manager](assets/first_timelogin1.png)

1. Dans l’assistant de création de programme, sélectionnez **Configuration d’un environnement de test**, indiquez un nom de programme, puis cliquez sur **Créer**.

   ![Création de type de programme](assets/create-sandbox.png)

Une nouvelle carte de programme sandbox s’affiche sur la page d’entrée avec un indicateur d’état au fur et à mesure que le processus de configuration progresse.

![Création d’un environnement de test à partir de la page d’aperçu](assets/program-create-setupdemo2.png)

## Accès à votre environnement de test {#access}

Vous pouvez afficher les détails de la configuration de votre environnement de test et accéder à l’environnement (une fois disponible) en consultant la page d’aperçu du programme.

1. Dans la page d’entrée de Cloud Manager, cliquez sur le bouton représentant des points de suspension du programme que vous venez de créer.

   ![Accéder à la présentation du programme](assets/program-overview-sandbox.png)

1. Une fois l’étape de création du projet terminée, vous pouvez accéder au **Accès aux informations sur le référentiel** pour pouvoir utiliser votre référentiel git.

   ![Configuration du programme](assets/create-program4.png)

   >[!TIP]
   >
   >Pour en savoir plus sur l’accès à votre référentiel git et sa gestion, reportez-vous au document . [Accès à Git.](/help/implementing/cloud-manager/managing-code/accessing-repos.md)

1. Une fois l’environnement de développement créé, vous pouvez utiliser la variable **Accès aux AEM** lien pour vous connecter à AEM.

   ![Accès à AEM lien](assets/create-program-5.png)

1. Une fois le pipeline hors production qui se déploie vers le développement terminé, l’assistant vous guide à accéder à l’environnement de développement AEM ou à déployer le code vers l’environnement de développement.

   ![Déploiement d’un environnement de test](assets/create-program-setup-deploy.png)

Si, à tout moment, vous devez passer à un autre programme ou revenir à la page d’aperçu pour créer un autre programme, cliquez sur le nom de votre programme dans le coin supérieur gauche de l’écran pour afficher la variable **Accédez à** .

![Accédez à ](assets/create-program-a1.png).
