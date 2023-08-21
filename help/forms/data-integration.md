---
title: Connexion d’AEM Forms à une base de données
description: Vous pouvez récupérer des données et les enregistrer dans les services web RESTful, les services web SOAP et les services OData depuis [!DNL AEM Forms] as a Cloud Service. Le service fournit un outil dédié pour récupérer, tester, valider et envoyer des données à divers types de sources de données.
source-git-commit: b8366fc19a89582f195778c92278cc1e15b15617
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 60%

---

# Connexion d’AEM Forms à une base de données {#aem-forms-data-integration}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/data-integration.html) |
| AEM as a Cloud Service | Cet article |


![Intégration de données](do-not-localize/data-integeration.png)

Les infrastructures d’entreprise comprennent des systèmes principaux ou des sources de données disparates comme des bases de données, des services web, des services REST, des services OData et des solutions de gestion de la relation client. Ensemble, ils créent un système d’information qui fournit des données aux applications d’entreprise pour effectuer des tâches quotidiennes. D’un autre côté, les applications capturent les données et les renvoient pour mettre à jour les sources de données.

Les applications [!DNL AEM Forms] telles que les formulaires adaptatifs et les communications interactives nécessitent l’intégration à des sources de données à des fins de récupération des données client lors du rendu des formulaires et la création de communications interactives. Il existe des cas d’utilisation dans lesquels les données sont extraites de sources de données en fonction des entrées utilisateur dans les formulaires adaptatifs. De plus, les données de formulaire adaptatif envoyées peuvent être réécrites pour mettre à jour les sources de données respectives.

Bien qu’un système modulaire et distribué présente ses propres avantages, le défi consiste à intégrer et à créer des associations de données entre les sources de données. L’intégration des données est la clé d’une infrastructure d’entreprise fonctionnelle et efficace avec des sources de données disparates connectées aux applications d’échange de données commerciales.

## Aperçu de l’intégration de données {#data-integration-overview}

![aem-forms-data-integeration](assets/aem-forms-data-integeration.png)

L’intégration de données [!DNL AEM Forms] permet de configurer et de connecter des sources de données disparates à [!DNL AEM Forms]. Elle fournit une interface utilisateur intuitive qui permet de créer un schéma de représentation de données unifiée des entités d’entreprise dans les sources de données connectées. La représentation unifiée est appelée modèle de données de formulaire, qui est une extension du schéma JSON. Les entités d’un modèle de données de formulaire sont appelées objets de modèle de données. Un modèle de données de formulaire permet :

* Accédez aux objets, propriétés et services de modèle de données à partir de sources de données connectées.
* Création d’objets et de propriétés de modèle de données personnalisés
* Créez des associations entre les objets de modèle de données dans et entre les sources de données.
* Appelez les services d’objet de modèle de données pour interroger ou écrire des données vers et depuis des sources de données.

Une fois que vous avez créé un modèle de données de formulaire, vous pouvez l’utiliser dans divers processus de formulaires adaptatifs et de communications interactives :

* Créer des formulaires adaptatifs et des communications interactives basés sur le modèle de données de formulaire
* Remplir des formulaires adaptatifs et des communications interactives à partir de sources de données configurées
* Appeler des services/opérations de source de données à l’aide de règles de formulaire adaptatif
* Écrire les données de formulaire adaptatif envoyées dans les sources de données

## Prise en main de l’intégration de données {#get-started-with-data-integration}

La première étape de l’implémentation de l’intégration de données consiste à identifier et configurer les sources de données qui stockent les informations que vous souhaitez utiliser dans les cas d’utilisation de Forms adaptatif et des communications interactives. Ensuite, vous créez un modèle de données de formulaire qui utilise un objet, des propriétés et des services de modèle de données provenant d’une ou de plusieurs sources de données. Vous pouvez créer des formulaires adaptatifs et des communications interactives basés sur un modèle de données de formulaire dans lequel les champs de formulaire adaptatif ou les espaces réservés dans les communications interactives sont liés aux propriétés de source de données respectives.

[!DNL AEM Forms] vous permet également de créer un modèle de données de formulaire indépendant des sources de données et d’associer ou de lier ultérieurement des objets et des propriétés de modèle de données dans le modèle de données de formulaire à la source de données. Cela élimine toute dépendance aux sources de données lorsque vous travaillez sur un modèle de données de formulaire.

Consultez les sections suivantes pour commencer, comprendre et mettre en oeuvre l’intégration des données.

* [Configuration des sources de données](configure-data-sources.md)
* [Création d’un modèle de données de formulaire](create-form-data-models.md)
* [Utilisation d’un modèle de données de formulaire](work-with-form-data-model.md)
* [Utilisation d’un modèle de données de formulaire](using-form-data-model.md)

>[!NOTE]
>
>[!UICONTROL Experience Manager Forms] ne prend pas en charge les bases de données relationnelles.
