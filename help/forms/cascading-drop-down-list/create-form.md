---
title: Créer un formulaire à l’aide l’éditeur universel
description: Utilisez des expressions de formulaires adaptatifs pour ajouter la validation et le calcul automatiques ainsi que pour activer ou désactiver la visibilité d’une section.
feature: Adaptive Forms, Foundation Components
role: User
hide: true
hidefromtoc: true
source-git-commit: cc3cd74ad87f4213a200f36745ab3d335edca02d
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 76%

---

# Créer un formulaire à l’aide l’éditeur universel

Créez le formulaire suivant à l’aide de l’éditeur universel. Le formulaire comporte 3 listes déroulantes dont les valeurs seront renseignées à l’aide de l’intégration d’API
![adaptive-form](assets/address-form.png)

## Pays de résidence

Lors de l’initialisation, la liste déroulante Pays de résidence est renseignée avec les résultats de l’appel API.
![initialize-event](assets/initialize-event.png)

## Gestionnaire de succès

Le gestionnaire de succès a été défini pour configurer les valeurs enum et enumNames de la liste déroulante des pays avec les valeurs appropriées du tableau geonames. Le tableau geonames est disponible sous l&#39;option Payload d&#39;événement .
![event-payload](assets/event-payload.png)
![success-handler](assets/success-handler.png)

## Récupérer les valeurs enfants

La liste déroulante d’État ou de province est renseignée lorsque l’utilisateur ou l’utilisatrice effectue une sélection dans la liste déroulante Pays de résidence. Le geonameId associé au pays sélectionné est transmis en tant que paramètre d’entrée à l’intégration de l’API GetChildren.

![get-children](assets/invoke-service-get-children.png)

Le gestionnaire de succès a été défini pour définir enum/enumNames du champ déroulant StateOrProvince .
![get-children-success-handler](assets/child-success-handler.png)

Lorsque l’État ou la province est sélectionné, vous pouvez renseigner la liste déroulante Ville en suivant le modèle mentionné ci-dessus utilisé pour remplir la liste déroulante d’État ou de province.