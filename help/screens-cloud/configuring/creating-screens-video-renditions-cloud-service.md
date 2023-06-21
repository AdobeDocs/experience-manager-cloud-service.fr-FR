---
title: Création de rendus vidéo dans Screens as a Cloud Service
description: Cette page décrit comment créer des rendus vidéo dans Screens as a Cloud Service.
exl-id: a9c46036-cd29-47fa-81d9-c865cf22c98a
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 86%

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
   >Pour plus d’informations, voir [Utilisation du fournisseur de contenu Screens](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/configure-screens-cloud/using-screens-content-provider.html?lang=fr#screens-content-provider).

1. Cliquez sur la section Outils de la barre de navigation de gauche, puis sur **Ressources** et sur **Profils de traitement**.

   ![](/help/screens-cloud/assets/configure/screens-cp-3.png)

1. Cliquez sur **Créer** pour créer un profil de traitement.

   ![](/help/screens-cloud/assets/configure/screens-video-2.png)

1. Saisissez le **nom**, par exemple **ScreensProcessingProfile**.

   ![](/help/screens-cloud/assets/configure/screens-video-3.png)

1. Accédez à l’onglet **Vidéo** pour ajouter un codage vidéo, puis cliquez sur **Ajouter nouveau**.

   ![](/help/screens-cloud/assets/configure/screens-video-4a.png)

1. Saisissez le **Nom de codage** tel que, **screens-fullhd** et le **Débit** **2500**.

   ![](/help/screens-cloud/assets/configure/screens-video-4.png)

   >[!IMPORTANT]
   >Veillez à utiliser le nom du codage commençant par &quot;screens-&quot;. Seuls ces rendus vidéo sont considérés comme lisant l’expérience vidéo dans Screens as a Cloud Service. Saisissez le débit qui fonctionne avec vos vidéos (2 500 Kbit/s pour une vidéo de 720 px et 5 000 Kbit/s pour une vidéo de 1 080 px).

   >[!NOTE]
   >Vous pouvez ajouter plusieurs rendus vidéo avec des valeurs de largeur/hauteur/débit variables pour utiliser vos vidéos. Tous les écrans et rendus sont téléchargés par les appareils Screens, même si l’appareil lit uniquement le rendu vidéo.

1. Cliquez sur **Enregistrer**.

1. Sélectionnez le profil de traitement et cliquez sur **Appliquer le profil au(x) dossier(s)**.

   ![](/help/screens-cloud/assets/configure/screens-video-5.png)

1. Sélectionnez le ou les dossiers dans lesquels les vidéos Screens sont conservées et cliquez sur **Appliquer**.

   ![](/help/screens-cloud/assets/configure/screens-video-6.png)

   >[!NOTE]
   >* Vous pouvez créer plusieurs profils de traitement et les appliquer aux dossiers correspondants, de sorte que les vidéos contenues dans ces dossiers obtiennent les rendus vidéo spécifiques.
   >* Lorsque vous chargez des vidéos dans le dossier où le profil de traitement est appliqué, les vidéos sont traitées et les rendus configurés sont créés, qui sont ensuite utilisés par les périphériques Screens pour lire les vidéos.
