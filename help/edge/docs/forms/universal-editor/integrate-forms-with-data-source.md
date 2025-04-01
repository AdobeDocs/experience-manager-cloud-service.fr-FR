---
title: Comment intégrer un modèle de données de formulaire (FDM) pour un formulaire dans l’éditeur universel ?
description: Découvrez comment créer des formulaires basés sur un modèle de données de formulaire (FDM). Générer et modifiez des données d’exemples pour les objets de modèle de données dans FDM.
feature: Edge Delivery Services, Form Data Model
role: Admin, User
hide: true
hidefromtoc: true
exl-id: 9ce51223-57d0-47d8-8868-84b37d4e8e3e
source-git-commit: 381aad580762fe957e1dc1d5824e4d35098f1ca4
workflow-type: ht
source-wordcount: '1036'
ht-degree: 100%

---

# Intégrer des formulaires à un modèle de données de formulaire dans l’éditeur universel

L’intégration de formulaires à un modèle de données de formulaire (FDM) dans l’éditeur universel vous permet d’utiliser diverses sources de données back-end pour créer un modèle de données de formulaire (FDM). Vous pouvez utiliser le modèle de données de formulaire (FDM) comme schéma dans divers workflows de formulaire. Configurez les sources de données et créez un modèle de données de formulaire (FDM) basé sur les objets et services de modèle de données disponibles dans les sources de données.

## Remarque

* Le service de préremplissage des formulaires dans l’éditeur universel n’est actuellement pas pris en charge.

## Conditions préalables

Avant de configurer votre formulaire avec le modèle de données de formulaire dans l’éditeur universel, assurez-vous d’avoir effectué les étapes suivantes :

* [Configurer la source de données](/help/forms/configure-data-sources.md) : configurez la source de données pour connecter votre formulaire aux données back-end.
* [Créer un modèle de données de formulaire (FDM)](/help/forms/create-form-data-models.md) : créez un modèle de données à l’aide des objets et services de données provenant de la source de données configurée.
* [Configurer les objets et services de modèle de données](/help/forms/work-with-form-data-model.md) : mappez les objets et services de modèle de données afin d’assurer un flux de données fluide entre le formulaire et la source de données.

## Création de formulaires avec un modèle de données de formulaire dans l’éditeur universel

Dans l’éditeur universel, vous pouvez créer ce qui suit :
* [Formulaire basé sur un schéma](#schema-based-form) : un formulaire basé sur un schéma utilise une source de données configurée lors de la création du formulaire dans l’onglet **Données**, liant automatiquement les données aux champs du formulaire.
* [Formulaire non basé sur un schéma](#non-schema-based-form) : un formulaire non basé sur un schéma nécessite que vous ajoutiez manuellement une source de données et que vous liiez chaque champ à partir de l’arborescence de contenu.

![Types de formulaire dans l’éditeur universel](/help/edge/docs/forms/universal-editor/assets/form-types.png){width="50%" align="center" height="50%"}

Ces méthodes vous offrent la possibilité de connecter des modèles de données à des formulaires en fonction de vos besoins.

### Formulaire basé sur un schéma

Lorsque vous créez un formulaire basé sur un schéma, il est automatiquement configuré avec une source de données et les champs du formulaire sont déjà liés aux données par le biais de liaisons de données. Pour créer un formulaire basé sur un schéma à l’aide de l’assistant de création de formulaire, procédez comme suit :

1. Connectez-vous à votre instance de création [!DNL Experience Manager Forms].
2. Entrez vos informations d’identification dans la page de connexion d’Experience Manager. Une fois connecté, dans le coin supérieur gauche, sélectionnez **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents.]**.
3. Sélectionnez **[!UICONTROL Créer]** > **[!UICONTROL Formulaires adaptatifs]**. Cette action permet d’ouvrir l’assistant. Dans l’onglet **Source**, sélectionnez un modèle :

   ![Modèle Edge Delivery Services](/help/edge/assets/create-eds-forms.png)

   Lorsque vous sélectionnez un modèle basé sur Edge Delivery Services, le bouton **[!UICONTROL Créer]** est activé. Vous pouvez accéder aux onglets **[!UICONTROL Source de données]** ou **[!UICONTROL Envoi]** pour sélectionner une source de données ou une action d’envoi.

4. Dans l’onglet **Données**, vous pouvez sélectionner l’un des modèles de données suivants :

   * **Modèle de données de formulaire (FDM)** : intégrez des objets et des services de modèle de données provenant de sources de données dans votre formulaire. Choisissez le modèle de données de formulaire (FDM) si votre formulaire nécessite la lecture et l’écriture de données provenant de plusieurs sources.

   * **Schéma JSON** : intégrez votre formulaire à un système back-end en associant un schéma JSON qui définit la structure des données. Cela vous permet d’ajouter du contenu dynamique à l’aide des éléments de schéma.

     Par exemple, sélectionnez le modèle de données de formulaire créé nommé Pet Form Data Model.

     ![Sélectionner un modèle de données de formulaire](/help/edge/docs/forms/universal-editor/assets/select-petstore-form-data-model.png)


     Par défaut, tous les champs du schéma JSON ou du modèle de données de formulaire (FDM) associé sont automatiquement sélectionnés et convertis en composants de formulaire correspondants, ce qui simplifie le processus de création. L’assistant vous permet également de sélectionner les champs à inclure dans le formulaire à l’aide de cases à cocher.

5. Cliquez sur **[!UICONTROL Créer]** et l’assistant **Créer un formulaire** s’affiche.
6. Spécifiez le **Nom** et le **Titre**.
7. Spécifiez l’**URL GitHub**. Par exemple, si votre référentiel GitHub est nommé `edsforms`, il se trouve sous le compte `wkndforms`, l’URL est la suivante :
   `https://github.com/wkndforms/edsforms`
8. Cliquez sur **[!UICONTROL Créer]**.

   ![Créer un formulaire basé sur un schéma](/help/edge/docs/forms/universal-editor/assets/create-schema-based-form.png)

   Dès que vous cliquez sur **[!UICONTROL Créer]**, le formulaire s’ouvre dans l’éditeur universel en vue Création.

   ![créer le formulaire](/help/edge/docs/forms/universal-editor/assets/schema-based-form-in-ue.png)

   Le formulaire est créé à l’aide des éléments de données de la source de données associée, les champs du formulaire ayant une liaison de données préconfigurée.

   ![Liaison de données automatique](/help/edge/docs/forms/universal-editor/assets/schema-based-form-data-binding.png)

   Vous pouvez maintenant ajouter et [configurer l’action d’envoi](/help/edge/docs/forms/universal-editor/submit-action.md) pour votre formulaire.

### Formulaire non basé sur un schéma

Lorsque vous créez un formulaire non basé sur un schéma, aucune source de données n’est configurée. Vous pouvez modifier les propriétés du formulaire ultérieurement pour ajouter une source de données et configurer manuellement les liaisons de données pour vos champs de formulaire. Effectuez les étapes suivantes pour modifier les propriétés du formulaire et ajouter une source de données :

1. Connectez-vous à votre instance de création [!DNL Experience Manager Forms].
1. Entrez vos informations d’identification dans la page de connexion d’Experience Manager. Une fois connecté, dans le coin supérieur gauche, sélectionnez **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents.]**.
1. Sélectionnez le formulaire pour lequel vous souhaitez ajouter une source de données et cliquez sur **[!UICONTROL Propriétés]**.
   ![Ouverture des propriétés du formulaire](/help/edge/docs/forms/universal-editor/assets/non-schema-based-edit-properties.png)

   Les propriétés du formulaire s’ouvrent.
1. Cliquez pour ouvrir l’onglet **Modèle de formulaire**, puis, dans le menu déroulant **Choisir parmi**, vous pouvez spécifier l’une des options suivantes :

   * **Modèle de données de formulaire (FDM)** : créez le formulaire à l’aide d’un modèle de données de formulaire.
   * **Connecteur** : créez le formulaire à l’aide de la source de données Adobe Marketo.
   * **Schéma** : créez le formulaire à l’aide d’un schéma JSON chargé dans AEM Forms.
   * **Aucun** : créez le formulaire à partir de zéro sans utiliser de modèle de formulaire.

     Par exemple, sélectionnez le modèle de données de formulaire (FDM).

     ![Sélection de l’onglet Modèle de formulaire](/help/edge/docs/forms/universal-editor/assets/select-form-model.png)

1. Sélectionnez le modèle de données de formulaire (FDM) créé dans la liste déroulante. Par exemple, sélectionnez le modèle de données de formulaire créé nommé « Pet Form Data Model » dans la liste déroulante.

   ![Sélection de FDM](/help/edge/docs/forms/universal-editor/assets/select-fdm.png)

   Lorsque vous sélectionnez le modèle de données de formulaire (FDM), la boîte de dialogue d’avertissement s’affiche. Cliquez sur **OK** pour fermer la boîte de dialogue.

   ![Assistant de modèle de formulaire](/help/edge/docs/forms/universal-editor/assets/form-model-wizard.png)

1. Cliquez sur **[!UICONTROL Enregistrer et fermer]**.
1. Ouvrez le formulaire pour le modifier. Le formulaire s’ouvre dans l’éditeur universel pour la création.

   ![Création de formulaire non basé sur un schéma](/help/edge/docs/forms/universal-editor/assets/non-schema-form-authoring.png)

   Les éléments de formulaire présents dans le modèle de données de formulaire (FDM) associé sont affichés dans l’onglet **[!UICONTROL Source de données]** de l’**[!UICONTROL explorateur de contenu]** dans le **panneau Propriétés**.

   ![Source de données de formulaire](/help/edge/docs/forms/universal-editor/assets/non-schema-data-source.png)

1. Sélectionnez les éléments de données dans l’onglet **[!UICONTROL Source de données]** et cliquez sur **[!UICONTROL Ajouter]**.

   ![Ajout d’éléments de données](/help/edge/docs/forms/universal-editor/assets/non-schema-add-data-element.png)

   Vous pouvez également faire glisser ces éléments pour créer votre formulaire adaptatif. Lorsque vous cliquez sur **[!UICONTROL Ajouter]**, les éléments sélectionnés de l’onglet **[!UICONTROL Source de données]** sont ajoutés à votre formulaire et une coche apparaît devant les éléments ajoutés.

   ![Créer le formulaire](/help/edge/docs/forms/universal-editor/assets/non-schema-form.png)

   Vous devez ajouter manuellement une liaison de données à un élément de formulaire en la spécifiant dans les propriétés **Référence de liaison** de l’élément de formulaire.
Par exemple, ajoutons une référence de liaison de données à la zone de texte **Pet Name** déjà présente dans le formulaire :

   ![Ajout manuel de la liaison de données pour un champ de formulaire](/help/edge/docs/forms/universal-editor/assets/non-schema-add-data-binding.png)

   Vous pouvez maintenant ajouter et [configurer l’action d’envoi](/help/edge/docs/forms/universal-editor/submit-action.md) pour votre formulaire.

## Voir également

{{universal-editor-see-also}}
