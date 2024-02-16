---
title: Intégration d’Adobe Workfront Fusion avec envoi AEM Forms
description: Adobe Workfront Fusion vous permet de vous concentrer sur de nouvelles tâches plutôt que de vous concentrer sur des tâches répétitives. Vous pouvez connecter Adobe Workfront Fusion à un formulaire adaptatif à l’aide de l’envoi de formulaire.
keywords: Envoyer un formulaire adaptatif à Adobe Workfront Fusion, Intégration d’Adobe Workfront Fusion à l’envoi d’AEM Forms, Adobe Workfront Fusion avec AEM Forms, Workfront Fusion avec AEM Forms, Connecter la fusion Workfront à AEM Forms, AEM Forms et à la fusion, Comment connecter la fusion à ?, Connecter la fusion de  à un formulaire
topic-tags: author, developer
feature: Adaptive Forms
role: Admin, User
exl-id: d3efb450-a879-40ae-8958-0040f99bdafc
source-git-commit: 8546e6286bea5f603b1e011a76c206b178337ab7
workflow-type: tm+mt
source-wordcount: '1238'
ht-degree: 4%

---

# Envoyer un formulaire adaptatif à Adobe Workfront Fusion

<span class="preview"> La fonctionnalité est disponible sous le programme des premiers adopteurs. Vous pouvez écrire à aem-forms-early-adopter-program@adobe.com à partir de votre ID de courrier électronique officiel pour rejoindre le programme des premiers adopteurs et demander l’accès à la fonctionnalité. </span>

[Adobe Workfront Fusion](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-fusion/get-started-with-workfront-fusion/workfront-fusion-overview.html) automatise le processus de répétition des mêmes tâches, comme les workflows d’approbation de document, le filtrage et le tri des emails, ce qui vous permet de vous concentrer sur de nouvelles tâches plutôt que sur des tâches récurrentes. Adobe Workfront Fusion comprend plusieurs scénarios. Un scénario se compose d’une série de modules qui exécutent le transfert de données entre les applications et les services web. Dans un scénario, vous ajoutez différentes étapes (modules) pour automatiser une tâche.

Par exemple, avec Workfront Fusion, vous pouvez créer un scénario pour rassembler des données avec le formulaire adaptatif, traiter les données et envoyer les données à un entrepôt de données en vue de les archiver. Une fois qu’un scénario est configuré, Workfront Fusion exécute automatiquement les tâches chaque fois qu’un utilisateur remplit un formulaire, en mettant à jour facilement l’entrepôt de données.

AEM as a Cloud Service propose différentes actions d’envoi prêtes à l’emploi pour gérer les envois de formulaire. Pour en savoir plus sur ces options, voir [Action d’envoi de formulaire adaptatif](/help/forms/configure-submit-actions-core-components.md)  article.


## Avantages de l’utilisation d’Adobe Workfront Fusion{#advatages-of-workfront-fusion}

Certains des avantages de l’utilisation d’Adobe Workfront Fusion avec AEM Forms :

* Envoi de données capturées avec le Forms adaptatif à un scénario de fusion Workfront
* Automatisation des tâches moins sujettes aux erreurs.
* Personnalisation des exigences spécifiques à une organisation qui n’est pas directement incluse dans Workfront.
* Gestion de logiques simples et de décisions simples, par exemple des instructions if/then.

## Conditions préalables pour intégrer AEM Forms à Adobe Workfront Fusion {#prerequisites}

Les conditions préalables requises pour connecter Workfront Fusion à AEM Forms sont les suivantes :

* Un valide [Licence Workfront Fusion](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-fusion/get-started-with-workfront-fusion/license-automation-vs-integration.html).
* Un utilisateur AEM ayant le droit d’accéder [Console de développement](https://my.cloudmanager.adobe.com/) to [récupération des informations d’identification du service](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=fr).

## Intégration d’AEM Forms à Adobe Workfront Fusion

>[!VIDEO](https://video.tv.adobe.com/v/3427145/adaptive-forms-adobe-workfront-af-workfront-workfront-aem-forms/?quality=12&learn=on)

Pour se connecter [Fusion Workfront](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-fusion/get-started-with-workfront-fusion/workfront-fusion-overview.html) pour créer un formulaire, procédez comme suit :

### 1. Création d’un scénario Workfront {#workflow-scenario}

Pour créer un scénario Workfront :
1. Se connecter à [Compte Workfront Fusion](https://app-qa.workfrontfusion.com/).
1. Cliquez sur **[!UICONTROL Scénarios]** ![Icône Partager](/help/forms/assets/Smock_ShareAndroid_18_N.svg) dans le panneau de gauche.
1. Cliquez sur **[!UICONTROL Création d’un scénario]** dans le coin supérieur droit de la page. Une page pour créer un scénario s’affiche à l’écran.
1. Sélectionner **[!UICONTROL Nouveau scénario]** dans le coin supérieur gauche de la page, saisissez un nom approprié pour le scénario.
1. Cliquez sur le point d’interrogation et assurez-vous d’ajouter le premier module en tant que **[!UICONTROL AEM Forms]**.

   ![Ajout d’un module AEM Forms](/help/forms/assets/workfront-aemforms.png)

   La variable **[!UICONTROL Surveillance des événements de formulaire]** s’affiche.

   >[!NOTE]
   >
   > Il est obligatoire d’ajouter le premier module en tant que **[!UICONTROL AEM Forms]**.

1. Sélectionnez la variable **[!UICONTROL Surveillance des événements de formulaire]** s’affiche, ainsi qu’une fenêtre permettant d’ajouter un webhook.

#### 1.1 Ajout d’un webhook {#add-webhook}

![Ajout d’un webhook](/help/forms/assets/workfront-add-webhook.png)

Pour ajouter un webhook :

1. Cliquez sur **[!UICONTROL Ajouter]** et un **[!UICONTROL Ajout d’un webhook]** s’affiche.
1. Indiquez un nom de webhook.

   >[!NOTE]
   >
   > Il est recommandé de choisir soigneusement votre nom de webhook, car le nom spécifié s’affiche dans l’instance AEM.

1. Cliquez sur **[!UICONTROL Ajouter]** pour ajouter une nouvelle connexion. La variable **[!UICONTROL Création d’une connexion]** s’affiche.

#### 1.2 Ajout d’une connexion à un webhook {#add-connection}

![Ajout d’une connexion](/help/forms/assets/workfront-add-connection.png)

Pour ajouter une connexion :

1. Spécifiez un **[!UICONTROL Nom de la connexion]** dans le **[!UICONTROL Création d’une connexion]** de la boîte de dialogue

1. Sélectionner **Environnement** et **Type** dans la liste déroulante.

1. Saisissez le **URL de l’instance**.

   >[!NOTE]
   >
   > URL d’instance est l’adresse web unique qui pointe vers une instance AEM Forms spécifique.

   Vous pouvez récupérer la variable [informations d’identification du service à partir de Developer Console](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=fr) requis pour créer une connexion.

1. Remplacer `ims-na1.adobelogin.com` dans le **Point d’entrée IMS** avec la valeur de **imsEndpoint** à partir des informations d’identification du service dans Developer Console.

   >[!NOTE]
   >
   > Conservez la variable `https://` dans le **Point d’entrée IMS** textbox lors de l’ajout de la propriété `imsEndpoint` URL.

1. Spécifiez les valeurs suivantes dans la variable **[!UICONTROL Création d’une connexion]** boîte de dialogue :
   * Spécifier **ID client** avec la valeur de **clientId** à partir des informations d’identification du service dans Developer Console.
   * Spécifier **Secret du client** avec la valeur de **clientSecret** à partir des informations d’identification du service dans Developer Console.
   * Spécifier **Identifiant du compte technique**  avec la valeur de **id** à partir des informations d’identification du service dans Developer Console.
   * Spécifier **ID d’organisation**  avec la valeur de **org** à partir des informations d’identification du service dans Developer Console.
   * **Métadonnées**  avec la valeur de **métascopes** à partir des informations d’identification du service dans Developer Console.
   * **Clés privées**  avec la valeur de **privateKey** à partir des informations d’identification du service dans Developer Console.

   >[!NOTE]
   >
   >* Pour **Clé privée**, supprimer `\r\n` de sa valeur.
   >  Par exemple, si la valeur de la clé privée est :
   >`\r\nIJAVO8GDYAOZ9jMA0GCSqGSIb3DQEBCwUAMDAxL\r\nMy1lMTUxODMxLWNtc3RnLWludGVncmF0aW9uLTAw`, puis après avoir supprimé la variable `\r\n` à partir de la clé privée, la clé ressemblerait à ce qui suit, les deux valeurs apparaissant dans une ligne distincte :
   >
   >   `IJAVO8GDYAOZ9jMA0GCSqGSIb3DQEBCwUAMDAxL`
   >
   >   `My1lMTUxODMxLWNtc3RnLWludGVncmF0aW9uLTAw`
   > 
   >* Vous avez également la possibilité de récupérer une clé privée ou un certificat à partir du fichier en sélectionnant l’option **Extract** bouton .

1. Cliquez sur **Continuer**.

   La connexion créée commence à apparaître dans la liste déroulante du **[!UICONTROL Connexion]** dans le **[!UICONTROL Ajout d’un webhook]** de la boîte de dialogue

1. Sélectionner la connexion créée **[!UICONTROL Connexion]** dans la liste déroulante.
1. Cliquez sur **[!UICONTROL Enregistrer]**.
1. Cliquez sur **[!UICONTROL OK]** et enregistrez les modifications pour le scénario.
1. Pour activer le scénario, cliquez sur le bouton d’activation/de désactivation dans l’éditeur de scénarios.

>[!NOTE]
>
> Si vous n’activez pas le scénario Workfront, celui-ci ne détecte pas l’envoi du formulaire, et la définition de l’action d’envoi sur Workfront entraîne l’échec de l’envoi.

### 2. Configuration de l’action d’envoi d’un formulaire adaptatif pour Workfront Fusion

Vous pouvez configurer l’action d’envoi pour la fusion de polices de travail pour :
* [Nouvelle Forms adaptative](#new-af-submit-action)
* [Formulaires adaptatifs existants](#existing-af-submit-action)

#### Configuration de l’action d’envoi du nouveau formulaire adaptatif pour Workfront Fusion {#new-af-submit-action}

Pour configurer l’action d’envoi du nouveau formulaire adaptatif pour Workfront Fusion :

1. Connectez-vous à votre instance AEM.
1. Accédez à **[!UICONTROL Forms]** > **[!UICONTROL Forms et documents]** > **[!UICONTROL Créer]** > **[!UICONTROL Formulaire adaptatif]**. La variable **[!UICONTROL Créer un formulaire]** s’affiche.
1. Sélectionnez un modèle de formulaire adaptatif dans la **[!UICONTROL Source]** .
1. Sélectionnez un thème dans la **[!UICONTROL Style]** .

   ![Action Envoyer pour Workfront Fusion](/help/forms/assets/workfront-scenario-new-af.png)

1. Sélectionnez la variable **[!UICONTROL Appeler un scénario de fusion Workfront]** de la **[!UICONTROL Envoi]** .
1. Sélectionnez le webhook créé à partir du **[!UICONTROL Options]** dans le **[!UICONTROL Propriétés]** fenêtre.

   >[!NOTE]
   >
   > Le nom du webhook du scénario Workfront s’affiche dans la variable **Options** liste déroulante.

1. Cliquez sur **[!UICONTROL Créer]**.
1. Indiquez le nom de votre nouveau formulaire adaptatif, puis cliquez sur **[!UICONTROL Créer]**.

#### Configuration de l’action d’envoi du formulaire adaptatif existant pour Workfront Fusion {#existing-af-submit-action}

Pour configurer l’action d’envoi du formulaire adaptatif existant pour Workfront Fusion :

1. Connectez-vous à votre instance AEM.
1. Accédez à **[!UICONTROL Forms]** > **[!UICONTROL Forms et documents]**.
1. Sélectionnez un formulaire adaptatif et ouvrez-le en mode d’édition.
1. Ouvrez l’explorateur de contenu, puis sélectionnez le composant **[!UICONTROL Conteneur de guide]** de votre formulaire adaptatif.
1. Cliquez sur l’icône des propriétés du conteneur de guide ![Propriétés du guide](/help/forms/assets/configure-icon.svg). La fenêtre du conteneur de formulaires adaptatifs s’ouvre.

   ![Action Envoyer pour Workfront Fusion](/help/forms/assets/workfront-scenario-existing-af.png)

1. Ouvrez l’onglet **[!UICONTROL Envoi]**.
1. Sélectionnez la variable **[!UICONTROL Action Envoyer]** as **[!UICONTROL Appeler un scénario de fusion Workfront]**
1. Sélectionner **[!UICONTROL Scénario de Workfront Fusion]** dans la liste déroulante.
1. Cliquez sur **[!UICONTROL Terminé]**.

## Bonnes pratiques {#best-practices}

* Il est recommandé de choisir soigneusement votre nom de webhook, car il n’est pas possible d’obtenir le nom du scénario dans l’instance AEM. Si vous modifiez le nom du webhook à l’avenir, il n’est plus pris en compte dans la liste déroulante Action d’envoi d’AEM Forms.
* Un scénario peut comporter plusieurs liens webhook, mais à la fois, un seul lien webhook est actif. Il est recommandé de supprimer le webhook non lié afin qu’il n’apparaisse pas dans la liste déroulante Action d’envoi AEM Forms.

<!-- During testing or development of Workfront, add the Author URL to the instance URL. However, when deploying Workfront Fusion in a production environment, it is recommended to replicate the scenario URLs for the Publish instance. -->

## Articles connexes

{{af-submit-action}}