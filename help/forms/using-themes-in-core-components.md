---
title: Création et utilisation des thèmes
description: Vous pouvez utiliser des thèmes pour styliser et fournir une identité visuelle à un formulaire adaptatif à l’aide de composants principaux. Vous pouvez partager un thème sur un certain nombre de formulaires adaptatifs.
source-git-commit: e3fa30d5be29b4070a09873e8ca20036a788486a
workflow-type: tm+mt
source-wordcount: '1669'
ht-degree: 20%

---


# Présentation des thèmes de formulaire adaptatif à l’aide des composants principaux {#introduction-to-themes-for-af-using-core-components}

Vous pouvez créer et appliquer des thèmes pour styliser un formulaire adaptatif à l’aide de composants principaux. Un thème contient des détails de style pour les composants et les panneaux. Ces styles incluent les propriétés telles que les couleurs d’arrière-plan, les couleurs d’état, la transparence, l’alignement et la taille. Lorsque vous appliquez un thème, le style spécifié se reflète sur les composants correspondants. Le thème est géré indépendamment sans référence à un formulaire adaptatif.

Lorsque vous [créer un formulaire adaptatif](/help/forms/creating-adaptive-form.md) à l’aide des composants principaux, les thèmes d’usine apparaissent sous **Style** . Par défaut, seule la variable **Canevas** est disponible.

>[!NOTE]
>
>Un thème de formulaire adaptatif ne doit pas être confondu avec [Modèles de formulaires adaptatifs.](/help/forms/template-editor.md) Les thèmes de formulaire adaptatif contiennent uniquement les informations de style d’un formulaire adaptatif. Les modèles de formulaire adaptatif définissent la structure du formulaire et le contenu initial et contiennent un thème afin de permettre la création de [Formulaire adaptatif.](/help/forms/creating-adaptive-form.md)

## Utilisation du thème Zone de travail dans les Forms adaptatives à l’aide des composants principaux {#using-theme-in-adaptive-form}

Les étapes à suivre pour appliquer un thème à un formulaire adaptatif sont les suivantes :

1. Connectez-vous à votre instance d’auteur AEM Forms.

1. Appuyer **Adobe Experience Manager** > **Forms** > **Forms et documents**.

1. Cliquez sur **Créer** > **Forms adaptatif**. L’assistant de création de formulaire adaptatif s’ouvre.

1. Sélectionnez le modèle de composant principal dans le **Source** .

   >[!NOTE]
   >
   > Lorsque vous créez un formulaire adaptatif avec des composants principaux, le thème Zone de travail s’affiche sous l’onglet Style . Il s’agit du seul thème d’usine disponible en ce moment. Mais vous pouvez modifier le thème à votre convenance et l’enregistrer pour une utilisation ultérieure en configurant un pipeline frontal.

1. Sélectionnez le thème Zone de travail dans la **Style** .
1. Cliquez sur **Créer**.

Les thèmes de formulaire adaptatif sont utilisés dans le cadre d’un modèle de formulaire adaptatif pour définir le style lors de la création d’un formulaire adaptatif.

## Personnalisation du thème {#customizing-theme}

Pour personnaliser un thème,

* [configuration d’un pipeline dans Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#setup-pipeline)
* Configurez un utilisateur avec la variable [rôle de contributeur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/assign-profiles-aem.html).
* Vous devriez avoir une [connaissance de base de Git](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=en#accessing-git) et référentiels Git Cloud Service.

Pour personnaliser un thème Canevas :
1. [Clonage du thème Zone de travail](#1-download-canvas-theme-download-canvas-theme)
1. [Comprendre la structure du thème](#2-understand-structure-of-the-canvas-theme-structure-of-canvas-theme)
1. [Changez de nom dans package.json et package_lock.json](#changename-packagelock-packagelockjson)
1. [Créez le ](#3-create-the-env-file-in-a-theme-folder-creating-env-file-theme-folder)
1. [Démarrer le serveur proxy local.](#4-start-a-local-proxy-server-starting-a-local-proxy-server)
1. [Personnalisation du thème](#customize-the-theme-customizing-theme)
1. [Valider les modifications](#6-committing-the-changes-committing-the-changes)
1. [Déploiement du pipeline](#7-deploying-the-customized-theme-deploy-customized-theme)

### 1. Cloner le thème Zone de travail {#download-canvas-theme}

Ouvrez une invite de commande et exécutez la commande suivante pour cloner le thème de la zone de travail :

```
git clone https://github.com/adobe/aem-forms-theme-canvas
```

>[!NOTE]
>
> L’onglet Style de l’assistant de création de formulaire affiche le même nom de thème que dans le fichier package.json.

### 2. Comprendre la structure du thème {#structure-of-canvas-theme}

Un thème de formulaire adaptatif est un module contenant les ressources CSS, JavaScript et statiques qui définissent le style de votre formulaire et respectent la structure d’un thème de formulaire adaptatif. Un thème de formulaire adaptatif présente la structure suivante typique d’un projet front-end :

* `src/components`: Fichiers JavaScript et CSS spécifiques aux composants principaux AEM
* `src/resources` : fichiers statiques (icônes, logos et polices).
* `src/site`: Fichiers JavaScript et CSS qui s’appliquent à l’ensemble de la page AEM Sites
* `src/theme.ts`: Point d’entrée principal de votre thème JavaScript et CSS
* `src\theme.scss`: Fichiers JavaScript et CSS qui s’appliquent à l’ensemble du thème

Le `src/components` comporte des fichiers JavaScript et CSS spécifiques à tous les composants principaux d’AEM tels que les boutons, cases à cocher, conteneur, pied de page, etc. Vous pouvez mettre en forme un bouton ou une case à cocher en modifiant le fichier CSS spécifique au composant AEM.

![Modification du thème](/help/forms/assets/theme_structure.png)

Pour personnaliser le thème, vous pouvez démarrer le serveur proxy local pour afficher les personnalisations du thème en temps réel en fonction du contenu AEM réel.

### 4. Changez le nom dans package.json et package_lock.json du thème Canevas {#changename-packagelock-packagelockjson}

Mettez à jour le nom et la version du thème Zone de travail dans la `package.json` et `package_lock.json` fichiers .

>[!NOTE]
>
> Les noms ne doivent pas comporter `@aemforms` balise . Il doit s’agir d’un texte simple sous la forme d’un nom fourni par l’utilisateur.

![Rubrique du thème de la zone de travail](/help/forms/assets/changename_canvastheme.png)

### 3. Créez le fichier .env dans un dossier de thème {#creating-env-file-theme-folder}

Créez un `.env` dans le dossier theme et ajoutez les paramètres suivants :

* **URL d’AEM**
AEM_URL=https://[author-instance]

* **AEM nom du site**
AEM_ADAPTIVE_FORM=Form_name

* **AEM port proxy**
AEM_PROXY_PORT=7000


![Structure du thème du canevas](/help/forms/assets/env-file-canvas-theme.png)

### 4. Démarrez un serveur proxy local. {#starting-a-local-proxy-server}

1. Dans la ligne de commande, accédez à la racine du thème sur votre ordinateur local.
1. Exécutez `npm install` pour que npm récupère les dépendances et installe le projet.
1. Exécutez `npm run live` et le serveur proxy démarre.

   ![npm run live](/help/forms/assets/theme_proxy.png)


1. Appuyez ou cliquez sur **CONNEXION LOCALE (TÂCHES D’ADMINISTRATION UNIQUEMENT)** et connectez-vous avec les informations d’identification de l’utilisateur proxy fournies par l’administrateur AEM.

   ![Connexion locale](/help/forms/assets/local_signin.png)

   >[!NOTE]
   >
   > * Créez un utilisateur local pour vous connecter localement. Attribuez un rôle de contributeur au concepteur de thèmes.
   > * Si vous spécifiez l’URL d’AEM comme `http://localhost:[port]/` dans le `.env` du thème Zone de travail, vous êtes directement redirigé vers le navigateur.


1. Une fois connecté, modifiez l’URL dans le navigateur afin qu’elle pointe vers le chemin d’accès de l’exemple de contenu que l’administrateur AEM vous a fourni.

   * Par exemple, si le chemin fourni était `/content/formname.html?wcmmode=disabled`,, remplacez l’URL par `http://localhost:[port]/content/forms/af/formname.html?wcmmode=disabled`

   ![Exemple de contenu proxy](/help/forms/assets/sample_af.png)

Accédez à un formulaire adaptatif pour afficher le thème Zone de travail appliqué à un formulaire adaptatif.

### 5. Personnaliser le thème {#customize-theme}

1. Dans l’éditeur, ouvrez le fichier . `<your-theme-sources>/src/site/_variables.scss`.

   >[!NOTE]
   >
   > Vous pouvez appliquer un style à tous les composants de formulaire adaptatif d’un site directement en modifiant le `site/_variables.scss` fichier .

1. Modifiez la variable pour le `font colour` to `red`.

   ![Modifier le thème](/help/forms/assets/edit_theme.png)

   **Style des différents composants AEM**

   Vous pouvez mettre en forme les différents composants d’un formulaire adaptatif en modifiant son fichier CSS dans l’éditeur. Il existe différents dossiers CSS pour chaque composant principal de formulaire adaptatif dans le dossier Thème de zone de travail.

   ![Composant principal](/help/forms/assets/theme-component.png)

   Pour spécifier des styles pour un composant spécifique dans l’éditeur de thèmes, vous pouvez modifier le CSS dans un dossier de thèmes. Par exemple, si vous souhaitez modifier la couleur de bordure d’un champ de zone de texte, ouvrez le fichier CSS dans l’éditeur et modifiez sa couleur de bordure.

   ![Modifier la zone de texte CSS](/help/forms/assets/edit_color_textbox.png)

1. Lorsque vous enregistrez le fichier, le serveur proxy reconnaît la modification via la ligne . `[Browsersync] File event [change]`.

   ![Proxy browsersync](/help/forms/assets/browser_sync.png)

1. La modification est immédiatement visible lorsque vous revenez à votre navigateur du serveur proxy local.

   ![changer le thème de l’AF](/help/forms/assets/edit_theme_af.png)

Le concepteur de thème prévisualise les modifications apportées au serveur proxy local et personnalise le thème en fonction des exigences des différents composants d’AEM.

Avant de valider les modifications dans le référentiel Git d’AEM, vous devez accéder à votre [Informations sur le référentiel Git](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#accessing-git).

### 6. Validation des modifications {#committing-the-changes}

Après avoir apporté des modifications au thème et l’avoir testé avec un serveur proxy local, validez les modifications dans le référentiel Git de votre Cloud Service AEM Forms. Elle rend le thème personnalisé disponible dans votre environnement de Cloud Service Forms pour que les auteurs de Forms adaptatif puissent l’utiliser.

Avant de valider les modifications apportées au référentiel Git de votre Cloud Service AEM Forms, vous avez besoin d’un clone du référentiel sur votre ordinateur local. Pour cloner le référentiel :

1. Créez un référentiel de thèmes en cliquant sur le bouton **[!UICONTROL Référentiels]** .

   ![créer un référentiel de thème](/help/forms/assets/createrepo_canvastheme.png)

1. Cliquez sur **[!UICONTROL Ajouter un référentiel]** et spécifiez la variable **Nom du référentiel** dans le **Ajouter un référentiel** de la boîte de dialogue Cliquez sur **[!UICONTROL Enregistrer]**.

   ![Ajout d’un thème de canevas](/help/forms/assets/addcanvasthemerepo.png)

1. Cliquez sur **[!UICONTROL Copier l’URL du référentiel]** pour copier l’URL du référentiel créé.

   ![URL du thème du canevas](/help/forms/assets/copyurl_canvastheme.png)

1. Ouvrez l’invite de commande et clonez le référentiel cloud créé ci-dessus.

   ```
   git clone https://git.cloudmanager.adobe.com/aemforms/Canvasthemerepo/
   ```

1. Déplacez les fichiers du référentiel de thème que vous modifiez dans le référentiel cloud avec une commande similaire à
   `cp -r [source-theme-folder]/* [destination-cloud-repo]`
Par exemple, utilisez cette commande 
`cp -r [C:/cloned-git-canvas/*] [C:/cloned-repo]`
1. Dans le répertoire du référentiel cloud, validez les fichiers de thème dans lesquels vous avez déplacé les commandes suivantes.

   ```text
   git add .
   git commit -a -m "Adding theme files"
   git push
   ```

1. Les personnalisations sont transmises au référentiel Git.

   ![Modifications validées](/help/forms/assets/cmd_git_push.png)

Vos personnalisations sont désormais stockées en toute sécurité dans le référentiel Git.


### 7. Exécution du pipeline front-end {#deploy-pipeline}

1. Créez le pipeline frontal pour déployer le thème personnalisé. En savoir plus [comment configurer un pipeline de première ligne pour déployer un thème personnalisé](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#setup-pipeline).
1. Exécutez le pipeline front-end créé pour déployer le dossier de thème personnalisé sous **[!UICONTROL Style]** de l’assistant de création de formulaire adaptatif.

>[!NOTE]
>
>À l’avenir, si vous apportez des modifications au dossier de thèmes Canevas, vous devrez réexécuter le pipeline ci-dessus. Par conséquent, il est nécessaire de mémoriser le nom du pipeline.

## Exemple de personnalisation du thème {#example-to-customize-a-theme}

1. Connectez-vous à votre instance d’auteur AEM Forms.
1. Ouvrez un formulaire adaptatif créé à l’aide des composants principaux.
1. Démarrez le serveur proxy local à l’aide de l’invite de commande, puis cliquez sur **CONNEXION LOCALE (TÂCHES D’ADMINISTRATION UNIQUEMENT)**.
1. Une fois connecté, vous êtes redirigé vers le navigateur et le thème appliqué s’affiche.
1. Téléchargez la [Thème Canevas](https://github.com/adobe/aem-forms-theme-canvas) et extrayez le dossier zip téléchargé.
1. Ouvrez le dossier zip extrait dans l’éditeur de votre choix.
1. Créez un `.env` dans le dossier theme et ajoutez des paramètres : **URL AEM**, **AEM_ADAPTIVE_FORM** et **AEM_PROXY_PORT**.
1. Ouvrez le fichier CSS de la zone de texte dans le dossier de thème Canevas et modifiez la couleur de sa bordure pour indiquer `red` et enregistrez les modifications.
1. rouvrez le navigateur et vous verrez que les modifications sont répercutées immédiatement dans un formulaire adaptatif.
1. Déplacez le dossier de thème de la zone de travail dans votre référentiel cloné.
1. Validez les modifications et exécutez le pipeline frontal.

Une fois le pipeline exécuté, le thème est disponible sous l’onglet Style .

## Bonnes pratiques {#best-practices}

* **Éviter les ressources d’un autre thème**

   Lorsque vous modifiez un thème, vous pouvez parcourir et ajouter des actifs (tels que des images) d’autres thèmes. Par exemple, vous pouvez modifier l’arrière-plan d’une page. Par exemple, lorsque vous sélectionnez la **[!UICONTROL Page]** ![bouton de modification](assets/edit-button.png) > **[!UICONTROL Arrière plan]** > **[!UICONTROL Ajoutez]** > **[!UICONTROL Image]**, une boîte de dialogue s’affiche et vous permet de parcourir et d’ajouter des images dans l’autre thème.

   Vous pouvez rencontrer des problèmes avec votre thème actuel si un actif est ajouté à partir d’un autre thème et l’autre thème est déplacé ou supprimé. Nous vous recommandons d’éviter de parcourir les actifs d’autres thèmes et de les ajouter.

* **Modification de la largeur de disposition du panneau conteneur**

   Il n’est pas recommandé de modifier la largeur de disposition du panneau conteneur. Lorsque vous spécifiez la largeur d’un panneau de contenu, il devient statique et ne s’adapte pas aux différents affichages.

* **Utilisation de l’éditeur de formulaire ou de l’éditeur de thème pour l’utilisation de l’en-tête et du pied de page**

   Utilisez l’éditeur de thèmes si vous souhaitez mettre en forme l’en-tête et le pied de page à l’aide d’options de style telles que le style de police, l’arrière-plan et la transparence.
Si vous souhaitez fournir des informations comme une image de logo, le nom de l’entreprise dans l’en-tête et des informations de copyright dans le pied de page, utilisez les options de l’éditeur de formulaires.
