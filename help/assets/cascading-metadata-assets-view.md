---
title: Métadonnées en cascade
description: Cet article décrit comment définir des métadonnées en cascade pour des ressources en mode Ressources.
feature: Metadata
role: Admin, User
source-git-commit: 2bb309afc372fe18ce274a2813ed25cba22eb4de
workflow-type: tm+mt
source-wordcount: '1214'
ht-degree: 29%

---


# Vue Assets des métadonnées en cascade{#cascading-metadata-assets-view}

Lors de la capture des informations de métadonnées d’une ressource, les utilisateurs et utilisatrices fournissent des informations dans les différents champs disponibles. Vous pouvez afficher des champs de métadonnées ou des valeurs de champ spécifiques en fonction des options sélectionnées dans les autres champs. Ce type d’affichage conditionnel des métadonnées est appelé « métadonnées en cascade ». En d’autres termes, vous pouvez créer une dépendance entre un champ/une valeur de métadonnées spécifique et un ou plusieurs champs et/ou leurs valeurs.

Utilisez le Forms de métadonnées pour définir des règles d’affichage des métadonnées en cascade. Par exemple, si votre formulaire de métadonnées comprend un champ de type de ressource, vous pouvez définir un ensemble de champs pertinent à afficher en fonction du type de ressource sélectionné par l’utilisateur ou l’utilisatrice.

Voici quelques cas d’utilisation pour lesquels vous pouvez définir des métadonnées en cascade :

* Lorsque l’emplacement de l’utilisateur ou de l’utilisatrice est requis, afficher les noms de ville pertinents en fonction du pays de l’utilisateur ou l’utilisatrice.
* Charger les noms de marque pertinents dans une liste en fonction du choix de catégorie de produits de l’utilisateur ou l’utilisatrice.
* Activer/désactiver la visibilité d’un champ spécifique en fonction de la valeur spécifiée dans un autre champ. Par exemple, afficher des champs d’adresse d’expédition distincts si l’utilisateur ou l’utilisatrice demande un envoi à une autre adresse.
* Désigner un champ comme obligatoire en fonction de la valeur spécifiée dans un autre champ.
* Modifier les options affichées pour un champ particulier en fonction de la valeur spécifiée dans un autre champ.
* Définir la valeur de métadonnées par défaut dans un champ particulier en fonction de la valeur spécifiée dans un autre champ.

>[!IMPORTANT]
>
>La fonction Métadonnées en cascade est disponible en tant que fonctions à disponibilité limitée. Vous pouvez [créer et envoyer un dossier d’assistance client Adobe](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html) pour l’activer pour votre déploiement.

## Configuration des métadonnées en cascade dans [!DNL Experience Manager] {#configure-cascading-metadata-in-aem}

Supposons que vous souhaitiez afficher des métadonnées en cascade en fonction du type de ressource sélectionné. Par exemple-

* Pour une vidéo, affichez les champs applicables tels que le format, le codec, la durée, etc.
* Pour un document Word ou PDF, affichez des champs tels que le nombre de pages, l’auteur, etc.

Nous utilisons un champ déroulant nommé `Image` à titre d’exemple pour classer les fichiers en fonction de leur type d’image. La liste déroulante contient des options représentant les extensions d’image prises en charge (JPG/JPEG, GIF, etc.). Pour garantir la cohérence des données et empêcher la sélection ou le traitement de formats non pris en charge, une règle de validation est appliquée à ce champ. La règle évalue la valeur de liste déroulante sélectionnée et applique des contraintes qui s’alignent sur les formats d’image acceptés.

>[!IMPORTANT]
>
>Vous pouvez créer des règles basées sur des champs de liste déroulante uniquement.

Quel que soit le type de ressource choisi, affichez les informations de copyright sous la forme d’un champ obligatoire. Vous pouvez utiliser les [composants de métadonnées prédéfinis](metadata-assets-view.md#property-components) et [affecter des métadonnées à un dossier](metadata-assets-view.md#assign-metadata-form-folder).

### Création d’un Forms de métadonnées {#build-metadata-schema-forms}

Suivez les étapes ci-dessous pour créer un formulaire de métadonnées :

1. Sélectionnez le logo du [!DNL Experience Manager] et accédez à **[!UICONTROL Paramètres]** > **[!UICONTROL Forms de métadonnées]** > **[!UICONTROL Créer]**.

1. Dans la liste déroulante **[!UICONTROL Type]**, sélectionnez le type de formulaire approprié : **[!UICONTROL Fichier]**, **[!UICONTROL Dossier]** ou **[!UICONTROL Collection]**.

1. Indiquez le titre du formulaire de métadonnées dans le champ **[!UICONTROL Nom]**.

1. Vous pouvez également choisir un modèle de formulaire de métadonnées existant dans la liste déroulante **[!UICONTROL Choisir parmi un modèle de formulaire existant]**.

1. Un formulaire de métadonnées vierge s’affiche. Ajoutez un nouvel onglet.

   ![Interface utilisateur des formulaires de métadonnées](assets/metadata-form-ui.png)

   * **A:** Basculer entre [!UICONTROL Modifier] ou [!UICONTROL Prévisualiser]
   * **B:** [Composants du formulaire de métadonnées](metadata-assets-view.md#property-components)
   * **C:** Passer à un autre formulaire de métadonnées
   * **D:** Ajouter un nouvel onglet
   * **E:** Canvas
   * **F :** Paramètres généraux du composant sélectionné
   * Onglet Règles **G:**
   * Propriétés du composant **H:**

Regardez cette vidéo pour afficher la séquence d’étapes, [Configurer le Forms de métadonnées](https://video.tv.adobe.com/v/341275).

### Modifier un formulaire de métadonnées existant {#modify-existing-metadata-form}

Pour modifier un formulaire de métadonnées existant, procédez comme suit :

1. Ouvrez un formulaire de métadonnées existant et accédez aux [composants prédéfinis](metadata-assets-view.md#property-components) que vous souhaitez ajouter au formulaire et déposez les éléments sur la zone de travail.

   Conformément au cas d’utilisation **Image**, ajoutez un champ déroulant pour définir les types de ressources d’image. Indiquez le nom et le chemin de la propriété dans **Paramètres**, puis configurez éventuellement le champ comme **[!UICONTROL Lecture seule]** ou **[!UICONTROL Sélections multiples]**.

1. Fournissez les options clé-valeur pour la liste déroulante en les saisissant manuellement, en spécifiant un chemin JSON ou en important un fichier CSV.

   * Pour spécifier les valeurs manuellement, sélectionnez **[!UICONTROL Ajouter manuellement]** sous **[!UICONTROL Choix]**, cliquez sur `Add` et spécifiez le libellé et la valeur de l’option. Par exemple, spécifiez les types de ressources Vidéo, PDF et Image.

     ![Type de ressource image](assets/image-asset-type.png)

   * Pour récupérer des valeurs à partir d’un chemin JSON, sélectionnez **[!UICONTROL Ajouter via le chemin JSON]** et spécifiez le chemin d’accès au fichier JSON.

     >[!NOTE]
     >
     >Veillez à stocker le fichier JSON dans un emplacement partagé accessible à tous les éditeurs et auteurs de gestion des ressources numériques.

     ![Ajouter des choix via le chemin JSON](assets/add-json-choices.png)

   * Pour récupérer dynamiquement les valeurs d’un fichier CSV, cliquez sur **[!UICONTROL Importer CSV]** et indiquez le chemin d’accès au fichier CSV. [!DNL Experience Manager] récupère les paires clé/valeur en temps réel lorsque le formulaire est présenté à l’utilisateur.

     ![Ajouter des choix via CSV](assets/import-csv-choices.png)

   >[!NOTE]
   > 
   >Vous ne pouvez pas importer les options d’un fichier CSV et les modifier manuellement, car les deux options s’excluent mutuellement.

1. Pour créer une dépendance entre le champ Image et d’autres champs, sélectionnez le champ dépendant et ouvrez l’onglet **[!UICONTROL Règles]**. Chaque composant prend en charge un ensemble spécifique de règles. Pour ce cas d’utilisation, les options Type de ressource d’image sont utilisées pour définir la logique de la règle.

   <!--![Image Asset Type Rule](assets/image-asset-type-rule.png)-->

   <!--![rule tab](assets/rule-tab.png)-->

1. Sous **[!UICONTROL Obligatoire]**, sélectionnez l’option **[!UICONTROL Obligatoire basé sur la nouvelle règle]**. Cliquez sur ![icône plus](assets/do-not-localize/aem_assets_add_icon.png) pour ajouter une nouvelle règle.

   ![règle](assets/image-required-rule1.png)

   Dans le cas d’utilisation actuel, le champ Type de ressource est obligatoire lorsque le format de ressource d’image est JPG/JPEG, PNG, GIF, TIFF ou WEBP. De plus, cliquez sur ![icône de modification](assets/do-not-localize/edit.svg) pour redéfinir la règle ou sur ![icône de suppression](assets/do-not-localize/delete.svg) pour supprimer la règle définie.

   ![règle](assets/image-required-rule2.png)

1. Sous **[!UICONTROL Visibilité]**, sélectionnez l’option **[!UICONTROL Visible, en fonction d’une nouvelle règle]**. Cliquez sur ![icône plus](assets/do-not-localize/aem_assets_add_icon.png) pour ajouter une nouvelle règle.

   >[!NOTE]
   >
   >Vous pouvez appliquer la condition **[!UICONTROL Exigence]** et la condition **[!UICONTROL Visibilité]** indépendamment les unes des autres.

   ![règle](assets/image-visible-rule1.png)

   Dans le cas d’utilisation actuel, le champ Type de ressource est visible lorsque le format de ressource d’image est JPG/JPEG, PNG ou GIF. De plus, cliquez sur ![icône de modification](assets/do-not-localize/edit.svg) pour redéfinir la règle ou sur ![icône de suppression](assets/do-not-localize/delete.svg) pour supprimer la règle définie.

   ![règle](assets/image-visible-rule2.png)

1. Sélectionnez **[!UICONTROL Choix basés sur une règle]** pour créer une dépendance et définir une règle. Cliquez sur ![icône plus](assets/do-not-localize/aem_assets_add_icon.png) pour ajouter une nouvelle règle.

   ![règle](assets/image-choices-rule1.png)

   Pour configurer les choix basés sur des règles pour la liste déroulante Type de ressource, créez une règle et définissez Image comme champ dépendant. Définissez ensuite les valeurs d’affichage de chaque format d’image en sélectionnant Image pour JPG/JPEG, PNG, GIF et TIFF, puis Vidéo pour WEBP. Assurez-vous que seules les valeurs prévues sont cochées pour chaque format afin d’afficher de manière dynamique les options pertinentes. De plus, cliquez sur ![icône de modification](assets/do-not-localize/edit.svg) pour redéfinir la règle ou sur ![icône de suppression](assets/do-not-localize/delete.svg) pour supprimer la règle définie.

   ![règle](assets/image-choices-rule2.png)

1. De même, répétez les étapes pour créer une dépendance entre les autres ressources telles que PDF et Word dans le champ [!UICONTROL Type de ressource] et des champs tels que [!UICONTROL Nombre de pages] et [!UICONTROL Auteur].

1. Cliquez sur **[!UICONTROL Enregistrer]**. Appliquez le formulaire de métadonnées à un dossier.

1. Accédez au dossier auquel vous avez appliqué le formulaire de métadonnées et ouvrez la page des propriétés d’une ressource. Selon votre choix dans le champ Type de ressource, les champs de métadonnées en cascade pertinents s’affichent.

   ![Sortie de formulaire de métadonnées en cascade](assets/cascading-metadata-form-output.png)

>[!NOTE]
> 
>Pour obtenir un accès anticipé aux métadonnées en cascade sur votre compte Assets View, [créez et envoyez un dossier de support client Adobe](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html).

## Étapes suivantes {#next-steps}

* [Regardez une vidéo pour gérer les formulaires de métadonnées dans la vue Assets](https://experienceleague.adobe.com/docs/experience-manager-learn/assets-essentials/configuring/metadata-forms.html?lang=fr)

* Faites des commentaires sur le produit en utilisant l’option [!UICONTROL Commentaires] disponible dans l’interface utilisateur de la vue Assets

* Faites des commentaires sur la documentation en utilisant l’option [!UICONTROL Modifier cette page] ![modifier la page](assets/do-not-localize/edit-page.png) ou [!UICONTROL Enregistrer un problème] ![créer un problème GitHub](assets/do-not-localize/github-issue.png) disponible dans la barre latérale droite.

* Contactez l’[assistance clientèle](https://experienceleague.adobe.com/fr?support-solution=General&lang=fr#support).

