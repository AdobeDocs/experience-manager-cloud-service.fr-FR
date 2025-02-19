---
title: Comment utiliser Google reCAPTCHA dans un formulaire adaptatif AEM ?
description: Améliorez la sécurité des formulaires avec le service reCAPTCHA de Google sans effort. Guide détaillé inclus.
topic-tags: Adaptive Forms, author
keywords: Service Google reCAPTCHA, Forms adaptatif, défi CAPTCHA, prévention des robots, composants principaux, sécurité de l’envoi des formulaires, prévention des spams des formulaires
feature: Adaptive Forms, Core Components
role: User, Developer
exl-id: d116f979-efb6-4fac-8202-89afd1037b2c
source-git-commit: 76301ca614ae2256f5f8b00c41399298c761ee33
workflow-type: tm+mt
source-wordcount: '1418'
ht-degree: 22%

---

# Utilisation de Google reCAPTCHA dans un formulaire adaptatif AEM basé sur les composants principaux {#using-reCAPTCHA-in-adaptive-forms}

| Application | Lien de l’article |
| -------- | ---------------------------- |
| Formulaire adaptatif basé sur les composants principaux | Cet article |
| Formulaire adaptatif basé sur les composants de base | [Cliquez ici](/help/forms/captcha-adaptive-forms.md) |

CAPTCHA (Completely Automated Public Turing test to tell Computers and Humans Apart, Test public de Turing complètement automatisé ayant pour but de différencier les personnes humaines des ordinateurs) est un programme couramment utilisé dans les transactions en ligne pour différencier les personnes humaines des programmes automatisés ou des robots. Il présente un test et évalue la réponse de l’utilisateur ou de l’utilisatrice pour déterminer s’il s’agit d’une personne humaine ou d’un robot qui interagit avec le site. Cela empêche l’utilisateur ou l’utilisatrice de continuer si le test échoue et permet de sécuriser les transactions en ligne en empêchant les robots d’envoyer du spam ou des éléments malveillants.

AEM Forms as a Cloud Service prend en charge les solutions CAPTCHA suivantes :

* [reCAPTCHA de Google](#connect-your-aem-forms-environment-with-recaptcha-service-by-google)
* [hCaptcha](/help/forms/integrate-adaptive-forms-hcaptcha-core-components.md)


## Connecter vos composants principaux AEM Forms au service reCAPTCHA de Google {#connect-your-forms-environment-with-recaptcha-service-by-google}

Les auteurs de formulaires peuvent utiliser le service reCAPTCHA de Google pour implémenter reCAPTCHA dans le Forms adaptatif. Il offre des fonctionnalités CAPTCHA avancées pour protéger votre site. Pour plus d’informations sur le fonctionnement de reCAPTCHA, consultez [Google reCAPTCHA](https://developers.google.com/recaptcha/). Vous l’utilisez pour présenter un défi CAPTCHA lors de l’envoi du formulaire.[!DNL AEM Forms] as a [!DNL Cloud Service] prend en charge Google reCAPTCHA v2 et reCAPTCHA Enterprise. Aucune autre version n’est prise en charge. Notez également que reCAPTCHA dans le Forms adaptatif n’est pas pris en charge en mode hors ligne sur l’application AEM Forms.

Selon vos besoins, vous pouvez configurer le service reCAPTCHA pour activer :

* [reCAPTCHA Enterprise](#steps-to-implement-reCAPTCHA-enterprise-in-forms-core-components)
* [reCAPTCHA v2](#steps-to-implement-reCAPTCHA-v2-in-forms)

### Configuration de reCAPTCHA Enterprise  {#steps-to-implement-reCAPTCHA-enterprise-in-forms-core-components}

1. Créez ou sélectionnez un [projet Google Cloud](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#before-you-begin) puis activez l’API [reCAPTCHA Enterprise](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#enable-the-recaptcha-enterprise-api).
1. Obtenez l’[ID de projet](https://support.google.com/googleapi/answer/7014113?hl=en#:~:text=To%20locate%20your%20project%20ID,a%20member%20of%20are%20displayed) et créez une [clé API](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#create_an_api_key) et une [clé de site pour les sites web](https://cloud.google.com/recaptcha-enterprise/docs/create-key#create-key).
1. Créez un conteneur de configurations pour les services cloud.

   1. Accédez à **[!UICONTROL Outils > Général > Navigateur de configuration]**.
   1. Sélectionnez un dossier ou créez-en un, puis activez-le pour les configurations cloud en procédant comme suit :
      1. Dans l’explorateur de configurations, sélectionnez le dossier, puis sélectionnez **[!UICONTROL Propriétés]**.
      1. Dans la boîte de dialogue Propriétés de configuration, activez **[!UICONTROL Configurations cloud]**.
      1. Sélectionnez **[!UICONTROL Enregistrer et fermer]** pour enregistrer la configuration et fermer la boîte de dialogue.

1. Configurez le service cloud pour [!DNL reCAPTCHA Enterprise].

   1. Sur votre instance de création Experience Manager, accédez à ![tools-1](assets/tools-1.png) > **[!UICONTROL Cloud Services]**.
   1. Sélectionnez **[!UICONTROL reCAPTCHA]**. La page de configuration s’ouvre. Sélectionnez le conteneur de configurations que vous avez créé et sélectionnez **[!UICONTROL Créer]**.
   1. Sélectionnez la version comme [!DNL reCAPTCHA Enterprise] et spécifiez le nom, l’ID de projet, la clé de site et la clé API (obtenue à l’étape 2) pour le service reCAPTCHA Enterprise.
   1. Sélectionnez le type de clé. Le type de clé doit être identique à celui que vous avez configuré dans le projet [Google Cloud](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#before-you-begin) par exemple, **Clé de site de case à cocher** ou **Clé de site basée sur les scores**.
   1. Spécifiez un score [seuil compris entre 0 et 1](https://cloud.google.com/recaptcha-enterprise/docs/interpret-assessment#interpret_scores). Les scores supérieurs ou égaux aux scores de seuil indiquent une interaction humaine, sinon il s’agit d’une interaction avec un robot.
   1. Sélectionnez **[!UICONTROL Créer]** pour créer la configuration du service cloud.

<!--
    1. In the Edit Component dialog, specify the name, project ID, site key, API key (obtained in steps 2 and 3), select the key type, and enter the threshold score. Select **[!UICONTROL Save Settings]** and then select **[!UICONTROL OK]** to complete the configuration.
-->

Une fois que le service reCAPTCHA Enterprise est activé, il peut être utilisé dans les formulaires adaptatifs. Voir [Utilisation du CAPTCHA dans les formulaires adaptifs](#using-reCAPTCHA).

<!--
![reCAPTCHA Enterprise](/help/forms/assets/recaptcha1-enterprise.png)
-->


### Configurer Google reCAPTCHA v2 {#steps-to-implement-reCAPTCHA-v2-in-forms}

1. Obtenir la [paire de clés de l’API reCAPTCHA](https://www.google.com/recaptcha/admin) de Google. Elle comprend une **clé de site** et une **clé secrète**.

   ![Créez une configuration reCAPTCHA Google du site web Google pour obtenir des clés reCAPTCHA](/help/forms/assets/google-captcha.gif)
1. Créez un conteneur de configuration dans votre environnement AEM Forms as a Cloud Service. Un conteneur de configurations contient les configurations cloud utilisées pour connecter AEM à des services externes. Pour créer et configurer un conteneur de configuration afin de connecter votre environnement AEM Forms au service reCAPTCHA de Google :
   1. Ouvrez votre instance AEM Forms as a Cloud Service.
   1. Accédez à **[!UICONTROL Outils > Général > Navigateur de configuration]**. Dans l’explorateur de configurations, vous pouvez :
   1. Sélectionnez un dossier existant ou créez-en un. Vous pouvez créer un dossier et activer l’option Configurations cloud pour celui-ci ou Activer l’option Configurations cloud pour un dossier existant :

      * Pour créer un dossier et activer l’option Configurations cloud pour celui-ci :
         1. Dans le navigateur de configuration, cliquez sur **[!UICONTROL Créer]**.
         1. Dans la boîte de dialogue Créer une configuration, spécifiez le nom et le titre, puis sélectionnez l’option **[!UICONTROL Configurations cloud]**.
         1. Cliquez sur **[!UICONTROL Créer]**.
      * Pour activer l’option Configurations cloud pour un dossier existant :
         1. Dans l’explorateur de configurations, sélectionnez le dossier, puis sélectionnez **[!UICONTROL Propriétés]**.
         1. Dans la boîte de dialogue Propriétés de configuration, activez **[!UICONTROL Configurations cloud]**.
         1. Sélectionnez **[!UICONTROL Enregistrer et fermer]** pour enregistrer la configuration et fermer la boîte de dialogue.

1. Configurez le Cloud Service :
   1. Sur votre instance d’auteur AEM, accédez à ![tools-1](assets/tools-1.png) > **[!UICONTROL Services cloud]** et sélectionnez **[!UICONTROL reCAPTCHA]**.
   1. Sélectionnez un conteneur de configuration, créé ou mis à jour dans la section précédente. Sélectionnez **[!UICONTROL Créer]**.
   1. Spécifiez **[!UICONTROL Titre]**, **[!UICONTROL Nom]**, **[!UICONTROL Clé du site]** et **[!UICONTROL Clé secrète]** pour le service reCAPTCHA (obtenu à l’étape 1). Sélectionnez **[!UICONTROL Créer]**.

   ![Configurez le Cloud Service pour connecter votre environnement AEM Forms au service reCAPTCHA de Google](/help/forms/assets/captcha-configuration.gif)

   Une fois le service reCAPTCHA configuré, il peut être utilisé dans un formulaire adaptatif. Pour plus d’informations, voir [utilisation de Google reCAPTCHA dans un formulaire adaptatif](#using-reCAPTCHA).


Utilisation de Google reCAPTCHA dans les formulaires adaptatifs

## Utiliser Google reCAPTCHA dans un formulaire adaptatif {#using-reCAPTCHA}

Pour utiliser reCAPTCHA dans le Forms adaptatif :

1. Ouvrez votre instance AEM Forms as a Cloud Service.
1. Accédez à **[!UICONTROL Forms]** > **[!UICONTROL Forms et documents]**.
1. Sélectionnez un Forms adaptatif, puis sélectionnez **[!UICONTROL Propriétés]**. Pour l’option **[!UICONTROL Conteneur de configurations]**, sélectionnez le Conteneur de configurations contenant la Configuration du cloud qui connecte AEM Forms au service reCAPTCHA de Google et sélectionnez **[!UICONTROL Enregistrer et fermer]**.

   Si vous ne disposez pas d’un tel conteneur de configuration, consultez la section [Connecter votre environnement AEM Forms au service reCAPTCHA de Google](#connect-your-forms-environment-with-recaptcha-service-by-google) pour savoir comment créer un tel conteneur de configuration.

   ![Sélectionner le conteneur de configuration](/help/forms/assets/captcha-properties.png)

1. Sélectionnez un Forms adaptatif, puis sélectionnez **[!UICONTROL Modifier]**. Le formulaire adaptatif s’ouvre dans l’éditeur de Forms adaptatif.
1. À partir de l’explorateur de composants, faites glisser et déposez le composant **[!UICONTROL formulaire adaptatif reCAPTCHA]** sur le formulaire adaptatif.

   >[!NOTE]
   > * La validation reCAPTCHA de Google est sensible au temps et expire dans environ deux minutes. Par conséquent, Adobe recommande de placer le composant **[!UICONTROL Formulaire adaptatif reCAPTCHA]** juste avant le bouton **[!UICONTROL Envoyer]**.

1. Sélectionnez le composant **[!UICONTROL Formulaire adaptatif reCAPTCHA]** et sélectionnez l’icône de propriétés ![Icône Propriétés](assets/configure-icon.svg). Cela ouvre la boîte de dialogue des propriétés. Spécifiez les propriétés obligatoires suivantes :
   * **[!UICONTROL Nom] :** vous pouvez identifier facilement un composant de formulaire en lui attribuant un nom unique dans le formulaire et dans l’éditeur de règles, mais le nom ne doit pas contenir d’espaces ni de caractères spéciaux.
   * **[!UICONTROL Titre] :** spécifiez un titre pour le widget CAPTCHA. La valeur par défaut est **Captcha**. Sélectionnez **Masquer le titre** si vous ne souhaitez pas que le titre apparaisse. Sélectionnez **Autoriser le texte enrichi pour le titre** pour modifier votre titre au format texte enrichi. Vous pouvez également marquer votre titre comme **Élément de formulaire non lié**.
   * **[!UICONTROL Configuration de CAPTCHA] :** sélectionnez une configuration dans le menu déroulant Paramètres pour **reCAPTCHA Enterprise** ou **reCAPTCHA v2** afin de présenter la boîte de dialogue reCAPTCHA Google pour le formulaire :
      1. Si vous sélectionnez la version **reCAPTCHA Enterprise**, le type de clé peut être **case à cocher** ou **basé sur le score**. Il dépend de votre sélection lorsque vous configurez [clé de site pour les sites web](https://cloud.google.com/recaptcha-enterprise/docs/create-key#create-key) :

         >[!NOTE]
         >
         >* Dans la configuration cloud avec **type de clé** comme **case à cocher**, le message d’erreur personnalisé s’affiche sous la forme d’un message intégré si la validation captcha échoue.
         >* Dans la configuration cloud avec **type de clé** comme **basé sur le score**, le message d’erreur personnalisé s’affiche sous la forme d’un pop-up si la validation captcha échoue.

      1. Vous pouvez sélectionner la taille **[!UICONTROL normale]** et la taille **[!UICONTROL compacte]**.

     >[!NOTE]
     >* Vous pouvez disposer de plusieurs configurations cloud dans votre environnement à des fins similaires. Donc, choisissez le service avec soin. Si aucun service n’est répertorié, consultez [Connexion de votre environnement AEM Forms au service reCAPTCHA de Google](#connect-your-forms-environment-with-recaptcha-service-by-google) pour savoir comment créer un Cloud Service qui connecte votre environnement AEM Forms au service reCAPTCHA de Google.

   * **Taille de Captcha :** vous pouvez sélectionner la taille d’affichage de la boîte de dialogue de défi reCAPTCHA de Google. Utilisez l’option **[!UICONTROL Compact]** pour afficher une boîte de dialogue de défi de Google reCAPTCHA de petite taille et l’option **[!UICONTROL Normal]** pour afficher une boîte de dialogue de défi de de taille relativement grande.
Si vous sélectionnez la version **reCAPTCHA v2** :
      1. Vous pouvez sélectionner la taille **[!UICONTROL Normale]** ou **[!UICONTROL Compacte]** pour le widget reCAPTCHA.
      1. Vous pouvez sélectionner l’option **[!UICONTROL Invisible]** pour ne montrer le test CAPTCHA que dans le cas d’une activité suspecte.

   Le service reCAPTCHA est activé sur le formulaire adaptatif. Vous pouvez prévisualiser le formulaire et voir le fonctionnement du CAPTCHA. Le badge **protégé par reCAPTCHA**, affiché ci-dessous, s’affiche sur les formulaires protégés.

   ![Badge protégé par reCAPTCHA de Google](/help/forms/assets/google-recaptcha-v2.png)

1. Sélectionnez **[!UICONTROL Terminé]**.

   Désormais, le **protégé par reCAPTCHA** s’affiche sur votre formulaire adaptatif. Elle s’affiche sur tous les Forms adaptatifs configurés pour utiliser le service reCAPTCHA de Google.

   Désormais, seuls les formulaires légitimes, dans lesquels le remplisseur de formulaire résout avec succès le problème posé par le service reCAPTCHA de Google, sont autorisés pour l’envoi.

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
**Réponse :** l’utilisation de plusieurs composants Captcha dans un formulaire adaptatif n’est pas prise en charge. En outre, il n’est pas recommandé d’utiliser le composant Captcha dans un fragment ou un panneau marqué pour le chargement différé.

## Voir également {#see-also}

{{see-also}}
