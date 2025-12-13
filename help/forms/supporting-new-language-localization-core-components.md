---
title: Comment ajouter la prise en charge de nouveaux paramètres régionaux à un formulaire adaptatif basé sur les composants principaux ?
description: Découvrez comment ajouter de nouveaux paramètres régionaux pour un formulaire adaptatif.
feature: Adaptive Forms, Core Components
Role: Developer, Author
exl-id: bc06542b-84c8-4c6a-a305-effbd16d5630
role: User, Developer
source-git-commit: 8f39bffd07e3b4e88bfa200fec51572e952ac837
workflow-type: tm+mt
source-wordcount: '2154'
ht-degree: 9%

---

# Ajout des paramètres régionaux pour les formulaires adaptatifs sur la base des composants principaux {#supporting-new-locales-for-adaptive-forms-localization}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| Composants de base | [Cliquer ici](supporting-new-language-localization.md) |
| Composants principaux | Cet article |

<span class="preview"> La fonctionnalité de prise en charge linguistique de droite à gauche est disponible dans le cadre du programme des utilisateurs et utilisatrices précoces. Vous pouvez écrire à aem-forms-ea@adobe.com à partir de votre identifiant e-mail officiel pour rejoindre le programme d’adoption précoce et demander l’accès à la fonctionnalité. </span>

AEM Forms fournit une prise en charge immédiate des paramètres régionaux en anglais (en), espagnol (es), français (fr), italien (it), allemand (de), japonais (ja), portugais du Brésil (pt-BR), chinois (zh-CN), chinois taïwanais (zh-TW) et coréen (ko-KR). Vous pouvez également ajouter la prise en charge d’autres paramètres régionaux, comme l’hindi (hi_IN). Vous pouvez également présenter le Forms adaptatif dans une langue de droite à gauche (RTL) comme l’arabe, le persan et l’ourdou en ajoutant ces paramètres régionaux.

>[!VIDEO](https://video.tv.adobe.com/v/3433132/adaptive-forms-rtl--arabic-hebrew-farsi)

## Applicabilité et cas d’utilisation

### Assurance

## AEM Forms prend-il en charge les cas d’utilisation d’assurance multilingues ?

Oui. AEM Forms prend en charge les expériences de formulaires multilingues, ce qui est important pour les assureurs opérant entre les régions et les langues.

## Comment AEM Forms détermine-t-il les paramètres régionaux d’un formulaire adaptatif ?

Il est essentiel de comprendre comment AEM Forms sélectionne les paramètres régionaux pour le rendu d’un formulaire adaptatif afin d’assurer une localisation correcte. Voici une répartition du processus de sélection :

### Sélection des paramètres régionaux en fonction de la priorité

AEM Forms donne la priorité aux méthodes suivantes pour déterminer les paramètres régionaux d’un formulaire adaptatif :

1. **Sélecteur de paramètre régional d’URL ([paramètre régional])** :

   Le système donne la priorité au paramètre régional spécifié dans l’URL à l’aide du sélecteur [locale]. Ce format permet la mise en cache pour de meilleures performances.

   Format : l’URL suit ce format : http:/[URL du serveur AEM Forms]/content/forms/af/[afName].[locale].html?wcmmode=disabled.

   Exemple : https://[server]/content/forms/af/contact-us.hi.html effectue le rendu du formulaire en hindi.


1. **afAcceptLang, paramètre de requête** :

   Pour remplacer les paramètres régionaux du navigateur de l’utilisateur, vous pouvez utiliser le paramètre `afAcceptLang` dans l’URL.

   Exemple : https://[server]/forms/af/survey.ca-fr.html?afAcceptLang=ca-fr force le rendu du formulaire en français canadien.

1. **Paramètres régionaux du navigateur de l’utilisateur (en-tête Accept-Language)** :

   Si aucun autre paramètre régional n’est spécifié, AEM Forms prend en compte les paramètres régionaux du navigateur de l’utilisateur envoyés à l’aide de l’en-tête `Accept-Language`.


### Mécanisme de secours :


* Si une bibliothèque cliente (processus d’ajout d’un nouveau paramètre régional, expliqué plus loin dans ce document) pour le paramètre régional requis n’est pas disponible, AEM Forms recherche une bibliothèque en fonction du code de langue du paramètre régional.

  Exemple : si en_ZA (anglais d’Afrique du Sud) est demandé et qu’il n’existe pas de bibliothèque en_ZA, il utilise en (anglais) s’il est disponible.

  Si aucune bibliothèque cliente appropriée n’est trouvée, le dictionnaire par défaut (principalement `en`) pour la langue de création du formulaire est utilisé.

  En l’absence d’informations sur les paramètres régionaux, le formulaire adaptatif s’affiche dans sa langue d’origine utilisée lors du développement.


## Conditions préalables pour l’ajout d’un paramètre régional

Avant de commencer à ajouter un nouveau paramètre régional pour votre Forms adaptative, vérifiez que vous disposez des éléments suivants :

**Logiciel:**

* Éditeur de texte brut (IDE) : bien que tout éditeur de texte brut puisse fonctionner, un environnement de développement intégré (IDE) comme [Microsoft Visual Studio Code](https://code.visualstudio.com/download) offre des fonctionnalités avancées pour faciliter la modification.

* Git : ce système de contrôle de version est nécessaire pour gérer les modifications de code. Si vous ne l’avez pas installé, téléchargez-le à partir de [https://git-scm.com](https://git-scm.com).


**Référentiel de code :**

Clonez le référentiel des composants principaux de Forms adaptative : vous avez besoin d’une bibliothèque cliente de ce référentiel pour ajouter des paramètres régionaux. Pour cloner le référentiel :

1. Ouvrez la ligne de commande ou la fenêtre du terminal.

1. Accédez à l’emplacement souhaité sur votre ordinateur, où vous souhaitez stocker le référentiel (par exemple, /adaptive-forms-core-components).

1. Exécutez la commande suivante pour cloner le référentiel :

   ```
   git clone https://github.com/adobe/aem-core-forms-components.git
   ```

   Cette commande télécharge le référentiel et crée un dossier nommé `aem-core-forms-components` sur votre ordinateur. Tout au long de ce guide, nous nous référons à ce dossier sous le nom de `[Adaptive Forms Core Components repository]`.


## Ajouter des paramètres régionaux {#add-localization-support-for-non-supported-locales}

Pour ajouter la prise en charge de nouveaux paramètres régionaux à un formulaire adaptatif basé sur les composants principaux, procédez comme suit :

### Clonage de votre référentiel Git AEM as a Cloud Service

1. Ouvrez la ligne de commande et sélectionnez un répertoire pour stocker votre référentiel AEM as a Cloud Service, tel que `/cloud-service-repository/`.

1. Exécutez la commande ci-dessous pour cloner le référentiel :

   ```SHELL
   git clone https://git.cloudmanager.adobe.com/<organization-name>/<program id>/
   ```

   Pour cloner votre référentiel Git, vous avez besoin de certaines informations :

   * **Nom de l’organisation** : identifie votre équipe ou votre projet dans Adobe Experience Manager as a Cloud Service (AEM as a Cloud Service).

   * **ID du programme** : il s’agit du programme associé à votre référentiel.

   * **Informations d’identification** : vous avez besoin d’un nom d’utilisateur et d’un mot de passe (ou d’un jeton d’accès personnel) pour accéder au référentiel en toute sécurité.

   **Où trouver ces informations ?**

   Pour obtenir des instructions détaillées sur la localisation de ces détails, reportez-vous à l’article Adobe Experience League « [Accès à Git](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=fr#accessing-git) ».

   **Votre projet est prêt !**

   Une fois la commande terminée, un nouveau dossier est créé dans votre répertoire local. Ce dossier porte le nom de votre programme (par exemple, program-id). Ce dossier contient tous les fichiers et le code téléchargés à partir de votre référentiel Git AEM as a Cloud Service.

   Tout au long de ce guide, nous nous référons à ce dossier sous le nom de `[AEMaaCS project directory]`.


### Ajouter les nouveaux paramètres régionaux au Guide Localization Service

1. Ouvrez le dossier du référentiel dans un éditeur.

   ![Dossier du référentiel dans un éditeur](/help/forms/assets/repository-folder-in-an-editor.png)

1. Recherchez le fichier `Guide Localization Service.cfg.json`. Ce fichier contrôle les paramètres régionaux pris en charge par votre application AEM Forms. Vous pouvez modifier ce fichier pour ajouter un nouveau paramètre régional.

   * **Fichier existant** : si le fichier existe déjà, localisez-le dans votre répertoire de projet AEM Forms. L’emplacement type est :

     ```Shell
     [AEMaaCS project directory]/ui.config/src/main/content/jcr_root/apps/<appid>/osgiconfig/config`. 
     ```

     Remplacez `<appid>` par l’ID d’application spécifique à votre projet. Le `<appid>` de votre projet AEM se trouve dans le fichier `archetype.properties`.

     ![Propriétés de l’archétype](/help/forms/assets/archetype-properties.png)

   * **Nouveau fichier** : si le fichier n&#39;existe pas, vous devez le créer au même emplacement que celui mentionné ci-dessus. Ne copiez pas et ne collez pas le nom du fichier à partir de ce document, mais saisissez-le manuellement. Le nom du fichier `Guide Localization Service.cfg.json` comprend des espaces. Il s’agit d’une intention et non d’une faute de frappe dans la documentation.

     Voici un exemple de fichier avec la liste des paramètres régionaux pris en charge par l’usine :

     ```
         {
             "supportedLocales":[
             "en",
             "fr",
             "de",
             "ja",
             "pt-br",
             "zh-cn",
             "zh-tw",
             "ko-kr",
             "it",
             "es"
             ]
         }
     ```

1. Ajoutez au fichier le code de paramètre régional correspondant à la langue souhaitée.
   1. Utilisez la [Liste des codes ISO 639-1](https://en.wikipedia.org/wiki/List_of_ISO_639_language_codes) pour trouver le code à deux lettres représentant la langue souhaitée.

   1. Incluez le code de paramètre régional dans le fichier `Guide Localization Service.cfg.json`. Voici quelques exemples :

      * Langues de gauche à droite :
         * Anglais (États-Unis) : en-US
         * Espagnol (Espagne) : es-ES
         * Français (France) : fr-FR
      * Langues écrites de droite à gauche :
         * Arabe (Émirats arabes unis) : ar-ae
         * Hébreu : il (ou est pour référence historique)
         * Farsi : fa

1. Après avoir apporté des modifications, assurez-vous que le fichier `Guide Localization Service.cfg.json` est correctement formaté en tant que fichier JSON valide. Des erreurs de formatage JSON peuvent empêcher le système de fonctionner correctement. Enregistrez le fichier.



### Tirez parti de l’exemple de bibliothèque cliente pour ajouter facilement des paramètres régionaux

AEM Forms fournit un exemple utile de bibliothèque cliente, `clientlib-it-custom-locale`, pour simplifier l’ajout de nouveaux paramètres régionaux. Cette bibliothèque fait partie du [référentiel des composants principaux de Forms adaptatif](https://github.com/adobe/aem-core-forms-components), disponible sur GitHub.


Avant de commencer, vérifiez que vous disposez d’une copie locale du [référentiel des composants principaux de Forms adaptatif]. Sinon, vous pouvez facilement le cloner à l’aide de Git avec la commande suivante :

```SHELL
git clone https://github.com/adobe/aem-core-forms-components.git
```

Cette commande télécharge l’ensemble du référentiel, y compris la bibliothèque clientlib-it-custom-locale, dans un répertoire nommé aem-core-forms-components sur votre ordinateur.

![Répertoire de référentiel des composants principaux de Forms adaptatif sur l’ordinateur local](/help/forms/assets/core-forms-components-repo-on-local-machine.png)

### Intégration de l’exemple de bibliothèque cliente

Maintenant, incorporons la bibliothèque `clientlib-it-custom-locale` dans votre répertoire de projet AEM as a Cloud Service [AEMaaCS] :

1. Recherchez l’exemple de bibliothèque cliente :

   Dans votre copie locale du [référentiel des composants principaux de Forms adaptatif], accédez au chemin suivant :

   ```
       /aem-core-forms-components/it/apps/src/main/content/jcr_root/apps/forms-core-components-it/clientlibs
   ```

1. Copiez et collez la bibliothèque :

   1. Copiez le dossier `clientlib-it-custom-locale`.

      ![Copie de clientlib-it-custom-locale](/help/forms/assets/clientlib-it-custom-locale-copy.png)

   1. Accédez au répertoire suivant dans votre [répertoire de projet AEMaaCS] :

      ```
      /ui.apps/src/main/content/jcr_root/apps/<app-id>/clientlib
      ```

      **Important** : remplacez `<app-id>` par l’ID réel de votre application.

   1. Collez le dossier `clientlib-it-custom-locale` copié dans ce répertoire.

      ![Collage de clientlib-it-custom-locale](/help/forms/assets/clientlib-it-custom-locale-paste.png)

1. Mettre à jour `aemLangUrl` chemin dans `languageinit.js`

   1. Accédez au répertoire suivant dans votre [répertoire de projet AEMaaCS] :

      ```
      /ui.apps/src/main/content/jcr_root/apps/<app-id>/clientlib/clientlib-it-custom-locale/js
      ```

   1. Ouvrez le fichier `languageinit.js` dans l’éditeur.
   1. Recherchez la ligne suivante dans le fichier `languageinit.js` :

      `const aemLangUrl = /etc.clientlibs/forms-core-components-it/clientlibs/clientlib-it-custom-locale/resources/i18n/${lang}.json;`

   1. Remplacez `forms-core-components-it` par votre `<app-id>` (ID réel de votre application) dans la ligne ci-dessus.

      `const aemLangUrl = '/etc.clientlibs/<app-id>/clientlibs/clientlib-it-custom-locale/resources/i18n/${lang}.json';`

      ![language-init-file](/help/forms/assets/language-init-name-change.png)

>[!NOTE]
>  
> Si vous ne remplacez pas `forms-core-components-it` par le nom ou le `<app-id>` de votre projet, le composant Sélecteur de date ne peut pas être traduit.

### Créez un fichier pour vos nouveaux paramètres régionaux :

1. Accédez au répertoire des paramètres régionaux :

   Dans votre `[AEMaaCS project directory]`, accédez au chemin suivant :

   ```
       /ui.apps/src/main/content/jcr_root/apps/<program-id>/clientlibs/clientlib-it-custom-locale/resources/i18n/
   ```

   **Important** : remplacez `<program-id>` par votre ID d’application réel.

1. Recherchez l’exemple de fichier de langue anglaise :

   AEM Forms fournit un [exemple de fichier de paramètres régionaux d’anglais (.json) sur GitHub](https://github.com/adobe/aem-core-forms-components/blob/master/ui.af.apps/src/main/content/jcr_root/apps/core/fd/af-clientlibs/core-forms-components-runtime-all/resources/i18n/en.json).

   Le fichier de langue anglaise inclut l’ensemble par défaut de chaînes à titre de référence. Votre fichier spécifique aux paramètres régionaux doit imiter la structure du fichier de langue anglaise.

   Pour des langues comme l’arabe, l’hébreu et le farsi, le texte se lit de droite à gauche (RTL) au lieu de gauche à droite (LTR) comme l’anglais. Pour que vos formulaires s’affichent correctement dans ces langues, nous vous recommandons d’utiliser nos exemples de fichiers de paramètres régionaux comme guide. Ces fichiers fournissent une référence pour le format du texte, des dates et d’autres éléments pour les langues de RTL. Vous trouverez des exemples de fichiers de paramètres régionaux pour :

   * [Arabe](/help/forms/assets/ar-ae.json)
   * [Hébreu](/help/forms/assets/he.json)
   * [farsi](/help/forms/assets/fa.json)

   En utilisant ces fichiers d’exemple, vous pouvez vous assurer que vos formulaires offrent une expérience transparente aux utilisateurs qui travaillent dans des langues de RTL.


1. Créez votre fichier de paramètres régionaux :

   1. Créez un fichier .json dans le répertoire `i18n`.
   1. Nommez le fichier à l’aide du code de paramètre régional approprié à la langue souhaitée (par exemple, fr-FR.json pour le français et ar-ae.json pour l’arabe). La structure de ce fichier doit refléter le fichier de paramètres régionaux anglais.


1. Structure et traduction :

   1. Ouvrez le fichier nouvellement créé dans un éditeur de texte.

   1. Remplacez les valeurs de l’anglais par les traductions correspondantes pour votre langue cible.

   1. Une fois que vous avez terminé de traduire les chaînes, enregistrez le fichier.




### Ajouter la prise en charge des paramètres régionaux au dictionnaire

Cette étape s’applique uniquement aux paramètres régionaux autres que les paramètres régionaux couramment pris en charge suivants : anglais (en), allemand (de), espagnol (es), français (fr), italien (it), portugais du Brésil (pt-br), chinois (simplifié - zh_cn), chinois (traditionnel - zh_tw), japonais (ja) et coréen (ko_kr).

1. Recherchez le dossier de configuration :

   Accédez au répertoire suivant dans votre [répertoire de projet AEMaaCS] :

   ```
   /ui.content/src/main/content/jcr_root/etc
   ```

1. Créez les dossiers nécessaires (s’ils sont manquants) :

   Si le dossier `etc` n’existe pas dans `jcr_root` dossier, créez-le. Dans `etc`, créez un autre dossier nommé `languages` s’il n’est pas présent.

1. Créez le fichier de configuration des paramètres régionaux :

   Dans le dossier `languages`, créez un fichier nommé `.content.xml`. Ne copiez pas et ne collez pas le nom du fichier à partir de ce document, mais saisissez-le manuellement.

   ![créez un fichier nommé `.content.xml`](etc-content-xml.png)

   Ouvrez ce fichier et collez le contenu suivant, en remplaçant [LOCALE_CODE] par le code de paramètre régional réel (par exemple, ar-ae pour l’arabe).


   ```XML
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:nt="http://www.jcp.org/jcr/nt/1.0"
         jcr:primaryType="nt:unstructured"
         languages="[de,es,fr,it,pt-br,zh-cn,zh-tw,ja,ko-kr,hi]"/>
   ```

   AVERTISSEMENT : ne pas remplacer la liste existante. Au lieu de cela, ajoutez votre nouveau code de paramètre régional entre crochets, séparés par des virgules, comme suit (en utilisant ar-ae comme exemple) :

   ```XML
   languages="[de,es,fr,it,pt-br,zh-cn,zh-tw,ja,ko-kr,hi,ar-ae]"
   ```

1. Incluez les nouveaux dossiers dans filter.xml :

   Accédez au fichier `/ui.content/src/main/content/meta-inf/vault/filter.xml` dans votre [répertoire de projet AEMaaCS].

   Ouvrez le fichier et ajoutez la ligne suivante à la fin :

   ```
   <filter root="/etc/languages"/>
   ```

   ![Ajoutez les dossiers créés dans le `filter.xml` sous `/ui.content/src/main/content/meta-inf/vault/filter.xml`](langauge-filter.png)

1. Enregistrez le fichier.

### Déployez le paramètre régional nouvellement créé dans votre environnement AEM

Vous êtes maintenant prêt à utiliser les nouveaux paramètres régionaux avec votre Forms adaptative. Vous pouvez :

* Déployez l’AEM as a Cloud Service [répertoire de projet AEMaaCS] dans votre environnement de développement local pour essayer la nouvelle configuration des paramètres régionaux sur votre ordinateur local. Pour déployer sur votre environnement de développement local :

   1. Vérifiez que votre environnement de développement local est opérationnel. Si vous n’avez pas encore configuré d’environnement de développement local, reportez-vous au guide sur la [Configuration d’un environnement de développement local pour AEM Forms](/help/forms/setup-local-development-environment.md).

   1. Ouvrez la fenêtre du terminal ou l’invite de commande.

   1. Accédez au répertoire du projet [AEMaaCS]

   1. Exécutez la commande suivante :

      ```
      mvn -PautoInstallPackage clean install
      ```

* Déployez l’AEM as a Cloud Service, [répertoire de projet AEMaaCS], dans votre environnement Cloud Service. Pour effectuer un déploiement dans votre environnement Cloud Service :

   1. Validez Vos Modifications :

      Après avoir ajouté la nouvelle configuration des paramètres régionaux, validez vos modifications avec un message Git clair décrivant l’ajout des paramètres régionaux (par exemple, « Ajout de la prise en charge du [ Nom du paramètre régional »]).

   1. Déployez le code mis à jour :

      Déclenchez un déploiement de votre code via le [pipeline full stack existant](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=fr#setup-pipeline). Cela crée et déploie automatiquement le code mis à jour avec la nouvelle prise en charge des paramètres régionaux.

      Si vous n’avez pas encore configuré de pipeline, reportez-vous au guide sur [comment configurer un pipeline pour AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=fr#setup-pipeline).


## Prévisualiser un formulaire adaptatif avec des paramètres régionaux nouvellement ajoutés

Ces étapes vous guident tout au long de la prévisualisation d’un formulaire adaptatif avec le nouveau paramètre régional ajouté :

1. Connectez-vous à votre instance AEM Forms as a Cloud Service.
1. Accédez à **Formulaires** > **Formulaires et documents**.
1. Sélectionnez un formulaire adaptatif, puis cliquez sur **Ajouter un dictionnaire**. L’assistant **Ajouter un dictionnaire au projet de traduction** s’affiche.
1. Spécifiez le **Titre du projet** et sélectionnez les **Langues cibles** dans le menu déroulant de l’assistant **Ajouter un dictionnaire au projet de traduction**.
1. Cliquez sur **Terminé** et exécutez le projet de traduction créé.
1. Accédez à **Formulaires** > **Formulaires et documents**.
1. Sélectionnez le formulaire adaptatif et choisissez l’option **Prévisualiser sous HTML**.
1. Ajoutez `&afAcceptLang=<locale-name>` à l’URL d’aperçu et appuyez sur la touche Entrée. Remplacez `<locale-name>` par votre code de paramètres régionaux réel. Le formulaire adaptatif s’affiche dans les paramètres régionaux spécifiés.

## Bonnes pratiques pour la prise en charge d’une nouvelle localisation {#best-practices}

* Adobe recommande de créer un projet de traduction après la création d’un formulaire adaptatif. Cela simplifie le processus de localisation.
* Lorsque les composants Zone numérique et Sélecteur de date sont traduits en paramètres régionaux spécifiques, des problèmes de mise en forme peuvent survenir. Pour atténuer ce problème, une option **Langue** a été intégrée dans la boîte de dialogue de configuration du composant [Sélecteur de date](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/date-picker#format-tab) et [Zone numérique](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/numeric-box#formats-configure-tab).


* Gestion des nouveaux champs :

   * **Traduction automatique** : si vous utilisez la traduction automatique, vous devez recréer le dictionnaire et [&#x200B; le projet de traduction](/help/forms/using-aem-translation-workflow-to-localize-adaptive-forms-core-components.md) après avoir ajouté de nouveaux champs à un formulaire adaptatif existant. Les nouveaux champs ajoutés après le projet de traduction initial ne sont toujours pas traduits.

   * **Traduction humaine** : pour les workflows de traduction humaine, exportez le dictionnaire à l’aide de l’interface utilisateur à l’adresse `[AEM Forms Server]/libs/cq/i18n/gui/translator.html`. Mettez à jour le dictionnaire pour les nouveaux champs et chargez la version révisée.


## Voir également {#see-also}

{{see-also}}

* [Générer un document d’enregistrement pour les formulaires adaptatifs](/help/forms/generate-document-of-record-core-components.md)
* [Ajouter un formulaire adaptatif à une page AEM Sites ou un fragment d’expérience](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)

