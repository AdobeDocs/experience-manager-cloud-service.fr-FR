---
title: Comment connecter AEM formulaire adaptatif à Microsoft&reg; SharePoint List ?
description: Connectez un formulaire adaptatif à Microsoft&reg; SharePoint List. Découvrez comment configurer Microsoft&reg; SharePoint list et créer un modèle de données de formulaire (FDM) à l’aide de la configuration. En outre, vous pouvez apprendre à intégrer le FDM à votre formulaire adaptatif.
role: User, Developer
keywords: Connectez AEM formulaire adaptatif à la liste SharePoint Microsoft, connectez le formulaire adaptatif à la liste SharePoint de Microsoft, intégrez AEM formulaire adaptatif à la liste SharePoint Microsoft, intégrez le formulaire adaptatif à la liste de , envoyez les données d’un formulaire adaptatif à la liste de , envoyez le processus d’ à la liste de .
hide: true
hidefromToC: true
source-git-commit: 81951a9507ec3420cbadb258209bdc8e2b5e2942
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 10%

---


# Connecter un formulaire adaptatif à une liste Microsoft® SharePoint

<span class="preview"> Il s’agit d’une fonctionnalité de préversion accessible par le biais de notre [canal de pré-version](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/release-notes/prerelease#new-features). </span>

**Microsoft® SharePoint** : Microsoft® SharePoint permet la collaboration en fournissant des sites d’équipe dynamiques et efficaces pour toutes les équipes, tous les départements et toutes les divisions. Il permet de stocker, d’organiser, de partager et d’accéder aux informations de n’importe quel périphérique à l’aide de n’importe quel navigateur Web, par exemple Microsoft® Edge, Internet Explorer, Chrome ou Firefox. Les deux composants principaux de **Microsoft® SharePoint** sont les suivants :

* **Bibliothèque de documents SharePoint Microsoft®** : la bibliothèque de documents SharePoint de Microsoft® affiche une liste de fichiers et de dossiers avec leurs informations clés, telles que la date de dernière modification et le propriétaire d’un fichier. Cette fonctionnalité facilite l’organisation et la navigation des fichiers.
Pour plus d’informations sur l’intégration d’une **bibliothèque de documents SharePoint Microsoft®** à un formulaire adaptatif, reportez-vous à l’article [ Action d’envoi de formulaire adaptatif](/help/forms/configuring-submit-actions.md#submit-to-sharepoint) .

* **Microsoft® SharePoint List** : Microsoft® SharePoint List est une collection de données. Vous pouvez ajouter des colonnes pour différents types de données et créer des vues afin d’afficher efficacement les données. Vous pouvez regrouper, filtrer, trier et formater facilement les listes.

>[!VIDEO](https://video.tv.adobe.com/v/3424820/connect-aem-adaptive-form-to-sharepointlist/?quality=12&learn=on)

## Conditions préalables pour connecter un formulaire adaptatif à la liste SharePoint Microsoft® {#prerequisites}

Avant de connecter un formulaire adaptatif à la liste SharePoint Microsoft®, procédez comme suit :

1. [Configuration de Microsoft](/help/forms/configure-data-sources.md#configure-microsoft-sharepoint-list)
1. [Création d’un modèle de données de formulaire (FDM) à l’aide de Microsoft](/help/forms/create-form-data-models.md)
1. [Configuration du modèle de données de formulaire (FDM) pour récupérer et envoyer des données](/help/forms/work-with-form-data-model.md#configure-services)
1. [Créer un formulaire adaptatif](/help/forms/creating-adaptive-form-core-components.md)

Vous pouvez désormais :

* [Connexion à Microsoft](#connect-an-adaptive-form-to-microsoft-sharepoint-list-connect-af-sharepoint-list)
* [Connexion à Microsoft](#connect-sharepoint-list-workflow)

## Connecter un formulaire adaptatif à une liste Microsoft® SharePoint {#connect-af-sharepoint-list}

Pour intégrer la liste SharePoint Microsoft® à votre formulaire adaptatif [configurez un formulaire adaptatif pour utiliser un modèle de données de formulaire (FDM)](/help/forms/creating-adaptive-form-core-components.md#configure-a-schema-or-form-data-model-for-an-adaptive-formconfigure-schema-or-data-model-for-form)

Après avoir configuré un formulaire adaptatif pour utiliser un modèle de données de formulaire (FDM), vous pouvez :

* [Configuration de l’action Envoyer à l’aide d’un modèle de données de formulaire (FDM)](/help/forms/configuring-submit-actions.md#submit-using-form-data-model)
* [Configuration de l’éditeur de règles pour appeler un modèle de données de formulaire (FDM)](/help/forms/rule-editor.md#invoke-form-data-model-service-invoke)

## Connecter Microsoft® SharePoint List à un workflow AEM {#connect-sharepoint-list-workflow}

Pour intégrer la liste SharePoint Microsoft® à un workflow AEM :

1. [Créer un workflow pour appeler un modèle de données de formulaire (FDM)](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=fr)

   <!--
    To create a workflow with the editor:
    1.  Go to your **AEM Forms Author** instance > **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
    1.  Click **[!UICONTROL Create]** > **[!UICONTROL Create Model]**. The Add Workflow Model dialog appears. 
    1. Specify **[!UICONTROL Title]** and **[!UICONTROL Name (optional)]**.
    1. Click **[!UICONTROL Done]**. The new model is listed in the Workflow Models console.
    1. Select your new workflow, then use **[!UICONTROL Edit]** to open it for configuration.
    1. Add **[!UICONTROL Invoke Form Data Model Service]** step to your workflow.
    1. Confirm the changes with Sync (editor toolbar) to generate the runtime model.
    -->

1. [Configuration d’une action Envoyer pour appeler un processus AEM](/help/forms/configuring-submit-actions.md#invoke-an-aem-workflow)


Découvrez comment [utiliser AEM Workflow](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/workflow/use-workflow.html) pour collaborer, gérer et traiter du contenu dans un formulaire adaptatif.

## Bonnes pratiques {#best-practices}

<!-- * For storing data in a tabular format or implementing data permissions, it is advisable to use Microsoft&reg; SharePoint List rather than Microsoft&reg; SharePoint Document Library. -->
* Dans la liste Microsoft® SharePoint, les types de colonnes suivants ne sont pas pris en charge :
   * Colonne image
   * Colonne métadonnées
   * Colonne personne
   * Colonne données externes

## Voir également {#see-also}

* [Création d’un formulaire adaptatif basé sur les composants principaux](/help/forms/creating-adaptive-form-core-components.md)
* [Configurer des sources de données](/help/forms/configuring-submit-actions.md)
* [Créer un modèle de données de formulaire (FDM)](/help/forms/create-form-data-models.md)
* [Utilisation de processus d’AEM basés sur Forms - Référence d’étape pour automatiser les processus d’entreprise](/help/forms/aem-forms-workflow-step-reference.md)
* [Création d’une action Envoyer personnalisée pour les formulaires adaptatifs](/help/forms/custom-submit-action-form.md)
* [Création ou ajout d’un formulaire adaptatif à une page AEM Sites](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)
* [Incorporation d’un formulaire adaptatif à une page AEM Sites](/help/forms/embed-adaptive-form-aem-sites.md)
* [Créer, utiliser et personnaliser des thèmes dans un formulaire adaptatif](/help/forms/using-themes-in-core-components.md)







