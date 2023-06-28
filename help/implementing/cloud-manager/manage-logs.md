---
title: Accès aux journaux et gestion des journaux
description: Découvrez comment accéder aux journaux et les gérer pour faciliter votre processus de développement dans AEM as a Cloud Service.
exl-id: f17274ce-acf5-4e7d-b875-75d4938806cd
source-git-commit: 92c123817a654d0103d0f7b8e457489d9e82c2ce
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 26%

---


# Accès aux journaux et gestion des journaux {#manage-logs}

Découvrez comment accéder aux journaux et les gérer pour faciliter votre processus de développement dans AEM as a Cloud Service.

Vous pouvez accéder à une liste de fichiers journaux disponibles pour l’environnement sélectionné à l’aide de la **Environnements** de la carte **Présentation** page ou page Détails de l’environnement.

## Journaux de téléchargement {#download-logs}

Pour télécharger les journaux, procédez comme suit.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la carte **Environnements** à partir de la page **Aperçu**.

1. Sélectionner **Journaux de téléchargement** dans le menu points de suspension.

   ![Option de menu des journaux de téléchargement](assets/download-logs1.png)

1. Dans le **Journaux de téléchargement** , sélectionnez la **Service** dans le menu déroulant

   ![Boîte de dialogue Télécharger les journaux](assets/download-preview.png)

1. Une fois que vous avez sélectionné votre service, cliquez sur l’icône de téléchargement en regard du journal que vous souhaitez récupérer.

Vous pouvez également accéder à vos journaux à partir du **Environnements** page.

![Journaux de l’écran Environnements](assets/download-logs.png)

## Journaux via l’API {#logs-through-api}

Outre le téléchargement de journaux via l’interface utilisateur, les journaux sont disponibles via l’API et l’interface de ligne de commande.

Pour télécharger les fichiers journaux d’un environnement spécifique, la commande est similaire à la suivante.

```shell
$ aio cloudmanager:download-logs --programId 5 1884 author aemerror
```

En outre, vous pouvez afficher les journaux à l’aide de l’interface de ligne de commande.

```shell
$ aio cloudmanager:tail-log --programId 5 1884 author aemerror
```

Pour obtenir l’ID d’environnement (1884 dans cet exemple) et les options de service ou de nom de journal disponibles, vous pouvez utiliser les commandes suivantes.

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

Reportez-vous aux ressources supplémentaires suivantes pour en savoir plus sur l’API Cloud Manager et l’interface de ligne de commande d’Adobe I/O :

* [Documentation de l’API Cloud Manager](https://developer.adobe.com/experience-cloud/cloud-manager/)
* [Interface de ligne de commande d’Adobe I/O](https://github.com/adobe/aio-cli-plugin-cloudmanager)
