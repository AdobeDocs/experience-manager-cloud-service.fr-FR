---
title: Paramètres prédéfinis de lot
description: Découvrez comment automatiser la création de visionneuses d’images et de visionneuses à 360° à l’aide des paramètres prédéfinis de lot de Dynamic Media.
contentOwner: Rick Brough
feature: Image Presets,Viewer Presets
role: User
exl-id: 022ee347-54ec-4cec-b808-9eb3a9e51424
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
workflow-type: tm+mt
source-wordcount: '3434'
ht-degree: 98%

---

# À propos des paramètres prédéfinis de lot {#about-bsp}

Utilisez les **[!UICONTROL paramètres prédéfinis de lot]** pour créer et organiser différentes ressources dans une visionneuse d’images ou une visionneuse à 360° lorsque vous chargez des fichiers de ressources dans un dossier, individuellement ou par une ingestion en masse. Il est possible d’exécuter le paramètre prédéfini en même temps que les tâches d’importation de ressources planifiées dans [!DNL Dynamic Media]. Chaque paramètre prédéfini est un ensemble d’instructions indépendant possédant un nom unique. Il définit comment construire la visionneuse d’images ou la visionneuse à 360° à l’aide d’images correspondant aux conventions d’affectation des noms définies dans la recette du paramètre prédéfini.

>[!IMPORTANT]
>
>Utilisez-vous des paramètres prédéfinis d’ensemble par lot dans [!DNL Dynamic Media Classic] et effectuez-vous une migration de [!DNL Dynamic Media Classic] vers Adobe Experience Manager as a Cloud Service ? Si tel est le cas, vous devez recréer manuellement les définitions de paramètres prédéfinis d’ensemble par lot dans [!DNL Adobe Experience Manager as a Cloud Service].

**Bonne pratique** : lorsque vous utilisez des paramètres prédéfinis de lot, Adobe recommande le workflow suivant :

1. Créez un paramètre prédéfini de lot. Voir [Création d’un paramètre prédéfini de lot pour une visionneuse d’images ou une visionneuse à 360°](#creating-bsp).
1. Créez un dossier de ressources ou utilisez un dossier de ressources existant et assurez-vous qu’il est synchronisé avec [!DNL Dynamic Media]. Voir [Création de dossiers](/help/assets/manage-digital-assets.md#creating-folders).
1. Appliquez le paramètre prédéfini de lot au dossier de ressources. Voir [À propos de l’application des paramètres prédéfinis de lot aux dossiers](#apply-bsp).
1. Chargez les images vers le dossier de ressources. Voir [Chargement de ressources pour les visionneuses d’images](/help/assets/dynamic-media/image-sets.md#uploading-assets-in-image-sets), [Chargement de ressources pour les visionneuses à 360°](/help/assets/dynamic-media/spin-sets.md#uploading-assets-for-spin-sets) ou [Ajout de ressources numériques à Adobe Experience Manager](/help/assets/add-assets.md#add-assets-to-experience-manager).
1. La visionneuse d’images ou à 360° est générée automatiquement dans le dossier souhaité.
1. Publiez votre visionneuse d’images ou votre visionneuse à 360°. Voir [Publication de ressources Dynamic Media](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

## Création d’un paramètre prédéfini de lot pour une visionneuse d’images ou une visionneuse à 360° {#creating-bsp}

Pour créer des paramètres prédéfinis de lot, il est souhaitable de connaître et de comprendre les expressions régulières.

Idéalement, votre société a déjà défini une convention d’affectation des noms concernant le mode de regroupement des ressources dans un ensemble.
Pour vous aider à comprendre l’importance d’une convention d’affectation des noms, supposons que cette convention définie soit `<style>-<color>-<view>`. De plus, le nom de base de l’ensemble doit toujours être `<style>-<color>` et l’extension du nom de l’ensemble doit être `-SET`. Si vous chargez une image nommée `0123-RED-01`, un ensemble nommé `0123-RED-SET` est créé. Si vous chargez ultérieurement des images `0123-RED-03` et `0123-BLUE-01`, l’image `RED-03` sera ajoutée à la visionneuse en deuxième position, car le tri la place au-dessous de `01`. Cependant, l’image `BLUE-01` fait partie d’un nouvel ensemble nommé `0123-BLUE-SET`. Lors du chargement de ressources suivant, vous ajoutez les fichiers `0123-RED-02` et `0123-BLUE-02`. Chaque ressource devrait être ajoutée à son ensemble respectif. L’image `RED-02` devrait être automatiquement placée entre les images `01` et `03` existantes, en raison de l’ordre de tri.

La page **[!UICONTROL Paramètre prédéfini de lot]** de [!DNL Dynamic Media] permet de créer, modifier ou supprimer des paramètres prédéfinis de lot, mais aussi d’appliquer ces paramètres à des dossiers de ressources ou de les y supprimer. Vous pouvez utiliser les listes déroulantes du champ de formulaire pour définir un paramètre prédéfini de lot ou utiliser le champ **[!UICONTROL Code brut]**, qui vous permet de saisir la syntaxe d’expression régulière.

Vous pouvez créer de nombreux paramètres prédéfinis de lot pour répondre aux besoins de toutes vos tâches d’ingestion de ressources.

### À propos de la convention d’affectation des noms de ressources

La zone **[!UICONTROL Convention d’affectation des noms de ressources]** de la page **[!UICONTROL Paramètre prédéfini de lot]** contient deux éléments utilisables pour définir votre paramètre prédéfini de lot : **[!UICONTROL Correspondance]** et **[!UICONTROL Nom de base]**. Ces éléments vous permettent de définir une convention d’affectation des noms et d’identifier la partie de la convention utilisée pour nommer la visionneuse dans laquelle ils se trouvent. <!-- While **[!UICONTROL Match]** is required, **[!UICONTROL Base Name]** is mandatory only if the **[!UICONTROL Match]** field does not already specify a base name through the use of a bracket grouping. -->

La convention de nommage individuelle d’une entreprise utilise souvent une ou plusieurs lignes de définition de chacun de ces deux éléments. Vous pouvez utiliser autant de lignes que vous le souhaitez pour votre définition unique et les regrouper dans des éléments distincts, par exemple, pour l’image principale, les éléments Couleur, Affichage secondaire et Échantillon.

Par exemple, la syntaxe d’une expression régulière avec correspondance littérale peut se présenter comme suit :

`(\w+)-\w+-\w+`

### À propos du tri séquentiel

Vous pouvez éventuellement définir l’ordre d’affichage des images après le regroupement de la visionneuse d’images ou de la visionneuse à 360° dans [!DNL Dynamic Media]. Par défaut, vos ressources sont classées par ordre alphanumérique. Cependant, vous pouvez utiliser une liste d’expressions régulières séparées par des virgules pour définir l’ordre.

En ce qui concerne l’automatisation du tri séquentiel, vous spécifiez des règles pour forcer le tri des ressources selon une méthode déterminée, si nécessaire. Supposons, par exemple, que votre première ressource soit toujours nommée `_main` et que vous souhaitiez qu’elle soit suivie de `_alt1`, `_alt2`, `_alt3`, etc. Dans ce cas, vous pouvez créer une règle de tri séquentiel selon la syntaxe suivante :

`.*_main,.*_alt[0-9]`

Bien qu’un tri séquentiel forcé soit possible, il est préférable de se baser autant que possible sur la numérotation alphanumérique pour le tri séquentiel. En outre, vous pouvez utiliser les outils d’éditeur de visionneuse d’images ou de visionneuse à 360° de [!DNL Dynamic Media] pour réorganiser l’ordre séquentiel des ressources, ou ajouter et supprimer de nouvelles ressources dans la visionneuse par une opération glisser-déposer.

Lorsque vous avez terminé de créer un paramètre prédéfini de lot, vous l’appliquez à un ou plusieurs des dossiers créés. Voir [À propos de l’application des paramètres prédéfinis de lot aux dossiers](#apply-bsp).

<!-- See also [Creating a batch set preset for the auto generation of a 2D Spin Set](application-setup.md#creating_a_batch_set_preset_for_the_auto_generation_of_a_2d_spin_set). -->

**Pour créer un paramètre prédéfini de lot pour une visionneuse d’images ou une visionneuse à 360° :**

1. Sélectionnez le logo Experience Manager et accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Paramètres prédéfinis de lot]**.

   ![bsp-create1.png](/help/assets/assets-dm/bsp-create1.png)

1. Sur la page **[!UICONTROL Paramètres prédéfinis de lot]**, près de l’angle supérieur droit, sélectionnez **[!UICONTROL Créer]**.
1. Dans la boîte de dialogue **[!UICONTROL Créer un paramètre prédéfini de lot]**, dans le champ **[!UICONTROL Nom du paramètre prédéfini]**, saisissez un nom descriptif. Le nom du paramètre prédéfini n’est pas modifiable si vous décidez de le modifier ultérieurement.

1. Dans la liste déroulante **[!UICONTROL Type de paramètre prédéfini]**, sélectionnez **[!UICONTROL ImageSet]** ou **[!UICONTROL SpinSet]**. Veillez à choisir le type de paramètre prédéfini approprié ; il ne sera pas modifiable ultérieurement.
1. Sélectionnez **[!UICONTROL Créer]**.
1. Sur le côté droit de la page **[!UICONTROL Modifier le paramètre prédéfini de lot]**, définissez les options modifiables de votre choix sous les en-têtes **[!UICONTROL Détails du paramètre prédéfini]** et **[!UICONTROL Définir la convention d’affectation des noms]**.
Pour en savoir plus sur les options modifiables disponibles, voir [Détails des paramètres prédéfinis, convention d’affectation des noms et résultats des règles – RegX](#features-options-bsp).

   ![bsp-create4.png](/help/assets/assets-dm/bsp-create4.png)

1. Créez un ou plusieurs groupes d’expressions régulières.

   * Sur le côté gauche de la page **[!UICONTROL Modifier le paramètre prédéfini de lot]**, sous **[!UICONTROL Correspondance]**, **[!UICONTROL Nom de base]** ou **[!UICONTROL Tri séquentiel]**, sélectionnez **[!UICONTROL Ajouter un groupe]**.
   * Le champ **[!UICONTROL Correspondance]** est obligatoire. Le **[!UICONTROL Nom de base]** n’est obligatoire que si le champ **[!UICONTROL Correspondance]** ne spécifie pas déjà un nom de base à l’aide d’un regroupement entre crochets. Le **[!UICONTROL Tri séquentiel]** est facultatif.
   * Avec les listes déroulantes et les zones de texte du formulaire du groupe, spécifiez un groupe d’expressions que vous souhaitez utiliser pour définir les critères d’affectation de noms pour les ressources de la visionneuse d’images ou de la visionneuse à 360°.
      * Lorsque vous sélectionnez et spécifiez des expressions pour un groupe, notez que la syntaxe réelle de l’expression régulière est reflétée en bas, à droite de la page, sous l’en-tête **[!UICONTROL Résultats de la règle – RegX]**. Pour afficher la chaîne d’expression régulière mise à jour en bas à droite, sélectionnez n’importe où en dehors de la zone de formulaire. Ces chaînes d’expression régulière représentent le modèle que vous souhaitez mettre en correspondance dans une recherche de ressources [!DNL Dynamic Media] pour créer votre visionneuse d’images ou votre visionneuse à 360°.
      * Si vous avez ajouté un groupe et souhaitez le supprimer, sélectionnez **[!UICONTROL X]**.
   * Lorsque vous ajoutez deux groupes ou plus, dans la liste déroulante **[!UICONTROL Et]**, sélectionnez **[!UICONTROL Et]** pour joindre un groupe récemment ajouté à un groupe d’expressions précédent ajouté. Ou, sélectionnez **[!UICONTROL Ou]** pour ajouter une alternative entre le groupe d’expressions précédent et le groupe créé. L’opérande **[!UICONTROL Ou]** est défini par l’utilisation d’un caractère de ligne verticale `|` dans la syntaxe de l’expression régulière elle-même.

1. Utilisez l’une des méthodes suivantes :

   * Pour ajouter un autre nouveau groupe, sous **[!UICONTROL Correspondance]**, **[!UICONTROL Nom de base]** ou **[!UICONTROL Tri séquentiel]**, sélectionnez **[!UICONTROL Ajouter un groupe]**. Créez un autre groupe d’expressions régulières comme à l’étape précédente.
   * Examinez la syntaxe d’expression régulière dans la zone **[!UICONTROL Résultats de la règle – RegX]**. Si vous devez modifier la syntaxe, effectuez vos modifications dans le groupe correspondant à gauche de la page.
   * Si vous avez terminé de créer des groupes d’expressions, passez à l’étape suivante.

1. Dans le coin supérieur droit de la page, sélectionnez **[!UICONTROL Enregistrer]**.

Vous êtes maintenant prêt à appliquer le paramètre prédéfini d’ensemble par lot à un dossier de ressources. Ensuite, vous téléchargez les éléments dans ce dossier. Ce workflow génère automatiquement la visionneuse d’images ou à 360°. Voir [À propos de l’application des paramètres prédéfinis de lot aux dossiers de ressources](#apply-bsp).

### Détails des paramètres prédéfinis, convention d’affectation des noms et résultats des règles – RegX {#features-options-bsp}

Ces options sont disponibles sur la page **[!UICONTROL Modifier le paramètre prédéfini de lot]** lorsque vous créez ou modifiez un paramètre prédéfini de lot.

Voir [Création d’un paramètre prédéfini de lot pour une visionneuse d’images ou une visionneuse à 360°](#creating-bsp) ou [Modification d’un paramètre prédéfini de lot](#edit-bsp).

| **[!UICONTROL Détails du paramètre prédéfini]** | Description |
| --- | --- |
| Nom du paramètre prédéfini | Lecture seule. Nom spécifié lors de la première création du lot. Si vous devez renommer le paramètre prédéfini, vous pouvez copier le paramètre prédéfini de lot existant et spécifier un nouveau nom. Voir [Copie d’un paramètre prédéfini de lot existant](#copy-bsp). |
| Type | Lecture seule. Le type a été spécifié lors de la première création du lot. La copie d’un paramètre prédéfini de lot existant ne vous permet pas de modifier son [!UICONTROL type] ; vous devez créer un paramètre prédéfini. |
| Inclure les ressources dérivées | Facultatif. Pour que l’IPS (Image Production System) de [!DNL Dynamic Media] intègre des images générées ou « dérivées » à votre visionneuse à 360° ou votre visionneuse d’images, sélectionnez **[!UICONTROL Oui]** (par défaut). Une ressource dérivée est une image qui n’a pas été directement chargée par un utilisateur. Au lieu de cela, la ressource a été produite par l’IPS lors du chargement d’une ressource principale. Par exemple, une ressource d’image générée par l’IPS à partir d’une page d’un fichier PDF, au moment où le fichier PDF a été chargé dans [!DNL Dynamic Media], est considérée comme une ressource dérivée. |
| Dossier de destination | Facultatif. Si vous définissez un grand nombre de visionneuses d’images ou de visionneuses à 360°, Adobe recommande de conserver séparément des dossiers contenant les ressources elles-mêmes. Ainsi, vous pouvez envisager de créer un dossier Visionneuses d’images ou Visionneuses à 360° et de rediriger l’application pour y placer les visionneuses créées sous forme de lots.<br>Dans ce cas, spécifiez le dossier dans la structure de dossiers Experience Manager Assets (`/content/dam`) pour lequel le paramètre prédéfini de lot doit être actif. Assurez-vous que le dossier est activé pour la synchronisation de [!DNL Dynamic Media] afin de l’autoriser en tant que dossier de destination. Voir [Configuration de la publication sélective au niveau des dossiers dans Dynamic Media](/help/assets/dynamic-media/selective-publishing.md#selective-publish-configure-folder).<br> Plusieurs dossiers peuvent être dotés d’un paramètre prédéfini de lot donné si vous appliquez ce paramètre au moyen des **[!UICONTROL Propriétés]** du dossier. Voir [Application de paramètres prédéfinis de lot à partir de la page Propriétés d’un dossier de ressources](#apply-bsp-to-folders-via-properties).<br>Si vous ne spécifiez pas de dossier, la visionneuse d’images ou la visionneuse à 360° générée par un paramètre prédéfini d’ensemble par lot est créée dans le même dossier que le dossier de ressources dans lequel vous avez chargé le fichier. |
| **[!UICONTROL Définir la convention d’affectation des noms]** |  |
| Préfixe<br>ou<br>Suffixe | Facultatif. Entrez un préfixe, un suffixe ou les deux dans les champs respectifs.<br>Les champs de préfixe et de suffixe permettent de créer de nombreux paramètres prédéfinis de lot à l’aide d’une autre convention personnalisée d’affectation de noms de fichier pour un ensemble de contenu particulier. Cette méthode est particulièrement utile dans les cas où il existe une exception à un schéma d’affectation de nom par défaut défini par une société.<br>Le préfixe ou le suffixe est ajouté au **[!UICONTROL nom de base]** que vous définissez dans la zone **[!UICONTROL Convention d’affectation des noms de ressources]**. En ajoutant un préfixe ou un suffixe, vous vous assurez que la visionneuse d’images ou la visionneuse à 360° est créée de manière exclusive et indépendante des autres ressources. Cette opération peut également aider d’autres personnes à identifier les types de fichiers. Par exemple, pour déterminer un mode de couleur utilisé, vous pouvez ajouter comme préfixe ou suffixe `rgb` ou `cmyk`.<br>Bien que la spécification d’une convention d’affectation des noms d’ensemble ne soit pas nécessaire pour utiliser la fonctionnalité de paramètre prédéfini de lot, il est recommandé d’appliquer une telle convention. Cette pratique permet de définir autant d’éléments de convention d’affectation des noms que vous souhaitez regrouper pour simplifier la création d’ensembles par lot. |
| **[!UICONTROL Résultats de la règle – RegX]** |  |
| Convention d’affectation des noms de ressources – Correspondance | Lecture seule. Affiche la syntaxe d’expression régulière en fonction des options de formulaire de correspondance que vous avez sélectionnées ou du code brut que vous avez saisi. |
| Convention d’affectation des noms de ressources – Nom de base | Lecture seule. Affiche la syntaxe d’expression régulière en fonction des options de formulaire de nom de base que vous avez sélectionnées ou du code brut que vous avez saisi. |
| Ordre des séquences – Correspondance | Lecture seule. Affiche la syntaxe d’expression régulière en fonction des options de formulaire que vous avez sélectionnées ou du code brut que vous avez saisi. |

## À propos de l’application de paramètres prédéfinis de lot aux dossiers {#apply-bsp}

Lorsque vous affectez des paramètres prédéfinis de lot à un ou plusieurs dossiers de ressources, tous les sous-dossiers héritent automatiquement des paramètres prédéfinis de leur dossier parent.

Vous pouvez appliquer plusieurs paramètres prédéfinis de lot à un dossier de ressources.

Les dossiers auxquels un paramètre prédéfini de lot est affecté sont indiqués dans l’interface utilisateur avec le nom du paramètre prédéfini affiché dans le dossier, dans la vue **[!UICONTROL Carte]**.

Pour appliquer des paramètres prédéfinis de lot aux dossiers, utilisez l’une des deux méthodes suivantes :

* [Appliquer des paramètres prédéfinis de lot aux dossiers de ressources à l’aide de la page Paramètre prédéfini de lot](#apply-bsp-to-folders-via-bsp-page). Cette méthode offre une flexibilité maximale. Vous pouvez appliquer un ou plusieurs paramètres prédéfinis à un ou plusieurs dossiers.
* [Appliquer des paramètres prédéfinis de lot à partir de la page Propriétés d’un dossier de ressources](#apply-bsp-to-folders-via-properties). Cette méthode permet d’appliquer un ou plusieurs paramètres prédéfinis de lot à un seul dossier.

Il est recommandé de s’assurer que les dossiers de ressources sont synchronisés avec [!DNL Dynamic Media], puis d’appliquer les paramètres prédéfinis de votre choix.

Retraitez les fichiers d’un dossier si vous rencontrez l’une des deux situations suivantes :

* Vous souhaitez appliquer un paramètre prédéfini de lot à un dossier de ressources existant dans lequel des ressources ont déjà été téléchargées.
* Vous modifiez ensuite un paramètre prédéfini de lot existant qui était précédemment appliqué à un dossier de ressources.

<!-- See [Reprocessing assets in a folder](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets). -->

### Application de paramètres prédéfinis de lot aux dossiers de ressources à l’aide de la page Paramètres prédéfinis de lot {#apply-bsp-to-folders-via-bsp-page}

1. Sélectionnez le logo Experience Manager et accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Paramètres prédéfinis de lot]**.
1. Sur la page **[!UICONTROL Paramètres prédéfinis de lot]**, à gauche de la colonne **[!UICONTROL Nom du paramètre prédéfini]**, cochez la case de chaque paramètre prédéfini de lot à appliquer aux dossiers.
1. Dans la barre d’outils, sélectionnez **[!UICONTROL Appliquer le paramètre prédéfini de lot aux dossiers]**.
1. Sur la page **[!UICONTROL Sélectionner les dossiers]**, cochez la case de chaque dossier auquel vous voulez appliquer les paramètres prédéfinis de lot.
1. Dans l’angle supérieur droit de la page **[!UICONTROL Sélectionner les dossiers]**, sélectionnez **[!UICONTROL Appliquer]**.

### Application de paramètres prédéfinis de lot à partir de la page Propriétés d’un dossier de ressources {#apply-bsp-to-folders-via-properties}

1. Sélectionnez le logo Experience Manager et accédez à **[!UICONTROL Ressources]** > **[!UICONTROL Fichiers]**.
1. Accédez au dossier dans lequel vous souhaitez appliquer un ou plusieurs paramètres prédéfinis de lot.
1. Sur la page, à gauche de la colonne **[!UICONTROL Nom]**, cochez la case d’un dossier.
1. Dans la barre d’outils, sélectionnez **[!UICONTROL Propriétés]**.
1. Dans la page Propriétés du dossier, sélectionnez l’onglet **[!UICONTROL Traitement Dynamic Media]**.

   ![bsp-apply-via-properties2.png](/help/assets/assets-dm/bsp-apply-via-properties2a.png)

1. Sous **[!UICONTROL Paramètres prédéfinis de lot]**, sélectionnez le nom d’un paramètre prédéfini de lot à appliquer dans la liste déroulante **[!UICONTROL Nom du paramètre prédéfini]**. La capture d’écran ci-dessus montre deux paramètres prédéfinis de lot sélectionnés, appliqués au dossier de ressources.

   S’il n’existe aucun nom de paramètre prédéfini de lot dans la zone de liste déroulante **[!UICONTROL Nom du paramètre prédéfini]**, cela signifie que vous n’avez pas encore créé ce paramètre. Voir [Création d’un paramètre prédéfini de lot pour une visionneuse d’images ou une visionneuse à 360°](#creating-bsp).

   Pour supprimer un paramètre prédéfini de lot appliqué, sélectionnez **[!UICONTROL X]** à droite du type de paramètre prédéfini.

1. Dans l’angle supérieur droit de la page, sélectionnez **[!UICONTROL Enregistrer et fermer]**.

## Modification d’un paramètre prédéfini de lot {#edit-bsp}

Vous pouvez modifier un paramètre prédéfini de lot existant que vous avez créé. Vous pouvez modifier n’importe quel groupe d’expressions que vous avez créé pour la convention d’affectation des noms de ressource ou le tri séquentiel. Si nécessaire, vous pouvez également mettre à jour le dossier de destination et définir des conventions d’affectation des noms.

Toutefois, vous ne pouvez pas modifier le nom ni le type de paramètre prédéfini (visionneuse d’images ou visionneuse à 360°). S’il devient nécessaire de modifier le nom d’un paramètre prédéfini, copiez le paramètre prédéfini existant et spécifiez un nouveau nom. Voir [Copie d’un paramètre prédéfini de lot](#copy-bsp).

Si vous modifiez un paramètre prédéfini de lot précédemment appliqué à un dossier, ce nouveau paramètre n’est appliqué qu’aux nouvelles ressources chargées dans le dossier.

Si vous souhaitez que ce paramètre prédéfini modifié soit réappliqué aux ressources existantes du dossier, vous devez retraiter le dossier. <!-- See [Reprocessing assets in a folder](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets). -->Ainsi, les ressources existantes pourraient désormais être incluses dans une visionneuse d’images ou une visionneuse à 360° et y être ajoutées. En outre, les ressources existantes qui étaient déjà incluses dans la visionneuse d’images ou la visionneuse à 360°, en fonction du paramètre prédéfini de lot précédent utilisé, ne sont pas supprimées et sont affichées en l’état. Ce scénario suppose qu’ils ne sont plus qualifiés en fonction du paramètre prédéfini nouvellement modifié.

**Pour modifier un paramètre prédéfini de lot :**

1. Sélectionnez le logo Experience Manager et accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Paramètres prédéfinis de lot]**.
1. Sur la page **[!UICONTROL Paramètres prédéfinis de lot]**, à gauche de la colonne **[!UICONTROL Nom du paramètre prédéfini]**, vérifiez le paramètre prédéfini de lot que vous souhaitez modifier.
1. Dans la barre d’outils, sélectionnez **[!UICONTROL Modifier le paramètre prédéfini de lot]**.
1. Modifiez le paramètre prédéfini selon vos besoins.
1. Dans l’angle supérieur droit de la page **[!UICONTROL Paramètre prédéfini de lot]**, sélectionnez **[!UICONTROL Enregistrer]**.

## Copie d’un paramètre prédéfini de lot existant {#copy-bsp}

Vous pouvez copier un paramètre prédéfini de lot existant pour éviter d’avoir à recréer manuellement un paramètre prédéfini complexe ou simplement pour renommer un paramètre prédéfini. Toutefois, vous ne pouvez pas modifier le type de paramètre prédéfini (visionneuse d’images ou visionneuse à 360°).

Si vous copiez un paramètre prédéfini existant référencé par des dossiers de ressources, ces dossiers ne sont pas concernés.

**Copie d’un paramètre prédéfini de lot existant:**

1. Sélectionnez le logo Experience Manager et accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Paramètres prédéfinis de lot]**.
1. Sur la page **[!UICONTROL Paramètres prédéfinis de lot]**, à gauche de la colonne **[!UICONTROL Nom du paramètre prédéfini]**, cochez la case du paramètre prédéfini de lot à copier.
1. Dans la barre d’outils, sélectionnez **[!UICONTROL Copie]**.
1. Dans la boîte de dialogue **[!UICONTROL Copier le paramètre prédéfini de lot]**, dans la zone de texte **[!UICONTROL Titre]**, saisissez un nouveau nom pour le paramètre prédéfini.

   ![bsp-copy2.png](/help/assets/assets-dm/bsp-copy2.png)

1. Sélectionnez **[!UICONTROL Copie]**.

## À propos de la suppression des paramètres prédéfinis de lot dans les dossiers {#remove-bsp-from-folder}

Lorsque vous supprimez des paramètres prédéfinis de lot dans des dossiers, les nouvelles ressources chargées vers ces dossiers ne seront pas associées au paramètre prédéfini de lot. Les ressources existantes du dossier déjà ajoutées à la visionneuse d’images ou à la visionneuse à 360°, en fonction du paramètre prédéfini de lot appliqué au dossier, continuent à s’afficher en l’état.

Si vous souhaitez plutôt *supprimer* les paramètres prédéfinis des dossiers, voir [Suppression des paramètres prédéfinis de lot](#delete-bsp).

Vous pouvez utiliser deux méthodes pour supprimer des paramètres prédéfinis de lot des dossiers.

* [Suppression des paramètres prédéfinis de lot des dossiers par le biais de la page Paramètres prédéfinis de lot](#remove-bsp-from-folders-via-bsp-page). Cette méthode offre une flexibilité maximale. Vous pouvez supprimer un ou plusieurs paramètres prédéfinis dans un ou plusieurs dossiers.
* [Suppression des paramètres prédéfinis de lot à partir de la page Propriétés d’un dossier](#remove-bsp-from-folders-via-properties). Cette méthode permet de supprimer un ou plusieurs paramètres prédéfinis de lot d’un seul dossier.

### Suppression des paramètres prédéfinis de lot des dossiers par le biais de la page Paramètres prédéfinis de lot {#remove-bsp-from-folders-via-bsp-page}

1. Sélectionnez le logo Experience Manager et accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Paramètres prédéfinis de lot]**.
1. Sur la page **[!UICONTROL Paramètres prédéfinis de lot]**, à gauche de la colonne **[!UICONTROL Nom du paramètre prédéfini]**, cochez la case d’un ou de plusieurs paramètres prédéfinis de lot à supprimer d’un ou plusieurs dossiers.
1. Dans la barre d’outils, sélectionnez **[!UICONTROL Supprimer le paramètre prédéfini de lot des dossiers]**.

1. Sur la page **[!UICONTROL Sélectionner les dossiers]**, sélectionnez un ou plusieurs dossiers dans lesquels vous souhaitez supprimer les paramètres prédéfinis de lot.
1. Dans l’angle supérieur droit de la page **[!UICONTROL Sélectionner les dossiers]**, sélectionnez **[!UICONTROL Supprimer]**.

   ![bsp-remove-from-folders3.png](/help/assets/assets-dm/bsp-remove-from-folders3.png)

1. Dans la boîte de dialogue **[!UICONTROL Supprimer le profil]**, sélectionnez **[!UICONTROL Supprimer]**.

### Suppression de paramètres prédéfinis de lot à partir de la page Propriétés d’un dossier {#remove-bsp-from-folders-via-properties}

1. Sélectionnez le logo Experience Manager et accédez à **[!UICONTROL Ressources]** > **[!UICONTROL Fichiers]**.
1. Accédez au dossier dans lequel vous souhaitez supprimer un ou plusieurs paramètres prédéfinis de lot.
1. Sur la page, à gauche de la colonne **[!UICONTROL Nom]**, cochez la case d’un dossier.
1. Dans la barre d’outils, sélectionnez **[!UICONTROL Propriétés]**.
1. Dans la page Propriétés du dossier, sélectionnez **[!UICONTROL Traitement Dynamic Media]**.

   ![bsp-apply-via-properties2.png](/help/assets/assets-dm/bsp-remove-via-properties2.png)

1. Sous **[!UICONTROL Paramètres prédéfinis de lot]**, sélectionnez **[!UICONTROL X]** à droite du type de paramètre prédéfini.

1. Dans l’angle supérieur droit de la page, sélectionnez **[!UICONTROL Enregistrer et fermer]**.

## Suppression des paramètres prédéfinis de lot {#delete-bsp}

Vous pouvez supprimer des paramètres prédéfinis de lot pour les supprimer définitivement de [!DNL Dynamic Media]. En d’autres termes, ils ne s’affichent plus sur la page [!UICONTROL Paramètre prédéfini de lot] et ne s’affichent plus non plus dans la liste déroulante **[!UICONTROL Paramètres prédéfinis de lot]** de l’onglet **[!UICONTROL Traitement Dynamic Media]**, dans la page **[!UICONTROL Propriétés]** du dossier. Le paramètre prédéfini n’est donc pas appliqué aux ressources existantes lors d’un retraitement de dossier ou si de nouvelles ressources sont chargées dans le dossier.

Si vous supprimez un paramètre prédéfini précédemment appliqué à un ou plusieurs dossiers, les visionneuses d’images ou les visionneuses à 360° créées à partir de ressources de ces dossiers continuent de s’afficher en l’état.

Si vous souhaitez simplement *supprimer* les paramètres prédéfinis des dossiers, voir [Suppression des paramètres prédéfinis de lot des dossiers](#remove-bsp-from-folder).

**Pour supprimer des paramètres prédéfinis de lot :**

1. Sélectionnez le logo Experience Manager et accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Paramètres prédéfinis de lot]**.
1. Sur la page **[!UICONTROL Paramètres prédéfinis de lot]**, à gauche de la colonne **[!UICONTROL Nom du paramètre prédéfini]**, cochez la case d’un ou plusieurs paramètres prédéfinis de lot à supprimer.
1. Dans la barre d’outils, sélectionnez **[!UICONTROL Supprimer les paramètres prédéfinis de lot]**.

   ![bsp-delete2.png](/help/assets/assets-dm/bsp-delete2.png)

1. Dans la boîte de dialogue **[!UICONTROL Supprimer les paramètres prédéfinis de lot]**, sélectionnez **[!UICONTROL Supprimer]**.

   Si le paramètre prédéfini que vous supprimez a été référencé à l’aide d’un dossier de ressources, sélectionnez **[!UICONTROL Forcer la suppression]** à la place.

   ![bsp-delete3.png](/help/assets/assets-dm/bsp-delete3.png)

>[!MORELIKETHIS]
>
>* [Visionneuses d’images](/help/assets/dynamic-media/image-sets.md)
>* [Visionneuses à 360°](/help/assets/dynamic-media/spin-sets.md)
>* [Configuration de la publication sélective au niveau des dossiers dans Dynamic Media](/help/assets/dynamic-media/selective-publishing.md#selective-publish-configure-folder) – Voir Mode de synchronisation dans la rubrique pour en savoir plus sur la synchronisation d’un dossier unique avec [!DNL Dynamic Media].
>* [Création d’une configuration Dynamic Media dans Cloud Services](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services) – Voir la section Mode de synchronisation Dynamic Media de la rubrique pour en savoir plus sur la synchronisation de tous les dossiers avec [!DNL Dynamic Media].
