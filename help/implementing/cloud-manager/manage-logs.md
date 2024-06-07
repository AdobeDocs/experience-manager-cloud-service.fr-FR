---
title: Accéder aux journaux et les gérer
description: Découvrez comment accéder aux journaux et les gérer pour faciliter votre processus de développement dans AEM as a Cloud Service.
exl-id: f17274ce-acf5-4e7d-b875-75d4938806cd
solution: Experience Manager
feature: Log Files, Developing
role: Admin, Architect, Developer
source-git-commit: bc92ed7acefbbd906b0986ea0b6b96fa6d8422de
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 69%

---


# Accéder aux journaux et les gérer {#manage-logs}

Découvrez comment accéder aux journaux et les gérer pour faciliter votre processus de développement dans AEM as a Cloud Service.

Vous pouvez accéder à la liste des fichiers journaux disponibles pour l’environnement sélectionné à l’aide de la carte **Environnements** de la page **Vue d’ensemble** ou de la page Détails de l’environnement.

Les journaux sont conservés pendant sept jours.

## Télécharger les journaux {#download-logs}

Pour télécharger les journaux, procédez comme suit :

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.

1. Accédez à la carte **Environnements** à partir de la page **Vue d’ensemble**.

1. Sélectionnez **Télécharger les journaux** dans le menu représentant des points de suspension.

   ![Élément de menu Télécharger les journaux](assets/download-logs1.png)

1. Dans la boîte de dialogue **Télécharger les journaux**, sélectionnez le **service** approprié dans le menu déroulant

   ![Boîte de dialogue Télécharger les journaux](assets/download-preview.png)

   Dans le cas [Autres régions de publication](/help/operations/additional-publish-regions.md) sont activés pour votre environnement, vous pourrez sélectionner chaque région et télécharger ses journaux séparément, comme illustré ci-dessous :

   ![Journaux de téléchargement pour d’autres régions de publication](assets/download-publish-region-logs.png)

1. Une fois que vous avez sélectionné votre service, cliquez sur l’icône de téléchargement en regard du journal que vous souhaitez récupérer.

Vous pouvez également accéder à vos journaux à partir de la page **Environnements**.

![Journaux depuis l’écran Environnements](assets/download-logs.png)

## Journaux via l’API {#logs-through-api}

En plus de l’interface utilisateur, les journaux sont disponibles via l’API et l’interface de ligne de commande.

Pour télécharger les fichiers journaux d’un environnement spécifique, la commande est similaire à la suivante.

```shell
$ aio cloudmanager:download-logs --programId 5 1884 author aemerror
```

En outre, vous pouvez suivre les journaux à l’aide de l’interface de ligne de commande.

```shell
$ aio cloudmanager:tail-log --programId 5 1884 author aemerror
```

Pour obtenir l’ID d’environnement (1884 dans ce cas) et les options de nom de service ou de journal disponibles, utilisez les commandes suivantes :

```shell
$ aio cloudmanager:list-environments
Environment Id Name                     Type  Description                          
1884           FoundationInternal_dev   dev   Foundation Internal Dev environment  
1884           FoundationInternal_stage stage Foundation Internal STAGE environment
1884           FoundationInternal_prod  prod  Foundation Internal Prod environment
 
 
$ aio cloudmanager:list-available-log-options 1884
Environment Id Service    Name         
1884           author     aemerror     
1884           author     aemrequest   
1884           author     aemaccess    
1884           publish    aemerror     
1884           publish    aemrequest   
1884           publish    aemaccess    
1884           dispatcher httpderror   
1884           dispatcher aemdispatcher
1884           dispatcher httpdaccess
```

### Ressources supplémentaires {#resources}

>[!TIP]
>
>Consulter [cette ressource vidéo](https://app.frame.io/reviews/28cdf463-b7fc-443b-a54a-93cb7da6567e/dbf158f1-568b-4efc-8fbc-3b241561cbab) pour en savoir plus sur le débogage AEM as a Cloud Service.

Reportez-vous aux ressources supplémentaires suivantes pour en savoir plus sur l’API Cloud Manager et l’interface de ligne de commande d’Adobe I/O :

* [Documentation de l’API Cloud Manager](https://developer.adobe.com/experience-cloud/cloud-manager/)
* [Interface de ligne de commande d’Adobe I/O](https://github.com/adobe/aio-cli-plugin-cloudmanager)

Consultez les ressources supplémentaires suivantes pour en savoir plus sur les fichiers journaux dans AEM as a Cloud Service :

* [Fichiers journaux d’AEM Cloud 5](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/expert-resources/cloud-5/cloud5-aem-log-files.html)
* [Débogage AEM as a Cloud Service à l’aide des journaux](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html?lang=fr)
