---
title: Intégration d’Adobe Workfront Fusion avec envoi AEM Forms
description: Adobe Workfront Fusion vous permet de vous concentrer sur de nouvelles tâches plutôt que de vous concentrer sur des tâches répétitives. Vous pouvez connecter Adobe Workfront Fusion à un formulaire adaptatif à l’aide de l’envoi de formulaire.
keywords: Envoyer un formulaire adaptatif à Adobe Workfront Fusion, Intégration d’Adobe Workfront Fusion à l’envoi d’AEM Forms, Adobe Workfront Fusion avec AEM Forms, Workfront Fusion avec AEM Forms, Connecter la fusion Workfront à AEM Forms, AEM Forms et à la fusion, Comment connecter la fusion à ?, Connecter la fusion de  à un formulaire
topic-tags: author, developer
feature: Adaptive Forms
role: Admin, User
exl-id: d3efb450-a879-40ae-8958-0040f99bdafc
source-git-commit: d0d7a10b2c1dadb0f8bfaa654db7993d3e5e6635
workflow-type: tm+mt
source-wordcount: '1272'
ht-degree: 6%

---

# Envoyer un formulaire adaptatif à Adobe Workfront Fusion

<span class="preview"> La fonctionnalité est disponible dans le cadre du programme d’adoption précoce. Vous pouvez écrire à aem-forms-ea@adobe.com à partir de votre adresse e-mail officielle pour rejoindre le programme d’adoption précoce et demander l’accès à la fonctionnalité. </span>

[Adobe Workfront Fusion](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-fusion/get-started-with-workfront-fusion/workfront-fusion-overview.html?lang=fr) automatise le processus de répétition des mêmes tâches, comme les workflows d’approbation de document, le filtrage et le tri des emails, ce qui vous permet de vous concentrer sur de nouvelles tâches plutôt que sur des tâches récurrentes. Adobe Workfront Fusion comprend plusieurs scénarios. Un scénario se compose d’une série de modules qui exécutent le transfert de données entre les applications et les services web. Dans un scénario, vous ajoutez différentes étapes (modules) pour automatiser une tâche.

Par exemple, avec Workfront Fusion, vous pouvez créer un scénario pour rassembler des données avec le formulaire adaptatif, traiter les données et envoyer les données à un entrepôt de données en vue de les archiver. Une fois qu’un scénario est configuré, Workfront Fusion exécute automatiquement les tâches chaque fois qu’un utilisateur remplit un formulaire, en mettant à jour facilement l’entrepôt de données.

AEM Forms as a Cloud Service fournit un connecteur prêt à l’emploi pour se connecter et envoyer un formulaire adaptatif à Adobe Workfront Fusion. L’envoi d’un formulaire à Adobe Workfront Fusion peut offrir plusieurs avantages :
* Cela a permis le transfert transparent des données d’envoi de formulaire vers les processus Workfront Fusion.
* Cela permet d’automatiser les différentes tâches déclenchées par les envois de formulaire. Cela peut inclure le lancement de projets, l’affectation de tâches à des membres spécifiques de l’équipe, l’envoi de notifications et la mise à jour des statuts des projets, le tout sans intervention manuelle.
* Toutes les soumissions de formulaires capturées dans Workfront Fusion fournissent une source unique de vérité pour les informations relatives au projet.


<!--  AEM as a Cloud Service offers various out of the box submit actions for handling form submissions. You can learn more about these options in the [Adaptive Form Submit Action](/help/forms/configure-submit-actions-core-components.md)  article.-->

>[!VIDEO](https://video.tv.adobe.com/v/3427145/adaptive-forms-adobe-workfront-af-workfront-workfront-aem-forms/?quality=12&learn=on)

## Conditions préalables pour intégrer AEM Forms à Adobe Workfront Fusion {#prerequisites}

Pour établir une connexion entre Workfront Fusion et AEM Forms, les éléments suivants sont nécessaires :

* Une licence [Workfront and Workfront Fusion](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-fusion/get-started-with-workfront-fusion/license-automation-vs-integration.html?lang=fr) valide.
* Un utilisateur AEM ayant le droit d’accéder à [Dev Console](https://my.cloudmanager.adobe.com/) pour [ récupérer les informations d’identification du service](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=fr).

## Intégration d’AEM Forms à Adobe Workfront Fusion

### 1. Création d’un scénario Workfront {#workflow-scenario}

Pour créer un scénario Workfront, procédez comme suit :

1. [Création d’un scénario](#create-scenario)
1. [Ajout d’un point d’extension Web à un scénario](#add-webhook)
1. [Ajout d’une connexion à un point d’extension Web](#add-connection)

#### Création d’un scénario {#create-scenario}

Pour créer un scénario :
1. Connectez-vous à votre [compte Workfront Fusion](https://app-qa.workfrontfusion.com/).
1. Cliquez sur **[!UICONTROL Scénarios]** ![Icône Partager](/help/forms/assets/Smock_ShareAndroid_18_N.svg) dans le panneau de gauche.
1. Cliquez sur **[!UICONTROL Créer un nouveau scénario]** dans le coin supérieur droit de la page. Une page pour créer un scénario s’affiche à l’écran.
1. Sélectionnez **[!UICONTROL Nouveau scénario]** dans le coin supérieur gauche de la page et saisissez un nom approprié pour le scénario.
1. Cliquez sur le point d’interrogation et assurez-vous d’ajouter le premier module en tant que **[!UICONTROL AEM Forms]**.

   ![Ajouter un module AEM Forms](/help/forms/assets/workfront-aemforms.png)

   La boîte de dialogue **[!UICONTROL Rechercher les événements de formulaire]** s’affiche.

   >[!NOTE]
   >
   > Il est obligatoire d’ajouter le premier module en tant que **[!UICONTROL AEM Forms]**.

1. Sélectionnez la boîte de dialogue **[!UICONTROL Rechercher les événements de formulaire]** et une fenêtre pour ajouter un webhook s’affiche.

#### Ajout d’un webhook {#add-webhook}

![Ajouter un webhook](/help/forms/assets/workfront-add-webhook.png)

Pour ajouter un webhook :

1. Cliquez sur **[!UICONTROL Ajouter]** et une boîte de dialogue **[!UICONTROL Ajouter un webhook]** s’affiche.
1. Indiquez un nom de webhook.

   >[!NOTE]
   >
   > Il est recommandé de choisir soigneusement votre nom de webhook, car le nom spécifié s’affiche dans l’instance AEM.

1. Cliquez sur **[!UICONTROL Ajouter]** pour ajouter une nouvelle connexion. La boîte de dialogue **[!UICONTROL Créer une connexion]** s’affiche.

>[!NOTE]
>
> Assurez-vous que le compte technique est membre du groupe **forms-users** ; dans le cas contraire, l’ajout d’un webhook échoue.

#### Ajout d’une connexion à un webhook {#add-connection}

![Ajouter une connexion](/help/forms/assets/workfront-add-connection.png)

Pour ajouter une connexion :

1. Spécifiez un **[!UICONTROL nom de connexion]** dans la boîte de dialogue **[!UICONTROL Créer une connexion]**.

1. Sélectionnez **Environnement** et **Type** dans la liste déroulante.

1. Saisissez l’ **URL de l’instance**.

   >[!NOTE]
   >
   > URL d’instance est l’adresse web unique qui pointe vers une instance AEM Forms spécifique.

   Vous pouvez récupérer les [informations d’identification du service à partir de Developer Console](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=fr) requises pour créer une connexion.

1. Remplacez `ims-na1.adobelogin.com` dans le **point d’entrée IMS** par la valeur **imsEndpoint** des informations d’identification du service dans la console de développement.

   >[!NOTE]
   >
   > Conservez l’ `https://` dans la zone de texte **IMS endpoint** lors de l’ajout de l’URL `imsEndpoint`.

1. Spécifiez les valeurs suivantes dans la boîte de dialogue **[!UICONTROL Créer une connexion]** :
   * Spécifiez **Client ID** avec la valeur **clientId** à partir des informations d’identification du service dans la console de développement.
   * Spécifiez **Client Secret** avec la valeur **clientSecret** des informations d’identification du service dans la console de développement.
   * Spécifiez **l’identifiant de compte technique** avec la valeur **id** à partir des informations d’identification du service dans Developer Console.
   * Spécifiez **ID d’organisation** avec la valeur **org** à partir des informations d’identification du service dans la console de développement.
   * **Métadonnées** avec la valeur de **metascopes** des informations d’identification du service dans la console de développement.
   * **Clés privées** avec la valeur **privateKey** des informations d’identification du service dans Developer Console.

   >[!NOTE]
   >
   >* Pour **Private Key**, supprimez `\r\n` de sa valeur.
   >  Par exemple, si la valeur de la clé privée est :
   >`\r\nIJAVO8GDYAOZ9jMA0GCSqGSIb3DQEBCwUAMDAxL\r\nMy1lMTUxODMxLWNtc3RnLWludGVncmF0aW9uLTAw`, puis après avoir supprimé l’élément `\r\n` de la clé privée, la clé ressemblerait à ce qui suit, avec les deux valeurs apparaissant dans une ligne distincte :
   >
   >   `IJAVO8GDYAOZ9jMA0GCSqGSIb3DQEBCwUAMDAxL`
   >
   >   `My1lMTUxODMxLWNtc3RnLWludGVncmF0aW9uLTAw`
   > 
   >* Vous avez également la possibilité de récupérer une clé privée ou un certificat à partir du fichier en sélectionnant le bouton **Extract** .

1. Cliquez sur **Continuer**.

   La connexion créée commence à apparaître dans la liste déroulante de **[!UICONTROL Connexion]** dans la boîte de dialogue **[!UICONTROL Ajouter un webhook]** .

1. Sélectionnez la connexion **[!UICONTROL Connexion]** créée dans la liste déroulante.
1. Cliquez sur **[!UICONTROL Enregistrer]**.
1. Cliquez sur **[!UICONTROL OK]** et enregistrez les modifications pour le scénario.
1. Pour activer le scénario, cliquez sur le bouton d’activation/de désactivation dans l’éditeur de scénarios.

>[!NOTE]
>
> Si vous n’activez pas le scénario Workfront, celui-ci ne détecte pas l’envoi du formulaire, et la définition de l’action d’envoi sur Workfront entraîne l’échec de l’envoi.

### 2. Configuration de l’action d’envoi d’un formulaire adaptatif pour Workfront Fusion

Vous pouvez configurer l’action d’envoi pour Workfront Fusion pour :
* [Nouvelle Forms adaptative](#new-af-submit-action)
* [Formulaires adaptatifs existants](#existing-af-submit-action)

#### Configuration de l’action d’envoi du nouveau formulaire adaptatif pour Workfront Fusion {#new-af-submit-action}

Pour configurer l’action d’envoi du nouveau formulaire adaptatif pour Workfront Fusion :

1. Connectez-vous à votre instance AEM.
1. Accédez à **[!UICONTROL Forms]** > **[!UICONTROL Forms and Documents]** > **[!UICONTROL Créer]** > **[!UICONTROL Formulaire adaptatif]**. L’assistant **[!UICONTROL Créer un formulaire]** s’affiche.
1. Sélectionnez un modèle de formulaire adaptatif dans l’onglet **[!UICONTROL Source]** .
1. Sélectionnez un thème dans l’onglet **[!UICONTROL Style]** .

   ![Action Envoyer pour Workfront Fusion](/help/forms/assets/workfront-scenario-new-af.png)

1. Sélectionnez **[!UICONTROL Appeler un scénario de fusion Workfront]** dans l’onglet **[!UICONTROL Submission]** (Envoi).
1. Sélectionnez le webhook créé dans l’onglet **[!UICONTROL Options]** de la fenêtre **[!UICONTROL Propriétés]** .

   >[!NOTE]
   >
   > Le nom du webhook du scénario Workfront apparaît dans la liste déroulante **Options** .

1. Cliquez sur **[!UICONTROL Créer]**.
1. Indiquez le nom de votre nouveau formulaire adaptatif et cliquez sur **[!UICONTROL Créer]**.

#### Configuration de l’action d’envoi du formulaire adaptatif existant pour Workfront Fusion {#existing-af-submit-action}

Pour configurer l’action d’envoi du formulaire adaptatif existant pour Workfront Fusion :

1. Connectez-vous à votre instance AEM.
1. Accédez à **[!UICONTROL Forms]** > **[!UICONTROL Forms and Documents]**.
1. Sélectionnez un formulaire adaptatif et ouvrez-le en mode d’édition.
1. Ouvrez l’explorateur de contenu, puis sélectionnez le composant **[!UICONTROL Conteneur de guide]** de votre formulaire adaptatif.
1. Cliquez sur l’icône des propriétés du conteneur de guide ![Propriétés du guide](/help/forms/assets/configure-icon.svg). La fenêtre du conteneur de formulaires adaptatifs s’ouvre.

   ![Action Envoyer pour Workfront Fusion](/help/forms/assets/workfront-scenario-existing-af.png)

1. Ouvrez l’onglet **[!UICONTROL Envoi]**.
1. Sélectionnez l’ **[!UICONTROL action Envoyer]** comme **[!UICONTROL Appeler un scénario de fusion Workfront]**
1. Sélectionnez **[!UICONTROL scénario de fusion Workfront]** dans la liste déroulante.
1. Cliquez sur **[!UICONTROL Terminé]**.

## Bonnes pratiques {#best-practices}

* Il est recommandé de choisir soigneusement votre nom de webhook, car il n’est pas possible d’obtenir le nom du scénario dans l’instance AEM. Si vous modifiez le nom du webhook à l’avenir, il n’est plus pris en compte dans la liste déroulante Action d’envoi d’AEM Forms.
* Un scénario peut comporter plusieurs liens webhook, mais à la fois, un seul lien webhook est actif. Il est recommandé de supprimer le webhook non lié afin qu’il n’apparaisse pas dans la liste déroulante Action d’envoi AEM Forms.

<!-- During testing or development of Workfront, add the Author URL to the instance URL. However, when deploying Workfront Fusion in a production environment, it is recommended to replicate the scenario URLs for the Publish instance. -->

## Articles connexes

{{af-submit-action}}