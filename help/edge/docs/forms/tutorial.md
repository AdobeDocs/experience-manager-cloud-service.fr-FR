---
title: Prise en main d’AEM Forms Edge Delivery Services - Tutoriel du développeur
description: Ce tutoriel vous aide à vous familiariser avec un nouveau projet Adobe Experience Manager Forms (AEM). Dans dix à vingt minutes, vous aurez créé vos propres formulaires.s
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 610f9ba3f342b37d0d20a91c337323bffe95d58d
workflow-type: tm+mt
source-wordcount: '1786'
ht-degree: 1%

---


# Prise en main – Tutoriel pour l’équipe de développement

A l&#39;ère numérique actuelle, la création de formulaires conviviaux est essentielle pour toute entreprise. AEM Forms Edge Delivery Services (EDS) vous permet de créer des formulaires à l’aide d’outils familiers tels que Google Docs et Microsoft Office.

Ces formulaires envoient directement des données à un fichier Microsoft Excel ou Google Sheets, ce qui vous permet d’utiliser un écosystème dynamique et des API robustes de Google Sheets, Microsoft Excel et Microsoft SharePoint pour traiter facilement les données envoyées ou lancer un processus d’entreprise existant.

AEM Forms fournit un bloc, appelé Bloc Forms adaptatif, qui vous aide à créer facilement des formulaires pour capturer et stocker les données capturées. Vous pouvez créer un projet AEM prééquipé avec le bloc Forms adaptatif ou ajouter le bloc Forms adaptatif à un projet AEM existant.

Ce tutoriel AEM Forms vous guide tout au long des étapes de création, de prévisualisation et de publication de votre propre formulaire personnalisé avec un nouveau projet Adobe Experience Manager (AEM) Forms. Vous apprendrez également à ajouter un bloc Forms adaptatif à un projet AEM existant.

* **[Créez un projet AEM prééquipé avec le bloc Forms adaptatif](#create-a-new-eds-project-pre-equipped-with-adaptive-forms-block)**
* **[Ajout d’un bloc Forms adaptatif à un projet AEM existant](#add-adaptive-forms-block-to-an-existing-eds-project)**



## Conditions préalables

* Vous disposez d’un compte GitHub et vous comprenez les concepts de base de Git.
* Vous disposez d’un compte Google ou Microsoft SharePoint.
* Vous comprenez les principes de base du HTML, de CSS et de JavaScript.
* Node/npm est installé pour le développement local.

**Tête-toi !** Ce tutoriel utilise macOS, Chrome et Visual Studio Code. Bien que les étapes puissent être adaptées à d’autres configurations, les captures d’écran et les éléments spécifiques de l’interface utilisateur peuvent différer en fonction du système d’exploitation, du navigateur et de l’éditeur de code de votre choix.


## Créez un projet AEM prééquipé avec le bloc Forms adaptatif

Le modèle standard AEM Forms vous permet de commencer rapidement avec un projet AEM préconfiguré avec le bloc Forms adaptatif. Il s’agit de la méthode la plus rapide et la plus simple pour suivre AEM bonnes pratiques et passer directement à la création de vos formulaires.

### Prise en main du modèle de référentiel standard AEM Forms

1. Créez un référentiel GitHub pour votre projet AEM. Pour créer un référentiel :
   1. Accédez à [https://github.com/adobe-rnd/aem-boilerplate-forms](https://github.com/adobe-rnd/aem-boilerplate-forms).

      ![AEM Forms Boilerplate](/help/edge/assets/aem-forms-boilerplate.png)
   1. Cliquez sur le bouton **Utiliser ce modèle** et sélectionnez l’option **Création d’un référentiel** . L’écran Créer un référentiel s’affiche.

      ![Création d’un référentiel à l’aide du standard AEM Forms](/help/edge/assets/create-new-repository-using-aem-forms-boilerplate.png)

   1. Dans l’écran de création d’un référentiel, sélectionnez l’option **propriétaire**, et spécifiez **Nom du référentiel** . Adobe recommande que le référentiel soit défini sur **Public**. Ainsi, sélectionnez la variable **public** puis cliquez sur **Créer un référentiel**.

   ![Définir le référentiel public](/help/edge/assets/create-a-new-repo-keep-it-public.png)


1. Installez l’application GitHub de synchronisation du code AEM sur votre référentiel. Pour installer :
   1. Accédez à [https://github.com/apps/aem-code-sync/installations/new](https://github.com/apps/aem-code-sync/installations/new).
   1. Sur l’écran Installer la synchronisation du code d’AEM, sélectionnez le **Sélectionner uniquement les référentiels** et sélectionnez le référentiel nouvellement créé. Cliquez sur Enregistrer.

   ![Définir le référentiel public](/help/edge/assets/install-aem-code-sync-app-for-your-repo.png)

   >[!NOTE]
   >
   >
   > Si vous utilisez GitHub Enterprise avec le filtrage IP, vous pouvez ajouter l’adresse IP suivante à la liste autorisée : 3.227.118.73

   Félicitations. Un nouveau site web est en cours d’exécution sur `https://<branch>--<repo>--<owner>.hlx.page/`.

   * `<branch>` fait référence à la branche de votre référentiel GitHub.
   * `<repository>` indique votre référentiel GitHub.
   * `<owner>` fait référence au nom d’utilisateur de votre compte GitHub qui héberge votre référentiel GitHub.

   Par exemple, si le nom de la branche est `main`, le référentiel `wefinance`, et le propriétaire est `wkndforms`, le site web serait opérationnel sur [https://main—wefinance—wkndforms.hlx.page/](https://main--wefinance--wkndforms.hlx.page/).



### Lier votre propre source de contenu

Votre référentiel GitHub nouvellement créé pointe vers [exemple de contenu stocké dans un dossier de lecteur Google](https://drive.google.com/drive/folders/17LSiMZC77N8tCJRW45TnHHGcG8V3SLG_). Ce contenu en lecture seule constitue un excellent point de départ pour vos formulaires. N’hésitez pas à le copier dans votre propre lecteur Google et à le personnaliser en fonction de vos besoins.

![Exemple de contenu sur Google Drive](/help/edge/assets/folder-with-sample-content.png)

Pour copier l’exemple de contenu dans votre propre dossier de contenu et pointer votre référentiel GitHub vers votre propre dossier de contenu :

1. Créez un dossier spécifique à votre contenu AEM dans Google Drive ou Microsoft SharePoint. Ce document utilise un dossier créé sur Microsoft SharePoint.

1. Partagez le dossier avec l’utilisateur Adobe Experience Manager (helix@adobe.com).

   ![Utilisez l’option Gérer l’accès pour partager un dossier avec AEM User - SharePoint](/help/edge/assets/share-folder-with-aem-user.png)

   ![Utilisez l’option Gérer l’accès pour partager un dossier avec AEM User - Google Drive](/help/edge/assets/share-google-drive-folder.png)


   Assurez-vous que vous avez fourni des droits de modification sur le dossier à l’utilisateur Adobe Experience Manager.

   ![Partager le dossier avec AEM utilisateur, fournir les droits d’édition - SharePoint](/help/edge/assets/share-folder-with-aem-user-provide-editing-access.png)

   ![Partager le dossier avec l’utilisateur AEM, fournir les droits d’édition - Google Drive](/help/edge/assets/add-aem-user-google-folder.png)

1. Copiez le [exemple de contenu stocké dans le dossier de lecteur Google](https://drive.google.com/drive/folders/17LSiMZC77N8tCJRW45TnHHGcG8V3SLG_) dans votre dossier . Pour copier :

   1. Téléchargez les fichiers ensemble ou téléchargez des fichiers individuels.

      ![Télécharger un exemple de contenu](/help/edge/assets/download-sample-content.png)

      La variable `index`, `nav`, et `footer` Les fichiers définissent la disposition de base de vos pages et changent rarement dans l’ensemble d’un projet. Ils ont également une structure spécifique différente de la plupart des autres fichiers de contenu. En examinant ces fichiers, vous vous rendrez compte de l’organisation du contenu dans AEM Projets.


   1. Chargez ces fichiers dans le dossier SharePoint Microsoft ou Google Drive.

      ![Exemple de contenu sur Google Drive](/help/edge/assets/upload-sample-files-to-your-content-folder.png)

      Assurez-vous de copier la variable  `enquiry` de l’exemple de contenu dans votre dossier sur Google Drive ou Microsoft SharePoint. Il contient la structure d’un exemple de formulaire.

1. Maintenant que votre dossier de contenu est configuré, il est temps de le lier à votre projet sur GitHub que vous avez créé à l’aide du standard AEM Forms. Pour vous connecter :

   1. Accédez au référentiel GitHub que vous avez créé précédemment à l’aide d’AEM Forms Boilerplate.
   1. Ouvrez le `fstab.yaml` pour édition.
   1. Remplacez la référence existante par le chemin d’accès au dossier que vous avez partagé avec l’utilisateur AEM (helix@adobe.com).

      ![Exemple de contenu sur Google Drive](/help/edge/assets/replace-path-in-fstab-yaml-with-your-content-folder.png)


      Si vous utilisez Microsoft SharePoint, le chemin du dossier utilise le format suivant :

      ```HTML
      https://<tenant>.sharepoint.com/sites/  <sp-site>/Shared%20Documents/<folder-name>
      ```

      Par exemple,

      ```HTML
      https://adobe.sharepoint.com/sites/wkndforms/Shared%20Documents/wefinance
      ```

      Pour plus d’informations sur la gestion des fichiers avec Microsoft SharePoint, voir [Utilisation d’Adobe SharePoint](https://www.aem.live/docs/setup-customer-sharepoint).



   1. Valider la mise à jour `fsatb.yaml` une fois que vous avez mis à jour la référence et que tout semble correct. Si vous rencontrez des problèmes de version, reportez-vous à la section [Résolution des problèmes de génération GitHub](#troubleshooting-github-build-issues).



      ![Validez le fichier fsatab.yaml mis à jour](/help/edge/assets/commit-updated-fstab-yaml.png)

      Cela connecte votre dossier de contenu à votre site web. Après la mise à jour de la référence, vous pouvez rencontrer des erreurs &quot;404 Not Found&quot; (404 introuvable). En effet, votre contenu n’a pas encore été prévisualisé. La section suivante explique comment commencer à créer et prévisualiser votre contenu.

      ![Validez le fichier fsatab.yaml mis à jour](/help/edge/assets/aem-forms-project-folder-error.png)

### Prévisualiser et publier votre contenu

Une fois la dernière étape terminée, votre nouvelle source de contenu n’est pas vide, mais elle ne sera pas visible sur votre site web tant qu’elle n’aura pas été convertie en aperçu ou en scènes en direct. Actuellement, cela peut entraîner des erreurs 404.

Pour prévisualiser du contenu non publié :

1. Installez l’extension Chrome appelée [AEM Sidekick](https://chrome.google.com/webstore/detail/helix-sidekick-beta/ccfggkjabjahcjoljmgmklhpaccedipo).

   ![Installer AEM Sidekick](/help/edge/assets/install-aem-sidekick.png)

   Après l’installation de l’extension vers Chrome, n’oubliez pas de l’épingler. Cela facilite sa recherche.

   ![AEM Sidekick Pin](/help/edge/assets/pin-aem-sidekick.png)

1. Pour configurer l’extension Chrome Sidekick, accédez à votre dossier Google Drive ou Microsoft SharePoint précédemment partagé, cliquez avec le bouton droit de la souris sur l’icône d’extension dans la barre d’outils du navigateur et sélectionnez `Add this project`.

   ![AEM Sidekick - Ajout d’un projet](/help/edge/assets/aem-sidekick-add-a-project.png)

   Une fois l’extension installée et votre projet ajouté, vous êtes prêt à prévisualiser et publier votre contenu à partir de votre lecteur Google.

1. Sélectionnez tous les documents du dossier SharePoint Microsoft ou Lecteur Google . Vous pouvez sélectionner plusieurs documents en maintenant la touche Ctrl (Windows/Linux) ou Cmd (Mac) enfoncée tout en cliquant.

   ![Sélectionner tous les fichiers](/help/edge/assets/select-all-files.png)

1. Cliquez sur l’icône du AEM Sidekick épinglée sur votre barre d’extension Chrome. Une barre d’outils s’affiche à l’écran. Vous pouvez choisir de prévisualiser ou de publier votre contenu.

   Si vous avez copié sur `index`, `nav`, `footer` et `enquiry` tous ces fichiers sont des documents distincts ayant leurs propres cycles de prévisualisation et de publication. Veillez donc à les prévisualiser (et à les publier) tous.

   Lors de la prévisualisation des fichiers, les nouveaux onglets du navigateur affichent les documents. Pour prévisualiser l’exemple de formulaire, accédez à l’URL suivante :


   ```HTML
   https://<branch>--<repository>--<owner>.hlx.live
   ```

   * `<branch>` fait référence à la branche de votre référentiel GitHub.
   * `<repository>` indique votre référentiel GitHub.
   * `<owner>` fait référence au nom d’utilisateur de votre compte GitHub qui héberge votre référentiel GitHub.


   `https://<branch>--<repo>--<owner>.hlx.page/enquiry` URL.

   Par exemple, si le référentiel de votre projet s’appelle &quot;wefinance&quot;, il se trouve sous le propriétaire du compte &quot;wkndforms&quot; et que vous utilisez la branche &quot;main&quot;, l’URL est :



   [https://main—wefinance—wkndforms.hlx.page](https://main--wefinance--wkndforms.hlx.page).

### Création d’un formulaire

L’exemple de contenu comprend une feuille &quot;enquête&quot; qui sert de modèle pour le formulaire &quot;enquête&quot;. Chaque ligne de la feuille représente une [champ de formulaire](/help/edge/docs/forms/form-components.md#available-components)et les en-têtes de colonne définissent la variable [propriétés de champ](/help/edge/docs/forms/form-components.md#available-components). Cet exemple de formulaire vous donne un aperçu de la création de votre formulaire.

![Demander](/help/edge/assets/enquiry-form-microsoft-sharepoint.png)

Commençons par mettre à jour un libellé de champ. Ouvrez la feuille &quot;Requête&quot; pour la modifier, modifiez le libellé du bouton Envoyer en `Let's Chat`et utilisez le sidekick pour le publier.

![Demander](/help/edge/assets/enquiry-form-preview-publish.png)

Pour prévisualiser le formulaire de demande mis à jour, accédez à l&#39;URL suivante :


```HTML
    https://<branch>--<repository>--<owner>.hlx.page/enquiry
       
```

Le libellé du bouton d’envoi est mis à jour vers `Let's Chat`.

![Demander](/help/edge/assets/updated-form.png)

Pour plus d’informations sur la création et la publication d’un nouveau formulaire, passez à la section [création d’un formulaire](/help/edge/docs/forms/create-forms.md) guide.

### Commencer à développer le style et les fonctionnalités


Pour être opérationnel avec un environnement de développement AEM local en un rien de temps :

1. Installez l’interface de ligne de commande AEM : l’interface de ligne de commande AEM simplifie les tâches de développement. Installez-le globalement à l’aide de npm :

   ```Bash
       npm install -g @adobe/aem-cli
   ```

1. Cloner votre projet GitHub : clonez votre référentiel de projet depuis GitHub à l’aide de la commande suivante, en remplaçant <owner> avec le propriétaire du référentiel et <repo> avec le nom du référentiel :

   ```
   git clone https://github.com/<owner>/<repo>
   ```

1. Démarrez votre environnement local : accédez à votre répertoire de projet et déclenchez votre instance d’AEM locale à l’aide d’une seule commande :

   ```
   cd <repo>
   aem up
   ```

Bloc Forms adaptatif `blocks/form` Le dossier est votre terrain de jeu pour le style et le code de vos formulaires ! Modifiez les `.css` ou `.js` dans ce répertoire. Les modifications sont répercutées instantanément dans votre navigateur.

Prêt à présenter votre création ? Utilisez Git pour valider et pousser vos modifications. Cela met à jour les environnements de prévisualisation et de production accessibles à l’adresse suivante : (remplacez les espaces réservés par les détails du projet) :

Aperçu : `https://<branch>--<repo>--<owner>.hlx.page/`
Production : `https://<branch>--<repo>--<owner>.hlx.live/`
Félicitations ! Vous avez correctement configuré votre environnement de développement local et déployé vos modifications.



## Ajout d’un bloc Forms adaptatif à votre projet AEM existant


>[!VIDEO](https://video.tv.adobe.com/v/3427789)

Si vous disposez déjà d’un projet AEM, vous pouvez intégrer le bloc Forms adaptatif à votre projet actuel pour commencer à créer le formulaire. Pour intégrer :

1. Cloner le référentiel de bloc de Forms adaptatif : https://github.com/adobe-rnd/aem-boilerplate-forms sur votre ordinateur.

1. Dans le dossier téléchargé, recherchez le `blocks/form` dossier. Copiez ce dossier. Maintenant, accédez au site local de votre projet AEM `blocks` et collez le dossier de formulaire copié ici.

1. Validez et envoyez ces modifications à votre projet AEM sur GitHub.


C’est terminé ! Le bloc Forms adaptatif fait désormais partie de votre projet AEM. Vous pouvez commencer à créer et ajouter des formulaires à vos pages d’AEM.


## Résolution des problèmes de génération GitHub

Assurez-vous d’un processus de création GitHub fluide en résolvant les problèmes potentiels :

* **Résoudre l’erreur de chemin du module :**
Si vous rencontrez l’erreur &quot;Impossible de résoudre le chemin d’accès au module &quot;&#39;../../scripts/lib-franklin.js&#39;&quot;, accédez au [Projet EDS]fichier /blocks/forms/form.js . Mettez à jour l’instruction d’importation en remplaçant le fichier lib-franklin.js par le fichier aem.js .

* **Gérer les erreurs de liaison :**
Si vous rencontrez des erreurs de ligne, vous pouvez les contourner. Ouvrez le [Projet EDS]/package.json et modifiez le script &quot;lint&quot; depuis `"lint": "npm run lint:js && npm run lint:css"` to `"lint": "echo 'skipping linting for now'"`. Enregistrez le fichier et validez les modifications apportées à votre projet GitHub.


## Voir également

* [Création d’un formulaire à l’aide de feuilles de calcul Google ou de Microsoft Excel](/help/edge/docs/forms/create-forms.md)
* [Envoyer des formulaires directement à vos feuilles Microsoft Excel ou Google](/help/edge/docs/forms/submit-forms.md)
* [Modifier l’aspect de vos formulaires](/help/edge/docs/forms/style-theme-forms.md)
