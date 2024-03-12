---
title: Publication de contenu pour les Edge Delivery Services
description: Découvrez comment la publication de contenu fonctionne avec des Edge Delivery Services et comment publier AEM contenu avec des Edge Delivery Services.
feature: Edge Delivery Services
exl-id: 32fbb144-9175-47a9-bb5a-ca15f3fcd2d8
source-git-commit: 3ee1ba83518c3d4fba59b0c98b31e5c63a2eb6ab
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---


# Publication de contenu pour les Edge Delivery Services {#publishing-edge}

Avec les Edge Delivery Services, la publication de contenu est transparente, quelle que soit votre source de contenu :

* Contenu basé sur un document - Voir [Publication de section](/help/edge/docs/authoring.md) de la documentation Edge Delivery Services.
* Contenu AEM - Veuillez consulter les détails ci-dessous.

## Flux de publication depuis AEM {#publishing-flow}

Lorsque vous utilisez l’éditeur universel pour créer AEM contenu, la publication est aussi simple que de cliquer sur le **Publier** dans Universal Editor. Consultez le document [Publication de contenu avec l’éditeur universel.](/help/sites-cloud/authoring/universal-editor/publishing.md)

Le flux d’informations lors de la publication est le suivant. Une fois la publication commencée, ce flux est automatique et est illustré ici à titre d’information.

>[!NOTE]
>
>Jusqu’à 5 000 chemins d’accès publiés à partir de l’interface utilisateur de création ou par des workflows sont autorisés par jour. Les intégrations qui créent des charges de travail de publication en bloc ne sont pas prises en charge.

![Flux d’informations lors de la publication d’AEM vers des Edge Delivery Services](assets/publishing-flow.png)

1. L’auteur du contenu publie AEM contenu dans l’éditeur universel.
1. Un événement de publication est envoyé pour Adobe la file d’attente du pipeline.
1. Le service de publication Edge Delivery Services transfère les événements pertinents à l’API d’administration Edge Delivery Services.
1. Edge Delivery extrait et ingère le HTML sémantique de l’auteur AEM.
1. AEM est mis à jour avec l’état de publication.

>[!NOTE]
>
>Par défaut, l’API d’administration des Edge Delivery Services n’est pas protégée et peut être utilisée pour publier ou annuler la publication de documents sans authentification. Pour configurer l’authentification pour l’API d’administration, comme indiqué dans [Configuration de l’authentification pour les auteurs](https://www.aem.live/docs/authentication-setup-authoring), votre projet doit être configuré avec une API_KEY, qui accorde l’accès au service de publication. [Veuillez contacter l&#39;équipe d&#39;Adobe en Slack](/help/edge/docs/slack.md) pour obtenir des conseils.

## Prise en main {#how-to-get-started}

Veuillez contacter votre représentant d’Adobe pour accéder à cette fonctionnalité.
