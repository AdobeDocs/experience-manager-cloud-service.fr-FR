---
title: Workflow de soumission pour Associate UI — IC Generate PDF Output
description: Découvrez comment fonctionnent l’envoi et le workflow pour l’interface utilisateur associée, et suivez un exemple de workflow qui génère PDF à partir du JSON de communication interactive (IC).
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
exl-id: 9d8a33e4-e206-48e6-9daf-b15feb9c67a3
source-git-commit: 53ff71c82d35b9ec9b20b521ef469d3f0abd79df
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 1%

---

# Workflow d’envoi pour l’interface utilisateur associée


Cet article explique comment fonctionnent l’envoi et le workflow lorsque vous activez un workflow pour l’interface utilisateur associée. Il explique ensuite comment configurer un workflow d’envoi. La présentation utilise la génération d’un PDF à partir de la payload de communication interactive (IC) comme exemple ; vous pouvez adapter les étapes à d’autres types de workflow.

<!--
## Submission and workflow behavior {#submission-and-workflow-behavior}

When you enable **Configure Workflow for Update** for an Associate UI, submissions from the Associate UI can trigger an AEM workflow. The following explains where workflows run, who uses which environment, and how to plan for data and access.

### Where workflows run

AEM workflows always run on the **Author** instance. It does not matter whether the person submitting is an author or an associate—the workflow runs on Author. Plan your user groups and where you store workflow data with this in mind.

### Where associates use the Associate UI

Customer-facing associates use the Associate UI on the **Publish** instance only. You publish the Interactive Communication and expose the Associate UI through your Publish environment (for example, via your application or dispatcher). Associates do not use the Author instance. For step-by-step integration and how to invoke the Associate UI on the Publish instance, see [Integrate Associate UI in Your Application](/help/forms/interactive-communication/invoke-associate-ui.md).

### When an author submits from the Author instance

Authors can open the Associate UI on the Author instance—for example, to test the Interactive Communication or to submit on behalf of a customer. When they submit, the request is handled on Author and the workflow runs there. For this to work, the author must be in both **forms-associates** (to access the Associate UI) and **workflow-users** (to run the workflow).

### When an associate submits from the Publish instance

Associates open the Associate UI on the Publish instance, using the integration you set up. When they submit, the submission is sent to the Author instance and the workflow runs on Author. Associates sign in on Publish (for example, via [Microsoft Entra ID](https://www.microsoft.com/en-us/security/business/identity-access/microsoft-entra-id)) and do not need access to Author. To set up how associates open the Associate UI on Publish, see [Integrate Associate UI in Your Application](/help/forms/interactive-communication/invoke-associate-ui.md).
-->

## Configuration d’un workflow d’envoi

Les étapes suivantes indiquent comment créer un workflow qui s’exécute lorsque les utilisateurs effectuent des envois à partir de l’interface utilisateur associée. Dans cet exemple, nous utilisons **rendering de l’IC vers PDF** avec l’étape prête à l’emploi **IC Render PDF Output**. Lorsqu’un utilisateur effectue un envoi à partir de l’interface utilisateur associée, la payload est envoyée au workflow ; cette étape utilise le **communicationDom** (IC-JSON) de la payload pour produire le PDF.

### Structure de la payload

Le workflow reçoit une payload JSON. Le champ **communicationDom** contient l’IC-JSON utilisé pour la génération de PDF. L’étape **IC Render PDF Output** l’utilise comme entrée de modèle.

| Champ | Description |
|-------|-------------|
| communicationDom | Génération d’IC-JSON pour PDF |
| auditMetadata | Informations d&#39;audit |
| submitData | Données de formulaire envoyées (JSON) |
| prefillData | Données de préremplissage (JSON) |
| referer, cookies, queryString, clientIP, userAgent, formSubmitter | Demander des métadonnées |

### Créer un modèle de workflow

1. **De base :** créez un modèle de processus (par exemple, ajoutez un processus en tant que **pdfrenderworkflow**).

   ![Onglet De base du modèle de workflow](/help/forms/assets/associate-ui-add-workflow.png)

1. **Variables :** ajoutez des variables qui correspondent à la payload et à l’étape : **communicationDom** (JSON), **auditMetadata** (JSON), **outputDocument** (Document).

   ![Variables de workflow](/help/forms/assets/associate-ui-add-variables.png)

1. **Étape :** ajoutez l’étape **IC Render PDF Output**.
   ![Ajouter une étape de workflow](/help/forms/assets/associate-ui-add-step.png)

1. Dans son onglet **Entrée**, définissez **Sélectionner le modèle (JsonObject)** sur **Variable** → **communicationDom**. Enregistrez l’étape et le modèle.

   ![IC Render PDF Output — Onglet Entrée](/help/forms/assets/associate-ui-input-variable.png)

1. Dans son onglet **Output**, définissez **Sélectionner le modèle (JsonObject)** sur **Variable** → **communicationDom**. Enregistrez l’étape et le modèle.

   ![Variables de workflow et zone de travail](/help/forms/assets/assocaite-ui-output-variable.png)

### Câblage du workflow à l’interface utilisateur associée

Dans [Activer et configurer l’interface utilisateur associée](/help/forms/interactive-communication/enable-configure-associate-ui.md), activez la vue associée et dans **Workflow** définissez **Configurer le workflow pour la mise à jour** sur Activé et sélectionnez ce modèle de workflow. Publiez l’IC et [intégrez l’interface utilisateur associée](/help/forms/interactive-communication/invoke-associate-ui.md) afin que les envois déclenchent ce workflow.

![Paramètres de communication interactive - Configuration du workflow pour l’interface utilisateur associée](/help/forms/assets/associate-ui-configure-workflow.png)

Lorsque l’option **Externaliser le stockage des données de workflow** est activée, configurez l’externaliseur afin que les données de workflow soient stockées dans votre stockage externe (par exemple, Azure). Voir [Externalisation des données de workflow](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/forms/create-aem-workflow/externalize-workflow.html?lang=fr).

## Voir également

- [Associer l’interface utilisateur dans l’éditeur de communication interactive](/help/forms/interactive-communication/associate-ui-in-interactive-communication-editor.md)
- [Activer et configurer l’interface utilisateur associée pour les communications interactives](/help/forms/interactive-communication/enable-configure-associate-ui.md)
- [Intégrer l’interface utilisateur associée à votre application](/help/forms/interactive-communication/invoke-associate-ui.md)
- [Externaliser les données de workflow](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/forms/create-aem-workflow/externalize-workflow.html?lang=fr)

