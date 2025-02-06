---
title: Comment ajouter la prise en charge de nouveaux paramètres régionaux à un formulaire adaptatif basé sur les composants de base ?
description: Pour le Forms adaptatif, vous pouvez ajouter des paramètres régionaux pour d’autres langues en dehors de celle prête à l’emploi.
feature: Adaptive Forms, Foundation Components
exl-id: 4c7d6caa-1adb-4663-933f-b09129b9baef
role: User, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '1220'
ht-degree: 79%

---

# Prise en charge de nouveaux paramètres régionaux pour la localisation des formulaires adaptatifs {#supporting-new-locales-for-adaptive-forms-localization}

>[!NOTE]
>
> Adobe recommande d’utiliser la capture de données moderne et extensible [composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=fr) pour [créer un nouveau Forms adaptatif](/help/forms/creating-adaptive-form-core-components.md) ou [ajouter un Forms adaptatif aux pages AEM Sites](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Ces composants représentent une avancée significative dans la création de formulaires adaptatifs, ce qui garantit des expériences utilisateur impressionnantes. Cet article décrit une ancienne approche de création de Forms adaptatif à l’aide de composants de base.


| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/manage-administer-aem-forms/supporting-new-language-localization.html) |
| Composants principaux | [Cliquez ici](supporting-new-language-localization-core-components.md) |
| Composants de base | Cet article |

AEM Forms fournit une prise en charge immédiate des paramètres régionaux en anglais (en), espagnol (es), français (fr), italien (it), allemand (de), japonais (ja), portugais du Brésil (pt-BR), chinois (zh-CN), chinois taïwanais (zh-TW) et coréen (ko-KR). Vous pouvez également ajouter la prise en charge d’autres paramètres régionaux comme l’hindi (hi_IN).

## Présentation des dictionnaires de paramètres régionaux {#about-locale-dictionaries}

La localisation des formulaires adaptatifs repose sur deux types de dictionnaires de paramètres régionaux : 

* **Dictionnaire spécifique au formulaire** : il contient des chaînes utilisées dans des formulaires adaptatifs. Par exemple, les étiquettes, les noms de champ, les messages d’erreur et les descriptions d’aide. Il est géré sous forme de jeu de fichiers XLIFF pour chaque jeu de paramètres régionaux et accessible à l’adresse `[author-instance]/libs/cq/i18n/gui/translator.html`.

* **Dictionnaires globaux** La bibliothèque cliente AEM contient deux dictionnaires globaux, gérés en tant qu’objets JSON. Ces dictionnaires contiennent les messages d’erreur par défaut, les noms des mois, les symboles de devise, les modèles de date et d’heure, etc. Vous trouverez ces dictionnaires à l’adresse `[author-instance]/libs/fd/xfaforms/clientlibs/I18N`. Ces emplacements contiennent des dossiers distincts pour chaque paramètre régional. Comme les dictionnaires globaux ne sont pas mis à jour fréquemment, la conservation de fichiers JavaScript distincts pour chaque paramètre régional permet aux navigateurs de les mettre en cache et de réduire l’utilisation de la bande passante du réseau lors de l’accès à différents formulaires adaptatifs sur le même serveur.

## Ajouter la prise en charge de nouveaux paramètres régionaux {#add-support-for-new-locales}

Pour ajouter la prise en charge d’un nouveau paramètre régional, procédez comme suit :

1. [Ajoutez la localisation pour les paramètres régionaux non pris en charge](#add-localization-support-for-non-supported-locales)
1. [Utilisez les paramètres régionaux ajoutés dans Adaptive Forms](#use-added-locale-in-af)

### Ajoutez la localisation pour les paramètres régionaux non pris en charge {#add-localization-support-for-non-supported-locales}

AEM Forms prend actuellement en charge la localisation du contenu de formulaire adaptatif en anglais (en), espagnol (es), français (fr), italien (it), allemand (de), japonais (ja), portugais du Brésl (pt-BR), chinois (zh-CN), chinois taïwanais (zh-TW) et coréen (ko-KR).

Pour ajouter la prise en charge d’un nouveau paramètre régional lors de l’exécution du Forms adaptatif :

1. [Clonez votre référentiel](#clone-the-repository)
1. [Ajoutez des paramètres régionaux au service GuideLocalizationService](#add-a-locale-to-the-guide-localization-service)
1. [Ajoutez un dossier spécifique au nom du paramètre régional](#add-locale-name-specific-folder)
1. [Ajoutez la prise en charge des paramètres régionaux pour le dictionnaire](#add-locale-support-for-the-dictionary)
1. [Validez les modifications dans le référentiel et déployez le pipeline](#commit-changes-in-repo-deploy-pipeline)

#### 1. Cloner le référentiel {#clone-the-repository}

1. Sur la ligne de commande, accédez à l’emplacement où vous souhaitez cloner le référentiel Forms Cloud Service.
1. Exécutez la commande [récupérée à partir de Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#accessing-git). Elle est similaire à `git clone https://git.cloudmanager.adobe.com/<my-org>/<my-program>/`.
1. Utilisez le nom d’utilisateur et le mot de passe Git pour cloner le référentiel.
1. Ouvrez le dossier de référentiel de Forms Cloud Service cloné dans l’éditeur de votre choix.

#### 2. Ajouter un paramètre régional au Guide Localization Service {#add-a-locale-to-the-guide-localization-service}

1. Recherchez le fichier `Guide Localization Service.cfg.json` et ajoutez le paramètre régional que vous souhaitez à la liste des paramètres régionaux pris en charge.

   >[!NOTE]
   >
   > Créez un fichier portant le nom `Guide Localization Service.cfg.json` s’il n’est pas déjà présent.

#### 3. Ajouter la bibliothèque cliente de dossiers spécifiques au nom du paramètre régional {#add-locale-name-specific-folder}

1. Dans le dossier UI.content, créez le dossier `etc/clientlibs`.
1. Ensuite, créez un dossier appelé `locale-name` sous `etc/clientlibs` pour servir de conteneur pour les bibliothèques clientes xfa et af clientlibs.

##### 3.1 Ajouter la bibliothèque XFA cliente pour des paramètres régionaux dans un dossier locale-name

Créez un nœud appelé `[locale-name]_xfa` et saisissez `cq:ClientLibraryFolder` sous `etc/clientlibs/locale_name`, avec la catégorie `xfaforms.I18N.<locale>`, puis ajoutez les fichiers suivants :

* **I18N.js** qui définit `xfalib.locale.Strings` pour `<locale>`, comme défini dans `/etc/clientlibs/fd/xfaforms/I18N/ja/I18N`.
* **js.txt** qui contient les éléments suivants :
  */libs/fd/xfaforms/clientlibs/I18N/Namespace.js
I18N.js
/etc/clientlibs/fd/xfaforms/I18N/LogMessages.js*

##### 3.2. Ajouter une bibliothèque cliente de formulaires adaptatifs pour un dossier locale-name de paramètre régional

1. Créez un nœud appelé `[locale-name]_af` avec le type `cq:ClientLibraryFolder` sous `etc/clientlibs/locale_name`, avec la catégorie `guides.I18N.<locale>` et les dépendances `xfaforms.3rdparty`, `xfaforms.I18N.<locale>` et `guide.common`.
1. Créez un dossier appelé `javascript` et ajoutez les fichiers suivants :

   * **i18n.js** qui définit `guidelib.i18n`, comportant des motifs « calendarSymbols », `datePatterns`, `timePatterns`, `dateTimeSymbols`, `numberPatterns`, `numberSymbols`, `currencySymbols`, `typefaces` pour `<locale>` conformément aux spécifications XFA décrites dans [Spécification du jeu de paramètres régionaux](https://helpx.adobe.com/content/dam/Adobe/specs/xfa_spec_3_3.pdf).
   * **LogMessages.js** qui définit `guidelib.i18n.strings` et `guidelib.i18n.LogMessages` pour `<locale>`, comme défini dans `/etc/clientlibs/fd/af/I18N/fr/javascript/LogMessages.js`.

1. Ajoutez le **js.txt** contenant les éléments suivants :

   ```
     i18n.js
     LogMessages.js
   ```

#### 4. Ajouter la prise en charge des paramètres régionaux pour le dictionnaire {#add-locale-support-for-the-dictionary}

Exécutez cette étape uniquement si l’élément `<locale>` que vous ajoutez ne se trouve pas parmi `en`, `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`.

1. Créez un dossier `languages` sous `etc`, s’il n’est pas déjà présent.

1. Ajoutez une propriété comprenant plusieurs valeurs `languages` au nœud, s’il ne sont pas déjà présents.
1. Ajoutez les valeurs des paramètres régionaux par défaut `<locale-name>` `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`, si elles ne sont pas déjà présentes.

1. Ajoutez `<locale>` aux valeurs de la propriété `languages` de `/etc/languages`.
1. Ajoutez les dossiers créés dans le `filter.xml` sous etc/META-INF/[hiérarchie de dossiers] en tant que :

   ```
   <filter root="/etc/clientlibs/[locale-name]"/>
   <filter root="/etc/languages"/>
   ```

Avant de valider les modifications dans le référentiel Git d’AEM, vous devez accéder à vos [informations sur le référentiel Git](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=fr#accessing-git).

#### 5. Valider les modifications dans le référentiel et déployer le pipeline {#commit-changes-in-repo-deploy-pipeline}

Validez les modifications dans le référentiel GIT après l’ajout d’une prise en charge de paramètres régionaux. Déployez votre code à l’aide du pipeline de pile pleine. Découvrez [comment configurer un pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=fr#setup-pipeline) pour ajouter une nouvelle prise en charge de paramètres régionaux.
Une fois le pipeline terminé, le nouveau paramètre régional ajouté apparaît dans l’environnement AEM.

### Utiliser des paramètres régionaux ajoutés dans les formulaires adaptatifs {#use-added-locale-in-af}

Effectuez les étapes suivantes pour utiliser et générer un formulaire adaptatif à l’aide du paramètre régional nouvellement ajouté :

1. Connectez-vous à votre instance de création AEM.
1. Accédez à **Formulaires** > **Formulaires et documents**.
1. Sélectionnez un formulaire adaptatif, puis cliquez sur **Ajouter un dictionnaire**. L’assistant **Ajouter un dictionnaire au projet de traduction** s’affiche.
1. Spécifiez le **Titre du projet** et sélectionnez les **Langues cibles** dans le menu déroulant de l’assistant **Ajouter un dictionnaire au projet de traduction**.
1. Cliquez sur **Terminé** et exécutez le projet de traduction créé.
1. Sélectionnez un formulaire adaptatif et cliquez sur **Aperçu au format HTML**.
1. Ajoutez `&afAcceptLang=<locale-name>` dans l’URL d’un formulaire adaptatif.
1. Actualisez la page et le formulaire adaptatif est rendu dans un paramètre régional spécifié.

Deux méthodes permettent d’identifier les paramètres régionaux d’un formulaire adaptatif. Lors du rendu d’un formulaire adaptatif, il identifie les paramètres régionaux nécessaires :

* Récupération du sélecteur `[local]` dans l’URL du formulaire adaptatif. Le format de l’URL est `http://host:[port]/content/forms/af/[afName].[locale].html?wcmmode=disabled`. L’utilisation du sélecteur `[local]` permet de mettre en cache un formulaire adaptatif ;

* La récupération des paramètres suivants dans l’ordre indiqué :

   * Paramètre de requête `afAcceptLang`
Pour remplacer la langue du navigateur des utilisateurs et des utilisatrices, vous pouvez transmettre le paramètre de requête `afAcceptLang` afin de forcer les paramètres régionaux. Par exemple, l’URL ci-dessous force le rendu du formulaire dans le paramètre régional français canadien :
     `https://'[server]:[port]'/<contextPath>/<formFolder>/<formName>.html?wcmmode=disabled&afAcceptLang=ca-fr`

   * La langue du navigateur défini pour l’utilisateur ou l’utilisatrice, qui est spécifiée dans la demande par le biais de l’en-tête `Accept-Language`.

S’il n’existe pas de bibliothèque cliente pour le paramètre régional nécessaire, il cherche une bibliothèque cliente correspondant au code de langue présent dans le paramètre régional. Par exemple, si le paramètre régional requis est `en_ZA` (anglais Afrique du Sud) et qu’il n’existe pas de bibliothèque cliente correspondant à `en_ZA`, le formulaire adaptatif utilise la bibliothèque cliente correspondant à langue `en` (anglais), si elle existe. Toutefois, si aucune de ces bibliothèques n’existe, le formulaire adaptatif utilise le dictionnaire correspondant au paramètre régional `en`.


Une fois le paramètre régional identifié, le formulaire adaptatif sélectionne le dictionnaire qui lui est spécifique. Si le dictionnaire spécifique au formulaire pour les paramètres régionaux nécessaires est introuvable, il utilise le dictionnaire de la langue dans laquelle le formulaire adaptatif est créé.

En l’absence d’informations de paramètres régionaux, le formulaire adaptatif est distribué dans la langue d’origine du formulaire. La langue d’origine est la langue utilisée lors du développement du formulaire adaptatif.

Obtenez un [exemple de bibliothèque cliente](/help/forms/assets/locale-support-sample.zip) pour ajouter la prise en charge de nouveaux paramètres régionaux. Vous devez modifier le contenu du dossier dans le paramètre régional requis.

## Bonnes pratiques pour la prise en charge d’une nouvelle localisation {#best-practices}

* Adobe recommande de créer un projet de traduction après la création d’un formulaire adaptatif.

* Lorsque de nouveaux champs sont ajoutés dans un formulaire adaptatif existant :
   * **Pour la traduction automatique** : recréez le dictionnaire et exécutez le projet de traduction. Les champs ajoutés à un formulaire adaptatif après la création d’un projet de traduction ne sont pas traduits.
   * **Pour la traduction humaine** : exportez le dictionnaire via `[server:port]/libs/cq/i18n/gui/translator.html`. Mettez à jour le dictionnaire avec les champs nouvellement ajoutés et téléchargez-le.


## Voir également {#see-also}

{{see-also}}