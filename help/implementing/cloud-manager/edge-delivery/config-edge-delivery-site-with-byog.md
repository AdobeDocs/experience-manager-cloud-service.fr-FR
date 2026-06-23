---
title: Configurer un site Edge Delivery pour utiliser un référentiel Git externe
description: Découvrez comment lier un site Edge Delivery à un référentiel Git privé ou d’entreprise.
feature: Cloud Manager, Developing
role: Admin, Developer
exl-id: 1dbaef34-efa3-4287-b7b1-f60db938146d
source-git-commit: 069e94e230b856fba15c3f465c966a5bf6b0ac46
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 54%

---

# Configurer un site Edge Delivery pour utiliser un référentiel Git externe

Pour extraire du code de tout référentiel Git privé déjà intégré à Cloud Manager, vous pouvez configurer votre site Edge Delivery.

<!--
**Supported Git Vendors**

| Support level | Vendors | Notes |
| --- | --- | --- |
| General availability | &bull; GitHub Enterprise (self-hosted version)<br>&bull; Bitbucket (Cloud version)<br>&bull; GitLab (Cloud and self-hosted version) | Connect without enablement requests |
| Alpha program | Azure DevOps (Cloud version) | [Request access](mailto:grp-cloudmanager_byog@adobe.com) |
| Beta program | Adobe-hosted repository (created in Cloud Manager) | [Request access](mailto:grp-cloudmanager_byog@adobe.com) |
-->

**Pour utiliser un référentiel Git externe, configurez un site Edge Delivery :**

{{sign-in-to-cloud-manager}}

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme pour lequel Edge Delivery Services est configuré. Sélectionnez le programme dans lequel vous souhaitez configurer un site Edge Delivery pour utiliser un référentiel Git externe.
1. Dans le rail de gauche, sous l’en-tête **Programme**, cliquez sur **![Icône Vue d’ensemble](/help/implementing/cloud-manager/edge-delivery/assets/overview.svg) Vue d’ensemble**.
1. Sur la page **Vue d’ensemble du programme**, cliquez sur l’onglet **Edge Delivery**.
1. Dans le tableau **Sites Edge Delivery**, cliquez sur ![Icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) à la fin d’une ligne dont vous souhaitez configurer le site pour utiliser un référentiel externe, puis cliquez sur **Apporter votre propre référentiel Git**.
1. Dans la boîte de dialogue **Apporter votre propre Git**, dans la liste déroulante **Nom du référentiel**, choisissez un référentiel Git avec `READY` statut, puis cliquez sur **Confirmer**.

   Cloud Manager renvoie un jeton secret à usage unique. Si vous reconfigurez le site, Cloud Manager génère un nouveau jeton secret.

1. Copiez le jeton et ajoutez-le à la configuration du site dans **helix-admin**, comme décrit dans le guide [BYO Git](https://www.aem.live/developer/byo-git).
1. Dans Cloud Manager, cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) à la fin d’une ligne dont vous avez configuré le site pour utiliser un référentiel externe, puis cliquez sur **Code de synchronisation**.
1. Sélectionnez la branche à synchroniser, puis cliquez sur **Synchroniser**.

Chaque validation sur une branche déclenche désormais une synchronisation automatique. Réutilisez **Synchroniser le code** chaque fois qu’une synchronisation manuelle complète est requise.
