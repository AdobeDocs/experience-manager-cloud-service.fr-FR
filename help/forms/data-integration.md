---
title: Comment connecter une base de données à [!DNL AEM Forms] as a Cloud Service ?
description: Récupérez et enregistrez des données sur les services web RESTful, les services web basés sur SOAP et les services OData à partir d’un formulaire adaptatif ou d’un processus AEM.
feature: Adaptive Forms, Form Data Model
role: Admin, User
exl-id: 9d146275-de0a-4861-b060-d205ed6305f3
source-git-commit: 8f39bffd07e3b4e88bfa200fec51572e952ac837
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 37%

---

# Connexion d’AEM Forms à une base de données {#aem-forms-data-integration}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/data-integration.html) |
| AEM as a Cloud Service | Cet article |



![Intégration de données](do-not-localize/data-integeration.png)

Les infrastructures d’entreprise comprennent des systèmes back-end ou des sources de données disparates comme des bases de données, des services web, des services REST, des services OData et des solutions CRM. Associés, ils constituent un système d’informations qui fournit des données aux applications d’entreprise pour effectuer les activités quotidiennes. En revanche, les applications capturent des données et les renvoient pour mettre à jour les sources de données.

Lorsque vous connectez un formulaire adaptatif à une base de données, l’intégration à des sources de données est nécessaire pour récupérer les données client lors du rendu des formulaires. Il existe des cas d’utilisation dans lesquels les données sont extraites de sources de données en fonction des entrées utilisateur dans les formulaires adaptatifs. En outre, lorsque vous envoyez un formulaire adaptatif à une base de données, les données de formulaire adaptatif envoyées peuvent être réécrites pour mettre à jour les sources de données respectives.

Alors qu’un système modulaire distribué a des avantages propres, le défi consiste à intégrer et créer des associations de données dans plusieurs sources de données. L’intégration des données est essentielle au fonctionnement et à l’efficacité d’une infrastructure d’entreprise avec des sources de données distinctes connectées à des applications à des fins d’échange des données d’entreprise.

## Aperçu de l’intégration de données {#data-integration-overview}

![aem-forms-data-integeration](assets/aem-forms-data-integeration.png)

L’intégration de données [!DNL AEM Forms] permet de configurer et de connecter des sources de données disparates à [!DNL AEM Forms]. Elle fournit une interface utilisateur intuitive qui permet de créer un schéma de représentation de données unifiée des entités d’entreprise dans les sources de données connectées. La représentation unifiée est connue sous le nom de modèle de données de formulaire (FDM), une extension du schéma JSON. Les entités d’un modèle de données de formulaire (FDM) sont appelées objets de modèle de données. Un modèle de données de formulaire (FDM) vous permet d’effectuer les opérations suivantes :

* Accéder aux objets de modèle de données, aux propriétés et aux services à partir de sources de données connectées.
* Créer des objets et des propriétés de modèle de données personnalisés.
* Créez des associations entre les objets de modèle de données dans et entre les sources de données.
* Appelez les services d’objet de modèle de données pour interroger ou écrire des données vers et depuis des sources de données.

Une fois que vous avez créé un modèle de données de formulaire (FDM), vous pouvez l’utiliser pour :

* Créer un Forms adaptatif basé sur un modèle de données de formulaire (FDM)
* Préremplissage du Forms adaptatif à partir des sources de données configurées
* Appeler des services/opérations de source de données à l’aide de règles de formulaire adaptatif
* Écrire les données de formulaire adaptatif envoyées dans les sources de données

## Applicabilité et cas d’utilisation

### Assurance

## AEM Forms peut-il être utilisé pour des applications de police d’assurance ?

Oui. AEM Forms peut être utilisé pour créer des formulaires de demande d’assurance numériques qui collectent les informations sur les demandeurs, valident les entrées et s’intègrent aux systèmes de souscription principaux.

## AEM Forms prend-il en charge les workflows de souscription ?

Oui, avec les workflows et les intégrations. AEM Forms prend en charge les processus pilotés par les workflows et les intégrations principales qui permettent aux données d’application de se diriger vers les systèmes de souscription et de prise de décision.

## AEM Forms peut-il s’intégrer aux systèmes principaux d’assurance ?

Oui. AEM Forms prend en charge l’intégration à l’aide des API REST et SOAP, ce qui lui permet de se connecter aux systèmes d’administration des politiques, de gestion des réclamations et de gestion de la relation client (CRM).

## AEM Forms peut-il écrire des données de formulaire dans les systèmes d’assurance ?

Oui. AEM Forms prend en charge l’écriture différée des données sur les systèmes principaux dans le cadre de l’envoi de formulaires et de l’exécution de workflows.

## Prise en main de l’intégration de données {#get-started-with-data-integration}

La première étape de l’implémentation de l’intégration de données pour envoyer un formulaire adaptatif à une base de données consiste à identifier et à configurer les sources de données qui stockent les informations que vous souhaitez utiliser dans le Forms adaptatif. Ensuite, vous créez un modèle de données de formulaire (FDM) qui utilise des objets, des propriétés et des services de modèle de données provenant d’une ou de plusieurs sources de données. Vous pouvez créer un Forms adaptatif basé sur un modèle de données de formulaire (FDM) où les champs de formulaire adaptatif sont liés aux propriétés de source de données respectives.

[!DNL AEM Forms] vous permet également de créer un modèle de données de formulaire (FDM) indépendant des sources de données et d’associer ou de lier des objets et des propriétés de modèle de données dans le modèle de données de formulaire (FDM) à la source de données ultérieurement. Il élimine toutes les dépendances sur les sources de données lorsque vous travaillez sur un modèle de données de formulaire (FDM).

Consultez les éléments suivants pour commencer, comprendre et implémenter l’intégration de données :

* [Configurer des sources de données](configure-data-sources.md)
* [Créer un modèle de données de formulaire (FDM)](create-form-data-models.md)
* [Utilisation d’un modèle de données de formulaire (FDM)](work-with-form-data-model.md)
* [Utilisation du modèle de données de formulaire (FDM)](using-form-data-model.md)

<!--

>[!NOTE]
>
>[!UICONTROL Experience Manager Forms] does not support relational database.

-->