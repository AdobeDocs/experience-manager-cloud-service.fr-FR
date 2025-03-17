---
title: Comment créer un modèle de données de formulaire (FDM) pour un formulaire dans l’éditeur universel ?
description: Découvrez comment créer des formulaires basés sur un modèle de données de formulaire (FDM). Générer et modifier des exemples de données pour les objets de modèle de données dans FDM.
feature: Edge Delivery Services, Form Data Model
role: Admin, User
hide: true
hidefromtoc: true
source-git-commit: e2259e542df5a12748705af901d073e4486292c4
workflow-type: tm+mt
source-wordcount: '1036'
ht-degree: 8%

---


# Intégrer des formulaires à un modèle de données de formulaire dans l’éditeur universel

L’intégration de formulaires à un modèle de données de formulaire (FDM) dans l’éditeur universel vous permet d’utiliser diverses sources de données principales pour créer un modèle de données de formulaire (FDM). Vous pouvez utiliser le modèle de données de formulaire (FDM) comme schéma dans divers processus de formulaire. Configurez les sources de données et créez un modèle de données de formulaire (FDM) basé sur les objets et services de modèle de données disponibles dans les sources de données.

## Considération

* Le service de préremplissage des formulaires dans l’éditeur universel n’est actuellement pas pris en charge.

## Conditions préalables

Avant de configurer votre formulaire avec le modèle de données de formulaire dans l’éditeur universel, assurez-vous d’avoir effectué les étapes suivantes :

* [Configurer le Source de données](/help/forms/configure-data-sources.md) : configurez la source de données pour connecter votre formulaire aux données principales.
* [Créer un modèle de données de formulaire (FDM)](/help/forms/create-form-data-models.md) : créez un modèle de données à l’aide des objets et services de données de la source de données configurée.
* [Configurer les objets et services de modèle de données](/help/forms/work-with-form-data-model.md) : mappez les objets et services de modèle de données afin d’assurer un flux de données fluide entre le formulaire et la source de données.

## Création d’un Forms avec un modèle de données de formulaire dans l’éditeur universel

Dans l’éditeur universel, vous pouvez créer les éléments suivants :
* [Formulaire basé sur un schéma](#schema-based-form) : un formulaire basé sur un schéma utilise une source de données configurée lors de la création du formulaire dans l’onglet **Données**, liant automatiquement les données aux champs du formulaire.
* [Formulaire non basé sur un schéma](#non-schema-based-form) : un formulaire non basé sur un schéma nécessite que vous ajoutiez manuellement une source de données et que vous liiez chaque champ de l’arborescence de contenu.

![Types de formulaire dans l’éditeur universel](/help/edge/docs/forms/universal-editor/assets/form-types.png){width="50%" align="center" height="50%"}

Ces méthodes vous offrent la possibilité de connecter des modèles de données à des formulaires en fonction de vos besoins.

### Formulaire basé sur un schéma

Lorsque vous créez un formulaire basé sur un schéma, il est automatiquement configuré avec une source de données et les champs du formulaire sont déjà liés aux données par le biais de liaisons de données. Pour créer un formulaire basé sur un schéma à l’aide de l’assistant de création de formulaire, procédez comme suit :

1. Connectez-vous à votre instance d’auteur [!DNL Experience Manager Forms].
2. Entrez vos informations d’identification dans la page de connexion d’Experience Manager. Une fois connecté, dans le coin supérieur gauche, sélectionnez **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents.]**.
3. Sélectionnez **[!UICONTROL Créer]** > **[!UICONTROL Forms adaptatif]**. Cette action permet d’ouvrir l’assistant. Dans l&#39;onglet **Source**, sélectionnez un modèle :

   ![modèle Edge Delivery Services](/help/edge/assets/create-eds-forms.png)

   Lorsque vous sélectionnez un modèle basé sur Edge Delivery Services, le bouton **[!UICONTROL Créer]** est activé. Vous pouvez accéder aux onglets **[!UICONTROL Source de données]** ou **[!UICONTROL Envoi]** pour sélectionner une source de données ou une action d’envoi.

4. Dans l’onglet **Données**, vous pouvez sélectionner l’un des modèles de données suivants :

   * **Modèle de données de formulaire (FDM)** : intégrez des objets et des services de modèle de données provenant de sources de données dans votre formulaire. Choisissez le modèle de données de formulaire (FDM) si votre formulaire nécessite la lecture et l’écriture de données provenant de plusieurs sources.

   * **Schéma JSON** : intégrez votre formulaire à un système principal en associant un schéma JSON qui définit la structure des données. Elle permet d’ajouter du contenu dynamique à l’aide des éléments de schéma.

     Par exemple, sélectionnez le modèle de données de formulaire créé nommé Modèle de données de formulaire prédéfini.

     ![Sélectionner le modèle de données de formulaire](/help/edge/docs/forms/universal-editor/assets/select-petstore-form-data-model.png)


     Par défaut, tous les champs du schéma JSON ou du modèle de données de formulaire (FDM) associé sont automatiquement sélectionnés et convertis en composants de formulaire correspondants, ce qui simplifie le processus de création. L’assistant vous permet également de sélectionner les champs à inclure dans le formulaire à l’aide de cases à cocher.

5. Cliquez sur **[!UICONTROL Créer]**. L’assistant **Créer un formulaire** s’affiche.
6. Spécifiez les **Nom** et **Titre**.
7. Spécifiez l’**URL GitHub**. Par exemple, si votre référentiel GitHub est nommé `edsforms`, il se trouve sous le compte `wkndforms`, l’URL est :
   `https://github.com/wkndforms/edsforms`
8. Cliquez sur **[!UICONTROL Créer]**.

   ![Créer un formulaire basé sur un schéma](/help/edge/docs/forms/universal-editor/assets/create-schema-based-form.png)

   Dès que vous cliquez sur **[!UICONTROL Créer]**, le formulaire s’ouvre dans l’éditeur universel en vue Création.

   ![créer le formulaire](/help/edge/docs/forms/universal-editor/assets/schema-based-form-in-ue.png)

   Le formulaire est créé à l’aide des éléments de données de la source de données associée, les champs du formulaire ayant une liaison de données préconfigurée.

   ![Liaison automatique des données](/help/edge/docs/forms/universal-editor/assets/schema-based-form-data-binding.png)

   Vous pouvez maintenant ajouter et [configurer l’action d’envoi](/help/edge/docs/forms/universal-editor/submit-action.md) pour votre formulaire.

### Formulaire Non Basé Sur Un Schéma

Lorsque vous créez un formulaire non basé sur un schéma, aucune source de données n’est configurée. Vous pouvez modifier les propriétés du formulaire ultérieurement pour ajouter une source de données et configurer manuellement les liaisons de données pour vos champs de formulaire. Pour modifier les propriétés du formulaire et ajouter une source de données, procédez comme suit :

1. Connectez-vous à votre instance d’auteur [!DNL Experience Manager Forms].
1. Entrez vos informations d’identification dans la page de connexion d’Experience Manager. Une fois connecté, dans le coin supérieur gauche, sélectionnez **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents.]**.
1. Sélectionnez le formulaire pour lequel vous souhaitez ajouter une source de données et cliquez sur **[!UICONTROL Propriétés]**.
   ![Ouvrir les propriétés du formulaire](/help/edge/docs/forms/universal-editor/assets/non-schema-based-edit-properties.png)

   Les propriétés du formulaire s’ouvrent.
1. Cliquez pour ouvrir l’onglet **Modèle de formulaire**, puis dans le menu déroulant **Sélectionner à partir de**. Vous pouvez sélectionner l’une des options suivantes :

   * **Modèle de données de formulaire (FDM)** : créez le formulaire à l’aide d’un modèle de données de formulaire.
   * **Connecteur** : créez le formulaire à l’aide de la source de données Adobe Marketo.
   * **Schéma** : créez le formulaire à l’aide d’un schéma JSON téléchargé dans AEM Forms.
   * **Aucun** : créez entièrement le formulaire sans utiliser de modèle de formulaire.

     Par exemple, sélectionnez le modèle de données de formulaire (FDM)

     ![Sélectionnez l’onglet Modèle de formulaire](/help/edge/docs/forms/universal-editor/assets/select-form-model.png)

1. Sélectionnez le modèle de données de formulaire (FDM) créé dans la liste déroulante. Par exemple, sélectionnez le modèle de données de formulaire créé nommé Modèle de données de formulaire prédéfini dans la liste déroulante.

   ![Sélectionner FDM](/help/edge/docs/forms/universal-editor/assets/select-fdm.png)

   Lorsque vous sélectionnez le modèle de données de formulaire (FDM), la boîte de dialogue d’avertissement s’affiche. Cliquez sur **OK** pour fermer la boîte de dialogue.

   ![Assistant Modèle de formulaire](/help/edge/docs/forms/universal-editor/assets/form-model-wizard.png)

1. Cliquez sur **[!UICONTROL Enregistrer et fermer]**.
1. Ouvrez le formulaire pour le modifier. Le formulaire s’ouvre dans l’éditeur universel pour la création.

   ![Création de formulaires non basée sur un schéma](/help/edge/docs/forms/universal-editor/assets/non-schema-form-authoring.png)

   Les éléments de formulaire présents dans le modèle de données de formulaire (FDM) associé sont affichés dans l’onglet **[!UICONTROL Source de données]** de l’**[!UICONTROL Explorateur de contenu]** dans le panneau **Propriétés**.

   ![Source de données de formulaire](/help/edge/docs/forms/universal-editor/assets/non-schema-data-source.png)

1. Sélectionnez les éléments de données dans l’onglet **[!UICONTROL Source de données]** et cliquez sur **[!UICONTROL Ajouter]**.

   ![Ajouter des éléments de données](/help/edge/docs/forms/universal-editor/assets/non-schema-add-data-element.png)

   Vous pouvez également faire glisser ces éléments pour créer votre formulaire adaptatif. Lorsque vous cliquez sur **[!UICONTROL Ajouter]**, les éléments sélectionnés de l’onglet **[!UICONTROL Source de données]** sont ajoutés à votre formulaire et une coche apparaît devant les éléments ajoutés.

   ![Créer un formulaire](/help/edge/docs/forms/universal-editor/assets/non-schema-form.png)

   Vous pouvez également ajouter manuellement une liaison de données à un élément de formulaire en la spécifiant dans les propriétés **Référence de liaison** de l’élément de formulaire.
Par exemple, ajoutons une référence de liaison de données à la zone de texte **Nom de l’animal de compagnie** déjà présente dans le formulaire :

   ![Ajout manuel de la recherche de données pour un champ de formulaire](/help/edge/docs/forms/universal-editor/assets/non-schema-add-data-binding.png)

   Vous pouvez maintenant ajouter et [configurer l’action d’envoi](/help/edge/docs/forms/universal-editor/submit-action.md) pour votre formulaire.

## Voir également

{{universal-editor-see-also}}
