---
title: Publier du contenu pour Edge Delivery Services
description: Découvrez le fonctionnement de la publication de contenu avec Edge Delivery Services et comment publier du contenu AEM avec Edge Delivery Services.
feature: Edge Delivery Services
exl-id: 32fbb144-9175-47a9-bb5a-ca15f3fcd2d8
role: User
index: false
hide: true
hidefromtoc: true
source-git-commit: 17c14a78c2cfa262e25c6196fa73c6c4b17e200a
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 100%

---


# Publier du contenu pour Edge Delivery Services {#publishing-edge}

Avec Edge Delivery Services, la publication de contenu est transparente, quelle que soit votre source de contenu.

* Contenu basé sur un document : voir la [section Publier](/help/edge/docs/authoring.md) de la documentation Edge Delivery Services.
* Contenu AEM : consultez les détails ci-dessous.

## Flux de publication depuis AEM {#publishing-flow}

Lorsque vous utilisez l’éditeur universel pour créer du contenu AEM, il suffit, pour publier, de cliquer sur le bouton **Publier** dans l’éditeur universel. Consultez le document [Publication de contenu avec l’éditeur universel](/help/sites-cloud/authoring/universal-editor/publishing.md).

Le flux d’informations pendant la publication est le suivant. Une fois la publication commencée, ce flux est automatique. Il est illustré ici à titre d’information.

>[!NOTE]
>
>Jusqu’à 5 000 chemins d’accès publiés à partir de l’interface utilisateur de création ou par des workflows sont autorisés par jour. Les intégrations qui créent des charges de travail de publication en masse ne sont pas prises en charge. Si votre projet nécessite une capacité supérieure, veuillez le proposer pour le [Programme VIP](https://www.aem.live/vip/intake).

![Flux d’informations lors de la publication d’AEM vers Edge Delivery Services](assets/publishing-flow.png)

1. L’auteur ou l’autrice du contenu publie du contenu AEM dans l’éditeur universel.
1. Un événement de publication est envoyé vers la file d’attente du pipeline d’Adobe.
1. Le service de publication d’Edge Delivery Services transfère les événements pertinents à l’API d’administration d’Edge Delivery Services.
1. Edge Delivery Services extrait et ingère du HTML sémantique à partir de l’instance de création AEM.
1. AEM est mis à jour avec le statut de publication.

>[!NOTE]
>
>Par défaut, l’API d’administration d’Edge Delivery Services n’est pas protégée et peut être utilisée pour publier ou annuler la publication de documents sans authentification. Pour configurer l’authentification pour l’API d’administration, comme indiqué dans [Configuration de l’authentification pour les auteurs et autrices](https://www.aem.live/docs/authentication-setup-authoring), votre projet doit être configuré avec une API_KEY, qui accorde l’accès au service de publication. [Contactez l’équipe d’Adobe sur Slack](/help/edge/docs/slack.md) pour obtenir des conseils.

