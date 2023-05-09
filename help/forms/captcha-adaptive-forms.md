---
title: Utilisation de CAPTCHA dans les formulaires adaptatifs
seo-title: Using CAPTCHA in Adaptive Forms
description: Découvrez comment configurer le service AEM CAPTCHA ou Google reCAPTCHA dans les formulaires adaptatifs.
seo-description: Learn how to configure AEM CAPTCHA or Google reCAPTCHA service in Adaptive Forms.
uuid: 0e11e98a-12ac-484c-b77f-88ebdf0f40e5
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: adaptive_forms, author
discoiquuid: 4c53dfc0-25ca-419d-abfe-cf31fc6ebf61
docset: aem65
exl-id: 3fdbe5a3-5c3c-474d-b701-e0182da4191a
source-git-commit: 0c303439c879605f1ab0927cf79b132dbb448af5
workflow-type: tm+mt
source-wordcount: '1415'
ht-degree: 88%

---

# Utiliser CAPTCHA dans les formulaires adaptatifs {#using-captcha-in-adaptive-forms}

CAPTCHA (Completely Automated Public Turing test to say Computers and Humans apart) est un programme couramment utilisé dans les transactions en ligne pour distinguer les humains des programmes ou robots automatisés. Il pose un problème et évalue la réponse de l’utilisateur pour déterminer s’il s’agit d’un humain ou d’un robot interagissant avec le site. Elle empêche l’utilisateur de procéder si le test échoue et permet de sécuriser les transactions en ligne en empêchant les robots de publier du spam ou des fins malveillantes.

[!DNL AEM Forms] prend en charge CAPTCHA dans les formulaires adaptatifs. Vous pouvez utiliser le service reCAPTCHA de Google pour implémenter CAPTCHA.

>[!NOTE]
>
>* [!DNL AEM Forms] prend en charge uniquement reCaptcha v2. Toute autre version n’est pas prise en charge.
>* Dans les formulaires adaptatifs, CAPTCHA n’est pas pris en charge dans le mode hors ligne sur l’application [!DNL AEM Forms].
>


## Configuration du service ReCAPTCHA de Google {#google-recaptcha}

Les auteurs de formulaires peuvent utiliser le service reCAPTCHA de Google pour mettre en place CAPTCHA dans les formulaires adaptatifs. Il offre des fonctionnalités CAPTCHA avancées pour protéger votre site. Pour plus d’informations sur le fonctionnement de reCAPTCHA, voir [Google reCAPTCHA](https://developers.google.com/recaptcha/).

![Recaptcha](assets/recaptcha_new.png)

Pour implémenter le service reCAPTCHA dans [!DNL AEM Forms] :

1. Obtenir [paire de clés API reCAPTCHA](https://www.google.com/recaptcha/admin) de Google. Il comprend une clé et un secret de site.
1. Créez un conteneur de configuration pour les services cloud.

   1. Accédez à **[!UICONTROL Outils > Général > Navigateur de configuration]**.
      * Pour plus d’informations, consultez la documentation relative au [Navigateur de configuration](https://experienceleague.adobe.com/docs/experience-manager-65/administering/introduction/configurations.html?lang=fr#introduction).
   1. Procédez comme suit pour activer le dossier global pour les configurations cloud ou ignorez cette étape pour créer et configurer un autre dossier pour les configurations de service cloud.

      1. Dans le navigateur de configuration, sélectionnez le dossier **[!UICONTROL global]** et appuyez sur **[!UICONTROL Propriétés]**.

      1. Dans la boîte de dialogue Propriétés de configuration, activez **[!UICONTROL Configurations cloud]**.
      1. Appuyez sur **[!UICONTROL Enregistrer et fermer]** pour enregistrer la configuration et fermer la boîte de dialogue.
   1. Dans le navigateur de configuration, appuyez sur **[!UICONTROL Créer]**.
   1. Dans la boîte de dialogue Créer une configuration, indiquez un titre pour le dossier et activez **[!UICONTROL Configurations cloud]**.
   1. Appuyez sur **[!UICONTROL Créer]** pour créer le dossier activé pour les configurations de service cloud.


1. Configurez le service cloud pour reCAPTCHA.

   1. Sur votre instance d’auteur Experience Manager, accédez à ![tools-1](assets/tools-1.png) > **[!UICONTROL Cloud Services]**.
   1. Appuyer **[!UICONTROL reCAPTCHA]**. La page Configurations s’ouvre. Sélectionnez le conteneur de configuration créé à l’étape précédente et appuyez sur **[!UICONTROL Créer]**.
   1. Indiquez le nom, la clé de site et la clé secrète pour le service reCAPTCHA, puis appuyez sur **[!UICONTROL Créer]** pour créer la configuration du service cloud.
   1. Dans cette boîte de dialogue, spécifiez le site et les clés de site et secrète obtenues à l’étape 1. Appuyez sur **[!UICONTROL Enregistrer les paramètres]** puis sur **[!UICONTROL OK]** pour terminer la configuration.

   Une fois que le service reCAPTCHA est configuré, il peut être utilisé dans les formulaires adaptatifs. Pour plus d’informations, voir [Utilisation de CAPTCHA dans les formulaires adaptatifs](#using-captcha).

## Utiliser CAPTCHA dans les formulaires adaptatifs  {#using-captcha}

Pour utiliser CAPTCHA dans les formulaires adaptatifs :

1. Ouvrez un formulaire adaptatif en mode d’édition.

   >[!NOTE]
   >
   >Assurez-vous que le conteneur de configurations sélectionné lors de la création du formulaire adaptatif contient le service cloud reCAPTCHA. Vous pouvez également modifier les propriétés de formulaire adaptatif pour modifier le conteneur de configurations associé au formulaire.

1. À partir du navigateur de composant, faites glisser et déposez le composant **[!UICONTROL Captcha]** sur le formulaire adaptatif.

   >[!NOTE]
   >
   >L’utilisation de plusieurs composants Captcha dans un formulaire adaptatif n’est pas prise en charge. En outre, il n’est pas recommandé d’utiliser CAPTCHA dans un panneau marqué pour le chargement différé ou dans un fragment.

   >[!NOTE]
   >
   >Captcha est sensible au temps et arrive à expiration dans une minute. Par conséquent, il est recommandé de placer le composant Captcha juste avant le bouton Envoyer dans le formulaire adaptatif.

1. Sélectionnez le composant Captcha que vous avez ajouté et appuyez sur ![cmppr](assets/configure-icon.svg) pour modifier ses propriétés.
1. Indiquez un titre pour le widget CAPTCHA. La valeur par défaut est **[!UICONTROL Captcha]**. Sélectionnez **[!UICONTROL Masquer le titre]** si vous ne voulez pas que le titre apparaisse.
1. Dans le menu déroulant **[!UICONTROL Service Captcha]**, sélectionnez **[!UICONTROL reCaptcha]** pour activer le service reCAPTCHA si vous l’avez configuré comme décrit dans [Service ReCAPTCHA de Google](#google-recaptcha). Sélectionnez une configuration dans la liste déroulante Paramètres.
1. Sélectionnez le type **[!UICONTROL Normal]** ou **[!UICONTROL Compact]** pour le widget reCAPTCHA. Vous pouvez également sélectionner l’option **[!UICONTROL Invisible]** pour ne montrer le test CAPTCHA que dans le cas d’une activité suspecte. Le badge protégé par reCAPTCHA, affiché ci-dessous, s’affiche sur les formulaires protégés.

   ![Badge protégé par reCAPTCHA de Google](assets/google-recaptcha-v2.png)

   >[!NOTE]
   >
   >Ne sélectionnez pas **[!UICONTROL Par défaut]** dans le menu déroulant Service Captcha puisque le service par défaut Experience Manager CAPTCHA est obsolète.

1. Enregistrez les propriétés.

Le service reCAPTCHA est activé sur le formulaire adaptatif. Vous pouvez prévisualiser le formulaire et voir le fonctionnement de CAPTCHA.

### Affichage ou masquage du composant CAPTCHA en fonction de règles {#show-hide-captcha}

Vous pouvez choisir d’afficher ou de masquer le composant CAPTCHA en fonction des règles que vous appliquez à un composant d’un formulaire adaptatif. Appuyez sur le composant, sélectionnez ![modifier les règles](assets/edit-rules-icon.svg), puis appuyez sur **[!UICONTROL Créer]** pour créer une règle. Pour plus d’informations sur la création de règles, voir la section [Éditeur de règles](rule-editor.md).

Par exemple, le composant CAPTCHA ne doit s’afficher dans un formulaire adaptatif que si la valeur du champ Valeur monétaire du formulaire est supérieure à 25 000.

Appuyez sur le champ **[!UICONTROL Valeur monétaire]** dans le formulaire et créez les règles suivantes :

![Afficher ou masquer des règles](assets/rules-show-hide-captcha.png)

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

### Modifier le domaine de service reCAPTCHA {#recaptcha-service-domain}

Le service reCAPTCHA utilise `https://www.recaptcha.net/` comme domaine par défaut. Vous pouvez modifier les paramètres pour définir `https://www.google.com/` ou tout nom de domaine personnalisé pour le chargement, le rendu et la validation du service reCAPTCHA.

Définissez la propriété **[!UICONTROL af.cloudservices.recaptcha.domain]** de la **[!UICONTROL configuration du formulaire adaptatif et du canal web de communication interactive]** pour spécifier `https://www.google.com/` ou tout autre nom de domaine personnalisé. Le fichier JSON suivant affiche un exemple :

```json
{
  "af.cloudservices.recaptcha.domain": "https://www.google.com/"
}
```

Pour définir les valeurs d’une configuration, [générez des configurations OSGi à l’aide du SDK AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=fr#generating-osgi-configurations-using-the-aem-sdk-quickstart) et [déployez la configuration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=fr#deployment-process) sur votre instance de Cloud Service.
