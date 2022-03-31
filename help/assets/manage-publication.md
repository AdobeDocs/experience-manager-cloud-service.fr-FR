---
title: Gérer la publication
description: Publication ou annulation de la publication de ressources dans Experience Manager Assets, Dynamic Media et Brand Portal
contentOwner: Vishabh Gupta
mini-toc-levels: 1
feature: Asset Management, Publishing, Collaboration, Asset Processing
role: User, Architect, Admin
exl-id: 691a0925-0061-4c62-85ac-8257b96dddf2
source-git-commit: ca01102673211f17e58af36ef2a59d0e964022d5
workflow-type: tm+mt
source-wordcount: '1435'
ht-degree: 16%

---

# Gestion de la publication dans Experience Manager Assets {#manage-publication-in-aem}

En tant que [!DNL Adobe Experience Manager Assets] administrateur, vous pouvez publier des ressources et des dossiers contenant des ressources de votre instance d’auteur sur [!DNL Experience Manager Assets], [!DNL Dynamic Media], et [!DNL Brand Portal]. Vous pouvez également planifier le workflow de publication d’une ressource ou d’un dossier à une date ou une heure ultérieure. Une fois les ressources publiées, les utilisateurs peuvent y accéder et les distribuer à d’autres utilisateurs. Par défaut, vous pouvez publier des ressources et des dossiers sur [!DNL Experience Manager Assets]. Cependant, vous pouvez configurer [!DNL Experience Manager Assets] pour activer la publication sur [[!DNL Dynamic Media]](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/config-dm.html) et [[!DNL Brand Portal]](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/brand-portal/configure-aem-assets-with-brand-portal.html).

Vous pouvez publier ou annuler la publication de ressources au niveau de la ressource ou du dossier à l’aide de l’option **[!UICONTROL Publication rapide]** ou **[!UICONTROL Gérer la publication]** , disponible dans la variable [!DNL Experience Manager Assets] . Si vous apportez des modifications ultérieures à la ressource ou au dossier d’origine dans [!DNL Experience Manager Assets], les modifications ne sont pas répercutées dans l’instance de publication tant que vous n’avez pas republié à partir de [!DNL Experience Manager Assets]. Cela permet de s’assurer que les modifications en cours ne sont pas disponibles dans l’instance de publication. Seules les modifications approuvées publiées par un administrateur sont disponibles dans l’instance de publication.

* [Publication de ressources à l’aide de la publication rapide](#quick-publish)
* [Publication de ressources à l’aide de la fonction Gérer la publication](#manage-publication)
* [Publication ultérieure des ressources](#publish-assets-later)
* [Publication de ressources dans Dynamic Media](#publish-assets-to-dynamic-media)
* [Publication de ressources sur Brand Portal](#publish-assets-to-brand-portal)
* [Limites et conseils](#limitations-and-tips)

## Publication de ressources à l’aide de la publication rapide {#quick-publish}

La publication rapide vous permet de publier immédiatement le contenu vers la destination sélectionnée. Dans la [!DNL Experience Manager Assets] , accédez au dossier parent et sélectionnez toutes les ressources ou tous les dossiers à publier. Cliquez sur **[!UICONTROL Publication rapide]** dans la barre d’outils, puis sélectionnez destination dans la liste déroulante où vous souhaitez publier les ressources.

![Publication rapide](assets/quick-publish-to-aem.png)

## Publication de ressources à l’aide de la fonction Gérer la publication {#manage-publication}

Gérer la publication permet de publier ou d’annuler la publication de contenu vers et depuis la destination sélectionnée, [ajouter du contenu](#add-content) à la liste de publication à partir du référentiel DAM, [paramètres du dossier d’inclusion](#include-folder-settings) pour publier le contenu des dossiers sélectionnés et appliquer des filtres, et [planification de la publication](#publish-assets-later) à une date ou une heure ultérieure.

Dans la [!DNL Experience Manager Assets] , accédez au dossier parent et sélectionnez toutes les ressources ou tous les dossiers à publier. Cliquez sur **[!UICONTROL Gérer la publication]** dans la barre d’outils. Si vous n’avez pas [!DNL Dynamic Media] et [!DNL Brand Portal] configuré dans votre [!DNL Experience Manager Assets] vous pouvez publier des ressources et des dossiers uniquement sur [!DNL Experience Manager Assets].

![Gérer la publication](assets/manage-publication-aem.png)

Les options suivantes sont disponibles dans la variable [!UICONTROL Gérer la publication] interface :

* [!UICONTROL Actions]
   * `Publish`: Publication de ressources et de dossiers sur la destination sélectionnée
   * `Unpublish`: Annulation de la publication de ressources et de dossiers à partir de la destination

* [!UICONTROL Destination]
   * `Publish`: Publication de ressources et de dossiers sur [!DNL Experience Manager Assets] (`AEM`)
   * `Dynamic Media`: Publication de ressources sur [!DNL Dynamic Media]
   * `Brand Portal`: Publication de ressources et de dossiers sur [!DNL Brand Portal]

* [!UICONTROL Planification]
   * `Now`: Publier les ressources immédiatement
   * `Later`: Publiez des ressources en fonction de la variable `Activation` date ou heure

Pour continuer, cliquez sur **[!UICONTROL Suivant]**. Selon la sélection, la variable **[!UICONTROL Portée]** reflète différentes options. Les options de **[!UICONTROL Ajouter du contenu]** et **[!UICONTROL Paramètres du dossier d’inclusion]** ne sont disponibles que pour la publication des ressources et des dossiers sur [!DNL Experience Manager Assets] (`Destination: Publish`).

![Gérer la portée de la publication](assets/manage-publication-aem-scope.png)

### Ajouter du contenu {#add-content}

Publication sur [!DNL Experience Manager Assets] vous permet d’ajouter davantage de contenu (ressources et dossiers) à la liste de publication. Vous pouvez ajouter d’autres ressources ou dossiers à la liste dans les référentiels DAM. Cliquez sur **[!UICONTROL Ajouter du contenu]** pour ajouter du contenu.

Vous pouvez ajouter plusieurs ressources à partir d’un dossier ou ajouter plusieurs dossiers à la fois. Mais vous ne pouvez pas ajouter de ressources à partir de plusieurs dossiers à la fois.

![Ajouter du contenu](assets/manage-publication-add-content.png)

### Inclure les paramètres de dossier {#include-folder-settings}

Par défaut, publier un dossier dans [!DNL Experience Manager Assets] publie toutes les ressources, tous les sous-dossiers et leurs références.

Pour filtrer le contenu du dossier que vous souhaitez publier, cliquez sur **[!UICONTROL Paramètres du dossier d’inclusion]**:

* `Include folder contents`

   * Activé : Toutes les ressources du dossier sélectionné, les sous-dossiers (y compris toutes les ressources des sous-dossiers) et les références sont publiés.
   * Désactivé : Seul le dossier sélectionné (vide) et les références sont publiés. Les ressources du dossier sélectionné ne sont pas publiées.

* `Include folder contents` et `Include only immediate folder contents`

   Si les deux options sont sélectionnées, toutes les ressources du dossier, des sous-dossiers (vides) et des références sélectionnés sont publiées. Les ressources des sous-dossiers ne sont pas publiées.

<!--
* [!UICONTROL Include only immediate folder contents]: Only the subfolders content and references are published. 

Only the selected folder content and references are published.
-->

![Inclure les paramètres de dossier](assets/manage-publication-include-folder-settings.png)

Après avoir appliqué les filtres, cliquez sur **[!UICONTROL OK]**, puis cliquez sur **[!UICONTROL Publier]**. Lorsque vous cliquez sur le bouton de publication, un message de confirmation s’affiche. `Resource(s) have been scheduled for publication` apparaît. Et les ressources et (ou) dossiers sélectionnés sont publiés vers la destination définie en fonction du planificateur (`Now` ou `Later`). Connectez-vous à votre instance de publication pour vérifier que les ressources et (ou) les dossiers ont bien été publiés.

![Publier sur AEM](assets/manage-publication-publish-aem.png)

Dans l’illustration ci-dessus, vous pouvez voir différentes valeurs pour la variable **[!UICONTROL Cible de publication]** attribut. Rappelons-nous que vous avez choisi de publier sur [!DNL Experience Manager Assets] (`Destination: Publish`). Alors, pourquoi indique-t-il que seuls un dossier et une ressource sont publiés sur `AEM`, et les deux autres ressources sont publiées sur les deux `AEM` et `Dynamic Media`?

Ici, vous devez comprendre le rôle des propriétés du dossier. Un dossier **[!UICONTROL Mode de publication Dynamic Media]** joue un rôle important dans la publication. Pour afficher les propriétés d’un dossier, sélectionnez-le, puis cliquez sur **[!UICONTROL Propriétés]** dans la barre d’outils. Pour une ressource, voir les propriétés de son dossier parent.

Le tableau suivant explique comment la publication se produit en fonction des **[!UICONTROL Destination]** et **[!UICONTROL Mode de publication Dynamic Media]**:

| [!UICONTROL Destination] | [!UICONTROL Mode de publication Dynamic Media] | [!UICONTROL Cible de publication] | Contenu autorisé |
| --- | --- | --- | --- |
| Publier | Publication sélective | `AEM` | Ressources et (ou) dossiers |
| Publication | Immédiat | `AEM` et `Dynamic Media` | Ressources et (ou) dossiers |
| Publication | Lors de l’activation | `AEM` et `Dynamic Media` | Ressources et (ou) dossiers |
| Dynamic Media | Publication sélective | `Dynamic Media` | Assets |
| Dynamic Media | Immédiat | `None` | Impossible de publier les ressources |
| Dynamic Media | Lors de l’activation | `None` | Impossible de publier les ressources |

>[!NOTE]
>
>Seules les ressources sont publiées sur [!DNL Dynamic Media].
>
>Publication d’un dossier sur [!DNL Dynamic Media] n’est pas prise en charge.
>
>Si vous sélectionnez un dossier (`Selective Publish`) et choisissez la variable [!DNL Dynamic Media] destination, la variable [!UICONTROL Cible de publication] L’attribut `None`.


Changeons maintenant **[!UICONTROL Destination]** dans le cas d’utilisation ci-dessus à **[!UICONTROL Dynamic Media]** et vérifiez les résultats. Ce faisant, seul l’actif de `Selective Publish` est publié dans [!DNL Dynamic Media]. Les ressources de `Immediate` et `Upon Activation` Les dossiers ne sont pas publiés et reflètent `None`.

![Publier vers Dynamic Media](assets/manage-publication-dynamic-media.png)

>[!NOTE]
>
>If [!DNL Dynamic Media] n’est pas configuré sur [!DNL Experience Manager Assets] et l’instance **[!UICONTROL Destination]** is **[!UICONTROL Publier]**, les ressources et les dossiers sont toujours publiés sur `AEM`.
>
>Publication sur [!DNL Brand Portal] est indépendant des propriétés du dossier. Toutes les ressources, dossiers et collections peuvent être publiés sur Brand Portal. Voir [publication de ressources dans Brand Portal](#publish-assets-to-brand-portal).

>[!NOTE]
>
>Si vous avez personnalisé la variable [!DNL Manage Publication] , votre personnalisation continue de fonctionner avec les fonctionnalités existantes.
>
>Cependant, vous pouvez supprimer la personnalisation existante pour utiliser la nouvelle [!DNL Manager Publication] fonctions.


## Publication ultérieure des ressources {#publish-assets-later}

Pour planifier le workflow de publication des ressources à une date ou une heure ultérieure :

1. Dans la [!UICONTROL Experience Manager Assets] , accédez au dossier parent et sélectionnez toutes les ressources ou tous les dossiers à planifier pour la publication.
1. Cliquez sur **[!UICONTROL Gérer la publication]** dans la barre d’outils.
1. Cliquez sur **[!UICONTROL Publier]** de **[!UICONTROL Action]**, puis sélectionnez la variable **[!UICONTROL Destination]** où vous souhaitez publier le contenu.
1. Sélectionnez **[!UICONTROL Plus tard]** dans **[!UICONTROL Planification]**.
1. Sélectionnez une **[!UICONTROL Date d’activation]** et indiquez la date et l’heure. Cliquez sur **[!UICONTROL Suivant]**.

   ![Processus de gestion de la publication](assets/manage-publication-workflow.png)

1. Dans le **[!UICONTROL Portée]** onglet, **[!UICONTROL Ajouter du contenu]** (si nécessaire). Cliquez sur **[!UICONTROL Suivant]**.
1. Dans le **[!UICONTROL Workflows]** , spécifiez un titre de workflow. Cliquez sur **[!UICONTROL Publier ultérieurement]**.

   ![Titre du workflow](assets/manage-publication-workflow-title.png)

   Connectez-vous à l’instance de destination pour vérifier les ressources publiées (selon la date ou l’heure planifiée).

## Publication de ressources dans Dynamic Media {#publish-assets-to-dynamic-media}

Seules les ressources sont publiées sur [!DNL Dynamic Media]. Cependant, le comportement de publication diffère en fonction des propriétés du dossier. Un dossier peut avoir **[!UICONTROL Mode de publication Dynamic Media]** configuré pour la publication sélective qui peut être l’une des options suivantes :

* `Selective Publish`
* `Immediate`
* `Upon Activation`

Le processus de publication pour **[!UICONTROL Immédiat]** et **[!UICONTROL Lors de l’activation]** est cohérent, mais différent de **[!UICONTROL Publication sélective]**. Voir [configuration de la publication sélective au niveau des dossiers dans Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/selective-publishing.html). Après avoir configuré la publication sélective dans un dossier, vous pouvez effectuer l’une des opérations suivantes :

* [Publier sélectivement des ressources dans Dynamic Media ou Experience Manager à l’aide de la fonction Gérer la publication](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/selective-publishing.html?lang=en#selective-publish-manage-publication)
* [Annuler sélectivement la publication de ressources dans Dynamic Media ou Experience Manager à l’aide de la fonction Gérer la publication](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/selective-publishing.html?lang=en#selective-unpublish-manage-publication)
* [Publication de ressources dans Dynamic Media ou Experience Manager à l’aide de la publication rapide](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/selective-publishing.html?lang=en#quick-publish-aem-dm)
* [Publier des ressources ou en annuler la publication de manière sélective au moyen des résultats de recherche](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/selective-publishing.html?lang=en#selective-publish-unpublish-search-results)

## Publication de ressources sur Brand Portal {#publish-assets-to-brand-portal}

Vous pouvez publier des ressources, des dossiers et des collections dans le [!DNL Experience Manager Assets Brand Portal] instance.

* [Publication de ressources sur Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/brand-portal/publish-to-brand-portal.html?lang=en#publish-assets-to-bp)
* [Publication de dossiers sur Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/brand-portal/publish-to-brand-portal.html?lang=en#publish-folders-to-brand-portal)
* [Publication de collections sur Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/brand-portal/publish-to-brand-portal.html?lang=en#publish-collections-to-brand-portal)

## Limites et conseils {#limitations-and-tips}

* L’option [!UICONTROL Gérer la publication] n’est disponible que pour les comptes d’utilisateurs disposant d’autorisations de réplication.
* Les dossiers vides ne sont pas publiés.
* Si vous publiez une ressource en cours de traitement, seul le contenu original est publié. Les rendus sont absents. Attendez que le traitement soit terminé, puis publiez ou republiez la ressource une fois le traitement terminé.
* Lors de l’annulation de la publication d’une ressource complexe, annulez uniquement la publication de la ressource. Évitez d’annuler la publication des références, car elles peuvent être référencées par d’autres ressources publiées.
