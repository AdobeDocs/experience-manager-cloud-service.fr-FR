---
title: Comment utiliser Google reCAPTCHA dans un formulaire adaptatif AEM ?
description: Améliorez la sécurité des formulaires avec le service Google reCAPTCHA sans effort. Guide détaillé inclus.
topic-tags: Adaptive Forms, author
keywords: Service Google reCAPTCHA, Forms adaptatif, défi CAPTCHA, prévention des robots, composants principaux, sécurité d’envoi de formulaire, prévention des messages indésirables de formulaire
feature: Adaptive Forms, Core Components
exl-id: d116f979-efb6-4fac-8202-89afd1037b2c
role: User, Developer
source-git-commit: bba5e5d283da616baa57b788181af73d59d86ee3
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 17%

---

# Utilisation de Google reCAPTCHA dans un formulaire adaptatif AEM basé sur les composants principaux {#using-reCAPTCHA-in-adaptive-forms}

| Application | Lien de l’article |
| -------- | ---------------------------- |
| Formulaire adaptatif basé sur les composants principaux | Cet article |
| Formulaire adaptatif basé sur des composants de base | [Cliquez ici](/help/forms/captcha-adaptive-forms.md) |

CAPTCHA (Completely Automated Public Turing test to tell Computers and Humans Apart, Test public de Turing complètement automatisé ayant pour but de différencier les personnes humaines des ordinateurs) est un programme couramment utilisé dans les transactions en ligne pour différencier les personnes humaines des programmes automatisés ou des robots. Il présente un test et évalue la réponse de l’utilisateur ou de l’utilisatrice pour déterminer s’il s’agit d’une personne humaine ou d’un robot qui interagit avec le site. Cela empêche l’utilisateur ou l’utilisatrice de continuer si le test échoue et permet de sécuriser les transactions en ligne en empêchant les robots d’envoyer du spam ou des éléments malveillants.

AEM Forms as a Cloud Service prend en charge les solutions CAPTCHA suivantes :

* [reCAPTCHA de Google](#connect-your-aem-forms-environment-with-recaptcha-service-by-google)
* [Captcha](/help/forms/integrate-adaptive-forms-hcaptcha-core-components.md)


## Connectez votre environnement AEM Forms avec le service reCAPTCHA de Google {#connect-your-forms-environment-with-recaptcha-service-by-google}

Les auteurs de formulaires peuvent utiliser le service reCAPTCHA de Google pour implémenter reCAPTCHA dans les Forms adaptatifs. Il offre des fonctionnalités avancées de CAPTCHA pour protéger votre site. Pour plus d’informations sur le fonctionnement de reCAPTCHA, consultez [Google reCAPTCHA](https://developers.google.com/recaptcha/). [!DNL AEM Forms] as a [!DNL Cloud Service] prend en charge Google reCAPTCHA v2 dans Adaptive Forms. Vous pouvez l’utiliser pour présenter un défi CAPTCHA lors de l’envoi du formulaire. Pour connecter votre environnement AEM Forms avec le service reCAPTCHA de Google

1. Obtenir la [paire de clés de l’API reCAPTCHA](https://www.google.com/recaptcha/admin) de Google. Elle comprend une **clé de site** et une **clé secrète**.

   ![Créez une configuration Google reCAPTCHA du site web Google pour obtenir les clés reCAPTCHA](/help/forms/assets/google-captcha.gif)
1. Créez un conteneur de configuration sur votre environnement as a Cloud Service AEM Forms. Un conteneur de configuration contient les configurations cloud utilisées pour se connecter AEM aux services externes. Pour créer et configurer un conteneur de configuration afin de connecter votre environnement AEM Forms au service reCAPTCHA par Google :
   1. Ouvrez votre instance AEM Forms as a Cloud Service.
   1. Accédez à **[!UICONTROL Outils > Général > Navigateur de configuration]**. Dans l’explorateur de configurations, vous pouvez :
   1. Sélectionnez un dossier existant ou créez-en un. Vous pouvez créer un dossier et activer l’option Configurations du cloud pour celui-ci ou Activer l’option Configurations du cloud pour un dossier existant :

      * Pour créer un dossier et activer l’option Configurations du cloud :
         1. Dans l’explorateur de configurations, cliquez sur **[!UICONTROL Créer]**.
         1. Dans la boîte de dialogue Créer une configuration, spécifiez le nom, le titre et sélectionnez l’option **[!UICONTROL Configurations du cloud]**.
         1. Cliquez sur **[!UICONTROL Créer]**.
      * Pour activer l’option Configurations du cloud pour un dossier existant :
         1. Dans l’explorateur de configurations, sélectionnez le dossier, puis **[!UICONTROL Propriétés]**.
         1. Dans la boîte de dialogue Propriétés de configuration, activez **[!UICONTROL Configurations cloud]**.
         1. Sélectionnez **[!UICONTROL Enregistrer et fermer]** pour enregistrer la configuration et fermer la boîte de dialogue.

1. Configurez le Cloud Service :
   1. Sur votre instance d’auteur AEM, accédez à ![tools-1](assets/tools-1.png) > **[!UICONTROL Cloud Service]** et sélectionnez **[!UICONTROL reCAPTCHA]**.
   1. Sélectionnez un conteneur de configuration, créé ou mis à jour dans la section précédente. Sélectionnez **[!UICONTROL Créer]**.
   1. Spécifiez **[!UICONTROL Title]**, **[!UICONTROL Name]**, **[!UICONTROL Site Key]** et **[!UICONTROL Secret Key]** pour le service reCAPTCHA (Obtenu à l’étape 1). Sélectionnez **[!UICONTROL Créer]**.

   ![Configurez le Cloud Service pour connecter votre environnement AEM Forms avec le service reCAPTCHA par Google](/help/forms/assets/captcha-configuration.gif)

   Une fois le service reCAPTCHA configuré, il peut être utilisé dans un formulaire adaptatif. Pour plus d’informations, voir [Utilisation de Google reCAPTCHA dans un formulaire adaptatif](#using-reCAPTCHA).

## Utiliser Google reCAPTCHA dans un formulaire adaptatif {#using-reCAPTCHA}

Pour utiliser reCAPTCHA dans Adaptive Forms :

1. Ouvrez votre instance AEM Forms as a Cloud Service.
1. Accédez à **[!UICONTROL Forms]** > **[!UICONTROL Forms and Documents]**.
1. Sélectionnez une Forms adaptative et sélectionnez **[!UICONTROL Propriétés]**. Pour l’option **[!UICONTROL Conteneur de configuration]**, sélectionnez le Conteneur de configuration contenant la configuration de cloud qui connecte AEM Forms au service reCAPTCHA par Google et sélectionnez **[!UICONTROL Enregistrer et fermer]**.

   Si vous ne disposez pas d’un conteneur de configuration de ce type, reportez-vous à la section [ Connexion de votre environnement AEM Forms avec le service reCAPTCHA de Google](#connect-your-forms-environment-with-recaptcha-service-by-google) pour savoir comment créer un tel conteneur de configuration.

   ![Sélectionner Conteneur de configuration](/help/forms/assets/captcha-properties.png)

1. Sélectionnez une Forms adaptative et sélectionnez **[!UICONTROL Modifier]**. Le formulaire adaptatif s’ouvre dans l’éditeur de Forms adaptatif.
1. A partir de l’explorateur de composants, faites glisser le composant **[!UICONTROL Adaptive Form reCAPTCHA]** sur le formulaire adaptatif.

   La validation de Google reCAPTCHA est sensible au temps et expire dans environ deux minutes. Par conséquent, Adobe recommande de placer le composant **[!UICONTROL reCAPTCHA]** de formulaire adaptatif juste avant le bouton **[!UICONTROL Envoyer]** .

1. Sélectionnez le composant **[!UICONTROL Adaptive Form reCAPTCHA]** et sélectionnez l’icône de propriétés ![Icône Propriétés](assets/configure-icon.svg) . Elle ouvre la boîte de dialogue des propriétés. Spécifiez les propriétés obligatoires suivantes :
   * **[!UICONTROL Nom] :** Vous pouvez facilement identifier un composant de formulaire avec son nom unique dans le formulaire et dans l’éditeur de règles, mais le nom ne doit pas contenir d’espaces ni de caractères spéciaux.
   * **[!UICONTROL Configuration CAPTCHA] :** Sélectionnez une configuration cloud configurée pour présenter la boîte de dialogue Google reCAPTCHA pour le formulaire. Vous pouvez avoir plusieurs configurations de cloud dans votre environnement à des fins similaires. Choisissez donc le service avec soin. Si aucun service n’est répertorié, reportez-vous à la section [Connexion de votre environnement AEM Forms avec le service reCAPTCHA de Google](#connect-your-forms-environment-with-recaptcha-service-by-google) pour savoir comment créer un Cloud Service qui connecte votre environnement AEM Forms au service reCAPTCHA par Google.
   * **Taille du captcha :** Vous pouvez sélectionner la taille d’affichage de la boîte de dialogue de défi Google reCAPTCHA. Utilisez l’option **[!UICONTROL Compact]** pour afficher une petite taille et l’option **[!UICONTROL Normale]** pour afficher une boîte de dialogue de défi Google reCAPTCHA de taille relativement importante.

1. Sélectionnez **[!UICONTROL Terminé]**.

   Désormais, le **protégé par reCAPTCHA** s’affiche sur votre formulaire adaptatif. Il s’affiche sur toutes les Forms adaptatives configurées pour utiliser le service Google reCAPTCHA.

   Désormais, seuls les formulaires légitimes, dans lesquels l’utilisateur réussit à résoudre le problème posé par le service Google reCAPTCHA, sont autorisés à être envoyés.
   ![Badge protégé par reCAPTCHA de Google](/help/forms/assets/google-recaptcha-v2.png)

<!--
### Show or hide CAPTCHA component based on rules {#show-hide-captcha}

You can select to show or hide the CAPTCHA component based on rules that you apply on a component in an Adaptive Form. Select the component, select ![edit rules](assets/edit-rules-icon.svg), and select **[!UICONTROL Create]** to create a rule. For more information on creating rules, see [Rule Editor](rule-editor.md).

For example, the CAPTCHA component must display in an Adaptive Form only if the Currency Value field in the form has a value of more than 25000.

Select the **[!UICONTROL Currency Value]** field in the form and create the following rules:

![Show or hide rules](assets/rules-show-hide-captcha.png)

   >[!NOTE]
   >
   > When you select a reCAPTCHA v2 configuration and the size is set to [!UICONTROL Invisible], the show/hide option remains disabled.

   -->

## Questions fréquentes

**Q : Puis-je utiliser plusieurs composants Captcha dans un formulaire adaptatif ?**
**Réponse :** L’utilisation de plusieurs composants Captcha dans un formulaire adaptatif n’est pas prise en charge. En outre, il n’est pas recommandé d’utiliser le composant Captcha dans un fragment ou un panneau marqué pour le chargement différé.

## Voir également {#see-also}

{{see-also}}