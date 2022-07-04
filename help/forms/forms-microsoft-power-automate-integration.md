---
title: Intégration d’un formulaire adaptatif à Microsoft® Power Automate
description: Intégrer un formulaire adaptatif à Microsoft® Power Automate.
hide: true
hidefromtoc: true
exl-id: a059627b-df12-454d-9e2c-cc56986b7de6
source-git-commit: ccc4d487cb180273284276cf9cdf18680a3efcb8
workflow-type: tm+mt
source-wordcount: '1183'
ht-degree: 10%

---

# Connexion d’un formulaire adaptatif à Microsoft® Power Automate {#connect-adaptive-form-with-power-automate}

Vous pouvez configurer un formulaire adaptatif pour exécuter un flux cloud Microsoft® Power Automate Cloud lors de l’envoi. Le formulaire adaptatif configuré envoie les données, les pièces jointes et le document d’enregistrement capturés à Power Automate Cloud Flow pour traitement. Il vous permet de créer une expérience de capture de données personnalisée tout en tirant parti de la puissance de Microsoft® Power Automate pour élaborer des logiques commerciales autour des données capturées et automatiser les workflows client. Voici quelques exemples de ce que vous pouvez faire après l’intégration d’un formulaire adaptatif à Microsoft® Power Automate :

* Utilisation de données Forms adaptatives dans des processus d’entreprise Power Automate
* Utilisez Power Automate pour envoyer des données capturées à plus de 500 sources de données ou à toute API publique
* Exécution de calculs complexes sur les données capturées
* Enregistrement des données de Forms adaptatives dans les systèmes de stockage selon un calendrier prédéfini

L’éditeur de Forms adaptatif fournit la variable **Appeler un flux Microsoft® Power Automate** Les actions d’envoi pour envoyer des données de formulaires adaptatifs, des pièces jointes et un document d’enregistrement sont envoyées à Power Automate Cloud Flow. Pour utiliser l’action Envoyer afin d’envoyer les données capturées à Microsoft® Power Automate, [Connexion de votre instance Forms as a Cloud Service à Microsoft® Power Automate](forms-microsoft-power-automate-integration.md#connect-forms-server-with-power-automate)

## Prérequis

Les éléments suivants sont requis pour connecter un formulaire adaptatif à Microsoft® Power Automate :

* Licence Microsoft® Power Automate Premium.
* Microsoft® [Flux de Power Automate](https://docs.microsoft.com/en-us/power-automate/create-flow-solution) avec le `When an HTTP request is received` pour accepter les données d’envoi de formulaire adaptatif.


* Utilisateur Experience Manager disposant de droits d’auteur Forms et d’administrateur Forms.
* Assurez-vous que le compte utilisé pour se connecter à Power Automate est le propriétaire du flux Power Automate.


## Connexion de votre instance Forms as a Cloud Service à Microsoft® Power Automate {#connect-forms-server-with-power-automate}

Effectuez les actions suivantes pour connecter votre instance Forms as a Cloud Service à Microsoft® Power Automate :

1. Création d’une application Microsoft® Azure Principale Directory
1. Créez la configuration du cloud Microsoft® Power Automate Dataverse Cloud.
1. Création de la configuration cloud du service de flux de Microsoft® Power Automate
1. Publiez la configuration du cloud Microsoft® Power Automate Dataverse.

### Création d’une application Microsoft® Azure Principale Directory {#ms-power-automate-application}

1. Connectez-vous à [Portail Azure](https://portal.azure.com/).
1. Sélectionner [!UICONTROL Azure Principal Directory] dans le volet de navigation de gauche.
1. Sur la page Répertoire par défaut , sélectionnez [!UICONTROL Inscriptions des applications] dans le panneau de gauche.
1. Sur la page Inscriptions de l’application, cliquez sur Nouvelles inscriptions.
1. Spécifiez le nom, les types de compte pris en charge et l’URI de redirection sur la page. Dans l’URI de redirection, spécifiez ce qui suit et cliquez sur Enregistrer.
   * `https://[Forms as a Cloud Service Server]/libs/fd/powerautomate/content/dataverse/config.html`
   * `https://[Forms as a Cloud Service Server]/libs/fd/powerautomate/content/flowservice/config.html`

   ![Enregistrement d’une application Azure Principale Directory](assets/power-automate-application.png)

   >[!NOTE]
   >Vous pouvez également spécifier des URI de redirection supplémentaires, si nécessaire, à partir de la page Authentification .
   > Pour les types de compte pris en charge, sélectionnez un client unique, plusieurs clients ou un compte Microsoft personnel, selon votre cas d’utilisation.


1. Sur la page Authentification , activez les options suivantes, puis cliquez sur Enregistrer.


   * Jetons d’accès (utilisés pour les flux implicites)
   * Jetons d’ID (utilisés pour les flux implicites et hybrides)

1. Sur la page des autorisations d’API, cliquez sur Ajouter une autorisation.
1. Sous API Microsoft®, sélectionnez le service de flux, puis les autorisations suivantes.
   * Flows.Manage.All
   * Flows.Read.All

   Cliquez sur Ajouter des autorisations pour enregistrer les autorisations.
1. Sur la page des autorisations d’API, cliquez sur Ajouter une autorisation. Sélectionner les API utilisées par mon entreprise et effectuer des recherches `DataVerse`.
1. Activez user_impersonation et cliquez sur Ajouter des autorisations.
1. (Facultatif) Sur la page Certificats et secrets, cliquez sur Nouveau secret client. Dans l’écran Ajouter un secret client, fournissez une description et un délai d’expiration du secret, puis cliquez sur Ajouter. Une chaîne secrète est générée.
1. Conserver une note spécifique à votre organisation [URL de l’environnement Dynamics](https://docs.microsoft.com/en-us/power-automate/web-api#compose-http-requests).

### Création d’une configuration Microsoft® Power Automate Dataverse Cloud {#microsoft-power-automate-dataverse-cloud-configuration}

1. Dans l’instance d’auteur AEM Forms, accédez à **[!UICONTROL Outils]** ![hammer](assets/hammer.png) > **[!UICONTROL Général]** > **[!UICONTROL Navigateur de configuration]**.
1. Sur la page du **[!UICONTROL navigateur de configuration]**, appuyez sur **[!UICONTROL Créer]**.
1. Dans la boîte de dialogue **[!UICONTROL Créer une configuration]**, indiquez un **[!UICONTROL titre]** pour la configuration, activez **[!UICONTROL Configurations cloud]** et appuyez sur **[!UICONTROL Créer]**. Un conteneur de configurations pour Cloud Services est ainsi créé. Vérifiez que le nom du dossier ne contient aucun espace.
1. Accédez à **[!UICONTROL Outils]** ![marteau](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Microsoft® Power Automate Dataverse]** et ouvrez le conteneur de configuration que vous avez créé à l’étape précédente.

   >[!NOTE]
   >
   >Lorsque vous créez un formulaire adaptatif, indiquez le nom du conteneur dans le champ **[!UICONTROL Conteneur de configurations]**.
1. Sur la page de configuration, appuyez sur **[!UICONTROL Créer]** pour créer une configuration [!DNL Microsoft® Power Automate Flow Service] dans AEM Forms.
1. Sur le **[!UICONTROL Configuration du service Dataverse pour Microsoft® Power Automate]** , indiquez la variable **[!UICONTROL ID client]** (également appelé ID d’application), **[!UICONTROL Secret du client]**, **[!UICONTROL URL OAuth]** et **[!UICONTROL URL de l’environnement dynamique]**. Utilisez l’ID client, le secret client, l’URL OAuth et l’URL de l’environnement dynamique de [Microsoft® Azure Principale Directory Application](#ms-power-automate-application) vous avez créé dans la section précédente. Utilisez l’option Points de fin dans l’interface utilisateur de l’application Microsoft® Azure Principale Directory pour trouver l’URL OAuth.

![Utiliser l’option Points de fin dans l’interface utilisateur de l’application Microsoft Power Automate pour rechercher l’URL OAuth](assets/endpoints.png)
Utiliser l’option Points de fin dans l’interface utilisateur de l’application Microsoft® Power Automate pour rechercher l’URL OAuth

1. Appuyer **[!UICONTROL Connexion]** . Si vous y êtes invité, connectez-vous à votre compte Microsoft® Azure. Appuyez sur **[!UICONTROL Enregistrer]**.

### Créez la configuration du cloud de service de flux de production de Microsoft® Power Automate.

1. Accédez à **[!UICONTROL Outils]** ![marteau](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Service de flux Microsoft® Power Automate]** et ouvrez le conteneur de configuration que vous avez créé dans la section précédente.

   >[!NOTE]
   >
   >Lorsque vous créez un formulaire adaptatif, indiquez le nom du conteneur dans le champ **[!UICONTROL Conteneur de configurations]**.
1. Sur la page de configuration, appuyez sur **[!UICONTROL Créer]** pour créer une configuration [!DNL Microsoft® Power Automate Flow Service] dans AEM Forms.
1. Sur le **[!UICONTROL Configuration de Dataverse pour Microsoft® Power Automate]** , indiquez la variable **[!UICONTROL ID client]** (également appelé ID d’application), **[!UICONTROL Secret du client]**, **[!UICONTROL URL OAuth]** et **[!UICONTROL URL de l’environnement dynamique]**. Utilisez l’ID client, le secret client, l’URL OAuth et l’ID d’environnement Dynamics. Utilisez l’option Points de fin dans l’interface utilisateur de l’application Microsoft® Azure Principale Directory pour trouver l’URL OAuth. Ouvrez le [Mes flux](https://us.flow.microsoft.com) et appuyez sur Mes flux pour utiliser l’identifiant répertorié dans l’URL en tant qu’identifiant d’environnement Dynamics.
1. Appuyer **[!UICONTROL Connexion]**. Si vous y êtes invité, connectez-vous à votre compte Microsoft® Azure. Appuyez sur **[!UICONTROL Enregistrer]**.

### Publiez les configurations cloud Microsoft® Power Automate Dataverse et Microsoft® Power Automate Flow Service {#publish-microsoft-power-automate-dataverse-cloud-configuration}

1. Accédez à **[!UICONTROL Outils]** ![marteau](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Microsoft® Power Automate Dataverse]** et ouvrez le conteneur de configuration que vous avez créé lors de la précédente [Création d’une configuration Microsoft® Power Automate Dataverse Cloud](#microsoft-power-automate-dataverse-cloud-configuration) .
1. Sélectionnez la `dataverse` configuration et appuyez sur **[!UICONTROL Publier]**.
1. Sur la page Publier, sélectionnez **[!UICONTROL Toutes les configurations]** et appuyez sur **[!UICONTROL Publier]**. Publiez les configurations cloud de Power Automate Dataverse et Power Automate Flow Service.

Votre instance Forms as a Cloud Service est maintenant connectée à Microsoft® Power Automate. Vous pouvez désormais envoyer des données de Forms adaptatif à un flux Power Automate.

## Utilisez l’action d’envoi Appeler un flux Microsoft® Power Automate pour envoyer des données à un flux d’automatisation Power Automate. {#use-the-invoke-microsoft-power-automate-flow-submit-action}

Après vous [Connexion de votre instance Forms as a Cloud Service à Microsoft® Power Automate](#connect-forms-server-with-power-automate), effectuez l’action suivante pour configurer votre formulaire adaptatif afin d’envoyer les données capturées à un flux Microsoft® lors de l’envoi du formulaire.

1. Connectez-vous à votre instance d’auteur, sélectionnez votre formulaire adaptatif et cliquez sur **[!UICONTROL Propriétés]**.
1. Dans Configuration Container, recherchez et sélectionnez le conteneur créé dans la section . [Création d’une configuration Microsoft® Power Automate Dataverse Cloud](#microsoft-power-automate-dataverse-cloud-configuration), puis appuyez sur **[!UICONTROL Enregistrer et fermer]**.
1. Ouvrez le formulaire adaptatif pour le modifier et accédez à **[!UICONTROL Envoi]** section des propriétés du conteneur de formulaires adaptatifs.
1. Dans le conteneur de propriétés, pour **[!UICONTROL Actions Envoyer]** sélectionnez la variable **[!UICONTROL Appeler un flux d’automatisation de puissance]** . Une liste des flux d’automatisation de puissance disponibles devient disponible **[!UICONTROL Flux de Power Automate]** . Sélectionnez le flux requis et les données Forms adaptatives lui sont envoyées lors de l’envoi.

![Configuration de l’action d’envoi](assets/submission.png)

>[!NOTE]
>
> Avant d’envoyer le formulaire adaptatif, assurez-vous que la variable `When an HTTP Request is received` Le déclencheur avec sous le schéma JSON est ajouté à votre flux Power Automate.

```
        {
            "type": "object",
            "properties": {
                "attachments": {
                    "type": "array",
                    "items": {
                        "type": "object",
                        "properties": {
                            "filename": {
                                "type": "string"
                            },
                            "data": {
                                "type": "string"
                            },
                            "contentType": {
                                "type": "string"
                            },
                            "size": {
                                "type": "integer"
                            }
                        },
                        "required": [
                            "filename",
                            "data",
                            "contentType",
                            "size"
                        ]
                    }
                },
                "templateId": {
                    "type": "string"
                },
                "templateType": {
                    "type": "string"
                },
                "data": {
                    "type": "string"
                },
                "document": {
                    "type": "object",
                    "properties": {
                        "filename": {
                            "type": "string"
                        },
                        "data": {
                            "type": "string"
                        },
                        "contentType": {
                            "type": "string"
                        },
                        "size": {
                            "type": "integer"
                        }
                    }
                }
            }
        }
```

