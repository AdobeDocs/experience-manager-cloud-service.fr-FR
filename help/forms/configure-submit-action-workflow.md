---
title: Comment intégrer un workflow AEM à un formulaire adaptatif ?
description: Explorez le processus de lancement automatisé des workflows avec l’action d’envoi AEM Forms.
keywords: Processus AEM, intégrer le formulaire adaptatif au processus AEM, appeler l’action d’envoi du processus AEM
feature: Adaptive Forms, Core Components
exl-id: b7788e3d-acd8-4867-b232-f9767cf6b2f5
role: User, Developer
source-git-commit: 1be7bafc1d93a65a81eeb2f7e86cac33cde7aa35
workflow-type: tm+mt
source-wordcount: '1434'
ht-degree: 64%

---

# Intégrer le formulaire adaptatif AEM au processus AEM : rationalisation des processus d’entreprise

L’action d’envoi **[!UICONTROL Appeler un processus AEM]** associe un formulaire adaptatif à un processus AEM. Lorsqu’un formulaire est envoyé, le processus associé commence automatiquement sur l’instance de création. Vous pouvez enregistrer les fichiers de données, les pièces jointes et le document d’enregistrement à l’emplacement de la payload du workflow ou dans une variable. Si le processus est marqué pour le stockage de données externe et configuré pour un stockage de données externe, seule l’option variable est disponible. Vous pouvez choisir dans la liste des variables disponibles pour le modèle de workflow. Si le processus est marqué pour le stockage des données externes à une étape ultérieure et non au moment de la création du processus, assurez-vous que les configurations de variable requises sont en place.

>[!NOTE]
>
>  Découvrez comment [créer un modèle de workflow](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=fr#extending-aem) pour définir les étapes exécutées lorsqu’un utilisateur lance le workflow. Vous pouvez également définir des propriétés de modèle pour déterminer, par exemple, si le workflow est transitoire ou s’il utilise plusieurs ressources.

AEM as a Cloud Service propose différentes actions d’envoi prêtes à l’emploi pour gérer les envois de formulaires. Pour en savoir plus sur ces options, consultez l’article [Action d’envoi de formulaire adaptatif](/help/forms/configure-submit-actions-core-components.md).

## Avantages

Voici quelques-uns des avantages de l’intégration du workflow AEM à Adaptive Forms :

* L’intégration des workflows AEM permet d’automatiser les processus métier complexes impliquant des envois de formulaires.
* Les processus AEM prennent en charge la logique conditionnelle, ce qui permet de prendre des décisions dynamiques basées sur des données de formulaire ou des facteurs externes.
* Le workflow AEM achemine les tâches en fonction de règles et de conditions prédéfinies, en s’assurant que les tâches sont affectées aux personnes ou aux groupes appropriés.

<!--
## Prerequisites

Before using the **[!UICONTROL Invoke an AEM Workflow]** Submit Action configure the following for the **[!UICONTROL AEM DS settings service]** configuration: 

* **[!UICONTROL Processing Server URL]**: The Processing Server is the server where the Forms or AEM Workflow is triggered. This can be same as the URL of the AEM author instance or another server.

* **[!UICONTROL Processing Server User Name]**: Workflow user's username

* **[!UICONTROL Processing Server Password]**: Workflow user's password -->

## Intégration d’un workflow AEM à un Forms adaptatif {#steps-to-integrate-workflow-with-af}

>[!BEGINTABS]

>[!TAB Composant de base]

Pour configurer un processus automatisé avec [AEM Workflow](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=fr#extending-aem) pour un formulaire adaptatif basé sur des composants de base, procédez comme suit :

1. Ouvrez le formulaire adaptatif pour le modifier et accéder à la section **[!UICONTROL Envoi]** des propriétés du Conteneur de formulaires adaptatifs.
1. Dans la liste déroulante **[!UICONTROL Action Envoyer]**, sélectionnez **Action Envoyer** comme **[!UICONTROL Appeler un workflow AEM]**.
1. Sélectionnez le modèle de workflow dans la liste déroulante **[!UICONTROL Modèle de workflow]**.
1. Sélectionnez l’option dans la liste déroulante **[!UICONTROL Stocker le fichier de données à l’aide de]**.

   **Fichier de données** : Il contient les données envoyées au formulaire adaptatif. Vous pouvez utiliser l’option **[!UICONTROL Chemin d’accès au fichier de données]** pour spécifier le nom du fichier et le chemin d’accès du fichier par rapport à la charge utile. Par exemple, le chemin d’accès `/addresschange/data.xml` crée un dossier nommé `addresschange` et le place par rapport à la charge utile. Vous pouvez également spécifier uniquement `data.xml` pour envoyer uniquement les données envoyées sans créer de hiérarchie de dossiers. Si le workflow est marqué pour le stockage de données externe, utilisez l’option variable et sélectionnez la variable dans la liste des variables disponibles pour le modèle de workflow.

   ![invoke-workflow-fc](/help/forms/assets/invoke-workflow-fc.png)

1. Sélectionnez l’option dans la liste déroulante **[!UICONTROL Stocker les pièces jointes en utilisant]**.

   **Pièces jointes** : vous pouvez utiliser l’option **[!UICONTROL Chemin d’accès aux pièces jointes]** pour spécifier le nom de dossier dans lequel stocker les pièces jointes chargées dans le formulaire adaptatif. Le dossier est créé par rapport à la payload. Si le workflow est marqué pour le stockage de données externe, utilisez l’option variable et sélectionnez la variable dans la liste des variables disponibles pour le modèle de workflow.

1. Sélectionnez l’option dans la liste déroulante **[!UICONTROL Documents d’enregistrement à l’aide de]**.

   **Document d’enregistrement** : il contient le document d’enregistrement généré pour le formulaire adaptatif. Vous pouvez utiliser l’option **[!UICONTROL Chemin du document d’enregistrement]** pour spécifier le nom du fichier de document d’enregistrement et le chemin d’accès du fichier par rapport à la charge utile. Par exemple, le chemin d’accès `/addresschange/DoR.pdf` crée un dossier nommé `addresschange` relatif à la charge utile et place `DoR.pdf` relatif à la charge utile. Vous pouvez également spécifier uniquement `DoR.pdf` pour n’enregistrer que le document d’enregistrement sans créer de hiérarchie de dossiers. Si le workflow est marqué pour le stockage de données externe, utilisez l’option variable et sélectionnez la variable dans la liste des variables disponibles pour le modèle de workflow.
1. Cliquez sur **[!UICONTROL Terminé]**.

   >[!NOTE]
   >
   > En savoir plus sur les [workflows centrés sur Forms d’AEM - Référence des étapes pour automatiser les processus métier](/help/forms/aem-forms-workflow-step-reference.md).

>[!TAB Composant principal]

Pour configurer un processus automatisé avec [AEM Workflow](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=fr#extending-aem) pour un formulaire adaptatif basé sur les composants principaux, procédez comme suit :

1. Ouvrez l’explorateur de contenu, puis sélectionnez le composant **[!UICONTROL Conteneur de guide]** de votre formulaire adaptatif.
1. Cliquez sur l’icône des propriétés du conteneur de guide ![Propriétés du guide](/help/forms/assets/configure-icon.svg). La fenêtre du conteneur de formulaires adaptatifs s’ouvre.
1. Cliquez sur l’onglet **[!UICONTROL Envoi]**.
1. Dans la liste déroulante **[!UICONTROL Action Envoyer]**, sélectionnez **[!UICONTROL Appeler un workflow AEM]** .

   ![Configuration de l’action Envoyer un e-mail](/help/forms/assets/configure-invoke-aem-workflow.png)

1. Sélectionnez le modèle de workflow dans la liste déroulante **[!UICONTROL Modèle de workflow]**.
1. Sélectionnez l’option dans la liste déroulante **[!UICONTROL Stocker le fichier de données à l’aide de]**.

   **Fichier de données** : Il contient les données envoyées au formulaire adaptatif. Vous pouvez utiliser l’option **[!UICONTROL Chemin d’accès au fichier de données]** pour spécifier le nom du fichier et le chemin d’accès du fichier par rapport à la charge utile. Par exemple, le chemin d’accès `/addresschange/data.xml` crée un dossier nommé `addresschange` et le place par rapport à la charge utile. Vous pouvez également spécifier uniquement `data.xml` pour envoyer uniquement les données envoyées sans créer de hiérarchie de dossiers. Si le workflow est marqué pour le stockage de données externe, utilisez l’option variable et sélectionnez la variable dans la liste des variables disponibles pour le modèle de workflow.

1. Sélectionnez l’option dans la liste déroulante **[!UICONTROL Stocker les pièces jointes en utilisant]**.

   **Pièces jointes** : vous pouvez utiliser l’option **[!UICONTROL Chemin d’accès aux pièces jointes]** pour spécifier le nom de dossier dans lequel stocker les pièces jointes chargées dans le formulaire adaptatif. Le dossier est créé par rapport à la payload. Si le workflow est marqué pour le stockage de données externe, utilisez l’option variable et sélectionnez la variable dans la liste des variables disponibles pour le modèle de workflow.

1. Sélectionnez l’option dans la liste déroulante **[!UICONTROL Documents d’enregistrement à l’aide de]**.

   **Document d’enregistrement** : il contient le document d’enregistrement généré pour le formulaire adaptatif. Vous pouvez utiliser l’option **[!UICONTROL Chemin du document d’enregistrement]** pour spécifier le nom du fichier de document d’enregistrement et le chemin d’accès du fichier par rapport à la charge utile. Par exemple, le chemin d’accès `/addresschange/DoR.pdf` crée un dossier nommé `addresschange` relatif à la charge utile et place `DoR.pdf` relatif à la charge utile. Vous pouvez également spécifier uniquement `DoR.pdf` pour n’enregistrer que le document d’enregistrement sans créer de hiérarchie de dossiers. Si le workflow est marqué pour le stockage de données externe, utilisez l’option variable et sélectionnez la variable dans la liste des variables disponibles pour le modèle de workflow.
1. Cliquez sur **[!UICONTROL Terminé]**.

   >[!NOTE]
   >
   > En savoir plus sur les [workflows centrés sur Forms d’AEM - Référence des étapes pour automatiser les processus métier](/help/forms/aem-forms-workflow-step-reference.md).

>[!TAB Éditeur universel]

Pour configurer un processus automatisé avec [AEM Workflow](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=fr#extending-aem) pour un formulaire adaptatif créé dans l’éditeur universel, procédez comme suit :

1. Ouvrez le formulaire adaptatif pour le modifier.
1. Cliquez sur l’extension **Modifier les propriétés du formulaire** dans l’éditeur.
La boîte de dialogue **Propriétés du formulaire** s’affiche.

   >[!NOTE]
   >
   > * Si l’icône **Modifier les propriétés de formulaire** ne s’affiche pas dans l’interface de l’éditeur universel, activez l’extension **Modifier les propriétés de formulaire** dans Extension Manager.
   > * Consultez l’article [Caractéristiques des fonctionnalités d’Extension Manager](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions) pour savoir comment activer ou désactiver les extensions dans l’éditeur universel.

1. Cliquez sur l’onglet **Envoi** et sélectionnez l’action d’envoi **[!UICONTROL Appeler un workflow AEM]**.


   ![Configuration de l’action Envoyer un e-mail](/help/forms/assets/invoke-service-ue.png)

1. Sélectionnez le modèle de workflow dans la liste déroulante **[!UICONTROL Modèle de workflow]**.
1. Sélectionnez l’option dans la liste déroulante **[!UICONTROL Stocker le fichier de données à l’aide de]**.

   **Fichier de données** : Il contient les données envoyées au formulaire adaptatif. Vous pouvez utiliser l’option **[!UICONTROL Chemin d’accès au fichier de données]** pour spécifier le nom du fichier et le chemin d’accès du fichier par rapport à la charge utile. Par exemple, le chemin d’accès `/addresschange/data.xml` crée un dossier nommé `addresschange` et le place par rapport à la charge utile. Vous pouvez également spécifier uniquement `data.xml` pour envoyer uniquement les données envoyées sans créer de hiérarchie de dossiers. Si le workflow est marqué pour le stockage de données externe, utilisez l’option variable et sélectionnez la variable dans la liste des variables disponibles pour le modèle de workflow.

1. Sélectionnez l’option dans la liste déroulante **[!UICONTROL Stocker les pièces jointes en utilisant]**.

   **Pièces jointes** : vous pouvez utiliser l’option **[!UICONTROL Chemin d’accès aux pièces jointes]** pour spécifier le nom de dossier dans lequel stocker les pièces jointes chargées dans le formulaire adaptatif. Le dossier est créé par rapport à la payload. Si le workflow est marqué pour le stockage de données externe, utilisez l’option variable et sélectionnez la variable dans la liste des variables disponibles pour le modèle de workflow.

1. Sélectionnez l’option dans la liste déroulante **[!UICONTROL Documents d’enregistrement à l’aide de]**.

   **Document d’enregistrement** : il contient le document d’enregistrement généré pour le formulaire adaptatif. Vous pouvez utiliser l’option **[!UICONTROL Chemin du document d’enregistrement]** pour spécifier le nom du fichier de document d’enregistrement et le chemin d’accès du fichier par rapport à la charge utile. Par exemple, le chemin d’accès `/addresschange/DoR.pdf` crée un dossier nommé `addresschange` relatif à la charge utile et place `DoR.pdf` relatif à la charge utile. Vous pouvez également spécifier uniquement `DoR.pdf` pour n’enregistrer que le document d’enregistrement sans créer de hiérarchie de dossiers. Si le workflow est marqué pour le stockage de données externe, utilisez l’option variable et sélectionnez la variable dans la liste des variables disponibles pour le modèle de workflow.
1. Cliquez sur **[!UICONTROL Terminé]**.

   >[!NOTE]
   >
   > En savoir plus sur les [workflows centrés sur Forms d’AEM - Référence des étapes pour automatiser les processus métier](/help/forms/aem-forms-workflow-step-reference.md).

>[!ENDTABS]

<!--
## Best Practices

* When configuring the **[!UICONTROL Invoke an AEM Workflow]** Submit Action, select the appropriate workflow model that aligns with the desired business process.
* In case, the workflow involves external data storage, be sure to configure the workflow accordingly. It is recommended to set up variables appropriately and in accordance with any external storage requirements. -->

## Articles connexes

{{af-submit-action}}
