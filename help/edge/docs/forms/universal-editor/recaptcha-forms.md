---
title: Utiliser reCAPTCHA avec Edge Delivery Services pour AEM Forms as a Cloud Service
description: Utiliser Google reCAPTCHA dans un formulaire pour Edge Delivery Services pour AEM Forms
feature: Edge Delivery Services
keywords: reCAPTCHA dans les formulaires, Utiliser reCAPTCHA dans l’éditeur universel, Ajouter reCAPTCHA dans les formulaires
role: Admin, Architect, Developer
exl-id: 1f28bd13-133f-487e-8b01-334be7c08a3f
source-git-commit: 0c6f024594e1b1fd98174914d2c0714dffecb241
workflow-type: tm+mt
source-wordcount: '1273'
ht-degree: 96%

---


# Utiliser reCAPTCHA dans la création WYSIWYG

<span class="preview"> Cette fonctionnalité est disponible via le programme d’accès anticipé. Pour demander l’accès, envoyez un e-mail à partir de votre adresse officielle à <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a> avec le nom de votre organisation GitHub et le nom du référentiel. Par exemple, si l’URL du référentiel est https://github.com/adobe/abc, le nom de l’organisation est adobe et le nom du référentiel est abc.</span>


La validation CAPTCHA (Completely Automated Public Turing test to tell Computers and Humans Apart) est un outil populaire utilisé pour protéger les sites web contre les activités frauduleuses, le spam et les abus.

Prenons l’exemple d’un formulaire qui calcule la taxe en fonction des déductions supplémentaires et du taux de taxation. Dans de tels cas, il existe un risque que des utilisateurs et des utilisatrices malveillants exploitent le formulaire pour envoyer des e-mails d’hameçonnage ou pour le saturer de contenu non pertinent ou nuisible en utilisant des robots de spam. L’intégration de CAPTCHA fournit une sécurité supplémentaire en vérifiant que les envois proviennent d’utilisateurs et d’utilisatrices authentiques, réduisant en pratique les entrées de spam.

![reCAPTCHA de Google](/help/edge/docs/forms/universal-editor/assets/google-recaptcha.png)

Dans Edge Delivery Services pour AEM Forms, le bloc de formulaire permet de [connecter Google reCAPTCHA aux formulaires](#connect-forms-with-recaptcha-service-by-google) à l’aide du composant **Captcha(Invisible)** pour faire la différence entre les humains et les robots. Cette fonctionnalité permet aux créateurs et aux créatrices de protéger leurs formulaires contre le spam et toute utilisation abusive.

## Connecter Forms au service reCAPTCHA de Google

Vous pouvez créer des Edge Delivery Services pour AEM Forms afin d’implémenter le service reCAPTCHA fourni par Google. Selon vos besoins, vous pouvez configurer l’un des services reCAPTCHA suivants pour Edge Delivery Services pour AEM Forms :

* [reCAPTCHA Enterprise](#configure-recaptcha-enterprise)
* [reCAPTCHA](#configure-recaptcha)

>[!NOTE]
>
> Pour plus d’informations sur le fonctionnement de reCAPTCHA, consultez [Google reCAPTCHA](https://developers.google.com/recaptcha?hl=fr).

### Configurer reCAPTCHA Enterprise

reCAPTCHA Enterprise est un service Premium de détection et de prévention des fraudes de niveau professionnel, proposé par Google. Il s’appuie sur les bases de reCAPTCHA (basé sur les scores) mais offre des fonctionnalités supplémentaires, une évolutivité et une personnalisation pour répondre aux besoins complexes des entreprises.

#### Avant de commencer

Avant de configurer Google reCAPTCHA Enterprise pour Edge Delivery Services pour AEM Forms, assurez-vous d’avoir effectué les étapes suivantes :

1. Créez ou sélectionnez un [projet Google Cloud](https://cloud.google.com/recaptcha/docs/prepare-environment?hl=fr#before-you-begin) et récupérez l’[ID du projet](https://support.google.com/googleapi/answer/7014113?hl=fr#:~:text=To%20locate%20your%20project%20ID,a%20member%20of%20are%20displayed).

1. [Activez l’API reCAPTCHA Enterprise](https://cloud.google.com/recaptcha/docs/prepare-environment?hl=fr#enable-api) pour votre projet Google Cloud et [créez une clé API](https://console.cloud.google.com/apis/credentials).

1. Créez une [clé de site pour votre projet Google Cloud](https://console.cloud.google.com/security/recaptcha), puis copiez-la.

Une fois que vous disposez de ces informations d’identification, vous pouvez poursuivre la configuration de reCAPTCHA Enterprise pour vos formulaires :

1. [Créer un conteneur de configurations cloud](#1-create-cloud-configuration-container)
1. [Créer la configuration du service cloud pour reCAPTCHA Enterprise](#2-create-the-cloud-service-configuration-for-recaptcha-enterprise)

#### 1. Créer un conteneur de configurations cloud

Pour créer le conteneur de configurations cloud , procédez comme suit :

1. Connectez-vous à votre instance de création.
1. Accédez à **[!UICONTROL Outils]** ![tools-1](/help/forms/assets/tools-1.png) > **[!UICONTROL Général]** > **[!UICONTROL Explorateur de configuration]**.

   ![Conteneur de configurations cloud](/help/edge/docs/forms/universal-editor/assets/recaptcha-general-configuration.png)

1. Dans l’**[!UICONTROL Explorateur de configuration]**, accédez à votre formulaire et sélectionnez **[!UICONTROL Propriétés]**.

   ![Propriétés de configuration cloud](/help/edge/docs/forms/universal-editor/assets/general-configuration-properties.png)

1. Dans la boîte de dialogue **[!UICONTROL Propriétés de configuration]**, activez **[!UICONTROL Configurations cloud]**.

1. Sélectionnez **[!UICONTROL Enregistrer et fermer]** pour enregistrer la configuration et fermer la boîte de dialogue.

   ![Activer les propriétés de configuration cloud](/help/edge/docs/forms/universal-editor/assets/enable-cloud-configurations.png)
`
Après avoir créé le conteneur de configurations cloud, publiez-le.

   ![Publier la configuration cloud](/help/edge/docs/forms/universal-editor/assets/publish-cloud-configuration.png)

#### 2. Créer la configuration du service cloud pour reCAPTCHA Enterprise

Pour créer la configuration du service cloud pour reCAPTCHA Enterprise, procédez comme suit :

1. Connectez-vous à votre instance de création.
1. Accédez à **[!UICONTROL Outils]** ![tools-1](/help/forms/assets/tools-1.png) > **[!UICONTROL Services cloud]** > **[!UICONTROL reCAPTCHA]**.

   ![Configuration du cloud Recaptcha](/help/edge/docs/forms/universal-editor/assets/recaptcha-cloud-configuration.png)

   La boîte de dialogue **Configurations** s’ouvre.

1. Accédez à votre formulaire et sélectionnez **[!UICONTROL Créer]**.

   ![Configuration Captcha](/help/edge/docs/forms/universal-editor/assets/create-captcha-confguration.png)

   La boîte de dialogue **[!UICONTROL Créer une configuration reCAPTCHA]** s’ouvre.

   ![reCaptcha Enterprise](/help/edge/docs/forms/universal-editor/assets/recaptcha-enterprise.png)

1. Sélectionnez [!DNL ReCAPTCHA Enterprise] pour la version et spécifiez le titre, le nom, l’ID du projet, la clé de site et la clé API.

   >[!NOTE]
   >
   > Dans reCAPTCHA Enterprise, vous pouvez obtenir l’ID du projet, la clé de site et la clé API à partir de la section [Avant de commencer](#before-you-start).

1. Sélectionnez **Clé de site basée sur les scores** pour le **[!UICONTROL Type de clé]**.
1. Spécifiez un [score seuil compris entre 0 et 1](https://cloud.google.com/recaptcha/docs/interpret-assessment-website?hl=fr#interpret_scores). Les scores supérieurs ou égaux aux scores seuils indiquent une interaction humaine, sinon il s’agit d’une interaction avec un robot.
1. Sélectionnez **[!UICONTROL Créer]** pour créer la configuration du service cloud.

   Une fois la configuration cloud reCAPTCHA créée, publiez-la.

   ![Publier la configuration Recaptcha](/help/edge/docs/forms/universal-editor/assets/publisg-recaptcha-configuration.png)

Vous pouvez maintenant créer ou modifier un formulaire et ajouter le composant reCAPTCHA à l’aide de la création basée sur WYSIWYG. Pour obtenir des instructions détaillées sur l’intégration de Google reCAPTCHA dans votre formulaire, reportez-vous à la section [Utiliser reCAPTCHA dans votre formulaire](#use-recaptcha-in-your-form).

## Configurer reCAPTCHA

reCAPTCHA est un service gratuit proposé par Google qui permet aux sites web de détecter et de prévenir le trafic abusif, notamment des robots et du spam. Il prend en charge une version basée sur les scores qui fonctionne en arrière-plan et attribue un score de risque (compris entre 0,0 et 1,0) à chaque interaction avec une personne. Les scores supérieurs ou égaux aux scores seuils indiquent une interaction humaine, sinon il s’agit d’une interaction avec un robot.

#### Avant de commencer

Avant de configurer Google reCAPTCHA pour Edge Delivery Services pour AEM Forms, récupérez la [paire de clés API reCAPTCHA dans la console Google](https://www.google.com/recaptcha/admin). Elle comprend une clé de site et une clé secrète.

>[!NOTE]
>
> * Edge Delivery Services pour AEM Forms ne prend en charge que la version **reCAPTCHA basée sur les scores**.

Lorsque vous disposez de la paire de clés API, vous pouvez procéder à la configuration de reCAPTCHA pour vos formulaires :

1. [Créer un conteneur de configurations cloud](#1-create-cloud-configuration-container-1)
1. [Créer la configuration du service cloud pour reCAPTCHA](#2-create-the-cloud-service-configuration-for-recaptcha)

#### 1. Créer un conteneur de configurations cloud

Pour créer le conteneur de configurations cloud , procédez comme suit :

1. Connectez-vous à votre instance de création.
1. Accédez à **[!UICONTROL Outils]** ![tools-1](/help/forms/assets/tools-1.png) > **[!UICONTROL Général]** > **[!UICONTROL Explorateur de configuration]**.

   ![Conteneur de configurations cloud](/help/edge/docs/forms/universal-editor/assets/recaptcha-general-configuration.png)

1. Dans l’**[!UICONTROL Explorateur de configuration]**, accédez à votre formulaire et sélectionnez **[!UICONTROL Propriétés]**.

   ![Propriétés de configuration cloud](/help/edge/docs/forms/universal-editor/assets/general-configuration-properties.png)

1. Dans la boîte de dialogue **[!UICONTROL Propriétés de configuration]**, activez **[!UICONTROL Configurations cloud]**.

1. Sélectionnez **[!UICONTROL Enregistrer et fermer]** pour enregistrer la configuration et fermer la boîte de dialogue.

   ![Activer les propriétés de la configuration cloud](/help/edge/docs/forms/universal-editor/assets/enable-cloud-configurations.png)

   Après avoir créé le conteneur de configurations cloud, publiez-le.

   ![Publier la configuration cloud](/help/edge/docs/forms/universal-editor/assets/publish-cloud-configuration.png)

#### 2. Créer la configuration du service cloud pour reCAPTCHA

Pour créer la configuration du service cloud pour reCAPTCHA, procédez comme suit :

1. Connectez-vous à votre instance de création.
1. Accédez à **[!UICONTROL Outils]** ![tools-1](/help/forms/assets/tools-1.png) > **[!UICONTROL Services cloud]** > **[!UICONTROL reCAPTCHA]**.

   ![Configuration du cloud Recaptcha](/help/edge/docs/forms/universal-editor/assets/recaptcha-cloud-configuration.png)

   La boîte de dialogue **Configurations** s’ouvre.

1. Accédez à votre formulaire et sélectionnez **[!UICONTROL Créer]**.

   ![Configuration Captcha](/help/edge/docs/forms/universal-editor/assets/create-captcha-confguration.png)

   La boîte de dialogue **[!UICONTROL Créer une configuration reCAPTCHA]** s’ouvre.

   ![reCaptcha Enterprise](/help/edge/docs/forms/universal-editor/assets/recaptcha.png)

1. Sélectionnez la version [!DNL ReCAPTCHA v2] et spécifiez le titre et le nom.
1. Entrez une clé de site et une clé secrète.

   >[!NOTE]
   >
   > Pour obtenir la clé de site et la clé secrète, reportez-vous à la section [Avant de commencer](#before-you-begin) de reCAPTCHA.

1. Sélectionnez **[!UICONTROL Créer]** pour créer la configuration du service cloud.

   Une fois la configuration cloud reCAPTCHA créée, publiez-la.

   ![Publier la configuration Recaptcha](/help/edge/docs/forms/universal-editor/assets/publisg-recaptcha-configuration.png)

Vous pouvez maintenant créer et modifier un formulaire et ajouter le composant reCAPTCHA à l’aide de la création basée sur WYSIWYG. Pour obtenir des instructions détaillées sur l’intégration de Google reCAPTCHA dans votre formulaire, reportez-vous à la section [Utiliser reCAPTCHA dans votre formulaire](#use-recaptcha-in-your-form).

### Utiliser reCAPTCHA dans votre formulaire

Pour créer un formulaire et ajouter le composant reCAPTCHA (invisible), procédez comme suit :

1. Ouvrez un formulaire dans l’éditeur universel pour le modifier.
1. Accédez à la section Formulaire adaptatif ajoutée dans l’arborescence de contenu.
1. Cliquez sur l’icône **[!UICONTROL Ajouter]** et ajoutez le composant **[!UICONTROL Captcha (Invisble)]** dans la liste **Composants de formulaire adaptatif**.

   ![Ajouter un composant reCaptcha](/help/edge/docs/forms/universal-editor/assets/add-recaptcha-component.png)

   Vous pouvez également faire glisser et déposer les composants de formulaire adaptatif requis, car l’éditeur universel offre une fonctionnalité intuitive de glisser-déposer.

1. Cliquez sur **Publier** pour republier le formulaire après l’ajout du composant **[!UICONTROL Captcha (invisible)]**.

   ![republier le formulaire](/help/edge/docs/forms/universal-editor/assets/publish-form.png)

Vous pouvez désormais afficher le formulaire avec le service reCAPTCHA à l’adresse URL suivante :
`https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form-name`.

![Formulaire avec reCAPTCHA](/help/edge/docs/forms/universal-editor/assets/form-with-recaptcha.png)

## Questions fréquentes

* **Que se passe-t-il si une personne ne crée pas de configuration cloud reCAPTCHA ?**

  **R** : si une personne ne crée pas de configuration cloud reCAPTCHA, le serveur AEM recherche la configuration cloud reCAPTCHA dans le conteneur de configurations globales. Si aucune configuration n’est présente dans le conteneur de configurations globales, le serveur AEM renvoie une erreur.

* **Que se passe-t-il si une personne crée plusieurs configurations cloud reCAPTCHA ?**
  **R** : si une personne crée plusieurs configurations cloud reCAPTCHA, le système sélectionne automatiquement la première configuration reCAPTCHA créée.

* **Pourquoi les modifications ou les changements ne sont-ils pas visibles dans l’URL publiée ?**
Si les modifications ou les changements ne sont pas visibles dans l’URL publiée, republiez le formulaire pour appliquer les mises à jour.

* **Quel service reCAPTCHA Edge Delivery Services pour AEM Forms prend-il en charge ?**
  **R** : Edge Delivery Services pour AEM Forms prend uniquement en charge le service reCAPTCHA basé sur les scores fourni par Google.


## Voir également

{{universal-editor-see-also}}

