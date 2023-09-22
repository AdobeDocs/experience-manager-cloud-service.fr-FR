---
title: Comment ajouter la prise en charge de nouveaux paramètres régionaux à un formulaire adaptatif en fonction des composants principaux ?
description: Découvrez comment ajouter de nouveaux paramètres régionaux pour un formulaire adaptatif.
source-git-commit: 2a738d17b1e2f46c06828512ee07c1c20f35596c
workflow-type: tm+mt
source-wordcount: '1449'
ht-degree: 26%

---


# Ajout d’un paramètre régional pour Forms adaptatif basé sur les composants principaux {#supporting-new-locales-for-adaptive-forms-localization}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| Composants de base | [Cliquez ici](supporting-new-language-localization.md) |
| Composants principaux | Cet article |

AEM Forms fournit une prise en charge immédiate des paramètres régionaux en anglais (en), espagnol (es), français (fr), italien (it), allemand (de), japonais (ja), portugais du Brésil (pt-BR), chinois (zh-CN), chinois taïwanais (zh-TW) et coréen (ko-KR). 

## Comment le paramètre régional est-il sélectionné pour un formulaire adaptatif ?


Il existe deux méthodes pour identifier et sélectionner les paramètres régionaux d’un formulaire adaptatif lors de son rendu :

* **En utilisant la variable [locale] Sélecteur dans l’URL**: lors du rendu d’un formulaire adaptatif, le système identifie les paramètres régionaux requis en examinant la variable [locale] dans l’URL du formulaire adaptatif. L&#39;URL suit ce format : http:/[URL du serveur AEM Forms]/content/forms/af/[afName].[locale].html?wcmmode=disabled. L’utilisation de la variable [locale] Le sélecteur permet la mise en cache du formulaire adaptatif.

* Récupération des paramètres dans l’ordre indiqué ci-dessous :

   * **Paramètre de requête`afAcceptLang`**: pour remplacer les paramètres régionaux du navigateur de l’utilisateur, vous pouvez transmettre le paramètre de requête afAcceptLang . Par exemple, cette URL applique le rendu du formulaire en français canadien : `https://'[server]:[port]'/<contextPath>/<formFolder>/<formName>.html?wcmmode=disabled&afAcceptLang=ca-fr`.

   * **Paramètre régional du navigateur (en-tête Accept-Language)**: le système prend également en compte les paramètres régionaux du navigateur de l’utilisateur, qui sont spécifiés dans la requête à l’aide de la variable `Accept-Language` en-tête .

  Si une bibliothèque cliente correspondant au paramètre régional requis n’est pas disponible, le système vérifie si une bibliothèque cliente existe pour le code de langue dans le paramètre régional. Par exemple, si le paramètre régional requis est `en_ZA` (en anglais sud-africain) et il n’y a pas de bibliothèque cliente pour `en_ZA`, le formulaire adaptatif utilise la bibliothèque cliente pour en (en anglais) si disponible. Si aucun de ces éléments n’est trouvé, le formulaire adaptatif a recours au dictionnaire pour la variable `en` locale.

  Une fois le paramètre régional identifié, le formulaire adaptatif sélectionne le dictionnaire correspondant spécifique au formulaire. Si le dictionnaire correspondant au paramètre régional requis est introuvable, il utilise par défaut le dictionnaire dans la langue dans laquelle le formulaire adaptatif a été créé.

  Dans les cas où aucune information locale n’est disponible, le formulaire adaptatif s’affiche dans sa langue d’origine, qui est la langue utilisée lors du développement du formulaire.


## Conditions préalables requises {#prerequistes}

Avant de commencer à ajouter la prise en charge d’un nouveau paramètre régional,

* Installez un éditeur de texte brut (IDE) pour faciliter la modification. Les exemples de ce document sont basés sur Microsoft® Visual Studio Code.
* Installation d’une version de [Git](https://git-scm.com), si elles ne sont pas disponibles sur votre ordinateur.
* Cloner le [Composants principaux de Forms adaptatif](https://github.com/adobe/aem-core-forms-components) référentiel. Pour cloner le référentiel :
   1. Ouvrez la ligne de commande ou la fenêtre de terminal et accédez à un emplacement pour stocker le référentiel. Par exemple, `/adaptive-forms-core-components`
   1. Exécutez la commande suivante pour cloner le référentiel :

      ```SHELL
          git clone https://github.com/adobe/aem-core-forms-components.git
      ```

  Le référentiel comprend une bibliothèque cliente nécessaire à l’ajout d’un paramètre régional. Dans le reste de l’article, le dossier est appelé : [Référentiel des composants principaux de Forms adaptatif].


## Ajouter un paramètre régional {#add-localization-support-for-non-supported-locales}

Pour ajouter la prise en charge d’un nouveau paramètre régional, procédez comme suit :

![Ajouter un paramètre régional à un référentiel](add-a-locale-adaptive-form-core-components.png)

### 1. Cloner votre référentiel Git as a Cloud Service AEM {#clone-the-repository}

1. Ouvrez la ligne de commande et choisissez un répertoire dans lequel stocker votre référentiel as a Cloud Service AEM Forms, tel que `/cloud-service-repository/`.

1. Exécutez la commande suivante pour cloner le référentiel :

   ```SHELL
   git clone https://git.cloudmanager.adobe.com/<my-org>/<my-program>/
   ```

   Remplacer `<my-org>` et `<my-program>` dans l’URL ci-dessus avec le nom de votre organisation et le nom du programme. Pour obtenir des instructions détaillées sur le nom de l’organisation, le nom du programme ou le chemin d’accès complet à votre référentiel Git et les informations d’identification requises pour cloner le référentiel, reportez-vous à la section [Accès à Git](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#accessing-git) article.

   Une fois la commande terminée, un dossier `<my-program>` est créée. Il contient le contenu cloné à partir du référentiel Git. Dans le reste de l’article, le dossier est appelé : `[AEM Forms as a Cloud Service Git repository]`.


### 2. Ajoutez le nouveau paramètre régional au Guide Localization Service {#add-a-locale-to-the-guide-localization-service}

1. Ouvrez le dossier du référentiel, cloné dans la section précédente, dans un éditeur de texte brut.
1. Accédez au dossier `[AEM Forms as a Cloud Service Git repository]/ui.config/src/main/content/jcr_root/apps/<appid>/osgiconfig/config`. Vous pouvez trouver la variable `<appid>` dans le `archetype.properties` fichiers du projet.
1. Ouvrez le fichier `[AEM Forms as a Cloud Service Git repository]/ui.config/src/main/content/jcr_root/apps/<appid>/osgiconfig/config/Guide Localization Service.cfg.json` pour le modifier. Si le fichier n’existe pas, créez-le. Un exemple de fichier avec les paramètres régionaux pris en charge ressemble à ce qui suit :

   ![Exemple de guide Localization Service.cfg.json](locales.png)

1. Ajoutez la variable [code du paramètre régional pour la langue](https://fr.wikipedia.org/wiki/Liste_des_codes_ISO_639-1) que vous souhaitez ajouter, par exemple, &quot;hi&quot; pour le hindi.
1. Enregistrez et fermez le fichier.

### 3. Création d’une bibliothèque cliente pour ajouter un paramètre régional

AEM Forms fournit un exemple de bibliothèque cliente pour vous aider à ajouter facilement de nouveaux paramètres régionaux. Vous pouvez télécharger et ajouter le `clientlib-it-custom-locale` de la bibliothèque cliente [Référentiel des composants principaux de Forms adaptatif] sur GitHub vers votre référentiel as a Cloud Service Forms. Pour ajouter la bibliothèque cliente, procédez comme suit :

1. Ouvrez votre [Référentiel des composants principaux de Forms adaptatif] dans votre éditeur de texte brut. Si le référentiel n’est pas cloné, voir [Conditions préalables](#prerequistes) pour obtenir des instructions sur le clonage du référentiel.
1. Accédez au répertoire `/aem-core-forms-components/it/apps/src/main/content/jcr_root/apps/forms-core-components-it/clientlibs`.
1. Copiez le `clientlib-it-custom-locale` répertoire .
1. Accédez à `[AEM Forms as a Cloud Service Git repository]/ui.apps/src/main/content/jcr_root/apps/moonlightprodprogram/clientlibs` et collez le `clientlib-it-custom-locale` répertoire .


### 4. Création d’un fichier spécifique aux paramètres régionaux {#locale-specific-file}

1. Accédez à `[AEM Forms as a Cloud Service Git repository]/ui.apps/src/main/content/jcr_root/apps/<program-id>/clientlibs/clientlib-it-custom-locale/resources/i18n/`.
1. Recherchez la variable [Fichier .json de paramètres régionaux anglais sur GitHub](https://github.com/adobe/aem-core-forms-components/blob/master/ui.af.apps/src/main/content/jcr_root/apps/core/fd/af-clientlibs/core-forms-components-runtime-all/resources/i18n/en.json), qui contient le dernier ensemble de chaînes par défaut inclus dans le produit.
1. Créez un fichier .json correspondant à vos paramètres régionaux spécifiques.
1. Dans le fichier .json que vous venez de créer, mettez en miroir la structure du fichier de paramètres régionaux anglais.
1. Remplacez les chaînes en anglais de votre fichier .json par les chaînes localisées correspondantes pour votre langue.
1. Enregistrez et fermez le fichier.


### 5. Ajout de la prise en charge des paramètres régionaux au dictionnaire {#add-locale-support-for-the-dictionary}

Exécutez cette étape uniquement si l’élément `<locale>` que vous ajoutez ne se trouve pas parmi `en`, `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`.

1. Accédez au dossier `[AEM Forms as a Cloud Service Git repository]/ui.content/src/main/content/jcr_root/etc/`.

1. Créez un `etc` sous `jcr_root` , le cas échéant.

1. Création d’un dossier `languages` sous le `etc` , le cas échéant.

   ![Texte de remplacement](etc-content-xml.png)

1. Créez un `.content.xml` sous le `languages` dossier. Ajoutez le contenu suivant au fichier :

   ```XML
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:nt="http://www.jcp.org/jcr/nt/1.0"
   jcr:primaryType="nt:unstructured"
   languages="[de,es,fr,it,pt-br,zh-cn,zh-tw,ja,ko-kr]"/>
   ```

1. Ajoutez le code de paramètres régionaux au `languages` . Par exemple, il a ajouté le hindi à l’exemple de code suivant.


   ```XML
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:nt="http://www.jcp.org/jcr/nt/1.0"
   jcr:primaryType="nt:unstructured"
   languages="[de,es,fr,it,pt-br,zh-cn,zh-tw,ja,ko-kr,hi]"/>
   ```

1. Ajoutez les dossiers nouvellement créés dans le `filter.xml` under `/ui.content/src/main/content/meta-inf/vault/filter.xml` en tant que :

   ```
   <filter root="/etc/languages"/>
   ```

   ![Ajoutez les dossiers nouvellement créés dans le `filter.xml` under `/ui.content/src/main/content/meta-inf/vault/filter.xml`](langauge-filter.png)

### 6. Validez les modifications et déployez le pipeline {#commit-changes-in-repo-deploy-pipeline}

Validez les modifications dans le référentiel GIT après l’ajout du nouveau paramètre régional. Déployez votre code à l’aide du pipeline de pile pleine. Découvrez [comment configurer un pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=fr#setup-pipeline) pour ajouter une nouvelle prise en charge de paramètres régionaux.

Une fois l’exécution du pipeline terminée, le nouveau paramètre régional ajouté est prêt à l’emploi.

## Aperçu d’un formulaire adaptatif avec les paramètres régionaux nouvellement ajoutés {#use-added-locale-in-af}

Effectuez les étapes suivantes pour prévisualiser un fichier adaptatif avec les paramètres régionaux nouvellement ajoutés :

1. Connectez-vous à votre instance AEM Forms as a Cloud Service.
1. Accédez à **Formulaires** > **Formulaires et documents**.
1. Sélectionnez un formulaire adaptatif, puis cliquez sur **Ajouter un dictionnaire**. L’assistant **Ajouter un dictionnaire au projet de traduction** s’affiche.
1. Spécifiez le **Titre du projet** et sélectionnez les **Langues cibles** dans le menu déroulant de l’assistant **Ajouter un dictionnaire au projet de traduction**.
1. Cliquez sur **Terminé** et exécutez le projet de traduction créé.
1. Sélectionnez un formulaire adaptatif et cliquez sur **Aperçu au format HTML**.
1. Ajoutez `&afAcceptLang=<locale-name>` dans l’URL d’un formulaire adaptatif.
1. Actualisez la page et le formulaire adaptatif est rendu dans un paramètre régional spécifié.

Deux méthodes permettent d’identifier les paramètres régionaux d’un formulaire adaptatif. Lors du rendu d’un formulaire adaptatif, il identifie les paramètres régionaux nécessaires :

* Récupération du sélecteur `[local]` dans l’URL du formulaire adaptatif. Le format de l’URL est `http:/[AEM Forms Server URL]/content/forms/af/[afName].[locale].html?wcmmode=disabled`. L’utilisation du sélecteur `[local]` permet de mettre en cache un formulaire adaptatif ;

* La récupération des paramètres suivants dans l’ordre indiqué :

   * Paramètre de requête `afAcceptLang`
Pour remplacer les paramètres régionaux du navigateur des utilisateurs, vous pouvez transmettre la variable `afAcceptLang` paramètre de requête pour forcer le paramètre régional. Par exemple, l’URL ci-dessous force le rendu du formulaire dans le paramètre régional français canadien :
     `https://'[server]:[port]'/<contextPath>/<formFolder>/<formName>.html?wcmmode=disabled&afAcceptLang=ca-fr`

   * La langue du navigateur défini pour l’utilisateur ou l’utilisatrice, qui est spécifiée dans la demande par le biais de l’en-tête `Accept-Language`.

Si aucune bibliothèque cliente pour le paramètre régional requis n’existe, elle recherche une bibliothèque cliente pour le code de langue présent dans le paramètre régional. Par exemple, si le paramètre régional requis est `en_ZA` (en anglais d’Afrique du Sud) et la bibliothèque cliente pour `en_ZA` n’existe pas, le formulaire adaptatif utilise la bibliothèque cliente pour `en` (anglais), s’il existe. Toutefois, si aucune de ces bibliothèques n’existe, le formulaire adaptatif utilise le dictionnaire correspondant au paramètre régional `en`.

Une fois le paramètre régional identifié, le formulaire adaptatif sélectionne le dictionnaire qui lui est spécifique. Si le dictionnaire spécifique au formulaire correspondant au paramètre régional requis est introuvable, il utilise le dictionnaire correspondant à la langue dans laquelle le formulaire adaptatif est créé.

Si aucune information de paramètres régionaux n’est disponible, le formulaire adaptatif s’affiche dans sa langue d’origine, la langue utilisée lors du développement des formulaires.


## Bonnes pratiques pour la prise en charge d’une nouvelle localisation {#best-practices}

* Adobe recommande de créer un projet de traduction après la création d’un formulaire adaptatif.

* Lorsque de nouveaux champs sont ajoutés dans un formulaire adaptatif existant :
   * **Pour la traduction automatique** : recréez le dictionnaire et exécutez le projet de traduction. Les champs ajoutés à un formulaire adaptatif après la création d’un projet de traduction ne sont pas traduits.
   * **Pour la traduction humaine** : exportez le dictionnaire via `[server:port]/libs/cq/i18n/gui/translator.html`. Mettez à jour le dictionnaire avec les champs nouvellement ajoutés et téléchargez-le.


