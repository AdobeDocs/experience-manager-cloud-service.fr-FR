---
title: Configuration des paramètres OSGi pour le niveau d’aperçu
description: Découvrez comment configurer le service d’aperçu AEM pour prévisualiser le contenu avant la mise en ligne.
exl-id: 1200bb17-8a3c-4e41-85f4-ed2334b61f69
source-git-commit: 9cff6e94b38016f008fd8177be2e071a530d80b6
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 64%

---

# Configuration des paramètres OSGi pour le niveau d’aperçu {#configure-osgi-preview-tier}

AEM propose un service de prévisualisation de sites qui permet aux développeurs et aux auteurs de contenu de prévisualiser l’expérience finale d’un site web avant qu’il n’atteigne l’environnement de publication et soit disponible publiquement.

Elle permet de prévisualiser une gamme d’expériences qui ne seraient pas visibles autrement à partir de l’environnement de création. Par exemple, les transitions de page, les fragments d’expérience et tout autre contenu côté publication uniquement.

Les valeurs de propriété OSGi du niveau d’aperçu sont héritées du niveau de publication. Toutefois, les valeurs du niveau d’aperçu peuvent être distinctes du niveau de publication en définissant le `service` paramètre à la valeur `preview`.

>[!NOTE]
>
>Pour plus d’informations sur les environnements de prévisualisation, consultez le document [Gestion des environnements.](/help/implementing/cloud-manager/manage-environments.md#access-preview-service).

## Configuration des paramètres OSGi pour le niveau de prévisualisation {#configuring-osgi-settings-for-the-preview-tier}

L’exemple suivant d’une propriété OSGi détermine l’URL d’un point d’entrée d’intégration.

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
