---
title: Comment intégrer Adobe Acrobat Sign à AEM Forms ?
description: Découvrez comment configurer Adobe Acrobat Sign pour [!DNL AEM Forms] as a Cloud Service ?
feature: Adaptive Forms
role: User
level: Intermediate
source-git-commit: b6dcb6308d1f4af7a002671f797db766e5cfe9b5
workflow-type: tm+mt
source-wordcount: '1939'
ht-degree: 46%

---

# Connexion [!DNL AEM Forms] as a Cloud Service avec [!DNL Adobe Acrobat Sign] {#integrate-adobe-sign-with-aem-forms}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/adobe-sign-integration-adaptive-forms.html#adobe-acrobat-sign-for-government) |
| AEM as a Cloud Service | Cet article |

[!DNL Adobe Acrobat Sign] active les processus de signature électronique pour les processus Forms adaptatifs et AEM. Les signatures électroniques améliorent les processus de traitement des documents pour les services juridiques, commercial, des ressources humaines, et bien d’autres domaines.

Dans un scénario [!DNL Adobe Acrobat Sign] et de formulaires adaptatifs standard, un utilisateur remplit un formulaire adaptatif pour effectuer une demande de service. Par exemple, un formulaire de demande de carte bancaire et d’allocation. Lorsqu’un utilisateur remplit, envoie et signe le formulaire de demande, le formulaire est envoyé au fournisseur de services pour qu’il prenne d’autres mesures. Le prestataire de services passe en revue la demande et utilise [!DNL Adobe Acrobat Sign] pour marquer la demande comme approuvée. AEM Forms prend en charge Adobe Acrobat Sign et Adobe Acrobat Sign Solutions pour l’administration. En fonction de votre licence et de vos exigences, vous pouvez intégrer ou connecter AEM Forms à l’une des solutions suivantes :

* [Connexion d’AEM Forms à Adobe Acrobat Sign](#adobe-sign)
* [Connexion d’AEM Forms à Adobe Acrobat Sign Solutions for Government](#adobe-acrobat-sign-for-government)

## Connexion d’AEM Forms à Adobe Acrobat Sign {#adobe-sign}

Pour se connecter **[!DNL AEM Forms]** avec **[!DNL Adobe Acrobat Sign]**, configurez le logiciel et les comptes répertoriés dans la section Conditions préalables et configurez Adobe Sign Cloud Service dans vos instances Forms as a Cloud Service Author and Publish :

### Conditions préalables à la connexion d’AEM Forms à Adobe Acrobat Sign {#prerequisites-for-adobe-sign}

Vous avez besoin de la configuration suivante pour intégrer [!DNL Adobe Acrobat Sign] avec [!DNL AEM Forms]:

1. Une principale [Compte de développeur Adobe Acrobat Sign](https://acrobat.adobe.com/fr/fr/sign/developer-form.html).
1. Un [Application d’API Adobe Acrobat Sign](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md).
1. Les informations d’identification (ID client et clé secrète client) de l’application API [!DNL Adobe Acrobat Sign].
1. (Uniquement pour l’authentification par ID de gouvernement) [Activation de la méthode d’authentification](https://helpx.adobe.com/fr/sign/using/adobesign-authentication-government-id.html#AuditReport) pour l’authentification des ID de gouvernement.



### Connexion des instances d’auteur et de publication AEM Forms à Adobe Acrobat Sign {#configure-adobe-sign-with-aem-forms}

Une fois les prérequis réunis, procédez comme suit pour configurer [!DNL Adobe Acrobat Sign] avec [!DNL AEM Forms] sur les instances d’auteur.

1. Dans l’instance d’auteur AEM Forms, accédez à **[!UICONTROL Outils]** ![hammer](assets/hammer.png) > **[!UICONTROL Général]** > **[!UICONTROL Navigateur de configuration]**.
1. Sur la page du **[!UICONTROL navigateur de configuration]**, appuyez sur **[!UICONTROL Créer]**.
1. Dans la boîte de dialogue **[!UICONTROL Créer une configuration]**, indiquez un **[!UICONTROL titre]** pour la configuration, activez **[!UICONTROL Configurations cloud]** et appuyez sur **[!UICONTROL Créer]**. Un conteneur de configurations pour Cloud Services est ainsi créé. Vérifiez que le nom du dossier ne contient aucun espace.
1. Accédez à **[!UICONTROL Outils]** ![marteau](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Acrobat Sign]** et ouvrez le conteneur de configuration que vous avez créé à l’étape précédente.

   >[!NOTE]
   >
   >Lorsque vous créez un formulaire adaptatif, indiquez le nom du conteneur dans le champ **[!UICONTROL Conteneur de configurations]**.

1. Sur la page de configuration, appuyez sur **[!UICONTROL Créer]** pour créer une configuration [!DNL Adobe Acrobat Sign] dans AEM Forms.
1. Dans le **[!UICONTROL Général]** de l’onglet **[!UICONTROL Création d’une configuration Adobe Acrobat Sign]** , spécifiez une **[!UICONTROL Nom]** pour la configuration, appuyez sur **[!UICONTROL Suivant]**. Vous avez la possibilité d’indiquer un **[!UICONTROL titre]** et de rechercher et sélectionner une **[!UICONTROL vignette]** pour la configuration.

1. Maintenant, vous pouvez **[!UICONTROL Sélectionner une solution]** pour sélectionner [!DNL Adobe Acrobat Sign].

   ![Adobe Acrobat Sign Solutions for Government](assets/adobe-sign-solution.png)

1. Copiez l’URL présente dans la fenêtre de votre navigateur actuel dans un bloc-notes et supprimez la partie `/ui#/aem` de l’URL. L’URL modifiée est alors requise pour configurer [!DNL Adobe Acrobat Sign] application avec [!DNL AEM Forms], à une étape ultérieure. Appuyez sur **[!UICONTROL Suivant]**.

1. Dans l’onglet **[!UICONTROL Paramètres]**, le champ **[!UICONTROL URL OAuth]** contient l’URL par défaut. Le format de l’URL est:

   `https://<shard>/public/oAuth/v2`

   Par exemple :
   `https://secure.na1.echosign.com/public/oauth/v2`

   où :

   **na1** fait référence au partitionnement de base de données par défaut. Vous pouvez modifier la valeur du partitionnement de base de données. Assurez-vous que les configurations cloud de [!DNL  Adobe Acrobat Sign] pointent vers le [fragment correct](https://helpx.adobe.com/fr/sign/using/identify-account-shard.html).

   Si vous créez une autre configuration [!DNL Adobe Acrobat Sign] pour une fonctionnalité ou un composant Adobe Experience Manager, assurez-vous que toutes les configurations cloud de [!DNL Adobe Acrobat Sign] pointent vers le même fragment.

   >[!NOTE]
   >
   > Conserver la variable **Création d’une configuration Adobe Acrobat Sign** s’ouvre. Ne la fermez pas. Vous pouvez récupérer l’**ID client** et le **secret client** après la configuration des paramètres OAuth pour l’application [!DNL Adobe Acrobat Sign] comme décrit dans les étapes à venir.


1. Configurez les paramètres OAuth pour l’application [!DNL Adobe Acrobat Sign] :

   1. Ouvrez une fenêtre de navigateur et connectez-vous au compte de développeur [!DNL Adobe Acrobat Sign].
   1. Sélectionnez l’application configurée pour [!DNL AEM Forms], puis appuyez sur **[!UICONTROL Configurer OAuth pour l’application]**.
   1. Dans la zone **[!UICONTROL URL de redirection]**, ajoutez l’URL copiée à l’étape précédente (étape 8) et cliquez sur **[!UICONTROL Enregistrer]**.
   1. Activez la Portée suivante pour l’application [!DNL Adobe Acrobat Sign] et cliquez sur **[!UICONTROL Enregistrer]**.

   * [!DNL aggrement_read]
   * [!DNL aggrement_write]
   * [!DNL aggrement_send]
   * [!DNL widget_read]
   * [!DNL widget_write]
   * [!DNL workflow_read]

   Pour obtenir des informations détaillées sur la configuration des paramètres OAuth pour une application [!DNL Adobe Acrobat Sign] et l’obtention des clés, voir [Configurer les paramètres oAuth pour l’application](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md) dans la documentation du développeur.

   ![Configuration OAuth](assets/oauthconfig_new.png)

1. Revenez au **[!UICONTROL Création d’une configuration Adobe Acrobat Sign]** page. Dans l’onglet **[!UICONTROL Paramètres]**, spécifiez l’[**[!UICONTROL ID client]**(également appelé ID de l’application) et le **[!UICONTROL Secret client]**]. Utilisez la variable [ID client et secret client de l’application Adobe Acrobat Sign](https://opensource.adobe.com/acrobat-sign/developer_guide/helloworld.html#get-the-app-id-and-secret) vous avez créé à l’étape précédente.

1. Sélectionnez la **[!UICONTROL Activation de Adobe Acrobat Sign pour les pièces jointes]** option pour ajouter les fichiers joints à un formulaire adaptatif à la [!DNL Adobe Acrobat Sign] document envoyé pour signature.

1. Appuyer **[!UICONTROL Connexion à Adobe Acrobat Sign]**. Lorsque vous êtes invité à saisir des informations d’identification, saisissez **username** et **password** du compte utilisé lors de la création [!DNL Adobe Acrobat Sign] application. Lorsque vous êtes invité à confirmer, accédez à `your developer account`, cliquez sur **[!UICONTROL Autoriser l’accès]**. Si les informations d’identification sont correctes et que vous autorisez [!DNL AEM Forms] à accéder à votre compte de développeur [!DNL Adobe Acrobat Sign], un message, semblable à celui ci-dessous, s’affiche pour vous notifier le succès de l’opération.

   ![Succès de la configuration du cloud Adobe Acrobat Sign](assets/adobe-sign-cloud-configuration-success.png)

1. Appuyez sur **[!UICONTROL Créer]** pour créer la configuration [!DNL Adobe Acrobat Sign].

1. Sélectionnez la configuration, cliquez sur **[!UICONTROL Publier]**, sélectionnez la configuration, puis cliquez sur **[!UICONTROL Publier]**. La configuration sera ainsi répliquée sur les environnements de publication correspondants.

1. Répétez toutes les étapes ci-dessus sur vos instances de développement, d’évaluation ou de production (toutes celles non encore configurées) pour terminer la configuration d’[!DNL Adobe Acrobat Sign] avec [!DNL AEM Forms] pour votre environnement.

Maintenant, vous pouvez [Utilisation de l’ajout de champs Adobe Acrobat Sign à un formulaire adaptatif](working-with-adobe-sign.md). Veillez à ajouter le conteneur de configurations utilisé pour Cloud Service à tous les formulaires adaptatifs activés pour [!DNL Adobe Acrobat Sign]. Vous pouvez spécifier un conteneur de configurations à partir des propriétés d’un formulaire adaptatif.

## Connexion d’AEM Forms à Adobe Acrobat Sign Solutions for Government {#adobe-acrobat-sign-for-government}

La connexion d’AEM Forms à Adobe Acrobat Sign Solutions for Government est un processus en plusieurs étapes. Cela implique :

* Création de l’URL de redirection pour vos instances AEM
* Partage de l’URL de redirection et des portées avec les solutions Adobe Sign pour l’équipe gouvernementale
* Réception des informations d’identification de l’équipe Adobe Sign
* Utilisation des informations d’identification reçues pour connecter AEM Forms à Adobe Acrobat Sign Solutions for Government

![](/help/forms/assets/adobe-acrobat-sign-govt-workflow.png)


AEM Forms as a Cloud Service fournit des environnements de développement, d’évaluation et de production. Vous pouvez commencer par connecter votre environnement de développement pour avec Adobe Acrobat Sign Solutions for Government et connecter ultérieurement les environnements intermédiaire et de production.

### Avant de commencer {#prerequisites-for-adobe-sign-for-acrobat-sign-for-government}

Avant de commencer à connecter AEM Forms à la solution Adobe Acrobat Sign, assurez-vous que la variable [Adobe Acrobat Sign Solutions for Government](https://opensource.adobe.com/acrobat-sign/signgov/gstarted.html#account-provisioning) est configuré.


### Connexion d’AEM Forms as a Cloud Service à Adobe Acrobat Sign Solutions for Government {#connect-adobe-acrobat-sign-for-government}

#### Création d’une URL de redirection pour votre instance AEM

1. Sur l’instance de création as a Cloud Service Forms, accédez à **[!UICONTROL Outils]** ![marteau](assets/hammer.png) > **[!UICONTROL Général]** > **[!UICONTROL Explorateur de configuration]**.
1. Sur la page du **[!UICONTROL navigateur de configuration]**, appuyez sur **[!UICONTROL Créer]**.
1. Dans la boîte de dialogue **[!UICONTROL Créer une configuration]**, indiquez un **[!UICONTROL titre]** pour la configuration, activez **[!UICONTROL Configurations cloud]** et appuyez sur **[!UICONTROL Créer]**. Un conteneur de configurations pour Cloud Services est ainsi créé. Vérifiez que le nom du dossier ne contient aucun espace.
1. Accédez à **[!UICONTROL Outils]** ![marteau](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Acrobat Sign]** et ouvrez le conteneur de configuration que vous avez créé à l’étape précédente. Lorsque vous créez un formulaire adaptatif, indiquez le nom du conteneur dans le champ **[!UICONTROL Conteneur de configurations]**.
1. Sur la page de configuration, appuyez sur **[!UICONTROL Créer]** pour créer une configuration [!DNL Adobe Acrobat Sign] dans AEM Forms.
1. Copiez l’URL de la fenêtre de votre navigateur actuel dans un bloc-notes et supprimez `/ui#/aem` de l’URL. Cette URL est appelée `re-direct URL`. Dans la section suivante, vous partagez la variable `re-direct URL` et `Scopes` avec l’équipe Adobe Sign et demandez des informations d’identification (identifiant client et secret client).


#### Partage de l’URL de redirection et des portées avec l’équipe Adobe Sign et réception des informations d’identification

L’équipe Adobe Acrobat Sign for Government Solutions a besoin des `re-direct URL` et les portées spécifiques à activer pour votre application Adobe Acrobat Sign (répertoriées ci-dessous) pour générer les informations d’identification (identifiant client et secret client) qui vous permettent de connecter AEM Forms à Adobe Acrobat Sign Solutions for Government.

Partagez la variable `scopes` (répertoriés ci-dessous) et la variable `re-direct URL` créé et noté à la dernière étape de la section précédente avec votre représentant de solution Adobe Acrobat Sign for Government ([membre de l’équipe Adobe Professional Services](https://opensource.adobe.com/acrobat-sign/signgov/gstarted.html#password)).

**_Portées_**

* [!DNL aggrement_read]
* [!DNL aggrement_write]
* [!DNL aggrement_send]
* [!DNL widget_read]
* [!DNL widget_write]
* [!DNL workflow_read]
* [!DNL offline_access]

Le représentant génère et partage des informations d’identification avec vous. Dans la section suivante, vous utilisez les informations d’identification (ID client et secret client) pour connecter AEM Forms à Adobe Acrobat Sign Solutions for Government.

#### Utilisez les informations d’identification reçues pour connecter AEM Forms à Adobe Acrobat Sign Solutions for Government

1. Ouvrez le `re-direct URL` dans votre navigateur. Vous avez créé et noté la variable `re-direct URL` dans la dernière étape de la [créer une URL de redirection sur votre instance AEM](#create-redirect-url) .

1. Dans l’onglet **[!UICONTROL Général]** de la page **[!UICONTROL Créer une configuration Adobe Sign]**, spécifiez un **[!UICONTROL nom]** de configuration et appuyez sur **[!UICONTROL Suivant]**. Vous avez la possibilité d’indiquer un **[!UICONTROL titre]** et de rechercher et sélectionner une **[!UICONTROL vignette]** pour la configuration. Cliquez sur **[!UICONTROL Suivant]**.

1. Dans le **[!UICONTROL Paramètres]** de l’onglet **[!UICONTROL Création d’une configuration Adobe Sign]** , pour la **[!UICONTROL Sélectionner une solution]** option, sélectionnez [!DNL Adobe Acrobat Sign Solutions for Government].

   ![Adobe Acrobat Sign Solutions for Government](assets/adobe-sign-for-govt.png)

1. Dans le **[!UICONTROL Email]** , indiquez l’adresse électronique associée à votre compte Adobe Acrobat Sign Solutions for Government.

1. Le **[!UICONTROL URL OAuth]** spécifie le partage de base de données Adobe Sign. Le champ contient l’URL par défaut. Ne modifiez pas l’URL.

1. Utilisez les informations d’identification partagées par Adobe Acrobat Sign pour le représentant de la solution gouvernementale ([membre de l’équipe Adobe Professional Services]) de la section précédente en tant que [**[!UICONTROL ID client]** et **[!UICONTROL Secret du client]**].

1. Sélectionnez la **[!UICONTROL Activation de Adobe Acrobat Sign pour les pièces jointes]** option pour ajouter les fichiers joints à un formulaire adaptatif à la [!DNL Adobe Acrobat Sign] document envoyé pour signature.

1. Appuyez sur **[!UICONTROL Se connecter à Adobe Sign]**. Lorsque vous êtes invité à fournir vos informations d’identification, indiquez le nom d’utilisateur et le mot de passe du compte utilisé lors de la création de l’application [!DNL Adobe Acrobat Sign]. Lorsque vous êtes invité à confirmer l’accès à `your developer account`, cliquez sur **[!UICONTROL Autoriser l’accès]**. Si les informations d’identification sont correctes et que vous autorisez [!DNL AEM Forms] à accéder à votre compte de développeur [!DNL Adobe Acrobat Sign], un message, semblable à celui ci-dessous, s’affiche pour vous notifier le succès de l’opération.

   ![Succès de la configuration du cloud Adobe Acrobat Sign](assets/adobe-sign-cloud-configuration-success.png)

   <!-- > When prompted for credentials, provide username and password of the account used while creating [!DNL Adobe Acrobat Sign] application. When asked to confirm access for `your developer account`, Click **[!UICONTROL Allow Access]**. -->

1. Appuyez sur **[!UICONTROL Créer]** pour créer la configuration .

1. Sélectionnez la configuration, cliquez sur **[!UICONTROL Publier]**, sélectionnez la configuration, puis cliquez sur **[!UICONTROL Publier]**. Elle réplique la configuration dans les environnements de publication correspondants.

1. Répétez toutes les étapes ci-dessus sur vos instances de développement, d’évaluation ou de production (toutes celles non encore configurées) pour terminer la configuration d’[!DNL Adobe Acrobat Sign Solutions for Government] avec [!DNL AEM Forms] pour votre environnement.

Maintenant, vous pouvez [utiliser l’ajout de champs Adobe Acrobat Sign dans un formulaire adaptatif ;](working-with-adobe-sign.md) ou [Processus AEM](/help/forms/aem-forms-workflow-step-reference.md#sign-document-step-sign-document-step). Assurez-vous d’ajouter le conteneur de configuration utilisé pour la configuration du Cloud Service à toutes les Forms adaptatives activées pour [!DNL Adobe Acrobat Sign]. Vous pouvez spécifier un conteneur de configurations à partir des propriétés d’un formulaire adaptatif.

## (Pour les workflows AEM uniquement) Configurez le planificateur [!DNL Adobe Acrobat Sign] pour synchroniser le statut de la signature {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

Lorsque vous utilisez l’étape de processus [!DNL Adobe Acrobat Sign] pour signer un formulaire adaptatif, le formulaire peut être transmis aux signataires l’un après l’autre ou envoyé à tous les signataires simultanément, selon la configuration de l’étape de processus. Les formulaires adaptatifs avec [!DNL Adobe Acrobat Sign] activé ne sont envoyés à Experience Manager Forms Server qu’une fois que tous les signataires ont terminé le processus de signature.

Par défaut, les services de Planificateur [!DNL Adobe Acrobat Sign] vérifient la réponse du signataire (sondages) toutes les 24 heures. Vous pouvez modifier l’intervalle par défaut pour votre environnement.

Pour modifier l’intervalle par défaut, spécifiez une [expression cron](https://en.wikipedia.org/wiki/Cron#CRON_expression) pour le **sign.status.exp** de la propriété **Service de configuration Adobe Acrobat Sign** configuration.

Par exemple, pour exécuter le service de configuration tous les jours à 00 h 00, définissez la variable **sign.status.exp** de la propriété **Service de configuration Adobe Acrobat Sign** configuration à spécifier `0 0 0 1/1 * ? *`. Le fichier JSON suivant affiche l’échantillon d’exécution du service de configuration tous les jours à 00:00 :

```json
{
  "sign.status.exp":"0 0 0 1/1 * ? *"
}
```

Pour définir les valeurs d’une configuration, [générez des configurations OSGi à l’aide du SDK AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=fr#generating-osgi-configurations-using-the-aem-sdk-quickstart) et [déployez la configuration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=fr#deployment-process) sur votre instance de Cloud Service.


## Articles connexes {#related-articles}

* [Utilisation de Adobe Acrobat Sign dans un formulaire adaptatif](working-with-adobe-sign.md)

* [Bonnes pratiques relatives à l’utilisation de Adobe Acrobat Sign avec Forms adaptatif](https://medium.com/adobetech/using-adobe-sign-to-e-sign-an-adaptive-form-heres-the-best-way-to-do-it-dc3e15f9b684)
