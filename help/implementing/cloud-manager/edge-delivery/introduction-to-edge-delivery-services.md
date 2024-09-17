---
title: Présentation des Edge Delivery Services dans Cloud Manager
description: Découvrez comment diffuser vos projets Cloud Manager à l’aide de Edge Delivery Services.
exl-id: f33bd6f0-62fc-4ecc-b8d2-65d1f1c44d82
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5dc3d571c553f2972295172c7a6d0249be3285b8
workflow-type: tm+mt
source-wordcount: '750'
ht-degree: 6%

---

# Présentation des Edge Delivery Services dans Cloud Manager {#edge-delivery-services}

Edge Delivery Services est un ensemble de services composable qui offre une grande flexibilité quant à la manière dont vous créez du contenu sur votre site web. Cette fonctionnalité vous permet d’effectuer les opérations suivantes :

* Créez des sites rapides avec un score Lighthouse parfait.
* Surveillez continuellement les performances grâce à la fonction RUM (surveillance de l’utilisation réelle).
* Augmentez l’efficacité de la création en découplant les sources de contenu.

Vous pouvez utiliser AEM gestion de contenu et la création WYSIWYG à l’aide de l’éditeur universel et de la création basée sur des documents.

Cloud Manager dans AEM as a Cloud Service vous permet d’activer le service Edge Delivery pour votre projet.

>[!TIP]
>
>Pour plus d’informations sur les Edge Delivery Services et leur utilisation avec AEM, voir [Présentation des Edge Delivery Services](/help/edge/overview.md).

<!-- RELEASED TO GA SEPTEMBER 5, 2024
>[!NOTE]
>
>This feature is only available to [the early adopter program](/help/implementing/cloud-manager/release-notes/current.md#early-adoption). -->


## À propos des Edge Delivery Services dans Cloud Manager {#edge-in-cloud-manager}

Si vous possédez des Edge Delivery Services sous licence dans Adobe Experience Manager Sites, vous pouvez embarquer sur votre site avec des Edge Delivery Services directement dans Cloud Manager et passer en ligne [ à l’aide d’une expérience guidée en libre-service](/help/implementing/cloud-manager/managing-code/private-repositories.md).

De plus, vous pouvez accéder à une expérience unifiée pour gérer toutes vos propriétés AEM tout en assurant la cohérence entre les workflows clés. Il s’agit notamment de la gestion des noms de domaine, de la gestion des certificats SSL et des mappages CDN.

## Ajout de Edge Delivery Services à un programme de production ou à un programme sandbox

Pour ajouter ou modifier des programmes, vous devez être membre du rôle **Propriétaire de l’entreprise** ou être autorisé à le faire.

Votre entreprise doit disposer d’une licence de Edge Delivery Services inutilisée pour pouvoir l’appliquer à un programme de production.

>[!NOTE]
>
>Une fois la licence Edge Delivery Services appliquée ou supprimée d’un programme, la modification prend effet immédiatement sans qu’il soit nécessaire d’exécuter un pipeline. <!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2024.9.0+Release -->

Selon votre cas d’utilisation, effectuez l’une des opérations suivantes :

| Cas d’utilisation | Description |
| --- | --- |
| Je veux ajouter des Edge Delivery Services à un nouveau programme de production. | Voir [Création de programmes de production](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md).<br>Dans l’assistant, sous l’onglet **Solutions &amp; Add-ons**, sélectionnez **Edge Delivery Services**. |
| Je veux ajouter des Edge Delivery Services à un programme de production existant. | Voir [Modification de programmes](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md).<br>Dans la boîte de dialogue **Modifier le programme**, sous l’onglet **Solutions &amp; Add-ons**, sélectionnez **Edge Delivery Services**. |
| Je souhaite ajouter un site Edge Delivery à Cloud Manager | Voir [Ajout d’un site Edge Delivery](/help/implementing/cloud-manager/edge-delivery/add-edge-delivery-site.md). |
| Je souhaite ajouter des Edge Delivery Services à un nouveau programme sandbox ou à un programme sandbox existant. | Voir [Création de programmes Sandbox](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md).<br>Lorsque vous créez un programme sandbox, des Edge Delivery Services sont ajoutés au programme par défaut ; vous n’avez pas besoin de le sélectionner.<br>Les programmes Sandbox existants avant la disponibilité générale d’Edge Delivery héritent automatiquement des Edge Delivery Services. |

## Chemin d’accès recommandé pour les clients sous licence {#recommended-path-eds}

En tant que client sous licence, assurez-vous de tirer le meilleur parti de l’Adobe en accédant à et en utilisant votre licence Edge Delivery Services via Cloud Manager. Cette approche vous permet d’utiliser [Adobe managed CDN](/help/implementing/dispatcher/cdn.md#aem-managed-cdn) et de tirer parti des avantages clés tels que la gestion du CDN en libre-service, y compris la configuration et l’ajout de certificats DV. En outre, une fois un certificat DV créé, Adobe le renouvelle automatiquement tous les trois mois, sauf s’il est supprimé. Si vous ne disposez pas d’une licence Edge Delivery Services avec Adobe et que vous décidez de contourner ces avantages, vous ne pouvez utiliser qu’un réseau de diffusion de contenu géré par le client. Cette configuration doit se trouver sur la plateforme `aem.live`.

Si vous possédez une licence AEM as a Cloud Service Sites Edge Delivery Services, connectez-vous à Cloud Manager pour vous assurer que vous pouvez effectuer les opérations suivantes :

* Utilisez votre licence sur le programme de votre choix.
* Profitez des avantages [API-first](https://developer.adobe.com/experience-cloud/experience-manager-apis/) pour effectuer des opérations CRUD (créer, lire, mettre à jour, supprimer).
<!-- REMOVED AS PER https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+Self-service+access+to+Edge+Delivery+Services+and+Adobe+Managed+CDN * Access to license dashboard and reporting -->
* Accéder aux rapports SLA (*bientôt disponible*) <!-- ADD LINK TO IT WHEN FINALLY ADDED -->
* Obtenez le soutien des Adobes. Assurez-vous que vos sites Edge Delivery Services sont enregistrés par le biais d’un programme de production dans Cloud Manager pour une reconnaissance et une prise en charge appropriées de la part de l’Adobe.


## À propos de la liste de tâches d’Edge Delivery {#ed-todo-list}

La **liste de tâches d’Edge Delivery** est une liste de contrôle de tâches d’intégration destinée à vous guider tout au long de l’intégration et de la gestion de votre site Edge Delivery jusqu’à [Go-Live](/help/journey-onboarding/go-live-checklist.md).

![Liste de tâches de site Edge Delivery](/help/implementing/cloud-manager/assets/cm-eds-todo-list.png)

|  | Tâche | Description |
| --- | --- | --- |
| 1 | Rejoindre le canal de collaboration de produit | Cliquer sur **Soumettre la demande maintenant** envoie une demande à l’Adobe pour créer un canal pour votre entreprise. Si le canal existe déjà, vous êtes transféré vers le canal de votre entreprise. |
| 2 | Remplir les conditions préalables | Cliquez sur **Afficher le tutoriel de prise en main** pour accéder au [didacticiel de prise en main - développeur](https://www.aem.live/developer/tutorial). |
| 3 | Ajout d’un site Edge Delivery | Voir [Ajout d’un site Edge Delivery](#eds-add-site). |
| 4 | Ajouter un domaine | Voir [Ajout d’un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). |
| 5 | Configurer le CDN | Voir [Ajout d’un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md). |
| 6 | Configuration du réseau de diffusion de contenu de votre site Edge Delivery | Voir [Ajout d’une configuration CDN](#add-cdn). |

>[!VIDEO](https://video.tv.adobe.com/v/3428020?learn=on)

<!--
Edge Delivery Services can be enabled when adding a new production program or editing an existing one.

![Add production program with Edge Delivery Services](assets/add-production-program-with-edge.png)

For more information about adding programs, see the following:

* [Create Production programs](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)
* [Create Sandbox programs](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) -->
