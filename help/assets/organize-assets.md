---
title: Organisez vos ressources numériques.
description: Organisez vos ressources numériques, images, fichiers, dossiers, etc. à l’aide de Experience Manager.
contentOwner: AG
feature: Asset Management, Search
role: User
exl-id: 6b3ce076-2dd9-47f6-9b68-4fa52bfedd42
source-git-commit: 843d6660fc2a2048d138601b4b74ee9f2faa54c9
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 5%

---

# Organisez vos ressources numériques. {#organize-digital-assets}

Toutes les ressources numériques, les métadonnées et le contenu des documents Microsoft® Office et PDF sont extraits et peuvent faire l’objet de recherches. La recherche permet un filtrage sophistiqué des ressources et respecte entièrement les autorisations appropriées. Les métadonnées sont traitées en détail dans la section Métadonnées dans la gestion des actifs numériques.

[!DNL Experience Manager Assets] prend en charge plusieurs méthodes d’organisation du contenu. Vous pouvez les organiser de manière hiérarchique à l’aide de dossiers ou les organiser de manière ad hoc et non ordonnée, par exemple à l’aide de balises. Les utilisateurs peuvent modifier des balises dans l’éditeur de ressources de gestion des actifs numériques où s’affichent des sous-ressources, des rendus et des métadonnées.

<!-- Commenting to pull down the existing content before applying changes wrt CQDOC-15930
## Create folders {#create-folders}

When organizing a collection of assets, for example, all *Nature* images, you can create folders to keep them together. You can use folders to categorize and organize your assets. [!DNL Assets] does not require you to organize assets in folders to work better.

>[!NOTE]
>
>Sharing an Assets folder (in Marketing Cloud) of the type `sling:OrderedFolder`, is not supported. If you want to share a folder, do not select Ordered when creating a folder.

1. Navigate to the place in your digital assets folder where you want to create a new folder.
1. In the menu, click **[!UICONTROL Create]**. Select **[!UICONTROL New Folder]**.
1. In the **[!UICONTROL Title]** field, provide a folder name. By default, DAM uses the title that you provided as the folder name. Once the folder is created, you can override the default and specify another folder name.
1. Click **[!UICONTROL Create]**. Your folder is displayed in the digital assets folder.

## Add CUG properties to folders {#add-cug-properties-to-folders}

You can limit who can access certain folders in Assets by making the folder part of a closed user group (CUG). To make a folder part of a CUG:

1. In Assets, right-click the folder you want to add closed user group properties for and select **Properties**.  
1. Click the **CUG** tab.
1. Select the **Enabled** check box to make the folder and its assets available only to a closed user group.  
1. Browse to the login page, if there is one, to add that information. Add admitted groups by clicking **Add item**. If necessary, add the realm. Click **OK** to save your changes.

## Use tags to organize assets {#use-tags-to-organize-assets}

You can use folders or tags or both to organize assets. Adding tags to assets makes them more easy to retrieve during a search. To add tags to an asset, follow these steps:

1. In the Digital Asset Manager, double-click the asset to open it.
1. In the **Tags** area, open the menu to reveal the available tags. Select tags as appropriate. To delete a tag, hover the pointer over the tag and click `X` to delete it.
1. Click **Save** to save any tags you added.

Date24/08/2021
-->

## Organisation des ressources dans des dossiers {#organize-using-folders}

La méthode la plus simple pour organiser les ressources consiste à les enregistrer dans des dossiers. Cela revient à organiser les fichiers dans des dossiers de votre système de fichiers local. Pour plus d’informations sur la création et la gestion des dossiers, voir [Gestion des ressources](manage-digital-assets.md). La manière dont vous nommez les fichiers et les dossiers, organisez les sous-dossiers et gérez les fichiers dans ces dossiers peut avoir un impact significatif sur la manière dont ces ressources sont traitées. Grâce à des stratégies d’attribution de noms de fichiers et de dossiers cohérentes et appropriées, ainsi qu’à de bonnes pratiques de métadonnées, vous pouvez tirer le meilleur parti de votre référentiel de ressources numériques.

* En règle générale, votre référentiel de ressources numériques est toujours en croissance. Il est donc important de formaliser l’utilisation des métadonnées, la structure des dossiers et l’attribution de noms aux fichiers au début du cycle de création de contenu.
* Utilisez les dossiers uniquement pour imposer une structure de stockage cohérente pour vos ressources numériques. Cette cohérence aide votre processus et gère mieux vos ressources. Par exemple, les ressources placées dans les types de dossiers suivants peuvent vous aider à séparer les ressources :

   * **Dossiers** de développement : contient les ressources numériques que vous utilisez actuellement.
   * **Dossiers** clients : contient des ressources numériques en fonction des clients ou des noms de projet.
   * **Dossiers** Principal : contient des ressources numériques sources originales.
   * **Dossiers** de rendu : contient des rendus et des copies des ressources numériques sources originales.
   * **Dossiers de taille de fichier** : contient des ressources numériques en fonction des tailles de fichier petite, moyenne ou volumineuse.
   * **Dossiers intermédiaires** : contient des ressources numériques prêtes à être publiées sur votre site web.
   * **Dossiers de type MIME** : contient des ressources numériques qui sont spécifiques à des types MIME tels que des images, des documents et des fichiers multimédia.
   * **Dossiers d’archives** : contient des ressources numériques retirées.
   * **Dossiers basés sur des dates** : contient des ressources numériques en fonction d’une date de création ou d’une date de dernière modification.

* Créez un répertoire de dossiers susceptibles de ne pas changer, de sorte que toute personnalisation ou automatisation continue de fonctionner. Par exemple, les profils de traitement affectés continuent à fonctionner.
* Si une ressource est déjà publiée, utilisez [!DNL Experience Manager] pour la déplacer vers un autre dossier et la republier à partir de son nouvel emplacement. L’emplacement de la ressource publiée d’origine est toujours disponible avec la ressource qui vient d’être republiée. La ressource publiée d’origine, cependant, est *perdue* par [!DNL Experience Manager] et ne peut pas être annulée. Par conséquent, il est recommandé d’abord d’annuler la publication d’une ressource, puis de la déplacer vers un autre dossier.

## Organisation des ressources à l’aide de balises {#use-tags-to-organize-assets}

À l’aide de balises, en tant que métadonnées, vous pouvez facilement rechercher des ressources, créer des collections à l’aide des résultats de recherche, améliorer le classement de certaines ressources et appliquer des algorithmes d’IA d’Adobe Sensei pour la découverte de ressources.

[!DNL Adobe Experience Manager Assets] utilise un algorithme d’auto-apprentissage pour créer des balises hautement descriptives qui vous permettent de trouver la ressource appropriée en quelques clics seulement. Le balisage intelligent utilise Adobe Sensei, l’intelligence artificielle et la structure d’apprentissage automatique, qui peuvent être formés pour reconnaître et appliquer des balises standard et commerciales à l’imagerie. Les balises intelligentes peuvent également identifier le contenu, les mots individuels ou les expressions et appliquer automatiquement des balises descriptives aux ressources.

Pour plus d’informations, voir les articles suivants :

* [Modification des métadonnées de ressource](meta-edit.md)
* [Balises intelligentes dans Assets](smart-tags.md)

## Organisation en tant que collections {#organize-as-collections}

Avec les collections de ressources dans [!DNL Experience Manager Assets], vous pouvez rationaliser la possibilité de créer, modifier et partager des ressources entre les utilisateurs. Créez plusieurs types de collections en fonction de leur utilisation, y compris des collections qui contiennent une liste de référence statique de ressources, dossiers et collections, ainsi que des collections qui extraient des ressources en fonction de critères de recherche. Vous pouvez créer des collections avec des ressources provenant de différents emplacements et les partager avec plusieurs utilisateurs disposant de différents niveaux d’accès, d’affichage et de modification des privilèges.

Pour plus d’informations, voir [Gestion des collections](manage-collections.md)


## Utilisation de profils pour organiser vos ressources {#organize-to-use-profiles}

Un profil de traitement contient des commandes [!DNL Assets] de traitement qui s’appliquent aux ressources qui sont chargées dans des dossiers prédéfinis. Les profils sont utilisés pour automatiser le traitement du contenu d’un dossier ou de ressources fraîchement chargées. Vous pouvez utiliser des profils pour mieux organiser vos ressources.

La normalisation de l’utilisation des métadonnées, de l’attribution des noms de fichiers et de la structure des dossiers vous permet d’appliquer des profils de traitement à vos dossiers avec une précision et une cohérence accrues.

>[!MORELIKETHIS]
>
>* [Utilisation des microservices de ressources et des profils de traitement](asset-microservices-configure-and-use.md)
>* [Profils de métadonnées](metadata-profiles.md)
>* [Profils vidéo](/help/assets/dynamic-media/video-profiles.md)
>* [Profils d’image Dynamic Media](/help/assets/dynamic-media/image-profiles.md)


