---
title: Notes de mise à jour de la version 2026.7.0 de Cloud Manager
description: Découvrez la version 2026.7.0 de Cloud Manager dans Adobe Experience Manager as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: d1b28c7cfb323042f038a070bf0cb4ccfa27d9a1
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 3%

---

# Notes de mise à jour de Cloud Manager 2026.7.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

Découvrez la version 2026.7.0 de Cloud Manager dans AEM (Adobe Experience Manager) as a Cloud Service.

Consultez également les [notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Dates de publication {#release-date}

La date de publication de Cloud Manager 2026.7.0 dans AEM as a Cloud Service est le jeudi 9 juillet 2026.

La prochaine version prévue est le jeudi 6 août 2026.


## Nouvelles fonctionnalités - Cloud Manager {#cloud-manager-whats-new}

* **Apportez votre propre Git (BYOG) - Authentification secrète pour le clone Git**

  Vous pouvez désormais authentifier les requêtes de clone Git sur votre référentiel [!DNL Bring Your Own Git] à l’aide du secret byogit généré par Cloud Manager, en plus d’un jeton IMS. Cette fonctionnalité permet [!DNL Edge Delivery Services] clients d’utiliser les mêmes informations d’identification que celles déjà stockées par helix-admin pour la synchronisation du code. Les workflows de clone authentifiés par IMS existants ne sont pas affectés.

  Voir [ Authentification des requêtes de clone Git](/help/implementing/cloud-manager/edge-delivery/config-edge-delivery-site-with-byog.md#authenticate-git-clone-requests).

* **Infrastructure réseau VPN — Routage BGP et connexions multiples**\
  L&#39;API d&#39;infrastructure réseau VPN de mise en réseau avancée prend désormais en charge le routage dynamique BGP (Border Gateway Protocol) avec le routage statique existant. Les équipes peuvent configurer BGP par connexion en fournissant le numéro de système autonome BGP côté client et l&#39;adresse d&#39;homologue ; Cloud Manager gère dynamiquement l&#39;apprentissage des itinéraires — aucun préfixe statique requis.

  La limite précédente d’une connexion VPN par infrastructure a également été supprimée. Plusieurs connexions sont désormais prises en charge au sein de la même infrastructure, et les connexions statiques et BGP peuvent coexister. Les équipes de mise en réseau d’entreprise bénéficient ainsi d’une plus grande flexibilité lors de la conception de topologies VPN pour les environnements AEM Cloud Service.

* **Amélioration des performances de build avec la mise en cache du module**
Un nouveau modèle de version compile uniquement les modules modifiés (plutôt que le référentiel entier) à l’aide de la mise en cache au niveau du module pour améliorer les performances de la version. Elle s’applique aux pipelines de production. Vous contrôlez les pipelines de production qui utilisent **Smart Build**.

  Pour plus d’informations, consultez les sections suivantes :

   * [À propos de l’utilisation du Smart Build dans un pipeline de production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#about-smart-build-production-pipeline) et [À propos de l’utilisation du Smart Build dans un pipeline hors production](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#about-smart-build-non-production-pipeline)
   * [Ajouter un pipeline de production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md##adding-production-pipeline) et [Ajouter un pipeline hors production](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#configuring-non-production-pipelines).

* **Copie de contenu : programme croisé et flux de transfert**\
  Cloud Manager **Content Copy**, qui permet aux équipes de copier du contenu entre des environnements AEM sans déploiement, comprend deux fonctionnalités disponibles pour tous les programmes. La prise en charge inter-programmes permet de copier du contenu dans différents programmes Cloud Manager, et pas seulement dans le même programme. Le flux direct supprime la restriction directionnelle, ce qui permet de copier du contenu de n’importe quel environnement vers n’importe quel autre, y compris depuis les environnements inférieurs vers le haut.


## Programmes bêta {#private-beta-program}

Pour obtenir un accès exclusif aux fonctionnalités à venir avant leur publication, vous pouvez participer aux programmes bêta de Cloud Manager.

>[!IMPORTANT]
>
>Les versions de Beta contiennent des défauts et sont fournies « EN L’ÉTAT » sans garantie d’aucune sorte. Adobe n’a aucune obligation de tenir à jour, corriger, mettre à jour, modifier, remplacer ou prendre en charge les versions bêta. Les clients utilisent les versions bêta à leurs propres risques et périls. Ils ne se fient pas au bon fonctionnement ou aux performances des versions bêta, ni à la documentation ou aux documents qui les accompagnent. Les fonctionnalités et API de la version bêta peuvent être modifiées sans préavis. Toute utilisation des versions Beta s’effectue entièrement aux risques et périls du client.

Voir aussi [Programmes AEM Beta](/help/release-notes/release-notes-cloud/release-notes-current.md#aem-beta-programs)

Les opportunités de programme Beta suivantes sont actuellement disponibles :

### Edge Delivery Services avec création AEM et configuration flexible du niveau de publication {#eds-with-aem-authoring}

Cloud Manager propose deux nouvelles fonctionnalités conçues pour prendre en charge les architectures de diffusion modernes.

* **Edge Delivery Services avec création AEM**
Vous pouvez désormais diffuser des sites à l’aide de Edge Delivery Services tout en continuant à créer du contenu en mode de création AEM. Selon les préférences de votre workflow, vous pouvez choisir parmi les approches de création suivantes :

   * Création basée sur des documents
   * Création basée sur AEM

Pour plus d’informations, voir [Création d’un site Edge Delivery dans Cloud Manager](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md#one-click-edge-delivery-site).

* **Configuration flexible du niveau de publication**

Cloud Manager vous permet désormais de configurer si un niveau de publication est requis pour votre programme. Cette flexibilité vous permet de configurer des environnements qui correspondent mieux à l’architecture de diffusion choisie.

Pour plus d’informations, voir [Niveau de publication flexible (Beta)](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#flexible-publish-tier).

Pour rejoindre la version bêta, envoyez un courrier électronique à l’adresse [](mailto:grp-beta_xwalk-publish_config@adobe.com) avec votre ID d’organisation et votre ID de programme Adobe.

<!-- 
OLD
### Improved build performance with module caching {#quick-build-cm-pipelines}

A new build model compiles only changed modules (rather than the entire repository) using module-level caching to improve build performance. It applies to production pipelines. You control which production pipelines use **Smart Build**.

For more information, see the following:

* [Using Smart Build in a production pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#about-smart-build).
* [Add a production pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#full-stack-code).

To join the Beta, email [beta_quickbuild_cmpipelines@adobe.com](mailto:beta_quickbuild_cmpipelines@adobe.com) with your Adobe Organization ID and Program ID.

### Experience Hub Extensibility and Customization {#exp-hub-extensibility}

[Experience Hub](/help/experience-hub.md) serves as your entry point to AEM, customized for your organization's needs. Tell Adobe about your existing AEM UI Extensions so they can help you enable them in Experience Hub with minimal effort.

![Diagram of Experience Hub extensibility and customization workflow](/help/implementing/cloud-manager/release-notes/assets/experience-hub-extensibility-customization.png)

Embed custom experiences in Experience Hub to extend and personalize your organization's dashboard. In addition to Adobe's built-in widgets, add your own using the [UI Extensibility](https://developer.adobe.com/uix/docs/) framework. Build JavaScript-based UI apps and surface them to your users to meet business-specific requirements and workflows. 

Interested in the beta? Email [beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com) with your Adobe OrgID and a short description of the customization you intend to create.
-->

<!-- 
OLD
### Support for Custom Author Domains in Cloud Service

AEM Cloud Service is going to soon support one custom domain per Author environment.
-->



## Correctifs {#bug-fixes}

* Les crédits principaux ne sont pas libérés lorsque les deux environnements de groupe de production terminent la suppression réversible simultanément. Ce problème a été résolu. Les crédits sont désormais correctement libérés, quel que soit l’ordre dans lequel les suppressions simultanées se terminent. (CMGR-77845)

* Le crédit Content Hub est devenu orphelin après la suppression réversible de l’environnement suivie de la suppression définitive. Cloud Manager libère désormais correctement le crédit Content Hub lorsque l’environnement associé est entièrement supprimé. (CMGR-77585)

* La commande de l’interface de ligne de commande aio cloudmanager:tail-log se déconnecte à la rotation du journal au lieu de se reconnecter. La commande se reconnecte désormais automatiquement lorsqu’une rotation de journal est détectée. (CMGR-76557)

* Le contenu de la boîte de dialogue de mise en production complète ne peut pas défiler dans la Présentation du programme. La boîte de dialogue défile désormais correctement, s’assurant que tout le contenu est accessible quelle que soit la taille de l’écran. (CMGR-76405)

* Le mappage de domaine personnalisé échoue sur les nouveaux environnements de RDE créés. Après la création d’un environnement de développement rapide (RDE), les clients et clientes rencontraient l’erreur « Le statut de l’environnement n’est pas valide pour le changement de configuration de domaine » lors de la tentative d’ajout d’un mappage de domaine personnalisé immédiatement après la mise en service.Cloud Manager reflète désormais correctement l’état ready de l’environnement avant toute tentative de mappage de domaine. (CMGR-75904)

* La suppression d’un certificat DV et sa recréation pour le même domaine échouent avec l’erreur « certificat existant ». Lorsque les clients ont supprimé un certificat validé par un domaine (DV), puis ont essayé d’en créer un nouveau pour le même domaine, Cloud Manager a renvoyé l’erreur « Il existe un certificat qui couvre tous les domaines ». Par conséquent, il a bloqué l’émission du nouveau certificat. La suppression s’est produite dans l’interface utilisateur, mais le certificat n’a pas été entièrement supprimé en interne, ce qui a verrouillé le domaine. Ce problème est maintenant résolu. (CMGR-72784)

<!-- There are no significant bug fixes in the July 2026 Cloud Manager release. -->

<!-- ## Known issues {#known-issues} -->

