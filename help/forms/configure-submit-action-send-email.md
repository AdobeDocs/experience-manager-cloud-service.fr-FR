---
Title: How to send an email on submission of an Adaptive Form?
Description: Explore the process to set up email notifications when submitting an Adaptive Form.
keywords: comment envoyer un courrier électronique pour un formulaire adaptatif, une action Envoyer par messagerie, un courrier électronique de formulaire adaptatif, un courrier électronique d’envoi de formulaire, un guide d’envoi de courrier électronique
feature: Adaptive Forms, Core Components
exl-id: 70386e57-345b-4edb-97f1-3fd52ea9ff4f
title: "Comment configurer une action Envoyer pour un formulaire adaptatif ?"
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 16%

---

# Configurer l’action Envoyer un e-mail pour un formulaire adaptatif

L’action d’envoi **[!UICONTROL Envoyer un courrier électronique]** vous permet d’envoyer un courrier électronique à un ou plusieurs destinataires lors de l’envoi réussi du formulaire. Cette action Envoyer permet de créer un email pouvant inclure des données de formulaire dans un format prédéfini. Prenons l’exemple du modèle suivant où le nom du client, l’adresse de livraison, le nom de l’état et le code postal sont récupérés dans les données de formulaire envoyées :


    &quot;
    Hi ${customer_Name},
    
    Les paramètres suivants sont définis comme votre adresse de livraison par défaut :
    ${customer_Name},
    ${customer_Shipping_Address},
    ${customer_State},
    ${customer_ZIPCode}
    
    Regards,
    WKND
    
    &quot;


## Avantages

La configuration d’un formulaire adaptatif avec l’action Envoyer un courrier électronique présente les avantages suivants :

* Il permet une communication rapide, car les données de formulaire sont directement envoyées aux destinataires désignés de l’e-mail.
* Cela permet de rationaliser le processus en intégrant directement les envois de formulaire dans les notifications électroniques.
* Il aide les entreprises à personnaliser le contenu de l’email, ce qui le rend adapté à des besoins de communication spécifiques.

## Configuration de l’action Envoyer un courrier électronique {#steps-to-configure-send-email-submit-action}

Pour configurer l’action Envoyer :

1. Ouvrez l’explorateur de contenu, puis sélectionnez le composant **[!UICONTROL Conteneur de guide]** de votre formulaire adaptatif.
1. Cliquez sur l’icône des propriétés du conteneur de guide ![Propriétés du guide](/help/forms/assets/configure-icon.svg). La fenêtre du conteneur de formulaires adaptatifs s’ouvre.
1. Cliquez sur l’onglet **[!UICONTROL Envoi]**.
1. Dans la liste déroulante **[!UICONTROL Submit Action]**, sélectionnez **[!UICONTROL Send email]**.

   ![ Configuration d’action de Send Email](/help/forms/assets/send-email-action-configuration.gif)
1. Indiquez l’ID d’adresse électronique de l’expéditeur dans la zone de texte **[!UICONTROL De]** .
1. Ajoutez l’ID d’email du destinataire dans la zone de texte **[!UICONTROL À]** . Vous pouvez ajouter plusieurs destinataires en cliquant sur le bouton **[!UICONTROL Ajouter]** .
1. [Facultatif] Ajoutez le destinataire pour CC et Cci en cliquant sur le bouton **[!UICONTROL Ajouter]** .
1. Spécifiez un objet dans la zone de texte **[!UICONTROL Objet]**.
1. Ajoutez un modèle de courrier électronique pour configurer l’action d’envoi de courrier électronique.
   * Vous pouvez spécifier le chemin d’accès au modèle de courrier électronique externe enregistré dans vos ressources AEM à l’aide de l’option **[!UICONTROL Chemin d’accès au modèle externe]** .
   * Vous pouvez également ajouter un modèle de courrier électronique personnalisé pour l’envoi du formulaire dans la zone de texte **[!UICONTROL Modèle de courrier électronique]** .
1. [Facultatif] L’action d’envoi **[!UICONTROL Envoyer un courrier électronique]** permet d’inclure des pièces jointes et un [document d’enregistrement (DoR)](generate-document-of-record-core-components.md) avec le courrier électronique.
1. Cliquez sur **[!UICONTROL Terminé]**.

## Bonnes pratiques {#best-practices}

* Il est recommandé de garder le contenu de l&#39;email clair et concis. Les utilisateurs doivent comprendre l’objectif de l’email et les actions qu’ils doivent entreprendre.
* Il est recommandé que tous les champs de formulaire aient des noms d’éléments uniques, même s’ils sont placés sur différents panneaux dans un formulaire adaptatif.
* Lors de l’utilisation d’AEM as a Cloud Service, le courrier électronique sortant nécessite un chiffrement. Par défaut, la fonctionnalité des emails sortants est désactivée. Pour l&#39;activer, envoyez un ticket d&#39;assistance à [request access](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=fr#sending-email).


## Articles connexes

{{af-submit-action}}
