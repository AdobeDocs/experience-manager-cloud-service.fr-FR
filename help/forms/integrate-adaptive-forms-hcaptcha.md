---
title: Comment utiliser hCaptcha&reg; dans un formulaire adaptatif AEM ?
description: Améliorez sans effort la sécurité des formulaires grâce au service hCaptcha®. Guide détaillé inclus.
topic-tags: Adaptive Forms, author
keywords: hCaptcha&reg; service, Forms adaptatif, défi CAPTCHA, prévention des robots, sécurité de l’envoi des formulaires, prévention des spams des formulaires
feature: Adaptive Forms, Foundation Components
role: User, Developer
exl-id: dc7ca723-1008-472a-b6eb-8e9ed6332a16
source-git-commit: 914139a6340f15ee77024793bf42fa30c913931e
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 23%

---

# Connecter votre environnement AEM Forms avec hCaptcha® {#connect-your-forms-environment-with-hcaptcha-service}

<span class="preview"> Cette fonctionnalité se trouve dans le programme des utilisateurs et utilisatrices précoces. Vous pouvez écrire à aem-forms-ea@adobe.com à partir de votre identifiant e-mail officiel pour rejoindre le programme d’adoption précoce et demander l’accès à la fonctionnalité. </span>

CAPTCHA (Completely Automated Public Turing test to tell Computers and Humans Apart, Test public de Turing complètement automatisé ayant pour but de différencier les personnes humaines des ordinateurs) est un programme couramment utilisé dans les transactions en ligne pour différencier les personnes humaines des programmes automatisés ou des robots. Il présente un test et évalue la réponse de l’utilisateur ou de l’utilisatrice pour déterminer s’il s’agit d’une personne humaine ou d’un robot qui interagit avec le site. Cela empêche l’utilisateur ou l’utilisatrice de continuer si le test échoue et permet de sécuriser les transactions en ligne en empêchant les robots d’envoyer du spam ou des éléments malveillants.

AEM Forms as a Cloud Service prend en charge les solutions CAPTCHA suivantes :

* [hCaptcha](#integrate-aem-forms-environment-with-hcaptcha-captcha)
* [Tourniquet Cloudflare](/help/forms/integrate-adaptive-forms-turnstile.md)
* [reCAPTCHA de Google](/help/forms/captcha-adaptive-forms.md)

## Intégration de l’environnement AEM Forms avec hCaptcha

Le service hCaptcha® protège vos formulaires des robots, spams et violations automatisées. Il propose un test sous forme de widget de case à cocher et évalue la réponse de l’utilisateur ou de l’utilisatrice pour déterminer s’il s’agit d’une personne humaine ou d’un robot qui interagit avec le formulaire. Cela empêche l’utilisateur ou l’utilisatrice de continuer si le test échoue et permet de sécuriser les transactions en ligne en empêchant les robots d’envoyer du spam ou des activités malveillantes.

AEM Forms as a Cloud Service prend en charge hCaptcha® dans Adaptive Forms. Vous pouvez l’utiliser pour présenter un défi de widget de case à cocher lors de l’envoi du formulaire.

<!-- ![hCaptcha&reg;](assets/hCaptcha&reg;-challenge.png)-->

## Conditions préalables à l’intégration de l’environnement AEM Forms à hCaptcha® {#prerequisite}

Pour configurer hCaptcha® avec AEM Forms, vous devez obtenir la [hCaptcha® sitekey et la clé secrète](https://docs.hcaptcha.com/switch/#get-your-hcaptcha-sitekey-and-secret-key) à partir du site web hCaptcha®.

## Étapes de configuration de hCaptcha® {#steps-to-configure-hcaptcha}

1. Créez un conteneur de configuration sur votre environnement AEM Forms as a Cloud Service. Un conteneur de configurations contient les configurations cloud utilisées pour connecter AEM à des services externes. Pour créer et configurer un conteneur de configuration afin de connecter votre environnement AEM Forms à hCaptcha ® :
   1. Ouvrez votre instance AEM Forms as a Cloud Service.
   1. Accédez à **[!UICONTROL Outils > Général > Navigateur de configuration]**.
   1. Dans l’explorateur de configurations, vous pouvez sélectionner un dossier existant ou en créer un. Vous pouvez créer un dossier et activer l’option Configurations cloud pour celui-ci ou activer l’option Configurations cloud pour un dossier existant :

      * **Pour créer un dossier et activer l’option Configurations cloud pour celui-ci** :
         1. Dans le navigateur de configuration, cliquez sur **[!UICONTROL Créer]**.
         1. Dans la boîte de dialogue Créer une configuration, spécifiez un nom et un titre, puis sélectionnez l’option **[!UICONTROL Configurations cloud]**.
         1. Cliquez sur **[!UICONTROL Créer]**.
      * Pour activer l’option Configurations cloud pour un dossier existant :
         1. Dans l’explorateur de configurations, sélectionnez le dossier, puis sélectionnez **[!UICONTROL Propriétés]**.
         1. Dans la boîte de dialogue Propriétés de configuration, activez **[!UICONTROL Configurations cloud]**.
         1. Sélectionnez **[!UICONTROL Enregistrer et fermer]** pour enregistrer la configuration et fermer la boîte de dialogue.

1. Configurez le Cloud Service :
   1. Sur votre instance d’auteur AEM, accédez à ![tools-1](assets/tools-1.png) > **[!UICONTROL Services cloud]** et sélectionnez **[!UICONTROL hCaptcha®]**.

      ![hCaptcha® dans l’interface utilisateur](assets/hcaptcha-in-ui.png)
   1. Sélectionnez un conteneur de configuration, créé ou mis à jour, comme décrit dans la section précédente. Sélectionnez **[!UICONTROL Créer]**.

      ![Configuration hCaptcha®](assets/config-hcaptcha.png)
   1. Spécifiez **[!UICONTROL Titre]**, **[!UICONTROL Nom]**, **[!UICONTROL Clé du site]** et **[!UICONTROL Clé secrète]** pour le service hCaptcha® [obtenu dans les conditions préalables](#prerequisite). Sélectionnez **[!UICONTROL Créer]**.

      ![Configuration de Cloud Service pour connecter votre environnement AEM Forms à hCaptcha®](assets/create-hcaptcha-config.png)

>[!NOTE]
> Les utilisateurs n’ont pas besoin de modifier les [URL de validation JavaScript côté client](https://docs.hcaptcha.com/#add-the-hcaptcha-widget-to-your-webpage) et [URL de validation côté serveur](https://docs.hcaptcha.com/#verify-the-user-response-server-side), car elles sont déjà préremplies pour la validation hCaptcha®. Pour certains pays, les points d’entrée peuvent être différents, consultez [FAQ sur hCaptcha®](https://docs.hcaptcha.com/faq#does-hcaptcha-support-access-by-users-in-china) pour plus d’informations.

Une fois le service hCAPTCHA configuré, il peut être utilisé dans un formulaire adaptatif.

## Utilisation de hCaptcha® dans un formulaire adaptatif{#using-hCaptcha®-foundation-components}

1. Ouvrez votre instance AEM Forms as a Cloud Service.
1. Accédez à **[!UICONTROL Forms]** > **[!UICONTROL Forms et documents]**.
1. Sélectionnez un formulaire adaptatif et sélectionnez **[!UICONTROL Propriétés]**. Pour l’option **[!UICONTROL Conteneur de configurations]**, sélectionnez le Conteneur de configurations contenant la configuration cloud qui connecte AEM Forms à hCaptcha®, puis sélectionnez **[!UICONTROL Enregistrer et fermer]**.

   Si vous ne disposez pas d’un tel conteneur de configuration, consultez la section [Connecter votre environnement AEM Forms à hCaptcha®](#connect-your-forms-environment-with-hcaptcha-service) pour savoir comment créer un conteneur de configuration.

   ![Sélectionner le conteneur de configuration](/help/forms/assets/captcha-properties.png)

1. Sélectionnez un formulaire adaptatif, puis sélectionnez **[!UICONTROL Modifier]**. Le formulaire adaptatif s’ouvre dans l’éditeur de Forms adaptatif.
1. À partir du navigateur de composant, faites glisser et déposez le composant **[!UICONTROL Captcha]** sur le formulaire adaptatif.
1. Sélectionnez le composant **[!UICONTROL Captcha]** et cliquez sur l’icône Propriétés ![Icône Propriétés](assets/configure-icon.svg). Cela ouvre la boîte de dialogue des propriétés.

   ![Texte de remplacement](assets/hcaptcha-properties.png)

   Spécifiez les propriétés suivantes :

   * **[!UICONTROL Titre] :** indiquez le titre de votre composant Captcha ; vous pouvez identifier facilement un composant de formulaire en lui attribuant un nom unique dans le formulaire et dans l’éditeur de règles.
   * **[!UICONTROL Message de validation] :** envoyez un message de validation pour la validation Captcha lors de l’envoi du formulaire.
   * **[!UICONTROL Valider le captcha] :** vous pouvez sélectionner l’une des options de validation du captcha :
      * Lors de l’envoi du formulaire
      * Sur une action utilisateur.
   * **[!UICONTROL Service Captcha] :** sélectionnez votre service Captcha, puis sélectionnez le service hCaptcha®.
   * **[!UICONTROL Configuration Captcha] :** sélectionnez une configuration cloud configurée pour hCaptcha®.

     >[!NOTE]
     >
     > Plusieurs configurations cloud peuvent être définies dans votre environnement dans un but similaire. Donc, choisissez le service avec soin. Si aucun service n’est répertorié, consultez [Connexion de votre environnement AEM Forms à hCaptcha®](#connect-your-forms-environment-with-hcaptcha-service) pour savoir comment créer un Cloud Service qui connecte votre environnement AEM Forms au service hCaptcha®.

   * **Message d’erreur :** le message d’erreur à afficher à l’utilisateur ou à l’utilisatrice en cas d’échec de l’envoi du Captcha.
   * **Taille de Captcha :** sélectionnez la taille d’affichage de la boîte de dialogue de vérification préliminaire hCaptcha®. Utilisez l’option **[!UICONTROL Compact]** pour afficher un objet de petite taille, et l’option **[!UICONTROL Normal]** pour afficher une boîte de dialogue de défi hCaptcha® de taille relativement importante, ou **[!UICONTROL Invisible]** pour valider le hCaptcha® sans rendre explicitement le widget de case à cocher dans l’interface utilisateur.

1. Sélectionnez **[!UICONTROL Terminé]**.

Désormais, seuls les formulaires légitimes, dans lesquels le remplisseur de formulaire résout avec succès le problème posé par le service hCaptcha®, sont autorisés pour l’envoi du formulaire.

**hCaptcha® est une marque déposée d’Intuition Machines, Inc.**

## Questions fréquentes

* **Q : Puis-je utiliser plusieurs composants Captcha dans un formulaire adaptatif ?**
* **Réponse :** l’utilisation de plusieurs composants Captcha dans un formulaire adaptatif n’est pas prise en charge. En outre, il n’est pas recommandé d’utiliser un composant Captcha dans un fragment ou un panneau marqué pour le chargement différé.

## Voir également {#see-also}

{{see-also}}
