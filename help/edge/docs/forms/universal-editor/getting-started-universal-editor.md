---
title: Commencer avec Edge Delivery Services pour AEM Forms dans l’éditeur universel - Tutoriel pour l’équipe de développement
description: Ce tutoriel vous permet de prendre en main un nouveau projet Adobe Experience Manager Forms (AEM). D’ici dix à vingt minutes, vous aurez créé vos propres formulaires Edge Delivery Services dans l’éditeur universel.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 24a23d98-1819-4d6b-b823-3f1ccb66dbd8
source-git-commit: 95998daf04ae579ca11896953903852e6140c3a4
workflow-type: tm+mt
source-wordcount: '1853'
ht-degree: 91%

---


# Commencer avec Edge Delivery Services pour AEM Forms dans l’éditeur universel (WYSIWYG)

| Version | Lien de l’article |
| -------- | ---------------------------- |
| Création basée sur l’éditeur universel | Cet article |
| Création basée sur des documents | [Cliquer ici](/help/edge/docs/forms/tutorial.md) |


<span class="preview"> Cette fonctionnalité est disponible par le biais du programme d’accès précoce. Pour demander l’accès, envoyez un e-mail à partir de votre adresse officielle à <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a> avec le nom de votre organisation GitHub et le nom du référentiel. Par exemple, si l’URL du référentiel est https://github.com/adobe/abc, le nom de l’organisation est adobe et le nom du référentiel est abc.</span>

À l’ère numérique actuelle, les formulaires conviviaux sont essentiels pour toute entreprise. Les formulaires Edge Delivery Services sont créés à l’aide de l’éditeur universel, qui offre des fonctionnalités WYSIWYG (ce que vous voyez est ce que vous obtenez). Il fournit une interface moderne et intuitive pour une création de formulaire efficace.

AEM Forms fournit un bloc, appelé bloc de formulaires adaptatifs, qui vous permet de créer facilement des formulaires Edge Delivery Services pour capturer et stocker les données. Vous pouvez [créer un projet AEM préconfiguré avec le bloc de formulaires adaptatifs](#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) ou [ajouter le bloc de formulaires adaptatifs à un projet AEM existant](#add-adaptive-forms-block-to-your-existing-aem-project).

![Workflow du référentiel Github](/help/edge/assets/repo-workflow.png){width=auto}

Ce tutoriel vous guide tout au long de la création, de la prévisualisation et de la publication de votre formulaire avec un projet de site Adobe Experience Manager nouveau ou existant à l’aide de la création WYSIWYG dans l’éditeur universel.


## Prérequis

* Vous disposez d’un compte GitHub et vous comprenez les concepts de base de Git.
* Vous comprenez les principes de base du HTML, du CSS et du JavaScript.
* Node/npm est installé pour le développement local.

## Créer un projet AEM préconfiguré avec le bloc de formulaires adaptatifs

Le modèle standard AEM Forms vous permet de prendre rapidement en main un projet AEM préconfiguré avec le bloc de formulaires adaptatifs. Il s’agit de la méthode la plus rapide et la plus simple pour respecter les bonnes pratiques relatives à AEM et passer directement à la création de vos formulaires.

### Prise en main du modèle de référentiel standard AEM Forms

1. Créez un référentiel GitHub pour votre projet AEM. Pour créer un référentiel :
   1. Accédez à [https://github.com/adobe-rnd/aem-boilerplate-forms](https://github.com/adobe-rnd/aem-boilerplate-forms).

      ![Modèle standard AEM Forms](/help/edge/docs/forms/assets/eds-form-boilerplate.png)
   1. Cliquez sur l’option **Utiliser ce modèle** et sélectionnez l’option **Créer un référentiel**.

      ![Création d’un référentiel à l’aide du modèle standard AEM Forms](/help/edge/docs/forms/assets/use-eds-form-template.png)

      L’écran **Créer un référentiel** s’ouvre.

   1. Dans l’écran **Créer un référentiel**, sélectionnez la personne **propriétaire** et spécifiez le **Nom du référentiel**. Adobe recommande de définir le référentiel sur **Public**. Ainsi, sélectionnez l’option **public** puis cliquez sur **Créer un référentiel**.

      ![Définition du référentiel sur public](/help/edge/docs/forms/assets/name-eds-repo.png)

1. Installez l’application GitHub AEM Code Sync sur votre référentiel. Pour l’installer :
   1. Accédez à [https://github.com/apps/aem-code-sync/installations/new](https://github.com/apps/aem-code-sync/installations/new).
   1. Sur l’écran **Installer AEM Code Sync**, sélectionnez l’option **Sélectionner uniquement les référentiels** et sélectionnez le référentiel nouvellement créé. Cliquez sur **Enregistrer**.

   ![Définition du référentiel sur public](/help/edge/docs/forms/assets/aem-code-sync-up.png)

1. Liez maintenant le référentiel GitHub que vous avez créé à l’aide du modèle standard AEM Forms à votre environnement de création de projet AEM. Pour le connecter :

   1. Accédez au référentiel GitHub que vous avez créé plus tôt à l’aide du modèle standard AEM Forms.
   1. Ouvrez le fichier **fstab.yaml** pour le modifier.

      ![ouvrir le fichier fstab.yaml](/help/edge/docs/forms/assets/open-fstab.png)

   1. Modifiez le fichier **fstab.yaml** pour mettre à jour le point de montage de votre projet. Remplacez l’URL par l’URL de votre instance de création AEM as a Cloud Service.

      `https://<aem-author>/bin/franklin.delivery/<owner>/<repository>/main`

      ![modifier le fichier fstab.yaml](/help/edge/docs/forms/assets/edit-fstab-file.png)

   1. Validez le fichier **fstab.yaml** mis à jour une fois que vous avez mis à jour la référence et que tout semble correct.

      ![valider les modifications](/help/edge/docs/forms/assets/commit-fstab-changes.png)

      Si vous rencontrez des problèmes de génération, consultez [Résolution des problèmes de génération dans GitHub](#troubleshooting-github-build-issues).

### Créer un projet AEM

Maintenant que vous disposez d’un projet GitHub, vous pouvez procéder à la création et à la publication d’un projet AEM sur l’instance de création AEM as a Cloud Service.

1. Pour créer un projet AEM :

   1. Connectez-vous à l’instance de création AEM as a Cloud Service et sélectionnez **Sites**.

      ![sélectionner des sites](/help/edge/assets/select-sites.png)

   1. Cliquez sur **Créer** > **Site à partir d’un modèle**.

      ![créer des sites](/help/edge/docs/forms/assets/create-sites.png)

   1. Sélectionnez le modèle de site Edge Delivery Services et cliquez sur **Suivant**.

      ![select-site-template](/help/edge/docs/forms/assets/select-site-template.png)

      >[!NOTE]
      >
      > * Si le modèle de site Edge Delivery Services n’est pas disponible sur votre instance de création, cliquez sur le bouton d’import pour charger le modèle.
      > * Vous pouvez télécharger les modèles de site Edge Delivery Services depuis [GitHub](https://github.com/adobe-rnd/aem-boilerplate-xwalk/releases).

   1. Saisissez les informations suivantes pour créer un projet AEM :
      * **Titre du site** : ajoutez un titre descriptif pour le site.
      * **Titre du site** : utilisez le `site-name` que vous avez défini à l’étape précédente.
      * **URL GitHub** : utilisez l’URL du projet GitHub que vous avez créé à l’étape précédente.

      ![créer un site AEM](/help/edge/docs/forms/assets/create-aem-site.png)

   1. La boîte de dialogue **Créer un site** s’affiche. Cliquez sur **OK**.

      ![cliquer sur ok](/help/edge/docs/forms/assets/click-ok-aem-site.png)

      En quelques minutes, votre projet AEM est créé.

   1. Accédez à votre projet AEM nouvellement créé dans la console Sites et cliquez sur **Modifier**.
Dans ce cas, la page `index.html` est utilisée à titre d’illustration.

      ![modifier le site AEM](/help/edge/docs/forms/assets/edit-site.png)

      Le projet AEM s’ouvre dans l’éditeur universel dans un nouvel onglet, permettant la création WYSIWYG. Vous pouvez désormais modifier votre projet AEM.

      ![Ouverture du site dans l’éditeur universel](/help/edge/docs/forms/assets/site-in-universal-editor.png)

1. Publier le projet AEM créé

   Une fois la modification du projet AEM terminée, publiez-le. Pour publier :

   1. Dans la console Sites, sélectionnez toutes les pages de projet AEM et cliquez sur **Publication rapide**.

      ![Publication d’un projet AEM Sites](/help/edge/docs/forms/assets/publish-sites.png)

   1. La boîte de dialogue de confirmation **Publication rapide** s’affiche. Cliquez sur **Publier** pour lancer le processus de publication.

      ![Boîte de dialogue de confirmation de la publication rapide](/help/edge/docs/forms/assets/quick-publish.png)

      Vous pouvez également publier vos pages de projet AEM directement à partir de l’interface d’utilisation de l’éditeur universel.

      ![Boîte de dialogue de confirmation de la publication rapide](/help/edge/docs/forms/assets/qui.png)

   Félicitations. Vous avez désormais un nouveau site web en cours d’exécution dans `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/`.

   * `<branch>` fait référence à la branche de votre référentiel GitHub.
   * `<repository>` indique votre référentiel GitHub.
   * `<owner>` fait référence au nom d’utilisateur ou d’utilisatrice de votre compte GitHub qui héberge votre référentiel GitHub.
   * `<site-name>` fait référence au nom du site que vous avez créé.

   Par exemple, si le nom de la branche est `main`, le référentiel est `edsforms`, la personne propriétaire est `wkndforms` et le `site-name` est `eds-forms`, le site web serait opérationnel à l’adresse `https://main--edsforms--wkndforms.aem.page/content/eds-forms/`.

   >[!NOTE]
   >
   > * Pour afficher la page `index.html` du projet AEM, utilisez l’URL suivante : `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/`.
   > * Pour afficher des pages autres que la `index page` du projet AEM, utilisez l’URL suivante : `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/<site-page-name>`.

Vous pouvez maintenant commencer à [créer des formulaires et les ajouter dans votre projet AEM](#add-edge-delivery-services-forms-to-aem-project).

## Ajouter un bloc de formulaires adaptatifs à votre projet AEM existant

Si vous disposez déjà d’un projet AEM, vous pouvez intégrer le bloc de formulaires adaptatifs à votre projet actuel pour commencer à créer le formulaire.

>[!NOTE]
>
>
> Cette étape s’applique aux projets créés avec [AEM Boilerplate XWalk](https://github.com/adobe-rnd/aem-boilerplate-xwalk). Si vous avez créé votre projet AEM à l’aide du [modèle standard AEM Forms](https://github.com/adobe-rnd/aem-boilerplate-forms), vous pouvez ignorer cette étape.

Pour effectuer l’intégration :

1. Accédez au dossier Référentiel du projet AEM sur votre système local.

1. Copiez et collez les dossiers et fichiers suivants du [modèle standard AEM Forms](https://github.com/adobe-rnd/aem-boilerplate-forms) dans votre projet AEM :

   * [bloc de formulaire](https://github.com/adobe-rnd/aem-boilerplate-forms/tree/main/blocks/form) dossier
   * Fichier [form-editor-support.js](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/form-editor-support.js)
   * Fichier [form-editor-support.css](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/form-editor-support.css)
1. Accédez au fichier `/scripts/editor-support.js` dans votre projet AEM et mettez-le à jour avec le fichier [editor-support.js dans AEM Forms Boilerplate](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/editor-support.js)
1. Accédez au `/models/_section.json` dans votre projet AEM et ajoutez « form » et « embed-adaptive-form » au tableau de composants de l’objet `filters` :

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

1. (Facultatif) Accédez à `/.eslintignore` dans votre projet AEM et ajoutez les lignes de code suivantes :

   ```
   blocks/form/rules/formula/*
   blocks/form/rules/model/*
   blocks/form/rules/functions.js
   scripts/editor-support.js
   scripts/editor-support-rte.js
   ```

1. (Facultatif) Accédez à `/.eslintrc.js` dans votre projet AEM et ajoutez les lignes de code ci-dessous dans l’objet `rules` :

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

1. Ouvrez le terminal et exécutez les commandes suivantes :

   ```
   npm i
   npm run build:json
   ```

   >[!NOTE]
   >
   > Avant d’envoyer les modifications au référentiel de votre projet AEM sur GitHub, assurez-vous que les fichiers `component-definition.json`, `component-models.json` et `component-filters.json` situés au niveau racine du projet AEM sont mis à jour avec les objets liés au formulaire.

1. Validez et envoyez ces modifications vers votre référentiel de projet AEM sur GitHub.

   <!--
    1. **Update ESLint configuration file**
    2. Navigate to the `../.eslintignore` file in your AEM Project and add the following line of codes to prevent errors related to the Form Block rule engine:
        
            blocks/form/rules/formula/*
            blocks/form/rules/model/*
       * [form-common](https://github.com/adobe-rnd/aem-boilerplate-forms/tree/main/models/form-common)  folder
       * [form-components](https://github.com/adobe-rnd/aem-boilerplate-forms/tree/main/models/form-components) folder
    
     3. **Update component definitions and models files**
       1. Navigate to the `../models/_component-definition.json` file in your AEM Project and update it with the changes from the [_component-definition.json file in the AEM Forms Boilerplate](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/models/_component-definition.json#L39-L48).
    
    3. Navigate to the `../models/_component-models.json` file in your AEM Project and update it with the changes from the [_component-models.json file in the AEM Forms Boilerplate](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/models/_component-models.json#L24-L26) -->

C’est terminé. Le bloc de formulaires adaptatifs fait désormais partie de votre projet AEM. Vous pouvez [commencer à créer et ajouter des formulaires à vos pages AEM](#add-edge-delivery-services-forms-to-aem-site-project).

## Créer des formulaires à l’aide de la création WYSIWYG

Vous pouvez ouvrir votre projet AEM dans l’éditeur universel pour la création WYSIWYG, où vous pouvez modifier le projet et ajouter la section Formulaire adaptatif pour inclure des formulaires Edge Delivery Services sur les pages de projet AEM.

1. Ajoutez la section Formulaire adaptatif à votre page Projet AEM. Pour ajouter :
   1. Accédez à votre projet AEM dans la console Sites, sélectionnez la page du site à modifier, puis cliquez sur **Modifier**. La page du projet AEM s’ouvre dans l’éditeur universel pour modification.
Dans ce cas, la page `index.html` est utilisée à titre d’illustration.
   1. Ouvrez l’arborescence de contenu et accédez à l’emplacement où vous souhaitez ajouter la section Formulaire adaptatif.
   1. Cliquez sur l’icône **[!UICONTROL Ajouter]** et sélectionnez le composant **[!UICONTROL Formulaire adaptatif]** dans la liste des composants.

   ![arborescence de contenu](/help/edge/docs/forms/assets/add-adaptive-form-block.png)

   La section Formulaire adaptatif est ajoutée. Vous pouvez maintenant commencer à ajouter des composants de formulaire à la page Projet AEM.

1. Ajoutez des composants de formulaire à la section Formulaire adaptatif ajoutée. Pour ajouter des composants de formulaire :
   1. Accédez à la section Formulaire adaptatif ajoutée dans l’arborescence de contenu.

      ![bloc de formulaire adaptatif ajouté](/help/edge/docs/forms/assets/adative-form-block.png)


   1. Cliquez sur l’icône **[!UICONTROL Ajouter]** et ajoutez les composants de votre choix dans la liste **Composants de formulaire adaptatif**.

      ![ajouter un composant](/help/edge/docs/forms/assets/add-component.png)

      Vous pouvez également faire glisser et déposer les composants de formulaire adaptatif requis, car l’éditeur universel offre une fonctionnalité intuitive de glisser-déposer.

   1. Sélectionnez le composant de formulaire adaptatif ajouté et mettez à jour ses propriétés à l’aide des **[!UICONTROL Propriétés]**.

      ![ouvrir les propriétés](/help/edge/docs/forms/assets/component-properties.png)

   1. Prévisualisez le formulaire.
La capture d’écran ci-dessous affiche le formulaire créé dans le projet AEM à l’aide de la création WYSIWYG :

      ![formulaire ajouté](/help/edge/docs/forms/assets/added-form-aem-sites.png)

      Une fois que l’aperçu est satisfaisant, l’utilisateur ou l’utilisatrice peut publier la page.

      >[!NOTE]
      >
      > Il est important de republier votre page de projet AEM après avoir apporté des modifications. Dans le cas contraire, les mises à jour ne sont pas visibles dans le navigateur.

1. Republiez la page du projet AEM.

   1. Cliquez sur **Publier** pour republier la page du projet AEM après avoir ajouté le formulaire.

      ![publier le formulaire](/help/edge/docs/forms/assets/publish-form.png)

   1. La boîte de dialogue de confirmation **Publier** s’affiche à l’écran. Cliquez sur **Publier** pour lancer la publication.

      ![publier le formulaire1](/help/edge/docs/forms/assets/publish-form1.png)

      Une fois que vous avez cliqué sur le bouton **Publier**, le message `Publish started successfully` s’affiche.

      ![publier le formulaire2](/help/edge/docs/forms/assets/publish-form2.png)

   Vous pouvez désormais afficher la page du projet AEM avec le formulaire Edge Delivery Services ajouté à l’adresse URL suivante :
   `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/`.

   Par exemple, si le nom de la branche est `main`, le référentiel est `edsforms`, la personne propriétaire est `wkndforms` et le nom du site est `eds-forms`, l’URL serait :
   `https://main--edsforms--wkndforms.aem.page/content/eds-forms/`

   ![page index](/help/edge/docs/forms/assets/publish-index-page.png)

Vous pouvez mettre en forme les formulaires Edge Delivery Services en modifiant les fichiers `.css` et `.js` dans le bloc de formulaires adaptatifs et en [configurant un environnement de développement AEM local](#set-up-local-aem-development-environment) pour afficher instantanément les modifications dans votre navigateur.

>[!NOTE]
>
> Vous pouvez également [créer un formulaire autonome dans l’éditeur universel et le publier dans Edge Delivery Services](/help/edge/docs/forms/universal-editor/create-forms.md).

## Configurer un environnement de développement AEM local

Vous pouvez configurer un environnement de développement AEM local pour développer localement des styles et des composants personnalisés. Pour rendre opérationnel un environnement de développement AEM local :

1. **Installez l’interface de ligne de commande AEM** : l’interface de ligne de commande AEM simplifie les tâches de développement. Installez-la globalement à l’aide de npm :

   ```Bash
       npm install -g @adobe/aem-cli
   ```

1. **Clonez votre projet GitHub** : clonez votre référentiel de projet AEM à partir de GitHub à l’aide de la commande suivante, en remplaçant &lt;owner> la personne propriétaire du référentiel et &lt;repo> le nom du référentiel :

   ```
   git clone https://github.com/<owner>/<repo>
   ```

1. **Démarrez votre environnement local** : accédez à votre répertoire de projet et déclenchez votre instance AEM locale à l’aide d’une seule commande :

   ```
   cd <repo>
   aem up
   ```

Vous pouvez apporter des modifications locales au dossier `blocks/form` du bloc de formulaires adaptatifs pour le style et le codage de vos formulaires. Modifiez les fichiers `.css` ou `.js` dans ce répertoire et les modifications seront visibles instantanément dans votre navigateur.

Une fois les modifications effectuées, utilisez les commandes Git pour les valider et les transmettre. Cela met à jour les environnements de prévisualisation et de production accessibles aux URL suivantes (remplacez les espaces réservés par les détails de votre projet) :

Aperçu : `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>`

Production : `https://<branch>--<repo>--<owner>.aem.live/content/<site-name>`


## Résolution des problèmes de génération dans GitHub

Assurez-vous d’avoir un processus de génération GitHub fluide en résolvant les problèmes potentiels :

* **Gérer les erreurs de lint :**
si vous rencontrez des erreurs de lint, vous avez la possibilité de les contourner. Ouvrez le fichier /package.json [Projet EDS] et modifiez le script « lint » de `"lint": "npm run lint:js && npm run lint:css"` en `"lint": "echo 'skipping linting for now'"`. Enregistrez le fichier et validez les modifications apportées à votre projet GitHub.

* **Erreur de chemin d&#39;accès du module Resolve:**
Si vous rencontrez l’erreur « Impossible de résoudre le chemin d’accès au module « /scripts/lib-franklin.js », accédez au fichier [Projet EDS]/blocks/forms/form.js. Mettez à jour l’instruction d’import en remplaçant le fichier lib-franklin.js par le fichier aem.js.

## Voir également

{{universal-editor-see-also}}
