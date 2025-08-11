---
title: Comment intégrer un modèle de données de formulaire (FDM) pour un formulaire dans l’éditeur universel ?
description: Découvrez comment créer des formulaires pour les services de diffusion Edge basés sur un modèle de données de formulaire (FDM). Générer et modifiez des données d’exemples pour les objets de modèle de données dans FDM.
feature: Edge Delivery Services, Form Data Model
role: Admin, User
exl-id: 9ce51223-57d0-47d8-8868-84b37d4e8e3e
source-git-commit: cfff846e594b39aa38ffbd3ef80cce1a72749245
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 32%

---


# Intégration de Forms au modèle de données de formulaire (FDM)

Connectez vos formulaires aux sources de données principales à l’aide de FDM pour activer les workflows de liaison, de validation et d’envoi de données.

## Prérequis

Effectuez les étapes suivantes avant d’intégrer FDM à vos formulaires :

1. **[Configurer la Source de données](/help/forms/configure-data-sources.md)** : configurer des connexions principales
2. **[Créer un modèle de données de formulaire](/help/forms/create-form-data-models.md)** : définir la structure et les services de données
3. **[Configurer des objets de modèle de données](/help/forms/work-with-form-data-model.md)** : mappage des relations de données

## Considérations

Si l’icône **Sources de données** ne s’affiche pas dans l’interface de l’éditeur universel ou si la propriété **Référence de liaison** n’apparaît pas dans le panneau de propriété de droite, activez l’extension **Source de données** dans **Extension Manager**.

![Capture d’écran de l’interface Extension Manager de l’éditeur universel présentant les extensions disponibles, y compris l’extension Sources de données, qui peuvent être activées pour l’intégration de formulaires](/help/edge/docs/forms/universal-editor/assets/extension-manager.png)

Consultez l’article [Caractéristiques des fonctionnalités d’Extension Manager](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions) pour savoir comment activer et désactiver les extensions dans l’éditeur universel.

## Choisissez votre type de formulaire

L’éditeur universel prend en charge deux approches de création de formulaire :

| Aspect | Formulaire basé sur un schéma | Formulaire non basé sur un schéma |
|--------|-------------------|----------------------|
| **Complexité de la configuration** | Simple (liaison automatique) | Manuel (liaison champ par champ) |
| **Cas d’utilisation** | Nouveaux formulaires avec structure de données définie | Formulaires existants ou exigences flexibles |
| **Source de données** | Requis lors de la création | Peut être ajouté ultérieurement |
| **Liaison** | Liaison de champ automatique | Liaison manuelle par champ |

![Types de formulaire dans l’éditeur universel](/help/edge/docs/forms/universal-editor/assets/form-types.png){width="50%" align="center" height="50%"}

## Formulaire basé sur un schéma

Les formulaires basés sur un schéma configurent automatiquement les sources de données et lient les champs de formulaire aux données. Cette approche est idéale pour les nouveaux formulaires dotés de structures de données bien définies.

### Créer Un Formulaire Basé Sur Un Schéma

1. **Accéder à la console Forms**
   - Connectez-vous à votre instance d’auteur [!DNL Experience Manager Forms]
   - Accédez à **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms et documents]**

2. **Démarrer la création du formulaire**
   - Sélectionnez **[!UICONTROL Créer]** > **[!UICONTROL Forms adaptatif]**
   - Choisir un modèle Edge Delivery Services
   - Cliquez sur **[!UICONTROL Créer]** lorsqu’il est activé.

   ![Modèle Edge Delivery Services](/help/edge/assets/create-eds-forms.png)

3. **Configurer le modèle de données**
   - Accédez à l’onglet **Données**
   - Sélectionnez **Modèle de données de formulaire (FDM)** pour plusieurs sources de données ou **Schéma JSON** pour un seul système principal
   - Choisissez le FDM que vous avez créé (par exemple, Modèle de données de formulaire prédéfini)

   ![Sélectionner un modèle de données de formulaire](/help/edge/docs/forms/universal-editor/assets/select-petstore-form-data-model.png)

4. **Terminer la configuration du formulaire**
   - Saisissez **Nom** et **Titre**
   - Spécifiez **URL GitHub** (par exemple, `https://github.com/wkndforms/edsforms`).
   - Cliquez sur **[!UICONTROL Créer]**.

   ![Créer un formulaire basé sur un schéma](/help/edge/docs/forms/universal-editor/assets/create-schema-based-form.png)

### Vérifier le formulaire basé sur un schéma

Le formulaire s’ouvre dans l’éditeur universel avec une liaison de données préconfigurée :

![Copie d’écran de l’éditeur universel présentant un formulaire basé sur un schéma avec des champs de formulaire préremplis et le navigateur de contenu affichant les éléments de source de données disponibles](/help/edge/docs/forms/universal-editor/assets/schema-based-form-in-ue.png)

![Liaison de données automatique](/help/edge/docs/forms/universal-editor/assets/schema-based-form-data-binding.png)

## Formulaire non basé sur un schéma

Les formulaires non schématiques nécessitent une configuration manuelle de la source de données et une liaison de champs. Cette approche offre une certaine flexibilité pour les formulaires existants ou les exigences complexes.

### Créer Un Formulaire Non Basé Sur Un Schéma

1. **Accéder aux propriétés du formulaire**
   - Connectez-vous à votre instance d’auteur [!DNL Experience Manager Forms]
   - Accédez à **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms et documents]**
   - Sélectionnez votre formulaire et cliquez sur **[!UICONTROL Propriétés]**

   ![Ouverture des propriétés du formulaire](/help/edge/docs/forms/universal-editor/assets/non-schema-based-edit-properties.png)

2. **Configurer le modèle de formulaire**
   - Ouvrez l’onglet **Modèle de formulaire**
   - Sélectionnez **Modèle de données de formulaire (FDM)** dans le menu déroulant **Sélectionner à partir de**.
   - Choisissez votre FDM dans la liste

   ![Sélection de l’onglet Modèle de formulaire](/help/edge/docs/forms/universal-editor/assets/select-form-model.png)

   ![Sélection de FDM](/help/edge/docs/forms/universal-editor/assets/select-fdm.png)

3. **Confirmer la configuration**
   - Cliquez sur **OK** dans la boîte de dialogue d’avertissement
   - Cliquez sur **[!UICONTROL Enregistrer et fermer]**.

   ![Assistant de modèle de formulaire](/help/edge/docs/forms/universal-editor/assets/form-model-wizard.png)

### Ajouter des éléments de données

1. **Ouvrir le formulaire pour le modifier**
   - Le formulaire s’ouvre en éditeur universel

   ![Création de formulaire non basé sur un schéma](/help/edge/docs/forms/universal-editor/assets/non-schema-form-authoring.png)

2. **Accès aux éléments de la Source de données**
   - Accédez à l’onglet **[!UICONTROL Source de données]** dans l’**[!UICONTROL Explorateur de contenu]**
   - Affichage des éléments de données disponibles à partir de votre FDM

   ![Source de données de formulaire](/help/edge/docs/forms/universal-editor/assets/non-schema-data-source.png)

3. **Ajouter des éléments au formulaire**
   - Sélectionnez les éléments de données et cliquez sur **[!UICONTROL Ajouter]**
   - Vous pouvez également faire glisser des éléments pour créer votre formulaire

   ![Ajout d’éléments de données](/help/edge/docs/forms/universal-editor/assets/non-schema-add-data-element.png)

   ![Capture d’écran montrant l’éditeur universel avec un formulaire non schématique en cours de création par glisser-déposer d’éléments de données, de l’onglet Source de données vers la structure du formulaire](/help/edge/docs/forms/universal-editor/assets/non-schema-form.png)

### Ajouter une liaison de données manuelle

Pour les champs de formulaire existants, ajoutez la liaison de données via la propriété **Référence de liaison** :

1. **Ouvrir les propriétés du champ**
   - Sélectionner le champ de formulaire à lier
   - Ouvrir son panneau des propriétés

2. **Configurer la référence de liaison**
   - Accédez à la propriété **Référence de liaison**
   - Cliquez sur l’icône **Parcourir**

   ![Ajout manuel de la liaison de données pour un champ de formulaire](/help/edge/docs/forms/universal-editor/assets/non-schema-add-data-binding.png)

3. **Sélectionner l’élément de données**
   - Faites votre choix dans l’arborescence de la source de données de l’assistant **Sélectionner une référence de liaison**.
   - Sélectionnez l’élément de données souhaité, puis cliquez sur **Sélectionner**

   ![Sélection de la référence de liaison de données](/help/edge/docs/forms/universal-editor/assets/select-bind-reference.png)

   ![Sélection de l’élément de données](/help/edge/docs/forms/universal-editor/assets/select-data-element.png)

4. **Vérifier la liaison**
   - Le champ de formulaire se lie désormais à l’élément de données
   - La liaison apparaît dans la propriété **Référence de liaison**

   ![Liaison de données automatique](/help/edge/docs/forms/universal-editor/assets/schema-based-form-data-binding.png)

## Vérifier l’intégration

Une fois l’intégration terminée :

1. **Tester la liaison de données** : vérifier que les champs du formulaire affichent les données correctes
2. **Valider les envois** : assurez-vous que les données sont enregistrées dans les sources configurées
3. **Vérifier la gestion des erreurs** : test avec des scénarios de données non valides

## Étapes suivantes

Configurez les [actions d’envoi](/help/edge/docs/forms/universal-editor/submit-action.md) pour terminer le processus de formulaire.
