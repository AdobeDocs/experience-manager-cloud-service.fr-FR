---
title: Paramètres prédéfinis d’ensemble par lot
description: Découvrez comment automatiser la création de visionneuses d’images et de visionneuses à 360° à l’aide des paramètres prédéfinis d’ensemble par lot de Dynamic Media.
contentOwner: Rick Brough
translation-type: tm+mt
source-git-commit: c7a2fbb4fa6e81caabab829b876741ecf393a2c3
workflow-type: tm+mt
source-wordcount: '3521'
ht-degree: 3%

---


# À propos des paramètres prédéfinis d’ensemble par lot {#about-bsp}

Utilisez **[!UICONTROL Paramètres prédéfinis d’ensemble par lot]** pour faciliter la création et l’organisation de plusieurs fichiers dans une visionneuse d’images ou une visionneuse à 360° au moment où vous téléchargez des fichiers dans un dossier, individuellement ou par assimilation en masse. Le paramètre prédéfini peut être exécuté en même temps que les tâches d’importation de ressources planifiées dans [!DNL Dynamic Media]. Chaque paramètre prédéfini est un ensemble d’instructions indépendant à nom unique qui définit comment construire la visionneuse d’images ou la visionneuse à 360° à l’aide d’images qui correspondent aux conventions d’affectation de nom définies dans la recette de paramètres prédéfinis.

>[!IMPORTANT]
>
>Si vous avez utilisé des paramètres prédéfinis d’ensemble par lot dans [!DNL Dynamic Media Classic] et que vous migrez de [!DNL Dynamic Media Classic] vers Adobe Experience Manager en tant que Cloud Service, vous devrez recréer manuellement vos définitions de paramètres prédéfinis d’ensemble par lot dans [!DNL Adobe Experience Manager as a Cloud Service].

**Recommandé**  - Lorsque vous utilisez des paramètres prédéfinis d’ensemble par lot, l’Adobe recommande le processus suivant :

1. Créez un paramètre prédéfini d’ensemble par lot. Voir [Création d’un paramètre prédéfini d’ensemble par lot pour une visionneuse d’images ou une visionneuse à 360°](#creating-bsp).
1. Créez un dossier de ressources ou utilisez un dossier de ressources existant et assurez-vous qu’il est synchronisé avec [!DNL Dynamic Media]. Voir [Création de dossiers](/help/assets/manage-digital-assets.md#creating-folders).
1. Appliquez le paramètre prédéfini d’ensemble par lot au dossier Fichiers. Voir [A propos de l’application des paramètres prédéfinis d’ensemble par lot aux dossiers](#apply-bsp).
1. Téléchargez des images vers le dossier de fichiers. Voir [Téléchargement de fichiers pour les visionneuses d’images](/help/assets/dynamic-media/image-sets.md#uploading-assets-in-image-sets), [Téléchargement de fichiers pour les visionneuses à 360°](/help/assets/dynamic-media/spin-sets.md#uploading-assets-for-spin-sets) ou [Ajouter des ressources numériques à Adobe Experience Manager](/help/assets/add-assets.md#add-assets-to-experience-manager).
1. Créez votre visionneuse d’images ou votre visionneuse à 360°. Voir [Visionneuses d’images](/help/assets/dynamic-media/image-sets.md) ou [Visionneuses à 360°](/help/assets/dynamic-media/spin-sets.md).
1. Publiez votre visionneuse d’images ou votre visionneuse à 360°. Voir [Publication de ressources Dynamic Media](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

## Création d’un paramètre prédéfini d’ensemble par lot pour une visionneuse d’images ou une visionneuse à 360° {#creating-bsp}

Pour créer des paramètres prédéfinis d’ensemble par lot, il est souhaitable de connaître et de comprendre les expressions courantes.

Idéalement, votre société doit également avoir une convention d’affectation de nom définie pour la manière dont les ressources doivent être regroupées dans un ensemble.
Pour vous aider à comprendre l’importance de l’utilisation d’une convention d’affectation de nom, supposons que la convention d’affectation de nom définie par votre société est `<style>-<color>-<view>`. De plus, le nom de base de l&#39;ensemble doit toujours être `<style>-<color>` et l&#39;extension du nom de l&#39;ensemble doit être `-SET`. Si vous téléchargez une image nommée `0123-RED-01`, un ensemble nommé `0123-RED-SET` est alors créé. Si vous téléchargez ultérieurement des images `0123-RED-03` et `0123-BLUE-01`, l’image `RED-03` sera ajoutée à la visionneuse à la deuxième position, car elle est triée en dessous de `01`. Cependant, l&#39;image `BLUE-01` fait partie d&#39;un nouveau jeu nommé `0123-BLUE-SET`. Pour le prochain transfert de fichier, vous ajoutez les fichiers `0123-RED-02` et `0123-BLUE-02`. Chaque actif serait ajouté à son jeu respectif. L&#39;image `RED-02` est automatiquement triée entre les images `01` et `03` existantes, en raison de l&#39;ordre de tri.

La page **[!UICONTROL Paramètre prédéfini d’ensemble par lot]** de [!DNL Dynamic Media] permet de créer, modifier ou supprimer des paramètres prédéfinis d’ensemble par lot, et d’appliquer ou de supprimer des paramètres prédéfinis d’ensemble par lot à des dossiers de fichiers ou à des dossiers de fichiers. Vous pouvez utiliser les listes déroulantes de champ de formulaire pour définir un paramètre prédéfini d’ensemble par lot ou utiliser le champ **[!UICONTROL Code brut]**, qui vous permet de saisir la syntaxe d’expression standard.

Vous pouvez créer autant de paramètres prédéfinis d’ensemble par lot que nécessaire pour couvrir toutes les tâches d’assimilation de fichiers dont vous avez besoin.

**A propos de la convention de dénomination des ressources**

La zone **[!UICONTROL Convention d’affectation de nom]** de la page **[!UICONTROL Paramètre prédéfini d’ensemble par lot]** contient deux éléments que vous pouvez utiliser pour définir votre paramètre prédéfini d’ensemble par lot : **[!UICONTROL Correspondance]** et **[!UICONTROL Nom de base]**. Ces éléments vous permettent de définir une convention d’affectation de nom et d’identifier la partie de la convention utilisée pour nommer l’ensemble dans lequel ils se trouvent. <!-- While **[!UICONTROL Match]** is required, **[!UICONTROL Base Name]** is mandatory only if the **[!UICONTROL Match]** field does not already specify a base name through the use of a bracket grouping. -->

La convention d’affectation de nom individuelle d’une société utilise souvent une ou plusieurs lignes de définition de chacun de ces deux éléments. Vous pouvez utiliser autant de lignes que vous le souhaitez pour votre définition unique et les regrouper dans des éléments distincts, par exemple, pour l’image principale, les éléments Couleur, Affichage secondaire et Échantillon.

Par exemple, la syntaxe d’une expression régulière de correspondance littérale peut se présenter comme suit :

`(\w+)-\w+-\w+`

**A propos de l&#39;ordre des séquences**

Vous pouvez éventuellement définir l’ordre d’affichage des images après le regroupement de la visionneuse d’images ou de la visionneuse à 360° dans [!DNL Dynamic Media]. Par défaut, les ressources sont classées par ordre alphanumérique. Cependant, vous pouvez utiliser une liste d’expressions régulières séparées par des virgules pour définir l’ordre.

En ce qui concerne l’automatisation de l’ordre des séquences, vous spécifiez des règles pour forcer le tri des fichiers d’une certaine manière, si nécessaire. Supposons, par exemple, que votre premier fichier soit toujours nommé `_main` et que vous souhaitiez qu’il soit suivi de `_alt1`, `_alt2`, `_alt3`, etc. Dans ce cas, vous pouvez créer une règle d’ordre de séquence avec la syntaxe suivante :

`.*_main,.*_alt[0-9]`

Bien qu’une séquence de tri forcé soit possible, il est généralement préférable de se baser autant que possible sur la numérotation alphanumérique pour l’ordre des séquences. En outre, vous pouvez utiliser les outils d’éditeur de visionneuse d’images ou de visionneuses à 360° dans [!DNL Dynamic Media] pour réorganiser facilement l’ordre de séquence des fichiers, ou ajouter et supprimer de nouveaux fichiers dans la visionneuse en utilisant une opération de glisser-déposer.

Lorsque vous avez terminé de créer un paramètre prédéfini d’ensemble par lot, vous l’appliquez à un ou plusieurs dossiers que vous avez créés. Voir [A propos de l’application des paramètres prédéfinis d’ensemble par lot aux dossiers](#apply-bsp).

<!-- See also [Creating a batch set preset for the auto generation of a 2D Spin Set](application-setup.md#creating_a_batch_set_preset_for_the_auto_generation_of_a_2d_spin_set). -->

**Pour créer un paramètre prédéfini d’ensemble par lot pour une visionneuse d’images ou une visionneuse à 360° :**

1. Appuyez sur le logo Adobe Experience Manager et accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Paramètres prédéfinis d’ensemble par lot]**.

   ![bsp-create1.png](/help/assets/assets-dm/bsp-create1.png)

1. Sur la page **[!UICONTROL Paramètres prédéfinis d’ensemble par lot]**, près du coin supérieur droit, appuyez sur **[!UICONTROL Créer]**.
1. Dans la boîte de dialogue **[!UICONTROL Créer un paramètre prédéfini d’ensemble par lot]**, dans le champ **[!UICONTROL Nom du paramètre prédéfini]**, saisissez un nom descriptif. Notez que le nom du paramètre prédéfini n’est pas modifiable si vous décidez de le modifier ultérieurement.

1. Dans la liste déroulante **[!UICONTROL Type de paramètre prédéfini]**, sélectionnez **[!UICONTROL ImageSet]** ou **[!UICONTROL SpinSet]**. Veillez à choisir le type de paramètre prédéfini approprié ; il n&#39;est pas modifiable plus tard.
1. Appuyez sur **[!UICONTROL Créer]**. 
1. Sur le côté droit de la page **[!UICONTROL Modifier le paramètre prédéfini d’ensemble par lot]**, définissez les options modifiables de votre choix sous les en-têtes **[!UICONTROL Détails du paramètre prédéfini]** et **[!UICONTROL Définir la convention d’affectation de nom]**.
Voir [Détails des paramètres prédéfinis, Définir la convention de dénomination et Résultats de la règle - Options RegX](#features-options-bsp) pour en savoir plus sur les options modifiables disponibles.

   ![bsp-create4.png](/help/assets/assets-dm/bsp-create4.png)

1. Créez un ou plusieurs groupes d’expressions réguliers.

   * Sur le côté gauche de la page **[!UICONTROL Modifier le paramètre prédéfini d’ensemble par lot]**, sous **[!UICONTROL Correspondance]**, **[!UICONTROL Nom de base]** ou **[!UICONTROL Ordre des séquences]**, appuyez sur **[!UICONTROL Ajouter le groupe]**.
   * Le champ **[!UICONTROL Correspondance]** est obligatoire. **[!UICONTROL Le]** nom de base n&#39;est obligatoire que si le  **** champ de correspondance ne spécifie pas déjà un nom de base par le biais d&#39;un regroupement de crochets. **[!UICONTROL La]** commande de séquence est facultative.
   * A l’aide des listes déroulantes et des zones de texte du formulaire du groupe, spécifiez un groupe d’expressions que vous souhaitez utiliser pour définir les critères d’attribution de noms pour les membres de la visionneuse d’images ou de la visionneuse à 360°.
      * Lorsque vous sélectionnez et spécifiez des expressions pour un groupe, vous remarquerez que la syntaxe d&#39;expression standard se reflète dans la partie inférieure droite de la page, sous l&#39;en-tête **[!UICONTROL Résultats de la règle - RegX]** (vous devrez peut-être appuyer n&#39;importe où en dehors de la zone de formulaire pour voir la chaîne d&#39;expression régulière mise à jour dans la partie inférieure droite). Ces chaînes d’expression standard représentent le modèle que vous souhaitez faire correspondre dans une recherche de ressources [!DNL Dynamic Media] pour créer votre visionneuse d’images ou votre visionneuse à 360°.
      * Pour supprimer un groupe que vous avez ajouté, appuyez sur **[!UICONTROL X]**.
   * Lorsque vous ajoutez deux groupes ou plus, dans la liste déroulante **[!UICONTROL Et]**, sélectionnez **[!UICONTROL Et]** pour joindre un groupe récemment ajouté à tout groupe d’expressions précédent que vous avez ajouté. Ou, sélectionnez **[!UICONTROL Ou]** pour ajouter une alternative entre le groupe d’expressions précédent et le nouveau groupe que vous créez. L&#39;opérande **[!UICONTROL Or]** est défini par l&#39;utilisation d&#39;un caractère de ligne verticale `|` dans la syntaxe d&#39;expression classique elle-même.

1. Utilisez l’une des méthodes suivantes :

   * Pour ajouter un autre nouveau groupe, sous **[!UICONTROL Correspondance]**, **[!UICONTROL Nom de base]** ou **[!UICONTROL Ordre de séquencement]**, appuyez sur **[!UICONTROL Ajouter le groupe]**. Créez un autre groupe d’expressions régulier comme vous l’avez fait à l’étape précédente.
   * Examinez la syntaxe d&#39;expression standard dans la zone **[!UICONTROL Résultats de la règle - RegX]**. Si vous devez modifier la syntaxe, apportez vos modifications dans le groupe correspondant situé à gauche de la page.
   * Si vous avez terminé de créer des groupes d’expressions, passez à l’étape suivante.

1. Dans le coin supérieur droit de la page, appuyez sur **[!UICONTROL Enregistrer]**.

Vous êtes maintenant prêt à appliquer le paramètre prédéfini d’ensemble par lot à un ou plusieurs dossiers de fichiers, à télécharger des fichiers dans le dossier, puis à créer votre visionneuse d’images ou votre visionneuse à 360°. Voir [A propos de l’application des paramètres prédéfinis d’ensemble par lot aux dossiers](#apply-bsp).

### Détails des paramètres prédéfinis, Convention de dénomination des paramètres et résultats des règles - Options RegX {#features-options-bsp}

Ces options sont disponibles sur la page **[!UICONTROL Modifier le paramètre prédéfini d’ensemble par lot]** lorsque vous créez ou modifiez un paramètre prédéfini d’ensemble par lot.

Voir [Création d’un paramètre prédéfini d’ensemble par lot pour une visionneuse d’images ou une visionneuse à 360°](#creating-bsp) ou [Modification d’un paramètre prédéfini d’ensemble par lot](#edit-bsp).

| **[!UICONTROL Détails du paramètre prédéfini]** | Description |
| --- | --- |
| Nom du paramètre prédéfini | Lecture seule. Nom que vous avez spécifié lors de la première création du jeu de lots. Si vous devez renommer le paramètre prédéfini, vous pouvez copier le paramètre prédéfini d’ensemble par lot existant et spécifier un nouveau nom. Voir [Copie d’un paramètre prédéfini d’ensemble par lot existant](#copy-bsp). |
| Type | Lecture seule. Le type a été spécifié lors de la première création du jeu de lots. La copie d’un paramètre prédéfini d’ensemble par lot existant ne vous permet pas de modifier son [!UICONTROL type]; vous devez créer un nouveau paramètre prédéfini. |
| Inclure les ressources dérivées | Facultatif. Sélectionnez **[!UICONTROL Oui]** (par défaut) pour que [!DNL Dynamic Media]’s IPS (Image Production System) intègre des images générées ou &quot;dérivées&quot; à votre visionneuse à 360° ou visionneuse d’images. Un fichier dérivé est une image qui n’a pas été directement téléchargée par un utilisateur. Au lieu de cela, la ressource a été produite par IPS lorsqu’une ressource principale a été téléchargée. Par exemple, un fichier d’image généré par IPS à partir d’une page d’un fichier PDF, au moment où le fichier PDF a été téléchargé dans [!DNL Dynamic Media], est considéré comme un fichier dérivé. |
| Dossier de destination | Facultatif.  Si vous définissez un grand nombre de visionneuses d’images ou de visionneuses à 360°, vous préférerez peut-être séparer ces visionneuses des dossiers contenant les fichiers eux-mêmes. Par conséquent, vous pouvez envisager de créer un dossier Visionneuses d’images ou Visionneuses à 360° et de rediriger l’application pour y placer les visionneuses générées par lot.<br>Dans ce cas, spécifiez le dossier dans la structure de dossiers Adobe Experience Manager Assets (`/content/dam`) pour lequel le paramètre prédéfini d’ensemble par lot doit être principal. Assurez-vous que le dossier est activé pour la synchronisation [!DNL Dynamic Media] afin de l&#39;autoriser en tant que dossier de destination. Voir [Configuration de la publication sélective au niveau des dossiers dans Dynamic Media](/help/assets/dynamic-media/selective-publishing.md#selective-publish-configure-folder).<br>Sachez que plusieurs dossiers peuvent être dotés d’un paramètre prédéfini d’ensemble par lot donné si vous appliquez ce paramètre prédéfini au moyen des  **[!UICONTROL Propriétés]** du dossier. Voir [Application de paramètres prédéfinis d’ensemble par lot à partir de la page Propriétés d’un dossier de ressources](#apply-bsp-to-folders-via-properties).<br>Si vous ne spécifiez pas de dossier, le paramètre prédéfini d’ensemble par lot est créé dans le même dossier que le dossier de téléchargement des fichiers. |
| **[!UICONTROL Définir la convention d’affectation des noms]** |  |
| Préfixe<br>ou<br>Suffixe | Facultatif. Entrez un préfixe, un suffixe ou les deux dans les champs respectifs.<br>Les champs de préfixe et de suffixe vous permettent de créer autant de paramètres prédéfinis d’ensemble par lot à l’aide d’une autre convention d’affectation de nom de fichier personnalisée qui peut s’avérer nécessaire pour un ensemble de contenu particulier. Cette méthode est particulièrement utile dans les cas où il existe une exception à un schéma d’affectation de nom par défaut défini par une société.<br>Le préfixe ou le suffixe est ajouté au  **[!UICONTROL nom de]** base que vous définissez dans la zone  **[!UICONTROL Conventionpour le nommage des]** ressources. En ajoutant un préfixe ou un suffixe, vous vous assurez que votre visionneuse d’images ou visionneuse à 360° est créée de manière exclusive et indépendante des autres fichiers. Il peut également aider d&#39;autres personnes à identifier les types de fichiers. Par exemple, pour déterminer un mode de couleur utilisé, vous pouvez ajouter comme préfixe ou suffixe `rgb` ou `cmyk`.<br>Bien que la spécification d’une convention d’affectation de nom d’ensemble ne soit pas nécessaire pour utiliser la fonctionnalité de paramètres prédéfinis d’ensemble par lot, il est recommandé d’utiliser la convention d’affectation de nom d’ensemble pour définir autant d’éléments de votre convention d’affectation de nom que vous souhaitez regrouper dans une visionneuse afin de simplifier la création d’ensembles par lot. |
| **[!UICONTROL Résultats de la règle - RegX]** |  |
| Convention de dénomination des ressources - Correspondance | Lecture seule. Affiche la syntaxe d’expression régulière en fonction des options de formulaire Correspondance que vous avez sélectionnées ou du code brut que vous avez saisi. |
| Convention de dénomination des ressources - Nom de base | Lecture seule. Affiche la syntaxe d’expression régulière en fonction des options de formulaire Nom de base que vous avez sélectionnées ou du code brut que vous avez saisi. |
| Ordre des séquences - Correspondance | Lecture seule. Affiche la syntaxe d’expression régulière en fonction des options de formulaire que vous avez sélectionnées ou du code brut que vous avez saisi. |

## A propos de l&#39;application de paramètres prédéfinis d&#39;ensemble par lot aux dossiers {#apply-bsp}

Lorsque vous affectez des paramètres prédéfinis d’ensemble par lot à un ou plusieurs dossiers, tous les sous-dossiers héritent automatiquement des paramètres prédéfinis de leur dossier parent.

Vous pouvez appliquer plusieurs paramètres prédéfinis d’ensemble par lot à un dossier.

Les dossiers auxquels un paramètre prédéfini de lot est affecté sont indiqués dans l’interface utilisateur par le nom du paramètre prédéfini affiché dans le dossier, dans la vue **[!UICONTROL Carte]**.

Utilisez l’une des deux méthodes suivantes pour appliquer des paramètres prédéfinis d’ensemble par lot aux dossiers :

* [Appliquez des paramètres prédéfinis d’ensemble par lot aux dossiers de fichiers à partir de la page](#apply-bsp-to-folders-via-bsp-page)  Paramètre prédéfini d’ensemble par lot. Cette méthode vous offre la plus grande flexibilité. Vous pouvez appliquer un ou plusieurs paramètres prédéfinis à un ou plusieurs dossiers.
* [Appliquer des paramètres prédéfinis d’ensemble par lot à partir de la page](#apply-bsp-to-folders-via-properties)  Propriétés d’un dossier de fichiers : cette méthode vous permet d’appliquer un ou plusieurs paramètres prédéfinis d’ensemble par lot à un seul dossier.

Il est recommandé de s’assurer que les dossiers de fichiers sont synchronisés [!DNL Dynamic Media], puis d’appliquer les paramètres prédéfinis de votre choix.

Il peut s’avérer nécessaire de retraiter des fichiers dans un dossier si vous effectuez l’une des deux situations suivantes :

* Vous souhaitez exécuter un paramètre prédéfini d’ensemble par lot sur un dossier de fichiers existant dans lequel des fichiers ont déjà été téléchargés.
* Vous modifiez ensuite un paramètre prédéfini d’ensemble par lot existant qui était précédemment appliqué à un dossier de fichiers.

<!-- See [Reprocessing assets in a folder](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets). -->

### Application de paramètres prédéfinis d’ensemble par lot aux dossiers de fichiers à partir de la page Paramètres prédéfinis d’ensemble par lot {#apply-bsp-to-folders-via-bsp-page}

1. Appuyez sur le logo Adobe Experience Manager et accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Paramètres prédéfinis d’ensemble par lot]**.
1. Sur la page **[!UICONTROL Paramètres prédéfinis d’ensemble par lot]**, à gauche de la colonne **[!UICONTROL Nom du paramètre prédéfini]**, cochez la case de chaque paramètre prédéfini d’ensemble par lot à appliquer aux dossiers.
1. Dans la barre d’outils, appuyez sur **[!UICONTROL Appliquer le paramètre prédéfini de lot aux dossiers]**.
1. Sur la page **[!UICONTROL Sélectionner les dossiers]**, cochez la case de chaque dossier auquel vous voulez appliquer les paramètres prédéfinis d’ensemble par lot.
1. Dans le coin supérieur droit de la page **[!UICONTROL Sélectionner un(des) dossier(s)]**, appuyez sur **[!UICONTROL Appliquer]**.

### Application de paramètres prédéfinis d’ensemble par lot à partir de la page Propriétés d’un dossier de ressources {#apply-bsp-to-folders-via-properties}

1. Appuyez sur le logo Adobe Experience Manager et accédez à **[!UICONTROL Ressources]** > **[!UICONTROL Fichiers]**.
1. Accédez au dossier auquel vous souhaitez appliquer un ou plusieurs paramètres prédéfinis d’ensemble par lot.
1. Sur la page, à gauche de la colonne **[!UICONTROL Nom]**, cochez la case de la colonne.
1. Dans la barre d’outils, appuyez sur **[!UICONTROL Propriétés]**.
1. Dans la page Propriétés du dossier, appuyez sur l’onglet **[!UICONTROL Traitement Dynamic Media]**.

   ![bsp-apply-via-properties2.png](/help/assets/assets-dm/bsp-apply-via-properties2a.png)

1. Sous **[!UICONTROL Paramètre(s) prédéfini(s) d’ensemble par lot]**, sélectionnez le nom d’un paramètre prédéfini d’ensemble par lot à appliquer dans la liste déroulante **[!UICONTROL Nom du paramètre prédéfini]**. La capture d’écran ci-dessus montre que deux paramètres prédéfinis d’ensemble par lot ont été appliqués au dossier.

   S’il n’existe aucun nom de paramètre prédéfini d’ensemble par lot dans la zone de liste déroulante **[!UICONTROL Nom du paramètre prédéfini]**, cela signifie que vous n’avez pas encore créé de paramètre prédéfini d’ensemble par lot. Voir [Création d’un paramètre prédéfini d’ensemble par lot pour une visionneuse d’images ou une visionneuse à 360°](#creating-bsp).

   Pour supprimer un paramètre prédéfini d’ensemble par lot appliqué, appuyez sur **[!UICONTROL X]** à droite du type de paramètre prédéfini.

1. Dans le coin supérieur droit de la page, appuyez sur **[!UICONTROL Enregistrer et fermer]**.

## Modification d’un paramètre prédéfini d’ensemble par lot {#edit-bsp}

Vous pouvez modifier un paramètre prédéfini d’ensemble par lot existant que vous avez créé. Vous pouvez modifier n’importe quel groupe d’expressions que vous avez créé pour la convention d’affectation des noms de fichier ou l’ordre de séquence. Si nécessaire, vous pouvez également mettre à jour le dossier de destination et définir des conventions d’affectation de nom.

Vous ne pouvez toutefois pas modifier le nom ou le type de paramètre prédéfini du paramètre prédéfini (visionneuse d’images ou visionneuse à 360°). S’il devient nécessaire de modifier le nom d’un paramètre prédéfini, il vous suffit de copier le paramètre prédéfini existant et de spécifier un nouveau nom. Voir [Copie d’un paramètre prédéfini d’ensemble par lot](#copy-bsp).

Si vous modifiez un paramètre prédéfini d’ensemble par lot précédemment appliqué à un dossier, le paramètre prédéfini nouvellement modifié est appliqué uniquement aux nouveaux fichiers téléchargés dans le dossier.

Si vous souhaitez que le paramètre prédéfini nouvellement modifié soit réappliqué aux fichiers existants du dossier, vous devez retraiter le dossier. <!-- See [Reprocessing assets in a folder](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets). --> De cette façon, les fichiers existants pourraient désormais faire partie d’une visionneuse d’images ou d’une visionneuse à 360° et être ajoutés. En outre, les fichiers existants qui étaient déjà inclus dans la visionneuse d’images ou la visionneuse à 360°, en fonction du paramètre prédéfini d’ensemble par lot précédent utilisé, ne sont pas supprimés (à condition qu’ils ne soient plus qualifiés en fonction du paramètre prédéfini récemment modifié) et s’affichent en l’état.

**Pour modifier un paramètre prédéfini d’ensemble par lot :**

1. Appuyez sur le logo Adobe Experience Manager et accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Paramètres prédéfinis d’ensemble par lot.]**
1. Sur la page **[!UICONTROL Paramètres prédéfinis d’ensemble par lot]**, à gauche de la colonne **[!UICONTROL Nom du paramètre prédéfini]**, vérifiez le paramètre prédéfini d’ensemble par lot que vous souhaitez modifier.
1. Dans la barre d’outils, appuyez sur **[!UICONTROL Modifier le paramètre prédéfini d’ensemble par lot.]**
1. Modifiez le paramètre prédéfini selon vos besoins.
1. Dans le coin supérieur droit de la page **[!UICONTROL Paramètre prédéfini d’ensemble par lot]**, appuyez sur **[!UICONTROL Enregistrer.]**

## Copie d’un paramètre prédéfini d’ensemble par lot existant {#copy-bsp}

Vous pouvez copier un paramètre prédéfini d’ensemble par lot existant afin d’éviter d’avoir à recréer manuellement un paramètre prédéfini complexe ou simplement de renommer un paramètre prédéfini. Vous ne pouvez toutefois pas modifier le type de paramètre prédéfini utilisé (visionneuse d’images ou visionneuse à 360°).

Si vous copiez un paramètre prédéfini existant référencé par des dossiers de fichiers, ces dossiers ne sont pas concernés.

**Pour copier un paramètre prédéfini d’ensemble par lot existant :**

1. Appuyez sur le logo Adobe Experience Manager et accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Paramètres prédéfinis d’ensemble par lot.]**
1. Sur la page **[!UICONTROL Paramètres prédéfinis d’ensemble par lot]**, à gauche de la colonne **[!UICONTROL Nom du paramètre prédéfini]**, cochez la case du paramètre prédéfini d’ensemble par lot à copier.
1. Dans la barre d’outils, appuyez sur **[!UICONTROL Copier]**.
1. Dans la boîte de dialogue **[!UICONTROL Copier le paramètre prédéfini d’ensemble par lot]**, dans la zone de texte **[!UICONTROL Titre]**, saisissez un nouveau nom pour le paramètre prédéfini.

   ![bsp-copy2.png](/help/assets/assets-dm/bsp-copy2.png)

1. Appuyez sur **[!UICONTROL Copier]**.

## A propos de la suppression des paramètres prédéfinis d’ensemble par lot dans les dossiers {#remove-bsp-from-folder}

Lorsque vous supprimez des dossiers des paramètres prédéfinis d’ensemble par lot, les nouveaux fichiers que vous téléchargez vers ces dossiers ne sont pas associés au paramètre prédéfini d’ensemble par lot. Les fichiers existants du dossier qui ont déjà été ajoutés à la visionneuse d’images ou à la visionneuse d’impressions, en fonction du paramètre prédéfini d’ensemble par lot appliqué au dossier, continueront à s’afficher en l’état.

Si vous souhaitez *supprimer* les paramètres prédéfinis des dossiers à la place, voir [Suppression des paramètres prédéfinis d’ensemble par lot](#delete-bsp).

Vous pouvez utiliser deux méthodes pour supprimer des dossiers des paramètres prédéfinis d’ensemble par lot.

* [Suppression des paramètres prédéfinis d’ensemble par lot des dossiers par le biais de la page](#remove-bsp-from-folders-via-bsp-page)  Paramètres prédéfinis d’ensemble par lot - Cette méthode vous offre la plus grande flexibilité. Vous pouvez supprimer un ou plusieurs paramètres prédéfinis d’un ou de plusieurs dossiers.
* [Suppression des paramètres prédéfinis d’ensemble par lot de la page](#remove-bsp-from-folders-via-properties)  Propriétés d’un dossier - Cette méthode vous permet de supprimer un ou plusieurs paramètres prédéfinis d’ensemble par lot d’un seul dossier.

### Suppression des paramètres prédéfinis d’ensemble par lot des dossiers par le biais de la page Paramètres prédéfinis d’ensemble par lot {#remove-bsp-from-folders-via-bsp-page}

1. Appuyez sur le logo Adobe Experience Manager et accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Paramètres prédéfinis d’ensemble par lot]**.
1. Sur la page **[!UICONTROL Paramètres prédéfinis d’ensemble par lot]**, à gauche de la colonne **[!UICONTROL Nom du paramètre prédéfini]**, cochez la case d’un ou de plusieurs paramètres prédéfinis d’ensemble par lot à supprimer d’un ou de plusieurs dossiers.
1. Dans la barre d’outils, appuyez sur **[!UICONTROL Supprimer le paramètre prédéfini de lot des dossiers]**.

1. Sur la page **[!UICONTROL Sélectionner les dossiers]**, sélectionnez un ou plusieurs dossiers dans lesquels vous souhaitez supprimer les paramètres prédéfinis d’ensemble par lot. La capture d’écran ci-dessus montre un dossier sélectionné avec le nom de deux paramètres prédéfinis d’ensemble par lot qui lui ont déjà été appliqués et qui sera supprimé.
1. Dans le coin supérieur droit de la page **[!UICONTROL Sélectionner un(des) dossier(s)]**, appuyez sur **[!UICONTROL Supprimer]**.

   ![bsp-remove-from-folders3.png](/help/assets/assets-dm/bsp-remove-from-folders3.png)

1. Dans la boîte de dialogue **[!UICONTROL Supprimer le profil]**, appuyez sur **[!UICONTROL Supprimer]**.

### Suppression de paramètres prédéfinis d’ensemble par lot de la page Propriétés d’un dossier {#remove-bsp-from-folders-via-properties}

1. Appuyez sur le logo Adobe Experience Manager et accédez à **[!UICONTROL Ressources]** > **[!UICONTROL Fichiers]**.
1. Accédez au dossier dans lequel vous souhaitez supprimer un ou plusieurs paramètres prédéfinis d’ensemble par lot.
1. Sur la page, à gauche de la colonne **[!UICONTROL Nom]**, cochez la case d’un dossier.
1. Dans la barre d’outils, appuyez sur **[!UICONTROL Propriétés]**.
1. Dans la page Propriétés du dossier, appuyez sur **[!UICONTROL Traitement Dynamic Media]**.

   ![bsp-apply-via-properties2.png](/help/assets/assets-dm/bsp-remove-via-properties2.png)

1. Sous **[!UICONTROL Paramètres prédéfinis d’ensemble par lot]**, appuyez sur **[!UICONTROL X]** à droite du type de paramètre prédéfini.

1. Dans le coin supérieur droit de la page, appuyez sur **[!UICONTROL Enregistrer et fermer]**.

## Suppression des paramètres prédéfinis d’ensemble par lot {#delete-bsp}

Vous pouvez supprimer des paramètres prédéfinis d’ensemble par lot afin de les supprimer définitivement de [!DNL Dynamic Media]. En d’autres termes, ils ne s’afficheront plus sur la page [!UICONTROL Paramètre prédéfini d’ensemble par lot] et ne s’afficheront plus dans la liste déroulante **[!UICONTROL Paramètres prédéfinis d’ensemble par lot]** de l’onglet **[!UICONTROL Traitement Dynamic Media]** de la page **[!UICONTROL Propriétés]** du dossier. Par conséquent, le paramètre prédéfini n’est pas appliqué aux fichiers existants lors d’un retraitement de dossier ou lorsque de nouveaux fichiers sont téléchargés dans le dossier.

Si vous supprimez un paramètre prédéfini précédemment appliqué à un ou plusieurs dossiers, les visionneuses d’images ou les visionneuses à 360° créées à partir de fichiers de ces dossiers continueront de s’afficher en l’état.

Si vous souhaitez simplement *supprimer* les paramètres prédéfinis des dossiers, voir [Suppression des paramètres prédéfinis d’ensemble par lot des dossiers](#remove-bsp-from-folder).

**Pour supprimer des paramètres prédéfinis d’ensemble par lot :**

1. Appuyez sur le logo Adobe Experience Manager et accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Paramètres prédéfinis d’ensemble par lot]**.
1. Sur la page **[!UICONTROL Paramètres prédéfinis d’ensemble par lot]**, à gauche de la colonne **[!UICONTROL Nom du paramètre prédéfini]**, cochez la case d’un ou de plusieurs paramètres prédéfinis d’ensemble par lot à supprimer.
1. Dans la barre d’outils, appuyez sur **[!UICONTROL Supprimer les paramètres prédéfinis d’ensemble par lot]**.

   ![bsp-delete2.png](/help/assets/assets-dm/bsp-delete2.png)

1. Dans la boîte de dialogue **[!UICONTROL Supprimer les paramètres prédéfinis d’ensemble par lot]**, appuyez sur **[!UICONTROL Supprimer]**.

   Si le paramètre prédéfini que vous supprimez a été référencé par un dossier de ressources, vous devrez peut-être appuyer sur **[!UICONTROL Forcer la suppression]** à la place.

   ![bsp-delete3.png](/help/assets/assets-dm/bsp-delete3.png)

>[!MORELIKETHIS]
>
>* [Visionneuses d’images](/help/assets/dynamic-media/image-sets.md)
>* [Visionneuses à 360°](/help/assets/dynamic-media/spin-sets.md)
>* [Configuration de la publication sélective au niveau des dossiers dans Dynamic Media](/help/assets/dynamic-media/selective-publishing.md#selective-publish-configure-folder)  - Voir &quot;Mode de synchronisation&quot; dans la rubrique pour en savoir plus sur la synchronisation d’un dossier unique  [!DNL Dynamic Media].
>* [Création d’une configuration Dynamic Media en Cloud Services](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services)  - Voir &quot;Mode de synchronisation Dynamic Media&quot; dans la rubrique pour en savoir plus sur la synchronisation de tous les dossiers vers  [!DNL Dynamic Media].