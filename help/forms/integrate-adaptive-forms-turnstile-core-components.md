---
title: Comment utiliser Turnstile dans un AEM des composants principaux de formulaire adaptatif ?
description: Améliorez la sécurité des formulaires grâce au service Turnstile sans effort. Guide pas à pas à l'intérieur !
topic-tags: Adaptive Forms, author
feature: Adaptive Forms, Core Components
hide: true
hidefromtoc: true
source-git-commit: d2c6514eb1f38b06dfa58daa03b781920b8928f6
workflow-type: tm+mt
source-wordcount: '891'
ht-degree: 13%

---

# Connexion de votre environnement AEM Forms à Turnstile {#connect-your-forms-environment-with-turnstile-service}

<span class="preview"> Cette fonctionnalité est inscrite dans le Programme des Adopteurs Anticipés. Vous pouvez écrire à aem-forms-ea@adobe.com à partir de votre ID de courrier électronique officiel pour rejoindre le programme des premiers adopteurs et demander l’accès à la fonctionnalité. </span>

CAPTCHA (Completely Automated Public Turing test to tell Computers and Humans Apart, Test public de Turing complètement automatisé ayant pour but de différencier les personnes humaines des ordinateurs) est un programme couramment utilisé dans les transactions en ligne pour différencier les personnes humaines des programmes automatisés ou des robots. Il présente un test et évalue la réponse de l’utilisateur ou de l’utilisatrice pour déterminer s’il s’agit d’une personne humaine ou d’un robot qui interagit avec le site. Cela empêche l’utilisateur ou l’utilisatrice de continuer si le test échoue et permet de sécuriser les transactions en ligne en empêchant les robots d’envoyer du spam ou des éléments malveillants.

AEM Forms as a Cloud Service prend en charge les solutions CAPTCHA suivantes :


* [Cloudflare Turnstile](#integrate-aem-forms-environment-with-turnstile-captcha)
* [reCAPTCHA de Google](/help/forms/captcha-adaptive-forms-core-components.md)
* [Captcha](/help/forms/integrate-adaptive-forms-hcaptcha-core-components.md)



<!-- ![Turnstile](assets/Turnstile-challenge.png)-->

## Intégration de l’environnement AEM Forms à Turnstile Captcha

Le captcha de Cloudflare est une mesure de sécurité visant à protéger les formulaires et les sites contre les robots automatisés, les attaques malveillantes, les spams et le trafic automatisé indésirable. Il affiche une case à cocher lors de l’envoi du formulaire pour vérifier qu’il est humain, avant de lui permettre d’envoyer le formulaire. AEM Forms as a Cloud Service prend en charge le captcha de Turnstile dans les composants principaux de Forms adaptatif.

### Conditions préalables pour intégrer l’environnement AEM Forms avec Turnstile Captcha {#prerequisite}

Pour configurer Turnstile pour les composants principaux AEM Forms, vous devez obtenir [Installation clé en main et clé secrète](https://developers.cloudflare.com/turnstile/get-started/) à partir du site web de Turnstile.

### Configuration de Turnstile {#steps-to-configure-hcaptcha}

Pour intégrer AEM Forms avec le service Turnstile, procédez comme suit :

1. Créez un conteneur de configuration sur votre environnement as a Cloud Service AEM Forms. Un conteneur de configuration contient les configurations cloud utilisées pour se connecter AEM aux services externes. Pour créer et configurer un conteneur de configuration afin de connecter votre environnement AEM Forms à Turnstile :
   1. Ouvrez votre instance AEM Forms as a Cloud Service.
   1. Accédez à **[!UICONTROL Outils > Général > Navigateur de configuration]**.
   1. Dans l’explorateur de configurations, vous pouvez sélectionner un dossier existant ou créer un dossier. Vous pouvez créer un dossier et activer l’option Configurations du cloud pour celui-ci ou Activer l’option Configurations du cloud pour un dossier existant :

      * Pour créer un dossier et activer l’option Configurations du cloud :
         1. Dans le navigateur de configuration, cliquez sur **[!UICONTROL Créer]**.
         1. Dans la boîte de dialogue Créer une configuration, indiquez un nom et un titre, puis sélectionnez le paramètre **[!UICONTROL Configurations du cloud]** .
         1. Cliquez sur **[!UICONTROL Créer]**.
      * Pour activer l’option Configurations du cloud pour un dossier existant :
         1. Dans l’explorateur de configurations, sélectionnez le dossier, puis sélectionnez **[!UICONTROL Propriétés]**.
         1. Dans la boîte de dialogue Propriétés de configuration, activez **[!UICONTROL Configurations cloud]**.
         1. Sélectionnez **[!UICONTROL Enregistrer et fermer]** pour enregistrer la configuration et fermer la boîte de dialogue.

1. Configurez le Cloud Service :
   1. Sur votre instance d’auteur AEM, accédez à ![tools-1](assets/tools-1.png) > **[!UICONTROL Cloud Service]** et sélectionnez **[!UICONTROL Turnstile]**.
      ![Turnstile dans l’interface utilisateur](assets/turnstile-in-ui.png)
   1. Sélectionnez un conteneur de configuration, créé ou mis à jour, comme décrit dans la section précédente. Sélectionnez **[!UICONTROL Créer]**.
      ![Installation de configuration](assets/config-hcaptcha.png)
   1. Spécifier **[!UICONTROL Type de widget]** en tant que géré, **[!UICONTROL Titre]**, **[!UICONTROL Nom]**, **[!UICONTROL Clé du site]**, et **[!UICONTROL Clé secrète]** pour le service Turnstile [obtenu dans la condition préalable](#prerequisite).
   1. Cliquez sur **[!UICONTROL Créer]**.

      ![Configuration du Cloud Service pour connecter votre environnement AEM Forms à Turnstile](assets/config-turntstile.png)

   >[!NOTE]
   > Les utilisateurs n’ont pas besoin de modifier l’URL de validation JavaScript côté client et l’URL de validation côté serveur, car ils sont déjà préremplis pour la validation Turnstile.

   Une fois le service de captcha Turnstile configuré, il peut être utilisé dans un [Formulaire adaptatif basé sur les composants principaux](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/adaptive-forms/introduction).

## Utiliser le tuteur dans un formulaire adaptatif {#using-turnstile-core-components}

1. Ouvrez votre instance AEM Forms as a Cloud Service.
1. Accédez à **[!UICONTROL Forms]** > **[!UICONTROL Forms et documents]**.
1. Sélectionnez un formulaire adaptatif et choisissez **[!UICONTROL Propriétés]**. Pour le **[!UICONTROL Conteneur de configuration]** Sélectionnez l’option Conteneur de configuration contenant la configuration cloud qui connecte AEM Forms à Turnstile et sélectionnez **[!UICONTROL Enregistrer et fermer]**.

   Si vous ne disposez pas d’un tel conteneur de configuration, reportez-vous à la section . [Connexion de votre environnement AEM Forms à Turnstile](#connect-your-forms-environment-with-turnstile-service) pour savoir comment créer un conteneur de configuration.

   ![Sélectionner le conteneur de configuration](/help/forms/assets/captcha-properties.png)

1. Sélectionnez un formulaire adaptatif et choisissez **[!UICONTROL Modifier]**. Le formulaire adaptatif s’ouvre dans l’éditeur de Forms adaptatif.
1. À partir de l’explorateur de composants, effectuez un glisser-déposer ou ajoutez le **[!UICONTROL Turnstile de formulaire adaptatif]** sur le formulaire adaptatif.
1. Sélectionnez la variable **[!UICONTROL Turnstile de formulaire adaptatif]** composants et propriétés de clic ![Icône Propriétés](assets/configure-icon.svg) Icône Elle ouvre la boîte de dialogue des propriétés. Spécifiez les propriétés suivantes :

   ![Turnstile v2](assets/turnstile-settings-v2.png)

   * **[!UICONTROL Nom]:** Indiquez le nom de votre composant Captcha. Vous pouvez identifier facilement un composant de formulaire avec son nom unique dans le formulaire et dans l’éditeur de règles.
   * **[!UICONTROL Titre]:** Indiquez le titre de votre composant Captcha.
   * **[!UICONTROL Paramètres de configuration]:** Sélectionnez une configuration de cloud configurée pour Turnstile.
   * **[!UICONTROL Message de validation]:** Fournissez un message de validation pour valider Captcha lors de l’envoi du formulaire.
   * **[!UICONTROL Message de validation de script]**: cette option permet de saisir un message à afficher en cas d’échec de la validation du script.
     >[!NOTE]
     >Vous pouvez avoir plusieurs configurations de cloud dans votre environnement à des fins similaires. Choisissez donc le service avec soin. Si aucun service n’est répertorié, voir [Connexion de votre environnement AEM Forms à Turnstile](#connect-your-forms-environment-with-turnstile-service) pour savoir comment créer un Cloud Service qui connecte votre environnement AEM Forms au service Turnstile.
   * **Message d’erreur :** Fournissez le message d’erreur à afficher à l’utilisateur en cas d’échec de l’envoi du Captcha.

1. Sélectionnez **[!UICONTROL Terminé]**.


Désormais, seuls les formulaires légitimes dans lesquels l’utilisateur parvient à résoudre le problème posé par le service Turnstile sont autorisés pour l’envoi du formulaire.

![Défi de Turnstile](assets/turnstile-challenge.png)


## Questions fréquentes

* **Q : Puis-je utiliser plusieurs composants Captcha dans un formulaire adaptatif ?**
* **Réponse :** L’utilisation de plusieurs composants Captcha dans un formulaire adaptatif n’est pas prise en charge. En outre, il n’est pas recommandé d’utiliser un composant Captcha dans un fragment ou un panneau marqué pour le chargement différé.

## Voir également {#see-also}

{{see-also}}
