---
title: Application de signatures électroniques à un formulaire à l’aide de signatures tactiles
seo-title: Apply electronic signatures to a form using scribble signatures
description: Signature de formulaires à l’aide de la saisie tactile
seo-description: Signing forms using scribble
uuid: ffeba886-9b24-4ed1-95c0-e19356ff2f23
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 76d178d1-8e40-41b3-80d4-66b2f8d04211
docset: aem65
google-site-verification: A1dSvxshSAiaZvk0yHu7-S3hJBb1THj0CZ2Uh8N_ck4
source-git-commit: 73953a3d71f3328def3bd4c1f03516b4839695ea
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 100%

---


# Application de signatures électroniques à un formulaire à l’aide de signatures tactiles {#apply-electronic-signatures-to-a-form-using-deprecated-scribble-signatures}

Vous pouvez utiliser les composants **Signature tactile** et **Étape de signature** pour tracer la signature (saisie tactile) sur un formulaire adaptatif. Le composant Étape de signature affiche une version PDF du formulaire adaptatif. Pour utiliser le composant Étape de signature, l’option Document d’enregistrement doit être activée ou vous devez disposer de formulaires adaptatifs basés sur un modèle de formulaire.

Les deux composants présentent une fenêtre, comme illustré ci-dessous, pour signer un formulaire. Vous pouvez également cliquer sur l’icône de géolocalisation ![aem_6_3_geolocation](assets/aem_6_3_geolocation.png) pour ajouter la géolocalisation à la signature.

![Boîte de dialogue de signature tactile](assets/scribble-signature.png)

## Configuration d’un formulaire adaptatif pour utiliser la signature tactile {#configure-an-adaptive-form-to-use-scribble-signature}

1. Créez une option Document d’enregistrement activée ou un formulaire adaptatif basé sur modèle de formulaire. Pour obtenir des informations détaillées, voir [Création d’un formulaire adaptatif](creating-adaptive-form.md).
1. Faites glisser le composant **Signature tactile** depuis le navigateur de composant et déposez-le dans le formulaire adaptatif.
1. Appuyez sur l’icône de ![configuration](assets/configure.png) **Configurer**. Vous ouvrez ainsi le navigateur de propriétés qui affiche les propriétés du composant Signature tactile. Configurez les propriétés du composant Signature tactile.
1. Faites glisser le composant Étape de signature depuis le navigateur de composant et déposez-le dans le formulaire adaptatif.

   >[!NOTE]
   >
   >Le composant Étape de signature prend toute la largeur disponible pour le formulaire. Il est recommandé de ne pas avoir d’autre composant sur la section contenant le composant Étape de signature.

1. Dans l’explorateur de contenu, appuyez sur **Conteneur de formulaires**, puis sur l’icône **Configurer** ![](assets/configure.png). L’explorateur de propriétés s’ouvre et affiche les propriétés du conteneur de formulaires adaptatifs. Accédez à **Conteneur de formulaires adaptatifs** > **Signature électronique** et décochez l’option **Activer Adobe Sign**. Appuyez sur l’icône Terminé ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) pour enregistrer les modifications.

   >[!NOTE]
   >
   >Lorsque vous ajoutez un composant Étape de signature à un formulaire adaptatif, l’option Activer Adobe Sign est sélectionnée automatiquement.

1. Appuyez sur l’icône de ![configuration](assets/configure.png) **Configurer**. Elle ouvre l’explorateur de propriétés et affiche les propriétés Étape de signature. Configurez les propriétés suivantes :

   * **Nom de l’élément** : spécifiez le nom du composant.

   * **Titre :** indiquez le titre unique du composant.
   * **Message du modèle :** indiquez le message à afficher lorsque la signature PDF est chargée. Les services Adobe Sign mettent un certain temps à préparer et charger la signature PDF.
   * **Service de signature :** sélectionnez l’option **Signature tactile**.

   * **Classe CSS** : spécifiez la classe CSS de la bibliothèque client, le cas échéant. Il est recommandé d’utiliser des [thèmes](themes.md) et des [styles en ligne](inline-style-adaptive-forms.md) au lieu de la classe CSS.

   Appuyez sur l’icône Terminé ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) pour enregistrer les modifications. La signature est configurée correctement.

   Désormais, lorsque vous remplissez un formulaire, une version PDF du formulaire adaptatif est affichée et les options pour signer le document PDF sont fournies. Pour plus d’informations, voir [Signature d’un formulaire adaptatif en utilisant la signature tactile](signing-forms-using-scribble.md#sign-an-adaptive-form-using-scribble-signature).

## Signature d’un formulaire adaptatif en utilisant la signature tactile {#sign-an-adaptive-form-using-scribble-signature}

1. Une fois que vous avez renseigné le Formulaire adaptatif et que vous avez atteint la page Étape de signature, l’écran de signature s’affiche.

   ![Écran de signature de la page EchoSign](assets/esignscribblesign.jpg)

1. Cliquez sur **[!UICONTROL Signer]**. La boîte de dialogue de signature tactile apparaît. Signez le formulaire et cliquez sur l’icône Terminé ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) pour enregistrer la signature.

   ![Boîte de dialogue de signature tactile](assets/scribblewidget.jpg)

1. Cliquez sur Terminer pour terminer le processus de signature.

   ![Terminer le processus de signature](assets/scribblecomplete.jpg)

Les signatures sont ajoutées au formulaire, et le contrôle de formulaire passe au panneau suivant.

