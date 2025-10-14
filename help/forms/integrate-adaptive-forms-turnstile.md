---
title: Comment utiliser Turnstile dans un formulaire adaptatif AEM ?
description: Améliorez la sécurité des formulaires avec le service Turnstile sans effort. Guide détaillé inclus.
topic-tags: Adaptive Forms, author
feature: Adaptive Forms, Foundation Components
role: User, Developer
exl-id: 644c351b-a167-4d18-8b99-b7cae6be48d5
source-git-commit: 914139a6340f15ee77024793bf42fa30c913931e
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 16%

---

# Intégrer le CAPTCHA Turnstile au Forms adaptatif

<span class="preview"> Cette fonctionnalité se trouve dans le programme des utilisateurs et utilisatrices précoces. Vous pouvez écrire à aem-forms-ea@adobe.com à partir de votre identifiant e-mail officiel pour rejoindre le programme d’adoption précoce et demander l’accès à la fonctionnalité. </span>

CAPTCHA (Completely Automated Public Turing test to tell Computers and Humans Apart, Test public de Turing complètement automatisé ayant pour but de différencier les personnes humaines des ordinateurs) est un programme couramment utilisé dans les transactions en ligne pour différencier les personnes humaines des programmes automatisés ou des robots. Il présente un test et évalue la réponse de l’utilisateur ou de l’utilisatrice pour déterminer s’il s’agit d’une personne humaine ou d’un robot qui interagit avec le site. Cela empêche l’utilisateur ou l’utilisatrice de continuer si le test échoue et permet de sécuriser les transactions en ligne en empêchant les robots d’envoyer du spam ou des éléments malveillants.

AEM Forms as a Cloud Service prend en charge les solutions CAPTCHA suivantes :

* [Tourniquet Cloudflare](#integrate-aem-forms-environment-with-turnstile-captcha)
* [reCAPTCHA de Google](/help/forms/captcha-adaptive-forms.md)
* [hCaptcha](/help/forms/integrate-adaptive-forms-hcaptcha.md)

## Intégration de l’environnement AEM Forms à Captcha Turnstile

Le Captcha Turnstile de Cloudflare est une mesure de sécurité qui vise à protéger les formulaires et les sites contre les robots automatisés, les attaques malveillantes, les spams et le trafic automatisé indésirable. Elle présente une case à cocher lors de l’envoi du formulaire pour vérifier qu’ils sont humains, avant de leur permettre d’envoyer le formulaire. AEM Forms as a Cloud Service prend en charge le captcha de tourniquet dans le Forms adaptatif.

<!-- ![Turnstile](assets/Turnstile-challenge.png)-->

### Conditions préalables à l’intégration de l’environnement AEM Forms avec le Captcha Turnstile {#prerequisite}

Pour configurer Turnstile pour AEM Forms, vous devez obtenir la [clé de site Turnstile et clé secrète](https://developers.cloudflare.com/turnstile/get-started/) à partir du site Web Turnstile.

### Étapes de configuration de Turnstile pour AEM Forms{#steps-to-configure-turnstile}

1. Créez un conteneur de configuration sur votre environnement AEM Forms as a Cloud Service. Un conteneur de configurations contient les configurations cloud utilisées pour connecter AEM à des services externes. Pour créer et configurer un conteneur de configuration afin de connecter votre environnement AEM Forms à Turnstile :
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
   1. Sur votre instance d’auteur AEM, accédez à ![tools-1](assets/tools-1.png) > **[!UICONTROL Services cloud]** et sélectionnez **[!UICONTROL Tourniquet]**.

      ![Tourniquet dans l’interface utilisateur](assets/turnstile-in-ui.png)
   1. Sélectionnez un conteneur de configuration, créé ou mis à jour, comme décrit dans la section précédente. Sélectionnez **[!UICONTROL Créer]**.

      ![Tourniquet de configuration](assets/config-hcaptcha.png)
   1. Spécifiez **[!UICONTROL Type de widget]** comme géré. Le type de widget peut changer en fonction de la clé obtenue dans la condition préalable **[!UICONTROL Titre]**, **[!UICONTROL Nom]**, **[!UICONTROL Clé du site]** et **[!UICONTROL Clé secrète]** pour le service Tourniquet [&#x200B; obtenu dans la condition préalable &#x200B;](#prerequisite). Sélectionnez **[!UICONTROL Créer]**.

      ![Configurez le Cloud Service pour connecter votre environnement AEM Forms à Turnstile](assets/config-turntstile.png)

>[!NOTE]
> Les utilisateurs n’ont pas besoin de modifier les URL de validation de JavaScript côté client et côté serveur, car elles sont déjà préremplies pour la validation Turnstile.

Une fois le service Captcha de tourniquet configuré, il peut être utilisé dans un formulaire adaptatif.

## Utiliser Turnstile dans un formulaire adaptatif{#using-turnstile-foundation-components}

1. Ouvrez votre instance AEM Forms as a Cloud Service.
1. Accédez à **[!UICONTROL Forms]** > **[!UICONTROL Forms et documents]**.
1. Sélectionnez un formulaire adaptatif et sélectionnez **[!UICONTROL Propriétés]**. Pour l’option **[!UICONTROL Conteneur de configurations]**, sélectionnez le Conteneur de configurations contenant la configuration cloud qui connecte AEM Forms à Turnstile, puis sélectionnez **[!UICONTROL Enregistrer et fermer]**.

   Si vous ne disposez pas d’un tel conteneur de configuration, consultez la section [Connecter votre environnement AEM Forms à Turnstile](#connect-your-forms-environment-with-turnstile-service) pour savoir comment créer un conteneur de configuration.

   ![Sélectionner le conteneur de configuration](/help/forms/assets/captcha-properties.png)

1. Sélectionnez un formulaire adaptatif, puis sélectionnez **[!UICONTROL Modifier]**. Le formulaire adaptatif s’ouvre dans l’éditeur de Forms adaptatif.
1. À partir du navigateur de composant, faites glisser et déposez le composant **[!UICONTROL Captcha]** sur le formulaire adaptatif.
1. Sélectionnez le composant **[!UICONTROL Captcha]** et cliquez sur l’icône Propriétés ![Icône Propriétés](assets/configure-icon.svg). Cela ouvre la boîte de dialogue des propriétés.

   ![Paramètres](assets/turnstile-setting-v1.png)

   Spécifiez les propriétés suivantes :

   * **[!UICONTROL Titre] :** indiquez le titre de votre composant Captcha ; vous pouvez identifier facilement un composant de formulaire en lui attribuant un nom unique dans le formulaire et dans l’éditeur de règles.
   * **[!UICONTROL Message de validation] :** fournissez un message de validation pour valider le Captcha lors de l’envoi du formulaire.
   * **[!UICONTROL Valider le captcha] :** vous pouvez sélectionner l’une des options suivantes pour valider le captcha :
      * Lors de l’envoi du formulaire
      * Sur une action utilisateur.
   * **[!UICONTROL Service Captcha] :** sélectionnez votre service Captcha, ici vous sélectionnez le service Captcha Turnstile de Cloudfare.
   * **[!UICONTROL Configuration Captcha] :** sélectionnez une configuration cloud configurée pour Turnstile. par exemple, vous sélectionnez ici la **clé gérée**.

     >[!NOTE]
     >
     > Plusieurs configurations cloud peuvent être définies dans votre environnement dans un but similaire. Donc, choisissez le service avec soin. Si aucun service n’est répertorié, voir [Connecter votre environnement AEM Forms à Turnstile](#connect-your-forms-environment-with-turnstile-service) pour savoir comment créer un Cloud Service qui connecte votre environnement AEM Forms à ce service.

   * **Message d’erreur :** le message d’erreur à afficher à l’utilisateur ou à l’utilisatrice en cas d’échec de l’envoi du Captcha.
   * **Taille de Captcha :** sélectionnez la taille d’affichage de la boîte de dialogue de vérification du tourniquet. Utilisez l’option **[!UICONTROL Compact]** pour afficher une boîte de dialogue de vérification de petite taille et l’option **[!UICONTROL Normal]** pour afficher une boîte de dialogue de vérification de tourniquet de taille relativement grande.


     >[!NOTE]
     >Cela s’applique aux widgets de type Géré et Non interactif. Si le type de widget est invisible, la propriété size n’est pas obligatoire et elle est désactivée.

1. Sélectionnez **[!UICONTROL Terminé]**.

Désormais, seuls les formulaires légitimes, dans lesquels le remplisseur de formulaire résout avec succès le problème posé par le service Turnstile, sont autorisés pour l’envoi du formulaire.

![Défi du tourniquet](assets/turnstile-challenge.png)

## Questions fréquentes

* **Q : Puis-je utiliser plusieurs composants Captcha dans un formulaire adaptatif ?**
* **Réponse :** l’utilisation de plusieurs composants Captcha dans un formulaire adaptatif n’est pas prise en charge. En outre, il n’est pas recommandé d’utiliser un composant Captcha dans un fragment ou un panneau marqué pour le chargement différé.

## Voir également {#see-also}

{{see-also}}
