---
title: Créer un formulaire à l’aide de l’éditeur universel
description: Créez un formulaire adaptatif pour tester la liste déroulante en cascade à l’aide des intégrations d’API
feature: Edge Delivery Services
role: User
source-git-commit: 53e476981874597bfb7f9293e67b2d135c72b318
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Créer un formulaire à l’aide de l’éditeur universel

Créez le formulaire suivant à l’aide de l’éditeur universel. Le formulaire comporte 3 listes déroulantes dont les valeurs seront renseignées à l’aide de l’intégration d’API
![formulaire-adaptatif](assets/address-form.png)

## Pays de résidence

Lors de l’initialisation, le menu déroulant Pays de résidence est renseigné avec les résultats de l’appel API.
![initialize-event](assets/initialize-event.png)

## Gestionnaire de succès

Le gestionnaire de succès a été défini pour définir les valeurs enum et enumNames de la liste déroulante pays avec les valeurs appropriées du tableau geonames . Le tableau geonames est disponible sous l&#39;option Payload d&#39;événement .
![event-payload](assets/event-payload.png)
![success-handler](assets/success-handler.png)

## Récupérer les valeurs enfants

La liste déroulante d’état ou de province est renseignée lorsque l’utilisateur effectue une sélection dans la liste déroulante Pays de résidence. L’identifiant de nom de domaine associé au pays sélectionné est transmis en tant que paramètre d’entrée à l’intégration de l’API GetChildren

![get-children](assets/invoke-service-get-children.png)

Le gestionnaire de succès a été défini pour définir enum/enumNames du champ déroulant StateOrProvince .
![get-children-success-handler](assets/child-success-handler.png)

Lorsque l’état ou la province est sélectionné, vous pouvez remplir la liste déroulante Ville en suivant le modèle mentionné ci-dessus utilisé pour remplir la liste déroulante État ou Province .