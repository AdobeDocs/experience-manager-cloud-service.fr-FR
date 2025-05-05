---
title: Comment ajouter la prise en charge de nouveaux paramètres régionaux à un formulaire adaptatif en fonction des composants principaux ?
description: Découvrez comment ajouter de nouveaux paramètres régionaux pour un formulaire adaptatif.
feature: Adaptive Forms, Core Components
Role: Developer, Author
exl-id: bc06542b-84c8-4c6a-a305-effbd16d5630
role: User, Developer
source-git-commit: cc2a226898f5dbe9073ba9b5a859218da664b1d7
workflow-type: tm+mt
source-wordcount: '2124'
ht-degree: 8%

---

# Ajout d’un paramètre régional pour Forms adaptatif basé sur les composants principaux {#supporting-new-locales-for-adaptive-forms-localization}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| Composants de base | [Cliquez ici](supporting-new-language-localization.md) |
| Composants principaux | Cet article |

<span class="preview"> La fonctionnalité de prise en charge de la langue de droite à gauche est disponible dans le programme des premiers adopteurs. Vous pouvez écrire à aem-forms-ea@adobe.com à partir de votre adresse e-mail officielle pour rejoindre le programme d’adoption précoce et demander l’accès à la fonctionnalité. </span>

AEM Forms fournit une prise en charge immédiate des paramètres régionaux en anglais (en), espagnol (es), français (fr), italien (it), allemand (de), japonais (ja), portugais du Brésil (pt-BR), chinois (zh-CN), chinois taïwanais (zh-TW) et coréen (ko-KR). Vous pouvez également ajouter la prise en charge d’autres paramètres régionaux, comme Hindi(hi_IN). Vous pouvez également présenter Adaptive Forms dans une langue de droite à gauche (RTL) telle que l’arabe, le persan et l’ourdou en ajoutant ces paramètres régionaux.

>[!VIDEO](https://video.tv.adobe.com/v/3433132/adaptive-forms-rtl--arabic-hebrew-farsi)

## Comment AEM Forms détermine-t-il les paramètres régionaux d’un formulaire adaptatif ?

Pour une localisation correcte, il est essentiel de comprendre comment AEM Forms sélectionne les paramètres régionaux du rendu d’un formulaire adaptatif. Voici une répartition du processus de sélection :

### Sélection des paramètres régionaux en fonction de la priorité

AEM Forms donne la priorité aux méthodes suivantes pour déterminer les paramètres régionaux d’un formulaire adaptatif :

1. **Sélecteur de paramètres régionaux de l’URL ([locale])** :

   Le système donne la priorité aux paramètres régionaux spécifiés dans l’URL à l’aide du sélecteur [locale] . Ce format permet la mise en cache pour de meilleures performances.

   Format : l’URL suit ce format : http:/[URL du serveur AEM Forms]/content/forms/af/[afName].[locale].html?wcmmode=disabled.

   Exemple : https://[server]/content/forms/af/contact-us.hi.html effectue le rendu du formulaire en hindi.


1. **Paramètre de requête afAcceptLang** :

   Pour remplacer les paramètres régionaux du navigateur de l’utilisateur, vous pouvez utiliser le paramètre `afAcceptLang` dans l’URL.

   Exemple : https://[server]/forms/af/survey.ca-fr.html?afAcceptLang=ca-fr force le rendu du formulaire en français canadien.

1. **Paramètre régional du navigateur de l’utilisateur (en-tête Accept-Language)** :

   Si aucun autre paramètre régional n’est spécifié, AEM Forms prend en compte le paramètre régional du navigateur de l’utilisateur envoyé à l’aide de l’en-tête `Accept-Language`.


### Mécanisme de secours :


* Si une bibliothèque cliente (processus d’ajout d’un nouveau paramètre régional, comme expliqué plus loin dans ce document) pour le paramètre régional requis n’est pas disponible, AEM Forms recherche une bibliothèque en fonction du code de langue dans le paramètre régional.

  Exemple : si en_ZA (anglais d’Afrique du Sud) est demandé et qu’il n’existe pas de bibliothèque en_ZA, il utilise en (anglais) s’il est disponible.

  Si aucune bibliothèque cliente appropriée n’est trouvée, le dictionnaire par défaut (principalement `en`) pour le langage de création du formulaire est utilisé.

  En l’absence d’informations sur les paramètres régionaux, le formulaire adaptatif s’affiche dans la langue d’origine utilisée lors du développement.


## Conditions préalables pour l’ajout d’un paramètre régional

Avant de commencer à ajouter un nouveau paramètre régional pour votre Forms adaptatif, vérifiez que vous disposez des éléments suivants :

**Logiciel :**

* Éditeur de texte brut (IDE) : bien que tout éditeur de texte brut puisse fonctionner, un environnement de développement intégré (IDE) comme [Microsoft Visual Studio Code](https://code.visualstudio.com/download) offre des fonctionnalités avancées pour faciliter la modification.

* Git : ce système de contrôle de version est nécessaire pour gérer les modifications de code. Si vous ne l&#39;avez pas installé, téléchargez-le depuis [https://git-scm.com](https://git-scm.com).


**Référentiel de code :**

Cloner le référentiel des composants principaux de Forms adaptatif : vous avez besoin d’une bibliothèque cliente à partir de ce référentiel pour ajouter un paramètre régional. Pour cloner le référentiel :

1. Ouvrez la ligne de commande ou la fenêtre de terminal.

1. Accédez à l’emplacement souhaité sur votre ordinateur où stocker le référentiel (par exemple, /adaptive-forms-core-components).

1. Exécutez la commande suivante pour cloner le référentiel :

   ```
   git clone https://github.com/adobe/aem-core-forms-components.git
   ```

   Cette commande télécharge le référentiel et crée un dossier nommé `aem-core-forms-components` sur votre ordinateur. Dans ce guide, nous nous référons à ce dossier sous le nom de `[Adaptive Forms Core Components repository]`.


## Ajouter un paramètre régional {#add-localization-support-for-non-supported-locales}

Pour ajouter la prise en charge de nouveaux paramètres régionaux à un formulaire adaptatif en fonction des composants principaux, procédez comme suit :

### Clonage de votre référentiel Git AEM as a Cloud Service

1. Ouvrez la ligne de commande et choisissez un répertoire pour stocker votre référentiel AEM as a Cloud Service, tel que `/cloud-service-repository/`.

1. Exécutez la commande ci-dessous pour cloner le référentiel :

   ```SHELL
   git clone https://git.cloudmanager.adobe.com/<organization-name>/<program id>/
   ```

   Pour cloner votre référentiel Git, vous avez besoin d’informations :

   * **Nom de l’organisation** : cela identifie votre équipe ou votre projet dans Adobe Experience Manager as a Cloud Service (AEM as a Cloud Service).

   * **ID de programme** : indique le programme associé à votre référentiel.

   * **Credentials** : vous avez besoin d’un nom d’utilisateur et d’un mot de passe (ou d’un jeton d’accès personnel) pour accéder au référentiel en toute sécurité.

   **Où trouver ces informations ?**

   Pour obtenir des instructions détaillées sur la localisation de ces détails, reportez-vous à l’article de Adobe Experience League &quot;[Accès à Git](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#accessing-git)&quot;.

   **Votre projet est prêt !**

   Une fois la commande terminée, un nouveau dossier est créé dans votre répertoire local. Ce dossier porte le nom de votre programme (par exemple, program-id). Ce dossier contient tous les fichiers et le code téléchargés à partir de votre référentiel Git AEM as a Cloud Service.

   Dans ce guide, nous nous référons à ce dossier sous le nom de `[AEMaaCS project directory]`.


### Ajouter le nouveau paramètre régional au Guide Localization Service

1. Ouvrez le dossier du référentiel dans un éditeur.

   ![Dossier Référentiel dans un éditeur](/help/forms/assets/repository-folder-in-an-editor.png)

1. Recherchez le fichier `Guide Localization Service.cfg.json`. Ce fichier contrôle les paramètres régionaux pris en charge par votre application AEM Forms. Vous pouvez modifier ce fichier pour ajouter un nouveau paramètre régional.

   * **Fichier existant** : si le fichier existe déjà, localisez-le dans votre répertoire de projet AEM Forms. L’emplacement type est :

     ```Shell
     [AEMaaCS project directory]/ui.config/src/main/content/jcr_root/apps/<appid>/osgiconfig/config`. 
     ```

     Remplacez `<appid>` par l’ID d’application spécifique à votre projet. Vous pouvez trouver `<appid>` pour votre projet AEM dans le fichier `archetype.properties` .

     ![Propriétés de l’archétype](/help/forms/assets/archetype-properties.png)

   * **Nouveau fichier** : si le fichier n’existe pas, vous devez le créer au même emplacement que celui mentionné ci-dessus. Ne copiez pas le nom du fichier à partir de ce document, mais saisissez-le manuellement. Le nom de fichier `Guide Localization Service.cfg.json` comprend des espaces. Il s’agit d’une faute intentionnelle et non d’une faute de frappe dans la documentation.

     Voici un exemple de fichier avec la liste des paramètres régionaux OOTB pris en charge :

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

1. Ajoutez le code de paramètres régionaux correspondant à la langue souhaitée au fichier.
   1. Utilisez la [Liste des codes ISO 639-1](https://en.wikipedia.org/wiki/List_of_ISO_639_language_codes) pour trouver le code à deux lettres représentant la langue souhaitée.

   1. Insérez le code de paramètres régionaux dans le fichier `Guide Localization Service.cfg.json`. Voici quelques exemples :

      * Langues écrites de gauche à droite :
         * Anglais (Etats-Unis) : en-US
         * Espagnol (Espagne) : es-ES
         * Français (France) : fr-FR
      * Langues écrites de droite à gauche :
         * Arabe (Emirats arabes unis) : ar-ae
         * Hébreu : he (ou iw pour référence historique)
         * Farsi : fa

1. Après avoir apporté des modifications, assurez-vous que le fichier `Guide Localization Service.cfg.json` est correctement formaté en tant que fichier JSON valide. Des erreurs de mise en forme JSON peuvent l’empêcher de fonctionner correctement. Enregistrez le fichier.



### Utilisation de l’exemple de bibliothèque cliente pour faciliter l’ajout de paramètres régionaux

AEM Forms fournit un exemple de bibliothèque cliente utile, `clientlib-it-custom-locale`, pour simplifier l’ajout de nouveaux paramètres régionaux. Cette bibliothèque fait partie du [référentiel des composants principaux de Forms adaptatif](https://github.com/adobe/aem-core-forms-components), disponible sur GitHub.


Avant de commencer, assurez-vous d’avoir une copie locale du [référentiel des composants principaux de Forms adaptatif]. Sinon, vous pouvez facilement le cloner à l’aide de Git avec la commande suivante :

```SHELL
git clone https://github.com/adobe/aem-core-forms-components.git
```

Cette commande télécharge l’ensemble du référentiel, y compris la bibliothèque clientlib-it-custom-locale, dans un répertoire nommé aem-core-forms-components sur votre ordinateur.

![Répertoire du référentiel des composants principaux de Forms adaptatif sur l’ordinateur local](/help/forms/assets/core-forms-components-repo-on-local-machine.png)

### Intégration de l’exemple de bibliothèque cliente

Maintenant, incorporons la bibliothèque `clientlib-it-custom-locale` dans votre répertoire de projet AEM as a Cloud Service, [AEMaaCS project directory] :

1. Recherchez l’exemple de bibliothèque cliente :

   Dans votre copie locale du [référentiel des composants principaux de Forms adaptatif], accédez au chemin suivant :

   ```
       /aem-core-forms-components/it/apps/src/main/content/jcr_root/apps/forms-core-components-it/clientlibs
   ```

1. Copiez et collez la bibliothèque :

   1. Copiez le dossier `clientlib-it-custom-locale`.

      ![Copie de clientlib-it-custom-locale](/help/forms/assets/clientlib-it-custom-locale-copy.png)

   1. Accédez au répertoire suivant dans votre [ répertoire de projet AEMaaCS ] :

      ```
      /ui.apps/src/main/content/jcr_root/apps/<app-id>/clientlib
      ```

      **Important** : remplacez `<app-id>` par l’identifiant réel de votre application.

   1. Collez le dossier `clientlib-it-custom-locale` copié dans ce répertoire.

      ![Collage de clientlib-it-custom-locale](/help/forms/assets/clientlib-it-custom-locale-paste.png)

1. Mettre à jour le chemin `aemLangUrl` dans `languageinit.js`

   1. Accédez au répertoire suivant dans votre [ répertoire de projet AEMaaCS ] :

      ```
      /ui.apps/src/main/content/jcr_root/apps/<app-id>/clientlib/clientlib-it-custom-locale/js
      ```

   1. Ouvrez le fichier `languageinit.js` dans votre éditeur.
   1. Recherchez la ligne suivante dans le fichier `languageinit.js` :

      `const aemLangUrl = /etc.clientlibs/forms-core-components-it/clientlibs/clientlib-it-custom-locale/resources/i18n/${lang}.json;`

   1. Remplacez `forms-core-components-it` par votre `<app-id>` (identifiant réel de votre application) dans la ligne ci-dessus.

      `const aemLangUrl = '/etc.clientlibs/<app-id>/clientlibs/clientlib-it-custom-locale/resources/i18n/${lang}.json';`

      ![language-init-file](/help/forms/assets/language-init-name-change.png)

>[!NOTE]
>  
> Si vous ne remplacez pas `forms-core-components-it` par le nom de votre projet ou `<app-id>`, la traduction du composant Sélecteur de date échoue.

### Créez un fichier pour vos nouveaux paramètres régionaux :

1. Accédez au répertoire de paramètres régionaux :

   Dans votre `[AEMaaCS project directory]`, accédez au chemin suivant :

   ```
       /ui.apps/src/main/content/jcr_root/apps/<program-id>/clientlibs/clientlib-it-custom-locale/resources/i18n/
   ```

   **Important** : remplacez `<program-id>` par votre ID d’application réel.

1. Recherchez l’exemple de fichier en anglais :

   AEM Forms fournit un [exemple de fichier de paramètres régionaux anglais (.json) sur GitHub](https://github.com/adobe/aem-core-forms-components/blob/master/ui.af.apps/src/main/content/jcr_root/apps/core/fd/af-clientlibs/core-forms-components-runtime-all/resources/i18n/en.json).

   Le fichier en anglais comprend l’ensemble de chaînes par défaut à titre de référence. Votre fichier spécifique au paramètre régional doit imiter la structure du fichier en anglais.

   Pour les langues comme l&#39;arabe, l&#39;hébreu et le farsi, le texte se lit de droite à gauche (RTL) au lieu de gauche à droite (LTR) comme l&#39;anglais. Pour vous assurer que vos formulaires s’affichent correctement dans ces langues, nous vous recommandons d’utiliser nos exemples de fichiers de paramètres régionaux comme guide. Ces fichiers fournissent une référence pour la mise en forme du texte, des dates et d’autres éléments pour les langues RTL. Vous trouverez des exemples de fichiers de paramètres régionaux pour :

   * [Arabe](/help/forms/assets/ar-ae.json)
   * [Hébreu](/help/forms/assets/he.json)
   * [Farsi](/help/forms/assets/fa.json)

   En exploitant ces fichiers d’exemple, vous pouvez vous assurer que vos formulaires offrent une expérience transparente aux utilisateurs travaillant dans des langues RTL.


1. Créez votre fichier de paramètres régionaux :

   1. Créez un fichier .json dans le répertoire `i18n`.
   1. Nommez le fichier à l’aide du code de paramètres régionaux correspondant à la langue souhaitée (par exemple, fr-FR.json pour le français et ar-ae.json pour l’arabe). La structure de ce fichier doit refléter le fichier de paramètres régionaux anglais.


1. Structure et traduction :

   1. Ouvrez le fichier nouvellement créé dans un éditeur de texte.

   1. Remplacez les valeurs anglaises par les traductions correspondantes pour votre langue cible.

   1. Une fois la traduction des chaînes terminée, enregistrez le fichier.




### Ajout de la prise en charge des paramètres régionaux au dictionnaire

Cette étape s’applique uniquement aux langues autres que les suivantes couramment prises en charge : anglais (en), allemand (de), espagnol (es), français (fr), italien (it), portugais brésilien (pt-br), chinois (simplifié - zh_cn), chinois (traditionnel - zh_tw), japonais (ja) et coréen (ko_kr).

1. Recherchez le dossier de configuration :

   Accédez au répertoire suivant dans votre [répertoire de projet AEMaaCS] :

   ```
   /ui.content/src/main/content/jcr_root/etc
   ```

1. Créez les dossiers nécessaires (le cas échéant) :

   Si le dossier `etc` n’existe pas dans le dossier `jcr_root`, créez-le. Dans `etc`, créez un autre dossier nommé `languages` s&#39;il manque.

1. Créez le fichier de configuration des paramètres régionaux :

   Dans le dossier `languages`, créez un fichier nommé `.content.xml`. Ne copiez pas le nom du fichier à partir de ce document, mais saisissez-le manuellement.

   ![ créez un nouveau fichier nommé `.content.xml`](etc-content-xml.png)

   Ouvrez ce fichier et collez le contenu suivant, en remplaçant [LOCALE_CODE] par le code de paramètres régionaux réel (par exemple, ar-ae pour l’arabe).


   ```XML
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:nt="http://www.jcp.org/jcr/nt/1.0"
         jcr:primaryType="nt:unstructured"
         languages="[de,es,fr,it,pt-br,zh-cn,zh-tw,ja,ko-kr,hi]"/>
   ```

   AVERTISSEMENT : ne remplacez pas la liste existante. Ajoutez plutôt votre nouveau code de paramètres régionaux entre crochets, séparés par des virgules, comme illustré ci-dessous (à l’aide de ar-ae comme exemple) :

   ```XML
   languages="[de,es,fr,it,pt-br,zh-cn,zh-tw,ja,ko-kr,hi,ar-ae]"
   ```

1. Incluez les nouveaux dossiers dans filter.xml :

   Accédez au fichier `/ui.content/src/main/content/meta-inf/vault/filter.xml` dans votre [ répertoire de projet AEMaaCS].

   Ouvrez le fichier et ajoutez la ligne suivante à la fin :

   ```
   <filter root="/etc/languages"/>
   ```

   ![Ajoutez les dossiers créés dans le `filter.xml` sous `/ui.content/src/main/content/meta-inf/vault/filter.xml`](langauge-filter.png)

1. Enregistrez le fichier.

### Déployer les paramètres régionaux nouvellement créés dans votre environnement AEM

Vous êtes maintenant prêt à utiliser le nouveau paramètre régional avec votre Forms adaptatif. Vous pouvez

* Déployez le [répertoire de projet AEMaaCS] d’AEM as a Cloud Service dans votre environnement de développement local pour essayer la nouvelle configuration des paramètres régionaux sur votre ordinateur local. Pour effectuer un déploiement sur votre environnement de développement local :

   1. Assurez-vous que votre environnement de développement local est opérationnel. Si vous n’avez pas encore configuré d’environnement de développement local, reportez-vous au guide sur la [configuration de l’environnement de développement local pour AEM Forms](/help/forms/setup-local-development-environment.md).

   1. Ouvrez la fenêtre de terminal ou l’invite de commande.

   1. Accédez au [ répertoire du projet AEMaaCS]

   1. Exécutez la commande suivante :

      ```
      mvn -PautoInstallPackage clean install
      ```

* Déployez le [répertoire de projet AEMaaCS] d’AEM as a Cloud Service dans votre environnement de Cloud Service. Pour effectuer un déploiement sur votre environnement de Cloud Service :

   1. Validez vos modifications :

      Après avoir ajouté la nouvelle configuration de paramètres régionaux, validez vos modifications avec un message Git clair décrivant l’ajout de paramètres régionaux (par exemple, &quot;Ajout de la prise en charge de [Nom de paramètre régional]&quot;).

   1. Déployer le code mis à jour :

      Déclenchez un déploiement de votre code par le biais du [pipeline de pile complète existant](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=fr#setup-pipeline). Cette opération génère et déploie automatiquement le code mis à jour avec la nouvelle prise en charge des paramètres régionaux.

      Si vous n’avez pas encore configuré de pipeline, reportez-vous au guide sur la configuration d’un pipeline pour AEM Forms as a Cloud Service[&#128279;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=fr#setup-pipeline).


## Aperçu d’un formulaire adaptatif avec les paramètres régionaux nouvellement ajoutés

Ces étapes vous guident tout au long de l’aperçu d’un formulaire adaptatif avec les paramètres régionaux nouvellement ajoutés :

1. Connectez-vous à votre instance AEM Forms as a Cloud Service.
1. Accédez à **Formulaires** > **Formulaires et documents**.
1. Sélectionnez un formulaire adaptatif, puis cliquez sur **Ajouter un dictionnaire**. L’assistant **Ajouter un dictionnaire au projet de traduction** s’affiche.
1. Spécifiez le **Titre du projet** et sélectionnez les **Langues cibles** dans le menu déroulant de l’assistant **Ajouter un dictionnaire au projet de traduction**.
1. Cliquez sur **Terminé** et exécutez le projet de traduction créé.
1. Accédez à **Formulaires** > **Formulaires et documents**.
1. Sélectionnez le formulaire adaptatif et choisissez l’option **Aperçu en tant qu’HTML** .
1. Ajoutez `&afAcceptLang=<locale-name>` à l’URL de prévisualisation et appuyez sur la touche Entrée. Remplacez `<locale-name>` par votre code de paramètres régionaux réel. Le formulaire adaptatif s’affiche dans les paramètres régionaux spécifiés.

## Bonnes pratiques pour la prise en charge d’une nouvelle localisation {#best-practices}

* Adobe recommande de créer un projet de traduction après la création d’un formulaire adaptatif. Cela simplifie le processus de localisation.
* Lorsque les composants Zone numérique et Sélecteur de date sont traduits dans un paramètre régional spécifique, des problèmes de mise en forme peuvent se produire. Pour atténuer ce problème, une option **Langue** a été incorporée dans la boîte de dialogue de configuration de [composant Sélecteur de date](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/date-picker#format-tab) et [composant Zone numérique](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/numeric-box#formats-configure-tab).


* Gestion des nouveaux champs :

   * **Traduction automatique** : si vous utilisez la traduction automatique, vous devez recréer le dictionnaire et exécuter à nouveau le projet de traduction[&#128279;](/help/forms/using-aem-translation-workflow-to-localize-adaptive-forms-core-components.md) après avoir ajouté de nouveaux champs à un formulaire adaptatif existant.  Les nouveaux champs ajoutés après le projet de traduction initial restent non traduits.

   * **Traduction humaine** : pour les processus de traduction humaine, exportez le dictionnaire à l’aide de l’interface utilisateur à l’adresse `[AEM Forms Server]/libs/cq/i18n/gui/translator.html`. Mettez à jour le dictionnaire des nouveaux champs et téléchargez la version révisée.


## Voir également {#see-also}

{{see-also}}

* [Générer un document d’enregistrement pour les formulaires adaptatifs](/help/forms/generate-document-of-record-core-components.md)
* [Ajouter un formulaire adaptatif à une page AEM Sites ou un fragment d’expérience](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)

