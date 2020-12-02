---
title: Création d'un Programme - Cloud Service
description: Création d'un Programme - Cloud Service
translation-type: tm+mt
source-git-commit: 5658b2cc853ff7e6222a7f35e56527577d2c7324
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 3%

---


# Création d’un programme {#create-a-program}

La solution native de cloud fournit à l’utilisateur les autorisations requises et la possibilité de créer un programme sur un modèle en libre-service.

Un assistant de création de programme demande à l’utilisateur d’envoyer des détails, en fonction de l’objectif de l’utilisateur de créer le programme dans les limites de ce qui est disponible pour le client ou l’organisation spécifique.

Dans le événement de l’accès initial à Cloud Manager ou s’il n’existe aucun programme dans le client, l’utilisateur verra **Créer votre premier écran de Programme**. Si l’utilisateur sélectionne *Echap* ou clique en dehors de la boîte de dialogue, l’écran suivant s’affiche :

![](assets/create-program1.png)


## Utilisation de l&#39;Assistant Création de Programme {#using-create-program-wizard}

En fonction de l’objectif de l’utilisateur de créer le programme dans les limites de ce qui est disponible pour le client/l’organisation spécifique, un assistant de création de programme demande à l’utilisateur d’envoyer un ou plusieurs détails.

![](assets/create-sandbox.png)

>[!NOTE]
>Si un programme existe déjà, vous verrez **Ajouter le Programme** en haut à droite du landing page, comme illustré dans la figure ci-dessous.

![](assets/create-program-add.png)

## Création d’un programme Sandbox {#create-sandbox-program}

Pour créer un programme de sandbox, procédez comme suit :

1. Dans l’assistant de création de programme, sélectionnez **Configurer un sandbox**. L’utilisateur envoie le nom du programme avant de sélectionner **Créer**.

   ![](assets/create-sandbox.png)

1. L’utilisateur voit la nouvelle carte de programme sandbox sur le landing page et peut la survoler pour sélectionner l’icône Cloud Manager et accéder à la page d’aperçu de Cloud Manager. La carte informe l&#39;utilisateur de l&#39;état de la configuration automatique du programme de sandbox nouvellement créé. L&#39;utilisateur verra la progression.

   ![](assets/program-create-setupdemo2.png)

1. Une fois le programme configuré et l&#39;étape de création du projet terminée, l&#39;utilisateur peut accéder au lien **Gérer les accès**, comme indiqué dans la figure ci-dessous :

   ![](assets/create-program4.png)

   >[!NOTE]
   >
   >Pour en savoir plus sur l’accès et la gestion de votre référentiel Git à l’aide de la gestion de compte Git en libre-service depuis l’interface utilisateur de Cloud Manager, voir [Accès à Git](/help/implementing/cloud-manager/accessing-git.md).


1. Une fois l’environnement de développement créé, l’utilisateur peut accéder au lien **AEM**, comme indiqué dans la figure ci-dessous :

   ![](assets/create-program-5.png)

1. Une fois le déploiement du canal de non-production vers le développement terminé, l’assistant guide l’utilisateur à accéder à AEM (sur le développement) ou à déployer du code vers l’environnement de développement :

   ![](assets/create-program-setup-deploy.png)

   >[!NOTE]
   >Vous pouvez également modifier, changer ou ajouter un programme à partir de la page d’aperçu de Cloud Manager, comme illustré ci-dessous :

   ![](assets/create-program-a1.png)

## Suppression d&#39;un Programme Sandbox {#delete-sandbox-program}

Un utilisateur de Programme Sandbox dans le rôle *Propriétaire d’entreprise* ou *Deployment Manager* de Cloud Manager peut supprimer son jeu d’environnements de production et d’étape via l’interface utilisateur de Cloud Manager.

>[!NOTE]
>La sélection de l’option de suppression dans l’environnement de production ou d’évaluation supprime également l’autre dans le jeu d’environnements.

L’option de suppression est disponible à partir du landing page, comme illustré ci-dessous :

![](assets/delete-sandbox1.png)

Ou,

Sélectionnez **Supprimer le Programme** dans la page **Aperçu du Programme** pour supprimer votre Programme Sandbox.

![](assets/delete-sandbox2.png)


## Création d’un Programme régulier {#create-regular-program}

Un programme *Normal* est destiné à un utilisateur familiarisé avec AEM et Cloud Manager et prêt à début la rédaction, la création et le test de code dans le but de le déployer vers Production.

Pour créer un programme normal, procédez comme suit :

1. Sélectionnez **Configurer pour la production** dans l’assistant de création de Programme pour créer un programme normal. L’utilisateur peut accepter le nom de programme par défaut ou le modifier avant de sélectionner **Continuer**.

   ![](assets/create-prod1.png)

1. L&#39;utilisateur sélectionne les solutions à inclure dans le programme de l&#39;écran qui seront présentées après l&#39;écran ci-dessus.



   >[!NOTE]
   >
   >L’écran ci-dessous s’affiche uniquement pour le segment de clients ayant acheté plusieurs solutions. Pour les clients qui n&#39;ont acheté qu&#39;une seule solution, l&#39;écran de sélection de la solution ci-dessous ne s&#39;affiche pas.

   ![](assets/set-up-prod2.png)

1. Une fois les solutions sélectionnées, cliquez sur **Créer**.

   ![](assets/set-up-prod3.png)

1. Une fois que vous avez vu votre carte de programme sur le landing page, passez la souris dessus pour sélectionner l’icône Cloud Manager et accéder à la page Cloud Manager **Aperçu**.

   ![](assets/set-up-prod4.png)

1. La carte d&#39;appel à l&#39;action principale guide l&#39;utilisateur à créer un environnement, à créer un pipeline de non-production et enfin un pipeline de production.
   ![](assets/set-up-prod5.png)


   >[!NOTE]
   >
   >Un programme normal n&#39;a pas de fonction **de configuration automatique**.





