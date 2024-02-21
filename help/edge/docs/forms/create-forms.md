---
title: Prise en main d’AEM Forms Edge Delivery Service
description: Concevez des formes parfaites, vite ! ⚡ Création basée sur des documents de diffusion AEM Forms Edge = vitesse époustouflante et formulaires compatibles avec l’optimisation pour les moteurs de recherche et les utilisateurs plus heureux.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 34ba430ae9b40fc3bc675af20bbee2534c44a0c3
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 1%

---


# Création d’un formulaire sur le service de diffusion Edge AEM Forms

A l&#39;ère numérique actuelle, la création de formulaires conviviaux est essentielle pour toute entreprise. AEM Forms Edge Delivery permet de créer des formulaires à l’aide d’outils familiers tels que Word ou Google Docs.

Ces formulaires envoient directement des données à un fichier Microsoft Excel ou Google Sheets, ce qui vous permet d’utiliser un écosystème dynamique et des API robustes de Google Sheets, Microsoft Excel et Microsoft SharePoint pour traiter facilement les données envoyées ou lancer un processus d’entreprise existant.

## Conditions préalables

* Vous disposez d’un compte GitHub.
* Vous avez accès à Google Sheets ou Microsoft SharePoint.
* Vous comprenez les concepts de base de Git, HTML, CSS et JavaScript.
* Vous avez installé Node et NPM pour le développement local.

## Avant de commencer

* Configurez et clonez votre projet Edge Delivery Service (EDS). Voir [tutoriel pour les développeurs](https://www.aem.live/developer/tutorial) pour plus d’informations.
* Cloner le [Référentiel de bloc Forms](https://github.com/adobe/afb). Il comprend le bloc Form nécessaire pour générer le formulaire.

![Prise en main d’Edge Delivery Forms](/help/edge/assets/getting-started-with-eds-forms.png)


## Étape 1 : Ajout du bloc Form à votre projet Edge Delivery Service (EDS) {#add-forms-block-to-an-eds-project}

AEM Forms Edge Delivery comprend un bloc de formulaire qui permet de créer facilement des formulaires pour capturer et stocker les données capturées. Pour inclure le bloc Form à votre projet Edge Delivery Service :

1. Accédez au `blocks` dossier de votre projet Edge Delivery Service (EDS) sur votre environnement de développement local.


   ```Shell
   cd [EDS Project folder]/blocks
   ```

1. Créez un dossier nommé `form` sous le `blocks` répertoire . Par exemple, sous le répertoire du projet EDS nommé `Portal`, créez un dossier nommé `form`.

   ```Shell
   mkdir form
   ```


1. Ajoutez la variable [Bloc Forms](https://github.com/adobe/afb/tree/main/blocks/form) dans le dossier &quot;form&quot;.

   ```shell
   cp -R <source:path of the form block> <destination: path of the form folder created in the previous step>
   ```

   **Par exemple :**


   ```shell
   cp -R ../../afb/blocks/form ../../fantastic-computing-machine/blocks 
   ```



1. Archivez le dossier &quot;form&quot; et les fichiers sous-jacents à votre projet Edge Delivery Service sur GitHub.

   ```Shell
   cd ..
   git add .
   git commit -m "Added form block"
   git push origin
   ```

   Le bloc Formulaire est ajouté à votre projet EDS. Vous pouvez maintenant créer un formulaire et l’ajouter à votre site.

   >[!NOTE]
   >
   > * Si vous rencontrez une erreur &quot;Impossible de résoudre le chemin d’accès au module &quot;&#39;../../scripts/lib-franklin.js&#39;&quot;, ouvrez la `[EDS Project]/blocks/forms/form.js` fichier . Dans l’instruction d’importation, remplacez la variable `franklin-lib.js` avec le fichier `aem.js` fichier .
   > * Si vous rencontrez des erreurs de linting, n&#39;hésitez pas à les ignorer. Pour contourner les contrôles d’alignement, ouvrez le `[EDS Project]\package.json` et mettre à jour le script &quot;lint&quot; à partir de `"lint": "npm run lint:js && npm run lint:css"` to `"lint": "echo 'skipping linting for now'"`. Enregistrez le fichier et validez-le dans votre projet GitHub.

## Étape 2 : création d’un formulaire à l’aide de Microsoft Excel ou de Google Sheet

Au lieu de processus complexes, vous pouvez facilement créer un formulaire à l’aide d’une feuille de calcul. Vous pouvez commencer par ajouter les lignes et les en-têtes de colonne à une feuille de calcul. Chaque ligne définit un champ de formulaire et chaque en-tête de colonne définit les propriétés des champs de formulaire correspondants.

Par exemple, dans la feuille de calcul suivante, les lignes définissent les champs d’une `contact us` L’en-tête de formulaire et de colonne définit les propriétés des champs correspondants.

![contactez-nous pour la feuille de calcul](/help/edge/assets/contact-us-form-spreadsheet.png)

Pour créer un formulaire :

1. Ouvrez votre dossier de projet de diffusion Edge AEM sur Microsoft SharePoint ou Google Drive.

1. Créez un classeur Excel Microsoft ou une feuille de calcul Google n’importe où sous votre répertoire de projet Edge Delivery AEM. Par exemple, créez une feuille de calcul nommée `contact-us` sur le répertoire du projet Edge Delivery d’AEM sur Google Drive.

1. Assurez-vous que la feuille est partagée avec AEM utilisateur (par exemple `helix@adobe.com`) [configuré pour votre projet](https://www.aem.live/docs/setup-customer-sharepoint) et l’utilisateur dispose d’autorisations de modification pour la feuille.

1. Ouvrez la feuille de calcul que vous avez créée et remplacez le nom de la feuille par défaut par &quot;shared-default&quot;.

   ![renommer la feuille par défaut en &quot;shared-default&quot;](/help/edge/assets/rename-sheet-to-shared-default.png)

1. Pour ajouter les champs du formulaire, ajoutez les rangées et les en-têtes de colonne au `shared-default` , où chaque ligne définit un champ de formulaire et chaque en-tête de colonne définit [properties](/help/edge/docs/forms/eds-form-field-properties)) des champs de formulaire correspondants.

   Pour démarrer rapidement, vous pouvez copier le contenu de la variable [contactez-nous pour la feuille de calcul](https://docs.google.com/spreadsheets/d/12jvYjo1a3GOV30IqPY6_7YaCQtUmzWpFhoiOHDcjB28/edit?usp=drive_link) à votre feuille de calcul.

   >[!VIDEO](https://video.tv.adobe.com/v/3427468?quality=12&learn=on)

1. Utilisation [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) pour prévisualiser et publier la feuille.

   ![Utilisez AEM Sidekick pour prévisualiser et publier la feuille.](/help/edge/assets/preview-form.png)

   Lors de la prévisualisation et de la publication, le navigateur ouvre de nouveaux onglets qui affichent le contenu de la feuille au format JSON. Veillez à prendre note de l’URL active, car elle est nécessaire pour effectuer le rendu du formulaire ultérieurement.

   Le format de l’URL est:

   ```JSON
   https://<branch>--<repository>--<owner>.hlx.live/<form>.json
   
   For example, https://main--portal--wkndforms.hlx.live/contact-us.json
   ```



## Étape 3 : aperçu du formulaire à l’aide de votre page Edge Delivery Service (EDS)

Jusqu’à présent, vous avez activé le bloc de formulaire pour votre projet EDS et préparé la structure du formulaire. Maintenant, pour prévisualiser le formulaire :

1. Accédez à votre répertoire de projet Edge Delivery AEM sur Microsoft SharePoint ou Google Drive.

1. Créez ou ouvrez un fichier de document pour héberger le formulaire. Par exemple, ouvrez le fichier d’index.

1. Accédez à l’emplacement souhaité dans le document où vous souhaitez ajouter le formulaire.

1. Ajoutez au fichier un bloc nommé &quot;Formulaire&quot;, similaire à celui affiché ci-dessous.

   ![](/help/edge/assets/form-block-in-sites-page-example.png)

   Sur la deuxième ligne, insérez l’URL que vous avez notée dans la section précédente sous la forme d’un lien hypertexte. Vous pouvez utiliser l’URL de prévisualisation (URL de page) ou l’URL de publication (.live). L’URL d’aperçu peut être utilisée lors de la création ou du test du formulaire et de l’URL de publication en vue de la production.

   >[!IMPORTANT]
   >
   >
   > Assurez-vous que l’URL n’est pas mentionnée en tant que texte brut. Il doit être ajouté en tant que lien hypertexte.

1. Utilisation [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) pour prévisualiser la page. La page affiche désormais le formulaire. Par exemple, voici le formulaire basé sur le [contactez-nous pour la feuille de calcul](https://docs.google.com/spreadsheets/d/12jvYjo1a3GOV30IqPY6_7YaCQtUmzWpFhoiOHDcjB28/edit?usp=drive_link):


   ![Exemple de formulaire EDS](/help/edge/assets/eds-form.png)

   Maintenant, remplissez le formulaire et cliquez sur le bouton d’envoi. Vous rencontrez une erreur, semblable à la suivante, car la feuille de calcul n’est pas encore configurée pour accepter les données.

   ![erreur lors de l’envoi du formulaire](/help/edge/assets/form-error.png)

## Étape suivante

L’étape suivante consiste à [préparer votre feuille de calcul pour accepter les données ;](/help/edge/docs/forms/submit-forms.md).



## En savoir plus

* [Propriétés des champs de formulaire](/help/edge/docs/forms/eds-form-field-properties)
* [Créer et prévisualiser un formulaire](/help/edge/docs/forms/create-forms.md)
* [Activer le formulaire pour envoyer des données](/help/edge/docs/forms/submit-forms.md)
* [Publier un formulaire sur la page de sites](/help/edge/docs/forms/publish-eds-forms.md)
* [Ajouter des validations à des champs de formulaire](/help/edge/docs/forms/validate-forms.md)
* [Modifier les thèmes et le style du formulaire](/help/edge/docs/forms/style-theme-forms.md)
