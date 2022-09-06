---
title: Prévisualisation du contenu
description: Découvrez comment utiliser le service d’aperçu AEM pour prévisualiser le contenu avant sa mise en ligne.
exl-id: 6b4b57f6-2e66-4c83-94d9-bc1e0daab0f3
source-git-commit: 5a804895013e19592f918341bbc7921261b26945
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 91%

---


# Prévisualisation du contenu {#previewing-content}

AEM propose un service d’aperçu Sites qui permet aux développeurs et aux auteurs de contenu de prévisualiser l’expérience finale d’un site web avant qu’il n’atteigne l’environnement de publication et soit disponible publiquement.

Il facilite la prévisualisation des expériences de page qui ne seraient pas visibles autrement à partir de l’environnement de création, comme les transitions de page et tout autre contenu côté publication uniquement.

Pour plus d’informations sur les environnements de prévisualisation, consultez le document [Gestion des environnements.](/help/implementing/cloud-manager/manage-environments.md#access-preview-service).

>[!NOTE]
>
>La publication d’un fragment d’expérience en aperçu suit la même procédure que pour une page, à partir de la console de Fragments d’expérience ou de l’éditeur.

## Publication de contenu en vue de la prévisualisation {#publishing-content-to-preview}

Vous pouvez publier du contenu dans le service d’aperçu à l’aide de l’interface utilisateur de **Publication gérée**.

1. Dans la console Sites, sélectionnez la ou les pages à envoyer en prévisualisation, puis cliquez sur le bouton **Gérer la publication**
1. Dans l’assistant suivant, sélectionnez **Aperçu** comme destination.

   ![publication gérée](/help/sites-cloud/authoring/assets/previewmanagedpublication.png)

1. Cliquez sur **Suivant**, puis sur **Publier** pour confirmer.

1. Une boîte de dialogue affiche les URL d’accès au contenu dans l’environnement de prévisualisation.


Vous pouvez également utiliser les URL affichées dans l’assistant pour afficher le contenu de l’aperçu, ou ajouter `preview-` à l’URL de publication de votre instance de production.

```
https://preview-p<programID>-e>environmentID>.adobeaemcloud.com/<pathtopage>.html
```

Consultez le document [Gestion des environnements](/help/implementing/cloud-manager/manage-environments.md) pour plus d’informations sur la manière de récupérer les URL de vos environnements.

Le contenu peut également être publié pour la prévisualisation à l’aide d’un [workflow de publication de l’arborescence de contenu](/help/operations/replication.md#publish-content-tree-workflow) avec le paramètre `agentId` défini sur `preview` ou à l’aide de l’[API de réplication](/help/operations/replication.md#replication-api) avec un `AgentFilter` configuré pour la prévisualisation.

## Annulation de la publication de contenu à partir de l’aperçu {#unpublishing-content-from-preview}

Annulation de la publication de contenu à partir de **Aperçu** L’environnement est fondamentalement le même processus que [annulation de la publication de pages](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#unpublishing-pages) de la **Publier** environnement.

La seule différence réside dans le fait que vous pouvez sélectionner la variable **Destination** to **Aperçu**.

## Configuration des paramètres OSGi pour le niveau d’aperçu {#configuring-osgi-settings-for-the-preview-tier}

Les valeurs de propriété OSGi du niveau d’aperçu sont héritées du niveau de publication. Toutefois, les valeurs du niveau d’aperçu peuvent être distinctes du niveau de publication en définissant le `service` paramètre à la valeur `preview`. L’exemple suivant d’une propriété OSGi détermine l’URL d’un point d’entrée d’intégration.

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
