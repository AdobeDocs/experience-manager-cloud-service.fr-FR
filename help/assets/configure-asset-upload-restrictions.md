---
title: Configuration des restrictions de chargement des ressources
description: 'Configurez Adobe Experience Manager Assets pour restreindre le type de ressources que les utilisateurs peuvent charger en fonction du type MIME. Cela permet d’éviter les chargements accidentels de fichiers au format indésirable. '
source-git-commit: 3be29e4f76b53b4be7815e50ec42c627fec84b68
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 3%

---

# Configuration des restrictions de chargement des ressources {#configure-asset-upload-restrictions}

Vous pouvez configurer Adobe Experience Manager Assets pour restreindre le type de ressources que les utilisateurs peuvent charger en fonction du type MIME.

>[!IMPORTANT]
>
>Par défaut, Experience Manager Assets permet aux utilisateurs de charger des ressources de tous les types MIME. Cependant, vous pouvez configurer les paramètres pour empêcher les utilisateurs de charger des fichiers de types MIME spécifiques uniquement.

## Conditions préalables {#prerequisites-asset-upload-restrictions}

Vous devez disposer de droits d’administrateur pour configurer les restrictions de chargement des ressources.

## Application de restrictions aux chargements de ressources {#apply-restrictions-asset-uploadsssssss}

Pour configurer [!DNL Experience Manager] pour empêcher les utilisateurs de charger des fichiers de types MIME spécifiques :

1. Accédez à **[!UICONTROL Outils > Ressources > Configurations des ressources]**.

1. Cliquez sur **[!UICONTROL Restrictions de téléchargement]**.

1. Cliquez sur **[!UICONTROL Ajouter]** pour définir les types MIME autorisés.

1. Spécifiez le type MIME dans la zone de texte. Vous pouvez cliquer sur **[!UICONTROL Ajouter]** pour spécifier d’autres types MIME autorisés. Vous pouvez également cliquer sur ![icône de suppression](assets/delete-icon.svg) pour supprimer tout type MIME de la liste.

1. Cliquez sur **[!UICONTROL Enregistrer]**.

**Exemple 1 : Autorisation du chargement de toutes les images et fichiers de PDF vers Experience Manager Assets**

Pour permettre le téléchargement d’images dans tous les formats et fichiers de PDF vers Experience Manager Assets, procédez comme suit :

![Restrictions de chargement des ressources](assets/asset-upload-restrictions.png)

`image/*` car le type MIME permet de télécharger des images dans tous les formats. `application/pdf` car le type MIME permet le chargement de fichiers de PDF vers Experience Manager Assets.

**Exemple 2 : Autorisation du téléchargement de formats d’image spécifiques vers Experience Manager Assets**

Pour ajouter des formats d’image spécifiques aux types MIME autorisés et limiter le téléchargement de tous les autres formats de ressource, procédez comme suit :

![Restrictions des ressources](assets/asset-restrictions.png)

En fonction des paramètres décrits dans l’image, vous pouvez télécharger des images aux formats .JPG, .PNG et .GIF vers Experience Manager Assets.




