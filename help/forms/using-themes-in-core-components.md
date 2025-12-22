---
title: Comment créer et utiliser des thèmes dans le Forms adaptatif ?
description: Vous pouvez utiliser les thèmes pour appliquer un style et fournir une identité visuelle à un formulaire adaptatif à l’aide des composants principaux. Vous pouvez partager un thème sur un certain nombre de formulaires adaptatifs.
keywords: thèmes de form builder, composants principaux de style des formulaires adaptatifs, créateur de thème de formulaire, style du formulaire adaptatif, personnalisation des thèmes, créer des thèmes de formulaire
feature: Adaptive Forms, Core Components
role: User, Developer
exl-id: 11c52b66-dbb1-4c47-a94d-322950cbdac1
source-git-commit: c0e0a700e85563ff65c703d5d20e6d6c1ff0651c
workflow-type: tm+mt
source-wordcount: '2897'
ht-degree: 29%

---

# Utilisation des thèmes pour appliquer un style au Forms adaptatif basé sur les composants principaux{#themes-for-af-using-core-components}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-core-components/create-or-customize-themes-for-adaptive-forms-core-components.html) |
| AEM as a Cloud Service | Cet article |

Vous pouvez créer et appliquer des thèmes pour appliquer un style à un formulaire adaptatif. Un thème contient des détails de style pour les composants et les panneaux. Ces styles incluent des propriétés telles que les couleurs d’arrière-plan, les couleurs d’état, la transparence, l’alignement et la taille. Lorsque vous appliquez un thème, le style spécifié se reflète sur les composants correspondants. Un thème est géré indépendamment sans référence à un formulaire adaptatif et peut être réutilisé dans plusieurs formulaires adaptatifs.

Dans cet article, nous expliquons comment concevoir des styles personnalisés pour le Forms adaptatif basé sur les composants principaux à l’aide de thèmes.

## Thèmes disponibles pour la mise en forme des composants principaux

Forms as a Cloud Service fournit les thèmes répertoriés ci-dessous pour le Forms adaptatif basé sur les composants principaux :

* [Thème Canevas](https://github.com/adobe/aem-forms-theme-canvas)
* [Thème WKND](https://github.com/adobe/aem-forms-theme-wknd)
* [Thème EASEL](https://github.com/adobe/aem-forms-theme-easel)

## Comprendre la structure des thèmes

Un thème est un package qui inclut des composants de style tels que le fichier CSS, les fichiers JavaScript et des ressources (comme des icônes) qui définissent le style de votre Forms adaptatif. Un thème de formulaire adaptatif suit une organisation spécifique composée des composants suivants :

* `src/theme.scss` : ce dossier comprend le fichier CSS qui a un large impact sur l’ensemble du thème. Il sert d’emplacement centralisé pour définir et gérer le style et le comportement de votre thème. En apportant des modifications à ce fichier, vous pouvez apporter des modifications appliquées de manière universelle à l’ensemble du thème, en influençant l’aspect et les fonctionnalités de vos pages de formulaires adaptatifs et d’AEM Sites.

* `src/site` : ce dossier contient des fichiers CSS qui sont appliqués à l’ensemble de la page d’un site AEM. Ces fichiers se composent de code et de styles qui affectent la fonctionnalité globale et la disposition de la page de votre site AEM. Toutes les modifications apportées ici sont répercutées sur toutes les pages de votre site. [Quand l’utiliser ?]

* `src/components` : les fichiers CSS de ce dossier sont conçus pour des composants principaux d’AEM individuels. Chaque dossier dédié d’un composant comprend un fichier `.scss` qui met en forme ce composant particulier dans un formulaire adaptatif. Par exemple, le fichier /src/components/accordion/_accordion.scss contient des informations de style pour le composant Accordéon de Forms adaptative.

  ![structure de thème basée sur les formulaires adaptatifs](/help/forms/assets/theme_structure.png)

* `src/resources` : ce dossier contient des fichiers statiques tels que des icônes, des logos et des polices. Ces ressources sont utilisées pour améliorer les éléments visuels et la conception globale de votre thème.

## Créer un thème

Forms as a Cloud Service fournit, les thèmes de style de formulaire adaptatif répertoriés ci-dessous pour le Forms adaptatif basé sur les composants principaux.

* [Thème Canevas](https://github.com/adobe/aem-forms-theme-canvas)
* [Thème WKND](https://github.com/adobe/aem-forms-theme-wknd)
* [Thème EASEL](https://github.com/adobe/aem-forms-theme-easel)

Vous pouvez [personnaliser l’un de ces thèmes pour créer un thème](#customize-a-theme-core-components).

![Workflow de personnalisation du thème](/help/forms/assets/workflow-of-customization-of-theme.png)

## Personnaliser un thème {#customize-a-theme-core-components}

La personnalisation d’un thème fait référence au processus de modification, de mise en forme et de personnalisation de l’aspect d’un thème. Lorsque vous personnalisez un thème, vous apportez des modifications à ses éléments de conception, à sa disposition, à ses couleurs, à sa typographie et parfois au code sous-jacent. Il vous permet de créer une apparence unique et personnalisée de votre site web ou de votre application tout en conservant la structure et les fonctionnalités de base fournies par le thème.

### Conditions préalables {#prerequisites-to-customize}

* Familiarisez-vous avec [la configuration d’un pipeline dans Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=fr#setup-pipeline) et des connaissances de base sur la configuration d’un pipeline vous permettent de gérer et de déployer efficacement vos personnalisations de thème.
* Découvrez comment [configurer un utilisateur avec le rôle de contributeur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/assign-profiles-aem.html?lang=fr). Comprendre comment configurer un utilisateur avec le rôle de contributeur vous permet d’accorder les autorisations nécessaires à la personnalisation du thème.
* Installez la dernière version d’[Apache Maven](https://maven.apache.org/download.cgi). Apache Maven est un outil d’automatisation de création couramment utilisé dans les projets Java™. L’installation de la dernière version vous garantit les dépendances nécessaires à la personnalisation du thème.
* Installez un éditeur de texte brut. Par exemple, Microsoft® Visual Studio Code. L’utilisation d’un éditeur de texte brut tel que Microsoft® Visual Studio Code fournit un environnement convivial pour la création et la modification de fichiers de thème.

### Configuration de votre environnement

* Installez la dernière version de pour activer les composants principaux de Forms adaptatif pour votre environnement AEM Cloud Service.
* Configurez un [pipeline de déploiement front-end](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/enable-frontend-pipeline-devops/create-frontend-pipeline.html) pour votre environnement Cloud Service. Vous pouvez également configurer le pipeline ultérieurement, ce qui vous offre la possibilité de hiérarchiser les tests et d’affiner le thème avant de configurer le pipeline de déploiement.

<!-- 
To deploy your themes to a Forms as a Cloud Service environment, first test theme on a local development environment to address any issues. Once the theme is tested, configure the front-end deployment pipeline, which is responsible for deploying the themes.

These themes are deployed to a Forms as a Cloud Service environment via the front-end pipeline. You can configure the pipeline later also, after testing the theme on a local development environment. 

-->

Après avoir pris connaissance des conditions préalables et configuré l’environnement de développement, vous êtes prêt à commencer à personnaliser ou à mettre en forme votre thème en fonction de vos besoins spécifiques.

### Personnaliser un thème {#steps-to-customize-a-theme-core-components}

La personnalisation d’un thème est un processus à plusieurs étapes. Pour personnaliser le thème, effectuez les étapes dans l’ordre indiqué :

1. [Cloner un thème](#download-a-theme-core-components)
1. [Définir le nom d’un thème](#set-name-of-theme)
1. [Personnaliser un thème](#customize-the-theme)
1. [Test d’un thème](#test-the-theme)
1. [Déploiement d’un thème](#deploy-the-theme)

Les exemples fournis dans le document sont basés sur le thème **Zone de travail**, mais il est important de noter que vous pouvez cloner n’importe quel thème et le personnaliser à l’aide des mêmes instructions. Ces instructions s’appliquent à n’importe quel thème, ce qui vous permet de modifier des thèmes en fonction de vos besoins spécifiques.

Commençons par un processus de création d’une expérience de marque pour votre Forms adaptative basée sur les composants principaux à l’aide des thèmes ?

#### &#x200B;1. Cloner un thème {#download-a-theme-core-components}

Pour cloner un thème pour les formulaires adaptatifs basés sur les composants principaux, choisissez l’un des thèmes suivants :

* [Thème Zone de travail](https://github.com/adobe/aem-forms-theme-canvas)
* [Thème WKND](https://github.com/adobe/aem-forms-theme-wknd)
* [Thème EASEL](https://github.com/adobe/aem-forms-theme-easel)

Pour cloner un thème, effectuez les instructions suivantes :

1. Ouvrez l’invite de commande ou la fenêtre de terminal dans votre environnement de développement local.

1. Exécutez la commande `git clone` pour cloner un thème.

   ```
      git clone [Path of Git Repository of the theme]
   ```

   Remplacez le [Chemin du référentiel Git du thème] par l’URL réelle du référentiel Git correspondant du thème

   Par exemple, pour cloner le thème Zone de travail, exécutez la commande suivante :

   ```
      git clone https://github.com/adobe/aem-forms-theme-canvas
   ```

   Une fois la commande exécutée, une copie locale du thème est disponible sur votre ordinateur dans le dossier `aem-forms-theme-canvas`.


#### &#x200B;2. Définir le nom d’un thème {#set-name-of-theme}

1. Ouvrez le dossier du thème dans votre IDE. Par exemple, pour ouvrir le dossier `aem-forms-theme-canvas` dans l’éditeur de code Visual Studio.

1. Accédez au dossier `aem-forms-theme-canvas`.

1. Exécutez la commande suivante :

   ```
      code .
   ```

   ![Ouvrez le dossier du thème dans un éditeur de texte brut](/help/forms/assets/aem-forms-theme-folder-in-vs-code.png)

   Le dossier s’ouvre dans Visual Studio Code.

1. Ouvrez le fichier `package.json` en mode d’édition.

1. Définissez les valeurs des attributs `name` et `version`.

   ![Image de modification du nom du thème de la zone de travail](/help/forms/assets/changename_canvastheme.png)

   >[!NOTE]
   >
   > * L’attribut name est utilisé pour identifier de manière unique le thème, et le nom spécifié est affiché dans l’onglet **Style** de l’assistant **Création de formulaire**.
   > * Vous avez la possibilité de sélectionner un nom pour votre thème en fonction de votre choix, par exemple `mytheme` ou `customtheme`. Cependant, dans ce cas, nous avons spécifié le nom comme `aem-forms-wknd-theme`.

1. Ouvrez le fichier `package-lock.json` en mode d’édition.
1. Définissez les valeurs des attributs `name` et `version`. Assurez-vous que les valeurs des attributs `name` et `version` du fichier `Package-lock`.json correspondent à celles du fichier `Package.json`.

   ![Image de modification du nom du thème de la zone de travail](/help/forms/assets/changename_canvastheme-package-lock.png)

1. (Facultatif) Ouvrez le fichier `ReadMe` pour modifier et mettre à jour le nom du thème.

   ![Image de modification du nom du thème de la zone de travail](/help/forms/assets/changename_canvastheme-readme-file.png)

1. Enregistrez et fermez les fichiers.

**Considérations lors de la définition du nom du thème**

* Il est obligatoire de supprimer le `@aemforms` du nom du thème dans `Package.json` fichier et `Package-lock.json` fichier . Si vous ne parvenez pas à supprimer `@aemforms` de votre nom de thème personnalisé, cela entraîne l’échec du pipeline front-end pendant le déploiement du thème.
* Il est recommandé de mettre à jour le `version` de thème dans `Package.json` fichier et `Package-lock.json` fichier pour refléter précisément les modifications et améliorations apportées à votre thème au fil du temps.
* Pour obtenir des informations importantes sur l’utilisation, les instructions d’installation et d’autres détails pertinents, il est recommandé de mettre à jour le nom du thème dans le fichier `ReadMe`.

#### &#x200B;3. Personnaliser un thème {#customize-the-theme}

Vous pouvez personnaliser des composants individuels ou apporter des modifications au niveau du thème à l’aide des variables globales d’un thème. Toute modification apportée aux variables globales a un impact sur tous les composants individuels. Par exemple, vous pouvez utiliser des variables globales pour modifier la couleur de bordure de tous les composants d’un formulaire adaptatif et une couleur de remplissage claire pour définir CTA (Call to action) à l’aide du composant Bouton :

* [Définir des styles de niveau de thème](#theme-customization-global-level)

* [Définir des styles de niveau de composant](#component-based-customization)

##### Définir des styles de niveau de thème{#theme-customization-global-level}

Le fichier `variable.scss` contient les variables globales du thème . En mettant à jour ces variables, vous pouvez apporter des modifications liées au style au niveau du thème. Pour appliquer des styles au niveau du thème, procédez comme suit :

1. Ouvrez le fichier `<your-theme-sources>/src/site/_variables.scss` en mode d’édition.
1. Modifiez la valeur de n’importe quelle propriété. Par exemple, la couleur d’erreur par défaut est `red`. Pour modifier la couleur d’erreur de `red` en `blue`, modifiez le code hexadécimal de couleur de la `$errorvariable`. Par exemple, `$error: #196ee5`.
1. Enregistrez et fermez le fichier.

   ![Modifier le thème](/help/forms/assets/edit_theme.png)

De même, vous pouvez utiliser la variable `variable.scss` pour définir la famille et le type de polices, les couleurs du thème et de la police, la taille de la police, l’espacement des thèmes, l’icône d’erreur, les styles de bordure du thème et d’autres variables ayant un impact sur plusieurs composants de formulaire adaptatif.

##### Définir des styles de niveau de composant {#component-based-customization}

Vous pouvez également modifier la police, la couleur, la taille et d’autres propriétés CSS d’un composant principal de formulaire adaptatif spécifique. Par exemple, bouton, case à cocher, conteneur, pied de page, etc. Vous pouvez mettre en forme un bouton ou une case à cocher en modifiant le fichier CSS du composant spécifique afin de l’aligner sur le style de votre entreprise. Pour personnaliser un style d’un composant :

1. Ouvrez le fichier `<your-theme-sources>/src/components/<component>/<component.scss>` pour le modifier. Par exemple, pour modifier la couleur de police du composant Bouton, ouvrez le fichier `<your-theme-sources>/src/components/button/button.scss`, .
1. Modifiez la valeur de n’importe quelle variable selon vos besoins. Par exemple, pour modifier la couleur du composant Bouton lorsque vous pointez avec la souris sur `green`, modifiez la valeur de la propriété `color: $white` dans la classe `cmp-adaptiveform-button__widget:hover` sur `#12B453` de code hexadécimal ou toute autre nuance de `green`. Le code final ressemble à ce qui suit :

   ```
   .cmp-adaptiveform-button__widget:hover {
   background: $dark-gray;
   color: #12B453;
   }
   ```

1. Enregistrez et fermez le fichier.

   ![Modifier la zone de texte du CSS](/help/forms/assets/edit_color_textbox.png)

   >[!NOTE]
   >
   > Lorsqu’un style est défini au niveau du thème et du composant, le style défini au niveau du composant est prioritaire.

#### &#x200B;4. Tester un thème personnalisé {#test-the-theme}

Pour prévisualiser et tester les modifications dans l’environnement local et personnaliser le thème en fonction des exigences des différents composants d’AEM, procédez comme suit :

* 4.1 [Configuration d’un environnement local pour les tests](#rename-env-file-theme-folder)
* 4.2 [Tester le thème à l’aide de l’environnement local](#start-a-local-proxy-server)

##### 4.1. Configuration d’un environnement local pour les tests {#rename-env-file-theme-folder}

1. Ouvrez le dossier du thème dans votre IDE. Par exemple, ouvrez le dossier `aem-forms-theme-canvas` dans l’éditeur Visual Studio Code.
1. Renommez le fichier `env_template` en fichier `.env` dans le dossier du thème et ajoutez les paramètres suivants :

   ```
   * **AEM url**
   AEM_URL=https://[author-instance] 
   
   * **AEM Adaptive form name**
   AEM_ADAPTIVE_FORM=Form_name
   
   * **AEM proxy port**
   AEM_PROXY_PORT=7000
   ```

   Par exemple, l’URL du formulaire est `http://localhost:4502/editor.html/content/forms/af/contactusform.html`. Les valeurs de :

   * AEM_URL = `http://localhost:4502/`
   * AEM_ADAPTIVE_FORM = `contactusform`

1. Enregistrez le fichier.

   ![Structure du thème de zone de travail](/help/forms/assets/env-file-canvas-theme.png)

##### 4.2 Tester le thème en utilisant un environnement local {#start-a-local-proxy-server}

1. Accédez à la racine du dossier du thème. Dans ce cas, le nom du dossier du thème est `aem-forms-theme-canvas`.
1. Ouvrez l’invite de commande ou le terminal.
1. Exécutez `npm install` pour installer les dépendances.
1. Exécutez `npm run live` pour prévisualiser le formulaire avec le thème mis à jour dans votre navigateur local.

   >[!NOTE]
   >
   > Si une erreur se produit lors de l&#39;exécution de la commande `npm run live`, exécutez les commandes suivantes avant `npm run live` commande :
   >
   > * `npm install parcel --save-dev`
   > * `npm i @parcel/transformer-sass`

Il s’agit d’un déploiement à chaud. Ainsi, chaque fois que vous apportez des modifications et enregistrez les fichiers `_variables.scss` et `button.scss`, le serveur sélectionne automatiquement les modifications et prévisualise la dernière sortie. La ligne `[Browsersync] File event [change]` signifie que le serveur a reconnu les dernières modifications et qu’il déploie les modifications dans l’environnement local.

![Proxy browsersync](/help/forms/assets/browser_sync.png)

Après avoir suivi les exemples de mise en forme d’un formulaire adaptatif (composants principaux) au niveau du thème et du composant pour les personnalisations du thème, les messages d’erreur d’un formulaire adaptatif sont modifiés en couleur `blue`, tandis que la couleur du libellé du composant Bouton devient `green` lorsque vous passez la souris dessus.

**Aperçu du style de niveau de thème**

![Exemple : couleur d’erreur définie sur bleu](/help/forms/assets/theme-level-changes.png)

**Aperçu du style au niveau du composant**

![Exemple : la couleur de survol est définie sur le vert](/help/forms/assets/button-customization.png)

La personnalisation d’un thème permet de concevoir les styles personnalisés du Forms adaptatif basé sur les composants principaux en fonction des exigences de l’entreprise.

###### Tester le thème pour les formulaires hébergés dans un environnement Cloud Service

Vous pouvez également tester le thème du formulaire adaptatif hébergé sur votre instance AEM Forms as a Cloud Service. Pour configurer et définir l’environnement local pour le test des thèmes avec le Forms adaptatif hébergé sur l’instance cloud, procédez comme suit :

1. Ouvrez le dossier du thème dans votre IDE. Par exemple, ouvrez le dossier `aem-forms-theme-canvas` dans l’éditeur Visual Studio Code.
1. Renommez le fichier `env_template` en fichier `.env` et ajoutez les paramètres suivants :

   ```
   * **AEM url**
   AEM_URL=https://[author-instance] 
   
   * **AEM Adaptive form name**
   AEM_ADAPTIVE_FORM=Form_name
   
   * **AEM proxy port**
   AEM_PROXY_PORT=7000
   ```

   Par exemple, l’URL du formulaire dans l’environnement cloud est `https://author-XXXX.adobeaemcloud.com/editor.html/content/forms/af/contactusform.html`. Les valeurs de :

   * AEM_URL = `https://author-XXXX-cmstg.adobeaemcloud.com/`
   * AEM_ADAPTIVE_FORM = `contactusform`
1. Enregistrez le fichier.
1. Créez un utilisateur local ou une utilisatrice locale.

   >[!NOTE]
   >
   > Pour créer un utilisateur local ou une utilisatrice locale :
   >
   > * Accédez à **[!UICONTROL Accueil AEM]** > **[!UICONTROL Outils]** > **[!UICONTROL Sécurité]** > **[!UICONTROL Utilisateurs]** .
   > * Assurez-vous que l’utilisateur ou l’utilisatrice est membre du groupe `forms-users`.

1. Accédez à la racine du dossier du thème. Dans ce cas, le nom du dossier du thème est `aem-forms-theme-canvas`.
1. Exécutez `npm run live` et vous êtes redirigé vers un navigateur local.
1. Cliquez sur `SIGN IN LOCALLY (ADMIN TASKS ONLY)` et connectez-vous à l’aide des informations d’identification de l’utilisateur local.

Vous pouvez prévisualiser le formulaire adaptatif avec les dernières modifications. Une fois que vous êtes satisfait des modifications apportées à un dossier de thème, déployez le thème dans votre environnement AEM Cloud Service à l’aide du pipeline front-end.

#### &#x200B;5. Déploiement d’un thème {#deploy-the-theme}

Pour déployer le thème dans votre environnement Cloud Service à l’aide du pipeline front-end :

* 5.1 [Créer un référentiel pour le thème](#create-a-new-theme-repo)
* 5.2 [Envoyez les modifications au référentiel](#committing-the-changes)
* 5.3 [Exécution du pipeline front-end](#run-a-frontend-pipeline)

##### 5.1 Création d’un référentiel pour le thème{#create-a-new-theme-repo}

Vous avez besoin d’un référentiel pour déployer le thème. Connectez-vous à votre référentiel [AEM Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#accessing-git) et ajoutez un nouveau référentiel pour votre thème.

1. Créez un référentiel pour un thème en cliquant sur le **[!UICONTROL Référentiels]** > **[!UICONTROL Ajouter un référentiel]**.

   ![Créer un nouveau référentiel de thème](/help/forms/assets/createrepo_canvastheme.png).


1. Spécifiez le **Nom du référentiel** dans la boîte de dialogue **Ajouter un référentiel**. Par exemple, le nom fourni est `custom-canvas-theme-repo`.
1. Cliquez sur **[!UICONTROL Enregistrer]**.

   ![Ajoutez un référentiel de thème pour la zone de travail](/help/forms/assets/addcanvasthemerepo.png).

1. Cliquez sur **[!UICONTROL Copier l’URL du référentiel]** pour copier l’URL du référentiel.

   ![URL du thème de la zone de travail](/help/forms/assets/copyurl_canvastheme.png).

   >[!NOTE]
   > 
   >* Vous pouvez utiliser un référentiel unique pour plusieurs thèmes.
   >* Pour déployer différents thèmes, vous devez créer des pipelines front-end distincts.
   >* Par exemple, vous pouvez utiliser le même référentiel, comme `custom-canvas-theme-repo`, pour le thème Zone de travail, le thème WKND et le thème EASEL. Cependant, pour déployer les thèmes, vous devez créer des pipelines front-end distincts. Les futures personnalisations d’un thème spécifique sont déployées à l’aide du pipeline front-end correspondant.

##### 5.2. Envoyez les modifications au référentiel {#committing-the-changes}

Désormais, envoyez les modifications au référentiel de thèmes de votre Cloud Service AEM Forms.

1. Accédez à la racine du dossier du thème.  Dans ce cas, le nom du dossier du thème est `aem-forms-theme-canvas`.
1. Ouvrez l’invite de commande ou le terminal.
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

Le thème est déployé à l’aide du [pipeline front-end](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/enable-frontend-pipeline-devops/create-frontend-pipeline.html). Pour déployer le thème, effectuez les étapes suivantes :

1. Connectez-vous à votre référentiel AEM Cloud Manager.
1. Cliquez sur le bouton **[!UICONTROL Ajouter]** dans la section **[!UICONTROL Pipelines]**.
1. Sélectionnez **[!UICONTROL Ajouter un pipeline hors production]** ou **[!UICONTROL Ajouter un pipeline de production]** en fonction de l’environnement Cloud Service. Par exemple, ici, l’option **[!UICONTROL Ajouter un pipeline de production]** est sélectionnée.
1. Dans la boîte de dialogue **[!UICONTROL Ajouter un pipeline de production]** qui fait partie des étapes **[!UICONTROL Configuration]**, indiquez le nom de votre pipeline. Par exemple, le nom du pipeline est `customcanvastheme`.
1. Cliquez sur **[!UICONTROL Continuer]**.
1. Sélectionnez les options **[!UICONTROL Déploiement ciblé]** > **[!UICONTROL Code front-end]** dans
les étapes de **[!UICONTROL Source Code]**.
1. Sélectionnez les valeurs **[!UICONTROL Référentiel]** et **[!UICONTROL Branche Git]** comportant vos dernières modifications. Par exemple, ici, le nom du référentiel sélectionné est `custom-canvas-theme-repo` et la branche Git est `main`.
1. Sélectionnez le **[!UICONTROL Emplacement du code]** comme `/`, si vos modifications sont présentes dans le dossier racine.
1. Cliquez sur **[!UICONTROL Enregistrer]**.
   ![créer un pipeline front-end](/help/forms/assets/canvas-theme-frontendpipeline.gif)

   Une fois la configuration du pipeline terminée, la carte call-to-action est mise à jour.

   >[!NOTE]
   >
   > Pour vous assurer que votre pipeline front-end n’échoue pas dans Cloud Manager, [définissez la version de Node.js sur 20](#set-the-nodejs-vesrion-to-20).

1. Cliquez avec le bouton droit sur le pipeline créé.
1. Cliquez sur **[!UICONTROL Exécuter]** .

   ![exécuter un pipeline](/help/forms/assets/canvas-theme-run-pipeline.png)

Une fois la création terminée, le thème est disponible au niveau de l’instance de création pour être utilisé. Elle apparaît sous l’onglet **[!UICONTROL Style]** de l’assistant de création de formulaire adaptatif, lors de la création d’un formulaire adaptatif.

![thème personnalisé disponible sous l’onglet style](/help/forms/assets/custom-theme-style-tab.png)

Le thème personnalisé permet de créer une expérience de marque pour le Forms adaptatif basé sur les composants principaux.

## Appliquer un thème à un formulaire adaptatif {#using-theme-in-adaptive-form}

Les étapes à suivre pour appliquer un thème à un formulaire adaptatif sont les suivantes :

1. Connectez-vous à votre instance de création AEM Forms.

1. Sélectionnez **Adobe Experience Manager** > **Formulaires** > **Formulaires et documents**.

1. Cliquez sur **Créer** > **Formulaires adaptatifs**. L’assistant de création de formulaires adaptatifs s’ouvre.

1. Sélectionnez le modèle de composant principal dans l’onglet **Source**.
1. Sélectionnez le thème dans l’onglet **Style**.
1. Cliquez sur **Créer**.

Les thèmes de formulaire adaptatif sont utilisés dans le cadre d’un modèle de formulaire adaptatif pour définir le style lors de la création d’un formulaire adaptatif.

## Définissez la version de Node.js sur 20.

Pour définir la version de Node.js sur 20 à l’aide de la configuration de pipeline :

1. Accédez à la section **Pipelines** et localisez votre pipeline front-end.
2. Sur le côté droit du pipeline, cliquez sur le menu à trois points **⋯** et dans la liste déroulante, sélectionnez **Afficher/Modifier les variables**.
3. Dans la boîte de dialogue **Configuration des variables**, renseignez les champs comme suit :
   * **NAME** - NODE_VERSION
   * **VALUE** - 20
   * **ÉTAPE APPLIQUÉE** - Créer
   * **TYPE** - Variable
4. Cliquez sur **Enregistrer** pour appliquer la configuration.

![configuration du pipeline](/help/forms/assets/pipeline-config.png)

## Bonnes pratiques {#best-practices}

* **Éviter les ressources d’un autre thème**.

  Lorsque vous modifiez un thème, vous pouvez parcourir et ajouter des actifs (tels que des images) d’autres thèmes. Par exemple, vous pouvez modifier l’arrière-plan d’une page. Par exemple, lorsque vous sélectionnez la **[!UICONTROL Page]** ![bouton de modification](assets/edit-button.png) > **[!UICONTROL Arrière plan]** > **[!UICONTROL Ajoutez]** > **[!UICONTROL Image]**, une boîte de dialogue s’affiche et vous permet de parcourir et d’ajouter des images dans l’autre thème.

  Vous pouvez rencontrer des problèmes avec votre thème actuel si un actif est ajouté à partir d’un autre thème et l’autre thème est déplacé ou supprimé. Nous vous recommandons d’éviter de parcourir les actifs d’autres thèmes et de les ajouter.

* **Modification de la largeur de disposition du panneau conteneur**

  Il n’est pas recommandé de modifier la largeur de disposition du panneau conteneur. Lorsque vous spécifiez la largeur d’un panneau de contenu, il devient statique et ne s’adapte pas aux différents affichages.

## Questions fréquentes {#faq}

**Question :** Quelle personnalisation est prioritaire lorsque vous effectuez des personnalisations dans un dossier de thème au niveau global et au niveau des composants ?

**Réponse :** lorsque des personnalisations sont effectuées au niveau global et au niveau des composants, la personnalisation au niveau des composants est prioritaire.

<!--

## See next

* [Set layout of forms for different screen sizes and device types](/help/sites-cloud/authoring/page-editor/responsive-layout.md)
* [Generate Document of Record for Adaptive Forms (Core Components](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)
* [Create an Adaptive Forms with Repeatable sections](/help/forms/create-forms-repeatable-sections.md)
* [Sample themes templates and form data models](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html)

-->


## Voir également {#see-also}

{{see-also}}

* [Définir la disposition des formulaires pour différentes tailles d’écran et différents types d’appareils](/help/sites-cloud/authoring/page-editor/responsive-layout.md)
* [Génération d’un document d’enregistrement pour le Forms adaptatif (composants principaux)](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)
* [Création d’un Forms adaptatif avec des sections répétables](/help/forms/create-forms-repeatable-sections.md)
* [Exemples de modèles de thèmes et de modèles de données de formulaire](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html?lang=fr)
