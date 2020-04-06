---
title: Gérer les journaux - Cloud Service
description: Gérer les journaux - Cloud Service
translation-type: tm+mt
source-git-commit: 81f993325b80c0de17d6032a45ebd61c22169d39

---


# Accès aux journaux et gestion {#manage-logs}

Les utilisateurs peuvent accéder à la liste des fichiers journaux disponibles pour l’environnement sélectionné à l’aide de la carte d’environnement. Les utilisateurs peuvent accéder à la liste des fichiers journaux disponibles pour l’environnement sélectionné.

Ces fichiers peuvent être téléchargés soit par le biais de l’interface utilisateur, soit à partir de la page **Aperçu**.

![](assets/manage-logs1.png)

Ou encore à partir de la page **Environnements** :

![](assets/manage-logs2.png)

>[!NNote]
>Quel que soit l’emplacement d’ouverture, la même boîte de dialogue s’affiche et permet de télécharger un fichier journal.

![](assets/manage-logs3.png)


## Journaux disponibles via l’API {#logs-thorugh-api}

Outre le téléchargement de journaux par le biais l’interface utilisateur, les journaux seront disponibles via l’API et l’interface de ligne de commande.

Par exemple, pour télécharger les fichiers journaux d’un environnement spécifique, la commande pourrait ressembler à ceci :

```java
$ aio cloudmanager:download-logs --programId 5 1884 author aemerror
```

La commande suivante permet de retailler les journaux :

```java
$ aio cloudmanager:tail-log --programId 5 1884 author aemerror
```

Pour obtenir l’ID d’environnement (1884 dans ce cas) et les options de service ou de nom de journal disponibles, vous pouvez utiliser :

```java
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

>[!NNote]
>Alors que **les téléchargements de journaux** seront disponibles par le biais de l’interface utilisateur et de l’API, **** la fonction d’envoi de journaux est disponible uniquement sur l’API/CLI.
