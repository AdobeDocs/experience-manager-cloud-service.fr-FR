---
title: Schéma de métadonnées de dossier
description: Découvrez comment créer des schémas de métadonnées pour des dossiers de ressources dans AEM Assets
contentOwner: AG
translation-type: ht
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Schéma de métadonnées de dossier {#folder-metadata-schema}

Adobe Experience Manager (AEM) Assets vous permet de créer des schémas de métadonnées pour des dossiers de ressources. Ces schémas définissent la disposition et les métadonnées affichées dans les pages de propriétés des dossiers.

## Ajout d’un formulaire de schéma de métadonnées de dossier   {#add-a-folder-metadata-schema-form}

Utilisez l’éditeur Formulaires de schéma de métadonnées de dossier pour créer et modifier des schémas de métadonnées pour les dossiers.

1. Appuyez/cliquez sur le logo AEM, puis accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Schémas de métadonnées de dossier]**.
1. Sur la page Formulaires de schéma de métadonnées de dossier, appuyez/cliquez sur **[!UICONTROL Créer]**.
1. Indiquez un nom pour le formulaire, puis appuyez/cliquez sur **[!UICONTROL Créer]**. Le nouveau formulaire de schéma est répertorié dans la page Formulaires de schéma.

## Modification des formulaires de schéma de métadonnées de dossier   {#edit-folder-metadata-schema-forms}

Vous pouvez modifier un formulaire de schéma de métadonnées nouveau ou existant comprenant les éléments suivants :

* Onglets
* Éléments de formulaire dans des onglets

Vous pouvez associer ou configurer ces éléments de formulaire dans un champ au sein d’un nœud de métadonnées dans le référentiel CRX. Vous pouvez ajouter de nouveaux onglets ou éléments de formulaire au formulaire de schéma de métadonnées.

1. Sur la page Formulaires de schéma, sélectionnez le formulaire que vous avez créé, puis appuyez/cliquez sur l’icône **[!UICONTROL Modifier]** dans la barre d’outils.
1. Sur la page Éditeur de schéma de métadonnées de dossier, appuyez/cliquez sur l’icône **[!UICONTROL +]** pour ajouter un onglet au formulaire. Pour renommer l’onglet, appuyez/cliquez sur le nom par défaut, puis indiquez le nouveau nom sous **[!UICONTROL Paramètres]**.

   ![custom_tab](assets/custom_tab.png)

   Pour ajouter d’autres onglets, appuyez/cliquez sur l’icône **[!UICONTROL +]**. Pour supprimer un onglet, appuyez/cliquez sur **[!UICONTROL X]**.

1. Dans l’onglet actif, ajoutez un ou plusieurs composants de l’onglet **[!UICONTROL Créer le formulaire]**.

   ![adding_components](assets/adding_components.png)

   Si vous créez plusieurs onglets, appuyez/cliquez sur un onglet spécifique pour ajouter des composants.

1. Pour configurer un composant, sélectionnez-le et modifiez ses propriétés dans l’onglet **[!UICONTROL Paramètres]**.

   Si nécessaire, supprimez un composant de l’onglet **[!UICONTROL Paramètres]**.

   ![configure_properties](assets/configure_properties.png)

1. Appuyez/cliquez sur **[!UICONTROL Enregistrer]** dans la barre d’outils pour enregistrer les modifications.

### Composants de création de formulaires   {#components-to-build-forms}

L’onglet **[!UICONTROL Créer le formulaire]** répertorie les éléments de formulaire que vous utilisez dans votre formulaire de schéma de métadonnées de dossier. L’onglet **[!UICONTROL Paramètres]** contient les attributs de chaque élément sélectionné dans l’onglet **[!UICONTROL Créer le formulaire]**. Voici la liste des éléments de formulaire disponibles dans l’onglet **[!UICONTROL Créer le formulaire]** :

<table>
 <tbody>
  <tr>
   <td><p><strong>Nom du composant</strong></p> </td>
   <td><p><strong>Description</strong></p> </td>
  </tr>
  <tr>
   <td><p>En-tête de section</p> </td>
   <td><p> Permet d’ajouter un en-tête de section pour une liste de composants communs.</p> </td>
  </tr>
  <tr>
   <td><p>Une seule ligne de texte</p> </td>
   <td><p> Permet d’ajouter une propriété de texte d’une seule ligne. Elle est stockée sous la forme d’une chaîne.</p> </td>
  </tr>
  <tr>
   <td><p>Texte à plusieurs valeurs</p> </td>
   <td><p> Permet d’ajouter une propriété de texte à plusieurs valeurs. Il est stocké sous forme de tableau de chaînes.</p> </td>
  </tr>
  <tr>
   <td><p>Nombre</p> </td>
   <td><p> Permet d’ajouter un composant de nombre.</p> </td>
  </tr>
  <tr>
   <td><p>Date</p> </td>
   <td><p> Permet d’ajouter un composant de date.</p> </td>
  </tr>
  <tr>
   <td><p>Liste déroulante</p> </td>
   <td><p> Permet d’ajouter une liste déroulante.</p> </td>
  </tr>
  <tr>
   <td><p>Balises standard</p> </td>
   <td><p> Permet d’ajouter une balise. </p> </td>
  </tr>
  <tr>
   <td><p>Champ masqué</p> </td>
   <td><p> Permet d’ajouter un champ masqué. Il est envoyé en tant que paramètre POST lorsque la ressource est enregistrée.</p> </td>
  </tr>
 </tbody>
</table>

### Modification d’éléments de formulaire {#editing-form-items}

Pour modifier les propriétés d’éléments de formulaire, appuyez/cliquez sur le composant et modifiez l’ensemble ou un sous-ensemble des propriétés suivantes dans l’onglet **[!UICONTROL Paramètres]**.

**[!UICONTROL Libellé du champ]** : nom de la propriété de métadonnées qui s’affiche sur la page des propriétés du dossier.

**[!UICONTROL Associer à la propriété]** : cette propriété spécifie le chemin d’accès relatif au nœud de dossier dans le référentiel CRX où il est enregistré. Elle commence par « **./** », ce qui indique que le chemin est situé sous le nœud du dossier.

Les valeurs admises pour cette propriété sont les suivantes :

* `./jcr:content/metadata/dc:title` : stocke la valeur dans le nœud de métadonnées du dossier en tant que propriété `dc:title`.

* `./jcr:created` : affiche la propriété JCR au niveau du nœud du dossier. Si vous configurez ces propriétés dans CRXDE, Adobe recommande de les marquer avec l’état Désactiver la modification, car elles sont protégées. Dans le cas contraire, l’erreur « `Asset(s) failed to modify` » se produit lorsque vous enregistrez les propriétés de la ressource.

Pour vous assurer que le composant est affiché correctement dans le formulaire de schéma de métadonnées, n’insérez pas d’espace dans le chemin de propriété.

**[!UICONTROL Chemin JSON]** : utilisez cette propriété pour indiquer le chemin d’accès au fichier JSON où vous spécifiez des paires clé/valeur pour les options.

**[!UICONTROL Espace réservé]** : utilisez cette propriété pour spécifier du texte dans l’espace réservé concernant la propriété de métadonnées.

**[!UICONTROL Choix]** : utilisez cette propriété pour spécifier des choix dans une liste.

**[!UICONTROL Description]** : utilisez cette propriété pour ajouter une brève description pour le composant de métadonnées.

**[!UICONTROL Classe]** : classe d’objets à laquelle la propriété est associée.

## Suppression de formulaires de schéma de métadonnées de dossier   {#delete-folder-metadata-schema-forms}

Vous pouvez supprimer des formulaires de schéma de métadonnées de dossier sur la page Formulaires de schéma de métadonnées de dossier. Pour supprimer un formulaire, sélectionnez-le, puis appuyez/cliquez sur l’icône Supprimer dans la barre d’outils.

![delete_form](assets/delete_form.png)

## Affectation d’un schéma de métadonnées de dossier {#assign-a-folder-metadata-schema}

Vous pouvez affecter un schéma de métadonnées de dossier à un dossier à partir de la page Formulaires de schéma de métadonnées de dossier ou lors de la création d’un dossier.

Si vous configurez un schéma de métadonnées pour un dossier, le chemin d’accès au formulaire est stocké dans la propriété `folderMetadataSchema` du nœud de dossier sous .*/jcr:content*.

### Affectation d’un schéma à partir de la page Schéma de métadonnées de dossier   {#assign-to-a-schema-from-the-folder-metadata-schema-page}

1. Appuyez/cliquez sur le logo AEM, puis accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Schémas de métadonnées de dossier]**.
1. Sur la page Formulaires de schéma de métadonnées de dossier, sélectionnez le formulaire à appliquer à un dossier.
1. Dans la barre d’outils, appuyez/cliquez sur **[!UICONTROL Appliquer au(x) dossier(s)]**.

1. Sélectionnez le dossier auquel appliquer le schéma, puis appuyez/cliquez sur **[!UICONTROL Appliquer]**. Si un schéma de métadonnées est déjà appliqué au dossier, un message d’avertissement vous informe que vous êtes sur le point de remplacer le schéma existant. Appuyez/cliquez sur **[!UICONTROL Remplacer]**.
1. Ouvrez les propriétés des métadonnées pour le dossier auquel vous avez appliqué le schéma de métadonnées.

   ![folder_properties](assets/folder_properties.png)

   Pour afficher les champs de métadonnées du dossier, appuyez/cliquez sur l’onglet **[!UICONTROL Métadonnées du dossier]**.

   ![folder_metadata_properties](assets/folder_metadata_properties.png)

### Affectation d’un schéma lors de la création d’un dossier {#assign-a-schema-when-creating-a-folder}

Vous pouvez affecter un schéma de métadonnées de dossier lors de la création d’un dossier. S’il existe au moins un schéma de métadonnées de dossier dans le système, une liste supplémentaire s’affiche dans la boîte de dialogue **[!UICONTROL Créer un dossier]**. Vous pouvez sélectionner le schéma de votre choix. Par défaut, aucun schéma n’est sélectionné.

1. Dans l’interface utilisateur d’AEM Assets, appuyez/cliquez sur **[!UICONTROL Créer]** dans la barre d’outils.
1. Attribuez un titre et un nom au dossier.
1. Dans la liste Schéma de métadonnées de dossier, sélectionnez le schéma de votre choix. Ensuite, appuyez/cliquez sur **[!UICONTROL Créer]**.

   ![select_schema](assets/select_schema.png)

1. Ouvrez les propriétés des métadonnées pour le dossier auquel vous avez appliqué le schéma de métadonnées.
1. Pour afficher les champs de métadonnées du dossier, appuyez/cliquez sur l’onglet **[!UICONTROL Métadonnées du dossier]**.

## Utilisation du schéma de métadonnées de dossier {#use-the-folder-metadata-schema}

Ouvrez les propriétés d’un dossier configuré avec un schéma de métadonnées de dossier. Un onglet **[!UICONTROL Métadonnées de dossier]** s’affiche sur la page des propriétés du dossier. Pour afficher le formulaire de schéma de métadonnées de dossier, sélectionnez cet onglet.

Saisissez les valeurs de métadonnées dans les différents champs, puis appuyez/cliquez sur **[!UICONTROL Enregistrer]** pour les stocker. Les valeurs renseignées sont stockées dans le nœud de dossier du référentiel CRX.

![folder_metadata_properties-1](assets/folder_metadata_properties-1.png)

