---
title: Comment intégrer Adobe Sign à AEM Forms ?
description: Découvrez comment configurer Adobe Sign pour [!DNL AEM Forms] as a Cloud Service.
feature: Adaptive Forms
role: User
level: Intermediate
exl-id: 609c3072-1c3d-43fa-898a-b4e62db8483b
source-git-commit: 28bf3e1c33def6c8a17b39a6bd9abca10faa1bd8
workflow-type: tm+mt
source-wordcount: '1024'
ht-degree: 89%

---

# Intégration d’[!DNL Adobe Sign] à [!DNL AEM Forms] as a Cloud Service  {#integrate-adobe-sign-with-aem-forms}

[!DNL Adobe Sign] permet des processus de signature électronique pour les formulaires adaptatifs. Les signatures électroniques améliorent les processus de traitement des documents pour les services juridiques, commercial, des ressources humaines, et bien d’autres domaines.

Dans un scénario [!DNL Adobe Sign] et de formulaires adaptatifs standard, un utilisateur remplit un formulaire adaptatif pour effectuer une demande de service. Par exemple, un formulaire de demande de carte de paiement et d’allocation. Lorsqu’un utilisateur remplit, envoie et signe le formulaire de demande, le formulaire est envoyé au prestataire de services qui décidera des actions à entreprise. Le prestataire de services passe en revue la demande et utilise [!DNL Adobe Sign] pour marquer la demande comme approuvée. Pour activer les workflows de signature électronique similaires, vous pouvez intégrer [!DNL Adobe Sign] à [!DNL AEM Forms].

Pour utiliser [!DNL Adobe Sign] avec [!DNL AEM Forms], configurez [!DNL Adobe Sign] dans AEM Cloud Services :

## Prérequis {#prerequisites}

Vous avez besoin des éléments suivants pour intégrer [!DNL Adobe Sign] à [!DNL AEM Forms] :

* Un compte de développeur [Adobe Sign actif](https://acrobat.adobe.com/fr/fr/sign/developer-form.html).
* Une [application API Adobe Sign](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md).
* Les informations d’identification (ID client et clé secrète client) de l’application API [!DNL Adobe Sign].
* Une [crypto-clé identique](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html?lang=fr#make-sure-you-properly-replicate-encryption-keys-when-needed) pour les instances d’auteur et de publication.
* (Uniquement pour l’authentification par ID gouvernement) [Activez la méthode d’authentification](https://helpx.adobe.com/fr/sign/using/adobesign-authentication-government-id.html#AuditReport) pour l’authentification par ID gouvernement.

## Configuration d’[!DNL Adobe Sign] avec [!DNL AEM Forms] {#configure-adobe-sign-with-aem-forms}

Une fois les prérequis réunis, procédez comme suit pour configurer [!DNL Adobe Sign] avec [!DNL AEM Forms] sur les instances d’auteur.

1. Dans l’instance d’auteur AEM Forms, accédez à **[!UICONTROL Outils]** ![hammer](assets/hammer.png) > **[!UICONTROL Général]** > **[!UICONTROL Navigateur de configuration]**.
1. Sur la page du **[!UICONTROL navigateur de configuration]**, appuyez sur **[!UICONTROL Créer]**.
1. Dans la boîte de dialogue **[!UICONTROL Créer une configuration]**, indiquez un **[!UICONTROL titre]** pour la configuration, activez **[!UICONTROL Configurations cloud]** et appuyez sur **[!UICONTROL Créer]**. Un conteneur de configurations pour Cloud Services est ainsi créé. Vérifiez que le nom du dossier ne contient aucun espace.
1. Accédez à **[!UICONTROL Outils]** ![hammer](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Sign]** et ouvrez le conteneur de configurations que vous avez créé à l’étape précédente.

   >[!NOTE]
   >
   >Lorsque vous créez un formulaire adaptatif, indiquez le nom du conteneur dans le champ **[!UICONTROL Conteneur de configurations]**.

1. Sur la page de configuration, appuyez sur **[!UICONTROL Créer]** pour créer une configuration [!DNL Adobe Sign] dans AEM Forms.
1. Dans l’onglet **[!UICONTROL Général]** de la page **[!UICONTROL Créer une configuration Adobe Sign]**, spécifiez un **[!UICONTROL nom]** de configuration et appuyez sur **[!UICONTROL Suivant]**. Vous avez la possibilité d’indiquer un **[!UICONTROL titre]** et de rechercher et sélectionner une **[!UICONTROL vignette]** pour la configuration.

1. Copiez l’URL dans la fenêtre active du navigateur dans un bloc-notes. L’URL est nécessaire pour configurer l’application [!DNL Adobe Sign] avec [!DNL AEM Forms] à une étape ultérieure. Appuyez sur **[!UICONTROL Suivant]**.

1. Dans le **[!UICONTROL Paramètres]** , **[!UICONTROL URL OAuth]** contient l’URL par défaut. Le format de l’URL est:

   `https://<shard>/public/oAuth/v2`

   Par exemple :
   `https://secure.na1.echosign.com/public/oauth/v2`

   où :

   **na1** fait référence au partitionnement de base de données par défaut. Vous pouvez modifier la valeur du partitionnement de base de données. Assurez-vous que les configurations cloud de [!DNL  Adobe Sign] pointent vers le [fragment correct](https://helpx.adobe.com/fr/sign/using/identify-account-shard.html).

   Si vous créez une autre configuration [!DNL Adobe Sign] pour une fonctionnalité ou un composant Adobe Experience Manager, assurez-vous que toutes les configurations cloud de [!DNL Adobe Sign] pointent vers le même fragment.

   >[!NOTE]
   >
   > Conserver la variable **Création d’une configuration Adobe Sign** s’ouvre. Ne le fermez pas. Vous pouvez récupérer **ID client** et **Secret du client** après la configuration des paramètres OAuth pour la variable [!DNL Adobe Sign] comme décrit dans les étapes à venir.


1. Configurez les paramètres OAuth pour l’application [!DNL Adobe Sign] :

   1. Ouvrez une fenêtre de navigateur et connectez-vous au compte de développeur [!DNL Adobe Sign].
   1. Sélectionnez l’application configurée pour [!DNL AEM Forms], puis appuyez sur **[!UICONTROL Configurer OAuth pour l’application]**.
   1. Dans le **[!UICONTROL URL de redirection]** , ajoutez l’URL copiée lors d’une étape précédente (étape 7) et cliquez sur **[!UICONTROL Enregistrer]**.
   1. Activez la portée suivante pour la variable [!DNL Adobe Sign] application et cliquez sur **[!UICONTROL Enregistrer]**.
   * [!DNL aggrement_read]
   * [!DNL aggrement_write]
   * [!DNL aggrement_send]
   * [!DNL widget_read]
   * [!DNL widget_write]
   * [!DNL workflow_read]

   Pour obtenir des informations détaillées sur la configuration des paramètres OAuth pour une application [!DNL Adobe Sign] et l’obtention des clés, voir [Configurer les paramètres oAuth pour l’application](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md) dans la documentation du développeur.

   ![Configuration OAuth](assets/oauthconfig_new.png)

1. Revenez à la page **[!UICONTROL Créer une configuration Adobe Sign]**. Spécifiez le [**[!UICONTROL ID client]** (également appelé ID d’application) et **[!UICONTROL Secret du client]**]. Utilisez la variable [ID client et secret client de l’application Adobe Sign](https://opensource.adobe.com/acrobat-sign/developer_guide/helloworld.html#get-the-app-id-and-secret) vous avez créé à l’étape précédente.

1. Sélectionnez l’option **[!UICONTROL Activer Adobe Sign pour les pièces jointes]** pour ajouter les fichiers joints à un formulaire adaptatif au document [!DNL Adobe Sign] correspondant envoyé à des fins de signature.

1. Appuyez sur **[!UICONTROL Se connecter à Adobe Sign]**. Lorsque vous êtes invité à fournir vos informations d’identification, indiquez le nom d’utilisateur et le mot de passe du compte utilisé lors de la création de l’application [!DNL Adobe Sign]. Lorsque vous êtes invité à confirmer l’accès à `your developer account`, cliquez sur **[!UICONTROL Autoriser l’accès]**. Si les informations d’identification sont correctes et que vous autorisez [!DNL AEM Forms] à accéder à votre compte de développeur [!DNL Adobe Sign], un message, semblable à celui ci-dessous, s’affiche pour vous notifier le succès de l’opération.

   ![Succès de la configuration Adobe Sign Cloud](assets/adobe-sign-cloud-configuration-success.png)

1. Appuyez sur **[!UICONTROL Créer]** pour créer la configuration [!DNL Adobe Sign].

1. Sélectionnez la configuration, cliquez sur **[!UICONTROL Publier]**, sélectionnez la configuration, puis cliquez sur **[!UICONTROL Publier]**. La configuration sera ainsi répliquée sur les environnements de publication correspondants.

1. Répétez toutes les étapes ci-dessus sur vos instances de développement, d’évaluation ou de production (toutes celles non encore configurées) pour terminer la configuration d’[!DNL Adobe Sign] avec [!DNL AEM Forms] pour votre environnement.

Vous pouvez maintenant [utiliser l’ajout de champs Adobe Sign à un formulaire adaptatif](working-with-adobe-sign.md). Veillez à ajouter le conteneur de configurations utilisé pour Cloud Service à tous les formulaires adaptatifs activés pour [!DNL Adobe Sign]. Vous pouvez spécifier un conteneur de configurations à partir des propriétés d’un formulaire adaptatif.

## (Pour les workflows AEM uniquement) Configurez le planificateur [!DNL Adobe Sign] pour synchroniser le statut de la signature {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

Lorsque vous utilisez l’étape de processus [!DNL Adobe Sign] pour signer un formulaire adaptatif, le formulaire peut être transmis aux signataires l’un après l’autre ou envoyé à tous les signataires simultanément, selon la configuration de l’étape de processus. Les formulaires adaptatifs avec [!DNL Adobe Sign] activé ne sont envoyés à Experience Manager Forms Server qu’une fois que tous les signataires ont terminé le processus de signature.

Par défaut, les services de Planificateur [!DNL Adobe Sign] vérifient la réponse du signataire (sondages) toutes les 24 heures. Vous pouvez modifier l’intervalle par défaut pour votre environnement.

Pour modifier l’intervalle par défaut, spécifiez une [expression cron](https://en.wikipedia.org/wiki/Cron#CRON_expression) pour la propriété **sign.status.exp** de la configuration **Service de configuration Adobe Sign**.

Par exemple, pour exécuter le service de configuration tous les jours à 00:00, définissez la propriété **sign.status.exp** de la configuration **Service de configuration Adobe Sign** pour spécifier `0 0 0 1/1 * ? *`. Le fichier JSON suivant affiche l’échantillon d’exécution du service de configuration tous les jours à 00:00 :

```json
{
  "sign.status.exp":"0 0 0 1/1 * ? *"
}
```

Pour définir les valeurs d’une configuration, [générez des configurations OSGi à l’aide du SDK AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=fr#generating-osgi-configurations-using-the-aem-sdk-quickstart) et [déployez la configuration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=fr#deployment-process) sur votre instance de Cloud Service.

<!-- , perform the following steps:

1. Log in to [!DNL AEM Forms] Server with admin credentials and navigate to **[!UICONTROL Tools]** &gt;**[!UICONTROL Operations]** &gt; **[!UICONTROL Web Console]**.

   You can also open the following URL in a browser window:
   `https://server/system/console/configMgr`

1. Locate and open the **[!UICONTROL Adobe Sign Configuration Service]** option. Specify a [cron expression](https://en.wikipedia.org/wiki/Cron#CRON_expression) in the **Status Update Scheduler Expression** field and click **Save**. For example, to run the configuration service daily at 00:00 am, specify `0 0 0 1/1 * ? *` in the **Status Update Scheduler Expression** field.

Default interval to sync status of [!DNL Adobe Sign] is now changed. -->

## Articles connexes {#related-articles}

* [Utilisation d’Adobe Sign dans un formulaire adaptatif](working-with-adobe-sign.md)

* [Recommandations relatives à l’utilisation d’Adobe Sign avec des formulaires adaptatifs](https://medium.com/adobetech/using-adobe-sign-to-e-sign-an-adaptive-form-heres-the-best-way-to-do-it-dc3e15f9b684)
