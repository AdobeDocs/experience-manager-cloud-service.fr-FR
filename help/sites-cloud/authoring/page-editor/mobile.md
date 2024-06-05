---
title: Création d’une page pour les appareils mobiles
description: Lors de la création pour les appareils mobiles, vous pouvez basculer entre plusieurs émulateurs pour voir ce que l’utilisateur final voit.
exl-id: fabd4468-3304-402f-9522-342da3bbae94
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 100%

---

# Création d’une page pour les appareils mobiles {#authoring-a-page-for-mobile-devices}

Les pages d’Adobe Experience Manager reposent sur une mise en page réactive. La [mise en page réactive](/help/sites-cloud/authoring/page-editor/responsive-layout.md) adapte automatiquement votre contenu à l’appareil cible, éliminant ainsi la nécessité de créer du contenu pour des appareils spécifiques.

Lorsque vous créez une page mobile, celle-ci est affichée d’une manière qui émule l’appareil mobile. Lors de la création de la page, vous pouvez basculer entre plusieurs émulateurs pour voir ce que la personne utilisatrice finale voit lorsqu’elle accède à la page.

Les périphériques sont regroupés dans les catégories fonctionnalité, intelligent et tactile selon les capacités des périphériques à effectuer le rendu d’une page. Lorsque la personne utilisatrice finale accède à une page mobile, AEM détecte le périphérique et envoie la représentation qui correspond à son groupe de périphériques.

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
1. [Modifiez la disposition réactive](/help/sites-cloud/authoring/page-editor/responsive-layout.md) de la page et de ses composants en fonction de l’appareil sélectionné.

La page ressemble à ce qui suit :

![Exemple de mobile](/help/sites-cloud/authoring/assets/mobile.png)

>[!NOTE]
>
>Les émulateurs sont désactivés lorsqu’une page de l’instance de création est demandée à partir d’un appareil mobile.
