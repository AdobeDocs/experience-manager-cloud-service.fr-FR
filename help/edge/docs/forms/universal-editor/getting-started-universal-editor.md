---
title: Prise en main des Edge Delivery Services pour AEM Forms dans l’éditeur universel - Tutoriel de développement
description: Ce tutoriel vous permet de prendre en main un nouveau projet Adobe Experience Manager Forms (AEM). Dans dix à vingt minutes, vous aurez créé votre propre Forms Edge Delivery Services dans l’éditeur universel.
feature: Edge Delivery Services
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
source-git-commit: c27b8e413c060de601a72a669d86c4add2a4167d
workflow-type: tm+mt
source-wordcount: '1623'
ht-degree: 22%

---


# Prise en main des Edge Delivery Services pour AEM Forms à l’aide de l’éditeur universel (WYSIWYG)

À l’ère numérique, les formulaires conviviaux sont essentiels pour toutes les organisations. Les Forms Edge Delivery Services sont créées à l’aide de l’éditeur universel, qui offre des fonctionnalités WYSIWYG (ce que vous voyez est ce que vous obtenez). Il fournit une interface moderne et intuitive pour une création de formulaire efficace.

AEM Forms fournit un bloc, appelé bloc de Forms adaptatif, pour vous aider à créer facilement des Forms de Edge Delivery Services afin de capturer et stocker des données. Vous pouvez [créer un projet AEM préconfiguré avec le bloc de Forms adaptatif](#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) ou [ajouter le bloc de Forms adaptatif à un projet AEM existant](#add-adaptive-forms-block-to-your-existing-aem-project).

Ce tutoriel vous guide tout au long de la création, de la prévisualisation et de la publication de votre propre formulaire avec un projet de site Adobe Experience Manager nouveau ou existant à l’aide de la création WYSIWYG dans l’éditeur universel.


## Prérequis

* Vous disposez d’un compte GitHub et vous comprenez les concepts de base de Git.
* Vous disposez d’un compte Google ou Microsoft SharePoint.
* Vous comprenez les principes de base du HTML, du CSS et du JavaScript.
* Node/npm est installé pour le développement local.

## Créer un projet AEM préconfiguré avec le bloc de formulaires adaptatifs

Le modèle standard AEM Forms vous permet de prendre rapidement en main un projet AEM préconfiguré avec le bloc de formulaires adaptatifs. Il s’agit du moyen le plus simple et le plus rapide de suivre les bonnes pratiques d’AEM et de vous lancer directement dans la création de vos formulaires.

### Prise en main du modèle de référentiel standard AEM Forms

1. Créez un référentiel GitHub pour votre projet AEM. Pour créer un référentiel :
   1. Accédez à [https://github.com/adobe-rnd/aem-boilerplate-forms](https://github.com/adobe-rnd/aem-boilerplate-forms).

      ![Modèle standard AEM Forms](/help/edge/docs/forms/assets/eds-form-boilerplate.png)
   1. Cliquez sur l’option **Utiliser ce modèle** et sélectionnez l’option **Créer un référentiel**.

      ![Création d’un référentiel à l’aide du modèle standard AEM Forms](/help/edge/docs/forms/assets/use-eds-form-template.png)

      L’écran **Créer un référentiel** s’ouvre.

   1. Sur l’écran **Créer un référentiel**, sélectionnez le **propriétaire** et spécifiez **Nom du référentiel** . Adobe recommande de définir le référentiel sur **Public**. Ainsi, sélectionnez l’option **public** puis cliquez sur **Créer un référentiel**.

      ![Définition du référentiel sur public](/help/edge/docs/forms/assets/name-eds-repo.png)

1. Installez l’application GitHub AEM Code Sync sur votre référentiel. Pour l’installer :
   1. Accédez à [https://github.com/apps/aem-code-sync/installations/new](https://github.com/apps/aem-code-sync/installations/new).
   1. Sur l’écran **Installer la synchronisation du code AEM**, sélectionnez l’option **Sélectionner uniquement les référentiels** et sélectionnez le référentiel que vous venez de créer. Cliquez sur **Enregistrer**.

   ![Définition du référentiel sur public](/help/edge/docs/forms/assets/aem-code-sync-up.png)

1. Liez maintenant le référentiel GitHub que vous avez créé à l’aide d’AEM Forms Boilerplate à votre environnement de création de projet AEM. Pour le connecter :

   1. Accédez au référentiel GitHub que vous avez créé plus tôt à l’aide du modèle standard AEM Forms.
   1. Ouvrez le fichier **fstab.yaml** pour le modifier.

      ![ouvrez le fichier fstab.yaml](/help/edge/docs/forms/assets/open-fstab.png)

   1. Modifiez le fichier **fstab.yaml** pour mettre à jour le point de montage de votre projet. Remplacez l’URL par l’URL de votre instance de création AEM as a Cloud Service.
      `https://<aem-author>/bin/franklin.delivery/<owner>/<repository>/main`

      ![modifier le fichier fstab.yaml](/help/edge/docs/forms/assets/edit-fstab-file.png)

   1. Validez le fichier **fstab.yaml** mis à jour, une fois que vous avez mis à jour la référence et que tout semble correct.

      ![valider les modifications](/help/edge/docs/forms/assets/commit-fstab-changes.png)

      Si vous rencontrez des problèmes de génération, consultez [Résolution des problèmes de génération dans GitHub](#troubleshooting-github-build-issues).

### Création d’un projet AEM

Maintenant que vous disposez d’un projet GitHub, vous pouvez procéder à la création et à la publication d’un projet AEM sur l’instance de création AEM as a Cloud Service.
1. Pour créer un projet AEM, procédez comme suit :

   1. Connectez-vous à l’instance de création AEM as a Cloud Service et sélectionnez **Sites**.

      ![sélectionner des sites](/help/edge/assets/select-sites.png)

   1. Cliquez sur **Créer** > **Site à partir du modèle**.

      ![create-sites](/help/edge/docs/forms/assets/create-sites.png)

   1. Sélectionnez le modèle Site Edge Delivery Services et cliquez sur **Suivant**.

      ![select-site-template](/help/edge/docs/forms/assets/select-site-template.png)

      >[!NOTE]
      >
      > * Si le modèle de site Edge Delivery Services n’est pas disponible sur votre instance de création, cliquez sur le bouton Importer pour charger le modèle.
      > * Vous pouvez télécharger les modèles de site Edge Delivery Services depuis [GitHub](https://github.com/adobe-rnd/aem-boilerplate-xwalk/releases).

   1. Saisissez les informations suivantes pour créer un projet AEM :
      * **Titre du site** : ajoutez un titre descriptif pour le site.
      * **Titre du site** - Utilisez la `site-name` que vous avez définie à l’étape précédente.
      * **URL GitHub** : utilisez l’URL du projet GitHub que vous avez créé à l’étape précédente.

      ![création d’un site AEM](/help/edge/docs/forms/assets/create-aem-site.png)

   1. La boîte de dialogue **Créer un site** s’affiche. Cliquez sur **OK**.

      ![cliquez sur ok](/help/edge/docs/forms/assets/click-ok-aem-site.png)

      En quelques minutes, votre nouveau projet AEM est créé.

   1. Accédez à votre projet AEM nouvellement créé dans la console Sites et cliquez sur **Modifier**.
Dans ce cas, la page `index.html` est utilisée à titre d’illustration.

      ![modifier le site AEM](/help/edge/docs/forms/assets/edit-site.png)

      Le projet AEM s’ouvre dans l’éditeur universel dans un nouvel onglet, permettant la création dans WYSIWYG. Vous pouvez maintenant modifier votre projet AEM.

      ![Ouverture du site dans l’éditeur universel](/help/edge/docs/forms/assets/site-in-universal-editor.png)

1. Publish du projet AEM créé

   Une fois la modification du projet AEM terminée, publiez-le. Pour publier :

   1. Dans la console Sites, sélectionnez toutes les pages de projet AEM et cliquez sur **Quick Publish**.

      ![Publication d’un projet AEM Sites](/help/edge/docs/forms/assets/publish-sites.png)

   1. La boîte de dialogue de confirmation **Quick Publish** s’affiche. Cliquez sur **Publish** pour lancer le processus de publication.

      ![Boîte de dialogue de confirmation Quick Publish](/help/edge/docs/forms/assets/quick-publish.png)

      Vous pouvez également publier vos pages de projet AEM directement à partir de l’interface utilisateur de l’éditeur universel.

      ![Boîte de dialogue de confirmation Quick Publish](/help/edge/docs/forms/assets/qui.png)

   Félicitations. Vous avez désormais un nouveau site web en cours d’exécution dans `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/`.

   * `<branch>` fait référence à la branche de votre référentiel GitHub.
   * `<repository>` indique votre référentiel GitHub.
   * `<owner>` fait référence au nom d’utilisateur ou d’utilisatrice de votre compte GitHub qui héberge votre référentiel GitHub.
   * `<site-name>` fait référence au nom du site que vous avez créé.

   Par exemple, si le nom de la branche est `main`, le référentiel est `edsforms`, le propriétaire est `wkndforms` et le `site-name` est `eds-forms`, le site web est opérationnel à l’adresse `https://main--edsforms--wkndforms.aem.page/content/eds-forms/`

   >[!NOTE]
   >
   > * Pour afficher la page `index.html` du projet AEM, utilisez l’URL suivante : `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/`
   > * Pour afficher des pages autres que la `index page` du projet AEM, utilisez l’URL suivante : `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/<site-page-name>`

Vous pouvez maintenant commencer à [créer et ajouter des formulaires à votre projet AEM](#add-edge-delivery-services-forms-to-aem-project).

## Ajouter un bloc de Forms adaptatif à votre projet AEM existant

Si vous disposez déjà d’un projet AEM, vous pouvez intégrer le bloc de formulaires adaptatifs à votre projet actuel pour commencer à créer le formulaire.

>[!NOTE]
>
>
> Cette étape s’applique aux projets créés à l’aide du [modèle standard AEM](https://github.com/adobe-rnd/aem-boilerplate-xwalk). Si vous avez créé votre projet AEM à l’aide du [modèle standard AEM Forms](https://github.com/adobe-rnd/aem-boilerplate-forms), vous pouvez ignorer cette étape.

Pour effectuer l’intégration :

1. Clonez le référentiel GitHub de bloc de Forms adaptatif : [https://github.com/adobe-rnd/aem-boilerplate-forms](https://github.com/adobe-rnd/aem-boilerplate-forms) sur votre ordinateur.
1. Dans le dossier téléchargé, recherchez le dossier `blocks/form` et copiez-le.
1. Clonez le référentiel GitHub de votre projet AEM sur votre ordinateur.
1. Accédez maintenant au dossier `blocks` dans votre référentiel de projet AEM local et collez-y le dossier de formulaire copié.
1. Validez et envoyez ces modifications au référentiel de votre projet AEM sur GitHub.

C’est terminé. Le bloc de Forms adaptatif fait désormais partie de votre projet AEM. Vous pouvez [commencer à créer et à ajouter des formulaires à votre projet AEM](#add-edge-delivery-services-forms-to-aem-site-project).

## Créer AEM Forms à l’aide de WYSIWYG

Vous pouvez ouvrir votre projet AEM dans l’éditeur universel pour la création WYSIWYG, où vous pouvez modifier le projet et ajouter la section Formulaire adaptatif pour inclure des formulaires Edge Delivery Services sur les pages de projet AEM.

1. Ajoutez la section Formulaire adaptatif à votre page Projet AEM. Pour ajouter :
   1. Accédez à votre projet AEM dans la console Sites et cliquez sur **Modifier**. La page Projet AEM s’ouvre dans l’éditeur universel en vue d’être modifiée.
Dans ce cas, la page `index.html` est utilisée à titre d’illustration.
   1. Ouvrez l’arborescence de contenu et accédez à l’emplacement où vous souhaitez ajouter la section Formulaire adaptatif .
   1. Cliquez sur l’icône **[!UICONTROL Ajouter]** et sélectionnez le composant **[!UICONTROL Formulaire adaptatif]** dans la liste des composants.

   ![arborescence de contenu](/help/edge/docs/forms/assets/add-adaptive-form-block.png)

   La section Formulaire adaptatif est ajoutée à l’emplacement spécifié. Vous pouvez maintenant commencer à ajouter des composants de formulaire à la page Projet AEM.

1. Ajoutez des composants de formulaire à la section de formulaire adaptatif ajoutée. Pour ajouter des composants de formulaire :
   1. Accédez à la section Formulaire adaptatif ajoutée dans l’arborescence de contenu.

      ![bloc de formulaire adaptatif ajouté](/help/edge/docs/forms/assets/adative-form-block.png)


   1. Cliquez sur l’icône **[!UICONTROL Ajouter]** et ajoutez les composants de votre choix dans la liste **Composants de formulaire adaptatif**.

      ![ajouter un composant](/help/edge/docs/forms/assets/add-component.png)

      Vous pouvez également effectuer un glisser-déposer des composants Forms adaptatifs requis, car l’éditeur universel offre une fonctionnalité intuitive de glisser-déposer.

   1. Sélectionnez le composant de formulaire adaptatif ajouté pour mettre à jour ses propriétés à l’aide de **[!UICONTROL Propriétés]**.

      ![ouvrir les propriétés](/help/edge/docs/forms/assets/component-properties.png)

      La capture d’écran ci-dessous affiche le formulaire créé dans le projet AEM à l’aide de la création WYSIWYG :

      ![ formulaire ajouté ](/help/edge/docs/forms/assets/added-form-aem-sites.png)

   >[!NOTE]
   >
   > Il est important de republier votre page de projet AEM après avoir apporté des modifications. Dans le cas contraire, les mises à jour ne sont pas visibles dans le navigateur.

1. Republiez la page du projet AEM.

   1. Cliquez sur **Publish** pour republier la page du projet AEM après avoir ajouté le formulaire.

      ![formulaire de publication](/help/edge/docs/forms/assets/publish-form.png)

   1. La boîte de dialogue de confirmation **Publish** s’affiche à l’écran. Cliquez sur **Publish** pour lancer la publication.

      ![publication du formulaire1](/help/edge/docs/forms/assets/publish-form1.png)

      Une fois que vous avez cliqué sur le bouton **Publish**, le message `Publish started successfully` s’affiche.

      ![publication du formulaire 2](/help/edge/docs/forms/assets/publish-form2.png)

   Vous pouvez désormais afficher la page du projet AEM avec le formulaire des Edge Delivery Services ajouté à l’adresse URL suivante :
   `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/`.

   Par exemple, si le nom de la branche est `main`, le référentiel est `edsforms`, le propriétaire est `wkndforms` et le nom du site est `eds-forms`, l’URL serait :
   `https://main--edsforms--wkndforms.aem.page/content/eds-forms/`

   ![page index](/help/edge/docs/forms/assets/publish-index-page.png)

Vous pouvez mettre en forme le Forms Edge Delivery Services en modifiant les fichiers `.css` et `.js` dans le bloc de Forms adaptatif et en [configurant un environnement de développement AEM local](#set-up-local-aem-development-environment) pour afficher instantanément les modifications dans votre navigateur.

## Configuration de l’environnement de développement AEM local

Vous pouvez configurer un environnement de développement AEM local pour développer localement des styles et des composants personnalisés. Pour être opérationnel avec un environnement de développement AEM local :

1. **Installation de l’interface de ligne de commande AEM** : l’interface de ligne de commande AEM simplifie les tâches de développement. Installez-la globalement à l’aide de npm :

   ```Bash
       npm install -g @adobe/aem-cli
   ```

1. **Clonez votre projet GitHub** : clonez votre référentiel de projet AEM à partir de GitHub à l’aide de la commande suivante, en remplaçant <owner> la personne propriétaire du référentiel et <repo> le nom du référentiel :

   ```
   git clone https://github.com/<owner>/<repo>
   ```

1. **Démarrer votre environnement local** : accédez au répertoire de votre projet et démarrez votre instance AEM locale à l’aide d’une seule commande :

   ```
   cd <repo>
   aem up
   ```

Vous pouvez apporter des modifications locales au dossier `blocks/form` Bloc de Forms adaptatif pour le style et le codage de vos formulaires. Modifiez les fichiers `.css` ou `.js` de ce répertoire pour que les modifications soient immédiatement répercutées dans votre navigateur.

Une fois les modifications effectuées, utilisez les commandes Git pour les valider et les transmettre. Cela met à jour vos environnements de prévisualisation et de production, accessibles aux URL suivantes (remplacez les espaces réservés par les détails de votre projet) :

Prévisualisation : `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>`
Production : `https://<branch>--<repo>--<owner>.aem.live/content/<site-name>`


## Résolution des problèmes de génération dans GitHub

Assurez-vous d’avoir un processus de génération GitHub fluide en résolvant les problèmes potentiels :

* **Gérer les erreurs de lint :**
si vous rencontrez des erreurs de lint, vous avez la possibilité de les contourner. Ouvrez le fichier /package.json [Projet EDS] et modifiez le script « lint » de `"lint": "npm run lint:js && npm run lint:css"` en `"lint": "echo 'skipping linting for now'"`. Enregistrez le fichier et validez les modifications apportées à votre projet GitHub.

<!-- * **Resolve Module Path Error:**
    If you encounter the error "Unable to resolve path to module "'../../scripts/lib-franklin.js'", navigate to the [EDS Project]/blocks/forms/form.js file. Update the import statement by replacing the lib-franklin.js file with the aem.js file. -->
