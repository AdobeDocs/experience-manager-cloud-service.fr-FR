---
title: Création et gestion des affichages dans Screens as a Cloud Service
description: Cette page décrit comment créer et gérer des affichages dans Screens as a Cloud Service.
exl-id: 0f9faa4b-b50e-40f8-a8ed-280f8bd0a9b8
feature: Authoring Screens
role: Admin, Developer, User
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 89%

---

# Création et gestion des affichages dans Screens as a Cloud Service {#create-displays-screens-cloud}

Une fois que vous avez publié votre canal, il est temps de créer votre affichage dans le fournisseur de services Screens.

Un affichage est un groupe virtuel d’écrans généralement positionnés les uns à côté des autres. L’affichage est généralement permanent par rapport à une installation. Les auteurs et autrices utilisent ce contenu d’objet et se réfèrent toujours à un affichage logique plutôt qu’à leurs contreparties physiques.

## Objectif {#objective}

Ce document vous aide à comprendre comment créer et gérer des affichages dans le fournisseur de services Screens. Après avoir lu ce document, vous devriez :

* savoir comment créer et supprimer des affichages ;
* comprendre comment organiser vos affichages dans des dossiers.

## Procédure de création d’un affichage {#create-display}

Pour créer l’affichage à partir du fournisseur de services Screens, procédez comme suit :

1. Accédez au fournisseur de services Screens à partir de votre instance AEM Cloud Service.
1. Sélectionnez **Affiche** dans le panneau de navigation de gauche et cliquez sur **Créer** dans le coin supérieur droit de l’écran.

   ![image](/help/screens-cloud/assets/display/disp-1.png)

1. Sélectionnez **Affichage** dans la barre d’actions.

   ![image](/help/screens-cloud/assets/display/disp-2.png)

1. Saisissez le titre **LoopingChannelDisplay** dans **Nom d’affichage** et cliquez sur **Créer**.

   ![image](/help/screens-cloud/assets/display/disp3.png)

1. L’affichage intitulé **LoopingChannelDisplay** est désormais visible dans la liste d’affichage.

   ![image](/help/screens-cloud/assets/display/disp-4.png)

### Suppression d’un affichage {#deleting-display}

Vous pouvez supprimer un affichage du fournisseur de services Screens.

Sélectionnez l’affichage et cliquez sur **Supprimer** au bas du panneau, comme illustré dans la figure ci-dessous.

![Image](/help/screens-cloud/assets/display/disp-5.png)

## Étapes d’organisation des affichages dans des dossiers {#organize-display}

## Activer et désactiver le rail de dossiers {#toggle-rail}

Vous pouvez régler le rail de dossiers pour qu’il affiche des dossiers spécifiques plutôt que tous les dossiers :

1. Accédez à la vue d’inventaire affichée en cliquant sur le bouton mis en surbrillance ci-dessous :

   ![image](/help/screens-cloud/assets/display/display-inventory.png)

1. Le rail latéral des dossiers s’affiche.

   ![image](/help/screens-cloud/assets/display/toggle-rail.png)

1. Sélectionnez **Masquer les dossiers** pour le fermer à nouveau.

## Création d’un dossier {#create-folder}

Vous pouvez créer des dossiers pour améliorer l’organisation de vos affichages.

1. Accédez à la vue d’inventaire.
1. Assurez-vous que vous ne vous trouvez pas dans un dossier. Les éléments suivants doivent s’afficher :

   ![image](/help/screens-cloud/assets/display/verify-view.png)

   Remarque : **Tous les affichages** doit être sélectionné dans le rail latéral du dossier et la navigation du chemin de navigation doit uniquement afficher **Affichages**.

1. Cliquez sur le bouton « Créer » en haut à droite et sélectionnez l’option **Dossier**.

   ![image](/help/screens-cloud/assets/display/Createfolder.png)

1. Renseignez le titre du nouveau dossier et cliquez sur **Créer**.

   ![image](/help/screens-cloud/assets/display/Createfolder2.png)

## Création d’un dossier imbriqué {#nested-folder}

1. Accédez à la vue d’inventaire.

1. Sélectionnez le dossier parent souhaité dans le rail latéral du dossier ou en naviguant dans la vue d’inventaire.
1. Vérifiez que le dossier parent souhaité est sélectionné.

   ![image](/help/screens-cloud/assets/display/Nestedview.png)

   * Le dossier doit être sélectionné dans le rail latéral du dossier.
   * La navigation dans le chemin de navigation doit afficher le nom du dossier actif en face d’**Affichages**.

1. Cliquez sur **Créer** en haut à droite et sélectionnez l’option **Dossier**.

   ![image](/help/screens-cloud/assets/display/Createfolder.png)

1. Renseignez le titre du nouveau dossier et cliquez sur **Créer**.

   ![image](/help/screens-cloud/assets/display/Createfolder2.png)

## Déplacer du contenu vers un nouveau dossier {#move-folder}

Vous pouvez déplacer du contenu vers vos nouveaux dossiers pour mieux organiser vos affichages.

1. Accédez à la vue d’inventaire.

1. Sélectionnez le dossier parent souhaité dans le rail latéral du dossier ou en le sélectionnant dans la vue d’inventaire.

1. Vérifiez que vous avez sélectionné le dossier parent souhaité.

![image](/help/screens-cloud/assets/display/movetofolder.png)

**Remarque** : Le dossier doit être sélectionné dans le rail latéral de dossiers. De plus, la navigation dans le chemin de navigation doit afficher le nom du dossier actif en regard de **Affichages**.

## Comment supprimer du contenu d’un dossier {#delete-folder}

Toutes les opérations de dossier sont accessibles via la barre d’actions de sélection dans la vue d’inventaire.

1. Accédez au dossier parent ou sélectionnez-le dans le rail latéral.

1. Dans la vue d’inventaire, sélectionnez le dossier enfant que vous souhaitez supprimer et assurez-vous qu’il est vide.

1. Cliquez sur le bouton **Supprimer** dans la barre d’actions de sélection. L’action est désactivée si le dossier n’est pas vide.


## Et après ? {#whats-next}

Maintenant que vous avez appris à créer et gérer des affichages pour votre projet, vous devez continuer votre parcours Screens as a Cloud Service en consultant le document [Attribution d’un canal à un affichage dans Screens as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/create-content/assigning-channels-to-display.html?lang=fr).
