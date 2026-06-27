---
title: Accéder aux journaux et les gérer
description: Découvrez comment accéder aux journaux et les gérer pour faciliter votre processus de développement dans AEM as a Cloud Service.
exl-id: f17274ce-acf5-4e7d-b875-75d4938806cd
solution: Experience Manager
feature: Log Files, Developing
role: Admin, Developer
source-git-commit: 8f1bbbb30dad4c87a0f373117c0ca89afee98235
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 24%

---


# Accéder aux journaux et les gérer {#manage-logs}

Découvrez comment accéder aux journaux et les gérer pour prendre en charge votre processus de développement dans AEM as a Cloud Service.

Vous pouvez accéder à la liste des fichiers journaux disponibles pour l’environnement sélectionné à l’aide de la vignette **Environnements** de la page **Aperçu** ou de la page **Détails de l’environnement**.

Les journaux sont conservés pendant sept jours.

## Télécharger les journaux {#download-logs}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.

1. Accédez à la carte **Environnements** à partir de la page **Vue d’ensemble**.

1. Sélectionnez **Télécharger les journaux** dans le menu représentant des points de suspension.

   ![Élément de menu Télécharger les journaux](assets/download-logs1.png)

1. Dans la boîte de dialogue **Télécharger les journaux**, sélectionnez le **Service** approprié dans le menu déroulant.

   ![Boîte de dialogue Télécharger les journaux](assets/download-preview.png)

   Si les [Régions de publication supplémentaires](/help/operations/additional-publish-regions.md) sont activées pour votre environnement, vous pouvez sélectionner chaque région et télécharger ses journaux séparément, comme illustré ci-dessous :

   ![Télécharger les journaux pour les régions de publication supplémentaires](assets/download-publish-region-logs.png)

1. Une fois que vous avez sélectionné votre service, cliquez sur l’icône de téléchargement en regard du journal que vous souhaitez récupérer.

Vous pouvez également accéder à vos journaux à partir de la page **Environnements**.

![Journaux depuis l’écran Environnements](assets/download-logs.png)

## Journaux via l’API {#logs-through-api}

Les journaux sont disponibles via l’API et l’interface de ligne de commande, en plus de l’interface utilisateur.

Pour télécharger les fichiers journaux d’un environnement spécifique, utilisez une commande similaire à la suivante :

```shell
$ aio cloudmanager:download-logs --programId 5 1884 author aemerror
```

Vous pouvez également accéder immédiatement aux journaux à l’aide de l’interface de ligne de commande.

```shell
$ aio cloudmanager:tail-log --programId 5 1884 author aemerror
```

Pour obtenir l’identifiant de l’environnement (1884 dans cet exemple) et les options de nom de service ou de journal disponibles, vous pouvez utiliser les commandes suivantes :

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
>Pour en savoir plus sur le débogage d’AEM as a Cloud Service, regardez [&#x200B; cette ressource vidéo &#x200B;](https://app.frame.io/reviews/28cdf463-b7fc-443b-a54a-93cb7da6567e/dbf158f1-568b-4efc-8fbc-3b241561cbab).

Pour en savoir plus sur l’API Cloud Manager et l’interface de ligne de commande Adobe I/O, consultez les ressources supplémentaires suivantes :

* [Documentation de l’API Cloud Manager](https://developer.adobe.com/experience-cloud/cloud-manager/)
* [ADOBE I/O CLI](https://github.com/adobe/aio-cli-plugin-cloudmanager)

Pour en savoir plus sur les fichiers journaux dans AEM as a Cloud Service, consultez les ressources supplémentaires suivantes :

* [Cloud 5 : fichiers journaux AEM](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/expert-resources/cloud-5/cloud5-aem-log-files#)
* [Déboguer AEM as a Cloud Service à l’aide de journaux](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs#)
