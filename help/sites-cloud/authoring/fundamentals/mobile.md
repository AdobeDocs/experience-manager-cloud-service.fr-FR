---
title: Création d’une page pour les périphériques mobiles
description: Lors de la création pour les périphériques mobiles, vous pouvez basculer entre plusieurs émulateurs pour voir ce que l’utilisateur final voit.
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Création d’une page pour les périphériques mobiles {#authoring-a-page-for-mobile-devices}

Les pages d’Adobe Experience Manager reposent sur une disposition réactive. La mise en page réactive adapte automatiquement votre contenu au périphérique cible, éliminant ainsi la nécessité de créer du contenu pour des périphériques spécifiques.

Lorsque vous créez une page mobile, celle-ci est affichée d’une manière qui émule le périphérique mobile. Lorsque vous créez une page, vous pouvez basculer entre plusieurs émulateurs pour voir ce que l’utilisateur voit lorsqu’il accède à la page.

Les périphériques sont regroupés en fonction des catégories : fonction, intelligent et tactile, selon les fonctionnalités des périphériques pour effectuer le rendu d’une page. Lorsque l’utilisateur final accède à une page mobile, AEM détecte le périphérique et envoie la représentation qui correspond à son groupe de périphériques.

>[!NOTE]
>
>Pour créer un site mobile en fonction d’un site standard existant, créez une live copy du site standard. Voir Création d’une Live Copy pour différents canaux.
>
>Les développeurs AEM peuvent créer des groupes de périphériques. Voir Création de filtres de groupe de périphériques.
<!--
>To create a mobile site based on an existing standard site, create a live copy of the standard site. (See [Creating a Live Copy for Different Channels](/help/sites-administering/msm-livecopy.md).)
>
>AEM developers can create new device groups. (See [Creating Device Group Filters](/help/sites-developing/groupfilters.md).)
-->

Utilisez la procédure suivante pour créer une page mobile :

1. From global navigation open the **Sites** console.
1. Modification d’une page de contenu.
1. Switch to the desired emulator by clicking the **Emulator** icon at the top of the page.

   ![Icône Emulateur](/help/sites-cloud/authoring/assets/emulator.png)

1. Faites glisser des composants de l’explorateur de composants ou de ressources vers la page.
1. [Modifiez la disposition](/help/sites-cloud/authoring/features/responsive-layout.md) réactive de la page et de ses composants en fonction du périphérique sélectionné.

La page se présente comme suit :

![Exemple de mobile](/help/sites-cloud/authoring/assets/mobile.png)

>[!NOTE]
>
>Les émulateurs sont désactivés lorsqu’une page de l’instance de création est demandée à partir d’un périphérique mobile.
