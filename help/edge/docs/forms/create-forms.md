---
title: Prise en main d’AEM Forms Edge Delivery Service
description: Concevez des formes parfaites, vite ! ⚡ Création basée sur des documents de diffusion AEM Forms Edge = vitesse époustouflante et formulaires compatibles avec l’optimisation pour les moteurs de recherche et les utilisateurs plus heureux.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: f37a99cd5cbfb745cb591e3be2a46a5f52139cb2
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 1%

---


# Création d’un formulaire sur le service de diffusion Edge AEM Forms

A l&#39;ère numérique actuelle, la création de formulaires conviviaux est essentielle pour toute entreprise. AEM Forms Edge Delivery permet de créer des formulaires à l’aide d’outils familiers tels que Word ou Google Docs.

Ces formulaires envoient directement des données à un fichier Microsoft Excel ou Google Sheets, ce qui vous permet d’utiliser un écosystème dynamique et des API robustes de Google Sheets, Microsoft Excel et Microsoft SharePoint pour traiter facilement les données envoyées ou lancer un processus d’entreprise existant.

## Conditions préalables

* Vous avez un compte Github.
* Vous avez accès à Google Sheets ou Microsoft SharePoint.
* Vous comprenez les concepts de base de Git, HTML, CSS et JavaScript.
* Vous avez installé Node et NPM pour le développement local.

## Avant de commencer

* Configurez et clonez votre projet de service de diffusion Edge (EDS). Voir [tutoriel pour les développeurs](https://www.aem.live/developer/tutorial) pour plus d’informations.
* Cloner le [Référentiel de bloc Forms](https://github.com/adobe/afb). Il comprend le bloc Form nécessaire pour générer le formulaire.

![Prise en main d’Edge Delivery Forms](/help/edge/assets/getting-started-with-eds-forms.png)

## Ajoutez le bloc Form à votre projet Edge Delivery Service (EDS). {#add-forms-block-to-an-eds-project}

AEM Forms Edge Delivery comprend un bloc de formulaire qui permet de créer facilement des formulaires pour capturer et stocker les données capturées. Pour inclure le bloc Form à votre projet Edge Delivery Service :

1. Accédez au dossier de projet du service de diffusion Edge (EDS) dans votre environnement de développement local.


   ```Shell
   cd [EDS Project folder]
   ```

1. Créez un dossier nommé `form` sous le répertoire du projet EDS. Par exemple, sous le répertoire du projet EDS nommé `Portal`, créez un dossier nommé `form`.

   ```Shell
   mkdir form
   ```


1. Ajoutez la variable [Bloc Forms](https://github.com/adobe/afb/tree/main/blocks/form) dans le dossier &quot;form&quot;.

   ```shell
   cp -R <source:path of the form block> <destination: path of the form folder created in the previous step>
   
   For example
   
   cp -R Documents/afb/blocks/form Documents/portal/blocks/
   ```

1. Archivez le dossier &quot;form&quot; et les fichiers sous-jacents à votre projet Edge Delivery Service sur GitHub.

   ```Shell
   git add .
   git commit -m "Added form block"
   git push origin
   ```

   Vous êtes maintenant prêt à effectuer le rendu d’un formulaire EDS.

   >[!NOTE]
   >
   > * Si la génération de votre projet de requête de tirage/flux échoue et que vous rencontrez une erreur liée à l’importation de la variable `franklin-lib.js` , mettez à jour l’instruction d’importation pour référencer le fichier `aem.js` au lieu du fichier `franklin-lib.js` fichier .
   > * Si vous rencontrez des erreurs de linting, n&#39;hésitez pas à les ignorer. Pour contourner les vérifications de liaison, accédez au fichier package.json et mettez à jour le script &quot;lint&quot; à partir de `"lint": "npm run lint:js && npm run lint:css"` to `"lint": "echo 'skipping linting for now'"`. Ensuite, validez les modifications apportées au fichier package.json.

## Créer un formulaire à l’aide de Microsoft Excel ou d’une feuille de calcul Google {#create-a-form-for-an-eds-project}

Permet aux développeurs de sites web de créer des formulaires et de choisir les informations à collecter auprès des visiteurs du site web. Au lieu de processus complexes, les auteurs peuvent facilement configurer un formulaire à l’aide d’une feuille de calcul. Ils doivent ajouter les en-têtes de colonne de droite, puis utiliser un bloc de formulaire pour l’afficher sur le site web sans problème. Pour créer un formulaire :

1. Créez un classeur Excel Microsoft ou une feuille de calcul Google n’importe où sous votre répertoire de projet Edge Delivery AEM sur Microsoft SharePoint ou Google Drive.

1. Assurez-vous que l’utilisateur AEM (par exemple `helix@adobe.com`) configuré pour votre projet dispose d’autorisations de modification pour la feuille.

1. Ouvrez le classeur que vous avez créé et remplacez le nom de la feuille par défaut par &quot;shared-default&quot;.

   ![renommer la feuille par défaut en &quot;shared-default&quot;](/help/edge/assets/rename-sheet-to-helix-default.png)

1. Copiez le contenu de la [contactez-nous pour la feuille de calcul](https://docs.google.com/spreadsheets/d/12jvYjo1a3GOV30IqPY6_7YaCQtUmzWpFhoiOHDcjB28/edit?usp=drive_link) à votre propre feuille de calcul.

   ![contactez-nous pour la feuille de calcul](/help/edge/assets/contact-us-form-spreadsheet.png)

1. Utilisation [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) pour prévisualiser et publier la feuille.

   Lors de la prévisualisation et de la publication, le navigateur ouvre de nouveaux onglets qui affichent le contenu de la feuille au format JSON. Veillez à prendre note de l’URL active, car elle est nécessaire pour effectuer le rendu du formulaire ultérieurement.

   Le format de l’URL est:

   ```shell
   https://<branch>--<repository>--<owner>.hlx.live/<form>.json
   
   For example, https://main--portal--wkndforms.hlx.live/contact-us.json
   ```

## Prévisualisez le formulaire à l’aide de votre page Edge Delivery Service (EDS). {#add-a-form-to-your-eds-page}

Jusqu’à présent, vous avez activé le bloc de formulaire pour votre projet EDS et préparé la structure du formulaire. Maintenant, pour inclure le formulaire à votre page EDS et le rendre :

1. Accédez à votre répertoire de projet Edge Delivery AEM sur Microsoft SharePoint ou Google Drive.

1. Pour ajouter le formulaire à une page, ouvrez le fichier de document correspondant. Par exemple, ouvrez le fichier d’index.

1. Accédez à l’emplacement souhaité dans le document où vous souhaitez ajouter le formulaire.

1. Ajoutez au fichier un bloc nommé &quot;Formulaire&quot;, similaire à celui affiché ci-dessous.

   ![](/help/edge/assets/form-block-in-sites-page-example.png)

   Sur la deuxième ligne, insérez l’URL que vous avez notée dans la section précédente sous la forme d’un lien hypertexte.

1. Utilisation [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) pour prévisualiser et publier la page. Le formulaire est rendu.

   Par exemple, voici le formulaire basé sur le [contactez-nous pour la feuille de calcul](https://docs.google.com/spreadsheets/d/12jvYjo1a3GOV30IqPY6_7YaCQtUmzWpFhoiOHDcjB28/edit?usp=drive_link):


   ![contactez-nous (formulaire EDS)](/help/edge/assets/eds-form.png)

   Le bloc de formulaire affiche le formulaire, mais il n’est pas encore prêt à accepter les données. Lorsque vous cliquez sur le bouton Envoyer, une erreur similaire à celle-ci s’affiche :

   ![erreur lors de l’envoi du formulaire](/help/edge/assets/form-error.png)

   [Préparer votre feuille pour accepter les données](/help/edge/docs/forms/submit-forms.md). Vous pouvez envoyer les données à la feuille après les avoir préparées pour accepter les données.


## En savoir plus

* [Créer et prévisualiser un formulaire](/help/edge/docs/forms/create-forms.md)
* [Activer le formulaire pour envoyer des données](/help/edge/docs/forms/submit-forms.md)
* [Publier un formulaire sur la page de sites](/help/edge/docs/forms/publish-eds-forms.md)
* [Ajouter des validations à des champs de formulaire](/help/edge/docs/forms/validate-forms.md)
* [Modifier les thèmes et le style du formulaire](/help/edge/docs/forms/style-theme-forms.md)