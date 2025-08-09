---
title: Comment envoyer un e-mail lors de l’envoi d’un formulaire adaptatif ?
description: Découvrez le processus de configuration des notifications par e-mail lors de l’envoi d’un formulaire adaptatif.
keywords: Guide d’envoi et d’envoi de formulaire adaptatif, Comment envoyer un e-mail pour un formulaire adaptatif, Action d’envoi d’e-mail, E-mail de formulaire adaptatif, Envoyer un e-mail
feature: Adaptive Forms, Core Components, Foundation Components, Edge Delivery Services
exl-id: 70386e57-345b-4edb-97f1-3fd52ea9ff4f
role: User, Developer
source-git-commit: 44a8d5d5fdd2919d6d170638c7b5819c898dcefe
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 17%

---

# Configurer l’action Envoyer un e-mail pour un formulaire adaptatif

L’action d’envoi **[!UICONTROL Envoyer un e-mail]** permet d’envoyer un e-mail à un ou à plusieurs destinataires lors de l’envoi réussi du formulaire. Cette action Envoyer vous permet de créer un e-mail qui peut inclure des données de formulaire dans un format prédéfini. Prenons l’exemple du modèle suivant, dans lequel le nom du client, l’adresse d’expédition, le nom de l’état et le code postal sont récupérés à partir des données de formulaire envoyées :


    ```
    Bonjour ${customer_Name},
    
    Les paramètres suivants sont définis comme votre adresse d’expédition par défaut :
    ${customer_Name},
    ${customer_Shipping_Address},
    ${customer_State},
    ${customer_ZIPCode}
    
    Cordialement,
    WKND
    ```

## Avantages

Voici quelques avantages de la configuration d’un formulaire adaptatif avec une action d’envoi Envoyer un e-mail :

* Il permet une communication rapide, car les données de formulaire sont directement envoyées aux destinataires d’e-mail désignés.
* Elle permet de rationaliser le workflow en intégrant directement les envois de formulaire dans les notifications par e-mail.
* Elle permet aux entreprises de personnaliser le contenu des e-mails, afin qu’il réponde à des besoins de communication spécifiques.

>[!BEGINTABS]

>[!TAB Composant de base]

Pour configurer une action Envoyer un e-mail pour le composant de base :

1. Ouvrez le formulaire adaptatif pour le modifier et accéder à la section **[!UICONTROL Envoi]** des propriétés du Conteneur de formulaires adaptatifs.
1. Dans la liste déroulante **[!UICONTROL Action Envoyer]**, sélectionnez **[!UICONTROL Envoyer un e-mail]**.

   ![Configuration de l’action Envoyer un e-mail](/help/forms/assets/send-email-fc.png)

1. Indiquez l’ID d’e-mail de l’expéditeur dans la zone de texte **[!UICONTROL De]**.
1. Ajoutez l’ID d’e-mail du destinataire dans la zone de texte **[!UICONTROL À]**. Vous pouvez ajouter plusieurs destinataires en cliquant sur le bouton **[!UICONTROL Ajouter]**.
1. [Facultatif] Ajoutez le destinataire pour Cc et Cci en cliquant sur le bouton **[!UICONTROL Ajouter]**.
1. Spécifiez une ligne d’objet dans la zone de texte **[!UICONTROL Objet]**.
1. Ajoutez un modèle d’e-mail pour configurer l’action d’envoi d’e-mail.
   * Vous pouvez spécifier le chemin d’accès au modèle d’e-mail externe enregistré dans vos ressources AEM à l’aide de l’option **[!UICONTROL Chemin d’accès au modèle externe]**.
   * Vous pouvez également ajouter un modèle d’e-mail personnalisé pour l’envoi du formulaire dans la zone de texte **[!UICONTROL Modèle d’e-mail]**.
1. [Facultatif] L’action d’envoi **[!UICONTROL Envoyer un e-mail]** permet d’inclure des pièces jointes et un [document d’enregistrement)](generate-document-of-record-core-components.md) dans l’e-mail.
1. Cliquez sur **[!UICONTROL Terminé]**.

>[!TAB Composant principal]

Pour configurer l’action d’envoi Envoyer un e-mail pour le composant principal :

1. Ouvrez l’explorateur de contenu, puis sélectionnez le composant **[!UICONTROL Conteneur de guide]** de votre formulaire adaptatif.
1. Cliquez sur l’icône des propriétés du conteneur de guide ![Propriétés du guide](/help/forms/assets/configure-icon.svg). La fenêtre du conteneur de formulaires adaptatifs s’ouvre.
1. Cliquez sur l’onglet **[!UICONTROL Envoi]**.
1. Dans la liste déroulante **[!UICONTROL Action Envoyer]**, sélectionnez **[!UICONTROL Envoyer un e-mail]**.

   ![Configuration de l’action Envoyer un e-mail](/help/forms/assets/send-email-action-configuration.gif)
1. Indiquez l’ID d’e-mail de l’expéditeur dans la zone de texte **[!UICONTROL De]**.
1. Ajoutez l’ID d’e-mail du destinataire dans la zone de texte **[!UICONTROL À]**. Vous pouvez ajouter plusieurs destinataires en cliquant sur le bouton **[!UICONTROL Ajouter]**.
1. [Facultatif] Ajoutez le destinataire pour Cc et Cci en cliquant sur le bouton **[!UICONTROL Ajouter]**.
1. Spécifiez une ligne d’objet dans la zone de texte **[!UICONTROL Objet]**.
1. Ajoutez un modèle d’e-mail pour configurer l’action d’envoi d’e-mail.
   * Vous pouvez spécifier le chemin d’accès au modèle d’e-mail externe enregistré dans vos ressources AEM à l’aide de l’option **[!UICONTROL Chemin d’accès au modèle externe]**.
   * Vous pouvez également ajouter un modèle d’e-mail personnalisé pour l’envoi du formulaire dans la zone de texte **[!UICONTROL Modèle d’e-mail]**.
1. [Facultatif] L’action d’envoi **[!UICONTROL Envoyer un e-mail]** permet d’inclure des pièces jointes et un [document d’enregistrement)](generate-document-of-record-core-components.md) dans l’e-mail.
1. Cliquez sur **[!UICONTROL Terminé]**.

>[!TAB Éditeur universel]

Pour configurer l’action d’envoi Envoyer un e-mail dans l’éditeur universel :

1. Ouvrez le formulaire adaptatif pour le modifier.
1. Cliquez sur l’extension **Modifier les propriétés du formulaire** dans l’éditeur.
La boîte de dialogue **Propriétés du formulaire** s’affiche.

   >[!NOTE]
   >
   > * Si l’icône **Modifier les propriétés de formulaire** ne s’affiche pas dans l’interface de l’éditeur universel, activez l’extension **Modifier les propriétés de formulaire** dans Extension Manager.
   > * Consultez l’article [Caractéristiques des fonctionnalités d’Extension Manager](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions) pour savoir comment activer ou désactiver les extensions dans l’éditeur universel.


1. Cliquez sur l’onglet **Envoi** et sélectionnez l’action d’envoi **[!UICONTROL Envoyer un e-mail]**.

   ![Envoyer un e-mail à l’éditeur universel](/help/forms/assets/send-email-ue.png)

1. Indiquez l’ID d’e-mail de l’expéditeur dans la zone de texte **[!UICONTROL De]**.
1. Ajoutez l’ID d’e-mail du destinataire dans la zone de texte **[!UICONTROL À]**. Vous pouvez ajouter plusieurs destinataires en cliquant sur le bouton **[!UICONTROL Ajouter]**.
1. [Facultatif] Ajoutez le destinataire pour Cc et Cci en cliquant sur le bouton **[!UICONTROL Ajouter]**.
1. Spécifiez une ligne d’objet dans la zone de texte **[!UICONTROL Objet]**.
1. Ajoutez un modèle d’e-mail pour configurer l’action d’envoi d’e-mail.
   * Vous pouvez spécifier le chemin d’accès au modèle d’e-mail externe enregistré dans vos ressources AEM à l’aide de l’option **[!UICONTROL Chemin d’accès au modèle externe]**.
   * Vous pouvez également ajouter un modèle d’e-mail personnalisé pour l’envoi du formulaire dans la zone de texte **[!UICONTROL Modèle d’e-mail]**.
1. [Facultatif] L’action d’envoi **[!UICONTROL Envoyer un e-mail]** permet d’inclure des pièces jointes et un [document d’enregistrement)](generate-document-of-record-core-components.md) dans l’e-mail.
1. Cliquez sur **[!UICONTROL Enregistrer et fermer]**.

>[!ENDTABS]

## Bonnes pratiques {#best-practices}

* Il est recommandé de garder le contenu de l’e-mail clair et concis. Les utilisateurs doivent comprendre l’objectif de l’e-mail et toute action qu’ils doivent entreprendre.
* Il est recommandé que tous les champs de formulaire aient des noms d’élément uniques, même s’ils sont placés sur différents panneaux au sein d’un formulaire adaptatif.
* Lorsque vous utilisez AEM as a Cloud Service, les e-mails sortants doivent être chiffrés. Par défaut, la fonctionnalité d’e-mail sortant est désactivée. Pour les désactiver, envoyez un ticket d’assistance pour [demander l’accès](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=fr#sending-email).

## Articles connexes

{{af-submit-action}}
