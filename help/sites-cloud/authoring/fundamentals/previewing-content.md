---
title: Prévisualisation du contenu
description: Découvrez comment utiliser le service d’aperçu AEM pour prévisualiser le contenu avant la mise en ligne.
exl-id: 6b4b57f6-2e66-4c83-94d9-bc1e0daab0f3
source-git-commit: 66bc262b35f69b7877e4a01df9ab26395afd604d
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 28%

---


# Prévisualisation du contenu {#previewing-content}

AEM propose un service de prévisualisation de sites qui permet aux développeurs et aux auteurs de contenu de prévisualiser l’expérience finale d’un site web avant qu’il n’atteigne l’environnement de publication et soit disponible publiquement.

Elle permet de prévisualiser plus facilement des expériences de page qui ne seraient pas visibles autrement à partir de l’environnement de création, comme les transitions de page et tout autre contenu côté publication uniquement.

Pour plus d’informations sur les environnements d’aperçu, consultez le document . [Gestion des environnements.](/help/implementing/cloud-manager/manage-environments.md#access-preview-service).

>[!NOTE]
>
>La publication d’un fragment d’expérience à prévisualiser suit la même procédure que pour une page, à partir de la console Fragments d’expérience ou de l’éditeur.

## Publication de contenu en vue de la prévisualisation {#publishing-content-to-preview}

Vous pouvez publier du contenu sur le service d’aperçu à l’aide du **Publication gérée** Interface utilisateur.

1. Dans la console Sites , sélectionnez la ou les pages à envoyer en prévisualisation, puis cliquez sur le bouton **Gérer la publication** button
1. Dans l’assistant suivant, sélectionnez **Aperçu** comme destination.

   ![publication gérée](/help/sites-cloud/authoring/assets/previewmanagedpublication.png)

1. Cliquez sur **Suivant**, puis sur **Publier** pour confirmer.

1. Une boîte de dialogue affiche les URL d’accès au contenu dans l’environnement de prévisualisation.


Vous pouvez également utiliser les URL affichées dans l’assistant pour afficher le contenu de l’aperçu en préfixe. `preview-` à l’URL de publication de votre instance de production.

```
https://preview-p<programID>-e>environmentID>.adobeaemcloud.com/<pathtopage>.html
```

Voir le document [Gestion des environnements](/help/implementing/cloud-manager/manage-environments.md) pour plus d’informations sur la récupération des URL de vos environnements.

Le contenu peut également être publié pour une prévisualisation à l’aide d’une [workflow de l’arborescence de contenu de publication](/help/operations/replication.md#publish-content-tree-workflow) avec le `agentId` paramètre défini sur `preview` ou en utilisant la variable [API de réplication](/help/operations/replication.md#replication-api) avec un `AgentFilter` configuré pour l’aperçu.

## Configuration des paramètres OSGi pour le niveau d’aperçu {#configuring-osgi-settings-for-the-preview-tier}

Les valeurs de propriété OSGi du niveau d’aperçu sont héritées du niveau de publication. Toutefois, les valeurs du niveau d’aperçu peuvent être distinctes du niveau de publication en définissant la variable `service` à la valeur `preview`. L’exemple suivant de propriété OSGi détermine l’URL d’un point de terminaison d’intégration.

```
[
{
"name":"INTEGRATION_URL",
"type":"string",
"value":"http://s2.integrationvendor.com",
"service": "preview"
}
]
```

Pour plus d’informations, consultez [cette section](/help/implementing/deploying/configuring-osgi.md#author-vs-publish-configuration) de la documentation de la configuration OSGi.

## Débogage de l’aperçu à l’aide de Developer Console {#debugging-preview-using-the-developer-console}

Pour déboguer le niveau d’aperçu à l’aide de Developer Console, procédez comme suit :

* Dans [Developer Console](/help/implementing/developing/introduction/development-guidelines.md#aem-as-a-cloud-service-development-tools), sélectionnez **-- Tous les aperçus --** ou un environnement de production qui inclut **prev** dans son nom.
* Générez les informations pertinentes pour l’instance d’aperçu
Voir [Gestion des environnements](/help/implementing/cloud-manager/manage-environments.md) pour plus d’informations sur la manière d’obtenir les URL de vos environnements.
