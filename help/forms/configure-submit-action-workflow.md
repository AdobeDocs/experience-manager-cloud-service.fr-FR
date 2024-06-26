---
Title: How to integrate AEM workflow with an Adaptive Form?
Description: Explore the process of automated workflow initiation with AEM Forms Submit Action.
keywords: Processus AEM, intégrer le formulaire adaptatif au processus AEM, appeler l’action d’envoi de processus de l’AEM
feature: Adaptive Forms, Core Components
exl-id: b7788e3d-acd8-4867-b232-f9767cf6b2f5
title: "Comment configurer une action Envoyer pour un formulaire adaptatif ?"
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 58%

---

# Intégrer AEM formulaire adaptatif à AEM Workflow : rationaliser les processus d’entreprise

La variable **[!UICONTROL Appeler un workflow d’AEM]** L’action Envoyer associe un formulaire adaptatif à un processus AEM. Lorsqu’un formulaire est envoyé, le processus associé commence automatiquement sur l’instance de création. Vous pouvez enregistrer les fichiers de données, les pièces jointes et le document d’enregistrement à l’emplacement de charge utile du workflow ou dans une variable. Si le processus est marqué pour le stockage de données externe et configuré pour un stockage de données externe, seule l’option variable est disponible. Vous pouvez choisir dans la liste des variables disponibles pour le modèle de workflow. Si le processus est marqué pour le stockage des données externes à une étape ultérieure et non au moment de la création du processus, assurez-vous que les configurations de variable requises sont en place.

>[!NOTE]
>
>  Découvrez comment [créer un modèle de workflow ;](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=fr#extending-aem) pour définir la série d’étapes exécutées lorsqu’un utilisateur démarre le workflow. Vous pouvez également définir des propriétés de modèle pour déterminer, par exemple, si le workflow est transitoire ou s’il utilise plusieurs ressources.

AEM as a Cloud Service propose différentes actions d’envoi prêtes à l’emploi pour gérer les envois de formulaire. Pour en savoir plus sur ces options, voir [Action d’envoi de formulaire adaptatif](/help/forms/configure-submit-actions-core-components.md)  article.

## Avantages

Voici quelques-uns des avantages de l’intégration du processus AEM à Adaptive Forms :

* L’intégration AEM Workflow permet d’automatiser des processus d’entreprise complexes impliquant des envois de formulaire.
* AEM Workflow prend en charge la logique conditionnelle, ce qui permet des décisions dynamiques basées sur des données de formulaire ou des facteurs externes.
* AEM Workflow achemine les tâches en fonction de règles et de conditions prédéfinies, en s’assurant que les tâches sont assignées aux personnes ou aux groupes appropriés.

<!--
## Prerequisites

Before using the **[!UICONTROL Invoke an AEM Workflow]** Submit Action configure the following for the **[!UICONTROL AEM DS settings service]** configuration: 

* **[!UICONTROL Processing Server URL]**: The Processing Server is the server where the Forms or AEM Workflow is triggered. This can be same as the URL of the AEM author instance or another server.

* **[!UICONTROL Processing Server User Name]**: Workflow user's username

* **[!UICONTROL Processing Server Password]**: Workflow user's password -->

## Intégration d’AEM Workflow à Adaptive Forms {#steps-to-integrate-workflow-with-af}

Pour configurer un processus automatisé avec [Processus AEM](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=fr#extending-aem) pour un formulaire adaptatif, procédez comme suit :

1. Ouvrez l’explorateur de contenu, puis sélectionnez le composant **[!UICONTROL Conteneur de guide]** de votre formulaire adaptatif.
1. Cliquez sur l’icône des propriétés du conteneur de guide ![Propriétés du guide](/help/forms/assets/configure-icon.svg). La fenêtre du conteneur de formulaires adaptatifs s’ouvre.
1. Cliquez sur l’onglet **[!UICONTROL Envoi]**.
1. Dans la **[!UICONTROL Action Envoyer]** liste déroulante, sélectionnez **[!UICONTROL Appeler un workflow d’AEM]** .
   ![Configuration des actions pour Send Email](/help/forms/assets/configure-invoke-aem-workflow.png)

1. Sélectionnez le modèle de workflow dans la **[!UICONTROL Modèle de workflow]** liste déroulante.
1. Sélectionnez l’option dans la **[!UICONTROL Stocker les données à l’aide de]** liste déroulante.

   **Fichier de données** : Il contient les données envoyées au formulaire adaptatif. Vous pouvez utiliser l’option **[!UICONTROL Chemin d’accès au fichier de données]** pour spécifier le nom du fichier et le chemin d’accès du fichier par rapport à la charge utile. Par exemple, le chemin d’accès `/addresschange/data.xml` crée un dossier nommé `addresschange` et le place par rapport à la charge utile. Vous pouvez également spécifier uniquement `data.xml` pour envoyer uniquement les données envoyées sans créer de hiérarchie de dossiers. Si le workflow est marqué pour le stockage de données externe, utilisez l’option variable et sélectionnez la variable dans la liste des variables disponibles pour le modèle de workflow.

1. Sélectionnez l’option dans la **[!UICONTROL Stocker les pièces jointes à l’aide de]** liste déroulante.

   **Pièces jointes** : vous pouvez utiliser l’option **[!UICONTROL Chemin d’accès aux pièces jointes]** pour spécifier le nom de dossier dans lequel stocker les pièces jointes chargées dans le formulaire adaptatif. Le dossier est créé par rapport à la payload. Si le workflow est marqué pour le stockage de données externe, utilisez l’option variable et sélectionnez la variable dans la liste des variables disponibles pour le modèle de workflow.

1. Sélectionnez l’option dans la **[!UICONTROL Documents d’enregistrement utilisant]** liste déroulante.

   **Document d’enregistrement** : il contient le document d’enregistrement généré pour le formulaire adaptatif. Vous pouvez utiliser l’option **[!UICONTROL Chemin du document d’enregistrement]** pour spécifier le nom du fichier de document d’enregistrement et le chemin d’accès du fichier par rapport à la charge utile. Par exemple, le chemin d’accès `/addresschange/DoR.pdf` crée un dossier nommé `addresschange` relatif à la charge utile et place `DoR.pdf` relatif à la charge utile. Vous pouvez également spécifier uniquement `DoR.pdf` pour n’enregistrer que le document d’enregistrement sans créer de hiérarchie de dossiers. Si le workflow est marqué pour le stockage de données externe, utilisez l’option variable et sélectionnez la variable dans la liste des variables disponibles pour le modèle de workflow.
1. Cliquez sur **[!UICONTROL Terminé]**.

>[!NOTE]
>
> En savoir plus sur [Processus d’AEM centrés sur Forms - Référence d’étape pour automatiser les processus d’entreprise](/help/forms/aem-forms-workflow-step-reference.md).

<!--
## Best Practices

* When configuring the **[!UICONTROL Invoke an AEM Workflow]** Submit Action, select the appropriate workflow model that aligns with the desired business process.
* In case, the workflow involves external data storage, be sure to configure the workflow accordingly. It is recommended to set up variables appropriately and in accordance with any external storage requirements. -->

## Articles connexes

{{af-submit-action}}
