---
title: Configuration d’un site Edge Delivery pour utiliser un référentiel Git externe
description: Découvrez comment lier un site Edge Delivery à un référentiel Git privé ou d’entreprise.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 87650caea6eb907093f0f327f1dbc19641098e4a
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 9%

---


# Configuration d’un site Edge Delivery pour utiliser un référentiel Git externe

Vous pouvez configurer votre site Edge Delivery pour extraire du code de tout référentiel Git privé déjà intégré à Cloud Manager.

**Fournisseurs Git Pris En Charge**

| Niveau de prise en charge | Fournisseurs | Remarques |
| --- | --- | --- |
| Disponibilité générale | · GitHub Enterprise (version auto-hébergée)<br>· Bitbucket (version cloud)<br>· GitLab (version cloud et auto-hébergée) | Se connecter sans demandes d’activation |
| programme Alpha | Azure DevOps (version cloud) | [Demander l’accès](mailto:grp-cloudmanager_byog@adobe.com) |
| Programme Beta | Référentiel hébergé par Adobe (créé dans Cloud Manager) | [Demander l’accès](mailto:grp-cloudmanager_byog@adobe.com) |

**Pour configurer un site Edge Delivery afin d’utiliser un référentiel Git externe, procédez comme suit**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez le programme approprié.

1. Dans la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme avec Edge Delivery Services configuré, dans lequel vous souhaitez configurer un site Edge Delivery pour utiliser un référentiel Git externe.

1. Dans le rail de gauche, sous l’en-tête **Programme**, cliquez sur **![Icône Aperçu](/help/implementing/cloud-manager/edge-delivery/assets/overview.svg) Aperçu**.

1. Sur la page **Vue d’ensemble du programme**, cliquez sur l’onglet **Edge Delivery**.

1. Dans le tableau **Sites Edge Delivery**, cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) à la fin d’une ligne dont vous souhaitez configurer le site pour utiliser un référentiel externe, puis cliquez sur **Apporter votre propre référentiel Git**.

1. Dans la boîte de dialogue Apporter votre propre référentiel Git, dans la liste déroulante **Nom du référentiel**, choisissez un référentiel Git avec `READY` statut, puis cliquez sur **Confirmer**.

   Cloud Manager renvoie un jeton secret à usage unique. Si vous reconfigurez le site, Cloud Manager génère un nouveau jeton secret.

1. Copiez le jeton et ajoutez-le à la configuration du site dans **helix-admin**, comme décrit dans le guide [BYO Git](https://www.aem.live/developer/byo-git).

1. De retour dans Cloud Manager, cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) à la fin d’une ligne dont vous venez de configurer le site pour utiliser un référentiel externe, puis cliquez sur **Code de synchronisation**.

1. Sélectionnez la branche à synchroniser, puis cliquez sur **Synchroniser**.

Chaque validation sur une branche déclenche désormais une synchronisation automatique. Utilisez à nouveau le **code de synchronisation** chaque fois qu’une synchronisation manuelle complète est requise.

