---
title: Relations des ressources
description: Découvrez comment mettre en relation des ressources numériques qui partagent certains attributs communs. Créez également des relations dérivées de la source entre les ressources numériques à l’aide des relations de ressources.
role: User
feature: Collaboration,Asset Management
solution: Experience Manager, Experience Manager Assets
source-git-commit: 77dab2731f8d442bf999bf1614ef060944794574
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 59%

---

# Relations des ressources {#related-assets}

[!DNL Adobe Experience Manager Assets] vous permet de mettre en relation manuellement des ressources en fonction des besoins de votre organisation à l’aide de la fonctionnalité Ressources associées. Vous pouvez, par exemple, associer un fichier de licence à une ressource ou à une image/vidéo sur une rubrique similaire. Vous pouvez mettre en relation des ressources qui partagent certains attributs communs. Vous pouvez également utiliser la fonction pour créer des relations sources/dérivées entre les ressources. Par exemple, si vous disposez d’un fichier PDF généré à partir d’un fichier INDD, vous pouvez associer le fichier PDF à son fichier INDD source.

Grâce à cette fonctionnalité, vous avez la possibilité de partager un fichier PDF ou JPG basse résolution avec des fournisseurs ou des agences et de rendre le fichier INDD haute résolution disponible uniquement sur demande.

>[!NOTE]
>
>Seuls les utilisateurs disposant d’autorisations de modification des ressources peuvent mettre en relation et dissocier ces dernières.

## Étapes de mise en relation des ressources {#steps-to-relate-assets}

1. À partir de l’interface d’[!DNL Experience Manager], ouvrez la page **[!UICONTROL Propriétés]** d’une ressource que vous souhaitez mettre en relation.

   ![ouvrir la page Propriétés d’une ressource pour mettre celle-ci en relation](assets/asset-properties-relate-assets.png)

1. Pour mettre en relation une autre ressource avec celle que vous avez sélectionnée, cliquez sur **[!UICONTROL Relations entre les ressources]** ![lier des ressources](assets/do-not-localize/link-relate.png).
1. Utilisez l’une des méthodes suivantes :

   * Pour mettre en relation le fichier source de la ressource, sélectionnez **[!UICONTROL Ajouter Source]** dans la liste. Vous ne pouvez associer qu’une seule ressource en tant que source.
   * Pour mettre en relation un fichier dérivé, sélectionnez **[!UICONTROL Ajouter dérivé]** dans la liste. Vous pouvez associer plusieurs ressources dans cette catégorie.
   * Pour créer une relation bidirectionnelle entre les ressources, sélectionnez **[!UICONTROL Ajouter autre]** dans la liste. Vous pouvez associer plusieurs ressources dans cette catégorie.

1. Dans l’écran **[!UICONTROL Sélectionner Assets]**, accédez à l’emplacement de la ressource à mettre en relation, puis sélectionnez-la. Vous pouvez sélectionner une ou plusieurs ressources à la fois en maintenant la touche Maj enfoncée tout en cliquant. Cela peut inclure n’importe quel format de fichier [pris en charge dans la vue Assets](/help/assets/supported-file-formats-assets-view.md).

   ![ajouter une ressource associée](assets/add-related-asset.png)

1. Cliquez sur **[!UICONTROL Sélectionner]**. Selon la relation que vous avez choisie à l’étape 3, l’actif associé est répertorié sous une catégorie appropriée dans la section **[!UICONTROL Relations entre les actifs]**. Par exemple, si la ressource que vous avez associée est le fichier source de la ressource actuelle, elle est répertoriée sous **[!UICONTROL Source]**.

   ![Exemple de relation Assets](assets/asset-relations-example.png)

1. Cliquez sur **[!UICONTROL Dissocier]** ![dissocier les ressources](assets/do-not-localize/link-unrelate-icon.png) disponible pour toutes les ressources associées dans chaque section ([!UICONTROL Source], [!UICONTROL Dérivé] et [!UICONTROL Autre]) pour dissocier une ressource.

## Traduire les ressources liées {#translating-related-assets}

La création de relations source/dérivés entre des ressources à l’aide de la fonctionnalité Ressources mises en relation est également utile dans les workflows de traduction. Lorsque vous exécutez un workflow de traduction sur une ressource dérivée, [!DNL Experience Manager Assets] récupère automatiquement toute ressource référencée par le fichier source et la soumet pour traduction. Ainsi, la ressource référencée par la ressource source est traduite avec les ressources source et dérivées. Si le fichier source est mis en relation avec une autre ressource, [!DNL Experience Manager Assets] récupère la ressource référencée et la soumet pour traduction.

Voir [&#x200B; Traduction des ressources dans AEM](/help/assets/translate-assets.md).

## Étapes suivantes {#next-steps}

* Faites des commentaires sur le produit en utilisant l’option [!UICONTROL Commentaires] disponible dans l’interface utilisateur de la vue Assets

* Faites des commentaires sur la documentation en utilisant l’option [!UICONTROL Modifier cette page] ![modifier la page](assets/do-not-localize/edit-page.png) ou [!UICONTROL Enregistrer un problème] ![créer un problème GitHub](assets/do-not-localize/github-issue.png) disponible dans la barre latérale droite.

* Contactez l’[assistance clientèle](https://experienceleague.adobe.com/fr?support-solution=General#support).

>[!MORELIKETHIS]
>
>* [Afficher les versions d’une ressource](/help/assets/manage-organize-assets-view.md#view-versions)
>* [Traduire les ressources dans AEM](/help/assets/translate-assets.md)
>* [Formats de fichiers pris en charge dans la vue Assets](/help/assets/supported-file-formats-assets-view.md).
