---
Title: How to Integrate Marketo Engage with AEM Forms?
Description: Learn how to integrate your Marketo Engage instance with AEM Forms.
Keywords: How to connect a Marketo instance with form? , Connect a form to Marketo, Integrate a form with Marketo Engage, Integrate an Adaptive Form with a Marketo instance.
Feature: Adaptive Forms, Form Data Model
Role: User, Developer
source-git-commit: 681c194f997ab66f93beedad4eea273614e6797d
workflow-type: tm+mt
source-wordcount: '731'
ht-degree: 5%

---


# Intégration du Marketo Engage à AEM Forms

<span class="preview"> La fonctionnalité est disponible dans le cadre du programme d’adoption précoce. Vous pouvez écrire à aem-forms-ea@adobe.com à partir de votre adresse e-mail officielle pour rejoindre le programme d’adoption précoce et demander l’accès à la fonctionnalité. </span>

L’intégration d’AEM Forms à [Adobe Marketo Engage](https://experienceleague.adobe.com/en/docs/marketo/using/home) permet aux utilisateurs d’exploiter les fonctionnalités de Marketo Engage pour créer une logique métier à partir de données capturées et automatiser les workflows, y compris les campagnes intelligentes et l’automatisation des emails. Le formulaire configuré peut envoyer des données capturées à Marketo Engage pour traitement.

## Avantages de l’intégration de Marketo Engage à Forms

Voici quelques avantages de la connexion d’un formulaire AEM à Adobe Marketo Engage :

* **Intégration simplifiée** : la connexion de formulaires à Marketo Engage élimine la nécessité de créer un modèle de données de formulaire distinct. Le processus d’intégration est simple et convivial.
* **Capture de données automatisée** : permet de capturer automatiquement les envois de formulaire et de les stocker dans Marketo, ce qui élimine la saisie manuelle des données et réduit les erreurs.

* **Gestion des pistes** : cette fonctionnalité rationalise les processus de gestion des pistes en intégrant directement les envois de formulaires à votre base de données marketing, ce qui permet un meilleur suivi et une amélioration des pistes.

* **Performance de campagne améliorée** : il utilise les données de formulaire pour analyser et optimiser les campagnes marketing, en améliorant les performances globales et le retour sur investissement (ROI).

* **Analytics et création de rapports** : permet d’accéder à des outils d’analyse et de création de rapports fiables, tels que Munchkin, dans Marketo pour mesurer l’efficacité des formulaires et des campagnes.

* **Automatisation de relance** : elle permet d’automatiser les courriers électroniques de relance et les workflows déclenchés par les envois de formulaire, ce qui assure une communication opportune avec les pistes.

## Avantages clés de l’utilisation d’AEM Forms par rapport à d’autres solutions de formulaire

Le tableau ci-dessous présente les quelques raisons de choisir AEM Forms plutôt que d’autres solutions de formulaire :

| **Fonctionnalité** | **AEM Forms** | **Autres solutions de formulaire** |
|-------------------------------------|----------------------------------------------------------------------|-----------------------------------------------------------|
| **Personnalisations** | Permet d’ajouter des fonctions personnalisées spécifiques, d’ajuster les actions de formulaire et de modifier les comportements de champ pour améliorer les interactions de formulaire, les processus complexes | Aucune prise en charge de la personnalisation |
| **Éditeur de règles** | Prend en charge un éditeur de règles intégré pour ajouter une logique et des conditions. | Aucune prise en charge de l’éditeur de règles |
| **Options de mise en page** | Prise en charge des options de mise en page multiple | Options de mise en page limitées |
| **Service de préremplissage** | Offre un service de préremplissage pour renseigner automatiquement les données de formulaire. | Aucun service de préremplissage disponible |
| **Incorporation dans Sites** | Peut être incorporé dans Sites à l’aide d’iFrame | Ne peut pas être incorporé dans Sites à l’aide d’iFrame |
| **Facilité d’intégration avec Sites** | Aucun apprentissage supplémentaire n’est requis ; AEM Forms utilise les mêmes compétences que Sites | Un apprentissage supplémentaire peut être requis |
| **Envoi de données** | Peut envoyer des données à différentes plateformes et proposer plusieurs connecteurs, tels que Se connecter à SharePoint, Se connecter à OneDrive, Se connecter à Salesforce, etc. | Peut envoyer des données à des connecteurs limités, par exemple à Salesforce |

## Points à prendre en compte pour l’intégration de Marketo Engage à Forms

Quelques considérations à prendre en compte lors de l’intégration de Marketo Engage à AEM Forms :

* AEM ne prend en charge que la base de données Personnes (Leads) parmi les différentes bases de données Marketo.
* Marketo permet la [création de 10 objets personnalisés](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/marketo-custom-objects/add-marketo-custom-object-fields) en tant qu’objets définis par l’utilisateur pour stocker des données spécialisées au-delà des champs standard dans Leads, en tenant compte des besoins professionnels uniques.
* AEM ne peut accéder aux objets personnalisés que s’ils sont associés à la base de données de piste.

## Prérequis pour l’intégration de Marketo Engage à Forms

Vous trouverez ci-dessous les conditions préalables à la connexion du Marketo Engage à AEM Forms :

* Une licence Adobe Marketo Engage valide
* Une instance opérationnelle de Marketo Engage pour [récupérer l’ID client et le secret client](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/additional-integrations/create-a-custom-service-for-use-with-rest-api) pour créer une configuration cloud.

## Création d’une configuration de service cloud pour connecter AEM Forms (Forms adaptatif) à Marketo Engage

![Workflow](/help/forms/assets/workflow-marketo-1.png)

La configuration cloud connecte votre instance d’Experience Manager à l’instance Adobe Marketo Engage. Pour créer une configuration cloud de Marketo Engage, procédez comme suit :

1. Accédez à **Outils** > **Cloud Service** > **Marketo Engage**.

   ![Marketo Engage](/help/forms/assets/marketo-engage.png)

1. Ouvrez un dossier pour héberger la configuration et cliquez sur **Créer**. La fenêtre **Créer une configuration de Marketo Engage** s’affiche.

   >[!NOTE]
   >
   > Vous pouvez également [configurer le dossier pour les configurations de service cloud](/help/forms/configure-data-sources.md#configure-folder-for-cloud-service-configurations).

1. Spécifiez le **titre** de la configuration et des informations d’identification pour vous connecter au service. Vous pouvez récupérer les informations d’authentification à partir du tableau de bord Adobe Marketo Engage :
   * **L&#39;identifiant du client** et le **secret du client** sont disponibles dans **Admin** > **Intégration** > **LaunchPoint** en sélectionnant le service personnalisé et en cliquant sur **Afficher les détails**.
   * **L’URL d’identité** est disponible dans **Admin** > **Intégration** > **Services web** en tant que **Identité** dans la section **API REST**.

1. Cliquez sur **Connect**.  Lors d’une connexion réussie, le message `Authentication Successful` s’affiche.
1. Cliquez sur **[!UICONTROL Créer]** pour enregistrer les paramètres de configuration du cloud.

![Configuration du cloud Marketo Engage](/help/forms/assets/marketo-engage-cloud-configuration.png)

Vous pouvez désormais utiliser la configuration de service cloud créée pour connecter la source de données du Marketo Engage à un formulaire adaptatif.

## Étape suivante

Vous avez créé la configuration du service cloud pour intégrer Adobe Marketo Engage à AEM Forms. Vous pouvez désormais intégrer :
* [Nouveau formulaire adaptatif avec Marketo Engage](/help/forms/integrate-adaptive-form-with-marketo-engage.md)
* [Formulaire adaptatif existant avec Marketo Engage](/help/forms/use-marketo-engage-data-source-in-form.md)

## Articles connexes

{{af-submit-action}}

## Voir également

{{marketo-engage-see-also}}



