---
title: Utilisation de reCAPTCHA dans le Forms adaptatif
description: Découvrez comment configurer le service Google reCAPTCHA dans Forms adaptatif.
topic-tags: adaptive_forms, author
source-git-commit: a1689c61715f01cb4eb62882dbcd6e202b74ffc9
workflow-type: tm+mt
source-wordcount: '1913'
ht-degree: 48%

---

# Utiliser reCAPTCHA dans les Forms adaptatives{#using-reCAPTCHA-in-adaptive-forms}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/captcha-adaptive-forms.html) |
| AEM as a Cloud Service | Cet article |

<span class="preview"> Adobe recommande d’utiliser la capture de données moderne et extensible. [Composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=fr) pour [création d’un Forms adaptatif](/help/forms/creating-adaptive-form-core-components.md) ou [Ajout de Forms adaptatif à des pages AEM Sites](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Ces composants représentent une avancée significative dans la création de Forms adaptatif, ce qui garantit des expériences utilisateur impressionnantes. Cet article décrit l’approche plus ancienne de la création de Forms adaptatif à l’aide de composants de base. </span>

CAPTCHA (Completely Automated Public Turing test to say Computers and Humans apart) est un programme couramment utilisé dans les transactions en ligne pour distinguer les humains des programmes ou robots automatisés. Il pose un problème et évalue la réponse de l’utilisateur pour déterminer s’il s’agit d’un humain ou d’un robot interagissant avec le site. Elle empêche l’utilisateur de procéder si le test échoue et permet de sécuriser les transactions en ligne en empêchant les robots de publier du spam ou des fins malveillantes.

[!DNL AEM Forms] prendre en charge reCAPTCHA dans Adaptive Forms. Vous pouvez utiliser le service reCAPTCHA de Google pour implémenter CAPTCHA.

>[!NOTE]
>
>* [!DNL AEM Forms] prendre en charge reCaptcha v2 et reCaptcha Enterprise. Toute autre version n’est pas prise en charge.
>* reCAPTCHA dans Adaptive Forms n’est pas pris en charge en mode hors ligne sur [!DNL AEM Forms] application.
>

## Configuration du service reCAPTCHA par Google {#google-reCAPTCHA}

Les auteurs de formulaires peuvent utiliser le service reCAPTCHA de Google pour implémenter reCAPTCHA dans les Forms adaptatifs. Il offre des fonctionnalités avancées de CAPTCHA pour protéger votre site. Pour plus d’informations sur le fonctionnement de reCAPTCHA, voir [Google reCAPTCHA](https://developers.google.com/recaptcha/). Le service reCAPTCHA comprend [!DNL reCAPTCHA v2] et [!DNL reCAPTCHA Enterprise] dans lequel vous pouvez intégrer [!DNL AEM Forms]. Selon vos besoins, vous pouvez configurer le service reCAPTCHA pour activer :

![reCAPTCHA](/help/forms/assets/recaptcha_new.png)

* [reCAPTCHA Enterprise dans AEM Forms](#steps-to-implement-reCAPTCHA-enterprise-in-forms)
* [reCAPTCHA v2 dans AEM Forms](#steps-to-implement-reCAPTCHA-v2-in-forms)


### Configuration de reCAPTCHA Enterprise  {#steps-to-implement-reCAPTCHA-enterprise-in-forms}

1. Créez ou sélectionnez une [Projet Google Cloud](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#before-you-begin) et activez [API d’entreprise reCAPTCHA](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#enable-the-recaptcha-enterprise-api).
1. Obtention de la variable [Identifiant de projet](https://support.google.com/googleapi/answer/7014113?hl=en#:~:text=To%20locate%20your%20project%20ID,a%20member%20of%20are%20displayed) et créez un [Clé API](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#create_an_api_key) et un [clé de site pour les sites web](https://cloud.google.com/recaptcha-enterprise/docs/create-key#create-key).
1. Créez un conteneur de configuration pour les services cloud.

   1. Accédez à **[!UICONTROL Outils > Général > Navigateur de configuration]**.
   1. Sélectionnez un dossier ou créez-en un, puis activez le dossier pour les configurations cloud en procédant comme suit :
      1. Dans le navigateur de configuration, sélectionnez le dossier  et appuyez sur **[!UICONTROL Propriétés]**.
      1. Dans la boîte de dialogue Propriétés de configuration, activez **[!UICONTROL Configurations cloud]**.
      1. Appuyez sur **[!UICONTROL Enregistrer et fermer]** pour enregistrer la configuration et fermer la boîte de dialogue.

1. Configurez le service cloud pour [!DNL reCAPTCHA Enterprise].

   1. Sur votre instance d’auteur Experience Manager, accédez à ![tools-1](assets/tools-1.png) > **[!UICONTROL Cloud Services]**.
   1. Appuyer **[!UICONTROL reCAPTCHA]**. La page Configurations s’ouvre. Sélectionnez le conteneur de configuration que vous avez créé et appuyez sur **[!UICONTROL Créer]**.
   1. Sélectionner la version comme [!DNL reCAPTCHA Enterprise] et indiquez le nom, l’ID de projet, la clé du site et la clé API (Obtenu à l’étape 2) pour le service d’entreprise reCAPTCHA.
   1. Sélectionnez le type de clé, le type de clé doit être identique à la clé du site que vous avez configurée dans la variable [Projet Google Cloud](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#before-you-begin), par exemple : **Clé de site de case à cocher** ou **Clé de site basée sur les scores**.
   1. Spécifiez un [score de seuil dans la plage 0 à 1](https://cloud.google.com/recaptcha-enterprise/docs/interpret-assessment#interpret_scores). Les scores supérieurs ou égaux au seuil identifient l’interaction humaine, considérée autrement comme une interaction de robots.
   1. Appuyer **[!UICONTROL Créer]** pour créer la configuration du service cloud.

<!--
    1. In the Edit Component dialog, specify the name, project ID, site key, API key (obtained in steps 2 and 3), select the key type, and enter the threshold score. Tap **[!UICONTROL Save Settings]** and then tap **[!UICONTROL OK]** to complete the configuration.
-->

Une fois que le service reCAPTCHA Enterprise est activé, il peut être utilisé dans les formulaires adaptatifs. Voir [utilisation de CAPTCHA dans les formulaires adaptatifs](#using-reCAPTCHA).

<!--
![reCAPTCHA Enterprise](/help/forms/assets/recaptcha1-enterprise.png)
-->

### Configuration de Google reCAPTCHA v2 {#steps-to-implement-reCAPTCHA-v2-in-forms}

1. Obtenir [paire de clés de l’API reCAPTCHA](https://www.google.com/recaptcha/admin) de Google. Il comprend un **clé du site** et un **clé secrète**.
1. Créez un conteneur de configuration pour les services cloud.
   1. Accédez à **[!UICONTROL Outils > Général > Navigateur de configuration]**.
   1. Sélectionnez un dossier ou créez-en un, puis activez le dossier pour les configurations cloud en procédant comme suit :
      1. Dans le navigateur de configuration, sélectionnez le dossier  et appuyez sur **[!UICONTROL Propriétés]**.
      1. Dans la boîte de dialogue Propriétés de configuration, activez **[!UICONTROL Configurations cloud]**.
      1. Appuyez sur **[!UICONTROL Enregistrer et fermer]** pour enregistrer la configuration et fermer la boîte de dialogue.

1. Configurez le service cloud pour reCAPTCHA v2.

   1. Sur votre instance d’auteur AEM, accédez à ![tools-1](assets/tools-1.png) > Déploiement > **Services cloud**.
   1. Appuyer **[!UICONTROL reCAPTCHA]**. La page Configurations s’ouvre. Sélectionnez le conteneur de configuration que vous avez créé et appuyez sur **[!UICONTROL Créer]**.
   1. Sélectionner la version comme [!DNL reCAPTCHA v2] , spécifiez le nom, la clé du site et la clé secrète pour le service reCAPTCHA (Obtenu à l’étape 1), puis appuyez sur **[!UICONTROL Créer]** pour créer la configuration du service cloud.
   1. Dans cette boîte de dialogue, spécifiez le site et les clés de site et secrète obtenues à l’étape 1. Appuyez sur **[!UICONTROL Enregistrer les paramètres]** puis sur **OK** pour terminer la configuration.

   Une fois le service reCAPTCHA configuré, il peut être utilisé dans les formulaires adaptatifs. Pour plus d’informations, voir [utilisation de CAPTCHA dans les formulaires adaptatifs](#using-reCAPTCHA).

<!--![reCAPTCHA v2](/help/forms/assets/recaptcha-v2.png)-->


## Utiliser reCAPTCHA dans les formulaires adaptatifs {#using-reCAPTCHA}

Pour utiliser reCAPTCHA dans les formulaires adaptatifs :

1. Ouvrez un formulaire adaptatif en mode d’édition.

   >[!NOTE]
   >
   >Assurez-vous que le conteneur de configuration sélectionné lors de la création du formulaire adaptatif contient le service cloud reCAPTCHA. Vous pouvez également modifier les propriétés du formulaire adaptatif pour modifier le conteneur de configuration associé au formulaire.

1. Dans l’explorateur de composants, faites glisser et déposez le composant **Captcha** sur le formulaire adaptatif.

   >[!NOTE]
   >
   >* L’utilisation de plusieurs composants Captcha dans un formulaire adaptatif n’est pas prise en charge. En outre, il n’est pas recommandé d’utiliser CAPTCHA dans un panneau marqué pour le chargement différé ou dans un fragment.
   >* reCaptcha est sensible au temps et expire dans environ deux minutes. Par conséquent, il est recommandé de placer le composant Captcha juste avant le bouton Envoyer dans le formulaire adaptatif.

1. Sélectionnez le composant Captcha que vous avez ajouté et appuyez sur ![cmppr](assets/cmppr.png) pour modifier ses propriétés.
1. Indiquez un titre pour le widget CAPTCHA. La valeur par défaut est **Captcha**. Sélectionnez **Masquer le titre** si vous ne voulez pas que le titre apparaisse.
1. Dans la **Service Captcha** , sélectionnez **reCAPTCHA** pour activer le service reCAPTCHA si vous l’avez configuré comme décrit à la section [Service reCAPTCHA par Google](#google-reCAPTCHA).
1. Sélectionnez une configuration dans la liste déroulante Paramètres pour **reCAPTCHA Enterprise** ou **reCAPTCHA v2**
   1. Si vous sélectionnez **reCAPTCHA Enterprise** version, le type de clé peut être **checkbox** ou **score basé**, Selon votre sélection lors de la configuration de [clé de site pour les sites web](https://cloud.google.com/recaptcha-enterprise/docs/create-key#create-key):

   >[!NOTE]
   >
   >* Dans la configuration cloud avec **type de clé** as **checkbox**, le message d’erreur personnalisé s’affiche en ligne si la validation du captcha échoue.
   >* Dans la configuration cloud avec **type de clé** as **score basé**, le message d’erreur personnalisé s’affiche sous forme de message contextuel si la validation du captcha échoue.

   1. Vous pouvez sélectionner la taille **[!UICONTROL Normal]** et **[!UICONTROL Compact]**.
   1. Vous pouvez sélectionner un **[!UICONTROL Référence de liaison]**, dans **[!UICONTROL Référence de liaison]** les données envoyées sont des données liées, sinon il s’agit de données non liées. Vous trouverez ci-dessous des exemples XML de données non liées et de données liées (avec une référence de liaison comme SSN), respectivement, lorsqu’un formulaire est envoyé.

   ```xml
           <?xml version="1.0" encoding="UTF-8" standalone="no"?>
           <afData>
           <afUnboundData>
               <data>
                   <captcha16820607953761>
                       <captchaType>reCaptchaEnterprise</captchaType>
                       <captchaScore>0.9</captchaScore>
                   </captcha16820607953761>
               </data>
           </afUnboundData>
           <afBoundData>
               <Root
                   xmlns:xfa="http://www.xfa.org/schema/xfa-data/1.0/"
                   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
                   <PersonalDetails>
                       <SSN>371237912</SSN>
                       <FirstName>Sarah </FirstName>
                       <LastName>Smith</LastName>
                   </PersonalDetails>
                   <OtherInfo>
                       <City>California</City>
                       <Address>54 Residency</Address>
                       <State>USA</State>
                       <Zip>123112</Zip>
                   </OtherInfo>
               </Root>
           </afBoundData>
           <afSubmissionInfo>
               <stateOverrides/>
               <signers/>
               <afPath>/content/dam/formsanddocuments/captcha-form</afPath>
               <afSubmissionTime>20230608034928</afSubmissionTime>
           </afSubmissionInfo>
           </afData>
   ```

   ```xml
           <?xml version="1.0" encoding="UTF-8" standalone="no"?>
           <afData>
           <afUnboundData>
               <data/>
           </afUnboundData>
           <afBoundData>
               <Root
                   xmlns:xfa="http://www.xfa.org/schema/xfa-data/1.0/"
                   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
                   <PersonalDetails>
                       <SSN>
                           <captchaType>reCaptchaEnterprise</captchaType>
                           <captchaScore>0.9</captchaScore>
                       </SSN>
                       <FirstName>Sarah</FirstName>
                       <LastName>Smith</LastName>
                   </PersonalDetails>
                   <OtherInfo>
                       <City>California</City>
                       <Address>54 Residency</Address>
                       <State>USA</State>
                       <Zip>123112</Zip>
                   </OtherInfo>
               </Root>
           </afBoundData>
           <afSubmissionInfo>
               <stateOverrides/>
               <signers/>
               <afPath>/content/dam/formsanddocuments/captcha-form</afPath>
               <afSubmissionTime>20230608035111</afSubmissionTime>
           </afSubmissionInfo>
           </afData>
   ```

   Si vous sélectionnez **reCAPTCHA v2** version :
   1. Vous pouvez sélectionner la taille comme **[!UICONTROL Normal]** ou **[!UICONTROL Compact]** pour le widget reCAPTCHA.
   1. Vous pouvez sélectionner la variable **[!UICONTROL Invisible]** option de ne montrer le défi CAPTCHA que dans le cas d&#39;une activité suspecte.

   Le service reCAPTCHA est activé sur le formulaire adaptatif. Vous pouvez prévisualiser le formulaire et voir le fonctionnement de CAPTCHA. La variable **protégé par reCAPTCHA** Le badge, affiché ci-dessous, s’affiche sur les formulaires protégés.
   ![Badge protégé par reCAPTCHA de Google](/help/forms/assets/google-recaptcha-v2.png)

1. Enregistrez les propriétés.

>[!NOTE]
> 
> Ne pas sélectionner **[!UICONTROL Par défaut]** dans la liste déroulante Service Captcha , car le service CAPTCHA par défaut AEM est obsolète.

>[!VIDEO](https://video.tv.adobe.com/v/3422097/adaptive-forms-recaptcha-core-components-captcha/?quality=12&learn=on)

### Affichage ou masquage du composant CAPTCHA en fonction de règles {#show-hide-captcha}

Vous pouvez choisir d’afficher ou de masquer le composant CAPTCHA en fonction des règles que vous appliquez à un composant d’un formulaire adaptatif. Appuyez sur le composant, sélectionnez ![modifier les règles](assets/edit-rules-icon.svg), puis appuyez sur **[!UICONTROL Créer]** pour créer une règle. Pour plus d’informations sur la création de règles, voir la section [Éditeur de règles](rule-editor.md).

Par exemple, le composant CAPTCHA ne doit s’afficher dans un formulaire adaptatif que si la valeur du champ Valeur monétaire du formulaire est supérieure à 25 000.

Appuyez sur le champ **[!UICONTROL Valeur monétaire]** dans le formulaire et créez les règles suivantes :

![Afficher ou masquer des règles](assets/rules-show-hide-captcha.png)

>[!NOTE]
>
> Lorsque vous sélectionnez une configuration reCAPTCHA v2 et que la taille est définie sur [!UICONTROL Invisible], l’option d’affichage/masquage reste désactivée.

### Valider le CAPTCHA {#validate-captcha}

Vous pouvez valider le CAPTCHA dans un formulaire adaptatif lorsque vous envoyez le formulaire ou que vous basez la validation CAPTCHA sur des actions et conditions des utilisateurs.

#### Valider le CAPTCHA lors de l’envoi du formulaire {#validation-form-submission}

Pour valider automatiquement un CAPTCHA lorsque vous envoyez un formulaire adaptatif :

1. Appuyez sur le composant CAPTCHA et sélectionnez ![cmppr](assets/configure-icon.svg) pour afficher les propriétés du composant.
1. Dans la section **[!UICONTROL Valider le CAPTCHA]**, sélectionnez **[!UICONTROL Valider le CAPTCHA lors de l’envoi du formulaire]**.
1. Appuyez sur ![Terminé](assets/save_icon.svg) pour enregistrer les propriétés du composant.

#### Validation du CAPTCHA sur les actions et conditions des utilisateurs {#validate-captcha-user-action}

Pour valider un CAPTCHA en fonction des conditions et des actions des utilisateurs :

1. Appuyez sur le composant CAPTCHA et sélectionnez ![cmppr](assets/configure-icon.svg) pour afficher les propriétés du composant.
1. Dans la section **[!UICONTROL Valider le CAPTCHA]**, sélectionnez **[!UICONTROL Valider le CAPTCHA sur une action utilisateur]**.
1. Appuyez sur ![Terminé](assets/save_icon.svg) pour enregistrer les propriétés du composant.

[!DNL Experience Manager Forms] fournit une API `ValidateCAPTCHA` pour valider le CAPTCHA à l’aide de conditions prédéfinies. Vous pouvez appeler l’API à l’aide d’une action d’envoi personnalisée ou en définissant des règles sur les composants d’un formulaire adaptatif.

Voici un exemple d’API `ValidateCAPTCHA` permettant de valider le CAPTCHA à l’aide de conditions prédéfinies :

```javascript
if (slingRequest.getParameter("numericbox1614079614831").length() >= 5) {
     GuideCaptchaValidatorProvider apiProvider = sling.getService(GuideCaptchaValidatorProvider.class);
        String formPath = slingRequest.getResource().getPath();
        String captchaData = slingRequest.getParameter(GuideConstants.GUIDE_CAPTCHA_DATA);
        if (!apiProvider.validateCAPTCHA(formPath, captchaData).isCaptchaValid()){
            response.setStatus(400);
            return;
        }
    }
```

L’exemple signifie que l’API `ValidateCAPTCHA` valide le CAPTCHA dans le formulaire uniquement si le nombre de chiffres dans la zone numérique spécifiée par l’utilisateur lors du remplissage du formulaire est supérieur à 5.

**Option 1 : utiliser l’API [!DNL Experience Manager Forms] ValidateCAPTCHA pour valider le CAPTCHA à l’aide d’une action d’envoi personnalisée**

Effectuez les étapes suivantes pour utiliser l’API `ValidateCAPTCHA` pour valider le CAPTCHA à l’aide d’une action d’envoi personnalisée :

1. Ajoutez le script qui inclut l’API `ValidateCAPTCHA` à l’action d’envoi personnalisée. Pour plus d’informations sur les actions d’envoi personnalisées, voir [Création d’une action d’envoi personnalisée pour les formulaires adaptatifs](custom-submit-action-form.md).
1. Sélectionnez le nom de l’action d’envoi personnalisée dans la liste déroulante **[!UICONTROL Action d’envoi]** des propriétés **[!UICONTROL Envoi]** d’un formulaire adaptatif.
1. Appuyez sur **[!UICONTROL Envoyer]**. Le CAPTCHA est validé en fonction des conditions définies dans l’API `ValidateCAPTCHA` de l’action d’envoi personnalisée.

**Option 2 : utiliser l’API [!DNL Experience Manager Forms] ValidateCAPTCHA pour valider le CAPTCHA sur une action de l’utilisateur avant d’envoyer le formulaire**

Vous pouvez également appeler l’API `ValidateCAPTCHA` en appliquant des règles à un composant d’un formulaire adaptatif.

Par exemple, vous ajoutez un bouton **[!UICONTROL Valider le CAPTCHA]** dans un formulaire adaptatif et créez une règle pour appeler un service lors d’un clic sur un bouton.

La figure suivante illustre comment vous pouvez appeler un service lors d’un clic sur le bouton **[!UICONTROL Valider le CAPTCHA]** :

![Valider le CAPTCHA](assets/captcha-validation1.gif)

Vous pouvez appeler la servlet personnalisée qui inclut l’API `ValidateCAPTCHA` à l’aide de l’éditeur de règles et activer ou désactiver le bouton d’envoi du formulaire adaptatif en fonction du résultat de la validation.

De même, vous pouvez utiliser l’éditeur de règles pour inclure une méthode personnalisée pour valider le CAPTCHA dans un formulaire adaptatif.

### Ajout de services CAPTCHA personnalisés {#add-custom-captcha-service}

[!DNL Experience Manager Forms] fournit reCAPTCHA en tant que service CAPTCHA. Cependant, vous pouvez ajouter un service personnalisé à afficher dans la liste déroulante **[!UICONTROL Service CAPTCHA]**.

Voici un exemple de mise en œuvre de l’interface pour ajouter un service CAPTCHA supplémentaire à votre formulaire adaptatif :

```javascript
package com.adobe.aemds.guide.service;

import org.osgi.annotation.versioning.ConsumerType;

/**
 * An interface to provide captcha validation at server side in Adaptive Form
 * This interface can be used to provide custom implementation for different captcha services.
 */
@ConsumerType
public interface GuideCaptchaValidator {
    /**
     * This method should define the actual validation logic of the captcha
     * @param captchaPropertyNodePath path to the node with CAPTCHA configurations inside form container
     * @param userResponseToken  The user response token provided by the CAPTCHA from client-side
     *
     * @return  {@link GuideCaptchaValidationResult} validation result of the captcha
     */
     GuideCaptchaValidationResult validateCaptcha(String captchaPropertyNodePath, String userResponseToken);

    /**
     * Returns the name of the captcha validator. This should be unique among the different implementations
     * @return  name of the captcha validator
     */
     String getCaptchaValidatorName();
}
```

`captchaPropertyNodePath` fait référence au chemin des ressources du composant CAPTCHA dans le référentiel Sling. Utilisez cette propriété pour inclure des détails spécifiques au composant CAPTCHA. Par exemple, `captchaPropertyNodePath` contient des informations pour la configuration du cloud reCAPTCHA configurée sur le composant CAPTCHA. Les informations de configuration du cloud fournissent les paramètres **[!UICONTROL Clé du site]** et **[!UICONTROL Clé secrète]** pour la mise en œuvre du service reCAPTCHA.

`userResponseToken` fait référence au `g_recaptcha_response` qui est généré après la résolution d’un CAPTCHA dans un formulaire.

### Modifier le domaine de service reCAPTCHA {#reCAPTCHA-service-domain}

Le service reCAPTCHA utilise `https://www.recaptcha.net/` comme domaine par défaut. Vous pouvez modifier les paramètres pour définir `https://www.google.com/` ou tout nom de domaine personnalisé pour le chargement, le rendu et la validation du service reCAPTCHA.

Définissez la propriété **[!UICONTROL af.cloudservices.recaptcha.domain]** de la **[!UICONTROL configuration du formulaire adaptatif et du canal web de communication interactive]** pour spécifier `https://www.google.com/` ou tout autre nom de domaine personnalisé. Le fichier JSON suivant affiche un exemple :

```json
{
  "af.cloudservices.recaptcha.domain": "https://www.google.com/"
}
```

Pour définir les valeurs d’une configuration, [générez des configurations OSGi à l’aide du SDK AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=fr#generating-osgi-configurations-using-the-aem-sdk-quickstart) et [déployez la configuration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=fr#deployment-process) sur votre instance de Cloud Service.
