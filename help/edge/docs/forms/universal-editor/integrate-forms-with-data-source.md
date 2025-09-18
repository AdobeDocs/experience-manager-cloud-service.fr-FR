---
title: Intégration d’un modèle de données de formulaire (FDM) pour un formulaire dans l’éditeur universel
description: Découvrez comment créer des formulaires pour Edge Delivery Services basés sur un modèle de données de formulaire (FDM). Générez et modifiez des données d’exemples pour les objets de modèle de données dans FDM.
feature: Edge Delivery Services, Form Data Model
role: Admin, User
exl-id: 9ce51223-57d0-47d8-8868-84b37d4e8e3e
source-git-commit: 7d3ea5bdc6545b9610f595660fcfb2ef70c837de
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 100%

---


# Intégrer des formulaires au modèle de données de formulaire (FDM)

Connectez vos formulaires aux sources de données back-end à l’aide du FDM pour activer les workflows de liaison, de validation et d’envoi de données.

## Prérequis

Effectuez les étapes suivantes avant d’intégrer le FDM à vos formulaires :

1. **[Configurer la source de données](/help/forms/configure-data-sources.md)** : configurez des connexions back-end.
2. **[Créer un modèle de données de formulaire](/help/forms/create-form-data-models.md)** : définir la structure et les services de données
3. **[Configurer des objets de modèle de données](/help/forms/work-with-form-data-model.md)** : mappez les relations des données.

## Considérations

Si l’icône **Sources de données** ne s’affiche pas dans l’interface de l’éditeur universel ou si la propriété **Référence de liaison** n’apparaît pas dans le panneau de propriété de droite, activez l’extension **Source de données** dans **Extension Manager**.

![Capture d’écran de l’interface Extension Manager de l’éditeur universel présentant les extensions disponibles, y compris l’extension Sources de données, qui peuvent être activées pour l’intégration de formulaires](/help/edge/docs/forms/universal-editor/assets/extension-manager.png)

Consultez l’article [Caractéristiques des fonctionnalités d’Extension Manager](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions) pour savoir comment activer et désactiver les extensions dans l’éditeur universel.

## Choisir votre type de formulaire

L’éditeur universel prend en charge deux approches de création de formulaire :

| Aspect | Formulaire basé sur un schéma | Formulaire non basé sur un schéma |
|--------|-------------------|----------------------|
| **Complexité de la configuration** | Simple (liaison automatique) | Manuelle (liaison champ par champ) |
| **Cas d’utilisation** | Nouveaux formulaires avec structure de données définie | Formulaires existants ou exigences flexibles |
| **Source de données** | Requis lors de la création | Peut être ajoutée ultérieurement |
| **Liaison** | Liaison de champ automatique | Liaison manuelle par champ |

![Types de formulaire dans l’éditeur universel](/help/edge/docs/forms/universal-editor/assets/form-types.png){width="50%" align="center" height="50%"}

## Formulaire basé sur un schéma

Les formulaires basés sur un schéma configurent automatiquement les sources de données et lient les champs de formulaire aux données. Cette approche est idéale pour les nouveaux formulaires dotés de structures de données bien définies.

### Créer un formulaire basé sur un schéma

1. **Accéder à la console Forms**
   - Connectez-vous à votre instance de création [!DNL Experience Manager Forms].
   - Accédez à **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents]**.

2. **Lancer la création du formulaire**
   - Sélectionnez **[!UICONTROL Créer]** > **[!UICONTROL Formulaires adaptatifs]**.
   - Choisissez un modèle Edge Delivery Services.
   - Cliquez sur **[!UICONTROL Créer]** lorsqu’il est activé.

   ![Modèle Edge Delivery Services](/help/edge/assets/create-eds-forms.png)

3. **Configurer un modèle de données**
   - Accédez à l’onglet **Données**.
   - Sélectionnez **Modèle de données de formulaire (FDM)** pour plusieurs sources de données ou **Schéma JSON** pour un seul système back-end.
   - Choisissez le FDM que vous avez créé (par exemple, Modèle de données de formulaire Pet).

   ![Sélectionner un modèle de données de formulaire](/help/edge/docs/forms/universal-editor/assets/select-petstore-form-data-model.png)

4. **Terminer la configuration du formulaire**
   - Saisissez le **Nom** et le **Titre**.
   - Spécifiez l’**URL GitHub** (par exemple, `https://github.com/wkndforms/edsforms`).
   - Cliquer sur **[!UICONTROL Créer]**

   ![Créer un formulaire basé sur un schéma](/help/edge/docs/forms/universal-editor/assets/create-schema-based-form.png)

### Vérifier le formulaire basé sur un schéma

Le formulaire s’ouvre dans l’éditeur universel avec une liaison de données préconfigurée :

![Copie d’écran de l’éditeur universel présentant un formulaire basé sur un schéma avec des champs de formulaire préremplis et le navigateur de contenu affichant les éléments de source de données disponibles](/help/edge/docs/forms/universal-editor/assets/schema-based-form-in-ue.png)

![Liaison de données automatique](/help/edge/docs/forms/universal-editor/assets/schema-based-form-data-binding.png)

## Formulaire non basé sur un schéma

Les formulaires non basés sur un schéma nécessitent une configuration manuelle de la source de données et une liaison de champs. Cette approche offre une certaine flexibilité pour les formulaires existants ou les exigences complexes.

### Créer un formulaire non basé sur un schéma

1. **Accéder aux propriétés du formulaire**
   - Connectez-vous à votre instance de création [!DNL Experience Manager Forms].
   - Accédez à **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents]**.
   - Sélectionner votre formulaire et cliquer sur **[!UICONTROL Propriétés]**

   ![Ouverture des propriétés du formulaire](/help/edge/docs/forms/universal-editor/assets/non-schema-based-edit-properties.png)

2. **Configurer un modèle de formulaire**
   - Ouvrez l’onglet **Modèle de formulaire**.
   - Sélectionnez **Modèle de données de formulaire (FDM)** dans le menu déroulant **Sélectionner à partir de**.
   - Choisissez votre FDM dans la liste.

   ![Sélection de l’onglet Modèle de formulaire](/help/edge/docs/forms/universal-editor/assets/select-form-model.png)

   ![Sélection de FDM](/help/edge/docs/forms/universal-editor/assets/select-fdm.png)

3. **Confirmation de la configuration**
   - Cliquez sur **OK** dans la boîte de dialogue d’avertissement.
   - Cliquer sur **[!UICONTROL Enregistrer et fermer]**

   ![Assistant de modèle de formulaire](/help/edge/docs/forms/universal-editor/assets/form-model-wizard.png)

### Ajouter des éléments de données

1. **Ouverture du formulaire pour le modifier**
   - Le formulaire s’ouvre dans l’éditeur universel.

   ![Création de formulaire non basé sur un schéma](/help/edge/docs/forms/universal-editor/assets/non-schema-form-authoring.png)

2. **Accès aux éléments de la source de données**
   - Accédez à l’onglet **[!UICONTROL Source de données]** dans l’**[!UICONTROL Explorateur de contenu]**.
   - Afficher les éléments de données disponibles dans votre FDM

   ![Source de données de formulaire](/help/edge/docs/forms/universal-editor/assets/non-schema-data-source.png)

3. **Ajout d’éléments au formulaire**
   - Sélectionnez des éléments de données et cliquez sur **[!UICONTROL Ajouter]**.
   - Vous pouvez également faire glisser des éléments pour créer votre formulaire.

   ![Ajout d’éléments de données](/help/edge/docs/forms/universal-editor/assets/non-schema-add-data-element.png)

   ![Capture d’écran montrant l’éditeur universel avec un formulaire non schématique en cours de création par glisser-déposer d’éléments de données, de l’onglet Source de données vers la structure du formulaire](/help/edge/docs/forms/universal-editor/assets/non-schema-form.png)

### Ajouter une liaison de données manuelle

Pour les champs de formulaire existants, ajoutez la liaison de données via la propriété **Référence de liaison** :

1. **Ouverture des propriétés des champs**
   - Sélectionnez le champ de formulaire à lier.
   - Ouvrez son panneau des propriétés.

2. **Configuration d’une référence de liaison**
   - Accédez à la propriété **Référence de liaison**.
   - Cliquez sur l’icône **Parcourir**.

   ![Ajout manuel de la liaison de données pour un champ de formulaire](/help/edge/docs/forms/universal-editor/assets/non-schema-add-data-binding.png)

3. **Sélection d’un élément de données**
   - Choisissez dans l’arborescence de la source de données de l’assistant **Sélectionner une référence de liaison**.
   - Sélectionnez l’élément de données souhaité et cliquez sur **Sélectionner**.

   ![Sélection de la référence de liaison de données](/help/edge/docs/forms/universal-editor/assets/select-bind-reference.png)

   ![Sélection de l’élément de données](/help/edge/docs/forms/universal-editor/assets/select-data-element.png)

4. **Vérification de la liaison**
   - Le champ de formulaire est désormais lié à l’élément de données.
   - La liaison apparaît dans la propriété **Référence de liaison**.

   ![Liaison de données automatique](/help/edge/docs/forms/universal-editor/assets/schema-based-form-data-binding.png)

## Vérifier l’intégration

Une fois l’intégration terminée :

1. **Tester la liaison de données** : vérifiez que les champs de formulaire affichent les données correctes.
2. **Valider les envois** : assurez-vous que les données sont enregistrées dans les sources configurées.
3. **Vérifier la gestion des erreurs** : testez avec des scénarios de données non valides.

## Étapes suivantes

Configurez les [actions Envoyer](/help/edge/docs/forms/universal-editor/submit-action.md) pour terminer votre workflow de formulaire.
