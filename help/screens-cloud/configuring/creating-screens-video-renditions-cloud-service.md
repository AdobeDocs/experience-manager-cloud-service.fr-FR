---
title: Création de rendus vidéo dans Screens as a Cloud Service
description: Cette page décrit comment créer des rendus vidéo dans Screens as a Cloud Service.
exl-id: a9c46036-cd29-47fa-81d9-c865cf22c98a
feature: Administering Screens
role: Admin, Developer, User
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 91%

---

# Création de rendus vidéo dans Screens as a Cloud Service {#creating-screens-video-renditions}

## Présentation {#introduction}

Cette section décrit comment créer des rendus vidéo utilisés dans les lecteurs Screens.

>[!IMPORTANT]
>Si vous envisagez d’utiliser des vidéos dans les canaux Screen, les étapes mises en évidence dans cette section doivent être configurées.

## Procédure de création de rendus vidéo dans Screens as a Cloud Service {#steps-creating-screens-video-renditions}

Pour créer des rendus vidéo dans Screens as a Cloud Service à partir du fournisseur de contenu Screens, procédez comme suit :

1. Accédez à votre canal dans le fournisseur de contenu Screens.

   >[!NOTE]
   >Pour plus d’informations, voir [Utilisation du fournisseur de contenu Screens](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/configure-screens-cloud/using-screens-content-provider.html?lang=fr#screens-content-provider).

1. Cliquez sur la section Outils de la barre de navigation de gauche, puis sur **Ressources** et sur **Profils de traitement**.

   ![Cliquez sur Profils de traitement](/help/screens-cloud/assets/configure/screens-cp-3.png)

1. Cliquez sur **Créer** pour créer un profil de traitement.

   ![Clic sur Créer](/help/screens-cloud/assets/configure/screens-video-2.png)

1. Saisissez le **nom**, par exemple **ScreensProcessingProfile**.

   ![Boîte de dialogue Profil de traitement présentant le champ Nom en surbrillance.](/help/screens-cloud/assets/configure/screens-video-3.png)

1. Accédez à l’onglet **Vidéo** pour ajouter un codage vidéo, puis cliquez sur **Ajouter**.

   ![Boîte de dialogue Profil de traitement présentant le bouton Ajouter nouveau en surbrillance.](/help/screens-cloud/assets/configure/screens-video-4a.png)

1. Saisissez le **Nom de codage**, par exemple **screens-fullhd**, et le **Débit** sur **2500**.

   ![Boîte de dialogue Profil de traitement affichant le bouton Enregistrer en surbrillance.](/help/screens-cloud/assets/configure/screens-video-4.png)

   >[!IMPORTANT]
   >Utilisez le nom de codage qui commence par « screens- ». Seuls ces rendus vidéo sont considérés comme lisant l’expérience vidéo dans Screens as a Cloud Service. Saisissez le débit qui fonctionne avec vos vidéos (2 500 Kbit/s pour une vidéo de 720 px et 5 000 Kbit/s pour une vidéo de 1 080 px).

   >[!NOTE]
   >Vous pouvez ajouter plusieurs rendus vidéo avec des valeurs de largeur/hauteur/débit variables pour utiliser vos vidéos. N’oubliez pas que tous les rendus Screens seront téléchargés par les appareils Screens, même si l’appareil ne lit que le rendu vidéo.

1. Cliquez sur **Enregistrer**.

1. Sélectionnez le profil de traitement et cliquez sur **Appliquer le profil aux dossiers**.

   ![Appliquer le profil aux dossiers](/help/screens-cloud/assets/configure/screens-video-5.png)

1. Sélectionnez les dossiers dans lesquels les vidéos Screens sont conservées et cliquez sur **Appliquer**.

   ![Clic sur Appliquer](/help/screens-cloud/assets/configure/screens-video-6.png)

   >[!NOTE]
   >
   >* Vous pouvez créer plusieurs profils de traitement et les appliquer aux dossiers correspondants, de sorte que les vidéos contenues dans ces dossiers obtiennent les rendus vidéo spécifiques.
   >* Lorsque vous chargez des vidéos dans le dossier où un profil de traitement est appliqué, ces dernières sont traitées. Les rendus configurés sont créés et utilisés par les appareils Screens pour lire les vidéos.
