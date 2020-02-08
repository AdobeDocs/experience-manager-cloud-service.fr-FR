---
title: Création d’un programme - Service Cloud
description: Création d’un programme - Service Cloud
translation-type: tm+mt
source-git-commit: 57206e36725e28051b2468d47da726e318bd763b

---


# Création d&#39;un programme {#create-a-program}

La solution native de cloud fournit à l’utilisateur les autorisations requises et la capacité de créer un programme sur un modèle en libre-service.

Un assistant de création de programme demandera à l’utilisateur d’envoyer des détails, en fonction de l’objectif de l’utilisateur de créer le programme dans les limites de ce qui est disponible pour le client ou l’organisation spécifique.

En cas d’accès initial à Cloud Manager ou si aucun programme n’existe dans le client, l’utilisateur verra **Créer votre premier écran de programme** . Si l’utilisateur sélectionne *Echap* ou clique en dehors de la boîte de dialogue, l’écran suivant s’affiche :

![](assets/create-program1.png)


## Utilisation de l’assistant de création de programme {#using-create-program-wizard}

Selon l’objectif de l’utilisateur de créer le programme dans les limites de ce qui est disponible pour le client/l’organisation spécifique, un assistant de création de programme demandera à l’utilisateur d’envoyer un ou plusieurs détails.

![](assets/create-program-2.png)

>[!NOTE]
>Si un programme existe déjà, vous verrez **Ajouter un programme** en haut à droite de la page d&#39;entrée, comme illustré dans la figure ci-dessous.

![](assets/create-program-add.png)

## Création d’un programme de démonstration {#create-demo-program}

>[!NOTE]
>
Un programme de démonstration est analogue à un programme sandbox dans l’interface utilisateur de Cloud Manager.

Pour créer un programme sandbox, procédez comme suit :

1. Dans l&#39;assistant de création de programme, sélectionnez **Configurer une démonstration**. L’utilisateur envoie le nom du programme avant de sélectionner **Créer**.

   ![](assets/create-program-setupdemo.png)

1. L’utilisateur verra la nouvelle carte de programme sandbox sur la page d’entrée et peut la survoler pour sélectionner l’icône Cloud Manager et accéder à la page d’aperçu de Cloud Manager. La carte informera l’utilisateur de l’état de la configuration automatique du nouveau programme sandbox. L’utilisateur verra la progression.

   ![](assets/program-create-setupdemo2.png)

1. Une fois le programme configuré et l’étape de création du projet terminée, l’utilisateur peut accéder au lien **Gérer Git** , comme illustré dans la figure ci-dessous :

   ![](assets/create-program4.png)

   >[!NOTE]
   >
   >Pour en savoir plus sur l’accès et la gestion de votre référentiel Git à l’aide de la gestion de compte Git en libre-service à partir de l’interface utilisateur de Cloud Manager, voir [Accès à Git](/help/implementing/cloud-manager/accessing-git.md).


1. Une fois l’environnement de développement créé, l’utilisateur peut **accéder au lien AEM** , comme illustré dans la figure ci-dessous :

   ![](assets/create-program-5.png)

1. Une fois le déploiement du pipeline de non-production vers le développement terminé, l’assistant guide l’utilisateur à accéder à AEM (en cours de développement) ou à déployer du code dans l’environnement de développement :

   ![](assets/create-program-setup-deploy.png)


## Création d&#39;un programme régulier {#create-regular-program}

Un programme *régulier* est destiné à un utilisateur familiarisé avec AEM et Cloud Manager et prêt à commencer à écrire, créer et tester du code dans le but de le déployer vers Production.

Pour créer un programme normal, procédez comme suit :

1. Sélectionnez **Configurer pour la production** dans l’assistant Créer un programme pour créer un programme ordinaire. L’utilisateur peut accepter le nom de programme par défaut ou le modifier avant de sélectionner **Continuer**.

   ![](assets/set-up-prod1.png)

1. L&#39;utilisateur sélectionnera les solutions à inclure dans le programme dans l&#39;écran qui sera présenté après l&#39;écran ci-dessus.



   >[!NOTE]
   >
   >L’écran ci-dessous s’affiche uniquement pour le segment des clients qui ont acheté plusieurs solutions. Pour les clients qui n’ont acheté qu’une seule solution, l’écran de sélection de la solution ci-dessous ne s’affiche pas.

   ![](assets/set-up-prod2.png)

1. Once you have selected the solutions, click **Create**.

   ![](assets/set-up-prod3.png)

1. Une fois la carte de votre programme affichée sur la page d’entrée, passez le curseur de la souris dessus pour sélectionner l’icône Cloud Manager et accéder à la page **Présentation** de Cloud Manager.

   ![](assets/set-up-prod4.png)

1. La carte d&#39;appel à l&#39;action principale guidera l&#39;utilisateur à créer un environnement, à créer un pipeline de non-production et enfin un pipeline de production.
   ![](assets/set-up-prod5.png)


   >[!NOTE]
   >
   >Un programme normal ne comporte pas de fonction de configuration **** automatique.





