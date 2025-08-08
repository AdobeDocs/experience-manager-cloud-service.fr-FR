---
title: Comment intégrer le modèle de données de formulaire (FDM) d’un formulaire à un formulaire adaptatif ?
description: Découvrez comment créer des formulaires basés sur un modèle de données de formulaire (FDM). Générer et modifiez des données d’exemples pour les objets de modèle de données dans FDM.
feature: Edge Delivery Services, Adaptive Forms, Form Data Model
role: Admin, User
source-git-commit: 62134c5b67d610f801c407e696e761ed05e02c87
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 31%

---

# Intégration de formulaires au modèle de données de formulaire

L’intégration de formulaires à un modèle de données de formulaire (FDM) vous permet d’utiliser diverses sources de données principales pour créer un modèle de données de formulaire (FDM). Vous pouvez utiliser le modèle de données de formulaire (FDM) comme schéma dans divers workflows de formulaire. Configurez les sources de données et créez un modèle de données de formulaire (FDM) basé sur les objets et services de modèle de données disponibles dans les sources de données.

## Avantages de l’intégration de Forms au modèle de données de formulaire (FDM)

* **Connectivité back-end transparente** : connectez les formulaires à divers systèmes back-end (par exemple, bases de données, API REST, services SOAP, CRM) sans code personnalisé. Cela permet l’échange de données en temps réel et réduit les efforts d’intégration.
* **Schéma de données centralisé** le modèle de données de formulaire sert de schéma de données unifié qui simplifie le mappage et la gestion des objets et services de données utilisés dans plusieurs formulaires et workflows.

* **Amélioration du préremplissage et de l’envoi de formulaire** : configurez facilement les actions de préremplissage et d’envoi à l’aide des services de données de formulaire, en assurant une récupération et un stockage des données précis et à jour.

* **Prise en charge des workflows dynamiques** : le modèle de données de formulaire peut être intégré aux workflows pour automatiser les processus métier en fonction des données envoyées ou récupérées, ce qui améliore l’efficacité globale.

## Conditions préalables

Avant de configurer votre formulaire avec le modèle de données de formulaire, assurez-vous d’avoir effectué les étapes suivantes :

* [Configurer la source de données](/help/forms/configure-data-sources.md) : configurez la source de données pour connecter votre formulaire aux données back-end.
* [Créer un modèle de données de formulaire (FDM)](/help/forms/create-form-data-models.md) : créez un modèle de données à l’aide des objets et services de données provenant de la source de données configurée.
* [Configurer les objets et services de modèle de données](/help/forms/work-with-form-data-model.md) : mappez les objets et services de modèle de données afin d’assurer un flux de données fluide entre le formulaire et la source de données.

>[!BEGINTABS]

>[!TAB Composant de base]

Pour configurer le modèle de données de formulaire avec un formulaire adaptatif basé sur un composant de base comme suit :

1. Ouvrez le formulaire adaptatif pour le modifier et accéder à la section **[!UICONTROL Envoi]** des propriétés du Conteneur de formulaires adaptatifs.
1. Dans la liste déroulante **[!UICONTROL Action d’envoi]**, sélectionnez **[!UICONTROL Envoyer à l’aide du modèle de données de formulaire]**.

   ![envoyer à l’aide du modèle de données de formulaire](/help/forms/assets/submit-uisng-fdm-fc.png)

1. Sélectionnez la configuration **[!UICONTROL Modèle de données à envoyer]** créée.
Pour envoyer des pièces jointes à la base de données, sélectionnez **Envoyer les pièces jointes du formulaire**. Le document d’enregistrement est enregistré dans la base de données en sélectionnant **Envoyer le document d’enregistrement**.
1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les paramètres d’envoi.

>[!TAB Composant principal]

Pour configurer le modèle de données de formulaire avec un formulaire adaptatif basé sur le composant principal comme suit :

1. Ouvrez l’explorateur de contenu, puis sélectionnez le composant **[!UICONTROL Conteneur de guide]** de votre formulaire adaptatif.
1. Cliquez sur l’icône des propriétés du conteneur de guide ![Propriétés du guide](/help/forms/assets/configure-icon.svg). La fenêtre du conteneur de formulaires adaptatifs s’ouvre.
1. Cliquez sur l’onglet **[!UICONTROL Envoi]**.
1. Dans la liste déroulante **[!UICONTROL Action d’envoi]**, sélectionnez **[Envoyer à l’aide du modèle de données de formulaire]**.

   ![envoyer à l’aide du modèle de données de formulaire](/help/forms/assets/submit-uisng-fdm-cc.png)

1. Sélectionnez la configuration **[!UICONTROL Modèle de données à envoyer]** créée.
Pour envoyer des pièces jointes à la base de données, sélectionnez **Envoyer les pièces jointes du formulaire**. Le document d’enregistrement est enregistré dans la base de données en sélectionnant **Envoyer le document d’enregistrement**.
1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les paramètres d’envoi.

>[!TAB Éditeur universel]

Pour configurer le modèle de données de formulaire avec un formulaire adaptatif créé dans Universal comme suit :

1. Ouvrez le formulaire adaptatif pour le modifier.
1. Cliquez sur l’extension **Modifier les propriétés du formulaire** dans l’éditeur.

   La boîte de dialogue **Propriétés du formulaire** s’affiche.

   >[!NOTE]
   >
   > * Si l’icône **Modifier les propriétés de formulaire** ne s’affiche pas dans l’interface de l’éditeur universel, activez l’extension **Modifier les propriétés de formulaire** dans Extension Manager.
   > * Consultez l’article [Caractéristiques des fonctionnalités d’Extension Manager](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions) pour savoir comment activer ou désactiver les extensions dans l’éditeur universel.

1. Cliquez sur l’onglet **Envoi** et sélectionnez **[!UICONTROL Envoyer à l’aide du modèle de données de formulaire]**.

   ![OneDrive GIF](/help/forms/assets/submit-uisng-fdm-ue.png)
Si vous sélectionnez **Enregistrer les pièces jointes avec le nom d’origine**, les pièces jointes sont stockées dans le dossier à l’aide de leurs noms de fichier d’origine. Vous pouvez également enregistrer un document d’enregistrement (DE) dans le stockage Blob Azure.

1. Sélectionnez la **[!UICONTROL configuration de stockage]** où vous souhaitez enregistrer vos données.
1. Cliquez sur **[!UICONTROL Enregistrer et fermer]**

Pour obtenir des instructions détaillées sur l’intégration des formulaires créés dans l’éditeur universel, reportez-vous à l’article [Intégration de Forms au modèle de données de formulaire dans l’éditeur universel](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md).

>[!ENDTABS]

## Articles connexes

{{af-submit-action}}
