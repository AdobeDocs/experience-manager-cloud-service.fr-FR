---
title: Présentation d’Edge Delivery Services dans Cloud Manager
description: Découvrez comment diffuser vos projets Cloud Manager à l’aide d’Edge Delivery Services.
exl-id: f33bd6f0-62fc-4ecc-b8d2-65d1f1c44d82
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: 71d514b2eaf83732cc0856f6b508ab814fe7f469
workflow-type: tm+mt
source-wordcount: '1426'
ht-degree: 53%

---


# Présentation d’Edge Delivery Services dans Cloud Manager {#edge-delivery-services}

Edge Delivery Services est un ensemble de services composable qui offre une grande flexibilité quant à la manière dont vous créez du contenu sur votre site web. Cette fonctionnalité permet d’effectuer les opérations suivantes :

* Créer des sites rapides avec un score Lighthouse parfait.
* Surveillez en permanence les performances grâce à la télémétrie opérationnelle.
* Augmenter l’efficacité de la création en découplant les sources de contenu.

Vous pouvez utiliser la gestion de contenu AEM et la création WYSIWYG à l’aide de l’éditeur universel, ainsi que la création basée sur des documents.

Cloud Manager dans AEM as a Cloud Service vous permet d’activer le service Edge Delivery pour votre projet.

>[!TIP]
>
>Pour plus d’informations sur Edge Delivery Services et son utilisation avec AEM, consultez la [vue d’ensemble d’Edge Delivery Services](/help/edge/overview.md#how-does-it-work).

## Présentation d’Edge Delivery Services dans Cloud Manager {#edge-in-cloud-manager}

Si vous disposez d’Edge Delivery Services sous licence avec Adobe Experience Manager Sites, vous pouvez désormais intégrer votre site à Edge Delivery Services directement dans Cloud Manager et publier votre contenu [à l’aide d’une expérience guidée en libre-service](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md).

De plus, vous pouvez accéder à une expérience unifiée pour gérer toutes vos propriétés AEM tout en assurant la cohérence entre les workflows clés. Ces workflows comprennent notamment la gestion des noms de domaine, la gestion des certificats SSL et les mappages de réseau CDN.

Cloud Manager propose deux types de déploiement pour Edge Delivery Services dans le réseau CDN géré par Adobe avec des fonctionnalités distinctes. [En savoir plus](#edge-delivery-deployment-options).

>[!NOTE]
>
>Edge Delivery Services peut également être intégré aux environnements AEM Sites as a Cloud Service existants à l’aide du pipeline de configuration et des sélecteurs d’origine. Pour plus d’informations, consultez les sections [Proxy vers Edge Delivery Services](/help/implementing/dispatcher/cdn-configuring-traffic.md#proxying-to-edge-delivery) et [Configuration d’un proxy à partir d’un environnement existant](https://www.aem.live/docs/byo-cdn-adobe-managed#option-1-setup-a-proxy-from-an-existing-environment).

## Options de déploiement de Edge Delivery Services dans le réseau CDN géré par Adobe {#edge-delivery-deployment-options}

Il existe deux types de déploiement pour Edge Delivery Services dans le réseau CDN géré par Adobe :

1. **Avec un environnement AEMaaCS existant** — Configurez un proxy HTTP à partir d’un environnement AEM Sites as a Cloud Service existant. Cette approche est généralement utilisée lorsque vous disposez déjà d’un environnement et que vous souhaitez migrer une partie d’un site vers Edge Delivery Services. Voir [ Configuration d’un proxy à partir d’un environnement existant](https://www.aem.live/docs/byo-cdn-adobe-managed#option-1-setup-a-proxy-from-an-existing-environment).

1. **Sans environnement AEMaaCS existant (environnement Edge)** — Configurez un nouveau site Edge Delivery indépendamment d’un environnement AEM Sites as a Cloud Service. Cette approche est utilisée lorsque vous ne disposez pas d’un environnement de création ou de publication AEM et que vous souhaitez utiliser Edge Delivery Services seul. Voir [Configuration d’un site Edge Delivery sans environnement existant](https://www.aem.live/docs/byo-cdn-adobe-managed#option-2-setup-an-edge-delivery-site-without-an-existing-environment).

Ces deux options disposent également de fonctionnalités différentes :

* Le **Pipeline de configuration** est disponible pour les environnements AEM as a Cloud Service.
* Le **Pipeline de configuration** est actuellement disponible pour les environnements Edge uniquement par le biais du programme Beta limité.

Pour obtenir des instructions de configuration complètes, voir [Réseau CDN géré par ](https://www.aem.live/docs/byo-cdn-adobe-managed)


## À propos de Edge Delivery Services avec la création AEM (Beta) {#eds-aem-authoring}

>[!NOTE]
>
>Les fonctionnalités flexibles de niveau publication et de croisement de création AEM décrites ici se trouvent dans Beta. Pour rejoindre Beta, envoyez un e-mail à l’adresse [grp-beta_xwalk-publish_config@adobe.com](mailto:grp-beta_xwalk-publish_config@adobe.com) avec votre ID d’organisation et votre ID de programme Adobe.

Les expériences web modernes nécessitent une diffusion hautement performante, mais de nombreuses entreprises s’appuient également sur des workflows de création AEM établis, la gouvernance et les modèles de réutilisation du contenu. Pour aider vos équipes à moderniser la diffusion sans interrompre la création, Cloud Manager propose des fonctionnalités qui vous permettent d’effectuer les opérations suivantes :

* Diffuser des expériences à l’aide de Edge Delivery Services.
* Continuez à utiliser l’instance de création AEM pour la création de contenu.
* Configurez uniquement l’infrastructure requise pour votre architecture.

Ces fonctionnalités permettent aux entreprises d’adopter une diffusion moderne de manière incrémentielle, sans sacrifier les workflows existants.

### Options de création pour les sites Edge Delivery {#authoring-options-eds}

Lorsque vous créez un site Edge Delivery dans Cloud Manager, vous pouvez choisir l’approche de création souhaitée :

* Création basée sur des documents : créez du contenu dans Google Drive ou SharePoint. Aucun environnement AEM n’est requis.
* Création AEM : créez du contenu dans AEM à l’aide de l’éditeur universel. Cette méthode nécessite un environnement de création AEM. Avec cette option, aucun niveau de publication n’est requis lorsqu’Edge Delivery gère la diffusion de contenu.

Les entreprises peuvent choisir entre ces approches ou les utiliser de manière incrémentielle, en fonction de leurs préférences de workflow. Voir [ Création de votre premier site Edge Delivery en un clic](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md).

### Niveau de publication flexible {#flexible-publish-tier}

Cloud Manager vous permet de configurer si un niveau de publication est configuré pour les environnements de votre programme. Toutes les architectures ne nécessitent pas de niveau de publication, comme illustré dans le tableau suivant :

| Architecture | Niveau de publication |
| --- | --- |
| AEM Sites traditionnel | Requis |
| Découplé / API-first | Requis |
| Edge Delivery Services | Non nécessaires |

En activant le niveau de publication uniquement lorsque cela est nécessaire, les équipes peuvent configurer des environnements plus rapidement, simplifier l’infrastructure et réduire les composants inutiles. Voir [Niveau de publication flexible (Beta)](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#flexible-publish-tier).

## Avantages de l’utilisation du chemin recommandé par Adobe pour Edge Delivery Services {#recommended-path-eds}

Optimisez vos avantages grâce à Adobe en accédant à votre licence Edge Delivery Services via Cloud Manager et en l’utilisant. Cela vous permet de tirer parti de plusieurs avantages clés.

* [Utilisez votre licence sur le programme de votre choix](/help/implementing/cloud-manager/edge-delivery/add-edge-delivery-site.md) ou [mettez à jour d’autres programmes](/help/implementing/cloud-manager/edge-delivery/manage-edge-delivery-sites.md), ou les deux.
* [Utilisez un référentiel Git externe](/help/implementing/cloud-manager/managing-code/external-repositories.md) (apportez votre propre Git) pour synchroniser et déployer le code de votre site Edge Delivery Services. Pour tirer parti de cette fonctionnalité, vous devez d’abord [intégrer votre site dans Cloud Manager](/help/implementing/cloud-manager/edge-delivery/add-edge-delivery-site.md). <!-- NEW from CQDOC-22867 -->
* [Utilisez le Pipeline de configuration Edge Delivery](/help/implementing/dispatcher/cdn-configuring-traffic.md) pour configurer les paramètres du réseau CDN géré par Adobe pour votre site Edge Delivery en définissant des règles telles que les filtres de trafic, les sélecteurs d’origine et les redirections. <!-- NEW from CQDOC-22867 -->
* Profitez des avantages de la [priorisation des API](https://developer.adobe.com/experience-cloud/experience-manager-apis/) pour effectuer des opérations CRUD (créer, lire, mettre à jour, supprimer).
* [Accédez aux rapports SLA](/help/implementing/cloud-manager/reports/report-sla.md).
* [Accédez à l’assistance Adobe](/help/edge/overview.md#support-ticket) pour vos programmes de production enregistrés.

Si vous disposez d’une licence Edge Delivery Services (EDS), vous pouvez utiliser un [réseau CDN géré par Adobe](/help/implementing/dispatcher/cdn.md#aem-managed-cdn) pour votre site Edge Delivery. Cela permet une gestion de réseau CDN en libre-service et des certificats DV qui se renouvellent automatiquement tous les trois mois, sauf si vous supprimez le certificat.

Si vous choisissez d’utiliser votre CDN (c’est-à-dire un CDN non géré par Adobe), indépendamment de votre licence Edge Delivery Services, vous devez le configurer sur la plateforme `aem.live`. Consultez [Configuration de CDN BYO](https://www.aem.live/docs/byo-cdn-setup).


## À propos de l’ajout d’Edge Delivery Services à un programme de production ou à un programme sandbox {#about-adding-eds-to-prod-sandbox}

Vous pouvez ajouter Edge Delivery Services de différentes manières en fonction de la façon dont vous avez commencé votre projet ou de quand vous souhaitez créer le site.

| Cas d’utilisation | Description |
| --- | --- |
| Je veux ajouter Edge Delivery Services à un nouveau programme de production. | Voir [Création de programmes de production](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md).<br>Dans l’assistant, sous l’onglet **Solutions et modules complémentaires**, sélectionnez **Edge Delivery Services**. |
| Je veux ajouter Edge Delivery Services à un programme de production existant. | Voir [Modification de programmes](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md).<br>Dans la boîte de dialogue **Modification de programme**, sous l’onglet **Solutions et modules complémentaires**, sélectionnez **Edge Delivery Services**. |
| Je veux ajouter un site Edge Delivery à Cloud Manager. | Voir [Ajout d’un site Edge Delivery](/help/implementing/cloud-manager/edge-delivery/add-edge-delivery-site.md). |
| Je souhaite créer un site Edge Delivery maintenant. | Consultez [Créer rapidement un site Edge Delivery dans Cloud Manager en un clic](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md). |
| Je souhaite ajouter Edge Delivery Services à un nouveau programme sandbox ou à un programme sandbox existant. | Voir [Création de programmes Sandbox](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md).<br>Lorsque vous créez un programme sandbox, Edge Delivery Services est ajouté au programme par défaut ; vous n’avez pas besoin de le sélectionner.<br>Les programmes sandbox existants avant la disponibilité générale d’Edge Delivery héritent automatiquement d’Edge Delivery Services. |
| Je souhaite créer un site Edge Delivery qui utilise la création AEM | Voir [Création d’un site Edge Delivery](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md#one-click-edge-delivery-site). Lors de l’utilisation de la création AEM avec Edge Delivery, un niveau de publication est facultatif. Voir [Niveau de publication flexible (Beta)](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#flexible-publish-tier). |

>[!NOTE]
>
>* Pour ajouter ou modifier des programmes, vous devez être membre du rôle **Propriétaire de l’entreprise** ou avoir l’autorisation de le faire.
>* Votre entreprise doit disposer d’une licence Edge Delivery Services inutilisée pour pouvoir l’appliquer à un programme de production.
>* Une fois la licence Edge Delivery Services appliquée ou supprimée d’un programme, la modification prend effet immédiatement sans qu’il soit nécessaire d’exécuter un pipeline.


## À propos de la liste des tâches Edge Delivery dans Cloud Manager {#ed-todo-list}

<!-- &#x2460; for "1" inside circle -->

La **liste de tâches Edge Delivery** est une liste de contrôle de tâches d’intégration destinée à vous guider tout au long de l’intégration et de la gestion de votre site Edge Delivery jusqu’à sa [mise en production](/help/journey-onboarding/go-live-checklist.md).

![Liste de tâches de site Edge Delivery dans Cloud Manager](/help/implementing/cloud-manager/assets/cm-eds-todo-list.png)

|   | Tâche | Description |
| --- | --- | --- |
| 1 | Rejoindre le canal de collaboration de produit | Cliquer sur **Envoyer la demande maintenant** envoie une demande à Adobe pour créer un canal pour votre entreprise. Si le canal existe déjà, vous faites l’objet d’un transfert vers le canal de votre entreprise. |
| 2 | Remplir les conditions préalables | Voir [Afficher le tutoriel de prise en main](https://www.aem.live/developer/tutorial). |
| 3 | Ajouter un site Edge Delivery OU <br>Créer un site maintenant | Voir [Ajout d’un site Edge Delivery](#eds-add-site).<br>Consultez [Créer un site Edge Delivery dans Cloud Manager](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md). |
| 4 | Configurer un site Edge Delivery pour utiliser un référentiel Git externe | Consultez la section [Configuration d’un site Edge Delivery pour utiliser un référentiel Git externe](/help/implementing/cloud-manager/edge-delivery/config-edge-delivery-site-with-byog.md). |
| 5 | Ajouter un domaine | Consultez [Ajouter un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). |
| 6 | Ajouter le certificat SSL | Voir [Ajout d’un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md). |
| 7 | Configurer le CDN de votre site Edge Delivery | Consultez [Ajouter un mappage de domaine](/help/implementing/cloud-manager/domain-mappings/add-domain-mapping.md). |
| 8 | Configuration de la validation push | Voir [Configuration de la validation push pour un site Edge Delivery](/help/implementing/cloud-manager/edge-delivery/cdn-setup-push-invalidation.md). |
| 9 | Mise en production | Voir [Liste de contrôle de mise en production](https://www.aem.live/docs/go-live-checklist). |

>[!VIDEO](https://video.tv.adobe.com/v/3428020?learn=on)

## Soumettre un ticket d’assistance {#eds-support-ticket}

{{support-ticket}}



