---
title: Maintenance d’un connecteur AEM
description: Découvrez comment gérer et mettre à jour votre connecteur AEM après l’envoi initial.
exl-id: 8122a8c8-6577-4907-8f6e-52711eed3970
feature: Operations
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 92%

---

Maintenance d’un connecteur AEM
============================

Cet article contient des informations sur la maintenance d’AEM Connector et doit être lu conjointement avec les articles sur l’[implémentation](implement.md) et l’[envoi](submit.md) de connecteurs.

Même après l’envoi initial, il peut y avoir des raisons pour qu’un partenaire mette à jour son connecteur AEM, soit en raison d’une nouvelle version d’AEM, soit indépendamment de celle-ci, par exemple, pour ajouter des fonctionnalités ou corriger des bogues. Cet article décrit le processus pour les deux scénarios et décrit également le processus type de validation des connecteurs par un client lors de la mise à niveau d’AEM.

Les applications AEM as a Cloud Service sont mises à jour quotidiennement avec les correctifs de maintenance d’AEM et les modifications plus importantes sont activées chaque mois au cours de la mise à jour des fonctionnalités. Bien que les mises à jour d’AEM soient conçues pour être rétrocompatibles et ne pas interrompre les applications, il est conseillé aux partenaires revendeurs de vérifier régulièrement que leurs connecteurs se comportent comme ils le devraient. L’accès au programme ou à l’environnement AEM est déterminé par l’équipe partenaire.
