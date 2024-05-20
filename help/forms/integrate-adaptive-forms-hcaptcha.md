---
title: Comment utiliser le captcha® dans un formulaire adaptatif AEM ?
description: Améliorez la sécurité des formulaires grâce au service Captcha® sans effort. Guide pas à pas à l'intérieur !
topic-tags: Adaptive Forms, author
keywords: Service Captcha®, Forms adaptatif, défi CAPTCHA, prévention des robots, sécurité d’envoi de formulaire, prévention des spams de formulaire
feature: Adaptive Forms, Foundation Components
hide: true
hidefromtoc: true
source-git-commit: a8a31bae0f937aa8941d258af648d6be030a9fac
workflow-type: tm+mt
source-wordcount: '883'
ht-degree: 5%

---


# Connexion de votre environnement AEM Forms avec Captcha® {#connect-your-forms-environment-with-hcaptcha-service}

<span class="preview"> Cette fonctionnalité est inscrite dans le Programme des Adopteurs Anticipés. Vous pouvez écrire à aem-forms-ea@adobe.com à partir de votre ID de courrier électronique officiel pour rejoindre le programme des premiers adopteurs et demander l’accès à la fonctionnalité. </span>

Le service Captcha® protège vos formulaires contre les robots, les spams et les abus automatisés. Il pose un problème de widget de case à cocher et évalue la réponse de l’utilisateur pour déterminer s’il s’agit d’un humain ou d’un robot interagissant avec le formulaire. Elle empêche l’utilisateur de procéder si le test échoue et permet de sécuriser les transactions en ligne en empêchant les robots de publier du spam ou des activités malveillantes.

<!-- ![hCaptcha®](assets/hCaptcha®-challenge.png)-->

AEM Forms as a Cloud Service prend en charge Captcha® dans Adaptive Forms. Vous pouvez l’utiliser pour présenter à l’utilisateur un défi de widget de case à cocher lors de l’envoi du formulaire.

## Conditions préalables pour intégrer l’environnement AEM Forms avec Captcha® {#prerequisite}

Pour configurer Captcha® avec AEM Forms, vous devez obtenir la variable [Clé de site et clé secrète Captcha®](https://docs.hcaptcha.com/switch/#get-your-hcaptcha-sitekey-and-secret-key) du site web de Captcha®.

## Etapes de configuration du captcha® {#steps-to-configure-hcaptcha}

1. Créez un conteneur de configuration sur votre environnement as a Cloud Service AEM Forms. Un conteneur de configuration contient les configurations cloud utilisées pour se connecter AEM aux services externes. Pour créer et configurer un conteneur de configuration afin de connecter votre environnement AEM Forms à avec Captcha® :
   1. Ouvrez votre instance AEM Forms as a Cloud Service.
   1. Accédez à **[!UICONTROL Outils > Général > Navigateur de configuration]**.
   1. Dans l’explorateur de configurations, vous pouvez sélectionner un dossier existant ou créer un dossier. Vous pouvez créer un dossier et activer l’option Configurations du cloud pour celui-ci ou activer l’option Configurations du cloud pour un dossier existant :

      * **Pour créer un dossier et activer l’option Configurations du cloud**:
         1. Dans le navigateur de configuration, cliquez sur **[!UICONTROL Créer]**.
         1. Dans la boîte de dialogue Créer une configuration, indiquez un nom et un titre, puis sélectionnez le paramètre **[!UICONTROL Configurations du cloud]** .
         1. Cliquez sur **[!UICONTROL Créer]**.
      * Pour activer l’option Configurations du cloud pour un dossier existant :
         1. Dans l’explorateur de configurations, sélectionnez le dossier, puis sélectionnez **[!UICONTROL Propriétés]**.
         1. Dans la boîte de dialogue Propriétés de configuration, activez **[!UICONTROL Configurations cloud]**.
         1. Sélectionnez **[!UICONTROL Enregistrer et fermer]** pour enregistrer la configuration et fermer la boîte de dialogue.

1. Configurez le Cloud Service :
   1. Sur votre instance d’auteur AEM, accédez à ![tools-1](assets/tools-1.png) > **[!UICONTROL Cloud Service]** et sélectionnez **[!UICONTROL Captcha®]**.
      ![Captcha® dans l’interface utilisateur](assets/hcaptcha-in-ui.png)
   1. Sélectionnez un conteneur de configuration, créé ou mis à jour, comme décrit dans la section précédente. Sélectionnez **[!UICONTROL Créer]**.
      ![Captcha de configuration®](assets/config-hcaptcha.png)
   1. Spécifier **[!UICONTROL Titre]**, **[!UICONTROL Nom]**, **[!UICONTROL Clé du site]**, et **[!UICONTROL Clé secrète]** pour le service Captcha® [obtenu dans la condition préalable](#prerequisite). Sélectionnez **[!UICONTROL Créer]**.

      ![Configurez le Cloud Service pour connecter votre environnement AEM Forms à Captcha®](assets/create-hcaptcha-config.png)

>[!NOTE]
> Les utilisateurs ne doivent pas modifier [URL de validation JavaScript côté client](https://docs.hcaptcha.com/#add-the-hcaptcha-widget-to-your-webpage) et [URL de validation côté serveur](https://docs.hcaptcha.com/#verify-the-user-response-server-side) car ils sont déjà préremplis pour la validation du Captcha®. Pour certains pays, les points de terminaison peuvent différer, visite [FAQ sur Captcha®](https://docs.hcaptcha.com/faq#does-hcaptcha-support-access-by-users-in-china) pour plus d’informations.

Une fois le service hCAPTCHA configuré, il peut être utilisé dans un formulaire adaptatif.

## Utilisation de Captcha® dans un formulaire adaptatif{#using-hCaptcha®-foundation-components}

1. Ouvrez votre instance AEM Forms as a Cloud Service.
1. Accédez à **[!UICONTROL Forms]** > **[!UICONTROL Forms et documents]**.
1. Sélectionnez un formulaire adaptatif et choisissez **[!UICONTROL Propriétés]**. Pour le **[!UICONTROL Conteneur de configuration]** sélectionnez l’option Conteneur de configuration contenant la configuration du cloud qui connecte AEM Forms à avec Captcha®, puis sélectionnez **[!UICONTROL Enregistrer et fermer]**.

   Si vous ne disposez pas d’un tel conteneur de configuration, reportez-vous à la section . [Connexion de votre environnement AEM Forms avec Captcha®](#connect-your-forms-environment-with-hcaptcha-service) pour savoir comment créer un conteneur de configuration.

   ![Sélectionner le conteneur de configuration](/help/forms/assets/captcha-properties.png)

1. Sélectionnez un formulaire adaptatif et choisissez **[!UICONTROL Modifier]**. Le formulaire adaptatif s’ouvre dans l’éditeur de Forms adaptatif.
1. À partir du navigateur de composant, faites glisser et déposez le composant **[!UICONTROL Captcha]** sur le formulaire adaptatif.
1. Sélectionnez la variable **[!UICONTROL Captcha]** composant et cliquez sur propriétés ![Icône Propriétés](assets/configure-icon.svg) Icône Elle ouvre la boîte de dialogue des propriétés.

   ![texte alternatif](assets/hcaptcha-properties.png)

   Spécifiez les propriétés suivantes :

   * **[!UICONTROL Titre]:** Indiquez le titre de votre composant Captcha. Vous pouvez identifier facilement un composant de formulaire avec son nom unique dans le formulaire et dans l’éditeur de règles.
   * **[!UICONTROL Message de validation]:** Fournissez un message de validation pour votre validation Captcha lors de l’envoi du formulaire.
   * **[!UICONTROL Validation de Captcha]:** Vous pouvez sélectionner l&#39;une des options pour valider Captcha :
      * Lors de l’envoi du formulaire
      * Sur une action utilisateur.
   * **[!UICONTROL Service Captcha]:** Sélectionnez votre service Captcha, ici vous sélectionnez le service Captcha®.
   * **[!UICONTROL Configuration du captcha]:** Sélectionnez une configuration de cloud configurée pour Captcha®.
     >[!NOTE]
     >Vous pouvez avoir plusieurs configurations de cloud dans votre environnement à des fins similaires. Choisissez donc le service avec soin. Si aucun service n’est répertorié, voir [Connexion de votre environnement AEM Forms avec Captcha®](#connect-your-forms-environment-with-hcaptcha-service) pour savoir comment créer un Cloud Service qui connecte votre environnement AEM Forms au service Captcha®.

   * **Message d’erreur :** Fournissez le message d’erreur à afficher à l’utilisateur en cas d’échec de l’envoi du Captcha.
   * **Taille du captcha :** Vous sélectionnez la taille d&#39;affichage de la boîte de dialogue de défi Captcha®. Utilisez la variable **[!UICONTROL Compact]** pour afficher une petite taille et la variable **[!UICONTROL Normal]** pour afficher une boîte de dialogue de défi Captcha® de taille relativement grande ou **[!UICONTROL Invisible]** pour valider Captcha® sans générer explicitement le widget de case à cocher dans l’interface utilisateur.

1. Sélectionnez **[!UICONTROL Terminé]**.

Désormais, seuls les formulaires légitimes dans lesquels l’utilisateur réussit à résoudre le problème posé par le service Captcha® sont autorisés pour l’envoi du formulaire.

**Captcha® est une marque déposée de Intuition Machines, Inc.**

## Questions fréquentes

* **Q : Puis-je utiliser plusieurs composants Captcha dans un formulaire adaptatif ?**
* **Réponse :** L’utilisation de plusieurs composants Captcha dans un formulaire adaptatif n’est pas prise en charge. En outre, il n’est pas recommandé d’utiliser un composant Captcha dans un fragment ou un panneau marqué pour le chargement différé.

## Voir également {#see-also}

{{see-also}}
