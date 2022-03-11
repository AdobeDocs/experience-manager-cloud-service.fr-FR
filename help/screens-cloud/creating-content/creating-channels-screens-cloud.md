---
title: Création et gestion des canaux dans Screens as a Cloud Service
description: Cette page décrit comment créer et gérer des canaux dans Screens as a Cloud Service.
exl-id: 3b0bae7a-4a45-485a-ab04-604510ff6578
source-git-commit: 96a0dacf69f6f9c5744f224d1a48b2afa11fb09e
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 100%

---

# Création et gestion d’un canal dans Screens as a Cloud Service {#creating-channels-screens-cloud}

Une fois que vous avez créé un projet AEM Screens, vous devez créer des canaux.
Les ***canaux*** affichent une séquence de contenu (images et vidéos), un site web ou une application d’une seule page.

## Objectif {#objective}

Ce document vous aide à comprendre la création et la gestion de canaux pour votre projet AEM Screens dans le fournisseur de contenu Screens. Après lecture, vous devriez être en mesure de :

* comprendre comment créer des canaux pour le fournisseur de contenu Screens ;
* gérer et modifier du contenu dans vos canaux.

## Procédure de création d’un canal de séquence dans Screens as a Cloud Service {#create-new-channel}

>[!NOTE]
>**Prérequis**
>Avant de commencer cette section du guide, consultez la section [Création et gestion de projets dans Screens as a Cloud Service](/help/screens-cloud/creating-content/creating-projects-screens-cloud.md).

Pour créer un canal de séquence dans Screens as a Cloud Service, procédez comme suit :

1. Accédez au fournisseur de contenu Screens.

1. Accédez à votre projet AEM Screens, par exemple *FirstDigitalExperience*.

1. Sélectionnez le dossier **Canaux** de votre projet, par exemple **FirstDigitalExperience** --> **Canaux** et cliquez sur **Créer** dans la barre d’actions.

   ![](/help/screens-cloud/assets/create-content/channel-create1.png)

1. Sélectionnez le modèle, par exemple **Canal de séquence** dans l’assistant **Créer** et cliquez sur **Suivant**.

   ![](/help/screens-cloud/assets/create-content/channel-create2.png)
   >[!NOTE]
   > L’assistant **Créer** fournit différents types de modèles lors de la création d’un canal. Pour plus d’informations, reportez-vous à la section [Modèles disponibles](#available-templates) de l’assistant de création.

1. Saisissez le nom de votre canal de séquence, par exemple **LoopingChannelOne** et cliquez sur **Créer**.

   ![](/help/screens-cloud/assets/create-content/channel-create3.png)

   Un **LoopingChannelOne** apparaît désormais dans le dossier Canaux de votre projet AEM Screens.

   Une fois que vous avez créé le canal, vous pouvez ajouter du contenu à votre canal. Reportez-vous à la section [Ajout de contenu à un canal](#add-content) pour savoir comment ajouter des ressources (images/vidéos) à votre canal.

## Gestion d’un canal {#managing-channels}

Vous pouvez modifier, copier, prévisualiser, supprimer un canal, et afficher ses propriétés et son tableau de bord.

Accédez au canal à partir de votre projet et sélectionnez-le, comme illustré ci-dessous. Dans la barre d’action, vous pouvez désormais sélectionner les options telles que la modification du canal, l’affichage des propriétés, la prévisualisation du contenu, la gestion de la publication ou la suppression du canal.

![](/help/screens-cloud/assets/create-content/channelprop1.png)

### Ajout de contenu à un canal {#add-content}

Pour ajouter du contenu à un canal ou modifier son contenu, suivez les étapes ci-dessous :

1. Sélectionnez le canal que vous souhaitez modifier, tel qu’illustré ci-dessous. Cliquez sur **Modifier** dans l’angle supérieur gauche de la barre d’actions pour ouvrir l’éditeur.

   ![](/help/screens-cloud/assets/create-content/edit-channel1.png)

1. L’éditeur vous permet d’ajouter au canal des ressources/composants que vous souhaitez publier.

1. Faites glisser et déposez les ressources à partir du volet de gauche et ajoutez-les à l’éditeur.

   ![](/help/screens-cloud/assets/create-content/edit-channel2.png)

   >[!NOTE]
   >Cliquez sur **Aperçu** pour prévisualiser le contenu de votre canal.
   >![](/help/screens-cloud/assets/create-content/edit-channelpreview.png)

## Modèles disponibles dans l’assistant de création {#available-templates}

Les modèles suivants sont disponibles lors de l’utilisation de l’assistant de canal **Créer** :

| Modèles disponibles | Description |
|--- |--- |
| Dossier de canaux | Permet de créer un dossier où stocker une collection de canaux. |
| Canal de séquence | Permet de créer un canal qui lit les composants de manière séquentielle (l’un après l’autre comme une série de diapositives). |
| Canal d’écran partagé barre en L gauche ou droite | Permet aux auteurs de contenus d’afficher différents types de ressources dans des zones de taille appropriée. |


## Et après ? {#whats-next}

Maintenant que vous avez configuré un canal AEM Screens dans votre projet, vous devez publier votre canal. Reportez-vous à [Publication de canaux dans Screens as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/create-content/manage-publish.html?lang=fr) avant de gérer vos lecteurs à partir du fournisseur de services Screens.
