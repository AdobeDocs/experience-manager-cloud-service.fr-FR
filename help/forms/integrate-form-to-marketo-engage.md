---
title: Comment intégrer Marketo Engage à AEM Forms ?
description: Découvrez comment intégrer votre instance Marketo Engage à AEM Forms.
keywords: Comment connecter une instance Marketo à un formulaire ? , Connecter un formulaire à Marketo, Intégrer un formulaire à Marketo Engage, Intégrer un formulaire adaptatif à une instance Marketo.
feature: Adaptive Forms, Form Data Model
role: User, Developer
exl-id: 74cd25f9-1ee1-4f3f-8e02-8714071e7c86
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 9%

---

# Intégrer Marketo Engage à AEM Forms

<span class="preview"> Cette fonctionnalité est disponible par le biais d’un programme d’adoption précoce. Vous pouvez écrire à aem-forms-ea@adobe.com à partir de votre identifiant e-mail officiel pour rejoindre le programme d’adoption précoce et demander l’accès à la fonctionnalité. </span>

L’intégration d’AEM Forms à [Adobe Marketo Engage](https://experienceleague.adobe.com/fr/docs/marketo/using/home) permet aux utilisateurs de tirer parti des fonctionnalités de Marketo Engage pour élaborer une logique commerciale à partir des données capturées et automatiser les workflows, y compris les campagnes intelligentes et l’automatisation des e-mails. Le formulaire configuré peut envoyer les données capturées à Marketo Engage pour traitement.

## Avantages de l’intégration de Marketo Engage aux formulaires

Vous trouverez ci-dessous quelques avantages de la connexion d’un formulaire AEM à Adobe Marketo Engage :

* **Intégration simplifiée** : la connexion de formulaires à Marketo Engage élimine la nécessité de créer un modèle de données de formulaire distinct. Le processus d’intégration est simple et convivial.
* **Capture de données automatisée** : elle permet de capturer automatiquement les envois de formulaire et de les stocker dans Marketo, ce qui élimine la saisie manuelle des données et réduit les erreurs.

* **Gestion des prospects** : rationalise les processus de gestion des prospects en intégrant directement les envois de formulaires à votre base de données marketing, ce qui permet d’améliorer le suivi et le suivi des prospects.

* **Amélioration des performances des campagnes** : il utilise les données de formulaire pour analyser et optimiser les campagnes marketing, ce qui améliore les performances globales et le retour sur investissement (ROI).

* **Analyses et rapports** : permet d’accéder à des outils d’analyse et de création de rapports fiables, tels que Munchkin, dans Marketo afin de mesurer l’efficacité des formulaires et des campagnes.

* **Automatisation des suivis** : elle permet d’automatiser les e-mails de suivi et les workflows déclenchés par les envois de formulaire, en assurant une communication rapide avec les prospects.

## Avantages clés de l’utilisation d’AEM Forms par rapport aux autres solutions de formulaires

Le tableau ci-dessous présente les quelques raisons de choisir AEM Forms plutôt que d’autres solutions de formulaires alternatives :

| **Fonctionnalité** | **AEM Forms** | **Autres solutions de formulaire** |
|-------------------------------------|----------------------------------------------------------------------|-----------------------------------------------------------|
| **Personnalisations** | Permet d’ajouter des fonctions personnalisées spécifiques, d’ajuster les actions de formulaire et de modifier les comportements de champ pour améliorer les interactions de formulaire et les workflows complexes | Aucune prise en charge de la personnalisation |
| **Éditeur de règles** | Prend en charge un éditeur de règles intégré pour l’ajout de logique et de conditions. | Aucune prise en charge de l’éditeur de règles |
| **Options de disposition** | Prend en charge plusieurs options de disposition | Options de disposition limitées |
| **Service de préremplissage** | Offre un service de préremplissage pour renseigner automatiquement les données de formulaire. | Aucun service de préremplissage disponible |
| **Incorporation dans des sites** | Peut être incorporé dans Sites à l’aide d’iFrame | Ne peut pas être incorporé dans Sites à l’aide d’iFrame |
| **Facilité d’intégration à Sites** | Aucun apprentissage supplémentaire requis ; AEM Forms utilise les mêmes compétences que Sites | Un apprentissage supplémentaire peut être nécessaire |
| **Envoi de données** | peut envoyer des données à différentes plateformes et offre plusieurs connecteurs, tels que Se connecter à SharePoint, Se connecter à OneDrive, Se connecter à Salesforce, etc. ; | Possibilité d’envoyer des données à des connecteurs limités, par exemple à Salesforce |

## Considérations relatives à l’intégration de Marketo Engage aux formulaires

Quelques considérations à prendre en compte lors de l’intégration de Marketo Engage à AEM Forms :

* AEM ne prend en charge que la base de données Personnes (Leads) parmi les différentes bases de données Marketo.
* Marketo permet la [création de 10 objets personnalisés](https://experienceleague.adobe.com/fr/docs/marketo/using/product-docs/administration/marketo-custom-objects/add-marketo-custom-object-fields) en tant qu’objets définis par l’utilisateur pour stocker des données spécialisées au-delà des champs standard des prospects, en prenant en charge les besoins spécifiques de l’entreprise.
* AEM ne peut accéder aux objets personnalisés que s’ils sont associés à la base de données du lead

## Conditions préalables à l’intégration de Marketo Engage aux formulaires

Vous trouverez ci-dessous les conditions préalables à la connexion de Marketo Engage à AEM Forms :

* Une licence Adobe Marketo Engage valide
* Une instance de travail de Marketo Engage pour [récupérer l’ID client et le secret client](https://experienceleague.adobe.com/fr/docs/marketo/using/product-docs/administration/additional-integrations/create-a-custom-service-for-use-with-rest-api) afin de créer une configuration cloud.

## Créez une configuration de service cloud pour connecter AEM Forms (Adaptive Forms) à Marketo Engage

![Workflow](/help/forms/assets/workflow-marketo-1.png)

>[!VIDEO](https://video.tv.adobe.com/v/3442865/engage-marketo-aem-forms-aem)

<span> Cette vidéo s’applique uniquement aux composants principaux. Pour les composants éditeur universel/de base, reportez-vous à l’article </span>.

La configuration cloud connecte votre instance Experience Manager à l’instance Adobe Marketo Engage. Pour créer une configuration cloud Marketo Engage, procédez comme suit :

1. Accédez à **Outils** > **Services cloud** > **Marketo Engage**.

   ![Marketo Engage](/help/forms/assets/marketo-engage.png)

1. Ouvrez un dossier pour héberger la configuration, puis cliquez sur **Créer**. La fenêtre **Créer une configuration Marketo Engage** s’affiche.

   >[!NOTE]
   >
   > Vous pouvez également [configurer le dossier pour les configurations de service cloud](/help/forms/configure-data-sources.md#configure-folder-for-cloud-service-configurations).

1. Indiquez le **titre** de la configuration et les informations d’identification pour vous connecter au service. Vous pouvez récupérer les informations d’authentification à partir du tableau de bord Adobe Marketo Engage :

   * **ID client** et **Secret client** sont disponibles dans **Admin** > **Intégration** > **LaunchPoint** en sélectionnant le service personnalisé et en cliquant sur **Afficher les détails**.
   * **URL d’identité** est disponible dans **Admin** > **Intégration** > **Services web** en tant que **Identité** dans la section **API REST**.

1. Cliquez sur **Connexion**.  Lors d’une connexion réussie, le message `Authentication Successful` s’affiche.
1. Cliquez sur **[!UICONTROL Créer]** pour enregistrer les paramètres de configuration du cloud.

![Configuration du cloud Marketo Engage](/help/forms/assets/marketo-engage-cloud-configuration.png)

Vous pouvez désormais utiliser la configuration de service cloud créée pour connecter la source de données Marketo Engage à un formulaire adaptatif.

## Étape suivante

Vous avez créé la configuration de service cloud pour intégrer Adobe Marketo Engage à AEM Forms. Vous pouvez désormais intégrer les éléments suivants :

* [Nouveau formulaire adaptatif avec Marketo Engage](/help/forms/integrate-adaptive-form-with-marketo-engage.md)
* [Formulaire adaptatif existant avec Marketo Engage](/help/forms/use-marketo-engage-data-source-in-form.md)

## Articles connexes

{{af-submit-action}}

## Voir également

{{marketo-engage-see-also}}
