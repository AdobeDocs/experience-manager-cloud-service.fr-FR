---
title: Commencer avec Edge Delivery Services pour AEM Forms - Tutoriel pour l’équipe de développement
description: Ce tutoriel vous permet de prendre en main un nouveau projet Adobe Experience Manager Forms (AEM). D’ici dix à vingt minutes, vous aurez créé vos propres formulaires.
feature: Edge Delivery Services
exl-id: bb7e93ee-0575-44e1-9c5e-023284c19490
role: Admin, Architect, Developer
source-git-commit: edfefb163e2d48dc9f9ad90fa68809484ce6abb0
workflow-type: tm+mt
source-wordcount: '1921'
ht-degree: 96%

---

# Prise en main - Tutoriel pour l’équipe de développement

À l’ère numérique actuelle, la création de formulaires conviviaux est essentielle pour toute entreprise. Edge Delivery Services pour AEM Forms vous permet de créer des formulaires à l’aide d’outils courants tels que Google Docs et Microsoft Office.

Ces formulaires envoient directement les données vers un fichier Microsoft Excel ou Google Sheets, ce qui vous permet d’utiliser l’écosystème dynamique et les API robustes de Google Sheets, Microsoft Excel et Microsoft SharePoint pour traiter facilement les données envoyées ou pour démarrer un workflow d’entreprise existant.

AEM Forms fournit un bloc, appelé bloc de formulaires adaptatifs, qui vous permet de créer facilement des formulaires pour capturer les données et stocker les données capturées. Vous pouvez [créer un projet AEM préconfiguré avec le bloc de formulaires adaptatifs](#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) <!--or [add the Adaptive Forms Block to an existing AEM project](#add-adaptive-forms-block-to-your-existing-aem-project)-->.

Ce tutoriel AEM Forms vous guide tout au long des étapes de création, de prévisualisation et de publication de votre propre formulaire personnalisé avec un nouveau projet Adobe Experience Manager (AEM) Forms.

## Prérequis

- Vous disposez d’un compte GitHub et vous comprenez les concepts de base de Git.
- Vous disposez d’un compte Google ou Microsoft SharePoint.
- Vous comprenez les principes de base du HTML, du CSS et du JavaScript.
- Node/npm est installé pour le développement local.

**Attention.** Ce tutoriel utilise macOS, Chrome et Visual Studio Code. Bien que les étapes puissent être adaptées à d’autres configurations, les captures d’écran et des éléments spécifiques de l’interface utilisateur peuvent différer en fonction du système d’exploitation, du navigateur et de l’éditeur de code que vous avez choisi d’utiliser.


## Créer un projet AEM préconfiguré avec le bloc de formulaires adaptatifs

Le modèle standard AEM Forms vous permet de prendre rapidement en main un projet AEM préconfiguré avec le bloc de formulaires adaptatifs. Il s’agit de la méthode la plus rapide et la plus simple pour respecter les bonnes pratiques relatives à AEM et passer directement à la création de vos formulaires.

### Prise en main du modèle de référentiel standard AEM Forms

1. Créez un référentiel GitHub pour votre projet AEM. Pour créer un référentiel :
   1. Accédez à [https://github.com/adobe-rnd/aem-boilerplate-forms](https://github.com/adobe-rnd/aem-boilerplate-forms).

      ![Modèle standard AEM Forms](/help/edge/docs/forms/assets/eds-form-boilerplate.png)
   1. Cliquez sur l’option **Utiliser ce modèle** et sélectionnez l’option **Créer un référentiel**. L’écran Créer un référentiel s’affiche.

      ![Création d’un référentiel à l’aide du modèle standard AEM Forms](/help/edge/docs/forms/assets/use-eds-form-template.png)

   1. Dans l’écran de création d’un référentiel, sélectionnez la personne **propriétaire** et spécifiez le **Nom du référentiel**. Adobe recommande que le référentiel soit défini sur **Public**. Ainsi, sélectionnez l’option **public** puis cliquez sur **Créer un référentiel**.

   ![Définition du référentiel sur public](/help/edge/assets/create-a-new-repo-keep-it-public.png)


1. Installez l’application GitHub AEM Code Sync sur votre référentiel. Pour l’installer :
   1. Accédez à [https://github.com/apps/aem-code-sync/installations/new](https://github.com/apps/aem-code-sync/installations/new).
   1. Sur l’écran Installer AEM Code Sync, sélectionnez l’option **Sélectionner uniquement les référentiels** et sélectionnez le référentiel nouvellement créé. Cliquez sur Enregistrer.

   ![Définition du référentiel sur public](/help/edge/assets/install-aem-code-sync-app-for-your-repo.png)

   >[!NOTE]
   >
   >
   > Si vous utilisez GitHub Enterprise avec le filtrage d’adresses IP, vous pouvez ajouter l’adresse IP suivante à la liste autorisée : 3.227.118.73.

   Félicitations. Vous avez désormais un nouveau site web en cours d’exécution dans `https://<branch>--<repo>--<owner>.aem.page/`.

   - `<branch>` fait référence à la branche de votre référentiel GitHub.
   - `<repository>` indique votre référentiel GitHub.
   - `<owner>` fait référence au nom d’utilisateur ou d’utilisatrice de votre compte GitHub qui héberge votre référentiel GitHub.

   Par exemple, si le nom de la branche est `main`, le référentiel est `wefinance` et la personne propriétaire est `wkndforms`, le site web serait opérationnel à l’adresse `https://main--wefinance--wkndforms.aem.page`
&lt;!—(https://main--wefinance--wkndform.aem.page)-->

### Lier votre propre source de contenu

<!--Your newly created GitHub repository points to [example content stored in a Google Drive folder](https://drive.google.com/drive/folders/1bvjfi6TqpYA7DvbX6kKc-m7FgHuJ4RUQ). This read-only content provides a great starting point for your forms. Feel free to copy it into your own Google Drive and customize it to fit your needs.

![Sample Content on Google Drive](/help/edge/assets/folder-with-sample-content.png)-->

Pour copier l’exemple de contenu dans votre propre dossier de contenu et pointer votre référentiel GitHub vers votre propre dossier de contenu :

1. Créez un dossier spécifique pour votre contenu AEM dans Google Drive ou Microsoft SharePoint. Ce document utilise un dossier créé sur Microsoft SharePoint.

1. Partagez le dossier avec l’utilisateur ou l’utilisatrice Adobe Experience Manager (forms@adobe.com).

   ![Utilisation de l’option Gérer l’accès pour partager un dossier avec un utilisateur ou une utilisatrice AEM - SharePoint](/help/edge/assets/share-folder-with-aem-user.png)

   ![Utilisation de l’option Gérer l’accès pour partager un dossier avec un utilisateur ou une utilisatrice AEM - Google Drive](/help/edge/assets/share-google-drive-folder.png)


   Assurez-vous que vous avez accordé des droits de modification sur le dossier à l’utilisateur ou à l’utilisatrice Adobe Experience Manager.

   ![Partage d’un dossier avec un utilisateur ou une utilisatrice AEM et octroi des droits de modification - SharePoint](/help/edge/assets/share-folder-with-aem-user-provide-editing-access.png){width=50%}

   ![Partage d’un dossier avec un utilisateur ou une utilisatrice AEM et octroi des droits de modification - Google Drive](/help/edge/assets/add-aem-user-google-folder.png){width=50%}

1. Copiez l’[exemple de contenu](/help/edge/assets/wefinance1.zip) dans votre dossier. Pour le copier :

   1. Décompressez le dossier téléchargé et copiez le contenu.

      ![Téléchargement de l’exemple de contenu](/help/edge/assets/download-sample-content.png)

      Les fichiers `nav` et `footer` définissent la disposition de base de vos pages et changent rarement au cours d’un projet. Ils ont également une structure spécifique différente de la plupart des autres fichiers de contenu. En examinant ces fichiers, vous pouvez observer comment le contenu est organisé dans des projets AEM.


   1. Chargez ces fichiers dans le dossier Microsoft SharePoint ou le dossier Google Drive.

      ![Exemple de contenu sur Google Drive](/help/edge/assets/upload-sample-files-to-your-content-folder.png)

      Assurez-vous de copier la feuille `enquiry` de l’exemple de contenu dans votre dossier Google Drive ou Microsoft SharePoint. Elle contient la structure d’un exemple de formulaire.

1. Maintenant que votre dossier de contenu est configuré, il est temps de le lier à votre projet sur GitHub que vous avez créé plus tôt à l’aide du modèle standard AEM Forms. Pour le connecter :

   1. Accédez au référentiel GitHub que vous avez créé plus tôt à l’aide du modèle standard AEM Forms.
   1. Ajoutez le fichier `fstab.yaml` dans le dossier racine.
   1. Ajoutez la référence avec le chemin d’accès au dossier que vous avez partagé avec l’utilisateur AEM (forms@adobe.com).

      ![Exemple de contenu sur Google Drive](/help/edge/assets/replace-path-in-fstab-yaml-with-your-content-folder.png)


      Si vous utilisez Microsoft SharePoint, le chemin d’accès au dossier utilise le format suivant :

      ```HTML
      https://<tenant>.SharePoint.com/sites/<sp-site>/Shared%20Documents/<folder-name>
      ```

      par exemple,

      ```HTML
      https://adobe.SharePoint.com/sites/wkndforms/Shared%20Documents/wefinance
      ```

      Pour plus d’informations sur la gestion des fichiers avec Microsoft SharePoint, consultez [Utilisation d’Adobe SharePoint](https://www.aem.live/docs/setup-customer-sharepoint).


   1. Validez le fichier `fsatb.yaml`, une fois que vous avez ajouté la référence et que tout semble correct. Si vous rencontrez des problèmes de génération, consultez [Résolution des problèmes de génération dans GitHub](#troubleshooting-github-build-issues).

      ![Validation du fichier fsatab.yaml mis à jour](/help/edge/assets/commit-updated-fstab-yaml.png)

      Cela connecte votre dossier de contenu à votre site web. Après la mise à jour de la référence, vous pouvez au départ rencontrer des erreurs « 404 Not Found ». Celles-ci se produisent parce que votre contenu n’a pas encore été prévisualisé. La section suivante explique comment commencer à créer et à prévisualiser votre contenu.

### Prévisualiser et publier votre contenu

Une fois la dernière étape terminée, votre nouvelle source de contenu n’est pas vide, mais elle ne sera pas visible sur votre site web tant qu’elle n’aura pas été transférée à l’état de prévisualisation ou à l’état actif. Actuellement, cela peut entraîner des erreurs 404.

Pour prévisualiser du contenu non publié :

1. Installez l’extension Chrome [AEM Sidekick](https://chrome.google.com/webstore/detail/helix-sidekick-beta/ccfggkjabjahcjoljmgmklhpaccedipo).

   ![Installation d’AEM Sidekick](/help/edge/assets/install-aem-sidekick.png)

   Après l’installation de l’extension dans Chrome, n’oubliez pas de l’épingler. Cela permet de la retrouver plus facilement.

   ![Épinglage d’AEM Sidekick](/help/edge/assets/pin-aem-sidekick.png)

1. Pour configurer l’extension Chrome Sidekick, accédez à votre dossier Google Drive ou Microsoft SharePoint précédemment partagé, puis cliquez avec le bouton droit de la souris sur l’icône de l’extension dans la barre d’outils du navigateur et sélectionnez `Add this project`.

   ![AEM Sidekick - Ajout d’un projet](/help/edge/assets/aem-sidekick-add-a-project.png)

   Une fois l’extension installée et votre projet ajouté, vous êtes en mesure de prévisualiser et de publier votre contenu à partir de votre Google Drive.

1. Sélectionnez tous les documents du dossier Microsoft SharePoint ou Google Drive. Vous pouvez sélectionner plusieurs documents en maintenant la touche Ctrl (Windows/Linux) ou Cmd (Mac) enfoncée tout en cliquant.

   ![Sélection de tous les fichiers](/help/edge/assets/select-all-files.png)

1. Cliquez sur l’icône d’AEM Sidekick épinglée à votre barre d’extensions Chrome. Une barre d’outils s’affiche à l’écran. Vous pouvez choisir de prévisualiser ou de publier votre contenu.

   Si vous avez copié les fichiers `index`, `nav`, `footer` et `enquiry`, il s’agit de documents distincts possédant chacun leurs propres cycles de prévisualisation et de publication. Veillez donc à tous les prévisualiser (et à les publier).

   Lors de la prévisualisation des fichiers, de nouveaux onglets dans le navigateur affichent les documents. Pour prévisualiser l’exemple de formulaire, accédez à l’URL suivante :


   ```HTML
   https://<branch>--<repository>--<owner>.aem.live
   ```

   - `<branch>` fait référence à la branche de votre référentiel GitHub.
   - `<repository>` indique votre référentiel GitHub.
   - `<owner>` fait référence au nom d’utilisateur ou d’utilisatrice de votre compte GitHub qui héberge votre référentiel GitHub.


   URL `https://<branch>--<repo>--<owner>.aem.page/enquiry`.

   Par exemple, si le référentiel de votre projet s’appelle « wefinance », que la personne propriétaire du compte est « wkndforms », que vous utilisez la branche « main » et le nom de formulaire `enquiry`, l’URL est : `https://main--wefinance--wkndform.aem.live/enquiry`.
&lt;!—(https://main--wefinance--wkndform.aem.live/enquiry).-->

### Créer un formulaire

L’exemple de contenu inclut une feuille « demande » qui sert de modèle pour le formulaire « demande ». Chaque ligne de la feuille représente un [champ de formulaire](/help/edge/docs/forms/form-components.md#available-components) et les en-têtes de colonne définissent les [propriétés des champs](/help/edge/docs/forms/form-components.md#available-components). Cet exemple de formulaire vous offre une base pour la création de votre formulaire.

![Formulaire de demande](/help/edge/docs/forms/assets/enquiry-form-microsoft-sharepoint.png)

>[!IMPORTANT]
>
>**La feuille dans laquelle le formulaire est créé présente des restrictions quant au nom qui lui est attribué. Seuls `helix-default` et `shared-aem` peuvent être utilisés comme noms de feuille.**

Commençons par mettre à jour un libellé de champ. Ouvrez la feuille « demande » pour effectuer des modifications, modifiez le libellé du bouton Envoyer en `Let's Talk` et utilisez AEM Sidekick pour prévisualiser et publier le fichier.

![Formulaire de demande](/help/edge/assets/enquiry-form-preview-publish.png)

Lorsque vous prévisualisez ou publiez le fichier, une version JSON du fichier s’affiche dans un nouvel onglet. Copiez l’URL de prévisualisation (.aem.page) ou de publication (.aem.live) du fichier.

![JSON de la feuille de calcul du formulaire](/help/edge/assets/preview-and-publish-enquiry-form.png)

Ouvrez le fichier `enquiry` et remplacez l’URL du bloc de formulaire par l’URL du fichier copié lors de l’étape précédente. Vérifiez que l’URL est un lien hypertexte.

![Fichier de demande avec l’URL .json de l’URL de la feuille de calcul](/help/edge/assets/enquiry-doc-to-embed-form.png)

Utilisez AEM Sidekick pour prévisualiser et publier le document de demande.

![Fichier de demande avec l’URL .json de l’URL de la feuille de calcul](/help/edge/assets/preview-and-publish-enquiry-document.png)


Pour prévisualiser le formulaire de demande mis à jour, accédez à l’URL suivante :


```HTML
    https://<branch>--<repository>--<owner>.aem.page/enquiry
       
```

Le libellé du bouton Envoyer est remplacé par `Let's Talk`.

![Formulaire de demande](/help/edge/assets/updated-form.png)

&lt;!—(https://main--wefinance--wkndform.aem.live/enquiry)-->

URL : `https://main--wefinance--wkndform.aem.live/enquiry`
&lt;!—(https://main--wefinance--wkndform.aem.live/enquiry)-->


Pour plus d’informations sur la création et la publication d’un nouveau formulaire, consultez le guide [Créer un formulaire](/help/edge/docs/forms/create-forms.md).

### Commencer à développer le style et les fonctionnalités


Pour être rapidement capable d’opérer avec un environnement de développement AEM local :

1. Installez l’interface de ligne de commande AEM : l’interface de ligne de commande AEM simplifie les tâches de développement. Installez-la globalement à l’aide de npm :

   ```Bash
       npm install -g @adobe/aem-cli
   ```

1. Clonez votre projet GitHub : clonez le référentiel de votre projet à partir de GitHub à l’aide de la commande suivante, en remplaçant `<owner>` par le propriétaire du référentiel et `<repo>` par le nom du référentiel :

   ```
   git clone https://github.com/<owner>/<repo>
   ```

1. Démarrez votre environnement local : accédez à votre répertoire de projet et déclenchez votre instance d’AEM locale à l’aide d’une seule commande :

   ```
   cd <repo>
   aem up
   ```

Le dossier du bloc de formulaires adaptatifs `blocks/form` est votre espace réservé pour le style et le code de vos formulaires. Modifiez n’importe quel fichier `.css` ou `.js` dans ce répertoire et les modifications seront visibles instantanément dans votre navigateur.

Votre création est prête à être dévoilée ? Utilisez Git pour valider et envoyer vos modifications. Cela met à jour les environnements de prévisualisation et de production accessibles aux URL suivantes (remplacez les espaces réservés par les détails de votre projet) :

Prévisualisation : `https://<branch>--<repo>--<owner>.aem.page/`
Production : `https://<branch>--<repo>--<owner>.aem.live/`

Félicitations. Vous avez correctement configuré votre environnement de développement local et déployé vos modifications.

## Ajouter un bloc de formulaires adaptatifs à votre projet AEM existant

<!--
>[!VIDEO](https://video.tv.adobe.com/v/3427789)-->

Si vous disposez déjà d’un projet AEM, vous pouvez intégrer le bloc de formulaires adaptatifs à votre projet actuel pour commencer à créer le formulaire.

>[!NOTE]
>
>
> Cette étape s’applique aux projets créés à l’aide du [modèle standard AEM XWalk](https://github.com/adobe/aem-boilerplate). Si vous avez créé votre projet AEM à l’aide du [modèle standard AEM Forms](https://github.com/adobe-rnd/aem-boilerplate-forms), vous pouvez ignorer cette étape.

Pour effectuer l’intégration, procédez comme suit :

1. Accédez au dossier du référentiel du projet AEM sur votre système local.

1. Copiez et collez les dossiers et fichiers suivants du [modèle standard AEM Forms](https://github.com/adobe-rnd/aem-boilerplate-forms) dans votre projet AEM :

   - Dossier [form block](https://github.com/adobe-rnd/aem-boilerplate-forms/tree/main/blocks/form)
   - Fichier [form-editor-support.js](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/form-editor-support.js)
   - Fichier [form-editor-support.css](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/form-editor-support.css)
1. Accédez au fichier `/scripts/editor-support.js` dans votre projet AEM et mettez-le à jour avec les modifications du [fichier editor-support.js dans le modèle standard AEM Forms](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/editor-support.js).
1. Accédez au fichier `/models/_section.json` dans votre projet AEM et ajoutez « form » et « embed-adaptive-form » au tableau de composants de l’objet `filters` :

   ```
       "filters": [
       {
     "id": "section",
     "components": [
       .
       .
       .
       "form",
       "embed-adaptive-form"
     ]
    }]
   ```

1. (Facultatif) Accédez à `/.eslintignore` dans votre projet AEM et ajoutez les lignes de code suivantes :

   ```
   blocks/form/rules/formula/*
   blocks/form/rules/model/*
   blocks/form/rules/functions.js
   scripts/editor-support.js
   scripts/editor-support-rte.js
   ```

1. (Facultatif) Accédez à `/.eslintrc.js` dans votre projet AEM et ajoutez les lignes de code suivantes dans l’objet `rules` :

   ```
   'xwalk/max-cells': ['error', {
     '*': 4, // default limit for all models
     form: 15,
     wizard: 12,
     'form-button': 7,
     'checkbox-group': 20,
     checkbox: 19,
     'date-input': 21,
     'drop-down': 19,
     email: 22,
     'file-input': 20,
     'form-fragment': 15,
     'form-image': 7,
     'multiline-input': 23,
     'number-input': 22,
     panel: 17,
     'radio-group': 20,
     'form-reset-button': 7,
     'form-submit-button': 7,
     'telephone-input': 20,
     'text-input': 23,
     accordion: 14,
     modal: 11,
     rating: 18,
     password: 20,
     tnc: 12,
   }],
   'xwalk/no-orphan-collapsible-fields': 'off', // Disable until enhancement is done for Forms properties
   ```

1. Ouvrez le terminal et exécutez les commandes suivantes :

   ```
   npm i
   npm run build:json
   ```

   >[!NOTE]
   >
   > Avant de transmettre les modifications au référentiel de votre projet AEM sur GitHub, assurez-vous que les fichiers `component-definition.json`, `component-models.json` et `component-filters.json` situés au niveau racine du projet AEM sont mis à jour avec les objets liés au formulaire.

1. Validez et envoyez ces modifications vers votre référentiel de projet AEM sur GitHub.

C’est terminé. Le bloc de formulaires adaptatifs fait désormais partie de votre projet AEM. Vous pouvez commencer à créer et ajouter des formulaires à vos pages AEM.

## Résolution des problèmes de génération dans GitHub

Assurez-vous d’avoir un processus de génération GitHub fluide en résolvant les problèmes potentiels :

- **Résoudre l’erreur de chemin d’accès du module :**
si vous rencontrez l’erreur « Impossible de résoudre le chemin d’accès au module &quot;scripts/lib-franklin.js&quot; », accédez au fichier [EDS Project]/blocks/forms/form.js. Mettez à jour l’instruction d’import en remplaçant le fichier lib-franklin.js par le fichier aem.js.

- **Gérer les erreurs de lint :**
si vous rencontrez des erreurs de lint, vous avez la possibilité de les contourner. Ouvrez le fichier /package.json [Projet EDS] et modifiez le script « lint » de `"lint": "npm run lint:js && npm run lint:css"` en `"lint": "echo 'skipping linting for now'"`. Enregistrez le fichier et validez les modifications apportées à votre projet GitHub.

