---
title: Comment configurer une page de redirection ou un message de remerciement ?
description: Découvrez comment les utilisateurs et utilisatrices peuvent voir affiché un message de remerciement ou être redirigés vers une page web que les personnes chargées de la création de formulaires peuvent configurer lors de la phase de création.
feature: Adaptive Forms, Edge Delivery Services
role: User
level: Intermediate
source-git-commit: 958891216e117acc03c50446ae92f85108d275a7
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 52%

---

# Configurer la redirection ou le message de remerciement

Dans les formulaires créés à l’aide de l’éditeur universel, les auteurs de formulaires peuvent configurer ce qui se passe après l’envoi d’un formulaire par un utilisateur. Vous pouvez afficher un message de remerciement ou rediriger l’utilisateur vers une page web spécifique à l’aide de l’onglet Envoi dans l’extension Modifier les propriétés du formulaire .

Vous pouvez configurer le message de remerciement ou les URL de redirection pour les formulaires créés dans l’éditeur universel à l’aide de l’onglet **Envoi** de l’extension **Propriétés du formulaire AEM**.

## Prérequis

Vous pouvez configurer l’action d’envoi pour les formulaires créés dans l’éditeur universel à l’aide de l’onglet **Envoi** de l’extension **Modifier les propriétés du formulaire**.

![Icône Propriétés du formulaire](/help/forms/assets/ue-form-properties-icon.png)

![Propriétés de formulaire de l’éditeur universel](/help/forms/assets/ue-form-properties.png)

>[!NOTE]
>
> * Si l’icône **Propriétés du formulaire** ne s’affiche pas dans l’interface de l’éditeur universel, activez l’extension **Modifier les propriétés du formulaire** dans Extension Manager.
> * Consultez l’article [Caractéristiques des fonctionnalités d’Extension Manager](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions) pour savoir comment activer ou désactiver les extensions dans l’éditeur universel.

## Comment configurer une redirection ou un message de remerciement ?

Lors de l’envoi d’un formulaire, vous pouvez rediriger l’utilisateur vers une autre page web ou afficher un message.

Pour configurer la page de redirection ou le message de remerciement :

1. Ouvrez le formulaire adaptatif pour le modifier.
2. Ouvrez l’arborescence de contenu et sélectionnez le **[!UICONTROL conteneur de guide]**.
3. Cliquez sur l’icône des propriétés de conteneur de formulaires adaptatifs ![propriétés de conteneur de formulaires adaptatifs](/help/forms/assets/configure-icon.svg). La boîte de dialogue Conteneur de formulaires adaptatifs pour configurer les modèles de données s’ouvre.
4. Ouvrez l’onglet **[!UICONTROL Envoi]**. Les options de paramétrage d’une page de redirection ou d’un message s’affichent :

   ![Boîte de dialogue d’envoi du conteneur de guide pour configurer une page de redirection ou un message](/help/forms/assets/adaptive-forms-core-components-redirect-page-or-thank-you-message.png)

**Configuration des URL de redirection**

* Pour configurer une URL de redirection, pour l’option Lors de l’envoi, sélectionnez l’**[!UICONTROL option Rediriger vers l’URL]**, puis fournissez une adresse absolue, une URL de redirection ou le chemin relatif d’une page AEM Sites.

![rediriger](/help/edge/docs/forms/universal-editor/assets/redirect-ue.png)

**Configurer le message de remerciement**

* Pour configurer un message de remerciement ou personnalisé, sélectionnez l’option **[!UICONTROL Afficher le message]** et écrivez un message dans la zone Contenu du message. Il s’agit d’une zone de texte enrichi. Vous pouvez utiliser l’option Plein écran pour afficher tous les éléments de texte enrichi disponibles.

![merci](/help/edge/docs/forms/universal-editor/assets/thankyou-ue.png)

Pour chaque formulaire, les auteurs et les autrices peuvent configurer une page vers laquelle les utilisateurs et les utilisatrices seront redirigés après l’envoi du formulaire.


