---
title: Ajouter la prise en charge de nouveaux paramètres régionaux à un formulaire adaptatif
seo-title: Learn to add support for new locales to your adaptive forms
description: AEM Forms vous permet d’ajouter de nouveaux paramètres régionaux pour localiser les formulaires adaptatifs. les langues anglais (en), espagnol (es), français (fr), italien (it), allemand (de), japonais (ja), portugais-brésilien (pt-BR), chinois (zh-CN), chinois-taïwanais (zh-TW) et coréen (ko-KR).
seo-description: AEM Forms allows you to add new locales for localizing adaptive forms. We support 10 locales out of the box curently, as  "en","fr","de","ja","pt-br","zh-cn","zh-tw","ko-kr","it","es".
source-git-commit: 400e9fa0263b3e9bdae10dc80d524b291f99496d
workflow-type: tm+mt
source-wordcount: '1180'
ht-degree: 29%

---

# Prise en charge de nouveaux paramètres régionaux pour la localisation des formulaires adaptatifs {#supporting-new-locales-for-adaptive-forms-localization}

AEM Forms fournit une prise en charge immédiate des langues suivantes : anglais (en), espagnol (es), français (fr), italien (it), allemand (de), japonais (ja), portugais-brésilien (pt-BR), chinois (zh-CN), chinois-Taïwan (zh-TW) et coréen (ko-KR). Vous pouvez également ajouter la prise en charge d’autres paramètres régionaux, comme Hindi(hi_IN).

## Présentation des dictionnaires de paramètres régionaux {#about-locale-dictionaries}

La localisation des formulaires adaptatifs repose sur deux types de dictionnaires de paramètres régionaux : 

* **Dictionnaire spécifique au formulaire** : il contient des chaînes utilisées dans des formulaires adaptatifs. Par exemple, étiquettes, noms de champs, messages d’erreur, descriptions d’aide, etc. Il est géré sous forme de jeu de fichiers XLIFF pour chaque jeu de paramètres régionaux et accessible à l’adresse `[author-instance]/libs/cq/i18n/gui/translator.html`.

* **Dictionnaires globaux** : la bibliothèque client AEM comporte deux dictionnaires globaux, gérés en tant qu’objets JSON. Ces dictionnaires contiennent les messages d’erreur par défaut, les noms des mois, les symboles de devise, les modèles de date et d’heure, etc. Vous trouverez ces dictionnaires à l’adresse `[author-instance]/libs/fd/xfaforms/clientlibs/I18N`. Ces emplacements contiennent des dossiers distincts pour chaque langue. Comme les dictionnaires globaux ne sont pas mis à jour fréquemment, conserver des fichiers JavaScript distincts pour chaque langue permet aux navigateurs de les mettre en cache et de réduire l’utilisation de la bande passante du réseau lors de l’accès à différents formulaires adaptatifs sur le même serveur.

## Ajouter la prise en charge des nouveaux paramètres régionaux {#add-support-for-new-locales}

Pour ajouter la prise en charge d’un nouveau paramètre régional, procédez comme suit :

1. [Ajoutez la localisation pour les paramètres régionaux non pris en charge](#add-localization-support-for-non-supported-locales-add-localization-support-for-non-supported-locales)
1. [Utilisation de paramètres régionaux ajoutés dans Adaptive Forms](#use-added-locale-in-adaptive-forms-use-added-locale-in-af)

### Ajoutez la localisation pour les paramètres régionaux non pris en charge {#add-localization-support-for-non-supported-locales}

AEM Forms prend actuellement en charge la localisation de contenu Adaptive Forms en anglais (en), espagnol (es), français (fr), italien (it), allemand (de), japonais (ja), portugais-brésilien (pt-BR), chinois (zh-CN), chinois-taïwanais (zh-TW) et coréen (ko-KR).

Pour ajouter de nouveaux paramètres régionaux lors de l’exécution des formulaires adaptatifs :

1. [Clonage de votre référentiel](#1-clone-the-repository-clone-the-repository)
1. [Ajouter des paramètres régionaux au service GuideLocalizationService](#2-add-a-locale-to-the-guide-localization-service-add-a-locale-to-the-guide-localization-service-br)
1. [Ajouter un dossier spécifique au nom du paramètre régional](#3-add-locale-name-specific-folder-client-library-add-locale-name-specific-folder)
1. [Ajouter la prise en charge des paramètres régionaux pour la langue du dictionnaire](#about-locale-dictionaries-about-locale-dictionaries)
1. [Validation des modifications dans le référentiel et déploiement du pipeline](#5-commit-the-changes-in-the-repository-and-deploy-the-pipeline-commit-chnages-in-repo-deploy-pipeline)

#### 1. Cloner le référentiel {#clone-the-repository}

1. Sur la ligne de commande, accédez à l’emplacement où vous souhaitez cloner le référentiel du Cloud Service Forms.
1. Exécutez la commande [récupéré à partir de Cloud Manager.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#accessing-git) Elle est similaire à `git clone https://git.cloudmanager.adobe.com/<my-org>/<my-program>/`.
1. Utilisez le nom d’utilisateur et le mot de passe Git pour cloner le référentiel.
1. Ouvrez le dossier de référentiel du Cloud Service Forms cloné dans l’éditeur de votre choix.

#### 2. Ajout d’un paramètre régional au service de localisation du guide {#add-a-locale-to-the-guide-localization-service-br}

1. Recherchez la variable `Guide Localization Service.cfg.json` et ajoutez les paramètres régionaux que vous souhaitez ajouter à la liste des paramètres régionaux pris en charge.

   >[!NOTE]
   >
   >* Créez un fichier portant le nom `Guide Localization Service.cfg.json` s’il n’est pas déjà présent.


#### 3. Ajout d’une bibliothèque cliente de dossiers spécifique au nom du paramètre régional {#add-locale-name-specific-folder}

1. Dans le dossier UI.content, créez `etc/clientlibs` dossier.
1. Créez plus loin un dossier appelé `locale-name` under `etc/clientlibs` pour servir de conteneur pour xfa et af clientlibs.

##### 3.1 Ajout de la bibliothèque cliente XFA pour un paramètre régional dans le dossier locale-name

Créez un noeud appelé `[locale-name]_xfa` et saisissez comme `cq:ClientLibraryFolder` under `etc/clientlibs/locale_name`, avec catégorie `xfaforms.I18N.<locale>`et ajoutez les fichiers suivants :

* **I18N.js** qui définit `xfalib.locale.Strings` pour `<locale>`, comme défini dans `/etc/clientlibs/fd/xfaforms/I18N/ja/I18N`.
* **js.txt** qui contient les éléments suivants :
   */libs/fd/xfaforms/clientlibs/I18N/Namespace.js I18N.js /etc/clientlibs/fd/xfaforms/I18N/LogMessages.js*

##### 3.2. Ajout de la bibliothèque cliente Formulaire adaptatif pour un dossier locale-name {#add-adaptive-form-client-library-for-a-locale-br}

1. Créez un noeud appelé `[locale-name]_af` et saisissez comme `cq:ClientLibraryFolder` under `etc/clientlibs/locale_name`, avec la catégorie comme `guides.I18N.<locale>` et les dépendances en tant que `xfaforms.3rdparty`, `xfaforms.I18N.<locale>` et `guide.common`.
1. Créez un dossier appelé `javascript` et ajoutez les fichiers suivants :

   * **i18n.js** qui définit `guidelib.i18n`, comportant des motifs « calendarSymbols », `datePatterns`, `timePatterns`, `dateTimeSymbols`, `numberPatterns`, `numberSymbols`, `currencySymbols`, `typefaces` pour `<locale>` conformément aux spécifications XFA décrites dans [Spécification du jeu de paramètres régionaux](https://helpx.adobe.com/content/dam/Adobe/specs/xfa_spec_3_3.pdf).
   * **LogMessages.js** qui définit `guidelib.i18n.strings` et `guidelib.i18n.LogMessages` pour `<locale>`, défini dans `/etc/clientlibs/fd/af/I18N/fr/javascript/LogMessages.js`.

1. Ajouter **js.txt** contenant les éléments suivants :

   ```
     i18n.js
     LogMessages.js
   ```

#### 4. Ajout de la prise en charge des paramètres régionaux pour le dictionnaire {#add-locale-support-for-the-dictionary-br}

Exécutez cette étape uniquement si l’élément `<locale>` que vous ajoutez ne se trouve pas parmi `en`, `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`.

1. Création d’un dossier `languages` under `etc`, s’il n’est pas déjà présent.

1. Ajoutez une propriété comprenant plusieurs valeurs `languages` au nœud, s’il ne sont pas déjà présents.
1. Ajoutez les valeurs des paramètres régionaux par défaut `<locale-name>` `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`, si elles ne sont pas déjà présentes.

1. Ajoutez `<locale>` aux valeurs de la propriété `languages` de `/etc/languages`.


```text
Add the newly created folders in the `filter.xml` under etc/META-INF/[folder hierarchy] as:
<filter root="/etc/clientlibs/[locale-name]"/>
<filter root="/etc/languages"/>
```

Avant de valider les modifications dans le référentiel Git d’AEM, vous devez accéder à votre [Informations sur le référentiel Git](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=en#accessing-git).

#### 5. Validez les modifications dans le référentiel et déployez le pipeline {#commit-chnages-in-repo-deploy-pipeline}

Validez les modifications dans le référentiel GIT après l’ajout d’une nouvelle prise en charge des paramètres régionaux. Déployez votre code à l’aide du pipeline de pile complet. En savoir plus [configuration d’un pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=en#setup-pipeline) pour ajouter une nouvelle prise en charge des paramètres régionaux.

Une fois le pipeline terminé, le nouveau paramètre régional ajouté apparaît dans l’environnement AEM.

### Utilisation de paramètres régionaux ajoutés dans le Forms adaptatif {#use-added-locale-in-af}

Effectuez les étapes suivantes pour utiliser et générer un formulaire adaptatif à l’aide d’un paramètre régional nouvellement ajouté :

1. Connectez-vous à votre instance d’auteur AEM.
1. Accédez à **Forms** >  **Forms et documents**.
1. Sélectionnez un formulaire adaptatif et cliquez sur **Ajouter un dictionnaire** et **Ajout D’Un Dictionnaire Au Projet De Traduction** s’affiche.
1. Spécifiez la variable **Titre du projet** et sélectionnez la variable **Langues cibles** dans le menu déroulant du **Ajout D’Un Dictionnaire Au Projet De Traduction** assistant.
1. Cliquez sur **Terminé** et exécutez le projet de traduction créé.
1. Sélectionnez un formulaire adaptatif et cliquez sur **Aperçu en tant que HTML**.
1. Ajouter `&afAcceptLang=<locale-name>` dans l’URL d’un formulaire adaptatif.
1. Actualisez la page et le formulaire adaptatif est rendu dans un paramètre régional spécifié.

Il existe deux méthodes pour identifier les paramètres régionaux d’un formulaire adaptatif. Lors du rendu d’un formulaire adaptatif, il identifie les paramètres régionaux nécessaires :

* Rétablissement de la variable `[local]` sélecteur dans l’URL du formulaire adaptatif. Le format de l’URL est `http://host:[port]/content/forms/af/[afName].[locale].html?wcmmode=disabled`. L’utilisation du sélecteur `[local]` permet de mettre en cache un formulaire adaptatif ;

* Conservez les paramètres suivants dans l’ordre indiqué :

   * Paramètre de requête `afAcceptLang`
Pour remplacer les paramètres régionaux du navigateur des utilisateurs, vous pouvez transmettre le paramètre de demande 
`afAcceptLang` pour forcer les paramètres régionaux. Par exemple, l’URL suivante force le rendu du formulaire dans la langue française-canadienne :
      `https://'[server]:[port]'/<contextPath>/<formFolder>/<formName>.html?wcmmode=disabled&afAcceptLang=ca-fr`

   * La langue du navigateur défini pour l’utilisateur, qui est spécifiée dans la demande par le biais de l’en-tête `Accept-Language`.

S’il n’existe pas de bibliothèque client pour les paramètres régionaux nécessaires, il cherche une bibliothèque cliente correspondant au code de langue présent dans les paramètres régionaux. Par exemple, si le paramètre régional requis est `en_ZA` (en anglais d’Afrique du Sud) et la bibliothèque cliente pour `en_ZA` n’existe pas, le formulaire adaptatif utilise la bibliothèque cliente pour `en` (anglais), si elle existe. Toutefois, si aucune de ces bibliothèques n’existe, le formulaire adaptatif utilise le dictionnaire correspondant aux paramètres régionaux `en`.


Une fois le paramètre régional identifié, le formulaire adaptatif sélectionne le dictionnaire propre au formulaire. Si le dictionnaire spécifique au formulaire correspondant au paramètre régional requis est introuvable, il utilise le dictionnaire correspondant à la langue dans laquelle le formulaire adaptatif est créé.

En l’absence d’informations de paramètres régionaux, le formulaire adaptatif est distribué dans la langue d’origine du formulaire. La langue d’origine est la langue utilisée lors du développement du formulaire adaptatif.

Get [exemple de bibliothèque cliente](/help/forms/assets/locale-support-sample.zip) pour ajouter la prise en charge des nouveaux paramètres régionaux. Vous devez modifier le contenu du dossier dans les paramètres régionaux requis.

## Bonnes pratiques pour la prise en charge d’une nouvelle localisation {#best-practices}

* Adobe recommande de créer un projet de traduction après la création d’un formulaire adaptatif.

* Lorsque de nouveaux champs sont ajoutés dans un formulaire adaptatif existant :
   * **Pour la traduction automatique**: Recréez le dictionnaire et exécutez le projet de traduction. Les champs ajoutés à un formulaire adaptatif après la création d’un projet de traduction ne sont pas traduits.
   * **Pour la traduction humaine**: Exporter le dictionnaire via `[server:port]/libs/cq/i18n/gui/translator.html`. Mettez à jour le dictionnaire des champs nouvellement ajoutés et téléchargez-le.
