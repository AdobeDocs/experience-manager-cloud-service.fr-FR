---
title: Configurer des restrictions de téléchargement des ressources
description: Configurez Adobe Experience Manager Assets de façon à restreindre le type de ressources que les utilisateurs peuvent télécharger en fonction du type MIME. Cela permet d’éviter les téléchargements accidentels de fichiers à un format indésirable ou malveillants.
exl-id: 094c31f3-f2e9-4b44-9995-c76fb78ca458
source-git-commit: d2d0d8b0d484d2e5cd2bf44449e7d71d3da98eea
workflow-type: ht
source-wordcount: '333'
ht-degree: 100%

---

# Configurer des restrictions de téléchargement des ressources {#configure-asset-upload-restrictions}

Vous pouvez configurer Adobe Experience Manager Assets de façon à restreindre le type de ressources que les utilisateurs peuvent télécharger en fonction du type MIME.

>[!IMPORTANT]
>
>Par défaut, Experience Manager Assets permet aux utilisateurs de télécharger des ressources quel que soit leur type MIME. Cependant, vous pouvez définir les paramètres afin d’empêcher les utilisateurs de télécharger des fichiers disposant de types MIME spécifiques.

## Prérequis {#prerequisites-asset-upload-restrictions}

Vous devez disposer de droits d’administrateur pour configurer les restrictions de téléchargement de ressources.

## Appliquer des restrictions aux téléchargements de ressources {#apply-restrictions-asset-uploadsssssss}

Pour configurer [!DNL Experience Manager] de façon à empêcher les utilisateurs de télécharger des fichiers de types MIME spécifiques, procédez comme suit :

1. Accédez à **[!UICONTROL Outils > Ressources > Configurations des ressources]**.

1. Cliquez sur **[!UICONTROL Restrictions de téléchargement]**.

1. Cliquez sur **[!UICONTROL Ajouter]** pour définir les types MIME autorisés.

1. Spécifiez le type MIME dans la zone de texte. Cliquez à nouveau sur **[!UICONTROL Ajouter]** pour renseigner d’autres types MIME autorisés. Vous pouvez également cliquer sur ![icône de suppression](assets/delete-icon.svg) pour supprimer un type MIME de la liste.

1. Cliquez sur **[!UICONTROL Enregistrer]**.

**Exemple 1 : autoriser le téléchargement de tous les fichiers images et PDF sur Experience Manager Assets**

Pour autoriser le téléchargement d’images dans tous les formats et de fichiers PDF sur Experience Manager Assets, définissez les paramètres suivants :

![Restrictions de téléchargement des ressources](assets/asset-upload-restrictions.png)

`image/*` : ce type MIME permet de télécharger des images dans tous les formats. `application/pdf` : ce type MIME permet de télécharger des fichiers PDF sur Experience Manager Assets.

Si vous tentez de télécharger un fichier qui n’est pas inclus dans la liste des types MIME autorisés, Experience Manager Assets affiche le message d’erreur suivant :

![Fichiers restreints](assets/asset-upload-restricted-files.png)

`Screen Recording 2022-08-31 at 3.36.09 PM.mov` fait référence à un nom de fichier qui n’est pas inclus dans les types MIME autorisés.

**Exemple 2 : autoriser le téléchargement de formats d’image spécifiques sur Experience Manager Assets**

Pour ajouter des formats d’image spécifiques aux types MIME autorisés et interdire le téléchargement de tous les autres formats de ressource, définissez les paramètres suivants :

![Restrictions des ressources](assets/asset-restrictions.png)

En définissant les paramètres renseignés sur l’image, vous pouvez télécharger des images aux formats .JPG, .PNG et .GIF sur Experience Manager Assets.
