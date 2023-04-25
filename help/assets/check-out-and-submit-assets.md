---
title: Archivage et extraction de fichiers dans  [!DNL Assets]
description: Découvrez comment extraire les ressources pour modification et les archiver à nouveau une fois les modifications effectuées.
contentOwner: AG
feature: Asset Management
role: User
exl-id: adb94a31-d949-4f4a-89bc-44f1b4f67e14
source-git-commit: 034899c2a717fafdc50cc269d6db3feb77d907c5
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 95%

---

# Archivage et extraction de fichiers dans la gestion des ressources numériques [!DNL Experience Manager] {#check-in-and-check-out-files-in-assets}

[!DNL Adobe Experience Manager Assets] permet d’extraire des ressources pour les modifier et de les ré-archiver après y avoir apporté les modifications. Après avoir extrait une ressource, vous seul pouvez la modifier, l’annoter, la publier, la déplacer ou la supprimer. Le fait d’extraire une ressource entraîne son verrouillage. Les autres utilisateurs ne peuvent effectuer aucune de ces opérations sur la ressource tant que vous ne l’avez pas archivée dans [!DNL Assets]. Toutefois, ils peuvent modifier les métadonnées de la ressource verrouillée.

Vous avez besoin d’un accès en écriture à ces ressources pour être en mesure de les extraire ou de les archiver.

Cette caractéristique permet d’empêcher les autres utilisateurs d’écraser les modifications apportées par un auteur lorsque plusieurs utilisateurs issus de plusieurs équipes collaborent à la modification des workflows.

## Extraction de ressources {#checking-out-assets}

1. Dans l’interface utilisateur d’[!DNL Assets], sélectionnez la ressource que vous souhaitez extraire. Vous pouvez également sélectionner plusieurs ressources à extraire.

1. Dans la barre d’outils, cliquez sur **[!UICONTROL Extraction]**. L’option **[!UICONTROL Extraction]** passe en **[!UICONTROL Archivage]**.
Pour vérifier si d’autres utilisateurs peuvent modifier la ressource que vous avez extraite, connectez-vous comme un utilisateur différent. L’icône ![icône en forme de verrou pour l’extraction](assets/do-not-localize/checkout_lock.png) s’affiche sur la miniature de la ressource que vous avez extraite.

   ![icône d’extraction en mode Carte](assets/checkout-icon-card-view.png)

   Sélectionnez la ressource. Notez que la barre d’outils n’affiche aucune option vous permettant de modifier, d’annoter, de publier ou de supprimer la ressource.

   ![chlimage_1-472](assets/checkout-asset-toolbar-options.png)

   Pour modifier les métadonnées de la ressource verrouillée, cliquez sur **[!UICONTROL Afficher les propriétés]**.

1. Cliquez sur **[!UICONTROL Modifier]** pour ouvrir la ressource en mode d’édition.

1. Modifiez la ressource et enregistrez les modifications. Par exemple, recadrez l’image et enregistrez-la. Vous pouvez également choisir d’annoter ou de publier la ressource.

1. Sélectionnez la ressource modifiée dans l’interface [!DNL Assets], puis cliquez sur **[!UICONTROL Archiver]** dans la barre d’outils. La ressource modifiée est archivée dans [!DNL Assets] et peut être modifiée par les autres utilisateurs.

## Archivage forcé {#forced-check-in}

Les administrateurs peuvent archiver les ressources extraites par d’autres utilisateurs.

1. Connectez-vous à [!DNL Assets] en tant qu’administrateur.
1. Dans l’interface utilisateur d’[!DNL Assets], sélectionnez une ou plusieurs ressources extraites par d’autres utilisateurs.

   ![chlimage_1-476](assets/chlimage_1-476.png)

1. Dans la barre d’outils, cliquez sur **[!UICONTROL Verrouillage de version]**. La ressource est à nouveau archivée et disponible pour modification pour d’autres utilisateurs.

## Bonnes pratiques et restrictions {#tips-limitations}

* Il est possible de supprimer un *dossier* contenant des fichiers de ressources extraits. Avant de supprimer un dossier, assurez-vous qu’aucune ressource numérique n’ait été extraite par les utilisateurs.

>[!MORELIKETHIS]
>
>* [Présentation de l’archivage et de l’extraction dans l’appli de bureau [!DNL Experience Manager]  ](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=fr#how-app-works2)
>* [Tutoriel vidéo pour comprendre l’archivage et l’extraction [!DNL Assets]](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/collaboration/check-in-and-check-out.html?lang=fr)

