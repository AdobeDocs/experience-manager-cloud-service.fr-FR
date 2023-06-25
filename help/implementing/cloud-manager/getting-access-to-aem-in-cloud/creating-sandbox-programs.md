---
title: Création de programmes Sandbox
description: Découvrez comment utiliser Cloud Manager pour créer votre propre programme Sandbox à des fins de formation, de démonstration, de point de vente ou à d’autres fins hors production.
exl-id: 10011392-3059-4bb0-88db-0af1d390742e
source-git-commit: f0e9fe0bdf35cc001860974be1fa2a7d90f7a3a9
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 59%

---

# Création de programmes Sandbox {#create-sandbox-program}

Un programme Sandbox est généralement créé à des fins de formation, pour l’exécution de démonstrations, d’activation, de points de vente ou de documentation, et n’est pas destiné à transporter du trafic en direct.

Découvrez-en plus sur les types de programme dans le document [Présentation des programmes et des types de programme.](program-types.md)

## Création d’un programme Sandbox {#create}

Pour créer un programme Sandbox, procédez comme suit.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Dans la page de destination de Cloud Manager, cliquez sur **Ajouter le programme** dans le coin supérieur droit de l’écran.

   ![Page de destination de Cloud Manager](assets/cloud-manager-my-programs.png)

1. Dans l’assistant de création de programme, sélectionnez **Configuration d’un environnement de test** et indiquez un nom de programme.

   ![Création d’un type de programme](assets/create-sandbox.png)

1. Vous pouvez éventuellement ajouter une image au programme en la faisant glisser et en la déposant sur le **Ajout d’une image de programme** cibler ou cliquer dessus pour sélectionner une image dans l’explorateur de fichiers. Cliquez ou appuyez sur **Continuer**.

   * L’image sert uniquement de mosaïque dans la fenêtre de présentation du programme et permet d’identifier le programme.

1. Dans le **Configuration de votre environnement de test** , sélectionnez les solutions que vous souhaitez activer dans votre programme sandbox en cochant les options de la section **Solutions et modules complémentaires** table.

   * Utilisez les chevrons en regard des noms des solutions pour afficher des modules complémentaires facultatifs supplémentaires pour les solutions.

   * Le **Sites** et **Ressources** Les solutions sont toujours incluses dans les programmes sandbox et ne peuvent pas être désélectionnées.

   ![Sélection de solutions et de modules complémentaires pour un environnement de test](assets/sandbox-solutions-add-ons.png)

1. Une fois que vous avez sélectionné les solutions et modules complémentaires pour votre programme sandbox, appuyez sur cliquez sur . **Créer**.

Une nouvelle carte de programme sandbox s’affiche sur la page de destination avec un indicateur de statut au fur et à mesure que le processus de configuration progresse.

![Création d’un sandbox à partir de la page d’aperçu](assets/sandbox-setup.png)

## Accès aux environnements de test {#access}

Vous pouvez afficher les détails de la configuration de votre sandbox et accéder à l’environnement (une fois disponible) en consultant la page d’aperçu du programme.

1. Sur la page d’entrée de Cloud Manager, cliquez sur le bouton représentant des points de suspension du nouveau programme.

   ![Accès à l’aperçu du programme](assets/program-overview-sandbox.png)

1. Une fois l’étape de création du projet terminée, vous pouvez accéder à la variable **Accès aux informations sur le référentiel** pour pouvoir utiliser votre référentiel git.

   ![Configuration du programme](assets/create-program4.png)

   >[!TIP]
   >
   >Pour en savoir plus sur l’accès à votre référentiel git et sa gestion, reportez-vous au document [Accès à Git.](/help/implementing/cloud-manager/managing-code/accessing-repos.md)

1. Une fois l’environnement de développement créé, vous pouvez utiliser le lien **Accès à AEM** pour vous connecter à AEM.

   ![Lien Accès à AEM](assets/create-program-5.png)

1. Une fois terminé le déploiement du canal hors production vers le développement, l’assistant vous aide à accéder à l’environnement de développement AEM ou à déployer du code vers l’environnement de développement.

   ![Déploiement d’une Sandbox](assets/create-program-setup-deploy.png)

Si, à tout moment, vous devez passer à un autre programme ou revenir à la page d’aperçu pour créer un autre programme, cliquez sur le nom de votre programme dans le coin supérieur gauche de l’écran pour afficher l’option **Accéder à**.

![Accéder à ](assets/create-program-a1.png).
