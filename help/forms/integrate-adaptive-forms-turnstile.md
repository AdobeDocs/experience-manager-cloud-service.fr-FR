---
title: Comment utiliser Turnstile dans un formulaire adaptatif AEM ?
description: Améliorez la sécurité des formulaires grâce au service Turnstile sans effort. Guide détaillé inclus.
topic-tags: Adaptive Forms, author
feature: Adaptive Forms, Foundation Components
hide: true
hidefromtoc: true
exl-id: 644c351b-a167-4d18-8b99-b7cae6be48d5
role: User, Developer
source-git-commit: d69d64a02c62b9a796188107cfe1ab7543b5a2be
workflow-type: tm+mt
source-wordcount: '956'
ht-degree: 16%

---


# Intégration de Turnstile CAPTCHA à Adaptive Forms

<span class="preview"> Cette fonctionnalité est disponible dans le cadre du Programme Adopteur Anticipé. Vous pouvez écrire à aem-forms-ea@adobe.com à partir de votre adresse e-mail officielle pour rejoindre le programme d’adoption précoce et demander l’accès à la fonctionnalité. </span>

CAPTCHA (Completely Automated Public Turing test to tell Computers and Humans Apart, Test public de Turing complètement automatisé ayant pour but de différencier les personnes humaines des ordinateurs) est un programme couramment utilisé dans les transactions en ligne pour différencier les personnes humaines des programmes automatisés ou des robots. Il présente un test et évalue la réponse de l’utilisateur ou de l’utilisatrice pour déterminer s’il s’agit d’une personne humaine ou d’un robot qui interagit avec le site. Cela empêche l’utilisateur ou l’utilisatrice de continuer si le test échoue et permet de sécuriser les transactions en ligne en empêchant les robots d’envoyer du spam ou des éléments malveillants.

AEM Forms as a Cloud Service prend en charge les solutions CAPTCHA suivantes :

* [Cloudflare Turnstile](#integrate-aem-forms-environment-with-turnstile-captcha)
* [reCAPTCHA de Google](/help/forms/captcha-adaptive-forms.md)
* [Captcha](/help/forms/integrate-adaptive-forms-hcaptcha.md)

## Intégration de l’environnement AEM Forms à Turnstile Captcha

Le captcha de Cloudflare est une mesure de sécurité visant à protéger les formulaires et les sites contre les robots automatisés, les attaques malveillantes, les spams et le trafic automatisé indésirable. Il affiche une case à cocher lors de l’envoi du formulaire pour vérifier qu’il est humain, avant de lui permettre d’envoyer le formulaire. AEM Forms as a Cloud Service prend en charge le captcha de Turnstile dans les composants principaux de Forms adaptatif.

<!-- ![Turnstile](assets/Turnstile-challenge.png)-->

### Conditions préalables pour intégrer l’environnement AEM Forms avec Turnstile Captcha {#prerequisite}

Pour configurer Turnstile pour les composants principaux AEM Forms, vous devez obtenir la [clé de site Turnstile et la clé secrète](https://developers.cloudflare.com/turnstile/get-started/) à partir du site Web Turnstile.

### Étapes de configuration de Turnstile pour AEM Forms{#steps-to-configure-turnstile}

1. Créez un conteneur de configuration sur votre environnement as a Cloud Service AEM Forms. Un conteneur de configuration contient les configurations cloud utilisées pour se connecter AEM aux services externes. Pour créer et configurer un conteneur de configuration afin de connecter votre environnement AEM Forms à Turnstile :
   1. Ouvrez votre instance AEM Forms as a Cloud Service.
   1. Accédez à **[!UICONTROL Outils > Général > Navigateur de configuration]**.
   1. Dans l’explorateur de configurations, vous pouvez sélectionner un dossier existant ou créer un dossier. Vous pouvez créer un dossier et activer l’option Configurations du cloud pour celui-ci ou activer l’option Configurations du cloud pour un dossier existant :

      * **Pour créer un dossier et activer l’option Configurations du cloud pour celui-ci** :
         1. Dans l’explorateur de configurations, cliquez sur **[!UICONTROL Créer]**.
         1. Dans la boîte de dialogue Créer une configuration, indiquez un nom et un titre, puis sélectionnez l’option **[!UICONTROL Configurations cloud]** .
         1. Cliquez sur **[!UICONTROL Créer]**.
      * Pour activer l’option Configurations du cloud pour un dossier existant :
         1. Dans l’explorateur de configurations, sélectionnez le dossier, puis **[!UICONTROL Propriétés]**.
         1. Dans la boîte de dialogue Propriétés de configuration, activez **[!UICONTROL Configurations cloud]**.
         1. Sélectionnez **[!UICONTROL Enregistrer et fermer]** pour enregistrer la configuration et fermer la boîte de dialogue.

1. Configurez le Cloud Service :
   1. Sur votre instance d’auteur AEM, accédez à ![tools-1](assets/tools-1.png) > **[!UICONTROL Cloud Service]** et sélectionnez **[!UICONTROL Turnstile]**.
      ![Turnstile dans ui](assets/turnstile-in-ui.png)
   1. Sélectionnez un conteneur de configuration, créé ou mis à jour, comme décrit dans la section précédente. Sélectionnez **[!UICONTROL Créer]**.
      ![Turnstile de configuration](assets/config-hcaptcha.png)
   1. Spécifiez **[!UICONTROL Widget Type]** comme type de widget géré, qui peut changer en fonction de la clé obtenue dans la condition préalable, **[!UICONTROL Title]**, **[!UICONTROL Name]**, **[!UICONTROL Site Key]** et **[!UICONTROL Secret Key]** for Turnstile service [obtenu dans la condition](#prerequisite). Sélectionnez **[!UICONTROL Créer]**.

      ![Configurez le Cloud Service pour connecter votre environnement AEM Forms à Turnstile](assets/config-turntstile.png)

>[!NOTE]
> Les utilisateurs ne doivent pas modifier l’URL de validation JavaScript côté client et l’URL de validation côté serveur, car ils sont déjà préremplis pour la validation de Turnstile.

Une fois le service de capture de Turnstile configuré, il peut être utilisé dans un formulaire adaptatif.

## Utiliser Turnstile dans un formulaire adaptatif{#using-turnstile-foundation-components}

1. Ouvrez votre instance AEM Forms as a Cloud Service.
1. Accédez à **[!UICONTROL Forms]** > **[!UICONTROL Forms and Documents]**.
1. Sélectionnez un formulaire adaptatif et sélectionnez **[!UICONTROL Propriétés]**. Pour l’option **[!UICONTROL Conteneur de configuration]**, sélectionnez le Conteneur de configuration contenant la configuration cloud qui connecte AEM Forms à Turnstile, puis sélectionnez **[!UICONTROL Enregistrer et fermer]**.

   Si vous ne disposez pas d’un tel conteneur de configuration, reportez-vous à la section [Connexion de votre environnement AEM Forms à Turnstile](#connect-your-forms-environment-with-turnstile-service) pour savoir comment créer un conteneur de configuration.

   ![Sélectionner Conteneur de configuration](/help/forms/assets/captcha-properties.png)

1. Sélectionnez un formulaire adaptatif et choisissez **[!UICONTROL Modifier]**. Le formulaire adaptatif s’ouvre dans l’éditeur de Forms adaptatif.
1. À partir du navigateur de composant, faites glisser et déposez le composant **[!UICONTROL Captcha]** sur le formulaire adaptatif.
1. Sélectionnez le composant **[!UICONTROL Captcha]** et cliquez sur l&#39;icône de propriétés ![Icône Propriétés](assets/configure-icon.svg) . Elle ouvre la boîte de dialogue des propriétés.

   ![Paramètres](assets/turnstile-setting-v1.png)

   Spécifiez les propriétés suivantes :

   * **[!UICONTROL Titre] :** Spécifiez le titre de votre composant Captcha. Vous pouvez identifier facilement un composant de formulaire avec son nom unique dans le formulaire et dans l’éditeur de règles.
   * **[!UICONTROL Message de validation] :** fournissez un message de validation pour valider Captcha lors de l’envoi du formulaire.
   * **[!UICONTROL Valider Captcha] :** Vous pouvez sélectionner l’une des options pour valider Captcha :
      * Lors de l’envoi du formulaire
      * Sur une action utilisateur.
   * **[!UICONTROL Service Captcha] :** Sélectionnez votre service Captcha, ici vous sélectionnez Cloudfare Service Captcha Turnstile.
   * **[!UICONTROL Configuration de Captcha] :** Sélectionnez une configuration de cloud configurée pour Turnstile. par exemple, ici, vous sélectionnez la **clé gérée**.
     >[!NOTE]
     >Vous pouvez avoir plusieurs configurations de cloud dans votre environnement à des fins similaires. Choisissez donc le service avec soin. Si aucun service n’est répertorié, voir [Connexion de votre environnement AEM Forms à Turnstile](#connect-your-forms-environment-with-turnstile-service) pour savoir comment créer un Cloud Service qui connecte votre environnement AEM Forms au service Turnstile.

   * **Message d’erreur :** indiquez le message d’erreur à afficher à l’utilisateur lorsque l’envoi du Captcha échoue.
   * **Taille du captcha :** Vous sélectionnez la taille d’affichage de la boîte de dialogue de défi Turnstile. Utilisez l’option **[!UICONTROL Compact]** pour afficher une petite taille et l’option **[!UICONTROL Normale]** pour afficher une boîte de dialogue de défi de Turnstile de taille relativement importante.


     >[!NOTE]
     >Cela s’applique au type de widget Géré et Non interactif. Si le type de widget est invisible, la propriété size n’est pas requise et elle est désactivée.

1. Sélectionnez **[!UICONTROL Terminé]**.

Désormais, seuls les formulaires légitimes dans lesquels l’utilisateur parvient à résoudre le problème posé par le service Turnstile sont autorisés pour l’envoi du formulaire.

![Défi Turnstile](assets/turnstile-challenge.png)

## Questions fréquentes

* **Q : Puis-je utiliser plusieurs composants Captcha dans un formulaire adaptatif ?**
* **Réponse :** L’utilisation de plusieurs composants Captcha dans un formulaire adaptatif n’est pas prise en charge. En outre, il n’est pas recommandé d’utiliser un composant Captcha dans un fragment ou un panneau marqué pour le chargement différé.

## Voir également {#see-also}

{{see-also}}
