---
title: Comment créer et utiliser des thèmes dans Forms adaptatif ?
description: Vous pouvez utiliser des thèmes pour mettre en forme et fournir une identité visuelle à un formulaire adaptatif à l’aide de composants principaux. Vous pouvez partager un thème sur un certain nombre de formulaires adaptatifs.
exl-id: 11c52b66-dbb1-4c47-a94d-322950cbdac1
source-git-commit: 7a65aa82792500616f971df52b8ddb6d893ab89d
workflow-type: tm+mt
source-wordcount: '2698'
ht-degree: 17%

---

# Thèmes dans Forms adaptatif {#themes-for-af-using-core-components}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-core-components/create-or-customize-themes-for-adaptive-forms-core-components.html) |
| AEM as a Cloud Service | Cet article |

Vous pouvez créer et appliquer des thèmes pour mettre en forme un formulaire adaptatif. Un thème contient des détails de style pour les composants et les panneaux. Ces styles incluent les propriétés telles que les couleurs d’arrière-plan, les couleurs d’état, la transparence, l’alignement et la taille. Lorsque vous appliquez un thème, le style spécifié se reflète sur les composants correspondants. Un thème est géré indépendamment sans référence à un formulaire adaptatif et peut être réutilisé dans plusieurs Forms adaptatives.

## Thèmes disponibles

Forms comme le fournit Cloud Service, les thèmes répertoriés ci-dessous pour le Forms adaptatif basé sur les composants principaux :

* [Thème Canevas](https://github.com/adobe/aem-forms-theme-canvas)
* [Thème WKND](https://github.com/adobe/aem-forms-theme-wknd)
* [Thème EASEL](https://github.com/adobe/aem-forms-theme-easel)

## Comprendre la structure des thèmes

Un thème est un module qui englobe le fichier CSS, les fichiers JavaScript et les ressources (comme les icônes) qui définissent le style de votre Forms adaptatif. Un thème de formulaire adaptatif suit une organisation spécifique composée des composants suivants :

* `src/theme.scss`: ce dossier comprend le fichier CSS qui a un large impact sur l’ensemble du thème. Il sert d’emplacement centralisé pour définir et gérer le style et le comportement de votre thème. En apportant des modifications à ce fichier, vous pouvez apporter des modifications appliquées de manière universelle à l’ensemble du thème, en influençant l’aspect et les fonctionnalités de vos pages Forms adaptatives et AEM Sites.

* `src/site`: ce dossier contient des fichiers CSS qui sont appliqués à l’ensemble de la page d’un site AEM. Ces fichiers se composent de code et de styles qui affectent la fonctionnalité globale et la disposition de la page de votre site AEM. Toutes les modifications apportées ici sont répercutées sur toutes les pages de votre site. [Quand l’utiliser ?]

* `src/components`: les fichiers CSS de ce dossier sont conçus pour des composants principaux d’AEM individuels. Chaque dossier dédié d’un composant comprend une `.scss` qui met en forme ce composant particulier dans un formulaire adaptatif. Par exemple, le fichier /src/components/accordion/_accordion.scss contient des informations de style pour le composant d’accordéon Adaptive Forms.

  ![structure de thème basée sur un formulaire adaptatif](/help/forms/assets/theme_structure.png)

* `src/resources`: ce dossier contient des fichiers statiques tels que des icônes, des logos et des polices. Ces ressources sont utilisées pour améliorer les éléments visuels et la conception globale de votre thème.

## Création d’un thème

Forms comme le fournit Cloud Service, les thèmes répertoriés ci-dessous pour le Forms adaptatif basé sur les composants principaux.

* [Thème Canevas](https://github.com/adobe/aem-forms-theme-canvas)
* [Thème WKND](https://github.com/adobe/aem-forms-theme-wknd)
* [Thème EASEL](https://github.com/adobe/aem-forms-theme-easel)

Vous pouvez [personnaliser n’importe lequel de ces thèmes pour créer un nouveau thème ;](#customize-a-theme-core-components).

![Workflow de personnalisation de thème](/help/forms/assets/workflow-of-customization-of-theme.png)

## Personnalisation d’un thème {#customize-a-theme-core-components}

La personnalisation d’un thème fait référence au processus de modification et de personnalisation de l’aspect d’un thème. Lorsque vous personnalisez un thème, vous modifiez ses éléments de conception, sa mise en page, ses couleurs, sa typographie, et parfois le code sous-jacent. Il vous permet de créer un aspect unique et personnalisé pour votre site web ou votre application tout en conservant la structure et les fonctionnalités de base fournies par le thème.

### Conditions préalables requises {#prerequisites-to-customize}

* Se familiariser avec [configuration d’un pipeline dans Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=fr#setup-pipeline) et posséder des connaissances de base sur la configuration d’un pipeline vous aide à gérer et déployer efficacement vos personnalisations de thème.
* Découvrez comment [configuration d’un utilisateur avec le rôle de contributeur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/assign-profiles-aem.html?lang=fr). Comprendre comment configurer un utilisateur avec le rôle de contributeur vous permet d’accorder les autorisations nécessaires à la personnalisation du thème.
* Installez la dernière version d’[Apache Maven.](https://maven.apache.org/download.cgi) Apache Maven est un outil d’automatisation de génération couramment utilisé pour les projets Java™. L’installation de la dernière version vous garantit les dépendances nécessaires à la personnalisation du thème.
* Installez un éditeur de texte brut. Par exemple, Microsoft® Visual Studio Code. L’utilisation d’un éditeur de texte brut tel que Microsoft® Visual Studio Code fournit un environnement convivial pour la modification et la modification de fichiers de thème.

### Configuration de votre environnement

* [Activation des composants principaux de Forms adaptatif](/help/forms/enable-adaptive-forms-core-components.md)  pour votre environnement de développement local et de Cloud Service.
* Configurer [pipeline de déploiement front-end](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/enable-frontend-pipeline-devops/create-frontend-pipeline.html) pour votre environnement de Cloud Service. Vous pouvez également configurer le pipeline ultérieurement, ce qui vous donne la possibilité de prioriser le test et l’affinage du thème avant de configurer le pipeline de déploiement.

<!-- 
To deploy your themes to a Forms as a Cloud Service environment, first test theme on a local development environment to address any issues. Once the theme is tested, configure the front-end deployment pipeline, which is responsible for deploying the themes.

These themes are deployed to a Forms as a Cloud Service environment via the front-end pipeline. You can configure the pipeline later also, after testing the theme on a local development environment. 

-->

Après avoir appris les conditions préalables requises et configuré l’environnement de développement, vous êtes bien préparé à commencer à personnaliser votre thème en fonction de vos besoins spécifiques.

### Personnalisation d’un thème {#steps-to-customize-a-theme-core-components}

La personnalisation d’un thème est un processus à plusieurs étapes. Pour personnaliser le thème, effectuez les étapes dans l’ordre indiqué :

1. [Clonage d’un thème](#download-a-theme-core-components)
1. [Nom d’un thème](#set-name-of-theme)
1. [Personnalisation d’un thème](#customize-the-theme)
1. [Test d’un thème](#test-the-theme)
1. [Déploiement d’un thème](#deploy-the-theme)

Les exemples fournis dans le document reposent sur la variable **Canevas** mais il est important de noter que vous pouvez cloner n’importe quel thème et le personnaliser en suivant les mêmes instructions. Ces instructions s’appliquent à n’importe quel thème, ce qui vous permet de modifier des thèmes en fonction de vos besoins spécifiques.

#### 1. Cloner un thème {#download-a-theme-core-components}

Pour cloner un thème pour Forms adaptatif basé sur les composants principaux, choisissez l’un des thèmes suivants :

* [Thème Canevas](https://github.com/adobe/aem-forms-theme-canvas)
* [Thème WKND](https://github.com/adobe/aem-forms-theme-wknd)
* [Thème EASEL](https://github.com/adobe/aem-forms-theme-easel)

Pour cloner un thème, suivez les instructions suivantes :

1. Ouvrez l’invite de commande ou la fenêtre de terminal dans votre environnement de développement local.

1. Exécutez la variable `git clone` pour cloner un thème.

   ```
      git clone [Path of Git Repository of the theme]
   ```

   Remplacez la variable [Chemin du référentiel Git du thème] avec l’URL réelle du référentiel Git correspondant du thème

   Par exemple, pour cloner le thème Zone de travail, exécutez la commande suivante :

   ```
      git clone https://github.com/adobe/aem-forms-theme-canvas
   ```

   Une fois la commande exécutée correctement, vous disposez d’une copie locale du thème disponible sur votre ordinateur dans le  `aem-forms-theme-canvas` dossier.


#### 2. Nom d’un thème {#set-name-of-theme}

1. Ouvrez le dossier de thème dans un éditeur de texte brut. Par exemple, pour ouvrir la `aem-forms-theme-canvas` dans l’éditeur de code Visual Studio.

1. Accédez au dossier `aem-forms-theme-canvas`.

1. Exécutez la commande suivante :

   ```
         code .
   ```

   ![Ouvrez le dossier de thème dans un éditeur de texte brut.](/help/forms/assets/aem-forms-theme-folder-in-vs-code.png)

   Le dossier s’ouvre dans le code Visual Studio.

1. Ouvrez le fichier `package.json` en mode d’édition.

1. Définissez les valeurs de la variable `name` et `description` attributs.

   L’attribut name est utilisé pour identifier de manière unique le thème, par exemple &quot;aem-forms-wknd-theme&quot; et s’affiche dans la variable **Style** de **Assistant de création de formulaires**. L’attribut description fournit des détails supplémentaires sur le thème, y compris son objectif et les scénarios pour lesquels il est conçu. Vous pouvez également spécifier la version, la description et la licence du thème.

1. Enregistrez et fermez le fichier.

![Image de changement du nom du thème de la zone de travail](/help/forms/assets/changename_canvastheme.png)


#### 3. Personnaliser un thème {#customize-the-theme}

Vous pouvez personnaliser des composants individuels ou effectuer des modifications au niveau du thème à l’aide de variables globales d’un thème. Toutes les modifications apportées aux variables globales affectent tous les composants individuels. Vous pouvez, par exemple, utiliser des variables globales pour modifier la couleur de bordure de tous les composants d’un formulaire adaptatif et une couleur de fond claire pour définir CTA (Appel à l’action) à l’aide du composant de bouton :

* [Définition des styles de thème](#theme-customization-global-level)

* [Définition des styles de composant](#component-based-customization)

##### Définition des styles de thème{#theme-customization-global-level}

La variable `variable.scss` contient les variables globales du thème. En mettant à jour ces variables, vous pouvez apporter des modifications liées au style au niveau du thème. Pour appliquer des styles au niveau du thème, procédez comme suit :

1. Ouvrez le fichier `<your-theme-sources>/src/site/_variables.scss` en mode d’édition.
1. Modifiez la valeur de n’importe quelle propriété. Par exemple, la couleur d’erreur par défaut est `red`. Pour modifier la couleur d’erreur de `red` to `blue`, modifiez le code hexadécimal de couleur de la propriété `$errorvariable`. Par exemple, `$error: #196ee5`.
1. Enregistrez et fermez le fichier.

   ![Modifier le thème](/help/forms/assets/edit_theme.png)

De même, vous pouvez utiliser la variable `variable.scss` pour définir la famille et le type de polices, les couleurs du thème et de la police, la taille de la police, l’espacement des thèmes, l’icône d’erreur, les styles de bordure du thème et d’autres variables ayant un impact sur plusieurs composants de formulaire adaptatif.

##### Définition des styles de composant {#component-based-customization}

Vous pouvez également modifier la police, la couleur, la taille et d’autres propriétés CSS d’un composant principal de formulaire adaptatif spécifique. Par exemple, bouton, case à cocher, conteneur, pied de page, etc. Vous pouvez mettre en forme un bouton ou une case à cocher en modifiant le fichier CSS du composant spécifique afin de l’aligner sur le style de votre entreprise. Pour personnaliser le style d’un composant :

1. Ouvrir le fichier `<your-theme-sources>/src/components/<component>/<component.scss>` pour modification. Par exemple, pour modifier la couleur de police du composant Bouton, ouvrez le `<your-theme-sources>/src/components/button/button.scss`, fichier .
1. Modifiez la valeur de n’importe quelle variable selon vos besoins. Par exemple, pour modifier la couleur du composant de bouton lorsque vous passez la souris sur `green`, modifiez la valeur de la variable `color: $white` dans la propriété `cmp-adaptiveform-button__widget:hover` classe en code hexadécimal `#12B453` ou toute autre nuance de `green`. Le code final ressemble à ce qui suit :

   ```
   .cmp-adaptiveform-button__widget:hover {
   background: $dark-gray;
   color: #12B453;
   }
   ```

1. Enregistrez et fermez le fichier.

   ![Modifier la zone de texte du CSS](/help/forms/assets/edit_color_textbox.png)

   >
   >
   > Lorsqu’un style est défini au niveau du thème et du composant, le style défini au niveau du composant est prioritaire.

#### 4. Tester un thème personnalisé {#test-the-theme}

Pour prévisualiser et tester les modifications dans l’environnement local et personnaliser le thème en fonction des exigences des différents composants d’AEM, procédez comme suit :

* 4.1 [Configuration de l’environnement local pour les tests](#rename-env-file-theme-folder)
* 4.2 [Tester le thème à l’aide de l’environnement local](#start-a-local-proxy-server)

##### 4.1. Configuration d’un environnement local à des fins de test {#rename-env-file-theme-folder}

1. Ouvrez le dossier de thème dans un éditeur de texte brut. Par exemple, ouvrez le `aem-forms-theme-canvas` dans l’éditeur de code Visual Studio.
1. Renommez la variable `env_template` vers `.env` dans le dossier theme et ajoutez les paramètres suivants :

   ```
   * **AEM url**
   AEM_URL=https://[author-instance] 
   
   * **AEM Adaptive form name**
   AEM_ADAPTIVE_FORM=Form_name
   
   * **AEM proxy port**
   AEM_PROXY_PORT=7000
   ```

   Par exemple, l’URL du formulaire est `http://localhost:4502/editor.html/content/forms/af/contactusform.html`. Ainsi, les valeurs de :

   * AEM_URL = `http://localhost:4502/`
   * AEM_ADAPTIVE_FORM = `contactusform`

1. Enregistrez le fichier.

   ![Structure du thème de zone de travail](/help/forms/assets/env-file-canvas-theme.png)

##### 4.2 Test du thème à l’aide de l’environnement local {#start-a-local-proxy-server}

1. Accédez à la racine du dossier de thème. Dans ce cas, le nom du dossier de thème est `aem-forms-theme-canvas`.
1. Ouvrez l’invite de commandes ou le terminal.
1. Exécuter `npm install` pour installer les dépendances.
1. Exécuter `npm run live` pour prévisualiser le formulaire avec le thème mis à jour dans votre navigateur local.

   >[!NOTE]
   >
   > Si une erreur se produit lors de l’exécution de la variable `npm run live` , exécutez les commandes suivantes avant `npm run live` command :
   >
   > * `npm install parcel --save-dev`
   > * `npm i @parcel/transformer-sass`

C&#39;est un déploiement brûlant. Ainsi, chaque fois que vous apportez des modifications et enregistrez la variable `_variables.scss` et `button.scss` fichiers, le serveur sélectionne automatiquement les modifications et prévisualise la dernière sortie. La ligne `[Browsersync] File event [change]` signifie que le serveur a reconnu les dernières modifications et qu’il déploie les modifications dans l’environnement local.

![Proxy browsersync](/help/forms/assets/browser_sync.png)

Après avoir suivi les exemples fournis aux niveaux de thème et de composant pour les personnalisations de thème, les messages d’erreur d’un formulaire adaptatif sont modifiés en `blue` tandis que la couleur de l’étiquette du composant de bouton est remplacée par `green` au survol.

**Prévisualiser le style du niveau du thème**

![Exemple : couleur d’erreur définie sur bleu](/help/forms/assets/theme-level-changes.png)

**Aperçu du style au niveau du composant**

![Exemple : couleur de survol définie sur vert](/help/forms/assets/button-customization.png)

###### Tester le thème pour les formulaires hébergés dans un environnement de Cloud Service

Vous pouvez également tester le thème du formulaire adaptatif hébergé sur votre instance as a Cloud Service AEM Forms. Pour configurer et définir l’environnement local pour tester les thèmes avec la Forms adaptative hébergée sur l’instance cloud, procédez comme suit :

1. Ouvrez le dossier de thème dans un éditeur de texte brut. Par exemple, ouvrez le `aem-forms-theme-canvas` dans l’éditeur de code Visual Studio.
1. Renommez la variable `env_template` vers `.env` et ajoutez les paramètres suivants :

   ```
   * **AEM url**
   AEM_URL=https://[author-instance] 
   
   * **AEM Adaptive form name**
   AEM_ADAPTIVE_FORM=Form_name
   
   * **AEM proxy port**
   AEM_PROXY_PORT=7000
   ```

   Par exemple, l’URL du formulaire dans l’environnement cloud est `https://author-XXXX.adobeaemcloud.com/editor.html/content/forms/af/contactusform.html`. Ainsi, les valeurs de :

   * AEM_URL = `https://author-XXXX-cmstg.adobeaemcloud.com/`
   * AEM_ADAPTIVE_FORM = `contactusform`
1. Enregistrez le fichier.
1. Créez un utilisateur local.

   >[!NOTE]
   >
   > Pour créer un utilisateur local :
   >
   > * Accédez à **[!UICONTROL Accueil AEM]** > **[!UICONTROL Outils]** > **[!UICONTROL Sécurité]** > **[!UICONTROL Utilisateurs]** .
   > * Assurez-vous que l’utilisateur est membre du `forms-users` groupe.

1. Accédez à la racine du dossier de thème. Dans ce cas, le nom du dossier de thème est `aem-forms-theme-canvas`.
1. Exécuter `npm run live` et vous êtes redirigé vers un navigateur local.
1. Cliquez sur `SIGN IN LOCALLY (ADMIN TASKS ONLY)` et se connecter à l’aide des informations d’identification de l’utilisateur local.

Vous pouvez prévisualiser le formulaire adaptatif avec les dernières modifications. Une fois que vous êtes satisfait des modifications effectuées dans un dossier de thèmes, déployez le thème dans votre environnement AEM Cloud Service à l’aide du pipeline frontal.

#### 5. Déployer un thème {#deploy-the-theme}

Pour déployer le thème dans votre environnement de Cloud Service à l’aide du pipeline frontal :

* 5.1 [Création d’un référentiel pour le thème](#create-a-new-theme-repo)
* 5.2 [Envoyez les modifications au référentiel.](#committing-the-changes)
* 5.3 [Exécution du pipeline front-end](#run-a-frontend-pipeline)

##### 5.1 Création d’un référentiel pour le thème{#create-a-new-theme-repo}

Vous avez besoin d’un référentiel pour déployer le thème. Connectez-vous à [Référentiel AEM Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#accessing-git) et ajoutez un nouveau référentiel pour votre thème.

1. Créez un référentiel pour le thème en cliquant sur **[!UICONTROL Référentiels]** > **[!UICONTROL Ajouter un référentiel]**.

   ![Créer un nouveau référentiel de thème](/help/forms/assets/createrepo_canvastheme.png).


1. Spécifiez la variable **Nom du référentiel** dans le **Ajouter un référentiel** de la boîte de dialogue Par exemple, le nom fourni est `custom-canvas-theme-repo`.
1. Cliquez sur **[!UICONTROL Enregistrer]**.

   ![Ajoutez un référentiel de thème pour la zone de travail](/help/forms/assets/addcanvasthemerepo.png).

1. Cliquez sur **[!UICONTROL Copier l’URL du référentiel]** pour copier l’URL du référentiel.

   ![URL du thème de la zone de travail](/help/forms/assets/copyurl_canvastheme.png).

   >[!NOTE]
   > 
   > * Vous pouvez utiliser un seul référentiel pour plusieurs thèmes.
   > * Pour déployer différents thèmes, vous devez créer des pipelines front-end distincts.
   >* Par exemple, vous pouvez utiliser le même référentiel, comme `custom-canvas-theme-repo`, pour le thème Canevas, le thème WKND et le thème EASEL. Toutefois, pour déployer les thèmes, vous devez créer des pipelines front-end distincts. Les futures personnalisations pour un thème spécifique sont déployées à l’aide du pipeline front-end correspondant.

##### 5.2. Envoyez les modifications au référentiel. {#committing-the-changes}

Maintenant, envoyez les modifications au référentiel de thème de votre Cloud Service AEM Forms. .

1. Accédez à la racine du dossier de thème.  Dans ce cas, le nom du dossier de thème est `aem-forms-theme-canvas`.
1. Ouvrez l’invite de commandes ou le terminal.
1. Exécutez la commande suivante dans l’ordre indiqué :

   ```
   git remote add [alias-name-for-repository] [URL of repository]
   git add .
   git commit
   git push [name-for-createdrepository]
   ```

   Par exemple :

   ```
   git remote add canvascloudthemerepo https://git.cloudmanager.adobe.com/stage-aemformsdev/customcanvastheme/
   git add .
   git commit
   git push canvascloudthemerepo 
   ```

   ![Modifications validées](/help/forms/assets/cmd_git_push.png)



##### 5.3 Exécution du pipeline front-end {#run-a-frontend-pipeline}

Le thème est déployé à l’aide de la fonction [pipeline front-end.](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/enable-frontend-pipeline-devops/create-frontend-pipeline.html). Pour déployer le thème, procédez comme suit :

1. Connectez-vous à votre référentiel AEM Cloud Manager.
1. Cliquez sur **[!UICONTROL Ajouter]** à partir du bouton **[!UICONTROL Pipelines]** .
1. Sélectionner **[!UICONTROL Ajout d’un pipeline hors production]** ou **[!UICONTROL Ajout d’un pipeline de production]** selon l’environnement du Cloud Service. Par exemple, ici, la variable **[!UICONTROL Ajout d’un pipeline de production]** est sélectionnée.
1. Dans le **[!UICONTROL Ajout d’un pipeline de production]** dans la boîte de dialogue **[!UICONTROL Configuration]** , indiquez le nom de votre pipeline. Par exemple, le nom du pipeline est `customcanvastheme`.
1. Cliquez sur **[!UICONTROL Continuer]**.
1. Sélectionnez la variable **[!UICONTROL Déploiement ciblé]** > le **[!UICONTROL Code front-end]** , dans la variable **[!UICONTROL Code source]** étapes.
1. Sélectionnez la variable **[!UICONTROL Référentiel]** et la variable **[!UICONTROL Branche Git]** qui présentent vos dernières modifications. Par exemple, ici, le nom du référentiel sélectionné est `custom-canvas-theme-repo` et la branche Git est `main`.
1. Sélectionnez la variable **[!UICONTROL Emplacement du code]** as `/`, si vos modifications sont présentes dans le dossier racine.
1. Cliquez sur **[!UICONTROL Enregistrer]**.
   ![création d’un pipeline front-end](/help/forms/assets/canvas-theme-frontendpipeline.gif)

   Une fois la configuration du pipeline terminée, la carte d’appel à l’action est mise à jour.

1. Cliquez avec le bouton droit sur le pipeline créé.
1. Cliquez sur **[!UICONTROL Exécuter]** .

   ![run-a-pipeline](/help/forms/assets/canvas-theme-run-pipeline.png)

Une fois la génération terminée, le thème est disponible dans l’instance d’auteur pour l’utilisation. Il apparaît sous le **[!UICONTROL Style]** dans l’assistant de création de formulaire adaptatif, lors de la création d’un formulaire adaptatif.

![thème personnalisé disponible sous l’onglet Style](/help/forms/assets/custom-theme-style-tab.png)

## Application d’un thème à un formulaire adaptatif {#using-theme-in-adaptive-form}

Les étapes pour appliquer un thème à un formulaire adaptatif sont les suivantes :

1. Connectez-vous à votre instance de création AEM Forms.

1. Appuyez sur **Adobe Experience Manager** > **Formulaires** > **Formulaires et documents**.

1. Cliquez sur **Créer** > **Formulaires adaptatifs**. L’assistant de création de formulaires adaptatifs s’ouvre.

1. Sélectionnez le modèle de composant principal dans l’onglet **Source**.
1. Sélectionnez le thème dans le **Style** .
1. Cliquez sur **Créer**.

Les thèmes de formulaire adaptatif sont utilisés dans le cadre d’un modèle de formulaire adaptatif pour définir le style lors de la création d’un formulaire adaptatif.

## Bonnes pratiques {#best-practices}

* **Éviter les ressources d’un autre thème**.

  Lorsque vous modifiez un thème, vous pouvez parcourir et ajouter des actifs (tels que des images) d’autres thèmes. Par exemple, vous pouvez modifier l’arrière-plan d’une page. Par exemple, lorsque vous sélectionnez la **[!UICONTROL Page]** ![bouton de modification](assets/edit-button.png) > **[!UICONTROL Arrière plan]** > **[!UICONTROL Ajoutez]** > **[!UICONTROL Image]**, une boîte de dialogue s’affiche et vous permet de parcourir et d’ajouter des images dans l’autre thème.

  Vous pouvez rencontrer des problèmes avec votre thème actuel si un actif est ajouté à partir d’un autre thème et l’autre thème est déplacé ou supprimé. Nous vous recommandons d’éviter de parcourir les actifs d’autres thèmes et de les ajouter.

* **Modification de la largeur de disposition du panneau conteneur**

  Il n’est pas recommandé de modifier la largeur de disposition du panneau conteneur. Lorsque vous spécifiez la largeur d’un panneau de contenu, il devient statique et ne s’adapte pas aux différents affichages.

* **Utiliser l’éditeur de formulaires ou l’éditeur de thèmes pour travailler sur l’en-tête et le pied de page**.

  Utilisez l’éditeur de thèmes si vous souhaitez mettre en forme l’en-tête et le pied de page à l’aide d’options de style telles que le style de police, l’arrière-plan et la transparence.
Si vous souhaitez fournir des informations comme une image de logo, le nom de l’entreprise dans l’en-tête et des informations de copyright dans le pied de page, utilisez les options de l’éditeur de formulaires.

## Questions fréquentes  {#faq}

**Q :** Quelle personnalisation est la priorité lorsque vous effectuez des personnalisations dans un dossier de thème au niveau global et au niveau des composants ?

**Réponse :** Lorsque des personnalisations sont effectuées au niveau global et au niveau des composants, la personnalisation au niveau des composants est prioritaire.

## Voir suivant

* [Définir la disposition des formulaires pour différentes tailles d’écran et différents types d’appareils](/help/sites-cloud/authoring/features/responsive-layout.md)
* [Générer un document d’enregistrement pour les Forms adaptatives (composants principaux)](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)
* [Création d’un Forms adaptatif avec des sections répétables](/help/forms/create-forms-repeatable-sections.md)
* [Exemples de modèles de thèmes et de modèles de données de formulaire](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html)


## Article connexe {#related-article}

* [Activation des composants principaux de Forms adaptatif dans l’environnement de développement as a Cloud Service et local d’AEM Forms](/help/forms/enable-adaptive-forms-core-components.md)
* [Création d’un formulaire adaptatif basé sur des composants principaux autonomes](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components.html?lang=fr)
