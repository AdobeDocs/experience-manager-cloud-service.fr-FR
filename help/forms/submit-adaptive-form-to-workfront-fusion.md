---
title: Intégration d’Adobe Workfront Fusion à l’envoi AEM Forms
description: Adobe Workfront Fusion vous permet de vous concentrer sur de nouvelles tâches plutôt que sur des tâches répétitives. Vous pouvez connecter Adobe Workfront Fusion à un formulaire adaptatif à l’aide de l’envoi de formulaire.
keywords: Envoi d’un formulaire adaptatif à Adobe Workfront Fusion, Intégration d’Adobe Workfront Fusion à l’envoi AEM Forms, Adobe Workfront Fusion à AEM Forms, Workfront Fusion à AEM Forms, Connexion de Workfront Fusion à AEM Forms, AEM Forms et Workfront Fusion, Comment connecter Workfront Fusion à AEM Forms ?, Connexion de Workfront Fusion à un formulaire
topic-tags: author, developer
feature: Adaptive Forms, Foundation Components, Edge Delivery Services, Core Components
role: Admin, User
exl-id: d3efb450-a879-40ae-8958-0040f99bdafc
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1304'
ht-degree: 13%

---

# Envoyer un formulaire adaptatif à Adobe Workfront Fusion

<span class="preview"> Cette fonctionnalité est disponible par le biais d’un programme d’adoption précoce. Vous pouvez écrire à aem-forms-ea@adobe.com à partir de votre identifiant e-mail officiel pour rejoindre le programme d’adoption précoce et demander l’accès à la fonctionnalité. </span>

[Adobe Workfront Fusion](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-fusion/get-started-with-workfront-fusion/workfront-fusion-overview.html) automatise la répétition des mêmes tâches, comme les workflows d’approbation de documents, le filtrage et le tri des e-mails, ce qui vous permet de vous concentrer sur de nouvelles tâches plutôt que sur des tâches récurrentes. Adobe Workfront Fusion comprend plusieurs scénarios. Un scénario se compose d’une série de modules qui exécutent le transfert de données entre les applications et les services web. Dans un scénario, vous ajoutez différentes étapes (modules) pour automatiser une tâche.

Par exemple, à l’aide de Workfront Fusion, vous pouvez créer un scénario afin de collecter des données avec un formulaire adaptatif, de traiter les données et d’envoyer les données à un magasin de données pour archivage. Une fois qu’un scénario est configuré, Workfront Fusion exécute automatiquement les tâches chaque fois qu’un utilisateur remplit un formulaire, mettant ainsi à jour l’entrepôt de données de manière transparente.

AEM Forms as a Cloud Service fournit un connecteur prêt à l’emploi pour se connecter et envoyer un formulaire adaptatif à Adobe Workfront Fusion. L’envoi d’un formulaire à Adobe Workfront Fusion peut présenter plusieurs avantages :

* Il a permis le transfert transparent des données d’envois de formulaire vers les workflows Workfront Fusion.
* Il permet d’automatiser diverses tâches déclenchées par des envois de formulaire. Vous pouvez notamment lancer des projets, affecter des tâches à des membres d’équipe spécifiques, envoyer des notifications et mettre à jour le statut des projets, le tout sans intervention manuelle.
* Tous les envois de formulaires capturés dans Workfront Fusion fournissent une source unique de vérité pour les informations liées au projet


<!--  AEM as a Cloud Service offers various out of the box submit actions for handling form submissions. You can learn more about these options in the [Adaptive Form Submit Action](/help/forms/configure-submit-actions-core-components.md)  article.-->

>[!VIDEO](https://video.tv.adobe.com/v/3427145/adaptive-forms-adobe-workfront-af-workfront-workfront-aem-forms/?quality=12&learn=on)

<span> Cette vidéo s’applique uniquement aux composants principaux. Pour les composants éditeur universel/de base, reportez-vous à l’article </span>.

## Conditions préalables à l’intégration d’AEM Forms à Adobe Workfront Fusion {#prerequisites}

Pour établir une connexion entre Workfront Fusion et AEM Forms, les éléments suivants sont nécessaires :

* Une licence [Workfront et Workfront Fusion valide](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-fusion/get-started-with-workfront-fusion/license-automation-vs-integration.html).
* Un utilisateur d’AEM disposant du droit d’accéder à [la console de développement](https://my.cloudmanager.adobe.com/) pour [récupérer les informations d’identification du service](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=fr).

## Intégration d’AEM Forms à Adobe Workfront Fusion

### &#x200B;1. Création d’un scénario Workfront {#workflow-scenario}

Pour créer un scénario Workfront, procédez comme suit :

1. [Création d’un scénario](#create-scenario)
1. [Ajouter un hook web à un scénario](#add-webhook)
1. [Ajouter une connexion à un hook web](#add-connection)

#### Création d’un scénario {#create-scenario}

Pour créer un scénario, procédez comme suit :

1. Connectez-vous à votre compte [Workfront Fusion](https://app-qa.workfrontfusion.com/).
1. Cliquez sur **[!UICONTROL Scénarios]** ![icône Partager](/help/forms/assets/Smock_ShareAndroid_18_N.svg) dans le panneau de gauche.
1. Cliquez sur **[!UICONTROL Créer un nouveau scénario]** dans le coin supérieur droit de la page. Une page permettant de créer un nouveau scénario s’affiche à l’écran.
1. Sélectionnez **[!UICONTROL Nouveau scénario]** dans le coin supérieur gauche de la page, puis saisissez le nom correct du scénario.
1. Cliquez sur le point d’interrogation et veillez à ajouter le premier module en tant que **[!UICONTROL AEM Forms]**.

   ![Ajouter un module AEM Forms](/help/forms/assets/workfront-aemforms.png)

   La boîte de dialogue **[!UICONTROL Observer les événements de formulaire]** s’affiche.

   >[!NOTE]
   >
   > Il est obligatoire d’ajouter le premier module en tant que **[!UICONTROL AEM Forms]**.

1. Sélectionnez la boîte de dialogue **[!UICONTROL Observer les événements de formulaire]** et une fenêtre permettant d’ajouter un webhook s’affiche.

#### Ajouter un webhook {#add-webhook}

![Ajouter un webhook](/help/forms/assets/workfront-add-webhook.png)

Pour ajouter un webhook :

1. Cliquez sur **[!UICONTROL Ajouter]** et une boîte de dialogue **[!UICONTROL Ajouter un webhook]** s’affiche.
1. Spécifiez un nom de Webhook.

   >[!NOTE]
   >
   > Il est recommandé de choisir soigneusement le nom de votre webhook, car le nom webhook spécifié apparaît dans l’instance AEM.

1. Cliquez sur **[!UICONTROL Ajouter]** pour ajouter une nouvelle connexion. La boîte de dialogue **[!UICONTROL Créer une connexion]** s’affiche.

>[!NOTE]
>
> Assurez-vous que le compte technique est membre du groupe **forms-users** ; dans le cas contraire, l’ajout d’un webhook échoue.

#### Ajouter une connexion à un webhook {#add-connection}

![Ajouter une connexion](/help/forms/assets/workfront-add-connection.png)

Pour ajouter une connexion :

1. Spécifiez un **[!UICONTROL Nom de la connexion]** dans la boîte de dialogue **[!UICONTROL Créer une connexion]**.

1. Sélectionnez **Environnement** et **Type** dans la liste déroulante.

1. Saisissez l’**URL de l’instance**.

   >[!NOTE]
   >
   > L’URL de l’instance est l’adresse web unique qui pointe vers une instance AEM Forms spécifique.

   Vous pouvez récupérer les informations d’identification du service [ à partir de Developer Console](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=fr) requises pour créer une connexion.

1. Remplacez `ims-na1.adobelogin.com` dans le point d’entrée **IMS** par la valeur de **imsEndpoint** à partir des informations d’identification de service dans la Developer Console.

   >[!NOTE]
   >
   > Conservez la `https://` dans la zone de texte **Point d’entrée IMS** lors de l’ajout de l’URL `imsEndpoint`.

1. Spécifiez les valeurs suivantes dans la boîte de dialogue **[!UICONTROL Créer une connexion]** :
   * Spécifiez **ID client** avec la valeur **clientId** à partir des informations d’identification de service dans la Developer Console.
   * Spécifiez **Client Secret** avec la valeur **clientSecret** à partir des informations d’identification de service dans la Developer Console.
   * Spécifiez **ID de compte technique** avec la valeur **id** à partir des informations d’identification du service dans la Developer Console.
   * Spécifiez **ID d’organisation** avec la valeur **org** à partir des informations d’identification du service dans la Developer Console.
   * **Étendues Meta** avec une valeur de **métascopes** à partir des informations d’identification du service dans la Developer Console.
   * **Clés privées** avec la valeur **privateKey** à partir des informations d’identification de service dans la Developer Console.

   >[!NOTE]
   >
   >* Pour **Clé privée**, supprimez `\r\n` de sa valeur.
   >  Par exemple, si la valeur de la clé privée est :
   >`\r\nIJAVO8GDYAOZ9jMA0GCSqGSIb3DQEBCwUAMDAxL\r\nMy1lMTUxODMxLWNtc3RnLWludGVncmF0aW9uLTAw`, après avoir supprimé la `\r\n` de la clé privée, la clé se présenterait comme suit, avec les deux valeurs apparaissant sur une ligne distincte :
   >
   >   `IJAVO8GDYAOZ9jMA0GCSqGSIb3DQEBCwUAMDAxL`
   >
   >   `My1lMTUxODMxLWNtc3RnLWludGVncmF0aW9uLTAw`
   > 
   >* Vous avez également la possibilité de récupérer une clé privée ou un certificat à partir du fichier en sélectionnant le bouton **Extraire**.

1. Cliquez sur **Continuer**.

   La connexion créée commence à apparaître dans la liste déroulante de la boîte de dialogue **[!UICONTROL Connexion]** dans **[!UICONTROL Ajouter un webhook]**.

1. Sélectionnez la connexion créée **[!UICONTROL Connexion]** dans la liste déroulante.
1. Cliquez sur **[!UICONTROL Enregistrer]**.
1. Cliquez sur **[!UICONTROL OK]** et enregistrez les modifications pour le scénario.
1. Pour activer le scénario, cliquez sur le bouton bascule ON/OFF dans l’éditeur de scénarios.

>[!NOTE]
>
> Si vous n’activez pas le scénario Workfront, il ne détecte pas l’envoi du formulaire. Si vous définissez l’action d’envoi sur Workfront, l’envoi échoue.

### &#x200B;2. Configuration de l’action d’envoi d’un formulaire adaptatif pour Workfront Fusion

>[!BEGINTABS]

>[!TAB Composant de base]

Pour configurer l’action d’envoi d’un formulaire adaptatif en fonction des composants de base pour Workfront Fusion :

1. Ouvrez le formulaire adaptatif pour le modifier et accéder à la section **[!UICONTROL Envoi]** des propriétés du Conteneur de formulaires adaptatifs.
1. Dans la liste déroulante **[!UICONTROL Action Envoyer]**, sélectionnez **[!UICONTROL Appeler un scénario Workfront Fusion]**.
   ![Action Envoyer pour Workfront Fusion](/help/forms/assets/workfront-fusion-fc.png)

1. Sélectionnez **[!UICONTROL Scénario Workfront Fusion]** dans la liste déroulante.
1. Cliquez sur **[!UICONTROL Terminé]**.


>[!TAB Composant principal]

Pour configurer l’action d’envoi d’un formulaire adaptatif en fonction des composants principaux pour Workfront Fusion :

1. Ouvrez l’explorateur de contenu, puis sélectionnez le composant **[!UICONTROL Conteneur de guide]** de votre formulaire adaptatif.
1. Cliquez sur l’icône des propriétés du conteneur de guide ![Propriétés du guide](/help/forms/assets/configure-icon.svg). La fenêtre du conteneur de formulaires adaptatifs s’ouvre.
1. Cliquez sur l’onglet **[!UICONTROL Envoi]**.
1. Dans la liste déroulante **[!UICONTROL Action Envoyer]**, sélectionnez **[!UICONTROL Appeler un scénario Workfront Fusion]**.

   ![Action Envoyer pour Workfront Fusion](/help/forms/assets/workfront-scenario-existing-af.png)
1. Sélectionnez **[!UICONTROL Scénario Workfront Fusion]** dans la liste déroulante.
1. Cliquez sur **[!UICONTROL Terminé]**.

>[!TAB Éditeur universel]

Pour configurer l’action d’envoi d’un formulaire adaptatif créé à l’aide de l’éditeur universel :

1. Ouvrez le formulaire adaptatif pour le modifier.
1. Cliquez sur l’extension **Modifier les propriétés du formulaire** dans l’éditeur.
La boîte de dialogue **Propriétés du formulaire** s’affiche.

   >[!NOTE]
   >
   > * Si l’icône **Modifier les propriétés du formulaire** ne s’affiche pas dans l’interface de l’éditeur universel, activez l’extension **Modifier les propriétés du formulaire** dans Extension Manager.
   > * Consultez l’article [Principales fonctionnalités d’Extension Manager](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions) pour savoir comment activer et désactiver les extensions dans l’éditeur universel.

1. Cliquez sur l’onglet **Envoi** et sélectionnez **[!UICONTROL Appeler un scénario Workfront Fusion]** action d’envoi.

   ![Action Envoyer pour Workfront Fusion](/help/forms/assets/workfront-fusion-ue.png)

1. Sélectionnez **[!UICONTROL Scénario Workfront Fusion]** dans la liste déroulante.
1. Cliquez sur **[!UICONTROL Enregistrer et fermer]**.

>[!ENDTABS]

## Bonnes pratiques {#best-practices}

* Il est recommandé de choisir soigneusement le nom de votre webhook, car il n’existe aucun moyen d’obtenir le nom du scénario au niveau de l’instance AEM. Si vous modifiez le nom du webhook à l’avenir, il ne sera pas reflété dans la liste déroulante d’action d’envoi d’AEM Forms.
* Un scénario peut avoir plusieurs liens webhook, mais un seul lien webhook à la fois est actif. Il est recommandé de supprimer le webhook non lié, de sorte qu’il n’apparaisse pas dans la liste déroulante d’action d’envoi d’AEM Forms.

<!-- During testing or development of Workfront, add the Author URL to the instance URL. However, when deploying Workfront Fusion in a production environment, it is recommended to replicate the scenario URLs for the Publish instance. -->

## Articles connexes

{{af-submit-action}}