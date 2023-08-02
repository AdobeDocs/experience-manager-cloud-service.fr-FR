---
title: Utilisation de Google reCAPTCHA dans un formulaire adaptatif basé sur les composants principaux
description: Améliorez la sécurité des formulaires avec le service Google reCAPTCHA sans effort. Guide pas à pas à l'intérieur !
topic-tags: Adaptive Forms, author
hide: true
hidefromtoc: true
Keywords: Google reCAPTCHA service, Adaptive Forms, CAPTCHA challenge, Bot prevention, Core Components, Form submission security, Form spam prevention
source-git-commit: 4f2a51502202fba3792cde370180d127f8e17418
workflow-type: tm+mt
source-wordcount: '868'
ht-degree: 7%

---

# Utiliser reCAPTCHA dans les Forms adaptatives en fonction des composants principaux {#using-reCAPTCHA-in-adaptive-forms}

CAPTCHA (Completely Automated Public Turing test to say Computers and Humans apart) est un programme couramment utilisé dans les transactions en ligne pour distinguer les humains des programmes ou robots automatisés. Il pose un problème et évalue la réponse de l’utilisateur pour déterminer s’il s’agit d’un humain ou d’un robot interagissant avec le site. Elle empêche l’utilisateur de procéder si le test échoue et permet de sécuriser les transactions en ligne en empêchant les robots de publier du spam ou des fins malveillantes.

[!DNL AEM Forms] as a [!DNL Cloud Service] prend en charge Google reCAPTCHA v2 dans Adaptive Forms. Vous pouvez l’utiliser pour présenter un défi CAPTCHA lors de l’envoi du formulaire. Pour utiliser reCAPTCHA dans un formulaire adaptatif :

1. [Connectez votre environnement AEM Forms avec le service reCAPTCHA de Google](#connect-your-forms-environment-with-recaptcha-service-by-google)
1. [Configurer votre formulaire adaptatif pour afficher le défi CAPTCHA lors de l’envoi du formulaire](#using-reCAPTCHA)

## Connectez votre environnement AEM Forms avec le service reCAPTCHA de Google {#connect-your-forms-environment-with-recaptcha-service-by-google}

Pour connecter votre environnement AEM Forms avec le service reCAPTCHA de Google

1. Obtenir [paire de clés de l’API reCAPTCHA](https://www.google.com/recaptcha/admin) de Google. Il comprend un **clé du site** et un **clé secrète**.

   ![Créer une configuration Google reCAPTCHA du site web Google pour obtenir les clés reCAPTCHA](/help/forms/assets/google-captcha.gif)
1. Créez un conteneur de configuration sur votre environnement as a Cloud Service AEM Forms. Un conteneur de configuration contient les configurations cloud utilisées pour se connecter AEM aux services externes. Pour créer et configurer un conteneur de configuration afin de connecter votre environnement AEM Forms au service reCAPTCHA par Google :
   1. Ouvrez votre instance AEM Forms as a Cloud Service.
   1. Accédez à **[!UICONTROL Outils > Général > Navigateur de configuration]**. Dans l’explorateur de configurations, vous pouvez :
   1. Sélectionnez un dossier existant ou créez-en un. Vous pouvez
      * Créez un dossier et activez l’option Configurations du cloud pour celui-ci :
         1. Dans le navigateur de configuration, cliquez sur **[!UICONTROL Créer]**.
         1. Dans la boîte de dialogue Créer une configuration, indiquez le nom et le titre, puis sélectionnez le **[!UICONTROL Configurations du cloud]** .
         1. Cliquez sur **[!UICONTROL Créer]**.
            ![Création d’une configuration cloud pour connecter votre environnement AEM Forms au service reCAPTCHA par Google](/help/forms/assets/create-configuration.png){width="50%"}
      * Activez l’option Configurations du cloud pour un dossier existant :
         1. Dans le navigateur de configuration, sélectionnez le dossier  et appuyez sur **[!UICONTROL Propriétés]**.
         1. Dans la boîte de dialogue Propriétés de configuration, activez **[!UICONTROL Configurations cloud]**.
         1. Appuyez sur **[!UICONTROL Enregistrer et fermer]** pour enregistrer la configuration et fermer la boîte de dialogue.

1. Configurer le service cloud:
   1. Sur votre instance d’auteur AEM, accédez à ![tools-1](assets/tools-1.png) > **[!UICONTROL Cloud Services]** et appuyez sur **[!UICONTROL reCAPTCHA]**.
   1. Sélectionnez un conteneur de configuration, créé ou mis à jour dans la section précédente. Appuyez sur **[!UICONTROL Créer]**.
   1. Spécifier **[!UICONTROL Titre]**, **[!UICONTROL Nom]**, **[!UICONTROL Clé du site]**, et **[!UICONTROL Clé secrète]** pour le service reCAPTCHA (obtenu à l’étape 1). Appuyez sur **[!UICONTROL Créer]**.
      ![Configurez le Cloud Service pour connecter votre environnement AEM Forms au service reCAPTCHA par Google.](/help/forms/assets/captcha-configuration.gif)

   Une fois le service reCAPTCHA configuré, il peut être utilisé dans un formulaire adaptatif. Pour plus d’informations, voir [utilisation de Google reCAPTCHA dans un formulaire adaptatif](#using-reCAPTCHA).


## Utilisation de Google reCAPTCHA dans un formulaire adaptatif {#using-reCAPTCHA}

Pour utiliser reCAPTCHA dans Adaptive Forms :

1. Ouvrez votre instance AEM Forms as a Cloud Service.
1. Accédez à **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents]**.
1. Sélectionnez un Forms adaptatif et appuyez sur **[!UICONTROL Propriétés]**. Pour le **[!UICONTROL Conteneur de configuration]** Sélectionnez l’option Conteneur de configuration qui contient la configuration cloud qui connecte AEM Forms au service reCAPTCHA par Google et appuyez sur . **[!UICONTROL Enregistrer et fermer]**.

   Si vous ne disposez pas d’un tel conteneur de configuration, reportez-vous à la section . [Connectez votre environnement AEM Forms avec le service reCAPTCHA de Google](#connect-your-forms-environment-with-recaptcha-service-by-google) pour savoir comment créer un tel conteneur de configuration.

   ![Sélectionner le conteneur de configuration](/help/forms/assets/captcha-properties.png)
1. Sélectionnez un Forms adaptatif et appuyez sur **[!UICONTROL Modifier]**. Le formulaire adaptatif s’ouvre dans l’éditeur de Forms adaptatif.
1. Dans l’explorateur de composants, faites glisser et déposez le composant **[!UICONTROL reCAPTCHA du formulaire adaptatif]** sur le formulaire adaptatif.

   La validation Google reCAPTCHA est sensible au temps et expire dans environ une minute. Par conséquent, Adobe recommande de placer la variable **[!UICONTROL reCAPTCHA du formulaire adaptatif]** juste avant le composant **[!UICONTROL Envoyer]** bouton .

1. Sélectionnez la variable **[!UICONTROL reCAPTCHA du formulaire adaptatif]** composant et appuyez sur les propriétés ![Icône Propriétés](assets/configure-icon.svg) Icône Elle ouvre la boîte de dialogue des propriétés. Spécifiez les propriétés obligatoires suivantes :
   * **[!UICONTROL Nom]:** Vous pouvez identifier facilement un composant de formulaire avec son nom unique dans le formulaire et dans l’éditeur de règles, mais le nom ne doit pas contenir d’espaces ni de caractères spéciaux.
   * **[!UICONTROL Configuration CAPTCHA]:** Sélectionnez une configuration de cloud configurée pour présenter la boîte de dialogue Google reCAPTCHA pour le formulaire. Vous pouvez avoir plusieurs configurations de cloud dans votre environnement à des fins similaires. Choisissez donc le service avec soin. Si aucun service n’est répertorié, voir [Connectez votre environnement AEM Forms avec le service reCAPTCHA de Google](#connect-your-forms-environment-with-recaptcha-service-by-google) pour savoir comment créer un Cloud Service qui connecte votre environnement AEM Forms au service reCAPTCHA de Google.
   * **Taille du captcha :** Vous pouvez sélectionner la taille d’affichage de la boîte de dialogue de défi Google reCAPTCHA. Utilisez la variable **[!UICONTROL Compact]** pour afficher une petite taille et la variable **[!UICONTROL Normal]** pour afficher une boîte de dialogue de défi Google reCAPTCHA de taille relativement importante.

1. Appuyez sur **[!UICONTROL Terminé]**.

   Maintenant, le **protégé par reCAPTCHA** s’affiche sur votre formulaire adaptatif. Il s’affiche sur toutes les Forms adaptatives configurées pour utiliser le service Google reCAPTCHA.

   Désormais, seuls les formulaires légitimes, dans lesquels l’utilisateur réussit à résoudre le problème posé par le service Google reCAPTCHA, peuvent être envoyés.
   ![Badge protégé par reCAPTCHA de Google](/help/forms/assets/google-recaptcha-v2.png)

<!--
### Show or hide CAPTCHA component based on rules {#show-hide-captcha}

You can select to show or hide the CAPTCHA component based on rules that you apply on a component in an Adaptive Form. Tap the component, select ![edit rules](assets/edit-rules-icon.svg), and tap **[!UICONTROL Create]** to create a rule. For more information on creating rules, see [Rule Editor](rule-editor.md).

For example, the CAPTCHA component must display in an Adaptive Form only if the Currency Value field in the form has a value of more than 25000.

Tap the **[!UICONTROL Currency Value]** field in the form and create the following rules:

![Show or hide rules](assets/rules-show-hide-captcha.png)

   >[!NOTE]
   >
   > When you select a reCAPTCHA v2 configuration and the size is set to [!UICONTROL Invisible], the show/hide option remains disabled.

   -->

## Foire aux questions

**Q : Puis-je utiliser plusieurs composants Captcha dans un formulaire adaptatif ?**
**Réponse :** L’utilisation de plusieurs composants Captcha dans un formulaire adaptatif n’est pas prise en charge. En outre, il n’est pas recommandé d’utiliser le composant Captcha dans un fragment ou un panneau marqué pour le chargement différé.

