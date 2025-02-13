---
title: Utiliser reCAPTCHA avec Edge Delivery Services pour AEM Forms as a Cloud Service
description: Utiliser Google reCAPTCHA dans un formulaire pour Edge Delivery Services pour AEM Forms
feature: Edge Delivery Services
keywords: reCAPTCHA dans les formulaires, en utilisant reCAPTCHA dans l’éditeur universel, ajouter reCAPTCHA dans les formulaires
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
exl-id: 1f28bd13-133f-487e-8b01-334be7c08a3f
source-git-commit: 320ab86bc73e874705d985b927e90eec3cad1cf9
workflow-type: tm+mt
source-wordcount: '1225'
ht-degree: 12%

---


# Utilisation de reCAPTCHA dans la création WYSIWYG

Le CAPTCHA (Completely Automated Public Turing test to tell Computers and Humans Apart) est un outil populaire utilisé pour protéger les sites web contre les activités frauduleuses, le spam et les abus.

Prenons l’exemple d’un formulaire qui calcule la taxe en fonction des déductions supplémentaires et du taux de taxe. Dans de tels cas, il existe un risque que des utilisateurs et des utilisatrices malveillants exploitent le formulaire pour envoyer des e-mails de phishing ou pour le saturer de contenu non pertinent ou nuisible en utilisant des robots de spam. L’intégration de CAPTCHA offre une sécurité accrue en vérifiant que les envois proviennent d’utilisateurs authentiques, ce qui réduit efficacement les entrées de spam.

![Google recaptcha](/help/edge/docs/forms/universal-editor/assets/google-recaptcha.png)

Dans Edge Delivery Services Forms, le bloc de formulaire vous permet de [connecter Google reCAPTCHA aux formulaires](#connect-forms-with-recaptcha-service-by-google) à l’aide du composant **Captcha(Invisible)** pour faire la distinction entre les humains et les robots. Cette fonctionnalité permet aux créateurs et aux créatrices de protéger leurs formulaires contre le spam et toute utilisation abusive.

## Connexion de Forms au service reCAPTCHA de Google

Vous pouvez créer Edge Delivery Services Forms pour implémenter le service reCAPTCHA fourni par Google. Selon vos besoins, vous pouvez configurer l’un des services reCAPTCHA suivants pour votre Forms Edge Delivery Services :

* [reCAPTCHA Enterprise](#configure-recaptcha-enterprise)
* [reCAPTCHA](#configure-recaptcha)

>[!NOTE]
>
> Pour plus d’informations sur le fonctionnement de reCAPTCHA, consultez [Google reCAPTCHA](https://developers.google.com/recaptcha/).

### Configuration de reCAPTCHA Enterprise

reCAPTCHA Enterprise est un service haut de gamme de détection et de prévention des fraudes de niveau professionnel, proposé par Google. Il s’appuie sur la base de reCAPTCHA (basé sur les scores) mais fournit des fonctionnalités supplémentaires, l’évolutivité et la personnalisation pour répondre aux besoins complexes des entreprises.

#### Avant de commencer

Avant de configurer Google reCAPTCHA Enterprise pour Edge Delivery Services Forms, assurez-vous d’avoir effectué les étapes suivantes :

1. Créez ou sélectionnez un [projet Google Cloud](https://cloud.google.com/recaptcha/docs/prepare-environment#before-you-begin) et récupérez l’[ID de projet](https://support.google.com/googleapi/answer/7014113?hl=en#:~:text=To%20locate%20your%20project%20ID,a%20member%20of%20are%20displayed).

1. [Activez l’API reCAPTCHA Enterprise](https://cloud.google.com/recaptcha/docs/prepare-environment#enable-api) pour votre projet Google Cloud et [créez une clé API](https://console.cloud.google.com/apis/credentials).

1. Créez une [clé de site pour votre projet Google Cloud](https://console.cloud.google.com/security/recaptcha) puis copiez la clé de site.

Une fois que vous disposez de ces informations d’identification, vous pouvez poursuivre la configuration de reCAPTCHA Enterprise pour vos formulaires :

1. [Créer un conteneur de configuration cloud](#1-create-cloud-configuration-container)
1. [Créer la configuration de service cloud pour reCAPTCHA Enterprise](#2-create-the-cloud-service-configuration-for-recaptcha-enterprise)

#### 1. Créer Un Conteneur De Configurations Cloud

Pour créer le conteneur de configurations cloud , procédez comme suit :

1. Connectez-vous à votre instance de création.
1. Accédez à **[!UICONTROL Outils]** ![outils-1](/help/forms/assets/tools-1.png) > **[!UICONTROL Général]** > **[!UICONTROL Explorateur de configuration]**.

   ![ Conteneur de configurations cloud ](/help/edge/docs/forms/universal-editor/assets/recaptcha-general-configuration.png)

1. Dans le **[!UICONTROL navigateur de configuration]**, accédez à votre formulaire et sélectionnez **[!UICONTROL Propriétés]**.

   ![Propriétés de configuration du cloud](/help/edge/docs/forms/universal-editor/assets/general-configuration-properties.png)

1. Dans la boîte de dialogue **[!UICONTROL Propriétés de configuration]**, activez **[!UICONTROL Configurations cloud]**.

1. Sélectionnez **[!UICONTROL Enregistrer et fermer]** pour enregistrer la configuration et fermer la boîte de dialogue.

   ![Activation des propriétés de configuration du cloud](/help/edge/docs/forms/universal-editor/assets/enable-cloud-configurations.png)
`
Après avoir créé le conteneur de configuration cloud, publiez-le.

   ![Publication de la configuration cloud](/help/edge/docs/forms/universal-editor/assets/publish-cloud-configuration.png)

#### 2. Créez la configuration de service cloud pour reCAPTCHA Enterprise

Pour créer la configuration de service cloud pour reCAPTCHA Enterprise, procédez comme suit :

1. Connectez-vous à votre instance de création.
1. Accédez à **[!UICONTROL Outils]** ![outils-1](/help/forms/assets/tools-1.png) > **[!UICONTROL Services cloud]** > **[!UICONTROL reCAPTCHA]**.

   ![Configuration cloud Recaptcha](/help/edge/docs/forms/universal-editor/assets/recaptcha-cloud-configuration.png)

   La boîte de dialogue **Configurations** s’ouvre.

1. Accédez à votre formulaire et sélectionnez **[!UICONTROL Créer]**.

   ![Configuration Captcha](/help/edge/docs/forms/universal-editor/assets/create-captcha-confguration.png)

   La boîte de dialogue **[!UICONTROL Créer une configuration reCAPTCHA]** s’ouvre.

   ![reCaptcha Enterprise](/help/edge/docs/forms/universal-editor/assets/recaptcha-enterprise.png)

1. Sélectionnez la version comme [!DNL ReCAPTCHA Enterprise] et spécifiez le titre, le nom, l’ID de projet, la clé de site et la clé API.

   >[!NOTE]
   >
   > Vous pouvez obtenir l’ID de projet, la clé de site et la clé API à partir de la section [Avant de commencer](#before-you-start) pour reCAPTCHA Enterprise.

1. Sélectionnez **[!UICONTROL Type de clé]** comme **Clé de site basée sur les scores**.
1. Spécifiez un score [seuil compris entre 0 et 1](https://cloud.google.com/recaptcha/docs/interpret-assessment-website#interpret_scores). Des scores supérieurs ou égaux aux scores seuils identifient l’interaction humaine, considérée par ailleurs comme une interaction entre robots.
1. Sélectionnez **[!UICONTROL Créer]** pour créer la configuration du service cloud.

   Après avoir créé la configuration cloud reCAPTCHA, publiez-la.

   ![Publier la configuration Recaptcha](/help/edge/docs/forms/universal-editor/assets/publisg-recaptcha-configuration.png)

Vous pouvez maintenant créer ou modifier un formulaire et ajouter le composant reCAPTCHA à l’aide de la création basée sur WYSIWYG. Pour obtenir des instructions détaillées sur l’intégration de Google reCAPTCHA dans votre formulaire, reportez-vous à la section [Utilisation de reCAPTCHA dans votre formulaire](#use-recaptcha-in-your-form).

## Configuration de reCAPTCHA

reCAPTCHA est un service gratuit proposé par Google qui aide les sites web à détecter et à prévenir le trafic abusif, y compris les robots et les spams. Il prend en charge une version basée sur les scores qui fonctionne en arrière-plan et attribue un score de risque (compris entre 0,0 et 1,0) à chaque interaction utilisateur. Des scores supérieurs ou égaux aux scores seuils identifient l’interaction humaine, considérée par ailleurs comme une interaction entre robots.

#### Avant De Commencer

Avant de configurer Google reCAPTCHA pour Edge Delivery Services Forms, récupérez la paire de clés d’API [reCAPTCHA dans la console Google](https://www.google.com/recaptcha/admin). La paire comprend une clé de site et une clé secrète.

>[!NOTE]
>
> * Edge Delivery Services Forms ne prend en charge que la version **basée sur le score reCAPTCHA**.

Une fois que vous disposez de la paire de clés API, vous pouvez procéder à la configuration de reCAPTCHA pour vos formulaires :

1. [Créer un conteneur de configuration cloud](#1-create-cloud-configuration-container-1)
1. [Créer la configuration de service cloud pour reCAPTCHA](#2-create-the-cloud-service-configuration-for-recaptcha)

#### 1. Créer Un Conteneur De Configurations Cloud

Pour créer le conteneur de configurations cloud , procédez comme suit :

1. Connectez-vous à votre instance de création.
1. Accédez à **[!UICONTROL Outils]** ![outils-1](/help/forms/assets/tools-1.png) > **[!UICONTROL Général]** > **[!UICONTROL Explorateur de configuration]**.

   ![ Conteneur de configurations cloud ](/help/edge/docs/forms/universal-editor/assets/recaptcha-general-configuration.png)

1. Dans le **[!UICONTROL navigateur de configuration]**, accédez à votre formulaire et sélectionnez **[!UICONTROL Propriétés]**.

   ![Propriétés de configuration du cloud](/help/edge/docs/forms/universal-editor/assets/general-configuration-properties.png)

1. Dans la boîte de dialogue **[!UICONTROL Propriétés de configuration]**, activez **[!UICONTROL Configurations cloud]**.

1. Sélectionnez **[!UICONTROL Enregistrer et fermer]** pour enregistrer la configuration et fermer la boîte de dialogue.

   ![Activation des propriétés de configuration du cloud](/help/edge/docs/forms/universal-editor/assets/enable-cloud-configurations.png)

   Après avoir créé le conteneur de configuration cloud, publiez-le.

   ![Publication de la configuration cloud](/help/edge/docs/forms/universal-editor/assets/publish-cloud-configuration.png)

#### 2. Créez la configuration de service cloud pour reCAPTCHA

Pour créer la configuration de service cloud pour reCAPTCHA, procédez comme suit :

1. Connectez-vous à votre instance de création.
1. Accédez à **[!UICONTROL Outils]** ![outils-1](/help/forms/assets/tools-1.png) > **[!UICONTROL Services cloud]** > **[!UICONTROL reCAPTCHA]**.

   ![Configuration cloud Recaptcha](/help/edge/docs/forms/universal-editor/assets/recaptcha-cloud-configuration.png)

   La boîte de dialogue **Configurations** s’ouvre.

1. Accédez à votre formulaire et sélectionnez **[!UICONTROL Créer]**.

   ![Configuration Captcha](/help/edge/docs/forms/universal-editor/assets/create-captcha-confguration.png)

   La boîte de dialogue **[!UICONTROL Créer une configuration reCAPTCHA]** s’ouvre.

   ![reCaptcha Enterprise](/help/edge/docs/forms/universal-editor/assets/recaptcha.png)

1. Sélectionnez la version comme [!DNL ReCAPTCHA v2] et spécifiez le titre et le nom.
1. Spécifiez la clé de site et la clé secrète .

   >[!NOTE]
   >
   > Vous pouvez obtenir la clé de site et la clé secrète à partir de la section [Avant de commencer](#before-you-begin) pour reCAPTCHA.

1. Sélectionnez **[!UICONTROL Créer]** pour créer la configuration du service cloud.

   Après avoir créé la configuration cloud reCAPTCHA, publiez-la.

   ![Publier la configuration Recaptcha](/help/edge/docs/forms/universal-editor/assets/publisg-recaptcha-configuration.png)

Vous pouvez maintenant créer et modifier un formulaire et ajouter le composant reCAPTCHA à l’aide de la création basée sur WYSIWYG. Pour obtenir des instructions détaillées sur l’intégration de Google reCAPTCHA dans votre formulaire, reportez-vous à la section [Utilisation de reCAPTCHA dans votre formulaire](#use-recaptcha-in-your-form).

### Utilisation de reCAPTCHA dans votre formulaire

Pour créer un formulaire et ajouter le composant reCAPTCHA (invisible) , procédez comme suit :

1. Ouvrez un formulaire dans l’éditeur universel pour le modifier.
1. Accédez à la section Formulaire adaptatif ajoutée dans l’arborescence de contenu.
1. Cliquez sur l’icône **[!UICONTROL Ajouter]** et ajoutez le composant **[!UICONTROL Captcha (invisible)]** dans la liste **Composants de formulaire adaptatif**.

   ![Ajouter un composant reCaptcha](/help/edge/docs/forms/universal-editor/assets/add-recaptcha-component.png)

   Vous pouvez également effectuer un glisser-déposer du composant Forms adaptatif requis, car l’éditeur universel offre une fonctionnalité intuitive de glisser-déposer.

1. Cliquez sur **Publier** pour republier le formulaire après l’ajout du composant **[!UICONTROL Captcha (invisible)]**.

   ![republier le formulaire](/help/edge/docs/forms/universal-editor/assets/publish-form.png)

Vous pouvez désormais afficher le formulaire avec le service reCAPTCHA à l’adresse URL suivante :
`https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form-name`.

![ Formulaire avec reCAPTCHA ](/help/edge/docs/forms/universal-editor/assets/form-with-recaptcha.png)

## Questions fréquentes

* **Que se passe-t-il si un utilisateur ne crée pas de configuration cloud reCAPTCHA ?**

  **A** : si un utilisateur ne crée pas de configuration cloud reCAPTCHA, le serveur AEM recherche la configuration cloud reCAPTCHA dans le conteneur de configuration globale. S’il n’existe aucune configuration dans le conteneur de configuration globale, le serveur AEM renvoie une erreur.

* **Que se passe-t-il si un utilisateur crée plusieurs configurations cloud reCAPTCHA ?**
  **A** : si un utilisateur crée plusieurs configurations cloud reCAPTCHA, le système sélectionne automatiquement la première configuration reCAPTCHA créée.

* **Pourquoi les modifications ou les changements ne sont-ils pas visibles à l’URL publiée ?**
Si les modifications ou les changements ne sont pas visibles à l’URL publiée, assurez-vous que le formulaire est republié pour appliquer les mises à jour.

* **Quel service reCAPTCHA Edge Delivery Services Forms prend-il en charge ?**
  **A** : Edge Delivery Services Forms prend uniquement en charge le service reCAPTCHA basé sur les scores fourni par Google.


## Voir également

{{see-more-forms-eds}}
