---
title: Prise en main d’AEM Forms Edge Delivery Service. Créez un formulaire.
description: Concevez des formes parfaites, vite ! ⚡ Création basée sur des documents de diffusion AEM Forms Edge = vitesse époustouflante et formulaires compatibles avec l’optimisation pour les moteurs de recherche et les utilisateurs plus heureux.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: e2970c7a141025222c6b119787142e7c39d453af
workflow-type: tm+mt
source-wordcount: '1147'
ht-degree: 1%

---


# Créer un formulaire à l’aide d’un bloc de formulaire adaptatif

A l&#39;ère numérique actuelle, la création de formulaires conviviaux est essentielle pour toute entreprise. AEM Forms Edge Delivery permet de créer des formulaires à l’aide d’outils familiers tels que Word ou Google Docs.

Ces formulaires envoient directement des données à un fichier Microsoft Excel ou Google Sheets, ce qui vous permet d’utiliser un écosystème dynamique et des API robustes de Google Sheets, Microsoft Excel et Microsoft SharePoint pour traiter facilement les données envoyées ou lancer un processus d’entreprise existant.

AEM Forms Edge Delivery fournit un bloc, appelé Bloc de formulaire adaptatif, qui vous permet de créer facilement des formulaires pour capturer et stocker les données capturées. Vous pouvez inclure le bloc de formulaire adaptatif dans votre projet AEM EDS pour commencer à créer un formulaire. C’est parti !


## Conditions préalables

Avant de commencer, vérifiez que vous avez suivi les étapes suivantes :

* Configurez le projet GitHub du service de diffusion Edge (EDS) à l’aide AEM standard et clonez le référentiel GitHub correspondant sur votre ordinateur local. Voir [tutoriel pour les développeurs](https://www.aem.live/developer/tutorial) pour plus d’informations. Dans ce document, le dossier local de votre projet Edge Delivery Service (EDS) est appelé `[EDS Project repository]` .
* Assurez-vous que vous avez accès aux feuilles de calcul Google Sheets ou à Microsoft SharePoint. Pour configurer Microsoft SharePoint en tant que source de contenu, voir [Utilisation de SharePoint](https://www.aem.live/docs/setup-customer-sharepoint)



## Création d’un formulaire

+++ Étape 1 : ajoutez le bloc Formulaire adaptatif à votre projet Edge Delivery Service (EDS).

L’outil adaptatif permet aux utilisateurs de créer des formulaires pour un site de service de diffusion Edge. Cependant, ce bloc n’est pas inclus dans le standard d’AEM par défaut (utilisé pour créer un projet de service de diffusion Edge). Pour intégrer de manière transparente le bloc Formulaire adaptatif à votre projet de service de diffusion Edge :

1. **Cloner le référentiel de bloc de formulaire adaptatif**: clonez la variable [Référentiel de bloc de formulaire adaptatif](https://github.com/adobe/afb) sur votre ordinateur local. Il contient le code permettant d’effectuer le rendu du formulaire sur une page web EDS. Dans ce document, le dossier local de votre référentiel de bloc Forms est appelé `[Adaptive Form block repository]`.
1. **Recherchez le bloc de formulaire adaptatif Repository :** Accédez au [Référentiel de bloc de formulaire adaptatif]/block sur votre ordinateur local et copiez le dossier `form` dossier.
1. **Collez le bloc Formulaire adaptatif dans votre projet EDS :**
Accédez au [Référentiel de projet EDS]/block/ sur votre ordinateur local et collez le dossier du formulaire.
1. **Validez les modifications apportées à GitHub :** Archivez le dossier de formulaire et ses fichiers sous-jacents à votre projet de service de diffusion Edge sur GitHub.

Une fois ces étapes terminées, le bloc Formulaire adaptatif est ajouté au référentiel de projet du service de diffusion Edge (EDS) sur GitHub. Vous pouvez désormais créer et ajouter des formulaires à une page de sites EDS.


**Résolution des problèmes de génération GitHub**

Assurez-vous d’un processus de création GitHub fluide en résolvant les problèmes potentiels :

* **Résoudre l’erreur de chemin du module :**
Si vous rencontrez l’erreur &quot;Impossible de résoudre le chemin d’accès au module &quot;&#39;../../scripts/lib-franklin.js&#39;&quot;, accédez au [Projet EDS]fichier /blocks/forms/form.js . Mettez à jour l’instruction d’importation en remplaçant le fichier lib-franklin.js par le fichier aem.js .

* **Gérer les erreurs de liaison :**
Si vous rencontrez des erreurs de ligne, vous pouvez les contourner. Ouvrez le [Projet EDS]/package.json et modifiez le script &quot;lint&quot; à partir de &quot;lint&quot; : &quot;npm run lint:js &amp;&amp; npm run lint:css&quot; à &quot;lint&quot;: &quot;echo &#39;skipping linting for now&#39;&quot;. Enregistrez le fichier et validez les modifications apportées à votre projet GitHub.



+++

+++ Étape 2 : créez un formulaire à l’aide de Microsoft Excel ou de la feuille de calcul Google.

Au lieu de naviguer dans des processus complexes, il est possible d’obtenir facilement un formulaire à l’aide d’une feuille de calcul. Vous pouvez commencer par ajouter les lignes et les en-têtes de colonne à une feuille de calcul, où chaque ligne représente un champ de formulaire, tandis que chaque en-tête de colonne définit les propriétés du champ correspondant.

Prenons l’exemple de la feuille de calcul suivante, dans laquelle les lignes encadrent les champs d’une `enquiry` Les en-têtes de formulaire et de colonne définissent leurs propriétés :

![Feuille de calcul de requête](/help/edge/assets/enquiry-form-spreadsheet.png)

Pour poursuivre la création du formulaire :

1. Accédez à votre dossier de projet Edge Delivery AEM sur Microsoft SharePoint ou Google Drive.

1. Créez un classeur Excel Microsoft ou une feuille de calcul Google n’importe où dans votre répertoire de projet Edge Delivery AEM. Par exemple, créez une feuille de calcul nommée `enquiry` sur le répertoire du projet Edge Delivery d’AEM sur Google Drive.

1. Assurez-vous que la feuille est partagée avec l’utilisateur AEM approprié (par exemple `helix@adobe.com`) [selon les configurations spécifiées pour votre projet.](https://www.aem.live/docs/setup-customer-sharepoint). Octroyez à l’utilisateur l’autorisation de modification de la feuille.

1. Ouvrez la feuille de calcul créée et renommez la feuille par défaut &quot;shared-default&quot;.

   ![renommer la feuille par défaut en &quot;shared-default&quot;](/help/edge/assets/rename-sheet-to-shared-default.png)

1. Pour ajouter les champs du formulaire, insérez les lignes et les en-têtes de colonne dans la feuille &#39;shared-default&#39;. Chaque ligne doit représenter une [champ de formulaire](/help/edge/docs/forms/form-components.md), avec des en-têtes de colonne définissant le champ correspondant [properties](/help/edge/docs/forms/eds-form-field-properties).

   Pour un démarrage rapide, pensez à copier le contenu de la variable [Feuille de calcul de requête](https://docs.google.com/spreadsheets/d/196lukD028RDK_evBelkOonPxC7w0l_IiJ-Yx3DvMfNk/edit#gid=0) dans votre feuille de calcul. Après avoir copié le contenu, enregistrez votre feuille de calcul.

   >[!VIDEO](https://video.tv.adobe.com/v/3427468?quality=12&learn=on)


1. Utilisation [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) pour prévisualiser la feuille.

   ![Utilisez AEM Sidekick pour prévisualiser la feuille](/help/edge/assets/preview-form.png)

   Lors de la prévisualisation, les nouveaux onglets du navigateur affichent le contenu de la feuille au format JSON. Veillez à capturer l’URL d’aperçu, car elle est nécessaire pour le rendu du formulaire dans la section suivante. Le format d’URL se présente comme suit :


   ```JSON
       https://<branch>--<repository>--<owner>.hlx.live/<form>.json
   ```

   * `<branch>` fait référence à la branche de votre référentiel GitHub.
   * `<repository>` indique votre référentiel GitHub.
   * `<owner>` fait référence au nom d’utilisateur de votre compte GitHub qui héberge votre référentiel GitHub.

   Par exemple, si le référentiel de votre projet est nommé &quot;portal&quot;, il se trouve sous le compte &quot;wkndforms&quot; et que vous utilisez la branche &quot;main&quot;, l’URL ressemble à ce qui suit :

   `https://main--portal--wkndforms.hlx.page/enquiry.json`


+++

+++ Étape 3 : prévisualisez le formulaire à l’aide de votre page Edge Delivery Service (EDS).


Jusqu’à présent, vous avez ajouté le bloc Formulaire adaptatif à votre projet EDS et préparé la structure du formulaire. Maintenant, pour prévisualiser le formulaire :

1. **Accédez au répertoire de votre projet :** Ouvrez votre compte Microsoft SharePoint ou Google Drive et accédez au répertoire de votre projet Edge Delivery AEM.

1. **Incorporer le formulaire dans un document :** Ouvrez un fichier document (fichier d’index, par exemple) pour incorporer le formulaire. Vous pouvez également créer un document.

1. **Accédez à l’emplacement de votre choix :** Accédez à l’emplacement souhaité dans le document où vous avez l’intention d’ajouter le formulaire.

1. **Ajouter le bloc de formulaire adaptatif :** Insérez dans le fichier un bloc nommé &quot;Formulaire&quot;, comme illustré ci-dessous :

   | Formulaire |
   |---|
   | [https://main—portal—wkndforms.hlx.live/enquiry.json](https://main--portal--wkndforms.hlx.live/enquiry.json) |

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



## En savoir plus

* [Composants de formulaire](/help/edge/docs/forms/form-components.md)
* [Propriétés des champs de formulaire](/help/edge/docs/forms/eds-form-field-properties)
* [Créer et prévisualiser un formulaire](/help/edge/docs/forms/create-forms.md)
* [Activer le formulaire pour envoyer des données](/help/edge/docs/forms/submit-forms.md)
* [Publier un formulaire sur la page de sites](/help/edge/docs/forms/publish-eds-forms.md)
* [Ajouter des validations à des champs de formulaire](/help/edge/docs/forms/validate-forms.md)
* [Modifier les thèmes et le style du formulaire](/help/edge/docs/forms/style-theme-forms.md)
