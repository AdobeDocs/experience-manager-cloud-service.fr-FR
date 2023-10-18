---
title: Configuration des paramètres OSGi pour le niveau de prévisualisation
description: Découvrez comment configurer le service de prévisualisation AEM pour prévisualiser le contenu avant sa mise en ligne.
exl-id: 1310eb1a-63ad-44f1-adf5-7a93ee3a8ae6
source-git-commit: 0109cea1be85e647fb6c04dde4714b162bdc75a5
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 100%

---

# Configuration des paramètres OSGi pour le niveau de prévisualisation {#configure-osgi-preview-tier}

AEM propose un service de prévisualisation Sites qui permet aux équipes de développement et de création de contenu de prévisualiser l’expérience finale d’un site web avant qu’il n’atteigne l’environnement de publication et qu’il soit disponible publiquement.

Ce service permet de prévisualiser une gamme d’expériences qui ne seraient pas visibles autrement à partir de l’environnement de création. Il s’agit par exemple des transitions de page, des fragments d’expérience et de tout autre contenu côté publication uniquement.

Les valeurs de propriété OSGi du niveau de prévisualisation sont héritées du niveau de publication. Toutefois, les valeurs du niveau de prévisualisation peuvent être distinctes du niveau de publication en définissant le paramètre `service` sur la valeur `preview`.

>[!NOTE]
>
>Pour plus d’informations sur les environnements de prévisualisation, consultez le document [Gestion des environnements](/help/implementing/cloud-manager/manage-environments.md#access-preview-service).

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

Pour déboguer le niveau d’aperçu à l’aide de la Developer Console, procédez comme suit :

* Dans [Developer Console](/help/implementing/developing/introduction/development-guidelines.md#aem-as-a-cloud-service-development-tools), sélectionnez **-- Tous les aperçus --** ou un environnement de production qui inclut **prev** dans son nom.
* Générez les informations pertinentes pour l’instance d’aperçu
Voir [Gestion des environnements](/help/implementing/cloud-manager/manage-environments.md) pour plus d’informations sur la manière d’obtenir les URL de vos environnements.
