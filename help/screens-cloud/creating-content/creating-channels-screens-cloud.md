---
title: Création et gestion des canaux dans Screens en tant que Cloud Service
description: Cette page décrit comment créer et gérer des canaux dans Screens en tant que Cloud Service.
hide: true
hidefromtoc: true
index: false
source-git-commit: f0e005ddc59c575188d15986cabdbe04cb48ad03
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 16%

---


# Création et gestion des canaux dans Screens en tant que Cloud Service {#creating-channels-screens-cloud}

Une fois que vous avez créé un projet AEM Screens, vous devez créer des canaux.
***Canaux*** : affichez une séquence de contenu (images et vidéos), un site web ou une application d’une seule page.

## Intention {#objective}

Ce document vous aide à comprendre la création et la gestion de canaux pour votre projet AEM Screens dans le fournisseur de contenu Screens. Après lecture, vous devez être :

* Découvrez comment créer des canaux pour le fournisseur de contenu Screens
* gestion et modification du contenu de vos canaux

## Procédure de création d’un canal de séquence dans Screens en tant que Cloud Service {#create-new-channel}

>[!NOTE]
>**Prérequis**
>Avant de commencer cette section du guide, consultez la section [Création et gestion de projets dans Screens en tant que Cloud Service](/help/screens-cloud/creating-content/creating-projects-screens-cloud.md).

Pour créer un canal de séquence dans Screens en tant que Cloud Service, procédez comme suit :

1. Accédez à Fournisseur de contenu Screens.

1. Accédez à votre projet AEM Screens, par exemple *FirstDigitalExperience*.

1. Sélectionnez le dossier **Canaux** de votre projet, par exemple **FirstDigitalExperience** —> **Canaux** et cliquez sur **Créer** dans la barre d’actions.

   ![](/help/screens-cloud/assets/create-content/channel-create1.png)

1. Sélectionnez le modèle, par exemple **Canal de séquence** dans l’assistant **Créer** et cliquez sur **Suivant**.

   ![](/help/screens-cloud/assets/create-content/channel-create2.png)
   >[!NOTE]
   > L’assistant **Créer** fournit différents types de modèles lors de la création d’un canal. Pour plus d’informations, reportez-vous à la section [Modèles disponibles](#available-templates) de l’assistant de création.

1. Saisissez le nom de votre canal de séquence, par exemple **LoopingChannelOne** et cliquez sur **Créer**.

   ![](/help/screens-cloud/assets/create-content/channel-create3.png)

   Un **LoopingChannelOne** apparaît désormais dans le dossier Canaux de votre projet AEM Screens.

   Une fois que vous avez créé le canal, vous pouvez maintenant ajouter du contenu à votre canal. Reportez-vous à la section [Ajout de contenu à un canal](#add-content) pour savoir comment ajouter des ressources (images/vidéos) à votre canal.

## Gestion d’un canal {#managing-channels}

Vous pouvez modifier, copier, prévisualiser, supprimer un canal, et afficher ses propriétés et son tableau de bord.

Accédez au canal à partir de votre projet et sélectionnez-le, comme illustré dans la figure ci-dessous. Vous pouvez désormais sélectionner les options telles que la modification du canal, l’affichage des propriétés, la prévisualisation du contenu, la gestion de la publication ou la suppression du canal dans la barre d’actions.

![](/help/screens-cloud/assets/create-content/channelprop1.png)

### Ajout de contenu à un canal {#add-content}

Pour ajouter du contenu à un canal ou modifier son contenu, suivez les étapes ci-dessous :

1. Sélectionnez le canal à modifier, comme illustré dans la figure ci-dessous. Cliquez sur **Modifier** dans le coin supérieur gauche de la barre d’actions pour ouvrir l’éditeur.

   ![](/help/screens-cloud/assets/create-content/edit-channel1.png)

1. L’éditeur vous permet d’ajouter à votre canal des ressources/composants que vous souhaitez publier.

1. Faites glisser et déposez les ressources à partir du volet de gauche et ajoutez-les à l’éditeur.

   ![](/help/screens-cloud/assets/create-content/edit-channel2.png)

   >[!NOTE]
   >Cliquez sur **Aperçu** pour prévisualiser le contenu de votre canal.
   >![](/help/screens-cloud/assets/create-content/edit-channelpreview.png)

## Modèles disponibles dans l’assistant de création {#available-templates}

Les modèles suivants sont disponibles lors de l’utilisation de l’assistant de canal **Créer** :

| Modèles disponibles | Description |
|--- |--- |
| Dossier de canaux | Permet de créer un dossier où stocker une collection de canaux. |
| Canal de séquence | Permet de créer un canal qui lit les composants de manière séquentielle (l’un après l’autre comme une série de diapositives). |
| Canal d’écran partagé barre en L gauche ou droite | Permet aux auteurs de contenus d’afficher différents types de ressources dans des zones de taille appropriée. |


## Suite {#whats-next}

Maintenant que vous avez configuré un canal AEM Screens dans votre projet, vous devez publier votre canal. Reportez-vous à [Publication de canaux dans Screens en tant que Cloud Service](/help/screens-cloud/creating-content/manage-publish.md) avant de gérer vos lecteurs à partir du fournisseur de services Screens.