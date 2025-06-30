---
title: Comment traduire des ressources dans AEM ?
description: Découvrez comment automatiser les workflows de traduction des ressources dans AEM, y compris les fichiers binaires, les métadonnées et les balises, et ce dans plusieurs langues.
contentOwner: AG
feature: Asset Management, Translation
role: Admin, User
exl-id: 98df1412-a957-48a3-81c2-7dfe1d5e6d31
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '2615'
ht-degree: 84%

---

# Traduire les ressources dans AEM {#multilingual-assets}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/multilingual-assets.html?lang=fr) |
| AEM as a Cloud Service | Cet article |

Les ressources multilingues sont des ressources comportant des fichiers binaires, des métadonnées et des balises dans plusieurs langues. En règle générale, les fichiers binaires, les métadonnées et les balises d’une ressource existent dans une langue, et sont ensuite traduits dans d’autres langues pour être utilisés dans des projets multilingues. Adobe Experience Manager Assets vous permet d’automatiser les workflows de traduction des ressources (y compris les fichiers binaires, les métadonnées et les balises) pour générer des ressources dans d’autres langues à utiliser dans des projets multilingues.

Pour automatiser les traductions de ressources dans AEM, vous intégrez des fournisseurs de traduction à Experience Manager et créez des projets pour traduire les ressources dans plusieurs langues. Experience Manager prend en charge les workflows de traduction humaine et automatique.

Traduction humaine des ressources dans AEM : les ressources traduites sont renvoyées et importées dans Experience Manager. Lorsque votre fournisseur de traduction est intégré à Experience Manager, les ressources sont envoyées automatiquement entre Experience Manager et le fournisseur de traduction.

Traduction automatique des ressources dans AEM : le service de traduction automatique traduit instantanément les métadonnées et les balises des ressources.

<!--
We have multiple articles around translation of assets. For now, dumping all content in this article to remove others and create only ONE UBER article.

https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/translation-projects.html?lang=fr
https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/preparing-assets-for-translation.html?lang=fr
[Apply translation cloud services to folders](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/transition-cloud-services.html?lang=fr)

One of these articles is a copy of [Preparing Content for Translation](https://experienceleague.adobe.com/docs/experience-manager-65/administering/introduction/tc-prep.html?lang=fr

-->

<!-- 
Translating assets includes the following:

1. [Connecting Experience Manager with the translation service provider](/help/sites-administering/tc-tic.md#connecting-to-a-translation-service-provider)
1. [Creating translation integration framework configurations](/help/sites-administering/tc-tic.md)
1. [Preparing assets for translation](prepare-assets-for-translation.md)
1. [Applying translation cloud services to folders](transition-cloud-services.md)
1. [Create translation projects](translation-projects.md)

If your translation service provider does not provide a connector to integrate with Experience Manager, use an [alternative process](/help/sites-administering/tc-manage.md#exporting-a-translation-job).

Also see, [Creating translation projects for content fragments](creating-translation-projects-for-content-fragments.md).

-->

## Préparer la traduction des ressources {#prepare-to-translate-assets}

Les ressources multilingues sont des ressources comportant des fichiers binaires, des métadonnées et des balises dans plusieurs langues. En règle générale, les fichiers binaires, les métadonnées et les balises d’une ressource existent dans une langue, et sont ensuite traduits dans d’autres langues pour être utilisés dans des projets multilingues.

Dans Adobe Experience Manager Assets, les ressources multilingues se trouvent dans des dossiers, chaque dossier contenant les ressources dans une langue différente.

Chaque dossier de langue est appelé « copie de langue ». Le dossier racine d’une copie de langue, appelé « racine de langue », identifie la langue du contenu de la copie de langue. Par exemple, `/content/dam/it` est la racine de langue italienne de la copie en italien. Les copies de langue doivent utiliser une [racine de langue correctement configurée](#create-a-language-root) pour que la bonne langue soit ciblée lors de la traduction des ressources sources.

La copie de langue pour laquelle vous ajoutez initialement des ressources est le gabarit de langue. Le gabarit de langue est la source qui est traduite dans d’autres langues. L’exemple de hiérarchie de dossiers comporte plusieurs racines de langue :

```shell
/content
    /- dam
        |- en
        |- fr
        |- de
        |- es
        |- it
        |- ja
        |- zh
```

Effectuez les étapes suivantes pour préparer la traduction des ressources :

1. Créez la racine de langue de votre gabarit de langue. Par exemple, la racine de langue de la copie en anglais dans l’exemple de hiérarchie de dossiers est `/content/dam/en`. Vérifiez que la racine de langue est configurée conformément aux informations de la section [Création d’une racine de langue](#create-a-language-root).

1. Ajoutez des ressources à votre gabarit de langue.
1. Créez la racine de langue de chaque langue cible pour laquelle vous avez besoin d’une copie de langue.

### Création d’une racine de langue {#create-a-language-root}

Pour créer la racine de langue, créez un dossier, puis utilisez le code de langue ISO comme valeur de la propriété Nom. Après avoir créé la racine de langue, vous pouvez créer une copie de langue à n’importe quel niveau de la racine de langue.

Par exemple, la page racine de la copie en italien de l’exemple de hiérarchie présente la propriété Nom `it`. La propriété Nom est utilisée comme nom du nœud de ressource dans le référentiel et détermine donc le chemin d’accès des ressources. (*&lt;server>:&lt;port>/assets.html/content/dam/it/*)

1. Dans la console Assets, sélectionnez **[!UICONTROL Créer]** et choisissez **[!UICONTROL Dossier]** dans le menu.
1. Dans le champ Nom, tapez le code de pays au format `<language-code>`.
1. Sélectionnez **[!UICONTROL Créer]**. La racine de langue est créée dans la console Ressources.

### Affichage des racines de langue {#view-language-roots}

L’IU optimisée pour les écrans tactiles propose un panneau Références qui affiche la liste des racines de langue créées dans [!DNL Assets].

1. Dans la console Ressources, choisissez le gabarit de langue pour lequel vous souhaitez créer des copies de langue.
1. Sélectionnez l’icône de navigation globale, puis choisissez **[!UICONTROL Références]** pour ouvrir le volet Référence.
1. Dans le volet Références, sélectionnez **[!UICONTROL Copies de langue]**. Le panneau Copies de langue affiche les copies de langue des ressources.

### Créer un projet de traduction {#create-a-new-translation-project}

Si vous utilisez cette option, les ressources à traduire sont copiées dans la racine de la langue vers laquelle vous souhaitez effectuer la traduction. Selon les options que vous choisissez, un projet de traduction est créé pour les ressources dans la console Projets. Selon les paramètres, le projet de traduction peut être démarré manuellement ou s’exécuter automatiquement dès sa création.

1. Dans l’interface utilisateur d’Assets, sélectionnez le dossier source pour lequel vous souhaitez créer une copie de langue.
1. Ouvrez le volet **[!UICONTROL Références]** et sélectionnez **[!UICONTROL Copies de langue]** sous **[!UICONTROL Copies]**.
1. Sélectionnez **[!UICONTROL Créer et traduire]** en bas de la page.
1. Dans la liste **[!UICONTROL Langues cibles]**, choisissez les langues pour lesquelles vous souhaitez créer une structure de dossiers.
1. Dans la liste **[!UICONTROL Projet]**, choisissez **[!UICONTROL Créer un projet de traduction]**.
1. Dans le champ **[!UICONTROL Titre du projet]**, saisissez un titre pour le projet.
1. Sélectionnez sur **[!UICONTROL Créer]**. Les ressources du dossier source sont copiées vers les dossiers cibles pour les paramètres régionaux que vous avez sélectionnés à l’étape 4.
1. Pour accéder au dossier, sélectionnez la copie de langue, puis cliquez sur **[!UICONTROL Afficher dans Assets]**.
1. Accédez à la console Projets. Le dossier de traduction est copié dans la console Projets.
1. Ouvrez le dossier pour afficher le projet de traduction.
1. Sélectionnez le projet pour ouvrir la page de détails.
1. Pour afficher l’état de la tâche de traduction, cliquez sur les points de suspension en bas de la mosaïque **[!UICONTROL Tâche de traduction]**. <!-- For more details around job statuses, see [Monitoring the Status of a Translation Job](/help/sites-administering/tc-manage.md#monitoring-the-status-of-a-translation-job). -->
1. Accédez à l’interface utilisateur d’Assets et ouvrez la page Propriétés de chacune des ressources traduites afin d’afficher les métadonnées traduites.

>[!NOTE]
>
>Cette fonctionnalité est disponible à la fois pour les ressources et les dossiers. Lorsqu’une ressource est sélectionnée au lieu d’un dossier, la hiérarchie de dossiers complète jusqu’à la langue racine est copiée afin de créer une copie de langue pour la ressource.

### Ajout à un projet de traduction existant {#add-to-existing-translation-project}

Si vous utilisez cette option, le workflow de traduction s’exécute pour les ressources que vous ajoutez au dossier source après l’exécution d’un précédent workflow de traduction. Seules les ressources nouvellement ajoutées sont copiées dans le dossier cible contenant les ressources précédemment traduites. Dans ce cas, aucun nouveau projet de traduction n’est créé.

1. Dans l’interface utilisateur d’Assets, accédez au dossier source qui contient des ressources non traduites.
1. Sélectionnez une ressource à traduire, puis ouvrez le **[!UICONTROL volet Référence]**. La section **[!UICONTROL Copies de langue]** indique le nombre de copies de traduction actuellement disponibles.
1. Sélectionnez **[!UICONTROL Copies de langue]** sous **[!UICONTROL Copies]**. La liste des copies de traduction disponibles s’affiche.
1. Sélectionnez **[!UICONTROL Créer et traduire]** en bas de la page.
1. Dans la liste **[!UICONTROL Langues cibles]**, choisissez les langues pour lesquelles vous souhaitez créer une structure de dossiers.
1. Dans la liste **[!UICONTROL Projet]**, sélectionnez **[!UICONTROL Ajouter à un projet de traduction existant]** afin d’exécuter le workflow de traduction sur le dossier.
   >[!NOTE]
   >
   >Si vous choisissez l’option **[!UICONTROL Ajouter à un projet de traduction existant]**, votre projet de traduction n’est ajouté à un projet préexistant que si les paramètres du projet correspondent exactement aux paramètres du projet préexistant. Dans le cas contraire, un nouveau projet est créé.
1. Dans la liste **[!UICONTROL Projet de traduction existant]**, choisissez un projet auquel ajouter la ressource à traduire.
1. Sélectionnez **[!UICONTROL Créer]**. Les fichiers à traduire sont ajoutés au dossier cible. Le dossier mis à jour est répertorié sous la section **[!UICONTROL Copies de langue]**.
1. Accédez à la console Projets, puis ouvrez le projet de traduction existant auquel vous avez ajouté des ressources.
1. Sélectionnez le projet de traduction pour afficher la page des détails du projet.
1. Sélectionnez les points de suspension en bas de la mosaïque **Tâche de traduction** pour afficher les ressources du workflow de traduction. La liste des tâches de traduction affiche également les entrées des métadonnées et des balises de ressources. Ces entrées indiquent que les métadonnées et les balises des ressources sont également traduites.

   >[!NOTE]
   >
   >* Si vous supprimez l’entrée pour les balises ou les métadonnées, aucune balise ou métadonnée n’est traduite pour l’une des ressources.
   >* Si vous utilisez la traduction automatique, les fichiers binaires des ressources ne sont pas traduits.
   >* Si la ressource que vous ajoutez à la tâche de traduction contient des sous-ressources, sélectionnez-les et supprimez-les pour que la traduction se déroule sans problème.

1. Pour commencer la traduction des ressources, sélectionnez la flèche sur la mosaïque **[!UICONTROL Tâche de traduction]** et sélectionnez **[!UICONTROL Démarrer]** dans la liste. Un message indique le début de la tâche de traduction.
1. Pour afficher le statut de la tâche de traduction, sélectionnez les points de suspension en bas de la mosaïque **[!UICONTROL Tâche de traduction]**. <!-- For more details, see [Monitoring the Status of a Translation Job](/help/sites-administering/tc-manage.md#monitoring-the-status-of-a-translation-job). -->
1. Une fois la traduction terminée, l’état devient Prêt pour la révision. Accédez à l’interface utilisateur d’Assets et ouvrez la page Propriétés de chacune des ressources traduites afin d’afficher les métadonnées traduites.

### Mise à jour des copies de langue {#update-language-copies}

Exécutez ce workflow afin de traduire un ensemble de ressources supplémentaire et de l’intégrer à une copie de langue pour des paramètres régionaux donnés. Dans ce cas, les ressources traduites sont ajoutées au dossier cible qui contient des ressources précédemment traduites. Selon le choix des options, un projet de traduction est créé ou un projet de traduction existant est mis à jour pour les nouvelles ressources. Le workflow Màj des copies de langue comprend les options suivantes :

* Créer un projet de traduction
* Ajouter à un projet de traduction existant

### Ajouter à un projet de traduction existant {#add-to-existing-translation-project-1}

Si vous utilisez cette option, l’ensemble de ressources est ajouté à un projet de traduction existant afin de mettre à jour la copie de langue pour les paramètres régionaux que vous sélectionnez.

1. Dans l’interface utilisateur d’Assets, sélectionnez le dossier source auquel vous avez ajouté un dossier de ressources.
1. Ouvrez le **[!UICONTROL volet Références]** et sélectionnez **[!UICONTROL Copies de langue]** sous **[!UICONTROL Copies]** pour afficher la liste des copies de langue.
1. Activez la case à cocher devant **[!UICONTROL Copies de langue]** de façon à sélectionner toutes les copies de langue. Désélectionnez les autres copies à l’exception des copies de langue correspondant aux paramètres régionaux dans lesquels vous souhaitez traduire.
1. Sélectionnez **[!UICONTROL Mettre à jour les copies de langue]** en bas de la page.
1. Dans la liste **[!UICONTROL Projet]**, choisissez **[!UICONTROL Ajouter à un projet de traduction existant]**.
1. Dans la liste **[!UICONTROL Projet de traduction existant]**, choisissez un projet auquel ajouter la ressource à traduire.
1. Sélectionner **[!UICONTROL Début]**.
1. Consultez les étapes 9 à 14 de la section [Ajouter à un projet de traduction existant](#add-to-existing-translation-project) pour accomplir le reste de la procédure.

### Création de copies de langue temporaires {#creating-temporary-language-copies}

Lorsque vous exécutez un workflow de traduction pour mettre à jour une copie de langue avec les versions modifiées des ressources d’origine, la copie de langue existante est conservée jusqu’à ce que vous approuviezles ressources traduites. [!DNL Assets] stocke les nouvelles ressources traduites dans un emplacement temporaire et met à jour la copie de langue existante après votre approbation explicite des ressources. Si vous refusez les ressources, la copie de langue reste inchangée.

1. Sélectionnez le dossier racine source sous **[!UICONTROL Copies de langue]** pour lequel vous avez déjà créé une copie de langue, puis sélectionnez **[!UICONTROL Afficher dans Assets]** pour ouvrir le dossier dans [!DNL Assets].
1. Dans l’interface utilisateur d’Assets, sélectionnez une ressource que vous avez déjà traduite, puis sélectionnez l’icône **[!UICONTROL Modifier]** dans la barre d’outils pour ouvrir la ressource en mode d’édition.
1. Modifiez la ressource et enregistrez les modifications.
1. Exécutez les étapes 2 à 14 de la procédure [Ajouter à un projet de traduction existant](#add-to-existing-translation-project) pour mettre à jour la copie de langue.
1. Sélectionnez les points de suspension en bas de la mosaïque **[!UICONTROL Tâche de traduction]**. Dans la liste des ressources sur la page **[!UICONTROL Tâche de traduction]**, vous pouvez voir l’emplacement temporaire dans lequel la version traduite de la ressource est stockée.
1. Cochez la case en regard de **[!UICONTROL Titre]**.
1. Dans la barre d’outils, sélectionnez **[!UICONTROL Accepter la traduction]** puis sélectionnez **[!UICONTROL Accepter]** dans la boîte de dialogue pour remplacer la ressource traduite dans le dossier cible par la version traduite de la ressource modifiée.

   >[!NOTE]
   >
   >Pour permettre au workflow de traduction de mettre à jour la ou les ressources de destination, acceptez à la fois la ressource et les métadonnées.

   Sélectionnez **[!UICONTROL Rejeter la traduction]** pour conserver la version traduite d’origine de la ressource dans la racine des paramètres régionaux cibles et rejeter la version modifiée.

1. Accédez à la console Ressources et ouvrez la page Propriétés de chacune des ressources traduites afin d’afficher les métadonnées traduites.

<!-- TBD: Possibly this blog was not migrated. Still try to find from the author. Old one is archived at https://web.archive.org/web/20180423042713/https://blogs.adobe.com/experiencedelivers/experience-management/translate_aemassets_metadata/

For tips on translating metadata for assets efficiently, see [5 Steps to efficiently translate metadata](https://blogs.adobe.com/experiencedelivers/experience-management/translate_aemassets_metadata/). 
-->

## Création de projets de traduction {#creating-translation-projects}

Pour créer une copie de langue, déclenchez l’un des workflows de copie de langue disponibles sous le rail Références dans l’interface utilisateur d’Assets :

**Créer et traduire**

Dans ce workflow, les ressources à traduire sont copiées dans la racine de la langue vers laquelle vous souhaitez effectuer la traduction. En outre, en fonction des options que vous choisissez, un projet de traduction est créé pour les ressources dans la console Projets. Selon les paramètres, le projet de traduction peut être démarré manuellement ou exécuté automatiquement dès sa création.

**Mise à jour des copies de langue**

Vous exécutez ce workflow afin de traduire un groupe de ressources supplémentaire et de l’intégrer à une copie de langue pour des paramètres régionaux spécifiques. Dans ce cas, les ressources traduites sont ajoutées au dossier cible qui contient des ressources précédemment traduites.

>[!NOTE]
>
>Les fichiers binaires des ressources ne sont traduits que si le fournisseur de traduction prend en charge la traduction des fichiers binaires.

>[!NOTE]
>
>Si vous lancez un workflow de traduction de ressources complexes, telles que des fichiers PDF et Adobe InDesign, leurs sous-ressources ou rendus (le cas échéant) ne sont pas soumis pour traduction.

### Workflow Créer et traduire {#create-and-translate-workflow}

Vous utilisez le workflow Créer et traduire afin de générer des copies de langue dans une langue spécifique pour la première fois. Le workflow offre les options suivantes :

* Créer uniquement la structure
* Créer un projet de traduction
* Ajouter à un projet de traduction existant

### Création de la structure uniquement {#create-structure-only}

Utilisez l’option **Créer uniquement la structure** pour créer une hiérarchie de dossiers cible au niveau de la racine de la langue cible semblable à celle du dossier source au sein de la racine de la langue source. Dans ce cas, les fichiers source sont copiés dans le dossier de destination. Cependant, aucun projet de traduction n’est généré.

1. Dans l’interface utilisateur d’Assets, sélectionnez le dossier source pour lequel vous souhaitez créer une structure au niveau de la racine de la langue cible.
1. Ouvrez le volet **[!UICONTROL Références]** et sélectionnez **[!UICONTROL Copies de langue]** sous **[!UICONTROL Copies]**.
1. Sélectionnez **[!UICONTROL Créer et traduire]** en bas de la page.
1. Dans la liste **[!UICONTROL Langues cibles]**, choisissez la langue pour laquelle vous souhaitez créer une structure de dossiers.
1. Dans la liste **[!UICONTROL Projet]**, sélectionnez **[!UICONTROL Créer uniquement la structure]**.
1. Sélectionnez **[!UICONTROL Créer]**. La nouvelle structure de la langue cible est répertoriée sous **[!UICONTROL Copies de langue]**.
1. Sélectionnez la structure dans la liste, puis sélectionnez **[!UICONTROL Afficher dans Assets]** pour accéder à la structure de dossiers au sein de la langue cible.

## Application de services cloud de traduction à des dossiers {#applying-translation-cloud-services-to-folders}

Adobe Experience Manager vous offre des services de traduction basés sur le cloud du fournisseur de traduction de votre choix afin de vous assurer que vos ressources sont traduites en fonction de vos besoins.

Vous pouvez appliquer le service cloud de traduction directement à votre dossier de ressources afin qu’elles puissent être utilisées au cours des workflows de traduction.

### Application de services de traduction {#applying-the-translation-services}

L’application de services cloud directement à votre dossier de ressources élimine le besoin de configurer des services de traduction lorsque vous créez ou mettez à jour les workflows de traduction.

1. Depuis l’interface utilisateur d’Assets, sélectionnez le dossier auquel vous souhaitez appliquer des services de traduction.
1. Dans la barre d’outils, sélectionnez l’icône **[!UICONTROL Propriétés]** pour afficher la page **[!UICONTROL Propriétés du dossier]**.

   ![chlimage_1-215](assets/chlimage_1-215.png)

1. Accédez à l’onglet **[!UICONTROL Services Cloud]**.
1. Depuis la liste Configurations du service Cloud, sélectionnez le fournisseur de services de traduction de votre choix. Par exemple, si vous souhaitez utiliser les services de traduction de Microsoft, choisissez **[!UICONTROL Microsoft Translator]**.

   ![chlimage_1-216](assets/chlimage_1-216.png)

1. Sélectionnez le connecteur pour le fournisseur de traduction.

   ![chlimage_1-217](assets/chlimage_1-217.png)

1. Dans la barre d’outils, sélectionnez **[!UICONTROL Enregistrer]**, puis cliquez sur **[!UICONTROL OK]** pour fermer la boîte de dialogue. Le service de traduction est appliqué au dossier.

### Application d’un connecteur de traduction personnalisé {#applying-custom-translation-connector}

Si vous souhaitez appliquer un connecteur personnalisé pour les services de traduction que vous souhaitez utiliser dans les workflows de traduction. Pour appliquer un connecteur personnalisé, installez d’abord le connecteur à partir du [gestionnaire de modules](/help/implementing/developing/tools/package-manager.md). Configurez ensuite le connecteur depuis la console Cloud Services. Une fois le connecteur configuré, il est disponible dans la liste des connecteurs de l’onglet Cloud Services décrits dans la section [Application des services de traduction](#applying-the-translation-services). Une fois que vous avez appliqué le connecteur personnalisé et exécuté des workflows de traduction, la mosaïque **[!UICONTROL Résumé de traduction]** du projet de traduction affiche les détails du connecteur dans les sections **[!UICONTROL Fournisseur]** et **[!UICONTROL Méthode]**.

1. Installez le connecteur depuis le [Gestionnaire de modules](/help/implementing/developing/tools/package-manager.md).
1. Sélectionnez le logo Experience Manager et accédez à **[!UICONTROL Outils > Déploiement > Services cloud]**.
1. Localisez le connecteur que vous avez installé sous **[!UICONTROL Services tiers]** sur la page **[!UICONTROL Services Cloud]**.

   ![chlimage_1-218](assets/chlimage_1-218.png)

1. Sélectionnez le lien **[!UICONTROL Configurer maintenant]** pour ouvrir la boîte de dialogue **[!UICONTROL Créer une configuration]**.

   ![chlimage_1-219](assets/chlimage_1-219.png)

1. Indiquez un titre et un nom pour le connecteur, puis sélectionnez **[!UICONTROL Créer]**. Le connecteur personnalisé est alors disponible dans la liste des connecteurs de l’onglet **[!UICONTROL Services Cloud]** décrit à l’étape 5 de la section [Application des services de traduction](#applying-the-translation-services).
1. Exécutez n’importe quel workflow de traduction tel que décrit dans la section Création de projets de traduction après avoir appliqué le connecteur personnalisé. Vérifiez les informations détaillées du connecteur dans la mosaïque **[!UICONTROL Résumé de traduction]** du projet de traduction dans la console **[!UICONTROL Projets]**.

   ![chlimage_1-220](assets/chlimage_1-220.png)

**Voir également**

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
