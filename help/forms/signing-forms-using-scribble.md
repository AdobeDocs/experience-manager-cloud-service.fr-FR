---
title: Comment appliquer des signatures électroniques à un formulaire à l’aide de signatures tactiles ?
description: Découvrez comment appliquer des signatures électroniques à un formulaire à l’aide de signatures tactiles.
uuid: ffeba886-9b24-4ed1-95c0-e19356ff2f23
products: SG_EXPERIENCEMANAGER/FORMS
topic-tags: author
feature: Adaptive Forms, Foundation Components
exl-id: dc89ecb1-2d9e-4d1d-b85b-af90c550e7d8
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 84%

---

# Signer électroniquement un formulaire à l’aide de signatures tactiles{#apply-electronic-signatures-to-a-form-using-deprecated-scribble-signatures}

<span class="preview"> Adobe recommande d’utiliser les [composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=fr) de capture de données modernes et extensibles pour [créer de nouveaux formulaires adaptatifs](/help/forms/creating-adaptive-form-core-components.md) ou [ajouter des formulaires adaptatifs à des pages AEM Sites](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Ces composants représentent une avancée significative dans la création de formulaires adaptatifs, ce qui garantit des expériences utilisateur impressionnantes. Cet article décrit l’ancienne approche de la création de formulaires adaptatifs à l’aide de composants de base. </span>

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/signing-forms-using-scribble.html) |
| AEM as a Cloud Service | Cet article |


Vous pouvez utiliser les composants **Signature tactile** et **Étape de signature** pour tracer la signature (saisie tactile) sur un formulaire adaptatif. Le composant Étape de signature affiche une version PDF du formulaire adaptatif. Pour utiliser le composant Étape de signature, l’option Document d’enregistrement doit être activée ou vous devez disposer de formulaires adaptatifs basés sur un modèle de formulaire.

![Boîte de dialogue de signature tactile](assets/scribble-signature.png)

## Diverses options disponibles dans la fenêtre de signature.

* **A :** cliquez sur l’icône **Pinceau** pour tracer votre signature sur la zone de travail.
* **B :** cliquez sur l’icône **Effacer** pour effacer la signature sur la zone de travail.
* **C :** cliquez sur l’icône **Géolocalisation** pour ajouter une géolocalisation avec la signature.
* **D :** cliquez sur l’icône **Clavier** pour saisir votre nom sur la zone de travail.

Une fois que vous avez sélectionné l’icône Terminé ![aem_forms_save](assets/aem_forms_save.png) dans la fenêtre de signature tactile, vous ne pouvez pas modifier la signature. Si vous souhaitez modifier la signature, vous devez ignorer la signature actuelle et la signer à nouveau à l’aide de l’option Pinceau/Clavier ci-dessus.

Vous pouvez sélectionner l’icône **Configurer** ![Configurer l’icône](assets/configure.png) pour définir les proportions du canevas de signature tactile.
* Lorsque le rapport d’aspect de la zone de travail de signature tactile est inférieur à 1, les informations de géolocalisation sont ajoutées au bas de la zone de travail de signature tactile.


* Lorsque le rapport d’aspect de la zone de travail de signature tactile est supérieur à 1, les informations de géolocalisation sont ajoutées au côté droit de la zone de travail de signature tactile.


![Bas de la signature tactile](assets/scribble-signature-aspectratio.PNG)



>[!NOTE]
>
>Les signatures sont toujours enregistrées au format PNG.
>

## Configuration d’un formulaire adaptatif pour utiliser la signature tactile {#configure-an-adaptive-form-to-use-scribble-signature}

1. Créez une option Document d’enregistrement activée ou un formulaire adaptatif basé sur modèle de formulaire. Pour obtenir des informations détaillées, voir [Création d’un formulaire adaptatif](creating-adaptive-form.md).
1. Faites glisser le composant **Signature tactile** depuis le navigateur de composant et déposez-le dans le formulaire adaptatif.
1. Sélectionnez l’icône **Configurer** ![configurer](assets/configure.png). Vous ouvrez ainsi le navigateur de propriétés qui affiche les propriétés du composant Signature tactile. Configurez les propriétés du composant Signature tactile.
1. Faites glisser le composant Étape de signature depuis le navigateur de composant et déposez-le dans le formulaire adaptatif.

   >[!NOTE]
   >
   >Le composant Étape de signature prend toute la largeur disponible pour le formulaire. Il est recommandé de ne pas avoir d’autre composant sur la section contenant le composant Étape de signature. 

1. Dans le navigateur de contenu, sélectionnez **Form Container**, puis l’icône **Configurer** ![ ](assets/configure.png) . L’explorateur de propriétés s’ouvre et affiche les propriétés du conteneur de formulaires adaptatifs. Accédez à **Conteneur de formulaires adaptatifs** > **Signature électronique** et désélectionnez l’option **Activer Adobe Sign**. Sélectionnez l’icône Terminé ![aem_forms_save](assets/aem_forms_save.png) pour enregistrer les modifications.

   >[!NOTE]
   >
   >Lorsque vous ajoutez un composant Étape de signature à un formulaire adaptatif, l’option Activer Adobe Sign est sélectionnée automatiquement.

1. Sélectionnez l’icône **Configurer**![Configurer](assets/configure.png). Elle ouvre l’explorateur de propriétés et affiche les propriétés Étape de signature. Configurez les propriétés suivantes :

   * **Nom de l’élément** : spécifiez le nom du composant.

   * **Titre :** indiquez le titre unique du composant.
   * **Message du modèle :** indiquez le message à afficher lorsque la signature PDF est chargée. Les services Adobe Sign mettent un certain temps à préparer et charger la signature PDF.
   * **Service de signature :** sélectionnez l’option **Signature tactile**.

   * **Classe CSS** : spécifiez la classe CSS de la bibliothèque client, le cas échéant. Adobe recommande d’utiliser [themes](themes.md) et [styles intégrés](inline-style-adaptive-forms.md) au lieu de la classe CSS.

   Sélectionnez l’icône Terminé ![aem_forms_save](assets/aem_forms_save.png) pour enregistrer les modifications. La signature est correctement configurée.

   Désormais, lorsque vous remplissez un formulaire, une version PDF du formulaire adaptatif est affichée et les options pour signer le document PDF sont fournies. Pour plus d’informations, voir [Signature d’un formulaire adaptatif en utilisant la signature tactile](signing-forms-using-scribble.md#sign-an-adaptive-form-using-scribble-signature).

## Signature d’un formulaire adaptatif en utilisant la signature tactile {#sign-an-adaptive-form-using-scribble-signature}

1. Une fois que vous avez renseigné le Formulaire adaptatif et que vous avez atteint la page Étape de signature, l’écran de signature s’affiche.

   ![Écran de signature de la page EchoSign](assets/esignscribblesign.jpg)

1. Cliquez sur **[!UICONTROL Signer]**. La boîte de dialogue de signature tactile apparaît. Signez le formulaire et cliquez sur l’icône Terminé ![aem_forms_save](assets/aem_forms_save.png) pour enregistrer la signature.

   ![Boîte de dialogue de signature tactile](assets/scribblewidget.png)

1. Cliquez sur Terminer pour terminer le processus de signature.

   ![Terminer le processus de signature](assets/scribblecomplete.jpg)

Les signatures sont ajoutées au formulaire, et le contrôle de formulaire passe au panneau suivant.

## Voir également {#see-also}

{{see-also}}