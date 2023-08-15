---
title: Création de programmes Sandbox
description: Découvrez comment utiliser Cloud Manager pour créer votre propre programme Sandbox à des fins de formation, de démonstration, de point de vente ou à d’autres fins hors production.
exl-id: 10011392-3059-4bb0-88db-0af1d390742e
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 51%

---

# Création de programmes Sandbox {#create-sandbox-program}

Un programme Sandbox est généralement créé à des fins de formation, pour l’exécution de démonstrations, d’activation, de points de vente ou de documentation, et n’est pas destiné à transporter du trafic en direct.

Découvrez-en plus sur les types de programme dans le document [Présentation des programmes et des types de programme.](program-types.md)

## Création d’un programme Sandbox {#create}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Dans la page d’entrée de Cloud Manager, près du coin supérieur droit de l’écran, cliquez sur **Ajout d’un programme**.

   ![Page de destination de Cloud Manager](assets/cloud-manager-my-programs.png)

1. Dans l’assistant de création de programme, sélectionnez **Configuration d’un environnement de test** et indiquez un nom de programme.

   ![Création d’un type de programme](assets/create-sandbox.png)

1. Vous pouvez éventuellement ajouter une image au programme en faisant glisser un fichier image et en le déposant sur la cible **Ajouter une image de programme** ou en cliquant dessus pour sélectionner une image dans l’explorateur de fichiers. Cliquez ou appuyez sur **Continuer**.

   * L’image sert uniquement de vignette dans la fenêtre de vue d’ensemble du programme et permet d’identifier le programme.

1. Dans le **Configuration de votre environnement de test** , sélectionnez les solutions que vous souhaitez activer dans votre programme sandbox en cochant les options de la section **Solutions et modules complémentaires** table.

   * Utilisez les chevrons en regard des noms des solutions pour afficher des modules complémentaires facultatifs supplémentaires pour les solutions.

   * La variable **Sites** et **Ressources** Les solutions sont toujours incluses dans les programmes sandbox et ne peuvent pas être désélectionnées.

   ![Sélectionner des solutions et des modules complémentaires pour un sandbox](assets/sandbox-solutions-add-ons.png)

1. Une fois que vous avez sélectionné les solutions et modules complémentaires pour votre programme sandbox, cliquez sur **Créer**.

Une nouvelle carte de programme sandbox s’affiche sur la page d’entrée avec un indicateur d’état au fur et à mesure que le processus de configuration progresse.

![Création d’un sandbox à partir de la page d’aperçu](assets/sandbox-setup.png)

## Accès au sandbox {#access}

Vous pouvez afficher les détails de la configuration de votre environnement de test et accéder à l’environnement (une fois disponible) en consultant la page d’aperçu du programme.

1. Dans la page de destination de Cloud Manager, cliquez sur le bouton représentant des points de suspension du programme que vous venez de créer.

   ![Accès à l’aperçu du programme](assets/program-overview-sandbox.png)

1. Une fois l’étape de création du projet terminée, vous pouvez accéder au **Accès aux informations sur le référentiel** pour pouvoir utiliser votre référentiel git.

   ![Configuration du programme](assets/create-program4.png)

   >[!TIP]
   >
   >Pour en savoir plus sur l’accès et la gestion de votre référentiel git, voir [Accès à Git](/help/implementing/cloud-manager/managing-code/accessing-repos.md).

1. Une fois l’environnement de développement créé, vous pouvez utiliser le lien **Accès à AEM** pour vous connecter à AEM.

   ![Lien Accès à AEM](assets/create-program-5.png)

1. Une fois terminé le déploiement du canal hors production vers le développement, l’assistant vous aide à accéder à l’environnement de développement AEM ou à déployer du code vers l’environnement de développement.

   ![Déploiement d’une Sandbox](assets/create-program-setup-deploy.png)

Si vous devez passer à un autre programme ou revenir à la page d’aperçu pour créer un autre programme, cliquez sur le nom de votre programme dans le coin supérieur gauche de l’écran pour afficher la variable **Accédez à** .

![Accéder à ](assets/create-program-a1.png)
