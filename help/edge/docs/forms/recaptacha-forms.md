---
title: Utiliser reCAPTCHA avec Edge Delivery Services pour AEM Forms as a Cloud Service
description: Utiliser Google reCAPTCHA dans un formulaire EDS
feature: Edge Delivery Services
exl-id: ac104e23-f175-435f-8414-19847efa5825
role: Admin, Architect, Developer
source-git-commit: fe45123b3aefddaf02bc8584283941db168ba174
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 25%

---


# Utiliser reCAPTCHA avec Edge Delivery Services pour AEM Forms as a Cloud Service

<span>La fonctionnalité **reCAPTCHA** se trouve dans le programme de version préliminaire. Pour demander l’accès à la fonction **reCAPTCHA** pour les Edge Delivery Services AEM Forms, envoyez un courrier électronique à l’adresse mailto:aem-forms-ea@adobe.com.</span>

reCAPTCHA est un outil couramment utilisé pour protéger les sites web contre les activités frauduleuses, le spam et les abus. Dans Edge Delivery Services, le bloc de formulaire adaptatif permet d’ajouter Google reCAPTCHA pour distinguer les personnes des robots. Cette fonctionnalité permet aux utilisateurs et aux utilisatrices de protéger leur site web contre le spam et les abus.
Prenons l’exemple d’un formulaire de demande qui collecte des données telles que les dates de début et de fin d’un voyage, le prix d’une chambre, l’estimation du coût du voyage et les informations sur la personne qui voyage. Dans de tels cas, il existe un risque que des utilisateurs et des utilisatrices malveillants exploitent le formulaire pour envoyer des e-mails de phishing ou pour le saturer de contenu non pertinent ou nuisible en utilisant des robots de spam. L’intégration de reCAPTCHA fournit une sécurité supplémentaire en vérifiant que les envois proviennent d’utilisateurs et d’utilisatrices authentiques, réduisant en pratique les entrées de spam.

<!-- ![Recaptcha Image](/help/edge/docs/forms/assets/recaptcha-image.png){width="300" align="center"} -->

Les Edge Delivery Services ne prennent en charge que le paramètre **Score based(v3)-reCAPTCHA** pour le bloc de formulaire adaptatif.

![reCAPTCHA v2](/help/forms/assets/recaptcha-v2-invisible.png){width="300" align="center"}


À la fin de cet article, vous saurez accomplir ce qui suit :
* [Activation de Google reCAPTCHA pour un seul formulaire](#enable-google-recaptchas-for-a-single-form)
* [Activer reCAPTCHA pour tous les formulaires de votre site](#enable-recaptcha-for-all-the-forms)

## Conditions préalables

* Commencez le développement de Forms Edge Delivery Services en suivant les étapes décrites dans la section [Création d’un formulaire à l’aide du bloc Forms adaptatif](/help/edge/docs/forms/create-forms.md).
* Enregistrez votre domaine avec [Google reCAPTCHA et obtenez des informations d’identification](https://www.google.com/recaptcha/admin/create).

## Activation de Google reCAPTCHA pour un seul formulaire {#enable-google-recaptchas-for-a-single-form}

L’activation de Google reCAPTCHA pour un formulaire unique implique l’intégration du service Google reCAPTCHA dans un formulaire web spécifique afin d’éviter les envois automatisés d’abus ou de spam.

Pour activer Google reCAPTCHA pour un seul formulaire :
1. [Configuration de la clé secrète reCAPTCHA dans le fichier de configuration du projet](#configure-secret-key)
1. [Ajout de la clé de site reCAPTCHA à votre formulaire](#add-site-key)

Pour commencer à configurer reCaptcha dans Edge Delivery Services Forms, reportez-vous à la [feuille de calcul](/help/edge/docs/forms/assets/recaptcha.xlsx) suivante qui comprend la définition de formulaire pour un formulaire.

### Configuration de la clé secrète reCAPTCHA dans le fichier de configuration du projet {#configure-secret-key}

Le Secret du site pour le domaine enregistré avec Google reCAPTCHA est ajouté au projet du fichier de configuration (`.helix/config`) dans votre dossier de projet AEM sur Microsoft SharePoint ou Google Drive. Pour ajouter le Secret du site au fichier de configuration :

1. Accédez à votre dossier de projet AEM sur Microsoft® SharePoint ou Google Drive.
1. Créez le fichier `.helix/config.xlsx` dans votre dossier de projet AEM dans le site Microsoft SharePoint ou le fichier `.helix/config` dans AEM dossier de projet de votre lecteur Google.

   >[!NOTE]
   >
   > Le [ fichier de configuration de projet](https://www.aem.live/docs/configuration) est une feuille de calcul située à l’emplacement `/.helix/config`. Si le fichier n’existe pas, créez-le.

1. Ouvrez le fichier `config` et ajoutez les paires clé-valeur suivantes :

   * **captcha.secret** : valeur de clé secrète Google reCAPTCHA
   * **captcha.type** : reCAPTCHA v2

   >[!NOTE]
   >
   >  * Vous pouvez récupérer les clés reCAPTCHA de l’ [Admin Console Google reCAPTCHA](https://www.google.com/recaptcha/admin).
   >  * Vous devez spécifier la valeur de **captcha.type** dans le fichier `config` comme **reCAPTCHA v2**.

   Reportez-vous à la capture d’écran d’un fichier de configuration de projet ci-dessous :

   ![Fichier de configuration de projet](/help/forms/assets/recaptcha-config-file.png)

1. Enregistrez le fichier `config`.

1. Prévisualisez et publiez le fichier `config` à l’aide de [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

### Ajout de la clé de site reCAPTCHA à votre formulaire {#add-site-key}

La clé de site d’un domaine enregistré avec Google reCAPTCHA est ajoutée à la feuille de calcul du formulaire à protéger. Pour ajouter la clé Site à un formulaire :

1. Accédez au dossier de votre projet AEM sur Microsoft® SharePoint ou Google Drive et ouvrez votre feuille de calcul. Vous pouvez également créer une feuille de calcul pour un formulaire.
1. Insérez une ligne dans la feuille de calcul pour ajouter un nouveau champ en tant que CAPTCHA, avec les détails suivants :
   * **type** : captcha
   * **value** : valeur clé du site Google reCAPTCHA

   Reportez-vous à la capture d’écran ci-dessous, illustrant la feuille de calcul avec le nouveau type de ligne CAPTCHA :

   ![Feuille de calcul Recaptcha](/help/edge/docs/forms/assets/recaptcha-spreadsheet.png)

   >[!NOTE]
   >
   >  Vous pouvez récupérer les clés reCAPTCHA de l’ [Admin Console Google reCAPTCHA](https://www.google.com/recaptcha/admin).

1. Enregistrez la feuille de calcul.
1. Utilisez [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) pour prévisualiser et publier la feuille.

Après avoir ajouté une nouvelle ligne dans la définition de formulaire, un badge reCAPTCHA s’affiche dans le coin inférieur droit du formulaire. Cela permet de s’assurer que le formulaire est désormais protégé contre les activités frauduleuses, les spams et les abus.

![recaptcha-form](/help/edge/docs/forms/assets/recaptcha-form.png)

## Activer reCAPTCHA pour tous les formulaires de votre site{#enable-recaptcha-for-all-the-forms}

Pour appliquer Google reCAPTCHA à tous les formulaires de votre site qui utilisent le bloc Adaptive Forms, ignorez les étapes précédentes et incorporez directement la valeur `sitekey` dans le fichier `recaptcha.js`. Pour inclure la valeur de la clé du site dans le fichier `recaptcha.js` :

1. [Mise à jour de la clé de site Google reCAPTCHA dans le fichier recaptcha.js](#1-update-google-recaptcha-site-key-in-recaptchajs-file)
1. [Déployez le fichier et créez le projet.](#2-deploy-the-file-and-build-the-project)
1. [Aperçu du site à l’aide du sidekick AEM](#3-preview-the-site-using-the-aem-sidekick)

### Mise à jour de la clé de site Google reCAPTCHA dans le fichier recaptcha.js

1. Ouvrez le référentiel GitHub correspondant sur votre ordinateur local.
1. Accédez au dossier `[../Form Block/integrations]` et ouvrez le fichier `recaptcha.js`.
1. Remplacez la valeur `siteKey` par la valeur de clé de site reCAPTCHA Google.

   ![Recaptcha s’applique à tous les formulaires](/help/forms/assets/recaptcha-apply-to-all-forms.png)

   >[!NOTE]
   >
   >  Vous pouvez récupérer les clés reCAPTCHA de l’ [Admin Console Google reCAPTCHA](https://www.google.com/recaptcha/admin).

1. Enregistrez le fichier `recaptcha.js`.

### Déployez le fichier et créez le projet.

Déployez le fichier `recaptcha.js` mis à jour dans votre projet GitHub et vérifiez la création.

### Aperçu du site à l’aide du sidekick AEM

Utilisez [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) pour prévisualiser et publier le site.

Le badge reCAPTCHA commence à apparaître pour tous les formulaires de votre site.

## Voir également

{{see-more-forms-eds}}

