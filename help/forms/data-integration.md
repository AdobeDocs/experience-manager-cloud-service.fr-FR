---
title: 'Comment connecter une base de données à [!DNL AEM Forms] as a Cloud Service ? '
seo-title: AEM Forms Data Integration
description: Vous pouvez récupérer des données et les enregistrer dans les services web RESTful, les services web SOAP et les services OData depuis [!DNL AEM Forms] as a Cloud Service. Le service fournit un outil dédié pour récupérer, tester, valider et envoyer des données à divers types de sources de données.
exl-id: 9d146275-de0a-4861-b060-d205ed6305f3
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 100%

---

# Connexion de vos sources de données à Cloud Service {#aem-forms-data-integration}

![Intégration de données](do-not-localize/data-integeration.png)

Les infrastructures d’entreprise comprennent des systèmes principaux ou des sources de données telles que des bases de données, des services Web, des services REST, des services OData et des solutions CRM. Associés, ils constituent un système d’informations qui fournit des données aux applications d’entreprise pour effectuer les activités quotidiennes. En revanche, les applications capturent des données et les renvoient pour mettre à jour les sources de données.

Les applications [!DNL AEM Forms] telles que les formulaires adaptatifs et les communications interactives nécessitent l’intégration à des sources de données à des fins de récupération des données client lors du rendu des formulaires et la création de communications interactives. Il existe des cas d’utilisation dans lesquels les données sont extraites de sources de données en fonction des entrées utilisateur dans les formulaires adaptatifs. De plus, les données de formulaire adaptatif envoyées peuvent être réécrites pour mettre à jour les sources de données respectives.

Alors qu’un système modulaire distribué a des avantages propres, le défi consiste à intégrer et créer des associations de données dans plusieurs sources de données. L’intégration des données est essentielle au fonctionnement et à l’efficacité d’une infrastructure d’entreprise avec des sources de données distinctes connectées à des applications à des fins d’échange des données d’entreprise.

## Aperçu de l’intégration de données {#data-integration-overview}

![aem-forms-data-integeration](assets/aem-forms-data-integeration.png)

L’intégration de données [!DNL AEM Forms] permet de configurer et de connecter des sources de données disparates à [!DNL AEM Forms]. Elle fournit une interface utilisateur intuitive qui permet de créer un schéma de représentation de données unifiée des entités d’entreprise dans les sources de données connectées. La représentation unifiée est appelée modèle de données de formulaire, qui est une extension du schéma JSON. Les entités d’un modèle de données de formulaire sont appelées objets de modèle de données. Un modèle de données de formulaire vous permet d’effectuer les opérations suivantes :

* Accédez aux objets de modèle de données, aux propriétés et aux services à partir de sources de données connectées.
* Créez des objets et des propriétés de modèle de données personnalisés.
* Créez des associations entre les objets de modèle de données dans et entre les sources de données.
* Appelez les services d’objet de modèle de données pour interroger ou écrire des données vers et depuis des sources de données.

Une fois que vous avez créé un modèle de données de formulaire, vous pouvez l’utiliser dans divers processus de formulaires adaptatifs et de communications interactives :

* Créer des formulaires adaptatifs et des communications interactives basés sur le modèle de données de formulaire
* Remplir des formulaires adaptatifs et des communications interactives à partir de sources de données configurées
* Appeler des services/opérations de source de données à l’aide de règles de formulaire adaptatif
* Écrire les données de formulaire adaptatif envoyées dans les sources de données

## Prise en main de l’intégration de données {#get-started-with-data-integration}

La première étape de l’implémentation de l’intégration de données consiste à identifier et à configurer les sources de données qui stockent les informations que vous souhaitez exploiter dans les formulaires adaptatifs et les cas d’utilisation de communications interactives. Ensuite, vous créez un modèle de données de formulaire qui utilise un objet, des propriétés et des services de modèle de données provenant d’une ou de plusieurs sources de données. Vous pouvez créer des formulaires adaptatifs et des communications interactives basés sur un modèle de données de formulaire dans lequel les champs de formulaire adaptatif ou les espaces réservés dans les communications interactives sont liés aux propriétés de source de données respectives.

[!DNL AEM Forms] vous permet également de créer un modèle de données de formulaire indépendant des sources de données et d’associer ou de lier des objets et des propriétés de modèle de données dans le modèle de données de formulaire à la source de données ultérieurement. Il élimine les dépendances sur les sources de données lorsque vous travaillez sur un modèle de données de formulaire.

Examinez les éléments suivants pour commencer, comprendre et implémenter l’intégration de données.

* [Configuration des sources de données](configure-data-sources.md)
* [Création d’un modèle de données de formulaire](create-form-data-models.md)
* [Utilisation d’un modèle de données de formulaire](work-with-form-data-model.md)
* [Utilisation d’un modèle de données de formulaire](using-form-data-model.md)

>[!NOTE]
>
>[!UICONTROL Experience Manager Forms] ne prend pas en charge les bases de données relationnelles.
