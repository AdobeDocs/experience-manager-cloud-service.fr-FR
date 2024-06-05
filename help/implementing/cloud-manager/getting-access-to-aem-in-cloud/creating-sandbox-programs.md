---
title: Création de programmes Sandbox
description: Découvrez comment utiliser Cloud Manager pour créer votre propre programme Sandbox à des fins de formation, de démonstration, de point de vente ou à d’autres fins hors production.
exl-id: 10011392-3059-4bb0-88db-0af1d390742e
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 74%

---

# Création de programmes Sandbox {#create-sandbox-program}

Un programme Sandbox est généralement créé à des fins de formation, pour l’exécution de démonstrations, d’activation, de points de vente ou de documentation, et n’est pas destiné à transporter du trafic en direct.

Découvrez-en plus sur les types de programme dans le document [Présentation des programmes et des types de programme.](program-types.md)

## Création d’un programme Sandbox {#create}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur le **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)** console, appuyez ou cliquez sur **Ajout d’un programme** près du coin supérieur droit de l’écran.

   ![Page de destination de Cloud Manager](assets/log-in.png)

1. Dans l’assistant de création de programme, sélectionnez **Configurer une sandbox** et indiquez un nom de programme.

   ![Création d’un type de programme](assets/create-sandbox.png)

1. Vous pouvez éventuellement ajouter une image au programme en faisant glisser un fichier image et en le déposant sur la cible **Ajouter une image de programme** ou en cliquant dessus pour sélectionner une image dans l’explorateur de fichiers. Sélectionnez **Continuer**.

   * L’image sert uniquement de vignette dans la fenêtre de vue d’ensemble du programme et permet d’identifier le programme.

1. Dans le **Configuration de votre environnement de test** , sélectionnez les solutions que vous souhaitez activer dans votre programme sandbox en cochant les options du **Solutions et modules complémentaires** table.

   * Utilisez les chevrons en regard des noms des solutions pour afficher des modules complémentaires facultatifs supplémentaires pour les solutions.

   * Les solutions **Sites** et **Assets** sont toujours incluses dans les programmes Sandbox et ne peuvent pas être désélectionnées.

   ![Sélection de solutions et de modules complémentaires pour une sandbox](assets/sandbox-solutions-add-ons.png)

1. Une fois que vous avez sélectionné les solutions et modules complémentaires pour votre programme Sandbox, cliquez sur **Créer**.

Une nouvelle carte de programme Sandbox s’affiche sur la page de destination avec un indicateur de statut au fur et à mesure que le processus de configuration progresse.

![Création d’une sandbox à partir de la page d’aperçu](assets/sandbox-setup.png)

## Accès au sandbox {#access}

Vous pouvez afficher les détails de la configuration de votre sandbox et accéder à l’environnement (une fois disponible) en consultant la page d’aperçu du programme.

1. Dans la page d’entrée de Cloud Manager, cliquez sur le bouton représentant des points de suspension du programme créé.

   ![Accès à l’aperçu du programme](assets/program-overview-sandbox.png)

1. Une fois l’étape de création du projet terminée, vous pouvez accéder au lien **Accéder aux informations sur le référentiel** pour pouvoir utiliser votre référentiel git.

   ![Configuration du programme](assets/create-program4.png)

   >[!TIP]
   >
   >Pour en savoir plus sur l’accès à votre référentiel git et sa gestion, consultez [Accès à Git](/help/implementing/cloud-manager/managing-code/accessing-repos.md).

1. Une fois l’environnement de développement créé, vous pouvez utiliser le lien **Accès à AEM** pour vous connecter à AEM.

   ![Lien Accès à AEM](assets/create-program5.png)

1. Une fois le pipeline hors production se déployant vers le développement terminé, l’assistant de l’ appel à l’action vous guide à accéder à l’environnement de développement AEM ou à déployer du code vers l’environnement de développement.

   ![Déploiement d’une Sandbox](assets/create-program-setup-deploy.png)

>[!TIP]
>
>Consultez le document [Navigation dans l’interface utilisateur de Cloud Manager](/help/implementing/cloud-manager/navigation.md) pour plus d’informations sur la navigation dans Cloud Manager et sur la compréhension de la variable **Mes programmes** console.
