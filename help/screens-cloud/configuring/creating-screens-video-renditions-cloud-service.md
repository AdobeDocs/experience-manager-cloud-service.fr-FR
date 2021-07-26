---
title: Création de rendus vidéo Screens dans Screens en tant que Cloud Service
description: Cette page décrit comment créer des rendus vidéo Screens en tant que Cloud Service dans Screens.
source-git-commit: b8691bb77079eeb7efd141ce89c44c5a312262b3
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 1%

---


# Création de rendus vidéo Screens dans Screens en tant que Cloud Service {#creating-screens-video-renditions}

## Présentation {#introduction}

Ce guide explique comment créer des rendus vidéo utilisés dans les lecteurs Screens.

>[!IMPORTANT]
>Les étapes mises en évidence dans cette section doivent être configurées si vous envisagez d’utiliser des vidéos dans les canaux Screens.

## Procédure de création de rendus vidéo Screens en tant que Cloud Service {#steps-creating-screens-video-renditions}

1. Accédez aux canaux dans l’interface utilisateur de Screens Cloud.
1. Cliquez sur Adobe Experience Manager dans le coin supérieur gauche pour accéder au fournisseur de contenu Screens, c’est-à-dire AEM en tant que Cloud Service.
1. Cliquez maintenant sur la section Outils dans la navigation principale, puis sur &quot;Ressources&quot; et ensuite sur &quot;Profils de traitement&quot;.

1. Cliquez sur &quot;Créer&quot; pour créer un profil de traitement.
1. Attribuez un nom tel que &quot;ScreensProcessingProfile&quot;.
1. Accédez à l’onglet Vidéo pour ajouter un codage vidéo et cliquez sur &quot;Ajouter nouveau&quot;.


   >[!IMPORTANT]
   >Veillez à utiliser le nom du codage commençant par &quot;screens-&quot;. Seuls ces rendus vidéo seront considérés comme lisant l’expérience vidéo dans Screens en tant que Cloud Service. Saisissez le débit qui convient à vos vidéos (2 500 Kbit/s pour une vidéo de 720 px et 5 000 Kbit/s pour une vidéo de 1 080 px).

   >[!NOTE]
   >Plusieurs rendus vidéo peuvent être ajoutés avec des valeurs de largeur/hauteur/débit/débit variables en fonction de vos besoins, mais n’oubliez pas que tous les écrans - rendus seront téléchargés par les appareils Screens, même si l’appareil ne lit que le rendu vidéo.

1. Cliquez sur Enregistrer.

1. Sélectionnez le profil de traitement et cliquez sur &quot;Appliquer le profil au(x) dossier(s)&quot;

1. Sélectionnez le ou les dossiers dans lesquels les vidéos Screens sont conservées et cliquez sur Appliquer .

1. Vous pouvez créer plusieurs profils de traitement et les appliquer aux dossiers correspondants, de sorte que les vidéos contenues dans ces dossiers obtiennent les rendus vidéo spécifiques.

1. Lorsque vous chargez des vidéos dans le dossier où le profil de traitement est appliqué, les vidéos sont traitées et les rendus configurés sont créés, qui seront utilisés par les périphériques Screens pour lire les vidéos.

