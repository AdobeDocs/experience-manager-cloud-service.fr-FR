---
title: Comment intégrer un modèle de données de formulaire (FDM) pour un formulaire dans l’éditeur universel ?
description: Découvrez comment créer des formulaires basés sur un modèle de données de formulaire (FDM). Générer et modifiez des données d’exemples pour les objets de modèle de données dans FDM.
feature: Edge Delivery Services, Form Data Model
role: Admin, User
exl-id: 9ce51223-57d0-47d8-8868-84b37d4e8e3e
source-git-commit: e1ead9342fadbdf82815f082d7194c9cdf6d799d
workflow-type: tm+mt
source-wordcount: '1271'
ht-degree: 94%

---

# Intégrer des formulaires à un modèle de données de formulaire dans l’éditeur universel

L’intégration de formulaires à un modèle de données de formulaire (FDM) dans l’éditeur universel vous permet d’utiliser diverses sources de données back-end pour créer un modèle de données de formulaire (FDM). Vous pouvez utiliser le modèle de données de formulaire (FDM) comme schéma dans divers workflows de formulaire. Configurez les sources de données et créez un modèle de données de formulaire (FDM) basé sur les objets et services de modèle de données disponibles dans les sources de données.

## Considérations

* Si l’icône **Sources de données** ne s’affiche pas dans l’interface de l’éditeur universel ou si la propriété **Référence de liaison** n’apparaît pas dans le panneau de propriété de droite, activez l’extension **Source de données** dans **Extension Manager**.

  ![Capture d’écran de l’interface Extension Manager de l’éditeur universel présentant les extensions disponibles, y compris l’extension Sources de données, qui peuvent être activées pour l’intégration de formulaires](/help/edge/docs/forms/universal-editor/assets/extension-manager.png)

  Consultez l’article [Caractéristiques des fonctionnalités d’Extension Manager](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions) pour savoir comment activer et désactiver les extensions dans l’éditeur universel.

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
1. Entrez vos informations d’identification dans la page de connexion d’Experience Manager. Une fois connecté, dans le coin supérieur gauche, sélectionnez **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents.]**.
1. Sélectionnez **[!UICONTROL Créer]** > **[!UICONTROL Formulaires adaptatifs]**. Cette action permet d’ouvrir l’assistant. Dans l’onglet **Source**, sélectionnez un modèle :

   ![Modèle Edge Delivery Services](/help/edge/assets/create-eds-forms.png)

   Lorsque vous sélectionnez un modèle basé sur Edge Delivery Services, le bouton **[!UICONTROL Créer]** est activé. Vous pouvez accéder aux onglets **[!UICONTROL Source de données]** ou **[!UICONTROL Envoi]** pour sélectionner une source de données ou une action d’envoi.

1. Dans l’onglet **Données**, vous pouvez sélectionner l’un des modèles de données suivants :

   * **Modèle de données de formulaire (FDM)** : intégrez des objets et des services de modèle de données provenant de sources de données dans votre formulaire. Choisissez le modèle de données de formulaire (FDM) si votre formulaire nécessite la lecture et l’écriture de données provenant de plusieurs sources.

   * **Schéma JSON** : intégrez votre formulaire à un système back-end en associant un schéma JSON qui définit la structure des données. Cela vous permet d’ajouter du contenu dynamique à l’aide des éléments de schéma.

     Par exemple, sélectionnez le modèle de données de formulaire créé nommé Pet Form Data Model.

     ![Sélectionner un modèle de données de formulaire](/help/edge/docs/forms/universal-editor/assets/select-petstore-form-data-model.png)


     Par défaut, tous les champs du schéma JSON ou du modèle de données de formulaire (FDM) associé sont automatiquement sélectionnés et convertis en composants de formulaire correspondants, ce qui simplifie le processus de création. L’assistant vous permet également de sélectionner les champs à inclure dans le formulaire à l’aide de cases à cocher.

1. Cliquez sur **[!UICONTROL Créer]** et l’assistant **Créer un formulaire** s’affiche.
1. Spécifiez le **Nom** et le **Titre**.
1. Spécifiez l’**URL GitHub**. Par exemple, si votre référentiel GitHub est nommé `edsforms`, il se trouve sous le compte `wkndforms`, l’URL est la suivante :
   `https://github.com/wkndforms/edsforms`
1. Cliquez sur **[!UICONTROL Créer]**.

   ![Créer un formulaire basé sur un schéma](/help/edge/docs/forms/universal-editor/assets/create-schema-based-form.png)

   Dès que vous cliquez sur **[!UICONTROL Créer]**, le formulaire s’ouvre dans l’éditeur universel en vue Création.

   ![Copie d’écran de l’éditeur universel présentant un formulaire basé sur un schéma avec des champs de formulaire préremplis et l’explorateur de contenu affichant les éléments de source de données disponibles](/help/edge/docs/forms/universal-editor/assets/schema-based-form-in-ue.png)

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

   ![Capture d’écran montrant l’éditeur universel avec un formulaire non schématique en cours de création en faisant glisser des éléments de données de l’onglet Source de données vers la structure du formulaire](/help/edge/docs/forms/universal-editor/assets/non-schema-form.png)

Vous pouvez ajouter une liaison de données à un champ de formulaire en la sélectionnant dans la propriété **Référence de liaison**. Par exemple, ajoutons une référence de liaison de données à la zone de texte **Id** déjà présente dans le formulaire.
Pour sélectionner la liaison de données pour le champ de formulaire dans l’arborescence de la source de données, procédez comme suit :

1. Ouvrez les propriétés du champ de formulaire pour lequel vous souhaitez ajouter la référence de liaison de données.
1. Accédez à la propriété **Référence de liaison** et cliquez sur l’icône **Parcourir**.

   ![Ajout manuel de la liaison de données pour un champ de formulaire](/help/edge/docs/forms/universal-editor/assets/non-schema-add-data-binding.png)

1. Choisissez la référence de liaison de données dans l’arborescence de la source de données de l’assistant **Sélectionner une référence de liaison**.

   ![Sélection de la référence de liaison de données](/help/edge/docs/forms/universal-editor/assets/select-bind-reference.png)

1. Dans l’arborescence de la source de données, sélectionnez l’élément de données que vous souhaitez lier au champ de formulaire, puis cliquez sur **Sélectionner**.

   ![Sélection de l’élément de données](/help/edge/docs/forms/universal-editor/assets/select-data-element.png)

   Le champ de formulaire est lié à l’élément de données et il apparaît dans la propriété **Référence de liaison**.

   ![Liaison de données automatique](/help/edge/docs/forms/universal-editor/assets/schema-based-form-data-binding.png)

   Vous pouvez également modifier manuellement la propriété **Référence de liaison** pour le champ de formulaire.

Vous pouvez maintenant ajouter et [configurer l’action d’envoi](/help/edge/docs/forms/universal-editor/submit-action.md) pour votre formulaire.

## Voir également

{{universal-editor-see-also}}
