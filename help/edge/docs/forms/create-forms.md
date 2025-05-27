---
title: Créer un formulaire à l’aide du bloc de formulaires adaptatifs
description: Commencer avec Edge Delivery Services pour AEM Forms. Créer rapidement des formulaires parfaits. Création basée sur des documents de formulaires AEM Forms Edge Delivery = vitesse époustouflante et formulaires adaptés au SEO pour des utilisateurs et utilisatrices plus heureux.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 0cf881a2-3784-45eb-afe8-3435e5e95cf4
source-git-commit: efd4fbb38724632865d87b80827611899e2c6d1f
workflow-type: ht
source-wordcount: '784'
ht-degree: 100%

---

# Créer un formulaire à l’aide du bloc de formulaires adaptatifs

>[!VIDEO](https://video.tv.adobe.com/v/3427881?quality=12&learn=on)

AEM Forms Edge Delivery fournit un bloc, appelé bloc de formulaires adaptatifs, qui vous permet de créer facilement des formulaires pour capturer et stocker les données capturées. Vous pouvez [créer un projet AEM préconfiguré avec le bloc de formulaires adaptatifs](/help/edge/docs/forms/tutorial.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) ou [ajouter le bloc de formulaires adaptatifs à un projet AEM existant](/help/edge/docs/forms/tutorial.md#add-adaptive-forms-block-to-your-existing-aem-project).

Ces formulaires envoient directement les données vers un fichier Microsoft Excel ou Google Sheets, ce qui vous permet d’utiliser l’écosystème dynamique et les API robustes de Google Sheets, Microsoft Excel et Microsoft SharePoint pour traiter facilement les données envoyées ou pour démarrer un workflow d’entreprise existant.

![Écosystème de création basé sur des documents](/help/edge/assets/document-based-authoring-workflow-create-form.png)


## Prérequis

Avant de commencer, vérifiez que vous avez déjà effectué les étapes suivantes :

* Vous avez configuré un [projet AEM à l’aide du modèle standard AEM Forms](/help/edge/docs/forms/tutorial.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) ou [ajouté un bloc de formulaires adaptatifs à votre projet AEM existant](/help/edge/docs/forms/tutorial.md#add-adaptive-forms-block-to-your-existing-aem-project) et cloné le référentiel GitHub correspondant sur votre ordinateur local.
<!--In this document, the local folder of your Edge Delivery Services (EDS) project is referred as `[EDS Project repository]`.  -->
* Assurez-vous d’avoir accès à Google Sheets ou à Microsoft SharePoint. Pour configurer Microsoft SharePoint en tant que source de contenu, voir [Utilisation de SharePoint](https://www.aem.live/docs/setup-customer-sharepoint).



## Créer un formulaire

<!--
+++ Step 1: Add the Adaptive Forms Block to your Edge Delivery Services (EDS) project.

The Adaptive  empowers users to create forms for an Edge Delivery Service Site. However, this block isn't included in the default AEM boilerplate (used to create an Edge Delivery Services project). To seamlessly integrate the Adaptive Forms Block into your Edge Delivery Services project:

1. **Clone the Adaptive Forms Block repository**: Clone the [Adaptive Forms Block repository](https://github.com/adobe-rnd/form-block) on your local machine. It contains the code to render the form on an EDS webpage. In this document, the local folder of your Forms Block repository is referred as `[Adaptive Forms Block repository]`.
2. **Locate the Adaptive Forms Block Repository:** Access the [Adaptive Forms Block repository]/blocks/src folder and copy its content. 

3. on your local machine and copy the `form` folder. 
4. **Paste the Adaptive Forms Block's code into your EDS Project:**
Navigate to the [EDS Project repository]/blocks/ folder on your local machine and create a 'form' folder. Paste the `[Adaptive Forms Block repository]/blocks/src content`, copied in perevious step to the `[EDS Project repository]/blocks/form` folder.
1. **Commit Changes to GitHub:** Check in the `[EDS Project repository]/blocks/form` folder and its underlying files to your Edge Delivery Services project on GitHub.

After completing these steps, the Adaptive Forms Block is successfully added to your Edge Delivery Services (EDS) project repository on GitHub. You can now create and add forms to a EDS Sites page.
 

**Troubleshooting GitHub build issues**

Ensure a smooth GitHub build process by addressing potential issues:

* **Resolve Module Path Error:**
    If you encounter the error "Unable to resolve path to module "'../../scripts/lib-franklin.js'", navigate to the [EDS Project]/blocks/forms/form.js file. Update the import statement by replacing the lib-franklin.js file with the aem.js file.

* **Handle Linting Errors:**
    Should you come across any linting errors, you can bypass them. Open the [EDS Project]/package.json file and modify the "lint" script from "lint": "npm run lint:js && npm run lint:css" to "lint": "echo 'skipping linting for now'". Save the file and commit the changes to your GitHub project. -->

+++ Étape 1 : créez un formulaire à l’aide de Microsoft Excel ou Google Sheets.

Plutôt que de recourir à des processus complexes, il est possible de créer facilement un formulaire à l’aide d’une feuille de calcul. Vous pouvez définir les lignes et les colonnes qui constitueront la structure du formulaire. Chaque ligne représente un [champ de formulaire](/help/edge/docs/forms/form-components.md#available-components) individuel et les en-têtes de colonne définissent les [propriétés du champ](/help/edge/docs/forms/form-components.md#components-properties) correspondantes.

Prenons l’exemple de la feuille de calcul suivante, dans laquelle les lignes correspondent aux champs d’une feuille de calcul [enquiry](/help/edge/assets/enquiry.xlsx) et les en-têtes de colonne définissent leurs propriétés :

![Feuille de calcul de demande](/help/edge/assets/enquiry-form-spreadsheet.png)

Pour poursuivre la création du formulaire :

1. Accédez au dossier de votre projet AEM Edge Delivery sur Microsoft SharePoint ou Google Drive.

1. Créez un classeur Microsoft Excel ou une feuille Google Sheets n’importe où dans le répertoire de votre projet AEM Edge Delivery. Par exemple, créez une feuille de calcul nommée `enquiry` dans le répertoire du projet AEM Edge Delivery sur Google Drive.

   <!-- ![Sample Content on Google Drive](/help/edge/assets/upload-sample-files-to-your-content-folder.png)-->

1. Assurez-vous que la feuille est partagée avec la personne appropriée utilisant AEM (par exemple, `forms@adobe.com`) [conformément aux configurations spécifiées pour votre projet](https://www.aem.live/docs/setup-customer-sharepoint). Octroyez à l’utilisateur ou l’utilisatrice l’autorisation de modification de la feuille.

1. Ouvrez la feuille de calcul créée et renommez la feuille par défaut en « shared-aem ».

   ![Renommage de la feuille par défaut en « shared-default »](/help/edge/assets/rename-sheet-to-shared-default.png)

1. Pour ajouter les champs du formulaire, insérez les lignes et les en-têtes de colonne dans la feuille « shared-aem ». Chaque ligne doit représenter un [champ de formulaire](/help/edge/docs/forms/form-components.md#available-components), avec des en-têtes de colonne définissant les [propriétés](/help/edge/docs/forms/form-components.md#components-properties) du champ correspondantes.


   Pour un démarrage rapide, pensez à copier le contenu de la [feuille de calcul de demande](/help/edge/assets/enquiry.xlsx) dans votre feuille de calcul. Après avoir copié le contenu, enregistrez votre feuille de calcul.

   >[!VIDEO](https://video.tv.adobe.com/v/3427468?quality=12&learn=on)


1. Utilisez [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) pour prévisualiser la feuille.

   ![Utilisation d’AEM Sidekick pour prévisualiser la feuille](/help/edge/assets/preview-form.png)

   Lors de la prévisualisation, de nouveaux onglets de navigateur affichent le contenu de la feuille au format JSON. Veillez à noter l’URL d’aperçu, car elle sera nécessaire pour le rendu du formulaire dans la section suivante. Le format de l’URL se présente comme suit :


   ```JSON
       https://<branch>--<repository>--<owner>.aem.live/<form-path>/<form-file-name>.json
   ```

   * `<branch>` fait référence à la branche de votre référentiel GitHub.
   * `<repository>` indique votre référentiel GitHub.
   * `<owner>` fait référence au nom d’utilisateur ou d’utilisatrice de votre compte GitHub qui héberge votre référentiel GitHub.

   Par exemple, si le référentiel de votre projet est nommé « wefinance », qu’il se trouve dans le compte « wkndform » et que vous utilisez la branche « main », l’URL ressemble à ceci :

`https://main--wefinance--wkndform.aem.page/enquiry.json`
&lt;!—(https://main--wefinance--wkndform.aem.page/enquiry.json)-->


+++

+++ Étape 2 : prévisualisez le formulaire à l’aide de votre page Edge Delivery Services.


À ce stade, vous avez préparé la structure du formulaire. Maintenant, pour prévisualiser le formulaire :

1. Ouvrez votre compte Microsoft SharePoint ou votre compte Google Drive et accédez au répertoire de votre projet AEM Edge Delivery.



1. Ouvrez un fichier document (fichier d’index, par exemple) pour incorporer le formulaire. Vous pouvez également [créer un document](/help/edge/assets/enquiry-form.docx).

1. Accédez à l’emplacement souhaité dans le document où vous avez l’intention d’ajouter le formulaire.

1. Pour créer un bloc de formulaire afin d’afficher le formulaire. Sélectionnez Insérer > Tableau, puis créez un tableau à une colonne et deux lignes. Nommez le tableau « Form » (formulaire) et collez l’URL d’aperçu dans la deuxième ligne. Assurez-vous que l’URL se présente sous la forme d’un lien hypertexte et non de texte brut, comme illustré ci-dessous :

   | Formulaire |
   |---|
   | `https://main--wefinance--wkndform.aem.live/enquiry.json` |


   ![Ajout d’un bloc Formulaires adaptatifs à votre page web](/help/edge/assets/enquiry-doc-to-embed-form.png)

   Ce bloc sert d’espace réservé à l’emplacement où le formulaire est incorporé. Dans la deuxième ligne du bloc, ajoutez l’URL d’aperçu de votre fichier `<form>.json` sous la forme d’un lien hypertexte.

   >[!IMPORTANT]
   >
   >
   > Assurez-vous que l’URL est formatée en tant que lien hypertexte et non sous forme de texte brut.


1. Utilisez [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) pour prévisualiser le document. La page affiche désormais le formulaire. Par exemple, voici le formulaire basé sur la [feuille de calcul de demande](/help/edge/assets/enquiry-form.docx) :


   [![Exemple de formulaire EDS](/help/edge/assets/updated-form.png)](https://main--wefinance--wkndform.aem.page/enquiry-form)

   Remplissez maintenant le formulaire et cliquez sur le bouton d’envoi. Une erreur semblable à celle ci-dessous s’affiche, car la feuille de calcul n’est pas encore configurée pour accepter les données.

   ![Erreur lors de l’envoi du formulaire](/help/edge/assets/form-error.png)

+++


## Étape suivante

[Préparez votre feuille de calcul](/help/edge/docs/forms/submit-forms.md) pour commencer à accepter les données lors de l’envoi du formulaire.


## Voir également

{{see-more-forms-eds}}
