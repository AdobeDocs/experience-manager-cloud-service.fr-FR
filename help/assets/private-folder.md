---
title: Dossiers privés pour le partage de ressources
description: Découvrez comment créer un dossier privé dans le [!DNL Adobe Experience Manager Assets] et le partager avec d’autres utilisateurs et leur attribuer divers privilèges.
contentOwner: Vishabh Gupta
role: User
feature: Collaboration
exl-id: d48f6daf-af81-4024-bff2-e8bf6d683b0c
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 8%

---

# Dossier privé dans [!DNL Adobe Experience Manager Assets] {#private-folder}

Vous pouvez créer un dossier privé dans le [!DNL Adobe Experience Manager Assets] l’interface utilisateur qui vous est réservée. Vous pouvez partager ce dossier privé avec d’autres utilisateurs et leur attribuer divers privilèges. Selon le niveau de privilège que vous affectez, les utilisateurs peuvent effectuer différentes tâches dans le dossier, par exemple consulter des ressources du dossier ou les modifier.

>[!NOTE]
>
>Le dossier privé comporte au moins un membre avec le rôle Propriétaire.
>
>Pour créer un dossier privé, vous devez `Read` et `Modify` autorisations sur le dossier parent sous lequel vous créez un dossier privé. Si vous n’êtes pas administrateur, ces autorisations ne sont pas activées par défaut sur `/content/dam`. Dans ce cas, vous devez d’abord obtenir ces autorisations pour votre identifiant utilisateur/groupe avant de tenter de créer des dossiers privés.

## Créer et partager un dossier privé  {#create-share-private-folder}

Pour créer et partager un dossier privé :

1. Dans le [!DNL Assets] , cliquez sur **[!UICONTROL Créer]** dans la barre d’outils, puis sélectionnez **[!UICONTROL Dossier]** dans le menu.

   ![Création d’un dossier de ressources](assets/create-folder.png)

1. Dans le **[!UICONTROL Créer un dossier]** , saisissez une `Title` et `Name` (facultatif) pour le dossier .

   Sélectionnez la **[!UICONTROL Privé]** , puis cliquez sur **[!UICONTROL Créer]**.

   ![chlimage_1-413](assets/create-private-folder.png)

   Un dossier privé est créé. Vous pouvez désormais [ajout de ressources](add-assets.md#upload-assets) dans le dossier et partagez le dossier avec d’autres utilisateurs ou groupes. Le dossier n’est visible par aucun autre utilisateur tant que vous ne l’avez pas partagé et que vous ne lui avez pas attribué des privilèges.

1. Pour partager le dossier, sélectionnez-le, puis cliquez sur **[!UICONTROL Propriétés]** dans la barre d’outils.

1. Dans le **[!UICONTROL Propriétés du dossier]** , sélectionnez un utilisateur ou un groupe dans la **[!UICONTROL Ajouter un utilisateur]** liste, affecter un rôle (`Viewer`, `Editor`ou `Owner`) dans votre dossier privé, puis cliquez sur **[!UICONTROL Ajouter]**.

   ![assign-user-group](assets/assign-permissions-private-folder.png)

   Vous pouvez affecter différents rôles, tels que `Editor`, `Owner`ou `Viewer` à l’utilisateur avec lequel vous partagez le dossier. Si vous affectez une `Owner` rôle de l’utilisateur, l’utilisateur a `Editor` sur le dossier . En outre, il peut partager le dossier avec d’autres utilisateurs. Si vous affectez une `Editor` , l’utilisateur peut modifier les ressources de votre dossier privé. Si vous attribuez un rôle de visionneuse, l’utilisateur ne peut afficher que les ressources de votre dossier privé.

   >[!NOTE]
   >
   >Le dossier privé comporte au moins un membre avec `Owner` rôle. Par conséquent, l’administrateur ne peut pas supprimer tous les membres propriétaires d’un dossier privé. Toutefois, pour supprimer les propriétaires existants (et l’administrateur lui-même) du dossier privé, l’administrateur doit ajouter un autre utilisateur en tant que propriétaire.

1. Cliquez sur **[!UICONTROL Enregistrer et fermer]**. Selon le rôle que vous attribuez, l’utilisateur se voit attribuer un ensemble de privilèges sur votre dossier privé lorsqu’il se connecte à [!DNL Assets].
1. Cliquez sur **[!UICONTROL OK]** pour fermer le message de confirmation.
1. L’utilisateur avec lequel vous partagez le dossier reçoit une notification de partage dans son interface utilisateur.

1. Cliquez sur [!UICONTROL Notifications] pour ouvrir une liste de notifications.

   ![notification](assets/notification-icon.png)

1. Cliquez sur l’entrée du dossier privé partagé par l’administrateur pour ouvrir le dossier.

## Suppression de dossiers privés {#delete-private-folder}

Vous pouvez supprimer un dossier en le sélectionnant et en sélectionnant [!UICONTROL Supprimer] à partir du menu supérieur ou à l’aide de la touche Retour arrière de votre clavier.

![option de suppression dans le menu supérieur](assets/delete-option.png)

>[!CAUTION]
>
>Si vous supprimez un dossier privé de CRXDE Lite, les groupes d’utilisateurs redondants restent dans le référentiel.

>[!NOTE]
>
>Si vous supprimez un dossier à l’aide de la méthode ci-dessus de l’interface utilisateur, les groupes d’utilisateurs associés sont également supprimés.
>
>Cependant, les groupes d’utilisateurs redondants, inutilisés et générés automatiquement existants peuvent être supprimés du référentiel à l’aide de la variable `clean` dans JMX dans l’instance de création (`http://[server]:[port]/system/console/jmx/com.day.cq.dam.core.impl.team%3Atype%3DClean+redundant+groups+for+Assets`).
