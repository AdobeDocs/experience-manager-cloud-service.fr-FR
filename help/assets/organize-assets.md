---
title: Organisation des ressources numériques
description: Organisez vos ressources numériques à l’aide de diverses méthodes fournies dans Adobe Experience Manager Assets.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Organisation des ressources numériques{#organize-digital-assets}

L’ensemble des ressources numériques, des métadonnées et du contenu des documents Microsoft Office et PDF sont extraits et rendus utilisables dans une requête. Les recherches permettent un filtrage élaboré des ressources et respectent entièrement les autorisations. Les métadonnées sont traitées en détail dans la section Métadonnées dans la gestion des actifs numériques.

AEM Assets prend en charge plusieurs manières d’organiser le contenu. Vous pouvez l’organiser de façon hiérarchique à l’aide de dossiers ou de manière ad hoc, non classée à l’aide de balises. Les utilisateurs peuvent modifier les balises dans l’éditeur de ressources de gestion des actifs numériques où les sous-ressources, rendus et métadonnées sont affichés.

## Création de dossiers {#create-folders}

Lorsque vous organisez une collection de ressources, comme toutes les images *Nature*, vous pouvez créer des dossiers pour les conserver ensemble. Vous pouvez utiliser des dossiers pour classer et organiser vos ressources. AEM Assets ne nécessite pas de classer les ressources dans des dossiers pour mieux fonctionner.

>[!NOTE]
>
>Le partage d’un dossier de ressources (dans Marketing Cloud) de type `sling:OrderedFolder` n’est pas pris en charge. Si vous souhaitez partager un dossier, ne sélectionnez pas Ordonné lors de la création d’un dossier.

1. Dans le dossier Ressources numériques, accédez à l’emplacement où vous souhaitez créer un dossier.
1. Dans le menu, cliquez sur **[!UICONTROL Créer]**. Select **[!UICONTROL New Folder]**.
1. In the **[!UICONTROL Title]** field, provide a folder name. Par défaut, DAM utilise le titre que vous avez fourni comme nom du dossier. Une fois le dossier créé, vous pouvez remplacer le nom par défaut et entrer un autre nom de dossier.
1. Cliquez sur **[!UICONTROL Créer]**. Le dossier apparaît dans le dossier Ressources numériques.

## Ajout de propriétés CUG à des dossiers {#add-cug-properties-to-folders}

Dans Assets, vous pouvez limiter les utilisateurs autorisés à accéder à certains dossiers en les faisant appartenir à un groupe d’utilisateurs fermé (CUG). Pour faire appartenir un dossier à un groupe d’utilisateurs fermé

1. Dans Assets, cliquez avec le bouton droit sur le dossier pour lequel souhaitez ajouter des propriétés CUG, puis sélectionnez **Propriétés**.
1. Cliquez sur l’onglet **CUG**.
1. Cochez la case **Activé** pour que le dossier et les ressources qu’il contient ne soient accessibles que par un groupe d’utilisateurs fermé.
1. Pour ajouter ces informations, accédez à la page de connexion, le cas échéant. Ajoutez les groupes admis en cliquant sur **Ajouter un élément**. Si nécessaire, ajoutez le domaine. Cliquez sur **OK** pour enregistrer vos modifications.

## Utilisation de balises pour organiser les ressources {#use-tags-to-organize-assets}

Vous pouvez utiliser des dossiers, des balises ou les deux pour organiser des ressources. Lorsque vous ajoutez des balises aux ressources, vous facilitez leur récupération lors d’une recherche. Pour ajouter des balises à un fichier, procédez comme suit :

1. Dans Digital Asset Manager, double-cliquez sur la ressource pour l’ouvrir.
1. In the **Tags** area, click the drop-down button to reveal the available tags. Sélectionnez les balises adéquates à ajouter. To delete a tag, hover the mouse over the tag and click the **x** to delete it.
1. Click **Save** to save any tags you added.
