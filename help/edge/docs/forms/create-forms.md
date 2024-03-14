---
title: Prise en main d’AEM Forms Edge Delivery Service. Créez un formulaire.
description: Concevez des formes parfaites, vite ! ⚡ Création basée sur des documents de diffusion AEM Forms Edge = vitesse époustouflante et formulaires compatibles avec l’optimisation pour les moteurs de recherche et les utilisateurs plus heureux.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: 0cf881a2-3784-45eb-afe8-3435e5e95cf4
source-git-commit: f4cf79e2cd71a390741987cfcf034e6eed02432d
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 1%

---

# Création d’un formulaire à l’aide d’un bloc Forms adaptatif

>[!VIDEO](https://video.tv.adobe.com/v/3427881?quality=12&learn=on)

AEM Forms Edge Delivery fournit un bloc, appelé Bloc Forms adaptatif, qui vous permet de créer facilement des formulaires pour capturer et stocker les données capturées. Vous pouvez [créer un projet AEM préconfiguré avec le bloc Forms adaptatif](/help/edge/docs/forms/tutorial.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) ou [ajouter le bloc Forms adaptatif à un projet AEM existant ;](/help/edge/docs/forms/tutorial.md#add-adaptive-forms-block-to-your-existing-aem-project).

Ces formulaires envoient directement des données à un fichier Microsoft Excel ou Google Sheets, ce qui vous permet d’utiliser un écosystème dynamique et des API robustes de Google Sheets, Microsoft Excel et Microsoft SharePoint pour traiter facilement les données envoyées ou lancer un processus d’entreprise existant.

![Écosystème de création basé sur les documents](/help/edge/assets/document-based-authoring-workflow-create-form.png)


## Conditions préalables

Avant de commencer, vérifiez que vous avez suivi les étapes suivantes :

* Configurez une [AEM projet à l’aide du standard AEM Forms](/help/edge/docs/forms/tutorial.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) ou [Ajout d’un bloc Forms adaptatif à votre projet AEM existant](/help/edge/docs/forms/tutorial.md#add-adaptive-forms-block-to-your-existing-aem-project) et cloner le référentiel GitHub correspondant sur votre ordinateur local.
Dans ce document, le dossier local de votre projet Edge Delivery Services (EDS) est désigné sous la forme `[EDS Project repository]`.
* Assurez-vous que vous avez accès aux feuilles de calcul Google Sheets ou à Microsoft SharePoint. Pour configurer Microsoft SharePoint en tant que source de contenu, voir [Utilisation de SharePoint](https://www.aem.live/docs/setup-customer-SharePoint).



## Création d’un formulaire

<!-- 

+++ Step 1: Add the Adaptive Forms Block to your Edge Delivery Services (EDS) project.

The Adaptive  empowers users to create forms for an Edge Delivery Service Site. However, this block isn't included in the default AEM boilerplate (used to create an Edge Delivery Services project). To seamlessly integrate the Adaptive Forms Block into your Edge Delivery Services project:

1. **Clone the Adaptive Forms Block repository**: Clone the [Adaptive Forms Block repository](https://github.com/adobe-rnd/form-block) on your local machine. It contains the code to render the form on an EDS webpage. In this document, the local folder of your Forms Block repository is referred as `[Adaptive Forms Block repository]`.
1. **Locate the Adaptive Forms Block Repository:** Access the [Adaptive Forms Block repository]/blocks/src folder and copy its content. 

1. on your local machine and copy the `form` folder. 
1. **Paste the Adaptive Forms Block's code into your EDS Project:**
Navigate to the [EDS Project repository]/blocks/ folder on your local machine and create a 'form' folder. Paste the `[Adaptive Forms Block repository]/blocks/src content`, copied in perevious step to the `[EDS Project repository]/blocks/form` folder.
1. **Commit Changes to GitHub:** Check in the `[EDS Project repository]/blocks/form` folder and its underlying files to your Edge Delivery Services project on GitHub.

After completing these steps, the Adaptive Forms Block is successfully added to your Edge Delivery Services (EDS) project repository on GitHub. You can now create and add forms to a EDS Sites page.
 

**Troubleshooting GitHub build issues**

Ensure a smooth GitHub build process by addressing potential issues:

* **Resolve Module Path Error:**
    If you encounter the error "Unable to resolve path to module "'../../scripts/lib-franklin.js'", navigate to the [EDS Project]/blocks/forms/form.js file. Update the import statement by replacing the lib-franklin.js file with the aem.js file.

* **Handle Linting Errors:**
    Should you come across any linting errors, you can bypass them. Open the [EDS Project]/package.json file and modify the "lint" script from "lint": "npm run lint:js && npm run lint:css" to "lint": "echo 'skipping linting for now'". Save the file and commit the changes to your GitHub project.

+++

-->

+++ Étape 1 : créez un formulaire à l’aide de Microsoft Excel ou de la feuille de calcul Google.

Au lieu de naviguer dans des processus complexes, il est possible d’obtenir facilement un formulaire à l’aide d’une feuille de calcul. Vous pouvez définir les lignes et les colonnes qui constitueront la structure du formulaire. Chaque ligne représente un individu [champ de formulaire](/help/edge/docs/forms/form-components.md#available-components) et les en-têtes de colonne définissent les [propriétés de champ](/help/edge/docs/forms/form-components.md#components-properties).

Prenons l’exemple de la feuille de calcul suivante, dans laquelle les lignes encadrent les champs d’une `enquiry` Les en-têtes de formulaire et de colonne définissent leurs propriétés :

![Feuille de calcul de requête](/help/edge/assets/enquiry-form-spreadsheet.png)

Pour poursuivre la création du formulaire :

1. Accédez à votre dossier de projet Edge Delivery AEM sur Microsoft SharePoint ou Google Drive.

1. Créez un classeur Excel Microsoft ou une feuille de calcul Google n’importe où dans votre répertoire de projet Edge Delivery AEM. Par exemple, créez une feuille de calcul nommée `enquiry` sur le répertoire du projet Edge Delivery d’AEM sur Google Drive.

   ![Exemple de contenu sur Google Drive](/help/edge/assets/upload-sample-files-to-your-content-folder.png)

1. Assurez-vous que la feuille est partagée avec l’utilisateur AEM approprié (par exemple `helix@adobe.com`) [selon les configurations spécifiées pour votre projet.](https://www.aem.live/docs/setup-customer-SharePoint). Octroyez à l’utilisateur l’autorisation de modification de la feuille.

1. Ouvrez la feuille de calcul créée et renommez la feuille par défaut &quot;shared-default&quot;.

   ![renommer la feuille par défaut en &quot;shared-default&quot;](/help/edge/assets/rename-sheet-to-shared-default.png)

1. Pour ajouter les champs du formulaire, insérez les lignes et les en-têtes de colonne dans la feuille &#39;shared-default&#39;. Chaque ligne doit représenter une [champ de formulaire](/help/edge/docs/forms/form-components.md#available-components), avec des en-têtes de colonne définissant le champ correspondant [properties](/help/edge/docs/forms/form-components.md#components-properties).


   Pour un démarrage rapide, pensez à copier le contenu de la variable [Feuille de calcul de requête](https://docs.google.com/spreadsheets/d/196lukD028RDK_evBelkOonPxC7w0l_IiJ-Yx3DvMfNk/edit#gid=0) dans votre feuille de calcul. Après avoir copié le contenu, enregistrez votre feuille de calcul.

   >[!VIDEO](https://video.tv.adobe.com/v/3427468?quality=12&learn=on)


1. Utilisation [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) pour prévisualiser la feuille.

   ![Utilisez AEM Sidekick pour prévisualiser la feuille](/help/edge/assets/preview-form.png)

   Lors de la prévisualisation, les nouveaux onglets du navigateur affichent le contenu de la feuille au format JSON. Veillez à capturer l’URL d’aperçu, car elle est nécessaire pour le rendu du formulaire dans la section suivante. Le format d’URL se présente comme suit :


   ```JSON
       https://<branch>--<repository>--<owner>.hlx.live/<form-path>/<form-file-name>.json
   ```

   * `<branch>` fait référence à la branche de votre référentiel GitHub.
   * `<repository>` indique votre référentiel GitHub.
   * `<owner>` fait référence au nom d’utilisateur de votre compte GitHub qui héberge votre référentiel GitHub.

   Par exemple, si le référentiel de votre projet est nommé &quot;portal&quot;, il se trouve sous le compte &quot;wkndforms&quot; et que vous utilisez la branche &quot;main&quot;, l’URL ressemble à ce qui suit :

   `https://main--portal--wkndforms.hlx.page/enquiry.json`


+++

+++ Étape 2 : prévisualisez le formulaire à l’aide de votre page Edge Delivery Services (EDS).


Jusqu’à présent, vous avez préparé la structure du formulaire. Maintenant, pour prévisualiser le formulaire :

1. Ouvrez votre compte Microsoft SharePoint ou Google Drive et accédez au répertoire de votre projet Edge Delivery AEM.



1. Ouvrez un fichier document (fichier d’index, par exemple) pour incorporer le formulaire. Vous pouvez également créer un document.

1. Accédez à l’emplacement souhaité dans le document où vous avez l’intention d’ajouter le formulaire.

1. Pour créer un bloc de formulaire afin de générer le formulaire. Choisissez Insertion > Tableau, puis créez un tableau d’une colonne et de deux rangées. Nommez le tableau &quot;Formulaire&quot; et collez l’URL d’aperçu dans la deuxième ligne. Assurez-vous que l’URL est formatée en tant que lien hypertexte et non en texte brut, comme illustré ci-dessous :

   | Formulaire |
   |---|
   | [https://main—wefinance—wkndforms.hlx.live/enquiry.json](https://main--wefinance--wkndforms.hlx.live/enquiry.json) |


   ![Ajout d’un bloc Forms adaptatif à une page web](/help/edge/assets/add-adaptive-forms-block.png)

   Ce bloc sert d’espace réservé où le formulaire est incorporé. Dans la deuxième ligne du bloc, ajoutez l’URL d’aperçu de votre `<form>.json` comme lien hypertexte.

   >[!IMPORTANT]
   >
   >
   > Assurez-vous que l’URL est formatée en tant que lien hypertexte plutôt que sous la forme de texte brut.


1. Utilisation [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) pour prévisualiser le document. La page affiche désormais le formulaire. Par exemple, voici le formulaire basé sur le [feuille de calcul d&#39;enquête](https://docs.google.com/spreadsheets/d/196lukD028RDK_evBelkOonPxC7w0l_IiJ-Yx3DvMfNk/edit#gid=0):


   [![Exemple de formulaire EDS](/help/edge/assets/eds-form.png)](https://main--portal--wkndforms.hlx.live/)

   Maintenant, remplissez le formulaire et cliquez sur le bouton d’envoi. Vous rencontrez une erreur, semblable à la suivante, car la feuille de calcul n’est pas encore configurée pour accepter les données.

   ![erreur lors de l’envoi du formulaire](/help/edge/assets/form-error.png)

+++


## Étape suivante

[Préparation de votre feuille de calcul](/help/edge/docs/forms/submit-forms.md) pour commencer à accepter les données lors de l’envoi du formulaire.


## Voir également

{{see-more-forms-eds}}
