---
title: Création de rendus vidéo Screens dans Screens en tant que Cloud Service
description: Cette page décrit comment créer des rendus vidéo Screens en tant que Cloud Service dans Screens.
source-git-commit: ec939ac6a91523a9ba64a555943eba8e6da071eb
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 1%

---


# Création de rendus vidéo Screens dans Screens en tant que Cloud Service {#creating-screens-video-renditions}

## Présentation {#introduction}

Ce guide explique comment créer des rendus vidéo utilisés dans les lecteurs Screens.

>[!IMPORTANT]
>Les étapes mises en évidence dans cette section doivent être configurées si vous envisagez d’utiliser des vidéos dans les canaux Screens.

## Procédure de création de rendus vidéo Screens en tant que Cloud Service {#steps-creating-screens-video-renditions}

1. Accédez à votre canal dans le fournisseur de contenu Screens.

   >[!NOTE]
   >Pour plus d’informations, voir [Utilisation du fournisseur de contenu Screens](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/configure-screens-cloud/using-screens-content-provider.html?lang=en#screens-content-provider) .

1. Cliquez sur la section Outils de la barre de navigation de gauche, puis sur **Ressources** et cliquez sur **Profils de traitement**.

   ![](/help/screens-cloud/assets/configure/screens-cp-3.png)

1. Cliquez sur **Créer** pour créer un profil de traitement.

   ![](/help/screens-cloud/assets/configure/screens-video-2.png)

1. Saisissez le **nom**, par exemple **ScreensProcessingProfile**.

   ![](/help/screens-cloud/assets/configure/screens-video-3.png)

1. Accédez à l’onglet **Vidéo** pour ajouter un codage vidéo, puis cliquez sur **Ajouter nouveau**.


   >[!IMPORTANT]
   >Veillez à utiliser le nom du codage commençant par &quot;screens-&quot;. Seuls ces rendus vidéo seront considérés comme lisant l’expérience vidéo dans Screens en tant que Cloud Service. Saisissez le débit qui convient à vos vidéos (2 500 Kbit/s pour une vidéo de 720 px et 5 000 Kbit/s pour une vidéo de 1 080 px).

   >[!NOTE]
   >Plusieurs rendus vidéo peuvent être ajoutés avec des valeurs de largeur/hauteur/débit/débit variables en fonction de vos besoins, mais n’oubliez pas que tous les écrans - rendus seront téléchargés par les appareils Screens, même si l’appareil ne lit que le rendu vidéo.

1. Cliquez sur Enregistrer.

1. Sélectionnez le profil de traitement et cliquez sur &quot;Appliquer le profil au(x) dossier(s)&quot;

1. Sélectionnez le ou les dossiers dans lesquels les vidéos Screens sont conservées et cliquez sur Appliquer .

1. Vous pouvez créer plusieurs profils de traitement et les appliquer aux dossiers correspondants, de sorte que les vidéos contenues dans ces dossiers obtiennent les rendus vidéo spécifiques.

1. Lorsque vous chargez des vidéos dans le dossier où le profil de traitement est appliqué, les vidéos sont traitées et les rendus configurés sont créés, qui seront utilisés par les périphériques Screens pour lire les vidéos.

