---
title: Assistant de création du projet
description: Découvrez l’assistant de création de projet qui vous aide à configurer rapidement votre projet après avoir créé votre programme de production.
exl-id: 03736ca7-1345-4faf-a61a-f9213ab5c89a
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 96%

---

# Assistant de création du projet {#project-creation-wizard}

Une fois votre programme de production créé, Cloud Manager propose un assistant pour créer un projet AEM minimal basé sur l’[archétype de projet AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr) pour vous permettre de commencer rapidement.

Suivez ces étapes pour créer un projet d’application AEM dans Cloud Manager à l’aide de l’assistant.

1. Créez un programme de production en suivant les étapes du document [Création de programmes de production](creating-production-programs.md)

1. Une fois la configuration du programme terminée, accédez à l’écran **Présentation** de votre programme et affichez la carte d’appel à l’action **Créer une branche et un projet** dans la partie supérieure.

   ![Carte d’appel à l’action pour l’assistant](assets/create-wizard1.png)

1. Cliquez sur **Créer** pour démarrer l’assistant et confirmez le **Titre** et le **Nom de nouvelle branche** dans la fenêtre **Créer une branche et un projet**.

   ![Créer une branche et un projet](assets/create-wizard2.png)

1. Cliquez éventuellement sur le séparateur pour afficher les paramètres supplémentaires de votre projet. Les valeurs par défaut sont fournies par l’archétype de projet AEM et n’ont généralement pas besoin d’être modifiées.

   ![Paramètres de projet supplémentaires](assets/create-wizard5.png)

1. Cliquez sur **Créer** pour lancer le processus de création du projet.


Une carte **Création du projet en cours** remplace maintenant la carte d’appel à l’action **Créer une branche et un projet** en haut de l’écran **Présentation du programme**.

![Création du projet en cours](assets/create-wizard3.png)

Une fois la création du programme terminée, une carte **Ajouter un environnement** remplace la carte **Création du projet en cours** en haut de l’écran **Présentation du programme**.

![Ajout d’un environnement](assets/create-wizard4.png)

Vous disposez désormais d’un projet AEM basé sur l’archétype AEM ajouté à votre référentiel git afin de servir de base de développement pour votre propre projet. Vous pouvez ensuite créer vos environnements dans lesquels vous pouvez déployer le code du projet.

Consultez [Gestion de vos environnements](/help/implementing/cloud-manager/manage-environments.md) pour savoir comment ajouter ou gérer des environnements.

>[!NOTE]
>
>L’assistant n’est disponible que pour les programmes de production. Étant donné que les [programmes sandbox](introduction-sandbox-programs.md#auto-creation) comprennent une création automatique de projet, l’assistant n’est pas nécessaire.