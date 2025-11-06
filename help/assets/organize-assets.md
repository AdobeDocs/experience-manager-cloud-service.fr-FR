---
title: Organisez vos ressources numériques
description: Organisez vos ressources numériques, vos images, vos fichiers, vos dossiers, etc. à l’aide d’Experience Manager.
contentOwner: AG
feature: Asset Management, Best Practices
role: User
exl-id: 6b3ce076-2dd9-47f6-9b68-4fa52bfedd42
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '929'
ht-degree: 94%

---

# Organisez vos ressources numériques {#organize-digital-assets}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/organize-assets.html?lang=fr) |
| AEM as a Cloud Service | Cet article |

L’ensemble des ressources numériques, des métadonnées et du contenu des documents Microsoft® Office et PDF sont extraits et rendus utilisables dans une requête. Les recherches permettent un filtrage élaboré des ressources et respectent entièrement les autorisations. Les métadonnées sont traitées en détail dans la section Métadonnées dans la gestion des actifs numériques.

[!DNL Experience Manager Assets] prend en charge plusieurs manières d’organiser le contenu. Vous pouvez les organiser de manière hiérarchique à l’aide de dossiers ou de manière ad hoc et non classée à l’aide de balises. Les utilisateurs peuvent modifier les balises dans l’éditeur de ressources de gestion des actifs numériques où les sous-ressources, rendus et métadonnées sont affichés.

<!-- Commenting to pull down the existing content before applying changes wrt CQDOC-15930
## Create folders {#create-folders}

When organizing a collection of assets, for example, all *Nature* images, you can create folders to keep them together. You can use folders to categorize and organize your assets. [!DNL Assets] does not require you to organize assets in folders to work better.

>[!NOTE]
>
>Sharing an Assets folder (in Marketing Cloud) of the type `sling:OrderedFolder`, is not supported. If you want to share a folder, do not select Ordered when creating a folder.

1. Navigate to the place in your digital assets folder where you want to create a folder.
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

You can use folders or tags or both to organize assets. Adding tags to assets makes them easier to retrieve during a search. To add tags to an asset, follow these steps:

1. In the Digital Asset Manager, double-click the asset to open it.
1. In the **Tags** area, open the menu to reveal the available tags. Select tags as appropriate. To delete a tag, hover the pointer over the tag and click `X` to delete it.
1. Click **Save** to save any tags you added.

Date24/08/2021
-->

## Organisation des ressources dans des dossiers {#organize-using-folders}

La méthode la plus simple pour organiser les ressources consiste à les enregistrer dans des dossiers. Cela revient à organiser les fichiers dans des dossiers de votre système de fichiers local. Pour plus d’informations sur la création et la gestion des dossiers, consultez [Gestion des ressources](manage-digital-assets.md). La façon dont vous nommez les fichiers ou les dossiers, organisez les sous-dossiers ou gérez les fichiers au sein des dossiers peut avoir un impact significatif sur le traitement des ressources. Grâce à des stratégies d’attribution de noms de fichiers et de dossiers cohérentes et appropriées, ainsi qu’à de bonnes pratiques d’utilisation des métadonnées, vous pouvez tirer le meilleur parti de votre référentiel de ressources numériques.

* En règle générale, votre référentiel de ressources numériques ne fait que croître. Il est donc important de formaliser l’utilisation des métadonnées, la structure des dossiers et l’attribution de noms aux fichiers au début du cycle de création de contenu.
* Utilisez les dossiers uniquement pour imposer une structure de stockage cohérente pour vos ressources numériques. Cette cohérence consolide vos processus et vous aide à gérer vos ressources. Par exemple, les types de dossiers suivants peuvent vous aider à séparer les ressources :

   * **Dossiers de développement** : contiennent les ressources numériques que vous utilisez actuellement.
   * **Dossiers de clients** : contiennent des ressources numériques en fonction des clients ou des noms de projet.
   * **Dossiers principaux** : contiennent les ressources numériques sources originales.
   * **Dossiers de rendus** : contiennent les rendus et les copies des ressources numériques sources originales.
   * **Dossiers de taille de fichier** : contiennent des ressources numériques en fonction des tailles de fichier petite, moyenne et volumineuse.
   * **Dossiers intermédiaires** : contiennent les ressources numériques qui sont prêtes à être publiées sur votre site web.
   * **Dossiers de type MIME** : contiennent des ressources numériques qui sont spécifiques à des types MIME tels que des images, des documents et des fichiers multimédias.
   * **Dossiers d’archives** : contiennent les ressources numériques retirées.
   * **Dossiers reposant sur une date** : contiennent des ressources numériques en fonction d’une date de création ou d’une date de dernière modification.

* Créez un répertoire de dossiers qui n’est pas susceptible de changer afin que les processus de personnalisation ou d’autonomisation puissent continuer à fonctionner. Par exemple, les profils de traitement affectés continuent à fonctionner.
* Si une ressource a déjà été publiée, utilisez [!DNL Experience Manager] pour déplacer cette ressource vers un autre dossier et la republier depuis son nouvel emplacement. L’emplacement d’origine de la ressource publiée est toujours disponible ainsi que la ressource récemment republiée. Toutefois, la version d’origine de la ressource publiée est *« perdue »* pour [!DNL Experience Manager] et elle ne peut pas être dépubliée. Il est donc recommandé de dépublier une ressource avant de la déplacer vers un autre dossier.

## Organisation de ressources à l’aide de balises {#use-tags-to-organize-assets}

L’ajout de balises à des ressources permet de les récupérer plus facilement au cours d’une recherche, de créer des collections à l’aide des résultats de recherche, d’améliorer le classement de certaines ressources et d’appliquer des algorithmes d’IA d’Adobe Sensei pour la découverte de ressources.

[!DNL Adobe Experience Manager Assets] utilise un algorithme d’auto-apprentissage pour créer des balises hautement descriptives qui vous permettent de trouver la ressource appropriée en quelques clics seulement. Le balisage intelligent utilise Adobe Sensei, l’intelligence artificielle et la structure de machine learning, qui peuvent être entraînés pour reconnaître et appliquer des balises standard et commerciales à l’imagerie. Les balises intelligentes peuvent également identifier le contenu, les mots ou les expressions et appliquer automatiquement des balises descriptives aux ressources.

Vous trouverez ci-dessous la procédure à suivre pour ajouter des balises à une ressource :

1. Connectez-vous à [!DNL Experience Manager Assets].
1. Cliquez sur **[!UICONTROL Ressources]** > **[!UICONTROL Fichiers]**, sélectionnez la ressource et cliquez sur **[!UICONTROL Propriétés]** pour ouvrir les propriétés de la ressource.
1. Dans l’onglet **[!UICONTROL De base]**, cliquez sur l’icône de dossier dans les métadonnées **[!UICONTROL Balises]**. Une fenêtre pop-up s’ouvre.
1. Recherchez ou sélectionnez les balises appropriées parmi les balises existantes dans `cq-tags`. Vous pouvez affecter plusieurs balises à la ressource.

   Vous pouvez trier la structure des balises par ordre croissant ou décroissant en fonction du **[!UICONTROL Nom]** (par ordre alphabétique), de la date de **[!UICONTROL Création]** ou de la date de **[!UICONTROL Modification]**. Dans l’illustration suivante, la structure des balises est triée par ordre alphabétique en fonction de la variable **[!UICONTROL Nom]**.

   ![add-tags](assets/add-tags-to-asset.png)

1. Cliquez sur **Enregistrer** pour mettre à jour les modifications apportées aux métadonnées de la ressource.

Pour plus d’informations, consultez les articles suivants :

* [Modification de métadonnées de ressource](meta-edit.md)
* [Balises intelligentes dans Assets](smart-tags.md)
* [Ajout d’un prédicat de balises au panneau de recherche](/help/assets/search-facets.md#adding-a-tags-predicate)

## Organisation en tant que collections {#organize-as-collections}

Grâce aux collections de ressources dans [!DNL Experience Manager Assets], vous pouvez optimiser la possibilité de créer, modifier et partager des ressources entre les utilisateurs. Créez plusieurs types de collections en fonction de leur utilisation, y compris des collections qui contiennent une liste de références statiques des ressources, dossiers et collections, ainsi que des collections qui extraient des ressources en fonction de critères de recherche. Vous pouvez créer des collections avec des ressources provenant de différents emplacements et les partager avec plusieurs utilisateurs disposant de différents niveaux d’accès, d’affichage et de modification des privilèges.

Pour plus d’informations, consultez [Gérer les collections](manage-collections.md).


## Utilisation de profils pour organiser vos ressources {#organize-to-use-profiles}

Un profil de traitement contient les commandes de traitement [!DNL Assets] qui s’appliquent aux ressources chargées dans des dossiers prédéfinis. Les profils sont utilisés pour automatiser le traitement du contenu d’un dossier ou de ressources nouvellement chargées. Vous pouvez utiliser des profils pour mieux organiser vos ressources.

Grâce à cette normalisation de l’utilisation des métadonnées, de l’attribution des noms et de la structure des dossiers, vous aurez l’assurance, au fur et à mesure que le nombre de vos ressources augmente, de pouvoir appliquer des profils de traitement aux dossiers avec une précision et une cohérence toujours plus grandes.

**Voir également**

* [Traduire les ressources](translate-assets.md)
* [API HTTP Assets](mac-api-assets.md)
* [Formats de fichiers pris en charge par Assets](file-format-support.md)
* [Rechercher des ressources](search-assets.md)
* [Ressources connectées](use-assets-across-connected-assets-instances.md)
* [Rapports de ressources](asset-reports.md)
* [Schémas de métadonnées](metadata-schemas.md)
* [Télécharger des ressources](download-assets-from-aem.md)
* [Gestion des métadonnées](manage-metadata.md)
* [Facettes de recherche](search-facets.md)
* [Gérer les collections](manage-collections.md)
* [Import des métadonnées en bloc](metadata-import-export.md)
* [Publier des ressources sur AEM et Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [Utilisation des microservices de ressources et des profils de traitement](asset-microservices-configure-and-use.md)
>* [Profils de métadonnées](metadata-profiles.md)
>* [Profils vidéo](/help/assets/dynamic-media/video-profiles.md)
>* [Profils d’image Dynamic Media](/help/assets/dynamic-media/image-profiles.md)

