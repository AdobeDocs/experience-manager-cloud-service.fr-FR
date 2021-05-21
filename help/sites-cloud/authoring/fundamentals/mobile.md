---
title: Création d’une page pour les appareils mobiles
description: Lors de la création pour les appareils mobiles, vous pouvez basculer entre plusieurs émulateurs pour voir ce que l’utilisateur final voit.
exl-id: fabd4468-3304-402f-9522-342da3bbae94
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 100%

---

# Création d’une page pour les appareils mobiles {#authoring-a-page-for-mobile-devices}

Les pages d’Adobe Experience Manager reposent sur une disposition réactive. La [mise en page réactive](/help/sites-cloud/authoring/features/responsive-layout.md) adapte automatiquement votre contenu à l’appareil cible, éliminant ainsi la nécessité de créer du contenu pour des appareils spécifiques.

Lorsque vous créez une page mobile, celle-ci est affichée d’une manière qui émule l’appareil mobile. Lorsque vous créez une page, vous pouvez basculer entre plusieurs émulateurs pour voir ce que l’utilisateur voit lorsqu’il accède à la page.

Les périphériques sont regroupés en fonction des catégories : fonction, intelligent et tactile, selon les fonctionnalités des périphériques pour effectuer le rendu d’une page. Lorsque l’utilisateur final accède à une page mobile, AEM détecte le périphérique et envoie la représentation qui correspond à son groupe de périphériques.

>[!NOTE]
>
>Pour créer un site mobile en fonction d’un site standard existant, créez une Live Copy du site standard. Voir la section [Création de Live Copies](/help/sites-cloud/administering/msm/creating-live-copies.md).
>
>Les développeurs d’AEM peuvent créer de nouveaux groupes d’appareils. Consultez Création de filtres de groupe d’appareils.

<!--
>AEM developers can create new device groups. (See [Creating Device Group Filters](/help/sites-developing/groupfilters.md).)
-->

Utilisez la procédure suivante pour créer une page mobile :

1. À partir de la navigation globale, ouvrez la console **Sites**.
1. Modifiez une page de contenu.
1. Basculez vers l’émulateur de votre choix en cliquant sur l’icône **Émulateur** en haut de la page.

   ![Icône Émulateur](/help/sites-cloud/authoring/assets/emulator.png)

1. Faites glisser des composants de l’explorateur de composants ou de ressources vers la page.
1. [Modifiez la disposition réactive](/help/sites-cloud/authoring/features/responsive-layout.md) de la page et de ses composants en fonction de l’appareil sélectionné.

La page ressemble à ce qui suit :

![Exemple de mobile](/help/sites-cloud/authoring/assets/mobile.png)

>[!NOTE]
>
>Les émulateurs sont désactivés lorsqu’une page de l’instance de création est demandée à partir d’un appareil mobile.
